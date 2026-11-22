<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/libraries/coroutine -->

coroutine | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Bibliotheken](/docs/nl-nl/reference/engine/libraries)
2. /
3. [coroutine](/docs/nl-nl/reference/engine/libraries/coroutine)

Nederlands

Feedback

Engine-bibliotheek

coroutine

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/libraries/coroutine)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Functies

|

[close](#close) (co :  [coroutine](/docs/nl-nl/reference/engine/libraries/coroutine) ) :[boolean](/docs/nl-nl/luau/booleans) , Variant <[string](/docs/nl-nl/luau/strings) , () >

 |
| --- | --- |
|

[create](#create) (f :  [function](/docs/nl-nl/luau/functions) ) :[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine)

 |
|

[finally](#finally) (co :  [coroutine](/docs/nl-nl/reference/engine/libraries/coroutine) , callback :  Variant )

 |
|

[isyieldable](#isyieldable) () :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[resume](#resume) (co :  [coroutine](/docs/nl-nl/reference/engine/libraries/coroutine) , ... :  Variant ) :[boolean](/docs/nl-nl/luau/booleans) , Variant <[Tuple](/docs/nl-nl/luau/tuples) , [string](/docs/nl-nl/luau/strings) >

 |
|

[running](#running) () :[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine)

 |
|

[status](#status) (co :  [coroutine](/docs/nl-nl/reference/engine/libraries/coroutine) ) :[string](/docs/nl-nl/luau/strings)

 |
|

[wrap](#wrap) (f :  [function](/docs/nl-nl/luau/functions) ) :[function](/docs/nl-nl/luau/functions)

 |
|

[yield](#yield) (... :  [Tuple](/docs/nl-nl/luau/tuples) ) :[Tuple](/docs/nl-nl/luau/tuples) < Variant >

 |

---

API-referentie

Functies

close

coroutine.close (co :[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine) ) :[boolean](/docs/nl-nl/luau/booleans) , Variant <[string](/docs/nl-nl/luau/strings) , () >

Parameters

|

co :[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine)

 |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans) , Variant <[string](/docs/nl-nl/luau/strings) , () >

Codevoorbeelden

##### Coroutine Sluiten

Feedback geven

---

create

coroutine.create (f :[function](/docs/nl-nl/luau/functions) ) :[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine)

Parameters

|

f :[function](/docs/nl-nl/luau/functions)

 |

Teruggaves

[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine)

Codevoorbeelden

##### Coroutine Aanmaken

Feedback geven

---

finally

coroutine.finally (

co :[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine) , callback : Variant )

Parameters

|

co :[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine)

 |
|

callback : Variant

 |

Codevoorbeelden

Coroutine Eindelijk

```

local function observe(co, label)

	coroutine.finally(co, function(status, ...)

		print(label, status, ...)

	end)

end

local finishing = coroutine.create(function()

	return "result"

end)

observe(finishing, "finishing") --> finishing voltooid resultaat

coroutine.resume(finishing)

local failing = coroutine.create(function()

	error("boom", 0)

end)

observe(failing, "failing") --> falen fout boom

coroutine.resume(failing)

local cancelled = coroutine.create(function()

	coroutine.yield()

end)

coroutine.resume(cancelled)

observe(cancelled, "cancelled") --> geannuleerd geannuleerd

coroutine.close(cancelled)

```

Feedback geven

---

isyieldable

coroutine.isyieldable () :[boolean](/docs/nl-nl/luau/booleans)

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

##### Coroutine Is Yieldable

Feedback geven

---

resume

coroutine.resume (

co :[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine) , ... : Variant

) :[boolean](/docs/nl-nl/luau/booleans) , Variant <[Tuple](/docs/nl-nl/luau/tuples) , [string](/docs/nl-nl/luau/strings) >

Parameters

|

co :[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine)

 |
|

... : Variant

 |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans) , Variant <[Tuple](/docs/nl-nl/luau/tuples) , [string](/docs/nl-nl/luau/strings) >

Codevoorbeelden

##### Coroutine Hervatten

Feedback geven

---

running

coroutine.running () :[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine)

Teruggaves

[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine)

Codevoorbeelden

##### Coroutine Uitvoering

Feedback geven

---

status

coroutine.status (co :[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine) ) :[string](/docs/nl-nl/luau/strings)

Parameters

|

co :[coroutine](/docs/nl-nl/reference/engine/libraries/coroutine)

 |

Teruggaves

[string](/docs/nl-nl/luau/strings)

Codevoorbeelden

##### Coroutine Status

Feedback geven

---

wrap

coroutine.wrap (f :[function](/docs/nl-nl/luau/functions) ) :[function](/docs/nl-nl/luau/functions)

Parameters

|

f :[function](/docs/nl-nl/luau/functions)

 |

Teruggaves

[function](/docs/nl-nl/luau/functions)

Codevoorbeelden

##### Coroutine Wrap

Feedback geven

---

yield

coroutine.yield (... :[Tuple](/docs/nl-nl/luau/tuples) ) :[Tuple](/docs/nl-nl/luau/tuples) < Variant >

Parameters

|

... :[Tuple](/docs/nl-nl/luau/tuples)

 |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples) < Variant >

Codevoorbeelden

##### Coroutine Yield

Feedback geven

---

Ga naar

▼

coroutine

[Samenvatting](#summary)

[Functies](#summary-functions)

[Functies](#functions)

[close()](#close)

[create()](#create)

[finally()](#finally)

[isyieldable()](#isyieldable)

[resume()](#resume)

[running()](#running)

[status()](#status)

[wrap()](#wrap)

[yield()](#yield)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
