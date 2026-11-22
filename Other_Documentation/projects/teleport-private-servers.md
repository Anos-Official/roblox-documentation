<!-- Source: https://create.roblox.com/docs/projects/teleport-private-servers -->

Teleport to private servers | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/projects/teleport-private-servers.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Players](/docs/players)

# Teleport to private servers

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/projects/teleport-private-servers.md)

In addition to teleporting players between public servers, [TeleportService](/docs/reference/engine/classes/TeleportService)  supports teleporting to private servers , which are servers restricted to specific players. There are two kinds of private servers you can teleport to:

-

Reserved servers : Developer-created servers accessed via a developer-supplied ID. Useful for private matches, co-op sessions, or any scenario where you control who joins.

-

VIP servers : Player-purchased private servers. Use [TeleportOptions.VipServerId](/docs/reference/engine/classes/TeleportOptions#VipServerId)  to route players to a VIP server they've purchased.

Both [ReservedServerId](/docs/reference/engine/classes/TeleportOptions#ReservedServerId)  and [VipServerId](/docs/reference/engine/classes/TeleportOptions#VipServerId)  are properties of the [TeleportOptions](/docs/reference/engine/classes/TeleportOptions)  class. You can only set one private-server routing field at a time. See [Teleport between places](/docs/projects/teleport)  for an overview of all teleport options.

## [Teleport to a reserved server](#teleport-to-a-reserved-server)[](#teleport-to-a-reserved-server)

Reserved servers are created on demand: the first teleport using a new ReservedServerId  creates the server, and reusing the same ID routes subsequent teleports to that same server. Generate the ID with [HttpService:GenerateGUID(false)](/docs/reference/engine/classes/HttpService#GenerateGUID) :

```

local HttpService = game:GetService("HttpService")

local TeleportService = game:GetService("TeleportService")

local Players = game:GetService("Players")

local TARGET_PLACE_ID = 12345678901234

-- The users to teleport (e.g. from Players:GetPlayers() or a matchmaking group)

local player1, player2 = Players:GetPlayers()[1], Players:GetPlayers()[2]

-- Generate a unique ID for the reserved server

local reservedServerId = HttpService:GenerateGUID(false)

local teleportOptions = Instance.new("TeleportOptions")

teleportOptions.ReservedServerId = reservedServerId

-- First teleport creates the server

TeleportService:TeleportAsync(TARGET_PLACE_ID, {player1, player2}, teleportOptions)

```

### [Reuse a reserved server ID](#reuse-a-reserved-server-id)[](#reuse-a-reserved-server-id)

To let other players join the same reserved server later, persist the reserved server ID with a [DataStoreService](/docs/reference/engine/classes/DataStoreService)  data store so it survives across sessions and servers.

On the server that creates the reserved server, generate the ID for the first teleport, then save it keyed by whatever identifies the session (for example a lobby ID or party ID):

```

local DataStoreService = game:GetService("DataStoreService")

local HttpService = game:GetService("HttpService")

local TeleportService = game:GetService("TeleportService")

local reservedServersStore = DataStoreService:GetDataStore("ReservedServers")

-- Key that identifies the shared session across servers

local sessionKey = "lobby-123"

-- A new ID creates the reserved server on arrival at the destination

local reservedServerId = HttpService:GenerateGUID(false)

reservedServersStore:SetAsync(sessionKey, reservedServerId)

local teleportOptions = Instance.new("TeleportOptions")

teleportOptions.ReservedServerId = reservedServerId

TeleportService:TeleportAsync(TARGET_PLACE_ID, { player }, teleportOptions)

```

On any other server that needs to send players to that same reserved server, look the ID up by the same session key and set it as the [TeleportOptions.ReservedServerId](/docs/reference/engine/classes/TeleportOptions#ReservedServerId)  of the teleport:

```

local DataStoreService = game:GetService("DataStoreService")

local TeleportService = game:GetService("TeleportService")

local reservedServersStore = DataStoreService:GetDataStore("ReservedServers")

local sessionKey = "lobby-123"

local existingId = reservedServersStore:GetAsync(sessionKey)

if existingId then

	local teleportOptions = Instance.new("TeleportOptions")

	teleportOptions.ReservedServerId = existingId

	TeleportService:TeleportAsync(TARGET_PLACE_ID, { player }, teleportOptions)

end

```

On a VIP server, to make the VIP server ID available on the destination server without a data store, attach it to each player with [TeleportOptions:SetTeleportData()](/docs/reference/engine/classes/TeleportOptions#SetTeleportData) :

```

local teleportOptions = Instance.new("TeleportOptions")

teleportOptions.VipServerId = game.PrivateServerId

teleportOptions:SetTeleportData({ vipServerId = game.PrivateServerId })

TeleportService:TeleportAsync(TARGET_PLACE_ID, {player}, teleportOptions)

```

On arrival, read it back from the player's join data. For more information, see [Send user data along with teleports](/docs/projects/teleport#send-user-data-along-with-teleports) .

### [Identify a reserved server on arrival](#identify-a-reserved-server-on-arrival)[](#identify-a-reserved-server-on-arrival)

On the destination server, check whether the current server is a reserved server:

```

local isReserved = game.PrivateServerId ~= "" and game.PrivateServerOwnerId == 0

```

[DataModel.PrivateServerId](/docs/reference/engine/classes/DataModel#PrivateServerId)  matches the ReservedServerId  you supplied and remains constant across all server instances for that reserved server. [DataModel.JobId](/docs/reference/engine/classes/DataModel#JobId)  is unique per running instance and changes when the server restarts.

## [Teleport to a VIP server](#teleport-to-a-vip-server)[](#teleport-to-a-vip-server)

VIP servers are private servers that players can purchase from the game's page. To teleport a player to a VIP server, set [TeleportOptions.VipServerId](/docs/reference/engine/classes/TeleportOptions#VipServerId)  to the [DataModel.PrivateServerId](/docs/reference/engine/classes/DataModel#PrivateServerId)  of the target VIP server.

```

local TeleportService = game:GetService("TeleportService")

local TARGET_PLACE_ID = 12345678901234

-- The PrivateServerId of the destination VIP server, for example carried

-- in the player's teleport data or read from a data store

local vipServerId = player:GetJoinData().TeleportData.vipServerId

local teleportOptions = Instance.new("TeleportOptions")

teleportOptions.VipServerId = vipServerId

TeleportService:TeleportAsync(TARGET_PLACE_ID, {player}, teleportOptions)

```

[TeleportOptions.VipServerId](/docs/reference/engine/classes/TeleportOptions#VipServerId)  is distinct from [TeleportOptions.ReservedServerId](/docs/reference/engine/classes/TeleportOptions#ReservedServerId) . Use ReservedServerId  for developer-created reserved servers and VipServerId  for player-purchased VIP servers.

A VIP server ID is scoped to the experience that owns the VIP server: you can use it with the place ID of any place in that experience, but not with a place ID from another experience.

When you leave a routing field unset, the engine chooses the destination server. A teleport with no private-server routing fields set can land on a public server or, if the player recently joined a VIP server of that experience, on that VIP server.

A common use case for this pattern is returning a player from a reserved server back to the VIP server of the experience's root place. Since a reserved server's game.PrivateServerId  is its own reserved ID rather than the origin VIP server's, carry the VIP server's ID into the reserved server, for example by passing it in teleportData  on the outbound teleport or persisting it in a data store as shown in [Reuse a reserved server ID](#reuse-a-reserved-server-id) , then set it as the [TeleportOptions.VipServerId](/docs/reference/engine/classes/TeleportOptions#VipServerId)  of the return teleport.

Set the same [TeleportOptions.VipServerId](/docs/reference/engine/classes/TeleportOptions#VipServerId)  on every teleport to keep players in the same VIP server across places throughout gameplay.

### [VIP server access checks](#vip-server-access-checks)[](#vip-server-access-checks)

A player can join a VIP server if the server's Friends Allowed  setting, its allowlist, or a link code grants them access at the moment of the teleport. VIP server owners can change these settings at any time, so a player who had access earlier might lose it.

If a player isn't allowed to join, [TeleportService.TeleportInitFailed](/docs/reference/engine/classes/TeleportService#TeleportInitFailed)  fires and the player sees an error saying the server is restricted. To teleport a group to a VIP server, pass multiple players with the same [TeleportOptions.VipServerId](/docs/reference/engine/classes/TeleportOptions#VipServerId) . The engine checks each player independently at connect time, so players without access fail individually while the rest teleport normally. Always handle [TeleportService.TeleportInitFailed](/docs/reference/engine/classes/TeleportService#TeleportInitFailed)  for VIP teleports, since players might also have closed the VIP server or switched to a different one.

## [Store and share server IDs](#store-and-share-server-ids)[](#store-and-share-server-ids)

The [TeleportAsyncResult](/docs/reference/engine/classes/TeleportAsyncResult)  object returned by [TeleportService:TeleportAsync()](/docs/reference/engine/classes/TeleportService#TeleportAsync)  contains information about the destination:

-

[TeleportAsyncResult.PrivateServerId](/docs/reference/engine/classes/TeleportAsyncResult#PrivateServerId)  - The private server ID of the destination server. Matches [DataModel.PrivateServerId](/docs/reference/engine/classes/DataModel#PrivateServerId)  on the destination.

-

[TeleportAsyncResult.ReservedServerAccessCode](/docs/reference/engine/classes/TeleportAsyncResult#ReservedServerAccessCode)  - Only populated for legacy access-code teleports. Not populated when using ReservedServerId  or VipServerId .

```

local result = TeleportService:TeleportAsync(TARGET_PLACE_ID, {player}, teleportOptions)

if result then

    print("Destination PrivateServerId:", result.PrivateServerId)

end

```

## [Migrate from legacy access codes](#migrate-from-legacy-access-codes)[](#migrate-from-legacy-access-codes)

If your game uses the deprecated [TeleportOptions.ReservedServerAccessCode](/docs/reference/engine/classes/TeleportOptions#ReservedServerAccessCode)  or [TeleportOptions.ShouldReserveServer](/docs/reference/engine/classes/TeleportOptions#ShouldReserveServer) , migrate to ReservedServerId  by replacing the access-code flow with a GUID-based flow:

1.

Replace  ReserveServerAsync()  and ReservedServerAccessCode  with [HttpService:GenerateGUID(false)](/docs/reference/engine/classes/HttpService#GenerateGUID)  and ReservedServerId .

2.

Store  the generated GUID so you can reuse it for subsequent teleports to the same server.

3.

Update  all TeleportOptions  usages to set ReservedServerId  instead of ReservedServerAccessCode  or ShouldReserveServer .

### [Before (deprecated)](#before-deprecated)[](#before-deprecated)

```

-- Deprecated: ReserveServerAsync + ReservedServerAccessCode

local accessCode, privateServerId = TeleportService:ReserveServerAsync(TARGET_PLACE_ID)

local teleportOptions = Instance.new("TeleportOptions")

teleportOptions.ReservedServerAccessCode = accessCode

TeleportService:TeleportAsync(TARGET_PLACE_ID, {player}, teleportOptions)

```

### [After (current)](#after-current)[](#after-current)

```

local HttpService = game:GetService("HttpService")

local TeleportService = game:GetService("TeleportService")

-- Current: GenerateGUID + ReservedServerId

local reservedServerId = HttpService:GenerateGUID(false)

local teleportOptions = Instance.new("TeleportOptions")

teleportOptions.ReservedServerId = reservedServerId

TeleportService:TeleportAsync(TARGET_PLACE_ID, {player}, teleportOptions)

```

The legacy ReserveServerAsync()  and ReservedServerAccessCode  remain available for backward compatibility, but are not recommended for new work. ReserveServerAsync()  does not actually reserve a server in advance, but simply generates a random GUID. Existing reserved servers created with access codes continue to function.

## [Handle failed teleports](#handle-failed-teleports)[](#handle-failed-teleports)

Teleports to private servers can fail like any network call. Wrap them in pcall  and retry as needed. When a teleport is initiated but fails at the last moment, [TeleportService.TeleportInitFailed](/docs/reference/engine/classes/TeleportService#TeleportInitFailed)  fires with the original [TeleportOptions](/docs/reference/engine/classes/TeleportOptions)  so you can retry with the same destination.

For a full retry implementation, see [Handle failed teleports](/docs/projects/teleport#handle-failed-teleports)  in the main teleport guide.

When the engine itself routes a plain teleport to a VIP server, VIP-specific join failures such as a full or flooded server fall back to a public join instead of firing [TeleportService.TeleportInitFailed](/docs/reference/engine/classes/TeleportService#TeleportInitFailed) . Only teleports with an explicit [TeleportOptions.VipServerId](/docs/reference/engine/classes/TeleportOptions#VipServerId)  surface these failures to your retry handler.

## [Best practices](#best-practices)[](#best-practices)

-

Generate IDs on the server.  Always call [HttpService:GenerateGUID(false)](/docs/reference/engine/classes/HttpService#GenerateGUID)  from a server [Script](/docs/reference/engine/classes/Script)  to prevent clients from predicting or controlling reserved server IDs.

-

Persist reserved server IDs.  Store the GUID in a data store if players need to rejoin the same reserved server across sessions.

-

Use the right field.  Use ReservedServerId  for developer-created reserved servers, VipServerId  for player-purchased VIP servers. Never set both on the same [TeleportOptions](/docs/reference/engine/classes/TeleportOptions)  instance.

-

Don't mix routing fields.  You can only set one of ReservedServerId , VipServerId , or ServerInstanceId  at a time. Setting more than one causes an error.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
