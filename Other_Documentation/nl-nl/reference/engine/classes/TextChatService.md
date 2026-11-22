<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/TextChatService -->

TextChatService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService)

Nederlands

Feedback

Engine-klasse

TextChatService

Niet maakbaar

Service

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/TextChatService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[ChatTranslationEnabled](#ChatTranslationEnabled) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |
|

[ChatVersion](#ChatVersion) :[Enum.ChatVersion](/docs/nl-nl/reference/engine/enums/ChatVersion)

Verouderd

 |
|

[CreateDefaultCommands](#CreateDefaultCommands) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[CreateDefaultTextChannels](#CreateDefaultTextChannels) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[PlatformIntegratedChat](#PlatformIntegratedChat) :[Enum.RolloutState](/docs/nl-nl/reference/engine/enums/RolloutState)

 |

Methoden

|

[CanUserChatAsync](#CanUserChatAsync) (userId :  [User](/docs/nl-nl/reference/engine/datatypes/User) ) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[CanUsersChatAsync](#CanUsersChatAsync) (userIdFrom :  [User](/docs/nl-nl/reference/engine/datatypes/User) , userIdTo :  [User](/docs/nl-nl/reference/engine/datatypes/User) ) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[CanUsersDirectChatAsync](#CanUsersDirectChatAsync) (requesterUserId :  [User](/docs/nl-nl/reference/engine/datatypes/User) , userIds :  [{any}](/docs/nl-nl/luau/tables#arrays) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[DisplayBubble](#DisplayBubble) (partOrCharacter :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) , message :  [string](/docs/nl-nl/luau/strings) ) : ()

 |
|

[GetChatGroupsAsync](#GetChatGroupsAsync) (players :  Instances ) :[{any}](/docs/nl-nl/luau/tables#arrays)

 |

Evenementen

|

[BubbleDisplayed](#BubbleDisplayed) (partOrCharacter :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) , textChatMessage :  [TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[MessageReceived](#MessageReceived) (textChatMessage :  [TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[SendingMessage](#SendingMessage) (textChatMessage :  [TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Callbacks

|

[OnBubbleAdded](#OnBubbleAdded) (message :  [TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage) , adornee :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[Tuple](/docs/nl-nl/luau/tuples)

 |
|

[OnChatWindowAdded](#OnChatWindowAdded) (message :  [TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage) ) :[Tuple](/docs/nl-nl/luau/tuples)

 |
|

[OnIncomingMessage](#OnIncomingMessage) (message :  [TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage) ) :[Tuple](/docs/nl-nl/luau/tuples)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

ChatTranslationEnabled

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Chat

TextChatService.ChatTranslationEnabled :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

ChatVersion

Verouderd

Details weergeven

---

CreateDefaultCommands

Parallel lezen

Mogelijkheden: Chat

TextChatService.CreateDefaultCommands :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

CreateDefaultTextChannels

Parallel lezen

Mogelijkheden: Chat

TextChatService.CreateDefaultTextChannels :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

PlatformIntegratedChat

Roblox-scriptbeveiliging

Parallel lezen

Mogelijkheden: Chat

TextChatService.PlatformIntegratedChat :[Enum.RolloutState](/docs/nl-nl/reference/engine/enums/RolloutState)

Feedback geven

---

Methoden

CanUserChatAsync

Opbrengst

Mogelijkheden: Chat

TextChatService:CanUserChatAsync (userId :[User](/docs/nl-nl/reference/engine/datatypes/User) ) :[boolean](/docs/nl-nl/luau/booleans)

Parameters

|

userId :[User](/docs/nl-nl/reference/engine/datatypes/User)

 |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

CanUsersChatAsync

Opbrengst

Mogelijkheden: Chat

TextChatService:CanUsersChatAsync (

userIdFrom :[User](/docs/nl-nl/reference/engine/datatypes/User) , userIdTo :[User](/docs/nl-nl/reference/engine/datatypes/User)

) :[boolean](/docs/nl-nl/luau/booleans)

Parameters

|

userIdFrom :[User](/docs/nl-nl/reference/engine/datatypes/User)

 |
|

userIdTo :[User](/docs/nl-nl/reference/engine/datatypes/User)

 |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

CanUsersDirectChatAsync

Opbrengst

Mogelijkheden: Chat

TextChatService:CanUsersDirectChatAsync (

requesterUserId :[User](/docs/nl-nl/reference/engine/datatypes/User) , userIds :[{any}](/docs/nl-nl/luau/tables#arrays)

) :[{any}](/docs/nl-nl/luau/tables#arrays)

Parameters

|

requesterUserId :[User](/docs/nl-nl/reference/engine/datatypes/User)

 |
|

userIds :[{any}](/docs/nl-nl/luau/tables#arrays)

 |

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Codevoorbeelden

CanUsersDirectChatAsync

```

local TextChatService = game:GetService("TextChatService")

local directChatParticipants = TextChatService:CanUsersDirectChatAsync(userId1, { userId2 })

-- Controleer op in aanmerking komende deelnemers

if #directChatParticipants > 0 then

	local directChannel = Instance.new("TextChannel")

	directChannel.Parent = TextChatService

	for _, participant in directChatParticipants do

		directChannel:AddUserAsync(participant)

	end

	return directChannel

end

warn("Kon geen TextChannel maken. Niet genoeg in aanmerking komende gebruikers.")

return nil

```

Feedback geven

---

DisplayBubble

Mogelijkheden: Chat

TextChatService:DisplayBubble (

partOrCharacter :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) , message :[string](/docs/nl-nl/luau/strings)

) : ()

Parameters

|

partOrCharacter :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
|

message :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

()

Feedback geven

---

GetChatGroupsAsync

Opbrengst

Mogelijkheden: Chat

TextChatService:GetChatGroupsAsync (players : Instances ) :[{any}](/docs/nl-nl/luau/tables#arrays)

Parameters

|

players : Instances

 |

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Codevoorbeelden

TeleporteerSpelerNaarBesteChatServer

```

-- Server Script

local TextChatService = game:GetService("TextChatService")

local TeleportService = game:GetService("TeleportService")

local Players = game:GetService("Players")

local TARGET_PLACE_ID = 1234567890 -- Bestemmingsplaats ID

--[[

	Stubbed universe-brede serverstatus.

	In de praktijk kunnen deze gegevens worden opgeslagen en bijgewerkt met behulp van MemoryStore

	of een ander backend-systeem.

	Voorbeeldstructuur:

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

		warn("Kon chatgroepen voor speler niet ophalen:", player.UserId)

		return

	end

	-- Verzamel alle chatgroep-ID's waarvoor de speler in aanmerking komt

	local playerGroupIds = {}

	for _, group in ipairs(chatGroups) do

		for _, groupId in ipairs(group) do

			playerGroupIds[groupId] = true

		end

	end

	local bestServer = nil

	local bestUserCount = 0

	-- Kies de server met het hoogste aantal compatibele gebruikers

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

		warn("Geen geschikte server gevonden voor speler:", player.UserId)

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

		warn("Teleporteren mislukt:", err)

	end

end

Players.PlayerAdded:Connect(teleportPlayerToBestServer)

```

Krijg Chatgroepen Asynchroon

```

local TextChatService = game:GetService("TextChatService")

local Players = game:GetService("Players")

local players = Players:GetPlayers()

local success, chatGroups = pcall(function()

  return TextChatService:GetChatGroupsAsync(players)

end)

if not success then

  warn("Kon chatgroepen niet ophalen")

  return

end

for _, group in ipairs(chatGroups) do

  -- Elke groep bevat chatgroep ID-strings.

  -- Spelers die een overeenkomende groep ID delen, kunnen met elkaar chatten.

  for _, groupId in ipairs(group) do

    print("Chatgroep ID:", groupId)

  end

end

```

Feedback geven

---

Evenementen

BubbleDisplayed

Mogelijkheden: Chat

TextChatService.BubbleDisplayed (

partOrCharacter :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) , textChatMessage :[TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage)

) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

partOrCharacter :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
|

textChatMessage :[TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage)

 |

Feedback geven

---

MessageReceived

Mogelijkheden: Chat

TextChatService.MessageReceived (textChatMessage :[TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

textChatMessage :[TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage)

 |

Feedback geven

---

SendingMessage

Mogelijkheden: Chat

TextChatService.SendingMessage (textChatMessage :[TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

textChatMessage :[TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage)

 |

Feedback geven

---

Callbacks

OnBubbleAdded

Mogelijkheden: Chat

TextChatService.OnBubbleAdded (

message :[TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage) , adornee :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

) :[Tuple](/docs/nl-nl/luau/tuples)

Parameters

|

message :[TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage)

 |
|

adornee :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Feedback geven

---

OnChatWindowAdded

Mogelijkheden: Chat

TextChatService.OnChatWindowAdded (message :[TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage) ) :[Tuple](/docs/nl-nl/luau/tuples)

Parameters

|

message :[TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage)

 |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Feedback geven

---

OnIncomingMessage

Mogelijkheden: Chat

TextChatService.OnIncomingMessage (message :[TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage) ) :[Tuple](/docs/nl-nl/luau/tuples)

Parameters

|

message :[TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage)

 |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Feedback geven

---

Ga naar

▼

TextChatService

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Callbacks](#summary-callbacks)

[Eigenschappen](#properties)

[ChatTranslationEnabled](#ChatTranslationEnabled)

[ChatVersion](#ChatVersion)

[CreateDefaultCommands](#CreateDefaultCommands)

[CreateDefaultTextChannels](#CreateDefaultTextChannels)

[PlatformIntegratedChat](#PlatformIntegratedChat)

[Methoden](#methods)

[CanUserChatAsync()](#CanUserChatAsync)

[CanUsersChatAsync()](#CanUsersChatAsync)

[CanUsersDirectChatAsync()](#CanUsersDirectChatAsync)

[DisplayBubble()](#DisplayBubble)

[GetChatGroupsAsync()](#GetChatGroupsAsync)

[Evenementen](#events)

[BubbleDisplayed](#BubbleDisplayed)

[MessageReceived](#MessageReceived)

[SendingMessage](#SendingMessage)

[Callbacks](#callbacks)

[OnBubbleAdded()](#OnBubbleAdded)

[OnChatWindowAdded()](#OnChatWindowAdded)

[OnIncomingMessage()](#OnIncomingMessage)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
