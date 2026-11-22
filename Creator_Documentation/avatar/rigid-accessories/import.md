<!-- Source: https://create.roblox.com/docs/en-us/avatar/rigid-accessories/import -->

Import rigid accessories | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar/rigid-accessories/import.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. Accessories and clothing
6. /
7. Rigid accessories

# Import rigid accessories

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar/rigid-accessories/import.md)

Studio's Importer lets you import 3D assets into your projects, such as character bodies, makeup, and rigid accessories. The following instructions detail how to import a rigid accessory .fbx  or .gltf  file into Studio as a Model  object and convert it into an Accessory  object that you can use in your games, upload to the Marketplace, or share with other creators.

While the Importer provides object previews and error-checking to ensure that your creation meets Roblox's [general 3D requirements](/docs/en-us/art/modeling/specifications) , it's important to ensure that your character model also meets Roblox's [rigid accessory specifications](/docs/en-us/avatar/rigid-accessories/specifications)  to use or sell this asset as an avatar-ready rigid accessory, otherwise you can encounter errors at different points in the workflow.

## [Import accessories](#import-accessories)[](#import-accessories)

To import your asset as a rigid accessory:

1.

In the Home  tab, click the Import  button to open the Importer. A file browser opens.

2.

Select your rigid accessory's .fbx  or .gltf  file. The Importer loads a preview of the rigid accessory.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating-rigid/Import-Rigid-Accessory.png)

3.

Select Import . The asset populates in your workspace as a [Model](/docs/en-us/reference/engine/classes/Model)  with the appropriate textures applied as a [SurfaceAppearance](/docs/en-us/reference/engine/classes/SurfaceAppearance)  or [MeshPart.TextureID](/docs/en-us/reference/engine/classes/MeshPart#TextureID) .

Textures didn't load correctly?

If your textures didn't load correctly, you can import them manually using the [Asset Manager](/docs/en-us/projects/assets/manager) :

1.

In the Asset Manager , click the Import  button. If you are unable to access the Asset Manager, save and publish your game first.

2.

Upload your image files.

3.

After moderation clears your images, select the [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  parented within your imported [Model](/docs/en-us/reference/engine/classes/Model) , then add a [SurfaceAppearance](/docs/en-us/reference/engine/classes/SurfaceAppearance)  child to your [MeshPart](/docs/en-us/reference/engine/classes/MeshPart) .

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating-rigid/Adding-Surface-Appearance-Bow.png)

4.

Select the [SurfaceAppearance](/docs/en-us/reference/engine/classes/SurfaceAppearance)  object, then in the Properties  window, click each property value and assign the appropriate texture image from the asset dropdown:

1.

Set the ColorMap  to the _ALB  texture image.

2.

Set the MetalnessMap  to the _MTL  texture image.

3.

Set the NormalMap  to the _NOR  texture image.

4.

Set the RoughnessMap  to the _RGH  texture image.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating-rigid/Surface-Appearance-Asset-Dropdown-Bow.png)

## [Convert rigid accessories](#convert-rigid-accessories)[](#convert-rigid-accessories)

After importing your asset into Studio, you can begin fitting  your imported object to a mannequin and converting  the [Model](/docs/en-us/reference/engine/classes/Model)  object into a [Accessory](/docs/en-us/reference/engine/classes/Accessory) . When fitting and converting your accessory, it's important to use the [Accessory Fitting Tool](/docs/en-us/avatar/accessory-fitting-tool)  (AFT) to correctly preview the placement and apply the correct configurations to your accessory.

To fit and generate your rigid accessory:

1.

In the toolbar's Avatar  tab, click Accessory  to open the AFT. The Accessory Fitting Tool  panel displays.

2.

In the panel:

1.

Select the Part  field, then in the Explorer  window, select the rigid accessory [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  object.

2.

Back in the panel, click the Next  button. The Asset Type  page displays.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating-rigid/AFT-Select-Mesh-Bow.png)

3.

In the Asset Type  page:

1.

Set asset type to Accessory , then use the dropdown menu to choose the location of where you want the rigid accessory to attach to a character's body.

2.

Set body type to the [body scale](/docs/en-us/avatar/rigid-accessories/specifications#body-scale)  you determined while sculpting and sizing of the asset during the creation process, then click the Next  button. A preview panel displays with a default character wearing your rigid accessory.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating-rigid/AFT-Select-Type-Bow.png)

4.

Select one of the humanoid characters as a mannequin:

1.

In the Avatars  section, select a humanoid character body.

2.

In the preview panel, deselect the previous selection. Your character body selection displays in the preview window.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating-rigid/AFT-Add-Avatar-Panel-Bow.png)

5.

Using both the AFT preview window and the viewport, adjust the position, scale, and rotation of the rigid accessory.

1.

Use the AFT preview window and your mannequin as an accurate preview of how your asset fits on the character. The clothing mannequin in the viewport does not accurately portray how rigid accessories attach.

2.

In the viewport, use the Move , Scale , and Rotate  tools to adjust the positioning of your rigid accessory.

3.

If you accidentally select something else, click back into the AFT panel to reselect the accessory and resume your adjustments using the transformation tools.

6.

After previewing and fitting your asset, click the Generate MeshPart Accessory  button. Your 3D model populates in your project as an [Accessory](/docs/en-us/reference/engine/classes/Accessory)  object.

With this [Accessory](/docs/en-us/reference/engine/classes/Accessory)  object, you can perform any of the following:

-

Begin the process of [uploading and publishing](/docs/en-us/marketplace/publish-to-marketplace#upload-an-asset)  the rigid accessory to the Marketplace.

-

Use the rigid accessory in your current game by equipping it to character models with a [HumanoidDescription](/docs/en-us/characters/appearance#manually-modify-appearance) , or by dragging and dropping the rigid accessory under the appropriate character [Model](/docs/en-us/reference/engine/classes/Model)  object.

-

Save the rigid accessory to your [Toolbox](/docs/en-us/projects/assets/toolbox)  or make it public on the [Creator Store](/docs/en-us/production/creator-store)  to use within any of your games or share with other creators.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
