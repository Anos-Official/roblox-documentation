<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/datatypes/Vector3 -->

Vector3 | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Gegevenstypen](/docs/nl-nl/reference/engine/datatypes)
2. /
3. [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Nederlands

Feedback

Engine-gegevenstype

Vector3

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/datatypes/Vector3)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Constructors

|

[new](#new) (x :  [number](/docs/nl-nl/luau/numbers) , y :  [number](/docs/nl-nl/luau/numbers) , z :  [number](/docs/nl-nl/luau/numbers) )

 |
| --- | --- |
|

[FromNormalId](#FromNormalId) (normal :  [Enum.NormalId](/docs/nl-nl/reference/engine/enums/NormalId) )

 |
|

[FromAxis](#FromAxis) (axis :  [Enum.Axis](/docs/nl-nl/reference/engine/enums/Axis) )

 |

Eigenschappen

|

[zero](#zero) :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |
|

[one](#one) :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |
|

[xAxis](#xAxis) :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |
|

[yAxis](#yAxis) :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |
|

[zAxis](#zAxis) :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |
|

[X](#X) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Y](#Y) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Z](#Z) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Magnitude](#Magnitude) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Unit](#Unit) :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |

Methoden

|

[Abs](#Abs) () :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |
|

[Ceil](#Ceil) () :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |
|

[Floor](#Floor) () :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |
|

[Sign](#Sign) () :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |
|

[Cross](#Cross) (other :  [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) ) :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |
|

[Angle](#Angle) (other :  [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) , axis :  [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Dot](#Dot) (other :  [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[FuzzyEq](#FuzzyEq) (other :  [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) , epsilon :  [number](/docs/nl-nl/luau/numbers) ) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[Lerp](#Lerp) (goal :  [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) , alpha :  [number](/docs/nl-nl/luau/numbers) ) :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |
|

[Max](#Max) (vector :  [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) ) :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |
|

[Min](#Min) (vector :  [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) ) :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |

Rekenkundige bewerkingen

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

API-referentie

Constructors

new

Vector3.new (

x :[number](/docs/nl-nl/luau/numbers) , y :[number](/docs/nl-nl/luau/numbers) , z :[number](/docs/nl-nl/luau/numbers) )

Parameters

|

x :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0 |
|

y :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0 |
|

z :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0 |

Feedback geven

---

FromNormalId

Vector3.FromNormalId (normal :[Enum.NormalId](/docs/nl-nl/reference/engine/enums/NormalId) )

Parameters

|

normal :[Enum.NormalId](/docs/nl-nl/reference/engine/enums/NormalId)

 |

Feedback geven

---

FromAxis

Vector3.FromAxis (axis :[Enum.Axis](/docs/nl-nl/reference/engine/enums/Axis) )

Parameters

|

axis :[Enum.Axis](/docs/nl-nl/reference/engine/enums/Axis)

 |

Feedback geven

---

Eigenschappen

zero

Vector3.zero :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

one

Vector3.one :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

xAxis

Vector3.xAxis :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

yAxis

Vector3.yAxis :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

zAxis

Vector3.zAxis :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

X

Vector3.X :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Y

Vector3.Y :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Z

Vector3.Z :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Magnitude

Vector3.Magnitude :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Unit

Vector3.Unit :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

Methoden

Abs

Vector3:Abs () :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Teruggaves

[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

Ceil

Vector3:Ceil () :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Teruggaves

[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

Floor

Vector3:Floor () :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Teruggaves

[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

Sign

Vector3:Sign () :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Teruggaves

[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

Cross

Vector3:Cross (other :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) ) :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Parameters

|

other :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |

Teruggaves

[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

Angle

Vector3:Angle (

other :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) , axis :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

other :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |
|

axis :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Standaardwaarde: nil |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Dot

Vector3:Dot (other :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) ) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

other :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

FuzzyEq

Vector3:FuzzyEq (

other :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) , epsilon :[number](/docs/nl-nl/luau/numbers)

) :[boolean](/docs/nl-nl/luau/booleans)

Parameters

|

other :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |
|

epsilon :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0.00001 aka 1e-5 |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Lerp

Vector3:Lerp (

goal :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) , alpha :[number](/docs/nl-nl/luau/numbers)

) :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Parameters

|

goal :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |
|

alpha :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

Max

Vector3:Max (vector :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) ) :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Parameters

|

vector :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |

Teruggaves

[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

Min

Vector3:Min (vector :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) ) :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Parameters

|

vector :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |

Teruggaves

[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

Rekenkundige bewerkingen

`Vector3` +  `Vector3`

[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  +  [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  : [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

`Vector3` -  `Vector3`

[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  -  [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  : [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

`Vector3` *  `Vector3`

[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  *  [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  : [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

`Vector3` /  `Vector3`

[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  /  [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  : [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

`Vector3` //  `Vector3`

[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  //  [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  : [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

`Vector3` *  `number`

[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  *  [number](/docs/nl-nl/luau/numbers)  : [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

`Vector3` /  `number`

[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  /  [number](/docs/nl-nl/luau/numbers)  : [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

`Vector3` //  `number`

[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  //  [number](/docs/nl-nl/luau/numbers)  : [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

Ga naar

▼

Vector3

[Samenvatting](#summary)

[Constructors](#summary-constructors)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Rekenkundige bewerkingen](#summary-math-operations)

[Constructors](#constructors)

[new()](#new)

[FromNormalId()](#FromNormalId)

[FromAxis()](#FromAxis)

[Eigenschappen](#properties)

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

[Methoden](#methods)

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

[Rekenkundige bewerkingen](#math-operations)

[Vector3 + Vector3](#Vector3+Vector3)

[Vector3 - Vector3](#Vector3-Vector3)

[Vector3 * Vector3](#Vector3*Vector3)

[Vector3 / Vector3](#Vector3_Vector3)

[Vector3 // Vector3](#Vector3__Vector3)

[Vector3 * number](#Vector3*number)

[Vector3 / number](#Vector3_number)

[Vector3 // number](#Vector3__number)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
