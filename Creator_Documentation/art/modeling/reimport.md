<!-- Source: https://create.roblox.com/docs/en-us/art/modeling/reimport -->

Reimport | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/art/modeling/reimport.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Assets](/docs/en-us/assets)

# Reimport

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/art/modeling/reimport.md)

Reimport  allows you to update existing custom models and their textures from an external 3D file. Unlike regular [import](/docs/en-us/studio/importer#import-files) , which creates brand new instances, the reimport function updates existing objects non-destructively to help support the iterative nature of 3D development.

Along with asset updates, reimport remembers the file and settings used to import the original asset. This means you can easily update an imported asset with a single click or hotkey without going through all the initial import settings. This memory persists across Studio sessions.

## [Supported instances](#supported-instances)[](#supported-instances)

Reimport supports the following entry points in the Explorer. Reimport also supports [packages](/docs/en-us/projects/assets/packages) , allowing you to reimport batches of asset instances at once.

-

[Model](/docs/en-us/reference/engine/classes/Model)  - The reimport feature scans the container, updating any changed [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  and [SurfaceAppearance](/docs/en-us/reference/engine/classes/SurfaceAppearance)  instances and adding newly created ones, while leaving your existing properties unchanged. Reimport replaces meshes based off of mesh names saved in Studio and the external 3D file (see [MeshPart detection](#meshpart-detection) ). It replaces images for PBR textures based off of filenames (see [SurfaceAppearance detection](#surfaceappearance-detection) ).

-

[SurfaceAppearance](/docs/en-us/reference/engine/classes/SurfaceAppearance)  or [Decal](/docs/en-us/reference/engine/classes/Decal)  (selected directly) - Reimport uploads all texture maps found in the same folder as the selected file in one operation.

Reimport memory is local to your device. A Reimport ID is stored on the [Model](/docs/en-us/reference/engine/classes/Model)  instance and referenced locally. Keep in mind the following:

-

Filepaths are never saved in the place file.

-

Reimport supports different reimport paths on different devices for the same instance.

-

Reimport supports copy-pasting, saving and loading from .rbxm / .rbxl , and [Asset Manager](/docs/en-us/projects/assets/manager)  workflows.

### [MeshPart detection](#meshpart-detection)[](#meshpart-detection)

Reimport updates meshes based off of the path and name of the 3D source file, and the path and name of the mesh object in Studio. Reimport only updates the mesh content and transform properties and preserves other Roblox-specific properties, including [CollisionFidelity](/docs/en-us/reference/engine/classes/MeshPart#CollisionFidelity)  and [RenderFidelity](/docs/en-us/reference/engine/classes/MeshPart#RenderFidelity) . If the incoming mesh has no texture assigned, reimport keeps the existing [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  texture rather than clearing it.

Reimport relies on matching mesh names between the Studio and the 3D source file:

-

If a mesh's path/name  in the 3D source file matches  a [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  path/name  in Studio, reimport updates the matching [MeshPart](/docs/en-us/reference/engine/classes/MeshPart) .

-

If a mesh's path/name  in the 3D source file doesn't exist  as [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  path/name  in Studio, reimport creates a new [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  within the [Model](/docs/en-us/reference/engine/classes/Model) .

-

If a [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  path/name  in Studio doesn't exist  in the 3D source file, reimport does not modify the [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  in Studio.

#### [Known asset cache](#known-asset-cache)[](#known-asset-cache)

Studio uses a known asset cache  which helps detect duplicate imports in the same Studio session. If an imported or reimported asset is detected, Roblox reuses the existing asset ID instead of creating and uploading a new asset.

If you attempt to reimport a single mesh object, but the 3D file contains a larger number of meshes or textures, Roblox only applies a single asset upload for that object.

#### [Duplicates](#duplicates)[](#duplicates)

Reimport detects duplicate meshes, and doesn't reupload matching meshes that are the same in both Studio and the 3D source file. In the scenario where a mesh in Blender is renamed from Mesh1  to Mesh2 , reimport creates a new [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  named Mesh2  and doesn't apply changes to the original Mesh1 .

#### [Pivot points](#pivot-points)[](#pivot-points)

In cases where you may want to use the pivot point of the [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  and not the [Model](/docs/en-us/reference/engine/classes/Model) , right-click any [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  with reimport information and select Reimport  ⟩ Reimport relative to this . Doing so triggers a reimport for the entire model using the pivot point of right-clicked [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  as an anchor instead of the [Model](/docs/en-us/reference/engine/classes/Model)  pivot point. You can use this for models that have custom pivots by reimporting relative to a mesh that has not changed position in the 3D file.

### [SurfaceAppearance detection](#surfaceappearance-detection)[](#surfaceappearance-detection)

Reimport can quickly batch update the textures of a model with [PBR textures](/docs/en-us/art/modeling/surface-appearance)  based off of the naming convention of the image files.

Reimport detects a set of known suffixes for color, metalness, normal, roughness, and emissive maps. You can find the full list of supported suffixes in the following table:

| Map Type | | Suffixes | | Example |
| --- | --- |
| [Color](/docs/en-us/art/modeling/surface-appearance#color-albedo) | | color , col , diffuse , diff , albedo , alb , base | | Tree_Color.png |
| [Metalness](/docs/en-us/art/modeling/surface-appearance#metalness) | | metal , metallic , metalness , mtl , met | | Tree_Metal.png |
| [Roughness](/docs/en-us/art/modeling/surface-appearance#roughness) | | rough , roughness , rgh | | Tree_Rough.png |
| [Normal](/docs/en-us/art/modeling/surface-appearance#normal) | | normal , nor , nrm , nrml , norm | | Tree_Normal.png |
| [Emissive Mask](/docs/en-us/art/modeling/surface-appearance#emissive-mask) | | emissive , emission , emiss , emit , glow , illum , selfillum , light , luminance , emissivemask | | Tree_Emissive.png |

When reimporting an asset with a [SurfaceAppearance](/docs/en-us/reference/engine/classes/SurfaceAppearance)  selected, a file dialog displays allowing you to select a new image file to use as a PBR texture. Reimport automatically detects other PBR images in the directory based off of naming and maps them to the [SurfaceAppearance](/docs/en-us/reference/engine/classes/SurfaceAppearance)  object.

Texture files without a recognized material map suffix are accepted as the color map for [SurfaceAppearance](/docs/en-us/reference/engine/classes/SurfaceAppearance)  reimport.

## [Reimport models](#reimport-models)[](#reimport-models)

When you bring an asset into Studio through the [importer](/docs/en-us/studio/importer#import-files) , reimport automatically stores the filepath, import preset, and upload inventory, so subsequent reimports require no manual setup.

To reimport a configured [Model](/docs/en-us/reference/engine/classes/Model) :

1.

Right-click the [Model](/docs/en-us/reference/engine/classes/Model)  and select Reimport  ⟩ Reimport  from the context menu.

-

Alternatively, when selecting the object, use the reimport hotkey Alt Shift R .

-

A loading indicator appears after selecting reimport. If there are any issues, an error dialog displays with a Configure Reimport Settings  button that opens the Configure  dialog.

If a [Model](/docs/en-us/reference/engine/classes/Model)  has no saved reimport configuration (for example, a model imported on a different device or before reimport was available), triggering Reimport  opens the Configure  dialog instead of starting the reimport. You can also open it directly at any time through Reimport  ⟩ Configure . In this dialog, you can set the file path, upload target, and import presets.

Since reimport relies on matching mesh paths/names to update a [Model](/docs/en-us/reference/engine/classes/Model)  from a 3D file, it’s important to maintain unique naming of meshes and their paths in your external 3D tools. In Studio, you should also maintain the naming/tree structure of the [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  objects within your model in order for reimport to update correctly.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
