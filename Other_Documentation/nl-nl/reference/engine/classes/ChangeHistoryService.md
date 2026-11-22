<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/ChangeHistoryService -->

ChangeHistoryService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [ChangeHistoryService](/docs/nl-nl/reference/engine/classes/ChangeHistoryService)

Nederlands

Feedback

Engine-klasse

ChangeHistoryService

Niet maakbaar

Service

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/ChangeHistoryService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[FinishRecording](#FinishRecording) (identifier :  [string](/docs/nl-nl/luau/strings) , operation :  [Enum.FinishRecordingOperation](/docs/nl-nl/reference/engine/enums/FinishRecordingOperation) , finalOptions :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ? ) : ()

 |
| --- | --- |
|

[GetCanRedo](#GetCanRedo) () :[Tuple](/docs/nl-nl/luau/tuples)

 |
|

[GetCanUndo](#GetCanUndo) () :[Tuple](/docs/nl-nl/luau/tuples)

 |
|

[IsRecordingInProgress](#IsRecordingInProgress) (identifier :  [string](/docs/nl-nl/luau/strings) ? ) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[Redo](#Redo) () : ()

 |
|

[ResetWaypoints](#ResetWaypoints) () : ()

 |
|

[SetEnabled](#SetEnabled) (state :  [boolean](/docs/nl-nl/luau/booleans) ) : ()

 |
|

[SetWaypoint](#SetWaypoint) (name :  [string](/docs/nl-nl/luau/strings) ) : ()

 |
|

[TryBeginRecording](#TryBeginRecording) (name :  [string](/docs/nl-nl/luau/strings) , displayName :  [string](/docs/nl-nl/luau/strings) ? ) :[string](/docs/nl-nl/luau/strings) ?

 |
|

[Undo](#Undo) () : ()

 |

Evenementen

|

[OnRecordingFinished](#OnRecordingFinished) (name :  [string](/docs/nl-nl/luau/strings) , displayName :  [string](/docs/nl-nl/luau/strings) ? , identifier :  [string](/docs/nl-nl/luau/strings) ? , operation :  [Enum.FinishRecordingOperation](/docs/nl-nl/reference/engine/enums/FinishRecordingOperation) , finalOptions :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ? ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[OnRecordingStarted](#OnRecordingStarted) (name :  [string](/docs/nl-nl/luau/strings) , displayName :  [string](/docs/nl-nl/luau/strings) ? ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[OnRedo](#OnRedo) (waypoint :  [string](/docs/nl-nl/luau/strings) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[OnUndo](#OnUndo) (waypoint :  [string](/docs/nl-nl/luau/strings) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Methoden

FinishRecording

Plugin-beveiliging

ChangeHistoryService:FinishRecording (

identifier :[string](/docs/nl-nl/luau/strings) , operation :[Enum.FinishRecordingOperation](/docs/nl-nl/reference/engine/enums/FinishRecordingOperation) , finalOptions :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ?

) : ()

Parameters

|

identifier :[string](/docs/nl-nl/luau/strings)

 |
|

operation :[Enum.FinishRecordingOperation](/docs/nl-nl/reference/engine/enums/FinishRecordingOperation)

 |
|

finalOptions :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ?

 |

Teruggaves

()

Codevoorbeelden

ChangeHistoryService:TryBeginRecording

```

local ChangeHistoryService = game:GetService("ChangeHistoryService")

local Selection = game:GetService("Selection")

local toolbar = plugin:CreateToolbar("Voorbeeld Plugin")

local button = toolbar:CreateButton("Neon het op", "", "")

button.Click:Connect(function()

	local parts = {}

	for _, part in pairs(Selection:Get()) do

		if part:IsA("BasePart") then

			parts[#parts + 1] = part

		end

	end

	if #parts < 1 then

		-- Niets te doen.

		return

	end

	local recording = ChangeHistoryService:TryBeginRecording("Stel selectie in op neon")

	if not recording then

		-- Fout hier afhandelen. Dit geeft aan dat je plugin een eerdere

		-- opname is begonnen en deze nooit heeft voltooid. Je kunt slechts één opname

		-- per plugin tegelijk actief hebben.

		return

	end

	for _, part in pairs(parts) do

		part.Material = Enum.Material.Neon

	end

	ChangeHistoryService:FinishRecording(recording, Enum.FinishRecordingOperation.Commit)

end)

```

Feedback geven

---

GetCanRedo

Plugin-beveiliging

ChangeHistoryService:GetCanRedo () :[Tuple](/docs/nl-nl/luau/tuples)

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Feedback geven

---

GetCanUndo

Plugin-beveiliging

ChangeHistoryService:GetCanUndo () :[Tuple](/docs/nl-nl/luau/tuples)

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Feedback geven

---

IsRecordingInProgress

Plugin-beveiliging

ChangeHistoryService:IsRecordingInProgress (identifier :[string](/docs/nl-nl/luau/strings) ? ) :[boolean](/docs/nl-nl/luau/booleans)

Parameters

|

identifier :[string](/docs/nl-nl/luau/strings) ?

 |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Redo

Plugin-beveiliging

ChangeHistoryService:Redo () : ()

Teruggaves

()

Feedback geven

---

ResetWaypoints

Plugin-beveiliging

ChangeHistoryService:ResetWaypoints () : ()

Teruggaves

()

Feedback geven

---

SetEnabled

Plugin-beveiliging

ChangeHistoryService:SetEnabled (state :[boolean](/docs/nl-nl/luau/booleans) ) : ()

Parameters

|

state :[boolean](/docs/nl-nl/luau/booleans)

 |

Teruggaves

()

Feedback geven

---

SetWaypoint

Plugin-beveiliging

ChangeHistoryService:SetWaypoint (name :[string](/docs/nl-nl/luau/strings) ) : ()

Parameters

|

name :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

()

Codevoorbeelden

ChangeHistoryService:SetWaypoint

```

local ChangeHistoryService = game:GetService("ChangeHistoryService")

local Selection = game:GetService("Selection")

local toolbar = plugin:CreateToolbar("Voorbeeld Plugin")

local button = toolbar:CreateButton("Neon het omhoog", "", "")

button.Click:Connect(function()

	local parts = {}

	for _, part in pairs(Selection:Get()) do

		if part:IsA("BasePart") then

			parts[#parts + 1] = part

		end

	end

	if #parts > 0 then

		-- Het aanroepen van SetWaypoint voor het werk zal geen problemen veroorzaken, echter

		-- het is overbodig, alleen de aanroep NA het werk is nodig.

		--ChangeHistoryService:SetWaypoint("Selectie instellen op neon")

		for _, part in pairs(parts) do

			part.Material = Enum.Material.Neon

		end

		-- Roep SetWaypoint NA het voltooien van het werk aan

		ChangeHistoryService:SetWaypoint("Selectie ingesteld op neon")

	else

		-- Niets te doen. Je hoeft SetWaypoint niet aan te roepen in het geval dat

		-- de actie geen wijzigingen in de ervaring heeft aangebracht.

	end

end)

```

Feedback geven

---

TryBeginRecording

Plugin-beveiliging

ChangeHistoryService:TryBeginRecording (

name :[string](/docs/nl-nl/luau/strings) , displayName :[string](/docs/nl-nl/luau/strings) ?

) :[string](/docs/nl-nl/luau/strings) ?

Parameters

|

name :[string](/docs/nl-nl/luau/strings)

 |
|

displayName :[string](/docs/nl-nl/luau/strings) ?

 |

Teruggaves

[string](/docs/nl-nl/luau/strings) ?

Codevoorbeelden

ChangeHistoryService:TryBeginRecording

```

local ChangeHistoryService = game:GetService("ChangeHistoryService")

local Selection = game:GetService("Selection")

local toolbar = plugin:CreateToolbar("Voorbeeld Plugin")

local button = toolbar:CreateButton("Neon het op", "", "")

button.Click:Connect(function()

	local parts = {}

	for _, part in pairs(Selection:Get()) do

		if part:IsA("BasePart") then

			parts[#parts + 1] = part

		end

	end

	if #parts < 1 then

		-- Niets te doen.

		return

	end

	local recording = ChangeHistoryService:TryBeginRecording("Stel selectie in op neon")

	if not recording then

		-- Fout hier afhandelen. Dit geeft aan dat je plugin een eerdere

		-- opname is begonnen en deze nooit heeft voltooid. Je kunt slechts één opname

		-- per plugin tegelijk actief hebben.

		return

	end

	for _, part in pairs(parts) do

		part.Material = Enum.Material.Neon

	end

	ChangeHistoryService:FinishRecording(recording, Enum.FinishRecordingOperation.Commit)

end)

```

Feedback geven

---

Undo

Plugin-beveiliging

ChangeHistoryService:Undo () : ()

Teruggaves

()

Feedback geven

---

Evenementen

OnRecordingFinished

Plugin-beveiliging

ChangeHistoryService.OnRecordingFinished (

name :[string](/docs/nl-nl/luau/strings) , displayName :[string](/docs/nl-nl/luau/strings) ? , identifier :[string](/docs/nl-nl/luau/strings) ? , operation :[Enum.FinishRecordingOperation](/docs/nl-nl/reference/engine/enums/FinishRecordingOperation) , finalOptions :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ?

) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

name :[string](/docs/nl-nl/luau/strings)

 |
|

displayName :[string](/docs/nl-nl/luau/strings) ?

 |
|

identifier :[string](/docs/nl-nl/luau/strings) ?

 |
|

operation :[Enum.FinishRecordingOperation](/docs/nl-nl/reference/engine/enums/FinishRecordingOperation)

 |
|

finalOptions :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ?

 |

Feedback geven

---

OnRecordingStarted

Plugin-beveiliging

ChangeHistoryService.OnRecordingStarted (

name :[string](/docs/nl-nl/luau/strings) , displayName :[string](/docs/nl-nl/luau/strings) ?

) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

name :[string](/docs/nl-nl/luau/strings)

 |
|

displayName :[string](/docs/nl-nl/luau/strings) ?

 |

Feedback geven

---

OnRedo

Plugin-beveiliging

ChangeHistoryService.OnRedo (waypoint :[string](/docs/nl-nl/luau/strings) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

waypoint :[string](/docs/nl-nl/luau/strings)

 |

Feedback geven

---

OnUndo

Plugin-beveiliging

ChangeHistoryService.OnUndo (waypoint :[string](/docs/nl-nl/luau/strings) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

waypoint :[string](/docs/nl-nl/luau/strings)

 |

Feedback geven

---

Ga naar

▼

ChangeHistoryService

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Methoden](#methods)

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

[Evenementen](#events)

[OnRecordingFinished](#OnRecordingFinished)

[OnRecordingStarted](#OnRecordingStarted)

[OnRedo](#OnRedo)

[OnUndo](#OnUndo)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
