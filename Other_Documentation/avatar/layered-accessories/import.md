<!-- Source: https://create.roblox.com/docs/avatar/layered-accessories/import -->

Import layered accessories | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar/layered-accessories/import.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. Accessories and clothing
6. /
7. Layered accessories

# Import layered accessories

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar/layered-accessories/import.md)

Studio's Importer lets you import 3D assets into your projects, such as character bodies, makeup, and layered accessories. The following instructions detail how to import a layered accessory .fbx  or .gltf  file into Studio as a Model  object and convert it into an Accessory  object that you can use in your games, upload to the Marketplace, or share with other creators.

While the Importer provides object previews and error-checking to ensure that your creation meets Roblox's [general 3D requirements](/docs/art/modeling/specifications) , it's important to ensure that your character model also meets Roblox's [layered accessory specifications](/docs/avatar/layered-accessories/specifications)  to use or sell this asset as an avatar-ready layered accessory, otherwise you can encounter errors at different points in the workflow.

## [Import accessories](#import-accessories)[](#import-accessories)

To import your asset as a layered accessory:

1.

In the Home  tab, click the Import  button to open the Importer. A file browser opens.

2.

Select your layered accessory's .fbx  or .gltf  file. The Importer loads a preview of the layered accessory.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/Import-Layered-Accessory.png)

3.

Select Import . The asset populates in your workspace as a [Model](/docs/reference/engine/classes/Model)  with the appropriate textures applied as a [SurfaceAppearance](/docs/reference/engine/classes/SurfaceAppearance)  or [MeshPart.TextureID](/docs/reference/engine/classes/MeshPart#TextureID) .

Textures didn't load correctly?

If your textures didn't load correctly, you can import them manually using the [Asset Manager](/docs/projects/assets/manager) :

1.

In the Asset Manager , click the Import  button. If you are unable to access the Asset Manager, save and publish your game first.

2.

Upload your image files.

3.

After moderation clears your images, select the [MeshPart](/docs/reference/engine/classes/MeshPart)  parented within your imported [Model](/docs/reference/engine/classes/Model) .

4.

If you are using a single basic texture, set the [MeshPart.TextureID](/docs/reference/engine/classes/MeshPart#TextureID)  property to your uploaded texture image.

5.

If you are using PBR textures:

1.

Add a [SurfaceAppearance](/docs/reference/engine/classes/SurfaceAppearance)  child to your [MeshPart](/docs/reference/engine/classes/MeshPart) .

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Avatar-Surface-Appearance.png)

2.

In the [SurfaceAppearance](/docs/reference/engine/classes/SurfaceAppearance)  properties, click each property value and assign the appropriate texture image from the asset dropdown:

1.

Set the ColorMap  to the _ALB  texture image.

2.

Set the MetalnessMap  to the _MTL  texture image.

3.

Set the NormalMap  to the _NOR  texture image.

4.

Set the RoughnessMap  to the _RGH  texture image.

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Avatar-Roughness-Map.png)

## [Convert layered accessories](#convert-layered-accessories)[](#convert-layered-accessories)

After importing your asset into Studio, you can begin converting  the [Model](/docs/reference/engine/classes/Model)  object into a [Accessory](/docs/reference/engine/classes/Accessory)  using the [Accessory Fitting Tool](/docs/avatar/accessory-fitting-tool)  (AFT) so that avatar character bodies can equip your layered accessory.

For shoes, you must convert the left shoe and the right shoe as separate layered accessories. Use the following instructions for each shoe before grouping both shoe accessories as a [Model](/docs/reference/engine/classes/Model)  when [saving to Roblox](/docs/marketplace/publish-to-marketplace#upload-an-asset) .

To generate your layered accessory:

1.

In the toolbar's Avatar  tab, click Accessory  to open the AFT. The Accessory Fitting Tool  panel displays.

2.

In the panel:

1.

Select the Part  field, then in the Explorer  window, select the layered accessory [MeshPart](/docs/reference/engine/classes/MeshPart)  object.

2.

Back in the panel, click the Next  button. The Asset Type  page displays.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/AFT-Select-Mesh-Pants.png)

3.

In the Asset Type  page:

1.

Set asset type to Clothing , then use the dropdown menu to choose the clothing type of your layered accessory.

2.

Click the Next  button. A preview panel displays with a default character wearing your layered accessory.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/AFT-Select-Type-Pants.png)

4.

[Test](/docs/avatar/accessory-fitting-tool#test-accessories)  out various sample characters and animations to make sure your layered accessory is deforming and moving correctly.

-

If necessary, make minor cage adjustments using the editing features. Larger cage changes may require returning to your third-party modeling software and re-exporting the asset.

5.

After previewing your asset, click the Generate MeshPart Accessory  button. Your 3D model populates in your project as an [Accessory](/docs/reference/engine/classes/Accessory)  object.

With this [Accessory](/docs/reference/engine/classes/Accessory)  object, you can perform any of the following:

-

Begin the process of [uploading and publishing](/docs/marketplace/publish-to-marketplace#upload-an-asset)  the layered accessory to the Marketplace.

-

Use the layered accessory in your current game by equipping it to character models with [HumanoidDescription](/docs/characters/appearance#manually-modify-appearance) , or by dragging and dropping the layered accessory under the appropriate character [Model](/docs/reference/engine/classes/Model)  object.

-

Save the layered accessory to your [Toolbox](/docs/projects/assets/toolbox)  or make it public on the [Creator Store](/docs/production/creator-store)  to use within any of your games or share with other creators.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
