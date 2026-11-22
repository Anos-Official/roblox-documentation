<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/ObjectValue -->

ObjectValue | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/ObjectValue.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [ValueBase](/docs/en-us/reference/engine/classes/ValueBase)
8. /
9. [ObjectValue](/docs/en-us/reference/engine/classes/ObjectValue)

English

Feedback

Engine Class

ObjectValue

---

## Summary

Properties

|

[Value](#Value) :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |
| --- | --- |

Events

|

[Changed](#Changed) (value :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[changed](#changed) (value :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Deprecated

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

ObjectValue Example

```

local objectValue = Instance.new("ObjectValue")

objectValue.Name = "MyBaseplateReference"

objectValue.Value = workspace:FindFirstChild("Baseplate")

objectValue.Parent = workspace

```

---

API Reference

Properties

Value

Read Parallel

Simulation Access

ObjectValue.Value :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

Provide feedback

---

Events

Changed

ObjectValue.Changed (value :[Instance](/docs/en-us/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

value :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |

Code Samples

ObjectValue Changed

```

local objectValue = script.Parent.ObjectValue

local part = script.Parent.Part

local function printObject(object)

	print(object:GetFullName())

end

objectValue.Changed:Connect(printObject)

objectValue.Value = part

```

Provide feedback

---

changed

Deprecated

Show details

---

Jump to

▼

ObjectValue

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
