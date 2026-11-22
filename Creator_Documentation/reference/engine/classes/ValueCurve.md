<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/ValueCurve -->

ValueCurve | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/ValueCurve.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [ValueCurve](/docs/en-us/reference/engine/classes/ValueCurve)

English

Feedback

Engine Class

ValueCurve

---

## Summary

Properties

|

[Length](#Length) :[number](/docs/en-us/luau/numbers)

 |
| --- | --- |
|

[ValueType](#ValueType) :[string](/docs/en-us/luau/strings)

 |

Methods

|

[GetKeyAtIndex](#GetKeyAtIndex) (index :  [number](/docs/en-us/luau/numbers) ) :[ValueCurveKey](/docs/en-us/reference/engine/datatypes/ValueCurveKey)

 |
|

[GetKeyIndicesAtTime](#GetKeyIndicesAtTime) (time :  [number](/docs/en-us/luau/numbers) ) :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[GetKeys](#GetKeys) () :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[GetValueAtTime](#GetValueAtTime) (time :  [number](/docs/en-us/luau/numbers) ) : Variant ?

 |
|

[InsertKey](#InsertKey) (key :  [ValueCurveKey](/docs/en-us/reference/engine/datatypes/ValueCurveKey) ) :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[InsertKeyValue](#InsertKeyValue) (time :  [number](/docs/en-us/luau/numbers) , value :  Variant , Interpolation :  [Enum.KeyInterpolationMode](/docs/en-us/reference/engine/enums/KeyInterpolationMode) ) :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[RemoveKeyAtIndex](#RemoveKeyAtIndex) (startingIndex :  [number](/docs/en-us/luau/numbers) , count :  [number](/docs/en-us/luau/numbers) ) :[number](/docs/en-us/luau/numbers)

 |
|

[SetKeys](#SetKeys) (keys :  [{any}](/docs/en-us/luau/tables#arrays) ) :[number](/docs/en-us/luau/numbers)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Properties

Length

Read Only

Not Replicated

Read Parallel

Capabilities: Basic

ValueCurve.Length :[number](/docs/en-us/luau/numbers)

Provide feedback

---

ValueType

Read Only

Not Replicated

Read Parallel

Capabilities: Basic

ValueCurve.ValueType :[string](/docs/en-us/luau/strings)

Provide feedback

---

Methods

GetKeyAtIndex

Capabilities: Basic

ValueCurve:GetKeyAtIndex (index :[number](/docs/en-us/luau/numbers) ) :[ValueCurveKey](/docs/en-us/reference/engine/datatypes/ValueCurveKey)

Parameters

|

index :[number](/docs/en-us/luau/numbers)

 |

Returns

[ValueCurveKey](/docs/en-us/reference/engine/datatypes/ValueCurveKey)

Provide feedback

---

GetKeyIndicesAtTime

Capabilities: Basic

ValueCurve:GetKeyIndicesAtTime (time :[number](/docs/en-us/luau/numbers) ) :[{any}](/docs/en-us/luau/tables#arrays)

Parameters

|

time :[number](/docs/en-us/luau/numbers)

 |

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

GetKeys

Capabilities: Basic

ValueCurve:GetKeys () :[{any}](/docs/en-us/luau/tables#arrays)

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

GetValueAtTime

Capabilities: Basic

ValueCurve:GetValueAtTime (time :[number](/docs/en-us/luau/numbers) ) : Variant ?

Parameters

|

time :[number](/docs/en-us/luau/numbers)

 |

Returns

Variant ?

Provide feedback

---

InsertKey

Capabilities: Basic

ValueCurve:InsertKey (key :[ValueCurveKey](/docs/en-us/reference/engine/datatypes/ValueCurveKey) ) :[{any}](/docs/en-us/luau/tables#arrays)

Parameters

|

key :[ValueCurveKey](/docs/en-us/reference/engine/datatypes/ValueCurveKey)

 |

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

InsertKeyValue

Capabilities: Basic

ValueCurve:InsertKeyValue (

time :[number](/docs/en-us/luau/numbers) , value : Variant , Interpolation :[Enum.KeyInterpolationMode](/docs/en-us/reference/engine/enums/KeyInterpolationMode)

) :[{any}](/docs/en-us/luau/tables#arrays)

Parameters

|

time :[number](/docs/en-us/luau/numbers)

 |
|

value : Variant

 |
|

Interpolation :[Enum.KeyInterpolationMode](/docs/en-us/reference/engine/enums/KeyInterpolationMode)

 |

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

RemoveKeyAtIndex

Capabilities: Basic

ValueCurve:RemoveKeyAtIndex (

startingIndex :[number](/docs/en-us/luau/numbers) , count :[number](/docs/en-us/luau/numbers)

) :[number](/docs/en-us/luau/numbers)

Parameters

|

startingIndex :[number](/docs/en-us/luau/numbers)

 |
|

count :[number](/docs/en-us/luau/numbers)

Default Value: 1 |

Returns

[number](/docs/en-us/luau/numbers)

Provide feedback

---

SetKeys

Capabilities: Basic

ValueCurve:SetKeys (keys :[{any}](/docs/en-us/luau/tables#arrays) ) :[number](/docs/en-us/luau/numbers)

Parameters

|

keys :[{any}](/docs/en-us/luau/tables#arrays)

 |

Returns

[number](/docs/en-us/luau/numbers)

Provide feedback

---

Jump to

▼

ValueCurve

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[Length](#Length)

[ValueType](#ValueType)

[Methods](#methods)

[GetKeyAtIndex()](#GetKeyAtIndex)

[GetKeyIndicesAtTime()](#GetKeyIndicesAtTime)

[GetKeys()](#GetKeys)

[GetValueAtTime()](#GetValueAtTime)

[InsertKey()](#InsertKey)

[InsertKeyValue()](#InsertKeyValue)

[RemoveKeyAtIndex()](#RemoveKeyAtIndex)

[SetKeys()](#SetKeys)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
