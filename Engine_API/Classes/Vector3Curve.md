<!-- Source: https://create.roblox.com/docs/reference/engine/classes/Vector3Curve -->

Vector3Curve | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Vector3Curve.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [Vector3Curve](/docs/reference/engine/classes/Vector3Curve)

English

Feedback

Engine Class

Vector3Curve

---

## Summary

Methods

|

[GetValueAtTime](#GetValueAtTime) (time :  [number](/docs/luau/numbers) ) :[{any}](/docs/luau/tables#arrays)

 |
| --- | --- |
|

[X](#X) () :[FloatCurve](/docs/reference/engine/classes/FloatCurve)

 |
|

[Y](#Y) () :[FloatCurve](/docs/reference/engine/classes/FloatCurve)

 |
|

[Z](#Z) () :[FloatCurve](/docs/reference/engine/classes/FloatCurve)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

Creating a Vector3Curve

```

--- Vector3Curve

local function createVector3Curve()

	local vectorCurve = Instance.new("Vector3Curve")

	local curveX = vectorCurve:X() -- creates and returns a FloatCurve animating the X channel

	local curveY = vectorCurve:Y() -- creates and returns a FloatCurve animating the Y channel

	-- Not setting the Z channel will leave the Z channel not animated.

	-- A missing curve or a curve with no keys don't participate in the animation

	local key = FloatCurveKey.new(0, 1) -- creates a key at time 0 and with value 1

	curveX:InsertKey(key)

	curveY:InsertKey(key)

	local key2 = FloatCurveKey.new(1, 2) -- creates a key at time 1 and with value 2

	curveX:InsertKey(key2)

	curveY:InsertKey(key2)

	return vectorCurve

end

local function testVector3Curve()

	local curve = createVector3Curve()

	-- sampling the curve at a given time (returns a vector3)

	print(curve:GetValueAtTime(0)) -- returns 1, 1, void

	print(curve:GetValueAtTime(0.5)) -- returns 1.5, 1.5, void (result of cubic interpolation with auto tangents)

	curve:X():RemoveKeyAtIndex(1)

	curve:X():RemoveKeyAtIndex(1)

	print(curve:X().Length) -- number of keys = 0

	print(curve:GetValueAtTime(0.5)) -- returns void, 1.5, void

end

testVector3Curve()

```

---

API Reference

Methods

GetValueAtTime

Capabilities: Basic

Vector3Curve:GetValueAtTime (time :[number](/docs/luau/numbers) ) :[{any}](/docs/luau/tables#arrays)

Parameters

|

time :[number](/docs/luau/numbers)

 |

Returns

[{any}](/docs/luau/tables#arrays)

Provide feedback

---

X

Capabilities: Basic

Vector3Curve:X () :[FloatCurve](/docs/reference/engine/classes/FloatCurve)

Returns

[FloatCurve](/docs/reference/engine/classes/FloatCurve)

Provide feedback

---

Y

Capabilities: Basic

Vector3Curve:Y () :[FloatCurve](/docs/reference/engine/classes/FloatCurve)

Returns

[FloatCurve](/docs/reference/engine/classes/FloatCurve)

Provide feedback

---

Z

Capabilities: Basic

Vector3Curve:Z () :[FloatCurve](/docs/reference/engine/classes/FloatCurve)

Returns

[FloatCurve](/docs/reference/engine/classes/FloatCurve)

Provide feedback

---

Jump to

▼

Vector3Curve

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[GetValueAtTime()](#GetValueAtTime)

[X()](#X)

[Y()](#Y)

[Z()](#Z)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
