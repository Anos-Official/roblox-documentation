<!-- Source: https://create.roblox.com/docs/en-us/resources/beyond-the-dark/user-interface -->

User interface | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/resources/beyond-the-dark/user-interface.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Samples and projects](/docs/en-us/samples)
4. /
5. [Beyond the Dark](/docs/en-us/resources/beyond-the-dark)

# User interface

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/resources/beyond-the-dark/user-interface.md)

We wanted to add an interactive map UI to let users consume information in the space station that looked and felt like it lived in this world. We decided to build the map inside the 3D space instead of on a screen that overlays the experience. This type of diegetic visualization allows for more immersion with the world as opposed to feeling like it is a completely separate experience.

## [Design the map](#design-the-map)[](#design-the-map)

To design the map:

1.

We mocked the UI in an external application and came up with a rough idea of how we wanted it to look.

 ![UI Mock](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/user-interface/UI-Mock.png)

2.

We exported the individual pieces of the map as .png  and imported them into Studio.

 ![UI Elements Exported](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/user-interface/UI-Export.png)

## [Build the map](#build-the-map)[](#build-the-map)

Building the map inside Studio involved using [Parts](/docs/en-us/reference/engine/classes/Part)  and [SurfaceGuis](/docs/en-us/reference/engine/classes/SurfaceGui) .

1.

For non-interactive elements, all we needed to do is add a [SurfaceGui](/docs/en-us/reference/engine/classes/SurfaceGui)  object to the part.

2.

For interactive elements, the [SurfaceGui](/docs/en-us/reference/engine/classes/SurfaceGui)  also needs to be inside the [StarterGui](/docs/en-us/reference/engine/classes/StarterGui)  container, with the Adornee  property linked to the appropriate part in the 3D workspace. Doing so allows you to add button events.

3.

