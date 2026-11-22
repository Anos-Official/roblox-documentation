<!-- Source: https://create.roblox.com/docs/en-us/art/characters/export-settings.md -->

---
title: "Character body export settings"
url: /docs/en-us/art/characters/export-settings
last_updated: 2026-06-16T15:58:01Z
description: "Use the appropriate export settings in Maya and Blender to generate Studio-ready .fbx files."
---

# Character body export settings

> **Warning:** It's important to test your assets multiple times at every point of the asset creation process, whether it is within your modeling application or after importing into Studio. See [Test characters](/docs/en-us/art/characters/testing.md) for more information.

Export your model as a `.fbx` or `.gltf` to take advantage of all of Studio's 3D import features. When rigging or skinning a layerable model, these file types contain all the mesh and texture data, including the rig and influence data, you need to later [import](/docs/en-us/studio/importer.md) into Studio.

Check that your model meets Roblox's [avatar character specifications](/docs/en-us/art/characters/specifications.md) before exporting to ensure Studio compatibility.

> **Warning:** **If creating other types of 3D models:**- For generic meshes, see [general mesh specifications](/docs/en-us/art/modeling/specifications.md) and [general export settings](/docs/en-us/art/modeling/export-requirements.md). - For rigid accessories, see [accessory specifications](/docs/en-us/art/accessories/specifications.md) and [accessory export settings](/docs/en-us/art/accessories/export-settings.md). - For layered accessories, see [layered accessory specifications](/docs/en-us/art/accessories/clothing-specifications.md) and [layered export settings](/docs/en-us/art/accessories/clothing-export-settings.md).
> **Error:** If you are using Roblox's avatar template files, you must perform the [cleanup steps](/docs/en-us/art/characters/creating/combine-head-geometry.md) in order for the assets to properly validate.
## Before exporting

Before exporting, ensure that you are only exporting the Roblox supported objects related to your model. If you have any modifiers to your mesh or project objects, make sure to apply or delete them before export.

Use the following guidance before exporting:

- While your mesh objects must be parented within an armature object, you can also parent your outer cage objects to a single empty object to simplify your workspace.![Screenshot of a Blender project Outliner with parent objects collapsed.](../../assets/art/avatar/Character-Data-Model-Collapsed.png)
- In the cage parent object, ensure you have an [outer cage](/docs/en-us/art/characters/specifications.md#outer-cages) for each of your 15 body parts with appropriate naming affix.![Screenshot of the 15 outer cage meshes that you must include with a character export.](../../assets/art/avatar/Character-Data-Model-Cages.png)
- In the armature object, ensure that you include the all [15 mesh objects](/docs/en-us/art/characters/specifications.md#body-parts) and [19 attachments](/docs/en-us/art/characters/specifications.md#attachments) with the appropriate naming affix.![Screenshot of 15 child objects parented within an Armature object.](../../assets/art/avatar/Character-Data-Model-Joints.png)

> **Info:** For more information on supported modeling objects and proper configuration, see [Character specifications](/docs/en-us/art/characters/specifications.md).

- When exporting characters with animation or FACS animation, ensure that your animation timeline **Start** and **End** include the entire range of your animations.

![Zoom-in of Blender animation track indicating a Start value of 0 and End value of 308.](../../assets/art/avatar/basic-creation/Blender-Animation-Start-End.png) ## Blender

Blender allows you to export in `.fbx` or `.gltf` as well as other formats. If you are using `.fbx` export, familiarize yourself with [Blender's FBX scaling](/docs/en-us/art/blender.md#adjust-scale-fbx) to ensure that you successfully import the model into Studio at the correct scale.

### Export settings

1. In the topbar, click **File** > **Export** > **FBX (.fbx)**. The Blender file browser window displays.
2. Set **Path Mode** to **Copy** and enable the **Embed Textures** icon.
3. In the Include section, enable **Custom Properties**.
4. If your project doesn't already have `.01` scene unit scaling, set the **Transform** > **Apply Scalings** to `FBX Unit Scale`. For more details, see [Blender FBX scaling](/docs/en-us/art/blender.md#adjust-scale-fbx).
5. Expand the Armature section and uncheck **Add Leaf Bones**.
6. Enable **Bake Animation**.
7. Expand Bake Animation and **uncheck NLA Strips**, **All Actions**, and **Force Start/End Keyframes**.
  1. Ensure your project animation timeline has the correct **Start** and **End** range of all your keyframes.
8. In Bake Animation, set **Simplify** to **0.0**.
9. Click the **Export FBX** button. Save the `.fbx` to the directory of your choice.

![Screenshot of Blender export settings](../../assets/art/avatar/basic-creation/Export-Settings.png) ## Maya export settings

To export a mesh in Maya as a `.fbx` file:

1. In the topbar, click **File**. A pop-up menu displays.
2. Select **Export All**. The **Export All** window displays.
3. Near the bottom of the window, click the **Files of type** dropdown, then select **FBX export**.
4. On the right-hand side of the window, navigate to the **Options...** section.
5. In the **Geometry** section, enable **Smooth Mesh** and **Referenced Asset Content**.
6. In the **Animation** section, enable **Animation**. Avatar characters with [facial animation data](/docs/en-us/art/characters/facial-animation.md) require animation data.
7. Enable **Bake Animation**.
8. If you need to import textures as a `.png`, in the **Embed Media** section, enable **Embed Media**.
9. In the **Advanced Options** section,
  - Navigate to **Units**, then enable **Automatic**.
  - Navigate to **Axis Conversion**, then set the **Up Axis** property to **Y**.
10. Click the **Export All** button.![Screenshot of Maya export settings for exports with animation.](../../assets/accessories/lc-requirements-maya-settings-with-animation.png)
11. After exporting, use Studio's [Importer](/docs/en-us/studio/importer.md) to import your model. See [Test characters in Studio](/docs/en-us/art/characters/testing/studio.md) for additional importing and testing information.

> **Success:** After importing the `Class.Model` character to Studio, you can now perform the following with this asset: - [Test your character model](/docs/en-us/art/characters/testing.md) in Studio using various tools and workflows. - [Upload the character](/docs/en-us/art/accessories/creating-rigid/publishing.md) to the Marketplace. - Use the humanoid character on an existing experience by applying a [HumanoidDescription](/docs/en-us/characters/appearance.md#manually-modify-appearance)to the `Class.Model` object. - Save the asset to your [Toolbox](/docs/en-us/projects/assets/toolbox.md) to share or use within any of your experiences.