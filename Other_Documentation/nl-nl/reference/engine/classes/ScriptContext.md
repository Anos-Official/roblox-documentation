<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/ScriptContext -->

ScriptContext | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [ScriptContext](/docs/nl-nl/reference/engine/classes/ScriptContext)

Nederlands

Feedback

Engine-klasse

ScriptContext

Niet maakbaar

Service

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/ScriptContext)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[EnableCoverage](#EnableCoverage) (instance :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

 |
| --- | --- |
|

[GetCoverageStats](#GetCoverageStats) () :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[SetTimeout](#SetTimeout) (seconds :  [number](/docs/nl-nl/luau/numbers) ) : ()

 |

Evenementen

|

[Error](#Error) (message :  [string](/docs/nl-nl/luau/strings) , stackTrace :  [string](/docs/nl-nl/luau/strings) , script :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Methoden

EnableCoverage

Mogelijkheden: PluginOrOpenCloud

ScriptContext:EnableCoverage (instance :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

Parameters

|

instance :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Teruggaves

()

Feedback geven

---

GetCoverageStats

Mogelijkheden: PluginOrOpenCloud

ScriptContext:GetCoverageStats () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

SetTimeout

Plugin-beveiliging

ScriptContext:SetTimeout (seconds :[number](/docs/nl-nl/luau/numbers) ) : ()

Parameters

|

seconds :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

()

Feedback geven

---

Evenementen

Error

Mogelijkheden: Logging

ScriptContext.Error (

message :[string](/docs/nl-nl/luau/strings) , stackTrace :[string](/docs/nl-nl/luau/strings) , script :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

message :[string](/docs/nl-nl/luau/strings)

 |
|

stackTrace :[string](/docs/nl-nl/luau/strings)

 |
|

script :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Codevoorbeelden

ScriptContext.Error

```

local ScriptContext = game:GetService("ScriptContext")

local function onError(message, trace, script)

	print(script:GetFullName(), "heeft een fout veroorzaakt!")

	print("Reden:", message)

	print("Trace:", trace)

end

ScriptContext.Error:Connect(onError)

-- Elders, in een ander script

error("Er is een fout opgetreden!")

```

Feedback geven

---

Ga naar

▼

ScriptContext

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Methoden](#methods)

[EnableCoverage()](#EnableCoverage)

[GetCoverageStats()](#GetCoverageStats)

[SetTimeout()](#SetTimeout)

[Evenementen](#events)

[Error](#Error)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
