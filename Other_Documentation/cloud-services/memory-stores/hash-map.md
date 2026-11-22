<!-- Source: https://create.roblox.com/docs/cloud-services/memory-stores/hash-map -->

Memory store hash map | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/cloud-services/memory-stores/hash-map.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Cloud services](/docs/cloud-services/data-stores-vs-memory-stores)
6. /
7. [Memory stores](/docs/cloud-services/memory-stores)

# Memory store hash map

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/cloud-services/memory-stores/hash-map.md)

Hash maps , similar to sorted maps, let you store in-memory data as key-value pairs. Unlike sorted maps, they maintain no ordering guarantees. This data structure is useful for cases that require simple data caching and rapid access, such as shared inventories, physical auction houses, and more. Hash maps automatically handle partitioning your data and are very useful if you have more than 1,000 keys. For smaller key spaces, we recommend [sorted maps](/docs/cloud-services/memory-stores/sorted-map) .

## [Limits](#limits)[](#limits)

Hash maps have a key size limit of 128 characters and a value size limit of 32 KB.

Otherwise, hash maps use the same [API request](/docs/cloud-services/memory-stores#api-requests-limits)  and [memory quota](/docs/cloud-services/memory-stores#memory-size-quota)  limits as the other memory store data structures.

## [Get a hash map](#get-a-hash-map)[](#get-a-hash-map)

To get a hash map, call [MemoryStoreService:GetHashMap()](/docs/reference/engine/classes/MemoryStoreService#GetHashMap)  with a name for the hash map. The name is global within the game, so you can access the same hash map on any script using this name.

Getting a Hash Map

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local hashMap = MemoryStoreService:GetHashMap("HashMap1")

```

After you get a hash map, call any of the following functions to read or write data in it:

| Function | | Action |
| --- | --- |
| [MemoryStoreHashMap:SetAsync()](/docs/reference/engine/classes/MemoryStoreHashMap#SetAsync) | | [Add](#add-or-overwrite-data)  a new key or overwrite the value if the key already exists. |
| [MemoryStoreHashMap:GetAsync()](/docs/reference/engine/classes/MemoryStoreHashMap#GetAsync) | | [Read](#get-data)  a particular key. |
| [MemoryStoreHashMap:ListItemsAsync()](/docs/reference/engine/classes/MemoryStoreHashMap#ListItemsAsync) | | [List](#get-data)  items in a hash map. |
| [MemoryStoreHashMap:UpdateAsync()](/docs/reference/engine/classes/MemoryStoreHashMap#UpdateAsync) | | [Update](#update-data)  the value of a key after retrieving it from a hash map. |
| [MemoryStoreHashMap:RemoveAsync()](/docs/reference/engine/classes/MemoryStoreHashMap#RemoveAsync) | | [Remove](#remove-data)  a key from the hash map. |

For in-depth documentation about each function, see [MemoryStoreHashMap](/docs/reference/engine/classes/MemoryStoreHashMap) .

All functions accessing data structures in memory stores are asynchronous network calls that might occasionally fail. You should wrap these calls in [pcall()](/docs/reference/engine/globals/LuaGlobals#pcall)  to catch and handle errors, as shown in the code samples.

## [Add or overwrite data](#add-or-overwrite-data)[](#add-or-overwrite-data)

To add a new key or overwrite the value of a key in the hash map, call [MemoryStoreHashMap:SetAsync()](/docs/reference/engine/classes/MemoryStoreHashMap#SetAsync)  with the key name , its value , and an expiration time  in seconds. The memory automatically cleans up once the key expires. The maximum expiration time is 3,888,000 seconds (45 days).

Adding Data to a Hash Map

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local hashMap = MemoryStoreService:GetHashMap("HashMap1")

local setSuccess, _ = pcall(function()

	return hashMap:SetAsync("User_1234", 1000, 30)

end)

if setSuccess then

	print("Set succeeded.")

end

```

## [Get data](#get-data)[](#get-data)

You can either get a value associated with a specific key or get multiple key-value pairs in the hash map.

### [Get data with one key](#get-data-with-one-key)[](#get-data-with-one-key)

To get a value associated with one key from the hash map, call [MemoryStoreHashMap:GetAsync()](/docs/reference/engine/classes/MemoryStoreHashMap#GetAsync)  with the key name .

Getting a Particular Key from a Hash Map

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local hashMap = MemoryStoreService:GetHashMap("HashMap1")

local setSuccess, _ = pcall(function()

	return hashMap:SetAsync("User_1234", 1000, 30)

end)

if setSuccess then

	print("Set succeeded.")

end

local item

local getSuccess, getError = pcall(function()

	item = hashMap:GetAsync("User_1234")

end)

if getSuccess then

	print(item)

else

	warn(getError)

end

```

### [Get data with multiple key-value pairs](#get-data-with-multiple-key-value-pairs)[](#get-data-with-multiple-key-value-pairs)

To get all the key-value pairs from the hash map as a single operation, call [MemoryStoreHashMap:ListItemsAsync()](/docs/reference/engine/classes/MemoryStoreHashMap#ListItemsAsync)  with the desired page size. This function lists all existing keys in a paginated manner. For example, the following code sample retrieves up to 32 items from the hash map.

Listing items in a Hash Map

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local hashMap = MemoryStoreService:GetHashMap("HashMap1")

-- Get list of items, 32 items at a time

local success, pages = pcall(function()

	return hashMap:ListItemsAsync(32)

end)

if success then

	while true do

		-- Get the current page

		local entries = pages:GetCurrentPage()

		-- Iterate through all key-value pairs on page

		for _, entry in ipairs(entries) do

			print(entry.key .. " : " .. tostring(entry.value))

		end

		-- Check if last page has been reached

		if pages.IsFinished then

			break

		else

			print("----------")

			-- Advance to next page

			pages:AdvanceToNextPageAsync()

		end

	end

end

```

## [Update data](#update-data)[](#update-data)

To retrieve the value of a key from a hash map and update it, call [MemoryStoreHashMap:UpdateAsync()](/docs/reference/engine/classes/MemoryStoreHashMap#UpdateAsync)  with the key name , a callback function  to update the key, and an expiration time  in seconds.

For most games, multiple servers can update the same key concurrently and change the value. As [UpdateAsync()](/docs/reference/engine/classes/MemoryStoreHashMap#UpdateAsync)  always modifies the latest value before updating, you should use it to read the latest value as the input for your callback function.

For example, the following code sample updates the resource count of a resource in a shared inventory. [UpdateAsync()](/docs/reference/engine/classes/MemoryStoreHashMap#UpdateAsync)  ensures that all player contributions will make their way into this shared inventory, even if these contributions are made simultaneously. In this function, it also enforces a max resource count of 500.

Updating Resource Count for a Resource in a Shared Inventory

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local hashMap = MemoryStoreService:GetHashMap("ResourceInventory")

local function contributeResources(itemResource, addedCount)

	local success, newResourceCount = pcall(function()

		return hashMap:UpdateAsync(itemResource, function(resource)

			resource = resource or {count = 0}

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

```

The latency for [UpdateAsync()](/docs/reference/engine/classes/MemoryStoreHashMap#UpdateAsync)  is similar to [GetAsync()](/docs/reference/engine/classes/MemoryStoreHashMap#GetAsync)  and [SetAsync()](/docs/reference/engine/classes/MemoryStoreHashMap#SetAsync)  unless there is contention.

When contention occurs, the system automatically retries the operation until one of these three happens: the operation succeeds, the callback function returns nil , or the maximum number of retries is reached. If the system reaches the maximum number of retries, it returns a conflict.

## [Remove data](#remove-data)[](#remove-data)

You can use [MemoryStoreHashMap:RemoveAsync()](/docs/reference/engine/classes/MemoryStoreHashMap#RemoveAsync)  for both removing one key from the hash map and deleting all data in a memory store hash map.

### [Remove a key](#remove-a-key)[](#remove-a-key)

To remove a key from the hash map, call [MemoryStoreHashMap:RemoveAsync()](/docs/reference/engine/classes/MemoryStoreHashMap#RemoveAsync)  with a key name .

Remove a Key from a Hash Map

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local hashMap = MemoryStoreService:GetHashMap("HashMap1")

local setSuccess, _ = pcall(function()

	return hashMap:SetAsync("User_1234", 1000, 30)

end)

if setSuccess then

	print("Set succeeded.")

end

local removeSuccess, removeError = pcall(function()

	hashMap:RemoveAsync("User_1234")

end)

if not removeSuccess then

	warn(removeError)

end

```

### [Delete all data](#delete-all-data)[](#delete-all-data)

To delete all data in a hash map, list all your items with [MemoryStoreHashMap:ListItemsAsync()](/docs/reference/engine/classes/MemoryStoreHashMap#ListItemsAsync) , then remove them with [MemoryStoreHashMap:RemoveAsync()](/docs/reference/engine/classes/MemoryStoreHashMap#RemoveAsync) .

Delete all data in a Hash Map

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local hashMap = MemoryStoreService:GetHashMap("HashMap1")

-- Get list of items, 32 items at a time

local success, pages = pcall(function()

	return hashMap:ListItemsAsync(32)

end)

if success then

	while true do

		-- Get the current page

		local entries = pages:GetCurrentPage()

		local removeSuccess = true

		local removeError = nil

		-- Iterate through all key-value pairs on page

		for _, entry in ipairs(entries) do

			print(entry.key .. " : " .. tostring(entry.value))

			removeSuccess, removeError = pcall(function()

				hashMap:RemoveAsync(entry.key)

			end)

			if not removeSuccess then

				warn(removeError)

			end

		end

		-- Check if last page has been reached

		if pages.IsFinished then

			print("Finished deleting all data.")

			break

		else

			print("----------")

			-- Advance to next page

			pages:AdvanceToNextPageAsync()

		end

	end

end

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
