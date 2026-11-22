<!-- Source: https://create.roblox.com/docs/reference/engine/classes/Teams -->

Teams | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Teams.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [Teams](/docs/reference/engine/classes/Teams)

English

Feedback

Engine Class

Teams

Not Creatable

Service

---

## Summary

Methods

|

[GetTeams](#GetTeams) () : {[Team](/docs/reference/engine/classes/Team) }

 |
| --- | --- |
|

[RebalanceTeams](#RebalanceTeams) () : ()

Deprecated

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

Simple Team Rebalance

```

local Teams = game:GetService("Teams")

-- create two teams

local redTeam = Instance.new("Team")

redTeam.TeamColor = BrickColor.new("Bright red")

redTeam.AutoAssignable = true

redTeam.Name = "Red Team"

redTeam.Parent = Teams

local blueTeam = Instance.new("Team")

blueTeam.TeamColor = BrickColor.new("Bright blue")

blueTeam.AutoAssignable = true

blueTeam.Name = "Blue Team"

blueTeam.Parent = Teams

-- start counting the number of players on each team

local numberRed, numberBlue = 0, 0

local function playerAdded(team)

	-- increase the team's count by 1

	if team == redTeam then

		numberRed = numberRed + 1

	elseif team == blueTeam then

		numberBlue = numberBlue + 1

	end

end

local function playerRemoved(team)

	-- decrease the team's count by 1

	if team == redTeam then

		numberRed = numberRed - 1

	elseif team == blueTeam then

		numberBlue = numberBlue - 1

	end

	-- check if the teams are unbalanced

	local bigTeam, smallTeam = nil, nil

	if (numberRed - numberBlue) > 2 then

		bigTeam = redTeam

		smallTeam = blueTeam

	elseif (numberBlue - numberRed) > 2 then

		bigTeam = blueTeam

		smallTeam = redTeam

	end

	if bigTeam then

		-- pick a random player

		local playerList = bigTeam:GetPlayers()

		local player = playerList[math.random(1, #playerList)]

		-- check the player exists

		if player then

			-- change the player's team

			player.TeamColor = smallTeam.TeamColor

			-- respawn the player

			player:LoadCharacterAsync()

		end

	end

end

-- listen for players being added / removed

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

Team Only Door

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

	if playerAttack.Team ~= playerVictim.Team or playerAttack.Neutral or playerVictim.Neutral then

		return false

	end

	return true

end

local players = Players:GetPlayers()

checkTeamKill(players[1], players[2])

```

---

API Reference

Methods

GetTeams

Capabilities: Players

Teams:GetTeams () : {[Team](/docs/reference/engine/classes/Team) }

Returns

{[Team](/docs/reference/engine/classes/Team) }

Code Samples

Teams GetTeams

```

local Teams = game:GetService("Teams")

local teams = Teams:GetTeams()

for _, team in pairs(teams) do

	local players = team:GetPlayers()

	print("Team", team.Name, "has", #players, "players")

end

```

Provide feedback

---

RebalanceTeams

Deprecated

Show details

---

Jump to

▼

Teams

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[GetTeams()](#GetTeams)

[RebalanceTeams()](#RebalanceTeams)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
