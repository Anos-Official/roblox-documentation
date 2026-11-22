<!-- Source: https://create.roblox.com/docs/en-us/avatar/layered-accessories/caging-best-practices -->

Layered accessory caging best practices | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar/layered-accessories/caging-best-practices.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. Accessories and clothing
6. /
7. Layered accessories

# Layered accessory caging best practices

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar/layered-accessories/caging-best-practices.md)

Caging is a complex process required to define the inner and outer surface of a layered accessory. Properly caged assets allow your layered accessories to stretch and layer in combination with each other. Cages that are improperly configured can lead to cosmetic issues with the look and feel of your layered accessory.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/7-Typical-Caging-Example-D.png) A properly configured cage typically includes a tight layering of the inner cage, clothing mesh, and the outer cage.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/7-Typical-Caging-Example-B.png) The t-shirt stretches and fits naturally over a base body.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/7-Typical-Caging-Example-C.png) Other layered accessories, such as a jacket, should stretch and fit naturally over a target body and any other caged assets.

A high-quality cage matters because it affects:

-

Fit and layering  - Cages define how a layered accessory wraps over the body and over other layered accessories. Poor cages cause clipping, unnatural stretching, or accessories that don't stack correctly.

-

Hidden surface removal  - Hidden surface removal (HSR) hides the parts of the body underneath a layered accessory. HSR only works when the inner cage is completely inside the layered accessory mesh and the outer cage completely encloses it.

-

Body shape compatibility  - Characters come in many shapes and sizes. Precise cages help a layered accessory fit as well as possible on every body, not just one.

-

Inflation control  - The outer cage of the body and the inner cage of the layered accessory define the space that the accessory occupies. Imprecise cages cause unnatural puffing or clipping.

-

Animation  - Cages drive how a layered accessory fits and moves with the skeleton, especially when it uses auto-skinning. Sloppy cages create visual artifacts during any animation other than idle.

In extreme cases, improper cages may interfere with gameplay or social elements on Roblox. If your asset includes improper cages, Roblox may prevent you from uploading them to the Marketplace and may remove existing assets with improper cages from the catalog.

Roblox is enforcing a stricter set of validation rules to improve the overall quality of layered accessories in the Marketplace.

The following [best practices](#best-practices)  and [common issues](#common-issues)  are useful for avatar asset creators of all levels and can elevate the quality of your layered accessory creations and save time with troubleshooting.

## [Best practices](#best-practices)[](#best-practices)

Always start any caging work with one of Roblox's [provided caging templates](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Clothing_Cage_Templates.zip) . These templates include an inner cage and outer cage with properly set UVs.

You should not edit the cage UVs since this will introduce visual artifacts.

When caging your layered accessories, use these important universal guidelines:

-

Any clothing mesh positioned between the inner cage and outer cage will be deformed by the layering system. This is the typical configuration for nearly all layered accessory assets.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/7-Typical-Caging-Example-D.png) The t-shirt mesh fits snugly between the inner and outer cage.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/7-Typical-Caging-Example-B.png) The correctly configured t-shirt naturally stretches over a target body.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/7-Typical-Caging-Example-C.png) Other layered accessory assets should stretch and fit naturally over a target body and any equipped caged assets.

-

