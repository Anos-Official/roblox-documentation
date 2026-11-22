<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Translator -->

Translator | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [Translator](/docs/nl-nl/reference/engine/classes/Translator)

Nederlands

Feedback

Engine-klasse

Translator

Niet maakbaar

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Translator)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[LocaleId](#LocaleId) :[string](/docs/nl-nl/luau/strings)

 |
| --- | --- |

Methoden

|

[FormatByKey](#FormatByKey) (key :  [string](/docs/nl-nl/luau/strings) , args :  Variant ) :[string](/docs/nl-nl/luau/strings)

 |
|

[Translate](#Translate) (context :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) , text :  [string](/docs/nl-nl/luau/strings) ) :[string](/docs/nl-nl/luau/strings)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

LocaleId

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Basic

Translator.LocaleId :[string](/docs/nl-nl/luau/strings)

Feedback geven

---

Methoden

FormatByKey

Mogelijkheden: Basic

Translator:FormatByKey (

key :[string](/docs/nl-nl/luau/strings) , args : Variant

) :[string](/docs/nl-nl/luau/strings)

Parameters

|

key :[string](/docs/nl-nl/luau/strings)

 |
|

args : Variant

 |

Teruggaves

[string](/docs/nl-nl/luau/strings)

Feedback geven

---

Translate

Mogelijkheden: Basic

Translator:Translate (

context :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) , text :[string](/docs/nl-nl/luau/strings)

) :[string](/docs/nl-nl/luau/strings)

Parameters

|

context :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
|

text :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[string](/docs/nl-nl/luau/strings)

Codevoorbeelden

Vertalen

```

local Players = game:GetService("Players")

local LocalizationService = game:GetService("LocalizationService")

local success, translator = pcall(function()

	return LocalizationService:GetTranslatorForPlayerAsync(Players.LocalPlayer)

end)

if success then

	local trans = translator:Translate(workspace.ComputerScreen.SurfaceGui.TextLabel, "Scherm")

	print(trans)

else

	warn("Kan vertaler voor speler niet laden!")

end

```

Feedback geven

---

Ga naar

▼

Translator

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[LocaleId](#LocaleId)

[Methoden](#methods)

[FormatByKey()](#FormatByKey)

[Translate()](#Translate)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
