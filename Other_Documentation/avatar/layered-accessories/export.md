<!-- Source: https://create.roblox.com/docs/avatar/layered-accessories/export -->

Export layered accessories | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar/layered-accessories/export.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. Accessories and clothing
6. /
7. Layered accessories

# Export layered accessories

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar/layered-accessories/export.md)

When you are ready to export a layered accessory model that meets Roblox's [layered accessory specifications](/docs/avatar/layered-accessories/specifications) , it's important to review the following prerequisite information and step-by-step instructions for the .fbx  or .gltf  export files so that your creation takes advantage of all of Studio's [Importer](/docs/studio/importer)  features.

This is particularly important for layered accessory models because they contain all the mesh and texture data, including the rig and influence data that's essential for accessories to move and animate properly with character bodies across the platform.

For other types of 3D models:

-

[General mesh](/docs/art/modeling/export-requirements)  export settings.

-

[Rigid accessory](/docs/avatar/rigid-accessories/export)  export settings.

## [Prerequisites](#prerequisites)[](#prerequisites)

Before you export your custom layered accessory, ensure that you are only exporting the Roblox supported objects related to your model. If you have any modifiers to your mesh or project objects, make sure to apply or delete them before export.

You can export layered accessory models with the following object structure:

|
-

Armature parent
-

Bones / joints

-

Primary mesh object

-

Cage parent object
-

Inner cage mesh object

-

Outer cage mesh object

 | | ![Blender layered accessory data model example](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Clothing-Data-Model.png) |
| --- | --- |

You can also export shoes together. Even though left and right shoes are separate layered accessories, you can either export the left and right shoe individually, or export both shoes at the same time using the following structure:

|
-

Armature parent
-

Bones / joints

-

Left shoe mesh object

-

Right shoe mesh object

-

Cage parent object
-

Left shoe inner cage

-

Left shoe outer cage

-

Right shoe inner cage

-

Right shoe outer cage

 | | ![Shoe layered accessory data model example](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Shoe-Data-Model.png) |

Each shoe must include their own inner and outer cage.

## [Blender export settings](#blender-export-settings)[](#blender-export-settings)

Blender allows you to export your layered accessory as either a .fbx  or .gltf  file. If you are exporting it as a .fbx  file, familiarize yourself with [Blender's FBX scaling](/docs/art/blender#adjust-scale-fbx)  to ensure that you successfully import the model into Studio at the correct scale.

To export your layered accessory in Blender as a .fbx  file:

1.

In the topbar, click File  > Export  > FBX (.fbx) . The Blender File View  window displays.

2.

On the right-hand side, set Path Mode  to Copy , then toggle the Embed Textures  button.

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Blender-Export-Settings-1.png)

3.

In the Transform  section, set Apply Scalings  to FBX Unit Scale . If you run into scaling issues on import, see [Blender FBX scaling](/docs/art/blender#adjust-scale-fbx)  for alternative approaches.

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Blender-Export-Settings-5.png)

4.

In the Armature  section, uncheck Add Leaf Bones .

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Blender-Export-Settings-3.png)

5.

Click the Export FBX  button and save the .fbx  to the directory of your choice.

You now have a .fbx  file that you can [import into Studio](/docs/avatar/layered-accessories/import)  as a [Model](/docs/reference/engine/classes/Model)  layered accessory. Once the layered accessory is in Studio, you can use the [Accessory Fitting Tool](/docs/avatar/accessory-fitting-tool)  to convert the model into an accessory.

## [Maya export settings](#maya-export-settings)[](#maya-export-settings)

To export your layered accessory in Maya as a .fbx  file:

1.

In the topbar, click File  > Export All . The Export All  window displays.

2.

Near the bottom of the window, click the Files of type  dropdown, then select FBX export .

3.

On the right-hand side of the window, navigate to the Options...  section.

4.

In the Geometry  section, enable Smooth Mesh  and Referenced Asset Content .

5.

If you need to import textures as a .png , in the Embed Media  section, enable Embed Media .

6.

In the Advanced Options  section,

-

Navigate to Units , then enable Automatic .

-

Navigate to Axis Conversion , then set the Up Axis  property to Y .

7.

Click the Export All  button and save the .fbx  to the directory of your choice.

 ![Screenshot of Maya export settings for exports with animation.](https://prod.docsiteassets.roblox.com/assets/accessories/lc-requirements-maya-settings-with-animation-layeredaccessories.png)

You now have a .fbx  file that you can [import into Studio](/docs/avatar/layered-accessories/import)  as a [Model](/docs/reference/engine/classes/Model)  layered accessory. Once the layered accessory is in Studio, you can use the [Accessory Fitting Tool](/docs/avatar/accessory-fitting-tool)  to convert the model into an accessory.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
