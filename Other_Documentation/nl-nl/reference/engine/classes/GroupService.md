<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/GroupService -->

GroupService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [GroupService](/docs/nl-nl/reference/engine/classes/GroupService)

Nederlands

Feedback

Engine-klasse

GroupService

Niet maakbaar

Service

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/GroupService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[GetAlliesAsync](#GetAlliesAsync) (groupId :  [number](/docs/nl-nl/luau/numbers) ) :[StandardPages](/docs/nl-nl/reference/engine/classes/StandardPages)

 |
| --- | --- |
|

[GetEnemiesAsync](#GetEnemiesAsync) (groupId :  [number](/docs/nl-nl/luau/numbers) ) :[StandardPages](/docs/nl-nl/reference/engine/classes/StandardPages)

 |
|

[GetGroupInfoAsync](#GetGroupInfoAsync) (groupId :  [number](/docs/nl-nl/luau/numbers) ) : Variant

 |
|

[GetGroupsAsync](#GetGroupsAsync) (userId :  [User](/docs/nl-nl/reference/engine/datatypes/User) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[GetRolesInGroupAsync](#GetRolesInGroupAsync) (userId :  [User](/docs/nl-nl/reference/engine/datatypes/User) , groupId :  [number](/docs/nl-nl/luau/numbers) ) : Variant

 |
|

[PromptJoinAsync](#PromptJoinAsync) (groupId :  [number](/docs/nl-nl/luau/numbers) ) :[Enum.GroupMembershipStatus](/docs/nl-nl/reference/engine/enums/GroupMembershipStatus)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Groep Bondgenoot/Vijand Controle

```

local GroupService = game:GetService("GroupService")

local Players = game:GetService("Players")

-- Definieer hier de groeps-ID

local GROUP_ID = 271454

-- Hulpfunctie voor het omgaan met pagina's

local function pagesToArray(pages)

	local array = {}

	while true do

		for _, v in ipairs(pages:GetCurrentPage()) do

			table.insert(array, v)

		end

		if pages.IsFinished then

			break

		end

		pages:AdvanceToNextPageAsync()

	end

	return array

end

-- Verkrijg lijsten van bondgenoten en vijanden

local alliesPages = GroupService:GetAlliesAsync(GROUP_ID)

local enemiesPages = GroupService:GetEnemiesAsync(GROUP_ID)

-- Omzetten naar array

local allies = pagesToArray(alliesPages)

local enemies = pagesToArray(enemiesPages)

local function playerAdded(player)

	-- Controleer of de speler in de groep zit

	if player:IsInGroupAsync(GROUP_ID) then

		print(player.Name .. " is een lid!")

	else

		local isAlly, isEnemy = false, false

		-- Controleer of de speler in een van de bondgenootgroepen zit

		for _, groupInfo in ipairs(allies) do

			local groupId = groupInfo.Id

			if player:IsInGroupAsync(groupId) then

				isAlly = true

				break

			end

		end

		-- Controleer of de speler in een van de vijandgroepen zit

		for _, groupInfo in ipairs(enemies) do

			local groupId = groupInfo.Id

			if player:IsInGroupAsync(groupId) then

				isEnemy = true

				break

			end

		end

		if isAlly and not isEnemy then

			print(player.Name .. " is een bondgenoot!")

		elseif isEnemy and not isAlly then

			print(player.Name .. " is een vijand!")

		elseif isEnemy and isAlly then

			print(player.Name .. " is zowel een bondgenoot als een vijand!")

		else

			print(player.Name .. " is noch een bondgenoot noch een vijand!")

		end

	end

end

-- Luister naar nieuwe spelers die worden toegevoegd

Players.PlayerAdded:Connect(playerAdded)

-- Behandel spelers die al in het spel zijn

for _, player in ipairs(Players:GetPlayers()) do

	playerAdded(player)

end

```

---

API-referentie

Methoden

GetAlliesAsync

Opbrengst

Mogelijkheden: Groups

GroupService:GetAlliesAsync (groupId :[number](/docs/nl-nl/luau/numbers) ) :[StandardPages](/docs/nl-nl/reference/engine/classes/StandardPages)

Parameters

|

groupId :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[StandardPages](/docs/nl-nl/reference/engine/classes/StandardPages)

Codevoorbeelden

GroupService:GetAlliesAsync

```

local Players = game:GetService("Players")

local GroupService = game:GetService("GroupService")

local GROUP_ID = 57

-- maakt een tabel van alle bondgenoten van een gegeven groep

local allies = {}

local pages = GroupService:GetAlliesAsync(GROUP_ID)

while true do

	for _, group in pairs(pages:GetCurrentPage()) do

		table.insert(allies, group)

	end

	if pages.IsFinished then

		break

	end

	pages:AdvanceToNextPageAsync()

end

function onPlayerAdded(player)

	for _, group in pairs(allies) do

		if player:IsInGroupAsync(group.Id) then

			print("Speler is een bondgenoot!")

			break

		end

	end

end

Players.PlayerAdded:Connect(onPlayerAdded)

-- verwerk spelers die zich hebben aangemeld terwijl de bondgenotenlijst nog aan het laden was

for _, player in pairs(Players:GetPlayers()) do

	onPlayerAdded(player)

end

```

Groep Bondgenoot/Vijand Controle

```

local GroupService = game:GetService("GroupService")

local Players = game:GetService("Players")

-- Definieer hier de groeps-ID

local GROUP_ID = 271454

-- Hulpfunctie voor het omgaan met pagina's

local function pagesToArray(pages)

	local array = {}

	while true do

		for _, v in ipairs(pages:GetCurrentPage()) do

			table.insert(array, v)

		end

		if pages.IsFinished then

			break

		end

		pages:AdvanceToNextPageAsync()

	end

	return array

end

-- Verkrijg lijsten van bondgenoten en vijanden

local alliesPages = GroupService:GetAlliesAsync(GROUP_ID)

local enemiesPages = GroupService:GetEnemiesAsync(GROUP_ID)

-- Omzetten naar array

local allies = pagesToArray(alliesPages)

local enemies = pagesToArray(enemiesPages)

local function playerAdded(player)

	-- Controleer of de speler in de groep zit

	if player:IsInGroupAsync(GROUP_ID) then

		print(player.Name .. " is een lid!")

	else

		local isAlly, isEnemy = false, false

		-- Controleer of de speler in een van de bondgenootgroepen zit

		for _, groupInfo in ipairs(allies) do

			local groupId = groupInfo.Id

			if player:IsInGroupAsync(groupId) then

				isAlly = true

				break

			end

		end

		-- Controleer of de speler in een van de vijandgroepen zit

		for _, groupInfo in ipairs(enemies) do

			local groupId = groupInfo.Id

			if player:IsInGroupAsync(groupId) then

				isEnemy = true

				break

			end

		end

		if isAlly and not isEnemy then

			print(player.Name .. " is een bondgenoot!")

		elseif isEnemy and not isAlly then

			print(player.Name .. " is een vijand!")

		elseif isEnemy and isAlly then

			print(player.Name .. " is zowel een bondgenoot als een vijand!")

		else

			print(player.Name .. " is noch een bondgenoot noch een vijand!")

		end

	end

end

-- Luister naar nieuwe spelers die worden toegevoegd

Players.PlayerAdded:Connect(playerAdded)

-- Behandel spelers die al in het spel zijn

for _, player in ipairs(Players:GetPlayers()) do

	playerAdded(player)

end

```

Feedback geven

---

GetEnemiesAsync

Opbrengst

Mogelijkheden: Groups

GroupService:GetEnemiesAsync (groupId :[number](/docs/nl-nl/luau/numbers) ) :[StandardPages](/docs/nl-nl/reference/engine/classes/StandardPages)

Parameters

|

groupId :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[StandardPages](/docs/nl-nl/reference/engine/classes/StandardPages)

Codevoorbeelden

GroupService:GetEnemiesAsync

```

local Players = game:GetService("Players")

local GroupService = game:GetService("GroupService")

local GROUP_ID = 57

-- maakt een lijst van alle vijanden van een gegeven groep

local enemies = {}

local pages = GroupService:GetEnemiesAsync(GROUP_ID)

while true do

	for _, group in pairs(pages:GetCurrentPage()) do

		table.insert(enemies, group)

	end

	if pages.IsFinished then

		break

	end

	pages:AdvanceToNextPageAsync()

end

function onPlayerAdded(player)

	for _, enemyGroup in pairs(enemies) do

		if player:IsInGroupAsync(enemyGroup.Id) then

			print("Speler is een vijand!")

			break

		end

	end

end

Players.PlayerAdded:Connect(onPlayerAdded)

-- verwerk spelers die zijn toegetreden terwijl de vijandenlijst nog aan het laden was

for _, player in pairs(Players:GetPlayers()) do

	onPlayerAdded(player)

end

```

Groep Bondgenoot/Vijand Controle

```

local GroupService = game:GetService("GroupService")

local Players = game:GetService("Players")

-- Definieer hier de groeps-ID

local GROUP_ID = 271454

-- Hulpfunctie voor het omgaan met pagina's

local function pagesToArray(pages)

	local array = {}

	while true do

		for _, v in ipairs(pages:GetCurrentPage()) do

			table.insert(array, v)

		end

		if pages.IsFinished then

			break

		end

		pages:AdvanceToNextPageAsync()

	end

	return array

end

-- Verkrijg lijsten van bondgenoten en vijanden

local alliesPages = GroupService:GetAlliesAsync(GROUP_ID)

local enemiesPages = GroupService:GetEnemiesAsync(GROUP_ID)

-- Omzetten naar array

local allies = pagesToArray(alliesPages)

local enemies = pagesToArray(enemiesPages)

local function playerAdded(player)

	-- Controleer of de speler in de groep zit

	if player:IsInGroupAsync(GROUP_ID) then

		print(player.Name .. " is een lid!")

	else

		local isAlly, isEnemy = false, false

		-- Controleer of de speler in een van de bondgenootgroepen zit

		for _, groupInfo in ipairs(allies) do

			local groupId = groupInfo.Id

			if player:IsInGroupAsync(groupId) then

				isAlly = true

				break

			end

		end

		-- Controleer of de speler in een van de vijandgroepen zit

		for _, groupInfo in ipairs(enemies) do

			local groupId = groupInfo.Id

			if player:IsInGroupAsync(groupId) then

				isEnemy = true

				break

			end

		end

		if isAlly and not isEnemy then

			print(player.Name .. " is een bondgenoot!")

		elseif isEnemy and not isAlly then

			print(player.Name .. " is een vijand!")

		elseif isEnemy and isAlly then

			print(player.Name .. " is zowel een bondgenoot als een vijand!")

		else

			print(player.Name .. " is noch een bondgenoot noch een vijand!")

		end

	end

end

-- Luister naar nieuwe spelers die worden toegevoegd

Players.PlayerAdded:Connect(playerAdded)

-- Behandel spelers die al in het spel zijn

for _, player in ipairs(Players:GetPlayers()) do

	playerAdded(player)

end

```

Feedback geven

---

GetGroupInfoAsync

Opbrengst

Mogelijkheden: Groups

Cloud-API

GroupService:GetGroupInfoAsync (groupId :[number](/docs/nl-nl/luau/numbers) ) : Variant

Parameters

|

groupId :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

Variant

Codevoorbeelden

GroupService:GetGroupInfoAsync

```

local GroupService = game:GetService("GroupService")

local GROUP_ID = 377251

local group = GroupService:GetGroupInfoAsync(GROUP_ID)

print(group.Name .. " heeft de volgende rollen:")

for _, role in ipairs(group.Roles) do

	print("Rang " .. role.Rank .. ": " .. role.Name)

end

```

Laad Groep Embleem

```

local GroupService = game:GetService("GroupService")

local function getEmblemAsync(groupId)

	local groupInfo = GroupService:GetGroupInfoAsync(groupId)

	return groupInfo.EmblemUrl

end

local part = Instance.new("Part")

part.Anchored = true

part.CanCollide = false

part.Size = Vector3.new(5, 5, 1)

part.Position = Vector3.new(0, 5, 0)

local decal = Instance.new("Decal")

decal.Parent = part

part.Parent = workspace

decal.ColorMapContent = Content.fromUri(getEmblemAsync(377251))

```

Feedback geven

---

GetGroupsAsync

Opbrengst

Mogelijkheden: Groups

GroupService:GetGroupsAsync (userId :[User](/docs/nl-nl/reference/engine/datatypes/User) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

Parameters

|

userId :[User](/docs/nl-nl/reference/engine/datatypes/User)

 |

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Codevoorbeelden

De Groepen waar een Gebruiker Lid van is

```

local GroupService = game:GetService("GroupService")

local Players = game:GetService("Players")

local function playerAdded(player)

	-- laad een lijst met informatie over alle groepen waarvan de speler lid is

	local groups = GroupService:GetGroupsAsync(player.UserId)

	for _, groupInfo in pairs(groups) do

		for key, value in pairs(groupInfo) do

			print(key .. ": " .. tostring(value))

		end

		print("--")

	end

end

Players.PlayerAdded:Connect(playerAdded)

-- door bestaande spelers gaan

for _, player in pairs(Players:GetPlayers()) do

	playerAdded(player)

end

```

Feedback geven

---

GetRolesInGroupAsync

Opbrengst

Mogelijkheden: Groups

Cloud-API

GroupService:GetRolesInGroupAsync (

userId :[User](/docs/nl-nl/reference/engine/datatypes/User) , groupId :[number](/docs/nl-nl/luau/numbers)

) : Variant

Parameters

|

userId :[User](/docs/nl-nl/reference/engine/datatypes/User)

 |
|

groupId :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

Variant

Codevoorbeelden

Krijg Rollen In Groep Async

```

local GroupService = game:GetService("GroupService")

local Players = game:GetService("Players")

local GROUP_ID = 377251

local localPlayer = Players.LocalPlayer

local result = GroupService:GetRolesInGroupAsync(localPlayer.UserId, GROUP_ID)

if result.IsMember then

    print("Gebruiker is een lid met", #result.Roles, "rol(len)")

    for _, role in ipairs(result.Roles) do

        print(role.Name, "rang", role.Rank)

    end

else

    print("Gebruiker is geen lid")

end

```

Feedback geven

---

PromptJoinAsync

Opbrengst

Mogelijkheden: Groups

GroupService:PromptJoinAsync (groupId :[number](/docs/nl-nl/luau/numbers) ) :[Enum.GroupMembershipStatus](/docs/nl-nl/reference/engine/enums/GroupMembershipStatus)

Parameters

|

groupId :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[Enum.GroupMembershipStatus](/docs/nl-nl/reference/engine/enums/GroupMembershipStatus)

Codevoorbeelden

Een speler vragen om lid te worden van een groep

```

local GroupService = game:GetService("GroupService")

local GROUP_ID = 377251

-- Dit moet worden gedaan in een script dat op de client draait

local success, result = pcall(function()

    return GroupService:PromptJoinAsync(GROUP_ID)

end)

if success then

    if result == Enum.GroupMembershipStatus.Joined then

        print("Speler is lid geworden van de groep!")

    elseif result == Enum.GroupMembershipStatus.JoinRequestPending then

        print("Speler heeft een openstaande lidmaatschapsaanvraag")

    elseif result == Enum.GroupMembershipStatus.AlreadyMember then

        print("Al lid")

    else

        print("Niet lid geworden of niet in aanmerking")

    end

else

    warn("Prompt mislukt:", result)

end

```

Feedback geven

---

Ga naar

▼

GroupService

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[GetAlliesAsync()](#GetAlliesAsync)

[GetEnemiesAsync()](#GetEnemiesAsync)

[GetGroupInfoAsync()](#GetGroupInfoAsync)

[GetGroupsAsync()](#GetGroupsAsync)

[GetRolesInGroupAsync()](#GetRolesInGroupAsync)

[PromptJoinAsync()](#PromptJoinAsync)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
