<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/CFrameValue -->

CFrameValue | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/CFrameValue.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [ValueBase](/docs/en-us/reference/engine/classes/ValueBase)
8. /
9. [CFrameValue](/docs/en-us/reference/engine/classes/CFrameValue)

English

Feedback

Engine Class

CFrameValue

---

## Summary

Properties

|

[Value](#Value) :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

 |
| --- | --- |

Events

|

[Changed](#Changed) (value :  [CFrame](/docs/en-us/reference/engine/datatypes/CFrame) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[changed](#changed) (value :  [CFrame](/docs/en-us/reference/engine/datatypes/CFrame) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Deprecated

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Store the Camera's CFrame

```

-- Create a CFrame that stores the camera's current position/orientation

local vSnapshot = Instance.new("CFrameValue")

vSnapshot.Value = workspace.CurrentCamera.CFrame

vSnapshot.Name = "Snapshot"

vSnapshot.Parent = workspace

-- Later, we can load the CFrame back into the camera

workspace.CurrentCamera.CFrame = vSnapshot.Value

```

---

API Reference

Properties

Value

Read Parallel

Simulation Access

CFrameValue.Value :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

Provide feedback

---

Events

Changed

CFrameValue.Changed (value :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

value :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

 |

Code Samples

CFrameValue.Changed

```

local cframeValue = script.Parent.CFrameValue

cframeValue.Changed:Connect(print)

cframeValue.Value = CFrame.new(1, 2, 3)

```

Provide feedback

---

changed

Deprecated

Show details

---

Jump to

▼

CFrameValue

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
