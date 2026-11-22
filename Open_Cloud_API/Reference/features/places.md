<!-- Source: https://create.roblox.com/docs/cloud/reference/features/places.md -->

---
name: "Places"
last_updated: 2026-11-20T18:47:47Z
type: feature
api_base_url: "https://apis.roblox.com"
endpoints: 23
auth: [api-key, oauth2, cookie]
description: "Manage places, update instance properties, and publish place versions programmatically"
---

# Places

Manage places, update instance properties, and publish place versions programmatically. See the [Engine Instances Guide](/cloud/guides/instance) and [Place Publishing Guide](/cloud/guides/usage-place-publishing).

Common use cases include:

- Automated publishing: Publish place updates from CI/CD pipelines with version control and rollback support
- Instance management: [Read](#Cloud_GetInstance) and [update](#Cloud_UpdateInstance) Script, LocalScript, and ModuleScript objects in collaborative sessions
- Luau execution: [Run Luau scripts](#Cloud_CreateLuauExecutionSessionTask__Using_Universes) on specific place versions for testing or automation

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

### GET `/cloud/v2/universes/{universeId}/places/{placeId}` [STABLE]

Get Place

Gets the specified place.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `string` | Yes | The universe ID. |
| `placeId` | path | `string` | Yes | The place ID. |

**Responses:**

- `200`: OK → `Place`

**Response fields** (`Place`)

See [Place](#place) in Models.

**Response example:**
```json
{
  "path": "string",
  "createTime": "2024-01-01T00:00:00Z",
  "updateTime": "2024-01-01T00:00:00Z",
  "displayName": "string",
  "description": "string",
  "serverSize": 0
}
```

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/universes/{UNIVERSEID}/places/{PLACEID}"
```

### PATCH `/cloud/v2/universes/{universeId}/places/{placeId}` [STABLE]

Update Place

Updates the specified place. To avoid overwriting changes, this endpoint
responds with an HTTP 409 Conflict error if the place is open in an
active Team Create session.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.place:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `string` | Yes | The universe ID. |
| `placeId` | path | `string` | Yes | The place ID. |
| `updateMask` | query | `string` | No | The list of fields to update. |

**Request Body:** `application/json-patch+json` — Type: `Place`

See [Place](#place) in Models.

**Request example:**
```json
{
  "path": "string",
  "createTime": "2024-01-01T00:00:00Z",
  "updateTime": "2024-01-01T00:00:00Z",
  "displayName": "string",
  "description": "string",
  "serverSize": 0
}
```

**Responses:**

- `200`: OK → `Place`

**Response fields** (`Place`)

See [Place](#place) in Models.

**Response example:**
```json
{
  "path": "string",
  "createTime": "2024-01-01T00:00:00Z",
  "updateTime": "2024-01-01T00:00:00Z",
  "displayName": "string",
  "description": "string",
  "serverSize": 0
}
```

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X PATCH -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/universes/{UNIVERSEID}/places/{PLACEID}" \
  -H "Content-Type: application/json" \
  -d '{
  "path": "string",
  "createTime": "2024-01-01T00:00:00Z",
  "updateTime": "2024-01-01T00:00:00Z",
  "displayName": "string",
  "description": "string",
  "serverSize": 0
}'
```

### GET `/cloud/v2/universes/{universe_id}/places/{place_id}/instances/{instance_id}` [BETA]

Get Instance

Gets an instance and its property data.

The maximum supported response data size is 500,000 bytes. If this limit is
exceeded, the returned `Operation` will be completed with an error result
that has an error code of `422`.

**Auth:** API Key (`x-api-key` header)

**Scopes:** `universe.place.instance:read`, `universe.place.instance:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universe_id` | path | `string` | Yes | The universe ID. |
| `place_id` | path | `string` | Yes | The place ID. |
| `instance_id` | path | `string` | Yes | The instance ID. |

**Responses:**

- `200`: OK → `Operation`

**Response fields** (`Operation`)

See [Operation](#operation) in Models.

**Response example:**
```json
{
  "path": "string",
  "metadata": {
    "@type": "string"
  },
  "done": false,
  "error": {
    "code": 0,
    "message": "string",
    "details": [
      "..."
    ]
  },
  "response": {
    "@type": "string"
  }
}
```

**Rate Limits:** perApiKeyOwner: 45/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/universes/{UNIVERSE_ID}/places/{PLACE_ID}/instances/{INSTANCE_ID}"
```

### PATCH `/cloud/v2/universes/{universe_id}/places/{place_id}/instances/{instance_id}` [BETA]

Update Instance

Updates an instance's property data.

When updating a `Script` instance's source property, the maximum supported
property size is 200,000 bytes after UTF-8 encoding.

**Auth:** API Key (`x-api-key` header)

**Scopes:** `universe.place.instance:write`, `universe.place.instance:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universe_id` | path | `string` | Yes | The universe ID. |
| `place_id` | path | `string` | Yes | The place ID. |
| `instance_id` | path | `string` | Yes | The instance ID. |
| `updateMask` | query | `string` | No | The list of fields to update. |

**Request Body:** `application/json` — Type: `Instance`

See [Instance](#instance) in Models.

**Request example:**
```json
{
  "path": "string",
  "hasChildren": false,
  "engineInstance": {
    "Id": "string",
    "Parent": "string",
    "Name": "string",
    "Details": {
      "Folder": "...",
      "LocalScript": "...",
      "ModuleScript": "...",
      "Script": "..."
    }
  }
}
```

**Responses:**

- `200`: OK → `Operation`

**Response fields** (`Operation`)

See [Operation](#operation) in Models.

**Response example:**
```json
{
  "path": "string",
  "metadata": {
    "@type": "string"
  },
  "done": false,
  "error": {
    "code": 0,
    "message": "string",
    "details": [
      "..."
    ]
  },
  "response": {
    "@type": "string"
  }
}
```

**Rate Limits:** perApiKeyOwner: 45/minute

**Example:**
```bash
curl -X PATCH -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/universes/{UNIVERSE_ID}/places/{PLACE_ID}/instances/{INSTANCE_ID}" \
  -H "Content-Type: application/json" \
  -d '{
  "path": "string",
  "hasChildren": false,
  "engineInstance": {
    "Id": "string",
    "Parent": "string",
    "Name": "string",
    "Details": {
      "Folder": "...",
      "LocalScript": "...",
      "ModuleScript": "...",
      "Script": "..."
    }
  }
}'
```

### GET `/cloud/v2/universes/{universe_id}/places/{place_id}/instances/{instance_id}/operations/{operation_id}` [BETA]

Get Update Instance Operation

Retrieves the status of the operation to [update an instance](https://create.roblox.com/docs/cloud/reference/features/universes#Cloud_UpdateInstance).

**Auth:** API Key (`x-api-key` header)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universe_id` | path | `string` | Yes | The universe ID. |
| `place_id` | path | `string` | Yes | The place ID. |
| `instance_id` | path | `string` | Yes | The instance ID. |
| `operation_id` | path | `string` | Yes | The operation ID. |

**Responses:**

- `200`: OK → `OCV2.Operations.Operation`

**Response fields** (`OCV2.Operations.Operation`)

See [OCV2.Operations.Operation](#ocv2-operations-operation) in Models.

**Response example:**
```json
{
  "path": "string",
  "metadata": {
    "@type": "string"
  },
  "done": false,
  "error": {
    "code": 0,
    "message": "string",
    "details": [
      "..."
    ]
  },
  "response": {
    "@type": "string"
  }
}
```

**Rate Limits:** perApiKeyOwner: 45/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/universes/{UNIVERSE_ID}/places/{PLACE_ID}/instances/{INSTANCE_ID}/operations/{OPERATION_ID}"
```

### GET `/cloud/v2/universes/{universe_id}/places/{place_id}/instances/{instance_id}:listChildren` [BETA]

List Instance Children

Lists an instance's children.

The maximum supported response data size is 500,000 bytes. If this limit is
exceeded, the returned `Operation` will be completed with an error result
that has an error code of `422`.

**Auth:** API Key (`x-api-key` header)

**Scopes:** `universe.place.instance:read`, `universe.place.instance:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universe_id` | path | `string` | Yes | The universe ID. |
| `place_id` | path | `string` | Yes | The place ID. |
| `instance_id` | path | `string` | Yes | The instance ID. |
| `maxPageSize` | query | `integer` | No | The maximum number of child instance to return. The service may return fewer than this value. If unspecified, at most 200 children will be returned. The maximum value is 200; values above 200 will be coerced to 200. |
| `pageToken` | query | `string` | No | A page token, received from a previous `ListInstanceChildrenRequest` call. Provide this to retrieve the subsequent page.  When paginating, all other parameters provided to `ListInstanceChildrenRequest` must match the call that provided the page token. |

**Responses:**

- `200`: OK → `Operation`

**Response fields** (`Operation`)

See [Operation](#operation) in Models.

**Response example:**
```json
{
  "path": "string",
  "metadata": {
    "@type": "string"
  },
  "done": false,
  "error": {
    "code": 0,
    "message": "string",
    "details": [
      "..."
    ]
  },
  "response": {
    "@type": "string"
  }
}
```

**Rate Limits:** perApiKeyOwner: 45/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/universes/{UNIVERSE_ID}/places/{PLACE_ID}/instances/{INSTANCE_ID}:listChildren"
```

### GET `/legacy-develop/v1/places/{placeId}/teamcreate/active_session/members` [EXPERIMENTAL]

List of users in the active Team Create session

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `legacy-team-collaboration:manage`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `placeId` | path | `integer` | Yes | The place Id. |
| `limit` | query | `10 \| 25 \| 50 \| 100` | No | The number of results per request. Valid values: `10`, `25`, `50`, `100` |
| `cursor` | query | `string` | No | The paging cursor for the previous or next page. |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Web.Responses.Users.SkinnyUserResponse_`
- `400`: 1: The universe is invalid. 5: The place is invalid.
- `401`: 0: Authorization has been denied for this request.
- `403`: 2: Not authorized to perform this action. 4: TeamCreate on universe is disabled.
- `404`: 0: An unknown error occurred.
- `500`: 6: Multiple active sessions in a Team Create place.

**Response fields** (`Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Web.Responses.Users.SkinnyUserResponse_`)

See [Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Web.Responses.Users.SkinnyUserResponse_](#roblox-web-webapi-models-apiarrayresponse-roblox-web-responses-users-skinnyuserresponse-) in Models.

**Response example:**
```json
{
  "data": [
    {
      "id": "...",
      "name": "...",
      "displayName": "..."
    }
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/legacy-develop/v1/places/{PLACEID}/teamcreate/active_session/members"
```

### DELETE `/legacy-develop/v2/teamtest/{placeId}` [EXPERIMENTAL]

Close a game instance that is being used for team testing

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `legacy-team-collaboration:manage`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `placeId` | path | `integer` | Yes | The Id of the place we are setting the metadata for. |
| `gameId` | query | `string` | Yes | the Guid of the game instance System.Guid |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.ApiEmptyResponseModel`
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed

**Response fields** (`Roblox.Web.WebAPI.ApiEmptyResponseModel`)

See [Roblox.Web.WebAPI.ApiEmptyResponseModel](#roblox-web-webapi-apiemptyresponsemodel) in Models.

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X DELETE -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/legacy-develop/v2/teamtest/{PLACEID}?gameId={VALUE}"
```

### GET `/place-version-history-api/v1/{placeId}/contributors` [EXPERIMENTAL]

Endpoint used to fetch all previous contributors of a place.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `universe.place:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `placeId` | path | `integer` | Yes |  |
| `cursor` | query | `string` | No |  |
| `pageSize` | query | `integer` | No |  |

**Responses:**

- `200`: Success → `GetPlaceContributorsResponse`
- `400`: Bad Request → `OperationErrorResponse`
- `401`: Unauthorized → `OperationErrorResponse`
- `403`: Forbidden → `OperationErrorResponse`
- `500`: Server Error → `OperationErrorResponse`

**Response fields** (`GetPlaceContributorsResponse`)

See [GetPlaceContributorsResponse](#getplacecontributorsresponse) in Models.

**Response example:**
```json
{
  "nextCursor": "string",
  "hasMore": false,
  "contributors": [
    0
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 120/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/place-version-history-api/v1/{PLACEID}/contributors"
```

### GET `/place-version-history-api/v1/{placeId}/history` [EXPERIMENTAL]

Endpoint used to get place versions, using various filters

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `universe.place:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `placeId` | path | `integer` | Yes |  |
| `cursor` | query | `string` | No |  |
| `isPublished` | query | `boolean` | No |  |
| `hasNotes` | query | `boolean` | No |  |
| `saveType` | query | `integer` | No |  |
| `searchTerm` | query | `string` | No |  |
| `contributor` | query | `integer` | No |  |
| `startTime` | query | `string` | No |  |
| `endTime` | query | `string` | No |  |
| `pageSize` | query | `integer` | No |  |

**Responses:**

- `200`: Success → `GetPlaceVersionHistoryResponse`
- `400`: Bad Request → `OperationErrorResponse`
- `401`: Unauthorized → `OperationErrorResponse`
- `403`: Forbidden → `OperationErrorResponse`
- `500`: Server Error → `OperationErrorResponse`

**Response fields** (`GetPlaceVersionHistoryResponse`)

See [GetPlaceVersionHistoryResponse](#getplaceversionhistoryresponse) in Models.

**Response example:**
```json
{
  "nextCursor": "string",
  "hasMore": false,
  "placeVersions": [
    {
      "version": "...",
      "title": "...",
      "description": "...",
      "contributors": "...",
      "saveType": "...",
      "isPublished": "..."
    }
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 120/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/place-version-history-api/v1/{PLACEID}/history"
```

### POST `/place-version-history-api/v1/{placeId}/version/{version}/notes` [EXPERIMENTAL]

Endpoint used to modify the notes of a particular version for a place.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `universe.place:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `placeId` | path | `integer` | Yes |  |
| `version` | path | `string` | Yes |  |

**Request Body:** `application/json-patch+json` — Type: `UpdatePlaceVersionNotesRequest`

See [UpdatePlaceVersionNotesRequest](#updateplaceversionnotesrequest) in Models.

**Request example:**
```json
{
  "title": "string",
  "description": "string"
}
```

**Responses:**

- `200`: Success → `UpdatePlaceVersionNotesResponse`
- `400`: Bad Request → `OperationErrorResponse`
- `401`: Unauthorized → `OperationErrorResponse`
- `403`: Forbidden → `OperationErrorResponse`
- `500`: Server Error → `OperationErrorResponse`

**Response fields** (`UpdatePlaceVersionNotesResponse`)

See [UpdatePlaceVersionNotesResponse](#updateplaceversionnotesresponse) in Models.

**Response example:**
```json
{
  "placeVersion": {
    "version": "string",
    "title": "string",
    "description": "string",
    "contributors": [
      "..."
    ],
    "saveType": 0,
    "isPublished": false
  }
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/place-version-history-api/v1/{PLACEID}/version/{VERSION}/notes" \
  -H "Content-Type: application/json" \
  -d '{
  "title": "string",
  "description": "string"
}'
```

### POST `/universes/v1/{universeId}/places/{placeId}/versions` [EXPERIMENTAL]

Invokes Roblox.UniversesApi.CreatePlaceVersionApiKeyOperation operation.

**Auth:** API Key (`x-api-key` header)

**Scopes:** `universe-places:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |
| `placeId` | path | `integer` | Yes |  |
| `versionType` | query | `string` | No |  |
| `isOldVersionAllowed` | query | `boolean` | No |  |
| `shouldForceRestart` | query | `boolean` | No |  |

**Responses:**

- `200`: OK → `CreatePlaceVersionOperationResponse`

**Response fields** (`CreatePlaceVersionOperationResponse`)

See [CreatePlaceVersionOperationResponse](#createplaceversionoperationresponse) in Models.

**Response example:**
```json
{
  "versionNumber": 0
}
```

**Rate Limits:** perApiKeyOwner: 30/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/universes/v1/{UNIVERSEID}/places/{PLACEID}/versions"
```

### GET `/v1/games/multiget-place-details` [EXPERIMENTAL]

Get place details

**Server:** `https://games.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `placeIds` | query | `integer[]` | Yes | List of placeId to uniquely Identify a place |

**Responses:**

- `200`: OK → `Roblox.Games.Api.Models.Response.PlaceDetails[]`
- `401`: 0: Authorization has been denied for this request.

**Response fields** (`Roblox.Games.Api.Models.Response.PlaceDetails[]`)

See [Roblox.Games.Api.Models.Response.PlaceDetails](#roblox-games-api-models-response-placedetails) in Models.

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://games.roblox.com/v1/games/multiget-place-details?placeIds={VALUE}"
```

### GET `/v1/games/{placeId}/servers/{serverType}`

**Server:** `https://games.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `placeId` | path | `integer` | Yes |  |
| `serverType` | path | `PublicServerBrowserService.ServerType` | Yes | Valid values: `0`, `1` |
| `sortOrder` | query | `PublicServerBrowserService.SortOrder` | No | Valid values: `1`, `2` |
| `limit` | query | `integer` | No |  |
| `cursor` | query | `string` | No |  |
| `excludeFullGames` | query | `boolean` | No |  |

**Responses:**

- `200`: OK → `GameServerResponsePageResponse`
- `400`: Bad Request
- `404`: Not Found

**Response fields** (`GameServerResponsePageResponse`)

See [GameServerResponsePageResponse](#gameserverresponsepageresponse) in Models.

**Response example:**
```json
{
  "previousPageCursor": "string",
  "nextPageCursor": "string",
  "data": [
    {
      "id": "...",
      "maxPlayers": "...",
      "playing": "...",
      "playerTokens": "...",
      "players": "...",
      "fps": "..."
    }
  ]
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://games.roblox.com/v1/games/{PLACEID}/servers/{SERVERTYPE}"
```

### POST `/v1/places/{placeId}` [EXPERIMENTAL]

Updates the place configuration for the place with the id placeId

Currently the only supported functionality for updating the configuration is around Name, and Description.

**Server:** `https://develop.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `placeId` | path | `integer` | Yes | The place id for the place to be updated. |

**Responses:**

- `200`: OK → `Roblox.Api.Develop.Models.PlaceModel`
- `400`: placeId is invalid.
- `401`: 0: Authorization has been denied for this request.
- `403`: Authenticated user is not authorized to manage this place. 0: Token Validation Failed

**Response fields** (`Roblox.Api.Develop.Models.PlaceModel`)

See [Roblox.Api.Develop.Models.PlaceModel](#roblox-api-develop-models-placemodel) in Models.

**Response example:**
```json
{
  "id": 0,
  "universeId": 0,
  "name": "string",
  "description": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://develop.roblox.com/v1/places/{PLACEID}" \
  -H "Content-Type: application/json" \
  -d '{"key": "value"}'
```

### PATCH `/v1/places/{placeId}` [EXPERIMENTAL]

Updates the place configuration for the place with the id placeId

Currently the only supported functionality for updating the configuration is around Name, and Description.

**Server:** `https://develop.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `placeId` | path | `integer` | Yes | The place id for the place to be updated. |

**Responses:**

- `200`: OK → `Roblox.Api.Develop.Models.PlaceModel`
- `400`: placeId is invalid.
- `401`: 0: Authorization has been denied for this request.
- `403`: Authenticated user is not authorized to manage this place. 0: Token Validation Failed

**Response fields** (`Roblox.Api.Develop.Models.PlaceModel`)

See [Roblox.Api.Develop.Models.PlaceModel](#roblox-api-develop-models-placemodel) in Models.

**Response example:**
```json
{
  "id": 0,
  "universeId": 0,
  "name": "string",
  "description": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X PATCH -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://develop.roblox.com/v1/places/{PLACEID}" \
  -H "Content-Type: application/json" \
  -d '{"key": "value"}'
```

### GET `/v1/places/{placeId}/teamcreate/active_session/members` [EXPERIMENTAL]

List of users in the active Team Create session

**Server:** `https://develop.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `placeId` | path | `integer` | Yes | The place Id. |
| `limit` | query | `10 \| 25 \| 50 \| 100` | No | The number of results per request. Valid values: `10`, `25`, `50`, `100` |
| `cursor` | query | `string` | No | The paging cursor for the previous or next page. |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Web.Responses.Users.SkinnyUserResponse_`
- `400`: 1: The universe is invalid. 5: The place is invalid.
- `401`: 0: Authorization has been denied for this request.
- `403`: 2: Not authorized to perform this action. 4: TeamCreate on universe is disabled.
- `404`: 0: An unknown error occurred.
- `500`: 6: Multiple active sessions in a Team Create place.

**Response fields** (`Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Web.Responses.Users.SkinnyUserResponse_`)

See [Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Web.Responses.Users.SkinnyUserResponse_](#roblox-web-webapi-models-apiarrayresponse-roblox-web-responses-users-skinnyuserresponse-) in Models.

**Response example:**
```json
{
  "data": [
    {
      "id": "...",
      "name": "...",
      "displayName": "..."
    }
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://develop.roblox.com/v1/places/{PLACEID}/teamcreate/active_session/members"
```

### GET `/v1/public-server-browser-service/games/{placeId}/servers/{serverType}`

**Server:** `https://games.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `placeId` | path | `integer` | Yes |  |
| `serverType` | path | `PublicServerBrowserService.ServerType` | Yes | Valid values: `0`, `1` |
| `sortOrder` | query | `PublicServerBrowserService.SortOrder` | No | Valid values: `1`, `2` |
| `limit` | query | `integer` | No |  |
| `cursor` | query | `string` | No |  |
| `excludeFullGames` | query | `boolean` | No |  |

**Responses:**

- `200`: OK → `GameServerResponsePageResponse`
- `400`: Bad Request
- `404`: Not Found

**Response fields** (`GameServerResponsePageResponse`)

See [GameServerResponsePageResponse](#gameserverresponsepageresponse) in Models.

**Response example:**
```json
{
  "previousPageCursor": "string",
  "nextPageCursor": "string",
  "data": [
    {
      "id": "...",
      "maxPlayers": "...",
      "playing": "...",
      "playerTokens": "...",
      "players": "...",
      "fps": "..."
    }
  ]
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://games.roblox.com/v1/public-server-browser-service/games/{PLACEID}/servers/{SERVERTYPE}"
```

### GET `/v1/universes/{universeId}/places` [EXPERIMENTAL]

Gets a list of places for a universe.

**Server:** `https://develop.roblox.com`

**Auth:** 

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes | The asset id. |
| `isUniverseCreation` | query | `boolean` | No |  |
| `limit` | query | `10 \| 25 \| 50 \| 100` | No | The number of results per request. Valid values: `10`, `25`, `50`, `100` |
| `cursor` | query | `string` | No | The paging cursor for the previous or next page. |
| `sortOrder` | query | `Asc \| Desc` | No | Sorted by placeId Valid values: `Asc`, `Desc` |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Api.Develop.Models.IPlaceModel_`

**Response fields** (`Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Api.Develop.Models.IPlaceModel_`)

See [Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Api.Develop.Models.IPlaceModel_](#roblox-web-webapi-models-apipageresponse-roblox-api-develop-models-iplacemodel-) in Models.

**Response example:**
```json
{
  "previousPageCursor": "string",
  "nextPageCursor": "string",
  "data": [
    "..."
  ]
}
```

**Example:**
```bash
curl -H "Authorization: Bearer $ROBLOX_ACCESS_TOKEN" \
  "https://develop.roblox.com/v1/universes/{UNIVERSEID}/places"
```

### GET `/v2/games/{placeId}/servers/{serverType}`

**Server:** `https://games.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `placeId` | path | `integer` | Yes |  |
| `serverType` | path | `PublicServerBrowserService.ServerType` | Yes | Valid values: `0`, `1` |
| `orderBy` | query | `ServerListSortOption` | No | Valid values: `0`, `1`, `2`, `3`, `4` |
| `limit` | query | `integer` | No |  |
| `cursor` | query | `string` | No |  |
| `excludeFullGames` | query | `boolean` | No |  |

**Responses:**

- `200`: OK → `GameServerResponsePageResponse`
- `400`: Bad Request
- `404`: Not Found

**Response fields** (`GameServerResponsePageResponse`)

See [GameServerResponsePageResponse](#gameserverresponsepageresponse) in Models.

**Response example:**
```json
{
  "previousPageCursor": "string",
  "nextPageCursor": "string",
  "data": [
    {
      "id": "...",
      "maxPlayers": "...",
      "playing": "...",
      "playerTokens": "...",
      "players": "...",
      "fps": "..."
    }
  ]
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://games.roblox.com/v2/games/{PLACEID}/servers/{SERVERTYPE}"
```

### GET `/v2/places/{placeId}` [EXPERIMENTAL]

Gets the place configuration for the place with the id placeId

**Server:** `https://develop.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `placeId` | path | `integer` | Yes | The place id for the place to be updated. |

**Responses:**

- `200`: OK → `Roblox.Api.Develop.Models.PlaceModelV2`
- `401`: 0: Authorization has been denied for this request.
- `403`: Authenticated user is not authorized to manage this place.
- `404`: placeId Place not found.

**Response fields** (`Roblox.Api.Develop.Models.PlaceModelV2`)

See [Roblox.Api.Develop.Models.PlaceModelV2](#roblox-api-develop-models-placemodelv2) in Models.

**Response example:**
```json
{
  "maxPlayerCount": 0,
  "socialSlotType": "string",
  "customSocialSlotsCount": 0,
  "allowCopying": false,
  "currentSavedVersion": 0,
  "isAllGenresAllowed": false
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://develop.roblox.com/v2/places/{PLACEID}"
```

### PATCH `/v2/places/{placeId}` [EXPERIMENTAL]

Updates the place configuration for the place with the id placeId

**Server:** `https://develop.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `placeId` | path | `integer` | Yes | The place id for the place to be updated. |

**Request Body:** `application/json` — Type: `Roblox.Api.Develop.Models.PlaceConfigurationModelV2`

See [Roblox.Api.Develop.Models.PlaceConfigurationModelV2](#roblox-api-develop-models-placeconfigurationmodelv2) in Models.

**Request example:**
```json
{
  "name": "string",
  "description": "string",
  "maxPlayerCount": 0,
  "socialSlotType": "string",
  "customSocialSlotsCount": 0,
  "allowCopying": false
}
```

**Responses:**

- `200`: OK → `Roblox.Api.Develop.Models.PlaceModelV2`
- `401`: 0: Authorization has been denied for this request.
- `403`: Authenticated user is not authorized to manage this place. 0: Token Validation Failed
- `404`: placeId Place not found.

**Response fields** (`Roblox.Api.Develop.Models.PlaceModelV2`)

See [Roblox.Api.Develop.Models.PlaceModelV2](#roblox-api-develop-models-placemodelv2) in Models.

**Response example:**
```json
{
  "maxPlayerCount": 0,
  "socialSlotType": "string",
  "customSocialSlotsCount": 0,
  "allowCopying": false,
  "currentSavedVersion": 0,
  "isAllGenresAllowed": false
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X PATCH -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://develop.roblox.com/v2/places/{PLACEID}" \
  -H "Content-Type: application/json" \
  -d '{
  "name": "string",
  "description": "string",
  "maxPlayerCount": 0,
  "socialSlotType": "string",
  "customSocialSlotsCount": 0,
  "allowCopying": false
}'
```

### DELETE `/v2/teamtest/{placeId}` [EXPERIMENTAL]

Close a game instance that is being used for team testing

**Server:** `https://develop.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `placeId` | path | `integer` | Yes | The Id of the place we are setting the metadata for. |
| `gameId` | query | `string` | Yes | the Guid of the game instance System.Guid |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.ApiEmptyResponseModel`
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed

**Response fields** (`Roblox.Web.WebAPI.ApiEmptyResponseModel`)

See [Roblox.Web.WebAPI.ApiEmptyResponseModel](#roblox-web-webapi-apiemptyresponsemodel) in Models.

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X DELETE -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://develop.roblox.com/v2/teamtest/{PLACEID}?gameId={VALUE}"
```

## Models

### Place

Represents a Roblox place.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `path` | `string` | No | The resource path of the place.              Format: `universes/{universe_id}/places/{place_id}` |
| `createTime` | `string` | No | The timestamp at which the place was created. |
| `updateTime` | `string` | No | The timestamp at which the place was updated. |
| `displayName` | `string` | No | The name of the place. |
| `description` | `string` | No | The description of the place. |
| `serverSize` | `integer` | No | The maximum number of allowed users in a single server. |
| `root` | `boolean` | No | Whether this place is its parent universe's root place or not. Each universe has exactly one root place. |
| `universeRuntimeCreation` | `boolean` | No | Whether this place was created through in-experience creation. If true, the place was created by calling AssetService::CreatePlaceAsync() from a script. |
| `templatePlace` | `string` | Yes |  *(immutable)* The resource path of the template place used to initialize the place on creation. The newly created place will be a clone of this template. A list of the valid template places can be obtained from ListTemplatePlaces. Format: universes/{universe_id}/places/{place_id} |

### Operation

This resource represents a long-running operation that is the result of a
network API call.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `path` | `string` | No | The server-assigned path, which is only unique within the same service that originally returns it. If you use the default HTTP mapping, the `path` should be a resource path ending with `operations/{unique_id}`. |
| `metadata` | `GoogleProtobufAny` | No | Service-specific metadata associated with the operation.  It typically contains progress information and common metadata such as create time. Some services might not provide such metadata.  Any method that returns a long-running operation should document the metadata type, if any. |
| `done` | `boolean` | No | If the value is `false`, it means the operation is still in progress. If `true`, the operation is completed, and either `error` or `response` is available. |
| `error` | `Status` | No | The error result of the operation in case of failure or cancellation. |
| `response` | `GoogleProtobufAny` | No | The normal response of the operation in case of success.  If the original method returns no data on success, such as `Delete`, the response is `google.protobuf.Empty`.  If the original method is standard `Get`/`Create`/`Update`, the response should be the resource.  For other methods, the response should have the type `XxxResponse`, where `Xxx` is the original method name.  For example, if the original method name is `TakeSnapshot()`, the inferred response type is `TakeSnapshotResponse`. |

### Instance

Represents a data model instance.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `path` | `string` | No | The resource path of the instance.  Format: `universes/{universe_id}/places/{place_id}/instances/{instance_id}` |
| `hasChildren` | `boolean` | No | whether the instance has any children instance |
| `engineInstance` | `roblox.engine.Instance` | No | the property details of the instance |

### OCV2.Operations.Operation

This resource represents a long-running operation that is the result of a
network API call.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `path` | `string` | No | The server-assigned path, which is only unique within the same service that originally returns it. If you use the default HTTP mapping, the `path` should be a resource path ending with `operations/{unique_id}`. |
| `metadata` | `GoogleProtobufAny` | No | Service-specific metadata associated with the operation.  It typically contains progress information and common metadata such as create time. Some services might not provide such metadata.  Any method that returns a long-running operation should document the metadata type, if any. |
| `done` | `boolean` | No | If the value is `false`, it means the operation is still in progress. If `true`, the operation is completed, and either `error` or `response` is available. |
| `error` | `Status` | No | The error result of the operation in case of failure or cancellation. |
| `response` | `GoogleProtobufAny` | No | The normal response of the operation in case of success.  If the original method returns no data on success, such as `Delete`, the response is `google.protobuf.Empty`.  If the original method is standard `Get`/`Create`/`Update`, the response should be the resource.  For other methods, the response should have the type `XxxResponse`, where `Xxx` is the original method name.  For example, if the original method name is `TakeSnapshot()`, the inferred response type is `TakeSnapshotResponse`. |

### Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Web.Responses.Users.SkinnyUserResponse_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `data` | `Roblox.Web.Responses.Users.SkinnyUserResponse[]` | No |  |

### GetPlaceContributorsResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `nextCursor` | `string` | No |  |
| `hasMore` | `boolean` | No |  |
| `contributors` | `integer[]` | No |  |

### OperationErrorResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `code` | `integer` | No |  |
| `error` | `string` | No |  |
| `message` | `string` | No |  |

### GetPlaceVersionHistoryResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `nextCursor` | `string` | No |  |
| `hasMore` | `boolean` | No |  |
| `placeVersions` | `PlaceVersion[]` | No |  |

### UpdatePlaceVersionNotesRequest

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `title` | `string` | No |  |
| `description` | `string` | No |  |

### UpdatePlaceVersionNotesResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `placeVersion` | `PlaceVersion` | No |  |

### CreatePlaceVersionOperationResponse

response for !:CreatePlaceVersionOperation

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `versionNumber` | `integer` | No |  |

### Roblox.Games.Api.Models.Response.PlaceDetails

Response model for a place.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `placeId` | `integer` | No | Place Id |
| `name` | `string` | No | Place name |
| `description` | `string` | No | Place description |
| `sourceName` | `string` | No | Place name in source language |
| `sourceDescription` | `string` | No | Place description in source language |
| `url` | `string` | No | Url |
| `builder` | `string` | No | Creator name |
| `builderId` | `integer` | No | Creator Id |
| `hasVerifiedBadge` | `boolean` | No | Builder verified badge status. |
| `isPlayable` | `boolean` | No | Is playable |
| `reasonProhibited` | `string` | No | Reason prohibited |
| `universeId` | `integer` | No | Universe id |
| `universeRootPlaceId` | `integer` | No | UniverseRootPlaceId |
| `price` | `integer` | No | Price |
| `imageToken` | `string` | No | Place image token |
| `fiatPurchaseData` | `Roblox.Games.Api.Models.Response.PurchaseData` | No |  |

### PublicServerBrowserService.ServerType

Values: `0`, `1`

### PublicServerBrowserService.SortOrder

Values: `1`, `2`

### GameServerResponsePageResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `previousPageCursor` | `string` | No |  |
| `nextPageCursor` | `string` | No |  |
| `data` | `PublicServerBrowserService.GameServerResponse[]` | No |  |

### Roblox.Api.Develop.Models.PlaceModel

A model containing information about a place

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No | Returns the place id. |
| `universeId` | `integer` | No | Returns the id of the place's universe, or null - if the place is not part of a universe. |
| `name` | `string` | No | Returns the place name. |
| `description` | `string` | No | Returns the place description. |

### Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Api.Develop.Models.IPlaceModel_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `previousPageCursor` | `string` | No |  |
| `nextPageCursor` | `string` | No |  |
| `data` | `Roblox.Api.Develop.Models.IPlaceModel[]` | No |  |

### ServerListSortOption

Values: `0`, `1`, `2`, `3`, `4`

### Roblox.Api.Develop.Models.PlaceModelV2

A model containing information about a place

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `maxPlayerCount` | `integer` | No | The max number of players for the place. |
| `socialSlotType` | `string` | No | The social slot type for the place. Determines how users are placed into servers.  Examples:       Automatic,      Empty,      Custom |
| `customSocialSlotsCount` | `integer` | No | The number of social slots for the place when the slot type is custom. |
| `allowCopying` | `boolean` | No | Determines if copying of the place is allowed. |
| `currentSavedVersion` | `integer` | No | The current saved version number of the place. |
| `isAllGenresAllowed` | `boolean` | No | Whether all genres allowed in the place. |
| `allowedGearTypes` | `integer enum (10 values)[]` | No | Types of Roblox gear that are allowed to exist in the place. Valid values are from amp::AssetCategory Values: 0, 8, 9, 10, 11, 12, 13, 14, 21, 22 |
| `maxPlayersAllowed` | `integer` | No | The maximum allowed number of players for the place that the user can set, based on user roleset. |
| `created` | `string` | No | The time place was created. |
| `updated` | `string` | No | The time place was updated. |
| `id` | `integer` | No | Returns the place id. |
| `universeId` | `integer` | No | Returns the id of the place's universe, or null - if the place is not part of a universe. |
| `name` | `string` | No | Returns the place name. |
| `description` | `string` | No | Returns the place description. |
| `isRootPlace` | `boolean` | No | Returns whether this place is the root place. |

### Roblox.Api.Develop.Models.PlaceConfigurationModelV2

A model containing information about a place to be configured

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `name` | `string` | No | The name for the place. |
| `description` | `string` | No | The new description for the place. |
| `maxPlayerCount` | `integer` | No | The max number of players for the place. |
| `socialSlotType` | `string` | No | The social slot type for the place. Determines how users are placed into servers.  Examples:       Automatic,      Empty,      Custom |
| `customSocialSlotsCount` | `integer` | No | The number of social slots for the place when the slot type is custom. |
| `allowCopying` | `boolean` | No | Determines if copying of the place is allowed. |
| `allowedGearTypes` | `string[]` | No | List of allowed gear types |
| `isAllGenresAllowed` | `boolean` | No | If all genres are allowed, or only the experience type |

### PublicServerBrowserService.GameServerResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `string` | No |  |
| `maxPlayers` | `integer` | No |  |
| `playing` | `integer` | No |  |
| `playerTokens` | `string[]` | No |  |
| `players` | `GameServerPlayerResponse[]` | No |  |
| `fps` | `number` | No |  |
| `ping` | `integer` | No |  |
| `languageMatchCount` | `integer` | No |  |
| `pingSignalLevel` | `PingSignalLevel` | No |  |
| `friendCount` | `integer` | No |  |
| `name` | `string` | No |  |
| `vipServerId` | `integer` | No |  |
| `accessCode` | `string` | No |  |
| `owner` | `VerifiedBadgeUserResponse` | No |  |

### GameServerPlayerResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No |  |
| `name` | `string` | No |  |
| `displayName` | `string` | No |  |
| `playerToken` | `string` | No |  |

### PingSignalLevel

Values: `Low`, `Medium`, `High`

### VerifiedBadgeUserResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No |  |
| `name` | `string` | No |  |
| `displayName` | `string` | No |  |
| `hasVerifiedBadge` | `boolean` | No |  |

### Roblox.Games.Api.Models.Response.PurchaseData

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `localizedFiatPrice` | `string` | No | Fiat purchase price in a localized string for display on client. |
| `basePriceId` | `string` | No | ID of base price, needed by clients to prepare purchase url. |

### PlaceVersion

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `version` | `string` | No |  |
| `title` | `string` | No |  |
| `description` | `string` | No |  |
| `contributors` | `integer[]` | No |  |
| `saveType` | `SaveType` | No |  |
| `isPublished` | `boolean` | No |  |
| `publishStatus` | `PublishStatus` | No |  |
| `hasNotes` | `boolean` | No |  |
| `createdTime` | `string` | No |  |
| `createdBy` | `integer` | No |  |

### SaveType

Values: `0`, `1`, `2`

### PublishStatus

Values: `0`, `1`, `2`

### Roblox.Web.Responses.Users.SkinnyUserResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No |  |
| `name` | `string` | No |  |
| `displayName` | `string` | No |  |

### GoogleProtobufAny

Contains an arbitrary serialized message along with a @type that describes the type of the serialized message.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `@type` | `string` | No | The type of the serialized message. |

### Status

The `Status` type defines a logical error model that is suitable for different programming environments, including REST APIs and RPC APIs. It is used by [gRPC](https://github.com/grpc). Each `Status` message contains three pieces of data: error code, error message, and error details. You can find out more about this error model and how to work with it in the [API Design Guide](https://cloud.google.com/apis/design/errors).

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `code` | `integer` | No | The status code, which should be an enum value of [google.rpc.Code][google.rpc.Code]. |
| `message` | `string` | No | A developer-facing error message, which should be in English. Any user-facing error message should be localized and sent in the [google.rpc.Status.details][google.rpc.Status.details] field, or localized by the client. |
| `details` | `GoogleProtobufAny[]` | No | A list of messages that carry the error details.  There is a common set of message types for APIs to use. |

### roblox.engine.Instance

Instance is the base class for all classes in the Roblox class hierarchy.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `Id` | `string` | No | The unique identifier for an instance.  Format: lower-case hexadecimal characters Example: 44b188da-ce63-2b47-02e9-c68d004b5664 |
| `Parent` | `string` | No | The parent of the Instance. Format: lower-case hexadecimal characters Example: 44b188da-ce63-2b47-02e9-c68d004b5664 |
| `Name` | `string` | No | A non-unique identifier of the Instance. |
| `Details` | `roblox.engine.InstanceDetails` | No | Properties specific to the type of the instance. |

### roblox.engine.InstanceDetails

Contains instance type-specific details about a data model instance.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `Folder` | `roblox.engine.Folder` | No | A simple container used to hold and organize Roblox instances. |
| `LocalScript` | `roblox.engine.LocalScript` | No | A LocalScript is a Lua code container that runs its contents on the client (player's device) instead of the server. |
| `ModuleScript` | `roblox.engine.ModuleScript` | No | A ModuleScript is a type of Lua source container that runs once and must return exactly one value. |
| `Script` | `roblox.engine.Script` | No | A Script is a Lua code container that can access server-side objects, properties, and events, such as to award badges to players using BadgeService, while LocalScripts on the client cannot. |

### roblox.engine.Folder

A simple container used to hold and organize Roblox instances.

| Property | Type | Required | Description |
|----------|------|----------|-------------|

### roblox.engine.LocalScript

A LocalScript is a Lua code container that runs its contents on the client (player's device) instead of the server.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `Enabled` | `boolean` | No | Determines whether a BaseScript will run or not. |
| `RunContext` | `Legacy \| Server \| Client \| Plugin` | No | Determines the context under which the script will run.  Possible values:    \| Value \| Description \|   \| --- \| --- \|   \| Legacy \| Runs in legacy script containers dependent on the type of script used, such as LocalScript or Script. \|   \| Server \| Runs on the server. \|   \| Client \| Runs on the client. \|   \| Plugin \| Runs as a descendant of Plugin instances. \| |
| `Source` | `string` | No | The code to be executed. |

### roblox.engine.ModuleScript

A ModuleScript is a type of Lua source container that runs once and must return exactly one value.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `Source` | `string` | No | The code to be executed. |

### roblox.engine.Script

A Script is a Lua code container that can access server-side objects, properties, and events, such as to award badges to players using BadgeService, while LocalScripts on the client cannot.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `Enabled` | `boolean` | No | Determines whether the BaseScript will run or not. |
| `RunContext` | `Legacy \| Server \| Client \| Plugin` | No | Determines the context in which the script will run.  Possible values:    \| Value \| Description \|   \| --- \| --- \|   \| Legacy \| Runs in legacy script containers dependent on the type of script used, such as LocalScript or Script. \|   \| Server \| Runs on the server. \|   \| Client \| Runs on the client. \|   \| Plugin \| Runs as a descendant of Plugin instances. \| |
| `Source` | `string` | No | The code to be executed. |