<!-- Source: https://create.roblox.com/docs/en-us/ui/scrolling-frames -->

Scrolling frames | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/ui/scrolling-frames.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [User interface](/docs/en-us/ui)
6. /
7. UI objects

# Scrolling frames

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/ui/scrolling-frames.md)

A [ScrollingFrame](/docs/en-us/reference/engine/classes/ScrollingFrame)  consists of a customizable canvas  and scroll bars  with built‑in scrolling interactivity and different ways to customize how the scrolling works. [ScrollingFrame](/docs/en-us/reference/engine/classes/ScrollingFrame)  is ideal for displaying a lot of information in a confined space and it works well with [list](/docs/en-us/ui/list-flex-layouts)  and [grid](/docs/en-us/ui/grid-table-layouts)  layouts.

 ![Example ScrollingFrame on the screen containing a tabbed category bar and a list of magical items for the player to consider purchasing.](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/ScrollingFrame-Example.jpg)

## [Canvas](#canvas)[](#canvas)

The canvas  is the primary area of a [ScrollingFrame](/docs/en-us/reference/engine/classes/ScrollingFrame)  that can contain other [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject) . Scrolling behavior automatically adapts in the following scenarios:

| Frame Setup | | Result |
| --- | --- |
| The frame's [CanvasSize](/docs/en-us/reference/engine/classes/ScrollingFrame#CanvasSize)  is taller than its overall height; specifically the total [CanvasSize.Y](/docs/en-us/reference/engine/classes/ScrollingFrame#CanvasSize)  exceeds the total [Size.Y](/docs/en-us/reference/engine/classes/ScrollingFrame#Size) . | | Vertical scrolling is enabled and a vertical scroll bar appears. |
| The frame's [CanvasSize](/docs/en-us/reference/engine/classes/ScrollingFrame#CanvasSize)  is wider than its overall width; specifically the total [CanvasSize.X](/docs/en-us/reference/engine/classes/ScrollingFrame#CanvasSize)  exceeds the total [Size.X](/docs/en-us/reference/engine/classes/ScrollingFrame#Size) . | | Horizontal scrolling is enabled and a horizontal scroll bar appears. |
| The frame's [AutomaticCanvasSize](/docs/en-us/reference/engine/classes/ScrollingFrame#AutomaticCanvasSize)  is set to [Y](/docs/en-us/reference/engine/enums/AutomaticSize)  or [XY](/docs/en-us/reference/engine/enums/AutomaticSize)  and the total height of its contents (child [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject) ) exceed its total [Size.Y](/docs/en-us/reference/engine/classes/ScrollingFrame#Size) . | | Vertical scrolling is enabled and a vertical scroll bar appears. |
| The frame's [AutomaticCanvasSize](/docs/en-us/reference/engine/classes/ScrollingFrame#AutomaticCanvasSize)  is set to [X](/docs/en-us/reference/engine/enums/AutomaticSize)  or [XY](/docs/en-us/reference/engine/enums/AutomaticSize)  and the total width of its contents (child [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject) ) exceed its total [Size.X](/docs/en-us/reference/engine/classes/ScrollingFrame#Size) . | | Horizontal scrolling is enabled and a horizontal scroll bar appears. |

The [CanvasPosition](/docs/en-us/reference/engine/classes/ScrollingFrame#CanvasPosition)  property reflects the current  positional offset of the canvas within the frame, in pixels, and it sets the position of scroll bars accordingly. Note that this property doesn't do anything if scroll bars aren't visible.

## [Insets](#insets)[](#insets)

A scrolling frame's [CanvasSize](/docs/en-us/reference/engine/classes/ScrollingFrame#CanvasSize)  may be affected by the [VerticalScrollBarInset](/docs/en-us/reference/engine/classes/ScrollingFrame#VerticalScrollBarInset)  and/or [HorizontalScrollBarInset](/docs/en-us/reference/engine/classes/ScrollingFrame#HorizontalScrollBarInset)  properties. In the following example diagram, a vertically scrolling frame uses a canvas width of 100%. With [VerticalScrollBarInset](/docs/en-us/reference/engine/classes/ScrollingFrame#VerticalScrollBarInset)  set to [None](/docs/en-us/reference/engine/enums/ScrollBarInset)  (default), the canvas extends to the full width of the scrolling frame, obscuring a slight amount of content under the scroll bar. In contrast, a [VerticalScrollBarInset](/docs/en-us/reference/engine/classes/ScrollingFrame#VerticalScrollBarInset)  setting of either [Always](/docs/en-us/reference/engine/enums/ScrollBarInset)  or [ScrollBar](/docs/en-us/reference/engine/enums/ScrollBarInset)  insets the canvas by the [ScrollBarThickness](/docs/en-us/reference/engine/classes/ScrollingFrame#ScrollBarThickness)  amount so that the canvas meets edge‑to‑edge with the scroll bar.

None (Default) Always / ScrollBar

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/ScrollingFrame-Canvas-No-Inset.png)

