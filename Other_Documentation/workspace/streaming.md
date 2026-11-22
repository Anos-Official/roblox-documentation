<!-- Source: https://create.roblox.com/docs/workspace/streaming -->

Instance streaming | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/workspace/streaming.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Projects](/docs/projects)
6. /
7. [Architecture](/docs/projects/data-model)
8. /
9. [Instance streaming](/docs/workspace/streaming)

# Instance streaming

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/workspace/streaming/index.md)

In-game instance streaming  allows the Roblox engine to dynamically load and unload 3D content and related instances in the [Workspace](/docs/reference/engine/classes/Workspace) . This can improve the overall player experience in several ways, including:

-

Faster Join Times

 — Players can start playing in one part of the world while more of the world loads in the background.

-

Memory Efficiency

 — Games can be played on devices with less memory since content is dynamically streamed in and out. More immersive and detailed worlds can be played on a wider range of devices.

-

Improved Performance

 — Better frame rates and performance, as the server can spend less time and bandwidth synchronizing changes between the world and players in it. Clients spend less time updating instances that aren't currently relevant to the player.

-

Level of Detail

 — When configured, distant models, platform avatars, and terrain remain visible even when they're not streamed to clients, keeping the game optimized without entirely sacrificing background visuals. [SLIM](/docs/workspace/streaming/slim)  provides the highest-fidelity level of detail for both models and avatars.

