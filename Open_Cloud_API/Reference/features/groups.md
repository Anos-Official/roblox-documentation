<!-- Source: https://create.roblox.com/docs/cloud/reference/features/groups.md -->

---
name: "Groups"
last_updated: 2026-11-20T18:47:47Z
type: feature
api_base_url: "https://apis.roblox.com"
endpoints: 46
auth: [api-key, oauth2, cookie]
description: "Manage Roblox groups including memberships, roles, and group settings"
---

# Groups

Manage Roblox groups including memberships, roles, and group settings.

Common use cases include:

- Membership management: [Accept](#Cloud_AcceptGroupJoinRequest) or [decline](#Cloud_DeclineGroupJoinRequest) join requests and [manage member roles](#Cloud_UpdateGroupMembership)
- Role configuration: [Create](#groups_post_v1_groups__groupId__rolesets_create), [update](#groups_patch_v1_groups__groupId__rolesets__rolesetId_), and [delete](#groups_delete_v1_groups__groupId__rolesets__rolesetId_) group roles with custom permissions
- Audit logging: [Review group activity](#get_legacy_groups_v1_groups__groupId__audit_log) through audit logs

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

### GET `/cloud/v2/groups/{group_id}` [BETA]

Get Group

Gets the specified group.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `group_id` | path | `string` | Yes | The group ID. |

**Responses:**

- `200`: OK → `Group`

**Response fields** (`Group`)

See [Group](#group) in Models.

**Response example:**
```json
{
  "path": "string",
  "createTime": "2024-01-01T00:00:00Z",
  "updateTime": "2024-01-01T00:00:00Z",
  "id": "string",
  "displayName": "string",
  "description": "string"
}
```

**Rate Limits:** perApiKeyOwner: 150/minute, perOauth2Authorization: 30/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/groups/{GROUP_ID}"
```

### GET `/cloud/v2/groups/{group_id}/forum-categories` [BETA]

List Group Forum Categories

Lists forum categories in the group. Supports filtering.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `group-forum:read`, `group-forum:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `group_id` | path | `string` | Yes | The group ID. |
| `maxPageSize` | query | `integer` | No | The maximum number of group forum categories to return. The service might return fewer than this value. If unspecified, at most 10 group forum categories are returned. The maximum value is 10 and higher values are set to 10. |
| `pageToken` | query | `string` | No | A page token, received from a previous call, to retrieve a subsequent page.  When paginating, all other parameters provided to the subsequent call must match the call that provided the page token. |
| `filter` | query | `string` | No | This field may be set in order to filter the resources returned.  Filtering conforms to Common Expression Language (CEL). Only the boolean field `archived` and `==` operator are supported. If `archived=false`, archived categories are not returned. The default value is `false`. Example: `"filter=archived==true"` |

**Responses:**

- `200`: OK → `ListGroupForumCategoriesResponse`

**Response fields** (`ListGroupForumCategoriesResponse`)

See [ListGroupForumCategoriesResponse](#listgroupforumcategoriesresponse) in Models.

**Response example:**
```json
{
  "groupForumCategories": [
    {
      "path": "...",
      "createTime": "...",
      "updateTime": "...",
      "groupForumCategoryId": "...",
      "displayName": "...",
      "creator": "..."
    }
  ],
  "nextPageToken": "string"
}
```

**Rate Limits:** perApiKeyOwner: 150/minute, perOauth2Authorization: 30/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/groups/{GROUP_ID}/forum-categories"
```

### GET `/cloud/v2/groups/{group_id}/forum-categories/{forum_category_id}/posts` [BETA]

List Group Forum Posts

Lists forum posts in the group's forum category. Supports filtering.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `group-forum:read`, `group-forum:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `group_id` | path | `string` | Yes | The group ID. |
| `forum_category_id` | path | `string` | Yes | The forum-category ID. |
| `maxPageSize` | query | `integer` | No | The maximum number of group forum posts to return. The service might return fewer than this value. If unspecified, at most 10 group forum posts are returned. The maximum value is 100 and higher values are set to 100. |
| `pageToken` | query | `string` | No | A page token, received from a previous call, to retrieve a subsequent page.  When paginating, all other parameters provided to the subsequent call must match the call that provided the page token. |
| `filter` | query | `string` | No | This field may be set in order to filter the resources returned.  Filtering conforms to Common Expression Language (CEL). Only the query `filter=pinned==true` is supported, where only pinned posts are returned. `filter=pinned==false`is not supported. |
| `view` | query | `VIEW_UNSPECIFIED \| FULL \| FULL_WITH_FIRST_COMMENT` | No | The view in which to retrieve the group forum post.  Supports FULL and FULL_WITH_FIRST_COMMENT.  Defaults to FULL.  Possible values:    \| Value \| Description \|   \| --- \| --- \|   \| VIEW_UNSPECIFIED \| The group forum post view is not specified; the default will be used. \|   \| FULL \| Includes all fields but does not dereference `first_comment`. Only the `path` field is populated. \|   \| FULL_WITH_FIRST_COMMENT \| Includes all fields and also fully populates `first_comment`. The default view. \| Valid values: `VIEW_UNSPECIFIED`, `FULL`, `FULL_WITH_FIRST_COMMENT` |

**Responses:**

- `200`: OK → `ListGroupForumPostsResponse`

**Response fields** (`ListGroupForumPostsResponse`)

See [ListGroupForumPostsResponse](#listgroupforumpostsresponse) in Models.

**Response example:**
```json
{
  "groupForumPosts": [
    {
      "path": "...",
      "createTime": "...",
      "updateTime": "...",
      "pinned": "...",
      "locked": "...",
      "groupForumPostId": "..."
    }
  ],
  "nextPageToken": "string"
}
```

**Rate Limits:** perApiKeyOwner: 150/minute, perOauth2Authorization: 30/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/groups/{GROUP_ID}/forum-categories/{FORUM_CATEGORY_ID}/posts"
```

### GET `/cloud/v2/groups/{group_id}/forum-categories/{forum_category_id}/posts/{post_id}/comments` [BETA]

List Group Forum Comments

Lists forum comments on a group's forum post. Supports filtering.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `group-forum:read`, `group-forum:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `group_id` | path | `string` | Yes | The group ID. |
| `forum_category_id` | path | `string` | Yes | The forum-category ID. |
| `post_id` | path | `string` | Yes | The post ID. |
| `maxPageSize` | query | `integer` | No | The maximum number of group forum comments to return. The service might return fewer than this value. If unspecified, at most 10 group forum comments are returned. The maximum value is 100 and higher values are set to 100. |
| `pageToken` | query | `string` | No | A page token, received from a previous call, to retrieve a subsequent page.  When paginating, all other parameters provided to the subsequent call must match the call that provided the page token. |
| `filter` | query | `string` | No | This field may be set in order to filter the resources returned.  Filtering conforms to Common Expression Language (CEL). Only the string field `repliesToCommentId` and the `==` operator are supported. If `repliesToCommentId` is specified, only comments that respond to the comment are returned. The default value is `''`. If `repliesToCommentId=''`, only comments responding directly to the post are returned. Example: `"filter=repliesToCommentId==01234567-89ab-cdef-0123-456789abcdef"` |

**Responses:**

- `200`: OK → `ListGroupForumCommentsResponse`

**Response fields** (`ListGroupForumCommentsResponse`)

See [ListGroupForumCommentsResponse](#listgroupforumcommentsresponse) in Models.

**Response example:**
```json
{
  "groupForumComments": [
    {
      "path": "...",
      "groupForumCommentId": "...",
      "message": "..."
    }
  ],
  "nextPageToken": "string"
}
```

**Rate Limits:** perApiKeyOwner: 150/minute, perOauth2Authorization: 30/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/groups/{GROUP_ID}/forum-categories/{FORUM_CATEGORY_ID}/posts/{POST_ID}/comments"
```

### GET `/cloud/v2/groups/{group_id}/join-requests` [BETA]

List Group Join Requests

List join requests under a group. Supports filtering.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `group:read`, `group:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `group_id` | path | `string` | Yes | The group ID. |
| `maxPageSize` | query | `integer` | No | The maximum number of group join requests to return. The service might return fewer than this value. If unspecified, at most 10 group join requests are returned. The maximum value is 20 and higher values are set to 20. |
| `pageToken` | query | `string` | No | A page token, received from a previous call, to retrieve a subsequent page.  When paginating, all other parameters provided to the subsequent call must match the call that provided the page token. |
| `filter` | query | `string` | No | This field may be set in order to filter the resources returned.  Filtering conforms to Common Expression Language (CEL). Only the `user` field and `==` operator are supported.   Example: `"user == 'users/156'"` |

**Responses:**

- `200`: OK → `ListGroupJoinRequestsResponse`

**Response fields** (`ListGroupJoinRequestsResponse`)

See [ListGroupJoinRequestsResponse](#listgroupjoinrequestsresponse) in Models.

**Response example:**
```json
{
  "groupJoinRequests": [
    {
      "path": "...",
      "createTime": "...",
      "user": "..."
    }
  ],
  "nextPageToken": "string"
}
```

**Rate Limits:** perApiKeyOwner: 300/minute, perOauth2Authorization: 90/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/groups/{GROUP_ID}/join-requests"
```

### POST `/cloud/v2/groups/{group_id}/join-requests/{join_request_id}:accept` [BETA]

Accept Group Join Request

Accepts a join request.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `group:write`, `group:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `group_id` | path | `string` | Yes | The group ID. |
| `join_request_id` | path | `string` | Yes | The join-request ID. |

**Request Body:** `application/json` — Type: `AcceptGroupJoinRequestRequest`

See [AcceptGroupJoinRequestRequest](#acceptgroupjoinrequestrequest) in Models.

**Request example:**
```json
{}
```

**Responses:**

- `200`: OK

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 90/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/groups/{GROUP_ID}/join-requests/{JOIN_REQUEST_ID}:accept" \
  -H "Content-Type: application/json" \
  -d '{}'
```

### POST `/cloud/v2/groups/{group_id}/join-requests/{join_request_id}:decline` [BETA]

Decline Group Join Request

Declines a join request.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `group:write`, `group:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `group_id` | path | `string` | Yes | The group ID. |
| `join_request_id` | path | `string` | Yes | The join-request ID. |

**Request Body:** `application/json` — Type: `DeclineGroupJoinRequestRequest`

See [DeclineGroupJoinRequestRequest](#declinegroupjoinrequestrequest) in Models.

**Request example:**
```json
{}
```

**Responses:**

- `200`: OK

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 90/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/groups/{GROUP_ID}/join-requests/{JOIN_REQUEST_ID}:decline" \
  -H "Content-Type: application/json" \
  -d '{}'
```

### GET `/cloud/v2/groups/{group_id}/memberships` [BETA]

List Group Memberships

List group members in a group. Supports filtering.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `group_id` | path | `string` | Yes | The group ID. |
| `maxPageSize` | query | `integer` | No | The maximum number of group memberships to return. The service might return fewer than this value. If unspecified, at most 10 group memberships are returned. The maximum value is 100 and higher values are set to 100. |
| `pageToken` | query | `string` | No | A page token, received from a previous call, to retrieve a subsequent page.  When paginating, all other parameters provided to the subsequent call must match the call that provided the page token. |
| `filter` | query | `string` | No | This field may be set in order to filter the resources returned.  See the [filtering](/cloud/reference/patterns#list-group-memberships) documentation for more information. |

**Responses:**

- `200`: OK → `ListGroupMembershipsResponse`

**Response fields** (`ListGroupMembershipsResponse`)

See [ListGroupMembershipsResponse](#listgroupmembershipsresponse) in Models.

**Response example:**
```json
{
  "groupMemberships": [
    {
      "path": "...",
      "createTime": "...",
      "updateTime": "...",
      "user": "...",
      "role": "...",
      "roles": "..."
    }
  ],
  "nextPageToken": "string"
}
```

**Rate Limits:** perApiKeyOwner: 300/minute, perOauth2Authorization: 90/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/groups/{GROUP_ID}/memberships"
```

### PATCH `/cloud/v2/groups/{group_id}/memberships/{membership_id}` [BETA]

Update Group Membership

**Deprecated.** Use AssignGroupRole and UnassignGroupRole instead.
Updates the group membership for a particular group member. This action
requires the requester to be able to assign or remove roles below their
highest role. The requester cannot change their own roles.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `group:write`, `group:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `group_id` | path | `string` | Yes | The group ID. |
| `membership_id` | path | `string` | Yes | The membership ID. |

**Request Body:** `application/json` — Type: `GroupMembership`

See [GroupMembership](#groupmembership) in Models.

**Request example:**
```json
{
  "path": "string",
  "createTime": "2024-01-01T00:00:00Z",
  "updateTime": "2024-01-01T00:00:00Z",
  "user": "string",
  "role": "string",
  "roles": [
    "string"
  ]
}
```

**Responses:**

- `200`: OK → `GroupMembership`

**Response fields** (`GroupMembership`)

See [GroupMembership](#groupmembership) in Models.

**Response example:**
```json
{
  "path": "string",
  "createTime": "2024-01-01T00:00:00Z",
  "updateTime": "2024-01-01T00:00:00Z",
  "user": "string",
  "role": "string",
  "roles": [
    "string"
  ]
}
```

**Rate Limits:** perApiKeyOwner: 300/minute, perOauth2Authorization: 90/minute

**Example:**
```bash
curl -X PATCH -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/groups/{GROUP_ID}/memberships/{MEMBERSHIP_ID}" \
  -H "Content-Type: application/json" \
  -d '{
  "path": "string",
  "createTime": "2024-01-01T00:00:00Z",
  "updateTime": "2024-01-01T00:00:00Z",
  "user": "string",
  "role": "string",
  "roles": [
    "string"
  ]
}'
```

### POST `/cloud/v2/groups/{group_id}/memberships/{membership_id}:assignRole` [BETA]

Assign Role Group Membership

Assigns a specific role to a user within a group. If the user already
holds the specified role, no action is taken.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `group:write`, `group:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `group_id` | path | `string` | Yes | The group ID. |
| `membership_id` | path | `string` | Yes | The membership ID. |

**Request Body:** `application/json` — Type: `AssignRoleGroupMembershipRequest`

See [AssignRoleGroupMembershipRequest](#assignrolegroupmembershiprequest) in Models.

**Request example:**
```json
{
  "role": "string"
}
```

**Responses:**

- `200`: OK → `GroupMembership`

**Response fields** (`GroupMembership`)

See [GroupMembership](#groupmembership) in Models.

**Response example:**
```json
{
  "path": "string",
  "createTime": "2024-01-01T00:00:00Z",
  "updateTime": "2024-01-01T00:00:00Z",
  "user": "string",
  "role": "string",
  "roles": [
    "string"
  ]
}
```

**Rate Limits:** perApiKeyOwner: 300/minute, perOauth2Authorization: 90/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/groups/{GROUP_ID}/memberships/{MEMBERSHIP_ID}:assignRole" \
  -H "Content-Type: application/json" \
  -d '{
  "role": "string"
}'
```

### POST `/cloud/v2/groups/{group_id}/memberships/{membership_id}:unassignRole` [BETA]

Unassign Role Group Membership

Unassigns a specific role from a user within a group. If the user does
not hold the specified role, no action is taken.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `group:write`, `group:write`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `group_id` | path | `string` | Yes | The group ID. |
| `membership_id` | path | `string` | Yes | The membership ID. |

**Request Body:** `application/json` — Type: `UnassignRoleGroupMembershipRequest`

See [UnassignRoleGroupMembershipRequest](#unassignrolegroupmembershiprequest) in Models.

**Request example:**
```json
{
  "role": "string"
}
```

**Responses:**

- `200`: OK → `GroupMembership`

**Response fields** (`GroupMembership`)

See [GroupMembership](#groupmembership) in Models.

**Response example:**
```json
{
  "path": "string",
  "createTime": "2024-01-01T00:00:00Z",
  "updateTime": "2024-01-01T00:00:00Z",
  "user": "string",
  "role": "string",
  "roles": [
    "string"
  ]
}
```

**Rate Limits:** perApiKeyOwner: 300/minute, perOauth2Authorization: 90/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/groups/{GROUP_ID}/memberships/{MEMBERSHIP_ID}:unassignRole" \
  -H "Content-Type: application/json" \
  -d '{
  "role": "string"
}'
```

### GET `/cloud/v2/groups/{group_id}/roles` [BETA]

List Group Roles

List roles in a group.

Roles can be public or private. The response includes private roles and
their fields only when the acting user is permitted to view them. The
endpoint does not provide a public-roles-only view.

The permissions field for roles is viewable based on the requester's access
and scopes.

Permissions for the guest role are always visible - a scope is not needed.

If the requester is a member of the group and has the `group:read` scope,
permissions in their role are visible.

If the requester is the owner of the group and has the `group:read` scope,
permissions in all roles are visible.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `group:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `group_id` | path | `string` | Yes | The group ID. |
| `maxPageSize` | query | `integer` | No | The maximum number of group roles to return. The service might return fewer than this value. If unspecified, at most 10 group roles are returned. The maximum value is 20 and higher values are set to 20. |
| `pageToken` | query | `string` | No | A page token, received from a previous call, to retrieve a subsequent page.  When paginating, all other parameters provided to the subsequent call must match the call that provided the page token. |

**Responses:**

- `200`: OK → `ListGroupRolesResponse`

**Response fields** (`ListGroupRolesResponse`)

See [ListGroupRolesResponse](#listgrouprolesresponse) in Models.

**Response example:**
```json
{
  "groupRoles": [
    {
      "path": "...",
      "createTime": "...",
      "updateTime": "...",
      "id": "...",
      "displayName": "...",
      "description": "..."
    }
  ],
  "nextPageToken": "string"
}
```

**Rate Limits:** perApiKeyOwner: 300/minute, perOauth2Authorization: 90/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/groups/{GROUP_ID}/roles"
```

### GET `/cloud/v2/groups/{group_id}/roles/{role_id}` [BETA]

Get Group Role

Get the group role

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `group:read`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `group_id` | path | `string` | Yes | The group ID. |
| `role_id` | path | `string` | Yes | The role ID. |

**Responses:**

- `200`: OK → `GroupRole`

**Response fields** (`GroupRole`)

See [GroupRole](#grouprole) in Models.

**Response example:**
```json
{
  "path": "string",
  "createTime": "2024-01-01T00:00:00Z",
  "updateTime": "2024-01-01T00:00:00Z",
  "id": "string",
  "displayName": "string",
  "description": "string"
}
```

**Rate Limits:** perApiKeyOwner: 300/minute, perOauth2Authorization: 90/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/cloud/v2/groups/{GROUP_ID}/roles/{ROLE_ID}"
```

### GET `/legacy-develop/v1/user/groups/canmanage` [EXPERIMENTAL]

Gets a list of Groups that a user can manage.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `legacy-group:manage`

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

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/legacy-develop/v1/user/groups/canmanage"
```

### POST `/legacy-groups/v1/groups/policies`

Gets group policy info used for compliance.

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `legacy-group:manage`

**Request Body:** `application/json` — Type: `Roblox.Groups.Api.GroupPolicyRequest`

See [Roblox.Groups.Api.GroupPolicyRequest](#roblox-groups-api-grouppolicyrequest) in Models.

**Request example:**
```json
{
  "groupIds": [
    0
  ]
}
```

**Responses:**

- `200`: OK → `Roblox.Groups.Api.GroupPoliciesResponse`
- `400`: 1: Too many ids in request. 2: Ids could not be parsed from request.
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed

**Response fields** (`Roblox.Groups.Api.GroupPoliciesResponse`)

See [Roblox.Groups.Api.GroupPoliciesResponse](#roblox-groups-api-grouppoliciesresponse) in Models.

**Response example:**
```json
{
  "groups": [
    {
      "canViewGroup": "...",
      "groupId": "..."
    }
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X POST -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/legacy-groups/v1/groups/policies" \
  -H "Content-Type: application/json" \
  -d '{
  "groupIds": [
    0
  ]
}'
```

### GET `/legacy-groups/v1/groups/{groupId}/audit-log`

Gets the Group's audit log

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `legacy-group:manage`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | path | `integer` | Yes | The id of the group the user is in. |
| `actionType` | query | `string enum (80 values)` | No | Filter for specific type of action performed Valid values: `DeletePost`, `RemoveMember`, `AcceptJoinRequest`, `DeclineJoinRequest`, `PostStatus`, `ChangeRank`, `BuyAd`, `SendAllyRequest`, `CreateEnemy`, `AcceptAllyRequest`, `DeclineAllyRequest`, `DeleteAlly`, `DeleteEnemy`, `AddGroupPlace`, `RemoveGroupPlace`, `CreateItems`, `ConfigureItems`, `SpendGroupFunds`, `ChangeOwner`, `Delete`, `AdjustCurrencyAmounts`, `Abandon`, `Claim`, `Rename`, `ChangeDescription`, `InviteToClan`, `KickFromClan`, `CancelClanInvite`, `BuyClan`, `CreateGroupAsset`, `UpdateGroupAsset`, `ConfigureGroupAsset`, `RevertGroupAsset`, `CreateGroupDeveloperProduct`, `ConfigureGroupGame`, `CreateGroupDeveloperSubscriptionProduct`, `Lock`, `Unlock`, `CreateGamePass`, `CreateBadge`, `ConfigureBadge`, `SavePlace`, `PublishPlace`, `UpdateRolesetRank`, `UpdateRolesetData`, `UpdateRoleSetPosition`, `BanMember`, `UnbanMember`, `CreateForumCategory`, `UpdateForumCategory`, `ArchiveForumCategory`, `DeleteForumCategory`, `DeleteForumPost`, `DeleteForumComment`, `PinForumPost`, `UnpinForumPost`, `LockForumPost`, `UnlockForumPost`, `CreateRoleset`, `DeleteRoleset`, `CreateCommerceProduct`, `SetCommerceProductActive`, `ArchiveCommerceProduct`, `AcceptCommerceProductBundlingFee`, `SetCommerceProductInactive`, `ConnectMerchant`, `DisconnectMerchant`, `JoinGroup`, `LeaveGroup`, `UpdateGroupIcon`, `UpdateGroupCoverPhoto`, `AssignRole`, `UnassignRole`, `PublishAnnouncement`, `DeleteAnnouncement`, `UpdateRoleSetPermissions`, `UpdateGroupSecuritySettings`, `GrantEnterpriseTier`, `RevokeEnterpriseTier`, `DeactivateGroup` |
| `userId` | query | `integer` | No | Filter for specific user id |
| `limit` | query | `10 \| 25 \| 50 \| 100` | No | The number of results per request. Valid values: `10`, `25`, `50`, `100` |
| `cursor` | query | `string` | No | The paging cursor for the previous or next page. |
| `sortOrder` | query | `Asc \| Desc` | No | The order the results are sorted in. Valid values: `Asc`, `Desc` |

**Responses:**

- `200`: OK → `Roblox.Groups.Api.GroupAuditLogPageResponse_Roblox.Groups.Api.Models.Response.GroupAuditLogResponseItem_`
- `400`: 1: Group is invalid or does not exist. 8: Invalid or missing pagination parameters
- `401`: 0: Authorization has been denied for this request.
- `403`: 23: Insufficient permissions to complete the request.

**Response fields** (`Roblox.Groups.Api.GroupAuditLogPageResponse_Roblox.Groups.Api.Models.Response.GroupAuditLogResponseItem_`)

See [Roblox.Groups.Api.GroupAuditLogPageResponse_Roblox.Groups.Api.Models.Response.GroupAuditLogResponseItem_](#roblox-groups-api-groupauditlogpageresponse-roblox-groups-api-models-response-groupauditlogresponseitem-) in Models.

**Response example:**
```json
{
  "previousPageCursor": "string",
  "nextPageCursor": "string",
  "data": [
    {
      "actor": "...",
      "actionType": "...",
      "description": "...",
      "created": "..."
    }
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/legacy-groups/v1/groups/{GROUPID}/audit-log"
```

### PATCH `/legacy-groups/v1/groups/{groupId}/description`

Updates the groups description

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `legacy-group:manage`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | path | `integer` | Yes | The id of the group the user is in. |

**Request Body:** `application/json` — Type: `Roblox.Groups.Api.UpdateGroupDescriptionRequest`

See [Roblox.Groups.Api.UpdateGroupDescriptionRequest](#roblox-groups-api-updategroupdescriptionrequest) in Models.

**Request example:**
```json
{
  "description": "string"
}
```

**Responses:**

- `200`: OK → `Roblox.Groups.Api.GroupDescriptionResponse`
- `400`: 1: Group is invalid or does not exist. 29: Your group description was empty.
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed 18: The description is too long. 23: Insufficient permissions to complete the request.

**Response fields** (`Roblox.Groups.Api.GroupDescriptionResponse`)

See [Roblox.Groups.Api.GroupDescriptionResponse](#roblox-groups-api-groupdescriptionresponse) in Models.

**Response example:**
```json
{
  "newDescription": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X PATCH -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/legacy-groups/v1/groups/{GROUPID}/description" \
  -H "Content-Type: application/json" \
  -d '{
  "description": "string"
}'
```

### PATCH `/legacy-groups/v1/groups/{groupId}/notification-preference`

Updates the group's settings

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `legacy-user:manage`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | path | `integer` | Yes | The id of the group the user is in. |

**Request Body:** `application/json` — Type: `Roblox.Groups.Api.UpdateGroupNotificationPreferenceRequest`

See [Roblox.Groups.Api.UpdateGroupNotificationPreferenceRequest](#roblox-groups-api-updategroupnotificationpreferencerequest) in Models.

**Request example:**
```json
{
  "notificationsEnabled": false,
  "type": 0
}
```

**Responses:**

- `200`: OK → `0 \| 1 \| 2 \| 3`
- `400`: 1: Group is invalid or does not exist.
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X PATCH -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/legacy-groups/v1/groups/{GROUPID}/notification-preference" \
  -H "Content-Type: application/json" \
  -d '{
  "notificationsEnabled": false,
  "type": 0
}'
```

### GET `/legacy-groups/v1/groups/{groupId}/settings`

Gets the Group's settings

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `legacy-group:manage`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | path | `integer` | Yes | The id of the group the user is in. |

**Responses:**

- `200`: OK → `Roblox.Groups.Api.GroupSettingsResponse`
- `400`: 1: Group is invalid or does not exist.
- `401`: 0: Authorization has been denied for this request.
- `403`: 23: Insufficient permissions to complete the request.

**Response fields** (`Roblox.Groups.Api.GroupSettingsResponse`)

See [Roblox.Groups.Api.GroupSettingsResponse](#roblox-groups-api-groupsettingsresponse) in Models.

**Response example:**
```json
{
  "isApprovalRequired": false,
  "isBuildersClubRequired": false,
  "areEnemiesAllowed": false,
  "areGroupFundsVisible": false,
  "areGroupGamesVisible": false,
  "isGroupNameChangeEnabled": false
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/legacy-groups/v1/groups/{GROUPID}/settings"
```

### PATCH `/legacy-groups/v1/groups/{groupId}/settings`

Updates the group's settings

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `legacy-group:manage`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | path | `integer` | Yes | The id of the group the user is in. |

**Request Body:** `application/json` — Type: `Roblox.Groups.Api.UpdateGroupSettingsRequest`

See [Roblox.Groups.Api.UpdateGroupSettingsRequest](#roblox-groups-api-updategroupsettingsrequest) in Models.

**Request example:**
```json
{
  "isApprovalRequired": false,
  "areEnemiesAllowed": false,
  "areGroupFundsVisible": false,
  "areGroupGamesVisible": false,
  "verificationLevel": 0,
  "accountTenureRequirement": 0
}
```

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.ApiEmptyResponseModel`
- `400`: 1: Group is invalid or does not exist.
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed 23: Insufficient permissions to complete the request.
- `503`: 31: Service is currently unavailable.

**Response fields** (`Roblox.Web.WebAPI.ApiEmptyResponseModel`)

See [Roblox.Web.WebAPI.ApiEmptyResponseModel](#roblox-web-webapi-apiemptyresponsemodel) in Models.

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X PATCH -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/legacy-groups/v1/groups/{GROUPID}/settings" \
  -H "Content-Type: application/json" \
  -d '{
  "isApprovalRequired": false,
  "areEnemiesAllowed": false,
  "areGroupFundsVisible": false,
  "areGroupGamesVisible": false,
  "verificationLevel": 0,
  "accountTenureRequirement": 0
}'
```

### PATCH `/legacy-groups/v1/groups/{groupId}/status`

Sets group status

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `legacy-group:manage`

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | path | `integer` | Yes | The group Id. |

**Request Body:** `application/json` — Type: `Roblox.Groups.Api.PostGroupStatusRequest`

See [Roblox.Groups.Api.PostGroupStatusRequest](#roblox-groups-api-postgroupstatusrequest) in Models.

**Request example:**
```json
{
  "message": "string"
}
```

**Responses:**

- `200`: OK → `Roblox.Groups.Api.ShoutResponse`
- `400`: 1: Group is invalid or does not exist. 7: Missing group status content. 32: Description was filtered.
- `401`: 0: Authorization has been denied for this request.
- `403`: 0: Token Validation Failed 6: You are not authorized to set the status of this group

**Response fields** (`Roblox.Groups.Api.ShoutResponse`)

See [Roblox.Groups.Api.ShoutResponse](#roblox-groups-api-shoutresponse) in Models.

**Response example:**
```json
{
  "body": "string",
  "poster": {
    "buildersClubMembershipType": 0,
    "hasVerifiedBadge": false,
    "userId": 0,
    "username": "string",
    "displayName": "string"
  },
  "created": "2024-01-01T00:00:00Z",
  "updated": "2024-01-01T00:00:00Z"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -X PATCH -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/legacy-groups/v1/groups/{GROUPID}/status" \
  -H "Content-Type: application/json" \
  -d '{
  "message": "string"
}'
```

### GET `/legacy-groups/v1/user/groups/pending`

Gets groups that the authenticated user has requested to join

**Auth:** API Key (`x-api-key` header) or OAuth 2.0 Bearer token

**Scopes:** `legacy-group:manage`

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Groups.Api.GroupDetailResponse_`
- `401`: 0: Authorization has been denied for this request.

**Response fields** (`Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Groups.Api.GroupDetailResponse_`)

See [Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Groups.Api.GroupDetailResponse_](#roblox-web-webapi-models-apiarrayresponse-roblox-groups-api-groupdetailresponse-) in Models.

**Response example:**
```json
{
  "data": [
    {
      "id": "...",
      "name": "...",
      "description": "...",
      "owner": "...",
      "shout": "...",
      "memberCount": "..."
    }
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Rate Limits:** perApiKeyOwner: 100/minute, perOauth2Authorization: 100/minute

**Example:**
```bash
curl -H "x-api-key: $ROBLOX_API_KEY" \
  "https://apis.roblox.com/legacy-groups/v1/user/groups/pending"
```

### GET `/v1/groups/icons` [STABLE]

Fetches thumbnail URLs for a list of groups. Ids that do not correspond to groups will be filtered out.

**Server:** `https://thumbnails.roblox.com`

**Auth:** 

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupIds` | query | `integer[]` | Yes |  |
| `size` | query | `150x150 \| 420x420` | No | The thumbnail size, formatted widthxheight Valid values: `150x150`, `420x420` |
| `format` | query | `Png \| Webp` | No | The thumbnail format Valid values: `Png`, `Webp` |
| `isCircular` | query | `true \| false` | No | The circle thumbnail output parameter, true or false Valid values: `true`, `false` |

**Responses:**

- `200`: OK
- `400`: 1: There are too many requested Ids. 2: The requested image format is invalid. Please see documentation for valid thumbnail format parameter name and values. 3: The requested size is invalid. Please see documentation for valid thumbnail size parameter name and format. 4: The requested Ids are invalid, of an invalid type or missing. 10: Circular thumbnail requests are not allowed

**Example:**
```bash
curl -H "Authorization: Bearer $ROBLOX_ACCESS_TOKEN" \
  "https://thumbnails.roblox.com/v1/groups/icons?groupIds={VALUE}"
```

### GET `/v1/groups/{groupId}/addfunds/allowed` [EXPERIMENTAL]

**Server:** `https://economy.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | path | `integer` | Yes |  |

**Responses:**

- `200`: OK → `boolean`
- `400`: 2: The group is invalid.
- `403`: 3: Insufficient permissions.

**Error handling:** `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://economy.roblox.com/v1/groups/{GROUPID}/addfunds/allowed"
```

### GET `/v1/groups/{groupId}/addfunds/latest` [EXPERIMENTAL]

**Server:** `https://economy.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | path | `integer` | Yes |  |

**Responses:**

- `200`: OK → `Roblox.Economy.Api.Models.LatestAddFundsResponse`
- `400`: 2: The group is invalid.
- `403`: 3: Insufficient permissions.

**Response fields** (`Roblox.Economy.Api.Models.LatestAddFundsResponse`)

See [Roblox.Economy.Api.Models.LatestAddFundsResponse](#roblox-economy-api-models-latestaddfundsresponse) in Models.

**Response example:**
```json
{
  "transactionDate": "string",
  "rateLimitInDays": 0
}
```

**Error handling:** `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://economy.roblox.com/v1/groups/{GROUPID}/addfunds/latest"
```

### GET `/v1/groups/{groupId}/currency` [EXPERIMENTAL]

Gets currency for the specified group.

Currency can only be retrieved for groups the authenticated user has permission to view group funds for.

**Server:** `https://economy.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | path | `integer` | Yes | The group Id to get the currency for. |

**Responses:**

- `200`: OK → `Roblox.Web.Responses.Economy.CurrencyResponse`
- `400`: 2: The group is invalid.
- `403`: 3: Insufficient permissions.

**Response fields** (`Roblox.Web.Responses.Economy.CurrencyResponse`)

See [Roblox.Web.Responses.Economy.CurrencyResponse](#roblox-web-responses-economy-currencyresponse) in Models.

**Response example:**
```json
{
  "robux": 0
}
```

**Error handling:** `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://economy.roblox.com/v1/groups/{GROUPID}/currency"
```

### GET `/v1/groups/{groupId}/payouts/latest` [BETA]

Gets the latest one-time payout for each requested user.

**Server:** `https://groups.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | path | `integer` | Yes |  |
| `userIds` | query | `string[]` | No |  |

**Responses:**

- `200`: Success → `PublicAllOneTimePayoutsResponseModel`
- `400`: Bad Request → `OrganizationsServiceApi.ErrorResponse`
- `401`: Unauthorized → `OrganizationsServiceApi.ErrorResponse`
- `403`: Forbidden → `OrganizationsServiceApi.ErrorResponse`

**Response fields** (`PublicAllOneTimePayoutsResponseModel`)

See [PublicAllOneTimePayoutsResponseModel](#publicallonetimepayoutsresponsemodel) in Models.

**Response example:**
```json
{
  "payouts": [
    {
      "recipientUserId": "...",
      "status": "...",
      "oneTimePayout": "..."
    }
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://groups.roblox.com/v1/groups/{GROUPID}/payouts/latest"
```

### GET `/v1/groups/{groupId}/payouts/suggested` [BETA]

Gets suggested one-time payouts for eligible collaborators.

**Server:** `https://groups.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | path | `integer` | Yes |  |

**Responses:**

- `200`: Success → `PublicAllOneTimePayoutsResponseModel`
- `401`: Unauthorized → `OrganizationsServiceApi.ErrorResponse`
- `403`: Forbidden → `OrganizationsServiceApi.ErrorResponse`

**Response fields** (`PublicAllOneTimePayoutsResponseModel`)

See [PublicAllOneTimePayoutsResponseModel](#publicallonetimepayoutsresponsemodel) in Models.

**Response example:**
```json
{
  "payouts": [
    {
      "recipientUserId": "...",
      "status": "...",
      "oneTimePayout": "..."
    }
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://groups.roblox.com/v1/groups/{GROUPID}/payouts/suggested"
```

### GET `/v1/groups/{groupId}/payouts/universes` [BETA]

Gets payout-visible universes for a group.

**Server:** `https://groups.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | path | `integer` | Yes |  |
| `limit` | query | `integer` | No |  |
| `cursor` | query | `string` | No |  |

**Responses:**

- `200`: Success → `PublicGroupUniversePayoutPageResponseModel`
- `400`: Bad Request → `OrganizationsServiceApi.ErrorResponse`
- `401`: Unauthorized → `OrganizationsServiceApi.ErrorResponse`
- `403`: Forbidden → `OrganizationsServiceApi.ErrorResponse`

**Response fields** (`PublicGroupUniversePayoutPageResponseModel`)

See [PublicGroupUniversePayoutPageResponseModel](#publicgroupuniversepayoutpageresponsemodel) in Models.

**Response example:**
```json
{
  "data": [
    {
      "universeId": "...",
      "percentage": "..."
    }
  ],
  "nextPageCursor": "string",
  "previousPageCursor": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://groups.roblox.com/v1/groups/{GROUPID}/payouts/universes"
```

### GET `/v1/groups/{groupId}/revenue/summary/{timeFrame}` [EXPERIMENTAL]

**Server:** `https://economy.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | path | `integer` | Yes |  |
| `timeFrame` | path | `RevenueSummaryTimeFrame` | Yes | Valid values: `Day`, `Week`, `Month`, `Year` |

**Responses:**

- `200`: OK → `RevenueSummaryResponse`

**Response fields** (`RevenueSummaryResponse`)

See [RevenueSummaryResponse](#revenuesummaryresponse) in Models.

**Response example:**
```json
{
  "recurringRobuxStipend": 0,
  "itemSaleRobux": 0,
  "purchasedRobux": 0,
  "tradeSystemRobux": 0,
  "pendingRobux": 0,
  "groupPayoutRobux": 0
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://economy.roblox.com/v1/groups/{GROUPID}/revenue/summary/{TIMEFRAME}"
```

### GET `/v1/groups/{groupId}/snapshot-robux` [EXPERIMENTAL]

Gets the robux amount at old dev-ex rate for the specified group.
The response field RobuxAt35 is the amount of robux a group has at the dev ex rate of $3.50 per 1000 robux.

Snapshot robux can only be retrieved for groups the authenticated user has permission to view group funds for.

**Server:** `https://economy.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | path | `integer` | Yes | The group Id to get the snapshot robux amount for. |

**Responses:**

- `200`: OK → `Roblox.Economy.Api.Models.GetGroupSnapshotRobuxResponse`
- `400`: 2: The group is invalid.
- `403`: 3: Insufficient permissions.

**Response fields** (`Roblox.Economy.Api.Models.GetGroupSnapshotRobuxResponse`)

See [Roblox.Economy.Api.Models.GetGroupSnapshotRobuxResponse](#roblox-economy-api-models-getgroupsnapshotrobuxresponse) in Models.

**Response example:**
```json
{
  "robuxAt35": 0
}
```

**Error handling:** `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://economy.roblox.com/v1/groups/{GROUPID}/snapshot-robux"
```

### GET `/v1/groups/{groupId}/universes` [EXPERIMENTAL]

Gets a list of universes for the given group.

**Server:** `https://develop.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | path | `integer` | Yes | The group id. |
| `isArchived` | query | `boolean` | No | Whether or not to return archived games. |
| `limit` | query | `10 \| 25 \| 50 \| 100` | No | The number of results per request. Valid values: `10`, `25`, `50`, `100` |
| `cursor` | query | `string` | No | The paging cursor for the previous or next page. |
| `sortOrder` | query | `Asc \| Desc` | No | Sorted by universeId Valid values: `Asc`, `Desc` |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Api.Develop.Models.UniverseModel_`
- `400`: Invalid groupId.

**Response fields** (`Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Api.Develop.Models.UniverseModel_`)

See [Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Api.Develop.Models.UniverseModel_](#roblox-web-webapi-models-apipageresponse-roblox-api-develop-models-universemodel-) in Models.

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
      "isArchived": "...",
      "rootPlaceId": "...",
      "isActive": "..."
    }
  ]
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://develop.roblox.com/v1/groups/{GROUPID}/universes"
```

### GET `/v1/groups/{groupId}/users-payout-eligibility` [EXPERIMENTAL]

Gets the group payout eligibility for a group of users.

**Server:** `https://economy.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | path | `integer` | Yes |  |
| `userIds` | query | `integer[]` | Yes |  |

**Responses:**

- `200`: OK → `Roblox.Economy.Api.Models.UserGroupPayoutEligibilityResponseModel`
- `401`: 0: Authorization has been denied for this request.

**Response fields** (`Roblox.Economy.Api.Models.UserGroupPayoutEligibilityResponseModel`)

See [Roblox.Economy.Api.Models.UserGroupPayoutEligibilityResponseModel](#roblox-economy-api-models-usergrouppayouteligibilityresponsemodel) in Models.

**Response example:**
```json
{
  "usersGroupPayoutEligibility": "..."
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://economy.roblox.com/v1/groups/{GROUPID}/users-payout-eligibility?userIds={VALUE}"
```

### GET `/v1/universes/{universeId}/payouts` [BETA]

Gets recurring payouts for a group-owned universe.

**Server:** `https://groups.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `universeId` | path | `integer` | Yes |  |

**Responses:**

- `200`: Success → `PublicAllGroupUniversePayoutsResponseModel`
- `401`: Unauthorized → `OrganizationsServiceApi.ErrorResponse`
- `403`: Forbidden → `OrganizationsServiceApi.ErrorResponse`
- `404`: Not Found → `OrganizationsServiceApi.ErrorResponse`

**Response fields** (`PublicAllGroupUniversePayoutsResponseModel`)

See [PublicAllGroupUniversePayoutsResponseModel](#publicallgroupuniversepayoutsresponsemodel) in Models.

**Response example:**
```json
{
  "payouts": [
    {
      "userId": "...",
      "percentage": "..."
    }
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://groups.roblox.com/v1/universes/{UNIVERSEID}/payouts"
```

### GET `/v1/user/groups/canmanage` [EXPERIMENTAL]

Gets a list of Groups that a user can manage.

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
  "https://develop.roblox.com/v1/user/groups/canmanage"
```

### PATCH `/v1/vip-servers/{id}/permissions`

**Server:** `https://games.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `id` | path | `integer` | Yes |  |

**Request Body:** `application/json` — Type: `PrivateServerUpdatePermissionsRequest`

See [PrivateServerUpdatePermissionsRequest](#privateserverupdatepermissionsrequest) in Models.

**Request example:**
```json
{
  "clanAllowed": false,
  "enemyClanId": 0,
  "friendsAllowed": false,
  "usersToAdd": [
    0
  ],
  "usersToRemove": [
    0
  ]
}
```

**Responses:**

- `200`: OK → `PrivateServerPermissionsResponse`

**Response fields** (`PrivateServerPermissionsResponse`)

See [PrivateServerPermissionsResponse](#privateserverpermissionsresponse) in Models.

**Response example:**
```json
{
  "clanAllowed": false,
  "enemyClanId": 0,
  "friendsAllowed": false,
  "users": [
    {
      "id": "...",
      "name": "...",
      "displayName": "..."
    }
  ]
}
```

**Example:**
```bash
curl -X PATCH -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://games.roblox.com/v1/vip-servers/{ID}/permissions" \
  -H "Content-Type: application/json" \
  -d '{
  "clanAllowed": false,
  "enemyClanId": 0,
  "friendsAllowed": false,
  "usersToAdd": [
    0
  ],
  "usersToRemove": [
    0
  ]
}'
```

### GET `/v2/groups/{groupId}/games`

Gets experiences created by the specified group id.

**Server:** `https://games.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | path | `integer` | Yes | The group Id |
| `accessFilter` | query | `1 \| 2 \| 4` | No | The access type of the experiences. Valid values: `1`, `2`, `4` |
| `limit` | query | `10 \| 25 \| 50 \| 100` | No | The number of results per request. Valid values: `10`, `25`, `50`, `100` |
| `cursor` | query | `string` | No | The paging cursor for the previous or next page. |
| `sortOrder` | query | `Asc \| Desc` | No | The order the results are sorted in. Valid values: `Asc`, `Desc` |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Groups.Api.Models.Response.GroupExperienceResponse_`
- `501`: 47: Code path is not implemented.

**Response fields** (`Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Groups.Api.Models.Response.GroupExperienceResponse_`)

See [Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Groups.Api.Models.Response.GroupExperienceResponse_](#roblox-web-webapi-models-apipageresponse-roblox-groups-api-models-response-groupexperienceresponse-) in Models.

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
      "creator": "...",
      "rootPlace": "...",
      "created": "..."
    }
  ]
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://games.roblox.com/v2/groups/{GROUPID}/games"
```

### GET `/v2/groups/{groupId}/gamesV2`

Gets experiences created by the specified group id.

**Server:** `https://games.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | path | `integer` | Yes | The group Id |
| `accessFilter` | query | `1 \| 2 \| 4` | No | The access type of the experiences. Valid values: `1`, `2`, `4` |
| `limit` | query | `10 \| 25 \| 50 \| 100` | No | The number of results per request. Valid values: `10`, `25`, `50`, `100` |
| `cursor` | query | `string` | No | The paging cursor for the previous or next page. |
| `sortOrder` | query | `Asc \| Desc` | No | The order the results are sorted in. Valid values: `Asc`, `Desc` |

**Responses:**

- `200`: OK → `Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Groups.Api.Models.Response.GroupExperienceResponse_`
- `501`: 47: Code path is not implemented.

**Response fields** (`Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Groups.Api.Models.Response.GroupExperienceResponse_`)

See [Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Groups.Api.Models.Response.GroupExperienceResponse_](#roblox-web-webapi-models-apipageresponse-roblox-groups-api-models-response-groupexperienceresponse-) in Models.

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
      "creator": "...",
      "rootPlace": "...",
      "created": "..."
    }
  ]
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://games.roblox.com/v2/groups/{GROUPID}/gamesV2"
```

### GET `/v2/groups/{groupId}/invitations` [BETA]

List open invitations to a group

**Server:** `https://groups.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | path | `integer` | Yes |  |
| `Cursor` | query | `string` | No | Cursor returned by a previous page. Omit for the first page. |
| `Limit` | query | `integer` | No | Page size: 10, 25, 50, or 100. Defaults to 10. |
| `SortOrder` | query | `SortOrder` | No | Sort order. Only `Asc` is currently supported; defaults to `Asc`. Valid values: `Asc`, `Desc` |

**Responses:**

- `200`: Success → `GroupInvitationCursorPageResponse`
- `400`: Bad Request → `OrganizationsServiceApi.ErrorResponse`
- `401`: Unauthorized → `OrganizationsServiceApi.ErrorResponse`
- `403`: Forbidden → `OrganizationsServiceApi.ErrorResponse`
- `404`: Not Found → `OrganizationsServiceApi.ErrorResponse`
- `500`: Server Error → `OrganizationsServiceApi.ErrorResponse`

**Response fields** (`GroupInvitationCursorPageResponse`)

See [GroupInvitationCursorPageResponse](#groupinvitationcursorpageresponse) in Models.

**Response example:**
```json
{
  "data": [
    {
      "id": "...",
      "groupId": "...",
      "recipientUserId": "...",
      "senderUserId": "...",
      "status": "...",
      "roleIds": "..."
    }
  ],
  "nextPageCursor": "string",
  "previousPageCursor": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://groups.roblox.com/v2/groups/{GROUPID}/invitations"
```

### POST `/v2/groups/{groupId}/invitations` [BETA]

Invite a user to a group

**Server:** `https://groups.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | path | `integer` | Yes |  |
| `isSecure` | query | `boolean` | No |  |

**Request Body:** `application/json-patch+json` — Type: `CreateGroupInvitationRequestModel`

See [CreateGroupInvitationRequestModel](#creategroupinvitationrequestmodel) in Models.

**Request example:**
```json
{
  "recipientUserId": 0,
  "roleIds": [
    0
  ]
}
```

**Responses:**

- `200`: Success → `GroupInvitation`
- `400`: Bad Request → `OrganizationsServiceApi.ErrorResponse`
- `401`: Unauthorized → `OrganizationsServiceApi.ErrorResponse`
- `403`: Forbidden → `OrganizationsServiceApi.ErrorResponse`
- `404`: Not Found → `OrganizationsServiceApi.ErrorResponse`
- `429`: Too Many Requests → `OrganizationsServiceApi.ErrorResponse`
- `500`: Server Error → `OrganizationsServiceApi.ErrorResponse`

**Response fields** (`GroupInvitation`)

See [GroupInvitation](#groupinvitation) in Models.

**Response example:**
```json
{
  "id": "string",
  "groupId": 0,
  "recipientUserId": 0,
  "senderUserId": 0,
  "status": "Open",
  "roleIds": [
    0
  ]
}
```

**Error handling:** `429`: Retry with exponential backoff (start at 1s). `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X POST -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://groups.roblox.com/v2/groups/{GROUPID}/invitations" \
  -H "Content-Type: application/json" \
  -d '{
  "recipientUserId": 0,
  "roleIds": [
    0
  ]
}'
```

### GET `/v2/groups/{groupId}/invitations/{invitationId}` [BETA]

Get an invitation to a group

**Server:** `https://groups.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | path | `integer` | Yes |  |
| `invitationId` | path | `integer` | Yes |  |

**Responses:**

- `200`: Success → `GroupInvitation`
- `401`: Unauthorized → `OrganizationsServiceApi.ErrorResponse`
- `403`: Forbidden → `OrganizationsServiceApi.ErrorResponse`
- `404`: Not Found → `OrganizationsServiceApi.ErrorResponse`
- `500`: Server Error → `OrganizationsServiceApi.ErrorResponse`

**Response fields** (`GroupInvitation`)

See [GroupInvitation](#groupinvitation) in Models.

**Response example:**
```json
{
  "id": "string",
  "groupId": 0,
  "recipientUserId": 0,
  "senderUserId": 0,
  "status": "Open",
  "roleIds": [
    0
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://groups.roblox.com/v2/groups/{GROUPID}/invitations/{INVITATIONID}"
```

### PATCH `/v2/groups/{groupId}/invitations/{invitationId}` [BETA]

Accept or decline an invitation to a group (recipient)

**Server:** `https://groups.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | path | `integer` | Yes |  |
| `invitationId` | path | `integer` | Yes |  |

**Request Body:** `application/json-patch+json` — Type: `UpdateGroupInvitationRequestModel`

See [UpdateGroupInvitationRequestModel](#updategroupinvitationrequestmodel) in Models.

**Request example:**
```json
{
  "status": "Open"
}
```

**Responses:**

- `200`: Success → `SuccessResponse`
- `400`: Bad Request → `OrganizationsServiceApi.ErrorResponse`
- `401`: Unauthorized → `OrganizationsServiceApi.ErrorResponse`
- `403`: Forbidden → `OrganizationsServiceApi.ErrorResponse`
- `404`: Not Found → `OrganizationsServiceApi.ErrorResponse`
- `500`: Server Error → `OrganizationsServiceApi.ErrorResponse`

**Response fields** (`SuccessResponse`)

See [SuccessResponse](#successresponse) in Models.

**Response example:**
```json
{
  "success": false
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X PATCH -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://groups.roblox.com/v2/groups/{GROUPID}/invitations/{INVITATIONID}" \
  -H "Content-Type: application/json" \
  -d '{
  "status": "Open"
}'
```

### DELETE `/v2/groups/{groupId}/invitations/{invitationId}` [BETA]

Revoke an invitation to a group (member manager)

**Server:** `https://groups.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | path | `integer` | Yes |  |
| `invitationId` | path | `integer` | Yes |  |

**Responses:**

- `200`: Success → `SuccessResponse`
- `401`: Unauthorized → `OrganizationsServiceApi.ErrorResponse`
- `403`: Forbidden → `OrganizationsServiceApi.ErrorResponse`
- `404`: Not Found → `OrganizationsServiceApi.ErrorResponse`
- `500`: Server Error → `OrganizationsServiceApi.ErrorResponse`

**Response fields** (`SuccessResponse`)

See [SuccessResponse](#successresponse) in Models.

**Response example:**
```json
{
  "success": false
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -X DELETE -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://groups.roblox.com/v2/groups/{GROUPID}/invitations/{INVITATIONID}"
```

### GET `/v2/groups/{groupId}/roles/{roleId}/invitations` [BETA]

List open invitations to a group that grant a role

**Server:** `https://groups.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | path | `integer` | Yes |  |
| `roleId` | path | `integer` | Yes |  |
| `Cursor` | query | `string` | No | Cursor returned by a previous page. Omit for the first page. |
| `Limit` | query | `integer` | No | Page size: 10, 25, 50, or 100. Defaults to 10. |
| `SortOrder` | query | `SortOrder` | No | Sort order. Only `Asc` is currently supported; defaults to `Asc`. Valid values: `Asc`, `Desc` |

**Responses:**

- `200`: Success → `GroupInvitationCursorPageResponse`
- `400`: Bad Request → `OrganizationsServiceApi.ErrorResponse`
- `401`: Unauthorized → `OrganizationsServiceApi.ErrorResponse`
- `403`: Forbidden → `OrganizationsServiceApi.ErrorResponse`
- `404`: Not Found → `OrganizationsServiceApi.ErrorResponse`
- `500`: Server Error → `OrganizationsServiceApi.ErrorResponse`

**Response fields** (`GroupInvitationCursorPageResponse`)

See [GroupInvitationCursorPageResponse](#groupinvitationcursorpageresponse) in Models.

**Response example:**
```json
{
  "data": [
    {
      "id": "...",
      "groupId": "...",
      "recipientUserId": "...",
      "senderUserId": "...",
      "status": "...",
      "roleIds": "..."
    }
  ],
  "nextPageCursor": "string",
  "previousPageCursor": "string"
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://groups.roblox.com/v2/groups/{GROUPID}/roles/{ROLEID}/invitations"
```

### GET `/v2/groups/{groupId}/transactions` [EXPERIMENTAL]

**Server:** `https://economy.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | path | `integer` | Yes |  |
| `exclusiveStartRequest` | query | `Int64ExclusiveStartKeyCursor` | No |  |
| `transactionType` | query | `TransactionType` | No | Valid values: `Undefined`, `Sale`, `Purchase`, `AffiliateSale`, `DevEx`, `GroupPayout`, `AdImpressionPayout`, `CurrencyPurchase`, `TradeRobux`, `PremiumStipend`, `PendingRobux`, `EngagementPayout`, `GroupEngagementPayout`, `AdSpend`, `Summary`, `IndividualToGroup`, `CSAdjustment`, `AdsRevsharePayout`, `GroupAdsRevsharePayout`, `SubscriptionsRevsharePayout`, `GroupSubscriptionsRevsharePayout`, `SubscriptionsRevshareClawback`, `GroupSubscriptionsRevshareClawback`, `PublishingAdvanceRebates`, `AffiliatePayout`, `LicensingPayment`, `LicensingPaymentClawback`, `CurrencyTransfer`, `RobloxSelectTransfer`, `PrivateServerEngagementPayout`, `CurrencySubscriptionStipend`, `SubscriptionReferralPayout`, `CreatorRewardsPayout`, `Gifts` |

**Responses:**

- `200`: OK → `TransactionResponseApiPageResponse`

**Response fields** (`TransactionResponseApiPageResponse`)

See [TransactionResponseApiPageResponse](#transactionresponseapipageresponse) in Models.

**Response example:**
```json
{
  "previousPageCursor": "string",
  "nextPageCursor": "string",
  "data": [
    {
      "id": "...",
      "idHash": "...",
      "created": "...",
      "isPending": "...",
      "agent": "...",
      "details": "..."
    }
  ]
}
```

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://economy.roblox.com/v2/groups/{GROUPID}/transactions"
```

### GET `/v2/groups/{groupId}/users/{userId}/invitation` [BETA]

Get the open invitation to a group for a user

**Server:** `https://groups.roblox.com`

**Auth:** Cookie (`.ROBLOSECURITY`)

**Parameters:**

| Name | In | Type | Required | Description |
|------|-----|------|----------|-------------|
| `groupId` | path | `integer` | Yes |  |
| `userId` | path | `integer` | Yes |  |

**Responses:**

- `200`: Success → `GroupInvitation`
- `401`: Unauthorized → `OrganizationsServiceApi.ErrorResponse`
- `403`: Forbidden → `OrganizationsServiceApi.ErrorResponse`
- `404`: Not Found → `OrganizationsServiceApi.ErrorResponse`
- `500`: Server Error → `OrganizationsServiceApi.ErrorResponse`

**Response fields** (`GroupInvitation`)

See [GroupInvitation](#groupinvitation) in Models.

**Response example:**
```json
{
  "id": "string",
  "groupId": 0,
  "recipientUserId": 0,
  "senderUserId": 0,
  "status": "Open",
  "roleIds": [
    0
  ]
}
```

**Error handling:** `401`: Check that your API key/token is valid and not expired. `403`: Verify your API key has the required scopes listed above. 

**Example:**
```bash
curl -b ".ROBLOSECURITY=$ROBLOSECURITY" \
  "https://groups.roblox.com/v2/groups/{GROUPID}/users/{USERID}/invitation"
```

## Models

### Group

A mini-community within Roblox for communication, discussions, and more.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `path` | `string` | No | The resource path of the group.  Format: `groups/{group_id}` |
| `createTime` | `string` | No | The timestamp when the group was created. |
| `updateTime` | `string` | No | The timestamp when the group was last updated. |
| `id` | `string` | No | A unique ID that identifies the group. |
| `displayName` | `string` | No | The name of the group.  Must be non-empty. Has a maximum limit of 50 characters. |
| `description` | `string` | No | The description of the group.  Has a maximum limit of 1000 characters. |
| `owner` | `string` | No | The resource path of the owner.  If the group is abandoned and has no owner, this field is not returned. |
| `memberCount` | `integer` | No | The total number of members within a group. |
| `publicEntryAllowed` | `boolean` | No | Whether the group allows public entry. |
| `locked` | `boolean` | No | Whether the group is locked.  A locked group is a group that has been moderated/banned by Roblox. |
| `verified` | `boolean` | No | Whether the group has the verified badge. |

### ListGroupForumCategoriesResponse

A list of GroupForumCategories in the parent collection.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `groupForumCategories` | `GroupForumCategory[]` | No | The GroupForumCategories from the specified Group. |
| `nextPageToken` | `string` | No | A token that you can send as a `pageToken` parameter to retrieve the next page. If this field is omitted, there are no subsequent pages. |

### ListGroupForumPostsResponse

A list of GroupForumPosts in the parent collection.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `groupForumPosts` | `GroupForumPost[]` | No | The GroupForumPosts from the specified GroupForumCategory. |
| `nextPageToken` | `string` | No | A token that you can send as a `pageToken` parameter to retrieve the next page. If this field is omitted, there are no subsequent pages. |

### ListGroupForumCommentsResponse

A list of GroupForumComments in the parent collection.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `groupForumComments` | `GroupForumComment[]` | No | The GroupForumComments from the specified GroupForumPost. |
| `nextPageToken` | `string` | No | A token that you can send as a `pageToken` parameter to retrieve the next page. If this field is omitted, there are no subsequent pages. |

### ListGroupJoinRequestsResponse

A list of GroupJoinRequests in the parent collection.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `groupJoinRequests` | `GroupJoinRequest[]` | No | The GroupJoinRequests from the specified Group. |
| `nextPageToken` | `string` | No | A token that you can send as a `pageToken` parameter to retrieve the next page. If this field is omitted, there are no subsequent pages. |

### AcceptGroupJoinRequestRequest

A join request ID.

| Property | Type | Required | Description |
|----------|------|----------|-------------|

### DeclineGroupJoinRequestRequest

A join request ID.

| Property | Type | Required | Description |
|----------|------|----------|-------------|

### ListGroupMembershipsResponse

A list of GroupMemberships in the parent collection.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `groupMemberships` | `GroupMembership[]` | No | The GroupMemberships from the specified Group. |
| `nextPageToken` | `string` | No | A token that you can send as a `pageToken` parameter to retrieve the next page. If this field is omitted, there are no subsequent pages. |

### GroupMembership

A membership to a group. A user ID can be used in place of a membership ID.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `path` | `string` | No | The resource path of the group membership.  Format: `groups/{group_id}/memberships/{group_membership_id}` |
| `createTime` | `string` | No | The timestamp when the group membership was created. |
| `updateTime` | `string` | No | The timestamp when the group membership was last updated. |
| `user` | `string` | No |  *(immutable)* The resource path of a member of the group. |
| `role` | `string` | No | The resource path of the member's highest-ranked role. When the member holds multiple roles, this reflects only the highest-ranked one. Prefer using the `roles` field, which always contains the complete set of assigned roles. |
| `roles` | `string[]` | No | The resource paths of all roles assigned to the group member. This is the recommended field for reading a member's roles, as it always contains the complete set of roles held by the member. |

### AssignRoleGroupMembershipRequest

Assigns a role to the specified group membership.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `role` | `string` | Yes | The resource path of the role to assign.  Format: `groups/{group_id}/roles/{group_role_id}` |

### UnassignRoleGroupMembershipRequest

Unassigns a role from the specified group membership.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `role` | `string` | Yes | The resource path of the role to unassign.  Format: `groups/{group_id}/roles/{group_role_id}` |

### ListGroupRolesResponse

A list of GroupRoles in the parent collection.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `groupRoles` | `GroupRole[]` | No | The GroupRoles from the specified Group. |
| `nextPageToken` | `string` | No | A token that you can send as a `pageToken` parameter to retrieve the next page. If this field is omitted, there are no subsequent pages. |

### GroupRole

A configurable property to grant specific privileges for members within a
group.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `path` | `string` | No | The resource path of the group role.  Format: `groups/{group_id}/roles/{group_role_id}` |
| `createTime` | `string` | No | The timestamp for when the group role was last updated.  Visible only to owners of the group. |
| `updateTime` | `string` | No | The timestamp when the group role was last updated.  Visible only to owners of the group. |
| `id` | `string` | No | A unique ID that identifies a role.  Distinct from a role's rank, which is only unique within the group. |
| `displayName` | `string` | No | The name of the role.  Has a maximum limit of 100 characters. Names above the limit are rejected. |
| `description` | `string` | No | The description of the role.  Has a maximum limit of 1000 characters. Strings above the limit are rejected. Visible only to owners of the group. |
| `rank` | `integer` | No | The rank of the role.  The minimum value is 0. The maximum value is 255. |
| `memberCount` | `integer` | No | Total number of members within a role.  This field is not returned for guest roles. |
| `permissions` | `GroupRole_RolePermissions` | No | The permissions granted for this role.  This value is populated based on the read scope and role of the authorized user or API key creator. If the user or creator is the owner of the parent group, they are able to view all role permissions in the group. If the user or creator is a member of the parent group, they are able to view their role's permissions in the group. Anyone can view guest permissions. In the case that someone can't view the permissions, this field is not returned. |

### Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Api.Develop.Models.GroupModel_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `data` | `Roblox.Api.Develop.Models.GroupModel[]` | No |  |

### Roblox.Groups.Api.GroupPolicyRequest

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `groupIds` | `integer[]` | No |  |

### Roblox.Groups.Api.GroupPoliciesResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `groups` | `Roblox.Groups.Api.GroupPolicyResponse[]` | No |  |

### Roblox.Groups.Api.GroupAuditLogPageResponse_Roblox.Groups.Api.Models.Response.GroupAuditLogResponseItem_

ApiPageResponse for group audit log

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `previousPageCursor` | `string` | No |  |
| `nextPageCursor` | `string` | No |  |
| `data` | `Roblox.Groups.Api.Models.Response.GroupAuditLogResponseItem[]` | No |  |

### Roblox.Groups.Api.UpdateGroupDescriptionRequest

A request model for setting a description for the group

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `description` | `string` | No | The group description being set. |

### Roblox.Groups.Api.GroupDescriptionResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `newDescription` | `string` | No | The new description returned |

### Roblox.Groups.Api.UpdateGroupNotificationPreferenceRequest

A request model for updating a group's notification preference.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `notificationsEnabled` | `boolean` | No | Whether the user wants to receive notifications from the group. |
| `type` | `0 \| 1 \| 2 \| 3 \| 4` | No | ['AnnouncementCreatedNotification' = 0, 'ForumPostCreatedNotification' = 1, 'ForumCommentCreatedNotification' = 2, 'ForumCommentReplyCreatedNotification' = 3, 'ForumSubscriberNotification' = 4] |

### Roblox.Groups.Api.GroupSettingsResponse

Response model for Group Settings

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `isApprovalRequired` | `boolean` | No | Whether public entry is allowed. |
| `isBuildersClubRequired` | `boolean` | No | Whether Builder's Club is required. |
| `areEnemiesAllowed` | `boolean` | No | Whether enemy club declarations are allowed. |
| `areGroupFundsVisible` | `boolean` | No | Whether funds are publicly visible. |
| `areGroupGamesVisible` | `boolean` | No | Whether games are publicly visible. |
| `isGroupNameChangeEnabled` | `boolean` | No | If the group name change feature is enabled for this group. |
| `verificationLevel` | `0 \| 1 \| 2 \| 3` | No | The verification level for the group. Null if the verification level could not be determined due to an error. |
| `accountTenureRequirement` | `integer enum (6 values)` | No | The account tenure requirement for the group. Null if the account tenure requirement could not be determined due to an error. Values: 0, 1, 2, 3, 4, 5 |
| `slowmode` | `0 \| 1 \| 2 \| 3` | No | The slowmode level for the group (0-4). 0 = No slowmode, 1-4 = Slowmode levels with increasing restrictions. |
| `isMemberListVisibleToPublic` | `boolean` | No | Whether the group member list is visible to public. |
| `isAutoAssignRoleDisabled` | `boolean` | No | Whether automatic assignment of the lowest non-guest role is disabled for this group. For non-legacy groups (created after the multi-role cutoff), this is always true. For legacy groups, reflects the persisted GroupFeatureSettings value. Null when the value could not be determined. |
| `hasLegacyAutoAssignRole` | `boolean` | No | Whether this group still auto-assigns its lowest non-guest role to new members. |
| `communityTier` | `Roblox.Groups.Client.CommunityTierInfoResponse` | No |  |

### Roblox.Groups.Api.UpdateGroupSettingsRequest

A request model for updating a group's settings.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `isApprovalRequired` | `boolean` | No | Whether public entry is allowed. |
| `areEnemiesAllowed` | `boolean` | No | Whether enemy club declarations are allowed. |
| `areGroupFundsVisible` | `boolean` | No | Whether funds are publicly visible. |
| `areGroupGamesVisible` | `boolean` | No | Whether games are publicly visible. |
| `verificationLevel` | `0 \| 1 \| 2 \| 3` | No | The verification level for the group. |
| `accountTenureRequirement` | `integer enum (6 values)` | No | The account tenure requirement for the group. Values: 0, 1, 2, 3, 4, 5 |
| `slowmode` | `0 \| 1 \| 2 \| 3` | No | The slowmode level for the group (0-4). 0 = No slowmode, 1-4 = Slowmode levels with increasing restrictions. Null = No change to current slowmode setting. |
| `isMemberListVisibleToPublic` | `boolean` | No | Whether the group member list is visible to public. |

### Roblox.Groups.Api.PostGroupStatusRequest

A request model for setting the authenticated user's primary group.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `message` | `string` | No | The message to set the group status to. |

### Roblox.Groups.Api.ShoutResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `body` | `string` | No | The shout's message |
| `poster` | `Roblox.Groups.Api.Models.Response.UserModel` | No |  |
| `created` | `string` | No | The shout's created time |
| `updated` | `string` | No | The shout's last updated time |

### Roblox.Web.WebAPI.Models.ApiArrayResponse_Roblox.Groups.Api.GroupDetailResponse_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `data` | `Roblox.Groups.Api.GroupDetailResponse[]` | No |  |

### Roblox.Economy.Api.Models.LatestAddFundsResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `transactionDate` | `string` | No | Date of latest transfer |
| `rateLimitInDays` | `integer` | No | Days from the last transfer a new transfer is allowed |

### Roblox.Web.Responses.Economy.CurrencyResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `robux` | `integer` | No |  |

### PublicAllOneTimePayoutsResponseModel

Public response for one-time payouts.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `payouts` | `PublicOneTimePayoutResponseModel[]` | No |  |

### OrganizationsServiceApi.ErrorResponse

Standard error response model.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `code` | `OrganizationsServiceApi.ErrorCode` | Yes |  |
| `message` | `string` | No | The error message. |
| `field` | `string` | No | Field on which model validation failed. |

### PublicGroupUniversePayoutPageResponseModel

Public groups-style payout page.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `data` | `PublicUserUniversePayout[]` | No |  |
| `nextPageCursor` | `string` | No |  |
| `previousPageCursor` | `string` | No |  |

### RevenueSummaryTimeFrame

Values: `Day`, `Week`, `Month`, `Year`

### RevenueSummaryResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `recurringRobuxStipend` | `integer` | No |  |
| `itemSaleRobux` | `integer` | No |  |
| `purchasedRobux` | `integer` | No |  |
| `tradeSystemRobux` | `integer` | No |  |
| `pendingRobux` | `integer` | No |  |
| `groupPayoutRobux` | `integer` | No |  |
| `individualToGroupRobux` | `integer` | No |  |
| `premiumPayouts` | `integer` | No |  |
| `groupPremiumPayouts` | `integer` | No |  |
| `adjustmentRobux` | `integer` | No |  |
| `immersiveAdPayouts` | `integer` | No |  |
| `subscriptionPayouts` | `integer` | No |  |
| `subscriptionClawbacks` | `integer` | No |  |
| `isShowImmersiveAdPayoutSummaryOnZeroEnabled` | `boolean` | No |  |
| `commissionRobux` | `integer` | No |  |
| `publishingAdvanceRebates` | `integer` | No |  |
| `groupAffiliatePayoutRobux` | `integer` | No |  |
| `creatorRewardsPayoutRobux` | `integer` | No |  |

### Roblox.Economy.Api.Models.GetGroupSnapshotRobuxResponse

GetGroupSnapshotRobuxResponse.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `robuxAt35` | `integer` | No | Snapshot robux at the given rate. |

### Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Api.Develop.Models.UniverseModel_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `previousPageCursor` | `string` | No |  |
| `nextPageCursor` | `string` | No |  |
| `data` | `Roblox.Api.Develop.Models.UniverseModel[]` | No |  |

### Roblox.Economy.Api.Models.UserGroupPayoutEligibilityResponseModel

The response model for M:Roblox.Economy.Api.Controllers.V1.GroupPayoutsController.GetUserGroupPayoutEligibility(System.Int64,System.Collections.Generic.ICollection{System.Int64},System.Threading.CancellationToken)

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `usersGroupPayoutEligibility` | `object` | No | Gets the dictionary of (userId, groupPayoutEligibility) mapping. |

### PublicAllGroupUniversePayoutsResponseModel

Public response for recurring payouts.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `payouts` | `PublicGroupUniversePayout[]` | No |  |

### PrivateServerUpdatePermissionsRequest

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `clanAllowed` | `boolean` | No |  |
| `enemyClanId` | `integer` | No |  |
| `friendsAllowed` | `boolean` | No |  |
| `usersToAdd` | `integer[]` | No |  |
| `usersToRemove` | `integer[]` | No |  |

### PrivateServerPermissionsResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `clanAllowed` | `boolean` | No |  |
| `enemyClanId` | `integer` | No |  |
| `friendsAllowed` | `boolean` | No |  |
| `users` | `SkinnyUserResponse[]` | No |  |

### Roblox.Web.WebAPI.Models.ApiPageResponse_Roblox.Groups.Api.Models.Response.GroupExperienceResponse_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `previousPageCursor` | `string` | No |  |
| `nextPageCursor` | `string` | No |  |
| `data` | `Roblox.Groups.Api.Models.Response.GroupExperienceResponse[]` | No |  |

### SortOrder

Sort order for groups-api style paginated requests.

Values: `Asc`, `Desc`

### GroupInvitationCursorPageResponse

A page of results using groups-api opaque cursor pagination.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `data` | `GroupInvitation[]` | Yes | The items in this page. |
| `nextPageCursor` | `string` | No | Cursor for the next page, if any. |
| `previousPageCursor` | `string` | No | Cursor for the previous page, if any. |

### CreateGroupInvitationRequestModel

Request for inviting a user to a group.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `recipientUserId` | `integer` | Yes | The user to invite. |
| `roleIds` | `integer[]` | No | Group role ids to grant when the invitation is accepted. |

### GroupInvitation

An invitation to join a group.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `string` | Yes | The invitation id. Stringified because it can exceed the 2^53-1 JSON number limit. |
| `groupId` | `integer` | Yes | The group the invitation is for. |
| `recipientUserId` | `integer` | Yes | The invited user. |
| `senderUserId` | `integer` | Yes | The user who sent the invitation. |
| `status` | `GroupInvitationStatus` | Yes |  |
| `roleIds` | `integer[]` | Yes | Every group role id attached to the invitation. |
| `updatedAt` | `string` | Yes | When the invitation was last updated (UTC). |

### UpdateGroupInvitationRequestModel

Request for accepting or declining a group invitation.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `status` | `GroupInvitationStatus` | Yes |  |

### SuccessResponse

Standard success response model.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `success` | `boolean` | Yes | Whether or not the request was successfully executed. |

### Int64ExclusiveStartKeyCursor

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `key` | `integer` | No |  |
| `sortOrder` | `TransactionRecordsApi.SortOrder` | No |  |
| `pagingDirection` | `CursorPagingDirection` | No |  |
| `pageNumber` | `integer` | No |  |
| `discriminator` | `string` | No |  |
| `count` | `integer` | No |  |

### TransactionType

Values: `Undefined`, `Sale`, `Purchase`, `AffiliateSale`, `DevEx`, `GroupPayout`, `AdImpressionPayout`, `CurrencyPurchase`, `TradeRobux`, `PremiumStipend`, `PendingRobux`, `EngagementPayout`, `GroupEngagementPayout`, `AdSpend`, `Summary`, `IndividualToGroup`, `CSAdjustment`, `AdsRevsharePayout`, `GroupAdsRevsharePayout`, `SubscriptionsRevsharePayout`, `GroupSubscriptionsRevsharePayout`, `SubscriptionsRevshareClawback`, `GroupSubscriptionsRevshareClawback`, `PublishingAdvanceRebates`, `AffiliatePayout`, `LicensingPayment`, `LicensingPaymentClawback`, `CurrencyTransfer`, `RobloxSelectTransfer`, `PrivateServerEngagementPayout`, `CurrencySubscriptionStipend`, `SubscriptionReferralPayout`, `CreatorRewardsPayout`, `Gifts`

### TransactionResponseApiPageResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `previousPageCursor` | `string` | No |  |
| `nextPageCursor` | `string` | No |  |
| `data` | `TransactionResponse[]` | No |  |

### TransactionResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No |  |
| `idHash` | `string` | No |  |
| `created` | `string` | No |  |
| `isPending` | `boolean` | No |  |
| `agent` | `AgentResponse` | No |  |
| `details` | `TransactionDetailsResponse` | No |  |
| `currency` | `GenericCurrencyResponse` | No |  |
| `purchaseToken` | `string` | No |  |

### AgentResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No |  |
| `type` | `AgentType` | No |  |
| `name` | `string` | No |  |

### GenericCurrencyResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `amount` | `integer` | No |  |
| `type` | `CurrencyType` | No |  |

### CurrencyType

Values: `Robux`, `Tickets`

### AgentType

Values: `User`, `Group`

### TransactionRecordsApi.SortOrder

Values: `Asc`, `Desc`

### CursorPagingDirection

Values: `Forward`, `Backward`

### GroupInvitationStatus

Status of a group invitation, serialized as its name.

Values: `Open`, `Accepted`, `Declined`, `Deleted`

### Roblox.Groups.Api.Models.Response.GroupExperienceResponse

A response model representing an experience/game.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No | The game (universe) Id. |
| `name` | `string` | No | The game name. |
| `description` | `string` | No | The game description. |
| `creator` | `Roblox.Web.Responses.RelatedEntityTypeResponse_Roblox.Platform.Core.CreatorType_` | No |  |
| `rootPlace` | `GroupsApi.Roblox.Web.Responses.RelatedEntityTypeResponse_Roblox.Platform.Assets.AssetType_` | No |  |
| `created` | `string` | No | When the game was created. |
| `updated` | `string` | No | When the game was last updated. |
| `placeVisits` | `integer` | No | The number of place visits for this game. |

### Roblox.Web.Responses.RelatedEntityTypeResponse_Roblox.Platform.Core.CreatorType_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No |  |
| `type` | `0 \| 1 \| 2` | No | ['User' = 0, 'Group' = 1, 'Experience' = 2] |
| `name` | `string` | No |  |

### GroupsApi.Roblox.Web.Responses.RelatedEntityTypeResponse_Roblox.Platform.Assets.AssetType_

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No |  |
| `type` | `integer enum (91 values)` | No | ['Image' = 1, 'TShirt' = 2, 'Audio' = 3, 'Mesh' = 4, 'Lua' = 5, 'HTML' = 6, 'Text' = 7, 'Hat' = 8, 'Place' = 9, 'Model' = 10, 'Shirt' = 11, 'Pants' = 12, 'Decal' = 13, 'Avatar' = 16, 'Head' = 17, 'Face' = 18, 'Gear' = 19, 'Badge' = 21, 'GroupEmblem' = 22, 'Animation' = 24, 'Arms' = 25, 'Legs' = 26, 'Torso' = 27, 'RightArm' = 28, 'LeftArm' = 29, 'LeftLeg' = 30, 'RightLeg' = 31, 'Package' = 32, 'YouTubeVideo' = 33, 'GamePass' = 34, 'App' = 35, 'Code' = 37, 'Plugin' = 38, 'SolidModel' = 39, 'MeshPart' = 40, 'HairAccessory' = 41, 'FaceAccessory' = 42, 'NeckAccessory' = 43, 'ShoulderAccessory' = 44, 'FrontAccessory' = 45, 'BackAccessory' = 46, 'WaistAccessory' = 47, 'ClimbAnimation' = 48, 'DeathAnimation' = 49, 'FallAnimation' = 50, 'IdleAnimation' = 51, 'JumpAnimation' = 52, 'RunAnimation' = 53, 'SwimAnimation' = 54, 'WalkAnimation' = 55, 'PoseAnimation' = 56, 'LocalizationTableManifest' = 59, 'LocalizationTableTranslation' = 60, 'EmoteAnimation' = 61, 'Video' = 62, 'TexturePack' = 63, 'TShirtAccessory' = 64, 'ShirtAccessory' = 65, 'PantsAccessory' = 66, 'JacketAccessory' = 67, 'SweaterAccessory' = 68, 'ShortsAccessory' = 69, 'LeftShoeAccessory' = 70, 'RightShoeAccessory' = 71, 'DressSkirtAccessory' = 72, 'FontFamily' = 73, 'FontFace' = 74, 'MeshHiddenSurfaceRemoval' = 75, 'EyebrowAccessory' = 76, 'EyelashAccessory' = 77, 'MoodAnimation' = 78, 'DynamicHead' = 79, 'CodeSnippet' = 80, 'AdsVideo' = 81, 'OtaUpdate' = 82, 'Screenshot' = 83, 'RuntimePropertySet' = 84, 'StorePreviewVideo' = 85, 'GamePreviewVideo' = 86, 'CreatorExperienceConfig' = 87, 'FaceMakeup' = 88, 'LipMakeup' = 89, 'EyeMakeup' = 90, 'VoxelFragment' = 91, 'AvatarBackground' = 92, 'TextDocument' = 93, 'Post' = 94, 'AnimatedImage' = 95, 'ComputeFunction' = 96, 'AvatarSpawnEffect' = 97, 'Voice' = 98] Values: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 16, 17, 18, 19, 21, 22, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98 |
| `name` | `string` | No |  |

### SkinnyUserResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No |  |
| `name` | `string` | No |  |
| `displayName` | `string` | No |  |

### PublicGroupUniversePayout

A recurring payout in the public groups API contract.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `userId` | `integer` | No |  |
| `percentage` | `integer` | No |  |

### Roblox.Api.Develop.Models.UniverseModel

Represents a universe in API endpoint results.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No | The universe Id. |
| `name` | `string` | No | The name of the universe |
| `description` | `string` | No | The description of the universe |
| `isArchived` | `boolean` | No | Is this universe archived |
| `rootPlaceId` | `integer` | No | The universe's root place id |
| `isActive` | `boolean` | No | Is this universe active |
| `privacyType` | `string` | No | The universe's privacy type. |
| `creatorType` | `string` | No | The creator type, either "User" or "Group" |
| `creatorTargetId` | `integer` | No | The id of the user or group that created this universe. |
| `creatorName` | `string` | No | The name of the creator of the universe. |
| `created` | `string` | No | The created System.DateTime |
| `updated` | `string` | No | The updated System.DateTime |
| `audiences` | `0 \| 1 \| 2 \| 3 \| 4[]` | No | The audiences this universe is visible to (e.g. Editors, PlayTesters, Friends, Public). Always non-null; may be empty when audience visibility has not been configured. |

### PublicUserUniversePayout

A payout-visible universe in the public groups API contract.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `universeId` | `integer` | No |  |
| `percentage` | `integer` | No |  |

### OrganizationsServiceApi.ErrorCode

Error code for OrganizationsServiceApi.Models.Response.ErrorResponse.

Values: `InternalError`, `InvalidGroupId`, `InvalidUniverseId`, `InsufficientPermission`, `PermissionNotSupported`, `TooManyRequests`, `FeatureNotEnabled`, `RoleNameReserved`, `RoleNotFound`, `InvitationNotFound`, `UserNotInGroup`, `TooManyRoles`, `FeatureNotSupportedForRole`, `UserInMaxGroups`, `NeedsSecureEndpoint`, `InsufficientGroupPermission`, `TooManyUsers`, `GroupFeatureFrozen`, `GroupMigrated`, `UnificationInProgress`, `InvalidPageLimit`, `InvalidSortOrder`, `InvalidInvitationStatus`, `InvalidRequestBody`

### PublicOneTimePayoutResponseModel

A one-time payout result in the public groups API contract.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `recipientUserId` | `integer` | No |  |
| `status` | `FetchStatus` | No |  |
| `oneTimePayout` | `PublicOneTimePayout` | No |  |

### FetchStatus

Describes whether a fetch operation failed or succeeded.

Values: `Failure`, `Success`

### PublicOneTimePayout

One-time payout details in the public groups API contract.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `amount` | `integer` | No |  |
| `createdAt` | `string` | No |  |

### Roblox.Groups.Api.GroupDetailResponse

A detailed group response model

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No | The group id |
| `name` | `string` | No | The group name |
| `description` | `string` | No | The group description |
| `owner` | `Roblox.Groups.Api.Models.Response.UserModel` | No |  |
| `shout` | `Roblox.Groups.Api.ShoutResponse` | No |  |
| `memberCount` | `integer` | No | The number of members in the group |
| `isBuildersClubOnly` | `boolean` | No | Whether the group is Builders Club only |
| `publicEntryAllowed` | `boolean` | No | Whether the group is public (no approval required) |
| `isLocked` | `boolean` | No | Whether the group is locked |
| `isDeactivated` | `boolean` | No | Whether the group is deactivated |
| `hasVerifiedBadge` | `boolean` | No | Whether the group has a verified badge. |
| `hasSocialModules` | `boolean` | No | Whether the group has social modules enabled (e.g. Forums) (determines if "Followers" vs "Members" should be shown). |
| `communityTier` | `Roblox.Groups.Client.CommunityTierInfoResponse` | No |  |

### Roblox.Groups.Api.Models.Response.UserModel

A model representing data about an Roblox.Platform.Membership.IUser

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `buildersClubMembershipType` | `0 \| 1 \| 2 \| 3 \| 4` | No | The user's builders club membership type |
| `hasVerifiedBadge` | `boolean` | No | The user's verified badge status. |
| `userId` | `integer` | No |  |
| `username` | `string` | No |  |
| `displayName` | `string` | No |  |

### Roblox.Groups.Client.CommunityTierInfoResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `groupId` | `integer` | Yes |  |
| `currentTier` | `integer` | Yes |  |
| `previousTier` | `integer` | No |  |
| `tierUpdatedTime` | `string` | No |  |
| `lastEvaluatedTime` | `string` | No |  |
| `requirements` | `Roblox.Groups.Client.TierRequirement[]` | No |  |
| `capabilities` | `Roblox.Groups.Client.TierCapabilities` | No |  |

### Roblox.Groups.Client.TierRequirement

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `key` | `1 \| 2 \| 3 \| 4 \| 5` | Yes | ['OwnerModerationStatusOk' = 1, 'OwnerAgeEstimationVerified' = 2, 'OwnerIdVerified' = 3, 'OwnerTwoStepVerified' = 4, 'CommunityMeetsPlayerRequirement' = 5] |
| `satisfied` | `boolean` | Yes |  |

### Roblox.Groups.Client.TierCapabilities

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `isEligibleForUnrestrictedMessages` | `boolean` | Yes |  |

### Roblox.Groups.Api.Models.Response.GroupAuditLogResponseItem

A group audit log response model

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `actor` | `Roblox.Groups.Api.UserGroupRoleResponse` | No |  |
| `actionType` | `string` | No | The action type |
| `description` | `any` | No | Information on the action performed |
| `created` | `string` | No | Date the group action was performed |

### Roblox.Groups.Api.UserGroupRoleResponse

A user group role response model

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `user` | `Roblox.Groups.Api.Models.Response.UserModel` | No |  |
| `role` | `Roblox.Groups.Api.GroupRoleResponse` | No |  |

### Roblox.Groups.Api.GroupRoleResponse

A group role response model

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No | The role id |
| `name` | `string` | No | The role name |
| `description` | `string` | No | The role description |
| `rank` | `integer` | No | The role rank |
| `memberCount` | `integer` | No | The number of members in the role. |
| `isBase` | `boolean` | No | Whether or not the role is the base role for the group |
| `color` | `integer enum (17 values)` | No | The role color. ['Invalid' = 0, 'Blue' = 1, 'Green' = 2, 'Purple' = 3, 'Yellow' = 4, 'Orange' = 5, 'Red' = 6, 'Magenta' = 7, 'Teal' = 8, 'Turquoise' = 9, 'Rust' = 10, 'Pistachio' = 11, 'Midnight' = 12, 'Lavender' = 13, 'Pink' = 14, 'Crimson' = 15, 'Plum' = 16] Values: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16 |
| `isPrivate` | `boolean` | No | Whether the role is private (only visible to members with permission). Omitted from the response when false. |

### Roblox.Groups.Api.GroupPolicyResponse

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `canViewGroup` | `boolean` | No |  |
| `groupId` | `integer` | No |  |

### Roblox.Api.Develop.Models.GroupModel

A model containing information about a group

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | `integer` | No | The Roblox.Platform.Groups.IGroup's Id. |
| `name` | `string` | No | The Roblox.Platform.Groups.IGroup's name. |

### GroupRole_RolePermissions

Represents the permissions on a role.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `viewWallPosts` | `boolean` | No | View group wall. |
| `createWallPosts` | `boolean` | No | Post on group wall. |
| `deleteWallPosts` | `boolean` | No | Delete group wall posts. |
| `viewGroupShout` | `boolean` | No | View group shout. |
| `createGroupShout` | `boolean` | No | Post group shout. |
| `changeRank` | `boolean` | No | Manage lower-ranked member ranks. |
| `acceptRequests` | `boolean` | No | Accept join requests. |
| `exileMembers` | `boolean` | No | Kick lower-ranked members. |
| `manageRelationships` | `boolean` | No | Manage allies and enemies. |
| `viewAuditLog` | `boolean` | No | View audit log. |
| `spendGroupFunds` | `boolean` | No | Spend group funds. |
| `advertiseGroup` | `boolean` | No | Advertise group. |
| `createAvatarItems` | `boolean` | No | Create avatar items. |
| `manageAvatarItems` | `boolean` | No | Manage avatar items. |
| `manageGroupUniverses` | `boolean` | No | Manage group universes. |
| `viewUniverseAnalytics` | `boolean` | No | View universe analytics. |
| `createApiKeys` | `boolean` | No | Create group API Keys. |
| `manageApiKeys` | `boolean` | No | Manage all group API keys. |
| `banMembers` | `boolean` | No | Ban lower-ranked members. |
| `viewForums` | `boolean` | No | Can view forums |
| `manageCategories` | `boolean` | No | Can change forum categories |
| `createPosts` | `boolean` | No | Can create forum post |
| `lockPosts` | `boolean` | No | Can lock forum post |
| `pinPosts` | `boolean` | No | Can pin forum post |
| `removePosts` | `boolean` | No | Can remove forum post |
| `createComments` | `boolean` | No | Can create forum comment |
| `removeComments` | `boolean` | No | Can remove forum comment |
| `manageBlockedWords` | `boolean` | No | Can manage blocked words |
| `viewBlockedWords` | `boolean` | No | Can view blocked words |
| `bypassSlowMode` | `boolean` | No | can bypass slow mode |

### GroupJoinRequest

A request to join a group.

The `acceptRequests` permission is required.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `path` | `string` | No | The resource path of the group join request.  Format: `groups/{group_id}/join-requests/{group_join_request_id}` |
| `createTime` | `string` | No | The timestamp when the group join request was created. |
| `user` | `string` | No | The resource path of the user. |

### GroupForumComment

Represents a forum comment on a group's forum post.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `path` | `string` | No | The resource path of the group forum comment.  Format: `groups/{group_id}/forum-categories/{group_forum_category_id}/posts/{group_forum_post_id}/comments/{group_forum_comment_id}` |
| `groupForumCommentId` | `string` | No | The id of the group forum comment. |
| `message` | `ContentMessage` | No | The message content of the group forum comment. |

### ContentMessage

Represents the content of a message.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `createTime` | `string` | No | The timestamp when the message was created. |
| `updateTime` | `string` | No | The timestamp when the message was last updated. |
| `plainText` | `string` | No | The plain text content of the message. |
| `author` | `string` | No | The resource path of the user who created the message. |
| `messageReaction` | `MessageReaction[]` | No | The reactions to the message, if this feature is enabled for this message. |

### MessageReaction

Represents the reaction to a message.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `emoteId` | `string` | No | The id of the emote. |
| `count` | `integer` | No | The count of reactions for this emote. |

### GroupForumPost

Represents a forum post within a group's forum category.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `path` | `string` | No | The resource path of the group forum post.  Format: `groups/{group_id}/forum-categories/{group_forum_category_id}/posts/{group_forum_post_id}` |
| `createTime` | `string` | No | The timestamp when the group forum post was created. |
| `updateTime` | `string` | No | The timestamp when the group forum post was last updated. |
| `pinned` | `boolean` | No | Whether the group forum post is pinned. |
| `locked` | `boolean` | No | Whether the group forum post is locked. |
| `groupForumPostId` | `string` | No | The id of the group forum post. |
| `title` | `string` | No | The title of the group forum post. |
| `firstComment` | `GroupForumComment` | No | The resource path of the group forum post's first comment, which holds the post content.  By default, the `first_comment` field is fully populated. This **will not** dereference resource references within the first comment, such as `GroupForumComment.author`; only the `path` subfield of these fields will be populated. However, if only the `path` field of the first comment is needed, you can specify the FULL view. |
| `author` | `string` | No | The resource path of the user who created the group forum post. |
| `archiveTime` | `string` | No | The timestamp when the group forum post was archived. |
| `archiver` | `string` | No | The resource path of the user who archived the group forum post. |
| `commentCount` | `integer` | No | The number of comments on the group forum post. This includes the first comment (post content). |

### GroupForumCategory

Represents a forum category within a group for user discussions.

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `path` | `string` | No | The resource path of the group forum category.  Format: `groups/{group_id}/forum-categories/{group_forum_category_id}` |
| `createTime` | `string` | No | The timestamp when the group forum category was created. |
| `updateTime` | `string` | No | The timestamp when the group forum category was last updated. |
| `groupForumCategoryId` | `string` | No | The id of the group forum category. |
| `displayName` | `string` | No | The display name of the group forum category. |
| `creator` | `string` | No | The resource path of the user who created the group forum category. |
| `archiveTime` | `string` | No | The timestamp when the group forum category was archived. |
| `archiver` | `string` | No | The resource path of the user who archived the group forum category. |