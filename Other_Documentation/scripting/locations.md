<!-- Source: https://create.roblox.com/docs/scripting/locations -->

Script types and locations | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/scripting/locations.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Scripting](/docs/scripting)

# Script types and locations

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/scripting/locations.md)

For many developers, the fundamental challenge of adapting to Roblox scripting is the importance of file location and the [Script.RunContext](/docs/reference/engine/classes/Script#RunContext)  property. Depending on script type, location in the Explorer , and run context, scripts can behave very differently. Certain method calls might fail, objects in your game might be inaccessible, or scripts might not run at all.

The reason for this complexity is that Roblox games are multiplayer by default. Scripts need the ability to only run on the server, only run on the client, or be shared across both. The evolution of the Roblox platform over time has further complicated the situation.

## [Script types](#script-types)[](#script-types)

Roblox has three types of scripts:

-

[Script](/docs/reference/engine/classes/Script)  - Code that runs on either the server or the client, depending on its location and [Script.RunContext](/docs/reference/engine/classes/Script#RunContext)  property.

-

[LocalScript](/docs/reference/engine/classes/LocalScript)  - Code that runs only on the client. Does not have a run context.

-

[ModuleScript](/docs/reference/engine/classes/ModuleScript)  - Code that you can reuse in other scripts. Does not have a run context.

When you create a [Script](/docs/reference/engine/classes/Script) , its default run context is Legacy , meaning that it a) is a server-side script and b) only runs if it is in a server container, such as [ServerScriptService](/docs/reference/engine/classes/ServerScriptService)  or [Workspace](/docs/reference/engine/classes/Workspace) .

-

If you change the script's run context to Server , it can now also run in [ReplicatedStorage](/docs/reference/engine/classes/ReplicatedStorage) , but we don't recommend it. The contents of that location are replicated to clients, so it's a poor location for server-side scripts.

-

If you change the script's run context to Client , it can run in [ReplicatedStorage](/docs/reference/engine/classes/ReplicatedStorage) . It can also run in [StarterCharacterScripts](/docs/reference/engine/classes/StarterCharacterScripts)  and [StarterPlayerScripts](/docs/reference/engine/classes/StarterPlayerScripts) . Starter containers are copied to clients, though, so the original script and  the copy run, which isn't desirable.

