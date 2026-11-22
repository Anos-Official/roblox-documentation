<!-- Source: https://create.roblox.com/docs/audio/assets -->

Audio assets | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/audio/assets.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Audio](/docs/audio)

# Audio assets

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/audio/assets.md)

You can [find](#find-audio)  a wide variety of free‑to‑use audio assets in the Creator Store, or you can [import](#import-audio)  audio assets that you're certain you have permission to use, such as audio that you make yourself. The [asset privacy](/docs/projects/assets/privacy)  system automatically ensures that the IDs of your imported audio can't be accessed by users without proper permissions.

## [Find audio](#find-audio)[](#find-audio)

The [Creator Store](/docs/production/creator-store)  tab of the [Toolbox](/docs/projects/assets/toolbox)  contains a wide variety of free-to-use audio assets made by Roblox and the Roblox community for creators to use within their games, including more than 100,000 professionally-produced sound effects and music tracks from top audio and music partners.

To find audio assets on the Creator Store:

1.

In the Toolbox , navigate to the Creator Store  tab, then use the category selector dropdown to select Audio .

 ![Audio section of Creator Store in Studio's Toolbox](https://prod.docsiteassets.roblox.com/assets/studio/toolbox/Creator-Store-Audio.png)

2.

Use the keyword search, quick filter options, and/or advanced filters to narrow down the results.

 ![Audio discovery options in Studio's Toolbox](https://prod.docsiteassets.roblox.com/assets/studio/toolbox/Creator-Store-Audio-Discovery.png)

3.

Right-click any audio asset, then select Copy Asset ID  to copy the asset ID to your clipboard. You can now paste this asset ID into a [AudioPlayer](/docs/reference/engine/classes/AudioPlayer)  object to [play the audio](/docs/audio/objects) .

If you click any audio asset, Studio inserts it as a new [Sound](/docs/reference/engine/classes/Sound)  instance into the Explorer  window. However, [Sound](/docs/reference/engine/classes/Sound)  objects don't have the same dynamic functionality as [AudioPlayer](/docs/reference/engine/classes/AudioPlayer)  objects.

## [Import audio](#import-audio)[](#import-audio)

You can import custom audio through the [Asset Manager](/docs/projects/assets/manager) , Creator Dashboard, and Open Cloud API as long as your audio meets the following requirements:

-

You have the legal rights to that audio asset.

-

It adheres to the [Community Rules](https://en.help.roblox.com/hc/articles/203313410)  and [Terms of Use](https://en.help.roblox.com/hc/articles/115004647846) .

-

It's a single track/stream in either .mp3 , .ogg , .wav  or .flac  format.

-

It's less than 20 MB in size and 7 minutes in duration.

-

Its sample rate is less than or equal to 48 kHz.

-

Its channels are set to mono or stereo 2.0, 3.0, or 5.1 surround.

If you're [ID verified](/docs/production/publishing/account-verification) , you can import 2,000 free audio assets per 30 days; if you're unverified, you can import 100 free audio assets per 30 days. If a daily import limit exists, it's removed and replaced with a simplified monthly limit.

Studio assigns each new audio asset a unique asset ID  that you can use within your games to [play the audio](/docs/audio/objects) .

Asset Manager Creator Dashboard Open Cloud API

To import audio through the Asset Manager :

1.

Click the Import  button.

2.

Select and then confirm the audio files you want to import from your local system.

3.

Once you confirm the imports and the files import successfully, they display with a green checkmark and a completed status.

To standardize the playback format and check for corrupt or invalid files, Studio transcodes imported audio before saving it as an asset. If you receive an error while importing audio, Studio is likely rejecting it during the transcode process. In addition, some older audio tools generate invalid file headers or frames when exporting.

If Studio continues to reject the audio you're trying to import, ensure your audio tools are updated, then verify that the audio files meet the import requirements.

After the audio assets pass moderation, you can reuse them in any project on the platform. Although you are initially the only one who can view and use private audio assets, the [asset privacy](/docs/projects/assets/privacy)  system lets you grant usage permissions to specific friends and experiences.

## [Visibility](#visibility)[](#visibility)

When you upload audio to Roblox, it is automatically classified as a sound effect  or a song . Sound effects are not eligible to appear on the details page of the game in which they're used, but they can be distributed on the [Creator Store](/docs/production/creator-store) . A song can  appear on the game details page if:

-

It passes all moderation and copyright checks.

-

It meets the minimum duration, playback (number of unique plays), and platform age requirements.

-

It has a meaningful and appropriate title.

-

The uploader is [ID verified](/docs/production/publishing/account-verification) .

-

The uploader has acknowledged the Roblox [Audio Terms of Use](https://en.help.roblox.com/hc/en-us/articles/23359485439124-Audio-Upload-License-Agreement) .

Eligible songs will become visible on the game details page by default when the above requirements are met. You can toggle this visibility on the asset's Configure  page in the [Creator Hub](https://create.roblox.com/) . You can also add the Roblox usernames of song composers and collaborators in the Song Artist  field; if this field is left blank, you'll be listed as the artist.

Once a song is on the game details page, players can click the song tile to see the song details page. Here, they can view additional information about the track and listen to a 15-second preview.

 ![Song preview page linked from a game's details page](https://prod.docsiteassets.roblox.com/assets/publishing/experiences-places-assets/Song-Preview-Details-Page.jpg)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
