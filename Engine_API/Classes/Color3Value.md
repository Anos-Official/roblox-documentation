<!-- Source: https://create.roblox.com/docs/reference/engine/classes/Color3Value -->

Color3Value | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Color3Value.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [ValueBase](/docs/reference/engine/classes/ValueBase)
8. /
9. [Color3Value](/docs/reference/engine/classes/Color3Value)

English

Feedback

Engine Class

Color3Value

---

## Summary

Properties

|

[Value](#Value) :[Color3](/docs/reference/engine/datatypes/Color3)

 |
| --- | --- |

Events

|

[Changed](#Changed) (value :  [Color3](/docs/reference/engine/datatypes/Color3) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |
|

[changed](#changed) (value :  [Color3](/docs/reference/engine/datatypes/Color3) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Deprecated

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

Set Color3Value

```

local myColor3Value = script.Parent

myColor3Value.Value = Color3.new(1, 0, 0) -- Red

-- You can also store the color of a BrickColor value by accessing BrickColor's Color property, which is a Color3:

local someBrickColor = BrickColor.new("Really red")

myColor3Value.Value = someBrickColor.Color

```

---

API Reference

Properties

Value

Read Parallel

Simulation Access

Color3Value.Value :[Color3](/docs/reference/engine/datatypes/Color3)

Provide feedback

---

Events

Changed

Color3Value.Changed (value :[Color3](/docs/reference/engine/datatypes/Color3) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

value :[Color3](/docs/reference/engine/datatypes/Color3)

 |

Code Samples

How to Use Color3Value.Changed

```

local value = Instance.new("Color3Value")

value.Parent = workspace

value.Changed:Connect(function(NewValue)

	print(NewValue)

end)

value.Value = Color3.fromRGB(50, 50, 50)

```

Provide feedback

---

changed

Deprecated

Show details

---

Jump to

▼

Color3Value

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
