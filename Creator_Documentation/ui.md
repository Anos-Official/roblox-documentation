<!-- Source: https://create.roblox.com/docs/en-us/ui -->

User interface | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/ui.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [User interface](/docs/en-us/ui)

# User interface

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/ui/index.md)

You can quickly create high-quality graphical user interfaces with minimal scripting requirements using built-in [UI objects](#ui-objects) . Depending on where you create it, UI renders either [on-screen](#on-screen-ui)  or [within a game's 3D world](#in-game-ui) .

## [On-screen UI](#on-screen-ui)[](#on-screen-ui)

[On-screen containers](/docs/en-us/ui/on-screen-containers)  hold UI objects that you want to display on a player's screen, including [frames](/docs/en-us/ui/frames) , [labels](/docs/en-us/ui/labels) , [buttons](/docs/en-us/ui/buttons) , and more. All on-screen UI objects and code are stored and changed on the client.

![Example ScreenGui with various GuiObject children, including a Frame, TextLabel, TextBox, and ImageButton.](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/ScreenGui-Example.jpg)

## [In-game UI](#in-game-ui)[](#in-game-ui)

[In-game containers](/docs/en-us/ui/in-experience-containers)  such as [SurfaceGuis](/docs/en-us/reference/engine/classes/SurfaceGui)  and [BillboardGuis](/docs/en-us/reference/engine/classes/BillboardGui)  hold UI objects that you want to display within your game's 3D world.

## [UI objects](#ui-objects)[](#ui-objects)

Most UI elements are [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject) , 2D graphical user interface objects that you can parent to containers. The four most common are [frames](/docs/en-us/ui/frames) , [labels](/docs/en-us/ui/labels) , [buttons](/docs/en-us/ui/buttons) , and [text input](/docs/en-us/ui/text-input)  objects.

 ![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/ScreenGui-Example.jpg)

| Object | | Description |
| --- | --- |
| [Frame](/docs/en-us/ui/frames) | | [Frames](/docs/en-us/reference/engine/classes/Frame)  act as containers for other UI objects. When you manipulate frames, you also manipulate the objects they contain. |
| [Label](/docs/en-us/ui/labels) | | [TextLabel](/docs/en-us/reference/engine/classes/TextLabel)  and [ImageLabel](/docs/en-us/reference/engine/classes/ImageLabel)  objects allow you to display customizable text and images. |
| [Button](/docs/en-us/ui/buttons) | | [TextButton](/docs/en-us/reference/engine/classes/TextButton)  and [ImageButton](/docs/en-us/reference/engine/classes/ImageButton)  objects allow users to prompt an action. |
| [Text Input](/docs/en-us/ui/text-input) | | [TextBox](/docs/en-us/reference/engine/classes/TextBox)  objects allow users to input text. |

Using the [Position](/docs/en-us/reference/engine/classes/GuiObject#Position) , [Size](/docs/en-us/reference/engine/classes/GuiObject#Size) , [AnchorPoint](/docs/en-us/reference/engine/classes/GuiObject#AnchorPoint) , and [ZIndex](/docs/en-us/reference/engine/classes/GuiObject#ZIndex)  properties, you have complete control on how to [position](/docs/en-us/ui/position-and-size#position) , [size](/docs/en-us/ui/position-and-size#size) , and [layer](/docs/en-us/ui/position-and-size#zindex)  [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject) . You can also use [tweening](/docs/en-us/ui/animation)  to transition a [GuiObject](/docs/en-us/reference/engine/classes/GuiObject)  smoothly from one state to another and provide dynamic visual feedback.

## [Layout and design](#layout-and-design)[](#layout-and-design)

Beyond basic properties for adjusting position and size, Roblox also provides layout structures like [list/flex](/docs/en-us/ui/list-flex-layouts)  and [grid](/docs/en-us/ui/grid-table-layouts) , as well as [size modifiers](/docs/en-us/ui/size-modifiers)  and [appearance modifiers](/docs/en-us/ui/appearance-modifiers) .

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIListLayout-Example.png)[UIListLayout](/docs/en-us/reference/engine/classes/UIListLayout)  for horizontal or vertical item sequences

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-Color-Solid.png)[UIStroke](/docs/en-us/reference/engine/classes/UIStroke)  on [TextLabel](/docs/en-us/reference/engine/classes/TextLabel)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-Color-Gradient.png)[UIStroke](/docs/en-us/reference/engine/classes/UIStroke)  with [UIGradient](/docs/en-us/reference/engine/classes/UIGradient)

## [Universal styling](#universal-styling)[](#universal-styling)

[Universal styling](/docs/en-us/ui/styling)  is a Roblox solution to stylesheets, similar to CSS, that lets you declare and globally apply overrides to UI instance properties. This engine‑level support is the foundation for the [Style Editor](/docs/en-us/ui/styling/editor)  and the end‑to‑end token pipeline.

## [Interactive frameworks](#interactive-frameworks)[](#interactive-frameworks)

In addition to the core [user interface objects](#ui-objects) , the following frameworks provide built‑in and customizable interactivity for your games.

### [Proximity prompts](#proximity-prompts)[](#proximity-prompts)

[Proximity prompts](/docs/en-us/ui/proximity-prompts)  are unique built-in UI objects which prompt user interaction to trigger an action when they approach in-game objects such as doors, light switches, and buttons.

### [UI drag detectors](#ui-drag-detectors)[](#ui-drag-detectors)

[UI drag detectors](/docs/en-us/ui/ui-drag-detectors)  facilitate and encourage interaction with 2D user interface elements such as sliders, spinners, and more.

### [3D drag detectors](#3d-drag-detectors)[](#3d-drag-detectors)

[3D drag detectors](/docs/en-us/ui/3D-drag-detectors)  encourage physical interaction with 3D objects in a game, such as opening doors and drawers, sliding a part around, grabbing and tossing a bowling ball, pulling back and firing a slingshot, and much more.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