## [Scroll bars](#scroll-bars)[](#scroll-bars)

The frame's scroll bars  reflect the current canvas position and provide automatic drag‑to‑scroll interactivity. For vertical scroll bars, the [VerticalScrollBarPosition](/docs/en-us/reference/engine/classes/ScrollingFrame#VerticalScrollBarPosition)  property switches the bar's position to either the left or right of the canvas, but horizontal scroll bars can only be positioned below the canvas.

Scroll bar construction consists of three asset properties:

-

[TopImage](/docs/en-us/reference/engine/classes/ScrollingFrame#TopImage)  — Displays on the top of a vertical scroll bar, or the left of a horizontal scroll bar (rotated 90° counterclockwise for a horizontal scroll bar).

-

[MidImage](/docs/en-us/reference/engine/classes/ScrollingFrame#MidImage)  — Spans the area between [TopImage](/docs/en-us/reference/engine/classes/ScrollingFrame#TopImage)  and [BottomImage](/docs/en-us/reference/engine/classes/ScrollingFrame#BottomImage)  (rotated 90° counterclockwise for a horizontal scroll bar).

-

[BottomImage](/docs/en-us/reference/engine/classes/ScrollingFrame#BottomImage)  — Displays on the bottom of a vertical scroll bar, or the right of a horizontal scroll bar (rotated 90° counterclockwise for a horizontal scroll bar).

 ![Diagram showing the three image asset elements which construct a scrolling frame's scroll bar.](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/ScrollingFrame-Scroll-Bar-Elements.png)

Each image scales based on the [ScrollBarThickness](/docs/en-us/reference/engine/classes/ScrollingFrame#ScrollBarThickness)  property which changes the width of a vertical scroll bar or the height of a horizontal scroll bar.

Additional visual modifications can be made through the [ScrollBarImageColor3](/docs/en-us/reference/engine/classes/ScrollingFrame#ScrollBarImageColor3)  and [ScrollBarImageTransparency](/docs/en-us/reference/engine/classes/ScrollingFrame#ScrollBarImageTransparency)  properties which tint the bar's image assets and modify its opacity, respectively.

## [Clipping](#clipping)[](#clipping)

By default, [GuiObject](/docs/en-us/reference/engine/classes/GuiObject)  containers clip  their content (descendant [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject) ) through the [ClipsDescendants](/docs/en-us/reference/engine/classes/GuiObject#ClipsDescendants)  boolean. If you want descendants to appear outside of a container's bounds, simply set [ClipsDescendants](/docs/en-us/reference/engine/classes/GuiObject#ClipsDescendants)  to false .

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/ClipsDescendants-On.png)[ClipsDescendants](/docs/en-us/reference/engine/classes/GuiObject#ClipsDescendants)  = true

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/ClipsDescendants-Off.png)[ClipsDescendants](/docs/en-us/reference/engine/classes/GuiObject#ClipsDescendants)  = false

Importantly, [StarterGui.ClipsDescendantsSupportsRotation](/docs/en-us/reference/engine/classes/StarterGui#ClipsDescendantsSupportsRotation)  must be true  for clipping to work on rotated  descendants (non‑zero [Rotation](/docs/en-us/reference/engine/classes/GuiObject#Rotation) ) within the container. However, clipping by  a rotated container (clipping container itself is rotated) or by rounded corners ([UICorner](/docs/en-us/reference/engine/classes/UICorner) ) is not supported. If you need clipping on rotated or rounded containers, consider [CanvasGroup](/docs/en-us/reference/engine/classes/CanvasGroup) .

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Clipping-Descendants-Rotated.png)[ClipsDescendants](/docs/en-us/reference/engine/classes/GuiObject#ClipsDescendants)  = true
[Rotation](/docs/en-us/reference/engine/classes/GuiObject#Rotation)  = 0

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Clipping-Parent-Rotated.png)[ClipsDescendants](/docs/en-us/reference/engine/classes/GuiObject#ClipsDescendants)  = true
[Rotation](/docs/en-us/reference/engine/classes/GuiObject#Rotation)  = 10

## [Elasticity](#elasticity)[](#elasticity)

By default, [ScrollingFrames](/docs/en-us/reference/engine/classes/ScrollingFrame)  exhibit elastic scrolling behavior on touch‑enabled devices, meaning that users can drag the canvas slightly further than its bounds and, upon release, the canvas will spring back to its minimum or maximum limit. If you want to remove the elastic behavior completely and ensure the canvas never scrolls past its limits, set the [ElasticBehavior](/docs/en-us/reference/engine/classes/ScrollingFrame#ElasticBehavior)  property to [Never](/docs/en-us/reference/engine/enums/ElasticBehavior) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
