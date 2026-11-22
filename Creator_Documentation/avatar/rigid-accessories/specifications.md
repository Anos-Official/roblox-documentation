<!-- Source: https://create.roblox.com/docs/en-us/avatar/rigid-accessories/specifications -->

Rigid accessory specifications | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar/rigid-accessories/specifications.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. Accessories and clothing
6. /
7. Rigid accessories

# Rigid accessory specifications

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar/rigid-accessories/specifications.md)

Rigid accessories require a specific set of components and configuration standards to ensure they are able to attach to character bodies and include optimizations for performance and quality. Because you must apply many of these requirements as you're designing and modeling the rigid accessory in a third-party modeling program like [Blender](https://www.blender.org/)  or [Maya](https://www.autodesk.com/products/maya/overview) , it's important to review these specifications early and often as you work.

When you're ready to export your rigid accessory, reference all [export setting requirements](/docs/en-us/avatar/rigid-accessories/export)  for Blender and Maya.

For other types of 3D models:

-

[General mesh](/docs/en-us/art/modeling/specifications)  specifications.

-

[Layered accessory](/docs/en-us/avatar/layered-accessories/specifications)  specifications.

## [Geometry and budgets](#geometry-and-budgets)[](#geometry-and-budgets)

-

Single Mesh  - Rigid accessories must be a single mesh.

-

Budgets  - Rigid accessories can't exceed 4k  triangles.

-

Watertight  - All geometry must be watertight without exposed holes or backfaces.

-

Use quads  whenever possible. Avoid faces with 5 or more sides.

-

Mesh Size  - Meshes must adhere to maximum size requirements (in studs, centered on attachment point) according to the type of rigid accessory you're designing and the [body scale](#body-scale)  you're designing the rigid accessory for.

### [Body scale](#body-scale)[](#body-scale)

Roblox supports 3 types of character body scales: Normal , Slender , and Classic . When designing a rigid accessory, the size of the accessory cannot exceed the following sizes based on body scale and rigid accessory asset type. A rigid accessory's size is measured based attachment orientation.

When modeling rigid accessories, it's important to use a [mannequin](/docs/en-us/avatar/resources#mannequin-models)  to help ensure your proportions fit. When using the [Importer](/docs/en-us/studio/importer#avatar-general)  to import a mannequin:

-

Use Rig Scale  > Rthro  to import your model as a Normal  body scale.

-

Use Rig Scale  > Rthro Narrow  to import your model as a Slender  body scale.

-

Use Rig Scale  > Default  to import your model as a Classic  body scale.

