<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/RayValue -->

RayValue | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/RayValue.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [ValueBase](/docs/en-us/reference/engine/classes/ValueBase)
8. /
9. [RayValue](/docs/en-us/reference/engine/classes/RayValue)

English

Feedback

Engine Class

RayValue

---

## Summary

Properties

|

[Value](#Value) :[Ray](/docs/en-us/reference/engine/datatypes/Ray)

 |
| --- | --- |

Events

|

[Changed](#Changed) (value :  [Ray](/docs/en-us/reference/engine/datatypes/Ray) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[changed](#changed) (value :  [Ray](/docs/en-us/reference/engine/datatypes/Ray) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Deprecated

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Rays, RayValue and Raycasting

```

local partA = workspace.PartA

local partB = workspace.PartB

local origin = partA.Position

local direction = partB.Position - partA.Position

local ray = Ray.new(origin, direction)

local rayValue = Instance.new("RayValue")

rayValue.Value = ray

rayValue.Name = "PartA-to-PartB Ray"

rayValue.Parent = workspace

-- Raycast to find any parts in between PartA and PartB

local part = workspace:FindPartOnRay(ray)

if part then

	print("Hit part: " .. part:GetFullName())

else

	-- This ought to never happen, as our ray starts at PartA

	-- and points towards PartB, so we should always hit PartB

	-- or some other part.

	print("No part hit!")

end

```

---

API Reference

Properties

Value

Read Parallel

Simulation Access

RayValue.Value :[Ray](/docs/en-us/reference/engine/datatypes/Ray)

Provide feedback

---

Events

Changed

RayValue.Changed (value :[Ray](/docs/en-us/reference/engine/datatypes/Ray) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

value :[Ray](/docs/en-us/reference/engine/datatypes/Ray)

 |

Code Samples

How to Use RayValue.Changed

```

local value = Instance.new("RayValue")

value.Parent = workspace

value.Changed:Connect(function(NewValue)

	print(NewValue)

end)

local start = Vector3.new(0, 0, 0)

local lookAt = Vector3.new(10, 10, 10)

local ray = Ray.new(start, (lookAt - start).Unit)

value.Value = ray

```

Provide feedback

---

changed

Deprecated

Show details

---

Jump to

▼

RayValue

[Summary](#summary)

[Properties](#summary-properties)

[Events](#summary-events)

[Properties](#properties)

[Value](#Value)

[Events](#events)

[Changed](#Changed)

[changed](#changed)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
