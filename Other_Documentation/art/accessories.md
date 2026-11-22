<!-- Source: https://create.roblox.com/docs/art/accessories -->

Rigid accessories | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar/rigid-accessories.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. Accessories and clothing
6. /
7. Rigid accessories

# Rigid accessories

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar/rigid-accessories/index.md)

A high-level overview of rigid accessories on Roblox.

Create and sell your first basic rigid accessory.

Rigid accessories  are 3D objects that attach to attachment points around an avatar character's body. When users purchase rigid accessories on the [Marketplace](https://www.roblox.com/catalog) , such as props, weapons, and hats, they can adjust the position and rotation of the item away from the attachment point according to their avatar's body type.

There are two main layers of a rigid accessory that structure how the accessory looks and works on the platform:

-

Mesh & textures  that make up the rigid accessory's visual appearance.

-

Attachments  that determine how the accessory attaches to the character's body.

While you can create the first of these layers manually in third-party modeling tools like [Blender](https://www.blender.org/)  or [Maya](https://www.autodesk.com/products/maya/overview) , attachments have strict configuration requirements to meet Roblox's technical [rigid accessory specifications](/docs/avatar/rigid-accessories/specifications)  that guarantee your rigid accessories behave consistently from game to game. Before you create your first custom rigid accessory, it's recommended to:

1.

Understand the [essential components](#rigid-accessory-components)  of a rigid accessory and how they work together.

2.

Review all [resources](#resources)  that Roblox provides to standardize and expedite the [creation process](#creation-process) , such as Blender and Maya project files, Studio tooling, and step-by-step guides.

3.

Follow the [basic rigid accessory creation tutorial](/docs/art/accessories/creating-rigid)  that covers how to convert a simple 3D model into a rigid accessory.

Once you have a custom rigid accessory, you can import it into Studio and use the Avatar Setup tool to process your creation into an avatar asset that's ready to be sold on the [Marketplace](/docs/marketplace) .

Unlike rigid accessories that don't deform when they attach to a specific point on the avatar, layered accessories stretch and wrap over a target until it fits over the character's body. For more information, see [Layered accessories](/docs/avatar/layered-accessories) .

## [Rigid accessory components](#rigid-accessory-components)[](#rigid-accessory-components)

All rigid accessories are made up of the same fundamental components that allow users to equip 3D items with consistent behavior according  to the character's [body type](/docs/avatar/rigid-accessories/specifications#body-scale) .

Layered accessories require [additional components](/docs/avatar/layered-accessories)  to apply the layerable effect to the 3D item.

### [Mesh part](#mesh-part)[](#mesh-part)

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Mesh-Bow-Example.png) Bow rigid accessory mesh object.

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Mesh-Hair-Example.png) Hair rigid accessory mesh object.

All rigid accessories require a single mesh object that represents the accessory's geometry. In Studio, this mesh object is represented as a [MeshPart](/docs/reference/engine/classes/MeshPart)  nested under a single [Model](/docs/reference/engine/classes/Model) .

### [Textures](#textures)[](#textures)

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Texture-Bow-Example.png)  2D texture map for the bow rigid accessory.

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Texture-Hair-Example.png)  2D texture map for the hair rigid accessory.

Textures are image files that define the surface appearance of your rigid accessory. You can create textures within a texture painting program or 3D modeling software.

In Studio, you must import textures as image files and set them to [MeshPart](/docs/reference/engine/classes/MeshPart)  objects by a child [SurfaceAppearance](/docs/reference/engine/classes/SurfaceAppearance)  object or the mesh's [TextureID](/docs/reference/engine/classes/MeshPart#TextureID)  property.

### [Attachments](#attachments)[](#attachments)

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Attachment-Bow-Example.png)  The bow's attachment point enables the bow to connect to a character's back.

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Attachment-Hair-Example.png)  The hair's attachment point enables the hair to connect to a character's head.

Attachment points define where accessories attach to a character's body. In Studio, attachment points are represented by [Attachment](/docs/reference/engine/classes/Attachment)  objects.

You can automatically generate attachment points for your rigid accessories using the [Accessory Fitting Tool](/docs/avatar/accessory-fitting-tool) .

## [Creation process](#creation-process)[](#creation-process)

When designing a rigid accessory in [Blender](https://www.blender.org/)  or [Maya](https://www.autodesk.com/products/maya/overview) , you must export all of the avatar components in a single .fbx  or .gltf  for import into Studio. Since 3D creation isn't a linear process and always requires reiteration and testing, the process of creating a rigid accessory can differ between individuals and various creation workflows.

In general, the creation process follows the following workflow:

Rigid Accessory Workflow![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Workflow-Rigid.png)

## [Resources](#resources)[](#resources)

There are a variety of resources available for creators of all backgrounds to get started with rigid accessory creation. Review the following table for specific topics and resources:

| Topic | | Resources |
| --- | --- |
| Tutorials | | [Rigid accessory creation](/docs/art/accessories/creating-rigid) |
| Reference files | | [Accessory and clothing reference files](/docs/art/modeling/project-files) |
| Technical specs | | [.FBX export settings](/docs/art/modeling/export-requirements)
[General mesh specifications](/docs/art/modeling/specifications)
[Rigid accessory specifications](/docs/avatar/rigid-accessories/specifications)
[Marketplace policy](/docs/marketplace/marketplace-policy) |
| Cosmetic creation | | [Rigid accessories overview](/docs/avatar/rigid-accessories)
[Layered clothing overview](/docs/avatar/layered-accessories)
[Accessory Fitting Tool](/docs/avatar/accessory-fitting-tool)
[Rigid accessory specifications](/docs/avatar/rigid-accessories/specifications)
[Marketplace requirements](/docs/marketplace/marketplace-policy) |
| Texturing | | [Texturing requirements](/docs/art/modeling/texture-specifications)
[PBR textures](/docs/art/modeling/surface-appearance) |
| Rigging and skinning | | [Rigging and skinning overview](/docs/art/modeling/rigging)
[Humanoid rig requirements](/docs/avatar/character-bodies/specifications#rigging)
[Rig facial bones](/docs/art/characters/facial-animation/create-basic-heads#rig-and-skin-the-head)
[Automatic Skin Transfer](/docs/avatar/automatic-skinning-transfer)
[Skin facial bones](/docs/art/characters/facial-animation/create-basic-heads#skin-joints) |
| Publishing and Marketplace | | [Uploading to Marketplace](/docs/marketplace/publish-to-marketplace)
[Marketplace Policy](/docs/marketplace/marketplace-policy)
[Fees and commissions](/docs/marketplace/marketplace-fees-and-commissions) |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
