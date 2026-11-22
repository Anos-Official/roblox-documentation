<!-- Source: https://create.roblox.com/docs/avatar/layered-accessories -->

Layered accessories | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar/layered-accessories.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. Accessories and clothing
6. /
7. Layered accessories

# Layered accessories

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar/layered-accessories/index.md)

A high-level overview of layered accessories on Roblox.

Create and sell your first basic layered accessory.

Layered accessories , often referred to as layered clothing , are 3D assets that stretch and fit on an avatar character's body according to their rigging armature and cage meshes. When users purchase layered accessories on the Marketplace, such as jackets, dresses, and cardigans, they expect it to move with the character's animations and layer appropriately on top of existing clothing the character is wearing.

There are three main layers of a layered accessory that structure how the accessory looks and works on the platform:

-

Mesh & textures  that make up the layered accessory's visual appearance.

-

Rigging armature  that determines how the character moves and animates with the layered accessory.

-

Cage meshes & attachments  that determine how the layered accessory stretches, fits, and layers over the character's body.

While you can create most of these layers manually in third-party modeling tools like [Blender](https://www.blender.org/)  or [Maya](https://www.autodesk.com/products/maya/overview) , cage meshes and attachments have strict configuration requirements to meet Roblox's technical [layered accessory specifications](/docs/avatar/layered-accessories/specifications)  that guarantee your layered accessories behave consistently from game to game. Before you create your first custom layered accessory, it's recommended to:

1.

Understand the [essential components](#layered-accessory-components)  of a layered accessory and how they work together.

2.

Review all [resources](#resources)  that Roblox provides to standardize and expedite the [creation process](#creation-process) , such as Blender and Maya project files, Studio tooling, and step-by-step guides.

3.

Follow the [basic layered accessory creation tutorial](/docs/art/accessories/creating)  that covers how to create your own avatar-ready sweater from scratch in Blender.

Once you have a custom layered accessory, you can import it into Studio and use the Avatar Setup tool to process your creation into an avatar asset that's ready to be sold on the [Marketplace](/docs/marketplace) .

Unlike layered accessories that stretch and wrap over a target until it fits over the character's body, rigid accessories don't deform and only attach to a specific point on the avatar. For more information, see [Rigid accessories](/docs/avatar/rigid-accessories) .

If you are a game developer and are looking for information on manually equipping or configuring layered accessories within a game, such as implementing layered accessories on a non-standard character model, see [Character appearance](/docs/characters/appearance) .

## [Layered accessory components](#layered-accessory-components)[](#layered-accessory-components)

All layered accessories are made up of the same fundamental components that allow users to equip 3D items that stretch, fit, and layer over a target character and existing clothing items with consistent behavior regardless  of the character's [body type](/docs/avatar/character-bodies/specifications#body-scale) .

### [Mesh part](#mesh-part)[](#mesh-part)

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Mesh-Jumpsuit-Example.png)  Jumpsuit layered accessory mesh object.

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Mesh-ShoulderPads-Example.png) Shoulder pads layered accessory mesh object.

All layered accessories require a single mesh object that represents the accessory's geometry. In Studio, this mesh object is represented as a [MeshPart](/docs/reference/engine/classes/MeshPart)  nested under a single [Model](/docs/reference/engine/classes/Model) .

### [Textures](#textures)[](#textures)

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Texture-Jumpsuit-Example.png)  2D texture map for the jumpsuit layered accessory.

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Texture-ShoulderPads-Example.png) 2D texture map for the shoulder pads layered accessory.

Textures are image files that define the surface appearance of your layered accessory. You can create textures within a texture painting program or 3D modeling software.

In Studio, you must import textures as image files and set them to [MeshPart](/docs/reference/engine/classes/MeshPart)  objects by a child [SurfaceAppearance](/docs/reference/engine/classes/SurfaceAppearance)  object or the mesh's [TextureID](/docs/reference/engine/classes/MeshPart#TextureID)  property.

### [Rigging armature](#rigging-armature)[](#rigging-armature)

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Rigging-Example.png)  To ensure the layered accessory can deform with the character's body, it must be weighted to a rigging armature.

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Rigging-Pose-Example.png) When the rigging armature is properly set up, the layered accessory moves and bends as the character moves in the 3D space.

