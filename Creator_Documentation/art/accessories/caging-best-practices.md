<!-- Source: https://create.roblox.com/docs/en-us/art/accessories/caging-best-practices.md -->

---
title: "Caging best practices"
url: /docs/en-us/art/accessories/caging-best-practices
last_updated: 2026-06-16T15:58:00Z
description: "In-depth description and images of various caging best practices for layered clothing."
---

# Caging best practices

Caging is a complex process required to define the inner and outer surface of a layered clothing item. Properly caged assets allow your clothing items to stretch and layer in combination with each other. Cages that are improperly configured can lead to cosmetic issues with the look and feel of your clothing item.

_A properly configured cage typically includes a tight layering of the inner cage, clothing mesh, and the outer cage._

_The t-shirt stretches and fits naturally over a base body._

_Other layered objects, such as a jacket, should stretch and fit naturally over a target body and any other caged assets._

In extreme cases, improper cages may interfere with gameplay or social elements on Roblox. If your asset includes improper cages, Roblox may prevent you from uploading them to the Marketplace and may remove existing assets with improper cages from the catalog.

> **Warning:** Roblox is enforcing a stricter set of validation rules to improve the overall quality of layered clothing accessories in the Marketplace.

The following [best practices](#best-practices) and [common issues](#common-issues) is useful for 3D clothing creators of all levels and can elevate the quality of your clothing creations and save time with troubleshooting.

## Best practices

Always start any caging work with one of Roblox's [provided caging templates](../../assets/modeling/meshes/reference-files/Clothing_Cage_Templates.zip). These templates include an inner cage and outer cage with properly set UVs.

> **Error:** You should not edit the cage UVs since this will introduce visual artifacts.

When caging your clothing items, use these important universal guidelines:

- Any clothing mesh positioned between the inner cage and outer cage will be deformed by the layering system. This is the typical configuration for nearly all layered clothing assets._The t-shirt mesh fits snugly between the inner and outer cage.__The correctly configured t-shirt naturally stretches over a target body.__Other layered assets should stretch and fit naturally over a target body and any equipped caged assets._
- You must follow the [naming conventions](/docs/en-us/art/accessories/clothing-specifications.md#cage-meshes) for the clothing geometry and the cage.
- Many caging issues start from incorrect outer cage setup. See [working with outer cages](#working-with-outer-cages) for specific details.
- Do not modify areas of your cage that are unrelated to the clothing item you are caging. For example, do not modify the inner or outer cages of the lower leg areas when caging a t-shirt.
- Review any specific best practices for [form-fitting clothes](#caging-form-fitting-clothing), [bulky clothes](#caging-bulky-clothing-items), and [clothing with protrusions](#caging-protrusions).
- If troubleshooting any issues, review [common issues](#common-issues) to help identify problematic clothing items or specific validation errors.

### Working with outer cages

As long as the clothing mesh properly fits **over the inner cage** and **under the outer cage**, you can edit the outer cage in various ways depending on the final visual effect you intend to achieve.

When working with the outer cage, use the following guidelines when possible:

- Move vertices outwards in the normal's direction.
- Keep the outer cage as close to the clothing as possible.
- Work symmetrically as much as possible to save time.
- Do not alter the UVs in any way.
- Do not stack your vertices._Two vertices stacked directly over each other. This will introduce visual artifacts when layering other layered accessories on top._
- Keep the vertex, edge, and face count exactly the same as when you started.
- Keep your cage's edge spacing as evenly as possible._
  > **Success:** Outer cage with even spacing whenever possible on the faces.__
  > **Error:** Outer cage with uneven spacing throughout the torso area. Uneven cages can create visual artifacts and uneven deformations._
- Keep your cage's break lines between body parts lined up to the joint's position as possible. For example, try to align the elbow to where the LowerArm joint is located._Proportional changes can help improve animation and posing quality._

### Caging form-fitting clothing

Form-fitting clothing, like t-shirts, yoga pants, shorts, sweaters and slim jackets, are the most common type of layered clothing.

In this case, the outer cage needs to completely envelop the clothing accessory with minimal gaps between inner cage, clothing, and outer cage.

- Move outer cage vertices outwards to completely cover the clothing item, while maintaining the silhouette of the clothing as much as possible.
- Do not move outer cage vertices that don't contribute to covering the clothing item. For example, don't move outer cage vertices in the lower leg when the clothing item is a t-shirt.
- The entire clothing item should be located in-between the outer and inner cages.

### Caging bulky clothing items

Bulky clothing items, like puffy jackets, sweat pants, and hoodies, require additional displacement of the outer cage vertices will be much larger to envelop the bulky asset. The outer cage should still completely wrap the external surface of a bulky item.

- Pay special attention to the direction neighboring outer cage vertices are moved.
- Move along vertex normal directions as much as possible.
- Move vertices nearby each other more or less along the same directions (smooth relative displacements).
- Avoid moving vertices that are not covered by the clothing item, such as moving vertices in the arm region if you are making pants.

### Caging protrusions

Some clothing items may have assets that may protrude or extend past the rest of the clothing. Examples include clothing with puffy hoods, shoulder pads, and spikes.

_Like all clothing, clothing with protrusions should fit over inner cages._

_> **Success:** Setting the outer cage below the puffy hood allows the hood to be visible even when equipping other layered assets._

_> **Error:** Setting the outer cage above the puffy hood causes additional layered assets to stretch and cover the protrusion which is often undesired._

To ensure that the protruded region stays visible independent of the number of layers:

- Leave the protruded region outside the outer cage. Alternatively, edit the outer cage to pass under the regions that are meant to be visible and undeformed.
- Avoid moving vertices that are not covered by the clothing item

## Common issues

Improper caging can cause various rendering and deformation issues. The following common examples can help diagnose and troubleshoot any caging issues you may encounter.

### Uneven caging

Unexpected outer cage shapes causes issues when other layered assets are equipped. While the clothing may fit correctly on a target body, any additional layers will fail to stretch and deform appropriately.

_The outer cage of the black shirt is set up with uneven vertices producing an undulated caging surface._

_Any layered clothing accessory fit on top will have visual artifacts even if the clothing asset itself looks fine._

### Identical inner and outer cage

If the inner cage and outer cage are exactly the same, the layered clothing system cannot properly determine the accessory and may not deform or deform unexpectedly.

_An example of an identical inner and outer cages._

_The tshirt deforms in an unexpected manner and fails to render in its original shape or placement._

### Clothing inside inner cage

Any part of the clothing mesh positioned **inside** the **inner cage** will introduce visual artifacts when the clothing is layered on top of other clothing. You should always avoid this type of configuration.

_The clothing mesh intersects and is positioned within the inner cage at the shoulders and abdomen areas._

_When equipped, the t-shirt does not fit properly, exposing the problematic areas in the shoulders and abdomen._

### Clothing partially outside outer cage

Any part of the clothing mesh positioned **outside** the **outer cage** will not be deformed by the layered system. This configuration can sometimes be intentional for effect, such as when [caging clothing assets that include protrusions](#caging-protrusions).

_The outer cage of the tshirt is positioned within the clothing mesh near the abdomen._

_When equipped, layered assets fail to fit properly at the affected areas._

### Oversized outer cage

Ensure that the gap between the layered accessory and the outer cage is not too large. This can cause severe deformation issues when combined with other layered assets.

### Collapsed cage vertices

When cage vertices are collapsed into one vertex or a small region, any additional layer placed on top of your clothing item will have weird artifacts near the collapsed region.

_Most 3D applications can indicate if vertices are directly overlapping_

> **Warning:** This setup will be rejected during validation.
### Cages with missing limbs

The cage is meant to match the shape of the template body used to model your clothing item. Cages without heads or missing limbs won't work properly with the layered clothing system.

> **Warning:** This setup will be rejected during validation.
### Outer cage inside the inner cage

Setting the outer cage inside the inner cage creates a clothing item that can't properly layer with other assets.

> **Warning:** This setup will be rejected during validation.
### Mesh outside of outer cage

Layered assets placed outside their outer cages do not deform. If the item is completely outside then it will behave similar to a rigid accessory.

_Assets outside of the cage meshes are not supported._

_Even with a correct hierarchy, assets outside the cages will not deform._

> **Warning:** This setup will be rejected during validation.