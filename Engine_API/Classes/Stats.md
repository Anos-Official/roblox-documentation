<!-- Source: https://create.roblox.com/docs/reference/engine/classes/Stats -->

Stats | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Stats.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [Stats](/docs/reference/engine/classes/Stats)

English

Feedback

Engine Class

Stats

Not Creatable

Service

---

## Summary

Properties

|

[ContactsCount](#ContactsCount) :[number](/docs/luau/numbers)

 |
| --- | --- |
|

[DataReceiveKbps](#DataReceiveKbps) :[number](/docs/luau/numbers)

 |
|

[DataSendKbps](#DataSendKbps) :[number](/docs/luau/numbers)

 |
|

[FrameTime](#FrameTime) :[number](/docs/luau/numbers)

 |
|

[HeartbeatTime](#HeartbeatTime) :[number](/docs/luau/numbers)

 |
|

[HeartbeatTimeMs](#HeartbeatTimeMs) :[number](/docs/luau/numbers)

Deprecated

 |
|

[InstanceCount](#InstanceCount) :[number](/docs/luau/numbers)

 |
|

[MemoryTrackingEnabled](#MemoryTrackingEnabled) :[boolean](/docs/luau/booleans)

 |
|

[MovingPrimitivesCount](#MovingPrimitivesCount) :[number](/docs/luau/numbers)

 |
|

[PhysicsReceiveKbps](#PhysicsReceiveKbps) :[number](/docs/luau/numbers)

 |
|

[PhysicsSendKbps](#PhysicsSendKbps) :[number](/docs/luau/numbers)

 |
|

[PhysicsStepTime](#PhysicsStepTime) :[number](/docs/luau/numbers)

 |
|

[PhysicsStepTimeMs](#PhysicsStepTimeMs) :[number](/docs/luau/numbers)

Deprecated

 |
|

[PrimitivesCount](#PrimitivesCount) :[number](/docs/luau/numbers)

 |
|

[RenderCPUFrameTime](#RenderCPUFrameTime) :[number](/docs/luau/numbers)

 |
|

[RenderGPUFrameTime](#RenderGPUFrameTime) :[number](/docs/luau/numbers)

 |
|

[SceneDrawcallCount](#SceneDrawcallCount) :[number](/docs/luau/numbers)

 |
|

[SceneTriangleCount](#SceneTriangleCount) :[number](/docs/luau/numbers)

 |
|

[ShadowsDrawcallCount](#ShadowsDrawcallCount) :[number](/docs/luau/numbers)

 |
|

[ShadowsTriangleCount](#ShadowsTriangleCount) :[number](/docs/luau/numbers)

 |
|

[UI2DDrawcallCount](#UI2DDrawcallCount) :[number](/docs/luau/numbers)

 |
|

[UI2DTriangleCount](#UI2DTriangleCount) :[number](/docs/luau/numbers)

 |
|

[UI3DDrawcallCount](#UI3DDrawcallCount) :[number](/docs/luau/numbers)

 |
|

[UI3DTriangleCount](#UI3DTriangleCount) :[number](/docs/luau/numbers)

 |

Methods

|

[GetHarmonyQualityLevel](#GetHarmonyQualityLevel) () :[number](/docs/luau/numbers)

 |
|

[GetMemoryCategoryNames](#GetMemoryCategoryNames) () :[{any}](/docs/luau/tables#arrays)

 |
|

[GetMemoryUsageMbAllCategories](#GetMemoryUsageMbAllCategories) () :[{any}](/docs/luau/tables#arrays)

 |
|

[GetMemoryUsageMbForTag](#GetMemoryUsageMbForTag) (tag :  [Enum.DeveloperMemoryTag](/docs/reference/engine/enums/DeveloperMemoryTag) ) :[number](/docs/luau/numbers)

 |
|

[GetTotalMemoryUsageMb](#GetTotalMemoryUsageMb) () :[number](/docs/luau/numbers)

 |
|

[ResetHarmonyMemoryTarget](#ResetHarmonyMemoryTarget) () : ()

 |
|

[SetHarmonyMemoryTarget](#SetHarmonyMemoryTarget) (targetMB :  [number](/docs/luau/numbers) ) : ()

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Properties

ContactsCount

Read Only

Not Replicated

Read Parallel

Stats.ContactsCount :[number](/docs/luau/numbers)

Provide feedback

---

DataReceiveKbps

Read Only

Not Replicated

Read Parallel

Stats.DataReceiveKbps :[number](/docs/luau/numbers)

Provide feedback

---

DataSendKbps

Read Only

Not Replicated

Read Parallel

Stats.DataSendKbps :[number](/docs/luau/numbers)

Provide feedback

---

FrameTime

Read Only

Not Replicated

Read Parallel

Stats.FrameTime :[number](/docs/luau/numbers)

Provide feedback

---

HeartbeatTime

Read Only

Not Replicated

Read Parallel

Stats.HeartbeatTime :[number](/docs/luau/numbers)

Provide feedback

---

HeartbeatTimeMs

Deprecated

Show details

---

InstanceCount

Read Only

Not Replicated

Read Parallel

Stats.InstanceCount :[number](/docs/luau/numbers)

Provide feedback

---

MemoryTrackingEnabled

Read Only

Not Replicated

Read Parallel

Stats.MemoryTrackingEnabled :[boolean](/docs/luau/booleans)

Provide feedback

---

MovingPrimitivesCount

Read Only

Not Replicated

Read Parallel

Stats.MovingPrimitivesCount :[number](/docs/luau/numbers)

Provide feedback

---

PhysicsReceiveKbps

Read Only

Not Replicated

Read Parallel

Stats.PhysicsReceiveKbps :[number](/docs/luau/numbers)

Provide feedback

---

PhysicsSendKbps

Read Only

Not Replicated

Read Parallel

Stats.PhysicsSendKbps :[number](/docs/luau/numbers)

Provide feedback

---

PhysicsStepTime

Read Only

Not Replicated

Read Parallel

Stats.PhysicsStepTime :[number](/docs/luau/numbers)

Provide feedback

---

PhysicsStepTimeMs

Deprecated

Show details

---

PrimitivesCount

Read Only

Not Replicated

Read Parallel

Stats.PrimitivesCount :[number](/docs/luau/numbers)

Provide feedback

---

RenderCPUFrameTime

Read Only

Not Replicated

Read Parallel

Stats.RenderCPUFrameTime :[number](/docs/luau/numbers)

Provide feedback

---

RenderGPUFrameTime

Read Only

Not Replicated

Read Parallel

Stats.RenderGPUFrameTime :[number](/docs/luau/numbers)

Provide feedback

---

SceneDrawcallCount

Read Only

Not Replicated

Read Parallel

Stats.SceneDrawcallCount :[number](/docs/luau/numbers)

Provide feedback

---

SceneTriangleCount

Read Only

Not Replicated

Read Parallel

Stats.SceneTriangleCount :[number](/docs/luau/numbers)

Provide feedback

---

ShadowsDrawcallCount

Read Only

Not Replicated

Read Parallel

Stats.ShadowsDrawcallCount :[number](/docs/luau/numbers)

Provide feedback

---

ShadowsTriangleCount

Read Only

Not Replicated

Read Parallel

Stats.ShadowsTriangleCount :[number](/docs/luau/numbers)

Provide feedback

---

UI2DDrawcallCount

Read Only

Not Replicated

Read Parallel

Stats.UI2DDrawcallCount :[number](/docs/luau/numbers)

Provide feedback

---

UI2DTriangleCount

Read Only

Not Replicated

Read Parallel

Stats.UI2DTriangleCount :[number](/docs/luau/numbers)

Provide feedback

---

UI3DDrawcallCount

Read Only

Not Replicated

Read Parallel

Stats.UI3DDrawcallCount :[number](/docs/luau/numbers)

Provide feedback

---

UI3DTriangleCount

Read Only

Not Replicated

Read Parallel

Stats.UI3DTriangleCount :[number](/docs/luau/numbers)

Provide feedback

---

Methods

GetHarmonyQualityLevel

Capabilities: InternalTest

Stats:GetHarmonyQualityLevel () :[number](/docs/luau/numbers)

Returns

[number](/docs/luau/numbers)

Provide feedback

---

GetMemoryCategoryNames

Capabilities: InternalTest

Stats:GetMemoryCategoryNames () :[{any}](/docs/luau/tables#arrays)

Returns

[{any}](/docs/luau/tables#arrays)

Provide feedback

---

GetMemoryUsageMbAllCategories

Capabilities: InternalTest

Stats:GetMemoryUsageMbAllCategories () :[{any}](/docs/luau/tables#arrays)

Returns

[{any}](/docs/luau/tables#arrays)

Provide feedback

---

GetMemoryUsageMbForTag

Stats:GetMemoryUsageMbForTag (tag :[Enum.DeveloperMemoryTag](/docs/reference/engine/enums/DeveloperMemoryTag) ) :[number](/docs/luau/numbers)

Parameters

|

tag :[Enum.DeveloperMemoryTag](/docs/reference/engine/enums/DeveloperMemoryTag)

 |

Returns

[number](/docs/luau/numbers)

Provide feedback

---

GetTotalMemoryUsageMb

Stats:GetTotalMemoryUsageMb () :[number](/docs/luau/numbers)

Returns

[number](/docs/luau/numbers)

Provide feedback

---

ResetHarmonyMemoryTarget

Capabilities: InternalTest

Stats:ResetHarmonyMemoryTarget () : ()

Returns

()

Provide feedback

---

SetHarmonyMemoryTarget

Capabilities: InternalTest

Stats:SetHarmonyMemoryTarget (targetMB :[number](/docs/luau/numbers) ) : ()

Parameters

|

targetMB :[number](/docs/luau/numbers)

 |

Returns

()

Provide feedback

---

Jump to

▼

Stats

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[ContactsCount](#ContactsCount)

[DataReceiveKbps](#DataReceiveKbps)

[DataSendKbps](#DataSendKbps)

[FrameTime](#FrameTime)

[HeartbeatTime](#HeartbeatTime)

[HeartbeatTimeMs](#HeartbeatTimeMs)

[InstanceCount](#InstanceCount)

[MemoryTrackingEnabled](#MemoryTrackingEnabled)

[MovingPrimitivesCount](#MovingPrimitivesCount)

[PhysicsReceiveKbps](#PhysicsReceiveKbps)

[PhysicsSendKbps](#PhysicsSendKbps)

[PhysicsStepTime](#PhysicsStepTime)

[PhysicsStepTimeMs](#PhysicsStepTimeMs)

[PrimitivesCount](#PrimitivesCount)

[RenderCPUFrameTime](#RenderCPUFrameTime)

[RenderGPUFrameTime](#RenderGPUFrameTime)

[SceneDrawcallCount](#SceneDrawcallCount)

[SceneTriangleCount](#SceneTriangleCount)

[ShadowsDrawcallCount](#ShadowsDrawcallCount)

[ShadowsTriangleCount](#ShadowsTriangleCount)

[UI2DDrawcallCount](#UI2DDrawcallCount)

[UI2DTriangleCount](#UI2DTriangleCount)

[UI3DDrawcallCount](#UI3DDrawcallCount)

[UI3DTriangleCount](#UI3DTriangleCount)

[Methods](#methods)

[GetHarmonyQualityLevel()](#GetHarmonyQualityLevel)

[GetMemoryCategoryNames()](#GetMemoryCategoryNames)

[GetMemoryUsageMbAllCategories()](#GetMemoryUsageMbAllCategories)

[GetMemoryUsageMbForTag()](#GetMemoryUsageMbForTag)

[GetTotalMemoryUsageMb()](#GetTotalMemoryUsageMb)

[ResetHarmonyMemoryTarget()](#ResetHarmonyMemoryTarget)

[SetHarmonyMemoryTarget()](#SetHarmonyMemoryTarget)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
