<!-- Source: https://create.roblox.com/docs/reference/engine/datatypes/SharedTable -->

SharedTable | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/datatypes/SharedTable.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Data types](/docs/reference/engine/datatypes)
2. /
3. [SharedTable](/docs/reference/engine/datatypes/SharedTable)

English

Feedback

Engine Data Type

SharedTable

---

## Summary

Constructors

|

[new](#new) ()

 |
| --- | --- |
|

[new](#new-t) (t :  [table](/docs/luau/tables) )

 |

Functions

|

[clear](#clear) (st :  [SharedTable](/docs/reference/engine/datatypes/SharedTable) ) : ()

 |
|

[clone](#clone) (st :  [SharedTable](/docs/reference/engine/datatypes/SharedTable) , deep :  [boolean](/docs/luau/booleans) ? ) :[SharedTable](/docs/reference/engine/datatypes/SharedTable)

 |
|

[cloneAndFreeze](#cloneAndFreeze) (st :  [SharedTable](/docs/reference/engine/datatypes/SharedTable) , deep :  [boolean](/docs/luau/booleans) ? ) :[SharedTable](/docs/reference/engine/datatypes/SharedTable)

 |
|

[increment](#increment) (st :  [SharedTable](/docs/reference/engine/datatypes/SharedTable) , key :  [string](/docs/luau/strings)  | [number](/docs/luau/numbers) , delta :  [number](/docs/luau/numbers) ) :[number](/docs/luau/numbers)

 |
|

[isFrozen](#isFrozen) (st :  [SharedTable](/docs/reference/engine/datatypes/SharedTable) ) :[boolean](/docs/luau/booleans)

 |
|

[size](#size) (st :  [SharedTable](/docs/reference/engine/datatypes/SharedTable) ) :[number](/docs/luau/numbers)

 |
|

[update](#update) (st :  [SharedTable](/docs/reference/engine/datatypes/SharedTable) , key :  [string](/docs/luau/strings)  | [number](/docs/luau/numbers) , f :  [function](/docs/luau/functions) ) : ()

 |

Code Samples

Element Access

```

local st = SharedTable.new()

st[1] = "a"

st["x"] = true

st.y = 5

assert(st[1] == "a")

assert(st["x"] == true)

assert(st.x == true)

assert(st["y"] == 5)

assert(st.y == 5)

-- true is not a valid SharedTable key, so attempting to set that key

-- fails:

assert(not pcall(function() st[true] = 100 end))

-- A function is not a valid SharedTable value, so attempting to set a

-- value to a function fails:

assert(not pcall(function() st["f"] = function() end end))

```

Element Iteration

```

local st = SharedTable.new({"a", "b", "c"})

for k, v in SharedTable.clone(st, false) do

	print(k, ": ", v)

end

for k, v in st do

	print(k, ": ", v)

end

```

---

API Reference

Constructors

new

SharedTable.new ()

Provide feedback

---

new

SharedTable.new (t :[table](/docs/luau/tables) )

Parameters

|

t :[table](/docs/luau/tables)

 |

Provide feedback

---

Functions

clear

SharedTable.clear (st :[SharedTable](/docs/reference/engine/datatypes/SharedTable) ) : ()

Parameters

|

st :[SharedTable](/docs/reference/engine/datatypes/SharedTable)

 |

Returns

()

Provide feedback

---

clone

SharedTable.clone (

st :[SharedTable](/docs/reference/engine/datatypes/SharedTable) , deep :[boolean](/docs/luau/booleans) ?

) :[SharedTable](/docs/reference/engine/datatypes/SharedTable)

Parameters

|

st :[SharedTable](/docs/reference/engine/datatypes/SharedTable)

 |
|

deep :[boolean](/docs/luau/booleans) ?

Default Value: false |

Returns

[SharedTable](/docs/reference/engine/datatypes/SharedTable)

Provide feedback

---

cloneAndFreeze

SharedTable.cloneAndFreeze (

st :[SharedTable](/docs/reference/engine/datatypes/SharedTable) , deep :[boolean](/docs/luau/booleans) ?

) :[SharedTable](/docs/reference/engine/datatypes/SharedTable)

Parameters

|

st :[SharedTable](/docs/reference/engine/datatypes/SharedTable)

 |
|

deep :[boolean](/docs/luau/booleans) ?

Default Value: false |

Returns

[SharedTable](/docs/reference/engine/datatypes/SharedTable)

Provide feedback

---

increment

SharedTable.increment (

st :[SharedTable](/docs/reference/engine/datatypes/SharedTable) , key :[string](/docs/luau/strings)  | [number](/docs/luau/numbers) , delta :[number](/docs/luau/numbers)

) :[number](/docs/luau/numbers)

Parameters

|

st :[SharedTable](/docs/reference/engine/datatypes/SharedTable)

 |
|

key :[string](/docs/luau/strings)  | [number](/docs/luau/numbers)

 |
|

delta :[number](/docs/luau/numbers)

 |

Returns

[number](/docs/luau/numbers)

Provide feedback

---

isFrozen

SharedTable.isFrozen (st :[SharedTable](/docs/reference/engine/datatypes/SharedTable) ) :[boolean](/docs/luau/booleans)

Parameters

|

st :[SharedTable](/docs/reference/engine/datatypes/SharedTable)

 |

Returns

[boolean](/docs/luau/booleans)

Provide feedback

---

size

SharedTable.size (st :[SharedTable](/docs/reference/engine/datatypes/SharedTable) ) :[number](/docs/luau/numbers)

Parameters

|

st :[SharedTable](/docs/reference/engine/datatypes/SharedTable)

 |

Returns

[number](/docs/luau/numbers)

Provide feedback

---

update

SharedTable.update (

st :[SharedTable](/docs/reference/engine/datatypes/SharedTable) , key :[string](/docs/luau/strings)  | [number](/docs/luau/numbers) , f :[function](/docs/luau/functions)

) : ()

Parameters

|

st :[SharedTable](/docs/reference/engine/datatypes/SharedTable)

 |
|

key :[string](/docs/luau/strings)  | [number](/docs/luau/numbers)

 |
|

f :[function](/docs/luau/functions)

 |

Returns

()

Provide feedback

---

Jump to

▼

SharedTable

[Summary](#summary)

[Constructors](#summary-constructors)

[Functions](#summary-functions)

[Constructors](#constructors)

[new()](#new)

[Functions](#functions)

[clear()](#clear)

[clone()](#clone)

[cloneAndFreeze()](#cloneAndFreeze)

[increment()](#increment)

[isFrozen()](#isFrozen)

[size()](#size)

[update()](#update)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
