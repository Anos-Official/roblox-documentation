<!-- Source: https://create.roblox.com/docs/en-us/avatar/makeup/import -->

Import into Studio | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar/makeup/import.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. Makeup

# Import into Studio

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar/makeup/import.md)

Studio's Importer lets you import 3D assets into your projects, such as avatar clothing, accessories, and Roblox's [template heads](/docs/en-us/avatar/makeup#template-heads)  for makeup. The following instructions detail how to import a .fbx  or .gltf  template file from the best practice [creation process](/docs/en-us/avatar/makeup#creation-process)  into Studio as a Model  object that you can use in your games, upload to the Marketplace, or share with other creators.

These instructions apply specifically to the [Makeup test place](https://github.com/Roblox/avatar/tree/main/Makeup)  that uses a script to programmatically apply a decal to the face of the associated character.

To import your asset as a makeup model:

1.

Before you begin, it's important to ensure that your template file includes the following objects that are correctly configured to meet Roblox's [makeup specifications](/docs/en-us/avatar/makeup/specifications) , otherwise you can encounter errors in later steps:

-

Target head mesh

-

Target head cage mesh

-

If modified, Lips  mesh and associated textures.

-

If modified, Face  mesh and associated textures.

-

If modified, Eyes  mesh and associated textures.

2.

In Studio, open up the [Makeup test place](https://github.com/Roblox/avatar/tree/main/Makeup) .

3.

In the Home  tab, click the Import  button to open the Importer. A file browser opens.

4.

Select your makeup's .fbx  or .gltf  file. The Importer loads a preview of your makeup.

5.

Verify there are no errors with the imported components, then click Import  to add the file into Studio. A new Model  populates in the workspace.

6.

In the Explorer  window, expand the new Model  and verify that Decal  child objects have populated, each with their own WrapTextureTransfer  child object.

![](https://prod.docsiteassets.roblox.com/assets/makeup/Imported-DataModel.png) On import, makeup decals appear within the Model.

![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Studio-Datamodel.png) Each decal parents a WrapTextureTransfer object

7.

Copy your new Decal  objects into a character model's Makeup  folder.

8.

OPTIONAL

 If you want to apply eyebrows or eyelashes, move those [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  objects into the character's Accessories  folder. For this place file, you do not need to convert eyelashes and eyebrows into Accessories first.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Character-Folders.png)

9.

Press Play  to playtest and verify that the character has the new makeup applied.

## [Test with Avatar Setup](#test-with-avatar-setup)[](#test-with-avatar-setup)

You can also use the Avatar Setup tool to preview makeup assets without playtesting.

1.

Open the Avatar Setup tool by navigating to Avatar  > Setup .

2.

Select the model you would like to preview your assets on.

3.

For makeup decals , such as eyes, face, and lips:

1.

In the Explorer  window, select any makeup decal assets you want to add into the Avatar Setup preview. The preview only supports valid makeup decals with a child [WrapTextureTransfer](/docs/en-us/reference/engine/classes/WrapTextureTransfer) .

2.

In the Avatar Setup panel, click the +  symbol to add the assets to the Avatar Setup tool.

3.

In the new prompt, specify the makeup asset type (eyes, face, lips), for each decal selected.

4.

For makeup meshes , such as eyebrows and eyelashes:

1.

In the Explorer  window, move the [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  objects as children within the avatar model.

2.

In the Avatar Setup panel, click the +  symbol to add the assets to the Avatar Setup tool.

5.

In the Avatar Setup panel, navigate to the Face  > Makeup  tab, then validate that your assets were properly imported into the tool.

6.

Click on assets to equip them in your preview.

1.

Change the order of the assets by dragging their icons on the right side of the preview box.

2.

Click X  to remove them from your avatar preview.

7.

To see how makeup animates, navigate to the Animations  tab, then test various sequences to see what your avatar looks like with the makeup applied.

For the best results, use the avatars provided from Roblox in the test place. You may also bring in any other avatar, but the quality of the makeup fit depends on the head's underlying cage, which may result in varied appearance if not properly aligned.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
