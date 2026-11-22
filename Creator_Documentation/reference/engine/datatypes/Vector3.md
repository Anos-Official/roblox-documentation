<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/datatypes/Vector3 -->

Vector3 | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/datatypes/Vector3.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Data types](/docs/en-us/reference/engine/datatypes)
2. /
3. [Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

English

Feedback

Engine Data Type

Vector3

---

## Summary

Constructors

|

[new](#new) (x :  [number](/docs/en-us/luau/numbers) , y :  [number](/docs/en-us/luau/numbers) , z :  [number](/docs/en-us/luau/numbers) )

 |
| --- | --- |
|

[FromNormalId](#FromNormalId) (normal :  [Enum.NormalId](/docs/en-us/reference/engine/enums/NormalId) )

 |
|

[FromAxis](#FromAxis) (axis :  [Enum.Axis](/docs/en-us/reference/engine/enums/Axis) )

 |

Properties

|

[zero](#zero) :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

 |
|

[one](#one) :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

 |
|

[xAxis](#xAxis) :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

 |
|

[yAxis](#yAxis) :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

 |
|

[zAxis](#zAxis) :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

 |
|

[X](#X) :[number](/docs/en-us/luau/numbers)

 |
|

[Y](#Y) :[number](/docs/en-us/luau/numbers)

 |
|

[Z](#Z) :[number](/docs/en-us/luau/numbers)

 |
|

[Magnitude](#Magnitude) :[number](/docs/en-us/luau/numbers)

 |
|

[Unit](#Unit) :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

 |

Methods

|

[Abs](#Abs) () :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

 |
|

[Ceil](#Ceil) () :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

 |
|

[Floor](#Floor) () :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

 |
|

[Sign](#Sign) () :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

 |
|

[Cross](#Cross) (other :  [Vector3](/docs/en-us/reference/engine/datatypes/Vector3) ) :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

 |
|

[Angle](#Angle) (other :  [Vector3](/docs/en-us/reference/engine/datatypes/Vector3) , axis :  [Vector3](/docs/en-us/reference/engine/datatypes/Vector3) ) :[number](/docs/en-us/luau/numbers)

 |
|

[Dot](#Dot) (other :  [Vector3](/docs/en-us/reference/engine/datatypes/Vector3) ) :[number](/docs/en-us/luau/numbers)

 |
|

[FuzzyEq](#FuzzyEq) (other :  [Vector3](/docs/en-us/reference/engine/datatypes/Vector3) , epsilon :  [number](/docs/en-us/luau/numbers) ) :[boolean](/docs/en-us/luau/booleans)

 |
|

[Lerp](#Lerp) (goal :  [Vector3](/docs/en-us/reference/engine/datatypes/Vector3) , alpha :  [number](/docs/en-us/luau/numbers) ) :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

 |
|

[Max](#Max) (vector :  [Vector3](/docs/en-us/reference/engine/datatypes/Vector3) ) :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

 |
|

[Min](#Min) (vector :  [Vector3](/docs/en-us/reference/engine/datatypes/Vector3) ) :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

 |

Math Operations

|

[`Vector3  +  Vector3`](#Vector3-+-Vector3)

 |
|

[`Vector3  -  Vector3`](#Vector3---Vector3)

 |
|

[`Vector3  *  Vector3`](#Vector3-*-Vector3)

 |
|

[`Vector3  /  Vector3`](#Vector3-_-Vector3)

 |
|

[`Vector3  //  Vector3`](#Vector3-__-Vector3)

 |
|

[`Vector3  *  number`](#Vector3-*-number)

 |
|

[`Vector3  /  number`](#Vector3-_-number)

 |
|

[`Vector3  //  number`](#Vector3-__-number)

 |

---

API Reference

Constructors

new

Vector3.new (

x :[number](/docs/en-us/luau/numbers) , y :[number](/docs/en-us/luau/numbers) , z :[number](/docs/en-us/luau/numbers) )

Parameters

|

x :[number](/docs/en-us/luau/numbers)

Default Value: 0 |
|

y :[number](/docs/en-us/luau/numbers)

Default Value: 0 |
|

z :[number](/docs/en-us/luau/numbers)

Default Value: 0 |

Provide feedback

---

FromNormalId

Vector3.FromNormalId (normal :[Enum.NormalId](/docs/en-us/reference/engine/enums/NormalId) )

Parameters

|

normal :[Enum.NormalId](/docs/en-us/reference/engine/enums/NormalId)

 |

Provide feedback

---

FromAxis

Vector3.FromAxis (axis :[Enum.Axis](/docs/en-us/reference/engine/enums/Axis) )

Parameters

|

axis :[Enum.Axis](/docs/en-us/reference/engine/enums/Axis)

 |

Provide feedback

---

Properties

zero

Vector3.zero :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Provide feedback

---

one

Vector3.one :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Provide feedback

---

xAxis

Vector3.xAxis :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Provide feedback

---

yAxis

Vector3.yAxis :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Provide feedback

---

zAxis

Vector3.zAxis :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Provide feedback

---

X

Vector3.X :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Y

Vector3.Y :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Z

Vector3.Z :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Magnitude

Vector3.Magnitude :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Unit

Vector3.Unit :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Provide feedback

---

Methods

Abs

Vector3:Abs () :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Returns

[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Provide feedback

---

Ceil

Vector3:Ceil () :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Returns

[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Provide feedback

---

Floor

Vector3:Floor () :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Returns

[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Provide feedback

---

Sign

Vector3:Sign () :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Returns

[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Provide feedback

---

Cross

Vector3:Cross (other :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3) ) :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Parameters

|

other :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

 |

Returns

[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Provide feedback

---

Angle

Vector3:Angle (

other :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3) , axis :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

) :[number](/docs/en-us/luau/numbers)

Parameters

|

other :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

 |
|

axis :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Default Value: nil |

Returns

[number](/docs/en-us/luau/numbers)

Provide feedback

---

Dot

Vector3:Dot (other :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3) ) :[number](/docs/en-us/luau/numbers)

Parameters

|

other :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

 |

Returns

[number](/docs/en-us/luau/numbers)

Provide feedback

---

FuzzyEq

Vector3:FuzzyEq (

other :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3) , epsilon :[number](/docs/en-us/luau/numbers)

) :[boolean](/docs/en-us/luau/booleans)

Parameters

|

other :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

 |
|

epsilon :[number](/docs/en-us/luau/numbers)

Default Value: 0.00001 aka 1e-5 |

Returns

[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

Lerp

Vector3:Lerp (

goal :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3) , alpha :[number](/docs/en-us/luau/numbers)

) :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Parameters

|

goal :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

 |
|

alpha :[number](/docs/en-us/luau/numbers)

 |

Returns

[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Provide feedback

---

Max

Vector3:Max (vector :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3) ) :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Parameters

|

vector :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

 |

Returns

[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Provide feedback

---

Min

Vector3:Min (vector :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3) ) :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Parameters

|

vector :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

 |

Returns

[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Provide feedback

---

Math Operations

`Vector3` +  `Vector3`

[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)  +  [Vector3](/docs/en-us/reference/engine/datatypes/Vector3)  : [Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Provide feedback

---

`Vector3` -  `Vector3`

[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)  -  [Vector3](/docs/en-us/reference/engine/datatypes/Vector3)  : [Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Provide feedback

---

`Vector3` *  `Vector3`

[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)  *  [Vector3](/docs/en-us/reference/engine/datatypes/Vector3)  : [Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Provide feedback

---

`Vector3` /  `Vector3`

[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)  /  [Vector3](/docs/en-us/reference/engine/datatypes/Vector3)  : [Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Provide feedback

---

`Vector3` //  `Vector3`

[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)  //  [Vector3](/docs/en-us/reference/engine/datatypes/Vector3)  : [Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Provide feedback

---

`Vector3` *  `number`

[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)  *  [number](/docs/en-us/luau/numbers)  : [Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Provide feedback

---

`Vector3` /  `number`

[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)  /  [number](/docs/en-us/luau/numbers)  : [Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Provide feedback

---

`Vector3` //  `number`

[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)  //  [number](/docs/en-us/luau/numbers)  : [Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Provide feedback

---

Jump to

▼

Vector3

[Summary](#summary)

[Constructors](#summary-constructors)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Math Operations](#summary-math-operations)

[Constructors](#constructors)

[new()](#new)

[FromNormalId()](#FromNormalId)

[FromAxis()](#FromAxis)

[Properties](#properties)

[zero](#zero)

[one](#one)

[xAxis](#xAxis)

[yAxis](#yAxis)

[zAxis](#zAxis)

[X](#X)

[Y](#Y)

[Z](#Z)

[Magnitude](#Magnitude)

[Unit](#Unit)

[Methods](#methods)

[Abs()](#Abs)

[Ceil()](#Ceil)

[Floor()](#Floor)

[Sign()](#Sign)

[Cross()](#Cross)

[Angle()](#Angle)

[Dot()](#Dot)

[FuzzyEq()](#FuzzyEq)

[Lerp()](#Lerp)

[Max()](#Max)

[Min()](#Min)

[Math Operations](#math-operations)

[Vector3 + Vector3](#Vector3+Vector3)

[Vector3 - Vector3](#Vector3-Vector3)

[Vector3 * Vector3](#Vector3*Vector3)

[Vector3 / Vector3](#Vector3_Vector3)

[Vector3 // Vector3](#Vector3__Vector3)

[Vector3 * number](#Vector3*number)

[Vector3 / number](#Vector3_number)

[Vector3 // number](#Vector3__number)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
