<!-- Source: https://create.roblox.com/docs/en-us/ui/temporary-limits -->

Temporary text limits | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/ui/temporary-limits.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [User interface](/docs/en-us/ui)
6. /
7. [Text filtering](/docs/en-us/ui/text-filtering)

# Temporary text limits

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/ui/temporary-limits.md)

Roblox temporarily limits text features in a game when it detects players holding conversations through a surface other than [TextChatService](/docs/en-us/reference/engine/classes/TextChatService) . This page explains how to tell if your game has been limited, what players see, and how to get the limit lifted.

Any chat between players must go through [TextChatService](/docs/en-us/reference/engine/classes/TextChatService) . For the requirements that each type of text surface must meet, see [Chat system guidelines](/docs/en-us/chat/guidelines) .

## [How temporary limits work](#how-temporary-limits-work)[](#how-temporary-limits-work)

When Roblox detects conversations through a surface other than [TextChatService](/docs/en-us/reference/engine/classes/TextChatService) , it temporarily limits text features in the game. The limit lasts a minimum of 24 hours and requires a game update before Roblox lifts it. The limit can return if Roblox continues to observe players holding conversations outside of [TextChatService](/docs/en-us/reference/engine/classes/TextChatService) .

## [Identify a temporary limit](#identify-a-temporary-limit)[](#identify-a-temporary-limit)

When Roblox limits your game:

-

Notifications and banners about the limit appear on the game's Creator Hub page.

-

The game owner receives an email.

While the limit is active, any feature that collects text from players, passes it through [text filtering](/docs/en-us/ui/text-filtering) , and shows that text to other players is rate-limited to one submission per player every 60 seconds.

## [Player experience](#player-experience)[](#player-experience)

If your game is limited, players who use text features more than once per 60 seconds see their text replaced with ⏱️⏱️⏱️ until they can submit text again.

For example, in a game where players hold signs:

| Timestamp | | Text the player submits | | Text the sign shows |
| --- | --- |
| 1:00:00 | | Hello | | Hello |
| 1:00:17 | | I like rainy days | | ⏱️⏱️⏱️ |
| 1:02:00 | | I like sunny days even more | | I like sunny days even more |

## [Lift a temporary limit](#lift-a-temporary-limit)[](#lift-a-temporary-limit)

To lift a temporary text limit:

1.

Find the surface players are using to hold conversations. Check every feature where players enter text that other players can see, such as signs, license plates, bulletin boards, pet and item names, comments, item trading windows, and admin tools.

2.

Decide how to fix each surface:

-

If the feature is built for communication, send all conversations through [TextChatService](/docs/en-us/reference/engine/classes/TextChatService)  in a [TextChannel](/docs/en-us/reference/engine/classes/TextChannel) . See [TextChatService](/docs/en-us/reference/engine/classes/TextChatService) .

-

If the feature isn't meant for communication, continue with the next steps.

3.

