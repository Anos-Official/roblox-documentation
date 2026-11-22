<!-- Source: https://create.roblox.com/docs/en-us/ui/frames -->

Frames | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/ui/frames.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [User interface](/docs/en-us/ui)
6. /
7. UI objects

# Frames

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/ui/frames.md)

Basic [Frames](/docs/en-us/reference/engine/classes/Frame)  act as containers for other [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject)  such as [labels](/docs/en-us/ui/labels)  and [buttons](/docs/en-us/ui/buttons) . You can apply frames to display on a user's [screen](/docs/en-us/ui/on-screen-containers)  or on a [surface](/docs/en-us/ui/in-experience-containers)  within the game.

 ![Example Frame on the screen containing a TextLabel, TextBox, and ImageButton.](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/Frame-Example.jpg)

Frames are ideal containers for responsive layouts such as [list and flex layouts](/docs/en-us/ui/list-flex-layouts) , allowing you to change the size of the frame and dynamically adjust how layout items fit within it. [Frames](/docs/en-us/reference/engine/classes/Frame)  are also core [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject) , so you can customize properties such as [BackgroundColor3](/docs/en-us/reference/engine/classes/GuiObject#BackgroundColor3) , [Transparency](/docs/en-us/reference/engine/classes/GuiObject#Transparency) , apply a [background gradient](/docs/en-us/ui/appearance-modifiers#gradient)  or [border](/docs/en-us/ui/appearance-modifiers#stroke) , and more.

Aside from their common use as containers, you can also use [Frames](/docs/en-us/reference/engine/classes/Frame)  for UI design. For example, as a visual separator between other UI elements, you can scale a frame to be thin and long until it becomes a line.

See also [scrolling frames](/docs/en-us/ui/scrolling-frames) , [viewport frames](/docs/en-us/ui/viewport-frames) , and [video frames](/docs/en-us/ui/video-frames)  as specialty frame types with unique built‑in capabilities.

## [Clipping](#clipping)[](#clipping)

By default, [GuiObject](/docs/en-us/reference/engine/classes/GuiObject)  containers clip  their content (descendant [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject) ) through the [ClipsDescendants](/docs/en-us/reference/engine/classes/GuiObject#ClipsDescendants)  boolean. If you want descendants to appear outside of a container's bounds, simply set [ClipsDescendants](/docs/en-us/reference/engine/classes/GuiObject#ClipsDescendants)  to false .

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/ClipsDescendants-On.png)[ClipsDescendants](/docs/en-us/reference/engine/classes/GuiObject#ClipsDescendants)  = true

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/ClipsDescendants-Off.png)[ClipsDescendants](/docs/en-us/reference/engine/classes/GuiObject#ClipsDescendants)  = false

Importantly, [StarterGui.ClipsDescendantsSupportsRotation](/docs/en-us/reference/engine/classes/StarterGui#ClipsDescendantsSupportsRotation)  must be true  for clipping to work on rotated  descendants (non‑zero [Rotation](/docs/en-us/reference/engine/classes/GuiObject#Rotation) ) within the container. However, clipping by  a rotated container (clipping container itself is rotated) or by rounded corners ([UICorner](/docs/en-us/reference/engine/classes/UICorner) ) is not supported. If you need clipping on rotated or rounded containers, consider [CanvasGroup](/docs/en-us/reference/engine/classes/CanvasGroup) .

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Clipping-Descendants-Rotated.png)[ClipsDescendants](/docs/en-us/reference/engine/classes/GuiObject#ClipsDescendants)  = true
[Rotation](/docs/en-us/reference/engine/classes/GuiObject#Rotation)  = 0

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Clipping-Parent-Rotated.png)[ClipsDescendants](/docs/en-us/reference/engine/classes/GuiObject#ClipsDescendants)  = true
[Rotation](/docs/en-us/reference/engine/classes/GuiObject#Rotation)  = 10

## [Automatic sizing](#automatic-sizing)[](#automatic-sizing)

Frames can be set to [automatically size](/docs/en-us/ui/size-modifiers#automatic-sizing)  depending on their content. To achieve this, set the frame's [Size](/docs/en-us/reference/engine/classes/Frame#Size)  to the minimum  width and/or height, then set its [AutomaticSize](/docs/en-us/reference/engine/classes/Frame#AutomaticSize)  property to either [X](/docs/en-us/reference/engine/enums/AutomaticSize) , [Y](/docs/en-us/reference/engine/enums/AutomaticSize) , or [XY](/docs/en-us/reference/engine/enums/AutomaticSize)  depending on which axes automatic sizing should apply to. Once set, the frame will automatically resize based on the size of [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject)  and layouts within it.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