To change a script run context, select it in the [Explorer](/docs/studio/explorer)  and change the value in the [Properties](/docs/studio/properties)  window.

 ![RunContext property indicated for a Script.](https://prod.docsiteassets.roblox.com/assets/studio/properties/Script-RunContext.png)

## [Recommendations](#recommendations)[](#recommendations)

-

Put a single [Script](/docs/reference/engine/classes/Script)  with a RunContext  of Client  into [ReplicatedStorage](/docs/reference/engine/classes/ReplicatedStorage) .

-

Put a single [Script](/docs/reference/engine/classes/Script)  with a RunContext  of Server  into [ServerScriptService](/docs/reference/engine/classes/ServerScriptService) .

-

Use [ModuleScripts](/docs/reference/engine/classes/ModuleScript)  for as much client and server code as possible. Require these modules from your client script and your server script.

This approach gives your code a single entry point on the client and server sides, which simplifies organization and makes it easy to isolate or disable problematic modules. Add a start()  function to each [ModuleScript](/docs/reference/engine/classes/ModuleScript)  so that all modules can load before you begin executing their code:

Sample server script

```

--!strict

local ServerScriptService = game:GetService("ServerScriptService")

local SampleModule = require(ServerScriptService.SampleModule)

local AnotherSampleModule = require(ServerScriptService.AnotherSampleModule)

SampleModule.start()

AnotherSampleModule.start()

```

Sample module

```

--!strict

local CollectionService = game:GetService("CollectionService")

local NPC_TAG = "npc"

local SampleModule = {}

local function setUpNpc(npc: Instance)

    -- initialize each NPC

end

local function cleanUpNpc(npc: Instance)

    -- run when event fires

end

function SampleModule.start() -- add the function to the table

    -- example loop for setup based on tags

    for _, npc in CollectionService:GetTagged(NPC_TAG) do

        setUpNpc(npc)

    end

    -- run functions when events fire

    CollectionService:GetInstanceAddedSignal(NPC_TAG):Connect(setUpNpc)

    CollectionService:GetInstanceRemovedSignal(NPC_TAG):Connect(cleanUpNpc)

end

return SampleModule

```

-

To share code, use [ModuleScripts](/docs/reference/engine/classes/ModuleScript)  in ReplicatedStorage  and require them in both your client script and your server script.

-

If necessary for your game, repeat the same pattern in [ReplicatedFirst](/docs/reference/engine/classes/ReplicatedFirst)  with a single client script and a minimal number of [ModuleScripts](/docs/reference/engine/classes/ModuleScript)  to implement a loading screen. To learn more about ReplicatedFirst , see [Replication order](/docs/scripting/attributes#replication-order) .

-

Use [LocalScripts](/docs/reference/engine/classes/LocalScript)  sparingly. If you must use them, put them in StarterCharacterScripts , StarterPlayerScripts , StarterGui , or StarterPack .

Scripts in these containers clone to player containers rather than running from one location, which can complicate debugging. Using ReplicatedStorage  for client code lets you click lines in the Output  window and go to ReplicatedStorage.YourScript  (the stable location of the script) rather than Players.YourName.PlayerScripts.YourLocalScript  (the ephemeral location that the script was copied to at runtime).

-

Avoid attaching scripts directly to instances in [Workspace](/docs/reference/engine/classes/Workspace) . Instead, [tag instances](/docs/studio/properties#instance-tags)  and use [CollectionService](/docs/reference/engine/classes/CollectionService)  to work with them from a single [ModuleScript](/docs/reference/engine/classes/ModuleScript) .

The key exception is if you distribute models or packages on the Creator Store. In that case, you might need to include scripts within the instance hierarchy; specify a RunContext  for each script to remove ambiguity from how it runs. Explicitly setting this property makes models and packages more likely to work properly from a variety of locations.

### [Example project structure](#example-project-structure)[](#example-project-structure)

The [Plant](/docs/resources/plant-reference-project)  reference project shows how you might organize your code in a large, complex game. It stores the vast majority of its code as reusable [ModuleScripts](/docs/reference/engine/classes/ModuleScript) .

## [Script locations](#script-locations)[](#script-locations)

| Location | | Description |
| --- | --- |
| [Workspace](/docs/reference/engine/classes/Workspace) | | Represents the game's 3D world. Can run server scripts that attach directly to objects and control their behavior. |
| [ReplicatedFirst](/docs/reference/engine/classes/ReplicatedFirst) | | Contains objects that replicate to the client before anything else. This location is ideal for the absolute minimum set of objects and client scripts necessary to display a loading screen. |
| [ReplicatedStorage](/docs/reference/engine/classes/ReplicatedStorage) | | Contains objects that are replicated to both the client and the server. This location is ideal for [Scripts](/docs/reference/engine/classes/Script)  with a [RunContext](/docs/reference/engine/classes/BaseScript#RunContext)  of [Client](/docs/reference/engine/enums/RunContext) , client [ModuleScripts](/docs/reference/engine/classes/ModuleScript) , and [ModuleScripts](/docs/reference/engine/classes/ModuleScript)  that you want to use on both the server and the client. [LocalScripts](/docs/reference/engine/classes/LocalScript)  do not run from this location. |
| [ServerScriptService](/docs/reference/engine/classes/ServerScriptService) | | Contains server scripts. This location is ideal for scripts that need to access server-side functionality or objects, such as game logic and cloud storage. |
| [ServerStorage](/docs/reference/engine/classes/ServerStorage) | | Contains server-side objects. This location is ideal for large objects that don't need to be immediately replicated to clients when they join a game. Scripts do not run from this location, but you can store server-side [ModuleScripts](/docs/reference/engine/classes/ModuleScript)  here. |
| [StarterPlayer](/docs/reference/engine/classes/StarterPlayer)  ⟩ [StarterCharacterScripts](/docs/reference/engine/classes/StarterCharacterScripts) | | Contains [LocalScripts](/docs/reference/engine/classes/LocalScript)  that run when the character spawns. |
| [StarterPlayer](/docs/reference/engine/classes/StarterPlayer)  ⟩ [StarterPlayerScripts](/docs/reference/engine/classes/StarterPlayerScripts) | | Contains [LocalScripts](/docs/reference/engine/classes/LocalScript)  that run when the player joins the game. |
| [StarterGui](/docs/reference/engine/classes/StarterGui) | | Contains GUI elements that the client displays when it loads the game. [LocalScripts](/docs/reference/engine/classes/LocalScript)  can run from this location. |
| [StarterPack](/docs/reference/engine/classes/StarterPack) | | Generally only contains [Tools](/docs/reference/engine/classes/Tool) , but can also include [LocalScripts](/docs/reference/engine/classes/LocalScript)  for setting up player backpacks. |

This image shows which Explorer  window locations can contain client scripts. Remember, ReplicatedFirst  and ReplicatedStorage  can contain [Scripts](/docs/reference/engine/classes/Script)  with a [RunContext](/docs/reference/engine/classes/BaseScript#RunContext)  of [Client](/docs/reference/engine/enums/RunContext) , whereas the Starter[]  containers should use [LocalScripts](/docs/reference/engine/classes/LocalScript) .

 ![Diagram showing which script locations run on clients.](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Client-Script-Containers.png)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
