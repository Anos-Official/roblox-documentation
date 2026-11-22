<!-- Source: https://create.roblox.com/docs/studio/mcp-open-cloud -->

Use Open Cloud with the Studio MCP server | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/studio/mcp-open-cloud.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Studio](/docs/en-us/studio)
4. /
5. [MCP server](/docs/studio/mcp)

# Use Open Cloud with the Studio MCP server

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/studio/mcp-open-cloud.md)

The [Studio MCP server](/docs/studio/mcp)  can call [Open Cloud](/docs/cloud)  APIs on your behalf. Your MCP client can upload assets, manage developer products and game passes, change game settings, and more without creating or pasting an [API key](/docs/cloud/auth/api-keys) .

You decide what your client is allowed to do. Permissions are saved to your Roblox account for each game, and Studio enforces them on every request.

## [Prerequisites](#prerequisites)[](#prerequisites)

Before you use Open Cloud with the Studio MCP server:

-

Enable the Studio MCP server and connect your client. For more information, see [Connect to the Roblox Studio MCP server](/docs/studio/mcp) .

-

Open a place that belongs to a published game. Permissions are saved per game, so unpublished local places can't use them.

-

Have permission to manage the game. If a group owns the game, your group role must allow the actions you grant to the client.

## [How it works](#how-it-works)[](#how-it-works)

The Studio MCP server adds the open_cloud_invoke  tool. Studio manages access for you. Your client can only use the scopes you've enabled for the current game, and it never sees or handles credentials. Only you can change your permissions. Your client can't enable them on its own.

For each game, you control which Open Cloud scopes your client can call, which folders it can upload from, whether data store and memory store calls work from execute_luau , and whether scripts can make HTTP requests and to which domains.

