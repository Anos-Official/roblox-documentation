<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Smoke -->

Smoke | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [Smoke](/docs/nl-nl/reference/engine/classes/Smoke)

Nederlands

Feedback

Engine-klasse

Smoke

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Smoke)  om deze pagina in het Engels te bekijken.

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

[Opacity](#Opacity) :[number](/docs/nl-nl/luau/numbers)

 |
|

[RiseVelocity](#RiseVelocity) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Size](#Size) :[number](/docs/nl-nl/luau/numbers)

 |
|

[TimeScale](#TimeScale) :[number](/docs/nl-nl/luau/numbers)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Voeg Rook toe aan Alle Vuren

```

local function recurseForFire(object)

	-- Controleer of we een Fire-object hebben gevonden zonder Smoke

	if object:IsA("Fire") and not object.Parent:FindFirstChildOfClass("Smoke") then

		-- Maak een rookeffect voor dit vuur

		local smoke = Instance.new("Smoke")

		smoke.Color = Color3.new(0, 0, 0)

		smoke.Opacity = 0.15

		smoke.RiseVelocity = 4

		smoke.Size = object.Size / 4

		smoke.Parent = object.Parent

	end

	-- Ga door met zoeken naar Fire-objecten

	for _, child in pairs(object:GetChildren()) do

		recurseForFire(child)

	end

end

recurseForFire(workspace)

```

---

API-referentie

Eigenschappen

Color

Parallel lezen

Mogelijkheden: Basic

Smoke.Color :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

Codevoorbeelden

Voeg Rook toe aan Alle Vuren

```

local function recurseForFire(object)

	-- Controleer of we een Fire-object hebben gevonden zonder Smoke

	if object:IsA("Fire") and not object.Parent:FindFirstChildOfClass("Smoke") then

		-- Maak een rookeffect voor dit vuur

		local smoke = Instance.new("Smoke")

		smoke.Color = Color3.new(0, 0, 0)

		smoke.Opacity = 0.15

		smoke.RiseVelocity = 4

		smoke.Size = object.Size / 4

		smoke.Parent = object.Parent

	end

	-- Ga door met zoeken naar Fire-objecten

	for _, child in pairs(object:GetChildren()) do

		recurseForFire(child)

	end

end

recurseForFire(workspace)

```

Feedback geven

---

Enabled

Parallel lezen

Mogelijkheden: Basic

Smoke.Enabled :[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

Voeg Rook toe aan Alle Vuren

```

local function recurseForFire(object)

	-- Controleer of we een Fire-object hebben gevonden zonder Smoke

	if object:IsA("Fire") and not object.Parent:FindFirstChildOfClass("Smoke") then

		-- Maak een rookeffect voor dit vuur

		local smoke = Instance.new("Smoke")

		smoke.Color = Color3.new(0, 0, 0)

		smoke.Opacity = 0.15

		smoke.RiseVelocity = 4

		smoke.Size = object.Size / 4

		smoke.Parent = object.Parent

	end

	-- Ga door met zoeken naar Fire-objecten

	for _, child in pairs(object:GetChildren()) do

		recurseForFire(child)

	end

end

recurseForFire(workspace)

```

Ingeschakeld

```

local Debris = game:GetService("Debris")

local part = Instance.new("Part")

part.Parent = workspace

local smoke = Instance.new("Smoke")

smoke.Parent = part

function stopSmoke(smoke)

	smoke.Enabled = false -- Geen nieuwe deeltjes meer

	Debris:AddItem(smoke, 10) -- Verwijder het object na een vertraging (nadat bestaande deeltjes zijn vervallen)

end

stopSmoke(part.Smoke)

```

Feedback geven

---

Opacity

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Basic

Smoke.Opacity :[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

Voeg Rook toe aan Alle Vuren

```

local function recurseForFire(object)

	-- Controleer of we een Fire-object hebben gevonden zonder Smoke

	if object:IsA("Fire") and not object.Parent:FindFirstChildOfClass("Smoke") then

		-- Maak een rookeffect voor dit vuur

		local smoke = Instance.new("Smoke")

		smoke.Color = Color3.new(0, 0, 0)

		smoke.Opacity = 0.15

		smoke.RiseVelocity = 4

		smoke.Size = object.Size / 4

		smoke.Parent = object.Parent

	end

	-- Ga door met zoeken naar Fire-objecten

	for _, child in pairs(object:GetChildren()) do

		recurseForFire(child)

	end

end

recurseForFire(workspace)

```

Feedback geven

---

RiseVelocity

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Basic

Smoke.RiseVelocity :[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

Voeg Rook toe aan Alle Vuren

```

local function recurseForFire(object)

	-- Controleer of we een Fire-object hebben gevonden zonder Smoke

	if object:IsA("Fire") and not object.Parent:FindFirstChildOfClass("Smoke") then

		-- Maak een rookeffect voor dit vuur

		local smoke = Instance.new("Smoke")

		smoke.Color = Color3.new(0, 0, 0)

		smoke.Opacity = 0.15

		smoke.RiseVelocity = 4

		smoke.Size = object.Size / 4

		smoke.Parent = object.Parent

	end

	-- Ga door met zoeken naar Fire-objecten

	for _, child in pairs(object:GetChildren()) do

		recurseForFire(child)

	end

end

recurseForFire(workspace)

```

Feedback geven

---

Size

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Basic

Smoke.Size :[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

Voeg Rook toe aan Alle Vuren

```

local function recurseForFire(object)

	-- Controleer of we een Fire-object hebben gevonden zonder Smoke

	if object:IsA("Fire") and not object.Parent:FindFirstChildOfClass("Smoke") then

		-- Maak een rookeffect voor dit vuur

		local smoke = Instance.new("Smoke")

		smoke.Color = Color3.new(0, 0, 0)

		smoke.Opacity = 0.15

		smoke.RiseVelocity = 4

		smoke.Size = object.Size / 4

		smoke.Parent = object.Parent

	end

	-- Ga door met zoeken naar Fire-objecten

	for _, child in pairs(object:GetChildren()) do

		recurseForFire(child)

	end

end

recurseForFire(workspace)

```

Feedback geven

---

TimeScale

Parallel lezen

Mogelijkheden: Basic

Smoke.TimeScale :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Ga naar

▼

Smoke

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Eigenschappen](#properties)

[Color](#Color)

[Enabled](#Enabled)

[Opacity](#Opacity)

[RiseVelocity](#RiseVelocity)

[Size](#Size)

[TimeScale](#TimeScale)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
