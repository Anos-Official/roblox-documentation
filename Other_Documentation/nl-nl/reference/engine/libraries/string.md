<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/libraries/string -->

string | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Bibliotheken](/docs/nl-nl/reference/engine/libraries)
2. /
3. [string](/docs/nl-nl/reference/engine/libraries/string)

Nederlands

Feedback

Engine-bibliotheek

string

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/libraries/string)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Functies

|

[byte](#byte) (s :  [string](/docs/nl-nl/luau/strings) , i :  [number](/docs/nl-nl/luau/numbers) , j :  [number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers)

 |
| --- | --- |
|

[char](#char) (... :  [number](/docs/nl-nl/luau/numbers) ) :[string](/docs/nl-nl/luau/strings)

 |
|

[find](#find) (s :  [string](/docs/nl-nl/luau/strings) , pattern :  [string](/docs/nl-nl/luau/strings) , init :  [number](/docs/nl-nl/luau/numbers) , plain :  [boolean](/docs/nl-nl/luau/booleans) ) :[number](/docs/nl-nl/luau/numbers) ,[number](/docs/nl-nl/luau/numbers)

 |
|

[format](#format) (formatstring :  [string](/docs/nl-nl/luau/strings) , ... :  [string](/docs/nl-nl/luau/strings) ) :[string](/docs/nl-nl/luau/strings)

 |
|

[gmatch](#gmatch) (s :  [string](/docs/nl-nl/luau/strings) , pattern :  [string](/docs/nl-nl/luau/strings) ) :[function](/docs/nl-nl/luau/functions)

 |
|

[gsub](#gsub) (s :  [string](/docs/nl-nl/luau/strings) , pattern :  [string](/docs/nl-nl/luau/strings) , replacement :  Variant , n :  [number](/docs/nl-nl/luau/numbers) ) :[string](/docs/nl-nl/luau/strings) ,[number](/docs/nl-nl/luau/numbers)

 |
|

[len](#len) (s :  [string](/docs/nl-nl/luau/strings) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[lower](#lower) (s :  [string](/docs/nl-nl/luau/strings) ) :[string](/docs/nl-nl/luau/strings)

 |
|

[match](#match) (s :  [string](/docs/nl-nl/luau/strings) , pattern :  [string](/docs/nl-nl/luau/strings) , init :  [number](/docs/nl-nl/luau/numbers) ) :[string](/docs/nl-nl/luau/strings)

 |
|

[pack](#pack) (format :  [string](/docs/nl-nl/luau/strings) , ... :  Variant ) :[string](/docs/nl-nl/luau/strings)

 |
|

[packsize](#packsize) (format :  [string](/docs/nl-nl/luau/strings) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[rep](#rep) (s :  [string](/docs/nl-nl/luau/strings) , n :  [number](/docs/nl-nl/luau/numbers) ) :[string](/docs/nl-nl/luau/strings)

 |
|

[reverse](#reverse) (s :  [string](/docs/nl-nl/luau/strings) ) :[string](/docs/nl-nl/luau/strings)

 |
|

[split](#split) (s :  [string](/docs/nl-nl/luau/strings) , separator :  [string](/docs/nl-nl/luau/strings) ) :[table](/docs/nl-nl/luau/tables)

 |
|

[sub](#sub) (s :  [string](/docs/nl-nl/luau/strings) , i :  [number](/docs/nl-nl/luau/numbers) , j :  [number](/docs/nl-nl/luau/numbers) ) :[string](/docs/nl-nl/luau/strings)

 |
|

[unpack](#unpack) (format :  [string](/docs/nl-nl/luau/strings) , data :  [string](/docs/nl-nl/luau/strings) , readStart :  [number](/docs/nl-nl/luau/numbers) ) :[Tuple](/docs/nl-nl/luau/tuples)

 |
|

[upper](#upper) (s :  [string](/docs/nl-nl/luau/strings) ) :[string](/docs/nl-nl/luau/strings)

 |

---

API-referentie

Functies

byte

string.byte (

s :[string](/docs/nl-nl/luau/strings) , i :[number](/docs/nl-nl/luau/numbers) , j :[number](/docs/nl-nl/luau/numbers)

) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

s :[string](/docs/nl-nl/luau/strings)

 |
|

i :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 1 |
|

j :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: i |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

##### String Byte

Feedback geven

---

char

string.char (... :[number](/docs/nl-nl/luau/numbers) ) :[string](/docs/nl-nl/luau/strings)

Parameters

|

... :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[string](/docs/nl-nl/luau/strings)

Codevoorbeelden

##### String Char

Feedback geven

---

find

string.find (

s :[string](/docs/nl-nl/luau/strings) , pattern :[string](/docs/nl-nl/luau/strings) , init :[number](/docs/nl-nl/luau/numbers) , plain :[boolean](/docs/nl-nl/luau/booleans)

) :[number](/docs/nl-nl/luau/numbers) ,[number](/docs/nl-nl/luau/numbers)

Parameters

|

s :[string](/docs/nl-nl/luau/strings)

 |
|

pattern :[string](/docs/nl-nl/luau/strings)

 |
|

init :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 1 |
|

plain :[boolean](/docs/nl-nl/luau/booleans)

Standaardwaarde: false |

Teruggaves

[number](/docs/nl-nl/luau/numbers) , [number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

##### String Vinden

Feedback geven

---

format

string.format (

formatstring :[string](/docs/nl-nl/luau/strings) , ... :[string](/docs/nl-nl/luau/strings)

) :[string](/docs/nl-nl/luau/strings)

Parameters

|

formatstring :[string](/docs/nl-nl/luau/strings)

 |
|

... :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[string](/docs/nl-nl/luau/strings)

Codevoorbeelden

##### Stringformaat

Feedback geven

---

gmatch

string.gmatch (

s :[string](/docs/nl-nl/luau/strings) , pattern :[string](/docs/nl-nl/luau/strings)

) :[function](/docs/nl-nl/luau/functions)

Parameters

|

s :[string](/docs/nl-nl/luau/strings)

 |
|

pattern :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[function](/docs/nl-nl/luau/functions)

Codevoorbeelden

##### String Gmatch

Feedback geven

---

gsub

string.gsub (

s :[string](/docs/nl-nl/luau/strings) , pattern :[string](/docs/nl-nl/luau/strings) , replacement : Variant , n :[number](/docs/nl-nl/luau/numbers)

) :[string](/docs/nl-nl/luau/strings) ,[number](/docs/nl-nl/luau/numbers)

Parameters

|

s :[string](/docs/nl-nl/luau/strings)

 |
|

pattern :[string](/docs/nl-nl/luau/strings)

 |
|

replacement : Variant

 |
|

n :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[string](/docs/nl-nl/luau/strings) , [number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

##### String Gsub

Feedback geven

---

len

string.len (s :[string](/docs/nl-nl/luau/strings) ) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

s :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

##### String Len

Feedback geven

---

lower

string.lower (s :[string](/docs/nl-nl/luau/strings) ) :[string](/docs/nl-nl/luau/strings)

Parameters

|

s :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[string](/docs/nl-nl/luau/strings)

Codevoorbeelden

##### String Klein

Feedback geven

---

match

string.match (

s :[string](/docs/nl-nl/luau/strings) , pattern :[string](/docs/nl-nl/luau/strings) , init :[number](/docs/nl-nl/luau/numbers)

) :[string](/docs/nl-nl/luau/strings)

Parameters

|

s :[string](/docs/nl-nl/luau/strings)

 |
|

pattern :[string](/docs/nl-nl/luau/strings)

 |
|

init :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 1 |

Teruggaves

[string](/docs/nl-nl/luau/strings)

Codevoorbeelden

##### String Match

Feedback geven

---

pack

string.pack (

format :[string](/docs/nl-nl/luau/strings) , ... : Variant

) :[string](/docs/nl-nl/luau/strings)

Parameters

|

format :[string](/docs/nl-nl/luau/strings)

 |
|

... : Variant

 |

Teruggaves

[string](/docs/nl-nl/luau/strings)

Codevoorbeelden

##### String Pack

Feedback geven

---

packsize

string.packsize (format :[string](/docs/nl-nl/luau/strings) ) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

format :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

##### String Packgrootte

Feedback geven

---

rep

string.rep (

s :[string](/docs/nl-nl/luau/strings) , n :[number](/docs/nl-nl/luau/numbers)

) :[string](/docs/nl-nl/luau/strings)

Parameters

|

s :[string](/docs/nl-nl/luau/strings)

 |
|

n :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[string](/docs/nl-nl/luau/strings)

Codevoorbeelden

##### String Rep

Feedback geven

---

reverse

string.reverse (s :[string](/docs/nl-nl/luau/strings) ) :[string](/docs/nl-nl/luau/strings)

Parameters

|

s :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[string](/docs/nl-nl/luau/strings)

Codevoorbeelden

##### String Omkeren

Feedback geven

---

split

string.split (

s :[string](/docs/nl-nl/luau/strings) , separator :[string](/docs/nl-nl/luau/strings)

) :[table](/docs/nl-nl/luau/tables)

Parameters

|

s :[string](/docs/nl-nl/luau/strings)

 |
|

separator :[string](/docs/nl-nl/luau/strings)

Standaardwaarde: , |

Teruggaves

[table](/docs/nl-nl/luau/tables)

Codevoorbeelden

##### String Splits

Feedback geven

---

sub

string.sub (

s :[string](/docs/nl-nl/luau/strings) , i :[number](/docs/nl-nl/luau/numbers) , j :[number](/docs/nl-nl/luau/numbers)

) :[string](/docs/nl-nl/luau/strings)

Parameters

|

s :[string](/docs/nl-nl/luau/strings)

 |
|

i :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 1 |
|

j :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: -1 |

Teruggaves

[string](/docs/nl-nl/luau/strings)

Codevoorbeelden

##### String Sub

Feedback geven

---

unpack

string.unpack (

format :[string](/docs/nl-nl/luau/strings) , data :[string](/docs/nl-nl/luau/strings) , readStart :[number](/docs/nl-nl/luau/numbers)

) :[Tuple](/docs/nl-nl/luau/tuples)

Parameters

|

format :[string](/docs/nl-nl/luau/strings)

 |
|

data :[string](/docs/nl-nl/luau/strings)

 |
|

readStart :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 1 |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Codevoorbeelden

##### String Uitpakken

Feedback geven

---

upper

string.upper (s :[string](/docs/nl-nl/luau/strings) ) :[string](/docs/nl-nl/luau/strings)

Parameters

|

s :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[string](/docs/nl-nl/luau/strings)

Codevoorbeelden

##### String Hoofdletters

Feedback geven

---

Ga naar

▼

string

[Samenvatting](#summary)

[Functies](#summary-functions)

[Functies](#functions)

[byte()](#byte)

[char()](#char)

[find()](#find)

[format()](#format)

[gmatch()](#gmatch)

[gsub()](#gsub)

[len()](#len)

[lower()](#lower)

[match()](#match)

[pack()](#pack)

[packsize()](#packsize)

[rep()](#rep)

[reverse()](#reverse)

[split()](#split)

[sub()](#sub)

[unpack()](#unpack)

[upper()](#upper)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
