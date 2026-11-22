<!-- Source: https://create.roblox.com/docs/en-us/scripting/services -->

Services | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/scripting/services.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Scripting](/docs/en-us/scripting)

# Services

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/scripting/services.md)

In [Reuse code](/docs/en-us/scripting/module) , you might have noticed frequent use of the game:GetService()  method. Roblox services let you access the built-in features of the engine, like selling in-game items, enabling chat, playing sounds, animating objects, and managing instances.

In fact, services are the first step in the most fundamental, common pattern of Roblox development :

1.

Get services.

2.

Require module scripts.

3.

Add local functions.

4.

Add the [events](/docs/en-us/scripting/events)  that trigger those functions.

For example, you might want to save players' positions in the world when they exit your game:

```

local Players = game:GetService("Players")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local SaveManager = require(ReplicatedStorage:WaitForChild("SaveManager"))

-- Local function that calls a reusable function in the module script.

local function saveProgress(character)

	-- Get the position of the player's character.

	local position = character:FindFirstChild("HumanoidRootPart").Position

	-- Use the saveData function in the module script, which writes to the

	-- DataStoreService.

	SaveManager.saveData(character, position)

end

-- Another local function that calls saveProgress() when a character is removed

-- from the game (in this case, when the player leaves).

local function onPlayerAdded(player)

	player.CharacterRemoving:Connect(saveProgress)

end

-- Calls onPlayerAdded when a player first connects to the game.

Players.PlayerAdded:Connect(onPlayerAdded)

```

Some key details include:

-

Because you should only retrieve a service once per script, the convention is to give the variable the same name as the service. This convention applies to module scripts, as well.

-

You retrieve services with the global variable [game](/docs/en-us/reference/engine/classes/DataModel) , a reference to the root of the data model.

-

Roblox doesn't make guarantees around loading order (and [instance streaming](/docs/en-us/workspace/streaming)  further complicates what is and isn't loaded at any given time), so the use of [Instance:WaitForChild()](/docs/en-us/reference/engine/classes/Instance#WaitForChild)  is an important safety measure.

Rather than comparing [standard libraries](/docs/en-us/reference/engine/libraries) , [global functions and variables](/docs/en-us/reference/engine/globals) , or third-party libraries, a big part of Roblox development is identifying which of the many, many services can help you add the desired functionality to your games. In the example above, instead of using a standard I/O library to write to disk, you use [cloud services](#cloud-services)  to store data.

## [Container services](#container-services)[](#container-services)

Container services can contain and influence other objects. These container services reside at the root of the data model and are visible in Studio's Explorer window. Collectively, these container services form a structured hierarchy for the data model, so the Roblox Engine can properly interpret and render your place. The following table includes some common container services.

| Service | | Description |
| --- | --- |
| [Workspace](/docs/en-us/reference/engine/classes/Workspace) | | Contains all objects that render in the 3D world, such as parts and terrain. |
| [Lighting](/docs/en-us/reference/engine/classes/Lighting) | | Contains objects for setting universal lighting effects, such as [Atmosphere](/docs/en-us/reference/engine/classes/Atmosphere)  and [Sky](/docs/en-us/reference/engine/classes/Sky) . |
| [ReplicatedStorage](/docs/en-us/reference/engine/classes/ReplicatedStorage)  and [ReplicatedFirst](/docs/en-us/reference/engine/classes/ReplicatedFirst) | | Contain content and logic that replicates between the server and client. |

To further examine the data model, you can use these methods:

-

[game:FindService()](/docs/en-us/reference/engine/classes/DataModel#FindService)  searches for the instance of the specified service.

-

[game:GetChildren()](/docs/en-us/reference/engine/classes/DataModel#GetChildren)  returns an array of all root children of the data model, which are the top-level container services.

-

[game:GetDescendants()](/docs/en-us/reference/engine/classes/DataModel#GetDescendants)  returns an array of all the descendants of the data model, including all container services and their children.

For more information on container services, see the [data model](/docs/en-us/projects/data-model#object-organization)  documentation.

## [Scripting services](#scripting-services)[](#scripting-services)

Scripting services provide standard functionality in the Roblox Engine that you call within scripts. The following table includes some common scripting services.

| Service | | Description |
| [TweenService](/docs/en-us/reference/engine/classes/TweenService) | | Used to interpolate numeric properties of other instances from a start to end value, with options for easing direction and style, repeat, and delay. |
| [MarketplaceService](/docs/en-us/reference/engine/classes/MarketplaceService) | | The service responsible for in-game transactions, such as prompting the player to purchase a developer product, subscription, pass, Roblox Premium, etc. |
| [RunService](/docs/en-us/reference/engine/classes/RunService) | | Contains methods and events for frame-by-frame time management, as well as for checking the context (server, client, Studio mode) in which the game is running. Useful for running any process or update on every runtime frame. |
| [SoundService](/docs/en-us/reference/engine/classes/SoundService) | | Controls various global aspects of how audio plays in a game, such as the doppler scale and volumetric audio. Can also contain sound groups to control the volume and dynamic effects properties of multiple audio signals at once. |
| [CollectionService](/docs/en-us/reference/engine/classes/CollectionService) | | Manages groups (collections) of instances with tags that replicate from the server to the client, letting you more easily assign and work with groups of related instances. |

## [Cloud services](#cloud-services)[](#cloud-services)

Roblox also has special cloud services for handling tasks and processes that occur in the Roblox cloud. The following table includes some common cloud services.

| Service | | Description |
| [DataStoreService](/docs/en-us/reference/engine/classes/DataStoreService) | | For storing persistent data across sessions. |
| [MemoryStoreService](/docs/en-us/reference/engine/classes/MemoryStoreService) | | For storing frequent and ephemeral data that change rapidly. |
| [MessagingService](/docs/en-us/reference/engine/classes/MessagingService) | | For communicating between multiple servers during live sessions. |

Cloud services also have corresponding web APIs; they're accessible from external scripts or tools. For more information, see [Open Cloud](/docs/en-us/cloud/guides) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
