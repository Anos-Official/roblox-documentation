<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/datatypes/Vector2 -->

Vector2 | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/datatypes/Vector2.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Data types](/docs/en-us/reference/engine/datatypes)
2. /
3. [Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

English

Feedback

Engine Data Type

Vector2

---

## Summary

Constructors

|

[new](#new) (x :  [number](/docs/en-us/luau/numbers) , y :  [number](/docs/en-us/luau/numbers) )

 |
| --- | --- |

Properties

|

[X](#X) :[number](/docs/en-us/luau/numbers)

 |
|

[Y](#Y) :[number](/docs/en-us/luau/numbers)

 |
|

[Magnitude](#Magnitude) :[number](/docs/en-us/luau/numbers)

 |
|

[Unit](#Unit) :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |

Methods

|

[Cross](#Cross) (other :  [Vector2](/docs/en-us/reference/engine/datatypes/Vector2) ) :[number](/docs/en-us/luau/numbers)

 |
|

[Abs](#Abs) () :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
|

[Ceil](#Ceil) () :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
|

[Floor](#Floor) () :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
|

[Sign](#Sign) () :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
|

[Angle](#Angle) (other :  [Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , isSigned :  [boolean](/docs/en-us/luau/booleans) ) :[number](/docs/en-us/luau/numbers)

 |
|

[Dot](#Dot) (v :  [Vector2](/docs/en-us/reference/engine/datatypes/Vector2) ) :[number](/docs/en-us/luau/numbers)

 |
|

[Lerp](#Lerp) (v :  [Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , alpha :  [number](/docs/en-us/luau/numbers) ) :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
|

[Max](#Max) (others... :  [Tuple](/docs/en-us/luau/tuples) ) :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
|

[Min](#Min) (others... :  [Tuple](/docs/en-us/luau/tuples) ) :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
|

[FuzzyEq](#FuzzyEq) (other :  [Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , epsilon :  [number](/docs/en-us/luau/numbers) ) :[boolean](/docs/en-us/luau/booleans)

 |

Math Operations

|

[`Vector2  +  Vector2`](#Vector2-+-Vector2)

 |
|

[`Vector2  -  Vector2`](#Vector2---Vector2)

 |
|

[`Vector2  *  Vector2`](#Vector2-*-Vector2)

 |
|

[`Vector2  /  Vector2`](#Vector2-_-Vector2)

 |
|

[`Vector2  *  number`](#Vector2-*-number)

 |
|

[`Vector2  /  number`](#Vector2-_-number)

 |

---

API Reference

Constructors

new

Vector2.new (

x :[number](/docs/en-us/luau/numbers) , y :[number](/docs/en-us/luau/numbers) )

Parameters

|

x :[number](/docs/en-us/luau/numbers)

 |
|

y :[number](/docs/en-us/luau/numbers)

 |

Provide feedback

---

Properties

X

Vector2.X :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Y

Vector2.Y :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Magnitude

Vector2.Magnitude :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Unit

Vector2.Unit :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Provide feedback

---

Methods

Cross

Vector2:Cross (other :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2) ) :[number](/docs/en-us/luau/numbers)

Parameters

|

other :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |

Returns

[number](/docs/en-us/luau/numbers)

Provide feedback

---

Abs

Vector2:Abs () :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Returns

[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Provide feedback

---

Ceil

Vector2:Ceil () :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Returns

[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Provide feedback

---

Floor

Vector2:Floor () :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Returns

[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Provide feedback

---

Sign

Vector2:Sign () :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Returns

[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Provide feedback

---

Angle

Vector2:Angle (

other :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , isSigned :[boolean](/docs/en-us/luau/booleans)

) :[number](/docs/en-us/luau/numbers)

Parameters

|

other :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
|

isSigned :[boolean](/docs/en-us/luau/booleans)

Default Value: false |

Returns

[number](/docs/en-us/luau/numbers)

Provide feedback

---

Dot

Vector2:Dot (v :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2) ) :[number](/docs/en-us/luau/numbers)

Parameters

|

v :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |

Returns

[number](/docs/en-us/luau/numbers)

Provide feedback

---

Lerp

Vector2:Lerp (

v :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , alpha :[number](/docs/en-us/luau/numbers)

) :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Parameters

|

v :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
|

alpha :[number](/docs/en-us/luau/numbers)

 |

Returns

[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Provide feedback

---

Max

Vector2:Max (others... :[Tuple](/docs/en-us/luau/tuples) ) :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Parameters

|

others... :[Tuple](/docs/en-us/luau/tuples)

 |

Returns

[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Provide feedback

---

Min

Vector2:Min (others... :[Tuple](/docs/en-us/luau/tuples) ) :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Parameters

|

others... :[Tuple](/docs/en-us/luau/tuples)

 |

Returns

[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Provide feedback

---

FuzzyEq

Vector2:FuzzyEq (

other :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2) , epsilon :[number](/docs/en-us/luau/numbers)

) :[boolean](/docs/en-us/luau/booleans)

Parameters

|

other :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
|

epsilon :[number](/docs/en-us/luau/numbers)

Default Value: 0.00001 (1e-5) |

Returns

[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

Math Operations

`Vector2` +  `Vector2`

[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)  +  [Vector2](/docs/en-us/reference/engine/datatypes/Vector2)  : [Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Provide feedback

---

`Vector2` -  `Vector2`

[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)  -  [Vector2](/docs/en-us/reference/engine/datatypes/Vector2)  : [Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Provide feedback

---

`Vector2` *  `Vector2`

[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)  *  [Vector2](/docs/en-us/reference/engine/datatypes/Vector2)  : [Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Provide feedback

---

`Vector2` /  `Vector2`

[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)  /  [Vector2](/docs/en-us/reference/engine/datatypes/Vector2)  : [Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Provide feedback

---

`Vector2` *  `number`

[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)  *  [number](/docs/en-us/luau/numbers)  : [Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Provide feedback

---

`Vector2` /  `number`

[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)  /  [number](/docs/en-us/luau/numbers)  : [Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Provide feedback

---

Jump to

▼

Vector2

[Summary](#summary)

[Constructors](#summary-constructors)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Math Operations](#summary-math-operations)

[Constructors](#constructors)

[new()](#new)

[Properties](#properties)

[X](#X)

[Y](#Y)

[Magnitude](#Magnitude)

[Unit](#Unit)

[Methods](#methods)

[Cross()](#Cross)

[Abs()](#Abs)

[Ceil()](#Ceil)

[Floor()](#Floor)

[Sign()](#Sign)

[Angle()](#Angle)

[Dot()](#Dot)

[Lerp()](#Lerp)

[Max()](#Max)

[Min()](#Min)

[FuzzyEq()](#FuzzyEq)

[Math Operations](#math-operations)

[Vector2 + Vector2](#Vector2+Vector2)

[Vector2 - Vector2](#Vector2-Vector2)

[Vector2 * Vector2](#Vector2*Vector2)

[Vector2 / Vector2](#Vector2_Vector2)

[Vector2 * number](#Vector2*number)

[Vector2 / number](#Vector2_number)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