You must follow the [naming conventions](/docs/en-us/avatar/layered-accessories/specifications#cage-meshes)  for the layered accessory geometry and the cage.

-

Don't change the vertex count or UVs of either cage. Cages are deformers that rely on matching vertex counts and UVs to deform correctly. If either changes, the layered accessory distorts or fails to deform.

 ![A coat with its cage in a modeling application next to the unchanged cage UV layout.](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/16-Vertex-Count-UVs.jpg)

-

Model the layered accessory on the character body it's intended for. This is easier to visualize than modeling directly against a cage. For the best results, use the outer cage of the body as the inner cage of the layered accessory.

![A coat modeled on a character body.](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/17-Model-To-Body-A.jpg) A coat modeled on the character body it's intended for.

![The coat over the outer cage of the body.](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/17-Model-To-Body-B.jpg) The outer cage of the body becomes the inner cage of the coat.

-

Make sure the layered accessory mesh covers the inner cage everywhere. If needed, adjust the mesh to fit over the inner cage so it fits over the body and other layered accessories without intersecting them. For an example of what goes wrong, see [Clothing inside inner cage](#clothing-inside-inner-cage) .

 ![A coat sleeve that fully covers the inner cage of the arm.](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/18-Mesh-Covers-Inner-Cage.jpg)

-

Many caging issues start from incorrect outer cage setup. For more information, see [Working with outer cages](#working-with-outer-cages) .

-

Do not modify areas of your cage that are unrelated to the layered accessory you are caging. For example, do not modify the inner or outer cages of the lower leg areas when caging a t-shirt.

-

Review any specific best practices for [form-fitting clothes](#caging-form-fitting-clothing) , [bulky clothes](#caging-bulky-clothing) , and [clothing with protrusions](#caging-protrusions) .

-

If troubleshooting any issues, review [common issues](#common-issues)  to help identify problematic layered accessories or specific validation errors.

### [Working with outer cages](#working-with-outer-cages)[](#working-with-outer-cages)

To create an outer cage, duplicate the inner cage and edit only the areas where the layered accessory sits. Offset the vertices along their normals, and use retopology tools that snap the cage to the layered accessory mesh for an accurate, close fit.

![A coat with an outer cage created from a duplicate of the inner cage.](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/19-Create-Outer-Cage-A.jpg)

![Shorts with an outer cage edited only around the area that the shorts cover.](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/19-Create-Outer-Cage-B.jpg)

As long as the clothing mesh properly fits over the inner cage  and under the outer cage , you can edit the outer cage in various ways depending on the final visual effect you intend to achieve.

When working with the outer cage, use the following guidelines when possible:

-

Move vertices outwards in the normal's direction.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/8-Symmetry.png)

-

Keep the outer cage as close to the clothing mesh as possible without intersecting it. Because the cage has a different topology and a lower resolution than the layered accessory mesh, this can be difficult. A close outer cage lets the next layer fit closely without intersecting the layered accessory, and keeps it from looking puffy or floating away from the body.

 ![An outer cage that closely covers a shirt without intersecting it.](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/20-Close-Outer-Cage.jpg)

-

Keep the outer cage similar in shape to the inner cage. Treat it as an offset along the normals rather than reshaping or distorting it to fit over the mesh. This reduces distortion in the next layer.

![An outer cage that keeps the shape of the inner cage.](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/21-Outer-Cage-Offset-A.jpg)

![The same outer cage offset along its normals over the layered accessory.](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/21-Outer-Cage-Offset-B.jpg)

-

Work symmetrically as much as possible to save time.

-

Do not alter the UVs in any way.

-

Do not stack your vertices.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/9-Stacking-Vertices.png) Two vertices stacked directly over each other. This will introduce visual artifacts when layering other layered accessories on top.

-

Keep the vertex, edge, and face count exactly the same as when you started.

-

Keep your cage's edge spacing as evenly as possible.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/10-Even-Spacing-A.png)

Outer cage with even spacing whenever possible on the faces.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/10-Even-Spacing-B.png)

Outer cage with uneven spacing throughout the torso area. Uneven cages can create visual artifacts and uneven deformations.

-

Keep your cage's break lines between body parts lined up to the joint's position as possible. For example, try to align the elbow to where the LowerArm joint is located.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/11-Positioning-Along-Joints.png) Proportional changes can help improve animation and posing quality.

### [Caging form-fitting clothing](#caging-form-fitting-clothing)[](#caging-form-fitting-clothing)

Form-fitting clothing, like t-shirts, yoga pants, shorts, sweaters and slim jackets, are the most common type of layered accessory.

In this case, the outer cage needs to completely envelop the layered accessory with minimal gaps between inner cage, clothing mesh, and outer cage.

-

Move outer cage vertices outwards to completely cover the layered accessory, while maintaining the silhouette of the clothing mesh as much as possible.

-

Do not move outer cage vertices that don't contribute to covering the layered accessory. For example, don't move outer cage vertices in the lower leg when the layered accessory is a t-shirt.

-

The entire layered accessory should be located in-between the outer and inner cages.

### [Caging bulky clothing](#caging-bulky-clothing)[](#caging-bulky-clothing)

Bulky clothing, like puffy jackets, sweat pants, and hoodies, require additional displacement of the outer cage vertices to envelop the bulky asset. The outer cage should still completely wrap the external surface of a bulky item.

-

Pay special attention to the direction neighboring outer cage vertices are moved.

-

Move along vertex normal directions as much as possible.

-

Move vertices nearby each other more or less along the same directions (smooth relative displacements).

-

Avoid moving vertices that are not covered by the layered accessory, such as moving vertices in the arm region if you are making pants.

### [Caging protrusions](#caging-protrusions)[](#caging-protrusions)

Some clothing items have assets that protrude or extend past the rest of the clothing. Examples include clothing with puffy hoods, shoulder pads, and spikes.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/12-Protusions-A.png) Like all layered accessories, clothing with protrusions should fit over inner cages.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/12-Protusions-B.png)

Setting the outer cage below the puffy hood allows the hood to be visible even when equipping other layered accessories.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/12-Protusions-C.png)

Setting the outer cage above the puffy hood causes additional layered accessories to stretch and cover the protrusion which is often undesired.

To ensure that the protruded region stays visible independent of the number of layers:

-

Leave the protruded region outside the outer cage. Alternatively, edit the outer cage to pass under the regions that are meant to be visible and undeformed.

-

Avoid moving vertices that are not covered by the layered accessory.

### [Caging examples](#caging-examples)[](#caging-examples)

The following examples show caged layered accessories of different types.

#### [Skirt](#skirt)[](#skirt)

![A long skirt layered accessory.](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/22-Skirt-A.jpg)

![The long skirt with its outer cage.](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/22-Skirt-B.jpg)

#### [Tall boots](#tall-boots)[](#tall-boots)

![A tall boot layered accessory.](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/23-Tall-Boots-A.jpg)

