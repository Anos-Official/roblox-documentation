<!-- Source: https://create.roblox.com/docs/cloud/reference/features/service-efficiency.md -->

---
name: "Service Efficiency"
last_updated: 2026-11-20T18:47:47Z
type: feature
api_base_url: "https://apis.roblox.com"
endpoints: 3
auth: [api-key, oauth2, cookie]
description: "Manage Service Efficiency accounts and billing for users and groups, and configure consumer settings for a universe"
---

# Service Efficiency

Manage Service Efficiency accounts and billing for users and groups, and configure consumer settings for a universe.

Common use cases include:

- Account management: [Retrieve](#ServiceEfficiencyApi_GetAccountForUser) or [update](#ServiceEfficiencyApi_UpdateAccountForUser) a user's account, or [retrieve](#ServiceEfficiencyApi_GetAccountForGroup) or [update](#ServiceEfficiencyApi_UpdateAccountForGroup) a group's account
- Billing: [Review billing activity](#ServiceEfficiencyApi_GetBillingActivitiesByUser) and [retrieve bills](#ServiceEfficiencyApi_GetBillByUser) for a user, or [review billing activity](#ServiceEfficiencyApi_GetBillingActivitiesByGroup) and [retrieve bills](#ServiceEfficiencyApi_GetBillByGroup) for a group
- Eligibility and access: [Check user](#ServiceEfficiencyApi_CheckEligibilityForUser) or [group](#ServiceEfficiencyApi_CheckEligibilityForGroup) eligibility, and [check access](#ServiceEfficiencyApi_IsAllowed) for the current user
- Payment profiles: [List](#ServiceEfficiencyApi_ListPaymentProfilesByUser), [create](#ServiceEfficiencyApi_CreatePaymentProfileForUser), or [delete](#ServiceEfficiencyApi_DeletePaymentProfileForUser) a user's payment profile
- Payment methods: [Retrieve](#ServiceEfficiencyApi_GetServiceEfficiencyPaymentMethodForUser) or [set](#ServiceEfficiencyApi_SetServiceEfficiencyPaymentMethodForUser) a user's payment method, or [retrieve](#ServiceEfficiencyApi_GetServiceEfficiencyPaymentMethodForGroup) or [set](#ServiceEfficiencyApi_SetServiceEfficiencyPaymentMethodForGroup) a group's payment method
- Manual payments: [Submit a payment for a user](#ServiceEfficiencyApi_SubmitManualPaymentForUser) or [group](#ServiceEfficiencyApi_SubmitManualPaymentForGroup)
- Universe service management: [Retrieve](#ServiceEfficiencyApi_GetConsumerConfigurationsByUniverse) or [update](#ServiceEfficiencyApi_UpdateConsumerConfigurationsByUniverse) consumer configuration, and [retrieve live monthly free-tier usage](#ServiceEfficiencyApi_GetConsumerUsages) for a universe

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

### GET `/service-efficiency-api/v1/configurations/universes/{universeId}` [EXPERIMENTAL]

Operation to Get ConsumerConfiguration for a universe.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `extended-services:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |

**Responses:**

- `200`: OK → `ConsumerConfigurationResponse`
- `400`: Bad Request
- `401`: Unauthorized
- `403`: Forbidden
- `404`: Not Found
- `500`: Internal Server Error
- `503`: Service Unavailable

**Response fields** (`ConsumerConfigurationResponse`)

See [ConsumerConfigurationResponse](#consumerconfigurationresponse) in Models.

**Response example:**
```json
{
  "accountState": "Invalid",
  "accountInfoComplete": false,
  "serviceConfigurations": [
    {
      "serviceId": "...",
      "monthlyBudget": "...",
      "resourceConfigurations": "...",
      "budgetLevel": "..."
    }
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 5000/minute, perOauth2Authorization: 5000/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/service-efficiency-api/v1/configurations/universes/{UNIVERSEID}"
```

### PATCH `/service-efficiency-api/v1/configurations/universes/{universeId}` [EXPERIMENTAL]

Operation to Update ConsumerConfiguration for a universe.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `extended-services:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |

**Request Body:** `application/json-patch+json` — Type: `ConsumerConfigurationRequest`

See [ConsumerConfigurationRequest](#consumerconfigurationrequest) in Models.

**Request example:**
```json
{
  "serviceConfigurations": [
    {
      "serviceId": "...",
      "monthlyBudget": "...",
      "resourceConfigurations": "...",
      "budgetLevel": "..."
    }
  ]
}
```

**Responses:**

- `200`: OK → `ConsumerConfigurationResponse`
- `400`: Bad Request
- `401`: Unauthorized
- `403`: Forbidden
- `404`: Not Found
- `500`: Internal Server Error
- `503`: Service Unavailable

**Response fields** (`ConsumerConfigurationResponse`)

See [ConsumerConfigurationResponse](#consumerconfigurationresponse) in Models.

**Response example:**
```json
{
  "accountState": "Invalid",
  "accountInfoComplete": false,
  "serviceConfigurations": [
    {
      "serviceId": "...",
      "monthlyBudget": "...",
      "resourceConfigurations": "...",
      "budgetLevel": "..."
    }
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 5000/minute, perOauth2Authorization: 5000/minute

**Example:**
```bash
curl -X PATCH -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/service-efficiency-api/v1/configurations/universes/{UNIVERSEID}" \
  -H "Content-Type: application/json" \
  -d '{
  "serviceConfigurations": [
    {
      "serviceId": "...",
      "monthlyBudget": "...",
      "resourceConfigurations": "...",
      "budgetLevel": "..."
    }
  ]
}'
```

### GET `/service-efficiency-api/v1/usages/universes/{universeId}` [EXPERIMENTAL]

Returns the live monthly free-tier usage for a universe, used by the Service Unlock page.
Wraps the cloud-pricing-billing `GetConsumerFreeTierUsage` RPC.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `extended-services:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes | Universe id. |

**Responses:**

- `200`: OK → `FreeTierUsagesResponse`
- `400`: Bad Request
- `401`: Unauthorized
- `403`: Forbidden
- `404`: Not Found
- `500`: Internal Server Error
- `503`: Service Unavailable

**Response fields** (`FreeTierUsagesResponse`)

See [FreeTierUsagesResponse](#freetierusagesresponse) in Models.

**Response example:**
```json
{
  "monthStartUtc": "2024-01-01T00:00:00Z",
  "usages": [
    {
      "serviceId": "...",
      "resourceId": "...",
      "monthlyFreeUnits": "...",
      "consumed": "...",
      "remaining": "...",
      "lastUpdatedUtc": "..."
    }
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 5000/minute, perOauth2Authorization: 5000/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/service-efficiency-api/v1/usages/universes/{UNIVERSEID}"
```

## Models

### ConsumerConfigurationResponse

Response object for consumer configuration.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `accountState` | `ResponseAccountState` | No | Gets or sets the account state. |
| `accountInfoComplete` | `boolean` | No | Gets or sets a value indicating whether account information is complete. |
| `serviceConfigurations` | `ServiceConfiguration[]` | Yes | Gets or sets the service configuration lists. |

### ConsumerConfigurationRequest

Request for updating consumer configuration.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `serviceConfigurations` | `ServiceConfiguration[]` | Yes | Gets or sets the service configuration lists. |

### FreeTierUsagesResponse

Response object for free-tier usage on the Service Unlock page.
One entry per resource that opts in to a monthly free tier (i.e. monthly_free_units > 0).

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `monthStartUtc` | `string` | No | Gets or sets UTC midnight of the first day of the month covered by this response. |
| `usages` | `FreeTierUsageItem[]` | No | Gets or sets per-resource free-tier usage snapshots. |

### FreeTierUsageItem

Per-resource free-tier usage snapshot.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `serviceId` | `string` | No | Gets or sets the service identifier (e.g. "rcc"). |
| `resourceId` | `string` | No | Gets or sets the resource identifier (e.g. "ccu-cores"). |
| `monthlyFreeUnits` | `integer` | No | Gets or sets the current monthly free-tier cap from pricing config. |
| `consumed` | `number` | No | Gets or sets the live month-to-date consumed units. |
| `remaining` | `number` | No | Gets or sets the live month-to-date remaining units. |
| `lastUpdatedUtc` | `string` | No | Gets or sets the time at which this snapshot was projected. |

### ServiceConfiguration

Configuration of a service, including whether unlocked and budget.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `serviceId` | `string` | Yes | Gets or sets the service ID. |
| `monthlyBudget` | `ServiceEfficiencyApi.Money` | No | Gets or sets the monthly budget. |
| `resourceConfigurations` | `ResourceConfiguration[]` | Yes | Gets or sets the list of resource configurations. |
| `budgetLevel` | `BudgetLevel` | Yes | Gets or sets the allowed budget level for this service. This value can only be set in the GetConsumerConfiguration endpoint, it will be ignored in the UpdateConsumerConfiguration endpoint. |

### ServiceEfficiencyApi.Money

Temporary until https://roblox.atlassian.net/browse/ICSC-1360 is done.
Will be replaced by google.type.Money

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `currencyCode` | `string` | No | The three-letter currency code defined in ISO 4217. |
| `units` | `integer` | No | The whole units of the amount. For example if `currencyCode` is `"USD"`, then 1 unit is one US dollar. |
| `nanos` | `integer` | No | Number of nano (10^-9) units of the amount. The value must be between -999,999,999 and +999,999,999 inclusive. If `units` is positive, `nanos` must be positive or zero. If `units` is zero, `nanos` can be positive, zero, or negative. If `units` is negative, `nanos` must be negative or zero. For example $-1.75 is represented as `units`=-1 and `nanos`=-750,000,000. |

### ResourceConfiguration

Configuration for a resource, like Memory Stores request unit.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `resourceId` | `string` | Yes | Gets or sets the resource ID. |
| `unlocked` | `boolean` | Yes | Gets or sets a value indicating whether the resource has unlocked additional usage. |
| `monthlyBudget` | `ServiceEfficiencyApi.Money` | No | Gets or sets the monthly budget. |
| `unitCost` | `ServiceEfficiencyApi.Money` | Yes | Gets or sets the unit cost of this resource. |
| `price` | `Price` | Yes | Gets or sets the price of this resource. |

### BudgetLevel

Indicates the allowed budget levels for a service.

Values: `ResourceOnly`, `ServiceOnly`

### Price

Describes the price of a resource.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `cost` | `ServiceEfficiencyApi.Money` | No | Cost of the resource. |
| `unitAmount` | `integer` | No | The number of units of the resource to which the cost applies. For example, if `cost` is 0.0044 and `unit_amount` is 1000000, the cost is $0.0044 per million of units. The split between `cost` and `unit_amount` should reflect how we refer to the price in real life, e.g. the above example reflects how we talk about the price of UMS request units ($0.0044 per million request units). |

### ResponseAccountState

Account State in the HTTP response.

Values: `Invalid`, `Normal`, `Overdue`, `Suspended`