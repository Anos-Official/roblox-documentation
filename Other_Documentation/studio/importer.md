<!-- Source: https://create.roblox.com/docs/studio/importer -->

Importer | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/studio/importer.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Assets](/docs/en-us/assets)

# Importer

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/studio/importer.md)

The Importer allows you to import 3D models, images, sounds, and video files into Studio. 3D model import supports meshes with PBR textures, meshes with rigging, skinning, and animation data, and meshes designed as avatar items.

Import general 3D custom models into Studio.

Use the Importer to import assets with avatar item components.

To import an asset:

1.

From Studio's File  menu, select Import .

2.

In the file browser, select the [supported file type](#supported-file-types)  you intend to import.

3.

Configure your import settings and verify any [warning or error messages](#warnings-and-errors) .

4.

Click Import .

5.

After importing, you can right-click  the imported asset in the importer and perform the following:

1.

Copy asset ID  - Copies the uploaded asset ID to your clipboard. For models, this copies the asset ID of the [Model](/docs/reference/engine/classes/Model) .

2.

Find in Workspace  (3D models only) - Automatically positions the camera to the location of the imported object in workspace.

To directly import assets using HTTP requests, see the [Open Cloud usage guide for assets](/docs/cloud/guides/usage-assets) .

## [Supported file types](#supported-file-types)[](#supported-file-types)

Before importing a 3D object, ensure that the .fbx , .gltf  or .obj  meets Studio's [mesh requirements](/docs/avatar/character-bodies/specifications)  to reduce errors or unexpected behavior.

| Asset Type | | Details |
| --- | --- |
| Image | | You can import images in .png , .jpg , .gif , .tga , or .bmp  format for use as [textures/decals](/docs/parts/textures-decals)  on parts, [image labels](/docs/ui/labels) , [mesh textures](/docs/parts/meshes#texture) , textures for [custom materials](/docs/parts/materials#custom-materials) , textures for [special effects](/docs/effects) , and more. |
| Mesh | | You can import meshes in the .fbx , .obj , or .gltf  format.
The .fbx  and .gltf  formats support multiple mesh objects and hierachies, basic and [PBR textures](/docs/art/modeling/surface-appearance) , cage mesh objects, [rigs](/docs/art/modeling/rigging) , [avatar components](/docs/avatar) , animation data, and [vertex colors](/docs/art/blender#vertex-painting) .  |
| Audio | | You can import audio assets in either .ogg , .mp3 , .flac , or .wav  format. See [Audio Assets](/docs/audio/assets#import-audio)  for details. |
| Video | | You can import video assets in either .mp4  or .mov  format if all of the [requirements](/docs/ui/video-frames)  are met. |

### [glTF import hierarchy](#gltf-import-hierarchy)[](#gltf-import-hierarchy)

.gltf  and .glb  files import with a different hierarchy than .fbx  files. The following table compares what appears in the Explorer after you import the same mesh with cage meshes in each format.

|  | | .fbx | | .gltf  / .glb |
| Top level | | A [Model](/docs/reference/engine/classes/Model) . | | A [Model](/docs/reference/engine/classes/Model) . |
| Mesh | | A [MeshPart](/docs/reference/engine/classes/MeshPart)  directly inside the top-level Model . | | A [Model](/docs/reference/engine/classes/Model)  inside the top-level Model , containing one [MeshPart](/docs/reference/engine/classes/MeshPart)  for each primitive in the glTF mesh. |
| Cage meshes | | A [WrapLayer](/docs/reference/engine/classes/WrapLayer)  inside the MeshPart . | | A [WrapLayer](/docs/reference/engine/classes/WrapLayer)  inside the MeshPart , plus an extra [Model](/docs/reference/engine/classes/Model)  for each original inner and outer cage node. You can delete these extra models after import. |

In a glTF import, if a node and its mesh have the same name, such as Cover , the Importer adds a _Node  suffix to one of them, such as Cover_Node .

## [Import queue](#import-queue)[](#import-queue)

If you selected multiple files with the Importer, you can use the import queue to bulk manage your various imports.

 ![The Importer interface, showing a preview of the mesh in the top left, a list of 3D objects on the bottom left, and a list of toggle-able properties on the right side.](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/3d-Import-Queue.png)

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-A.png)

The top bar  allows you to add new files, clear the queue, search and filter, and import all enabled assets.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-B.png)

The import queue  lists all added files, with quick access dropdowns to change creator, presets, and file paths.

### [Add files to queue](#add-files-to-queue)[](#add-files-to-queue)

To open a file browser and add additional files to the import queue, you can:

-

Click the Add file  button in the top bar of the import queue window.

-

From Studio's File  menu, select Import .

### [Remove files from queue](#remove-files-from-queue)[](#remove-files-from-queue)

To remove all files from the queue, click the Clear queue  button with the broom icon. To remove an individual file from the queue, right-click an item in the queue and select Delete from queue .

### [Apply preset settings](#apply-preset-settings)[](#apply-preset-settings)

Use the Import Preset  column to select a preset configuration to apply to your asset. For more information, see [Presets](#presets) .

You can also apply the settings of one item to all items by right-clicking an item with the desired settings and selecting Apply settings to all .

### [Access individual preview and settings](#access-individual-preview-and-settings)[](#access-individual-preview-and-settings)

If you are importing a 3D model, click the individual Asset  name of an unimported model to access the [import preview](#import-preview-models)  for that item. Use the import preview to view and check your model, as well as set any individual [import settings](#import-settings) .

### [Import files](#import-files)[](#import-files)

Ensure that each item you want to import has a checkbox enabled in the first column. By default, all items are selected if they are importable.

Press the Import  button to start the import process.

## [Import preview (Models)](#import-preview-models)[](#import-preview-models)

The import preview window appears if you are importing a single model file, or if you selected an individual asset from the import queue. This preview window provides individual controls for the various objects in your model.

The preview window is divided into multiple sections:

 ![The Importer interface, showing a preview of the mesh in the top left, a list of 3D objects on the bottom left, and a list of toggle-able properties on the right side.](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/3d-Importer-Panels.png)

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-A.png)

The file path  of your model file. Click Browse  to edit.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-B.png)

The preset  applied to your import. Use the dropdown to select multiple presets, or the hamburger menu to set a new preset.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-C.png)

The 3D preview  of your model. Use mouse buttons and top-right icons for various camera options and views.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-D.png)

The object hierarchy  of the imported object. Includes mesh objects and other supported components.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-E.png)

