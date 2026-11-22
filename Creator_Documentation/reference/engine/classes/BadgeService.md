<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/BadgeService -->

BadgeService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/BadgeService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [BadgeService](/docs/en-us/reference/engine/classes/BadgeService)

English

Feedback

Engine Class

BadgeService

Not Creatable

Service

---

## Summary

Methods

|

[AwardBadge](#AwardBadge) (userId :  [User](/docs/en-us/reference/engine/datatypes/User) , badgeId :  [number](/docs/en-us/luau/numbers) ) :[boolean](/docs/en-us/luau/booleans)

Deprecated

 |
| --- | --- |
|

[AwardBadgeAsync](#AwardBadgeAsync) (userId :  [User](/docs/en-us/reference/engine/datatypes/User) , badgeId :  [number](/docs/en-us/luau/numbers) ) :[boolean](/docs/en-us/luau/booleans)

 |
|

[CheckUserBadgesAsync](#CheckUserBadgesAsync) (userId :  [User](/docs/en-us/reference/engine/datatypes/User) , badgeIds :  [{any}](/docs/en-us/luau/tables#arrays) ) :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[GetBadgeInfoAsync](#GetBadgeInfoAsync) (badgeId :  [number](/docs/en-us/luau/numbers) ) :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |
|

[GetUserBadgesAsync](#GetUserBadgesAsync) (userId :  [User](/docs/en-us/reference/engine/datatypes/User) , badgeIds :  [{any}](/docs/en-us/luau/tables#arrays) ) :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[IsDisabled](#IsDisabled) (badgeId :  [number](/docs/en-us/luau/numbers) ) :[boolean](/docs/en-us/luau/booleans)

Deprecated

 |
|

[IsLegal](#IsLegal) (badgeId :  [number](/docs/en-us/luau/numbers) ) :[boolean](/docs/en-us/luau/booleans)

Deprecated

 |
|

[UserHasBadge](#UserHasBadge) (userId :  [User](/docs/en-us/reference/engine/datatypes/User) , badgeId :  [number](/docs/en-us/luau/numbers) ) :[boolean](/docs/en-us/luau/booleans)

Deprecated

 |
|

[UserHasBadgeAsync](#UserHasBadgeAsync) (userId :  [User](/docs/en-us/reference/engine/datatypes/User) , badgeId :  [number](/docs/en-us/luau/numbers) ) :[boolean](/docs/en-us/luau/booleans)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Methods

AwardBadge

Deprecated

Show details

---

AwardBadgeAsync

Yields

Capabilities: AssetManagement

BadgeService:AwardBadgeAsync (

userId :[User](/docs/en-us/reference/engine/datatypes/User) , badgeId :[number](/docs/en-us/luau/numbers)

) :[boolean](/docs/en-us/luau/booleans)

Parameters

|

userId :[User](/docs/en-us/reference/engine/datatypes/User)

 |
|

badgeId :[number](/docs/en-us/luau/numbers)

 |

Returns

[boolean](/docs/en-us/luau/booleans)

Code Samples

Awarding a Badge

```

local BadgeService = game:GetService("BadgeService")

local Players = game:GetService("Players")

local BADGE_ID = 0

local function awardBadge(player, badgeId)

	-- Fetch badge information

	local success, badgeInfo = pcall(function()

		return BadgeService:GetBadgeInfoAsync(badgeId)

	end)

	if success then

		-- Confirm that badge can be awarded

		if badgeInfo.IsEnabled then

			-- Award badge

			local awarded, errorMessage = pcall(BadgeService.AwardBadgeAsync, BadgeService, player.UserId, badgeId)

			if not awarded then

				warn("Error while awarding badge:", errorMessage)

			end

		end

	else

		warn("Error while fetching badge info: " .. badgeInfo)

	end

end

local function onPlayerAdded(player)

	awardBadge(player, BADGE_ID)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Provide feedback

---

CheckUserBadgesAsync

Yields

Capabilities: AssetManagement

BadgeService:CheckUserBadgesAsync (

userId :[User](/docs/en-us/reference/engine/datatypes/User) , badgeIds :[{any}](/docs/en-us/luau/tables#arrays)

) :[{any}](/docs/en-us/luau/tables#arrays)

Parameters

|

userId :[User](/docs/en-us/reference/engine/datatypes/User)

 |
|

badgeIds :[{any}](/docs/en-us/luau/tables#arrays)

 |

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Code Samples

Checking Earned Badges in Batches

```

local BadgeService = game:GetService("BadgeService")

local Players = game:GetService("Players")

local badgeIds = { 0000000000, 1111111111, 2222222222 } -- Change this to a list of your badge IDs

local function onPlayerAdded(player)

	-- Check if the player has any of the badges

	local success, result = pcall(function()

		return BadgeService:CheckUserBadgesAsync(player.UserId, badgeIds)

	end)

	-- If there's an error, issue a warning and exit the function

	if not success then

		warn("Error while checking if player", player.Name, "has badges:", result)

		return

	end

	local ownedBadgeIds = result

	if #ownedBadgeIds == 0 then

		print(player.Name, "does not have any of the badges")

	else

		print(player.Name, "has the following badges:", table.concat(ownedBadgeIds, ", "))

	end

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Provide feedback

---

GetBadgeInfoAsync

Yields

Capabilities: AssetManagement

BadgeService:GetBadgeInfoAsync (badgeId :[number](/docs/en-us/luau/numbers) ) :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Parameters

|

badgeId :[number](/docs/en-us/luau/numbers)

 |

Returns

[Dictionary](/docs/en-us/luau/tables#dictionaries)

Code Samples

Getting Badge Info

```

local BadgeService = game:GetService("BadgeService")

-- Fetch badge information

local success, result = pcall(function()

	return BadgeService:GetBadgeInfoAsync(00000000) -- Change this to desired badge ID

end)

-- Output the information

if success then

	print("Badge:", result.Name)

	print("Enabled:", result.IsEnabled)

	print("Description:", result.Description)

	print("Icon:", "rbxassetid://" .. result.IconImageId)

else

	warn("Error while fetching badge info:", result)

end

```

Provide feedback

---

GetUserBadgesAsync

Yields

Capabilities: AssetManagement

BadgeService:GetUserBadgesAsync (

userId :[User](/docs/en-us/reference/engine/datatypes/User) , badgeIds :[{any}](/docs/en-us/luau/tables#arrays)

) :[{any}](/docs/en-us/luau/tables#arrays)

Parameters

|

userId :[User](/docs/en-us/reference/engine/datatypes/User)

 |
|

badgeIds :[{any}](/docs/en-us/luau/tables#arrays)

 |

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Code Samples

Getting Earned Badges and Award Dates

```

local BadgeService = game:GetService("BadgeService")

local Players = game:GetService("Players")

local badgeIds = { 0000000000, 1111111111, 2222222222 } -- Change this to a list of your badge IDs

local function onPlayerAdded(player)

	-- Get which of the badges the player owns, along with when each was awarded

	local success, result = pcall(function()

		return BadgeService:GetUserBadgesAsync(player.UserId, badgeIds)

	end)

	-- If there's an error, issue a warning and exit the function

	if not success then

		warn("Error while getting badges for player", player.Name, ":", result)

		return

	end

	local ownedBadges = result

	if #ownedBadges == 0 then

		print(player.Name, "does not have any of the badges")

	else

		for _, badge in ownedBadges do

			print(player.Name, "was awarded badge", badge.BadgeId, "on", badge.AwardedDate:ToIsoDate())

		end

	end

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Provide feedback

---

IsDisabled

Deprecated

Show details

---

IsLegal

Deprecated

Show details

---

UserHasBadge

Deprecated

Show details

---

UserHasBadgeAsync

Yields

Capabilities: AssetManagement

BadgeService:UserHasBadgeAsync (

userId :[User](/docs/en-us/reference/engine/datatypes/User) , badgeId :[number](/docs/en-us/luau/numbers)

) :[boolean](/docs/en-us/luau/booleans)

Parameters

|

userId :[User](/docs/en-us/reference/engine/datatypes/User)

 |
|

badgeId :[number](/docs/en-us/luau/numbers)

 |

Returns

[boolean](/docs/en-us/luau/booleans)

Code Samples

Checking Earned Badges

```

local BadgeService = game:GetService("BadgeService")

local Players = game:GetService("Players")

local badgeId = 00000000 -- Change this to your badge ID

local function onPlayerAdded(player)

	-- Check if the player has the badge

	local success, hasBadge = pcall(function()

		return BadgeService:UserHasBadgeAsync(player.UserId, badgeId)

	end)

	-- If there's an error, issue a warning and exit the function

	if not success then

		warn("Error while checking if player has badge!")

		return

	end

	if hasBadge then

		-- Handle player's badge ownership as needed

		print(player.Name, "has badge", badgeId)

	end

end

-- Connect "PlayerAdded" events to the "onPlayerAdded()" function

Players.PlayerAdded:Connect(onPlayerAdded)

```

Provide feedback

---

Jump to

▼

BadgeService

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[AwardBadge()](#AwardBadge)

[AwardBadgeAsync()](#AwardBadgeAsync)

[CheckUserBadgesAsync()](#CheckUserBadgesAsync)

[GetBadgeInfoAsync()](#GetBadgeInfoAsync)

[GetUserBadgesAsync()](#GetUserBadgesAsync)

[IsDisabled()](#IsDisabled)

[IsLegal()](#IsLegal)

[UserHasBadge()](#UserHasBadge)

[UserHasBadgeAsync()](#UserHasBadgeAsync)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
