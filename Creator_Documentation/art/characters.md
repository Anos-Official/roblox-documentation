<!-- Source: https://create.roblox.com/docs/en-us/art/characters.md -->

---
title: "Avatar characters"
url: /docs/en-us/art/characters
last_updated: 2026-06-16T15:58:04Z
description: "All Roblox users are represented by an avatar character which can be customized with body parts, accessories, and clothes from the Marketplace or within experiences."
---

# Avatar characters

Every Roblox user is represented by a customizable character called an **avatar**. Avatars are character models with many specialized features that allow users to interact with the world and customize themselves with a wide range of clothing and accessories from the Marketplace.

Custom avatars are first created in 3D modeling programs, such as [Blender](https://www.blender.org/) or [Maya](https://www.autodesk.com/products/maya/overview), before importing into Studio. To create a custom Roblox avatar character for your own experience, it's important to start with the following:

- An advanced background with 3D modeling tools such as [Blender](https://www.blender.org/) or [Maya](https://www.autodesk.com/products/maya/overview).
- An understanding of the [components that make up an avatar character](#components-of-an-avatar).
- An understanding of the general [character creation process](#creation-process).
- Review the [basic character creation tutorial](/docs/en-us/characters/creating.md) to get started on creating your first avatar character using Roblox's templates.
- [Various tools, resources, and guides](#resources) provided by Roblox to standardize and expedite the creation process.

## Components of an avatar

All avatar character models are made up of several fundamental components that provide users the functionality and flexibility to interact with their world. Many of these components are never made visible to the user, but they enable powerful avatar features that enhance social and environmental interactions. When creating avatar characters, all of these components are typically created first in your modeling software and then converted to their appropriate Roblox Studio instance on import.

Each avatar character is made up of the following rendered and non-rendered components:

#### Rendered

_15 body part meshes make up the physical aspects of the character model_

_Texture image maps apply a surface color and appearance. Transparency allows underlying part colors to be exposed, such as custom skin tones._

#### Non-Rendered

_A rigging armature allows the body parts to properly connect with each other, driving movement, expressions, and animations_

_Facial animation data allows avatars to express virtually all types of facial expressions for chatting and socializing_

_Cage meshes set the outer boundary of the character, defining the surface where clothing and other layerable items can wrap and stretch over._

_Attachment points define where rigid accessories attach to a character_

### Body parts

_Each avatar character is made up of 15 separate mesh objects_

_These meshes must follow a standard naming convention_

Roblox avatar characters are made up of 15 body parts, pieces of geometry that define the shape and contours of your avatar character. In Studio, these geometries are represented as `Class.MeshPart` objects and are nested under a single `Class.Model`.

### Textures

_Textures apply color and surface details to your character model._

_A texture image map's opacity can combine with the `Class.MeshPart.Color` to apply custom skin tones to characters._

Textures are image files that define the surface appearance of your character. You can create textures using a texture painting program or a 3D modeling software. In Studio, you must import textures as image files and access them through the `Class.SurfaceAppearance` instance, or set as a `Class.MeshPart.TextureID` property.

> **Warning:** When texturing parts of your character model's body, ensure that your character model includes a modesty layer over sensitive regions. See [Community Standards](https://en.help.roblox.com/hc/en-us/articles/203313410#safety) for more information on Roblox's policies.
### Rigging armature

_The armature is made up of 16 bones, 1 for each body part geometry and a root bone_

_Bones must follow a specific hierarchy and naming convention_

An armature allows each character to articulate its limbs and move naturally through the environment. Often referred to as bones or joints, this rigging character information includes skinning data which allows connected limbs, like the knees or elbows to bend organically. In Studio, each bone of the character armature is represented by `Class.Bone` objects that connect the character `Class.MeshPart` objects together.

[Standard character rigs](/docs/en-us/art/specifications.md#standard-rigs) require 15 poseable `Class.Bone` objects, and higher-fidelity rigs support up to 37 additional `Class.Bone` objects for a greater level of realism with articulated hands, shoulders, and spine movements. All `Class.Bone` objects must follow a specific hierarchy and naming convention to function properly in Studio and on the Marketplace. For more information, see [Rigging](/docs/en-us/art/specifications.md#rigging).

### Face animation data

_Each avatar character face is rigged and skinned to create various expressions_

_Each pose is mapped to a pose name within the Custom Properties (Extra Attributes in Maya) of the Head_Geo object_

_Each required face pose is saved as a keyframe in the animation timeline._

Facial animation data allow each character to use global facial expressions. Each character includes facial bones and skinning, animation timeline data, and mapped pose data that allows it. In Studio, these facial animation elements are represented by a `Class.FaceControls` instance.

### Cage meshes

_Head and Upper Torso cage mesh objects (wireframe)_

_Cage objects must exist for each of the 15 body parts_

This outer cage sets the invisible surface on which layerable accessories, such as clothing, will stretch and fit over the body. These cage meshes allow clothes to fit over models of different shapes and sizes without having to remodel the clothing item. In Studio, outer cage mesh objects are represented by a `Class.WrapTarget` instance.

If you are caging your own non-template character model, it's important to use one of Roblox's body cage [project files](/docs/en-us/avatar/resources.md#mannequin-models) to ensure you are using a Roblox standard cage mesh. Removing or adding vertices from this standard mesh can cause issues with clothing fit and import.

### Attachments

_Each character has common attachment points for equipping rigid cosmetics_

_Each avatar character must include their associated 19 attachment points_

Attachment points define where rigid 3D accessories and equipables attach to the character's body. These are not rendered to the end-user but are represented as sphere geometries in 3D modeling software and, when imported into Studio, these geometries are created as `Class.Attachment` instances using the standardized names.

When wearing layered clothing, the clothing isn't attached directly to the attachment, but it does reference the associated attachment point during ragdoll and dismemberment animations.

## Creation process

When designing an avatar model, you must export all of the avatar components in a single `.fbx` or `.gltf` for import into Studio. Since 3D creation isn't a linear process and always requires reiteration and testing, the process of creating an avatar character model can differ between individuals and various creation workflows.

In general, the creation process follows these typical workflows:

_ Basic Creation with Templates__Customize a Roblox template character that already includes all the necessary components. See [Create with templates](/docs/en-us/characters/creating.md) for guides and instructions._

_ Advanced Creation from Scratch__Create characters from scratch, allowing full customization of the avatar character's components._

> **Warning:** Ensure that all assets you create follow any applicable [Marketplace policies](/docs/en-us/marketplace/marketplace-policy.md) and [Roblox Community Standards](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards).
## Resources

There are a variety of resources available for creators of all backgrounds to get started with character creation.

If you are interested in specific avatar creation topics, use the following table to find guides and resources that best match your needs:

| Topic | Resources |
| --- | --- |
| Tutorials | [Basic character creation tutorial](/docs/en-us/accessories/creating.md) |
| Reference files | [Avatar references and project files](/docs/en-us/characters/project-files.md)<br><br>[Example mesh/model objects](/docs/en-us/modeling/project-files.md) |
| Technical specs | [.FBX export settings](/docs/en-us/characters/export-settings.md)<br><br>[Avatar specifications](/docs/en-us/characters/specifications.md)<br><br>[General mesh specifications](/docs/en-us/modeling/specifications.md)<br><br>[Accessory specifications](/docs/en-us/accessories/specifications.md)<br><br>[Marketplace policy](/docs/en-us/marketplace/marketplace-policy.md) |
| Cosmetic creation | [Accessories overview](/docs/en-us/accessories.md)<br><br>[Creating face accessories](/docs/en-us/characters/facial-animation/create-face-accessories.md)<br><br>[Accessory Fitting Tool](/docs/en-us/accessories/accessory-fitting-tool.md)<br><br>[Accessory specifications](/docs/en-us/accessories/specifications.md)<br><br>[Marketplace requirements](/docs/en-us/marketplace/marketplace-policy.md) |
| Texturing | [Texturing requirements](/docs/en-us/modeling/texture-specifications.md)<br><br>[PBR textures](/docs/en-us/modeling/surface-appearance.md) |
| Rigging and skinning | [Rigging and skinning overview](/docs/en-us/modeling/rigging.md)<br><br>[Humanoid rig requirements](/docs/en-us/characters/specifications.md#rig)<br><br>[Rigging facial bones](/docs/en-us/characters/facial-animation/create-basic-heads.md#rig)<br><br>[Automatic Skinning Transfer](/docs/en-us/accessories/automatic-skinning-transfer.md)<br><br>[Skinning facial bones](/docs/en-us/characters/facial-animation/create-basic-heads.md#skin-face-bones) |
| Facial animation and live heads | [Basic head creation](/docs/en-us/characters/facial-animation/create-basic-heads.md)<br><br>[Face accessory creation](/docs/en-us/characters/facial-animation/create-face-accessories.md)<br><br>[FACS pose references](/docs/en-us/characters/facial-animation/facs-poses-reference.md) |
| Testing and validation | [Calisthenics Tool](/docs/en-us/modeling/calisthenics-tool.md)<br><br>[Clothing Validation Tool](/docs/en-us/accessories/validation-tool.md) |
| Publishing and Marketplace | [Uploading to Marketplace](/docs/en-us/marketplace/publish-to-marketplace.md)<br><br>[Marketplace policy](/docs/en-us/marketplace/marketplace-policy.md)<br><br>[Fees and commissions](/docs/en-us/marketplace/marketplace-fees-and-commissions.md) |