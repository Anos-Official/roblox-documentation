<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/Vector3Value -->

Vector3Value | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Vector3Value.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [ValueBase](/docs/en-us/reference/engine/classes/ValueBase)
8. /
9. [Vector3Value](/docs/en-us/reference/engine/classes/Vector3Value)

English

Feedback

Engine Class

Vector3Value

---

## Summary

Properties

|

[Value](#Value) :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

 |
| --- | --- |

Events

|

[Changed](#Changed) (value :  [Vector3](/docs/en-us/reference/engine/datatypes/Vector3) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[changed](#changed) (value :  [Vector3](/docs/en-us/reference/engine/datatypes/Vector3) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Deprecated

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Teleporter Part

```

-- Paste me in a Script inside a Part

local part = script.Parent

local teleportPosition = part.TeleportPosition

local function onTouch(otherPart)

	-- First, find the HumanoidRootPart. If we can't find it, exit.

	local hrp = otherPart.Parent:FindFirstChild("HumanoidRootPart")

	if not hrp then

		return

	end

	-- Now teleport by setting the CFrame to one created from

	-- the stored TeleportPosition

	hrp.CFrame = CFrame.new(teleportPosition.Value)

end

part.Touched:Connect(onTouch)

```

Storing Vector2 inside Vector3Value

```

local vector3Value = Instance.new("Vector3Value")

-- Store a Vector2 in a Vector3

local vector2 = Vector2.new(42, 70)

vector3Value.Value = Vector3.new(vector2.X, vector2.Y, 0) -- The Z value is ignored

-- Load a Vector2 from a Vector3

vector2 = Vector2.new(vector3Value.Value.X, vector3Value.Value.Y)

print(vector2)

```

---

API Reference

Properties

Value

Read Parallel

Simulation Access

Vector3Value.Value :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Provide feedback

---

Events

Changed

Vector3Value.Changed (value :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

value :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

 |

Code Samples

How to Use Vector3Value.Changed

```

local value = Instance.new("Vector3Value")

value.Parent = workspace

value.Changed:Connect(function(NewValue)

	print(NewValue)

end)

value.Value = Vector3.new(10, 10, 10)

```

Provide feedback

---

changed

Deprecated

Show details

---

Jump to

▼

Vector3Value

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
