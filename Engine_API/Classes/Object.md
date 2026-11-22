<!-- Source: https://create.roblox.com/docs/reference/engine/classes/Object -->

Object | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Object.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)

English

Feedback

Engine Class

Object

Not Creatable

Not Replicated

---

## Summary

Properties

|

[ClassName](#ClassName) :[string](/docs/luau/strings)

 |
| --- | --- |
|

[className](#className) :[string](/docs/luau/strings)

Deprecated

 |

Methods

|

[GetPropertyChangedSignal](#GetPropertyChangedSignal) (property :  [string](/docs/luau/strings) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |
|

[IsA](#IsA) (className :  [string](/docs/luau/strings) ) :[boolean](/docs/luau/booleans)

 |
|

[isA](#isA) (className :  [string](/docs/luau/strings) ) :[boolean](/docs/luau/booleans)

Deprecated

 |

Events

|

[Changed](#Changed) (property :  [string](/docs/luau/strings) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited by

[Capture](/docs/reference/engine/classes/Capture) , [ConfigSnapshot](/docs/reference/engine/classes/ConfigSnapshot) , [EditableImage](/docs/reference/engine/classes/EditableImage) , [EditableMesh](/docs/reference/engine/classes/EditableMesh) , [Instance](/docs/reference/engine/classes/Instance) , Show more...

---

API Reference

Properties

ClassName

Read Only

Not Replicated

Read Parallel

Object.ClassName :[string](/docs/luau/strings)

Code Samples

Class Name

```

for _, child in workspace:GetChildren() do

    if child.ClassName == "Part" then

        print("Found a Part")

        -- will find Parts in model, but NOT TrussParts, WedgeParts, etc

    end

end

```

Provide feedback

---

className

Deprecated

Show details

---

Methods

GetPropertyChangedSignal

Object:GetPropertyChangedSignal (property :[string](/docs/luau/strings) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

property :[string](/docs/luau/strings)

 |

Returns

[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Code Samples

Old-to-New Values with Changed

```

local part = Instance.new("Part")

local currentColor = part.BrickColor

local function onBrickColorChanged()

	local newColor = part.BrickColor

	print("Color changed from", currentColor.Name, "to", newColor.Name)

	currentColor = newColor

end

part:GetPropertyChangedSignal("BrickColor"):Connect(onBrickColorChanged)

part.BrickColor = BrickColor.new("Really red")

part.BrickColor = BrickColor.new("Really blue")

```

Changed and GetPropertyChangedSignal

```

local part = Instance.new("Part")

local function onBrickColorChanged()

	print("My color is now " .. part.BrickColor.Name)

end

local function onChanged(property)

	if property == "BrickColor" then

		onBrickColorChanged()

	end

end

part:GetPropertyChangedSignal("BrickColor"):Connect(onBrickColorChanged)

part.Changed:Connect(onChanged)

-- Trigger some changes (because we connected twice,

-- both of these will cause two calls to onBrickColorChanged)

part.BrickColor = BrickColor.new("Really red")

part.BrickColor = BrickColor.new("Institutional white")

```

Provide feedback

---

IsA

Write Parallel

Object:IsA (className :[string](/docs/luau/strings) ) :[boolean](/docs/luau/booleans)

Parameters

|

className :[string](/docs/luau/strings)

 |

Returns

[boolean](/docs/luau/booleans)

Code Samples

Instance:IsA()

```

local Workspace = game:GetService("Workspace")

print(Workspace:IsA("Workspace")) -- true

print(Workspace:IsA("BasePart")) -- false

print(Workspace:IsA("Instance")) -- true

```

Provide feedback

---

isA

Deprecated

Show details

---

Events

Changed

Object.Changed (property :[string](/docs/luau/strings) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

property :[string](/docs/luau/strings)

 |

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

Change Detector

```

local object = script.Parent

local function onChanged(property)

	-- Get the current value of the property

	local value = object[property]

	-- Print a message saying what changed

	print(object:GetFullName() .. "." .. property .. " (" .. typeof(value) .. ") changed to " .. tostring(value))

end

object.Changed:Connect(onChanged)

-- Trigger a simple change in the object (add an underscore to the name)

object.Name = "_" .. object.Name

```

Provide feedback

---

Jump to

▼

Object

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[ClassName](#ClassName)

[className](#className)

[Methods](#methods)

[GetPropertyChangedSignal()](#GetPropertyChangedSignal)

[IsA()](#IsA)

[isA()](#isA)

[Events](#events)

[Changed](#Changed)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
