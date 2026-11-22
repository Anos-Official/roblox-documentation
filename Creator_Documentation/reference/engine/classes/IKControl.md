<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/IKControl -->

IKControl | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/IKControl.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [IKControl](/docs/en-us/reference/engine/classes/IKControl)

English

Feedback

Engine Class

IKControl

---

## Summary

Properties

|

[ChainRoot](#ChainRoot) :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |
| --- | --- |
|

[Enabled](#Enabled) :[boolean](/docs/en-us/luau/booleans)

 |
|

[EndEffector](#EndEffector) :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |
|

[EndEffectorOffset](#EndEffectorOffset) :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

 |
|

[Offset](#Offset) :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

 |
|

[Pole](#Pole) :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |
|

[Priority](#Priority) :[number](/docs/en-us/luau/numbers)

 |
|

[SmoothTime](#SmoothTime) :[number](/docs/en-us/luau/numbers)

 |
|

[Target](#Target) :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |
|

[Type](#Type) :[Enum.IKControlType](/docs/en-us/reference/engine/enums/IKControlType)

 |
|

[Weight](#Weight) :[number](/docs/en-us/luau/numbers)

 |

Methods

|

[GetChainCount](#GetChainCount) () :[number](/docs/en-us/luau/numbers)

 |
|

[GetChainLength](#GetChainLength) () :[number](/docs/en-us/luau/numbers)

 |
|

[GetNodeLocalCFrame](#GetNodeLocalCFrame) (index :  [number](/docs/en-us/luau/numbers) ) :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

 |
|

[GetNodeWorldCFrame](#GetNodeWorldCFrame) (index :  [number](/docs/en-us/luau/numbers) ) :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

 |
|

[GetRawFinalTarget](#GetRawFinalTarget) () :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

 |
|

[GetSmoothedFinalTarget](#GetSmoothedFinalTarget) () :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

IKControl setup

```

local character = script.Parent.Character

local humanoid = character.Humanoid

local root = character.HumanoidRootPart

-- Create a new attachment to use as the IKControl.Target

local target = Instance.new("Attachment")

target.CFrame = CFrame.new(-1, 0, -1)

target.Parent = root

local ikControl = Instance.new("IKControl")

ikControl.Type = Enum.IKControlType.Position

ikControl.EndEffector = character.LeftHand

ikControl.ChainRoot = character.LeftUpperArm

ikControl.Target = target

ikControl.Parent = humanoid

```

---

API Reference

Properties

ChainRoot

Read Parallel

Capabilities: Animation

Simulation Access

IKControl.ChainRoot :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

Provide feedback

---

Enabled

Read Parallel

Capabilities: Animation

Simulation Access

IKControl.Enabled :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

EndEffector

Read Parallel

Capabilities: Animation

Simulation Access

IKControl.EndEffector :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

Provide feedback

---

EndEffectorOffset

Read Parallel

Capabilities: Animation

IKControl.EndEffectorOffset :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

Provide feedback

---

Offset

Read Parallel

Capabilities: Animation

IKControl.Offset :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

Provide feedback

---

Pole

Read Parallel

Capabilities: Animation

IKControl.Pole :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

Provide feedback

---

Priority

Read Parallel

Capabilities: Animation

IKControl.Priority :[number](/docs/en-us/luau/numbers)

Provide feedback

---

SmoothTime

Read Parallel

Capabilities: Animation

IKControl.SmoothTime :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Target

Read Parallel

Capabilities: Animation

Simulation Access

IKControl.Target :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

Provide feedback

---

Type

Read Parallel

Capabilities: Animation

Simulation Access

IKControl.Type :[Enum.IKControlType](/docs/en-us/reference/engine/enums/IKControlType)

Provide feedback

---

Weight

Read Parallel

Capabilities: Animation

Simulation Access

IKControl.Weight :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Methods

GetChainCount

Capabilities: Animation

IKControl:GetChainCount () :[number](/docs/en-us/luau/numbers)

Returns

[number](/docs/en-us/luau/numbers)

Provide feedback

---

GetChainLength

Capabilities: Animation

IKControl:GetChainLength () :[number](/docs/en-us/luau/numbers)

Returns

[number](/docs/en-us/luau/numbers)

Provide feedback

---

GetNodeLocalCFrame

Capabilities: Animation

IKControl:GetNodeLocalCFrame (index :[number](/docs/en-us/luau/numbers) ) :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

Parameters

|

index :[number](/docs/en-us/luau/numbers)

 |

Returns

[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

Provide feedback

---

GetNodeWorldCFrame

Capabilities: Animation

IKControl:GetNodeWorldCFrame (index :[number](/docs/en-us/luau/numbers) ) :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

Parameters

|

index :[number](/docs/en-us/luau/numbers)

 |

Returns

[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

Provide feedback

---

GetRawFinalTarget

Capabilities: Animation

IKControl:GetRawFinalTarget () :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

Returns

[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

Provide feedback

---

GetSmoothedFinalTarget

Capabilities: Animation

IKControl:GetSmoothedFinalTarget () :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

Returns

[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

Provide feedback

---

Jump to

▼

IKControl

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[ChainRoot](#ChainRoot)

[Enabled](#Enabled)

[EndEffector](#EndEffector)

[EndEffectorOffset](#EndEffectorOffset)

[Offset](#Offset)

[Pole](#Pole)

[Priority](#Priority)

[SmoothTime](#SmoothTime)

[Target](#Target)

[Type](#Type)

[Weight](#Weight)

[Methods](#methods)

[GetChainCount()](#GetChainCount)

[GetChainLength()](#GetChainLength)

[GetNodeLocalCFrame()](#GetNodeLocalCFrame)

[GetNodeWorldCFrame()](#GetNodeWorldCFrame)

[GetRawFinalTarget()](#GetRawFinalTarget)

[GetSmoothedFinalTarget()](#GetSmoothedFinalTarget)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