![The tall boots with their outer cages.](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/23-Tall-Boots-B.jpg)

#### [Scarf](#scarf)[](#scarf)

![A scarf layered accessory.](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/24-Scarf-A.jpg)

![The scarf with its outer cage.](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/24-Scarf-B.jpg)

#### [Shoulder pauldrons](#shoulder-pauldrons)[](#shoulder-pauldrons)

![A pair of shoulder pauldron layered accessories.](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/25-Pauldrons-A.jpg)

![The shoulder pauldrons with their outer cage.](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/25-Pauldrons-B.jpg)

#### [Hat](#hat)[](#hat)

![A cap layered accessory.](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/26-Hat-A.jpg)

![The cap with its outer cage.](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/26-Hat-B.jpg)

#### [Hair](#hair)[](#hair)

![A long hair layered accessory.](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/27-Hair-A.jpg)

![The long hair with its outer cage.](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/27-Hair-B.jpg)

## [Common issues](#common-issues)[](#common-issues)

Improper caging can cause various rendering and deformation issues. The following common examples can help diagnose and troubleshoot any caging issues you may encounter.

### [Uneven caging](#uneven-caging)[](#uneven-caging)

Unexpected outer cage shapes cause issues when other layered accessories are equipped. While the layered accessory may fit correctly on a target body, any additional layers will fail to stretch and deform appropriately.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/1-Uneven-Cage-A.png) The outer cage of the black shirt is set up with uneven vertices producing an undulated caging surface.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/1-Uneven-Cage-B.png) Any layered accessory fit on top will have visual artifacts even if the layered accessory itself looks fine.

### [Identical inner and outer cage](#identical-inner-and-outer-cage)[](#identical-inner-and-outer-cage)

If the inner cage and outer cage are exactly the same, the layered accessory system cannot properly determine the accessory and may not deform or deform unexpectedly.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/2-Inner-Outer-Identical-A.png) An example of an identical inner and outer cages.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/2-Inner-Outer-Identical-B.png) The tshirt deforms in an unexpected manner and fails to render in its original shape or placement.

### [Clothing inside inner cage](#clothing-inside-inner-cage)[](#clothing-inside-inner-cage)

Any part of the clothing mesh positioned inside  the inner cage  will introduce visual artifacts when the layered accessory is layered on top of other clothing. You should always avoid this type of configuration.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/3-Clothing-Under-Inner-A.png) The clothing mesh intersects and is positioned within the inner cage at the shoulders and abdomen areas.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/3-Clothing-Under-Inner-B.png) When equipped, the t-shirt does not fit properly, exposing the problematic areas in the shoulders and abdomen.

### [Clothing partially outside outer cage](#clothing-partially-outside-outer-cage)[](#clothing-partially-outside-outer-cage)

Any part of the clothing mesh positioned outside  the outer cage  will not be deformed by the layered system. This configuration can sometimes be intentional for effect, such as when [caging layered accessories that include protrusions](#caging-protrusions) .

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/4-Outer-Not-Fully-Covering-A.png) The outer cage of the tshirt is positioned within the clothing mesh near the abdomen.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/4-Outer-Not-Fully-Covering-B.png) When equipped, layered accessories fail to fit properly at the affected areas.

### [Oversized outer cage](#oversized-outer-cage)[](#oversized-outer-cage)

Ensure that the gap between the layered accessory and the outer cage is not too large. This can cause severe deformation issues when combined with other layered accessories.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/6-Oversized-Cage.png)

### [Collapsed cage vertices](#collapsed-cage-vertices)[](#collapsed-cage-vertices)

When cage vertices are collapsed into one vertex or a small region, any additional layer placed on top of your layered accessory will have weird artifacts near the collapsed region.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/9-Stacking-Vertices.png) Most 3D applications can indicate if vertices are directly overlapping

This setup will be rejected during validation.

### [Cages with missing limbs](#cages-with-missing-limbs)[](#cages-with-missing-limbs)

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/13-Cage-Missing-Parts.png)

The cage is meant to match the shape of the template body used to model your layered accessory. Cages without heads or missing limbs won't work properly with the layered accessory system.

This setup will be rejected during validation.

### [Outer cage inside the inner cage](#outer-cage-inside-the-inner-cage)[](#outer-cage-inside-the-inner-cage)

Setting the outer cage inside the inner cage creates a layered accessory that can't properly layer with other assets.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/14-Outer-Inside-Inner.png)

This setup will be rejected during validation.

### [Mesh outside of outer cage](#mesh-outside-of-outer-cage)[](#mesh-outside-of-outer-cage)

Layered accessories placed outside their outer cages do not deform. If the layered accessory is completely outside then it will behave similar to a rigid accessory.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/15-Orbitting-Accessory-B.png) Layered accessories outside of their cage meshes are not supported.

![](https://prod.docsiteassets.roblox.com/assets/accessories/caging-best-practices/15-Orbitting-Accessory-A.png) Even with a correct hierarchy, layered accessories outside the cages will not deform.

This setup will be rejected during validation.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
