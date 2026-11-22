<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/WeldConstraint -->

WeldConstraint | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/WeldConstraint.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [WeldConstraint](/docs/en-us/reference/engine/classes/WeldConstraint)

English

Feedback

Engine Class

WeldConstraint

---

## Summary

Properties

|

[Active](#Active) :[boolean](/docs/en-us/luau/booleans)

 |
| --- | --- |
|

[Enabled](#Enabled) :[boolean](/docs/en-us/luau/booleans)

 |
|

[Part0](#Part0) :[BasePart](/docs/en-us/reference/engine/classes/BasePart)

 |
|

[Part1](#Part1) :[BasePart](/docs/en-us/reference/engine/classes/BasePart)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Properties

Active

Read Only

Not Replicated

Read Parallel

Capabilities: Physics

Simulation Access

WeldConstraint.Active :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

Enabled

Not Replicated

Read Parallel

Capabilities: Physics

Simulation Access

WeldConstraint.Enabled :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

Part0

Not Replicated

Read Parallel

Capabilities: Physics

Simulation Access

WeldConstraint.Part0 :[BasePart](/docs/en-us/reference/engine/classes/BasePart)

Code Samples

Part0

```

local Workspace = game:GetService("Workspace")

local partA = Instance.new("Part")

local partB = Instance.new("Part")

partA.Position = Vector3.new(0, 10, 0)

partA.Parent = Workspace

partB.Position = Vector3.new(0, 10, 10)

partB.Parent = Workspace

local weld = Instance.new("WeldConstraint")

weld.Part0 = partA

weld.Part1 = partB

weld.Parent = partA

```

Provide feedback

---

Part1

Not Replicated

Read Parallel

Capabilities: Physics

Simulation Access

WeldConstraint.Part1 :[BasePart](/docs/en-us/reference/engine/classes/BasePart)

Code Samples

Part1

```

local Workspace = game:GetService("Workspace")

local partA = Instance.new("Part")

local partB = Instance.new("Part")

partA.Position = Vector3.new(0, 10, 0)

partA.Parent = Workspace

partB.Position = Vector3.new(0, 10, 10)

partB.Parent = Workspace

local weld = Instance.new("WeldConstraint")

weld.Part0 = partA

weld.Part1 = partB

weld.Parent = partA

```

Provide feedback

---

Jump to

▼

WeldConstraint

[Summary](#summary)

[Properties](#summary-properties)

[Properties](#properties)

[Active](#Active)

[Enabled](#Enabled)

[Part0](#Part0)

[Part1](#Part1)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
