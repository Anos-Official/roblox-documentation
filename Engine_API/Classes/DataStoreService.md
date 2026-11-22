<!-- Source: https://create.roblox.com/docs/reference/engine/classes/DataStoreService -->

DataStoreService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/DataStoreService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [DataStoreService](/docs/reference/engine/classes/DataStoreService)

English

Feedback

Engine Class

DataStoreService

Not Creatable

Service

Not Replicated

---

## Summary

Methods

|

[GetDataStore](#GetDataStore) (name :  [string](/docs/luau/strings) , scope :  [string](/docs/luau/strings) , options :  [Instance](/docs/reference/engine/datatypes/Instance) ) :[DataStore](/docs/reference/engine/classes/DataStore)

 |
| --- | --- |
|

[GetGlobalDataStore](#GetGlobalDataStore) () :[DataStore](/docs/reference/engine/classes/DataStore)

 |
|

[GetOrderedDataStore](#GetOrderedDataStore) (name :  [string](/docs/luau/strings) , scope :  [string](/docs/luau/strings) ) :[OrderedDataStore](/docs/reference/engine/classes/OrderedDataStore)

 |
|

[GetRequestBudgetForRequestType](#GetRequestBudgetForRequestType) (requestType :  [Enum.DataStoreRequestType](/docs/reference/engine/enums/DataStoreRequestType) ) :[number](/docs/luau/numbers)

 |
|

[ListDataStoresAsync](#ListDataStoresAsync) (prefix :  [string](/docs/luau/strings) , pageSize :  [number](/docs/luau/numbers) , cursor :  [string](/docs/luau/strings) ) :[DataStoreListingPages](/docs/reference/engine/classes/DataStoreListingPages)

 |
|

[SetRateLimitForRequestType](#SetRateLimitForRequestType) (requestType :  [Enum.DataStoreRequestType](/docs/reference/engine/enums/DataStoreRequestType) , baseLimit :  [number](/docs/luau/numbers) , perPlayerLimit :  [number](/docs/luau/numbers) ) : ()

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

DataStore Budget

```

local DataStoreService = game:GetService("DataStoreService")

for _, enumItem in pairs(Enum.DataStoreRequestType:GetEnumItems()) do

	print(enumItem.Name, DataStoreService:GetRequestBudgetForRequestType(enumItem))

end

```

---

API Reference

Methods

GetDataStore

Capabilities: DataStore

DataStoreService:GetDataStore (

name :[string](/docs/luau/strings) , scope :[string](/docs/luau/strings) , options :[Instance](/docs/reference/engine/datatypes/Instance)

) :[DataStore](/docs/reference/engine/classes/DataStore)

Parameters

|

name :[string](/docs/luau/strings)

 |
|

scope :[string](/docs/luau/strings)

Default Value: "global" |
|

options :[Instance](/docs/reference/engine/datatypes/Instance)

Default Value: nil |

Returns

[DataStore](/docs/reference/engine/classes/DataStore)

Provide feedback

---

GetGlobalDataStore

Capabilities: DataStore

DataStoreService:GetGlobalDataStore () :[DataStore](/docs/reference/engine/classes/DataStore)

Returns

[DataStore](/docs/reference/engine/classes/DataStore)

Code Samples

Get GlobalDataStore Instance

```

local DataStoreService = game:GetService("DataStoreService")

local GlobalDataStore = DataStoreService:GetGlobalDataStore()

print(GlobalDataStore.Name)

```

Provide feedback

---

GetOrderedDataStore

Capabilities: DataStore

DataStoreService:GetOrderedDataStore (

name :[string](/docs/luau/strings) , scope :[string](/docs/luau/strings)

) :[OrderedDataStore](/docs/reference/engine/classes/OrderedDataStore)

Parameters

|

name :[string](/docs/luau/strings)

 |
|

scope :[string](/docs/luau/strings)

Default Value: "global" |

Returns

[OrderedDataStore](/docs/reference/engine/classes/OrderedDataStore)

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

Provide feedback

---

GetRequestBudgetForRequestType

Capabilities: DataStore

DataStoreService:GetRequestBudgetForRequestType (requestType :[Enum.DataStoreRequestType](/docs/reference/engine/enums/DataStoreRequestType) ) :[number](/docs/luau/numbers)

Parameters

|

requestType :[Enum.DataStoreRequestType](/docs/reference/engine/enums/DataStoreRequestType)

 |

Returns

[number](/docs/luau/numbers)

Code Samples

Print Request Budget

```

local DataStoreService = game:GetService("DataStoreService")

local globalStore = DataStoreService:GetGlobalDataStore()

local function printBudget()

	local budget = DataStoreService:GetRequestBudgetForRequestType(Enum.DataStoreRequestType.SetIncrementAsync)

	print("Current set/increment budget:", budget)

end

for i = 1, 5 do

	local key = "key" .. i

	local success, err = pcall(function()

		globalStore:SetAsync(key, true)

	end)

	if success then

		printBudget()

	else

		print(err)

	end

end

```

Provide feedback

---

ListDataStoresAsync

Yields

Capabilities: DataStore

DataStoreService:ListDataStoresAsync (

prefix :[string](/docs/luau/strings) , pageSize :[number](/docs/luau/numbers) , cursor :[string](/docs/luau/strings)

) :[DataStoreListingPages](/docs/reference/engine/classes/DataStoreListingPages)

Parameters

|

prefix :[string](/docs/luau/strings)

 |
|

pageSize :[number](/docs/luau/numbers)

Default Value: 0 |
|

cursor :[string](/docs/luau/strings)

 |

Returns

[DataStoreListingPages](/docs/reference/engine/classes/DataStoreListingPages)

Provide feedback

---

SetRateLimitForRequestType

Capabilities: DataStore

DataStoreService:SetRateLimitForRequestType (

requestType :[Enum.DataStoreRequestType](/docs/reference/engine/enums/DataStoreRequestType) , baseLimit :[number](/docs/luau/numbers) , perPlayerLimit :[number](/docs/luau/numbers)

) : ()

Parameters

|

requestType :[Enum.DataStoreRequestType](/docs/reference/engine/enums/DataStoreRequestType)

 |
|

baseLimit :[number](/docs/luau/numbers)

 |
|

perPlayerLimit :[number](/docs/luau/numbers)

 |

Returns

()

Code Samples

Set Rate Limits

```

local MigrateScript = require(script.Parent.MigrateScript)

local DataStoreService = game:GetService("DataStoreService")

DataStoreService:SetRateLimitForRequestType(Enum.DataStoreRequestType.StandardRead, 1000, 0)

DataStoreService:SetRateLimitForRequestType(Enum.DataStoreRequestType.StandardWrite, 2000, 0) -- two writes, so needs double the limit as get

DataStoreService:SetRateLimitForRequestType(Enum.DataStoreRequestType.StandardList, 100, 0)

DataStoreService:SetRateLimitForRequestType(Enum.DataStoreRequestType.StandardRemove, 1000, 0)

local sourceStore = DataStoreService:GetDataStore("ds_to_migrate")

local destinationStore1 = DataStoreService:GetDataStore("ds_destination_1")

local destinationStore2 = DataStoreService:GetDataStore("ds_destination_2")

-- Helper to wait for budget

local function waitForBudget(requestType)

	while (DataStoreService:GetRequestBudgetForRequestType(requestType) <= 0) do

		task.wait(1)

	end

end

waitForBudget(Enum.DataStoreRequestType.StandardList)

local success, pages = pcall(function()

	return sourceStore:ListKeysAsync()

end)

if success then

	while true do

		local items = pages:GetCurrentPage()

		for _, item in ipairs(items) do

			-- 1. Fetch data from Source

			waitForBudget(Enum.DataStoreRequestType.StandardRead)

			local getSuccess, value = pcall(function()

				return sourceStore:GetAsync(item.KeyName)

			end)

			if getSuccess and value ~= nil then

				-- 2. Migrate data to Destinations

				waitForBudget(Enum.DataStoreRequestType.StandardWrite)

				local setSuccess, err = pcall(function()

					destinationStore1:SetAsync(item.KeyName, MigrateScript.Migrate1(value))

				end)

				if setSuccess then

					print("Successfully migrated key to destination 1: " .. item.KeyName)

				else

					warn("Failed to migrate key to destination 1: " .. item.KeyName .. " - " .. tostring(err))

				end

waitForBudget(Enum.DataStoreRequestType.StandardWrite)

				local setSuccess, err = pcall(function()

					destinationStore2:SetAsync(item.KeyName, MigrateScript.Migrate2(value))

				end)

				if setSuccess then

					print("Successfully migrated key to destination 2: " .. item.KeyName)

				else

					warn("Failed to migrate key to destination 2: " .. item.KeyName .. " - " .. tostring(err))

				end

				-- 3. Delete data from source

				waitForBudget(Enum.DataStoreRequestType.StandardRemove)

				local deleteSuccess, err = pcall(function()

					sourceStore:RemoveAsync(item.KeyName)

				end)

				if deleteSuccess then

					print("Successfully deleted key from source: " .. item.KeyName)

				else

					warn("Failed to delete key from source: " .. item.KeyName .. " - " .. tostring(err))

				end

			else

				warn("Failed to fetch key from source: " .. item.KeyName)

			end

		end

		if pages.IsFinished then break end

		-- 3. Advance Page

		waitForBudget(Enum.DataStoreRequestType.StandardList)

		local nextSuccess = pcall(function()

			pages:AdvanceToNextPageAsync()

		end)

		if not nextSuccess then

			warn("Failed to advance to next page.")

			break

		end

	end

	print("Migration process complete.")

else

	warn("Failed to list keys.")

end

```

Provide feedback

---

Jump to

▼

DataStoreService

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[GetDataStore()](#GetDataStore)

[GetGlobalDataStore()](#GetGlobalDataStore)

[GetOrderedDataStore()](#GetOrderedDataStore)

[GetRequestBudgetForRequestType()](#GetRequestBudgetForRequestType)

[ListDataStoresAsync()](#ListDataStoresAsync)

[SetRateLimitForRequestType()](#SetRateLimitForRequestType)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
