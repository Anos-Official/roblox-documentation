<!-- Source: https://create.roblox.com/docs/cloud/reference/features/notifications.md -->

---
name: "Notifications"
last_updated: 2026-11-20T18:47:47Z
type: feature
api_base_url: "https://apis.roblox.com"
endpoints: 18
auth: [api-key, oauth2, cookie]
description: "Send personalized notifications to re-engage players and keep them informed about your experience"
---

# Notifications

Send personalized notifications to re-engage players and keep them informed about your experience. Each user can receive one notification per day from a given experience. See the [Experience Notifications Guide](/cloud/guides/experience-notifications).

Common use cases include:

- Experience notifications: [Send targeted notifications](#Cloud_CreateUserNotification) to users about in-game events, rewards, or updates
- Notification configuration: [Create](#NotificationsDeveloperConfiguration_CreateNotificationString), [list](#NotificationsDeveloperConfiguration_ExperienceNotificationsList), [retrieve](#NotificationsDeveloperConfiguration_ExperienceNotification), [update](#NotificationsDeveloperConfiguration_UpdateNotificationString), and [archive](#NotificationsDeveloperConfiguration_ArchiveNotificationString) message templates
- Notification analytics: [Review aggregated experience notification analytics](#NotificationsAggregatedAnalytics_ExperienceNotification) to measure notification performance
- Personalized messages: Customize notifications with dynamic parameters like usernames and scores
- **Launch Data Integration**: Include launch data to route users to specific locations when they join

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

### POST `/cloud/v2/users/{user_id}/notifications` [STABLE]

Create User Notification

Sends a notification to a user.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `user.user-notification:write`, `user.user-notification:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `user_id` | path | `string` | Yes | The user ID. |

**Request Body:** `application/json` — Type: `UserNotification`

See [UserNotification](#usernotification) in Models.

**Request example:**
```json
{
  "path": "string",
  "id": "string",
  "source": {
    "universe": "string"
  },
  "payload": {
    "type": "TYPE_UNSPECIFIED",
    "messageId": "string",
    "parameters": "...",
    "joinExperience": {
      "launchData": "..."
    },
    "analyticsData": {
      "category": "..."
    }
  }
}
```

**Responses:**

- `200`: OK → `UserNotification`

**Response fields** (`UserNotification`)

See [UserNotification](#usernotification) in Models.

**Response example:**
```json
{
  "path": "string",
  "id": "string",
  "source": {
    "universe": "string"
  },
  "payload": {
    "type": "TYPE_UNSPECIFIED",
    "messageId": "string",
    "parameters": "...",
    "joinExperience": {
      "launchData": "..."
    },
    "analyticsData": {
      "category": "..."
    }
  }
}
```

**Rate Limits:** perApiKeyOwner: 4000/second, perOauth2Authorization: 4000/second

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/users/{USER_ID}/notifications" \
  -H "Content-Type: application/json" \
  -d '{
  "path": "string",
  "id": "string",
  "source": {
    "universe": "string"
  },
  "payload": {
    "type": "TYPE_UNSPECIFIED",
    "messageId": "string",
    "parameters": "...",
    "joinExperience": {
      "launchData": "..."
    },
    "analyticsData": {
      "category": "..."
    }
  }
}'
```

### POST `/notifications/v1/developer-configuration/archive-notification` [EXPERIMENTAL]

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `universe.notification-string:write`

**Request Body:** `application/json-patch+json` — Type: `ArchiveNotificationStringRequest`

See [ArchiveNotificationStringRequest](#archivenotificationstringrequest) in Models.

**Request example:**
```json
{
  "id": "string"
}
```

**Responses:**

- `200`: OK

**Rate Limits:** perApiKeyOwner: 100/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/notifications/v1/developer-configuration/archive-notification" \
  -H "Content-Type: application/json" \
  -d '{
  "id": "string"
}'
```

### POST `/notifications/v1/developer-configuration/create-notification` [EXPERIMENTAL]

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `universe.notification-string:write`

**Request Body:** `application/json-patch+json` — Type: `CreateNotificationStringRequest`

See [CreateNotificationStringRequest](#createnotificationstringrequest) in Models.

**Request example:**
```json
{
  "name": "string",
  "content": "string",
  "universeId": 0
}
```

**Responses:**

- `200`: OK → `CreateNotificationStringResponse`

**Response fields** (`CreateNotificationStringResponse`)

See [CreateNotificationStringResponse](#createnotificationstringresponse) in Models.

**Response example:**
```json
{
  "id": "string"
}
```

**Rate Limits:** perApiKeyOwner: 100/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/notifications/v1/developer-configuration/create-notification" \
  -H "Content-Type: application/json" \
  -d '{
  "name": "string",
  "content": "string",
  "universeId": 0
}'
```

### GET `/notifications/v1/developer-configuration/experience-notification` [EXPERIMENTAL]

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `universe.notification-string:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `Id` | query | `string` | No |  |

**Responses:**

- `200`: OK → `ConfigureExperienceNotificationResponse`

**Response fields** (`ConfigureExperienceNotificationResponse`)

See [ConfigureExperienceNotificationResponse](#configureexperiencenotificationresponse) in Models.

**Response example:**
```json
{
  "id": "string",
  "name": "string",
  "content": "string"
}
```

**Rate Limits:** perApiKeyOwner: 1200/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/notifications/v1/developer-configuration/experience-notification"
```

### GET `/notifications/v1/developer-configuration/experience-notifications-list` [EXPERIMENTAL]

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `universe.notification-string:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `UniverseId` | query | `integer` | No |  |
| `Count` | query | `integer` | No |  |
| `Cursor` | query | `string` | No |  |
| `Previous` | query | `boolean` | No |  |
| `ReverseOrder` | query | `boolean` | No |  |

**Responses:**

- `200`: OK → `ConfigureExperienceNotificationsListResponse`

**Response fields** (`ConfigureExperienceNotificationsListResponse`)

See [ConfigureExperienceNotificationsListResponse](#configureexperiencenotificationslistresponse) in Models.

**Response example:**
```json
{
  "notificationStringConfigs": [
    {
      "id": "...",
      "name": "...",
      "content": "..."
    }
  ],
  "previousPageCursor": "string",
  "nextPageCursor": "string"
}
```

**Rate Limits:** perApiKeyOwner: 200/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/notifications/v1/developer-configuration/experience-notifications-list"
```

### POST `/notifications/v1/developer-configuration/update-notification` [EXPERIMENTAL]

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `universe.notification-string:write`

**Request Body:** `application/json-patch+json` — Type: `UpdateNotificationStringRequest`

See [UpdateNotificationStringRequest](#updatenotificationstringrequest) in Models.

**Request example:**
```json
{
  "id": "string",
  "name": "string",
  "content": "string"
}
```

**Responses:**

- `200`: OK

**Rate Limits:** perApiKeyOwner: 100/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/notifications/v1/developer-configuration/update-notification" \
  -H "Content-Type: application/json" \
  -d '{
  "id": "string",
  "name": "string",
  "content": "string"
}'
```

### POST `/notifications/v1/report-notification` [EXPERIMENTAL]

**Auth:** Cookie (`.ROBLOSECURITY`) or API Key (`x-api-key` header)

**Scopes:** `notification-report:write`

**Request Body:** `application/json-patch+json` — Type: `ReportNotificationRequest`

See [ReportNotificationRequest](#reportnotificationrequest) in Models.

**Request example:**
```json
{
  "notificationId": "string"
}
```

**Responses:**

- `200`: OK

**Rate Limits:** perApiKeyOwner: 100/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/notifications/v1/report-notification" \
  -H "Content-Type: application/json" \
  -d '{
  "notificationId": "string"
}'
```

### POST `/v2/push-notifications/deregister-all-devices`

De-register all devices to disable push notifications

**Server:** `https://notifications.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Responses:**

- `200`: OK → `Roblox.Api.Notifications.Models.SuccessResponseModel`
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed

**Response fields** (`Roblox.Api.Notifications.Models.SuccessResponseModel`)

See [Roblox.Api.Notifications.Models.SuccessResponseModel](#roblox-api-notifications-models-successresponsemodel) in Models.

**Response example:**
```json
{
  "statusMessage": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://notifications.roblox.com/v2/push-notifications/deregister-all-devices"
```

### POST `/v2/push-notifications/deregister-current-device`

De-register current device to disable push notifications

**Server:** `https://notifications.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Responses:**

- `200`: OK → `Roblox.Api.Notifications.Models.SuccessResponseModel`
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed

**Response fields** (`Roblox.Api.Notifications.Models.SuccessResponseModel`)

See [Roblox.Api.Notifications.Models.SuccessResponseModel](#roblox-api-notifications-models-successresponsemodel) in Models.

**Response example:**
```json
{
  "statusMessage": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://notifications.roblox.com/v2/push-notifications/deregister-current-device"
```

### POST `/v2/push-notifications/deregister-current-device-ios-pushkit`

De-register current device to disable pushkit notifications

**Server:** `https://notifications.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Responses:**

- `200`: OK → `Roblox.Api.Notifications.Models.SuccessResponseModel`
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed

**Response fields** (`Roblox.Api.Notifications.Models.SuccessResponseModel`)

See [Roblox.Api.Notifications.Models.SuccessResponseModel](#roblox-api-notifications-models-successresponsemodel) in Models.

**Response example:**
```json
{
  "statusMessage": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://notifications.roblox.com/v2/push-notifications/deregister-current-device-ios-pushkit"
```

### POST `/v2/push-notifications/register-android-native`

Register Android Native for push notifications

**Server:** `https://notifications.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Request Body:** `application/json` — Type: `Roblox.Api.Notifications.Models.RegisterAndroidRequestModel`

See [Roblox.Api.Notifications.Models.RegisterAndroidRequestModel](#roblox-api-notifications-models-registerandroidrequestmodel) in Models.

**Request example:**
```json
{
  "notificationToken": "string",
  "authorizeForUser": false,
  "oldNotificationToken": "string",
  "deviceName": "string"
}
```

**Responses:**

- `200`: OK → `Roblox.Api.Notifications.Models.RegistrationResponseModel`
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed

**Response fields** (`Roblox.Api.Notifications.Models.RegistrationResponseModel`)

See [Roblox.Api.Notifications.Models.RegistrationResponseModel](#roblox-api-notifications-models-registrationresponsemodel) in Models.

**Response example:**
```json
{
  "registration": {
    "userPushNotificationDestinationId": 0,
    "name": "string",
    "notificationToken": "string",
    "application": "string",
    "platform": "ChromeOnDesktop"
  },
  "statusMessage": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://notifications.roblox.com/v2/push-notifications/register-android-native" \
  -H "Content-Type: application/json" \
  -d '{
  "notificationToken": "string",
  "authorizeForUser": false,
  "oldNotificationToken": "string",
  "deviceName": "string"
}'
```

### POST `/v2/push-notifications/register-ios-native`

Registers IOS device for push notifications

**Server:** `https://notifications.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Request Body:** `application/json` — Type: `Roblox.Api.Notifications.Models.RegisterIOSNativeRequestModel`

See [Roblox.Api.Notifications.Models.RegisterIOSNativeRequestModel](#roblox-api-notifications-models-registeriosnativerequestmodel) in Models.

**Request example:**
```json
{
  "notificationToken": "string",
  "destinationIdentifier": "string",
  "authorizeForUser": false,
  "oldNotificationToken": "string",
  "deviceName": "string",
  "isProvisional": false
}
```

**Responses:**

- `200`: OK → `Roblox.Api.Notifications.Models.RegistrationResponseModel`
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed

**Response fields** (`Roblox.Api.Notifications.Models.RegistrationResponseModel`)

See [Roblox.Api.Notifications.Models.RegistrationResponseModel](#roblox-api-notifications-models-registrationresponsemodel) in Models.

**Response example:**
```json
{
  "registration": {
    "userPushNotificationDestinationId": 0,
    "name": "string",
    "notificationToken": "string",
    "application": "string",
    "platform": "ChromeOnDesktop"
  },
  "statusMessage": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://notifications.roblox.com/v2/push-notifications/register-ios-native" \
  -H "Content-Type: application/json" \
  -d '{
  "notificationToken": "string",
  "destinationIdentifier": "string",
  "authorizeForUser": false,
  "oldNotificationToken": "string",
  "deviceName": "string",
  "isProvisional": false
}'
```

### POST `/v2/push-notifications/register-ios-pushkit`

Registers IOS device for pushkit notifications

**Server:** `https://notifications.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Request Body:** `application/json` — Type: `Roblox.Api.Notifications.Models.RegisterIOSPushKitRequestModel`

See [Roblox.Api.Notifications.Models.RegisterIOSPushKitRequestModel](#roblox-api-notifications-models-registeriospushkitrequestmodel) in Models.

**Request example:**
```json
{
  "notificationToken": "string",
  "destinationIdentifier": "string",
  "authorizeForUser": false,
  "oldNotificationToken": "string",
  "deviceName": "string"
}
```

**Responses:**

- `200`: OK → `Roblox.Api.Notifications.Models.RegistrationResponseModel`
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed

**Response fields** (`Roblox.Api.Notifications.Models.RegistrationResponseModel`)

See [Roblox.Api.Notifications.Models.RegistrationResponseModel](#roblox-api-notifications-models-registrationresponsemodel) in Models.

**Response example:**
```json
{
  "registration": {
    "userPushNotificationDestinationId": 0,
    "name": "string",
    "notificationToken": "string",
    "application": "string",
    "platform": "ChromeOnDesktop"
  },
  "statusMessage": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://notifications.roblox.com/v2/push-notifications/register-ios-pushkit" \
  -H "Content-Type: application/json" \
  -d '{
  "notificationToken": "string",
  "destinationIdentifier": "string",
  "authorizeForUser": false,
  "oldNotificationToken": "string",
  "deviceName": "string"
}'
```

### POST `/v2/stream-notifications/clear-unread` [EXPERIMENTAL]

Clears the unread Notification stream count

**Server:** `https://notifications.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Responses:**

- `200`: OK → `Roblox.Api.Notifications.Models.SuccessResponseModel`
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed

**Response fields** (`Roblox.Api.Notifications.Models.SuccessResponseModel`)

See [Roblox.Api.Notifications.Models.SuccessResponseModel](#roblox-api-notifications-models-successresponsemodel) in Models.

**Response example:**
```json
{
  "statusMessage": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://notifications.roblox.com/v2/stream-notifications/clear-unread"
```

### GET `/v2/stream-notifications/get-latest-game-updates` [EXPERIMENTAL]

Get the latest non aggregated Game Updates sent to the logged in user

**Server:** `https://notifications.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeIds` | query | `integer[]` | Yes | List of universe IDs |
| `sinceDateTime` | query | `string` | No | For retrieving only updates that created after a time point. |

**Responses:**

- `200`: OK → `Roblox.Api.Notifications.Models.GameUpdateNotificationModel[]`
- `401`: 0: Authorization has been denied for this request.

**Response fields** (`Roblox.Api.Notifications.Models.GameUpdateNotificationModel[]`)

See [Roblox.Api.Notifications.Models.GameUpdateNotificationModel](#roblox-api-notifications-models-gameupdatenotificationmodel) in Models.

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://notifications.roblox.com/v2/stream-notifications/get-latest-game-updates?universeIds={VALUE}"
```

### GET `/v2/stream-notifications/get-recent` [EXPERIMENTAL]

Gets the recent entries from the notification stream

**Server:** `https://notifications.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `startIndex` | query | `integer` | No | Index to start the entries from. (Optional : Defaults to 0 which means the most recent entry) |
| `maxRows` | query | `integer` | No | Number of entries to be returned. (Optional : Defaults to 10 entries) |

**Responses:**

- `200`: OK → `Roblox.Api.Notifications.Models.NotificationStreamEntriesModel[]`
- `401`: 0: Authorization has been denied for this request.

**Response fields** (`Roblox.Api.Notifications.Models.NotificationStreamEntriesModel[]`)

See [Roblox.Api.Notifications.Models.NotificationStreamEntriesModel](#roblox-api-notifications-models-notificationstreamentriesmodel) in Models.

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://notifications.roblox.com/v2/stream-notifications/get-recent"
```

### POST `/v2/stream-notifications/page` [EXPERIMENTAL]

**Server:** `https://notifications.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Request Body:** `application/json` — Type: `Roblox.AppPagePlatform.Notifications.V1Beta1.StreamPageRequest`

See [Roblox.AppPagePlatform.Notifications.V1Beta1.StreamPageRequest](#roblox-apppageplatform-notifications-v1beta1-streampagerequest) in Models.

**Request example:**
```json
{
  "Cursor": "string",
  "MaxRows": 0,
  "NotificationId": "string",
  "HasNotificationId": false,
  "State": "string",
  "HasState": false
}
```

**Responses:**

- `200`: OK
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://notifications.roblox.com/v2/stream-notifications/page" \
  -H "Content-Type: application/json" \
  -d '{
  "Cursor": "string",
  "MaxRows": 0,
  "NotificationId": "string",
  "HasNotificationId": false,
  "State": "string",
  "HasState": false
}'
```

### GET `/v2/stream-notifications/unread-count` [EXPERIMENTAL]

Gets the count of unread Notification stream entries

**Server:** `https://notifications.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Responses:**

- `200`: OK → `Roblox.Api.Notifications.Models.UnreadStreamNotificationsModel`
- `401`: 0: Authorization has been denied for this request.

**Response fields** (`Roblox.Api.Notifications.Models.UnreadStreamNotificationsModel`)

See [Roblox.Api.Notifications.Models.UnreadStreamNotificationsModel](#roblox-api-notifications-models-unreadstreamnotificationsmodel) in Models.

**Response example:**
```json
{
  "unreadNotifications": 0,
  "statusMessage": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://notifications.roblox.com/v2/stream-notifications/unread-count"
```

## Models

### UserNotification

Represents a notification sent to a user.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `path` | `string` | No | The resource path of the user notification.  Format: `users/{user_id}/notifications/{user_notification_id}` |
| `id` | `string` | No | A unique UUID of the user notification. |
| `source` | `UserNotification_Source` | No | The source of the notification. |
| `payload` | `UserNotification_Payload` | No | The notification payload. |

### ArchiveNotificationStringRequest

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `string` | No |  |

### CreateNotificationStringRequest

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `name` | `string` | Yes |  |
| `content` | `string` | Yes |  |
| `universeId` | `integer` | Yes |  |

### CreateNotificationStringResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `string` | No |  |

### ConfigureExperienceNotificationResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `string` | No |  |
| `name` | `string` | No |  |
| `content` | `string` | No |  |

### ConfigureExperienceNotificationsListResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `notificationStringConfigs` | `ConfigureExperienceNotificationResponse[]` | No |  |
| `previousPageCursor` | `string` | No |  |
| `nextPageCursor` | `string` | No |  |

### UpdateNotificationStringRequest

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `string` | Yes |  |
| `name` | `string` | No |  |
| `content` | `string` | No |  |

### ReportNotificationRequest

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `notificationId` | `string` | No |  |

### Roblox.Api.Notifications.Models.SuccessResponseModel

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `statusMessage` | `string` | No | Message for the success response |

### Roblox.Api.Notifications.Models.RegisterAndroidRequestModel

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `notificationToken` | `string` | No | Token for notification |
| `authorizeForUser` | `boolean` | No | Is this call authorized for user |
| `oldNotificationToken` | `string` | No | Old notification token |
| `deviceName` | `string` | No | Name of the requesting device |

### Roblox.Api.Notifications.Models.RegistrationResponseModel

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `registration` | `Roblox.Api.Notifications.Models.PushNotificationRegistration` | No |  |
| `statusMessage` | `string` | No | Message for the success response |

### Roblox.Api.Notifications.Models.RegisterIOSNativeRequestModel

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `notificationToken` | `string` | No | Token for notification |
| `destinationIdentifier` | `string` | No | Identifier string for the destination |
| `authorizeForUser` | `boolean` | No | Is call authorized for user |
| `oldNotificationToken` | `string` | No | Old notification token |
| `deviceName` | `string` | No | Name of the requesting device |
| `isProvisional` | `boolean` | No | True when the client granted iOS provisional authorization (silent, quiet-only) rather than full authorization. Absent/null is treated as not provisional. |

### Roblox.Api.Notifications.Models.RegisterIOSPushKitRequestModel

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `notificationToken` | `string` | No | Token for notification |
| `destinationIdentifier` | `string` | No | Identifier string for the destination |
| `authorizeForUser` | `boolean` | No | Is call authorized for user |
| `oldNotificationToken` | `string` | No | Old notification token |
| `deviceName` | `string` | No | Name of the requesting device |

### Roblox.Api.Notifications.Models.GameUpdateNotificationModel

Model for a game update message to be displayed in notification stream.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `universeId` | `integer` | No | ID of the game. |
| `rootPlaceId` | `integer` | No | ID of the game. |
| `createdOn` | `string` | No | Creation date of the update message. |
| `createdOnKey` | `string` | No | Key of Creation date ticks (dynamo table sort key). |
| `content` | `string` | No | Content of the update message. |
| `universeName` | `string` | No | Name of the game. |

### Roblox.Api.Notifications.Models.NotificationStreamEntriesModel

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `string` | No | Id of the notification stream entry |
| `notificationSourceType` | `string enum (15 values)` | No | Type of the notification source ['Test' = 0, 'FriendRequestReceived' = 1, 'FriendRequestAccepted' = 2, 'PartyInviteReceived' = 3, 'PartyMemberJoined' = 4, 'ChatNewMessage' = 5, 'PrivateMessageReceived' = 6, 'UserAddedToPrivateServerWhiteList' = 7, 'ConversationUniverseChanged' = 8, 'TeamCreateInvite' = 9, 'GameUpdate' = 10, 'DeveloperMetricsAvailable' = 11, 'GroupJoinRequestAccepted' = 12, 'Sendr' = 13, 'ExperienceInvitation' = 14] Values: Test, FriendRequestReceived, FriendRequestAccepted, PartyInviteReceived, PartyMemberJoined, ChatNewMessage, PrivateMessageReceived, UserAddedToPrivateServerWhiteList, ConversationUniverseChanged, TeamCreateInvite, GameUpdate, DeveloperMetricsAvailable, GroupJoinRequestAccepted, Sendr, ExperienceInvitation |
| `eventDate` | `string` | No | Datetime when the notification stream entry event had occured |
| `timestamp` | `string` | No | Relative timestamp for sendr notification stream entry |
| `isInteracted` | `boolean` | No | Has the user interacted with the notification stream entry |
| `metadataCollection` | `any[]` | No | List of metadata objects showing more details related to the notification stream entry |
| `eventCount` | `integer` | No | Count of events corresponding to the group of notification stream entry |
| `content` | `any` | No | Content object for sendr notification stream entry |

### Roblox.AppPagePlatform.Notifications.V1Beta1.StreamPageRequest

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `Cursor` | `string` | No |  |
| `MaxRows` | `integer` | No |  |
| `NotificationId` | `string` | No |  |
| `HasNotificationId` | `boolean` | No |  |
| `State` | `string` | No |  |
| `HasState` | `boolean` | No |  |
| `ClientCapabilities` | `Roblox.AppPagePlatform.Shared.V1Beta1.ClientCapabilities` | No |  |
| `CachedRobloxComponentToTemplateId` | `object` | No |  |
| `ClientAttributes` | `object` | No |  |

### Roblox.Api.Notifications.Models.UnreadStreamNotificationsModel

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `unreadNotifications` | `integer` | No | Count of unread notifications in the stream |
| `statusMessage` | `string` | No | Message for the success response |

### Roblox.AppPagePlatform.Shared.V1Beta1.ClientCapabilities

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `EnabledCapabilities` | `integer enum (25 values)[]` | No |  Values: 0, 1, 2, 3, 4, 5, 6, 2000, 2001, 2002, 2003, 2004, 2005, 2006, 2007, 2008, 2009, 2010, 3000, 4000, 5000, 5001, 5002, 6000, 7000 |
| `ProtoVersion` | `string` | No |  |
| `Platform` | `0 \| 1 \| 2` | No | ['Invalid' = 0, 'Web' = 1, 'App' = 2] |
| `RegisteredUiComponentTypes` | `integer enum (128 values)[]` | No |  Values: 0, 1, 10, 11, 12, 13, 14, 15, 100, 101, 102, 103, 104, 105, 106, 107, 108, 109, 110, 200, 201, 202, 203, 204, 205, 206, 207, 208, 209, 210, 211, 212, 213, 214, 215, 216, 217, 218, 219, 220, 221, 222, 223, 224, 225, 226, 227, 228, 229, 230, 231, 232, 233, 234, 235, 236, 237, 238, 239, 240, 241, 242, 243, 244, 245, 246, 247, 248, 249, 250, 251, 252, 253, 254, 255, 256, 257, 258, 259, 260, 261, 262, 263, 264, 265, 266, 267, 268, 269, 270, 271, 272, 273, 274, 275, 276, 277, 278, 279, 280, 281, 282, 283, 284, 300, 400, 401, 500, 600, 601, 602, 603, 604, 605, 606, 607, 608, 700, 701, 800, 801, 802, 803, 804, 900, 901, 902, 9999 |
| `RegisteredActionTypes` | `integer enum (125 values)[]` | No |  Values: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98, 99, 100, 101, 102, 103, 104, 105, 106, 107, 108, 109, 110, 111, 112, 113, 114, 115, 116, 117, 118, 119, 120, 121, 122, 123, 124 |
| `RuntimeFlagValues` | `object` | No |  |

### Roblox.Api.Notifications.Models.PushNotificationRegistration

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `userPushNotificationDestinationId` | `integer` | No | Id of the push notification destination |
| `name` | `string` | No | Name of the push Notification destination |
| `notificationToken` | `string` | No | Notification token |
| `application` | `string` | No | Notification application Example : "Roblox" |
| `platform` | `string enum (8 values)` | No | Notification platform ['ChromeOnDesktop' = 0, 'AndroidNative' = 1, 'FirefoxOnDesktop' = 2, 'IOSNative' = 3, 'AndroidAmazon' = 4, 'IOSTencent' = 5, 'AndroidTencentService' = 6, 'IOSPushKit' = 7] Values: ChromeOnDesktop, AndroidNative, FirefoxOnDesktop, IOSNative, AndroidAmazon, IOSTencent, AndroidTencentService, IOSPushKit |

### UserNotification_Source

The source of the notification.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `universe` | `string` | No | The universe from which the user notification is sent. |

### UserNotification_Payload

Details about the notification.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `type` | `TYPE_UNSPECIFIED \| MOMENT` | No | The type of notification.  Possible values:    \| Value \| Description \|   \| --- \| --- \|   \| TYPE_UNSPECIFIED \| The default value. This value is unused. \|   \| MOMENT \| A notification type representing a moment. \| |
| `messageId` | `string` | No | An ID that represents a customizable notification message template that you create in Creator Dashboard.  The message can contain customizable parameters that you can specify values for. For example, `Your {egg_name} just hatched` has an `egg_name` parameter. See the `parameters` field for more information. |
| `parameters` | `object` | No | A map of parameters used to render a notification message template.  For example, given a template of `Your {egg_name} just hatched.` with parameters of `[{"egg_name": {"string_value": "royal egg"}}]`, the rendered notification message is: `Your royal egg just hatched.` |
| `joinExperience` | `UserNotification_Payload_JoinExperience` | No | Call-to-action that represents joining an experience. |
| `analyticsData` | `UserNotification_Payload_AnalyticsData` | No | Data for how analytics are reported. |

### UserNotification_Payload_ParameterValue

A parameter value that a template uses to render a notification message.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `stringValue` | `string` | No | A string value. |
| `int64Value` | `integer` | No | An int64 value. |

### UserNotification_Payload_JoinExperience

A call-to-action that represents joining an experience.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `launchData` | `string` | No | Arbitrary data that is available to an experience when a user joins the experience with the notification.  This value is limited to a maximum of 200 bytes. |

### UserNotification_Payload_AnalyticsData

Data for how analytics are reported.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `category` | `string` | No | Category of the notification, used to group analytics data.  For example, "Golden egg hatched", "Bronze egg hatched", "Volcano eruptions". |