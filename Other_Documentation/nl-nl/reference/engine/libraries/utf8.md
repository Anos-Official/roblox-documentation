<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/libraries/utf8 -->

utf8 | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Bibliotheken](/docs/nl-nl/reference/engine/libraries)
2. /
3. [utf8](/docs/nl-nl/reference/engine/libraries/utf8)

Nederlands

Feedback

Engine-bibliotheek

utf8

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/libraries/utf8)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Functies

|

[char](#char) (codepoints :  [Tuple](/docs/nl-nl/luau/tuples) <[number](/docs/nl-nl/luau/numbers) > ) :[string](/docs/nl-nl/luau/strings)

 |
| --- | --- |
|

[codes](#codes) (str :  [string](/docs/nl-nl/luau/strings) ) :[function](/docs/nl-nl/luau/functions) ,[string](/docs/nl-nl/luau/strings) ,[number](/docs/nl-nl/luau/numbers)

 |
|

[codepoint](#codepoint) (str :  [string](/docs/nl-nl/luau/strings) , i :  [number](/docs/nl-nl/luau/numbers) , j :  [number](/docs/nl-nl/luau/numbers) ) :[Tuple](/docs/nl-nl/luau/tuples) <[number](/docs/nl-nl/luau/numbers) >

 |
|

[len](#len) (s :  [string](/docs/nl-nl/luau/strings) , i :  [number](/docs/nl-nl/luau/numbers) , j :  [number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[offset](#offset) (s :  [string](/docs/nl-nl/luau/strings) , n :  [number](/docs/nl-nl/luau/numbers) , i :  [number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers) ?

 |
|

[graphemes](#graphemes) (str :  [string](/docs/nl-nl/luau/strings) , i :  [number](/docs/nl-nl/luau/numbers) , j :  [number](/docs/nl-nl/luau/numbers) ) :[function](/docs/nl-nl/luau/functions)

 |
|

[nfcnormalize](#nfcnormalize) (str :  [string](/docs/nl-nl/luau/strings) ) :[string](/docs/nl-nl/luau/strings)

 |
|

[nfdnormalize](#nfdnormalize) (str :  [string](/docs/nl-nl/luau/strings) ) :[string](/docs/nl-nl/luau/strings)

 |

Eigenschappen

|

[charpattern](#charpattern) :[string](/docs/nl-nl/luau/strings)

 |

---

API-referentie

Functies

char

utf8.char (codepoints :[Tuple](/docs/nl-nl/luau/tuples) <[number](/docs/nl-nl/luau/numbers) > ) :[string](/docs/nl-nl/luau/strings)

Parameters

|

codepoints :[Tuple](/docs/nl-nl/luau/tuples) <[number](/docs/nl-nl/luau/numbers) >

 |

Teruggaves

[string](/docs/nl-nl/luau/strings)

Codevoorbeelden

##### Utf8-teken

Feedback geven

---

codes

utf8.codes (str :[string](/docs/nl-nl/luau/strings) ) :[function](/docs/nl-nl/luau/functions) ,[string](/docs/nl-nl/luau/strings) ,[number](/docs/nl-nl/luau/numbers)

Parameters

|

str :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[function](/docs/nl-nl/luau/functions) , [string](/docs/nl-nl/luau/strings) , [number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

##### Utf8 Codes

Feedback geven

---

codepoint

utf8.codepoint (

str :[string](/docs/nl-nl/luau/strings) , i :[number](/docs/nl-nl/luau/numbers) , j :[number](/docs/nl-nl/luau/numbers)

) :[Tuple](/docs/nl-nl/luau/tuples) <[number](/docs/nl-nl/luau/numbers) >

Parameters

|

str :[string](/docs/nl-nl/luau/strings)

 |
|

i :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 1 |
|

j :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: i |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples) <[number](/docs/nl-nl/luau/numbers) >

Codevoorbeelden

##### Utf8 Codepoint

Feedback geven

---

len

utf8.len (

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

Standaardwaarde: -1 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

##### Utf8 Len

Feedback geven

---

offset

utf8.offset (

s :[string](/docs/nl-nl/luau/strings) , n :[number](/docs/nl-nl/luau/numbers) , i :[number](/docs/nl-nl/luau/numbers)

) :[number](/docs/nl-nl/luau/numbers) ?

Parameters

|

s :[string](/docs/nl-nl/luau/strings)

 |
|

n :[number](/docs/nl-nl/luau/numbers)

 |
|

i :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 1 |

Teruggaves

[number](/docs/nl-nl/luau/numbers) ?

Codevoorbeelden

##### Utf8 Offset

Feedback geven

---

graphemes

utf8.graphemes (

str :[string](/docs/nl-nl/luau/strings) , i :[number](/docs/nl-nl/luau/numbers) , j :[number](/docs/nl-nl/luau/numbers)

) :[function](/docs/nl-nl/luau/functions)

Parameters

|

str :[string](/docs/nl-nl/luau/strings)

 |
|

i :[number](/docs/nl-nl/luau/numbers)

 |
|

j :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[function](/docs/nl-nl/luau/functions)

Codevoorbeelden

Utf8 Graphemes

```

-- "e" gevolgd door een combinerende acute accent is één grapheem maar twee codepunten

local str = "ae\u{0301}b"

print(utf8.len(str)) --> 4

for first, last in utf8.graphemes(str) do

	local grapheme = string.sub(str, first, last)

	print(first, last, #grapheme)

end

--> 1 1 1

--> 2 4 3

--> 5 5 1

```

Feedback geven

---

nfcnormalize

utf8.nfcnormalize (str :[string](/docs/nl-nl/luau/strings) ) :[string](/docs/nl-nl/luau/strings)

Parameters

|

str :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[string](/docs/nl-nl/luau/strings)

Codevoorbeelden

Utf8 NFC Normaliseren

```

local decomposed = "e\u{0301}" -- "e" plus een gecombineerde acute accent

local composed = utf8.nfcnormalize(decomposed)

print(utf8.len(decomposed)) --> 2

print(utf8.len(composed)) --> 1

print(composed == "\u{00E9}") --> true

```

Feedback geven

---

nfdnormalize

utf8.nfdnormalize (str :[string](/docs/nl-nl/luau/strings) ) :[string](/docs/nl-nl/luau/strings)

Parameters

|

str :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[string](/docs/nl-nl/luau/strings)

Codevoorbeelden

Utf8 NFD Normaliseren

```

local composed = "\u{00E9}" -- voorgecomposeerd "é"

local decomposed = utf8.nfdnormalize(composed)

print(utf8.len(composed)) --> 1

print(utf8.len(decomposed)) --> 2

print(decomposed == "e\u{0301}") --> true

```

Feedback geven

---

Eigenschappen

charpattern

utf8.charpattern :[string](/docs/nl-nl/luau/strings)

Codevoorbeelden

##### Utf8 Charpattern

Feedback geven

---

Ga naar

▼

utf8

[Samenvatting](#summary)

[Functies](#summary-functions)

[Eigenschappen](#summary-properties)

[Functies](#functions)

[char()](#char)

[codes()](#codes)

[codepoint()](#codepoint)

[len()](#len)

[offset()](#offset)

[graphemes()](#graphemes)

[nfcnormalize()](#nfcnormalize)

[nfdnormalize()](#nfdnormalize)

[Eigenschappen](#properties)

[charpattern](#charpattern)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
