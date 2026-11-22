<!-- Source: https://create.roblox.com/docs/en-us/cloud-services/data-stores -->

Data stores | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/cloud-services/data-stores.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Cloud services](/docs/en-us/cloud-services/data-stores-vs-memory-stores)
6. /
7. [Data stores](/docs/en-us/cloud-services/data-stores)

# Data stores

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/cloud-services/data-stores/index.md)

The [DataStoreService](/docs/en-us/reference/engine/classes/DataStoreService)  lets you store data that needs to persist between sessions, like items in a player's inventory or skill points. Data stores are consistent per game, so any place in a game can access and change the same data, including places on different servers.

If you want to add granular permission control to your data stores and access them outside of Studio or Roblox servers, you can use [Open Cloud APIs for data stores](/docs/en-us/cloud/reference/DataStore) .

To view and monitor all the data stores in a game through the Creator Hub, use the [Data Stores Manager](/docs/en-us/cloud-services/data-stores/data-stores-manager) .

For temporary data that you need to update or access frequently, use [memory stores](/docs/en-us/cloud-services/memory-stores) .

## [Enable Studio access](#enable-studio-access)[](#enable-studio-access)

By default, games tested in Studio can't access data stores, so you must first enable them. Accessing data stores in Studio can be dangerous for live games because Studio accesses the same data stores as the client application. To avoid overwriting production data, do not enable this setting for live games. Instead, enable it for a separate test version of the game.

To enable Studio access in a [published](/docs/en-us/production/publishing/publish-games-and-places)  game:

1.

Open Studio's File  ⟩ Experience Settings  window.

2.

Navigate to Security .

3.

Enable the Enable Studio Access to API Services  toggle.

4.

Click Save .

## [Access data stores](#access-data-stores)[](#access-data-stores)

To access a data store inside a game:

1.

Add [DataStoreService](/docs/en-us/reference/engine/classes/DataStoreService)  to a server-side [Script](/docs/en-us/reference/engine/classes/Script) .

2.

