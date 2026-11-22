<!-- Source: https://create.roblox.com/docs/players -->

Users and players | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/players.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Players](/docs/players)

# Users and players

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/players/index.md)

When a Roblox user joins a game, they are represented as a [Player](/docs/reference/engine/classes/Player)  in the [DataModel](/docs/reference/engine/classes/DataModel) . This [Player](/docs/reference/engine/classes/Player)  object contains information about the user that's universal across games, such as their username, friend list, and saved [avatar character](/docs/characters#player-characters) , as well as properties, methods, and events that affect the user's [lifecycle](#lifecycle)  between joining and leaving the game. Each [Player](/docs/reference/engine/classes/Player)  object also parents four important [containers](#containers)  that you can use to customize a user's experience: [Backpack](/docs/reference/engine/classes/Backpack) , [StarterGear](/docs/reference/engine/classes/StarterGear) , [PlayerGui](/docs/reference/engine/classes/PlayerGui) , and [PlayerScripts](/docs/reference/engine/classes/PlayerScripts) .

Each [Player](/docs/reference/engine/classes/Player)  also exposes a [Player.User](/docs/reference/engine/classes/Player#User)  property, which is a [User](/docs/reference/engine/datatypes/User)  that represents the player's identity within the current game's domain. The [Id](/docs/reference/engine/datatypes/User#Id)  property is always that user's [effective user ID](/docs/players/users#effective-user-ids-and-domains)  for the associated domain. For more information on effective user IDs, see [Users and scoped user IDs](/docs/players/users) .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Players-Player-Hierarchy.png)

## [Lifecycle](#lifecycle)[](#lifecycle)

The [Players](/docs/reference/engine/classes/Players)  service contains all the [Player](/docs/reference/engine/classes/Player)  instances in a game. Client and server-side scripts can both connect to the [Players.PlayerAdded](/docs/reference/engine/classes/Players#PlayerAdded)  and [Players.PlayerRemoved](/docs/reference/engine/classes/Players#PlayerRemoved)  events to perform actions in response to the lifecycle of a [Player](/docs/reference/engine/classes/Player)  object. Scripts can also connect to the [Player.CharacterAdded](/docs/reference/engine/classes/Player#CharacterAdded)  and [Player.CharacterRemoving](/docs/reference/engine/classes/Player#CharacterRemoving)  events to perform gameplay-related actions for when the character spawns or despawns.

### [User join](#user-join)[](#user-join)

When a user client connects to a game, the [Players.PlayerAdded](/docs/reference/engine/classes/Players#PlayerAdded)  event fires and passes the [Player](/docs/reference/engine/classes/Player)  object of the user who joins; you can use this object for numerous purposes such as loading [user data](/docs/cloud-services/data-stores-vs-memory-stores)  from a data store or assigning the player to a [team](/docs/players/teams) .

For example, to load a user's data when they join a game, use the [PlayerAdded](/docs/reference/engine/classes/Players#PlayerAdded)  event in a [Script](/docs/reference/engine/classes/Script)  to retrieve the user's data stored in a data store under their user ID:

Script in ServerScriptService

```

local DataStoreService = game:GetService("DataStoreService")

local Players = game:GetService("Players")

local playerDataStore = DataStoreService:GetDataStore("PlayerData")

Players.PlayerAdded:Connect(function(player)

	local userId = player.UserId

	-- Read data store key

	local getSuccess, currentData = pcall(function()

		return playerDataStore:GetAsync(userId)

	end)

	if getSuccess then

		print(currentData)

	end

	-- Do further actions with currentData

end)

```

### [Character spawn](#character-spawn)[](#character-spawn)

By default, a user's [Player.Character](/docs/reference/engine/classes/Player#Character)  model represents their platform avatar and [Players.CharacterAutoLoads](/docs/reference/engine/classes/Players#CharacterAutoLoads)  is true , meaning the character model automatically spawns when the user joins a game.

When a user's [Player.Character](/docs/reference/engine/classes/Player#Character)  spawns, [Scripts](/docs/reference/engine/classes/Script)  and [LocalScripts](/docs/reference/engine/classes/LocalScript)  in [StarterCharacterScripts](/docs/reference/engine/classes/StarterCharacterScripts)  clone into the character model and the [Player.CharacterAdded](/docs/reference/engine/classes/Player#CharacterAdded)  event fires. This event passes the new character model to its listeners which you can use to find the character's [Humanoid](/docs/reference/engine/classes/Humanoid)  object and modify its behavior. For example, you can use [Humanoid:ApplyDescription()](/docs/reference/engine/classes/Humanoid#ApplyDescription)  to change the outfit of the avatar.

### [Character despawn](#character-despawn)[](#character-despawn)

When the player's [Humanoid](/docs/reference/engine/classes/Humanoid)  dies, the server automatically removes the character model after the amount of time specified by [Players.RespawnTime](/docs/reference/engine/classes/Players#RespawnTime) . You can then use the [Player.CharacterRemoving](/docs/reference/engine/classes/Player#CharacterRemoving)  event to reset other objects or update data associated with the character.

### [User leave](#user-leave)[](#user-leave)

When a user client disconnects from a game, the server destroys its associated [Player](/docs/reference/engine/classes/Player)  object inside the [Players](/docs/reference/engine/classes/Players)  service. At this point, the [Players.PlayerRemoving](/docs/reference/engine/classes/Players#PlayerRemoving)  event fires and passes the [Player](/docs/reference/engine/classes/Player)  object of the user who disconnected. You can use this for numerous purposes such as saving user data, removing player stats from a scoreboard, or destroying player‑created models in the game.

The following example [Script](/docs/reference/engine/classes/Script)  listens to the [PlayerRemoving](/docs/reference/engine/classes/Players#PlayerRemoving)  event and attempts to save the user's data in a data store under their user ID:

Script in ServerScriptService

```

local DataStoreService = game:GetService("DataStoreService")

local Players = game:GetService("Players")

local playerDataStore = DataStoreService:GetDataStore("PlayerData")

Players.PlayerRemoving:Connect(function(player)

	local userId = player.UserId

	-- Get the player's data state in the game

	local currentData = getCurrentData(player)

	-- Save to data store

	local setSuccess, errorMessage = pcall(function()

	    playerDataStore:SetAsync(userId, currentData)

	end)

	if not setSuccess then

	    warn(errorMessage)

	end

end)

```

## [Containers](#containers)[](#containers)

Each [Player](/docs/reference/engine/classes/Player)  object representing a user's client stores several important containers: [Backpack](/docs/reference/engine/classes/Backpack) , [StarterGear](/docs/reference/engine/classes/StarterGear) , [PlayerGui](/docs/reference/engine/classes/PlayerGui) , and [PlayerScripts](/docs/reference/engine/classes/PlayerScripts) . At game runtime, several containers in the "edit" data model copy their contents over to these [Player](/docs/reference/engine/classes/Player)  containers, including [StarterGui](/docs/reference/engine/classes/StarterGui)  to [PlayerGui](/docs/reference/engine/classes/PlayerGui) , [StarterPack](/docs/reference/engine/classes/StarterPack)  to [Backpack](/docs/reference/engine/classes/Backpack) , and [StarterPlayerScripts](/docs/reference/engine/classes/StarterPlayerScripts)  to [PlayerScripts](/docs/reference/engine/classes/PlayerScripts) .

![A diagram that maps objects between 'edit' and 'runtime' data models.](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Data-Model-Mapping.png)

Backpack StarterGear PlayerGui PlayerScripts

[Tool](/docs/reference/engine/classes/Tool)  objects in the [Backpack](/docs/reference/engine/classes/Backpack)  make up the player's inventory and display as icon buttons at the bottom of the screen. See [in‑game tools](/docs/players/tools)  for more information.

As illustrated above, the contents of [StarterPack](/docs/reference/engine/classes/StarterPack)  and the player's [StarterGear](/docs/reference/engine/classes/StarterGear)  clone to [Backpack](/docs/reference/engine/classes/Backpack)  when a player's [Character](/docs/reference/engine/classes/Player#Character)  spawns. When the character dies, the client destroys the [Backpack](/docs/reference/engine/classes/Backpack)  and replaces it with a new one.

To disable the default Roblox inventory GUI and replace it with your own, call [StarterGui:SetCoreGuiEnabled()](/docs/reference/engine/classes/StarterGui#SetCoreGuiEnabled)  in a [LocalScript](/docs/reference/engine/classes/LocalScript)  as outlined in [disable default UI](/docs/players/disable-ui) .

## [Ban users](#ban-users)[](#ban-users)

To ensure civility and fair play in your games, you can ban users who violate rules or community guidelines. You can modify ban durations, ban messages, and even extend bans to potential alternate accounts. When using this feature, you must follow banning [guidelines](#ban-guidelines)  and [messaging](#message-guidelines) .

You have several options for working with bans:

-

Each game page on the [Creator Hub](https://create.roblox.com/)  has a [Bans](/docs/production/bans)  dashboard.

-

For programmatic usage with the engine API, see [Players:BanAsync()](/docs/reference/engine/classes/Players#BanAsync) .

-

For Open Cloud, see [bans and blocks](/docs/cloud/features/bans-and-blocks) .

### [Device blocking](#device-blocking)[](#device-blocking)

In addition to banning an account, [Players:BanAsync()](/docs/reference/engine/classes/Players#BanAsync)  supports device blocking  through the ApplyDeviceBlock  field in its config table. When you ban a user who is currently connected to your game with ApplyDeviceBlock  set to true , the device associated with that user is also blocked from rejoining for 24 hours. This option adds friction against ban evasion; banned players can't immediately rejoin the game from a new account on the same device.

-

Device blocking currently only applies to players on desktop (Windows and macOS). It does not apply to mobile devices or consoles.

-

The device block does not propagate as a ban to any other accounts that have used the device.

-

Calling the unban API on the affected user immediately removes any active device block associated with that user's device, allowing them to rejoin the game.

### [Ban guidelines](#ban-guidelines)[](#ban-guidelines)

When implementing bans in your game, adhere to the following guidelines:

-

Game rules must not contradict Roblox's [Community Standards](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards)  and [Terms of Use](https://en.help.roblox.com/hc/en-us/articles/115004647846-Roblox-Terms-of-Use) . For example, you cannot create a game rule that excludes someone because of their gender, as this violates [Roblox's Discrimination, Slurs, and Hate Speech policy](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards#discrimination-slurs-and-hate-speech) .

-

Creators must clearly state their game rules somewhere accessible to all users.

-

Creators must apply their game rules fairly and not arbitrarily target certain users.

-

Users can appeal to creators directly if they believe their ban was incorrect. Roblox will not mediate these appeals, unless the user believes the creator's game rules or enforcement of their rules violate the [Community Standards](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards) .

-

Roblox can moderate a game if there is reason to believe that a creator's game rules or enforcement of their rules violate the [Community Standards](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards) .

### [Message guidelines](#message-guidelines)[](#message-guidelines)

When a user is banned, they receive an error modal displaying information such as the ban length and reason. In the text-filtered message, you can include additional information such as appeal or contact information as long as you meet Roblox's [Community Standards](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards) .

For example, in your ban messages, you are allowed to reference brand names and platforms:

-

"Visit the Discord in my group/game page"

-

"Message me on Twitter or X"

Mentions of personal information or direct links are not allowed in this message field. This includes posting a specific username or handle, or providing a direct link to a Discord server or X account.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
