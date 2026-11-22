<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/libraries/string -->

string | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/libraries/string.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Libraries](/docs/en-us/reference/engine/libraries)
2. /
3. [string](/docs/en-us/reference/engine/libraries/string)

English

Feedback

Engine Library

string

---

## Summary

Functions

|

[byte](#byte) (s :  [string](/docs/en-us/luau/strings) , i :  [number](/docs/en-us/luau/numbers) , j :  [number](/docs/en-us/luau/numbers) ) :[number](/docs/en-us/luau/numbers)

 |
| --- | --- |
|

[char](#char) (... :  [number](/docs/en-us/luau/numbers) ) :[string](/docs/en-us/luau/strings)

 |
|

[find](#find) (s :  [string](/docs/en-us/luau/strings) , pattern :  [string](/docs/en-us/luau/strings) , init :  [number](/docs/en-us/luau/numbers) , plain :  [boolean](/docs/en-us/luau/booleans) ) :[number](/docs/en-us/luau/numbers) ,[number](/docs/en-us/luau/numbers)

 |
|

[format](#format) (formatstring :  [string](/docs/en-us/luau/strings) , ... :  [string](/docs/en-us/luau/strings) ) :[string](/docs/en-us/luau/strings)

 |
|

[gmatch](#gmatch) (s :  [string](/docs/en-us/luau/strings) , pattern :  [string](/docs/en-us/luau/strings) ) :[function](/docs/en-us/luau/functions)

 |
|

[gsub](#gsub) (s :  [string](/docs/en-us/luau/strings) , pattern :  [string](/docs/en-us/luau/strings) , replacement :  Variant , n :  [number](/docs/en-us/luau/numbers) ) :[string](/docs/en-us/luau/strings) ,[number](/docs/en-us/luau/numbers)

 |
|

[len](#len) (s :  [string](/docs/en-us/luau/strings) ) :[number](/docs/en-us/luau/numbers)

 |
|

[lower](#lower) (s :  [string](/docs/en-us/luau/strings) ) :[string](/docs/en-us/luau/strings)

 |
|

[match](#match) (s :  [string](/docs/en-us/luau/strings) , pattern :  [string](/docs/en-us/luau/strings) , init :  [number](/docs/en-us/luau/numbers) ) :[string](/docs/en-us/luau/strings)

 |
|

[pack](#pack) (format :  [string](/docs/en-us/luau/strings) , ... :  Variant ) :[string](/docs/en-us/luau/strings)

 |
|

[packsize](#packsize) (format :  [string](/docs/en-us/luau/strings) ) :[number](/docs/en-us/luau/numbers)

 |
|

[rep](#rep) (s :  [string](/docs/en-us/luau/strings) , n :  [number](/docs/en-us/luau/numbers) ) :[string](/docs/en-us/luau/strings)

 |
|

[reverse](#reverse) (s :  [string](/docs/en-us/luau/strings) ) :[string](/docs/en-us/luau/strings)

 |
|

[split](#split) (s :  [string](/docs/en-us/luau/strings) , separator :  [string](/docs/en-us/luau/strings) ) :[table](/docs/en-us/luau/tables)

 |
|

[sub](#sub) (s :  [string](/docs/en-us/luau/strings) , i :  [number](/docs/en-us/luau/numbers) , j :  [number](/docs/en-us/luau/numbers) ) :[string](/docs/en-us/luau/strings)

 |
|

[unpack](#unpack) (format :  [string](/docs/en-us/luau/strings) , data :  [string](/docs/en-us/luau/strings) , readStart :  [number](/docs/en-us/luau/numbers) ) :[Tuple](/docs/en-us/luau/tuples)

 |
|

[upper](#upper) (s :  [string](/docs/en-us/luau/strings) ) :[string](/docs/en-us/luau/strings)

 |

---

API Reference

Functions

byte

string.byte (

s :[string](/docs/en-us/luau/strings) , i :[number](/docs/en-us/luau/numbers) , j :[number](/docs/en-us/luau/numbers)

) :[number](/docs/en-us/luau/numbers)

Parameters

|

s :[string](/docs/en-us/luau/strings)

 |
|

i :[number](/docs/en-us/luau/numbers)

Default Value: 1 |
|

j :[number](/docs/en-us/luau/numbers)

Default Value: i |

Returns

[number](/docs/en-us/luau/numbers)

Code Samples

##### String Byte

Provide feedback

---

char

string.char (... :[number](/docs/en-us/luau/numbers) ) :[string](/docs/en-us/luau/strings)

Parameters

|

... :[number](/docs/en-us/luau/numbers)

 |

Returns

[string](/docs/en-us/luau/strings)

Code Samples

##### String Char

Provide feedback

---

find

string.find (

s :[string](/docs/en-us/luau/strings) , pattern :[string](/docs/en-us/luau/strings) , init :[number](/docs/en-us/luau/numbers) , plain :[boolean](/docs/en-us/luau/booleans)

) :[number](/docs/en-us/luau/numbers) ,[number](/docs/en-us/luau/numbers)

Parameters

|

s :[string](/docs/en-us/luau/strings)

 |
|

pattern :[string](/docs/en-us/luau/strings)

 |
|

init :[number](/docs/en-us/luau/numbers)

Default Value: 1 |
|

plain :[boolean](/docs/en-us/luau/booleans)

Default Value: false |

Returns

[number](/docs/en-us/luau/numbers) , [number](/docs/en-us/luau/numbers)

Code Samples

##### String Find

Provide feedback

---

format

string.format (

formatstring :[string](/docs/en-us/luau/strings) , ... :[string](/docs/en-us/luau/strings)

) :[string](/docs/en-us/luau/strings)

Parameters

|

formatstring :[string](/docs/en-us/luau/strings)

 |
|

... :[string](/docs/en-us/luau/strings)

 |

Returns

[string](/docs/en-us/luau/strings)

Code Samples

##### String Format

Provide feedback

---

gmatch

string.gmatch (

s :[string](/docs/en-us/luau/strings) , pattern :[string](/docs/en-us/luau/strings)

) :[function](/docs/en-us/luau/functions)

Parameters

|

s :[string](/docs/en-us/luau/strings)

 |
|

pattern :[string](/docs/en-us/luau/strings)

 |

Returns

[function](/docs/en-us/luau/functions)

Code Samples

##### String Gmatch

Provide feedback

---

gsub

string.gsub (

s :[string](/docs/en-us/luau/strings) , pattern :[string](/docs/en-us/luau/strings) , replacement : Variant , n :[number](/docs/en-us/luau/numbers)

) :[string](/docs/en-us/luau/strings) ,[number](/docs/en-us/luau/numbers)

Parameters

|

s :[string](/docs/en-us/luau/strings)

 |
|

pattern :[string](/docs/en-us/luau/strings)

 |
|

replacement : Variant

 |
|

n :[number](/docs/en-us/luau/numbers)

 |

Returns

[string](/docs/en-us/luau/strings) , [number](/docs/en-us/luau/numbers)

Code Samples

##### String Gsub

Provide feedback

---

len

string.len (s :[string](/docs/en-us/luau/strings) ) :[number](/docs/en-us/luau/numbers)

Parameters

|

s :[string](/docs/en-us/luau/strings)

 |

Returns

[number](/docs/en-us/luau/numbers)

Code Samples

##### String Len

Provide feedback

---

lower

string.lower (s :[string](/docs/en-us/luau/strings) ) :[string](/docs/en-us/luau/strings)

Parameters

|

s :[string](/docs/en-us/luau/strings)

 |

Returns

[string](/docs/en-us/luau/strings)

Code Samples

##### String Lower

Provide feedback

---

match

string.match (

s :[string](/docs/en-us/luau/strings) , pattern :[string](/docs/en-us/luau/strings) , init :[number](/docs/en-us/luau/numbers)

) :[string](/docs/en-us/luau/strings)

Parameters

|

s :[string](/docs/en-us/luau/strings)

 |
|

pattern :[string](/docs/en-us/luau/strings)

 |
|

init :[number](/docs/en-us/luau/numbers)

Default Value: 1 |

Returns

[string](/docs/en-us/luau/strings)

Code Samples

##### String Match

Provide feedback

---

pack

string.pack (

format :[string](/docs/en-us/luau/strings) , ... : Variant

) :[string](/docs/en-us/luau/strings)

Parameters

|

format :[string](/docs/en-us/luau/strings)

 |
|

... : Variant

 |

Returns

[string](/docs/en-us/luau/strings)

Code Samples

##### String Pack

Provide feedback

---

packsize

string.packsize (format :[string](/docs/en-us/luau/strings) ) :[number](/docs/en-us/luau/numbers)

Parameters

|

format :[string](/docs/en-us/luau/strings)

 |

Returns

[number](/docs/en-us/luau/numbers)

Code Samples

##### String Packsize

Provide feedback

---

rep

string.rep (

s :[string](/docs/en-us/luau/strings) , n :[number](/docs/en-us/luau/numbers)

) :[string](/docs/en-us/luau/strings)

Parameters

|

s :[string](/docs/en-us/luau/strings)

 |
|

n :[number](/docs/en-us/luau/numbers)

 |

Returns

[string](/docs/en-us/luau/strings)

Code Samples

##### String Rep

Provide feedback

---

reverse

string.reverse (s :[string](/docs/en-us/luau/strings) ) :[string](/docs/en-us/luau/strings)

Parameters

|

s :[string](/docs/en-us/luau/strings)

 |

Returns

[string](/docs/en-us/luau/strings)

Code Samples

##### String Reverse

Provide feedback

---

split

string.split (

s :[string](/docs/en-us/luau/strings) , separator :[string](/docs/en-us/luau/strings)

) :[table](/docs/en-us/luau/tables)

Parameters

|

s :[string](/docs/en-us/luau/strings)

 |
|

separator :[string](/docs/en-us/luau/strings)

Default Value: , |

Returns

[table](/docs/en-us/luau/tables)

Code Samples

##### String Split

Provide feedback

---

sub

string.sub (

s :[string](/docs/en-us/luau/strings) , i :[number](/docs/en-us/luau/numbers) , j :[number](/docs/en-us/luau/numbers)

) :[string](/docs/en-us/luau/strings)

Parameters

|

s :[string](/docs/en-us/luau/strings)

 |
|

i :[number](/docs/en-us/luau/numbers)

Default Value: 1 |
|

j :[number](/docs/en-us/luau/numbers)

Default Value: -1 |

Returns

[string](/docs/en-us/luau/strings)

Code Samples

##### String Sub

Provide feedback

---

unpack

string.unpack (

format :[string](/docs/en-us/luau/strings) , data :[string](/docs/en-us/luau/strings) , readStart :[number](/docs/en-us/luau/numbers)

) :[Tuple](/docs/en-us/luau/tuples)

Parameters

|

format :[string](/docs/en-us/luau/strings)

 |
|

data :[string](/docs/en-us/luau/strings)

 |
|

readStart :[number](/docs/en-us/luau/numbers)

Default Value: 1 |

Returns

[Tuple](/docs/en-us/luau/tuples)

Code Samples

##### String Unpack

Provide feedback

---

upper

string.upper (s :[string](/docs/en-us/luau/strings) ) :[string](/docs/en-us/luau/strings)

Parameters

|

s :[string](/docs/en-us/luau/strings)

 |

Returns

[string](/docs/en-us/luau/strings)

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
