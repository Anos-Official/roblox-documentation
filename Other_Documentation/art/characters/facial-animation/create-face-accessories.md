<!-- Source: https://create.roblox.com/docs/art/characters/facial-animation/create-face-accessories -->

Create face accessories | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/art/characters/facial-animation/create-face-accessories.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Tutorials](/docs/en-us/tutorials)
4. /
5. Avatar items

# Create face accessories

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/art/characters/facial-animation/create-face-accessories.md)

This tutorial covers advanced topics.  Before you begin, you should have prior knowledge on modeling, UV mapping, rigging, animation, and how to set up a character in [Blender](https://www.blender.org)  or [Maya](https://www.autodesk.com/products/maya/overview) .

Face accessories are a type of [layered accessory](/docs/avatar/layered-accessories)  that equip to [dynamic heads](/docs/avatar/dynamic-heads) . As the head animates and emotes, face accessories like eyebrows, eyelashes, or glasses stretch and deform with the character's facial features.

You can create a face accessory model in third-party modeling software, such as [Blender](https://www.blender.org)  or [Maya](https://www.autodesk.com/products/maya/overview) . When creating a face accessory, your accessory model must meet the following requirements:

-

The accessory model must meet Studio's [modeling requirements](#modeling-requirements) .

-

The model must be parented (Blender) or bound (Maya) to a character with a [standard](/docs/avatar/character-bodies/specifications#standard-r15-rigs)  or [advanced](/docs/avatar/character-bodies/specifications#advanced-r15-rigs)  R15 rig.

-

The model must include an inner and outer cage.

To help you meet these requirements, this tutorial covers the processes of connecting accessories to a Cubie character body's rigging armature from [Create basic dynamic heads](/docs/art/characters/facial-animation/create-basic-heads) , applying skinning data, and adding cages to the accessory, as well as how to export the accessory for import into Studio.

This tutorial uses [Blender version 5.2](https://www.blender.org/download/releases/5-2/) . If you are using another version of Blender, there might be minor differences in UI and settings.

## [Reference files](#reference-files)[](#reference-files)

The following face accessory reference files include all checkpoint references throughout this tutorial:

The reference Cubie character model is for educational purposes only. It does not meet the technical avatar [character body specifications](/docs/avatar/character-bodies/specifications)  to be ready for the Marketplace.

| Name | | Description |
| --- | --- |
| [Cubie-Complete.fbx](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-dynamic-heads/reference-files/Cubie-Complete.fbx) | | The complete Cubie reference character, from [Create basic dynamic heads](/docs/art/characters/facial-animation/create-basic-heads) . This file is ready for import into Studio. |
| [Cubie-Cage-Only.fbx](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/reference-files/Cubie-Cage-Only.fbx) | | The full body cage mesh of the Cubie reference character. This includes the inner and outer cage meshes. |
| [Cubie-Eyebrow-Geo.fbx](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/reference-files/CubieEyebrow_Geo.fbx) | | A standalone eyebrow model, designed for the Cubie model. |
| [Cubie-Eyebrow-Rigged-And-Caged.fbx](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/reference-files/Cubie-Eyebrow-Rigged-And-Caged.fbx) | | The Cubie eyebrow model, correctly rigged and caged following the instructions in this tutorial. This file is ready for import into Studio. |
| [Cubie-Hawk-Hair.fbx](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/reference-files/CubieHawkHair_Geo.fbx) | | A hair model reference, designed for the Cubie model. |
| [Creating-Face-Accessories-Reference-Files.zip](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/reference-files/Creating-Face-Accessories-Reference-Files.zip) | | A collection of all the provided reference files. |

## [Modeling requirements](#modeling-requirements)[](#modeling-requirements)

This tutorial uses a simple eyebrow reference as a demonstration on how to create a face accessory. If you're rigging and caging a different face accessory, ensure that your accessory model meets Roblox's [layered accessory specifications](/docs/avatar/layered-accessories/specifications) , including the [face accessory](/docs/avatar/layered-accessories/specifications#face-accessories)  requirements.

If creating your own face accessory mesh, consider the following guidelines:

-

Model your face accessory mesh with your character body model for best results and fit.

-

When possible, try to match up the edges of your face accessory's geometry with the edges/vertices of the underlying head topology. This improves the deformation of the accessory with the underlying head model.

-

Some accessories like eyebrows can extrude or slightly intersect the character model mesh to achieve a certain cosmetic look.

-

When working with a face accessory with multiple pieces, such as eyebrows or eyelashes, combine the meshes to a single mesh once you are done modeling and rigging.

-

Face accessory meshes do not require a _Geo  naming convention.

## [Rig the eyebrows](#rig-the-eyebrows)[](#rig-the-eyebrows)

Rigging  is the process of connecting a mesh with an internal rig so that mesh surfaces can rotate and move as joints rotate and move. You must [rig](/docs/art/modeling/rigging)  your face accessory to a character body's bone structure so that the accessory can bend and deform along with the character's facial poses.

After rigging, you can skin your model in your modeling tool, or you can transfer skinning data from your character to the face accessory at runtime by using [Automatic skinning transfer](/docs/avatar/automatic-skinning-transfer) .

### [Project setup](#project-setup)[](#project-setup)

This tutorial uses a simple eyebrow model and the complete version of the dynamic head model from [Create basic dynamic heads](/docs/art/characters/facial-animation/create-basic-heads)  in a new Blender project.

To set up your Blender project:

1.

Open a new General  project in Blender.

2.

Select the default shape, camera, and lights, then press Delete .

3.

Import [Cubie-Complete](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-dynamic-heads/reference-files/Cubie-Complete.fbx) .

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/Importing-Cubie.png)

4.

To simplify the workspace, delete the inner and outer cage mesh objects. You will import a full-body cage later in the tutorial.

5.

Import [CubieEyebrow_Geo](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/reference-files/CubieEyebrow_Geo.fbx) . If necessary:

1.

Reposition the accessory model on the face.

2.

Hide the armature temporarily to verify model placement.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/Importing-Eyebrows.png)

### [Parent accessory to armature](#parent-accessory-to-armature)[](#parent-accessory-to-armature)

Now that you have the accessory in your scene, it's time to connect it to the character's rigging armature so that its joints can move the eyebrows appropriately. It's recommended to parent with automatic weights because it automatically applies influences to your model, which can save you time during the [skinning](#skin-the-eyebrows)  process.

To parent your accessory to the armature:

1.

In Object  mode, hold Shift  and click CubieEyebrow .

2.

While still holding Shift , click any of the character joints.

3.

Right-click in the viewport, then select Parent  > Armature Deform  > With Automatic Weights .

You can parent with Empty Weights  to not apply any skinning influence to your accessory mesh, giving you more manual control over the skinning process. For more information, see Blender's official [Automatic Weights](https://docs.blender.org/manual/en/latest/animation/armatures/skinning/parenting.html#with-automatic-weights)  documentation.

## [Skin the eyebrows](#skin-the-eyebrows)[](#skin-the-eyebrows)

Skinning  is the process of assigning which parts of the mesh surface move and rotate with specific joints. In many cases, you can skip the skinning process for your accessory and use Studio's [Automatic Skinning Transfer](/docs/avatar/automatic-skinning-transfer)  process instead. Alternatively, if you want manual control, you can apply manual skinning in Blender using the same process in [Create basic dynamic heads - Skin joints](/docs/art/characters/facial-animation/create-basic-heads#skin-joints) .

Because the complete version of the dynamic head model includes a fully rigged and posed head, you can test your accessory on various FACS poses saved to the timeline within Blender, then adjust your skinning data as necessary.

## [Add cages](#add-cages)[](#add-cages)

The caging process for face accessories is similar to caging layered accessories and shares the same modeling and caging requirements. After you finish rigging, it's time to import a full-body inner and outer cage to your project, rename the cages, then stretch the vertices of the Outer Cage to cover the accessory model with minimal space.

To cage the eyebrow accessory:

1.

Import [Cubie-Cage-Only](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/reference-files/Cubie-Cage-Only.fbx) . This includes a single full-body inner and outer cage mesh for the Cubie model.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/Importing-Cage.png)

2.

Rename cages to begin with CubieEyebrow  before the _InnerCage  and _OuterCage  affix.

3.

In Edit  mode, extend the outer cage to fit over the accessory with minimal space. Use various material and viewing options to easily manipulate the correct vertices on the outer cage.

If you are using automatic skinning transfer, you can ensure that automatic skinning transfer only applies to specific parts of the accessory by removing unnecessary sections of the cage. For more information, see [Automatic Skinning Transfer - Modify character cages](/docs/avatar/automatic-skinning-transfer#modify-character-cages) .

## [Export your accessory](#export-your-accessory)[](#export-your-accessory)

Export your model when ready to test your accessory model in Studio or when setting up for final export. When exporting face accessories, keep in mind the following guidelines:

-

Ensure that the final accessory model follows Roblox's [layered accessory specifications](/docs/avatar/layered-accessories/specifications) , including properly named mesh and cage objects.

-

Do not export any unnecessary data, such as animation data, or light and camera objects.

-

If exporting PBR textures, follow Roblox's [texture specifications](/docs/avatar/layered-accessories/specifications#textures)  when exporting texture images from your texture software.

To export your face accessory:

1.

Ensure only the accessory mesh , armature object  and cage meshes  are exported. Delete all other objects in the workspace. You can quickly filter out Geo  and Att  named objects in your workspace to quickly delete them.

2.

Follow the [layered accessories export settings](/docs/avatar/layered-accessories/export#blender-export-settings)  and save the file to your preferred location. The final export of the eyebrow .fbx  is available for reference.

## [Test in Studio](#test-in-studio)[](#test-in-studio)

To use your exported model into Studio as an [Accessory](/docs/reference/engine/classes/Accessory) , use the [Accessory Fitting Tool](/docs/avatar/accessory-fitting-tool)  to test and generate the accessory object. At this point, you can equip the accessory to a humanoid character. If you intend to transfer skinning data from your character to the accessory model at runtime, also enable [automatic skinning transfer](/docs/avatar/automatic-skinning-transfer)  for your accessory.

If following the references provided by this tutorial, only EnabledOverride  applies the skinning transfer in Studio, since some skinning data will have been applied to the model during the [parenting](#parent-accessory-to-armature)  process.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
