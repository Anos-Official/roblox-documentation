<!-- Source: https://create.roblox.com/docs/en-us/workspace/streaming/techniques -->

Techniques and conversion | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/workspace/streaming/techniques.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Projects](/docs/en-us/projects)
6. /
7. [Architecture](/docs/en-us/projects/data-model)
8. /
9. [Instance streaming](/docs/en-us/workspace/streaming)

# Techniques and conversion

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/workspace/streaming/techniques.md)

This guide outlines several techniques for using in-game [instance streaming](/docs/en-us/workspace/streaming)  efficiently and effectively. While there's no "one size fits all" solution for designing a streaming game, following these high‑level steps will get you most of the way there.

If you are converting a non-streaming game to streaming, be sure to check out the [AI streaming conversion skill](#ai-streaming-conversion-skill)  which can convert games to streaming automatically.

## [Streaming properties](#streaming-properties)[](#streaming-properties)

Once [StreamingEnabled](/docs/en-us/reference/engine/classes/Workspace#StreamingEnabled)  is toggled on for the [Workspace](/docs/en-us/reference/engine/classes/Workspace)  object in Studio, set its related properties to the following recommended values:

| Property | | Recommendation |
| --- | --- |
| [EnableSLIMAvatars](/docs/en-us/reference/engine/classes/Workspace#EnableSLIMAvatars) | | Use [Enabled](/docs/en-us/reference/engine/enums/RolloutState#Enabled)  to render R15 avatars as lightweight, animated stand‑ins when appropriate. See [SLIM avatars](#slim-avatars)  for more info. |
| [ModelStreamingBehavior](/docs/en-us/reference/engine/classes/Workspace#ModelStreamingBehavior) | | Use [Improved](/docs/en-us/reference/engine/enums/ModelStreamingBehavior#Improved)  to enable the most efficient streaming for [Models](/docs/en-us/reference/engine/classes/Model)  with [BasePart](/docs/en-us/reference/engine/classes/BasePart)  descendants. |
| [StreamingIntegrityMode](/docs/en-us/reference/engine/classes/Workspace#StreamingIntegrityMode) | | Use [PauseOutsideLoadedArea](/docs/en-us/reference/engine/enums/StreamingIntegrityMode#PauseOutsideLoadedArea)  to balance gameplay integrity without pausing unnecessarily or too often. |
| [StreamingMinRadius](/docs/en-us/reference/engine/classes/Workspace#StreamingMinRadius) | | Use the default of 64  to maximize how much the engine can scale the game down for low‑end devices. |
| [StreamingTargetRadius](/docs/en-us/reference/engine/classes/Workspace#StreamingTargetRadius) | | Use the default of 1024  to strike a good balance between visibility for players on high‑end devices and a reasonable memory footprint. |
| [StreamOutBehavior](/docs/en-us/reference/engine/classes/Workspace#StreamOutBehavior) | | Use [Opportunistic](/docs/en-us/reference/engine/enums/StreamOutBehavior#Opportunistic)  to allow the client to aggressively garbage collect content, significantly reducing memory usage and helping prevent out‑of‑memory crashes. |

## [Model level-of-detail](#model-level-of-detail)[](#model-level-of-detail)

[Model.LevelOfDetail](/docs/en-us/reference/engine/classes/Model#LevelOfDetail)  helps fill in non‑streamed [Model](/docs/en-us/reference/engine/classes/Model)  content with lightweight composite or imposter meshes, making the world look visually complete. [SLIM](/docs/en-us/workspace/streaming/slim)  (Scalable Lightweight Interactive Models) are particularly effective, as players often cannot distinguish a SLIM mesh from the fully streamed‑in original.

For best results:

-

Group parts that are spatially and logically related, for example all the parts of a car.

-

Set [LevelOfDetail](/docs/en-us/reference/engine/classes/Model#LevelOfDetail)  to [SLIM](/docs/en-us/reference/engine/enums/ModelLevelOfDetail#SLIM)  on models that contain static  meshes and parts. Models that are modified at runtime or play animations are not supported.

-

Keep the spatial extent of each model under ~64 cubic studs to increase the likelihood that the entire actual model streams in together. If a model has very large extents, break it up into smaller modular models and apply an appropriate [LevelOfDetail](/docs/en-us/reference/engine/classes/Model#LevelOfDetail)  to each one.

![](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/SLIM-Disabled.jpg)[Disabled](/docs/en-us/reference/engine/enums/ModelLevelOfDetail#Disabled) /[Automatic](/docs/en-us/reference/engine/enums/ModelLevelOfDetail#Automatic)

![](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/SLIM-Enabled.jpg)[SLIM](/docs/en-us/reference/engine/enums/ModelLevelOfDetail#SLIM)

## [Model structure](#model-structure)[](#model-structure)

Beyond setting [model level‑of‑detail](#model-level-of-detail) , the structure and settings of your [Models](/docs/en-us/reference/engine/classes/Model)  has a significant impact on how well streaming performs. As you build out or convert an existing game:

-

Use atomic models for logical grouping  — When a script needs access to all of the parts within a model, set its [ModelStreamingMode](/docs/en-us/reference/engine/classes/Model#ModelStreamingMode)  to [Atomic](/docs/en-us/reference/engine/enums/ModelStreamingMode#Atomic) . This allows client‑side scripts to safely access instances inside the model without excessive use of [WaitForChild()](/docs/en-us/reference/engine/classes/Instance#WaitForChild)  (although such scripts must still use [WaitForChild()](/docs/en-us/reference/engine/classes/Instance#WaitForChild)  for the overall atomic model).

Atomicity guarantees apply only during initial replication. Once an atomic model has been replicated to the client, any new  instances added under that model are not  replicated atomically and are instead streamed according to normal [streaming behavior](/docs/en-us/workspace/streaming#technical-behavior) . Systems that dynamically modify atomic models must handle late‑arriving instances explicitly where necessary.

-

Minimize persistent models  — [Persistent](/docs/en-us/workspace/streaming#persistent)  models load after join and never stream out, permanently occupying memory. Set a model's [ModelStreamingMode](/docs/en-us/reference/engine/classes/Model#ModelStreamingMode)  to [Persistent](/docs/en-us/reference/engine/enums/ModelStreamingMode#Persistent)  only if it must  remain available and accessible to scripts at all times.

-

Decompose container models  — A common non‑streaming pattern is a single huge [Model](/docs/en-us/reference/engine/classes/Model)  that contains many NPCs, props, or similar groupings. Under streaming, container models decrease streaming efficiency and they aren't optimal for [model level‑of‑detail](#model-level-of-detail)  which works best with closely grouped instances. Decompose container models into smaller models with physically close or logically related parts.

-

Flatten deeply nested model hierarchies  — Nesting a [persistent](/docs/en-us/workspace/streaming#persistent)  model inside an [atomic](/docs/en-us/workspace/streaming#atomic)  model effectively forces the atomic model to behave as persistent. Flat hierarchies are easier to reason about under streaming.

## [SLIM avatars](#slim-avatars)[](#slim-avatars)

Platform avatars outside of the currently streamed area are not visible by default, but enabling [Workspace.EnableSLIMAvatars](/docs/en-us/reference/engine/classes/Workspace#EnableSLIMAvatars)  renders R15 avatars as lightweight, animated stand‑ins when appropriate. Effectively, the engine:

-

Renders a SLIM version when an actual avatar model streams out.

-

Swaps between SLIM and full-resolution representations based on available resources, even inside the streaming radius.

-

Throttles SLIM animations based on scene importance and available bandwidth.

SLIM avatars support R15 player characters with a body, dynamic head, [standard](/docs/en-us/avatar/character-bodies/specifications#standard-r15-rigs)  or [advanced](/docs/en-us/avatar/character-bodies/specifications#advanced-r15-rigs)  R15 rig, and rigid/layered accessories. R6 avatars, NPCs, and avatars with custom proportions are excluded. For the full list of supported and excluded avatar configurations, performance data, and troubleshooting tips, see [SLIM avatars](/docs/en-us/workspace/streaming/slim#enabling-slim-for-avatars) .

## [Script patterns](#script-patterns)[](#script-patterns)

The following script patterns are most commonly affected by streaming. The correct strategy depends on the intent of the code, so each pattern lists multiple options where appropriate.

### [Direct index to descendants](#direct-index-to-descendants)[](#direct-index-to-descendants)

Indexing into [Workspace](/docs/en-us/reference/engine/classes/Workspace)  descendants with the .  operator throws an error if any instance in the path isn't currently streamed in. The same applies to [FindFirstChild()](/docs/en-us/reference/engine/classes/Instance#FindFirstChild) , [FindFirstChildWhichIsA()](/docs/en-us/reference/engine/classes/Instance#FindFirstChildWhichIsA) , and [FindFirstChildOfClass()](/docs/en-us/reference/engine/classes/Instance#FindFirstChildOfClass)  which return nil  if the child has not streamed in.

Descendant Lookup

```

local house1 = workspace:FindFirstChild("House1") -- nil if "House1" has not streamed in

local door = workspace.House1.Door -- Broken if "House1" or "Door" has not streamed in

```

A similar pattern is accessing the [Humanoid](/docs/en-us/reference/engine/classes/Humanoid)  or other character descendants directly inside a [Player.CharacterAdded](/docs/en-us/reference/engine/classes/Player#CharacterAdded)  connection. Under streaming, the character model is parented to [Workspace](/docs/en-us/reference/engine/classes/Workspace)  before all of its descendants have replicated, so direct indexing fails.

Character Descendants

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

player.CharacterAdded:Connect(function(character)

	local humanoid = character.Humanoid

end)

```

Strategy #1 Strategy #2 Strategy #3

If the script cannot make progress without an instance, wait for it with [WaitForChild()](/docs/en-us/reference/engine/classes/Instance#WaitForChild) :

Descendant Lookup

```

local house1 = workspace:WaitForChild("House1")

local door = house1:WaitForChild("Door")

```

### [Instances sent remotely](#instances-sent-remotely)[](#instances-sent-remotely)

A [RemoteEvent](/docs/en-us/reference/engine/classes/RemoteEvent) /[RemoteFunction](/docs/en-us/reference/engine/classes/RemoteFunction)  signal and the instance it refers to travel independently, so the signal can arrive on the client before the instance is present — or the instance may never be present at all. Two likely causes include:

-

Under streaming, there may be a slight delay between when a part/model is created on the server and when it gets replicated to clients. Effectively, a part referenced by a [RemoteEvent](/docs/en-us/reference/engine/classes/RemoteEvent) /[RemoteFunction](/docs/en-us/reference/engine/classes/RemoteFunction)  may simply not exist yet, even inside a streamed area.

-

Sending a part/model reference from server to client through a [RemoteEvent](/docs/en-us/reference/engine/classes/RemoteEvent)  or [RemoteFunction](/docs/en-us/reference/engine/classes/RemoteFunction)  requires that the instance is replicated to the receiving client. Sending an instance path as a string has the same issue, as the path may resolve to a non‑existent location on the client:

Client Script

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

remoteEvent.OnClientEvent:Connect(function(data)

	local checkpoint = data.checkpoint -- Errors if "checkpoint" isn't streamed in

	local level = workspace.Levels[data.levelPath] -- Errors if path isn't streamed in

end)

```

Strategy #1 Strategy #2 Strategy #3

If the receiving client script needs the instance to proceed, include [WaitForChild()](/docs/en-us/reference/engine/classes/Instance#WaitForChild)  before using it. Note that this can yield indefinitely if the instance never streams in, so consider adding a timeout as the second parameter of [WaitForChild()](/docs/en-us/reference/engine/classes/Instance#WaitForChild) .

### [Client desynchronization](#client-desynchronization)[](#client-desynchronization)

Client‑side desynchronization should be treated as an exception, not a standard design pattern. Introducing client‑only copies or reparenting instances locally can create serious issues. Audit your code for places which rely on these types of changes persisting on the client.

For example, reparenting an instance locally from [ReplicatedStorage](/docs/en-us/reference/engine/classes/ReplicatedStorage)  to [Workspace](/docs/en-us/reference/engine/classes/Workspace)  can make that instance eligible to be streamed out. Similarly, cloning an instance locally ([Instance:Clone()](/docs/en-us/reference/engine/classes/Instance#Clone) ) from [ReplicatedStorage](/docs/en-us/reference/engine/classes/ReplicatedStorage)  into [Workspace](/docs/en-us/reference/engine/classes/Workspace)  creates a client‑only copy that is no longer part of the server replication pipeline and will not receive property updates from the original server‑owned instance.

The same concept applies when calling [Instance:Destroy()](/docs/en-us/reference/engine/classes/Instance#Destroy)  on the client for a server‑owned object. This removes the instance locally but the server still has it, so it will stream in again with its original state when eligible.

### [Proactive streaming](#proactive-streaming)[](#proactive-streaming)

When a player's next destination can be anticipated, make server‑side calls to [Player:RequestStreamAroundAsync()](/docs/en-us/reference/engine/classes/Player#RequestStreamAroundAsync)  to stream in transient areas for temporary loading, or use [Player:AddReplicationFocus()](/docs/en-us/reference/engine/classes/Player#AddReplicationFocus)  on a limited  basis for areas that should remain loaded until explicitly released.

For example, when a player character is about to teleport by [CFrame](/docs/en-us/reference/engine/datatypes/CFrame)  change to another player's house in a distant location, you can pre‑fetch the destination area to minimize pop‑in and provide a smoother transition. The following script shows how a client-to-server [remote event](/docs/en-us/scripting/events/remote)  can be fired to move a player character using a pre-fetching method. If the pre-fetch request is successful when the function returns, the minimum radius around the target location should be present on the client.

Server Script - Teleport Player Character

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local teleportEvent = ReplicatedStorage:WaitForChild("TeleportEvent")

local function teleportPlayer(player, teleportTarget)

	-- Request streaming around target location

	player:RequestStreamAroundAsync(teleportTarget)

	-- Teleport character

	local character = player.Character

	if character and character.Parent then

		local currentPivot = character:GetPivot()

		character:PivotTo(currentPivot * CFrame.new(teleportTarget))

	end

end

-- Call teleport function when the client fires the remote event

teleportEvent.OnServerEvent:Connect(teleportPlayer)

```

### [Instance property reads](#instance-property-reads)[](#instance-property-reads)

Once an instance streams out, its property updates are no longer replicated to that client. Reading properties such as [BasePart.Position](/docs/en-us/reference/engine/classes/BasePart#Position)  continue to succeed but return the last replicated value which can be arbitrarily stale.

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

-- Position may be stale if "target" has streamed out

local dist = (target.Position - player.Character.HumanoidRootPart.Position).Magnitude

```

Strategy #1 Strategy #2 Strategy #3

Move the logic to the server, as server‑side scripts see all instances at all times. This is generally the most reliable option for distance checks and other position‑sensitive logic.

### [Waiting on the critical path](#waiting-on-the-critical-path)[](#waiting-on-the-critical-path)

Some non‑streaming games load their map by cloning it from [ReplicatedStorage](/docs/en-us/reference/engine/classes/ReplicatedStorage)  into [Workspace](/docs/en-us/reference/engine/classes/Workspace) , then wait for it on the client before dismissing a loading screen and signaling readiness. Under streaming this hangs indefinitely — the client's character hasn't spawned yet, so there's no [replication focus](/docs/en-us/workspace/streaming#replication-focus) , and the spatial map instance never streams in.

Strategy #1 Strategy #2

Move the loading screen logic so that it doesn't depend on a specific spatial instance being present, for example by signaling readiness once the character has spawned and the immediate surrounding area is streamed in.

### [Signal change handling](#signal-change-handling)[](#signal-change-handling)

Signals such as [Instance.ChildAdded](/docs/en-us/reference/engine/classes/Instance#ChildAdded) /[Instance.ChildRemoved](/docs/en-us/reference/engine/classes/Instance#ChildRemoved)  and [CollectionService](/docs/en-us/reference/engine/classes/CollectionService)  signals like [GetInstanceAddedSignal()](/docs/en-us/reference/engine/classes/CollectionService#GetInstanceAddedSignal)  or [GetInstanceRemovedSignal()](/docs/en-us/reference/engine/classes/CollectionService#GetInstanceRemovedSignal)  also fire on stream in/out, indistinguishable from real spawns/removals. Receiving scripts can't tell the difference from the signal alone, so logic which assumes a signal corresponds to a "real" event needs to be updated.

Strategy #1 Strategy #2

Audit scripts for any signal listeners that could break or change significantly when triggered by stream in and/or stream out. For example, if you play audio or visual effects when an enemy NPC initially spawns into the world, assign each enemy an [attribute](/docs/en-us/studio/properties#instance-attributes)  such as Spawned  on the first spawn, and skip replaying the same audio/effects in future stream‑ins of the enemy.

Attribute Tracking

```

local CollectionService = game:GetService("CollectionService")

local TAG_NAME = "Enemy"

CollectionService:GetInstanceAddedSignal(TAG_NAME):Connect(function(enemy)

	if not enemy:GetAttribute("Spawned") then

		-- Set "Spawned" attribute on enemy for initial spawn

		enemy:SetAttribute("Spawned", true)

		-- Play audio/visual effects for this initial spawn

		playSpawnEffects(enemy)

	end

end)

```

### [Iteration over collections](#iteration-over-collections)[](#iteration-over-collections)

Client-side collection iterations like [Instance:GetChildren()](/docs/en-us/reference/engine/classes/Instance#GetChildren)  and [Instance:GetDescendants()](/docs/en-us/reference/engine/classes/Instance#GetDescendants)  return only the streamed‑in subset of descendants. This applies even when the parent itself is always replicated, such as a [Folder](/docs/en-us/reference/engine/classes/Folder)  directly under [Workspace](/docs/en-us/reference/engine/classes/Workspace)  whose spatial descendants stream in and out.

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

-- Folder "Homes" is always replicated but its children stream in and out

-- This loop may miss homes that aren't currently streamed in

for _, home in workspace.Homes:GetChildren() do

	if home.Settings.Owner.Value == player.Name then

		return home

	end

end

```

Strategy #1 Strategy #2 Strategy #3

If a complete enumeration is required, perform the scan on the server and pass the result to the player through a [RemoteEvent](/docs/en-us/reference/engine/classes/RemoteEvent)  if needed.

### [Spatial queries](#spatial-queries)[](#spatial-queries)

Client‑side spatial queries like [WorldRoot:Raycast()](/docs/en-us/reference/engine/classes/WorldRoot#Raycast) , [WorldRoot:GetPartBoundsInBox()](/docs/en-us/reference/engine/classes/WorldRoot#GetPartBoundsInBox) , and [Model:GetBoundingBox()](/docs/en-us/reference/engine/classes/Model#GetBoundingBox)  reflect only streamed‑in content. Whether that's a problem depends on what the query is used for.

Strategy #1 Strategy #2 Strategy #3 Strategy #4

Use the server for queries whose result must reflect the full world, for example a raycast that checks whether the player has line of sight to a distant target.

### [Other patterns](#other-patterns)[](#other-patterns)

The following patterns also may also apply and should be carefully considered:

-

A [Sound](/docs/en-us/reference/engine/classes/Sound)  or [AudioPlayer](/docs/en-us/reference/engine/classes/AudioPlayer)  parented to a 3D object stops when that object streams out. For ambient audio that should persist regardless of streaming, parent the emitter to a [persistent](/docs/en-us/workspace/streaming#persistent)  model or to a non‑streaming container.

-

In-game [UI](/docs/en-us/ui/in-experience-containers)  objects like [BillboardGui](/docs/en-us/reference/engine/classes/BillboardGui)  or [SurfaceGui](/docs/en-us/reference/engine/classes/SurfaceGui)  as well as [visual effects](/docs/en-us/effects)  like [Beams](/docs/en-us/reference/engine/classes/Beam)  or [Highlights](/docs/en-us/reference/engine/classes/Highlight)  whose adornee or attachment streams out simply stop rendering. This may be the intended behavior, but you should verify it.

-

[BasePart.Touched](/docs/en-us/reference/engine/classes/BasePart#Touched)  events, [ProximityPrompts](/docs/en-us/reference/engine/classes/ProximityPrompt) , [DragDetectors](/docs/en-us/reference/engine/classes/DragDetector) , and [ClickDetectors](/docs/en-us/reference/engine/classes/ClickDetector)  do not operate for players whose client doesn't have the associated part/model streamed in. If interaction must be possible from any range, the model needs to be [persistent](/docs/en-us/workspace/streaming#persistent)  or the interaction needs a different mechanism.

-

For [PathfindingService](/docs/en-us/reference/engine/classes/PathfindingService)  and client‑side pathfinding, the pathfinder only sees streamed‑in geometry on the client and it may route through obstacles that exist on the server. For strategies, see [Pathfinding - Strategies](/docs/en-us/characters/pathfinding#streaming-compatibility)  for strategies.

## [Realistic test conditions](#realistic-test-conditions)[](#realistic-test-conditions)

Once [scripts are updated](#script-patterns) , test the game thoroughly. Streaming bugs often only manifest at the edges of the streamed area or during transitions, so only testing near spawn or at target radius isn't sufficient.

-

Test with [Workspace.StreamingTargetRadius](/docs/en-us/reference/engine/classes/Workspace#StreamingTargetRadius)  set to its minimum value (64 ). Some streaming bugs only appear when the streamed area is small.

-

Play through the full traversal patterns of the game, teleport between distant areas, and revisit areas after leaving them. These are the situations that exercise stream in and stream out the most.

-

Use the [streaming debug overlay](/docs/en-us/workspace/streaming#runtime-debugging)  to monitor the active streaming settings, currently loaded regions, and runtime streaming state.

-

Watch the [Output](/docs/en-us/studio/output)  window and [Developer Console](/docs/en-us/studio/developer-console)  for errors, as many of the [script patterns](#script-patterns)  produce errors rather than silent misbehavior. Pay particular attention to errors of the form attempt to index nil with ...  which often indicate a missing [WaitForChild()](/docs/en-us/reference/engine/classes/Instance#WaitForChild)  call.

-

Equip and activate [Tools](/docs/en-us/reference/engine/classes/Tool) , fire weapons, and trigger different game interactions.

## [AI streaming conversion skill](#ai-streaming-conversion-skill)[](#ai-streaming-conversion-skill)

To assist with streaming conversion and optimization, Roblox offers an AI streaming skill  that evaluates your game, applies recommended configurations, and cleans up compatibility issues, including:

Model & World Adjustments Script & Replication Fixes Built-in Guardrails

-

Configures streaming settings to the [recommended baselines](#streaming-properties) .

-

Sets [level-of-detail](#model-level-of-detail)  for models to [SLIM](/docs/en-us/workspace/streaming/slim)  where applicable.

-

Refactors [model structures](#model-structure)  to achieve optimal sizes and visual quality.

Even if your game already utilizes streaming, the skill will scan your existing setup, identify potential issues or areas for improvement, and automatically apply fixes to optimize it further.

To use the AI skill in your game:

1.

IMPORTANT

 Back up your game. The conversion process can be complex, so you should always  save a backup (File  ⟩ Publish to Roblox As ) before running the skill.

2.

You can run this skill directly in Assistant or using any LLM you prefer through the [Model Context Protocol (MCP)](/docs/en-us/studio/mcp)  in Studio. Higher-end AI models with large context windows are recommended; for a typical conversion, a frontier model might take 20-30 minutes and utilize roughly 200,000 tokens of context.

1.

[Enable and connect the MCP server in Studio](/docs/en-us/studio/mcp) .

2.

Open your game in Studio.

3.

Open Assistant Settings  ⟩ Skills  and ensure that rbx-convert-to-streaming  is toggled on.

4.

Prompt Assistant (or your LLM connected via MCP) to use the skill.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
