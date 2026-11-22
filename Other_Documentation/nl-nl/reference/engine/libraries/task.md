<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/libraries/task -->

task | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Bibliotheken](/docs/nl-nl/reference/engine/libraries)
2. /
3. [task](/docs/nl-nl/reference/engine/libraries/task)

Nederlands

Feedback

Engine-bibliotheek

task

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/libraries/task)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Functies

|

[spawn](#spawn) (functionOrThread :  [function](/docs/nl-nl/luau/functions)  | [coroutine](/docs/nl-nl/reference/engine/libraries/coroutine) , ... :  Variant ) :[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine)

 |
| --- | --- |
|

[defer](#defer) (functionOrThread :  [function](/docs/nl-nl/luau/functions)  | [coroutine](/docs/nl-nl/reference/engine/libraries/coroutine) , ... :  Variant ) :[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine)

 |
|

[delay](#delay) (duration :  [number](/docs/nl-nl/luau/numbers) , functionOrThread :  [function](/docs/nl-nl/luau/functions)  | [coroutine](/docs/nl-nl/reference/engine/libraries/coroutine) , ... :  Variant ) :[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine)

 |
|

[desynchronize](#desynchronize) () : ()

 |
|

[synchronize](#synchronize) () : ()

 |
|

[wait](#wait) (duration :  [number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[cancel](#cancel) (thread :  [coroutine](/docs/nl-nl/reference/engine/libraries/coroutine) ) : ()

 |

---

API-referentie

Functies

spawn

task.spawn (

functionOrThread :[function](/docs/nl-nl/luau/functions)  | [coroutine](/docs/nl-nl/reference/engine/libraries/coroutine) , ... : Variant

) :[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine)

Parameters

|

functionOrThread :[function](/docs/nl-nl/luau/functions)  | [coroutine](/docs/nl-nl/reference/engine/libraries/coroutine)

 |
|

... : Variant

 |

Teruggaves

[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine)

Codevoorbeelden

Taak Spawnen

```

local function greet(name, punctuation)

	print("Hallo, " .. name .. punctuation)

end

print("voor") --> voor

task.spawn(greet, "Roblox", "!") --> Hallo, Roblox!

print("na") --> na

-- Een opgeschorte coroutine kan ook met argumenten worden hervat.

local worker = coroutine.create(function(label)

	print("werknemer gestart met", label)

end)

task.spawn(worker, "taak 1") --> werknemer gestart met taak 1

print(coroutine.status(worker)) --> dood

```

Feedback geven

---

defer

task.defer (

functionOrThread :[function](/docs/nl-nl/luau/functions)  | [coroutine](/docs/nl-nl/reference/engine/libraries/coroutine) , ... : Variant

) :[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine)

Parameters

|

functionOrThread :[function](/docs/nl-nl/luau/functions)  | [coroutine](/docs/nl-nl/reference/engine/libraries/coroutine)

 |
|

... : Variant

 |

Teruggaves

[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine)

Codevoorbeelden

Taak Uitstellen

```

print("een") --> een

task.defer(function(message)

	print(message) --> uitgesteld

end, "uitgesteld")

task.spawn(function()

	print("twee") --> twee

end)

print("drie") --> drie

-- De uitgestelde functie wordt uitgevoerd nadat de huidige code is voltooid, dus deze print als laatste.

```

Feedback geven

---

delay

task.delay (

duration :[number](/docs/nl-nl/luau/numbers) , functionOrThread :[function](/docs/nl-nl/luau/functions)  | [coroutine](/docs/nl-nl/reference/engine/libraries/coroutine) , ... : Variant

) :[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine)

Parameters

|

duration :[number](/docs/nl-nl/luau/numbers)

 |
|

functionOrThread :[function](/docs/nl-nl/luau/functions)  | [coroutine](/docs/nl-nl/reference/engine/libraries/coroutine)

 |
|

... : Variant

 |

Teruggaves

[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine)

Codevoorbeelden

Taakvertraging

```

local scheduledAt = os.clock()

task.delay(1, function(message)

	local elapsed = os.clock() - scheduledAt

	print(message, elapsed >= 1) --> Uitgestelde hallo	true

end, "Uitgestelde hallo")

print("gepland") --> gepland

-- De geretourneerde thread kan worden geannuleerd voordat deze wordt uitgevoerd.

local cancelled = task.delay(2, function()

	print("nooit afgedrukt")

end)

task.cancel(cancelled)

```

Feedback geven

---

desynchronize

task.desynchronize () : ()

Teruggaves

()

Codevoorbeelden

Taak Desynchroniseren

```

-- Binnen een Script dat een afstammeling is van een Actor, desynchronize() hervat de

-- thread in de volgende parallelle fase, waar zware taken naast andere Actors kunnen draaien.

-- Buiten een Actor genereert het een fout, die pcall ons laat observeren.

local ok = pcall(task.desynchronize)

print(ok) --> false (wanneer dit script geen afstammeling is van een Actor)

```

Feedback geven

---

synchronize

task.synchronize () : ()

Teruggaves

()

Codevoorbeelden

Taak Synchroniseren

```

-- Binnen een Script dat een afstammeling is van een Actor, resumeert synchronize() de

-- thread in de volgende seriële fase, waar het veilig is om het datamodel te wijzigen.

-- Buiten een Actor genereert het een fout, die pcall ons laat observeren.

local ok = pcall(task.synchronize)

print(ok) --> false (wanneer dit script geen afstammeling is van een Actor)

```

Feedback geven

---

wait

task.wait (duration :[number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

duration :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

Taak Wacht

```

local elapsed = task.wait(1)

print(elapsed >= 1) --> true

-- Zonder argument hervat de thread bij de volgende Heartbeat.

local frameTime = task.wait()

print(frameTime < 1) --> true

```

Feedback geven

---

cancel

task.cancel (thread :[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine) ) : ()

Parameters

|

thread :[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine)

 |

Teruggaves

()

Codevoorbeelden

Taak Annuleren

```

local thread = task.delay(5, function()

	print("Hallo wereld!") -- nooit afgedrukt

end)

task.cancel(thread)

print(coroutine.status(thread)) --> dood

-- Het annuleren van de momenteel draaiende thread is niet toegestaan en genereert een fout.

local ok = pcall(task.cancel, coroutine.running())

print(ok) --> false

```

Feedback geven

---

Ga naar

▼

task

[Samenvatting](#summary)

[Functies](#summary-functions)

[Functies](#functions)

[spawn()](#spawn)

[defer()](#defer)

[delay()](#delay)

[desynchronize()](#desynchronize)

[synchronize()](#synchronize)

[wait()](#wait)

[cancel()](#cancel)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
