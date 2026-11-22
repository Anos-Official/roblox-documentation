<!-- Source: https://create.roblox.com/docs/cloud/reference/domains/presence.md -->

---
name: "presence-api"
last_updated: 2026-11-20T18:47:47Z
type: legacy
versions: [v1]
endpoints: 1
auth: [cookie]
---

# presence-api

> **Warning:** Legacy APIs with cookie authentication can incorporate breaking changes without notice. We don't recommend them for production applications.

**Versions:** v1

## Endpoints

### POST `/v1/presence/users`

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

- `200`: Success → `UserPresencesResponse`
- `400`: Bad Request → `ErrorResponse`
- `403`: Forbidden → `ErrorResponse`
- `429`: Too Many Requests → `ErrorResponse`

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
curl -X POST -H "Authorization: Bearer $ROBLOX_ACCESS_TOKEN" \
  "/v1/presence/users" \
  -H "Content-Type: application/json" \
  -d '{
  "userIds": [
    0
  ]
}'
```

## Models

### Error

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `code` | `integer` | No |  |
| `message` | `string` | No |  |

### ErrorResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `errors` | `Error[]` | No |  |

### PresenceType

Values: `0`, `1`, `2`, `3`

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

### UserPresenceRequest

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `userIds` | `integer[]` | No |  |

### UserPresencesResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `userPresences` | `UserPresence[]` | No |  |