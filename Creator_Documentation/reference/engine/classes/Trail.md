<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/Trail -->

Trail | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Trail.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [Trail](/docs/en-us/reference/engine/classes/Trail)

English

Feedback

Engine Class

Trail

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

[Enabled](#Enabled) :[boolean](/docs/en-us/luau/booleans)

 |
|

[FaceCamera](#FaceCamera) :[boolean](/docs/en-us/luau/booleans)

 |
|

[Lifetime](#Lifetime) :[number](/docs/en-us/luau/numbers)

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

[MaxLength](#MaxLength) :[number](/docs/en-us/luau/numbers)

 |
|

[MinLength](#MinLength) :[number](/docs/en-us/luau/numbers)

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

[Transparency](#Transparency) :[NumberSequence](/docs/en-us/reference/engine/datatypes/NumberSequence)

 |
|

[WidthScale](#WidthScale) :[NumberSequence](/docs/en-us/reference/engine/datatypes/NumberSequence)

 |

Methods

|

[Clear](#Clear) () : ()

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Creating a Part with a Basic Trail

```

local TweenService = game:GetService("TweenService")

-- Create a parent part

local part = Instance.new("Part")

part.Material = Enum.Material.SmoothPlastic

part.Size = Vector3.new(4, 1, 2)

part.Position = Vector3.new(0, 5, 0)

part.Anchored = true

part.Parent = workspace

-- Create attachments on part

local attachment0 = Instance.new("Attachment")

attachment0.Name = "Attachment0"

attachment0.Position = Vector3.new(-2, 0, 0)

attachment0.Parent = part

local attachment1 = Instance.new("Attachment")

attachment1.Name = "Attachment1"

attachment1.Position = Vector3.new(2, 0, 0)

attachment1.Parent = part

-- Create a new trail

local trail = Instance.new("Trail")

trail.Attachment0 = attachment0

trail.Attachment1 = attachment1

trail.Parent = part

-- Tween part to display trail

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

API Reference

Properties

Attachment0

Read Parallel

Capabilities: Basic

Trail.Attachment0 :[Attachment](/docs/en-us/reference/engine/classes/Attachment)

Provide feedback

---

Attachment1

Read Parallel

Capabilities: Basic

Trail.Attachment1 :[Attachment](/docs/en-us/reference/engine/classes/Attachment)

Provide feedback

---

Brightness

Read Parallel

Capabilities: Basic

Trail.Brightness :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Color

Read Parallel

Capabilities: Basic

Trail.Color :[ColorSequence](/docs/en-us/reference/engine/datatypes/ColorSequence)

Code Samples

Creating a Trail with a Color Gradient

```

local TweenService = game:GetService("TweenService")

-- Create a parent part

local part = Instance.new("Part")

part.Material = Enum.Material.SmoothPlastic

part.Size = Vector3.new(4, 1, 2)

part.Position = Vector3.new(0, 5, 0)

part.Anchored = true

part.Parent = workspace

-- Create attachments on part

local attachment0 = Instance.new("Attachment")

attachment0.Name = "Attachment0"

attachment0.Position = Vector3.new(-2, 0, 0)

attachment0.Parent = part

local attachment1 = Instance.new("Attachment")

attachment1.Name = "Attachment1"

attachment1.Position = Vector3.new(2, 0, 0)

attachment1.Parent = part

-- Create a new trail with color gradient

local trail = Instance.new("Trail")

trail.Attachment0 = attachment0

trail.Attachment1 = attachment1

local color1 = Color3.fromRGB(255, 0, 0)

local color2 = Color3.fromRGB(0, 0, 255)

trail.Color = ColorSequence.new(color1, color2)

trail.Parent = part

-- Tween part to display trail

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

Provide feedback

---

Enabled

Read Parallel

Capabilities: Basic

Trail.Enabled :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

FaceCamera

Read Parallel

Capabilities: Basic

Trail.FaceCamera :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

Lifetime

Read Parallel

Capabilities: Basic

Trail.Lifetime :[number](/docs/en-us/luau/numbers)

Provide feedback

---

LightEmission

Read Parallel

Capabilities: Basic

Trail.LightEmission :[number](/docs/en-us/luau/numbers)

Provide feedback

---

LightInfluence

Read Parallel

Capabilities: Basic

Trail.LightInfluence :[number](/docs/en-us/luau/numbers)

Provide feedback

---

LocalTransparencyModifier

Hidden

Not Replicated

Read Parallel

Capabilities: Basic

Trail.LocalTransparencyModifier :[number](/docs/en-us/luau/numbers)

Provide feedback

---

MaxLength

Read Parallel

Capabilities: Basic

Trail.MaxLength :[number](/docs/en-us/luau/numbers)

Provide feedback

---

MinLength

Read Parallel

Capabilities: Basic

Trail.MinLength :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Texture

Read Parallel

Capabilities: Basic

Trail.Texture : ContentId

Code Samples

Creating a Trail with a Paw Print Texture

```

local TweenService = game:GetService("TweenService")

-- Create a parent part

local part = Instance.new("Part")

part.Material = Enum.Material.SmoothPlastic

part.Size = Vector3.new(2, 1, 2)

part.Position = Vector3.new(0, 5, 0)

part.Anchored = true

part.Parent = workspace

-- Create attachments on part

local attachment0 = Instance.new("Attachment")

attachment0.Name = "Attachment0"

attachment0.Position = Vector3.new(-1, 0, 0)

attachment0.Parent = part

local attachment1 = Instance.new("Attachment")

attachment1.Name = "Attachment1"

attachment1.Position = Vector3.new(1, 0, 0)

attachment1.Parent = part

-- Create a new trail with color gradient

local trail = Instance.new("Trail")

trail.Attachment0 = attachment0

trail.Attachment1 = attachment1

trail.Texture = "rbxassetid://16178262222"

trail.TextureMode = Enum.TextureMode.Static

trail.TextureLength = 2

trail.Parent = part

-- Tween part to display trail

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

Provide feedback

---

TextureContent

Read Parallel

Capabilities: Basic

Trail.TextureContent :[Content](/docs/en-us/reference/engine/datatypes/Content)

Provide feedback

---

TextureLength

Read Parallel

Capabilities: Basic

Trail.TextureLength :[number](/docs/en-us/luau/numbers)

Provide feedback

---

TextureMode

Read Parallel

Capabilities: Basic

Trail.TextureMode :[Enum.TextureMode](/docs/en-us/reference/engine/enums/TextureMode)

Provide feedback

---

Transparency

Read Parallel

Capabilities: Basic

Trail.Transparency :[NumberSequence](/docs/en-us/reference/engine/datatypes/NumberSequence)

Provide feedback

---

WidthScale

Read Parallel

Capabilities: Basic

Trail.WidthScale :[NumberSequence](/docs/en-us/reference/engine/datatypes/NumberSequence)

Provide feedback

---

Methods

Clear

Capabilities: Basic

Trail:Clear () : ()

Returns

()

Provide feedback

---

Jump to

▼

Trail

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

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

[Methods](#methods)

[Clear()](#Clear)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
