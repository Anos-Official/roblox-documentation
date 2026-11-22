<!-- Source: https://create.roblox.com/docs/art/characters/creating/verify-attachments -->

Verify attachment placement | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/art/characters/creating/verify-attachments.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Tutorials](/docs/en-us/tutorials)

# Verify attachment placement

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/art/characters/creating/verify-attachments.md)

Attachment points are non-rendered objects of your avatar where rigid accessories attach to. Each template includes the required attachments at their expected locations ending with _Att . Before exporting, it's important to verify the attachment position and, if necessary, adjust the location if you made any changes to the shape of your model.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Pre-Attachment.png)  Original template attachment positions

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Post-Attachment.png) Attachments after adjustment

Center attachment points at their respective locations. Each attachment should overlap approximately halfway with the character's mesh.

This tutorial only changes the head of your model, so you only need to adjust the Hat , Hair  and FaceFront  attachments. To enable visibility and verify your head attachment point:

1.

If you haven't already, enable [disabled objects](/docs/art/characters/creating#disabled-objects)  in your Outliner.

2.

In the Outliner, find the Joints  parent object.

3.

Hold Shift  and click the Hide  icon for the Joints  object to hide everything.

4.

Expand the Joints  object's hierarchy and unhide Head_Geo , Hat_Att , Hair_Att , and FaceFront_Att .

1.

If required, disable Disable In Viewport  ![](https://prod.docsiteassets.roblox.com/assets/art/blender-ui/Disabled-Icon.png)  next to the _Att objects.

5.

In the viewport, verify the placement of the attachments. The goblin's head is shorter than the starting template, so the attachments require minor vertical adjustment.

6.

Select the attachments, then switch to Edit  mode.

7.

Using the Grab  tool, position the attachments vertically along the y-axis until they are about halfway embedded in the head.

[Next](/docs/art/characters/creating/final-checks)[Previous](/docs/art/characters/creating/remove-extra-bones)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
