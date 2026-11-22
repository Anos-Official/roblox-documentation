<!-- Source: https://create.roblox.com/docs/en-us/production/localization/image-translations -->

Image translations | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/production/localization/image-translations.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. Localization
6. /
7. Automatic translation

# Image translations

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/production/localization/image-translations.md)

Image translation is currently in beta. Functionality and availability are subject to change.

Image translation  automatically translates images containing text in your game, matching the style of the original text as closely as possible. This lets you localize signs, UI graphics, and other text-in-image content without manually creating a version for every supported language.

## [How image translation works](#how-image-translation-works)[](#how-image-translation-works)

Roblox's image translation system is trained to match the font size, style, and color of the original text as closely as possible in the translated image. Any non-text elements in the image remain exactly the same.

For example, the following signs keep their original color, font style, and layout in both the source and translated image:

![](https://prod.docsiteassets.roblox.com/assets/localization/Image-Translation-Example-Cash-English.png) English (Source)

![](https://prod.docsiteassets.roblox.com/assets/localization/Image-Translation-Example-Cash-Korean.png) Korean

![](https://prod.docsiteassets.roblox.com/assets/localization/Image-Translation-Example-Ice-Cream-English.png) English (Source)

![](https://prod.docsiteassets.roblox.com/assets/localization/Image-Translation-Example-Ice-Cream-Spanish.png) Spanish

We don't yet support all languages for image translation. Only the following languages are currently supported:

-

French

-

German

-

Indonesian

-

Italian

-

Korean

-

Portuguese

-

Spanish

Automatic image translation is not turned on by default. You can enable it in your experience's localization settings in Creator Hub, as described in the following section.

## [Enable automatic image translation](#enable-automatic-image-translation)[](#enable-automatic-image-translation)

To start translating images in your game, enable the following three settings in your experience's localization settings.

1.

Navigate to the Languages  tab and enable image translation for each language you want to support.

 ![The Localization Languages section showing the option to turn on auto translation for experience images for a language.](https://prod.docsiteassets.roblox.com/assets/localization/Image-Translation-Enable-Per-Language.png)

2.

Navigate to the Settings  tab and enable Automatic Image Capture . This allows Roblox to automatically detect which images in your game contain text and need to be translated.

Once enabled, Roblox adds eligible images to your localization table when players encounter them in your game. Image translation isn't immediate — it can take up to a few days for images to be captured and for translations to be generated.

 ![The Localization Settings section highlighting the Automatic Image Capture toggle.](https://prod.docsiteassets.roblox.com/assets/localization/Image-Translation-Automatic-Image-Capture.png)

3.

In the Settings  tab, enable Use Translated Content  for images to show translated images to players live. If you want to preview translated images in Creator Hub before players see them, leave this setting off until you've reviewed the translations and are ready for them to be displayed.

 ![The Localization Settings section highlighting the Enable translated image in experience toggle.](https://prod.docsiteassets.roblox.com/assets/localization/Image-Translation-Use-Translated-Content.png)

## [Manage translated images](#manage-translated-images)[](#manage-translated-images)

Images that have been added to your localization table appear in the Images  tab of the Translation page. To get there, navigate to your game's localization page and select Translate .

 ![The Localization Languages section highlighting the Translate button.](https://prod.docsiteassets.roblox.com/assets/localization/Image-Translation-Translate-Button.png)

Select the Images  tab to see a side-by-side comparison of the source and translated image for each entry in your localization table.

 ![The Translation page Images tab showing a side-by-side comparison of a source image and its translated image.](https://prod.docsiteassets.roblox.com/assets/localization/Image-Translation-Images-Tab.png)

If there's a translation you don't like, you can disable it by turning off the [AutoLocalize](/docs/en-us/reference/engine/classes/GuiBase2d#AutoLocalize)  property for that image in Studio. You can also leave feedback on a translation you don't like by clicking the icon at the bottom right of the translated image.

 ![The Translation page Images tab highlighting the feedback icon in the bottom right of a translated image.](https://prod.docsiteassets.roblox.com/assets/localization/Image-Translation-Feedback-Icon.png)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