Search your code for calls to [FilterStringAsync()](/docs/en-us/reference/engine/classes/TextService#FilterStringAsync) , [FilterStringForBroadcast()](/docs/en-us/reference/engine/classes/Chat#FilterStringForBroadcast) , or [FilterStringForPlayerAsync()](/docs/en-us/reference/engine/classes/Chat#FilterStringForPlayerAsync)  on player text to find where player text is used.

4.

Remove the feature, or [rate-limit](#rate-limit-text-surfaces)  it to one submission per player every 60 seconds.

5.

Publish a new version of your root place.

Roblox lifts the limit in under 24 hours after you publish a new version of your root place. The banner on your Creator Hub page disappears, and text behavior returns to normal.

Roblox continues to monitor the game for conversations outside of [TextChatService](/docs/en-us/reference/engine/classes/TextChatService) . If it detects those conversations again, it applies the limit again. You might have missed a text feature the first time. Repeat the investigation and publish a new version.

## [Rate-limit text surfaces](#rate-limit-text-surfaces)[](#rate-limit-text-surfaces)

Prevent players from holding conversations outside of [TextChatService](/docs/en-us/reference/engine/classes/TextChatService) . Rate-limit every player-editable text surface to one submission per player every 60 seconds, and filter the text with [FilterStringAsync()](/docs/en-us/reference/engine/classes/TextService#FilterStringAsync)  before displaying it. At that rate, players can't hold a conversation through the surface, so Roblox doesn't detect it as chat. You can also remove or change the feature.

Enforce the cooldown on the server. Players can bypass a timer that runs on the client.

For another example that applies the same 60-second server-side cooldown and text filtering to a community bulletin board, see [Rate-limited text inputs](/docs/en-us/chat/examples/rate-limit-public-text-inputs) . The following [Script](/docs/en-us/reference/engine/classes/Script)  adds a 60-second limit to a sign. It assumes a [RemoteEvent](/docs/en-us/reference/engine/classes/RemoteEvent)  named SubmitSignText  in [ReplicatedStorage](/docs/en-us/reference/engine/classes/ReplicatedStorage)  that the client fires with the player's text:

Server

```

local Players = game:GetService("Players")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local TextService = game:GetService("TextService")

local COOLDOWN_SECONDS = 60

local lastSubmit = {}

local submitSignText = ReplicatedStorage:WaitForChild("SubmitSignText")

submitSignText.OnServerEvent:Connect(function(player, text)

	if typeof(text) ~= "string" or #text > 100 then

		return

	end

	local now = os.clock()

	local last = lastSubmit[player]

	if last and now - last < COOLDOWN_SECONDS then

		return -- On cooldown: reject and tell the player how long to wait

	end

	lastSubmit[player] = now

	local success, filtered = pcall(function()

		return TextService:FilterStringAsync(text, player.UserId)

	end)

	if success then

		local safeText = filtered:GetNonChatStringForBroadcastAsync()

		-- Display safeText on the sign

	end

end)

Players.PlayerRemoving:Connect(function(player)

	lastSubmit[player] = nil

end)

```

## [Takedowns](#takedowns)[](#takedowns)

A temporary text limit isn't a takedown, and temporary limits largely replace takedowns as the consequence for this violation. However, Roblox can still take down games for repeated violations, or for openly promoting features such as uncontrolled or limitless chat.

If Roblox takes down your game for a [TextChatService](/docs/en-us/reference/engine/classes/TextChatService)  violation:

1.

Remove or rate-limit the surface that lets players converse outside of [TextChatService](/docs/en-us/reference/engine/classes/TextChatService) . See [Lift a temporary limit](#lift-a-temporary-limit)  and [Rate-limit text surfaces](#rate-limit-text-surfaces) .

2.

Publish the change.

3.

[Submit an appeal](https://www.roblox.com/report-appeals#/)  that describes what you changed and what measures you're taking to prevent future violations. Replies typically arrive within one to two weeks.

## [FAQ](#faq)[](#faq)

Will this limit be applied to all games?

No. Roblox only applies these temporary limits to certain games after it detects that players are holding conversations through a surface other than [TextChatService](/docs/en-us/reference/engine/classes/TextChatService) .

Should I appeal via Support channels?

No. Follow the guidance in [Lift a temporary limit](#lift-a-temporary-limit)  and investigate your text features. The support team repeats the same guidance and asks you to publish a version update and wait 24 hours.

How will I know if the limits are lifted?

The banner on your game's Creator Hub page is removed, and text behavior goes back to normal.

Once the limit is removed, does that mean my game is approved going forward?

Detection is based on player behavior patterns, and these patterns change over time. Roblox continues monitoring the game and detecting if players are holding conversations outside of [TextChatService](/docs/en-us/reference/engine/classes/TextChatService) . If such conversations are detected, the limit is applied again.

Unrelated text features in my game are limited. Why?

Roblox detects and enforces at the game level, not the feature level. Your "hold a sign" feature might be the one used for conversations, while an unrelated feature such as making a playlist is limited as part of the game-wide text limit. Roblox can't apply limits for individual features of your game.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
