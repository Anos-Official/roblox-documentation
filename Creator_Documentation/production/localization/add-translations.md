<!-- Source: https://create.roblox.com/docs/en-us/production/localization/add-translations -->

Add translations | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/production/localization/add-translations.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. Localization
6. /
7. Manual translations

# Add translations

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/production/localization/add-translations.md)

You can add translations to source entries on your game's localization table using the [translator portal](#in-translator-portal)  or [with a .csv  file upload](#with-file-upload) .

In some cases, strings may require real-time translation during gameplay, such as a timer, using units of measurement, or when displaying player names. You can add translation parameters to the localization table as placeholders for this type of content. See [Translate dynamic content](/docs/en-us/production/localization/translate-dynamic-content)  for implementation details.

### [In Translator Portal](#in-translator-portal)[](#in-translator-portal)

Your game's [Translator Portal](/docs/en-us/production/localization#localization-settings)  provides a direct way to provide translations for the collected strings. Users added as translators for your game can access the Translator Portal.

#### [Add string translations](#add-string-translations)[](#add-string-translations)

To translate text through the localization page:

1.

In the localization settings page, click the Translate  button on the top right.

2.

In the Target Languages  menu on the left, select the target language you want to add a translation to.

3.

Select the Strings  tab at the top of the page.

4.

In the Strings column, select the string you intend to translate.

5.

