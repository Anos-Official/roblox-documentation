<!-- Source: https://create.roblox.com/docs/en-us/ui/size-modifiers -->

Size modifiers and constraints | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/ui/size-modifiers.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [User interface](/docs/en-us/ui)

# Size modifiers and constraints

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/ui/size-modifiers.md)

Alongside basic [sizing](/docs/en-us/ui/position-and-size)  of UI objects, you can utilize size modifiers to [scale](#scale)  an object proportionally or [automatically resize](#automatic-sizing)  it. You can also insert [size constraints](#constraints)  to control aspect ratio , or set a minimum and maximum size  or text size .

## [Scale](#scale)[](#scale)

A [UIScale](/docs/en-us/reference/engine/classes/UIScale)  object stores a numerical value that multiplies the [AbsoluteSize](/docs/en-us/reference/engine/classes/GuiBase2d#AbsoluteSize)  property of the parent [GuiObject](/docs/en-us/reference/engine/classes/GuiObject) . For example, if you want an object to be twice as large as it currently is, you can insert a [UIScale](/docs/en-us/reference/engine/classes/UIScale)  object with a [Scale](/docs/en-us/reference/engine/classes/UIScale#Scale)  property of 2 .

This modifier is useful for "zooming in" while designing a detailed user interface in Studio, since it proportionally scales the object and all of its children, including any applied [appearance modifiers](/docs/en-us/ui/appearance-modifiers)  like [UIStroke](/docs/en-us/reference/engine/classes/UIStroke)  or [UICorner](/docs/en-us/reference/engine/classes/UICorner) . It's also useful to [tween](/docs/en-us/ui/animation)  the size of an object, for example to slightly increase the size of a button when a player hovers their mouse over it.

 ![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIScale-Example.png)

## [Automatic sizing](#automatic-sizing)[](#automatic-sizing)

The [AutomaticSize](/docs/en-us/reference/engine/classes/GuiObject#AutomaticSize)  property automatically resizes a parent [GuiObject](/docs/en-us/reference/engine/classes/GuiObject)  to the size of its descendants. You can use this property in a variety of cases, including:

-

Expanding a [GuiObject](/docs/en-us/reference/engine/classes/GuiObject)  to fit text that has been [localized](/docs/en-us/production/localization)  in many languages.

-

Allowing users to [input text](/docs/en-us/ui/text-input)  within a [TextBox](/docs/en-us/reference/engine/classes/TextBox) , automatically adjusting its size based on the amount of text entered.

-

Automatically adjusting the size of text objects using [rich text markup](/docs/en-us/ui/rich-text) , including font type and size.

You can enable the [AutomaticSize](/docs/en-us/reference/engine/classes/GuiObject#AutomaticSize)  property for any [GuiObject](/docs/en-us/reference/engine/classes/GuiObject) . By default, it is set to [None](/docs/en-us/reference/engine/enums/AutomaticSize) , but you can change its value to have specific control over which direction(s) the [GuiObject](/docs/en-us/reference/engine/classes/GuiObject)  resizes to fit its content.

[ScrollingFrame](/docs/en-us/reference/engine/classes/ScrollingFrame)  uses the [AutomaticCanvasSize](/docs/en-us/reference/engine/classes/ScrollingFrame#AutomaticCanvasSize)  property instead of [AutomaticSize](/docs/en-us/reference/engine/classes/GuiObject#AutomaticSize) . It behaves the same but resizes the frame's [CanvasSize](/docs/en-us/reference/engine/classes/ScrollingFrame#CanvasSize) , not its base [Size](/docs/en-us/reference/engine/classes/GuiObject#Size) .

To enable automatic sizing:

1.

In the [Explorer](/docs/en-us/studio/explorer)  window, click any [GuiObject](/docs/en-us/reference/engine/classes/GuiObject) , such as a [Frame](/docs/en-us/reference/engine/classes/Frame) , [TextBox](/docs/en-us/reference/engine/classes/TextBox) , or [ImageLabel](/docs/en-us/reference/engine/classes/ImageLabel) .

2.

In the [Properties](/docs/en-us/studio/properties)  window, navigate to the [AutomaticSize](/docs/en-us/reference/engine/classes/GuiObject#AutomaticSize)  property ([AutomaticCanvasSize](/docs/en-us/reference/engine/classes/ScrollingFrame#AutomaticCanvasSize)  for [ScrollingFrame](/docs/en-us/reference/engine/classes/ScrollingFrame) ) and set it to one of the following options:

-

[X](/docs/en-us/reference/engine/enums/AutomaticSize)  — Resizes content horizontally.

-

[Y](/docs/en-us/reference/engine/enums/AutomaticSize)  — Resizes content vertically.

-

[XY](/docs/en-us/reference/engine/enums/AutomaticSize)  — Resizes content both horizontally and vertically.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/GuiObject-AutomaticSize.png)

Once automatic sizing is set, note that other object properties behave as follows:

AnchorPoint Size TextWrapped

Similar to the concept of [sizing](/docs/en-us/ui/position-and-size#size)  an object, [AutomaticSize](/docs/en-us/reference/engine/classes/GuiObject#AutomaticSize)  takes the [AnchorPoint](/docs/en-us/reference/engine/classes/GuiObject#AnchorPoint)  property into consideration when resizing content. For example, the following video displays three [TextLabels](/docs/en-us/reference/engine/classes/TextLabel)  that automatically resize from their anchor point.

-

The top label has an [AnchorPoint](/docs/en-us/reference/engine/classes/GuiObject#AnchorPoint)  value of [(0, 0.5)](/docs/en-us/reference/engine/datatypes/Vector2#new)  which anchors it to the middle of the left side.

-

The middle label has an [AnchorPoint](/docs/en-us/reference/engine/classes/GuiObject#AnchorPoint)  value of [(0.5, 0.5)](/docs/en-us/reference/engine/datatypes/Vector2#new)  which anchors it to the center.

-

The bottom label has an [AnchorPoint](/docs/en-us/reference/engine/classes/GuiObject#AnchorPoint)  value of [(1, 0.5)](/docs/en-us/reference/engine/datatypes/Vector2#new)  which anchors it to the middle of the right side.

## [Constraints](#constraints)[](#constraints)

There are three types of constraints  you can use for a user interface object: [size](#size) , [text size](#text-size) , and [aspect ratio](#aspect-ratio) . To use a constraint, you must set it as a child  of the [GuiObject](/docs/en-us/reference/engine/classes/GuiObject)  you want to constrain.

### [Size](#size)[](#size)

The [UISizeConstraint](/docs/en-us/reference/engine/classes/UISizeConstraint)  specifies a minimum and maximum size for a [GuiObject](/docs/en-us/reference/engine/classes/GuiObject) . This constraint ensures that the [GuiObject](/docs/en-us/reference/engine/classes/GuiObject)  doesn't become too small or large on different screen sizes.

For example, if you set the [MinSize](/docs/en-us/reference/engine/classes/UISizeConstraint#MinSize)  property to (200, 200)  and the [MaxSize](/docs/en-us/reference/engine/classes/UISizeConstraint#MaxSize)  property to (400, 400) , the [GuiObject](/docs/en-us/reference/engine/classes/GuiObject)  cannot scale smaller than 200×200 pixels or larger than 400×400 pixels.

When a UI object is under control of both a layout structure such as [UIListLayout](/docs/en-us/reference/engine/classes/UIListLayout)  and a [UISizeConstraint](/docs/en-us/reference/engine/classes/UISizeConstraint) , the constraint will override  the layout and control the object's size.

### [Text size](#text-size)[](#text-size)

The [UITextSizeConstraint](/docs/en-us/reference/engine/classes/UITextSizeConstraint)  specifies a minimum and maximum font size for a [GuiObject](/docs/en-us/reference/engine/classes/GuiObject)  with text, such as a [TextLabel](/docs/en-us/reference/engine/classes/TextLabel) , [TextButton](/docs/en-us/reference/engine/classes/TextButton) , or [TextBox](/docs/en-us/reference/engine/classes/TextBox) . This constraint ensures that the text  within a [GuiObject](/docs/en-us/reference/engine/classes/GuiObject)  doesn't become illegible or too large.

If you enable the [TextScaled](/docs/en-us/reference/engine/classes/TextLabel#TextScaled)  property of the parent [GuiObject](/docs/en-us/reference/engine/classes/GuiObject) , the text size scales with the container's size and respects constraints even if the object becomes smaller or larger than the [MinTextSize](/docs/en-us/reference/engine/classes/UITextSizeConstraint#MinTextSize)  and [MaxTextSize](/docs/en-us/reference/engine/classes/UITextSizeConstraint#MaxTextSize)  values.

For example, the following [TextLabel](/docs/en-us/reference/engine/classes/TextLabel)  object has a [UITextSizeConstraint](/docs/en-us/reference/engine/classes/UITextSizeConstraint)  with a [MinTextSize](/docs/en-us/reference/engine/classes/UITextSizeConstraint#MinTextSize)  value of 50  and a MaxTextSize value of 80 . Even when the [TextLabel](/docs/en-us/reference/engine/classes/TextLabel)  becomes smaller, the font never becomes smaller than 50 pixels, and when the object becomes large, the font next exceeds 80 pixels.

Do not use [MinTextSize](/docs/en-us/reference/engine/classes/UITextSizeConstraint#MinTextSize)  property values lower than 9  or the text will be difficult to read for many viewers.

### [Aspect ratio](#aspect-ratio)[](#aspect-ratio)

The [UIAspectRatioConstraint](/docs/en-us/reference/engine/classes/UIAspectRatioConstraint)  enforces a width‑to‑height  aspect ratio on a [GuiObject](/docs/en-us/reference/engine/classes/GuiObject)  regardless of its core size, even if that size is set as a percentage of its parent. For example, inserting this constraint as a child of a [Frame](/docs/en-us/reference/engine/classes/Frame)  and setting the constraint's [AspectRatio](/docs/en-us/reference/engine/classes/UIAspectRatioConstraint#AspectRatio)  property to 2  (2:1 ) keeps the frame's width at twice that of its height. Similarly, setting this constraint's [AspectRatio](/docs/en-us/reference/engine/classes/UIAspectRatioConstraint#AspectRatio)  property to 0.5  (0.5:1 ) keeps the frame's width at half that of its height.

Setting this constraint's [AspectRatio](/docs/en-us/reference/engine/classes/UIAspectRatioConstraint#AspectRatio)  to the default of 1  (1:1 ) is a convenient way to prevent non‑proportional scaling/stretching of an [ImageLabel](/docs/en-us/reference/engine/classes/ImageLabel)  with a square image asset, such as an [avatar thumbnail](/docs/en-us/projects/assets#rbxthumb) .

When a UI object is under control of both a layout structure such as [UIListLayout](/docs/en-us/reference/engine/classes/UIListLayout)  and a [UIAspectRatioConstraint](/docs/en-us/reference/engine/classes/UIAspectRatioConstraint) , the constraint will override  the layout and control the object's size.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
