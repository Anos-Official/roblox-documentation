<!-- Source: https://create.roblox.com/docs/art/modeling/assign-textures -->

Blender and Maya texture settings | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/art/modeling/assign-textures.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Assets](/docs/en-us/assets)
4. /
5. Texturing

# Blender and Maya texture settings

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/art/modeling/assign-textures.md)

This guide covers the process to assign texture images in Blender or Maya to your 3D model so that they import seamlessly into Studio. The import process supports both basic textures and realistic PBR textures, as long as they meet Roblox's [texture specifications](/docs/art/modeling/texture-specifications) .

The following information is specific for applying makeup textures generic meshes . For more information on reassigning textures for makeup assets, see [Reassign textures in Blender and Maya](/docs/avatar/makeup/reassign-textures) .

## [Blender](#blender)[](#blender)

To assign Roblox-supported textures to your 3D model in Blender:

1.

In the Outliner, select your mesh object.

2.

In the Properties panel, navigate to the Materials tab .

3.

Verify that your object has a Material assigned with the Surface set to Principled BSDF .

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Blender-Material-Check.png)

4.

If no material is assigned, click the + symbol to add a material.

1.

Click the New button. A new Principled BSDF  material populates.

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Blender-Create-New-Material.png)

5.

Navigate to the Shading tab .

6.

With your mesh object selected, check the node graph. There may already be texture image nodes connected to the Principled BSDF  node.

7.

In the node graph area, add a texture image node with right-click ⟩ Add  ⟩ Texture  ⟩ Image Texture .

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Blender-Add-Image-Texture.png)

8.

In the new Image Texture node, click Open to open a file browser and insert your custom texture.

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Blender-Image-Texture-No-Assignment.png)

Alternatively to steps 7-8, you can drag and drop  texture file from another window into the graph editor space.

9.

After adding image texture nodes and assigning the appropriate files, drag the Image Texture  sockets to the appropriate sockets in the Principled BSDF  node:

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Blender-Expected-Nodes.png)

-

Basic texture  or PBR color/albedo : connect Color  to Base Color .

-

Metallic texture : connect Color  to Metallic .

-

Roughness texture : connect Color  to Roughness .

-

Normal texture  images need to be added to a NormalMap node:

1.

Right-click in the graph-editor area and select Add  ⟩ Vector  ⟩ Normal Map .

2.

Connect Image Texture Color  to NormalMap's Color .

3.

Connect NormalMap's Normal  to PrincipledBSDF's Normal  socket.

After replacing your PBR textures, [export the entire model](/docs/art/modeling/export-requirements#blender)  and follow instructions to [import into Studio](/docs/studio/importer)

## [Maya](#maya)[](#maya)

To assign Roblox-supported textures to your 3D model in Maya:

1.

In the Status Line near the top of the default layout, click on the Hypershade icon.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Maya-Select-Hypershade.png)

2.

In the Create Window panel on the Hypershade popup, navigate to Maya  ⟩ Surface  and click Standard Surface . A surface node appears in the node editor.

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Maya-Create-Surface.png)

1.

If adding a normal map, navigate to Maya  ⟩ Utilities  and click Bump 2d . A node required for normal maps appears in the node editor.

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Maya-Bump-2D.png)

3.

Drag and drop your PBR textures to the graph network.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Maya-Select-Graph-Network.png)

1.

If adding a normal map, select the Bump 2d node, and change to Tangent Space Normals.

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Maya-Tangent-Space-Normals.png)

4.

Select your model and navigate to your material you intend to assign. Right-click and hold over the material and select Assign Material to Selection .

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Maya-Assign-Material.png)

After replacing your PBR textures, [export the model](/docs/art/modeling/export-requirements#maya)  and follow instructions to [import into Studio](/docs/studio/importer) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
