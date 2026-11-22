<!-- Source: https://create.roblox.com/docs/en-us/art/accessories/clothing-specifications.md -->

---
title: "Clothing specifications"
url: /docs/en-us/art/accessories/clothing-specifications
last_updated: 2026-06-16T15:58:00Z
description: "Layered clothing specifications lists the specific technical requirements for the visible mesh, cages, and proper rigging and skinning data."
---

# Clothing specifications

When creating clothing for Roblox, it's important to meet specific technical requirements to ensure compatibility and optimize for performance and quality. Many of these requirements must be applied when designing and modeling your asset in a third-party modeling application.

Although [rigid accessories](/docs/en-us/art/accessories/specifications.md) and layerable accessories share many technical requirements, layerable clothing accessories must include additional components to ensure the accessories deform and stretch appropriately on different body scales.

If you are intending to publish and sell these assets on the Marketplace, there are additional [Marketplace policy](/docs/en-us/marketplace/marketplace-policy.md) standards that you must follow for any accessory or clothing item.

When ready to export, see [export requirements](/docs/en-us/art/accessories/clothing-export-settings.md) for mesh export settings for Blender and Maya.

> **Warning:** **If creating other types of 3D models:**- For generic meshes, see [general mesh specifications](/docs/en-us/art/modeling/specifications.md) and [general export settings](/docs/en-us/art/modeling/export-requirements.md). - For rigid accessories, see [accessory specifications](/docs/en-us/art/accessories/specifications.md) and [accessory export settings](/docs/en-us/art/accessories/export-settings.md). - For avatar characters, see [avatar specifications](/docs/en-us/art/characters/specifications.md) and [avatar export settings](/docs/en-us/art/characters/export-settings.md).
## Geometry and Budgets

