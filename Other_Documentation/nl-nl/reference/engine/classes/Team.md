<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Team -->

Team | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [Team](/docs/nl-nl/reference/engine/classes/Team)

Nederlands

Feedback

Engine-klasse

Team

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Team)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[AutoAssignable](#AutoAssignable) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |
|

[AutoColorCharacters](#AutoColorCharacters) :[boolean](/docs/nl-nl/luau/booleans)

Verouderd

 |
|

[Score](#Score) :[number](/docs/nl-nl/luau/numbers)

Verouderd

 |
|

[TeamColor](#TeamColor) :[BrickColor](/docs/nl-nl/reference/engine/datatypes/BrickColor)

 |

Methoden

|

[GetPlayers](#GetPlayers) () : {[Player](/docs/nl-nl/reference/engine/classes/Player) }

 |

Evenementen

|

[PlayerAdded](#PlayerAdded) (player :  [Player](/docs/nl-nl/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[PlayerRemoved](#PlayerRemoved) (player :  [Player](/docs/nl-nl/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Eenvoudige Team Herverdeling

```

local Teams = game:GetService("Teams")

-- maak twee teams

local redTeam = Instance.new("Team")

redTeam.TeamColor = BrickColor.new("Heldere rood")

redTeam.AutoAssignable = true

redTeam.Name = "Rood Team"

redTeam.Parent = Teams

local blueTeam = Instance.new("Team")

blueTeam.TeamColor = BrickColor.new("Heldere blauw")

blueTeam.AutoAssignable = true

blueTeam.Name = "Blauw Team"

blueTeam.Parent = Teams

-- begin met tellen van het aantal spelers in elk team

local numberRed, numberBlue = 0, 0

local function playerAdded(team)

	-- verhoog de telling van het team met 1

	if team == redTeam then

		numberRed = numberRed + 1

	elseif team == blueTeam then

		numberBlue = numberBlue + 1

	end

end

local function playerRemoved(team)

	-- verlaag de telling van het team met 1

	if team == redTeam then

		numberRed = numberRed - 1

	elseif team == blueTeam then

		numberBlue = numberBlue - 1

	end

	-- controleer of de teams ongelijk zijn

	local bigTeam, smallTeam = nil, nil

	if (numberRed - numberBlue) > 2 then

		bigTeam = redTeam

		smallTeam = blueTeam

	elseif (numberBlue - numberRed) > 2 then

		bigTeam = blueTeam

		smallTeam = redTeam

	end

	if bigTeam then

		-- kies een willekeurige speler

		local playerList = bigTeam:GetPlayers()

		local player = playerList[math.random(1, #playerList)]

		-- controleer of de speler bestaat

		if player then

			-- verander het team van de speler

			player.TeamColor = smallTeam.TeamColor

			-- respawn de speler

			player:LoadCharacterAsync()

		end

	end

end

-- luister naar spelers die worden toegevoegd / verwijderd

blueTeam.PlayerAdded:Connect(function(_player)

	playerAdded(blueTeam)

end)

blueTeam.PlayerRemoved:Connect(function(_player)

	playerRemoved(blueTeam)

end)

redTeam.PlayerAdded:Connect(function(_player)

	playerAdded(redTeam)

end)

redTeam.PlayerRemoved:Connect(function(_player)

	playerRemoved(redTeam)

end)

```

Team Kill Check

```

local Players = game:GetService("Players")

function checkTeamKill(playerAttack, playerVictim)

	-- Controleer of de spelers in verschillende teams zitten of neutraal zijn

	if playerAttack.Team ~= playerVictim.Team or playerAttack.Neutral or playerVictim.Neutral then

		return false

	end

	return true

end

local players = Players:GetPlayers()

-- Controleer team killing tussen de eerste en tweede speler

checkTeamKill(players[1], players[2])

```

Deur Alleen Voor Team

```

local Players = game:GetService("Players")

local door = Instance.new("Part")

door.Anchored = true

door.Size = Vector3.new(7, 10, 1)

door.Position = Vector3.new(0, 5, 0)

door.Parent = workspace

local debounce = false

door.Touched:Connect(function(hit)

	if not debounce then

		debounce = true

		if hit then

			local player = Players:GetPlayerFromCharacter(hit.Parent)

			if player and player.TeamColor == BrickColor.new("Bright red") then

				door.Transparency = 0.5

				door.CanCollide = false

				task.wait(3)

				door.Transparency = 0

				door.CanCollide = true

			end

		end

		task.wait(0.5)

		debounce = false

	end

end)

```

Team Herverdeling met Partijintegratie

```

local Teams = game:GetService("Teams")

local Players = game:GetService("Players")

local SocialService = game:GetService("SocialService")

local redTeam = Instance.new("Team")

redTeam.Name = "Rood Team"

redTeam.TeamColor = BrickColor.Red()

redTeam.AutoAssignable = false

redTeam.Parent = Teams

local blueTeam = Instance.new("Team")

blueTeam.Name = "Blauw Team"

blueTeam.TeamColor = BrickColor.Blue()

blueTeam.AutoAssignable = false

blueTeam.Parent = Teams

local function assignPlayerToTeam(player)

	local partyId = player.PartyId

	if partyId == "" then

		assignBalancedTeam(player)

		return

	end

	local teams = { redTeam, blueTeam }

	local matchingTeam = nil

	local partyPlayers = SocialService:GetPlayersByPartyId(partyId)

	for _, partyPlayer in partyPlayers do

		if partyPlayer ~= player and table.find(teams, partyPlayer.Team) then

			matchingTeam = partyPlayer.Team

			break

		end

	end

	if matchingTeam then

		player.Team = matchingTeam

		player.TeamColor = matchingTeam.TeamColor

	else

		assignBalancedTeam(player)

	end

end

function assignBalancedTeam(player)

	local redCount = #redTeam:GetPlayers()

	local blueCount = #blueTeam:GetPlayers()

	local chosenTeam = redCount <= blueCount and redTeam or blueTeam

	player.Team = chosenTeam

	player.TeamColor = chosenTeam.TeamColor

end

local function groupPlayersByParty()

	local seenPartyIds = {}

	local groupedPlayers = {}

	for _, player in Players:GetPlayers() do

		if player.PartyId == "" then

			table.insert(groupedPlayers, { player })

		elseif not table.find(seenPartyIds, player.PartyId) then

			table.insert(seenPartyIds, player.PartyId)

			local partyPlayers = SocialService:GetPlayersByPartyId(player.PartyId)

			table.insert(groupedPlayers, partyPlayers)

		end

	end

	return groupedPlayers

end

-- Roep deze functie aan om teams opnieuw in balans te brengen

local function rebalanceTeams()

	local groups = groupPlayersByParty()

	table.sort(groups, function(a, b)

		return #a > #b

	end)

	for _, player in Players:GetPlayers() do

		player.Team = nil

	end

	for _, group in groups do

		local redCount = #redTeam:GetPlayers()

		local blueCount = #blueTeam:GetPlayers()

		local bestTeam

		if redCount <= blueCount then

			bestTeam = redTeam

		else

			bestTeam = blueTeam

		end

		for _, player in group do

			player.Team = bestTeam

			player.TeamColor = bestTeam.TeamColor

		end

	end

	for _, player in Players:GetPlayers() do

		player:LoadCharacterAsync()

	end

end

Players.PlayerAdded:Connect(function(player)

	assignPlayerToTeam(player)

	player:LoadCharacterAsync()

	player:GetPropertyChangedSignal("PartyId"):Connect(function()

		if player.PartyId ~= "" then

			assignPlayerToTeam(player)

		end

	end)

end)

```

---

API-referentie

Eigenschappen

AutoAssignable

Parallel lezen

Mogelijkheden: Players

Team.AutoAssignable :[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

Eenvoudige Team Herverdeling

```

local Teams = game:GetService("Teams")

-- maak twee teams

local redTeam = Instance.new("Team")

redTeam.TeamColor = BrickColor.new("Heldere rood")

redTeam.AutoAssignable = true

redTeam.Name = "Rood Team"

redTeam.Parent = Teams

local blueTeam = Instance.new("Team")

blueTeam.TeamColor = BrickColor.new("Heldere blauw")

blueTeam.AutoAssignable = true

blueTeam.Name = "Blauw Team"

blueTeam.Parent = Teams

-- begin met tellen van het aantal spelers in elk team

local numberRed, numberBlue = 0, 0

local function playerAdded(team)

	-- verhoog de telling van het team met 1

	if team == redTeam then

		numberRed = numberRed + 1

	elseif team == blueTeam then

		numberBlue = numberBlue + 1

	end

end

local function playerRemoved(team)

	-- verlaag de telling van het team met 1

	if team == redTeam then

		numberRed = numberRed - 1

	elseif team == blueTeam then

		numberBlue = numberBlue - 1

	end

	-- controleer of de teams ongelijk zijn

	local bigTeam, smallTeam = nil, nil

	if (numberRed - numberBlue) > 2 then

		bigTeam = redTeam

		smallTeam = blueTeam

	elseif (numberBlue - numberRed) > 2 then

		bigTeam = blueTeam

		smallTeam = redTeam

	end

	if bigTeam then

		-- kies een willekeurige speler

		local playerList = bigTeam:GetPlayers()

		local player = playerList[math.random(1, #playerList)]

		-- controleer of de speler bestaat

		if player then

			-- verander het team van de speler

			player.TeamColor = smallTeam.TeamColor

			-- respawn de speler

			player:LoadCharacterAsync()

		end

	end

end

-- luister naar spelers die worden toegevoegd / verwijderd

blueTeam.PlayerAdded:Connect(function(_player)

	playerAdded(blueTeam)

end)

blueTeam.PlayerRemoved:Connect(function(_player)

	playerRemoved(blueTeam)

end)

redTeam.PlayerAdded:Connect(function(_player)

	playerAdded(redTeam)

end)

redTeam.PlayerRemoved:Connect(function(_player)

	playerRemoved(redTeam)

end)

```

Feedback geven

---

AutoColorCharacters

Verouderd

Details weergeven

---

Score

Verouderd

Details weergeven

---

TeamColor

Parallel lezen

Mogelijkheden: Players

Team.TeamColor :[BrickColor](/docs/nl-nl/reference/engine/datatypes/BrickColor)

Codevoorbeelden

Deur Alleen Voor Team

```

local Players = game:GetService("Players")

local door = Instance.new("Part")

door.Anchored = true

door.Size = Vector3.new(7, 10, 1)

door.Position = Vector3.new(0, 5, 0)

door.Parent = workspace

local debounce = false

door.Touched:Connect(function(hit)

	if not debounce then

		debounce = true

		if hit then

			local player = Players:GetPlayerFromCharacter(hit.Parent)

			if player and player.TeamColor == BrickColor.new("Bright red") then

				door.Transparency = 0.5

				door.CanCollide = false

				task.wait(3)

				door.Transparency = 0

				door.CanCollide = true

			end

		end

		task.wait(0.5)

		debounce = false

	end

end)

```

Feedback geven

---

Methoden

GetPlayers

Parallel schrijven

Mogelijkheden: Players

Team:GetPlayers () : {[Player](/docs/nl-nl/reference/engine/classes/Player) }

Teruggaves

{[Player](/docs/nl-nl/reference/engine/classes/Player) }

Codevoorbeelden

Teams GetTeams

```

local Teams = game:GetService("Teams")

local teams = Teams:GetTeams()

for _, team in pairs(teams) do

	local players = team:GetPlayers()

	print("Team", team.Name, "heeft", #players, "spelers")

end

```

Feedback geven

---

Evenementen

PlayerAdded

Mogelijkheden: Players

Team.PlayerAdded (player :[Player](/docs/nl-nl/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

player :[Player](/docs/nl-nl/reference/engine/classes/Player)

 |

Codevoorbeelden

Eenvoudige Team Herverdeling

```

local Teams = game:GetService("Teams")

-- maak twee teams

local redTeam = Instance.new("Team")

redTeam.TeamColor = BrickColor.new("Heldere rood")

redTeam.AutoAssignable = true

redTeam.Name = "Rood Team"

redTeam.Parent = Teams

local blueTeam = Instance.new("Team")

blueTeam.TeamColor = BrickColor.new("Heldere blauw")

blueTeam.AutoAssignable = true

blueTeam.Name = "Blauw Team"

blueTeam.Parent = Teams

-- begin met tellen van het aantal spelers in elk team

local numberRed, numberBlue = 0, 0

local function playerAdded(team)

	-- verhoog de telling van het team met 1

	if team == redTeam then

		numberRed = numberRed + 1

	elseif team == blueTeam then

		numberBlue = numberBlue + 1

	end

end

local function playerRemoved(team)

	-- verlaag de telling van het team met 1

	if team == redTeam then

		numberRed = numberRed - 1

	elseif team == blueTeam then

		numberBlue = numberBlue - 1

	end

	-- controleer of de teams ongelijk zijn

	local bigTeam, smallTeam = nil, nil

	if (numberRed - numberBlue) > 2 then

		bigTeam = redTeam

		smallTeam = blueTeam

	elseif (numberBlue - numberRed) > 2 then

		bigTeam = blueTeam

		smallTeam = redTeam

	end

	if bigTeam then

		-- kies een willekeurige speler

		local playerList = bigTeam:GetPlayers()

		local player = playerList[math.random(1, #playerList)]

		-- controleer of de speler bestaat

		if player then

			-- verander het team van de speler

			player.TeamColor = smallTeam.TeamColor

			-- respawn de speler

			player:LoadCharacterAsync()

		end

	end

end

-- luister naar spelers die worden toegevoegd / verwijderd

blueTeam.PlayerAdded:Connect(function(_player)

	playerAdded(blueTeam)

end)

blueTeam.PlayerRemoved:Connect(function(_player)

	playerRemoved(blueTeam)

end)

redTeam.PlayerAdded:Connect(function(_player)

	playerAdded(redTeam)

end)

redTeam.PlayerRemoved:Connect(function(_player)

	playerRemoved(redTeam)

end)

```

Feedback geven

---

PlayerRemoved

Mogelijkheden: Players

Team.PlayerRemoved (player :[Player](/docs/nl-nl/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

player :[Player](/docs/nl-nl/reference/engine/classes/Player)

 |

Codevoorbeelden

Eenvoudige Team Herverdeling

```

local Teams = game:GetService("Teams")

-- maak twee teams

local redTeam = Instance.new("Team")

redTeam.TeamColor = BrickColor.new("Heldere rood")

redTeam.AutoAssignable = true

redTeam.Name = "Rood Team"

redTeam.Parent = Teams

local blueTeam = Instance.new("Team")

blueTeam.TeamColor = BrickColor.new("Heldere blauw")

blueTeam.AutoAssignable = true

blueTeam.Name = "Blauw Team"

blueTeam.Parent = Teams

-- begin met tellen van het aantal spelers in elk team

local numberRed, numberBlue = 0, 0

local function playerAdded(team)

	-- verhoog de telling van het team met 1

	if team == redTeam then

		numberRed = numberRed + 1

	elseif team == blueTeam then

		numberBlue = numberBlue + 1

	end

end

local function playerRemoved(team)

	-- verlaag de telling van het team met 1

	if team == redTeam then

		numberRed = numberRed - 1

	elseif team == blueTeam then

		numberBlue = numberBlue - 1

	end

	-- controleer of de teams ongelijk zijn

	local bigTeam, smallTeam = nil, nil

	if (numberRed - numberBlue) > 2 then

		bigTeam = redTeam

		smallTeam = blueTeam

	elseif (numberBlue - numberRed) > 2 then

		bigTeam = blueTeam

		smallTeam = redTeam

	end

	if bigTeam then

		-- kies een willekeurige speler

		local playerList = bigTeam:GetPlayers()

		local player = playerList[math.random(1, #playerList)]

		-- controleer of de speler bestaat

		if player then

			-- verander het team van de speler

			player.TeamColor = smallTeam.TeamColor

			-- respawn de speler

			player:LoadCharacterAsync()

		end

	end

end

-- luister naar spelers die worden toegevoegd / verwijderd

blueTeam.PlayerAdded:Connect(function(_player)

	playerAdded(blueTeam)

end)

blueTeam.PlayerRemoved:Connect(function(_player)

	playerRemoved(blueTeam)

end)

redTeam.PlayerAdded:Connect(function(_player)

	playerAdded(redTeam)

end)

redTeam.PlayerRemoved:Connect(function(_player)

	playerRemoved(redTeam)

end)

```

Feedback geven

---

Ga naar

▼

Team

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[AutoAssignable](#AutoAssignable)

[AutoColorCharacters](#AutoColorCharacters)

[Score](#Score)

[TeamColor](#TeamColor)

[Methoden](#methods)

[GetPlayers()](#GetPlayers)

[Evenementen](#events)

[PlayerAdded](#PlayerAdded)

[PlayerRemoved](#PlayerRemoved)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
