<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/OrderedDataStore -->

OrderedDataStore | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/OrderedDataStore.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [GlobalDataStore](/docs/en-us/reference/engine/classes/GlobalDataStore)
8. /
9. [OrderedDataStore](/docs/en-us/reference/engine/classes/OrderedDataStore)

English

Feedback

Engine Class

OrderedDataStore

Not Creatable

Not Replicated

---

## Summary

Methods

|

[GetSortedAsync](#GetSortedAsync) (ascending :  [boolean](/docs/en-us/luau/booleans) , pagesize :  [number](/docs/en-us/luau/numbers) , minValue :  Variant , maxValue :  Variant ) :[DataStorePages](/docs/en-us/reference/engine/classes/DataStorePages)

 |
| --- | --- |

Inherited Members

7  inherited from [GlobalDataStore](/docs/en-us/reference/engine/classes/GlobalDataStore)

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

OrderedDataStore Basics

```

local DataStoreService = game:GetService("DataStoreService")

local pointsStore = DataStoreService:GetOrderedDataStore("Points")

local function printTopTenPlayers()

	local isAscending = false

	local pageSize = 10

	local pages = pointsStore:GetSortedAsync(isAscending, pageSize)

	local topTen = pages:GetCurrentPage()

	-- The data in 'topTen' is stored with the index being the index on the page

	-- For each item, 'data.key' is the key in the OrderedDataStore and 'data.value' is the value

	for rank, data in ipairs(topTen) do

		local name = data.key

		local points = data.value

		print(name .. " is ranked #" .. rank .. " with " .. points .. "points")

	end

	-- Potentially load the next page...

	--pages:AdvanceToNextPageAsync()

end

-- Create some data

pointsStore:SetAsync("Alex", 55)

pointsStore:SetAsync("Charley", 32)

pointsStore:SetAsync("Sydney", 68)

-- Display the top ten players

printTopTenPlayers()

```

---

API Reference

Methods

GetSortedAsync

Yields

Capabilities: DataStore

OrderedDataStore:GetSortedAsync (

ascending :[boolean](/docs/en-us/luau/booleans) , pagesize :[number](/docs/en-us/luau/numbers) , minValue : Variant , maxValue : Variant

) :[DataStorePages](/docs/en-us/reference/engine/classes/DataStorePages)

Parameters

|

ascending :[boolean](/docs/en-us/luau/booleans)

 |
|

pagesize :[number](/docs/en-us/luau/numbers)

 |
|

minValue : Variant

 |
|

maxValue : Variant

 |

Returns

[DataStorePages](/docs/en-us/reference/engine/classes/DataStorePages)

Provide feedback

---

Jump to

▼

OrderedDataStore

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[GetSortedAsync()](#GetSortedAsync)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
