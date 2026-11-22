<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/datatypes/SharedTable -->

SharedTable | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Gegevenstypen](/docs/nl-nl/reference/engine/datatypes)
2. /
3. [SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable)

Nederlands

Feedback

Engine-gegevenstype

SharedTable

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/datatypes/SharedTable)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Constructors

|

[new](#new) ()

 |
| --- | --- |
|

[new](#new-t) (t :  [table](/docs/nl-nl/luau/tables) )

 |

Functies

|

[clear](#clear) (st :  [SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable) ) : ()

 |
|

[clone](#clone) (st :  [SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable) , deep :  [boolean](/docs/nl-nl/luau/booleans) ? ) :[SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable)

 |
|

[cloneAndFreeze](#cloneAndFreeze) (st :  [SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable) , deep :  [boolean](/docs/nl-nl/luau/booleans) ? ) :[SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable)

 |
|

[increment](#increment) (st :  [SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable) , key :  [string](/docs/nl-nl/luau/strings)  | [number](/docs/nl-nl/luau/numbers) , delta :  [number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[isFrozen](#isFrozen) (st :  [SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable) ) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[size](#size) (st :  [SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[update](#update) (st :  [SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable) , key :  [string](/docs/nl-nl/luau/strings)  | [number](/docs/nl-nl/luau/numbers) , f :  [function](/docs/nl-nl/luau/functions) ) : ()

 |

Codevoorbeelden

Toegang tot Elementen

```

local st = SharedTable.new()

st[1] = "a"

st["x"] = true

st.y = 5

assert(st[1] == "a")

assert(st["x"] == true)

assert(st.x == true)

assert(st["y"] == 5)

assert(st.y == 5)

-- true is geen geldige SharedTable sleutel, dus het proberen om die sleutel

-- in te stellen:

assert(not pcall(function() st[true] = 100 end))

-- Een functie is geen geldige SharedTable waarde, dus het proberen om een

-- waarde aan een functie in te stellen mislukt:

assert(not pcall(function() st["f"] = function() end end))

```

Element Iteratie

```

local st = SharedTable.new({"a", "b", "c"})

for k, v in SharedTable.clone(st, false) do

	print(k, ": ", v)

end

for k, v in st do

	print(k, ": ", v)

end

```

---

API-referentie

Constructors

new

SharedTable.new ()

Feedback geven

---

new

SharedTable.new (t :[table](/docs/nl-nl/luau/tables) )

Parameters

|

t :[table](/docs/nl-nl/luau/tables)

 |

Feedback geven

---

Functies

clear

SharedTable.clear (st :[SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable) ) : ()

Parameters

|

st :[SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable)

 |

Teruggaves

()

Feedback geven

---

clone

SharedTable.clone (

st :[SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable) , deep :[boolean](/docs/nl-nl/luau/booleans) ?

) :[SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable)

Parameters

|

st :[SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable)

 |
|

deep :[boolean](/docs/nl-nl/luau/booleans) ?

Standaardwaarde: false |

Teruggaves

[SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable)

Feedback geven

---

cloneAndFreeze

SharedTable.cloneAndFreeze (

st :[SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable) , deep :[boolean](/docs/nl-nl/luau/booleans) ?

) :[SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable)

Parameters

|

st :[SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable)

 |
|

deep :[boolean](/docs/nl-nl/luau/booleans) ?

Standaardwaarde: false |

Teruggaves

[SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable)

Feedback geven

---

increment

SharedTable.increment (

st :[SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable) , key :[string](/docs/nl-nl/luau/strings)  | [number](/docs/nl-nl/luau/numbers) , delta :[number](/docs/nl-nl/luau/numbers)

) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

st :[SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable)

 |
|

key :[string](/docs/nl-nl/luau/strings)  | [number](/docs/nl-nl/luau/numbers)

 |
|

delta :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

isFrozen

SharedTable.isFrozen (st :[SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable) ) :[boolean](/docs/nl-nl/luau/booleans)

Parameters

|

st :[SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable)

 |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

size

SharedTable.size (st :[SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable) ) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

st :[SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

update

SharedTable.update (

st :[SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable) , key :[string](/docs/nl-nl/luau/strings)  | [number](/docs/nl-nl/luau/numbers) , f :[function](/docs/nl-nl/luau/functions)

) : ()

Parameters

|

st :[SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable)

 |
|

key :[string](/docs/nl-nl/luau/strings)  | [number](/docs/nl-nl/luau/numbers)

 |
|

f :[function](/docs/nl-nl/luau/functions)

 |

Teruggaves

()

Feedback geven

---

Ga naar

▼

SharedTable

[Samenvatting](#summary)

[Constructors](#summary-constructors)

[Functies](#summary-functions)

[Constructors](#constructors)

[new()](#new)

[Functies](#functions)

[clear()](#clear)

[clone()](#clone)

[cloneAndFreeze()](#cloneAndFreeze)

[increment()](#increment)

[isFrozen()](#isFrozen)

[size()](#size)

[update()](#update)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
