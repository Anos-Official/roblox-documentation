<!-- Source: https://create.roblox.com/docs/projects/server-authority -->

Server authority model | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/projects/server-authority.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Projects](/docs/projects)
6. /
7. [Architecture](/docs/projects/data-model)
8. /
9. [Server authority](/docs/projects/server-authority)

# Server authority model

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/projects/server-authority/index.md)

In a server authority model , the server is the single source of truth  for the entire game state, and clients are only trusted to report their own inputs. This architecture is the core netcode foundation of a fair, competitive game because it prevents entire classes of cheating like flyhacks or speedhacks by never trusting a client to report its own position or state.

## [Advantages](#advantages)[](#advantages)

In a naive server-owned system, clients would simply send their inputs to the server and display the results of the game sent back by the server. While technically correct, such a system would face significant input latency  because every player action would have to travel to the server, be processed, and have the result sent back to the client before it could be displayed. For most games, especially those fast‑paced, that round‑trip delay would cause gameplay to feel laggy, unresponsive, and unplayable.

In Roblox's server authority  model, latency is compensated for by having clients instantly [predict](#client-prediction)  the effects of their inputs in addition to sending them to the server. For example, when a player presses a key, the client doesn't wait for the server to respond; instead it predicts  a few frames ahead of the last known server state. This allows the client to show the result of the input action instantly, effectively hiding network latency and making the game feel responsive.

