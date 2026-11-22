<!-- Source: https://create.roblox.com/docs/en-us/marketplace/custom-thumbnails -->

Custom thumbnails | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/marketplace/custom-thumbnails.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. Marketplace

# Custom thumbnails

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/marketplace/custom-thumbnails.md)

Thumbnail images provide a preview of the 3D asset in the [Marketplace](https://www.roblox.com/catalog) , user inventories, and avatar editors. Before [uploading an asset to the Marketplace](/docs/en-us/marketplace/publish-to-marketplace) , you can create your own thumbnails to customize the exact look and feel of your item preview thumbnails. This step is optional, but can help ensure that the thumbnail accurately portrays your item.

![](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Thumbnail-Example-A.png)

The default thumbnail may not correctly represent your item.

![](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Thumbnail-Example-B.png)

A custom thumbnail can create a more accurate preview.

### [Create thumbnails](#create-thumbnails)[](#create-thumbnails)

You must create thumbnails before [publishing your asset on the Marketplace](/docs/en-us/marketplace/publish-to-marketplace) . You can quickly create these thumbnail configuration instances with the [Custom Thumbnail Tool](https://www.roblox.com/library/11628621048/UGC-Custom-Thumbnail-Tool) . Roblox stores custom thumbnail information in a child ThumbnailConfiguration  object that parents a CameraTarget  and CameraValue .

 ![](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Thumbnail-Configuration-Example.png)

To use the Custom Thumbnail Tool:

1.

Install the [Custom Thumbnail Tool plugin](https://www.roblox.com/library/11628621048/UGC-Custom-Thumbnail-Tool) . This may require restarting Studio.

2.

In the Explorer  window, select the [Accessory](/docs/en-us/reference/engine/classes/Accessory)  you intend to create a thumbnail for.

3.

With the [Accessory](/docs/en-us/reference/engine/classes/Accessory)  highlighted in the Explorer  window, navigate to the Plugins  tab and click the UGC Thumbnail Tool . The viewport display updates and centers on the selected accessory in the workspace.

4.

Adjust the viewport to center on your accessory. Use the following controls to help navigate the camera:

-

W  A  S  D  to pan the camera.

-

Hold right-click  to rotate the camera.

-

Hold middle-click  to pan the camera.

-

Hold Shift  for fine adjustment.

5.

When complete, click Accept  to generate the thumbnail configuration objects.

6.

You can preview the thumbnail by right-clicking the accessory in the Explorer  window and selecting Save To Roblox… . The Asset Configuration  window appears and displays the current thumbnail.

If your thumbnail does not look correct, repeat steps 2-5  to overwrite the existing thumbnail data.

Once you upload an asset, you can't modify or change an asset's thumbnail.

### [Troubleshooting thumbnails](#troubleshooting-thumbnails)[](#troubleshooting-thumbnails)

If your thumbnails don't look the way you expect, you might need to manually resolve these issues or attempt to use the Custom Thumbnail tool again. See the following for common issues and fixes:

| Issue | | Description |
| --- | --- |
| Incorrect Thumbnail Zoom | | The scale of the thumbnail depends on the Handle  size of the [Accessory](/docs/en-us/reference/engine/classes/Accessory) . For the best thumbnail, make sure your Handle  covers the entire item.
When changing the size of the Handle  object, adjust the Size  property instead of using the resize tool. The resize tool can cause other unintended changes to the item.
 You can resolve this issue by using the [Custom Thumbnail Tool](https://www.roblox.com/library/11628621048/UGC-Custom-Thumbnail-Tool) . |
| Backward Thumbnails | | When importing meshes, Studio may change the orientation of the custom model by 180°. To resolve this, you can rotate your mesh 180° in your third party modeling tool, such as Blender or Maya, and then re-import the 3D model into Studio.
Regardless of import orientation, Studio equips the [Accessory](/docs/en-us/reference/engine/classes/Accessory)  on a character with the same fit and attachment. |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
