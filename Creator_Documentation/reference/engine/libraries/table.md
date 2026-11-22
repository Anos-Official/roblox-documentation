<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/libraries/table -->

table | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/libraries/table.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Libraries](/docs/en-us/reference/engine/libraries)
2. /
3. [table](/docs/en-us/reference/engine/libraries/table)

English

Feedback

Engine Library

table

---

## Summary

Functions

|

[clear](#clear) (table :  [table](/docs/en-us/luau/tables) ) : ()

 |
| --- | --- |
|

[clone](#clone) (t :  [table](/docs/en-us/luau/tables) ) :[table](/docs/en-us/luau/tables)

 |
|

[concat](#concat) (t :  [{any}](/docs/en-us/luau/tables#arrays) , sep :  [string](/docs/en-us/luau/strings) , i :  [number](/docs/en-us/luau/numbers) , j :  [number](/docs/en-us/luau/numbers) ) :[string](/docs/en-us/luau/strings)

 |
|

[create](#create) (count :  [number](/docs/en-us/luau/numbers) , value :  Variant ) :[table](/docs/en-us/luau/tables)

 |
|

[find](#find) (haystack :  [table](/docs/en-us/luau/tables) , needle :  Variant , init :  [number](/docs/en-us/luau/numbers) ) : Variant

 |
|

[foreach](#foreach) (t :  [table](/docs/en-us/luau/tables) , f :  [function](/docs/en-us/luau/functions) ) : ()

Deprecated

 |
|

[foreachi](#foreachi) (t :  [{any}](/docs/en-us/luau/tables#arrays) , f :  [function](/docs/en-us/luau/functions) ) : ()

Deprecated

 |
|

[freeze](#freeze) (t :  [table](/docs/en-us/luau/tables) ) :[table](/docs/en-us/luau/tables)

 |
|

[getn](#getn) (t :  [{any}](/docs/en-us/luau/tables#arrays) ) :[number](/docs/en-us/luau/numbers)

Deprecated

 |
|

[insert](#insert) (t :  [{any}](/docs/en-us/luau/tables#arrays) , pos :  [number](/docs/en-us/luau/numbers) , value :  Variant ) : ()

 |
|

[insert](#insert-t-value) (t :  [{any}](/docs/en-us/luau/tables#arrays) , value :  Variant ) : ()

 |
|

[isfrozen](#isfrozen) (t :  [table](/docs/en-us/luau/tables) ) :[boolean](/docs/en-us/luau/booleans)

 |
|

[maxn](#maxn) (t :  [table](/docs/en-us/luau/tables) ) :[number](/docs/en-us/luau/numbers)

 |
|

[move](#move) (src :  [table](/docs/en-us/luau/tables) , a :  [number](/docs/en-us/luau/numbers) , b :  [number](/docs/en-us/luau/numbers) , t :  [number](/docs/en-us/luau/numbers) , dst :  [table](/docs/en-us/luau/tables) ) :[table](/docs/en-us/luau/tables)

 |
|

[pack](#pack) (values... :  Variant ) :[table](/docs/en-us/luau/tables)

 |
|

[remove](#remove) (t :  [{any}](/docs/en-us/luau/tables#arrays) , pos :  [number](/docs/en-us/luau/numbers) ) : Variant

 |
|

[sort](#sort) (t :  [{any}](/docs/en-us/luau/tables#arrays) , comp :  [function](/docs/en-us/luau/functions) ) : ()

 |
|

[unpack](#unpack) (list :  [table](/docs/en-us/luau/tables) , i :  [number](/docs/en-us/luau/numbers) , j :  [number](/docs/en-us/luau/numbers) ) :[Tuple](/docs/en-us/luau/tuples)

 |

---

API Reference

Functions

clear

table.clear (table :[table](/docs/en-us/luau/tables) ) : ()

Parameters

|

table :[table](/docs/en-us/luau/tables)

 |

Returns

()

Code Samples

##### Table Clear

Provide feedback

---

clone

table.clone (t :[table](/docs/en-us/luau/tables) ) :[table](/docs/en-us/luau/tables)

Parameters

|

t :[table](/docs/en-us/luau/tables)

 |

Returns

[table](/docs/en-us/luau/tables)

Code Samples

##### Table Clone

Provide feedback

---

concat

table.concat (

t :[{any}](/docs/en-us/luau/tables#arrays) , sep :[string](/docs/en-us/luau/strings) , i :[number](/docs/en-us/luau/numbers) , j :[number](/docs/en-us/luau/numbers)

) :[string](/docs/en-us/luau/strings)

Parameters

|

t :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

sep :[string](/docs/en-us/luau/strings)

 |
|

i :[number](/docs/en-us/luau/numbers)

Default Value: 1 |
|

j :[number](/docs/en-us/luau/numbers)

 |

Returns

[string](/docs/en-us/luau/strings)

Code Samples

##### Table Concat

Provide feedback

---

create

table.create (

count :[number](/docs/en-us/luau/numbers) , value : Variant

) :[table](/docs/en-us/luau/tables)

Parameters

|

count :[number](/docs/en-us/luau/numbers)

 |
|

value : Variant

 |

Returns

[table](/docs/en-us/luau/tables)

Code Samples

##### Table Create

Provide feedback

---

find

table.find (

haystack :[table](/docs/en-us/luau/tables) , needle : Variant , init :[number](/docs/en-us/luau/numbers)

) : Variant

Parameters

|

haystack :[table](/docs/en-us/luau/tables)

 |
|

needle : Variant

 |
|

init :[number](/docs/en-us/luau/numbers)

 |

Returns

Variant

Code Samples

##### Table Find

Provide feedback

---

foreach

Deprecated

Show details

---

foreachi

Deprecated

Show details

---

freeze

table.freeze (t :[table](/docs/en-us/luau/tables) ) :[table](/docs/en-us/luau/tables)

Parameters

|

t :[table](/docs/en-us/luau/tables)

 |

Returns

[table](/docs/en-us/luau/tables)

Code Samples

##### Table Freeze

Provide feedback

---

getn

Deprecated

Show details

---

insert

table.insert (

t :[{any}](/docs/en-us/luau/tables#arrays) , pos :[number](/docs/en-us/luau/numbers) , value : Variant

) : ()

Parameters

|

t :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

pos :[number](/docs/en-us/luau/numbers)

 |
|

value : Variant

 |

Returns

()

Code Samples

##### Table Insert At Position

Provide feedback

---

insert

table.insert (

t :[{any}](/docs/en-us/luau/tables#arrays) , value : Variant

) : ()

Parameters

|

t :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

value : Variant

 |

Returns

()

Code Samples

##### Table Insert Append

Provide feedback

---

isfrozen

table.isfrozen (t :[table](/docs/en-us/luau/tables) ) :[boolean](/docs/en-us/luau/booleans)

Parameters

|

t :[table](/docs/en-us/luau/tables)

 |

Returns

[boolean](/docs/en-us/luau/booleans)

Code Samples

##### Table Isfrozen

Provide feedback

---

maxn

table.maxn (t :[table](/docs/en-us/luau/tables) ) :[number](/docs/en-us/luau/numbers)

Parameters

|

t :[table](/docs/en-us/luau/tables)

 |

Returns

[number](/docs/en-us/luau/numbers)

Code Samples

##### Table Maxn

Provide feedback

---

move

table.move (

src :[table](/docs/en-us/luau/tables) , a :[number](/docs/en-us/luau/numbers) , b :[number](/docs/en-us/luau/numbers) , t :[number](/docs/en-us/luau/numbers) , dst :[table](/docs/en-us/luau/tables)

) :[table](/docs/en-us/luau/tables)

Parameters

|

src :[table](/docs/en-us/luau/tables)

 |
|

a :[number](/docs/en-us/luau/numbers)

 |
|

b :[number](/docs/en-us/luau/numbers)

 |
|

t :[number](/docs/en-us/luau/numbers)

 |
|

dst :[table](/docs/en-us/luau/tables)

Default Value: src |

Returns

[table](/docs/en-us/luau/tables)

Code Samples

##### Table Move

Provide feedback

---

pack

table.pack (values... : Variant ) :[table](/docs/en-us/luau/tables)

Parameters

|

values... : Variant

 |

Returns

[table](/docs/en-us/luau/tables)

Code Samples

##### Table Pack

Provide feedback

---

remove

table.remove (

t :[{any}](/docs/en-us/luau/tables#arrays) , pos :[number](/docs/en-us/luau/numbers)

) : Variant

Parameters

|

t :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

pos :[number](/docs/en-us/luau/numbers)

 |

Returns

Variant

Code Samples

##### Table Remove

Provide feedback

---

sort

table.sort (

t :[{any}](/docs/en-us/luau/tables#arrays) , comp :[function](/docs/en-us/luau/functions)

) : ()

Parameters

|

t :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

comp :[function](/docs/en-us/luau/functions)

Default Value: nil |

Returns

()

Code Samples

##### Table Sort

Provide feedback

---

unpack

table.unpack (

list :[table](/docs/en-us/luau/tables) , i :[number](/docs/en-us/luau/numbers) , j :[number](/docs/en-us/luau/numbers)

) :[Tuple](/docs/en-us/luau/tuples)

Parameters

|

list :[table](/docs/en-us/luau/tables)

 |
|

i :[number](/docs/en-us/luau/numbers)

Default Value: 1 |
|

j :[number](/docs/en-us/luau/numbers)

Default Value: #list |

Returns

[Tuple](/docs/en-us/luau/tuples)

Code Samples

##### Table Unpack

Provide feedback

---

Jump to

▼

table

[Summary](#summary)

[Functions](#summary-functions)

[Functions](#functions)

[clear()](#clear)

[clone()](#clone)

[concat()](#concat)

[create()](#create)

[find()](#find)

[foreach()](#foreach)

[foreachi()](#foreachi)

[freeze()](#freeze)

[getn()](#getn)

[insert()](#insert)

[isfrozen()](#isfrozen)

[maxn()](#maxn)

[move()](#move)

[pack()](#pack)

[remove()](#remove)

[sort()](#sort)

[unpack()](#unpack)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
