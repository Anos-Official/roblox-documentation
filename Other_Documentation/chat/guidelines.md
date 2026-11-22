<!-- Source: https://create.roblox.com/docs/chat/guidelines -->

Chat system guidelines | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/chat/guidelines.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. Chat
6. /
7. [Text chat](/docs/chat/in-experience-text-chat)

# Chat system guidelines

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/chat/guidelines.md)

Chat  is any feature that lets players hold a back-and-forth conversation in under 60 seconds. To keep players safe, chat must go through [TextChatService](/docs/reference/engine/classes/TextChatService) , which applies privacy settings, age-based limits, text filtering, and abuse reporting automatically. If players can converse in your game outside [TextChatService](/docs/reference/engine/classes/TextChatService) , Roblox might take your game down.

Use this breakdown to decide how each text surface in your game must comply:

-

Chat (must use [TextChatService](/docs/reference/engine/classes/TextChatService) ) : Chat windows and chat bubbles over avatars, direct messages and team messages, custom chat systems, radios, phones and messaging UIs, admin tools that let players or admins message each other, and any text field that players can use to message each other in under 60 seconds.

-

Not chat (if it meets the requirements on this page) : Player-editable text that other players can see, such as signs, bulletin boards, pet names, and name fields, as long as it has a one-minute rate limit per player and text filtering; preset phrases that players send from a fixed list for gameplay coordination; and developer-set text that players can't edit or reply to, such as menus, status updates, one-way announcements, and moderation logs.

## [In-game text chat](#in-game-text-chat)[](#in-game-text-chat)

In-game text chat is any message created in your game that one user sends to one or more other users and that allows back-and-forth conversation in under 60 seconds, including:

-

Chat bubbles over an avatar's head

-

Direct messages between users

-

Chat window communication between users

-

Team-specific messages

## [Comply with text chat requirements](#comply-with-text-chat-requirements)[](#comply-with-text-chat-requirements)

1.