| Parameter | | Description |
| --- | --- |
| method | | GET , POST , PUT , PATCH , or DELETE . |
| endpoint | | The path under https://apis.roblox.com , including any query string. For example, /cloud/v2/universes/123 . |
| body | | A JSON-encoded request body. Omit for GET  and DELETE . |
| scopes | | The scopes the endpoint requires, such as ["universe:read"] . Optional, but returns a clear error if a required scope isn't enabled. |
| files | | Local files for multipart/form-data  endpoints, such as asset uploads. Files must be in an approved [upload folder](#upload-folders) . |

Permissions are per person. If you work on a game with collaborators, each collaborator sets their own permissions. Enabling a permission for yourself doesn't enable it for anyone else.

These permissions apply to external MCP clients only. They don't change what Assistant can do inside Studio.

## [Manage permissions](#manage-permissions)[](#manage-permissions)

To manage permissions for the game you have open, click MCP  in the bottom-right corner of Studio, then select the MCP Permissions  tab. Or, from Assistant:

1.

Open Assistant .

2.

Click …  ⟩ Settings .

3.

Select the MCP Permissions  tab.

4.

Enable or disable permissions. Changes apply to your client's next request.

### [Access levels](#access-levels)[](#access-levels)

Pick an access level as a starting point, then enable or disable individual permissions. Each game starts at Balanced .

| Access level | | What it turns on |
| Safe | | Low-risk scopes only. Most permissions are off. |
| Balanced | | Low- and moderate-risk scopes. |
| Full access | | All scopes, including high-risk ones that can cost Robux, affect your players, or publish to your live game. |
| Custom | | Shown when you change any permission after picking a level. |

Roblox sets the risk level for each scope.

### [Permission sections](#permission-sections)[](#permission-sections)

Permissions are grouped by what they let your client do. Each section maps to one or more Open Cloud [scopes](/docs/cloud/reference/scopes)  or script capabilities. For details on each scope, see the [Open Cloud scopes](/docs/cloud/reference/scopes)  reference.

| Section | | What it allows | | Scopes |
| Look at your game | | Read game and place settings, version history, analytics, and instances. | | universe:read , universe.place:read , universe.analytics:read , universe.place.instance:read |
| Edit your game | | Change game and place settings, publish, restart servers, and edit instances remotely. | | universe:write , universe.place:write , universe.place.instance:write |
| Players & social | | Read profiles and inventories, send notifications, manage groups and forums, manage events, and read saved Creator Store items. | | user.* , group:* , group-forum:read , universe.event:* , creator-store-save:* |
| Save & load data | | Use [DataStoreService](/docs/reference/engine/classes/DataStoreService)  and [MemoryStoreService](/docs/reference/engine/classes/MemoryStoreService)  from execute_luau . | | universe-datastores.* , universe.ordered-data-store.* , memory-store.* |
| Connect to the internet | | Make HTTP requests from Luau to domains you allow, and publish cross-server messages. | | Network  capability, universe-messaging-service:publish |
| Publish & manage assets | | Upload assets and check their status, share assets, manage Creator Store listings, publish place versions, and manage thumbnails. | | asset:* , asset-permissions:write , creator-store-product:* , universe-places:write , universe.thumbnail:* |
| Money & monetization | | Create and edit developer products, game passes, and ad campaigns, and read subscriptions. | | developer-product:* , game-pass:* , ad.campaign:* , ad.billing:read , universe.subscription-product.subscription:read |
| Player consequences | | Read, create, and remove bans. | | universe.user-restriction:* |
| Security & credentials | | Read secret names and create secrets, and run Luau in the cloud. | | universe.secret:* , universe.place.luau-execution-session:* |

Some permissions can cost Robux, affect your players, or publish changes to your live game. These include Money & monetization , Player consequences , Security & credentials , universe:write , and universe-places:write . Enable them only for tasks that require them, and disable them when you finish.

### [Upload folders](#upload-folders)[](#upload-folders)

Your client can only upload files from folders you approve. Add a folder before asking your client to upload assets, and keep exports there.

The client can't copy or move files into an approved folder to bypass this restriction. If a file is elsewhere, move it yourself or approve its folder.

### [Data stores and memory stores](#data-stores-and-memory-stores)[](#data-stores-and-memory-stores)

Your client accesses data stores and memory stores through [DataStoreService](/docs/reference/engine/classes/DataStoreService)  and [MemoryStoreService](/docs/reference/engine/classes/MemoryStoreService)  in execute_luau , not through Open Cloud. To use them:

1.

Enable the scopes you need under Save & load data . Reads require universe-datastores.objects:read . Writes require universe-datastores.objects:update .

2.

In Game Settings  ⟩ Security , enable Enable Studio Access to API Services . This game setting is separate from your MCP permissions.

Studio uses your live data stores. Writes from your client change real player data. Consider testing against a separate game first.

### [HTTP requests](#http-requests)[](#http-requests)

To let scripts your client runs make HTTP requests with [HttpService](/docs/reference/engine/classes/HttpService) :

1.

Enable Connect to the internet . This grants the Network  [script capability](/docs/scripting/capabilities) .

2.

Add each domain your client needs to the HTTP domain allow list .

Studio denies requests to any domain that isn't on the list.

### [Unavailable permissions](#unavailable-permissions)[](#unavailable-permissions)

Some scopes can't be granted to an MCP client. These include badge scopes, universe-datastores.control:* , universe-datastores.objects:create , analytics alerts, and all legacy-*  scopes. Use the [Creator Dashboard](https://create.roblox.com/dashboard/creations)  or an [API key](/docs/cloud/auth/api-keys)  for these tasks.

Some endpoints also reject the token Studio uses, even when the matching scope is enabled. If that happens, your client reports the error and suggests another way to complete the task.

## [Import a 3D model](#import-a-3d-model)[](#import-a-3d-model)

Importing assets from Blender, Maya, or another 3D tool is a common workflow. Your client exports the model, uploads it, inserts it, then compares the result against the source and fixes what the import changed.

To import a model:

1.

Enable Publish & manage assets  ⟩ asset:read  and asset:write .

2.

Approve the folder your exports go into.

3.

Open the model in your 3D tool, or export it as .glb  or .fbx  into the approved folder.

4.

Prompt your client. For example:

Import the castle from my open Blender file into Studio, next to the spawn point.

The import skill tells your client to confirm before uploading. It then:

-

Checks each mesh against the triangle limit, and asks whether to split or simplify any that exceed it.

-

Uploads the model and waits for moderation.

-

Inserts the model and fixes scale, rotation, missing textures, colors, and anchoring.

-

Places the model on the ground, clear of other objects and spawn points.

Uploads create permanent assets owned by the game's owner. If a group owns the game, uploads go to the group. Open Cloud can't archive or delete them. To remove an asset, use the [Creator Dashboard](https://create.roblox.com/dashboard/creations) . You're responsible for what's uploaded to your account, including uploads your client makes for you.

For supported asset types, formats, and size limits, see [Usage guide for assets](/docs/cloud/guides/usage-assets#supported-asset-types-and-limits) .

## [Skills](#skills)[](#skills)

The following skills teach your client how to use these permissions. Clients connected through MCP get them automatically and load them with the skill  tool. To view them, open Assistant , click …  ⟩ Assistant Settings , then select Skills . To adapt one to your workflow, select it and click Duplicate , then edit your copy. Your copy replaces the original, but doesn't receive future updates.

| Skill | | Description |
| rbx-open-cloud-usage | | Calls Open Cloud with open_cloud_invoke , selects the correct endpoint, and handles errors. |
| rbx-permissions | | Determines which permissions a task needs, checks which are enabled, and asks you for only the missing ones. |
| rbx-import-asset | | Imports a model from an external 3D tool, then checks and fixes it in Studio. |

## [Troubleshooting](#troubleshooting)[](#troubleshooting)

When a request is blocked, the client reports what's missing. It never bypasses a permission you've disabled.

| Error | | Cause | | Fix |
| Scope '<scope>' has not been granted | | The scope is disabled, or the name is misspelled. | | Enable the scope in the matching section. |
| HTTP 403  or 401 , with the scope enabled | | The endpoint doesn't accept the MCP token. | | Use the Creator Dashboard or an API key for this task. |
| lacking capability <capability> | | A script needs a capability that isn't granted. | | Enable Connect to the internet  for Network . Other capabilities can't be granted. |
| domain <domain> is not in the Assistant HTTP allowlist | | The domain isn't on your allow list. | | Add it under Connect to the internet  ⟩ HTTP domain allow list . |
| 502 … Access forbidden  from a data store call | | The matching Save & load data  scope is disabled. | | Enable the read or update scope. |
| Studio access to APIs is not allowed | | Studio API access is disabled for this game. | | Enable Game Settings  ⟩ Security  ⟩ Enable Studio Access to API Services . |
| InternalError  from a memory store call | | The memory-store.*  scopes are disabled. | | Enable the memory store scopes under Save & load data . |
| File not in an approved upload directory | | The file is outside your approved folders. | | Approve the folder, or move the file into one. |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
