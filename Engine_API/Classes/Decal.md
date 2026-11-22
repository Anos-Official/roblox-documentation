<!-- Source: https://create.roblox.com/docs/reference/engine/classes/Decal -->

Decal | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Decal.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [FaceInstance](/docs/reference/engine/classes/FaceInstance)
8. /
9. [Decal](/docs/reference/engine/classes/Decal)

English

Feedback

Engine Class

Decal

---

## Summary

Properties

|

[AutoLocalize](#AutoLocalize) :[boolean](/docs/luau/booleans)

 |
| --- | --- |
|

[Color3](#Color3) :[Color3](/docs/reference/engine/datatypes/Color3)

 |
|

[ColorMap](#ColorMap) : ContentId

 |
|

[ColorMapContent](#ColorMapContent) :[Content](/docs/reference/engine/datatypes/Content)

 |
|

[EmissiveMaskContent](#EmissiveMaskContent) :[Content](/docs/reference/engine/datatypes/Content)

 |
|

[EmissiveStrength](#EmissiveStrength) :[number](/docs/luau/numbers)

 |
|

[EmissiveTint](#EmissiveTint) :[Color3](/docs/reference/engine/datatypes/Color3)

 |
|

[LocalTransparencyModifier](#LocalTransparencyModifier) :[number](/docs/luau/numbers)

 |
|

[MetalnessMap](#MetalnessMap) : ContentId

 |
|

[MetalnessMapContent](#MetalnessMapContent) :[Content](/docs/reference/engine/datatypes/Content)

 |
|

[NormalMap](#NormalMap) : ContentId

 |
|

[NormalMapContent](#NormalMapContent) :[Content](/docs/reference/engine/datatypes/Content)

 |
|

[ResampleMode](#ResampleMode) :[Enum.ResamplerMode](/docs/reference/engine/enums/ResamplerMode)

 |
|

[Rotation](#Rotation) :[number](/docs/luau/numbers)

 |
|

[RoughnessMap](#RoughnessMap) : ContentId

 |
|

[RoughnessMapContent](#RoughnessMapContent) :[Content](/docs/reference/engine/datatypes/Content)

 |
|

[Shiny](#Shiny) :[number](/docs/luau/numbers)

Deprecated

 |
|

[Specular](#Specular) :[number](/docs/luau/numbers)

Deprecated

 |
|

[Texture](#Texture) : ContentId

Deprecated

 |
|

[TextureContent](#TextureContent) :[Content](/docs/reference/engine/datatypes/Content)

Deprecated

 |
|

[TexturePackContent](#TexturePackContent) :[Content](/docs/reference/engine/datatypes/Content)

 |
|

[Transparency](#Transparency) :[number](/docs/luau/numbers)

 |
|

[UVOffset](#UVOffset) :[Vector2](/docs/reference/engine/datatypes/Vector2)

 |
|

[UVScale](#UVScale) :[Vector2](/docs/reference/engine/datatypes/Vector2)

 |
|

[ZIndex](#ZIndex) :[number](/docs/luau/numbers)

 |

Inherited Members

1  inherited from [FaceInstance](/docs/reference/engine/classes/FaceInstance)

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Inherited by

[Texture](/docs/reference/engine/classes/Texture)

Code Samples

Changing Decal Texture

```

-- create part

local part = Instance.new("Part")

part.Size = Vector3.new(5, 1, 5)

part.Position = Vector3.new(0, 0.5, 0)

part.Anchored = true

part.TopSurface = Enum.SurfaceType.Smooth

part.BrickColor = BrickColor.new("Toothpaste")

-- create decal

local decal = Instance.new("Decal")

decal.Face = Enum.NormalId.Top

decal.Parent = part

-- define faces

local happyFace = Content.fromUri("http://www.roblox.com/asset/?id=26424652")

local sadFace = Content.fromUri("http://www.roblox.com/asset/?id=147144198")

decal.ColorMapContent = happyFace

-- touched event

local cooldown = false

part.Touched:Connect(function(hit)

	if not cooldown then

		if hit and hit.Parent then

			cooldown = true

			sound:Play()

			decal.ColorMapContent = sadFace

			task.wait(1)

			decal.ColorMapContent = happyFace

			task.wait(0.2)

			cooldown = false

		end

	end

end)

-- add to workspace

part.Parent = workspace

```

Fading Decal

```

local TweenService = game:GetService("TweenService")

local part = Instance.new("Part")

part.Size = Vector3.new(10, 10, 1)

part.Position = Vector3.new(0, 5, 0)

part.Anchored = true

part.Transparency = 1

local decal = Instance.new("Decal")

decal.Face = Enum.NormalId.Front

decal.ColorMapContent = Content.fromUri("http://www.roblox.com/asset/?id=699259085") -- roblox logo

decal.Parent = part

part.Parent = workspace

local tween = TweenService:Create(

	decal,

	TweenInfo.new(1, Enum.EasingStyle.Linear, Enum.EasingDirection.Out, -1, true),

	{ Transparency = 1 }

)

tween:Play()

```

---

API Reference

Properties

AutoLocalize

Read Parallel

Capabilities: Basic

Decal.AutoLocalize :[boolean](/docs/luau/booleans)

Provide feedback

---

Color3

Read Parallel

Capabilities: Basic

Decal.Color3 :[Color3](/docs/reference/engine/datatypes/Color3)

Code Samples

Decal Color3

```

local TweenService = game:GetService("TweenService")

local part = Instance.new("Part")

part.Size = Vector3.new(10, 10, 1)

part.Position = Vector3.new(0, 5, 0)

part.Anchored = true

part.Transparency = 1

local decal = Instance.new("Decal")

decal.Face = Enum.NormalId.Front

decal.ColorMapContent = Content.fromUri("http://www.roblox.com/asset/?id=1145367640")

decal.Parent = part

part.Parent = workspace

local redTween = TweenService:Create(

	decal,

	TweenInfo.new(1, Enum.EasingStyle.Linear, Enum.EasingDirection.Out),

	{ Color3 = Color3.new(1, 0, 0) }

)

local greenTween = TweenService:Create(

	decal,

	TweenInfo.new(1, Enum.EasingStyle.Linear, Enum.EasingDirection.Out),

	{ Color3 = Color3.new(0, 1, 0) }

)

local blueTween = TweenService:Create(

	decal,

	TweenInfo.new(1, Enum.EasingStyle.Linear, Enum.EasingDirection.Out),

	{ Color3 = Color3.new(0, 0, 1) }

)

while true do

	redTween:Play()

	redTween.Completed:Wait()

	greenTween:Play()

	greenTween.Completed:Wait()

	blueTween:Play()

	blueTween.Completed:Wait()

end

```

Provide feedback

---

ColorMap

Not Replicated

Read Parallel

Capabilities: Basic

Decal.ColorMap : ContentId

Provide feedback

---

ColorMapContent

Not Replicated

Read Parallel

Capabilities: Basic

Decal.ColorMapContent :[Content](/docs/reference/engine/datatypes/Content)

Provide feedback

---

EmissiveMaskContent

Read Parallel

Capabilities: Basic

Decal.EmissiveMaskContent :[Content](/docs/reference/engine/datatypes/Content)

Provide feedback

---

EmissiveStrength

Read Parallel

Capabilities: Basic

Decal.EmissiveStrength :[number](/docs/luau/numbers)

Provide feedback

---

EmissiveTint

Read Parallel

Capabilities: Basic

Decal.EmissiveTint :[Color3](/docs/reference/engine/datatypes/Color3)

Provide feedback

---

LocalTransparencyModifier

Hidden

Not Replicated

Read Parallel

Capabilities: Basic

Decal.LocalTransparencyModifier :[number](/docs/luau/numbers)

Provide feedback

---

MetalnessMap

Hidden

Read Parallel

Capabilities: Basic, PluginOrOpenCloud

Decal.MetalnessMap : ContentId

Provide feedback

---

MetalnessMapContent

Read Parallel

Capabilities: Basic

Decal.MetalnessMapContent :[Content](/docs/reference/engine/datatypes/Content)

Provide feedback

---

NormalMap

Hidden

Read Parallel

Capabilities: Basic, PluginOrOpenCloud

Decal.NormalMap : ContentId

Provide feedback

---

NormalMapContent

Read Parallel

Capabilities: Basic

Decal.NormalMapContent :[Content](/docs/reference/engine/datatypes/Content)

Provide feedback

---

ResampleMode

Read Parallel

Capabilities: Basic

Decal.ResampleMode :[Enum.ResamplerMode](/docs/reference/engine/enums/ResamplerMode)

Provide feedback

---

Rotation

Read Parallel

Capabilities: Basic

Decal.Rotation :[number](/docs/luau/numbers)

Provide feedback

---

RoughnessMap

Hidden

Read Parallel

Capabilities: Basic, PluginOrOpenCloud

Decal.RoughnessMap : ContentId

Provide feedback

---

RoughnessMapContent

Read Parallel

Capabilities: Basic

Decal.RoughnessMapContent :[Content](/docs/reference/engine/datatypes/Content)

Provide feedback

---

Shiny

Deprecated

Show details

---

Specular

Deprecated

Show details

---

Texture

Deprecated

Show details

---

TextureContent

Deprecated

Show details

---

TexturePackContent

Roblox Security

Read Parallel

Capabilities: Basic

Decal.TexturePackContent :[Content](/docs/reference/engine/datatypes/Content)

Provide feedback

---

Transparency

Read Parallel

Capabilities: Basic

Decal.Transparency :[number](/docs/luau/numbers)

Provide feedback

---

UVOffset

Read Parallel

Capabilities: Basic

Decal.UVOffset :[Vector2](/docs/reference/engine/datatypes/Vector2)

Provide feedback

---

UVScale

Read Parallel

Capabilities: Basic

Decal.UVScale :[Vector2](/docs/reference/engine/datatypes/Vector2)

Provide feedback

---

ZIndex

Read Parallel

Capabilities: Basic

Decal.ZIndex :[number](/docs/luau/numbers)

Provide feedback

---

Jump to

▼

Decal

[Summary](#summary)

[Properties](#summary-properties)

[Properties](#properties)

[AutoLocalize](#AutoLocalize)

[Color3](#Color3)

[ColorMap](#ColorMap)

[ColorMapContent](#ColorMapContent)

[EmissiveMaskContent](#EmissiveMaskContent)

[EmissiveStrength](#EmissiveStrength)

[EmissiveTint](#EmissiveTint)

[LocalTransparencyModifier](#LocalTransparencyModifier)

[MetalnessMap](#MetalnessMap)

[MetalnessMapContent](#MetalnessMapContent)

[NormalMap](#NormalMap)

[NormalMapContent](#NormalMapContent)

[ResampleMode](#ResampleMode)

[Rotation](#Rotation)

[RoughnessMap](#RoughnessMap)

[RoughnessMapContent](#RoughnessMapContent)

[Shiny](#Shiny)

[Specular](#Specular)

[Texture](#Texture)

[TextureContent](#TextureContent)

[TexturePackContent](#TexturePackContent)

[Transparency](#Transparency)

[UVOffset](#UVOffset)

[UVScale](#UVScale)

[ZIndex](#ZIndex)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
