<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/GetTextBoundsParams -->

GetTextBoundsParams | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [GetTextBoundsParams](/docs/nl-nl/reference/engine/classes/GetTextBoundsParams)

Nederlands

Feedback

Engine-klasse

GetTextBoundsParams

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/GetTextBoundsParams)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Font](#Font) :[Font](/docs/nl-nl/reference/engine/datatypes/Font)

 |
| --- | --- |
|

[RichText](#RichText) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[Size](#Size) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Text](#Text) :[string](/docs/nl-nl/luau/strings)

 |
|

[Width](#Width) :[number](/docs/nl-nl/luau/numbers)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Tekstgrootte Meten

```

local TextService = game:GetService("TextService")

-- Verklaar parameters

local params = Instance.new("GetTextBoundsParams")

params.Text = "Hallo wereld!"

params.Font = Font.new("rbxasset://fonts/families/GrenzeGotisch.json", Enum.FontWeight.Thin)

params.Size = 20

params.Width = 200

local success, bounds = pcall(function()

	return TextService:GetTextBoundsAsync(params)

end)

if success then

	print(bounds)

end

```

---

API-referentie

Eigenschappen

Font

Parallel lezen

Mogelijkheden: UI

GetTextBoundsParams.Font :[Font](/docs/nl-nl/reference/engine/datatypes/Font)

Feedback geven

---

RichText

Parallel lezen

Mogelijkheden: UI

GetTextBoundsParams.RichText :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Size

Parallel lezen

Mogelijkheden: UI

GetTextBoundsParams.Size :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Text

Parallel lezen

Mogelijkheden: UI

GetTextBoundsParams.Text :[string](/docs/nl-nl/luau/strings)

Feedback geven

---

Width

Parallel lezen

Mogelijkheden: UI

GetTextBoundsParams.Width :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Ga naar

▼

GetTextBoundsParams

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Eigenschappen](#properties)

[Font](#Font)

[RichText](#RichText)

[Size](#Size)

[Text](#Text)

[Width](#Width)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
