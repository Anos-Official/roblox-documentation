<!-- Source: https://create.roblox.com/docs/reference/engine/classes/ScriptDebuggerService -->

ScriptDebuggerService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/ScriptDebuggerService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [ScriptDebuggerService](/docs/reference/engine/classes/ScriptDebuggerService)

English

Feedback

Engine Class

ScriptDebuggerService

Not Creatable

Service

Not Replicated

---

## Summary

Methods

|

[AddBreakpoint](#AddBreakpoint) (scriptInstance :  [LuaSourceContainer](/docs/reference/engine/classes/LuaSourceContainer) , breakpoint :  [Dictionary](/docs/luau/tables#dictionaries) ) : ScriptBreakpointResult

 |
| --- | --- |
|

[ClearBreakpoints](#ClearBreakpoints) () : ()

 |
|

[Evaluate](#Evaluate) (expression :  [string](/docs/luau/strings) , frameId :  [number](/docs/luau/numbers) ? ) : ScriptEvaluateResult

 |
|

[GetRootVariables](#GetRootVariables) (frameId :  [number](/docs/luau/numbers) ) : { ScriptVariable }

 |
|

[GetStackTrace](#GetStackTrace) (threadId :  [number](/docs/luau/numbers) , startFrame :  [number](/docs/luau/numbers) ? ) : DebugStackTraceResult

 |
|

[GetThreads](#GetThreads) () : { ScriptDebugThread }

 |
|

[GetVariables](#GetVariables) (variablesReference :  [number](/docs/luau/numbers) ) : { ScriptVariable }

 |
|

[Pause](#Pause) () : ()

 |
|

[RemoveBreakpoint](#RemoveBreakpoint) (scriptInstance :  [LuaSourceContainer](/docs/reference/engine/classes/LuaSourceContainer) , line :  [number](/docs/luau/numbers) ) :[boolean](/docs/luau/booleans)

 |
|

[SetExceptionBreakMode](#SetExceptionBreakMode) (breakMode :  [Enum.DebugBreakModeType](/docs/reference/engine/enums/DebugBreakModeType) ) : ()

 |

Events

|

[Resumed](#Resumed) (threadIds :  [{any}](/docs/luau/tables#arrays) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |

Callbacks

|

[OnStopped](#OnStopped) (stopped :  [Dictionary](/docs/luau/tables#dictionaries) ) : ScriptResumeAction

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Methods

AddBreakpoint

Plugin Security

ScriptDebuggerService:AddBreakpoint (

scriptInstance :[LuaSourceContainer](/docs/reference/engine/classes/LuaSourceContainer) , breakpoint :[Dictionary](/docs/luau/tables#dictionaries)

) : ScriptBreakpointResult

Parameters

|

scriptInstance :[LuaSourceContainer](/docs/reference/engine/classes/LuaSourceContainer)

 |
|

breakpoint :[Dictionary](/docs/luau/tables#dictionaries)

 |

Returns

ScriptBreakpointResult

Provide feedback

---

ClearBreakpoints

Plugin Security

ScriptDebuggerService:ClearBreakpoints () : ()

Returns

()

Provide feedback

---

Evaluate

Plugin Security

ScriptDebuggerService:Evaluate (

expression :[string](/docs/luau/strings) , frameId :[number](/docs/luau/numbers) ?

) : ScriptEvaluateResult

Parameters

|

expression :[string](/docs/luau/strings)

 |
|

frameId :[number](/docs/luau/numbers) ?

Default Value: nil |

Returns

ScriptEvaluateResult

Provide feedback

---

GetRootVariables

Plugin Security

ScriptDebuggerService:GetRootVariables (frameId :[number](/docs/luau/numbers) ) : { ScriptVariable }

Parameters

|

frameId :[number](/docs/luau/numbers)

 |

Returns

{ ScriptVariable }

Provide feedback

---

GetStackTrace

Plugin Security

ScriptDebuggerService:GetStackTrace (

threadId :[number](/docs/luau/numbers) , startFrame :[number](/docs/luau/numbers) ?

) : DebugStackTraceResult

Parameters

|

threadId :[number](/docs/luau/numbers)

 |
|

startFrame :[number](/docs/luau/numbers) ?

Default Value: nil |

Returns

DebugStackTraceResult

Provide feedback

---

GetThreads

Plugin Security

ScriptDebuggerService:GetThreads () : { ScriptDebugThread }

Returns

{ ScriptDebugThread }

Provide feedback

---

GetVariables

Plugin Security

ScriptDebuggerService:GetVariables (variablesReference :[number](/docs/luau/numbers) ) : { ScriptVariable }

Parameters

|

variablesReference :[number](/docs/luau/numbers)

 |

Returns

{ ScriptVariable }

Provide feedback

---

Pause

Plugin Security

ScriptDebuggerService:Pause () : ()

Returns

()

Provide feedback

---

RemoveBreakpoint

Plugin Security

ScriptDebuggerService:RemoveBreakpoint (

scriptInstance :[LuaSourceContainer](/docs/reference/engine/classes/LuaSourceContainer) , line :[number](/docs/luau/numbers)

) :[boolean](/docs/luau/booleans)

Parameters

|

scriptInstance :[LuaSourceContainer](/docs/reference/engine/classes/LuaSourceContainer)

 |
|

line :[number](/docs/luau/numbers)

 |

Returns

[boolean](/docs/luau/booleans)

Provide feedback

---

SetExceptionBreakMode

Plugin Security

ScriptDebuggerService:SetExceptionBreakMode (breakMode :[Enum.DebugBreakModeType](/docs/reference/engine/enums/DebugBreakModeType) ) : ()

Parameters

|

breakMode :[Enum.DebugBreakModeType](/docs/reference/engine/enums/DebugBreakModeType)

 |

Returns

()

Provide feedback

---

Events

Resumed

Plugin Security

ScriptDebuggerService.Resumed (threadIds :[{any}](/docs/luau/tables#arrays) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

threadIds :[{any}](/docs/luau/tables#arrays)

 |

Provide feedback

---

Callbacks

OnStopped

Plugin Security

ScriptDebuggerService.OnStopped (stopped :[Dictionary](/docs/luau/tables#dictionaries) ) : ScriptResumeAction

Parameters

|

stopped :[Dictionary](/docs/luau/tables#dictionaries)

 |

Returns

ScriptResumeAction

Provide feedback

---

Jump to

▼

ScriptDebuggerService

[Summary](#summary)

[Methods](#summary-methods)

[Events](#summary-events)

[Callbacks](#summary-callbacks)

[Methods](#methods)

[AddBreakpoint()](#AddBreakpoint)

[ClearBreakpoints()](#ClearBreakpoints)

[Evaluate()](#Evaluate)

[GetRootVariables()](#GetRootVariables)

[GetStackTrace()](#GetStackTrace)

[GetThreads()](#GetThreads)

[GetVariables()](#GetVariables)

[Pause()](#Pause)

[RemoveBreakpoint()](#RemoveBreakpoint)

[SetExceptionBreakMode()](#SetExceptionBreakMode)

[Events](#events)

[Resumed](#Resumed)

[Callbacks](#callbacks)

[OnStopped()](#OnStopped)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
