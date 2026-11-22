<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Actor -->

Actor | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [PVInstance](/docs/nl-nl/reference/engine/classes/PVInstance)
8. /
9. [Model](/docs/nl-nl/reference/engine/classes/Model)
10. /
11. [Actor](/docs/nl-nl/reference/engine/classes/Actor)

Nederlands

Feedback

Engine-klasse

Actor

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Actor)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[BindToMessage](#BindToMessage) (topic :  [string](/docs/nl-nl/luau/strings) , function :  [function](/docs/nl-nl/luau/functions) ) :[RBXScriptConnection](/docs/nl-nl/reference/engine/datatypes/RBXScriptConnection)

 |
| --- | --- |
|

[BindToMessageParallel](#BindToMessageParallel) (topic :  [string](/docs/nl-nl/luau/strings) , function :  [function](/docs/nl-nl/luau/functions) ) :[RBXScriptConnection](/docs/nl-nl/reference/engine/datatypes/RBXScriptConnection)

 |
|

[SendMessage](#SendMessage) (topic :  [string](/docs/nl-nl/luau/strings) , message :  [Tuple](/docs/nl-nl/luau/tuples) ) : ()

 |

Overgenomen leden

26  overgenomen van [Model](/docs/nl-nl/reference/engine/classes/Model)

4  overgenomen van [PVInstance](/docs/nl-nl/reference/engine/classes/PVInstance)

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Methoden

BindToMessage

Parallel schrijven

Mogelijkheden: Basic

Actor:BindToMessage (

topic :[string](/docs/nl-nl/luau/strings) , function :[function](/docs/nl-nl/luau/functions)

) :[RBXScriptConnection](/docs/nl-nl/reference/engine/datatypes/RBXScriptConnection)

Parameters

|

topic :[string](/docs/nl-nl/luau/strings)

 |
|

function :[function](/docs/nl-nl/luau/functions)

 |

Teruggaves

[RBXScriptConnection](/docs/nl-nl/reference/engine/datatypes/RBXScriptConnection)

Codevoorbeelden

Bind Aan Bericht

```

local actor = script:GetActor()

-- Print een bericht wanneer een begroetingsbericht naar de Actor wordt verzonden

-- waar dit script een afstammeling van is.

local connection = actor:BindToMessage("Greeting", function(message)

  print("Ontvangen Begroetingsbericht:", message)

end)

```

Feedback geven

---

BindToMessageParallel

Parallel schrijven

Mogelijkheden: Basic

Actor:BindToMessageParallel (

topic :[string](/docs/nl-nl/luau/strings) , function :[function](/docs/nl-nl/luau/functions)

) :[RBXScriptConnection](/docs/nl-nl/reference/engine/datatypes/RBXScriptConnection)

Parameters

|

topic :[string](/docs/nl-nl/luau/strings)

 |
|

function :[function](/docs/nl-nl/luau/functions)

 |

Teruggaves

[RBXScriptConnection](/docs/nl-nl/reference/engine/datatypes/RBXScriptConnection)

Codevoorbeelden

Bind Aan Bericht Parallel

```

local actor = script:GetActor()

-- Print een bericht wanneer een begroetingsbericht naar de Actor wordt verzonden

-- waar dit script een afstammeling van is.

local connection = actor:BindToMessageParallel("Greeting", function(message)

  print("Ontvangen Begroetingsbericht:", message)

end)

```

Feedback geven

---

SendMessage

Parallel schrijven

Mogelijkheden: Basic

Actor:SendMessage (

topic :[string](/docs/nl-nl/luau/strings) , message :[Tuple](/docs/nl-nl/luau/tuples)

) : ()

Parameters

|

topic :[string](/docs/nl-nl/luau/strings)

 |
|

message :[Tuple](/docs/nl-nl/luau/tuples)

 |

Teruggaves

()

Codevoorbeelden

Bericht Verzenden

```

local actor = script:GetActor()

actor:SendMessage("Groet", "Hallo Wereld")

```

Feedback geven

---

Ga naar

▼

Actor

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[BindToMessage()](#BindToMessage)

[BindToMessageParallel()](#BindToMessageParallel)

[SendMessage()](#SendMessage)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