Sometimes the client will get its prediction wrong ([misprediction](#client-misprediction) ) and, because of network latency, the client will not know that it has made a mistake for a few frames. For example:

Your client predicts that you've moved forward, but on the server another player used a stun ability that stopped you from moving. The client and server now have different states.

When a misprediction is detected, the client must correct its prediction based on the server's authoritative state . If the authoritative state is different from the client's predicted state, the client must [roll back and resimulate](#rollback-and-resimulation)  its predicted frames. This system of client‑side prediction, rollback, and resimulation is known as "latency compensation" and helps make server‑authoritative multiplayer games feel smooth and responsive.

Mispredictions are a normal and expected  part of the server authority architecture because clients inherently cannot predict other players' inputs, so actions by other players will always trigger some amount of misprediction. When tuned correctly, the resulting corrections are small and should be imperceptible to players. Read further on [advanced techniques](/docs/projects/server-authority/techniques)  to smooth out and mask network artifacts.

## [Setup](#setup)[](#setup)

The server authority model requires certain other engine technologies to function correctly. Confirm the following property settings on the [Workspace](/docs/reference/engine/classes/Workspace)  object in the [Explorer](/docs/studio/explorer) :

1.

[Workspace.AuthorityMode](/docs/reference/engine/classes/Workspace#AuthorityMode)  must be [Server](/docs/reference/engine/enums/AuthorityMode#Server)  (setting this automatically sets the following five).

2.

[Workspace.NextGenerationReplication](/docs/reference/engine/classes/Workspace#NextGenerationReplication)  must be enabled.

3.

[Workspace.PlayerScriptsUseInputActionSystem](/docs/reference/engine/classes/Workspace#PlayerScriptsUseInputActionSystem)  must be enabled.

4.

[Workspace.SignalBehavior](/docs/reference/engine/classes/Workspace#SignalBehavior)  must be [Deferred](/docs/reference/engine/enums/SignalBehavior#Deferred) .

5.

[Workspace.UseFixedSimulation](/docs/reference/engine/classes/Workspace#UseFixedSimulation)  must be enabled.

6.

[Workspace.StreamingEnabled](/docs/reference/engine/classes/Workspace#StreamingEnabled)  must be enabled.

## [Concepts](#concepts)[](#concepts)

The server authority system runs on a few core concepts as follows.

### [Client prediction](#client-prediction)[](#client-prediction)

Through client prediction , the client simulates a few frames ahead of the last known server state to predict the effects of player inputs immediately. This hides input latency, but the prediction may later turn out to be incorrect ([client misprediction](#client-misprediction) ) and thus require correction. The client tries to simulate just far enough ahead of the last known authoritative server state so that its inputs arrive on the server at the intended frame. The number of frames the client will predict ahead of the known server state is based on the latency behind the client and server.

### [Client misprediction](#client-misprediction)[](#client-misprediction)

When the client receives the authoritative state from the server, it checks that state against a historical record of what it predicted locally for that frame. When there is a difference between what the client [predicted](#client-prediction)  and what the server actually did, this is a misprediction . Mispredictions can occur for several reasons, including shifts in network latency, other players acting in ways the client didn't anticipate, the game running certain logic exclusively on the server, etc.

If the authoritative state is different from the client's predicted state, the client must [roll back and resimulate](#rollback-and-resimulation) .

### [Rollback and resimulation](#rollback-and-resimulation)[](#rollback-and-resimulation)

When a client detects a [misprediction](#client-misprediction) , it must reset to the server's authoritative state and then resimulate to jump back to its predicted frame. Based on the network latency, the client tries to simulate just far enough ahead of the last known authoritative server state so that its inputs arrive on the server at the intended frame.

In the above diagram, the client is simulating 2 frames ahead of the server. It sends its inputs for frame 3 which arrive at the intended frame (3) on the server. The server sends the authoritative state for frame 3 and the client receives it on frame 7. The client discovers it mispredicted frame 3 so it resets to the server's frame 3 and resimulates frames 4, 5 and 6 before it simulates frame 7. Players may see a noticeable network artifact such as a sudden movement.

In summary, the client :

1.

Receives the authoritative state  from the server and compares it against its own predicted state .

2.

If the client's prediction was incorrect:

1.

Client rolls back to the last known authoritative state received from the server.

2.

Client resimulates from the authoritative state to its predicted state, re-applying any local inputs.

## [Implementation](#implementation)[](#implementation)

### [Network ownership and prediction](#network-ownership-and-prediction)[](#network-ownership-and-prediction)

In the server authority model, you're able to keep the core gameplay objects server‑owned without incurring the input latency cost normally associated with server ownership. Things like cars, player characters, or other gameplay‑critical objects can remain server‑owned, even when interacting with other players.

By default, Roblox will automatically predict properties with [simulation access](#simulation-access)  near the local player [Character](/docs/reference/engine/classes/Player#Character) , but if you want more fine‑grained control, you can explicitly force an instance's prediction on or off with [RunService:SetPredictionMode()](/docs/reference/engine/classes/RunService#SetPredictionMode) .

Automatic prediction applies to whole physics assemblies, not individual instances. When the client predicts a part, it also predicts every part that's physically connected to it through welds, joints, or constraints, along with the parent [Model](/docs/reference/engine/classes/Model)  of those parts and any [Humanoid](/docs/reference/engine/classes/Humanoid)  inside that model. For example:

-

A sword model that's welded to a predicted character becomes part of the character's assembly, so it's predicted automatically.

-

A model that's parented to the character but not  physically connected to it is a separate assembly. It's only predicted if it's within the client's [simulation radius](/docs/projects/server-authority/techniques#simulation-radius)  or if you force prediction on with [RunService:SetPredictionMode()](/docs/reference/engine/classes/RunService#SetPredictionMode) .

To check whether a specific instance is currently predicted, call [RunService:GetPredictionStatus()](/docs/reference/engine/classes/RunService#GetPredictionStatus)  from the client.

### [Simulation sync](#simulation-sync)[](#simulation-sync)

In the server authority model, the client and the server must both run the core simulation, and the client's simulation needs to be able to [roll back and resimulate](#rollback-and-resimulation)  when a [misprediction](#client-misprediction)  occurs. To enable this, write your core logic inside functions bound through [RunService:BindToSimulation()](/docs/reference/engine/classes/RunService#BindToSimulation)  in a [ModuleScript](/docs/reference/engine/classes/ModuleScript)  that's initialized on both the client and server.

 ![Server authority setup](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-Server-Authority.png)

During a resimulation, Roblox will re-run the functions bound to the simulation via [BindToSimulation()](/docs/reference/engine/classes/RunService#BindToSimulation) . Processing player inputs, interacting with synchronized physics objects, and updating the core game state should live inside those bound functions.

Use [time()](/docs/reference/engine/globals/RobloxGlobals#time)  for any time-based logic inside a bound simulation function, such as driving an animation speed or oscillating a value over time. When [Workspace.AuthorityMode](/docs/reference/engine/classes/Workspace#AuthorityMode)  is [Enum.AuthorityMode.Server](/docs/reference/engine/enums/AuthorityMode#Server) , time()  is synchronized between the client and the server and uses fixed-step simulation time. During [resimulation](#rollback-and-resimulation) , it rewinds to the authoritative frame and advances as the client replays frames, so it returns a consistent value each time a frame is simulated.

Other time functions don't share this behavior. [tick()](/docs/reference/engine/globals/RobloxGlobals#tick)  and [os.time()](/docs/reference/engine/libraries/os#time)  read the local device clock, while [os.clock()](/docs/reference/engine/libraries/os#clock)  measures elapsed time from an arbitrary local baseline. They aren't synchronized between the client and the server and don't roll back during resimulation, so avoid them for simulation-affecting logic.

Simulation ServerLoader ClientLoader

[ModuleScript](/docs/reference/engine/classes/ModuleScript)  named Simulation  in [ReplicatedStorage](/docs/reference/engine/classes/ReplicatedStorage) :

Simulation

```

local RunService = game:GetService("RunService")

local Players = game:GetService("Players")

local Simulation = {}

Simulation.Initialize = function()

	RunService:BindToSimulation(function(deltaTime)

		-- Read player inputs

		-- Update game state

	end)

end

return Simulation

```

### [State sync with attributes](#state-sync-with-attributes)[](#state-sync-with-attributes)

Roblox automatically synchronizes all properties with [simulation access](#simulation-access)  on predicted instances. For custom data, [attributes](/docs/studio/properties#instance-attributes)  are the primary way to synchronize instances marked as predicted; on such instances, any mismatch in attribute values between the server's source of truth and the client's prediction will trigger a full [rollback and resimulation](#rollback-and-resimulation) .

Use attributes to store game data that affects your core simulation, including player health, ammunition, inventory, or custom rules (see [limitations](#attribute-limits) ).

Only write to attributes on predicted  instances from within functions bound through [BindToSimulation()](/docs/reference/engine/classes/RunService#BindToSimulation)  to ensure that Roblox can fully track relevant game states and resimulate properly.

#### [Attribute limits](#attribute-limits)[](#attribute-limits)

In order to be replicated, an attribute must meet all of the following criteria:

-

It is among the first 64 attributes on its [Instance](/docs/reference/engine/classes/Instance) .

-

Its name contains at most 50 characters.

-

If a string type attribute, its value contains at most 50 characters.

#### [Simulation access](#simulation-access)[](#simulation-access)

Many properties and methods in the engine API reference include the Simulation Access  label, for example [BasePart.CFrame](/docs/reference/engine/classes/BasePart#CFrame) . Properties with this label will be predicted by the server authority system. Additionally, only properties and methods with this label can be accessed inside functions bound with [RunService:BindToSimulation()](/docs/reference/engine/classes/RunService#BindToSimulation) .

### [Create and remove instances](#create-and-remove-instances)[](#create-and-remove-instances)

Inside functions bound through [BindToSimulation()](/docs/reference/engine/classes/RunService#BindToSimulation) , you can create instances with [Instance.new()](/docs/reference/engine/datatypes/Instance#new) , [Instance:Clone()](/docs/reference/engine/classes/Instance#Clone) , or [Instance.fromExisting()](/docs/reference/engine/datatypes/Instance#fromExisting) . The client creates the instance immediately, and Roblox merges it with the server's authoritative copy when that copy arrives. For details, see [predictive instance creation](/docs/projects/server-authority/techniques#predictive-instance-creation-instance-stitching) .

Removing instances works differently. [Instance:Destroy()](/docs/reference/engine/classes/Instance#Destroy)  doesn't have [simulation access](#simulation-access) , and you can't change the [Parent](/docs/reference/engine/classes/Instance#Parent)  of an instance that's already in the [DataModel](/docs/reference/engine/classes/DataModel) , so calling either inside a bound function causes an error. Instead, record the intent to remove an instance in an [attribute](#state-sync-with-attributes)  inside the simulation, then remove the instance outside the simulation, such as in a [PostSimulation](/docs/reference/engine/classes/RunService#PostSimulation)  connection on the server.

Server Script - Remove an Instance Outside the Simulation

```

local RunService = game:GetService("RunService")

local character = script.Parent

RunService.PostSimulation:Connect(function()

	-- "SwordEquipped" is written by the simulation when the player unequips the sword

	local sword = character:FindFirstChild("Sword")

	if sword and not character:GetAttribute("SwordEquipped") then

		sword:Destroy()

	end

end)

```

[Tools](/docs/reference/engine/classes/Tool)  aren't fully supported in the server authority model yet. [Humanoid:EquipTool()](/docs/reference/engine/classes/Humanoid#EquipTool)  and [Humanoid:UnequipTools()](/docs/reference/engine/classes/Humanoid#UnequipTools)  don't have [simulation access](#simulation-access) , so they can't be called inside bound functions. To build an equippable item such as a sword, clone and weld a [Model](/docs/reference/engine/classes/Model)  to the character inside the simulation and track whether it's equipped with an attribute.

### [Input actions](#input-actions)[](#input-actions)

In a server-authoritative game, the primary way for a client to affect the game's state is through the [Input Action System](/docs/input/input-action-system) . These inputs are sent to the server and are replayed during resimulation on the client. As a result, [InputActions](/docs/reference/engine/classes/InputAction)  should be used for all inputs that affect the core simulation  and they should be checked for sanity before they're processed.

To reiterate, do not use traditional events like [UserInputService.InputBegan](/docs/reference/engine/classes/UserInputService#InputBegan)  in the core simulation of a server-authoritative game.

Note that [InputContexts](/docs/reference/engine/classes/InputContext)  must be a descendent of a [Player](/docs/reference/engine/classes/Player)  so that the engine knows who has ownership over the [InputContext](/docs/reference/engine/classes/InputContext) . One approach is to add your [InputContexts](/docs/reference/engine/classes/InputContext)  to a folder under [ReplicatedStorage](/docs/reference/engine/classes/ReplicatedStorage)  and use a [Script](/docs/reference/engine/classes/Script)  under [ServerScriptService](/docs/reference/engine/classes/ServerScriptService)  to clone the [InputContexts](/docs/reference/engine/classes/InputContext)  per player:

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/IAS-InputSetup.png)

InputSetup

```

local Players = game:GetService("Players")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local InputsFolder = ReplicatedStorage:WaitForChild("Inputs")

local function onPlayerAdded(player)

	local clone = InputsFolder:Clone()

	clone.Parent = player

end

Players.PlayerAdded:Connect(onPlayerAdded)

for _, player in Players:GetPlayers() do

	onPlayerAdded(player)

end

```

Using this pattern, you can read [InputActions](/docs/reference/engine/classes/InputAction)  for all players in [RunService:BindToSimulation()](/docs/reference/engine/classes/RunService#BindToSimulation)  on both client and server to receive the same data for a given frame and record the previous frame's input in an [attribute](/docs/studio/properties#instance-attributes) , for example to trigger a character run when a RunAction  input action is triggered.

### [Remote events](#remote-events)[](#remote-events)

[Remote events](/docs/scripting/events/remote)  can still be used within the server authority model to facilitate discrete communication between client and server. For example, servers can use remote events to broadcast data about players scoring points or picking up objects, and clients can use remote events as an alternative API for sending inputs to the server, such as for button presses or tapping objects in the 3D world.

[RemoteEvents](/docs/reference/engine/classes/RemoteEvent)  might not be consistently ordered with property and attribute updates over the network. For example, if you change a property before firing a remote event on a client, the server might receive the property change after the remote event. To learn more, see [replication order](/docs/scripting/attributes#replication-order) .

### [Animations](#animations)[](#animations)

Animations that affect gameplay, such as character movement or attack animations, should be controlled inside functions bound through [BindToSimulation()](/docs/reference/engine/classes/RunService#BindToSimulation)  in the same [ModuleScript](/docs/reference/engine/classes/ModuleScript)  that runs on both the client and server. Core [Animator](/docs/reference/engine/classes/Animator)  and [AnimationTrack](/docs/reference/engine/classes/AnimationTrack)  members such as [LoadAnimation()](/docs/reference/engine/classes/Animator#LoadAnimation) , [Play()](/docs/reference/engine/classes/AnimationTrack#Play) , [Stop()](/docs/reference/engine/classes/AnimationTrack#Stop) , [AdjustSpeed()](/docs/reference/engine/classes/AnimationTrack#AdjustSpeed) , and [TimePosition](/docs/reference/engine/classes/AnimationTrack#TimePosition)  have [simulation access](#simulation-access) .

Animation state is part of the predicted simulation. When a [rollback](#rollback-and-resimulation)  occurs during an animation, the client rewinds the animation to the authoritative state and replays it along with the rest of the simulation, so client and server animations stay in sync. Because the client may replace animation tracks during a rollback, don't cache [AnimationTrack](/docs/reference/engine/classes/AnimationTrack)  references across frames. Instead, look up the live track each frame with [Animator:GetTrackByAnimationId()](/docs/reference/engine/classes/Animator#GetTrackByAnimationId) . For a full example, see [writing animation code](/docs/projects/server-authority/techniques#writing-animation-code) .

### [Sounds and effects](#sounds-and-effects)[](#sounds-and-effects)

Client-side effects like sounds and particles must be written knowing that the client simulation is merely a prediction of the authoritative server state. [BindToSimulation()](/docs/reference/engine/classes/RunService#BindToSimulation)  limits what properties and methods can be called from within bound functions to help guide you in writing only to the synchronized simulation state. Displaying the results of this simulation, triggering effects and sounds, etc. should be done in a separate function connected to [RenderStepped](/docs/reference/engine/classes/RunService#RenderStepped)  that reads the results of the simulation and triggers the desired effects.

Because the client might predict an event that never happens on the server, your rendering code should be able to undo or hide mispredicted effects. Further guidance around rendering a predicted simulation is covered in [playing sounds and visual effects](/docs/projects/server-authority/techniques#playing-sounds-and-visual-effects) .

## [Example projects](#example-projects)[](#example-projects)

In addition to this documentation, the following templates can help you get started:

[![](https://prod.docsiteassets.roblox.com/assets/misc/SA-Icon-Racing.jpg)](https://www.roblox.com/games/134686834388911/Racing-Server-Authority-Template) Racing

[![](https://prod.docsiteassets.roblox.com/assets/misc/SA-Icon-Soccer.jpg)](https://www.roblox.com/games/110687099504272/Soccer-Server-Authority-Template) Soccer

[![](https://prod.docsiteassets.roblox.com/assets/misc/SA-Icon-Laser-Tag.jpg)](https://www.roblox.com/games/90572444221193/Laser-Tag-Server-Authority-Template) Laser Tag

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
