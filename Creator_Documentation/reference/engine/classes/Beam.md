<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/Beam -->

Beam | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Beam.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [Beam](/docs/en-us/reference/engine/classes/Beam)

English

Feedback

Engine Class

Beam

---

## Summary

Properties

|

[Attachment0](#Attachment0) :[Attachment](/docs/en-us/reference/engine/classes/Attachment)

 |
| --- | --- |
|

[Attachment1](#Attachment1) :[Attachment](/docs/en-us/reference/engine/classes/Attachment)

 |
|

[Brightness](#Brightness) :[number](/docs/en-us/luau/numbers)

 |
|

[Color](#Color) :[ColorSequence](/docs/en-us/reference/engine/datatypes/ColorSequence)

 |
|

[CurveSize0](#CurveSize0) :[number](/docs/en-us/luau/numbers)

 |
|

[CurveSize1](#CurveSize1) :[number](/docs/en-us/luau/numbers)

 |
|

[Enabled](#Enabled) :[boolean](/docs/en-us/luau/booleans)

 |
|

[FaceCamera](#FaceCamera) :[boolean](/docs/en-us/luau/booleans)

 |
|

[LightEmission](#LightEmission) :[number](/docs/en-us/luau/numbers)

 |
|

[LightInfluence](#LightInfluence) :[number](/docs/en-us/luau/numbers)

 |
|

[LocalTransparencyModifier](#LocalTransparencyModifier) :[number](/docs/en-us/luau/numbers)

 |
|

[Segments](#Segments) :[number](/docs/en-us/luau/numbers)

 |
|

[Texture](#Texture) : ContentId

 |
|

[TextureContent](#TextureContent) :[Content](/docs/en-us/reference/engine/datatypes/Content)

 |
|

[TextureLength](#TextureLength) :[number](/docs/en-us/luau/numbers)

 |
|

[TextureMode](#TextureMode) :[Enum.TextureMode](/docs/en-us/reference/engine/enums/TextureMode)

 |
|

[TextureSpeed](#TextureSpeed) :[number](/docs/en-us/luau/numbers)

 |
|

[Transparency](#Transparency) :[NumberSequence](/docs/en-us/reference/engine/datatypes/NumberSequence)

 |
|

[Width0](#Width0) :[number](/docs/en-us/luau/numbers)

 |
|

[Width1](#Width1) :[number](/docs/en-us/luau/numbers)

 |
|

[ZOffset](#ZOffset) :[number](/docs/en-us/luau/numbers)

 |

Methods

|

[SetTextureOffset](#SetTextureOffset) (offset :  [number](/docs/en-us/luau/numbers) ) : ()

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Creating a Beam From Scratch

```

-- create attachments

local att0 = Instance.new("Attachment")

local att1 = Instance.new("Attachment")

-- parent to terrain (can be part instead)

att0.Parent = workspace.Terrain

att1.Parent = workspace.Terrain

-- position attachments

att0.Position = Vector3.new(0, 10, 0)

att1.Position = Vector3.new(0, 10, 10)

-- create beam

local beam = Instance.new("Beam")

beam.Attachment0 = att0

beam.Attachment1 = att1

-- appearance properties

beam.Color = ColorSequence.new({ -- a color sequence shifting from white to blue

	ColorSequenceKeypoint.new(0, Color3.fromRGB(255, 255, 255)),

	ColorSequenceKeypoint.new(1, Color3.fromRGB(0, 255, 255)),

})

beam.LightEmission = 1 -- use additive blending

beam.LightInfluence = 0 -- beam not influenced by light

beam.Texture = "rbxasset://textures/particles/sparkles_main.dds" -- a built in sparkle texture

beam.TextureMode = Enum.TextureMode.Wrap -- wrap so length can be set by TextureLength

beam.TextureLength = 1 -- repeating texture is 1 stud long

beam.TextureSpeed = 1 -- slow texture speed

beam.Transparency = NumberSequence.new({ -- beam fades out at the end

	NumberSequenceKeypoint.new(0, 0),

	NumberSequenceKeypoint.new(0.8, 0),

	NumberSequenceKeypoint.new(1, 1),

})

beam.ZOffset = 0 -- render at the position of the beam without offset

-- shape properties

beam.CurveSize0 = 2 -- create a curved beam

beam.CurveSize1 = -2 -- create a curved beam

beam.FaceCamera = true -- beam is visible from every angle

beam.Segments = 10 -- default curve resolution

beam.Width0 = 0.2 -- starts small

beam.Width1 = 2 -- ends big

-- parent beam

beam.Enabled = true

beam.Parent = att0

```

---

API Reference

Properties

Attachment0

Read Parallel

Capabilities: Basic

Beam.Attachment0 :[Attachment](/docs/en-us/reference/engine/classes/Attachment)

Provide feedback

---

Attachment1

Read Parallel

Capabilities: Basic

Beam.Attachment1 :[Attachment](/docs/en-us/reference/engine/classes/Attachment)

Provide feedback

---

Brightness

Read Parallel

Capabilities: Basic

Beam.Brightness :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Color

Read Parallel

Capabilities: Basic

Beam.Color :[ColorSequence](/docs/en-us/reference/engine/datatypes/ColorSequence)

Provide feedback

---

CurveSize0

Read Parallel

Capabilities: Basic

Beam.CurveSize0 :[number](/docs/en-us/luau/numbers)

Code Samples

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

Provide feedback

---

CurveSize1

Read Parallel

Capabilities: Basic

Beam.CurveSize1 :[number](/docs/en-us/luau/numbers)

Code Samples

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

Provide feedback

---

Enabled

Read Parallel

Capabilities: Basic

Beam.Enabled :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

FaceCamera

Read Parallel

Capabilities: Basic

Beam.FaceCamera :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

LightEmission

Read Parallel

Capabilities: Basic

Beam.LightEmission :[number](/docs/en-us/luau/numbers)

Provide feedback

---

LightInfluence

Read Parallel

Capabilities: Basic

Beam.LightInfluence :[number](/docs/en-us/luau/numbers)

Provide feedback

---

LocalTransparencyModifier

Hidden

Not Replicated

Read Parallel

Capabilities: Basic

Beam.LocalTransparencyModifier :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Segments

Read Parallel

Capabilities: Basic

Beam.Segments :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Texture

Read Parallel

Capabilities: Basic

Beam.Texture : ContentId

Provide feedback

---

TextureContent

Read Parallel

Capabilities: Basic

Beam.TextureContent :[Content](/docs/en-us/reference/engine/datatypes/Content)

Provide feedback

---

TextureLength

Read Parallel

Capabilities: Basic

Beam.TextureLength :[number](/docs/en-us/luau/numbers)

Provide feedback

---

TextureMode

Read Parallel

Capabilities: Basic

Beam.TextureMode :[Enum.TextureMode](/docs/en-us/reference/engine/enums/TextureMode)

Provide feedback

---

TextureSpeed

Read Parallel

Capabilities: Basic

Beam.TextureSpeed :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Transparency

Read Parallel

Capabilities: Basic

Beam.Transparency :[NumberSequence](/docs/en-us/reference/engine/datatypes/NumberSequence)

Provide feedback

---

Width0

Read Parallel

Capabilities: Basic

Beam.Width0 :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Width1

Read Parallel

Capabilities: Basic

Beam.Width1 :[number](/docs/en-us/luau/numbers)

Provide feedback

---

ZOffset

Read Parallel

Capabilities: Basic

Beam.ZOffset :[number](/docs/en-us/luau/numbers)

Code Samples

Layering Beams

```

-- Create beams

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

-- Layer beams

beam1.ZOffset = 0

beam2.ZOffset = 0.01

beam3.ZOffset = 0.02

-- Create attachments

local attachment0 = Instance.new("Attachment")

attachment0.Position = Vector3.new(0, -10, 0)

attachment0.Parent = workspace.Terrain

local attachment1 = Instance.new("Attachment")

attachment1.Position = Vector3.new(0, 10, 0)

attachment1.Parent = workspace.Terrain

-- Connect beams

beam1.Attachment0 = attachment0

beam1.Attachment1 = attachment1

beam2.Attachment0 = attachment0

beam2.Attachment1 = attachment1

beam3.Attachment0 = attachment0

beam3.Attachment1 = attachment1

-- Parent beams

beam1.Parent = workspace

beam2.Parent = workspace

beam3.Parent = workspace

```

Provide feedback

---

Methods

SetTextureOffset

Capabilities: Basic

Beam:SetTextureOffset (offset :[number](/docs/en-us/luau/numbers) ) : ()

Parameters

|

offset :[number](/docs/en-us/luau/numbers)

Default Value: 0 |

Returns

()

Provide feedback

---

Jump to

▼

Beam

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

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

[Methods](#methods)

[SetTextureOffset()](#SetTextureOffset)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
