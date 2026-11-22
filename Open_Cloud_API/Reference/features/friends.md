<!-- Source: https://create.roblox.com/docs/cloud/reference/features/friends.md -->

---
name: "Connections"
last_updated: 2026-11-20T18:47:47Z
type: feature
api_base_url: "https://apis.roblox.com"
endpoints: 19
auth: [api-key, oauth2, cookie]
description: "Manage user connections, such as [viewing pending trusted friend requests](#friends_get_v1_my_trusted_friends_requests), [retrieving the pending trusted friend request count](#friends_get_v1_user_trusted_friend_requests_count), [declining all connection requests](#friends_post_v1_users__requesterUserId__decline_friend_request), or [retrieving a connection list](#friends_get_v1_users__userId__friends)"
---

# Connections

Manage user connections, such as [viewing pending trusted friend requests](#friends_get_v1_my_trusted_friends_requests), [retrieving the pending trusted friend request count](#friends_get_v1_user_trusted_friend_requests_count), [declining all connection requests](#friends_post_v1_users__requesterUserId__decline_friend_request), or [retrieving a connection list](#friends_get_v1_users__userId__friends).

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

### GET `/v1/metadata#friends.roblox.com`

**Server:** `https://friends.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `targetUserId` | query | `integer` | No |  |

**Responses:**

- `200`: OK → `Roblox.Friends.Api.Models.Response.FriendsPageMetadataResponse`

**Response fields** (`Roblox.Friends.Api.Models.Response.FriendsPageMetadataResponse`)

See [Roblox.Friends.Api.Models.Response.FriendsPageMetadataResponse](#roblox-friends-api-models-response-friendspagemetadataresponse) in Models.

**Response example:**
```json
{
  "isFriendsFilterBarEnabled": false,
  "isFriendsPageSortExperimentEnabled": false,
  "isFriendsUserDataStoreCacheEnabled": false,
  "frequentFriendSortRollout": 0,
  "userName": "string",
  "displayName": "string"
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://friends.roblox.com/v1/metadata#friends.roblox.com"
```

### GET `/v1/my/friends/count` [EXPERIMENTAL]

Get the number of friends a user has

**Server:** `https://friends.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Responses:**

- `200`: OK → `Roblox.Friends.Api.FriendsCountResponse`
- `401`: 0: Authorization has been denied for this request.

**Response fields** (`Roblox.Friends.Api.FriendsCountResponse`)

See [Roblox.Friends.Api.FriendsCountResponse](#roblox-friends-api-friendscountresponse) in Models.

**Response example:**
```json
{
  "count": 0
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://friends.roblox.com/v1/my/friends/count"
```

### POST `/v1/my/friends/refresh-qr-session`

**Server:** `https://friends.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Responses:**

- `200`: OK → `Roblox.Friends.Api.Models.Response.RefreshQrSessionResponse`
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed

**Response fields** (`Roblox.Friends.Api.Models.Response.RefreshQrSessionResponse`)

See [Roblox.Friends.Api.Models.Response.RefreshQrSessionResponse](#roblox-friends-api-models-response-refreshqrsessionresponse) in Models.

**Response example:**
```json
{
  "Success": false
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://friends.roblox.com/v1/my/friends/refresh-qr-session"
```

### GET `/v1/my/friends/requests` [EXPERIMENTAL]

Get all users that friend requests with targetUserId using exclusive start paging

**Server:** `https://friends.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `limit` | query | `integer` | No | The number of results per request. |
| `cursor` | query | `string` | No | The paging cursor for the previous or next page. |
| `sessionId` | query | `string` | No | Optional session identifier. |
| `friendRequestSort` | query | `0 \| 1 \| 2` | No | Valid values: `0`, `1`, `2` |
| `uprankUnseen` | query | `boolean` | No | Whether to uprank unseen friend requests and return isUnseen per friend request. |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Friends.Api.FriendRequestResponse_`
- `400`: 1: The target user is invalid or does not exist. 6: Invalid parameters. 34: Invalid pagination cursor.
- `401`: 0: Authorization has been denied for this request.
- `403`: 2: The user is banned from performing operation. 3: The user is blocked from performing this action.
- `429`: 9: The flood limit has been exceeded.

**Response fields** (`Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Friends.Api.FriendRequestResponse_`)

See [Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Friends.Api.FriendRequestResponse_](#roblox-web-webapi-models-apipageresponse-roblox-friends-api-friendrequestresponse-) in Models.

**Response example:**
```json
{
  "previousPageCursor": "string",
  "nextPageCursor": "string",
  "data": [
    {
      "friendRequest": "...",
      "mutualFriendsList": "...",
      "hasVerifiedBadge": "...",
      "isUnseen": "...",
      "description": "...",
      "created": "..."
    }
  ]
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://friends.roblox.com/v1/my/friends/requests"
```

### GET `/v1/my/friends/{userId}/check-qr-session`

**Server:** `https://friends.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `userId` | path | `integer` | Yes | user Id that shows the qr code |

**Responses:**

- `200`: OK → `boolean`
- `401`: 0: Authorization has been denied for this request.

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://friends.roblox.com/v1/my/friends/{USERID}/check-qr-session"
```

### GET `/v1/my/new-friend-requests/count`

**Server:** `https://friends.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Responses:**

- `200`: OK → `Roblox.Friends.Api.Models.Response.NewFriendRequestsCountResponse`
- `401`: 0: Authorization has been denied for this request.

**Response fields** (`Roblox.Friends.Api.Models.Response.NewFriendRequestsCountResponse`)

See [Roblox.Friends.Api.Models.Response.NewFriendRequestsCountResponse](#roblox-friends-api-models-response-newfriendrequestscountresponse) in Models.

**Response example:**
```json
{
  "count": 0
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://friends.roblox.com/v1/my/new-friend-requests/count"
```

### GET `/v1/my/trusted-friends/candidates`

Get a page of friends that the authenticated user can add as trusted friends. Friends with a pending trusted
friend request from the user come after the other friends. A page can be short or empty and still have a
cursor, so request pages until nextPageCursor is null.

**Server:** `https://friends.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `limit` | query | `integer` | No | The maximum number of candidates in the page, from 1 to 50. |
| `cursor` | query | `string` | No | The cursor from the previous page. Null for the first page. |

**Responses:**

- `200`: OK → `Roblox.Paging.CursoredPagedResult_Roblox.Friends.Api.Models.Response.TrustedFriendCandidateResponse_`
- `400`: 34: Invalid pagination cursor. 44: Invalid count, Allowed values: 10, 18, 25, 50, 100
- `401`: 0: Authorization has been denied for this request.
- `500`: 39: There was an internal error processing Trusted Friends.

**Response fields** (`Roblox.Paging.CursoredPagedResult_Roblox.Friends.Api.Models.Response.TrustedFriendCandidateResponse_`)

See [Roblox.Paging.CursoredPagedResult_Roblox.Friends.Api.Models.Response.TrustedFriendCandidateResponse_](#roblox-paging-cursoredpagedresult-roblox-friends-api-models-response-trustedfriendcandidateresponse-) in Models.

**Response example:**
```json
{
  "PreviousCursor": "string",
  "PageItems": [
    {
      "userId": "...",
      "state": "..."
    }
  ],
  "NextCursor": "string",
  "HasMore": false
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://friends.roblox.com/v1/my/trusted-friends/candidates"
```

### GET `/v1/my/trusted-friends/requests`

Get all incoming trusted friend requests using exclusive start paging.

**Server:** `https://friends.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `limit` | query | `integer` | No | The number of results per request. |
| `cursor` | query | `string` | No | The paging cursor for the previous or next page. |
| `sortOrder` | query | `0 \| 1` | No | Specifies how to sort the returned trusted friend requests. Valid values: `0`, `1` |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Friends.Api.Models.Response.TrustedFriendRequestResponse_`
- `400`: 1: The target user is invalid or does not exist. 6: Invalid parameters.
- `401`: 0: Authorization has been denied for this request.
- `403`: 2: The user is banned from performing operation. 3: The user is blocked from performing this action.
- `429`: 9: The flood limit has been exceeded.

**Response fields** (`Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Friends.Api.Models.Response.TrustedFriendRequestResponse_`)

See [Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Friends.Api.Models.Response.TrustedFriendRequestResponse_](#roblox-web-webapi-models-apipageresponse-roblox-friends-api-models-response-trustedfriendrequestresponse-) in Models.

**Response example:**
```json
{
  "previousPageCursor": "string",
  "nextPageCursor": "string",
  "data": [
    {
      "sentAt": "...",
      "senderId": "...",
      "isUnseen": "..."
    }
  ]
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://friends.roblox.com/v1/my/trusted-friends/requests"
```

### POST `/v1/presence/users` [EXPERIMENTAL]

**Server:** `https://presence.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Request Body:** `application/json` — Type: `UserPresenceRequest`

See [UserPresenceRequest](#userpresencerequest) in Models.

**Request example:**
```json
{
  "userIds": [
    0
  ]
}
```

**Responses:**

- `200`: OK → `UserPresencesResponse`
- `400`: Bad Request → `PresenceApi.ErrorResponse`
- `403`: Forbidden → `PresenceApi.ErrorResponse`
- `429`: Too Many Requests → `PresenceApi.ErrorResponse`

**Response fields** (`UserPresencesResponse`)

See [UserPresencesResponse](#userpresencesresponse) in Models.

**Response example:**
```json
{
  "userPresences": [
    {
      "userPresenceType": "...",
      "lastLocation": "...",
      "placeId": "...",
      "rootPlaceId": "...",
      "gameId": "...",
      "universeId": "..."
    }
  ]
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://presence.roblox.com/v1/presence/users" \
  -H "Content-Type: application/json" \
  -d '{
  "userIds": [
    0
  ]
}'
```

### GET `/v1/user/friend-requests/count` [EXPERIMENTAL]

Return the number of pending friend requests.

**Server:** `https://friends.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Responses:**

- `200`: OK → `Roblox.Friends.Api.PendingFriendRequestCountModel`
- `401`: 0: Authorization has been denied for this request.

**Response fields** (`Roblox.Friends.Api.PendingFriendRequestCountModel`)

See [Roblox.Friends.Api.PendingFriendRequestCountModel](#roblox-friends-api-pendingfriendrequestcountmodel) in Models.

**Response example:**
```json
{
  "count": 0
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://friends.roblox.com/v1/user/friend-requests/count"
```

### GET `/v1/user/trusted-friend-requests/count`

Return the number of pending trusted friend requests.

**Server:** `https://friends.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Responses:**

- `200`: OK → `Roblox.Friends.Api.PendingFriendRequestCountModel`
- `401`: 0: Authorization has been denied for this request.

**Response fields** (`Roblox.Friends.Api.PendingFriendRequestCountModel`)

See [Roblox.Friends.Api.PendingFriendRequestCountModel](#roblox-friends-api-pendingfriendrequestcountmodel) in Models.

**Response example:**
```json
{
  "count": 0
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://friends.roblox.com/v1/user/trusted-friend-requests/count"
```

### POST `/v1/user/{userId}/multiget-are-friends`

Check if the requesting user is friends with the specified users.

**Server:** `https://friends.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `userId` | path | `integer` | Yes | The requesting userId. |

**Request Body:** `application/json` — Type: `Roblox.Friends.Api.MultigetAreFriendsRequestModel`

See [Roblox.Friends.Api.MultigetAreFriendsRequestModel](#roblox-friends-api-multigetarefriendsrequestmodel) in Models.

**Request example:**
```json
{
  "targetUserIds": [
    0
  ]
}
```

**Responses:**

- `200`: OK → `Roblox.Friends.Api.MultigetAreFriendsResponse`
- `400`: 1: The target user is invalid or does not exist.
- `403`: 0: Token Validation Failed

**Response fields** (`Roblox.Friends.Api.MultigetAreFriendsResponse`)

See [Roblox.Friends.Api.MultigetAreFriendsResponse](#roblox-friends-api-multigetarefriendsresponse) in Models.

**Response example:**
```json
{
  "friendsId": [
    0
  ]
}
```

**Error handling:** `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://friends.roblox.com/v1/user/{USERID}/multiget-are-friends" \
  -H "Content-Type: application/json" \
  -d '{
  "targetUserIds": [
    0
  ]
}'
```

### GET `/v1/users/{userId}/friends`

Get list of all friends for the specified user.

**Server:** `https://friends.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `userId` | path | `integer` | Yes | The user Id to get the friends for. |
| `userSort` | query | `0 \| 1 \| 2` | No | Specifies how to sort the returned friends. Valid values: `0`, `1`, `2` |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Friends.Api.Models.Response.UserResponse_`
- `400`: 1: The target user is invalid or does not exist.

**Response fields** (`Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Friends.Api.Models.Response.UserResponse_`)

See [Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Friends.Api.Models.Response.UserResponse_](#roblox-web-webapi-models-apiarrayresponse-roblox-friends-api-models-response-userresponse-) in Models.

**Response example:**
```json
{
  "data": [
    {
      "isOnline": "...",
      "presenceType": "...",
      "isDeleted": "...",
      "friendFrequentScore": "...",
      "friendFrequentRank": "...",
      "hasVerifiedBadge": "..."
    }
  ]
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://friends.roblox.com/v1/users/{USERID}/friends"
```

### GET `/v1/users/{userId}/friends/count`

Get the number of friends a user has

**Server:** `https://friends.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `userId` | path | `integer` | Yes |  |

**Responses:**

- `200`: OK → `Roblox.Friends.Api.FriendsCountResponse`
- `400`: 1: The target user is invalid or does not exist.

**Response fields** (`Roblox.Friends.Api.FriendsCountResponse`)

See [Roblox.Friends.Api.FriendsCountResponse](#roblox-friends-api-friendscountresponse) in Models.

**Response example:**
```json
{
  "count": 0
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://friends.roblox.com/v1/users/{USERID}/friends/count"
```

### GET `/v1/users/{userId}/friends/find` [EXPERIMENTAL]

Get a paginated list of all friends for the specified user.

**Server:** `https://friends.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `userId` | path | `integer` | Yes | The user Id to get the friends for. |
| `userSort` | query | `0 \| 1 \| 2` | No | Specifies how to sort the returned friends. Valid values: `0`, `1`, `2` |
| `cursor` | query | `string` | No | The paging cursor for the previous or next page. |
| `limit` | query | `integer` | No | The number of results per request. |
| `findFriendsType` | query | `0 \| 1` | No | ['FindFriends' = 0, 'FindTrustedFriends' = 1] Valid values: `0`, `1` |

**Responses:**

- `200`: OK → `Roblox.Paging.CursoredPagedResult_Roblox.Friends.Api.Models.Response.FriendResponse_`
- `400`: 1: The target user is invalid or does not exist. 6: Invalid parameters.

**Response fields** (`Roblox.Paging.CursoredPagedResult_Roblox.Friends.Api.Models.Response.FriendResponse_`)

See [Roblox.Paging.CursoredPagedResult_Roblox.Friends.Api.Models.Response.FriendResponse_](#roblox-paging-cursoredpagedresult-roblox-friends-api-models-response-friendresponse-) in Models.

**Response example:**
```json
{
  "PreviousCursor": "string",
  "PageItems": [
    {
      "id": "...",
      "hasVerifiedBadge": "..."
    }
  ],
  "NextCursor": "string",
  "HasMore": false
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://friends.roblox.com/v1/users/{USERID}/friends/find"
```

### GET `/v1/users/{userId}/friends/inactive`

Get list of inactive friends for the specified user.

**Server:** `https://friends.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `userId` | path | `integer` | Yes | The user Id to get the friends for. |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Friends.Api.Models.Response.UserResponse_`
- `400`: 1: The target user is invalid or does not exist. 6: Invalid parameters.
- `401`: 0: Authorization has been denied for this request.

**Response fields** (`Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Friends.Api.Models.Response.UserResponse_`)

See [Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Friends.Api.Models.Response.UserResponse_](#roblox-web-webapi-models-apiarrayresponse-roblox-friends-api-models-response-userresponse-) in Models.

**Response example:**
```json
{
  "data": [
    {
      "isOnline": "...",
      "presenceType": "...",
      "isDeleted": "...",
      "friendFrequentScore": "...",
      "friendFrequentRank": "...",
      "hasVerifiedBadge": "..."
    }
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://friends.roblox.com/v1/users/{USERID}/friends/inactive"
```

### GET `/v1/users/{userId}/friends/online`

Get list of all online friends for the specified user.

**Server:** `https://friends.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `userId` | path | `integer` | Yes | The user Id to get the friends for. |
| `userSort` | query | `0 \| 1 \| 2` | No | The sort order to return the friends. Valid values: `0`, `1`, `2` |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Friends.Api.Models.Response.UserPresenceResponse_`
- `400`: 1: The target user is invalid or does not exist. 6: Invalid parameters.
- `401`: 0: Authorization has been denied for this request.

**Response fields** (`Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Friends.Api.Models.Response.UserPresenceResponse_`)

See [Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Friends.Api.Models.Response.UserPresenceResponse_](#roblox-web-webapi-models-apiarrayresponse-roblox-friends-api-models-response-userpresenceresponse-) in Models.

**Response example:**
```json
{
  "data": [
    {
      "userPresence": "...",
      "sortScore": "...",
      "id": "...",
      "name": "...",
      "displayName": "..."
    }
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://friends.roblox.com/v1/users/{USERID}/friends/online"
```

### GET `/v1/users/{userId}/friends/search` [EXPERIMENTAL]

Search for friends by name using a text query.

**Server:** `https://friends.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `userId` | path | `integer` | Yes | The user Id to get the friends for. |
| `query` | query | `string` | No | The string to search names of friends for. |
| `cursor` | query | `string` | No | The paging cursor for the previous or next page. |
| `limit` | query | `integer` | No | The number of results per request. |

**Responses:**

- `200`: OK → `Roblox.Paging.CursoredPagedResult_Roblox.Friends.Api.Models.Response.FriendResponse_`
- `400`: 1: The target user is invalid or does not exist. 6: Invalid parameters.
- `401`: 0: Authorization has been denied for this request.

**Response fields** (`Roblox.Paging.CursoredPagedResult_Roblox.Friends.Api.Models.Response.FriendResponse_`)

See [Roblox.Paging.CursoredPagedResult_Roblox.Friends.Api.Models.Response.FriendResponse_](#roblox-paging-cursoredpagedresult-roblox-friends-api-models-response-friendresponse-) in Models.

**Response example:**
```json
{
  "PreviousCursor": "string",
  "PageItems": [
    {
      "id": "...",
      "hasVerifiedBadge": "..."
    }
  ],
  "NextCursor": "string",
  "HasMore": false
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://friends.roblox.com/v1/users/{USERID}/friends/search"
```

### GET `/v1/users/{userId}/friends/statuses` [EXPERIMENTAL]

Gets a list of friend statuses of specified users against the specified user.

**Server:** `https://friends.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `userId` | path | `integer` | Yes | The user to check the friend statuses against. |
| `userIds` | query | `integer[]` | Yes |  |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Friends.Api.FriendStatusResponse_`
- `400`: 1: The target user is invalid or does not exist. 15: Too many ids. 16: Invalid ids.

**Response fields** (`Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Friends.Api.FriendStatusResponse_`)

See [Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Friends.Api.FriendStatusResponse_](#roblox-web-webapi-models-apiarrayresponse-roblox-friends-api-friendstatusresponse-) in Models.

**Response example:**
```json
{
  "data": [
    {
      "id": "...",
      "status": "..."
    }
  ]
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://friends.roblox.com/v1/users/{USERID}/friends/statuses?userIds={VALUE}"
```

## Models

### Roblox.Friends.Api.Models.Response.FriendsPageMetadataResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `isFriendsFilterBarEnabled` | `boolean` | No |  |
| `isFriendsPageSortExperimentEnabled` | `boolean` | No |  |
| `isFriendsUserDataStoreCacheEnabled` | `boolean` | No |  |
| `frequentFriendSortRollout` | `integer` | No |  |
| `userName` | `string` | No |  |
| `displayName` | `string` | No |  |

### Roblox.Friends.Api.FriendsCountResponse

Response model for Friends Count

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `count` | `integer` | No | Count of friends |

### Roblox.Friends.Api.Models.Response.RefreshQrSessionResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `Success` | `boolean` | No |  |

### Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Friends.Api.FriendRequestResponse_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `previousPageCursor` | `string` | No |  |
| `nextPageCursor` | `string` | No |  |
| `data` | `Roblox.Friends.Api.FriendRequestResponse[]` | No |  |

### Roblox.Friends.Api.Models.Response.NewFriendRequestsCountResponse

The friendship status response model.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `count` | `integer` | No | Count of new friend requests. |

### Roblox.Paging.CursoredPagedResult_Roblox.Friends.Api.Models.Response.TrustedFriendCandidateResponse_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `PreviousCursor` | `string` | No |  |
| `PageItems` | `Roblox.Friends.Api.Models.Response.TrustedFriendCandidateResponse[]` | No |  |
| `NextCursor` | `string` | No |  |
| `HasMore` | `boolean` | No |  |

### Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Friends.Api.Models.Response.TrustedFriendRequestResponse_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `previousPageCursor` | `string` | No |  |
| `nextPageCursor` | `string` | No |  |
| `data` | `Roblox.Friends.Api.Models.Response.TrustedFriendRequestResponse[]` | No |  |

### UserPresenceRequest

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `userIds` | `integer[]` | No |  |

### UserPresencesResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `userPresences` | `UserPresence[]` | No |  |

### PresenceApi.ErrorResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `errors` | `Error[]` | No |  |

### Roblox.Friends.Api.PendingFriendRequestCountModel

Response model for Pending Friend Request Count

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `count` | `integer` | No | Count of pending friend requests |

### Roblox.Friends.Api.MultigetAreFriendsRequestModel

Request model for MultigetAreFriends endpoint

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `targetUserIds` | `integer[]` | No | The target userIds to check against with the requesting user regarding friendship. |

### Roblox.Friends.Api.MultigetAreFriendsResponse

Response model for MultigetAreFriendsResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `friendsId` | `integer[]` | No | friends id list |

### Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Friends.Api.Models.Response.UserResponse_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `data` | `Roblox.Friends.Api.Models.Response.UserResponse[]` | No |  |

### Roblox.Paging.CursoredPagedResult_Roblox.Friends.Api.Models.Response.FriendResponse_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `PreviousCursor` | `string` | No |  |
| `PageItems` | `Roblox.Friends.Api.Models.Response.FriendResponse[]` | No |  |
| `NextCursor` | `string` | No |  |
| `HasMore` | `boolean` | No |  |

### Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Friends.Api.Models.Response.UserPresenceResponse_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `data` | `Roblox.Friends.Api.Models.Response.UserPresenceResponse[]` | No |  |

### Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Friends.Api.FriendStatusResponse_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `data` | `Roblox.Friends.Api.FriendStatusResponse[]` | No |  |

### Roblox.Friends.Api.FriendStatusResponse

The friendship status response model.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No | The user Id of the friend. |
| `status` | `0 \| 1 \| 2 \| 3` | No | The friendship status. ['NotFriends' = 0, 'Friends' = 1, 'RequestSent' = 2, 'RequestReceived' = 3] |

### Roblox.Friends.Api.Models.Response.UserPresenceResponse

A response model representing user presence information.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `userPresence` | `Roblox.Friends.Api.Models.Response.UserPresenceResponseModel` | No |  |
| `sortScore` | `number` | No | Carousel sort score |
| `id` | `integer` | No | The user Id. |
| `name` | `string` | No | The user name. |
| `displayName` | `string` | No | The user DisplayName. |

### Roblox.Friends.Api.Models.Response.UserPresenceResponseModel

Response model for !:IUserPresence objects

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `UserPresenceType` | `string` | No | User Presence Type |
| `UserLocationType` | `string` | No | Location Type |
| `lastLocation` | `string` | No | Last Location |
| `placeId` | `integer` | No | Place Id |
| `rootPlaceId` | `integer` | No | Root Place Id |
| `gameInstanceId` | `string` | No | Game Instance Id |
| `universeId` | `integer` | No | Universe Id |
| `lastOnline` | `string` | No | Most recent time online |

### Roblox.Friends.Api.Models.Response.FriendResponse

A response model representing friend information

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No | The friend's userId |
| `hasVerifiedBadge` | `boolean` | No | The friend's verified badge status. |

### Roblox.Friends.Api.Models.Response.UserResponse

A response model representing user information that also contains select presence information

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `isOnline` | `boolean` | No | Whether the user is online. |
| `presenceType` | `0 \| 1 \| 2 \| 3 \| 4` | No | Where the user is online. |
| `isDeleted` | `boolean` | No | Whether the user is deleted. |
| `friendFrequentScore` | `integer` | No | Frequents value for the user. |
| `friendFrequentRank` | `integer` | No | Frequents rank for the user. |
| `hasVerifiedBadge` | `boolean` | No | The user's verified badge status. |
| `description` | `string` | No | The user description. |
| `created` | `string` | No | When the user signed up. |
| `isBanned` | `boolean` | No | Whether or not the user is banned |
| `externalAppDisplayName` | `string` | No | Used when user is logged in from third party app (e.g. QQ) ExternalAppDisplayName is the name used in that app (e.g. QQ nickname) |
| `id` | `integer` | No | The user Id. |
| `name` | `string` | No | The user name. |
| `displayName` | `string` | No | The user DisplayName. |

### Error

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `code` | `integer` | No |  |
| `message` | `string` | No |  |

### UserPresence

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `userPresenceType` | `PresenceType` | No |  |
| `lastLocation` | `string` | No |  |
| `placeId` | `integer` | No |  |
| `rootPlaceId` | `integer` | No |  |
| `gameId` | `string` | No |  |
| `universeId` | `integer` | No |  |
| `userId` | `integer` | No |  |

### PresenceType

Values: `0`, `1`, `2`, `3`

### Roblox.Friends.Api.Models.Response.TrustedFriendRequestResponse

A response model representing a friend request.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `sentAt` | `string` | No | When the TF request was sent. |
| `senderId` | `integer` | No | The sender user Id. |
| `isUnseen` | `boolean` | No | Whether this trusted friend request is unseen by the recipient. |

### Roblox.Friends.Api.Models.Response.TrustedFriendCandidateResponse

A friend that the authenticated user can add as a trusted friend.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `userId` | `integer` | No | The friend's user Id. |
| `state` | `string` | No | The trusted friend request state between the authenticated user and this friend: None, RequestSent, or RequestReceived. |

### Roblox.Friends.Api.FriendRequestResponse

A response model representing a friend request.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `friendRequest` | `Roblox.Friends.Api.FriendRequest` | No |  |
| `mutualFriendsList` | `string[]` | No | mutualFriendsList |
| `hasVerifiedBadge` | `boolean` | No | The user's verified badge status. |
| `isUnseen` | `boolean` | No | The user's verified badge status. |
| `description` | `string` | No | The user description. |
| `created` | `string` | No | When the user signed up. |
| `isBanned` | `boolean` | No | Whether or not the user is banned |
| `externalAppDisplayName` | `string` | No | Used when user is logged in from third party app (e.g. QQ) ExternalAppDisplayName is the name used in that app (e.g. QQ nickname) |
| `id` | `integer` | No | The user Id. |
| `name` | `string` | No | The user name. |
| `displayName` | `string` | No | The user DisplayName. |

### Roblox.Friends.Api.FriendRequest

A response model representing a friend request.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `sentAt` | `string` | No | When the friend request was sent. |
| `senderId` | `integer` | No | The sender user Id. |
| `sourceUniverseId` | `integer` | No | The source universe Id which the request was sent in. |
| `originSourceType` | `integer enum (14 values)` | No | The origin source type associated with the friend request. ['Unknown' = 0, 'PlayerSearch' = 1, 'QrCode' = 2, 'InGame' = 3, 'UserProfile' = 4, 'QqContactImporter' = 5, 'WeChatContactImporter' = 6, 'ProfileShare' = 7, 'PhoneContactImporter' = 8, 'FriendRecommendations' = 9, 'UserCommunities' = 10, 'TrustedFriend' = 11, 'SchoolMemberList' = 12, 'SocialTabsPage' = 13] Values: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13 |
| `contactName` | `string` | No | The contact name associated with the friend request. |
| `senderNickname` | `string` | No | The nickname associated with the friend request. |