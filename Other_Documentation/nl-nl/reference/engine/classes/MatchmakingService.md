<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/MatchmakingService -->

MatchmakingService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [MatchmakingService](/docs/nl-nl/reference/engine/classes/MatchmakingService)

Nederlands

Feedback

Engine-klasse

MatchmakingService

Niet maakbaar

Service

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/MatchmakingService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[GetServerAttribute](#GetServerAttribute) (name :  [string](/docs/nl-nl/luau/strings) ) :[Tuple](/docs/nl-nl/luau/tuples)

 |
| --- | --- |
|

[InitializeServerAttributesForStudio](#InitializeServerAttributesForStudio) (serverAttributes :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[Tuple](/docs/nl-nl/luau/tuples)

 |
|

[SetServerAttribute](#SetServerAttribute) (name :  [string](/docs/nl-nl/luau/strings) , value :  Variant ) :[Tuple](/docs/nl-nl/luau/tuples)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Methoden

GetServerAttribute

Mogelijkheden: Basic

MatchmakingService:GetServerAttribute (name :[string](/docs/nl-nl/luau/strings) ) :[Tuple](/docs/nl-nl/luau/tuples)

Parameters

|

name :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Feedback geven

---

InitializeServerAttributesForStudio

Mogelijkheden: Basic

MatchmakingService:InitializeServerAttributesForStudio (serverAttributes :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[Tuple](/docs/nl-nl/luau/tuples)

Parameters

|

serverAttributes :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Feedback geven

---

SetServerAttribute

Mogelijkheden: Basic

MatchmakingService:SetServerAttribute (

name :[string](/docs/nl-nl/luau/strings) , value : Variant

) :[Tuple](/docs/nl-nl/luau/tuples)

Parameters

|

name :[string](/docs/nl-nl/luau/strings)

 |
|

value : Variant

 |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Codevoorbeelden

Voorbeeld van MatchmakingService

```

local MatchmakingService = game:GetService("MatchmakingService")

local RunService = game:GetService("RunService")

if RunService:IsStudio() then

	-- Stelt initiële attributen en schema in voor testen

	MatchmakingService:InitializeServerAttributesForStudio({

		Level = "Geavanceerd",

		Elo = 123.456,

		TrainingMode = true

	})

end

-- Haalt het Level attribuut op

local currentLevel, errorMessage = MatchmakingService:GetServerAttribute("Level")

if errorMessage then

	warn(errorMessage)

else

	print("Huidig niveau: " .. currentLevel)

end

-- Werkt de waarde van het Level attribuut bij naar Geavanceerd

local success, errorMessage = MatchmakingService:SetServerAttribute("Level", "Geavanceerd")

if not success then

	warn("Kon serverattribuut [Level] niet bijwerken naar [Geavanceerd] vanwege fout: " .. errorMessage)

else

	print("[Level] succesvol ingesteld op [Geavanceerd]")

end

```

Feedback geven

---

Ga naar

▼

MatchmakingService

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[GetServerAttribute()](#GetServerAttribute)

[InitializeServerAttributesForStudio()](#InitializeServerAttributesForStudio)

[SetServerAttribute()](#SetServerAttribute)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
