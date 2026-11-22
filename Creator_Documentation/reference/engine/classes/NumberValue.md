<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/NumberValue -->

NumberValue | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/NumberValue.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [ValueBase](/docs/en-us/reference/engine/classes/ValueBase)
8. /
9. [NumberValue](/docs/en-us/reference/engine/classes/NumberValue)

English

Feedback

Engine Class

NumberValue

---

## Summary

Properties

|

[Value](#Value) :[number](/docs/en-us/luau/numbers)

 |
| --- | --- |

Events

|

[Changed](#Changed) (value :  [number](/docs/en-us/luau/numbers) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[changed](#changed) (value :  [number](/docs/en-us/luau/numbers) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Deprecated

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Changed Event

```

-- Demonstrate the Changed event by creating a Part

local part = Instance.new("Part")

part.Changed:Connect(print)

-- This fires Changed with "Transparency"

part.Transparency = 0.5

-- Similarly, this fires Changed with "Number"

part.Name = "SomePart"

-- Since changing BrickColor will also change other

-- properties at the same time, this line fires Changed

-- with "BrickColor", "Color3" and "Color3uint16".

part.BrickColor = BrickColor.Red()

-- A NumberValue holds a double-precision floating-point number

local vNumber = Instance.new("NumberValue")

vNumber.Changed:Connect(print)

-- This fires Changed with 123.456 (not "Value")

vNumber.Value = 123.456

-- This does not fire Changed

vNumber.Name = "SomeNumber"

-- A StringValue stores one string

local vString = Instance.new("StringValue")

vString.Changed:Connect(print)

-- This fires Changed with "Hello" (not "Value")

vString.Value = "Hello"

```

---

API Reference

Properties

Value

Read Parallel

Simulation Access

NumberValue.Value :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Events

Changed

NumberValue.Changed (value :[number](/docs/en-us/luau/numbers) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

value :[number](/docs/en-us/luau/numbers)

 |

Code Samples

NumberValue Changed

```

local numberValue = script.Parent.NumberValue

local function printValue(value)

	print(value)

end

numberValue.Changed:Connect(printValue)

numberValue.Value = 20

```

Provide feedback

---

changed

Deprecated

Show details

---

Jump to

▼

NumberValue

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
