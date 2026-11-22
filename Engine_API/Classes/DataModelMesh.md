<!-- Source: https://create.roblox.com/docs/reference/engine/classes/DataModelMesh -->

DataModelMesh | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/DataModelMesh.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [DataModelMesh](/docs/reference/engine/classes/DataModelMesh)

English

Feedback

Engine Class

DataModelMesh

Not Creatable

Not Browsable

---

## Summary

Properties

|

[Offset](#Offset) :[Vector3](/docs/reference/engine/datatypes/Vector3)

 |
| --- | --- |
|

[Scale](#Scale) :[Vector3](/docs/reference/engine/datatypes/Vector3)

 |
|

[VertexColor](#VertexColor) :[Vector3](/docs/reference/engine/datatypes/Vector3)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Inherited by

[BevelMesh](/docs/reference/engine/classes/BevelMesh) , [FileMesh](/docs/reference/engine/classes/FileMesh)

---

API Reference

Properties

Offset

Read Parallel

DataModelMesh.Offset :[Vector3](/docs/reference/engine/datatypes/Vector3)

Code Samples

Mesh Offset and Scale

```

local TweenService = game:GetService("TweenService")

-- instance a part and a mesh

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

-- selection box to show part extents

local box = Instance.new("SelectionBox")

box.Adornee = part

box.Parent = part

-- parent part to workspace

part.Parent = workspace

-- animate offset and scale with a tween

local tween = TweenService:Create(

	mesh,

	TweenInfo.new(1, Enum.EasingStyle.Linear, Enum.EasingDirection.Out, -1, true, 0),

	{ Scale = Vector3.new(1, 1, 1), Offset = Vector3.new(0, 3, 0) }

)

tween:Play()

```

Provide feedback

---

Scale

Read Parallel

DataModelMesh.Scale :[Vector3](/docs/reference/engine/datatypes/Vector3)

Code Samples

Mesh Offset and Scale

```

local TweenService = game:GetService("TweenService")

-- instance a part and a mesh

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

-- selection box to show part extents

local box = Instance.new("SelectionBox")

box.Adornee = part

box.Parent = part

-- parent part to workspace

part.Parent = workspace

-- animate offset and scale with a tween

local tween = TweenService:Create(

	mesh,

	TweenInfo.new(1, Enum.EasingStyle.Linear, Enum.EasingDirection.Out, -1, true, 0),

	{ Scale = Vector3.new(1, 1, 1), Offset = Vector3.new(0, 3, 0) }

)

tween:Play()

```

Provide feedback

---

VertexColor

Read Parallel

DataModelMesh.VertexColor :[Vector3](/docs/reference/engine/datatypes/Vector3)

Provide feedback

---

Jump to

▼

DataModelMesh

[Summary](#summary)

[Properties](#summary-properties)

[Properties](#properties)

[Offset](#Offset)

[Scale](#Scale)

[VertexColor](#VertexColor)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
