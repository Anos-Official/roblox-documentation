<!-- Source: https://create.roblox.com/docs/reference/engine/libraries/string -->

string | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/libraries/string.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Libraries](/docs/reference/engine/libraries)
2. /
3. [string](/docs/reference/engine/libraries/string)

English

Feedback

Engine Library

string

---

## Summary

Functions

|

[byte](#byte) (s :  [string](/docs/luau/strings) , i :  [number](/docs/luau/numbers) , j :  [number](/docs/luau/numbers) ) :[number](/docs/luau/numbers)

 |
| --- | --- |
|

[char](#char) (... :  [number](/docs/luau/numbers) ) :[string](/docs/luau/strings)

 |
|

[find](#find) (s :  [string](/docs/luau/strings) , pattern :  [string](/docs/luau/strings) , init :  [number](/docs/luau/numbers) , plain :  [boolean](/docs/luau/booleans) ) :[number](/docs/luau/numbers) ,[number](/docs/luau/numbers)

 |
|

[format](#format) (formatstring :  [string](/docs/luau/strings) , ... :  [string](/docs/luau/strings) ) :[string](/docs/luau/strings)

 |
|

[gmatch](#gmatch) (s :  [string](/docs/luau/strings) , pattern :  [string](/docs/luau/strings) ) :[function](/docs/luau/functions)

 |
|

[gsub](#gsub) (s :  [string](/docs/luau/strings) , pattern :  [string](/docs/luau/strings) , replacement :  Variant , n :  [number](/docs/luau/numbers) ) :[string](/docs/luau/strings) ,[number](/docs/luau/numbers)

 |
|

[len](#len) (s :  [string](/docs/luau/strings) ) :[number](/docs/luau/numbers)

 |
|

[lower](#lower) (s :  [string](/docs/luau/strings) ) :[string](/docs/luau/strings)

 |
|

[match](#match) (s :  [string](/docs/luau/strings) , pattern :  [string](/docs/luau/strings) , init :  [number](/docs/luau/numbers) ) :[string](/docs/luau/strings)

 |
|

[pack](#pack) (format :  [string](/docs/luau/strings) , ... :  Variant ) :[string](/docs/luau/strings)

 |
|

[packsize](#packsize) (format :  [string](/docs/luau/strings) ) :[number](/docs/luau/numbers)

 |
|

[rep](#rep) (s :  [string](/docs/luau/strings) , n :  [number](/docs/luau/numbers) ) :[string](/docs/luau/strings)

 |
|

[reverse](#reverse) (s :  [string](/docs/luau/strings) ) :[string](/docs/luau/strings)

 |
|

[split](#split) (s :  [string](/docs/luau/strings) , separator :  [string](/docs/luau/strings) ) :[table](/docs/luau/tables)

 |
|

[sub](#sub) (s :  [string](/docs/luau/strings) , i :  [number](/docs/luau/numbers) , j :  [number](/docs/luau/numbers) ) :[string](/docs/luau/strings)

 |
|

[unpack](#unpack) (format :  [string](/docs/luau/strings) , data :  [string](/docs/luau/strings) , readStart :  [number](/docs/luau/numbers) ) :[Tuple](/docs/luau/tuples)

 |
|

[upper](#upper) (s :  [string](/docs/luau/strings) ) :[string](/docs/luau/strings)

 |

---

API Reference

Functions

byte

string.byte (

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

Default Value: i |

Returns

[number](/docs/luau/numbers)

Code Samples

##### String Byte

Provide feedback

---

char

string.char (... :[number](/docs/luau/numbers) ) :[string](/docs/luau/strings)

Parameters

|

... :[number](/docs/luau/numbers)

 |

Returns

[string](/docs/luau/strings)

Code Samples

##### String Char

Provide feedback

---

find

string.find (

s :[string](/docs/luau/strings) , pattern :[string](/docs/luau/strings) , init :[number](/docs/luau/numbers) , plain :[boolean](/docs/luau/booleans)

) :[number](/docs/luau/numbers) ,[number](/docs/luau/numbers)

Parameters

|

s :[string](/docs/luau/strings)

 |
|

pattern :[string](/docs/luau/strings)

 |
|

init :[number](/docs/luau/numbers)

Default Value: 1 |
|

plain :[boolean](/docs/luau/booleans)

Default Value: false |

Returns

[number](/docs/luau/numbers) , [number](/docs/luau/numbers)

Code Samples

##### String Find

Provide feedback

---

format

string.format (

formatstring :[string](/docs/luau/strings) , ... :[string](/docs/luau/strings)

) :[string](/docs/luau/strings)

Parameters

|

formatstring :[string](/docs/luau/strings)

 |
|

... :[string](/docs/luau/strings)

 |

Returns

[string](/docs/luau/strings)

Code Samples

##### String Format

Provide feedback

---

gmatch

string.gmatch (

s :[string](/docs/luau/strings) , pattern :[string](/docs/luau/strings)

) :[function](/docs/luau/functions)

Parameters

|

s :[string](/docs/luau/strings)

 |
|

pattern :[string](/docs/luau/strings)

 |

Returns

[function](/docs/luau/functions)

Code Samples

##### String Gmatch

Provide feedback

---

gsub

string.gsub (

s :[string](/docs/luau/strings) , pattern :[string](/docs/luau/strings) , replacement : Variant , n :[number](/docs/luau/numbers)

) :[string](/docs/luau/strings) ,[number](/docs/luau/numbers)

Parameters

|

s :[string](/docs/luau/strings)

 |
|

pattern :[string](/docs/luau/strings)

 |
|

replacement : Variant

 |
|

n :[number](/docs/luau/numbers)

 |

Returns

[string](/docs/luau/strings) , [number](/docs/luau/numbers)

Code Samples

##### String Gsub

Provide feedback

---

len

string.len (s :[string](/docs/luau/strings) ) :[number](/docs/luau/numbers)

Parameters

|

s :[string](/docs/luau/strings)

 |

Returns

[number](/docs/luau/numbers)

Code Samples

##### String Len

Provide feedback

---

lower

string.lower (s :[string](/docs/luau/strings) ) :[string](/docs/luau/strings)

Parameters

|

s :[string](/docs/luau/strings)

 |

Returns

[string](/docs/luau/strings)

Code Samples

##### String Lower

Provide feedback

---

match

string.match (

s :[string](/docs/luau/strings) , pattern :[string](/docs/luau/strings) , init :[number](/docs/luau/numbers)

) :[string](/docs/luau/strings)

Parameters

|

s :[string](/docs/luau/strings)

 |
|

pattern :[string](/docs/luau/strings)

 |
|

init :[number](/docs/luau/numbers)

Default Value: 1 |

Returns

[string](/docs/luau/strings)

Code Samples

##### String Match

Provide feedback

---

pack

string.pack (

format :[string](/docs/luau/strings) , ... : Variant

) :[string](/docs/luau/strings)

Parameters

|

format :[string](/docs/luau/strings)

 |
|

... : Variant

 |

Returns

[string](/docs/luau/strings)

Code Samples

##### String Pack

Provide feedback

---

packsize

string.packsize (format :[string](/docs/luau/strings) ) :[number](/docs/luau/numbers)

Parameters

|

format :[string](/docs/luau/strings)

 |

Returns

[number](/docs/luau/numbers)

Code Samples

##### String Packsize

Provide feedback

---

rep

string.rep (

s :[string](/docs/luau/strings) , n :[number](/docs/luau/numbers)

) :[string](/docs/luau/strings)

Parameters

|

s :[string](/docs/luau/strings)

 |
|

n :[number](/docs/luau/numbers)

 |

Returns

[string](/docs/luau/strings)

Code Samples

##### String Rep

Provide feedback

---

reverse

string.reverse (s :[string](/docs/luau/strings) ) :[string](/docs/luau/strings)

Parameters

|

s :[string](/docs/luau/strings)

 |

Returns

[string](/docs/luau/strings)

Code Samples

##### String Reverse

Provide feedback

---

split

string.split (

s :[string](/docs/luau/strings) , separator :[string](/docs/luau/strings)

) :[table](/docs/luau/tables)

Parameters

|

s :[string](/docs/luau/strings)

 |
|

separator :[string](/docs/luau/strings)

Default Value: , |

Returns

[table](/docs/luau/tables)

Code Samples

##### String Split

Provide feedback

---

sub

string.sub (

s :[string](/docs/luau/strings) , i :[number](/docs/luau/numbers) , j :[number](/docs/luau/numbers)

) :[string](/docs/luau/strings)

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

[string](/docs/luau/strings)

Code Samples

##### String Sub

Provide feedback

---

unpack

string.unpack (

format :[string](/docs/luau/strings) , data :[string](/docs/luau/strings) , readStart :[number](/docs/luau/numbers)

) :[Tuple](/docs/luau/tuples)

Parameters

|

format :[string](/docs/luau/strings)

 |
|

data :[string](/docs/luau/strings)

 |
|

readStart :[number](/docs/luau/numbers)

Default Value: 1 |

Returns

[Tuple](/docs/luau/tuples)

Code Samples

##### String Unpack

Provide feedback

---

upper

string.upper (s :[string](/docs/luau/strings) ) :[string](/docs/luau/strings)

Parameters

|

s :[string](/docs/luau/strings)

 |

Returns

[string](/docs/luau/strings)

Code Samples

##### String Upper

Provide feedback

---

Jump to

▼

string

[Summary](#summary)

[Functions](#summary-functions)

[Functions](#functions)

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

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
