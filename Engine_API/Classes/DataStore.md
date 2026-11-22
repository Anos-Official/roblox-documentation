<!-- Source: https://create.roblox.com/docs/reference/engine/classes/DataStore -->

DataStore | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/DataStore.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [GlobalDataStore](/docs/reference/engine/classes/GlobalDataStore)
8. /
9. [DataStore](/docs/reference/engine/classes/DataStore)

English

Feedback

Engine Class

DataStore

Not Creatable

Not Replicated

---

## Summary

Methods

|

[GetVersionAsync](#GetVersionAsync) (key :  [string](/docs/luau/strings) , version :  [string](/docs/luau/strings) ) :[Tuple](/docs/luau/tuples)

 |
| --- | --- |
|

[GetVersionAtTimeAsync](#GetVersionAtTimeAsync) (key :  [string](/docs/luau/strings) , timestamp :  [number](/docs/luau/numbers) ) :[Tuple](/docs/luau/tuples)

 |
|

[ListKeysAsync](#ListKeysAsync) (prefix :  [string](/docs/luau/strings) , pageSize :  [number](/docs/luau/numbers) , cursor :  [string](/docs/luau/strings) , excludeDeleted :  [boolean](/docs/luau/booleans) ) :[DataStoreKeyPages](/docs/reference/engine/classes/DataStoreKeyPages)

 |
|

[ListVersionsAsync](#ListVersionsAsync) (key :  [string](/docs/luau/strings) , sortDirection :  [Enum.SortDirection](/docs/reference/engine/enums/SortDirection) , minDate :  [number](/docs/luau/numbers) , maxDate :  [number](/docs/luau/numbers) , pageSize :  [number](/docs/luau/numbers) ) :[DataStoreVersionPages](/docs/reference/engine/classes/DataStoreVersionPages)

 |
|

[RemoveVersionAsync](#RemoveVersionAsync) (key :  [string](/docs/luau/strings) , version :  [string](/docs/luau/strings) ) : ()

Deprecated

 |

Inherited Members

7  inherited from [GlobalDataStore](/docs/reference/engine/classes/GlobalDataStore)

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Methods

GetVersionAsync

Yields

Capabilities: DataStore

DataStore:GetVersionAsync (

key :[string](/docs/luau/strings) , version :[string](/docs/luau/strings)

) :[Tuple](/docs/luau/tuples)

Parameters

|

key :[string](/docs/luau/strings)

 |
|

version :[string](/docs/luau/strings)

 |

Returns

[Tuple](/docs/luau/tuples)

Provide feedback

---

GetVersionAtTimeAsync

Yields

Capabilities: DataStore

DataStore:GetVersionAtTimeAsync (

key :[string](/docs/luau/strings) , timestamp :[number](/docs/luau/numbers)

) :[Tuple](/docs/luau/tuples)

Parameters

|

key :[string](/docs/luau/strings)

 |
|

timestamp :[number](/docs/luau/numbers)

 |

Returns

[Tuple](/docs/luau/tuples)

Code Samples

Retrieving DataStore Versions by Time

```

local DataStoreService = game:GetService("DataStoreService")

local dataStore = DataStoreService:GetDataStore("DataStore")

local key = "key-123"

function setData(data)

	local success, result = pcall(function()

		dataStore:SetAsync(key, data)

	end)

	if not success then

		warn(result)

	end

end

function getVersionAtTime(timestamp)

	local success, result, keyInfo = pcall(function()

		return dataStore:GetVersionAtTimeAsync(key, timestamp.UnixTimestampMillis)

	end)

	if success then

		if result == nil then

			print("No version found at time")

		else

			print(result, keyInfo.Version)

		end

	else

		warn(result)

	end

end

-- Previously ran at 2024/12/02 6:00 UTC

setData("version 1")

-- Previously ran at 2024/12/02 9:00 UTC

setData("version 2")

-- Prints "No version found at time"

local time1 = DateTime.fromUniversalTime(2024, 12, 02, 05, 00)

getVersionAtTime(time1)

-- Prints "version 1 <version>"

local time2 = DateTime.fromUniversalTime(2024, 12, 02, 07, 00)

getVersionAtTime(time2)

-- Prints "version 2 <version>"

local time3 = DateTime.fromUniversalTime(2024, 12, 02, 10, 00)

getVersionAtTime(time3)

```

Provide feedback

---

ListKeysAsync

Yields

Capabilities: DataStore

DataStore:ListKeysAsync (

prefix :[string](/docs/luau/strings) , pageSize :[number](/docs/luau/numbers) , cursor :[string](/docs/luau/strings) , excludeDeleted :[boolean](/docs/luau/booleans)

) :[DataStoreKeyPages](/docs/reference/engine/classes/DataStoreKeyPages)

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
|

excludeDeleted :[boolean](/docs/luau/booleans)

Default Value: false |

Returns

[DataStoreKeyPages](/docs/reference/engine/classes/DataStoreKeyPages)

Provide feedback

---

ListVersionsAsync

Yields

Capabilities: DataStore

DataStore:ListVersionsAsync (

key :[string](/docs/luau/strings) , sortDirection :[Enum.SortDirection](/docs/reference/engine/enums/SortDirection) , minDate :[number](/docs/luau/numbers) , maxDate :[number](/docs/luau/numbers) , pageSize :[number](/docs/luau/numbers)

) :[DataStoreVersionPages](/docs/reference/engine/classes/DataStoreVersionPages)

Parameters

|

key :[string](/docs/luau/strings)

 |
|

sortDirection :[Enum.SortDirection](/docs/reference/engine/enums/SortDirection)

Default Value: Ascending |
|

minDate :[number](/docs/luau/numbers)

Default Value: 0 |
|

maxDate :[number](/docs/luau/numbers)

Default Value: 0 |
|

pageSize :[number](/docs/luau/numbers)

Default Value: 0 |

Returns

[DataStoreVersionPages](/docs/reference/engine/classes/DataStoreVersionPages)

Code Samples

Retrieving DataStore Versions With A Date Filter

```

local DataStoreService = game:GetService("DataStoreService")

local experienceStore = DataStoreService:GetDataStore("PlayerExperience")

local time = DateTime.fromUniversalTime(2020, 10, 09, 01, 42)

local listSuccess, pages = pcall(function()

	return experienceStore:ListVersionsAsync("User_1234", nil, time.UnixTimestampMillis)

end)

if listSuccess then

	local items = pages:GetCurrentPage()

	for key, info in pairs(items) do

		print("Key:", key, "; Version:", info.Version, "; Created:", info.CreatedTime, "; Deleted:", info.IsDeleted)

	end

end

```

Provide feedback

---

RemoveVersionAsync

Deprecated

Show details

---

Jump to

▼

DataStore

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[GetVersionAsync()](#GetVersionAsync)

[GetVersionAtTimeAsync()](#GetVersionAtTimeAsync)

[ListKeysAsync()](#ListKeysAsync)

[ListVersionsAsync()](#ListVersionsAsync)

[RemoveVersionAsync()](#RemoveVersionAsync)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
