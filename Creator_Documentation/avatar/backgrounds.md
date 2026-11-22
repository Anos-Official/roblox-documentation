<!-- Source: https://create.roblox.com/docs/en-us/avatar/backgrounds -->

Backgrounds | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar/backgrounds.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. Backgrounds

# Backgrounds

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar/backgrounds/index.md)

Backgrounds  for avatars are 2D assets that display behind an avatar on different surfaces throughout Roblox. When users purchase backgrounds on the [Marketplace](https://www.roblox.com/catalog) , they can immediately equip them so that the backgrounds are visible on their web profile and in the 3D avatar viewer.

You can create a background using any 2D editing software, such as [Procreate](https://procreate.com/)  or [GNU Image Manipulation Program](https://www.gimp.org/)  (GIMP). After you verify that the image meets Roblox's [technical background specifications](/docs/en-us/avatar/backgrounds/specifications)  that guarantee your backgrounds behave consistently in the 3D viewer and web profiles, you can upload the image in the [Creator Hub](https://create.roblox.com/dashboard/creations)  to process it into an avatar asset that's ready to be sold on the Marketplace.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/backgrounds/Backgrounds-Examples.png)

## [How a background displays](#how-a-background-displays)[](#how-a-background-displays)

Backgrounds display differently depending on if a user is looking at the background from the 3D viewer or a profile page. While the following subsections detail the differences between these two views, it's important to optimize your image for the 3D viewer because backgrounds that work well for the 3D space still display correctly as a flat image on profile pages.

### [3D viewer](#3d-viewer)[](#3d-viewer)

Roblox projects the image onto a cyclorama , which is a curved plane behind an avatar. The curve hides the seam between the wall and the floor, in the same way a photo studio backdrop does. The avatar renders in 3D, standing in front of the cyclorama. As the camera moves, different parts of the image come into view.

To demonstrate this concept, review the following images of how a cat avatar displays as the camera moves closer to the cyclorama. When the camera is far away, the whole background is visible, but when the camera zooms in closer, only a small view of the background is visible.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/backgrounds/Cyclorama.png)  ![](https://prod.docsiteassets.roblox.com/assets/avatar/backgrounds/Cyclorama-2.png)

### [Profile pages](#profile-pages)[](#profile-pages)

The web profile page displays the image as a flat picture behind the avatar thumbnail. It has no 3D scene and no camera, so the image appears closer to the file you exported. The avatar thumbnail still covers the center of the frame, so keep important content in the safe area.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/backgrounds/Web-profile.png)

## [Template zones](#template-zones)[](#template-zones)

The 2D template for backgrounds has four zones and a horizon line. As you create backgrounds, it's important to review each zone and how it treats details so that your image is crisp and displays according to your creative vision.

| ** Zone** | | ** Where it sits** | | ** Guidance** |
| --- | --- |
| Transparent area | | Outer edge of the image | | Roblox applies an alpha fade in this region so the background blends into surrounding UI. Leave it free of important details, and export the image without a fade of your own. |
| Safe area | | Center of the image, including the horizon | | Put important content here. This region stays visible at every camera position, and the cyclorama curve preserves its shape. |
| Distortion area | | Foreground floor and the outer regions the curve bends | | Use ground texture and gradients. The cyclorama foreshortens this region, so detailed subjects lose their shape. |
| Avatar location | | Lower center | | The avatar stands here. Keep the floor under the avatar clear. |
| Horizon line | | Boundary between the floor and the far background | | Keep tall objects above this line, in the far background. |

![Background template with a faded transparent edge, a green safe area, red distortion areas, a horizon line, and the avatar at the lower center.](https://prod.docsiteassets.roblox.com/assets/avatar/backgrounds/Template-Zones.png)

In addition, consider the following best practice guidance:

-

Place tall elements, such as trees and buildings, in the far background.

-

Give the avatar a clear floor to stand on.

-

Keep important content in the center of the image, and keep foreground elements low in the composition.

-

Keep tall objects from crossing the horizon line.

## [Creation process](#creation-process)[](#creation-process)

To create a background for avatars:

1.

Review the previous [template zones](#template-zones)  as you decide on your design, and reference all [file specifications](/docs/en-us/avatar/backgrounds/specifications) .

2.

Create the image using your favorite 2D editing software, such as Procreate or GIMP.

3.

Export a flattened file in the sRGB color space that meets the specifications.

4.

[Upload](#upload-backgrounds)  the background in the Creator Hub.

5.

[Publish](#publish-backgrounds)  the background for others to purchase on the Marketplace.

## [Upload backgrounds](#upload-backgrounds)[](#upload-backgrounds)

To upload backgrounds, you must verify your account through your own [government ID](/docs/en-us/production/publishing/account-verification#verify-through-government-id)  or a linked [parental account](https://about.roblox.com/parental-controls)  with government ID verification, and have 200 Robux for the upload fee. There is an upload limit of 1 background per day.

To upload a background for avatars:

1.

In the left-hand navigation of the Creator Hub, navigate to Avatar items. The Avatar items  page displays.

2.

In the horizontal navigation, navigate to Backgrounds , then click the Create background  button. The page updates with new UI options.

3.

Click the Upload  button, then select your 2560 x 1440 image.

4.

Fill in the Name  and Description  fields.

5.

Click the Create  button, then accept the 200 Robux fee.

 ![Create background page with an image preview, name and description fields, a 200 Robux upload fee, and Create and Cancel buttons.](https://prod.docsiteassets.roblox.com/assets/avatar/backgrounds/Create-UI.png)

## [Publish backgrounds](#publish-backgrounds)[](#publish-backgrounds)

To publish backgrounds, you must have a [Roblox Plus](https://www.roblox.com/plus)  account, verify your account through your own [government ID](/docs/en-us/production/publishing/account-verification#verify-through-government-id)  or a linked [parental account](https://about.roblox.com/parental-controls)  with government ID verification, and have Robux for the publishing advance fee:

-

100 a unit for free Limited backgrounds

-

2000 for paid non-Limited backgrounds

-

15000 for paid Limited backgrounds

For commissions and the standard publishing flow, see [Marketplace fees and commissions](/docs/en-us/marketplace/marketplace-fees-and-commissions)  and [Publish to Marketplace - Publish an asset](/docs/en-us/marketplace/publish-to-marketplace#publish-an-asset) .

Backgrounds support standard publishing options, including [Limited items](/docs/en-us/marketplace/publish-to-marketplace#item-attributes) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