Integrate [TextChatService](/docs/reference/engine/classes/TextChatService)  for all player-to-player chat, per the [Misusing Roblox Systems Community Standard](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards) . For information on migrating from the legacy chat system, see the [Roblox Developer Forum](https://devforum.roblox.com/t/migrate-to-textchatservice-removing-support-for-legacy-chat-and-custom-chat-systems/3237100)  and [Migrate from legacy chat](/docs/chat/in-experience-text-chat#migrate-from-legacy-chat) .

2.

Don't circumvent [TextChatService](/docs/reference/engine/classes/TextChatService) , text filtering, or age-based limits. [TextChatService](/docs/reference/engine/classes/TextChatService)  enforces these automatically.

3.

Mark [TextChannels](/docs/reference/engine/classes/TextChannel)  created for direct chat with [TextChannel:SetDirectChatRequester()](/docs/reference/engine/classes/TextChannel#SetDirectChatRequester) .

4.

Don't include any feature that lets a user send text to other users in under 60 seconds outside of [TextChatService](/docs/reference/engine/classes/TextChatService) .

If users repeatedly send messages that violate community standards, Roblox warns them and then temporarily prevents them from sending messages. For details, see [Text Chat Nudge FAQ](https://en.help.roblox.com/hc/en-us/articles/37541811348884-Text-Chat-Nudge-FAQ-s) .

If Roblox takes your game down for a chat violation, remove or rate-limit the surface that lets players converse outside [TextChatService](/docs/reference/engine/classes/TextChatService) , then appeal and describe what you changed. Replies typically arrive within one to two weeks.

## [UGC text and editable text](#ugc-text-and-editable-text)[](#ugc-text-and-editable-text)

Some features let players edit text that other players can see, such as:

-

An interface for a user to rename their pet or license plate

-

Signs that players can enter and edit text on

-

Comments or bulletin boards

-

Editable text fields for in-game items and accessories

These surfaces are allowed, but they must not become a substitute for chat. Players might misuse them to chat by editing text repeatedly in quick succession, so editable text must meet the requirements in [Rate-limit and filter editable text](#rate-limit-and-filter-editable-text) .

## [Rate-limit and filter editable text](#rate-limit-and-filter-editable-text)[](#rate-limit-and-filter-editable-text)

1.

Filter player-written text with [text filtering](/docs/ui/text-filtering)  before your game displays it.

2.

Rate-limit editable text that other players can see to at least one minute between submissions per player so it can't be used as makeshift chat. See [rate-limited text inputs](/docs/chat/examples/rate-limit-public-text-inputs)  for an example.

3.

Rate-limit comments on posts and bulletin boards to one minute per player, like other editable text. Don't let comments support a reply feature. Replies are a conversation and must meet the chat requirements.

Filtering text is required, but it isn't sufficient on its own. Filtering doesn't stop players from using a surface to talk to each other, so you still need the rate limit. Don't create any way for players to communicate outside [TextChatService](/docs/reference/engine/classes/TextChatService) .

## [Developer-set text](#developer-set-text)[](#developer-set-text)

Developer-set text  is one-way text written and controlled by a game's developers, admins, or moderators to inform or guide players. Players can't alter it, and static text you write yourself doesn't need text filtering. Examples include:

-

Text on menus created by developers, for example "Press any button to continue."

-

Status updates from the game, for example "Two minutes remaining!"

-

One-way announcements from the creator, including admin commands that only send one-way announcements

-

Moderation audit logs or messages

If several users can use developer-set text, or admins use it to chat with each other, Roblox might moderate your game until those surfaces comply with the chat requirements or no longer allow real-time communication between users. Admin commands that let players reply, or that let admins chat with each other, count as chat.

## [Use Quick Words for preset phrases](#use-quick-words-for-preset-phrases)[](#use-quick-words-for-preset-phrases)

[Quick Words](/docs/chat/quick-words)  are a limited set of approved phrases that players can use to coordinate gameplay. Players choose a phrase from the list and can't type their own text. By May 2027, any preset phrases that players can use, especially ones that appear in chat, must go through Quick Words and follow the [preset system guidelines](/docs/chat/preset-system-guidelines) .

1.

In [Creator Hub](https://create.roblox.com/dashboard/creations) , select your game, then go to Configure  ⟩ Chat  ⟩ Quick Words .

2.

Add up to three custom categories, with three to ten phrases in each. Your custom categories replace the default Roblox categories, but the General  category stays available in every game.

3.

Write phrases in English. Roblox translates them automatically based on each player's chat language setting.

4.

Publish your phrases. Roblox reviews them against the content guidelines before they go live. If a phrase isn't approved, revise it and publish again.

## [Respect privacy settings](#respect-privacy-settings)[](#respect-privacy-settings)

Users can have different levels of access to communication features based on their [privacy and content rating settings](https://www.roblox.com/my/account#!/privacy/Communication/ExperienceChat)  or parental controls. Users might also have restrictions based on the app store they installed Roblox from or local law. [TextChatService](/docs/reference/engine/classes/TextChatService)  applies all of these automatically.

To comply:

1.

Mark every direct chat channel, meaning a private conversation between specific users, with [TextChannel:SetDirectChatRequester()](/docs/reference/engine/classes/TextChannel#SetDirectChatRequester) , which applies the correct privacy settings.

2.

Use [TextChatService:CanUserChatAsync()](/docs/reference/engine/classes/TextChatService#CanUserChatAsync)  and [TextChatService:CanUsersChatAsync()](/docs/reference/engine/classes/TextChatService#CanUsersChatAsync)  to check whether players can chat, and update your UI to match, for example by hiding the chat button.

3.

Use [TextChatService:CanUsersDirectChatAsync()](/docs/reference/engine/classes/TextChatService#CanUsersDirectChatAsync)  to do the same for direct chat between specific users.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
