<!-- Source: https://create.roblox.com/docs/en-us/art/accessories/clothing-export-settings.md -->

---
title: "Layered clothing export settings"
url: /docs/en-us/art/accessories/clothing-export-settings
last_updated: 2026-06-16T15:58:00Z
description: "Use the appropriate export settings in Maya and Blender to generate Studio-ready .fbx files."
---

# Layered clothing export settings

Export your mesh or model as a `.fbx` or `.gltf` to take advantage of all of Studio's 3D import features. When rigging or skinning a layerable model, these file types contain all the mesh and texture data, including the rig and influence data, you need to later [import](/docs/en-us/studio/importer.md) into Studio.

> **Warning:** **If creating other types of 3D models:**- For generic meshes, see [general mesh specifications](/docs/en-us/art/modeling/specifications.md) and [general export settings](/docs/en-us/art/modeling/export-requirements.md). - For rigid accessories, see [accessory specifications](/docs/en-us/art/accessories/specifications.md) and [accessory export settings](/docs/en-us/art/accessories/export-settings.md). - For avatar characters, see [avatar specifications](/docs/en-us/art/characters/specifications.md) and [avatar export settings](/docs/en-us/art/characters/export-settings.md).
## Before exporting

Before exporting, ensure that you are only exporting the Roblox supported objects related to your model. If you have any modifiers to your mesh or project objects, make sure to apply or delete them before export.

You can export layered clothing models with the following object structure:

![Blender clothing data model example](../../assets/modeling/skinned-meshes/Clothing-Data-Model.png)

- Armature parent
  - Bones / joints
  - Primary mesh object
- Cage parent object
  - Inner cage mesh object
  - Outer cage mesh object

You can also export shoes together. Even though left and right shoes are separate accessories, you can either export the left and right shoe individually, or export both shoes at the same time using the following structure:

![Shoe clothing data model example](../../assets/modeling/skinned-meshes/Shoe-Data-Model.png)

- Armature parent
  - Bones / joints
  - Left shoe mesh object
  - Right shoe mesh object
- Cage parent object
  - Left shoe inner cage
  - Left shoe outer cage
  - Right shoe inner cage
  - Right shoe outer cage

> **Warning:** Each shoe must include their own inner and outer cage.
## Blender

Blender allows you to export in `.fbx` or `.gltf` as well as other formats. If you are using `.fbx` export, familiarize yourself with [Blender's FBX scaling](/docs/en-us/art/blender.md#adjust-scale-fbx) to ensure that you successfully import the model into Studio at the correct scale.

### Export settings

To export the `.fbx` file in Blender:

1. In the topbar, click **File**. A pop-up menu displays.
2. Select **Export**, then **FBX (.fbx)**. The **Blender File View** window displays.
3. On the right-hand side, change the **Path Mode** property to **Copy**, then toggle the **Embed Textures** button.
4. If your project doesn't already have `.01` scene unit scaling, set the **Transform** > **Apply Scalings** to `FBX Unit Scale`. For more details, see [Blender FBX scaling](/docs/en-us/art/blender.md#adjust-scale-fbx).
5. Under the **Armature** section, disable **Add Leaf Bones**.
6. Click the **Export FBX** button.
7. After exporting, use Studio's [Importer](/docs/en-us/studio/importer.md) to import your model and the [Accessory Fitting Tool](/docs/en-us/art/accessories/accessory-fitting-tool.md) to convert the model into an accessory.

## Maya export settings

To export a mesh in Maya as a `.fbx` file:

1. In the topbar, click **File**. A pop-up menu displays.
2. Select **Export All**. The **Export All** window displays.
3. Near the bottom of the window, click the **Files of type** dropdown, then select **FBX export**.
4. On the right-hand side of the window, navigate to the **Options...** section.
5. In the **Geometry** section, enable **Smooth Mesh** and **Referenced Asset Content**.
6. If you need to import textures as a `.png`, in the **Embed Media** section, enable **Embed Media**.
7. In the **Advanced Options** section,
  - Navigate to **Units**, then enable **Automatic**.
  - Navigate to **Axis Conversion**, then set the **Up Axis** property to **Y**.
8. Click the **Export All** button.
9. After exporting, use Studio's [Importer](/docs/en-us/studio/importer.md) to import your model and the [Accessory Fitting Tool](/docs/en-us/art/accessories/accessory-fitting-tool.md) to convert the model into an accessory.