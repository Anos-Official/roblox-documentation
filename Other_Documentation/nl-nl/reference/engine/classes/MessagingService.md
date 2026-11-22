<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/MessagingService -->

MessagingService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [MessagingService](/docs/nl-nl/reference/engine/classes/MessagingService)

Nederlands

Feedback

Engine-klasse

MessagingService

Niet maakbaar

Service

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/MessagingService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[PublishAsync](#PublishAsync) (topic :  [string](/docs/nl-nl/luau/strings) , message :  Variant ) : ()

 |
| --- | --- |
|

[SubscribeAsync](#SubscribeAsync) (topic :  [string](/docs/nl-nl/luau/strings) , callback :  [function](/docs/nl-nl/luau/functions) ) :[RBXScriptConnection](/docs/nl-nl/reference/engine/datatypes/RBXScriptConnection)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Methoden

PublishAsync

Opbrengst

Mogelijkheden: ServerCommunication

Cloud-API

MessagingService:PublishAsync (

topic :[string](/docs/nl-nl/luau/strings) , message : Variant

) : ()

Parameters

|

topic :[string](/docs/nl-nl/luau/strings)

 |
|

message : Variant

 |

Teruggaves

()

Feedback geven

---

SubscribeAsync

Opbrengst

Mogelijkheden: ServerCommunication

MessagingService:SubscribeAsync (

topic :[string](/docs/nl-nl/luau/strings) , callback :[function](/docs/nl-nl/luau/functions)

) :[RBXScriptConnection](/docs/nl-nl/reference/engine/datatypes/RBXScriptConnection)

Parameters

|

topic :[string](/docs/nl-nl/luau/strings)

 |
|

callback :[function](/docs/nl-nl/luau/functions)

 |

Teruggaves

[RBXScriptConnection](/docs/nl-nl/reference/engine/datatypes/RBXScriptConnection)

Codevoorbeelden

Abonneren op Cross Server Berichten

```

local MessagingService = game:GetService("MessagingService")

local Players = game:GetService("Players")

local function onPlayerAdded(player)

	-- abonneer op het onderwerp

	local topic = "player-" .. player.UserId

	local connection = MessagingService:SubscribeAsync(topic, function(message)

		print("Ontvangen bericht voor", player.Name, message.Data)

	end)

	player.AncestryChanged:Connect(function()

		-- schrijf je uit van het onderwerp

		connection:Disconnect()

	end)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Feedback geven

---

Ga naar

▼

MessagingService

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[PublishAsync()](#PublishAsync)

[SubscribeAsync()](#SubscribeAsync)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
