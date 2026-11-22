<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/libraries/bit32 -->

bit32 | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Bibliotheken](/docs/nl-nl/reference/engine/libraries)
2. /
3. [bit32](/docs/nl-nl/reference/engine/libraries/bit32)

Nederlands

Feedback

Engine-bibliotheek

bit32

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/libraries/bit32)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Functies

|

[arshift](#arshift) (x :  [number](/docs/nl-nl/luau/numbers) , disp :  [number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers)

 |
| --- | --- |
|

[band](#band) (numbers :  [Tuple](/docs/nl-nl/luau/tuples) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[bnot](#bnot) (x :  [number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[bor](#bor) (numbers :  [Tuple](/docs/nl-nl/luau/tuples) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[btest](#btest) (numbers :  [Tuple](/docs/nl-nl/luau/tuples) ) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[bxor](#bxor) (numbers :  [Tuple](/docs/nl-nl/luau/tuples) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[byteswap](#byteswap) (x :  [number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[countlz](#countlz) (n :  [number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[countrz](#countrz) (n :  [number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[extract](#extract) (n :  [number](/docs/nl-nl/luau/numbers) , field :  [number](/docs/nl-nl/luau/numbers) , width :  [number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[replace](#replace) (n :  [number](/docs/nl-nl/luau/numbers) , v :  [number](/docs/nl-nl/luau/numbers) , field :  [number](/docs/nl-nl/luau/numbers) , width :  [number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[lrotate](#lrotate) (x :  [number](/docs/nl-nl/luau/numbers) , disp :  [number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[lshift](#lshift) (x :  [number](/docs/nl-nl/luau/numbers) , disp :  [number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[rrotate](#rrotate) (x :  [number](/docs/nl-nl/luau/numbers) , disp :  [number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[rshift](#rshift) (x :  [number](/docs/nl-nl/luau/numbers) , disp :  [number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers)

 |

---

API-referentie

Functies

arshift

bit32.arshift (

x :[number](/docs/nl-nl/luau/numbers) , disp :[number](/docs/nl-nl/luau/numbers)

) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

x :[number](/docs/nl-nl/luau/numbers)

 |
|

disp :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

##### Bit32 Aritmetische Verschuiving

Feedback geven

---

band

bit32.band (numbers :[Tuple](/docs/nl-nl/luau/tuples) ) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

numbers :[Tuple](/docs/nl-nl/luau/tuples)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

##### Bit32 EN

Feedback geven

---

bnot

bit32.bnot (x :[number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

x :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

##### Bit32 NIET

Feedback geven

---

bor

bit32.bor (numbers :[Tuple](/docs/nl-nl/luau/tuples) ) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

numbers :[Tuple](/docs/nl-nl/luau/tuples)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

##### Bit32 OF

Feedback geven

---

btest

bit32.btest (numbers :[Tuple](/docs/nl-nl/luau/tuples) ) :[boolean](/docs/nl-nl/luau/booleans)

Parameters

|

numbers :[Tuple](/docs/nl-nl/luau/tuples)

 |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

##### Bit32 Test

Feedback geven

---

bxor

bit32.bxor (numbers :[Tuple](/docs/nl-nl/luau/tuples) ) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

numbers :[Tuple](/docs/nl-nl/luau/tuples)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

##### Bit32 XOR

Feedback geven

---

byteswap

bit32.byteswap (x :[number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

x :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

##### Bit32 Byte Swap

Feedback geven

---

countlz

bit32.countlz (n :[number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

n :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

##### Bit32 Aantal Voorafgaande Nullen

Feedback geven

---

countrz

bit32.countrz (n :[number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

n :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

##### Bit32 Aantal Achtereenvolgende Nullen

Feedback geven

---

extract

bit32.extract (

n :[number](/docs/nl-nl/luau/numbers) , field :[number](/docs/nl-nl/luau/numbers) , width :[number](/docs/nl-nl/luau/numbers)

) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

n :[number](/docs/nl-nl/luau/numbers)

 |
|

field :[number](/docs/nl-nl/luau/numbers)

 |
|

width :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 1 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

##### Bit32 Extract

Feedback geven

---

replace

bit32.replace (

n :[number](/docs/nl-nl/luau/numbers) , v :[number](/docs/nl-nl/luau/numbers) , field :[number](/docs/nl-nl/luau/numbers) , width :[number](/docs/nl-nl/luau/numbers)

) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

n :[number](/docs/nl-nl/luau/numbers)

 |
|

v :[number](/docs/nl-nl/luau/numbers)

 |
|

field :[number](/docs/nl-nl/luau/numbers)

 |
|

width :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 1 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

##### Bit32 Vervangen

Feedback geven

---

lrotate

bit32.lrotate (

x :[number](/docs/nl-nl/luau/numbers) , disp :[number](/docs/nl-nl/luau/numbers)

) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

x :[number](/docs/nl-nl/luau/numbers)

 |
|

disp :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

##### Bit32 Links Roteren

Feedback geven

---

lshift

bit32.lshift (

x :[number](/docs/nl-nl/luau/numbers) , disp :[number](/docs/nl-nl/luau/numbers)

) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

x :[number](/docs/nl-nl/luau/numbers)

 |
|

disp :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

##### Bit32 Links Verschuiven

Feedback geven

---

rrotate

bit32.rrotate (

x :[number](/docs/nl-nl/luau/numbers) , disp :[number](/docs/nl-nl/luau/numbers)

) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

x :[number](/docs/nl-nl/luau/numbers)

 |
|

disp :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

##### Bit32 Rechts Roteren

Feedback geven

---

rshift

bit32.rshift (

x :[number](/docs/nl-nl/luau/numbers) , disp :[number](/docs/nl-nl/luau/numbers)

) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

x :[number](/docs/nl-nl/luau/numbers)

 |
|

disp :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

##### Bit32 Rechts Verschuiven

Feedback geven

---

Ga naar

▼

bit32

[Samenvatting](#summary)

[Functies](#summary-functions)

[Functies](#functions)

[arshift()](#arshift)

[band()](#band)

[bnot()](#bnot)

[bor()](#bor)

[btest()](#btest)

[bxor()](#bxor)

[byteswap()](#byteswap)

[countlz()](#countlz)

[countrz()](#countrz)

[extract()](#extract)

[replace()](#replace)

[lrotate()](#lrotate)

[lshift()](#lshift)

[rrotate()](#rrotate)

[rshift()](#rshift)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
