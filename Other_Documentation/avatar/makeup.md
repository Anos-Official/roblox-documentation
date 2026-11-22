<!-- Source: https://create.roblox.com/docs/avatar/makeup -->

Makeup | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar/makeup.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. Makeup

# Makeup

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar/makeup/index.md)

Makeup  is a cosmetic item that you can apply to a face of an avatar or non-playable character for additional creative expression, such as traditional makeup art (e.g., eyeshadow, lipstick, and blush), face paint, battle markings, and camouflage.

Makeup is made up of multiple specialized texture layers baked into a [Decal](/docs/reference/engine/classes/Decal)  object, and each texture layer contains a unique makeup component like the lips or eyes region. Players can purchase makeup as a set on the [Marketplace](https://www.roblox.com/catalog)  and apply it as a complete cohesive look, or swap out individual makeup components for others that match their own avatar's style.

This guide covers authoring makeup assets in Studio. To let players create and purchase makeup directly within your experience at runtime, see [In-experience creation for makeup](/docs/avatar/in-experience-creation-makeup) .

![](https://prod.docsiteassets.roblox.com/assets/makeup/MakeupIntro-FullFace.png) Complete look

![](https://prod.docsiteassets.roblox.com/assets/makeup/MakeupIntro-Eyes.png) Eyes texture layer

![](https://prod.docsiteassets.roblox.com/assets/makeup/MakeupIntro-Lips.png) Lip texture layer

![](https://prod.docsiteassets.roblox.com/assets/makeup/MakeupIntro-Face.png) Face texture layer

This guide provides several [makeup templates](#resources)  that you can use within your creation process, such as:

-

Template textures that you can use in 2D editing software to author makeup.

-

Template heads that you can use to view and test your makeup before export.

-

Reference game you can use to import and test your makeup assets on characters with different skin tones and body types.

You can either use these templates as a pure reference to see how everything works, or you can use all of them at each step of the suggested creation process.

![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Full-Render.png) Reference template render

![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Blender-Datamodel.png) Reference template data model

## [Makeup components](#makeup-components)[](#makeup-components)

You can apply textures to three primary regions of the face: the eyes region, lips region, and face region. Each region has overlapping surfaces with other regions to allow for seamless, continuous looks between makeup components.

![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Eyes-Region.png) Eyes region

![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Lips-Region.png) Lips region

![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Face-Region.png) Face region

In addition, you can include eyebrows and eyelashes with your makeup creations. Eyebrows and eyelashes are [Model](/docs/reference/engine/classes/Model)  objects that contain [MeshPart](/docs/reference/engine/classes/MeshPart)  objects with skinning and caging data. This allows them to animate properly as the character's face changes expressions.

![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Eye-Acc.png) Eyebrow and eyelash mesh objects

![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Eye-Accessory-Datamodel.png) Eyebrow and eyelash data model

When you import your makeup creation from your favorite third-party modeling software into the [reference game](#reference-game) , Studio automatically detects mesh names, then generates the necessary [Decal](/docs/reference/engine/classes/Decal)  objects under the imported model. You can then quickly apply your makeup [Decal](/docs/reference/engine/classes/Decal)  objects and accessories by dragging them from the imported reference head into a character's Makeup  or Accessories  folder.

![](https://prod.docsiteassets.roblox.com/assets/makeup/Imported-DataModel.png) The imported model contains your makeup decals and face accessories

![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Character-Folders.png) Your makeup displays at runtime when you drag your makeup assets into the correct folders

Makeup assets that you create for the [Marketplace](https://www.roblox.com/catalog)  can include up to 6 total [Decal](/docs/reference/engine/classes/Decal)  objects, comprised of any combination of regions.

## [Resources](#resources)[](#resources)

The following are downloadable resources you can use within the creation process:

-

See [Template textures](#template-textures)  for image and project files you can use in 2D editing software like GIMP or Photoshop.

-

See [Template heads](#template-heads)  for required 3D models you can use to view and test your makeup assets.

-

See [Reference game](#reference-game)  to import and test your makeup assets into Studio

For resources that include two templates, in almost every case it's recommended to use the mesh template  to create makeup because:

-

It's easier and more intuitive to use because it mimics applying makeup in the real world.

-

It contains a higher-fidelity mesh and UVs with minimal distortion.

Some creators prefer using the cage template because there is only one transfer when projecting the texture, while there are two transfers before projecting the texture for the mesh template. This can result in makeup transferring more accurately with less artifacts.

Be sure to review your options before  starting to create makeup because you cannot start with one template, then transfer your makeup to the other.

### [Template textures](#template-textures)[](#template-textures)

When you are finished making changes to any of the following template texture images:

1.

Export your new textures.

Exporting from Photoshop

The video presenter uses File  > Export  > Layers to Files  to export each layer as its own .png  file.

Exporting from Substance Painter

Exporting from Procreate

To export textures from Procreate:

1.

Navigate to the Layers  pane, then hide everything but your first makeup component layer, such as your eyes, lips, or face layer.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/Procreate-ActiveLayer.jpg)

2.

With your makeup component layer active, navigate to the Actions  menu > Share  tab > Share Textures - PNG  to save all of your makeup component's textures to a location on your device.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/Procreate-ShareTextures.jpg)  ![](https://prod.docsiteassets.roblox.com/assets/makeup/Procreate-AllTextures.jpg)

3.

Delete all of the head, eyebrows, and eyelash textures.

1.

Open the location where you saved all of your makeup component's textures.

2.

Delete everything except for the following PBR textures:

-

TransferTarget_FullHead_Mat-Color

-

TransferTarget_FullHead_Mat-Metallic

-

TransferTarget_FullHead_Mat-Roughness

4.

Replace your makeup component's TransferTarget_FullHead_Mat-Color  layer with a version that will export transparency in the output texture.

1.

Copy your active makeup component layer.

2.

Navigate to the Gallery  > Plus  icon > Clipboard . A new Procreate file displays with your makeup component layer.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/Procreate-Clipboard.png)

3.

In the Layers  pane, disable the Background color  layer. Your makeup component displays without a background.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/Procreate-HideBackground.png)

4.

With your makeup component layer active, navigate to the Actions  menu > Share  tab > Share Image - PNG .

5.

In the file browser, navigate to the location on your device with all of your makeup component's textures, then save/override the TransferTarget_FullHead_Mat-Color  texture.

5.

Rename your makeup component's PBR textures appropriately so that you can easily reference each makeup component's PBR data when you reassign your textures in Blender or Maya. For example, if you are exporting texture maps for lips:

-

Lips-Color

-

Lips-Metallic

-

Lips-Roughness

6.

Repeat this process for every makeup component you want to import for your makeup look.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/Procreate-Final.png)

2.

[Reassign the preset textures](/docs/avatar/makeup/reassign-textures)  in a [template head](#template-heads)  with your new textures.

3.

[Import the reference head](/docs/avatar/makeup/import)  with your new textures into Studio.

Photoshop / GIMP texture images

![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Photoshop-Realistic-Mesh-Thumbnail.png)![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Photoshop-Realistic-Cage-Thumbnail.png)

A comprehensive .zip  folder with realistic texture images for use in Photoshop or your preferred image editor.

[Mesh Template](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Photoshop-Gimp-Realistic-Mesh.zip)

[Cage Template](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Photoshop-Gimp-Realistic-Cage.zip)

Substance Painter files

![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Substance-Realistic-Mesh-Thumbnail.png)![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Substance-Realistic-Cage-Thumbnail.png)

A comprehensive .zip  folder with realistic texture files for use in Substance Painter, an industry-standard PBR authoring software.

[Mesh Template](https://prod.docsiteassets.roblox.com/assets/makeup/resources/SubstancePainter-Realistic-Mesh.zip)

[Cage Template](https://prod.docsiteassets.roblox.com/assets/makeup/resources/SubstancePainter-Realistic-Cage.zip)

Procreate texture images

![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Procreate-Realistic-Mesh-Thumbnail.png)![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Procreate-Realistic-Cage-Thumbnail.png)

A comprehensive .zip  folder with realistic texture images for use in Procreate.

[Mesh Template](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Procreate-Realistic-Mesh.zip)

[Cage Template](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Procreate-Realistic-Cage.zip)

Photoshop / GIMP texture images

![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Photoshop-Blocky-Mesh-Thumbnail.png)

A comprehensive .zip  folder with blocky texture images for use in Photoshop or your preferred image editor.

[Mesh Template](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Photoshop-Gimp-Blocky-Mesh.zip)

Substance Painter files

![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Substance-Blocky-Mesh-Thumbnail.png)

A comprehensive .zip  folder with blocky texture files for use in Substance Painter, an industry-standard PBR authoring software.

[Mesh Template](https://prod.docsiteassets.roblox.com/assets/makeup/resources/SubstancePainter-Blocky-Mesh.zip)

Procreate texture images

![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Procreate-Blocky-Mesh-Thumbnail.png)

A comprehensive .zip  folder with blocky texture images for use in Procreate.

[Mesh Template](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Procreate-Blocky-Mesh.zip)

### [Template heads](#template-heads)[](#template-heads)

Each template head includes:

-

Target head mesh object or head cage mesh object

-

Eye, lip, and multiple face region mesh objects, fully linked to reference PBR textures

-

Eyebrows and eyelash mesh objects

The Blender and Maya templates also include a facial region reference .png  file that you can use to reference how your makeup assets fit into the eye, lips, and face/cheek regions.

Blender template reference files

![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Blender-Realistic-Mesh-Thumbnail.png)![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Blender-Realistic-Cage-Thumbnail.png)

A comprehensive .zip  folder of Blender assets, including multiple realistic reference heads pre-configured for testing in the Makeup test place or for authoring your own makeup.

[Mesh Template](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Blender-Realistic-Mesh.zip)

[Cage Template](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Blender-Realistic-Cage.zip)

Maya template reference files

![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Maya-Realistic-Mesh-Thumbnail.png)![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Maya-Realistic-Cage-Thumbnail.png)

A comprehensive .zip  folder of Maya assets, including multiple realistic reference heads pre-configured for testing in the Makeup test place or for authoring your own makeup.

[Mesh Template](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Maya-Realistic-Mesh.zip)

[Cage Template](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Maya-Realistic-Cage.zip)

FBX / GLTF template reference files

![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Fbx-Realistic-Mesh-Thumbnail.png)![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Fbx-Realistic-Cage-Thumbnail.png)

A comprehensive .zip  folder of .fbx  and .gltf  assets, including realistic heads with various example makeup looks that are ready to be implemented into Studio for testing purposes.

[Mesh Template](https://prod.docsiteassets.roblox.com/assets/makeup/resources/FBX-GLTF-Realistic-Mesh.zip)

[Cage Template](https://prod.docsiteassets.roblox.com/assets/makeup/resources/FBX-GLTF-Realistic-Cage.zip)

Blender template reference files

![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Blender-Blocky-Mesh-Thumbnail.png)

A comprehensive .zip  folder of Blender assets, including multiple blocky reference heads pre-configured for testing in the Makeup test place or for authoring your own makeup.

[Mesh Template](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Blender-Blocky-Mesh.zip)

Maya template reference files

![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Maya-Blocky-Mesh-Thumbnail.png)

A comprehensive .zip  folder of Maya assets, including multiple blocky reference heads pre-configured for testing in the Makeup test place or for authoring your own makeup.

[Mesh Template](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Maya-Blocky-Mesh.zip)

FBX / GLTF template reference files

![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Fbx-Blocky-Mesh-Thumbnail.png)

A comprehensive .zip  folder of .fbx  and .gltf  assets, including blocky heads with various example makeup looks that are ready to be implemented into Studio for testing purposes.

[Mesh Template](https://prod.docsiteassets.roblox.com/assets/makeup/resources/FBX-GLTF-Blocky-Mesh.zip)

### [Reference game](#reference-game)[](#reference-game)

Reference place file (download)

![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Experience-Thumbnail.png)

At this time, you can only test makeup on the downloadable placefile.

In Github, select the download icon on the right-side to download the MakeupBeta.zip  file.

[Github link](https://github.com/Roblox/avatar/blob/main/Makeup/MakeupBeta.zip)

## [Creation process](#creation-process)[](#creation-process)

This process assumes that you are proficient in 3D modeling software, such as Blender or Maya, and that you understand how to update, replace, export, save, and alter materials within your modeling tool and any additional texturing software or plugins.

![](https://prod.docsiteassets.roblox.com/assets/makeup/Creation-Steps-1.png) Download the 3D reference template head and texture templates applicable to your workflow.

![](https://prod.docsiteassets.roblox.com/assets/makeup/Creation-Steps-2.png) Modify the texture images in the tools of your choice.

![](https://prod.docsiteassets.roblox.com/assets/makeup/Creation-Steps-3.png) In Blender or Maya, replace the textures in the template with your new textures and export.

While you can easily swap [Decal](/docs/reference/engine/classes/Decal)  objects in Studio to make a quick change to a character's makeup, the following instruction is best practice for implementing PBR-based textures into Roblox makeup at scale. This process requires:

-

The [Makeup test place and template files](#resources)

-

A 3D modeling tool such as [Blender](https://www.blender.org)  or [Maya](https://www.autodesk.com/products/maya/overview)

-

Any PBR texturing software, such as [Substance Painter](https://www.adobe.com/products/substance3d/apps/painter.html) , [Materialize](http://boundingboxsoftware.com/materialize/index.php) , or plugins like [Ucupaint](https://extensions.blender.org/add-ons/ucupaint/)  (Blender).

As always with 3D art and creation workflows, there are many ways to achieve a specific goal, and the makeup and PBR publishing flow is no exception. It's recommended to try the workflow in this guide first, then adjust as necessary for your own creation requirements:

1.

Download a [reference template head](#resources)  and open it in the general modeling software of your choice.

2.

Using your texturing tools or image editing software, modify the texture images associated with the different regions: TransferTexture_Eyes , TransferTexture_Face , or TransferTexture_Lips .

3.

When you've created your new texture images, use Blender or Maya to reassign the existing file textures in the template. For more information, see [Reassign textures](/docs/avatar/makeup/reassign-textures) .

4.

Review [Face caging best practices](/docs/avatar/dynamic-heads/caging-best-practices)  for guidance on how to adjust face cages so that your makeup displays correctly for your use case.

5.

Export the entire template file as a .fbx  or .gltf . All 3D modeling [export requirements](/docs/art/modeling/export-requirements)  apply, but there are a few makeup-specific settings you must configure:

-

If you are using Blender,

1.

In the export file browser window, navigate to the Include  section, then enable the Custom Properties  toggle for makeup UV data transfer purposes.

2.

In the Armature  section, enable Only Deform Bones  to ensure your export file includes skinning data for eyebrows and eyelashes.

![](https://prod.docsiteassets.roblox.com/assets/makeup/Blender-MakeupExport.png) All necessary Blender export settings for makeup

-

If you are using Maya, in the export file browser window, navigate to the Deformed Models  section, then enable the Skins  toggle to ensure your export file includes skinning data for eyebrows and eyelashes.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/Maya-MakeupExport.png)

6.

[Import](/docs/avatar/makeup/import)  the template file into Studio. Studio automatically detects your mesh object names and associated textures, and generates Decal  objects.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/Imported-DataModel.png)

7.

Apply any makeup decals or eyebrow and eyelash accessories to characters in the test place by dropping makeup assets in the appropriate character's Makeup  or Accessories  folder.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Character-Folders.png)

8.

Click the Play  button, then navigate to the character with new makeup assets to preview.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
