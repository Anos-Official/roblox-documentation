<!-- Source: https://create.roblox.com/docs/en-us/production/publishing/accessibility -->

Accessibility guidelines | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/production/publishing/accessibility.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Game design](/docs/en-us/production/game-design)
6. /
7. Build your experience

# Accessibility guidelines

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/production/publishing/accessibility.md)

Accessibility  is the practice of designing products and services to be usable by people with disabilities. Recent stats cite that over 26% of people have some type of disability, so making your Roblox game accessible can help you reach a wider audience.

## [Text size](#text-size)[](#text-size)

Players may find it difficult to read small text. Compare the following in-game shop menu with a blur applied, simulating what it might look like to somebody with impaired vision.

Sighted Low Vision

![Example of small text on user interface](https://prod.docsiteassets.roblox.com/assets/publishing/accessibility/Text-Size-SM.jpg)

If you increase the size of the smaller font labels, it will be clearer to most players.

Sighted Low Vision

![Example of larger text on user interface](https://prod.docsiteassets.roblox.com/assets/publishing/accessibility/Text-Size-LG.jpg)

## [Color contrast](#color-contrast)[](#color-contrast)

Players might find it difficult to read light text on a light background, or dark text on a dark background. To improve accessibility, it's recommended that you pick text and background colors with sufficient color contrast.

![Example UI elements with high contrast](https://prod.docsiteassets.roblox.com/assets/publishing/accessibility/Color-Contrast-High.png)

High contrast

![Example UI elements with low contrast](https://prod.docsiteassets.roblox.com/assets/publishing/accessibility/Color-Contrast-Low.png)

Low contrast

## [Color non-reliance](#color-non-reliance)[](#color-non-reliance)

Over 5% of people in the world have some form of color blindness. Although it's rare for someone to see only  in black and white, imagine viewing a game in grayscale:

No Color Blindness Color Blindness

![Example user interface shown in full color](https://prod.docsiteassets.roblox.com/assets/publishing/accessibility/Color-Normal.jpg)

By modifying the image to use different symbols  alongside colors, more players can tell the difference in gameplay and in other contexts:

No Color Blindness Color Blindness

![Example user interface shown in full color](https://prod.docsiteassets.roblox.com/assets/publishing/accessibility/Color-Symbols-Normal.jpg)

## [Sound non-reliance](#sound-non-reliance)[](#sound-non-reliance)

Sound is an excellent addition for immersive games, but hearing-impaired players or anyone who turns their volume off will be confused by in-game events that are only  conveyed with sound.

Consider the following scene where a ringing phone is signalled only by sound, and then signalled with both sound and  visual aids.

## [Player preferences](#player-preferences)[](#player-preferences)

Various visual settings are available to players from the Roblox and in-game Settings  menus, including [preferred transparency](#preferred-transparency) , [preferred text size](#preferred-text-size) , and [reduced motion](#reduced-motion) . For optimal accessibility, your [user interface](/docs/en-us/ui)  should accommodate each.

### [Preferred transparency](#preferred-transparency)[](#preferred-transparency)

The Background Transparency  setting maps to the [GuiService.PreferredTransparency](/docs/en-us/reference/engine/classes/GuiService#PreferredTransparency)  property. A value of 1  indicates the player prefers the default background transparency, while a value of 0  indicates the player prefers fully opaque (non‑transparent) background transparency for improved readability and contrast.

Multiplying a UI element's [BackgroundTransparency](/docs/en-us/reference/engine/classes/GuiObject#BackgroundTransparency)  with [PreferredTransparency](/docs/en-us/reference/engine/classes/GuiService#PreferredTransparency)  is the recommended way to use this setting; backgrounds will become more opaque as [PreferredTransparency](/docs/en-us/reference/engine/classes/GuiService#PreferredTransparency)  approaches 0 .

1.

Using the [tagging](/docs/en-us/studio/properties#instance-tags)  system, apply a tag of TransparentBack  to all UI items with [BackgroundTransparency](/docs/en-us/reference/engine/classes/GuiObject#BackgroundTransparency)  such as [TextLabels](/docs/en-us/reference/engine/classes/TextLabel)  or [Frames](/docs/en-us/reference/engine/classes/Frame) .

![Four TextLabel elements with varying BackgroundTransparency levels](https://prod.docsiteassets.roblox.com/assets/publishing/accessibility/Preferred-Transparency-Labels.png) Four [TextLabel](/docs/en-us/reference/engine/classes/TextLabel)  elements with varying [BackgroundTransparency](/docs/en-us/reference/engine/classes/GuiObject#BackgroundTransparency)  levels

2.

Paste the following code into a [LocalScript](/docs/en-us/reference/engine/classes/LocalScript)  within [StarterPlayerScripts](/docs/en-us/reference/engine/classes/StarterPlayerScripts) .

Dynamic Adjustment for Preferred Transparency

```

local GuiService = game:GetService("GuiService")

local CollectionService = game:GetService("CollectionService")

local TAG = "TransparentBack"

local transparentBackObjects = {}

local function onInstanceAdded(object)

	if object.BackgroundTransparency then

		local defaultTransparency = object.BackgroundTransparency

		transparentBackObjects[object] = defaultTransparency

		object.BackgroundTransparency = defaultTransparency * GuiService.PreferredTransparency

	end

end

local function onInstanceRemoved(object)

	transparentBackObjects[object] = nil

end

-- Store initial tagged instances

for _, object in CollectionService:GetTagged(TAG) do

	onInstanceAdded(object)

end

-- Detect when tagged instance is added or removed

CollectionService:GetInstanceAddedSignal(TAG):Connect(onInstanceAdded)

CollectionService:GetInstanceRemovedSignal(TAG):Connect(onInstanceRemoved)

-- When in-game setting is changed, adjust tagged instances

GuiService:GetPropertyChangedSignal("PreferredTransparency"):Connect(function()

	for object, defaultTransparency in transparentBackObjects do

		object.BackgroundTransparency = defaultTransparency * GuiService.PreferredTransparency

	end

end)

```

3.

Playtest the game, open the Settings  menu, and adjust Background Transparency . The tagged UI elements should update between their default [BackgroundTransparency](/docs/en-us/reference/engine/classes/GuiObject#BackgroundTransparency)  and fully opaque.

Default 50% More Opaque Fully Opaque

![](https://prod.docsiteassets.roblox.com/assets/publishing/accessibility/Preferred-Transparency-Default.png)

### [Preferred text size](#preferred-text-size)[](#preferred-text-size)

The Text Size  setting maps to the [GuiService.PreferredTextSize](/docs/en-us/reference/engine/classes/GuiService#PreferredTextSize)  property which defaults to [Medium](/docs/en-us/reference/engine/enums/PreferredTextSize#Medium) . Players can choose to increase text size through the engine's font rendering pipeline to [Large](/docs/en-us/reference/engine/enums/PreferredTextSize#Large) , [Larger](/docs/en-us/reference/engine/enums/PreferredTextSize#Larger) , or [Largest](/docs/en-us/reference/engine/enums/PreferredTextSize#Largest) .

When working with UI elements, note the following behaviors:

-

Text that is constrained to a minimum and/or maximum size through a [UITextSizeConstraint](/docs/en-us/reference/engine/classes/UITextSizeConstraint)  will not  shrink below or expand above the set [MinTextSize](/docs/en-us/reference/engine/classes/UITextSizeConstraint#MinTextSize) /[MaxTextSize](/docs/en-us/reference/engine/classes/UITextSizeConstraint#MaxTextSize) , regardless of the player's text size setting.

-

When [TextScaled](/docs/en-us/reference/engine/classes/TextLabel#TextScaled)  is enabled for a [TextLabel](/docs/en-us/reference/engine/classes/TextLabel#TextScaled)  or [TextButton](/docs/en-us/reference/engine/classes/TextButton#TextScaled) , the element's text will not  be scaled by the [PreferredTextSize](/docs/en-us/reference/engine/classes/GuiService#PreferredTextSize)  value.

-

UI elements with [AutomaticSize](/docs/en-us/reference/engine/classes/GuiObject#AutomaticSize)  enabled will shrink/grow as [PreferredTextSize](/docs/en-us/reference/engine/classes/GuiService#PreferredTextSize)  decreases/increases (element bounds will resize to fit the resized text).

-

When [TextWrapped](/docs/en-us/reference/engine/classes/TextLabel#TextWrapped)  is enabled for a [TextLabel](/docs/en-us/reference/engine/classes/TextLabel#TextWrapped)  or [TextButton](/docs/en-us/reference/engine/classes/TextButton#TextWrapped) , the element's text will wrap to additional lines as [PreferredTextSize](/docs/en-us/reference/engine/classes/GuiService#PreferredTextSize)  increases, within limits of the element's absolute size.

-

The results returned by [TextService:GetTextSize()](/docs/en-us/reference/engine/classes/TextService#GetTextSize)  and [TextService:GetTextBoundsAsync()](/docs/en-us/reference/engine/classes/TextService#GetTextBoundsAsync)  honor changes related to [PreferredTextSize](/docs/en-us/reference/engine/classes/GuiService#PreferredTextSize) .

### [Reduced motion](#reduced-motion)[](#reduced-motion)

The Reduce Motion  toggle maps to the [GuiService.ReducedMotionEnabled](/docs/en-us/reference/engine/classes/GuiService#ReducedMotionEnabled)  property. A value of true  indicates the player wants motion effects through [UI animations/tweens](/docs/en-us/ui/animation)  to be reduced or completely removed.

A basic approach to removing motion from UI tweens is to set the [Time](/docs/en-us/reference/engine/datatypes/TweenInfo#Time)  parameter of a [TweenInfo](/docs/en-us/reference/engine/datatypes/TweenInfo)  to 0  when [ReducedMotionEnabled](/docs/en-us/reference/engine/classes/GuiService#ReducedMotionEnabled)  is true , effectively making the UI object snap to its target instantly.

UI Tween Snap-to-Target for Reduced Motion

```

local GuiService = game:GetService("GuiService")

local Players = game:GetService("Players")

local TweenService = game:GetService("TweenService")

local player = Players.LocalPlayer

local playerGui = player.PlayerGui

local menuUI = playerGui:WaitForChild("MenuUI")

-- Use tween time of 0.75 seconds unless reduced motion is enabled

local TWEEN_TIME = if GuiService.ReducedMotionEnabled then 0 else 0.75

local tweenInfo = TweenInfo.new(TWEEN_TIME, Enum.EasingStyle.Cubic, Enum.EasingDirection.Out)

local tween = TweenService:Create(menuUI.SettingsFrame, tweenInfo, {Position = UDim2.fromScale(0.5, 0.5)})

tween:Play()

```

Alternatively to instant snapping, you can handle [ReducedMotionEnabled](/docs/en-us/reference/engine/classes/GuiService#ReducedMotionEnabled)  with more distinct true / false  logic. For example, the following [LocalScript](/docs/en-us/reference/engine/classes/LocalScript)  uses motion tweening by default, but switches to fade‑in for players who enable reduced motion, resulting in a more elegant transition without positional movement.

Fallback to Fade Tween for Reduced Motion

```

local GuiService = game:GetService("GuiService")

local Players = game:GetService("Players")

local TweenService = game:GetService("TweenService")

local player = Players.LocalPlayer

local playerGui = player.PlayerGui

local menuUI = playerGui:WaitForChild("MenuUI")

-- Create a canvas group to tween all children uniformly

local canvasGroup = Instance.new("CanvasGroup")

canvasGroup.Size = UDim2.fromScale(1, 1)

canvasGroup.BackgroundTransparency = 1

canvasGroup.Parent = menuUI

-- Add children to canvas group

menuUI.SettingsFrame.Parent = canvasGroup

local tweenInfo = TweenInfo.new(0.75, Enum.EasingStyle.Cubic, Enum.EasingDirection.Out)

local tween

-- Use fading tween for reduced motion, or a motion tween otherwise

if GuiService.ReducedMotionEnabled then

	-- Initially set canvas group to fully transparent (invisible)

	canvasGroup.GroupTransparency = 1

	-- Fade in canvas group

	tween = TweenService:Create(canvasGroup, tweenInfo, {GroupTransparency = 0})

else

	-- Initially set canvas group off screen

	canvasGroup.Position = UDim2.fromScale(0, -1)

	-- Move canvas group on screen

	tween = TweenService:Create(canvasGroup, tweenInfo, {Position = UDim2.fromScale(0, 0)})

end

tween:Play()

```

## [Volume controls](#volume-controls)[](#volume-controls)

Different sounds playing at the same time can be overwhelming, distracting, or difficult to distinguish. Providing users with volume controls for different "groups" of audio such as sound effects, music, and speech lets them customize their game and focus on what they need to.

Consider the following example of a very noisy game where the user is able to modify music and sound effect volumes separately.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