You can use tools like the [Accessory Fitting Tool](/docs/en-us/avatar/accessory-fitting-tool)  to help visualize and adjust the scale of your mesh on a mannequin within a visualized boundary before uploading and publishing the asset to the Marketplace. For a demonstration, see [Convert rigid accessories](/docs/en-us/avatar/rigid-accessories/import#convert-rigid-accessories) .

#### [Normal](#normal)[](#normal)

![](https://prod.docsiteassets.roblox.com/assets/art/resources/Body-Scale-Rthro-Normal.png)

A Rthro Normal body scale [downloadable mannequin](/docs/en-us/avatar/resources#references)  that's roughly 5.75-6.5 studs tall.

| Asset Type | | Width (X) | | Height (Y) | | Depth (Z) |
| --- | --- |
| Hat | | 1.87 | | 2.5 | | 1.87 |
| Hair | | 1.87 | | 3.12*
 (Not centered: 1.25 up, 1.875 down) | | 2.18*
 (Not centered: 0.9375 front, 1.25 behind) |
| Face | | 1.87 | | 1.25 | | 1.25 |
| Eyebrow and Eyelashes | | 1.5 | | 0.5 | | 0.5 |
| Neck | | 2.95 | | 3.68 | | 2.16 |
| Shoulder (attached to NeckAttachment) | | 6.90 | | 3.68 | | 3.24 |
| Shoulder (attached to RightCollarAttachment, LeftCollarAttachment) | | 2.95 | | 3.68 | | 3.24 |
| Shoulder (attached to RightShoulderAttachment, LeftShoulderAttachment) | | 2.67 | | 4.40 | | 3.09 |
| Front | | 2.95 | | 3.68 | | 3.24 |
| Back | | 9.86 | | 8.59 | | 4.87*
 (Not centered: 1.623 front, 3.246 behind) |
| Waist | | 3.94 | | 4.29*
 (Not centered: 1.842 up, 2.457 down) | | 7.57 |

#### [Slender](#slender)[](#slender)

![](https://prod.docsiteassets.roblox.com/assets/art/resources/Body-Scale-Rthro-Slender.png)

A Rthro Slender (Narrow) body scale [downloadable mannequin](/docs/en-us/avatar/resources#references)  that's roughly 5.25-6.25 studs tall.

| Asset Type | | Width (X) | | Height (Y) | | Depth (Z) |
| Hat | | 1.78 | | 2.5 | | 1.78 |
| Hair | | 1.78 | | 3.12*
 (Not centered: 1.25 up, 1.875 down) | | 2.08*
 (Not centered: 1.892 front, 1.189 behind) |
| Face | | 1.78 | | 1.25 | | 1.18 |
| Eyebrow and Eyelashes | | 1.5 | | 0.5 | | 0.5 |
| Neck | | 2.59 | | 3.39 | | 1.92 |
| Shoulder (attached to NeckAttachment) | | 6.05 | | 3.39 | | 2.88 |
| Shoulder (attached to RightCollarAttachment, LeftCollarAttachment) | | 2.59 | | 3.39 | | 2.88 |
| Shoulder (attached to RightShoulderAttachment, LeftShoulderAttachment) | | 2.37 | | 3.96 | | 2.75 |
| Front | | 2.59 | | 3.39 | | 2.88 |
| Back | | 8.64 | | 7.91 | | 4.32*
 (Not centered: 1.443 front, 2.886 behind) |
| Waist | | 3.76 | | 3.29*
 (Not centered: 1.414 up, 1.885 down) | | 6.73 |

#### [Classic](#classic)[](#classic)

![](https://prod.docsiteassets.roblox.com/assets/art/resources/Body-Scale-Classic.png)

A Classic body scale [downloadable mannequin](/docs/en-us/avatar/resources#references)  that's roughly 4.75 studs tall.

| Asset Type | | Width (X) | | Height (Y) | | Depth (Z) |
| Hat | | 3 | | 4 | | 3 |
| Hair | | 3 | | 5*
 (Not centered: 2 up, 3 down) | | 3.5*
 (Not centered: 1.5 front, 2 behind) |
| Face | | 3 | | 2 | | 2 |
| Eyebrow and Eyelashes | | 1.5 | | 0.5 | | 0.5 |
| Neck | | 3 | | 3 | | 2 |
| Shoulder (attached to NeckAttachment) | | 7 | | 3 | | 3 |
| Shoulder (other) | | 3 | | 3 | | 3 |
| Front | | 3 | | 3 | | 3 |
| Back | | 10 | | 7 | | 4.5*
 (Not centered: 1.5 front, 3 behind) |
| Waist | | 4 | | 3.5*
 (Not centered: 1.5 up, 2 down) | | 7 |

### [AvatarPartScaleType](#avatarpartscaletype)[](#avatarpartscaletype)

Roblox represents body scale in the engine by an AvatarPartScaleType  [StringValue](/docs/en-us/reference/engine/classes/StringValue)  object within each avatar character part and associated accessory. In most cases, asset creators do not need to directly access or modify this value object since tools like the [Accessory Fitting Tool](/docs/en-us/avatar/accessory-fitting-tool)  automatically generate the appropriate value object on accessory creation.

In cases where you need to identify the current body scale of a body part or accessory, the following table defines the AvatarPartScaleType  value for each type of body size. When importing your rigid accessory, use the Importer's [Rig Scale](/docs/en-us/studio/importer)  to automatically apply a scale to your accessory.

| Body Scale | | AvatarPartScaleType value |
| Classic | | Classic |
| Normal | | ProportionsNormal |
| Slender | | ProportionsSlender |

## [Textures](#textures)[](#textures)

-

Rigid accessory textures must meet Roblox's general [texture specifications](/docs/en-us/art/modeling/texture-specifications) . High resolution textures are automatically converted to lower-resolution textures to optimize performance.

-

Rigid accessory textures for Marketplace assets cannot exceed 2048x2048 resolution.

## [Attachment points](#attachment-points)[](#attachment-points)

[Attachment](/docs/en-us/reference/engine/classes/Attachment)  objects determine where an accessory model attaches to a point on a character body. Whether you are creating rigid or [layered](/docs/en-us/avatar/layered-accessories)  accessories, Studio's [Accessory Fitting Tool](/docs/en-us/avatar/accessory-fitting-tool)  (AFT) automatically adds and configures the appropriate [Attachment](/docs/en-us/reference/engine/classes/Attachment)  with the following specifications:

-

One attachment  - Each rigid accessory requires at least one attachment point to its associated body part.

-

Naming convention  - The [Attachment](/docs/en-us/reference/engine/classes/Attachment)  name must follow a specific naming convention depending on the [Accessory.AccessoryType](/docs/en-us/reference/engine/classes/Accessory#AccessoryType) . The AFT automatically generates an appropriate [Attachment](/docs/en-us/reference/engine/classes/Attachment)  name.

-

Head placement  - For accessories that attach to the head, such as hats and hair, position the attachment point so it fits on the visible surface of the head mesh. Attachment points that float away from the visible head violate [Marketplace policy](/docs/en-us/marketplace/marketplace-policy#general-creation-guidelines) .

If setting or configuring attachments manually in Studio, use the following names for your [Attachment](/docs/en-us/reference/engine/classes/Attachment)  object according to the accessory type:

| Accessory type | | Attachment name |
| Hat | | HatAttachment |
| Hair | | HairAttachment |
| Back | | BodyBackAttachment |
| Waist | | WaistFrontAttachment , WaistCenterAttachment , WaistBackAttachment |
| Shoulder | | RightShoulderAttachment , RightCollarAttachment , NeckAttachment , LeftCollarAttachment , LeftShoulderAttachment |
| Face, Eyelash, Eyebrow | | FaceFrontAttachment , FaceCenterAttachment |
| Neck | | NeckAttachment |
| Front | | BodyFrontAttachment |

Importing attachment objects from a third-party tool is not supported for rigid accessories, but is supported for [character bodies](/docs/en-us/avatar/character-bodies/specifications#attachments) .

-

Shoulders and Collars  - Even though they are in similar locations, Shoulder and Collar attachment points interact with character body armature rigs differently for rigid accessories.

-

Items using RightShoulderAttachment  or LeftShoulderAttachment  move with the character's arm.

-

Items using RightCollarAttachment  or LeftCollarAttachment  do not move with the character's arm.

## [Marketplace requirements](#marketplace-requirements)[](#marketplace-requirements)

Rigid accessories must meet the following requirements before you upload them to the Marketplace:

-

Ensure that your rigid accessories adhere to [Marketplace policies](/docs/en-us/marketplace/marketplace-policy) .

-

Whenever applicable, ensure that your rigid accessories adhere to Roblox's [custom mesh specifications](/docs/en-us/art/modeling/specifications) .

-

Object [Material](/docs/en-us/reference/engine/classes/MeshPart#Material)  is set to Plastic .

-

Object [Transparency](/docs/en-us/reference/engine/classes/MeshPart#Transparency)  is set to 0.

-

Object [VertexColor](/docs/en-us/reference/engine/classes/MeshPart#VertexColor)  is the default 1, 1, 1 .

-

Your [Accessory](/docs/en-us/reference/engine/classes/Accessory)  object does not contain extraneous objects, like [Script](/docs/en-us/reference/engine/classes/Script)  or additional [Part](/docs/en-us/reference/engine/classes/Part)  objects.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
