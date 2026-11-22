<!-- Source: https://create.roblox.com/docs/en-us/avatar/accessory-fitting-tool -->

Accessory Fitting Tool | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar/accessory-fitting-tool.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Avatar](/docs/en-us/avatar)

# Accessory Fitting Tool

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar/accessory-fitting-tool.md)

The Accessory Fitting Tool  (AFT) is a built-in Studio tool that allows you to test your custom models on multiple combinations of character bodies, animations, and accessories before generating the final [Accessory](/docs/en-us/reference/engine/classes/Accessory)  object. When testing your accessories, you can make minor fit and positional changes to ensure that you get the best result possible.

The AFT automatically handles the conversion of the custom [Model](/docs/en-us/reference/engine/classes/Model)  or [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  based on your menu selections, allowing you to create [layered accessories](/docs/en-us/avatar/layered-accessories)  or [rigid accessories](/docs/en-us/avatar/rigid-accessories) . After generating an accessory, the AFT creates the correct [Accessory](/docs/en-us/reference/engine/classes/Accessory)  object hierarchy with any updated fit edits, sets the appropriate AccessoryType  property, and generates any required body attachment points.

![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Rigid-Example.png) Test and edit the orientation and placement of your rigid accessories.

![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Layered-Example.png) Test and edit the cages of your layered accessories.

If you are intending to sell an accessory on the Marketplace, make sure your accessory model design adheres to [Marketplace policies](/docs/en-us/marketplace/marketplace-policy) .

## [Set up accessories](#set-up-accessories)[](#set-up-accessories)

The first stage of the fitting workflow allows you to configure the type of accessory to correctly populate the correct fitting tools and generate the appropriate accessory object. When selecting the type of accessory, the following options are available:

-

Clothing : Layered accessories that use an inner and outer cage to stretch and wrap around a character body and existing clothing items.

-

Accessory : Rigid accessories that attach to a specific attachment point of a character body and remain static in that position and orientation.

Before using the AFT, ensure that you have the [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  or [Model](/docs/en-us/reference/engine/classes/Model)  you intend to create into an accessory selectable in your project. As a reference, you can test the AFT using a reference [layered accessory](https://prod.docsiteassets.roblox.com/assets/accessories/reference-files/Additional-FBX-assets.zip)  or [rigid accessory](https://prod.docsiteassets.roblox.com/assets/accessories/reference-files/Bow-rigid.rbxm)  custom model.

To setup your accessories:

1.

In the toolbar's Avatar  tab, click Accessory  to open the AFT. The Accessory Fitting Tool  panel displays.

2.

In the panel:

1.

Select the Part  field, then in the Explorer  window, select your accessory's respective [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  or [Model](/docs/en-us/reference/engine/classes/Model)  object. The text field populates with the name of the object.

2.

Back in the panel, click the Next  button. The Asset Type  page displays.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating-rigid/AFT-Select-Mesh-Bow.png)

3.

In the Asset Type  page:

1.

Select the correct asset type for your accessory:

-

If your asset is a layered accessory, select Clothing .

-

If your asset is a rigid accessory, select Accessory .

2.

Use the dropdown menu to choose the AssetType  of your accessory.

3.

Set body type to the [body scale](/docs/en-us/avatar/character-bodies/specifications#body-scale)  you determined while sculpting and sizing of the asset during the creation process.

-

Classic : Sets the scaling of the accessory to classic proportions.

-

Proportions Slender : Sets the AvatarPartScaleType  value to ProportionsSlender .

-

Proportions Normal : Sets the AvatarPartScaleType  value to ProportionsNormal .

This setting does not affect layered accessories, and it only affects rigid accessories if the specific body part has a different AvatarPartScaleType  [StringValue](/docs/en-us/reference/engine/classes/StringValue)  object. For more information, see [Rigid Accessories - AvatarPartScaleType](/docs/en-us/avatar/rigid-accessories/specifications#avatarpartscaletype) .

4.

Click the Next  button. A preview panel displays with a default character wearing your accessory.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/AFT-Select-Type-Pants.png)  ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating-rigid/AFT-Add-Avatar-Panel-Bow.png)

## [Test accessories](#test-accessories)[](#test-accessories)

After you provide the initial accessory details, the AFT displays a preview panel. With the preview panel, you can test how your accessory looks on different combinations of character bodies, rigid accessories, layered accessories, animations, and custom assets in your game. If you notice any fitting issues with your accessory, you can use the [edit](#edit-accessory-fit)  tools to make minor adjustments to your accessory.

At any point of the testing process, you can [initiate a playtest](/docs/en-us/studio/testing-modes#playtesting)  to launch an instance of your game where your avatar is replaced with the currently selected character body and accessories from the AFT.

### [With different bodies](#with-different-bodies)[](#with-different-bodies)

You can select different character bodies to test the fit and wear of your accessories. The AFT supplies several default character body models you can use to ensure your accessories fit as expected.

![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Body-Example-1.png) Bazooka Bones character preview

![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Body-Example-2.png) Magma Fiend character preview

To test your accessory with a different character body:

1.

In the tool's catalog, navigate to Avatars  > Default .

2.

Click one of the character model tiles. The preview loads with the selected character model.

1.

If two character tiles are selected, click a selected tile to deselect it.

2.

In the character preview, click  and drag  to rotate and right-click  to pan to inspect your character.

### [With other layered accessories](#with-other-layered-accessories)[](#with-other-layered-accessories)

You can select multiple layered accessories to test the fit and layering of your caged accessories. The AFT supplies several default character models you can use to ensure your accessories fit as expected.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Clothing-Examples.png)

To test your accessory with a different layered accessory:

1.

In the tool's catalog, navigate to Clothing  > Default .

2.

Click one or more of the available catalog items. The character preview loads with the selected clothing accessory.

1.

In the catalog, click an active tile to deselect the asset.

2.

In the character preview, drag  and drop  the accessory boxes to change the layer order.

3.

In the character preview, click  and drag  to rotate and right-click  to pan to inspect your character.

### [With animations](#with-animations)[](#with-animations)

You can select different animations to test the movement of your accessories. The AFT supplies several default animation assets you can use to ensure your accessories fit as expected when a model is performing various movements.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Animation-Examples.png)

To test your accessory with different animations:

1.

In the tool's catalog, navigate to Animations  > Default .

2.

Click one of the animation asset tiles.

1.

In the catalog, press the play and pause icon to control the playback.

2.

In the character preview, click  and drag  to rotate and right-click  to pan to inspect your character.

### [With custom assets](#with-custom-assets)[](#with-custom-assets)

You can add custom character body models, layered accessories, and animations that are part of your workspace to the AFT preview catalog. Use this functionality to verify that your accessory works with any other custom models or accessories they may interact with in your game.

To add custom assets:

1.

Click the ⊕ icon next to the catalog search. A prompt appears, allowing you to choose a supported object.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Custom-Asset-Icon.png)

2.

Select any [Accessory](/docs/en-us/reference/engine/classes/Accessory) , [Model](/docs/en-us/reference/engine/classes/Model) , [MeshPart](/docs/en-us/reference/engine/classes/MeshPart) , [Animation](/docs/en-us/reference/engine/classes/Animation)  or [Folder](/docs/en-us/reference/engine/classes/Folder)  within the 3D viewport or Explorer  window. The asset displays in the corresponding Custom  category.

## [Edit accessory fit](#edit-accessory-fit)[](#edit-accessory-fit)

The AFT populates different fitting tools depending on the type of accessory you're creating.

### [Layered accessories](#layered-accessories)[](#layered-accessories)

When editing layered accessories, the following tools populate in the viewport:

| Icon | | Description |
| --- | --- |
| ![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Cage-Editing-Icon.png) | | Toggles the [Cage Editing](#cage-editing)  interface in the viewport for making minor inner or outer cage changes to your clothing.  |
| ![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Autoskin-Icon.png) | | Toggles [auto-skinning](/docs/en-us/avatar/automatic-skinning-transfer#enable-automatic-skinning-transfer)  between EnabledPreserved  and EnabledOverride . Depending on the asset and skinning quality, auto-skinning may provide better results.
-

EnabledPreserved  uses the asset's original skinning data applied in a modeling software.

-

EnabledOverride  transfers skinning data from the avatar character instead of using the asset's original skinning data.

 |
| ![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Expand-Button.png) | | Displays a button to Bring Mannequin in View  which centers mannequin in front of the camera. |
| ![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Center-Mannequin.png) | | Centers the camera on the mannequin. |

#### [Cage editing](#cage-editing)[](#cage-editing)

When the Cage Editing interface is enabled, additional tools display in the viewport along with the vertices of the selected cage over the mannequin. This allows you to make positional edits to the cage and change how a layered accessory fits on a character body.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Cage-Editing-Example.png)

You can use these cage editing tools for minor to moderate cage edits, but if your asset requires major fit or sculpting changes, it's recommended to edit the cage meshes directly in a third-party modeling software, then reimport the updated model into Studio.

Use the following cage editing tools to help visualize and edit any cage vertices:

| Icon | | Description |
| ![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Cage-Editing-Icon.png) | | Toggles the selection for the inner and outer cage vertices. When selected, the vertices of that specific cage are available to edit.  |
| ![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Autoskin-Icon.png) | | Sets the radius of influence when editing vertices of the cage mesh. When editing a cage vertex, nearby vertices follow the changes for efficient cage editing.

A higher Falloff Distance applies influence to vertices further away from the origin. |
| ![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Expand-Button.png) | | Displays additional buttons:
-

Bring Mannequin in View - centers camera on the mannequin.

-

Reset Inner/Outer Cage - resets any changes made to the selected cage.

 |
| ![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Center-Mannequin.png) | | Sets the opacity of the mesh or the cage vertices, allowing you to better see and access certain vertices and angles of your layered accessory. |

To make changes to the vertices of the currently selected cage:

1.

In the toolbar, disable Move  snapping. This enables you to make detailed changes to a vertex's position.

2.

Select a vertex and use the Move  tool to reposition. Changes to the cage apply immediately and display in the preview panel.

1.

Use the opacity sliders to better visualize the changes to your cage.

2.

Set the Falloff Distance  depending on the number of vertices being adjusted at once.  ![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Edit-Vertex-Example.png)

### [Rigid accessories](#rigid-accessories)[](#rigid-accessories)

When fitting rigid accessories, a bounding box appears around the mannequin indicating the possible placement of that specific type of accessory. You can position, rotate, and scale objects within this bounding box to ensure your accessory fits on different character models.

![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Bounding-Box-Example-1.png) Adjust your rigid accessory fit within the bounding box.

![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Bounding-Box-Example-2.png) If the accessory is outside the appropriate space, the bounding box turns red.

### [Create accessory](#create-accessory)[](#create-accessory)

AFT applies any fit changes and generates the appropriate [Accessory](/docs/en-us/reference/engine/classes/Accessory)  instance in the workspace depending on the type of accessory selected and any configurations applied.

When you are ready to generate your accessory, select Generate MeshPart Accessory .

![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/LC-Hierarchy.png) Hierarchy generated for layered accessories.

![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Rigid-Hierarchy.png) Hierarchy generated for rigid accessories.

With an accessory successfully created, you can now try the following:

-

Begin the process of [uploading and publishing](/docs/en-us/marketplace/publish-to-marketplace)  the accessory to the Marketplace.

-

Use the accessory in your current game by equipping it to character models with [HumanoidDescription](/docs/en-us/characters/appearance#manually-modify-appearance) , or by dragging and dropping the accessory under the appropriate character [Model](/docs/en-us/reference/engine/classes/Model)  object.

-

Save the accessory to your [Toolbox](/docs/en-us/projects/assets/toolbox)  or make it public on the [Creator Store](/docs/en-us/production/creator-store)  to use within any of your games or share with other creators.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
