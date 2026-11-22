<!-- Source: https://create.roblox.com/docs/cloud/reference/features/observability.md -->

---
name: "Observability"
last_updated: 2026-11-20T18:47:47Z
type: feature
api_base_url: "https://apis.roblox.com"
endpoints: 7
auth: [api-key, oauth2, cookie]
description: "Monitor and manage game servers for an experience"
---

# Observability

Monitor and manage game servers for an experience.

Common use cases include:

- Server discovery: [List active game servers](#GameServers_ListGameServers) for a specific place version and [retrieve available filter options](#GameServers_GetFilterOptions)
- Log retrieval: [Inspect logs](#GameServers_ListGameServerLogs) for a specific game server and [client session logs](#GameServers_ListClientLogs) for a specific play session
- Server restarts: [Forecast the impact](#Restarts_ForecastRestart) of a restart, [launch it](#Restarts_LaunchRestart), and [monitor its status](#Restarts_ListRestartStatuses)

**Base URL:** `https://apis.roblox.com`

## Authentication

Each endpoint requires one of the following authentication methods:

- **API Key**: Pass your key in the `x-api-key` HTTP header. Create keys at [Creator Dashboard](https://create.roblox.com/dashboard/credentials).
- **OAuth 2.0**: Use Bearer token in the `Authorization` header. Authorization URL: `https://apis.roblox.com/oauth/v1/authorize`, Token URL: `https://apis.roblox.com/oauth/v1/token`
- **Cookie** *(not recommended)*: `.ROBLOSECURITY` cookie. Do not use in production.

```
# API Key example
curl -H "x-api-key: YOUR_API_KEY" https://apis.roblox.com/...

# OAuth 2.0 example
curl -H "Authorization: Bearer YOUR_ACCESS_TOKEN" https://apis.roblox.com/...
```

## Endpoints

### GET `/server-management/v1/universes/{universeId}/places/{placeId}/game-servers/{jobId}/client-sessions/{sessionId}/logs` [EXPERIMENTAL]

Lists client log entries emitted during a play session on a game server.

Requires an authenticated caller with read access to the universe. `sessionId` must be a
non-zero UUID. Results default to `message_timestamp desc` when `orderBy` is omitted.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes | The universe that owns the play session. |
| `placeId` | path | `integer` | Yes | The place that hosted the play session. |
| `jobId` | path | `string` | Yes | The game-server job id that hosted the play session. |
| `sessionId` | path | `string` | Yes | The non-zero UUID that identifies the client play session. |
| `MaxPageSize` | query | `integer` | No | The maximum number of log entries to return. Defaults to 25 and values above 100 are capped at 100. |
| `PageToken` | query | `string` | No | An opaque token from a previous response. Preserve the other query parameters when requesting the next page. |
| `OrderBy` | query | `string` | No | Sorts by `message_timestamp` or `log_severity`. Append ` desc` for descending order. Each endpoint defines its own default when this value is omitted. |
| `Filter` | query | `string` | No | Filters log entries with CEL. Use `severity` with equality or `in`, `message_timestamp` with comparisons, or `search` with equality or inequality for case-insensitive full-text matching. |

**Responses:**

- `200`: OK → `ListClientLogsResponse`
- `400`: Bad Request → `ServerManagementService.ProblemDetails`
- `401`: Unauthorized → `ServerManagementService.ProblemDetails`
- `403`: Forbidden → `ServerManagementService.ProblemDetails`
- `500`: Internal Server Error

**Response fields** (`ListClientLogsResponse`)

See [ListClientLogsResponse](#listclientlogsresponse) in Models.

**Response example:**
```json
{
  "clientLogs": [
    {
      "messageTimestampMs": "...",
      "universeId": "...",
      "placeId": "...",
      "placeVersion": "...",
      "sessionId": "...",
      "severity": "..."
    }
  ],
  "nextPageToken": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/server-management/v1/universes/{UNIVERSEID}/places/{PLACEID}/game-servers/{JOBID}/client-sessions/{SESSIONID}/logs"
```

### GET `/server-management/v1/universes/{universeId}/places/{placeId}/game-servers:filter-options` [BETA]

Gets available filter options for game servers.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes | The universe ID |
| `placeId` | path | `integer` | Yes | The place ID |
| `Filter` | query | `FilterField` | No | The specific filter to query. If null or empty, the endpoint returns all available filters. Valid values: `EngineVersion`, `PlaceVersion`, `ALL`, `ServerRegion` |

**Responses:**

- `200`: OK → `FilterOptionsResponse`
- `400`: Bad Request → `ServerManagementService.ProblemDetails`
- `401`: Unauthorized → `ServerManagementService.ProblemDetails`
- `403`: Forbidden → `ServerManagementService.ProblemDetails`

**Response fields** (`FilterOptionsResponse`)

See [FilterOptionsResponse](#filteroptionsresponse) in Models.

**Response example:**
```json
{
  "filters": {
    "EngineVersion": {
      "field": "...",
      "type": "...",
      "values": "..."
    },
    "PlaceVersion": {
      "field": "...",
      "type": "...",
      "values": "..."
    },
    "ALL": {
      "field": "...",
      "type": "...",
      "values": "..."
    },
    "ServerRegion": {
      "field": "...",
      "type": "...",
      "values": "..."
    }
  }
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/server-management/v1/universes/{UNIVERSEID}/places/{PLACEID}/game-servers:filter-options"
```

### GET `/server-management/v1/universes/{universeId}/places/{placeId}/versions/{versionNumber}/game-servers` [BETA]

Lists game servers for a specific place version.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes | The universe ID |
| `placeId` | path | `integer` | Yes | The place ID |
| `versionNumber` | path | `string` | Yes | The version number |
| `MaxPageSize` | query | `integer` | No | The maximum number of game servers to return. The service might return fewer than this value. If unspecified, at most 25 game servers are returned. The maximum value is 100 and higher values are set to 100. Zero returns no game servers and only the total count, for callers that need the count without paging through rows. |
| `PageToken` | query | `string` | No | A page token, received from a previous call, to retrieve a subsequent page. When paginating, all other parameters provided to the subsequent call must match the call that provided the page token. |
| `OrderBy` | query | `string` | No | Sorting is supported only for a single field at a time. Example: "orderBy": "uptime" Defaults to ascending, but descending ordering is also supported by including the " desc" suffix. For example: "orderBy": "uptime desc". |
| `Filter` | query | `string` | No | This field may be set in order to filter the resources returned. - CEL filtering is supported on all fields. - Supported operators &&, <, <=, >, >=, ==, and `in` |

**Responses:**

- `200`: OK → `ListGameServersResponse`
- `400`: Bad Request → `ServerManagementService.ProblemDetails`
- `401`: Unauthorized → `ServerManagementService.ProblemDetails`
- `403`: Forbidden → `ServerManagementService.ProblemDetails`

**Response fields** (`ListGameServersResponse`)

See [ListGameServersResponse](#listgameserversresponse) in Models.

**Response example:**
```json
{
  "gameServers": [
    {
      "placeId": "...",
      "placeVersion": "...",
      "jobId": "...",
      "engineVersion": "...",
      "createTime": "...",
      "uptime": "..."
    }
  ],
  "nextPageToken": "string",
  "previousPageToken": "string",
  "totalCount": 0,
  "shutdownServersFetchError": false,
  "activeServersFetchError": false
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/server-management/v1/universes/{UNIVERSEID}/places/{PLACEID}/versions/{VERSIONNUMBER}/game-servers"
```

### GET `/server-management/v1/universes/{universeId}/places/{placeId}/versions/{versionNumber}/game-servers/{jobId}/logs` [BETA]

Lists game server logs for a specific server job id

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes | The universe id |
| `placeId` | path | `integer` | Yes | The place id |
| `versionNumber` | path | `string` | Yes | The version number |
| `jobId` | path | `string` | Yes | The server job id |
| `MaxPageSize` | query | `integer` | No | The maximum number of log entries to return. Defaults to 25 and values above 100 are capped at 100. |
| `PageToken` | query | `string` | No | An opaque token from a previous response. Preserve the other query parameters when requesting the next page. |
| `OrderBy` | query | `string` | No | Sorts by `message_timestamp` or `log_severity`. Append ` desc` for descending order. Each endpoint defines its own default when this value is omitted. |
| `Filter` | query | `string` | No | Filters log entries with CEL. Use `severity` with equality or `in`, `message_timestamp` with comparisons, or `search` with equality or inequality for case-insensitive full-text matching. |

**Responses:**

- `200`: OK → `ListGameServerLogsResponse`
- `400`: Bad Request → `ServerManagementService.ProblemDetails`
- `401`: Unauthorized → `ServerManagementService.ProblemDetails`
- `403`: Forbidden → `ServerManagementService.ProblemDetails`

**Response fields** (`ListGameServerLogsResponse`)

See [ListGameServerLogsResponse](#listgameserverlogsresponse) in Models.

**Response example:**
```json
{
  "gameServerLogs": [
    {
      "messageTimestampMs": "...",
      "universeId": "...",
      "placeId": "...",
      "placeVersion": "...",
      "jobId": "...",
      "severity": "..."
    }
  ],
  "nextPageToken": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/server-management/v1/universes/{UNIVERSEID}/places/{PLACEID}/versions/{VERSIONNUMBER}/game-servers/{JOBID}/logs"
```

### GET `/server-management/v1/universes/{universeId}/restarts` [BETA]

List restart statuses for a universe.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes | The universe ID |

**Responses:**

- `200`: OK → `ListRestartStatusesResponse`
- `400`: Bad Request → `ServerManagementService.ProblemDetails`
- `401`: Unauthorized → `ServerManagementService.ProblemDetails`
- `403`: Forbidden → `ServerManagementService.ProblemDetails`

**Response fields** (`ListRestartStatusesResponse`)

See [ListRestartStatusesResponse](#listrestartstatusesresponse) in Models.

**Response example:**
```json
{
  "restartStatuses": "..."
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/server-management/v1/universes/{UNIVERSEID}/restarts"
```

### POST `/server-management/v1/universes/{universeId}/restarts` [BETA]

Launch a game server restart for a universe.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes | The universe ID |

**Request Body:** `application/json` — Type: `LaunchRestartRequest`

See [LaunchRestartRequest](#launchrestartrequest) in Models.

**Request example:**
```json
{
  "bleedOffDurationMinutes": 0,
  "places": "...",
  "attributes": "..."
}
```

**Responses:**

- `200`: OK → `LaunchRestartResponse`
- `400`: Bad Request → `ServerManagementService.ProblemDetails`
- `401`: Unauthorized → `ServerManagementService.ProblemDetails`
- `403`: Forbidden → `ServerManagementService.ProblemDetails`

**Response fields** (`LaunchRestartResponse`)

See [LaunchRestartResponse](#launchrestartresponse) in Models.

**Response example:**
```json
{
  "id": "string",
  "playersImpacted": 0,
  "instancesImpacted": 0
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/server-management/v1/universes/{UNIVERSEID}/restarts" \
  -H "Content-Type: application/json" \
  -d '{
  "bleedOffDurationMinutes": 0,
  "places": "...",
  "attributes": "..."
}'
```

### GET `/server-management/v1/universes/{universeId}/restarts:forecast` [BETA]

Forecast the impact of restarting game servers for a universe.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes | The universe ID |

**Responses:**

- `200`: OK → `ForecastRestartResponse`
- `400`: Bad Request → `ServerManagementService.ProblemDetails`
- `401`: Unauthorized → `ServerManagementService.ProblemDetails`
- `403`: Forbidden → `ServerManagementService.ProblemDetails`

**Response fields** (`ForecastRestartResponse`)

See [ForecastRestartResponse](#forecastrestartresponse) in Models.

**Response example:**
```json
{
  "placeForecasts": "..."
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/server-management/v1/universes/{UNIVERSEID}/restarts:forecast"
```

## Models

### ListClientLogsResponse

A page of client log entries from one play session.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `clientLogs` | `ClientLog[]` | No | The client log entries in this page. |
| `nextPageToken` | `string` | No | An opaque token for the next page. Omitted when there are no more entries. |

### ServerManagementService.ProblemDetails

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `type` | `string` | No |  |
| `title` | `string` | No |  |
| `status` | `integer` | No |  |
| `detail` | `string` | No |  |
| `instance` | `string` | No |  |

### FilterField

Enum describing the different available filter fields.

Values: `EngineVersion`, `PlaceVersion`, `ALL`, `ServerRegion`

### FilterOptionsResponse

Response model for filter options endpoint.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `filters` | `object` | No | A dictionary of filter field names to their metadata and available values. |

### ListGameServersResponse

Response model for listing game servers.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `gameServers` | `GameServer[]` | No | The GameServers from the specified PlaceVersion. |
| `nextPageToken` | `string` | No | A token that you can send as a `pageToken` parameter to retrieve the next page. If this field is omitted, there are no subsequent pages. |
| `previousPageToken` | `string` | No | A token that you can send as a `pageToken` parameter to retrieve the previous page (reverse cursor). If this field is omitted, there are no prior pages. |
| `totalCount` | `integer` | No | Total matching rows across all pages. Combined active+shutdown queries return the sum of each source total when both are known; omitted when a source failed or omitted its total. |
| `shutdownServersFetchError` | `boolean` | No | True when this page includes active rows but shutdown rows could not be fetched. Results may be a partial slice of the globally ordered combined stream. |
| `activeServersFetchError` | `boolean` | No | True when this page includes shutdown rows but active rows could not be fetched. Results may be a partial slice of the globally ordered combined stream. |

### ListGameServerLogsResponse

Response model for listing game servers.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `gameServerLogs` | `GameServerLog[]` | No | The GameServers from the specified PlaceVersion. |
| `nextPageToken` | `string` | No | A token that you can send as a `pageToken` parameter to retrieve the next page. If this field is omitted, there are no subsequent pages. |

### ListRestartStatusesResponse

Response model for listing restart statuses.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `restartStatuses` | `object` | No | Restart statuses keyed by restart ID. |

### LaunchRestartRequest

Request model for launching a game restart.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `bleedOffDurationMinutes` | `integer` | No | Period in minutes before servers begin to be restarted. During this time, players will not be matchmade to servers scheduled for restart. Valid range: 1-240. |
| `places` | `object` | No | Optional mapping of place ID to specific PlaceFilter objects. If empty for a place, restart all versions of that place. If null/omitted entirely, restart all places in the universe. |
| `attributes` | `any` | No | Optional JSON object sent to game servers when the restart is scheduled. Must be a JSON object and at most 500 bytes when serialized (UTF-8). |

### LaunchRestartResponse

Response model for launching a game restart.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `string` | No | ID of the restart. |
| `playersImpacted` | `integer` | No | Number of players in instances that will be shut down. |
| `instancesImpacted` | `integer` | No | Number of game instances that will be closed. |

### ForecastRestartResponse

Response model for the forecast restart endpoint.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `placeForecasts` | `object` | No | Per-place forecast data keyed by place ID. Empty if no active places. |

### PlaceSummaryForGameRestart

Per-place forecast data for a game restart.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `playersImpacted` | `integer` | No | Number of players that would be kicked during the restart. |
| `totalPlayers` | `integer` | No | Total players currently in the place, including those not impacted. |
| `instancesImpacted` | `integer` | No | Number of instances that would be closed. |
| `totalInstances` | `integer` | No | Total instances for the place. |
| `latestPlaceVersion` | `string` | No | The most recent version of the place in any active server. |
| `publishTime` | `string` | No | Timestamp for the publication of the latest place version. |
| `isNotInUniverse` | `boolean` | No | Whether the place does not belong to the universe. True when a place moved to a different universe but still has active servers from before. |
| `playersPerVersion` | `object` | No | Player count per place version. |
| `instancesPerVersion` | `object` | No | Instance count per place version. |

### PlaceFilter

Filter for which versions of a place to restart.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `versions` | `integer[]` | No | List of placeVersions to restart. Mutually exclusive with ServerManagementService.V2.Models.PlaceFilter.ExcludeCurrentVersion. |
| `excludeCurrentVersion` | `boolean` | No | If true, all versions except the most recently published will be restarted. Mutually exclusive with ServerManagementService.V2.Models.PlaceFilter.Versions. |

### RestartStatus

Status of a game restart.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `universeId` | `string` | No | Universe ID. |
| `scheduledTime` | `string` | No | When the restart was launched (scheduled time). |
| `startTime` | `string` | No | When the bleed-off period ends and restarts begin. |
| `placeRestartStatuses` | `object` | No | Per-place statuses keyed by place ID. |

### PlaceRestartStatus

Per-place restart status.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `state` | `RestartState` | No | Current state of the place restart. |
| `startTime` | `string` | No | When the place restart started. |
| `endTime` | `string` | No | When the place restart ended (null if still in progress). |
| `totalPlayers` | `integer` | No | Initial total count of players to be kicked. |
| `totalInstances` | `integer` | No | Initial total count of instances to be restarted. |
| `remainingPlayers` | `integer` | No | Remaining players to be kicked. |
| `remainingInstances` | `integer` | No | Remaining instances to be closed. |
| `filter` | `PlaceFilter` | No | The filter that was applied to select which versions to restart. |
| `latestVersion` | `string` | No | Latest version at the time of the restart. |

### RestartState

The current state of a place restart.

Values: `DELAYING`, `RESTARTING`, `SUCCEEDED`

### GameServerLog

Response model for listing a game server log

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `messageTimestampMs` | `string` | Yes | The timestamp the log was received |
| `universeId` | `integer` | Yes | The universe where the log was created |
| `placeId` | `string` | Yes | The place where the log was created |
| `placeVersion` | `string` | Yes | The place version on which the log was created |
| `jobId` | `string` | Yes | The Game Server id where the log was created |
| `severity` | `LogSeverity` | Yes | The severity of the log |
| `message` | `string` | Yes | The log message |
| `stackTrace` | `string` | Yes | The stack trace of the log |
| `messageTemplate` | `string` | No | Optional message template included with structured logging |
| `context` | `string` | No | Optional message context included with structured logging |
| `loggerFullPath` | `string` | No | The full path of the logger that emitted the log entry |
| `skippedCount` | `integer` | Yes | How many duplicate versions of this message were present in the same time window as this log |
| `rateLimitedCount` | `integer` | Yes | How many more messages were present in the time window beyond our overall rate limits |
| `structuredStackTrace` | `StructuredStackFrame[]` | No | A list of ServerManagementService.V2.Models.StructuredStackFrame metadata, identifying the script that errored when combined with the ServerManagementService.V2.Models.GameServerLog.PlaceVersion |

### LogSeverity

Defines the various log severity types with values:
Output (0), Info (1), Warning (2), Error (3)

Values: `0`, `1`, `2`, `3`

### StructuredStackFrame

Part of the ServerManagementService.V2.Models.GameServerLog and ServerManagementService.V2.Models.ClientLog response objects.
Representing the metadata for a single frame in a structured stack trace.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `line` | `integer` | Yes | The line number where the error occurred. |
| `function` | `string` | No | The name of the function in which the error occurred. |
| `scriptPath` | `string` | No | The data model path to the script where the error occurred. |
| `scriptUniqueId` | `string` | No | The unique id for the script where the error occurred. Will be null for frames where the code was from ```loadScript``` or ```require(assetId)```. If ServerManagementService.V2.Models.StructuredStackFrame.IsDynamic is true, this will be a dynamic id that does not refer to a script in the studio Data Model. |
| `isDynamic` | `boolean` | No | Identifies whether the ServerManagementService.V2.Models.StructuredStackFrame.ScriptUniqueId refers to a script that exists in the Studio Data Model. If this is true, then the script that generated the error was copied at runtime. This includes Starter scripts (e.g. StarterGui, StarterPack, StarterPlayerScripts, StarterCharacterScripts). |

### GameServer

Response model for listing a Game Server

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `placeId` | `string` | Yes | The place ID this game server belongs to. |
| `placeVersion` | `string` | Yes | The place version this game server belongs to. |
| `jobId` | `string` | Yes | The unique ID for this server. |
| `engineVersion` | `string` | Yes | The RCC Version the server is running |
| `createTime` | `string` | Yes | The time this server was created. |
| `uptime` | `string` | Yes | How long this server has been running. |
| `memoryUsageBytes` | `integer` | Yes | The Memory Usage of the server in bytes. |
| `frameRate` | `number` | Yes | The Server Frame Rate. |
| `occupancy` | `integer` | Yes | The current number of users in the server. |
| `maxOccupancy` | `integer` | Yes | The maximum number of users in the server. |
| `type` | `ServerType` | Yes | The Type of Server. |
| `full` | `boolean` | Yes | Whether the server is at max occupancy. |
| `shutDown` | `boolean` | Yes | Whether the server has been shutdown. |
| `status` | `ServerStatus` | Yes | Creator-visible server status. |
| `terminationTime` | `string` | Yes | The time the server terminated. Null while ServerManagementService.V2.Models.GameServer.ShutDown is false. |
| `playerIds` | `integer[]` | Yes | The list of PlayerIds in the server |
| `serverRegion` | `string` | No | The region of the server, as nearest Airport Code (Metro) |

### ServerType

Defines the different types of servers

Values: `0`, `1`, `2`, `3`, `4`, `5`

### ServerStatus

Server status that is visible to creators.
This is derived from the shutdown reason for shutdown rows; it is always "Active" for currently live servers.

Values: `active`, `shut_down`, `restarted`, `roblox_restarted`, `crashed`, `out_of_memory`, `moderated`, `pending`, `developer_restarted`, `unspecified`

### FilterFieldInfo

Describes the metadata and available values for a single filter field.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `field` | `FilterField` | No | The technical name of the field. |
| `type` | `FilterType` | No | The data type of the filter values. |
| `values` | `any[]` | No | The list of available values for the filter. |

### FilterType

Enum describing the data type of a filter field's values.

Values: `String`, `Number`

### ClientLog

A log entry emitted by a client during a play session.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `messageTimestampMs` | `string` | Yes | The UTC timestamp when the logging system received the entry. |
| `universeId` | `integer` | Yes | The universe that contains the play session. |
| `placeId` | `string` | Yes | The place that emitted the entry. |
| `placeVersion` | `string` | Yes | The version of the place that emitted the entry. |
| `sessionId` | `string` | Yes | The UUID that identifies the client play session. |
| `severity` | `LogSeverity` | Yes | The severity: output (0), info (1), warning (2), or error (3). |
| `message` | `string` | Yes | The log message. |
| `stackTrace` | `string` | Yes | The stack trace attached to the entry. |
| `messageTemplate` | `string` | No | The optional message template from structured logging. |
| `context` | `string` | No | The optional structured logging context. |
| `loggerFullPath` | `string` | No | The full path of the logger that emitted the log entry. |
| `skippedCount` | `integer` | Yes | The number of duplicate messages coalesced into this entry. |
| `rateLimitedCount` | `integer` | Yes | The number of messages suppressed after rate limiting. |
| `structuredStackTrace` | `StructuredStackFrame[]` | No | A list of ServerManagementService.V2.Models.StructuredStackFrame metadata, identifying the script that errored when combined with the ServerManagementService.V2.Models.ClientLog.PlaceVersion |