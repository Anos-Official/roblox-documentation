<!-- Source: https://create.roblox.com/docs/art/modeling/calisthenics-tool -->

Calisthenics Tool | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/art/modeling/calisthenics-tool.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Learn](/docs/en-us/learn)

# Calisthenics Tool

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/art/modeling/calisthenics-tool.md)

This tool is no longer in active development. You are free to use the tool for any purpose. The tool may be out of date or incompatible with modern Roblox assets.

The Calisthenics Tool  is a supplemental [Blender](https://www.blender.org/)  add-on that allows you to quickly test your asset through a set of animation cycles to verify your skinning data. At any point during the animation testing, you can pause and use Blender's skinning Tools, such as [Weight Painting brushes](https://docs.blender.org/manual/en/latest/sculpt_paint/weight_paint/introduction.html) , to resolve any skinning imperfections.

Skinning your layered accessories and character bodies is a critical and often time-intensive process to create high quality assets that move and fit with different character bodies. Similar to the [Layered Accessory Validation Tool](/docs/art/accessories/validation-tool) , the Calisthenics Tool can save you time when testing your character models after rigging and skinning.

The Calisthenics Tool doesn't provide complete verification of all potential skinning issues. You must also ensure that your custom models meet Studio's [character body specifications](/docs/avatar/character-bodies/specifications)  and any applicable [layered accessory specifications](/docs/avatar/layered-accessories/specifications)  for the best results in your game.

Walking Animation

Running Animation

Generic Movements

## [Installation](#installation)[](#installation)

The Calisthenics Tool plugin is designed for [Blender 3.0+](https://www.blender.org/download/) . You can download and modify the tool for any use.

To install the Calisthenics Tool in Blender:

1.

Download the [CalisthenicsTool.zip](https://github.com/Roblox/avatar/tree/main/Tools/CalisthenicsTool)  and save the .zip  file locally.

2.

In Blender, navigate to Edit  > Preferences .

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/calisthenic-tool/Blender-Preferences.png)

3.

In the left sidebar of the Preferences  window, navigate to the Add-Ons  section.

4.

Click the Install…  button. A file browser displays.

5.

Select the .zip  and click Install Add-On .

6.

Using the search bar, search for "Calisthenics Tool" and select the add-on.

7.

Enable the add-on by checking the box next to the add-on name.

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/calisthenic-tool/Calisthenics-Tool-Addon.png)

8.

Close the Preferences window. You can now access the Calisthenics Tool by expanding the tool sidebar in the Viewport.

![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/calisthenic-tool/Toolbar-Slider.png) Use the arrow on the side of the Viewport to open the sidebar.

![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/calisthenic-tool/Calisthenics-Tool-Open.png) Access the Calisthenics Tool by selecting the tab in the sidebar tool menu.

## [Use the Calisthenics Tool](#use-the-calisthenics-tool)[](#use-the-calisthenics-tool)

After installation, you can use the Calisthenics Tool whenever you want to test a [standard R15](/docs/avatar/character-bodies/specifications#standard-r15-rigs)  rigging armature with skinning data. With the Calisthenics Tool, you can check how a character body would move with generic animations, as well as attach reference rigid accessories to verify attachment during these movements. The tool also includes an option to automatically export your character, removing reference animation and accessory data.

You can try out the Calisthenics Tool using an [example character body model](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/calisthenic-tool/Fish-Character-No-FACS.fbx) .

For demonstration purposes, this reference model doesn't contain FACS data. If you require a reference with facial animation, you can download the same model with FACS data from our [reference models](/docs/avatar/character-bodies/specifications#reference-files) .

### [Test animations](#test-animations)[](#test-animations)

When testing your character body model, first set the armature in the Calisthenics Tool then select one of the reference animations. It is important to visually verify your skinning quality using various movements and angles to ensure the best results for your model.

If you encounter any errors or warnings when setting armature or playing animations, verify that your model uses an appropriate bone hierarchy and naming convention outlined in Roblox's [custom mesh requirements](/docs/avatar/character-bodies/specifications) .

To test animations:

1.

Open a Blender project with an existing character body with a [standard R15 rig](/docs/avatar/character-bodies/specifications#standard-r15-rigs) , or import an appropriate character model .fbx  using File  > Import  > FBX (.fbx) .

2.

For easier visualization, hide non-rendered mesh objects, such as armature, cages, and attachments to better preview the reference animations.

3.

Set which rig you want to test a reference animation on:

1.

In the add-on's Armature  field, select the Eyedropper.

2.

In the Outliner, select the Armature  object that contains your character's rig data.

4.

Click on an animation cycle to preview, such as Walk , Run , Move  or Idle .

5.

Press Stop Animation  to clear animation data.

6.

If you notice any unexpected skinning deformations, pause on the frame and switch to Weight Paint mode  or use Blender's other skinning tools to resolve. See [Skin a humanoid model](/docs/art/modeling/skin-a-humanoid-model)  for additional instruction.

### [Test accessory attachments](#test-accessory-attachments)[](#test-accessory-attachments)

You can add reference attachments to your character body model using the Attach Test Accessory  buttons. These test accessories help preview how rigid accessories attach to your character and how they can move with your model. The tool includes two sets of rigid accessories to apply to your character.

![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/calisthenic-tool/Normal-Reference.png) Normal Size  - Loads normal accessory references.

![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/calisthenic-tool/Slender-Reference.png) Slender Size  - Loads slender accessory references.

To test accessories:

1.

Use the following Attach Test Accessory  buttons to add or remove sample accessories to your character's attachment points:

-

Normal Size  - Adds normal scale test accessories.

-

Slender Size  - Adds slender scale test accessories.

-

Detach Test Accessories  - Removes any test accessories from your character.

2.

If an accessory is not attaching at an expected location, reposition the associated Attachment object  in your character's rigging armature.

### [Export models](#export-models)[](#export-models)

When you are ready to export your model, you can export your character body directly through the Calisthenics Tool. The tool automatically clears any of the test data and applies appropriate export settings.

Using this tool to export models with [facial animations](/docs/avatar/dynamic-heads)  may result in unexpected behavior because the stored FACS data can conflict with the tool's reference animations.

To export from the Calisthenics Tool:

1.

In the Export Path  field, set the export directory by clicking the folder icon and browsing to the appropriate file directory.

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/calisthenic-tool/Exporting-Model.png)

2.

Click the Export Model  button. The character model .fbx  populates in the designated folder as Character_Model_Export.fbx .

If you are manually exporting your model with Blender's .fbx  importer instead of the Calisthenics Tool, ensure the following before export:

-

Detach the Calisthenics Tool's test accessories.

-

Use the Stop Animation  button to clear test animations from the timeline.

-

Return the model to the default pose with no additional pose data.

-

Verify your settings follow Roblox's [Blender export settings](/docs/art/modeling/export-requirements) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
