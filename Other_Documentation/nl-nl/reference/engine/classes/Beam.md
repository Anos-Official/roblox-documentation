<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Beam -->

Beam | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [Beam](/docs/nl-nl/reference/engine/classes/Beam)

Nederlands

Feedback

Engine-klasse

Beam

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Beam)  om deze pagina in het Engels te bekijken.

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

[CurveSize0](#CurveSize0) :[number](/docs/nl-nl/luau/numbers)

 |
|

[CurveSize1](#CurveSize1) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Enabled](#Enabled) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[FaceCamera](#FaceCamera) :[boolean](/docs/nl-nl/luau/booleans)

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

[Segments](#Segments) :[number](/docs/nl-nl/luau/numbers)

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

[TextureSpeed](#TextureSpeed) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Transparency](#Transparency) :[NumberSequence](/docs/nl-nl/reference/engine/datatypes/NumberSequence)

 |
|

[Width0](#Width0) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Width1](#Width1) :[number](/docs/nl-nl/luau/numbers)

 |
|

[ZOffset](#ZOffset) :[number](/docs/nl-nl/luau/numbers)

 |

Methoden

|

[SetTextureOffset](#SetTextureOffset) (offset :  [number](/docs/nl-nl/luau/numbers) ) : ()

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Een Straal Maken Vanuit Niets

```

-- maak attachments

local att0 = Instance.new("Attachment")

local att1 = Instance.new("Attachment")

-- ouder aan terrein (kan ook een onderdeel zijn)

att0.Parent = workspace.Terrain

att1.Parent = workspace.Terrain

-- positioneer attachments

att0.Position = Vector3.new(0, 10, 0)

att1.Position = Vector3.new(0, 10, 10)

-- maak beam

local beam = Instance.new("Beam")

beam.Attachment0 = att0

beam.Attachment1 = att1

-- uiterlijk eigenschappen

beam.Color = ColorSequence.new({ -- een kleurvolgorde die verschuift van wit naar blauw

	ColorSequenceKeypoint.new(0, Color3.fromRGB(255, 255, 255)),

	ColorSequenceKeypoint.new(1, Color3.fromRGB(0, 255, 255)),

})

beam.LightEmission = 1 -- gebruik additieve menging

beam.LightInfluence = 0 -- beam wordt niet beïnvloed door licht

beam.Texture = "rbxasset://textures/particles/sparkles_main.dds" -- een ingebouwde sparkle textuur

beam.TextureMode = Enum.TextureMode.Wrap -- wikkel zodat de lengte kan worden ingesteld door TextureLength

beam.TextureLength = 1 -- herhalende textuur is 1 stud lang

beam.TextureSpeed = 1 -- trage textuursnelheid

beam.Transparency = NumberSequence.new({ -- beam vervaagt aan het einde

	NumberSequenceKeypoint.new(0, 0),

	NumberSequenceKeypoint.new(0.8, 0),

	NumberSequenceKeypoint.new(1, 1),

})

beam.ZOffset = 0 -- render op de positie van de beam zonder offset

-- vorm eigenschappen

beam.CurveSize0 = 2 -- maak een gebogen beam

beam.CurveSize1 = -2 -- maak een gebogen beam

beam.FaceCamera = true -- beam is zichtbaar vanuit elke hoek

beam.Segments = 10 -- standaard curve resolutie

beam.Width0 = 0.2 -- begint klein

beam.Width1 = 2 -- eindigt groot

-- ouder beam

beam.Enabled = true

beam.Parent = att0

```

---

API-referentie

Eigenschappen

Attachment0

Parallel lezen

Mogelijkheden: Basic

Beam.Attachment0 :[Attachment](/docs/nl-nl/reference/engine/classes/Attachment)

Feedback geven

---

Attachment1

Parallel lezen

Mogelijkheden: Basic

Beam.Attachment1 :[Attachment](/docs/nl-nl/reference/engine/classes/Attachment)

Feedback geven

---

Brightness

Parallel lezen

Mogelijkheden: Basic

Beam.Brightness :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Color

Parallel lezen

Mogelijkheden: Basic

Beam.Color :[ColorSequence](/docs/nl-nl/reference/engine/datatypes/ColorSequence)

Feedback geven

---

CurveSize0

Parallel lezen

Mogelijkheden: Basic

Beam.CurveSize0 :[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

Curve Size0

```

local part = Instance.new("Part")

part.Anchored = true

part.Parent = workspace

local attachment0 = Instance.new("Attachment")

attachment0.Parent = part

local attachment1 = Instance.new("Attachment")

attachment1.Parent = part

local Beam = Instance.new("Beam")

Beam.Attachment0 = attachment0

Beam.Attachment1 = attachment1

Beam.Parent = part

local controlPoint2 = Beam.Attachment0.WorldPosition + (Beam.Attachment0.CFrame.RightVector * Beam.CurveSize0)

```

Feedback geven

---

CurveSize1

Parallel lezen

Mogelijkheden: Basic

Beam.CurveSize1 :[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

Curve Size1

```

local part = Instance.new("Part")

part.Anchored = true

part.Parent = workspace

local attachment0 = Instance.new("Attachment")

attachment0.Parent = part

local attachment1 = Instance.new("Attachment")

attachment1.Parent = part

local Beam = Instance.new("Beam")

Beam.Attachment0 = attachment0

Beam.Attachment1 = attachment1

Beam.Parent = part

local controlPoint3 = Beam.Attachment1.WorldPosition - (Beam.Attachment1.CFrame.RightVector * Beam.CurveSize1)

```

Feedback geven

---

Enabled

Parallel lezen

Mogelijkheden: Basic

Beam.Enabled :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

FaceCamera

Parallel lezen

Mogelijkheden: Basic

Beam.FaceCamera :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

LightEmission

Parallel lezen

Mogelijkheden: Basic

Beam.LightEmission :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

LightInfluence

Parallel lezen

Mogelijkheden: Basic

Beam.LightInfluence :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

LocalTransparencyModifier

Verborgen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Basic

Beam.LocalTransparencyModifier :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Segments

Parallel lezen

Mogelijkheden: Basic

Beam.Segments :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Texture

Parallel lezen

Mogelijkheden: Basic

Beam.Texture : ContentId

Feedback geven

---

TextureContent

Parallel lezen

Mogelijkheden: Basic

Beam.TextureContent :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

Feedback geven

---

TextureLength

Parallel lezen

Mogelijkheden: Basic

Beam.TextureLength :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

TextureMode

Parallel lezen

Mogelijkheden: Basic

Beam.TextureMode :[Enum.TextureMode](/docs/nl-nl/reference/engine/enums/TextureMode)

Feedback geven

---

TextureSpeed

Parallel lezen

Mogelijkheden: Basic

Beam.TextureSpeed :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Transparency

Parallel lezen

Mogelijkheden: Basic

Beam.Transparency :[NumberSequence](/docs/nl-nl/reference/engine/datatypes/NumberSequence)

Feedback geven

---

Width0

Parallel lezen

Mogelijkheden: Basic

Beam.Width0 :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Width1

Parallel lezen

Mogelijkheden: Basic

Beam.Width1 :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

ZOffset

Parallel lezen

Mogelijkheden: Basic

Beam.ZOffset :[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

Laagstructuur Stralen

```

-- Maak stralen

local beam1 = Instance.new("Beam")

beam1.Color = ColorSequence.new(Color3.new(1, 0, 0))

beam1.FaceCamera = true

beam1.Width0 = 3

beam1.Width1 = 3

local beam2 = Instance.new("Beam")

beam2.Color = ColorSequence.new(Color3.new(0, 1, 0))

beam2.FaceCamera = true

beam2.Width0 = 2

beam2.Width1 = 2

local beam3 = Instance.new("Beam")

beam3.Color = ColorSequence.new(Color3.new(0, 0, 1))

beam3.FaceCamera = true

beam3.Width0 = 1

beam3.Width1 = 1

-- Laag stralen

beam1.ZOffset = 0

beam2.ZOffset = 0.01

beam3.ZOffset = 0.02

-- Maak bevestigingen

local attachment0 = Instance.new("Attachment")

attachment0.Position = Vector3.new(0, -10, 0)

attachment0.Parent = workspace.Terrain

local attachment1 = Instance.new("Attachment")

attachment1.Position = Vector3.new(0, 10, 0)

attachment1.Parent = workspace.Terrain

-- Verbind stralen

beam1.Attachment0 = attachment0

beam1.Attachment1 = attachment1

beam2.Attachment0 = attachment0

beam2.Attachment1 = attachment1

beam3.Attachment0 = attachment0

beam3.Attachment1 = attachment1

-- Voeg stralen toe aan de ouder

beam1.Parent = workspace

beam2.Parent = workspace

beam3.Parent = workspace

```

Feedback geven

---

Methoden

SetTextureOffset

Mogelijkheden: Basic

Beam:SetTextureOffset (offset :[number](/docs/nl-nl/luau/numbers) ) : ()

Parameters

|

offset :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0 |

Teruggaves

()

Feedback geven

---

Ga naar

▼

Beam

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[Attachment0](#Attachment0)

[Attachment1](#Attachment1)

[Brightness](#Brightness)

[Color](#Color)

[CurveSize0](#CurveSize0)

[CurveSize1](#CurveSize1)

[Enabled](#Enabled)

[FaceCamera](#FaceCamera)

[LightEmission](#LightEmission)

[LightInfluence](#LightInfluence)

[LocalTransparencyModifier](#LocalTransparencyModifier)

[Segments](#Segments)

[Texture](#Texture)

[TextureContent](#TextureContent)

[TextureLength](#TextureLength)

[TextureMode](#TextureMode)

[TextureSpeed](#TextureSpeed)

[Transparency](#Transparency)

[Width0](#Width0)

[Width1](#Width1)

[ZOffset](#ZOffset)

[Methoden](#methods)

[SetTextureOffset()](#SetTextureOffset)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
