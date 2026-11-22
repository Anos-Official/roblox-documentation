<!-- Source: https://create.roblox.com/docs/reference/engine/classes/StudioTestService -->

StudioTestService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/StudioTestService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [StudioTestService](/docs/reference/engine/classes/StudioTestService)

English

Feedback

Engine Class

StudioTestService

Not Creatable

Service

Not Replicated

---

## Summary

Properties

|

[EditModeActive](#EditModeActive) :[boolean](/docs/luau/booleans)

 |
| --- | --- |

Methods

|

[AddPlayers](#AddPlayers) (numPlayers :  [number](/docs/luau/numbers) ) : ()

 |
|

[CanLeaveTest](#CanLeaveTest) () :[boolean](/docs/luau/booleans)

 |
|

[EndTest](#EndTest) (value :  Variant ) : ()

 |
|

[ExecuteMultiplayerTestAsync](#ExecuteMultiplayerTestAsync) (numPlayers :  [number](/docs/luau/numbers) , args :  Variant ) : Variant

 |
|

[ExecutePlayModeAsync](#ExecutePlayModeAsync) (args :  Variant ) : Variant

 |
|

[ExecuteRunModeAsync](#ExecuteRunModeAsync) (args :  Variant ) : Variant

 |
|

[GetTestArgs](#GetTestArgs) () : Variant

 |
|

[LeaveTest](#LeaveTest) () : ()

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Properties

EditModeActive

Plugin Security

Read Parallel

StudioTestService.EditModeActive :[boolean](/docs/luau/booleans)

Provide feedback

---

Methods

AddPlayers

StudioTestService:AddPlayers (numPlayers :[number](/docs/luau/numbers) ) : ()

Parameters

|

numPlayers :[number](/docs/luau/numbers)

 |

Returns

()

Code Samples

Add Players example

```

local StudioTestService = game:GetService("StudioTestService")

task.wait(5)

StudioTestService:AddPlayers(3)

```

Provide feedback

---

CanLeaveTest

StudioTestService:CanLeaveTest () :[boolean](/docs/luau/booleans)

Returns

[boolean](/docs/luau/booleans)

Code Samples

Can Leave Test example

```

local StudioTestService = game:GetService("StudioTestService")

if StudioTestService:CanLeaveTest() then

    StudioTestService:LeaveTest()

end

```

Provide feedback

---

EndTest

StudioTestService:EndTest (value : Variant ) : ()

Parameters

|

value : Variant

 |

Returns

()

Code Samples

End Test example

```

local StudioTestService = game:GetService("StudioTestService")

-- Server-side logic runs here, waits for players, runs assertions, etc.

StudioTestService:EndTest("Success!")

```

Provide feedback

---

ExecuteMultiplayerTestAsync

Yields

Plugin Security

StudioTestService:ExecuteMultiplayerTestAsync (

numPlayers :[number](/docs/luau/numbers) , args : Variant

) : Variant

Parameters

|

numPlayers :[number](/docs/luau/numbers)

 |
|

args : Variant

 |

Returns

Variant

Code Samples

Execute Multiplayer Test example

```

local StudioTestService = game:GetService("StudioTestService")

local result = StudioTestService:ExecuteMultiplayerTestAsync(4, "LobbySpawnTest")

assert(result == "Success!")

print("Test finished:", result)

```

Provide feedback

---

ExecutePlayModeAsync

Yields

Plugin Security

StudioTestService:ExecutePlayModeAsync (args : Variant ) : Variant

Parameters

|

args : Variant

 |

Returns

Variant

Provide feedback

---

ExecuteRunModeAsync

Yields

Plugin Security

StudioTestService:ExecuteRunModeAsync (args : Variant ) : Variant

Parameters

|

args : Variant

 |

Returns

Variant

Provide feedback

---

GetTestArgs

StudioTestService:GetTestArgs () : Variant

Returns

Variant

Code Samples

Get Test Args example

```

local StudioTestService = game:GetService("StudioTestService")

local args = StudioTestService:GetTestArgs()

print("Received args:", args)

```

Provide feedback

---

LeaveTest

StudioTestService:LeaveTest () : ()

Returns

()

Provide feedback

---

Jump to

▼

StudioTestService

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[EditModeActive](#EditModeActive)

[Methods](#methods)

[AddPlayers()](#AddPlayers)

[CanLeaveTest()](#CanLeaveTest)

[EndTest()](#EndTest)

[ExecuteMultiplayerTestAsync()](#ExecuteMultiplayerTestAsync)

[ExecutePlayModeAsync()](#ExecutePlayModeAsync)

[ExecuteRunModeAsync()](#ExecuteRunModeAsync)

[GetTestArgs()](#GetTestArgs)

[LeaveTest()](#LeaveTest)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
