<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/LocalizationService -->

LocalizationService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [LocalizationService](/docs/nl-nl/reference/engine/classes/LocalizationService)

Nederlands

Feedback

Engine-klasse

LocalizationService

Niet maakbaar

Service

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/LocalizationService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[RobloxLocaleId](#RobloxLocaleId) :[string](/docs/nl-nl/luau/strings)

 |
| --- | --- |
|

[SystemLocaleId](#SystemLocaleId) :[string](/docs/nl-nl/luau/strings)

 |

Methoden

|

[GetCorescriptLocalizations](#GetCorescriptLocalizations) () : Instances

 |
|

[GetCountryRegionForPlayerAsync](#GetCountryRegionForPlayerAsync) (player :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[string](/docs/nl-nl/luau/strings)

 |
|

[GetTableEntries](#GetTableEntries) (instance :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[GetTranslatorForLocaleAsync](#GetTranslatorForLocaleAsync) (locale :  [string](/docs/nl-nl/luau/strings) ) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
|

[GetTranslatorForPlayer](#GetTranslatorForPlayer) (player :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Verouderd

 |
|

[GetTranslatorForPlayerAsync](#GetTranslatorForPlayerAsync) (player :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

RobloxLocaleId

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Basic

LocalizationService.RobloxLocaleId :[string](/docs/nl-nl/luau/strings)

Feedback geven

---

SystemLocaleId

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Basic

LocalizationService.SystemLocaleId :[string](/docs/nl-nl/luau/strings)

Feedback geven

---

Methoden

GetCorescriptLocalizations

Mogelijkheden: Basic

LocalizationService:GetCorescriptLocalizations () : Instances

Teruggaves

Instances

Feedback geven

---

GetCountryRegionForPlayerAsync

Opbrengst

Mogelijkheden: Basic

LocalizationService:GetCountryRegionForPlayerAsync (player :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[string](/docs/nl-nl/luau/strings)

Parameters

|

player :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Teruggaves

[string](/docs/nl-nl/luau/strings)

Codevoorbeelden

Land-/Regio-code voor een Speler Krijgen

```

local LocalizationService = game:GetService("LocalizationService")

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local result, code = pcall(LocalizationService.GetCountryRegionForPlayerAsync, LocalizationService, player)

if result and code == "CA" then

	print("Hallo, vriend uit Canada!")

else

	print("GetCountryRegionForPlayerAsync is mislukt: " .. code)

end

```

Feedback geven

---

GetTableEntries

Mogelijkheden: Basic

LocalizationService:GetTableEntries (instance :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

Parameters

|

instance :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Standaardwaarde: nil |

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

GetTranslatorForLocaleAsync

Opbrengst

Mogelijkheden: Basic

LocalizationService:GetTranslatorForLocaleAsync (locale :[string](/docs/nl-nl/luau/strings) ) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Parameters

|

locale :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Codevoorbeelden

Een vertaler krijgen en gebruiken voor een locale

```

local LocalizationService = game:GetService("LocalizationService")

local textLabel = script.Parent

local success, translator = pcall(function()

	return LocalizationService:GetTranslatorForLocaleAsync("fr")

end)

if success then

	local result = translator:Translate(textLabel, "Hallo Wereld!")

	print("Hallo in het Frans: " .. result)

else

	print("GetTranslatorForLocaleAsync is mislukt: " .. translator)

end

```

Feedback geven

---

GetTranslatorForPlayer

Verouderd

Details weergeven

---

GetTranslatorForPlayerAsync

Opbrengst

Mogelijkheden: Basic

LocalizationService:GetTranslatorForPlayerAsync (player :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Parameters

|

player :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Teruggaves

[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Codevoorbeelden

Een vertaler voor een speler krijgen en gebruiken

```

local LocalizationService = game:GetService("LocalizationService")

local Players = game:GetService("Players")

local textLabel = script.Parent

local success, translator = pcall(function()

	return LocalizationService:GetTranslatorForPlayerAsync(Players.LocalPlayer)

end)

if success then

	local result = translator:Translate(textLabel, "Hallo Wereld!")

	print(result)

else

	print("GetTranslatorForPlayerAsync is mislukt: " .. translator)

end

```

Feedback geven

---

Ga naar

▼

LocalizationService

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[RobloxLocaleId](#RobloxLocaleId)

[SystemLocaleId](#SystemLocaleId)

[Methoden](#methods)

[GetCorescriptLocalizations()](#GetCorescriptLocalizations)

[GetCountryRegionForPlayerAsync()](#GetCountryRegionForPlayerAsync)

[GetTableEntries()](#GetTableEntries)

[GetTranslatorForLocaleAsync()](#GetTranslatorForLocaleAsync)

[GetTranslatorForPlayer()](#GetTranslatorForPlayer)

[GetTranslatorForPlayerAsync()](#GetTranslatorForPlayerAsync)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
