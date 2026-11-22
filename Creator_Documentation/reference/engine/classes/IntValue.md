<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/IntValue -->

IntValue | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/IntValue.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [ValueBase](/docs/en-us/reference/engine/classes/ValueBase)
8. /
9. [IntValue](/docs/en-us/reference/engine/classes/IntValue)

English

Feedback

Engine Class

IntValue

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

---

API Reference

Properties

Value

Read Parallel

Simulation Access

IntValue.Value :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Events

Changed

IntValue.Changed (value :[number](/docs/en-us/luau/numbers) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

value :[number](/docs/en-us/luau/numbers)

 |

Code Samples

How to Use IntValue.Changed

```

local value = Instance.new("IntValue")

value.Parent = workspace

local function onValueChanged(newValue)

	print(newValue)

end

value.Changed:Connect(onValueChanged)

value.Value = 20

```

Provide feedback

---

changed

Deprecated

Show details

---

Jump to

▼

IntValue

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
