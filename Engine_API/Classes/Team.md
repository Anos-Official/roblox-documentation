<!-- Source: https://create.roblox.com/docs/reference/engine/classes/Team -->

Team | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Team.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [Team](/docs/reference/engine/classes/Team)

English

Feedback

Engine Class

Team

---

## Summary

Properties

|

[AutoAssignable](#AutoAssignable) :[boolean](/docs/luau/booleans)

 |
| --- | --- |
|

[AutoColorCharacters](#AutoColorCharacters) :[boolean](/docs/luau/booleans)

Deprecated

 |
|

[Score](#Score) :[number](/docs/luau/numbers)

Deprecated

 |
|

[TeamColor](#TeamColor) :[BrickColor](/docs/reference/engine/datatypes/BrickColor)

 |

Methods

|

[GetPlayers](#GetPlayers) () : {[Player](/docs/reference/engine/classes/Player) }

 |

Events

|

[PlayerAdded](#PlayerAdded) (player :  [Player](/docs/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |
|

[PlayerRemoved](#PlayerRemoved) (player :  [Player](/docs/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

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

Team Rebalance with Party Integration

```

local Teams = game:GetService("Teams")

local Players = game:GetService("Players")

local SocialService = game:GetService("SocialService")

local redTeam = Instance.new("Team")

redTeam.Name = "Red Team"

redTeam.TeamColor = BrickColor.Red()

redTeam.AutoAssignable = false

redTeam.Parent = Teams

local blueTeam = Instance.new("Team")

blueTeam.Name = "Blue Team"

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

-- Call this function to rebalance teams

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

API Reference

Properties

AutoAssignable

Read Parallel

Capabilities: Players

Team.AutoAssignable :[boolean](/docs/luau/booleans)

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

Provide feedback

---

AutoColorCharacters

Deprecated

Show details

---

Score

Deprecated

Show details

---

TeamColor

Read Parallel

Capabilities: Players

Team.TeamColor :[BrickColor](/docs/reference/engine/datatypes/BrickColor)

Code Samples

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

Provide feedback

---

Methods

GetPlayers

Write Parallel

Capabilities: Players

Team:GetPlayers () : {[Player](/docs/reference/engine/classes/Player) }

Returns

{[Player](/docs/reference/engine/classes/Player) }

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

Events

PlayerAdded

Capabilities: Players

Team.PlayerAdded (player :[Player](/docs/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

player :[Player](/docs/reference/engine/classes/Player)

 |

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

Provide feedback

---

PlayerRemoved

Capabilities: Players

Team.PlayerRemoved (player :[Player](/docs/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

player :[Player](/docs/reference/engine/classes/Player)

 |

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

Provide feedback

---

Jump to

▼

Team

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[AutoAssignable](#AutoAssignable)

[AutoColorCharacters](#AutoColorCharacters)

[Score](#Score)

[TeamColor](#TeamColor)

[Methods](#methods)

[GetPlayers()](#GetPlayers)

[Events](#events)

[PlayerAdded](#PlayerAdded)

[PlayerRemoved](#PlayerRemoved)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
