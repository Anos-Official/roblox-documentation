<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Trail -->

Trail | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [Trail](/docs/nl-nl/reference/engine/classes/Trail)

Nederlands

Feedback

Engine-klasse

Trail

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Trail)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Attachment0](#Attachment0) :[Attachment](/docs/nl-nl/reference/engine/classes/Attachment)

 |
| --- | --- |
|

[Attachment1](#Attachment1) :[Attachment](/docs/nl-nl/reference/engine/classes/Attachment)

 |
|

[Brightness](#Brightness) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Color](#Color) :[ColorSequence](/docs/nl-nl/reference/engine/datatypes/ColorSequence)

 |
|

[Enabled](#Enabled) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[FaceCamera](#FaceCamera) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[Lifetime](#Lifetime) :[number](/docs/nl-nl/luau/numbers)

 |
|

[LightEmission](#LightEmission) :[number](/docs/nl-nl/luau/numbers)

 |
|

[LightInfluence](#LightInfluence) :[number](/docs/nl-nl/luau/numbers)

 |
|

[LocalTransparencyModifier](#LocalTransparencyModifier) :[number](/docs/nl-nl/luau/numbers)

 |
|

[MaxLength](#MaxLength) :[number](/docs/nl-nl/luau/numbers)

 |
|

[MinLength](#MinLength) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Texture](#Texture) : ContentId

 |
|

[TextureContent](#TextureContent) :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

 |
|

[TextureLength](#TextureLength) :[number](/docs/nl-nl/luau/numbers)

 |
|

[TextureMode](#TextureMode) :[Enum.TextureMode](/docs/nl-nl/reference/engine/enums/TextureMode)

 |
|

[Transparency](#Transparency) :[NumberSequence](/docs/nl-nl/reference/engine/datatypes/NumberSequence)

 |
|

[WidthScale](#WidthScale) :[NumberSequence](/docs/nl-nl/reference/engine/datatypes/NumberSequence)

 |

Methoden

|

[Clear](#Clear) () : ()

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Een Deel maken met een Basis Spoor

```

local TweenService = game:GetService("TweenService")

-- Maak een ouderdeel

local part = Instance.new("Part")

part.Material = Enum.Material.SmoothPlastic

part.Size = Vector3.new(4, 1, 2)

part.Position = Vector3.new(0, 5, 0)

part.Anchored = true

part.Parent = workspace

-- Maak attachments op het deel

local attachment0 = Instance.new("Attachment")

attachment0.Name = "Attachment0"

attachment0.Position = Vector3.new(-2, 0, 0)

attachment0.Parent = part

local attachment1 = Instance.new("Attachment")

attachment1.Name = "Attachment1"

attachment1.Position = Vector3.new(2, 0, 0)

attachment1.Parent = part

-- Maak een nieuw spoor

local trail = Instance.new("Trail")

trail.Attachment0 = attachment0

trail.Attachment1 = attachment1

trail.Parent = part

-- Tween deel om spoor weer te geven

local dir = 15

while true do

	dir *= -1

	local goal = { Position = part.Position + Vector3.new(0, 0, dir) }

	local tweenInfo = TweenInfo.new(3)

	local tween = TweenService:Create(part, tweenInfo, goal)

	tween:Play()

	task.wait(4)

end

```

---

API-referentie

Eigenschappen

Attachment0

Parallel lezen

Mogelijkheden: Basic

Trail.Attachment0 :[Attachment](/docs/nl-nl/reference/engine/classes/Attachment)

Feedback geven

---

Attachment1

Parallel lezen

Mogelijkheden: Basic

Trail.Attachment1 :[Attachment](/docs/nl-nl/reference/engine/classes/Attachment)

Feedback geven

---

Brightness

Parallel lezen

Mogelijkheden: Basic

Trail.Brightness :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Color

Parallel lezen

Mogelijkheden: Basic

Trail.Color :[ColorSequence](/docs/nl-nl/reference/engine/datatypes/ColorSequence)

Codevoorbeelden

Een Spoor Maken met een Kleurverloop

```

local TweenService = game:GetService("TweenService")

-- Maak een ouderdeel

local part = Instance.new("Part")

part.Material = Enum.Material.SmoothPlastic

part.Size = Vector3.new(4, 1, 2)

part.Position = Vector3.new(0, 5, 0)

part.Anchored = true

part.Parent = workspace

-- Maak bevestigingen op het deel

local attachment0 = Instance.new("Attachment")

attachment0.Name = "Attachment0"

attachment0.Position = Vector3.new(-2, 0, 0)

attachment0.Parent = part

local attachment1 = Instance.new("Attachment")

attachment1.Name = "Attachment1"

attachment1.Position = Vector3.new(2, 0, 0)

attachment1.Parent = part

-- Maak een nieuw spoor met kleurverloop

local trail = Instance.new("Trail")

trail.Attachment0 = attachment0

trail.Attachment1 = attachment1

local color1 = Color3.fromRGB(255, 0, 0)

local color2 = Color3.fromRGB(0, 0, 255)

trail.Color = ColorSequence.new(color1, color2)

trail.Parent = part

-- Tween deel om spoor weer te geven

local dir = 15

while true do

	dir *= -1

	local goal = { Position = part.Position + Vector3.new(0, 0, dir) }

	local tweenInfo = TweenInfo.new(3)

	local tween = TweenService:Create(part, tweenInfo, goal)

	tween:Play()

	task.wait(4)

end

```

Feedback geven

---

Enabled

Parallel lezen

Mogelijkheden: Basic

Trail.Enabled :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

FaceCamera

Parallel lezen

Mogelijkheden: Basic

Trail.FaceCamera :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Lifetime

Parallel lezen

Mogelijkheden: Basic

Trail.Lifetime :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

LightEmission

Parallel lezen

Mogelijkheden: Basic

Trail.LightEmission :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

LightInfluence

Parallel lezen

Mogelijkheden: Basic

Trail.LightInfluence :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

LocalTransparencyModifier

Verborgen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Basic

Trail.LocalTransparencyModifier :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

MaxLength

Parallel lezen

Mogelijkheden: Basic

Trail.MaxLength :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

MinLength

Parallel lezen

Mogelijkheden: Basic

Trail.MinLength :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Texture

Parallel lezen

Mogelijkheden: Basic

Trail.Texture : ContentId

Codevoorbeelden

Een Spoor Maken met een Pootafdruk Textuur

```

local TweenService = game:GetService("TweenService")

-- Maak een ouderdeel

local part = Instance.new("Part")

part.Material = Enum.Material.SmoothPlastic

part.Size = Vector3.new(2, 1, 2)

part.Position = Vector3.new(0, 5, 0)

part.Anchored = true

part.Parent = workspace

-- Maak bevestigingen op het deel

local attachment0 = Instance.new("Attachment")

attachment0.Name = "Attachment0"

attachment0.Position = Vector3.new(-1, 0, 0)

attachment0.Parent = part

local attachment1 = Instance.new("Attachment")

attachment1.Name = "Attachment1"

attachment1.Position = Vector3.new(1, 0, 0)

attachment1.Parent = part

-- Maak een nieuw spoor met kleurverloop

local trail = Instance.new("Trail")

trail.Attachment0 = attachment0

trail.Attachment1 = attachment1

trail.Texture = "rbxassetid://16178262222"

trail.TextureMode = Enum.TextureMode.Static

trail.TextureLength = 2

trail.Parent = part

-- Tween deel om spoor weer te geven

local dir = 15

while true do

	dir *= -1

	local goal = { Position = part.Position + Vector3.new(0, 0, dir) }

	local tweenInfo = TweenInfo.new(3)

	local tween = TweenService:Create(part, tweenInfo, goal)

	tween:Play()

	task.wait(4)

end

```

Feedback geven

---

TextureContent

Parallel lezen

Mogelijkheden: Basic

Trail.TextureContent :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

Feedback geven

---

TextureLength

Parallel lezen

Mogelijkheden: Basic

Trail.TextureLength :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

TextureMode

Parallel lezen

Mogelijkheden: Basic

Trail.TextureMode :[Enum.TextureMode](/docs/nl-nl/reference/engine/enums/TextureMode)

Feedback geven

---

Transparency

Parallel lezen

Mogelijkheden: Basic

Trail.Transparency :[NumberSequence](/docs/nl-nl/reference/engine/datatypes/NumberSequence)

Feedback geven

---

WidthScale

Parallel lezen

Mogelijkheden: Basic

Trail.WidthScale :[NumberSequence](/docs/nl-nl/reference/engine/datatypes/NumberSequence)

Feedback geven

---

Methoden

Clear

Mogelijkheden: Basic

Trail:Clear () : ()

Teruggaves

()

Feedback geven

---

Ga naar

▼

Trail

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[Attachment0](#Attachment0)

[Attachment1](#Attachment1)

[Brightness](#Brightness)

[Color](#Color)

[Enabled](#Enabled)

[FaceCamera](#FaceCamera)

[Lifetime](#Lifetime)

[LightEmission](#LightEmission)

[LightInfluence](#LightInfluence)

[LocalTransparencyModifier](#LocalTransparencyModifier)

[MaxLength](#MaxLength)

[MinLength](#MinLength)

[Texture](#Texture)

[TextureContent](#TextureContent)

[TextureLength](#TextureLength)

[TextureMode](#TextureMode)

[Transparency](#Transparency)

[WidthScale](#WidthScale)

[Methoden](#methods)

[Clear()](#Clear)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
