<!-- Source: https://create.roblox.com/docs/reference/engine/classes/VoiceChatService -->

VoiceChatService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/VoiceChatService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [VoiceChatService](/docs/reference/engine/classes/VoiceChatService)

English

Feedback

Engine Class

VoiceChatService

Not Creatable

Service

---

## Summary

Properties

|

[DefaultDistanceAttenuation](#DefaultDistanceAttenuation) :[Enum.VoiceChatDistanceAttenuationType](/docs/reference/engine/enums/VoiceChatDistanceAttenuationType)

 |
| --- | --- |
|

[EnableDefaultVoice](#EnableDefaultVoice) :[boolean](/docs/luau/booleans)

 |
|

[EnableVoiceVolumeControls](#EnableVoiceVolumeControls) :[Enum.RolloutState](/docs/reference/engine/enums/RolloutState)

 |
|

[UseAudioApi](#UseAudioApi) :[Enum.AudioApiRollout](/docs/reference/engine/enums/AudioApiRollout)

 |

Methods

|

[GetChatGroupsAsync](#GetChatGroupsAsync) (players :  Instances ) :[{any}](/docs/luau/tables#arrays)

 |
|

[IsVoiceEnabledForUserIdAsync](#IsVoiceEnabledForUserIdAsync) (userId :  [User](/docs/reference/engine/datatypes/User) ) :[boolean](/docs/luau/booleans)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Properties

DefaultDistanceAttenuation

Read Parallel

Capabilities: Audio, Chat, PluginOrOpenCloud

VoiceChatService.DefaultDistanceAttenuation :[Enum.VoiceChatDistanceAttenuationType](/docs/reference/engine/enums/VoiceChatDistanceAttenuationType)

Provide feedback

---

EnableDefaultVoice

Read Parallel

Capabilities: Audio, Chat, PluginOrOpenCloud

VoiceChatService.EnableDefaultVoice :[boolean](/docs/luau/booleans)

Provide feedback

---

EnableVoiceVolumeControls

Roblox Script Security

Read Parallel

Capabilities: Audio, Chat

VoiceChatService.EnableVoiceVolumeControls :[Enum.RolloutState](/docs/reference/engine/enums/RolloutState)

Provide feedback

---

UseAudioApi

Read Parallel

Capabilities: Audio, Chat, PluginOrOpenCloud

VoiceChatService.UseAudioApi :[Enum.AudioApiRollout](/docs/reference/engine/enums/AudioApiRollout)

Provide feedback

---

Methods

GetChatGroupsAsync

Yields

Capabilities: Audio, Chat

VoiceChatService:GetChatGroupsAsync (players : Instances ) :[{any}](/docs/luau/tables#arrays)

Parameters

|

players : Instances

 |

Returns

[{any}](/docs/luau/tables#arrays)

Code Samples

TeleportPlayerToBestChatServer

```

-- Server Script

local VoiceChatService = game:GetService("VoiceChatService")

local TeleportService = game:GetService("TeleportService")

local Players = game:GetService("Players")

local TARGET_PLACE_ID = 1234567890 -- Destination place ID

--[[

	Stubbed universe-wide server state.

	In practice, this data could be stored and updated using MemoryStore

	or another backend system.

	Example shape:

	ActiveServers = {

		{

			serverId = "abc",

			privateServerId = game.PrivateServerId,

			groupUserCounts = {

				groupA = 12,

				groupB = 5

			}

		},

		{

			serverId = "def",

			privateServerId = game.PrivateServerId,

			groupUserCounts = {

				groupB = 8

			}

		}

	}

]]

local ActiveServers = {}

local function teleportPlayerToBestServer(player)

	local success, chatGroups = pcall(function()

		return VoiceChatService:GetChatGroupsAsync({ player })

	end)

	if not success or not chatGroups then

		warn("Failed to retrieve chat groups for player:", player.UserId)

		return

	end

	-- Collect all chat group IDs the player is eligible for

	local playerGroupIds = {}

	for _, group in ipairs(chatGroups) do

		for _, groupId in ipairs(group) do

			playerGroupIds[groupId] = true

		end

	end

	local bestServer = nil

	local bestUserCount = 0

	-- Choose the server with the highest number of compatible users

	for _, server in ipairs(ActiveServers) do

		local compatibleUserCount = 0

		for groupId, userCount in pairs(server.groupUserCounts) do

			if playerGroupIds[groupId] then

				compatibleUserCount += userCount

			end

		end

		if compatibleUserCount > bestUserCount then

			bestUserCount = compatibleUserCount

			bestServer = server

		end

	end

	if not bestServer then

		warn("No suitable server found for player:", player.UserId)

		return

	end

	local ok, err = pcall(function()

		local teleportOptions = Instance.new("TeleportOptions")

		teleportOptions.ReservedServerId = bestServer.privateServerId

		TeleportService:TeleportAsync(

			TARGET_PLACE_ID,

			{ player },

			teleportOptions

		)

	end)

	if not ok then

		warn("Teleport failed:", err)

	end

end

Players.PlayerAdded:Connect(teleportPlayerToBestServer)

```

Get Chat Groups Async

```

local VoiceChatService = game:GetService("VoiceChatService")

local Players = game:GetService("Players")

local players = Players:GetPlayers()

local success, chatGroups = pcall(function()

	return VoiceChatService:GetChatGroupsAsync(players)

end)

if not success then

	warn("Failed to retrieve chat groups")

	return

end

for _, group in ipairs(chatGroups) do

	-- Each group contains chat group ID strings.

	-- Players who share a matching group ID can chat with each other.

	for _, groupId in ipairs(group) do

		print("Chat group ID:", groupId)

	end

end

```

Provide feedback

---

IsVoiceEnabledForUserIdAsync

Yields

Capabilities: Audio, Chat

VoiceChatService:IsVoiceEnabledForUserIdAsync (userId :[User](/docs/reference/engine/datatypes/User) ) :[boolean](/docs/luau/booleans)

Parameters

|

userId :[User](/docs/reference/engine/datatypes/User)

 |

Returns

[boolean](/docs/luau/booleans)

Code Samples

Is Voice Enabled For User Id Async

```

local Players = game:GetService("Players")

local VoiceChatService = game:GetService("VoiceChatService")

local localPlayer = Players.LocalPlayer

local success, enabled = pcall(function()

	return VoiceChatService:IsVoiceEnabledForUserIdAsync(localPlayer.UserId)

end)

if success and enabled then

	print("Voice chat enabled!")

end

```

Provide feedback

---

Jump to

▼

VoiceChatService

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[DefaultDistanceAttenuation](#DefaultDistanceAttenuation)

[EnableDefaultVoice](#EnableDefaultVoice)

[EnableVoiceVolumeControls](#EnableVoiceVolumeControls)

[UseAudioApi](#UseAudioApi)

[Methods](#methods)

[GetChatGroupsAsync()](#GetChatGroupsAsync)

[IsVoiceEnabledForUserIdAsync()](#IsVoiceEnabledForUserIdAsync)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
