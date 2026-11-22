<!-- Source: https://create.roblox.com/docs/production/monetization/avatar-creation-token -->

Avatar creation token | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/production/monetization/avatar-creation-token.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. In-game creation

# Avatar creation token

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/production/monetization/avatar-creation-token.md)

An avatar creation token  enables developers to allow users to create, purchase, and save avatar items directly from a game to their platform-level inventory using [in-experience creation](/docs/avatar/in-experience-creation)  or [in-experience makeup creation](/docs/avatar/in-experience-creation-makeup) . Games that implement in-game creation APIs, such as [PromptCreateAvatarAsync](/docs/reference/engine/classes/AvatarCreationService#PromptCreateAvatarAsync) , [PromptCreateAvatarAssetAsync](/docs/reference/engine/classes/AvatarCreationService#PromptCreateAvatarAssetAsync) , and [PromptCreateMakeupAsync](/docs/reference/engine/classes/AvatarCreationService#PromptCreateMakeupAsync) , must include one or more avatar creation tokens. You can purchase and manage tokens in your game's [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

Owners of games that incorporate in-game avatar item creation also benefit from [Marketplace commissions](/docs/marketplace/marketplace-fees-and-commissions#commissions)  as both creator  and game owner .

To create avatar creation tokens, you or your group must meet the [Marketplace creator requirements](/docs/marketplace/marketplace-policy#creator-requirements) . For the token to remain valid, the token owner must maintain these creator requirements.

## [Create a token](#create-a-token)[](#create-a-token)

To allow users to create, pay for, and save avatar items to their Roblox inventory in your game, you'll need to set up an Avatar Creation Token in your game's dashboard.

Each token requires a Creation Advance  and a Creation Fee . The advance is fully recoupable and based on the [current publishing advance prices](/docs/marketplace/marketplace-fees-and-commissions#publishing-advance)  for that item type. Before purchase, you can preview a summary of your total combined advance and fee when creating your token.

To create a token:

1.

Navigate to the [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Expand the account switcher in the upper‑left and ensure that the appropriate user or group is selected.

3.

In Creations  ⟩ Experiences , select your game.

4.

On the left panel, navigate to Monetization  ⟩ Avatar Creation Tokens .

5.

Click Create Token .

1.

Ensure that your account or group account meets the [Marketplace Creator Requirements](/docs/marketplace/marketplace-policy#creator-requirements) . If the token owner account is not ID-verified with a Roblox Plus or Premium subscription, the game cannot enable in-game creation APIs. You must maintain these requirements for the token to remain valid.

6.

Complete the following fields:

1.

Name  - The name of your token. This is not user-facing and can be changed after creation.

2.

Description  - The description of your token. This is not user-facing and can be changed after creation.

3.

Item Type  - The Body  item type can be used in-game with [PromptCreateAvatarAsync](/docs/reference/engine/classes/AvatarCreationService#PromptCreateAvatarAsync)  whereas the rest of the item types are meant to be used with [PromptCreateAvatarAssetAsync](/docs/reference/engine/classes/AvatarCreationService#PromptCreateAvatarAssetAsync) . Makeup item types can also be composited into a single purchasable outfit with [PromptCreateMakeupAsync](/docs/reference/engine/classes/AvatarCreationService#PromptCreateMakeupAsync) , which requires a separate token per layer whose type matches that layer's asset type. You cannot change this setting after token creation.

4.

Amount Above Price Floor  - Set the price above the Marketplace Price Floor for created items. If you intend to have different price points for items of the same type in your game, the best way to achieve this is by purchasing multiple tokens. You can modify this field after creation.

5.

Do not price below

OPTIONAL

 - Set the minimum price for users to purchase your item. You can modify this field after creation.

 ![Price related fields for avatar token creation, including a calculated item price.](https://prod.docsiteassets.roblox.com/assets/monetization/avatar-creation-tokens/Avatar-Creation-Token-Prices.png)

7.

When complete, verify the Creation Advance  and Creation Fee  calculations and select Create Token  to submit your purchase.

8.

You can now access the created token in the game's avatar creation tokens  settings. To implement [PromptCreateAvatarAsync](/docs/reference/engine/classes/AvatarCreationService#PromptCreateAvatarAsync)  or [PromptCreateAvatarAssetAsync](/docs/reference/engine/classes/AvatarCreationService#PromptCreateAvatarAssetAsync) , you'll need the token ID, which you can access by selecting the three dots on the thumbnail and selecting Copy Token ID .

 ![Dropdown for created tokens revealing a Copy Token ID option](https://prod.docsiteassets.roblox.com/assets/monetization/avatar-creation-tokens/Avatar-Creation-Token-Copy-ID.png)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
