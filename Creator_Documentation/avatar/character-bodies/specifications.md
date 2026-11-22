<!-- Source: https://create.roblox.com/docs/en-us/avatar/character-bodies/specifications -->

Character body specifications | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar/character-bodies/specifications.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. Bodies

# Character body specifications

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar/character-bodies/specifications.md)

Character body models require a specific set of components and configuration standards to ensure all avatar features work as expected across the platform. Before you start the export process, verify that your model meets the following modeling specifications and guidelines for proper Studio compatibility.

When you're ready to export your character body, reference all [export setting requirements](/docs/en-us/avatar/character-bodies/export)  for Blender and Maya.

For other types of 3D models:

-

[General mesh](/docs/en-us/art/modeling/specifications)  specifications.

-

[Rigid accessory](/docs/en-us/avatar/rigid-accessories/specifications)  specifications.

-

[Layered accessory](/docs/en-us/avatar/layered-accessories/specifications)  specifications.

## [Geometry](#geometry)[](#geometry)

Character body models for avatars are made up of 15 separate mesh objects and require additional geometry requirements to import into Studio and publish successfully. In addition to [body scale types](#body-scale) , [body parts](#body-parts) , and [triangle budget](#triangle-budgets)  specifications, ensure that your models also fulfill the following general requirements when modeling your character's body:

-

Watertight  - All geometry must be watertight without exposed holes or backfaces. Meshes used as outer cages do not need to be watertight.

-

No N-gons  - Model your assets in quads where possible.

-

Transformations  - All translation, rotation, and scale values must be frozen and pivots set to 0 , 0 , 0 .

-

Orientation  - Characters must face positive Z and stand up in positive Y.

-

Pose  - Before exporting, set your character to an I-Pose, A-Pose, or T-Pose when possible.

### [Body scale](#body-scale)[](#body-scale)

Roblox supports three standards of character body scales: Normal , Slender , and Classic . These standards allow developers to create games and spaces with consistent body sizes for standardizing movement and interactions. You can select a body scale on import using [Rig Scale options](/docs/en-us/studio/importer#rig-general) , or modify the [body scale manually](/docs/en-us/avatar/rigid-accessories/specifications#avatarpartscaletype) . Body scale persists when the asset is [uploaded to the Marketplace](/docs/en-us/marketplace/publish-to-marketplace#upload-an-asset) .

![](https://prod.docsiteassets.roblox.com/assets/art/Body-Scale-Diagram.png)

A visualization of how Roblox combines the 15 body parts into 6 distinct assets.

Since body assets partially overlap with each other, the total body dimensions do not represent the sum of the avatar's asset dimensions. The total body dimension is the most important factor for ensuring a standard avatar size and scale.

The same bounding box limits apply to Normal, Slender, and Classic body scales. During validation, Roblox rotates each limb to a standard orientation. The validator measures the length of the rotated part and calculates its width and depth from the part's cross section.

#### [Bounding box limits](#bounding-box-limits)[](#bounding-box-limits)

Minimum (in studs)

| Part | | Width | | Length | | Depth |
| --- | --- |
| Head | | 0.05 | | 0.5 | | 0.05 |
| Arm | | 0.05 | | 0.5 | | 0.05 |
| Torso | | 0.05 | | 0.65 | | 0.05 |
| Leg | | 0.05 | | 0.5 | | 0.05 |
| Total | | 1.0 | | 4.0 | | 0.5 |

Maximum (in studs)

| Part | | Width | | Length | | Depth |
| Head | | 4.0 | | 2.0 | | 4.0 |
| Arm | | 4.0 | | 4.5 | | 4.0 |
| Torso | | 4.0 | | 4.0 | | 4.0 |
| Leg | | 4.0 | | 4.5 | | 4.0 |
| Total | | 8.0 | | 10.0 | | 4.0 |

![](https://prod.docsiteassets.roblox.com/assets/art/resources/Body-Scale-Rthro-Normal.png)

Normal
An Rthro Normal body scale [downloadable mannequin](/docs/en-us/avatar/resources#references) .
In the [Importer](/docs/en-us/studio/importer#avatar-general) , use Rig Type  > Rthro  to import your model as a Normal body scale.

![](https://prod.docsiteassets.roblox.com/assets/art/resources/Body-Scale-Rthro-Slender.png)

Slender
An Rthro Slender (Narrow) body scale [downloadable mannequin](/docs/en-us/avatar/resources#references) .
In the [Importer](/docs/en-us/studio/importer#avatar-general) , use Rig Type  > Rthro Narrow  to import your model as a Slender body scale.

![](https://prod.docsiteassets.roblox.com/assets/art/resources/Body-Scale-Classic.png)

Classic
A Classic body scale [downloadable mannequin](/docs/en-us/avatar/resources#references) .
In the [Importer](/docs/en-us/studio/importer#avatar-general) , use Rig Type  > Default  to import your model as a Classic body scale.

### [Triangle budgets](#triangle-budgets)[](#triangle-budgets)

Although character body model geometries are typically created using quads, the Roblox Engine converts imported assets into tris. Each asset of your character model must not exceed our maximum tri budget. To quickly get the number of expected tris in your third-party modeling application, you can double the number of quads in your model.

When character body models are uploaded to Studio and created into assets for the Marketplace, the body is split into 6 individual assets: DynamicHead , Torso , LeftArm , RightArm , LeftLeg , RightLeg .

| Asset type | | Included mesh objects | | Maximum triangles |
| DynamicHead | | Head | | 4000 |
| Torso | | UpperTorso, LowerTorso | | 1750 |
| LeftArm  | | LeftUpperArm, LeftLowerArm, LeftHand | | 1248 |
| Right Arm | | RightUpperArm, RightLowerArm, RightHand | | 1248 |
| LeftLeg  | | LeftUpperLeg, LeftLowerLeg, LeftFoot | | 1248 |
| Right Leg | | RightUpperLeg, RightLowerLeg, RightFoot | | 1248 |
| Total | | Head, UpperTorso, LowerTorso, LeftUpperArm, LeftLowerArm, LeftHand, RightUpperArm, RightLowerArm, RightHand, LeftUpperLeg, LeftLowerLeg, LeftFoot, RightUpperLeg, RightLowerLeg, RightFoot | | 10,742 |

### [Body parts](#body-parts)[](#body-parts)

See the following specifications for the individual mesh objects that make up a character body model:

-

Naming Convention  - Limbs must all be specifically named:

-

UpperTorso_Geo

-

LowerTorso_Geo

-

LeftUpperArm_Geo

-

LeftLowerArm_Geo

-

LeftHand_Geo

-

RightUpperArm_Geo

-

RightLowerArm_Geo

-

RightHand_Geo

-

LeftUpperLeg_Geo

-

LeftLowerLeg_Geo

-

LeftFoot_Geo

-

RightUpperLeg_Geo

-

RightLowerLeg_Geo

-

RightFoot_Geo

-

Head_Geo

-

Caps  - Limbs must be capped, so that they form a full watertight mesh when separated from the body. Caps can be rounded or flat depending on design.

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Modeling-Requirements-Caps.png)

Interested in creating a higher-fidelity avatar?

Higher-fidelity character body models require the same 15 mesh objects and naming structure. The only difference is that the mesh objects in higher-fidelity character body models can have [additional internal joints](#advanced-r15-rigs)  in their rigging armatures. When these joints are present in a character body model, their corresponding mesh objects need to be [skinned](#skinning)  for accurate deformation.

### [Face accessories](#face-accessories)[](#face-accessories)

Face accessories, such as eyebrows and eyelashes, are unique layered accessories that you can bundle with an avatar character body upload. Eyebrows and eyelashes cannot be uploaded as standalone accessories and must be bundled either with a character body or [makeup assets](/docs/en-us/avatar/makeup/specifications) . For more information on face accessories, see [Layered accessory specifications - Face accessories](/docs/en-us/avatar/layered-accessories/specifications#face-accessories) .

### [Visibility](#visibility)[](#visibility)

To ensure that avatar sizes are visually consistent, you must standardize body part visibility with the following requirements:

-

Opacity  - Body parts must be fully opaque.

-

Bounding Boxes  - Body part assets must take up a significant visible portion of their bounding box in a front, side, and back view.

-

Body parts, such as Torso, Left Arm, Right Leg, must take up at least 50% of body part's bounding box.

-

The head part must take up at least 50% of the mesh's bounding box.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Valid-Visibility.png) An acceptable head mesh example that takes up a majority of the bounding box in the front view

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Invalid-Visibility.png) A non-acceptable head mesh example that does not take up the appropriate amount of bounding box space in the front view

## [Attachments](#attachments)[](#attachments)

Attachments are points that determine the specific location where accessories and in-game equippable objects attach to the character's body. Like many [character components](/docs/en-us/avatar/character-bodies#character-body-components) , attachment points are set up in third-party modeling software and imported as [Attachment](/docs/en-us/reference/engine/classes/Attachment)  objects.

The Importer automatically recognizes and converts mesh objects as attachment points if the objects include the affix \_Att  and follow the naming conventions below. This only applies when importing meshes with caging data, such as bodies (accessory attachment points are created using the Accessory Fitting Tool). Check out examples of this implementation in any of Roblox's [downloadable reference models](/docs/en-us/avatar/resources#references) .

Generally, when placing attachment points, position them so they overlap halfway with the character model's mesh part.

![](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Collar-Attachment-1.png) Incorrect placement of collar attachments

![](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Collar-Attachment-2.png) Correct placement of collar attachments

For accessories that attach to the head, position the attachment point so it fits on the visible surface of the head mesh. Attachment points that float away from the visible head violate [Marketplace policy](/docs/en-us/marketplace/marketplace-policy#general-creation-guidelines) .

![](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/Correct-Head-Attachment.png) Correct placement of head attachments

![](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/Incorrect-Head-Attachment.png) Incorrect placement of head attachments

Attachments must follow a specific naming convention and positional consistency:

| Mesh part | | Attachment name | | Details |
| Head | | FaceCenter_Att | | Anywhere within mesh bounding box |
| FaceFront_Att | | Front half of mesh bounding box |
| Hat_Att | | Top half of mesh bounding box, can overlap with Hair_Att |
| Hair_Att | | Top half of mesh bounding box, can overlap with Hat_Att |
| UpperTorso | | LeftCollar_Att | | Left top half of mesh bounding box |
| RightCollar_Att | | Right top half of mesh bounding box |
| Neck_Att | | Top half of mesh bounding box |
| BodyBack_Att | | Back half of mesh bounding box |
| BodyFront_Att | | Front half of mesh bounding box |
| LowerTorso | | Root_Att | | Must set to 0 , 0 , 0  position |
| WaistFront_Att | | Front half of mesh bounding box, can overlap with WaistCenter_Att |
| WaistBack_Att | | Back half of mesh bounding box |
| WaistCenter_Att | | Anywhere in mesh bounding box, can overlap with WaistFront_Att |
| RightUpperArm | | RightShoulder_Att | | Top half of mesh bounding box |
| RightHand | | RightGrip_Att | | Anywhere in mesh bounding box.
Orient grip attachments perpendicular  to the lower arm bone. For example, for I-Pose (arms pointing down), set the grip attachment to 90 , 0 , 0  (grip attachment pointing forward).
![](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Grip-Attachments-Right.png) |
| LeftUpperArm | | LeftShoulder_Att | | Top half of mesh bounding box |
| LeftHand | | LeftGrip_Att | | Anywhere in mesh bounding box.
Orient grip attachments perpendicular  to the lower arm bone. For example, for I-Pose (arms pointing down), set the grip attachment to 90 , 0 , 0  (grip attachment pointing forward).
![](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Grip-Attachments-Left.png) |
| RightFoot | | RightFoot_Att | | Anywhere in mesh bounding box |
| LeftFoot | | LeftFoot_Att | | Anywhere in mesh bounding box |

## [Rigging](#rigging)[](#rigging)

Unlike generic rigs, humanoid models require a specific hierarchy and naming conventions for the internal bone or joint structure.

![](https://prod.docsiteassets.roblox.com/assets/animation/importing-custom-3d-rigs/Birdcaller-Imported.jpeg) Humanoid rig model

![](https://prod.docsiteassets.roblox.com/assets/animation/importing-custom-3d-rigs/Rig-Hierarchy-Birdcaller-Blender-Bones.png) Humanoid rig bone structure (Blender)

### [Standard R15 rigs](#standard-r15-rigs)[](#standard-r15-rigs)

The following requirements are for standard R15  rigs.

-

Rig Hierarchy  - Humanoid rigs require a specific bone or joint hierarchy and naming convention:

-

Root

-

HumanoidRootNode

-

LowerTorso

-

UpperTorso

-

Head (representing the base of the neck)

-

LeftUpperArm

-

LeftLowerArm

-

LeftHand

-

RightUpperArm

-

RightLowerArm

-

RightHand

-

LeftUpperLeg

-

LeftLowerLeg

-

LeftFoot

-

RightUpperLeg

-

RightLowerLeg

-

RightFoot

Blender standard humanoid rig hierarchy with all bones

![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Rig-Hierarchy-Blender.png)

Maya standard humanoid rig hierarchy with all joints

![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Rig-Hierarchy-Maya.png)

-

LowerTorso and Root  - The LowerTorso and Root bone or joint position must be set to 0 , 0 , 0 .

-

Pose  - Export your character model in an I-Pose, A-Pose, or T-Pose for the best Studio compatibility. The LeftUpperArm and RightUpperArm bones can be exported with rotation values to meet this requirement.

### [Advanced R15 rigs](#advanced-r15-rigs)[](#advanced-r15-rigs)

Advanced R15  rigs have the same requirements as standard rigs, but they support up to 37 additional optional bones or joints for a higher level of realism with articulated hands, shoulders, and spine movements.

You do not need to include every optional bone or joint for an advanced R15 rig, but each optional bone or joint you include must follow a specific hierarchy and naming convention for the respective body part.

Torso LeftHand RightHand LeftFoot RightFoot

| Hierarchy | | Example Rig Setup |
|
-

UpperTorso
-

Spine
-

Chest
-

Head
-

HeadBase

-

RightClavicle
-

RightUpperArm

-

LeftClavicle
-

LeftUpperArm

 | | ![](https://prod.docsiteassets.roblox.com/assets/avatar/specifications/High-Fidelity-Torso.png) |

Blender humanoid rig hierarchy with all optional bones

![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/R15Plus-Rig-Hierarchy-Blender.png)

Maya humanoid rig hierarchy with all optional joints

![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/R15Plus-Rig-Hierarchy-Maya.png)

Make sure that you skin each additional bone or joint's corresponding mesh object for accurate deformation.

After you [import an advanced R15 character rig](/docs/en-us/avatar/character-bodies/import)  into Studio, you must  insert [HumanoidRigDescription](/docs/en-us/reference/engine/classes/HumanoidRigDescription)  and/or [DigitsRigDescription](/docs/en-us/reference/engine/classes/DigitsRigDescription)  objects into your rig to be able to sell your character on the Marketplace, and for your animations to work properly:

-

[HumanoidRigDescription](/docs/en-us/reference/engine/classes/HumanoidRigDescription)  objects are necessary for animating individual body parts and adjusting behavioral characteristics of the rig, such as each bone or joint's size and range of motion.

-

[DigitsRigDescription](/docs/en-us/reference/engine/classes/DigitsRigDescription)  objects are necessary for hand articulation. Your character needs one for each hand with optional bone or joints.

Both of these object types detect bones or joints by their naming conventions, so it is very important to ensure every optional bone or joint is named correctly following the table above before  you import your character rig into Studio. For a set of advanced R15 rigs that you can reference, see [Resources - Advanced R15 rigs](/docs/en-us/avatar/resources#advanced-r15-rigs) .

## [Skinning](#skinning)[](#skinning)

Roblox supports skinning for rigged meshes. For more details on implementing skinned meshes in Studio, see [Rigging and Skinning](/docs/en-us/art/modeling/rigging) .

The following requirements are for skinning character bodies:

-

Max Influences  - A vertex can not be influenced by more than 4 bones or joints.

-

No Root Influences  - Do not apply influences to the Root bone or joint.

-

Symmetry  - When possible, maintain symmetry when applying influences to a rig.

## [Facial animation](#facial-animation)[](#facial-animation)

For information on required facial animation support, see [head specifications](/docs/en-us/avatar/dynamic-heads/specifications#facs-poses) .

## [Textures](#textures)[](#textures)

-

Textures for Marketplace assets can't exceed 2048x2048 resolution.

-

Textures created for accessories must meet Roblox's [texture specifications](/docs/en-us/art/modeling/texture-specifications) . High resolution textures are automatically converted to lower-resolution textures to optimize performance.

-

Avatar characters must follow Roblox's [texture specifications](/docs/en-us/art/modeling/texture-specifications) . Characters created for the Marketplace can take advantage of [custom skin tones](#custom-skin-tone) , which use alpha layers to allow users to select their own base color.

### [Custom skin tone](#custom-skin-tone)[](#custom-skin-tone)

When texturing an avatar character body model where the user can set their own skin tone, set the exposed skin areas as transparent so a default color or texture is not baked into the texture. When rendering, Studio applies the transparent layer on top without any layer effects. This step applies mostly to human-like characters with exposed skin that you intend users to customize.

The following are examples of skin tone shading for the face, and you can apply this process with any part of an avatar with exposed skin:

![](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/mesh-requirements/Face-Tone-Transparent.png)

-

Use 100% opacity for areas not related to a customized skin tone, such as eyes and brows.

-

When applying shading, use black at low opacity and adjust opacity when needed.

-

For areas that are partially translucent, such as shading contours or certain cosmetic features, leave some transparency for partial visibility of the skin tone.

-

You should consistently test out how various colors layers can interact with your shading.

![](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/mesh-requirements/Face-Tone-Beige.png) Beige

![](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/mesh-requirements/Face-Tone-Blue.png) Blue

![](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/mesh-requirements/Face-Tone-Brown.png) Brown

![](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/mesh-requirements/Face-Tone-Pink.png) Pink

## [Outer cages](#outer-cages)[](#outer-cages)

Outer cages on your character model allow your character to wear layered accessories, such as shirts and jackets that stretch and wrap around the body. Review the following list for requirements on adding outer cage meshes to your character body model:

-

Use Roblox's [Avatar Setup](/docs/en-us/avatar-setup)  or Roblox's [body cage templates](/docs/en-us/avatar/resources#project-files)  to ensure naming conventions and other configurations are correct.

-

Naming Conventions  - The outer cage of a body part must be named after the primary mesh object with _OuterCage  affixed, for example LeftUpperArm_OuterCage .

-

Vertices and UV Map  - Don't delete vertices or alter the UVs on outer cages as this can cause errors when importing in Studio or when equipping onto a character. Use Roblox's provided templates for cage meshes to ensure compatibility with other layered assets.

-

Symmetry and consistency  - Keep each face of your geometry consistently sized and retain symmetry wherever possible by using symmetry tools in your modeling software.

-

For information on dynamic head cages and best practices when caging, see [Dynamic head specifications](/docs/en-us/avatar/dynamic-heads/specifications#outer-cage) .

-

For best practices and examples when caging the body, see [Character body caging best practices](/docs/en-us/avatar/character-bodies/caging-best-practices) .

Character bodies only require an outer cage, but layered accessories require both an inner and outer cage to deform properly. For more information, see [Layered accessory specifications - Cage meshes](/docs/en-us/avatar/layered-accessories/specifications#cage-meshes) .

## [Marketplace requirements](#marketplace-requirements)[](#marketplace-requirements)

Along with the other technical requirements listed, your items must meet the following additional specifications before uploading them to the Marketplace to sell:

-

Ensure that your character bodies adhere to [Marketplace policies](/docs/en-us/marketplace/marketplace-policy) .

-

Whenever applicable, ensure that your character bodies adhere to Roblox's [custom mesh specifications](/docs/en-us/art/modeling/specifications) .

-

Object [Material](/docs/en-us/reference/engine/classes/MeshPart#Material)  is set to Plastic .

-

Object [Transparency](/docs/en-us/reference/engine/classes/MeshPart#Transparency)  is set to 0 .

-

Object [VertexColor](/docs/en-us/reference/engine/classes/MeshPart#VertexColor)  is the default 1, 1, 1 .

-

If your character's head includes separate eyelash and eyebrow assets, you must add them to your character body model as [Accessory](/docs/en-us/reference/engine/classes/Accessory)  objects. For more information, see [Publish bodies with eyelashes and eyebrows](/docs/en-us/art/accessories/publish-eyebrows-eyelashes) .

-

Your [Model](/docs/en-us/reference/engine/classes/Model)  instance doesn't contain extraneous objects, like [Script](/docs/en-us/reference/engine/classes/Script)  or additional [Part](/docs/en-us/reference/engine/classes/Part)  instances.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
