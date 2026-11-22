<!-- Source: https://create.roblox.com/docs/en-us/production/localization/manual-translations -->

Manual translations | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/production/localization/manual-translations.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. Localization
6. /
7. Manual translations

# Manual translations

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/production/localization/manual-translations.md)

When localizing your content, you might need to manually modify your localization table to improve translation quality, add context for when a translation should be used, or even remove unused translation entries.

Whether you have translation entries automatically captured or manually added, all the translation entries are saved to the [cloud localization table](#cloud-localization-table) . To modify the localization table, you can perform the following actions:

-

[Add source content](/docs/en-us/production/localization/add-source-content)  to the table, either manually or automatically.

-

[Remove content](/docs/en-us/production/localization/remove-content)  from the table, such as usernames or other strings that shouldn't be translated.

-

[Add translations](/docs/en-us/production/localization/add-translations)  to entries in the table for any supported languages set in your game.

Before making any changes to your table, it's important to understand each field in the [cloud localization table](#cloud-localization-table)  to prevent issues or conflicts.

Users with Automatic Translations enabled in their Roblox account settings will still see all manually added translations in your game. See [User-facing setting](/docs/en-us/production/localization#user-facing-setting)  for more information.

## [Cloud localization table](#cloud-localization-table)[](#cloud-localization-table)

The localization table is the reference for all translations within your game. It's important to understand each field of the localization table to effectively add or modify entries.

When populated, the table contains all user-facing content within your game that requires translation along with any available translations for specific languages. You can [add source content](/docs/en-us/production/localization/add-source-content)  and [add translations](/docs/en-us/production/localization/add-translations)  to the Cloud Localization Table or [download and upload a .csv  version of your table](/docs/en-us/production/localization/add-translations#with-file-upload) . Only users who have edit permission for a game can access a game's localization table.

The localization table has the following columns:

| Column | | Description |
| --- | --- |
| Source | | A required field containing the in-game source text strings gathered by automatic text capture or manual entry. This is the source text that you intend to translate to other languages. Source text is required before you can add a translation and multiple entries can share the same Source, as long as they have unique Context  fields.

If you are translating dynamic content, such as partial strings, the Source field must follow one of the supported parameter formats described in [Translate dynamic content](/docs/en-us/production/localization/translate-dynamic-content) .  |
| Context | |

An optional field containing a reference to the in-game object containing the source text. You can use the Context field to specify which translation Roblox displays on an object. See [Using Context Overrides](/docs/en-us/production/localization/localize-with-scripting#use-context-overrides)  for more details.

 The Automatic Text Capture system does not auto-fill the Context field and instead populates the Location  field with similar information.

 |
| Example | | An optional field containing any additional information about an entry you may want to include as notes for translators. You can use this field to show manual translators where and when your game uses a specific translation. |
| Key | |

An optional field for implementing [key-based lookup](/docs/en-us/reference/engine/classes/Translator#FormatByKey)  when using localization APIs. You can leave this field empty if you are not using [localization APIs](/docs/en-us/production/localization/localize-with-scripting)  for specific tasks, such as localizing images and sounds.

 |
| Location | |

A field that is auto-filled by the [Automatic Text Capture](#automatic-text-capture)  system. It contains a reference to the in-game object containing the source text which can help you or a translator identify where the string is being encountered in your game. This field is either blank or populated by the Automatic Text Capture System. To manually add your own object reference, use the Context  field.

 |

Some fields in the localization table must be unique to avoid unexpected behavior. Keep in mind the following:

-

For all entries, the Source  field must not be empty.

-

No two entries can share the same Source and Context  values.

-

No two entries can share the same Key .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