In the Text to translate  field, input the desired translation and click Save .

 ![](https://prod.docsiteassets.roblox.com/assets/localization/Portal-Adding-String.png)

You cannot make edits to an existing source's ** Key** , ** Context**  or ** Example**  fields through the localization settings page. To add or edit a source's ** Key** , ** Context,**  or ** Example**  fields, you can remove and re-add the entry on the Localization page with these fields included, or make the edits directly with [file upload](#with-file-upload) .

#### [Add locale-specific translations](#add-locale-specific-translations)[](#add-locale-specific-translations)

Some languages may have regional differences in terms or spelling, such as "soccer" and "football". These are considered locales within languages. Currently, Roblox supports adding translations for the following locales:

| Locale Name | | Locale ID |
| --- | --- |
| English (United States) | | en-us |
| English (United Kingdom) | | en-gb |
| French (France) | | fr-fr |
| French (Canada) | | fr-ca |
| Portuguese (Brazil) | | pt-br |
| Portuguese (Portugal) | | pt-pt |
| Spanish (Spain) | | es-es |
| Spanish (Mexico) | | es-mx |

For languages that have Roblox-supported locales, you'll see subheadings under the parent language for global and locale-specific translations.

 ![](https://prod.docsiteassets.roblox.com/assets/localization/Locale-Left-Nav.png)

Add translations that are universal for that language (not specific to a locale) to the "Global" section, and add locale-specific translations to the corresponding sections. If a locale-specific translation is present, it overrides what is in the "Global" section for users in that locale.

 ![](https://prod.docsiteassets.roblox.com/assets/localization/Locale-Translation.png)

You can also add locale-specific translations for your game source language if they are supported.

 ![](https://prod.docsiteassets.roblox.com/assets/localization/Locale-Source.png)

If the source language of your game is English, French, Portuguese, or Spanish, locale-specific translation overrides for game names and descriptions are not currently available for these locales:

-

English (United States)

-

French (France)

-

Portuguese (Brazil)

-

Spanish (Spain)

#### [Add game information translations](#add-game-information-translations)[](#add-game-information-translations)

You can modify game information, such as the name, description, icon, and thumbnails, by updating the localization table:

1.

In the localization settings page, click the Translate  button on the top right.

2.

In the Target Languages  menu on the left, select the target language you want to add a translation to.

3.

Select the Information  tab at the top of the page.

1.

For Name and Description fields, input the desired translation and click Save . Note that if you save an empty string here, it will be saved as a manual edit signaling that the text should not be translated. In this case, users in the target language will see the source string.

 ![](https://prod.docsiteassets.roblox.com/assets/localization/Portal-Adding-Information.png)

2.

For Icon and Thumbnails, use the Upload or Remove buttons to modify your localized images. You can upload up to 10 thumbnails per game. When complete, click Save .

 ![](https://prod.docsiteassets.roblox.com/assets/localization/Portal-Adding-Information-Thumbnail.png)

#### [Add game product translations](#add-game-product-translations)[](#add-game-product-translations)

You can modify game product details, such as developer [products](/docs/en-us/production/monetization/developer-products) , [passes](/docs/en-us/production/monetization/passes) , and [badges](/docs/en-us/production/publishing/badges) :

1.

In the localization settings page, click the Translate  button on the top right.

2.

In the Target Languages  menu on the left, select the target language you want to add a translation to.

3.

Select the Products  tab at the top of the page.

4.

Input the desired translations for your game product and click Save .

 ![](https://prod.docsiteassets.roblox.com/assets/localization/Portal-Adding-Product.png)

### [With file upload](#with-file-upload)[](#with-file-upload)

Using Studio or Creator Hub, you can download, modify, and re-upload your localization table as a .csv  spreadsheet. This is helpful when editing several translations at a time or when collaborating with translators outside of Roblox.

Using the file upload process, you can only modify in-game string entries and translations. Unlike editing translations through your [Translator Portal](#in-translator-portal) , modifying the .csv  allows you to edit the additional Key , Context , and Example  fields.

When modifying or adding translations with file upload, the following behavior applies to brand new or existing entries:

| Does the entry already exist in the Cloud Localization Table? | | Changes made to CSV | | Expected behavior on upload |
| No | | Source string row added with one or more translations | | Entry is added, any translations present are added as a manual translation entry. Any translations missing for supported languages are eligible for [automatic translation](/docs/en-us/production/localization/automatic-translations) . |
| No | | Source string row added without translations | | Entry is added and is eligible for [automatic translation](/docs/en-us/production/localization/automatic-translations) . |
| Yes | | Translation added or modified. | | If the translation is different than the one in the existing Cloud Localization Table, translation updates to the one in the .csv  file.
If the original translation was automatically generated, the new translation is added and locked as a manual translation. You can regenerate automatic translation for this entry by [unlocking the entry in Translator Portal.](/docs/en-us/production/localization/automatic-translations#automatic-translation-updates) |
| Yes | | Translation entry for a source string removed. | | Translation is deleted and locked as a manual translation. You can regenerate automatic translation for this entry by [unlocking the entry in Translator Portal](/docs/en-us/production/localization/automatic-translations#automatic-translation-updates) . |
| Yes | | Source string removed | | No change - entry will not be deleted.
To delete an entry through .csv , either:
 — In Creator Hub, use Delete Table  and then Upload CSV .
 — In Studio, use Advanced  ⟩ Replace  in the Cloud Localization Table section. |

To begin adding a new supported language, you need to manually add the country code as a new column in the spreadsheet. See [Language Codes](/docs/en-us/production/localization/language-codes)  for a list of supported languages and country codes.

Ensure your spreadsheet meets the following requirements to prevent uploading or processing issues:

-

Max total entries: 10,000

-

Max .csv  file size: 2 MB

-

Max number of modified or added entries per .csv  upload: 1,000

#### [With Creator Hub](#with-creator-hub)[](#with-creator-hub)

To translate text using the .csv  in Creator Hub:

1.

In the Creator Hub, navigate to your game settings page.

2.

Navigate to Localization  and switch to the Table Management  tab.

3.

Select Download CSV  to save the .csv  file locally.

4.

Open the .csv  in your preferred spreadsheet editor.

5.

Add translations on the same row as the source text, under the column with the specific country code you are localizing to. Save when finished.

6.

Select Upload CSV  and upload the updated .csv .

7.

Click Confirm  on the prompt to save the new entries to the cloud localization table.

#### [With Studio](#with-studio)[](#with-studio)

To translate text using the .csv  through Studio:

1.

In Studio, open Localization Tools  from the Window  ⟩ Localization  menu.

2.

In the Cloud Localization Table  section, select Download  to save the .csv .

3.

Open the .csv  in your preferred spreadsheet editor.

4.

Add translations on the same row as the source text, under the column with the specific country code you are localizing to. Save  when finished.

5.

In the Cloud Localization Table  section, select Update  and upload the updated .csv .

6.

Click Confirm  on the prompt to save the new entries to the cloud localization table.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
