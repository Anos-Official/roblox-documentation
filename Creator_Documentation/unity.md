<!-- Source: https://create.roblox.com/docs/en-us/unity -->

Roblox for Unity developers | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/unity.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Platform](/docs/en-us/get-started)
4. /
5. [Get started for experienced creators](/docs/en-us/onboarding)

# Roblox for Unity developers

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/unity.md)

This page contains information to help experienced Unity developers get started with Roblox, including basic orientation, a conceptual comparison, and key differences between the two platforms.

## [Get oriented](#get-oriented)[](#get-oriented)

 ![The Unity user interface with markup to show the various windows and panels.](https://prod.docsiteassets.roblox.com/assets/engine-comparisons/Unity-Editor-Layout.png)  ![The Roblox Studio user interface with markup to show the various windows and panels.](https://prod.docsiteassets.roblox.com/assets/studio/general/Studio-Layout.png)

Unity's Hierarchy  window and Roblox Studio's [Explorer](/docs/en-us/studio/explorer)  are the primary windows for organizing elements in 3D scenes:

-

Both allow you to manage and organize objects (for example, characters and environmental assets).

-

Both use a tree structure for the parent-child relationships between objects.

However, the Hierarchy  window has no predefined structure, whereas the Explorer  window has a strict structure. It might help to think of the Explorer  window as a combination of Unity's Hierarchy  and Project  windows, with the [Workspace](/docs/en-us/reference/engine/classes/Workspace)  folder as the most recognizable element.

Similarly, the Roblox Studio [Asset Manager](/docs/en-us/projects/assets/manager)  and [Toolbox](/docs/en-us/projects/assets/toolbox)  overlap with the Unity Project  window. The Asset Manager  lets you manage all assets within your game, whereas the Toolbox  lets you access any assets you've published. The Toolbox  also lets you search the [Creator Store](/docs/en-us/production/creator-store)  for assets from Roblox or the community, similar to the Unity Asset Store .

## [Philosophical differences](#philosophical-differences)[](#philosophical-differences)

Roblox is a "simulation engine" rather than a traditional game engine. Unity GameObjects  and Roblox [Parts](/docs/en-us/reference/engine/classes/Part)  both serve as the fundamental building blocks for creating objects in a 3D environment, but in practice, the two are quite different:

-

Representation : GameObjects  in Unity are a higher-level concept for any object in a scene, whereas Parts  in Roblox are designed to represent physical objects like wooden blocks and plastic spheres, rather than abstract geometry like primitive objects in Unity.

-

Physics : To perform physics simulations in Unity, you attach components like Rigidbody  and Collider  to a GameObject . In Roblox, physics are built into the Parts  data type; the engine handles interactions automatically.

You can see the difference immediately if you create a GameObject  and a Part . The GameObject  has nothing more than a position, rotation, and scale. The Part  has that same information—plus a material and color, values for reflectance and transparency, mass and shape, and much more. Turning a Part  into something more akin to an empty GameObject  means removing  a lot of built-in properties. Conversely, you can make a GameObject  that looks a lot like a Part  by adding MeshFilter , MeshRenderer , Collider , and Rigidbody  components to it.

From a scripting perspective, GameObject  is most similar to the Roblox [Instance](/docs/en-us/reference/engine/classes/Instance) , the base class for all other Roblox classes, but because you don't (and can't) create objects of type Instance , the comparison isn't especially practical.

Another comparison is the Unity GameObject  to the Roblox [Model](/docs/en-us/reference/engine/classes/Model) . Models act as a container for a collection of interconnected parts in the same way that you might establish a parent-child relationship between many GameObjects  in Unity. You specify one of the model's parts as its [primary part](/docs/en-us/parts/models#set-a-primary-part)  to define the pivot point. Models also hold scripts, animations, sound effects, prompts, constraints, particle emitters, and more.

For example, a Unity GameObject  might have components for ParticleSystem , Physics3D , SpringConstraint , and a script. In the Hierarchy window, you see a single GameObject  named SpringyFireball . The Inspector window shows the collection of components and properties.

In Roblox, a comparable SpringyFireball  model in the Explorer  window might look something like this:

