<!-- Source: https://create.roblox.com/docs/reference/engine/classes/BlockMesh -->

BlockMesh | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/BlockMesh.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

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
11. [BlockMesh](/docs/reference/engine/classes/BlockMesh)

English

Feedback

Engine Class

BlockMesh

---

## Summary

Inherited Members

3  inherited from [DataModelMesh](/docs/reference/engine/classes/DataModelMesh)

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

BlockMesh Instantiation

```

local part = Instance.new("Part")

part.Position = Vector3.new(0, 2, 0)

part.Size = Vector3.new(5, 2, 5)

part.Anchored = true

local mesh = Instance.new("BlockMesh")

mesh.Scale = Vector3.new(0.5, 0.5, 0.5)

mesh.Offset = Vector3.new(0, 2, 0)

mesh.Parent = part

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
