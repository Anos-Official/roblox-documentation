<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Decal -->

Decal | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [FaceInstance](/docs/nl-nl/reference/engine/classes/FaceInstance)
8. /
9. [Decal](/docs/nl-nl/reference/engine/classes/Decal)

Nederlands

Feedback

Engine-klasse

Decal

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Decal)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[AutoLocalize](#AutoLocalize) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |
|

[Color3](#Color3) :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

 |
|

[ColorMap](#ColorMap) : ContentId

 |
|

[ColorMapContent](#ColorMapContent) :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

 |
|

[EmissiveMaskContent](#EmissiveMaskContent) :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

 |
|

[EmissiveStrength](#EmissiveStrength) :[number](/docs/nl-nl/luau/numbers)

 |
|

[EmissiveTint](#EmissiveTint) :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

 |
|

[LocalTransparencyModifier](#LocalTransparencyModifier) :[number](/docs/nl-nl/luau/numbers)

 |
|

[MetalnessMap](#MetalnessMap) : ContentId

 |
|

[MetalnessMapContent](#MetalnessMapContent) :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

 |
|

[NormalMap](#NormalMap) : ContentId

 |
|

[NormalMapContent](#NormalMapContent) :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

 |
|

[ResampleMode](#ResampleMode) :[Enum.ResamplerMode](/docs/nl-nl/reference/engine/enums/ResamplerMode)

 |
|

[Rotation](#Rotation) :[number](/docs/nl-nl/luau/numbers)

 |
|

[RoughnessMap](#RoughnessMap) : ContentId

 |
|

[RoughnessMapContent](#RoughnessMapContent) :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

 |
|

[Shiny](#Shiny) :[number](/docs/nl-nl/luau/numbers)

Verouderd

 |
|

[Specular](#Specular) :[number](/docs/nl-nl/luau/numbers)

Verouderd

 |
|

[Texture](#Texture) : ContentId

Verouderd

 |
|

[TextureContent](#TextureContent) :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

Verouderd

 |
|

[TexturePackContent](#TexturePackContent) :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

 |
|

[Transparency](#Transparency) :[number](/docs/nl-nl/luau/numbers)

 |
|

[UVOffset](#UVOffset) :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

[UVScale](#UVScale) :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

[ZIndex](#ZIndex) :[number](/docs/nl-nl/luau/numbers)

 |

Overgenomen leden

1  overgenomen van [FaceInstance](/docs/nl-nl/reference/engine/classes/FaceInstance)

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Overgenomen door

[Texture](/docs/nl-nl/reference/engine/classes/Texture)

Codevoorbeelden

Het veranderen van Decal Textuur

```

-- maak part

local part = Instance.new("Part")

part.Size = Vector3.new(5, 1, 5)

part.Position = Vector3.new(0, 0.5, 0)

part.Anchored = true

part.TopSurface = Enum.SurfaceType.Smooth

part.BrickColor = BrickColor.new("Toothpaste")

-- maak decal

local decal = Instance.new("Decal")

decal.Face = Enum.NormalId.Top

decal.Parent = part

-- definieer gezichten

local happyFace = Content.fromUri("http://www.roblox.com/asset/?id=26424652")

local sadFace = Content.fromUri("http://www.roblox.com/asset/?id=147144198")

decal.ColorMapContent = happyFace

-- aangeraakt evenement

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

-- voeg toe aan workspace

part.Parent = workspace

```

Vervagende Decal

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

API-referentie

Eigenschappen

AutoLocalize

Parallel lezen

Mogelijkheden: Basic

Decal.AutoLocalize :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Color3

Parallel lezen

Mogelijkheden: Basic

Decal.Color3 :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

Codevoorbeelden

Decal Kleur3

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

Feedback geven

---

ColorMap

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Basic

Decal.ColorMap : ContentId

Feedback geven

---

ColorMapContent

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Basic

Decal.ColorMapContent :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

Feedback geven

---

EmissiveMaskContent

Parallel lezen

Mogelijkheden: Basic

Decal.EmissiveMaskContent :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

Feedback geven

---

EmissiveStrength

Parallel lezen

Mogelijkheden: Basic

Decal.EmissiveStrength :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

EmissiveTint

Parallel lezen

Mogelijkheden: Basic

Decal.EmissiveTint :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

Feedback geven

---

LocalTransparencyModifier

Verborgen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Basic

Decal.LocalTransparencyModifier :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

MetalnessMap

Verborgen

Parallel lezen

Mogelijkheden: Basic, PluginOrOpenCloud

Decal.MetalnessMap : ContentId

Feedback geven

---

MetalnessMapContent

Parallel lezen

Mogelijkheden: Basic

Decal.MetalnessMapContent :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

Feedback geven

---

NormalMap

Verborgen

Parallel lezen

Mogelijkheden: Basic, PluginOrOpenCloud

Decal.NormalMap : ContentId

Feedback geven

---

NormalMapContent

Parallel lezen

Mogelijkheden: Basic

Decal.NormalMapContent :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

Feedback geven

---

ResampleMode

Parallel lezen

Mogelijkheden: Basic

Decal.ResampleMode :[Enum.ResamplerMode](/docs/nl-nl/reference/engine/enums/ResamplerMode)

Feedback geven

---

Rotation

Parallel lezen

Mogelijkheden: Basic

Decal.Rotation :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

RoughnessMap

Verborgen

Parallel lezen

Mogelijkheden: Basic, PluginOrOpenCloud

Decal.RoughnessMap : ContentId

Feedback geven

---

RoughnessMapContent

Parallel lezen

Mogelijkheden: Basic

Decal.RoughnessMapContent :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

Feedback geven

---

Shiny

Verouderd

Details weergeven

---

Specular

Verouderd

Details weergeven

---

Texture

Verouderd

Details weergeven

---

TextureContent

Verouderd

Details weergeven

---

TexturePackContent

Roblox Security

Parallel lezen

Mogelijkheden: Basic

Decal.TexturePackContent :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

Feedback geven

---

Transparency

Parallel lezen

Mogelijkheden: Basic

Decal.Transparency :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

UVOffset

Parallel lezen

Mogelijkheden: Basic

Decal.UVOffset :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Feedback geven

---

UVScale

Parallel lezen

Mogelijkheden: Basic

Decal.UVScale :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Feedback geven

---

ZIndex

Parallel lezen

Mogelijkheden: Basic

Decal.ZIndex :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Ga naar

▼

Decal

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Eigenschappen](#properties)

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

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
