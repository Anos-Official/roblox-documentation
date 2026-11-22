<!-- Source: https://create.roblox.com/docs/scripting/events/bindable -->

Bindable events and callbacks | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/scripting/events/bindable.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Scripting](/docs/scripting)
6. /
7. [Events](/docs/scripting/events)

# Bindable events and callbacks

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/scripting/events/bindable.md)

[BindableEvent](/docs/reference/engine/classes/BindableEvent)  and [BindableFunction](/docs/reference/engine/classes/BindableFunction)  objects let you bind behaviors between scripts on the same side  of the [client-server](/docs/projects/client-server)  boundary and communicate a specific desired outcome for in-game actions.

The most common use case for bindable events is for games that have a round-based structure. For example, you might have a "match started" event that lets other scripts start a timer and display a leaderboard, with a corresponding "match ended" event that lets other scripts know when to move players back into a lobby and display the winners.

Because they coordinate activities between scripts, bindable events are typically used on the server, but you can use them on the client, too.

Depending on how your game works, bindable events can help make your code more modular, but [module scripts](/docs/scripting/module)  are often a better alternative for situations in which you need to share data between scripts. You can also use bindable events in conjunction with module scripts for a cleaner syntax, as noted in [Custom events](/docs/scripting/module#custom-events) .

To communicate between scripts across  the client-server boundary, see [Remote events](/docs/scripting/events/remote) .

## [Bindable events](#bindable-events)[](#bindable-events)

The [BindableEvent](/docs/reference/engine/classes/BindableEvent)  object enables custom events through asynchronous, one-way communication between scripts.

When you fire a [BindableEvent](/docs/reference/engine/classes/BindableEvent)  through the [Fire()](/docs/reference/engine/classes/BindableEvent#Fire)  method, the firing script does not  yield, and the target function receives the passed arguments with certain [limitations](#argument-limitations) . Like all events, [BindableEvents](/docs/reference/engine/classes/BindableEvent)  create threads of each connected function, so even if one errors, others continue.

To create a new [BindableEvent](/docs/reference/engine/classes/BindableEvent)  using the [Explorer](/docs/studio/explorer)  window in Studio:

1.

Hover over the container into which you want to insert the [BindableEvent](/docs/reference/engine/classes/BindableEvent) . We recommend using [ServerScriptService](/docs/reference/engine/classes/ServerScriptService)  for communication between server scripts and [ReplicatedStorage](/docs/reference/engine/classes/ReplicatedStorage)  for communication between client scripts.

2.

Click the ⊕  button that appears to the right of the container's name and insert a BindableEvent  instance.

3.

Rename the instance to TestBindableEvent .

After you've created a [BindableEvent](/docs/reference/engine/classes/BindableEvent) , connect a function to its [Event](/docs/reference/engine/classes/BindableEvent#Event)  event in one script, and then [Fire()](/docs/reference/engine/classes/BindableEvent#Fire)  the event from another script.

Event Connection

```

local ServerScriptService = game:GetService("ServerScriptService")

-- Get reference to bindable event instance

local bindableEvent = ServerScriptService:WaitForChild("TestBindableEvent")

-- Connect anonymous function to event

bindableEvent.Event:Connect(function(data)

	print(data)  --> Round started!

end)

```

Event Firing

```

local ServerScriptService = game:GetService("ServerScriptService")

-- Get reference to bindable event instance

local bindableEvent = ServerScriptService:WaitForChild("TestBindableEvent")

-- Fire bindable event

bindableEvent:Fire("Round started!")

```

You can connect multiple functions to the same [BindableEvent](/docs/reference/engine/classes/BindableEvent) , but Luau executes them in an unpredictable order. To ensure that functions execute in a particular order, combine them into a single function and connect it to the event.

## [Custom callbacks](#custom-callbacks)[](#custom-callbacks)

The [BindableFunction](/docs/reference/engine/classes/BindableFunction)  object allows for synchronous, two-way communication between scripts. You can use it to define a custom callback function and invoke it manually by calling [BindableFunction:Invoke()](/docs/reference/engine/classes/BindableFunction#Invoke) . The code invoking the function yields  until the corresponding callback is found, and the callback receives the arguments that you passed to [Invoke()](/docs/reference/engine/classes/BindableFunction#Invoke) . If the callback was never set, the script that invokes it doesn't resume execution.

To create a new [BindableFunction](/docs/reference/engine/classes/BindableFunction)  using the [Explorer](/docs/studio/explorer)  window in Studio:

1.

Hover over the container into which you want to insert the [BindableFunction](/docs/reference/engine/classes/BindableFunction) . We recommend using [ServerScriptService](/docs/reference/engine/classes/ServerScriptService)  for communication between server scripts and [ReplicatedStorage](/docs/reference/engine/classes/ReplicatedStorage)  for communication between client scripts.

2.

Click the ⊕  button that appears to the right of the container's name and insert a BindableFunction  instance.

3.

Rename the instance to TestBindableFunction .

Once you've created a [BindableFunction](/docs/reference/engine/classes/BindableFunction) , you can connect to its [OnInvoke](/docs/reference/engine/classes/BindableFunction#OnInvoke)  callback in one script, then [Invoke()](/docs/reference/engine/classes/BindableFunction#Invoke)  the callback function from another script.

Callback Connection

```

local ServerScriptService = game:GetService("ServerScriptService")

-- Get reference to bindable function

local bindableFunction = ServerScriptService:WaitForChild("TestBindableFunction")

-- Callback function

local function addTwoNumbers(a, b)

	return a + b

end

-- Set function as bindable function's callback

bindableFunction.OnInvoke = addTwoNumbers

```

Event Invocation

```

local ServerScriptService = game:GetService("ServerScriptService")

-- Get reference to bindable function

local bindableFunction = ServerScriptService:WaitForChild("TestBindableFunction")

-- Invoke callback function and output returned value

local sum = bindableFunction:Invoke(2, 4)

print(sum)  --> 6

```

Each [BindableFunction](/docs/reference/engine/classes/BindableFunction)  can only utilize one [OnInvoke](/docs/reference/engine/classes/BindableFunction#OnInvoke)  callback. If you make multiple definitions, only the last one assigned runs. Also note that if the [OnInvoke](/docs/reference/engine/classes/BindableFunction#OnInvoke)  callback does not have a return  statement, the invocation returns nil .

## [Argument limitations](#argument-limitations)[](#argument-limitations)

When you fire a [BindableEvent](/docs/reference/engine/classes/BindableEvent)  or invoke a [BindableFunction](/docs/reference/engine/classes/BindableFunction) , it forwards any arguments that you pass with the event or to the callback function. You can pass any type of Roblox object ([Enum](/docs/reference/engine/datatypes/Enum) , [Instance](/docs/reference/engine/classes/Instance) , etc.), as well as Luau types like numbers, strings, and booleans, although you should carefully consider the following limitations.

### [Non-string indices](#non-string-indices)[](#non-string-indices)

If any indices  of a passed table are non-string types, such as an [Instance](/docs/reference/engine/classes/Instance) , [userdata](/docs/luau/userdata) , or [function](/docs/luau/functions) , Roblox automatically converts those indices to strings.

Event Connection

```

local ServerScriptService = game:GetService("ServerScriptService")

local bindableEvent = ServerScriptService:WaitForChild("TestBindableEvent")

local function onEventFire(passedTable)

	for k, v in passedTable do

		print(typeof(k))  --> string

	end

end

-- Connect function to event

bindableEvent.Event:Connect(onEventFire)

```

Event Firing

```

local ServerScriptService = game:GetService("ServerScriptService")

local bindableEvent = ServerScriptService:WaitForChild("TestBindableEvent")

-- Fire event with table containing a workspace instance as a key

bindableEvent:Fire({

	[workspace.Baseplate] = true

})

```

### [Table indexing](#table-indexing)[](#table-indexing)

If you pass a table of data, do not pass a mixed table of numeric and string keys. Doing so can result in removed elements during the transfer. Instead, pass a table that consists entirely  of key-value pairs (a dictionary) or entirely  of numeric indices (an array).

In both cases, whether passing a dictionary table or a numerically indexed table, avoid nil  values for any index.

Event Connection

```

local ServerScriptService = game:GetService("ServerScriptService")

local bindableEvent = ServerScriptService:WaitForChild("TestBindableEvent")

local function onEventFire(passedTable)

	for k, v in passedTable do

		print(k .. " = " .. v)

		--> 1 = Sword

		--> 2 = Bow

		--> CharName = Diva Dragonslayer

		--> CharClass = Rogue

	end

end

-- Connect function to event

bindableEvent.Event:Connect(onEventFire)

```

Event Firing

```

local ServerScriptService = game:GetService("ServerScriptService")

local bindableEvent = ServerScriptService:WaitForChild("TestBindableEvent")

-- Numerically indexed table

local inventoryData = {

	"Sword", "Bow"

}

-- Dictionary table

local characterData = {

	CharName = "Diva Dragonslayer",

	CharClass = "Rogue"

}

-- Fire event with consistently-indexed tables

bindableEvent:Fire(inventoryData)

bindableEvent:Fire(characterData)

```

### [Table identities](#table-identities)[](#table-identities)

Tables passed as arguments to bindable events and callbacks are copied, meaning they will not be exactly equivalent to those provided when firing the event or invoking the callback. Nor will tables returned to the invoker be exactly equivalent to those provided. You can demonstrate this by running the following script on a [BindableFunction](/docs/reference/engine/classes/BindableFunction)  and observing how the table identities differ.

Callback Connection

```

local ServerScriptService = game:GetService("ServerScriptService")

local bindableFunction = ServerScriptService:WaitForChild("TestBindableFunction")

-- Callback function

local function returnTable(passedTable)

	-- Output table identity on invocation

	print(tostring(passedTable))  --> table: 0x48eb7aead27563d9

	return passedTable

end

-- Set function as bindable function's callback

bindableFunction.OnInvoke = returnTable

```

Event Invocation

```

local ServerScriptService = game:GetService("ServerScriptService")

local bindableFunction = ServerScriptService:WaitForChild("TestBindableFunction")

local inventoryData = {

	"Sword", "Bow"

}

-- Output original table identity

print(tostring(inventoryData))  --> table: 0x059bcdbb2b576549

local invokeReturn = bindableFunction:Invoke(inventoryData)

-- Output table identity upon return

print(tostring(invokeReturn))  --> table: 0x9fcae7919563a0e9

```

### [Metatables](#metatables)[](#metatables)

If a table has a metatable, all of the metatable information is lost in the transfer. In the following code sample, the NumWheels  property is part of the Car  metatable. When the server receives the following table, the truck  table has the Name  property but not  the NumWheels  property.

Event Connection

```

local ServerScriptService = game:GetService("ServerScriptService")

local bindableEvent = ServerScriptService:WaitForChild("TestBindableEvent")

local function onEvent(param)

	print(param)  --> {["Name"] = "MyTruck"}

end

-- Connect function to event

bindableEvent.Event:Connect(onEvent)

```

Event Firing

```

local ServerScriptService = game:GetService("ServerScriptService")

local bindableEvent = ServerScriptService:WaitForChild("TestBindableEvent")

local Car = {}

Car.NumWheels = 4

Car.__index = Car

local truck = {}

truck.Name = "MyTruck"

setmetatable(truck, Car)

-- Fire event with table including a metatable

bindableEvent:Fire(truck)

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
