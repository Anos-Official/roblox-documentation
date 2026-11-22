<!-- Source: https://create.roblox.com/docs/reference/engine/classes/CylinderMesh -->

CylinderMesh | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/CylinderMesh.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [DataModelMesh](/docs/reference/engine/classes/DataModelMesh)
8. /
9. [BevelMesh](/docs/reference/engine/classes/BevelMesh)
10. /
11. [CylinderMesh](/docs/reference/engine/classes/CylinderMesh)

English

Feedback

Engine Class

CylinderMesh

Deprecated

---

## Summary

Inherited Members

3  inherited from [DataModelMesh](/docs/reference/engine/classes/DataModelMesh)

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

CylinderMesh Instantiation

```

local part = Instance.new("Part")

part.Position = Vector3.new(0, 2, 0)

part.Size = Vector3.new(10, 2, 5)

part.Anchored = true

local mesh = Instance.new("CylinderMesh")

mesh.Parent = part

mesh.Scale = Vector3.new(1, 1, 1)

mesh.Offset = Vector3.new(0, 0, 0)

local adornment = Instance.new("SelectionBox")

adornment.Adornee = part

adornment.Parent = part

part.Parent = workspace

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
