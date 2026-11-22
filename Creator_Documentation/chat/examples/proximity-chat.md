<!-- Source: https://create.roblox.com/docs/en-us/chat/examples/proximity-chat -->

Proximity-based chat | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/chat/examples/proximity-chat.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. Chat
6. /
7. [Text chat](/docs/en-us/chat/in-experience-text-chat)
8. /
9. [Examples](/docs/en-us/chat/examples/simple-custom-frontend-ui)

# Proximity-based chat

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/chat/examples/proximity-chat.md)

This example shows how to implement an exclusive chat for users who are near each other in the 3D world. It extends the callback with a function using [TextSource](/docs/en-us/reference/engine/classes/TextSource)  to identify the locations of a user who might be a potential message receiver. If this function returns false , it means that the user locates further than the preset valid range from the message sender, so the system doesn't deliver the message to that user.

Add the following to a [Script](/docs/en-us/reference/engine/classes/Script)  in [ServerScriptService](/docs/en-us/reference/engine/classes/ServerScriptService) :

Server

```

local TextChatService = game:GetService("TextChatService")

local Players = game:GetService("Players")

-- Get the chat channel for proximity-based chat

-- You can replace this general channel with a dedicated channel

local generalChannel: TextChannel = TextChatService:WaitForChild("TextChannels").RBXGeneral

-- Function to get the position of a user's character

local function getPositionFromUserId(userId: number)

	-- Get the player associated with the given user ID

	local targetPlayer = Players:GetPlayerByUserId(userId)

	-- If the player exists, get their character's position

	if targetPlayer then

		local targetCharacter = targetPlayer.Character

		if targetCharacter then

			return targetCharacter:GetPivot().Position

		end

	end

	-- Return a default position if the player or character cannot be found

	return Vector3.zero

end

-- Set the callback for the general channel to control message delivery

generalChannel.ShouldDeliverCallback = function(textChatMessage: TextChatMessage, targetTextSource: TextSource)

	-- Get the positions of the message sender and target

	local sourcePos = getPositionFromUserId(textChatMessage.TextSource.UserId)

	local targetPos = getPositionFromUserId(targetTextSource.UserId)

	-- Deliver message if distance between sender and target is less than 50 units

	return (targetPos - sourcePos).Magnitude < 50

end

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
