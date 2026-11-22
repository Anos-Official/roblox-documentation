<!-- Source: https://create.roblox.com/docs/cloud/reference/features/bans-and-blocks.md -->

---
name: "Bans and blocks"
last_updated: 2026-11-20T18:47:47Z
type: feature
api_base_url: "https://apis.roblox.com"
endpoints: 7
auth: [api-key, oauth2, cookie]
description: "Manage user restrictions using the Ban API, which includes real-time alt account detection"
---

# Bans and blocks

Manage user restrictions using the Ban API, which includes real-time alt account detection. [Universe-level bans](#Cloud_UpdateUserRestriction__Using_Universes) affect all places, while [place-level bans](#Cloud_UpdateUserRestriction__Using_Universes_Places) allow granular control. Bans can also be managed via the Creator Hub dashboard.

Ban users with customizable duration and reasons, and [review moderation history](#Cloud_ListUserRestrictionLogs) for any banned users.

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

### GET `/cloud/v2/universes/{universe_id}/places/{place_id}/user-restrictions` [BETA]

List User Restrictions

List user restrictions for users that have ever been banned in either a
universe or a specific place.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.user-restriction:read`, `universe.user-restriction:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universe_id` | path | `string` | Yes | The universe ID. |
| `place_id` | path | `string` | Yes | The place ID. |
| `maxPageSize` | query | `integer` | No | The maximum number of user restrictions to return. The service might return fewer than this value. If unspecified, at most 10 user restrictions are returned. The maximum value is 100 and higher values are set to 100. |
| `pageToken` | query | `string` | No | A page token, received from a previous call, to retrieve a subsequent page.  When paginating, all other parameters provided to the subsequent call must match the call that provided the page token. |

**Responses:**

- `200`: OK → `ListUserRestrictionsResponse`

**Response fields** (`ListUserRestrictionsResponse`)

See [ListUserRestrictionsResponse](#listuserrestrictionsresponse) in Models.

**Response example:**
```json
{
  "userRestrictions": [
    {
      "path": "...",
      "updateTime": "...",
      "user": "...",
      "gameJoinRestriction": "..."
    }
  ],
  "nextPageToken": "string"
}
```

**Rate Limits:** perApiKeyOwner: 150/second, perOauth2Authorization: 30/second
**Rate Limit Note:** User Restrictions are subject to the additional rate limits, applied per universe

* Get User Restriction: 50 req/s
* List User Restrictions: 50 req/s
* Update User Restrictions: 10 req/s
* List User Restriction Logs: 50 req/s

Additionally, we impose the following rate limit for the same user within a universe:

* Update User Restriction: 2 req/min

For example, Update User Restriction may not be called for user 123 more than twice every minute.

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/universes/{UNIVERSE_ID}/places/{PLACE_ID}/user-restrictions"
```

### GET `/cloud/v2/universes/{universe_id}/places/{place_id}/user-restrictions/{user_restriction_id}` [BETA]

Get User Restriction

Get the user restriction.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.user-restriction:read`, `universe.user-restriction:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universe_id` | path | `string` | Yes | The universe ID. |
| `place_id` | path | `string` | Yes | The place ID. |
| `user_restriction_id` | path | `string` | Yes | The user-restriction ID. |

**Responses:**

- `200`: OK → `UserRestriction`

**Response fields** (`UserRestriction`)

See [UserRestriction](#userrestriction) in Models.

**Response example:**
```json
{
  "path": "string",
  "updateTime": "2024-01-01T00:00:00Z",
  "user": "string",
  "gameJoinRestriction": {
    "active": false,
    "startTime": "2024-01-01T00:00:00Z",
    "duration": "string",
    "privateReason": "string",
    "displayReason": "string",
    "excludeAltAccounts": false
  }
}
```

**Rate Limits:** perApiKeyOwner: 150/second, perOauth2Authorization: 30/second
**Rate Limit Note:** User Restrictions are subject to the additional rate limits, applied per universe

* Get User Restriction: 50 req/s
* List User Restrictions: 50 req/s
* Update User Restrictions: 10 req/s
* List User Restriction Logs: 50 req/s

Additionally, we impose the following rate limit for the same user within a universe:

* Update User Restriction: 2 req/min

For example, Update User Restriction may not be called for user 123 more than twice every minute.

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/universes/{UNIVERSE_ID}/places/{PLACE_ID}/user-restrictions/{USER_RESTRICTION_ID}"
```

### PATCH `/cloud/v2/universes/{universe_id}/places/{place_id}/user-restrictions/{user_restriction_id}` [BETA]

Update User Restriction

Update the user restriction.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.user-restriction:write`, `universe.user-restriction:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universe_id` | path | `string` | Yes | The universe ID. |
| `place_id` | path | `string` | Yes | The place ID. |
| `user_restriction_id` | path | `string` | Yes | The user-restriction ID. |
| `updateMask` | query | `string` | No | The list of fields to update.  The `game_join_restriction` field must be updated atomically; field masks that index into `game_join_restriction` (such as `"game_join_restriction.active"`) are not supported. |
| `idempotencyKey.key` | query | `string` | No | The unique key to use for idempotency. |
| `idempotencyKey.firstSent` | query | `string` | No | The timestamp at which the first request was sent.  If this is further in the past than the lifetime of the idempotency key (which *may* exceed the annotated minimum lifetime), the server *must* return an error. |

**Request Body:** `application/json` — Type: `UserRestriction`

See [UserRestriction](#userrestriction) in Models.

**Request example:**
```json
{
  "path": "string",
  "updateTime": "2024-01-01T00:00:00Z",
  "user": "string",
  "gameJoinRestriction": {
    "active": false,
    "startTime": "2024-01-01T00:00:00Z",
    "duration": "string",
    "privateReason": "string",
    "displayReason": "string",
    "excludeAltAccounts": false
  }
}
```

**Responses:**

- `200`: OK → `UserRestriction`

**Response fields** (`UserRestriction`)

See [UserRestriction](#userrestriction) in Models.

**Response example:**
```json
{
  "path": "string",
  "updateTime": "2024-01-01T00:00:00Z",
  "user": "string",
  "gameJoinRestriction": {
    "active": false,
    "startTime": "2024-01-01T00:00:00Z",
    "duration": "string",
    "privateReason": "string",
    "displayReason": "string",
    "excludeAltAccounts": false
  }
}
```

**Rate Limits:** perApiKeyOwner: 150/second, perOauth2Authorization: 30/second
**Rate Limit Note:** User Restrictions are subject to the additional rate limits, applied per universe

* Get User Restriction: 50 req/s
* List User Restrictions: 50 req/s
* Update User Restrictions: 10 req/s
* List User Restriction Logs: 50 req/s

Additionally, we impose the following rate limit for the same user within a universe:

* Update User Restriction: 2 req/min

For example, Update User Restriction may not be called for user 123 more than twice every minute.

**Example:**
```bash
curl -X PATCH -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/universes/{UNIVERSE_ID}/places/{PLACE_ID}/user-restrictions/{USER_RESTRICTION_ID}" \
  -H "Content-Type: application/json" \
  -d '{
  "path": "string",
  "updateTime": "2024-01-01T00:00:00Z",
  "user": "string",
  "gameJoinRestriction": {
    "active": false,
    "startTime": "2024-01-01T00:00:00Z",
    "duration": "string",
    "privateReason": "string",
    "displayReason": "string",
    "excludeAltAccounts": false
  }
}'
```

### GET `/cloud/v2/universes/{universe_id}/user-restrictions` [BETA]

List User Restrictions

List user restrictions for users that have ever been banned in either a
universe or a specific place.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.user-restriction:read`, `universe.user-restriction:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universe_id` | path | `string` | Yes | The universe ID. |
| `maxPageSize` | query | `integer` | No | The maximum number of user restrictions to return. The service might return fewer than this value. If unspecified, at most 10 user restrictions are returned. The maximum value is 100 and higher values are set to 100. |
| `pageToken` | query | `string` | No | A page token, received from a previous call, to retrieve a subsequent page.  When paginating, all other parameters provided to the subsequent call must match the call that provided the page token. |

**Responses:**

- `200`: OK → `ListUserRestrictionsResponse`

**Response fields** (`ListUserRestrictionsResponse`)

See [ListUserRestrictionsResponse](#listuserrestrictionsresponse) in Models.

**Response example:**
```json
{
  "userRestrictions": [
    {
      "path": "...",
      "updateTime": "...",
      "user": "...",
      "gameJoinRestriction": "..."
    }
  ],
  "nextPageToken": "string"
}
```

**Rate Limits:** perApiKeyOwner: 150/second, perOauth2Authorization: 30/second
**Rate Limit Note:** User Restrictions are subject to the additional rate limits, applied per universe

* Get User Restriction: 50 req/s
* List User Restrictions: 50 req/s
* Update User Restrictions: 10 req/s
* List User Restriction Logs: 50 req/s

Additionally, we impose the following rate limit for the same user within a universe:

* Update User Restriction: 2 req/min

For example, Update User Restriction may not be called for user 123 more than twice every minute.

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/universes/{UNIVERSE_ID}/user-restrictions"
```

### GET `/cloud/v2/universes/{universe_id}/user-restrictions/{user_restriction_id}` [BETA]

Get User Restriction

Get the user restriction.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.user-restriction:read`, `universe.user-restriction:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universe_id` | path | `string` | Yes | The universe ID. |
| `user_restriction_id` | path | `string` | Yes | The user-restriction ID. |

**Responses:**

- `200`: OK → `UserRestriction`

**Response fields** (`UserRestriction`)

See [UserRestriction](#userrestriction) in Models.

**Response example:**
```json
{
  "path": "string",
  "updateTime": "2024-01-01T00:00:00Z",
  "user": "string",
  "gameJoinRestriction": {
    "active": false,
    "startTime": "2024-01-01T00:00:00Z",
    "duration": "string",
    "privateReason": "string",
    "displayReason": "string",
    "excludeAltAccounts": false
  }
}
```

**Rate Limits:** perApiKeyOwner: 150/second, perOauth2Authorization: 30/second
**Rate Limit Note:** User Restrictions are subject to the additional rate limits, applied per universe

* Get User Restriction: 50 req/s
* List User Restrictions: 50 req/s
* Update User Restrictions: 10 req/s
* List User Restriction Logs: 50 req/s

Additionally, we impose the following rate limit for the same user within a universe:

* Update User Restriction: 2 req/min

For example, Update User Restriction may not be called for user 123 more than twice every minute.

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/universes/{UNIVERSE_ID}/user-restrictions/{USER_RESTRICTION_ID}"
```

### PATCH `/cloud/v2/universes/{universe_id}/user-restrictions/{user_restriction_id}` [BETA]

Update User Restriction

Update the user restriction.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.user-restriction:write`, `universe.user-restriction:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universe_id` | path | `string` | Yes | The universe ID. |
| `user_restriction_id` | path | `string` | Yes | The user-restriction ID. |
| `updateMask` | query | `string` | No | The list of fields to update.  The `game_join_restriction` field must be updated atomically; field masks that index into `game_join_restriction` (such as `"game_join_restriction.active"`) are not supported. |
| `idempotencyKey.key` | query | `string` | No | The unique key to use for idempotency. |
| `idempotencyKey.firstSent` | query | `string` | No | The timestamp at which the first request was sent.  If this is further in the past than the lifetime of the idempotency key (which *may* exceed the annotated minimum lifetime), the server *must* return an error. |

**Request Body:** `application/json` — Type: `UserRestriction`

See [UserRestriction](#userrestriction) in Models.

**Request example:**
```json
{
  "path": "string",
  "updateTime": "2024-01-01T00:00:00Z",
  "user": "string",
  "gameJoinRestriction": {
    "active": false,
    "startTime": "2024-01-01T00:00:00Z",
    "duration": "string",
    "privateReason": "string",
    "displayReason": "string",
    "excludeAltAccounts": false
  }
}
```

**Responses:**

- `200`: OK → `UserRestriction`

**Response fields** (`UserRestriction`)

See [UserRestriction](#userrestriction) in Models.

**Response example:**
```json
{
  "path": "string",
  "updateTime": "2024-01-01T00:00:00Z",
  "user": "string",
  "gameJoinRestriction": {
    "active": false,
    "startTime": "2024-01-01T00:00:00Z",
    "duration": "string",
    "privateReason": "string",
    "displayReason": "string",
    "excludeAltAccounts": false
  }
}
```

**Rate Limits:** perApiKeyOwner: 150/second, perOauth2Authorization: 30/second
**Rate Limit Note:** User Restrictions are subject to the additional rate limits, applied per universe

* Get User Restriction: 50 req/s
* List User Restrictions: 50 req/s
* Update User Restrictions: 10 req/s
* List User Restriction Logs: 50 req/s

Additionally, we impose the following rate limit for the same user within a universe:

* Update User Restriction: 2 req/min

For example, Update User Restriction may not be called for user 123 more than twice every minute.

**Example:**
```bash
curl -X PATCH -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/universes/{UNIVERSE_ID}/user-restrictions/{USER_RESTRICTION_ID}" \
  -H "Content-Type: application/json" \
  -d '{
  "path": "string",
  "updateTime": "2024-01-01T00:00:00Z",
  "user": "string",
  "gameJoinRestriction": {
    "active": false,
    "startTime": "2024-01-01T00:00:00Z",
    "duration": "string",
    "privateReason": "string",
    "displayReason": "string",
    "excludeAltAccounts": false
  }
}'
```

### GET `/cloud/v2/universes/{universe_id}/user-restrictions:listLogs` [BETA]

List User Restriction Logs

List changes to UserRestriction resources within a given universe.
This includes both universe-level and place-level restrictions.

For universe-level restriction logs, the `place` field will be empty.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `universe.user-restriction:read`, `universe.user-restriction:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universe_id` | path | `string` | Yes | The universe ID. |
| `maxPageSize` | query | `integer` | No | The maximum number of UserRestrictionLogs to return. The service may return fewer than this value. If unspecified, at most 10 UserRestrictionLogs are returned. The maximum value is 100 and higher values are set to 100. |
| `pageToken` | query | `string` | No | A page token, received from a previous call, to retrieve a subsequent page.  When paginating, all other parameters provided to the subsequent call must match the call that provided the page token. |
| `filter` | query | `string` | No | This field may be set to filter the logs returned.  The `filter` field supports a very small number of CEL:  * `user` * `place` * The `==` comparison operator is available. * The `&&` logical operator is also supported.  As an example, filtering for a user and a place takes the form `filter="user == 'users/123'" && "place == 'places/456'"` |

**Responses:**

- `200`: OK → `ListUserRestrictionLogsResponse`

**Response fields** (`ListUserRestrictionLogsResponse`)

See [ListUserRestrictionLogsResponse](#listuserrestrictionlogsresponse) in Models.

**Response example:**
```json
{
  "logs": [
    {
      "user": "...",
      "place": "...",
      "moderator": "...",
      "createTime": "...",
      "active": "...",
      "startTime": "..."
    }
  ],
  "nextPageToken": "string"
}
```

**Rate Limits:** perApiKeyOwner: 150/second, perOauth2Authorization: 30/second
**Rate Limit Note:** User Restrictions are subject to the additional rate limits, applied per universe

* Get User Restriction: 50 req/s
* List User Restrictions: 50 req/s
* Update User Restrictions: 10 req/s
* List User Restriction Logs: 50 req/s

Additionally, we impose the following rate limit for the same user within a universe:

* Update User Restriction: 2 req/min

For example, Update User Restriction may not be called for user 123 more than twice every minute.

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/universes/{UNIVERSE_ID}/user-restrictions:listLogs"
```

## Models

### ListUserRestrictionsResponse

A list of UserRestrictions in the parent collection.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `userRestrictions` | `UserRestriction[]` | No | The UserRestrictions from the specified Universe or Place. |
| `nextPageToken` | `string` | No | A token that you can send as a `pageToken` parameter to retrieve the next page. If this field is omitted, there are no subsequent pages. |

### UserRestriction

Represents a restriction on a user.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `path` | `string` | No | The resource path of the user restriction.  Formats: * `universes/{universe_id}/user-restrictions/{user_restriction_id}` * `universes/{universe_id}/places/{place_id}/user-restrictions/{user_restriction_id}` |
| `updateTime` | `string` | No | The timestamp when the user restriction was last updated. |
| `user` | `string` | No | The affected user. |
| `gameJoinRestriction` | `UserRestriction_GameJoinRestriction` | No | The user is banned from the parent universe or place. |

### ListUserRestrictionLogsResponse

Returns a list of change logs applied to UserRestriction resources.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `logs` | `UserRestrictionLog[]` | No | The UserRestrictionLogs from the specified Universe. |
| `nextPageToken` | `string` | No | A token that you can send as a `pageToken` parameter to retrieve the next page. If this field is omitted, there are no subsequent pages. |

### UserRestrictionLog

An entity capturing a state change on a type of restriction.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `user` | `string` | No | The user to which this restriction update is applied. |
| `place` | `string` | No | The place in which a user restriction was explicitly updated. This field is empty if the log captures a state change applied on the universe level. |
| `moderator` | `UserRestrictionLog_Moderator` | No | The moderator who issued the state change. |
| `createTime` | `string` | No | When the change happened. |
| `active` | `boolean` | No | Whether the restriction was active after the action represented by this log. |
| `startTime` | `string` | No | The start time of the restriction. |
| `duration` | `string` | No | The duration of the restriction.  If not specified, the restriction is permanent. |
| `privateReason` | `string` | No | The reason the restriction was created.  This field *is not* displayed to the user. |
| `displayReason` | `string` | No | The user-facing reason the restriction was created.  This field *is* displayed to the user. |
| `restrictionType` | `UserRestrictionLog_RestrictionType` | No | The type of restriction for this log. |
| `excludeAltAccounts` | `boolean` | No | When true, the restriction will not be be propagated to alt accounts.  Defaults to false. |

### UserRestrictionLog_Moderator

An entity capturing the author of a state change.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `robloxUser` | `string` | No | A moderator identified by the User resource. |
| `gameServerScript` | `UserRestrictionLog_Moderator_GameServerScript` | No | A moderator identified as a Lua script on game server. |

### UserRestrictionLog_RestrictionType

The type of restriction.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `gameJoinRestriction` | `UserRestrictionLog_RestrictionType_GameJoinRestriction` | No | Represents game join restriction as one of the restriction type. |

### UserRestrictionLog_RestrictionType_GameJoinRestriction

Represents game join restriction.

| Property | Type | Required | Description |
|----------|------|----------|-------------|

### UserRestrictionLog_Moderator_GameServerScript

Represents a user-written Lua script executed on game server.

| Property | Type | Required | Description |
|----------|------|----------|-------------|

### UserRestriction_GameJoinRestriction

A restriction means the affected user will not be able to join the parent
universe or place, and will be kicked if currently joined.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `active` | `boolean` | No | By default, this is false since a user's access to an experience is not restricted to begin with.  If this is set to true at the experience level, this becomes true automatically at the place level for all places in the experience. |
| `startTime` | `string` | No | The start time of the restriction. |
| `duration` | `string` | No | The duration of the restriction.  If not specified, the restriction is permanent. If specified, the range must be from 1 second to 315,576,000,000 seconds, inclusive. Durations with sub-second precision are not permitted. |
| `privateReason` | `string` | No | The reason the restriction was created.  This field *is not* displayed to the user. 1,000 character maximum. |
| `displayReason` | `string` | No | The user-facing reason the restriction was created.  This field *is* displayed to the user. 400 character maximum. |
| `excludeAltAccounts` | `boolean` | No | When true, the restriction will not be be propagated to alt accounts.  Defaults to false. |
| `inherited` | `boolean` | No | This is true when the restriction doesn't directly apply to the parent resource, but to some other ancestor resource.  For example, if a user restriction exists on universes/123, then any places within that universe from which the user was not explicitly restricted will have an inherited restriction and this field will be `true`. |