- **Single Mesh** - Accessories must be a single mesh.
- **Budgets** - Accessories can't exceed **4k** triangles.
- **Watertight** - All geometry must be watertight without exposed holes or backfaces.
- Use **quads** whenever possible. Avoid faces with 5 or more sides.
- **Mesh Size** - Depending on the type of accessory asset, meshes must follow a standard size (in studs, centered on attachment point) depending on the [body scale](#size-requirements) it is designed for.

### Size Requirements

Depending on the type of layerable asset, the size requirements can't exceed the following maximum width, height, and depth (in studs).

| Asset Type | Width (X) | Height (Y) | Depth (Z) |
| --- | --- | --- | --- |
| T-Shirt, Shirt, Sweater, Jacket, Pants, Shorts, Dress & Skirt | 8 | 8 | 8 |
| Eyebrow and Eyelashes | 1.5 | 0.5 | 0.5 |

### Attachment Points

`Class.Attachment` objects indicate where an accessory model attaches to a point on a character body. Whether you are creating rigid or [layered](/docs/en-us/art/accessories/layered-clothing.md) accessories, Studio's [Accessory Fitting Tool](/docs/en-us/art/accessories/accessory-fitting-tool.md) (AFT) automatically adds and configures the appropriate `Class.Attachment` with the following specifications:

- **One attachment** - Each accessory, including layered clothing, require at least one attachment point to its associated body part.
- **Naming Convention** - The `Class.Attachment` name must follow a specific naming convention depending on the `Class.Accessory.AccessoryType`. The AFT generates an appropriate `Class.Attachment` name automatically.

If setting attachment names manually in Studio, use the following `Class.Attachment` name for each accessory type:

| Accessory Type | Attachment Name |
| --- | --- |
| Hat | `HatAttachment` |
| Back | `BodyBackAttachment` |
| Waist | `WaistFrontAttachment`, `WaistCenterAttachment`, `WaistBackAttachment` |
| Shoulder | `RightShoulderAttachment`, `RightCollarAttachment`, `NeckAttachment`, `LeftCollarAttachment`, `LeftShoulderAttachment` |
| Face, Eyelash, Eyebrow | `FaceFrontAttachment`, `FaceCenterAttachment` |
| Neck | `NeckAttachment` |
| Front | `BodyFrontAttachment` |
| Layered tops (Shirt, TShirt, Sweater, Jacket) | `BodyFrontAttachment` |
| Layered bottoms (Pants, Shorts, DressSkirt) | `WaistCenterAttachment` |

> **Info:** The Importer automatically recognizes mesh objects as attachment points if the objects include the affix `\_Att`. This only applies when importing meshes with caging data, such as clothing or bodies.

- **Shoulders and Collars** - Even though they are in similar locations, Shoulder and Collar attachment points interact with character rigs differently for rigid accessories.
  - Items using `RightShoulderAttachment` or `LeftShoulderAttachment` move with the character's arm.
  - Items using `RightCollarAttachment` or `LeftCollarAttachment` do not move with the character's arm.

### Face Accessories

Face accessories, such as hair, eyebrows, and eyelashes are unique accessories that you can bundle with an avatar body upload. At this time, eyebrows and eyelashes can not be uploaded as standalone accessories and must be bundled with avatar bodies. For more information on bundling your face accessories with avatar models, see [Publishing bodies with eyelashes and eyebrows](/docs/en-us/art/accessories/publish-eyebrows-eyelashes.md).

- **Naming Convention when bundled** - When including these assets with an avatar body upload, the accessory objects must use the following name conventions:
  - `EyebrowAccessory`
  - `EyelashAccessory`
  - `HairAccessory`

## Textures

- Textures for Marketplace assets can't exceed 2048x2048 resolution.
- Textures created for accessories must meet Roblox's [texture specifications](/docs/en-us/art/modeling/texture-specifications.md). High resolution textures are automatically converted to lower-resolution textures to optimize performance.

## Layerable Properties

Clothing and accessories that deform and fit around any characters and existing clothing items require additional configuration in a 3D modeling software such as [Blender](https://www.blender.org) or [Maya](https://www.autodesk.com/products/maya/overview).

To achieve the layering effect, your clothing must meet the following requirements:

- Asset must be [weighted and bound](#rigging-and-skinning) to an R15 skeleton (Maya) or armature (Blender).
- Asset must contain an [inner mesh cage](#inner-cage) and an [outer mesh cage](#outer-cage).
- Asset must continue to follow any applicable [custom mesh requirements](/docs/en-us/art/characters/specifications.md), such as best practices on watertightness, textures, and polycount budgets.

See [Creating Layered Models](/docs/en-us/art/accessories/creating.md) for a basic guide on applying these requirements on a reference asset in Blender. Once the `.fbx` file is [exported](/docs/en-us/art/accessories/export-settings.md), see [Accessory Fitting Tool](/docs/en-us/art/accessories/accessory-fitting-tool.md) for instructions on creating an accessory from your model.

### Rigging and Skinning

Rigging and skinning a layered accessory allows the accessory to move naturally with a character body. You can perform this manually through a modeling tool, or [use automatic skinning transfer](/docs/en-us/art/accessories/automatic-skinning-transfer.md) to generate an accessory's skinning data at run time.

If using modeling software to skin your accessories, keep in mind that **Joint Influences** (Maya) or **Bone Assignments** (Blender) per vertex should be limited to **4**.

For more information on basic skinning in third-party modeling software, such as Blender's [Automatic Weights](https://docs.blender.org/manual/en/latest/animation/armatures/skinning/parenting.html#with-automatic-weights), see [Skinning a Simple Mesh](/docs/en-us/art/modeling/skin-a-simple-mesh.md) for instructions on rigging, applying weights, and skinning a basic mesh.

### Cage Meshes

**Cage meshes**, or **cages**, are invisible meshes that define the inner and outer surfaces of your asset and are fundamental to the layerable properties of clothing items. The inner cage determines the inside surface of a clothing item while the outer cage determines the outside surface of a clothing item.

> **Error:** Assets with invalid cage configurations may fail validation and are subject to moderation. See [Caging best practices](/docs/en-us/art/accessories/caging-best-practices.md) for examples and instructions.

For a basic overview on caging, see the [Basic Clothing Tutorial](/docs/en-us/art/accessories/creating/caging-setup.md) and the relevant section of the tutorial video at [8:32](https://www.youtube.com/watch?v=C-DwGRBHvmE&t=512s):

#### Inner Cage

The inner cage is the inner surface of your model and defines how the layered asset fits over another layered model. As a best practice, the shape of the inner and outer cage should match each other before editing the outer cage to completely cover your asset.

The inner cage mesh object must have the same name as the accessory model appended with **_InnerCage**.

#### Outer Cage

The outer cage defines the external surface that another item's inner cage would layer on top of. Avatar character models must have an outer cage included with its model in order to be compatible with layered clothing. All avatar models available on the [Marketplace](https://www.roblox.com/catalog) include a properly configured outer cage and are compatible with layered assets.

The outer cage of a layered clothing asset is a mesh that precisely covers the clothing item. The outer cage included in the template files is identical to the inner cage by default and must be the only cage adjusted to fit over an accessory.

The outer cage mesh object must have the same name as the accessory model appended with **_OuterCage**.

> **Warning:** The vertexes and UVs of the inner and outer cage meshes should not be deleted or removed, as they are used to match coordinates between other cages.
## Marketplace Requirements

Your items must meet the following requirements before you upload them to the Marketplace to sell:

- Ensure that your items adhere to the [Marketplace Program Guidelines](/docs/en-us/marketplace/marketplace-policy.md).
- Whenever applicable, ensure that your items adhere to Roblox's [custom mesh specifications](/docs/en-us/art/modeling/specifications.md) and [rigid accessory specifications](/docs/en-us/art/accessories/specifications.md).
- Object `Class.MeshPart.Material|Material` is set to `Plastic`.
- Object `Class.MeshPart.Transparency|Transparency` is set to 0.
- Object `Class.MeshPart.VertexColor|VertexColor` is the default `1, 1, 1`.
- Your `Class.Accessory` instance does not contain extraneous objects, like `Class.Script` or additional `Class.Part` instances.