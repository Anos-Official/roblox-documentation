<!-- Source: https://create.roblox.com/docs/en-us/cloud/reference/features/thumbnail-personalization.md -->

---
name: "Thumbnail Personalization"
last_updated: 2026-11-19T20:54:14Z
type: feature
api_base_url: "https://apis.roblox.com"
endpoints: 7
auth: [api-key, oauth2, cookie]
description: "Upload and manage creator-provided homepage thumbnail variants for an experience, then choose which player groups see each variant"
---

# Thumbnail Personalization

Upload and manage creator-provided homepage thumbnail variants for an experience, then choose which player groups see each variant. Unlike the Thumbnails feature, these APIs manage homepage images and targeting rules instead of generating or retrieving standard Roblox thumbnails. See [Manage experience icons and thumbnails](/cloud/guides/experience-icons-and-thumbnails) for the other types of icon/thumbnail.

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

### GET `/thumbnail-personalization-api/v1/universes/{universeId}/personalization` [EXPERIMENTAL]

Gets a page of thumbnail personalization configurations for a universe.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `universe.thumbnail:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes | The identifier of the universe whose configurations are returned. |
| `status` | query | `PersonalizedConfigStatus` | Yes | The configuration status to return. Valid values: `Active`, `Inactive` |
| `limit` | query | `integer` | No | The maximum number of configurations to return. |
| `cursor` | query | `string` | No | The cursor from a previous response, if any. |

**Responses:**

- `200`: Success → `FindPersonalizedConfigsResponse`
- `400`: Bad Request → `string`
- `401`: Unauthorized → `string`
- `403`: Forbidden → `string`
- `500`: Server Error

**Response fields** (`FindPersonalizedConfigsResponse`)

See [FindPersonalizedConfigsResponse](#findpersonalizedconfigsresponse) in Models.

**Response example:**
```json
{
  "personalizedConfigs": [
    {
      "id": "...",
      "personalizedConfigStatus": "...",
      "createdUtc": "...",
      "thumbnails": "...",
      "lastServedUtc": "..."
    }
  ],
  "nextCursor": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/thumbnail-personalization-api/v1/universes/{UNIVERSEID}/personalization?status={VALUE}"
```

### POST `/thumbnail-personalization-api/v1/universes/{universeId}/personalization/create` [EXPERIMENTAL]

Creates a new active thumbnail personalization configuration for a universe.
This deactivates the current active configuration, and the new configuration starts its own statistics.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `universe.thumbnail:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes | The identifier of the universe that owns the configuration. |

**Request Body:** `application/json-patch+json` — Type: `CreateThumbnailPersonalizationRequest`

See [CreateThumbnailPersonalizationRequest](#createthumbnailpersonalizationrequest) in Models.

**Request example:**
```json
{
  "homepageThumbnailIds": [
    "string"
  ]
}
```

**Responses:**

- `200`: Success → `string`
- `400`: Bad Request → `string`
- `401`: Unauthorized → `string`
- `403`: Forbidden → `string`
- `500`: Server Error

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 50/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/thumbnail-personalization-api/v1/universes/{UNIVERSEID}/personalization/create" \
  -H "Content-Type: application/json" \
  -d '{
  "homepageThumbnailIds": [
    "string"
  ]
}'
```

### POST `/thumbnail-personalization-api/v1/universes/{universeId}/personalization/update` [EXPERIMENTAL]

Replaces the homepage thumbnails in an active personalization configuration without changing its identifier
or existing statistics.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `universe.thumbnail:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes | The identifier of the universe that owns the configuration. |

**Request Body:** `application/json-patch+json` — Type: `UpdateThumbnailPersonalizationRequest`

See [UpdateThumbnailPersonalizationRequest](#updatethumbnailpersonalizationrequest) in Models.

**Request example:**
```json
{
  "homepageThumbnailIds": [
    "string"
  ],
  "id": "string"
}
```

**Responses:**

- `200`: Success → `string`
- `400`: Bad Request → `string`
- `401`: Unauthorized → `string`
- `403`: Forbidden → `string`
- `404`: Not Found
- `500`: Server Error

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 50/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/thumbnail-personalization-api/v1/universes/{UNIVERSEID}/personalization/update" \
  -H "Content-Type: application/json" \
  -d '{
  "homepageThumbnailIds": [
    "string"
  ],
  "id": "string"
}'
```

### GET `/thumbnail-personalization-api/v1/universes/{universeId}/thumbnails` [EXPERIMENTAL]

Gets a page of homepage thumbnails for a universe.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `universe.thumbnail:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes | The identifier of the universe whose thumbnails are returned. |
| `limit` | query | `integer` | No | The maximum number of thumbnails to return. |
| `nextCursor` | query | `string` | No | The cursor from a previous response, if any. |

**Responses:**

- `200`: Success → `FindThumbnailsResponse`
- `400`: Bad Request → `string`
- `401`: Unauthorized → `string`
- `403`: Forbidden → `string`
- `500`: Server Error

**Response fields** (`FindThumbnailsResponse`)

See [FindThumbnailsResponse](#findthumbnailsresponse) in Models.

**Response example:**
```json
{
  "homepageThumbnails": [
    {
      "homepageThumbnailId": "...",
      "assetId": "...",
      "moderationStatus": "...",
      "personalizedConfigStatus": "...",
      "homepageThumbnailStatus": "..."
    }
  ],
  "nextCursor": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/thumbnail-personalization-api/v1/universes/{UNIVERSEID}/thumbnails"
```

### DELETE `/thumbnail-personalization-api/v1/universes/{universeId}/thumbnails` [EXPERIMENTAL]

Deletes homepage thumbnails from a universe.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `universe.thumbnail:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes | The identifier of the universe that owns the thumbnails. |
| `homepageThumbnailIds` | query | `string[]` | Yes | The identifiers of the homepage thumbnails to delete. |

**Responses:**

- `200`: Success → `object`
- `400`: Bad Request → `string`
- `401`: Unauthorized → `string`
- `403`: Forbidden → `string`
- `500`: Server Error

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 50/minute

**Example:**
```bash
curl -X DELETE -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/thumbnail-personalization-api/v1/universes/{UNIVERSEID}/thumbnails?homepageThumbnailIds={VALUE}"
```

### POST `/thumbnail-personalization-api/v1/universes/{universeId}/thumbnails/uploads` [EXPERIMENTAL]

Uploads one or more images to create homepage thumbnails for a universe.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `universe.thumbnail:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes | The identifier of the universe that owns the thumbnails. |

**Request Body:** `multipart/form-data` — Type: `object`

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `files` | `string[]` | Yes |  |

**Request example:**
```json
{
  "files": [
    "string"
  ]
}
```

**Responses:**

- `200`: Success → `UploadThumbnailsResponse`
- `400`: Bad Request → `string`
- `401`: Unauthorized → `string`
- `403`: Forbidden → `string`
- `500`: Server Error

**Response fields** (`UploadThumbnailsResponse`)

See [UploadThumbnailsResponse](#uploadthumbnailsresponse) in Models.

**Response example:**
```json
{
  "fileToOperationIdDict": "..."
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 50/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/thumbnail-personalization-api/v1/universes/{UNIVERSEID}/thumbnails/uploads" \
  -F "files=["string"]"
```

### GET `/thumbnail-personalization-api/v1/universes/{universeId}/thumbnails/uploads/status` [EXPERIMENTAL]

Gets the processing status of homepage thumbnail upload operations.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `universe.thumbnail:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes | The identifier of the universe that owns the uploads. |
| `operationIds` | query | `string[]` | Yes | The upload operation IDs to query. |

**Responses:**

- `200`: Success → `UploadThumbnailsStatusResponse`
- `400`: Bad Request → `string`
- `401`: Unauthorized → `string`
- `403`: Forbidden → `string`
- `500`: Server Error

**Response fields** (`UploadThumbnailsStatusResponse`)

See [UploadThumbnailsStatusResponse](#uploadthumbnailsstatusresponse) in Models.

**Response example:**
```json
{
  "uploadStatus": 1,
  "uploadThumbnailStatusDict": "..."
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/thumbnail-personalization-api/v1/universes/{UNIVERSEID}/thumbnails/uploads/status?operationIds={VALUE}"
```

## Models

### PersonalizedConfigStatus

The lifecycle status of a thumbnail personalization configuration.

Values: `Active`, `Inactive`

### FindPersonalizedConfigsResponse

A page of thumbnail personalization configurations.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `personalizedConfigs` | `ThumbnailPersonalizedConfig[]` | Yes | The personalization configurations matching the requested universe and status. |
| `nextCursor` | `string` | No | The cursor to use for the next page of results. |

### CreateThumbnailPersonalizationRequest

The request to create a thumbnail personalization configuration.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `homepageThumbnailIds` | `string[]` | Yes | The homepage thumbnail identifiers to include in the configuration. Up to five are supported. |

### UpdateThumbnailPersonalizationRequest

The request to update a thumbnail personalization configuration.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `homepageThumbnailIds` | `string[]` | Yes | The homepage thumbnail identifiers to include in the configuration. Up to five are supported. |
| `id` | `string` | Yes | The identifier of the active personalization configuration to update. |

### FindThumbnailsResponse

A page of homepage thumbnails for a universe.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `homepageThumbnails` | `HomepageThumbnail[]` | Yes | The homepage thumbnails in this page. |
| `nextCursor` | `string` | No | The cursor to use for the next page of results. |

### UploadThumbnailsResponse

The operations created for uploaded homepage thumbnail files.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `fileToOperationIdDict` | `object` | Yes | A mapping from each uploaded file name to the operation ID used to track its processing. |

### UploadThumbnailsStatusResponse

The processing status of homepage thumbnail upload operations.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `uploadStatus` | `UploadStatus` | Yes | The aggregate status of the requested upload operations. |
| `uploadThumbnailStatusDict` | `object` | Yes | A mapping from each completed operation ID to its uploaded thumbnail details. |

### UploadStatus

The aggregate processing status of a set of homepage thumbnail uploads.

Values: `1`, `2`

### UploadThumbnailStatus

The result of a completed homepage thumbnail upload operation.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `homepageThumbnailId` | `string` | No | The unique identifier of the created homepage thumbnail. |
| `assetId` | `integer` | No | The identifier of the uploaded image asset. |
| `moderationStatus` | `ModerationStatus` | No | The moderation status of the uploaded image asset. |

### ModerationStatus

The moderation status of a homepage thumbnail's image asset.

Values: `Reviewing`, `Rejected`, `Approved`, `Unspecified`

### HomepageThumbnail

A homepage thumbnail associated with a universe.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `homepageThumbnailId` | `string` | Yes | The unique identifier of the homepage thumbnail. |
| `assetId` | `integer` | Yes | The identifier of the image asset used by the thumbnail. |
| `moderationStatus` | `ModerationStatus` | Yes | The moderation status of the thumbnail's image asset. |
| `personalizedConfigStatus` | `PersonalizedConfigStatus` | Yes | Indicates whether the thumbnail belongs to an active personalization configuration. |
| `homepageThumbnailStatus` | `HomepageThumbnailStatus` | Yes | The availability status of the homepage thumbnail. |

### HomepageThumbnailStatus

The availability status of a homepage thumbnail.

Values: `Active`, `Spammy`

### ThumbnailPersonalizedConfig

A thumbnail personalization configuration.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `string` | Yes | The unique identifier of the personalization configuration. |
| `personalizedConfigStatus` | `PersonalizedConfigStatus` | Yes | The lifecycle status of the personalization configuration. |
| `createdUtc` | `string` | Yes | The UTC date and time when the configuration was created. |
| `thumbnails` | `PersonalizedThumbnail[]` | Yes | The homepage thumbnails included in the configuration. |
| `lastServedUtc` | `string` | No | The UTC date and time when the configuration last served a thumbnail, when available. |

### PersonalizedThumbnail

A homepage thumbnail and its status within a personalization configuration.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `homepageThumbnailId` | `string` | Yes | The unique identifier of the homepage thumbnail. |
| `assetId` | `integer` | Yes | The identifier of the image asset used by the thumbnail. |
| `personalizedThumbnailStatus` | `PersonalizedThumbnailStatus` | Yes | The thumbnail's status within the personalization configuration. |
| `homepageThumbnailStatus` | `HomepageThumbnailStatus` | Yes | The availability status of the homepage thumbnail. |

### PersonalizedThumbnailStatus

The status of a thumbnail within a personalization configuration.

Values: `Active`, `Inactive`