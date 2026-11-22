<!-- Source: https://create.roblox.com/docs/reference/engine/libraries/debug -->

debug | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/libraries/debug.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Libraries](/docs/reference/engine/libraries)
2. /
3. [debug](/docs/reference/engine/libraries/debug)

English

Feedback

Engine Library

debug

---

## Summary

Functions

|

[traceback](#traceback) (message :  [string](/docs/luau/strings) , level :  [number](/docs/luau/numbers) ) :[string](/docs/luau/strings)

 |
| --- | --- |
|

[traceback](#traceback-thread-mes) (thread :  [coroutine](/docs/reference/engine/libraries/coroutine) , message :  [string](/docs/luau/strings) , level :  [number](/docs/luau/numbers) ) :[string](/docs/luau/strings)

 |
|

[info](#info) (level :  [number](/docs/luau/numbers) , options :  [string](/docs/luau/strings) ) :[Tuple](/docs/luau/tuples)

 |
|

[info](#info-function-o) (function :  [function](/docs/luau/functions) , options :  [string](/docs/luau/strings) ) :[Tuple](/docs/luau/tuples)

 |
|

[info](#info-thread-lev) (thread :  [coroutine](/docs/reference/engine/libraries/coroutine) , level :  [number](/docs/luau/numbers) , options :  [string](/docs/luau/strings) ) :[Tuple](/docs/luau/tuples)

 |
|

[profilebegin](#profilebegin) (label :  [string](/docs/luau/strings) ) : ()

 |
|

[profileend](#profileend) () : ()

 |
|

[getmemorycategory](#getmemorycategory) () :[string](/docs/luau/strings)

 |
|

[setmemorycategory](#setmemorycategory) (tag :  [string](/docs/luau/strings) ) :[string](/docs/luau/strings)

 |
|

[resetmemorycategory](#resetmemorycategory) () : ()

 |
|

[dumpcodesize](#dumpcodesize) () : ()

 |

---

API Reference

Functions

traceback

debug.traceback (

message :[string](/docs/luau/strings) , level :[number](/docs/luau/numbers)

) :[string](/docs/luau/strings)

Parameters

|

message :[string](/docs/luau/strings)

 |
|

level :[number](/docs/luau/numbers)

Default Value: 1 |

Returns

[string](/docs/luau/strings)

Code Samples

##### Debug Traceback

Provide feedback

---

traceback

debug.traceback (

thread :[coroutine](/docs/reference/engine/libraries/coroutine) , message :[string](/docs/luau/strings) , level :[number](/docs/luau/numbers)

) :[string](/docs/luau/strings)

Parameters

|

thread :[coroutine](/docs/reference/engine/libraries/coroutine)

 |
|

message :[string](/docs/luau/strings)

 |
|

level :[number](/docs/luau/numbers)

Default Value: 1 |

Returns

[string](/docs/luau/strings)

Code Samples

##### Debug Traceback Of A Thread

Provide feedback

---

info

debug.info (

level :[number](/docs/luau/numbers) , options :[string](/docs/luau/strings)

) :[Tuple](/docs/luau/tuples)

Parameters

|

level :[number](/docs/luau/numbers)

 |
|

options :[string](/docs/luau/strings)

 |

Returns

[Tuple](/docs/luau/tuples)

Code Samples

##### Debug Info By Level

Provide feedback

---

info

debug.info (

function :[function](/docs/luau/functions) , options :[string](/docs/luau/strings)

) :[Tuple](/docs/luau/tuples)

Parameters

|

function :[function](/docs/luau/functions)

 |
|

options :[string](/docs/luau/strings)

 |

Returns

[Tuple](/docs/luau/tuples)

Code Samples

##### Debug Info By Function

Provide feedback

---

info

debug.info (

thread :[coroutine](/docs/reference/engine/libraries/coroutine) , level :[number](/docs/luau/numbers) , options :[string](/docs/luau/strings)

) :[Tuple](/docs/luau/tuples)

Parameters

|

thread :[coroutine](/docs/reference/engine/libraries/coroutine)

 |
|

level :[number](/docs/luau/numbers)

 |
|

options :[string](/docs/luau/strings)

 |

Returns

[Tuple](/docs/luau/tuples)

Code Samples

##### Debug Info By Thread

Provide feedback

---

profilebegin

debug.profilebegin (label :[string](/docs/luau/strings) ) : ()

Parameters

|

label :[string](/docs/luau/strings)

 |

Returns

()

Code Samples

Debug Profile Begin

```

local function buildGrid(size)

	debug.profilebegin("BuildGrid")

	local grid = table.create(size * size, 0)

	debug.profileend()

	return grid

end

print(#buildGrid(32)) --> 1024

```

Provide feedback

---

profileend

debug.profileend () : ()

Returns

()

Code Samples

Debug Profile End

```

debug.profilebegin("Outer")

debug.profilebegin("Inner")

-- Work done here is timed under both labels

debug.profileend() -- closes "Inner"

debug.profileend() -- closes "Outer"

```

Provide feedback

---

getmemorycategory

debug.getmemorycategory () :[string](/docs/luau/strings)

Returns

[string](/docs/luau/strings)

Code Samples

Debug Get Memory Category

```

local category = debug.getmemorycategory()

print(type(category)) --> string

-- The category follows the thread, so a new one can differ from this one

local previous = debug.setmemorycategory("Pathfinding")

print(debug.getmemorycategory()) --> Pathfinding

debug.setmemorycategory(previous)

```

Provide feedback

---

setmemorycategory

debug.setmemorycategory (tag :[string](/docs/luau/strings) ) :[string](/docs/luau/strings)

Parameters

|

tag :[string](/docs/luau/strings)

 |

Returns

[string](/docs/luau/strings)

Code Samples

Debug Set Memory Category

```

local original = debug.setmemorycategory("MapGeneration")

print(debug.getmemorycategory()) --> MapGeneration

-- Allocations made here are listed under "MapGeneration" in the Developer Console

local tiles = table.create(1000, 0)

-- The return value is the previous category, so it can be restored

print(debug.setmemorycategory(original) == "MapGeneration") --> true

```

Provide feedback

---

resetmemorycategory

debug.resetmemorycategory () : ()

Returns

()

Code Samples

Debug Reset Memory Category

```

local automatic = debug.getmemorycategory()

debug.setmemorycategory("Spawning")

print(debug.getmemorycategory()) --> Spawning

debug.resetmemorycategory()

print(debug.getmemorycategory() == automatic) --> true

```

Provide feedback

---

dumpcodesize

debug.dumpcodesize () : ()

Returns

()

Code Samples

Debug Dump Code Size

```

-- debug.dumpcodesize() only works from the Studio Command Bar, where it prints a

-- report to the Output with one table per native script, largest functions first:

--   # Native Code Size Analysis

--     <n> scripts, <n> functions, <n> KB memory, 256 MB code size limit

--   ## <script name>

--     <n> functions, <n> KB memory

--     | Function | Line | Native Code Size | Native Code Size (%) |

-- Only scripts that start with --!native and have run appear in the report.

-- From a Script it raises an error, which pcall catches

local ok, message = pcall(debug.dumpcodesize)

print(ok) --> false

print(message) --> dumpcodesize can only be called from CommandBar

```

Provide feedback

---

Jump to

▼

debug

[Summary](#summary)

[Functions](#summary-functions)

[Functions](#functions)

[traceback()](#traceback)

[info()](#info)

[profilebegin()](#profilebegin)

[profileend()](#profileend)

[getmemorycategory()](#getmemorycategory)

[setmemorycategory()](#setmemorycategory)

[resetmemorycategory()](#resetmemorycategory)

[dumpcodesize()](#dumpcodesize)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
