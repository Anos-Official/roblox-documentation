<!-- Source: https://create.roblox.com/docs/en-us/art/accessories/specifications.md -->

---
title: "Rigid accessory specifications"
url: /docs/en-us/art/accessories/specifications
last_updated: 2026-06-16T15:58:01Z
description: "Rigid accessory specifications lists the specific technical requirements for basic avatar accessories."
---

# Rigid accessory specifications

When creating rigid accessories for Roblox, it's important to meet specific technical requirements to ensure compatibility and optimize for performance and quality. Many of these requirements must be applied when designing and modeling your asset in a third-party modeling application.

Although rigid accessories and layerable clothing accessories share many technical requirements, layerable accessories must include [additional components](/docs/en-us/art/accessories/clothing-specifications.md) to ensure the accessories deform and stretch appropriately on different body scales.

If you are intending to publish and sell these assets on the Marketplace, there are additional [Marketplace policy](/docs/en-us/marketplace/marketplace-policy.md) standards that you must follow for any accessory or clothing item.

When ready to export, see [Export requirements](/docs/en-us/art/accessories/export-settings.md) for mesh export settings for Blender and Maya.

> **Warning:** **If creating other types of 3D models:**- For generic meshes, see [general mesh specifications](/docs/en-us/art/modeling/specifications.md) and [general export settings](/docs/en-us/art/modeling/export-requirements.md). - For layered accessories, see [layered accessory specifications](/docs/en-us/art/accessories/clothing-specifications.md) and [layered export settings](/docs/en-us/art/accessories/clothing-export-settings.md). - For avatar characters, see [avatar specifications](/docs/en-us/art/characters/specifications.md) and [avatar export settings](/docs/en-us/art/characters/export-settings.md).
## Geometry and budgets

