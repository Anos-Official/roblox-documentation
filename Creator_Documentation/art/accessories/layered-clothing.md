<!-- Source: https://create.roblox.com/docs/en-us/art/accessories/layered-clothing.md -->

---
title: "Layered clothing"
url: /docs/en-us/art/accessories/layered-clothing
last_updated: 2026-06-16T15:58:01Z
description: "Layered clothing are cosmetic accessories that stretch, fit, and layer over any body type simulating real-life clothing."
---

# Layered clothing

A high-level overview of 3D clothing on Roblox.

Create and sell your first basic layered clothing.

Layered clothing accessories are 3D cosmetic items that users can equip and wear on their avatar body, such as pants, t-shirt, jackets, dresses, and more. Unlike [rigid accessories](/docs/en-us/art/accessories.md) that only attach to a specific point on a character, layered clothing stretches and fits over any body type and existing clothing.

To create a custom Roblox accessory for your own experience or to sell on the Marketplace, it's important to start with the following:

- A general background with 3D modeling tools such as [Blender](https://www.blender.org/) or [Maya](https://www.autodesk.com/products/maya/overview).
- An understanding of the [components that make up a layered accessory](#components-of-a-layered-clothing-accessory).
- An understanding of the general [clothing creation process](#creation-process).
- Review Roblox's official tutorials to create your own accessories:
  - [Rigid accessory creation tutorial](/docs/en-us/art/accessories/creating-rigid.md) - covers each process required for converting a 3D model to a rigid accessory and publishing it to the Marketplace.
  - [Clothing creation tutorial](/docs/en-us/art/accessories/creating.md) - a step-by-step process of creating your own avatar-ready clothing from scratch in Blender.
- [Additional tools, resources, and guides](#resources) provided by Roblox to standardize and expedite the creation process.

> **Warning:** If you are a developer and are looking for information on manually equipping or configuring layered clothing accessories within an experience, including [implementing layered clothing on a non-standard character model](/docs/en-us/characters/appearance.md#layered-clothing-on-non-r15), see [Character appearance](/docs/en-us/characters/appearance.md).

Roblox also supports [classic clothing](#classic-clothing), 2D images that can be applied to your character's surface.

## Components of a layered clothing accessory

All accessory models are made up of the same base components of a [mesh object](#mesh-part), [textures](#textures), and [attachment](#attachments). Layered clothing requires additional components, such as a [poseable rig](#rigging-armature), and an [inner and outer cage](#inner-and-outer-cages), to allow the asset to stretch, fit, and layer over a target character and existing clothing items.

When [creating accessories](#creation-process), all of the components are created first in your modeling software, then converted to their appropriate Roblox Studio instance on import.

### Mesh part

_T-shirt clothing mesh object_

_Bow accessory mesh object_

> **Warning:** Simple accessories, such as the bow, are [rigid accessories](/docs/en-us/art/accessories.md) do not require the rigging and caging components that allow it to stretch and fit over a target.

All accessories require a single mesh object that represents the geometry of the accessory object. In Studio, this mesh object is represented as a `Class.MeshPart` nested under a single `Class.Model`

### Textures

_2D texture map for the t-shirt model_

_T-shirt model with texture applied_

Textures are image files that define the surface appearance of your accessory. You can create textures within a texture painting program or a 3D modeling software. In Studio, textures images are imported as image assets and are set to `Class.MeshPart` objects by a child `Class.SurfaceAppearance` object or a `Class.MeshPart.TextureID` property.

### Attachments

_Attachment geometry defines where the attachment connects with the character_

_Geometry with the "_Att" suffix automatically convert to `Class.Attachment` objects in Studio_

For layered clothing, the attachment point is used to associate with the correct body part when the body ragdolls or is dismembered. In Studio, attachments are represented by `Class.Attachment` objects.

Attachments for clothing items are automatically generated in Studio using the [Accessory Fitting Tool](/docs/en-us/art/accessories/accessory-fitting-tool.md).

### Rigging armature

_To ensure natural movement of the clothing item, it must be weighted to a character rig_

_When the rig is properly set up, the layered model can move and bend with the character rig_

A rigging armature defines how a layered asset can move with a character model. Using rigging and skinning techniques, you can set the areas of your clothes to move naturally with a character model's joints, such as ensuring a shirt sleeve correctly follows the movement of the elbow and shoulder. In Studio, this rigging and skinning data is saved to the mesh geometry.

### Inner and outer cages

_The inner cage defines the inner surface of the clothing item where the clothes wrap over_

_The outer cage defines the outer surface of the clothing item where any additional clothes can wrap and layer over_

Cage meshes indicate the inner and outer surfaces of a layered accessory. The inside cage of a t-shirt defines how the t-shirt stretches and fits over a character body. The outer cage of a t-shirt defines how additional layered clothing fit over the t-shirt. In Studio, these cages are represented by `Class.WrapLayer` objects.

## Creation process

Custom accessories are first created in 3D modeling programs, such as [Blender](https://www.blender.org/) or [Maya](https://www.autodesk.com/products/maya/overview), before importing the `.fbx` or `.gltf` model into Studio. To get started creating your first avatar asset, see [Avatar Tutorials](/docs/en-us/avatar/tutorials.md).

Depending on the type of asset you are creating, the creation process follows these high-level workflows:

_ Layered Accessory Workflow_

_ Rigid Accessory Workflow_

> **Info:** Since 3D creation isn't a linear process and always requires reiteration and testing, the process of creating an accessory can differ between individuals and various creation workflows.
## Resources

There are a variety of resources available for creators of all backgrounds to get started with accessory creation.

If you are interested in specific avatar creation topics, use the following table to find guides and resources that best match your needs:

| Topic | Resources |
| --- | --- |
| Tutorials | [Rigid accessory creation](/docs/en-us/art/accessories/creating-rigid.md) <br><br>[Basic clothing creation](/docs/en-us/art/accessories/creating.md) |
| Reference files | [Accessory and clothing reference files](/docs/en-us/art/modeling/project-files.md) |
| Technical specs | [.FBX export settings](/docs/en-us/art/modeling/export-requirements.md)<br><br>[General mesh specifications](/docs/en-us/art/modeling/specifications.md)<br><br>[Accessory specifications](/docs/en-us/art/accessories/specifications.md)<br><br>[Marketplace policy](/docs/en-us/marketplace/marketplace-policy.md) |
| Cosmetic creation | [Accessories overview](/docs/en-us/art/accessories/specifications.md)<br><br>[Layered clothing overview](/docs/en-us/art/accessories.md)<br><br>[Create face accessories](/docs/en-us/art/characters/facial-animation/create-face-accessories.md)<br><br>[Accessory Fitting Tool](/docs/en-us/art/accessories/accessory-fitting-tool.md)<br><br>[Accessory specifications](/docs/en-us/art/accessories/specifications.md)<br><br>[Marketplace requirements](/docs/en-us/marketplace/marketplace-policy.md) |
| Texturing | [Texturing requirements](/docs/en-us/art/modeling/texture-specifications.md)<br><br>[PBR textures](/docs/en-us/art/modeling/surface-appearance.md) |
| Rigging and skinning | [Rigging and skinning overview](/docs/en-us/art/modeling/rigging.md)<br><br>[Humanoid rigging requirements](/docs/en-us/art/characters/specifications.md#rigging)<br><br>[Rigging facial bones](/docs/en-us/art/characters/facial-animation/create-basic-heads.md#rigging)<br><br>[Auto skin transfer](/docs/en-us/art/accessories/automatic-skinning-transfer.md)<br><br>[Skin facial bones](/docs/en-us/art/characters/facial-animation/create-basic-heads.md#skin-face-bones) |
| Testing and validation | [Calisthenics tool](/docs/en-us/art/modeling/calisthenics-tool.md)<br><br>[Clothing validation tool](/docs/en-us/art/accessories/validation-tool.md) |
| Publishing and Marketplace | [Upload to Marketplace](/docs/en-us/marketplace/publish-to-marketplace.md)<br><br>[Marketplace policy](/docs/en-us/marketplace/marketplace-policy.md)<br><br>[Fees and commissions](/docs/en-us/marketplace/marketplace-fees-and-commissions.md) |

## Classic clothing

Classic clothing assets are 2D images that you can apply to the surface of an avatar body as t-shirts, shirts, or pants. You can design these assets in any image processing software, test the textures in Studio, and then upload the designs to the Marketplace to sell. See [Classic clothing](/docs/en-us/art/classic-clothing.md) for more information on creating, uploading, and selling these assets.