<!-- Source: https://create.roblox.com/docs/effects/beams -->

Beams | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/effects/beams.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/workspace)
6. /
7. [Effects](/docs/effects)

# Beams

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/effects/beams.md)

A [Beam](/docs/reference/engine/classes/Beam)  is an object that renders a [Texture](/docs/reference/engine/classes/Texture)  between two [Attachment](/docs/reference/engine/classes/Attachment)  objects. By setting beam properties, you can:

-

Add a [texture](#texture)  and [color gradient](#color)  to create interesting visuals like waterfalls and force fields.

-

Modify a beam's [transparency](#transparency)  so that it fades over time.

-

Warp its shape by changing the [width](#width)  or [curve](#curve)  of each attachment point.

-

Specify the texture's [length and mode](#texture-lengthmode)  to affect how it repeats across the beam's length.

## [Create beams](#create-beams)[](#create-beams)

Before you begin to create a beam, it's useful to toggle on visibility of attachments so you can see where the beam starts and ends. You can do so by enabling Show Constraint Details  from Studio's View  menu.

To create a beam:

1.

Create two parts and position them a short distance from each other. One will act as the start of the beam and the other as the end of the beam. Group the parts into a [Model](/docs/reference/engine/classes/Model) .

2.

In the Explorer  window, add an [Attachment](/docs/reference/engine/classes/Attachment)  object to each part:

1.

Hover over one part and click the ⊕ button. A contextual menu displays.

2.

From the contextual menu, insert an Attachment .

3.

Repeat for the other part.

3.

In the Explorer  window, add a [Beam](/docs/reference/engine/classes/Beam)  object to the model:

1.

Hover over the model and click the ⊕ button. A contextual menu displays.

2.

From the contextual menu, insert a Beam .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Model-Beam-Setup.png)

4.

Select the new Beam  object and assign its attachments. Ensure you assign each attachment property to a different [Attachment](/docs/reference/engine/classes/Attachment)  object.

1.

In the Properties  window, select the Attachment0  property. Your cursor changes.

2.

In the Explorer  window, select the attachment of the part you want to be the start of your beam.

3.

Back in the Properties  window, select the Attachment1  property. Your cursor changes.

4.

In the Explorer  window, select the attachment of the part you want to be the end of your beam.

![](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/beam/Default-Beam.png) Default beam between two attachments

Beams require attachments to function properly. If you remove either attachment object from step 4, the beam stops rendering its texture.

## [Customize beams](#customize-beams)[](#customize-beams)

By experimenting with the following properties, you can customize a beam's visual appearance to make unique gameplay elements like force fields, waterfalls, and pathway obstacles.

The visual quality of your beams can change depending on the graphics settings on the player's device. To review your beam across quality levels, it's recommended to open [Studio Settings](/docs/studio/setup#customization) , search for Editor Quality Level , and set it to the both the lowest and highest level after you finish customizing your beam.

### [Texture](#texture)[](#texture)

The [Texture](/docs/reference/engine/classes/Beam#Texture)  property renders that texture across the length of the beam. You can set a beam's [Texture](/docs/reference/engine/classes/Beam#Texture)  property to any asset ID. For more information, including how to add or upload your own textures, see [here](/docs/projects/assets/manager#asset-import) .

 ![A texture of dark gray circles against a grey background emits between two attachments.](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/beam/Texture-Applied.png)

A beam renders its texture using two triangles drawn between [Segments](/docs/reference/engine/classes/Beam#Segments) , and the segments are laid out between the two attachment points' orientation. When you rotate attachment points in different directions, segments also rotate.

 ![The same texture from the previous image is now curved because the attachments are in different orientations.](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/beam/Attachments-Rotated.png)

### [Color](#color)[](#color)

The [Color](/docs/reference/engine/classes/Beam#Color)  property tints the beam's texture to either a specific hue, or to a gradient [ColorSequence](/docs/reference/engine/datatypes/ColorSequence)  across its entire span.

Constant Color Color Gradient

1.

In the Explorer  window, select the beam.

2.

In the Properties  window, select the Color  property. You can either:

1.

Click on the color square to open the Colors  pop-up window and select a color.

2.

Input three numbers into the RGB color value field.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Color-Input-Options.png)

### [Transparency](#transparency)[](#transparency)

The [Transparency](/docs/reference/engine/classes/Beam#Transparency)  property sets the transparency of the beam as a consistent value or as a [NumberSequence](/docs/reference/engine/datatypes/NumberSequence)  with ranges from 0  (totally opaque) to 1  (fully clear).

Constant Opacity Number Sequence

1.

In the Explorer  window, select the beam.

2.

In the Properties  window, select the Transparency  property.

3.

Input the desired opacity for the beam.

### [Width](#width)[](#width)

You can set the beam's width in studs at each endpoint by configuring the [Width0](/docs/reference/engine/classes/Beam#Width0)  and [Width1](/docs/reference/engine/classes/Beam#Width1)  properties. A higher value equates to a larger width and a lower value equates to a smaller width. If you set either value to smaller than 0, Studio sets it back to 0 .

The beam below has a [Width0](/docs/reference/engine/classes/Beam#Width0)  value of 0.5  and a [Width1](/docs/reference/engine/classes/Beam#Width1)  value of 3 .

 ![A texture emits between two attachments. The texture starts with a small width and ends with a large width.](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/beam/Width-Adjusted.png)

### [Texture length/mode](#texture-lengthmode)[](#texture-lengthmode)

A beam's [TextureLength](/docs/reference/engine/classes/Beam#TextureLength)  and [TextureMode](/docs/reference/engine/classes/Beam#TextureMode)  determine how its [texture](#texture)  repeats across its length.

When [TextureMode](/docs/reference/engine/classes/Beam#TextureMode)  is set to [Enum.TextureMode.Wrap](/docs/reference/engine/enums/TextureMode#Wrap)  or [Enum.TextureMode.Static](/docs/reference/engine/enums/TextureMode#Static) , the texture repetitions will equal the beam's overall length (in studs) divided by its [TextureLength](/docs/reference/engine/classes/Beam#TextureLength) .

 ![TextureMode diagram with Wrap or Static mode](https://prod.docsiteassets.roblox.com/assets/engine-api/enums/TextureMode/Wrap-Static.png)

When [TextureMode](/docs/reference/engine/classes/Beam#TextureMode)  is set to [Enum.TextureMode.Stretch](/docs/reference/engine/enums/TextureMode#Stretch) , the texture will repeat [TextureLength](/docs/reference/engine/classes/Beam#TextureLength)  times across the beam's overall length.

![TextureMode diagram with Stretch mode](https://prod.docsiteassets.roblox.com/assets/engine-api/enums/TextureMode/Stretch.png)

### [Facing](#facing)[](#facing)

A beam is a 2D projection existing in 3D space, meaning that it may not be visible from every angle. The [FaceCamera](/docs/reference/engine/classes/Beam#FaceCamera)  property, when set to true , ensures that the beam always faces the [CurrentCamera](/docs/reference/engine/classes/Workspace#CurrentCamera) , regardless of its orientation.

Default vs. FaceCamera

### [Curve](#curve)[](#curve)

Beams are configured to use a cubic Bézier curve formed by four control points. This means they are not constrained to straight lines and the curve of the beam can be modified by changing [CurveSize0](/docs/reference/engine/classes/Beam#CurveSize0) , [CurveSize1](/docs/reference/engine/classes/Beam#CurveSize1) , and the orientation of the beam's [Attachments](/docs/reference/engine/classes/Attachment) .

-

P0  — The start of the beam; position of [Attachment0](/docs/reference/engine/classes/Beam#Attachment0) .

-

P1  — [CurveSize0](/docs/reference/engine/classes/Beam#CurveSize0)  studs away from [Attachment0](/docs/reference/engine/classes/Beam#Attachment0) , in the positive X  direction of [Attachment0](/docs/reference/engine/classes/Beam#Attachment0) .

-

P2  — [CurveSize1](/docs/reference/engine/classes/Beam#CurveSize1)  studs away from [Attachment1](/docs/reference/engine/classes/Beam#Attachment1) , in the negative X  direction of [Attachment1](/docs/reference/engine/classes/Beam#Attachment1) .

-

P3  — The end of the beam; position of [Attachment1](/docs/reference/engine/classes/Beam#Attachment1) .

 ![Beam curvature diagram](https://prod.docsiteassets.roblox.com/assets/engine-api/classes/Beam/Curvature-Diagram.png)  ![](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/beam/Curves-Applied.png)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
