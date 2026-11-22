<!-- Source: https://create.roblox.com/docs/en-us/cloud/reference/features/analytics.md -->

---
name: "Analytics"
last_updated: 2026-11-20T18:47:47Z
type: feature
api_base_url: "https://apis.roblox.com"
endpoints: 27
auth: [api-key, oauth2, cookie]
description: "Query analytics data, compare your metrics against benchmarks, manage custom dashboards, manage analytics alerts, and access error reports for your experiences programmatically"
---

# Analytics

Query analytics data, compare your metrics against benchmarks, manage custom dashboards, manage analytics alerts, and access error reports for your experiences programmatically. See the [Analytics guide](https://create.roblox.com/docs/cloud/guides/analytics), [Alerts guide](https://create.roblox.com/docs/cloud/guides/alerts), or [Error Reporting guide](https://create.roblox.com/docs/cloud/guides/error-reporting) for Open Cloud setup and usage.

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

### GET `/analytics-alert-control-plane/v1/resource/{resourceType}/id/{resourceId}/alerts` [EXPERIMENTAL]

Returns the alert configurations for a resource. Optionally filter by alert IDs, firing
status, severity, or metric name.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.analytics.alert:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `resourceType` | path | `AlertStorage.ResourceType` | Yes | The type of resource to query. Currently only `Universe` is supported.  Universe Valid values: `Universe` |
| `resourceId` | path | `string` | Yes | The numeric ID of the resource (e.g. the universe ID). |
| `ids` | query | `string[]` | No | Optional list of alert IDs to restrict results to. Repeat the parameter for multiple values: `?ids=1&ids=2`. IDs are string-encoded 64-bit integers. |
| `firingStatus` | query | `AlertStorage.FiringStatus` | No | Optional firing-status filter (`OK` or `Firing`).  OK  Firing Valid values: `OK`, `Firing` |
| `severities` | query | `AlertStorage.Severity[]` | No | Optional list of severity levels to filter by. Repeat the parameter for multiple values: `?severities=SEV_0&severities=SEV_1`. Valid values: `SEV_0`, `SEV_1`, `SEV_2` |
| `metrics` | query | `string[]` | No | Optional list of metric names to filter by (exact match, case-sensitive). Repeat the parameter for multiple values: `?metrics=dau&metrics=mau`. |

**Responses:**

- `200`: OK → `AnalyticsAlertControlPlane.Models.AlertDetailResponse[]`
- `400`: Bad Request → `AnalyticsAlertControlPlane.Models.ErrorResponse`
- `401`: Unauthorized → `AnalyticsAlertControlPlane.Models.ErrorResponse`
- `403`: Forbidden → `AnalyticsAlertControlPlane.Models.ErrorResponse`
- `503`: Service Unavailable → `AnalyticsAlertControlPlane.Models.ErrorResponse`

**Response fields** (`AnalyticsAlertControlPlane.Models.AlertDetailResponse[]`)

See [AnalyticsAlertControlPlane.Models.AlertDetailResponse](#analyticsalertcontrolplane-models-alertdetailresponse) in Models.

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 120/minute, perOauth2Authorization: 120/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/analytics-alert-control-plane/v1/resource/{RESOURCETYPE}/id/{RESOURCEID}/alerts"
```

### POST `/analytics-alert-control-plane/v1/resource/{resourceType}/id/{resourceId}/alerts` [EXPERIMENTAL]

Creates a new alert configuration for a resource.

See the <a href="https://create.roblox.com/docs/cloud/guides/alerts/metrics">alerts guide</a> for supported metrics and dimensions.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.analytics.alert:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `resourceType` | path | `AlertStorage.ResourceType` | Yes | The type of resource to create the alert on. Currently only `Universe` is supported.  Universe Valid values: `Universe` |
| `resourceId` | path | `string` | Yes | The numeric ID of the resource (e.g. the universe ID). |

**Request Body:** `application/json` — Type: `AnalyticsAlertControlPlane.Models.CreateAlertConfigRequest`

See [AnalyticsAlertControlPlane.Models.CreateAlertConfigRequest](#analyticsalertcontrolplane-models-createalertconfigrequest) in Models.

**Request example:**
```json
{
  "name": "string",
  "metric": "string",
  "description": "string",
  "severity": "SEV_0",
  "interval": "OneMinute",
  "consecutiveOccurrences": 0
}
```

**Responses:**

- `201`: Created → `AnalyticsAlertControlPlane.Models.AlertDetailResponse`
- `400`: Bad Request → `AnalyticsAlertControlPlane.Models.ErrorResponse`
- `401`: Unauthorized → `AnalyticsAlertControlPlane.Models.ErrorResponse`
- `403`: Forbidden → `AnalyticsAlertControlPlane.Models.ErrorResponse`
- `409`: Conflict. Possible error codes:              - `ALERT_NAME_EXISTED`: An alert with this name already exists for the resource.   Alert names must be unique per resource.              - `MAX_ALERT_REACHED`: The resource has reached the maximum number of allowed alerts. → `AnalyticsAlertControlPlane.Models.ErrorResponse`
- `503`: Service Unavailable → `AnalyticsAlertControlPlane.Models.ErrorResponse`

**Response fields** (`AnalyticsAlertControlPlane.Models.AlertDetailResponse`)

See [AnalyticsAlertControlPlane.Models.AlertDetailResponse](#analyticsalertcontrolplane-models-alertdetailresponse) in Models.

**Response example:**
```json
{
  "alertId": "string",
  "resourceType": "Universe",
  "resourceId": "string",
  "name": "string",
  "metric": "string",
  "description": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 30/minute, perOauth2Authorization: 30/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/analytics-alert-control-plane/v1/resource/{RESOURCETYPE}/id/{RESOURCEID}/alerts" \
  -H "Content-Type: application/json" \
  -d '{
  "name": "string",
  "metric": "string",
  "description": "string",
  "severity": "SEV_0",
  "interval": "OneMinute",
  "consecutiveOccurrences": 0
}'
```

### GET `/analytics-alert-control-plane/v1/resource/{resourceType}/id/{resourceId}/alerts/incidents` [EXPERIMENTAL]

Returns alert incidents for a resource whose active window overlaps the specified time
range. An incident is included if it was open at any point between `startTime` and
`endTime`.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.analytics.alert:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `resourceType` | path | `AlertStorage.ResourceType` | Yes | The type of resource to query. Currently only `Universe` is supported.  Universe Valid values: `Universe` |
| `resourceId` | path | `string` | Yes | The numeric ID of the resource (e.g. the universe ID). |
| `startTime` | query | `string` | Yes | Start of the time range to query (ISO 8601, UTC). Must be within the last 30 days (see AnalyticsAlertControlPlane.Operations.GetAlertIncidentsOperation.MaxQueryDays). |
| `endTime` | query | `string` | Yes | End of the time range to query (ISO 8601, UTC). Must be greater than or equal to `startTime`. |
| `metric` | query | `string` | No | Optional metric name to restrict results to incidents from alerts on that metric (exact match, case-sensitive). |
| `alertIds` | query | `string[]` | No | Optional list of alert IDs to restrict results to. Repeat the parameter for multiple values: `?alertIds=1&alertIds=2`. IDs are string-encoded 64-bit integers. |
| `severities` | query | `AlertStorage.Severity[]` | No | Optional list of severity levels to restrict results to. Repeat the parameter for multiple values: `?severities=SEV_0&severities=SEV_1`. Valid values: `SEV_0`, `SEV_1`, `SEV_2` |

**Responses:**

- `200`: OK → `AnalyticsAlertControlPlane.Models.IncidentDetailResponse[]`
- `400`: Bad Request → `AnalyticsAlertControlPlane.Models.ErrorResponse`
- `401`: Unauthorized → `AnalyticsAlertControlPlane.Models.ErrorResponse`
- `403`: Forbidden → `AnalyticsAlertControlPlane.Models.ErrorResponse`
- `503`: Service Unavailable → `AnalyticsAlertControlPlane.Models.ErrorResponse`

**Response fields** (`AnalyticsAlertControlPlane.Models.IncidentDetailResponse[]`)

See [AnalyticsAlertControlPlane.Models.IncidentDetailResponse](#analyticsalertcontrolplane-models-incidentdetailresponse) in Models.

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 120/minute, perOauth2Authorization: 120/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/analytics-alert-control-plane/v1/resource/{RESOURCETYPE}/id/{RESOURCEID}/alerts/incidents?startTime={VALUE}&endTime={VALUE}"
```

### PATCH `/analytics-alert-control-plane/v1/resource/{resourceType}/id/{resourceId}/alerts/{alertId}` [EXPERIMENTAL]

Updates an existing alert configuration. Only the fields included in the request body are
changed; omitted fields retain their current values.

See the <a href="https://create.roblox.com/docs/cloud/guides/alerts/metrics">alerts guide</a> for supported metrics and dimensions.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.analytics.alert:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `resourceType` | path | `AlertStorage.ResourceType` | Yes | The type of resource the alert belongs to. Currently only `Universe` is supported.  Universe Valid values: `Universe` |
| `resourceId` | path | `string` | Yes | The numeric ID of the resource (e.g. the universe ID). |
| `alertId` | path | `string` | Yes | The ID of the alert to update. |

**Request Body:** `application/json` — Type: `AnalyticsAlertControlPlane.Models.UpdateAlertConfigRequest`

See [AnalyticsAlertControlPlane.Models.UpdateAlertConfigRequest](#analyticsalertcontrolplane-models-updatealertconfigrequest) in Models.

**Request example:**
```json
{
  "name": "string",
  "metric": "string",
  "description": "string",
  "severity": "SEV_0",
  "interval": "OneMinute",
  "consecutiveOccurrences": 0
}
```

**Responses:**

- `200`: OK → `AnalyticsAlertControlPlane.Models.AlertDetailResponse`
- `400`: Bad Request → `AnalyticsAlertControlPlane.Models.ErrorResponse`
- `401`: Unauthorized → `AnalyticsAlertControlPlane.Models.ErrorResponse`
- `403`: Forbidden → `AnalyticsAlertControlPlane.Models.ErrorResponse`
- `404`: Not Found → `AnalyticsAlertControlPlane.Models.ErrorResponse`
- `409`: Conflict (`ALERT_NAME_EXISTED`): the new name collides with an existing alert on the same resource. Alert names must be unique per resource. → `AnalyticsAlertControlPlane.Models.ErrorResponse`
- `503`: Service Unavailable → `AnalyticsAlertControlPlane.Models.ErrorResponse`

**Response fields** (`AnalyticsAlertControlPlane.Models.AlertDetailResponse`)

See [AnalyticsAlertControlPlane.Models.AlertDetailResponse](#analyticsalertcontrolplane-models-alertdetailresponse) in Models.

**Response example:**
```json
{
  "alertId": "string",
  "resourceType": "Universe",
  "resourceId": "string",
  "name": "string",
  "metric": "string",
  "description": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 30/minute, perOauth2Authorization: 30/minute

**Example:**
```bash
curl -X PATCH -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/analytics-alert-control-plane/v1/resource/{RESOURCETYPE}/id/{RESOURCEID}/alerts/{ALERTID}" \
  -H "Content-Type: application/json" \
  -d '{
  "name": "string",
  "metric": "string",
  "description": "string",
  "severity": "SEV_0",
  "interval": "OneMinute",
  "consecutiveOccurrences": 0
}'
```

### DELETE `/analytics-alert-control-plane/v1/resource/{resourceType}/id/{resourceId}/alerts/{alertId}` [EXPERIMENTAL]

Deletes an alert configuration. This action is irreversible.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.analytics.alert:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `resourceType` | path | `AlertStorage.ResourceType` | Yes | The type of resource the alert belongs to. Currently only `Universe` is supported.  Universe Valid values: `Universe` |
| `resourceId` | path | `string` | Yes | The numeric ID of the resource (e.g. the universe ID). |
| `alertId` | path | `string` | Yes | The ID of the alert to delete. |

**Responses:**

- `204`: No Content
- `400`: Bad Request → `AnalyticsAlertControlPlane.Models.ErrorResponse`
- `401`: Unauthorized → `AnalyticsAlertControlPlane.Models.ErrorResponse`
- `403`: Forbidden → `AnalyticsAlertControlPlane.Models.ErrorResponse`
- `404`: Not Found → `AnalyticsAlertControlPlane.Models.ErrorResponse`
- `503`: Service Unavailable → `AnalyticsAlertControlPlane.Models.ErrorResponse`

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 30/minute, perOauth2Authorization: 30/minute

**Example:**
```bash
curl -X DELETE -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/analytics-alert-control-plane/v1/resource/{RESOURCETYPE}/id/{RESOURCEID}/alerts/{ALERTID}"
```

### POST `/analytics-benchmark/v1/universes/{universeId}/benchmarks` [EXPERIMENTAL]

Returns daily benchmark percentiles for a metric, comparing a universe against other experiences on Roblox.

See [Analytics Guide](https://create.roblox.com/docs/cloud/guides/analytics) for more information.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.analytics:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes | The ID of the universe to compare against benchmarks. |

**Request Body:** `application/json` — Type: `BenchmarkQuery`

See [BenchmarkQuery](#benchmarkquery) in Models.

**Request example:**
```json
{
  "metric": "string",
  "startTime": "string",
  "endTime": "string",
  "filter": [
    {
      "dimension": "...",
      "value": "..."
    }
  ],
  "benchmarkType": "BENCHMARK_TYPE_INVALID",
  "percentiles": [
    0
  ]
}
```

**Responses:**

- `200`: OK → `QueryUniverseBenchmarkResponse`
- `default`: Error → `AnalyticsBenchmarkApi.Status`

**Response fields** (`QueryUniverseBenchmarkResponse`)

See [QueryUniverseBenchmarkResponse](#queryuniversebenchmarkresponse) in Models.

**Response example:**
```json
{
  "result": {
    "values": [
      "..."
    ]
  },
  "availableTypes": [
    "BENCHMARK_TYPE_INVALID"
  ],
  "objective": "BENCHMARK_OBJECTIVE_INVALID"
}
```

**Rate Limits:** perApiKeyOwner: 300/minute, perOauth2Authorization: 300/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/analytics-benchmark/v1/universes/{UNIVERSEID}/benchmarks" \
  -H "Content-Type: application/json" \
  -d '{
  "metric": "string",
  "startTime": "string",
  "endTime": "string",
  "filter": [
    {
      "dimension": "...",
      "value": "..."
    }
  ],
  "benchmarkType": "BENCHMARK_TYPE_INVALID",
  "percentiles": [
    0
  ]
}'
```

### POST `/analytics-custom-dashboards/v1/universes/{universeId}/custom-dashboard-documents/validate` [BETA]

Validates a candidate dashboard document.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.analytics.dashboard:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |

**Request Body:** `application/json` — Type: `object`

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `document` | `any` | No | CustomDashboardDocument is the dashboard authoring document persisted as the |

**Request example:**
```json
{
  "document": "..."
}
```

**Responses:**

- `200`: OK → `ValidateDashboardDocumentResponse`
- `400`: Bad Request → `OpenCloudErrorResponseOfCustomDashboardError`
- `401`: Unauthorized → `OpenCloudErrorResponseOfCustomDashboardError`
- `403`: Forbidden → `OpenCloudErrorResponseOfCustomDashboardError`
- `429`: Too Many Requests → `OpenCloudErrorResponseOfCustomDashboardError`
- `500`: Internal Server Error → `OpenCloudErrorResponseOfCustomDashboardError`
- `503`: Service Unavailable → `OpenCloudErrorResponseOfCustomDashboardError`

**Response fields** (`ValidateDashboardDocumentResponse`)

See [ValidateDashboardDocumentResponse](#validatedashboarddocumentresponse) in Models.

**Response example:**
```json
{
  "isValid": false,
  "validationIssues": [
    {
      "fieldPath": "...",
      "reason": "...",
      "message": "...",
      "rejectedValues": "..."
    }
  ]
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 50/minute, perOauth2Authorization: 50/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/analytics-custom-dashboards/v1/universes/{UNIVERSEID}/custom-dashboard-documents/validate" \
  -H "Content-Type: application/json" \
  -d '{
  "document": "..."
}'
```

### GET `/analytics-custom-dashboards/v1/universes/{universeId}/custom-dashboards` [BETA]

Lists dashboard metadata for a universe.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.analytics.dashboard:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |
| `pageSize` | query | `integer` | No |  |
| `pageToken` | query | `string` | No |  |

**Responses:**

- `200`: OK → `ListDashboardsResponse`
- `400`: Bad Request → `OpenCloudErrorResponseOfCustomDashboardError`
- `401`: Unauthorized → `OpenCloudErrorResponseOfCustomDashboardError`
- `403`: Forbidden → `OpenCloudErrorResponseOfCustomDashboardError`
- `429`: Too Many Requests → `OpenCloudErrorResponseOfCustomDashboardError`
- `500`: Internal Server Error → `OpenCloudErrorResponseOfCustomDashboardError`
- `503`: Service Unavailable → `OpenCloudErrorResponseOfCustomDashboardError`

**Response fields** (`ListDashboardsResponse`)

See [ListDashboardsResponse](#listdashboardsresponse) in Models.

**Response example:**
```json
{
  "dashboards": [
    {
      "dashboardId": "...",
      "universeId": "...",
      "name": "...",
      "description": "...",
      "lifecycleState": "...",
      "isPinned": "..."
    }
  ],
  "nextPageToken": "string",
  "capabilities": "..."
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/analytics-custom-dashboards/v1/universes/{UNIVERSEID}/custom-dashboards"
```

### POST `/analytics-custom-dashboards/v1/universes/{universeId}/custom-dashboards` [BETA]

Creates a dashboard.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.analytics.dashboard:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |

**Request Body:** `application/json` — Type: `object`

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `name` | `string` | No |  |
| `description` | `string` | No |  |
| `document` | `any` | No | CustomDashboardDocument is the dashboard authoring document persisted as the |
| `idempotencyKey` | `string` | No | Optional caller-supplied token that makes this create idempotent. Repeating a create with |

**Request example:**
```json
{
  "name": "string",
  "description": "string",
  "document": "...",
  "idempotencyKey": "string"
}
```

**Responses:**

- `200`: OK → `CreateDashboardResponse`
- `400`: Bad Request → `OpenCloudErrorResponseOfCustomDashboardError`
- `401`: Unauthorized → `OpenCloudErrorResponseOfCustomDashboardError`
- `403`: Forbidden → `OpenCloudErrorResponseOfCustomDashboardError`
- `409`: Conflict → `OpenCloudErrorResponseOfCustomDashboardError`
- `429`: Too Many Requests → `OpenCloudErrorResponseOfCustomDashboardError`
- `500`: Internal Server Error → `OpenCloudErrorResponseOfCustomDashboardError`
- `503`: Service Unavailable → `OpenCloudErrorResponseOfCustomDashboardError`

**Response fields** (`CreateDashboardResponse`)

See [CreateDashboardResponse](#createdashboardresponse) in Models.

**Response example:**
```json
{
  "dashboard": "..."
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 50/minute, perOauth2Authorization: 50/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/analytics-custom-dashboards/v1/universes/{UNIVERSEID}/custom-dashboards" \
  -H "Content-Type: application/json" \
  -d '{
  "name": "string",
  "description": "string",
  "document": "...",
  "idempotencyKey": "string"
}'
```

### GET `/analytics-custom-dashboards/v1/universes/{universeId}/custom-dashboards/capabilities` [BETA]

Gets the latest published dashboard snapshot.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.analytics.dashboard:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |

**Responses:**

- `200`: OK → `GetDashboardResponse`
- `401`: Unauthorized → `OpenCloudErrorResponseOfCustomDashboardError`
- `403`: Forbidden → `OpenCloudErrorResponseOfCustomDashboardError`
- `404`: Not Found → `OpenCloudErrorResponseOfCustomDashboardError`
- `429`: Too Many Requests → `OpenCloudErrorResponseOfCustomDashboardError`
- `500`: Internal Server Error → `OpenCloudErrorResponseOfCustomDashboardError`
- `503`: Service Unavailable → `OpenCloudErrorResponseOfCustomDashboardError`

**Response fields** (`GetDashboardResponse`)

See [GetDashboardResponse](#getdashboardresponse) in Models.

**Response example:**
```json
{
  "dashboard": "..."
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/analytics-custom-dashboards/v1/universes/{UNIVERSEID}/custom-dashboards/capabilities"
```

### GET `/analytics-custom-dashboards/v1/universes/{universeId}/custom-dashboards/pinned` [BETA]

Gets the latest published dashboard snapshot.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.analytics.dashboard:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |

**Responses:**

- `200`: OK → `GetDashboardResponse`
- `401`: Unauthorized → `OpenCloudErrorResponseOfCustomDashboardError`
- `403`: Forbidden → `OpenCloudErrorResponseOfCustomDashboardError`
- `404`: Not Found → `OpenCloudErrorResponseOfCustomDashboardError`
- `429`: Too Many Requests → `OpenCloudErrorResponseOfCustomDashboardError`
- `500`: Internal Server Error → `OpenCloudErrorResponseOfCustomDashboardError`
- `503`: Service Unavailable → `OpenCloudErrorResponseOfCustomDashboardError`

**Response fields** (`GetDashboardResponse`)

See [GetDashboardResponse](#getdashboardresponse) in Models.

**Response example:**
```json
{
  "dashboard": "..."
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/analytics-custom-dashboards/v1/universes/{UNIVERSEID}/custom-dashboards/pinned"
```

### GET `/analytics-custom-dashboards/v1/universes/{universeId}/custom-dashboards/{dashboardId}` [BETA]

Gets the latest published dashboard snapshot.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.analytics.dashboard:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |
| `dashboardId` | path | `string` | Yes |  |

**Responses:**

- `200`: OK → `GetDashboardResponse`
- `401`: Unauthorized → `OpenCloudErrorResponseOfCustomDashboardError`
- `403`: Forbidden → `OpenCloudErrorResponseOfCustomDashboardError`
- `404`: Not Found → `OpenCloudErrorResponseOfCustomDashboardError`
- `429`: Too Many Requests → `OpenCloudErrorResponseOfCustomDashboardError`
- `500`: Internal Server Error → `OpenCloudErrorResponseOfCustomDashboardError`
- `503`: Service Unavailable → `OpenCloudErrorResponseOfCustomDashboardError`

**Response fields** (`GetDashboardResponse`)

See [GetDashboardResponse](#getdashboardresponse) in Models.

**Response example:**
```json
{
  "dashboard": "..."
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/analytics-custom-dashboards/v1/universes/{UNIVERSEID}/custom-dashboards/{DASHBOARDID}"
```

### POST `/analytics-custom-dashboards/v1/universes/{universeId}/custom-dashboards/{dashboardId}/delete` [BETA]

Deletes a dashboard.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.analytics.dashboard:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |
| `dashboardId` | path | `string` | Yes |  |

**Request Body:** `application/json` — Type: `object`

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `expectedHeadEtag` | `string` | No |  |

**Request example:**
```json
{
  "expectedHeadEtag": "string"
}
```

**Responses:**

- `200`: OK → `DeleteDashboardResponse`
- `400`: Bad Request → `OpenCloudErrorResponseOfCustomDashboardError`
- `401`: Unauthorized → `OpenCloudErrorResponseOfCustomDashboardError`
- `403`: Forbidden → `OpenCloudErrorResponseOfCustomDashboardError`
- `404`: Not Found → `OpenCloudErrorResponseOfCustomDashboardError`
- `409`: Conflict → `OpenCloudErrorResponseOfCustomDashboardError`
- `429`: Too Many Requests → `OpenCloudErrorResponseOfCustomDashboardError`
- `500`: Internal Server Error → `OpenCloudErrorResponseOfCustomDashboardError`
- `503`: Service Unavailable → `OpenCloudErrorResponseOfCustomDashboardError`

**Response fields** (`DeleteDashboardResponse`)

See [DeleteDashboardResponse](#deletedashboardresponse) in Models.

**Response example:**
```json
{
  "metadata": "..."
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 50/minute, perOauth2Authorization: 50/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/analytics-custom-dashboards/v1/universes/{UNIVERSEID}/custom-dashboards/{DASHBOARDID}/delete" \
  -H "Content-Type: application/json" \
  -d '{
  "expectedHeadEtag": "string"
}'
```

### PATCH `/analytics-custom-dashboards/v1/universes/{universeId}/custom-dashboards/{dashboardId}/metadata` [BETA]

Updates dashboard metadata.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.analytics.dashboard:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |
| `dashboardId` | path | `string` | Yes |  |

**Request Body:** `application/json` — Type: `object`

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `expectedHeadEtag` | `string` | No | Required. Enforced for name/description CAS. Ignored for pin-only patches; |
| `patch` | `any` | No | DashboardMetadataPatch updates dashboard metadata without exposing storage rows. |

**Request example:**
```json
{
  "expectedHeadEtag": "string",
  "patch": "..."
}
```

**Responses:**

- `200`: OK → `UpdateDashboardMetadataResponse`
- `400`: Bad Request → `OpenCloudErrorResponseOfCustomDashboardError`
- `401`: Unauthorized → `OpenCloudErrorResponseOfCustomDashboardError`
- `403`: Forbidden → `OpenCloudErrorResponseOfCustomDashboardError`
- `404`: Not Found → `OpenCloudErrorResponseOfCustomDashboardError`
- `409`: Conflict → `OpenCloudErrorResponseOfCustomDashboardError`
- `429`: Too Many Requests → `OpenCloudErrorResponseOfCustomDashboardError`
- `500`: Internal Server Error → `OpenCloudErrorResponseOfCustomDashboardError`
- `503`: Service Unavailable → `OpenCloudErrorResponseOfCustomDashboardError`

**Response fields** (`UpdateDashboardMetadataResponse`)

See [UpdateDashboardMetadataResponse](#updatedashboardmetadataresponse) in Models.

**Response example:**
```json
{
  "metadata": "..."
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 50/minute, perOauth2Authorization: 50/minute

**Example:**
```bash
curl -X PATCH -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/analytics-custom-dashboards/v1/universes/{UNIVERSEID}/custom-dashboards/{DASHBOARDID}/metadata" \
  -H "Content-Type: application/json" \
  -d '{
  "expectedHeadEtag": "string",
  "patch": "..."
}'
```

### POST `/analytics-custom-dashboards/v1/universes/{universeId}/custom-dashboards/{dashboardId}/publish` [BETA]

Publishes a caller-provided dashboard document.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.analytics.dashboard:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |
| `dashboardId` | path | `string` | Yes |  |

**Request Body:** `application/json` — Type: `object`

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `expectedHeadEtag` | `string` | No |  |
| `document` | `any` | No | CustomDashboardDocument is the dashboard authoring document persisted as the |
| `metadataPatch` | `any` | No | DashboardMetadataPatch updates dashboard metadata without exposing storage rows. |

**Request example:**
```json
{
  "expectedHeadEtag": "string",
  "document": "...",
  "metadataPatch": "..."
}
```

**Responses:**

- `200`: OK → `PublishDashboardResponse`
- `400`: Bad Request → `OpenCloudErrorResponseOfCustomDashboardError`
- `401`: Unauthorized → `OpenCloudErrorResponseOfCustomDashboardError`
- `403`: Forbidden → `OpenCloudErrorResponseOfCustomDashboardError`
- `404`: Not Found → `OpenCloudErrorResponseOfCustomDashboardError`
- `409`: Conflict → `OpenCloudErrorResponseOfCustomDashboardError`
- `429`: Too Many Requests → `OpenCloudErrorResponseOfCustomDashboardError`
- `500`: Internal Server Error → `OpenCloudErrorResponseOfCustomDashboardError`
- `503`: Service Unavailable → `OpenCloudErrorResponseOfCustomDashboardError`

**Response fields** (`PublishDashboardResponse`)

See [PublishDashboardResponse](#publishdashboardresponse) in Models.

**Response example:**
```json
{
  "dashboard": "..."
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 50/minute, perOauth2Authorization: 50/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/analytics-custom-dashboards/v1/universes/{UNIVERSEID}/custom-dashboards/{DASHBOARDID}/publish" \
  -H "Content-Type: application/json" \
  -d '{
  "expectedHeadEtag": "string",
  "document": "...",
  "metadataPatch": "..."
}'
```

### POST `/analytics-query-api/v1/universes/{universeId}/dimension-values` [BETA]

Queries dimension values for a universe.

See the <a href="https://create.roblox.com/docs/cloud/guides/analytics">Analytics guide</a> for more information.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.analytics:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes | The universe ID to query dimension values for. |

**Request Body:** `application/json` — Type: `DimensionValuesRequest`

See [DimensionValuesRequest](#dimensionvaluesrequest) in Models.

**Request example:**
```json
{
  "metric": "string",
  "dimensions": [
    "string"
  ],
  "startTime": "2024-01-01T00:00:00Z",
  "endTime": "2024-01-01T00:00:00Z",
  "filter": [
    {
      "dimension": "...",
      "values": "...",
      "operation": "..."
    }
  ],
  "granularity": "OneMinute"
}
```

**Responses:**

- `200`: OK → `DimensionValuesOperationResult`
- `202`: Accepted → `OperationPending`
- `400`: Bad Request → `OperationError`
- `403`: Forbidden → `OperationError`
- `429`: Too Many Requests → `OperationError`
- `500`: Internal Server Error → `OperationError`
- `503`: Service Unavailable → `OperationError`
- `504`: Gateway Timeout → `OperationError`

**Response fields** (`DimensionValuesOperationResult`)

See [DimensionValuesOperationResult](#dimensionvaluesoperationresult) in Models.

**Response example:**
```json
{
  "path": "string",
  "done": false,
  "response": {
    "values": [
      "..."
    ]
  },
  "metadata": {
    "createdTime": "2024-01-01T00:00:00Z"
  }
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 30/minute, perOauth2Authorization: 30/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/analytics-query-api/v1/universes/{UNIVERSEID}/dimension-values" \
  -H "Content-Type: application/json" \
  -d '{
  "metric": "string",
  "dimensions": [
    "string"
  ],
  "startTime": "2024-01-01T00:00:00Z",
  "endTime": "2024-01-01T00:00:00Z",
  "filter": [
    {
      "dimension": "...",
      "values": "...",
      "operation": "..."
    }
  ],
  "granularity": "OneMinute"
}'
```

### POST `/analytics-query-api/v1/universes/{universeId}/metrics` [BETA]

Queries time series metric data for a universe.

See the <a href="https://create.roblox.com/docs/cloud/guides/analytics">Analytics guide</a> for more information.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.analytics:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes | The universe ID to query metrics for. |

**Request Body:** `application/json` — Type: `QueryRequest`

See [QueryRequest](#queryrequest) in Models.

**Request example:**
```json
{
  "metric": "string",
  "granularity": "OneMinute",
  "startTime": "2024-01-01T00:00:00Z",
  "endTime": "2024-01-01T00:00:00Z",
  "breakdown": [
    "string"
  ],
  "filter": [
    {
      "dimension": "...",
      "values": "...",
      "operation": "..."
    }
  ]
}
```

**Responses:**

- `200`: OK → `QueryOperationResult`
- `202`: Accepted → `OperationPending`
- `400`: Bad Request → `OperationError`
- `403`: Forbidden → `OperationError`
- `429`: Too Many Requests → `OperationError`
- `500`: Internal Server Error → `OperationError`
- `503`: Service Unavailable → `OperationError`
- `504`: Gateway Timeout → `OperationError`

**Response fields** (`QueryOperationResult`)

See [QueryOperationResult](#queryoperationresult) in Models.

**Response example:**
```json
{
  "path": "string",
  "done": false,
  "response": {
    "values": [
      "..."
    ]
  },
  "metadata": {
    "createdTime": "2024-01-01T00:00:00Z"
  }
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 30/minute, perOauth2Authorization: 30/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/analytics-query-api/v1/universes/{UNIVERSEID}/metrics" \
  -H "Content-Type: application/json" \
  -d '{
  "metric": "string",
  "granularity": "OneMinute",
  "startTime": "2024-01-01T00:00:00Z",
  "endTime": "2024-01-01T00:00:00Z",
  "breakdown": [
    "string"
  ],
  "filter": [
    {
      "dimension": "...",
      "values": "...",
      "operation": "..."
    }
  ]
}'
```

### GET `/analytics-query-api/v1/universes/{universeId}/operations/dimension-values/{operationId}` [BETA]

Retrieves the result of a long-running dimension values operation.

See the <a href="https://create.roblox.com/docs/cloud/guides/analytics">Analytics guide</a> for more information.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.analytics:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes | The universe ID the operation belongs to. |
| `operationId` | path | `string` | Yes | The operation id returned from a prior dimension values request. |

**Responses:**

- `200`: OK → `DimensionValuesOperationResult`
- `202`: Accepted → `OperationPending`
- `400`: Bad Request → `OperationError`
- `404`: Not Found → `OperationError`
- `429`: Too Many Requests → `OperationError`
- `500`: Internal Server Error → `OperationError`
- `503`: Service Unavailable → `OperationError`
- `504`: Gateway Timeout → `OperationError`

**Response fields** (`DimensionValuesOperationResult`)

See [DimensionValuesOperationResult](#dimensionvaluesoperationresult) in Models.

**Response example:**
```json
{
  "path": "string",
  "done": false,
  "response": {
    "values": [
      "..."
    ]
  },
  "metadata": {
    "createdTime": "2024-01-01T00:00:00Z"
  }
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). 

**Rate Limits:** perApiKeyOwner: 3000/minute, perOauth2Authorization: 3000/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/analytics-query-api/v1/universes/{UNIVERSEID}/operations/dimension-values/{OPERATIONID}"
```

### GET `/analytics-query-api/v1/universes/{universeId}/operations/metrics/{operationId}` [BETA]

Retrieves the result of a long-running metrics query operation.

See the <a href="https://create.roblox.com/docs/cloud/guides/analytics">Analytics guide</a> for more information.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.analytics:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes | The universe ID the operation belongs to. |
| `operationId` | path | `string` | Yes | The operation id returned from a prior query request. |

**Responses:**

- `200`: OK → `QueryOperationResult`
- `202`: Accepted → `OperationPending`
- `400`: Bad Request → `OperationError`
- `404`: Not Found → `OperationError`
- `429`: Too Many Requests → `OperationError`
- `500`: Internal Server Error → `OperationError`
- `503`: Service Unavailable → `OperationError`
- `504`: Gateway Timeout → `OperationError`

**Response fields** (`QueryOperationResult`)

See [QueryOperationResult](#queryoperationresult) in Models.

**Response example:**
```json
{
  "path": "string",
  "done": false,
  "response": {
    "values": [
      "..."
    ]
  },
  "metadata": {
    "createdTime": "2024-01-01T00:00:00Z"
  }
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). 

**Rate Limits:** perApiKeyOwner: 3000/minute, perOauth2Authorization: 3000/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/analytics-query-api/v1/universes/{UNIVERSEID}/operations/metrics/{OPERATIONID}"
```

### GET `/log-attribute-http-service/v1/universe-regexes` [EXPERIMENTAL]

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.analytics:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | query | `integer` | No |  |
| `status` | query | `RegexStatus` | No | Valid values: `Invalid`, `CreatorCreated`, `AutoGenerated`, `CreatorIgnored` |

**Responses:**

- `200`: OK → `FindUniverseRegexesHttpResponse`

**Response fields** (`FindUniverseRegexesHttpResponse`)

See [FindUniverseRegexesHttpResponse](#finduniverseregexeshttpresponse) in Models.

**Response example:**
```json
{
  "universeRegexes": [
    {
      "id": "...",
      "universeId": "...",
      "regexStatus": "...",
      "pattern": "...",
      "output": "...",
      "order": "..."
    }
  ]
}
```

**Rate Limits:** perApiKeyOwner: 60/minute, perOauth2Authorization: 60/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/log-attribute-http-service/v1/universe-regexes"
```

### POST `/log-attribute-http-service/v1/universe-regexes` [EXPERIMENTAL]

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.analytics:write`

**Request Body:** `application/json` — Type: `CreateUniverseRegexHttpRequest`

See [CreateUniverseRegexHttpRequest](#createuniverseregexhttprequest) in Models.

**Request example:**
```json
{
  "universeId": 0,
  "pattern": "string",
  "output": "string",
  "regexOperation": "Invalid"
}
```

**Responses:**

- `200`: OK → `UniverseRegexMutationHttpResponse`

**Response fields** (`UniverseRegexMutationHttpResponse`)

See [UniverseRegexMutationHttpResponse](#universeregexmutationhttpresponse) in Models.

**Response example:**
```json
{
  "order": 0
}
```

**Rate Limits:** perApiKeyOwner: 60/minute, perOauth2Authorization: 60/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/log-attribute-http-service/v1/universe-regexes" \
  -H "Content-Type: application/json" \
  -d '{
  "universeId": 0,
  "pattern": "string",
  "output": "string",
  "regexOperation": "Invalid"
}'
```

### PUT `/log-attribute-http-service/v1/universe-regexes/{id}` [EXPERIMENTAL]

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.analytics:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `id` | path | `integer` | Yes |  |

**Request Body:** `application/json` — Type: `UpdateUniverseRegexHttpRequest`

See [UpdateUniverseRegexHttpRequest](#updateuniverseregexhttprequest) in Models.

**Request example:**
```json
{
  "pattern": "string",
  "output": "string",
  "regexOperation": "Invalid"
}
```

**Responses:**

- `200`: OK → `UniverseRegexMutationHttpResponse`

**Response fields** (`UniverseRegexMutationHttpResponse`)

See [UniverseRegexMutationHttpResponse](#universeregexmutationhttpresponse) in Models.

**Response example:**
```json
{
  "order": 0
}
```

**Rate Limits:** perApiKeyOwner: 60/minute, perOauth2Authorization: 60/minute

**Example:**
```bash
curl -X PUT -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/log-attribute-http-service/v1/universe-regexes/{ID}" \
  -H "Content-Type: application/json" \
  -d '{
  "pattern": "string",
  "output": "string",
  "regexOperation": "Invalid"
}'
```

### DELETE `/log-attribute-http-service/v1/universe-regexes/{id}` [EXPERIMENTAL]

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.analytics:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `id` | path | `integer` | Yes |  |

**Responses:**

- `200`: OK

**Rate Limits:** perApiKeyOwner: 60/minute, perOauth2Authorization: 60/minute

**Example:**
```bash
curl -X DELETE -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/log-attribute-http-service/v1/universe-regexes/{ID}"
```

### PUT `/log-attribute-http-service/v1/universe-regexes/{id}/ignore` [EXPERIMENTAL]

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.analytics:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `id` | path | `integer` | Yes |  |

**Responses:**

- `200`: OK

**Rate Limits:** perApiKeyOwner: 60/minute, perOauth2Authorization: 60/minute

**Example:**
```bash
curl -X PUT -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/log-attribute-http-service/v1/universe-regexes/{ID}/ignore"
```

### PUT `/log-attribute-http-service/v1/universe-regexes/{id}/reorder` [EXPERIMENTAL]

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.analytics:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `id` | path | `integer` | Yes |  |

**Request Body:** `application/json` — Type: `ReorderUniverseRegexHttpRequest`

See [ReorderUniverseRegexHttpRequest](#reorderuniverseregexhttprequest) in Models.

**Request example:**
```json
{
  "order": 0
}
```

**Responses:**

- `200`: OK → `UniverseRegexMutationHttpResponse`

**Response fields** (`UniverseRegexMutationHttpResponse`)

See [UniverseRegexMutationHttpResponse](#universeregexmutationhttpresponse) in Models.

**Response example:**
```json
{
  "order": 0
}
```

**Rate Limits:** perApiKeyOwner: 60/minute, perOauth2Authorization: 60/minute

**Example:**
```bash
curl -X PUT -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/log-attribute-http-service/v1/universe-regexes/{ID}/reorder" \
  -H "Content-Type: application/json" \
  -d '{
  "order": 0
}'
```

### GET `/notifications/v1/developer-analytics/get-notifs-analytics` [EXPERIMENTAL]

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.analytics:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `UniverseId` | query | `integer` | No |  |
| `UserId` | query | `integer` | No |  |
| `AggregationStartDateTime` | query | `string` | No |  |
| `AggregationEndDateTime` | query | `string` | No |  |

**Responses:**

- `200`: OK → `GetNotificationsAnalyticsResponse`

**Response fields** (`GetNotificationsAnalyticsResponse`)

See [GetNotificationsAnalyticsResponse](#getnotificationsanalyticsresponse) in Models.

**Response example:**
```json
{
  "overview": "...",
  "campaigns": [
    "..."
  ]
}
```

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/notifications/v1/developer-analytics/get-notifs-analytics"
```

### GET `/universe-performance-raqi/v1/events/logging/universe/{universeId}/log-details` [EXPERIMENTAL]

Get logs based on message hash ids, keywords, placeVersions, start/end time.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.analytics:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |
| `messageHashIds` | query | `string[]` | No |  |
| `keyword` | query | `string` | No | Optional keyword to help highlight matching keyword in the error message |
| `startTime` | query | `string` | No | Optional query window start; omitted values are defaulted server-side. |
| `endTime` | query | `string` | No | Optional query window end; omitted values are defaulted server-side. |
| `placeId` | query | `integer` | No | Optional place id filter. |
| `placeVersions` | query | `integer[]` | No | Optional place version filters. |
| `firstSeenPlaceVersion` | query | `integer` | No | Optional minimum first seen place version filter (inclusive). |

**Responses:**

- `200`: OK → `ErrorLogDetailResponse`
- `400`: Bad Request → `ActionResult`
- `401`: Unauthorized → `ActionResult`
- `403`: Forbidden → `ActionResult`
- `500`: Internal Server Error → `ActionResult`

**Response fields** (`ErrorLogDetailResponse`)

See [ErrorLogDetailResponse](#errorlogdetailresponse) in Models.

**Response example:**
```json
{
  "values": [
    {
      "id": "...",
      "logSeverity": "...",
      "logSource": "...",
      "os": "...",
      "platform": "...",
      "message": "..."
    }
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 60/minute, perOauth2Authorization: 60/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/universe-performance-raqi/v1/events/logging/universe/{UNIVERSEID}/log-details"
```

## Models

### AlertStorage.ResourceType

The type of resource an alert is attached to.

Universe

Values: `Universe`

### AlertStorage.FiringStatus

Whether an alert is currently in a firing or resolved state.

OK

Firing

Values: `OK`, `Firing`

### AlertStorage.Severity

Severity level assigned to an alert configuration.

SEV_0

SEV_1

SEV_2

Values: `SEV_0`, `SEV_1`, `SEV_2`

### AnalyticsAlertControlPlane.Models.AlertDetailResponse

Full details of a saved alert configuration.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `alertId` | `string` | Yes | Unique identifier of the alert configuration (string-encoded 64-bit integer). |
| `resourceType` | `AlertStorage.ResourceType` | Yes |  |
| `resourceId` | `string` | Yes | Numeric ID of the resource this alert monitors (e.g. the universe ID). |
| `name` | `string` | Yes | Display name of the alert. Must be unique within the resource. |
| `metric` | `string` | Yes | Name of the metric this alert evaluates. |
| `description` | `string` | No | Optional free-text description of the alert's purpose. |
| `severity` | `AlertStorage.Severity` | Yes |  |
| `interval` | `AlertStorage.AlertInterval` | Yes |  |
| `consecutiveOccurrences` | `integer` | Yes | Number of consecutive evaluation periods the condition must be met before the alert fires. Must be at least 1. For example, a value of 3 with a 1-minute interval means the condition must hold for 3 consecutive minutes before an incident is opened. |
| `filter` | `AnalyticsAlertControlPlane.Models.AlertQueryFilter[]` | No | Optional dimension filters applied to the metric query. Each entry restricts the metric to rows where the specified dimension matches one of the given values. |
| `breakdown` | `AnalyticsAlertControlPlane.Models.AlertQueryBreakdown[]` | No | Optional grouping dimensions for the metric query. When set, the alert evaluates the metric independently for each combination of dimension values and fires if any group breaches the condition. |
| `condition` | `AlertStorage.AlertCondition` | Yes |  |
| `configState` | `AlertStorage.AlertConfigState` | Yes |  |
| `webhookReceiverConfig` | `AlertStorage.WebhookReceiverConfig` | No |  |
| `firingStatus` | `AlertStorage.FiringStatus` | Yes |  |
| `lastFiredAt` | `string` | No | Timestamp of the most recent firing event. `null` if the alert has never fired. |
| `createdAt` | `string` | Yes | Timestamp when this alert configuration was created (UTC). |
| `lastModifiedAt` | `string` | Yes | Timestamp of the most recent modification to this alert configuration (UTC). |
| `lastModifiedBy` | `string` | No | ID of the user who last modified this alert configuration. `null` if the last modification was made by the system. |

### AnalyticsAlertControlPlane.Models.ErrorResponse

Standard error response body for the Alerts API.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `errorCode` | `string` | No | Machine-readable error code (e.g. PERMISSION_DENIED). |
| `message` | `string` | No | Human-readable error description. |

### AnalyticsAlertControlPlane.Models.CreateAlertConfigRequest

Request body for creating a new alert configuration.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `name` | `string` | Yes | Display name of the alert. Must be unique within the resource. Maximum length is 128 characters and the value is subject to Roblox text-moderation policies. |
| `metric` | `string` | Yes | Name of the metric this alert should evaluate. |
| `description` | `string` | No | Optional free-text description of the alert's purpose. |
| `severity` | `AlertStorage.Severity` | Yes |  |
| `interval` | `AlertStorage.AlertInterval` | Yes |  |
| `consecutiveOccurrences` | `integer` | Yes | Number of consecutive evaluation periods the condition must be met before the alert fires. Must be at least 1. For example, a value of 3 with a 1-minute interval means the condition must hold for 3 consecutive minutes before an incident is opened. |
| `breakdown` | `AnalyticsAlertControlPlane.Models.AlertQueryBreakdown[]` | No | Optional grouping dimensions for the metric query. When set, the alert evaluates the metric independently for each combination of dimension values and fires if any group breaches the condition. |
| `filter` | `AnalyticsAlertControlPlane.Models.AlertQueryFilter[]` | No | Optional dimension filters applied to the metric query. Each entry restricts the metric to rows where the specified dimension matches one of the given values. |
| `condition` | `AnalyticsAlertControlPlane.Models.AlertConditionInput` | Yes |  |
| `webhookReceiverConfig` | `AlertStorage.WebhookReceiverConfig` | No |  |

### AnalyticsAlertControlPlane.Models.IncidentDetailResponse

Details of a single alert incident.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `string` | Yes | Unique identifier of this incident. |
| `resourceType` | `AlertStorage.ResourceType` | Yes |  |
| `resourceId` | `string` | Yes | Numeric ID of the resource this incident belongs to (e.g. the universe ID). |
| `status` | `AlertStorage.FiringStatus` | Yes |  |
| `openedAt` | `string` | Yes | Timestamp when this incident was first opened (UTC). |
| `openedWindowStartAt` | `string` | Yes | Start of the evaluation window that first satisfied the alert condition and opened this incident (UTC). |
| `resolvedAt` | `string` | No | Timestamp when this incident was resolved (UTC). `null` if the incident is still active. |
| `resolvedWindowStartAt` | `string` | No | Start of the evaluation window in which the alert condition was no longer satisfied, causing the incident to be resolved (UTC). `null` if the incident is still active. |
| `firstFiringMetadata` | `AnalyticsAlertControlPlane.Models.FiringMetadataResponse` | Yes |  |
| `latestFiringMetadata` | `AnalyticsAlertControlPlane.Models.FiringMetadataResponse` | Yes |  |
| `alertConfig` | `AnalyticsAlertControlPlane.Models.AlertConfigSummary` | Yes |  |

### AnalyticsAlertControlPlane.Models.UpdateAlertConfigRequest

Request body for partially updating an alert configuration (PATCH semantics). All fields
are optional; only the fields present in the request body are updated.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `name` | `string` | No | New display name for the alert. Must be unique within the resource. Subject to Roblox text-moderation policies. |
| `metric` | `string` | No | New metric name this alert should evaluate. |
| `description` | `string` | No | New free-text description of the alert's purpose. |
| `severity` | `AlertStorage.Severity` | No |  |
| `interval` | `AlertStorage.AlertInterval` | No |  |
| `consecutiveOccurrences` | `integer` | No | New consecutive-occurrences count. When set, the alert will require the condition to hold for this many consecutive evaluation periods before firing. Must be at least 1. |
| `breakdown` | `AnalyticsAlertControlPlane.Models.AlertQueryBreakdown[]` | No | New grouping dimensions for the metric query. Replaces the existing breakdown entirely when provided. |
| `filter` | `AnalyticsAlertControlPlane.Models.AlertQueryFilter[]` | No | New dimension filters for the metric query. Replaces the existing filter list entirely when provided. |
| `condition` | `AnalyticsAlertControlPlane.Models.AlertConditionInput` | No |  |
| `webhookReceiverConfig` | `AlertStorage.WebhookReceiverConfig` | No |  |
| `configState` | `AlertStorage.AlertConfigState` | No |  |

### BenchmarkQuery

BenchmarkQuery is the request object for the benchmark query.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `metric` | `string` | No | The metric to benchmark, such as `ForwardD1Retention`, using the same metric names as the Analytics Query API. Metrics without benchmark data return no data points. |
| `startTime` | `string` | No | The start of the date range, inclusive. Required. Each benchmark value has a midnight UTC date, so a start time later in the day excludes that day. |
| `endTime` | `string` | No | The end of the date range, inclusive. Required. For `/v1/universes/{universe_id}/benchmarks`, it must not be earlier than `start_time`, and must be at most 400 days after it. |
| `filter` | `BreakdownFilter[]` | No | Dimension filters. Only applied to `BENCHMARK_TYPE_TOP_EXPERIENCES` benchmarks, and ignored otherwise. Filter values without benchmark data return no data points. |
| `benchmarkType` | `BenchmarkType` | No | The benchmark type to return. When omitted, top-experience metrics return `BENCHMARK_TYPE_TOP_EXPERIENCES` benchmarks, and other metrics return genre benchmarks with similarity values replacing them on dates where both exist. If a metric has similarity benchmarks but no genre benchmarks, request `BENCHMARK_TYPE_SIMILARITY` explicitly. When the requested type has no data, the result is empty and `available_types` lists the types that do. |
| `percentiles` | `integer[]` | No | The percentiles to return, each between 0 and 100, with at most 10 values. Defaults to 50 and 90, or 10 and 50 when lower values are favorable. Percentiles without benchmark data return no data points. Ignored for `BENCHMARK_TYPE_TOP_EXPERIENCES` benchmarks, which return a single percentile chosen from the universe's own average over the last 30 days, or a fixed percentile for some metrics. |
| `benchmarkVariantId` | `string` | No | The metric variant to benchmark. The only supported value is `l7_average`, which benchmarks the 7-day rolling average of `metric`. Not every metric has this variant, and the API rejects requests for metrics without it. Omit to benchmark `metric` itself. |

### QueryUniverseBenchmarkResponse

QueryUniverseBenchmarkResponse is the response message for QueryUniverseBenchmark.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `result` | `QueryBenchmarkResult` | No | The benchmark series, one per percentile. |
| `availableTypes` | `BenchmarkType[]` | No | The benchmark types available for this universe and metric. Request one with `benchmark_type`. |
| `objective` | `BenchmarkObjective` | No | Whether higher (`BENCHMARK_OBJECTIVE_MAXIMIZE`) or lower (`BENCHMARK_OBJECTIVE_MINIMIZE`) values of the metric are favorable. |

### AnalyticsBenchmarkApi.Status

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `code` | `integer` | No |  |
| `message` | `string` | No |  |
| `details` | `Any[]` | No |  |

### CustomDashboardDocument

CustomDashboardDocument is the dashboard authoring document persisted as the
latest published content. Draft edits remain local client state until the
caller sends this document to create or publish a dashboard.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `schemaVersion` | `integer` | No |  |
| `config` | `any` | No | CustomDashboardConfig is the renderer-owned dashboard authoring model. It is intentionally a normalized dashboard document rather than a direct mirror of Creator Hub RAQI TypeScript config types. Creator Hub adapters may generate TS from this proto and map it into the current RAQI renderer. |

### ValidateDashboardDocumentResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `isValid` | `boolean` | No |  |
| `validationIssues` | `CustomDashboardValidationIssue[]` | No |  |

### OpenCloudErrorResponseOfCustomDashboardError

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `errors` | `OpenCloudErrorOfCustomDashboardError[]` | Yes |  |

### ListDashboardsResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `dashboards` | `DashboardMetadata[]` | No |  |
| `nextPageToken` | `string` | No |  |
| `capabilities` | `any` | No | Capabilities and limits for the calling user in `ListDashboardsRequest.universe_id`. Identical to what `GetDashboardCapabilities` returns for the same caller and universe; both are populated by one shared implementation. Present on every page so a manage page does not need a second round trip. |

### CreateDashboardResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `dashboard` | `any` | No | CustomDashboard is the full dashboard response shape. |

### GetDashboardResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `dashboard` | `any` | No | CustomDashboard is the full dashboard response shape. |

### DeleteDashboardResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `metadata` | `any` | No | DashboardMetadata is the metadata-only shape returned by list calls. It intentionally omits the document body so list views do not load dashboard payloads. |

### DashboardMetadataPatch

DashboardMetadataPatch updates dashboard metadata without exposing storage rows.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `name` | `string` | No |  |
| `description` | `string` | No |  |
| `isPinned` | `boolean` | No |  |

### UpdateDashboardMetadataResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `metadata` | `any` | No | DashboardMetadata is the metadata-only shape returned by list calls. It intentionally omits the document body so list views do not load dashboard payloads. |

### PublishDashboardResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `dashboard` | `any` | No | CustomDashboard is the full dashboard response shape. |

### DimensionValuesRequest

A request to query dimension values.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `metric` | `string` | Yes | The metric that provides context for resolving dimension namespaces. |
| `dimensions` | `string[]` | No | The dimensions to retrieve values for. Each entry is a single dimension name. |
| `startTime` | `string` | Yes | The inclusive start of the query time range. Any UTC offset is accepted; results are always bucketed in UTC. |
| `endTime` | `string` | Yes | The exclusive end of the query time range. Any UTC offset is accepted; results are always bucketed in UTC. |
| `filter` | `QueryFilter[]` | No | Filters to apply to the query. |
| `granularity` | `MetricGranularity` | No |  |
| `limit` | `integer` | No | Optional result limit. Omit to use the data source default; an explicit value must be positive. |

### DimensionValuesOperationResult

A completed long-running dimension values operation with results.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `path` | `string` | No | The server-assigned resource path. |
| `done` | `boolean` | No | If false, the operation is still in progress. If true, the operation is completed. |
| `response` | `DimensionValuesResponse` | No |  |
| `metadata` | `OperationMetadata` | No |  |

### OperationPending

A long-running operation that is still in progress.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `path` | `string` | No | The server-assigned resource path. |
| `done` | `boolean` | No | If false, the operation is still in progress. If true, the operation is completed. |
| `metadata` | `OperationMetadata` | No |  |

### OperationError

A completed long-running operation that failed with an error.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `path` | `string` | No | The server-assigned resource path. |
| `done` | `boolean` | No | If false, the operation is still in progress. If true, the operation is completed. |
| `error` | `QueryError` | No |  |
| `metadata` | `OperationMetadata` | No |  |

### QueryRequest

A request to query time series metric data.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `metric` | `string` | Yes | The metric to query. |
| `granularity` | `MetricGranularity` | Yes |  |
| `startTime` | `string` | Yes | The inclusive start of the query time range. Any UTC offset is accepted; results are always bucketed in UTC. |
| `endTime` | `string` | Yes | The exclusive end of the query time range. Any UTC offset is accepted; results are always bucketed in UTC. |
| `breakdown` | `string[]` | No | The dimensions to group results by. Each entry is a single dimension name. |
| `filter` | `QueryFilter[]` | No | Filters to apply to the query. |
| `limit` | `integer` | No | Optional result limit. Omit to use the data source default; an explicit value must be positive. |

### QueryOperationResult

A completed long-running query operation with results.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `path` | `string` | No | The server-assigned resource path. |
| `done` | `boolean` | No | If false, the operation is still in progress. If true, the operation is completed. |
| `response` | `QueryResponse` | No |  |
| `metadata` | `OperationMetadata` | No |  |

### RegexStatus

Values: `Invalid`, `CreatorCreated`, `AutoGenerated`, `CreatorIgnored`

### FindUniverseRegexesHttpResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `universeRegexes` | `UniverseRegexHttpResponse[]` | No |  |

### CreateUniverseRegexHttpRequest

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `universeId` | `integer` | No |  |
| `pattern` | `string` | No |  |
| `output` | `string` | No |  |
| `regexOperation` | `RegexOperation` | No |  |

### UniverseRegexMutationHttpResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `order` | `integer` | No |  |

### UpdateUniverseRegexHttpRequest

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `pattern` | `string` | No |  |
| `output` | `string` | No |  |
| `regexOperation` | `RegexOperation` | No |  |

### ReorderUniverseRegexHttpRequest

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `order` | `integer` | No |  |

### GetNotificationsAnalyticsResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `overview` | `object` | Yes |  |
| `campaigns` | `object[]` | Yes |  |

### ErrorLogDetailResponse

Response for top error logs

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `values` | `ErrorLogDetail[]` | No | The analytics data for display. |

### ErrorLogDetail

error log detail

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `string` | Yes | The message hash id for this log detail. |
| `logSeverity` | `string` | No | The logSeverity of the log |
| `logSource` | `string` | No | The source of the log |
| `os` | `string` | No |  |
| `platform` | `string` | No |  |
| `message` | `string` | Yes | The message of the error log |
| `stacktrace` | `string` | No | The stack trace of the error log. This might be not available |
| `firstSeenUtc` | `string` | No | UTC timestamp when this error was first observed. Null when the source document predates this field being populated. |
| `firstSeenPlaceVersion` | `integer` | No | First seen place version for the error. NOTE: This value will only be returned when place id is filtered |

### RegexOperation

Values: `Invalid`, `Ignore`, `Group`

### UniverseRegexHttpResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No |  |
| `universeId` | `integer` | No |  |
| `regexStatus` | `RegexStatus` | No |  |
| `pattern` | `string` | No |  |
| `output` | `string` | No |  |
| `order` | `integer` | No |  |
| `regexOperation` | `RegexOperation` | No |  |
| `createdTime` | `string` | No |  |
| `updatedTime` | `string` | No |  |
| `matchedCount` | `integer` | No |  |
| `sampleMessage` | `string` | No |  |

### QueryResponse

The response for a metric query.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `values` | `AnalyticsQueryPublicApi.MetricValue[]` | No | The metric values returned by the query. |

### OperationMetadata

The metadata associated with a long-running operation.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `createdTime` | `string` | No | The time the operation was created. |

### AnalyticsQueryPublicApi.MetricValue

A metric value for a single breakdown series.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `breakdowns` | `AnalyticsQueryPublicApi.BreakdownValue[]` | No | The breakdown values for this series. |
| `dataPoints` | `AnalyticsQueryPublicApi.DataPoint[]` | No | The data points for this series. |

### AnalyticsQueryPublicApi.BreakdownValue

A breakdown dimension value in a query result.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `dimension` | `string` | Yes | The dimension name. |
| `value` | `string` | Yes | The dimension value. |
| `displayValue` | `string` | No | A human-readable display value when the dimension is a unique ID. |

### AnalyticsQueryPublicApi.DataPoint

A single data point in a metric query result.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `time` | `string` | Yes | The timestamp of the data point in UTC. |
| `value` | `number` | Yes | The numeric value of the data point. |
| `stringValues` | `string[]` | No | String values associated with the data point, when applicable. |
| `status` | `DataStatus` | No |  |

### DataStatus

The status of a data point in a query result.

Values: `Valid`, `Projected`, `NotStatisticallySignificant`, `InsufficientSampleSize`

### MetricGranularity

The time granularity of metric data points in a query.

Values: `OneMinute`, `HalfHour`, `OneHour`, `OneDay`, `OneWeek`, `OneMonth`, `None`

### QueryFilter

A filter applied to a query dimension.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `dimension` | `string` | Yes | The dimension name to filter on. |
| `values` | `string[]` | No | The values to filter by. |
| `operation` | `FilterOperation` | Yes |  |

### FilterOperation

The operation to apply to a query filter.

Values: `In`, `NotIn`, `GreaterThan`, `GreaterThanOrEqual`, `LessThan`, `LessThanOrEqual`, `Match`

### QueryError

The error returned from a query request.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `code` | `integer` | No | The error code. |
| `message` | `string` | Yes | The message associated with the query error. |

### DimensionValuesResponse

The response for a dimension values query.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `values` | `DimensionValues[]` | No | The dimension values returned by the query. |

### DimensionValues

The values for a single dimension returned by a dimension values query.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `dimension` | `string` | Yes | The dimension name. |
| `values` | `DimensionValue[]` | No | The values for the dimension. |

### DimensionValue

A single dimension value returned by a dimension values query.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `value` | `string` | Yes | The dimension value. |
| `displayValue` | `string` | No | A human-readable display value when the dimension is a unique ID. |

### CustomDashboard

CustomDashboard is the full dashboard response shape.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `metadata` | `any` | No | DashboardMetadata is the metadata-only shape returned by list calls. It intentionally omits the document body so list views do not load dashboard payloads. |
| `document` | `any` | No | CustomDashboardDocument is the dashboard authoring document persisted as the latest published content. Draft edits remain local client state until the caller sends this document to create or publish a dashboard. |
| `version` | `any` | No | DashboardDocumentVersion identifies the latest persisted content returned by the backend. |

### DashboardMetadata

DashboardMetadata is the metadata-only shape returned by list calls.
It intentionally omits the document body so list views do not load dashboard payloads.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `dashboardId` | `string` | No |  |
| `universeId` | `string` | No | Signed 64-bit integer encoded as a decimal string. |
| `name` | `string` | No |  |
| `description` | `string` | No |  |
| `lifecycleState` | `any` | No | DashboardLifecycleState describes whether a dashboard is visible to normal reads. |
| `isPinned` | `boolean` | No |  |
| `pinnedTime` | `any` | No |  |
| `createdTime` | `any` | No |  |
| `createdBy` | `any` | No | DashboardActor identifies a user responsible for creating or mutating dashboard state. |
| `updatedTime` | `any` | No |  |
| `updatedBy` | `any` | No | DashboardActor identifies a user responsible for creating or mutating dashboard state. |
| `publishedTime` | `any` | No |  |
| `publishedBy` | `any` | No | DashboardActor identifies a user responsible for creating or mutating dashboard state. |
| `deletedTime` | `any` | No |  |
| `deletedBy` | `any` | No | DashboardActor identifies a user responsible for creating or mutating dashboard state. |
| `headEtag` | `string` | No | Optimistic concurrency token for metadata, publish, and delete mutations. |
| `latestPublishedDocumentId` | `string` | No | Identifier for the latest persisted dashboard document. Latest-only content wins; older document payloads are not exposed for backend restore. |
| `latestPublishedVersion` | `string` | No | Monotonically increasing version for latest persisted content. |

### DashboardDocumentVersion

DashboardDocumentVersion identifies the latest persisted content returned by the backend.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `publishedDocumentId` | `string` | No |  |
| `publishedVersion` | `string` | No | Signed 64-bit integer encoded as a decimal string. |
| `contentHash` | `string` | No |  |

### DashboardActor

DashboardActor identifies a user responsible for creating or mutating dashboard state.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `userId` | `string` | No | Signed 64-bit integer encoded as a decimal string. |

### DashboardCapabilities

DashboardCapabilities describes what the calling creator may do in a universe
and the limits the service enforces on writes. Limits can change without a
client update. Open Cloud credential scopes are enforced separately by API
Gateway. These booleans describe creator permissions, not credential scopes.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `universeId` | `string` | No | Signed 64-bit integer encoded as a decimal string. |
| `canCreate` | `boolean` | No | True when the caller may create a new dashboard in this universe. |
| `canEdit` | `boolean` | No | True when the caller may change dashboard metadata. |
| `canPublish` | `boolean` | No | True when the caller may replace a dashboard's published document. |
| `canDelete` | `boolean` | No | True when the caller may soft-delete a dashboard. |
| `limits` | `any` | No | DashboardLimits mirrors the write-time caps enforced by this service. Values are resolved per request, so they reflect the current runtime configuration rather than the values present at deploy time. A limit of 0 means the cap is disabled and the service does not enforce it.              Clients should treat these as upper bounds and may apply a stricter presentation limit of their own; the effective cap for a client is the minimum of the two. |

### DashboardLimits

DashboardLimits mirrors the write-time caps enforced by this service. Values
are resolved per request, so they reflect the current runtime configuration
rather than the values present at deploy time. A limit of 0 means the cap is
disabled and the service does not enforce it.
            
Clients should treat these as upper bounds and may apply a stricter
presentation limit of their own; the effective cap for a client is the
minimum of the two.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `maxDashboardsPerUniverse` | `integer` | No | Maximum active dashboards per universe, enforced by the quota guard. |
| `maxDocumentPayloadBytes` | `integer` | No | Maximum encoded dashboard document payload size in bytes. |
| `maxSummaryCardsPerDashboard` | `integer` | No | Maximum summary card tiles in one dashboard document. |
| `maxChartTilesPerDashboard` | `integer` | No | Maximum chart tiles in one dashboard document. |
| `maxTableMetricColumns` | `integer` | No | Maximum metric columns in a single table chart tile. |
| `maxDashboardNameLength` | `integer` | No | Maximum dashboard name length in characters. |
| `maxDashboardDescriptionLength` | `integer` | No | Maximum dashboard description length in characters. |
| `maxTileTitleLength` | `integer` | No | Maximum tile title length in characters. |
| `maxPinnedDashboardsPerUniverse` | `integer` | No | Maximum pinned dashboards per universe, enforced by the quota guard. |
| `maxIdempotencyKeyLength` | `integer` | No | Maximum `CreateDashboardRequest.idempotency_key` length in characters accepted for a new create. Because the key is client-supplied and this cap is runtime-configurable, clients should read it here rather than assuming a fixed length. Lowering it does not invalidate keys that are already bound: those keep replaying at their original length. |

### OpenCloudErrorOfCustomDashboardError

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `code` | `integer` | Yes |  |
| `message` | `string` | Yes |  |
| `details` | `object` | No | CustomDashboardError is the structured error detail for API failures. |
| `referenceId` | `string` | No |  |

### CustomDashboardValidationIssue

CustomDashboardValidationIssue identifies a document field/path and the failed rule.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `fieldPath` | `string` | No |  |
| `reason` | `any` | No | CustomDashboardValidationIssueReason categorizes a single validation failure. |
| `message` | `string` | No |  |
| `rejectedValues` | `string[]` | No |  |

### CustomDashboardConflictDetails

CustomDashboardConflictDetails describes an optimistic concurrency failure.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `expectedHeadEtag` | `string` | No |  |
| `actualHeadEtag` | `string` | No |  |

### CustomDashboardConfig

CustomDashboardConfig is the renderer-owned dashboard authoring model. It is
intentionally a normalized dashboard document rather than a direct mirror of
Creator Hub RAQI TypeScript config types. Creator Hub adapters may generate
TS from this proto and map it into the current RAQI renderer.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `page` | `any` | No | DashboardPage models page shell behavior separately from surface layout. |

### DashboardPage

DashboardPage models page shell behavior separately from surface layout.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `untabbed` | `any` | No | DashboardUntabbedPage renders a dashboard page without tabs. |
| `fixedTab` | `any` | No | A fixed-tab page; Creator Hub does not yet support authoring this page type. |
| `breakdownTab` | `any` | No | A breakdown-tab page; Creator Hub does not yet support authoring this page type. |

### DashboardUntabbedPage

DashboardUntabbedPage renders a dashboard page without tabs.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `metadata` | `any` | No | DashboardPageMetadata carries localized metadata for a dashboard page. |
| `surface` | `any` | No | DashboardSurface is a renderable analytics surface. It owns page-wide analytics context/controls as well as the layout nodes rendered inside that context. |

### DashboardFixedTabPage

DashboardFixedTabPage renders a dashboard with a fixed set of tabs.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `metadata` | `any` | No | DashboardPageMetadata carries localized metadata for a dashboard page. |
| `tabs` | `DashboardFixedTab[]` | No |  |
| `tabOrder` | `string[]` | No | Optional explicit ordering by `DashboardFixedTab.tab_key`. If omitted, adapters use the order of `tabs`. |

### DashboardBreakdownTabPage

DashboardBreakdownTabPage renders tabs generated from breakdown values.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `metadata` | `any` | No | DashboardPageMetadata carries localized metadata for a dashboard page. |
| `tabBreakdownDimensionKey` | `string` | No |  |
| `tabSurface` | `any` | No | DashboardSurface is a renderable analytics surface. It owns page-wide analytics context/controls as well as the layout nodes rendered inside that context. |
| `noTabEmptyState` | `any` | No | DashboardSurface is a renderable analytics surface. It owns page-wide analytics context/controls as well as the layout nodes rendered inside that context. |
| `preTabNodes` | `DashboardLayoutNode[]` | No |  |

### DashboardPageMetadata

DashboardPageMetadata carries localized metadata for a dashboard page.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `titleKey` | `string` | No |  |

### DashboardSurface

DashboardSurface is a renderable analytics surface. It owns page-wide
analytics context/controls as well as the layout nodes rendered inside that
context.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `resourceTypeKeys` | `any[]` | No |  |
| `controls` | `any` | No | DashboardSurfaceControls defines the page-wide controls for a dashboard surface. |
| `bodyNodes` | `DashboardLayoutNode[]` | No | Main recursive layout tree. |

### DashboardLayoutNode

DashboardLayoutNode is the normalized custom-dashboard layout AST.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `component` | `any` | No | A renderable dashboard component. |
| `stack` | `any` | No | DashboardStackLayout is the vertical stack supported by Creator Hub custom dashboards. |
| `flex` | `any` | No | DashboardFlexLayout is the fixed row/wrap flex layout supported by Creator Hub custom dashboards. |
| `grid` | `any` | No | DashboardResponsiveGridLayout is the one-or-two-column grid supported by Creator Hub custom dashboards. |

### DashboardComponent

DashboardComponent wraps each renderable dashboard body component.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `chart` | `any` | No | A chart component. |
| `tabbedChart` | `any` | No | A tabbed chart; Creator Hub does not yet support authoring this component. |
| `table` | `any` | No | A table component. Creator Hub currently authors tables through ChartTile instead. |
| `tabbedTable` | `any` | No | A tabbed table; Creator Hub does not yet support authoring this component. |
| `summaryCard` | `any` | No | A summary card component. |
| `controlledSubcontext` | `any` | No | Controls applied to a component. |

### DashboardStackLayout

DashboardStackLayout is the vertical stack supported by Creator Hub custom dashboards.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `children` | `DashboardLayoutNode[]` | No |  |

### DashboardFlexLayout

DashboardFlexLayout is the fixed row/wrap flex layout supported by Creator Hub custom dashboards.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `children` | `DashboardLayoutNode[]` | No |  |

### DashboardResponsiveGridLayout

DashboardResponsiveGridLayout is the one-or-two-column grid supported by Creator Hub custom dashboards.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `columnCount` | `integer` | No |  |
| `children` | `DashboardLayoutNode[]` | No |  |

### ChartTile

ChartTile is a chart body tile.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `tileId` | `string` | No |  |
| `title` | `string` | No |  |
| `dataSpec` | `any` | No | DashboardChartDataSpec carries chart query inputs synthesized into RAQI requests. |
| `chartSpec` | `any` | No | DashboardChartSpec carries chart renderer options (not query/data inputs). |

### DashboardTabbedChart

DashboardTabbedChart renders chart tiles behind chart-specific tabs.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `componentId` | `string` | No |  |
| `title` | `string` | No |  |
| `tabs` | `DashboardChartTab[]` | No |  |

### DashboardTable

DashboardTable renders a table from dashboard chart data inputs.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `componentId` | `string` | No |  |
| `title` | `string` | No |  |
| `dataSpec` | `any` | No | DashboardChartDataSpec carries chart query inputs synthesized into RAQI requests. |

### DashboardTabbedTable

DashboardTabbedTable renders table components behind table-specific tabs.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `componentId` | `string` | No |  |
| `title` | `string` | No |  |
| `tabs` | `DashboardTableTab[]` | No |  |

### SummaryCardTile

SummaryCardTile is a top-of-dashboard summary card.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `tileId` | `string` | No |  |
| `title` | `string` | No |  |
| `metric` | `any` | No | DashboardMetricReference identifies either a catalog metric or an inline computed metric. A future saved custom metric key can be added to this oneof without changing tile/document layout. |
| `aggregation` | `any` | No | DashboardAggregation is the aggregation applied to a tile or series. Enum names follow proto conventions; synthesis adapters map to Creator Hub aggregation literal strings (`RAQIV2AggregationType`, summary-card literals, and `RAQIV2PercentileType`). Arbitrary `Percentile{N}` literals are not represented here and require a future contract extension. |
| `filters` | `TileFilter[]` | No |  |
| `titleSource` | `any` | No | DashboardTitleSource describes how a dashboard tile title is derived. |

### DashboardControlledSubcontext

DashboardControlledSubcontext mirrors RAQI controlled subcontexts as a
component wrapper, not a layout primitive. It applies local controls/context
overrides to exactly one chart/table-like body.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `dimensionFilterAndBreakdown` | `any` | No | DashboardDimensionFilterAndBreakdownSubcontext applies local dimension controls to a component. |
| `timeRange` | `any` | No | DashboardTimeRangeSubcontext applies a local time range control to a component. |
| `body` | `any` | No | DashboardControlledSubcontextBody stores the chart or table controlled by a local subcontext. |

### DashboardDimensionFilterAndBreakdownSubcontext

DashboardDimensionFilterAndBreakdownSubcontext applies local dimension controls to a component.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `controls` | `DashboardDimensionFilterAndBreakdownControl[]` | No |  |

### DashboardTimeRangeSubcontext

DashboardTimeRangeSubcontext applies a local time range control to a component.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `controlMode` | `any` | No | DashboardTimeRangeControlMode describes how time range controls are exposed. |
| `dateRangeKeys` | `string[]` | No |  |
| `defaultDateRangeKey` | `string` | No |  |
| `granularityByDateRange` | `object` | No |  |

### DashboardControlledSubcontextBody

DashboardControlledSubcontextBody stores the chart or table controlled by a local subcontext.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `chart` | `any` | No | ChartTile is a chart body tile. |
| `tabbedChart` | `any` | No | DashboardTabbedChart renders chart tiles behind chart-specific tabs. |
| `table` | `any` | No | DashboardTable renders a table from dashboard chart data inputs. |
| `tabbedTable` | `any` | No | DashboardTabbedTable renders table components behind table-specific tabs. |

### DashboardDimensionFilterAndBreakdownControl

DashboardDimensionFilterAndBreakdownControl defines one local dimension filter and breakdown control.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `filterDimensionKey` | `string` | No |  |
| `breakdownDimensionKeys` | `string[]` | No |  |
| `defaultFilterDimensionValue` | `string` | No |  |
| `unfilteredEntry` | `any` | No | DashboardUnfilteredEntry defines the unfiltered selector option for a dimension control. |

### DashboardUnfilteredEntry

DashboardUnfilteredEntry defines the unfiltered selector option for a dimension control.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `textKey` | `string` | No |  |
| `breakdownDimensionKeys` | `string[]` | No |  |

### DashboardMetricReference

DashboardMetricReference identifies either a catalog metric or an inline
computed metric. A future saved custom metric key can be added to this oneof
without changing tile/document layout.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `metricKey` | `string` | No |  |
| `computedMetric` | `any` | No | DashboardComputedMetric is an inline dashboard authoring definition. It has no standalone resource or persistence lifecycle. |
| `variantSelections` | `DashboardMetricVariantSelection[]` | No |  |

### TileFilter

TileFilter is an authoring-time filter persisted as dashboard-owned dimension
keys and string values. Synthesis maps this shape to
`roblox.universeanalyticsquery.universeanalyticsquery.v1beta1.QueryFilter` and
`Dimension` in `universe_analytics_query.proto` (numeric dimension IDs are
resolved by the adapter, not stored on the dashboard document).
Keep this message wire-compatible with ComputedMetricFilter for schema-v1
computed sources.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `dimensionKey` | `string` | No |  |
| `values` | `string[]` | No |  |

### DashboardComputedMetric

DashboardComputedMetric is an inline dashboard authoring definition. It has
no standalone resource or persistence lifecycle.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `sources` | `DashboardComputedMetricSource[]` | No |  |
| `formula` | `string` | No |  |
| `displayName` | `string` | No |  |
| `l7Smoothing` | `boolean` | No |  |

### DashboardMetricVariantSelection

DashboardMetricVariantSelection selects one metric variant for a pseudo-dimension.
Keep this message wire-compatible with ComputedMetricVariantSelection for
schema-v1 computed sources.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `pseudoDimensionKey` | `string` | No |  |
| `variantKey` | `string` | No | Schema v3 uses AFC's stable key (e.g. SUM, COUNT_USER, AVERAGE), not its catalog value (e.g. Sum, CountUser, AVG). Older documents are normalized on migration. |

### DashboardComputedMetricSource

DashboardComputedMetricSource describes one named formula source.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `sourceKey` | `string` | No |  |
| `filters` | `ComputedMetricFilter[]` | No | Keep this message wire-compatible with TileFilter because field 3 is retained for schema-v1 documents. |
| `variantSelections` | `ComputedMetricVariantSelection[]` | No | Keep this message wire-compatible with DashboardMetricVariantSelection because field 4 is retained for schema-v1 documents. |
| `metricKey` | `string` | No |  |
| `metric` | `any` | No | Compatibility-only wire field for schema-v1 documents and already-compiled protobuf clients. New authors must use metric_key, filters, and variant_selections instead. |

### ComputedMetricFilter

ComputedMetricFilter is an authoring-time source filter. Keep this message
wire-compatible with TileFilter for schema-v1 computed sources.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `dimensionKey` | `string` | No |  |
| `values` | `string[]` | No |  |

### ComputedMetricVariantSelection

ComputedMetricVariantSelection selects one source metric variant. Keep this
message wire-compatible with DashboardMetricVariantSelection for schema-v1
computed sources.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `pseudoDimensionKey` | `string` | No |  |
| `variantKey` | `string` | No | Same stable-key identity as DashboardMetricVariantSelection in schema v3. |

### DashboardAtomicMetric

DashboardAtomicMetric is retained solely to deserialize schema-v1 dashboard
documents and clients. It is not part of the current authoring interface.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `metricKey` | `string` | No |  |
| `customEventMetric` | `any` | No | DashboardCustomEventMetric is the legacy custom-event source representation. |

### DashboardCustomEventMetric

DashboardCustomEventMetric is the legacy custom-event source representation.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `metricKey` | `string` | No |  |
| `customEventName` | `string` | No |  |
| `aggregation` | `any` | No | DashboardAggregation is the aggregation applied to a tile or series. Enum names follow proto conventions; synthesis adapters map to Creator Hub aggregation literal strings (`RAQIV2AggregationType`, summary-card literals, and `RAQIV2PercentileType`). Arbitrary `Percentile{N}` literals are not represented here and require a future contract extension. |

### DashboardTableTab

DashboardTableTab defines one table tab and its table component.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `tabKey` | `string` | No |  |
| `labelKey` | `string` | No |  |
| `table` | `any` | No | DashboardTable renders a table from dashboard chart data inputs. |

### DashboardChartDataSpec

DashboardChartDataSpec carries chart query inputs synthesized into RAQI requests.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `metrics` | `ChartTileMetric[]` | No | Cardinality rules for `metrics`:   - `metrics` MUST be non-empty.   - `DASHBOARD_CHART_TYPE_TABLE` accepts one or more metrics (one per rendered column).   - All other chart types accept exactly one metric in v1beta1. |
| `aggregation` | `any` | No | Default aggregation for metrics without a per-series override. |
| `breakdownDimensionKeys` | `string[]` | No | Ordered breakdown dimension keys. Synthesis maps to `QueryBreakdown` in `universe_analytics_query.proto` / RAQI breakdown lists. |
| `granularity` | `any` | No | Time bucketing for chart queries. |
| `filters` | `TileFilter[]` | No |  |

### ChartTileMetric

ChartTileMetric is one rendered series, table column, or metric input on a
chart tile. `metric` is required. `series_key` is required and must be unique
within a tile; renderers use it for stable color, legend, and column
identity across edits. If `aggregation` is set and not INVALID it overrides
`DashboardChartDataSpec.aggregation` for this series; otherwise the tile-level
value applies.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `metric` | `any` | No | DashboardMetricReference identifies either a catalog metric or an inline computed metric. A future saved custom metric key can be added to this oneof without changing tile/document layout. |
| `seriesKey` | `string` | No | Stable per-tile handle used for series identity, color assignment, and table column ordering. |
| `aggregation` | `any` | No | Optional per-series aggregation override. |
| `filters` | `TileFilter[]` | No | Optional filters scoped to this series or table column. These are combined conjunctively with ChartTile.data_spec.filters and, for computed metrics, the referenced source filters. Filters with the same dimension_key are also conjunctive; values within one TileFilter are alternatives (OR). |

### DashboardChartTab

DashboardChartTab defines one chart tab and its chart tile.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `tabKey` | `string` | No |  |
| `labelKey` | `string` | No |  |
| `chart` | `any` | No | ChartTile is a chart body tile. |

### DashboardChartSpec

DashboardChartSpec carries chart renderer options (not query/data inputs).

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `chartType` | `any` | No | DashboardChartType is the visual renderer requested by a chart tile. |
| `overlays` | `any` | No | ChartOverlays toggles optional chart adornments (display only, not query inputs). |
| `smoothing` | `any` | No | DashboardChartSmoothing controls optional chart smoothing. |

### ChartOverlays

ChartOverlays toggles optional chart adornments (display only, not query inputs).

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `genreBenchmark` | `boolean` | No |  |
| `similarExperienceBenchmark` | `boolean` | No |  |
| `topExperienceBenchmark` | `boolean` | No |  |
| `previousPeriod` | `boolean` | No | Legacy enablement bit. Writers that set previous_period_config must also set this field so older readers continue to render a default comparison. |
| `quota` | `boolean` | No |  |
| `previousPeriodConfig` | `any` | No | DashboardPreviousPeriodConfig stores an authored previous-period comparison. relative_offset and custom_start_time are optional independently so the contract can losslessly preserve Creator Hub editor state. |

### DashboardPreviousPeriodConfig

DashboardPreviousPeriodConfig stores an authored previous-period comparison.
relative_offset and custom_start_time are optional independently so the
contract can losslessly preserve Creator Hub editor state.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `relativeOffset` | `any` | No | DashboardComparisonRelativeOffset selects a fixed lookback for a configured previous-period comparison. |
| `customStartTime` | `any` | No |  |

### DashboardSurfaceControls

DashboardSurfaceControls defines the page-wide controls for a dashboard surface.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `timeRangeOptions` | `any` | No | DashboardTimeRangeOptions defines the available time range behavior for a surface. |
| `filterDimensionKeys` | `string[]` | No |  |
| `defaultFilters` | `TileFilter[]` | No |  |
| `breakdownDimensionKeys` | `string[]` | No |  |
| `defaultBreakdownDimensionKeys` | `string[]` | No |  |
| `granularity` | `any` | No | DashboardSurfaceGranularity defines granularity behavior for a dashboard surface. |
| `annotationOptions` | `any` | No | DashboardAnnotationOptions defines annotation controls for a dashboard surface. |

### DashboardTimeRangeOptions

DashboardTimeRangeOptions defines the available time range behavior for a surface.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `none` | `any` | No | DashboardNoTimeRangeOptions disables time range controls for a surface. |
| `dateRange` | `any` | No | DashboardDateRangeOptions defines date range control behavior for a surface. |

### DashboardSurfaceGranularity

DashboardSurfaceGranularity defines granularity behavior for a dashboard surface.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `fixed` | `any` | No | DashboardFixedGranularity fixes a surface to one granularity. |

### DashboardAnnotationOptions

DashboardAnnotationOptions defines annotation controls for a dashboard surface.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `defaultAnnotationTypeKeys` | `string[]` | No |  |
| `showAnnotationsControl` | `boolean` | No |  |

### DashboardFixedGranularity

DashboardFixedGranularity fixes a surface to one granularity.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `granularity` | `any` | No | DashboardGranularity is the time bucketing for chart and summary-card queries. Synthesis maps each value to Creator Hub `TimeInterval` literals and then to `MetricGranularity` in RAQI. INVALID is rejected on write. |

### DashboardDateRangeOptions

DashboardDateRangeOptions defines date range control behavior for a surface.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `defaultSelection` | `any` | No | DashboardDateRangeDefault selects the initial date range for a surface. |

### DashboardDateRangeDefault

DashboardDateRangeDefault selects the initial date range for a surface.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `relativeRangeKey` | `string` | No |  |
| `customRange` | `any` | No | DashboardCustomDateRange stores an explicit start and end time. |

### DashboardCustomDateRange

DashboardCustomDateRange stores an explicit start and end time.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `startTime` | `any` | No |  |
| `endTime` | `any` | No |  |

### DashboardFixedTab

DashboardFixedTab defines one tab in a fixed-tab dashboard page.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `tabKey` | `string` | No |  |
| `labelKey` | `string` | No |  |
| `surface` | `any` | No | DashboardSurface is a renderable analytics surface. It owns page-wide analytics context/controls as well as the layout nodes rendered inside that context. |

### Any

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `@type` | `string` | Yes |  |

### QueryBenchmarkResult

QueryBenchmarkResult is the response object for the benchmark query.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `values` | `MetricValue[]` | No | The benchmark series, one per percentile. |

### BenchmarkType

BenchmarkType is to store the type of benchmark.
`BENCHMARK_TYPE_SIMILARITY` compares against experiences with similar players.
`BENCHMARK_TYPE_GENRE` compares against experiences in the same genre, or against all experiences
when the universe has no genre or its genre doesn't qualify for genre benchmarks.
`BENCHMARK_TYPE_TOP_EXPERIENCES` compares against the top experiences on Roblox, and is the only type
for `DailyActiveUsers`, `DailyRevenue`, `MonthlyActiveUsers`, `PayingUsers`, `TotalPlayTimeHours`,
`UniqueAbuseReportSubmittersPer1000PlaytimeHours`, and `Visits`.

Values: `BENCHMARK_TYPE_INVALID`, `BENCHMARK_TYPE_GENRE`, `BENCHMARK_TYPE_SIMILARITY`, `BENCHMARK_TYPE_TOP_EXPERIENCES`

### BenchmarkObjective

BenchmarkObjective describes which direction is favorable for a metric.

Values: `BENCHMARK_OBJECTIVE_INVALID`, `BENCHMARK_OBJECTIVE_MAXIMIZE`, `BENCHMARK_OBJECTIVE_MINIMIZE`

### MetricValue

MetricValue content of a query result.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `breakdownValue` | `BreakdownValue[]` | No | The dimensions identifying the series. Always includes a `Percentile` dimension. `BENCHMARK_TYPE_TOP_EXPERIENCES` series also include the requested filters. |
| `dataPoints` | `DataPoint[]` | No | The data points for the breakdown. |

### BreakdownValue

BreakdownValue the breakdown in the query result.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `dimension` | `string` | No | The name of the dimension. |
| `value` | `string` | No | The value of the dimension. |
| `displayValue` | `string` | No | A display name for `value`. Not set in benchmark results. |

### DataPoint

DataPoint dataPoints in the resulting query.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `time` | `string` | No | The date of the benchmark value. |
| `value` | `number` | No | The benchmark value, in the metric's units. |
| `metadata` | `DataPointMetadata` | No | Where the benchmark value came from. |

### DataPointMetadata

DataPointMetadata metadata for a data point.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `benchmarkType` | `BenchmarkType` | No | The benchmark type this data point came from. Use this to tell genre and similarity values apart when `benchmark_type` is omitted. |
| `genre` | `string` | No | The genre compared against, set for `BENCHMARK_TYPE_GENRE` data points. `general` means all experiences. |

### BreakdownFilter

Filter to apply when searching for the benchmark value.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `dimension` | `string` | No | The name of the dimension. |
| `value` | `string` | No | The value of the dimension. |

### AlertStorage.AlertInterval

How frequently an alert condition is evaluated.

OneMinute

HalfHour

OneHour

OneDay

Values: `OneMinute`, `HalfHour`, `OneHour`, `OneDay`

### AnalyticsAlertControlPlane.Models.AlertQueryBreakdown

A set of dimensions used to group the metric query. When a breakdown is specified, the
alert evaluates each unique combination of dimension values independently and fires if any
group breaches the condition.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `dimensions` | `string[]` | Yes | Names of the dimensions to group by (e.g. `["platform", "age_bracket"]`). |

### AnalyticsAlertControlPlane.Models.AlertQueryFilter

A dimension filter applied to the metric query. Restricts the metric to rows where the
specified dimension matches one of the given values.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `dimension` | `string` | Yes | Name of the dimension to filter on (e.g. `platform`). |
| `values` | `string[]` | Yes | The allowed values for this dimension. A metric data point is included only if its dimension value is in this list. |

### AnalyticsAlertControlPlane.Models.AlertConditionInput

The threshold condition for an alert. Specifies the comparison operator, threshold value,
and how the metric value is derived before comparison.
            
On create, `operator`, `threshold`, and `evaluationMode` are all required.
On update (PATCH), the entire `condition` object is optional; when included, any
sub-field can be omitted to keep its current value.
            
`periodOffsetMultiplier` only applies when `evaluationMode` is
`PeriodOverPeriod`. It is ignored for `Absolute` conditions.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `operator` | `AlertStorage.ConditionOperator` | No |  |
| `threshold` | `number` | No | Numeric threshold the metric value is compared against. Required on create; optional on update. |
| `evaluationMode` | `AlertStorage.EvaluationMode` | No |  |
| `periodOffsetMultiplier` | `integer` | No | How many intervals back the comparison period is placed for `PeriodOverPeriod` evaluation. For example, a value of `1` (the default) compares the current interval against the immediately preceding interval. A value of `7` with a `OneDay` interval compares today against the same day last week. Only valid when `evaluationMode` is `PeriodOverPeriod`; omit or leave `null` for `Absolute` conditions. |

### AlertStorage.WebhookReceiverConfig

Webhook notification settings for an alert. When set, each webhook in the
`receivers` list will be called whenever the alert fires or resolves.
Set to `null` to disable webhook notifications for the alert.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `receivers` | `AlertStorage.WebhookReceiver[]` | No | List of webhook destinations to notify when the alert fires or resolves. Each entry references a webhook configuration you have created in the Webhook Delivery System. The list must contain unique entries with no duplicates. |

### AlertStorage.AlertConfigState

The current lifecycle state of an alert configuration.

Enabled

Disabled

PausedByRoblox

Syncing

Error

Values: `Enabled`, `Disabled`, `PausedByRoblox`, `Syncing`, `Error`

### AlertStorage.WebhookReceiver

A single webhook notification destination linked to an alert configuration.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `webhookConfigurationId` | `string` | Yes | The ID of the webhook configuration in the Webhook Delivery System. Must be a valid UUID and unique within the list on this alert configuration. |

### AlertStorage.ConditionOperator

Comparison operator used to evaluate whether a metric value breaches a threshold.

Gt

Gte

Lt

Lte

Values: `Gt`, `Gte`, `Lt`, `Lte`

### AlertStorage.EvaluationMode

Determines how the metric value is derived before being compared against the threshold.

Absolute

PeriodOverPeriod

Values: `Absolute`, `PeriodOverPeriod`

### AnalyticsAlertControlPlane.Models.FiringMetadataResponse

A snapshot of the alert condition at a specific evaluation, capturing the metric values
that were firing and any dimension breakdowns involved.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `filter` | `AnalyticsAlertControlPlane.Models.AlertQueryFilter[]` | No | Dimension filters that were active at this evaluation, if any. |
| `breakdown` | `AnalyticsAlertControlPlane.Models.AlertQueryBreakdown[]` | No | Grouping dimensions that were active at this evaluation, if any. |
| `condition` | `AlertStorage.AlertCondition` | Yes |  |
| `firingCondition` | `AnalyticsAlertControlPlane.Models.FiringConditionResponse[]` | Yes | The specific metric values and dimension combinations that caused the condition to fire. |

### AnalyticsAlertControlPlane.Models.AlertConfigSummary

Key fields of the alert configuration that triggered an incident.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `string` | Yes | Unique identifier of the alert configuration (string-encoded 64-bit integer). |
| `name` | `string` | Yes | Display name of the alert configuration. |
| `metric` | `string` | Yes | Name of the metric this alert evaluates. |
| `severity` | `AlertStorage.Severity` | Yes |  |
| `description` | `string` | No | Optional free-text description of the alert's purpose. |
| `interval` | `AlertStorage.AlertInterval` | Yes |  |
| `filter` | `AnalyticsAlertControlPlane.Models.AlertQueryFilter[]` | No | Dimension filters applied to the metric query, if any. |
| `breakdown` | `AnalyticsAlertControlPlane.Models.AlertQueryBreakdown[]` | No | Grouping dimensions for the metric query, if any. |
| `condition` | `AlertStorage.AlertCondition` | Yes |  |

### AlertStorage.AlertCondition

The threshold condition that determines when an alert fires.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `operator` | `AlertStorage.ConditionOperator` | Yes |  |
| `threshold` | `number` | Yes | Numeric threshold the metric value is compared against. |
| `evaluationMode` | `AlertStorage.EvaluationMode` | Yes |  |
| `periodOffsetMultiplier` | `integer` | No | How many intervals back the comparison period is placed for `PeriodOverPeriod` evaluation. A value of `1` compares against the immediately preceding interval; a value of `7` with a `OneDay` interval compares against the same day last week. `null` for `Absolute` conditions. |

### AnalyticsAlertControlPlane.Models.FiringConditionResponse

A single metric value that breached the alert threshold, optionally scoped to a specific
dimension value when the alert uses a breakdown.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `firingValue` | `number` | Yes | The metric value that exceeded the threshold at the time of evaluation. |
| `firingDimension` | `AnalyticsAlertControlPlane.Models.FiringDimensionResponse` | No |  |

### AnalyticsAlertControlPlane.Models.FiringDimensionResponse

A dimension name/value pair that identifies which slice of the metric was firing.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `dimension` | `string` | Yes | Name of the dimension (e.g. `platform`). |
| `value` | `string` | Yes | Value of the dimension for the slice that was firing (e.g. `Mobile`). |