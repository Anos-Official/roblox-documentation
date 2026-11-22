<!-- Source: https://create.roblox.com/docs/avatar/dynamic-heads -->

Dynamic heads | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar/dynamic-heads.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. Animations
6. /
7. Dynamic heads

# Dynamic heads

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar/dynamic-heads/index.md)

Dynamic heads  are rigged avatar character heads that support facial animations and custom expressions. When users purchase dynamic heads on the [Marketplace](https://www.roblox.com/catalog) , they can trigger emotes that combine both facial and body animations.

There are four main layers of a dynamic head that structure how the head looks and works on the platform:

-

Mesh & textures  that make up the head's visual appearance.

-

Facial animation data  that determine how the character's face moves and expresses the character's personality and emotions.

-

Cage meshes  that determine how the character's head equips facial accessories that deform with facial expressions, such as facial hair that moves accordingly when the character changes facial expressions.

-

Attachments  that determine how the character's head attaches accessories like hair and hats.

While you can create each of these layers manually in third-party modeling tools like [Blender](https://www.blender.org/)  or [Maya](https://www.autodesk.com/products/maya/overview) , some have strict configuration requirements to meet Roblox's technical [dynamic head specifications](/docs/avatar/dynamic-heads/specifications)  that guarantee your dynamic head animates consistently from game to game. Before you create your first custom dynamic head, it's recommended to:

1.

Understand the [essential components](#dynamic-head-components)  of a dynamic head and how they work together.

2.

Review all [resources](#resources)  that Roblox provides to standardize and expedite the [creation process](#creation-process) , such as Blender and Maya project files, Studio tooling, and step-by-step guides.

3.

Follow the [basic dynamic head creation tutorial](/docs/art/characters/facial-animation/create-basic-heads)  that covers how to add facial joints, apply skinning data, pose joints into expressions, and map poses on a head model in Blender.

Once you have a custom dynamic head, you can import it with a character body into Studio and use the Avatar Setup tool to process your creation into an avatar asset that's ready to be sold on the [Marketplace](/docs/marketplace) .

## [Dynamic head components](#dynamic-head-components)[](#dynamic-head-components)

All dynamic heads are made up of the same fundamental components that allow users to equip facial accessories that stretch, fit, and layer over a target character's head with consistent behavior.

### [Mesh part](#mesh-part)[](#mesh-part)

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Character-Head-Geo.png)  Masculine dynamic head mesh object.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Character-Head-Geo-2.png)  Feminine dynamic head mesh object.

All dynamic heads require a single mesh object that represents the head's geometry. In Studio, this mesh object is represented as a [MeshPart](/docs/reference/engine/classes/MeshPart)  object nested under a single [Model](/docs/reference/engine/classes/Model) .

### [Textures](#textures)[](#textures)

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Textures-Brown.png)  Textures apply color and surface details to your character model.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Textures-Blue.png) A texture image map's opacity can combine with the [MeshPart.Color](/docs/reference/engine/classes/MeshPart#Color)  to apply custom skin tones to characters.

Textures are image files that define the surface appearance of your character's head. You can create textures using a texture painting program or 3D modeling software. In Studio, you must import textures as image files and set them to [MeshPart](/docs/reference/engine/classes/MeshPart)  objects by a child [SurfaceAppearance](/docs/reference/engine/classes/SurfaceAppearance)  object or the mesh's [TextureID](/docs/reference/engine/classes/MeshPart#TextureID)  property.

### [Face animation data](#face-animation-data)[](#face-animation-data)

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Facial-Rig-Visual.png)  Each avatar character face is rigged and skinned to create various expressions

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Facial-Properties.png) Each pose is mapped to a pose name within the Custom Properties (Extra Attributes in Maya) of the Head_Geo object

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Facial-Animation-Timeline.png) Each required face pose is saved as a keyframe in the animation timeline.

Facial animation data from the character's facial joints allow avatars to express emotions with their eyes, mouth, and teeth. Each character includes facial joints, skinning data, animation timeline data, and mapped pose data that allows these expressions. In Studio, these facial animation elements are represented by a [FaceControls](/docs/reference/engine/classes/FaceControls)  instance.

### [Cage meshes](#cage-meshes)[](#cage-meshes)

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Cage-Mesh-Visual-DH.png)  Head geometry and cage mesh objects (wireframe)

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Cage-Mesh-Data-Model-2.png) Cage objects must exist for each of the 15 body parts, including the dynamic head

