<!-- Source: https://create.roblox.com/docs/cloud-services/http-service -->

In-game HTTP requests | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/cloud-services/http-service.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Cloud services](/docs/cloud-services/data-stores-vs-memory-stores)

# In-game HTTP requests

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/cloud-services/http-service.md)

You can use [HttpService](/docs/reference/engine/classes/HttpService)  to send generic HTTP requests to third-party web services for use cases like analytics, data storage, or error logging. [HttpService](/docs/reference/engine/classes/HttpService)  also supports certain Open Cloud endpoints.

## [Enable HTTP requests](#enable-http-requests)[](#enable-http-requests)

The [HttpService:GetAsync()](/docs/reference/engine/classes/HttpService#GetAsync) , [HttpService:PostAsync()](/docs/reference/engine/classes/HttpService#PostAsync) , and [HttpService:RequestAsync()](/docs/reference/engine/classes/HttpService#RequestAsync)  methods aren't enabled by default. To send requests, you must Allow HTTP Requests  under File  ⟩ Experience Settings  ⟩ Security  in Studio.

## [Use in plugins](#use-in-plugins)[](#use-in-plugins)

You can use [HttpService](/docs/reference/engine/classes/HttpService)  in Studio plugins to check for updates, download content, or other business logic. The first time a plugin attempts to use the service, the user might be prompted to give the plugin permission to communicate with the particular web address. Users can accept, deny, and revoke these permissions at any time through the Plugin Management  window.

Plugins can also communicate with other software running on the same computer through the localhost  and 127.0.0.1  hosts. By running programs compatible with such plugins, you can extend the functionality of your plugin beyond the normal capabilities of Studio, such as interacting with your computer's file system. Beware that such software must be distributed separately from the plugin itself and can pose security risks.

## [Use with Open Cloud](#use-with-open-cloud)[](#use-with-open-cloud)

[HttpService](/docs/reference/engine/classes/HttpService)  can currently call a subset of the Open Cloud endpoints. You can call these endpoints the same way that you'd call any other endpoint via HttpService . The only difference is that you must include an Open Cloud API key in the request:

1.

[Create an Open Cloud API key](/docs/cloud/auth/api-keys#create-api-keys) .

2.

[Save the API key to your secrets store](/docs/cloud-services/secrets#add-secrets) .

3.

Make the request.

The following code sample demonstrates how to update a user's group membership from within a game:

```

local HttpService = game:GetService("HttpService")

local groupId = "your_group_id"

local membershipId = "your_membership_id"

local roleId = "your_role_id"

local function request()

	local response = HttpService:RequestAsync({

		Url = `https://apis.roblox.com/cloud/v2/groups/{groupId}/memberships/{membershipId}`,

		Method = "PATCH",

		Headers = {

			["Content-Type"] = "application/json", -- When sending JSON, set this!

			["x-api-key"] = HttpService:GetSecret("APIKey"), -- Set in Creator Hub

		},

		Body = HttpService:JSONEncode({ role = `groups/{groupId}/roles/{roleId}` }),

	})

	if response.Success then

		print("The response was successful:", response.StatusCode, response.StatusMessage)

	else

		print("The response returned an error:", response.StatusCode, response.StatusMessage)

	end

	print("Response body:\n", response.Body)

	print("Response headers:\n", HttpService:JSONEncode(response.Headers))

end

-- Wrap the function in pcall() for safety

local success, errorMessage = pcall(request)

if not success then

	print("The HTTP request failed to send:", errorMessage)

end

```

### [Supported Open Cloud endpoints](#supported-open-cloud-endpoints)[](#supported-open-cloud-endpoints)

The following endpoints are supported. Due to current limitations on [HttpService](/docs/reference/engine/classes/HttpService) , the ..  string is not allowed in URL path parameters to Roblox domains. This means, for example, that data stores and entries containing this string are currently inaccessible from [HttpService](/docs/reference/engine/classes/HttpService) .

#### [Assets](#assets)[](#assets)

-

[GetAsset](/docs/cloud/features/assets#/default/Assets_GetAsset)

-

[ListAssetVersions](/docs/cloud/features/assets#/default/listAssetVersions)

-

[GetAssetVersion](/docs/cloud/features/assets#/default/Assets_GetAssetVersion)

#### [Bans and blocks](#bans-and-blocks)[](#bans-and-blocks)

-

[ListUserRestrictions (Place)](/docs/cloud/features/bans-and-blocks#/UserRestriction/Cloud_ListUserRestrictions__Using_Universes)

-

[GetUserRestriction (Place)](/docs/cloud/features/bans-and-blocks#/UserRestriction/Cloud_GetUserRestriction__Using_Universes_Places)

-

[UpdateUserRestriction (Place)](/docs/cloud/features/bans-and-blocks#/UserRestriction/Cloud_UpdateUserRestriction__Using_Universes_Places)

-

[ListUserRestrictions (Universe)](/docs/cloud/features/bans-and-blocks#/UserRestriction/Cloud_ListUserRestrictions)

-

[GetUserRestriction (Universe)](/docs/docs/cloud/features/bans-and-blocks#/UserRestriction/Cloud_GetUserRestriction__Using_Universes)

-

[UpdateUserRestriction (Universe)](/docs/cloud/features/bans-and-blocks#/UserRestriction/Cloud_UpdateUserRestriction__Using_Universes)

-

[ListUserRestrictionLogs (Universe)](/docs/cloud/features/bans-and-blocks#/UserRestriction/Cloud_ListUserRestrictionLogs)

#### [Configs](#configs)[](#configs)

-

[GetConfigRepositoryValues](/docs/cloud/reference/features/configs#CreatorConfigsPublicApi_GetConfigRepositoryValues)

-

[GetConfigRepositoryDraft](/docs/cloud/reference/features/configs#CreatorConfigsPublicApi_GetConfigRepositoryDraft)

-

[UpdateDraft](/docs/cloud/reference/features/configs#CreatorConfigsPublicApi_UpdateDraft)

-

[DeleteDraft](/docs/cloud/reference/features/configs#CreatorConfigsPublicApi_DeleteDraft)

-

[OverwriteDraft](/docs/cloud/reference/features/configs#CreatorConfigsPublicApi_OverwriteDraft)

-

[GetConfigRepositoryFull](/docs/cloud/reference/features/configs#CreatorConfigsPublicApi_GetConfigRepositoryFull)

-

[PublishDraft](/docs/cloud/reference/features/configs#CreatorConfigsPublicApi_PublishDraft)

-

[ListRevisions](/docs/cloud/reference/features/configs#CreatorConfigsPublicApi_ListRevisions)

-

[RestoreRevision](/docs/cloud/reference/features/configs#CreatorConfigsPublicApi_RestoreRevision)

#### [Creator Store](#creator-store)[](#creator-store)

-

[CreateCreatorStoreProduct](/docs/cloud/features/creator-store#/CreatorStoreProduct/Cloud_CreateCreatorStoreProduct)

-

[GetCreatorStoreProduct](/docs/cloud/features/creator-store#/CreatorStoreProduct/Cloud_GetCreatorStoreProduct)

-

[UpdateCreatorStoreProduct](/docs/cloud/features/creator-store#/CreatorStoreProduct/Cloud_UpdateCreatorStoreProduct)

-

[CreatorStoreAssetsSearch](/docs/cloud/features/creator-store#toolbox-service)

#### [Developer products](#developer-products)[](#developer-products)

-

[CreateDeveloperProduct](/docs/cloud/reference/features/developer-products#DeveloperProducts_CreateDeveloperProductV2)

-

[UpdateDeveloperProduct](/docs/cloud/reference/features/developer-products#DeveloperProducts_UpdateDeveloperProductV2)

-

[GetDeveloperProductConfig](/docs/cloud/reference/features/developer-products#DeveloperProducts_GetDeveloperProductConfigV2)

-

[ListDeveloperProductConfigsByUniverse](/docs/cloud/reference/features/developer-products#DeveloperProducts_ListDeveloperProductConfigsByUniverseV2)

#### [Game passes](#game-passes)[](#game-passes)

-

[CreateGamePass](/docs/cloud/reference/features/game-passes#GamePasses_CreateGamePass)

-

[UpdateGamePass](/docs/cloud/reference/features/game-passes#GamePasses_UpdateGamePass)

-

[GetGamePassConfig](/docs/cloud/reference/features/game-passes#GamePasses_GetGamePassConfig)

-

[ListGamePassConfigsByUniverse](/docs/cloud/reference/features/game-passes#GamePasses_ListGamePassConfigsByUniverse)

#### [Data and memory stores](#data-and-memory-stores)[](#data-and-memory-stores)

Data stores:

-

[ListDataStores](/docs/cloud/reference/DataStore#Cloud_ListDataStores)

-

[SnapshotDataStores](/docs/cloud/features/storage#/DataStore/Cloud_SnapshotDataStores)

-

[ListDataStoreEntries](/docs/cloud/reference/DataStoreEntry#Cloud_ListDataStoreEntries__Using_Universes)

-

[CreateDataStoreEntry](/docs/cloud/reference/DataStoreEntry#Cloud_CreateDataStoreEntry__Using_Universes)

-

[GetDataStoreEntry](/docs/cloud/reference/DataStoreEntry#Cloud_GetDataStoreEntry__Using_Universes_DataStores)

-

[DeleteDataStoreEntry](/docs/cloud/reference/DataStoreEntry#Cloud_DeleteDataStoreEntry__Using_Universes_DataStores)

-

[UpdateDataStoreEntry](/docs/cloud/reference/DataStoreEntry#Cloud_UpdateDataStoreEntry__Using_Universes_DataStores)

-

[IncrementDataStoreEntry](/docs/cloud/reference/DataStoreEntry#Cloud_IncrementDataStoreEntry__Using_Universes_DataStores)

-

[ListDataStoreEntryRevisions](/docs/cloud/features/storage#/DataStoreEntry/Cloud_ListDataStoreEntryRevisions__Using_Universes_DataStores)

-

[ListDataStoreEntries (With Scope)](/docs/cloud/features/storage#/DataStoreEntry/Cloud_ListDataStoreEntries__Using_Universes_DataStores)

-

[CreateDataStoreEntry (With Scope)](/docs/cloud/features/storage#/DataStoreEntry/Cloud_CreateDataStoreEntry__Using_Universes_DataStores)

-

[GetDataStoreEntry (With Scope)](/docs/cloud/features/storage#/DataStoreEntry/Cloud_GetDataStoreEntry__Using_Universes_DataStores_Scopes)

-

[DeleteDataStoreEntry (With Scope)](/docs/cloud/features/storage#/DataStoreEntry/Cloud_DeleteDataStoreEntry__Using_Universes_DataStores_Scopes)

-

[UpdateDataStoreEntry (With Scope)](/docs/cloud/features/storage#/DataStoreEntry/Cloud_UpdateDataStoreEntry__Using_Universes_DataStores_Scopes)

-

[IncrementDataStoreEntry (With Scope)](/docs/cloud/features/storage#/DataStoreEntry/Cloud_IncrementDataStoreEntry__Using_Universes_DataStores_Scopes)

-

[ListDataStoreEntryRevisions (With Scope)](/docs/cloud/features/storage#/DataStoreEntry/Cloud_ListDataStoreEntryRevisions__Using_Universes_DataStores_Scopes)

Memory stores:

-

[CreateMemoryStoreQueueItem](/docs/cloud/features/storage#/MemoryStoreQueueItem/Cloud_CreateMemoryStoreQueueItem)

-

[DiscardMemoryStoreQueueItems](/docs/cloud/features/storage#/MemoryStoreQueueItem/Cloud_DiscardMemoryStoreQueueItems)

-

[ReadMemoryStoreQueueItems](/docs/cloud/features/storage#/MemoryStoreQueueItem/Cloud_ReadMemoryStoreQueueItems)

-

[ListMemoryStoreSortedMapItems](/docs/cloud/features/storage#/MemoryStoreSortedMapItem/Cloud_ListMemoryStoreSortedMapItems)

-

[CreateMemoryStoreSortedMapItem](/docs/cloud/features/storage#/MemoryStoreSortedMapItem/Cloud_CreateMemoryStoreSortedMapItem)

-

[GetMemoryStoreSortedMapItem](/docs/cloud/features/storage#/MemoryStoreSortedMapItem/Cloud_GetMemoryStoreSortedMapItem)

-

[DeleteMemoryStoreSortedMapItem](/docs/cloud/features/storage#/MemoryStoreSortedMapItem/Cloud_DeleteMemoryStoreSortedMapItem)

-

[UpdateMemoryStoreSortedMapItem](/docs/cloud/features/storage#/MemoryStoreSortedMapItem/Cloud_UpdateMemoryStoreSortedMapItem)

-

[FlushMemoryStore](/docs/cloud/features/storage#/MemoryStore/Cloud_FlushMemoryStore)

Ordered data stores:

-

[ListOrderedDataStoreEntries](/docs/cloud/features/storage#/OrderedDataStoreEntry/Cloud_ListOrderedDataStoreEntries)

-

[CreateOrderedDataStoreEntry](/docs/cloud/features/storage#/OrderedDataStoreEntry/Cloud_CreateOrderedDataStoreEntry)

-

[GetOrderedDataStoreEntry](/docs/cloud/features/storage#/OrderedDataStoreEntry/Cloud_GetOrderedDataStoreEntry)

-

[DeleteOrderedDataStoreEntry](/docs/cloud/features/storage#/OrderedDataStoreEntry/Cloud_DeleteOrderedDataStoreEntry)

-

[UpdateOrderedDataStoreEntry](/docs/cloud/features/storage#/OrderedDataStoreEntry/Cloud_UpdateOrderedDataStoreEntry)

-

[IncrementOrderedDataStoreEntry](/docs/cloud/features/storage#/OrderedDataStoreEntry/Cloud_IncrementOrderedDataStoreEntry)

#### [Groups](#groups)[](#groups)

-

[GetGroup](/docs/cloud/reference/Group#Cloud_GetGroup)

-

[ListGroupJoinRequests](/docs/cloud/reference/GroupJoinRequest#Cloud_ListGroupJoinRequests)

-

[AcceptGroupJoinRequest](/docs/cloud/reference/GroupJoinRequest#Cloud_AcceptGroupJoinRequest)

-

[DeclineGroupJoinRequest](/docs/cloud/reference/GroupJoinRequest#Cloud_DeclineGroupJoinRequest)

-

[ListGroupMemberships](/docs/cloud/reference/GroupMembership#Cloud_ListGroupMemberships)

-

[UpdateGroupMembership](/docs/cloud/reference/GroupMembership#Cloud_UpdateGroupMembership)

-

[ListGroupRoles](/docs/cloud/reference/GroupRole#Cloud_ListGroupRoles)

-

[GetGroupRole](/docs/cloud/reference/GroupRole#Cloud_GetGroupRole)

-

[GetGroupShout](/docs/cloud/reference/GroupShout#Cloud_GetGroupShout)

#### [Inventories](#inventories)[](#inventories)

-

[ListInventoryItems](/docs/cloud/reference/InventoryItem#Cloud_ListInventoryItems)

#### [Luau execution](#luau-execution)[](#luau-execution)

-

[CreateLuauExecutionSessionTaskBinaryInput](/docs/cloud/features/luau-execution#/LuauExecutionSessionTaskBinaryInput/Cloud_CreateLuauExecutionSessionTaskBinaryInput)

-

[CreateLuauExecutionSessionTask](/docs/cloud/features/luau-execution#/LuauExecutionSessionTask/Cloud_CreateLuauExecutionSessionTask__Using_Universes)

-

[CreateLuauExecutionSessionTask (with version)](/docs/cloud/features/luau-execution#/LuauExecutionSessionTask/Cloud_CreateLuauExecutionSessionTask__Using_Universes_Places)

-

[GetLuauExecutionSessionTask](/docs/cloud/features/luau-execution#/LuauExecutionSessionTask/Cloud_GetLuauExecutionSessionTask)

-

[ListLuauExecutionSessionTaskLogs](/docs/cloud/features/luau-execution#/LuauExecutionSessionTaskLog/Cloud_ListLuauExecutionSessionTaskLogs)

#### [Notifications](#notifications)[](#notifications)

-

[CreateUserNotification](/docs/cloud/features/notifications#/UserNotification/Cloud_CreateUserNotification)

#### [Places](#places)[](#places)

-

[GetPlace](/docs/cloud/features/places#/Place/Cloud_GetPlace)

-

[UpdatePlace](/docs/cloud/features/places#/Place/Cloud_UpdatePlace)

-

[GetInstance](/docs/cloud/features/places#/Instance/Cloud_GetInstance)

-

[UpdateInstance](/docs/cloud/features/places#/Instance/Cloud_UpdateInstance)

#### [Universes](#universes)[](#universes)

-

[UpdateUniverse](/docs/cloud/features/universes#/Universe/Cloud_UpdateUniverse)

-

[GetUniverse](/docs/cloud/features/universes#/Universe/Cloud_GetUniverse)

-

[PublishUniverseMessage](/docs/cloud/features/universes#/Universe/Cloud_PublishUniverseMessage)

-

[RestartUniverseServers](/docs/cloud/features/universes#/Universe/Cloud_RestartUniverseServers)

#### [Users](#users)[](#users)

-

[GetUser](/docs/cloud/features/users#/User/Cloud_GetUser)

-

[GenerateUserThumbnail](/docs/cloud/features/users#/User/Cloud_GenerateUserThumbnail)

## [Limitations](#limitations)[](#limitations)

-

Only the x-api-key  and content-type  headers are allowed.

-

The x-api-key  header must be a [Secret](/docs/reference/engine/datatypes/Secret) . See [Secrets stores](/docs/cloud-services/secrets) .

-

The ".."  string is not allowed in URL path parameters.

-

Only the HTTPS protocol is supported.

-

You cannot use port 1194  or any port below 1024 , except 80  and 443 . If you try to use a blocked port, you receive either a 403 Forbidden  or ERR_ACCESS_DENIED  error.

## [Rate limits](#rate-limits)[](#rate-limits)

For each Roblox game server, there is a limit of 2500 Open Cloud requests per minute. Exceeding this can cause request-sending methods to stall for around 30 seconds. Your [pcall()](/docs/reference/engine/globals/LuaGlobals#pcall)  may also fail with a message of Number of Open Cloud requests exceeded limit .

-

Open Cloud requests do not  consume the same overall limit of 500 HTTP requests per minute enforced on all other requests.

-

Each endpoint has its own limit per API key owner (can be a user or a group) that is enforced no matter where the calls come from ([HttpService](/docs/reference/engine/classes/HttpService) , the web, etc.).

For detailed information about Open Cloud rate limits, authentication-based rate limiting, and best practices, see [Rate Limits](/docs/cloud/reference/rate-limits) .

## [Best practices](#best-practices)[](#best-practices)

To optimize your [HttpService](/docs/reference/engine/classes/HttpService)  usage and avoid exceeding the limits, apply the following best practices:

-

Handle errors gracefully . Web requests can fail for many reasons. Use [pcall()](/docs/reference/engine/globals/LuaGlobals#pcall)  and have a plan for when requests fail. Furthermore, strictly validate and sanitize all received data from external APIs, ensuring correct data where you can.

-

Use [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff)  to stay below limits.

If a request returns a recoverable error, instead of immediately retrying, wait for two seconds, then four, eights, etc. between attempts. This helps limit congestion and improves the chance of a successful request by giving the endpoint time to "cool off."

-

Aggregate and send data in bulk.

When possible, it's recommended to let your server collect all necessary data in order to send one HTTP request, rather than multiple small requests. For example, if you are sending an HTTP request for every player in your server, check if the API has a bulk/batch endpoint and, if so, collect the information from all players and send it all in one request.

In some cases you may have to use [HttpService:RequestAsync()](/docs/reference/engine/classes/HttpService#RequestAsync)  to include data in the body of the request.

-

Use HTTP/2 endpoints . HTTP/2 provides significant performance benefits through features such as header compression and request/response multiplexing over a single connection. [HttpService](/docs/reference/engine/classes/HttpService)  automatically uses HTTP/2 when available. Note that the HTTP/2 specification requires all header names to be sent in lowercase.

## [Observability](#observability)[](#observability)

The Observability Dashboard  provides insights and analytics for monitoring and troubleshooting your [HttpService](/docs/reference/engine/classes/HttpService)  usage. The dashboard features two primary charts: Request Count  which tracks the volume of [HttpService](/docs/reference/engine/classes/HttpService)  requests from your game, and Response Time  which measures the latency for endpoints to respond.

The available dimensions for filtering and breakdown are defined as follows:

### Request Type

-

GET

-

POST

-

PUT

-

PATCH

-

DELETE

-

Other  (for non-specified request types)

### Status

-

Success (HTTP 1xx and 2xx status codes)

-

Redirect (HTTP 3xx status codes)

-

400 (Bad Request)

-

401 (Unauthorized)

-

403 (Forbidden)

-

404 (Not Found)

-

429 (Too Many Requests)

-

500 (Internal Server Error)

-

503 (Service Unavailable)

-

ExternalError (any other non-specified error codes returned from the external service)

-

InternalError (an issue returned from [HttpService](/docs/reference/engine/classes/HttpService)  within Roblox)

The Response Time  chart is not correlated with status data. If you select "Status" as a breakdown or filter, this chart will not display data.

## [Additional considerations](#additional-considerations)[](#additional-considerations)

-

Requests should provide a secure form of authentication, such as a pre-shared secret key, so that bad actors cannot pose as one of your Roblox servers.

-

Be aware of the general capacity and rate-limiting policies of the web servers to which requests are being sent.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
