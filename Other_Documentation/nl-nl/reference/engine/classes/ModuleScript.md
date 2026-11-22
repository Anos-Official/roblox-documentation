<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/ModuleScript -->

ModuleScript | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [LuaSourceContainer](/docs/nl-nl/reference/engine/classes/LuaSourceContainer)
8. /
9. [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)

Nederlands

Feedback

Engine-klasse

ModuleScript

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/ModuleScript)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[LinkedSource](#LinkedSource) : ContentId

Verouderd

 |
| --- | --- |
|

[Source](#Source) :[string](/docs/nl-nl/luau/strings)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Eenvoudig ModuleScript Voorbeeld

```

-- Tabellen slaan meerdere waarden op in één variabele

local MyFunctions = {}

-- Voeg een paar functies toe aan de tabel

function MyFunctions.foo()

	print("Foo!")

end

function MyFunctions.bar()

	print("Bar!")

end

-- ModuleScripts moeten precies één waarde retourneren

return MyFunctions

```

Eenvoudig gebruik van ModuleScript

```

-- De require-functie krijgt een ModuleScript, en voert vervolgens

-- de code uit, wachtend tot het een enkele waarde retourneert.

local MyFunctions = require(script.Parent.MyFunctions)

-- Dit zijn enkele dummyfuncties gedefinieerd in een ander codevoorbeeld

MyFunctions.foo()

MyFunctions.bar()

```

---

API-referentie

Eigenschappen

LinkedSource

Verouderd

Details weergeven

---

Source

Parallel lezen

Mogelijkheden: PluginOrOpenCloud

ModuleScript.Source :[string](/docs/nl-nl/luau/strings)

Feedback geven

---

Ga naar

▼

ModuleScript

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Eigenschappen](#properties)

[LinkedSource](#LinkedSource)

[Source](#Source)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