Instance streaming is controlled through the [Workspace.StreamingEnabled](/docs/reference/engine/classes/Workspace#StreamingEnabled)  property, enabled by default for new places created in Studio. This property cannot be set in a script.

 ![The Properties window with the StreamingEnabled property enabled.](https://prod.docsiteassets.roblox.com/assets/studio/properties/Workspace-StreamingEnabled.png)

Once you review this technical guide, it's recommended that you review the [streaming techniques](/docs/workspace/streaming/techniques)  guide on how to use streaming efficiently and effectively, and the [SLIM](/docs/workspace/streaming/slim)  guide for enabling high‑fidelity level‑of‑detail on models and avatars.

## [Technical behavior](#technical-behavior)[](#technical-behavior)

### [Scope](#scope)[](#scope)

Streaming logic and features apply exclusively to instances that are descendants of [Workspace](/docs/reference/engine/classes/Workspace) , while instances stored in other containers such as [ReplicatedStorage](/docs/reference/engine/classes/ReplicatedStorage)  and [ReplicatedFirst](/docs/reference/engine/classes/ReplicatedFirst)  are ineligible for streaming. For example, placing an [atomic](#atomic)  model under [ReplicatedStorage](/docs/reference/engine/classes/ReplicatedStorage)  does not guarantee atomic replication.

### [Stream in](#stream-in)[](#stream-in)

When a player joins a game with instance streaming enabled:

1.

Instances in the [Workspace](/docs/reference/engine/classes/Workspace)  are replicated to the client excluding  the following:

![](https://prod.docsiteassets.roblox.com/assets/misc/Wait.png)

[BaseParts](/docs/reference/engine/classes/BasePart)  ([Parts](/docs/reference/engine/classes/Part)  and [MeshParts](/docs/reference/engine/classes/MeshPart) )

![](https://prod.docsiteassets.roblox.com/assets/misc/Wait.png)

[Models](/docs/reference/engine/classes/Model)  set to [Atomic](#atomic) , [Persistent](#persistent) , or [PersistentPerPlayer](#persistentperplayer) ; see [per‑model streaming controls](#model-streaming-controls)

![](https://prod.docsiteassets.roblox.com/assets/misc/Wait.png)

[Models](/docs/reference/engine/classes/Model)  set to [Nonatomic](#nonatomic)  (default) when [Workspace.ModelStreamingBehavior](/docs/reference/engine/classes/Workspace#ModelStreamingBehavior)  is set to [Improved](/docs/reference/engine/enums/ModelStreamingBehavior#Improved)

![](https://prod.docsiteassets.roblox.com/assets/misc/Wait.png)

Descendants of the above instances

2.

During gameplay, the server may stream instances in the above deferred categories to the client based on the game's [streaming properties](#streaming-properties) , player position, client device performance, and other conditions.

### [Stream out](#stream-out)[](#stream-out)

During gameplay, a client may remove regions of [BaseParts](/docs/reference/engine/classes/BasePart)  from the player's [Workspace](/docs/reference/engine/classes/Workspace)  based on the behavior set by [Workspace.StreamOutBehavior](/docs/reference/engine/classes/Workspace#StreamOutBehavior) . The process begins with regions furthest away from the [replication foci](#replication-focus)  and moves in closer, as needed. Regions inside the [Workspace.StreamingMinRadius](/docs/reference/engine/classes/Workspace#StreamingMinRadius)  range never stream out.

Note that a [Model](/docs/reference/engine/classes/Model)  with no [BasePart](/docs/reference/engine/classes/BasePart)  descendants, such as one used merely as a "container" for non‑[BasePart](/docs/reference/engine/classes/BasePart)  instances like scripts, is exempt  from streaming out unless  it is made a descendant of a [BasePart](/docs/reference/engine/classes/BasePart) .

Instances which are created  or cloned  by client-side scripts are exempted from streaming out unless they are parented under a server‑created instance.

When an instance streams out, it is parented to nil  so that any existing Luau state will reconnect if the instance streams back in. As a result, removal signals such as [ChildRemoved](/docs/reference/engine/classes/Instance#ChildRemoved)  or [DescendantRemoving](/docs/reference/engine/classes/Instance#DescendantRemoving)  fire on its parent  or ancestor , but the instance itself is not destroyed in the same sense as an [Instance:Destroy()](/docs/reference/engine/classes/Instance#Destroy)  call. Local-only changes to instance properties (changes that exist on a client and have not been replicated to the server) can be lost if the instances streams out and later streams back in.

### [Assemblies](#assemblies)[](#assemblies)

Physical [assemblies](/docs/physics/assemblies)  stream in  as complete units, including their associated [Constraints](/docs/reference/engine/classes/Constraint)  and [Attachments](/docs/reference/engine/classes/Attachment) , helping to ensure consistent physics updates on clients. The only exception is when the assembly is [anchored](/docs/physics/assemblies#anchoring-behavior) , in which case only the [BaseParts](/docs/reference/engine/classes/BasePart)  within the streaming radius are streamed in alongside their associated [Constraints](/docs/reference/engine/classes/Constraint)  and [Attachments](/docs/reference/engine/classes/Attachment) .

Assemblies do not stream out  until all of their [BaseParts](/docs/reference/engine/classes/BasePart)  are eligible to stream out.

Avoid creating moving assemblies with unnecessarily large numbers of instances, as all of the instances streaming in unison may cause network/CPU spikes.

## [Streaming properties](#streaming-properties)[](#streaming-properties)

The following properties control how instance streaming applies to your game. All of these properties are non-scriptable  and must be set on the [Workspace](/docs/reference/engine/classes/Workspace)  object in Studio.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Workspace-Streaming.png)

| Property | | Description |
| --- | --- |
| [EnableSLIMAvatars](/docs/reference/engine/classes/Workspace#EnableSLIMAvatars) | | Controls whether a [SLIM](/docs/workspace/streaming/slim#enabling-slim-for-avatars)  model is generated for avatar characters in the game. When enabled, avatars render using SLIM in the same way that setting [Model.LevelOfDetail](/docs/reference/engine/classes/Model#LevelOfDetail)  to [SLIM](/docs/reference/engine/enums/ModelLevelOfDetail#SLIM)  works for other models. See [SLIM](/docs/workspace/streaming/slim)  for details. |
| [ModelStreamingBehavior](/docs/reference/engine/classes/Workspace#ModelStreamingBehavior) | | Controls how [Nonatomic](#nonatomic)  (default) models stream in and out.

RECOMMENDED

 Use [Improved](/docs/reference/engine/enums/ModelStreamingBehavior#Improved)  to enable the most efficient streaming for [Models](/docs/reference/engine/classes/Model)  with [BasePart](/docs/reference/engine/classes/BasePart)  descendants. |
| [PredictiveStreamingMode](/docs/reference/engine/classes/Workspace#PredictiveStreamingMode) | | Opts in to [predictive streaming](#predictive-streaming)  which uses engine signals to proactively stream areas a player is likely to need soon, such as respawn locations or regions the player recently left via [CFrame](/docs/reference/engine/datatypes/CFrame)  change. Predictions are additive, expire after a short time if unused, and are skipped on resource‑constrained clients. |
| [StreamingIntegrityMode](/docs/reference/engine/classes/Workspace#StreamingIntegrityMode) | | The game may behave in unintended ways if a player moves into a region of the world that hasn't been streamed to them. This property offers a way to avoid those potentially problematic situations.

RECOMMENDED

 Use [PauseOutsideLoadedArea](/docs/reference/engine/enums/StreamingIntegrityMode#PauseOutsideLoadedArea)  to balance gameplay integrity without pausing unnecessarily or too often. You can also [customize the pause screen](#pause-screen-customization) . |
| [StreamingMinRadius](/docs/reference/engine/classes/Workspace#StreamingMinRadius) | | This property indicates the radius around the [replication foci](#replication-focus)  in which instances stream in at the highest priority. Care should be taken when increasing the default, as doing so will require more memory and more server bandwidth at the expense of other components.

RECOMMENDED

 Use the default of 64  to maximize how much the engine can scale the game down for low‑end devices. |
| [StreamingTargetRadius](/docs/reference/engine/classes/Workspace#StreamingTargetRadius) | | This property controls the maximum distance away from the [replication foci](#replication-focus)  in which instances stream in. Note that the engine is allowed to retain previously loaded instances beyond the target radius, memory permitting.
A smaller [StreamingTargetRadius](/docs/reference/engine/classes/Workspace#StreamingTargetRadius)  reduces server workload, as the server will not stream in additional instances beyond the set value. However, the target radius is also the maximum distance players will be able to see the full detail of your game, so you should pick a value that creates a nice balance between these.

RECOMMENDED

 Use the default of 1024  to strike a good balance between visibility for players on high‑end devices and a reasonable memory footprint. |
| [StreamOutBehavior](/docs/reference/engine/classes/Workspace#StreamOutBehavior) | | This property sets the [streaming out](#stream-out)  behavior according to the value of [Enum.StreamOutBehavior](/docs/reference/engine/enums/StreamOutBehavior) . If set to [LowMemory](/docs/reference/engine/enums/StreamOutBehavior#LowMemory)  (default), the client only streams out regions beyond the minimum radius in a low memory situation. If set to [Opportunistic](/docs/reference/engine/enums/StreamOutBehavior#Opportunistic) , regions beyond [StreamingTargetRadius](/docs/reference/engine/classes/Workspace#StreamingTargetRadius)  can be removed on the client even when there is no memory pressure (in this mode, the client never removes instances that are within the target radius, except in low memory situations).

RECOMMENDED

 Use [Opportunistic](/docs/reference/engine/enums/StreamOutBehavior#Opportunistic)  to allow the client to aggressively garbage collect content, significantly reducing memory usage and helping prevent out‑of‑memory crashes. |

[StreamingTargetRadius](/docs/reference/engine/classes/Workspace#StreamingTargetRadius)  should be larger than [StreamingMinRadius](/docs/reference/engine/classes/Workspace#StreamingMinRadius) . 3D content between the target radius and the minimum radius acts as a buffer in case the client temporarily stops receiving new content from the server. If the minimum radius and the target radius are equal, there is no buffer, which can lead to an increase in network pauses or an otherwise suboptimal player experience.

## [Replication focus](#replication-focus)[](#replication-focus)

By default, streaming occurs around the local player's character's [PrimaryPart](/docs/reference/engine/classes/Model#PrimaryPart) , although you can specify a different replication focus point through [Player.ReplicationFocus](/docs/reference/engine/classes/Player#ReplicationFocus) .

You can also add and remove additional replication foci through [Player:AddReplicationFocus()](/docs/reference/engine/classes/Player#AddReplicationFocus)  and [Player:RemoveReplicationFocus()](/docs/reference/engine/classes/Player#RemoveReplicationFocus)  to dynamically enable streaming in multiple areas of the game.

Use caution when adding additional replication foci as each additional focus increases the server's workload for streaming and updating regions. For example, a single player with nine dynamically moving foci could generate server networking and streaming processing comparable to ten players moving around the game.

On the client, too many foci for a player can limit the engine's ability to adjust to memory limitations and make it more likely for clients to be killed by the OS for using too much memory.

Physics Simulation Movement Between Zones Distant Viewpoints

Client-side physics simulation, including prediction and resimulations when [server authority](/docs/projects/server-authority)  is implemented, only occurs in streamed areas, even for locally created instances and for [Persistent](/docs/reference/engine/enums/ModelStreamingMode#Persistent)  instances. If you have instances that you'd like to keep simulating even when they're far away from the character, create an additional replication focus near those instances.

## [Predictive streaming](#predictive-streaming)[](#predictive-streaming)

Predictive streaming is an opt‑in feature that uses engine signals to anticipate player movement and proactively stream areas the player is likely to need soon. When enabled by setting [PredictiveStreamingMode](/docs/reference/engine/classes/Workspace#PredictiveStreamingMode)  to [Enabled](/docs/reference/engine/enums/PredictiveStreamingMode#Enabled) , it can reduce streaming pauses and visual pop‑in without any code changes.

Predictive streaming is additive . It creates small, temporary streaming foci in addition to your existing [replication foci](#replication-focus) , streams a small amount of extra content, and does not change your game logic or streaming contracts. If a prediction isn't needed, the predicted area expires after a short time and the engine unloads the content. The engine also takes client memory and performance into account, skipping predictions on resource‑constrained devices.

When [PredictiveStreamingMode](/docs/reference/engine/classes/Workspace#PredictiveStreamingMode)  is [Enabled](/docs/reference/engine/enums/PredictiveStreamingMode#Enabled) , the following predictive features are active:

| Feature | | Description |
| Spawn pre‑fetching | | When a player dies, the engine creates small, temporary streaming foci at possible spawn locations so that likely respawn areas begin streaming before the player character appears, reducing pauses and missing content immediately after respawn. |
| [CFrame](/docs/reference/engine/datatypes/CFrame)  return optimization | | When a player [CFrames](/docs/reference/engine/datatypes/CFrame)  away from an area, the engine creates a small, temporary streaming focus at the location they left. This helps keep that area streamed in if the player returns shortly after, a common scenario when moving between buildings, sublevels, shops, or hubs. |

Predictive streaming works seamlessly with manually created pre‑fetches ([Player:RequestStreamAroundAsync()](/docs/reference/engine/classes/Player#RequestStreamAroundAsync) ) and multiple replication foci ([Player:AddReplicationFocus()](/docs/reference/engine/classes/Player#AddReplicationFocus) ). If you've already created a pre‑fetch or replication focus at a specific location, predictive streaming does not add another streaming focus there.

## [Model streaming controls](#model-streaming-controls)[](#model-streaming-controls)

To avoid issues with streaming on a per-model basis and minimize use of [WaitForChild()](/docs/reference/engine/classes/Instance#WaitForChild) , you can customize how [Models](/docs/reference/engine/classes/Model)  and their descendants stream through their [ModelStreamingMode](/docs/reference/engine/classes/Model#ModelStreamingMode)  property.

### [Nonatomic](#nonatomic)[](#nonatomic)

By default, models are [Nonatomic](/docs/reference/engine/enums/ModelStreamingMode#Nonatomic)  and they stream in/out based on whether [Workspace.ModelStreamingBehavior](/docs/reference/engine/classes/Workspace#ModelStreamingBehavior)  is set to [Legacy](/docs/reference/engine/enums/ModelStreamingBehavior#Legacy)  (default) or [Improved](/docs/reference/engine/enums/ModelStreamingBehavior#Improved) .

###### Legacy

When [Workspace.ModelStreamingBehavior](/docs/reference/engine/classes/Workspace#ModelStreamingBehavior)  is set to [Legacy](/docs/reference/engine/enums/ModelStreamingBehavior#Legacy)  (default), the [Model](/docs/reference/engine/classes/Model)  container and its non ‑[BasePart](/docs/reference/engine/classes/BasePart)  descendants such as [Scripts](/docs/reference/engine/classes/Script)  replicate to the client when the player joins. Then, when eligible, the model's [BasePart](/docs/reference/engine/classes/BasePart)  descendants stream in.

 ![](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/Model-Stream-In-Default.png)

###### Improved

When [Workspace.ModelStreamingBehavior](/docs/reference/engine/classes/Workspace#ModelStreamingBehavior)  is set to [Improved](/docs/reference/engine/enums/ModelStreamingBehavior#Improved) , model streaming behavior varies by whether the model contains [BasePart](/docs/reference/engine/classes/BasePart)  descendants or does not  contain [BasePart](/docs/reference/engine/classes/BasePart)  descendants:

-

A model with [BasePart](/docs/reference/engine/classes/BasePart)  descendants streams in  only when one  of its [BasePart](/docs/reference/engine/classes/BasePart)  descendants is eligible to stream in. At that point, the model and the eligible [BasePart](/docs/reference/engine/classes/BasePart)  streams in, along with the model's non ‑[BasePart](/docs/reference/engine/classes/BasePart)  descendants.

When the very last remaining [BasePart](/docs/reference/engine/classes/BasePart)  of the model streams out , the model itself will stream out along with it.

 ![](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/Model-Stream-In-Improved-Spatial.png)

-

A model with no [BasePart](/docs/reference/engine/classes/BasePart)  descendants, such as one used merely as a "container" for non‑[BasePart](/docs/reference/engine/classes/BasePart)  instances like scripts, replicates to the client soon after the player joins. This type of model is exempt  from streaming out unless  it is made a descendant of a [BasePart](/docs/reference/engine/classes/BasePart) .

 ![](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/Model-Stream-In-Improved-Non-Spatial.png)

### [Atomic](#atomic)[](#atomic)

If a [Model](/docs/reference/engine/classes/Model)  is set to [Atomic](/docs/reference/engine/enums/ModelStreamingMode#Atomic) , all of its initial descendants are streamed in together when a descendant [BasePart](/docs/reference/engine/classes/BasePart)  is eligible to be streamed in. As a result, a client‑side script that needs to access instances inside  the model would need to use [WaitForChild()](/docs/reference/engine/classes/Instance#WaitForChild)  on the model itself, but not on a descendant [MeshPart](/docs/reference/engine/classes/MeshPart)  or [Part](/docs/reference/engine/classes/Part)  since they are sent alongside the model.

An atomic model is only streamed out when all of its descendant parts are eligible for streaming out, at which point the entire model streams out together.

 ![A diagram showing Atomic model streaming along with children.](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/Model-Streaming-Mode-Atomic.png)

### [Persistent](#persistent)[](#persistent)

[Persistent](/docs/reference/engine/enums/ModelStreamingMode#Persistent)  models are not subject to normal streaming in or out. They are sent as a complete atomic unit soon after the player joins and before the [Workspace.PersistentLoaded](/docs/reference/engine/classes/Workspace#PersistentLoaded)  event fires. Persistent models and their descendants are never streamed out, but to safely handle streaming in within a client‑side script, you should wait for the [PersistentLoaded](/docs/reference/engine/classes/Workspace#PersistentLoaded)  event to fire.

 ![A diagram showing Persistent model streaming along with children.](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/Model-Streaming-Mode-Persistent.png)

Persistent models are intended for very rare circumstances, such as when a small number of parts must always be present on clients for client‑side scripts to access. If possible, server-side [Scripts](/docs/reference/engine/classes/Script)  should be used, or client scripts should be tolerant of parts streaming in and out. Persistent models are not  intended to circumvent streaming, and overuse may negatively impact performance.

### [PersistentPerPlayer](#persistentperplayer)[](#persistentperplayer)

Models set to [PersistentPerPlayer](/docs/reference/engine/enums/ModelStreamingMode#PersistentPerPlayer)  behave the same as [Persistent](/docs/reference/engine/enums/ModelStreamingMode#Persistent)  for players that have been added using [Model:AddPersistentPlayer()](/docs/reference/engine/classes/Model#AddPersistentPlayer) . For other players, behavior is the same as [Atomic](/docs/reference/engine/enums/ModelStreamingMode#Atomic) . You can revert a model from player persistence via [Model:RemovePersistentPlayer()](/docs/reference/engine/classes/Model#RemovePersistentPlayer) .

## [Pause screen customization](#pause-screen-customization)[](#pause-screen-customization)

Assuming [Workspace.StreamingIntegrityMode](/docs/reference/engine/classes/Workspace#StreamingIntegrityMode)  is set to the recommended [PauseOutsideLoadedArea](/docs/reference/engine/enums/StreamingIntegrityMode#PauseOutsideLoadedArea) , the game will pause if a player moves into a region of the world that hasn't been streamed to them. In these cases, the [Player.GameplayPaused](/docs/reference/engine/classes/Player#GameplayPaused)  property indicates the player's current pause state which can be used with a [GetPropertyChangedSignal()](/docs/reference/engine/classes/Instance#GetPropertyChangedSignal)  connection to show or hide a custom GUI.

LocalScript

```

local Players = game:GetService("Players")

local GuiService = game:GetService("GuiService")

local player = Players.LocalPlayer

-- Disable default pause modal

GuiService:SetGameplayPausedNotificationEnabled(false)

local function onPauseStateChanged()

	if player.GameplayPaused then

		-- Show custom GUI

	else

		-- Hide custom GUI

	end

end

player:GetPropertyChangedSignal("GameplayPaused"):Connect(onPauseStateChanged)

```

## [Runtime debugging](#runtime-debugging)[](#runtime-debugging)

The engine includes multiple on-screen debug panels that can be enabled on the client using keyboard shortcuts. To access streaming debug information:

1.

Open the Network Stats  debug overlay. In a live experience, press Shift F3 . When playtesting in Studio, press Shift Ctrl F3  (Windows) or Shift ⌘ F3  (Mac).

2.

Once the debug overlay is open, press Shift 1  repeatedly to cycle through the available panels. The fourth panel is the Streaming  debug view which displays useful runtime information:

-

Active streaming settings

-

Currently loaded (streamed in) regions

-

Streaming behavior and state

Once enabled, colored highlighted regions appear in the 3D viewport:

| Color | | Description |
|  | | Less than [StreamingMinRadius](/docs/reference/engine/classes/Workspace#StreamingMinRadius) |
|  | | Greater than or equal to [StreamingMinRadius](/docs/reference/engine/classes/Workspace#StreamingMinRadius)  and less than [StreamingTargetRadius](/docs/reference/engine/classes/Workspace#StreamingTargetRadius) |
|  | | Equal to [StreamingTargetRadius](/docs/reference/engine/classes/Workspace#StreamingTargetRadius) |
|  | | Greater than [StreamingTargetRadius](/docs/reference/engine/classes/Workspace#StreamingTargetRadius) |

To increase the ability to zoom the default camera considerably far out while debugging, temporarily increase [StarterPlayer.CameraMaxZoomDistance](/docs/reference/engine/classes/StarterPlayer#CameraMaxZoomDistance)  while in edit mode or [Player.CameraMaxZoomDistance](/docs/reference/engine/classes/Player#CameraMaxZoomDistance)  during runtime. A value of 1000 , for example, allows you to pull the camera out to view most of the 3D world while still navigating the character around.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
