<!-- Source: https://create.roblox.com/docs/art/modeling -->

Custom 3D assets | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/art/modeling.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Assets](/docs/en-us/assets)
4. /
5. Modeling

# Custom 3D assets

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/art/modeling/index.md)

Meshes are custom 3D assets  that let you personalize and stylize your game's environment and characters. Unlike parts, which you can directly create in Studio, you need to use a third-party modeling application like [Blender](https://www.blender.org)  or [Maya](https://www.autodesk.com/products/maya/overview)  to design and model meshes, then import them into Studio. Studio represents imported meshes as [MeshPart](/docs/reference/engine/classes/MeshPart)  objects, descendants of the [BasePart](/docs/reference/engine/classes/BasePart)  class.

Many 3D assets are made up of several meshes that are parented to a single [Model](/docs/reference/engine/classes/Model)  object.

Meshes typically fall into one of three types of application in games:

-

Meshes for decorating your game's environment , such as plants, buildings, and vehicles.

-

Meshes for individual body parts  for avatars or non-player characters (NPCs).

-

Meshes for cosmetic accessories  that characters can equip and wear, such as clothing, props, and weapons.

Each mesh type must meet specifications according to how you are going to use the mesh on the platform. For example, while all meshes must meet general mesh specifications, meshes for characters must also meet character specifications that account for rigging and skinning data. For a full list of specifications for different types of meshes, see [Resources](#resources) .

In addition, if you meet certain account requirements, you can publish and sell collections of meshes that are parented to a single [Model](/docs/reference/engine/classes/Model)  object. For example, you can publish avatar-ready models on the Marketplace and earn a commission for each sale, or you can sell models on the Creator Store and earn 100% of net proceeds on each transaction.

For more information on monetizing meshes, see [Monetize avatar items](/docs/monetize-avatar)  and [Creator Store - Distribute and sell assets](/docs/production/creator-store#distribute-and-sell-assets) .

![A cluttered interior room with a candle in the forefront and spooky interior lighting from the Mystery of Duvall Drive game](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Mystery-of-Duvall-Example.png) Use custom meshes and models to give your environments ambiance and depth

![A floating alien creature in space, from the Beyond The Dark game](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Beyond-The-Dark-Example.png) Design a custom character unique to your game

![A Roblox avatar wearing a glossy puffy jacket and jeans](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Layered-Clothing-Example.png) Create custom accessories, clothing, and characters that anyone can wear and use

## [Supported 3D assets](#supported-3d-assets)[](#supported-3d-assets)

Roblox supports many types of custom 3D assets, as long as they adhere to the [general mesh specifications](/docs/art/modeling/specifications) . A basic custom 3D asset consists of at least one [MeshPart](/docs/reference/engine/classes/MeshPart)  object and one texture:

![A plain white tree mesh without a texture](https://prod.docsiteassets.roblox.com/assets/art/Basic-Mesh-Example.png) A [MeshPart](/docs/reference/engine/classes/MeshPart)  object sets the shape and geometry of the 3D asset

![Various color maps used to apply textures to the tree bark, and inner, middle, and outer leaves](https://prod.docsiteassets.roblox.com/assets/art/Basic-Texture-Example.png) A texture image map applies a surface appearance and color

![The tree mesh and the image maps combined to create a single tree](https://prod.docsiteassets.roblox.com/assets/art/Basic-Mesh-Combined-Example.png) The mesh and texture combine to make a unique custom 3D asset

Studio also supports custom 3D assets that include [rigging and skinning](#rigging-and-skinning)  data, [PBR textures](#pbr-textures) , and other [Studio-related objects](#studio-related-objects)  like cage meshes and attachments. Many of these various components are required if you are creating avatar character models or accessories.

### [Rigging and skinning](#rigging-and-skinning)[](#rigging-and-skinning)

A rigged mesh  is a [MeshPart](/docs/reference/engine/classes/MeshPart)  object with an internal poseable skeleton rig and bone structure. Rigged meshes allow mesh surfaces to rotate and move where internal bone joints are placed within a model, such as a character's knee or elbow. Skinning a rigged mesh allows the mesh to bend organically, imitating the natural way joints would move in real life.

Without skinning, the entire head mesh rotates on a single axis

With skinning, the head mesh bends naturally at the neck, and the bottom of the neck stays connected to the torso

For more information on rigging and skinning, see [Rigging and skinning](/docs/art/modeling/rigging) .

### [PBR textures](#pbr-textures)[](#pbr-textures)

Physically-Based rendering  (PBR) textures allow you to represent realistic shading and lighting by using multiple types of texture images, or maps , on a single 3D asset. Combining multiple texture maps can more accurately simulate color, roughness, and reflectivity in any lighting environment, and can enhance the visual elements of your assets and environment.

![A realistic looking leafy bush with shadows and depth.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-Example-1.jpg)

![A realistic looking rock with moss on the top.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-Example-3.jpg)

For more information on PBR textures, see [PBR textures](/docs/art/modeling/surface-appearance) .

### [Studio-related objects](#studio-related-objects)[](#studio-related-objects)

Studio automatically converts certain types of objects found in 3D modeling files as specific workspace objects in the game. These are typically used when creating a character or accessory, and configuring these in your modeling software can sometimes be the primary way of correctly setting up these Studio objects.

The following objects are automatically created in Studio if they are detected by the 3D Importer:

-

[Attachment](/docs/reference/engine/classes/Attachment)  - Created when Studio detects mesh objects that include _Att  at the end of their name.

-

[WrapTarget](/docs/reference/engine/classes/WrapTarget)  - Created when Studio detects mesh objects that include _OuterCage  at the end of their name.

-

[WrapLayer](/docs/reference/engine/classes/WrapLayer)  - Created when Studio detects a mesh object with _InnerCage  and similarly named mesh object with _OuterCage  at the end of their names.

-

[FaceControls](/docs/reference/engine/classes/FaceControls)  - Created when Studio detects an avatar character head and the appropriate facial animation data in the model.

For more information on how the [WrapTarget](/docs/reference/engine/classes/WrapTarget)  and [WrapLayer](/docs/reference/engine/classes/WrapLayer)  objects reshape and layer meshes, see [Cage meshes](/docs/art/modeling/cage-meshes) .

## [Resources](#resources)[](#resources)

There are a variety of resources available for creators of all backgrounds to get started with custom 3D assets.

If you are interested in specific avatar creation topics, use the following table to find guides and resources that best match your needs:

| Topic | | Resources |
| --- | --- |
| Reference files | | [Example models, project kits, and templates](/docs/art/modeling/project-files) |
| Technical specs | | [.FBX export settings](/docs/art/modeling/export-requirements)
[General mesh specifications](/docs/art/modeling/specifications)
 [Avatar specifications](/docs/avatar/character-bodies/specifications)
[Accessory specifications](/docs/avatar/rigid-accessories)
[Marketplace policy](/docs/marketplace/marketplace-policy) |
| Bodies and clothing creation | | [Accessories overview](/docs/avatar/rigid-accessories)
[Bodies overview](/docs/avatar/character-bodies)
[Face accessory creation](/docs/art/characters/facial-animation/create-face-accessories)
[Accessory Fitting Tool](/docs/avatar/accessory-fitting-tool)
[Accessory specifications](/docs/avatar/rigid-accessories/specifications)
[Marketplace requirements](/docs/marketplace/marketplace-policy) |
| Texturing | | [Texture specifications](/docs/art/modeling/texture-specifications)
[PBR textures](/docs/art/modeling/surface-appearance) |
| Rigging and skinning | | [Rigging and skinning overview](/docs/art/modeling/rigging)
[Basic mesh rigging](/docs/art/modeling/rig-a-simple-mesh)
[Facial bone rigging](/docs/art/characters/facial-animation/create-basic-heads#rig-and-skin-the-head)
[Facial bone skinning](/docs/art/characters/facial-animation/create-basic-heads#skin-joints)
[Avatar rigging requirements](/docs/avatar/character-bodies/specifications#rigging)
[Automatic skinning transfer](/docs/avatar/automatic-skinning-transfer) |
| Facial animation and live heads | | [Basic head creation](/docs/art/characters/facial-animation/create-basic-heads)
[Face accessory creation](/docs/art/characters/facial-animation/create-face-accessories)
[FACS pose references](/docs/avatar/dynamic-heads/facs-poses-reference) |
| Testing and validation | | [Calisthenics Tool](/docs/art/modeling/calisthenics-tool)
[Clothing Validation Tool](/docs/art/accessories/validation-tool) |
| Publishing and Marketplace | | [Upload to Marketplace](/docs/marketplace/publish-to-marketplace)
[Marketplace policy](/docs/marketplace/marketplace-policy)
[Fees and commissions](/docs/marketplace/marketplace-fees-and-commissions) |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
