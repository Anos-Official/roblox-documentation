<!-- Source: https://create.roblox.com/docs/reference/engine/libraries/table -->

table | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/libraries/table.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Libraries](/docs/reference/engine/libraries)
2. /
3. [table](/docs/reference/engine/libraries/table)

English

Feedback

Engine Library

table

---

## Summary

Functions

|

[clear](#clear) (table :  [table](/docs/luau/tables) ) : ()

 |
| --- | --- |
|

[clone](#clone) (t :  [table](/docs/luau/tables) ) :[table](/docs/luau/tables)

 |
|

[concat](#concat) (t :  [{any}](/docs/luau/tables#arrays) , sep :  [string](/docs/luau/strings) , i :  [number](/docs/luau/numbers) , j :  [number](/docs/luau/numbers) ) :[string](/docs/luau/strings)

 |
|

[create](#create) (count :  [number](/docs/luau/numbers) , value :  Variant ) :[table](/docs/luau/tables)

 |
|

[find](#find) (haystack :  [table](/docs/luau/tables) , needle :  Variant , init :  [number](/docs/luau/numbers) ) : Variant

 |
|

[foreach](#foreach) (t :  [table](/docs/luau/tables) , f :  [function](/docs/luau/functions) ) : ()

Deprecated

 |
|

[foreachi](#foreachi) (t :  [{any}](/docs/luau/tables#arrays) , f :  [function](/docs/luau/functions) ) : ()

Deprecated

 |
|

[freeze](#freeze) (t :  [table](/docs/luau/tables) ) :[table](/docs/luau/tables)

 |
|

[getn](#getn) (t :  [{any}](/docs/luau/tables#arrays) ) :[number](/docs/luau/numbers)

Deprecated

 |
|

[insert](#insert) (t :  [{any}](/docs/luau/tables#arrays) , pos :  [number](/docs/luau/numbers) , value :  Variant ) : ()

 |
|

[insert](#insert-t-value) (t :  [{any}](/docs/luau/tables#arrays) , value :  Variant ) : ()

 |
|

[isfrozen](#isfrozen) (t :  [table](/docs/luau/tables) ) :[boolean](/docs/luau/booleans)

 |
|

[maxn](#maxn) (t :  [table](/docs/luau/tables) ) :[number](/docs/luau/numbers)

 |
|

[move](#move) (src :  [table](/docs/luau/tables) , a :  [number](/docs/luau/numbers) , b :  [number](/docs/luau/numbers) , t :  [number](/docs/luau/numbers) , dst :  [table](/docs/luau/tables) ) :[table](/docs/luau/tables)

 |
|

[pack](#pack) (values... :  Variant ) :[table](/docs/luau/tables)

 |
|

[remove](#remove) (t :  [{any}](/docs/luau/tables#arrays) , pos :  [number](/docs/luau/numbers) ) : Variant

 |
|

[sort](#sort) (t :  [{any}](/docs/luau/tables#arrays) , comp :  [function](/docs/luau/functions) ) : ()

 |
|

[unpack](#unpack) (list :  [table](/docs/luau/tables) , i :  [number](/docs/luau/numbers) , j :  [number](/docs/luau/numbers) ) :[Tuple](/docs/luau/tuples)

 |

---

API Reference

Functions

clear

table.clear (table :[table](/docs/luau/tables) ) : ()

Parameters

|

table :[table](/docs/luau/tables)

 |

Returns

()

Code Samples

##### Table Clear

Provide feedback

---

clone

table.clone (t :[table](/docs/luau/tables) ) :[table](/docs/luau/tables)

Parameters

|

t :[table](/docs/luau/tables)

 |

Returns

[table](/docs/luau/tables)

Code Samples

##### Table Clone

Provide feedback

---

concat

table.concat (

t :[{any}](/docs/luau/tables#arrays) , sep :[string](/docs/luau/strings) , i :[number](/docs/luau/numbers) , j :[number](/docs/luau/numbers)

) :[string](/docs/luau/strings)

Parameters

|

t :[{any}](/docs/luau/tables#arrays)

 |
|

sep :[string](/docs/luau/strings)

 |
|

i :[number](/docs/luau/numbers)

Default Value: 1 |
|

j :[number](/docs/luau/numbers)

 |

Returns

[string](/docs/luau/strings)

Code Samples

##### Table Concat

Provide feedback

---

create

table.create (

count :[number](/docs/luau/numbers) , value : Variant

) :[table](/docs/luau/tables)

Parameters

|

count :[number](/docs/luau/numbers)

 |
|

value : Variant

 |

Returns

[table](/docs/luau/tables)

Code Samples

##### Table Create

Provide feedback

---

find

table.find (

haystack :[table](/docs/luau/tables) , needle : Variant , init :[number](/docs/luau/numbers)

) : Variant

Parameters

|

haystack :[table](/docs/luau/tables)

 |
|

needle : Variant

 |
|

init :[number](/docs/luau/numbers)

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

table.freeze (t :[table](/docs/luau/tables) ) :[table](/docs/luau/tables)

Parameters

|

t :[table](/docs/luau/tables)

 |

Returns

[table](/docs/luau/tables)

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

t :[{any}](/docs/luau/tables#arrays) , pos :[number](/docs/luau/numbers) , value : Variant

) : ()

Parameters

|

t :[{any}](/docs/luau/tables#arrays)

 |
|

pos :[number](/docs/luau/numbers)

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

t :[{any}](/docs/luau/tables#arrays) , value : Variant

) : ()

Parameters

|

t :[{any}](/docs/luau/tables#arrays)

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

table.isfrozen (t :[table](/docs/luau/tables) ) :[boolean](/docs/luau/booleans)

Parameters

|

t :[table](/docs/luau/tables)

 |

Returns

[boolean](/docs/luau/booleans)

Code Samples

##### Table Isfrozen

Provide feedback

---

maxn

table.maxn (t :[table](/docs/luau/tables) ) :[number](/docs/luau/numbers)

Parameters

|

t :[table](/docs/luau/tables)

 |

Returns

[number](/docs/luau/numbers)

Code Samples

##### Table Maxn

Provide feedback

---

move

table.move (

src :[table](/docs/luau/tables) , a :[number](/docs/luau/numbers) , b :[number](/docs/luau/numbers) , t :[number](/docs/luau/numbers) , dst :[table](/docs/luau/tables)

) :[table](/docs/luau/tables)

Parameters

|

src :[table](/docs/luau/tables)

 |
|

a :[number](/docs/luau/numbers)

 |
|

b :[number](/docs/luau/numbers)

 |
|

t :[number](/docs/luau/numbers)

 |
|

dst :[table](/docs/luau/tables)

Default Value: src |

Returns

[table](/docs/luau/tables)

Code Samples

##### Table Move

Provide feedback

---

pack

table.pack (values... : Variant ) :[table](/docs/luau/tables)

Parameters

|

values... : Variant

 |

Returns

[table](/docs/luau/tables)

Code Samples

##### Table Pack

Provide feedback

---

remove

table.remove (

t :[{any}](/docs/luau/tables#arrays) , pos :[number](/docs/luau/numbers)

) : Variant

Parameters

|

t :[{any}](/docs/luau/tables#arrays)

 |
|

pos :[number](/docs/luau/numbers)

 |

Returns

Variant

Code Samples

##### Table Remove

Provide feedback

---

sort

table.sort (

t :[{any}](/docs/luau/tables#arrays) , comp :[function](/docs/luau/functions)

) : ()

Parameters

|

t :[{any}](/docs/luau/tables#arrays)

 |
|

comp :[function](/docs/luau/functions)

Default Value: nil |

Returns

()

Code Samples

##### Table Sort

Provide feedback

---

unpack

table.unpack (

list :[table](/docs/luau/tables) , i :[number](/docs/luau/numbers) , j :[number](/docs/luau/numbers)

) :[Tuple](/docs/luau/tuples)

Parameters

|

list :[table](/docs/luau/tables)

 |
|

i :[number](/docs/luau/numbers)

Default Value: 1 |
|

j :[number](/docs/luau/numbers)

Default Value: #list |

Returns

[Tuple](/docs/luau/tuples)

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
