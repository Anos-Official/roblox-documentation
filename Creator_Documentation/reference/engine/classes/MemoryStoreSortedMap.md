<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/MemoryStoreSortedMap -->

MemoryStoreSortedMap | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/MemoryStoreSortedMap.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [MemoryStoreSortedMap](/docs/en-us/reference/engine/classes/MemoryStoreSortedMap)

English

Feedback

Engine Class

MemoryStoreSortedMap

Not Creatable

Not Replicated

---

## Summary

Methods

|

[GetAsync](#GetAsync) (key :  [string](/docs/en-us/luau/strings) ) :[Tuple](/docs/en-us/luau/tuples)

 |
| --- | --- |
|

[GetRangeAsync](#GetRangeAsync) (direction :  [Enum.SortDirection](/docs/en-us/reference/engine/enums/SortDirection) , count :  [number](/docs/en-us/luau/numbers) , exclusiveLowerBound :  Variant , exclusiveUpperBound :  Variant ) :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[GetSizeAsync](#GetSizeAsync) () :[number](/docs/en-us/luau/numbers)

 |
|

[RemoveAsync](#RemoveAsync) (key :  [string](/docs/en-us/luau/strings) ) : ()

 |
|

[SetAsync](#SetAsync) (key :  [string](/docs/en-us/luau/strings) , value :  Variant , expiration :  [number](/docs/en-us/luau/numbers) , sortKey :  Variant ) :[boolean](/docs/en-us/luau/booleans)

 |
|

[UpdateAsync](#UpdateAsync) (key :  [string](/docs/en-us/luau/strings) , transformFunction :  [function](/docs/en-us/luau/functions) , expiration :  [number](/docs/en-us/luau/numbers) ) :[Tuple](/docs/en-us/luau/tuples)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Methods

GetAsync

Yields

Capabilities: DataStore

MemoryStoreSortedMap:GetAsync (key :[string](/docs/en-us/luau/strings) ) :[Tuple](/docs/en-us/luau/tuples)

Parameters

|

key :[string](/docs/en-us/luau/strings)

 |

Returns

[Tuple](/docs/en-us/luau/tuples)

Provide feedback

---

GetRangeAsync

Yields

Capabilities: DataStore

MemoryStoreSortedMap:GetRangeAsync (

direction :[Enum.SortDirection](/docs/en-us/reference/engine/enums/SortDirection) , count :[number](/docs/en-us/luau/numbers) , exclusiveLowerBound : Variant , exclusiveUpperBound : Variant

) :[{any}](/docs/en-us/luau/tables#arrays)

Parameters

|

direction :[Enum.SortDirection](/docs/en-us/reference/engine/enums/SortDirection)

 |
|

count :[number](/docs/en-us/luau/numbers)

 |
|

exclusiveLowerBound : Variant

 |
|

exclusiveUpperBound : Variant

 |

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Code Samples

Retrieving MemoryStore Keys

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local myMap = MemoryStoreService:GetSortedMap("MySortedMap")

function printAllKeys(map)

	-- the initial lower bound is nil which means to start from the very first item

	local exclusiveLowerBound = nil

	-- this loop continues until the end of the map is reached

	while true do

		-- get up to a hundred items starting from the current lower bound

		local items = map:GetRangeAsync(Enum.SortDirection.Ascending, 100, exclusiveLowerBound)

		for _, item in ipairs(items) do

			print(item.key)

			print(item.sortKey)

		end

		-- if the call returned less than a hundred items it means we've reached the end of the map

		if #items < 100 then

			break

		end

		-- the last retrieved key is the exclusive lower bound for the next iteration

		exclusiveLowerBound = {}

		exclusiveLowerBound["key"] = items[#items].key

		exclusiveLowerBound["sortKey"] = items[#items].sortKey

	end

end

printAllKeys(myMap)

```

Provide feedback

---

GetSizeAsync

Yields

Capabilities: DataStore

MemoryStoreSortedMap:GetSizeAsync () :[number](/docs/en-us/luau/numbers)

Returns

[number](/docs/en-us/luau/numbers)

Provide feedback

---

RemoveAsync

Yields

Capabilities: DataStore

MemoryStoreSortedMap:RemoveAsync (key :[string](/docs/en-us/luau/strings) ) : ()

Parameters

|

key :[string](/docs/en-us/luau/strings)

 |

Returns

()

Provide feedback

---

SetAsync

Yields

Capabilities: DataStore

MemoryStoreSortedMap:SetAsync (

key :[string](/docs/en-us/luau/strings) , value : Variant , expiration :[number](/docs/en-us/luau/numbers) , sortKey : Variant

) :[boolean](/docs/en-us/luau/booleans)

Parameters

|

key :[string](/docs/en-us/luau/strings)

 |
|

value : Variant

 |
|

expiration :[number](/docs/en-us/luau/numbers)

 |
|

sortKey : Variant

 |

Returns

[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

UpdateAsync

Yields

Capabilities: DataStore

MemoryStoreSortedMap:UpdateAsync (

key :[string](/docs/en-us/luau/strings) , transformFunction :[function](/docs/en-us/luau/functions) , expiration :[number](/docs/en-us/luau/numbers)

) :[Tuple](/docs/en-us/luau/tuples)

Parameters

|

key :[string](/docs/en-us/luau/strings)

 |
|

transformFunction :[function](/docs/en-us/luau/functions)

 |
|

expiration :[number](/docs/en-us/luau/numbers)

 |

Returns

[Tuple](/docs/en-us/luau/tuples)

Code Samples

Updating a MemoryStore Sorted Map

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local map = MemoryStoreService:GetSortedMap("Leaderboard")

local Players = game:GetService("Players")

function updateLeaderboard(itemKey, killsToAdd, deathsToAdd)

	local success, newStats, newScore = pcall(function()

		return map:UpdateAsync(itemKey, function(playerStats, playerScore)

			playerStats = playerStats or { kills = 0, deaths = 0 }

			playerStats.kills += killsToAdd

			playerStats.deaths += deathsToAdd

			if playerStats then

				-- `playerScore` is the sortKey being used to sort items in the map

				playerScore = playerStats.kills / math.max(playerStats.deaths, 1)

				return playerStats, playerScore

			end

			return nil

		end, 30)

	end)

end

-- Add one kill to all players

for i, player in pairs(Players:GetPlayers()) do

	updateLeaderboard(player.UserId, 1, 0)

end

-- Add 5 kills and 1 death to player with userId 12345

updateLeaderboard(12345, 5, 1)

```

Provide feedback

---

Jump to

▼

MemoryStoreSortedMap

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[GetAsync()](#GetAsync)

[GetRangeAsync()](#GetRangeAsync)

[GetSizeAsync()](#GetSizeAsync)

[RemoveAsync()](#RemoveAsync)

[SetAsync()](#SetAsync)

[UpdateAsync()](#UpdateAsync)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
