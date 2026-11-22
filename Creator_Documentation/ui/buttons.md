<!-- Source: https://create.roblox.com/docs/en-us/ui/buttons -->

Text & image buttons | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/ui/buttons.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [User interface](/docs/en-us/ui)
6. /
7. UI objects

# Text & image buttons

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/ui/buttons.md)

[GuiButtons](/docs/en-us/reference/engine/classes/GuiButton)  are [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject)  that allow players to perform an action. You can customize these buttons to provide context and feedback, such as changing the visual appearance or [scripting](#script-buttons)  audible feedback when a player interacts with a button.

There are two types of buttons which you can place [on‑screen](/docs/en-us/ui/on-screen-containers)  or [in‑game](/docs/en-us/ui/in-experience-containers) :

-

A [TextButton](/docs/en-us/reference/engine/classes/TextButton)  is a rectangle with text that triggers the [Activated](/docs/en-us/reference/engine/classes/GuiButton#Activated)  and/or [SecondaryActivated](/docs/en-us/reference/engine/classes/GuiButton#SecondaryActivated)  event on click/tap.

-

An [ImageButton](/docs/en-us/reference/engine/classes/ImageButton)  is a rectangle with an image that triggers the [Activated](/docs/en-us/reference/engine/classes/GuiButton#Activated)  and/or [SecondaryActivated](/docs/en-us/reference/engine/classes/GuiButton#SecondaryActivated)  event on click/tap. It features additional states for swapping the image on player hover or press.

## [Buttons on the screen](#buttons-on-the-screen)[](#buttons-on-the-screen)

Buttons [on the screen](/docs/en-us/ui/on-screen-containers)  are useful to quickly guide players to various menus or pages. To add this type of button:

1.

In the [Explorer](/docs/en-us/studio/explorer)  window, hover over [StarterGui](/docs/en-us/reference/engine/classes/StarterGui) , click the ⊕ button, and insert a [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui) .

2.

Hover over the new [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui) , click the ⊕ button, and insert either a [TextButton](/docs/en-us/reference/engine/classes/TextButton)  or [ImageButton](/docs/en-us/reference/engine/classes/ImageButton) .

 ![](https://prod.docsiteassets.roblox.com/assets/ui/button-text-input/ImageButton-Screen-New.jpg)

## [Buttons on part faces](#buttons-on-part-faces)[](#buttons-on-part-faces)

Buttons on a part are useful for allowing players to interact with parts. For example, you can let players step on a button to complete an action.

To add a button to the face of a part:

1.

In the [Explorer](/docs/en-us/studio/explorer)  window, hover over the part , click the ⊕ button, and insert a [SurfaceGui](/docs/en-us/reference/engine/classes/SurfaceGui) .

2.

Hover over the new [SurfaceGui](/docs/en-us/reference/engine/classes/SurfaceGui) , click the ⊕ button, and insert either a [TextButton](/docs/en-us/reference/engine/classes/TextButton)  or [ImageButton](/docs/en-us/reference/engine/classes/ImageButton) .

 ![](https://prod.docsiteassets.roblox.com/assets/ui/button-text-input/ImageButton-SurfaceGui-New.jpg)

If you don't see the button, try choosing a different face ([Top](/docs/en-us/reference/engine/enums/NormalId#Top) , [Bottom](/docs/en-us/reference/engine/enums/NormalId#Bottom) , [Front](/docs/en-us/reference/engine/enums/NormalId#Front) , [Back](/docs/en-us/reference/engine/enums/NormalId#Back) , [Left](/docs/en-us/reference/engine/enums/NormalId#Left) , or [Right](/docs/en-us/reference/engine/enums/NormalId#Right) ) for the [Face](/docs/en-us/reference/engine/classes/SurfaceGui#Face)  property of the [SurfaceGui](/docs/en-us/reference/engine/classes/SurfaceGui) .

## [Button appearance](#button-appearance)[](#button-appearance)

Both [TextButton](/docs/en-us/reference/engine/classes/TextButton)  and [ImageButton](/docs/en-us/reference/engine/classes/ImageButton)  inherit from [GuiObject](/docs/en-us/reference/engine/classes/GuiObject)  which contains properties like [BackgroundColor3](/docs/en-us/reference/engine/classes/GuiObject#BackgroundColor3) , [Rotation](/docs/en-us/reference/engine/classes/GuiObject#Rotation) , and [Size](/docs/en-us/reference/engine/classes/GuiObject#Size) . Buttons also accept the [appearance modifiers](/docs/en-us/ui/appearance-modifiers)  common to most UI objects.

Unique to [TextButton](/docs/en-us/reference/engine/classes/TextButton)  are various properties to change its visual appearance:

-

[FontFace](/docs/en-us/reference/engine/classes/TextButton#FontFace)  — The font used to render text.

-

[Text](/docs/en-us/reference/engine/classes/TextButton#Text)  — The text string rendered on the button.

-

[TextSize](/docs/en-us/reference/engine/classes/TextButton#TextSize)  — The line height of text in offsets.

-

[TextColor3](/docs/en-us/reference/engine/classes/TextButton#TextColor3)  — Color of the rendered text.

An [ImageButton](/docs/en-us/reference/engine/classes/ImageButton)  has several properties to change its visual appearance, including hover and pressed image variants to indicate a player's interaction with the button:

-

[Image](/docs/en-us/reference/engine/classes/ImageButton#Image)  — The image that displays when a player is not interacting with the [ImageButton](/docs/en-us/reference/engine/classes/ImageButton) .

-

[HoverImage](/docs/en-us/reference/engine/classes/ImageButton#HoverImage)  — The image that displays when a player is hovering their cursor over the [ImageButton](/docs/en-us/reference/engine/classes/ImageButton) .

-

[PressedImage](/docs/en-us/reference/engine/classes/ImageButton#PressedImage)  — The image that displays when a player clicks/taps the [ImageButton](/docs/en-us/reference/engine/classes/ImageButton) .

![](https://prod.docsiteassets.roblox.com/assets/ui/button-text-input/ImageButton-State-Normal.png) Normal

![](https://prod.docsiteassets.roblox.com/assets/ui/button-text-input/ImageButton-State-Hover.png) Hover

![](https://prod.docsiteassets.roblox.com/assets/ui/button-text-input/ImageButton-State-Pressed.png) Pressed

## [Script buttons](#script-buttons)[](#script-buttons)

You can script an action when a player presses a button by connecting the button to the [GuiButton.Activated](/docs/en-us/reference/engine/classes/GuiButton#Activated)  event, or to [GuiButton.SecondaryActivated](/docs/en-us/reference/engine/classes/GuiButton#SecondaryActivated)  for cross‑platform secondary input like right‑click on desktop and long press on mobile. For example, when you parent the following [LocalScript](/docs/en-us/reference/engine/classes/LocalScript)  to a button, the button changes to a random color every time a player clicks/taps it.

```

local button = script.Parent

local RNG = Random.new()

local function onButtonActivated()

	-- Randomize the button color

	button.BackgroundColor3 = Color3.fromHSV(RNG:NextNumber(), 1, 1)

end

button.Activated:Connect(onButtonActivated)

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
