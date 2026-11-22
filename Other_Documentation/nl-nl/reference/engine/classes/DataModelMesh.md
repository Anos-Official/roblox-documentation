<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/DataModelMesh -->

DataModelMesh | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [DataModelMesh](/docs/nl-nl/reference/engine/classes/DataModelMesh)

Nederlands

Feedback

Engine-klasse

DataModelMesh

Niet maakbaar

Niet doorzoekbaar

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/DataModelMesh)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Offset](#Offset) :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |
| --- | --- |
|

[Scale](#Scale) :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |
|

[VertexColor](#VertexColor) :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Overgenomen door

[BevelMesh](/docs/nl-nl/reference/engine/classes/BevelMesh) , [FileMesh](/docs/nl-nl/reference/engine/classes/FileMesh)

---

API-referentie

Eigenschappen

Offset

Parallel lezen

DataModelMesh.Offset :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

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

Feedback geven

---

Scale

Parallel lezen

DataModelMesh.Scale :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

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

Feedback geven

---

VertexColor

Parallel lezen

DataModelMesh.VertexColor :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

Ga naar

▼

DataModelMesh

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Eigenschappen](#properties)

[Offset](#Offset)

[Scale](#Scale)

[VertexColor](#VertexColor)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
