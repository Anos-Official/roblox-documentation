<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/Path2D -->

Path2D | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Path2D.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [GuiBase](/docs/en-us/reference/engine/classes/GuiBase)
8. /
9. [Path2D](/docs/en-us/reference/engine/classes/Path2D)

English

Feedback

Engine Class

Path2D

---

## Summary

Properties

|

[Closed](#Closed) :[boolean](/docs/en-us/luau/booleans)

 |
| --- | --- |
|

[Color3](#Color3) :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

 |
|

[SelectedControlPoint](#SelectedControlPoint) :[number](/docs/en-us/luau/numbers)

 |
|

[SelectedControlPointData](#SelectedControlPointData) :[Path2DControlPoint](/docs/en-us/reference/engine/datatypes/Path2DControlPoint)

 |
|

[Thickness](#Thickness) :[number](/docs/en-us/luau/numbers)

 |
|

[Visible](#Visible) :[boolean](/docs/en-us/luau/booleans)

 |
|

[ZIndex](#ZIndex) :[number](/docs/en-us/luau/numbers)

 |

Methods

|

[GetBoundingRect](#GetBoundingRect) () :[Rect](/docs/en-us/reference/engine/datatypes/Rect)

 |
|

[GetControlPoint](#GetControlPoint) (index :  [number](/docs/en-us/luau/numbers) ) :[Path2DControlPoint](/docs/en-us/reference/engine/datatypes/Path2DControlPoint)

 |
|

[GetControlPoints](#GetControlPoints) () :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[GetLength](#GetLength) () :[number](/docs/en-us/luau/numbers)

 |
|

[GetMaxControlPoints](#GetMaxControlPoints) () :[number](/docs/en-us/luau/numbers)

 |
|

[GetPositionOnCurve](#GetPositionOnCurve) (t :  [number](/docs/en-us/luau/numbers) ) :[UDim2](/docs/en-us/reference/engine/datatypes/UDim2)

 |
|

[GetPositionOnCurveArcLength](#GetPositionOnCurveArcLength) (t :  [number](/docs/en-us/luau/numbers) ) :[UDim2](/docs/en-us/reference/engine/datatypes/UDim2)

 |
|

[GetTangentOnCurve](#GetTangentOnCurve) (t :  [number](/docs/en-us/luau/numbers) ) :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
|

[GetTangentOnCurveArcLength](#GetTangentOnCurveArcLength) (t :  [number](/docs/en-us/luau/numbers) ) :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
|

[InsertControlPoint](#InsertControlPoint) (index :  [number](/docs/en-us/luau/numbers) , point :  [Path2DControlPoint](/docs/en-us/reference/engine/datatypes/Path2DControlPoint) ) : ()

 |
|

[RemoveControlPoint](#RemoveControlPoint) (index :  [number](/docs/en-us/luau/numbers) ) : ()

 |
|

[SetControlPoints](#SetControlPoints) (controlPoints :  [{any}](/docs/en-us/luau/tables#arrays) ) : ()

 |
|

[UpdateControlPoint](#UpdateControlPoint) (index :  [number](/docs/en-us/luau/numbers) , point :  [Path2DControlPoint](/docs/en-us/reference/engine/datatypes/Path2DControlPoint) ) : ()

 |

Events

|

[ControlPointChanged](#ControlPointChanged) () :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Properties

Closed

Read Parallel

Capabilities: UI

Path2D.Closed :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

Color3

Read Parallel

Capabilities: UI

Path2D.Color3 :[Color3](/docs/en-us/reference/engine/datatypes/Color3)

Provide feedback

---

SelectedControlPoint

Not Replicated

Roblox Script Security

Read Parallel

Capabilities: UI

Path2D.SelectedControlPoint :[number](/docs/en-us/luau/numbers)

Provide feedback

---

SelectedControlPointData

Not Replicated

Roblox Script Security

Read Parallel

Capabilities: UI

Path2D.SelectedControlPointData :[Path2DControlPoint](/docs/en-us/reference/engine/datatypes/Path2DControlPoint)

Provide feedback

---

Thickness

Read Parallel

Capabilities: UI

Path2D.Thickness :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Visible

Read Parallel

Capabilities: UI

Path2D.Visible :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

ZIndex

Read Parallel

Capabilities: UI

Path2D.ZIndex :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Methods

GetBoundingRect

Capabilities: UI

Path2D:GetBoundingRect () :[Rect](/docs/en-us/reference/engine/datatypes/Rect)

Returns

[Rect](/docs/en-us/reference/engine/datatypes/Rect)

Provide feedback

---

GetControlPoint

Capabilities: UI

Path2D:GetControlPoint (index :[number](/docs/en-us/luau/numbers) ) :[Path2DControlPoint](/docs/en-us/reference/engine/datatypes/Path2DControlPoint)

Parameters

|

index :[number](/docs/en-us/luau/numbers)

 |

Returns

[Path2DControlPoint](/docs/en-us/reference/engine/datatypes/Path2DControlPoint)

Provide feedback

---

GetControlPoints

Capabilities: UI

Path2D:GetControlPoints () :[{any}](/docs/en-us/luau/tables#arrays)

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

GetLength

Capabilities: UI

Path2D:GetLength () :[number](/docs/en-us/luau/numbers)

Returns

[number](/docs/en-us/luau/numbers)

Provide feedback

---

GetMaxControlPoints

Capabilities: UI

Path2D:GetMaxControlPoints () :[number](/docs/en-us/luau/numbers)

Returns

[number](/docs/en-us/luau/numbers)

Provide feedback

---

GetPositionOnCurve

Capabilities: UI

Path2D:GetPositionOnCurve (t :[number](/docs/en-us/luau/numbers) ) :[UDim2](/docs/en-us/reference/engine/datatypes/UDim2)

Parameters

|

t :[number](/docs/en-us/luau/numbers)

 |

Returns

[UDim2](/docs/en-us/reference/engine/datatypes/UDim2)

Provide feedback

---

GetPositionOnCurveArcLength

Capabilities: UI

Path2D:GetPositionOnCurveArcLength (t :[number](/docs/en-us/luau/numbers) ) :[UDim2](/docs/en-us/reference/engine/datatypes/UDim2)

Parameters

|

t :[number](/docs/en-us/luau/numbers)

 |

Returns

[UDim2](/docs/en-us/reference/engine/datatypes/UDim2)

Provide feedback

---

GetTangentOnCurve

Capabilities: UI

Path2D:GetTangentOnCurve (t :[number](/docs/en-us/luau/numbers) ) :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Parameters

|

t :[number](/docs/en-us/luau/numbers)

 |

Returns

[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Provide feedback

---

GetTangentOnCurveArcLength

Capabilities: UI

Path2D:GetTangentOnCurveArcLength (t :[number](/docs/en-us/luau/numbers) ) :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Parameters

|

t :[number](/docs/en-us/luau/numbers)

 |

Returns

[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Provide feedback

---

InsertControlPoint

Capabilities: UI

Path2D:InsertControlPoint (

index :[number](/docs/en-us/luau/numbers) , point :[Path2DControlPoint](/docs/en-us/reference/engine/datatypes/Path2DControlPoint)

) : ()

Parameters

|

index :[number](/docs/en-us/luau/numbers)

 |
|

point :[Path2DControlPoint](/docs/en-us/reference/engine/datatypes/Path2DControlPoint)

 |

Returns

()

Provide feedback

---

RemoveControlPoint

Capabilities: UI

Path2D:RemoveControlPoint (index :[number](/docs/en-us/luau/numbers) ) : ()

Parameters

|

index :[number](/docs/en-us/luau/numbers)

 |

Returns

()

Provide feedback

---

SetControlPoints

Capabilities: UI

Path2D:SetControlPoints (controlPoints :[{any}](/docs/en-us/luau/tables#arrays) ) : ()

Parameters

|

controlPoints :[{any}](/docs/en-us/luau/tables#arrays)

 |

Returns

()

Provide feedback

---

UpdateControlPoint

Capabilities: UI

Path2D:UpdateControlPoint (

index :[number](/docs/en-us/luau/numbers) , point :[Path2DControlPoint](/docs/en-us/reference/engine/datatypes/Path2DControlPoint)

) : ()

Parameters

|

index :[number](/docs/en-us/luau/numbers)

 |
|

point :[Path2DControlPoint](/docs/en-us/reference/engine/datatypes/Path2DControlPoint)

 |

Returns

()

Provide feedback

---

Events

ControlPointChanged

Capabilities: UI

Path2D.ControlPointChanged () :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Provide feedback

---

Jump to

▼

Path2D

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[Closed](#Closed)

[Color3](#Color3)

[SelectedControlPoint](#SelectedControlPoint)

[SelectedControlPointData](#SelectedControlPointData)

[Thickness](#Thickness)

[Visible](#Visible)

[ZIndex](#ZIndex)

[Methods](#methods)

[GetBoundingRect()](#GetBoundingRect)

[GetControlPoint()](#GetControlPoint)

[GetControlPoints()](#GetControlPoints)

[GetLength()](#GetLength)

[GetMaxControlPoints()](#GetMaxControlPoints)

[GetPositionOnCurve()](#GetPositionOnCurve)

[GetPositionOnCurveArcLength()](#GetPositionOnCurveArcLength)

[GetTangentOnCurve()](#GetTangentOnCurve)

[GetTangentOnCurveArcLength()](#GetTangentOnCurveArcLength)

[InsertControlPoint()](#InsertControlPoint)

[RemoveControlPoint()](#RemoveControlPoint)

[SetControlPoints()](#SetControlPoints)

[UpdateControlPoint()](#UpdateControlPoint)

[Events](#events)

[ControlPointChanged](#ControlPointChanged)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