To achieve a parallax effect, we used three separate [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  instances assigned to three unique Parts  with different X  values.

 ![Parallax Example](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/user-interface/Parallax-Example.png)

4.

We then added a glow effect with the [SurfaceGui.LightInfluence](/docs/en-us/reference/engine/classes/SurfaceGui#LightInfluence)  property. If you set the property value to anything less than 1, it enables the [SurfaceGui.Brightness](/docs/en-us/reference/engine/classes/SurfaceGui#Brightness)  property. By adjusting the brightness, you can increase the glow emitting from the image.

5.

To let users toggle the display of the map, we used a [ProximityPrompt](/docs/en-us/reference/engine/classes/ProximityPrompt)  that we attached to a 3D model. This is an easy way to allow user interaction with world elements.

 ![Proximity Prompt in Explorer](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/user-interface/Proximity-Prompt.png)

6.

Finally, using a UITweenModule ModuleScript inside ReplicatedStorage, we animated hiding and showing the UI with TweenService and a bit of logic for determining the state. By tracking what the user clicked, we could hide and show elements by tweening various properties like alpha, position, and size.

 ![PUI Tween Module in Explorer](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/user-interface/UITweenModule.png)

UITweenModule ModuleScript

```

local TweenService = game:GetService("TweenService")

local UITween = {}

-- for fading images

function UITween.fadePart(object, amount, time, delay)

	local tweenAlpha = TweenInfo.new(

		time, --Time

		Enum.EasingStyle.Quad, --EasingStyle

		Enum.EasingDirection.Out, --EasingDirection

		0, --Repeat count

		false, --Reverses if true

		delay --Delay time

	)

	local tween = TweenService:Create(object, tweenAlpha, {Transparency = amount})

	tween:Play()

end

function UITween.fade(object, amount, time, delay)

	local tweenAlpha = TweenInfo.new(

		time, --Time

		Enum.EasingStyle.Quad, --EasingStyle

		Enum.EasingDirection.Out, --EasingDirection

		0, --Repeat count

		false, --Reverses if true

		delay --Delay time

	)

	local tween = TweenService:Create(object, tweenAlpha, {ImageTransparency = amount})

	tween:Play()

end

-- for fading images

function UITween.fadeBackground(object, amount, time, delay)

	local tweenAlpha = TweenInfo.new(

		time, --Time

		Enum.EasingStyle.Quad, --EasingStyle

		Enum.EasingDirection.Out, --EasingDirection

		0, --Repeat count

		false, --Reverses if true

		delay --Delay time

	)

	local tween = TweenService:Create(object, tweenAlpha, {BackgroundTransparency = amount})

	tween:Play()

end

-- for fading text

function UITween.fadeText(object, amount, time, delay)

	local tweenAlpha = TweenInfo.new(

		time, --Time

		Enum.EasingStyle.Quad, --EasingStyle

		Enum.EasingDirection.Out, --EasingDirection

		0, --Repeat count

		false, --Reverses if true

		delay --Delay time

	)

	local tween1 = TweenService:Create(object, tweenAlpha, {TextTransparency = amount})

	tween1:Play()

end

-- for moving text and images

function UITween.move(object, position, time, delay)

	task.wait(delay)

	object:TweenPosition(position, Enum.EasingDirection.Out, Enum.EasingStyle.Quint, time)

end

-- for changing size

function UITween.size(object, size, time, delay, override, callback)

	local tweenSize = TweenInfo.new(

		time, --Time

		Enum.EasingStyle.Quint, --EasingStyle

		Enum.EasingDirection.Out, --EasingDirection

		0, --Repeat count

		false, --Reverses if true

		delay, --Delay time

		override,

		callback

	)

	local tween = TweenService:Create(object, tweenSize, {Size = size})

	tween:Play()

end

function UITween.rotate(object, rotation, time, delay, override, callback)

	local tweenSize = TweenInfo.new(

		time, --Time

		Enum.EasingStyle.Quint, --EasingStyle

		Enum.EasingDirection.Out, --EasingDirection

		0, --Repeat count

		false, --Reverses if true

		delay, --Delay time

		override,

		callback

	)

	local tween = TweenService:Create(object, tweenSize, {Rotation = rotation})

	tween:Play()

end

-- for blurring the game camera

function UITween.blur(object, amount, time)

	local tweenInfo = TweenInfo.new(time, Enum.EasingStyle.Linear, Enum.EasingDirection.Out, 0, false, 0)

	local tween = TweenService:Create(object, tweenInfo, {Size = amount})

	tween:Play()

end

-- for blurring the game camera

function UITween.turnOn(object, amount, time)

	local tweenInfo = TweenInfo.new(time, Enum.EasingStyle.Linear, Enum.EasingDirection.Out, 0, false, 0)

	local tween = TweenService:Create(object, tweenInfo, {Brightness = amount})

	tween:Play()

end

return UITween

```

Applying UI Tween to Objects

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- Add UITween Module

local UITween = require(ReplicatedStorage.UITweenModule)

-- Find player Guis and UI objects

local playerGui = game:GetService('Players').LocalPlayer:WaitForChild('PlayerGui')

local screenGuiMapUIFrame = playerGui:WaitForChild("ScreenGuiMapUIFrame").SurfaceGui

local mapUIFrameStroke = screenGuiMapUIFrame.FrameStroke

local mapUIFrameFill = screenGuiMapUIFrame.FrameFill

-- Sizes used for tweening

local frameSizeStart = UDim2.new(0, 0, 0, 0)

local frameSizeMid = UDim2.new(1, 0, 0.05, 0)

local frameSizeEnd = UDim2.new(1, 0, 1, 0)

-- Example Tweening

UITween.fade(mapUIFrameStroke, 0, 2, 0)

UITween.size(mapUIFrameStroke, frameSizeMid, 0.4, 0)

UITween.fade(mapUIFrameFill, 0, 2, 0.5)

UITween.size(mapUIFrameFill, frameSizeEnd, 0.4, 0.25)

task.wait(0.25)

UITween.size(mapUIFrameStroke, frameSizeMid, 0.4, 0)

UITween.size(mapUIFrameFill, frameSizeMid, 0.4, 0.25)

task.wait(0.25)

UITween.size(mapUIFrameStroke, frameSizeEnd, 0.4, 0)

UITween.size(mapUIFrameFill, frameSizeEnd, 0.4, 0.25)

```

Here's the final result of the interactive map:

[Previous](/docs/en-us/resources/beyond-the-dark/sound-design)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
