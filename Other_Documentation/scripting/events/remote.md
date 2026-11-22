<!-- Source: https://create.roblox.com/docs/scripting/events/remote -->

Remote events and callbacks | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/scripting/events/remote.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Scripting](/docs/scripting)
6. /
7. [Events](/docs/scripting/events)

# Remote events and callbacks

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/scripting/events/remote.md)

Roblox games are multiplayer by default, so all games inherently communicate between the server and the players' connected clients. In the simplest case, as players move their characters, certain [Humanoid](/docs/reference/engine/classes/Humanoid)  properties, such as states, are communicated to the server, which passes this information to other connected clients.

Remote events and callbacks let you communicate across  the client-server boundary:

-

[RemoteEvents](/docs/reference/engine/classes/RemoteEvent)  enable one-way communication (sending a request and not  yielding for a response).

-

[UnreliableRemoteEvents](/docs/reference/engine/classes/UnreliableRemoteEvent)  enable one-way communication for data that changes continuously or isn't critical to the game's state. These events trade ordering and reliability for improved network performance.

-

[RemoteFunctions](/docs/reference/engine/classes/RemoteFunction)  enable two-way communication (sending a request and yielding until a response is received from the recipient).

Unlike [bindable events](/docs/scripting/events/bindable) , which have more limited utility, the use cases for remote events and functions are too numerous to list:

-

Gameplay  - Basic gameplay, such as a player reaching the end of a level, can require a remote event. A client script notifies the server, and server scripts reset the player's position.

-

Server verification  - If a player tries to drink a potion, do they actually * have*  that potion? To ensure fairness, the server has to be the source of truth for a game. A client script can use a remote event to notify the server that the player is drinking a potion, and then server scripts can decide whether the player actually has that potion and whether to confer any benefits.

-

User interface updates  - As the game's state changes, server scripts can use remote events to notify clients of changes to scores, objectives, etc.

-

