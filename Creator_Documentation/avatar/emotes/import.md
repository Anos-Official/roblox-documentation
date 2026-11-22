<!-- Source: https://create.roblox.com/docs/en-us/avatar/emotes/import -->

Import emotes | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar/emotes/import.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. Animations
6. /
7. Emotes

# Import emotes

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar/emotes/import.md)

Studio's [Animation Editor](/docs/en-us/animation/editor)  lets you import animations into your projects. The following instructions detail how to import a .fbx  file with animation data into Studio, convert it into a CurveAnimation  object with an asset ID, then use that asset ID in [Animation](/docs/en-us/reference/engine/classes/Animation)  objects that you can use in your games, upload to the Marketplace, or share with other creators.

It's important to ensure your emote meets Roblox's [emote specifications](/docs/en-us/avatar/emotes/specifications)  to use or sell this asset as an avatar-ready emote, otherwise you can encounter errors at different points in the workflow.

## [Import into Studio](#import-into-studio)[](#import-into-studio)

To import your asset as an animation:

1.

If you don't already have a character body with a [standard R15 rig](/docs/en-us/avatar/character-bodies/specifications#standard-r15-rigs) , add one to your project in Studio.

1.

In the Avatar  tab, click the Character  button.

 ![Character button highlighted in Studio's toolbar.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Character.png)

2.

Set Rig Type  to R15 .

3.

Set Body Shape  to either Masculine  or Feminine .

4.

Select an avatar style from the provided options. An avatar character body with a standard rigging armature displays in the viewport.

2.

Open the Animation Editor.

1.

In the Avatar  tab, click the Clip Editor  button.

2.

Select the character with a standard rigging armature. The Animation Editor updates accordingly.

3.

In the Animation Editor , select ⋯  > Import  > From File  and select your .fbx  file. Your animation populates in the Animation Editor's timeline.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-emotes/Animation-Editor-Import.png)

## [Generate asset ID](#generate-asset-id)[](#generate-asset-id)

To generate an asset ID for your animation, you must first convert your animation data in the timeline into a CurveAnimation  object. When you save the CurveAnimation  object, Roblox creates a cloud-based asset ID to represent your emote.

The animation data for emotes must be a [CurveAnimation](/docs/en-us/reference/engine/classes/CurveAnimation)  object instead of a [KeyframeSequence](/docs/en-us/reference/engine/classes/KeyframeSequence)  object.

To convert an existing keyframe sequence to a CurveAnimation :

1.

In the Animation Editor , select the Curve Editor  button next to the timeline. A confirmation prompt displays.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-emotes/Animation-Editor-Curve-Animation-Icon.png)

2.

Press Confirm  to convert your keyframes into a CurveAnimation  clip.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-emotes/Animation-Editor-Curve-Prompt.png)

3.

Back in the Animation Editor , select the ⋯  > Publish to Roblox . The Asset Configuration  window displays.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-emotes/Animation-Editor-Publish.png)

4.

Add a title and description, then click the Save  button. The Asset Configuration  window updates with a copyable asset ID.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-emotes/Generate-Asset-ID-Success.png)

## [Create an Animation object](#create-an-animation-object)[](#create-an-animation-object)

To submit an emote to the Marketplace, you must submit an [Animation](/docs/en-us/reference/engine/classes/Animation)  object with the AnimationId  property set to the asset ID of your CurveAnimation  object.

![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-emotes/Animation-Explorer.png) Animation  object in the Explorer window.

![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-emotes/Animation-Properties.png) AnimationId  property in the Properties window.

To create an [Animation](/docs/en-us/reference/engine/classes/Animation)  object you can publish as an emote:

1.

In the Explorer  window, add a new Animation  object.

2.

In the Properties  window, add the asset ID of your emote animation.

## [Upload emote to Marketplace](#upload-emote-to-marketplace)[](#upload-emote-to-marketplace)

When you have an [Animation](/docs/en-us/reference/engine/classes/Animation)  object with your emote animation asset ID set, you can upload the emote to the Marketplace. This process requires an [upload fee](/docs/en-us/marketplace/marketplace-fees-and-commissions#upload-fees)  of 80 Robux .

1.

In the Explorer  window, right-click the Animation  object and select Save to Roblox . The Asset Configuration  window displays.

2.

Configure the following fields:

1.

Add a title and description.

2.

Set the Content Type  to Avatar Item .

3.

Set the Asset Category  to Emote .

3.

Click the Submit  button to upload your asset for moderation.

For more information on the upload and publishing process, see [Publish to Marketplace](/docs/en-us/marketplace/publish-to-marketplace#upload-an-asset) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
