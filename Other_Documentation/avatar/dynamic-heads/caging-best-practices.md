<!-- Source: https://create.roblox.com/docs/avatar/dynamic-heads/caging-best-practices -->

Dynamic head caging best practices | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar/dynamic-heads/caging-best-practices.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. Animations
6. /
7. Dynamic heads

# Dynamic head caging best practices

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar/dynamic-heads/caging-best-practices.md)

The following information applies to character creators who are looking to improve or resolve errors with their character head cages. This improves compatibility with Marketplace items, such as accessories and makeup.

A character's dynamic head cage helps define the surface of the 3D model. The cage also plays an important role in Marketplace [head validation](/docs/avatar/dynamic-heads/validate) , so it's important to properly construct cages to ensure accurate fitting with head accessories and animations.

The following information and examples are best practices that are applicable to face caging as well as other caging processes. For additional best practices for caging, see [Layered accessory caging best practices](/docs/avatar/layered-accessories/caging-best-practices) .

## [General](#general)[](#general)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Primary-A.png) Realistic face model reference

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Primary-B.png) Realistic face model caging reference

### [Equidistant geometry](#equidistant-geometry)[](#equidistant-geometry)

Try to keep geometry equidistant whenever possible. This helps mitigate texture and layered accessory distortion. Keep in mind that this isn't always possible.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Equidistant-A.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Equidistant-B.png)

### [Vertex colored areas](#vertex-colored-areas)[](#vertex-colored-areas)

The template file includes vertex colors in the cages at important areas. Lining up vertex colored areas to the lips, eyebrows, and hairline areas help ensure quality makeup transfer and additionally any hair, facial hair, eyebrows, or eyelash accessories.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Vertex-A.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Vertex-B.png)

### [Important non-vertex colored areas](#important-non-vertex-colored-areas)[](#important-non-vertex-colored-areas)

Line up areas that aren't as obviously defined to the nose, eyes, and ear areas to correctly ensure quality makeup transfer and any hair, facial hair, eyebrows and eyelash accessory fit.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Non-Vertex-A.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Non-Vertex-B.png)

### [Middle axis at origin](#middle-axis-at-origin)[](#middle-axis-at-origin)

Try to keep it at origin if possible. This just keeps some consistency in the middle.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Middle-axis.png)

### [Line up neck cage part](#line-up-neck-cage-part)[](#line-up-neck-cage-part)

Cage parts need to line up to the render mesh objects. This doesn't have to be exact but should be close. This ensures that HSR (Hidden Surface Removal) can accurately hide the underlying surface when layered accessories are worn on top.

Not something you have to worry about if using auto-setup, but may help with troubleshooting issues near the neck. Keep in mind that HSR is disabled on the head, but not on the body where the neck attaches.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Neck-A.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Neck-B.png)

### [Cage should barely cover render mesh](#cage-should-barely-cover-render-mesh)[](#cage-should-barely-cover-render-mesh)

The cage needs to be close to the render mesh without actually intersecting it. Because the cage is a different topology and lower resolution than your render mesh, this can be difficult. This helps with the fit of layered accessories and with the accuracy of the makeup transfer.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Tight-Cage-A.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Tight-Cage-B.png)

## [Eyes](#eyes)[](#eyes)

### [Establish the inner and outer eye](#establish-the-inner-and-outer-eye)[](#establish-the-inner-and-outer-eye)

You should have three verts for the upper eyelid and three verts for the lower eyelid, and they should be equidistant from each other.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Eye-Inner.png)

### [Enclose the cage](#enclose-the-cage)[](#enclose-the-cage)

When applicable enclose the open edge of the eye section right up to the eye mesh.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Eye-Enclosed.png)

## [Eyebrows](#eyebrows)[](#eyebrows)

It's a little easier to visualize the eyebrow shape using the vertex color provided in the template. Once you've established the head and tail of the eyebrow, you should place the three upper and lower verts equidistant from each other.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Primary-B.png)

### [Establish the head and tail](#establish-the-head-and-tail)[](#establish-the-head-and-tail)

It's a little easier to visualize the eyebrow shape because of the vertex color. Once you've established the head and tail of the eyebrow, you should place the three upper and lower verts equidistant from each other.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Eyebrows-head-tail.png)

### [Missing eyebrows](#missing-eyebrows)[](#missing-eyebrows)

For missing eyebrows, it's important to rely on basic rules of facial proportions to figure out the placement. Take in account of stylization and face shape to account for how to shape them.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Missing-Eyebrows.png)

### [Layered clothing eyebrows](#layered-clothing-eyebrows)[](#layered-clothing-eyebrows)

For layered eyebrows try to match up the vertex colored area as best as possible to the shape of the eyebrow.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Eyebrows-Layered-Clothing.png)

### [Textured eyebrows](#textured-eyebrows)[](#textured-eyebrows)

Similar rule to layered eyebrows, try to match up the vertex colored area as best as possible to the shape of the eyebrow. Equipable eyebrows should fit right on top.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Eyebrows-Textured.png)

## [Mouth](#mouth)[](#mouth)

Outline the outside and inside of the lips. Green vertex color should be on the upper lip, and purple on the lower lip with an equidistant spacing.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Mouth.png)

## [Nose](#nose)[](#nose)

The bridge of the nose starts at the inner part of the eyes and ends two faces above the lips. Try to keep this generally in the area of where the nose should be.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Nose.png)

## [Ears](#ears)[](#ears)

Establish the top of the ear with the triangle portion of the ear, the bottom with the quad. Keep the shape of the hair line around the ear.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Ears-A.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Ears-B.png)

## [Hairline](#hairline)[](#hairline)

Establish from eyebrows the forehead shape and hairline.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Hairline-A.png)

If working with sideburns, define the shape of the sideburns in front and around the ears and consider where the hairline should end at the base of the neck. This will help determine how layered hair accessories fits to the head.

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Hairline-A.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Hairline-B.png)

## [Caging examples of other facial types](#caging-examples-of-other-facial-types)[](#caging-examples-of-other-facial-types)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Paint-on-A.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Paint-on-B.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Creatures-A.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Creatures-B.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Inorganic-A.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Inorganic-B.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Anthro-A.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Anthro-B.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Missing-A.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Missing-B.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Missing-C.png)

![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Missing-D.png)

## [Missing features](#missing-features)[](#missing-features)

For faces that are missing major facial features, use the following guidance. These tips may not always applicable, but they provide a good framework to understand how to cage faces with missing features.

-

The face is divided horizontally into three equal parts

-

Hairline to eyebrows

-

Eyebrows to the bottom of the nose

-

Bottom of the nose to the bottom of the chin.

-

Eyes are halfway down the head

-

Space between eyes is approximately eye width

-

The head is about five eyes wide

-

Tear ducts of the eyes line up with the edges of the nostrils

-

The corners of the mouth and pupils of the eyes are aligned

-

The bottom of the ears lines up With the bottom of the nose

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/caging-examples/Missing-Regions.jpg)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
