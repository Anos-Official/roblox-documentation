<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/ValueCurve -->

ValueCurve | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [ValueCurve](/docs/nl-nl/reference/engine/classes/ValueCurve)

Nederlands

Feedback

Engine-klasse

ValueCurve

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/ValueCurve)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Length](#Length) :[number](/docs/nl-nl/luau/numbers)

 |
| --- | --- |
|

[ValueType](#ValueType) :[string](/docs/nl-nl/luau/strings)

 |

Methoden

|

[GetKeyAtIndex](#GetKeyAtIndex) (index :  [number](/docs/nl-nl/luau/numbers) ) :[ValueCurveKey](/docs/nl-nl/reference/engine/datatypes/ValueCurveKey)

 |
|

[GetKeyIndicesAtTime](#GetKeyIndicesAtTime) (time :  [number](/docs/nl-nl/luau/numbers) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[GetKeys](#GetKeys) () :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[GetValueAtTime](#GetValueAtTime) (time :  [number](/docs/nl-nl/luau/numbers) ) : Variant ?

 |
|

[InsertKey](#InsertKey) (key :  [ValueCurveKey](/docs/nl-nl/reference/engine/datatypes/ValueCurveKey) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[InsertKeyValue](#InsertKeyValue) (time :  [number](/docs/nl-nl/luau/numbers) , value :  Variant , Interpolation :  [Enum.KeyInterpolationMode](/docs/nl-nl/reference/engine/enums/KeyInterpolationMode) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[RemoveKeyAtIndex](#RemoveKeyAtIndex) (startingIndex :  [number](/docs/nl-nl/luau/numbers) , count :  [number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[SetKeys](#SetKeys) (keys :  [{any}](/docs/nl-nl/luau/tables#arrays) ) :[number](/docs/nl-nl/luau/numbers)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

Length

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Basic

ValueCurve.Length :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

ValueType

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Basic

ValueCurve.ValueType :[string](/docs/nl-nl/luau/strings)

Feedback geven

---

Methoden

GetKeyAtIndex

Mogelijkheden: Basic

ValueCurve:GetKeyAtIndex (index :[number](/docs/nl-nl/luau/numbers) ) :[ValueCurveKey](/docs/nl-nl/reference/engine/datatypes/ValueCurveKey)

Parameters

|

index :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[ValueCurveKey](/docs/nl-nl/reference/engine/datatypes/ValueCurveKey)

Feedback geven

---

GetKeyIndicesAtTime

Mogelijkheden: Basic

ValueCurve:GetKeyIndicesAtTime (time :[number](/docs/nl-nl/luau/numbers) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

Parameters

|

time :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

GetKeys

Mogelijkheden: Basic

ValueCurve:GetKeys () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

GetValueAtTime

Mogelijkheden: Basic

ValueCurve:GetValueAtTime (time :[number](/docs/nl-nl/luau/numbers) ) : Variant ?

Parameters

|

time :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

Variant ?

Feedback geven

---

InsertKey

Mogelijkheden: Basic

ValueCurve:InsertKey (key :[ValueCurveKey](/docs/nl-nl/reference/engine/datatypes/ValueCurveKey) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

Parameters

|

key :[ValueCurveKey](/docs/nl-nl/reference/engine/datatypes/ValueCurveKey)

 |

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

InsertKeyValue

Mogelijkheden: Basic

ValueCurve:InsertKeyValue (

time :[number](/docs/nl-nl/luau/numbers) , value : Variant , Interpolation :[Enum.KeyInterpolationMode](/docs/nl-nl/reference/engine/enums/KeyInterpolationMode)

) :[{any}](/docs/nl-nl/luau/tables#arrays)

Parameters

|

time :[number](/docs/nl-nl/luau/numbers)

 |
|

value : Variant

 |
|

Interpolation :[Enum.KeyInterpolationMode](/docs/nl-nl/reference/engine/enums/KeyInterpolationMode)

 |

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

RemoveKeyAtIndex

Mogelijkheden: Basic

ValueCurve:RemoveKeyAtIndex (

startingIndex :[number](/docs/nl-nl/luau/numbers) , count :[number](/docs/nl-nl/luau/numbers)

) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

startingIndex :[number](/docs/nl-nl/luau/numbers)

 |
|

count :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 1 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

SetKeys

Mogelijkheden: Basic

ValueCurve:SetKeys (keys :[{any}](/docs/nl-nl/luau/tables#arrays) ) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

keys :[{any}](/docs/nl-nl/luau/tables#arrays)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Ga naar

▼

ValueCurve

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[Length](#Length)

[ValueType](#ValueType)

[Methoden](#methods)

[GetKeyAtIndex()](#GetKeyAtIndex)

[GetKeyIndicesAtTime()](#GetKeyIndicesAtTime)

[GetKeys()](#GetKeys)

[GetValueAtTime()](#GetValueAtTime)

[InsertKey()](#InsertKey)

[InsertKeyValue()](#InsertKeyValue)

[RemoveKeyAtIndex()](#RemoveKeyAtIndex)

[SetKeys()](#SetKeys)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
