<!-- Source: https://create.roblox.com/docs/en-us/art/accessories/creating/armature-setup -->

Armature setup | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/art/accessories/creating/armature-setup.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Tutorials](/docs/en-us/tutorials)

# Armature setup

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/art/accessories/creating/armature-setup.md)

Rigging  is the process that enables the clothing object to move and deform with a Roblox character's rigging armature. In this tutorial, you'll parent the t-shirt to Roblox's provided [standard R15 rig](/docs/en-us/avatar/character-bodies/specifications#standard-r15-rigs)  and verify the Automatic Skinning Transfer data. After rigging, be sure to test out some basic poses to ensure that your clothes move and stretch correctly with any character body.

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/Texturing-Complete.png) Clothing mesh with no rigging data

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/Rigging-Pose-Tests.png) Clothing mesh with rigging data performing pose tests

The next two rigging sections cover the following processes:

1.

Downloading and appending a standard R15 armature to your project.

2.

Parenting the rig with Blender's automatic weights.

3.

Testing poses.

## [Transfer armature](#transfer-armature)[](#transfer-armature)

Roblox provides base rigging armatures that you can import into your own project. While it is possible to create your own rigs, importing a premade rig with the proper configuration saves you time and reduces the potential for error.

To import a standard R15 rig into your file:

1.

Download Roblox's [Rig_and_Attachments_Template.blend](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Rig_and_Attachments_Templates.zip) , but do not open this project.

2.

In your current clothing project, return to Object  mode.

3.

Navigate to File  > Append , and select the saved Rig_And_Attachments_Template.blend  file. An additional folder structure appears.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/Rigging-Append-Browser.png)

4.

Select Armature  > Armature  and press Append . An armature object is added to your workspace.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/Rigging-Armature-Appended.png)

5.

Reorient the armature:

1.

With the armature active, open the Item tool  sidebar.

2.

Adjust the rotation so the armature is correctly aligned with your mesh.

3.

After alignment, navigate to Object  > Apply  > All Transforms  to freeze your new rotation values.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/Rigging-Freeze-Transforms.png)

## [Parent armature](#parent-armature)[](#parent-armature)

With the armature rig in place, you can use Blender's Parent with Automatic Weights  functionality to quickly set your t-shirt mesh as a child of the armature. This feature also applies vertex weighting, or skinning , automatically to your mesh, which can save you significant time over skinning your clothing manually.

To parent the t-shirt to the rig:

1.

Select LongSleeve , then hold Shift  and click the Armature  object. Ensure that the armature object is the last object selected.

2.

Right-click in the viewport, then select Parent  > With Automatic Weights  from the contextual menu.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/Rigging-Auto-Weights.png)

[Next](/docs/en-us/art/accessories/creating/test-poses)[Previous](/docs/en-us/art/accessories/creating/texture-painting)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
