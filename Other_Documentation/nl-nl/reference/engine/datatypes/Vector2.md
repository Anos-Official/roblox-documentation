<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/datatypes/Vector2 -->

Vector2 | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Gegevenstypen](/docs/nl-nl/reference/engine/datatypes)
2. /
3. [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Nederlands

Feedback

Engine-gegevenstype

Vector2

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/datatypes/Vector2)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Constructors

|

[new](#new) (x :  [number](/docs/nl-nl/luau/numbers) , y :  [number](/docs/nl-nl/luau/numbers) )

 |
| --- | --- |

Eigenschappen

|

[X](#X) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Y](#Y) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Magnitude](#Magnitude) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Unit](#Unit) :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |

Methoden

|

[Cross](#Cross) (other :  [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Abs](#Abs) () :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

[Ceil](#Ceil) () :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

[Floor](#Floor) () :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

[Sign](#Sign) () :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

[Angle](#Angle) (other :  [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , isSigned :  [boolean](/docs/nl-nl/luau/booleans) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Dot](#Dot) (v :  [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Lerp](#Lerp) (v :  [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , alpha :  [number](/docs/nl-nl/luau/numbers) ) :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

[Max](#Max) (others... :  [Tuple](/docs/nl-nl/luau/tuples) ) :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

[Min](#Min) (others... :  [Tuple](/docs/nl-nl/luau/tuples) ) :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

[FuzzyEq](#FuzzyEq) (other :  [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , epsilon :  [number](/docs/nl-nl/luau/numbers) ) :[boolean](/docs/nl-nl/luau/booleans)

 |

Rekenkundige bewerkingen

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

API-referentie

Constructors

new

Vector2.new (

x :[number](/docs/nl-nl/luau/numbers) , y :[number](/docs/nl-nl/luau/numbers) )

Parameters

|

x :[number](/docs/nl-nl/luau/numbers)

 |
|

y :[number](/docs/nl-nl/luau/numbers)

 |

Feedback geven

---

Eigenschappen

X

Vector2.X :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Y

Vector2.Y :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Magnitude

Vector2.Magnitude :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Unit

Vector2.Unit :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Feedback geven

---

Methoden

Cross

Vector2:Cross (other :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) ) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

other :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Abs

Vector2:Abs () :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Teruggaves

[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Feedback geven

---

Ceil

Vector2:Ceil () :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Teruggaves

[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Feedback geven

---

Floor

Vector2:Floor () :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Teruggaves

[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Feedback geven

---

Sign

Vector2:Sign () :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Teruggaves

[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Feedback geven

---

Angle

Vector2:Angle (

other :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , isSigned :[boolean](/docs/nl-nl/luau/booleans)

) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

other :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

isSigned :[boolean](/docs/nl-nl/luau/booleans)

Standaardwaarde: false |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Dot

Vector2:Dot (v :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) ) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

v :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Lerp

Vector2:Lerp (

v :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , alpha :[number](/docs/nl-nl/luau/numbers)

) :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Parameters

|

v :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

alpha :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Feedback geven

---

Max

Vector2:Max (others... :[Tuple](/docs/nl-nl/luau/tuples) ) :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Parameters

|

others... :[Tuple](/docs/nl-nl/luau/tuples)

 |

Teruggaves

[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Feedback geven

---

Min

Vector2:Min (others... :[Tuple](/docs/nl-nl/luau/tuples) ) :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Parameters

|

others... :[Tuple](/docs/nl-nl/luau/tuples)

 |

Teruggaves

[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Feedback geven

---

FuzzyEq

Vector2:FuzzyEq (

other :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , epsilon :[number](/docs/nl-nl/luau/numbers)

) :[boolean](/docs/nl-nl/luau/booleans)

Parameters

|

other :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

epsilon :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0.00001 (1e-5) |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Rekenkundige bewerkingen

`Vector2` +  `Vector2`

[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)  +  [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)  : [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Feedback geven

---

`Vector2` -  `Vector2`

[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)  -  [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)  : [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Feedback geven

---

`Vector2` *  `Vector2`

[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)  *  [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)  : [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Feedback geven

---

`Vector2` /  `Vector2`

[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)  /  [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)  : [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Feedback geven

---

`Vector2` *  `number`

[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)  *  [number](/docs/nl-nl/luau/numbers)  : [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Feedback geven

---

`Vector2` /  `number`

[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)  /  [number](/docs/nl-nl/luau/numbers)  : [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Feedback geven

---

Ga naar

▼

Vector2

[Samenvatting](#summary)

[Constructors](#summary-constructors)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Rekenkundige bewerkingen](#summary-math-operations)

[Constructors](#constructors)

[new()](#new)

[Eigenschappen](#properties)

[X](#X)

[Y](#Y)

[Magnitude](#Magnitude)

[Unit](#Unit)

[Methoden](#methods)

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

[Rekenkundige bewerkingen](#math-operations)

[Vector2 + Vector2](#Vector2+Vector2)

[Vector2 - Vector2](#Vector2-Vector2)

[Vector2 * Vector2](#Vector2*Vector2)

[Vector2 / Vector2](#Vector2_Vector2)

[Vector2 * number](#Vector2*number)

[Vector2 / number](#Vector2_number)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
