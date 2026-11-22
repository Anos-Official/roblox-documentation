<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/libraries/debug -->

debug | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Bibliotheken](/docs/nl-nl/reference/engine/libraries)
2. /
3. [debug](/docs/nl-nl/reference/engine/libraries/debug)

Nederlands

Feedback

Engine-bibliotheek

debug

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/libraries/debug)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Functies

|

[traceback](#traceback) (message :  [string](/docs/nl-nl/luau/strings) , level :  [number](/docs/nl-nl/luau/numbers) ) :[string](/docs/nl-nl/luau/strings)

 |
| --- | --- |
|

[traceback](#traceback-thread-mes) (thread :  [coroutine](/docs/nl-nl/reference/engine/libraries/coroutine) , message :  [string](/docs/nl-nl/luau/strings) , level :  [number](/docs/nl-nl/luau/numbers) ) :[string](/docs/nl-nl/luau/strings)

 |
|

[info](#info) (level :  [number](/docs/nl-nl/luau/numbers) , options :  [string](/docs/nl-nl/luau/strings) ) :[Tuple](/docs/nl-nl/luau/tuples)

 |
|

[info](#info-function-o) (function :  [function](/docs/nl-nl/luau/functions) , options :  [string](/docs/nl-nl/luau/strings) ) :[Tuple](/docs/nl-nl/luau/tuples)

 |
|

[info](#info-thread-lev) (thread :  [coroutine](/docs/nl-nl/reference/engine/libraries/coroutine) , level :  [number](/docs/nl-nl/luau/numbers) , options :  [string](/docs/nl-nl/luau/strings) ) :[Tuple](/docs/nl-nl/luau/tuples)

 |
|

[profilebegin](#profilebegin) (label :  [string](/docs/nl-nl/luau/strings) ) : ()

 |
|

[profileend](#profileend) () : ()

 |
|

[getmemorycategory](#getmemorycategory) () :[string](/docs/nl-nl/luau/strings)

 |
|

[setmemorycategory](#setmemorycategory) (tag :  [string](/docs/nl-nl/luau/strings) ) :[string](/docs/nl-nl/luau/strings)

 |
|

[resetmemorycategory](#resetmemorycategory) () : ()

 |
|

[dumpcodesize](#dumpcodesize) () : ()

 |

---

API-referentie

Functies

traceback

debug.traceback (

message :[string](/docs/nl-nl/luau/strings) , level :[number](/docs/nl-nl/luau/numbers)

) :[string](/docs/nl-nl/luau/strings)

Parameters

|

message :[string](/docs/nl-nl/luau/strings)

 |
|

level :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 1 |

Teruggaves

[string](/docs/nl-nl/luau/strings)

Codevoorbeelden

##### Debug Traceback

Feedback geven

---

traceback

debug.traceback (

thread :[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine) , message :[string](/docs/nl-nl/luau/strings) , level :[number](/docs/nl-nl/luau/numbers)

) :[string](/docs/nl-nl/luau/strings)

Parameters

|

thread :[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine)

 |
|

message :[string](/docs/nl-nl/luau/strings)

 |
|

level :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 1 |

Teruggaves

[string](/docs/nl-nl/luau/strings)

Codevoorbeelden

##### Debug Traceback Van Een Thread

Feedback geven

---

info

debug.info (

level :[number](/docs/nl-nl/luau/numbers) , options :[string](/docs/nl-nl/luau/strings)

) :[Tuple](/docs/nl-nl/luau/tuples)

Parameters

|

level :[number](/docs/nl-nl/luau/numbers)

 |
|

options :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Codevoorbeelden

##### Debug Informatie Per Niveau

Feedback geven

---

info

debug.info (

function :[function](/docs/nl-nl/luau/functions) , options :[string](/docs/nl-nl/luau/strings)

) :[Tuple](/docs/nl-nl/luau/tuples)

Parameters

|

function :[function](/docs/nl-nl/luau/functions)

 |
|

options :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Codevoorbeelden

##### Debug Informatie Per Functie

Feedback geven

---

info

debug.info (

thread :[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine) , level :[number](/docs/nl-nl/luau/numbers) , options :[string](/docs/nl-nl/luau/strings)

) :[Tuple](/docs/nl-nl/luau/tuples)

Parameters

|

thread :[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine)

 |
|

level :[number](/docs/nl-nl/luau/numbers)

 |
|

options :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Codevoorbeelden

##### Debug Informatie Per Draad

Feedback geven

---

profilebegin

debug.profilebegin (label :[string](/docs/nl-nl/luau/strings) ) : ()

Parameters

|

label :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

()

Codevoorbeelden

Debug Profiel Begin

```

local function buildGrid(size)

	debug.profilebegin("BuildGrid")

	local grid = table.create(size * size, 0)

	debug.profileend()

	return grid

end

print(#buildGrid(32)) --> 1024

```

Feedback geven

---

profileend

debug.profileend () : ()

Teruggaves

()

Codevoorbeelden

Debug Profiel Einde

```

debug.profilebegin("Outer")

debug.profilebegin("Inner")

-- Het werk dat hier gedaan wordt, wordt getimed onder beide labels

debug.profileend() -- sluit "Inner"

debug.profileend() -- sluit "Outer"

```

Feedback geven

---

getmemorycategory

debug.getmemorycategory () :[string](/docs/nl-nl/luau/strings)

Teruggaves

[string](/docs/nl-nl/luau/strings)

Codevoorbeelden

Debug Geheugen Categorie

```

local category = debug.getmemorycategory()

print(type(category)) --> string

-- De categorie volgt de thread, dus een nieuwe kan verschillen van deze

local previous = debug.setmemorycategory("Padvinden")

print(debug.getmemorycategory()) --> Padvinden

debug.setmemorycategory(previous)

```

Feedback geven

---

setmemorycategory

debug.setmemorycategory (tag :[string](/docs/nl-nl/luau/strings) ) :[string](/docs/nl-nl/luau/strings)

Parameters

|

tag :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[string](/docs/nl-nl/luau/strings)

Codevoorbeelden

Debug Set Geheugen Categorie

```

local original = debug.setmemorycategory("MapGeneration")

print(debug.getmemorycategory()) --> MapGeneration

-- Allocaties die hier worden gemaakt, worden vermeld onder "MapGeneration" in de Developer Console

local tiles = table.create(1000, 0)

-- De retourwaarde is de vorige categorie, zodat deze kan worden hersteld

print(debug.setmemorycategory(original) == "MapGeneration") --> true

```

Feedback geven

---

resetmemorycategory

debug.resetmemorycategory () : ()

Teruggaves

()

Codevoorbeelden

Debug Reset Geheugen Categorie

```

local automatic = debug.getmemorycategory()

debug.setmemorycategory("Spawning")

print(debug.getmemorycategory()) --> Spawning

debug.resetmemorycategory()

print(debug.getmemorycategory() == automatic) --> true

```

Feedback geven

---

dumpcodesize

debug.dumpcodesize () : ()

Teruggaves

()

Codevoorbeelden

Debug Dump Code Grootte

```

-- debug.dumpcodesize() werkt alleen vanuit de Studio Command Bar, waar het een

-- rapport naar de Output afdrukt met één tabel per native script, grootste functies eerst:

--   # Analyse van Native Code Grootte

--     <n> scripts, <n> functies, <n> KB geheugen, 256 MB codegrootte limiet

--   ## <script naam>

--     <n> functies, <n> KB geheugen

--     | Functie | Regel | Native Code Grootte | Native Code Grootte (%) |

-- Alleen scripts die beginnen met --!native en zijn uitgevoerd verschijnen in het rapport.

-- Vanuit een Script genereert het een fout, die pcall opvangt

local ok, message = pcall(debug.dumpcodesize)

print(ok) --> false

print(message) --> dumpcodesize kan alleen worden aangeroepen vanuit CommandBar

```

Feedback geven

---

Ga naar

▼

debug

[Samenvatting](#summary)

[Functies](#summary-functions)

[Functies](#functions)

[traceback()](#traceback)

[info()](#info)

[profilebegin()](#profilebegin)

[profileend()](#profileend)

[getmemorycategory()](#getmemorycategory)

[setmemorycategory()](#setmemorycategory)

[resetmemorycategory()](#resetmemorycategory)

[dumpcodesize()](#dumpcodesize)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
