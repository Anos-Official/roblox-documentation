<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/libraries/vector -->

vector | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/libraries/vector.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Libraries](/docs/en-us/reference/engine/libraries)
2. /
3. [vector](/docs/en-us/reference/engine/libraries/vector)

English

Feedback

Engine Library

vector

---

## Summary

Functions

|

[create](#create) (x :  [number](/docs/en-us/luau/numbers) , y :  [number](/docs/en-us/luau/numbers) , z :  [number](/docs/en-us/luau/numbers) ) :[vector](/docs/en-us/reference/engine/libraries/vector)

 |
| --- | --- |
|

[magnitude](#magnitude) (vec :  [vector](/docs/en-us/reference/engine/libraries/vector) ) :[number](/docs/en-us/luau/numbers)

 |
|

[normalize](#normalize) (vec :  [vector](/docs/en-us/reference/engine/libraries/vector) ) :[vector](/docs/en-us/reference/engine/libraries/vector)

 |
|

[cross](#cross) (vec1 :  [vector](/docs/en-us/reference/engine/libraries/vector) , vec2 :  [vector](/docs/en-us/reference/engine/libraries/vector) ) :[vector](/docs/en-us/reference/engine/libraries/vector)

 |
|

[dot](#dot) (vec1 :  [vector](/docs/en-us/reference/engine/libraries/vector) , vec2 :  [vector](/docs/en-us/reference/engine/libraries/vector) ) :[number](/docs/en-us/luau/numbers)

 |
|

[angle](#angle) (vec1 :  [vector](/docs/en-us/reference/engine/libraries/vector) , vec2 :  [vector](/docs/en-us/reference/engine/libraries/vector) , axis :  [vector](/docs/en-us/reference/engine/libraries/vector) ? ) :[number](/docs/en-us/luau/numbers)

 |
|

[floor](#floor) (vec :  [vector](/docs/en-us/reference/engine/libraries/vector) ) :[vector](/docs/en-us/reference/engine/libraries/vector)

 |
|

[ceil](#ceil) (vec :  [vector](/docs/en-us/reference/engine/libraries/vector) ) :[vector](/docs/en-us/reference/engine/libraries/vector)

 |
|

[abs](#abs) (vec :  [vector](/docs/en-us/reference/engine/libraries/vector) ) :[vector](/docs/en-us/reference/engine/libraries/vector)

 |
|

[sign](#sign) (vec :  [vector](/docs/en-us/reference/engine/libraries/vector) ) :[vector](/docs/en-us/reference/engine/libraries/vector)

 |
|

[clamp](#clamp) (vec :  [vector](/docs/en-us/reference/engine/libraries/vector) , min :  [vector](/docs/en-us/reference/engine/libraries/vector) , max :  [vector](/docs/en-us/reference/engine/libraries/vector) ) :[vector](/docs/en-us/reference/engine/libraries/vector)

 |
|

[lerp](#lerp) (vec1 :  [vector](/docs/en-us/reference/engine/libraries/vector) , vec2 :  [vector](/docs/en-us/reference/engine/libraries/vector) , alpha :  [number](/docs/en-us/luau/numbers) ) :[vector](/docs/en-us/reference/engine/libraries/vector)

 |
|

[max](#max) (... :  [vector](/docs/en-us/reference/engine/libraries/vector) ) :[vector](/docs/en-us/reference/engine/libraries/vector)

 |
|

[min](#min) (... :  [vector](/docs/en-us/reference/engine/libraries/vector) ) :[vector](/docs/en-us/reference/engine/libraries/vector)

 |

Properties

|

[zero](#zero) :[vector](/docs/en-us/reference/engine/libraries/vector)

 |
|

[one](#one) :[vector](/docs/en-us/reference/engine/libraries/vector)

 |

---

API Reference

Functions

create

vector.create (

x :[number](/docs/en-us/luau/numbers) , y :[number](/docs/en-us/luau/numbers) , z :[number](/docs/en-us/luau/numbers)

) :[vector](/docs/en-us/reference/engine/libraries/vector)

Parameters

|

x :[number](/docs/en-us/luau/numbers)

 |
|

y :[number](/docs/en-us/luau/numbers)

 |
|

z :[number](/docs/en-us/luau/numbers)

 |

Returns

[vector](/docs/en-us/reference/engine/libraries/vector)

Code Samples

##### Vector Create

Provide feedback

---

magnitude

vector.magnitude (vec :[vector](/docs/en-us/reference/engine/libraries/vector) ) :[number](/docs/en-us/luau/numbers)

Parameters

|

vec :[vector](/docs/en-us/reference/engine/libraries/vector)

 |

Returns

[number](/docs/en-us/luau/numbers)

Code Samples

##### Vector Magnitude

Provide feedback

---

normalize

vector.normalize (vec :[vector](/docs/en-us/reference/engine/libraries/vector) ) :[vector](/docs/en-us/reference/engine/libraries/vector)

Parameters

|

vec :[vector](/docs/en-us/reference/engine/libraries/vector)

 |

Returns

[vector](/docs/en-us/reference/engine/libraries/vector)

Code Samples

##### Vector Normalize

Provide feedback

---

cross

vector.cross (

vec1 :[vector](/docs/en-us/reference/engine/libraries/vector) , vec2 :[vector](/docs/en-us/reference/engine/libraries/vector)

) :[vector](/docs/en-us/reference/engine/libraries/vector)

Parameters

|

vec1 :[vector](/docs/en-us/reference/engine/libraries/vector)

 |
|

vec2 :[vector](/docs/en-us/reference/engine/libraries/vector)

 |

Returns

[vector](/docs/en-us/reference/engine/libraries/vector)

Code Samples

##### Vector Cross

Provide feedback

---

dot

vector.dot (

vec1 :[vector](/docs/en-us/reference/engine/libraries/vector) , vec2 :[vector](/docs/en-us/reference/engine/libraries/vector)

) :[number](/docs/en-us/luau/numbers)

Parameters

|

vec1 :[vector](/docs/en-us/reference/engine/libraries/vector)

 |
|

vec2 :[vector](/docs/en-us/reference/engine/libraries/vector)

 |

Returns

[number](/docs/en-us/luau/numbers)

Code Samples

##### Vector Dot

Provide feedback

---

angle

vector.angle (

vec1 :[vector](/docs/en-us/reference/engine/libraries/vector) , vec2 :[vector](/docs/en-us/reference/engine/libraries/vector) , axis :[vector](/docs/en-us/reference/engine/libraries/vector) ?

) :[number](/docs/en-us/luau/numbers)

Parameters

|

vec1 :[vector](/docs/en-us/reference/engine/libraries/vector)

 |
|

vec2 :[vector](/docs/en-us/reference/engine/libraries/vector)

 |
|

axis :[vector](/docs/en-us/reference/engine/libraries/vector) ?

 |

Returns

[number](/docs/en-us/luau/numbers)

Code Samples

##### Vector Angle

Provide feedback

---

floor

vector.floor (vec :[vector](/docs/en-us/reference/engine/libraries/vector) ) :[vector](/docs/en-us/reference/engine/libraries/vector)

Parameters

|

vec :[vector](/docs/en-us/reference/engine/libraries/vector)

 |

Returns

[vector](/docs/en-us/reference/engine/libraries/vector)

Code Samples

##### Vector Floor

Provide feedback

---

ceil

vector.ceil (vec :[vector](/docs/en-us/reference/engine/libraries/vector) ) :[vector](/docs/en-us/reference/engine/libraries/vector)

Parameters

|

vec :[vector](/docs/en-us/reference/engine/libraries/vector)

 |

Returns

[vector](/docs/en-us/reference/engine/libraries/vector)

Code Samples

##### Vector Ceil

Provide feedback

---

abs

vector.abs (vec :[vector](/docs/en-us/reference/engine/libraries/vector) ) :[vector](/docs/en-us/reference/engine/libraries/vector)

Parameters

|

vec :[vector](/docs/en-us/reference/engine/libraries/vector)

 |

Returns

[vector](/docs/en-us/reference/engine/libraries/vector)

Code Samples

##### Vector Abs

Provide feedback

---

sign

vector.sign (vec :[vector](/docs/en-us/reference/engine/libraries/vector) ) :[vector](/docs/en-us/reference/engine/libraries/vector)

Parameters

|

vec :[vector](/docs/en-us/reference/engine/libraries/vector)

 |

Returns

[vector](/docs/en-us/reference/engine/libraries/vector)

Code Samples

##### Vector Sign

Provide feedback

---

clamp

vector.clamp (

vec :[vector](/docs/en-us/reference/engine/libraries/vector) , min :[vector](/docs/en-us/reference/engine/libraries/vector) , max :[vector](/docs/en-us/reference/engine/libraries/vector)

) :[vector](/docs/en-us/reference/engine/libraries/vector)

Parameters

|

vec :[vector](/docs/en-us/reference/engine/libraries/vector)

 |
|

min :[vector](/docs/en-us/reference/engine/libraries/vector)

 |
|

max :[vector](/docs/en-us/reference/engine/libraries/vector)

 |

Returns

[vector](/docs/en-us/reference/engine/libraries/vector)

Code Samples

##### Vector Clamp

Provide feedback

---

lerp

vector.lerp (

vec1 :[vector](/docs/en-us/reference/engine/libraries/vector) , vec2 :[vector](/docs/en-us/reference/engine/libraries/vector) , alpha :[number](/docs/en-us/luau/numbers)

) :[vector](/docs/en-us/reference/engine/libraries/vector)

Parameters

|

vec1 :[vector](/docs/en-us/reference/engine/libraries/vector)

 |
|

vec2 :[vector](/docs/en-us/reference/engine/libraries/vector)

 |
|

alpha :[number](/docs/en-us/luau/numbers)

 |

Returns

[vector](/docs/en-us/reference/engine/libraries/vector)

Code Samples

##### Vector Lerp

Provide feedback

---

max

vector.max (... :[vector](/docs/en-us/reference/engine/libraries/vector) ) :[vector](/docs/en-us/reference/engine/libraries/vector)

Parameters

|

... :[vector](/docs/en-us/reference/engine/libraries/vector)

 |

Returns

[vector](/docs/en-us/reference/engine/libraries/vector)

Code Samples

##### Vector Max

Provide feedback

---

min

vector.min (... :[vector](/docs/en-us/reference/engine/libraries/vector) ) :[vector](/docs/en-us/reference/engine/libraries/vector)

Parameters

|

... :[vector](/docs/en-us/reference/engine/libraries/vector)

 |

Returns

[vector](/docs/en-us/reference/engine/libraries/vector)

Code Samples

##### Vector Min

Provide feedback

---

Properties

zero

vector.zero :[vector](/docs/en-us/reference/engine/libraries/vector)

Code Samples

##### Vector Zero

Provide feedback

---

one

vector.one :[vector](/docs/en-us/reference/engine/libraries/vector)

Code Samples

##### Vector One

Provide feedback

---

Jump to

▼

vector

[Summary](#summary)

[Functions](#summary-functions)

[Properties](#summary-properties)

[Functions](#functions)

[create()](#create)

[magnitude()](#magnitude)

[normalize()](#normalize)

[cross()](#cross)

[dot()](#dot)

[angle()](#angle)

[floor()](#floor)

[ceil()](#ceil)

[abs()](#abs)

[sign()](#sign)

[clamp()](#clamp)

[lerp()](#lerp)

[max()](#max)

[min()](#min)

[Properties](#properties)

[zero](#zero)

[one](#one)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
