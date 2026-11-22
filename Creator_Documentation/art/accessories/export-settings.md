<!-- Source: https://create.roblox.com/docs/en-us/art/accessories/export-settings.md -->

---
title: "Rigid accessory export settings"
url: /docs/en-us/art/accessories/export-settings
last_updated: 2026-06-16T15:58:00Z
description: "Use the appropriate export settings in Maya and Blender to generate Studio-ready .fbx files."
---

# Rigid accessory export settings

Export your rigid accessory model as a `.fbx` or `.gltf` file to take advantage of all of Studio's 3D import features. These file types contain mesh and texture data you need to later [import](/docs/en-us/studio/importer.md) into Studio.

> **Warning:** **If creating other types of 3D models:**- For generic meshes, see [general mesh specifications](/docs/en-us/art/modeling/specifications.md) and [general export settings](/docs/en-us/art/modeling/export-requirements.md). - For layered accessories, see [layered accessory specifications](/docs/en-us/art/accessories/clothing-specifications.md) and [layered export settings](/docs/en-us/art/accessories/clothing-export-settings.md). - For avatar characters, see [avatar specifications](/docs/en-us/art/characters/specifications.md) and [avatar export settings](/docs/en-us/art/characters/export-settings.md).
> **Warning:** If you have any modifiers to your mesh or project objects, make sure to apply or delete them before export.
## Blender

Blender allows you to export in `.fbx` or `.gltf` as well as other formats. If you are using `.fbx` export, familiarize yourself with [Blender's FBX scaling](/docs/en-us/art/blender.md#adjust-scale-fbx) to ensure that you successfully import the model into Studio at the correct scale.

### Export settings

To export the `.fbx` file in Blender:

1. In the topbar, click **File**. A pop-up menu displays.
2. Select **Export**, then **FBX (.fbx)**. The **Blender File View** window displays.
3. On the right-hand side, change the **Path Mode** property to **Copy**, then toggle the **Embed Textures** button.
4. Set **Transform** > **Apply Scalings** to **Unit Scale**. For more information, see [scaling and scene units](/docs/en-us/art/blender.md#adjust-scale-fbx).
5. Click the **Export FBX** button.
6. After exporting, use Studio's [Importer](/docs/en-us/studio/importer.md) to import your model and the [Accessory Fitting Tool](/docs/en-us/art/accessories/accessory-fitting-tool.md) to convert the model into an accessory.

## Maya export settings

To export a mesh in Maya as a `.fbx` file:

1. In the topbar, click **File**. A pop-up menu displays.
2. Select **Export All**. The **Export All** window displays.
3. Near the bottom of the window, click the **Files of type** dropdown, then select **FBX export**.
4. On the right-hand side of the window, navigate to the **Options...** section.
5. In the **Geometry** section, enable **Smooth Mesh** and **Referenced Asset Content**.
6. In the **Animation** section, disable **Animation**.
7. If you need to import textures as a `.png`, in the **Embed Media** section, enable **Embed Media**.
8. In the **Advanced Options** section,
  - Navigate to **Units**, then enable **Automatic**.
  - Navigate to **Axis Conversion**, then set the **Up Axis** property to **Y**.
9. Click the **Export All** button.
10. After exporting, use Studio's [Importer](/docs/en-us/studio/importer.md) to import your model and the [Accessory Fitting Tool](/docs/en-us/art/accessories/accessory-fitting-tool.md) to convert the model into an accessory.