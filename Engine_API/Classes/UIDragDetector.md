<!-- Source: https://create.roblox.com/docs/reference/engine/classes/UIDragDetector -->

UIDragDetector | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/UIDragDetector.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [UIBase](/docs/reference/engine/classes/UIBase)
8. /
9. [UIComponent](/docs/reference/engine/classes/UIComponent)
10. /
11. [UIDragDetector](/docs/reference/engine/classes/UIDragDetector)

English

Feedback

Engine Class

UIDragDetector

---

## Summary

Properties

|

[ActivatedCursorIcon](#ActivatedCursorIcon) : ContentId

 |
| --- | --- |
|

[ActivatedCursorIconContent](#ActivatedCursorIconContent) :[Content](/docs/reference/engine/datatypes/Content)

 |
|

[BoundingBehavior](#BoundingBehavior) :[Enum.UIDragDetectorBoundingBehavior](/docs/reference/engine/enums/UIDragDetectorBoundingBehavior)

 |
|

[BoundingUI](#BoundingUI) :[GuiBase2d](/docs/reference/engine/classes/GuiBase2d)

 |
|

[CursorIcon](#CursorIcon) : ContentId

 |
|

[CursorIconContent](#CursorIconContent) :[Content](/docs/reference/engine/datatypes/Content)

 |
|

[DragAxis](#DragAxis) :[Vector2](/docs/reference/engine/datatypes/Vector2)

 |
|

[DragRelativity](#DragRelativity) :[Enum.UIDragDetectorDragRelativity](/docs/reference/engine/enums/UIDragDetectorDragRelativity)

 |
|

[DragRotation](#DragRotation) :[number](/docs/luau/numbers)

 |
|

[DragSpace](#DragSpace) :[Enum.UIDragDetectorDragSpace](/docs/reference/engine/enums/UIDragDetectorDragSpace)

 |
|

[DragStyle](#DragStyle) :[Enum.UIDragDetectorDragStyle](/docs/reference/engine/enums/UIDragDetectorDragStyle)

 |
|

[DragUDim2](#DragUDim2) :[UDim2](/docs/reference/engine/datatypes/UDim2)

 |
|

[Enabled](#Enabled) :[boolean](/docs/luau/booleans)

 |
|

[MaxDragAngle](#MaxDragAngle) :[number](/docs/luau/numbers)

 |
|

[MaxDragTranslation](#MaxDragTranslation) :[UDim2](/docs/reference/engine/datatypes/UDim2)

 |
|

[MinDragAngle](#MinDragAngle) :[number](/docs/luau/numbers)

 |
|

[MinDragTranslation](#MinDragTranslation) :[UDim2](/docs/reference/engine/datatypes/UDim2)

 |
|

[ReferenceUIInstance](#ReferenceUIInstance) :[GuiObject](/docs/reference/engine/classes/GuiObject)

 |
|

[ResponseStyle](#ResponseStyle) :[Enum.UIDragDetectorResponseStyle](/docs/reference/engine/enums/UIDragDetectorResponseStyle)

 |
|

[SelectionModeDragSpeed](#SelectionModeDragSpeed) :[UDim2](/docs/reference/engine/datatypes/UDim2)

 |
|

[SelectionModeRotateSpeed](#SelectionModeRotateSpeed) :[number](/docs/luau/numbers)

 |
|

[UIDragSpeedAxisMapping](#UIDragSpeedAxisMapping) :[Enum.UIDragSpeedAxisMapping](/docs/reference/engine/enums/UIDragSpeedAxisMapping)

 |

Methods

|

[AddConstraintFunction](#AddConstraintFunction) (priority :  [number](/docs/luau/numbers) , function :  [function](/docs/luau/functions) ) :[RBXScriptConnection](/docs/reference/engine/datatypes/RBXScriptConnection)

 |
|

[GetReferencePosition](#GetReferencePosition) () :[UDim2](/docs/reference/engine/datatypes/UDim2)

 |
|

[GetReferenceRotation](#GetReferenceRotation) () :[number](/docs/luau/numbers)

 |
|

[SetDragStyleFunction](#SetDragStyleFunction) (function :  [function](/docs/luau/functions) ) : ()

 |

Events

|

[DragContinue](#DragContinue) (inputPosition :  [Vector2](/docs/reference/engine/datatypes/Vector2) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |
|

[DragEnd](#DragEnd) (inputPosition :  [Vector2](/docs/reference/engine/datatypes/Vector2) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |
|

[DragStart](#DragStart) (inputPosition :  [Vector2](/docs/reference/engine/datatypes/Vector2) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Properties

ActivatedCursorIcon

Read Parallel

Capabilities: UI

UIDragDetector.ActivatedCursorIcon : ContentId

Provide feedback

---

ActivatedCursorIconContent

Read Parallel

Capabilities: UI

UIDragDetector.ActivatedCursorIconContent :[Content](/docs/reference/engine/datatypes/Content)

Provide feedback

---

BoundingBehavior

Read Parallel

Capabilities: UI

UIDragDetector.BoundingBehavior :[Enum.UIDragDetectorBoundingBehavior](/docs/reference/engine/enums/UIDragDetectorBoundingBehavior)

Provide feedback

---

BoundingUI

Read Parallel

Capabilities: UI

UIDragDetector.BoundingUI :[GuiBase2d](/docs/reference/engine/classes/GuiBase2d)

Provide feedback

---

CursorIcon

Read Parallel

Capabilities: UI

UIDragDetector.CursorIcon : ContentId

Provide feedback

---

CursorIconContent

Read Parallel

Capabilities: UI

UIDragDetector.CursorIconContent :[Content](/docs/reference/engine/datatypes/Content)

Provide feedback

---

DragAxis

Read Parallel

Capabilities: UI

UIDragDetector.DragAxis :[Vector2](/docs/reference/engine/datatypes/Vector2)

Provide feedback

---

DragRelativity

Read Parallel

Capabilities: UI

UIDragDetector.DragRelativity :[Enum.UIDragDetectorDragRelativity](/docs/reference/engine/enums/UIDragDetectorDragRelativity)

Provide feedback

---

DragRotation

Read Parallel

Capabilities: UI

UIDragDetector.DragRotation :[number](/docs/luau/numbers)

Provide feedback

---

DragSpace

Read Parallel

Capabilities: UI

UIDragDetector.DragSpace :[Enum.UIDragDetectorDragSpace](/docs/reference/engine/enums/UIDragDetectorDragSpace)

Provide feedback

---

DragStyle

Read Parallel

Capabilities: UI

UIDragDetector.DragStyle :[Enum.UIDragDetectorDragStyle](/docs/reference/engine/enums/UIDragDetectorDragStyle)

Provide feedback

---

DragUDim2

Read Parallel

Capabilities: UI

UIDragDetector.DragUDim2 :[UDim2](/docs/reference/engine/datatypes/UDim2)

Provide feedback

---

Enabled

Read Parallel

Capabilities: UI

UIDragDetector.Enabled :[boolean](/docs/luau/booleans)

Provide feedback

---

MaxDragAngle

Read Parallel

Capabilities: UI

UIDragDetector.MaxDragAngle :[number](/docs/luau/numbers)

Provide feedback

---

MaxDragTranslation

Read Parallel

Capabilities: UI

UIDragDetector.MaxDragTranslation :[UDim2](/docs/reference/engine/datatypes/UDim2)

Provide feedback

---

MinDragAngle

Read Parallel

Capabilities: UI

UIDragDetector.MinDragAngle :[number](/docs/luau/numbers)

Provide feedback

---

MinDragTranslation

Read Parallel

Capabilities: UI

UIDragDetector.MinDragTranslation :[UDim2](/docs/reference/engine/datatypes/UDim2)

Provide feedback

---

ReferenceUIInstance

Read Parallel

Capabilities: UI

UIDragDetector.ReferenceUIInstance :[GuiObject](/docs/reference/engine/classes/GuiObject)

Provide feedback

---

ResponseStyle

Read Parallel

Capabilities: UI

UIDragDetector.ResponseStyle :[Enum.UIDragDetectorResponseStyle](/docs/reference/engine/enums/UIDragDetectorResponseStyle)

Provide feedback

---

SelectionModeDragSpeed

Read Parallel

Capabilities: UI

UIDragDetector.SelectionModeDragSpeed :[UDim2](/docs/reference/engine/datatypes/UDim2)

Provide feedback

---

SelectionModeRotateSpeed

Read Parallel

Capabilities: UI

UIDragDetector.SelectionModeRotateSpeed :[number](/docs/luau/numbers)

Provide feedback

---

UIDragSpeedAxisMapping

Read Parallel

Capabilities: UI

UIDragDetector.UIDragSpeedAxisMapping :[Enum.UIDragSpeedAxisMapping](/docs/reference/engine/enums/UIDragSpeedAxisMapping)

Provide feedback

---

Methods

AddConstraintFunction

Capabilities: UI

UIDragDetector:AddConstraintFunction (

priority :[number](/docs/luau/numbers) , function :[function](/docs/luau/functions)

) :[RBXScriptConnection](/docs/reference/engine/datatypes/RBXScriptConnection)

Parameters

|

priority :[number](/docs/luau/numbers)

 |
|

function :[function](/docs/luau/functions)

 |

Returns

[RBXScriptConnection](/docs/reference/engine/datatypes/RBXScriptConnection)

Provide feedback

---

GetReferencePosition

Capabilities: UI

UIDragDetector:GetReferencePosition () :[UDim2](/docs/reference/engine/datatypes/UDim2)

Returns

[UDim2](/docs/reference/engine/datatypes/UDim2)

Provide feedback

---

GetReferenceRotation

Capabilities: UI

UIDragDetector:GetReferenceRotation () :[number](/docs/luau/numbers)

Returns

[number](/docs/luau/numbers)

Provide feedback

---

SetDragStyleFunction

Capabilities: UI

UIDragDetector:SetDragStyleFunction (function :[function](/docs/luau/functions) ) : ()

Parameters

|

function :[function](/docs/luau/functions)

 |

Returns

()

Provide feedback

---

Events

DragContinue

Capabilities: UI

UIDragDetector.DragContinue (inputPosition :[Vector2](/docs/reference/engine/datatypes/Vector2) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

inputPosition :[Vector2](/docs/reference/engine/datatypes/Vector2)

 |

Provide feedback

---

DragEnd

Capabilities: UI

UIDragDetector.DragEnd (inputPosition :[Vector2](/docs/reference/engine/datatypes/Vector2) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

inputPosition :[Vector2](/docs/reference/engine/datatypes/Vector2)

 |

Provide feedback

---

DragStart

Capabilities: UI

UIDragDetector.DragStart (inputPosition :[Vector2](/docs/reference/engine/datatypes/Vector2) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

inputPosition :[Vector2](/docs/reference/engine/datatypes/Vector2)

 |

Provide feedback

---

Jump to

▼

UIDragDetector

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[ActivatedCursorIcon](#ActivatedCursorIcon)

[ActivatedCursorIconContent](#ActivatedCursorIconContent)

[BoundingBehavior](#BoundingBehavior)

[BoundingUI](#BoundingUI)

[CursorIcon](#CursorIcon)

[CursorIconContent](#CursorIconContent)

[DragAxis](#DragAxis)

[DragRelativity](#DragRelativity)

[DragRotation](#DragRotation)

[DragSpace](#DragSpace)

[DragStyle](#DragStyle)

[DragUDim2](#DragUDim2)

[Enabled](#Enabled)

[MaxDragAngle](#MaxDragAngle)

[MaxDragTranslation](#MaxDragTranslation)

[MinDragAngle](#MinDragAngle)

[MinDragTranslation](#MinDragTranslation)

[ReferenceUIInstance](#ReferenceUIInstance)

[ResponseStyle](#ResponseStyle)

[SelectionModeDragSpeed](#SelectionModeDragSpeed)

[SelectionModeRotateSpeed](#SelectionModeRotateSpeed)

[UIDragSpeedAxisMapping](#UIDragSpeedAxisMapping)

[Methods](#methods)

[AddConstraintFunction()](#AddConstraintFunction)

[GetReferencePosition()](#GetReferencePosition)

[GetReferenceRotation()](#GetReferenceRotation)

[SetDragStyleFunction()](#SetDragStyleFunction)

[Events](#events)

[DragContinue](#DragContinue)

[DragEnd](#DragEnd)

[DragStart](#DragStart)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