Cage meshes set the invisible outer boundary for facial accessories to stretch and fit over the character's head, allowing facial accessories to deform as the head animates and emotes. In Studio, outer cage mesh objects are represented by a [WrapTarget](/docs/reference/engine/classes/WrapTarget)  instance.

If you are caging your own non-template character model, it's important to use one of Roblox's body cage [project files](/docs/avatar/resources#mannequin-models)  to ensure you are using a Roblox standard cage mesh. Removing or adding vertices from this standard mesh can cause issues with how facial accessories deform and import.

### [Attachments](#attachments)[](#attachments)

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/DH-Attachments-Visual.png)  Each character has common attachment points for equipping rigid cosmetics

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Attachments-Data-Model-2.png) Each avatar character must include their associated 19 attachment points, including those on the dynamic head

Attachment points set the specific points where rigid accessories and in-game equippable objects attach to the character's head. These are not rendered on the platform, but they are represented visually as spheres in 3D modeling software when you use Roblox's R15 Rig and Attachments  [project file](/docs/avatar/resources#project-files) .

When you import a rig with these visual representations, the spheres are created as [Attachment](/docs/reference/engine/classes/Attachment)  objects using standardized names.

When users wear a layered accessory, the layered accessory isn't attached directly to the attachment, but it does reference the associated attachment point during ragdoll and dismemberment animations.

## [Creation process](#creation-process)[](#creation-process)

When designing a dynamic head in [Blender](https://www.blender.org/)  or [Maya](https://www.autodesk.com/products/maya/overview) , you must export all of the avatar components in a single .fbx  or .gltf  for import into Studio. Since 3D creation isn't a linear process and always requires reiteration and testing, the process of creating a dynamic head can differ between individuals and various creation workflows. Some choose to modify a rigged character model to meet Roblox's [dynamic head specifications](/docs/avatar/dynamic-heads/specifications) , while others prefer to create one from scratch.

In general, the creation process follows the following workflow:

Dynamic Head Workflow![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Workflow-DH.png)

Ensure that all assets you create follow Roblox's [Community Standards](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards)  and any applicable [Marketplace policies](/docs/marketplace/marketplace-policy) .

## [Resources](#resources)[](#resources)

There are a variety of resources available for creators of all backgrounds to get started with dynamic head creation. Review the following table for specific topics and resources:

| Topic | | Resources |
| --- | --- |
| Tutorials | | [Basic dynamic head creation tutorial](/docs/art/characters/facial-animation/create-basic-heads)
[Basic facial accessory creation tutorial](/docs/art/characters/facial-animation/create-face-accessories) |
| Reference files | | [Avatar references and project files](/docs/avatar/character-bodies/project-files)
[Example mesh/model objects](/docs/art/modeling/project-files)
[Dynamic head caging best practices](/docs/avatar/dynamic-heads/caging-best-practices)
[FACS pose references](/docs/avatar/dynamic-heads/facs-poses-reference) |
| Technical specs | | [Dynamic head specifications](/docs/avatar/dynamic-heads/specifications)
[General mesh specifications](/docs/art/modeling/specifications)
[Marketplace policy](/docs/marketplace/marketplace-policy) |
| Cosmetic creation | | [Accessories overview](/docs/avatar/rigid-accessories)
[Creating face accessories](/docs/art/characters/facial-animation/create-face-accessories)
[Accessory Fitting Tool](/docs/avatar/accessory-fitting-tool)
[Accessory specifications](/docs/avatar/rigid-accessories/specifications)
[Marketplace requirements](/docs/marketplace/marketplace-policy) |
| Texturing | | [PBR textures](/docs/art/modeling/surface-appearance) |
| Rigging and skinning | | [Rigging and skinning overview](/docs/art/modeling/rigging)
[Humanoid rig requirements](/docs/avatar/character-bodies/specifications#rigging)
[Rigging facial bones](/docs/art/characters/facial-animation/create-basic-heads#rig-and-skin-the-head)
[Skinning facial bones](/docs/art/characters/facial-animation/create-basic-heads#skin-joints)
[Automatic Skinning Transfer](/docs/avatar/automatic-skinning-transfer) |
| Animation | | [Animate dynamic heads](/docs/art/characters/facial-animation/animate-heads) |
| Testing and validation | | [Test dynamic heads](/docs/avatar/dynamic-heads/test)
[Validation process](/docs/avatar/dynamic-heads/validate) |
| Publishing and Marketplace | | [Uploading to Marketplace](/docs/marketplace/publish-to-marketplace)
[Marketplace policy](/docs/marketplace/marketplace-policy)
[Fees and commissions](/docs/marketplace/marketplace-fees-and-commissions) |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
