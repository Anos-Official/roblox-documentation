<!-- Source: https://create.roblox.com/docs/cloud-services/data-stores/versioning-listing-and-caching -->

Data store versioning, listing, and caching | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/cloud-services/data-stores/versioning-listing-and-caching.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Cloud services](/docs/cloud-services/data-stores-vs-memory-stores)
6. /
7. [Data stores](/docs/cloud-services/data-stores)

# Data store versioning, listing, and caching

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/cloud-services/data-stores/versioning-listing-and-caching.md)

Manage your data using versioning, listing, and caching.

## [Versioning](#versioning)[](#versioning)

Versioning happens when you [set](/docs/cloud-services/data-stores#create-data) , [update](/docs/cloud-services/data-stores#update-data) , and [increment](/docs/cloud-services/data-stores#increment-data)  data. The functions [SetAsync()](/docs/reference/engine/classes/GlobalDataStore#SetAsync) , [UpdateAsync()](/docs/reference/engine/classes/GlobalDataStore#UpdateAsync) , and [IncrementAsync()](/docs/reference/engine/classes/GlobalDataStore#IncrementAsync)  create versioned backups of your data using the first write to each key in each UTC hour. Successive writes to a key in the same UTC hour permanently overwrite the previous data.

Versioned backups expire 30 days after a new write overwrites them. The latest version never expires.

The following functions perform versioning operations:

| Function | | Description |
| --- | --- |
|

[ListVersionsAsync()](/docs/reference/engine/classes/DataStore#ListVersionsAsync)

 | |

Lists all versions for a key by returning a [DataStoreVersionPages](/docs/reference/engine/classes/DataStoreVersionPages)  instance that you can use to enumerate all version numbers. You can filter versions using a time range.

 |
|

[GetVersionAsync()](/docs/reference/engine/classes/DataStore#GetVersionAsync)

 | |

Retrieves a specific version of a key using the key's version number.

 |
|

[RemoveVersionAsync()](/docs/reference/engine/classes/DataStore#RemoveVersionAsync)

 | |

Deletes a specific version of a key.

This function also creates a tombstone version while retaining the previous version. For example, if you call RemoveAsync("User_1234")  and then try to call GetAsync("User_1234") , you get nil  back. However, you can still use [ListVersionsAsync()](/docs/reference/engine/classes/DataStore#ListVersionsAsync)  and [GetVersionAsync()](/docs/reference/engine/classes/DataStore#GetVersionAsync)  to retrieve older versions of the data.

 |

You can use versioning to handle user requests. If a user reports that a problem occurred at 2020-10-09T01:42, you can revert data to a previous version using the following example:

```

local DataStoreService = game:GetService("DataStoreService")

local gameStore = DataStoreService:GetDataStore("PlayerGame")

local DATA_STORE_KEY = "User_1234"

local maxDate = DateTime.fromUniversalTime(2020, 10, 09, 01, 42)

-- Gets the version closest to the given time

local listSuccess, pages = pcall(function()

    return gameStore:ListVersionsAsync(DATA_STORE_KEY, Enum.SortDirection.Descending, nil, maxDate.UnixTimestampMillis)

end)

if listSuccess then

    local items = pages:GetCurrentPage()

    if #items > 0 then

        -- Reads the closest version

        local closestEntry = items[1]

        local success, value, info = pcall(function()

            return gameStore:GetVersionAsync(DATA_STORE_KEY, closestEntry.Version)

        end)

        -- Restores current value by overwriting it with the closest version

        if success then

            local setOptions = Instance.new("DataStoreSetOptions")

            setOptions:SetMetadata(info:GetMetadata())

            gameStore:SetAsync(DATA_STORE_KEY, value, nil, setOptions)

        end

    else

        -- No entries found

    end

end

```

### [Snapshots](#snapshots)[](#snapshots)

The [Snapshot Data Stores Open Cloud API](/docs/cloud/reference/DataStore#Cloud_SnapshotDataStores)  lets you take a snapshot of all data stores in a game once a day. Before you publish any game update that changes your data storage logic, make sure to take a snapshot. Taking a snapshot guarantees that you have the most recent data available from the previous version of the game.

For example, without a snapshot, if you publish an update at 3:30 UTC that causes data corruption, the corrupted data overwrites any data written between 3:00-3:30 UTC. If you take a snapshot at 3:29 UTC, though, the corrupted data doesn't overwrite anything written before 3:29 UTC, and the latest data for all keys written between 3:00-3:29 UTC is preserved.

## [Listing and prefixes](#listing-and-prefixes)[](#listing-and-prefixes)

Data stores let you list by prefix. For example, listing by the first n  characters of a name, like "d" , "do", or "dog" for any key or data store with a prefix of "dog".

You can specify a prefix when listing all data stores or keys, and get back only objects that match that prefix. Both [ListDataStoresAsync()](/docs/reference/engine/classes/DataStoreService#ListDataStoresAsync)  and [ListKeysAsync()](/docs/reference/engine/classes/DataStore#ListKeysAsync)  functions return a [DataStoreListingPages](/docs/reference/engine/classes/DataStoreListingPages)  object that you can use to enumerate the list.

| Function | | Description |
| [ListDataStoresAsync()](/docs/reference/engine/classes/DataStoreService#ListDataStoresAsync) | | Lists all data stores. |
| [ListKeysAsync()](/docs/reference/engine/classes/DataStore#ListKeysAsync) | | Lists all keys in a data store. |

### [Scopes](#scopes)[](#scopes)

For new games, use [listing and prefixes](#listing-and-prefixes)  to organize keys in your data store instead of the legacy scopes feature. For existing games that use scopes, continue using them.

You can organize keys in a data store further by setting a unique string as a scope for the second parameter of [GetDataStore()](/docs/reference/engine/classes/DataStoreService#GetDataStore) . The default scope (if no scope is given) is global . The scope is automatically prepended to the beginning of all keys in all operations done on the data store.

| Key | | Scope |
| houses/User_1234 | | houses |
| pets/User_1234 | | pets |
| inventory/User_1234 | | inventory |

The combination of data store name, scope, and key uniquely identifies a key. All three values are required to identify a key with a scope. For example, you can read a global -scoped key named User_1234  as:

```

local DataStoreService = game:GetService("DataStoreService")

local inventoryStore = DataStoreService:GetDataStore("PlayerInventory")

local success, currentGold = pcall(function()

  return inventoryStore:GetAsync("User_1234")

end)

```

If the key User_1234  has a scope of gold , though, you can only read it as:

```

local DataStoreService = game:GetService("DataStoreService")

local inventoryStore = DataStoreService:GetDataStore("PlayerInventory", "gold")

local success, currentGold = pcall(function()

  return inventoryStore:GetAsync("User_1234")

end)

```

### [AllScopes property](#allscopes-property)[](#allscopes-property)

[DataStoreOptions](/docs/reference/engine/classes/DataStoreOptions)  contains an [AllScopes](/docs/reference/engine/classes/DataStoreOptions#AllScopes)  property that lets you return keys from all [scopes](#scopes)  in a list. You can then use the [KeyName](/docs/reference/engine/classes/DataStoreKey#KeyName)  property of a list item for common data store operations like [reading data](/docs/cloud-services/data-stores#reading-data)  with [GetAsync()](/docs/reference/engine/classes/GlobalDataStore#GetAsync)  and [removing data](/docs/cloud-services/data-stores#removing-data)  with [RemoveAsync()](/docs/reference/engine/classes/GlobalDataStore#RemoveAsync) .

When you use the AllScopes  property, the second parameter of [GetDataStore()](/docs/reference/engine/classes/DataStoreService#GetDataStore)  must be an empty string ("" ).

```

local DataStoreService = game:GetService("DataStoreService")

local options = Instance.new("DataStoreOptions")

options.AllScopes = true

local ds = DataStoreService:GetDataStore("DS1", "", options)

```

When you use the [AllScopes](/docs/reference/engine/classes/DataStoreOptions#AllScopes)  property, [ListKeysAsync()](/docs/reference/engine/classes/DataStore#ListKeysAsync)  returns every key with their scope as the prefix argument, such as global/player_data_1234  or houses/house3 . Remember that the default scope is global .

If you enable the [AllScopes](/docs/reference/engine/classes/DataStoreOptions#AllScopes)  property and create a new key in the data store, you must always specify a scope for that key in the format of scope/keyname. If you don't, the APIs throw an error. For example, gold/player_34545  is acceptable with gold as the scope, but player_34545  leads to an error.

| global/K1 | | house/K1 |
| global/L2 | | house/L2 |
| global/M3 | | house/M3 |

## [Caching](#caching)[](#caching)

Use caching to temporarily store data from data stores to improve performance and reduce the number of requests made to the server. For example, a game can cache a copy of its data so that it can access that data quickly without having to make another call to the data store.

Caching applies to modifications you make to data store keys using:

-

[GetAsync()](/docs/reference/engine/classes/GlobalDataStore#GetAsync)  to [read data](/docs/cloud-services/data-stores#reading-data) .

-

[SetAsync()](/docs/reference/engine/classes/GlobalDataStore#SetAsync)  to [create data](/docs/cloud-services/data-stores#creating-data) .

-

[UpdateAsync()](/docs/reference/engine/classes/GlobalDataStore#UpdateAsync)  to [update data](/docs/cloud-services/data-stores#updating-data) .

-

[IncrementAsync()](/docs/reference/engine/classes/GlobalDataStore#IncrementAsync)  to [increment data](/docs/cloud-services/data-stores#incrementing-data) .

-

[RemoveAsync()](/docs/reference/engine/classes/GlobalDataStore#RemoveAsync)  to [remove data](/docs/cloud-services/data-stores#removing-data) .

[GetVersionAsync()](/docs/reference/engine/classes/DataStore#GetVersionAsync) , [ListVersionsAsync()](/docs/reference/engine/classes/DataStore#ListVersionsAsync) , [ListKeysAsync()](/docs/reference/engine/classes/DataStore#ListKeysAsync) , and [ListDataStoresAsync()](/docs/reference/engine/classes/DataStoreService#ListDataStoresAsync)  don't implement caching and always fetch the latest data from the service backend.

By default, the engine uses [GetAsync()](/docs/reference/engine/classes/GlobalDataStore#GetAsync)  to store values you retrieve from the backend in a local cache for four seconds. Also by default, [GetAsync()](/docs/reference/engine/classes/GlobalDataStore#GetAsync)  requests for cached keys return the cached value instead of continuing to the backend. Your [GetAsync()](/docs/reference/engine/classes/GlobalDataStore#GetAsync)  requests that return a cached value don't count towards your [server limits](/docs/cloud-services/data-stores/error-codes-and-limits#server-limits)  and [throughput limits](/docs/cloud-services/data-stores/error-codes-and-limits#throughput-limits) .

All [GetAsync()](/docs/reference/engine/classes/GlobalDataStore#GetAsync)  calls that retrieve a value not being cached from the backend update the cache immediately and restart the four second timer.

Caching is local to a particular data store instance, so different data stores can have their caches in different states. For example, if you access a key twice through two different data store instances, like getting one data store with a specified scope and another through having the [AllScopes](/docs/reference/engine/classes/DataStoreOptions#AllScopes)  property enabled, each data store instance has its own cache. If you change the value of that key in one data store instance and not the other, you end up with inconsistent data.

### [Disable caching](#disable-caching)[](#disable-caching)

To disable caching and opt out of using the cache to retrieve the most up-to-date value from the servers, add the [DataStoreGetOptions](/docs/reference/engine/classes/DataStoreGetOptions)  parameter to your [GetAsync()](/docs/reference/engine/classes/GlobalDataStore#GetAsync)  call and set the [UseCache](/docs/reference/engine/classes/DataStoreGetOptions#UseCache)  property to false  to make your request ignore any keys in the cache.

Disabling caching is useful if you have multiple servers writing to a key with high frequency and need to get the latest value from servers. However, it can cause you to consume more of your [data stores limits and quotas](/docs/cloud-services/data-stores/error-codes-and-limits#limits) , since [GetAsync()](/docs/reference/engine/classes/GlobalDataStore#GetAsync)  requests bypassing caching always count towards your throughput and server limits.

For immediate verification reads after a write, use [GetAsync()](/docs/reference/engine/classes/GlobalDataStore#GetAsync)  with DataStoreGetOptions.UseCache = false . By default, [GetAsync()](/docs/reference/engine/classes/GlobalDataStore#GetAsync)  uses a local four-second cache, so a normal verification read can return stale data.

This is especially important after write operations like [UpdateAsync()](/docs/reference/engine/classes/GlobalDataStore#UpdateAsync) , [SetAsync()](/docs/reference/engine/classes/GlobalDataStore#SetAsync) , [IncrementAsync()](/docs/reference/engine/classes/GlobalDataStore#IncrementAsync) , or [RemoveAsync()](/docs/reference/engine/classes/GlobalDataStore#RemoveAsync)  return an error. In these cases, your code needs to determine whether to retry, refund, or take other corrective action.

The following example shows how to bypass the cache when verifying the result of a write:

```

local ok = pcall(function()

    store:UpdateAsync(key, transform)

end)

if not ok then

    local options = Instance.new("DataStoreGetOptions")

    options.UseCache = false

    local success, value = pcall(function()

        return store:GetAsync(key, options)

    end)

    if success then

        -- decide based on backend state, not cached state

    end

end

```

## [Serialization](#serialization)[](#serialization)

The [DataStoreService](/docs/reference/engine/classes/DataStoreService)  stores data in JSON format. When you save Luau data in Studio, Roblox uses a process called serialization to convert that data into JSON to save it in data stores. Roblox then converts your data back to Luau and returns it to you in another process called deserialization.

Serialization and deserialization support the following Luau data types:

-

[Nil](/docs/luau/nil)

-

[Booleans](/docs/luau/booleans)

-

[Numbers](/docs/luau/numbers)

-

You should not store the special numeric values inf , -inf , and nan , because these values don't conform to JSON standards. When you retrieve an entry containing these values through Open Cloud, the response represents them as tagged JSON objects. For details, see [Non-finite numbers](/docs/cloud/guides/data-stores#non-finite-numbers) .

-

[Strings](/docs/luau/strings)

-

[Tables](/docs/luau/tables)

-

Tables must only contain other supported data types

-

Numeric keys are translated into strings if the length of the table is 0

-

[Buffers](/docs/reference/engine/libraries/buffer)

If you try to store a data type that serialization doesn't support, you either:

-

Fail in storing that data type and get an error message.

-

Succeed in storing that data type as nil .

To debug why your data type is being stored as nil , you can use the [JSONEncode](/docs/reference/engine/classes/HttpService#JSONEncode)  function. When you pass your Luau data type into this function, you receive it back in the format Roblox would have stored it with data stores, which lets you preview and investigate the returned data.

Serialization doesn't happen when you use the [DataStore Open Cloud API](/docs/cloud/reference/DataStore)  because that data is already sent to Roblox in JSON format and doesn't need to be converted.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
