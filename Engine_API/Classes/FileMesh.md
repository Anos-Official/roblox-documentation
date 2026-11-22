<!-- Source: https://create.roblox.com/docs/reference/engine/classes/FileMesh -->

FileMesh | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/FileMesh.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [DataModelMesh](/docs/reference/engine/classes/DataModelMesh)
8. /
9. [FileMesh](/docs/reference/engine/classes/FileMesh)

English

Feedback

Engine Class

FileMesh

---

## Summary

Properties

|

[MeshContent](#MeshContent) :[Content](/docs/reference/engine/datatypes/Content)

 |
| --- | --- |
|

[MeshId](#MeshId) : ContentId

 |
|

[TextureContent](#TextureContent) :[Content](/docs/reference/engine/datatypes/Content)

 |
|

[TextureId](#TextureId) : ContentId

 |

Inherited Members

3  inherited from [DataModelMesh](/docs/reference/engine/classes/DataModelMesh)

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Inherited by

[SpecialMesh](/docs/reference/engine/classes/SpecialMesh)

Code Samples

FileMesh Offset and Scale

```

local TweenService = game:GetService("TweenService")

local part = Instance.new("Part")

part.Size = Vector3.new(4, 8, 4)

part.Position = Vector3.new(0, 4, 0)

part.Anchored = true

part.CanCollide = false

local mesh = Instance.new("FileMesh") -- advised to use SpecialMesh instead

mesh.MeshId = "rbxassetid://1086413449"

mesh.TextureId = "rbxassetid://1461576423"

mesh.Offset = Vector3.new(0, 0, 0)

mesh.Scale = Vector3.new(4, 4, 4)

mesh.Parent = part

local box = Instance.new("SelectionBox")

box.Adornee = part

box.Parent = part

part.Parent = workspace

local tween = TweenService:Create(

	mesh,

	TweenInfo.new(1, Enum.EasingStyle.Linear, Enum.EasingDirection.Out, -1, true, 0),

	{ Scale = Vector3.new(1, 1, 1), Offset = Vector3.new(0, 3, 0) }

)

tween:Play()

```

---

API Reference

Properties

MeshContent

Read Parallel

Capabilities: Basic

FileMesh.MeshContent :[Content](/docs/reference/engine/datatypes/Content)

Provide feedback

---

MeshId

Read Parallel

Capabilities: Basic

FileMesh.MeshId : ContentId

Code Samples

Mesh VertexColor

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

mesh.VertexColor = Vector3.new(1, 1, 1)

mesh.Parent = part

-- parent part to workspace

part.Parent = workspace

-- create tweens

local tweenInfo = TweenInfo.new(1, Enum.EasingStyle.Linear, Enum.EasingDirection.Out)

local blackTween = TweenService:Create(mesh, tweenInfo, { VertexColor = Vector3.new(0, 0, 0) })

local redTween = TweenService:Create(mesh, tweenInfo, { VertexColor = Vector3.new(1, 0, 0) })

local greenTween = TweenService:Create(mesh, tweenInfo, { VertexColor = Vector3.new(0, 1, 0) })

local blueTween = TweenService:Create(mesh, tweenInfo, { VertexColor = Vector3.new(0, 0, 1) })

local resetTween = TweenService:Create(mesh, tweenInfo, { VertexColor = Vector3.new(1, 1, 1) })

-- animate

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

Provide feedback

---

TextureContent

Read Parallel

Capabilities: Basic

FileMesh.TextureContent :[Content](/docs/reference/engine/datatypes/Content)

Provide feedback

---

TextureId

Read Parallel

Capabilities: Basic

FileMesh.TextureId : ContentId

Code Samples

Mesh VertexColor

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

mesh.VertexColor = Vector3.new(1, 1, 1)

mesh.Parent = part

-- parent part to workspace

part.Parent = workspace

-- create tweens

local tweenInfo = TweenInfo.new(1, Enum.EasingStyle.Linear, Enum.EasingDirection.Out)

local blackTween = TweenService:Create(mesh, tweenInfo, { VertexColor = Vector3.new(0, 0, 0) })

local redTween = TweenService:Create(mesh, tweenInfo, { VertexColor = Vector3.new(1, 0, 0) })

local greenTween = TweenService:Create(mesh, tweenInfo, { VertexColor = Vector3.new(0, 1, 0) })

local blueTween = TweenService:Create(mesh, tweenInfo, { VertexColor = Vector3.new(0, 0, 1) })

local resetTween = TweenService:Create(mesh, tweenInfo, { VertexColor = Vector3.new(1, 1, 1) })

-- animate

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

Provide feedback

---

Jump to

▼

FileMesh

[Summary](#summary)

[Properties](#summary-properties)

[Properties](#properties)

[MeshContent](#MeshContent)

[MeshId](#MeshId)

[TextureContent](#TextureContent)

[TextureId](#TextureId)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
