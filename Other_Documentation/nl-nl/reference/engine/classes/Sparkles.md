<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Sparkles -->

Sparkles | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [Sparkles](/docs/nl-nl/reference/engine/classes/Sparkles)

Nederlands

Feedback

Engine-klasse

Sparkles

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Sparkles)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Color](#Color) :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

Verouderd

 |
| --- | --- |
|

[Enabled](#Enabled) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[SparkleColor](#SparkleColor) :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

 |
|

[TimeScale](#TimeScale) :[number](/docs/nl-nl/luau/numbers)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Geef Sprankels

```

local Players = game:GetService("Players")

local function onCharacterSpawned(character)

	local hrp = character:WaitForChild("HumanoidRootPart")

	-- Voeg sprankels toe die zijn gekleurd naar de torso kleur van de speler

	local sparkles = Instance.new("Sparkles")

	sparkles.Parent = hrp

	sparkles.SparkleColor = character:WaitForChild("Body Colors").TorsoColor.Color

	sparkles.Enabled = true

end

local function onPlayerAdded(player)

	player.CharacterAdded:Connect(onCharacterSpawned)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

---

API-referentie

Eigenschappen

Color

Verouderd

Details weergeven

---

Enabled

Parallel lezen

Mogelijkheden: Basic

Sparkles.Enabled :[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

Geef Sprankels

```

local Players = game:GetService("Players")

local function onCharacterSpawned(character)

	local hrp = character:WaitForChild("HumanoidRootPart")

	-- Voeg sprankels toe die zijn gekleurd naar de torso kleur van de speler

	local sparkles = Instance.new("Sparkles")

	sparkles.Parent = hrp

	sparkles.SparkleColor = character:WaitForChild("Body Colors").TorsoColor.Color

	sparkles.Enabled = true

end

local function onPlayerAdded(player)

	player.CharacterAdded:Connect(onCharacterSpawned)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Ingeschakeld

```

local Debris = game:GetService("Debris")

local part = Instance.new("Part")

part.Parent = workspace

local sparkles = Instance.new("Sparkles")

sparkles.Parent = part

function stopSparkling(sparkles)

	sparkles.Enabled = false -- Geen nieuwe deeltjes meer

	Debris:AddItem(sparkles, 4) -- Verwijder het object na een vertraging (na het vervallen van bestaande deeltjes)

end

stopSparkling(part.Sparkles)

```

Feedback geven

---

SparkleColor

Parallel lezen

Mogelijkheden: Basic

Sparkles.SparkleColor :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

Codevoorbeelden

Geef Sprankels

```

local Players = game:GetService("Players")

local function onCharacterSpawned(character)

	local hrp = character:WaitForChild("HumanoidRootPart")

	-- Voeg sprankels toe die zijn gekleurd naar de torso kleur van de speler

	local sparkles = Instance.new("Sparkles")

	sparkles.Parent = hrp

	sparkles.SparkleColor = character:WaitForChild("Body Colors").TorsoColor.Color

	sparkles.Enabled = true

end

local function onPlayerAdded(player)

	player.CharacterAdded:Connect(onCharacterSpawned)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Feedback geven

---

TimeScale

Parallel lezen

Mogelijkheden: Basic

Sparkles.TimeScale :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Ga naar

▼

Sparkles

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Eigenschappen](#properties)

[Color](#Color)

[Enabled](#Enabled)

[SparkleColor](#SparkleColor)

[TimeScale](#TimeScale)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
