<!-- Source: https://create.roblox.com/docs/en-us/scripting/events -->

Events | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/scripting/events.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Scripting](/docs/en-us/scripting)
6. /
7. [Events](/docs/en-us/scripting/events)

# Events

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/scripting/events/index.md)

Events are occurrences within your game that you can listen for and respond to. Many Roblox services and objects have built-in events that automatically fire  in response to specific actions or changes.

For example, a player's [Character](/docs/en-us/reference/engine/classes/Player#Character)  touching a [BasePart](/docs/en-us/reference/engine/classes/BasePart)  automatically fires a [Touched](/docs/en-us/reference/engine/classes/BasePart#Touched)  event. Each time a player joins your game, the [Players.PlayerAdded](/docs/en-us/reference/engine/classes/Players#PlayerAdded)  event fires.

Due to the sheer number of events and client-server architecture, Roblox scripting is often referred to as event-driven . This approach is different from many other game engines, which emphasize running code on a frame-by-frame basis.

You don't have to listen for events or take any action in response to them, but the events are firing and available nevertheless. When you do want to respond to an event, you connect a function to it.

Deferred events can help you ensure more performant and consistent event handling. See [here](/docs/en-us/scripting/events/deferred)  for more information.

## [Connect functions to events](#connect-functions-to-events)[](#connect-functions-to-events)

You connect a function to an event using [Connect()](/docs/en-us/reference/engine/datatypes/RBXScriptSignal#Connect)  to execute code each time the event fires. Most events pass arguments to their connected functions. For example, the [BasePart.Touched](/docs/en-us/reference/engine/classes/BasePart#Touched)  event passes the object that touched the part (such as a left hand or car wheel), and the [Players.PlayerAdded](/docs/en-us/reference/engine/classes/Players#PlayerAdded)  event passes the [Player](/docs/en-us/reference/engine/classes/Player)  that joined your game.

The following code sample demonstrates how to connect a function named onPartTouched()  to the [Touched](/docs/en-us/reference/engine/classes/BasePart#Touched)  event of a part:

```

-- Assumes the script is parented to the part

local part = script.Parent

-- The function you want to run

local function onPartTouched(object)

	print("Part was touched by", object:GetFullName())

end

-- Connect the function to the part's Touched event

part.Touched:Connect(onPartTouched)

```

As a best practice and for optimal performance, it's recommended that you [disconnect](#disconnect-functions-from-events)  functions when the connection is no longer needed. Note, however, that this may not always  be necessary, as all connections to an object's [non-deferred](/docs/en-us/scripting/events/deferred)  events are automatically disconnected if an object is destroyed.

You can also connect [anonymous functions](/docs/en-us/luau/functions#anonymous-functions)  to events when you want to use variables in the parent scope and don't need to use the function elsewhere. For example, this code sample avoids the awkward intermediary function from the similar sample in [Services](/docs/en-us/scripting/services) :

```

local Players = game:GetService("Players")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local SaveManager = require(ReplicatedStorage:WaitForChild("SaveManager"))

local function saveProgress(character)

	local position = character:FindFirstChild("HumanoidRootPart").Position

	SaveManager.saveData(character, position)

end

-- Anonymous function that calls saveProgress() when a character is removed

-- from the game (in this case, when the player leaves).

Players.PlayerAdded:Connect(function(player)

	player.CharacterRemoving:Connect(saveProgress)

end)

```

## [Disconnect functions from events](#disconnect-functions-from-events)[](#disconnect-functions-from-events)

The [Connect()](/docs/en-us/reference/engine/datatypes/RBXScriptSignal#Connect)  method returns an [RBXScriptConnection](/docs/en-us/reference/engine/datatypes/RBXScriptConnection)  object. If you connect a function to an event, but don't want to call the function the next time an event fires (such as after some condition is met), disconnect it by calling [Disconnect()](/docs/en-us/reference/engine/datatypes/RBXScriptConnection#Disconnect)  on the [RBXScriptConnection](/docs/en-us/reference/engine/datatypes/RBXScriptConnection)  object.

The following code sample shows how to connect and disconnect a function from the [Part.Touched](/docs/en-us/reference/engine/classes/BasePart#Touched)  event:

```

local Workspace = game:GetService("Workspace")

local part = Workspace.Part

local targetPart = Workspace.TargetPart

-- Declare an empty placeholder variable for the connection

local connection

local function onPartTouched(otherPart)

	if otherPart == targetPart then

		print("The part hit the target!")

		-- Disconnect the connection

		connection:Disconnect()

	end

end

-- Connect the above function to the Touched event

connection = part.Touched:Connect(onPartTouched)

```

If you only want to connect a function to an event once — that is, only run the function the first time the event fires — use the [Once()](/docs/en-us/reference/engine/datatypes/RBXScriptSignal#Once)  method as a more convenient alternative to connecting and disconnecting the function.

When Luau destroys an event's object, such as the [Player](/docs/en-us/reference/engine/classes/Player)  object when a user leaves the game, all of its [non-deferred](/docs/en-us/scripting/events/deferred)  connections disconnect automatically.

## [Wait for events to fire](#wait-for-events-to-fire)[](#wait-for-events-to-fire)

If you want a script to yield until a specific event fires, use the [Wait()](/docs/en-us/reference/engine/datatypes/RBXScriptSignal#Wait)  method. This method returns the event's arguments, which you can assign to variables for later use:

```

local Workspace = game:GetService("Workspace")

local part = Workspace.Part

local touchedPart = part.Touched:Wait()

print("The part was touched by", touchedPart:GetFullName())

```

## [Other types of events](#other-types-of-events)[](#other-types-of-events)

-

[Bindable events](/docs/en-us/scripting/events/bindable)  let you communicate between scripts on the same side  of the client-server boundary.

-

[Remote events](/docs/en-us/scripting/events/remote)  let you communicate across  the client-server boundary.

-

[Deferred engine events](/docs/en-us/scripting/events/deferred)  defer event handlers until certain resumption points.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