In-game Marketplace purchases  - For an example implementation that uses remote functions, see [Prompt subscription purchases](/docs/production/monetization/subscriptions#prompt-subscription-purchases) .

## [Quick reference](#quick-reference)[](#quick-reference)

The following tables serve as a quick reference for how to use [RemoteEvents](/docs/reference/engine/classes/RemoteEvent)  and [RemoteFunctions](/docs/reference/engine/classes/RemoteFunction)  to communicate between the client and server.

Remote events Remote functions

| [Client → Server](#client-server) |
| --- | --- |
| Client | | RemoteEvent:FireServer(args) |
| Server | | RemoteEvent.OnServerEvent:Connect(function(player, args)) |
| [Server → Client](#server-client) |
| Server | | RemoteEvent:FireClient(player, args) |
| Client | | RemoteEvent.OnClientEvent:Connect(function(args)) |
| [Server → All Clients](#server-all-clients) |
| Server | | RemoteEvent:FireAllClients(args) |
| Client | | RemoteEvent.OnClientEvent:Connect(function(args)) |

## [Remote events](#remote-events)[](#remote-events)

A [RemoteEvent](/docs/reference/engine/classes/RemoteEvent)  object facilitates asynchronous, one-way communication across the client-server boundary without yielding for a response.

To create a new [RemoteEvent](/docs/reference/engine/classes/RemoteEvent)  via the [Explorer](/docs/studio/explorer)  window in Studio:

1.

Hover over the container into which you want to insert the [RemoteEvent](/docs/reference/engine/classes/RemoteEvent) . In order to ensure both server and client access, it must be in a place where both sides can see it, such as [ReplicatedStorage](/docs/reference/engine/classes/ReplicatedStorage) , although in some cases it's appropriate to store it in [Workspace](/docs/reference/engine/classes/Workspace)  or inside a [Tool](/docs/reference/engine/classes/Tool) .

2.

Click the ⊕  button that appears to the right of the container's name and insert a RemoteEvent  instance.

3.

Rename the instance to describe its purpose.

Once you've created a [RemoteEvent](/docs/reference/engine/classes/RemoteEvent) , it can facilitate one-way communication from [client to server](#client-server) , from [server to client](#server-client) , or from the [server to all clients](#server-all-clients) .

![](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Remote-Flow-Client-Server.png) Client → Server

![](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Remote-Flow-Server-Client.png) Server → Client

![](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Remote-Flow-Server-All-Clients.png) Server → All Clients

Clients cannot communicate directly with other clients, although you can effectively dispatch an event from one client to another by using the [RemoteEvent:FireServer()](/docs/reference/engine/classes/RemoteEvent#FireServer)  method, then calling [FireClient()](/docs/reference/engine/classes/RemoteEvent#FireClient)  or [FireAllClients()](/docs/reference/engine/classes/RemoteEvent#FireAllClients)  in the event handler for [OnServerEvent](/docs/reference/engine/classes/RemoteEvent#OnServerEvent) .

### [Client → server](#client-server)[](#client-server)

You can use a [LocalScript](/docs/reference/engine/classes/LocalScript)  to trigger an event on the [server](/docs/projects/client-server)  by calling the [FireServer()](/docs/reference/engine/classes/RemoteEvent#FireServer)  method on a [RemoteEvent](/docs/reference/engine/classes/RemoteEvent) . If you pass arguments to [FireServer()](/docs/reference/engine/classes/RemoteEvent#FireServer) , they pass to the event handler on the server with certain [limitations](#argument-limitations) . Note that the first parameter of the event handler on the server is always the [Player](/docs/reference/engine/classes/Player)  object of the client that calls it, and additional parameters follow.

| Client | | RemoteEvent:FireServer(args) |
| Server | | RemoteEvent.OnServerEvent:Connect(function(player, args)) |

The following [Script](/docs/reference/engine/classes/Script)  connects an event handler to [OnServerEvent](/docs/reference/engine/classes/RemoteEvent#OnServerEvent)  that creates a new [Part](/docs/reference/engine/classes/Part)  on the server. The accompanying [LocalScript](/docs/reference/engine/classes/LocalScript)  then calls [FireServer()](/docs/reference/engine/classes/RemoteEvent#FireServer)  on the [RemoteEvent](/docs/reference/engine/classes/RemoteEvent)  instance with the desired [Color](/docs/reference/engine/classes/BasePart#Color)  and [Position](/docs/reference/engine/classes/BasePart#Position)  for the part.

Event Connection - Script

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Workspace = game:GetService("Workspace")

-- Get reference to remote event instance

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

local function onCreatePart(player, partColor, partPosition)

	print(player.Name .. " fired the RemoteEvent")

	local newPart = Instance.new("Part")

	newPart.Color = partColor

	newPart.Position = partPosition

	newPart.Parent = Workspace

end

-- Connect function to event

remoteEvent.OnServerEvent:Connect(onCreatePart)

```

Event Firing - LocalScript

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- Get reference to remote event instance

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

-- Fire the remote event and pass additional arguments

remoteEvent:FireServer(Color3.fromRGB(255, 0, 0), Vector3.new(0, 25, -20))

```

### [Server → client](#server-client)[](#server-client)

You can use a [Script](/docs/reference/engine/classes/Script)  to trigger an event on a [client](/docs/projects/client-server)  by calling the [FireClient()](/docs/reference/engine/classes/RemoteEvent#FireClient)  method on a [RemoteEvent](/docs/reference/engine/classes/RemoteEvent) . The first argument for [FireClient()](/docs/reference/engine/classes/RemoteEvent#FireClient)  is the [Player](/docs/reference/engine/classes/Player)  object of the client that you want to respond to the event, and additional arguments pass to the client with certain [limitations](#argument-limitations) . Note that the event handler doesn't need to include the [Player](/docs/reference/engine/classes/Player)  object as its first argument because you can determine the player on the client with [Players.LocalPlayer](/docs/reference/engine/classes/Players#LocalPlayer) .

| Server | | RemoteEvent:FireClient(player, args) |
| Client | | RemoteEvent.OnClientEvent:Connect(function(args)) |

The following [LocalScript](/docs/reference/engine/classes/LocalScript)  connects an event handler to the [OnClientEvent](/docs/reference/engine/classes/RemoteEvent#OnClientEvent)  event. The accompanying [Script](/docs/reference/engine/classes/Script)  then listens for incoming players to the server and calls [FireClient()](/docs/reference/engine/classes/RemoteEvent#FireClient)  for each with arbitrary data.

Event Connection - LocalScript

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Players = game:GetService("Players")

-- Get reference to remote event instance

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

local player = Players.LocalPlayer

local function onNotifyPlayer(maxPlayers, respawnTime)

   print("[Client] Event received by player", player.Name)

   print(maxPlayers, respawnTime)

end

-- Connect function to event

remoteEvent.OnClientEvent:Connect(onNotifyPlayer)

```

Event Firing - Script

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Players = game:GetService("Players")

-- Get reference to remote event instance

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

-- Listen for incoming players and dispatch remote event to each

local function onPlayerAdded(player)

   print("[Server] Firing event to player", player.Name)

   remoteEvent:FireClient(player, Players.MaxPlayers, Players.RespawnTime)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

### [Server → all clients](#server-all-clients)[](#server-all-clients)

You can use a [Script](/docs/reference/engine/classes/Script)  to trigger an event on all clients by calling the [FireAllClients()](/docs/reference/engine/classes/RemoteEvent#FireAllClients)  method on a [RemoteEvent](/docs/reference/engine/classes/RemoteEvent) . Unlike [FireClient()](/docs/reference/engine/classes/RemoteEvent#FireClient) , the [FireAllClients()](/docs/reference/engine/classes/RemoteEvent#FireAllClients)  method doesn't require a [Player](/docs/reference/engine/classes/Player)  object because it fires the [RemoteEvent](/docs/reference/engine/classes/RemoteEvent)  to all clients.

| Server | | RemoteEvent:FireAllClients(args) |
| Client | | RemoteEvent.OnClientEvent:Connect(function(args)) |

The following [LocalScript](/docs/reference/engine/classes/LocalScript)  connects an event handler to the [OnClientEvent](/docs/reference/engine/classes/RemoteEvent#OnClientEvent)  event which outputs a remaining countdown time. The accompanying [Script](/docs/reference/engine/classes/Script)  then calls [FireAllClients()](/docs/reference/engine/classes/RemoteEvent#FireAllClients)  in a loop every second to fire the [RemoteEvent](/docs/reference/engine/classes/RemoteEvent)  for all clients.

Event Connection - LocalScript

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- Get reference to remote event instance

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

local function onTimerUpdate(seconds)

	print(seconds)

end

-- Connect function to event

remoteEvent.OnClientEvent:Connect(onTimerUpdate)

```

Event Firing - Script

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- Get reference to remote event instance

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

local countdown = 5

-- Fire the RemoteEvent every second until time expires

for timeRemaining = -1, countdown do

	remoteEvent:FireAllClients(countdown - timeRemaining)

	task.wait(1)

end

```

## [Remote callbacks](#remote-callbacks)[](#remote-callbacks)

A [RemoteFunction](/docs/reference/engine/classes/RemoteFunction)  object facilitates synchronous, two-way communication across the client-server boundary. The sender of a remote function will yield until it receives a response from the recipient.

To create a new [RemoteFunction](/docs/reference/engine/classes/RemoteFunction)  via the [Explorer](/docs/studio/explorer)  window in Studio:

1.

Hover over the container into which you want to insert the [RemoteFunction](/docs/reference/engine/classes/RemoteFunction) . In order to ensure both server and client access, it must be in a place where both sides can see it, such as [ReplicatedStorage](/docs/reference/engine/classes/ReplicatedStorage) , although in some cases it's appropriate to store it in [Workspace](/docs/reference/engine/classes/Workspace)  or inside a [Tool](/docs/reference/engine/classes/Tool) .

2.

Click the ⊕  button that appears to the right of the container's name and insert a RemoteFunction  instance.

3.

Rename the instance to describe its purpose.

Once you've created a [RemoteFunction](/docs/reference/engine/classes/RemoteFunction) , it can facilitate two-way communication between [client and server](#client-server-client)  or between [server and client](#server-client-server) .

![](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Remote-Flow-Client-Server-Client.png) Client → Server → Client

![](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Remote-Flow-Server-Client-Server.png) Server → Client → Server

### [Client → server → client](#client-server-client)[](#client-server-client)

You can use a [LocalScript](/docs/reference/engine/classes/LocalScript)  to call a function on the [server](/docs/projects/client-server)  by calling the [InvokeServer()](/docs/reference/engine/classes/RemoteFunction#InvokeServer)  method on a [RemoteFunction](/docs/reference/engine/classes/RemoteFunction) . Unlike a [remote event](#remote-events) , the [LocalScript](/docs/reference/engine/classes/LocalScript)  that invokes the [RemoteFunction](/docs/reference/engine/classes/RemoteFunction)  yields until the callback returns. Arguments that you pass to [InvokeServer()](/docs/reference/engine/classes/RemoteFunction#InvokeServer)  pass to the [OnServerInvoke](/docs/reference/engine/classes/RemoteFunction#OnServerInvoke)  callback of the [RemoteFunction](/docs/reference/engine/classes/RemoteFunction)  with certain [limitations](#argument-limitations) . Note that if you define multiple callbacks to the same [RemoteFunction](/docs/reference/engine/classes/RemoteFunction) , only the last definition executes.

| Client | | RemoteFunction:InvokeServer(args) |
| Server | | RemoteFunction.OnServerInvoke = function(player, args) |

The following [Script](/docs/reference/engine/classes/Script)  defines the callback function via [OnServerInvoke](/docs/reference/engine/classes/RemoteFunction#OnServerInvoke)  and returns the requested [Part](/docs/reference/engine/classes/Part)  through its return  value. The accompanying [LocalScript](/docs/reference/engine/classes/LocalScript)  then calls [InvokeServer()](/docs/reference/engine/classes/RemoteFunction#InvokeServer)  with extra arguments defining the requested part color and position.

Callback Connection - Script

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Workspace = game:GetService("Workspace")

-- Get reference to remote function instance

local remoteFunction = ReplicatedStorage:FindFirstChildOfClass("RemoteFunction")

-- Callback function

local function createPart(player, partColor, partPosition)

	print(player.Name .. " requested a new part")

	local newPart = Instance.new("Part")

	newPart.Color = partColor

	newPart.Position = partPosition

	newPart.Parent = Workspace

	return newPart

end

-- Set function as remote function's callback

remoteFunction.OnServerInvoke = createPart

```

Event Invocation - LocalScript

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- Get reference to remote function instance

local remoteFunction = ReplicatedStorage:FindFirstChildOfClass("RemoteFunction")

-- Pass a color and position when invoking the callback

local newPart = remoteFunction:InvokeServer(Color3.fromRGB(255, 0, 0), Vector3.new(0, 25, -20))

-- Output the returned part reference

print("The server created the requested part:", newPart)

```

### [Server → client → server](#server-client-server)[](#server-client-server)

You can use a [Script](/docs/reference/engine/classes/Script)  to call a function on the client by calling the [InvokeClient()](/docs/reference/engine/classes/RemoteFunction#InvokeClient)  method on a [RemoteFunction](/docs/reference/engine/classes/RemoteFunction) , but it has serious risks as follows:

-

If the client throws an error, the server throws the error too.

-

If the client disconnects while it's being invoked, [InvokeClient()](/docs/reference/engine/classes/RemoteFunction#InvokeClient)  throws an error.

-

If the client doesn't return a value, the server yields forever.

For actions that don't require two-way communications, such as updating a GUI, use a [RemoteEvent](/docs/reference/engine/classes/RemoteEvent)  and communicate from [server to client](#server-client) .

## [Delivery guarantees](#delivery-guarantees)[](#delivery-guarantees)

Each remote type makes different promises about whether a message arrives and in what order. These promises only apply to a single connection in a single direction, meaning from the server to one specific client, or from one specific client to the server.

### [RemoteEvents](#remoteevents)[](#remoteevents)

[RemoteEvents](/docs/reference/engine/classes/RemoteEvent)  are reliable and ordered:

-

If a message is lost in transit, Roblox retransmits it until it arrives, as long as the recipient stays connected.

-

Messages arrive in the order you fire them, including across different [RemoteEvent](/docs/reference/engine/classes/RemoteEvent)  instances . For example, if the server fires event A , then B , then A  again to the same client, that client receives A , B , A . This applies whether you use [FireClient()](/docs/reference/engine/classes/RemoteEvent#FireClient)  or [FireAllClients()](/docs/reference/engine/classes/RemoteEvent#FireAllClients) .

-

If a client fires events faster than the [throttling](#throttling-and-size-limits)  limit, the server processes the excess events later instead of dropping them, and they keep their order.

A reliable, ordered message can still fail to reach your code in the following cases:

-

No handler is connected.  If nothing is connected to [OnServerEvent](/docs/reference/engine/classes/RemoteEvent#OnServerEvent)  or [OnClientEvent](/docs/reference/engine/classes/RemoteEvent#OnClientEvent)  when a message arrives, Roblox queues it and delivers it, in order, as soon as a handler connects. The queue is limited in both count and memory. Once it's full, Roblox discards further messages and logs a Remote event invocation  error to the [Output](/docs/studio/output)  window.

-

The recipient disconnects.  Messages that haven't been delivered when a client leaves are lost.

Ordering applies to when each handler starts , not when it finishes. If a handler yields, such as by calling [task.wait()](/docs/reference/engine/libraries/task#wait)  or [WaitForChild()](/docs/reference/engine/classes/Instance#WaitForChild) , Roblox can start handling the next message before the earlier handler resumes.

### [RemoteFunctions](#remotefunctions)[](#remotefunctions)

[RemoteFunctions](/docs/reference/engine/classes/RemoteFunction)  send invocations and responses reliably, so Roblox retransmits lost messages as long as both sides stay connected. Because [InvokeServer()](/docs/reference/engine/classes/RemoteFunction#InvokeServer)  and [InvokeClient()](/docs/reference/engine/classes/RemoteFunction#InvokeClient)  yield until a response arrives, a single thread can't have more than one invocation in flight. Separate threads can invoke at the same time, though, and if a callback yields, responses can come back in a different order than the invocations were sent.

If no callback is assigned to [OnServerInvoke](/docs/reference/engine/classes/RemoteFunction#OnServerInvoke)  or [OnClientInvoke](/docs/reference/engine/classes/RemoteFunction#OnClientInvoke) , Roblox queues invocations until one is. This queue has the same kind of limits as the [RemoteEvent](/docs/reference/engine/classes/RemoteEvent)  queue.

Roblox doesn't guarantee the relative order of [RemoteFunction](/docs/reference/engine/classes/RemoteFunction)  invocations and [RemoteEvent](/docs/reference/engine/classes/RemoteEvent)  messages. They often arrive in the order you send them, but they're queued separately while no handler is connected, and a yielding callback can delay a response. If your code depends on strict ordering, send all related messages through the same remote type or include your own sequence number.

### [UnreliableRemoteEvents](#unreliableremoteevents)[](#unreliableremoteevents)

[UnreliableRemoteEvents](/docs/reference/engine/classes/UnreliableRemoteEvent)  guarantee neither delivery nor order. They also have no ordering relationship with [RemoteEvents](/docs/reference/engine/classes/RemoteEvent)  or [RemoteFunctions](/docs/reference/engine/classes/RemoteFunction) . Roblox might drop a message in any of the following cases, without resending it:

-

The message is lost in transit.

-

The network is congested and the message waits too long to send.

-

The payload is larger than 1,000 bytes.

-

The client fires faster than the [throttling](#throttling-and-size-limits)  limit. Unlike a [RemoteEvent](/docs/reference/engine/classes/RemoteEvent) , the server drops the excess messages instead of delaying them.

-

Nothing is connected to [OnServerEvent](/docs/reference/engine/classes/UnreliableRemoteEvent#OnServerEvent)  or [OnClientEvent](/docs/reference/engine/classes/UnreliableRemoteEvent#OnClientEvent)  when the message arrives. Unlike a [RemoteEvent](/docs/reference/engine/classes/RemoteEvent) , Roblox discards the message immediately instead of queuing it.

Roblox also doesn't wait for an earlier message to arrive before processing a later one, so messages can arrive out of order. If order matters, include a timestamp or sequence number in each message and ignore messages older than the latest one you've handled.

### [Throttling and size limits](#throttling-and-size-limits)[](#throttling-and-size-limits)

Client-to-server messages are subject to a rate limit that each remote type shares across all of its instances. For current limits, see the Throttling  section of [RemoteEvent](/docs/reference/engine/classes/RemoteEvent)  and the payload limits in [UnreliableRemoteEvent](/docs/reference/engine/classes/UnreliableRemoteEvent) .

## [Argument limitations](#argument-limitations)[](#argument-limitations)

When you fire a [RemoteEvent](/docs/reference/engine/classes/RemoteEvent)  or invoke a [RemoteFunction](/docs/reference/engine/classes/RemoteFunction) , it forwards any arguments that you pass with the event or to the callback function. Any type of Roblox object such as an [Enum](/docs/reference/engine/datatypes/Enum) , [Instance](/docs/reference/engine/classes/Instance) , or others can be passed, as well as Luau types such as numbers, strings, and booleans, although you should carefully explore the following limitations.

### [Non-string indices](#non-string-indices)[](#non-string-indices)

If any indices  of a passed table are non-string types such as an [Instance](/docs/reference/engine/classes/Instance) , [userdata](/docs/luau/userdata) , or [function](/docs/luau/functions) , Roblox automatically converts those indices to strings.

Event Connection - LocalScript

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

local function onEventFire(passedTable)

	for k, v in passedTable do

		print(typeof(k))  --> string

	end

end

-- Connect function to event

remoteEvent.OnClientEvent:Connect(onEventFire)

```

Event Firing - Script

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Players = game:GetService("Players")

local Workspace = game:GetService("Workspace")

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

-- Listen for incoming players and dispatch remote event to each

local function onPlayerAdded(player)

	remoteEvent:FireClient(player,

		{

			[Workspace.Baseplate] = true

		}

	)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

### [Passed functions](#passed-functions)[](#passed-functions)

Functions included as arguments for a [RemoteEvent](/docs/reference/engine/classes/RemoteEvent)  or [RemoteFunction](/docs/reference/engine/classes/RemoteFunction)  will not  be replicated across the [client-server](/docs/projects/client-server)  boundary, making it impossible to pass functions remotely. Instead, the resulting argument on the receiving side will be nil .

Event Connection - LocalScript

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

local function onClientEvent(func)

	print(func)  --> nil

end

remoteEvent.OnClientEvent:Connect(onClientEvent)

```

Event Firing - Script

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

local function testFunction()

	print("Hello world!")

end

-- Fire remote event with function as an argument

remoteEvent:FireAllClients(testFunction)

```

### [Table indexing](#table-indexing)[](#table-indexing)

If you pass a table of data, do not pass a mixed table of numeric and string keys. Instead, pass a table that consists entirely  of key-value pairs (dictionary) or entirely  of numeric indices.

Whether passing a dictionary table or  a numerically indexed table, avoid nil  values for any index.

Event Connection - Script

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

local function onEventFire(player, passedTable)

	for k, v in passedTable do

		print(k .. " = " .. v)

		--> 1 = Sword

		--> 2 = Bow

		--> CharName = Diva Dragonslayer

		--> CharClass = Rogue

	end

end

-- Connect function to event

remoteEvent.OnServerEvent:Connect(onEventFire)

```

Event Firing - LocalScript

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

-- Numerically indexed table

local inventoryData = {

	"Sword", "Bow"

}

-- Dictionary table

local characterData = {

	CharName = "Diva Dragonslayer",

	CharClass = "Rogue"

}

remoteEvent:FireServer(inventoryData)

remoteEvent:FireServer(characterData)

```

### [Table identities](#table-identities)[](#table-identities)

Tables passed as arguments to remote events/callbacks are copied, meaning they will not be exactly equivalent to those provided when firing the event or invoking the callback. Nor will tables returned to the invoker be exactly equivalent to those provided. You can demonstrate this by running the following script on a [RemoteFunction](/docs/reference/engine/classes/RemoteFunction)  and observing how the table identities differ.

Callback Connection - Script

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local remoteFunction = ReplicatedStorage:FindFirstChildOfClass("RemoteFunction")

-- Callback function

local function returnTable(player, passedTable)

	-- Output table identity on invocation

	print(tostring(passedTable))  --> table: 0x48eb7aead27563d9

	return passedTable

end

-- Set function as remote function's callback

remoteFunction.OnServerInvoke = returnTable

```

Event Invocation - LocalScript

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local remoteFunction = ReplicatedStorage:FindFirstChildOfClass("RemoteFunction")

local inventoryData = {

	"Sword", "Bow"

}

-- Output original table identity

print(tostring(inventoryData))  --> table: 0x059bcdbb2b576549

local invokeReturn = remoteFunction:InvokeServer(inventoryData)

-- Output table identity upon return

print(tostring(invokeReturn))  --> table: 0x9fcae7919563a0e9

```

### [Metatables](#metatables)[](#metatables)

If a table has a metatable, all of the metatable information is lost in the transfer. In the following code sample, the NumWheels  property is part of the Car  metatable. When the server receives the following table, the truck  table has the Name  property but not  the NumWheels  property.

Event Connection - Script

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

local function onEvent(player, param)

	print(param)  --> {["Name"] = "MyTruck"}

end

-- Connect function to event

remoteEvent.OnServerEvent:Connect(onEvent)

```

Event Firing - LocalScript

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

local Car = {}

Car.NumWheels = 4

Car.__index = Car

local truck = {}

truck.Name = "MyTruck"

setmetatable(truck, Car)

-- Fire event with table including a metatable

remoteEvent:FireServer(truck)

```

### [Non-replicated instances](#non-replicated-instances)[](#non-replicated-instances)

If a [RemoteEvent](/docs/reference/engine/classes/RemoteEvent)  or [RemoteFunction](/docs/reference/engine/classes/RemoteFunction)  passes a value that's only visible to the sender, Roblox doesn't replicate it across the client-server boundary and passes nil  instead of the value. For example, if a [Script](/docs/reference/engine/classes/Script)  passes a descendant of [ServerStorage](/docs/reference/engine/classes/ServerStorage) , the client listening to the event will receive a nil  value because that object isn't replicable for the client.

Event Firing - Script

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local ServerStorage = game:GetService("ServerStorage")

local Players = game:GetService("Players")

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

-- Will be received as "nil" because client can't access ServerStorage

local storedPart = Instance.new("Part")

storedPart.Parent = ServerStorage

local function onPlayerAdded(player)

	remoteEvent:FireClient(player, storedPart)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Similarly, if you create a part in a [LocalScript](/docs/reference/engine/classes/LocalScript)  and try to pass it to a [Script](/docs/reference/engine/classes/Script) , the server will see nil  because the part isn't replicable for the server.

Event Firing - LocalScript

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Workspace = game:GetService("Workspace")

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

-- Will be received as "nil" because the server doesn't know about this part

local clientPart = Instance.new("Part")

clientPart.Parent = Workspace

remoteEvent:FireServer(clientPart)

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
