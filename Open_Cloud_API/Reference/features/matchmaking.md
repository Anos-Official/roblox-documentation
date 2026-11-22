<!-- Source: https://create.roblox.com/docs/cloud/reference/features/matchmaking.md -->

---
name: "Matchmaking"
last_updated: 2026-11-20T18:47:47Z
type: feature
api_base_url: "https://apis.roblox.com"
endpoints: 32
auth: [api-key, oauth2, cookie]
description: "Configure and manage matchmaking for your experiences"
---

# Matchmaking

Configure and manage matchmaking for your experiences. Matchmaking APIs help you create fair, balanced matches by considering player skill, preferences, and latency.

Common use cases include:

- Player attributes: [Define](#post_matchmaking_api_v1_matchmaking_player_attribute) and [manage](#patch_matchmaking_api_v1_matchmaking_player_attribute__attributeId_) custom player attributes for matching (skill level, preferences, etc.)
- Scoring configuration: [Create](#post_matchmaking_api_v1_matchmaking_scoring_configuration) and [tune](#patch_matchmaking_api_v1_matchmaking_scoring_configuration__scoringConfigurationId_) scoring configurations that determine match quality
- Instance control: [Shut down game instances](#post_matchmaking_api_v1_game_instances_shutdown) for maintenance

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

### GET `/matchmaking-api/v1/client-status` [BETA]

Get the client-status

**Auth:** 

**Request Body:** `application/json-patch+json` — Type: `ClientStatusGetRequest`

See [ClientStatusGetRequest](#clientstatusgetrequest) in Models.

**Request example:**
```json
{
  "browserTrackerId": 0
}
```

**Responses:**

- `200`: OK

**Example:**
```bash
curl -H "Authorization: Bearer $ROBLOX_ACCESS_TOKEN" \
  "https://apis.roblox.com/matchmaking-api/v1/client-status" \
  -H "Content-Type: application/json" \
  -d '{
  "browserTrackerId": 0
}'
```

### POST `/matchmaking-api/v1/client-status` [BETA]

Set the client-status

**Auth:** 

**Request Body:** `application/json-patch+json` — Type: `ClientStatusSetRequest`

See [ClientStatusSetRequest](#clientstatussetrequest) in Models.

**Request example:**
```json
{
  "status": "string",
  "browserTrackerId": 0
}
```

**Responses:**

- `200`: OK

**Example:**
```bash
curl -X POST -H "Authorization: Bearer $ROBLOX_ACCESS_TOKEN" \
  "https://apis.roblox.com/matchmaking-api/v1/client-status" \
  -H "Content-Type: application/json" \
  -d '{
  "status": "string",
  "browserTrackerId": 0
}'
```

### POST `/matchmaking-api/v1/game-instances/forecast-update` [BETA]

Forecast the outcome of launching an update

**Auth:** Cookie (`.ROBLOSECURITY`)

**Request Body:** `application/json-patch+json` — Type: `ForecastUpdateRequest`

See [ForecastUpdateRequest](#forecastupdaterequest) in Models.

**Request example:**
```json
{
  "universeId": 0
}
```

**Responses:**

- `200`: OK → `ForecastUpdateResponse`

**Response fields** (`ForecastUpdateResponse`)

See [ForecastUpdateResponse](#forecastupdateresponse) in Models.

**Response example:**
```json
{
  "placeSummaries": [
    {
      "placeId": "...",
      "playersToBeKicked": "...",
      "totalPlayers": "...",
      "instancesToBeClosed": "...",
      "totalInstances": "...",
      "placeVersion": "..."
    }
  ]
}
```

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://apis.roblox.com/matchmaking-api/v1/game-instances/forecast-update" \
  -H "Content-Type: application/json" \
  -d '{
  "universeId": 0
}'
```

### GET `/matchmaking-api/v1/game-instances/get-update-status` [BETA]

Get the rollout status of an update

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | query | `integer` | No |  |

**Responses:**

- `200`: OK → `GetUpdateStatusResponse`

**Response fields** (`GetUpdateStatusResponse`)

See [GetUpdateStatusResponse](#getupdatestatusresponse) in Models.

**Response example:**
```json
{
  "updateStatusList": [
    {
      "id": "...",
      "universeId": "...",
      "startTime": "...",
      "closeOldVersionsOnly": "...",
      "bleedOffEndTime": "...",
      "placeUpdateStatuses": "..."
    }
  ]
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://apis.roblox.com/matchmaking-api/v1/game-instances/get-update-status"
```

### POST `/matchmaking-api/v1/game-instances/launch-update` [BETA]

Launch a game update

**Auth:** Cookie (`.ROBLOSECURITY`)

**Request Body:** `application/json-patch+json` — Type: `LaunchUpdateRequest`

See [LaunchUpdateRequest](#launchupdaterequest) in Models.

**Request example:**
```json
{
  "universeId": 0,
  "placeIds": [
    0
  ],
  "closeOldVersionsOnly": false,
  "bleedOffServers": false,
  "bleedOffDurationMinutes": 0,
  "placeIdToVersions": "..."
}
```

**Responses:**

- `200`: OK → `LaunchUpdateResponse`

**Response fields** (`LaunchUpdateResponse`)

See [LaunchUpdateResponse](#launchupdateresponse) in Models.

**Response example:**
```json
{
  "updateId": "string",
  "numPlayersToBeKicked": 0,
  "instancesToBeClosed": 0
}
```

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://apis.roblox.com/matchmaking-api/v1/game-instances/launch-update" \
  -H "Content-Type: application/json" \
  -d '{
  "universeId": 0,
  "placeIds": [
    0
  ],
  "closeOldVersionsOnly": false,
  "bleedOffServers": false,
  "bleedOffDurationMinutes": 0,
  "placeIdToVersions": "..."
}'
```

### POST `/matchmaking-api/v1/game-instances/shutdown` [BETA]

Shutdown game instances.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe:write`

**Request Body:** `application/json-patch+json` — Type: `ShutdownGameInstancesRequest`

See [ShutdownGameInstancesRequest](#shutdowngameinstancesrequest) in Models.

**Request example:**
```json
{
  "placeId": 0,
  "privateServerId": 0,
  "gameId": "string"
}
```

**Responses:**

- `200`: OK → `ShutdownGameInstancesResponse`

**Response fields** (`ShutdownGameInstancesResponse`)

See [ShutdownGameInstancesResponse](#shutdowngameinstancesresponse) in Models.

**Response example:**
```json
{
  "placeId": 0,
  "privateServerId": 0,
  "gameId": "string"
}
```

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/matchmaking-api/v1/game-instances/shutdown" \
  -H "Content-Type: application/json" \
  -d '{
  "placeId": 0,
  "privateServerId": 0,
  "gameId": "string"
}'
```

### POST `/matchmaking-api/v1/matchmaking/player-attribute` [BETA]

Create a PlayerAttributeDefinition.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.matchmaking-configuration:write`

**Request Body:** `application/json-patch+json` — Type: `CreateMatchmakingPlayerAttributeDefinitionRequest`

See [CreateMatchmakingPlayerAttributeDefinitionRequest](#creatematchmakingplayerattributedefinitionrequest) in Models.

**Request example:**
```json
{
  "universeId": 0,
  "name": "string",
  "dataType": "Invalid",
  "defaultValue": {
    "boolValue": false,
    "numericValue": 0,
    "stringValue": "string",
    "type": "Invalid"
  },
  "attributeValueLocation": {
    "locationCase": "Invalid",
    "dataStoreLocation": {
      "dataStoreName": "...",
      "scope": "...",
      "keyTemplate": "...",
      "valuePath": "..."
    }
  }
}
```

**Responses:**

- `200`: OK → `CreateMatchmakingPlayerAttributeDefinitionResponse`

**Response fields** (`CreateMatchmakingPlayerAttributeDefinitionResponse`)

See [CreateMatchmakingPlayerAttributeDefinitionResponse](#creatematchmakingplayerattributedefinitionresponse) in Models.

**Response example:**
```json
{
  "playerAttributeDefinition": {
    "id": "string",
    "universeId": 0,
    "name": "string",
    "dataType": "Invalid",
    "defaultValue": {
      "boolValue": "...",
      "numericValue": "...",
      "stringValue": "...",
      "type": "..."
    },
    "attributeValueLocation": {
      "locationCase": "...",
      "dataStoreLocation": "..."
    }
  }
}
```

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/matchmaking-api/v1/matchmaking/player-attribute" \
  -H "Content-Type: application/json" \
  -d '{"universeId":0,"name":"string","dataType":"Invalid","defaultValue":{"boolValue":false,"numericValue":0,"stringValue":"string","type":"Invalid"},"attributeValueLocation":{"locationCase":"Invalid","dataStoreLocation":{"dataStoreName":"...","scope":"...","keyTemplate":"...","valuePath":"..."}}}'
```

### PATCH `/matchmaking-api/v1/matchmaking/player-attribute/{attributeId}` [BETA]

Update the PlayerAttributeDefinition specified by attributeId.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.matchmaking-configuration:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `attributeId` | path | `string` | Yes |  |

**Request Body:** `application/json-patch+json` — Type: `UpdateMatchmakingPlayerAttributeDefinitionRequest`

See [UpdateMatchmakingPlayerAttributeDefinitionRequest](#updatematchmakingplayerattributedefinitionrequest) in Models.

**Request example:**
```json
{
  "attributeId": "string",
  "defaultValue": {
    "boolValue": false,
    "numericValue": 0,
    "stringValue": "string",
    "type": "Invalid"
  },
  "attributeValueLocation": {
    "locationCase": "Invalid",
    "dataStoreLocation": {
      "dataStoreName": "...",
      "scope": "...",
      "keyTemplate": "...",
      "valuePath": "..."
    }
  }
}
```

**Responses:**

- `200`: OK → `UpdateMatchmakingPlayerAttributeDefinitionResponse`

**Response fields** (`UpdateMatchmakingPlayerAttributeDefinitionResponse`)

See [UpdateMatchmakingPlayerAttributeDefinitionResponse](#updatematchmakingplayerattributedefinitionresponse) in Models.

**Response example:**
```json
{
  "playerAttributeDefinition": {
    "id": "string",
    "universeId": 0,
    "name": "string",
    "dataType": "Invalid",
    "defaultValue": {
      "boolValue": "...",
      "numericValue": "...",
      "stringValue": "...",
      "type": "..."
    },
    "attributeValueLocation": {
      "locationCase": "...",
      "dataStoreLocation": "..."
    }
  }
}
```

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X PATCH -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/matchmaking-api/v1/matchmaking/player-attribute/{ATTRIBUTEID}" \
  -H "Content-Type: application/json" \
  -d '{"attributeId":"string","defaultValue":{"boolValue":false,"numericValue":0,"stringValue":"string","type":"Invalid"},"attributeValueLocation":{"locationCase":"Invalid","dataStoreLocation":{"dataStoreName":"...","scope":"...","keyTemplate":"...","valuePath":"..."}}}'
```

### DELETE `/matchmaking-api/v1/matchmaking/player-attribute/{attributeId}` [BETA]

Delete the PlayerAttributeDefinition specified by attributeId.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.matchmaking-configuration:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `attributeId` | path | `string` | Yes |  |

**Responses:**

- `200`: OK → `DeleteMatchmakingPlayerAttributeDefinitionResponse`

**Response fields** (`DeleteMatchmakingPlayerAttributeDefinitionResponse`)

See [DeleteMatchmakingPlayerAttributeDefinitionResponse](#deletematchmakingplayerattributedefinitionresponse) in Models.

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X DELETE -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/matchmaking-api/v1/matchmaking/player-attribute/{ATTRIBUTEID}"
```

### GET `/matchmaking-api/v1/matchmaking/player-attributes/{universeId}` [BETA]

List all PlayerAttributeDefinitions of a universe.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.matchmaking-configuration:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |

**Responses:**

- `200`: OK → `ListMatchmakingPlayerAttributeDefinitionsResponse`

**Response fields** (`ListMatchmakingPlayerAttributeDefinitionsResponse`)

See [ListMatchmakingPlayerAttributeDefinitionsResponse](#listmatchmakingplayerattributedefinitionsresponse) in Models.

**Response example:**
```json
{
  "playerAttributeSchema": [
    {
      "id": "...",
      "universeId": "...",
      "name": "...",
      "dataType": "...",
      "defaultValue": "...",
      "attributeValueLocation": "..."
    }
  ]
}
```

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/matchmaking-api/v1/matchmaking/player-attributes/{UNIVERSEID}"
```

### POST `/matchmaking-api/v1/matchmaking/scoring-configuration` [BETA]

Creates a matchmaking scoring configuration.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.matchmaking-configuration:write`

**Request Body:** `application/json-patch+json` — Type: `CreateMatchmakingScoringConfigurationRequest`

See [CreateMatchmakingScoringConfigurationRequest](#creatematchmakingscoringconfigurationrequest) in Models.

**Request example:**
```json
{
  "universeId": 0,
  "name": "string",
  "matchmakingSignalWeights": {
    "Invalid": 0,
    "Occupancy": 0,
    "Age": 0,
    "Language": 0,
    "Latency": 0,
    "PreferredPlayers": 0
  },
  "customSignalWeights": "...",
  "template": "NotApplicable"
}
```

**Responses:**

- `200`: OK → `CreateMatchmakingScoringConfigurationResponse`

**Response fields** (`CreateMatchmakingScoringConfigurationResponse`)

See [CreateMatchmakingScoringConfigurationResponse](#creatematchmakingscoringconfigurationresponse) in Models.

**Response example:**
```json
{
  "scoringConfiguration": {
    "id": "string",
    "name": "string",
    "signalWeights": {
      "Invalid": "...",
      "Occupancy": "...",
      "Age": "...",
      "Language": "...",
      "Latency": "...",
      "PreferredPlayers": "..."
    },
    "customSignals": "...",
    "createdTime": "2024-01-01T00:00:00Z",
    "updatedTime": "2024-01-01T00:00:00Z"
  }
}
```

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/matchmaking-api/v1/matchmaking/scoring-configuration" \
  -H "Content-Type: application/json" \
  -d '{
  "universeId": 0,
  "name": "string",
  "matchmakingSignalWeights": {
    "Invalid": 0,
    "Occupancy": 0,
    "Age": 0,
    "Language": 0,
    "Latency": 0,
    "PreferredPlayers": 0
  },
  "customSignalWeights": "...",
  "template": "NotApplicable"
}'
```

### GET `/matchmaking-api/v1/matchmaking/scoring-configuration/default-weights` [BETA]

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.matchmaking-configuration:read`

**Responses:**

- `200`: OK → `GetMatchmakingScoringDefaultWeightsResponse`

**Response fields** (`GetMatchmakingScoringDefaultWeightsResponse`)

See [GetMatchmakingScoringDefaultWeightsResponse](#getmatchmakingscoringdefaultweightsresponse) in Models.

**Response example:**
```json
{
  "weights": {
    "Invalid": 0,
    "Occupancy": 0,
    "Age": 0,
    "Language": 0,
    "Latency": 0,
    "PreferredPlayers": 0
  }
}
```

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/matchmaking-api/v1/matchmaking/scoring-configuration/default-weights"
```

### GET `/matchmaking-api/v1/matchmaking/scoring-configuration/generate-mock-servers` [BETA]

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.matchmaking-configuration:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `count` | query | `integer` | No |  |
| `capacity` | query | `integer` | No |  |
| `playerAge` | query | `integer` | No |  |
| `playerPlayHistory` | query | `number` | No |  |
| `isPlayerVoiceChatEnabled` | query | `boolean` | No |  |

**Responses:**

- `200`: OK → `GenerateMockServerSignalValuesResponse`

**Response fields** (`GenerateMockServerSignalValuesResponse`)

See [GenerateMockServerSignalValuesResponse](#generatemockserversignalvaluesresponse) in Models.

**Response example:**
```json
{
  "exampleGameSignalValues": [
    {
      "capacity": "...",
      "occupancy": "...",
      "hasPreferredPlayers": "...",
      "playerAge": "...",
      "serverAveragePlayerAge": "...",
      "commonLanguagePlayers": "..."
    }
  ]
}
```

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/matchmaking-api/v1/matchmaking/scoring-configuration/generate-mock-servers"
```

### POST `/matchmaking-api/v1/matchmaking/scoring-configuration/place` [BETA]

Sets a matchmaking scoring configuration for a place.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.matchmaking-configuration:write`

**Request Body:** `application/json-patch+json` — Type: `SetPlaceMatchmakingScoringConfigurationRequest`

See [SetPlaceMatchmakingScoringConfigurationRequest](#setplacematchmakingscoringconfigurationrequest) in Models.

**Request example:**
```json
{
  "placeId": 0,
  "scoringConfigurationId": "string"
}
```

**Responses:**

- `200`: OK → `SetMatchmakingScoringConfigurationResponse`

**Response fields** (`SetMatchmakingScoringConfigurationResponse`)

See [SetMatchmakingScoringConfigurationResponse](#setmatchmakingscoringconfigurationresponse) in Models.

**Response example:**
```json
{
  "scoringConfiguration": {
    "id": "string",
    "name": "string",
    "signalWeights": {
      "Invalid": "...",
      "Occupancy": "...",
      "Age": "...",
      "Language": "...",
      "Latency": "...",
      "PreferredPlayers": "..."
    },
    "customSignals": "...",
    "createdTime": "2024-01-01T00:00:00Z",
    "updatedTime": "2024-01-01T00:00:00Z"
  }
}
```

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/matchmaking-api/v1/matchmaking/scoring-configuration/place" \
  -H "Content-Type: application/json" \
  -d '{
  "placeId": 0,
  "scoringConfigurationId": "string"
}'
```

### DELETE `/matchmaking-api/v1/matchmaking/scoring-configuration/place/{placeId}` [BETA]

Removes the matchmaking scoring configuration for a place.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.matchmaking-configuration:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `placeId` | path | `integer` | Yes |  |

**Responses:**

- `200`: OK → `RemovePlaceMatchmakingScoringConfigurationResponse`

**Response fields** (`RemovePlaceMatchmakingScoringConfigurationResponse`)

See [RemovePlaceMatchmakingScoringConfigurationResponse](#removeplacematchmakingscoringconfigurationresponse) in Models.

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X DELETE -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/matchmaking-api/v1/matchmaking/scoring-configuration/place/{PLACEID}"
```

### GET `/matchmaking-api/v1/matchmaking/scoring-configuration/{scoringConfigurationId}` [BETA]

Updates a matchmaking scoring configuration.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.matchmaking-configuration:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `scoringConfigurationId` | path | `string` | Yes |  |

**Responses:**

- `200`: OK → `GetMatchmakingScoringConfigurationResponse`

**Response fields** (`GetMatchmakingScoringConfigurationResponse`)

See [GetMatchmakingScoringConfigurationResponse](#getmatchmakingscoringconfigurationresponse) in Models.

**Response example:**
```json
{
  "scoringConfiguration": {
    "id": "string",
    "name": "string",
    "signalWeights": {
      "Invalid": "...",
      "Occupancy": "...",
      "Age": "...",
      "Language": "...",
      "Latency": "...",
      "PreferredPlayers": "..."
    },
    "customSignals": "...",
    "createdTime": "2024-01-01T00:00:00Z",
    "updatedTime": "2024-01-01T00:00:00Z"
  }
}
```

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/matchmaking-api/v1/matchmaking/scoring-configuration/{SCORINGCONFIGURATIONID}"
```

### PATCH `/matchmaking-api/v1/matchmaking/scoring-configuration/{scoringConfigurationId}` [BETA]

Updates a matchmaking scoring configuration.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.matchmaking-configuration:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `scoringConfigurationId` | path | `string` | Yes |  |

**Request Body:** `application/json-patch+json` — Type: `UpdateMatchmakingScoringConfigurationRequest`

See [UpdateMatchmakingScoringConfigurationRequest](#updatematchmakingscoringconfigurationrequest) in Models.

**Request example:**
```json
{
  "scoringConfigurationId": "string",
  "name": "string",
  "matchmakingSignalWeights": {
    "Invalid": 0,
    "Occupancy": 0,
    "Age": 0,
    "Language": 0,
    "Latency": 0,
    "PreferredPlayers": 0
  },
  "customSignalWeights": "..."
}
```

**Responses:**

- `200`: OK → `UpdateMatchmakingScoringConfigurationResponse`

**Response fields** (`UpdateMatchmakingScoringConfigurationResponse`)

See [UpdateMatchmakingScoringConfigurationResponse](#updatematchmakingscoringconfigurationresponse) in Models.

**Response example:**
```json
{
  "scoringConfiguration": {
    "id": "string",
    "name": "string",
    "signalWeights": {
      "Invalid": "...",
      "Occupancy": "...",
      "Age": "...",
      "Language": "...",
      "Latency": "...",
      "PreferredPlayers": "..."
    },
    "customSignals": "...",
    "createdTime": "2024-01-01T00:00:00Z",
    "updatedTime": "2024-01-01T00:00:00Z"
  }
}
```

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X PATCH -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/matchmaking-api/v1/matchmaking/scoring-configuration/{SCORINGCONFIGURATIONID}" \
  -H "Content-Type: application/json" \
  -d '{
  "scoringConfigurationId": "string",
  "name": "string",
  "matchmakingSignalWeights": {
    "Invalid": 0,
    "Occupancy": 0,
    "Age": 0,
    "Language": 0,
    "Latency": 0,
    "PreferredPlayers": 0
  },
  "customSignalWeights": "..."
}'
```

### DELETE `/matchmaking-api/v1/matchmaking/scoring-configuration/{scoringConfigurationId}` [BETA]

Deletes a matchmaking scoring configuration.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.matchmaking-configuration:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `scoringConfigurationId` | path | `string` | Yes |  |

**Responses:**

- `200`: OK → `DeleteMatchmakingScoringConfigurationResponse`

**Response fields** (`DeleteMatchmakingScoringConfigurationResponse`)

See [DeleteMatchmakingScoringConfigurationResponse](#deletematchmakingscoringconfigurationresponse) in Models.

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X DELETE -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/matchmaking-api/v1/matchmaking/scoring-configuration/{SCORINGCONFIGURATIONID}"
```

### POST `/matchmaking-api/v1/matchmaking/scoring-configuration/{scoringConfigurationId}/signals` [BETA]

Creates a matchmaking scoring configuration signal.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.matchmaking-configuration:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `scoringConfigurationId` | path | `string` | Yes |  |

**Request Body:** `application/json-patch+json` — Type: `CreateCustomMatchmakingSignalRequest`

See [CreateCustomMatchmakingSignalRequest](#createcustommatchmakingsignalrequest) in Models.

**Request example:**
```json
{
  "scoringConfigurationId": "string",
  "signalConfiguration": {
    "name": "string",
    "weight": 0,
    "customSignalType": "Invalid",
    "playerCategoricalSignalConfiguration": {
      "playerAttribute": "...",
      "curveType": "..."
    },
    "serverCategoricalSignalConfiguration": {
      "serverAttribute": "...",
      "comparisonType": "...",
      "playerAttribute": "...",
      "constantValue": "..."
    },
    "serverNumericalSignalConfiguration": {
      "serverAttribute": "...",
      "comparisonType": "...",
      "maxRelevantDifference": "...",
      "constantValue": "...",
      "playerAttribute": "..."
    }
  }
}
```

**Responses:**

- `200`: OK → `CreateCustomMatchmakingSignalResponse`

**Response fields** (`CreateCustomMatchmakingSignalResponse`)

See [CreateCustomMatchmakingSignalResponse](#createcustommatchmakingsignalresponse) in Models.

**Response example:**
```json
{
  "scoringConfiguration": {
    "id": "string",
    "name": "string",
    "signalWeights": {
      "Invalid": "...",
      "Occupancy": "...",
      "Age": "...",
      "Language": "...",
      "Latency": "...",
      "PreferredPlayers": "..."
    },
    "customSignals": "...",
    "createdTime": "2024-01-01T00:00:00Z",
    "updatedTime": "2024-01-01T00:00:00Z"
  }
}
```

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/matchmaking-api/v1/matchmaking/scoring-configuration/{SCORINGCONFIGURATIONID}/signals" \
  -H "Content-Type: application/json" \
  -d '{"scoringConfigurationId":"string","signalConfiguration":{"name":"string","weight":0,"customSignalType":"Invalid","playerCategoricalSignalConfiguration":{"playerAttribute":"...","curveType":"..."},"serverCategoricalSignalConfiguration":{"serverAttribute":"...","comparisonType":"...","playerAttribute":"...","constantValue":"..."},"serverNumericalSignalConfiguration":{"serverAttribute":"...","comparisonType":"...","maxRelevantDifference":"...","constantValue":"...","playerAttribute":"..."}}}'
```

### PATCH `/matchmaking-api/v1/matchmaking/scoring-configuration/{scoringConfigurationId}/signals/{signalName}` [BETA]

Updates a matchmaking scoring configuration signal.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.matchmaking-configuration:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `scoringConfigurationId` | path | `string` | Yes |  |
| `signalName` | path | `string` | Yes |  |

**Request Body:** `application/json-patch+json` — Type: `UpdateCustomMatchmakingSignalRequest`

See [UpdateCustomMatchmakingSignalRequest](#updatecustommatchmakingsignalrequest) in Models.

**Request example:**
```json
{
  "scoringConfigurationId": "string",
  "signalConfiguration": {
    "name": "string",
    "weight": 0,
    "customSignalType": "Invalid",
    "playerCategoricalSignalConfiguration": {
      "playerAttribute": "...",
      "curveType": "..."
    },
    "serverCategoricalSignalConfiguration": {
      "serverAttribute": "...",
      "comparisonType": "...",
      "playerAttribute": "...",
      "constantValue": "..."
    },
    "serverNumericalSignalConfiguration": {
      "serverAttribute": "...",
      "comparisonType": "...",
      "maxRelevantDifference": "...",
      "constantValue": "...",
      "playerAttribute": "..."
    }
  }
}
```

**Responses:**

- `200`: OK → `UpdateCustomMatchmakingSignalResponse`

**Response fields** (`UpdateCustomMatchmakingSignalResponse`)

See [UpdateCustomMatchmakingSignalResponse](#updatecustommatchmakingsignalresponse) in Models.

**Response example:**
```json
{
  "scoringConfiguration": {
    "id": "string",
    "name": "string",
    "signalWeights": {
      "Invalid": "...",
      "Occupancy": "...",
      "Age": "...",
      "Language": "...",
      "Latency": "...",
      "PreferredPlayers": "..."
    },
    "customSignals": "...",
    "createdTime": "2024-01-01T00:00:00Z",
    "updatedTime": "2024-01-01T00:00:00Z"
  }
}
```

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X PATCH -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/matchmaking-api/v1/matchmaking/scoring-configuration/{SCORINGCONFIGURATIONID}/signals/{SIGNALNAME}" \
  -H "Content-Type: application/json" \
  -d '{"scoringConfigurationId":"string","signalConfiguration":{"name":"string","weight":0,"customSignalType":"Invalid","playerCategoricalSignalConfiguration":{"playerAttribute":"...","curveType":"..."},"serverCategoricalSignalConfiguration":{"serverAttribute":"...","comparisonType":"...","playerAttribute":"...","constantValue":"..."},"serverNumericalSignalConfiguration":{"serverAttribute":"...","comparisonType":"...","maxRelevantDifference":"...","constantValue":"...","playerAttribute":"..."}}}'
```

### DELETE `/matchmaking-api/v1/matchmaking/scoring-configuration/{scoringConfigurationId}/signals/{signalName}` [BETA]

Deletes a matchmaking scoring configuration custom signal.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.matchmaking-configuration:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `scoringConfigurationId` | path | `string` | Yes |  |
| `signalName` | path | `string` | Yes |  |

**Responses:**

- `200`: OK → `DeleteCustomMatchmakingSignalResponse`

**Response fields** (`DeleteCustomMatchmakingSignalResponse`)

See [DeleteCustomMatchmakingSignalResponse](#deletecustommatchmakingsignalresponse) in Models.

**Response example:**
```json
{
  "scoringConfiguration": {
    "id": "string",
    "name": "string",
    "signalWeights": {
      "Invalid": "...",
      "Occupancy": "...",
      "Age": "...",
      "Language": "...",
      "Latency": "...",
      "PreferredPlayers": "..."
    },
    "customSignals": "...",
    "createdTime": "2024-01-01T00:00:00Z",
    "updatedTime": "2024-01-01T00:00:00Z"
  }
}
```

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X DELETE -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/matchmaking-api/v1/matchmaking/scoring-configuration/{SCORINGCONFIGURATIONID}/signals/{SIGNALNAME}"
```

### GET `/matchmaking-api/v1/matchmaking/scoring-configurations/{universeId}` [BETA]

List all matchmaking scoring configurations for a universe.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.matchmaking-configuration:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |

**Responses:**

- `200`: OK → `ListMatchmakingScoringConfigurationsResponse`

**Response fields** (`ListMatchmakingScoringConfigurationsResponse`)

See [ListMatchmakingScoringConfigurationsResponse](#listmatchmakingscoringconfigurationsresponse) in Models.

**Response example:**
```json
{
  "scoringConfigurations": [
    {
      "id": "...",
      "name": "...",
      "signalWeights": "...",
      "customSignals": "...",
      "createdTime": "...",
      "updatedTime": "..."
    }
  ]
}
```

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/matchmaking-api/v1/matchmaking/scoring-configurations/{UNIVERSEID}"
```

### GET `/matchmaking-api/v1/matchmaking/scoring-configurations/{universeId}/places` [BETA]

List all places with a matchmaking scoring configuration for a universe.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.matchmaking-configuration:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |

**Responses:**

- `200`: OK → `ListPlaceMatchmakingScoringConfigurationsResponse`

**Response fields** (`ListPlaceMatchmakingScoringConfigurationsResponse`)

See [ListPlaceMatchmakingScoringConfigurationsResponse](#listplacematchmakingscoringconfigurationsresponse) in Models.

**Response example:**
```json
{
  "placeScoringConfigurations": "..."
}
```

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/matchmaking-api/v1/matchmaking/scoring-configurations/{UNIVERSEID}/places"
```

### POST `/matchmaking-api/v1/matchmaking/server-attribute` [BETA]

Create a ServerAttributeDefinition.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.matchmaking-configuration:write`

**Request Body:** `application/json-patch+json` — Type: `CreateMatchmakingServerAttributeDefinitionRequest`

See [CreateMatchmakingServerAttributeDefinitionRequest](#creatematchmakingserverattributedefinitionrequest) in Models.

**Request example:**
```json
{
  "universeId": 0,
  "name": "string",
  "dataType": "Invalid",
  "defaultValue": {
    "sourceCase": "Invalid",
    "constant": {
      "boolValue": "...",
      "numericValue": "...",
      "stringValue": "...",
      "type": "..."
    },
    "playerAttributeReference": {
      "id": "..."
    }
  }
}
```

**Responses:**

- `200`: OK → `CreateMatchmakingServerAttributeDefinitionResponse`

**Response fields** (`CreateMatchmakingServerAttributeDefinitionResponse`)

See [CreateMatchmakingServerAttributeDefinitionResponse](#creatematchmakingserverattributedefinitionresponse) in Models.

**Response example:**
```json
{
  "playerAttributeDefinition": {
    "id": "string",
    "universeId": 0,
    "name": "string",
    "dataType": "Invalid",
    "defaultValue": {
      "sourceCase": "...",
      "constant": "...",
      "playerAttributeReference": "..."
    },
    "createdTime": "2024-01-01T00:00:00Z"
  }
}
```

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/matchmaking-api/v1/matchmaking/server-attribute" \
  -H "Content-Type: application/json" \
  -d '{"universeId":0,"name":"string","dataType":"Invalid","defaultValue":{"sourceCase":"Invalid","constant":{"boolValue":"...","numericValue":"...","stringValue":"...","type":"..."},"playerAttributeReference":{"id":"..."}}}'
```

### PATCH `/matchmaking-api/v1/matchmaking/server-attribute/{attributeId}` [BETA]

Update the ServerAttributeDefinition specified by attributeId.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.matchmaking-configuration:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `attributeId` | path | `string` | Yes |  |

**Request Body:** `application/json-patch+json` — Type: `UpdateMatchmakingServerAttributeDefinitionRequest`

See [UpdateMatchmakingServerAttributeDefinitionRequest](#updatematchmakingserverattributedefinitionrequest) in Models.

**Request example:**
```json
{
  "attributeId": "string",
  "defaultValue": {
    "sourceCase": "Invalid",
    "constant": {
      "boolValue": "...",
      "numericValue": "...",
      "stringValue": "...",
      "type": "..."
    },
    "playerAttributeReference": {
      "id": "..."
    }
  }
}
```

**Responses:**

- `200`: OK → `UpdateMatchmakingServerAttributeDefinitionResponse`

**Response fields** (`UpdateMatchmakingServerAttributeDefinitionResponse`)

See [UpdateMatchmakingServerAttributeDefinitionResponse](#updatematchmakingserverattributedefinitionresponse) in Models.

**Response example:**
```json
{
  "playerAttributeDefinition": {
    "id": "string",
    "universeId": 0,
    "name": "string",
    "dataType": "Invalid",
    "defaultValue": {
      "sourceCase": "...",
      "constant": "...",
      "playerAttributeReference": "..."
    },
    "createdTime": "2024-01-01T00:00:00Z"
  }
}
```

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X PATCH -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/matchmaking-api/v1/matchmaking/server-attribute/{ATTRIBUTEID}" \
  -H "Content-Type: application/json" \
  -d '{
  "attributeId": "string",
  "defaultValue": {
    "sourceCase": "Invalid",
    "constant": {
      "boolValue": "...",
      "numericValue": "...",
      "stringValue": "...",
      "type": "..."
    },
    "playerAttributeReference": {
      "id": "..."
    }
  }
}'
```

### DELETE `/matchmaking-api/v1/matchmaking/server-attribute/{attributeId}` [BETA]

Delete the ServerAttributeDefinition specified by attributeId.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.matchmaking-configuration:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `attributeId` | path | `string` | Yes |  |

**Responses:**

- `200`: OK → `DeleteMatchmakingServerAttributeDefinitionResponse`

**Response fields** (`DeleteMatchmakingServerAttributeDefinitionResponse`)

See [DeleteMatchmakingServerAttributeDefinitionResponse](#deletematchmakingserverattributedefinitionresponse) in Models.

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X DELETE -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/matchmaking-api/v1/matchmaking/server-attribute/{ATTRIBUTEID}"
```

### GET `/matchmaking-api/v1/matchmaking/server-attributes/{universeId}` [BETA]

List all ServerAttributeDefinitions of a universe.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.matchmaking-configuration:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |

**Responses:**

- `200`: OK → `ListMatchmakingServerAttributeDefinitionsResponse`

**Response fields** (`ListMatchmakingServerAttributeDefinitionsResponse`)

See [ListMatchmakingServerAttributeDefinitionsResponse](#listmatchmakingserverattributedefinitionsresponse) in Models.

**Response example:**
```json
{
  "serverAttributeSchema": [
    {
      "id": "...",
      "universeId": "...",
      "name": "...",
      "dataType": "...",
      "defaultValue": "...",
      "createdTime": "..."
    }
  ]
}
```

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/matchmaking-api/v1/matchmaking/server-attributes/{UNIVERSEID}"
```

### GET `/matchmaking-api/v1/matchmaking/universe/{universeId}/feature-flags` [BETA]

Gets feature flags for a customized matchmaking for a given universe.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.matchmaking-configuration:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |

**Responses:**

- `200`: OK → `GetMatchmakingCustomizationFeatureFlagsResponse`

**Response fields** (`GetMatchmakingCustomizationFeatureFlagsResponse`)

See [GetMatchmakingCustomizationFeatureFlagsResponse](#getmatchmakingcustomizationfeatureflagsresponse) in Models.

**Response example:**
```json
{
  "featureFlags": {
    "isMatchmakingCustomizationAllowed": false,
    "isMatchmakingCustomizationExperimentsAllowed": false,
    "isMatchmakingTextChatSignalEnabled": false
  }
}
```

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/matchmaking-api/v1/matchmaking/universe/{UNIVERSEID}/feature-flags"
```

### GET `/matchmaking-api/v1/matchmaking/universe/{universeId}/start-place` [BETA]

Gets the start place override for a universe.

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |

**Responses:**

- `200`: OK → `GetStartPlaceOverrideResponse`

**Response fields** (`GetStartPlaceOverrideResponse`)

See [GetStartPlaceOverrideResponse](#getstartplaceoverrideresponse) in Models.

**Response example:**
```json
{
  "dataStoreLocation": {
    "dataStoreName": "string",
    "scope": "string",
    "keyTemplate": "string",
    "valuePath": "string"
  },
  "enabled": false
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://apis.roblox.com/matchmaking-api/v1/matchmaking/universe/{UNIVERSEID}/start-place"
```

### POST `/matchmaking-api/v1/matchmaking/universe/{universeId}/start-place` [BETA]

Sets (creates or updates) the start place override for a universe.

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |

**Request Body:** `application/json-patch+json` — Type: `SetStartPlaceOverrideRequestBody`

See [SetStartPlaceOverrideRequestBody](#setstartplaceoverriderequestbody) in Models.

**Request example:**
```json
{
  "dataStoreLocation": {
    "dataStoreName": "string",
    "scope": "string",
    "keyTemplate": "string",
    "valuePath": "string"
  }
}
```

**Responses:**

- `200`: OK → `SetStartPlaceOverrideResponse`

**Response fields** (`SetStartPlaceOverrideResponse`)

See [SetStartPlaceOverrideResponse](#setstartplaceoverrideresponse) in Models.

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://apis.roblox.com/matchmaking-api/v1/matchmaking/universe/{UNIVERSEID}/start-place" \
  -H "Content-Type: application/json" \
  -d '{
  "dataStoreLocation": {
    "dataStoreName": "string",
    "scope": "string",
    "keyTemplate": "string",
    "valuePath": "string"
  }
}'
```

### DELETE `/matchmaking-api/v1/matchmaking/universe/{universeId}/start-place` [BETA]

Deletes the start place override for a universe.

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |

**Responses:**

- `200`: OK → `DeleteStartPlaceOverrideResponse`

**Response fields** (`DeleteStartPlaceOverrideResponse`)

See [DeleteStartPlaceOverrideResponse](#deletestartplaceoverrideresponse) in Models.

**Example:**
```bash
curl -X DELETE -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://apis.roblox.com/matchmaking-api/v1/matchmaking/universe/{UNIVERSEID}/start-place"
```

### GET `/matchmaking-api/v1/matchmaking/universe/{universeId}/start-place/test` [BETA]

Tests a user's saved start place in a universe against the place checks gamejoin makes.

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |
| `userId` | query | `integer` | No |  |

**Responses:**

- `200`: OK → `TestStartPlaceOverrideResponse`

**Response fields** (`TestStartPlaceOverrideResponse`)

See [TestStartPlaceOverrideResponse](#teststartplaceoverrideresponse) in Models.

**Response example:**
```json
{
  "result": "Invalid",
  "placeId": 0,
  "savedValue": "string"
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://apis.roblox.com/matchmaking-api/v1/matchmaking/universe/{UNIVERSEID}/start-place/test"
```

## Models

### ClientStatusGetRequest

Get Client Status request.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `browserTrackerId` | `integer` | No | The client's browser tracker id. |

### ClientStatusSetRequest

Set Client Status request.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `status` | `string` | No | The client's status to send. |
| `browserTrackerId` | `integer` | No | The client's browser tracker id. |

### ForecastUpdateRequest

ForecastUpdateRequest is used to request an update to the forecast of a Place in a Universe.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `universeId` | `integer` | No | The Universe ID to update. |

### ForecastUpdateResponse

ForecastUpdateResponse is used to return information about the forecasted update of a place.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `placeSummaries` | `PlaceSummaryForGameUpdate[]` | Yes |  |

### GetUpdateStatusResponse

Get Update Status response.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `updateStatusList` | `GameUpdateStatus[]` | Yes | The status of the game update. |

### LaunchUpdateRequest

Launch Update Request. Contains specification for how update should roll out

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `universeId` | `integer` | No | The Universe ID to update. |
| `placeIds` | `integer[]` | No | The place IDs to update. If none are specified, we will update all active Places in the Universe |
| `closeOldVersionsOnly` | `boolean` | No | If true (default in UI), we will only migrate players from servers running old PlaceVersions. If false, we will migrate all players |
| `bleedOffServers` | `boolean` | No | If true (default in UI), we will stop matchmaking to servers but keep them up before shutting them down, allowing  players to naturally migrate to the newer version. If false, we will immediately start shutting down servers |
| `bleedOffDurationMinutes` | `integer` | No | If BleedOffServers=true, how long will we allow old servers to stay up before shutting them down. Valid values: 1 - 60 minutes |
| `placeIdToVersions` | `object` | No | Optional. A mapping of PlaceId to the specific versions to restart/bleed off for that place. When set for a place, only servers running those exact versions will be affected. If a place is not in this dictionary or has an empty set, behavior falls back to CloseOldVersionsOnly logic. |
| `attributes` | `string` | No | Optional. Attributes string to include in the ServerLifecycleChanged CSM payload published to game servers. |

### LaunchUpdateResponse

Launch Update response.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `updateId` | `string` | Yes | An ID for UI to query status of this update |
| `numPlayersToBeKicked` | `integer` | Yes | How many players are playing in servers that will be shut down according to the update configuration |
| `instancesToBeClosed` | `integer` | Yes | How many game instances will be closed according to the update configuration |

### ShutdownGameInstancesRequest

Shutdown Game Instance request.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `placeId` | `integer` | No | The place ID to shut down. |
| `privateServerId` | `integer` | No | The private server ID. |
| `gameId` | `string` | No | The game ID. |

### ShutdownGameInstancesResponse

Shutdown Game Instance response.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `placeId` | `integer` | No | The place ID to shut down. |
| `privateServerId` | `integer` | No | The private server ID. |
| `gameId` | `string` | No | The game ID. |

### CreateMatchmakingPlayerAttributeDefinitionRequest

Request to create a new MatchmakingPlayerAttributeDefinition.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `universeId` | `integer` | No | UniverseId for the new PlayerAttributeDefinition. |
| `name` | `string` | No | Name of the new rule. |
| `dataType` | `MatchmakingAttributeDataType` | No |  |
| `defaultValue` | `MatchmakingAttributeValue` | No |  |
| `attributeValueLocation` | `MatchmakingAttributeValueLocation` | No |  |

### CreateMatchmakingPlayerAttributeDefinitionResponse

The response for creating a matchmaking player attribute definition.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `playerAttributeDefinition` | `MatchmakingPlayerAttributeDefinition` | Yes |  |

### UpdateMatchmakingPlayerAttributeDefinitionRequest

Request model for updating a PlayerAttributeDefinition.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `attributeId` | `string` | No | Id of the attribute to update. |
| `defaultValue` | `MatchmakingAttributeValue` | No |  |
| `attributeValueLocation` | `MatchmakingAttributeValueLocation` | No |  |

### UpdateMatchmakingPlayerAttributeDefinitionResponse

The response for updating a matchmaking player attribute definition.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `playerAttributeDefinition` | `MatchmakingPlayerAttributeDefinition` | Yes |  |

### ListMatchmakingPlayerAttributeDefinitionsResponse

The response for listing matchmaking player attribute definitions.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `playerAttributeSchema` | `MatchmakingPlayerAttributeDefinition[]` | No | All PlayerAttributeDefinitions for a universe. |

### CreateMatchmakingScoringConfigurationRequest

Request to create a matchmaking scoring configuration.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `universeId` | `integer` | No | UniverseId for the new matchmaking scoring configuraiton. |
| `name` | `string` | No | Name of the scoring configuration. |
| `matchmakingSignalWeights` | `object` | No | The desired set of weights for each matchmaking signal. |
| `customSignalWeights` | `object` | No | The desired set of weights for custom signals. It is a map from custom signal name to its weight. |
| `template` | `MatchmakingScoringConfigurationTemplate` | No |  |

### CreateMatchmakingScoringConfigurationResponse

Response to create a matchmaking scoring configuration.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `scoringConfiguration` | `MatchmakingScoringConfiguration` | Yes |  |

### GetMatchmakingScoringDefaultWeightsResponse

Response containing the weights of the current default matchmaking scoring weights

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `weights` | `object` | Yes | The weights of the current default matchmaking scoring weights. |

### GenerateMockServerSignalValuesResponse

Response for generating mock server signal values.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `exampleGameSignalValues` | `MockServerSignalValues[]` | No | The mock server signal values. |

### SetPlaceMatchmakingScoringConfigurationRequest

Request to set the matchmaking scoring configuration for a place.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `placeId` | `integer` | No | The place ID of the desired scoring configuration to set. |
| `scoringConfigurationId` | `string` | No | The ID of the scoring configuration. |

### SetMatchmakingScoringConfigurationResponse

Response to set the matchmaking scoring configuration.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `scoringConfiguration` | `MatchmakingScoringConfiguration` | Yes |  |

### GetMatchmakingScoringConfigurationResponse

Response to get the matchmaking scoring configuration.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `scoringConfiguration` | `MatchmakingScoringConfiguration` | Yes |  |

### UpdateMatchmakingScoringConfigurationRequest

Request to update a custom matchmaking signal.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `scoringConfigurationId` | `string` | No | The ID of the scoring configuration to be updated. |
| `name` | `string` | No | Name of the scoring configuration. |
| `matchmakingSignalWeights` | `object` | No | The desired set of weights for each matchmaking signal. |
| `customSignalWeights` | `object` | No | The desired set of weights for custom signals. It is a map from custom signal name to its weight. |

### UpdateMatchmakingScoringConfigurationResponse

Response to update a matchmaking scoring configuration.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `scoringConfiguration` | `MatchmakingScoringConfiguration` | Yes |  |

### CreateCustomMatchmakingSignalRequest

Request to create a custom matchmaking signal.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `scoringConfigurationId` | `string` | No | The ID of the scoring configuration that has the signal to be created. |
| `signalConfiguration` | `CustomSignalConfiguration` | No |  |

### CreateCustomMatchmakingSignalResponse

Response to create a custom matchmaking signal.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `scoringConfiguration` | `MatchmakingScoringConfiguration` | Yes |  |

### UpdateCustomMatchmakingSignalRequest

Request to update a custom matchmaking signal.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `scoringConfigurationId` | `string` | No | The ID of the scoring configuration. |
| `signalConfiguration` | `CustomSignalConfiguration` | No |  |

### UpdateCustomMatchmakingSignalResponse

Response to update a custom matchmaking signal.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `scoringConfiguration` | `MatchmakingScoringConfiguration` | Yes |  |

### DeleteCustomMatchmakingSignalResponse

Response to delete a custom matchmaking signal.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `scoringConfiguration` | `MatchmakingScoringConfiguration` | Yes |  |

### ListMatchmakingScoringConfigurationsResponse

Response to list matchmaking scoring configurations in a universe.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `scoringConfigurations` | `MatchmakingScoringConfiguration[]` | Yes | The scoring configurations. |

### ListPlaceMatchmakingScoringConfigurationsResponse

Response to list all places with scoring configuration in a universe.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `placeScoringConfigurations` | `object` | Yes | The scoring configurations for places. |

### CreateMatchmakingServerAttributeDefinitionRequest

Request to create a new ServerAttributeDefinition.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `universeId` | `integer` | No | UniverseId for the new PlayerAttributeDefinition. |
| `name` | `string` | No | Name of the new rule. |
| `dataType` | `MatchmakingAttributeDataType` | No |  |
| `defaultValue` | `MatchmakingServerAttributeDefaultValue` | No |  |

### CreateMatchmakingServerAttributeDefinitionResponse

The response for creating a matchmaking server attribute definition.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `playerAttributeDefinition` | `MatchmakingServerAttributeDefinition` | Yes |  |

### UpdateMatchmakingServerAttributeDefinitionRequest

Request model to update an exising ServerAttributeDefinition.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `attributeId` | `string` | No | Id of the attribute to update. |
| `defaultValue` | `MatchmakingServerAttributeDefaultValue` | No |  |

### UpdateMatchmakingServerAttributeDefinitionResponse

The response for updating a matchmaking server attribute definition.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `playerAttributeDefinition` | `MatchmakingServerAttributeDefinition` | Yes |  |

### ListMatchmakingServerAttributeDefinitionsResponse

The response for listing matchmaking server attribute definitions.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `serverAttributeSchema` | `MatchmakingServerAttributeDefinition[]` | No | All ServerAttributeDefinitions for a universe. |

### GetMatchmakingCustomizationFeatureFlagsResponse

Response to get matchmaking customization feature flags.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `featureFlags` | `MatchmakingCustomizationFeatureFlags` | Yes |  |

### GetStartPlaceOverrideResponse

Response for getting the start place override for a universe.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `dataStoreLocation` | `DataStoreLocation` | No |  |
| `enabled` | `boolean` | No | Whether game join routes players with the universe's start place override. Null when no start place override is configured for the universe. |

### SetStartPlaceOverrideRequestBody

Request body for setting the start place override for a universe. The universe is
identified by the route, so it is not part of the body.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `dataStoreLocation` | `DataStoreLocation` | No |  |

### TestStartPlaceOverrideResponse

Response for testing a user's saved start place in a universe.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `result` | `StartPlaceOverrideTestResult` | No |  |
| `placeId` | `integer` | No | The place id read from the user's data store entry. Null when no place id could be read. |
| `savedValue` | `string` | No | The value read at the configured value path of the user's data store entry, as JSON text, so a place id saved as text keeps its quotes. Cut to at most 100 characters. Null when no value could be read. |

### StartPlaceOverrideTestResult

Whether a user's saved start place passed every check, and if not, why.

Values: `Invalid`, `Found`, `NoOverrideConfigured`, `DataStoreEntryNotFound`, `DataStoreNotFound`, `DataStoreError`, `FieldMissing`, `ValueParseFailure`, `PlaceNotInExperience`, `PlaceNotPublished`, `UserNotFound`

### DataStoreLocation

Describes where an attribute value exists in DataStore.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `dataStoreName` | `string` | No | The DataStore name. |
| `scope` | `string` | No | The scope of the key in DataStore. |
| `keyTemplate` | `string` | No | The key of a DataStore value, with {UserId} replaced by the player's actual ID when fetching values. |
| `valuePath` | `string` | No | A JSON path to a value if it lives in a JSON object. |

### MatchmakingCustomizationFeatureFlags

Matchmaking object for universe feature flags controlling matchmaking customization.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `isMatchmakingCustomizationAllowed` | `boolean` | Yes | If matchmaking customization is allowed for this universe |
| `isMatchmakingCustomizationExperimentsAllowed` | `boolean` | Yes | If matchmaking customization experiments are allowed for this universe |
| `isMatchmakingTextChatSignalEnabled` | `boolean` | Yes | Whether text chat signal is enabled for Custom Matchmaking. |

### MatchmakingServerAttributeDefinition

Describes a player attribute definition for matchmaking.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `string` | Yes | The id of the attribute. |
| `universeId` | `integer` | No | The universe id of the attribute. |
| `name` | `string` | Yes | The name of the attribute. |
| `dataType` | `MatchmakingAttributeDataType` | No |  |
| `defaultValue` | `MatchmakingServerAttributeDefaultValue` | No |  |
| `createdTime` | `string` | No | The aggregation function of the attribute. |
| `updatedTime` | `string` | No | The time the attribute was last updated. |

### MatchmakingAttributeDataType

Data type of a matchmaking attribute. Can be a bool, number, or string.

Values: `Invalid`, `Bool`, `Number`, `String`

### MatchmakingServerAttributeDefaultValue

Describes how the server attribute value should be derived

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `sourceCase` | `MatchmakingServerAttributeDefaultValueSourceCase` | No |  |
| `constant` | `MatchmakingAttributeValue` | No |  |
| `playerAttributeReference` | `MatchmakingAttributeReference` | No |  |

### MatchmakingServerAttributeDefaultValueSourceCase

The storage solution used for this MatchmakingPlayerAttributeDefinition.

Values: `Invalid`, `Constant`, `PlayerAttributeReference`

### MatchmakingAttributeValue

Matchmaking attribute value object for matchmaking rules.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `boolValue` | `boolean` | No | Bool value of the attribute. One of BoolValue, NumericValue, or StringValue must be set. |
| `numericValue` | `number` | No | Double value of the attribute. One of BoolValue, NumericValue, or StringValue must be set. |
| `stringValue` | `string` | No | String value of the attribute. One of BoolValue, NumericValue, or StringValue must be set. |
| `type` | `MatchmakingAttributeValueType` | No |  |

### MatchmakingAttributeReference

Matchmaking attribute reference object for matchmaking rules.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `string` | No | The id of the attribute. |

### MatchmakingAttributeValueType

Matchmaking attribute value type.

Values: `Invalid`, `Bool`, `Number`, `String`

### MatchmakingScoringConfiguration

The custom scoring configuration for matchmaking.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `string` | Yes | The id of the scoring configuration. |
| `name` | `string` | Yes | The name of the scoring configuration. It needs to be unique within a universe. |
| `signalWeights` | `object` | Yes | The signal weights for the scoring configuration. |
| `customSignals` | `object` | Yes | The custom signals part of this place's scoring configuration. |
| `createdTime` | `string` | Yes | The scoring configuration's created time. |
| `updatedTime` | `string` | Yes | The scoring configuration's updated time. |

### MatchmakingSignalWeightConfiguration

The signal weight configuration for matchmaking.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `weight` | `number` | Yes | Weight of signal. |
| `signalType` | `MatchmakingSignalType` | Yes |  |

### CustomSignalConfiguration

The custom signal configuration using a developer created attribute.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `name` | `string` | No | The name of the signal. |
| `weight` | `number` | No | The weight of the signal. |
| `customSignalType` | `CustomSignalType` | No |  |
| `playerCategoricalSignalConfiguration` | `PlayerCategoricalSignalConfiguration` | No |  |
| `serverCategoricalSignalConfiguration` | `ServerCategoricalSignalConfiguration` | No |  |
| `serverNumericalSignalConfiguration` | `ServerNumericalSignalConfiguration` | No |  |
| `playerNumericalSignalConfiguration` | `PlayerNumericalSignalConfiguration` | No |  |
| `description` | `string` | No | A text description of the custom signal. |

### CustomSignalType

The custom signal type.

Values: `Invalid`, `PlayerCategorical`, `ServerCategorical`, `ServerNumerical`, `PlayerNumerical`

### PlayerCategoricalSignalConfiguration

The player categorical signal configuration.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `playerAttribute` | `MatchmakingAttributeReference` | No |  |
| `curveType` | `MatchmakingSignalCurveType` | No |  |

### ServerCategoricalSignalConfiguration

The server categorical signal configuration.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `serverAttribute` | `MatchmakingAttributeReference` | No |  |
| `comparisonType` | `MatchmakingCategoricalAttributeComparisonType` | No |  |
| `playerAttribute` | `MatchmakingAttributeReference` | No |  |
| `constantValue` | `string` | No | The constant value for this signal to be compared to. |

### ServerNumericalSignalConfiguration

The server numerical signal configuration.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `serverAttribute` | `MatchmakingAttributeReference` | No |  |
| `comparisonType` | `MatchmakingNumericalAttributeComparisonType` | No |  |
| `maxRelevantDifference` | `number` | No | The maximum relevant difference for this signal. |
| `constantValue` | `number` | No | The constant value for this signal to be compared to. |
| `playerAttribute` | `MatchmakingAttributeReference` | No |  |

### PlayerNumericalSignalConfiguration

The player numerical signal configuration.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `playerAttribute` | `MatchmakingAttributeReference` | No |  |
| `aggregation` | `MatchmakingAttributeAggregation` | No |  |
| `comparisonType` | `MatchmakingNumericalAttributeComparisonType` | No |  |
| `maxRelevantDifference` | `number` | No | The maximum relevant difference for this signal. |
| `constantValue` | `number` | No | The constant value for this signal to be compared to. |

### MatchmakingAttributeAggregation

Matchmaking attribute aggregation object for matchmaking rules.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `aggregationFunction` | `AttributeAggregationFunction` | No |  |

### MatchmakingNumericalAttributeComparisonType

The numerical attribute comparison type for matchmaking.

Values: `Invalid`, `AbsoluteDifferentToPlayer`, `AbsoluteDifferentToConstant`

### AttributeAggregationFunction

Matchmaking attribute aggregation function type.

Values: `Invalid`, `Average`, `Median`, `Sum`

### MatchmakingCategoricalAttributeComparisonType

The categorical attribute comparison type for matchmaking.

Values: `Invalid`, `EqualityToPlayer`, `EqualityToConstant`

### MatchmakingSignalCurveType

The signal curve type for matchmaking.

Values: `Invalid`, `PositiveLinear`, `NegativeLinear`

### MatchmakingSignalType

The default signal types matchmaking uses.

Values: `Invalid`, `Occupancy`, `Age`, `Language`, `Latency`, `PreferredPlayers`, `VoiceChat`, `DeviceType`, `PlayHistory`, `TextChat`

### MockServerSignalValues

Mock server signal values.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `capacity` | `integer` | No | The capacity of the mock server. |
| `occupancy` | `integer` | No | The occupancy of the mock server. |
| `hasPreferredPlayers` | `boolean` | No | If the game has preferred players. |
| `playerAge` | `integer` | No | The joining player's age. |
| `serverAveragePlayerAge` | `integer` | No | The server's age for the mock server. |
| `commonLanguagePlayers` | `integer` | No | The number of player's in the mock server that have a common language. |
| `latency` | `integer` | No | The latency of the mock server. |
| `commonDevicePlayers` | `integer` | No | The number of player's in the mock server that have a common device. |
| `playerPlayHistory` | `number` | No | The joining player's play history. The value is a log10 transformation of the player's playtime in minutes during last 28 days. |
| `serverAveragePlayHistory` | `number` | No | The server's play history for the mock server. |
| `commonVoicePlayers` | `integer` | No | The number of player's in the mock server that have voice chat enabled. |
| `commonTextChatPlayers` | `integer` | No | The number of player's in the mock server that can commonly text chat with the joining player. |

### MatchmakingScoringConfigurationTemplate

A predefined template used for creating matchmaking scoring configuration.

Values: `NotApplicable`, `UseDefault`

### MatchmakingPlayerAttributeDefinition

Describes a player attribute definition for matchmaking.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `string` | Yes | The id of the attribute. |
| `universeId` | `integer` | No | The universe id of the attribute. |
| `name` | `string` | Yes | The name of the attribute. |
| `dataType` | `MatchmakingAttributeDataType` | No |  |
| `defaultValue` | `MatchmakingAttributeValue` | No |  |
| `attributeValueLocation` | `MatchmakingAttributeValueLocation` | Yes |  |
| `createdTime` | `string` | No | The aggregation function of the attribute. |
| `updatedTime` | `string` | No | The time the attribute was last updated. |

### MatchmakingAttributeValueLocation

Describes where an attribute value exists.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `locationCase` | `MatchmakingAttributeValueLocationCase` | No |  |
| `dataStoreLocation` | `DataStoreLocation` | No |  |

### MatchmakingAttributeValueLocationCase

The storage solution used for this MatchmakingPlayerAttributeDefinition.

Values: `Invalid`, `DataStoreLocation`

### GameUpdateStatus

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `string` | Yes |  |
| `universeId` | `integer` | Yes |  |
| `startTime` | `string` | Yes |  |
| `closeOldVersionsOnly` | `boolean` | Yes |  |
| `bleedOffEndTime` | `string` | Yes |  |
| `placeUpdateStatuses` | `object` | Yes |  |
| `bleedOffServers` | `boolean` | Yes |  |

### PlaceUpdateStatus

Container for the status of a game update.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `placeId` | `integer` | Yes | The placeId of the game update |
| `phase` | `string` | Yes | Which phase is the update in: BleedOff, Migrate, or Done |
| `startTime` | `string` | Yes | When the update started |
| `endTime` | `string` | No | When the update is expected to end, or null if it has not ended yet |
| `startPlayersToBeKicked` | `integer` | Yes | Number of players in the game update initially, before any players are kicked |
| `startInstancesToBeClosed` | `integer` | Yes | Number of instances that will be closed during the game update |
| `numPlayersToBeKicked` | `integer` | Yes | How many players are remaining in instances that will be shut down according to the update configuration |
| `instancesToBeClosed` | `integer` | Yes | Number of places that will be updated |
| `placeVersion` | `integer` | Yes | The version of the place that is being updated |
| `placeVersionsToBeClosed` | `integer[]` | No | The versions of the place that will be closed during the update |

### PlaceSummaryForGameUpdate

Summary of a place for a game update.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `placeId` | `integer` | No | Place ID of the place to be updated. |
| `playersToBeKicked` | `integer` | No | Number of players to be kicked from the place during the game update. |
| `totalPlayers` | `integer` | No | Total number of players in the place. |
| `instancesToBeClosed` | `integer` | No | Number of instances to be closed for the place during the game update. |
| `totalInstances` | `integer` | No | Total number of instances for the place. |
| `placeVersion` | `integer` | No | Lastest version of the place to be updated. |
| `lastUpdated` | `string` | No | The timestamp of the last update to the place summary. |
| `isInUniverse` | `boolean` | No | Indicates whether the place is still part of the universe. A place may have active games but is no longer in the universe if it has been removed from the universe. |
| `versionToPlayerCounts` | `object` | No | Player counts broken down by place version. Key is the place version, value is the number of players on that version. |
| `versionToInstanceCounts` | `object` | No | Instance counts broken down by place version. Key is the place version, value is the number of instances on that version. |