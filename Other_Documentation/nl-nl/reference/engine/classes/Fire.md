<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Fire -->

Fire | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [Fire](/docs/nl-nl/reference/engine/classes/Fire)

Nederlands

Feedback

Engine-klasse

Fire

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Fire)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Color](#Color) :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

 |
| --- | --- |
|

[Enabled](#Enabled) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[Heat](#Heat) :[number](/docs/nl-nl/luau/numbers)

 |
|

[LocalTransparencyModifier](#LocalTransparencyModifier) :[number](/docs/nl-nl/luau/numbers)

 |
|

[SecondaryColor](#SecondaryColor) :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

 |
|

[Size](#Size) :[number](/docs/nl-nl/luau/numbers)

 |
|

[size](#size) :[number](/docs/nl-nl/luau/numbers)

Verouderd

 |
|

[TimeScale](#TimeScale) :[number](/docs/nl-nl/luau/numbers)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Fakkels Aansteken

```

local Workspace = game:GetService("Workspace")

for _, descendant in Workspace:GetDescendants() do

	if descendant.Name == "Torch" and descendant:IsA("BasePart") then

		local fire = Instance.new("Fire")

		fire.Heat = 10

		fire.SecondaryColor = Color3.new(1, 1, 1)

		fire.Size = math.max(descendant.Size.X, descendant.Size.Z) -- Kies de grotere van de twee dimensies

		fire.Parent = descendant

	end

end

```

Vuur Effect Inschakelen

```

local part = script.Parent

local clickDetector = Instance.new("ClickDetector")

clickDetector.Parent = part

local fire = Instance.new("Fire")

fire.Parent = part

local light = Instance.new("PointLight")

light.Parent = part

local function onClick()

	fire.Enabled = not fire.Enabled

	light.Enabled = fire.Enabled

end

clickDetector.MouseClick:Connect(onClick)

```

---

API-referentie

Eigenschappen

Color

Parallel lezen

Mogelijkheden: Basic

Fire.Color :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

Feedback geven

---

Enabled

Parallel lezen

Mogelijkheden: Basic

Fire.Enabled :[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

Ingeschakeld

```

local Debris = game:GetService("Debris")

local function douseFlames(fire)

	fire.Enabled = false -- Geen nieuwe deeltjes meer

	Debris:AddItem(fire, 2) -- Verwijder het object nadat bestaande deeltjes zijn vervallen

end

local part = Instance.new("Part")

part.Anchored = true

part.Parent = workspace

local fire = Instance.new("Fire")

fire.Parent = part

douseFlames(part.Fire)

```

Feedback geven

---

Heat

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Basic

Fire.Heat :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

LocalTransparencyModifier

Verborgen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Basic

Fire.LocalTransparencyModifier :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

SecondaryColor

Parallel lezen

Mogelijkheden: Basic

Fire.SecondaryColor :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

Feedback geven

---

Size

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Basic

Fire.Size :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

size

Verouderd

Details weergeven

---

TimeScale

Parallel lezen

Mogelijkheden: Basic

Fire.TimeScale :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Ga naar

▼

Fire

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Eigenschappen](#properties)

[Color](#Color)

[Enabled](#Enabled)

[Heat](#Heat)

[LocalTransparencyModifier](#LocalTransparencyModifier)

[SecondaryColor](#SecondaryColor)

[Size](#Size)

[size](#size)

[TimeScale](#TimeScale)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
