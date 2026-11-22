<!-- Source: https://create.roblox.com/docs/en-us/art/accessories.md -->

---
title: "Rigid accessories"
url: /docs/en-us/art/accessories
last_updated: 2026-06-16T15:58:01Z
description: "Rigid accessories are basic 3D cosmetics users can equip and wear on their avatar character."
---

# Rigid accessories

A high-level overview of accessories on Roblox.

Create and sell your first basic accessory.

Rigid accessories are the most basic 3D cosmetic items that users can equip and wear on their avatar character, such props, weapons, hats, and more. Unlike [clothing accessories](/docs/en-us/accessories/layered-clothing.md) that stretch and fit over a character body, rigid accessories attach to a specific point on an avatar character and don't deform or wrap over a target.

To create a custom Roblox accessory for your own experience or to sell on the Marketplace, it's important to start with the following:

- A basic background with 3D modeling tools such as [Blender](https://www.blender.org/) or [Maya](https://www.autodesk.com/products/maya/overview).
- An understanding of the [components that make up a rigid accessory](#components-of-a-rigid-accessory).
- An understanding of the general [accessory creation process](#creation-process).
- Review Roblox's official tutorials to create your own accessories:
  - [Rigid accessory creation tutorial](/docs/en-us/art/accessories/creating-rigid.md) - covers each process required for converting a 3D model to a rigid accessory and publishing it to the Marketplace.
  - [Clothing creation tutorial](/docs/en-us/art/accessories/creating.md) - a step-by-step process of creating your own avatar-ready clothing from scratch in Blender.
- [Additional tools, resources, and guides](#resources) provided by Roblox to standardize and expedite the creation process.

## Components of a rigid accessory

All accessory models are made up of the same base components of a [mesh object](#mesh-part), [textures](#textures), and [attachment](#attachments).

When [creating accessories](#creation-process), most of these components are created first in your modeling software, then converted to their appropriate Roblox Studio instance on import.

### Mesh part

_Bow rigid accessory mesh object_

_T-shirt layered clothing mesh object_

> **Warning:** Clothing, such as the t-shirt, require [additional clothing components](/docs/en-us/accessories/layered-clothing.md) to apply the layerable effect to the 3D object.

All accessories require a single mesh object that represents the geometry of the accessory object. In Studio, this mesh object is represented as a `Class.MeshPart` nested under a single `Class.Model`.

### Textures

_2D texture map for the t-shirt model_

_T-shirt model with texture applied_

Textures are 2D image files that define the surface appearance of your 3D object. You can create textures within a texture painting program or a 3D modeling software.

In Studio, textures images are imported as image assets and are set to `Class.MeshPart` objects by a child `Class.SurfaceAppearance` object or a `Class.MeshPart.TextureID` property.

### Attachments

_Attachment geometry defines where the attachment connects with the character_

_Geometry with the "_Att" suffix automatically convert to `Class.Attachment` objects in Studio_

Attachment points define where accessories attach to a character's body. In Studio, attachments are represented by `Class.Attachment` objects.

## Creation process

Custom accessories are first created in 3D modeling programs, such as [Blender](https://www.blender.org/) or [Maya](https://www.autodesk.com/products/maya/overview), before importing the `.fbx` or `.gltf` model into Studio. To get started creating your first avatar asset, see the [avatar tutorials](/docs/en-us/avatar/tutorials.md).

Depending on the type of asset you are creating, the creation process follows these high-level workflows:

_ Rigid Accessory Workflow_

_ Layered Accessory Workflow_

> **Info:** Since 3D creation isn't a linear process and always requires reiteration and testing, the process of creating an accessory can differ between individuals and various creation workflows.
## Resources

There are a variety of resources available for creators of all backgrounds to get started with accessory creation.

If you are interested in specific avatar creation topics, use the following table to find guides and resources that best match your needs:

| Topic | Resources |
| --- | --- |
| Tutorials | [Rigid accessory creation](/docs/en-us/art/accessories/creating-rigid.md) <br><br>[Basic clothing creation](/docs/en-us/art/accessories/creating.md) |
| Reference files | [Accessory and clothing reference files](/docs/en-us/art/modeling/project-files.md) |
| Technical specs | [.FBX export settings](/docs/en-us/art/modeling/export-requirements.md)<br><br>[General mesh specifications](/docs/en-us/art/modeling/specifications.md)<br><br>[Accessory specifications](/docs/en-us/art/accessories/specifications.md)<br><br>[Marketplace policy](/docs/en-us/marketplace/marketplace-policy.md) |
| Cosmetic creation | [Accessories overview](/docs/en-us/art/accessories/specifications.md)<br><br>[Layered clothing overview](/docs/en-us/art/accessories/layered-clothing.md)<br><br><br>[Accessory Fitting Tool](/docs/en-us/art/accessories/accessory-fitting-tool.md)<br><br>[Accessory specifications](/docs/en-us/art/accessories/specifications.md)<br><br>[Marketplace requirements](/docs/en-us/marketplace/marketplace-policy.md) |
| Texturing | [Texturing requirements](/docs/en-us/art/modeling/texture-specifications.md)<br><br>[PBR textures](/docs/en-us/art/modeling/surface-appearance.md) |
| Rigging and skinning | [Rigging and skinning overview](/docs/en-us/art/modeling/rigging.md)<br><br>[Humanoid rig requirements](/docs/en-us/art/characters/specifications.md#rigging)<br><br>[Rig facial bones](/docs/en-us/art/characters/facial-animation/create-basic-heads.md#rigging)<br><br>[Automatic Skin Transfer](/docs/en-us/art/accessories/automatic-skinning-transfer.md)<br><br>[Skin facial bones](/docs/en-us/art/characters/facial-animation/create-basic-heads.md#skin-face-bones) |
| Publishing and Marketplace | [Uploading to Marketplace](/docs/en-us/marketplace/publish-to-marketplace.md)<br><br>[Marketplace Policy](/docs/en-us/marketplace/marketplace-policy.md)<br><br>[Fees and commissions](/docs/en-us/marketplace/marketplace-fees-and-commissions.md) |