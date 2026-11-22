<!-- Source: https://create.roblox.com/docs/cloud/reference/features/metadata.md -->

---
name: "Metadata"
last_updated: 2026-11-20T18:47:47Z
type: feature
api_base_url: "https://apis.roblox.com"
endpoints: 17
auth: [api-key, oauth2, cookie]
description: "Retrieve configuration metadata and system information from various Roblox services, including settings, quotas, and limits"
---

# Metadata

Retrieve configuration metadata and system information from various Roblox services, including settings, quotas, and limits.

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

### GET `/v1/autolocalization/metadata` *(deprecated)*

Metadata for AutoLocalization Configuration

Use the Autolocalization controller in LocalizationTables API

**Server:** `https://gameinternationalization.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Responses:**

- `200`: OK → `Roblox.GameInternationalization.Api.AutoLocalizationMetadataResponse`
- `401`: 0: Authorization has been denied for this request.

**Response fields** (`Roblox.GameInternationalization.Api.AutoLocalizationMetadataResponse`)

See [Roblox.GameInternationalization.Api.AutoLocalizationMetadataResponse](#roblox-gameinternationalization-api-autolocalizationmetadataresponse) in Models.

**Response example:**
```json
{
  "isReactVersionEnabledForAutoLocalizationSettings": false,
  "isTabbedUIEnabledForConfigureLocalizationPage": false,
  "isAutomaticTranslationToggleUIEnabled": false,
  "isAutomaticTranslationQuotaUIEnabled": false
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://gameinternationalization.roblox.com/v1/autolocalization/metadata"
```

### GET `/v1/client-version/{binaryType}` [EXPERIMENTAL]

Get client version information for specific binary type

**Server:** `https://clientsettings.roblox.com`

**Auth:** 

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `binaryType` | path | `string` | Yes | Platform(WindowsPlayer, WindowsStudio, MacPlayer or MacStudio) for which we want the latest version |

**Responses:**

- `200`: OK → `Roblox.ClientSettings.Api.Models.Response.ClientVersionResponse`

**Response fields** (`Roblox.ClientSettings.Api.Models.Response.ClientVersionResponse`)

See [Roblox.ClientSettings.Api.Models.Response.ClientVersionResponse](#roblox-clientsettings-api-models-response-clientversionresponse) in Models.

**Response example:**
```json
{
  "version": "string",
  "clientVersionUpload": "string",
  "bootstrapperVersion": "string",
  "nextClientVersionUpload": "string",
  "nextClientVersion": "string",
  "forceInstall": false
}
```

**Example:**
```bash
curl -H "Authorization: Bearer $ROBLOX_ACCESS_TOKEN" \
  "https://clientsettings.roblox.com/v1/client-version/{BINARYTYPE}"
```

### GET `/v1/installer-cdns` [EXPERIMENTAL]

Get information about which CDNs to use for installation.

**Server:** `https://clientsettings.roblox.com`

**Auth:** 

**Responses:**

- `200`: OK

**Example:**
```bash
curl -H "Authorization: Bearer $ROBLOX_ACCESS_TOKEN" \
  "https://clientsettings.roblox.com/v1/installer-cdns"
```

### GET `/v1/mobile-client-version` [EXPERIMENTAL]

Get mobile client version information based on app version parameter

**Server:** `https://clientsettings.roblox.com`

**Auth:** 

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `appVersion` | query | `string` | Yes | AppiOSV2.13, AppVersioniOS2.0.1, etc |

**Responses:**

- `200`: OK → `Roblox.ClientSettings.Api.Models.Response.MobileClientVersionResponse`
- `400`: 2: Invalid binaryType.

**Response fields** (`Roblox.ClientSettings.Api.Models.Response.MobileClientVersionResponse`)

See [Roblox.ClientSettings.Api.Models.Response.MobileClientVersionResponse](#roblox-clientsettings-api-models-response-mobileclientversionresponse) in Models.

**Response example:**
```json
{
  "activeVersion": "string",
  "upgradeSource": "string",
  "MD5Sum": "string",
  "data": {
    "UpgradeAction": "string"
  }
}
```

**Example:**
```bash
curl -H "Authorization: Bearer $ROBLOX_ACCESS_TOKEN" \
  "https://clientsettings.roblox.com/v1/mobile-client-version?appVersion={VALUE}"
```

### GET `/v1/vip-servers/{id}`

**Server:** `https://games.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `id` | path | `integer` | Yes |  |

**Responses:**

- `200`: OK → `PrivateServerResponse`

**Response fields** (`PrivateServerResponse`)

See [PrivateServerResponse](#privateserverresponse) in Models.

**Response example:**
```json
{
  "id": 0,
  "name": "string",
  "game": {
    "id": 0,
    "name": "string",
    "rootPlace": {
      "id": "...",
      "name": "..."
    }
  },
  "joinCode": "string",
  "active": false,
  "subscription": {
    "active": false,
    "expired": false,
    "expirationDate": "2024-01-01T00:00:00Z",
    "price": 0,
    "canRenew": false,
    "hasInsufficientFunds": false
  }
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://games.roblox.com/v1/vip-servers/{ID}"
```

### GET `/v2/android-binaries/{version}/channels/{channelName}`

Retrieve the Android binary information for a given version and channel name.

**Server:** `https://clientsettings.roblox.com`

**Auth:** 

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `version` | path | `string` | Yes | The version string of the application. i.e. 2.660.392 |
| `channelName` | path | `string` | Yes | The name of the channel. E.g. ZFlag, ZIntegration |

**Responses:**

- `200`: OK → `Roblox.ClientSettings.Api.Models.Response.AndroidBinaryResponse`

**Response fields** (`Roblox.ClientSettings.Api.Models.Response.AndroidBinaryResponse`)

See [Roblox.ClientSettings.Api.Models.Response.AndroidBinaryResponse](#roblox-clientsettings-api-models-response-androidbinaryresponse) in Models.

**Response example:**
```json
{
  "moduleName": "string",
  "libraryNames": {
    "engine": "string"
  },
  "supportsAndroidBinaries": false
}
```

**Example:**
```bash
curl -H "Authorization: Bearer $ROBLOX_ACCESS_TOKEN" \
  "https://clientsettings.roblox.com/v2/android-binaries/{VERSION}/channels/{CHANNELNAME}"
```

### GET `/v2/beta-program-channel-version`

Get the channel and current version guid of a beta program the currently logged in user may use, whether or not they are opted in to it.
Only desktop Studio and Player binary types (MacStudio, WindowsStudio64, MacPlayer, WindowsPlayer) are supported for now.

**Server:** `https://clientsettings.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `programId` | query | `string` | Yes | The beta program id |
| `binaryType` | query | `string` | Yes | e.g. MacStudio, WindowsStudio64, MacPlayer or WindowsPlayer |

**Responses:**

- `200`: OK → `Roblox.ClientSettings.Api.Models.Response.BetaProgramChannelVersionResponse`
- `400`: 2: Invalid binaryType. 7: Unsupported binaryType. 10: Missing or invalid beta program id.
- `401`: 5: Not authorized to perform this action.
- `403`: 5: Not authorized to perform this action.
- `404`: 1: Could not find version details for binaryType.
- `500`: 3: Error while fetching version information.

**Response fields** (`Roblox.ClientSettings.Api.Models.Response.BetaProgramChannelVersionResponse`)

See [Roblox.ClientSettings.Api.Models.Response.BetaProgramChannelVersionResponse](#roblox-clientsettings-api-models-response-betaprogramchannelversionresponse) in Models.

**Response example:**
```json
{
  "channelName": "string",
  "isFlagOnly": false,
  "clientVersionUpload": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://clientsettings.roblox.com/v2/beta-program-channel-version?programId={VALUE}&binaryType={VALUE}"
```

### GET `/v2/client-version/{binaryType}` [EXPERIMENTAL]

Get client version information for specific binary type

**Server:** `https://clientsettings.roblox.com`

**Auth:** 

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `binaryType` | path | `string` | Yes | Platform(WindowsPlayer, WindowsStudio, MacPlayer or MacStudio) for which we want the latest version |

**Responses:**

- `200`: OK → `Roblox.ClientSettings.Api.Models.Response.ClientVersionResponse`

**Response fields** (`Roblox.ClientSettings.Api.Models.Response.ClientVersionResponse`)

See [Roblox.ClientSettings.Api.Models.Response.ClientVersionResponse](#roblox-clientsettings-api-models-response-clientversionresponse) in Models.

**Response example:**
```json
{
  "version": "string",
  "clientVersionUpload": "string",
  "bootstrapperVersion": "string",
  "nextClientVersionUpload": "string",
  "nextClientVersion": "string",
  "forceInstall": false
}
```

**Example:**
```bash
curl -H "Authorization: Bearer $ROBLOX_ACCESS_TOKEN" \
  "https://clientsettings.roblox.com/v2/client-version/{BINARYTYPE}"
```

### GET `/v2/client-version/{binaryType}/channel/{channelName}` [EXPERIMENTAL]

Get client version information for specific binary type

**Server:** `https://clientsettings.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `binaryType` | path | `string` | Yes | Platform(WindowsPlayer, WindowsStudio, MacPlayer or MacStudio) for which we want the latest version |
| `channelName` | path | `string` | Yes | Channel Name |

**Responses:**

- `200`: OK → `Roblox.ClientSettings.Api.Models.Response.ClientVersionResponse`
- `401`: 5: Not authorized to perform this action.

**Response fields** (`Roblox.ClientSettings.Api.Models.Response.ClientVersionResponse`)

See [Roblox.ClientSettings.Api.Models.Response.ClientVersionResponse](#roblox-clientsettings-api-models-response-clientversionresponse) in Models.

**Response example:**
```json
{
  "version": "string",
  "clientVersionUpload": "string",
  "bootstrapperVersion": "string",
  "nextClientVersionUpload": "string",
  "nextClientVersion": "string",
  "forceInstall": false
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://clientsettings.roblox.com/v2/client-version/{BINARYTYPE}/channel/{CHANNELNAME}"
```

### GET `/v2/compression-dictionaries` [EXPERIMENTAL]

Returns a listing of all known compression dictionaries, including their SHA256 and creation date.
This will be sorted by creation date, with the most recent dictionaries first.

**Server:** `https://clientsettings.roblox.com`

**Auth:** 

**Responses:**

- `200`: OK

**Example:**
```bash
curl -H "Authorization: Bearer $ROBLOX_ACCESS_TOKEN" \
  "https://clientsettings.roblox.com/v2/compression-dictionaries"
```

### GET `/v2/compression-dictionaries/{dictionarySha256}` [EXPERIMENTAL]

Returns the specified compression dictionary as a file download.

**Server:** `https://clientsettings.roblox.com`

**Auth:** 

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `dictionarySha256` | path | `string` | Yes | The SHA256 of the dictionary we wish to download. |

**Responses:**

- `200`: OK

**Example:**
```bash
curl -H "Authorization: Bearer $ROBLOX_ACCESS_TOKEN" \
  "https://clientsettings.roblox.com/v2/compression-dictionaries/{DICTIONARYSHA256}"
```

### GET `/v2/ota-version/{binaryType}` [EXPERIMENTAL]

Get OTA information for a specific binary type with a given version on some channel.
When a named channel has no OTA config for that version, the version is ignored and the channel's config is returned.
Returns empty list if no updates are found or channel/application with the given version does not exist in CVS.

**Server:** `https://clientsettings.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `binaryType` | path | `string` | Yes | Binary type of the application to get info for |
| `channel` | query | `string` | No | Channel name. If not provided, production is assumed. |
| `version` | query | `string` | No | Application version. Optional when a named channel is set. Required for production. |
| `tag` | query | `string` | No | Tag to filter results by. Only applicable to non-studio application types. |
| `name` | query | `string` | No | Name to filter results by. Only applicable to non-studio application types. |

**Responses:**

- `200`: OK → `Roblox.ClientSettings.Api.Models.Response.OtaVersionResponse[]`
- `400`: 2: Invalid binaryType. 4: Invalid app version. 6: Missing or invalid channel. 7: Unsupported binaryType.
- `401`: 5: Not authorized to perform this action.
- `501`: 9: The requested tag is not implemented.

**Response fields** (`Roblox.ClientSettings.Api.Models.Response.OtaVersionResponse[]`)

See [Roblox.ClientSettings.Api.Models.Response.OtaVersionResponse](#roblox-clientsettings-api-models-response-otaversionresponse) in Models.

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://clientsettings.roblox.com/v2/ota-version/{BINARYTYPE}"
```

### GET `/v2/push-notifications/chrome-manifest` [EXPERIMENTAL]

Get Chrome Manifest to link GCM project to Chrome Browser

**Server:** `https://notifications.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Responses:**

- `200`: OK → `Roblox.Api.Notifications.Models.ChromeManifestModel`
- `401`: 0: Authorization has been denied for this request.

**Response fields** (`Roblox.Api.Notifications.Models.ChromeManifestModel`)

See [Roblox.Api.Notifications.Models.ChromeManifestModel](#roblox-api-notifications-models-chromemanifestmodel) in Models.

**Response example:**
```json
{
  "name": "string",
  "gcm_sender_id": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://notifications.roblox.com/v2/push-notifications/chrome-manifest"
```

### GET `/v2/push-notifications/get-current-device-destination` [EXPERIMENTAL]

Gets the current device destination

**Server:** `https://notifications.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Responses:**

- `200`: OK → `Roblox.Api.Notifications.Models.GetCurrentPushDestinationResponseModel`
- `401`: 0: Authorization has been denied for this request.

**Response fields** (`Roblox.Api.Notifications.Models.GetCurrentPushDestinationResponseModel`)

See [Roblox.Api.Notifications.Models.GetCurrentPushDestinationResponseModel](#roblox-api-notifications-models-getcurrentpushdestinationresponsemodel) in Models.

**Response example:**
```json
{
  "destination": {
    "user": {
      "name": "...",
      "userId": "..."
    },
    "name": "string",
    "notificationToken": "string",
    "supportsUpdateNotifications": false,
    "userPushNotificationDestinationId": 0,
    "application": "string"
  },
  "statusMessage": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://notifications.roblox.com/v2/push-notifications/get-current-device-destination"
```

### GET `/v2/push-notifications/metadata` [EXPERIMENTAL]

Gets the corresponding metadata for the specified notification

**Server:** `https://notifications.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `notificationToken` | query | `string` | Yes | Token for the notification |
| `notificationId` | query | `string` | Yes | Id of the specified notification |

**Responses:**

- `200`: OK → `Roblox.Api.Notifications.Models.GetMetadataResponseModel`
- `401`: 0: Authorization has been denied for this request.

**Response fields** (`Roblox.Api.Notifications.Models.GetMetadataResponseModel`)

See [Roblox.Api.Notifications.Models.GetMetadataResponseModel](#roblox-api-notifications-models-getmetadataresponsemodel) in Models.

**Response example:**
```json
{
  "metadata": {
    "notificationId": "string",
    "type": "string",
    "detail": "...",
    "fallbackDelivered": false
  },
  "statusMessage": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://notifications.roblox.com/v2/push-notifications/metadata?notificationToken={VALUE}&notificationId={VALUE}"
```

### GET `/v2/stream-notifications/metadata` [EXPERIMENTAL]

Get Notification Stream metadata.

**Server:** `https://notifications.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Responses:**

- `200`: OK → `Roblox.Api.Notifications.Models.ResponseModels.NotificationStreamMetadataResponse`
- `401`: 0: Authorization has been denied for this request.

**Response fields** (`Roblox.Api.Notifications.Models.ResponseModels.NotificationStreamMetadataResponse`)

See [Roblox.Api.Notifications.Models.ResponseModels.NotificationStreamMetadataResponse](#roblox-api-notifications-models-responsemodels-notificationstreammetadataresponse) in Models.

**Response example:**
```json
{
  "bannerDismissTimeSpan": 0,
  "signalRDisconnectionResponseInMilliseconds": 0,
  "canLaunchGameFromGameUpdate": false
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://notifications.roblox.com/v2/stream-notifications/metadata"
```

### GET `/v2/user-channel` [EXPERIMENTAL]

Get channel name for currently logged in user

**Server:** `https://clientsettings.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `binaryType` | query | `string` | No |  |

**Responses:**

- `200`: OK → `Roblox.ClientSettings.Api.Models.Response.UserChannelResponse`

**Response fields** (`Roblox.ClientSettings.Api.Models.Response.UserChannelResponse`)

See [Roblox.ClientSettings.Api.Models.Response.UserChannelResponse](#roblox-clientsettings-api-models-response-userchannelresponse) in Models.

**Response example:**
```json
{
  "channelName": "string",
  "channelAssignmentType": 0,
  "token": "string",
  "program": {
    "name": "string",
    "id": "string"
  },
  "isFlagOnly": false
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://clientsettings.roblox.com/v2/user-channel"
```

## Models

### Roblox.GameInternationalization.Api.AutoLocalizationMetadataResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `isReactVersionEnabledForAutoLocalizationSettings` | `boolean` | No | Is React Implementation of AutoLocalization Settings Enabled |
| `isTabbedUIEnabledForConfigureLocalizationPage` | `boolean` | No | Is Tabbed UI Enabled for Configure Localization Page |
| `isAutomaticTranslationToggleUIEnabled` | `boolean` | No | Is Toggle UI Enabled for Automatic Translations |
| `isAutomaticTranslationQuotaUIEnabled` | `boolean` | No | Is Quota UI Enabled for Automatic Translations |

### Roblox.ClientSettings.Api.Models.Response.ClientVersionResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `version` | `string` | No |  |
| `clientVersionUpload` | `string` | No |  |
| `bootstrapperVersion` | `string` | No |  |
| `nextClientVersionUpload` | `string` | No |  |
| `nextClientVersion` | `string` | No |  |
| `forceInstall` | `boolean` | No |  |

### Roblox.ClientSettings.Api.Models.Response.MobileClientVersionResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `activeVersion` | `string` | No |  |
| `upgradeSource` | `string` | No |  |
| `MD5Sum` | `string` | No |  |
| `data` | `Roblox.ClientSettings.Api.Models.Response.MobileClientVersionResponseData` | No |  |

### PrivateServerResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No |  |
| `name` | `string` | No |  |
| `game` | `GameResponse` | No |  |
| `joinCode` | `string` | No |  |
| `active` | `boolean` | No |  |
| `subscription` | `PrivateServerSubscriptionResponse` | No |  |
| `permissions` | `PrivateServerPermissionsResponse` | No |  |
| `link` | `string` | No |  |

### Roblox.ClientSettings.Api.Models.Response.AndroidBinaryResponse

Contains information about an Android Binary Module for a given channel.
including its module name, the names of its libraries, and whether the channel supports Android binaries.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `moduleName` | `string` | No | The name of the Android Binary Module. |
| `libraryNames` | `Roblox.ClientSettings.Api.Models.Response.AndroidBinaryLibraryNames` | Yes |  |
| `supportsAndroidBinaries` | `boolean` | No | True if the channel supports android binaries. False otherwise. |

### Roblox.ClientSettings.Api.Models.Response.BetaProgramChannelVersionResponse

The channel of a beta program and its current version guid.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `channelName` | `string` | Yes | Name of the channel. |
| `isFlagOnly` | `boolean` | Yes | Whether the channel is flag-only, i.e. uses production binaries. |
| `clientVersionUpload` | `string` | Yes | The channel's current client version upload. For flag-only channels, this is production's. |

### Roblox.ClientSettings.Api.Models.Response.OtaVersionResponse

Response for endpoints returning ota information.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `name` | `string` | Yes | Ota library/plugin name |
| `version` | `string` | Yes | Version number of asset |
| `downloadUrl` | `string` | Yes | URL to download the ota asset |
| `isStandalone` | `boolean` | No | Refers to whether the plugin is core to Studio functions, and is used to determine when it is loaded. |
| `assetId` | `string` | No | The asset ID of the LuaApp OTA. |
| `assetVersion` | `string` | No | The asset version of the LuaApp OTA. |
| `maxAppVersion` | `string` | No | The maximum application version compatible with the LuaApp OTA. |
| `tryoutName` | `string` | No | The name of the tryout for the LuaApp OTA. |
| `localAssetURI` | `string` | No | The local asset URI for the LuaApp OTA. |
| `isForcedUpdate` | `boolean` | No | Indicates whether the LuaApp OTA is a forced update. |
| `appStorageResetId` | `string` | No | The application storage reset ID for the LuaApp OTA. |
| `isDevelopmentConfig` | `boolean` | No | Indicates whether the LuaApp OTA is a development configuration. |
| `assetsManifest` | `object` | No | Inlined assets manifest for the LuaApp OTA. |
| `versionV2` | `integer` | No | VersionV2 of the OTA asset. |

### Roblox.Api.Notifications.Models.ChromeManifestModel

Chrome Manifest to link GCM project to Chrome browser

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `name` | `string` | No |  |
| `gcm_sender_id` | `string` | No |  |

### Roblox.Api.Notifications.Models.GetCurrentPushDestinationResponseModel

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `destination` | `Roblox.Api.Notifications.Models.UserPushDestination` | No |  |
| `statusMessage` | `string` | No | Message for the success response |

### Roblox.Api.Notifications.Models.GetMetadataResponseModel

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `metadata` | `Roblox.Api.Notifications.Models.PushNotificationClientMetadata` | No |  |
| `statusMessage` | `string` | No | Message for the success response |

### Roblox.Api.Notifications.Models.ResponseModels.NotificationStreamMetadataResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `bannerDismissTimeSpan` | `integer` | No |  |
| `signalRDisconnectionResponseInMilliseconds` | `integer` | No |  |
| `canLaunchGameFromGameUpdate` | `boolean` | No |  |

### Roblox.ClientSettings.Api.Models.Response.UserChannelResponse

Response data object for getting a user's channel information.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `channelName` | `string` | No | Name of the channel. |
| `channelAssignmentType` | `integer enum (6 values)` | No | How the user was bound to the channel. If the user is not assigned to any channel, this is omitted. ['None' = 0, 'PerMille' = 1, 'BoundToPrivateChannel' = 2, 'BoundToPublicChannel' = 3, 'OptedInToBetaProgramWithPrivateChannel' = 4, 'OptedInToBetaProgramWithPublicChannel' = 5] Values: 0, 1, 2, 3, 4, 5 |
| `token` | `string` | No | JWT token. If the channel is not private, this is omitted. |
| `program` | `Roblox.ClientSettings.Api.Models.Response.BetaProgramInfo` | No |  |
| `isFlagOnly` | `boolean` | No | Whether the channel is flag-only. A flag-only channel uses production binaries. If the channel is not flag-only, this is omitted. |

### Roblox.ClientSettings.Api.Models.Response.BetaProgramInfo

Beta program information included in the user channel response.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `name` | `string` | Yes | The display name of the beta program. |
| `id` | `string` | Yes | The ID of the beta program. |

### Roblox.Api.Notifications.Models.PushNotificationClientMetadata

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `notificationId` | `string` | No | Id for the push client notification |
| `type` | `string` | No | Type of the push client notification |
| `detail` | `any` | No | Details corresponding to the notification |
| `fallbackDelivered` | `boolean` | No | Is fallback delivered for the notification metadata |

### Roblox.Api.Notifications.Models.UserPushDestination

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `user` | `Roblox.Api.Notifications.Models.NotificationUser` | No |  |
| `name` | `string` | No | Name of the destination |
| `notificationToken` | `string` | No | Token for the corresponding notification |
| `supportsUpdateNotifications` | `boolean` | No | Is Update notification feature supported |
| `userPushNotificationDestinationId` | `integer` | No | Destination Id for the push notification |
| `application` | `string` | No | application for the corresponding notification Example : "Roblox" |
| `platform` | `string enum (8 values)` | No | Platform for the corresponding notification ['ChromeOnDesktop' = 0, 'AndroidNative' = 1, 'FirefoxOnDesktop' = 2, 'IOSNative' = 3, 'AndroidAmazon' = 4, 'IOSTencent' = 5, 'AndroidTencentService' = 6, 'IOSPushKit' = 7] Values: ChromeOnDesktop, AndroidNative, FirefoxOnDesktop, IOSNative, AndroidAmazon, IOSTencent, AndroidTencentService, IOSPushKit |

### Roblox.Api.Notifications.Models.NotificationUser

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `name` | `string` | No | Name of the user |
| `userId` | `integer` | No | Id of the user |

### Roblox.ClientSettings.Api.Models.Response.AndroidBinaryLibraryNames

Contains the names of the libraries in an Android Binary Module.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `engine` | `string` | No | Name of the engine library. |

### GameResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No |  |
| `name` | `string` | No |  |
| `rootPlace` | `PlaceResponse` | No |  |

### PrivateServerSubscriptionResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `active` | `boolean` | No |  |
| `expired` | `boolean` | No |  |
| `expirationDate` | `string` | No |  |
| `price` | `integer` | No |  |
| `canRenew` | `boolean` | No |  |
| `hasInsufficientFunds` | `boolean` | No |  |
| `hasRecurringProfile` | `boolean` | No |  |
| `hasPriceChanged` | `boolean` | No |  |
| `purchaseScheduleId` | `integer` | No |  |
| `totalDiscountAmountInRobux` | `integer` | No |  |
| `metadata` | `PrivateServerSubscriptionMetadata` | No |  |

### PrivateServerPermissionsResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `clanAllowed` | `boolean` | No |  |
| `enemyClanId` | `integer` | No |  |
| `friendsAllowed` | `boolean` | No |  |
| `users` | `SkinnyUserResponse[]` | No |  |

### SkinnyUserResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No |  |
| `name` | `string` | No |  |
| `displayName` | `string` | No |  |

### PrivateServerSubscriptionMetadata

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `privateServerSubscriptionTags` | `PrivateServerSubscriptionTag[]` | No |  |

### PrivateServerSubscriptionTag

Values: `Invalid`, `RobloxSubscription`, `RobloxSubscriptionActiveBenefit`

### PlaceResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No |  |
| `name` | `string` | No |  |

### Roblox.ClientSettings.Api.Models.Response.MobileClientVersionResponseData

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `UpgradeAction` | `string` | No |  |