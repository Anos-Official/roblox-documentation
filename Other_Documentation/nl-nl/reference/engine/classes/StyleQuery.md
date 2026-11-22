<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/StyleQuery -->

StyleQuery | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [StyleQuery](/docs/nl-nl/reference/engine/classes/StyleQuery)

Nederlands

Feedback

Engine-klasse

StyleQuery

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/StyleQuery)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[IsActive](#IsActive) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |

Methoden

|

[GetCondition](#GetCondition) (name :  [string](/docs/nl-nl/luau/strings) ) : Variant

 |
|

[GetConditions](#GetConditions) () :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |
|

[SetCondition](#SetCondition) (name :  [string](/docs/nl-nl/luau/strings) , value :  Variant ) : ()

 |
|

[SetConditions](#SetConditions) (conditions :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

IsActive

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: UI

StyleQuery.IsActive :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Methoden

GetCondition

Mogelijkheden: UI

StyleQuery:GetCondition (name :[string](/docs/nl-nl/luau/strings) ) : Variant

Parameters

|

name :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

Variant

Feedback geven

---

GetConditions

Mogelijkheden: UI

StyleQuery:GetConditions () :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Teruggaves

[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Feedback geven

---

SetCondition

Mogelijkheden: UI

StyleQuery:SetCondition (

name :[string](/docs/nl-nl/luau/strings) , value : Variant

) : ()

Parameters

|

name :[string](/docs/nl-nl/luau/strings)

 |
|

value : Variant

 |

Teruggaves

()

Codevoorbeelden

Stel Voorwaarde In

```

local styleQuery = Instance.new("StyleQuery")

styleQuery:SetCondition("MaxSize", Vector2.new(200, math.huge))

```

Feedback geven

---

SetConditions

Mogelijkheden: UI

StyleQuery:SetConditions (conditions :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

Parameters

|

conditions :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |

Teruggaves

()

Codevoorbeelden

Voorwaarden Instellen

```

local styleQuery = Instance.new("StyleQuery")

styleQuery:SetConditions({

	["AspectRatioRange"] = NumberRange.new(0, 1),

	["MaxSize"] = Vector2.new(200, math.huge),

})

```

Feedback geven

---

Ga naar

▼

StyleQuery

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[IsActive](#IsActive)

[Methoden](#methods)

[GetCondition()](#GetCondition)

[GetConditions()](#GetConditions)

[SetCondition()](#SetCondition)

[SetConditions()](#SetConditions)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
