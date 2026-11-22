<!-- Source: https://create.roblox.com/docs/en-us/production/localization/add-source-content -->

Add source content | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/production/localization/add-source-content.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. Localization
6. /
7. Manual translations

# Add source content

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/production/localization/add-source-content.md)

You must add source text to translate to the game's localization table before you or any collaborators add translations. You can use [Automatic Text Capture](#automatic-text-capture)  to collect text strings automatically as your game is played by users or [manually add text sources](#manually-add-source-content) .

See [Localizing images and sounds](/docs/en-us/production/localization/localize-with-scripting#localize-images-and-sounds)  for instructions on localizing non-text content.

## [Automatic Text Capture](#automatic-text-capture)[](#automatic-text-capture)

The Automatic Text Capture (ATC)  tool collects text strings that users encounter in your game through GUI objects, such as [TextLabels](/docs/en-us/reference/engine/classes/TextLabel)  or [BillboardGui](/docs/en-us/reference/engine/classes/BillboardGui)  and is usually the fastest way to collect translatable text from your game. In many cases, the Automatic Text Capture tool is already enabled for [automatic translations](/docs/en-us/production/localization/automatic-translations#enable-automatic-text-capture) .

## [Manually add source content](#manually-add-source-content)[](#manually-add-source-content)

You can also add content manually. This is recommended if your game contains text that doesn't appear during typical gameplay, like a complex conversation tree, which may take longer to collect via ATC. You can add entries to the table [in the localization page](#add-sources-with-localization-settings)  or [with a .csv  file upload](#add-sources-with-file-upload) . It is recommended to use the .csv  upload if you want to specify an entry's Key, Context, or Example fields.

Entries in the localization table are case-sensitive.

For example, when using "hello" as a source value on the localization table, Roblox does not apply translations for "Hello" or "HELLO".

You can manually add image and sound asset IDs to the localization table with a .csv  upload. For more information see [Localize images and sounds](/docs/en-us/production/localization/localize-with-scripting#localize-images-and-sounds) .

### [Add sources with localization settings](#add-sources-with-localization-settings)[](#add-sources-with-localization-settings)

You can add source content in the [localization page](/docs/en-us/production/localization#localization-settings) . This is ideal for making quick additions to your localization table.

To add source content through the localization page:

1.

In your game's localization page, click the Translate  button on the top right.

 ![](https://prod.docsiteassets.roblox.com/assets/localization/Portal-Translate.png)

2.

Select the Strings  tab.

3.

Click Add Entry .

4.

In the Text to translate  field, input the source text and click Save .

 ![](https://prod.docsiteassets.roblox.com/assets/localization/Portal-Add-Source-String.png)

5.

If you are using key-based scripting to translate a string, input the key name in the Key  field.

6.

If the string has multiple meanings, such as a character's back and a back button, input the full path of the specific text object in the Context  field.

7.

Click Save .

### [Add sources with file upload](#add-sources-with-file-upload)[](#add-sources-with-file-upload)

You can add source content to your localization table with a .csv  upload. You can use this option when making large numbers of updates to your localization table.

To add source content through the .csv  upload:

1.

In Studio, open Localization Tools  from the Window  ⟩ Localization

2.

In the Cloud Localization Table  section, select Download  to save the .csv .

3.

Open the .csv  in your preferred spreadsheet editor.

4.

Under the Source  column, add source text and save. You can leave the other columns blank.

| Key | | Context  | | Example | | Source |
| --- | --- |
|  | |  | |  | | Options |
|  | |  | |  | | Start |

5.

In Studio, in the Cloud Localization Table  section, select Update  and upload the new .csv  file.

6.

Click Confirm  on the Confirm Upload  prompt to save the new entry to the cloud localization table.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
