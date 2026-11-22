<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/ImageLabel -->

ImageLabel | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [GuiBase](/docs/nl-nl/reference/engine/classes/GuiBase)
8. /
9. [GuiBase2d](/docs/nl-nl/reference/engine/classes/GuiBase2d)
10. /
11. [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)
12. /
13. [GuiLabel](/docs/nl-nl/reference/engine/classes/GuiLabel)
14. /
15. [ImageLabel](/docs/nl-nl/reference/engine/classes/ImageLabel)

Nederlands

Feedback

Engine-klasse

ImageLabel

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/ImageLabel)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Image](#Image) : ContentId

 |
| --- | --- |
|

[ImageColor3](#ImageColor3) :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

 |
|

[ImageContent](#ImageContent) :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

 |
|

[ImageRectOffset](#ImageRectOffset) :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

[ImageRectSize](#ImageRectSize) :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

[ImageTransparency](#ImageTransparency) :[number](/docs/nl-nl/luau/numbers)

 |
|

[IsLoaded](#IsLoaded) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[ResampleMode](#ResampleMode) :[Enum.ResamplerMode](/docs/nl-nl/reference/engine/enums/ResamplerMode)

 |
|

[ScaleType](#ScaleType) :[Enum.ScaleType](/docs/nl-nl/reference/engine/enums/ScaleType)

 |
|

[SliceCenter](#SliceCenter) :[Rect](/docs/nl-nl/reference/engine/datatypes/Rect)

 |
|

[SliceScale](#SliceScale) :[number](/docs/nl-nl/luau/numbers)

 |
|

[TileSize](#TileSize) :[UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)

 |

Overgenomen leden

51  overgenomen van [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)

12  overgenomen van [GuiBase2d](/docs/nl-nl/reference/engine/classes/GuiBase2d)

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

Image

Parallel lezen

Mogelijkheden: UI

ImageLabel.Image : ContentId

Feedback geven

---

ImageColor3

Parallel lezen

Mogelijkheden: UI

ImageLabel.ImageColor3 :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

Feedback geven

---

ImageContent

Parallel lezen

Mogelijkheden: UI

ImageLabel.ImageContent :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

Feedback geven

---

ImageRectOffset

Parallel lezen

Mogelijkheden: UI

ImageLabel.ImageRectOffset :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Feedback geven

---

ImageRectSize

Parallel lezen

Mogelijkheden: UI

ImageLabel.ImageRectSize :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Feedback geven

---

ImageTransparency

Parallel lezen

Mogelijkheden: UI

ImageLabel.ImageTransparency :[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

Oscilleer ImageTransparency

```

local RunService = game:GetService("RunService")

local imageLabel = script.Parent

local function onRenderStep()

	-- Oscilleer ImageTransparency van 0 tot 1 met behulp van een sinusgolf

	imageLabel.ImageTransparency = math.sin(workspace.DistributedGameTime * math.pi) * 0.5 + 0.5

end

RunService.RenderStepped:Connect(onRenderStep)

```

Feedback geven

---

IsLoaded

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: UI

ImageLabel.IsLoaded :[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

Afbeelding Laadtijd

```

local imageLabel = script.Parent

local startTime = workspace.DistributedGameTime

-- Wacht tot de afbeelding is geladen

while not imageLabel.IsLoaded do

	task.wait()

end

-- Meet en toon hoe lang het heeft geduurd om te laden

local deltaTime = workspace.DistributedGameTime - startTime

print(("Afbeelding geladen in %.3f seconden"):format(deltaTime))

```

Feedback geven

---

ResampleMode

Parallel lezen

Mogelijkheden: UI

ImageLabel.ResampleMode :[Enum.ResamplerMode](/docs/nl-nl/reference/engine/enums/ResamplerMode)

Feedback geven

---

ScaleType

Parallel lezen

Mogelijkheden: UI

ImageLabel.ScaleType :[Enum.ScaleType](/docs/nl-nl/reference/engine/enums/ScaleType)

Feedback geven

---

SliceCenter

Parallel lezen

Mogelijkheden: UI

ImageLabel.SliceCenter :[Rect](/docs/nl-nl/reference/engine/datatypes/Rect)

Feedback geven

---

SliceScale

Parallel lezen

Mogelijkheden: UI

ImageLabel.SliceScale :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

TileSize

Parallel lezen

Mogelijkheden: UI

ImageLabel.TileSize :[UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)

Codevoorbeelden

Afbeelding SchaalType Demo

```

local imageLabel = script.Parent

-- Stel de bronafbeelding in op een 64x64 hangslot

imageLabel.Image = "rbxassetid://284402752"

imageLabel.BackgroundTransparency = 0

imageLabel.BackgroundColor3 = Color3.new(1, 1, 1) -- Wit

imageLabel.ImageColor3 = Color3.new(0, 0, 0) -- Zwart

local function resizeInACircle()

	for theta = 0, 2, 0.02 do

		imageLabel.Size =

			UDim2.new(0, 100 + math.cos(theta * 2 * math.pi) * 50, 0, 100 + math.sin(theta * 2 * math.pi) * 50)

		task.wait()

	end

end

while true do

	-- Rekken rekt eenvoudig de bronafbeelding om te passen

	-- in de ruimte van het UI-element

	imageLabel.ScaleType = Enum.ScaleType.Stretch

	resizeInACircle()

	-- Tegelen zal de bronafbeelding meerdere keren weergeven

	-- genoeg om de ruimte van het UI-element te vullen

	imageLabel.ScaleType = Enum.ScaleType.Tile

	imageLabel.TileSize = UDim2.new(0, 64, 0, 64)

	resizeInACircle()

	-- Snijden zal de afbeelding omzetten in een negen-slice UI.

	imageLabel.ScaleType = Enum.ScaleType.Slice

	imageLabel.SliceCenter = Rect.new(30, 30, 34, 34)

	resizeInACircle()

end

```

Feedback geven

---

Ga naar

▼

ImageLabel

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Eigenschappen](#properties)

[Image](#Image)

[ImageColor3](#ImageColor3)

[ImageContent](#ImageContent)

[ImageRectOffset](#ImageRectOffset)

[ImageRectSize](#ImageRectSize)

[ImageTransparency](#ImageTransparency)

[IsLoaded](#IsLoaded)

[ResampleMode](#ResampleMode)

[ScaleType](#ScaleType)

[SliceCenter](#SliceCenter)

[SliceScale](#SliceScale)

[TileSize](#TileSize)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
