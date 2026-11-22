<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/ReflectionService -->

ReflectionService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [ReflectionService](/docs/nl-nl/reference/engine/classes/ReflectionService)

Nederlands

Feedback

Engine-klasse

ReflectionService

Niet maakbaar

Service

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/ReflectionService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[GetClass](#GetClass) (className :  [string](/docs/nl-nl/luau/strings) , filter :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ReflectedClass ?

 |
| --- | --- |
|

[GetClasses](#GetClasses) (filter :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : { ReflectedClass }

 |
|

[GetEventsOfClass](#GetEventsOfClass) (className :  [string](/docs/nl-nl/luau/strings) , filter :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : { ReflectedEvent }

 |
|

[GetMethodsOfClass](#GetMethodsOfClass) (className :  [string](/docs/nl-nl/luau/strings) , filter :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : { ReflectedMethod }

 |
|

[GetPropertiesOfClass](#GetPropertiesOfClass) (className :  [string](/docs/nl-nl/luau/strings) , filter :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : { ReflectedProperty }

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Overzicht van ReflectionService

```

local ReflectionService = game:GetService("ReflectionService")

-- Maak een SecurityCapabilities-object met alle mogelijkheden

local allCapabilities = SecurityCapabilities.new(table.unpack(Enum.SecurityCapability:GetEnumItems()))

-- Verkrijg alle klassen die toegankelijk zijn met alle mogelijkheden

local allClasses = ReflectionService:GetClasses({ Security = allCapabilities })

print("Totaal aantal klassen:", #allClasses)

-- Verkrijg een specifieke klasse

local partClass = ReflectionService:GetClass("Part")

if partClass then

	print("\nDeelklasse:")

	print("  Naam:", partClass.Name)

	print("  Superklasse:", partClass.Superclass and tostring(partClass.Superclass) or "geen")

end

-- Verkrijg de eerste 5 eigenschappen van een klasse

local properties = ReflectionService:GetPropertiesOfClass("Part", { Security = allCapabilities })

print("\nEigenschappen van het deel:", #properties)

for i = 1, math.min(5, #properties) do

	print("  -", properties[i].Name)

end

```

---

API-referentie

Methoden

GetClass

ReflectionService:GetClass (

className :[string](/docs/nl-nl/luau/strings) , filter :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

) : ReflectedClass ?

Parameters

|

className :[string](/docs/nl-nl/luau/strings)

 |
|

filter :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Standaardwaarde: nil |

Teruggaves

ReflectedClass ?

Feedback geven

---

GetClasses

ReflectionService:GetClasses (filter :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : { ReflectedClass }

Parameters

|

filter :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Standaardwaarde: nil |

Teruggaves

{ ReflectedClass }

Feedback geven

---

GetEventsOfClass

ReflectionService:GetEventsOfClass (

className :[string](/docs/nl-nl/luau/strings) , filter :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

) : { ReflectedEvent }

Parameters

|

className :[string](/docs/nl-nl/luau/strings)

 |
|

filter :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Standaardwaarde: nil |

Teruggaves

{ ReflectedEvent }

Feedback geven

---

GetMethodsOfClass

ReflectionService:GetMethodsOfClass (

className :[string](/docs/nl-nl/luau/strings) , filter :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

) : { ReflectedMethod }

Parameters

|

className :[string](/docs/nl-nl/luau/strings)

 |
|

filter :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Standaardwaarde: nil |

Teruggaves

{ ReflectedMethod }

Feedback geven

---

GetPropertiesOfClass

ReflectionService:GetPropertiesOfClass (

className :[string](/docs/nl-nl/luau/strings) , filter :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

) : { ReflectedProperty }

Parameters

|

className :[string](/docs/nl-nl/luau/strings)

 |
|

filter :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Standaardwaarde: nil |

Teruggaves

{ ReflectedProperty }

Feedback geven

---

Ga naar

▼

ReflectionService

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[GetClass()](#GetClass)

[GetClasses()](#GetClasses)

[GetEventsOfClass()](#GetEventsOfClass)

[GetMethodsOfClass()](#GetMethodsOfClass)

[GetPropertiesOfClass()](#GetPropertiesOfClass)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
