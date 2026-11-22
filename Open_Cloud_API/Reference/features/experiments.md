<!-- Source: https://create.roblox.com/docs/cloud/reference/features/experiments.md -->

---
name: "Experiments"
last_updated: 2026-11-20T18:47:47Z
type: feature
api_base_url: "https://apis.roblox.com"
endpoints: 11
auth: [api-key, oauth2, cookie]
description: "Manage and analyze experiments for your experiences programmatically"
---

# Experiments

Manage and analyze experiments for your experiences programmatically. See the [Experiments guide](https://create.roblox.com/docs/production/experiments) for setup and usage.

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

### GET `/creator-configs-public-api/v1/experimentation/universes/{universeId}/experiments` [EXPERIMENTAL]

Lists experiments for a universe.

Pagination is offset-based (`maxPageSize` + `skip`). The response carries the page slice plus the unpaginated total
matching the filters. Request includes optional pagination, search, and filters.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |
| `maxPageSize` | query | `integer` | No |  |
| `skip` | query | `integer` | No |  |
| `searchKey` | query | `string` | No |  |
| `stateFilters` | query | `ExperimentState[]` | No | Valid values: `EXPERIMENT_STATE_DRAFT`, `EXPERIMENT_STATE_SCHEDULED`, `EXPERIMENT_STATE_RUNNING`, `EXPERIMENT_STATE_COMPLETED`, `EXPERIMENT_STATE_CANCELLED`, `EXPERIMENT_STATE_DELETED` |
| `sortOrder` | query | `CreatorConfigsPublicApi.SortOrder` | No | SORT_ORDER_ASCENDING  SORT_ORDER_DESCENDING Valid values: `SORT_ORDER_ASCENDING`, `SORT_ORDER_DESCENDING` |
| `sortKey` | query | `ListExperimentSortKey` | No | LIST_EXPERIMENT_SORT_KEY_NAME  LIST_EXPERIMENT_SORT_KEY_LAST_MODIFIED_TIME  LIST_EXPERIMENT_SORT_KEY_START_TIME  LIST_EXPERIMENT_SORT_KEY_RELEVANCE Valid values: `LIST_EXPERIMENT_SORT_KEY_NAME`, `LIST_EXPERIMENT_SORT_KEY_LAST_MODIFIED_TIME`, `LIST_EXPERIMENT_SORT_KEY_START_TIME`, `LIST_EXPERIMENT_SORT_KEY_RELEVANCE` |
| `productTypeFilter` | query | `ExperimentProductType` | No | EXPERIMENT_PRODUCT_TYPE_IN_GAME_CONFIGS  EXPERIMENT_PRODUCT_TYPE_MATCHMAKING Valid values: `EXPERIMENT_PRODUCT_TYPE_IN_GAME_CONFIGS`, `EXPERIMENT_PRODUCT_TYPE_MATCHMAKING` |

**Responses:**

- `200`: OK → `ListExperimentsResponse`
- `400`: Bad Request → `ActionResult`
- `401`: Unauthorized → `ActionResult`
- `404`: Not Found → `ActionResult`

**Response fields** (`ListExperimentsResponse`)

See [ListExperimentsResponse](#listexperimentsresponse) in Models.

**Response example:**
```json
{
  "experiments": [
    {
      "id": "...",
      "name": "...",
      "description": "...",
      "createdTime": "...",
      "lastUpdatedTime": "...",
      "startedTime": "..."
    }
  ],
  "total": 0
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/creator-configs-public-api/v1/experimentation/universes/{UNIVERSEID}/experiments"
```

### POST `/creator-configs-public-api/v1/experimentation/universes/{universeId}/experiments` [EXPERIMENTAL]

Creates a new experiment for a universe.

Returns an ExperimentOperation describing the async create call.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |

**Request Body:** `application/json-patch+json` — Type: `CreateExperimentData`

See [CreateExperimentData](#createexperimentdata) in Models.

**Request example:**
```json
{
  "name": "string",
  "description": "string",
  "experimentConfiguration": {
    "productType": "EXPERIMENT_PRODUCT_TYPE_IN_GAME_CONFIGS",
    "inGameConfigExperimentConfiguration": {
      "variants": "..."
    },
    "matchmakingExperimentConfiguration": {
      "variants": "..."
    }
  },
  "exposurePercent": 0,
  "targetingCriteria": {
    "rule": {
      "tokens": "..."
    }
  },
  "durationSeconds": 0
}
```

**Responses:**

- `200`: OK → `CreateExperimentResponse`
- `400`: Bad Request → `ActionResult`
- `401`: Unauthorized → `ActionResult`
- `404`: Not Found → `ActionResult`

**Response fields** (`CreateExperimentResponse`)

See [CreateExperimentResponse](#createexperimentresponse) in Models.

**Response example:**
```json
{
  "operation": {
    "operationId": "string",
    "status": "OPERATIONAL_STATUS_READY",
    "createdTime": "2024-01-01T00:00:00Z",
    "done": false,
    "error": {
      "errorType": "...",
      "errorCode": "...",
      "errorMessage": "...",
      "errorContext": "..."
    },
    "experiment": {
      "id": "...",
      "name": "...",
      "description": "...",
      "createdTime": "...",
      "lastUpdatedTime": "...",
      "startedTime": "..."
    }
  }
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 10/minute, perOauth2Authorization: 10/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/creator-configs-public-api/v1/experimentation/universes/{UNIVERSEID}/experiments" \
  -H "Content-Type: application/json" \
  -d '{"name":"string","description":"string","experimentConfiguration":{"productType":"EXPERIMENT_PRODUCT_TYPE_IN_GAME_CONFIGS","inGameConfigExperimentConfiguration":{"variants":"..."},"matchmakingExperimentConfiguration":{"variants":"..."}},"exposurePercent":0,"targetingCriteria":{"rule":{"tokens":"..."}},"durationSeconds":0}'
```

### GET `/creator-configs-public-api/v1/experimentation/universes/{universeId}/experiments/{experimentId}` [EXPERIMENTAL]

Gets an experiment by ID.

Returns the `experiment`. Returns 404 if the experiment doesn't exist for the universe.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |
| `experimentId` | path | `string` | Yes |  |

**Responses:**

- `200`: OK → `GetExperimentResponse`
- `400`: Bad Request → `ActionResult`
- `401`: Unauthorized → `ActionResult`
- `404`: Not Found → `ActionResult`

**Response fields** (`GetExperimentResponse`)

See [GetExperimentResponse](#getexperimentresponse) in Models.

**Response example:**
```json
{
  "experiment": {
    "id": "string",
    "name": "string",
    "description": "string",
    "createdTime": "2024-01-01T00:00:00Z",
    "lastUpdatedTime": "2024-01-01T00:00:00Z",
    "startedTime": "2024-01-01T00:00:00Z"
  }
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/creator-configs-public-api/v1/experimentation/universes/{UNIVERSEID}/experiments/{EXPERIMENTID}"
```

### PATCH `/creator-configs-public-api/v1/experimentation/universes/{universeId}/experiments/{experimentId}` [EXPERIMENTAL]

Updates an existing experiment.

The payload is a full replacement of the mutable experiment fields. Returns an
ExperimentOperation describing the async update.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |
| `experimentId` | path | `string` | Yes |  |

**Request Body:** `application/json-patch+json` — Type: `UpdateExperimentData`

See [UpdateExperimentData](#updateexperimentdata) in Models.

**Request example:**
```json
{
  "name": "string",
  "description": "string",
  "experimentConfiguration": {
    "productType": "EXPERIMENT_PRODUCT_TYPE_IN_GAME_CONFIGS",
    "inGameConfigExperimentConfiguration": {
      "variants": "..."
    },
    "matchmakingExperimentConfiguration": {
      "variants": "..."
    }
  },
  "exposurePercent": 0,
  "targetingCriteria": {
    "rule": {
      "tokens": "..."
    }
  },
  "durationSeconds": 0
}
```

**Responses:**

- `200`: OK → `UpdateExperimentResponse`
- `400`: Bad Request → `ActionResult`
- `401`: Unauthorized → `ActionResult`
- `404`: Not Found → `ActionResult`

**Response fields** (`UpdateExperimentResponse`)

See [UpdateExperimentResponse](#updateexperimentresponse) in Models.

**Response example:**
```json
{
  "operation": {
    "operationId": "string",
    "status": "OPERATIONAL_STATUS_READY",
    "createdTime": "2024-01-01T00:00:00Z",
    "done": false,
    "error": {
      "errorType": "...",
      "errorCode": "...",
      "errorMessage": "...",
      "errorContext": "..."
    },
    "experiment": {
      "id": "...",
      "name": "...",
      "description": "...",
      "createdTime": "...",
      "lastUpdatedTime": "...",
      "startedTime": "..."
    }
  }
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 10/minute, perOauth2Authorization: 10/minute

**Example:**
```bash
curl -X PATCH -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/creator-configs-public-api/v1/experimentation/universes/{UNIVERSEID}/experiments/{EXPERIMENTID}" \
  -H "Content-Type: application/json" \
  -d '{"name":"string","description":"string","experimentConfiguration":{"productType":"EXPERIMENT_PRODUCT_TYPE_IN_GAME_CONFIGS","inGameConfigExperimentConfiguration":{"variants":"..."},"matchmakingExperimentConfiguration":{"variants":"..."}},"exposurePercent":0,"targetingCriteria":{"rule":{"tokens":"..."}},"durationSeconds":0}'
```

### DELETE `/creator-configs-public-api/v1/experimentation/universes/{universeId}/experiments/{experimentId}` [EXPERIMENTAL]

Discards an experiment.

The experiment record is retained with state Deleted.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |
| `experimentId` | path | `string` | Yes |  |

**Responses:**

- `200`: OK → `DiscardExperimentResponse`
- `400`: Bad Request → `ActionResult`
- `401`: Unauthorized → `ActionResult`
- `404`: Not Found → `ActionResult`

**Response fields** (`DiscardExperimentResponse`)

See [DiscardExperimentResponse](#discardexperimentresponse) in Models.

**Response example:**
```json
{
  "operation": {
    "operationId": "string",
    "status": "OPERATIONAL_STATUS_READY",
    "createdTime": "2024-01-01T00:00:00Z",
    "done": false,
    "error": {
      "errorType": "...",
      "errorCode": "...",
      "errorMessage": "...",
      "errorContext": "..."
    },
    "experiment": {
      "id": "...",
      "name": "...",
      "description": "...",
      "createdTime": "...",
      "lastUpdatedTime": "...",
      "startedTime": "..."
    }
  }
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 10/minute, perOauth2Authorization: 10/minute

**Example:**
```bash
curl -X DELETE -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/creator-configs-public-api/v1/experimentation/universes/{UNIVERSEID}/experiments/{EXPERIMENTID}"
```

### GET `/creator-configs-public-api/v1/experimentation/universes/{universeId}/experiments/{experimentId}/stats` [EXPERIMENTAL]

Gets diagnostic stats for an experiment.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |
| `experimentId` | path | `string` | Yes |  |

**Responses:**

- `200`: OK → `GetExperimentStatsResponse`
- `400`: Bad Request → `ActionResult`
- `401`: Unauthorized → `ActionResult`
- `404`: Not Found → `ActionResult`

**Response fields** (`GetExperimentStatsResponse`)

See [GetExperimentStatsResponse](#getexperimentstatsresponse) in Models.

**Response example:**
```json
{
  "operation": {
    "experimentId": 0,
    "lastModifiedTime": "2024-01-01T00:00:00Z",
    "done": false,
    "error": {
      "errorType": "...",
      "errorCode": "...",
      "errorMessage": "...",
      "errorContext": "..."
    },
    "experimentStats": {
      "isSrmDetected": "..."
    }
  }
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/creator-configs-public-api/v1/experimentation/universes/{UNIVERSEID}/experiments/{EXPERIMENTID}/stats"
```

### POST `/creator-configs-public-api/v1/experimentation/universes/{universeId}/experiments/{experimentId}:complete` [EXPERIMENTAL]

Completes an experiment by stopping it and rolling out the requested variant.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |
| `experimentId` | path | `string` | Yes |  |

**Request Body:** `application/json-patch+json` — Type: `CompleteExperimentRequest`

See [CompleteExperimentRequest](#completeexperimentrequest) in Models.

**Request example:**
```json
{
  "variantId": "string"
}
```

**Responses:**

- `200`: OK → `CompleteExperimentResponse`
- `400`: Bad Request → `ActionResult`
- `401`: Unauthorized → `ActionResult`
- `404`: Not Found → `ActionResult`

**Response fields** (`CompleteExperimentResponse`)

See [CompleteExperimentResponse](#completeexperimentresponse) in Models.

**Response example:**
```json
{
  "operation": {
    "operationId": "string",
    "status": "OPERATIONAL_STATUS_READY",
    "createdTime": "2024-01-01T00:00:00Z",
    "done": false,
    "error": {
      "errorType": "...",
      "errorCode": "...",
      "errorMessage": "...",
      "errorContext": "..."
    },
    "experiment": {
      "id": "...",
      "name": "...",
      "description": "...",
      "createdTime": "...",
      "lastUpdatedTime": "...",
      "startedTime": "..."
    }
  }
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 10/minute, perOauth2Authorization: 10/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/creator-configs-public-api/v1/experimentation/universes/{UNIVERSEID}/experiments/{EXPERIMENTID}:complete" \
  -H "Content-Type: application/json" \
  -d '{
  "variantId": "string"
}'
```

### POST `/creator-configs-public-api/v1/experimentation/universes/{universeId}/experiments/{experimentId}:schedule` [EXPERIMENTAL]

Schedules an experiment to start at a future UTC time.

Body must include `scheduledStartTime` as an ISO-8601 UTC timestamp.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |
| `experimentId` | path | `string` | Yes |  |

**Request Body:** `application/json-patch+json` — Type: `ScheduleExperimentRequest`

See [ScheduleExperimentRequest](#scheduleexperimentrequest) in Models.

**Request example:**
```json
{
  "scheduledStartTime": "2024-01-01T00:00:00Z"
}
```

**Responses:**

- `200`: OK → `ScheduleExperimentResponse`
- `400`: Bad Request → `ActionResult`
- `401`: Unauthorized → `ActionResult`
- `404`: Not Found → `ActionResult`

**Response fields** (`ScheduleExperimentResponse`)

See [ScheduleExperimentResponse](#scheduleexperimentresponse) in Models.

**Response example:**
```json
{
  "operation": {
    "operationId": "string",
    "status": "OPERATIONAL_STATUS_READY",
    "createdTime": "2024-01-01T00:00:00Z",
    "done": false,
    "error": {
      "errorType": "...",
      "errorCode": "...",
      "errorMessage": "...",
      "errorContext": "..."
    },
    "experiment": {
      "id": "...",
      "name": "...",
      "description": "...",
      "createdTime": "...",
      "lastUpdatedTime": "...",
      "startedTime": "..."
    }
  }
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 10/minute, perOauth2Authorization: 10/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/creator-configs-public-api/v1/experimentation/universes/{UNIVERSEID}/experiments/{EXPERIMENTID}:schedule" \
  -H "Content-Type: application/json" \
  -d '{
  "scheduledStartTime": "2024-01-01T00:00:00Z"
}'
```

### POST `/creator-configs-public-api/v1/experimentation/universes/{universeId}/experiments/{experimentId}:start` [EXPERIMENTAL]

Starts an experiment immediately.

For a future-dated start, use the sibling `:schedule` endpoint.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |
| `experimentId` | path | `string` | Yes |  |

**Responses:**

- `200`: OK → `StartExperimentResponse`
- `400`: Bad Request → `ActionResult`
- `401`: Unauthorized → `ActionResult`
- `404`: Not Found → `ActionResult`

**Response fields** (`StartExperimentResponse`)

See [StartExperimentResponse](#startexperimentresponse) in Models.

**Response example:**
```json
{
  "operation": {
    "operationId": "string",
    "status": "OPERATIONAL_STATUS_READY",
    "createdTime": "2024-01-01T00:00:00Z",
    "done": false,
    "error": {
      "errorType": "...",
      "errorCode": "...",
      "errorMessage": "...",
      "errorContext": "..."
    },
    "experiment": {
      "id": "...",
      "name": "...",
      "description": "...",
      "createdTime": "...",
      "lastUpdatedTime": "...",
      "startedTime": "..."
    }
  }
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 10/minute, perOauth2Authorization: 10/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/creator-configs-public-api/v1/experimentation/universes/{UNIVERSEID}/experiments/{EXPERIMENTID}:start"
```

### POST `/creator-configs-public-api/v1/experimentation/universes/{universeId}/experiments:calculateMde` [EXPERIMENTAL]

Calculates the Minimum Detectable Effect (MDE) for a prospective experiment.

Poll by clients until the operation is complete.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |

**Request Body:** `application/json-patch+json` — Type: `CalculateExperimentMdeData`

See [CalculateExperimentMdeData](#calculateexperimentmdedata) in Models.

**Request example:**
```json
{
  "exposurePercent": 0,
  "durationSeconds": 0,
  "baselineWeight": 0,
  "variantWeights": [
    0
  ],
  "universeGoalMetric": "UNIVERSE_EXPERIMENT_METRIC_AVERAGE_SESSION_TIME",
  "targetingCriteria": {
    "rule": {
      "tokens": "..."
    }
  }
}
```

**Responses:**

- `200`: OK → `CalculateExperimentMdeResponse`
- `400`: Bad Request → `ActionResult`
- `401`: Unauthorized → `ActionResult`
- `404`: Not Found → `ActionResult`

**Response fields** (`CalculateExperimentMdeResponse`)

See [CalculateExperimentMdeResponse](#calculateexperimentmderesponse) in Models.

**Response example:**
```json
{
  "operation": {
    "operationId": "string",
    "lastModifiedTime": "2024-01-01T00:00:00Z",
    "done": false,
    "error": {
      "errorType": "...",
      "errorCode": "...",
      "errorMessage": "...",
      "errorContext": "..."
    },
    "mde": {
      "totalSampleSize": "...",
      "mdeRelativePercentages": "...",
      "minimumSampleSizeThreshold": "..."
    }
  }
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 10/minute, perOauth2Authorization: 10/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/creator-configs-public-api/v1/experimentation/universes/{UNIVERSEID}/experiments:calculateMde" \
  -H "Content-Type: application/json" \
  -d '{
  "exposurePercent": 0,
  "durationSeconds": 0,
  "baselineWeight": 0,
  "variantWeights": [
    0
  ],
  "universeGoalMetric": "UNIVERSE_EXPERIMENT_METRIC_AVERAGE_SESSION_TIME",
  "targetingCriteria": {
    "rule": {
      "tokens": "..."
    }
  }
}'
```

### GET `/creator-configs-public-api/v1/experimentation/universes/{universeId}/operations/{operationId}` [EXPERIMENTAL]

Gets the status of an experiment async operation.

Polled by clients between mutations (Create / Update / Start / Schedule /
Complete / Discard) to determine when the operation reaches `done = true`.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |
| `operationId` | path | `string` | Yes |  |

**Responses:**

- `200`: OK → `GetExperimentOperationStatusResponse`
- `400`: Bad Request → `ActionResult`
- `401`: Unauthorized → `ActionResult`
- `404`: Not Found → `ActionResult`

**Response fields** (`GetExperimentOperationStatusResponse`)

See [GetExperimentOperationStatusResponse](#getexperimentoperationstatusresponse) in Models.

**Response example:**
```json
{
  "operation": {
    "operationId": "string",
    "status": "OPERATIONAL_STATUS_READY",
    "createdTime": "2024-01-01T00:00:00Z",
    "done": false,
    "error": {
      "errorType": "...",
      "errorCode": "...",
      "errorMessage": "...",
      "errorContext": "..."
    },
    "experiment": {
      "id": "...",
      "name": "...",
      "description": "...",
      "createdTime": "...",
      "lastUpdatedTime": "...",
      "startedTime": "..."
    }
  }
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/creator-configs-public-api/v1/experimentation/universes/{UNIVERSEID}/operations/{OPERATIONID}"
```

## Models

### ExperimentState

Lifecycle state of an experiment.

EXPERIMENT_STATE_DRAFT

EXPERIMENT_STATE_SCHEDULED

EXPERIMENT_STATE_RUNNING

EXPERIMENT_STATE_COMPLETED

EXPERIMENT_STATE_CANCELLED

EXPERIMENT_STATE_DELETED

Values: `EXPERIMENT_STATE_DRAFT`, `EXPERIMENT_STATE_SCHEDULED`, `EXPERIMENT_STATE_RUNNING`, `EXPERIMENT_STATE_COMPLETED`, `EXPERIMENT_STATE_CANCELLED`, `EXPERIMENT_STATE_DELETED`

### CreatorConfigsPublicApi.SortOrder

Sort direction for list queries.

SORT_ORDER_ASCENDING

SORT_ORDER_DESCENDING

Values: `SORT_ORDER_ASCENDING`, `SORT_ORDER_DESCENDING`

### ListExperimentSortKey

Key to sort an experiment list by.

LIST_EXPERIMENT_SORT_KEY_NAME

LIST_EXPERIMENT_SORT_KEY_LAST_MODIFIED_TIME

LIST_EXPERIMENT_SORT_KEY_START_TIME

LIST_EXPERIMENT_SORT_KEY_RELEVANCE

Values: `LIST_EXPERIMENT_SORT_KEY_NAME`, `LIST_EXPERIMENT_SORT_KEY_LAST_MODIFIED_TIME`, `LIST_EXPERIMENT_SORT_KEY_START_TIME`, `LIST_EXPERIMENT_SORT_KEY_RELEVANCE`

### ExperimentProductType

Type of product the experiment is targeting.

EXPERIMENT_PRODUCT_TYPE_IN_GAME_CONFIGS

EXPERIMENT_PRODUCT_TYPE_MATCHMAKING

Values: `EXPERIMENT_PRODUCT_TYPE_IN_GAME_CONFIGS`, `EXPERIMENT_PRODUCT_TYPE_MATCHMAKING`

### ListExperimentsResponse

Response body for `GET /v1/experimentation/universes/{universeId}/experiments`.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `experiments` | `ExperimentSummary[]` | No | The page of experiments matching the query. |
| `total` | `integer` | No | Total number of experiments for the universe matching the filters             (independent of pagination). |

### CreateExperimentData

Request body for `POST /v1/experimentation/universes/{universeId}/experiments`.
Payload describing a new experiment.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `name` | `string` | No | Experiment display name. |
| `description` | `string` | No | Experiment description. |
| `experimentConfiguration` | `ExperimentConfiguration` | No | Experiment configuration (variants + product-type-specific data). |
| `exposurePercent` | `integer` | No | Exposure percent in range 0-100. Percent of eligible users seeing the experiment. |
| `targetingCriteria` | `TargetingCriteria` | No | Targeting criteria scoping which users are eligible for the experiment. |
| `durationSeconds` | `integer` | No | Experiment duration in whole seconds. |
| `universeGoalMetric` | `UniverseExperimentMetric` | No | Goal metric for the experiment.  UNIVERSE_EXPERIMENT_METRIC_AVERAGE_SESSION_TIME  UNIVERSE_EXPERIMENT_METRIC_PLAYTIME_PER_USER  UNIVERSE_EXPERIMENT_METRIC_DAY_1_RETENTION  UNIVERSE_EXPERIMENT_METRIC_DAY_7_RETENTION  UNIVERSE_EXPERIMENT_METRIC_PAYER_CONVERSION_RATE  UNIVERSE_EXPERIMENT_METRIC_AVERAGE_REVENUE_PER_USER  UNIVERSE_EXPERIMENT_METRIC_AVERAGE_REVENUE_PER_PAYING_USER |

### CreateExperimentResponse

Response body for POST /v1/universes/{universeId}/experiment.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `operation` | `ExperimentOperation` | No | Resulting async operation describing the create call. |

### GetExperimentResponse

Response body for GET /v1/universes/{universeId}/experiment/{experimentId}.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `experiment` | `ProductExperiment` | No | The requested experiment. |

### UpdateExperimentData

Request body for
`PATCH /v1/experimentation/universes/{universeId}/experiments/{experimentId}`.
Mirrors CreatorConfigsPublicApi.Models.Experimentation.CreateExperimentData; updating is modeled as a full replace of these fields.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `name` | `string` | No | Experiment display name. |
| `description` | `string` | No | Experiment description. |
| `experimentConfiguration` | `ExperimentConfiguration` | No | Experiment configuration (variants + product-type-specific data). |
| `exposurePercent` | `integer` | No | Exposure percent in range 0-100. |
| `targetingCriteria` | `TargetingCriteria` | No | Targeting criteria scoping which users are eligible for the experiment. |
| `durationSeconds` | `integer` | No | Experiment duration in whole seconds. |
| `universeGoalMetric` | `UniverseExperimentMetric` | No | Goal metric for the experiment.  UNIVERSE_EXPERIMENT_METRIC_AVERAGE_SESSION_TIME  UNIVERSE_EXPERIMENT_METRIC_PLAYTIME_PER_USER  UNIVERSE_EXPERIMENT_METRIC_DAY_1_RETENTION  UNIVERSE_EXPERIMENT_METRIC_DAY_7_RETENTION  UNIVERSE_EXPERIMENT_METRIC_PAYER_CONVERSION_RATE  UNIVERSE_EXPERIMENT_METRIC_AVERAGE_REVENUE_PER_USER  UNIVERSE_EXPERIMENT_METRIC_AVERAGE_REVENUE_PER_PAYING_USER |

### UpdateExperimentResponse

Response body for PATCH /v1/universes/{universeId}/experiment/{experimentId}.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `operation` | `ExperimentOperation` | No | Resulting async operation describing the update call. |

### DiscardExperimentResponse

Response body for DELETE /v1/universes/{universeId}/experiment/{experimentId}.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `operation` | `ExperimentOperation` | No | Resulting async operation describing the delete call. |

### GetExperimentStatsResponse

Response body for
`GET /v1/experimentation/universes/{universeId}/experiments/{experimentId}/stats`.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `operation` | `ExperimentStatsOperation` | No | The async operation containing the experiment stats. |

### CompleteExperimentRequest

Request body for
`POST /v1/experimentation/universes/{universeId}/experiments/{experimentId}:complete`.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `variantId` | `string` | No | ID of the variant to roll out as the winning variant. If omitted, the experiment is stopped without rolling out a winner. |

### CompleteExperimentResponse

Response body for
`POST /v1/experimentation/universes/{universeId}/experiments/{experimentId}:complete`.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `operation` | `ExperimentOperation` | No | The async operation that completed the experiment. |

### ScheduleExperimentRequest

Request body for
`POST /v1/experimentation/universes/{universeId}/experiments/{experimentId}:schedule`.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `scheduledStartTime` | `string` | No | UTC time at which the experiment should be auto-started. |

### ScheduleExperimentResponse

Response body for
`POST /v1/experimentation/universes/{universeId}/experiments/{experimentId}:schedule`.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `operation` | `ExperimentOperation` | No | The async operation that scheduled the experiment. |

### StartExperimentResponse

Response body for
`POST /v1/experimentation/universes/{universeId}/experiments/{experimentId}:start`.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `operation` | `ExperimentOperation` | No | The async operation that started the experiment. |

### CalculateExperimentMdeData

Request body for
`POST /v1/experimentation/universes/{universeId}/experiments:calculateMde`.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `exposurePercent` | `integer` | No | Exposure percent in range 0-100. Percent of eligible users seeing the experiment. |
| `durationSeconds` | `integer` | No | Planned duration of the experiment in whole seconds. Values must be an exact multiple of `86400`. |
| `baselineWeight` | `number` | No | Relative weight (in [0, 100]) for the baseline (control) variant. |
| `variantWeights` | `number[]` | No | Relative weights (each in [0, 100]) for each non-baseline variant. |
| `universeGoalMetric` | `UniverseExperimentMetric` | No | The goal metric whose detectable effect is being calculated.  UNIVERSE_EXPERIMENT_METRIC_AVERAGE_SESSION_TIME  UNIVERSE_EXPERIMENT_METRIC_PLAYTIME_PER_USER  UNIVERSE_EXPERIMENT_METRIC_DAY_1_RETENTION  UNIVERSE_EXPERIMENT_METRIC_DAY_7_RETENTION  UNIVERSE_EXPERIMENT_METRIC_PAYER_CONVERSION_RATE  UNIVERSE_EXPERIMENT_METRIC_AVERAGE_REVENUE_PER_USER  UNIVERSE_EXPERIMENT_METRIC_AVERAGE_REVENUE_PER_PAYING_USER |
| `targetingCriteria` | `TargetingCriteria` | No | Targeting criteria used to scope the analytics window. |

### CalculateExperimentMdeResponse

Response body for
`POST /v1/experimentation/universes/{universeId}/experiments:calculateMde`.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `operation` | `MdeOperation` | No | The MDE async operation. |

### GetExperimentOperationStatusResponse

Response body for
`GET /v1/experimentation/universes/{universeId}/operations/{operationId}`.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `operation` | `ExperimentOperation` | No | The current state of the async operation. |

### ExperimentOperation

Async operation result for an experiment Create / Update / Discard call. When
Done is true, at most one of Error or Experiment is set; when false, neither is. A successful delete is the
one case where a done operation carries neither: the experiment no longer exists, so
no Experiment body is returned.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `operationId` | `string` | No | Stable operation ID. |
| `status` | `OperationalStatus` | No | Current operational status of the operation.  OPERATIONAL_STATUS_READY  OPERATIONAL_STATUS_CREATING  OPERATIONAL_STATUS_UPDATING  OPERATIONAL_STATUS_STARTING  OPERATIONAL_STATUS_STOPPING  OPERATIONAL_STATUS_SCHEDULING  OPERATIONAL_STATUS_DELETING  OPERATIONAL_STATUS_RAMPING_UP  OPERATIONAL_STATUS_SYNCING  OPERATIONAL_STATUS_ROLLING_OUT |
| `createdTime` | `string` | No | UTC time the operation was created. |
| `done` | `boolean` | No | True once the operation terminates (success or failure). When false, neither Error nor Experiment is populated. |
| `error` | `ExperimentApiError` | No | Error outcome. Populated iff Done is true and the operation failed. |
| `experiment` | `ProductExperiment` | No | Successful outcome. Populated iff Done is true and the operation succeeded and returned an experiment resource. |

### OperationalStatus

Current operational status reported on an experiment or an async operation performed on one.

OPERATIONAL_STATUS_READY

OPERATIONAL_STATUS_CREATING

OPERATIONAL_STATUS_UPDATING

OPERATIONAL_STATUS_STARTING

OPERATIONAL_STATUS_STOPPING

OPERATIONAL_STATUS_SCHEDULING

OPERATIONAL_STATUS_DELETING

OPERATIONAL_STATUS_RAMPING_UP

OPERATIONAL_STATUS_SYNCING

OPERATIONAL_STATUS_ROLLING_OUT

Values: `OPERATIONAL_STATUS_READY`, `OPERATIONAL_STATUS_CREATING`, `OPERATIONAL_STATUS_UPDATING`, `OPERATIONAL_STATUS_STARTING`, `OPERATIONAL_STATUS_STOPPING`, `OPERATIONAL_STATUS_SCHEDULING`, `OPERATIONAL_STATUS_DELETING`, `OPERATIONAL_STATUS_RAMPING_UP`, `OPERATIONAL_STATUS_SYNCING`, `OPERATIONAL_STATUS_ROLLING_OUT`

### ExperimentApiError

Application-layer error emitted on a failed experiment operation.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `errorType` | `ExperimentApiErrorType` | No | Broad category of the failure.  EXPERIMENT_API_ERROR_TYPE_INVALID_VARIANT_CONFIGURATION  EXPERIMENT_API_ERROR_TYPE_INVALID_VARIANT_LABEL  EXPERIMENT_API_ERROR_TYPE_MUST_HAVE_EXACTLY_ONE_BASELINE_VARIANT  EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_OVERLAPPING_RUNTIME  EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_INVALID_SCORING_CONFIGURATIONS  EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_UNEXPECTED_PRODUCT_TYPE  EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_EMPTY_CONFIGURATION  EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_EMPTY_VARIANT_METADATA  EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_VARIANT_WEIGHT_MUST_BE_POSITIVE  EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_VARIANT_WEIGHTS_UNBALANCED  EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_PLACE_CONFIG_REQUIRES_SCORING_ID_OR_DEFAULT  EXPERIMENT_API_ERROR_TYPE_CONFIGS_MISSING_VARIANT  EXPERIMENT_API_ERROR_TYPE_CONFIGS_VARIANT_MISSING_KEY  EXPERIMENT_API_ERROR_TYPE_CONFIGS_VARIANT_MISSING_VALUE  EXPERIMENT_API_ERROR_TYPE_CONFIGS_KEY_ALREADY_IN_USE  EXPERIMENT_API_ERROR_TYPE_SYSTEM_ERROR  EXPERIMENT_API_ERROR_TYPE_EXPERIMENT_RESULTS_NOT_FOUND  EXPERIMENT_API_ERROR_TYPE_INVALID_TARGETING_CRITERIA  EXPERIMENT_API_ERROR_TYPE_TARGETING_NOT_ALLOWED  EXPERIMENT_API_ERROR_TYPE_INVALID_DURATION  EXPERIMENT_API_ERROR_TYPE_CONFIGS_VARIANT_CONFIG_NOT_FOUND  EXPERIMENT_API_ERROR_TYPE_INVALID_EXPERIMENT_NAME  EXPERIMENT_API_ERROR_TYPE_CONDITIONAL_CONFIG_REQUIRES_NULL_BASELINE  EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_CONTROL_VARIANT_MUST_MATCH_CURRENT_CONFIGURATION  EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_VARIANTS_MUST_COVER_SAME_PLACES  EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_VARIANT_HAS_DUPLICATE_PLACES  EXPERIMENT_API_ERROR_TYPE_CONFIGS_KEY_HAS_RESERVED_PREFIX |
| `errorCode` | `string` | No | Stable machine-readable error code. |
| `errorMessage` | `string` | No | Human-readable description of the failure. |
| `errorContext` | `object` | No | Optional structured context about the failure (field paths, offending values, etc.). |

### ProductExperiment

Config-based experiment for a given product. Returned by the Get endpoint and embedded in
a successful experiment operation.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `string` | No | Experiment ID. |
| `name` | `string` | No | Experiment display name. |
| `description` | `string` | No | Experiment description. |
| `createdTime` | `string` | No | UTC time the experiment was created. |
| `lastUpdatedTime` | `string` | No | UTC time the experiment was last updated. |
| `startedTime` | `string` | No | UTC time the experiment was started (running), if it has been. |
| `stoppedTime` | `string` | No | UTC time the experiment was stopped, if it has been. |
| `state` | `ExperimentState` | No | Lifecycle state.  EXPERIMENT_STATE_DRAFT  EXPERIMENT_STATE_SCHEDULED  EXPERIMENT_STATE_RUNNING  EXPERIMENT_STATE_COMPLETED  EXPERIMENT_STATE_CANCELLED  EXPERIMENT_STATE_DELETED |
| `experimentConfiguration` | `ExperimentConfiguration` | No | Experiment configuration (variants and product-type-specific data). |
| `exposurePercent` | `integer` | No | Exposure percent in range 0-100. |
| `targetingCriteria` | `TargetingCriteria` | No | Targeting criteria scoping which users are eligible for the experiment. |
| `operationalStatus` | `OperationalStatus` | No | Current operational status of an in-flight async operation (if any).  OPERATIONAL_STATUS_READY  OPERATIONAL_STATUS_CREATING  OPERATIONAL_STATUS_UPDATING  OPERATIONAL_STATUS_STARTING  OPERATIONAL_STATUS_STOPPING  OPERATIONAL_STATUS_SCHEDULING  OPERATIONAL_STATUS_DELETING  OPERATIONAL_STATUS_RAMPING_UP  OPERATIONAL_STATUS_SYNCING  OPERATIONAL_STATUS_ROLLING_OUT |
| `createdBy` | `string` | No | User ID of the creator of the experiment. |
| `scheduledTime` | `string` | No | UTC time the experiment is scheduled to start, if scheduled. |
| `durationSeconds` | `integer` | No | Experiment duration in whole seconds. |
| `universeMetricConfiguration` | `UniverseMetricConfiguration` | No | Metric configuration (goal + learning metrics). |

### ExperimentConfiguration

Union of per-product experiment configurations. At most one of InGameConfigExperimentConfiguration or
MatchmakingExperimentConfiguration may be set.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `productType` | `ExperimentProductType` | No | Discriminator selecting which configuration variant is populated.  EXPERIMENT_PRODUCT_TYPE_IN_GAME_CONFIGS  EXPERIMENT_PRODUCT_TYPE_MATCHMAKING |
| `inGameConfigExperimentConfiguration` | `InGameConfigExperimentConfiguration` | No | Populated when ProductType is InGameConfigExperimentConfiguration, null otherwise. |
| `matchmakingExperimentConfiguration` | `MatchmakingExperimentConfiguration` | No | Populated when ProductType is MatchmakingExperimentConfiguration, null otherwise. |

### TargetingCriteria

Eligibility criteria scoping which users an experiment can apply to.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `rule` | `ConditionalRuleDefinition` | No | RPN rule that decides whether an evaluator (user, request, etc.) is eligible for the experiment. `null` means no targeting (every otherwise-eligible user is in scope). |

### UniverseMetricConfiguration

Metric configuration for an experiment.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `goalMetric` | `UniverseExperimentMetric` | No | Goal metric.  UNIVERSE_EXPERIMENT_METRIC_AVERAGE_SESSION_TIME  UNIVERSE_EXPERIMENT_METRIC_PLAYTIME_PER_USER  UNIVERSE_EXPERIMENT_METRIC_DAY_1_RETENTION  UNIVERSE_EXPERIMENT_METRIC_DAY_7_RETENTION  UNIVERSE_EXPERIMENT_METRIC_PAYER_CONVERSION_RATE  UNIVERSE_EXPERIMENT_METRIC_AVERAGE_REVENUE_PER_USER  UNIVERSE_EXPERIMENT_METRIC_AVERAGE_REVENUE_PER_PAYING_USER |
| `learningMetrics` | `UniverseExperimentMetric[]` | No | Learning (observation-only) metrics. |

### UniverseExperimentMetric

Metric tracked for a universe experiment.

UNIVERSE_EXPERIMENT_METRIC_AVERAGE_SESSION_TIME

UNIVERSE_EXPERIMENT_METRIC_PLAYTIME_PER_USER

UNIVERSE_EXPERIMENT_METRIC_DAY_1_RETENTION

UNIVERSE_EXPERIMENT_METRIC_DAY_7_RETENTION

UNIVERSE_EXPERIMENT_METRIC_PAYER_CONVERSION_RATE

UNIVERSE_EXPERIMENT_METRIC_AVERAGE_REVENUE_PER_USER

UNIVERSE_EXPERIMENT_METRIC_AVERAGE_REVENUE_PER_PAYING_USER

Values: `UNIVERSE_EXPERIMENT_METRIC_AVERAGE_SESSION_TIME`, `UNIVERSE_EXPERIMENT_METRIC_PLAYTIME_PER_USER`, `UNIVERSE_EXPERIMENT_METRIC_DAY_1_RETENTION`, `UNIVERSE_EXPERIMENT_METRIC_DAY_7_RETENTION`, `UNIVERSE_EXPERIMENT_METRIC_PAYER_CONVERSION_RATE`, `UNIVERSE_EXPERIMENT_METRIC_AVERAGE_REVENUE_PER_USER`, `UNIVERSE_EXPERIMENT_METRIC_AVERAGE_REVENUE_PER_PAYING_USER`

### ConditionalRuleDefinition

JSON shape of an RPN conditional rule in public API requests.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `tokens` | `RpnTokenDto[]` | No | Postfix RPN token sequence. |

### RpnTokenDto

One RPN token: either a logical/comparison ConditionalRuleOperator or an operand object.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `operator` | `ConditionalRuleOperator` | No | OPERATOR_AND  OPERATOR_OR  OPERATOR_NOT  OPERATOR_EQ  OPERATOR_NE  OPERATOR_GT  OPERATOR_LT  OPERATOR_GTE  OPERATOR_LTE  OPERATOR_IN  OPERATOR_NIN |
| `operand` | `RpnOperandDto` | No | RPN operand: attribute reference or literal value. |

### ConditionalRuleOperator

RPN token operator values for public HTTP JSON, aligned with
`roblox.creatorexperienceconfig.conditionrules.v1.Operator` numeric values `1`–`11`.
The proto `OPERATOR_INVALID` (`0`) is not exposed here; unknown or invalid operators are rejected at deserialization.
JSON uses proto symbolic names (`OPERATOR_AND`, …) via Google.Protobuf.Reflection.OriginalNameAttribute.

OPERATOR_AND

OPERATOR_OR

OPERATOR_NOT

OPERATOR_EQ

OPERATOR_NE

OPERATOR_GT

OPERATOR_LT

OPERATOR_GTE

OPERATOR_LTE

OPERATOR_IN

OPERATOR_NIN

Values: `OPERATOR_AND`, `OPERATOR_OR`, `OPERATOR_NOT`, `OPERATOR_EQ`, `OPERATOR_NE`, `OPERATOR_GT`, `OPERATOR_LT`, `OPERATOR_GTE`, `OPERATOR_LTE`, `OPERATOR_IN`, `OPERATOR_NIN`

### RpnOperandDto

RPN operand: attribute reference or literal value.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `attributeReference` | `string` | No |  |
| `literalValue` | `LiteralValueDto` | No | Literal constant for an RPN operand. |

### LiteralValueDto

Literal constant for an RPN operand.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `booleanValue` | `boolean` | No |  |
| `integerValue` | `integer` | No |  |
| `doubleValue` | `number` | No |  |
| `stringValue` | `string` | No |  |

### InGameConfigExperimentConfiguration

Configuration for an in-game-config experiment.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `variants` | `SingleConfigExperimentVariant[]` | No | Variants participating in the experiment. Exactly one must have IsBaseline set. |

### MatchmakingExperimentConfiguration

Configuration for a matchmaking experiment.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `variants` | `MatchmakingExperimentVariant[]` | No | Variants participating in the experiment. |

### MatchmakingExperimentVariant

Variant definition for a matchmaking experiment.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `variantMeta` | `VariantMeta` | No | Metadata common to all variants. |
| `placeMatchmakingConfigs` | `PlaceScoringConfig[]` | No | Per-place matchmaking scoring configurations applied when this variant is selected. |

### VariantMeta

Metadata shared by every experiment variant.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `variantId` | `string` | No | Unique identifier for the variant. Only assigned once the experiment starts running; empty or null for draft variants. |
| `label` | `string` | No | Human-readable label for the variant, e.g. `Control`, `Treatment A`. Non-empty, at most 50 characters; must start with a letter and contain only letters, digits, spaces, underscores, or hyphens. |
| `isBaseline` | `boolean` | No | True iff this variant is the baseline. Exactly one variant must be the baseline. |
| `weight` | `integer` | No | Relative traffic weight for this variant. The platform normalizes across all variants, so weights do not have to sum to 100. |

### PlaceScoringConfig

Matchmaking scoring configuration applied to a single place in an experiment variant.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `placeId` | `integer` | No | Place ID this scoring config applies to. |
| `matchmakingScoringConfigId` | `string` | No | Matchmaking scoring config ID for this place. Ignored when UsePlatformDefault is true. |
| `usePlatformDefault` | `boolean` | No | When true, this place uses the platform default matchmaking scoring config instead of MatchmakingScoringConfigId. |

### SingleConfigExperimentVariant

Variant definition for an in-game-config experiment (CreatorConfigsPublicApi.Models.Experimentation.InGameConfigExperimentConfiguration).

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `variantMeta` | `VariantMeta` | No | Metadata common to all variants. |
| `configEntry` | `ExperimentConfigEntry` | No | The config entry value for this variant. Required for non-`IsBaseline` variants. |

### ExperimentConfigEntry

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `key` | `string` | No | The config key this variant overrides. Must match across variants in the same experiment. |
| `entryValue` | `any` | No | The value assigned to Key for this variant. Can be a string, number, bool, array, object, or null. |
| `description` | `string` | No | Optional human-readable description carried alongside the value. |

### ExperimentApiErrorType

Validation failures.

EXPERIMENT_API_ERROR_TYPE_INVALID_VARIANT_CONFIGURATION

EXPERIMENT_API_ERROR_TYPE_INVALID_VARIANT_LABEL

EXPERIMENT_API_ERROR_TYPE_MUST_HAVE_EXACTLY_ONE_BASELINE_VARIANT

EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_OVERLAPPING_RUNTIME

EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_INVALID_SCORING_CONFIGURATIONS

EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_UNEXPECTED_PRODUCT_TYPE

EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_EMPTY_CONFIGURATION

EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_EMPTY_VARIANT_METADATA

EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_VARIANT_WEIGHT_MUST_BE_POSITIVE

EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_VARIANT_WEIGHTS_UNBALANCED

EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_PLACE_CONFIG_REQUIRES_SCORING_ID_OR_DEFAULT

EXPERIMENT_API_ERROR_TYPE_CONFIGS_MISSING_VARIANT

EXPERIMENT_API_ERROR_TYPE_CONFIGS_VARIANT_MISSING_KEY

EXPERIMENT_API_ERROR_TYPE_CONFIGS_VARIANT_MISSING_VALUE

EXPERIMENT_API_ERROR_TYPE_CONFIGS_KEY_ALREADY_IN_USE

EXPERIMENT_API_ERROR_TYPE_SYSTEM_ERROR

EXPERIMENT_API_ERROR_TYPE_EXPERIMENT_RESULTS_NOT_FOUND

EXPERIMENT_API_ERROR_TYPE_INVALID_TARGETING_CRITERIA

EXPERIMENT_API_ERROR_TYPE_TARGETING_NOT_ALLOWED

EXPERIMENT_API_ERROR_TYPE_INVALID_DURATION

EXPERIMENT_API_ERROR_TYPE_CONFIGS_VARIANT_CONFIG_NOT_FOUND

EXPERIMENT_API_ERROR_TYPE_INVALID_EXPERIMENT_NAME

EXPERIMENT_API_ERROR_TYPE_CONDITIONAL_CONFIG_REQUIRES_NULL_BASELINE

EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_CONTROL_VARIANT_MUST_MATCH_CURRENT_CONFIGURATION

EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_VARIANTS_MUST_COVER_SAME_PLACES

EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_VARIANT_HAS_DUPLICATE_PLACES

EXPERIMENT_API_ERROR_TYPE_CONFIGS_KEY_HAS_RESERVED_PREFIX

Values: `EXPERIMENT_API_ERROR_TYPE_INVALID_VARIANT_CONFIGURATION`, `EXPERIMENT_API_ERROR_TYPE_INVALID_VARIANT_LABEL`, `EXPERIMENT_API_ERROR_TYPE_MUST_HAVE_EXACTLY_ONE_BASELINE_VARIANT`, `EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_OVERLAPPING_RUNTIME`, `EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_INVALID_SCORING_CONFIGURATIONS`, `EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_UNEXPECTED_PRODUCT_TYPE`, `EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_EMPTY_CONFIGURATION`, `EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_EMPTY_VARIANT_METADATA`, `EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_VARIANT_WEIGHT_MUST_BE_POSITIVE`, `EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_VARIANT_WEIGHTS_UNBALANCED`, `EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_PLACE_CONFIG_REQUIRES_SCORING_ID_OR_DEFAULT`, `EXPERIMENT_API_ERROR_TYPE_CONFIGS_MISSING_VARIANT`, `EXPERIMENT_API_ERROR_TYPE_CONFIGS_VARIANT_MISSING_KEY`, `EXPERIMENT_API_ERROR_TYPE_CONFIGS_VARIANT_MISSING_VALUE`, `EXPERIMENT_API_ERROR_TYPE_CONFIGS_KEY_ALREADY_IN_USE`, `EXPERIMENT_API_ERROR_TYPE_SYSTEM_ERROR`, `EXPERIMENT_API_ERROR_TYPE_EXPERIMENT_RESULTS_NOT_FOUND`, `EXPERIMENT_API_ERROR_TYPE_INVALID_TARGETING_CRITERIA`, `EXPERIMENT_API_ERROR_TYPE_TARGETING_NOT_ALLOWED`, `EXPERIMENT_API_ERROR_TYPE_INVALID_DURATION`, `EXPERIMENT_API_ERROR_TYPE_CONFIGS_VARIANT_CONFIG_NOT_FOUND`, `EXPERIMENT_API_ERROR_TYPE_INVALID_EXPERIMENT_NAME`, `EXPERIMENT_API_ERROR_TYPE_CONDITIONAL_CONFIG_REQUIRES_NULL_BASELINE`, `EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_CONTROL_VARIANT_MUST_MATCH_CURRENT_CONFIGURATION`, `EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_VARIANTS_MUST_COVER_SAME_PLACES`, `EXPERIMENT_API_ERROR_TYPE_MATCHMAKING_VARIANT_HAS_DUPLICATE_PLACES`, `EXPERIMENT_API_ERROR_TYPE_CONFIGS_KEY_HAS_RESERVED_PREFIX`

### MdeOperation

Async operation result for a `:calculateMde` call. When Done is true
exactly one of Error or Mde is set; when false, neither is.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `operationId` | `string` | No | Stable operation ID. |
| `lastModifiedTime` | `string` | No | UTC time the operation was last modified. |
| `done` | `boolean` | No | True once the calculation terminates (success or failure). |
| `error` | `ExperimentApiError` | No | Error outcome, when Done is true and the calculation failed. |
| `mde` | `MdeResult` | No | Successful outcome, when Done is true and a result is available. |

### MdeResult

MDE calculation result. Returned in the `operation.result` field on a successful
`POST .../experiments:calculateMde` call.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `totalSampleSize` | `integer` | No | Estimated total sample size required for the experiment. |
| `mdeRelativePercentages` | `number[]` | No | MDE expressed as a relative percentage of the goal metric, per non-baseline variant. |
| `minimumSampleSizeThreshold` | `integer` | No | Below this sample-size threshold the MDE estimate is unreliable. |

### ExperimentStatsOperation

Async operation for fetching experiment stats. When Done is true exactly
one of Error or ExperimentStats is set; when false, neither is.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `experimentId` | `integer` | No | Experiment ID the stats are for. |
| `lastModifiedTime` | `string` | No | UTC time the operation was last modified. |
| `done` | `boolean` | No | True once the stats fetch terminates (success or failure). |
| `error` | `ExperimentApiError` | No | Error outcome, when Done is true and the fetch failed. |
| `experimentStats` | `ExperimentStats` | No | Successful outcome, when Done is true and stats are available. |

### ExperimentStats

Computed stats for a running experiment.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `isSrmDetected` | `boolean` | No | True if Sample Ratio Mismatch (SRM) was detected for the experiment. |

### ExperimentSummary

Summary view of an experiment returned by the list endpoint. Does not include the variant /
configuration payload; clients should call Get for the full payload.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `string` | No | Experiment ID. |
| `name` | `string` | No | Experiment display name. |
| `description` | `string` | No | Experiment description. |
| `createdTime` | `string` | No | UTC time the experiment was created. |
| `lastUpdatedTime` | `string` | No | UTC time the experiment was last updated. |
| `startedTime` | `string` | No | UTC time the experiment was started, if running. |
| `stoppedTime` | `string` | No | UTC time the experiment was stopped, if completed/cancelled. |
| `state` | `ExperimentState` | No | Lifecycle state.  EXPERIMENT_STATE_DRAFT  EXPERIMENT_STATE_SCHEDULED  EXPERIMENT_STATE_RUNNING  EXPERIMENT_STATE_COMPLETED  EXPERIMENT_STATE_CANCELLED  EXPERIMENT_STATE_DELETED |
| `createdBy` | `string` | No | User ID of the creator of the experiment. |
| `experimentConfigKey` | `string` | No | Convenience field exposing the first config key referenced by the first variant (in-game-configs experiments only). Empty for matchmaking. |
| `scheduledTime` | `string` | No | UTC time the experiment is scheduled to start, if scheduled. |
| `durationSeconds` | `integer` | No | Planned experiment duration in whole seconds. |
| `productType` | `ExperimentProductType` | No | Product type.  EXPERIMENT_PRODUCT_TYPE_IN_GAME_CONFIGS  EXPERIMENT_PRODUCT_TYPE_MATCHMAKING |