<!-- Source: https://create.roblox.com/docs/ui/animation -->

UI animation/tweens | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/ui/animation.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [User interface](/docs/ui)

# UI animation/tweens

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/ui/animation.md)

In animation, tweening  is the process of generating intermediate frames between two key points in a sequence. When designing a user interface, you can use tweening to transition a [GuiObject](/docs/reference/engine/classes/GuiObject)  smoothly from one state to another, such as:

-

Smoothly increasing the size of a button when a user selects it.

-

Sliding UI menus in and out from the screen edges.

-

Gradually animating a health bar between two widths when a user receives a health boost.

## [Single-property tweens](#single-property-tweens)[](#single-property-tweens)

### [Position](#position)[](#position)

To tween the position  of a [GuiObject](/docs/reference/engine/classes/GuiObject) :

1.

Set the [AnchorPoint](/docs/reference/engine/classes/GuiObject#AnchorPoint)  for the object.

2.

Determine [UDim2](/docs/reference/engine/datatypes/UDim2)  coordinates for the object's target position, using the scale  parameters of [UDim2](/docs/reference/engine/datatypes/UDim2)  instead of exact pixel values so that the object tweens to the exact center of the screen.

3.

Pass a [TweenInfo](/docs/reference/engine/datatypes/TweenInfo)  and the target position to [TweenService:Create()](/docs/reference/engine/classes/TweenService#Create) .

4.

Play the tween with [Tween:Play()](/docs/reference/engine/classes/Tween#Play) .

The following code snippet moves an [ImageLabel](/docs/reference/engine/classes/ImageLabel)  within a [ScreenGui](/docs/reference/engine/classes/ScreenGui)  to the exact center of the screen:

UI Tween - Position

```

local TweenService = game:GetService("TweenService")

local Players = game:GetService("Players")

local PlayerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

local ScreenGui = PlayerGui:WaitForChild("ScreenGui")

local object = ScreenGui:WaitForChild("ImageLabel")

object.AnchorPoint = Vector2.new(0.5, 0.5)

local targetPosition = UDim2.new(0.5, 0, 0.5, 0)

local tweenInfo = TweenInfo.new(2)

local tween = TweenService:Create(object, tweenInfo, {Position = targetPosition})

tween:Play()

```

### [Size](#size)[](#size)

To tween the size  of a [GuiObject](/docs/reference/engine/classes/GuiObject) :

1.

Determine [UDim2](/docs/reference/engine/datatypes/UDim2)  coordinates for the object's target size, using the scale  parameters of [UDim2](/docs/reference/engine/datatypes/UDim2)  instead of exact pixel values so that the object tweens to a relative percentage of the screen size.

2.

Attach a [UIAspectRatioConstraint](/docs/reference/engine/classes/UIAspectRatioConstraint)  to the object to maintain its designed aspect ratio when tweening.

3.

Pass a [TweenInfo](/docs/reference/engine/datatypes/TweenInfo)  and the target size to [TweenService:Create()](/docs/reference/engine/classes/TweenService#Create) .

4.

Play the tween with [Tween:Play()](/docs/reference/engine/classes/Tween#Play) .

The following code snippet scales an [ImageLabel](/docs/reference/engine/classes/ImageLabel)  within a [ScreenGui](/docs/reference/engine/classes/ScreenGui)  to 40% of the screen width or height (whichever is smaller) from the object's center anchor point:

UI Tween - Size

```

local TweenService = game:GetService("TweenService")

local Players = game:GetService("Players")

local PlayerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

local ScreenGui = PlayerGui:WaitForChild("ScreenGui")

local object = ScreenGui:WaitForChild("ImageLabel")

object.AnchorPoint = Vector2.new(0.5, 0.5)

local aspectRatioConstraint = Instance.new("UIAspectRatioConstraint")

aspectRatioConstraint.Parent = object

local targetSize = UDim2.new(0.4, 0, 0.4, 0)

local tweenInfo = TweenInfo.new(2)

local tween = TweenService:Create(object, tweenInfo, {Size = targetSize})

tween:Play()

```

### [Rotation](#rotation)[](#rotation)

To tween the rotation  of a [GuiObject](/docs/reference/engine/classes/GuiObject) :

1.

Set the [AnchorPoint](/docs/reference/engine/classes/GuiObject#AnchorPoint)  for the object to rotate around.

2.

Determine the target [Rotation](/docs/reference/engine/classes/GuiObject#Rotation)  for the object.

3.

Pass a [TweenInfo](/docs/reference/engine/datatypes/TweenInfo)  and the target rotation to [TweenService:Create()](/docs/reference/engine/classes/TweenService#Create) .

4.

Play the tween with [Tween:Play()](/docs/reference/engine/classes/Tween#Play) .

UI Tween - Size

```

local TweenService = game:GetService("TweenService")

local Players = game:GetService("Players")

local PlayerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

local ScreenGui = PlayerGui:WaitForChild("ScreenGui")

local object = ScreenGui:WaitForChild("ImageLabel")

object.AnchorPoint = Vector2.new(0.5, 0.5)

local targetRotation = 45

local tweenInfo = TweenInfo.new(2)

local tween = TweenService:Create(object, tweenInfo, {Rotation = targetRotation})

tween:Play()

```

### [Transparency](#transparency)[](#transparency)

Multiple properties control UI transparency, depending on the object type. You can tween each of these properties individually or combined through a [multi-property tween](#multi-property-tweens) . Alternatively, you can tween an object's overall transparency by placing it inside a [CanvasGroup](/docs/reference/engine/classes/CanvasGroup)  and tweening the group's [GroupTransparency](/docs/reference/engine/classes/CanvasGroup#GroupTransparency) .

| UI Object | | Properties |
| --- | --- |
| [Frame](/docs/reference/engine/classes/Frame) | | [BackgroundTransparency](/docs/reference/engine/classes/GuiObject#BackgroundTransparency) |
| [TextLabel](/docs/reference/engine/classes/TextLabel) | | [BackgroundTransparency](/docs/reference/engine/classes/GuiObject#BackgroundTransparency) , [TextTransparency](/docs/reference/engine/classes/TextLabel#TextTransparency) , [TextStrokeTransparency](/docs/reference/engine/classes/TextLabel#TextStrokeTransparency) |
| [TextButton](/docs/reference/engine/classes/TextButton) | | [BackgroundTransparency](/docs/reference/engine/classes/GuiObject#BackgroundTransparency) , [TextTransparency](/docs/reference/engine/classes/TextButton#TextTransparency) , [TextStrokeTransparency](/docs/reference/engine/classes/TextButton#TextStrokeTransparency) |
| [ImageLabel](/docs/reference/engine/classes/ImageLabel) | | [BackgroundTransparency](/docs/reference/engine/classes/GuiObject#BackgroundTransparency) , [ImageTransparency](/docs/reference/engine/classes/ImageLabel#ImageTransparency) |
| [ImageButton](/docs/reference/engine/classes/ImageButton) | | [BackgroundTransparency](/docs/reference/engine/classes/GuiObject#BackgroundTransparency) , [ImageTransparency](/docs/reference/engine/classes/ImageButton#ImageTransparency) |

As a modern alternative to [TextLabel.TextStrokeTransparency](/docs/reference/engine/classes/TextLabel#TextStrokeTransparency)  and [TextButton.TextStrokeTransparency](/docs/reference/engine/classes/TextButton#TextStrokeTransparency) , you can tween stroke transparency on a [UIStroke](/docs/reference/engine/classes/UIStroke)  object as outlined in [Stroke](#stroke) .

UI Tween - Image Transparency

```

local TweenService = game:GetService("TweenService")

local Players = game:GetService("Players")

local PlayerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

local ScreenGui = PlayerGui:WaitForChild("ScreenGui")

local object = ScreenGui:WaitForChild("ImageLabel")

local targetTransparency = 0.8

local tweenInfo = TweenInfo.new(2)

local tween = TweenService:Create(object, tweenInfo, {ImageTransparency = targetTransparency})

tween:Play()

```

UI Tween - Canvas Group Transparency

```

local TweenService = game:GetService("TweenService")

local Players = game:GetService("Players")

local PlayerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

local ScreenGui = PlayerGui:WaitForChild("ScreenGui")

local canvasGroup = ScreenGui:WaitForChild("CanvasGroup")

local targetTransparency = 0.8

local tweenInfo = TweenInfo.new(2)

local tween = TweenService:Create(canvasGroup, tweenInfo, {GroupTransparency = targetTransparency})

tween:Play()

```

### [Color](#color)[](#color)

Multiple properties control UI color, depending on the object type. You can tween each of these properties individually or combined through a [multi-property tween](#multi-property-tweens) . Alternatively, you can tween an object's overall color by placing it inside a [CanvasGroup](/docs/reference/engine/classes/CanvasGroup)  and tweening the group's [GroupColor3](/docs/reference/engine/classes/CanvasGroup#GroupColor3) .

| UI Object | | Properties |
| [Frame](/docs/reference/engine/classes/Frame) | | [BackgroundColor3](/docs/reference/engine/classes/GuiObject#BackgroundColor3) , [BorderColor3](/docs/reference/engine/classes/GuiObject#BorderColor3) |
| [TextLabel](/docs/reference/engine/classes/TextLabel) | | [BackgroundColor3](/docs/reference/engine/classes/GuiObject#BackgroundColor3) , [BorderColor3](/docs/reference/engine/classes/GuiObject#BorderColor3) , [TextColor3](/docs/reference/engine/classes/TextLabel#TextColor3) , [TextStrokeColor3](/docs/reference/engine/classes/TextLabel#TextStrokeColor3) |
| [TextButton](/docs/reference/engine/classes/TextButton) | | [BackgroundColor3](/docs/reference/engine/classes/GuiObject#BackgroundColor3) , [BorderColor3](/docs/reference/engine/classes/GuiObject#BorderColor3) , [TextColor3](/docs/reference/engine/classes/TextButton#TextColor3) , [TextStrokeColor3](/docs/reference/engine/classes/TextButton#TextStrokeColor3) |
| [ImageLabel](/docs/reference/engine/classes/ImageLabel) | | [BackgroundColor3](/docs/reference/engine/classes/GuiObject#BackgroundColor3) , [BorderColor3](/docs/reference/engine/classes/GuiObject#BorderColor3) , [ImageColor3](/docs/reference/engine/classes/ImageLabel#ImageColor3) |
| [ImageButton](/docs/reference/engine/classes/ImageButton) | | [BackgroundColor3](/docs/reference/engine/classes/GuiObject#BackgroundColor3) , [BorderColor3](/docs/reference/engine/classes/GuiObject#BorderColor3) , [ImageColor3](/docs/reference/engine/classes/ImageButton#ImageColor3) |

As a modern alternative to [GuiObject.BorderColor3](/docs/reference/engine/classes/GuiObject#BorderColor3) , [TextLabel.TextStrokeColor3](/docs/reference/engine/classes/TextLabel#TextStrokeColor3) , and [TextButton.TextStrokeColor3](/docs/reference/engine/classes/TextButton#TextStrokeColor3) , you can tween stroke color on a [UIStroke](/docs/reference/engine/classes/UIStroke)  object as outlined in [Stroke](#stroke) .

UI Tween - Image Color

```

local TweenService = game:GetService("TweenService")

local Players = game:GetService("Players")

local PlayerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

local ScreenGui = PlayerGui:WaitForChild("ScreenGui")

local object = ScreenGui:WaitForChild("ImageLabel")

local targetColor = Color3.fromRGB(255, 0, 0)

local tweenInfo = TweenInfo.new(2)

local tween = TweenService:Create(object, tweenInfo, {ImageColor3 = targetColor})

tween:Play()

```

UI Tween - Canvas Group Color

```

local TweenService = game:GetService("TweenService")

local Players = game:GetService("Players")

local PlayerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

local ScreenGui = PlayerGui:WaitForChild("ScreenGui")

local canvasGroup = ScreenGui:WaitForChild("CanvasGroup")

local targetColor = Color3.fromRGB(255, 0, 0)

local tweenInfo = TweenInfo.new(2)

local tween = TweenService:Create(canvasGroup, tweenInfo, {GroupColor3 = targetColor})

tween:Play()

```

### [Stroke](#stroke)[](#stroke)

Multiple properties control UI borders, depending on the object type.

| UI object | | Properties |
| [Frame](/docs/reference/engine/classes/Frame) | | [BorderSizePixel](/docs/reference/engine/classes/GuiObject#BorderSizePixel) , [BorderColor3](/docs/reference/engine/classes/GuiObject#BorderColor3) |
| [TextLabel](/docs/reference/engine/classes/TextLabel) | | [BorderSizePixel](/docs/reference/engine/classes/GuiObject#BorderSizePixel) , [BorderColor3](/docs/reference/engine/classes/GuiObject#BorderColor3) , [TextStrokeColor3](/docs/reference/engine/classes/TextLabel#TextStrokeColor3) , [TextStrokeTransparency](/docs/reference/engine/classes/TextLabel#TextStrokeTransparency) |
| [TextButton](/docs/reference/engine/classes/TextButton) | | [BorderSizePixel](/docs/reference/engine/classes/GuiObject#BorderSizePixel) , [BorderColor3](/docs/reference/engine/classes/GuiObject#BorderColor3) , [TextStrokeColor3](/docs/reference/engine/classes/TextButton#TextStrokeColor3) , [TextStrokeTransparency](/docs/reference/engine/classes/TextButton#TextStrokeTransparency) |
| [ImageLabel](/docs/reference/engine/classes/ImageLabel) | | [BorderSizePixel](/docs/reference/engine/classes/GuiObject#BorderSizePixel) , [BorderColor3](/docs/reference/engine/classes/GuiObject#BorderColor3) |
| [ImageButton](/docs/reference/engine/classes/ImageButton) | | [BorderSizePixel](/docs/reference/engine/classes/GuiObject#BorderSizePixel) , [BorderColor3](/docs/reference/engine/classes/GuiObject#BorderColor3) |

Alternatively, you can apply a [UIStroke](/docs/reference/engine/classes/UIStroke)  child and tween its thickness, color, and/or transparency.

| UI Object | | Properties |
| [UIStroke](/docs/reference/engine/classes/UIStroke) | | [Color](/docs/reference/engine/classes/UIStroke#Color) , [Thickness](/docs/reference/engine/classes/UIStroke#Thickness) , [Transparency](/docs/reference/engine/classes/UIStroke#Transparency) |

UI Tween - UIStroke Color & Thickness

```

local TweenService = game:GetService("TweenService")

local Players = game:GetService("Players")

local PlayerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

local ScreenGui = PlayerGui:WaitForChild("ScreenGui")

local object = ScreenGui:WaitForChild("TextLabel")

local stroke = Instance.new("UIStroke")

stroke.Color = Color3.fromRGB(255, 255, 255)

stroke.Thickness = 5

stroke.Parent = object

local targetColor = Color3.fromRGB(255, 0, 0)

local targetThickness = 10

local tweenInfo = TweenInfo.new(2)

local tween = TweenService:Create(stroke, tweenInfo, {Color = targetColor, Thickness = targetThickness})

tween:Play()

```

## [Multi-property tweens](#multi-property-tweens)[](#multi-property-tweens)

You can combine any of the [single-property tweens](#single-property-tweens)  into more complex tweens by passing multiple target properties to [TweenService:Create()](/docs/reference/engine/classes/TweenService#Create) , for example position + rotation  or size + transparency .

UI Tween - Position & Rotation

```

local TweenService = game:GetService("TweenService")

local Players = game:GetService("Players")

local PlayerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

local ScreenGui = PlayerGui:WaitForChild("ScreenGui")

local object = ScreenGui:WaitForChild("ImageLabel")

object.AnchorPoint = Vector2.new(0.5, 0.5)

local targetPosition = UDim2.new(0.5, 0, 0.5, 0)

local targetRotation = 45

local tweenInfo = TweenInfo.new(2)

local tween = TweenService:Create(object, tweenInfo, {Position = targetPosition, Rotation = targetRotation})

tween:Play()

```

UI Tween - Size & Transparency

```

local TweenService = game:GetService("TweenService")

local Players = game:GetService("Players")

local PlayerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

local ScreenGui = PlayerGui:WaitForChild("ScreenGui")

local object = ScreenGui:WaitForChild("ImageLabel")

object.AnchorPoint = Vector2.new(0.5, 0.5)

local aspectRatioConstraint = Instance.new("UIAspectRatioConstraint")

aspectRatioConstraint.Parent = object

local targetSize = UDim2.new(0.4, 0, 0.4, 0)

local targetTransparency = 0.8

local tweenInfo = TweenInfo.new(2)

local tween = TweenService:Create(object, tweenInfo, {Size = targetSize, ImageTransparency = targetTransparency})

tween:Play()

```

## [Tween sequences](#tween-sequences)[](#tween-sequences)

You can chain UI animations to occur one after another by playing subsequent tweens upon the previous tween's [Completed](/docs/reference/engine/classes/TweenBase#Completed)  event. For example, the following script moves an object to the center of the screen, then rotates it by 45°.

UI Tween Sequence

```

local TweenService = game:GetService("TweenService")

local Players = game:GetService("Players")

local PlayerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

local ScreenGui = PlayerGui:WaitForChild("ScreenGui")

local object = ScreenGui:WaitForChild("ImageLabel")

object.AnchorPoint = Vector2.new(0.5, 0.5)

local targetPosition = UDim2.new(0.5, 0, 0.5, 0)

local targetRotation = 45

local tweenInfo = TweenInfo.new(2)

local positionTween = TweenService:Create(object, tweenInfo, {Position = targetPosition})

local rotationTween = TweenService:Create(object, tweenInfo, {Rotation = targetRotation})

-- Initially play position tween

positionTween:Play()

-- Play rotation tween upon completion of position tween

positionTween.Completed:Connect(function()

	rotationTween:Play()

end)

```

## [Style transitions](#style-transitions)[](#style-transitions)

UI objects can also be animated through style transitions , comparable to [CSS transitions](/docs/ui/styling/css-comparisons#transitions) , where one or more UI properties are tweened through [StyleRule](/docs/reference/engine/classes/StyleRule)  definitions. See the [Style Editor](/docs/ui/styling/editor#style-transitions)  guide for details.

 ![Final styled state rule in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-Result.png)

## [Easing options](#easing-options)[](#easing-options)

Using the easing options of [TweenInfo](/docs/reference/engine/datatypes/TweenInfo) , you can control the easing style  and direction  of UI animations.

### [Style](#style)[](#style)

[Enum.EasingStyle](/docs/reference/engine/enums/EasingStyle)  sets the rate of interpolation from start to end. By default, easing style is set to [Enum.EasingStyle.Quad](/docs/reference/engine/enums/EasingStyle#Quad) .

| Style | | Description |
| Linear | | Moves at a constant speed. |
| Sine | | Speed is determined by a sine wave for a gentle easing motion. |
| Quad | | Similar to Sine  but with a slightly sharper curve based on quadratic interpolation. |
| Cubic | | Similar to Quad  but with a slightly sharper curve based on cubic interpolation. |
| Quart | | Similar to Cubic  but with an even sharper curve based on quartic interpolation. |
| Quint | | Similar to Quart  but with an even sharper curve based on quintic interpolation. |
| Exponential | | The sharpest curve based on exponential interpolation. |
| Circular | | Follows a circular arc, such that acceleration is more sudden and deceleration more gradual versus Quint  or Exponential . |
| Back | | Slightly overshoots the target, then backs into place. |
| Bounce | | Bounces backwards multiple times after reaching the target, before eventually settling. |
| Elastic | | Moves as if attached to a rubber band, overshooting the target several times. |

EasingDirection = In EasingDirection = Out EasingDirection = InOut

![Graphs of EasingStyle variations with an 'In' EasingDirection.](https://prod.docsiteassets.roblox.com/assets/engine-api/enums/EasingStyle/Easing-Styles-In.png)

Easing Style - Cubic

```

local tweenInfo = TweenInfo.new(2, Enum.EasingStyle.Cubic)

local tween = TweenService:Create(object, tweenInfo, {Rotation = 45})

```

### [Direction](#direction)[](#direction)

[Enum.EasingDirection](/docs/reference/engine/enums/EasingDirection)  defines how the [easing style](#style)  interpolation applies to an object, with a default of Out . Note that a tween with Linear  easing style is not affected, as linear interpolation is constant from start to end.

| Direction | | Description |
| In | | The easing style applies in a forward direction. |
| Out | | The easing style applies in a reverse direction. |
| InOut | | The easing style applies forward for the first half and in reverse for the second half. |

Easing direction - InOut

```

local tweenInfo = TweenInfo.new(2, Enum.EasingStyle.Cubic, Enum.EasingDirection.InOut)

local tween = TweenService:Create(object, tweenInfo, {Rotation = 45})

```

## [Typewriter effect on text](#typewriter-effect-on-text)[](#typewriter-effect-on-text)

You can easily enhance text-based UI, such as cutscene banners, player instructions, and prompts, with animated effects. The "typewriter" effect is ideal for [TextLabels](/docs/reference/engine/classes/TextLabel)  that tell a story, output NPC conversations, etc.

1.

Create a new [ModuleScript](/docs/reference/engine/classes/ModuleScript)  within ReplicatedStorage .

2.

Rename the new script AnimateUI .

 ![](https://prod.docsiteassets.roblox.com/assets/ui/ui-animation/ModuleScript-AnimateUI.png)

3.

Paste the following code into the script:

ModuleScript - AnimateUI

```

local LocalizationService = game:GetService("LocalizationService")

local Players = game:GetService("Players")

local SOURCE_LOCALE = "en"

local translator = nil

local AnimateUI = {}

function AnimateUI.loadTranslator()

	pcall(function()

		translator = LocalizationService:GetTranslatorForPlayerAsync(Players.LocalPlayer)

	end)

	if not translator then

		pcall(function()

			translator = LocalizationService:GetTranslatorForLocaleAsync(SOURCE_LOCALE)

		end)

	end

end

function AnimateUI.typeWrite(guiObject, text, delayBetweenChars)

	guiObject.Visible = true

	guiObject.AutoLocalize = false

	local displayText = text

	-- Translate text if possible

	if translator then

		displayText = translator:Translate(guiObject, text)

	end

	-- Replace line break tags so grapheme loop will not miss those characters

	displayText = displayText:gsub("<br%s*/>", "\n")

 	-- Remove RichText tags since char-by-char animation will break the tags

	displayText = displayText:gsub("<[^<>]->", "")

	-- Set translated/modified text on parent

	guiObject.Text = displayText

	local index = 0

	for first, last in utf8.graphemes(displayText) do

		index += 1

		guiObject.MaxVisibleGraphemes = index

		task.wait(delayBetweenChars)

	end

end

return AnimateUI

```

If your game's source language  is not English ("en" ), change the locale code for SOURCE_LOCALE  to match the source language in [localization settings](/docs/production/localization#localization-settings) .

4.

Create a [TextLabel](/docs/reference/engine/classes/TextLabel)  in a suitable location, such as within a [ScreenGui](/docs/reference/engine/classes/ScreenGui)  parented to [StarterGui](/docs/reference/engine/classes/StarterGui) .

5.

Insert a new [LocalScript](/docs/reference/engine/classes/LocalScript)  as a direct child of the label and paste in the following code. Note that each message is output by calling AnimateUI.typeWrite()  with parameters for the parent object, the string to output, and the delay between characters.

LocalScript

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local AnimateUI = require(ReplicatedStorage:WaitForChild("AnimateUI"))

local label = script.Parent

-- Load translator if game is localized

--AnimateUI.loadTranslator()

local message1 = [[Beyond this door is the<br /><font size="46" color="rgb(255,50,25)">Great Zorgoth...</font> <font size="40">🗡</font>]]

AnimateUI.typeWrite(label, message1, 0.05)

task.wait(1)

local message2 = [[...who rules this dungeon <font color="rgb(255,200,50)">unchallenged!</font> <font size="30">😈</font>]]

AnimateUI.typeWrite(label, message2, 0.05)

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
