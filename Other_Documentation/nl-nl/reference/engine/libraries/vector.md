<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/libraries/vector -->

vector | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Bibliotheken](/docs/nl-nl/reference/engine/libraries)
2. /
3. [vector](/docs/nl-nl/reference/engine/libraries/vector)

Nederlands

Feedback

Engine-bibliotheek

vector

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/libraries/vector)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Functies

|

[create](#create) (x :  [number](/docs/nl-nl/luau/numbers) , y :  [number](/docs/nl-nl/luau/numbers) , z :  [number](/docs/nl-nl/luau/numbers) ) :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |
| --- | --- |
|

[magnitude](#magnitude) (vec :  [vector](/docs/nl-nl/reference/engine/libraries/vector) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[normalize](#normalize) (vec :  [vector](/docs/nl-nl/reference/engine/libraries/vector) ) :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |
|

[cross](#cross) (vec1 :  [vector](/docs/nl-nl/reference/engine/libraries/vector) , vec2 :  [vector](/docs/nl-nl/reference/engine/libraries/vector) ) :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |
|

[dot](#dot) (vec1 :  [vector](/docs/nl-nl/reference/engine/libraries/vector) , vec2 :  [vector](/docs/nl-nl/reference/engine/libraries/vector) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[angle](#angle) (vec1 :  [vector](/docs/nl-nl/reference/engine/libraries/vector) , vec2 :  [vector](/docs/nl-nl/reference/engine/libraries/vector) , axis :  [vector](/docs/nl-nl/reference/engine/libraries/vector) ? ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[floor](#floor) (vec :  [vector](/docs/nl-nl/reference/engine/libraries/vector) ) :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |
|

[ceil](#ceil) (vec :  [vector](/docs/nl-nl/reference/engine/libraries/vector) ) :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |
|

[abs](#abs) (vec :  [vector](/docs/nl-nl/reference/engine/libraries/vector) ) :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |
|

[sign](#sign) (vec :  [vector](/docs/nl-nl/reference/engine/libraries/vector) ) :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |
|

[clamp](#clamp) (vec :  [vector](/docs/nl-nl/reference/engine/libraries/vector) , min :  [vector](/docs/nl-nl/reference/engine/libraries/vector) , max :  [vector](/docs/nl-nl/reference/engine/libraries/vector) ) :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |
|

[lerp](#lerp) (vec1 :  [vector](/docs/nl-nl/reference/engine/libraries/vector) , vec2 :  [vector](/docs/nl-nl/reference/engine/libraries/vector) , alpha :  [number](/docs/nl-nl/luau/numbers) ) :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |
|

[max](#max) (... :  [vector](/docs/nl-nl/reference/engine/libraries/vector) ) :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |
|

[min](#min) (... :  [vector](/docs/nl-nl/reference/engine/libraries/vector) ) :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |

Eigenschappen

|

[zero](#zero) :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |
|

[one](#one) :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |

---

API-referentie

Functies

create

vector.create (

x :[number](/docs/nl-nl/luau/numbers) , y :[number](/docs/nl-nl/luau/numbers) , z :[number](/docs/nl-nl/luau/numbers)

) :[vector](/docs/nl-nl/reference/engine/libraries/vector)

Parameters

|

x :[number](/docs/nl-nl/luau/numbers)

 |
|

y :[number](/docs/nl-nl/luau/numbers)

 |
|

z :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[vector](/docs/nl-nl/reference/engine/libraries/vector)

Codevoorbeelden

##### Vector Aanmaken

Feedback geven

---

magnitude

vector.magnitude (vec :[vector](/docs/nl-nl/reference/engine/libraries/vector) ) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

vec :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

##### Vector Grootte

Feedback geven

---

normalize

vector.normalize (vec :[vector](/docs/nl-nl/reference/engine/libraries/vector) ) :[vector](/docs/nl-nl/reference/engine/libraries/vector)

Parameters

|

vec :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |

Teruggaves

[vector](/docs/nl-nl/reference/engine/libraries/vector)

Codevoorbeelden

##### Vector Normaliseren

Feedback geven

---

cross

vector.cross (

vec1 :[vector](/docs/nl-nl/reference/engine/libraries/vector) , vec2 :[vector](/docs/nl-nl/reference/engine/libraries/vector)

) :[vector](/docs/nl-nl/reference/engine/libraries/vector)

Parameters

|

vec1 :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |
|

vec2 :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |

Teruggaves

[vector](/docs/nl-nl/reference/engine/libraries/vector)

Codevoorbeelden

##### Vector Kruis

Feedback geven

---

dot

vector.dot (

vec1 :[vector](/docs/nl-nl/reference/engine/libraries/vector) , vec2 :[vector](/docs/nl-nl/reference/engine/libraries/vector)

) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

vec1 :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |
|

vec2 :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

##### Vector Dot

Feedback geven

---

angle

vector.angle (

vec1 :[vector](/docs/nl-nl/reference/engine/libraries/vector) , vec2 :[vector](/docs/nl-nl/reference/engine/libraries/vector) , axis :[vector](/docs/nl-nl/reference/engine/libraries/vector) ?

) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

vec1 :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |
|

vec2 :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |
|

axis :[vector](/docs/nl-nl/reference/engine/libraries/vector) ?

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

##### Vector Hoek

Feedback geven

---

floor

vector.floor (vec :[vector](/docs/nl-nl/reference/engine/libraries/vector) ) :[vector](/docs/nl-nl/reference/engine/libraries/vector)

Parameters

|

vec :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |

Teruggaves

[vector](/docs/nl-nl/reference/engine/libraries/vector)

Codevoorbeelden

##### Vector Vloer

Feedback geven

---

ceil

vector.ceil (vec :[vector](/docs/nl-nl/reference/engine/libraries/vector) ) :[vector](/docs/nl-nl/reference/engine/libraries/vector)

Parameters

|

vec :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |

Teruggaves

[vector](/docs/nl-nl/reference/engine/libraries/vector)

Codevoorbeelden

##### Vector Ceil

Feedback geven

---

abs

vector.abs (vec :[vector](/docs/nl-nl/reference/engine/libraries/vector) ) :[vector](/docs/nl-nl/reference/engine/libraries/vector)

Parameters

|

vec :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |

Teruggaves

[vector](/docs/nl-nl/reference/engine/libraries/vector)

Codevoorbeelden

##### Vector Absoluut

Feedback geven

---

sign

vector.sign (vec :[vector](/docs/nl-nl/reference/engine/libraries/vector) ) :[vector](/docs/nl-nl/reference/engine/libraries/vector)

Parameters

|

vec :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |

Teruggaves

[vector](/docs/nl-nl/reference/engine/libraries/vector)

Codevoorbeelden

##### Vectorteken

Feedback geven

---

clamp

vector.clamp (

vec :[vector](/docs/nl-nl/reference/engine/libraries/vector) , min :[vector](/docs/nl-nl/reference/engine/libraries/vector) , max :[vector](/docs/nl-nl/reference/engine/libraries/vector)

) :[vector](/docs/nl-nl/reference/engine/libraries/vector)

Parameters

|

vec :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |
|

min :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |
|

max :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |

Teruggaves

[vector](/docs/nl-nl/reference/engine/libraries/vector)

Codevoorbeelden

##### Vector Clamp

Feedback geven

---

lerp

vector.lerp (

vec1 :[vector](/docs/nl-nl/reference/engine/libraries/vector) , vec2 :[vector](/docs/nl-nl/reference/engine/libraries/vector) , alpha :[number](/docs/nl-nl/luau/numbers)

) :[vector](/docs/nl-nl/reference/engine/libraries/vector)

Parameters

|

vec1 :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |
|

vec2 :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |
|

alpha :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[vector](/docs/nl-nl/reference/engine/libraries/vector)

Codevoorbeelden

##### Vector Lerp

Feedback geven

---

max

vector.max (... :[vector](/docs/nl-nl/reference/engine/libraries/vector) ) :[vector](/docs/nl-nl/reference/engine/libraries/vector)

Parameters

|

... :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |

Teruggaves

[vector](/docs/nl-nl/reference/engine/libraries/vector)

Codevoorbeelden

##### Vector Max

Feedback geven

---

min

vector.min (... :[vector](/docs/nl-nl/reference/engine/libraries/vector) ) :[vector](/docs/nl-nl/reference/engine/libraries/vector)

Parameters

|

... :[vector](/docs/nl-nl/reference/engine/libraries/vector)

 |

Teruggaves

[vector](/docs/nl-nl/reference/engine/libraries/vector)

Codevoorbeelden

##### Vector Min

Feedback geven

---

Eigenschappen

zero

vector.zero :[vector](/docs/nl-nl/reference/engine/libraries/vector)

Codevoorbeelden

##### Vector Nul

Feedback geven

---

one

vector.one :[vector](/docs/nl-nl/reference/engine/libraries/vector)

Codevoorbeelden

##### Vector Een

Feedback geven

---

Ga naar

▼

vector

[Samenvatting](#summary)

[Functies](#summary-functions)

[Eigenschappen](#summary-properties)

[Functies](#functions)

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

[Eigenschappen](#properties)

[zero](#zero)

[one](#one)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
