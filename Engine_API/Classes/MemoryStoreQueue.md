<!-- Source: https://create.roblox.com/docs/reference/engine/classes/MemoryStoreQueue -->

MemoryStoreQueue | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/MemoryStoreQueue.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [MemoryStoreQueue](/docs/reference/engine/classes/MemoryStoreQueue)

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

[AddAsync](#AddAsync) (value :  Variant , expiration :  [number](/docs/luau/numbers) , priority :  [number](/docs/luau/numbers) ) : ()

 |
| --- | --- |
|

[GetSizeAsync](#GetSizeAsync) (excludeInvisible :  [boolean](/docs/luau/booleans) ) :[number](/docs/luau/numbers)

 |
|

[ReadAsync](#ReadAsync) (count :  [number](/docs/luau/numbers) , allOrNothing :  [boolean](/docs/luau/booleans) , waitTimeout :  [number](/docs/luau/numbers) ) :[Tuple](/docs/luau/tuples)

 |
|

[RemoveAsync](#RemoveAsync) (id :  [string](/docs/luau/strings) ) : ()

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Methods

AddAsync

Yields

Capabilities: DataStore

MemoryStoreQueue:AddAsync (

value : Variant , expiration :[number](/docs/luau/numbers) , priority :[number](/docs/luau/numbers)

) : ()

Parameters

|

value : Variant

 |
|

expiration :[number](/docs/luau/numbers)

 |
|

priority :[number](/docs/luau/numbers)

Default Value: 0 |

Returns

()

Provide feedback

---

GetSizeAsync

Yields

Capabilities: DataStore

MemoryStoreQueue:GetSizeAsync (excludeInvisible :[boolean](/docs/luau/booleans) ) :[number](/docs/luau/numbers)

Parameters

|

excludeInvisible :[boolean](/docs/luau/booleans)

Default Value: false |

Returns

[number](/docs/luau/numbers)

Provide feedback

---

ReadAsync

Yields

Capabilities: DataStore

MemoryStoreQueue:ReadAsync (

count :[number](/docs/luau/numbers) , allOrNothing :[boolean](/docs/luau/booleans) , waitTimeout :[number](/docs/luau/numbers)

) :[Tuple](/docs/luau/tuples)

Parameters

|

count :[number](/docs/luau/numbers)

 |
|

allOrNothing :[boolean](/docs/luau/booleans)

Default Value: false |
|

waitTimeout :[number](/docs/luau/numbers)

Default Value: -1 |

Returns

[Tuple](/docs/luau/tuples)

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

MemoryStoreQueue:RemoveAsync (id :[string](/docs/luau/strings) ) : ()

Parameters

|

id :[string](/docs/luau/strings)

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
