<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/GlobalDataStore -->

GlobalDataStore | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/GlobalDataStore.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [GlobalDataStore](/docs/en-us/reference/engine/classes/GlobalDataStore)

English

Feedback

Engine Class

GlobalDataStore

Not Creatable

Not Replicated

---

## Summary

Methods

|

[BatchGetAsync](#BatchGetAsync) (keys :  [{any}](/docs/en-us/luau/tables#arrays) , options :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |
| --- | --- |
|

[GetAsync](#GetAsync) (key :  [string](/docs/en-us/luau/strings) , options :  [DataStoreGetOptions](/docs/en-us/reference/engine/classes/DataStoreGetOptions) ) :[Tuple](/docs/en-us/luau/tuples)

 |
|

[IncrementAsync](#IncrementAsync) (key :  [string](/docs/en-us/luau/strings) , delta :  [number](/docs/en-us/luau/numbers) , userIds :  [{any}](/docs/en-us/luau/tables#arrays) , options :  [DataStoreIncrementOptions](/docs/en-us/reference/engine/classes/DataStoreIncrementOptions) ) : Variant

 |
|

[OnUpdate](#OnUpdate) (key :  [string](/docs/en-us/luau/strings) , callback :  [function](/docs/en-us/luau/functions) ) :[RBXScriptConnection](/docs/en-us/reference/engine/datatypes/RBXScriptConnection)

Deprecated

 |
|

[RemoveAsync](#RemoveAsync) (key :  [string](/docs/en-us/luau/strings) ) :[Tuple](/docs/en-us/luau/tuples)

 |
|

[SetAsync](#SetAsync) (key :  [string](/docs/en-us/luau/strings) , value :  Variant , userIds :  [{any}](/docs/en-us/luau/tables#arrays) , options :  [DataStoreSetOptions](/docs/en-us/reference/engine/classes/DataStoreSetOptions) ) : Variant

 |
|

[UpdateAsync](#UpdateAsync) (key :  [string](/docs/en-us/luau/strings) , transformFunction :  [function](/docs/en-us/luau/functions) ) :[Tuple](/docs/en-us/luau/tuples)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Inherited by

[DataStore](/docs/en-us/reference/engine/classes/DataStore) , [OrderedDataStore](/docs/en-us/reference/engine/classes/OrderedDataStore)

---

API Reference

Methods

BatchGetAsync

Yields

Capabilities: DataStore

GlobalDataStore:BatchGetAsync (

keys :[{any}](/docs/en-us/luau/tables#arrays) , options :[Dictionary](/docs/en-us/luau/tables#dictionaries)

) :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Parameters

|

keys :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

options :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Default Value: nil |

Returns

[Dictionary](/docs/en-us/luau/tables#dictionaries)

Code Samples

Batch retrieve player scores

```

local DataStoreService = game:GetService("DataStoreService")

local playerScores = DataStoreService:GetOrderedDataStore("PlayerScores")

local keys = {"Player_123", "Player_456", "Player_789"}

local success, results = pcall(function()

	return playerScores:BatchGetAsync(keys)

end)

if success then

	for _, key in keys do

		local entry = results[key]

		if entry then

			print(key .. " : " .. tostring(entry.value))

		else

			print(key .. " has no saved entry")

		end

	end

end

```

Provide feedback

---

GetAsync

Yields

Capabilities: DataStore

GlobalDataStore:GetAsync (

key :[string](/docs/en-us/luau/strings) , options :[DataStoreGetOptions](/docs/en-us/reference/engine/classes/DataStoreGetOptions)

) :[Tuple](/docs/en-us/luau/tuples)

Parameters

|

key :[string](/docs/en-us/luau/strings)

 |
|

options :[DataStoreGetOptions](/docs/en-us/reference/engine/classes/DataStoreGetOptions)

Default Value: nil |

Returns

[Tuple](/docs/en-us/luau/tuples)

Provide feedback

---

IncrementAsync

Yields

Capabilities: DataStore

GlobalDataStore:IncrementAsync (

key :[string](/docs/en-us/luau/strings) , delta :[number](/docs/en-us/luau/numbers) , userIds :[{any}](/docs/en-us/luau/tables#arrays) , options :[DataStoreIncrementOptions](/docs/en-us/reference/engine/classes/DataStoreIncrementOptions)

) : Variant

Parameters

|

key :[string](/docs/en-us/luau/strings)

 |
|

delta :[number](/docs/en-us/luau/numbers)

Default Value: 1 |
|

userIds :[{any}](/docs/en-us/luau/tables#arrays)

Default Value: {} |
|

options :[DataStoreIncrementOptions](/docs/en-us/reference/engine/classes/DataStoreIncrementOptions)

Default Value: nil |

Returns

Variant

Provide feedback

---

OnUpdate

Deprecated

Show details

---

RemoveAsync

Yields

Capabilities: DataStore

GlobalDataStore:RemoveAsync (key :[string](/docs/en-us/luau/strings) ) :[Tuple](/docs/en-us/luau/tuples)

Parameters

|

key :[string](/docs/en-us/luau/strings)

 |

Returns

[Tuple](/docs/en-us/luau/tuples)

Provide feedback

---

SetAsync

Yields

Capabilities: DataStore

GlobalDataStore:SetAsync (

key :[string](/docs/en-us/luau/strings) , value : Variant , userIds :[{any}](/docs/en-us/luau/tables#arrays) , options :[DataStoreSetOptions](/docs/en-us/reference/engine/classes/DataStoreSetOptions)

) : Variant

Parameters

|

key :[string](/docs/en-us/luau/strings)

 |
|

value : Variant

 |
|

userIds :[{any}](/docs/en-us/luau/tables#arrays)

Default Value: {} |
|

options :[DataStoreSetOptions](/docs/en-us/reference/engine/classes/DataStoreSetOptions)

Default Value: nil |

Returns

Variant

Provide feedback

---

UpdateAsync

Yields

Capabilities: DataStore

GlobalDataStore:UpdateAsync (

key :[string](/docs/en-us/luau/strings) , transformFunction :[function](/docs/en-us/luau/functions)

) :[Tuple](/docs/en-us/luau/tuples)

Parameters

|

key :[string](/docs/en-us/luau/strings)

 |
|

transformFunction :[function](/docs/en-us/luau/functions)

 |

Returns

[Tuple](/docs/en-us/luau/tuples)

Provide feedback

---

Jump to

▼

GlobalDataStore

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[BatchGetAsync()](#BatchGetAsync)

[GetAsync()](#GetAsync)

[IncrementAsync()](#IncrementAsync)

[OnUpdate()](#OnUpdate)

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