The import settings  for your import. For a complete list of settings, see [Import settings](#import-settings) .

### [Import settings](#import-settings)[](#import-settings)

Depending on the object selected in the hierarchy panel, the inspector panel displays the following groups of settings:

-

File General : Affects the entire imported file.

-

Rig General : Affects the selected mesh object if rigging data is present.

-

File Transform : Affects the transform properties of the imported file.

-

File Geometry : Affects the geometry properties of the imported file.

-

Object General : Affects the selected child object.

-

Object Geometry : Affects the geometry of the selected child object.

#### [File general](#file-general)[](#file-general)

The Importer provides the following settings for all meshes:

| Setting | | Description |
| Name | | Sets the name of the imported asset as it will appear in your project. |
| Import Only As Model | | If enabled, the Importer imports the model as a single asset even if the model contains multiple children. By default, this is enabled .
If disabled, the Importer imports the model and all descendants, such as the multiple meshes, as individual assets. |
| Upload to Roblox | | If enabled, the Importer adds the model to your Toolbox  and Asset Manager  inventory as a new asset. By default, this is enabled .
If disabled, the Importer does not add the model to your inventory for later use. This is ideal when you want to test and iterate on a model's design without creating multiple copies in the Toolbox and Asset Manager. |
| Import as Package | | Adds your asset to the workspace as a [package](/docs/projects/assets/packages) , an auto-updating, scalable, and sharable format recommended for assets that are reused or commonly redistributed. By default, this is disabled . |
| Creator | | Sets the creator, or creator group, for the asset. |
| Add to Workspace | | If enabled, the Importer inserts the model into the [Workspace](/docs/reference/engine/classes/Workspace) . If importing from a saved or published game, this setting also grants permission to the game to use the restricted asset. By default, this is enabled .
If disabled, this setting only adds the model to your inventory and does not  grant the game permission to use the asset. |
| Insert Using Scene Position | | If enabled, the Importer uses the current scene position when inserting the model into the workspace. By default, this is disabled . |
| Keep Zero Influence Bones | | If enabled, the importer keeps bones that do not influence the mesh. By default, this is disabled .
If disabled, the importer removes zero influence bones. |
| Set Pivot to Scene Origin | | If enabled, the Importer sets the pivot point of the entire model to the scene origin. By default, this is enabled . |
| Anchored | | If enabled, the Importer sets the [Anchored](/docs/reference/engine/classes/BasePart#Anchored)  property to true  on all the imported [MeshParts](/docs/reference/engine/classes/MeshPart) . This is disabled for meshes with rig data / avatars. By default, this is disabled . |
| Uses Cage | | If enabled, the Importer finds cage meshes in the model and converts them to WrapInstance  objects, such as [WrapLayer](/docs/reference/engine/classes/WrapLayer)  or [WrapTarget](/docs/reference/engine/classes/WrapTarget) . If disabled, the Importer treats them as regular meshes. If the Importer initially detects cage meshes in the model, this is enabled  by default. |

#### [Rig general](#rig-general)[](#rig-general)

The Importer provides the following settings for meshes with rigging data, typically character bodies or clothing accessories:

| Setting | | Description |
| Rig Type | | Sets the type of rig the mesh should be associated with. The options are:
- R15
- Custom
- No Rig
By default, the Importer attempts to select the most appropriate setting based on the detected rigging and skinning data of the mesh.  |
| Validate UGC Body | | After importing, Studio opens the assets in the [Avatar Setup](/docs/avatar-setup)  tool, allowing you to quickly begin testing and uploading avatar assets to the Marketplace. |
| Rig Scale | | If Rig Type is set to R15, the importer provides additional options to specify [body type scaling](/docs/avatar/character-bodies/specifications#body-scale) . The options are:
- Default
- Rthro
- Rthro Narrow |

#### [File transform](#file-transform)[](#file-transform)

The Importer provides the following settings for all meshes:

| Setting | | Description |
| World Forward | | Sets the forward facing axis of the object. By default, this is set to Front . |
| World Up | | Sets the upward facing axis of the object. By default, this is set to Top . |

#### [File geometry](#file-geometry)[](#file-geometry)

File geometry includes information on the file dimensions and polycount of the entire model. You can edit the following settings for all meshes:

| Setting | | Description |
| Scale Unit | | Sets what units the file was modeled in so that it's sized appropriately when imported. By default, this is set to Studs . |
| Merge Meshes | | If enabled, merges all MeshParts in the model into a single MeshPart and creates one MeshPart rather than a Model. By default, this is disabled . |
| Invert Negative Faces | | Inverts the orientation of negative faces in the mesh. By default, this is disabled . |

#### [Object general](#object-general)[](#object-general)

When selecting a specific child object of your mesh, the Importer populates Object General settings. You can edit the following settings for the selected child objects:

| Setting | | Description |
| Name | | Sets the name of the selected child object within the model. |
| Anchored | | If enabled, sets the [Anchored](/docs/reference/engine/classes/BasePart#Anchored)  property to true  on the selected child object. By default, this is disabled . |
| Use Imported Pivot | | If enabled, imports the object using the pivot point set within the child object. By default, this is enabled . |

#### [Object geometry](#object-geometry)[](#object-geometry)

Object Geometry includes information on the dimensions and polycount of the selected child object of the model. You can edit the following settings for the selected child objects:

| Setting | | Description |
| Make Double Sided | | If disabled, sets the vertices as one-sided. One-sided vertices means that you can see through them from one side.
If enabled, sets the vertices as double-sided. Vertices that are double sided visually render on both sides. Double-sided is more performance intensive.
By default, this is disabled .  |
| Ignore Vertex Colors | | If enabled, ignores the vertex color data in the child object. By default, this is disabled .  |

## [Presets](#presets)[](#presets)

You can save presets of various import settings to quickly apply later within the [import preview](#import-preview-models)  or [import queue](#import-queue) .

By default, you can select between two presets:

-

Studio Default : The default import behavior.

-

Last Imported : Uses the settings applied to the most recent import.

You can use the ⋯  menu next to the Presets dropdown for additional options:

-

Reset all : Removes any changes to the current configuration, putting settings back in the default state for the current preset.

-

Save selection : Allows you to save any new changes to the importer settings into the currently selected preset.

-

Save as new : Sets the current settings as a new preset. A dialogue box displays allowing you to set a name.

-

Set as default : Sets the current preset as the default for all imports moving forward.

-

Rename : Renames the current preset.

-

Delete : Deletes the current preset. Resets to Studio Default  preset.

## [Warnings and errors](#warnings-and-errors)[](#warnings-and-errors)

If Studio detects any issues with your model, a small indicator displays in the hierarchy panel or the settings panel.

If you see a warning icon in the hierarchy, expand the hierarchy until you reach the specific child object to see more information about the issue. Warning and error messages display in the settings panel or as a tooltip.

![A warning message in orange stating an error about cages mismatching.](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Warning-Settings-Panel.png) Warning and error messages display in the appropriate section in the inspector panel.

![An error message in red with a pop-up message about missing textures.](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Warning-Mouse-Over.png) Some errors display a tooltip when hovering over the error icon.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
