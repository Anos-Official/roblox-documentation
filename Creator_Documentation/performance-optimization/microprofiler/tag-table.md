<!-- Source: https://create.roblox.com/docs/en-us/performance-optimization/microprofiler/tag-table -->

Tag reference | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/performance-optimization/microprofiler/tag-table.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Performance optimization](/docs/en-us/performance-optimization)
6. /
7. [MicroProfiler](/docs/en-us/performance-optimization/microprofiler)

# Tag reference

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/performance-optimization/microprofiler/tag-table.md)

The following is a list of common tags in the [MicroProfiler](/docs/en-us/performance-optimization/microprofiler) , grouped by category. Tags are also interchangeably called tasks, timers, scopes, processes, and labels. Whatever the name, they represent a unit of work.

Understanding these tags can help you identify problematic code in your game. The tables contain tag label, descriptions, and advice for improving performance and optimizing your game.

For a complete list of all MicroProfiler tags and their descriptions, see the [LibMP documentation](https://github.com/Roblox/libmp/blob/main/docs/ALL-SCOPES%2Emd)  on GitHub.

## [Sleep](#sleep)[](#sleep)

When threads aren't actively performing tasks, they enter a sleep state, with tags to indicate how long the thread was sleeping. At any given time, it's extremely common for most worker threads to be in a sleep state.

## [Navigation](#navigation)[](#navigation)

| Label | | Description | | Performance advice |
| --- | --- |
| rasterizeTile | | Updates navigation tiles needed for a pathfinding request, usually followed by computePath  which requires those tiles be up-to-date. Follows NavigationJob/preprocess  on the main thread. | | Reduce the number of pathfinding tile invalidations, as this causes those paths to need recomputing. This is caused by non-navigable parts moving. |
| computePath | |

Calculates paths, typically after rasterizeTile .

 | | Reduce the number and world extents of [Path:ComputeAsync()](/docs/en-us/reference/engine/classes/Path#ComputeAsync)  calls. Try reusing paths for multiple agents if they are expected to start/end from approximately similar locations. |
| preprocess/getPrimitivesOverlapping | | Collects the world geometry for each pathfinding tile and schedules the rasterization tasks to be executed by the pathfinding thread. | | Reduce the part count. |

## [Animation and humanoids](#animation-and-humanoids)[](#animation-and-humanoids)

| Label | | Description | | Performance advice |
| Simulation/gameStepped | | Processing of game-specific objects such as [Humanoids](/docs/en-us/reference/engine/classes/Humanoid) , [Animations](/docs/en-us/reference/engine/classes/Animation)  and heartbeat callbacks. | | See gameStepped  labels below. |
| Simulation/gameStepped/stepHumanoid | | [Humanoid](/docs/en-us/reference/engine/classes/Humanoid)  state changes and movement. | | Reduce the amount of [Humanoids](/docs/en-us/reference/engine/classes/Humanoid)  or disable [Humanoid](/docs/en-us/reference/engine/classes/Humanoid)  states on NPCs that don't need them, such as [Climbing](/docs/en-us/reference/engine/enums/HumanoidStateType)  or [Swimming](/docs/en-us/reference/engine/enums/HumanoidStateType) . Reduce callbacks to [Humanoid.StateChanged](/docs/en-us/reference/engine/classes/Humanoid#StateChanged)  or state changes such as [Running](/docs/en-us/reference/engine/classes/Humanoid#Running)  or [Died](/docs/en-us/reference/engine/classes/Humanoid#Died) . |
| Simulation/gameStepped/stepAnimation | | [Animators](/docs/en-us/reference/engine/classes/Animator)  will step forward in currently playing animations. | | Reduce the amount of [Animators](/docs/en-us/reference/engine/classes/Animator)  or animated joints to lower the workload of this step. Reduce number of callbacks to animation events such as [AnimationTrack.KeyframeReached](/docs/en-us/reference/engine/classes/AnimationTrack#KeyframeReached)  or [AnimationTrack.Ended](/docs/en-us/reference/engine/classes/AnimationTrack#Ended) |
| Simulation/gameStepped/RunService.Stepped | | Runs functions connected to the [RunService.Stepped](/docs/en-us/reference/engine/classes/RunService#Stepped)  event. | | Reduce the amount or workload of functions connected to this event. Consider delaying or replacing expensive calculations or spreading computation across multiple frames. |

## [Audio](#audio)[](#audio)

| Label | | Description | | Performance advice |
| Sound | | Processes acoustic simulation and updates sounds in active playback. | | See Sound  labels below. |
| Sound/stepInstances | | Updates the volume of active sounds in the workspace. | | Reduce the amount of sounds in active playback. |

## [Networking](#networking)[](#networking)

| Label | | Description | | Performance advice |
| Net PacketReceive | | Receives network packets. If many objects or events are being replicated, this step takes longer.  | | Replicate fewer objects or events. |
| Replicator/ProcessPackets | | Processes contents of network packets, such as motion, event invocations and property changes.  | | Reduce the number or size of objects being replicated, or do this in incremental steps. May increase if map size increases, as larger maps tend to have more overall activity. |
| Allocate Bandwidth and Run Senders/Dispatch Physics Senders and TouchSenders | | Sends data about activity in the game. | | Reduce the amount of moving objects and/or touches. See following sections. |
| Allocate Bandwidth and Run Senders/Dispatch StreamJob | | Sends corresponding specific regions to specific clients in the streaming feature. | | Reduce the minimum and target streaming radii. |
| Allocate Bandwidth and Run Senders/Dispatch Data Senders | | Sends property changes, remote event invocations, [Humanoid](/docs/en-us/reference/engine/classes/Humanoid)  state changes, animation state changes, and replication of new instances. | | Reduce the number of replicated changes to the data model. |
| Replicator SendCluster | | Sends [Terrain](/docs/en-us/parts/terrain)  data to clients. | | Reduce the amount or size of terrain changes. |
| ModelCompleteness Mega Job | | Server only: completeness is an internal concept. When models are completely sent, model completeness events are sent. | | Add or remove fewer instances. |
| deserializePacket | | Low-level network packet processing. Prepares for Replicator/ProcessPackets . | | Send fewer or smaller updates. |

## [Rendering](#rendering)[](#rendering)

| Label | | Description | | Performance advice |
| Prepare | | Information is gathered from the main thread and updates various data structures used for rendering. | | See Prepare  labels below. |
| Prepare/Pass3dAdorn | | Handles rendering of various object adorns, such as text labels above objects. For [Humanoid](/docs/en-us/reference/engine/classes/Humanoid)  labels with occlusion, this step includes raycasting to determine if such objects are visible. This includes non-transparent parts to facilitate debug visualizations. | | Reduce the number of visible adorned objects, such as [BillboardGuis](/docs/en-us/reference/engine/classes/BillboardGui) , [Humanoid](/docs/en-us/reference/engine/classes/Humanoid)  name/health labels, etc. Reduce the number of visible parts. |
| Prepare/Pass2d | | Readies 2D UI rendering (both player and Roblox UI). | | Reduce the amount or complexity of UI elements. |
| Prepare/UpdatePrepare/updateInvalidParts | | Updates parts that had some property changed or added. | | Reduce the amount of properties changes on the world. If a script updates a large set of object properties, break it down across frames. |
| Prepare/UpdatePrepare/updateInvalidatedFastClusters | | Prepares "FastCluster" geometries used to render [Humanoids](/docs/en-us/reference/engine/classes/Humanoid)  and [skinned](/docs/en-us/art/modeling/rigging)  [MeshParts](/docs/en-us/reference/engine/classes/MeshPart) . Labels specify the number of parts, vertices, and size of vertices. | | Reduce visual changes to models with [Humanoids](/docs/en-us/reference/engine/classes/Humanoid)  or skinned [MeshParts](/docs/en-us/reference/engine/classes/MeshPart) . |
| Prepare/UpdatePrepare/updateDynamicParts | | Prepares [Beams](/docs/en-us/reference/engine/classes/Beam) , [ParticleEmitters](/docs/en-us/reference/engine/classes/ParticleEmitter) , and [Humanoids](/docs/en-us/reference/engine/classes/Humanoid)  for rendering. | | Reduce the number of visible [Beams](/docs/en-us/reference/engine/classes/Beam) , [ParticleEmitters](/docs/en-us/reference/engine/classes/ParticleEmitter) , and [Humanoids](/docs/en-us/reference/engine/classes/Humanoid) . |
| Prepare/UpdatePrepare/updateInstancedClusters | | Updates geometry that uses instanced rendering such as parts. Labels Clusters  and Instances  indicate the number updated. | | Reduce work that implicitly updates the bounding box of the part, such as [BasePart.CFrame](/docs/en-us/reference/engine/classes/BasePart#CFrame) , [BasePart.Size](/docs/en-us/reference/engine/classes/BasePart#Size) , or [Motor6D.Transform](/docs/en-us/reference/engine/classes/Motor6D#Transform) . Creative property updates such as [Bone.Transform](/docs/en-us/reference/engine/classes/Bone#Transform)  can help. |
| Perform | | When actual rendering commands are created and issued. | | See Perform  labels below. |
| Perform/fillGuiVertices | | Fills buffers with UI vertices to prepare for rendering. gui count  label indicates the amount of [LayerCollectors](/docs/en-us/reference/engine/classes/LayerCollector)  visible in the frame. | | If the cost is high, reduce the amount, density, and space taken by UI elements. If there are too many Process GuiEffect  labels, consider reducing the use of [UIGradient](/docs/en-us/reference/engine/classes/UIGradient)  and [UICorner](/docs/en-us/reference/engine/classes/UICorner)  on text labels. |
| Perform/Scene/queryFrustumOrdered | | Applies frustum culling so that objects not visible are not rendered. | | If there is a high cost that means there are a lot of elements. Perhaps use some larger meshes where a single mesh has more details as opposed to many small individual pieces. |
| Perform/Scene/computeLightingPerform | | Computation of lighting near the camera. | | Manipulate the number of light sources or move the camera less to reduce the time it takes to recalculate lighting. |
| Perform/Scene/computeLightingPerform/LightGridCPU | | Updates the voxel lighting, which is used at lower quality levels. | | If updating chunk occupancy takes too long, consider using lower resolution geometry, reducing the number of parts, or anchoring parts. If the other labels take too long, consider reducing the number of lights and using non-shadow casting geometry for objects that move and invalidate the occupancy. |
| Perform/Scene/computeLightingPerform/ShadowMapSystem | | Updates shadow maps. Not performed at quality levels below 4. | | Reduce the number of lights. You can also use [Light.Shadows](/docs/en-us/reference/engine/classes/Light#Shadows)  and [BasePart.CastShadow](/docs/en-us/reference/engine/classes/BasePart#CastShadow)  to disable shadow casting on less important instances. See [Improve performance](/docs/en-us/performance-optimization/improve#mitigation-4) . |
| Perform/Scene/Glow, ColorCorrection, MSAA, SSAO, and SSAOApply | | Post-processing rendering. | | Reduce the number of post-processing effects. Usually this is not significant. |
| Perform/Scene/UI | | UI rendering. In Id_Screen , there is a label with the number of batches, materials and triangles used. | | Reduce the number of visible UI elements. Using [CanvasGroups](/docs/en-us/reference/engine/classes/CanvasGroup)  can help at the expense of increased memory use. |
| Perform/Scene/UpdateView/updateParticles, updateParticleBoundings | | Update particle position and bounds. | | Reduce the number of [ParticleEmitters](/docs/en-us/reference/engine/classes/ParticleEmitter) , emission rates, lifetimes, etc. Limit the movement of emitters. |
| Scene/Id_Opaque, RenderView/Id_Opaque | | Parts in the scene with an overall transparency of 0.01  or lower. | | Reduce the use and density of parts. |
| Scene/Id_Transparent, RenderView/Id_Transparent | | Parts in the scene with an overall transparency between 0.01  and 1 . | | Reduce the use of partial transparency. |
| Scene/Id_Decals, RenderView/Id_Decals | | Decals in the scene. | | Reduce the use of decals on complex meshes. |
| Scene/Shadows | | Shadow recalculation in the scene, usually performed on dynamic scenes and typical gameplay. Parts regardless of transparency cast shadows under the assumption that they contain decals. Not performed at quality levels below 4. | | If this step takes too long, consider disabling [BasePart.CastShadow](/docs/en-us/reference/engine/classes/BasePart#CastShadow)  for complex meshes, parts with high partial transparency, and less important instances. Fully transparent parts that don't have decals or need decal shadows should have [BasePart.CastShadow](/docs/en-us/reference/engine/classes/BasePart#CastShadow)  disabled. See [Improve performance](/docs/en-us/performance-optimization/improve#mitigation-4) . |
| Perform/Present | | Forwards to the GPU thread to perform rendering commands. | | Reduce scene complexity in general. If this step is taking a long time, you might be limited by the GPU. |
| Perform/Present/waitUntilCompleted | | Waits for the GPU to finish rendering the previous frame. | | If this is generally happening a lot then the amount of things rendered is too high. The Frame Rate Manager helps with balancing this, but if it remains high, try following performance advice from the individual Scene  tags. |
| LoadImage | | Processes images into a format the engine can use. | | Reduce the use of large images. |

## [Scripts](#scripts)[](#scripts)

| Label | | Description | | Performance advice |
| Render/PreRender/fireBindToRenderSteppedCallbacks | | Running functions bound to render step via [RunService:BindToRenderStep()](/docs/en-us/reference/engine/classes/RunService#BindToRenderStep) . | | Ensure functions connected to this event do as little work as possible. |
| Render/PreRender/RunService.RenderStepped | | Runs functions connected to the [RunService.RenderStepped](/docs/en-us/reference/engine/classes/RunService#RenderStepped)  event. | | Ensure functions connected to this event do as little work as possible. |
| WaitingHybridScriptJob | | Resumes scripts waiting using [Instance:WaitForChild()](/docs/en-us/reference/engine/classes/Instance#WaitForChild)  or Globals.Roblox.wait() . Usually performed 30 times per second. This step has an execution time budget to run waiting scripts. | | If you have too many waiting scripts or scripts with a long runtime before yielding, this step is throttled and waits longer before it can run again. Reduce the amount of bound functions or long computations in this step. |
| GC | | Luau's garbage collection cycle. | | Pool tables and other collectable objects or try to reduce creating temporary tables. |
| Heartbeat/RunService.Heartbeat | | Runs functions connected to the [RunService.Heartbeat](/docs/en-us/reference/engine/classes/RunService#Heartbeat)  event. | | Reduce the amount or workload of functions connected to this event. Consider delaying or replacing expensive calculations or spreading computation across multiple frames. |

## [Simulation](#simulation)[](#simulation)

| Label | | Description | | Performance advice |
| Distributed Physics Ownership | | Determines whether the server or a client has authority over certain instances such as parts. | | Reduce the amount of parts that frequently switch network ownership, especially those with common interaction. |
| Simulation/assemble | | Updates a tree of connected objects (assemblies) used by the physics engine. | | Reduce the amount of joints being created or destroyed. |
| Simulation/physicsSteppedTotal/physicsStepped | | Runs the physics simulation. | | Reduce the amount and complexity of physically simulated bodies. |
| Simulation/physicsSteppedTotal/physicsStepped/SpatialFilter/filterStep | | Updates simulation islands, arranging parts according to network ownership, local simulation. Islands are non-interacting groups of parts which can be simulated independently. | | Avoid setting network ownership frequently. Keep groups of parts far enough away from each other so they can be simulated separately. |
| Simulation/physicsSteppedTotal/physicsStepped/worldStep/stepContacts | | Updates contacts between objects. | | Reduce the amount of bodies colliding at once, or use simpler collision boxes. Cubes are better than complex meshes. |
| Simulation/physicsSteppedTotal/physicsStepped/worldStep/stepWorld OR  stepWorldThrottled | | Solves physics equations relating to connectors, buoyancy and [Humanoids](/docs/en-us/reference/engine/classes/Humanoid) . When the engine is overloaded and unable to simulate everything in real time, some steps may be throttled (stepWorldThrottled ) and only "real-time assemblies" such as [Humanoids](/docs/en-us/reference/engine/classes/Humanoid)  are simulated. | | Depends on where the time is going based on the following three phases: stepContacts : narrow phase collision detection geometry tests. Solver step : integrate time and resolve collisions and other constraints updateBroadphase : update positions of assemblies in collision detection system and find possibly colliding narrow phase pairs. |
| notifyMovingAssemblies | | Helps track how long primitives have been sleeping. | |  |
| Simulation/physicsSteppedTotal/physicsStepped/interpolateNetworkedAssemblies | | Interpolates assemblies not controlled by the current player. | | Set the network owner of parts to the current player to reduce this; although this will usually cause more physics work to be done elsewhere. |
| Simulation/handleFallenParts | | Removes parts that have fallen below [Workspace.FallenPartsDestroyHeight](/docs/en-us/reference/engine/classes/Workspace#FallenPartsDestroyHeight) . | | Lower the destroy height or reduce the amount of parts that fall to the destroy height. |
| Heartbeat/heartbeatInternal/workspaceOnHeartbeat/updateVisuallySleeping | | Second part of notifyMovingAssemblies . | |  |
| Heartbeat/RunService.Heartbeat | | Runs functions connected to the [RunService.Heartbeat](/docs/en-us/reference/engine/classes/RunService#Heartbeat)  event to simulation and scripts contacts. Current description is generic enough to be not wrong. | | Reduce the amount or workload of functions connected to [RunService.Heartbeat](/docs/en-us/reference/engine/classes/RunService#Heartbeat) . |
| worldStep/stepContacts | | Helps physics simulation step many contacts at once. | | Reduce the number of colliding objects. |
| SolveBatch | | Helps the physics simulation solve batches of objects' motion. | |  |

## [UI](#ui)[](#ui)

| Label | | Description | | Performance advice |
| Render/PreRender/UpdateInput | | Updates and fires all user input related events if the user has performed input since the last frame. | | Try and not do too much work directly as you get the input. Consider doing a minimal amount of processing for the input, and larger computations should be pushed off to another thread that happens later. |
| Render/PreRender/TweenService | | Updates objects being tweened using [TweenService](/docs/en-us/reference/engine/classes/TweenService)  and calls completion callbacks, such as those used provided to [GuiObject:TweenSize()](/docs/en-us/reference/engine/classes/GuiObject#TweenSize)  or [GuiObject:TweenPosition()](/docs/en-us/reference/engine/classes/GuiObject#TweenPosition) . | | Reduce the number of objects being tweened using [TweenService](/docs/en-us/reference/engine/classes/TweenService)  and ensure callbacks do as little work as possible. |
| Heartbeat/TweenService | | In the server, [TweenService](/docs/en-us/reference/engine/classes/TweenService)  runs in [RunService.Heartbeat](/docs/en-us/reference/engine/classes/RunService#Heartbeat)  instead of [RunService.PreRender](/docs/en-us/reference/engine/classes/RunService#PreRender) . | | Reduce the number of objects being tweened using [TweenService](/docs/en-us/reference/engine/classes/TweenService)  and ensure callbacks do as little work as possible. |
| Render/PreRender/UpdateUILayouts | | Updates position and size for UI elements on all enabled [LayerCollectors](/docs/en-us/reference/engine/classes/LayerCollector) . | | See UpdateUILayouts  labels below. |
| Render/PreRender/UpdateUILayouts/Rebuild Z-order list | | Rebuilds the internal Z-order list of UI elements (not to be confused with [GuiObject.ZIndex](/docs/en-us/reference/engine/classes/GuiObject#ZIndex) ) in a [LayerCollector](/docs/en-us/reference/engine/classes/LayerCollector)  on first render or when a new element is added, removed, or had its [GuiObject.ZIndex](/docs/en-us/reference/engine/classes/GuiObject#ZIndex)  changed. | | Reduce the number of UI elements in [LayerCollectors](/docs/en-us/reference/engine/classes/LayerCollector)  before first render and avoid frequently changing the parent and [GuiObject.ZIndex](/docs/en-us/reference/engine/classes/GuiObject#ZIndex)  of UI elements inside them. The more elements a [LayerCollector](/docs/en-us/reference/engine/classes/LayerCollector)  has, the worse it performs. |
| Render/PreRender/UpdateUILayouts/Layout | |

Updates position and size for UI elements in an individual [LayerCollector](/docs/en-us/reference/engine/classes/LayerCollector) . Can contain a label with information about the relevant UI, along with the amount of Relayouts, Updates and Resizes.

 | | Reduce the amount of UI elements being resized or repositioned, such as those managed by [UILayout](/docs/en-us/reference/engine/classes/UILayout)  and those tweened with [TweenService](/docs/en-us/reference/engine/classes/TweenService) , [GuiObject:TweenSize()](/docs/en-us/reference/engine/classes/GuiObject#TweenSize) , or [GuiObject:TweenPosition()](/docs/en-us/reference/engine/classes/GuiObject#TweenPosition) . Consider using fixed sizes for [BillboardGuis](/docs/en-us/reference/engine/classes/BillboardGui) . |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
