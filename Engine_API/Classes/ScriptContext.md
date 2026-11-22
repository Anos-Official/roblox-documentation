<!-- Source: https://create.roblox.com/docs/reference/engine/classes/ScriptContext -->

ScriptContext | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/ScriptContext.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [ScriptContext](/docs/reference/engine/classes/ScriptContext)

English

Feedback

Engine Class

ScriptContext

Not Creatable

Service

Not Replicated

---

## Summary

Methods

|

[EnableCoverage](#EnableCoverage) (instance :  [Instance](/docs/reference/engine/datatypes/Instance) ) : ()

 |
| --- | --- |
|

[GetCoverageStats](#GetCoverageStats) () :[{any}](/docs/luau/tables#arrays)

 |
|

[SetTimeout](#SetTimeout) (seconds :  [number](/docs/luau/numbers) ) : ()

 |

Events

|

[Error](#Error) (message :  [string](/docs/luau/strings) , stackTrace :  [string](/docs/luau/strings) , script :  [Instance](/docs/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Methods

EnableCoverage

Capabilities: PluginOrOpenCloud

ScriptContext:EnableCoverage (instance :[Instance](/docs/reference/engine/datatypes/Instance) ) : ()

Parameters

|

instance :[Instance](/docs/reference/engine/datatypes/Instance)

 |

Returns

()

Provide feedback

---

GetCoverageStats

Capabilities: PluginOrOpenCloud

ScriptContext:GetCoverageStats () :[{any}](/docs/luau/tables#arrays)

Returns

[{any}](/docs/luau/tables#arrays)

Provide feedback

---

SetTimeout

Plugin Security

ScriptContext:SetTimeout (seconds :[number](/docs/luau/numbers) ) : ()

Parameters

|

seconds :[number](/docs/luau/numbers)

 |

Returns

()

Provide feedback

---

Events

Error

Capabilities: Logging

ScriptContext.Error (

message :[string](/docs/luau/strings) , stackTrace :[string](/docs/luau/strings) , script :[Instance](/docs/reference/engine/datatypes/Instance)

) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

message :[string](/docs/luau/strings)

 |
|

stackTrace :[string](/docs/luau/strings)

 |
|

script :[Instance](/docs/reference/engine/datatypes/Instance)

 |

Code Samples

ScriptContext.Error

```

local ScriptContext = game:GetService("ScriptContext")

local function onError(message, trace, script)

	print(script:GetFullName(), "errored!")

	print("Reason:", message)

	print("Trace:", trace)

end

ScriptContext.Error:Connect(onError)

-- Somewhere, in another script

error("Error occurred!")

```

Provide feedback

---

Jump to

▼

ScriptContext

[Summary](#summary)

[Methods](#summary-methods)

[Events](#summary-events)

[Methods](#methods)

[EnableCoverage()](#EnableCoverage)

[GetCoverageStats()](#GetCoverageStats)

[SetTimeout()](#SetTimeout)

[Events](#events)

[Error](#Error)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
