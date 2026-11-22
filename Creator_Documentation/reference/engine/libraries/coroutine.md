<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/libraries/coroutine -->

coroutine | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/libraries/coroutine.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Libraries](/docs/en-us/reference/engine/libraries)
2. /
3. [coroutine](/docs/en-us/reference/engine/libraries/coroutine)

English

Feedback

Engine Library

coroutine

---

## Summary

Functions

|

[close](#close) (co :  [coroutine](/docs/en-us/reference/engine/libraries/coroutine) ) :[boolean](/docs/en-us/luau/booleans) , Variant <[string](/docs/en-us/luau/strings) , () >

 |
| --- | --- |
|

[create](#create) (f :  [function](/docs/en-us/luau/functions) ) :[coroutine](/docs/en-us/reference/engine/libraries/coroutine)

 |
|

[finally](#finally) (co :  [coroutine](/docs/en-us/reference/engine/libraries/coroutine) , callback :  Variant )

 |
|

[isyieldable](#isyieldable) () :[boolean](/docs/en-us/luau/booleans)

 |
|

[resume](#resume) (co :  [coroutine](/docs/en-us/reference/engine/libraries/coroutine) , ... :  Variant ) :[boolean](/docs/en-us/luau/booleans) , Variant <[Tuple](/docs/en-us/luau/tuples) , [string](/docs/en-us/luau/strings) >

 |
|

[running](#running) () :[coroutine](/docs/en-us/reference/engine/libraries/coroutine)

 |
|

[status](#status) (co :  [coroutine](/docs/en-us/reference/engine/libraries/coroutine) ) :[string](/docs/en-us/luau/strings)

 |
|

[wrap](#wrap) (f :  [function](/docs/en-us/luau/functions) ) :[function](/docs/en-us/luau/functions)

 |
|

[yield](#yield) (... :  [Tuple](/docs/en-us/luau/tuples) ) :[Tuple](/docs/en-us/luau/tuples) < Variant >

 |

---

API Reference

Functions

close

coroutine.close (co :[coroutine](/docs/en-us/reference/engine/libraries/coroutine) ) :[boolean](/docs/en-us/luau/booleans) , Variant <[string](/docs/en-us/luau/strings) , () >

Parameters

|

co :[coroutine](/docs/en-us/reference/engine/libraries/coroutine)

 |

Returns

[boolean](/docs/en-us/luau/booleans) , Variant <[string](/docs/en-us/luau/strings) , () >

Code Samples

##### Coroutine Close

Provide feedback

---

create

coroutine.create (f :[function](/docs/en-us/luau/functions) ) :[coroutine](/docs/en-us/reference/engine/libraries/coroutine)

Parameters

|

f :[function](/docs/en-us/luau/functions)

 |

Returns

[coroutine](/docs/en-us/reference/engine/libraries/coroutine)

Code Samples

##### Coroutine Create

Provide feedback

---

finally

coroutine.finally (

co :[coroutine](/docs/en-us/reference/engine/libraries/coroutine) , callback : Variant )

Parameters

|

co :[coroutine](/docs/en-us/reference/engine/libraries/coroutine)

 |
|

callback : Variant

 |

Code Samples

Coroutine Finally

```

local function observe(co, label)

	coroutine.finally(co, function(status, ...)

		print(label, status, ...)

	end)

end

local finishing = coroutine.create(function()

	return "result"

end)

observe(finishing, "finishing") --> finishing finished result

coroutine.resume(finishing)

local failing = coroutine.create(function()

	error("boom", 0)

end)

observe(failing, "failing") --> failing error boom

coroutine.resume(failing)

local cancelled = coroutine.create(function()

	coroutine.yield()

end)

coroutine.resume(cancelled)

observe(cancelled, "cancelled") --> cancelled cancelled

coroutine.close(cancelled)

```

Provide feedback

---

isyieldable

coroutine.isyieldable () :[boolean](/docs/en-us/luau/booleans)

Returns

[boolean](/docs/en-us/luau/booleans)

Code Samples

##### Coroutine Is Yieldable

Provide feedback

---

resume

coroutine.resume (

co :[coroutine](/docs/en-us/reference/engine/libraries/coroutine) , ... : Variant

) :[boolean](/docs/en-us/luau/booleans) , Variant <[Tuple](/docs/en-us/luau/tuples) , [string](/docs/en-us/luau/strings) >

Parameters

|

co :[coroutine](/docs/en-us/reference/engine/libraries/coroutine)

 |
|

... : Variant

 |

Returns

[boolean](/docs/en-us/luau/booleans) , Variant <[Tuple](/docs/en-us/luau/tuples) , [string](/docs/en-us/luau/strings) >

Code Samples

##### Coroutine Resume

Provide feedback

---

running

coroutine.running () :[coroutine](/docs/en-us/reference/engine/libraries/coroutine)

Returns

[coroutine](/docs/en-us/reference/engine/libraries/coroutine)

Code Samples

##### Coroutine Running

Provide feedback

---

status

coroutine.status (co :[coroutine](/docs/en-us/reference/engine/libraries/coroutine) ) :[string](/docs/en-us/luau/strings)

Parameters

|

co :[coroutine](/docs/en-us/reference/engine/libraries/coroutine)

 |

Returns

[string](/docs/en-us/luau/strings)

Code Samples

##### Coroutine Status

Provide feedback

---

wrap

coroutine.wrap (f :[function](/docs/en-us/luau/functions) ) :[function](/docs/en-us/luau/functions)

Parameters

|

f :[function](/docs/en-us/luau/functions)

 |

Returns

[function](/docs/en-us/luau/functions)

Code Samples

##### Coroutine Wrap

Provide feedback

---

yield

coroutine.yield (... :[Tuple](/docs/en-us/luau/tuples) ) :[Tuple](/docs/en-us/luau/tuples) < Variant >

Parameters

|

... :[Tuple](/docs/en-us/luau/tuples)

 |

Returns

[Tuple](/docs/en-us/luau/tuples) < Variant >

Code Samples

##### Coroutine Yield

Provide feedback

---

Jump to

▼

coroutine

[Summary](#summary)

[Functions](#summary-functions)

[Functions](#functions)

[close()](#close)

[create()](#create)

[finally()](#finally)

[isyieldable()](#isyieldable)

[resume()](#resume)

[running()](#running)

[status()](#status)

[wrap()](#wrap)

[yield()](#yield)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
