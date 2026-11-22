<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/PluginConnectionService -->

PluginConnectionService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [PluginConnectionService](/docs/nl-nl/reference/engine/classes/PluginConnectionService)

Nederlands

Feedback

Engine-klasse

PluginConnectionService

Niet maakbaar

Service

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/PluginConnectionService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[CanHaveConnectionType](#CanHaveConnectionType) (type :  [Enum.PluginConnectionTargetType](/docs/nl-nl/reference/engine/enums/PluginConnectionTargetType) ) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |
|

[GetPluginConnectionsOfType](#GetPluginConnectionsOfType) (type :  [Enum.PluginConnectionTargetType](/docs/nl-nl/reference/engine/enums/PluginConnectionTargetType) ) : {[PluginConnection](/docs/nl-nl/reference/engine/classes/PluginConnection) }

 |

Evenementen

|

[Connected](#Connected) (conn :  [PluginConnection](/docs/nl-nl/reference/engine/classes/PluginConnection) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

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

			Connection:SendMessage(`Hallo van {Side} iteratie {Count}`)

		end

		Count += 1

	end)

	plugin.Unloading:Connect(function()

		Binding:Disconnect()

	end)

	Connection:GetPropertyChangedSignal("Connected"):Once(function()

		assert(not Connection.Connected)

		print("Verbonden verbroken", Connection.TargetId)

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

	Connection:SendMessage("Hallo Edit!")

end

```

---

API-referentie

Methoden

CanHaveConnectionType

Plugin-beveiliging

PluginConnectionService:CanHaveConnectionType (type :[Enum.PluginConnectionTargetType](/docs/nl-nl/reference/engine/enums/PluginConnectionTargetType) ) :[boolean](/docs/nl-nl/luau/booleans)

Parameters

|

type :[Enum.PluginConnectionTargetType](/docs/nl-nl/reference/engine/enums/PluginConnectionTargetType)

 |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

GetPluginConnectionsOfType

Plugin-beveiliging

PluginConnectionService:GetPluginConnectionsOfType (type :[Enum.PluginConnectionTargetType](/docs/nl-nl/reference/engine/enums/PluginConnectionTargetType) ) : {[PluginConnection](/docs/nl-nl/reference/engine/classes/PluginConnection) }

Parameters

|

type :[Enum.PluginConnectionTargetType](/docs/nl-nl/reference/engine/enums/PluginConnectionTargetType)

 |

Teruggaves

{[PluginConnection](/docs/nl-nl/reference/engine/classes/PluginConnection) }

Feedback geven

---

Evenementen

Connected

Plugin-beveiliging

PluginConnectionService.Connected (conn :[PluginConnection](/docs/nl-nl/reference/engine/classes/PluginConnection) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

conn :[PluginConnection](/docs/nl-nl/reference/engine/classes/PluginConnection)

 |

Feedback geven

---

Ga naar

▼

PluginConnectionService

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Methoden](#methods)

[CanHaveConnectionType()](#CanHaveConnectionType)

[GetPluginConnectionsOfType()](#GetPluginConnectionsOfType)

[Evenementen](#events)

[Connected](#Connected)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
