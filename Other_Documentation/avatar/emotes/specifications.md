<!-- Source: https://create.roblox.com/docs/avatar/emotes/specifications -->

Emote specifications | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar/emotes/specifications.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. Animations
6. /
7. Emotes

# Emote specifications

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar/emotes/specifications.md)

Emotes are made up of an [Animation](/docs/reference/engine/classes/Animation)  object with the [Animation.AnimationId](/docs/reference/engine/classes/Animation#AnimationId)  property set to the asset ID of your animation sequence. The [Animation](/docs/reference/engine/classes/Animation)  object is the only component required to upload an emote to the Marketplace because animations do not require meshes, textures, or other 3D art components.

![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-emotes/Animation-Explorer.png) Animation  object in the Explorer window.

![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-emotes/Animation-Properties.png) AnimationId  property in the Properties window.

## [Animation requirements](#animation-requirements)[](#animation-requirements)

Emotes must meet the following requirements before you upload them to the Marketplace, otherwise they may fail validation:

-

Emotes must be less than 10 seconds.

-

The joint root of the character cannot move too far from its starting position.

-

Movement speed can't exceed a certain threshold to prevent teleportation abuse (measured from a frame-by-frame basis).

-

Animation data must reference a [standard R15 rig](/docs/avatar/character-bodies/specifications#standard-r15-rigs) .

Emotes for [advanced R15 rigs](/docs/avatar/character-bodies/specifications#advanced-r15-rigs)  are currently in a closed beta. For more information, see the [DevForum announcement](https://devforum.roblox.com/t/upload-and-publish-for-emotes-with-additional-joints-is-now-open/4710932) .

-

Animation must be sourced from a CurveAnimation . For information on converting animation data, see [Import emotes - Generate asset ID](/docs/avatar/emotes/import#generate-asset-id) .

-

Animations must meet Roblox's [Community Standards](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards)  and [Marketplace policies](/docs/marketplace/marketplace-policy) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
