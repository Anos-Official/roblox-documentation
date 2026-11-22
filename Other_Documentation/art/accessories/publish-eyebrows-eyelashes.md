<!-- Source: https://create.roblox.com/docs/art/accessories/publish-eyebrows-eyelashes -->

Publish bodies with eyelashes and eyebrows | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/art/accessories/publish-eyebrows-eyelashes.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Tutorials](/docs/en-us/tutorials)
4. /
5. Avatar items

# Publish bodies with eyelashes and eyebrows

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/art/accessories/publish-eyebrows-eyelashes.md)

Eyelashes and eyebrows are cosmetics that can help emphasize facial features and create a unique way of customizing a character. Similar to clothing, eyelashes and eyebrows are [3D layered accessories](/docs/avatar/layered-accessories)  that can stretch and fit over different face shapes and can deform and stretch with character face animations.

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Nature-Girl-No-Accessories.png) Character body without eyelashes and eyebrows

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Nature-Girl-With-Face-Accessories.png) Character body with eyelashes and eyebrows

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Eyebrows-Eyelashes-Only.png) Standalone eyelashes and eyebrows

When publishing eyelashes and eyebrows, you must parent these [Accessory](/docs/reference/engine/classes/Accessory)  objects under the avatar character's [Model](/docs/reference/engine/classes/Model)  prior to uploading the character Model  to the Marketplace. These Accessory  face objects must adhere to Roblox's accessory requirements and include layered components such as caging, rigging, and skinning components. For an overview on creating your own eyelashes and eyebrows, see [Create face accessories](/docs/art/characters/facial-animation/create-face-accessories) . Eyebrows and eyelashes must use [Automatic Skinning Transfer](/docs/avatar/automatic-skinning-transfer)  with the RBX_Leader  and RBX_Follower  special joints to be published on the marketplace.

At this time, you can only bundle eyelashes , eyebrows , and hair  with your body on Marketplace upload. Other facial accessories, such as horns, makeup, glitter, or other cosmetics are not acceptable. See [Marketplace policy](/docs/marketplace/marketplace-policy)  for specific information on allowable cosmetics and other policy regulations and guidelines.

## [Configure eyelash and eyebrow accessories](#configure-eyelash-and-eyebrow-accessories)[](#configure-eyelash-and-eyebrow-accessories)

Use the following steps to import your face accessory and body assets into Studio. After converting the eyelashes and eyebrows to Accessory  objects, parent the Accessory  objects within the character Model  before uploading the character to the Marketplace.

You can download reference .fbx  models of [eyelashes](https://prod.docsiteassets.roblox.com/assets/art/reference-files/Eyelashes.fbx) , [eyebrows](https://prod.docsiteassets.roblox.com/assets/art/reference-files/Eyebrows.fbx) , and an [avatar body](https://prod.docsiteassets.roblox.com/assets/art/reference-files/AnimeFemale-Studio-Ready.fbx)  to follow along this process.

1.

In the [Importer](/docs/studio/importer) , import the .fbx  files of your face accessory and body. The eyelashes, eyebrows, and body each populate in your Workspace as a Model .

1.

If you are using the reference body, set Rig General  > Rig Type  to Rthro .

2.

Use the [Accessory Fitting Tool](/docs/avatar/accessory-fitting-tool)  and select the Eyelash  or Eyebrow  model and click Next .

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/AFT-Eyebrows-Example.png)

3.

Select the appropriate Accessory  > Eyelash  or Accessory  > Eyebrow  asset type and click Next .

4.

OPTIONAL

 Preview the fit of your face accessory.

1.

If the face accessory was modeled on a specific character body, you may want to import that character body into Studio and use it as a mannequin in the fitting tool's preview. See [Accessory Fitting Tool](/docs/avatar/accessory-fitting-tool)  for more information on adding custom characters.

2.

If using the provided reference body, you can continue to step 5.

5.

Click Generate MeshPart Accessory  to create your MeshPart.

6.

Repeat steps 2-5  for the other face accessory.

7.

In the Outliner, drag and drop  the face Accessory  objects within the character Model  instance. The accessories automatically equip and attach to the correct areas of your avatar character.

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Anime-Girl-Eyebrows-Example.png) Workspace preview of body with face accessories

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Face-Accessory-Hierarchy.png) Outliner hierarchy

8.

If required, rename the accessory objects to EyelashAccessory  or EyebrowAccessory  accordingly.

9.

Once you are ready to upload the avatar model with your face accessories, see [Upload an asset](/docs/marketplace/publish-to-marketplace#upload-an-asset)  for instructions on uploading and publishing your avatar body with eyelashes and eyebrows to the Marketplace.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