- **Single Mesh** - Accessories must be a single mesh.
- **Budgets** - Accessories can't exceed **4k** triangles.
- **Watertight** - All geometry must be watertight without exposed holes or backfaces.
- Use **quads** whenever possible. Avoid faces with 5 or more sides.
- **Mesh Size** - Depending on the type of accessory asset, meshes must follow a standard size (in studs, centered on attachment point) depending on the [body scale](#body-scale) it is designed for.

### Body scale

Roblox supports 3 types of body scales: `Classic`, `Normal`, and `Slender`. When designing your accessory, the size of your accessory cannot exceed the following sizes based on body scale and accessory asset type. Accessory size is measured based on attachment orientation.

See [Body scale](/docs/en-us/art/accessories/body-scale.md) for more information on the different types of body proportions Roblox supports.

> **Info:** You can use tools like the [Accessory Fitting Tool](/docs/en-us/art/accessories/accessory-fitting-tool.md) to help visualize and adjust the scale of your mesh on a mannequin within a visualized boundary before uploading and publishing the asset.
#### Classic

| Asset Type | Width (X) | Height (Y) | Depth (Z) |
| --- | --- | --- | --- |
| Hat | 3 | 4 | 3 |
| Hair | 3 | 5* <br> (Not centered: 2 up, 3 down) | 3.5* <br> (Not centered: 1.5 front, 2 behind) |
| Face | 3 | 2 | 2 |
| Eyebrow and Eyelashes | 1.5 | 0.5 | 0.5 |
| Neck | 3 | 3 | 2 |
| Shoulder (attached to NeckAttachment) | 7 | 3 | 3 |
| Shoulder (other) | 3 | 3 | 3 |
| Front | 3 | 3 | 3 |
| Back | 10 | 7 | 4.5* <br> (Not centered: 1.5 front, 3 behind) |
| Waist | 4 | 3.5* <br> (Not centered: 1.5 up, 2 down) | 7 |

#### Normal

| Asset Type | Width (X) | Height (Y) | Depth (Z) |
| --- | --- | --- | --- |
| Hat | 1.87 | 2.5 | 1.87 |
| Hair | 1.87 | 3.12* <br> (Not centered: 1.25 up, 1.875 down) | 2.18* <br> (Not centered: 0.9375 front, 1.25 behind) |
| Face | 1.87 | 1.25 | 1.25 |
| Eyebrow and Eyelashes | 1.5 | 0.5 | 0.5 |
| Neck | 2.95 | 3.68 | 2.16 |
| Shoulder (attached to NeckAttachment) | 6.90 | 3.68 | 3.24 |
| Shoulder (attached to RightCollarAttachment, LeftCollarAttachment) | 2.95 | 3.68 | 3.24 |
| Shoulder (attached to RightShoulderAttachment, LeftShoulderAttachment) | 2.67 | 4.40 | 3.09 |
| Front | 2.95 | 3.68 | 3.24 |
| Back | 9.86 | 8.59 | 4.87* <br> (Not centered: 1.623 front, 3.246 behind) |
| Waist | 3.94 | 4.29* <br> (Not centered: 1.842 up, 2.457 down) | 7.57 |

#### Slender

| Asset Type | Width (X) | Height (Y) | Depth (Z) |
| --- | --- | --- | --- |
| Hat | 1.78 | 2.5 | 1.78 |
| Hair | 1.78 | 3.12* <br> (Not centered: 1.25 up, 1.875 down) | 2.08* <br> (Not centered: 1.892 front, 1.189 behind) |
| Face | 1.78 | 1.25 | 1.18 |
| Eyebrow and Eyelashes | 1.5 | 0.5 | 0.5 |
| Neck | 2.59 | 3.39 | 1.92 |
| Shoulder (attached to NeckAttachment) | 6.05 | 3.39 | 2.88 |
| Shoulder (attached to RightCollarAttachment, LeftCollarAttachment) | 2.59 | 3.39 | 2.88 |
| Shoulder (attached to RightShoulderAttachment, LeftShoulderAttachment) | 2.37 | 3.96 | 2.75 |
| Front | 2.59 | 3.39 | 2.88 |
| Back | 8.64 | 7.91 | 4.32* <br> (Not centered: 1.443 front, 2.886 behind) |
| Waist | 3.76 | 3.29* <br> (Not centered: 1.414 up, 1.885 down) | 6.73 |

## Textures

- Textures for Marketplace assets cannot exceed 2048x2048 resolution.
- Textures created for accessories must meet Roblox's [texture specifications](/docs/en-us/art/modeling/texture-specifications.md).

## Attachment points

`Class.Attachment` objects indicate where an accessory model attaches to a point on a character body. Whether you are creating rigid or [layered](/docs/en-us/art/accessories/layered-clothing.md) accessories, Studio's [Accessory Fitting Tool](/docs/en-us/art/accessories/accessory-fitting-tool.md) (AFT) automatically adds and configures the appropriate `Class.Attachment` with the following specifications:

- **One attachment** - Each accessory, including layered clothing, require at least one attachment point to its associated body part.
- **Naming Convention** - The `Class.Attachment` name must follow a specific naming convention depending on the `Class.Accessory.AccessoryType`. The AFT generates an appropriate `Class.Attachment` name automatically.

If setting or configuring attachments manually in Studio, use the following names for your `Class.Attachment` object depending on the accessory type:

| Accessory type | Attachment name |
| --- | --- |
| Hat | `HatAttachment` |
| Hair | `HairAttachment` |
| Back | `BodyBackAttachment` |
| Waist | `WaistFrontAttachment`, `WaistCenterAttachment`, `WaistBackAttachment` |
| Shoulder | `RightShoulderAttachment`, `RightCollarAttachment`, `NeckAttachment`, `LeftCollarAttachment`, `LeftShoulderAttachment` |
| Face, Eyelash, Eyebrow | `FaceFrontAttachment`, `FaceCenterAttachment` |
| Neck | `NeckAttachment` |
| Front | `BodyFrontAttachment` |

> **Warning:** Importing attachment objects from a third-party tool is not supported for rigid accessories, but is supported for [character bodies](/docs/en-us/art/characters/specifications.md#attachments).

- **Shoulders and Collars** - Even though they are in similar locations, Shoulder and Collar attachment points interact with character rigs differently for rigid accessories.
  - Items using `RightShoulderAttachment` or `LeftShoulderAttachment` move with the character's arm.
  - Items using `RightCollarAttachment` or `LeftCollarAttachment` do not move with the character's arm.

## Layered properties

Accessories, such as clothing items, which stretch and fit around any character body type, must include additional configurations to achieve the layering effect. See [Clothing specifications](/docs/en-us/art/accessories/clothing-specifications.md) for specifications required to create layerable accessories.

## Marketplace requirements

Your items must meet the following requirements before you upload them to the Marketplace to sell:

- Ensure that your items adhere to the [Marketplace program guidelines](/docs/en-us/marketplace/marketplace-policy.md).
- Whenever applicable, ensure that your items adhere to Roblox's [custom mesh specifications](/docs/en-us/art/modeling/specifications.md).
- Object `Class.MeshPart.Material|Material` is set to `Plastic`.
- Object `Class.MeshPart.Transparency|Transparency` is set to 0.
- Object `Class.MeshPart.VertexColor|VertexColor` is the default `1, 1, 1`.
- Your `Class.Accessory` instance does not contain extraneous objects, like `Class.Script` or additional `Class.Part` instances.