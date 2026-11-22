<!-- Source: https://create.roblox.com/docs/en-us/onboarding/developers -->

Onboarding for developers | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/onboarding/developers.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Platform](/docs/en-us/get-started)
4. /
5. [Get started for experienced creators](/docs/en-us/onboarding)

# Onboarding for developers

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/onboarding/developers.md)

This page covers the Roblox fundamentals that engineers coming from other engines most often need in their first weeks. Each section explains the core idea and links to the detailed guide.

## [Common terms](#common-terms)[](#common-terms)

-

Game:  A collection of places that players join through the game's start place . Data stores, secrets, analytics, and in-game purchases are all scoped to the game, which you might also see called an experience or a universe.

-

Place:  A scene or zone within a game, with its own data model. Each server runs one place, and moving players between places requires a [teleport](/docs/en-us/projects/teleport) .

-

Instance:  A node in the data model, with properties, methods, and events. [Parts](/docs/en-us/reference/engine/classes/Part)  and [Models](/docs/en-us/reference/engine/classes/Model)  are the most common instances for building physical objects.

-

Asset:  Uploaded content with a globally unique asset ID, such as an image, mesh, sound, or animation. Some asset types, like models and animations, can be updated in place, while others, like images and sounds, require uploading a new asset.

-

Script:  Code stored as an instance in the data model. Copying a script makes a full, independent copy, not a reference to a source file.

For more on how games and places relate, see [Games and places](/docs/en-us/production/publishing/publish-games-and-places) .

## [Data model structure](#data-model-structure)[](#data-model-structure)

The [data model](/docs/en-us/projects/data-model)  is the tree of instances that makes up a place. Its top-level services each have a specific purpose and replication behavior:

| Service | | What belongs there |
| --- | --- |
| [Workspace](/docs/en-us/reference/engine/classes/Workspace) | | The single 3D world of the place. When you edit it in Studio, you edit the server's view of the world, and part of it replicates to each client. |
| [ReplicatedStorage](/docs/en-us/reference/engine/classes/ReplicatedStorage) | | Modules, client code, effects, and other instances that both the client and server need at all times. |
| [ReplicatedFirst](/docs/en-us/reference/engine/classes/ReplicatedFirst) | | Content that replicates to clients before anything else, usually loading screens. |
| [ServerStorage](/docs/en-us/reference/engine/classes/ServerStorage) | | Server-only instances that clients don't need constant access to, such as maps that you swap in and out of the workspace. |
| [ServerScriptService](/docs/en-us/reference/engine/classes/ServerScriptService) | | Server-only scripts and modules. |
| [StarterGui](/docs/en-us/reference/engine/classes/StarterGui) | | [ScreenGuis](/docs/en-us/reference/engine/classes/ScreenGui)  and other UI that copies to each player. |
| [StarterPlayer](/docs/en-us/reference/engine/classes/StarterPlayer) | | Scripts and settings for players and characters, although larger projects usually keep code in [ReplicatedStorage](/docs/en-us/reference/engine/classes/ReplicatedStorage)  instead. |

 ![The editing data model next to the runtime data model, showing how StarterGui, StarterPack, StarterCharacterScripts, and StarterPlayerScripts copy into each player and character at runtime.](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Data-Model-Mapping.png)

The hierarchy in the Explorer  is mostly organizational:

-

Parts use world-space transforms, not transforms relative to their parent. To attach parts to each other, use constraints, most commonly a [WeldConstraint](/docs/en-us/reference/engine/classes/WeldConstraint) . For details, see [Mechanical constraints](/docs/en-us/physics/mechanical-constraints) .

-

[Attachments](/docs/en-us/reference/engine/classes/Attachment)  are an exception, because they position relative to their parent part.

-

