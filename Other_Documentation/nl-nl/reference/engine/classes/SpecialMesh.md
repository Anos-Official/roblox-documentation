<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/SpecialMesh -->

SpecialMesh | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [DataModelMesh](/docs/nl-nl/reference/engine/classes/DataModelMesh)
8. /
9. [FileMesh](/docs/nl-nl/reference/engine/classes/FileMesh)
10. /
11. [SpecialMesh](/docs/nl-nl/reference/engine/classes/SpecialMesh)

Nederlands

Feedback

Engine-klasse

SpecialMesh

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/SpecialMesh)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[MeshType](#MeshType) :[Enum.MeshType](/docs/nl-nl/reference/engine/enums/MeshType)

 |
| --- | --- |

Overgenomen leden

4  overgenomen van [FileMesh](/docs/nl-nl/reference/engine/classes/FileMesh)

3  overgenomen van [DataModelMesh](/docs/nl-nl/reference/engine/classes/DataModelMesh)

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Mesh Offset en Schaal

```

local TweenService = game:GetService("TweenService")

-- instantiëren van een deel en een mesh

local part = Instance.new("Part")

part.Size = Vector3.new(4, 8, 4)

part.Position = Vector3.new(0, 4, 0)

part.Anchored = true

part.CanCollide = false

local mesh = Instance.new("SpecialMesh")

mesh.MeshType = Enum.MeshType.FileMesh

mesh.MeshId = "rbxassetid://1086413449"

mesh.TextureId = "rbxassetid://1461576423"

mesh.Offset = Vector3.new(0, 0, 0)

mesh.Scale = Vector3.new(4, 4, 4)

mesh.Parent = part

-- selectiebox om de afmetingen van het deel te tonen

local box = Instance.new("SelectionBox")

box.Adornee = part

box.Parent = part

-- deel aan de workspace toevoegen

part.Parent = workspace

-- offset en schaal animeren met een tween

local tween = TweenService:Create(

	mesh,

	TweenInfo.new(1, Enum.EasingStyle.Linear, Enum.EasingDirection.Out, -1, true, 0),

	{ Scale = Vector3.new(1, 1, 1), Offset = Vector3.new(0, 3, 0) }

)

tween:Play()

```

Mesh VertexColor

```

local TweenService = game:GetService("TweenService")

-- maak een deel en een mesh aan

local part = Instance.new("Part")

part.Size = Vector3.new(4, 8, 4)

part.Position = Vector3.new(0, 4, 0)

part.Anchored = true

part.CanCollide = false

local mesh = Instance.new("SpecialMesh")

mesh.MeshType = Enum.MeshType.FileMesh

mesh.MeshId = "rbxassetid://1086413449"

mesh.TextureId = "rbxassetid://1461576423"

mesh.Offset = Vector3.new(0, 0, 0)

mesh.Scale = Vector3.new(4, 4, 4)

mesh.VertexColor = Vector3.new(1, 1, 1)

mesh.Parent = part

-- voeg het deel toe aan de workspace

part.Parent = workspace

-- maak tweens aan

local tweenInfo = TweenInfo.new(1, Enum.EasingStyle.Linear, Enum.EasingDirection.Out)

local blackTween = TweenService:Create(mesh, tweenInfo, { VertexColor = Vector3.new(0, 0, 0) })

local redTween = TweenService:Create(mesh, tweenInfo, { VertexColor = Vector3.new(1, 0, 0) })

local greenTween = TweenService:Create(mesh, tweenInfo, { VertexColor = Vector3.new(0, 1, 0) })

local blueTween = TweenService:Create(mesh, tweenInfo, { VertexColor = Vector3.new(0, 0, 1) })

local resetTween = TweenService:Create(mesh, tweenInfo, { VertexColor = Vector3.new(1, 1, 1) })

-- animeer

while true do

	blackTween:Play()

	blackTween.Completed:Wait()

	redTween:Play()

	redTween.Completed:Wait()

	greenTween:Play()

	greenTween.Completed:Wait()

	blueTween:Play()

	blueTween.Completed:Wait()

	resetTween:Play()

	resetTween.Completed:Wait()

	task.wait()

end

```

---

API-referentie

Eigenschappen

MeshType

Parallel lezen

Mogelijkheden: Basic

SpecialMesh.MeshType :[Enum.MeshType](/docs/nl-nl/reference/engine/enums/MeshType)

Codevoorbeelden

Mesh VertexColor

```

local TweenService = game:GetService("TweenService")

-- maak een deel en een mesh aan

local part = Instance.new("Part")

part.Size = Vector3.new(4, 8, 4)

part.Position = Vector3.new(0, 4, 0)

part.Anchored = true

part.CanCollide = false

local mesh = Instance.new("SpecialMesh")

mesh.MeshType = Enum.MeshType.FileMesh

mesh.MeshId = "rbxassetid://1086413449"

mesh.TextureId = "rbxassetid://1461576423"

mesh.Offset = Vector3.new(0, 0, 0)

mesh.Scale = Vector3.new(4, 4, 4)

mesh.VertexColor = Vector3.new(1, 1, 1)

mesh.Parent = part

-- voeg het deel toe aan de workspace

part.Parent = workspace

-- maak tweens aan

local tweenInfo = TweenInfo.new(1, Enum.EasingStyle.Linear, Enum.EasingDirection.Out)

local blackTween = TweenService:Create(mesh, tweenInfo, { VertexColor = Vector3.new(0, 0, 0) })

local redTween = TweenService:Create(mesh, tweenInfo, { VertexColor = Vector3.new(1, 0, 0) })

local greenTween = TweenService:Create(mesh, tweenInfo, { VertexColor = Vector3.new(0, 1, 0) })

local blueTween = TweenService:Create(mesh, tweenInfo, { VertexColor = Vector3.new(0, 0, 1) })

local resetTween = TweenService:Create(mesh, tweenInfo, { VertexColor = Vector3.new(1, 1, 1) })

-- animeer

while true do

	blackTween:Play()

	blackTween.Completed:Wait()

	redTween:Play()

	redTween.Completed:Wait()

	greenTween:Play()

	greenTween.Completed:Wait()

	blueTween:Play()

	blueTween.Completed:Wait()

	resetTween:Play()

	resetTween.Completed:Wait()

	task.wait()

end

```

Feedback geven

---

Ga naar

▼

SpecialMesh

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Eigenschappen](#properties)

[MeshType](#MeshType)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
