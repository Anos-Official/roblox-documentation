<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Path2D -->

Path2D | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [GuiBase](/docs/nl-nl/reference/engine/classes/GuiBase)
8. /
9. [Path2D](/docs/nl-nl/reference/engine/classes/Path2D)

Nederlands

Feedback

Engine-klasse

Path2D

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Path2D)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Closed](#Closed) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |
|

[Color3](#Color3) :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

 |
|

[SelectedControlPoint](#SelectedControlPoint) :[number](/docs/nl-nl/luau/numbers)

 |
|

[SelectedControlPointData](#SelectedControlPointData) :[Path2DControlPoint](/docs/nl-nl/reference/engine/datatypes/Path2DControlPoint)

 |
|

[Thickness](#Thickness) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Visible](#Visible) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[ZIndex](#ZIndex) :[number](/docs/nl-nl/luau/numbers)

 |

Methoden

|

[GetBoundingRect](#GetBoundingRect) () :[Rect](/docs/nl-nl/reference/engine/datatypes/Rect)

 |
|

[GetControlPoint](#GetControlPoint) (index :  [number](/docs/nl-nl/luau/numbers) ) :[Path2DControlPoint](/docs/nl-nl/reference/engine/datatypes/Path2DControlPoint)

 |
|

[GetControlPoints](#GetControlPoints) () :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[GetLength](#GetLength) () :[number](/docs/nl-nl/luau/numbers)

 |
|

[GetMaxControlPoints](#GetMaxControlPoints) () :[number](/docs/nl-nl/luau/numbers)

 |
|

[GetPositionOnCurve](#GetPositionOnCurve) (t :  [number](/docs/nl-nl/luau/numbers) ) :[UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)

 |
|

[GetPositionOnCurveArcLength](#GetPositionOnCurveArcLength) (t :  [number](/docs/nl-nl/luau/numbers) ) :[UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)

 |
|

[GetTangentOnCurve](#GetTangentOnCurve) (t :  [number](/docs/nl-nl/luau/numbers) ) :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

[GetTangentOnCurveArcLength](#GetTangentOnCurveArcLength) (t :  [number](/docs/nl-nl/luau/numbers) ) :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

[InsertControlPoint](#InsertControlPoint) (index :  [number](/docs/nl-nl/luau/numbers) , point :  [Path2DControlPoint](/docs/nl-nl/reference/engine/datatypes/Path2DControlPoint) ) : ()

 |
|

[RemoveControlPoint](#RemoveControlPoint) (index :  [number](/docs/nl-nl/luau/numbers) ) : ()

 |
|

[SetControlPoints](#SetControlPoints) (controlPoints :  [{any}](/docs/nl-nl/luau/tables#arrays) ) : ()

 |
|

[UpdateControlPoint](#UpdateControlPoint) (index :  [number](/docs/nl-nl/luau/numbers) , point :  [Path2DControlPoint](/docs/nl-nl/reference/engine/datatypes/Path2DControlPoint) ) : ()

 |

Evenementen

|

[ControlPointChanged](#ControlPointChanged) () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

Closed

Parallel lezen

Mogelijkheden: UI

Path2D.Closed :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Color3

Parallel lezen

Mogelijkheden: UI

Path2D.Color3 :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

Feedback geven

---

SelectedControlPoint

Niet gerepliceerd

Roblox-scriptbeveiliging

Parallel lezen

Mogelijkheden: UI

Path2D.SelectedControlPoint :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

SelectedControlPointData

Niet gerepliceerd

Roblox-scriptbeveiliging

Parallel lezen

Mogelijkheden: UI

Path2D.SelectedControlPointData :[Path2DControlPoint](/docs/nl-nl/reference/engine/datatypes/Path2DControlPoint)

Feedback geven

---

Thickness

Parallel lezen

Mogelijkheden: UI

Path2D.Thickness :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Visible

Parallel lezen

Mogelijkheden: UI

Path2D.Visible :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

ZIndex

Parallel lezen

Mogelijkheden: UI

Path2D.ZIndex :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Methoden

GetBoundingRect

Mogelijkheden: UI

Path2D:GetBoundingRect () :[Rect](/docs/nl-nl/reference/engine/datatypes/Rect)

Teruggaves

[Rect](/docs/nl-nl/reference/engine/datatypes/Rect)

Feedback geven

---

GetControlPoint

Mogelijkheden: UI

Path2D:GetControlPoint (index :[number](/docs/nl-nl/luau/numbers) ) :[Path2DControlPoint](/docs/nl-nl/reference/engine/datatypes/Path2DControlPoint)

Parameters

|

index :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[Path2DControlPoint](/docs/nl-nl/reference/engine/datatypes/Path2DControlPoint)

Feedback geven

---

GetControlPoints

Mogelijkheden: UI

Path2D:GetControlPoints () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

GetLength

Mogelijkheden: UI

Path2D:GetLength () :[number](/docs/nl-nl/luau/numbers)

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

GetMaxControlPoints

Mogelijkheden: UI

Path2D:GetMaxControlPoints () :[number](/docs/nl-nl/luau/numbers)

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

GetPositionOnCurve

Mogelijkheden: UI

Path2D:GetPositionOnCurve (t :[number](/docs/nl-nl/luau/numbers) ) :[UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)

Parameters

|

t :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)

Feedback geven

---

GetPositionOnCurveArcLength

Mogelijkheden: UI

Path2D:GetPositionOnCurveArcLength (t :[number](/docs/nl-nl/luau/numbers) ) :[UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)

Parameters

|

t :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)

Feedback geven

---

GetTangentOnCurve

Mogelijkheden: UI

Path2D:GetTangentOnCurve (t :[number](/docs/nl-nl/luau/numbers) ) :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Parameters

|

t :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Feedback geven

---

GetTangentOnCurveArcLength

Mogelijkheden: UI

Path2D:GetTangentOnCurveArcLength (t :[number](/docs/nl-nl/luau/numbers) ) :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Parameters

|

t :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Feedback geven

---

InsertControlPoint

Mogelijkheden: UI

Path2D:InsertControlPoint (

index :[number](/docs/nl-nl/luau/numbers) , point :[Path2DControlPoint](/docs/nl-nl/reference/engine/datatypes/Path2DControlPoint)

) : ()

Parameters

|

index :[number](/docs/nl-nl/luau/numbers)

 |
|

point :[Path2DControlPoint](/docs/nl-nl/reference/engine/datatypes/Path2DControlPoint)

 |

Teruggaves

()

Feedback geven

---

RemoveControlPoint

Mogelijkheden: UI

Path2D:RemoveControlPoint (index :[number](/docs/nl-nl/luau/numbers) ) : ()

Parameters

|

index :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

()

Feedback geven

---

SetControlPoints

Mogelijkheden: UI

Path2D:SetControlPoints (controlPoints :[{any}](/docs/nl-nl/luau/tables#arrays) ) : ()

Parameters

|

controlPoints :[{any}](/docs/nl-nl/luau/tables#arrays)

 |

Teruggaves

()

Feedback geven

---

UpdateControlPoint

Mogelijkheden: UI

Path2D:UpdateControlPoint (

index :[number](/docs/nl-nl/luau/numbers) , point :[Path2DControlPoint](/docs/nl-nl/reference/engine/datatypes/Path2DControlPoint)

) : ()

Parameters

|

index :[number](/docs/nl-nl/luau/numbers)

 |
|

point :[Path2DControlPoint](/docs/nl-nl/reference/engine/datatypes/Path2DControlPoint)

 |

Teruggaves

()

Feedback geven

---

Evenementen

ControlPointChanged

Mogelijkheden: UI

Path2D.ControlPointChanged () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Feedback geven

---

Ga naar

▼

Path2D

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[Closed](#Closed)

[Color3](#Color3)

[SelectedControlPoint](#SelectedControlPoint)

[SelectedControlPointData](#SelectedControlPointData)

[Thickness](#Thickness)

[Visible](#Visible)

[ZIndex](#ZIndex)

[Methoden](#methods)

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

[Evenementen](#events)

[ControlPointChanged](#ControlPointChanged)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
