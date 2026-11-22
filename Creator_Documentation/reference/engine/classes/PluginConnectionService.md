<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/PluginConnectionService -->

PluginConnectionService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/PluginConnectionService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [PluginConnectionService](/docs/en-us/reference/engine/classes/PluginConnectionService)

English

Feedback

Engine Class

PluginConnectionService

Not Creatable

Service

Not Replicated

---

## Summary

Methods

|

[CanHaveConnectionType](#CanHaveConnectionType) (type :  [Enum.PluginConnectionTargetType](/docs/en-us/reference/engine/enums/PluginConnectionTargetType) ) :[boolean](/docs/en-us/luau/booleans)

 |
| --- | --- |
|

[GetPluginConnectionsOfType](#GetPluginConnectionsOfType) (type :  [Enum.PluginConnectionTargetType](/docs/en-us/reference/engine/enums/PluginConnectionTargetType) ) : {[PluginConnection](/docs/en-us/reference/engine/classes/PluginConnection) }

 |

Events

|

[Connected](#Connected) (conn :  [PluginConnection](/docs/en-us/reference/engine/classes/PluginConnection) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

PluginConnection echo Plugin

```

local Service = game:GetService("PluginConnectionService")

local TestType = Enum.PluginConnectionTargetType.Test

local EditType = Enum.PluginConnectionTargetType.Edit

local function MakeConnection(Connection: PluginConnection, Side: string)

	assert(Connection.Connected)

	local Count = 0

	local Binding = Connection:BindToMessage(function(Msg: string)

		print(Msg)

		task.wait(1)

		if Connection.Connected then

			Connection:SendMessage(`Hello from {Side} iteration {Count}`)

		end

		Count += 1

	end)

	plugin.Unloading:Connect(function()

		Binding:Disconnect()

	end)

	Connection:GetPropertyChangedSignal("Connected"):Once(function()

		assert(not Connection.Connected)

		print("Disconnected", Connection.TargetId)

	end)

end

if Service:CanHaveConnectionType(TestType) then

	for _, ExistingConnection in Service:GetPluginConnectionsOfType(TestType) do

		MakeConnection(ExistingConnection, "Edit")

	end

	Service.Connected:Connect(function(NewConnection)

		if NewConnection.Type == TestType then

			MakeConnection(NewConnection, "Edit")

		end

	end)

elseif Service:CanHaveConnectionType(EditType) then

	local Connections = Service:GetPluginConnectionsOfType(EditType)

	assert(#Connections <= 1)

	local Connection: PluginConnection? = nil

	if #Connections == 1 then

		Connection = Connections[1]

	else

		while true do

			local NewConnection = Service.Connected:Wait()

			if NewConnection.Type == EditType then

				Connection = NewConnection

				break

			end

		end

	end

	assert(Connection)

	assert(Connection.Connected)

	MakeConnection(Connection, if game:GetService("RunService"):IsServer() then "Server" else "Client")

	Connection:SendMessage("Hello Edit!")

end

```

---

API Reference

Methods

CanHaveConnectionType

Plugin Security

PluginConnectionService:CanHaveConnectionType (type :[Enum.PluginConnectionTargetType](/docs/en-us/reference/engine/enums/PluginConnectionTargetType) ) :[boolean](/docs/en-us/luau/booleans)

Parameters

|

type :[Enum.PluginConnectionTargetType](/docs/en-us/reference/engine/enums/PluginConnectionTargetType)

 |

Returns

[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

GetPluginConnectionsOfType

Plugin Security

PluginConnectionService:GetPluginConnectionsOfType (type :[Enum.PluginConnectionTargetType](/docs/en-us/reference/engine/enums/PluginConnectionTargetType) ) : {[PluginConnection](/docs/en-us/reference/engine/classes/PluginConnection) }

Parameters

|

type :[Enum.PluginConnectionTargetType](/docs/en-us/reference/engine/enums/PluginConnectionTargetType)

 |

Returns

{[PluginConnection](/docs/en-us/reference/engine/classes/PluginConnection) }

Provide feedback

---

Events

Connected

Plugin Security

PluginConnectionService.Connected (conn :[PluginConnection](/docs/en-us/reference/engine/classes/PluginConnection) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

conn :[PluginConnection](/docs/en-us/reference/engine/classes/PluginConnection)

 |

Provide feedback

---

Jump to

▼

PluginConnectionService

[Summary](#summary)

[Methods](#summary-methods)

[Events](#summary-events)

[Methods](#methods)

[CanHaveConnectionType()](#CanHaveConnectionType)

[GetPluginConnectionsOfType()](#GetPluginConnectionsOfType)

[Events](#events)

[Connected](#Connected)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
