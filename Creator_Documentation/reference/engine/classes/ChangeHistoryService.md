<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/ChangeHistoryService -->

ChangeHistoryService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/ChangeHistoryService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [ChangeHistoryService](/docs/en-us/reference/engine/classes/ChangeHistoryService)

English

Feedback

Engine Class

ChangeHistoryService

Not Creatable

Service

---

## Summary

Methods

|

[FinishRecording](#FinishRecording) (identifier :  [string](/docs/en-us/luau/strings) , operation :  [Enum.FinishRecordingOperation](/docs/en-us/reference/engine/enums/FinishRecordingOperation) , finalOptions :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ? ) : ()

 |
| --- | --- |
|

[GetCanRedo](#GetCanRedo) () :[Tuple](/docs/en-us/luau/tuples)

 |
|

[GetCanUndo](#GetCanUndo) () :[Tuple](/docs/en-us/luau/tuples)

 |
|

[IsRecordingInProgress](#IsRecordingInProgress) (identifier :  [string](/docs/en-us/luau/strings) ? ) :[boolean](/docs/en-us/luau/booleans)

 |
|

[Redo](#Redo) () : ()

 |
|

[ResetWaypoints](#ResetWaypoints) () : ()

 |
|

[SetEnabled](#SetEnabled) (state :  [boolean](/docs/en-us/luau/booleans) ) : ()

 |
|

[SetWaypoint](#SetWaypoint) (name :  [string](/docs/en-us/luau/strings) ) : ()

 |
|

[TryBeginRecording](#TryBeginRecording) (name :  [string](/docs/en-us/luau/strings) , displayName :  [string](/docs/en-us/luau/strings) ? ) :[string](/docs/en-us/luau/strings) ?

 |
|

[Undo](#Undo) () : ()

 |

Events

|

[OnRecordingFinished](#OnRecordingFinished) (name :  [string](/docs/en-us/luau/strings) , displayName :  [string](/docs/en-us/luau/strings) ? , identifier :  [string](/docs/en-us/luau/strings) ? , operation :  [Enum.FinishRecordingOperation](/docs/en-us/reference/engine/enums/FinishRecordingOperation) , finalOptions :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ? ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[OnRecordingStarted](#OnRecordingStarted) (name :  [string](/docs/en-us/luau/strings) , displayName :  [string](/docs/en-us/luau/strings) ? ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[OnRedo](#OnRedo) (waypoint :  [string](/docs/en-us/luau/strings) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[OnUndo](#OnUndo) (waypoint :  [string](/docs/en-us/luau/strings) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Methods

FinishRecording

Plugin Security

ChangeHistoryService:FinishRecording (

identifier :[string](/docs/en-us/luau/strings) , operation :[Enum.FinishRecordingOperation](/docs/en-us/reference/engine/enums/FinishRecordingOperation) , finalOptions :[Dictionary](/docs/en-us/luau/tables#dictionaries) ?

) : ()

Parameters

|

identifier :[string](/docs/en-us/luau/strings)

 |
|

operation :[Enum.FinishRecordingOperation](/docs/en-us/reference/engine/enums/FinishRecordingOperation)

 |
|

finalOptions :[Dictionary](/docs/en-us/luau/tables#dictionaries) ?

 |

Returns

()

Code Samples

ChangeHistoryService:TryBeginRecording

```

local ChangeHistoryService = game:GetService("ChangeHistoryService")

local Selection = game:GetService("Selection")

local toolbar = plugin:CreateToolbar("Example Plugin")

local button = toolbar:CreateButton("Neon it up", "", "")

button.Click:Connect(function()

	local parts = {}

	for _, part in pairs(Selection:Get()) do

		if part:IsA("BasePart") then

			parts[#parts + 1] = part

		end

	end

	if #parts < 1 then

		-- Nothing to do.

		return

	end

	local recording = ChangeHistoryService:TryBeginRecording("Set selection to neon")

	if not recording then

		-- Handle error here. This indicates that your plugin began a previous

		-- recording and never completed it. You may only have one recording

		-- per plugin active at a time.

		return

	end

	for _, part in pairs(parts) do

		part.Material = Enum.Material.Neon

	end

	ChangeHistoryService:FinishRecording(recording, Enum.FinishRecordingOperation.Commit)

end)

```

Provide feedback

---

GetCanRedo

Plugin Security

ChangeHistoryService:GetCanRedo () :[Tuple](/docs/en-us/luau/tuples)

Returns

[Tuple](/docs/en-us/luau/tuples)

Provide feedback

---

GetCanUndo

Plugin Security

ChangeHistoryService:GetCanUndo () :[Tuple](/docs/en-us/luau/tuples)

Returns

[Tuple](/docs/en-us/luau/tuples)

Provide feedback

---

IsRecordingInProgress

Plugin Security

ChangeHistoryService:IsRecordingInProgress (identifier :[string](/docs/en-us/luau/strings) ? ) :[boolean](/docs/en-us/luau/booleans)

Parameters

|

identifier :[string](/docs/en-us/luau/strings) ?

 |

Returns

[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

Redo

Plugin Security

ChangeHistoryService:Redo () : ()

Returns

()

Provide feedback

---

ResetWaypoints

Plugin Security

ChangeHistoryService:ResetWaypoints () : ()

Returns

()

Provide feedback

---

SetEnabled

Plugin Security

ChangeHistoryService:SetEnabled (state :[boolean](/docs/en-us/luau/booleans) ) : ()

Parameters

|

state :[boolean](/docs/en-us/luau/booleans)

 |

Returns

()

Provide feedback

---

SetWaypoint

Plugin Security

ChangeHistoryService:SetWaypoint (name :[string](/docs/en-us/luau/strings) ) : ()

Parameters

|

name :[string](/docs/en-us/luau/strings)

 |

Returns

()

Code Samples

ChangeHistoryService:SetWaypoint

```

local ChangeHistoryService = game:GetService("ChangeHistoryService")

local Selection = game:GetService("Selection")

local toolbar = plugin:CreateToolbar("Example Plugin")

local button = toolbar:CreateButton("Neon it up", "", "")

button.Click:Connect(function()

	local parts = {}

	for _, part in pairs(Selection:Get()) do

		if part:IsA("BasePart") then

			parts[#parts + 1] = part

		end

	end

	if #parts > 0 then

		-- Calling SetWaypoint before the work will not cause any issues, however

		-- it is redundant, only the call AFTER the work is needed.

		--ChangeHistoryService:SetWaypoint("Setting selection to neon")

		for _, part in pairs(parts) do

			part.Material = Enum.Material.Neon

		end

		-- Call SetWaypoint AFTER completing the work

		ChangeHistoryService:SetWaypoint("Set selection to neon")

	else

		-- Nothing to do. You do not need to call SetWaypoint in the case where

		-- the action did not end up making any changes to the experience.

	end

end)

```

Provide feedback

---

TryBeginRecording

Plugin Security

ChangeHistoryService:TryBeginRecording (

name :[string](/docs/en-us/luau/strings) , displayName :[string](/docs/en-us/luau/strings) ?

) :[string](/docs/en-us/luau/strings) ?

Parameters

|

name :[string](/docs/en-us/luau/strings)

 |
|

displayName :[string](/docs/en-us/luau/strings) ?

 |

Returns

[string](/docs/en-us/luau/strings) ?

Code Samples

ChangeHistoryService:TryBeginRecording

```

local ChangeHistoryService = game:GetService("ChangeHistoryService")

local Selection = game:GetService("Selection")

local toolbar = plugin:CreateToolbar("Example Plugin")

local button = toolbar:CreateButton("Neon it up", "", "")

button.Click:Connect(function()

	local parts = {}

	for _, part in pairs(Selection:Get()) do

		if part:IsA("BasePart") then

			parts[#parts + 1] = part

		end

	end

	if #parts < 1 then

		-- Nothing to do.

		return

	end

	local recording = ChangeHistoryService:TryBeginRecording("Set selection to neon")

	if not recording then

		-- Handle error here. This indicates that your plugin began a previous

		-- recording and never completed it. You may only have one recording

		-- per plugin active at a time.

		return

	end

	for _, part in pairs(parts) do

		part.Material = Enum.Material.Neon

	end

	ChangeHistoryService:FinishRecording(recording, Enum.FinishRecordingOperation.Commit)

end)

```

Provide feedback

---

Undo

Plugin Security

ChangeHistoryService:Undo () : ()

Returns

()

Provide feedback

---

Events

OnRecordingFinished

Plugin Security

ChangeHistoryService.OnRecordingFinished (

name :[string](/docs/en-us/luau/strings) , displayName :[string](/docs/en-us/luau/strings) ? , identifier :[string](/docs/en-us/luau/strings) ? , operation :[Enum.FinishRecordingOperation](/docs/en-us/reference/engine/enums/FinishRecordingOperation) , finalOptions :[Dictionary](/docs/en-us/luau/tables#dictionaries) ?

) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

name :[string](/docs/en-us/luau/strings)

 |
|

displayName :[string](/docs/en-us/luau/strings) ?

 |
|

identifier :[string](/docs/en-us/luau/strings) ?

 |
|

operation :[Enum.FinishRecordingOperation](/docs/en-us/reference/engine/enums/FinishRecordingOperation)

 |
|

finalOptions :[Dictionary](/docs/en-us/luau/tables#dictionaries) ?

 |

Provide feedback

---

OnRecordingStarted

Plugin Security

ChangeHistoryService.OnRecordingStarted (

name :[string](/docs/en-us/luau/strings) , displayName :[string](/docs/en-us/luau/strings) ?

) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

name :[string](/docs/en-us/luau/strings)

 |
|

displayName :[string](/docs/en-us/luau/strings) ?

 |

Provide feedback

---

OnRedo

Plugin Security

ChangeHistoryService.OnRedo (waypoint :[string](/docs/en-us/luau/strings) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

waypoint :[string](/docs/en-us/luau/strings)

 |

Provide feedback

---

OnUndo

Plugin Security

ChangeHistoryService.OnUndo (waypoint :[string](/docs/en-us/luau/strings) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

waypoint :[string](/docs/en-us/luau/strings)

 |

Provide feedback

---

Jump to

▼

ChangeHistoryService

[Summary](#summary)

[Methods](#summary-methods)

[Events](#summary-events)

[Methods](#methods)

[FinishRecording()](#FinishRecording)

[GetCanRedo()](#GetCanRedo)

[GetCanUndo()](#GetCanUndo)

[IsRecordingInProgress()](#IsRecordingInProgress)

[Redo()](#Redo)

[ResetWaypoints()](#ResetWaypoints)

[SetEnabled()](#SetEnabled)

[SetWaypoint()](#SetWaypoint)

[TryBeginRecording()](#TryBeginRecording)

[Undo()](#Undo)

[Events](#events)

[OnRecordingFinished](#OnRecordingFinished)

[OnRecordingStarted](#OnRecordingStarted)

[OnRedo](#OnRedo)

[OnUndo](#OnUndo)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
