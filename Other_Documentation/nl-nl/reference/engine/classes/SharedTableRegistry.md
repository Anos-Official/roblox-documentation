<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/SharedTableRegistry -->

SharedTableRegistry | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [SharedTableRegistry](/docs/nl-nl/reference/engine/classes/SharedTableRegistry)

Nederlands

Feedback

Engine-klasse

SharedTableRegistry

Niet maakbaar

Service

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/SharedTableRegistry)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[GetSharedTable](#GetSharedTable) (name :  [string](/docs/nl-nl/luau/strings) ) :[SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable)

 |
| --- | --- |
|

[SetSharedTable](#SetSharedTable) (name :  [string](/docs/nl-nl/luau/strings) , st :  [SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable) ? ) : ()

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Methoden

GetSharedTable

Parallel schrijven

Mogelijkheden: ScriptGlobals

SharedTableRegistry:GetSharedTable (name :[string](/docs/nl-nl/luau/strings) ) :[SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable)

Parameters

|

name :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable)

Codevoorbeelden

Krijg Gedeelde Tabel

```

local SharedTableRegistry = game:GetService("SharedTableRegistry")

local st = SharedTableRegistry:GetSharedTable("MyData")

```

Feedback geven

---

SetSharedTable

Parallel schrijven

Mogelijkheden: ScriptGlobals

SharedTableRegistry:SetSharedTable (

name :[string](/docs/nl-nl/luau/strings) , st :[SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable) ?

) : ()

Parameters

|

name :[string](/docs/nl-nl/luau/strings)

 |
|

st :[SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable) ?

 |

Teruggaves

()

Codevoorbeelden

Gedeelde Tabel Instellen

```

local SharedTableRegistry = game:GetService("SharedTableRegistry")

-- Registreer een SharedTable met de naam "MyData":

local st = SharedTable.new({1, 2, 3})

SharedTableRegistry:SetSharedTable("MyData", st)

-- Deregistreer de SharedTable met de naam "MyData":

SharedTableRegistry:SetSharedTable("MyData", nil)

```

Feedback geven

---

Ga naar

▼

SharedTableRegistry

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[GetSharedTable()](#GetSharedTable)

[SetSharedTable()](#SetSharedTable)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
