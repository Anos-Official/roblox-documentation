<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/ScriptDebuggerService -->

ScriptDebuggerService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [ScriptDebuggerService](/docs/nl-nl/reference/engine/classes/ScriptDebuggerService)

Nederlands

Feedback

Engine-klasse

ScriptDebuggerService

Niet maakbaar

Service

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/ScriptDebuggerService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[AddBreakpoint](#AddBreakpoint) (scriptInstance :  [LuaSourceContainer](/docs/nl-nl/reference/engine/classes/LuaSourceContainer) , breakpoint :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ScriptBreakpointResult

 |
| --- | --- |
|

[ClearBreakpoints](#ClearBreakpoints) () : ()

 |
|

[Evaluate](#Evaluate) (expression :  [string](/docs/nl-nl/luau/strings) , frameId :  [number](/docs/nl-nl/luau/numbers) ? ) : ScriptEvaluateResult

 |
|

[GetRootVariables](#GetRootVariables) (frameId :  [number](/docs/nl-nl/luau/numbers) ) : { ScriptVariable }

 |
|

[GetStackTrace](#GetStackTrace) (threadId :  [number](/docs/nl-nl/luau/numbers) , startFrame :  [number](/docs/nl-nl/luau/numbers) ? ) : DebugStackTraceResult

 |
|

[GetThreads](#GetThreads) () : { ScriptDebugThread }

 |
|

[GetVariables](#GetVariables) (variablesReference :  [number](/docs/nl-nl/luau/numbers) ) : { ScriptVariable }

 |
|

[Pause](#Pause) () : ()

 |
|

[RemoveBreakpoint](#RemoveBreakpoint) (scriptInstance :  [LuaSourceContainer](/docs/nl-nl/reference/engine/classes/LuaSourceContainer) , line :  [number](/docs/nl-nl/luau/numbers) ) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[SetExceptionBreakMode](#SetExceptionBreakMode) (breakMode :  [Enum.DebugBreakModeType](/docs/nl-nl/reference/engine/enums/DebugBreakModeType) ) : ()

 |

Evenementen

|

[Resumed](#Resumed) (threadIds :  [{any}](/docs/nl-nl/luau/tables#arrays) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Callbacks

|

[OnStopped](#OnStopped) (stopped :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ScriptResumeAction

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Methoden

AddBreakpoint

Plugin-beveiliging

ScriptDebuggerService:AddBreakpoint (

scriptInstance :[LuaSourceContainer](/docs/nl-nl/reference/engine/classes/LuaSourceContainer) , breakpoint :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

) : ScriptBreakpointResult

Parameters

|

scriptInstance :[LuaSourceContainer](/docs/nl-nl/reference/engine/classes/LuaSourceContainer)

 |
|

breakpoint :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |

Teruggaves

ScriptBreakpointResult

Feedback geven

---

ClearBreakpoints

Plugin-beveiliging

ScriptDebuggerService:ClearBreakpoints () : ()

Teruggaves

()

Feedback geven

---

Evaluate

Plugin-beveiliging

ScriptDebuggerService:Evaluate (

expression :[string](/docs/nl-nl/luau/strings) , frameId :[number](/docs/nl-nl/luau/numbers) ?

) : ScriptEvaluateResult

Parameters

|

expression :[string](/docs/nl-nl/luau/strings)

 |
|

frameId :[number](/docs/nl-nl/luau/numbers) ?

Standaardwaarde: nil |

Teruggaves

ScriptEvaluateResult

Feedback geven

---

GetRootVariables

Plugin-beveiliging

ScriptDebuggerService:GetRootVariables (frameId :[number](/docs/nl-nl/luau/numbers) ) : { ScriptVariable }

Parameters

|

frameId :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

{ ScriptVariable }

Feedback geven

---

GetStackTrace

Plugin-beveiliging

ScriptDebuggerService:GetStackTrace (

threadId :[number](/docs/nl-nl/luau/numbers) , startFrame :[number](/docs/nl-nl/luau/numbers) ?

) : DebugStackTraceResult

Parameters

|

threadId :[number](/docs/nl-nl/luau/numbers)

 |
|

startFrame :[number](/docs/nl-nl/luau/numbers) ?

Standaardwaarde: nil |

Teruggaves

DebugStackTraceResult

Feedback geven

---

GetThreads

Plugin-beveiliging

ScriptDebuggerService:GetThreads () : { ScriptDebugThread }

Teruggaves

{ ScriptDebugThread }

Feedback geven

---

GetVariables

Plugin-beveiliging

ScriptDebuggerService:GetVariables (variablesReference :[number](/docs/nl-nl/luau/numbers) ) : { ScriptVariable }

Parameters

|

variablesReference :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

{ ScriptVariable }

Feedback geven

---

Pause

Plugin-beveiliging

ScriptDebuggerService:Pause () : ()

Teruggaves

()

Feedback geven

---

RemoveBreakpoint

Plugin-beveiliging

ScriptDebuggerService:RemoveBreakpoint (

scriptInstance :[LuaSourceContainer](/docs/nl-nl/reference/engine/classes/LuaSourceContainer) , line :[number](/docs/nl-nl/luau/numbers)

) :[boolean](/docs/nl-nl/luau/booleans)

Parameters

|

scriptInstance :[LuaSourceContainer](/docs/nl-nl/reference/engine/classes/LuaSourceContainer)

 |
|

line :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

SetExceptionBreakMode

Plugin-beveiliging

ScriptDebuggerService:SetExceptionBreakMode (breakMode :[Enum.DebugBreakModeType](/docs/nl-nl/reference/engine/enums/DebugBreakModeType) ) : ()

Parameters

|

breakMode :[Enum.DebugBreakModeType](/docs/nl-nl/reference/engine/enums/DebugBreakModeType)

 |

Teruggaves

()

Feedback geven

---

Evenementen

Resumed

Plugin-beveiliging

ScriptDebuggerService.Resumed (threadIds :[{any}](/docs/nl-nl/luau/tables#arrays) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

threadIds :[{any}](/docs/nl-nl/luau/tables#arrays)

 |

Feedback geven

---

Callbacks

OnStopped

Plugin-beveiliging

ScriptDebuggerService.OnStopped (stopped :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ScriptResumeAction

Parameters

|

stopped :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |

Teruggaves

ScriptResumeAction

Feedback geven

---

Ga naar

▼

ScriptDebuggerService

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Callbacks](#summary-callbacks)

[Methoden](#methods)

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

[Evenementen](#events)

[Resumed](#Resumed)

[Callbacks](#callbacks)

[OnStopped()](#OnStopped)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
