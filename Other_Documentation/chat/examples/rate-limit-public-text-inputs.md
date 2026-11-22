<!-- Source: https://create.roblox.com/docs/chat/examples/rate-limit-public-text-inputs -->

Rate-limited text inputs | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/chat/examples/rate-limit-public-text-inputs.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. Chat
6. /
7. [Text chat](/docs/chat/in-experience-text-chat)
8. /
9. [Examples](/docs/chat/examples/simple-custom-frontend-ui)

# Rate-limited text inputs

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/chat/examples/rate-limit-public-text-inputs.md)

This example shows how to implement a rate limit of 1 minute on a text input field that allows players to post notes to a community bulletin board.

Add the following to a [Script](/docs/reference/engine/classes/Script)  in [ServerScriptService](/docs/reference/engine/classes/ServerScriptService) :

Server

```

local Players = game:GetService("Players")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- Create RemoteEvent for communication

local postNoteEvent = Instance.new("RemoteEvent")

postNoteEvent.Name = "PostNoteEvent"

postNoteEvent.Parent = ReplicatedStorage

-- Rate limit of one note per minute per player

local COOLDOWN_TIME = 60 -- Time in seconds

local lastPostTime = {}

local function canPlayerPost(player)

	local userId = player.UserId

	local currentTime = tick()

	if lastPostTime[userId] then

		local timeSinceLastPost = currentTime - lastPostTime[userId]

		if timeSinceLastPost < COOLDOWN_TIME then

			return false, COOLDOWN_TIME - timeSinceLastPost

		end

	end

	return true, 0

end

-- Handle post requests with rate limit and text filtering

postNoteEvent.OnServerEvent:Connect(function(player, noteData)

	local canPost, cooldown = canPlayerPost(player)

	if not canPost then

		postNoteEvent:FireClient(player, "cooldown", math.ceil(cooldown))

		return

	end

	-- All text shared publicly must go through a text filter

	local filterResult = getFilterResult(noteData.text, player.UserId)

	if filterResult then

		local success, filteredText = pcall(function()

		return filterResult:GetNonChatStringForBroadcastAsync()

	end)

	if success then

		-- Create the note

		local note = {

			text = filteredText

		}

		-- Update last post time

		lastPostTime[player.UserId] = tick()

		-- Send success response

		postNoteEvent:FireClient(player, "success", note)

		-- Broadcast new note to all players

		postNoteEvent:FireAllClients("newNote", note)

	else

		warn("Error filtering text!")

	end

end)

-- Clean up when player leaves

Players.PlayerRemoving:Connect(function(player)

	lastPostTime[player.UserId] = nil

end)

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
