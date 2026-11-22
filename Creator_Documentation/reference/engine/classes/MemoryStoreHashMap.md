<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/MemoryStoreHashMap -->

MemoryStoreHashMap | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/MemoryStoreHashMap.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [MemoryStoreHashMap](/docs/en-us/reference/engine/classes/MemoryStoreHashMap)

English

Feedback

Engine Class

MemoryStoreHashMap

Not Creatable

Not Replicated

---

## Summary

Methods

|

[GetAsync](#GetAsync) (key :  [string](/docs/en-us/luau/strings) ) : Variant

 |
| --- | --- |
|

[ListItemsAsync](#ListItemsAsync) (count :  [number](/docs/en-us/luau/numbers) ) :[MemoryStoreHashMapPages](/docs/en-us/reference/engine/classes/MemoryStoreHashMapPages)

 |
|

[RemoveAsync](#RemoveAsync) (key :  [string](/docs/en-us/luau/strings) ) : ()

 |
|

[SetAsync](#SetAsync) (key :  [string](/docs/en-us/luau/strings) , value :  Variant , expiration :  [number](/docs/en-us/luau/numbers) ) :[boolean](/docs/en-us/luau/booleans)

 |
|

[UpdateAsync](#UpdateAsync) (key :  [string](/docs/en-us/luau/strings) , transformFunction :  [function](/docs/en-us/luau/functions) , expiration :  [number](/docs/en-us/luau/numbers) ) : Variant

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

MemoryStoreHashMap:GetAsync (key :[string](/docs/en-us/luau/strings) ) : Variant

Parameters

|

key :[string](/docs/en-us/luau/strings)

 |

Returns

Variant

Code Samples

Getting data from a MemoryStore Hash Map

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local hashMap = MemoryStoreService:GetHashMap("HashMap1")

local key = "User_1234"

local value = 1000

local expiration = 30

local setSuccess, _ = pcall(function()

	return hashMap:SetAsync(key, value, expiration)

end)

if setSuccess then

	print("Set succeeded!")

end

local item

local getSuccess, getError = pcall(function()

	item = hashMap:GetAsync(key)

end)

if getSuccess then

	print(item)

else

	warn(getError)

end

```

Provide feedback

---

ListItemsAsync

Yields

Capabilities: DataStore

MemoryStoreHashMap:ListItemsAsync (count :[number](/docs/en-us/luau/numbers) ) :[MemoryStoreHashMapPages](/docs/en-us/reference/engine/classes/MemoryStoreHashMapPages)

Parameters

|

count :[number](/docs/en-us/luau/numbers)

 |

Returns

[MemoryStoreHashMapPages](/docs/en-us/reference/engine/classes/MemoryStoreHashMapPages)

Code Samples

Listing items in a MemoryStore Hash Map

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local testHashMap = MemoryStoreService:GetHashMap("HashMap1")

local EXPIRATION = 600

local NUM_TEST_ITEMS = 32

local function populateHashMap(hashMap: MemoryStoreHashMap, numItems: number): { [string]: any }

	print("Setting HashMap data...")

	local createdItems = {}

	for index = 1, numItems do

		local key = tostring(index) -- HashMap keys must be strings

		local value = `{key}_test_value`

		local success, result = pcall(hashMap.SetAsync, hashMap, key, value, EXPIRATION)

		if success then

			createdItems[key] = value

		else

			warn(`Error setting key {key}: {result}`)

		end

	end

	print("Done setting HashMap data.")

	return createdItems

end

local function getItemsFromAllPages(pages: MemoryStoreHashMapPages): { [string]: any }

	-- Purely for logging purposes, we track what page number we're on

	local currentPageNumber = 1

	local retrievedItems = {}

	while not pages.IsFinished do

		print(`Getting items on page {currentPageNumber}...`)

		local items = pages:GetCurrentPage()

		for _, entry in pairs(items) do

			print(`	{entry.key}: {entry.value}`)

			retrievedItems[entry.key] = entry.value

		end

		-- Advance pages if there are more pages to read

		if not pages.IsFinished then

			pages:AdvanceToNextPageAsync()

			currentPageNumber += 1

		end

	end

	print("Finished reading all pages")

	return retrievedItems

end

local function compareAllItems(retrievedItems: { [string]: any }, expectedItems: { [string]: any }): number

	print("Comparing retrieved items to expected items...")

	local numMatchingItems = 0

	for key, expectedValue in pairs(expectedItems) do

		if retrievedItems[key] == expectedValue then

			numMatchingItems += 1

		else

			warn(`Mismatched retrieved value for key {key}: expected {expectedValue}, retrieved {retrievedItems[key]}`)

		end

	end

	print("Comparison complete!")

	return numMatchingItems

end

-- Keys added to the hashmap are also added to this expectedItems table.

-- Later, the retrieved hashmap items will be compared against this table of expected items.

local expectedItems = populateHashMap(testHashMap, NUM_TEST_ITEMS)

-- Getting pages can error. In this case, we will let it error and stop program execution,

-- but you may want to pcall it and handle it differently.

print(`Getting HashMap pages with ListItemsAsync...`)

local pages = testHashMap:ListItemsAsync(NUM_TEST_ITEMS)

local retrievedItems = getItemsFromAllPages(pages)

local numMatchingItems = compareAllItems(retrievedItems, expectedItems)

-- If there were no errors setting or getting items, all items should match.

print(`Program complete. {numMatchingItems}/{NUM_TEST_ITEMS} retrieved items matched the expected values.`)

```

Provide feedback

---

RemoveAsync

Yields

Capabilities: DataStore

MemoryStoreHashMap:RemoveAsync (key :[string](/docs/en-us/luau/strings) ) : ()

Parameters

|

key :[string](/docs/en-us/luau/strings)

 |

Returns

()

Code Samples

Removing data from a MemoryStore Hash Map

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local hashMap = MemoryStoreService:GetHashMap("HashMap1")

local key = "User_1234"

local value = 1000

local expiration = 30

local setSuccess, setError = pcall(function()

	return hashMap:SetAsync(key, value, expiration)

end)

if not setSuccess then

	warn(setError)

end

local removeSuccess, removeError = pcall(function()

	hashMap:RemoveAsync(key)

end)

if removeSuccess then

	print("Remove succeeded!")

else

	warn(removeError)

end

```

Provide feedback

---

SetAsync

Yields

Capabilities: DataStore

MemoryStoreHashMap:SetAsync (

key :[string](/docs/en-us/luau/strings) , value : Variant , expiration :[number](/docs/en-us/luau/numbers)

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

Returns

[boolean](/docs/en-us/luau/booleans)

Code Samples

Adding data to a MemoryStore Hash Map

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local hashMap = MemoryStoreService:GetHashMap("HashMap1")

local key = "User_1234"

local value = 1000

local expiration = 30

local setSuccess, setError = pcall(function()

	return hashMap:SetAsync(key, value, expiration)

end)

if setSuccess then

	print("Set succeeded!")

else

	warn(setError)

end

```

Provide feedback

---

UpdateAsync

Yields

Capabilities: DataStore

MemoryStoreHashMap:UpdateAsync (

key :[string](/docs/en-us/luau/strings) , transformFunction :[function](/docs/en-us/luau/functions) , expiration :[number](/docs/en-us/luau/numbers)

) : Variant

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

Variant

Code Samples

Updating a Memory Store Hash Map

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local hashMap = MemoryStoreService:GetHashMap("ResourceInventory")

local function contributeResources(itemResource, addedCount)

	local success, newResourceCount = pcall(function()

		return hashMap:UpdateAsync(itemResource, function(resource)

			resource = resource or { count = 0 }

			resource.count = resource.count + addedCount

			-- ensure we don't exceed the maximum resource count

			if resource.count > 500 then

				resource.count = 500

			end

			return resource

		end, 1200)

	end)

	if success then

		print(newResourceCount)

	end

end

contributeResources("myResource", 50)

```

Provide feedback

---

Jump to

▼

MemoryStoreHashMap

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[GetAsync()](#GetAsync)

[ListItemsAsync()](#ListItemsAsync)

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
