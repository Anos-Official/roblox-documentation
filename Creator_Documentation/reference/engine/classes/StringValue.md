<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/StringValue -->

StringValue | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/StringValue.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [ValueBase](/docs/en-us/reference/engine/classes/ValueBase)
8. /
9. [StringValue](/docs/en-us/reference/engine/classes/StringValue)

English

Feedback

Engine Class

StringValue

---

## Summary

Properties

|

[Value](#Value) :[string](/docs/en-us/luau/strings)

 |
| --- | --- |

Events

|

[Changed](#Changed) (value :  [string](/docs/en-us/luau/strings) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[changed](#changed) (value :  [string](/docs/en-us/luau/strings) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

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

StringValue.Value :[string](/docs/en-us/luau/strings)

Provide feedback

---

Events

Changed

StringValue.Changed (value :[string](/docs/en-us/luau/strings) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

value :[string](/docs/en-us/luau/strings)

 |

Code Samples

How to Use StringValue.Changed

```

local value = Instance.new("StringValue")

value.Parent = workspace

value.Changed:Connect(function(NewValue)

	print(NewValue)

end)

value.Value = "Hello world!"

```

Provide feedback

---

changed

Deprecated

Show details

---

Jump to

▼

StringValue

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
