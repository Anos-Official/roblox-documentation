<!-- Source: https://create.roblox.com/docs/en-us/scripting/events/deferred -->

Deferred engine events | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/scripting/events/deferred.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Scripting](/docs/en-us/scripting)
6. /
7. [Events](/docs/en-us/scripting/events)

# Deferred engine events

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/scripting/events/deferred.md)

The [Workspace.SignalBehavior](/docs/en-us/reference/engine/classes/Workspace#SignalBehavior)  property controls whether event handlers are fired immediately or deferred. The [Enum.SignalBehavior.Deferred](/docs/en-us/reference/engine/enums/SignalBehavior#Deferred)  option is recommended which helps improve the performance and correctness of the engine. The event handlers for deferred events  are resumed at the next [resumption point](#resumption-points) , along with any newly triggered event handlers.

The [Enum.SignalBehavior.Default](/docs/en-us/reference/engine/enums/SignalBehavior#Default)  value of [Workspace.SignalBehavior](/docs/en-us/reference/engine/classes/Workspace#SignalBehavior)  is currently equivalent to [Enum.SignalBehavior.Immediate](/docs/en-us/reference/engine/enums/SignalBehavior#Immediate) , but will eventually switch to being equivalent to [Enum.SignalBehavior.Deferred](/docs/en-us/reference/engine/enums/SignalBehavior#Deferred) . Template places are directly set to [Enum.SignalBehavior.Deferred](/docs/en-us/reference/engine/enums/SignalBehavior#Deferred)  by default.

The following diagram compares the [Immediate](/docs/en-us/reference/engine/enums/SignalBehavior#Immediate)  event behavior and the [Deferred](/docs/en-us/reference/engine/enums/SignalBehavior#Deferred)  event behavior.

-

With the Immediate  behavior, if an event triggers another event, the second event handler fires immediately.

-

With the Deferred  behavior, the second event is added to the back of a queue and run later.

The total time taken does not change, but the ordering is different.

 ![A comparison of three event handlers firing with Immediate and Deferred behavior](https://prod.docsiteassets.roblox.com/assets/scripting/scripts/ImmediateVsDeferredEvents.png)

"Re-entrancy" prevents events from continuously firing one another when they reach a certain depth. The current limit for this is 10.

## [Deferred event benefits](#deferred-event-benefits)[](#deferred-event-benefits)

The Immediate  behavior has some disadvantages. For every instance added to your game, property that changes, or some other trigger that is invoked, the engine needs to run Luau code before anything else happens.

-

To change 1,000 properties, 1,000 snippets of code potentially need to run after each change.

-

Strange, hard-to-diagnose bugs can occur, such as a removing event firing before something was even added.

-

Performance-critical systems can fire events requiring them to yield back and forth to Luau.

-

Event handlers can make changes to the place or trigger other events any time an event is fired.

-

An event can fire multiple times despite being redundant, such as a property changing twice.

By having specific portions of the engine life cycle in which Luau can run, the engine can gain improved performance by using a number of assumptions:

-

Performance-critical systems don't need to yield to Luau, which leads to performance gains.

-

Unless the engine itself changes it, the place never changes outside of a resumption point.

## [Resumption points](#resumption-points)[](#resumption-points)

After being deferred, an event handler is resumed at the next resumption point. Currently, the set of resumption points includes:

-

Input processing (resumes once per input to be processed, see [UserInputService](/docs/en-us/reference/engine/classes/UserInputService) )

-

[RunService.PreRender](/docs/en-us/reference/engine/classes/RunService#PreRender)

-

Legacy waiting script resumption such as wait() , spawn() , and delay()

-

[RunService.PreAnimation](/docs/en-us/reference/engine/classes/RunService#PreAnimation)

-

[RunService.PreSimulation](/docs/en-us/reference/engine/classes/RunService#PreSimulation)

-

[RunService.PostSimulation](/docs/en-us/reference/engine/classes/RunService#PostSimulation)

-

Waiting script resumption such as [task.wait()](/docs/en-us/reference/engine/libraries/task#wait) , [task.spawn()](/docs/en-us/reference/engine/libraries/task#spawn) , and [task.delay()](/docs/en-us/reference/engine/libraries/task#delay)

-

[RunService.Heartbeat](/docs/en-us/reference/engine/classes/RunService#Heartbeat)

-

[DataModel.BindToClose](/docs/en-us/reference/engine/classes/DataModel#BindToClose)

## [Common affected code patterns](#common-affected-code-patterns)[](#common-affected-code-patterns)

With remote events, the following examples either stop working correctly or have subtly different behavior; they rely on events being resumed immediately.

### [Trigger and catch events mid-execution](#trigger-and-catch-events-mid-execution)[](#trigger-and-catch-events-mid-execution)

In this example, false  is always returned when deferred events are enabled because the callback has not run. To work correctly, the thread must yield until at least when the event should have fired.

```

local success = false

event:Connect(function ()

   success = true

end)

doSomethingToTriggerEvent() -- Causes `event` to fire

return success

```

### [Listen for the first occurrence of an event](#listen-for-the-first-occurrence-of-an-event)[](#listen-for-the-first-occurrence-of-an-event)

```

connection = event:Connect(function ()

   connection:Disconnect()

   -- do something

end)

```

With deferred events enabled, multiple event handler invocations can be queued before you disconnect from the event. Calling [Disconnect()](/docs/en-us/reference/engine/classes/Instance#Disconnect)  drops all pending event handler invocations—the same behavior that exists for immediate events.

Any other method of disconnection besides [Disconnect()](/docs/en-us/reference/engine/classes/Instance#Disconnect) , such as calling [Destroy()](/docs/en-us/reference/engine/classes/Instance#Destroy)  on the [Instance](/docs/en-us/reference/engine/classes/Instance) , disconnects the signal immediately, but runs the associated event handler for any events that are still pending.

Alternatively, use [Once()](/docs/en-us/reference/engine/datatypes/RBXScriptSignal#Once)  as a more convenient method for connecting to an event that you only need the first invocation of.

### [Events that change ancestry or properties](#events-that-change-ancestry-or-properties)[](#events-that-change-ancestry-or-properties)

Deferred events cause events that handle a change in ancestry or a property to fire after the ancestry or property is changed:

```

local part = Instance.new("Part", workspace)

local function onPartDestroying()

	print("In signal:", part:GetFullName(), #part:GetChildren())

end

part.Destroying:Connect(onPartDestroying)

part:Destroy()

```

Because [Destroy()](/docs/en-us/reference/engine/classes/Instance#Destroy)  works immediately after the script that called it yields, the instance has already been destroyed by the time onPartDestroying()  is called. For more examples, see [Instance.Destroying](/docs/en-us/reference/engine/classes/Instance#Destroying) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
