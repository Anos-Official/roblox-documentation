<!-- Source: https://create.roblox.com/docs/effects/trails -->

Trails | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/effects/trails.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/workspace)
6. /
7. [Effects](/docs/effects)

# Trails

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/effects/trails.md)

A [Trail](/docs/reference/engine/classes/Trail)  is an object that creates a trail between and behind two [Attachment](/docs/reference/engine/classes/Attachment)  objects as they move through space. Trails are useful to help players visualize movement, such as a sword slashing through the air, projectiles flying to their target, or footprints walking away.

After you [create a trail](#create-trails) , you can:

-

Add a [texture](#texture)  to create interesting visuals.

-

Set a constant or gradient [color](#color)  and/or [transparency](#transparency) .

-

Modify a trail's [lifetime](#lifetime) .

-

Specify the texture's [length and mode](#texture-lengthmode)  to affect how it scales, repeats, and moves along with the trail's attachments.

## [Create trails](#create-trails)[](#create-trails)

Before you begin to create a trail, it's useful to toggle on visibility of attachments so you can more easily discern how their spacing affects the trail's width. You can do so by enabling Show Constraint Details  from Studio's View  menu.

The following video demonstrates how attachments that are closer to each other create a trail with a smaller width:

To create a trail on a part:

1.

In the Explorer  window, insert two [Attachments](/docs/reference/engine/classes/Attachment)  and a [Trail](/docs/reference/engine/classes/Trail)  object into the part.

1.

Hover over the part and click the ⊕  button. A contextual menu displays.

2.

From the menu, insert two Attachments  and one Trail .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Part-Trail-Setup.png)

2.

Select the new Trail  object and assign its attachments. Ensure you assign each attachment property to a different [Attachment](/docs/reference/engine/classes/Attachment)  object.

1.

In the Properties  window, select the Attachment0  property. Your cursor changes.

2.

In the Explorer  window, select the first attachment you created.

3.

Back in the Properties  window, select the Attachment1  property. Your cursor changes.

4.

In the Explorer  window, select the second attachment you created.

3.

Using the [Move](/docs/parts#move)  tool, position both attachments within the part according to how wide you want the trail to be.

4.

To see the trail, move the part in any direction and the trail follows.

Trails require attachments to function properly. If you remove either [Attachment](/docs/reference/engine/classes/Attachment)  object from step 2, the trail stops rendering its texture.

## [Customize trails](#customize-trails)[](#customize-trails)

By experimenting with the following properties, you can customize a trail's visual appearance to make unique gameplay elements like wind gusts, sword slashes, and tire marks from fast cars.

The visual quality of your trails can change depending on the graphics settings on the player's device. To review your trail across quality levels, it's recommended to open [Studio Settings](/docs/studio/setup#customization) , search for Editor Quality Level , and set it to the both the lowest and highest level after you finish customizing your trail.

### [Texture](#texture)[](#texture)

The [Texture](/docs/reference/engine/classes/Trail#Texture)  property renders a texture across the length of the trail. You can set a trail's [Texture](/docs/reference/engine/classes/Trail#Texture)  property to any asset ID. For more information, including how to add or import your own textures, see [here](/docs/projects/assets/manager#asset-import) .

### [Color](#color)[](#color)

The [Color](/docs/reference/engine/classes/Trail#Color)  property tints the trail's texture to either a specific hue or a [ColorSequence](/docs/reference/engine/datatypes/ColorSequence) . The video below shows how a constant color compares with a gradient color across the trail's [lifetime](#lifetime) .

Constant Color Color Gradient

1.

In the Explorer  window, select the trail.

2.

In the Properties  window, select the Color  property. You can either:

1.

Click on the color square to open the Colors  pop-up window and select a color.

2.

Input three numbers into the RGB color value field.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Color-Input-Options.png)

### [Transparency](#transparency)[](#transparency)

The [Transparency](/docs/reference/engine/classes/Trail#Transparency)  property sets the transparency of the trail's segments over its [Lifetime](/docs/reference/engine/classes/Trail#Lifetime) . It can be a consistent value or a [NumberSequence](/docs/reference/engine/datatypes/NumberSequence)  with ranges from 0  (totally opaque) to 1  (fully clear).

Constant Opacity Number Sequence

1.

In the Explorer  window, select the trail.

2.

In the Properties  window, select the Transparency  property.

3.

Input the desired opacity for the trail.

### [Lifetime](#lifetime)[](#lifetime)

The [Lifetime](/docs/reference/engine/classes/Trail#Lifetime)  property allows you to set the duration of the trail in seconds. When you decrease the value of this property, the trail moves through the space more quickly and consequently cuts down the length of the trail. This can provide the object with a faster, more animated visual appearance.

Trail with lifetime of 0.5 (left) vs. trail with lifetime of 3.0 (right)

### [Texture length/mode](#texture-lengthmode)[](#texture-lengthmode)

A trail's [TextureLength](/docs/reference/engine/classes/Trail#TextureLength)  and [TextureMode](/docs/reference/engine/classes/Trail#TextureMode)  determine how its [texture](#texture)  scales, repeats, and moves along with the trail's attachments.

Scaling and Repetition Movement

When [TextureMode](/docs/reference/engine/classes/Trail#TextureMode)  is set to [Enum.TextureMode.Wrap](/docs/reference/engine/enums/TextureMode#Wrap)  or [Enum.TextureMode.Static](/docs/reference/engine/enums/TextureMode#Static) , the [TextureLength](/docs/reference/engine/classes/Trail#TextureLength)  property sets the length of the texture as it repeats across the trail's length.

![TextureMode diagram with Wrap mode](https://prod.docsiteassets.roblox.com/assets/engine-api/enums/TextureMode/Wrap-Static.png)

When [TextureMode](/docs/reference/engine/classes/Trail#TextureMode)  is set to [Enum.TextureMode.Stretch](/docs/reference/engine/enums/TextureMode#Stretch) , the texture will repeat [TextureLength](/docs/reference/engine/classes/Trail#TextureLength)  times across the trail's overall length.

![TextureMode diagram with Stretch mode](https://prod.docsiteassets.roblox.com/assets/engine-api/enums/TextureMode/Stretch.png)

### [Facing](#facing)[](#facing)

A trail is a 2D projection existing in 3D space, meaning that it may not be visible from every angle. The [FaceCamera](/docs/reference/engine/classes/Trail#FaceCamera)  property, when set to true , ensures that the trail always faces the [CurrentCamera](/docs/reference/engine/classes/Workspace#CurrentCamera) , regardless of its orientation.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
