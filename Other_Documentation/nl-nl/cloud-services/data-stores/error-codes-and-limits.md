<!-- Source: https://create.roblox.com/docs/nl-nl/cloud-services/data-stores/error-codes-and-limits -->

Data store error codes and limits | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Clouddiensten](/docs/nl-nl/cloud-services/data-stores-vs-memory-stores)
6. /
7. [Gegevensopslag](/docs/nl-nl/cloud-services/data-stores)

# Data store error codes and limits

* Deze inhoud is binnenkort beschikbaar in je geselecteerde taal.

Nederlands

[Bewerken](https://github.com/Roblox/creator-docs/blob/main/content/en-us/cloud-services/data-stores/error-codes-and-limits.md)

This page lists the limits that data stores enforce on requests, data, throughput, and storage, followed by the error codes that failed requests return.

## [Limits](#limits)[](#limits)

Data models have limits . If an experience exceeds these limits, the service automatically throttles the experience's data store usage and causes future requests to be placed in one of the following queues:

-

Set

-

Ordered set

-

Get

-

Ordered get

Requests in a queue are handled in the order they are received. The called function continues to yield as long as its request is still queued. If the data store key itself is throttled, the request is placed in a queue but is temporarily skipped.

Each queue has a limit of 30 requests. When the limit of a queue is reached, requests fail with an error code in the 301-306 range, indicating that the requests have been dropped entirely.

### [Data limits](#data-limits)[](#data-limits)

Data stores limit how much data can be used per entry.

The data store name, key name, and [scope](/docs/nl-nl/cloud-services/data-stores/versioning-listing-and-caching#scopes)  must all be under a certain character length. Use [string.len()](/docs/nl-nl/reference/engine/libraries/string#len)  to check their length.

The data (key value) is also stored as a string, regardless of its initial type. You can check the size of the data with the [JSONEncode()](/docs/nl-nl/reference/engine/classes/HttpService#JSONEncode)  function, which converts Luau data into a serialized JSON table.

| Component | | Maximum number of characters |
| --- | --- |
| Data store name | | 50 |
| Key name | | 50 |
| Scope | | 50 |
| Data (key value) | | 4,194,304 per key |

### [Metadata limits](#metadata-limits)[](#metadata-limits)

Limits to the number of characters in user-defined metadata.

| Component | | Maximum number of characters |
| Key name | | 50 |
| Value | | 250 |
| Key-value pairs | | 300 |

There's no limit to the total number of key-value pairs, but the total size can't exceed 300 characters.

### [Throughput limits](#throughput-limits)[](#throughput-limits)

Per-key throughput limits ensure that performance is optimal on Roblox servers. Each limit applies to every single key across all servers in an experience and refreshes over time.

Roblox examines the usage of quota associated with the key over the last 60 seconds. If the usage, including the current request, is within the throughput limit, the request is approved. If the usage exceeds the limit, the request is denied.

| Request type | | Game server API | | Open Cloud API | | Limit |
| Read | | [GetAsync()](/docs/nl-nl/reference/engine/classes/DataStore#GetAsync)
[GetVersionAsync()](/docs/nl-nl/reference/engine/classes/DataStore#GetVersionAsync)
[GetVersionAtTimeAsync()](/docs/nl-nl/reference/engine/classes/DataStore#GetVersionAtTimeAsync)
[ListVersionsAsync()](/docs/nl-nl/reference/engine/classes/DataStore#ListVersionsAsync)
[UpdateAsync()](/docs/nl-nl/reference/engine/classes/DataStore#UpdateAsync) | | Get Data Store Entry | | 25 MB per minute |
| Write | | [SetAsync()](/docs/nl-nl/reference/engine/classes/DataStore#SetAsync)
[IncrementAsync()](/docs/nl-nl/reference/engine/classes/DataStore#IncrementAsync)
[UpdateAsync()](/docs/nl-nl/reference/engine/classes/DataStore#UpdateAsync)
[RemoveAsync()](/docs/nl-nl/reference/engine/classes/DataStore#RemoveAsync) | | Create, Update, Increment, Remove Data Store Entry | | 4 MB per minute |

In addition to the above throughput limits, Roblox organizes data into partitions based on an internal schema. As a result, when the backend server receives a high volume of requests to the same data store, it can result in further throttling. Regardless of the cause, throttling manifests as either DatastoreThrottled  or KeyThrottled  errors, depending on whether the throughput limit was exceeded for a single data store or a key. These error messages apply to both ordered and standard data stores.

For every request, Roblox rounds throughput up to the next kilobyte. For example, if you write 800 bytes and 1.2 KB in two requests, Roblox counts that as 3 KB total throughput (1 KB and 2 KB, respectively).

### [Storage limits](#storage-limits)[](#storage-limits)

To keep storage stable and scalable, data stores use a game-level limit on your storage usage.

This limit consists of a base allocation for each game plus an additional allocation based on the number of lifetime users. A lifetime user is any user who has joined your game at least once.

The storage limit is calculated using the following formula Total latest version storage limit = 500 MB + 1 MB × lifetime user count .

Storage usage is measured using the compressed size  of the latest version of each key. Data stores automatically compress your data before storage, so avoid pre-compressing it yourself. Pre-compression adds unnecessary CPU overhead and may reduce the effectiveness of data stores' built-in compression. By storing uncompressed data, you automatically benefit from improvements to Roblox's compression algorithms and future schema-based optimizations.

Only the latest version of each key counts toward your storage usage. Deleted keys and superseded versions, while still accessible through version APIs during their retention period, do not count toward your storage usage. However, data stores deleted through the Open Cloud [DeleteDataStore](/docs/nl-nl/cloud/reference/features/storage#Cloud_DeleteDataStore)  method continue to count toward storage usage during their 30-day deletion processing period, until they are permanently removed.

### [Access limits](#access-limits)[](#access-limits)

Data stores are subject to both ** experience and server-level limits** . Experience-level limits scale with total concurrent users across the experience, while server-level limits are configurable and meant to be used as a tool by the creator.

#### Experience Limits

Each experience is allowed a certain number of data store requests based on the data store type, request type, and number of concurrent users. For each data store type and request type, the limit is shared among all listed functions.

-

[UpdateAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync)  consumes from both the read and write request budgets. A single call will decrement both limits.

-

Game server and Open Cloud share  a budget; Open Cloud traffic can be throttled by in-experience usage (and vice versa). See [Control rate limits](#control-rate-limits)  for further guidance.

##### Standard data stores

| Request type | | Game server API | | Open Cloud API | | Shared limits (requests per minute) |
| ** Read** | | [GetAsync()](/docs/nl-nl/reference/engine/classes/DataStore#GetAsync)
[GetVersionAsync()](/docs/nl-nl/reference/engine/classes/DataStore#GetVersionAsync)
[GetVersionAtTimeAsync()](/docs/nl-nl/reference/engine/classes/DataStore#GetVersionAtTimeAsync)
[UpdateAsync()](/docs/nl-nl/reference/engine/classes/DataStore#UpdateAsync) | | Get Data Store Entry | | 300 + concurrentUsers × 40 |
| ** Write** | | [SetAsync()](/docs/nl-nl/reference/engine/classes/DataStore#SetAsync)
[IncrementAsync()](/docs/nl-nl/reference/engine/classes/DataStore#IncrementAsync)
[UpdateAsync()](/docs/nl-nl/reference/engine/classes/DataStore#UpdateAsync) | | Create, Update, Increment Data Store Entry | | 300 + concurrentUsers × 20 |
| ** List** | | [ListDataStoresAsync()](/docs/nl-nl/reference/engine/classes/DataStoreService#ListDataStoresAsync)
[ListKeysAsync()](/docs/nl-nl/reference/engine/classes/DataStore#ListKeysAsync)
[ListVersionsAsync()](/docs/nl-nl/reference/engine/classes/DataStore#ListVersionsAsync) | | List Data Stores, List Data Store Entries, List Data Store Entry Revisions | | 300 + concurrentUsers × 2 |
| ** Remove** | | [RemoveAsync()](/docs/nl-nl/reference/engine/classes/DataStore#RemoveAsync) | | Delete Data Store Entry, Delete Data Store, Undelete Data Store | | 300 + concurrentUsers × 40 |

##### Ordered data stores

| Request type | | Game server API | | Open Cloud API | | Shared limits (requests per minute) |
| ** Read** | | [GetAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#GetAsync)
[BatchGetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#BatchGetAsync)
[UpdateAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#UpdateAsync) | | Get Ordered Data Store Entry | | 300 + concurrentUsers × 40 |
| ** Write** | | [SetAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#SetAsync)
[IncrementAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#IncrementAsync)
[UpdateAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#UpdateAsync) | | Create, Update, Increment Ordered Data Store Entry | | 300 + concurrentUsers × 20 |
| ** List** | | [GetSortedAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#GetSortedAsync) | | List Ordered Data Store Entries | | 300 + concurrentUsers × 2 |
| ** Remove** | | [RemoveAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#RemoveAsync) | | Delete Ordered Data Store Entry | | 300 + concurrentUsers × 40 |

##### [Control rate limits](#control-rate-limits)[](#control-rate-limits)

Because Open Cloud and game server requests are shared, it is important to independently control how much each can consume from the budget.

###### Game server

Individual servers have built-in limits, as described above. Use a combination of [SetRateLimitForRequestType()](/docs/nl-nl/reference/engine/classes/DataStoreService#SetRateLimitForRequestType)  and [GetRequestBudgetForRequestType()](/docs/nl-nl/reference/engine/classes/DataStoreService#GetRequestBudgetForRequestType)  to maintain fine-grained control over individual servers' contribution to the total budget.

###### Open Cloud

Open Cloud requests require an external rate limiting solution. We recommend one of the following approaches:

-

(Simple) Add a short timeout after each request, especially if calling the same API in a continuous loop. Set this timeout equal to 60 / (desired budget consumption per minute)  seconds, as an upper bound. Note that this approach does not allow requests to be sent in bursts.

-

(Robust) Implement a local rate limiter using the leaky bucket strategy.

The following Node.js code samples include reference implementations.

Timeout rate limiting Leaky bucket rate limiting

```

const apiKey = process.env.API_KEY;

if (!apiKey) {

    throw new Error('The API_KEY environment variable is not set.');

}

const apiHeaderKey = 'x-api-key';

const universeId = '';

const dataStoreId = 'Inventory';

const baseUrl = 'https://apis.roblox.com/cloud/v2/';

// --- Per-operation rate limiting config (requests per minute) ---

const LIST_RATE_PER_MIN = 60;

const GET_RATE_PER_MIN = 120;

const UPDATE_RATE_PER_MIN = 60;

// Upper-bound spacing per operation: 60 / (requests per min) seconds.

const LIST_INTERVAL_MS = (60 / LIST_RATE_PER_MIN) * 1000;

const GET_INTERVAL_MS = (60 / GET_RATE_PER_MIN) * 1000;

const UPDATE_INTERVAL_MS = (60 / UPDATE_RATE_PER_MIN) * 1000;

const sleep = (ms) => new Promise((resolve) => setTimeout(resolve, ms));

// Performs the request, then waits this operation's own interval before returning.

async function throttledFetch(url, options, intervalMs) {

    const response = await fetch(url, options);

    await sleep(intervalMs);

    return response;

}

async function listEntries(universe, dataStore) {

    const listPath = `universes/${universe}/data-stores/${dataStore}/entries`;

    const url = baseUrl + listPath;

    const response = await throttledFetch(url, {

        headers: { [apiHeaderKey]: apiKey }

    }, LIST_INTERVAL_MS);

    return response.json();

}

async function getEntry(path) {

    const url = baseUrl + path;

    const response = await throttledFetch(url, {

        headers: { [apiHeaderKey]: apiKey }

    }, GET_INTERVAL_MS);

    return response.json();

}

async function updateEntry(path, payload) {

    const url = baseUrl + path;

    const response = await throttledFetch(url, {

        method: 'PATCH',

        headers: {

            [apiHeaderKey]: apiKey,

            'Content-Type': 'application/json'

        },

        body: JSON.stringify(payload) // The body must be a string

    }, UPDATE_INTERVAL_MS);

    return response;

}

(async () => {

    try {

        const entries = await listEntries(universeId, dataStoreId);

        for (const entry of entries.dataStoreEntries) {

            const path = entry.path;

            console.log(`\nProcessing entry: ${path}`);

            const currentData = await getEntry(path);

            currentData.value.currency += 10;

            const payload = { value: currentData.value };

            const updateResponse = await updateEntry(path, payload);

            console.log(`Status: ${updateResponse.status}`);

            console.log(`Response: ${await updateResponse.text()}`);

        }

    } catch (error) {

        console.error('An error occurred during execution:', error);

    }

})();

```

#### Server limits

Each server has a configurable rate limit for each request type, based on the number of players in that server. Servers receive a one-time startup burst of additional request budget when they are first created. Use [GetRequestBudgetForRequestType()](/docs/nl-nl/reference/engine/classes/DataStoreService#GetRequestBudgetForRequestType)  to confirm the number of data store requests that the current server can make at any given time.

These limits are configurable by the creator  using the [SetRateLimitForRequestType()](/docs/nl-nl/reference/engine/classes/DataStoreService#SetRateLimitForRequestType)  API. Using this API, a creator can configure their own data stores rate limits for each request type.

The following default rate limits  apply if the API is not called:

##### Standard data stores

| Request type | | DataStoreRequestType  Enum | | Game server API | | Requests per minute |
| ** Read** | | StandardRead | | [GetAsync()](/docs/nl-nl/reference/engine/classes/DataStore#GetAsync)
[GetVersionAsync()](/docs/nl-nl/reference/engine/classes/DataStore#GetVersionAsync)
[GetVersionAtTimeAsync()](/docs/nl-nl/reference/engine/classes/DataStore#GetVersionAtTimeAsync)
[UpdateAsync()](/docs/nl-nl/reference/engine/classes/DataStore#UpdateAsync) | | 60 + numPlayers × 40 |
| ** Write** | | StandardWrite | | [SetAsync()](/docs/nl-nl/reference/engine/classes/DataStore#SetAsync)
[IncrementAsync()](/docs/nl-nl/reference/engine/classes/DataStore#IncrementAsync)
[UpdateAsync()](/docs/nl-nl/reference/engine/classes/DataStore#UpdateAsync) | | 60 + numPlayers × 40 |
| ** List** | | StandardList | | [ListDataStoresAsync()](/docs/nl-nl/reference/engine/classes/DataStoreService#ListDataStoresAsync)
[ListKeysAsync()](/docs/nl-nl/reference/engine/classes/DataStore#ListKeysAsync)
[ListVersionsAsync()](/docs/nl-nl/reference/engine/classes/DataStore#ListVersionsAsync) | | 5 + numPlayers × 2 |
| ** Remove** | | StandardRemove | | [RemoveAsync()](/docs/nl-nl/reference/engine/classes/DataStore#RemoveAsync) | | 60 + numPlayers × 40 |
| ** RemoveVersion (Deprecated)** | | RemoveVersionAsync | | [RemoveVersionAsync()](/docs/nl-nl/reference/engine/classes/DataStore#RemoveVersionAsync) | | 5 + numPlayers × 2 |

##### Ordered data stores

| Request type | | DataStoreRequestType  Enum | | Game server API | | Requests per minute |
| ** Read** | | OrderedRead | | [GetAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#GetAsync)
[BatchGetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#BatchGetAsync)
[UpdateAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#UpdateAsync) | | 60 + numPlayers × 40 |
| ** Write** | | OrderedWrite | | [SetAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#SetAsync)
[IncrementAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#IncrementAsync)
[UpdateAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#UpdateAsync) | | 30 + numPlayers × 5 |
| ** List** | | OrderedList | | [GetSortedAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#GetSortedAsync) | | 5 + numPlayers × 2 |
| ** Remove** | | OrderedRemove | | [RemoveAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#RemoveAsync) | | 30 + numPlayers × 5 |

Data store requests made in Studio Run mode are subject to a separate set of static limits, which may be lower than the limits configured with [SetRateLimitForRequestType()](/docs/nl-nl/reference/engine/classes/DataStoreService#SetRateLimitForRequestType) . When testing rate limits, we recommend using Studio Team Create instead.

## [Error code reference](#error-code-reference)[](#error-code-reference)

Requests you make to data stores can fail due to poor connectivity or other issues. To handle errors and return messages with an error code, wrap data store functions in [pcall()](/docs/nl-nl/reference/engine/globals/LuaGlobals#pcall) .

A failed write call, such as [UpdateAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync) , means the game server did not receive a successful response. It does not always guarantee that the backend write did not occur. In some failure scenarios, the final write state may be unknown to the caller until it is verified with a follow-up read without cache.

| Error code | | Error name | | Error message | | Notes |
| 101 | | KeyNameEmpty | | Key name can't be empty. | | Check if the key input into the data store function is an empty string. |
| 102 | | KeyNameLimit | | Key name exceeds the 50 character limit. | | Check if the key input into the data store function exceeds a length of 50. |
| 103 | | ValueNotAllowed | | Can't allow ** X**  in DataStore . | | A bad update function returned a value of type ** X** . |
| 104 | | CantStoreValue | | Can't store ** X**  in DataStore . | | The update function returned a value of type ** X**  that didn't serialize. |
| 105 | | ValueTooLarge | | Serialized value exceeds ** X**  limit. | | If you're setting a value with [SetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#SetAsync)  or [UpdateAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync) , the serialized length of the value can't exceed the size ** X** . To check the serialized length of the data, use [JSONEncode()](/docs/nl-nl/reference/engine/classes/HttpService#JSONEncode) . |
| 106 | | MaxValueInvalid | | MaxValue  must be an integer. | | If you're passing a maximum value to [GetSortedAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#GetSortedAsync)  for an [OrderedDataStore](/docs/nl-nl/reference/engine/classes/OrderedDataStore) , it must be an integer. |
| 106 | | MinValueInvalid | | MinValue  must be an integer. | | If you're passing a minimum value to [GetSortedAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#GetSortedAsync)  for an [OrderedDataStore](/docs/nl-nl/reference/engine/classes/OrderedDataStore) , it must be an integer. |
| 106 | | PageSizeGreater | | PageSize  must be within a predefined range. | | The minimum page size for an [OrderedDataStore](/docs/nl-nl/reference/engine/classes/OrderedDataStore)  is 1. |
| 106 | | PageSizeLesser | | PageSize  must be within a predefined range. | | The maximum page size for an [OrderedDataStore](/docs/nl-nl/reference/engine/classes/OrderedDataStore)  is 100. |
| 107 | | MinMaxOrderInvalid | | MaxValue  must be greater than or equal to MinValue . | | The maximum value must be greater than or equal to the minimum value for [GetSortedAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#GetSortedAsync) . |
| 301 | | GetAsyncThrottle | | GetAsync  request dropped. Request was throttled but queue was full. | | [GetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#GetAsync)  request has exceeded the maximum queue size and Roblox is unable to process the requests at the current throughput. |
| 302 | | SetAsyncThrottle | | SetAsync  request dropped. Request was throttled but queue was full. | | [SetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#SetAsync)  request has exceeded the maximum queue size and Roblox is unable to process the requests at the current throughput. |
| 303 | | IncreAsyncThrottle | | IncrementAsync  request dropped. Request was throttled but queue was full. | | [IncrementAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#IncrementAsync)  request has exceeded the maximum queue size and Roblox is unable to process the requests at the current throughput. |
| 304 | | UpdateAsyncThrottle | | UpdateAsync  request dropped. Request was throttled but queue was full. | | [UpdateAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync)  request has exceeded the maximum queue size and Roblox is unable to process the requests at the current throughput. |
| 304 | | TransformThrottle | | UpdateAsync  request dropped. Request was throttled but queue was full. | | [UpdateAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync)  request has exceeded the maximum queue size and Roblox is unable to process the requests at the current throughput. |
| 305 | | GetSortedThrottle | | GetSorted  request dropped. Request was throttled but queue was full. | | [GetSortedAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#GetSortedAsync)  request has exceeded the maximum queue size and Roblox is unable to process the requests at the current throughput. |
| 306 | | RemoveAsyncThrottle | | RemoveAsync  request dropped. Request was throttled but queue was full. | | [RemoveAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#RemoveAsync)  request has exceeded the maximum queue size and Roblox is unable to process the requests at the current throughput. |
| 401 | | DataModelNoAccess | | Request failed. DataModel  is inaccessible while the experience is shutting down. | | [DataModel](/docs/nl-nl/reference/engine/classes/DataModel)  is uninitialized because the experience is shutting down. |
| 402 | | LuaWebSrvsNoAccess | | Request failed. LuaWebService  is inaccessible while the experience is shutting down. | | [LuaWebService](/docs/nl-nl/reference/engine/classes/LuaWebService)  is uninitialized because the experience is shutting down. |
| 403 | | StudioAccessToApisNotAllowed | | Can't write to DataStore  from Studio because API access is not enabled. | | API access must be active in order to use data stores in Studio. |
| 404 | | InternalError | | OrderedDataStore  doesn't exist. | | The [OrderedDataStore](/docs/nl-nl/reference/engine/classes/OrderedDataStore)  associated with this request wasn't found. This might be a sign of data corruption. Try again later. |
| 501 | | InternalError | | Can't parse response because data might be corrupted. | | The server was unable to parse the response to your request. This might be a sign of data corruption. Try again later. |
| 502 | | RequestRejected | | API Services rejected the request with error ** X** . | | Error ** X**  occurred when processing on Roblox servers. Try again later. |
| 503 | | InternalError | | Data store request was successful but key wasn't found. | | The key requested wasn't found in the data store. This might be a sign of data corruption. Try again later. |
| 504 | | InternalError | | Data store request was successful but the response wasn't formatted correctly. | | The server was unable to parse the response to your request. This might be a sign of data corruption. Try again later. |
| 505 | | InternalError | | OrderedDataStore  request was successful but the response wasn't formatted correctly. | | The server was unable to parse the response to your [OrderedDataStore](/docs/nl-nl/reference/engine/classes/OrderedDataStore)  request. This might be a sign of data corruption. Try again later. |
| 509 | | OperationNotAllowed | | Data store operations are blocked while running on a Personal RCC to prevent possible data corruption. | | Data store writes are blocked on private RCC channels. |
| 511 | | AttributeSizeTooLarge | | Metadata attribute size exceeds ** X**  limit. | | The serialized metadata size exceeds the limit of ** X** . The value ** X**  is dynamic. If the size changes, the value also changes. |
| 512 | | UserIdLimitExceeded | | UserID  size exceeds ** X**  limit. | | The length of the user IDs array provided by the user exceeds the limit of ** X** . |
| 513 | | AttributeFormatError | | Attribute userId  format is invalid. | | The user ID provided isn't a number. |
| 513 | | AttributeFormatError | | Attribute metadata format is invalid. | | The metadata isn't a table. |
|  | | GetVersionAsyncThrottle | | GetVersionAsync  request dropped. Request was throttled. | | [GetVersionAsync()](/docs/nl-nl/reference/engine/classes/DataStore#GetVersionAsync)  request has exceeded the maximum queue size and Roblox is unable to process the requests at the current throughput. |
|  | | GetVersionAtTimeAsyncThrottle | | GetVersionAtTimeAsync  request dropped. Request was throttled. | | [GetVersionAtTimeAsync()](/docs/nl-nl/reference/engine/classes/DataStore#GetVersionAtTimeAsync)  request has exceeded the maximum queue size and Roblox is unable to process the requests at the current throughput. |
|  | | ListDataStoresAsyncThrottle | | ListDataStoresAsync  request dropped. Request was throttled. | | [ListDataStoresAsync()](/docs/nl-nl/reference/engine/classes/DataStoreService#ListDataStoresAsync)  request has exceeded the maximum queue size and Roblox is unable to process the requests at the current throughput. |
|  | | ListKeysAsyncThrottle | | ListKeysAsync  request dropped. Request was throttled. | | [ListKeysAsync()](/docs/nl-nl/reference/engine/classes/DataStore#ListKeysAsync)  request has exceeded the maximum queue size and Roblox is unable to process the requests at the current throughput. |
|  | | ListVersionsAsyncThrottle | | ListVersionsAsync  request dropped. Request was throttled. | | [ListVersionsAsync()](/docs/nl-nl/reference/engine/classes/DataStore#ListVersionsAsync)  request has exceeded the maximum queue size and Roblox is unable to process the requests at the current throughput. |
|  | | RemoveVersionAsyncThrottle | | RemoveVersionAsync  request dropped. Request was throttled. | | [RemoveVersionAsync()](/docs/nl-nl/reference/engine/classes/DataStore#RemoveVersionAsync)  request has exceeded the maximum queue size and Roblox is unable to process the requests at the current throughput. | |  |
|  | | InvalidTimestamp | | Timestamp must be positive and not more than ten minutes in the future. | | The timestamp provided to [GetVersionAtTimeAsync()](/docs/nl-nl/reference/engine/classes/DataStore#GetVersionAtTimeAsync)  was not valid. | |  |
|  | | StandardReadExperienceThrottled | | StandardRead  request was throttled by experience limits. | | A request to [GetAsync()](/docs/nl-nl/reference/engine/classes/DataStore#GetAsync) , [GetVersionAsync()](/docs/nl-nl/reference/engine/classes/DataStore#GetVersionAsync) , [GetVersionAtTimeAsync()](/docs/nl-nl/reference/engine/classes/DataStore#GetVersionAtTimeAsync) , or the read of [UpdateAsync()](/docs/nl-nl/reference/engine/classes/DataStore#UpdateAsync)  on a standard data store exceeded the StandardRead  experience-level rate limit. |
|  | | StandardWriteExperienceThrottled | | StandardWrite  request was throttled by experience limits. | | A request to [SetAsync()](/docs/nl-nl/reference/engine/classes/DataStore#SetAsync) , [IncrementAsync()](/docs/nl-nl/reference/engine/classes/DataStore#IncrementAsync) , or the write of [UpdateAsync()](/docs/nl-nl/reference/engine/classes/DataStore#UpdateAsync)  on a standard data store exceeded the StandardWrite  experience-level rate limit. |
|  | | StandardListExperienceThrottled | | StandardList  request was throttled by experience limits. | | A request to [ListKeysAsync()](/docs/nl-nl/reference/engine/classes/DataStore#ListKeysAsync) , [ListVersionsAsync()](/docs/nl-nl/reference/engine/classes/DataStore#ListVersionsAsync) , or [ListDataStoresAsync()](/docs/nl-nl/reference/engine/classes/DataStoreService#ListDataStoresAsync)  on standard data stores exceeded the StandardList  experience-level rate limit. |
|  | | StandardRemoveExperienceThrottled | | StandardRemove  request was throttled by experience limits. | | A request to [RemoveAsync()](/docs/nl-nl/reference/engine/classes/DataStore#RemoveAsync)  on a standard data store exceeded the StandardRemove  experience-level rate limit. |
|  | | OrderedReadExperienceThrottled | | OrderedRead  request was throttled by experience limits. | | A request to [GetAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#GetAsync) , [BatchGetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#BatchGetAsync) , or the read of [UpdateAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#UpdateAsync)  on an ordered data store exceeded the OrderedRead  experience-level rate limit. |
|  | | OrderedWriteExperienceThrottled | | OrderedWrite  request was throttled by experience limits. | | A request to [SetAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#SetAsync) , [IncrementAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#IncrementAsync) , or the write of [UpdateAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#UpdateAsync)  on an ordered data store exceeded the OrderedWrite  experience-level rate limit. |
|  | | OrderedListExperienceThrottled | | OrderedList  request was throttled by experience limits. | | A request to [GetSortedAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#GetSortedAsync)  on an ordered data store exceeded the OrderedList  experience-level rate limit. |
|  | | OrderedRemoveExperienceThrottled | | OrderedRemove  request was throttled by experience limits. | | A request to [RemoveAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#RemoveAsync)  on an ordered data store exceeded the OrderedRemove  experience-level rate limit. |
|  | | StandardReadGameServerThrottled | | StandardRead  request was throttled by game server limits or the request queue was full. | | A request to [GetAsync()](/docs/nl-nl/reference/engine/classes/DataStore#GetAsync) , [GetVersionAsync()](/docs/nl-nl/reference/engine/classes/DataStore#GetVersionAsync) , [GetVersionAtTimeAsync()](/docs/nl-nl/reference/engine/classes/DataStore#GetVersionAtTimeAsync) , or the read of [UpdateAsync()](/docs/nl-nl/reference/engine/classes/DataStore#UpdateAsync)  on a standard data store exceeded the StandardRead  game server-level rate limit. |
|  | | StandardWriteGameServerThrottled | | StandardWrite  request was throttled by game server limits or the request queue was full. | | A request to [SetAsync()](/docs/nl-nl/reference/engine/classes/DataStore#SetAsync) , [IncrementAsync()](/docs/nl-nl/reference/engine/classes/DataStore#IncrementAsync) , or the write of [UpdateAsync()](/docs/nl-nl/reference/engine/classes/DataStore#UpdateAsync)  on a standard data store exceeded the StandardWrite  game server-level rate limit. |
|  | | StandardListGameServerThrottled | | StandardList  request was throttled by game server limits or the request queue was full. | | A request to [ListKeysAsync()](/docs/nl-nl/reference/engine/classes/DataStore#ListKeysAsync) , [ListVersionsAsync()](/docs/nl-nl/reference/engine/classes/DataStore#ListVersionsAsync) , or [ListDataStoresAsync()](/docs/nl-nl/reference/engine/classes/DataStoreService#ListDataStoresAsync)  on standard data stores exceeded the StandardList  game server-level rate limit. |
|  | | StandardRemoveGameServerThrottled | | StandardRemove  request was throttled by game server limits or the request queue was full. | | A request to [RemoveAsync()](/docs/nl-nl/reference/engine/classes/DataStore#RemoveAsync)  on a standard data store exceeded the StandardRemove  game server-level rate limit. |
|  | | OrderedReadGameServerThrottled | | OrderedRead  request was throttled by game server limits or the request queue was full. | | A request to [GetAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#GetAsync) , [BatchGetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#BatchGetAsync) , or the read of [UpdateAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#UpdateAsync)  on an ordered data store exceeded the OrderedRead  game server-level rate limit. |
|  | | OrderedWriteGameServerThrottled | | OrderedWrite  request was throttled by game server limits or the request queue was full. | | A request to [SetAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#SetAsync) , [IncrementAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#IncrementAsync) , or the write of [UpdateAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#UpdateAsync)  on an ordered data store exceeded the OrderedWrite  game server-level rate limit. |
|  | | OrderedListGameServerThrottled | | OrderedList  request was throttled by game server limits or the request queue was full. | | A request to [GetSortedAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#GetSortedAsync)  on an ordered data store exceeded the OrderedList  game server-level rate limit. |
|  | | OrderedRemoveGameServerThrottled | | OrderedRemove  request was throttled by game server limits or the request queue was full. | | A request to [RemoveAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#RemoveAsync)  on an ordered data store exceeded the OrderedRemove  game server-level rate limit. |

### [Server error codes](#server-error-codes)[](#server-error-codes)

| Error name | | Error message | | Notes |
| DatastoreDeleted | | The data store is deleted. | | An operation on the data store could not occur because the data store was previously deleted. |
| DatastoreThrottled | | The request rate exceeds the allowed maximum for the datastore . | | Too many requests were sent to a single data store.  |
| InternalServerError | | An internal server error occurred. | | Occasional error on Roblox servers. Try again, ideally with exponential backoff. |
| InvalidExclusiveStartKey | | The provided exclusive start key is not valid. | | The exclusive start key (cursor) provided to a list operation such as [ListKeysAsync()](/docs/nl-nl/reference/engine/classes/DataStore#ListKeysAsync)  is not valid. |
| InvalidJson | | The provided value exceeds the maximum allowed JSON nesting depth of 400. | | The nested JSON document is too deep, reduce the nesting in the JSON document and try again. |
| InvalidPlace | | The provided place is invalid. | | No matching Universe ID for the place. Try again later. |
| InvalidTarget | | The provided target is invalid. | | Ordered data store key name exceeds the 50 character limit. |
| InvalidUniverse | | The provided universe is invalid. | | No matching Place ID for the universe. Try again later. |
| InvalidUserIds | | The provided user IDs have an invalid format. | | Failed to parse user IDs. |
| KeyThrottled | | The request rate exceeds the allowed maximum for the key. | | The request rate exceeds the maximum allowed request rate for a single key. |
| KeyNotFound | | The requested key doesn't exist. | | The key doesn't exist. |
| N/A | | No pages to advance to. | | This error occurs when you call [Pages:AdvanceToNextPageAsync()](/docs/nl-nl/reference/engine/classes/Pages#AdvanceToNextPageAsync)  on the last page. |
| StandardReadExperienceThrottled | | The standard read request rate exceeds the allowed maximum for the experience. | | A request to [GetAsync()](/docs/nl-nl/reference/engine/classes/DataStore#GetAsync) , [GetVersionAsync()](/docs/nl-nl/reference/engine/classes/DataStore#GetVersionAsync) , [GetVersionAtTimeAsync()](/docs/nl-nl/reference/engine/classes/DataStore#GetVersionAtTimeAsync) , or the read of [UpdateAsync()](/docs/nl-nl/reference/engine/classes/DataStore#UpdateAsync)  on a standard data store exceeded the StandardRead  experience-level rate limit. |
| StandardWriteExperienceThrottled | | The standard write request rate exceeds the allowed maximum for the experience. | | A request to [SetAsync()](/docs/nl-nl/reference/engine/classes/DataStore#SetAsync) , [IncrementAsync()](/docs/nl-nl/reference/engine/classes/DataStore#IncrementAsync) , or the write of [UpdateAsync()](/docs/nl-nl/reference/engine/classes/DataStore#UpdateAsync)  on a standard data store exceeded the StandardWrite  experience-level rate limit. |
| StandardListExperienceThrottled | | The standard list request rate exceeds the allowed maximum for the experience. | | A request to [ListKeysAsync()](/docs/nl-nl/reference/engine/classes/DataStore#ListKeysAsync) , [ListVersionsAsync()](/docs/nl-nl/reference/engine/classes/DataStore#ListVersionsAsync) , or [ListDataStoresAsync()](/docs/nl-nl/reference/engine/classes/DataStoreService#ListDataStoresAsync)  on standard data stores exceeded the StandardList  experience-level rate limit. |
| StandardRemoveExperienceThrottled | | The standard remove request rate exceeds the allowed maximum for the experience. | | A request to [RemoveAsync()](/docs/nl-nl/reference/engine/classes/DataStore#RemoveAsync)  on a standard data store exceeded the StandardRemove  experience-level rate limit. |
| OrderedReadExperienceThrottled | | The ordered read request rate exceeds the allowed maximum for the experience. | | A request to [GetAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#GetAsync) , [BatchGetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#BatchGetAsync) , or the read of [UpdateAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#UpdateAsync)  on an ordered data store exceeded the OrderedRead  experience-level rate limit. |
| OrderedWriteExperienceThrottled | | The ordered write request rate exceeds the allowed maximum for the experience. | | A request to [SetAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#SetAsync) , [IncrementAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#IncrementAsync) , or the write of [UpdateAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#UpdateAsync)  on an ordered data store exceeded the OrderedWrite  experience-level rate limit. |
| OrderedListExperienceThrottled | | The ordered list request rate exceeds the allowed maximum for the experience. | | A request to [GetSortedAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#GetSortedAsync)  on an ordered data store exceeded the OrderedList  experience-level rate limit. |
| OrderedRemoveExperienceThrottled | | The ordered remove request rate exceeds the allowed maximum for the experience. | | A request to [RemoveAsync()](/docs/nl-nl/reference/engine/classes/OrderedDataStore#RemoveAsync)  on an ordered data store exceeded the OrderedRemove  experience-level rate limit. |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
