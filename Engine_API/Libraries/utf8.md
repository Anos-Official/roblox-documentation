<!-- Source: https://create.roblox.com/docs/reference/engine/libraries/utf8 -->

utf8 | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/libraries/utf8.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Libraries](/docs/reference/engine/libraries)
2. /
3. [utf8](/docs/reference/engine/libraries/utf8)

English

Feedback

Engine Library

utf8

---

## Summary

Functions

|

[char](#char) (codepoints :  [Tuple](/docs/luau/tuples) <[number](/docs/luau/numbers) > ) :[string](/docs/luau/strings)

 |
| --- | --- |
|

[codes](#codes) (str :  [string](/docs/luau/strings) ) :[function](/docs/luau/functions) ,[string](/docs/luau/strings) ,[number](/docs/luau/numbers)

 |
|

[codepoint](#codepoint) (str :  [string](/docs/luau/strings) , i :  [number](/docs/luau/numbers) , j :  [number](/docs/luau/numbers) ) :[Tuple](/docs/luau/tuples) <[number](/docs/luau/numbers) >

 |
|

[len](#len) (s :  [string](/docs/luau/strings) , i :  [number](/docs/luau/numbers) , j :  [number](/docs/luau/numbers) ) :[number](/docs/luau/numbers)

 |
|

[offset](#offset) (s :  [string](/docs/luau/strings) , n :  [number](/docs/luau/numbers) , i :  [number](/docs/luau/numbers) ) :[number](/docs/luau/numbers) ?

 |
|

[graphemes](#graphemes) (str :  [string](/docs/luau/strings) , i :  [number](/docs/luau/numbers) , j :  [number](/docs/luau/numbers) ) :[function](/docs/luau/functions)

 |
|

[nfcnormalize](#nfcnormalize) (str :  [string](/docs/luau/strings) ) :[string](/docs/luau/strings)

 |
|

[nfdnormalize](#nfdnormalize) (str :  [string](/docs/luau/strings) ) :[string](/docs/luau/strings)

 |

Properties

|

[charpattern](#charpattern) :[string](/docs/luau/strings)

 |

---

API Reference

Functions

char

utf8.char (codepoints :[Tuple](/docs/luau/tuples) <[number](/docs/luau/numbers) > ) :[string](/docs/luau/strings)

Parameters

|

codepoints :[Tuple](/docs/luau/tuples) <[number](/docs/luau/numbers) >

 |

Returns

[string](/docs/luau/strings)

Code Samples

##### Utf8 Char

Provide feedback

---

codes

utf8.codes (str :[string](/docs/luau/strings) ) :[function](/docs/luau/functions) ,[string](/docs/luau/strings) ,[number](/docs/luau/numbers)

Parameters

|

str :[string](/docs/luau/strings)

 |

Returns

[function](/docs/luau/functions) , [string](/docs/luau/strings) , [number](/docs/luau/numbers)

Code Samples

##### Utf8 Codes

Provide feedback

---

codepoint

utf8.codepoint (

str :[string](/docs/luau/strings) , i :[number](/docs/luau/numbers) , j :[number](/docs/luau/numbers)

) :[Tuple](/docs/luau/tuples) <[number](/docs/luau/numbers) >

Parameters

|

str :[string](/docs/luau/strings)

 |
|

i :[number](/docs/luau/numbers)

Default Value: 1 |
|

j :[number](/docs/luau/numbers)

Default Value: i |

Returns

[Tuple](/docs/luau/tuples) <[number](/docs/luau/numbers) >

Code Samples

##### Utf8 Codepoint

Provide feedback

---

len

utf8.len (

s :[string](/docs/luau/strings) , i :[number](/docs/luau/numbers) , j :[number](/docs/luau/numbers)

) :[number](/docs/luau/numbers)

Parameters

|

s :[string](/docs/luau/strings)

 |
|

i :[number](/docs/luau/numbers)

Default Value: 1 |
|

j :[number](/docs/luau/numbers)

Default Value: -1 |

Returns

[number](/docs/luau/numbers)

Code Samples

##### Utf8 Len

Provide feedback

---

offset

utf8.offset (

s :[string](/docs/luau/strings) , n :[number](/docs/luau/numbers) , i :[number](/docs/luau/numbers)

) :[number](/docs/luau/numbers) ?

Parameters

|

s :[string](/docs/luau/strings)

 |
|

n :[number](/docs/luau/numbers)

 |
|

i :[number](/docs/luau/numbers)

Default Value: 1 |

Returns

[number](/docs/luau/numbers) ?

Code Samples

##### Utf8 Offset

Provide feedback

---

graphemes

utf8.graphemes (

str :[string](/docs/luau/strings) , i :[number](/docs/luau/numbers) , j :[number](/docs/luau/numbers)

) :[function](/docs/luau/functions)

Parameters

|

str :[string](/docs/luau/strings)

 |
|

i :[number](/docs/luau/numbers)

 |
|

j :[number](/docs/luau/numbers)

 |

Returns

[function](/docs/luau/functions)

Code Samples

Utf8 Graphemes

```

-- "e" followed by a combining acute accent is one grapheme but two codepoints

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

Provide feedback

---

nfcnormalize

utf8.nfcnormalize (str :[string](/docs/luau/strings) ) :[string](/docs/luau/strings)

Parameters

|

str :[string](/docs/luau/strings)

 |

Returns

[string](/docs/luau/strings)

Code Samples

Utf8 NFC Normalize

```

local decomposed = "e\u{0301}" -- "e" plus a combining acute accent

local composed = utf8.nfcnormalize(decomposed)

print(utf8.len(decomposed)) --> 2

print(utf8.len(composed)) --> 1

print(composed == "\u{00E9}") --> true

```

Provide feedback

---

nfdnormalize

utf8.nfdnormalize (str :[string](/docs/luau/strings) ) :[string](/docs/luau/strings)

Parameters

|

str :[string](/docs/luau/strings)

 |

Returns

[string](/docs/luau/strings)

Code Samples

Utf8 NFD Normalize

```

local composed = "\u{00E9}" -- precomposed "é"

local decomposed = utf8.nfdnormalize(composed)

print(utf8.len(composed)) --> 1

print(utf8.len(decomposed)) --> 2

print(decomposed == "e\u{0301}") --> true

```

Provide feedback

---

Properties

charpattern

utf8.charpattern :[string](/docs/luau/strings)

Code Samples

##### Utf8 Charpattern

Provide feedback

---

Jump to

▼

utf8

[Summary](#summary)

[Functions](#summary-functions)

[Properties](#summary-properties)

[Functions](#functions)

[char()](#char)

[codes()](#codes)

[codepoint()](#codepoint)

[len()](#len)

[offset()](#offset)

[graphemes()](#graphemes)

[nfcnormalize()](#nfcnormalize)

[nfdnormalize()](#nfdnormalize)

[Properties](#properties)

[charpattern](#charpattern)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
