<!-- Source: https://create.roblox.com/docs/avatar-setup -->

Avatar Setup | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar-setup.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. Avatar Setup

# Avatar Setup

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar-setup/index.md)

Avatar Setup  helps accelerate the avatar character body, rigid accessory, and layered accessory creation process by automatically processing custom models into avatar assets. If your characters and rigid/layered accessories don't have all essential components for publishing to the [Marketplace](https://www.roblox.com/catalog) , Avatar Setup can perform the following for your 3D models:

-

Rigging  — Adds a [R15 rigging armature](/docs/avatar/character-bodies/specifications#rigging)  to your body model to enable movement and animation.

-

Skinning  — Adds weights and influences to various surfaces of your mesh, ensuring an organic and natural flexibility during movement.

-

Facial animation  — Generates the FACS poses, facial rigging, skinning, and animation data required for facial animation and avatar chat.

-

Caging  — Adds the required cages to your asset, enabling it to support layered accessories.

-

Partitioning  — Separates the body mesh into the appropriate 15 body parts necessary for an avatar character body.

-

Creating attachments  — Adds the appropriate attachment points enabling the character to wear rigid accessories.

 ![Avatar Preview button indicated in Avatar tab](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Avatar-Setup.png)

## [Import a 3D asset](#import-a-3d-asset)[](#import-a-3d-asset)

The [Importer](/docs/studio/importer)  tool allows you to import custom 3D assets that you made in third-party modeling tools like Blender or Maya directly into Studio. If your custom 3D assets don't include all essential avatar components for the Marketplace, Avatar Setup will add any missing components as it processes the assets.

To import a custom 3D asset using the Importer tool:

1.

Navigate to the Home  tab, then select Import . A file browser displays.

2.

Select the .fbx , .obj , or .gltf  model you want to import. After a few moments, the Import Preview  window opens with a preview of your asset.

3.

In the File General  section, disable the Upload To Roblox  option. This setting stops the asset from immediately saving to your Toolbox, preventing unwanted copies of similar assets.

4.

OPTIONAL

 To create an import preset for this workflow,

1.

In the top-right of the Import Preview  window, click the ⋯ dropdown.

2.

In the contextual menu, click Save as New .

5.

Verify the preview and any [warnings or errors](/docs/studio/importer#warnings-and-errors)  in your model. Certain warnings and errors may require readjusting the model in the third-party software you used to create the asset.

6.

Click the Import  button to add the model into your workspace. After a moment, it displays as a [Model](/docs/reference/engine/classes/Model)  object in the Explorer  window.

When you import a new model into Studio, the system adds the model to the moderation queue. If your model is moderated, you will receive a moderation email with a link to appeal. This appeal can take up to 10 minutes to resolve.

## [Run Avatar Setup](#run-avatar-setup)[](#run-avatar-setup)

When your project has the appropriate [Model](/docs/reference/engine/classes/Model)  object in your workspace, you can run Avatar Setup to see if your 3D asset requires any additional avatar components before you can publish it to the Marketplace as a character body, rigid accessory, or layered accessory. Avatar Setup supports the conversion of the following 3D asset types from a base [Model](/docs/reference/engine/classes/Model) :

| Asset type | | Input object | | Output object |
| --- | --- |
| Avatar character body | | [Model](/docs/reference/engine/classes/Model)  containing one or more [MeshPart](/docs/reference/engine/classes/MeshPart)  objects that meet Avatar Setup's supported [body inputs](/docs/avatar-setup/auto-setup-requirements#character-bodies) . | | [Model](/docs/reference/engine/classes/Model)  parenting associated 15 [MeshPart](/docs/reference/engine/classes/MeshPart)  objects and other expected [avatar components](/docs/avatar/character-bodies#character-body-components) . |
| Rigid accessory | | [Model](/docs/reference/engine/classes/Model)  containing one or more [MeshPart](/docs/reference/engine/classes/MeshPart)  objects that meet Avatar Setup's supported [rigid accessory inputs](/docs/avatar-setup/auto-setup-requirements#rigid-accessories) .

Must [bundle](/docs/avatar-setup/auto-setup-requirements#bundle-multiple-assets)  with an avatar body [Model](/docs/reference/engine/classes/Model)  for Avatar Setup. | | [Accessory](/docs/reference/engine/classes/Accessory)  that includes all expected [rigid accessory components](/docs/avatar/rigid-accessories#rigid-accessory-components) . |
| Layered accessory | | [Model](/docs/reference/engine/classes/Model)  containing one or more [MeshPart](/docs/reference/engine/classes/MeshPart)  objects that meet Avatar Setup's supported [accessory inputs](/docs/avatar-setup/auto-setup-requirements#accessories-and-clothing) .

Can optionally [bundle](/docs/avatar-setup/auto-setup-requirements#bundle-multiple-assets)  with an avatar body [Model](/docs/reference/engine/classes/Model)  for Avatar Setup. | | [Accessory](/docs/reference/engine/classes/Accessory)  that includes all expected [layered accessory components](/docs/avatar/layered-accessories#layered-accessory-components) . |
| Multiple accessories with single body | | Folder  [bundle](/docs/avatar-setup/auto-setup-requirements#bundle-multiple-assets)  containing one or more [Model](/docs/reference/engine/classes/Model)  that meet supported inputs for rigid accessories, layered accessories, or avatar bodies.

Must [bundle](/docs/avatar-setup/auto-setup-requirements#bundle-multiple-assets)  with an avatar character body [Model](/docs/reference/engine/classes/Model)  for Avatar Setup. | | [Model](/docs/reference/engine/classes/Model)  character body and any [Accessory](/docs/reference/engine/classes/Accessory)  equippable items.

All generated assets include expected avatar item components. |

For more in-depth information on supported input configurations, see the individual asset specifications on [Avatar Setup requirements](/docs/avatar-setup/auto-setup-requirements) .

To run Avatar Setup:

1.

In the Explorer  window, select the model or specific meshes of the model. If you want to select multiple meshes at once, expand the [Model](/docs/reference/engine/classes/Model)  object, then hold shift and click on the individual mesh objects you want to process as avatar assets.

Reference models

For an asset that meets all of these model requirements, download one of the following Avatar Setup templates for your own reference and testing:

Nature Girl

![](https://prod.docsiteassets.roblox.com/assets/art/resources/Archer-Girl-Preview.png)

A comprehensive .zip  folder of an Avatar Setup ready character model, including rigid and layered accessory assets and PBR textures.

This template is not compatible with the traditional avatar creation workflow.

[Download](https://prod.docsiteassets.roblox.com/assets/art/reference-files/NatureArcherGirl-AutoSetup.zip)

Stylish Male

![](https://prod.docsiteassets.roblox.com/assets/art/resources/StylizedMale-Preview.png)

A comprehensive .zip  folder of an Avatar Setup ready character model, including the base body and associated PBR textures.

This template is not compatible with the traditional avatar creation workflow.

[Download](https://prod.docsiteassets.roblox.com/assets/art/reference-files/StylizedMale-AutoSetup.zip)

2.

With the model or meshes selected, navigate to the Avatar  tab, then select Avatar Setup .

3.

In the Configure Models  section,

1.

Set Preset  to the appropriate category.

1.

If you want to publish your assets to the Marketplace for users to purchase and use across Roblox, select Platform Avatar . This option generates a more restrictive setup that's necessary to pass validation and moderation.

2.

If you want to upload your assets to your inventory for non-player characters (NPCs) or starter player characters for your games, select Development Avatar . This option generates a less restrictive setup.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Configure-Models.png)

2.

Set Type  for each asset to the correct asset type so that it moves and animates correctly in the 3D space.

1.

For character body geometry, select Body .

2.

For layered accessory assets, select Layered .

3.

For rigid accessory assets, select Rigid .

4.

For eyebrow and eyelash assets, select Eye Layered .

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Set-Type.png)

4.

OPTIONAL

 Near the bottom-left corner, click on the gear icon to configure specialty settings for your character model.

1.

If your character has a decal for its face and you want to enable the conversion of the texture into a [dynamic head](/docs/avatar/dynamic-heads) , enable Handle face as 2D decal . This process allows you to preserve your creative intent while complying with Marketplace policy that requires all avatars to have dynamic heads.

Converting a decal into a dynamic head?

The process of converting a decal into a dynamic head infers eye and mouth regions from your existing texture, generates cages and FACS data, then maps the result onto a dynamic head template. For best results, review the following guidance:

Run Avatar Setup with the character's body and head

-

If you only run Avatar Setup with the character's head, this speciality setting will fail.

Verify avatar face is front-facing

-

Before you run Avatar Setup, verify that your character's face is facing the front and visible in the preview. Whenever you manually position your character's face, make sure you enable Manually align front  in the Avatar Setup window's speciality settings.

Delete the [FaceControls](/docs/reference/engine/classes/FaceControls)  object

-

Avatar Setup retains your current face setup whenever it detects a [FaceControls](/docs/reference/engine/classes/FaceControls)  object under your character's [Head](/docs/reference/engine/enums/BodyPart)  model. If one exists in your character, delete it from before running Avatar Setup.

Use [SurfaceAppearance](/docs/reference/engine/classes/SurfaceAppearance)  instead of [TextureID](/docs/reference/engine/classes/MeshPart#TextureId)

-

When you have only [TextureID](/docs/reference/engine/classes/MeshPart#TextureId)  or both [TextureID](/docs/reference/engine/classes/MeshPart#TextureId)  and [SurfaceAppearance](/docs/reference/engine/classes/SurfaceAppearance)  objects defined for your avatar, remove or replace the [TextureID](/docs/reference/engine/classes/MeshPart#TextureId)  objects with [SurfaceAppearance](/docs/reference/engine/classes/SurfaceAppearance)  objects for significant texture quality improvements when rendering.

2.

If your character includes an [advanced R15 rig](/docs/avatar/character-bodies/specifications#advanced-r15-rigs)  with additional joints, enable Create R15 with optional joints .

3.

If you want to manually align the front direction of your character with the negative Z-axis in world space, enable Manually Align Front . While auto-setup does this automatically for you, it can sometimes fail to properly determine the front of your character.

4.

If you want to add a post-processing step to significantly improve the alignment of your character's head cage with the head model and its facial features, enable Improve facial caging . This is particularly important if you plan on using [makeup](/docs/avatar/makeup)  with your character.

5.

If you are importing a development avatar and want to skip the auto-decimation of input meshes with resolution above the triangle budgets required for the Marketplace, disable Reduce triangle count .

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Gear-Icon.png)

5.

Near the bottom-right corner, click the Set Up  button.

1.

If your model requires auto-setup for missing avatar components, the tool begins processing your model. This can take several minutes. Once auto-setup is complete, the tool populates your avatar asset in the Avatar Setup window.

2.

If your model doesn't require auto-setup, the tool populates your avatar asset in the Avatar Setup window.

## [Testing tools](#testing-tools)[](#testing-tools)

After you successfully load your character into the Avatar Setup window, you can access various testing tools in the window's side navigation to ensure your character moves, animates, and equips rigid and layered accessories properly.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Testing-Interface.png)

In each of these interfaces, you can see which items are currently equipped to your character on the right side of the Avatar Setup window. From here, you can:

-

Unequip items  by right-clicking on an equipped item, then selecting Unequip Item  from the contextual menu.

-

Set the worn order  by dragging and ordering the various equipped accessories.

If you discover any issues that can't be resolved with Avatar Setup testing tools, you may need to update your character model using the third-party modeling software you used to create the asset, then retry the auto-setup process.

### [Check Body](#check-body)[](#check-body)

The Check Body  interface contains various tabs for checking how your character model animates, emotes, wears rigid and layered accessories, and changes skin tone. To learn more about what you can do with this interface, click through the following tabs.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Skin-Tone-Selector.png)

Animations Clothing Accessories Body

The Animations  tab lets you test how your character animates and emotes using each [default animation](/docs/animation/using#default-character-animations)  that Roblox provides for every avatar, such as the walk, jump, and swim animation.

If you notice any issues with your character's body as it animates, you can either use Avatar Setup's editing tools or your favorite third-party 3D modeling application to adjust your character's rig until the animations play properly.

### [Check Face](#check-face)[](#check-face)

The Check Face  interface zooms closer to the character's face and allows you to test various facial poses and cosmetics. To learn more about what you can do with this interface, click through the following tabs.

![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Test-Face-1.png) Check the range of facial poses with multiple facial animation tests.

![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Test-Face-2.png) Unexpected facial animation behavior, such as crashing or artifacts, may require minor adjustment to the base mesh and re-running the auto-setup process.

Animations Body Makeup Accessories

The Animations  tab lets you test your character's facial animations and range of motion for different parts of the face, such as the character's eyeballs, eyebrows, and mouth.

If you notice any issues with your character's facial expressions, you can either use Avatar Setup's editing tools or your favorite third-party 3D modeling application to adjust your character until the animations play properly.

### [Test in Experience](#test-in-experience)[](#test-in-experience)

The Test in Experience  tab starts playtesting the game with your character model. This button references your active [playtesting mode](/docs/studio/testing-modes)  and retains the changes you make in the Avatar Setup window.

### [Add test items](#add-test-items)[](#add-test-items)

In addition to the side navigation test tooling, you can add custom assets to the Avatar Setup's testing palette that are either active in your current project or by assetID. For more information on either method, review the tabs below.

From Project By AssetID

To add a custom item that's active in your current project to the Avatar Setup testing palette:

1.

In the Explorer  window or viewport, select a valid accessory or body part asset.

2.

In the Avatar Setup  window, navigate to the Check Body  or Check Face  interface, then click the plus button at the bottom of the selection column along the left side of the window. The item appears in the appropriate section and subsection of the interface, such as Accessories → Hair.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Add-Object.png)

## [Editing tools](#editing-tools)[](#editing-tools)

In addition to the Avatar Setup window, you can use Avatar Setup's Attachment Tool and Cage Brush in the viewport to make minor to moderate adjustments to the character's attachment points and cage.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Editing-Tools.png)

### [Attachment Tool](#attachment-tool)[](#attachment-tool)

The Attachment Tool  displays all attachment points on the character's body. When you select an attachment point, the Move tool displays, allowing you to adjust the attachment point's position within the character's body.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Active-Attachment.png)

### [Cage Brush](#cage-brush)[](#cage-brush)

The Cage Brush lets you modify your character's body cage mesh and make adjustments to how layered accessories fit on your character. The following controls provide fine-grain control on your cage edits:

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Cage-Edit-Panel.png)

-

Symmetrical and mirror edits along X-axis.

-

Brush with radius and falloff controls.

-

Brush falloff visualization over the vertices.

-

Ability to hide or display equipped layered accessories. Layered accessories will update in real time in the Avatar Setup  tool's preview window.

Major cage edits may require returning to your third-party modeling tool, making your cage adjustments, and then re-exporting the asset.

## [Publish to the Marketplace](#publish-to-the-marketplace)[](#publish-to-the-marketplace)

The Save  button opens the Asset Configuration dialog, allowing you to upload the avatar and any accessory items to your inventory or publish everything configured as platform avatar assets to the Marketplace.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Save.png)

When publishing your assets to the Marketplace, you must pay an [upload fee](/docs/marketplace/publish-to-marketplace#upload-an-asset)  and pass moderation in order to add your assets to the catalog. For additional resources on the publishing process and Marketplace, see the following:

-

[Publish to the Marketplace](/docs/marketplace/publish-to-marketplace)

-

[Marketplace fees and commissions](/docs/marketplace/marketplace-fees-and-commissions)

-

[Marketplace policy](/docs/marketplace/marketplace-policy)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
