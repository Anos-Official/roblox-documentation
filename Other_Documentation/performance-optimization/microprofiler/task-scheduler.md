<!-- Source: https://create.roblox.com/docs/performance-optimization/microprofiler/task-scheduler -->

Task scheduler | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/performance-optimization/microprofiler/task-scheduler.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Performance optimization](/docs/performance-optimization)
6. /
7. [MicroProfiler](/docs/performance-optimization/microprofiler)

# Task scheduler

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/performance-optimization/microprofiler/task-scheduler.md)

The task scheduler  coordinates tasks done each frame as the game runs, even when it is paused. These tasks include detecting player input, animating characters, updating the physics simulation, and resuming scripts in a [task.wait()](/docs/reference/engine/libraries/task#wait)  state.

While there may be multiple tasks running, the task scheduler can potentially be overloaded, especially in the following situations:

-

Using a custom character rig or input scheme.

-

Animating parts yourself (instead of using an [Animator](/docs/reference/engine/classes/Animator) ).

-

Depending heavily on precise physics.

-

Replicating objects regularly.

## [RunService](#runservice)[](#runservice)

The most direct way to add frame-by-frame tasks is through the following members of [RunService](/docs/reference/engine/classes/RunService) :

-

[RunService.PreAnimation](/docs/reference/engine/classes/RunService#PreAnimation)

-

[RunService.PreSimulation](/docs/reference/engine/classes/RunService#PreSimulation)

-

[RunService.PostSimulation](/docs/reference/engine/classes/RunService#PostSimulation)

-

[RunService.Heartbeat](/docs/reference/engine/classes/RunService#Heartbeat)

-

[RunService:BindToRenderStep()](/docs/reference/engine/classes/RunService#BindToRenderStep)

-

[RunService.PreRender](/docs/reference/engine/classes/RunService#PreRender)

## [Scheduler priority](#scheduler-priority)[](#scheduler-priority)

The task scheduler categorizes and completes tasks in the following order. Some tasks may not perform work in a frame, while others may run multiple times.

 ![](https://prod.docsiteassets.roblox.com/assets/optimization/task-scheduler/task-scheduler.svg)

* Script execution during [RunService.Heartbeat](/docs/reference/engine/classes/RunService#Heartbeat)  differs depending on your game's [Workspace.SignalBehavior](/docs/reference/engine/classes/Workspace#SignalBehavior)  setting. See [Deferred events](/docs/scripting/events/deferred) .

## [Best practices](#best-practices)[](#best-practices)

To build performant games with efficiency in mind, note the following:

-

Don't connect/bind functions to the render step unless absolutely necessary.  Only tasks that must be done after input but before rendering should be done in such a way, like camera movement. For strict control over order, use [BindToRenderStep()](/docs/reference/engine/classes/RunService#BindToRenderStep)  instead of [PreRender](/docs/reference/engine/classes/RunService#PreRender) .

-

Manage physical states carefully.  [PreSimulation](/docs/reference/engine/classes/RunService#PreSimulation)  happens before  physics, while [PostSimulation](/docs/reference/engine/classes/RunService#PostSimulation)  happens after  physics. Therefore, gameplay logic that affects the physics state should be done in [PreSimulation](/docs/reference/engine/classes/RunService#PreSimulation) , such as setting the [Velocity](/docs/reference/engine/classes/BasePart#Velocity)  of parts. In contrast, gameplay logic that relies on or reacts to the physics state should be handled in [PostSimulation](/docs/reference/engine/classes/RunService#PostSimulation) , such as reading the [Position](/docs/reference/engine/classes/BasePart#Position)  of parts to detect when they enter defined zones.

-

Motor6D transform changes should be done on the PreSimulation event.  If you don't, [Animators](/docs/reference/engine/classes/Animator)  will overwrite changes on the next frame. Even without an [Animator](/docs/reference/engine/classes/Animator) , [PreSimulation](/docs/reference/engine/classes/RunService#PreSimulation)  is the last Luau event fired before [Motor6D.Transform](/docs/reference/engine/classes/Motor6D#Transform)  is applied to part positions.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
