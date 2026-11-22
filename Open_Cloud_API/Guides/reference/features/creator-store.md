<!-- Source: https://create.roblox.com/docs/en-us/cloud/reference/features/creator-store.md -->

---
name: "Creator Store"
last_updated: 2026-11-20T18:47:47Z
type: feature
api_base_url: "https://apis.roblox.com"
endpoints: 8
auth: [api-key, oauth2, cookie]
description: "Manage your presence on the [Creator Store](/production/creator-store)"
---

# Creator Store

Manage your presence on the [Creator Store](/production/creator-store). [Create](#Cloud_CreateCreatorStoreProduct) and [update](#Cloud_UpdateCreatorStoreProduct) product listings for your assets, and [search the toolbox](#Toolbox_SearchCreatorStoreAssets) for assets using various filters.

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

### POST `/cloud/v2/creator-store-products` [BETA]

Create Creator Store Product

Add a Creator Store product. Only use this method if your product has never been distributed on the Creator Store; otherwise, use the `PATCH` method to update the product.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `creator-store-product:write`

**Request Body:** `application/json` — Type: `MarketplaceFiatService.CreatorStoreProduct`

See [MarketplaceFiatService.CreatorStoreProduct](#marketplacefiatservice-creatorstoreproduct) in Models.

**Request example:**
```json
{
  "path": "string",
  "basePrice": {
    "currencyCode": "string",
    "quantity": {
      "significand": "...",
      "exponent": "..."
    }
  },
  "purchasePrice": {
    "currencyCode": "string",
    "quantity": {
      "significand": "...",
      "exponent": "..."
    }
  },
  "published": false,
  "restrictions": [
    "RESTRICTION_UNSPECIFIED"
  ],
  "purchasable": false
}
```

**Responses:**

- `200`: OK → `MarketplaceFiatService.CreatorStoreProduct`
- `default`: Error → `Google.Rpc.Status`

**Response fields** (`MarketplaceFiatService.CreatorStoreProduct`)

See [MarketplaceFiatService.CreatorStoreProduct](#marketplacefiatservice-creatorstoreproduct) in Models.

**Response example:**
```json
{
  "path": "string",
  "basePrice": {
    "currencyCode": "string",
    "quantity": {
      "significand": "...",
      "exponent": "..."
    }
  },
  "purchasePrice": {
    "currencyCode": "string",
    "quantity": {
      "significand": "...",
      "exponent": "..."
    }
  },
  "published": false,
  "restrictions": [
    "RESTRICTION_UNSPECIFIED"
  ],
  "purchasable": false
}
```

**Rate Limits:** perApiKeyOwner: 30/minute, perOauth2Authorization: 30/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/creator-store-products" \
  -H "Content-Type: application/json" \
  -d '{"path":"string","basePrice":{"currencyCode":"string","quantity":{"significand":"...","exponent":"..."}},"purchasePrice":{"currencyCode":"string","quantity":{"significand":"...","exponent":"..."}},"published":false,"restrictions":["RESTRICTION_UNSPECIFIED"],"purchasable":false}'
```

### GET `/cloud/v2/creator-store-products/{creator_store_product_id}` [BETA]

Get Creator Store Product

Get a Creator Store product.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `creator-store-product:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `creator_store_product_id` | path | `string` | Yes | The creator-store-product ID. |

**Responses:**

- `200`: OK → `MarketplaceFiatService.CreatorStoreProduct`
- `default`: Error → `Google.Rpc.Status`

**Response fields** (`MarketplaceFiatService.CreatorStoreProduct`)

See [MarketplaceFiatService.CreatorStoreProduct](#marketplacefiatservice-creatorstoreproduct) in Models.

**Response example:**
```json
{
  "path": "string",
  "basePrice": {
    "currencyCode": "string",
    "quantity": {
      "significand": "...",
      "exponent": "..."
    }
  },
  "purchasePrice": {
    "currencyCode": "string",
    "quantity": {
      "significand": "...",
      "exponent": "..."
    }
  },
  "published": false,
  "restrictions": [
    "RESTRICTION_UNSPECIFIED"
  ],
  "purchasable": false
}
```

**Rate Limits:** perApiKeyOwner: 30/minute, perOauth2Authorization: 30/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/creator-store-products/{CREATOR_STORE_PRODUCT_ID}"
```

### PATCH `/cloud/v2/creator-store-products/{creator_store_product_id}` [BETA]

Update Creator Store Product

Update a Creator Store product.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `creator-store-product:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `creator_store_product_id` | path | `string` | Yes | The creator-store-product ID. |
| `updateMask` | query | `string` | No | The list of fields to update. |
| `allowMissing` | query | `boolean` | No | If set to true, and the creator store product is not found, a creator store product is created. In this situation, `update_mask` is ignored. |

**Request Body:** `application/json` — Type: `MarketplaceFiatService.CreatorStoreProduct`

See [MarketplaceFiatService.CreatorStoreProduct](#marketplacefiatservice-creatorstoreproduct) in Models.

**Request example:**
```json
{
  "path": "string",
  "basePrice": {
    "currencyCode": "string",
    "quantity": {
      "significand": "...",
      "exponent": "..."
    }
  },
  "purchasePrice": {
    "currencyCode": "string",
    "quantity": {
      "significand": "...",
      "exponent": "..."
    }
  },
  "published": false,
  "restrictions": [
    "RESTRICTION_UNSPECIFIED"
  ],
  "purchasable": false
}
```

**Responses:**

- `200`: OK → `MarketplaceFiatService.CreatorStoreProduct`
- `default`: Error → `Google.Rpc.Status`

**Response fields** (`MarketplaceFiatService.CreatorStoreProduct`)

See [MarketplaceFiatService.CreatorStoreProduct](#marketplacefiatservice-creatorstoreproduct) in Models.

**Response example:**
```json
{
  "path": "string",
  "basePrice": {
    "currencyCode": "string",
    "quantity": {
      "significand": "...",
      "exponent": "..."
    }
  },
  "purchasePrice": {
    "currencyCode": "string",
    "quantity": {
      "significand": "...",
      "exponent": "..."
    }
  },
  "published": false,
  "restrictions": [
    "RESTRICTION_UNSPECIFIED"
  ],
  "purchasable": false
}
```

**Rate Limits:** perApiKeyOwner: 30/minute, perOauth2Authorization: 30/minute

**Example:**
```bash
curl -X PATCH -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/creator-store-products/{CREATOR_STORE_PRODUCT_ID}" \
  -H "Content-Type: application/json" \
  -d '{"path":"string","basePrice":{"currencyCode":"string","quantity":{"significand":"...","exponent":"..."}},"purchasePrice":{"currencyCode":"string","quantity":{"significand":"...","exponent":"..."}},"published":false,"restrictions":["RESTRICTION_UNSPECIFIED"],"purchasable":false}'
```

### GET `/toolbox-service/v1/saves` [BETA]

Gets saves from a collection.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `creator-store-save:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `targetType` | query | `SearchCategoryType` | No | The asset type to filter by Valid values: `Audio`, `Place`, `Model`, `Decal`, `Plugin`, `MeshPart`, `Video`, `FontFamily` |
| `targetId` | query | `integer` | No | The ID of the asset to filter by. If provided, targetType must also be provided. |
| `collectionName` | query | `string` | No | Custom collections are not currently supported. This field should be omitted. |
| `sortBy` | query | `SavesSortCategory` | No | The field to sort by Valid values: `Name`, `Creator`, `Ratings`, `TargetType`, `DateSaved`, `LastModified`, `Price` |
| `sortDirection` | query | `SortDirection` | No | The direction to sort by Valid values: `None`, `Ascending`, `Descending` |
| `limit` | query | `integer` | No | The maximum number of saves to return |
| `page` | query | `integer` | No | The page number to return, starting from 1 |
| `keyword` | query | `string` | No | The keyword to filter by |
| `hideOwnedAssets` | query | `boolean` | No | Whether to hide owned assets |

**Responses:**

- `200`: OK → `GetSavesResponse`
- `400`: Bad Request → `any`

**Response fields** (`GetSavesResponse`)

See [GetSavesResponse](#getsavesresponse) in Models.

**Response example:**
```json
{
  "totalCount": 0,
  "saves": [
    {
      "owned": "...",
      "dateSaved": "...",
      "creatorStoreAsset": "..."
    }
  ]
}
```

**Rate Limits:** perApiKeyOwner: 200/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/toolbox-service/v1/saves"
```

### POST `/toolbox-service/v1/saves` [BETA]

Creates a save.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `creator-store-save:write`

**Request Body:** `application/json-patch+json` — Type: `CreateSaveRequest`

See [CreateSaveRequest](#createsaverequest) in Models.

**Request example:**
```json
{
  "targetType": "Audio",
  "targetId": 0,
  "collectionName": "string"
}
```

**Responses:**

- `201`: Created
- `400`: Bad Request → `any`
- `404`: Not Found → `any`
- `409`: Conflict → `any`

**Rate Limits:** perApiKeyOwner: 200/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/toolbox-service/v1/saves" \
  -H "Content-Type: application/json" \
  -d '{
  "targetType": "Audio",
  "targetId": 0,
  "collectionName": "string"
}'
```

### DELETE `/toolbox-service/v1/saves` [BETA]

Deletes a save.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `creator-store-save:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `targetType` | query | `SearchCategoryType` | No | The type of asset being deleted Valid values: `Audio`, `Place`, `Model`, `Decal`, `Plugin`, `MeshPart`, `Video`, `FontFamily` |
| `targetId` | query | `integer` | No | The ID of the asset being deleted |
| `collectionName` | query | `string` | No | Custom collections are not currently supported. This field should be omitted. |

**Responses:**

- `204`: No Content
- `400`: Bad Request → `any`
- `404`: Not Found → `any`

**Rate Limits:** perApiKeyOwner: 200/minute

**Example:**
```bash
curl -X DELETE -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/toolbox-service/v1/saves"
```

### POST `/toolbox-service/v1/saves:bulkDelete` [BETA]

Bulk deletes saves.
Max of 5000 saves per request.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `creator-store-save:write`

**Request Body:** `application/json-patch+json` — Type: `BulkDeleteSavesRequest`

See [BulkDeleteSavesRequest](#bulkdeletesavesrequest) in Models.

**Request example:**
```json
{
  "targets": [
    {
      "targetType": "...",
      "targetId": "...",
      "collectionName": "..."
    }
  ]
}
```

**Responses:**

- `200`: OK → `BulkDeleteSavesResponse`
- `400`: Bad Request → `any`
- `404`: Not Found → `any`

**Response fields** (`BulkDeleteSavesResponse`)

See [BulkDeleteSavesResponse](#bulkdeletesavesresponse) in Models.

**Response example:**
```json
{
  "deletedCount": 0
}
```

**Rate Limits:** perApiKeyOwner: 200/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/toolbox-service/v1/saves:bulkDelete" \
  -H "Content-Type: application/json" \
  -d '{
  "targets": [
    {
      "targetType": "...",
      "targetId": "...",
      "collectionName": "..."
    }
  ]
}'
```

### POST `/toolbox-service/v2/assets:search` [BETA]

Search Creator Store Assets

Search Creator Store for assets.

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `creator-store-product:read`

**Request Body:** `application/json-patch+json` — Type: `SearchCreatorStoreAssetsRequest`

See [SearchCreatorStoreAssetsRequest](#searchcreatorstoreassetsrequest) in Models.

**Request example:**
```json
{
  "searchCategoryType": "Audio",
  "query": "string",
  "image": "string",
  "userId": 0,
  "groupId": 0,
  "pageToken": "string"
}
```

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
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/toolbox-service/v2/assets:search" \
  -H "Content-Type: application/json" \
  -d '{
  "searchCategoryType": "Audio",
  "query": "string",
  "image": "string",
  "userId": 0,
  "groupId": 0,
  "pageToken": "string"
}'
```

## Models

### MarketplaceFiatService.CreatorStoreProduct

Represents a product in the Creator Store. This resource is used to manage
distribution and pricing of assets on the Creator Store.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `path` | `string` | No | The resource path of the creator store product.  Format: `creator-store-products/{creator_store_product_id}` |
| `basePrice` | `MarketplaceFiatService.Money` | No | The base price of the product. For more information, see [Money](/cloud/reference/types.md#money). Each product type (such as `pluginAssetId`) supports a set of specific prices. Currently, only setting a base price in USD is supported.  Depending on type, each Creator Store product has a fixed set of supported prices; see the `productType` attribute for the full list. For example, to set the price of a plugin to $4.99, use the following base price: ``` "basePrice": {   "currencyCode": "USD",   "quantity": {     "significand": 4990000000,     "exponent": -9   } } ```  Note: The exponent **must** be -9, and the significand must be in this format. The corresponding [Decimal](/cloud/reference/types.md#decimal) format is `significand * 10^exponent`.  If you want to set the price of a plugin to $0 (i.e. free), use the following `base_price`  ``` "basePrice": {   "currencyCode": "USD",   "quantity": {     "significand": 0,     "exponent": 0   } } ```  Note: You must still set the `currencyCode` to USD, even for free products.  The actual purchase price is based on this base price, but often differs slightly due to locale-specific considerations.  Set this to zero to make the product free. |
| `purchasePrice` | `MarketplaceFiatService.Money` | No | The effective purchase price for the user, after factoring in locale-specific considerations. |
| `published` | `boolean` | No | Whether the seller intends to distribute the Creator Store product on the Creator Store. A seller might intend to distribute a product, but due to some restrictions on the seller or underlying Creator Store product, the product may not be available for purchase. See `restrictions` and `purchasable` for more details. |
| `restrictions` | `RESTRICTION_UNSPECIFIED \| SOLD_ITEM_RESTRICTED \| SELLER_TEMPORARILY_RESTRICTED \| SELLER_PERMANENTLY_RESTRICTED \| SELLER_NO_LONGER_ACTIVE[]` | No | Restrictions applied to the product. A product can have multiple restrictions active at one time.  Possible values:    \| Value \| Description \|   \| --- \| --- \|   \| RESTRICTION_UNSPECIFIED \| Unspecified restriction. \|   \| SOLD_ITEM_RESTRICTED \| The item being sold has been restricted by Roblox  Details may be available by looking up that item directly. \|   \| SELLER_TEMPORARILY_RESTRICTED \| The product is restricted because the seller's account is temporarily restricted by Roblox. \|   \| SELLER_PERMANENTLY_RESTRICTED \| The product is restricted because the seller's account is permanently restricted by Roblox. \|   \| SELLER_NO_LONGER_ACTIVE \| The product is restricted because the seller's account was deleted or is otherwise no longer active. \| |
| `purchasable` | `boolean` | No | Whether the product is purchasable.  For this value to be true, `published` must be true and `restrictions` must be empty. If this value is false, the product may not be acquired by any user. |
| `userSeller` | `string` | No | The Roblox user selling the product. |
| `groupSeller` | `string` | No | The Roblox group selling the product. |
| `modelAssetId` | `string` | No |  *(immutable)* The Creator Store product is a model with this asset ID. |
| `pluginAssetId` | `string` | No |  *(immutable)* The Creator Store product is a plugin with this asset ID.  Supported base prices in USD: $0, $4.99, $5.99, $6.99, $7.99, $8.99, $9.99, $10.99, $11.99, $12.99, $13.99, $14.99, $15.99, $16.99, $17.99, $18.99, $19.99, $24.99, $29.99, $34.99, $39.99, $44.99, $49.99, $59.99, $69.99, $79.99, $89.99, $99.99, $149.99, $199.99, $249.99 |
| `audioAssetId` | `string` | No |  *(immutable)* The Creator Store product is an audio file with this asset ID. |
| `decalAssetId` | `string` | No |  *(immutable)* The Creator Store product is a decal with this asset ID. |
| `meshPartAssetId` | `string` | No |  *(immutable)* The Creator Store product is a mesh part with this asset ID. |
| `videoAssetId` | `string` | No |  *(immutable)* The Creator Store product is a video with this asset ID. |
| `fontFamilyAssetId` | `string` | No |  *(immutable)* The Creator Store product is a font family with this asset ID. |

### Google.Rpc.Status

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `code` | `integer` | No |  |
| `message` | `string` | No |  |
| `details` | `Google.Protobuf.WellKnownTypes.Any[]` | No |  |

### SearchCategoryType

This represents a "subset" of Toolbox.Service.CategoryType options and represent the full set
of "categories" (or asset types) that can be searched upon from the toolbox search API.

Values: `Audio`, `Place`, `Model`, `Decal`, `Plugin`, `MeshPart`, `Video`, `FontFamily`

### SavesSortCategory

The category to sort the saves by.

Values: `Name`, `Creator`, `Ratings`, `TargetType`, `DateSaved`, `LastModified`, `Price`

### SortDirection

Represents the direction in which to sort the results

Values: `None`, `Ascending`, `Descending`

### GetSavesResponse

Response model for getting saves

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `totalCount` | `integer` | Yes | The total number of saves that match the query. |
| `saves` | `HydratedSave[]` | Yes | Gets or sets the saves. |

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

### CreateSaveRequest

Request model for creating a save

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `targetType` | `SearchCategoryType` | Yes | The type of asset being saved |
| `targetId` | `integer` | Yes | The ID of the asset being saved |
| `collectionName` | `string` | No | Custom collections are not currently supported. This field should be omitted. |

### BulkDeleteSavesRequest

Request model for bulk deleting saves

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `targets` | `DeleteSaveRequest[]` | Yes | A list of saves being deleted |

### BulkDeleteSavesResponse

Response model for bulk delete saves operation

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `deletedCount` | `integer` | No | Number of saves that were successfully deleted |

### SearchCreatorStoreAssetsRequest

Request model for searching Creator Store assets.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `searchCategoryType` | `SearchCategoryType` | No | The asset type to search within. Optional when CategoryPath resolves to an asset type; otherwise required. SearchCategoryType.Place is only valid with the `gameplay_templates` Swimlane. |
| `query` | `string` | No | The search terms used to filter the results. Only one of 'query' and 'image' can be present in a query. |
| `image` | `string` | No | The image file to search by. The image must be base64 encoded to be used in the search. Only one of 'query' and 'image' can be present in a query. |
| `userId` | `integer` | No | The User ID of the creator. Only one of 'userId' and 'groupId' can be present in a query. |
| `groupId` | `integer` | No | The Group ID of the creator. Only one of 'userId' and 'groupId' can be present in a query. |
| `pageToken` | `string` | No | The identifier for the desired search results page. Only one of 'pageNumber' and 'pageToken' can be present in a query. |
| `pageNumber` | `integer` | No | The page number to retrieve, starting from 0. Only one of 'pageNumber' and 'pageToken' can be present in a query. |
| `maxPageSize` | `integer` | No | The number of assets to be returned. Cannot be larger than 100. |
| `sortDirection` | `SortDirection` | No | The sort direction of the search results. |
| `sortCategory` | `SortCategory` | No | The category to sort the search results by. |
| `includeOnlyVerifiedCreators` | `boolean` | No | Whether the results should only include assets created by verified creators. |
| `minPriceCents` | `integer` | No | The minimum price of the asset in cents. If included, must be greater than or equal to 0. |
| `maxPriceCents` | `integer` | No | The maximum price of the asset in cents. If included, must be greater than or equal to 0. |
| `facets` | `string[]` | No | Additional keywords to query by. |
| `tags` | `string[]` | No | The tags to filter by. |
| `categoryPath` | `string` | No | The category path to filter by. |
| `swimlane` | `string` | No | Optional swimlane identifier (e.g. "trending", "essential", "priced"). |
| `searchView` | `SearchView` | No | Indicates which fields will be populated in the response. |
| `audioSearchFilters` | `AudioSearchFilters` | No | Audio-specific search filters. |
| `modelSearchFilters` | `ModelSearchFilters` | No | Model-specific search filters. |

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

### QueryFacets

The facets of a query.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `appliedFacets` | `string[]` | No | Facets that are already applied to the search. |
| `availableFacets` | `string[]` | No | The unused and still available facets. |

### CreatorStoreAsset

Representation of a creator store asset.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `voting` | `VotingModel` | No | The asset's voting details. |
| `creator` | `CreatorModelV2` | No | The asset creator's details. |
| `creatorStoreProduct` | `CreatorStoreProduct` | No | The asset's product details. |
| `asset` | `any` | Yes | The asset information. |

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

### ModelSubType

The supported model subtypes.

Values: `Ad`, `MaterialPack`, `Package`

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

### SearchAudioTypeModel

Represents audio type values that will be properly displayed in Swagger UI.

Values: `Music`, `SoundEffect`, `Unknown`

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

### SortCategory

The category to sort the search results by.

Values: `Relevance`, `Trending`, `Top`, `AudioDuration`, `CreateTime`, `UpdatedTime`, `Ratings`

### SearchView

This view controls which fields are populated in the search response. A lighter
view will result in faster response times and higher reliability.

Values: `IDs`, `Core`, `Full`

### AudioSearchFilters

Audio-specific search filter parameters.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `audioTypes` | `SearchAudioTypeModel[]` | No | Audio types to include (e.g. Music, SoundEffect) |
| `minDurationSeconds` | `integer` | No | The minimum duration for audio in seconds. If included, must be greater than or equal to 0. |
| `maxDurationSeconds` | `integer` | No | The maximum duration for audio in seconds. If included, must be greater than or equal to 1. |
| `artist` | `string` | No | The name of the artist to filter by. |
| `album` | `string` | No | The name of the album to filter by. |
| `musicChartType` | `MusicChartType` | No | Indicates which music charts to filter from. |

### ModelSearchFilters

Model-specific search filter parameters.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `includedSubTypes` | `ModelSubType[]` | No | If included, search for assets only with these subtypes. |
| `excludedSubTypes` | `ModelSubType[]` | No | If included, excludes assets with these subtypes. |
| `includedInstanceTypes` | `ModelInstanceType[]` | No | This filters that the following [Instance](https://create.roblox.com/docs/reference/engine/classes/Instance) types are included in the model. |

### ModelInstanceType

A list of model instance types. See Toolbox.Service.Models.Internal.InstanceCounts and [Instance](https://create.roblox.com/docs/reference/engine/classes/Instance) for more details.

Values: `Script`, `MeshPart`, `Decal`, `Animation`, `Audio`, `Tool`

### MusicChartType

Represents which music chart to pull entries from, if any

Values: `None`, `Current`, `Week`, `Month`, `Year`

### DeleteSaveRequest

Request model for deleting a save

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `targetType` | `SearchCategoryType` | Yes | The type of asset being deleted |
| `targetId` | `integer` | Yes | The ID of the asset being deleted |
| `collectionName` | `string` | No | Custom collections are not currently supported. This field should be omitted. |

### HydratedSave

A save record, hydrated with the asset details.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `owned` | `boolean` | Yes | Whether the asset is owned by the user. |
| `dateSaved` | `string` | Yes | Date the save was added. |
| `creatorStoreAsset` | `CreatorStoreAsset` | Yes | The asset that was saved. |

### Google.Protobuf.WellKnownTypes.Any

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `typeUrl` | `string` | No |  |
| `value` | `integer[]` | No |  |

### MarketplaceFiatService.Money

Represents an amount of money with its currency type.

Examples:
 - Five US dollars === `{currency_code: "USD" quantity: {significand: 5}}`

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `currencyCode` | `string` | No | A currency code.  This may be a three-letter currency code defined in ISO 4217.  APIs may define additional currency codes that are not included in the ISO 4217 standard (for example, virtual currencies or cryptocurrencies). These must start with `X-`, in order to distinguish them from potential future ISO 4217 codes. For example, `"USD"` is the ISO 4217 code for United States dollar. |
| `quantity` | `MarketplaceFiatService.Decimal` | No | The quantity of currency. |

### MarketplaceFiatService.Decimal

Represents a decimal number in a form similar to scientific notation.

Examples:
 - 17            === `{significand: 17   exponent: 0} (or just {significand:
   17})`
 - -0.005        === `{significand: -5   exponent: -3}`
 - 33.5 million  === `{significand: 335  exponent: 5}`
 - 11/8 (1.375)  === `{significand: 1375 exponent: -3}`

Note that the range of a Decimal exceeds that of a JSON `number` (double), as
well as that of a `decimal64`.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `significand` | `integer` | No | The significant digits of the number. |
| `exponent` | `integer` | No | Represents the position of the decimal point within the significand.  When the exponent is 0, the value of the Decimal is simply the value of `significand`.  When the exponent is greater than 0, represents the number of trailing zeroes after the significant digits.  When the exponent is less than 0, represents how many of the significant digits (and implicit leading zeroes, as needed) come after the decmial point. |