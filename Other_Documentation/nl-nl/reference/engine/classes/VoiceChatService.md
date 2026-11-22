<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/VoiceChatService -->

VoiceChatService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [VoiceChatService](/docs/nl-nl/reference/engine/classes/VoiceChatService)

Nederlands

Feedback

Engine-klasse

VoiceChatService

Niet maakbaar

Service

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/VoiceChatService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[DefaultDistanceAttenuation](#DefaultDistanceAttenuation) :[Enum.VoiceChatDistanceAttenuationType](/docs/nl-nl/reference/engine/enums/VoiceChatDistanceAttenuationType)

 |
| --- | --- |
|

[EnableDefaultVoice](#EnableDefaultVoice) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[EnableVoiceVolumeControls](#EnableVoiceVolumeControls) :[Enum.RolloutState](/docs/nl-nl/reference/engine/enums/RolloutState)

 |
|

[UseAudioApi](#UseAudioApi) :[Enum.AudioApiRollout](/docs/nl-nl/reference/engine/enums/AudioApiRollout)

 |

Methoden

|

[GetChatGroupsAsync](#GetChatGroupsAsync) (players :  Instances ) :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[IsVoiceEnabledForUserIdAsync](#IsVoiceEnabledForUserIdAsync) (userId :  [User](/docs/nl-nl/reference/engine/datatypes/User) ) :[boolean](/docs/nl-nl/luau/booleans)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

DefaultDistanceAttenuation

Parallel lezen

Mogelijkheden: Audio, Chat, PluginOrOpenCloud

VoiceChatService.DefaultDistanceAttenuation :[Enum.VoiceChatDistanceAttenuationType](/docs/nl-nl/reference/engine/enums/VoiceChatDistanceAttenuationType)

Feedback geven

---

EnableDefaultVoice

Parallel lezen

Mogelijkheden: Audio, Chat, PluginOrOpenCloud

VoiceChatService.EnableDefaultVoice :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

EnableVoiceVolumeControls

Roblox-scriptbeveiliging

Parallel lezen

Mogelijkheden: Audio, Chat

VoiceChatService.EnableVoiceVolumeControls :[Enum.RolloutState](/docs/nl-nl/reference/engine/enums/RolloutState)

Feedback geven

---

UseAudioApi

Parallel lezen

Mogelijkheden: Audio, Chat, PluginOrOpenCloud

VoiceChatService.UseAudioApi :[Enum.AudioApiRollout](/docs/nl-nl/reference/engine/enums/AudioApiRollout)

Feedback geven

---

Methoden

GetChatGroupsAsync

Opbrengst

Mogelijkheden: Audio, Chat

VoiceChatService:GetChatGroupsAsync (players : Instances ) :[{any}](/docs/nl-nl/luau/tables#arrays)

Parameters

|

players : Instances

 |

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Codevoorbeelden

TeleportSpelerNaarBesteChatServer

```

-- Server Script

local VoiceChatService = game:GetService("VoiceChatService")

local TeleportService = game:GetService("TeleportService")

local Players = game:GetService("Players")

local TARGET_PLACE_ID = 1234567890 -- Bestemmingsplaats ID

--[[

	Stubbed universe-brede serverstatus.

	In de praktijk kan deze data worden opgeslagen en bijgewerkt met behulp van MemoryStore

	of een ander backend-systeem.

	Voorbeeldvorm:

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

local VoiceChatService = game:GetService("VoiceChatService")

local Players = game:GetService("Players")

local players = Players:GetPlayers()

local success, chatGroups = pcall(function()

	return VoiceChatService:GetChatGroupsAsync(players)

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

IsVoiceEnabledForUserIdAsync

Opbrengst

Mogelijkheden: Audio, Chat

VoiceChatService:IsVoiceEnabledForUserIdAsync (userId :[User](/docs/nl-nl/reference/engine/datatypes/User) ) :[boolean](/docs/nl-nl/luau/booleans)

Parameters

|

userId :[User](/docs/nl-nl/reference/engine/datatypes/User)

 |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

Is Voice Enabled For User Id Async

```

local Players = game:GetService("Players")

local VoiceChatService = game:GetService("VoiceChatService")

local localPlayer = Players.LocalPlayer

local success, enabled = pcall(function()

	return VoiceChatService:IsVoiceEnabledForUserIdAsync(localPlayer.UserId)

end)

if success and enabled then

	print("Stemchat ingeschakeld!")

end

```

Feedback geven

---

Ga naar

▼

VoiceChatService

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[DefaultDistanceAttenuation](#DefaultDistanceAttenuation)

[EnableDefaultVoice](#EnableDefaultVoice)

[EnableVoiceVolumeControls](#EnableVoiceVolumeControls)

[UseAudioApi](#UseAudioApi)

[Methoden](#methods)

[GetChatGroupsAsync()](#GetChatGroupsAsync)

[IsVoiceEnabledForUserIdAsync()](#IsVoiceEnabledForUserIdAsync)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