Use the [GetDataStore()](/docs/en-us/reference/engine/classes/DataStoreService#GetDataStore)  function and specify the name of the data store you want to use. If the data store doesn't exist, Studio creates one when you save your game data for the first time.

```

local DataStoreService = game:GetService("DataStoreService")

local gameStore = DataStoreService:GetDataStore("PlayerGame")

```

The server can only access data stores through [Scripts](/docs/en-us/reference/engine/classes/Script) . Attempting client-side access in a [LocalScript](/docs/en-us/reference/engine/classes/LocalScript)  causes an error.

## [Create data](#create-data)[](#create-data)

A data store is essentially a dictionary, similar to a Luau table. A unique key  indexes each value in the data store, like a user's unique [Player.UserId](/docs/en-us/reference/engine/classes/Player#UserId)  or a named string for a game promo.

| User data key | | Value |
| --- | --- |
| 31250608 | | 50 |
| 351675979 | | 20 |
| 505306092 | | 78000 |
| Promo data key | | Value |
| ActiveSpecialEvent | | SummerParty2 |
| ActivePromoCode | | BONUS123 |
| CanAccessPartyPlace | | true |

To create a new entry, call [SetAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#SetAsync)  with the key name and a value.

```

local DataStoreService = game:GetService("DataStoreService")

local gameStore = DataStoreService:GetDataStore("PlayerGame")

local success, errorMessage = pcall(function()

	gameStore:SetAsync("User_1234", 50)

end)

if not success then

	print(errorMessage)

end

```

Functions like [SetAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#SetAsync)  that access a data store's contents are network calls that might occasionally fail. To catch and handle errors, make sure to wrap these calls in [pcall()](/docs/en-us/reference/engine/globals/LuaGlobals#pcall) .

## [Update data](#update-data)[](#update-data)

To change any stored value in a data store, call [UpdateAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#UpdateAsync)  with the entry's key name and a callback function that defines how you want to update the entry. This callback takes the current value and returns a new value based on the logic you define. If the callback returns nil , the write operation is cancelled and the value isn't updated.

The callback function you pass into [UpdateAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#UpdateAsync)  does not  have permission to yield. It can't contain any yielding functions like [task.wait()](/docs/en-us/reference/engine/libraries/task#wait) .

```

local DataStoreService = game:GetService("DataStoreService")

local nicknameStore = DataStoreService:GetDataStore("Nicknames")

local function makeNameUpper(currentName)

	local nameUpper = string.upper(currentName)

	return nameUpper

end

local success, updatedName = pcall(function()

	return nicknameStore:UpdateAsync("User_1234", makeNameUpper)

end)

if success then

	print("Uppercase Name:", updatedName)

end

```

### [Set vs update](#set-vs-update)[](#set-vs-update)

Use set to quickly update a specific key. The [SetAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#SetAsync)  function:

-

Can cause data inconsistency if two servers try to set the same key at the same time

-

Only counts against the write limit

Use update to handle multi-server attempts. The [UpdateAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#UpdateAsync)  function:

-

Reads the current key value from the server that last updated it before making any changes

-

Is slower because it reads before it writes

-

Counts against both the read and write limits

## [Read data](#read-data)[](#read-data)

To read the value of a data store entry, call [GetAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#GetAsync)  with the entry's key name.

```

local DataStoreService = game:GetService("DataStoreService")

local gameStore = DataStoreService:GetDataStore("PlayerGame")

local success, currentGame = pcall(function()

	return gameStore:GetAsync("User_1234")

end)

if success then

	print(currentGame)

end

```

The values you retrieve using [GetAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#GetAsync)  sometimes can be out of sync with the backend due to the [caching](/docs/en-us/cloud-services/data-stores/versioning-listing-and-caching#caching)  behavior. For more information, see [Disabling caching](/docs/en-us/cloud-services/data-stores/versioning-listing-and-caching#disable-caching) .

## [Increment data](#increment-data)[](#increment-data)

To increment an integer in a data store, call [IncrementAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#IncrementAsync)  with the entry's key name and a number for how much to change the value. [IncrementAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#IncrementAsync)  is a convenience function that lets you avoid calling [UpdateAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#UpdateAsync)  and manually incrementing the integer.

```

local DataStoreService = game:GetService("DataStoreService")

local gameStore = DataStoreService:GetDataStore("PlayerGame")

local success, newGame = pcall(function()

	return gameStore:IncrementAsync("Player_1234", 1)

end)

if success then

	print(newGame)

end

```

## [Remove data](#remove-data)[](#remove-data)

To remove an entry and return the value associated with the key, call [RemoveAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#RemoveAsync) .

```

local DataStoreService = game:GetService("DataStoreService")

local nicknameStore = DataStoreService:GetDataStore("Nicknames")

local success, removedValue = pcall(function()

	return nicknameStore:RemoveAsync("User_1234")

end)

if success then

	print(removedValue)

end

```

## [Metadata](#metadata)[](#metadata)

Ordered data stores don't support [versioning](/docs/en-us/cloud-services/data-stores/versioning-listing-and-caching#versioning)  and metadata, so [DataStoreKeyInfo](/docs/en-us/reference/engine/classes/DataStoreKeyInfo)  is always nil  for keys in an [OrderedDataStore](/docs/en-us/reference/engine/classes/OrderedDataStore) . If you need to support versioning and metadata, use [DataStore](/docs/en-us/reference/engine/classes/DataStore) .

There are two types of metadata associated with keys:

-

Service-defined : Default read-only metadata, like the most recent update time and creation time. Every object has service-defined metadata.

-

User-defined : Custom metadata for tagging and categorization. Defined using the [DataStoreSetOptions](/docs/en-us/reference/engine/classes/DataStoreSetOptions)  object and the [SetMetadata()](/docs/en-us/reference/engine/classes/DataStoreSetOptions#SetMetadata)  function.

To manage metadata, expand the [SetAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#SetAsync) , [UpdateAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#UpdateAsync) , [GetAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#GetAsync) , [IncrementAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#IncrementAsync) , and [RemoveAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#RemoveAsync)  functions.

-

[SetAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#SetAsync)  accepts the optional third and fourth arguments:

-

A table of [UserIds](/docs/en-us/reference/engine/classes/Player#UserId) . This can help with content copyright and intellectual property tracking and removal.

-

A [DataStoreSetOptions](/docs/en-us/reference/engine/classes/DataStoreSetOptions)  object, where you can define custom metadata using the [SetMetadata()](/docs/en-us/reference/engine/classes/DataStoreSetOptions#SetMetadata)  function.

```

local DataStoreService = game:GetService("DataStoreService")

local gameStore = DataStoreService:GetDataStore("PlayerGame")

local setOptions = Instance.new("DataStoreSetOptions")

setOptions:SetMetadata({["GameElement"] = "Fire"})

local success, errorMessage = pcall(function()

    gameStore:SetAsync("User_1234", 50, {1234}, setOptions)

end)

if not success then

    print(errorMessage)

end

```

-

[GetAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#GetAsync) , [IncrementAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#IncrementAsync) , and [RemoveAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#RemoveAsync)  return a second value in the [DataStoreKeyInfo](/docs/en-us/reference/engine/classes/DataStoreKeyInfo)  object. This second value contains both service-defined properties and functions to fetch user-defined metadata.

-

The [GetUserIds()](/docs/en-us/reference/engine/classes/DataStoreKeyInfo#GetUserIds)  function fetches the table of [UserIds](/docs/en-us/reference/engine/classes/Player#UserId)  that you passed to [SetAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#SetAsync) .

-

The [GetMetadata()](/docs/en-us/reference/engine/classes/DataStoreKeyInfo#GetMetadata)  function fetches user-defined metadata that you passed to [SetAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#SetAsync)  through [SetMetadata()](/docs/en-us/reference/engine/classes/DataStoreSetOptions#SetMetadata) .

-

The [Version](/docs/en-us/reference/engine/classes/DataStoreKeyInfo#Version)  property fetches the version of the key.

-

The [CreatedTime](/docs/en-us/reference/engine/classes/DataStoreKeyInfo#CreatedTime)  property fetches the time the key was created, formatted as the number of milliseconds since epoch.

-

The [UpdatedTime](/docs/en-us/reference/engine/classes/DataStoreKeyInfo#UpdatedTime)  property fetches the last time the key was updated, formatted as the number of milliseconds since epoch.

```

local DataStoreService = game:GetService("DataStoreService")

local gameStore = DataStoreService:GetDataStore("PlayerGame")

local success, currentGame, keyInfo = pcall(function()

    return gameStore:GetAsync("User_1234")

end)

if success then

    print(currentGame)

    print(keyInfo.Version)

    print(keyInfo.CreatedTime)

    print(keyInfo.UpdatedTime)

    print(keyInfo:GetUserIds())

    print(keyInfo:GetMetadata())

end

```

-

The callback function of [UpdateAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#UpdateAsync)  takes an additional parameter in the [DataStoreKeyInfo](/docs/en-us/reference/engine/classes/DataStoreKeyInfo)  object that describes the current key state. It returns the modified value, the keys associated with [UserIds](/docs/en-us/reference/engine/classes/Player#UserId) , and the key's metadata.

```

local DataStoreService = game:GetService("DataStoreService")

local nicknameStore = DataStoreService:GetDataStore("Nicknames")

local function makeNameUpper(currentName, keyInfo)

    local nameUpper = string.upper(currentName)

    local userIDs = keyInfo:GetUserIds()

    local metadata = keyInfo:GetMetadata()

    return nameUpper, userIDs, metadata

end

local success, updatedName, keyInfo = pcall(function()

    return nicknameStore:UpdateAsync("User_1234", makeNameUpper)

end)

if success then

    print(updatedName)

    print(keyInfo.Version)

    print(keyInfo.CreatedTime)

    print(keyInfo.UpdatedTime)

    print(keyInfo:GetUserIds())

    print(keyInfo:GetMetadata())

end

```

When calling [SetAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#SetAsync) , [IncrementAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#IncrementAsync) , and [UpdateAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#UpdateAsync) , you must always update metadata definitions with a value, even when there are no changes to the current value. If you don't, you lose the current value.

For limits when defining metadata, see the [metadata limits](/docs/en-us/cloud-services/data-stores/error-codes-and-limits#metadata-limits) .

## [Ordered data stores](#ordered-data-stores)[](#ordered-data-stores)

By default, data stores don't sort their content. If you need to get data in an ordered way, like in persistent leaderboard stats, call [GetOrderedDataStore()](/docs/en-us/reference/engine/classes/DataStoreService#GetOrderedDataStore)  instead of [GetDataStore()](/docs/en-us/reference/engine/classes/DataStoreService#GetDataStore) .

```

local DataStoreService = game:GetService("DataStoreService")

local characterAgeStore = DataStoreService:GetOrderedDataStore("CharacterAges")

```

Ordered data stores support the same basic functions as default data stores, plus the unique [GetSortedAsync()](/docs/en-us/reference/engine/classes/OrderedDataStore#GetSortedAsync)  function. This retrieves multiple sorted keys  based on a specific sorting order, page size, and minimum/maximum values.

The following example sorts character data into pages with three entries, each in descending order, then loops through the pages and outputs each character's name and age.

```

local DataStoreService = game:GetService("DataStoreService")

local characterAgeStore = DataStoreService:GetOrderedDataStore("CharacterAges")

-- Populates ordered data store

local characters = {

	Mars = 19,

	Janus = 20,

	Diana = 18,

	Venus = 25,

	Neptune = 62

}

for char, age in characters do

	local success, errorMessage = pcall(function()

		characterAgeStore:SetAsync(char, age)

	end)

	if not success then

		print(errorMessage)

	end

end

-- Sorts data by descending order into pages of three entries each

local success, pages = pcall(function()

	return characterAgeStore:GetSortedAsync(false, 3)

end)

if success then

	while true do

		-- Gets the current (first) page

		local entries = pages:GetCurrentPage()

		-- Iterates through all key-value pairs on page

		for _, entry in entries do

			print(entry.key .. " : " .. tostring(entry.value))

		end

		-- Checks if last page has been reached

		if pages.IsFinished then

			break

		else

			print("----------")

			-- Advances to next page

			pages:AdvanceToNextPageAsync()

		end

	end

end

```

When you iterate through [GetOrderedDataStore()](/docs/en-us/reference/engine/classes/DataStoreService#GetOrderedDataStore)  using [AdvanceToNextPageAsync()](/docs/en-us/reference/engine/classes/Pages#AdvanceToNextPageAsync) , the limit for requests is the same as the maximum page size you set for an ordered data store. [AdvanceToNextPageAsync()](/docs/en-us/reference/engine/classes/Pages#AdvanceToNextPageAsync)  always has the same limit as the class that originally requires it.

### [Read multiple entries](#read-multiple-entries)[](#read-multiple-entries)

To read multiple ordered data store  entries in a single request, call [BatchGetAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#BatchGetAsync)  with an array of keys. This is the batch counterpart to reading entries one at a time with [GetAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#GetAsync) .

[BatchGetAsync()](/docs/en-us/reference/engine/classes/GlobalDataStore#BatchGetAsync)  returns a dictionary that maps each requested key to a table with a value  field. Keys that don't exist are omitted from the dictionary, so confirm that a key is present before reading its value.

Each key you request counts as one read request, so a single call for N  keys counts as N  requests against the ordered data store [read limit](/docs/en-us/cloud-services/data-stores/error-codes-and-limits#access-limits) .

The following example reads three player scores in a single request, then loops through the keys and outputs each score that exists.

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

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