[Models](/docs/en-us/reference/engine/classes/Model)  use their [PrimaryPart](/docs/en-us/reference/engine/classes/Model#PrimaryPart)  as the reference point for moving and pivoting the whole model.

## [Scripting model](#scripting-model)[](#scripting-model)

In most cases, you only need two kinds of scripts:

-

A [Script](/docs/en-us/reference/engine/classes/Script)  with its [RunContext](/docs/en-us/reference/engine/classes/BaseScript#RunContext)  set to [Server](/docs/en-us/reference/engine/enums/RunContext)  or [Client](/docs/en-us/reference/engine/enums/RunContext) .

-

A [ModuleScript](/docs/en-us/reference/engine/classes/ModuleScript) , which returns a value that other scripts load with require() . Use modules for shared libraries, functions, and data.

Avoid the Legacy  run context and [LocalScripts](/docs/en-us/reference/engine/classes/LocalScript) . Their behavior depends on where they're placed, which makes code harder to organize. For recommended locations, see [Script types and locations](/docs/en-us/scripting/locations) .

Server scripts never replicate to clients. Modules replicate to clients when they're in a container that clients can access, like [ReplicatedStorage](/docs/en-us/reference/engine/classes/ReplicatedStorage) . Keep server-only modules in [ServerScriptService](/docs/en-us/reference/engine/classes/ServerScriptService)  or [ServerStorage](/docs/en-us/reference/engine/classes/ServerStorage) .

## [Networking and replication](#networking-and-replication)[](#networking-and-replication)

Roblox uses a [client-server model](/docs/en-us/projects/client-server) :

-

Changes the server makes to instances, including properties, attributes, and tags, replicate to clients automatically.

-

Changes a client makes don't replicate to the server, with a few exceptions. The main exceptions are physics for parts the client [owns](/docs/en-us/physics/network-ownership) , such as its own character, and input from the [input action system](/docs/en-us/input/input-action-system) .

-

The engine distributes physics simulation between the server and clients. Clients simulate the parts they own and send positions and velocities to the server.

To communicate between the client and server, use [remote events and callbacks](/docs/en-us/scripting/events/remote) :

-

[RemoteEvent](/docs/en-us/reference/engine/classes/RemoteEvent)  and [RemoteFunction](/docs/en-us/reference/engine/classes/RemoteFunction)  are reliable and ordered.

-

[UnreliableRemoteEvent](/docs/en-us/reference/engine/classes/UnreliableRemoteEvent)  is unreliable and unordered, for frequent updates where a dropped message doesn't matter.

-

Remotes aren't secured by default. Always validate data that the server receives from clients.

 ![A diagram of one client communicating with the server.](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Remote-Flow-Client-Server.png)

### [Server authority](#server-authority)[](#server-authority)

For competitive games, [server authority](/docs/en-us/projects/server-authority)  makes the server authoritative over physics and gameplay, while clients predict their own characters and nearby physics objects. When a client mispredicts, it rolls back and resimulates.

## [Input](#input)[](#input)

Handle input with the [input action system](/docs/en-us/input/input-action-system) . You define actions, like jump or sprint, in [InputContext](/docs/en-us/reference/engine/classes/InputContext)  instances and bind them to keys, buttons, and touch controls with [InputBinding](/docs/en-us/reference/engine/classes/InputBinding)  instances. When you use server authority, each [InputContext](/docs/en-us/reference/engine/classes/InputContext)  must be a descendant of a [Player](/docs/en-us/reference/engine/classes/Player)  so that the engine knows which player owns it. One approach is to keep your contexts in [ReplicatedStorage](/docs/en-us/reference/engine/classes/ReplicatedStorage)  and clone them to each player from a server script. For details, see [Input actions](/docs/en-us/projects/server-authority#input-actions) .

 ![An InputContext instance named PlayContext inside ReplicatedStorage.](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-InputContext.png)

## [Streaming](#streaming)[](#streaming)

[Instance streaming](/docs/en-us/workspace/streaming)  loads parts of the workspace onto each client as players move through the world, which keeps load times and memory low on all devices.

-

Instances in [ReplicatedStorage](/docs/en-us/reference/engine/classes/ReplicatedStorage)  replicate in full when a player joins, before scripts run, so they're safe to access immediately.

-

Instances in the workspace stream in and out. Client code must handle instances that aren't loaded yet.

-

Instances connected by constraints stream together to keep physics stable.

Each [Model](/docs/en-us/reference/engine/classes/Model)  has a [ModelStreamingMode](/docs/en-us/reference/engine/classes/Model#ModelStreamingMode)  that controls how it streams:

| Mode | | Behavior | | Good for |
| [Default](/docs/en-us/reference/engine/enums/ModelStreamingMode#Default) | | Parts stream individually, so a model can be partly loaded. | | Static environment pieces |
| [Atomic](/docs/en-us/reference/engine/enums/ModelStreamingMode#Atomic) | | The whole model streams in at once when any of its parts are needed. | | Characters, vehicles, and other discrete, dynamic objects |
| [Persistent](/docs/en-us/reference/engine/enums/ModelStreamingMode#Persistent) | | Always streamed in, and never streamed out. | | Lobbies, menus, and landmarks that must always be visible |
| [PersistentPerPlayer](/docs/en-us/reference/engine/enums/ModelStreamingMode#PersistentPerPlayer) | | Persistent for players you add with [Model:AddPersistentPlayer()](/docs/en-us/reference/engine/classes/Model#AddPersistentPlayer) , and atomic for everyone else. | | Content that only some players need at all times |

Assets like textures, meshes, and audio also stream at runtime. Images load at a low resolution first and then improve based on the device and how large they appear on screen.

## [Data persistence](#data-persistence)[](#data-persistence)

[DataStoreService](/docs/en-us/reference/engine/classes/DataStoreService)  saves player data across sessions. Its APIs are low level, so read [Data stores](/docs/en-us/cloud-services/data-stores)  and [Player data and purchasing](/docs/en-us/cloud-services/data-stores/player-data-purchasing)  before you design your save system. These guides cover common pitfalls like rate limits, session locking, and handling purchases safely.

Data stores are scoped to the game. To keep test data out of production, use a separate game for development. For details, see [Environments](/docs/en-us/projects/file-based-workflows#environments) .

## [Solve common tasks](#solve-common-tasks)[](#solve-common-tasks)

### [Reuse behavior across instances](#reuse-behavior-across-instances)[](#reuse-behavior-across-instances)

Because copied scripts are independent copies, avoid putting a copy of the same script in every instance that needs it. Instead, tag instances with [CollectionService](/docs/en-us/reference/engine/classes/CollectionService)  and write one script, backed by a [ModuleScript](/docs/en-us/reference/engine/classes/ModuleScript) , that attaches behavior to every tagged instance.

### [Use a custom character](#use-a-custom-character)[](#use-a-custom-character)

Characters can use the platform avatar, the platform rig with a custom look, or an entirely custom rig. To keep the default spawn system but replace the character, place a model named StarterCharacter  in [StarterPlayer](/docs/en-us/reference/engine/classes/StarterPlayer) .

### [Override the default control scripts](#override-the-default-control-scripts)[](#override-the-default-control-scripts)

Roblox adds default camera and control scripts to each player. To replace them:

1.

Enable [Workspace.PlayerScriptsUseInputActionSystem](/docs/en-us/reference/engine/classes/Workspace#PlayerScriptsUseInputActionSystem) , which moves the default player scripts under [StarterPlayer](/docs/en-us/reference/engine/classes/StarterPlayer) .

2.

Set [StarterPlayer.CreateDefaultPlayerModule](/docs/en-us/reference/engine/classes/StarterPlayer#CreateDefaultPlayerModule)  to false  so that the default camera and control scripts aren't added.

3.

Add your own camera and control scripts.

### [Create shader-like effects](#create-shader-like-effects)[](#create-shader-like-effects)

Roblox doesn't support custom shaders. Instead:

-

Use [SurfaceAppearance](/docs/en-us/reference/engine/classes/SurfaceAppearance)  or [MaterialVariant](/docs/en-us/reference/engine/classes/MaterialVariant)  for [PBR materials](/docs/en-us/art/modeling/surface-appearance) .

-

Use [SurfaceAppearance](/docs/en-us/reference/engine/classes/SurfaceAppearance)  or the [Neon](/docs/en-us/reference/engine/enums/Material#Neon)  material for emissive surfaces.

-

Use the [ForceField](/docs/en-us/reference/engine/enums/Material#ForceField)  material for intersection effects.

-

For special cases, generate dynamic textures and geometry with [EditableImage](/docs/en-us/reference/engine/classes/EditableImage)  and [EditableMesh](/docs/en-us/reference/engine/classes/EditableMesh) .

## [Performance](#performance)[](#performance)

Performance on Roblox depends mostly on the content you add and the time your scripts take each frame. Test regularly on your target hardware, and set budgets early for scene complexity (triangles, draw calls, and dynamic lights), physics, replication, and script time per frame. Most performance problems come from content that's configured incorrectly, and fixing them late often means reworking assets.

-

Automatic quality:  Most players use automatic graphics quality, which has 10 levels. As the level drops to keep frame rates up, the engine lowers render distance, geometry quality such as level of detail and SLIM, shading quality, lighting quality, shadows, particle emission, and streaming radius. Draw distance never drops below 500 studs, shadows turn off below level 4, and terrain water and beams look the same at every level. Roblox tunes these values continually, so don't design around exact numbers. To preview, change Editor Quality Level  in Studio settings, and test at both the lowest and highest levels. For details, see [Graphics quality levels](/docs/en-us/performance-optimization/design#graphics-quality-levels) .

-

Texture streaming:  Textures stream and scale automatically to fit memory budgets and on-screen size.

-

Occlusion culling:  The engine automatically skips draw calls for parts, meshes, and terrain hidden behind other objects. Structuring levels with walls and other view blockers lets you manage scene complexity. Simple hidden block parts inside walls make occlusion tests cheaper than relying on detailed meshes. For more ways to reduce draw calls, see [Rendering](/docs/en-us/performance-optimization/improve#rendering) .

-

Scripting:  Luau is fast enough for complex, dynamic gameplay code. You don't need to avoid garbage collection or pool objects, and creating instances at runtime is fast.

-

Lighting:  Scenes can use many lights. Roblox scales lighting quality automatically by device, and falls back to a lower-cost lighting path in complex scenes.

For tools to measure and fix problems, see [Performance optimization](/docs/en-us/performance-optimization) .

## [Tools and AI](#tools-and-ai)[](#tools-and-ai)

-

External editors:  Use VS Code or another editor with [Script Sync](/docs/en-us/scripting/sync)  or [Rojo](/docs/en-us/projects/rojo) . Add the Luau Language Server and the selene linter for type checking and linting. For team setups, see [Compare file-based workflows](/docs/en-us/projects/file-based-workflows) .

-

Studio MCP server:  Most professional developers will want to use their own AI tools and agent harness, like a coding agent in a terminal or editor. The [Studio MCP server](/docs/en-us/studio/mcp)  connects those tools to Studio so they can build and test directly in your open session.

-

Assistant:  [Assistant](/docs/en-us/assistant/guide)  is Studio's built-in AI helper for writing code and building, for when you want AI help without setting up your own tools.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