Inside of the avatar's physical body is a non-rendered rigging armature that allows the character to articulate its limbs. Often referred to as joints or bones, a rigging armature includes skinning data that allows connections between limbs to bend organically, such as the character's knees and elbows. In Studio, this rigging and skinning data is saved to the mesh geometry.

The rigging armature also defines how layered accessories move and deform as the character moves in the 3D space. Using rigging and skinning techniques, you can configure areas of your layered accessories to move naturally with the character's joints, such as a shirt sleeve following the natural movement of the character's elbow and shoulder during a walk cycle.

### [Cage meshes](#cage-meshes)[](#cage-meshes)

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Inner-Cage-Example.png)  The inner cage defines the inner surface of the clothing item where the clothes wrap over.

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Outer-Cage-Example.png) The outer cage defines the outer surface of the clothing item where any additional clothes can wrap and layer over.

Cage meshes set the inner and outer surfaces of a layered accessory. For example, the inner cage of a t-shirt defines how a layered accessory t-shirt stretches and fits over a character body, and the outer cage defines how other layered accessories can stretch and fit over the t-shirt itself.

In Studio, these cages are represented by [WrapLayer](/docs/reference/engine/classes/WrapLayer)  objects.

### [Attachments](#attachments)[](#attachments)

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Attachment-Jumpsuit-Example.png)  The jumpsuit layered accessory's attachment point.

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Attachment-ShoulderPads-Example.png) The shoulder pads layered accessory's attachment point.

Attachment points for layered accessories set which body part the accessory is attached to when the character body ragdolls or dismembers in a game. In Studio, attachment points are represented by [Attachment](/docs/reference/engine/classes/Attachment)  objects.

You can automatically generate attachment points for your layered accessories using the [Accessory Fitting Tool](/docs/avatar/accessory-fitting-tool) .

## [Creation process](#creation-process)[](#creation-process)

When designing a layered accessory in [Blender](https://www.blender.org/)  or [Maya](https://www.autodesk.com/products/maya/overview) , you must export all of the avatar components in a single .fbx  or .gltf  for import into Studio. Since 3D creation isn't a linear process and always requires reiteration and testing, the process of creating a layered accessory can differ between individuals and various creation workflows.

In general, the creation process follows the following workflow:

Layered Accessory Workflow![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Workflow-Layered.png)

## [Resources](#resources)[](#resources)

There are a variety of resources available for creators of all backgrounds to get started with layered accessory creation. Review the following table for specific topics and resources:

| Topic | | Resources |
| --- | --- |
| Tutorials | | [Create your first layered accessory](/docs/art/accessories/creating) |
| Reference files | | [Accessory and clothing reference files](/docs/art/modeling/project-files) |
| Technical specs | | [.FBX export settings](/docs/art/modeling/export-requirements)
[General mesh specifications](/docs/art/modeling/specifications)
[Accessory specifications](/docs/avatar/rigid-accessories/specifications)
[Marketplace policy](/docs/marketplace/marketplace-policy) |
| Cosmetic creation | | [Accessories overview](/docs/avatar/rigid-accessories)
[Layered clothing overview](/docs/avatar/layered-accessories)
[Create face accessories](/docs/art/characters/facial-animation/create-face-accessories)
[Accessory Fitting Tool](/docs/avatar/accessory-fitting-tool)
[Accessory specifications](/docs/avatar/rigid-accessories/specifications)
[Marketplace requirements](/docs/marketplace/marketplace-policy) |
| Texturing | | [Texturing requirements](/docs/art/modeling/texture-specifications)
[PBR textures](/docs/art/modeling/surface-appearance) |
| Rigging and skinning | | [Rigging and skinning overview](/docs/art/modeling/rigging)
[Humanoid rigging requirements](/docs/avatar/character-bodies/specifications#rigging)
[Rigging facial bones](/docs/art/characters/facial-animation/create-basic-heads#rig-and-skin-the-head)
[Auto skin transfer](/docs/avatar/automatic-skinning-transfer)
[Skin facial bones](/docs/art/characters/facial-animation/create-basic-heads#skin-joints) |
| Testing and validation | | [Calisthenics tool](/docs/art/modeling/calisthenics-tool)
[Clothing validation tool](/docs/art/accessories/validation-tool) |
| Publishing and Marketplace | | [Upload to Marketplace](/docs/marketplace/publish-to-marketplace)
[Marketplace policy](/docs/marketplace/marketplace-policy)
[Fees and commissions](/docs/marketplace/marketplace-fees-and-commissions) |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
