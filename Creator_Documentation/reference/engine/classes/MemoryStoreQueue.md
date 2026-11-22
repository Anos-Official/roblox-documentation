<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/MemoryStoreQueue -->

MemoryStoreQueue | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/MemoryStoreQueue.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [MemoryStoreQueue](/docs/en-us/reference/engine/classes/MemoryStoreQueue)

English

Feedback

Engine Class

MemoryStoreQueue

Not Creatable

Not Replicated

---

## Summary

Methods

|

[AddAsync](#AddAsync) (value :  Variant , expiration :  [number](/docs/en-us/luau/numbers) , priority :  [number](/docs/en-us/luau/numbers) ) : ()

 |
| --- | --- |
|

[GetSizeAsync](#GetSizeAsync) (excludeInvisible :  [boolean](/docs/en-us/luau/booleans) ) :[number](/docs/en-us/luau/numbers)

 |
|

[ReadAsync](#ReadAsync) (count :  [number](/docs/en-us/luau/numbers) , allOrNothing :  [boolean](/docs/en-us/luau/booleans) , waitTimeout :  [number](/docs/en-us/luau/numbers) ) :[Tuple](/docs/en-us/luau/tuples)

 |
|

[RemoveAsync](#RemoveAsync) (id :  [string](/docs/en-us/luau/strings) ) : ()

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Methods

AddAsync

Yields

Capabilities: DataStore

MemoryStoreQueue:AddAsync (

value : Variant , expiration :[number](/docs/en-us/luau/numbers) , priority :[number](/docs/en-us/luau/numbers)

) : ()

Parameters

|

value : Variant

 |
|

expiration :[number](/docs/en-us/luau/numbers)

 |
|

priority :[number](/docs/en-us/luau/numbers)

Default Value: 0 |

Returns

()

Provide feedback

---

GetSizeAsync

Yields

Capabilities: DataStore

MemoryStoreQueue:GetSizeAsync (excludeInvisible :[boolean](/docs/en-us/luau/booleans) ) :[number](/docs/en-us/luau/numbers)

Parameters

|

excludeInvisible :[boolean](/docs/en-us/luau/booleans)

Default Value: false |

Returns

[number](/docs/en-us/luau/numbers)

Provide feedback

---

ReadAsync

Yields

Capabilities: DataStore

MemoryStoreQueue:ReadAsync (

count :[number](/docs/en-us/luau/numbers) , allOrNothing :[boolean](/docs/en-us/luau/booleans) , waitTimeout :[number](/docs/en-us/luau/numbers)

) :[Tuple](/docs/en-us/luau/tuples)

Parameters

|

count :[number](/docs/en-us/luau/numbers)

 |
|

allOrNothing :[boolean](/docs/en-us/luau/booleans)

Default Value: false |
|

waitTimeout :[number](/docs/en-us/luau/numbers)

Default Value: -1 |

Returns

[Tuple](/docs/en-us/luau/tuples)

Code Samples

Using a MemoryStoreQueue

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local DataStoreService = game:GetService("DataStoreService")

local queue = MemoryStoreService:GetQueue("PlayerQueue")

local dataStore = DataStoreService:GetDataStore("PlayerStore")

while true do

	pcall(function()

		-- wait for an item to process

		local items, id = queue:ReadAsync(1, false, 30)

		-- check if an item was retrieved

		if #items > 0 then

			-- mark the item as processed

			dataStore:UpdateAsync(items[0], function(data)

				data = data or {}

				data.processed = 1

				return data

			end)

			-- remove the item from the queue

			queue:RemoveAsync(id)

		end

	end)

end

```

Provide feedback

---

RemoveAsync

Yields

Capabilities: DataStore

MemoryStoreQueue:RemoveAsync (id :[string](/docs/en-us/luau/strings) ) : ()

Parameters

|

id :[string](/docs/en-us/luau/strings)

 |

Returns

()

Code Samples

Using a MemoryStoreQueue

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local DataStoreService = game:GetService("DataStoreService")

local queue = MemoryStoreService:GetQueue("PlayerQueue")

local dataStore = DataStoreService:GetDataStore("PlayerStore")

while true do

	pcall(function()

		-- wait for an item to process

		local items, id = queue:ReadAsync(1, false, 30)

		-- check if an item was retrieved

		if #items > 0 then

			-- mark the item as processed

			dataStore:UpdateAsync(items[0], function(data)

				data = data or {}

				data.processed = 1

				return data

			end)

			-- remove the item from the queue

			queue:RemoveAsync(id)

		end

	end)

end

```

Provide feedback

---

Jump to

▼

MemoryStoreQueue

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[AddAsync()](#AddAsync)

[GetSizeAsync()](#GetSizeAsync)

[ReadAsync()](#ReadAsync)

[RemoveAsync()](#RemoveAsync)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
