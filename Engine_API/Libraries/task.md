<!-- Source: https://create.roblox.com/docs/reference/engine/libraries/task -->

task | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/libraries/task.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Libraries](/docs/reference/engine/libraries)
2. /
3. [task](/docs/reference/engine/libraries/task)

English

Feedback

Engine Library

task

---

## Summary

Functions

|

[spawn](#spawn) (functionOrThread :  [function](/docs/luau/functions)  | [coroutine](/docs/reference/engine/libraries/coroutine) , ... :  Variant ) :[coroutine](/docs/reference/engine/libraries/coroutine)

 |
| --- | --- |
|

[defer](#defer) (functionOrThread :  [function](/docs/luau/functions)  | [coroutine](/docs/reference/engine/libraries/coroutine) , ... :  Variant ) :[coroutine](/docs/reference/engine/libraries/coroutine)

 |
|

[delay](#delay) (duration :  [number](/docs/luau/numbers) , functionOrThread :  [function](/docs/luau/functions)  | [coroutine](/docs/reference/engine/libraries/coroutine) , ... :  Variant ) :[coroutine](/docs/reference/engine/libraries/coroutine)

 |
|

[desynchronize](#desynchronize) () : ()

 |
|

[synchronize](#synchronize) () : ()

 |
|

[wait](#wait) (duration :  [number](/docs/luau/numbers) ) :[number](/docs/luau/numbers)

 |
|

[cancel](#cancel) (thread :  [coroutine](/docs/reference/engine/libraries/coroutine) ) : ()

 |

---

API Reference

Functions

spawn

task.spawn (

functionOrThread :[function](/docs/luau/functions)  | [coroutine](/docs/reference/engine/libraries/coroutine) , ... : Variant

) :[coroutine](/docs/reference/engine/libraries/coroutine)

Parameters

|

functionOrThread :[function](/docs/luau/functions)  | [coroutine](/docs/reference/engine/libraries/coroutine)

 |
|

... : Variant

 |

Returns

[coroutine](/docs/reference/engine/libraries/coroutine)

Code Samples

Task Spawn

```

local function greet(name, punctuation)

	print("Hello, " .. name .. punctuation)

end

print("before") --> before

task.spawn(greet, "Roblox", "!") --> Hello, Roblox!

print("after") --> after

-- A suspended coroutine can be resumed with arguments too.

local worker = coroutine.create(function(label)

	print("worker started with", label)

end)

task.spawn(worker, "job 1") --> worker started with job 1

print(coroutine.status(worker)) --> dead

```

Provide feedback

---

defer

task.defer (

functionOrThread :[function](/docs/luau/functions)  | [coroutine](/docs/reference/engine/libraries/coroutine) , ... : Variant

) :[coroutine](/docs/reference/engine/libraries/coroutine)

Parameters

|

functionOrThread :[function](/docs/luau/functions)  | [coroutine](/docs/reference/engine/libraries/coroutine)

 |
|

... : Variant

 |

Returns

[coroutine](/docs/reference/engine/libraries/coroutine)

Code Samples

Task Defer

```

print("one") --> one

task.defer(function(message)

	print(message) --> deferred

end, "deferred")

task.spawn(function()

	print("two") --> two

end)

print("three") --> three

-- The deferred function runs after the current code has finished, so it prints last.

```

Provide feedback

---

delay

task.delay (

duration :[number](/docs/luau/numbers) , functionOrThread :[function](/docs/luau/functions)  | [coroutine](/docs/reference/engine/libraries/coroutine) , ... : Variant

) :[coroutine](/docs/reference/engine/libraries/coroutine)

Parameters

|

duration :[number](/docs/luau/numbers)

 |
|

functionOrThread :[function](/docs/luau/functions)  | [coroutine](/docs/reference/engine/libraries/coroutine)

 |
|

... : Variant

 |

Returns

[coroutine](/docs/reference/engine/libraries/coroutine)

Code Samples

Task Delay

```

local scheduledAt = os.clock()

task.delay(1, function(message)

	local elapsed = os.clock() - scheduledAt

	print(message, elapsed >= 1) --> Delayed hello	true

end, "Delayed hello")

print("scheduled") --> scheduled

-- The returned thread can be cancelled before it runs.

local cancelled = task.delay(2, function()

	print("never printed")

end)

task.cancel(cancelled)

```

Provide feedback

---

desynchronize

task.desynchronize () : ()

Returns

()

Code Samples

Task Desynchronize

```

-- Inside a Script that is a descendant of an Actor, desynchronize() resumes the

-- thread in the next parallel phase, where heavy work can run alongside other Actors.

-- Outside of an Actor it raises an error, which pcall lets us observe.

local ok = pcall(task.desynchronize)

print(ok) --> false (when this script is not a descendant of an Actor)

```

Provide feedback

---

synchronize

task.synchronize () : ()

Returns

()

Code Samples

Task Synchronize

```

-- Inside a Script that is a descendant of an Actor, synchronize() resumes the

-- thread in the next serial phase, where it is safe to modify the data model.

-- Outside of an Actor it raises an error, which pcall lets us observe.

local ok = pcall(task.synchronize)

print(ok) --> false (when this script is not a descendant of an Actor)

```

Provide feedback

---

wait

task.wait (duration :[number](/docs/luau/numbers) ) :[number](/docs/luau/numbers)

Parameters

|

duration :[number](/docs/luau/numbers)

Default Value: 0 |

Returns

[number](/docs/luau/numbers)

Code Samples

Task Wait

```

local elapsed = task.wait(1)

print(elapsed >= 1) --> true

-- With no argument the thread resumes on the next Heartbeat.

local frameTime = task.wait()

print(frameTime < 1) --> true

```

Provide feedback

---

cancel

task.cancel (thread :[coroutine](/docs/reference/engine/libraries/coroutine) ) : ()

Parameters

|

thread :[coroutine](/docs/reference/engine/libraries/coroutine)

 |

Returns

()

Code Samples

Task Cancel

```

local thread = task.delay(5, function()

	print("Hello world!") -- never printed

end)

task.cancel(thread)

print(coroutine.status(thread)) --> dead

-- Cancelling the currently running thread is not allowed and raises an error.

local ok = pcall(task.cancel, coroutine.running())

print(ok) --> false

```

Provide feedback

---

Jump to

▼

task

[Summary](#summary)

[Functions](#summary-functions)

[Functions](#functions)

[spawn()](#spawn)

[defer()](#defer)

[delay()](#delay)

[desynchronize()](#desynchronize)

[synchronize()](#synchronize)

[wait()](#wait)

[cancel()](#cancel)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
