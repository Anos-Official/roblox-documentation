<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Teams -->

Teams | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [Teams](/docs/nl-nl/reference/engine/classes/Teams)

Nederlands

Feedback

Engine-klasse

Teams

Niet maakbaar

Service

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Teams)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[GetTeams](#GetTeams) () : {[Team](/docs/nl-nl/reference/engine/classes/Team) }

 |
| --- | --- |
|

[RebalanceTeams](#RebalanceTeams) () : ()

Verouderd

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

---

API-referentie

Methoden

GetTeams

Mogelijkheden: Players

Teams:GetTeams () : {[Team](/docs/nl-nl/reference/engine/classes/Team) }

Teruggaves

{[Team](/docs/nl-nl/reference/engine/classes/Team) }

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

RebalanceTeams

Verouderd

Details weergeven

---

Ga naar

▼

Teams

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[GetTeams()](#GetTeams)

[RebalanceTeams()](#RebalanceTeams)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
