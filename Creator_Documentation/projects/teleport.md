<!-- Source: https://create.roblox.com/docs/en-us/projects/teleport -->

Teleport between places | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/projects/teleport.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Players](/docs/en-us/players)

# Teleport between places

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/projects/teleport.md)

Many games are subdivided into multiple [places](/docs/en-us/production/publishing/publish-games-and-places#create-additional-places) , such as a fantasy world with towns, castles, dungeons, and a vast forest. Use [TeleportService](/docs/en-us/reference/engine/classes/TeleportService)  to teleport users between places, to different servers, or even to other games.

## [Teleport players](#teleport-players)[](#teleport-players)

To teleport players, use [TeleportService:TeleportAsync()](/docs/en-us/reference/engine/classes/TeleportService#TeleportAsync) . This method accepts three parameters:

-

The [PlaceId](/docs/en-us/reference/engine/classes/DataModel#PlaceId)  for users to teleport to.

-

An array containing the [Player](/docs/en-us/reference/engine/classes/Player)  instances you want to teleport.

-

An optional [TeleportOptions](/docs/en-us/reference/engine/classes/TeleportOptions)  instance that contains custom properties for the [TeleportAsync()](/docs/en-us/reference/engine/classes/TeleportService#TeleportAsync)  call.

```

local Players = game:GetService("Players")

local TeleportService = game:GetService("TeleportService")

local TARGET_PLACE_ID = 12345678901234 -- replace with your own

local playerToTeleport = Players:GetPlayers()[1] -- get the first user in the game

TeleportService:TeleportAsync(TARGET_PLACE_ID, {playerToTeleport})

```

To get the appropriate players to teleport, you might use a [BasePart.Touched](/docs/en-us/reference/engine/classes/BasePart#Touched)  or a [ProximityPrompt.Triggered](/docs/en-us/reference/engine/classes/ProximityPrompt#Triggered)  event to get an individual [Player](/docs/en-us/reference/engine/classes/Player) . Then you can check if the player is part of a team ([Player.Team](/docs/en-us/reference/engine/classes/Player#Team) ) or party ([Player.PartyId](/docs/en-us/reference/engine/classes/Player#PartyId) ). Finally, you can use [Team:GetPlayers()](/docs/en-us/reference/engine/classes/Team#GetPlayers)  or [SocialService:GetPlayersByPartyId()](/docs/en-us/reference/engine/classes/SocialService#GetPlayersByPartyId)  if you want to teleport the entire group rather than just the individual.

To reduce client-side exploits, you can only call [TeleportAsync()](/docs/en-us/reference/engine/classes/TeleportService#TeleportAsync)  from server scripts. The client-side [Teleport()](/docs/en-us/reference/engine/classes/TeleportService#Teleport)  method is deprecated and should not be used for new work, even if your place is configured as "Fully Open." For more information, see [Configure secure teleportation](#configure-secure-teleportation) .

## [Configure secure teleportation](#configure-secure-teleportation)[](#configure-secure-teleportation)

Three settings handle teleport security.

| Setting | | Description |
| --- | --- |
| (Creator Dashboard) Audience  > Access Settings  > Access Control for Places | | Controls whether players can join any place in your game or must first join the [start place](/docs/en-us/production/publishing/publish-games-and-places#create-games) . |
| (Creator Dashboard) Place  > Access  > Direct Access Control | | Overrides your game-level Access Control for Places  setting for a non-start place. |
| (Studio) File  > Experience Settings  > Security  > Allow Third Party Teleports | | Controls teleports from your game to games that you don't own . You can leave this setting disabled and still teleport players between published games you own. |

Access Control for Places  controls players teleporting into  your game and is the most critical setting for preventing teleport-based exploits.

![Access control for places on the Creator Hub](https://prod.docsiteassets.roblox.com/assets/players/teleport-access-control.png)

-

If you choose Fully open , players can join any place in your game through teleports from any game, including deep links, game invites, joining a friend, and more.

This is a good choice if your game has several places and you want friends to be able to easily join each other no matter which place they're in. If you don't choose this option, players who try to join their friends in non-start places will instead join your game's start place.

-

If you choose Limited to same universe , players can only join non-start places through teleports within your games. This setting allows both client- and server-initiated teleports.

This is a good choice if you have a legacy game that you don't want to [migrate to secure teleports](#migrate-to-secure-teleports) .

-

If you choose Secure within universe only , players can only join non-start places through server-initiated teleports within this game.

This is a good choice if your game has a strict progression system before players can access certain areas. It's also a good choice if your game has a test place that players shouldn't have access to or for places that exclusively use reserved servers.

Ultimately, your Access Control for Places  setting depends on the type of game you want to build. Many games don't need secure teleports.

### [Migrate to secure teleports](#migrate-to-secure-teleports)[](#migrate-to-secure-teleports)

If you have an existing game that uses client-side teleports and want to require server-initiated teleports, the goal is to move all teleport logic out of client scripts and into server scripts:

1.

Find all client scripts that call [Teleport()](/docs/en-us/reference/engine/classes/TeleportService#Teleport) .

2.

Change these calls to instead fire [remote events](/docs/en-us/scripting/events/remote) . Alternatively, you can change the calls to instead use [ProximityPrompts](/docs/en-us/reference/engine/classes/ProximityPrompt) , [ClickDetectors](/docs/en-us/reference/engine/classes/ClickDetector) , or even just the [BasePart.Touched](/docs/en-us/reference/engine/classes/BasePart#Touched)  event.

3.

Reimplement the teleport in a server script using [TeleportAsync()](/docs/en-us/reference/engine/classes/TeleportService#TeleportAsync) .

4.

When no more [Teleport()](/docs/en-us/reference/engine/classes/TeleportService#Teleport)  calls exist, change Access Control for Places  to Secure .

## [Create custom teleport screens](#create-custom-teleport-screens)[](#create-custom-teleport-screens)

When a user triggers a teleport, they see the standard Roblox loading screen as they wait for the new place to load. If desired, you can add a custom teleport screen by calling [TeleportService:SetTeleportGui()](/docs/en-us/reference/engine/classes/TeleportService#SetTeleportGui)  on the client.

The following example sets a customized [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  from [ReplicatedStorage](/docs/en-us/reference/engine/classes/ReplicatedStorage) . Any scripts within the [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  do not  run.

```

local TeleportService = game:GetService("TeleportService")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local teleportGui = ReplicatedStorage.TeleportGui

TeleportService:SetTeleportGui(teleportGui)

```

## [Customize teleport options](#customize-teleport-options)[](#customize-teleport-options)

You can customize teleportations, such as [teleporting users to a specific server](#teleport-to-specific-servers)  and [sending user data along with teleports](#send-user-data-along-with-teleports) , by setting the [TeleportOptions](/docs/en-us/reference/engine/classes/TeleportOptions)  instance and passing it to the [TeleportService:TeleportAsync()](/docs/en-us/reference/engine/classes/TeleportService#TeleportAsync)  method.

### [Teleport to specific servers](#teleport-to-specific-servers)[](#teleport-to-specific-servers)

To teleport users to specific servers, set the target server using [TeleportOptions](/docs/en-us/reference/engine/classes/TeleportOptions)  and pass it to the [TeleportAsync()](/docs/en-us/reference/engine/classes/TeleportService#TeleportAsync)  method. If you don't specify a server, users are teleported into a public server; the information of the first user in the list is used for matchmaking.

To teleport users to a specific public server, set the [TeleportOptions.ServerInstanceId](/docs/en-us/reference/engine/classes/TeleportOptions#ServerInstanceId)  property as a valid instance ID, which is a unique identifier for a public server.

```

local teleportOptions = Instance.new("TeleportOptions")

teleportOptions.ServerInstanceId = targetServerId

```

To teleport users to a reserved server , generate a GUID with [HttpService:GenerateGUID(false)](/docs/en-us/reference/engine/classes/HttpService#GenerateGUID)  and set [TeleportOptions.ReservedServerId](/docs/en-us/reference/engine/classes/TeleportOptions#ReservedServerId) . The first teleport using a new ID creates the server; reusing the same ID routes subsequent teleports to that server.

```

local HttpService = game:GetService("HttpService")

local TeleportService = game:GetService("TeleportService")

local TARGET_PLACE_ID = 12345678901234

local reservedServerId = HttpService:GenerateGUID(false)

local teleportOptions = Instance.new("TeleportOptions")

teleportOptions.ReservedServerId = reservedServerId

TeleportService:TeleportAsync(TARGET_PLACE_ID, {player}, teleportOptions)

```

To teleport users to a VIP (private) server , set [TeleportOptions.VipServerId](/docs/en-us/reference/engine/classes/TeleportOptions#VipServerId)  to the [DataModel.PrivateServerId](/docs/en-us/reference/engine/classes/DataModel#PrivateServerId)  of the target VIP server:

```

-- The PrivateServerId of the destination VIP server, for example carried

-- in the player's teleport data or read from a data store

local vipServerId = player:GetJoinData().TeleportData.vipServerId

local teleportOptions = Instance.new("TeleportOptions")

teleportOptions.VipServerId = vipServerId

```

When teleporting users to another place within the same experience, set [TeleportOptions.VipServerId](/docs/en-us/reference/engine/classes/TeleportOptions#VipServerId)  to game.PrivateServerId  if you want them to stay in that same VIP server:

```

local teleportOptions = Instance.new("TeleportOptions")

teleportOptions.VipServerId = game.PrivateServerId

```

For more information on reserved and VIP server teleport patterns, including reusing server IDs and migrating from legacy access codes, see [Teleport to private servers](/docs/en-us/projects/teleport-private-servers) .

### [Send user data along with teleports](#send-user-data-along-with-teleports)[](#send-user-data-along-with-teleports)

Teleporting a user between places discards any local data associated with that user. You can use the following approaches to handle data persistence between places:

-

If your game utilizes secure  user data like in-game currency or inventory, implement [data stores](/docs/en-us/../cloud-services/data-stores)  or [memory stores](/docs/en-us/cloud-services/memory-stores)  to maintain data from place to place.

-

To send basic non-secure  data from place to place, call [TeleportOptions:SetTeleportData()](/docs/en-us/reference/engine/classes/TeleportOptions#SetTeleportData)  before passing it to [TeleportAsync()](/docs/en-us/reference/engine/classes/TeleportService#TeleportAsync) . Don't  pass secure data using this method; the data is visible to the client and unencrypted.

```

local teleportData = {

    randomNumber = RNG:NextInteger(1, 100),

}

local teleportOptions = Instance.new("TeleportOptions")

teleportOptions:SetTeleportData(teleportData)

```

To retrieve all data when a user arrives at the new place after a teleport, use the [Player:GetJoinData()](/docs/en-us/reference/engine/classes/Player#GetJoinData)  function, which returns a dictionary with a TeleportData  key.

```

local Players = game:GetService("Players")

local function onPlayerAdded(player)

    local joinData = player:GetJoinData()

    local teleportData = joinData.TeleportData

    local randomNumber = teleportData.randomNumber

    print(player.Name .. " joined with the number " .. randomNumber)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

To retrieve only the teleport data on the client, you can use [TeleportService:GetLocalPlayerTeleportData()](/docs/en-us/reference/engine/classes/TeleportService#GetLocalPlayerTeleportData) .

## [Test teleports in Studio](#test-teleports-in-studio)[](#test-teleports-in-studio)

You can test [TeleportAsync()](/docs/en-us/reference/engine/classes/TeleportService#TeleportAsync)  teleports in Studio's Test  and Team Test  modes without publishing your experience. When a teleport runs during a test, the destination place opens as a new test server, so you can debug both the origin and destination places in Studio. Studio tools such as server inspection, the debugger (including breakpoints), and the device simulator carry over to the destination place. You can also test teleports in [Build](/docs/en-us/ai/build)  and through playtest automation in the [Studio MCP server](/docs/en-us/studio/mcp) .

Testing teleports only supports [TeleportAsync()](/docs/en-us/reference/engine/classes/TeleportService#TeleportAsync) . Deprecated methods like [Teleport()](/docs/en-us/reference/engine/classes/TeleportService#Teleport) , [TeleportPartyAsync()](/docs/en-us/reference/engine/classes/TeleportService#TeleportPartyAsync) , and TeleportToPlaceAsync()  aren't supported in testing. If your game still uses these methods, see [Migrate to secure teleports](#migrate-to-secure-teleports) .

### [Known limitations](#known-limitations)[](#known-limitations)

A few behaviors differ between testing and production:

-

[PrivateServerId](/docs/en-us/reference/engine/classes/DataModel#PrivateServerId)  and [JobId](/docs/en-us/reference/engine/classes/DataModel#JobId) : In Test  mode, both are always empty, even for private servers. In Team Test , every server is private, so PrivateServerId  is never empty, even for teleports to public servers. Code that checks whether PrivateServerId  is empty behaves differently in Team Test than in production.

-

[ReservedServerId](/docs/en-us/reference/engine/classes/TeleportOptions#ReservedServerId)  vs. PrivateServerId : These values can differ in Team Test, though they match in production. To send more players to the same reserved server, reuse the original ReservedServerId , not the destination server's PrivateServerId .

-

VIP teleports : Teleports that use [VipServerId](/docs/en-us/reference/engine/classes/TeleportOptions#VipServerId)  fail in testing because Team Test servers have no owner.

-

Same experience only : You can only teleport between places that share the starting place's [GameId](/docs/en-us/reference/engine/classes/DataModel#GameId) .

-

Unsupported methods : [GetPlayerPlaceInstanceAsync()](/docs/en-us/reference/engine/classes/TeleportService#GetPlayerPlaceInstanceAsync)  doesn't work in testing.

## [Handle failed teleports](#handle-failed-teleports)[](#handle-failed-teleports)

Like any API call that involves network requests, teleports can fail and throw an error. Wrap them in protected calls ([pcall()](/docs/en-us/reference/engine/globals/LuaGlobals#pcall) ). Some failures benefit from retries, particularly those involving reserved servers, so we recommend retrying some number of times on failure.

Even if a call succeeds and the teleport initiates, it can still fail at the last moment without throwing an error and leave the user in the server. When this happens, it triggers the [TeleportService.TeleportInitFailed](/docs/en-us/reference/engine/classes/TeleportService#TeleportInitFailed)  event.

The following example [ModuleScript](/docs/en-us/reference/engine/classes/ModuleScript)  returns a single SafeTeleport  function that teleports players in a protected call with retry logic. It also has a handleFailedTeleport  function to deal with situations in which the call was successful, but the teleport didn't occur.

```

local TeleportService = game:GetService("TeleportService")

local ATTEMPT_LIMIT = 5

local RETRY_DELAY = 1

local FLOOD_DELAY = 15

local function SafeTeleport(placeId, players, options)

    local attemptIndex = 0

    local success, result -- define pcall results outside of loop so results can be reported later on

    repeat

        success, result = pcall(function()

            return TeleportService:TeleportAsync(placeId, players, options) -- teleport the user in a protected call to prevent erroring

        end)

        attemptIndex += 1

        if not success then

            task.wait(RETRY_DELAY)

        end

    until success or attemptIndex == ATTEMPT_LIMIT -- stop trying to teleport if call was successful, or if retry limit has been reached

    if not success then

        warn(result) -- print the failure reason to output

    end

    return success, result

end

local function handleFailedTeleport(player, teleportResult, errorMessage, targetPlaceId, teleportOptions)

    if teleportResult == Enum.TeleportResult.Flooded then

        task.wait(FLOOD_DELAY)

    elseif teleportResult == Enum.TeleportResult.Failure then

        task.wait(RETRY_DELAY)

    else

        -- if the teleport is invalid, report the error instead of retrying

        error(("Invalid teleport [%s]: %s"):format(teleportResult.Name, errorMessage))

    end

    SafeTeleport(targetPlaceId, {player}, teleportOptions)

end

TeleportService.TeleportInitFailed:Connect(handleFailedTeleport)

return SafeTeleport

```

The SafeTeleport  function receives the same arguments as the [TeleportAsync()](/docs/en-us/reference/engine/classes/TeleportService#TeleportAsync)  function. You can use the following script with the SafeTeleport  function to perform teleports from anywhere in your game:

```

local Players = game:GetService("Players")

local TeleportService = game:GetService("TeleportService")

local ServerScriptService = game:GetService("ServerScriptService")

local SafeTeleport = require(ServerScriptService.SafeTeleport)

local PLACE_TO_TELEPORT_TO = 12345678

local function teleport(touchPart)

    local playerToTeleport = game.Players:GetPlayerFromCharacter(touchPart.Parent)

    if playerToTeleport then

        SafeTeleport(PLACE_TO_TELEPORT_TO, {playerToTeleport})

    end

end

script.Parent.Touched:Connect(teleport)

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
