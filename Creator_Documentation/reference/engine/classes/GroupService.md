<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/GroupService -->

GroupService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/GroupService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [GroupService](/docs/en-us/reference/engine/classes/GroupService)

English

Feedback

Engine Class

GroupService

Not Creatable

Service

Not Replicated

---

## Summary

Methods

|

[GetAlliesAsync](#GetAlliesAsync) (groupId :  [number](/docs/en-us/luau/numbers) ) :[StandardPages](/docs/en-us/reference/engine/classes/StandardPages)

 |
| --- | --- |
|

[GetEnemiesAsync](#GetEnemiesAsync) (groupId :  [number](/docs/en-us/luau/numbers) ) :[StandardPages](/docs/en-us/reference/engine/classes/StandardPages)

 |
|

[GetGroupInfoAsync](#GetGroupInfoAsync) (groupId :  [number](/docs/en-us/luau/numbers) ) : Variant

 |
|

[GetGroupsAsync](#GetGroupsAsync) (userId :  [User](/docs/en-us/reference/engine/datatypes/User) ) :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[GetRolesInGroupAsync](#GetRolesInGroupAsync) (userId :  [User](/docs/en-us/reference/engine/datatypes/User) , groupId :  [number](/docs/en-us/luau/numbers) ) : Variant

 |
|

[PromptJoinAsync](#PromptJoinAsync) (groupId :  [number](/docs/en-us/luau/numbers) ) :[Enum.GroupMembershipStatus](/docs/en-us/reference/engine/enums/GroupMembershipStatus)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Group Ally/Enemy Checker

```

local GroupService = game:GetService("GroupService")

local Players = game:GetService("Players")

-- Define group ID here

local GROUP_ID = 271454

-- Utility function for dealing with pages

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

-- Get lists of allies and enemies

local alliesPages = GroupService:GetAlliesAsync(GROUP_ID)

local enemiesPages = GroupService:GetEnemiesAsync(GROUP_ID)

-- Convert to array

local allies = pagesToArray(alliesPages)

local enemies = pagesToArray(enemiesPages)

local function playerAdded(player)

	-- Check to see if the player is in the group

	if player:IsInGroupAsync(GROUP_ID) then

		print(player.Name .. " is a member!")

	else

		local isAlly, isEnemy = false, false

		-- Check to see if the player is in any ally groups

		for _, groupInfo in ipairs(allies) do

			local groupId = groupInfo.Id

			if player:IsInGroupAsync(groupId) then

				isAlly = true

				break

			end

		end

		-- Check to see if the player is in any enemy groups

		for _, groupInfo in ipairs(enemies) do

			local groupId = groupInfo.Id

			if player:IsInGroupAsync(groupId) then

				isEnemy = true

				break

			end

		end

		if isAlly and not isEnemy then

			print(player.Name .. " is an ally!")

		elseif isEnemy and not isAlly then

			print(player.Name .. " is an enemy!")

		elseif isEnemy and isAlly then

			print(player.Name .. " is both an ally and an enemy!")

		else

			print(player.Name .. " is neither an ally or an enemy!")

		end

	end

end

-- Listen for new players being added

Players.PlayerAdded:Connect(playerAdded)

-- Handle players already in game

for _, player in ipairs(Players:GetPlayers()) do

	playerAdded(player)

end

```

---

API Reference

Methods

GetAlliesAsync

Yields

Capabilities: Groups

GroupService:GetAlliesAsync (groupId :[number](/docs/en-us/luau/numbers) ) :[StandardPages](/docs/en-us/reference/engine/classes/StandardPages)

Parameters

|

groupId :[number](/docs/en-us/luau/numbers)

 |

Returns

[StandardPages](/docs/en-us/reference/engine/classes/StandardPages)

Code Samples

GroupService:GetAlliesAsync

```

local Players = game:GetService("Players")

local GroupService = game:GetService("GroupService")

local GROUP_ID = 57

-- creates a table of all of the allies of a given group

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

			print("Player is an ally!")

			break

		end

	end

end

Players.PlayerAdded:Connect(onPlayerAdded)

-- handle players who joined while the allies list was still loading

for _, player in pairs(Players:GetPlayers()) do

	onPlayerAdded(player)

end

```

Group Ally/Enemy Checker

```

local GroupService = game:GetService("GroupService")

local Players = game:GetService("Players")

-- Define group ID here

local GROUP_ID = 271454

-- Utility function for dealing with pages

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

-- Get lists of allies and enemies

local alliesPages = GroupService:GetAlliesAsync(GROUP_ID)

local enemiesPages = GroupService:GetEnemiesAsync(GROUP_ID)

-- Convert to array

local allies = pagesToArray(alliesPages)

local enemies = pagesToArray(enemiesPages)

local function playerAdded(player)

	-- Check to see if the player is in the group

	if player:IsInGroupAsync(GROUP_ID) then

		print(player.Name .. " is a member!")

	else

		local isAlly, isEnemy = false, false

		-- Check to see if the player is in any ally groups

		for _, groupInfo in ipairs(allies) do

			local groupId = groupInfo.Id

			if player:IsInGroupAsync(groupId) then

				isAlly = true

				break

			end

		end

		-- Check to see if the player is in any enemy groups

		for _, groupInfo in ipairs(enemies) do

			local groupId = groupInfo.Id

			if player:IsInGroupAsync(groupId) then

				isEnemy = true

				break

			end

		end

		if isAlly and not isEnemy then

			print(player.Name .. " is an ally!")

		elseif isEnemy and not isAlly then

			print(player.Name .. " is an enemy!")

		elseif isEnemy and isAlly then

			print(player.Name .. " is both an ally and an enemy!")

		else

			print(player.Name .. " is neither an ally or an enemy!")

		end

	end

end

-- Listen for new players being added

Players.PlayerAdded:Connect(playerAdded)

-- Handle players already in game

for _, player in ipairs(Players:GetPlayers()) do

	playerAdded(player)

end

```

Provide feedback

---

GetEnemiesAsync

Yields

Capabilities: Groups

GroupService:GetEnemiesAsync (groupId :[number](/docs/en-us/luau/numbers) ) :[StandardPages](/docs/en-us/reference/engine/classes/StandardPages)

Parameters

|

groupId :[number](/docs/en-us/luau/numbers)

 |

Returns

[StandardPages](/docs/en-us/reference/engine/classes/StandardPages)

Code Samples

GroupService:GetEnemiesAsync

```

local Players = game:GetService("Players")

local GroupService = game:GetService("GroupService")

local GROUP_ID = 57

-- creates a list of all of the enemies of a given group

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

			print("Player is an enemy!")

			break

		end

	end

end

Players.PlayerAdded:Connect(onPlayerAdded)

-- handle players who joined while the enemies list was still loading

for _, player in pairs(Players:GetPlayers()) do

	onPlayerAdded(player)

end

```

Group Ally/Enemy Checker

```

local GroupService = game:GetService("GroupService")

local Players = game:GetService("Players")

-- Define group ID here

local GROUP_ID = 271454

-- Utility function for dealing with pages

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

-- Get lists of allies and enemies

local alliesPages = GroupService:GetAlliesAsync(GROUP_ID)

local enemiesPages = GroupService:GetEnemiesAsync(GROUP_ID)

-- Convert to array

local allies = pagesToArray(alliesPages)

local enemies = pagesToArray(enemiesPages)

local function playerAdded(player)

	-- Check to see if the player is in the group

	if player:IsInGroupAsync(GROUP_ID) then

		print(player.Name .. " is a member!")

	else

		local isAlly, isEnemy = false, false

		-- Check to see if the player is in any ally groups

		for _, groupInfo in ipairs(allies) do

			local groupId = groupInfo.Id

			if player:IsInGroupAsync(groupId) then

				isAlly = true

				break

			end

		end

		-- Check to see if the player is in any enemy groups

		for _, groupInfo in ipairs(enemies) do

			local groupId = groupInfo.Id

			if player:IsInGroupAsync(groupId) then

				isEnemy = true

				break

			end

		end

		if isAlly and not isEnemy then

			print(player.Name .. " is an ally!")

		elseif isEnemy and not isAlly then

			print(player.Name .. " is an enemy!")

		elseif isEnemy and isAlly then

			print(player.Name .. " is both an ally and an enemy!")

		else

			print(player.Name .. " is neither an ally or an enemy!")

		end

	end

end

-- Listen for new players being added

Players.PlayerAdded:Connect(playerAdded)

-- Handle players already in game

for _, player in ipairs(Players:GetPlayers()) do

	playerAdded(player)

end

```

Provide feedback

---

GetGroupInfoAsync

Yields

Capabilities: Groups

Cloud API

GroupService:GetGroupInfoAsync (groupId :[number](/docs/en-us/luau/numbers) ) : Variant

Parameters

|

groupId :[number](/docs/en-us/luau/numbers)

 |

Returns

Variant

Code Samples

GroupService:GetGroupInfoAsync

```

local GroupService = game:GetService("GroupService")

local GROUP_ID = 377251

local group = GroupService:GetGroupInfoAsync(GROUP_ID)

print(group.Name .. " has the following roles:")

for _, role in ipairs(group.Roles) do

	print("Rank " .. role.Rank .. ": " .. role.Name)

end

```

Load Group Emblem

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

Provide feedback

---

GetGroupsAsync

Yields

Capabilities: Groups

GroupService:GetGroupsAsync (userId :[User](/docs/en-us/reference/engine/datatypes/User) ) :[{any}](/docs/en-us/luau/tables#arrays)

Parameters

|

userId :[User](/docs/en-us/reference/engine/datatypes/User)

 |

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Code Samples

Getting the Groups that a User is A Member Of

```

local GroupService = game:GetService("GroupService")

local Players = game:GetService("Players")

local function playerAdded(player)

	-- load a list of info on all groups the player is a member of

	local groups = GroupService:GetGroupsAsync(player.UserId)

	for _, groupInfo in pairs(groups) do

		for key, value in pairs(groupInfo) do

			print(key .. ": " .. tostring(value))

		end

		print("--")

	end

end

Players.PlayerAdded:Connect(playerAdded)

-- go through existing players

for _, player in pairs(Players:GetPlayers()) do

	playerAdded(player)

end

```

Provide feedback

---

GetRolesInGroupAsync

Yields

Capabilities: Groups

Cloud API

GroupService:GetRolesInGroupAsync (

userId :[User](/docs/en-us/reference/engine/datatypes/User) , groupId :[number](/docs/en-us/luau/numbers)

) : Variant

Parameters

|

userId :[User](/docs/en-us/reference/engine/datatypes/User)

 |
|

groupId :[number](/docs/en-us/luau/numbers)

 |

Returns

Variant

Code Samples

Get Roles In Group Async

```

local GroupService = game:GetService("GroupService")

local Players = game:GetService("Players")

local GROUP_ID = 377251

local localPlayer = Players.LocalPlayer

local result = GroupService:GetRolesInGroupAsync(localPlayer.UserId, GROUP_ID)

if result.IsMember then

    print("User is a member with", #result.Roles, "role(s)")

    for _, role in ipairs(result.Roles) do

        print(role.Name, "rank", role.Rank)

    end

else

    print("User is not a member")

end

```

Provide feedback

---

PromptJoinAsync

Yields

Capabilities: Groups

GroupService:PromptJoinAsync (groupId :[number](/docs/en-us/luau/numbers) ) :[Enum.GroupMembershipStatus](/docs/en-us/reference/engine/enums/GroupMembershipStatus)

Parameters

|

groupId :[number](/docs/en-us/luau/numbers)

 |

Returns

[Enum.GroupMembershipStatus](/docs/en-us/reference/engine/enums/GroupMembershipStatus)

Code Samples

Prompting a player to join a group

```

local GroupService = game:GetService("GroupService")

local GROUP_ID = 377251

-- This should be done in a script running on the client

local success, result = pcall(function()

    return GroupService:PromptJoinAsync(GROUP_ID)

end)

if success then

    if result == Enum.GroupMembershipStatus.Joined then

        print("Player joined the group!")

    elseif result == Enum.GroupMembershipStatus.JoinRequestPending then

        print("Player has an outstanding join request")

    elseif result == Enum.GroupMembershipStatus.AlreadyMember then

        print("Already a member")

    else

        print("Did not join or not eligible")

    end

else

    warn("Prompt failed:", result)

end

```

Provide feedback

---

Jump to

▼

GroupService

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[GetAlliesAsync()](#GetAlliesAsync)

[GetEnemiesAsync()](#GetEnemiesAsync)

[GetGroupInfoAsync()](#GetGroupInfoAsync)

[GetGroupsAsync()](#GetGroupsAsync)

[GetRolesInGroupAsync()](#GetRolesInGroupAsync)

[PromptJoinAsync()](#PromptJoinAsync)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
