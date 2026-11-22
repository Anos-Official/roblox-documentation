<!-- Source: https://create.roblox.com/docs/avatar/character-bodies/import -->

Import character bodies | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar/character-bodies/import.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. Bodies

# Import character bodies

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar/character-bodies/import.md)

Studio's Importer lets you import 3D assets into your projects, such as avatar clothing, accessories, and character bodies. The following instructions detail how to import a character body .fbx  or .gltf  file into Studio as a Model  object that you can use in your games, upload to the Marketplace, or share with other creators.

If your .fbx  or .gltf  file is a single mesh, you can use the [Avatar Setup](/docs/../../avatar-setup)  tool to automatically partition the mesh into the appropriate 15 body parts necessary for an avatar character body.

While the Importer provides object previews and error-checking to ensure that your creation meets Roblox's [general 3D requirements](/docs/art/modeling/specifications) , it's important to ensure that your character model also meets Roblox's [character body specifications](/docs/avatar/character-bodies/specifications)  to use or sell this asset as an avatar-ready character model, otherwise you can encounter errors at different points in the workflow.

To import your asset as a character body model:

1.

In the Home  tab, click the Import  button to open the 3D Importer. A file browser opens.

2.

Select your rigged character's .fbx  or .gltf  file. The 3D Importer loads a preview of the character model.

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Avatar-3D-Importer.png)

-

If textures don't load for your asset, you can manually import your textures later.

-

For additional information on import settings and troubleshooting, see [Importer](/docs/studio/importer) .

3.

In the Rig General  section,

1.

OPTIONAL

 If you are importing an [advanced R15 rig](/docs/avatar/character-bodies/specifications#advanced-r15-rigs) , set Rig Type  to Custom Humanoid .

2.

Set Rig Scale  to the appropriate [Body Scale](/docs/avatar/character-bodies/specifications#body-scale)  of your character.

3.

Set Constraint Type  to Joint Upgrade .

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Rig-General.png)

4.

Select Import . The asset populates in your workspace as a [Model](/docs/reference/engine/classes/Model)  with the appropriate textures applied as a [SurfaceAppearance](/docs/reference/engine/classes/SurfaceAppearance)  or [MeshPart.TextureID](/docs/reference/engine/classes/MeshPart#TextureID) .

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Avatar-Studio-Example.png)

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Avatar-Data-Model.png)

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

With this new character [Model](/docs/reference/engine/classes/Model) , you can perform any of the following:

-

If your character includes an [advanced R15 rig](/docs/avatar/character-bodies/specifications#advanced-r15-rigs) , add [HumanoidRigDescription](/docs/reference/engine/classes/HumanoidRigDescription)  and/or [DigitsRigDescription](/docs/reference/engine/classes/DigitsRigDescription)  objects for Marketplace and animation requirements. You may need to use the [Adaptive Animation](/docs/characters/adaptive-animation)  plugin to remap your joints and set a baseline t-pose reference to better support your animations.

-

Begin the process of [uploading and publishing](/docs/marketplace/publish-to-marketplace#upload-an-asset)  the character model to the Marketplace. This involves some additional validation and moderation steps.

-

Use the model in your current game and modify the model's appearance with [HumanoidDescription](/docs/characters/appearance#manually-modify-appearance) .

-

Playtest as the character by renaming the [Model](/docs/reference/engine/classes/Model)  to StarterCharacter  and moving the [Model](/docs/reference/engine/classes/Model)  to the [StarterPlayer](/docs/reference/engine/classes/StarterPlayer)  folder in the Explorer  before play testing.

-

Save the model to your [Toolbox](/docs/projects/assets/toolbox)  or make it public on the [Creator Store](/docs/production/creator-store)  to use within any of your games or share with other creators.

Character creation is a complex process that requires lots of testing and iteration. For information on importing your character model into a test place and verifying your avatar and related components, see [Test character bodies](/docs/avatar/character-bodies/test) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
