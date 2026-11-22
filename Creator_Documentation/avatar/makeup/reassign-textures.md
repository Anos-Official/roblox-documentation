<!-- Source: https://create.roblox.com/docs/en-us/avatar/makeup/reassign-textures -->

Reassign textures | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar/makeup/reassign-textures.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. Makeup

# Reassign textures

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar/makeup/reassign-textures.md)

To import custom makeup textures, use Blender or Maya to reassign the existing textures on the reference template head to your custom texture images. After replacing the textures, export the entire head model, then [import](/docs/en-us/avatar/makeup/import)  it into Studio.

The following information is specific  to applying makeup textures to Roblox's [template heads](/docs/en-us/avatar/makeup#template-heads)  that already have PBR texture nodes assigned. For information on assigning textures from scratch, see [Assign textures in Blender and Maya](/docs/en-us/art/modeling/assign-textures) .

## [Blender](#blender)[](#blender)

The video presenter opts to clear all existing image links by navigating to File  > External Data  > Unpack Resources  and selecting Remove Pack . This is a method to unassign all images instead of individually unassigning textures like step #5 in the following instructions.

To reassign textures in Blender:

1.

Unzip and open the [Blender reference head file](/docs/en-us/avatar/makeup#template-heads) .

2.

Switch to the Shading  tab.

3.

In the Outliner, expand the Makeup collection and select the face region you intend to replace textures for.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Blender-Select-Region.png)

4.

In the node graph, select the texture image you intend to update, such as Neutral_FaceDecal_ALB.png

5.

Click the X  to remove the existing image assignment.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Blender-Unlink-Image.png)

6.

Click the folder icon to browse for a new image.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Blender-Assign-New.png)

7.

Repeat for all PBR textures that you intend to replace.

8.

Delete any texture nodes you are not using.

9.

Verify your final node graph looks similar to the original reference with nothing unintentionally missing.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Blender-Expected-Nodes.png)

After replacing your PBR textures, export the entire template file as a .fbx  or .gltf . All 3D modeling [export requirements](/docs/en-us/art/modeling/export-requirements)  apply, but there are a few makeup-specific settings you must configure:

1.

In the export file browser window, navigate to the Include  section, then enable the Custom Properties  toggle for makeup UV data transfer data purposes.

2.

In the Armature  section, enable Only Deform Bones  to ensure your export file includes skinning data for eyebrows and eyelashes.

![](https://prod.docsiteassets.roblox.com/assets/makeup/Blender-MakeupExport.png) All necessary Blender export settings for makeup

## [Maya](#maya)[](#maya)

To reassign textures in Blender:

1.

Unzip and open the Maya [reference head file](/docs/en-us/avatar/makeup#template-heads) .

2.

In the Status Line near the top of the default layout, click on the Hypershade icon.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Maya-Select-Hypershade.png)

3.

Move your mouse over the material's texture you intend to replace.

4.

Click and hold right mouse-click and drag the selector to Graph Network .

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Maya-Select-Graph-Network.png)

5.

In the newly displayed node graph, click on the Texture Node you intend to replace, such as Neutral_Eyes_ALB.png .

6.

In the right Property Editor, navigate to Image Name and click the folder icon. A file browser displays.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Maya-Replace-Texture.png)

1.

Select the texture image file you want to use as a replacement.

2.

Repeat for all PBR textures that you intend to replace.

3.

Delete any texture nodes you are not using.

4.

Verify your final node graph looks similar to the original reference with nothing unintentionally missing.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Maya-Expected-Nodes.png)

After replacing your PBR textures, export the entire template file as a .fbx  or .gltf . All 3D modeling [export requirements](/docs/en-us/art/modeling/export-requirements)  apply, but there are a few makeup-specific settings you must configure:

1.

In the export file browser window, navigate to the Deformed Models  section.

2.

Enable the Skins  toggle to ensure your export file includes skinning data for eyebrows and eyelashes.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/Maya-MakeupExport.png)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
