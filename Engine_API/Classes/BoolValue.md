<!-- Source: https://create.roblox.com/docs/reference/engine/classes/BoolValue -->

BoolValue | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/BoolValue.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [ValueBase](/docs/reference/engine/classes/ValueBase)
8. /
9. [BoolValue](/docs/reference/engine/classes/BoolValue)

English

Feedback

Engine Class

BoolValue

---

## Summary

Properties

|

[Value](#Value) :[boolean](/docs/luau/booleans)

 |
| --- | --- |

Events

|

[Changed](#Changed) (value :  [boolean](/docs/luau/booleans) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |
|

[changed](#changed) (value :  [boolean](/docs/luau/booleans) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Deprecated

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Properties

Value

Read Parallel

Simulation Access

BoolValue.Value :[boolean](/docs/luau/booleans)

Provide feedback

---

Events

Changed

BoolValue.Changed (value :[boolean](/docs/luau/booleans) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

value :[boolean](/docs/luau/booleans)

 |

Code Samples

BoolValue.Changed

```

local boolValue = script.Parent.BoolValue

local function printValue(value)

	print(value)

end

boolValue.Changed:Connect(printValue)

boolValue.Value = true

```

Provide feedback

---

changed

Deprecated

Show details

---

Jump to

▼

BoolValue

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
