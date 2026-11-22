<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/UIScale -->

UIScale | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [UIBase](/docs/nl-nl/reference/engine/classes/UIBase)
8. /
9. [UIComponent](/docs/nl-nl/reference/engine/classes/UIComponent)
10. /
11. [UIScale](/docs/nl-nl/reference/engine/classes/UIScale)

Nederlands

Feedback

Engine-klasse

UIScale

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/UIScale)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Scale](#Scale) :[number](/docs/nl-nl/luau/numbers)

 |
| --- | --- |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

UI Schaal Demo

```

-- Leg de afbeeldingen in een lijst

Instance.new("UIListLayout", script.Parent).SortOrder = Enum.SortOrder.LayoutOrder

-- Maak enkele afbeeldingen van verschillende groottes met behulp van UIScale-objecten

for size = 0.2, 1.5, 0.2 do

	local image = Instance.new("ImageLabel")

	image.Image = "rbxassetid://284402752" -- een afbeelding van een slot

	image.Parent = script.Parent

	image.Size = UDim2.new(0, 100, 0, 100)

	-- Schaal de afbeelding door een UIScale toe te voegen met de grootte

	--  Opmerking: dit is een verkorte versie aangezien we geen referentie naar de UIScale nodig hebben

	Instance.new("UIScale", image).Scale = size

end

```

---

API-referentie

Eigenschappen

Scale

Parallel lezen

Mogelijkheden: UI

UIScale.Scale :[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

UI Schaal Demo

```

-- Leg de afbeeldingen in een lijst

Instance.new("UIListLayout", script.Parent).SortOrder = Enum.SortOrder.LayoutOrder

-- Maak enkele afbeeldingen van verschillende groottes met behulp van UIScale-objecten

for size = 0.2, 1.5, 0.2 do

	local image = Instance.new("ImageLabel")

	image.Image = "rbxassetid://284402752" -- een afbeelding van een slot

	image.Parent = script.Parent

	image.Size = UDim2.new(0, 100, 0, 100)

	-- Schaal de afbeelding door een UIScale toe te voegen met de grootte

	--  Opmerking: dit is een verkorte versie aangezien we geen referentie naar de UIScale nodig hebben

	Instance.new("UIScale", image).Scale = size

end

```

Feedback geven

---

Ga naar

▼

UIScale

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Eigenschappen](#properties)

[Scale](#Scale)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
