<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/globals/RobloxGlobals -->

Roblox globals | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Globals](/docs/nl-nl/reference/engine/globals)
2. /
3. [Roblox globals](/docs/nl-nl/reference/engine/globals/Roblox%20globals)

Nederlands

Feedback

Engine-global

Roblox globals

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/globals/RobloxGlobals)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Functies

|

[delay](#delay) (delayTime :  [number](/docs/nl-nl/luau/numbers) , callback :  [function](/docs/nl-nl/luau/functions) ) : ()

Verouderd

 |
| --- | --- |
|

[DebuggerManager](#DebuggerManager) () : DebuggerManager

Verouderd

 |
|

[elapsedTime](#elapsedTime) () :[number](/docs/nl-nl/luau/numbers)

Verouderd

 |
|

[PluginManager](#PluginManager) () :[PluginManager](/docs/nl-nl/reference/engine/classes/PluginManager)

 |
|

[printidentity](#printidentity) (prefix :  [string](/docs/nl-nl/luau/strings) ) : ()

Verouderd

 |
|

[settings](#settings) () :[GlobalSettings](/docs/nl-nl/reference/engine/classes/GlobalSettings)

 |
|

[spawn](#spawn) (callback :  [function](/docs/nl-nl/luau/functions) ) : ()

Verouderd

 |
|

[stats](#stats) () :[Stats](/docs/nl-nl/reference/engine/classes/Stats)

Verouderd

 |
|

[tick](#tick) () :[number](/docs/nl-nl/luau/numbers)

 |
|

[time](#time) () :[number](/docs/nl-nl/luau/numbers)

 |
|

[typeof](#typeof) (object :  Variant ) :[string](/docs/nl-nl/luau/strings)

 |
|

[UserSettings](#UserSettings) () :[UserSettings](/docs/nl-nl/reference/engine/classes/UserSettings)

 |
|

[version](#version) () :[string](/docs/nl-nl/luau/strings)

Verouderd

 |
|

[wait](#wait) (seconds :  [number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers) ,[number](/docs/nl-nl/luau/numbers)

Verouderd

 |
|

[warn](#warn) (params :  [Tuple](/docs/nl-nl/luau/tuples) ) : ()

 |
|

[ypcall](#ypcall) (f :  [function](/docs/nl-nl/luau/functions) , args :  [Tuple](/docs/nl-nl/luau/tuples) ) :[boolean](/docs/nl-nl/luau/booleans) , Variant

Verouderd

 |

Eigenschappen

|

[Enum](#Enum) :[Enums](/docs/nl-nl/reference/engine/datatypes/Enums)

 |
|

[game](#game) :[DataModel](/docs/nl-nl/reference/engine/classes/DataModel)

 |
|

[plugin](#plugin) :[Plugin](/docs/nl-nl/reference/engine/classes/Plugin)

 |
|

[shared](#shared) :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[script](#script) :[LuaSourceContainer](/docs/nl-nl/reference/engine/classes/LuaSourceContainer)

 |
|

[workspace](#workspace) :[Workspace](/docs/nl-nl/reference/engine/classes/Workspace)

 |

---

API-referentie

Functies

delay

Verouderd

Details weergeven

---

DebuggerManager

Verouderd

Details weergeven

---

elapsedTime

Verouderd

Details weergeven

---

PluginManager

PluginManager () :[PluginManager](/docs/nl-nl/reference/engine/classes/PluginManager)

Teruggaves

[PluginManager](/docs/nl-nl/reference/engine/classes/PluginManager)

Feedback geven

---

printidentity

Verouderd

Details weergeven

---

settings

settings () :[GlobalSettings](/docs/nl-nl/reference/engine/classes/GlobalSettings)

Teruggaves

[GlobalSettings](/docs/nl-nl/reference/engine/classes/GlobalSettings)

Feedback geven

---

spawn

Verouderd

Details weergeven

---

stats

Verouderd

Details weergeven

---

tick

tick () :[number](/docs/nl-nl/luau/numbers)

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

time

time () :[number](/docs/nl-nl/luau/numbers)

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

typeof

typeof (object : Variant ) :[string](/docs/nl-nl/luau/strings)

Parameters

|

object : Variant

 |

Teruggaves

[string](/docs/nl-nl/luau/strings)

Feedback geven

---

UserSettings

UserSettings () :[UserSettings](/docs/nl-nl/reference/engine/classes/UserSettings)

Teruggaves

[UserSettings](/docs/nl-nl/reference/engine/classes/UserSettings)

Feedback geven

---

version

Verouderd

Details weergeven

---

wait

Verouderd

Details weergeven

---

warn

warn (params :[Tuple](/docs/nl-nl/luau/tuples) ) : ()

Parameters

|

params :[Tuple](/docs/nl-nl/luau/tuples)

 |

Teruggaves

()

Feedback geven

---

ypcall

Verouderd

Details weergeven

---

Eigenschappen

Enum

Enum :[Enums](/docs/nl-nl/reference/engine/datatypes/Enums)

Feedback geven

---

game

game :[DataModel](/docs/nl-nl/reference/engine/classes/DataModel)

Feedback geven

---

plugin

plugin :[Plugin](/docs/nl-nl/reference/engine/classes/Plugin)

Codevoorbeelden

Roblox Globals Plugin

```

assert(plugin, "Dit script moet als een plugin worden uitgevoerd!")

-- Code verderop zal alleen worden uitgevoerd als het script als een plugin wordt uitgevoerd

```

Feedback geven

---

shared

shared :[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

script

script :[LuaSourceContainer](/docs/nl-nl/reference/engine/classes/LuaSourceContainer)

Feedback geven

---

workspace

workspace :[Workspace](/docs/nl-nl/reference/engine/classes/Workspace)

Feedback geven

---

Ga naar

▼

Roblox globals

[Samenvatting](#summary)

[Functies](#summary-functions)

[Eigenschappen](#summary-properties)

[Functies](#functions)

[delay()](#delay)

[DebuggerManager()](#DebuggerManager)

[elapsedTime()](#elapsedTime)

[PluginManager()](#PluginManager)

[printidentity()](#printidentity)

[settings()](#settings)

[spawn()](#spawn)

[stats()](#stats)

[tick()](#tick)

[time()](#time)

[typeof()](#typeof)

[UserSettings()](#UserSettings)

[version()](#version)

[wait()](#wait)

[warn()](#warn)

[ypcall()](#ypcall)

[Eigenschappen](#properties)

[Enum](#Enum)

[game](#game)

[plugin](#plugin)

[shared](#shared)

[script](#script)

[workspace](#workspace)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
