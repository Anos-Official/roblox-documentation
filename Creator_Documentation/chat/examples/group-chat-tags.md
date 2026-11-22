<!-- Source: https://create.roblox.com/docs/en-us/chat/examples/group-chat-tags -->

Assign chat tags | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/chat/examples/group-chat-tags.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. Chat
6. /
7. [Text chat](/docs/en-us/chat/in-experience-text-chat)
8. /
9. [Examples](/docs/en-us/chat/examples/simple-custom-frontend-ui)

# Assign chat tags

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/chat/examples/group-chat-tags.md)

This example demonstrates how to assign chat tags  to players based on their membership in a [group](/docs/en-us/projects/groups) . Chat tags are a way to visually identify a player in the chat window and useful for indicating a player's role or status.

 ![VIP chat tag appended to user name in the chat window.](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/Chat-Tag-VIP.png)

Because [text chat callbacks](/docs/en-us/chat/in-experience-text-chat#text-chat-hooks-and-callbacks)  expect a non-yielding callback, attempting to query the group membership status of a player in the [TextChatService.OnIncomingMessage](/docs/en-us/reference/engine/classes/TextChatService#OnIncomingMessage)  callback is not recommended, as it may cause the chat system to hang or become unresponsive.

Instead, set a player [attribute](/docs/en-us/studio/properties#instance-attributes)  when they join the server. Setting an attribute lets you reuse the player's status in other parts of your game such as allowing access to particular areas or providing bonus experiences.

1.

Create a [Script](/docs/en-us/reference/engine/classes/Script)  in [ServerScriptService](/docs/en-us/reference/engine/classes/ServerScriptService)  and add the following code to it:

Server

```

local Players = game:GetService("Players")

-- Replace 123456 with the group ID you want to check for

local groupID = 123456

Players.PlayerAdded:Connect(function(player)

	local success, isInGroup = pcall(function()

		return player:IsInGroupAsync(groupID)

	end)

	if success and isInGroup then

		player:SetAttribute("IsVIP", true)

	else

		player:SetAttribute("IsVIP", false)

	end

end)

```

2.

Create a [LocalScript](/docs/en-us/reference/engine/classes/LocalScript)  in [StarterPlayer](/docs/en-us/reference/engine/classes/StarterPlayer)  ⟩ [StarterCharacterScripts](/docs/en-us/reference/engine/classes/StarterCharacterScripts)  and add the following code to display a [VIP]  tag in the chat window:

Client

```

local Players = game:GetService("Players")

local TextChatService = game:GetService("TextChatService")

TextChatService.OnIncomingMessage = function(message: TextChatMessage)

	local textSource = message.TextSource

	if textSource then

		local player = Players:GetPlayerByUserId(textSource.UserId)

		if player then

			if player:GetAttribute("IsVIP") == true then

				local overrideProperties = Instance.new("TextChatMessageProperties")

				overrideProperties.PrefixText = "[VIP] " .. message.PrefixText

				return overrideProperties

			end

		end

	end

	return nil

end

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