```

Model

|- ParticleEmitter

|- MeshPart

|- SpringConstraint

|- ClickDetector

|  |- Script

```

Roblox's physics-by-default philosophy extends to the process of building 3D models. In Roblox, welding multiple parts together into an [assembly](/docs/en-us/physics/assemblies)  is an excellent way to quickly build things, because Roblox treats the welded parts as a single rigid body. This approach isn't available in Unity.

Rather than using standard metric units for length and mass, Roblox uses notional units called studs and Roblox Mass Units (RMUs). For approximate metric conversions and recommendations around use, see [Units](/docs/en-us/physics/units) .

## [Location matters](#location-matters)[](#location-matters)

Roblox games are multiplayer by default, so Roblox Studio includes many different storage locations with specific behaviors. For more information, see [client-server runtime](/docs/en-us/projects/client-server)  and [object organization](/docs/en-us/projects/data-model#object-organization) .

| Location | | Description |
| --- | --- |
| [Workspace](/docs/en-us/reference/engine/classes/Workspace) | | Represents the game's 3D world. Can run server scripts that attach directly to objects and control their behavior. |
| [ReplicatedFirst](/docs/en-us/reference/engine/classes/ReplicatedFirst) | | Contains objects that replicate to the client before anything else. This location is ideal for the absolute minimum set of objects and client scripts necessary to display a loading screen. |
| [ReplicatedStorage](/docs/en-us/reference/engine/classes/ReplicatedStorage) | | Contains objects that are replicated to both the client and the server. This location is ideal for [Scripts](/docs/en-us/reference/engine/classes/Script)  with a [RunContext](/docs/en-us/reference/engine/classes/BaseScript#RunContext)  of [Client](/docs/en-us/reference/engine/enums/RunContext) , client [ModuleScripts](/docs/en-us/reference/engine/classes/ModuleScript) , and [ModuleScripts](/docs/en-us/reference/engine/classes/ModuleScript)  that you want to use on both the server and the client. [LocalScripts](/docs/en-us/reference/engine/classes/LocalScript)  do not run from this location. |
| [ServerScriptService](/docs/en-us/reference/engine/classes/ServerScriptService) | | Contains server scripts. This location is ideal for scripts that need to access server-side functionality or objects, such as game logic and cloud storage. |
| [ServerStorage](/docs/en-us/reference/engine/classes/ServerStorage) | | Contains server-side objects. This location is ideal for large objects that don't need to be immediately replicated to clients when they join a game. Scripts do not run from this location, but you can store server-side [ModuleScripts](/docs/en-us/reference/engine/classes/ModuleScript)  here. |
| [StarterPlayer](/docs/en-us/reference/engine/classes/StarterPlayer)  ⟩ [StarterCharacterScripts](/docs/en-us/reference/engine/classes/StarterCharacterScripts) | | Contains [LocalScripts](/docs/en-us/reference/engine/classes/LocalScript)  that run when the character spawns. |
| [StarterPlayer](/docs/en-us/reference/engine/classes/StarterPlayer)  ⟩ [StarterPlayerScripts](/docs/en-us/reference/engine/classes/StarterPlayerScripts) | | Contains [LocalScripts](/docs/en-us/reference/engine/classes/LocalScript)  that run when the player joins the game. |
| [StarterGui](/docs/en-us/reference/engine/classes/StarterGui) | | Contains GUI elements that the client displays when it loads the game. [LocalScripts](/docs/en-us/reference/engine/classes/LocalScript)  can run from this location. |
| [StarterPack](/docs/en-us/reference/engine/classes/StarterPack) | | Generally only contains [Tools](/docs/en-us/reference/engine/classes/Tool) , but can also include [LocalScripts](/docs/en-us/reference/engine/classes/LocalScript)  for setting up player backpacks. |

## [Scripting](#scripting)[](#scripting)

Roblox games support three different types of Luau scripts:

-

Client scripts

These scripts run on the client, and the server has no visibility into their behavior. For legacy reasons, these scripts can take the form of [LocalScripts](/docs/en-us/reference/engine/classes/LocalScript)  or [Scripts](/docs/en-us/reference/engine/classes/Script)  with a [RunContext](/docs/en-us/reference/engine/classes/BaseScript#RunContext)  value of [Client](/docs/en-us/reference/engine/enums/RunContext) . Client scripts typically live in [ReplicatedStorage](/docs/en-us/reference/engine/classes/ReplicatedStorage) , [StarterPlayerScripts](/docs/en-us/reference/engine/classes/StarterPlayerScripts) , or [StarterCharacterScripts](/docs/en-us/reference/engine/classes/StarterCharacterScripts) .

-

Server scripts

These scripts run on the server, and the client has no visibility into their behavior. Server scripts have a [RunContext](/docs/en-us/reference/engine/classes/BaseScript#RunContext)  value of [Server](/docs/en-us/reference/engine/enums/RunContext)  and typically live in [ServerScriptService](/docs/en-us/reference/engine/classes/ServerScriptService) , the contents of which are not replicated to the client.

-

Module scripts

These scripts are reusable pieces of code that return exactly one value, typically a function or table (or a table of functions). Rather than duplicating code in client and server scripts, use module scripts to share code and data between the two. Module scripts often live in [ReplicatedStorage](/docs/en-us/reference/engine/classes/ReplicatedStorage) , but can live elsewhere if you want to share code between scripts on the same side of the client-server boundary.

Unity doesn't have the concept of different script types. If you choose to make a multiplayer game, Unity uses its networking libraries to indicate when a GameObject  (and its scripts) should be exclusive to the server.

In Unity, much of the engine's functionality is available through the methods of MonoBehaviour . For example, to run code before the render loop, you add code to the Update()  method. To handle physics collision events, you add code to the OnCollideEnter()  method.

Roblox scripts are more event-driven. You access similar functionality by subscribing to services and listening for updates.

### [C# and Luau](#c-and-luau)[](#c-and-luau)

For scripting, Unity uses C#. Roblox uses [Luau](/docs/en-us/luau) , a scripting language derived from [Lua 5.1](https://www.lua.org/manual/5.1/) .

Compared to C#, Luau is gradually typed and generally has a less verbose syntax. In larger projects, however, gradual typing can introduce categories of bugs that strongly typed languages like C# avoid, so consider enabling [strict type checking](/docs/en-us/luau/type-checking#inference-modes)  in Roblox scripts.

For basic syntax differences between the scripting languages, see [Luau and C# comparison](/docs/en-us/luau/luau-csharp-comparison) .

### [Luau code sample](#luau-code-sample)[](#luau-code-sample)

The following Luau code sample demonstrates how to, after a player equips a fishing pole, listen for user input (in this case, the E  key) and call additional functions:

```

local ContextActionService = game:GetService("ContextActionService")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- Get a module script from ReplicatedStorage that returns a single function

local performSomeAction = require(ReplicatedStorage.performSomeAction)

-- Assumes that this script is a child of the fishing pole

local fishingPole = script.Parent

local ACTION_CAST = "Cast"

-- Check that the key is down, then call another function

local function castLine(_actionName, inputState, _inputObject)

	if inputState == Enum.UserInputState.Begin then

		performSomeAction()

	end

end

-- Only enable the action when the player equips the fishing pole

fishingPole.Equipped:Connect(function()

	ContextActionService:BindAction(ACTION_CAST, castLine, true, Enum.KeyCode.E)

end)

-- Disable the action when the player unequips the fishing pole

fishingPole.Unequipped:Connect(function()

	ContextActionService:UnbindAction(ACTION_CAST)

end)

```

The Roblox script can be relatively concise because Roblox has many built-in assumptions: a [Player](/docs/en-us/reference/engine/classes/Player)  with a [Humanoid](/docs/en-us/reference/engine/classes/Humanoid)  character connected to the server and can equip [Tools](/docs/en-us/reference/engine/classes/Tool) . These assumptions don't exist in Unity, so the implementation would be very different.

## [Assets](#assets)[](#assets)

Unity and Roblox both support importing custom meshes and models in .fbx  format. Certain types of assets may require specific configurations and export settings from your third-party modeling software. For more information, see the following pages:

-

[Importer](/docs/en-us/studio/importer)

-

[General specifications](/docs/en-us/art/modeling/specifications)

-

[Blender and Maya export requirements](/docs/en-us/art/modeling/export-requirements)

In Unity, objects import into your Assets  directory, visible in the Project  window. In Roblox, assets import into your [Workspace](/docs/en-us/reference/engine/classes/Workspace)  and into the [Toolbox](/docs/en-us/projects/assets/toolbox)  or [Asset Manager](/docs/en-us/projects/assets/manager) .

Roblox also offers an open-source [Blender plugin](/docs/en-us/art/modeling/roblox-blender-plugin)  to streamline the import process.

## [Transforms](#transforms)[](#transforms)

Unity 's transforms and Roblox's [CFrames](/docs/en-us/reference/engine/datatypes/CFrame)  serve similar purposes in representing 3D transformations of objects:

-

Both transforms and [CFrames](/docs/en-us/reference/engine/datatypes/CFrame)  represent the position and rotation of an object in 3D space. Transforms include scale, whereas Roblox uses a [BasePart.Size](/docs/en-us/reference/engine/classes/BasePart#Size)  property that isn't part of the [CFrame](/docs/en-us/reference/engine/datatypes/CFrame) .

-

Both support multiplication for complex transformations and have built-in methods for other manipulations.

## [Collaboration](#collaboration)[](#collaboration)

In Unity, you collaborate with standard version control systems or paid services like Unity Version Control.

Roblox files live in the cloud (although you can export copies), so Roblox Studio provides built-in collaboration workflows for simultaneous editing, group management, permissions, script drafting, and more. See [Collaboration](/docs/en-us/projects/collaboration) .

Cloud syncing provides further benefits with [packages](/docs/en-us/projects/assets/packages) , the Roblox equivalent of Unity prefabs. Converting an asset or asset hierarchy to a package helps with local reusability, but also with collaboration. When you or your collaborators publish a new version of a package, you can quickly update existing instances of that package within a game or set them to auto-update.

## [Plugins](#plugins)[](#plugins)

Similar to Unity tools, Roblox Studio supports [plugins](/docs/en-us/studio/plugins) , which can simplify or give you additional control over various aspects of the development process. Plugins are available in the [Creator Store](/docs/en-us/production/creator-store) , just like assets, many for free.

## [Glossary](#glossary)[](#glossary)

| Unity | | Roblox | | Notes |
| Scene | | [Place](/docs/en-us/projects#places) | |  |
| GameObject | | [Part](/docs/en-us/reference/engine/classes/Part)  or [Model](/docs/en-us/reference/engine/classes/Model) | | See [Philosophical differences](#philosophical-differences) . |
| Prefab | | [Package](/docs/en-us/projects/assets/packages) | |  |
| Transform | | [CFrame](/docs/en-us/reference/engine/datatypes/CFrame) | | [CFrame](/docs/en-us/reference/engine/datatypes/CFrame)  doesn't include scale information. See [Transforms](#transforms) . |
| Hierarchy | | [Explorer](/docs/en-us/studio/explorer) | |  |
| Inspector | | [Properties](/docs/en-us/studio/properties) | |  |
| Scene view | | [3D viewport](/docs/en-us/studio/overview#3d-viewport) | |  |
| Game view | | [3D viewport](/docs/en-us/studio/overview#3d-viewport) | | The viewport transitions into a gameplay view when you test your game. |
| Project window | | [Asset Manager](/docs/en-us/projects/assets/manager)  or [Toolbox](/docs/en-us/projects/assets/toolbox) | |  |
| Terrain Inspector | | [Terrain Editor](/docs/en-us/studio/terrain-editor) | |  |
| Spawn point | | [SpawnLocation](/docs/en-us/reference/engine/classes/SpawnLocation) | |  |
| Console | | [Output](/docs/en-us/studio/output) | |  |
| Asset Store | | [Creator Store](/docs/en-us/production/creator-store) | |  |
| Overlays | | [Toolbar](/docs/en-us/studio/overview#toolbar-and-mezzanine) | |  |
| Tool | | [Plugin](/docs/en-us/studio/plugins) | |  |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
