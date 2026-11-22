<!-- Source: https://create.roblox.com/docs/en-us/cloud/reference/features/assets.md -->

---
name: "Assets"
last_updated: 2026-11-20T18:47:47Z
type: feature
api_base_url: "https://apis.roblox.com"
endpoints: 136
auth: [api-key, oauth2, cookie]
description: "Upload, update, and manage assets programmatically"
---

# Assets

Upload, update, and manage assets programmatically. Supported asset types include Audio, Decals, Images, Models, Meshes, and Videos. For detailed implementation, see the [Assets Usage Guide](/cloud/guides/usage-assets). To update a place icon or experience detail page thumbnails, see [Manage experience icons and thumbnails](/cloud/guides/experience-icons-and-thumbnails).

Common use cases include:

- Asset creation: [Create an asset](#Assets_CreateAsset), then [poll the operation endpoint](#Assets_GetOperation) for completion
- Asset retrieval: [Retrieve asset content](#get_asset_delivery_api_v1_assetId__assetId_) or [a specific version of it](#get_asset_delivery_api_v1_assetId__assetId__version__versionNumber_) for external tools
- Versioning: [Manage asset versions](#Assets_ListAssetVersions) with [rollback](#Assets_RollbackAssetVersion) support

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

### GET `/asset-delivery-api/v1/assetId/{assetId}`

Retrieves an asset by its ID with OpenCloud auth.

Returns an object containing a `location` property which is a temporary CDN URL for the asset content. All asset types are supported.
You should request that URL with the `Accept-Encoding: gzip` header and decompress the result if the response is gzipped. If you are using cURL, the `--compressed` flag will automate these steps for you.
This endpoint is expected to be called with API key authentication through `apis.roblox.com/asset-delivery-api/v1/assetId/{assetId}`.
While you are able to make requests to this endpoint with Cookie authentication via `assetdelivery.roblox.com/v1/openCloud/assetId/{assetId}`, we highly discourage use this way.
Expect unannounced removal of this second route in the future.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `legacy-asset:manage`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetId` | path | `integer` | Yes | The ID of the asset to retrieve. |
| `Accept-Encoding` | header | `string` | No | The Accept-Encoding header value specifying compression formats (e.g., "gzip, deflate"). Defaults to "gzip, deflate" if not provided. |
| `Roblox-Place-Id` | header | `integer` | No | The Roblox-Place-Id header value identifying the place making the request. |
| `AssetType` | header | `string` | No | The AssetType header value specifying the expected asset type. |
| `AssetFormat` | header | `string` | No | The AssetFormat header value specifying the desired asset format. Overridden by robloxAssetFormat if both are provided. |
| `Roblox-AssetFormat` | header | `string` | No | The Roblox-AssetFormat header value specifying the preferred Roblox-specific asset format. Takes precedence over assetFormat. |
| `Roblox-Usage-Context` | header | `string` | No |  |
| `skipSigningScripts` | query | `boolean` | No | Whether to skip script signing for the returned asset. Used for script assets that don't require signing. |
| `clientInsert` | query | `integer` | No | Set to 1 to indicate this is a client insert request. |
| `scriptinsert` | query | `integer` | No | Set to 1 to indicate this is a script insert request. |
| `modulePlaceId` | query | `integer` | No | The place ID of the module making the request. |
| `serverplaceid` | query | `integer` | No | The server place ID making the request. |
| `expectedAssetType` | query | `string` | No | The expected asset type as a fallback when assetType header is not provided. |
| `doNotFallbackToBaselineRepresentation` | query | `boolean` | No | Whether to prevent fallback to baseline representation when specific content representations are not available. |
| `contentRepresentationPriorityList` | query | `string` | No | Base64URL-encoded JSON string specifying the priority list of desired content representations (format, version, fidelity). |
| `accessContext` | query | `string` | No |  |

**Responses:**

- `200`: OK
- `401`: 0: Authorization has been denied for this request.

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 1000/minute, perOauth2Authorization: 1000/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/asset-delivery-api/v1/assetId/{ASSETID}"
```

### GET `/asset-delivery-api/v1/assetId/{assetId}/version/{versionNumber}`

Retrieves an asset by its ID and version number with OpenCloud auth.

Refer to the assetId endpoint for details on usage.
This endpoint is expected to be called with API key authentication through `apis.roblox.com/asset-delivery-api/v1/assetId/{assetId}/version/{versionNumber}`.
While you are able to make requests to this endpoint with Cookie authentication via `assetdelivery.roblox.com/v1/openCloud/assetId/{assetId}/version/{versionNumber}`, we highly discourage use this way.
Expect unannounced removal of this second route in the future.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `legacy-asset:manage`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetId` | path | `integer` | Yes | The ID of the asset to retrieve. |
| `versionNumber` | path | `integer` | Yes | The version number of the asset to retrieve. |
| `Accept-Encoding` | header | `string` | No |  |
| `Roblox-Place-Id` | header | `integer` | No |  |
| `AssetType` | header | `string` | No |  |
| `AssetFormat` | header | `string` | No |  |
| `Roblox-AssetFormat` | header | `string` | No |  |
| `Roblox-Usage-Context` | header | `string` | No |  |
| `skipSigningScripts` | query | `boolean` | No |  |
| `clientInsert` | query | `integer` | No |  |
| `scriptinsert` | query | `integer` | No |  |
| `modulePlaceId` | query | `integer` | No |  |
| `serverplaceid` | query | `integer` | No |  |
| `expectedAssetType` | query | `string` | No |  |
| `doNotFallbackToBaselineRepresentation` | query | `boolean` | No |  |
| `contentRepresentationPriorityList` | query | `string` | No |  |
| `accessContext` | query | `string` | No |  |

**Responses:**

- `200`: OK
- `401`: 0: Authorization has been denied for this request.

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 1000/minute, perOauth2Authorization: 1000/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/asset-delivery-api/v1/assetId/{ASSETID}/version/{VERSIONNUMBER}"
```

### PATCH `/asset-permissions-api/v1/assets/permissions` [BETA]

Grant a subject permission to multiple assets.
            
Authorization is required to grant permissions to the subject and asset IDs in the request.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `asset-permissions:write`

**Request Body:** `application/json-patch+json` — Type: `BatchGrantPermissionsRequest`

See [BatchGrantPermissionsRequest](#batchgrantpermissionsrequest) in Models.

**Request example:**
```json
{
  "subjectType": "Invalid",
  "subjectId": "string",
  "action": "Invalid",
  "requests": [
    {
      "assetId": "...",
      "grantToDependencies": "...",
      "parentVersionNumber": "..."
    }
  ],
  "assetIds": [
    0
  ],
  "enableDeepAccessCheck": false
}
```

**Responses:**

- `200`: OK → `BatchGrantPermissionsResponse`
- `400`: Bad Request → `AssetPermissions.ErrorResponse`
- `403`: Forbidden → `AssetPermissions.ErrorResponse`
- `500`: Internal Server Error → `AssetPermissions.ErrorResponse`

**Response fields** (`BatchGrantPermissionsResponse`)

See [BatchGrantPermissionsResponse](#batchgrantpermissionsresponse) in Models.

**Response example:**
```json
{
  "successAssetIds": [
    0
  ],
  "errors": [
    {
      "assetId": "...",
      "code": "..."
    }
  ]
}
```

**Error handling:** `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute

**Example:**
```bash
curl -X PATCH -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/asset-permissions-api/v1/assets/permissions" \
  -H "Content-Type: application/json" \
  -d '{
  "subjectType": "Invalid",
  "subjectId": "string",
  "action": "Invalid",
  "requests": [
    {
      "assetId": "...",
      "grantToDependencies": "...",
      "parentVersionNumber": "..."
    }
  ],
  "assetIds": [
    0
  ],
  "enableDeepAccessCheck": false
}'
```

### POST `/assets/v1/assets` [BETA]

Creates an asset with provided content and metadata.

Creates an asset with provided content and metadata.

You can't add `SocialLink` objects when you create an asset. Instead, use [Update Asset](#Assets_UpdateAsset).

Provide the `Asset`, binary asset file path, and [content type](/cloud/guides/usage-assets.md#supported-asset-types-and-limits) in the form data.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `asset:write`

**Request Body:** `multipart/form-data` — Type: `object`

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `fileContent` | `string` | Yes | The binary asset file path and the content type. See [Asset types and limits](/cloud/guides/usage-assets.md#supported-as |
| `additionalParameters` | `object` | No | Optional: Additional parameters to be sent with the request can be included here. |
| `request` | [AssetsUploadApi.Asset](#assetsuploadapi-asset) | Yes | Asset attributes to create. |
| `request.path` | `string` | No | The returned resource path of the asset. Format: `assets/{assetId}`. Example: `assets/2205400862`. |
| `request.revisionId` | `string` | No | *(immutable)* Revision ID of the asset. Equivalent to `versionNumber`. Every change of the asset automatically com |
| `request.revisionCreateTime` | `string` | No | The creation timestamp of the current revision. |
| `request.assetId` | `string` | No | The unique identifier of the asset. Required for [Update Asset](#Assets_UpdateAsset). |
| `request.displayName` | `string` | No | Display name of the asset. Required for [Create Asset](#Assets_CreateAsset). |
| `request.description` | `string` | No | The description of the asset. Limit to 1000 characters. Required for [Create Asset](#Assets_CreateAs |

**Request example:**
```json
{
  "fileContent": "string",
  "additionalParameters": "...",
  "request": {
    "path": "string",
    "revisionId": "string",
    "revisionCreateTime": "2024-01-01T00:00:00Z",
    "assetId": "string",
    "displayName": "string",
    "description": "string"
  }
}
```

**Responses:**

- `200`: Returns the Operation ID for checking the creation status. → `AssetsUploadApi.Operation`
- `400`: Invalid argument. Failed to parse the request or the file. → `AssetsUploadApi.Status`
- `401`: The API key is not valid for this operation / You don't have the authorization. → `AssetsUploadApi.Status`
- `403`: Doesn't have the required permission. → `AssetsUploadApi.Status`
- `500`: Server internal error / Unknown error. → `AssetsUploadApi.Status`

**Response fields** (`AssetsUploadApi.Operation`)

See [AssetsUploadApi.Operation](#assetsuploadapi-operation) in Models.

**Response example:**
```json
{
  "path": "string",
  "operationId": "string",
  "done": false,
  "error": {
    "code": "string",
    "message": "string",
    "details": [
      "..."
    ]
  },
  "response": {
    "path": "string",
    "revisionId": "string",
    "revisionCreateTime": "2024-01-01T00:00:00Z",
    "assetId": "string",
    "displayName": "string",
    "description": "string"
  }
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 120/minute, perOauth2Authorization: 120/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/assets/v1/assets" \
  -F "fileContent=@file.bin;type=application/octet-stream" \
  -F "additionalParameters="...";type=application/json" \
  -F "request={"path":"string","revisionId":"string","revisionCreateTime":"2024-01-01T00:00:00Z","assetId":"string","displayName":"string","description":"string"};type=application/json"
```

### GET `/assets/v1/assets/{assetId}` [BETA]

Retrieve specific asset metadata. Include the `readMask` parameter for additional asset metadata.

Retrieve specific asset metadata.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `asset:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetId` | path | `integer` | Yes | The unique identifier of the asset. |
| `readMask` | query | `string[]` | No | Asset metadata fields to retrieve, including the description, display name, icon, social links, and previews. Examples: `description%2CdisplayName`, `previews%2CtwitchSocialLink`. |

**Responses:**

- `200`: Asset resource retrieved successfully. → `AssetsUploadApi.Asset`
- `400`: Malformed request, likely due to an invalid read mask. → `AssetsUploadApi.Status`
- `401`: The API key is not valid for this operation / You don't have the authorization. → `AssetsUploadApi.Status`
- `403`: Doesn't have the required permission. → `AssetsUploadApi.Status`
- `404`: Asset doesn't exist. → `AssetsUploadApi.Status`
- `500`: Server internal error / Unknown error. → `AssetsUploadApi.Status`

**Response fields** (`AssetsUploadApi.Asset`)

See [AssetsUploadApi.Asset](#assetsuploadapi-asset) in Models.

**Response example:**
```json
{
  "path": "string",
  "revisionId": "string",
  "revisionCreateTime": "2024-01-01T00:00:00Z",
  "assetId": "string",
  "displayName": "string",
  "description": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 600/minute, perOauth2Authorization: 600/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/assets/v1/assets/{ASSETID}"
```

### PATCH `/assets/v1/assets/{assetId}` [BETA]

Updates an asset with provided content and metadata.

Updates an asset's content, metadata, or both. Metadata includes the description, display name, icon, social links, and previews. Updating content creates a new asset version and is supported for **Models** and **Places**. For Places, set `published` to `true` to publish the new version. Icons and previews must be **Image** assets, and icons must have square dimensions.

Provide the `Asset`, binary asset file path, and [content type](/cloud/guides/usage-assets.md#supported-asset-types-and-limits) in the form data.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `asset:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetId` | path | `integer` | Yes | The unique identifier of the asset. |
| `updateMask` | query | `string[]` | No | Asset metadata fields to update, including the description, display name, icon, and previews. Examples: `description%2CdisplayName`, `previews%2CtwitchSocialLink`. |

**Request Body:** `multipart/form-data` — Type: `object`

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `fileContent` | `string` | No | The binary asset file path and the content type. See [Asset types and limits](/cloud/guides/usage-assets.md#supported-as |
| `additionalParameters` | `object` | No | Optional: Additional parameters to be sent with the request can be included here. |
| `request` | [AssetsUploadApi.Asset](#assetsuploadapi-asset) | Yes | Asset attributes to update. |
| `request.path` | `string` | No | The returned resource path of the asset. Format: `assets/{assetId}`. Example: `assets/2205400862`. |
| `request.revisionId` | `string` | No | *(immutable)* Revision ID of the asset. Equivalent to `versionNumber`. Every change of the asset automatically com |
| `request.revisionCreateTime` | `string` | No | The creation timestamp of the current revision. |
| `request.assetId` | `string` | No | The unique identifier of the asset. Required for [Update Asset](#Assets_UpdateAsset). |
| `request.displayName` | `string` | No | Display name of the asset. Required for [Create Asset](#Assets_CreateAsset). |
| `request.description` | `string` | No | The description of the asset. Limit to 1000 characters. Required for [Create Asset](#Assets_CreateAs |

**Request example:**
```json
{
  "fileContent": "string",
  "additionalParameters": "...",
  "request": {
    "path": "string",
    "revisionId": "string",
    "revisionCreateTime": "2024-01-01T00:00:00Z",
    "assetId": "string",
    "displayName": "string",
    "description": "string"
  }
}
```

**Responses:**

- `200`: Returns the Operation ID for checking the update status / Returns the updated metadata fields. → `AssetsUploadApi.Operation`
- `400`: Invalid argument. Failed to parse the request or the file. → `AssetsUploadApi.Status`
- `401`: The API key is not valid for this operation / You don't have the authorization. → `AssetsUploadApi.Status`
- `403`: Doesn't have the required permission. → `AssetsUploadApi.Status`
- `500`: Server internal error / Unknown error. → `AssetsUploadApi.Status`

**Response fields** (`AssetsUploadApi.Operation`)

See [AssetsUploadApi.Operation](#assetsuploadapi-operation) in Models.

**Response example:**
```json
{
  "path": "string",
  "operationId": "string",
  "done": false,
  "error": {
    "code": "string",
    "message": "string",
    "details": [
      "..."
    ]
  },
  "response": {
    "path": "string",
    "revisionId": "string",
    "revisionCreateTime": "2024-01-01T00:00:00Z",
    "assetId": "string",
    "displayName": "string",
    "description": "string"
  }
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 120/minute, perOauth2Authorization: 120/minute

**Example:**
```bash
curl -X PATCH -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/assets/v1/assets/{ASSETID}" \
  -F "fileContent=@file.bin;type=application/octet-stream" \
  -F "additionalParameters="...";type=application/json" \
  -F "request={"path":"string","revisionId":"string","revisionCreateTime":"2024-01-01T00:00:00Z","assetId":"string","displayName":"string","description":"string"};type=application/json"
```

### GET `/assets/v1/assets/{assetId}/versions` [BETA]

List Asset Versions of an Asset

List all versions of a specific asset, with optional pagination.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `asset:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetId` | path | `integer` | Yes | The unique identifier of the asset. |
| `maxPageSize` | query | `integer` | No | Specifies the number of asset versions to include in the response. Valid values range from 1 to 50 (inclusive). Defaults to 8 when not provided. |
| `pageToken` | query | `string` | No | A token for pagination. The value is obtained from a previous request and allows for retrieving the next page of asset versions. |
| `filter` | query | `string` | No |  |

**Responses:**

- `200`: Asset versions listed successfully. → `ListAssetVersionsResponse`
- `400`: Bad request - invalid parameters. → `AssetsUploadApi.Status`
- `403`: Forbidden - API key without Read scope or user doesn't have access. → `AssetsUploadApi.Status`
- `404`: Asset not found. → `AssetsUploadApi.Status`

**Response fields** (`ListAssetVersionsResponse`)

See [ListAssetVersionsResponse](#listassetversionsresponse) in Models.

**Response example:**
```json
{
  "assetVersions": [
    {
      "path": "...",
      "createTime": "...",
      "creationContext": "...",
      "moderationResult": "...",
      "published": "..."
    }
  ],
  "nextPageToken": "string"
}
```

**Error handling:** `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/assets/v1/assets/{ASSETID}/versions"
```

### GET `/assets/v1/assets/{assetId}/versions/{versionNumber}` [BETA]

Get Asset Version

Retrieve a specific asset version by the asset ID and the version number.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `asset:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetId` | path | `integer` | Yes | The unique identifier of the asset. |
| `versionNumber` | path | `integer` | Yes | The version number. |

**Responses:**

- `200`: Asset version retrieved successfully. → `AssetVersion`
- `403`: Forbidden - API key without Read scope or user doesn't have access. → `AssetsUploadApi.Status`
- `404`: Asset or Asset Version not found. → `AssetsUploadApi.Status`

**Response fields** (`AssetVersion`)

See [AssetVersion](#assetversion) in Models.

**Response example:**
```json
{
  "path": "string",
  "createTime": "2024-01-01T00:00:00Z",
  "creationContext": {
    "creator": {
      "userId": "...",
      "groupId": "...",
      "experienceId": "..."
    },
    "expectedPrice": 0,
    "creatingUniverseId": 0,
    "assetPrivacy": "Unspecified"
  },
  "moderationResult": {
    "moderationState": "Unspecified"
  },
  "published": false
}
```

**Error handling:** `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 600/minute, perOauth2Authorization: 600/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/assets/v1/assets/{ASSETID}/versions/{VERSIONNUMBER}"
```

### POST `/assets/v1/assets/{assetId}/versions:rollback` [BETA]

Rollback an asset to a previous version.

Rollback an asset to a specific previous version.

Provide the asset version path in the request body.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `asset:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetId` | path | `integer` | Yes | The unique identifier of the asset. |

**Request Body:** `application/json` — Type: `RollbackAssetVersionRequest`

See [RollbackAssetVersionRequest](#rollbackassetversionrequest) in Models.

**Request example:**
```json
{
  "assetVersion": "string"
}
```

**Responses:**

- `200`: Asset rolled back successfully. → `AssetVersion`
- `400`: Bad request - invalid request body. → `AssetsUploadApi.Status`
- `403`: Forbidden - API key without Write scope or user doesn't have access. → `AssetsUploadApi.Status`
- `404`: Asset or Asset Version not found. → `AssetsUploadApi.Status`

**Response fields** (`AssetVersion`)

See [AssetVersion](#assetversion) in Models.

**Response example:**
```json
{
  "path": "string",
  "createTime": "2024-01-01T00:00:00Z",
  "creationContext": {
    "creator": {
      "userId": "...",
      "groupId": "...",
      "experienceId": "..."
    },
    "expectedPrice": 0,
    "creatingUniverseId": 0,
    "assetPrivacy": "Unspecified"
  },
  "moderationResult": {
    "moderationState": "Unspecified"
  },
  "published": false
}
```

**Error handling:** `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/assets/v1/assets/{ASSETID}/versions:rollback" \
  -H "Content-Type: application/json" \
  -d '{
  "assetVersion": "string"
}'
```

### POST `/assets/v1/assets/{assetId}:archive` [BETA]

Archives the asset.

Archives the asset. Archived assets disappear from the website and are no longer usable or visible in Roblox experiences, but you can [restore](#Assets_RestoreAsset) them.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `asset:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetId` | path | `integer` | Yes | The unique identifier of the asset. |

**Responses:**

- `200`: Asset archived successfully. → `AssetsUploadApi.Asset`
- `400`: Bad request - invalid request. → `AssetsUploadApi.Status`
- `401`: The API key is not valid for this operation / You don't have the authorization. → `AssetsUploadApi.Status`
- `403`: Forbidden - API key without Write scope or user doesn't have access. → `AssetsUploadApi.Status`
- `404`: Asset not found. → `AssetsUploadApi.Status`

**Response fields** (`AssetsUploadApi.Asset`)

See [AssetsUploadApi.Asset](#assetsuploadapi-asset) in Models.

**Response example:**
```json
{
  "path": "string",
  "revisionId": "string",
  "revisionCreateTime": "2024-01-01T00:00:00Z",
  "assetId": "string",
  "displayName": "string",
  "description": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/assets/v1/assets/{ASSETID}:archive"
```

### PATCH `/assets/v1/assets/{assetId}:multipartUpload` [EXPERIMENTAL]

Starts a multipart upload operation to update assets.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `asset:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetId` | path | `integer` | Yes |  |

**Request Body:** `application/json` — Type: `MultipartUploadStartRequest`

See [MultipartUploadStartRequest](#multipartuploadstartrequest) in Models.

**Request example:**
```json
{
  "asset": {
    "path": "string",
    "revisionId": "string",
    "revisionCreateTime": "2024-01-01T00:00:00Z",
    "assetId": "string",
    "displayName": "string",
    "description": "string"
  },
  "file": {
    "contentType": "string",
    "filesize": 0,
    "md5Checksum": "string",
    "chunkPlan": [
      "..."
    ]
  },
  "additionalParameters": "..."
}
```

**Responses:**

- `200`: OK → `MultipartUploadStartResponse`
- `400`: Bad Request → `AssetsUploadApi.Status`
- `401`: Unauthorized → `AssetsUploadApi.Status`
- `403`: Forbidden → `AssetsUploadApi.Status`

**Response fields** (`MultipartUploadStartResponse`)

See [MultipartUploadStartResponse](#multipartuploadstartresponse) in Models.

**Response example:**
```json
{
  "operationPath": "string",
  "uploadUrls": [
    {
      "httpVerb": "...",
      "url": "...",
      "expirationTimeMs": "...",
      "chunkNum": "...",
      "contentStart": "...",
      "contentLength": "..."
    }
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X PATCH -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/assets/v1/assets/{ASSETID}:multipartUpload" \
  -H "Content-Type: application/json" \
  -d '{"asset":{"path":"string","revisionId":"string","revisionCreateTime":"2024-01-01T00:00:00Z","assetId":"string","displayName":"string","description":"string"},"file":{"contentType":"string","filesize":0,"md5Checksum":"string","chunkPlan":["..."]},"additionalParameters":"..."}'
```

### POST `/assets/v1/assets/{assetId}:restore` [BETA]

Restores an archived asset.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `asset:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetId` | path | `integer` | Yes | The unique identifier of the asset. |

**Responses:**

- `200`: Asset restored successfully. → `AssetsUploadApi.Asset`
- `400`: Bad request - invalid request. → `AssetsUploadApi.Status`
- `401`: The API key is not valid for this operation / You don't have the authorization. → `AssetsUploadApi.Status`
- `403`: Forbidden - API key without Write scope or user doesn't have access. → `AssetsUploadApi.Status`
- `404`: Asset not found. → `AssetsUploadApi.Status`

**Response fields** (`AssetsUploadApi.Asset`)

See [AssetsUploadApi.Asset](#assetsuploadapi-asset) in Models.

**Response example:**
```json
{
  "path": "string",
  "revisionId": "string",
  "revisionCreateTime": "2024-01-01T00:00:00Z",
  "assetId": "string",
  "displayName": "string",
  "description": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/assets/v1/assets/{ASSETID}:restore"
```

### POST `/assets/v1/assets:multipartUpload` [EXPERIMENTAL]

Starts a multipart upload operation to create assets.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `asset:write`

**Request Body:** `application/json` — Type: `MultipartUploadStartRequest`

See [MultipartUploadStartRequest](#multipartuploadstartrequest) in Models.

**Request example:**
```json
{
  "asset": {
    "path": "string",
    "revisionId": "string",
    "revisionCreateTime": "2024-01-01T00:00:00Z",
    "assetId": "string",
    "displayName": "string",
    "description": "string"
  },
  "file": {
    "contentType": "string",
    "filesize": 0,
    "md5Checksum": "string",
    "chunkPlan": [
      "..."
    ]
  },
  "additionalParameters": "..."
}
```

**Responses:**

- `200`: OK → `MultipartUploadStartResponse`
- `400`: Bad Request → `AssetsUploadApi.Status`
- `401`: Unauthorized → `AssetsUploadApi.Status`
- `403`: Forbidden → `AssetsUploadApi.Status`

**Response fields** (`MultipartUploadStartResponse`)

See [MultipartUploadStartResponse](#multipartuploadstartresponse) in Models.

**Response example:**
```json
{
  "operationPath": "string",
  "uploadUrls": [
    {
      "httpVerb": "...",
      "url": "...",
      "expirationTimeMs": "...",
      "chunkNum": "...",
      "contentStart": "...",
      "contentLength": "..."
    }
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/assets/v1/assets:multipartUpload" \
  -H "Content-Type: application/json" \
  -d '{"asset":{"path":"string","revisionId":"string","revisionCreateTime":"2024-01-01T00:00:00Z","assetId":"string","displayName":"string","description":"string"},"file":{"contentType":"string","filesize":0,"md5Checksum":"string","chunkPlan":["..."]},"additionalParameters":"..."}'
```

### GET `/assets/v1/operations/{operationId}` [BETA]

Get the result of an asset creation or update.

Get the result of an asset creation or update using the returned Operation ID.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `asset:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `operationId` | path | `string` | Yes | The unique identifier of the operation. |

**Responses:**

- `200`: Operation result retrieved successfully. → `AssetsUploadApi.Operation`
- `400`: Invalid argument. Failed to parse the request or the file. → `AssetsUploadApi.Status`
- `401`: The API key is not valid for this operation / You don't have the authorization. → `AssetsUploadApi.Status`
- `403`: Doesn't have the required permission. → `AssetsUploadApi.Status`
- `500`: Server internal error / Unknown error. → `AssetsUploadApi.Status`

**Response fields** (`AssetsUploadApi.Operation`)

See [AssetsUploadApi.Operation](#assetsuploadapi-operation) in Models.

**Response example:**
```json
{
  "path": "string",
  "operationId": "string",
  "done": false,
  "error": {
    "code": "string",
    "message": "string",
    "details": [
      "..."
    ]
  },
  "response": {
    "path": "string",
    "revisionId": "string",
    "revisionCreateTime": "2024-01-01T00:00:00Z",
    "assetId": "string",
    "displayName": "string",
    "description": "string"
  }
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 300/minute, perOauth2Authorization: 300/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/assets/v1/operations/{OPERATIONID}"
```

### DELETE `/assets/v1/operations/{operationId}:multipartUpload` [EXPERIMENTAL]

Abort a multipart asset upload.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `asset:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `operationId` | path | `string` | Yes |  |

**Responses:**

- `200`: OK
- `400`: Bad Request → `AssetsUploadApi.Status`
- `401`: Unauthorized → `AssetsUploadApi.Status`
- `403`: Forbidden → `AssetsUploadApi.Status`

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X DELETE -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/assets/v1/operations/{OPERATIONID}:multipartUpload"
```

### POST `/assets/v1/operations/{operationId}:multipartUploadChunkComplete` [EXPERIMENTAL]

Records a chunk upload complete.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `asset:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `operationId` | path | `string` | Yes |  |

**Request Body:** `application/json` — Type: `MultipartUploadChunkCompleteRequest`

See [MultipartUploadChunkCompleteRequest](#multipartuploadchunkcompleterequest) in Models.

**Request example:**
```json
{
  "chunkNum": 0,
  "eTag": "string"
}
```

**Responses:**

- `200`: OK
- `400`: Bad Request → `AssetsUploadApi.Status`
- `401`: Unauthorized → `AssetsUploadApi.Status`
- `403`: Forbidden → `AssetsUploadApi.Status`

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/assets/v1/operations/{OPERATIONID}:multipartUploadChunkComplete" \
  -H "Content-Type: application/json" \
  -d '{
  "chunkNum": 0,
  "eTag": "string"
}'
```

### POST `/assets/v1/operations/{operationId}:multipartUploadComplete` [EXPERIMENTAL]

Records a multipart upload complete and returns a URL to poll the status.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `asset:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `operationId` | path | `string` | Yes |  |

**Responses:**

- `200`: OK → `AssetsUploadApi.Operation`
- `400`: Bad Request → `AssetsUploadApi.Status`
- `401`: Unauthorized → `AssetsUploadApi.Status`
- `403`: Forbidden → `AssetsUploadApi.Status`

**Response fields** (`AssetsUploadApi.Operation`)

See [AssetsUploadApi.Operation](#assetsuploadapi-operation) in Models.

**Response example:**
```json
{
  "path": "string",
  "operationId": "string",
  "done": false,
  "error": {
    "code": "string",
    "message": "string",
    "details": [
      "..."
    ]
  },
  "response": {
    "path": "string",
    "revisionId": "string",
    "revisionCreateTime": "2024-01-01T00:00:00Z",
    "assetId": "string",
    "displayName": "string",
    "description": "string"
  }
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/assets/v1/operations/{OPERATIONID}:multipartUploadComplete"
```

### POST `/cloud/v2/universes/{universe_id}:generateSpeechAsset` [BETA]

Generate Speech Asset

Generates an English speech audio asset from the specified text.

This endpoint requires the `asset:read` and `asset:write` scopes in
addition to the `universe:write` scope.

The response returns an `Operation` object that must be prefixed with
`/assets/v1`. For example, the URL to discover the result of the operation
could be
`https://apis.roblox.com/assets/v1/operations/8b42ef30-9c17-4526-b8cf-2ff0136ca94d`.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe:write`, `asset:read`, `asset:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universe_id` | path | `string` | Yes | The universe ID. |

**Request Body:** `application/json` — Type: `GenerateSpeechAssetRequest`

See [GenerateSpeechAssetRequest](#generatespeechassetrequest) in Models.

**Request example:**
```json
{
  "text": "string",
  "speechStyle": {
    "voiceId": "string",
    "pitch": 0,
    "speed": 0
  }
}
```

**Responses:**

- `200`: OK → `TextToSpeechService.Operation`

**Response fields** (`TextToSpeechService.Operation`)

See [TextToSpeechService.Operation](#texttospeechservice-operation) in Models.

**Response example:**
```json
{
  "path": "string",
  "metadata": "...",
  "done": false,
  "error": {
    "code": 0,
    "message": "string",
    "details": [
      "..."
    ]
  },
  "response": "..."
}
```

**Rate Limits:** perApiKeyOwner: 4/second, perOauth2Authorization: 4/second

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/universes/{UNIVERSE_ID}:generateSpeechAsset" \
  -H "Content-Type: application/json" \
  -d '{
  "text": "string",
  "speechStyle": {
    "voiceId": "string",
    "pitch": 0,
    "speed": 0
  }
}'
```

### GET `/cloud/v2/users/{user_id}/asset-quotas` [BETA]

List Asset Quotas

Returns a list of asset quotas.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `asset:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `user_id` | path | `integer` | Yes | The user ID. |
| `maxPageSize` | query | `integer` | No | The maximum number of asset quotas to return. The service might return fewer than this value. If unspecified, at most 10 asset quotas are returned. The maximum value is 100 and higher values are set to 100. |
| `pageToken` | query | `string` | No | A page token, received from a previous call, to retrieve a subsequent page.  When paginating, all other parameters provided to the subsequent call must match the call that provided the page token. |
| `filter` | query | `string` | No | This field may be set in order to filter the resources returned.  Supports the following subset of CEL: * Only the `quotaType` and `assetType` fields are supported. * Only the `==` and `&&` operator are supported.  For example:   `quotaType == RateLimitUpload && assetType == Audio` |

**Responses:**

- `200`: OK → `ListAssetQuotasResponse`
- `400`: Bad Request → `AssetsUploadApi.Status`
- `401`: Unauthorized → `AssetsUploadApi.Status`
- `403`: Forbidden → `AssetsUploadApi.Status`

**Response fields** (`ListAssetQuotasResponse`)

See [ListAssetQuotasResponse](#listassetquotasresponse) in Models.

**Response example:**
```json
{
  "assetQuotas": [
    {
      "path": "...",
      "quotaType": "...",
      "assetType": "...",
      "usage": "...",
      "capacity": "...",
      "period": "..."
    }
  ],
  "nextPageToken": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 60/minute, perOauth2Authorization: 60/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/users/{USER_ID}/asset-quotas"
```

### GET `/legacy-localization-tables/v1/localization-table/tables/{assetId}` [EXPERIMENTAL]

Get table information by the assetId of the table.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `legacy-universe:manage`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetId` | path | `integer` | Yes | The asset id associated with the table. |

**Responses:**

- `200`: OK → `Roblox.LocalizationTables.Api.GetTableResponse`
- `400`: 12: Invalid asset id.
- `401`: 0: Authorization has been denied for this request.
- `403`: 2: You do not have permission to get this table.

**Response fields** (`Roblox.LocalizationTables.Api.GetTableResponse`)

See [Roblox.LocalizationTables.Api.GetTableResponse](#roblox-localizationtables-api-gettableresponse) in Models.

**Response example:**
```json
{
  "id": "string",
  "name": "string",
  "ownerType": "User",
  "ownerId": 0,
  "assetId": 0
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/legacy-localization-tables/v1/localization-table/tables/{ASSETID}"
```

### POST `/legacy-publish/v1/badges/{badgeId}/icon` [EXPERIMENTAL]

Overwrites a badge icon with a new one.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `legacy-badge:manage`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `badgeId` | path | `integer` | Yes | The badge Id. |

**Responses:**

- `200`: OK → `Roblox.Publish.Api.UploadResponse`
- `400`: 2: File not present in request. 12: Name or description is moderated.
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed 5: You do not have permission to manage this item.
- `404`: 4: Target item is invalid or does not exist.
- `429`: 3: You're uploading too much, please wait and try again later.

**Response fields** (`Roblox.Publish.Api.UploadResponse`)

See [Roblox.Publish.Api.UploadResponse](#roblox-publish-api-uploadresponse) in Models.

**Response example:**
```json
{
  "targetId": 0
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/legacy-publish/v1/badges/{BADGEID}/icon" \
  -H "Content-Type: application/json" \
  -d '{"key": "value"}'
```

### GET `/toolbox-service/v2/assets/{id}` [BETA]

Get Creator Store Asset Details

Get details for a single Creator Store asset.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `creator-store-product:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `id` | path | `integer` | Yes | The asset ID to retrieve details for. |

**Responses:**

- `200`: OK → `CreatorStoreAsset`
- `403`: Forbidden → `any`
- `404`: Not Found → `any`
- `429`: Too Many Requests → `any`

**Response fields** (`CreatorStoreAsset`)

See [CreatorStoreAsset](#creatorstoreasset) in Models.

**Response example:**
```json
{
  "voting": {
    "showVotes": false,
    "upVotes": 0,
    "downVotes": 0,
    "canVote": false,
    "userVote": false,
    "hasVoted": false
  },
  "creator": {
    "creator": "string",
    "userId": 0,
    "groupId": 0,
    "name": "string",
    "verified": false,
    "latestGroupUpdaterUserId": 0
  },
  "creatorStoreProduct": {
    "purchasePrice": {
      "currencyCode": "...",
      "quantity": "..."
    },
    "purchasable": false
  },
  "asset": "..."
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 1000/minute, perOauth2Authorization: 1000/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/toolbox-service/v2/assets/{ID}"
```

### GET `/toolbox-service/v2/assets:search` [BETA]

Search Creator Store Assets

Search Creator Store for assets.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `creator-store-product:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `searchCategoryType` | query | `SearchCategoryType` | No | The asset type to search within. Optional when categoryPath is present in the request; otherwise required. Valid values: `Audio`, `Place`, `Model`, `Decal`, `Plugin`, `MeshPart`, `Video`, `FontFamily` |
| `query` | query | `string` | No | The search terms used to filter the results. |
| `modelSubTypes` | query | `ModelSubType[]` | No | When searching for models, the subtypes associated with the search results. Valid values: `Ad`, `MaterialPack`, `Package` |
| `excludedModelSubTypes` | query | `ModelSubType[]` | No | When searching for models, the subtypes not associated with the search results. Valid values: `Ad`, `MaterialPack`, `Package` |
| `creator` | query | `string` | No | Deprecated: Please refer to the 'userId' and 'groupId' properties instead. The creator type and ID. E.g. "user/123" or "group/456" |
| `userId` | query | `integer` | No | The User ID of the creator. Only one of 'userId' and 'groupId' can be present in a query. |
| `groupId` | query | `integer` | No | The Group ID of the creator. Only one of 'userId' and 'groupId' can be present in a query. |
| `pageToken` | query | `string` | No | The identifier for the desired search results page. Only one of 'pageNumber' and 'pageToken' can be present in a query. |
| `pageNumber` | query | `integer` | No | The page number to retrieve, starting from 0. Only one of 'pageNumber' and 'pageToken' can be present in a query. |
| `maxPageSize` | query | `integer` | No | The number of assets to be returned. Cannot be larger than 100. |
| `sortDirection` | query | `SortDirection` | No | The sort direction of the search results. Valid values: `None`, `Ascending`, `Descending` |
| `sortCategory` | query | `SortCategory` | No | The category to sort the search results by. Valid values: `Relevance`, `Trending`, `Top`, `AudioDuration`, `CreateTime`, `UpdatedTime`, `Ratings` |
| `audioMinDurationSeconds` | query | `integer` | No | When searching for audio, the minimum duration of the audio assets. If included, must be greater than or equal to 0. |
| `audioMaxDurationSeconds` | query | `integer` | No | When searching for audio, the maximum duration of the audio assets. If included, must be greater than or equal to 0. |
| `audioArtist` | query | `string` | No | When searching for audio, the artist name of the audio assets. |
| `audioAlbum` | query | `string` | No | When searching for audio, the album name of the audio assets. |
| `audioTypes` | query | `SearchAudioTypeModel[]` | No | When searching for audio, the type of the audio assets. Valid values: `Music`, `SoundEffect`, `Unknown` |
| `includedInstanceTypes` | query | `ModelInstanceType[]` | No | When searching for models, this filters that the following [Instance](https://create.roblox.com/docs/reference/engine/classes/Instance) types are included in the model. Valid values: `Script`, `MeshPart`, `Decal`, `Animation`, `Audio`, `Tool` |
| `includeOnlyVerifiedCreators` | query | `boolean` | No | Whether the results should only include assets created by verified creators. |
| `minPriceCents` | query | `integer` | No | The minimum price of the asset in cents. If included, must be greater than or equal to 0. |
| `maxPriceCents` | query | `integer` | No | The maximum price of the asset in cents. If included, must be greater than or equal to 0. |
| `facets` | query | `string[]` | No | Additional keywords to query by. |
| `tags` | query | `string[]` | No | The tags used to filter the results. |
| `categoryPath` | query | `string` | No |  |
| `searchView` | query | `SearchView` | No | Indicates which fields will be populated in the response. Valid values: `IDs`, `Core`, `Full` |
| `musicChartType` | query | `MusicChartType` | No | Indicates which music charts to filter from. Valid values: `None`, `Current`, `Week`, `Month`, `Year` |
| `swimlane` | query | `string` | No | Indicates which swimlane to filter from. |

**Responses:**

- `200`: OK → `SearchCreatorStoreAssetsResponse`
- `400`: Bad Request → `any`
- `429`: Too Many Requests → `any`
- `500`: Internal Server Error

**Response fields** (`SearchCreatorStoreAssetsResponse`)

See [SearchCreatorStoreAssetsResponse](#searchcreatorstoreassetsresponse) in Models.

**Response example:**
```json
{
  "nextPageToken": "string",
  "queryFacets": {
    "appliedFacets": [
      "..."
    ],
    "availableFacets": [
      "..."
    ]
  },
  "creatorStoreAssets": [
    {
      "voting": "...",
      "creator": "...",
      "creatorStoreProduct": "...",
      "asset": "..."
    }
  ],
  "totalResults": 0,
  "queryCorrection": {
    "suggestedQuery": "string"
  },
  "filteredKeyword": "string"
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). 

**Rate Limits:** perApiKeyOwner: 1000/minute, perOauth2Authorization: 1000/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/toolbox-service/v2/assets:search"
```

### GET `/v1/alias/{universeId}/{assetName}` [EXPERIMENTAL]

Retrieves an asset by its alias (universeID/name)

**Server:** `https://assetdelivery.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `string` | Yes |  |
| `assetName` | path | `string` | Yes |  |
| `Accept-Encoding` | header | `string` | Yes |  |
| `Roblox-Place-Id` | header | `integer` | Yes |  |
| `AssetType` | header | `string` | Yes |  |
| `AssetFormat` | header | `string` | Yes |  |
| `Roblox-AssetFormat` | header | `string` | Yes |  |
| `Roblox-Usage-Context` | header | `string` | No |  |
| `skipSigningScripts` | query | `boolean` | No |  |
| `clientInsert` | query | `integer` | No |  |
| `scriptinsert` | query | `integer` | No |  |
| `modulePlaceId` | query | `integer` | No |  |
| `serverplaceid` | query | `integer` | No |  |
| `expectedAssetType` | query | `string` | No |  |
| `accessContext` | query | `string` | No |  |

**Responses:**

- `200`: OK

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://assetdelivery.roblox.com/v1/alias/{UNIVERSEID}/{ASSETNAME}"
```

### GET `/v1/asset` [EXPERIMENTAL]

**Server:** `https://assetdelivery.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `Accept-Encoding` | header | `string` | Yes |  |
| `Roblox-Place-Id` | header | `integer` | Yes |  |
| `AssetType` | header | `string` | Yes |  |
| `AssetFormat` | header | `string` | Yes |  |
| `Roblox-AssetFormat` | header | `string` | Yes |  |
| `Roblox-Usage-Context` | header | `string` | No |  |
| `id` | query | `integer` | No |  |
| `userAssetId` | query | `integer` | No |  |
| `assetVersionId` | query | `integer` | No |  |
| `version` | query | `integer` | No |  |
| `universeId` | query | `integer` | No |  |
| `clientInsert` | query | `integer` | No |  |
| `scriptinsert` | query | `integer` | No |  |
| `modulePlaceId` | query | `integer` | No |  |
| `serverplaceid` | query | `string` | No |  |
| `assetName` | query | `string` | No |  |
| `hash` | query | `string` | No |  |
| `marAssetHash` | query | `string` | No |  |
| `marCheckSum` | query | `string` | No |  |
| `expectedAssetType` | query | `string` | No |  |
| `skipSigningScripts` | query | `boolean` | No |  |
| `permissionContext` | query | `string` | No |  |
| `doNotFallbackToBaselineRepresentation` | query | `boolean` | No |  |
| `contentRepresentationPriorityList` | query | `string` | No |  |
| `assetResolutionMode` | query | `string` | No |  |
| `accessContext` | query | `string` | No |  |

**Responses:**

- `200`: OK

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://assetdelivery.roblox.com/v1/asset"
```

### GET `/v1/asset-quotas`

List asset quotas of the given resource type and asset type.

**Server:** `https://publish.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `resourceType` | query | `string` | Yes | Resource type of the asset quota |
| `assetType` | query | `string` | Yes | Asset type of the asset quota |
| `useDummyData` | query | `boolean` | No | Use dummy data for testing. This is for internal use only |

**Responses:**

- `200`: OK → `Roblox.Publish.Api.AssetQuotasResponse`
- `400`: 7: The asset type is not appropriate for this request. 8: The resource type is not appropriate for this request.
- `401`: 0: Authorization has been denied for this request.
- `500`: 0: Reserved for base level errors. Do not use in your endpoint directly, do not document.

**Response fields** (`Roblox.Publish.Api.AssetQuotasResponse`)

See [Roblox.Publish.Api.AssetQuotasResponse](#roblox-publish-api-assetquotasresponse) in Models.

**Response example:**
```json
{
  "quotas": [
    {
      "duration": "...",
      "usage": "...",
      "capacity": "...",
      "expirationTime": "..."
    }
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://publish.roblox.com/v1/asset-quotas?resourceType={VALUE}&assetType={VALUE}"
```

### GET `/v1/asset-thumbnail-animated` [STABLE]

Thumbnails asset animated.

**Server:** `https://thumbnails.roblox.com`

**Auth:** 

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetId` | query | `integer` | Yes | The asset id. |
| `Roblox-Place-Id` | header | `integer` | No | (optional) placeid |

**Responses:**

- `200`: OK
- `400`: 4: The requested Ids are invalid, of an invalid type or missing.

**Example:**
```bash
curl -H "Authorization: Bearer $ROBLOX_ACCESS_TOKEN" \
  "https://thumbnails.roblox.com/v1/asset-thumbnail-animated?assetId={VALUE}"
```

### GET `/v1/asset-to-category` *(deprecated)*

Lists a mapping for assets to category IDs to convert from inventory ID to catalog ID. Creates a mapping to link 'Get More' button in inventory page to the relevant catalog page.

This endpoint will be deprecated soon. No new features will be added.

**Server:** `https://catalog.roblox.com`

**Auth:** 

**Responses:**

- `200`: OK → `object`

**Example:**
```bash
curl -H "Authorization: Bearer $ROBLOX_ACCESS_TOKEN" \
  "https://catalog.roblox.com/v1/asset-to-category"
```

### GET `/v1/asset-to-subcategory` *(deprecated)*

Lists a mapping for assets to subcategory IDs to convert from inventory ID to catalog ID. Creates a mapping to link 'Get More' button in inventory page to the relevant catalog page.

This endpoint will be deprecated soon. No new features will be added.

**Server:** `https://catalog.roblox.com`

**Auth:** 

**Responses:**

- `200`: OK → `object`

**Example:**
```bash
curl -H "Authorization: Bearer $ROBLOX_ACCESS_TOKEN" \
  "https://catalog.roblox.com/v1/asset-to-subcategory"
```

### GET `/v1/asset-types/{assetType}/agents` [EXPERIMENTAL]

Gets agents of type requestModel.AgentType who are allowed to perform requestModel.ActionType for assetType.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetType` | path | `integer enum (89 values)` | Yes | ['Image' = 1, 'TShirt' = 2, 'Audio' = 3, 'Mesh' = 4, 'Lua' = 5, 'HTML' = 6, 'Text' = 7, 'Hat' = 8, 'Place' = 9, 'Model' = 10, 'Shirt' = 11, 'Pants' = 12, 'Decal' = 13, 'Avatar' = 16, 'Head' = 17, 'Face' = 18, 'Gear' = 19, 'Badge' = 21, 'GroupEmblem' = 22, 'Animation' = 24, 'Arms' = 25, 'Legs' = 26, 'Torso' = 27, 'RightArm' = 28, 'LeftArm' = 29, 'LeftLeg' = 30, 'RightLeg' = 31, 'Package' = 32, 'YouTubeVideo' = 33, 'GamePass' = 34, 'App' = 35, 'Code' = 37, 'Plugin' = 38, 'SolidModel' = 39, 'MeshPart' = 40, 'HairAccessory' = 41, 'FaceAccessory' = 42, 'NeckAccessory' = 43, 'ShoulderAccessory' = 44, 'FrontAccessory' = 45, 'BackAccessory' = 46, 'WaistAccessory' = 47, 'ClimbAnimation' = 48, 'DeathAnimation' = 49, 'FallAnimation' = 50, 'IdleAnimation' = 51, 'JumpAnimation' = 52, 'RunAnimation' = 53, 'SwimAnimation' = 54, 'WalkAnimation' = 55, 'PoseAnimation' = 56, 'LocalizationTableManifest' = 59, 'LocalizationTableTranslation' = 60, 'EmoteAnimation' = 61, 'Video' = 62, 'TexturePack' = 63, 'TShirtAccessory' = 64, 'ShirtAccessory' = 65, 'PantsAccessory' = 66, 'JacketAccessory' = 67, 'SweaterAccessory' = 68, 'ShortsAccessory' = 69, 'LeftShoeAccessory' = 70, 'RightShoeAccessory' = 71, 'DressSkirtAccessory' = 72, 'FontFamily' = 73, 'FontFace' = 74, 'MeshHiddenSurfaceRemoval' = 75, 'EyebrowAccessory' = 76, 'EyelashAccessory' = 77, 'MoodAnimation' = 78, 'DynamicHead' = 79, 'CodeSnippet' = 80, 'AdsVideo' = 81, 'OtaUpdate' = 82, 'Screenshot' = 83, 'RuntimePropertySet' = 84, 'StorePreviewVideo' = 85, 'GamePreviewVideo' = 86, 'CreatorExperienceConfig' = 87, 'FaceMakeup' = 88, 'LipMakeup' = 89, 'EyeMakeup' = 90, 'VoxelFragment' = 91, 'AvatarBackground' = 92, 'TextDocument' = 93, 'Post' = 94, 'AnimatedImage' = 95, 'ComputeFunction' = 96] Valid values: `1`, `2`, `3`, `4`, `5`, `6`, `7`, `8`, `9`, `10`, `11`, `12`, `13`, `16`, `17`, `18`, `19`, `21`, `22`, `24`, `25`, `26`, `27`, `28`, `29`, `30`, `31`, `32`, `33`, `34`, `35`, `37`, `38`, `39`, `40`, `41`, `42`, `43`, `44`, `45`, `46`, `47`, `48`, `49`, `50`, `51`, `52`, `53`, `54`, `55`, `56`, `59`, `60`, `61`, `62`, `63`, `64`, `65`, `66`, `67`, `68`, `69`, `70`, `71`, `72`, `73`, `74`, `75`, `76`, `77`, `78`, `79`, `80`, `81`, `82`, `83`, `84`, `85`, `86`, `87`, `88`, `89`, `90`, `91`, `92`, `93`, `94`, `95`, `96` |
| `ActionType` | query | `1 \| 2` | Yes | The asset type target of the specified action. Valid values: `1`, `2` |
| `AgentType` | query | `1 \| 2` | Yes | The agentType of the agents for whom a user can perform specified action. Valid values: `1`, `2` |

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.AllowedAgentsAssetTypeActionResponse`
- `400`: 1: Invalid parameters in request. 2: Unsupported asset type. 3: Unsupported agent type
- `401`: 0: Authorization has been denied for this request.

**Response fields** (`Roblox.ItemConfiguration.Api.AllowedAgentsAssetTypeActionResponse`)

See [Roblox.ItemConfiguration.Api.AllowedAgentsAssetTypeActionResponse](#roblox-itemconfiguration-api-allowedagentsassettypeactionresponse) in Models.

**Response example:**
```json
{
  "agents": [
    {
      "type": "...",
      "id": "...",
      "name": "..."
    }
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/asset-types/{ASSETTYPE}/agents?ActionType={VALUE}&AgentType={VALUE}"
```

### GET `/v1/assetId/{assetId}`

Retrieves an asset by its ID

**Server:** `https://assetdelivery.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetId` | path | `integer` | Yes | The ID of the asset to retrieve. |
| `Accept-Encoding` | header | `string` | Yes |  |
| `Roblox-Place-Id` | header | `integer` | Yes |  |
| `AssetType` | header | `string` | Yes |  |
| `AssetFormat` | header | `string` | Yes |  |
| `Roblox-AssetFormat` | header | `string` | Yes |  |
| `Roblox-Usage-Context` | header | `string` | No |  |
| `skipSigningScripts` | query | `boolean` | No |  |
| `clientInsert` | query | `integer` | No |  |
| `scriptinsert` | query | `integer` | No |  |
| `modulePlaceId` | query | `integer` | No |  |
| `serverplaceid` | query | `integer` | No |  |
| `expectedAssetType` | query | `string` | No |  |
| `doNotFallbackToBaselineRepresentation` | query | `boolean` | No |  |
| `contentRepresentationPriorityList` | query | `string` | No |  |
| `accessContext` | query | `string` | No |  |

**Responses:**

- `200`: OK

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://assetdelivery.roblox.com/v1/assetId/{ASSETID}"
```

### GET `/v1/assetId/{assetId}/version/{versionNumber}`

Retrieves an asset by its ID and version number.

**Server:** `https://assetdelivery.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetId` | path | `integer` | Yes | The ID of the asset to retrieve. |
| `versionNumber` | path | `integer` | Yes | The version of the asset to retrieve. |
| `Accept-Encoding` | header | `string` | Yes |  |
| `Roblox-Place-Id` | header | `integer` | Yes |  |
| `AssetType` | header | `string` | Yes |  |
| `AssetFormat` | header | `string` | Yes |  |
| `Roblox-AssetFormat` | header | `string` | Yes |  |
| `Roblox-Usage-Context` | header | `string` | No |  |
| `skipSigningScripts` | query | `boolean` | No |  |
| `clientInsert` | query | `integer` | No |  |
| `scriptinsert` | query | `integer` | No |  |
| `modulePlaceId` | query | `integer` | No |  |
| `serverplaceid` | query | `integer` | No |  |
| `expectedAssetType` | query | `string` | No |  |
| `doNotFallbackToBaselineRepresentation` | query | `boolean` | No |  |
| `contentRepresentationPriorityList` | query | `string` | No |  |
| `accessContext` | query | `string` | No |  |

**Responses:**

- `200`: OK

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://assetdelivery.roblox.com/v1/assetId/{ASSETID}/version/{VERSIONNUMBER}"
```

### GET `/v1/assets` [STABLE]

Thumbnails assets.

**Server:** `https://thumbnails.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetIds` | query | `integer[]` | Yes | The asset ids. |
| `Roblox-Place-Id` | header | `integer` | No | (optional) placeid |
| `returnPolicy` | query | `PlaceHolder \| ForcePlaceHolder \| AutoGenerated \| ForceAutoGenerated` | No | Optional policy to use in selecting thumbnail to return (default = PlaceHolder). Valid values: `PlaceHolder`, `ForcePlaceHolder`, `AutoGenerated`, `ForceAutoGenerated` |
| `size` | query | `string enum (30 values)` | No | The thumbnail size, formatted widthxheight Valid values: `30x30`, `42x42`, `50x50`, `60x62`, `75x75`, `110x110`, `140x140`, `150x150`, `160x100`, `160x600`, `250x250`, `256x144`, `300x250`, `304x166`, `384x216`, `396x216`, `420x420`, `480x270`, `512x512`, `576x324`, `700x700`, `728x90`, `768x432`, `1200x80`, `330x110`, `660x220`, `1320x440`, `720x228`, `1440x456`, `930x480` |
| `format` | query | `Png \| Jpeg \| Webp` | No | The thumbnail format Valid values: `Png`, `Jpeg`, `Webp` |
| `isCircular` | query | `true \| false` | No | The circle thumbnail output parameter, true or false Valid values: `true`, `false` |

**Responses:**

- `200`: OK
- `400`: 1: There are too many requested Ids. 2: The requested image format is invalid. Please see documentation for valid thumbnail format parameter name and values. 3: The requested size is invalid. Please see documentation for valid thumbnail size parameter name and format. 4: The requested Ids are invalid, of an invalid type or missing. 8: The requested return policy is invalid (must be PlaceHolder, AutoGenerated or ForceAutoGenerated). 10: Circular thumbnail requests are not allowed
- `403`: 9: User not authorized to use AutoGenerated or ForceAutoGenerated return policies.

**Error handling:** `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://thumbnails.roblox.com/v1/assets?assetIds={VALUE}"
```

### GET `/v1/assets-thumbnail-3d` [BETA]

Thumbnails assets.

**Server:** `https://thumbnails.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `thumbnail:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetId` | query | `integer` | Yes | The asset id. |
| `useGltf` | query | `boolean` | No | (optional) formatType |
| `Roblox-Place-Id` | header | `integer` | No | (optional) placeid |

**Responses:**

- `200`: OK
- `400`: 4: The requested Ids are invalid, of an invalid type or missing.

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://thumbnails.roblox.com/v1/assets-thumbnail-3d?assetId={VALUE}"
```

### POST `/v1/assets/batch` [EXPERIMENTAL]

**Server:** `https://assetdelivery.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `Roblox-Place-Id` | header | `integer` | Yes |  |
| `Roblox-Browser-Asset-Request` | header | `string` | Yes |  |

**Request Body:** `application/json` — Type: `Roblox.Web.Assets.BatchAssetRequestItem[]`

See [Roblox.Web.Assets.BatchAssetRequestItem](#roblox-web-assets-batchassetrequestitem) in Models.

**Responses:**

- `200`: OK

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://assetdelivery.roblox.com/v1/assets/batch" \
  -H "Content-Type: application/json" \
  -d '[
  {
    "assetName": "string",
    "assetType": "string",
    "clientInsert": false,
    "placeId": 0,
    "requestId": "string",
    "scriptInsert": false
  }
]'
```

### GET `/v1/assets/voting` *(deprecated)*

Gets the voting information of the given assets

Please use toolbox service to get asset voting information.

**Server:** `https://develop.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetIds` | query | `integer[]` | Yes | The ids of the Roblox.Platform.Assets.IAsset. |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Api.Develop.Models.Response.AssetVotingModel_`

**Response fields** (`Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Api.Develop.Models.Response.AssetVotingModel_`)

See [Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Api.Develop.Models.Response.AssetVotingModel_](#roblox-web-webapi-models-apiarrayresponse-roblox-api-develop-models-response-assetvotingmodel-) in Models.

**Response example:**
```json
{
  "data": [
    {
      "assetId": "...",
      "hasUserVoted": "...",
      "canUserVote": "...",
      "shouldShowVotes": "...",
      "upVotes": "...",
      "downVotes": "..."
    }
  ]
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://develop.roblox.com/v1/assets/voting?assetIds={VALUE}"
```

### GET `/v1/assets/{assetId}/bundles` [EXPERIMENTAL]

Lists the bundles a particular asset belongs to. Use the Id of the last bundle in the response to get the next page.

**Server:** `https://catalog.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetId` | path | `integer` | Yes |  |
| `limit` | query | `10 \| 25 \| 50 \| 100` | No | The number of results per request. Valid values: `10`, `25`, `50`, `100` |
| `cursor` | query | `string` | No | The paging cursor for the previous or next page. |
| `sortOrder` | query | `Asc \| Desc` | No | The order the results are sorted in. Valid values: `Asc`, `Desc` |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Catalog.Api.BundleDetailsModel_`
- `400`: 1: Invalid assetId 4: Invalid Cursor.

**Response fields** (`Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Catalog.Api.BundleDetailsModel_`)

See [Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Catalog.Api.BundleDetailsModel_](#roblox-web-webapi-models-apipageresponse-roblox-catalog-api-bundledetailsmodel-) in Models.

**Response example:**
```json
{
  "previousPageCursor": "string",
  "nextPageCursor": "string",
  "data": [
    {
      "id": "...",
      "name": "...",
      "description": "...",
      "bundleType": "...",
      "isRecolorable": "...",
      "items": "..."
    }
  ]
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://catalog.roblox.com/v1/assets/{ASSETID}/bundles"
```

### GET `/v1/assets/{assetId}/resale-data` [EXPERIMENTAL]

Gets asset resale data.

This endpoint is only valid for resellable (limited) items.

**Server:** `https://economy.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetId` | path | `integer` | Yes | The asset id. |

**Responses:**

- `200`: OK → `Roblox.Economy.Api.ResaleDataResponse`
- `400`: 5: The asset id is invalid.

**Response fields** (`Roblox.Economy.Api.ResaleDataResponse`)

See [Roblox.Economy.Api.ResaleDataResponse](#roblox-economy-api-resaledataresponse) in Models.

**Response example:**
```json
{
  "assetStock": 0,
  "sales": 0,
  "numberRemaining": 0,
  "recentAveragePrice": 0,
  "originalPrice": 0,
  "priceDataPoints": [
    {
      "value": "...",
      "date": "..."
    }
  ]
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://economy.roblox.com/v1/assets/{ASSETID}/resale-data"
```

### POST `/v1/audio`

Published an audio file and returns the new asset info.

**Server:** `https://publish.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Request Body:** `application/json` — Type: `Roblox.Publish.Api.UploadAudioRequest`

See [Roblox.Publish.Api.UploadAudioRequest](#roblox-publish-api-uploadaudiorequest) in Models.

**Request example:**
```json
{
  "name": "string",
  "file": "string",
  "groupId": 0,
  "paymentSource": "string",
  "estimatedFileSize": 0,
  "estimatedDuration": 0
}
```

**Responses:**

- `200`: OK → `Roblox.Publish.Api.PublishAudioResponse`
- `400`: 3: The request did not contain a file to be uploaded. 4: The file in the request is too large. 5: The duration of the audio file is too long. 7: Failed to parse the file. 8: The file type is not supported. 9: The file is corrupted 11: Missing permissions to spend group funds. 14: The user/group does not have suffiecient funds to publish. 14: The user/group does not have suffiecient funds to publish. 15: The audio file has already been reviewed and rejected. 18: Too many requests. Try again later. 20: Error while trying to purchase the product. 22: The file size estimation error was greater than the acceptable margin of error. 23: The duration estimation error was greater than the acceptable margin of error. 24: Asset privacy is invalid. 29: Invalid argument in the request.
- `401`: 0: Authorization has been denied for this request. 1: The request did not include an authorization.
- `403`: 0: Token Validation Failed
- `500`: 19: Asset creation was unavailable. Please try again.

**Response fields** (`Roblox.Publish.Api.PublishAudioResponse`)

See [Roblox.Publish.Api.PublishAudioResponse](#roblox-publish-api-publishaudioresponse) in Models.

**Response example:**
```json
{
  "Id": 0,
  "Name": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://publish.roblox.com/v1/audio" \
  -H "Content-Type: application/json" \
  -d '{
  "name": "string",
  "file": "string",
  "groupId": 0,
  "paymentSource": "string",
  "estimatedFileSize": 0,
  "estimatedDuration": 0
}'
```

### POST `/v1/audio/verify`

Verifies an audio file and returns a product that you can purchase to publish the audio file.

**Server:** `https://publish.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Request Body:** `application/json` — Type: `Roblox.Publish.Api.VerifyAudioRequest`

See [Roblox.Publish.Api.VerifyAudioRequest](#roblox-publish-api-verifyaudiorequest) in Models.

**Request example:**
```json
{
  "name": "string",
  "file": "string",
  "groupId": 0,
  "paymentSource": "string",
  "fileSize": 0,
  "duration": 0
}
```

**Responses:**

- `200`: OK → `Roblox.Publish.Api.VerifyAudioResponse`
- `400`: 3: The request did not contain a file to be uploaded. 4: The file in the request is too large. 5: The duration of the audio file is too long. 7: Failed to parse the file. 8: The file type is not supported. 9: The file is corrupted 18: Too many requests. Try again later.
- `401`: 0: Authorization has been denied for this request. 1: The request did not include an authorization.
- `403`: 0: Token Validation Failed

**Response fields** (`Roblox.Publish.Api.VerifyAudioResponse`)

See [Roblox.Publish.Api.VerifyAudioResponse](#roblox-publish-api-verifyaudioresponse) in Models.

**Response example:**
```json
{
  "name": "string",
  "price": 0,
  "balance": 0,
  "canAfford": false
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://publish.roblox.com/v1/audio/verify" \
  -H "Content-Type: application/json" \
  -d '{
  "name": "string",
  "file": "string",
  "groupId": 0,
  "paymentSource": "string",
  "fileSize": 0,
  "duration": 0
}'
```

### POST `/v1/avatar-item-updates/create-context` [EXPERIMENTAL]

Mint an avatar item update context (parent operation) for an existing catalog item. Studio
threads the returned operationId as the ParentOperationId of the staging asset upload.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:write`

**Request Body:** `application/json` — Type: `Roblox.ItemConfiguration.Api.Models.Request.AvatarItemUpdate.CreateAvatarItemUpdateContextRequest`

See [Roblox.ItemConfiguration.Api.Models.Request.AvatarItemUpdate.CreateAvatarItemUpdateContextRequest](#roblox-itemconfiguration-api-models-request-avataritemupdate-createavataritemupdatecontextrequest) in Models.

**Request example:**
```json
{
  "originalAssetId": 0,
  "assetType": 0
}
```

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.Models.Response.AvatarItemUpdate.CreateAvatarItemUpdateContextResponse`
- `400`: 2: Invalid original asset id 3: Invalid asset type 4: The item is not a valid update target
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed 5: The item is not owned by the authenticated user 7: Missing authenticated user 9: In-experience-created items can't be updated 10: The item has not been approved by moderation
- `408`: 8: Request cancelled
- `409`: 6: Updating a published item isn't available yet
- `500`: 0: Unknown error
- `503`: 1: Service Unavailable

**Response fields** (`Roblox.ItemConfiguration.Api.Models.Response.AvatarItemUpdate.CreateAvatarItemUpdateContextResponse`)

See [Roblox.ItemConfiguration.Api.Models.Response.AvatarItemUpdate.CreateAvatarItemUpdateContextResponse](#roblox-itemconfiguration-api-models-response-avataritemupdate-createavataritemupdatecontextresponse) in Models.

**Response example:**
```json
{
  "operationId": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/avatar-item-updates/create-context" \
  -H "Content-Type: application/json" \
  -d '{
  "originalAssetId": 0,
  "assetType": 0
}'
```

### POST `/v1/badges/{badgeId}/icon`

Overwrites a badge icon with a new one.

Accepts a moderated image upload and updates the badge's icon asset.

**Server:** `https://badges.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `badgeId` | path | `integer` | Yes | The badge Id. |

**Request Body:** `multipart/form-data` — Type: `object`

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `Files` | `string` | No |  |

**Request example:**
```json
{
  "Files": "string"
}
```

**Responses:**

- `200`: OK → `Roblox.Badges.Api.IconUploadResponse`
- `400`: 6: Text moderated. 22: Icon file is not present in the request.
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed 2: You do not have permission to manage this badge.
- `404`: 1: Badge is invalid or does not exist.
- `429`: 13: Too many requests, try again later.

**Response fields** (`Roblox.Badges.Api.IconUploadResponse`)

See [Roblox.Badges.Api.IconUploadResponse](#roblox-badges-api-iconuploadresponse) in Models.

**Response example:**
```json
{
  "targetId": 0
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://badges.roblox.com/v1/badges/{BADGEID}/icon" \
  -F "Files=@file.bin;type=application/octet-stream"
```

### POST `/v1/badges/{badgeId}/icon#publish.roblox.com` [EXPERIMENTAL]

Overwrites a badge icon with a new one.

**Server:** `https://publish.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `badgeId` | path | `integer` | Yes | The badge Id. |

**Responses:**

- `200`: OK → `Roblox.Publish.Api.UploadResponse`
- `400`: 2: File not present in request. 12: Name or description is moderated.
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed 5: You do not have permission to manage this item.
- `404`: 4: Target item is invalid or does not exist.
- `429`: 3: You're uploading too much, please wait and try again later.

**Response fields** (`Roblox.Publish.Api.UploadResponse`)

See [Roblox.Publish.Api.UploadResponse](#roblox-publish-api-uploadresponse) in Models.

**Response example:**
```json
{
  "targetId": 0
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://publish.roblox.com/v1/badges/{BADGEID}/icon#publish.roblox.com" \
  -H "Content-Type: application/json" \
  -d '{"key": "value"}'
```

### POST `/v1/bundles` [EXPERIMENTAL]

Create a new bundle with the provided information.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:publish`

**Request Body:** `application/json` — Type: `Roblox.ItemConfiguration.Api.Models.Request.Bundle.CreateBundleRequest`

See [Roblox.ItemConfiguration.Api.Models.Request.Bundle.CreateBundleRequest](#roblox-itemconfiguration-api-models-request-bundle-createbundlerequest) in Models.

**Request example:**
```json
{
  "bundleType": "Unknown",
  "name": "string",
  "description": "string",
  "assetIds": [
    0
  ],
  "operationId": "string",
  "agreedCreationFee": 0
}
```

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.Models.Response.Bundle.CreateBundleResponse`
- `400`: 2: Invalid Bundle Name 3: Invalid AssetIds 4: Invalid OperationId 5: Invalid Bundle Type 6: Invalid/Null Create Bundle Request 7: Invalid Bundle Description 11: Group Creator Not Supported 13: Creation fee is invalid, must be a positive number
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed 9: Item is not allowed to be part of a new bundle 12: Creator mismatch
- `412`: 10: Invalid Bundle Creation State
- `501`: 8: Unsupported Bundle Type
- `503`: 1: Service Unavailable

**Response fields** (`Roblox.ItemConfiguration.Api.Models.Response.Bundle.CreateBundleResponse`)

See [Roblox.ItemConfiguration.Api.Models.Response.Bundle.CreateBundleResponse](#roblox-itemconfiguration-api-models-response-bundle-createbundleresponse) in Models.

**Response example:**
```json
{
  "creationStatusId": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 1/second

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/bundles" \
  -H "Content-Type: application/json" \
  -d '{
  "bundleType": "Unknown",
  "name": "string",
  "description": "string",
  "assetIds": [
    0
  ],
  "operationId": "string",
  "agreedCreationFee": 0
}'
```

### POST `/v1/bundles/create-context` [EXPERIMENTAL]

Generate bundle creation context which is necessary for the bundle creation process.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:publish`

**Request Body:** `application/json` — Type: `Roblox.ItemConfiguration.Api.Models.Request.Bundle.CreateBundleContextRequest`

See [Roblox.ItemConfiguration.Api.Models.Request.Bundle.CreateBundleContextRequest](#roblox-itemconfiguration-api-models-request-bundle-createbundlecontextrequest) in Models.

**Request example:**
```json
{
  "assetQuantities": "...",
  "bundleDescription": "string",
  "bundleName": "string",
  "bundleType": "Unknown",
  "bodyScale": {
    "height": 0,
    "width": 0,
    "head": 0,
    "bodyType": 0,
    "proportion": 0
  },
  "bodyColorSet": {
    "headColor3": "string",
    "torsoColor3": "string",
    "leftArmColor3": "string",
    "rightArmColor3": "string",
    "leftLegColor3": "string",
    "rightLegColor3": "string"
  }
}
```

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.Models.Response.Bundle.CreateBundleContextResponse`
- `400`: 2: Invalid AssetQuantities 3: Invalid Bundle Type 4: Invalid/Null Create Bundle Request 5: Invalid Bundle Description 6: Invalid Bundle Name 7: Inappropriate Bundle Description 8: Inappropriate Bundle Name 12: Invalid Body Scale 13: Invalid Body Color Set 14: Group creator not supported. 15: Request is missing required asset. 16: Asset counts must have non-zero, positive counts. 17: Too many asset types provided. 18: Creation fee is invalid. 19: Invalid Token ID. 20: Invalid Group ID.
- `401`: 0: Authorization has been denied for this request. 10: User not found
- `403`: 0: Token Validation Failed 9: User does not have bundle creation permission 106: Missing ID verification. 107: User's creation access is blocked. 110: Missing CatalogItemCreator role. 111: Missing Group Permission 112: Item type is not allowed.
- `412`: 11: Daily bundle creation limit reached 21: Bundle upload quota exceeded for this bundle type.
- `500`: 103: Publishing gateway returns denied without any reason 104: Publishing gateway returns unexpected reason 105: Publishing gateway returns unexpected access status
- `503`: 1: Service Unavailable

**Response fields** (`Roblox.ItemConfiguration.Api.Models.Response.Bundle.CreateBundleContextResponse`)

See [Roblox.ItemConfiguration.Api.Models.Response.Bundle.CreateBundleContextResponse](#roblox-itemconfiguration-api-models-response-bundle-createbundlecontextresponse) in Models.

**Response example:**
```json
{
  "operationId": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 1/second

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/bundles/create-context" \
  -H "Content-Type: application/json" \
  -d '{"assetQuantities":"...","bundleDescription":"string","bundleName":"string","bundleType":"Unknown","bodyScale":{"height":0,"width":0,"head":0,"bodyType":0,"proportion":0},"bodyColorSet":{"headColor3":"string","torsoColor3":"string","leftArmColor3":"string","rightArmColor3":"string","leftLegColor3":"string","rightLegColor3":"string"}}'
```

### GET `/v1/bundles/details` [EXPERIMENTAL]

Returns details about the given bundleIds.

**Server:** `https://catalog.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `bundleIds` | query | `integer[]` | Yes |  |

**Responses:**

- `200`: OK → `Roblox.Catalog.Api.BundleDetailsModel[]`
- `400`: 3: Cannot request so many bundles at once.

**Response fields** (`Roblox.Catalog.Api.BundleDetailsModel[]`)

See [Roblox.Catalog.Api.BundleDetailsModel](#roblox-catalog-api-bundledetailsmodel) in Models.

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://catalog.roblox.com/v1/bundles/details?bundleIds={VALUE}"
```

### GET `/v1/bundles/metadata` [EXPERIMENTAL]

Get metadata for bundle creation and publishing.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.Models.Response.Bundle.BundleMetadataResponse`
- `401`: 0: Authorization has been denied for this request.
- `500`: 0: Unknown error

**Response fields** (`Roblox.ItemConfiguration.Api.Models.Response.Bundle.BundleMetadataResponse`)

See [Roblox.ItemConfiguration.Api.Models.Response.Bundle.BundleMetadataResponse](#roblox-itemconfiguration-api-models-response-bundle-bundlemetadataresponse) in Models.

**Response example:**
```json
{
  "isBundlesControllerEnabled": false,
  "isBundlesCreationEnabled": false,
  "isBundlesPublishingEnabled": false,
  "allowedBundleTypeSettings": "...",
  "isGroupBundlesUploadEnabled": false
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/bundles/metadata"
```

### GET `/v1/bundles/status/{creationStatusId}` [EXPERIMENTAL]

Get status on the CreateBundle request that was previously queued up.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `creationStatusId` | path | `string` | Yes | an identifier associated with the create bundle request. |

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.Models.Response.Bundle.GetBundleCreationStatusResponse`
- `400`: 2: Invalid Creation Status Id
- `401`: 0: Authorization has been denied for this request.
- `404`: 3: Creation Status Not Found
- `500`: 0: Unknown error
- `503`: 1: Service Unavailable

**Response fields** (`Roblox.ItemConfiguration.Api.Models.Response.Bundle.GetBundleCreationStatusResponse`)

See [Roblox.ItemConfiguration.Api.Models.Response.Bundle.GetBundleCreationStatusResponse](#roblox-itemconfiguration-api-models-response-bundle-getbundlecreationstatusresponse) in Models.

**Response example:**
```json
{
  "bundleId": 0,
  "status": 0
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/bundles/status/{CREATIONSTATUSID}"
```

### GET `/v1/bundles/{bundleId}/details` [EXPERIMENTAL]

Returns details about the given bundleId.

**Server:** `https://catalog.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `bundleId` | path | `integer` | Yes |  |

**Responses:**

- `200`: OK → `Roblox.Catalog.Api.BundleDetailsModel`
- `400`: 1: Invalid bundle

**Response fields** (`Roblox.Catalog.Api.BundleDetailsModel`)

See [Roblox.Catalog.Api.BundleDetailsModel](#roblox-catalog-api-bundledetailsmodel) in Models.

**Response example:**
```json
{
  "id": 0,
  "name": "string",
  "description": "string",
  "bundleType": "string",
  "isRecolorable": false,
  "items": [
    {
      "owned": "...",
      "id": "...",
      "name": "...",
      "type": "...",
      "supportsHeadShapes": "...",
      "assetType": "..."
    }
  ]
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://catalog.roblox.com/v1/bundles/{BUNDLEID}/details"
```

### GET `/v1/bundles/{bundleId}/recommendations` [EXPERIMENTAL]

Gets recommendations for a given bundle, bundleId of 0 returns randomized bundles
- Accepts both public and authenticated users.

**Server:** `https://catalog.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `bundleId` | path | `integer` | Yes |  |
| `numItems` | query | `integer` | No | The number of recommended items to return. |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Catalog.Api.BundleDetailsModel_`
- `400`: 1: Invalid bundle 2: Error retrieving bundles 3: Error getting bundle recommendations 4: NumItems exceed maximum

**Response fields** (`Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Catalog.Api.BundleDetailsModel_`)

See [Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Catalog.Api.BundleDetailsModel_](#roblox-web-webapi-models-apiarrayresponse-roblox-catalog-api-bundledetailsmodel-) in Models.

**Response example:**
```json
{
  "data": [
    {
      "id": "...",
      "name": "...",
      "description": "...",
      "bundleType": "...",
      "isRecolorable": "...",
      "items": "..."
    }
  ]
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://catalog.roblox.com/v1/bundles/{BUNDLEID}/recommendations"
```

### POST `/v1/catalog/items/details` [EXPERIMENTAL]

Returns details for one or more catalog items.

There is an item count limit per request. Exceeding this returns 400 Bad Request.

**Server:** `https://catalog.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Catalog.Api.CatalogSearchDetailedResponseItemV2_`
- `400`: 2: Invalid count
- `403`: 0: Token Validation Failed 7: User is unauthorized.
- `429`: 8: The flood limit has been exceeded.

**Response fields** (`Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Catalog.Api.CatalogSearchDetailedResponseItemV2_`)

See [Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Catalog.Api.CatalogSearchDetailedResponseItemV2_](#roblox-web-webapi-models-apiarrayresponse-roblox-catalog-api-catalogsearchdetailedresponseitemv2-) in Models.

**Response example:**
```json
{
  "data": [
    {
      "bundledItems": "...",
      "taxonomy": "...",
      "itemCreatedUtc": "...",
      "discountInformation": "...",
      "license": "...",
      "id": "..."
    }
  ]
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://catalog.roblox.com/v1/catalog/items/details" \
  -H "Content-Type: application/json" \
  -d '{"key": "value"}'
```

### POST `/v1/catalog/items/details/complete`

Returns list of item details complete with user ownership and economy information.
Batch version of GetItemDetailsComplete. Items with critical errors are returned in ItemErrors
with their corresponding HTTP status code (404 for not-found, 500 for other errors).

**Server:** `https://catalog.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `Roblox-Place-Id` | header | `integer` | Yes |  |
| `Roblox-Game-Id` | header | `string` | Yes |  |

**Responses:**

- `200`: OK → `Roblox.Catalog.Api.BatchItemDetailsCompleteResponse`
- `400`: 2: Invalid count
- `403`: 0: Token Validation Failed 7: User is unauthorized.
- `429`: 8: The flood limit has been exceeded.

**Response fields** (`Roblox.Catalog.Api.BatchItemDetailsCompleteResponse`)

See [Roblox.Catalog.Api.BatchItemDetailsCompleteResponse](#roblox-catalog-api-batchitemdetailscompleteresponse) in Models.

**Response example:**
```json
{
  "data": [
    {
      "id": "...",
      "itemType": "...",
      "item": "...",
      "httpStatusCode": "..."
    }
  ]
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://catalog.roblox.com/v1/catalog/items/details/complete" \
  -H "Content-Type: application/json" \
  -d '{"key": "value"}'
```

### GET `/v1/categories` *(deprecated)*

Lists Category Names and their Ids.

This endpoint will be deprecated soon. No new features will be added.

**Server:** `https://catalog.roblox.com`

**Auth:** 

**Responses:**

- `200`: OK → `Roblox.Catalog.Api.CategoryModel[]`

**Response fields** (`Roblox.Catalog.Api.CategoryModel[]`)

See [Roblox.Catalog.Api.CategoryModel](#roblox-catalog-api-categorymodel) in Models.

**Example:**
```bash
curl -H "Authorization: Bearer $ROBLOX_ACCESS_TOKEN" \
  "https://catalog.roblox.com/v1/categories"
```

### POST `/v1/collectibles` [EXPERIMENTAL]

Publishes a given target as a Collectible.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:publish`

**Request Body:** `application/json` — Type: `Roblox.ItemConfiguration.Api.Models.Request.PublishCollectibleItemRequest`

See [Roblox.ItemConfiguration.Api.Models.Request.PublishCollectibleItemRequest](#roblox-itemconfiguration-api-models-request-publishcollectibleitemrequest) in Models.

**Request example:**
```json
{
  "isRentalOptIn": false,
  "idempotencyToken": "string",
  "targetId": 0,
  "targetType": 0,
  "publishingType": 0,
  "agreedPublishingFee": 0
}
```

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.PublishCollectibleItemResponse`
- `400`: 1: Invalid target type 4: Invalid Argument 8: Missing/Null request parameters 19: Item price is too low 20: Item price is too high 21: Asset Id is invalid 26: The upload content Name or Description was moderated. 32: Gateway could not publish item 35: Quantity is invalid 36: Specified SaleLocation is currently not supported. 43: Quantity limit is currently not supported. 44: Quantity limit is invalid. 47: Resale restriction is currently not supported. Must be none or unset for now. 48: Invalid resale restriction. 59: Price offset is invalid. 60: Minimum price is invalid. 62: Invalid price configuration. 65: Unexpected Place Ids. 76: The item is delisted. 111: Asset cannot be published because it has been used in Commerce products. 119: Item is not a rentable type. 122: Invalid name. 123: Invalid description. 146: Agreement is not publishable. 147: Resale is not allowed by the license. 148: Immediate on-sale is not allowed while the agreement is pending. 149: OnSaleTime is outside the agreement window. 150: OffSaleTime is outside the agreement window. 151: OffSaleTime is required for this agreement.
- `401`: 0: Authorization has been denied for this request. 66: Missing Authenticated User.
- `402`: 70: The user does not have enough Robux to pay
- `403`: 0: Token Validation Failed 10: Cannot release asset that is pending validation 11: Cannot release asset that contains invalid content 12: User does not have permission for the group owned asset 13: Cannot release the associated asset type 14: Cannot release asset that is pending review 15: Asset is moderated 16: Item is released 17: User does not have permission to release 18: User does not own the item 28: Asset has already been released as a non-limited item. 45: Asset is an exact copy of a published asset. 46: ItemIsInBundle 51: BundleType Cannot Be Released. 57: Non-limited publishing is not supported. 72: The Item is moderated. 74: The item's type is not allowed. 77: Resellable creation not allowed for user. 80: Publishing InExperienceCreation item is blocked. 94: Actor is moderated. 101: Calendar quota exceeded 102: Calendar quota is unavailable. 106: Missing ID verification. 107: User's creation access is blocked. 108: Missing premium subscription tier. 109: Group owner missing premium subscription tier. 115: User is not authorized for this action. 125: Missing two step verification. 143: Publishing AI-generated item is blocked. 146: Agreement is not publishable.
- `404`: 3: Service Unavailable 5: Not Found 71: The Item is not found. 134: Bundle not found.
- `412`: 75: The item has archived dependencies.
- `429`: 9: Publishing Limit Exceeded 34: Could not find initial user-owner asset 121: Purchase failed due to flood-check.
- `500`: 32: Gateway could not publish item 34: Could not find initial user-owner asset 41: Publishing quota is unavailable. 56: Publishing Gateway returns unexpected exception. 67: Invalid creator type 73: The Item's moderation status could not be determined. 103: Publishing gateway returns denied without any reason 104: Publishing gateway returns unexpected reason 105: Publishing gateway returns unexpected access status 144: Failed to get agreement. 145: Failed to get license.
- `507`: 42: Failed to fetch marketplace fee.

**Response fields** (`Roblox.ItemConfiguration.Api.PublishCollectibleItemResponse`)

See [Roblox.ItemConfiguration.Api.PublishCollectibleItemResponse](#roblox-itemconfiguration-api-publishcollectibleitemresponse) in Models.

**Response example:**
```json
{
  "status": 0
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 1/second

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/collectibles" \
  -H "Content-Type: application/json" \
  -d '{
  "isRentalOptIn": false,
  "idempotencyToken": "string",
  "targetId": 0,
  "targetType": 0,
  "publishingType": 0,
  "agreedPublishingFee": 0
}'
```

### PATCH `/v1/collectibles/bulk-update` [EXPERIMENTAL]

Updates some items in bulk.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:write`

**Request Body:** `application/json` — Type: `Roblox.ItemConfiguration.Api.Models.Request.Collectibles.BulkUpdateRequest`

See [Roblox.ItemConfiguration.Api.Models.Request.Collectibles.BulkUpdateRequest](#roblox-itemconfiguration-api-models-request-collectibles-bulkupdaterequest) in Models.

**Request example:**
```json
{
  "idempotencyKey": "string",
  "groupId": 0,
  "updateTargets": {
    "assetType": [
      "..."
    ],
    "target": [
      "..."
    ]
  },
  "updatePayload": {
    "rentalOptIn": false
  }
}
```

**Responses:**

- `200`: OK
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed
- `404`: 3: Service Unavailable

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 10/minute

**Example:**
```bash
curl -X PATCH -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/collectibles/bulk-update" \
  -H "Content-Type: application/json" \
  -d '{
  "idempotencyKey": "string",
  "groupId": 0,
  "updateTargets": {
    "assetType": [
      "..."
    ],
    "target": [
      "..."
    ]
  },
  "updatePayload": {
    "rentalOptIn": false
  }
}'
```

### GET `/v1/collectibles/check-item-configuration-access` [EXPERIMENTAL]

Checks the configure access permissions.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `TargetType` | query | `0 \| 1 \| 2 \| 3` | Yes | The type of the target item. Valid values: `0`, `1`, `2`, `3` |
| `TargetId` | query | `integer` | Yes | The id of the target item. |

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.CheckItemConfigurationAccessResponse`
- `400`: 1: Invalid target type 21: Asset Id is invalid
- `401`: 0: Authorization has been denied for this request.
- `403`: 66: Missing Authenticated User. 68: Permission provider not enabled
- `404`: 3: Service Unavailable
- `500`: 56: Publishing Gateway returns unexpected exception. 67: Invalid creator type 103: Publishing gateway returns denied without any reason 104: Publishing gateway returns unexpected reason 105: Publishing gateway returns unexpected access status

**Response fields** (`Roblox.ItemConfiguration.Api.CheckItemConfigurationAccessResponse`)

See [Roblox.ItemConfiguration.Api.CheckItemConfigurationAccessResponse](#roblox-itemconfiguration-api-checkitemconfigurationaccessresponse) in Models.

**Response example:**
```json
{
  "isAllowed": false,
  "deniedReason": 0
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/collectibles/check-item-configuration-access?TargetType={VALUE}&TargetId={VALUE}"
```

### GET `/v1/collectibles/check-item-publish-access` [EXPERIMENTAL]

Checks the publish access permissions.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `TargetType` | query | `0 \| 1 \| 2 \| 3` | Yes | The type of the target item. Valid values: `0`, `1`, `2`, `3` |
| `TargetId` | query | `integer` | Yes | The id of the target item. |
| `PublishingType` | query | `0 \| 1 \| 2` | Yes | The publishing type. Valid values: `0`, `1`, `2` |

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.CheckItemPublishAccessResponse`
- `400`: 1: Invalid target type 21: Asset Id is invalid
- `401`: 0: Authorization has been denied for this request.
- `403`: 66: Missing Authenticated User. 68: Permission provider not enabled
- `404`: 3: Service Unavailable
- `500`: 56: Publishing Gateway returns unexpected exception. 67: Invalid creator type 103: Publishing gateway returns denied without any reason 104: Publishing gateway returns unexpected reason 105: Publishing gateway returns unexpected access status

**Response fields** (`Roblox.ItemConfiguration.Api.CheckItemPublishAccessResponse`)

See [Roblox.ItemConfiguration.Api.CheckItemPublishAccessResponse](#roblox-itemconfiguration-api-checkitempublishaccessresponse) in Models.

**Response example:**
```json
{
  "isAllowed": false,
  "deniedReason": 0
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/collectibles/check-item-publish-access?TargetType={VALUE}&TargetId={VALUE}&PublishingType={VALUE}"
```

### GET `/v1/collectibles/check-item-upload-access` [EXPERIMENTAL]

Checks the upload access permissions.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `targetType` | query | `0 \| 1 \| 2 \| 3` | Yes | The type of the target item. Valid values: `0`, `1`, `2`, `3` |
| `groupId` | query | `integer` | No | The id of a group when uploading on the group behalf. |

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.CheckItemUploadAccessResponse`
- `400`: 1: Invalid target type 69: Invalid group id.
- `401`: 0: Authorization has been denied for this request.
- `403`: 66: Missing Authenticated User. 68: Permission provider not enabled
- `404`: 3: Service Unavailable
- `500`: 56: Publishing Gateway returns unexpected exception. 103: Publishing gateway returns denied without any reason 104: Publishing gateway returns unexpected reason 105: Publishing gateway returns unexpected access status

**Response fields** (`Roblox.ItemConfiguration.Api.CheckItemUploadAccessResponse`)

See [Roblox.ItemConfiguration.Api.CheckItemUploadAccessResponse](#roblox-itemconfiguration-api-checkitemuploadaccessresponse) in Models.

**Response example:**
```json
{
  "isAllowed": false,
  "deniedReason": 0
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/collectibles/check-item-upload-access?targetType={VALUE}"
```

### GET `/v1/collectibles/commission-rates` [EXPERIMENTAL]

Get commission rates for collectibles.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.GetCommissionRatesResponse`
- `401`: 0: Authorization has been denied for this request.
- `404`: 3: Service Unavailable
- `500`: 7: Failed to get commission rates

**Response fields** (`Roblox.ItemConfiguration.Api.GetCommissionRatesResponse`)

See [Roblox.ItemConfiguration.Api.GetCommissionRatesResponse](#roblox-itemconfiguration-api-getcommissionratesresponse) in Models.

**Response example:**
```json
{
  "creatorFeesPercentage": 0,
  "marketplaceFeesPercentage": 0,
  "resellerFeesPercentage": 0,
  "sellerFeesPercentage": 0
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/collectibles/commission-rates"
```

### GET `/v1/collectibles/metadata` [EXPERIMENTAL]

Gets metadata for Collectibles publishing.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.CollectiblesMetadataResponse`
- `401`: 0: Authorization has been denied for this request.

**Response fields** (`Roblox.ItemConfiguration.Api.CollectiblesMetadataResponse`)

See [Roblox.ItemConfiguration.Api.CollectiblesMetadataResponse](#roblox-itemconfiguration-api-collectiblesmetadataresponse) in Models.

**Response example:**
```json
{
  "isCollectiblesControllerEnabled": false,
  "isCollectiblesPublishingEnabled": false,
  "isCollectiblesPublishingLocationTypeEnabled": false,
  "allowedCollectibleSaleLocations": [
    0
  ],
  "IsCollectibleFreeItemPublishingAvailable": false,
  "isCollectibleGroupPublishingAvailable": false
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/collectibles/metadata"
```

### GET `/v1/collectibles/price-floor` [EXPERIMENTAL]

Get the price floor for a given item.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `TargetType` | query | `0 \| 1 \| 2 \| 3` | Yes | Target Type. Valid values: `0`, `1`, `2`, `3` |
| `TargetId` | query | `integer` | Yes | Target ID. |
| `PublishingType` | query | `0 \| 1 \| 2` | Yes | Publishing type. Valid values: `0`, `1`, `2` |

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.Models.Response.Collectibles.PriceFloorResponse`
- `400`: 1: Invalid target type 58: Invalid publishing type. 113: Item Id is invalid.
- `401`: 0: Authorization has been denied for this request. 66: Missing Authenticated User.
- `403`: 115: User is not authorized for this action.
- `404`: 3: Service Unavailable 114: Price floor not found.
- `500`: 2: Failed to fetch publishing fee

**Response fields** (`Roblox.ItemConfiguration.Api.Models.Response.Collectibles.PriceFloorResponse`)

See [Roblox.ItemConfiguration.Api.Models.Response.Collectibles.PriceFloorResponse](#roblox-itemconfiguration-api-models-response-collectibles-pricefloorresponse) in Models.

**Response example:**
```json
{
  "priceFloorInRobux": 0,
  "displayName": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/collectibles/price-floor?TargetType={VALUE}&TargetId={VALUE}&PublishingType={VALUE}"
```

### GET `/v1/collectibles/publishing-fees` [EXPERIMENTAL]

Gets the publishing fee required to publish a collectible item.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `TargetType` | query | `0 \| 1 \| 2 \| 3` | Yes | Target Type. Valid values: `0`, `1`, `2`, `3` |
| `TargetID` | query | `integer` | Yes | Target ID. |
| `Quantity` | query | `integer` | Yes | Quantity. |
| `SaleLocation` | query | `0 \| 1 \| 2 \| 3 \| 4` | Yes | SaleLocation. Valid values: `0`, `1`, `2`, `3`, `4` |
| `ResaleRestriction` | query | `0 \| 1 \| 2` | Yes | ResaleRestriction. Valid values: `0`, `1`, `2` |
| `IsFree` | query | `boolean` | Yes | Is item is free. |
| `PublishingType` | query | `0 \| 1 \| 2` | Yes | Publishing type. Valid values: `0`, `1`, `2` |

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.PublishingFeeResponse`
- `400`: 1: Invalid target type 35: Quantity is invalid
- `401`: 0: Authorization has been denied for this request.
- `404`: 3: Service Unavailable
- `500`: 2: Failed to fetch publishing fee

**Response fields** (`Roblox.ItemConfiguration.Api.PublishingFeeResponse`)

See [Roblox.ItemConfiguration.Api.PublishingFeeResponse](#roblox-itemconfiguration-api-publishingfeeresponse) in Models.

**Response example:**
```json
{
  "publishingFeeInRobux": 0,
  "unitPublishingFeeInRobux": 0,
  "isDynamicFeeEnabled": false,
  "publishingFeeType": 0
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/collectibles/publishing-fees?TargetType={VALUE}&TargetID={VALUE}&Quantity={VALUE}&SaleLocation={VALUE}&ResaleRestriction={VALUE}&IsFree={VALUE}&PublishingType={VALUE}"
```

### GET `/v1/collectibles/publishing-fees/preview` [EXPERIMENTAL]

Previews the publishing fee for an item type before the item exists, so the fee can be shown at
upload time. Takes the item's type directly instead of a target id.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `AssetType` | query | `integer enum (92 values)` | Yes | Asset type of the item being uploaded. Mutually exclusive with BundleType; exactly one is required. Same generated types the existing upload-fee endpoint takes, so the two fee endpoints agree. Valid values: `0`, `1`, `2`, `3`, `4`, `5`, `6`, `7`, `8`, `9`, `10`, `11`, `12`, `13`, `16`, `17`, `18`, `19`, `21`, `22`, `24`, `25`, `26`, `27`, `28`, `29`, `30`, `31`, `32`, `33`, `34`, `35`, `37`, `38`, `39`, `40`, `41`, `42`, `43`, `44`, `45`, `46`, `47`, `48`, `49`, `50`, `51`, `52`, `53`, `54`, `55`, `56`, `59`, `60`, `61`, `62`, `63`, `64`, `65`, `66`, `67`, `68`, `69`, `70`, `71`, `72`, `73`, `74`, `75`, `76`, `77`, `78`, `79`, `80`, `81`, `82`, `83`, `84`, `85`, `86`, `87`, `88`, `89`, `90`, `91`, `92`, `93`, `94`, `95`, `96`, `97`, `98` |
| `BundleType` | query | `0 \| 1 \| 2 \| 3 \| 4` | Yes | Bundle type of the item being uploaded. Mutually exclusive with AssetType; exactly one is required. Valid values: `0`, `1`, `2`, `3`, `4` |
| `Quantity` | query | `integer` | Yes | Quantity. Must be 0 for non-limited publishing. |
| `PublishingType` | query | `0 \| 1 \| 2` | Yes | Publishing type. Valid values: `0`, `1`, `2` |
| `IsFree` | query | `boolean` | Yes | Whether the item will be free. |

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.PublishingFeePreviewResponse`
- `400`: 1: Invalid target type 4: Invalid Argument 35: Quantity is invalid 58: Invalid publishing type. 64: Cannot be free.
- `401`: 0: Authorization has been denied for this request. 66: Missing Authenticated User.
- `404`: 5: Not Found
- `500`: 2: Failed to fetch publishing fee

**Response fields** (`Roblox.ItemConfiguration.Api.PublishingFeePreviewResponse`)

See [Roblox.ItemConfiguration.Api.PublishingFeePreviewResponse](#roblox-itemconfiguration-api-publishingfeepreviewresponse) in Models.

**Response example:**
```json
{
  "publishingFeeInRobux": 0,
  "publishingFeeType": 0
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/collectibles/publishing-fees/preview?AssetType={VALUE}&BundleType={VALUE}&Quantity={VALUE}&PublishingType={VALUE}&IsFree={VALUE}"
```

### GET `/v1/collectibles/regional-pricing/preview` [EXPERIMENTAL]

Get the preview for regional prices.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `TargetType` | query | `0 \| 1 \| 2 \| 3` | Yes | The type of the target item. Valid values: `0`, `1`, `2`, `3` |
| `TargetId` | query | `integer` | Yes | The id of the target item. |
| `PublishingType` | query | `0 \| 1 \| 2` | Yes | The publishing type of the target item. Valid values: `0`, `1`, `2` |
| `MinimumPrice` | query | `integer` | Yes | The minimum price of the item in Robux. |
| `PriceOffset` | query | `integer` | Yes | The price offset of the item in Robux above the price floor. |

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.GetRegionalpricingPreviewResponse`
- `400`: 1: Invalid target type 58: Invalid publishing type.
- `401`: 0: Authorization has been denied for this request.
- `403`: 12: User does not have permission for the group owned asset 18: User does not own the item 66: Missing Authenticated User. 72: The Item is moderated. 106: Missing ID verification. 108: Missing premium subscription tier. 115: User is not authorized for this action. 125: Missing two step verification.
- `404`: 3: Service Unavailable 71: The Item is not found.
- `500`: 56: Publishing Gateway returns unexpected exception.

**Response fields** (`Roblox.ItemConfiguration.Api.GetRegionalpricingPreviewResponse`)

See [Roblox.ItemConfiguration.Api.GetRegionalpricingPreviewResponse](#roblox-itemconfiguration-api-getregionalpricingpreviewresponse) in Models.

**Response example:**
```json
{
  "regionalPrices": [
    {
      "priceInRobux": "...",
      "countryIso2Code": "..."
    }
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/collectibles/regional-pricing/preview?TargetType={VALUE}&TargetId={VALUE}&PublishingType={VALUE}&MinimumPrice={VALUE}&PriceOffset={VALUE}"
```

### GET `/v1/collectibles/regional-pricing/representative-countries` [EXPERIMENTAL]

Get the representative countries for regional pricing.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.GetRepresentativeCountriesResponse`
- `401`: 0: Authorization has been denied for this request.
- `404`: 3: Service Unavailable

**Response fields** (`Roblox.ItemConfiguration.Api.GetRepresentativeCountriesResponse`)

See [Roblox.ItemConfiguration.Api.GetRepresentativeCountriesResponse](#roblox-itemconfiguration-api-getrepresentativecountriesresponse) in Models.

**Response example:**
```json
{
  "countryIso2Codes": [
    "string"
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/collectibles/regional-pricing/representative-countries"
```

### GET `/v1/collectibles/rental-pricing/preview` [EXPERIMENTAL]

Gets the rental pricing preview for a collectible item. Can include regional pricing if enabled.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `TargetType` | query | `0 \| 1 \| 2 \| 3` | Yes | The type of the target item. Valid values: `0`, `1`, `2`, `3` |
| `TargetId` | query | `integer` | Yes | The id of the target item. |
| `PublishingType` | query | `0 \| 1 \| 2` | Yes | The publishing type of the target item. Valid values: `0`, `1`, `2` |
| `MinimumPrice` | query | `integer` | Yes | The minimum price of the item in Robux. |
| `PriceOffset` | query | `integer` | Yes | The price offset of the item in Robux above the price floor. |
| `IncludeRegionalPricing` | query | `boolean` | Yes | Whether to include regional pricing in the preview response. |

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.Models.Response.GetRentalPricingPreviewResponse`
- `400`: 1: Invalid target type 58: Invalid publishing type.
- `401`: 0: Authorization has been denied for this request.
- `403`: 18: User does not own the item 72: The Item is moderated.
- `404`: 3: Service Unavailable 71: The Item is not found.

**Response fields** (`Roblox.ItemConfiguration.Api.Models.Response.GetRentalPricingPreviewResponse`)

See [Roblox.ItemConfiguration.Api.Models.Response.GetRentalPricingPreviewResponse](#roblox-itemconfiguration-api-models-response-getrentalpricingpreviewresponse) in Models.

**Response example:**
```json
{
  "rentalPrices": [
    {
      "rentalDays": "...",
      "priceInRobux": "..."
    }
  ],
  "regionalRentalPrices": [
    {
      "countryIso2Code": "...",
      "rentalPrices": "..."
    }
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/collectibles/rental-pricing/preview?TargetType={VALUE}&TargetId={VALUE}&PublishingType={VALUE}&MinimumPrice={VALUE}&PriceOffset={VALUE}&IncludeRegionalPricing={VALUE}"
```

### GET `/v1/collectibles/revenue-split` [EXPERIMENTAL]

Get Revenue Split for collectibles.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `TargetType` | query | `0 \| 1 \| 2 \| 3` | Yes | Target Type. Valid values: `0`, `1`, `2`, `3` |
| `TargetID` | query | `string` | Yes | Target ID. |
| `CollectibleItemType` | query | `0 \| 1 \| 2` | Yes | Collectible item type. Valid values: `0`, `1`, `2` |
| `MinimumPrice` | query | `integer` | Yes | Minimum Price. |
| `PriceOffset` | query | `integer` | Yes | Price offset. |
| `PurchasePlatform` | query | `0 \| 1 \| 2` | Yes | Purchase platform. Valid values: `0`, `1`, `2` |
| `LicenseId` | query | `string` | Yes | License id of the agreement selected in the picker. When present, the response reflects the IP-holder royalty for that license; when absent, the split is unchanged. |

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.Models.Request.Collectibles.RevenueSplitResponse`
- `400`: 1: Invalid target type 113: Item Id is invalid. 117: Transaction Type is invalid.
- `401`: 0: Authorization has been denied for this request.
- `403`: 115: User is not authorized for this action.
- `404`: 3: Service Unavailable
- `500`: 116: Failed to get revenue splits.

**Response fields** (`Roblox.ItemConfiguration.Api.Models.Request.Collectibles.RevenueSplitResponse`)

See [Roblox.ItemConfiguration.Api.Models.Request.Collectibles.RevenueSplitResponse](#roblox-itemconfiguration-api-models-request-collectibles-revenuesplitresponse) in Models.

**Response example:**
```json
{
  "RevenueSplit": {
    "creatorSplitPercentage": 0,
    "sellerSplitPercentage": 0,
    "marketplaceSplitPercentage": 0,
    "resellerSplitPercentage": 0,
    "ipHolderSplitPercentage": 0
  }
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/collectibles/revenue-split?TargetType={VALUE}&TargetID={VALUE}&CollectibleItemType={VALUE}&MinimumPrice={VALUE}&PriceOffset={VALUE}&PurchasePlatform={VALUE}&LicenseId={VALUE}"
```

### PATCH `/v1/collectibles/update-item-display-information` [EXPERIMENTAL]

Update the display information of an item.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:write`

**Request Body:** `application/json` — Type: `Roblox.ItemConfiguration.Api.Models.Request.UpdateItemDisplayInformationRequest`

See [Roblox.ItemConfiguration.Api.Models.Request.UpdateItemDisplayInformationRequest](#roblox-itemconfiguration-api-models-request-updateitemdisplayinformationrequest) in Models.

**Request example:**
```json
{
  "targetType": 0,
  "targetId": "string",
  "name": "string",
  "description": "string"
}
```

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.ApiEmptyResponseModel`
- `400`: 1: Invalid target type 1: Invalid target type 4: Invalid Argument 4: Invalid Argument 8: Missing/Null request parameters 21: Asset Id is invalid 26: The upload content Name or Description was moderated. 50: Bundle Id is Invalid. 113: Item Id is invalid. 122: Invalid name. 123: Invalid description.
- `401`: 0: Authorization has been denied for this request. 66: Missing Authenticated User.
- `403`: 0: Token Validation Failed 12: User does not have permission for the group owned asset 18: User does not own the item 72: The Item is moderated. 74: The item's type is not allowed. 106: Missing ID verification. 107: User's creation access is blocked. 108: Missing premium subscription tier. 109: Group owner missing premium subscription tier. 125: Missing two step verification.
- `404`: 3: Service Unavailable 5: Not Found 71: The Item is not found.
- `500`: 56: Publishing Gateway returns unexpected exception. 67: Invalid creator type 73: The Item's moderation status could not be determined.

**Response fields** (`Roblox.Web.WebAPI.ApiEmptyResponseModel`)

See [Roblox.Web.WebAPI.ApiEmptyResponseModel](#roblox-web-webapi-apiemptyresponsemodel) in Models.

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -X PATCH -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/collectibles/update-item-display-information" \
  -H "Content-Type: application/json" \
  -d '{
  "targetType": 0,
  "targetId": "string",
  "name": "string",
  "description": "string"
}'
```

### PATCH `/v1/collectibles/{collectibleItemId}` [EXPERIMENTAL]

Update product information about a published Collectible Item.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `collectibleItemId` | path | `string` | Yes |  |

**Request Body:** `application/json` — Type: `Roblox.ItemConfiguration.Api.Models.Request.UpdateCollectibleItemRequest`

See [Roblox.ItemConfiguration.Api.Models.Request.UpdateCollectibleItemRequest](#roblox-itemconfiguration-api-models-request-updatecollectibleitemrequest) in Models.

**Request example:**
```json
{
  "saleLocationConfiguration": {
    "saleLocationType": 0,
    "places": [
      "..."
    ]
  },
  "isRentalOptIn": false,
  "saleStatus": 0,
  "quantityLimitPerUser": 0,
  "resaleRestriction": 0,
  "priceInRobux": 0
}
```

**Responses:**

- `200`: OK
- `400`: 1: Invalid target type 4: Invalid Argument 8: Missing/Null request parameters 23: No experiences were listed when trying to whitelist by Experience Ids 26: The upload content Name or Description was moderated. 37: Invalid CollectibleItemId. 59: Price offset is invalid. 60: Minimum price is invalid. 61: Invalid sale status. 65: Unexpected Place Ids. 76: The item is delisted. 79: Invalid Sale Location Update. 82: Invalid scheduled sale status. 85: OnSaleTime is in the past. 86: OffSaleTime is in the past. 87: OnSaleTime too far in the future. 88: OffSaleTime too far in the future. 89: OffSaleTime is before OnSaleTime. 90: Scheduled Time On Sale too short. 91: Scheduled Time Already Set. 92: Scheduled Time cannot set item on sale again. 93: Scheduled Time cannot set item off sale again. 146: Agreement is not publishable. 147: Resale is not allowed by the license. 148: Immediate on-sale is not allowed while the agreement is pending. 149: OnSaleTime is outside the agreement window. 150: OffSaleTime is outside the agreement window. 151: OffSaleTime is required for this agreement.
- `401`: 0: Authorization has been denied for this request. 66: Missing Authenticated User.
- `403`: 0: Token Validation Failed 12: User does not have permission for the group owned asset 18: User does not own the item 39: Group created items are currently not supported. 72: The Item is moderated. 74: The item's type is not allowed. 77: Resellable creation not allowed for user. 84: Scheduled publishing not enabled. 106: Missing ID verification. 107: User's creation access is blocked. 108: Missing premium subscription tier. 109: Group owner missing premium subscription tier. 125: Missing two step verification.
- `404`: 3: Service Unavailable 5: Not Found 37: Invalid CollectibleItemId. 71: The Item is not found.
- `409`: 142: Resale is locked after restock.
- `412`: 75: The item has archived dependencies.
- `500`: 38: Failed to get Collectible Item information. 56: Publishing Gateway returns unexpected exception. 67: Invalid creator type 73: The Item's moderation status could not be determined. 144: Failed to get agreement. 145: Failed to get license.

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 1/second

**Example:**
```bash
curl -X PATCH -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/collectibles/{COLLECTIBLEITEMID}" \
  -H "Content-Type: application/json" \
  -d '{
  "saleLocationConfiguration": {
    "saleLocationType": 0,
    "places": [
      "..."
    ]
  },
  "isRentalOptIn": false,
  "saleStatus": 0,
  "quantityLimitPerUser": 0,
  "resaleRestriction": 0,
  "priceInRobux": 0
}'
```

### POST `/v1/collectibles/{collectibleItemId}/restock` [EXPERIMENTAL]

Restock a published limited collectible item by adding additional quantity.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:publish`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `collectibleItemId` | path | `string` | Yes |  |

**Request Body:** `application/json` — Type: `Roblox.ItemConfiguration.Api.Models.Request.Collectibles.RestockCollectibleItemRequest`

See [Roblox.ItemConfiguration.Api.Models.Request.Collectibles.RestockCollectibleItemRequest](#roblox-itemconfiguration-api-models-request-collectibles-restockcollectibleitemrequest) in Models.

**Request example:**
```json
{
  "newTotalQuantity": 0,
  "agreedRestockingFee": 0
}
```

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.Models.Response.Collectibles.RestockCollectibleItemResponse`
- `400`: 37: Invalid CollectibleItemId. 137: The agreed restocking fee is invalid. 139: The additional quantity for restocking is invalid.
- `401`: 0: Authorization has been denied for this request. 66: Missing Authenticated User.
- `402`: 70: The user does not have enough Robux to pay
- `403`: 0: Token Validation Failed 12: User does not have permission for the group owned asset 18: User does not own the item 94: Actor is moderated. 106: Missing ID verification. 107: User's creation access is blocked. 108: Missing premium subscription tier. 109: Group owner missing premium subscription tier. 125: Missing two step verification. 136: Item is not eligible for restocking because it has been resellable.
- `404`: 3: Service Unavailable
- `500`: 38: Failed to get Collectible Item information. 56: Publishing Gateway returns unexpected exception. 103: Publishing gateway returns denied without any reason 104: Publishing gateway returns unexpected reason 105: Publishing gateway returns unexpected access status 138: Failed to restock the collectible item.

**Response fields** (`Roblox.ItemConfiguration.Api.Models.Response.Collectibles.RestockCollectibleItemResponse`)

See [Roblox.ItemConfiguration.Api.Models.Response.Collectibles.RestockCollectibleItemResponse](#roblox-itemconfiguration-api-models-response-collectibles-restockcollectibleitemresponse) in Models.

**Response example:**
```json
{
  "newTotalQuantity": 0
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 1/second

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/collectibles/{COLLECTIBLEITEMID}/restock" \
  -H "Content-Type: application/json" \
  -d '{
  "newTotalQuantity": 0,
  "agreedRestockingFee": 0
}'
```

### GET `/v1/collectibles/{collectibleItemId}/restock-eligibility` [EXPERIMENTAL]

Returns structured restock eligibility information for a given collectible item.
This is the single source of truth the frontend should use to determine whether
restocking is available, instead of re-deriving from individual flags.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `collectibleItemId` | path | `string` | Yes |  |

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.Models.Response.Collectibles.RestockEligibilityResponse`
- `400`: 37: Invalid CollectibleItemId.
- `401`: 0: Authorization has been denied for this request.
- `403`: 12: User does not have permission for the group owned asset 18: User does not own the item
- `404`: 3: Service Unavailable
- `500`: 38: Failed to get Collectible Item information. 141: Failed to get restock eligibility.

**Response fields** (`Roblox.ItemConfiguration.Api.Models.Response.Collectibles.RestockEligibilityResponse`)

See [Roblox.ItemConfiguration.Api.Models.Response.Collectibles.RestockEligibilityResponse](#roblox-itemconfiguration-api-models-response-collectibles-restockeligibilityresponse) in Models.

**Response example:**
```json
{
  "isRestockingEnabled": false,
  "isEligible": false,
  "ineligibilityReason": 0,
  "hasBeenRestocked": false,
  "totalRestockedQuantity": 0,
  "maxRestockQuantityPerOperation": 0
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/collectibles/{COLLECTIBLEITEMID}/restock-eligibility"
```

### GET `/v1/collectibles/{collectibleItemId}/restocking-fees` [EXPERIMENTAL]

Get the restocking fee for a given collectible item and additional quantity.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `collectibleItemId` | path | `string` | Yes |  |
| `AdditionalQuantity` | query | `integer` | Yes | Number of additional units to add. |

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.Models.Response.Collectibles.RestockingFeeResponse`
- `400`: 37: Invalid CollectibleItemId. 136: Item is not eligible for restocking because it has been resellable. 139: The additional quantity for restocking is invalid.
- `401`: 0: Authorization has been denied for this request.
- `403`: 12: User does not have permission for the group owned asset 18: User does not own the item
- `500`: 140: Failed to fetch restocking fee.

**Response fields** (`Roblox.ItemConfiguration.Api.Models.Response.Collectibles.RestockingFeeResponse`)

See [Roblox.ItemConfiguration.Api.Models.Response.Collectibles.RestockingFeeResponse](#roblox-itemconfiguration-api-models-response-collectibles-restockingfeeresponse) in Models.

**Response example:**
```json
{
  "restockingFeeInRobux": 0,
  "unitRestockingFeeInRobux": 0
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/collectibles/{COLLECTIBLEITEMID}/restocking-fees?AdditionalQuantity={VALUE}"
```

### DELETE `/v1/collectibles/{collectibleItemId}/sale-schedule` [EXPERIMENTAL]

Cancel the collectible item's scheduled on/off sale time.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `collectibleItemId` | path | `string` | Yes |  |

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.CancelScheduledSaleStatusResponse`
- `400`: 37: Invalid CollectibleItemId. 83: Invalid cancel scheduled sale status request.
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed 66: Missing Authenticated User.
- `404`: 3: Service Unavailable
- `500`: 56: Publishing Gateway returns unexpected exception. 104: Publishing gateway returns unexpected reason

**Response fields** (`Roblox.ItemConfiguration.Api.CancelScheduledSaleStatusResponse`)

See [Roblox.ItemConfiguration.Api.CancelScheduledSaleStatusResponse](#roblox-itemconfiguration-api-cancelscheduledsalestatusresponse) in Models.

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -X DELETE -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/collectibles/{COLLECTIBLEITEMID}/sale-schedule"
```

### POST `/v1/creations/get-asset-details`

Gets the asset status and other configuration details for the given assetIds list.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Request Body:** `application/json` — Type: `Roblox.ItemConfiguration.Api.AssetCreationsDetailsRequest`

See [Roblox.ItemConfiguration.Api.AssetCreationsDetailsRequest](#roblox-itemconfiguration-api-assetcreationsdetailsrequest) in Models.

**Request example:**
```json
{
  "AssetIds": [
    0
  ]
}
```

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.AssetCreationsDetailsResponse[]`
- `400`: 1: Missing AssetIds parameters 2: Invalid asset Ids
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed
- `414`: 3: Too many asset Ids
- `429`: 9: Flood Limit Exceeded
- `503`: 6: Service Unavailable

**Response fields** (`Roblox.ItemConfiguration.Api.AssetCreationsDetailsResponse[]`)

See [Roblox.ItemConfiguration.Api.AssetCreationsDetailsResponse](#roblox-itemconfiguration-api-assetcreationsdetailsresponse) in Models.

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/creations/get-asset-details" \
  -H "Content-Type: application/json" \
  -d '{
  "AssetIds": [
    0
  ]
}'
```

### GET `/v1/creations/get-assets`

Gets the user created asset information filtered by the given asset type.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetType` | query | `string` | Yes |  |
| `isArchived` | query | `boolean` | No |  |
| `groupId` | query | `integer` | No |  |
| `limit` | query | `10 \| 25 \| 50 \| 100` | No | The number of results per request. Valid values: `10`, `25`, `50`, `100` |
| `cursor` | query | `string` | No | The paging cursor for the previous or next page. |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.ItemConfiguration.Api.AssetCreationsResponse_`
- `400`: 5: Invalid assetType 10: Invalid Asset Category
- `401`: 0: Authorization has been denied for this request.
- `403`: 7: User does not have necessary permissions for group 8: Asset type does not have necessary permissions for group
- `429`: 9: Flood Limit Exceeded
- `503`: 6: Service Unavailable

**Response fields** (`Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.ItemConfiguration.Api.AssetCreationsResponse_`)

See [Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.ItemConfiguration.Api.AssetCreationsResponse_](#roblox-web-webapi-models-apipageresponse-roblox-itemconfiguration-api-assetcreationsresponse-) in Models.

**Response example:**
```json
{
  "previousPageCursor": "string",
  "nextPageCursor": "string",
  "data": [
    {
      "assetId": "...",
      "name": "..."
    }
  ]
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 1/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/creations/get-assets?assetType={VALUE}"
```

### POST `/v1/delist-item` [EXPERIMENTAL]

Delists an item, permanently archiving it so it is no longer visible to any users on the marketplace.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `TargetType` | query | `0 \| 1 \| 2 \| 3` | Yes | The type of the target item. Valid values: `0`, `1`, `2`, `3` |
| `TargetId` | query | `integer` | Yes | The id of the target item. |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.ApiEmptyResponseModel`
- `400`: 2: Invalid target argument (item type or item id). 3: Attempted to delist an item that was created too recently. 4: User request error and is blocked from delisting this item.
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed 1: Item not owned. The user/group does not have permission to delist the item.
- `500`: 0: Unknown

**Response fields** (`Roblox.Web.WebAPI.ApiEmptyResponseModel`)

See [Roblox.Web.WebAPI.ApiEmptyResponseModel](#roblox-web-webapi-apiemptyresponsemodel) in Models.

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 1/second

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/delist-item?TargetType={VALUE}&TargetId={VALUE}"
```

### GET `/v1/favorites/assets/{assetId}/count` [EXPERIMENTAL]

Gets the favorite count for the given asset Id.

**Server:** `https://catalog.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetId` | path | `integer` | Yes |  |

**Responses:**

- `200`: OK → `integer`
- `400`: 2: Invalid asset Id.

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://catalog.roblox.com/v1/favorites/assets/{ASSETID}/count"
```

### GET `/v1/favorites/bundles/{bundleId}/count` [EXPERIMENTAL]

Gets the favorite count for the given bundle Id.

**Server:** `https://catalog.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `bundleId` | path | `integer` | Yes |  |

**Responses:**

- `200`: OK → `integer`
- `400`: 2: Invalid bundle Id.

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://catalog.roblox.com/v1/favorites/bundles/{BUNDLEID}/count"
```

### GET `/v1/favorites/users/{userId}/assets/{assetId}/favorite` [EXPERIMENTAL]

Gets the favorite model for the asset and user.

**Server:** `https://catalog.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `userId` | path | `integer` | Yes |  |
| `assetId` | path | `integer` | Yes |  |

**Responses:**

- `200`: OK → `Roblox.Catalog.Api.AssetFavoriteModel`
- `400`: 1: Invalid user Id. 2: Invalid asset Id.
- `401`: 0: Authorization has been denied for this request.

**Response fields** (`Roblox.Catalog.Api.AssetFavoriteModel`)

See [Roblox.Catalog.Api.AssetFavoriteModel](#roblox-catalog-api-assetfavoritemodel) in Models.

**Response example:**
```json
{
  "assetId": 0,
  "userId": 0,
  "created": "2024-01-01T00:00:00Z"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://catalog.roblox.com/v1/favorites/users/{USERID}/assets/{ASSETID}/favorite"
```

### POST `/v1/favorites/users/{userId}/assets/{assetId}/favorite` [EXPERIMENTAL]

Create a favorite for an asset by the authenticated user.

**Server:** `https://catalog.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `userId` | path | `integer` | Yes |  |
| `assetId` | path | `integer` | Yes |  |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.ApiEmptyResponseModel`
- `400`: 1: Invalid user Id. 2: Invalid asset Id.
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed 6: You are not authorized to perform this action.
- `409`: 3: Asset is already favorited.
- `429`: 5: This action was floodchecked. Please try again later.

**Response fields** (`Roblox.Web.WebAPI.ApiEmptyResponseModel`)

See [Roblox.Web.WebAPI.ApiEmptyResponseModel](#roblox-web-webapi-apiemptyresponsemodel) in Models.

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://catalog.roblox.com/v1/favorites/users/{USERID}/assets/{ASSETID}/favorite"
```

### DELETE `/v1/favorites/users/{userId}/assets/{assetId}/favorite` [EXPERIMENTAL]

Delete a favorite for an asset by the authenticated user.

**Server:** `https://catalog.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `userId` | path | `integer` | Yes |  |
| `assetId` | path | `integer` | Yes |  |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.ApiEmptyResponseModel`
- `400`: 1: Invalid user Id. 2: Invalid asset Id.
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed 6: You are not authorized to perform this action.
- `409`: 4: Asset is already not favorited.
- `429`: 5: This action was floodchecked. Please try again later.

**Response fields** (`Roblox.Web.WebAPI.ApiEmptyResponseModel`)

See [Roblox.Web.WebAPI.ApiEmptyResponseModel](#roblox-web-webapi-apiemptyresponsemodel) in Models.

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X DELETE -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://catalog.roblox.com/v1/favorites/users/{USERID}/assets/{ASSETID}/favorite"
```

### GET `/v1/favorites/users/{userId}/bundles/{bundleId}/favorite` [EXPERIMENTAL]

Gets the favorite model for the bundle and user.

**Server:** `https://catalog.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `userId` | path | `integer` | Yes |  |
| `bundleId` | path | `integer` | Yes |  |

**Responses:**

- `200`: OK → `Roblox.Catalog.Api.BundleFavoriteModel`
- `400`: 1: Invalid user Id. 2: Invalid bundle Id.
- `401`: 0: Authorization has been denied for this request.

**Response fields** (`Roblox.Catalog.Api.BundleFavoriteModel`)

See [Roblox.Catalog.Api.BundleFavoriteModel](#roblox-catalog-api-bundlefavoritemodel) in Models.

**Response example:**
```json
{
  "bundleId": 0,
  "userId": 0,
  "created": "2024-01-01T00:00:00Z"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://catalog.roblox.com/v1/favorites/users/{USERID}/bundles/{BUNDLEID}/favorite"
```

### POST `/v1/favorites/users/{userId}/bundles/{bundleId}/favorite` [EXPERIMENTAL]

Create a favorite for the bundle by the authenticated user.

**Server:** `https://catalog.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `userId` | path | `integer` | Yes |  |
| `bundleId` | path | `integer` | Yes |  |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.ApiEmptyResponseModel`
- `400`: 1: Invalid user Id. 2: Invalid bundle Id.
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed 6: You are not authorized to perform this action.
- `409`: 3: Bundle is already favorited.
- `429`: 5: This action was floodchecked. Please try again later.

**Response fields** (`Roblox.Web.WebAPI.ApiEmptyResponseModel`)

See [Roblox.Web.WebAPI.ApiEmptyResponseModel](#roblox-web-webapi-apiemptyresponsemodel) in Models.

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://catalog.roblox.com/v1/favorites/users/{USERID}/bundles/{BUNDLEID}/favorite"
```

### DELETE `/v1/favorites/users/{userId}/bundles/{bundleId}/favorite` [EXPERIMENTAL]

Delete favorite for the bundle by the authenticated user.

**Server:** `https://catalog.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `userId` | path | `integer` | Yes |  |
| `bundleId` | path | `integer` | Yes |  |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.ApiEmptyResponseModel`
- `400`: 1: Invalid user Id. 2: Invalid bundle Id.
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed 6: You are not authorized to perform this action.
- `409`: 4: Bundle is already not favorited.
- `429`: 5: This action was floodchecked. Please try again later.

**Response fields** (`Roblox.Web.WebAPI.ApiEmptyResponseModel`)

See [Roblox.Web.WebAPI.ApiEmptyResponseModel](#roblox-web-webapi-apiemptyresponsemodel) in Models.

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X DELETE -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://catalog.roblox.com/v1/favorites/users/{USERID}/bundles/{BUNDLEID}/favorite"
```

### GET `/v1/favorites/users/{userId}/favorites/{assetTypeId}/assets` [EXPERIMENTAL]

Lists the marketplace assets favorited by a given user with the given assetTypeId.

**Server:** `https://catalog.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `userId` | path | `integer` | Yes |  |
| `assetTypeId` | path | `integer` | Yes |  |
| `limit` | query | `integer enum (6 values)` | No | The number of results per request. Valid values: `10`, `18`, `24`, `25`, `50`, `100` |
| `cursor` | query | `string` | No | The paging cursor for the previous or next page. |
| `sortOrder` | query | `Asc \| Desc` | No | The order the results are sorted in. Valid values: `Asc`, `Desc` |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Catalog.Api.CatalogSearchDetailedResponseItem_`
- `400`: 1: Invalid user Id. 8: Ascending order is not allowed. 11: Invalid asset type id.
- `500`: 99: Internal server error.

**Response fields** (`Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Catalog.Api.CatalogSearchDetailedResponseItem_`)

See [Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Catalog.Api.CatalogSearchDetailedResponseItem_](#roblox-web-webapi-models-apipageresponse-roblox-catalog-api-catalogsearchdetailedresponseitem-) in Models.

**Response example:**
```json
{
  "previousPageCursor": "string",
  "nextPageCursor": "string",
  "data": [
    {
      "id": "...",
      "itemType": "...",
      "assetType": "...",
      "bundleType": "...",
      "isRecolorable": "...",
      "name": "..."
    }
  ]
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://catalog.roblox.com/v1/favorites/users/{USERID}/favorites/{ASSETTYPEID}/assets"
```

### GET `/v1/favorites/users/{userId}/favorites/{subtypeId}/bundles` [EXPERIMENTAL]

Lists the bundles favorited by a given user with the given bundle subtypeId.Switched to EAAS style pagination cursors since July 2024.

**Server:** `https://catalog.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `userId` | path | `integer` | Yes |  |
| `subtypeId` | path | `integer` | Yes |  |
| `itemsPerPage` | query | `integer` | No |  |
| `cursor` | query | `string` | No |  |
| `isPrevious` | query | `boolean` | No |  |

**Responses:**

- `200`: OK → `Roblox.Catalog.Api.FavoriteBundlesResponse`
- `400`: 1: Invalid user Id. 3: Cannot request so many bundles at once. 10: Invalid previous pagination request. Please provide a cursor when isPrevious is true
- `401`: 0: Authorization has been denied for this request.
- `403`: 6: You are not authorized to perform this action.
- `500`: 11: Internal server error. Please check if you have provided correct pagination cursor

**Response fields** (`Roblox.Catalog.Api.FavoriteBundlesResponse`)

See [Roblox.Catalog.Api.FavoriteBundlesResponse](#roblox-catalog-api-favoritebundlesresponse) in Models.

**Response example:**
```json
{
  "favorites": [
    {
      "id": "...",
      "name": "...",
      "description": "...",
      "bundleType": "...",
      "isRecolorable": "...",
      "items": "..."
    }
  ],
  "moreFavorites": false,
  "nextCursor": "string",
  "previousCursor": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://catalog.roblox.com/v1/favorites/users/{USERID}/favorites/{SUBTYPEID}/bundles"
```

### GET `/v1/folders` [EXPERIMENTAL]

Gets all folders belonging to the User or a Group.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | query | `integer` | No | The group ID if getting items for a group. |

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.Models.Response.Folder.GetFoldersResponse`
- `400`: 13: Group ID is invalid.
- `401`: 0: Authorization has been denied for this request. 7: The authenticated user is missing.
- `403`: 10: The user does not have permission to perform the operation.
- `503`: 11: The service is unavailable.

**Response fields** (`Roblox.ItemConfiguration.Api.Models.Response.Folder.GetFoldersResponse`)

See [Roblox.ItemConfiguration.Api.Models.Response.Folder.GetFoldersResponse](#roblox-itemconfiguration-api-models-response-folder-getfoldersresponse) in Models.

**Response example:**
```json
{
  "folders": [
    {
      "folderId": "...",
      "name": "...",
      "parentFolderId": "..."
    }
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/folders"
```

### POST `/v1/folders` [EXPERIMENTAL]

Creates a new folder.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:write`

**Request Body:** `application/json` — Type: `Roblox.ItemConfiguration.Api.Models.Request.Folder.CreateFolderRequest`

See [Roblox.ItemConfiguration.Api.Models.Request.Folder.CreateFolderRequest](#roblox-itemconfiguration-api-models-request-folder-createfolderrequest) in Models.

**Request example:**
```json
{
  "name": "string",
  "parentFolderId": "string",
  "groupId": 0
}
```

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.Models.Response.Folder.CreateFolderResponse`
- `400`: 2: The folder name is invalid. 12: Missing/Null request parameters 13: Group ID is invalid. 14: Folder name is moderated. 20: The folder limit has been reached.
- `401`: 0: Authorization has been denied for this request. 7: The authenticated user is missing.
- `403`: 0: Token Validation Failed 10: The user does not have permission to perform the operation.
- `503`: 11: The service is unavailable.

**Response fields** (`Roblox.ItemConfiguration.Api.Models.Response.Folder.CreateFolderResponse`)

See [Roblox.ItemConfiguration.Api.Models.Response.Folder.CreateFolderResponse](#roblox-itemconfiguration-api-models-response-folder-createfolderresponse) in Models.

**Response example:**
```json
{
  "folderId": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 1/second

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/folders" \
  -H "Content-Type: application/json" \
  -d '{
  "name": "string",
  "parentFolderId": "string",
  "groupId": 0
}'
```

### GET `/v1/folders/{folderId}` [EXPERIMENTAL]

Get a specific folder by its ID.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `folderId` | path | `string` | Yes | The ID of the folder. |

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.Models.Folder.Folder`
- `400`: 1: The folder ID is invalid.
- `401`: 0: Authorization has been denied for this request. 7: The authenticated user is missing.
- `403`: 8: The user does not own the folder.
- `404`: 5: The folder was not found.
- `503`: 11: The service is unavailable.

**Response fields** (`Roblox.ItemConfiguration.Api.Models.Folder.Folder`)

See [Roblox.ItemConfiguration.Api.Models.Folder.Folder](#roblox-itemconfiguration-api-models-folder-folder) in Models.

**Response example:**
```json
{
  "folderId": "string",
  "name": "string",
  "parentFolderId": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/folders/{FOLDERID}"
```

### PATCH `/v1/folders/{folderId}` [EXPERIMENTAL]

Updates folder details.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `folderId` | path | `string` | Yes | The ID of the folder to update. |

**Request Body:** `application/json` — Type: `Roblox.ItemConfiguration.Api.Models.Request.Folder.UpdateFolderRequest`

See [Roblox.ItemConfiguration.Api.Models.Request.Folder.UpdateFolderRequest](#roblox-itemconfiguration-api-models-request-folder-updatefolderrequest) in Models.

**Request example:**
```json
{
  "name": "string"
}
```

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.ApiEmptyResponseModel`
- `400`: 1: The folder ID is invalid. 2: The folder name is invalid. 12: Missing/Null request parameters 14: Folder name is moderated.
- `401`: 0: Authorization has been denied for this request. 7: The authenticated user is missing.
- `403`: 0: Token Validation Failed 8: The user does not own the folder.
- `404`: 5: The folder was not found.
- `503`: 11: The service is unavailable.

**Response fields** (`Roblox.Web.WebAPI.ApiEmptyResponseModel`)

See [Roblox.Web.WebAPI.ApiEmptyResponseModel](#roblox-web-webapi-apiemptyresponsemodel) in Models.

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 1/second

**Example:**
```bash
curl -X PATCH -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/folders/{FOLDERID}" \
  -H "Content-Type: application/json" \
  -d '{
  "name": "string"
}'
```

### DELETE `/v1/folders/{folderId}` [EXPERIMENTAL]

Deletes a folder.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `folderId` | path | `string` | Yes | The ID of the folder to delete. |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.ApiEmptyResponseModel`
- `400`: 1: The folder ID is invalid.
- `401`: 0: Authorization has been denied for this request. 7: The authenticated user is missing.
- `403`: 0: Token Validation Failed 8: The user does not own the folder.
- `404`: 5: The folder was not found.
- `503`: 11: The service is unavailable.

**Response fields** (`Roblox.Web.WebAPI.ApiEmptyResponseModel`)

See [Roblox.Web.WebAPI.ApiEmptyResponseModel](#roblox-web-webapi-apiemptyresponsemodel) in Models.

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 1/second

**Example:**
```bash
curl -X DELETE -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/folders/{FOLDERID}"
```

### GET `/v1/folders/{folderId}/items` [EXPERIMENTAL]

Gets the contents of a specific folder.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `folderId` | path | `string` | Yes | The ID of the folder to get items from. |
| `limit` | query | `integer` | No | Number of items per page. |
| `cursor` | query | `string` | No | Pagination cursor from a previous response. Omit for the first page. |

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.Models.Response.Folder.GetFolderItemsResponse`
- `400`: 1: The folder ID is invalid. 16: The limit is invalid. 17: The pagination cursor is invalid.
- `401`: 0: Authorization has been denied for this request. 7: The authenticated user is missing.
- `403`: 8: The user does not own the folder.
- `404`: 5: The folder was not found.
- `503`: 11: The service is unavailable.

**Response fields** (`Roblox.ItemConfiguration.Api.Models.Response.Folder.GetFolderItemsResponse`)

See [Roblox.ItemConfiguration.Api.Models.Response.Folder.GetFolderItemsResponse](#roblox-itemconfiguration-api-models-response-folder-getfolderitemsresponse) in Models.

**Response example:**
```json
{
  "items": [
    {
      "id": "...",
      "marketplaceItem": "...",
      "folder": "..."
    }
  ],
  "nextCursor": "string",
  "prevCursor": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/folders/{FOLDERID}/items"
```

### POST `/v1/folders/{folderId}/items` [EXPERIMENTAL]

Adds one or more items to a folder.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `folderId` | path | `string` | Yes | The ID of the folder to add items to. |

**Request Body:** `application/json` — Type: `Roblox.ItemConfiguration.Api.Models.Request.Folder.AddItemsRequest`

See [Roblox.ItemConfiguration.Api.Models.Request.Folder.AddItemsRequest](#roblox-itemconfiguration-api-models-request-folder-additemsrequest) in Models.

**Request example:**
```json
{
  "items": [
    {
      "id": "...",
      "itemType": "..."
    }
  ]
}
```

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.ApiEmptyResponseModel`
- `400`: 1: The folder ID is invalid. 3: The item ID is invalid. 4: The item type is invalid. 12: Missing/Null request parameters 18: Too many items were passed in a single request. 19: The folder item limit has been reached.
- `401`: 0: Authorization has been denied for this request. 7: The authenticated user is missing.
- `403`: 0: Token Validation Failed 8: The user does not own the folder. 9: The user does not own the item.
- `404`: 5: The folder was not found. 6: The item was not found.
- `503`: 11: The service is unavailable.

**Response fields** (`Roblox.Web.WebAPI.ApiEmptyResponseModel`)

See [Roblox.Web.WebAPI.ApiEmptyResponseModel](#roblox-web-webapi-apiemptyresponsemodel) in Models.

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 1/second

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/folders/{FOLDERID}/items" \
  -H "Content-Type: application/json" \
  -d '{
  "items": [
    {
      "id": "...",
      "itemType": "..."
    }
  ]
}'
```

### DELETE `/v1/folders/{folderId}/items` [EXPERIMENTAL]

Removes one or more items from a folder.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `folderId` | path | `string` | Yes | The ID of the folder to remove items from. |

**Request Body:** `application/json` — Type: `Roblox.ItemConfiguration.Api.Models.Request.Folder.DeleteItemsRequest`

See [Roblox.ItemConfiguration.Api.Models.Request.Folder.DeleteItemsRequest](#roblox-itemconfiguration-api-models-request-folder-deleteitemsrequest) in Models.

**Request example:**
```json
{
  "items": [
    {
      "id": "...",
      "itemType": "..."
    }
  ]
}
```

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.ApiEmptyResponseModel`
- `400`: 1: The folder ID is invalid. 3: The item ID is invalid. 4: The item type is invalid. 12: Missing/Null request parameters 18: Too many items were passed in a single request.
- `401`: 0: Authorization has been denied for this request. 7: The authenticated user is missing.
- `403`: 0: Token Validation Failed 8: The user does not own the folder.
- `404`: 5: The folder was not found.
- `503`: 11: The service is unavailable.

**Response fields** (`Roblox.Web.WebAPI.ApiEmptyResponseModel`)

See [Roblox.Web.WebAPI.ApiEmptyResponseModel](#roblox-web-webapi-apiemptyresponsemodel) in Models.

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 1/second

**Example:**
```bash
curl -X DELETE -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/folders/{FOLDERID}/items" \
  -H "Content-Type: application/json" \
  -d '{
  "items": [
    {
      "id": "...",
      "itemType": "..."
    }
  ]
}'
```

### POST `/v1/games/{gameId}/thumbnail/image`

Uploads a game thumbnail.

**Server:** `https://publish.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `gameId` | path | `integer` | Yes | The universe Id. |

**Responses:**

- `200`: OK → `Roblox.Publish.Api.UploadResponse`
- `400`: 1: File uploaded does not match known image format. Try converting to png. 2: File not present in request.
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed 5: You do not have permission to manage this item.
- `404`: 4: Target item is invalid or does not exist.
- `429`: 3: You're uploading too much, please wait and try again later.

**Response fields** (`Roblox.Publish.Api.UploadResponse`)

See [Roblox.Publish.Api.UploadResponse](#roblox-publish-api-uploadresponse) in Models.

**Response example:**
```json
{
  "targetId": 0
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://publish.roblox.com/v1/games/{GAMEID}/thumbnail/image" \
  -H "Content-Type: application/json" \
  -d '{"key": "value"}'
```

### GET `/v1/items` [EXPERIMENTAL]

Get an item by its id.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `itemType` | query | `0 \| 1 \| 2 \| 3` | Yes | Target Type for a collectible item. ['Asset' = 0, 'Bundle' = 1, 'IecToken' = 2, 'Look' = 3] Valid values: `0`, `1`, `2`, `3` |
| `itemId` | query | `string` | Yes |  |

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.GetItemResponse`
- `400`: 0: Unknown issues with configuration
- `401`: 0: Authorization has been denied for this request.
- `404`: 1: Service Unavailable
- `500`: 0: Unknown issues with configuration

**Response fields** (`Roblox.ItemConfiguration.Api.GetItemResponse`)

See [Roblox.ItemConfiguration.Api.GetItemResponse](#roblox-itemconfiguration-api-getitemresponse) in Models.

**Response example:**
```json
{
  "item": {
    "id": "string",
    "marketplaceItemDetails": {
      "assetDetails": "...",
      "bundleDetails": "..."
    },
    "createdTime": "2024-01-01T00:00:00Z",
    "name": "string",
    "description": "string",
    "creator": {
      "User": "...",
      "Group": "...",
      "KindCase": "..."
    }
  }
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/items?itemType={VALUE}&itemId={VALUE}"
```

### GET `/v1/items/by-creator` [EXPERIMENTAL]

Gets the marketplace items for a creator by item type (e.g. bundle, asset).

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `bundleType` | query | `0 \| 1 \| 2 \| 3 \| 4` | No | The type of bundles to get for the creator. Valid values: `0`, `1`, `2`, `3`, `4` |
| `assetType` | query | `integer enum (92 values)` | No | The type of assets to get for the creator. Valid values: `0`, `1`, `2`, `3`, `4`, `5`, `6`, `7`, `8`, `9`, `10`, `11`, `12`, `13`, `16`, `17`, `18`, `19`, `21`, `22`, `24`, `25`, `26`, `27`, `28`, `29`, `30`, `31`, `32`, `33`, `34`, `35`, `37`, `38`, `39`, `40`, `41`, `42`, `43`, `44`, `45`, `46`, `47`, `48`, `49`, `50`, `51`, `52`, `53`, `54`, `55`, `56`, `59`, `60`, `61`, `62`, `63`, `64`, `65`, `66`, `67`, `68`, `69`, `70`, `71`, `72`, `73`, `74`, `75`, `76`, `77`, `78`, `79`, `80`, `81`, `82`, `83`, `84`, `85`, `86`, `87`, `88`, `89`, `90`, `91`, `92`, `93`, `94`, `95`, `96`, `97`, `98` |
| `taxonomy` | query | `string` | No | Taxonomy category web_stable_id to filter by (mutually exclusive with bundleType/assetType). Passed through to AMPG, which resolves it server-side. |
| `cursor` | query | `string` | No | The pagination cursor. |
| `limit` | query | `integer` | No | The limit of the AMPG call. |
| `groupId` | query | `integer` | No | The group id if getting items for a group. |

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.GetItemsByCreatorResponse`
- `400`: 0: Unknown issues with configuration 3: The provided asset type or bundle type is not allowed 4: Invalid limit 5: Page size out of range 6: Invalid cursor 13: Both an asset type and a bundle type were provided or neither was provided 18: The provided taxonomy was not found
- `401`: 0: Authorization has been denied for this request.
- `403`: 2: User does not have necessary permissions for group
- `500`: 0: Unknown issues with configuration
- `503`: 1: Service Unavailable

**Response fields** (`Roblox.ItemConfiguration.Api.GetItemsByCreatorResponse`)

See [Roblox.ItemConfiguration.Api.GetItemsByCreatorResponse](#roblox-itemconfiguration-api-getitemsbycreatorresponse) in Models.

**Response example:**
```json
{
  "items": [
    {
      "id": "...",
      "marketplaceItemDetails": "...",
      "createdTime": "...",
      "name": "...",
      "description": "...",
      "creator": "..."
    }
  ],
  "nextCursor": "string",
  "prevCursor": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/items/by-creator"
```

### GET `/v1/items/by-token` [EXPERIMENTAL]

Gets the marketplace items for a token (i.e. an IEC avatar creation token).

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `tokenId` | query | `string` | Yes | The id of the creation token. |
| `limit` | query | `integer` | Yes | The maximum number of items that will be returned. |
| `cursor` | query | `string` | No | The pagination cursor. |

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.Models.Response.GetItemsByTokenResponse`
- `400`: 0: Unknown issues with configuration 3: The provided asset type or bundle type is not allowed 4: Invalid limit 5: Page size out of range 6: Invalid cursor
- `401`: 0: Authorization has been denied for this request.
- `403`: 2: User does not have necessary permissions for group 9: The user is not authenticated
- `404`: 10: Item was not found
- `500`: 0: Unknown issues with configuration
- `503`: 1: Service Unavailable

**Response fields** (`Roblox.ItemConfiguration.Api.Models.Response.GetItemsByTokenResponse`)

See [Roblox.ItemConfiguration.Api.Models.Response.GetItemsByTokenResponse](#roblox-itemconfiguration-api-models-response-getitemsbytokenresponse) in Models.

**Response example:**
```json
{
  "items": [
    {
      "id": "...",
      "marketplaceItemDetails": "...",
      "createdTime": "...",
      "name": "...",
      "description": "...",
      "creator": "..."
    }
  ],
  "nextCursor": "string",
  "prevCursor": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/items/by-token?tokenId={VALUE}&limit={VALUE}"
```

### GET `/v1/items/categories` [EXPERIMENTAL]

Gets a category hierarchy (by category domain) used to render category chips,
e.g. on the creator dashboard.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `categoryDomain` | query | `0 \| 1 \| 2 \| 3` | No | The category domain to fetch, rejected unless CreatorDashboard. Valid values: `0`, `1`, `2`, `3` |

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.Models.Response.GetCategoriesResponse`
- `400`: 0: Unknown issues with configuration 19: The provided category domain is not supported
- `401`: 0: Authorization has been denied for this request.
- `404`: 1: Service Unavailable
- `500`: 0: Unknown issues with configuration

**Response fields** (`Roblox.ItemConfiguration.Api.Models.Response.GetCategoriesResponse`)

See [Roblox.ItemConfiguration.Api.Models.Response.GetCategoriesResponse](#roblox-itemconfiguration-api-models-response-getcategoriesresponse) in Models.

**Response example:**
```json
{
  "categoriesVersionId": "string",
  "categories": [
    {
      "webStableId": "...",
      "id": "...",
      "name": "...",
      "isPublishable": "...",
      "assetTypeIds": "...",
      "bundleTypeIds": "..."
    }
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/items/categories"
```

### GET `/v1/items/price-floor` [EXPERIMENTAL]

Get the price floor.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `collectibleItemType` | query | `0 \| 1 \| 2` | Yes | ['Invalid' = 0, 'Limited' = 1, 'NonLimited' = 2] Valid values: `0`, `1`, `2` |
| `creationType` | query | `0 \| 1 \| 2` | Yes | The method by which an item is created. ['Invalid' = 0, 'Studio' = 1, 'InExperience' = 2] Valid values: `0`, `1`, `2` |
| `isPbr` | query | `boolean` | Yes |  |
| `isEmissive` | query | `boolean` | Yes |  |
| `assetType` | query | `integer enum (92 values)` | No | Valid values: `0`, `1`, `2`, `3`, `4`, `5`, `6`, `7`, `8`, `9`, `10`, `11`, `12`, `13`, `16`, `17`, `18`, `19`, `21`, `22`, `24`, `25`, `26`, `27`, `28`, `29`, `30`, `31`, `32`, `33`, `34`, `35`, `37`, `38`, `39`, `40`, `41`, `42`, `43`, `44`, `45`, `46`, `47`, `48`, `49`, `50`, `51`, `52`, `53`, `54`, `55`, `56`, `59`, `60`, `61`, `62`, `63`, `64`, `65`, `66`, `67`, `68`, `69`, `70`, `71`, `72`, `73`, `74`, `75`, `76`, `77`, `78`, `79`, `80`, `81`, `82`, `83`, `84`, `85`, `86`, `87`, `88`, `89`, `90`, `91`, `92`, `93`, `94`, `95`, `96`, `97`, `98` |
| `bundleType` | query | `0 \| 1 \| 2 \| 3 \| 4` | No | Valid values: `0`, `1`, `2`, `3`, `4` |
| `categoryId` | query | `string` | No |  |

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.Models.Response.GetPriceFloorResponse`
- `400`: 0: Unknown issues with configuration 3: The provided asset type or bundle type is not allowed 13: Both an asset type and a bundle type were provided or neither was provided 15: Invalid creation type
- `401`: 0: Authorization has been denied for this request.
- `404`: 1: Service Unavailable 14: Failed to get the price floor 21: Failed to get the publishing fees
- `500`: 0: Unknown issues with configuration

**Response fields** (`Roblox.ItemConfiguration.Api.Models.Response.GetPriceFloorResponse`)

See [Roblox.ItemConfiguration.Api.Models.Response.GetPriceFloorResponse](#roblox-itemconfiguration-api-models-response-getpricefloorresponse) in Models.

**Response example:**
```json
{
  "priceFloor": 0,
  "paidItemPublishingFee": {
    "publishingFeeInRobux": 0,
    "publishingFeeType": 0,
    "displayName": "string"
  },
  "freeItemPublishingFee": {
    "publishingFeeInRobux": 0,
    "publishingFeeType": 0,
    "displayName": "string"
  }
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/items/price-floor?collectibleItemType={VALUE}&creationType={VALUE}&isPbr={VALUE}&isEmissive={VALUE}"
```

### GET `/v1/items/upload-fee` [EXPERIMENTAL]

Get the upload fee for an item type.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item-upload-fee:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `bundleType` | query | `0 \| 1 \| 2 \| 3 \| 4` | No | Valid values: `0`, `1`, `2`, `3`, `4` |
| `assetType` | query | `integer enum (92 values)` | No | Valid values: `0`, `1`, `2`, `3`, `4`, `5`, `6`, `7`, `8`, `9`, `10`, `11`, `12`, `13`, `16`, `17`, `18`, `19`, `21`, `22`, `24`, `25`, `26`, `27`, `28`, `29`, `30`, `31`, `32`, `33`, `34`, `35`, `37`, `38`, `39`, `40`, `41`, `42`, `43`, `44`, `45`, `46`, `47`, `48`, `49`, `50`, `51`, `52`, `53`, `54`, `55`, `56`, `59`, `60`, `61`, `62`, `63`, `64`, `65`, `66`, `67`, `68`, `69`, `70`, `71`, `72`, `73`, `74`, `75`, `76`, `77`, `78`, `79`, `80`, `81`, `82`, `83`, `84`, `85`, `86`, `87`, `88`, `89`, `90`, `91`, `92`, `93`, `94`, `95`, `96`, `97`, `98` |
| `IsEmissive` | query | `boolean` | No |  |

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.GetItemUploadFeeResponse`
- `400`: 0: Unknown issues with configuration 3: The provided asset type or bundle type is not allowed 13: Both an asset type and a bundle type were provided or neither was provided
- `401`: 0: Authorization has been denied for this request.
- `403`: 9: The user is not authenticated
- `404`: 1: Service Unavailable 10: Item was not found
- `500`: 0: Unknown issues with configuration 11: Failed to get the item upload fee 12: Failed to get the robux balance of the authenticated user

**Response fields** (`Roblox.ItemConfiguration.Api.GetItemUploadFeeResponse`)

See [Roblox.ItemConfiguration.Api.GetItemUploadFeeResponse](#roblox-itemconfiguration-api-getitemuploadfeeresponse) in Models.

**Response example:**
```json
{
  "canAfford": false,
  "price": 0,
  "balance": 0
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/items/upload-fee"
```

### GET `/v1/localization-table/tables/{assetId}` [EXPERIMENTAL]

Get table information by the assetId of the table.

**Server:** `https://localizationtables.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetId` | path | `integer` | Yes | The asset id associated with the table. |

**Responses:**

- `200`: OK → `Roblox.LocalizationTables.Api.GetTableResponse`
- `400`: 12: Invalid asset id.
- `401`: 0: Authorization has been denied for this request.
- `403`: 2: You do not have permission to get this table.

**Response fields** (`Roblox.LocalizationTables.Api.GetTableResponse`)

See [Roblox.LocalizationTables.Api.GetTableResponse](#roblox-localizationtables-api-gettableresponse) in Models.

**Response example:**
```json
{
  "id": "string",
  "name": "string",
  "ownerType": "User",
  "ownerId": 0,
  "assetId": 0
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://localizationtables.roblox.com/v1/localization-table/tables/{ASSETID}"
```

### GET `/v1/marAssetHash/{marAssetHash}/marCheckSum/{marCheckSum}`

Retrieves an asset by its mar (moderation agnostic) hash and mar (moderation agnostic) checksum.

**Server:** `https://assetdelivery.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `marAssetHash` | path | `string` | Yes | The mar (moderation agnostic) hash of the asset to retrieve. |
| `marCheckSum` | path | `string` | Yes | The mar (moderation agnostic) checksum of the asset to retrieve. |
| `Accept-Encoding` | header | `string` | Yes |  |
| `Roblox-Place-Id` | header | `integer` | Yes |  |
| `AssetType` | header | `string` | Yes |  |
| `AssetFormat` | header | `string` | Yes |  |
| `Roblox-AssetFormat` | header | `string` | Yes |  |
| `skipSigningScripts` | query | `boolean` | No |  |
| `clientInsert` | query | `integer` | No |  |
| `scriptinsert` | query | `integer` | No |  |
| `modulePlaceId` | query | `integer` | No |  |
| `serverplaceid` | query | `integer` | No |  |
| `expectedAssetType` | query | `string` | No |  |

**Responses:**

- `200`: OK
- `400`: 2: invalid server request 3: Encoding cannot be empty
- `404`: 5: Asset hash cannot be empty

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://assetdelivery.roblox.com/v1/marAssetHash/{MARASSETHASH}/marCheckSum/{MARCHECKSUM}"
```

### GET `/v1/permissions/action-allowed-for-item-type` [EXPERIMENTAL]

Returns whether the authenticated user (or group on their behalf) may perform the given marketplace action
for a specific asset, bundle, or look type.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `action` | query | `integer enum (7 values)` | Yes | Actions that a user can perform on a given marketplace item on behalf of either themselves or a group. ['Invalid' = 0, 'Upload' = 1, 'Publish' = 2, 'IecCreation' = 3, 'PublishDurable' = 4, 'PublishRental' = 5, 'PublishToMarketplace' = 6] Valid values: `0`, `1`, `2`, `3`, `4`, `5`, `6` |
| `groupId` | query | `integer` | No |  |
| `assetType` | query | `integer enum (92 values)` | No | Valid values: `0`, `1`, `2`, `3`, `4`, `5`, `6`, `7`, `8`, `9`, `10`, `11`, `12`, `13`, `16`, `17`, `18`, `19`, `21`, `22`, `24`, `25`, `26`, `27`, `28`, `29`, `30`, `31`, `32`, `33`, `34`, `35`, `37`, `38`, `39`, `40`, `41`, `42`, `43`, `44`, `45`, `46`, `47`, `48`, `49`, `50`, `51`, `52`, `53`, `54`, `55`, `56`, `59`, `60`, `61`, `62`, `63`, `64`, `65`, `66`, `67`, `68`, `69`, `70`, `71`, `72`, `73`, `74`, `75`, `76`, `77`, `78`, `79`, `80`, `81`, `82`, `83`, `84`, `85`, `86`, `87`, `88`, `89`, `90`, `91`, `92`, `93`, `94`, `95`, `96`, `97`, `98` |
| `bundleType` | query | `0 \| 1 \| 2 \| 3 \| 4` | No | Valid values: `0`, `1`, `2`, `3`, `4` |
| `lookType` | query | `0 \| 1 \| 2 \| 3 \| 4` | No | Valid values: `0`, `1`, `2`, `3`, `4` |
| `trustedCreatorCheck` | query | `boolean` | No |  |

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.Models.Response.IsActionAllowedForItemTypeResponse`
- `400`: 1: Invalid parameters in request.
- `401`: 0: Authorization has been denied for this request.
- `500`: 0: Unknown issues.

**Response fields** (`Roblox.ItemConfiguration.Api.Models.Response.IsActionAllowedForItemTypeResponse`)

See [Roblox.ItemConfiguration.Api.Models.Response.IsActionAllowedForItemTypeResponse](#roblox-itemconfiguration-api-models-response-isactionallowedforitemtyperesponse) in Models.

**Response example:**
```json
{
  "isActionAllowed": false,
  "metadataPermissions": "..."
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/permissions/action-allowed-for-item-type?action={VALUE}"
```

### GET `/v1/permissions/groups` [EXPERIMENTAL]

Returns a list of allowed groups for a given Roblox.ItemConfiguration.Api.Enums.MarketplaceAction.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `action` | query | `integer enum (7 values)` | Yes | Actions that a user can perform on a given marketplace item on behalf of either themselves or a group. ['Invalid' = 0, 'Upload' = 1, 'Publish' = 2, 'IecCreation' = 3, 'PublishDurable' = 4, 'PublishRental' = 5, 'PublishToMarketplace' = 6] Valid values: `0`, `1`, `2`, `3`, `4`, `5`, `6` |

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.Models.Request.AllowedGroupsForActionResponse`
- `400`: 1: Invalid parameters in request.
- `401`: 0: Authorization has been denied for this request.

**Response fields** (`Roblox.ItemConfiguration.Api.Models.Request.AllowedGroupsForActionResponse`)

See [Roblox.ItemConfiguration.Api.Models.Request.AllowedGroupsForActionResponse](#roblox-itemconfiguration-api-models-request-allowedgroupsforactionresponse) in Models.

**Response example:**
```json
{
  "allowedGroups": [
    {
      "id": "...",
      "name": "..."
    }
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/permissions/groups?action={VALUE}"
```

### GET `/v1/permissions/item-types` [EXPERIMENTAL]

Gets item types which the requested action can be performed on.

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `marketplace.item:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `action` | query | `integer enum (7 values)` | Yes | Actions that a user can perform on a given marketplace item on behalf of either themselves or a group. ['Invalid' = 0, 'Upload' = 1, 'Publish' = 2, 'IecCreation' = 3, 'PublishDurable' = 4, 'PublishRental' = 5, 'PublishToMarketplace' = 6] Valid values: `0`, `1`, `2`, `3`, `4`, `5`, `6` |
| `targetTypes` | query | `0 \| 1 \| 2 \| 3[]` | Yes | Valid values: `0`, `1`, `2`, `3` |

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.Models.Response.AllowedItemTypesForActionResponse`
- `400`: 1: Invalid parameters in request.
- `401`: 0: Authorization has been denied for this request.

**Response fields** (`Roblox.ItemConfiguration.Api.Models.Response.AllowedItemTypesForActionResponse`)

See [Roblox.ItemConfiguration.Api.Models.Response.AllowedItemTypesForActionResponse](#roblox-itemconfiguration-api-models-response-alloweditemtypesforactionresponse) in Models.

**Response example:**
```json
{
  "allowedAssetTypes": [
    "string"
  ],
  "allowedBundleTypes": [
    "string"
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 10/second

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://itemconfiguration.roblox.com/v1/permissions/item-types?action={VALUE}&targetTypes={VALUE}"
```

### GET `/v1/plugins` [EXPERIMENTAL]

Gets plugin details by ids.

**Server:** `https://develop.roblox.com`

**Auth:** 

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `pluginIds` | query | `integer[]` | Yes | The plugin ids. |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Web.Responses.Plugins.PluginResponse_`
- `400`: 1: Too many ids. 2: The format of the ids are invalid.

**Response fields** (`Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Web.Responses.Plugins.PluginResponse_`)

See [Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Web.Responses.Plugins.PluginResponse_](#roblox-web-webapi-models-apiarrayresponse-roblox-web-responses-plugins-pluginresponse-) in Models.

**Response example:**
```json
{
  "data": [
    {
      "id": "...",
      "name": "...",
      "description": "...",
      "commentsEnabled": "...",
      "versionId": "...",
      "created": "..."
    }
  ]
}
```

**Example:**
```bash
curl -H "Authorization: Bearer $ROBLOX_ACCESS_TOKEN" \
  "https://develop.roblox.com/v1/plugins?pluginIds={VALUE}"
```

### PATCH `/v1/plugins/{pluginId}` [EXPERIMENTAL]

Updates a plugin.

**Server:** `https://develop.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `pluginId` | path | `integer` | Yes | The id of the plugin. |

**Request Body:** `application/json` — Type: `Roblox.Develop.Api.UpdatePluginRequest`

See [Roblox.Develop.Api.UpdatePluginRequest](#roblox-develop-api-updatepluginrequest) in Models.

**Request example:**
```json
{
  "name": "string",
  "description": "string",
  "commentsEnabled": false
}
```

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.ApiEmptyResponseModel`
- `400`: 5: Description too long. 6: Text moderated. 7: Invalid name. 8: The request body is missing.
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed 4: Insufficient permissions.
- `404`: 3: The id is invalid.

**Response fields** (`Roblox.Web.WebAPI.ApiEmptyResponseModel`)

See [Roblox.Web.WebAPI.ApiEmptyResponseModel](#roblox-web-webapi-apiemptyresponsemodel) in Models.

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X PATCH -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://develop.roblox.com/v1/plugins/{PLUGINID}" \
  -H "Content-Type: application/json" \
  -d '{
  "name": "string",
  "description": "string",
  "commentsEnabled": false
}'
```

### POST `/v1/plugins/{pluginId}/icon`

Overwrites a plugin icon with a new one.

**Server:** `https://publish.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `pluginId` | path | `integer` | Yes | The plugin Id. |

**Responses:**

- `200`: OK → `Roblox.Publish.Api.UploadResponse`
- `400`: 2: File not present in request.
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed 5: You do not have permission to manage this item.
- `404`: 4: Target item is invalid or does not exist.
- `429`: 3: You're uploading too much, please wait and try again later.

**Response fields** (`Roblox.Publish.Api.UploadResponse`)

See [Roblox.Publish.Api.UploadResponse](#roblox-publish-api-uploadresponse) in Models.

**Response example:**
```json
{
  "targetId": 0
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://publish.roblox.com/v1/plugins/{PLUGINID}/icon" \
  -H "Content-Type: application/json" \
  -d '{"key": "value"}'
```

### GET `/v1/preferences/publishing`

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | query | `integer` | No |  |

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.Models.Response.PublishingPreferences.PublishingPreferencesResponse`
- `401`: 0: Authorization has been denied for this request.

**Response fields** (`Roblox.ItemConfiguration.Api.Models.Response.PublishingPreferences.PublishingPreferencesResponse`)

See [Roblox.ItemConfiguration.Api.Models.Response.PublishingPreferences.PublishingPreferencesResponse](#roblox-itemconfiguration-api-models-response-publishingpreferences-publishingpreferencesresponse) in Models.

**Response example:**
```json
{
  "id": "string",
  "creatorUserId": 0,
  "creatorGroupId": 0,
  "publishingType": 0,
  "saleLocationType": 0,
  "places": [
    0
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://itemconfiguration.roblox.com/v1/preferences/publishing"
```

### POST `/v1/preferences/publishing`

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Request Body:** `application/json` — Type: `Roblox.ItemConfiguration.Api.Models.Request.PublishingPreferences.CreatePublishingPreferencesRequest`

See [Roblox.ItemConfiguration.Api.Models.Request.PublishingPreferences.CreatePublishingPreferencesRequest](#roblox-itemconfiguration-api-models-request-publishingpreferences-createpublishingpreferencesrequest) in Models.

**Request example:**
```json
{
  "creatorUserId": 0,
  "creatorGroupId": 0,
  "publishingType": 0,
  "saleLocationType": 0,
  "places": [
    0
  ],
  "priceInRobux": 0
}
```

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.Models.Response.PublishingPreferences.PublishingPreferencesResponse`
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed

**Response fields** (`Roblox.ItemConfiguration.Api.Models.Response.PublishingPreferences.PublishingPreferencesResponse`)

See [Roblox.ItemConfiguration.Api.Models.Response.PublishingPreferences.PublishingPreferencesResponse](#roblox-itemconfiguration-api-models-response-publishingpreferences-publishingpreferencesresponse) in Models.

**Response example:**
```json
{
  "id": "string",
  "creatorUserId": 0,
  "creatorGroupId": 0,
  "publishingType": 0,
  "saleLocationType": 0,
  "places": [
    0
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://itemconfiguration.roblox.com/v1/preferences/publishing" \
  -H "Content-Type: application/json" \
  -d '{
  "creatorUserId": 0,
  "creatorGroupId": 0,
  "publishingType": 0,
  "saleLocationType": 0,
  "places": [
    0
  ],
  "priceInRobux": 0
}'
```

### PATCH `/v1/preferences/publishing`

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Request Body:** `application/json` — Type: `Roblox.ItemConfiguration.Api.Models.Request.PublishingPreferences.UpdatePublishingPreferencesRequest`

See [Roblox.ItemConfiguration.Api.Models.Request.PublishingPreferences.UpdatePublishingPreferencesRequest](#roblox-itemconfiguration-api-models-request-publishingpreferences-updatepublishingpreferencesrequest) in Models.

**Request example:**
```json
{
  "creatorUserId": 0,
  "creatorGroupId": 0,
  "publishingType": 0,
  "saleLocationType": 0,
  "places": [
    0
  ],
  "priceInRobux": 0
}
```

**Responses:**

- `200`: OK → `Roblox.ItemConfiguration.Api.Models.Response.PublishingPreferences.PublishingPreferencesResponse`
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed

**Response fields** (`Roblox.ItemConfiguration.Api.Models.Response.PublishingPreferences.PublishingPreferencesResponse`)

See [Roblox.ItemConfiguration.Api.Models.Response.PublishingPreferences.PublishingPreferencesResponse](#roblox-itemconfiguration-api-models-response-publishingpreferences-publishingpreferencesresponse) in Models.

**Response example:**
```json
{
  "id": "string",
  "creatorUserId": 0,
  "creatorGroupId": 0,
  "publishingType": 0,
  "saleLocationType": 0,
  "places": [
    0
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X PATCH -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://itemconfiguration.roblox.com/v1/preferences/publishing" \
  -H "Content-Type: application/json" \
  -d '{
  "creatorUserId": 0,
  "creatorGroupId": 0,
  "publishingType": 0,
  "saleLocationType": 0,
  "places": [
    0
  ],
  "priceInRobux": 0
}'
```

### DELETE `/v1/preferences/publishing`

**Server:** `https://itemconfiguration.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | query | `integer` | No |  |

**Responses:**

- `200`: OK
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X DELETE -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://itemconfiguration.roblox.com/v1/preferences/publishing"
```

### GET `/v1/products/{productId}` [EXPERIMENTAL]

Retrieves the product purchasable details given its id.

**Server:** `https://economy.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `productId` | path | `integer` | Yes | The id of the product. |
| `showPurchasableOpt` | query | `boolean` | Yes |  |

**Responses:**

- `200`: OK → `Roblox.Economy.Api.Models.PurchasableDetailResponse`
- `400`: 1: The user is invalid. 33: The product id is invalid.
- `401`: 0: Authorization has been denied for this request.

**Response fields** (`Roblox.Economy.Api.Models.PurchasableDetailResponse`)

See [Roblox.Economy.Api.Models.PurchasableDetailResponse](#roblox-economy-api-models-purchasabledetailresponse) in Models.

**Response example:**
```json
{
  "purchasable": false,
  "reason": 0,
  "productId": 0,
  "statusCode": 0,
  "title": "string",
  "errorMsg": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://economy.roblox.com/v1/products/{PRODUCTID}?showPurchasableOpt={VALUE}"
```

### GET `/v1/subcategories` *(deprecated)*

Lists Subcategory Names and their Ids.

This endpoint will be deprecated soon. No new features will be added.

**Server:** `https://catalog.roblox.com`

**Auth:** 

**Responses:**

- `200`: OK → `object`

**Example:**
```bash
curl -H "Authorization: Bearer $ROBLOX_ACCESS_TOKEN" \
  "https://catalog.roblox.com/v1/subcategories"
```

### POST `/v1/topic/get-topics` [EXPERIMENTAL]

Gets topics for a populated request, or trending queries when the request has no topic inputs.
Topics and queries are mutually exclusive in the response.

**Server:** `https://catalog.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Request Body:** `application/json` — Type: `Roblox.Catalog.Api.TopicRequestModel`

See [Roblox.Catalog.Api.TopicRequestModel](#roblox-catalog-api-topicrequestmodel) in Models.

**Request example:**
```json
{
  "items": [
    {
      "TargetId": "...",
      "ItemType": "..."
    }
  ],
  "selectTopics": [
    "string"
  ],
  "inputQuery": "string",
  "maxResult": 0,
  "genderType": 1
}
```

**Responses:**

- `200`: OK → `Roblox.Catalog.Api.TopicResponse`
- `403`: 0: Token Validation Failed

**Response fields** (`Roblox.Catalog.Api.TopicResponse`)

See [Roblox.Catalog.Api.TopicResponse](#roblox-catalog-api-topicresponse) in Models.

**Response example:**
```json
{
  "topics": [
    {
      "displayName": "...",
      "originalTopicName": "..."
    }
  ],
  "queries": [
    "string"
  ],
  "error": {
    "Message": "string",
    "Code": 0
  }
}
```

**Error handling:** `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://catalog.roblox.com/v1/topic/get-topics" \
  -H "Content-Type: application/json" \
  -d '{
  "items": [
    {
      "TargetId": "...",
      "ItemType": "..."
    }
  ],
  "selectTopics": [
    "string"
  ],
  "inputQuery": "string",
  "maxResult": 0,
  "genderType": 1
}'
```

### GET `/v1/user/groups/canmanagegamesoritems` [EXPERIMENTAL]

Gets a list of groups a user can manage games or items for.

**Server:** `https://develop.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Api.Develop.Models.GroupModel_`
- `401`: 0: Authorization has been denied for this request.

**Response fields** (`Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Api.Develop.Models.GroupModel_`)

See [Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Api.Develop.Models.GroupModel_](#roblox-web-webapi-models-apiarrayresponse-roblox-api-develop-models-groupmodel-) in Models.

**Response example:**
```json
{
  "data": [
    {
      "id": "...",
      "name": "..."
    }
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://develop.roblox.com/v1/user/groups/canmanagegamesoritems"
```

### GET `/v1/users/{userId}/bundles` [EXPERIMENTAL]

Lists the bundles owned by a given user.

**Server:** `https://catalog.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `userId` | path | `integer` | Yes |  |
| `cursor` | query | `string` | No |  |
| `limit` | query | `integer` | No |  |
| `sortOrder` | query | `1 \| 2` | No | Valid values: `1`, `2` |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Catalog.Api.OwnedBundleModel_`
- `400`: 1: Invalid bundle

**Response fields** (`Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Catalog.Api.OwnedBundleModel_`)

See [Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Catalog.Api.OwnedBundleModel_](#roblox-web-webapi-models-apipageresponse-roblox-catalog-api-ownedbundlemodel-) in Models.

**Response example:**
```json
{
  "previousPageCursor": "string",
  "nextPageCursor": "string",
  "data": [
    {
      "id": "...",
      "name": "...",
      "bundleType": "...",
      "creator": "..."
    }
  ]
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://catalog.roblox.com/v1/users/{USERID}/bundles"
```

### GET `/v1/users/{userId}/bundles/{bundleType}` [EXPERIMENTAL]

**Server:** `https://catalog.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `userId` | path | `integer` | Yes |  |
| `bundleType` | path | `1 \| 2 \| 3 \| 4` | Yes | ['BodyParts' = 1, 'AvatarAnimations' = 2, 'Shoes' = 3, 'DynamicHead' = 4] Valid values: `1`, `2`, `3`, `4` |
| `cursor` | query | `string` | Yes |  |
| `limit` | query | `integer` | No |  |
| `sortOrder` | query | `1 \| 2` | No | ['Asc' = 1, 'Desc' = 2] Valid values: `1`, `2` |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Catalog.Api.OwnedBundleModel_`

**Response fields** (`Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Catalog.Api.OwnedBundleModel_`)

See [Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Catalog.Api.OwnedBundleModel_](#roblox-web-webapi-models-apipageresponse-roblox-catalog-api-ownedbundlemodel-) in Models.

**Response example:**
```json
{
  "previousPageCursor": "string",
  "nextPageCursor": "string",
  "data": [
    {
      "id": "...",
      "name": "...",
      "bundleType": "...",
      "creator": "..."
    }
  ]
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://catalog.roblox.com/v1/users/{USERID}/bundles/{BUNDLETYPE}?cursor={VALUE}"
```

### GET `/v1/users/{userId}/currently-wearing`

Gets a list of asset ids that the user is currently wearing.

**Server:** `https://avatar.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `userId` | path | `integer` | Yes | The user id. |
| `Roblox-Place-Id` | header | `integer` | No |  |

**Responses:**

- `200`: OK → `Roblox.Api.Avatar.Models.AssetIdListModel`
- `400`: 1: The specified user does not exist. 2: An account for the given userId does not exist!

**Response fields** (`Roblox.Api.Avatar.Models.AssetIdListModel`)

See [Roblox.Api.Avatar.Models.AssetIdListModel](#roblox-api-avatar-models-assetidlistmodel) in Models.

**Response example:**
```json
{
  "assetIds": [
    0
  ]
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://avatar.roblox.com/v1/users/{USERID}/currently-wearing"
```

### GET `/v1/users/{userId}/items/{itemType}/{itemTargetId}`

Gets owned items of the specified item type. Game Servers can make requests for any user, but can only make requests for game passes that belong to the place sending the request.
Place creators can make requests as if they were the Game Server.

**Server:** `https://inventory.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `userId` | path | `integer` | Yes | ID of the user in question |
| `itemType` | path | `0 \| 1 \| 2 \| 3 \| 4` | Yes | Type of the item in question (i.e. Asset, GamePass, Badge, Bundle) Valid values: `0`, `1`, `2`, `3`, `4` |
| `itemTargetId` | path | `integer` | Yes | ID of the item in question |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Inventory.Api.Models.IItemModel_`
- `400`: 1: The specified user does not exist! 5: The specified game pass does not exist! Are you using the new game pass ID? 6: The specified item type does not exist. 7: The specified Asset does not exist! 10: The specified asset is not a badge! 12: The specified bundle does not exist!

**Response fields** (`Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Inventory.Api.Models.IItemModel_`)

See [Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Inventory.Api.Models.IItemModel_](#roblox-web-webapi-models-apipageresponse-roblox-inventory-api-models-iitemmodel-) in Models.

**Response example:**
```json
{
  "previousPageCursor": "string",
  "nextPageCursor": "string",
  "data": [
    {
      "id": "...",
      "name": "...",
      "type": "...",
      "instanceId": "..."
    }
  ]
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://inventory.roblox.com/v1/users/{USERID}/items/{ITEMTYPE}/{ITEMTARGETID}"
```

### GET `/v2/alias/{universeId}/{assetName}` [EXPERIMENTAL]

**Server:** `https://assetdelivery.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `string` | Yes |  |
| `assetName` | path | `string` | Yes |  |
| `Accept-Encoding` | header | `string` | Yes |  |
| `Roblox-Place-Id` | header | `integer` | Yes |  |
| `AssetType` | header | `string` | Yes |  |
| `AssetFormat` | header | `string` | Yes |  |
| `Roblox-AssetFormat` | header | `string` | Yes |  |
| `Roblox-Usage-Context` | header | `string` | No |  |
| `skipSigningScripts` | query | `boolean` | No |  |
| `clientInsert` | query | `integer` | No |  |
| `scriptinsert` | query | `integer` | No |  |
| `modulePlaceId` | query | `integer` | No |  |
| `serverplaceid` | query | `integer` | No |  |
| `expectedAssetType` | query | `string` | No |  |
| `accessContext` | query | `string` | No |  |

**Responses:**

- `200`: OK

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://assetdelivery.roblox.com/v2/alias/{UNIVERSEID}/{ASSETNAME}"
```

### GET `/v2/asset` [EXPERIMENTAL]

**Server:** `https://assetdelivery.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `Accept-Encoding` | header | `string` | Yes |  |
| `Roblox-Place-Id` | header | `integer` | Yes |  |
| `AssetType` | header | `string` | Yes |  |
| `AssetFormat` | header | `string` | Yes |  |
| `Roblox-AssetFormat` | header | `string` | Yes |  |
| `Roblox-Usage-Context` | header | `string` | No |  |
| `id` | query | `integer` | No |  |
| `userAssetId` | query | `integer` | No |  |
| `assetVersionId` | query | `integer` | No |  |
| `version` | query | `integer` | No |  |
| `universeId` | query | `integer` | No |  |
| `clientInsert` | query | `integer` | No |  |
| `scriptinsert` | query | `integer` | No |  |
| `modulePlaceId` | query | `integer` | No |  |
| `serverplaceid` | query | `string` | No |  |
| `assetName` | query | `string` | No |  |
| `hash` | query | `string` | No |  |
| `marAssetHash` | query | `string` | No |  |
| `marCheckSum` | query | `string` | No |  |
| `expectedAssetType` | query | `string` | No |  |
| `skipSigningScripts` | query | `boolean` | No |  |
| `permissionContext` | query | `string` | No |  |
| `doNotFallbackToBaselineRepresentation` | query | `boolean` | No |  |
| `contentRepresentationPriorityList` | query | `string` | No |  |
| `accessContext` | query | `string` | No |  |

**Responses:**

- `200`: OK

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://assetdelivery.roblox.com/v2/asset"
```

### GET `/v2/assetId/{assetId}` [EXPERIMENTAL]

**Server:** `https://assetdelivery.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetId` | path | `integer` | Yes |  |
| `Accept-Encoding` | header | `string` | Yes |  |
| `Roblox-Place-Id` | header | `integer` | Yes |  |
| `AssetType` | header | `string` | Yes |  |
| `AssetFormat` | header | `string` | Yes |  |
| `Roblox-AssetFormat` | header | `string` | Yes |  |
| `Roblox-Usage-Context` | header | `string` | No |  |
| `skipSigningScripts` | query | `boolean` | No |  |
| `clientInsert` | query | `integer` | No |  |
| `scriptinsert` | query | `integer` | No |  |
| `modulePlaceId` | query | `integer` | No |  |
| `serverplaceid` | query | `integer` | No |  |
| `expectedAssetType` | query | `string` | No |  |
| `doNotFallbackToBaselineRepresentation` | query | `boolean` | No |  |
| `contentRepresentationPriorityList` | query | `string` | No |  |
| `accessContext` | query | `string` | No |  |

**Responses:**

- `200`: OK

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://assetdelivery.roblox.com/v2/assetId/{ASSETID}"
```

### GET `/v2/assetId/{assetId}/version/{versionNumber}` [EXPERIMENTAL]

**Server:** `https://assetdelivery.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetId` | path | `integer` | Yes |  |
| `versionNumber` | path | `integer` | Yes |  |
| `Accept-Encoding` | header | `string` | Yes |  |
| `Roblox-Place-Id` | header | `integer` | Yes |  |
| `AssetType` | header | `string` | Yes |  |
| `AssetFormat` | header | `string` | Yes |  |
| `Roblox-AssetFormat` | header | `string` | Yes |  |
| `Roblox-Usage-Context` | header | `string` | No |  |
| `skipSigningScripts` | query | `boolean` | No |  |
| `clientInsert` | query | `integer` | No |  |
| `scriptinsert` | query | `integer` | No |  |
| `modulePlaceId` | query | `integer` | No |  |
| `serverplaceid` | query | `integer` | No |  |
| `expectedAssetType` | query | `string` | No |  |
| `doNotFallbackToBaselineRepresentation` | query | `boolean` | No |  |
| `contentRepresentationPriorityList` | query | `string` | No |  |
| `accessContext` | query | `string` | No |  |

**Responses:**

- `200`: OK

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://assetdelivery.roblox.com/v2/assetId/{ASSETID}/version/{VERSIONNUMBER}"
```

### POST `/v2/assets/batch` [EXPERIMENTAL]

**Server:** `https://assetdelivery.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `Roblox-Place-Id` | header | `integer` | Yes |  |
| `Roblox-Browser-Asset-Request` | header | `string` | Yes |  |

**Request Body:** `application/json` — Type: `Roblox.Web.Assets.BatchAssetRequestItem[]`

See [Roblox.Web.Assets.BatchAssetRequestItem](#roblox-web-assets-batchassetrequestitem) in Models.

**Responses:**

- `200`: OK

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://assetdelivery.roblox.com/v2/assets/batch" \
  -H "Content-Type: application/json" \
  -d '[
  {
    "assetName": "string",
    "assetType": "string",
    "clientInsert": false,
    "placeId": 0,
    "requestId": "string",
    "scriptInsert": false
  }
]'
```

### GET `/v2/assets/{assetId}/bundles`

Lists bundles that contain the given asset (hydrated search-detail shape for marketplace).

**Server:** `https://catalog.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetId` | path | `integer` | Yes | Asset id. |
| `Roblox-Place-Id` | header | `integer` | Yes | Roblox-Place-Id header. |
| `Roblox-Game-Id` | header | `string` | Yes | Roblox-Game-Id header. |
| `limit` | query | `10 \| 25 \| 50 \| 100` | No | The number of results per request. Valid values: `10`, `25`, `50`, `100` |
| `cursor` | query | `string` | No | The paging cursor for the previous or next page. |
| `sortOrder` | query | `Asc \| Desc` | No | The order the results are sorted in. Valid values: `Asc`, `Desc` |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Catalog.Api.CatalogSearchDetailedResponseItem_`
- `400`: 1: Invalid assetId 4: Invalid Cursor.
- `403`: 7: User is unauthorized.

**Response fields** (`Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Catalog.Api.CatalogSearchDetailedResponseItem_`)

See [Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Catalog.Api.CatalogSearchDetailedResponseItem_](#roblox-web-webapi-models-apipageresponse-roblox-catalog-api-catalogsearchdetailedresponseitem-) in Models.

**Response example:**
```json
{
  "previousPageCursor": "string",
  "nextPageCursor": "string",
  "data": [
    {
      "id": "...",
      "itemType": "...",
      "assetType": "...",
      "bundleType": "...",
      "isRecolorable": "...",
      "name": "..."
    }
  ]
}
```

**Error handling:** `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://catalog.roblox.com/v2/assets/{ASSETID}/bundles"
```

### GET `/v2/assets/{assetId}/owners`

Gets a list of owners of an asset.

**Server:** `https://inventory.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetId` | path | `integer` | Yes | The asset id. |
| `limit` | query | `10 \| 25 \| 50 \| 100` | No | The number of results per request. Valid values: `10`, `25`, `50`, `100` |
| `cursor` | query | `string` | No | The paging cursor for the previous or next page. |
| `sortOrder` | query | `Asc \| Desc` | No | Sorted by userAssetId Valid values: `Asc`, `Desc` |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Inventory.Api.V2.AssetOwnerResponse_`
- `400`: 1: The asset id is invalid.
- `403`: 2: You do not have permission to view the owners of this asset.

**Response fields** (`Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Inventory.Api.V2.AssetOwnerResponse_`)

See [Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Inventory.Api.V2.AssetOwnerResponse_](#roblox-web-webapi-models-apipageresponse-roblox-inventory-api-v2-assetownerresponse-) in Models.

**Response example:**
```json
{
  "previousPageCursor": "string",
  "nextPageCursor": "string",
  "data": [
    {
      "id": "...",
      "collectibleItemInstanceId": "...",
      "serialNumber": "...",
      "owner": "...",
      "created": "...",
      "updated": "..."
    }
  ]
}
```

**Error handling:** `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://inventory.roblox.com/v2/assets/{ASSETID}/owners"
```

### GET `/v2/assets/{id}/versions` *(deprecated)*

Retrieves asset information for the specified asset ID. The authenticated user must be able to manage the asset
or granted by package permission.

Use OpenCloud Assets API instead.

**Server:** `https://develop.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `id` | path | `integer` | Yes | The ID of the asset.Roblox.Platform.Assets.IAsset |
| `Roblox-Place-Id` | header | `integer` | Yes | The ID of the place.Roblox.Platform.Assets.IPlace |
| `limit` | query | `10 \| 25 \| 50 \| 100` | No | The number of results per request. Valid values: `10`, `25`, `50`, `100` |
| `cursor` | query | `string` | No | The paging cursor for the previous or next page. |
| `sortOrder` | query | `Asc \| Desc` | No | Sort by version number, default is desc. Valid values: `Asc`, `Desc` |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Api.Develop.AssetVersion_`

**Response fields** (`Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Api.Develop.AssetVersion_`)

See [Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Api.Develop.AssetVersion_](#roblox-web-webapi-models-apipageresponse-roblox-api-develop-assetversion-) in Models.

**Response example:**
```json
{
  "previousPageCursor": "string",
  "nextPageCursor": "string",
  "data": [
    {
      "Id": "...",
      "assetId": "...",
      "assetVersionNumber": "...",
      "creatorType": "...",
      "creatorTargetId": "...",
      "creatingUniverseId": "..."
    }
  ]
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://develop.roblox.com/v2/assets/{ID}/versions"
```

### GET `/v2/collectible-items/{collectibleItemId}/owners`

Gets a list of owners of a collectible item.

**Server:** `https://inventory.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `collectibleItemId` | path | `string` | Yes | The collectible item ID. |
| `limit` | query | `integer` | No | The number of results per request. |
| `cursor` | query | `string` | No | The paging cursor for the previous or next page. |
| `sortOrder` | query | `1 \| 2` | No | The order the results are sorted in. Valid values: `1`, `2` |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Inventory.Api.V2.CollectibleItemOwnerResponse_`
- `400`: 1: The collectible item id is invalid.
- `401`: 0: Authorization has been denied for this request.
- `403`: 2: You do not have permission to view the owners of this item.

**Response fields** (`Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Inventory.Api.V2.CollectibleItemOwnerResponse_`)

See [Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Inventory.Api.V2.CollectibleItemOwnerResponse_](#roblox-web-webapi-models-apipageresponse-roblox-inventory-api-v2-collectibleitemownerresponse-) in Models.

**Response example:**
```json
{
  "previousPageCursor": "string",
  "nextPageCursor": "string",
  "data": [
    {
      "collectibleItemInstanceId": "...",
      "serialNumber": "...",
      "owner": "..."
    }
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://inventory.roblox.com/v2/collectible-items/{COLLECTIBLEITEMID}/owners"
```

### DELETE `/v2/inventory/asset/{assetId}`

Give up an asset owned by the authenticated user.
Assets that are created by Roblox user or are limited edition are not eligible for deletion
and will return NotEligibleForDelete.

**Server:** `https://inventory.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `assetId` | path | `integer` | Yes | ID of the asset to delete. |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.ApiEmptyResponseModel`
- `401`: 0: Authorization has been denied for this request. 4: You are not authorized.
- `403`: 0: Token Validation Failed 2: You don't own the specified item. 3: The item is not allowed to be deleted.
- `404`: 1: The item does not exist.
- `500`: 0: An unknown error occured.

**Response fields** (`Roblox.Web.WebAPI.ApiEmptyResponseModel`)

See [Roblox.Web.WebAPI.ApiEmptyResponseModel](#roblox-web-webapi-apiemptyresponsemodel) in Models.

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X DELETE -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://inventory.roblox.com/v2/inventory/asset/{ASSETID}"
```

### GET `/v2/marAssetHash/{marAssetHash}/marCheckSum/{marCheckSum}`

**Server:** `https://assetdelivery.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `marAssetHash` | path | `string` | Yes |  |
| `marCheckSum` | path | `string` | Yes |  |
| `Accept-Encoding` | header | `string` | Yes |  |
| `Roblox-Place-Id` | header | `integer` | Yes |  |
| `AssetType` | header | `string` | Yes |  |
| `AssetFormat` | header | `string` | Yes |  |
| `Roblox-AssetFormat` | header | `string` | Yes |  |
| `skipSigningScripts` | query | `boolean` | No |  |
| `clientInsert` | query | `integer` | No |  |
| `scriptinsert` | query | `integer` | No |  |
| `modulePlaceId` | query | `integer` | No |  |
| `serverplaceid` | query | `integer` | No |  |
| `expectedAssetType` | query | `string` | No |  |

**Responses:**

- `200`: OK

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://assetdelivery.roblox.com/v2/marAssetHash/{MARASSETHASH}/marCheckSum/{MARCHECKSUM}"
```

### GET `/v2/search/items/details` [EXPERIMENTAL]

Search for catalog items.

This endpoint is for search by item type ids.

**Server:** `https://catalog.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `RequiredPropertyFilters` | query | `0 \| 1 \| 2 \| 3[]` | No | Stackable boolean filters, e.g. if { Emissive, AdvancedMaterials }, returned items isEmissive AND isAdvancedMaterials. Unsupported enums throw 400s, duplicates get quietly filtered out. Valid values: `0`, `1`, `2`, `3` |
| `Taxonomy` | query | `string` | No |  |
| `AssetTypeIds` | query | `integer[]` | No |  |
| `BundleTypeIds` | query | `integer[]` | No |  |
| `CategoryFilter` | query | `integer enum (8 values)` | No | The category filter types, representing generic collections of catalog items requested by client. ['None' = 0, 'Featured' = 1, 'Collectibles' = 2, 'CommunityCreations' = 3, 'Landing' = 4, 'Premium' = 5, 'Recommended' = 6, 'HighDefinition' = 7] Valid values: `0`, `1`, `2`, `3`, `4`, `5`, `6`, `7` |
| `SortAggregation` | query | `integer enum (6 values)` | No | ['Past12Hours' = 0, 'PastDay' = 1, 'Past3Days' = 2, 'PastWeek' = 3, 'PastMonth' = 4, 'AllTime' = 5] Valid values: `0`, `1`, `2`, `3`, `4`, `5` |
| `SortType` | query | `integer enum (6 values)` | No | Price values to be consolidated after roll out to api site. ['Relevance' = 0, 'Favorited' = 1, 'Sales' = 2, 'Created' = 3, 'Updated' = 3, 'PriceAsc' = 4, 'PriceDesc' = 5] Valid values: `0`, `1`, `2`, `3`, `4`, `5` |
| `CreatorType` | query | `0 \| 1 \| 2` | No | ['All' = 0, 'User' = 1, 'Group' = 2] Valid values: `0`, `1`, `2` |
| `CreatorTargetId` | query | `integer` | No |  |
| `CreatorName` | query | `string` | No |  |
| `MaxPrice` | query | `integer` | No |  |
| `MinPrice` | query | `integer` | No |  |
| `Keyword` | query | `string` | No |  |
| `IncludeNotForSale` | query | `boolean` | No |  |
| `TriggeredByTopicDiscovery` | query | `boolean` | No |  |
| `SalesTypeFilter` | query | `0 \| 1 \| 2 \| 3 \| 4` | No | The Sales Type filter options for search. ['Unknown' = 0, 'All' = 1, 'Collectibles' = 2, 'Premium' = 3, 'TimedOptions' = 4] Valid values: `0`, `1`, `2`, `3`, `4` |
| `Topics` | query | `string` | No | The input topics format is split by ",". E.g "topics=cat,hat,red". |
| `limit` | query | `10 \| 28 \| 30 \| 60 \| 120` | No | The number of results per request. Valid values: `10`, `28`, `30`, `60`, `120` |
| `cursor` | query | `string` | No | The paging cursor for the previous or next page. |
| `sortOrder` | query | `Desc` | No | The order the results are sorted in. Valid values: `Desc` |

**Responses:**

- `200`: OK → `Roblox.Catalog.Api.CatalogSearchPageResponse_Roblox.Catalog.Api.CatalogSearchDetailedResponseItemV2_`
- `400`: 1: Category subcategory selection not supported. 2: Creator id not found. 3: Creator type not found or cannot search by CreatorTargetId with CreatorType.All 4: Genre not found. 5: Sort combination not supported. 6: Invalid price range. 10: StartRequest is invalid.
- `403`: 7: User is unauthorized. 22: In-experience search is denied for this place or universe.
- `429`: 8: The flood limit has been exceeded. 8: The flood limit has been exceeded.
- `503`: 18: Search request timed out

**Response fields** (`Roblox.Catalog.Api.CatalogSearchPageResponse_Roblox.Catalog.Api.CatalogSearchDetailedResponseItemV2_`)

See [Roblox.Catalog.Api.CatalogSearchPageResponse_Roblox.Catalog.Api.CatalogSearchDetailedResponseItemV2_](#roblox-catalog-api-catalogsearchpageresponse-roblox-catalog-api-catalogsearchdetailedresponseitemv2-) in Models.

**Response example:**
```json
{
  "keyword": "string",
  "elasticsearchDebugInfo": {
    "elasticsearchQuery": "string",
    "isFromCache": false,
    "indexName": "string",
    "isTerminatedEarly": false,
    "isForceTerminationEnabledByRequest": false,
    "searchResultDataSource": "string"
  },
  "previousPageCursor": "string",
  "nextPageCursor": "string",
  "data": [
    {
      "bundledItems": "...",
      "taxonomy": "...",
      "itemCreatedUtc": "...",
      "discountInformation": "...",
      "license": "...",
      "id": "..."
    }
  ]
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://catalog.roblox.com/v2/search/items/details"
```

### GET `/v2/users/{userId}/inventory`

Get user's inventory by multiple Roblox.Platform.Assets.AssetType.

GamePass and Badges not allowed.

**Server:** `https://inventory.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `userId` | path | `integer` | Yes | The inventory owner's userId. |
| `assetTypes` | query | `string enum (90 values)[]` | Yes | The asset types to query. Valid values: `1`, `2`, `3`, `4`, `5`, `6`, `7`, `8`, `9`, `10`, `11`, `12`, `13`, `16`, `17`, `18`, `19`, `21`, `22`, `24`, `25`, `26`, `27`, `28`, `29`, `30`, `31`, `32`, `33`, `34`, `35`, `37`, `38`, `39`, `40`, `41`, `42`, `43`, `44`, `45`, `46`, `47`, `48`, `49`, `50`, `51`, `52`, `53`, `54`, `55`, `56`, `59`, `60`, `61`, `62`, `63`, `64`, `65`, `66`, `67`, `68`, `69`, `70`, `71`, `72`, `73`, `74`, `75`, `76`, `77`, `78`, `79`, `80`, `81`, `82`, `83`, `84`, `85`, `86`, `87`, `88`, `89`, `90`, `91`, `92`, `93`, `94`, `95`, `96`, `97` |
| `filterDisapprovedAssets` | query | `boolean` | No | Filters moderated assets when enabled. |
| `showApprovedOnly` | query | `boolean` | No | Filters moderated assets and assets pending review when enabled. |
| `limit` | query | `10 \| 25 \| 50 \| 100` | No | The number of results per request. Valid values: `10`, `25`, `50`, `100` |
| `cursor` | query | `string` | No | The paging cursor for the previous or next page. |
| `sortOrder` | query | `Asc \| Desc` | No | The order the results are sorted in. Valid values: `Asc`, `Desc` |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Inventory.Api.V2.UserAssetItemModelV2_`
- `400`: 1: Invalid user Id. 2: Invalid asset type Id.
- `403`: 3: Insufficient permission. 4: You are not authorized to view this user's inventory.

**Response fields** (`Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Inventory.Api.V2.UserAssetItemModelV2_`)

See [Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Inventory.Api.V2.UserAssetItemModelV2_](#roblox-web-webapi-models-apipageresponse-roblox-inventory-api-v2-userassetitemmodelv2-) in Models.

**Response example:**
```json
{
  "previousPageCursor": "string",
  "nextPageCursor": "string",
  "data": [
    {
      "assetId": "...",
      "name": "...",
      "assetType": "...",
      "created": "..."
    }
  ]
}
```

**Error handling:** `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://inventory.roblox.com/v2/users/{USERID}/inventory?assetTypes={VALUE}"
```

### POST `/v3/assets/batch` [EXPERIMENTAL]

**Server:** `https://assetdelivery.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `Roblox-Place-Id` | header | `integer` | Yes |  |
| `Accept-Encoding` | header | `string` | Yes |  |

**Request Body:** `application/json` — Type: `Roblox2.Assetdelivery.V3.V3BatchRequest`

See [Roblox2.Assetdelivery.V3.V3BatchRequest](#roblox2-assetdelivery-v3-v3batchrequest) in Models.

**Request example:**
```json
{
  "assets": [
    {
      "requestId": "...",
      "asset": "...",
      "version": "...",
      "assetType": "...",
      "representation": "...",
      "skipSigningScripts": "..."
    }
  ]
}
```

**Responses:**

- `200`: OK

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://assetdelivery.roblox.com/v3/assets/batch" \
  -H "Content-Type: application/json" \
  -d '{
  "assets": [
    {
      "requestId": "...",
      "asset": "...",
      "version": "...",
      "assetType": "...",
      "representation": "...",
      "skipSigningScripts": "..."
    }
  ]
}'
```

### POST `/v3/assets/prewarm` [EXPERIMENTAL]

**Server:** `https://assetdelivery.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Request Body:** `application/json` — Type: `Roblox2.Assetdelivery.V3.V3PrewarmRequest`

See [Roblox2.Assetdelivery.V3.V3PrewarmRequest](#roblox2-assetdelivery-v3-v3prewarmrequest) in Models.

**Request example:**
```json
{
  "target": {
    "place": {
      "placeId": "..."
    }
  }
}
```

**Responses:**

- `200`: OK

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://assetdelivery.roblox.com/v3/assets/prewarm" \
  -H "Content-Type: application/json" \
  -d '{
  "target": {
    "place": {
      "placeId": "..."
    }
  }
}'
```

## Models

### BatchGrantPermissionsRequest

Request object to grant one permission to multiple assets.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `subjectType` | `SubjectType` | No |  |
| `subjectId` | `string` | No | The subject ID to grant to. Must be empty for SubjectType 'All'. |
| `action` | `AssetAction` | No |  |
| `requests` | `AssetGrantRequest[]` | No | Array of asset grant requests. If populated, 'requests' will override 'assetIds'. |
| `assetIds` | `integer[]` | No | [Deprecated] The list of asset IDs to grant this permission to. 'requests' will be prioritized over this list. |
| `enableDeepAccessCheck` | `boolean` | No | [Do not use] An optional boolean to indicate if a deep access check should be done. This is not intended for public use. |

### BatchGrantPermissionsResponse

Response object to grant one permission to multiple assets.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `successAssetIds` | `integer[]` | No | The list of asset IDs that granted successfully. |
| `errors` | `GrantPermissionError[]` | No | The list of grants that had errors. |

### AssetPermissions.ErrorResponse

The error object for responses.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `error` | `AssetPermissions.Error` | No |  |

### AssetsUploadApi.Asset

Represents an asset.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `path` | `string` | No | The returned resource path of the asset. Format: `assets/{assetId}`. Example: `assets/2205400862`. |
| `revisionId` | `string` | No |  *(immutable)* Revision ID of the asset. Equivalent to `versionNumber`. Every change of the asset automatically commits a new version. The format is an integer string. Example: `1`. |
| `revisionCreateTime` | `string` | No | The creation timestamp of the current revision. |
| `assetId` | `string` | No | The unique identifier of the asset. Required for [Update Asset](#Assets_UpdateAsset). |
| `displayName` | `string` | No | Display name of the asset. Required for [Create Asset](#Assets_CreateAsset). |
| `description` | `string` | No | The description of the asset. Limit to 1000 characters. Required for [Create Asset](#Assets_CreateAsset). |
| `assetType` | `AssetType` | No | The asset type. Required for [Create Asset](#Assets_CreateAsset). |
| `creationContext` | `CreationContext` | No |  |
| `moderationResult` | `ModerationResult` | No |  |
| `published` | `boolean` | No | Whether to publish the asset version created by the request. To check whether the current revision is published, see `isPublished`. |
| `icon` | `string` | No | The resource path for the icon. The icon must be an image set to [Open Use](https://create.roblox.com/docs/projects/assets/privacy). To create an Open Use image, set `creationContext.assetPrivacy` to `OpenUse` in [Create Asset](#Assets_CreateAsset). |
| `previews` | `Preview[]` | No | A list of previews, each with an asset path and alt text. Previews must be **Image** assets, except for Place assets, which can have one **GamePreviewVideo**, and for Model, MeshPart, and Plugin assets, which can have one **StorePreviewVideo**. Image previews must be set to [Open Use](https://create.roblox.com/docs/projects/assets/privacy). To create an Open Use image, set `creationContext.assetPrivacy` to `OpenUse` in [Create Asset](#Assets_CreateAsset). |
| `state` | `State` | No |  |
| `facebookSocialLink` | `SocialLink` | No |  |
| `twitterSocialLink` | `SocialLink` | No |  |
| `youtubeSocialLink` | `SocialLink` | No |  |
| `twitchSocialLink` | `SocialLink` | No |  |
| `discordSocialLink` | `SocialLink` | No |  |
| `githubSocialLink` | `SocialLink` | No |  |
| `robloxSocialLink` | `SocialLink` | No |  |
| `guildedSocialLink` | `SocialLink` | No |  |
| `devForumSocialLink` | `SocialLink` | No |  |
| `tryAssetSocialLink` | `SocialLink` | No |  |
| `isPublished` | `boolean` | No | Whether the current revision of the asset is published. |

### AssetsUploadApi.Operation

This resource represents a long-running operation that is the result of a network API call.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `path` | `string` | No | The server-assigned resource path. The default format is `operations/{operation_id}`. |
| `operationId` | `string` | Yes |  |
| `done` | `boolean` | No | If `false`, the operation is still in progress. If `true`, the operation is completed. |
| `error` | `AssetsUploadApi.Status` | No |  |
| `response` | `AssetsUploadApi.Asset` | No |  |

### AssetsUploadApi.Status

The logical error model explaining the error status.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `code` | `string` | No | The error code. |
| `message` | `string` | No | The error message. |
| `details` | `ErrorInfo[]` | No |  |

### ListAssetVersionsResponse

A list of AssetVersions in the parent collection.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `assetVersions` | `AssetVersion[]` | No | The asset versions on this page. May be omitted when empty. |
| `nextPageToken` | `string` | No | Pass this token as `pageToken` to retrieve the next page. If omitted, there are no subsequent pages. |

### AssetVersion

An asset version.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `path` | `string` | No | The returned resource path of the asset version. Format: `assets/{assetId}/versions/{version}`. |
| `createTime` | `string` | No | The timestamp when the asset version was created. |
| `creationContext` | `CreationContext` | No |  |
| `moderationResult` | `ModerationResult` | No |  |
| `published` | `boolean` | No | Indicates whether the asset version is published. If omitted, the version is not published. |

### RollbackAssetVersionRequest

Request to roll back an asset to a previous version.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `assetVersion` | `string` | Yes | The asset version path in the format of `assets/{assetId}/versions/{versionNumber}`. |

### MultipartUploadStartRequest

Request of Roblox.AssetsManagement.AssetsUploadApi.MultipartUploadStartOperation

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `asset` | `AssetsUploadApi.Asset` | No |  |
| `file` | `File` | No |  |
| `additionalParameters` | `object` | No | Optional: Additional parameters to be sent with the request can be included here. |

### MultipartUploadStartResponse

Response of Roblox.AssetsManagement.AssetsUploadApi.MultipartUploadStartOperation

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `operationPath` | `string` | No | ID of the operation. |
| `uploadUrls` | `PreSignedUploadUrl[]` | No | A list of upload urls to upload chunks. |

### MultipartUploadChunkCompleteRequest

Request of Roblox.AssetsManagement.AssetsUploadApi.MultipartUploadChunkCompleteOperation

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `chunkNum` | `integer` | No | The number of this Chunk. |
| `eTag` | `string` | No | ETag of this chunk. |

### GenerateSpeechAssetRequest

Specifies the text from which to generate speech and the voice style.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `text` | `string` | Yes | The text to be translated. |
| `speechStyle` | `GenerateSpeechAssetRequest_GeneratedSpeechStyle` | No | The style of the generated speech. |

### TextToSpeechService.Operation

This resource represents a long-running operation that is the result of a
network API call.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `path` | `string` | No | The server-assigned path, which is only unique within the same service that originally returns it. If you use the default HTTP mapping, the `path` should be a resource path ending with `operations/{unique_id}`. |
| `metadata` | `object` | No | Service-specific metadata associated with the operation.  It typically contains progress information and common metadata such as create time. Some services might not provide such metadata.  Any method that returns a long-running operation should document the metadata type, if any. |
| `done` | `boolean` | No | If the value is `false`, it means the operation is still in progress. If `true`, the operation is completed, and either `error` or `response` is available. |
| `error` | `TextToSpeechService.Status` | No | The error result of the operation in case of failure or cancellation. |
| `response` | `object` | No | The normal response of the operation in case of success.  If the original method returns no data on success, such as `Delete`, the response is `google.protobuf.Empty`.  If the original method is standard `Get`/`Create`/`Update`, the response should be the resource.  For other methods, the response should have the type `XxxResponse`, where `Xxx` is the original method name.  For example, if the original method name is `TakeSnapshot()`, the inferred response type is `TakeSnapshotResponse`. |

### ListAssetQuotasResponse

A list of AssetQuotas in the parent collection.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `assetQuotas` | `AssetQuota[]` | No | The AssetQuotas from the specified User. |
| `nextPageToken` | `string` | No | A token that you can send as a `pageToken` parameter to retrieve the next page. If this field is omitted, there are no subsequent pages. |

### Roblox.LocalizationTables.Api.GetTableResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `string` | No |  |
| `name` | `string` | No |  |
| `ownerType` | `User \| Group` | No | Enum for valid OwnerTypes. |
| `ownerId` | `integer` | No |  |
| `assetId` | `integer` | No |  |

### Roblox.Publish.Api.UploadResponse

A response used when an upload has completed.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `targetId` | `integer` | No | The target Id of the uploaded item. |

### CreatorStoreAsset

Representation of a creator store asset.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `voting` | `VotingModel` | No | The asset's voting details. |
| `creator` | `CreatorModelV2` | No | The asset creator's details. |
| `creatorStoreProduct` | `CreatorStoreProduct` | No | The asset's product details. |
| `asset` | `any` | Yes | The asset information. |

### ProblemDetails

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `type` | `string` | No |  |
| `title` | `string` | No |  |
| `status` | `integer` | No |  |
| `detail` | `string` | No |  |
| `instance` | `string` | No |  |

### HttpValidationProblemDetails

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `errors` | `object` | No |  |

### SearchCategoryType

This represents a "subset" of Toolbox.Service.CategoryType options and represent the full set
of "categories" (or asset types) that can be searched upon from the toolbox search API.

Values: `Audio`, `Place`, `Model`, `Decal`, `Plugin`, `MeshPart`, `Video`, `FontFamily`

### ModelSubType

The supported model subtypes.

Values: `Ad`, `MaterialPack`, `Package`

### SortDirection

Represents the direction in which to sort the results

Values: `None`, `Ascending`, `Descending`

### SortCategory

The category to sort the search results by.

Values: `Relevance`, `Trending`, `Top`, `AudioDuration`, `CreateTime`, `UpdatedTime`, `Ratings`

### SearchAudioTypeModel

Represents audio type values that will be properly displayed in Swagger UI.

Values: `Music`, `SoundEffect`, `Unknown`

### ModelInstanceType

A list of model instance types. See Toolbox.Service.Models.Internal.InstanceCounts and [Instance](https://create.roblox.com/docs/reference/engine/classes/Instance) for more details.

Values: `Script`, `MeshPart`, `Decal`, `Animation`, `Audio`, `Tool`

### SearchView

This view controls which fields are populated in the search response. A lighter
view will result in faster response times and higher reliability.

Values: `IDs`, `Core`, `Full`

### MusicChartType

Represents which music chart to pull entries from, if any

Values: `None`, `Current`, `Week`, `Month`, `Year`

### SearchCreatorStoreAssetsResponse

The response for the SearchCreatorStoreAssets endpoint.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `nextPageToken` | `string` | No | The page token to view the next page of results. |
| `queryFacets` | `QueryFacets` | No | The applied and available facets of a query. |
| `creatorStoreAssets` | `CreatorStoreAsset[]` | Yes | The list of creator store assets returned by the search query. |
| `totalResults` | `integer` | Yes | The total number of results for the given search query. |
| `queryCorrection` | `QueryCorrection` | No | Query correction information, if a correction was available for the search query. |
| `filteredKeyword` | `string` | No | The filtered keyword that was used to search for assets, if applicable. |

### Roblox.Publish.Api.AssetQuotasResponse

Response model for asset quotas.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `quotas` | `Roblox.Publish.Api.AssetQuota[]` | No | A list of quotas. |

### Roblox.ItemConfiguration.Api.AllowedAgentsAssetTypeActionResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `agents` | `Roblox.ItemConfiguration.Api.AgentModel[]` | No | The allowed agents for whom a user can perform specified action. |

### Roblox.Web.Assets.BatchAssetRequestItem

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `assetName` | `string` | No |  |
| `assetType` | `string` | No |  |
| `clientInsert` | `boolean` | No |  |
| `placeId` | `integer` | No |  |
| `requestId` | `string` | No |  |
| `scriptInsert` | `boolean` | No |  |
| `serverPlaceId` | `integer` | No |  |
| `universeId` | `integer` | No |  |
| `accept` | `string` | No |  |
| `encoding` | `string` | No |  |
| `hash` | `string` | No |  |
| `userAssetId` | `integer` | No |  |
| `assetId` | `integer` | No |  |
| `version` | `integer` | No |  |
| `assetVersionId` | `integer` | No |  |
| `modulePlaceId` | `integer` | No |  |
| `assetFormat` | `string` | No |  |
| `roblox-assetFormat` | `string` | No |  |
| `assetResolutionMode` | `string` | No |  |
| `accessContext` | `string` | No |  |
| `usageContext` | `string` | No |  |
| `contentRepresentationPriorityList` | `string` | No |  |
| `doNotFallbackToBaselineRepresentation` | `boolean` | No |  |
| `xcachesplit` | `integer` | No |  |

### Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Api.Develop.Models.Response.AssetVotingModel_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `data` | `Roblox.Api.Develop.Models.Response.AssetVotingModel[]` | No |  |

### Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Catalog.Api.BundleDetailsModel_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `previousPageCursor` | `string` | No |  |
| `nextPageCursor` | `string` | No |  |
| `data` | `Roblox.Catalog.Api.BundleDetailsModel[]` | No |  |

### Roblox.Economy.Api.ResaleDataResponse

Resale data for an item.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `assetStock` | `integer` | No | The total number of this item that can be sold. |
| `sales` | `integer` | No | How many of the item have been sold. |
| `numberRemaining` | `integer` | No | How many of the item remain to be sold. |
| `recentAveragePrice` | `integer` | No | The recent average selling price of the item. |
| `originalPrice` | `integer` | No | The original selling price for the item. |
| `priceDataPoints` | `Roblox.Economy.Api.ChartDataPointResponse[]` | No | Price points for the past 180 days. |
| `volumeDataPoints` | `Roblox.Economy.Api.ChartDataPointResponse[]` | No | Volume points for the past 180 days. |

### Roblox.Publish.Api.UploadAudioRequest

A request model for uploading an audio file.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `name` | `string` | No | Name for the audio file. |
| `file` | `string` | No | File to be uploaded. Formatted as a base64 string. |
| `groupId` | `integer` | No | Id of the group you are publishing the audio asset for. Null if not publishing under a group. |
| `paymentSource` | `string` | No | The source of funds for payment.   User: Use personal funds of authenticated user.   Group: Use group funds from Roblox.Publish.Api.UploadAudioRequest.GroupId.   Null/Empty: Will default to authenticated user funds. |
| `estimatedFileSize` | `integer` | No | Estimated file size of the audio file in bytes. |
| `estimatedDuration` | `number` | No | Estimated duration of the audio file in seconds. |
| `assetPrivacy` | `1 \| 2` | No | The asset privacy of the audio asset. |

### Roblox.Publish.Api.PublishAudioResponse

Response model for publish audio.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `Id` | `integer` | No | Id of the published asset. |
| `Name` | `string` | No | Name of the published asset. |

### Roblox.Publish.Api.VerifyAudioRequest

Request model to publish an audio asset.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `name` | `string` | No | Gets or sets the name of the audio asset. |
| `file` | `string` | No | File to be uploaded. Formatted as a base64 string. |
| `groupId` | `integer` | No | Gets or sets the ID of the group if applicable. Optional. |
| `paymentSource` | `string` | No | Gets or sets the payment source. 'User' or 'Group'. Required if Group ID is set. |
| `fileSize` | `integer` | No | Gets or sets the size of the audio file in bytes. |
| `duration` | `number` | No | Gets or sets the duration of the audio in seconds. |

### Roblox.Publish.Api.VerifyAudioResponse

Response model for verify audio endpoint.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `name` | `string` | No | Name of the audio file. |
| `price` | `integer` | No | Price in robux to publish the audio file. |
| `balance` | `integer` | No | User's current Robux balance. |
| `canAfford` | `boolean` | No | Boolean, true if the user can afford to purchase the publishing of the audio file. |

### Roblox.ItemConfiguration.Api.Models.Request.AvatarItemUpdate.CreateAvatarItemUpdateContextRequest

DTO of the incoming request from the client to create an avatar item update context, which mints
the parent update operation for an existing catalog avatar item.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `originalAssetId` | `integer` | No | The asset id of the existing catalog item being updated. |
| `assetType` | `integer enum (92 values)` | No | The asset type of the item being updated. Must match the original item's asset type: an update swaps content on the same item, it cannot change the item's type. ['Invalid' = 0, 'Image' = 1, 'Tshirt' = 2, 'Audio' = 3, 'Mesh' = 4, 'Lua' = 5, 'Html' = 6, 'Text' = 7, 'Hat' = 8, 'Place' = 9, 'Model' = 10, 'Shirt' = 11, 'Pants' = 12, 'Decal' = 13, 'Avatar' = 16, 'Head' = 17, 'Face' = 18, 'Gear' = 19, 'Badge' = 21, 'GroupEmblem' = 22, 'Animation' = 24, 'Arms' = 25, 'Legs' = 26, 'Torso' = 27, 'RightArm' = 28, 'LeftArm' = 29, 'LeftLeg' = 30, 'RightLeg' = 31, 'Package' = 32, 'YoutubeVideo' = 33, 'GamePass' = 34, 'App' = 35, 'Code' = 37, 'Plugin' = 38, 'SolidModel' = 39, 'MeshPart' = 40, 'HairAccessory' = 41, 'FaceAccessory' = 42, 'NeckAccessory' = 43, 'ShoulderAccessory' = 44, 'FrontAccessory' = 45, 'BackAccessory' = 46, 'WaistAccessory' = 47, 'ClimbAnimation' = 48, 'DeathAnimation' = 49, 'FallAnimation' = 50, 'IdleAnimation' = 51, 'JumpAnimation' = 52, 'RunAnimation' = 53, 'SwimAnimation' = 54, 'WalkAnimation' = 55, 'PoseAnimation' = 56, 'LocalizationTableManifest' = 59, 'LocalizationTableTranslation' = 60, 'EmoteAnimation' = 61, 'Video' = 62, 'TexturePack' = 63, 'TshirtAccessory' = 64, 'ShirtAccessory' = 65, 'PantsAccessory' = 66, 'JacketAccessory' = 67, 'SweaterAccessory' = 68, 'ShortsAccessory' = 69, 'LeftShoeAccessory' = 70, 'RightShoeAccessory' = 71, 'DressSkirtAccessory' = 72, 'FontFamily' = 73, 'FontFace' = 74, 'MeshHiddenSurfaceRemoval' = 75, 'EyebrowAccessory' = 76, 'EyelashAccessory' = 77, 'MoodAnimation' = 78, 'DynamicHead' = 79, 'CodeSnippet' = 80, 'AdsVideo' = 81, 'OtaUpdate' = 82, 'Screenshot' = 83, 'RuntimePropertySet' = 84, 'StorePreviewVideo' = 85, 'GamePreviewVideo' = 86, 'CreatorExperienceConfig' = 87, 'FaceMakeup' = 88, 'LipMakeup' = 89, 'EyeMakeup' = 90, 'VoxelFragment' = 91, 'AvatarBackground' = 92, 'TextDocument' = 93, 'Post' = 94, 'AnimatedImage' = 95, 'ComputeFunction' = 96, 'AvatarSpawnEffect' = 97, 'Voice' = 98] Values: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 16, 17, 18, 19, 21, 22, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98 |

### Roblox.ItemConfiguration.Api.Models.Response.AvatarItemUpdate.CreateAvatarItemUpdateContextResponse

Response DTO for the create avatar item update context endpoint.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `operationId` | `string` | No | The minted parent operation id. Studio threads this as the ParentOperationId of the staging asset upload so the backend can tie the new content back to the original item. |

### Roblox.Badges.Api.IconUploadResponse

Badge icon upload response.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `targetId` | `integer` | No | The asset id of the uploaded icon. |

### Roblox.ItemConfiguration.Api.Models.Request.Bundle.CreateBundleRequest

DTO of incoming request from the client to create a bundle.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `bundleType` | `Unknown \| Body \| DynamicHead \| Shoes \| AvatarAnimations` | No | The bundle type target for the bundle creation. ['Unknown' = 0, 'Body' = 1, 'DynamicHead' = 2, 'Shoes' = 3, 'AvatarAnimations' = 4] |
| `name` | `string` | No | Name of the bundle to be created. |
| `description` | `string` | No | Description of the bundle. |
| `assetIds` | `integer[]` | No | List of asset ids which are to be part of this bundle. These asset ids must include only the allowed asset types for the particular bundle type that is being created. |
| `operationId` | `string` | No | Operation ID of the original intent that was created to start bundle creation. |
| `agreedCreationFee` | `integer` | No | Fee in Robux to create bundle. It needs to be the same as the actual price on the upload fee product entity. Otherwise, the bundle will fail to be created. |

### Roblox.ItemConfiguration.Api.Models.Response.Bundle.CreateBundleResponse

DTO response for the create bundle request.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `creationStatusId` | `string` | No | ID associated with the corresponding create bundle request. This ID is used to query for bundle creation status endpoint. |

### Roblox.ItemConfiguration.Api.Models.Request.Bundle.CreateBundleContextRequest

DTO of incoming request from the client to create bundle context
which is necessary for bundle creation.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `assetQuantities` | `object` | No | The collection of AssetTypes and their corresponding quantities that are being requested to be uploaded by the client. |
| `bundleDescription` | `string` | No | Description for the particular bundle that is about to be created. |
| `bundleName` | `string` | No | Name for the particular bundle that is about to be created. |
| `bundleType` | `Unknown \| Body \| DynamicHead \| Shoes \| AvatarAnimations` | No | The bundle type target of the specified action. ['Unknown' = 0, 'Body' = 1, 'DynamicHead' = 2, 'Shoes' = 3, 'AvatarAnimations' = 4] |
| `bodyScale` | `Roblox.ItemConfiguration.Api.Models.Bundle.BodyScale` | No |  |
| `bodyColorSet` | `Roblox.ItemConfiguration.Api.Models.Bundle.BodyColorSet` | No |  |
| `groupId` | `integer` | No | The group id that the bundle is meant to belong to. |
| `isEmissive` | `boolean` | No | Whether the bundle is expected to contain emissive content. |

### Roblox.ItemConfiguration.Api.Models.Response.Bundle.CreateBundleContextResponse

Response DTO for create bundle context endpoint.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `operationId` | `string` | No | ID that was generated for the given bundle create request. |

### Roblox.Catalog.Api.BundleDetailsModel

The hydration model representing a bundle on marketplace. Returned in all bundles controller endpoints.
Bound in the game-engine MarketplaceService.GetProductInfo method.
https://create.roblox.com/docs/reference/engine/classes/MarketplaceService#GetProductInfo.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No |  |
| `name` | `string` | No |  |
| `description` | `string` | No |  |
| `bundleType` | `string` | No |  |
| `isRecolorable` | `boolean` | No |  |
| `items` | `Roblox.Catalog.Api.BundleItemDetailModel[]` | No |  |
| `creator` | `Roblox.Catalog.Api.BundleCreatorModel` | No |  |
| `product` | `Roblox.Catalog.Api.BundleProductModel` | No |  |
| `itemRestrictions` | `integer enum (9 values)[]` | No |  Values: 1, 2, 3, 4, 5, 6, 7, 8, 9 |
| `collectibleItemDetail` | `Roblox.Catalog.Api.CollectibleItemDetail` | No |  |
| `discountInformation` | `Roblox.Catalog.Api.DiscountInformation` | No |  |

### Roblox.ItemConfiguration.Api.Models.Response.Bundle.BundleMetadataResponse

Metadata response for Bundle.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `isBundlesControllerEnabled` | `boolean` | No | Indicates whether the entire controller is allowed to be accessed. |
| `isBundlesCreationEnabled` | `boolean` | No | Indicates whether bundles creation is allowed. |
| `isBundlesPublishingEnabled` | `boolean` | No | Indicates whether bundles publishing is allowed. |
| `allowedBundleTypeSettings` | `object` | No | A map containing allowed bundle type to all of its settings metadata. |
| `isGroupBundlesUploadEnabled` | `boolean` | No | Whether group bundle upload is enabled. |

### Roblox.ItemConfiguration.Api.Models.Response.Bundle.GetBundleCreationStatusResponse

DTO response containing create bundle status.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `bundleId` | `integer` | No | Bundle ID associated with the creation request if it had a successful status. |
| `status` | `integer enum (8 values)` | No | Current status for the given creationStatusId. ['Unknown' = 0, 'InProgress' = 1, 'Success' = 2, 'ValidationFailed' = 3, 'InsufficientFunds' = 4, 'Failed' = 5, 'CreationFeeMismatch' = 6, 'MetadataMismatch' = 7] Values: 0, 1, 2, 3, 4, 5, 6, 7 |

### Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Catalog.Api.BundleDetailsModel_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `data` | `Roblox.Catalog.Api.BundleDetailsModel[]` | No |  |

### Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Catalog.Api.CatalogSearchDetailedResponseItemV2_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `data` | `Roblox.Catalog.Api.CatalogSearchDetailedResponseItemV2[]` | No |  |

### Roblox.Catalog.Api.BatchItemDetailsCompleteResponse

Response for the batch GetItemDetailsComplete endpoint.
Each entry in Roblox.Catalog.Api.BatchItemDetailsCompleteResponse.Data is either a successfully hydrated item or a critical error.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `data` | `Roblox.Catalog.Api.CatalogItemOrError[]` | No |  |

### Roblox.Catalog.Api.CategoryModel

Response model for category.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `category` | `integer enum (14 values)` | No | Category type. Values: 0, 1, 2, 3, 4, 5, 11, 12, 13, 14, 15, 16, 17, 18 |
| `taxonomy` | `string` | No | The associated public facing web_stable_id corresponding to internal taxonomy uuid for this category. |
| `assetTypeIds` | `integer[]` | No | List of AssetTypeIds corresponding to AssetType enum that this category returns. |
| `bundleTypeIds` | `integer[]` | No | List of bundleTypeIds corresponding to BundleType enum that this category returns. |
| `categoryId` | `integer` | No | Category id. |
| `name` | `string` | No | Category name. |
| `orderIndex` | `integer` | No | Category order index. |
| `subcategories` | `Roblox.Catalog.Api.SubcategoryModel[]` | No | Subcategories under this category. |
| `isSearchable` | `boolean` | No | Gets or sets whether the category is searchable in search bar. |

### Roblox.ItemConfiguration.Api.Models.Request.PublishCollectibleItemRequest

Request model to publish a new CollectibleItem.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `isRentalOptIn` | `boolean` | No | Whether the item is opted into rental. |
| `idempotencyToken` | `string` | No | Idempotency token for publishing purposes. |
| `targetId` | `integer` | No | Target item's Id. |
| `targetType` | `0 \| 1 \| 2 \| 3` | No | Target item's type. ['Asset' = 0, 'Bundle' = 1, 'IecToken' = 2, 'Look' = 3] |
| `publishingType` | `0 \| 1 \| 2` | No | Publishing type of the CollectibleItem. ['Invalid' = 0, 'Limited' = 1, 'NonLimited' = 2] |
| `agreedPublishingFee` | `integer` | No | The publishing fee seen by the end-user. |
| `creatorUserId` | `integer` | No | The UserId of the creator if the creator is a user. |
| `creatorGroupId` | `integer` | No | The GroupId of the creator if the creator is a group. |
| `publisherUserId` | `integer` | No | The UserId of the publisher who pays the publishing fee. This should only be set if the creator is a group. |
| `quantity` | `integer` | No | The total number of instances for the CollectibleItem. |
| `quantityLimitPerUser` | `integer` | No | The max number of instances for the CollectibleItem a user can own. |
| `resaleRestriction` | `0 \| 1 \| 2` | No | The resale restriction of the CollectibleItem. ['INVALID' = 0, 'NONE' = 1, 'DISABLED' = 2] |
| `priceInRobux` | `integer` | No | The sale price of the CollectibleItem and it will be used as minimum price for DPF. |
| `priceOffset` | `integer` | No | Gets or sets the price offset of the item in Robux above the price floor. |
| `optOutFromRegionalPricing` | `boolean` | No | Whether to opt out of the regional pricing. |
| `isFree` | `boolean` | No | Gets or sets if the item is free. |
| `saleLocationConfiguration` | `Roblox.ItemConfiguration.Api.Models.Request.CollectiblesSaleLocationConfigurationModel` | No |  |
| `name` | `string` | No | The desired name of the CollectibleItem. If not set, will use the underlying itemname. |
| `description` | `string` | No | The desired description of the CollectibleItem. If not set, will use the underlying itemname. |
| `onSaleTime` | `string` | No | Scheduled on sale time for publishing the item. |
| `offSaleTime` | `string` | No | Scheduled off sale time for publishing the item. |
| `agreementId` | `string` | No | Optional. Content-licensing agreement id for a licensed publish. If unset, publishing behavior is unchanged. Not persisted on the collectible. |

### Roblox.ItemConfiguration.Api.PublishCollectibleItemResponse

Response model for publishing a new CollectibleItem.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `status` | `0 \| 1 \| 2` | No | The status of the collectible being published. ['Succeeded' = 0, 'Failed' = 1, 'InProgress' = 2] |

### Roblox.ItemConfiguration.Api.Models.Request.Collectibles.BulkUpdateRequest

Request model for bulk updating items.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `idempotencyKey` | `string` | No | Idempotency key for the bulk update request. |
| `groupId` | `integer` | No | The group id, if the update is for a group. |
| `updateTargets` | `Roblox.ItemConfiguration.Api.Models.Request.Collectibles.BulkUpdateTargets` | No |  |
| `updatePayload` | `Roblox.ItemConfiguration.Api.Models.Request.Collectibles.BulkUpdatePayload` | No |  |

### Roblox.ItemConfiguration.Api.CheckItemConfigurationAccessResponse

Defines the response model for the GET v1/collectibles/check-item-configuration-access.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `isAllowed` | `boolean` | No | Whether or not the access is allowed. |
| `deniedReason` | `integer enum (144 values)` | No | Denied reason when the access is rejected. Can return the following denied reasons (MissingIdVerification, MissingTwoStepVerification, CreationAccessBlocked, MissingPremiumSubscriptionTier, GroupOwnerMissingPremiumSubscriptionTier, MissingCicRoleset). ['Unknown' = 0, 'InvalidTargetType' = 1, 'FailedToFetchPublishingFee' = 2, 'ServiceUnavailable' = 3, 'InvalidArgument' = 4, 'NotFound' = 5, 'FailedToGetCollectibleItemId' = 6, 'FailedToGetCommissionRates' = 7, 'NullParameterRequest' = 8, 'PublishLimitExceeded' = 9, 'AssetIsPendingValidation' = 10, 'AssetContainsInvalidContent' = 11, 'UserDoesNotHavePermissionsForGroupAsset' = 12, 'AssetTypeCannotBeReleased' = 13, 'AssetIsPendingReview' = 14, 'AssetIsModerated' = 15, 'ItemIsReleased' = 16, 'UserDoesNotHavePermissionToRelease' = 17, 'UserDoesNotOwnTheItem' = 18, 'ItemPriceTooLow' = 19, 'ItemPriceTooHigh' = 20, 'InvalidAssetId' = 21, 'InvalidAgent' = 22, 'NoExperiencesListed' = 23, 'NameIsModerated' = 24, 'DescriptionIsModerated' = 25, 'TextIsModerated' = 26, 'FailedToFilterText' = 27, 'AssetAlreadyReleasedAsUnlimited' = 28, 'AssetInDelayedRelease' = 29, 'InvalidIdempotencyToken' = 30, 'InvalidAgreedPublishingFee' = 31, 'GatewayCouldNotPublishItem' = 32, 'GroupAssetNotSupported' = 33, 'CouldNotFindInitialUserAsset' = 34, 'InvalidQuantity' = 35, 'SaleLocationCurrentlyNotSupported' = 36, 'InvalidCollectibleItemId' = 37, 'FailedToGetCollectibleItemInformation' = 38, 'GroupItemsNotSupported' = 39, 'FailedToUpdateCollectibleItem' = 40, 'PublishQuotaUnavailable' = 41, 'FailedToFetchMarketplaceFee' = 42, 'QuantityLimitCurrentlyNotSupported' = 43, 'InvalidQuantityLimit' = 44, 'ExactCopyOfAssetHasBeenPublished' = 45, 'ItemIsInBundle' = 46, 'ResaleRestrictionCurrentlyNotSupported' = 47, 'InvalidResaleRestriction' = 48, 'FailedToUpdateCollectibleDescription' = 49, 'InvalidBundleId' = 50, 'BundleTypeCannotBeReleased' = 51, 'BundleIsModerated' = 52, 'BundleAlreadyReleasedAsUnlimited' = 53, 'BundlesGatewayUnexpectedErrorCode' = 54, 'CissUnexpectedException' = 55, 'PublishingGatewayUnexpectedException' = 56, 'NonLimitedPublishingNotSupported' = 57, 'InvalidPublishingType' = 58, 'InvalidPriceOffset' = 59, 'InvalidMinimumPrice' = 60, 'InvalidSaleStatus' = 61, 'InvalidPriceConfiguration' = 62, 'FailedToGetPriceConfiguration' = 63, 'CannotBeFree' = 64, 'UnexpectedPlaceIds' = 65, 'MissingAuthenticatedUser' = 66, 'InvalidCreatorType' = 67, 'PermissionProviderNotEnabled' = 68, 'InvalidGroupId' = 69, 'InsufficientRobux' = 70, 'ItemNotFound' = 71, 'ItemIsModerated' = 72, 'ItemModerationUnknown' = 73, 'InvalidItemType' = 74, 'ItemHasArchivedDependencies' = 75, 'ItemIsDelisted' = 76, 'ResellableCreationNotAllowed' = 77, 'PolicyError' = 78, 'InvalidSaleLocationUpdate' = 79, 'InExperienceCreationPublishingBlocked' = 80, 'TokenServiceUnexpectedException' = 81, 'InvalidScheduledSaleStatus' = 82, 'InvalidCancelScheduledSaleStatus' = 83, 'ScheduledPublishingNotEnabled' = 84, 'OnSaleTimeInThePast' = 85, 'OffSaleTimeInThePast' = 86, 'OnSaleTimeTooFarInTheFuture' = 87, 'OffSaleTimeTooFarInTheFuture' = 88, 'OffSaleTimeBeforeOnSaleTime' = 89, 'ScheduledTimeOnSaleTooShort' = 90, 'ScheduledTimeAlreadySet' = 91, 'ScheduledTimeCannotSetItemOnSaleAgain' = 92, 'ScheduledTimeCannotSetItemOffSaleAgain' = 93, 'ActorIsModerated' = 94, 'CalendarQuotaExceeded' = 101, 'CalendarQuotaUnavailable' = 102, 'PublishingGatewayMissingReason' = 103, 'PublishingGatewayUnexpectedReason' = 104, 'PublishingGatewayUnexpectedAccessStatus' = 105, 'MissingIdVerification' = 106, 'CreationAccessBlocked' = 107, 'MissingPremiumSubscriptionTier' = 108, 'GroupOwnerMissingPremiumSubscriptionTier' = 109, 'MissingCicRoleset' = 110, 'AssetRestrictedByCommerce' = 111, 'DisallowedItemType' = 112, 'InvalidTargetId' = 113, 'PriceFloorNotFound' = 114, 'UserNotAuthorizedForAction' = 115, 'FailedToGetRevenueSplit' = 116, 'InvalidTransactionType' = 117, 'GrantedItemCannotBePublished' = 118, 'InvalidRentableType' = 119, 'LimitedItemsCannotBeRentable' = 120, 'TooManyPurchaseAttempts' = 121, 'InvalidName' = 122, 'InvalidDescription' = 123, 'RequestCancelled' = 124, 'MissingTwoStepVerification' = 125, 'FreeAvatarSystemNotEnabled' = 126, 'LookNotLinkedToUniverse' = 127, 'FreeAvatarMaxUniversesExceeded' = 128, 'LookItemCreatorMismatch' = 130, 'LookContainsLimitedItem' = 131, 'LookItemCollectibleDelisted' = 133, 'BundleNotFound' = 134, 'RestockingNotEnabled' = 135, 'ItemNotEligibleForRestocking' = 136, 'InvalidAgreedRestockingFee' = 137, 'FailedToRestockCollectibleItem' = 138, 'InvalidRestockQuantity' = 139, 'FailedToFetchRestockingFee' = 140, 'FailedToGetRestockEligibility' = 141, 'ResaleLockedAfterRestock' = 142, 'AiGeneratedItemPublishingBlocked' = 143, 'FailedToGetAgreement' = 144, 'FailedToGetLicense' = 145, 'AgreementNotPublishable' = 146, 'ResaleNotAllowedByLicense' = 147, 'ImmediateOnSaleNotAllowedForPendingAgreement' = 148, 'OnSaleTimeOutsideAgreementWindow' = 149, 'OffSaleTimeOutsideAgreementWindow' = 150, 'OffSaleTimeRequiredForAgreement' = 151] Values: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 101, 102, 103, 104, 105, 106, 107, 108, 109, 110, 111, 112, 113, 114, 115, 116, 117, 118, 119, 120, 121, 122, 123, 124, 125, 126, 127, 128, 130, 131, 133, 134, 135, 136, 137, 138, 139, 140, 141, 142, 143, 144, 145, 146, 147, 148, 149, 150, 151 |

### Roblox.ItemConfiguration.Api.CheckItemPublishAccessResponse

Defines the response model for the GET v1/collectibles/check-item-publish-access.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `isAllowed` | `boolean` | No | Whether or not the access is allowed. |
| `deniedReason` | `integer enum (144 values)` | No | Denied reason when the access is rejected. Can return the following denied reasons (MissingIdVerification, MissingTwoStepVerification, CreationAccessBlocked, MissingPremiumSubscriptionTier, GroupOwnerMissingPremiumSubscriptionTier, MissingCicRoleset). ['Unknown' = 0, 'InvalidTargetType' = 1, 'FailedToFetchPublishingFee' = 2, 'ServiceUnavailable' = 3, 'InvalidArgument' = 4, 'NotFound' = 5, 'FailedToGetCollectibleItemId' = 6, 'FailedToGetCommissionRates' = 7, 'NullParameterRequest' = 8, 'PublishLimitExceeded' = 9, 'AssetIsPendingValidation' = 10, 'AssetContainsInvalidContent' = 11, 'UserDoesNotHavePermissionsForGroupAsset' = 12, 'AssetTypeCannotBeReleased' = 13, 'AssetIsPendingReview' = 14, 'AssetIsModerated' = 15, 'ItemIsReleased' = 16, 'UserDoesNotHavePermissionToRelease' = 17, 'UserDoesNotOwnTheItem' = 18, 'ItemPriceTooLow' = 19, 'ItemPriceTooHigh' = 20, 'InvalidAssetId' = 21, 'InvalidAgent' = 22, 'NoExperiencesListed' = 23, 'NameIsModerated' = 24, 'DescriptionIsModerated' = 25, 'TextIsModerated' = 26, 'FailedToFilterText' = 27, 'AssetAlreadyReleasedAsUnlimited' = 28, 'AssetInDelayedRelease' = 29, 'InvalidIdempotencyToken' = 30, 'InvalidAgreedPublishingFee' = 31, 'GatewayCouldNotPublishItem' = 32, 'GroupAssetNotSupported' = 33, 'CouldNotFindInitialUserAsset' = 34, 'InvalidQuantity' = 35, 'SaleLocationCurrentlyNotSupported' = 36, 'InvalidCollectibleItemId' = 37, 'FailedToGetCollectibleItemInformation' = 38, 'GroupItemsNotSupported' = 39, 'FailedToUpdateCollectibleItem' = 40, 'PublishQuotaUnavailable' = 41, 'FailedToFetchMarketplaceFee' = 42, 'QuantityLimitCurrentlyNotSupported' = 43, 'InvalidQuantityLimit' = 44, 'ExactCopyOfAssetHasBeenPublished' = 45, 'ItemIsInBundle' = 46, 'ResaleRestrictionCurrentlyNotSupported' = 47, 'InvalidResaleRestriction' = 48, 'FailedToUpdateCollectibleDescription' = 49, 'InvalidBundleId' = 50, 'BundleTypeCannotBeReleased' = 51, 'BundleIsModerated' = 52, 'BundleAlreadyReleasedAsUnlimited' = 53, 'BundlesGatewayUnexpectedErrorCode' = 54, 'CissUnexpectedException' = 55, 'PublishingGatewayUnexpectedException' = 56, 'NonLimitedPublishingNotSupported' = 57, 'InvalidPublishingType' = 58, 'InvalidPriceOffset' = 59, 'InvalidMinimumPrice' = 60, 'InvalidSaleStatus' = 61, 'InvalidPriceConfiguration' = 62, 'FailedToGetPriceConfiguration' = 63, 'CannotBeFree' = 64, 'UnexpectedPlaceIds' = 65, 'MissingAuthenticatedUser' = 66, 'InvalidCreatorType' = 67, 'PermissionProviderNotEnabled' = 68, 'InvalidGroupId' = 69, 'InsufficientRobux' = 70, 'ItemNotFound' = 71, 'ItemIsModerated' = 72, 'ItemModerationUnknown' = 73, 'InvalidItemType' = 74, 'ItemHasArchivedDependencies' = 75, 'ItemIsDelisted' = 76, 'ResellableCreationNotAllowed' = 77, 'PolicyError' = 78, 'InvalidSaleLocationUpdate' = 79, 'InExperienceCreationPublishingBlocked' = 80, 'TokenServiceUnexpectedException' = 81, 'InvalidScheduledSaleStatus' = 82, 'InvalidCancelScheduledSaleStatus' = 83, 'ScheduledPublishingNotEnabled' = 84, 'OnSaleTimeInThePast' = 85, 'OffSaleTimeInThePast' = 86, 'OnSaleTimeTooFarInTheFuture' = 87, 'OffSaleTimeTooFarInTheFuture' = 88, 'OffSaleTimeBeforeOnSaleTime' = 89, 'ScheduledTimeOnSaleTooShort' = 90, 'ScheduledTimeAlreadySet' = 91, 'ScheduledTimeCannotSetItemOnSaleAgain' = 92, 'ScheduledTimeCannotSetItemOffSaleAgain' = 93, 'ActorIsModerated' = 94, 'CalendarQuotaExceeded' = 101, 'CalendarQuotaUnavailable' = 102, 'PublishingGatewayMissingReason' = 103, 'PublishingGatewayUnexpectedReason' = 104, 'PublishingGatewayUnexpectedAccessStatus' = 105, 'MissingIdVerification' = 106, 'CreationAccessBlocked' = 107, 'MissingPremiumSubscriptionTier' = 108, 'GroupOwnerMissingPremiumSubscriptionTier' = 109, 'MissingCicRoleset' = 110, 'AssetRestrictedByCommerce' = 111, 'DisallowedItemType' = 112, 'InvalidTargetId' = 113, 'PriceFloorNotFound' = 114, 'UserNotAuthorizedForAction' = 115, 'FailedToGetRevenueSplit' = 116, 'InvalidTransactionType' = 117, 'GrantedItemCannotBePublished' = 118, 'InvalidRentableType' = 119, 'LimitedItemsCannotBeRentable' = 120, 'TooManyPurchaseAttempts' = 121, 'InvalidName' = 122, 'InvalidDescription' = 123, 'RequestCancelled' = 124, 'MissingTwoStepVerification' = 125, 'FreeAvatarSystemNotEnabled' = 126, 'LookNotLinkedToUniverse' = 127, 'FreeAvatarMaxUniversesExceeded' = 128, 'LookItemCreatorMismatch' = 130, 'LookContainsLimitedItem' = 131, 'LookItemCollectibleDelisted' = 133, 'BundleNotFound' = 134, 'RestockingNotEnabled' = 135, 'ItemNotEligibleForRestocking' = 136, 'InvalidAgreedRestockingFee' = 137, 'FailedToRestockCollectibleItem' = 138, 'InvalidRestockQuantity' = 139, 'FailedToFetchRestockingFee' = 140, 'FailedToGetRestockEligibility' = 141, 'ResaleLockedAfterRestock' = 142, 'AiGeneratedItemPublishingBlocked' = 143, 'FailedToGetAgreement' = 144, 'FailedToGetLicense' = 145, 'AgreementNotPublishable' = 146, 'ResaleNotAllowedByLicense' = 147, 'ImmediateOnSaleNotAllowedForPendingAgreement' = 148, 'OnSaleTimeOutsideAgreementWindow' = 149, 'OffSaleTimeOutsideAgreementWindow' = 150, 'OffSaleTimeRequiredForAgreement' = 151] Values: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 101, 102, 103, 104, 105, 106, 107, 108, 109, 110, 111, 112, 113, 114, 115, 116, 117, 118, 119, 120, 121, 122, 123, 124, 125, 126, 127, 128, 130, 131, 133, 134, 135, 136, 137, 138, 139, 140, 141, 142, 143, 144, 145, 146, 147, 148, 149, 150, 151 |

### Roblox.ItemConfiguration.Api.CheckItemUploadAccessResponse

Defines the response model for the GET v1/collectibles/check-item-upload-access.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `isAllowed` | `boolean` | No | Whether or not the access is allowed. |
| `deniedReason` | `integer enum (144 values)` | No | Denied reason when the access is rejected. Can return the following denied reasons (MissingIdVerification, MissingTwoStepVerification, CreationAccessBlocked, MissingPremiumSubscriptionTier, MissingCicRoleset). ['Unknown' = 0, 'InvalidTargetType' = 1, 'FailedToFetchPublishingFee' = 2, 'ServiceUnavailable' = 3, 'InvalidArgument' = 4, 'NotFound' = 5, 'FailedToGetCollectibleItemId' = 6, 'FailedToGetCommissionRates' = 7, 'NullParameterRequest' = 8, 'PublishLimitExceeded' = 9, 'AssetIsPendingValidation' = 10, 'AssetContainsInvalidContent' = 11, 'UserDoesNotHavePermissionsForGroupAsset' = 12, 'AssetTypeCannotBeReleased' = 13, 'AssetIsPendingReview' = 14, 'AssetIsModerated' = 15, 'ItemIsReleased' = 16, 'UserDoesNotHavePermissionToRelease' = 17, 'UserDoesNotOwnTheItem' = 18, 'ItemPriceTooLow' = 19, 'ItemPriceTooHigh' = 20, 'InvalidAssetId' = 21, 'InvalidAgent' = 22, 'NoExperiencesListed' = 23, 'NameIsModerated' = 24, 'DescriptionIsModerated' = 25, 'TextIsModerated' = 26, 'FailedToFilterText' = 27, 'AssetAlreadyReleasedAsUnlimited' = 28, 'AssetInDelayedRelease' = 29, 'InvalidIdempotencyToken' = 30, 'InvalidAgreedPublishingFee' = 31, 'GatewayCouldNotPublishItem' = 32, 'GroupAssetNotSupported' = 33, 'CouldNotFindInitialUserAsset' = 34, 'InvalidQuantity' = 35, 'SaleLocationCurrentlyNotSupported' = 36, 'InvalidCollectibleItemId' = 37, 'FailedToGetCollectibleItemInformation' = 38, 'GroupItemsNotSupported' = 39, 'FailedToUpdateCollectibleItem' = 40, 'PublishQuotaUnavailable' = 41, 'FailedToFetchMarketplaceFee' = 42, 'QuantityLimitCurrentlyNotSupported' = 43, 'InvalidQuantityLimit' = 44, 'ExactCopyOfAssetHasBeenPublished' = 45, 'ItemIsInBundle' = 46, 'ResaleRestrictionCurrentlyNotSupported' = 47, 'InvalidResaleRestriction' = 48, 'FailedToUpdateCollectibleDescription' = 49, 'InvalidBundleId' = 50, 'BundleTypeCannotBeReleased' = 51, 'BundleIsModerated' = 52, 'BundleAlreadyReleasedAsUnlimited' = 53, 'BundlesGatewayUnexpectedErrorCode' = 54, 'CissUnexpectedException' = 55, 'PublishingGatewayUnexpectedException' = 56, 'NonLimitedPublishingNotSupported' = 57, 'InvalidPublishingType' = 58, 'InvalidPriceOffset' = 59, 'InvalidMinimumPrice' = 60, 'InvalidSaleStatus' = 61, 'InvalidPriceConfiguration' = 62, 'FailedToGetPriceConfiguration' = 63, 'CannotBeFree' = 64, 'UnexpectedPlaceIds' = 65, 'MissingAuthenticatedUser' = 66, 'InvalidCreatorType' = 67, 'PermissionProviderNotEnabled' = 68, 'InvalidGroupId' = 69, 'InsufficientRobux' = 70, 'ItemNotFound' = 71, 'ItemIsModerated' = 72, 'ItemModerationUnknown' = 73, 'InvalidItemType' = 74, 'ItemHasArchivedDependencies' = 75, 'ItemIsDelisted' = 76, 'ResellableCreationNotAllowed' = 77, 'PolicyError' = 78, 'InvalidSaleLocationUpdate' = 79, 'InExperienceCreationPublishingBlocked' = 80, 'TokenServiceUnexpectedException' = 81, 'InvalidScheduledSaleStatus' = 82, 'InvalidCancelScheduledSaleStatus' = 83, 'ScheduledPublishingNotEnabled' = 84, 'OnSaleTimeInThePast' = 85, 'OffSaleTimeInThePast' = 86, 'OnSaleTimeTooFarInTheFuture' = 87, 'OffSaleTimeTooFarInTheFuture' = 88, 'OffSaleTimeBeforeOnSaleTime' = 89, 'ScheduledTimeOnSaleTooShort' = 90, 'ScheduledTimeAlreadySet' = 91, 'ScheduledTimeCannotSetItemOnSaleAgain' = 92, 'ScheduledTimeCannotSetItemOffSaleAgain' = 93, 'ActorIsModerated' = 94, 'CalendarQuotaExceeded' = 101, 'CalendarQuotaUnavailable' = 102, 'PublishingGatewayMissingReason' = 103, 'PublishingGatewayUnexpectedReason' = 104, 'PublishingGatewayUnexpectedAccessStatus' = 105, 'MissingIdVerification' = 106, 'CreationAccessBlocked' = 107, 'MissingPremiumSubscriptionTier' = 108, 'GroupOwnerMissingPremiumSubscriptionTier' = 109, 'MissingCicRoleset' = 110, 'AssetRestrictedByCommerce' = 111, 'DisallowedItemType' = 112, 'InvalidTargetId' = 113, 'PriceFloorNotFound' = 114, 'UserNotAuthorizedForAction' = 115, 'FailedToGetRevenueSplit' = 116, 'InvalidTransactionType' = 117, 'GrantedItemCannotBePublished' = 118, 'InvalidRentableType' = 119, 'LimitedItemsCannotBeRentable' = 120, 'TooManyPurchaseAttempts' = 121, 'InvalidName' = 122, 'InvalidDescription' = 123, 'RequestCancelled' = 124, 'MissingTwoStepVerification' = 125, 'FreeAvatarSystemNotEnabled' = 126, 'LookNotLinkedToUniverse' = 127, 'FreeAvatarMaxUniversesExceeded' = 128, 'LookItemCreatorMismatch' = 130, 'LookContainsLimitedItem' = 131, 'LookItemCollectibleDelisted' = 133, 'BundleNotFound' = 134, 'RestockingNotEnabled' = 135, 'ItemNotEligibleForRestocking' = 136, 'InvalidAgreedRestockingFee' = 137, 'FailedToRestockCollectibleItem' = 138, 'InvalidRestockQuantity' = 139, 'FailedToFetchRestockingFee' = 140, 'FailedToGetRestockEligibility' = 141, 'ResaleLockedAfterRestock' = 142, 'AiGeneratedItemPublishingBlocked' = 143, 'FailedToGetAgreement' = 144, 'FailedToGetLicense' = 145, 'AgreementNotPublishable' = 146, 'ResaleNotAllowedByLicense' = 147, 'ImmediateOnSaleNotAllowedForPendingAgreement' = 148, 'OnSaleTimeOutsideAgreementWindow' = 149, 'OffSaleTimeOutsideAgreementWindow' = 150, 'OffSaleTimeRequiredForAgreement' = 151] Values: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 101, 102, 103, 104, 105, 106, 107, 108, 109, 110, 111, 112, 113, 114, 115, 116, 117, 118, 119, 120, 121, 122, 123, 124, 125, 126, 127, 128, 130, 131, 133, 134, 135, 136, 137, 138, 139, 140, 141, 142, 143, 144, 145, 146, 147, 148, 149, 150, 151 |

### Roblox.ItemConfiguration.Api.GetCommissionRatesResponse

Defines the response model for the v1/collectibles/commission-rates.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `creatorFeesPercentage` | `integer` | No | Creator fees percentage. |
| `marketplaceFeesPercentage` | `integer` | No | Marketplace fees percentage. |
| `resellerFeesPercentage` | `integer` | No | Reseller fees percentage. |
| `sellerFeesPercentage` | `integer` | No | Seller fees percentage. |

### Roblox.ItemConfiguration.Api.CollectiblesMetadataResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `isCollectiblesControllerEnabled` | `boolean` | No | Determines if the Collectibles controller and its APIs are enabled. |
| `isCollectiblesPublishingEnabled` | `boolean` | No | Determines if publishing Collectible Items is enabled. |
| `isCollectiblesPublishingLocationTypeEnabled` | `boolean` | No | Determines if other sale locations are enabled. |
| `allowedCollectibleSaleLocations` | `0 \| 1 \| 2 \| 3 \| 4[]` | No | The list of available SaleLocations for collectible items. |
| `IsCollectibleFreeItemPublishingAvailable` | `boolean` | No | Whether or not publishing free Collectibles is allowed. |
| `isCollectibleGroupPublishingAvailable` | `boolean` | No | Whether or not publishing Collectibles for groups is allowed. |
| `isCollectibleResaleRestrictionsEnabled` | `boolean` | No | Whether or not resale restrictions for Collectibles are enabled. |
| `isCollectiblePublishMinQuantityEnabled` | `boolean` | No | Whether or not minimum quantity for Collectibles are enabled. |
| `IsUgc4AllUIEnabled` | `boolean` | No | Flag whether the new UI is enabled. |
| `LimitedMaxQuantity` | `integer` | No | The maximum quantity for limited item publishing. |
| `MaxCollectiblePrice` | `integer` | No | The maximum price for a collectible item. |
| `IsLimitedCollectibleBundlesPublishingEnabled` | `boolean` | No | Determines whether limited collectible bundles publishing is enabled. |
| `IsResellabilityEnabled` | `boolean` | No | Whether or not publishing resellable items is enabled. |
| `IsNewBundleUIEnabled` | `boolean` | No | Whether or not dpf bundle UI is enabled. |
| `IsCollectible2DPublishingEnabled` | `boolean` | No | Whether or not collectible 2D publishing is enabled. |
| `IsAvatarCreationTokensUIEnabled` | `boolean` | No | Whether or not the avatar creation tokens page should be displayed. |
| `IsScheduledPublishingEnabled` | `boolean` | No | Whether or not scheduled publishing is enabled. |
| `ScheduledPublishingSettings` | `Roblox.ItemConfiguration.Api.ScheduledPublishingSettings` | No |  |
| `isGetPriceFloorEnabled` | `boolean` | No | Determines whether GetPriceFloorAsync endpoint is enabled. |
| `isRegionalPricingEnabled` | `boolean` | No | Whether regional pricing is enabled. |
| `isRevenueSplitEnabled` | `boolean` | No | Whether revenue split endpoint is enabled. |
| `revenueSplitTiersForPurchase` | `Roblox.ItemConfiguration.Api.RevenueSplitTier[]` | No | List of revenue split tiers for purchase. |
| `isContentMetadataAppealEnabled` | `boolean` | No | Whether content metadata appeals are enabled. Always false; the appeal endpoints have been removed. |
| `bodysuitEligibleAssetTypes` | `integer[]` | No | List of asset types that are bodysuit eligible. |
| `unifyConfigureUI` | `boolean` | No | Whether the new configure UI is enabled for 2D assets. |
| `isRestockingEnabled` | `boolean` | No | Whether restocking of limited collectible items is enabled. |
| `restockResaleLockDurationSeconds` | `integer` | No | Duration in seconds that resale remains locked after a restock. The FE computes the unlock time as lastRestockedTime + this duration. |
| `isAvatarItemLicensingEnabled` | `boolean` | No | Whether the Avatar Item Licensing feature (UCP-1792) is enabled. The frontend shows/hides the licensing UI (e.g. the agreement picker) off this value, which mirrors the same server-side gate used to enable the licensing behavior. |
| `isMarketplaceAffiliateLinkUiEnabled` | `boolean` | No | Whether the marketplace affiliate link UI is enabled for the authenticated user. |

### Roblox.ItemConfiguration.Api.Models.Response.Collectibles.PriceFloorResponse

Price floor response.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `priceFloorInRobux` | `integer` | No | Price floor in Robux. |
| `displayName` | `string` | No | Optional display name for the price floor. |

### Roblox.ItemConfiguration.Api.PublishingFeeResponse

Response Model for Collectibles Publishing Fee request.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `publishingFeeInRobux` | `integer` | No | Publishing fee in Robux for a Collectible. |
| `unitPublishingFeeInRobux` | `integer` | No | Publishing fee per-unit in Robux for a Collectible. |
| `isDynamicFeeEnabled` | `boolean` | No | Whether the publishing fee is using a dynamically set value. |
| `publishingFeeType` | `0 \| 1 \| 2` | No | The type of the publishing fee. ['Invalid' = 0, 'PayPerInstance' = 1, 'PayInTotal' = 2] |

### Roblox.ItemConfiguration.Api.PublishingFeePreviewResponse

Response Model for a previewed Collectibles publishing fee.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `publishingFeeInRobux` | `integer` | No | Publishing fee in Robux for a Collectible. |
| `publishingFeeType` | `0 \| 1 \| 2` | No | The type of the publishing fee. ['Invalid' = 0, 'PayPerInstance' = 1, 'PayInTotal' = 2] |

### Roblox.ItemConfiguration.Api.GetRegionalpricingPreviewResponse

Defines the response model for the POST v1/collectibles/regional-pricing/preview.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `regionalPrices` | `Roblox.ItemConfiguration.Api.RegionalPrice[]` | No | List of representative countries. |

### Roblox.ItemConfiguration.Api.GetRepresentativeCountriesResponse

Defines the response model for the GET v1/collectibles/regional-pricing/representative-countries.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `countryIso2Codes` | `string[]` | No | List of representative countries. |

### Roblox.ItemConfiguration.Api.Models.Response.GetRentalPricingPreviewResponse

Defines the response model for the POST v1/collectibles/rental-pricing/preview.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `rentalPrices` | `Roblox.ItemConfiguration.Api.RentalOption[]` | No | Rental prices for the given target. |
| `regionalRentalPrices` | `Roblox.ItemConfiguration.Api.Models.MarketplaceItem.RegionalRentalPrice[]` | No | The regional rental prices for the given target. |

### Roblox.ItemConfiguration.Api.Models.Request.Collectibles.RevenueSplitResponse

Response model for Revenue Split.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `RevenueSplit` | `Roblox.ItemConfiguration.Api.RevenueSplit` | No |  |

### Roblox.ItemConfiguration.Api.Models.Request.UpdateItemDisplayInformationRequest

Api request to update the display information of an item.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `targetType` | `0 \| 1 \| 2 \| 3` | No | The type of the item. ['Asset' = 0, 'Bundle' = 1, 'IecToken' = 2, 'Look' = 3] |
| `targetId` | `string` | No | The id of the item. |
| `name` | `string` | No | The name of the item. Null means no update. |
| `description` | `string` | No | The description for the item. Null means no update. |

### Roblox.ItemConfiguration.Api.Models.Request.UpdateCollectibleItemRequest

Api request to update a collectible item.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `saleLocationConfiguration` | `Roblox.ItemConfiguration.Api.Models.Request.CollectiblesSaleLocationConfigurationModel` | No |  |
| `isRentalOptIn` | `boolean` | No | Whether the item is opted into rental. |
| `saleStatus` | `0 \| 1 \| 2` | No | The new sale status for the associated CollectibleItem. OnSale and OffSale are the only valid values. ['OnSale' = 0, 'OffSale' = 1, 'Free' = 2] |
| `quantityLimitPerUser` | `integer` | No | The max number of instances for the CollectibleItem a user can own. |
| `resaleRestriction` | `0 \| 1 \| 2` | No | The resale restriction of the CollectibleItem. ['INVALID' = 0, 'NONE' = 1, 'DISABLED' = 2] |
| `priceInRobux` | `integer` | No | The minimum price of the CollectibleItem. |
| `priceOffset` | `integer` | No | The price offset of the item in Robux above the price floor. |
| `optOutFromRegionalPricing` | `boolean` | No | Whether to opt out of the regional pricing. |
| `isFree` | `boolean` | No | Whether or not the item is free. If it's free, the MinimumPrice and PriceOffset values are ignored. |
| `onSaleTime` | `string` | No | Scheduled on sale time for publishing the item. |
| `offSaleTime` | `string` | No | Scheduled off sale time for publishing the item. |

### Roblox.ItemConfiguration.Api.Models.Request.Collectibles.RestockCollectibleItemRequest

Request model for restocking a collectible item.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `newTotalQuantity` | `integer` | No | The new total quantity for the item after restocking. |
| `agreedRestockingFee` | `integer` | No | The restocking fee the user agreed to pay. |

### Roblox.ItemConfiguration.Api.Models.Response.Collectibles.RestockCollectibleItemResponse

Response model for restocking a collectible item.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `newTotalQuantity` | `integer` | No | The new total quantity after restock. |

### Roblox.ItemConfiguration.Api.Models.Response.Collectibles.RestockEligibilityResponse

Structured eligibility response so the frontend does not need to re-derive restocking eligibility.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `isRestockingEnabled` | `boolean` | No | Whether the restocking feature is globally enabled. |
| `isEligible` | `boolean` | No | Whether the item is eligible for restocking right now. |
| `ineligibilityReason` | `integer enum (8 values)` | No | Why the item is ineligible for restocking. Serialized as PascalCase enum name (e.g. "NotLimited", "NotFree"). Null/omitted when the item is eligible. Values: 0, 1, 2, 3, 4, 5, 6, 7 |
| `hasBeenRestocked` | `boolean` | No | Whether the item has been restocked before (derived from TotalRestockedQuantity > 0). |
| `totalRestockedQuantity` | `integer` | No | Cumulative restocked quantity so far. |
| `maxRestockQuantityPerOperation` | `integer` | No | Maximum additional quantity allowed in a single restock operation. |

### Roblox.ItemConfiguration.Api.Models.Response.Collectibles.RestockingFeeResponse

Response model for getting the restocking fee.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `restockingFeeInRobux` | `integer` | No | The total restocking fee in Robux. |
| `unitRestockingFeeInRobux` | `integer` | No | The per-unit restocking fee in Robux. |

### Roblox.ItemConfiguration.Api.AssetCreationsDetailsRequest

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `AssetIds` | `integer[]` | No |  |

### Roblox.ItemConfiguration.Api.AssetCreationsDetailsResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `assetId` | `integer` | No | The asset Id. |
| `name` | `string` | No | The asset name. |
| `status` | `string enum (8 values)` | No | The asset status. ['Unknown' = 0, 'ReviewPending' = 1, 'Moderated' = 2, 'ReviewApproved' = 3, 'OnSale' = 4, 'OffSale' = 5, 'DelayedRelease' = 6, 'Free' = 7] Values: Unknown, ReviewPending, Moderated, ReviewApproved, OnSale, OffSale, DelayedRelease, Free |
| `description` | `string` | No | The asset description. |
| `creatorType` | `Unknown \| User \| Group` | No | The creator type. ['Unknown' = 0, 'User' = 1, 'Group' = 2] |
| `creatorTargetId` | `integer` | No | The creator target Id. |
| `isArchived` | `boolean` | No | Is the asset archived. |
| `assetType` | `string` | No | Type of the asset. |
| `created` | `string` | No | Date asset was created. |
| `updated` | `string` | No | Date asset was created. |

### Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.ItemConfiguration.Api.AssetCreationsResponse_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `previousPageCursor` | `string` | No |  |
| `nextPageCursor` | `string` | No |  |
| `data` | `Roblox.ItemConfiguration.Api.AssetCreationsResponse[]` | No |  |

### Roblox.Catalog.Api.AssetFavoriteModel

A model to represent asset favorites.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `assetId` | `integer` | No | The Id of the asset being favorited. |
| `userId` | `integer` | No | The Id of the user favoriting the asset. |
| `created` | `string` | No | The time at which the user favorited the asset. |

### Roblox.Catalog.Api.BundleFavoriteModel

A model to represent bundle favorites.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `bundleId` | `integer` | No | The Id of the bundle being favorited. |
| `userId` | `integer` | No | The Id of the user favoriting the bundle. |
| `created` | `string` | No | The time at which the user favorited the bundle. |

### Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Catalog.Api.CatalogSearchDetailedResponseItem_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `previousPageCursor` | `string` | No |  |
| `nextPageCursor` | `string` | No |  |
| `data` | `Roblox.Catalog.Api.CatalogSearchDetailedResponseItem[]` | No |  |

### Roblox.Catalog.Api.FavoriteBundlesResponse

A response containing favorited bundles and whether there are more.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `favorites` | `Roblox.Catalog.Api.BundleDetailsModel[]` | No | Collection of favorited bundles and associated details. |
| `moreFavorites` | `boolean` | No | True if there exists a next page of favorited bundles. |
| `nextCursor` | `string` | No | Pagination cursor for the next page. |
| `previousCursor` | `string` | No | Pagination cursor for the previous page. |

### Roblox.ItemConfiguration.Api.Models.Response.Folder.GetFoldersResponse

Response model for getting folders.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `folders` | `Roblox.ItemConfiguration.Api.Models.Folder.Folder[]` | No | The list of folders for the authenticated user. |

### Roblox.ItemConfiguration.Api.Models.Request.Folder.CreateFolderRequest

Request model for creating a new folder.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `name` | `string` | No | The name of the folder to create. |
| `parentFolderId` | `string` | No | The ID of the parent folder. Null for root folders. |
| `groupId` | `integer` | No | The group id that the folder will to belong to. |

### Roblox.ItemConfiguration.Api.Models.Response.Folder.CreateFolderResponse

Response model for creating a folder.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `folderId` | `string` | No | The ID of the created folder. |

### Roblox.ItemConfiguration.Api.Models.Folder.Folder

Information about a folder.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `folderId` | `string` | No | The unique identifier for the folder. |
| `name` | `string` | No | The name of the folder. |
| `parentFolderId` | `string` | No | The ID of the parent folder. Null for root folders. |

### Roblox.ItemConfiguration.Api.Models.Request.Folder.UpdateFolderRequest

Request model for updating a folder name.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `name` | `string` | No | The new name for the folder. |

### Roblox.ItemConfiguration.Api.Models.Response.Folder.GetFolderItemsResponse

Response model for getting folder items.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `items` | `Roblox.ItemConfiguration.Api.Models.Folder.FolderItemDetails[]` | No | The list of items in the folder. |
| `nextCursor` | `string` | No |  |
| `prevCursor` | `string` | No |  |

### Roblox.ItemConfiguration.Api.Models.Request.Folder.AddItemsRequest

Request model for adding one or more items to a folder.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `items` | `Roblox.ItemConfiguration.Api.Models.Folder.FolderItem[]` | No | The items to add to the folder. |

### Roblox.ItemConfiguration.Api.Models.Request.Folder.DeleteItemsRequest

Request model for removing one or more items from a folder via the bulk DELETE endpoint.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `items` | `Roblox.ItemConfiguration.Api.Models.Folder.FolderItem[]` | No | The items to remove from the folder. |

### Roblox.ItemConfiguration.Api.GetItemResponse

Defines the response model for the GET v1/marketplace-items/get-item.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `item` | `Roblox.ItemConfiguration.Api.MarketplaceItem` | No |  |

### Roblox.ItemConfiguration.Api.GetItemsByCreatorResponse

Defines the response model for the GET v2/creations/get-items-by-creator.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `items` | `Roblox.ItemConfiguration.Api.MarketplaceItem[]` | No | The list of marketplace items. |
| `nextCursor` | `string` | No | The next cursor. |
| `prevCursor` | `string` | No | The previous cursor. |

### Roblox.ItemConfiguration.Api.Models.Response.GetItemsByTokenResponse

Defines the response model for the GET v1/items/by-token.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `items` | `Roblox.ItemConfiguration.Api.MarketplaceItem[]` | No | The list of marketplace items. |
| `nextCursor` | `string` | No | The next cursor. |
| `prevCursor` | `string` | No | The previous cursor. |

### Roblox.ItemConfiguration.Api.Models.Response.GetCategoriesResponse

Defines the response model for GET v1/items/categories.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `categoriesVersionId` | `string` | No | The version id of the tree the categories were resolved from. |
| `categories` | `Roblox.ItemConfiguration.Api.Models.Response.CategoryNode[]` | No | The root category nodes of the hierarchy. |

### Roblox.ItemConfiguration.Api.Models.Response.GetPriceFloorResponse

Defines the response model for the GET v1/items/price-floor endpoint.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `priceFloor` | `integer` | No | The price floor. |
| `paidItemPublishingFee` | `Roblox.ItemConfiguration.Api.Models.Response.PublishingFeeInfo` | No |  |
| `freeItemPublishingFee` | `Roblox.ItemConfiguration.Api.Models.Response.PublishingFeeInfo` | No |  |

### Roblox.ItemConfiguration.Api.GetItemUploadFeeResponse

Defines the response model for the GET v1/items/upload-fee endpoint.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `canAfford` | `boolean` | No | Whether the user can afford the upload fee with their current balance. |
| `price` | `integer` | No | The upload fee. |
| `balance` | `integer` | No | The user's current robux balance. |

### Roblox.ItemConfiguration.Api.Models.Response.IsActionAllowedForItemTypeResponse

Result of checking whether a marketplace action is allowed for a specific item type for the agent.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `isActionAllowed` | `boolean` | No | Whether the action is allowed for the given item type and agent. |
| `metadataPermissions` | `object` | No | Permissions for configured metadata values. Key is MetadataName string (e.g., "EmissiveResult"). Absent keys are unrestricted (allowed). Null when metadata permissions are not available. |

### Roblox.ItemConfiguration.Api.Models.Request.AllowedGroupsForActionResponse

The response DTO for the allowed groups for a specified Roblox.ItemConfiguration.Api.Enums.MarketplaceAction.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `allowedGroups` | `Roblox.ItemConfiguration.Api.Models.Response.GroupInfo[]` | No | The list of groups allowed for the user for the given action. |

### Roblox.ItemConfiguration.Api.Models.Response.AllowedItemTypesForActionResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `allowedAssetTypes` | `string[]` | No | The list of asset types allowed for the user for the given Roblox.ItemConfiguration.Api.Enums.MarketplaceAction. |
| `allowedBundleTypes` | `string[]` | No | The list of bundle types allowed for the user for the given Roblox.ItemConfiguration.Api.Enums.MarketplaceAction. |

### Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Web.Responses.Plugins.PluginResponse_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `data` | `Roblox.Web.Responses.Plugins.PluginResponse[]` | No |  |

### Roblox.Develop.Api.UpdatePluginRequest

A request model for updating a plugin.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `name` | `string` | No | The new plugin name. |
| `description` | `string` | No | The new plugin description. |
| `commentsEnabled` | `boolean` | No | Whether or not comments should be enabled. |

### Roblox.ItemConfiguration.Api.Models.Response.PublishingPreferences.PublishingPreferencesResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `string` | No |  |
| `creatorUserId` | `integer` | No |  |
| `creatorGroupId` | `integer` | No |  |
| `publishingType` | `0 \| 1 \| 2` | No | Publishing type for the collectible. Currently can be either Limited or NonLimited. ['Invalid' = 0, 'Limited' = 1, 'NonLimited' = 2] |
| `saleLocationType` | `0 \| 1 \| 2 \| 3 \| 4` | No | Represents possible SaleLocation types of the Collectibles System. ['SALE_LOCATION_TYPE_INVALID' = 0, 'SALE_LOCATION_TYPE_SHOP_AND_ALL_EXPERIENCES' = 1, 'SALE_LOCATION_EXPERIENCES_AND_DEV_API_ONLY' = 2, 'SALE_LOCATION_TYPE_SHOP_ONLY' = 3, 'SALE_LOCATION_TYPE_SHOP_AND_EXPERIENCES_BY_ID' = 4] |
| `places` | `integer[]` | No |  |
| `priceInRobux` | `integer` | No |  |
| `priceOffset` | `integer` | No |  |
| `isFree` | `boolean` | No |  |
| `enableRegionalPricing` | `boolean` | No |  |
| `isRentalOptIn` | `boolean` | No |  |
| `autoPublishEnabled` | `boolean` | No |  |
| `created` | `string` | No |  |
| `updated` | `string` | No |  |

### Roblox.ItemConfiguration.Api.Models.Request.PublishingPreferences.CreatePublishingPreferencesRequest

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `creatorUserId` | `integer` | No |  |
| `creatorGroupId` | `integer` | No |  |
| `publishingType` | `0 \| 1 \| 2` | No | Publishing type for the collectible. Currently can be either Limited or NonLimited. ['Invalid' = 0, 'Limited' = 1, 'NonLimited' = 2] |
| `saleLocationType` | `0 \| 1 \| 2 \| 3 \| 4` | No | Represents possible SaleLocation types of the Collectibles System. ['SALE_LOCATION_TYPE_INVALID' = 0, 'SALE_LOCATION_TYPE_SHOP_AND_ALL_EXPERIENCES' = 1, 'SALE_LOCATION_EXPERIENCES_AND_DEV_API_ONLY' = 2, 'SALE_LOCATION_TYPE_SHOP_ONLY' = 3, 'SALE_LOCATION_TYPE_SHOP_AND_EXPERIENCES_BY_ID' = 4] |
| `places` | `integer[]` | No |  |
| `priceInRobux` | `integer` | No |  |
| `priceOffset` | `integer` | No |  |
| `isFree` | `boolean` | No |  |
| `enableRegionalPricing` | `boolean` | No |  |
| `isRentalOptIn` | `boolean` | No |  |
| `autoPublishEnabled` | `boolean` | No |  |

### Roblox.ItemConfiguration.Api.Models.Request.PublishingPreferences.UpdatePublishingPreferencesRequest

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `creatorUserId` | `integer` | No |  |
| `creatorGroupId` | `integer` | No |  |
| `publishingType` | `0 \| 1 \| 2` | No |  |
| `saleLocationType` | `0 \| 1 \| 2 \| 3 \| 4` | No |  |
| `places` | `integer[]` | No |  |
| `priceInRobux` | `integer` | No |  |
| `priceOffset` | `integer` | No |  |
| `isFree` | `boolean` | No |  |
| `enableRegionalPricing` | `boolean` | No |  |
| `isRentalOptIn` | `boolean` | No |  |
| `autoPublishEnabled` | `boolean` | No |  |

### Roblox.Economy.Api.Models.PurchasableDetailResponse

Purchasable detail request model.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `purchasable` | `boolean` | No | Defines if the product is purchasable. |
| `reason` | `integer enum (27 values)` | No | Defines the reason for failure. Values: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26 |
| `productId` | `integer` | No | Reflects the requested product id for reference. |
| `statusCode` | `integer` | No |  |
| `title` | `string` | No |  |
| `errorMsg` | `string` | No |  |
| `showDivId` | `string` | No |  |
| `shortfallPrice` | `integer` | No |  |
| `balanceAfterSale` | `integer` | No |  |
| `expectedPrice` | `integer` | No |  |
| `currency` | `integer` | No |  |
| `price` | `integer` | No |  |
| `assetId` | `integer` | No |  |
| `assetName` | `string` | No |  |
| `assetType` | `string` | No |  |
| `assetTypeDisplayName` | `string` | No |  |
| `assetIsWearable` | `boolean` | No |  |
| `sellerName` | `string` | No |  |
| `transactionVerb` | `string` | No |  |
| `isMultiPrivateSale` | `boolean` | No |  |
| `premiumPricing` | `Roblox.Economy.Api.PremiumPricingModel` | No |  |

### Roblox.Catalog.Api.TopicRequestModel

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `items` | `Roblox.MarketplaceTopicDiscovery.TopicDiscoveryService.V1Beta1.AvatarItem[]` | No |  |
| `selectTopics` | `string[]` | No |  |
| `inputQuery` | `string` | No |  |
| `maxResult` | `integer` | No | Maximum number of topic results returned from the server. |
| `genderType` | `1 \| 2 \| 3` | No | ['Unknown' = 1, 'Male' = 2, 'Female' = 3] |

### Roblox.Catalog.Api.TopicResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `topics` | `Roblox.Catalog.Api.TopicModel[]` | No |  |
| `queries` | `string[]` | No |  |
| `error` | `Roblox.MarketplaceTopicDiscovery.TopicDiscoveryService.V1Beta1.Error` | No |  |

### Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Api.Develop.Models.GroupModel_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `data` | `Roblox.Api.Develop.Models.GroupModel[]` | No |  |

### Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Catalog.Api.OwnedBundleModel_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `previousPageCursor` | `string` | No |  |
| `nextPageCursor` | `string` | No |  |
| `data` | `Roblox.Catalog.Api.OwnedBundleModel[]` | No |  |

### Roblox.Api.Avatar.Models.AssetIdListModel

A model that contains a list of asset ids

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `assetIds` | `integer[]` | No | The asset ids |

### Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Inventory.Api.Models.IItemModel_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `previousPageCursor` | `string` | No |  |
| `nextPageCursor` | `string` | No |  |
| `data` | `Roblox.Inventory.Api.Models.IItemModel[]` | No |  |

### Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Inventory.Api.V2.AssetOwnerResponse_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `previousPageCursor` | `string` | No |  |
| `nextPageCursor` | `string` | No |  |
| `data` | `Roblox.Inventory.Api.V2.AssetOwnerResponse[]` | No |  |

### Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Api.Develop.AssetVersion_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `previousPageCursor` | `string` | No |  |
| `nextPageCursor` | `string` | No |  |
| `data` | `Roblox.Api.Develop.AssetVersion[]` | No |  |

### Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Inventory.Api.V2.CollectibleItemOwnerResponse_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `previousPageCursor` | `string` | No |  |
| `nextPageCursor` | `string` | No |  |
| `data` | `Roblox.Inventory.Api.V2.CollectibleItemOwnerResponse[]` | No |  |

### Roblox.Catalog.Api.CatalogSearchPageResponse_Roblox.Catalog.Api.CatalogSearchDetailedResponseItemV2_

ApiPageResponse for catalog search.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `keyword` | `string` | No | Keyword used for search query. |
| `elasticsearchDebugInfo` | `Roblox.Catalog.Api.ElasticsearchDebugInfo` | No |  |
| `previousPageCursor` | `string` | No |  |
| `nextPageCursor` | `string` | No |  |
| `data` | `Roblox.Catalog.Api.CatalogSearchDetailedResponseItemV2[]` | No |  |

### Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Inventory.Api.V2.UserAssetItemModelV2_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `previousPageCursor` | `string` | No |  |
| `nextPageCursor` | `string` | No |  |
| `data` | `Roblox.Inventory.Api.V2.UserAssetItemModelV2[]` | No |  |

### Roblox2.Assetdelivery.V3.V3BatchRequest

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `assets` | `Roblox2.Assetdelivery.V3.AssetRequestItem[]` | Yes |  |

### Roblox2.Assetdelivery.V3.V3PrewarmRequest

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `target` | `Roblox2.Assetdelivery.V3.PrewarmTarget` | Yes |  |

### Roblox2.Assetdelivery.V3.PrewarmTarget

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `place` | `Roblox2.Assetdelivery.V3.PrewarmPlaceTarget` | No |  |

### Roblox2.Assetdelivery.V3.PrewarmPlaceTarget

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `placeId` | `integer` | No |  |

### Roblox2.Assetdelivery.V3.AssetRequestItem

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `requestId` | `string` | Yes |  |
| `asset` | `Roblox2.Assetdelivery.V3.AssetIdentifier` | Yes |  |
| `version` | `Roblox2.Assetdelivery.V3.VersionStrategy` | Yes |  |
| `assetType` | `string` | No |  |
| `representation` | `Roblox2.Assetdelivery.V3.RepresentationRequest` | No |  |
| `skipSigningScripts` | `boolean` | No |  |
| `permissionContext` | `string` | No |  |
| `options` | `Roblox2.Assetdelivery.V3.Options` | No |  |
| `insertContext` | `Roblox2.Assetdelivery.V3.InsertContext` | No |  |
| `assetResolutionMode` | `string` | No |  |
| `dataModelMode` | `0 \| 1 \| 2` | No |  |
| `usageContext` | `string` | No |  |
| `accessContext` | `any` | No |  |
| `thumbnailModerationAccessKey` | `string` | No |  |
| `placeId` | `integer` | No |  |
| `modulePlaceId` | `integer` | No |  |
| `xcachesplit` | `integer` | No |  |

### Roblox2.Assetdelivery.V3.AssetIdentifier

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `assetId` | `integer` | No |  |
| `hash` | `string` | No |  |
| `assetVersionId` | `integer` | No |  |
| `assetName` | `Roblox2.Assetdelivery.V3.AssetNameIdentifier` | No |  |

### Roblox2.Assetdelivery.V3.VersionStrategy

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `stable` | `Roblox2.Assetdelivery.V3.StableVersion` | No |  |
| `pinned` | `Roblox2.Assetdelivery.V3.PinnedVersion` | No |  |
| `latest` | `Roblox2.Assetdelivery.V3.LatestVersion` | No |  |

### Roblox2.Assetdelivery.V3.RepresentationRequest

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `priorityList` | `Roblox2.Assetdelivery.V3.RepresentationItem[]` | No |  |
| `doNotFallbackToBaseline` | `boolean` | No |  |

### Roblox2.Assetdelivery.V3.Options

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `metadata` | `any` | No |  |

### Roblox2.Assetdelivery.V3.InsertContext

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `scriptInsert` | `boolean` | No |  |
| `clientInsert` | `boolean` | No |  |
| `serverPlaceId` | `integer` | No |  |

### Roblox2.Assetdelivery.V3.RepresentationItem

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `format` | `string` | No |  |
| `majorVersion` | `string` | No |  |
| `fidelity` | `string` | No |  |

### Roblox2.Assetdelivery.V3.PinnedVersion

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `versionNumber` | `integer` | No |  |

### Roblox2.Assetdelivery.V3.AssetNameIdentifier

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `name` | `string` | Yes |  |
| `universeId` | `integer` | No |  |

### Roblox.Inventory.Api.V2.UserAssetItemModelV2

The user asset item model for V2 controllers.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `assetId` | `integer` | No | The asset id of the user asset. |
| `name` | `string` | No | The name of asset with id Roblox.Inventory.Api.V2.UserAssetItemModelV2.AssetId. |
| `assetType` | `integer enum (90 values)` | No | The asset type id of asset with id Roblox.Inventory.Api.V2.UserAssetItemModelV2.AssetId. ['Image' = 1, 'TShirt' = 2, 'Audio' = 3, 'Mesh' = 4, 'Lua' = 5, 'HTML' = 6, 'Text' = 7, 'Hat' = 8, 'Place' = 9, 'Model' = 10, 'Shirt' = 11, 'Pants' = 12, 'Decal' = 13, 'Avatar' = 16, 'Head' = 17, 'Face' = 18, 'Gear' = 19, 'Badge' = 21, 'GroupEmblem' = 22, 'Animation' = 24, 'Arms' = 25, 'Legs' = 26, 'Torso' = 27, 'RightArm' = 28, 'LeftArm' = 29, 'LeftLeg' = 30, 'RightLeg' = 31, 'Package' = 32, 'YouTubeVideo' = 33, 'GamePass' = 34, 'App' = 35, 'Code' = 37, 'Plugin' = 38, 'SolidModel' = 39, 'MeshPart' = 40, 'HairAccessory' = 41, 'FaceAccessory' = 42, 'NeckAccessory' = 43, 'ShoulderAccessory' = 44, 'FrontAccessory' = 45, 'BackAccessory' = 46, 'WaistAccessory' = 47, 'ClimbAnimation' = 48, 'DeathAnimation' = 49, 'FallAnimation' = 50, 'IdleAnimation' = 51, 'JumpAnimation' = 52, 'RunAnimation' = 53, 'SwimAnimation' = 54, 'WalkAnimation' = 55, 'PoseAnimation' = 56, 'LocalizationTableManifest' = 59, 'LocalizationTableTranslation' = 60, 'EmoteAnimation' = 61, 'Video' = 62, 'TexturePack' = 63, 'TShirtAccessory' = 64, 'ShirtAccessory' = 65, 'PantsAccessory' = 66, 'JacketAccessory' = 67, 'SweaterAccessory' = 68, 'ShortsAccessory' = 69, 'LeftShoeAccessory' = 70, 'RightShoeAccessory' = 71, 'DressSkirtAccessory' = 72, 'FontFamily' = 73, 'FontFace' = 74, 'MeshHiddenSurfaceRemoval' = 75, 'EyebrowAccessory' = 76, 'EyelashAccessory' = 77, 'MoodAnimation' = 78, 'DynamicHead' = 79, 'CodeSnippet' = 80, 'AdsVideo' = 81, 'OtaUpdate' = 82, 'Screenshot' = 83, 'RuntimePropertySet' = 84, 'StorePreviewVideo' = 85, 'GamePreviewVideo' = 86, 'CreatorExperienceConfig' = 87, 'FaceMakeup' = 88, 'LipMakeup' = 89, 'EyeMakeup' = 90, 'VoxelFragment' = 91, 'AvatarBackground' = 92, 'TextDocument' = 93, 'Post' = 94, 'AnimatedImage' = 95, 'ComputeFunction' = 96, 'AvatarSpawnEffect' = 97] Values: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 16, 17, 18, 19, 21, 22, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97 |
| `created` | `string` | No | The created date time of the user asset. |

### Roblox.Catalog.Api.ElasticsearchDebugInfo

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `elasticsearchQuery` | `string` | No | Gets or sets the nest query that resulted from the operation. |
| `isFromCache` | `boolean` | No | Gets or sets if the results were returned from cache. |
| `indexName` | `string` | No | Gets or sets the index name. |
| `isTerminatedEarly` | `boolean` | No | Gets or sets if the query was Terminated Early. |
| `isForceTerminationEnabledByRequest` | `boolean` | No | Gets or sets if Force Termination was Enabled in the Request. |
| `searchResultDataSource` | `string` | No | Gets or sets the search result data source. |
| `searchResultRelevanceScore` | `string` | No | Gets or sets the search result relevance score. |
| `searchResultEngagementScore` | `string` | No | Gets or sets the search result engagement score. |

### Roblox.Catalog.Api.CatalogSearchDetailedResponseItemV2

This is the beta (non game-engine) version of our hydration model representing asset or bundle in marketplace.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `bundledItems` | `Roblox.Catalog.Api.BundleItemDetailModelV2[]` | No | The System.Collections.Generic.IEnumerable`1 contained in the bundle, serialized if item is a bundle. |
| `taxonomy` | `Roblox.Catalog.Api.TaxonomyModel[]` | No | The taxonomy ids and names for this item. |
| `itemCreatedUtc` | `string` | No | The UTC creation date-time of the asset or bundle. |
| `discountInformation` | `Roblox.Catalog.Api.DiscountInformation` | No |  |
| `license` | `Roblox.Catalog.Api.CollectibleLicense` | No |  |
| `id` | `integer` | No | The Item Id. |
| `itemType` | `1 \| 2` | No | The Roblox.Catalog.Api.CatalogSearchDetailedResponseItem.ItemType item type. ['Asset' = 1, 'Bundle' = 2] |
| `assetType` | `integer enum (91 values)` | No | The Roblox.Platform.Assets.AssetType serialized if item is an asset. Values: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 16, 17, 18, 19, 21, 22, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98 |
| `bundleType` | `1 \| 2 \| 3 \| 4` | No | The Roblox.Platform.Bundles.Core.BundleType serialized if item is a bundle. |
| `isRecolorable` | `boolean` | No | Gets or sets the property whether a bundle is recolorable or not. Not serialized for asset. |
| `name` | `string` | No | The item name. |
| `description` | `string` | No | The item description. |
| `productId` | `integer` | No | The product id of corresponding item. |
| `itemStatus` | `1 \| 2 \| 7 \| 8[]` | No | The System.Collections.Generic.IEnumerable`1 if item has Roblox.Catalog.Api.CatalogItemStatus. |
| `itemRestrictions` | `integer enum (9 values)[]` | No | The System.Collections.Generic.IEnumerable`1 if item has Roblox.Catalog.Api.CatalogItemRestriction. Values: 1, 2, 3, 4, 5, 6, 7, 8, 9 |
| `creatorHasVerifiedBadge` | `boolean` | No | The verified status of a creator. |
| `creatorType` | `0 \| 1 \| 2` | No | The Roblox.Catalog.Api.CatalogSearchDetailedResponseItem.CreatorType of the item's creator. |
| `creatorTargetId` | `integer` | No | The creator id of the item's creator. |
| `creatorName` | `string` | No | The creator name of the item's creator. |
| `price` | `integer` | No | The item's price. |
| `lowestPrice` | `integer` | No | The item's lowest price, only if the item is resellable and there are resellers. |
| `lowestResalePrice` | `integer` | No | The item's lowest resale price, only if the item is resellable and there are resellers, including current user. |
| `priceStatus` | `string` | No | The localized string item status if the item's price should not be displayed. |
| `unitsAvailableForConsumption` | `integer` | No | The number of items in stock, only if the item is resellable and is limitedEdition. |
| `favoriteCount` | `integer` | No | The number of times the item has been favorited. |
| `offSaleDeadline` | `string` | No | When the item will go off sale, if the item has an off deadline. |
| `collectibleItemId` | `string` | No | The item's collectible item id. It is an UUID if a item is collectible type. Otherwise, it is null. |
| `totalQuantity` | `integer` | No | The collectible or limited-unique item's total quantity of unique instances. |
| `saleLocationType` | `integer enum (8 values)` | No | The sale location type of the item. ['NotApplicable' = 0, 'ShopOnly' = 1, 'MyExperiencesOnly' = 2, 'ShopAndMyExperiences' = 3, 'ExperiencesById' = 4, 'ShopAndAllExperiences' = 5, 'ExperiencesDevApiOnly' = 6, 'ShopAndExperiencesById' = 7] Values: 0, 1, 2, 3, 4, 5, 6, 7 |
| `hasResellers` | `boolean` | No | An indicator if the item has resellers or not (null if not resellable). |
| `isOffSale` | `boolean` | No | An indicator if the item is off sale or not. |
| `quantityLimitPerUser` | `integer` | No | Quantity limit for how many instances a user can buy. |
| `supportsHeadShapes` | `boolean` | No | Whether the item supports head shapes. |
| `timedOptions` | `Roblox.Catalog.Api.TimedOption[]` | No | The timed options for the item. |

### Roblox.Catalog.Api.BundleItemDetailModelV2

The is the beta (non game-engine) version of BundleItemDetailModel for internal consumption on Roblox web and universal-app.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `owned` | `boolean` | No |  |
| `id` | `integer` | No |  |
| `name` | `string` | No |  |
| `type` | `string` | No |  |
| `supportsHeadShapes` | `boolean` | No | Whether the bundle item supports head shapes. |
| `assetType` | `integer` | No | The asset type of the bundle item, if it's an asset. |

### Roblox.Catalog.Api.TaxonomyModel

public api model coaslescing taxonomy information for a single item.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `taxonomyId` | `string` | No | The id value to pass into taxonomy field in SearchV2 catalog-api. |
| `taxonomyName` | `string` | No | The localized human readable name of the category. |

### Roblox.Catalog.Api.DiscountInformation

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `originalPrice` | `integer` | No |  |
| `totalDiscountPercentage` | `number` | No |  |
| `totalDiscountAmount` | `integer` | No |  |
| `discounts` | `Roblox.Catalog.Api.Discount[]` | No |  |

### Roblox.Catalog.Api.CollectibleLicense

A model representing the license attached to a collectible, linked via the collectibleItemId.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `string` | No |  |
| `licenseType` | `0 \| 1 \| 2` | No | The type of license attached to a collectible. ['Invalid' = 0, 'ThirdParty' = 1, 'FirstParty' = 2] |
| `licenseDisplayName` | `string` | No |  |

### Roblox.Catalog.Api.TimedOption

Defines a timed option for a catalog item.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `days` | `integer` | No | The days for the timed option. |
| `price` | `integer` | No | The price for the timed option. |
| `discountInformation` | `Roblox.Catalog.Api.DiscountInformation` | No |  |
| `selected` | `boolean` | No | To indicate if this option is selected by the client. |

### Roblox.Catalog.Api.Discount

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `robuxDiscountAmount` | `integer` | No |  |
| `robuxDiscountPercentage` | `number` | No |  |
| `discountCampaign` | `string` | No |  |
| `localizedDiscountAttribution` | `string` | No |  |

### Roblox.Inventory.Api.V2.CollectibleItemOwnerResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `collectibleItemInstanceId` | `string` | No |  |
| `serialNumber` | `integer` | No |  |
| `owner` | `Roblox.Web.Responses.RelatedEntityTypeResponse_Roblox.Users.Client.AssociatedEntityType_` | No |  |

### Roblox.Web.Responses.RelatedEntityTypeResponse_Roblox.Users.Client.AssociatedEntityType_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No |  |
| `type` | `1 \| 2` | No | ['User' = 1, 'Group' = 2] |
| `name` | `string` | No |  |

### Roblox.Api.Develop.AssetVersion

Model of an asset version.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `Id` | `integer` | No | The VersionID of the asset version. |
| `assetId` | `integer` | No | The ID of the asset. |
| `assetVersionNumber` | `integer` | No | The version number. |
| `creatorType` | `string` | No | Type of the asset version creator. |
| `creatorTargetId` | `integer` | No | ID of the asset version creator. |
| `creatingUniverseId` | `integer` | No | ID of the universe this asset version was created in. |
| `created` | `string` | No | The created date of this asset version. |
| `isEqualToCurrentPublishedVersion` | `boolean` | No | Indicates if this version is same to current published version. This property is available on /v1/{assetId}/published-versions and /v1/{assetId}/version/{versionNumber}. |
| `isPublished` | `boolean` | No | Indicates if this version is / was published. This property is available on /v1/{assetId}/saved-versions. This should be true for all assets coming from GetAssetPublishedVersionsByAssetId |

### Roblox.Inventory.Api.V2.AssetOwnerResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No |  |
| `collectibleItemInstanceId` | `string` | No |  |
| `serialNumber` | `integer` | No |  |
| `owner` | `Roblox.Web.Responses.RelatedEntityTypeResponse_Roblox.Users.Client.AssociatedEntityType_` | No |  |
| `created` | `string` | No |  |
| `updated` | `string` | No |  |

### Roblox.Inventory.Api.Models.IItemModel

Model representing an inventory item

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No | The ID of the item |
| `name` | `string` | No | The name of the item |
| `type` | `0 \| 1 \| 2 \| 3 \| 4` | No | The type of the item ['Asset' = 0, 'GamePass' = 1, 'Badge' = 2, 'Bundle' = 3, 'Avatar' = 4] |
| `instanceId` | `integer` | No | The instance id of the item if applicable |

### Roblox.Catalog.Api.OwnedBundleModel

A model to represent owned bundles.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No |  |
| `name` | `string` | No |  |
| `bundleType` | `string` | No |  |
| `creator` | `Roblox.Catalog.Api.BundleCreatorModel` | No |  |

### Roblox.Catalog.Api.BundleCreatorModel

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No |  |
| `name` | `string` | No |  |
| `type` | `string` | No |  |
| `hasVerifiedBadge` | `boolean` | No |  |

### Roblox.Api.Develop.Models.GroupModel

A model containing information about a group

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No | The Roblox.Platform.Groups.IGroup's Id. |
| `name` | `string` | No | The Roblox.Platform.Groups.IGroup's name. |

### Roblox.Catalog.Api.TopicModel

Response model for avatar topics.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `displayName` | `string` | No | The display topic name. |
| `originalTopicName` | `string` | No | The original topic name stored in the table. |

### Roblox.MarketplaceTopicDiscovery.TopicDiscoveryService.V1Beta1.Error

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `Message` | `string` | No |  |
| `Code` | `integer` | No |  |

### Roblox.MarketplaceTopicDiscovery.TopicDiscoveryService.V1Beta1.AvatarItem

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `TargetId` | `integer` | No |  |
| `ItemType` | `0 \| 1 \| 2` | No | ['Invalid' = 0, 'Asset' = 1, 'Bundle' = 2] |

### Roblox.Economy.Api.PremiumPricingModel

Defines the Premium pricing for a product

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `premiumDiscountPercentage` | `integer` | No | The Premium discount percentage for a product |
| `premiumPriceInRobux` | `integer` | No | The Premium price for a product |

### Roblox.Web.Responses.Plugins.PluginResponse

Represents information about a plugin.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No | The plugin Id. |
| `name` | `string` | No | The plugin name. |
| `description` | `string` | No | The plugin description. |
| `commentsEnabled` | `boolean` | No | Whether or not the plugin allows comments to be posted. |
| `versionId` | `integer` | No | plugin version id |
| `created` | `string` | No | The time the plugin was created. |
| `updated` | `string` | No | The last time the plugin was updated. |

### Roblox.ItemConfiguration.Api.Models.Response.GroupInfo

High level group information.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No | Group id. |
| `name` | `string` | No | Group name. |

### Roblox.ItemConfiguration.Api.Models.Response.PublishingFeeInfo

A publishing fee returned with the price floor.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `publishingFeeInRobux` | `integer` | No | The publishing fee in Robux. For Roblox.ItemConfiguration.Api.PublishingFeeType.PayPerInstance, this is the fee for each unit. |
| `publishingFeeType` | `0 \| 1 \| 2` | No | Whether the fee is charged once or for each unit. ['Invalid' = 0, 'PayPerInstance' = 1, 'PayInTotal' = 2] |
| `displayName` | `string` | No | The user-facing name of the publishing fee. |

### Roblox.ItemConfiguration.Api.Models.Response.CategoryNode

A single node in the category hierarchy returned by Roblox.ItemConfiguration.Api.Models.Response.GetCategoriesResponse.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `webStableId` | `string` | No | The public, tree-stable identifier for the node. Callers pass this back as the category filter; it is expanded to leaf uuids server-side. |
| `id` | `string` | No | The internal taxonomy node identifier (Synapse branch id or leaf label id). |
| `name` | `string` | No | The canonical (English) display name of the category. |
| `isPublishable` | `boolean` | No | Whether the category is publishable by UGC creators. |
| `assetTypeIds` | `integer[]` | No | Default asset type ids backing this node. |
| `bundleTypeIds` | `integer[]` | No | Default bundle type ids backing this node. |
| `children` | `Roblox.ItemConfiguration.Api.Models.Response.CategoryNode[]` | No | Child category nodes; empty for leaves. |

### Roblox.ItemConfiguration.Api.MarketplaceItem

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `string` | No | The id of the item. |
| `marketplaceItemDetails` | `Roblox.ItemConfiguration.Api.MarketplaceItemDetails` | No |  |
| `createdTime` | `string` | No | The created time. |
| `name` | `string` | No | The name of the item. |
| `description` | `string` | No | The description of the item. |
| `creator` | `Roblox.AvatarMarketplacePublishing.Shared.V1Beta1.Creator` | No |  |
| `moderationStatus` | `0 \| 1 \| 2 \| 3 \| 4` | No | The moderation status of the item. ['Invalid' = 0, 'Pending' = 1, 'Moderated' = 2, 'Approved' = 3, 'RequiresIntervention' = 4] |
| `isUpdating` | `boolean` | No | Whether the item currently has an in-flight Catalog Asset Update (a submitted update whose staging content is still being created / validated / moderated). The creator dashboard renders such an item as "pending" — the same treatment as an item still under moderation review. |
| `price` | `integer` | No | The price of the item. If price = 0 => free, if price = null => unset. |
| `saleStatus` | `0 \| 1 \| 2` | No | The sale status of the item. ['OnSale' = 0, 'OffSale' = 1, 'Free' = 2] |
| `collectibleItemType` | `0 \| 1 \| 2` | No | The collectible item type. If null => item has not been published into collectible system. ['Invalid' = 0, 'Limited' = 1, 'NonLimited' = 2] |
| `creationUniverseId` | `integer` | No | The creation universe id. Used for IEC items. |
| `delistingStatus` | `Roblox.AvatarMarketplacePublishing.AvatarMarketplacePublishingGateway.V1Beta1.ItemDelistingStatus` | No |  |
| `scheduledRelease` | `Roblox.Collectibles.Shared.V1.ScheduledRelease` | No |  |
| `cannotBePublishedReason` | `integer enum (7 values)` | No | The cannot be published reason. If Invalid, the item CAN be published. ['Invalid' = 0, 'None' = 1, 'Iec' = 2, 'AssetPartOfBundle' = 3, 'Delisted' = 4, 'RealWorldCommerce' = 5, 'AiGenerated' = 6] Values: 0, 1, 2, 3, 4, 5, 6 |
| `dynamicPriceConfiguration` | `Roblox.AvatarMarketplacePublishing.AvatarMarketplacePublishingGateway.V1Beta1.DynamicPriceConfiguration` | No |  |
| `isRentalOptIn` | `boolean` | No | Whether the item is opted into rental. |
| `rentalOptions` | `Roblox.ItemConfiguration.Api.RentalOption[]` | No | All rental options for the collectible item. Empty if the item is not opted in for rental. |
| `taxonomyDetails` | `Roblox.ItemConfiguration.Api.Models.MarketplaceItem.TaxonomyDetails` | No |  |
| `isHD` | `boolean` | No | Whether the item is HD. |
| `discoverabilityDetails` | `Roblox.ItemConfiguration.Api.Models.MarketplaceItem.DiscoverabilityDetails` | No |  |
| `isEmissive` | `boolean` | No | Whether the item has emissive properties. |
| `isCollectible` | `boolean` | No | Whether the item is a collectible (i.e. it has been published into the collectible system). |
| `saleLocation` | `Roblox.ItemConfiguration.Api.Models.MarketplaceItem.SaleLocation` | No |  |
| `collectibleDetails` | `Roblox.ItemConfiguration.Api.Models.MarketplaceItem.CollectibleDetails` | No |  |

### Roblox.ItemConfiguration.Api.MarketplaceItemDetails

The marketplace item details.
Only one of the AssetDetails and BundleDetails will be set.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `assetDetails` | `Roblox.ItemConfiguration.Api.AssetDetails` | No |  |
| `bundleDetails` | `Roblox.ItemConfiguration.Api.BundleDetails` | No |  |

### Roblox.AvatarMarketplacePublishing.Shared.V1Beta1.Creator

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `User` | `Roblox.AvatarMarketplacePublishing.Shared.V1Beta1.Creator.Types.User` | No |  |
| `Group` | `Roblox.AvatarMarketplacePublishing.Shared.V1Beta1.Creator.Types.Group` | No |  |
| `KindCase` | `0 \| 1 \| 2` | No | ['None' = 0, 'User' = 1, 'Group' = 2] |

### Roblox.AvatarMarketplacePublishing.AvatarMarketplacePublishingGateway.V1Beta1.ItemDelistingStatus

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `Target` | `Roblox.AvatarMarketplacePublishing.AvatarMarketplacePublishingGateway.V1Beta1.Target` | No |  |
| `Status` | `0 \| 1 \| 2` | No | ['Invalid' = 0, 'Delisted' = 1, 'NotDelisted' = 2] |

### Roblox.Collectibles.Shared.V1.ScheduledRelease

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `OnSaleTime` | `Google.Protobuf.WellKnownTypes.Timestamp` | No |  |
| `OffSaleTime` | `Google.Protobuf.WellKnownTypes.Timestamp` | No |  |

### Roblox.AvatarMarketplacePublishing.AvatarMarketplacePublishingGateway.V1Beta1.DynamicPriceConfiguration

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `MinimumPrice` | `integer` | No |  |
| `PriceOffset` | `integer` | No |  |
| `IsOptOutRegionalPricing` | `boolean` | No |  |

### Roblox.ItemConfiguration.Api.RentalOption

Rental options for a collectible item.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `rentalDays` | `integer` | No | The duration of the rental in days. null is the permanent purchase price. |
| `priceInRobux` | `integer` | No | The price of the rental in Robux. |

### Roblox.ItemConfiguration.Api.Models.MarketplaceItem.TaxonomyDetails

The taxonomy-related details of an item.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `dpfTaxonomyName` | `string` | No |  |
| `dpfTaxonomyId` | `string` | No |  |
| `dpfTaxonomyIsDefaultTaxonomy` | `boolean` | No |  |

### Roblox.ItemConfiguration.Api.Models.MarketplaceItem.DiscoverabilityDetails

The discoverability-related details of an item.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `isDiscoverabilityReduced` | `boolean` | No |  |
| `isCoreContentGated` | `boolean` | No |  |

### Roblox.ItemConfiguration.Api.Models.MarketplaceItem.SaleLocation

The collectible sale location.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `saleLocationType` | `0 \| 1 \| 2 \| 3 \| 4` | No | The sale location type. ['SALE_LOCATION_TYPE_INVALID' = 0, 'SALE_LOCATION_TYPE_SHOP_AND_ALL_EXPERIENCES' = 1, 'SALE_LOCATION_EXPERIENCES_AND_DEV_API_ONLY' = 2, 'SALE_LOCATION_TYPE_SHOP_ONLY' = 3, 'SALE_LOCATION_TYPE_SHOP_AND_EXPERIENCES_BY_ID' = 4] |
| `universeIds` | `integer[]` | No | The universe ids the collectible item may be sold in. |

### Roblox.ItemConfiguration.Api.Models.MarketplaceItem.CollectibleDetails

Details specific to a collectible item. Set only when the item is a collectible.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `collectibleItemId` | `string` | No | The collectible item id. |
| `quantityLimitPerUser` | `integer` | No | The max number of instances of the collectible item a user can own. Null if there is no limit. |
| `totalRestockedQuantity` | `integer` | No | The total quantity that has been restocked for the collectible item. |
| `lastRestockedTime` | `string` | No | The time the collectible item was last restocked. |
| `isResellable` | `boolean` | No | Whether the collectible item is resellable. |
| `totalQuantity` | `integer` | No | The total quantity available for the collectible item. |
| `licensingInfo` | `Roblox.ItemConfiguration.Api.Models.MarketplaceItem.LicensingInfo` | No |  |

### Roblox.ItemConfiguration.Api.Models.MarketplaceItem.LicensingInfo

Licensing info for the collectible item.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `state` | `0 \| 1 \| 2 \| 3 \| 4` | No | The licensing state. See Roblox.ItemConfiguration.Api.Models.MarketplaceItem.LicensingState. ['Invalid' = 0, 'NotLicensed' = 1, 'Licensed' = 2, 'Expired' = 3, 'Terminated' = 4] |
| `licenseId` | `string` | No | The id of the license backing the agreement. Empty unless Roblox.ItemConfiguration.Api.Models.MarketplaceItem.LicensingInfo.State is Roblox.ItemConfiguration.Api.Models.MarketplaceItem.LicensingState.Licensed, Roblox.ItemConfiguration.Api.Models.MarketplaceItem.LicensingState.Expired, or Roblox.ItemConfiguration.Api.Models.MarketplaceItem.LicensingState.Terminated. |
| `agreementId` | `string` | No | The id of the agreement backing the license. Empty unless Roblox.ItemConfiguration.Api.Models.MarketplaceItem.LicensingInfo.State is Roblox.ItemConfiguration.Api.Models.MarketplaceItem.LicensingState.Licensed, Roblox.ItemConfiguration.Api.Models.MarketplaceItem.LicensingState.Expired, or Roblox.ItemConfiguration.Api.Models.MarketplaceItem.LicensingState.Terminated. |

### Google.Protobuf.WellKnownTypes.Timestamp

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `Seconds` | `integer` | No |  |
| `Nanos` | `integer` | No |  |

### Roblox.AvatarMarketplacePublishing.AvatarMarketplacePublishingGateway.V1Beta1.Target

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `TargetType` | `0 \| 1 \| 2 \| 3 \| 4` | No | ['Invalid' = 0, 'Asset' = 1, 'Bundle' = 2, 'AvatarMarketplaceToken' = 3, 'Look' = 4] |
| `Id` | `string` | No |  |

### Roblox.AvatarMarketplacePublishing.Shared.V1Beta1.Creator.Types.User

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `UserId` | `integer` | No |  |

### Roblox.AvatarMarketplacePublishing.Shared.V1Beta1.Creator.Types.Group

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `GroupId` | `integer` | No |  |

### Roblox.ItemConfiguration.Api.AssetDetails

The asset details.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `assetType` | `integer enum (92 values)` | No | The asset type. ['Invalid' = 0, 'Image' = 1, 'Tshirt' = 2, 'Audio' = 3, 'Mesh' = 4, 'Lua' = 5, 'Html' = 6, 'Text' = 7, 'Hat' = 8, 'Place' = 9, 'Model' = 10, 'Shirt' = 11, 'Pants' = 12, 'Decal' = 13, 'Avatar' = 16, 'Head' = 17, 'Face' = 18, 'Gear' = 19, 'Badge' = 21, 'GroupEmblem' = 22, 'Animation' = 24, 'Arms' = 25, 'Legs' = 26, 'Torso' = 27, 'RightArm' = 28, 'LeftArm' = 29, 'LeftLeg' = 30, 'RightLeg' = 31, 'Package' = 32, 'YoutubeVideo' = 33, 'GamePass' = 34, 'App' = 35, 'Code' = 37, 'Plugin' = 38, 'SolidModel' = 39, 'MeshPart' = 40, 'HairAccessory' = 41, 'FaceAccessory' = 42, 'NeckAccessory' = 43, 'ShoulderAccessory' = 44, 'FrontAccessory' = 45, 'BackAccessory' = 46, 'WaistAccessory' = 47, 'ClimbAnimation' = 48, 'DeathAnimation' = 49, 'FallAnimation' = 50, 'IdleAnimation' = 51, 'JumpAnimation' = 52, 'RunAnimation' = 53, 'SwimAnimation' = 54, 'WalkAnimation' = 55, 'PoseAnimation' = 56, 'LocalizationTableManifest' = 59, 'LocalizationTableTranslation' = 60, 'EmoteAnimation' = 61, 'Video' = 62, 'TexturePack' = 63, 'TshirtAccessory' = 64, 'ShirtAccessory' = 65, 'PantsAccessory' = 66, 'JacketAccessory' = 67, 'SweaterAccessory' = 68, 'ShortsAccessory' = 69, 'LeftShoeAccessory' = 70, 'RightShoeAccessory' = 71, 'DressSkirtAccessory' = 72, 'FontFamily' = 73, 'FontFace' = 74, 'MeshHiddenSurfaceRemoval' = 75, 'EyebrowAccessory' = 76, 'EyelashAccessory' = 77, 'MoodAnimation' = 78, 'DynamicHead' = 79, 'CodeSnippet' = 80, 'AdsVideo' = 81, 'OtaUpdate' = 82, 'Screenshot' = 83, 'RuntimePropertySet' = 84, 'StorePreviewVideo' = 85, 'GamePreviewVideo' = 86, 'CreatorExperienceConfig' = 87, 'FaceMakeup' = 88, 'LipMakeup' = 89, 'EyeMakeup' = 90, 'VoxelFragment' = 91, 'AvatarBackground' = 92, 'TextDocument' = 93, 'Post' = 94, 'AnimatedImage' = 95, 'ComputeFunction' = 96, 'AvatarSpawnEffect' = 97, 'Voice' = 98] Values: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 16, 17, 18, 19, 21, 22, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98 |

### Roblox.ItemConfiguration.Api.BundleDetails

The bundle details.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `bundleType` | `0 \| 1 \| 2 \| 3 \| 4` | No | The bundle type. ['Invalid' = 0, 'Body' = 1, 'DynamicHead' = 2, 'Shoes' = 3, 'AvatarAnimations' = 4] |

### Roblox.ItemConfiguration.Api.Models.Folder.FolderItem

Represents an identifier for an item in a folder.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `string` | No | The unique identifier for the item. |
| `itemType` | `Unknown \| Asset \| Bundle \| IECToken \| Folder` | No | The type of the item to be added to the folder. ['Unknown' = 0, 'Asset' = 1, 'Bundle' = 2, 'IECToken' = 3, 'Folder' = 4] |

### Roblox.ItemConfiguration.Api.Models.Folder.FolderItemDetails

Represents an item in a folder that can be either a MarketplaceItem or a Folder.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `string` | No | The unique identifier for the item. |
| `marketplaceItem` | `Roblox.ItemConfiguration.Api.MarketplaceItem` | No |  |
| `folder` | `Roblox.ItemConfiguration.Api.Models.Folder.Folder` | No |  |

### Roblox.Catalog.Api.CatalogSearchDetailedResponseItem

Game-engine version of fully hydrated asset or bundle in catalog marketplace.
Documented here: https://create.roblox.com/docs/reference/engine/classes/AvatarEditorService#SearchCatalog.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No | The Item Id. |
| `itemType` | `1 \| 2` | No | The Roblox.Catalog.Api.CatalogSearchDetailedResponseItem.ItemType item type. ['Asset' = 1, 'Bundle' = 2] |
| `assetType` | `integer enum (91 values)` | No | The Roblox.Platform.Assets.AssetType serialized if item is an asset. Values: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 16, 17, 18, 19, 21, 22, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98 |
| `bundleType` | `1 \| 2 \| 3 \| 4` | No | The Roblox.Platform.Bundles.Core.BundleType serialized if item is a bundle. |
| `isRecolorable` | `boolean` | No | Gets or sets the property whether a bundle is recolorable or not. Not serialized for asset. |
| `name` | `string` | No | The item name. |
| `description` | `string` | No | The item description. |
| `productId` | `integer` | No | The product id of corresponding item. |
| `bundledItems` | `Roblox.Catalog.Api.BundleItemDetailModel[]` | No | The System.Collections.Generic.IEnumerable`1 contained in the bundle, serialized if item is a bundle. |
| `itemStatus` | `1 \| 2 \| 7 \| 8[]` | No | The System.Collections.Generic.IEnumerable`1 if item has Roblox.Catalog.Api.CatalogItemStatus. |
| `itemRestrictions` | `integer enum (9 values)[]` | No | The System.Collections.Generic.IEnumerable`1 if item has Roblox.Catalog.Api.CatalogItemRestriction. Values: 1, 2, 3, 4, 5, 6, 7, 8, 9 |
| `creatorHasVerifiedBadge` | `boolean` | No | The verified status of a creator. |
| `creatorType` | `0 \| 1 \| 2` | No | The Roblox.Catalog.Api.CatalogSearchDetailedResponseItem.CreatorType of the item's creator. |
| `creatorTargetId` | `integer` | No | The creator id of the item's creator. |
| `creatorName` | `string` | No | The creator name of the item's creator. |
| `price` | `integer` | No | The item's price. |
| `lowestPrice` | `integer` | No | The item's lowest price, only if the item is resellable and there are resellers. |
| `lowestResalePrice` | `integer` | No | The item's lowest resale price, only if the item is resellable and there are resellers, including current user. |
| `priceStatus` | `string` | No | The localized string item status if the item's price should not be displayed. |
| `unitsAvailableForConsumption` | `integer` | No | The number of items in stock, only if the item is resellable and is limitedEdition. |
| `favoriteCount` | `integer` | No | The number of times the item has been favorited. |
| `offSaleDeadline` | `string` | No | When the item will go off sale, if the item has an off deadline. |
| `collectibleItemId` | `string` | No | The item's collectible item id. It is an UUID if a item is collectible type. Otherwise, it is null. |
| `totalQuantity` | `integer` | No | The collectible or limited-unique item's total quantity of unique instances. |
| `saleLocationType` | `integer enum (8 values)` | No | The sale location type of the item. ['NotApplicable' = 0, 'ShopOnly' = 1, 'MyExperiencesOnly' = 2, 'ShopAndMyExperiences' = 3, 'ExperiencesById' = 4, 'ShopAndAllExperiences' = 5, 'ExperiencesDevApiOnly' = 6, 'ShopAndExperiencesById' = 7] Values: 0, 1, 2, 3, 4, 5, 6, 7 |
| `hasResellers` | `boolean` | No | An indicator if the item has resellers or not (null if not resellable). |
| `isOffSale` | `boolean` | No | An indicator if the item is off sale or not. |
| `quantityLimitPerUser` | `integer` | No | Quantity limit for how many instances a user can buy. |
| `supportsHeadShapes` | `boolean` | No | Whether the item supports head shapes. |
| `timedOptions` | `Roblox.Catalog.Api.TimedOption[]` | No | The timed options for the item. |

### Roblox.Catalog.Api.BundleItemDetailModel

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `owned` | `boolean` | No |  |
| `id` | `integer` | No |  |
| `name` | `string` | No |  |
| `type` | `string` | No |  |
| `supportsHeadShapes` | `boolean` | No | Whether the bundle item supports head shapes. |
| `assetType` | `integer` | No | The asset type of the bundle item, if it's an asset. |

### Roblox.ItemConfiguration.Api.AssetCreationsResponse

Asset Status response model.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `assetId` | `integer` | No | The asset Id. |
| `name` | `string` | No | The asset name. |

### Roblox.ItemConfiguration.Api.Models.Request.CollectiblesSaleLocationConfigurationModel

Model for Sale Location of Collectible Items.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `saleLocationType` | `0 \| 1 \| 2 \| 3 \| 4` | No | Roblox.ItemConfiguration.Api.Models.Request.CollectiblesSaleLocationConfigurationModel.CollectiblesSaleLocationType. ['SALE_LOCATION_TYPE_INVALID' = 0, 'SALE_LOCATION_TYPE_SHOP_AND_ALL_EXPERIENCES' = 1, 'SALE_LOCATION_EXPERIENCES_AND_DEV_API_ONLY' = 2, 'SALE_LOCATION_TYPE_SHOP_ONLY' = 3, 'SALE_LOCATION_TYPE_SHOP_AND_EXPERIENCES_BY_ID' = 4] |
| `places` | `integer[]` | No | The list of PlaceIds this item is allowed to be sold in. This will be translated to UniverseIds inside the Collectibles Gateway. Requires Roblox.ItemConfiguration.Api.Models.Request.CollectiblesSaleLocationConfigurationModel.CollectiblesSaleLocationType set to ExperiencesById. |

### Roblox.ItemConfiguration.Api.RevenueSplit

Revenue split model.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `creatorSplitPercentage` | `integer` | No | Creator split percentage. |
| `sellerSplitPercentage` | `integer` | No | Seller split percentage. |
| `marketplaceSplitPercentage` | `integer` | No | Marketplace split percentage. |
| `resellerSplitPercentage` | `integer` | No | Reseller split percentage. |
| `ipHolderSplitPercentage` | `integer` | No | IP-holder split percentage. Non-zero only when the request carries a LicenseId with a royalty; rounded up and subtracted from Roblox.ItemConfiguration.Api.RevenueSplit.CreatorSplitPercentage. Defaults to 0. |

### Roblox.ItemConfiguration.Api.Models.MarketplaceItem.RegionalRentalPrice

The rental prices for a specific region.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `countryIso2Code` | `string` | No | The ISO2 code of the country. |
| `rentalPrices` | `Roblox.ItemConfiguration.Api.RentalOption[]` | No | The rental prices available in the region. |

### Roblox.ItemConfiguration.Api.RegionalPrice

Defines a country and its regional price.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `priceInRobux` | `integer` | No | The price in the country in robux. |
| `countryIso2Code` | `string` | No | The ISO2 code of the country. |

### Roblox.ItemConfiguration.Api.ScheduledPublishingSettings

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `scheduledPublishMaxTimeInAdvanceTimeSpan` | `string` | No | The maximum time in the future that a scheduled publish can be set. |
| `scheduledPublishMinDurationTimeSpan` | `string` | No | The minimum time in between scheduled publishes. |

### Roblox.ItemConfiguration.Api.RevenueSplitTier

Tiered revenue split model.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `priceFloorMultiplierLowerBound` | `number` | No | Lower bound of the price floor multiplier for which this tier is applicable. |
| `priceFloorMultiplierUpperBound` | `number` | No | Upper bound of the price floor multiplier for which this tier is applicable. |
| `revenueSplits` | `Roblox.ItemConfiguration.Api.RevenueSplit` | No |  |

### Roblox.ItemConfiguration.Api.Models.Request.Collectibles.BulkUpdateTargets

Targets model for bulk update.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `assetType` | `integer enum (92 values)[]` | No | The asset type for which we should update all items. Values: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 16, 17, 18, 19, 21, 22, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98 |
| `target` | `Roblox.ItemConfiguration.Api.TargetModel[]` | No | A specific target to update. |

### Roblox.ItemConfiguration.Api.Models.Request.Collectibles.BulkUpdatePayload

Payload model for bulk updating items.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `rentalOptIn` | `boolean` | No | The Rental Opt in status to be applied to the items. |

### Roblox.ItemConfiguration.Api.TargetModel

An item target model.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `targetType` | `0 \| 1 \| 2 \| 3` | No | The asset type of the target. ['Asset' = 0, 'Bundle' = 1, 'IecToken' = 2, 'Look' = 3] |
| `targetId` | `string` | No | The id of the target. |

### Roblox.Catalog.Api.SubcategoryModel

Response model for subcategory.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `subcategory` | `integer enum (52 values)` | No | Subcategory type. Values: 0, 1, 2, 3, 4, 5, 9, 10, 12, 13, 14, 15, 19, 20, 21, 22, 23, 24, 25, 26, 27, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66, 67 |
| `taxonomy` | `string` | No | The taxonomy UUID associated with this node. |
| `assetTypeIds` | `integer[]` | No | List of AssetTypeIds corresponding to AssetType enum that this category returns. |
| `bundleTypeIds` | `integer[]` | No | List of bundleTypeIds corresponding to BundleType enum that this category returns. |
| `subcategoryId` | `integer` | No | Subcategory id. |
| `name` | `string` | No | Subcategory name. |
| `shortName` | `string` | No | Subcategory short name. |

### Roblox.Catalog.Api.CatalogItemOrError

A union type representing either a successfully hydrated item or an error.
Exactly one of Roblox.Catalog.Api.CatalogItemOrError.Item or Roblox.Catalog.Api.CatalogItemOrError.HttpStatusCode will be non-null.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No |  |
| `itemType` | `1 \| 2` | No | ['Asset' = 1, 'Bundle' = 2] |
| `item` | `Roblox.Catalog.Api.CatalogSearchDetailedCompleteResponseItem` | No |  |
| `httpStatusCode` | `integer` | No |  |

### Roblox.Catalog.Api.CatalogSearchDetailedCompleteResponseItem

The detailed model for catalog items, complete with economy and ownership info.
This response model is bound in the game-engine here: https://create.roblox.com/docs/reference/engine/classes/AvatarEditorService#GetItemDetails.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `expectedSellerId` | `integer` | No | Id to pass into economy purchase api userID of lowest private seller if resellable Creator AgentID (deprecated) / CreatorTargetId otherwise. |
| `owned` | `boolean` | No | Whether item is owned by user. |
| `isPurchasable` | `boolean` | No | Whether item can be purchased. |
| `creatingUniverseId` | `integer` | No | The universeId that this asset was created in, null if not an in-experience creation. |
| `expirationTime` | `string` | No | If a user purchased timed option item, its expiration time. |
| `id` | `integer` | No | The Item Id. |
| `itemType` | `1 \| 2` | No | The Roblox.Catalog.Api.CatalogSearchDetailedResponseItem.ItemType item type. ['Asset' = 1, 'Bundle' = 2] |
| `assetType` | `integer enum (91 values)` | No | The Roblox.Platform.Assets.AssetType serialized if item is an asset. Values: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 16, 17, 18, 19, 21, 22, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98 |
| `bundleType` | `1 \| 2 \| 3 \| 4` | No | The Roblox.Platform.Bundles.Core.BundleType serialized if item is a bundle. |
| `isRecolorable` | `boolean` | No | Gets or sets the property whether a bundle is recolorable or not. Not serialized for asset. |
| `name` | `string` | No | The item name. |
| `description` | `string` | No | The item description. |
| `productId` | `integer` | No | The product id of corresponding item. |
| `bundledItems` | `Roblox.Catalog.Api.BundleItemDetailModel[]` | No | The System.Collections.Generic.IEnumerable`1 contained in the bundle, serialized if item is a bundle. |
| `itemStatus` | `1 \| 2 \| 7 \| 8[]` | No | The System.Collections.Generic.IEnumerable`1 if item has Roblox.Catalog.Api.CatalogItemStatus. |
| `itemRestrictions` | `integer enum (9 values)[]` | No | The System.Collections.Generic.IEnumerable`1 if item has Roblox.Catalog.Api.CatalogItemRestriction. Values: 1, 2, 3, 4, 5, 6, 7, 8, 9 |
| `creatorHasVerifiedBadge` | `boolean` | No | The verified status of a creator. |
| `creatorType` | `0 \| 1 \| 2` | No | The Roblox.Catalog.Api.CatalogSearchDetailedResponseItem.CreatorType of the item's creator. |
| `creatorTargetId` | `integer` | No | The creator id of the item's creator. |
| `creatorName` | `string` | No | The creator name of the item's creator. |
| `price` | `integer` | No | The item's price. |
| `lowestPrice` | `integer` | No | The item's lowest price, only if the item is resellable and there are resellers. |
| `lowestResalePrice` | `integer` | No | The item's lowest resale price, only if the item is resellable and there are resellers, including current user. |
| `priceStatus` | `string` | No | The localized string item status if the item's price should not be displayed. |
| `unitsAvailableForConsumption` | `integer` | No | The number of items in stock, only if the item is resellable and is limitedEdition. |
| `favoriteCount` | `integer` | No | The number of times the item has been favorited. |
| `offSaleDeadline` | `string` | No | When the item will go off sale, if the item has an off deadline. |
| `collectibleItemId` | `string` | No | The item's collectible item id. It is an UUID if a item is collectible type. Otherwise, it is null. |
| `totalQuantity` | `integer` | No | The collectible or limited-unique item's total quantity of unique instances. |
| `saleLocationType` | `integer enum (8 values)` | No | The sale location type of the item. ['NotApplicable' = 0, 'ShopOnly' = 1, 'MyExperiencesOnly' = 2, 'ShopAndMyExperiences' = 3, 'ExperiencesById' = 4, 'ShopAndAllExperiences' = 5, 'ExperiencesDevApiOnly' = 6, 'ShopAndExperiencesById' = 7] Values: 0, 1, 2, 3, 4, 5, 6, 7 |
| `hasResellers` | `boolean` | No | An indicator if the item has resellers or not (null if not resellable). |
| `isOffSale` | `boolean` | No | An indicator if the item is off sale or not. |
| `quantityLimitPerUser` | `integer` | No | Quantity limit for how many instances a user can buy. |
| `supportsHeadShapes` | `boolean` | No | Whether the item supports head shapes. |
| `timedOptions` | `Roblox.Catalog.Api.TimedOption[]` | No | The timed options for the item. |

### Roblox.ItemConfiguration.Api.Models.Response.Bundle.AllowedBundleTypeSettingsMetadata

Detailed metadata settings for a bundle type.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `allowedAssetTypeSettings` | `object` | No | For this particular bundle type, provides a map containing allowed asset type and its appropriate settings. |
| `marketplaceFeePercentage` | `integer` | No | The marketplace fee for uploading this particular bundle type. |
| `allowedPriceRange` | `Roblox.ItemConfiguration.Api.Models.Response.Bundle.PriceRange` | No |  |

### Roblox.ItemConfiguration.Api.Models.Response.Bundle.AllowedBundleAssetTypeSettingsMetadata

This class encapsulates the settings for each asset type which
is being added to the given bundle.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `minimumQuantity` | `integer` | No | This is the minimum number of this particular asset types that must exist in this bundle. |
| `maximumQuantity` | `integer` | No | This is the maximum number of this particular asset types that must exist in this bundle. |
| `isEligibleForUpload` | `boolean` | No | Boolean flag which indicates whether this particular item is allowed to have a new upload by the user. |
| `allowedFileExtensions` | `string[]` | No | List of string specifying allowed file extensions for upload. |

### Roblox.ItemConfiguration.Api.Models.Response.Bundle.PriceRange

DTO containing price range.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `minimumPrice` | `integer` | No | The minimum allowed price in Robux. |
| `maximumPrice` | `integer` | No | The maximum allowed price in Robux. |

### Roblox.Catalog.Api.BundleProductModel

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No |  |
| `type` | `string` | No |  |
| `isPublicDomain` | `boolean` | No |  |
| `isForSale` | `boolean` | No |  |
| `priceInRobux` | `integer` | No |  |
| `isFree` | `boolean` | No |  |
| `noPriceText` | `string` | No |  |
| `premiumPricing` | `Roblox.Catalog.Api.PremiumPricingModel` | No |  |

### Roblox.Catalog.Api.CollectibleItemDetail

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `collectibleItemId` | `string` | No |  |
| `collectibleProductId` | `string` | No |  |
| `price` | `integer` | No |  |
| `lowestPrice` | `integer` | No |  |
| `lowestResalePrice` | `integer` | No |  |
| `totalQuantity` | `integer` | No |  |
| `unitsAvailable` | `integer` | No |  |
| `saleLocation` | `Roblox.Catalog.Api.SaleLocation` | No |  |
| `hasResellers` | `boolean` | No |  |
| `saleStatus` | `0 \| 1 \| 2 \| 3 \| 4` | No | ['Invalid' = 0, 'Draft' = 1, 'OffSale' = 2, 'OnSale' = 3, 'PendingSale' = 4] |
| `quantityLimitPerUser` | `integer` | No |  |
| `offSaleDeadline` | `string` | No |  |
| `collectibleItemType` | `0 \| 1 \| 2` | No | The type of collectible item, limited or non-limited for now. ['Invalid' = 0, 'Limited' = 1, 'NonLimited' = 2] |
| `lowestAvailableResaleProductId` | `string` | No |  |
| `lowestAvailableResaleItemInstanceId` | `string` | No |  |
| `resaleRestriction` | `0 \| 1 \| 2` | No | ['Invalid' = 0, 'None' = 1, 'Disabled' = 2] |

### Roblox.Catalog.Api.SaleLocation

SaleLocation information for a collectible item (asset or bundle).

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `saleLocationType` | `integer enum (8 values)` | No | Sale location type related for an item detail. ['NotApplicable' = 0, 'ShopOnly' = 1, 'MyExperiencesOnly' = 2, 'ShopAndMyExperiences' = 3, 'ExperiencesById' = 4, 'ShopAndAllExperiences' = 5, 'ExperiencesDevApiOnly' = 6, 'ShopAndExperiencesById' = 7] Values: 0, 1, 2, 3, 4, 5, 6, 7 |
| `saleLocationTypeId` | `integer` | No |  |
| `universeIds` | `integer[]` | No |  |
| `enabledUniverseIds` | `integer[]` | No |  |

### Roblox.Catalog.Api.PremiumPricingModel

Defines the Premium pricing for a catalog item.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `premiumDiscountPercentage` | `integer` | No | The Premium discount percentage for a catalog item. |
| `premiumPriceInRobux` | `integer` | No | The Premium price for a catalog item. |

### Roblox.ItemConfiguration.Api.Models.Bundle.BodyScale

The body scale of the bundle.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `height` | `number` | No | Determines by what factor the height (top-to-bottom distance) is scaled. Range 0.9-1.05. |
| `width` | `number` | No | Determines by what factor the width (left-to-right distance) is scaled. Range: 0.7-1.0. |
| `head` | `number` | No | Determines by what factor the Head is scaled. Range 0.95-1.0. |
| `bodyType` | `number` | No | Determines by which the shape of a Humanoid rig is interpolated. Range 0.0-1.0. |
| `proportion` | `number` | No | Determines how wide (0) or narrow (1) a Humanoid rig. Range 0.0-1.0. |

### Roblox.ItemConfiguration.Api.Models.Bundle.BodyColorSet

The body color set of the associated Outfit for the body.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `headColor3` | `string` | No | The head color of the avatar. |
| `torsoColor3` | `string` | No | The torso color of the avatar. |
| `leftArmColor3` | `string` | No | The left arm color of the avatar. |
| `rightArmColor3` | `string` | No | The right arm color of the avatar. |
| `leftLegColor3` | `string` | No | The left leg color of the avatar. |
| `rightLegColor3` | `string` | No | The right leg color of the avatar. |

### Roblox.Economy.Api.ChartDataPointResponse

Chart data point.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `value` | `integer` | No | The value of the data point. |
| `date` | `string` | No | The date associated with the data point. |

### Roblox.Api.Develop.Models.Response.AssetVotingModel

Asset voting information

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `assetId` | `integer` | No | The !:IAsset's id. |
| `hasUserVoted` | `boolean` | No | Whether the user has voted on this !:IAsset. |
| `canUserVote` | `boolean` | No | Whether the user can vote on this !:IAsset. |
| `shouldShowVotes` | `boolean` | No | Whether votes should be shown. |
| `upVotes` | `integer` | No | The number of up votes. |
| `downVotes` | `integer` | No | The number of down votes. |
| `reasonForNotAbleToVote` | `string` | No | The reason this !:IAsset cannot be voted on. |

### Roblox.ItemConfiguration.Api.AgentModel

The agent model.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `type` | `1 \| 2` | No | ['User' = 1, 'Group' = 2] |
| `id` | `integer` | No |  |
| `name` | `string` | No |  |

### Roblox.Publish.Api.AssetQuota

Model for asset quota.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `duration` | `string` | No | Duration type of the quota. |
| `usage` | `integer` | No | Current usage of the quota. |
| `capacity` | `integer` | No | Capacity of the quota. |
| `expirationTime` | `string` | No | Expiration time of current usage limit. |

### QueryFacets

The facets of a query.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `appliedFacets` | `string[]` | No | Facets that are already applied to the search. |
| `availableFacets` | `string[]` | No | The unused and still available facets. |

### QueryCorrection

Contains query correction information for a search query.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `suggestedQuery` | `string` | No | The suggested spelling correction for the original search query. |

### VotingModel

model for voting.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `showVotes` | `boolean` | No | Gets or sets show votes. |
| `upVotes` | `integer` | No | Gets or sets success. |
| `downVotes` | `integer` | No | Gets or sets down votes. |
| `canVote` | `boolean` | No | Gets or sets can vote. |
| `userVote` | `boolean` | No | Gets or sets user vote. |
| `hasVoted` | `boolean` | No | Gets UserVote. |
| `voteCount` | `integer` | No | The total number of votes |
| `upVotePercent` | `integer` | No | The percentage of total votes that have been UpVotes |

### CreatorModelV2

Model representing a creator.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `creator` | `string` | Yes | Deprecated: Please refer to the 'userId' and 'groupId' properties instead. The creator type and ID. E.g. user/123 or group/456. |
| `userId` | `integer` | No | The User ID of the creator. Required if the asset is individual-user-owned. |
| `groupId` | `integer` | No | The Group ID. Required if the asset is group-owned. |
| `name` | `string` | No | The creator's name. |
| `verified` | `boolean` | No | Whether the creator is verified. |
| `latestGroupUpdaterUserId` | `integer` | No | This value only exists for group-based creators and represents the User ID of the creator who most recently updated the asset. |
| `latestGroupUpdaterUserName` | `string` | No | This value only exists for group-based creators and represents the name of the creator who most recently updated the asset. |

### CreatorStoreProduct

The asset's creator store product information.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `purchasePrice` | `Money` | Yes | The price of the asset, including the currency code. |
| `purchasable` | `boolean` | Yes | Whether or not the asset can be purchased in the Creator Store. |

### Asset

Representation of an asset.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No | The unique identifier of the asset. |
| `name` | `string` | No | The name of the asset. |
| `description` | `string` | No | The description of the asset. |
| `assetTypeId` | `integer` | No | The type that the asset belongs to. |
| `socialLinks` | `SocialLinkModel[]` | No | The social links associated with the asset. |
| `previewAssets` | `PreviewAssetsModel` | No | The asset's preview asset ids grouped by asset type. |
| `createTime` | `string` | No | The time the asset was created. |
| `updateTime` | `string` | No | The time the asset was last updated. |
| `creatingUniverseId` | `integer` | No | Universe ID if the asset was created within a specific universe. |
| `categoryPath` | `string` | No | Category Path of the asset, if it exists. e.g. "3d__characters" |
| `revisionId` | `string` | No | The latest revision ID of the asset. The format is an integer string. A new revision is committed whenever the asset is changed in any way. Omitted when unknown. |

### Audio

Representation of an audio asset.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `durationSeconds` | `integer` | No | The duration of the audio file in seconds. |
| `audioType` | `SearchAudioTypeModel` | No | The type of audio (Music or SoundEffect). |
| `artist` | `string` | No | The audio artist. |
| `title` | `string` | No | The audio title. |

### Decal

Representation of a decal asset.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `textureId` | `integer` | No | The texture id of the decal. |
| `textureRevisionId` | `string` | No | The Version Number of the texture that this decal version references, as a string to match the Open Cloud Assets API. Omitted when unknown. |

### MeshPart

Representation of a mesh asset.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `meshId` | `integer` | No | The mesh id of the meshpart. |
| `textureId` | `integer` | No | The texture id of the meshpart. |
| `meshRevisionId` | `string` | No | The Version Number of the mesh that this meshpart version references, as a string to match the Open Cloud Assets API. Omitted when unknown. |
| `textureRevisionId` | `string` | No | The Version Number of the texture that this meshpart version references, as a string to match the Open Cloud Assets API. Omitted when unknown. |

### Model

Representation of a model asset.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `subTypes` | `ModelSubType[]` | No | The subtypes that the model belongs to. |
| `hasScripts` | `boolean` | No | Whether the model has scripts. |
| `scriptCount` | `integer` | No | The number of scripts that are in the model. |
| `objectMeshSummary` | `ObjectMeshSummary` | No | The summary of the meshes within the model, if they exist. |
| `instanceCounts` | `InstanceCounts` | No | The number of studio Instance types in the model. See [Instance](https://create.roblox.com/docs/reference/engine/classes/Instance). These are broken down into specific types, such as MeshPart, Part, Script, Tool, Animation, etc. |
| `capabilities` | `CreatorStoreCapabilitiesModel` | No | Script capabilities for the asset (sandboxing) |

### Music

Representation of a music asset.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `album` | `string` | No | The album the music belongs to. |
| `genre` | `string` | No | The genre of the music. |

### Plugin

Representation of a plugin asset.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `hasScripts` | `boolean` | No | Whether the plugin has scripts. |
| `scriptCount` | `integer` | No | The number of scripts that are in the plugin. |

### SoundEffect

Representation of a sound effect asset.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `category` | `string` | No | The sound effect category. |
| `subcategory` | `string` | No | The sound effect subcategory. |

### ObjectMeshSummary

Provides a summary of the mesh characteristics of an object, such as triangle and vertex counts.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `triangles` | `integer` | No | The total number of triangles in the object's mesh. |
| `vertices` | `integer` | No | The total number of vertices in the object's mesh. |

### InstanceCounts

Represents the count of various instance types within an asset.
See [Instance](https://create.roblox.com/docs/reference/engine/classes/Instance).

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `script` | `integer` | No | The number of Script instances. |
| `meshPart` | `integer` | No | The number of MeshPart instances. |
| `animation` | `integer` | No | The number of Animation instances. |
| `decal` | `integer` | No | The number of Decal instances. |
| `audio` | `integer` | No | The number of Audio instances. |
| `tool` | `integer` | No | The number of Tool instances. |

### CreatorStoreCapabilitiesModel

Represents the capabilities that a model has (e.g. sandboxing).
Only present for model asset types; AMRS includes it in the response when available.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `shouldSandbox` | `boolean` | No | Controls whether the model will be sandboxed upon insertion when it has scripts. |

### SocialLinkModel

Model for a Social Link.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `linkType` | `LinkType` | No | Gets or sets the link type. |
| `url` | `string` | No | Gets or sets the Url. |
| `title` | `string` | No | Gets or sets the title. |

### PreviewAssetsModel

Grouped preview asset ids for an item, separated by media type.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `imagePreviewAssets` | `integer[]` | No | Ordered list of image preview asset ids. |
| `videoPreviewAssets` | `integer[]` | No | Ordered list of video preview asset ids. |

### LinkType

Values: `0`, `1`, `2`, `3`, `4`, `5`, `6`, `7`, `8`, `9`, `10`

### Money

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `currencyCode` | `string` | No |  |
| `quantity` | `Decimal` | No |  |

### Decimal

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `significand` | `integer` | No |  |
| `exponent` | `integer` | No |  |

### AssetQuota

Represents a quota for an asset-related action.

For example, a user might be able to upload 100 audio files per month and
have uploaded 15 already. In this example:
- `quotaType` is `RATE_LIMIT_UPLOAD`
- `assetType` is `AUDIO`
- `usage` is `15`
- `capacity` is `100`
- `period` is `MONTH`
`usageResetTime` indicates when a new period begins and usage resets to 0.
This value **doesn't** necessarily correlate with the first day of a
calendar month or midnight on a given day. For more information on the
upload process, see the
[usage
guide](https://create.roblox.com/docs/en-us/cloud/open-cloud/usage-assets).

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `path` | `string` | No | The resource path of the asset quota.  Format: `users/{user_id}/asset-quotas/{asset_quota_id}` |
| `quotaType` | `QuotaType` | No | Type of quota.  Possible values:    \| Value \| Description \|   \| --- \| --- \|   \| UNSPECIFIED \| The default quota type. \|   \| RATE_LIMIT_UPLOAD \| Rate limit on how often one can upload an asset. \|   \| RATE_LIMIT_CREATOR_STORE_DISTRIBUTE \| Rate limit on how often one can distribute an asset on the Creator Store. \| |
| `assetType` | `Roblox.OpenCloud.Cloud.V2.AssetType` | No | The asset type the quota is for.  Possible values:    \| Value \| Description \|   \| --- \| --- \|   \| UNSPECIFIED \| The default asset type. \|   \| IMAGE \| Image \|   \| TSHIRT \| Tshirt \|   \| AUDIO \| Audio \|   \| MESH \| Mesh \|   \| LUA \| Lua \|   \| HAT \| Hat \|   \| PLACE \| Place \|   \| MODEL \| Model \|   \| SHIRT \| Classic Shirt \|   \| PANTS \| Classic Pants \|   \| DECAL \| Decal \|   \| HEAD \| Head \|   \| FACE \| Face \|   \| GEAR \| Gear \|   \| ANIMATION \| Animation \|   \| TORSO \| Torso \|   \| RIGHT_ARM \| Right Arm \|   \| LEFT_ARM \| Left Arm \|   \| LEFT_LEG \| Left Leg \|   \| RIGHT_LEG \| Right Leg \|   \| YOUTUBE_VIDEO \| YouTube Video \|   \| APP \| App \|   \| CODE \| Code \|   \| PLUGIN \| Plugin \|   \| SOLID_MODEL \| Solid Model \|   \| MESH_PART \| Mesh Part \|   \| HAIR_ACCESSORY \| Hair Accessory \|   \| FACE_ACCESSORY \| Face Accessory \|   \| NECK_ACCESSORY \| Neck Accessory \|   \| SHOULDER_ACCESSORY \| Shoulder Accessory \|   \| FRONT_ACCESSORY \| Front Accessory \|   \| BACK_ACCESSORY \| Back Accessory \|   \| WAIST_ACCESSORY \| Waist Accessory \|   \| CLIMB_ANIMATION \| Climb Animation \|   \| DEATH_ANIMATION \| Death Animation \|   \| FALL_ANIMATION \| Fall Animation \|   \| IDLE_ANIMATION \| Idle Animation \|   \| JUMP_ANIMATION \| Jump Animation \|   \| RUN_ANIMATION \| Run Animation \|   \| SWIM_ANIMATION \| Swim Animation \|   \| WALK_ANIMATION \| Walk Animation \|   \| POSE_ANIMATION \| Pose Animation \|   \| LOCALIZATION_TABLE_MANIFEST \| Localization Table Manifest \|   \| LOCALIZATION_TABLE_TRANSLATION \| Localization Table Translation \|   \| EMOTE_ANIMATION \| Emote Animation \|   \| VIDEO \| Video \|   \| TEXTURE_PACK \| Texture Pack \|   \| TSHIRT_ACCESSORY \| Tshirt Accessory \|   \| SHIRT_ACCESSORY \| Shirt Accessory \|   \| PANTS_ACCESSORY \| Pants Accessory \|   \| JACKET_ACCESSORY \| Jacket Accessory \|   \| SWEATER_ACCESSORY \| Sweater Accessory \|   \| SHORTS_ACCESSORY \| Shorts Accessory \|   \| LEFT_SHOE_ACCESSORY \| Left Shoe Accessory \|   \| RIGHT_SHOE_ACCESSORY \| Right Shoe Accessory \|   \| DRESS_SKIRT_ACCESSORY \| Dress Skirt Accessory \|   \| FONT_FAMILY \| Font Family \|   \| FONT_FACE \| Font Face \|   \| MESH_HIDDEN_SURFACE_REMOVAL \| Mesh Hidden Surface Removal \|   \| EYEBROW_ACCESSORY \| Eyebrow Accessory \|   \| EYELASH_ACCESSORY \| Eyelash Accessory \|   \| MOOD_ANIMATION \| Mood Animation \|   \| DYNAMIC_HEAD \| Dynamic Head \|   \| CODE_SNIPPET \| Code Snippet \|   \| ADS_VIDEO \| Ads Video \| |
| `usage` | `string` | No | The current usage of the quota. |
| `capacity` | `string` | No | The capacity of the quota. |
| `period` | `Period` | No | The period of time the quota is for.  Possible values:    \| Value \| Description \|   \| --- \| --- \|   \| UNSPECIFIED \| The default period, which is invalid. Specify another value. \|   \| MONTH \| Month \|   \| DAY \| Day \| |
| `usageResetTime` | `string` | No | The time the usage will reset for this quota. |

### QuotaType

Quota type.

Values: `UNSPECIFIED`, `RATE_LIMIT_UPLOAD`, `RATE_LIMIT_CREATOR_STORE_DISTRIBUTE`

### Roblox.OpenCloud.Cloud.V2.AssetType

Type of the Asset.

Values: `UNSPECIFIED`, `IMAGE`, `TSHIRT`, `AUDIO`, `MESH`, `LUA`, `HAT`, `PLACE`, `MODEL`, `SHIRT`, `PANTS`, `DECAL`, `HEAD`, `FACE`, `GEAR`, `ANIMATION`, `TORSO`, `RIGHT_ARM`, `LEFT_ARM`, `LEFT_LEG`, `RIGHT_LEG`, `YOUTUBE_VIDEO`, `APP`, `CODE`, `PLUGIN`, `SOLID_MODEL`, `MESH_PART`, `HAIR_ACCESSORY`, `FACE_ACCESSORY`, `NECK_ACCESSORY`, `SHOULDER_ACCESSORY`, `FRONT_ACCESSORY`, `BACK_ACCESSORY`, `WAIST_ACCESSORY`, `CLIMB_ANIMATION`, `DEATH_ANIMATION`, `FALL_ANIMATION`, `IDLE_ANIMATION`, `JUMP_ANIMATION`, `RUN_ANIMATION`, `SWIM_ANIMATION`, `WALK_ANIMATION`, `POSE_ANIMATION`, `LOCALIZATION_TABLE_MANIFEST`, `LOCALIZATION_TABLE_TRANSLATION`, `EMOTE_ANIMATION`, `VIDEO`, `TEXTURE_PACK`, `TSHIRT_ACCESSORY`, `SHIRT_ACCESSORY`, `PANTS_ACCESSORY`, `JACKET_ACCESSORY`, `SWEATER_ACCESSORY`, `SHORTS_ACCESSORY`, `LEFT_SHOE_ACCESSORY`, `RIGHT_SHOE_ACCESSORY`, `DRESS_SKIRT_ACCESSORY`, `FONT_FAMILY`, `FONT_FACE`, `MESH_HIDDEN_SURFACE_REMOVAL`, `EYEBROW_ACCESSORY`, `EYELASH_ACCESSORY`, `MOOD_ANIMATION`, `DYNAMIC_HEAD`, `CODE_SNIPPET`, `ADS_VIDEO`

### Period

Period of time the quota is for.

Values: `UNSPECIFIED`, `MONTH`, `DAY`

### TextToSpeechService.Status

The `Status` type defines a logical error model that is suitable for
different programming environments, including REST APIs and RPC APIs. It is
used by [gRPC](https://github.com/grpc). Each `Status` message contains
three pieces of data: error code, error message, and error details.

You can find out more about this error model and how to work with it in the
[API Design Guide](https://cloud.google.com/apis/design/errors).

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `code` | `integer` | No | The status code, which should be an enum value of [google.rpc.Code][google.rpc.Code]. |
| `message` | `string` | No | A developer-facing error message, which should be in English. Any user-facing error message should be localized and sent in the [google.rpc.Status.details][google.rpc.Status.details] field, or localized by the client. |
| `details` | `object[]` | No | A list of messages that carry the error details.  There is a common set of message types for APIs to use. |

### GenerateSpeechAssetRequest_GeneratedSpeechStyle

Information about the style of generated speech.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `voiceId` | `string` | No | An ID corresponding to the voice type specified. A mapping of voice type to ID number is available in the documentation. |
| `pitch` | `number` | No | The pitch of the generated speech. |
| `speed` | `number` | No | The speed of the generated speech. |

### PreSignedUploadUrl

A pre-signed upload URL which allows anyone with this URL to upload a file with limited HTTP method and file size.
            
Example curl command to upload with a pre-signed PUT url:
curl -v {pre-signed url} -T {filepath}

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `httpVerb` | `string` | No | HTTP Verb to use with the given url. |
| `url` | `string` | No | Pre signed url used to upload. |
| `expirationTimeMs` | `string` | No | Expiration of pre signed url. |
| `chunkNum` | `string` | No | Num of file chunk to upload corresponding to the ChunkPlan in the start request. |
| `contentStart` | `string` | No | Start position of this chunk. |
| `contentLength` | `string` | No | Length of this chunk. |

### File

A file to be uploaded

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `contentType` | `string` | No | MIME type of the file content. |
| `filesize` | `integer` | No | Size of the file. |
| `md5Checksum` | `string` | No | MD5 checksum of the file. |
| `chunkPlan` | `integer[]` | No | A list of chunk lengths. |

### CreationContext

The context of creation that is not part of the asset content, such as metadata and creator information. Required for [Create Asset](#Assets_CreateAsset).

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `creator` | `AssetsUploadApi.Creator` | No |  |
| `expectedPrice` | `integer` | No | Expected asset upload fee in Robux. When the actual price is more than expected, the operation fails with a 400 error. |
| `creatingUniverseId` | `integer` | No |  |
| `assetPrivacy` | `AssetPrivacy` | No | Desired privacy setting for the asset on creation. Only applies to asset types that support privacy override. |

### ModerationResult

The moderation result of the asset.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `moderationState` | `ModerationState` | No | The moderation state of the asset. Can be `Reviewing`, `Rejected`, or `Approved`. |

### ModerationState

The moderation state of the asset.

Values: `Unspecified`, `Reviewing`, `Rejected`, `Approved`

### AssetsUploadApi.Creator

Represents a creator. Only one creator ID is set, according to the creator type.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `userId` | `string` | No | The user ID as a decimal string. Set when the asset is owned by a user. |
| `groupId` | `string` | No | The group ID as a decimal string. Set when the asset is owned by a group. |
| `experienceId` | `string` | No |  |

### AssetPrivacy

The privacy setting of the asset. Requested asset privacy is only applicable to asset types that allow privacy override. For more details see [Asset Privacy](/projects/assets/privacy.md).

Values: `Unspecified`, `Default`, `OpenUse`, `Restricted`

### ErrorInfo

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `reason` | `string` | No |  |
| `domain` | `string` | No |  |
| `metadata` | `object` | No |  |

### AssetType

Type of the Asset.

Values: `Unspecified`, `Image`, `Tshirt`, `Audio`, `Mesh`, `Lua`, `Html`, `Text`, `Hat`, `Place`, `Model`, `Shirt`, `Pants`, `Decal`, `Avatar`, `Head`, `Face`, `Gear`, `Badge`, `GroupEmblem`, `Animation`, `Arms`, `Legs`, `Torso`, `RightArm`, `LeftArm`, `LeftLeg`, `RightLeg`, `Package`, `YoutubeVideo`, `GamePass`, `App`, `Code`, `Plugin`, `SolidModel`, `MeshPart`, `HairAccessory`, `FaceAccessory`, `NeckAccessory`, `ShoulderAccessory`, `FrontAccessory`, `BackAccessory`, `WaistAccessory`, `ClimbAnimation`, `DeathAnimation`, `FallAnimation`, `IdleAnimation`, `JumpAnimation`, `RunAnimation`, `SwimAnimation`, `WalkAnimation`, `PoseAnimation`, `LocalizationTableManifest`, `LocalizationTableTranslation`, `EmoteAnimation`, `Video`, `TexturePack`, `TshirtAccessory`, `ShirtAccessory`, `PantsAccessory`, `JacketAccessory`, `SweaterAccessory`, `ShortsAccessory`, `LeftShoeAccessory`, `RightShoeAccessory`, `DressSkirtAccessory`, `FontFamily`, `FontFace`, `MeshHiddenSurfaceRemoval`, `EyebrowAccessory`, `EyelashAccessory`, `MoodAnimation`, `DynamicHead`, `CodeSnippet`, `AdsVideo`, `OtaUpdate`, `Screenshot`, `RuntimePropertySet`, `StorePreviewVideo`, `GamePreviewVideo`, `CreatorExperienceConfig`, `FaceMakeup`, `LipMakeup`, `EyeMakeup`, `VoxelFragment`, `AvatarBackground`, `TextDocument`, `Post`, `AnimatedImage`, `ComputeFunction`, `Voice`

### Preview

An asset preview.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `asset` | `string` | No | The preview asset path. |
| `altText` | `string` | No | Alt text for the preview asset. |

### State

Whether the asset is active or archived. Unspecified isn't used.

Values: `Unspecified`, `Active`, `Archived`

### SocialLink

A social media link for the asset. Maximum of three per asset. Object name can be any of: <ul><li>`facebookSocialLink`</li><li>`twitterSocialLink`</li><li>`youtubeSocialLink`</li><li>`twitchSocialLink`</li><li>`discordSocialLink`</li><li>`githubSocialLink`</li><li>`robloxSocialLink`</li><li>`guildedSocialLink`</li><li>`devForumSocialLink`</li></ul>For syntax, see the sample request under [Update Asset](#Assets_UpdateAsset).

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `title` | `string` | No | An optional title for the social media link. Not used on the Creator Hub. |
| `uri` | `string` | No | The URI for the social media link. Must match the expected format for the type of link. For example, the URI for a `twitchSocialLink` object must be of the format `https://twitch.tv/your-channel`. |

### AssetPermissions.Error

The error object for results.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `code` | `AssetPermissions.ErrorCode` | No |  |
| `message` | `string` | No | The human readable error message. |

### AssetPermissions.ErrorCode

Enums for customized error code in error responses.

Values: `UnknownError`, `InvalidRequest`, `AssetNotFound`, `CannotManageAsset`, `PublicAssetCannotBeGrantedTo`, `CannotManageSubject`, `SubjectNotFound`, `AssetTypeNotEnabled`, `PermissionLimitReached`, `DependenciesLimitReached`, `NotRequestable`, `RequesterNotAConnection`, `AlreadyPending`, `AlreadyHasAccess`, `RequestNotFound`, `InvalidRequestStatus`, `RateLimited`, `CallerNotOwner`, `BatchSizeLimitExceeded`

### GrantPermissionError

Single error for BatchGrantPermissionsResponse.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `assetId` | `integer` | No | Failed asset ID. |
| `code` | `AssetPermissions.ErrorCode` | No |  |

### SubjectType

Values: `Invalid`, `User`, `Group`, `GroupRoleset`, `All`, `Universe`, `CommunicationPlatformMessage`, `IpPlatform`

### AssetAction

Asset permission actions that can be granted.
            
Actions:
* Invalid - default value, not a valid action.
* Edit - grants the ability to edit and manage the asset.
* Use - grants the ability to use the asset.
* Download - grants the ability to download the asset.
* CopyFromRcc - grants the ability to copy the asset from RCC, used to enable AssetService:CreatePlaceAsync().
* UpdateFromRcc - grants the ability to update the asset from RCC, used to enable AssetService:UpdatePlaceAsync().
            
Valid AssetType - SubjectType - Action combinations:
* Animation - Group/User/Universe - Use
* Audio - Group/User/Universe - Use
* Decal - All/Group/User/Universe - Use
* Image - All/Group/User/Universe - Use
* Mesh - All/Group/User/Universe - Use
* MeshPart - Group/User/Universe - Use
* Model - User - Edit
  * Group/User/Universe - Use
* Place - All - Download
  * Universe - CopyFromRcc/UpdateFromRcc
* Video - Group/User/Universe - Use.

Values: `Invalid`, `Edit`, `Use`, `Download`, `CopyFromRcc`, `UpdateFromRcc`

### AssetGrantRequest

Asset grant requests with additional options to grant to dependencies.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `assetId` | `integer` | No | The asset ID to grant permission to. |
| `grantToDependencies` | `boolean` | No | Whether to extend the permission grant to dependencies of the asset. This will be done asynchronously after the main grant. |
| `parentVersionNumber` | `integer` | No | The version number of 'assetId' to use for determining asset dependencies. |