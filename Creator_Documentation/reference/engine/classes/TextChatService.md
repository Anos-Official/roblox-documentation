<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/TextChatService -->

TextChatService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/TextChatService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [TextChatService](/docs/en-us/reference/engine/classes/TextChatService)

English

Feedback

Engine Class

TextChatService

Not Creatable

Service

---

## Summary

Properties

|

[ChatTranslationEnabled](#ChatTranslationEnabled) :[boolean](/docs/en-us/luau/booleans)

 |
| --- | --- |
|

[ChatVersion](#ChatVersion) :[Enum.ChatVersion](/docs/en-us/reference/engine/enums/ChatVersion)

Deprecated

 |
|

[CreateDefaultCommands](#CreateDefaultCommands) :[boolean](/docs/en-us/luau/booleans)

 |
|

[CreateDefaultTextChannels](#CreateDefaultTextChannels) :[boolean](/docs/en-us/luau/booleans)

 |
|

[PlatformIntegratedChat](#PlatformIntegratedChat) :[Enum.RolloutState](/docs/en-us/reference/engine/enums/RolloutState)

 |

Methods

|

[CanUserChatAsync](#CanUserChatAsync) (userId :  [User](/docs/en-us/reference/engine/datatypes/User) ) :[boolean](/docs/en-us/luau/booleans)

 |
|

[CanUsersChatAsync](#CanUsersChatAsync) (userIdFrom :  [User](/docs/en-us/reference/engine/datatypes/User) , userIdTo :  [User](/docs/en-us/reference/engine/datatypes/User) ) :[boolean](/docs/en-us/luau/booleans)

 |
|

[CanUsersDirectChatAsync](#CanUsersDirectChatAsync) (requesterUserId :  [User](/docs/en-us/reference/engine/datatypes/User) , userIds :  [{any}](/docs/en-us/luau/tables#arrays) ) :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[DisplayBubble](#DisplayBubble) (partOrCharacter :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) , message :  [string](/docs/en-us/luau/strings) ) : ()

 |
|

[GetChatGroupsAsync](#GetChatGroupsAsync) (players :  Instances ) :[{any}](/docs/en-us/luau/tables#arrays)

 |

Events

|

[BubbleDisplayed](#BubbleDisplayed) (partOrCharacter :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) , textChatMessage :  [TextChatMessage](/docs/en-us/reference/engine/classes/TextChatMessage) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[MessageReceived](#MessageReceived) (textChatMessage :  [TextChatMessage](/docs/en-us/reference/engine/classes/TextChatMessage) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[SendingMessage](#SendingMessage) (textChatMessage :  [TextChatMessage](/docs/en-us/reference/engine/classes/TextChatMessage) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |

Callbacks

|

[OnBubbleAdded](#OnBubbleAdded) (message :  [TextChatMessage](/docs/en-us/reference/engine/classes/TextChatMessage) , adornee :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) ) :[Tuple](/docs/en-us/luau/tuples)

 |
|

[OnChatWindowAdded](#OnChatWindowAdded) (message :  [TextChatMessage](/docs/en-us/reference/engine/classes/TextChatMessage) ) :[Tuple](/docs/en-us/luau/tuples)

 |
|

[OnIncomingMessage](#OnIncomingMessage) (message :  [TextChatMessage](/docs/en-us/reference/engine/classes/TextChatMessage) ) :[Tuple](/docs/en-us/luau/tuples)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Properties

ChatTranslationEnabled

Not Replicated

Read Parallel

Capabilities: Chat

TextChatService.ChatTranslationEnabled :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

ChatVersion

Deprecated

Show details

---

CreateDefaultCommands

Read Parallel

Capabilities: Chat

TextChatService.CreateDefaultCommands :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

CreateDefaultTextChannels

Read Parallel

Capabilities: Chat

TextChatService.CreateDefaultTextChannels :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

PlatformIntegratedChat

Roblox Script Security

Read Parallel

Capabilities: Chat

TextChatService.PlatformIntegratedChat :[Enum.RolloutState](/docs/en-us/reference/engine/enums/RolloutState)

Provide feedback

---

Methods

CanUserChatAsync

Yields

Capabilities: Chat

TextChatService:CanUserChatAsync (userId :[User](/docs/en-us/reference/engine/datatypes/User) ) :[boolean](/docs/en-us/luau/booleans)

Parameters

|

userId :[User](/docs/en-us/reference/engine/datatypes/User)

 |

Returns

[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

CanUsersChatAsync

Yields

Capabilities: Chat

TextChatService:CanUsersChatAsync (

userIdFrom :[User](/docs/en-us/reference/engine/datatypes/User) , userIdTo :[User](/docs/en-us/reference/engine/datatypes/User)

) :[boolean](/docs/en-us/luau/booleans)

Parameters

|

userIdFrom :[User](/docs/en-us/reference/engine/datatypes/User)

 |
|

userIdTo :[User](/docs/en-us/reference/engine/datatypes/User)

 |

Returns

[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

CanUsersDirectChatAsync

Yields

Capabilities: Chat

TextChatService:CanUsersDirectChatAsync (

requesterUserId :[User](/docs/en-us/reference/engine/datatypes/User) , userIds :[{any}](/docs/en-us/luau/tables#arrays)

) :[{any}](/docs/en-us/luau/tables#arrays)

Parameters

|

requesterUserId :[User](/docs/en-us/reference/engine/datatypes/User)

 |
|

userIds :[{any}](/docs/en-us/luau/tables#arrays)

 |

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Code Samples

CanUsersDirectChatAsync

```

local TextChatService = game:GetService("TextChatService")

local directChatParticipants = TextChatService:CanUsersDirectChatAsync(userId1, { userId2 })

-- Check for eligible participants

if #directChatParticipants > 0 then

	local directChannel = Instance.new("TextChannel")

	directChannel.Parent = TextChatService

	for _, participant in directChatParticipants do

		directChannel:AddUserAsync(participant)

	end

	return directChannel

end

warn("Could not create TextChannel. Not enough eligible users.")

return nil

```

Provide feedback

---

DisplayBubble

Capabilities: Chat

TextChatService:DisplayBubble (

partOrCharacter :[Instance](/docs/en-us/reference/engine/datatypes/Instance) , message :[string](/docs/en-us/luau/strings)

) : ()

Parameters

|

partOrCharacter :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |
|

message :[string](/docs/en-us/luau/strings)

 |

Returns

()

Provide feedback

---

GetChatGroupsAsync

Yields

Capabilities: Chat

TextChatService:GetChatGroupsAsync (players : Instances ) :[{any}](/docs/en-us/luau/tables#arrays)

Parameters

|

players : Instances

 |

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Code Samples

TeleportPlayerToBestChatServer

```

-- Server Script

local TextChatService = game:GetService("TextChatService")

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

		return TextChatService:GetChatGroupsAsync({ player })

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

local TextChatService = game:GetService("TextChatService")

local Players = game:GetService("Players")

local players = Players:GetPlayers()

local success, chatGroups = pcall(function()

  return TextChatService:GetChatGroupsAsync(players)

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

Events

BubbleDisplayed

Capabilities: Chat

TextChatService.BubbleDisplayed (

partOrCharacter :[Instance](/docs/en-us/reference/engine/datatypes/Instance) , textChatMessage :[TextChatMessage](/docs/en-us/reference/engine/classes/TextChatMessage)

) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

partOrCharacter :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |
|

textChatMessage :[TextChatMessage](/docs/en-us/reference/engine/classes/TextChatMessage)

 |

Provide feedback

---

MessageReceived

Capabilities: Chat

TextChatService.MessageReceived (textChatMessage :[TextChatMessage](/docs/en-us/reference/engine/classes/TextChatMessage) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

textChatMessage :[TextChatMessage](/docs/en-us/reference/engine/classes/TextChatMessage)

 |

Provide feedback

---

SendingMessage

Capabilities: Chat

TextChatService.SendingMessage (textChatMessage :[TextChatMessage](/docs/en-us/reference/engine/classes/TextChatMessage) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

textChatMessage :[TextChatMessage](/docs/en-us/reference/engine/classes/TextChatMessage)

 |

Provide feedback

---

Callbacks

OnBubbleAdded

Capabilities: Chat

TextChatService.OnBubbleAdded (

message :[TextChatMessage](/docs/en-us/reference/engine/classes/TextChatMessage) , adornee :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

) :[Tuple](/docs/en-us/luau/tuples)

Parameters

|

message :[TextChatMessage](/docs/en-us/reference/engine/classes/TextChatMessage)

 |
|

adornee :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |

Returns

[Tuple](/docs/en-us/luau/tuples)

Provide feedback

---

OnChatWindowAdded

Capabilities: Chat

TextChatService.OnChatWindowAdded (message :[TextChatMessage](/docs/en-us/reference/engine/classes/TextChatMessage) ) :[Tuple](/docs/en-us/luau/tuples)

Parameters

|

message :[TextChatMessage](/docs/en-us/reference/engine/classes/TextChatMessage)

 |

Returns

[Tuple](/docs/en-us/luau/tuples)

Provide feedback

---

OnIncomingMessage

Capabilities: Chat

TextChatService.OnIncomingMessage (message :[TextChatMessage](/docs/en-us/reference/engine/classes/TextChatMessage) ) :[Tuple](/docs/en-us/luau/tuples)

Parameters

|

message :[TextChatMessage](/docs/en-us/reference/engine/classes/TextChatMessage)

 |

Returns

[Tuple](/docs/en-us/luau/tuples)

Provide feedback

---

Jump to

▼

TextChatService

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Callbacks](#summary-callbacks)

[Properties](#properties)

[ChatTranslationEnabled](#ChatTranslationEnabled)

[ChatVersion](#ChatVersion)

[CreateDefaultCommands](#CreateDefaultCommands)

[CreateDefaultTextChannels](#CreateDefaultTextChannels)

[PlatformIntegratedChat](#PlatformIntegratedChat)

[Methods](#methods)

[CanUserChatAsync()](#CanUserChatAsync)

[CanUsersChatAsync()](#CanUsersChatAsync)

[CanUsersDirectChatAsync()](#CanUsersDirectChatAsync)

[DisplayBubble()](#DisplayBubble)

[GetChatGroupsAsync()](#GetChatGroupsAsync)

[Events](#events)

[BubbleDisplayed](#BubbleDisplayed)

[MessageReceived](#MessageReceived)

[SendingMessage](#SendingMessage)

[Callbacks](#callbacks)

[OnBubbleAdded()](#OnBubbleAdded)

[OnChatWindowAdded()](#OnChatWindowAdded)

[OnIncomingMessage()](#OnIncomingMessage)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
