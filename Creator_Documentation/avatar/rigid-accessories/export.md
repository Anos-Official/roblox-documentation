<!-- Source: https://create.roblox.com/docs/en-us/avatar/rigid-accessories/export -->

Export rigid accessories | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar/rigid-accessories/export.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. Accessories and clothing
6. /
7. Rigid accessories

# Export rigid accessories

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar/rigid-accessories/export.md)

When you are ready to export a rigid accessory model that meets Roblox's [rigid accessory specifications](/docs/en-us/avatar/rigid-accessories/specifications) , it's important to review the following prerequisite information and step-by-step instructions for the .fbx  or .gltf  export files so that your creation takes advantage of all of Studio's [Importer](/docs/en-us/studio/importer)  features.

This is particularly important for rigid accessory models because they contain all the mesh, texture, and attachment data that's essential for rigid accessories to attach to character bodies correctly.

If you have any modifiers to your mesh or project objects, make sure to apply or delete them before export.

For other types of 3D models:

-

[General mesh](/docs/en-us/art/modeling/export-requirements)  export settings.

-

[Layered accessory](/docs/en-us/avatar/layered-accessories/export)  export settings.

## [Blender export settings](#blender-export-settings)[](#blender-export-settings)

Blender allows you to export your rigid accessory as either a .fbx  or .gltf  file. If you are exporting it as a .fbx  file, familiarize yourself with [Blender's FBX scaling](/docs/en-us/art/blender#adjust-scale-fbx)  to ensure that you successfully import the model into Studio at the correct scale.

To export your rigid accessory in Blender as a .fbx  file:

1.

In the topbar, click File  > Export  > FBX (.fbx) . The Blender File View  window displays.

2.

On the right-hand side, set Path Mode  to Copy , then toggle the Embed Textures  button.

3.

In the Transform  section, set Apply Scalings  to FBX Unit Scale . If you run into scaling issues on import, see [Blender FBX scaling](/docs/en-us/art/blender#adjust-scale-fbx)  for alternative approaches.

4.

Click the Export FBX  button and save the .fbx  to the directory of your choice.

 ![Screenshot of Blender export settings](https://prod.docsiteassets.roblox.com/assets/accessories/rigid-accessory-blender.png)

You now have a .fbx  file that you can [import into Studio](/docs/en-us/avatar/rigid-accessories/import)  as a [Model](/docs/en-us/reference/engine/classes/Model)  rigid accessory. Once the rigid accessory is in Studio, you can use the [Accessory Fitting Tool](/docs/en-us/avatar/accessory-fitting-tool)  to convert the model into an accessory.

## [Maya export settings](#maya-export-settings)[](#maya-export-settings)

To export your rigid accessory in Maya as a .fbx  file:

1.

In the topbar, click File  > Export All . The Export All  window displays.

2.

Near the bottom of the window, click the Files of type  dropdown, then select FBX export .

3.

On the right-hand side of the window, navigate to the Options...  section.

4.

In the Geometry  section, enable Smooth Mesh  and Referenced Asset Content .

5.

In the Animation  section, disable Animation .

6.

If you need to import textures as a .png , in the Embed Media  section, enable Embed Media .

7.

In the Advanced Options  section,

-

Navigate to Units , then enable Automatic .

-

Navigate to Axis Conversion , then set the Up Axis  property to Y .

8.

Click the Export All  button and save the .fbx  to the directory of your choice.

 ![Screenshot of Maya export settings](https://prod.docsiteassets.roblox.com/assets/accessories/lc-requirements-maya-settings.png)

You now have a .fbx  file that you can [import into Studio](/docs/en-us/avatar/rigid-accessories/import)  as a [Model](/docs/en-us/reference/engine/classes/Model)  rigid accessory. Once the rigid accessory is in Studio, you can use the [Accessory Fitting Tool](/docs/en-us/avatar/accessory-fitting-tool)  to convert the model into an accessory.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
