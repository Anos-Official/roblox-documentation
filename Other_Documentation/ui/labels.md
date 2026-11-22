<!-- Source: https://create.roblox.com/docs/ui/labels -->

Text & image labels | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/ui/labels.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [User interface](/docs/ui)
6. /
7. UI objects

# Text & image labels

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/ui/labels.md)

Labels  are [GuiObjects](/docs/reference/engine/classes/GuiObject)  that let you display customizable text and images [on‑screen](/docs/ui/on-screen-containers)  or [in-game](/docs/ui/in-experience-containers) . There are two types of labels:

-

A [TextLabel](/docs/reference/engine/classes/TextLabel)  is a rectangle with text that you can style through customizable properties. This is the primary way to display text in a game.

-

An [ImageLabel](/docs/reference/engine/classes/ImageLabel)  is a rectangle with an image [asset](/docs/projects/assets)  that you can style through customizable properties. Alongside [textures and decals](/docs/parts/textures-decals) , this lets you display images in a game.

## [Create labels on the screen](#create-labels-on-the-screen)[](#create-labels-on-the-screen)

Labels on a screen are useful for things like displaying images of characters with dialog.

To add a label to a screen:

1.

In the Explorer  window, select StarterGui  and add a ScreenGui .

1.

Hover over StarterGui and click the ⊕ button. A contextual menu displays.

2.

From the menu, insert a ScreenGui .

2.

Select the new ScreenGui  and add a label.

1.

Hover over ScreenGui  and click the ⊕ button. A contextual menu displays.

2.

From the menu, insert a TextLabel  or ImageLabel .

 ![](https://prod.docsiteassets.roblox.com/assets/ui/button-text-input/ImageButton-Screen-New.jpg)

## [Create labels on part faces](#create-labels-on-part-faces)[](#create-labels-on-part-faces)

Labels on a part are useful for things like creating billboards, posters, and wallpaper.

To add a label to the face of a part:

1.

In the Explorer  window, insert a SurfaceGui  onto the part.

1.

Hover over the part instance and click the ⊕ button. A contextual menu displays.

2.

From the menu, insert a SurfaceGui .

2.

Select the new SurfaceGui  and add a label.

1.

Hover over the SurfaceGui  and click the ⊕ button. A contextual menu displays.

2.

From the menu, insert a TextLabel  or ImageLabel .

 ![](https://prod.docsiteassets.roblox.com/assets/ui/button-text-input/ImageButton-SurfaceGui-New.jpg)

If you don't see the button, try [choosing a different face](/docs/parts/textures-decals#choose-a-face)  in the ** Face**  property of the ** SurfaceGui** .

## [Adjust ImageLabel properties](#adjust-imagelabel-properties)[](#adjust-imagelabel-properties)

All images within an [ImageLabel](/docs/reference/engine/classes/ImageLabel)  must be assets that have been [imported](/docs/projects/assets/manager#asset-import)  to Studio. While the image automatically scales to fit the area of the rectangle, the image looks best when it displays at its native resolution.

You can customize the visual appearance of an image with the following properties:

-

[ImageColor3](/docs/reference/engine/classes/ImageLabel#ImageColor3)

-

[ImageTransparency](/docs/reference/engine/classes/ImageLabel#ImageTransparency)

-

[BackgroundTransparency](/docs/reference/engine/classes/GuiObject#BackgroundTransparency)

For example, to display only the image and hide the rectangle, set the [BackgroundTransparency](/docs/reference/engine/classes/GuiObject#BackgroundTransparency)  property to 1 .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
