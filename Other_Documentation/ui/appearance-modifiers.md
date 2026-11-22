<!-- Source: https://create.roblox.com/docs/ui/appearance-modifiers -->

UI appearance modifiers | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/ui/appearance-modifiers.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [User interface](/docs/ui)

# UI appearance modifiers

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/ui/appearance-modifiers.md)

By utilizing appearance modifiers , you can further customize the appearance of your [GuiObjects](/docs/reference/engine/classes/GuiObject) .

-

Apply a [gradient](#gradient)  to the background of an object.

-

Apply a [stroke](#stroke)  to text or a border.

-

Set [rounded corners](#corners)  for an object.

-

Increase [padding](#padding)  between the borders of an object.

-

Add a [drop shadow](#shadow)  behind an object.

## [Gradient](#gradient)[](#gradient)

The [UIGradient](/docs/reference/engine/classes/UIGradient)  object applies a color and transparency gradient to its parent [GuiObject](/docs/reference/engine/classes/GuiObject) .

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Example.png)

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/UIGradient.png)

You can configure the gradient by:

-

Setting its [colors](#color-sequence)  through a [ColorSequence](/docs/reference/engine/datatypes/ColorSequence)  in the gradient's [Color](/docs/reference/engine/classes/UIGradient#Color)  property.

-

Setting its [transparency](#transparency)  through a [NumberSequence](/docs/reference/engine/datatypes/NumberSequence)  in the gradient's [Transparency](/docs/reference/engine/classes/UIGradient#Transparency)  property.

-

Choosing the gradient's [type](#type)  through the [Type](/docs/reference/engine/classes/UIGradient#Type)  property.

-

Choosing the gradient's [starting point](#offset-and-rotation)  (inside or outside the parent's bounds) through the [Offset](/docs/reference/engine/classes/UIGradient#Offset)  property.

-

Choosing the gradient's [angle](#offset-and-rotation)  through the [Rotation](/docs/reference/engine/classes/UIGradient#Rotation)  property.

-

Choosing the gradient's [scale](#scale)  through the [Scale](/docs/reference/engine/classes/UIGradient#Scale)  property.

-

Choosing the gradient's [edge sampling](#tile-mode)  behavior through the [TileMode](/docs/reference/engine/classes/UIGradient#TileMode)  property.

### [Color sequence](#color-sequence)[](#color-sequence)

To set a gradient's color sequence:

1.

In the [Explorer](/docs/studio/explorer)  window, select the [UIGradient](/docs/reference/engine/classes/UIGradient) .

2.

In the [Properties](/docs/studio/properties)  window, click inside the [Color](/docs/reference/engine/classes/UIGradient#Color)  property field, then click the ⋯  button to the right of the input box.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/UIGradient-Open-ColorSequence-Window.png)

3.

Each triangle on the bottom axis of the color sequence is a keypoint  that determines the color value at that point.

 ![Color sequence popup from white to white](https://prod.docsiteassets.roblox.com/assets/studio/general/ColorSequence-White-Keypoints-Labeled.png)

1.

Click a keypoint in the color sequence to select or reposition it, or add another keypoint by clicking anywhere on the graph.

2.

Click the small square next to Color  to open the Colors  pop-up window, then select the desired color for the keypoint.

3.

If needed, repeat these steps to add/adjust colors across the graph.

### [Transparency](#transparency)[](#transparency)

To adjust a gradient's transparency across its range:

1.

In the [Explorer](/docs/studio/explorer)  window, select the [UIGradient](/docs/reference/engine/classes/UIGradient) .

2.

In the [Properties](/docs/studio/properties)  window, click inside the [Transparency](/docs/reference/engine/classes/UIGradient#Transparency)  property field, then click the ⋯  button to the right of the input box.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/UIGradient-Open-NumberSequence-Window.png)

3.

Each square across the number sequence graph is a keypoint  that determines the transparency value at that point.

 ![Keypoints labeled in number sequence popup](https://prod.docsiteassets.roblox.com/assets/studio/general/NumberSequence-0-0-Keypoints-Labeled.png)

1.

Click a keypoint in the number sequence to select or reposition it, or add another keypoint by clicking anywhere on the graph.

2.

Enter a specific time/value combination through the Time  and Value  inputs.

3.

If needed, repeat these steps to add/adjust transparency levels across the graph.

### [Type](#type)[](#type)

This gradient feature is currently in beta. Enable it through File  ⟩ Beta Features  ⟩ Upgraded UIGradients .

A gradient's [Type](/docs/reference/engine/classes/UIGradient#Type)  property sets its type from among [Linear](/docs/reference/engine/enums/GradientType#Linear) , [Radial](/docs/reference/engine/enums/GradientType#Radial) , [Elliptical](/docs/reference/engine/enums/GradientType#Elliptical) , or [Conical](/docs/reference/engine/enums/GradientType#Conical) .

-

[Linear](/docs/reference/engine/enums/GradientType#Linear)  — The color/transparency sequence transitions in a straight line across the element. The direction is controlled by its [rotation](#offset-and-rotation)  and the position by its [offset](#offset-and-rotation) . This is the default.

-

[Radial](/docs/reference/engine/enums/GradientType#Radial)  — The color/transparency sequence radiates outward from the element's center, optionally shifted by [Offset](/docs/reference/engine/classes/UIGradient#Offset) . The radius is defined by the average of the element's width and height divided by two, effectively (width+height)/4 \text{(width+height)/4} (width+height)/4 . [Rotation](/docs/reference/engine/classes/UIGradient#Rotation)  has no effect on a radial gradient.

-

[Elliptical](/docs/reference/engine/enums/GradientType#Elliptical)  — The color/transparency sequence radiates outward from the element's center in an ellipse, optionally shifted by [Offset](/docs/reference/engine/classes/UIGradient#Offset) . The ellipse's horizontal and vertical radii are half the element's width and height, so the ellipse fits the element's bounds. [Rotation](/docs/reference/engine/classes/UIGradient#Rotation)  rotates the ellipse's axes.

-

[Conical](/docs/reference/engine/enums/GradientType#Conical)  — The color/transparency sequence sweeps clockwise around the center of the element, optionally shifted by [Offset](/docs/reference/engine/classes/UIGradient#Offset) . [Rotation](/docs/reference/engine/classes/UIGradient#Rotation)  controls the starting and ending angle of the sweep. By default this sweeps from 0  to 360  degrees, but [Scale](/docs/reference/engine/classes/UIGradient#Scale)  values less than 1  can reduce that angle.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Type-Linear.png)[Type](/docs/reference/engine/classes/UIGradient#Type)  = [Linear](/docs/reference/engine/enums/GradientType#Linear)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Type-Radial.png)[Type](/docs/reference/engine/classes/UIGradient#Type)  = [Radial](/docs/reference/engine/enums/GradientType#Radial)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Type-Elliptical.png)[Type](/docs/reference/engine/classes/UIGradient#Type)  = [Elliptical](/docs/reference/engine/enums/GradientType#Elliptical)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Type-Conical.png)[Type](/docs/reference/engine/classes/UIGradient#Type)  = [Conical](/docs/reference/engine/enums/GradientType#Conical)

### [Offset and rotation](#offset-and-rotation)[](#offset-and-rotation)

The [Offset](/docs/reference/engine/classes/UIGradient#Offset)  and [Rotation](/docs/reference/engine/classes/UIGradient#Rotation)  properties let you adjust the gradient's control points and its angle. As illustrated in the following diagrams, [Offset](/docs/reference/engine/classes/UIGradient#Offset)  is based on a percentage  of the parent's width or height, and both positive or negative values are valid.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Offset-X-0.png)[Offset.X](/docs/reference/engine/classes/UIGradient#Offset)  = 0

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Offset-X-Pos-0.25.png)[Offset.X](/docs/reference/engine/classes/UIGradient#Offset)  = 0.25

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Offset-X-Neg-0.25.png)[Offset.X](/docs/reference/engine/classes/UIGradient#Offset)  = -0.25

Similarly, when you rotate the gradient, the control points also rotate:

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Rotation-0.png)[Rotation](/docs/reference/engine/classes/UIGradient#Rotation)  = 0

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Rotation-Pos-45.png)[Rotation](/docs/reference/engine/classes/UIGradient#Rotation)  = 45

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Rotation-Neg-90.png)[Rotation](/docs/reference/engine/classes/UIGradient#Rotation)  = -90

### [Scale](#scale)[](#scale)

This gradient feature is currently in beta. Enable it through File  ⟩ Beta Features  ⟩ Upgraded UIGradients .

A gradient's [Scale](/docs/reference/engine/classes/UIGradient#Scale)  multiplies the extent of the gradient, controlling how much of the color/transparency sequence is visible within the element.

-

When [Scale](/docs/reference/engine/classes/UIGradient#Scale)  is less than 1 , the gradient spans less than the full extent. The remaining color/transparency is filled in according to the [TileMode](/docs/reference/engine/classes/UIGradient#TileMode)  property.

-

When [Scale](/docs/reference/engine/classes/UIGradient#Scale)  is greater than 1 , the gradient spans more than the full extent and only a part of the color/transparency is visible.

-

For [Elliptical](/docs/reference/engine/enums/GradientType#Elliptical)  gradients, [Scale](/docs/reference/engine/classes/UIGradient#Scale)  affects both radii of the ellipse.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Scale-1.0.png)[Scale](/docs/reference/engine/classes/UIGradient#Scale)  = 1

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Scale-0.25.png)[Scale](/docs/reference/engine/classes/UIGradient#Scale)  = 0.25

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Scale-1.8.png)[Scale](/docs/reference/engine/classes/UIGradient#Scale)  = 1.8

### [Tile Mode](#tile-mode)[](#tile-mode)

This gradient feature is currently in beta. Enable it through File  ⟩ Beta Features  ⟩ Upgraded UIGradients .

The [TileMode](/docs/reference/engine/classes/UIGradient#TileMode)  property sets how the gradient repeats when the full sequence does not fully cover the parent element.

-

[Clamp](/docs/reference/engine/enums/GradientTileMode#Clamp)  — Default mode where the color/transparency values at the start and end of the sequence extend infinitely, so the start values fill any area before the gradient and the end values fill any area after it.

-

[Repeat](/docs/reference/engine/enums/GradientTileMode#Repeat)  — The gradient repeats by wrapping the color/transparency sequence tiles seamlessly from end back to start. This can produce a visible seam if the first and last color/transparency values in the sequence differ.

-

[Mirror](/docs/reference/engine/enums/GradientTileMode#Mirror)  — The gradient reflects at each boundary so the color/transparency sequence ping‑pongs. This produces a smooth repetition with no seam, since the direction reverses at each tile edge.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-TileMode-Clamp.png)[TileMode](/docs/reference/engine/classes/UIGradient#TileMode)  = [Clamp](/docs/reference/engine/enums/GradientTileMode#Clamp)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-TileMode-Repeat.png)[TileMode](/docs/reference/engine/classes/UIGradient#TileMode)  = [Repeat](/docs/reference/engine/enums/GradientTileMode#Repeat)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-TileMode-Mirror.png)[TileMode](/docs/reference/engine/classes/UIGradient#TileMode)  = [Mirror](/docs/reference/engine/enums/GradientTileMode#Mirror)

## [Stroke](#stroke)[](#stroke)

The [UIStroke](/docs/reference/engine/classes/UIStroke)  instance applies an outline to text or a border. Key features include:

-

Adjustable [color](#color-or-gradient)  and [thickness](#thickness)  of the stroke outline.

-

Ability to set the stroke [transparency](#transparency-1)  independently of the parent's transparency.

-

Customizable [position and/or offset](#border-positionoffset)  relative to the parent's border.

-

Three [corner styles](#corner-style)  (round, bevel, or miter).

-

Stroke [gradient](#color-or-gradient)  support through the [UIGradient](/docs/reference/engine/classes/UIGradient)  instance.

### [Thickness](#thickness)[](#thickness)

You can set the stroke width through the [Thickness](/docs/reference/engine/classes/UIStroke#Thickness)  property which is measured in pixels (default) or scaled relative to the parent, depending on the modifier's [StrokeSizingMode](/docs/reference/engine/classes/UIStroke#StrokeSizingMode) . If stroke is on text and [StrokeSizingMode](/docs/reference/engine/classes/UIStroke#StrokeSizingMode)  is set to [ScaledSize](/docs/reference/engine/enums/StrokeSizingMode#ScaledSize) , thickness is relative to the font size.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-Thickness-4.png)[UIStroke.Thickness](/docs/reference/engine/classes/UIStroke#Thickness)  = 4

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-Thickness-12.png)[UIStroke.Thickness](/docs/reference/engine/classes/UIStroke#Thickness)  = 12

Avoid [tweening](/docs/ui/animation)  the [Thickness](/docs/reference/engine/classes/UIStroke#Thickness)  property of a [UIStroke](/docs/reference/engine/classes/UIStroke)  instance applied to text  objects. This renders and stores many glyph sizes each frame, potentially causing performance issues or text flickering.

### [Color or gradient](#color-or-gradient)[](#color-or-gradient)

You can set the stroke color through the [Color](/docs/reference/engine/classes/UIStroke#Color)  property, as well as insert a child [UIGradient](/docs/reference/engine/classes/UIGradient)  instance to create gradient strokes.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-Color-Solid.png)[UIStroke.Color](/docs/reference/engine/classes/UIStroke#Color)  = (0, 95, 225)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-Color-Gradient.png)[UIStroke](/docs/reference/engine/classes/UIStroke)  with [UIGradient](/docs/reference/engine/classes/UIGradient)  child

Both the parent object and [UIStroke](/docs/reference/engine/classes/UIStroke)  can have child [UIGradient](/docs/reference/engine/classes/UIGradient)  instances, letting you set gradients on the stroke  and fill  independently.

### [Text outline or border](#text-outline-or-border)[](#text-outline-or-border)

Depending on its parent type, [UIStroke](/docs/reference/engine/classes/UIStroke)  operates as either a text outline  or as a border . When you parent [UIStroke](/docs/reference/engine/classes/UIStroke)  to a text object like [TextLabel](/docs/reference/engine/classes/TextLabel) , it applies to the text's outline; when you parent [UIStroke](/docs/reference/engine/classes/UIStroke)  to other [GuiObjects](/docs/reference/engine/classes/GuiObject) , it applies to the border.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-As-Text-Outline.png)[TextLabel](/docs/reference/engine/classes/TextLabel)  with [UIStroke](/docs/reference/engine/classes/UIStroke)  child

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-As-Border.png)[Frame](/docs/reference/engine/classes/Frame)  with [UIStroke](/docs/reference/engine/classes/UIStroke)  and [UICorner](/docs/reference/engine/classes/UICorner)  children

When applied to a text object, you can override the default stroke behavior by the [ApplyStrokeMode](/docs/reference/engine/classes/UIStroke#ApplyStrokeMode)  property, letting you apply the stroke to the object's bounds instead of the text itself. You can even control the text outline and border independently by parenting two [UIStroke](/docs/reference/engine/classes/UIStroke)  instances to a text object, one set to Contextual  and the other to Border .

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-As-Text-Outline.png)[UIStroke.ApplyStrokeMode](/docs/reference/engine/classes/UIStroke#ApplyStrokeMode)  = [Contextual](/docs/reference/engine/enums/ApplyStrokeMode#Contextual)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-Stroke-Mode-Border.png)[UIStroke.ApplyStrokeMode](/docs/reference/engine/classes/UIStroke#ApplyStrokeMode)  = [Border](/docs/reference/engine/enums/ApplyStrokeMode#Border)

### [Border position/offset](#border-positionoffset)[](#border-positionoffset)

[BorderStrokePosition](/docs/reference/engine/classes/UIStroke#BorderStrokePosition)  sets the stroke's position relative to its parent's border and [BorderOffset](/docs/reference/engine/classes/UIStroke#BorderOffset)  lets you specify an additional offset to the stroke's position.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-BorderStrokePosition-Center.png)[BorderStrokePosition](/docs/reference/engine/classes/UIStroke#BorderStrokePosition)  = [Center](/docs/reference/engine/enums/BorderStrokePosition#Center)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-BorderStrokePosition-Inner.png)[BorderStrokePosition](/docs/reference/engine/classes/UIStroke#BorderStrokePosition)  = [Inner](/docs/reference/engine/enums/BorderStrokePosition#Inner)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-BorderStrokePosition-Outer.png)[BorderStrokePosition](/docs/reference/engine/classes/UIStroke#BorderStrokePosition)  = [Outer](/docs/reference/engine/enums/BorderStrokePosition#Outer)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-BorderOffset-Out.png)[BorderOffset](/docs/reference/engine/classes/UIStroke#BorderOffset)  = (0.15, 0)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-BorderOffset-In.png)[BorderOffset](/docs/reference/engine/classes/UIStroke#BorderOffset)  = (0, -16)

### [Transparency](#transparency-1)[](#transparency-1)

The [Transparency](/docs/reference/engine/classes/UIStroke#Transparency)  property sets the stroke transparency independently of the parent object's [BackgroundTransparency](/docs/reference/engine/classes/GuiObject#BackgroundTransparency)  or [TextTransparency](/docs/reference/engine/classes/TextLabel#TextTransparency) . This allows you to render text and borders that are "hollow" (consisting of only an outline).

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-Transparency-A.png)[TextLabel.TextTransparency](/docs/reference/engine/classes/TextLabel#TextTransparency)  = 0
[UIStroke.Transparency](/docs/reference/engine/classes/UIStroke#Transparency)  = 0.5

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-Transparency-B.png)[TextLabel.TextTransparency](/docs/reference/engine/classes/TextLabel#TextTransparency)  = 1
[UIStroke.Transparency](/docs/reference/engine/classes/UIStroke#Transparency)  = 0

### [Corner style](#corner-style)[](#corner-style)

The [LineJoinMode](/docs/reference/engine/classes/UIStroke#LineJoinMode)  property lets you control how corners are interpreted. It accepts a value of either [Round](/docs/reference/engine/enums/LineJoinMode#Round) , [Bevel](/docs/reference/engine/enums/LineJoinMode#Bevel) , or [Miter](/docs/reference/engine/enums/LineJoinMode#Miter) .

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-LineJoinMode-Round.png)[LineJoinMode](/docs/reference/engine/classes/UIStroke#LineJoinMode)  = [Round](/docs/reference/engine/enums/LineJoinMode#Round)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-LineJoinMode-Bevel.png)[LineJoinMode](/docs/reference/engine/classes/UIStroke#LineJoinMode)  = [Bevel](/docs/reference/engine/enums/LineJoinMode#Bevel)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-LineJoinMode-Miter.png)[LineJoinMode](/docs/reference/engine/classes/UIStroke#LineJoinMode)  = [Miter](/docs/reference/engine/enums/LineJoinMode#Miter)

### [Layering](#layering)[](#layering)

To layer multiple sibling [UIStroke](/docs/reference/engine/classes/UIStroke)  instances on a [GuiObject](/docs/reference/engine/classes/GuiObject)  from front to back, you can utilize the [ZIndex](/docs/reference/engine/classes/UIStroke#ZIndex)  property. Those with a lower [ZIndex](/docs/reference/engine/classes/UIStroke#ZIndex)  render under (behind) those with a higher [ZIndex](/docs/reference/engine/classes/UIStroke#ZIndex) .

Note that the rendering order for [UIStroke](/docs/reference/engine/classes/UIStroke)  instances with the same [ZIndex](/docs/reference/engine/classes/UIStroke#ZIndex)  is undefined. Do not apply multiple [UIStroke](/docs/reference/engine/classes/UIStroke)  instances with the same index if their rendering order matters.

## [Corners](#corners)[](#corners)

The [UICorner](/docs/reference/engine/classes/UICorner)  instance applies deformation to the corners of its parent [GuiObject](/docs/reference/engine/classes/GuiObject) . You can control the applied radius through the [CornerRadius](/docs/reference/engine/classes/UICorner#CornerRadius)  property using either [Scale](/docs/reference/engine/datatypes/UDim#Scale)  or [Offset](/docs/reference/engine/datatypes/UDim#Offset) .

[Scale](/docs/reference/engine/datatypes/UDim#Scale)  rounds the corners to a percentage  based on the total length of the shortest  edge of the parent, meaning that a scale of 0.5  or higher deforms the parent into a "pill" shape, regardless of its width or height. [Offset](/docs/reference/engine/datatypes/UDim#Offset)  rounds the corners to a specific number of pixels , regardless of the width/height of the parent.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UICorner-Scale-0.25.png)[Scale](/docs/reference/engine/datatypes/UDim#Scale)  = 0.25  · [Offset](/docs/reference/engine/datatypes/UDim#Offset)  = 0

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UICorner-Scale-0.5.png)[Scale](/docs/reference/engine/datatypes/UDim#Scale)  = 0.5  · [Offset](/docs/reference/engine/datatypes/UDim#Offset)  = 0

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UICorner-Offset-32.png)[Scale](/docs/reference/engine/datatypes/UDim#Scale)  = 0  · [Offset](/docs/reference/engine/datatypes/UDim#Offset)  = 32

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UICorner-Offset-64.png)[Scale](/docs/reference/engine/datatypes/UDim#Scale)  = 0  · [Offset](/docs/reference/engine/datatypes/UDim#Offset)  = 64

You can also control individual corners  through the [TopLeftRadius](/docs/reference/engine/classes/UICorner#TopLeftRadius) , [TopRightRadius](/docs/reference/engine/classes/UICorner#TopRightRadius) , [BottomRightRadius](/docs/reference/engine/classes/UICorner#BottomRightRadius) , and [BottomLeftRadius](/docs/reference/engine/classes/UICorner#BottomLeftRadius)  properties.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UICorner-Mixed-1.png)[TopLeftRadius](/docs/reference/engine/classes/UICorner#TopLeftRadius)  = (0, 0)
[TopRightRadius](/docs/reference/engine/classes/UICorner#TopRightRadius)  = (0, 48)
[BottomRightRadius](/docs/reference/engine/classes/UICorner#BottomRightRadius)  = (0, 48)
[BottomLeftRadius](/docs/reference/engine/classes/UICorner#BottomLeftRadius)  = (0, 0)

## [Padding](#padding)[](#padding)

A [UIPadding](/docs/reference/engine/classes/UIPadding)  object applies top, bottom, left, and/or right padding to the contents of the parent [GuiObject](/docs/reference/engine/classes/GuiObject) . For example, you can move the text inside a text label downward or upward by applying an offset to the modifier's [PaddingBottom](/docs/reference/engine/classes/UIPadding#PaddingBottom)  property.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIPadding-PaddingBottom-Default.png)[TextLabel](/docs/reference/engine/classes/TextLabel)  without [UIPadding](/docs/reference/engine/classes/UIPadding)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIPadding-PaddingBottom-Offset-Negative.png)[PaddingBottom](/docs/reference/engine/classes/UIPadding#PaddingBottom)  = (0, -20)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIPadding-PaddingBottom-Offset-Positive.png)[PaddingBottom](/docs/reference/engine/classes/UIPadding#PaddingBottom)  = (0, 30)

## [Shadow](#shadow)[](#shadow)

A [UIShadow](/docs/reference/engine/classes/UIShadow)  object renders a shadow for its parent UI instance. A shadow can follow the parent's rectangular shape or the glyphs of a text object. Shape shadows can appear outside or inside the parent, and mask the area directly behind the parent. Both shape and text shadows can use a color gradient.

If the parent has a [UICorner](/docs/reference/engine/classes/UICorner)  or a nonzero [GuiObject.Rotation](/docs/reference/engine/classes/GuiObject#Rotation) , its shape shadow follows the same corners or rotation. [UIShadow](/docs/reference/engine/classes/UIShadow)  doesn't support [Path2D](/docs/reference/engine/classes/Path2D)  or textures.

Some features are currently in beta. Enable them through File  ⟩ Beta Features  ⟩ Upgraded UIShadows .

### [Shape and text shadows](#shape-and-text-shadows)[](#shape-and-text-shadows)

The [Mode](/docs/reference/engine/classes/UIShadow#Mode)  property determines what casts the shadow, and both modes can coexist under the same parent.

-

[Shape](/docs/reference/engine/enums/ApplyShadowMode#Shape)  is the default. The shadow follows the rectangular area of any [GuiObject](/docs/reference/engine/classes/GuiObject) .

-

[Text](/docs/reference/engine/enums/ApplyShadowMode#Text)  follows the text glyphs of a [TextLabel](/docs/reference/engine/classes/TextLabel) , [TextButton](/docs/reference/engine/classes/TextButton) , or [TextBox](/docs/reference/engine/classes/TextBox) . Other UI objects don't render a shadow in this mode.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-Mode-Shape.png)[Mode](/docs/reference/engine/classes/UIShadow#Mode)  = [Shape](/docs/reference/engine/enums/ApplyShadowMode#Shape)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-Mode-Text.png)[Mode](/docs/reference/engine/classes/UIShadow#Mode)  = [Text](/docs/reference/engine/enums/ApplyShadowMode#Text)

[Spread](/docs/reference/engine/classes/UIShadow#Spread) , [Inset](/docs/reference/engine/classes/UIShadow#Inset) , and [ShowBehindParent](/docs/reference/engine/classes/UIShadow#ShowBehindParent)  have no effect in text mode.

### [Blur](#blur)[](#blur)

The [BlurRadius](/docs/reference/engine/classes/UIShadow#BlurRadius)  property determines the shadow's blurriness. A larger value makes the shadow's edges appear softer. Note that the scale  factor of this [UDim](/docs/reference/engine/datatypes/UDim)  property is relative to the parent's width or height, whichever is shorter.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-BlurRadius-Scale-0.png)[BlurRadius](/docs/reference/engine/classes/UIShadow#BlurRadius)  = (0, 0)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-BlurRadius-Scale-0.75.png)[BlurRadius](/docs/reference/engine/classes/UIShadow#BlurRadius)  = (0.75, 0)

### [Color and transparency](#color-and-transparency)[](#color-and-transparency)

The [Color](/docs/reference/engine/classes/UIShadow#Color)  property determines the shadow's color, while [Transparency](/docs/reference/engine/classes/UIShadow#Transparency)  sets the shadow's transparency with 0  being fully opaque and 1  being fully transparent.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-Color-White-Transparency-0.6.png)[Color](/docs/reference/engine/classes/UIShadow#Color)  = (255, 255, 255)  · [Transparency](/docs/reference/engine/classes/UIShadow#Transparency)  = 0.6

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-Color-Maroon-Transparency-0.png)[Color](/docs/reference/engine/classes/UIShadow#Color)  = (50, 0, 35)  · [Transparency](/docs/reference/engine/classes/UIShadow#Transparency)  = 0

For a multicolor shadow, insert a [UIGradient](/docs/reference/engine/classes/UIGradient)  as a child of the [UIShadow](/docs/reference/engine/classes/UIShadow) . The gradient affects the shadow without changing the parent's fill.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-Color-Gradient.png) A [UIGradient](/docs/reference/engine/classes/UIGradient)  applies a cyan-to-purple gradient to the shape shadow.

### [Offset and spread](#offset-and-spread)[](#offset-and-spread)

The [Offset](/docs/reference/engine/classes/UIShadow#Offset)  property moves the shadow relative to the parent's position, while [Spread](/docs/reference/engine/classes/UIShadow#Spread)  expands or shrinks the shadow relative to the parent's size.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-Offset-Offset.png)[Offset](/docs/reference/engine/classes/UIShadow#Offset)  = {0, -14}, {0, 6}

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-Offset-Scale.png)[Offset](/docs/reference/engine/classes/UIShadow#Offset)  = {0.1, 0}, {-0.15, 0}

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-Spread-Offset.png)[Spread](/docs/reference/engine/classes/UIShadow#Spread)  = {0, 10}, {0, 10}

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-Spread-Scale.png)[Spread](/docs/reference/engine/classes/UIShadow#Spread)  = {0.3, 0}, {0.3, 0}

### [Inset shadows](#inset-shadows)[](#inset-shadows)

Set [Inset](/docs/reference/engine/classes/UIShadow#Inset)  to true  to render the shadow on top of and inside the parent instead of behind it. Positive [Spread](/docs/reference/engine/classes/UIShadow#Spread)  values expand an inset shadow toward the center of the parent.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-Inset-False.png)[Inset](/docs/reference/engine/classes/UIShadow#Inset)  = false

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-Inset-True.png)[Inset](/docs/reference/engine/classes/UIShadow#Inset)  = true

### [Reveal content behind a transparent parent](#reveal-content-behind-a-transparent-parent)[](#reveal-content-behind-a-transparent-parent)

By default, [ShowBehindParent](/docs/reference/engine/classes/UIShadow#ShowBehindParent)  is true , so the entire shape shadow renders, including the portion directly behind the parent. Set it to false  to mask that portion of the shadow. This prevents the shadow from darkening content visible through a transparent parent.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-ShowBehindParent-True.png)[ShowBehindParent](/docs/reference/engine/classes/UIShadow#ShowBehindParent)  = true

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-ShowBehindParent-False.png)[ShowBehindParent](/docs/reference/engine/classes/UIShadow#ShowBehindParent)  = false

This property has no effect on inset or text shadows.

### [Layer shadows](#layer-shadows)[](#layer-shadows)

Add multiple [UIShadow](/docs/reference/engine/classes/UIShadow)  instances to the same parent to combine effects. The [ZIndex](/docs/reference/engine/classes/UIShadow#ZIndex)  property controls their render order. Shadows with lower values render behind shadows with higher values.

The render order of shadows that share the same [ZIndex](/docs/reference/engine/classes/UIShadow#ZIndex)  is undefined. Assign each sibling shadow a different value when their order matters.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
