<!-- Source: https://create.roblox.com/docs/reference/engine/classes/PVInstance -->

PVInstance | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/PVInstance.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [PVInstance](/docs/reference/engine/classes/PVInstance)

English

Feedback

Engine Class

PVInstance

Not Creatable

Not Browsable

---

## Summary

Properties

|

[Origin](#Origin) :[CFrame](/docs/reference/engine/datatypes/CFrame)

 |
| --- | --- |
|

[Pivot Offset](#Pivot-Offset) :[CFrame](/docs/reference/engine/datatypes/CFrame)

 |

Methods

|

[GetPivot](#GetPivot) () :[CFrame](/docs/reference/engine/datatypes/CFrame)

 |
|

[PivotTo](#PivotTo) (targetCFrame :  [CFrame](/docs/reference/engine/datatypes/CFrame) ) : ()

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Inherited by

[Camera](/docs/reference/engine/classes/Camera) , [BasePart](/docs/reference/engine/classes/BasePart) , [Model](/docs/reference/engine/classes/Model)

---

API Reference

Properties

Origin

Not Replicated

Not Scriptable

Read Parallel

PVInstance.Origin :[CFrame](/docs/reference/engine/datatypes/CFrame)

Provide feedback

---

Pivot Offset

Not Replicated

Not Scriptable

Read Parallel

PVInstance.Pivot Offset :[CFrame](/docs/reference/engine/datatypes/CFrame)

Provide feedback

---

Methods

GetPivot

Write Parallel

Simulation Access

PVInstance:GetPivot () :[CFrame](/docs/reference/engine/datatypes/CFrame)

Returns

[CFrame](/docs/reference/engine/datatypes/CFrame)

Code Samples

Simple Character Teleportation

```

-- This code should be placed in a LocalScript under StarterPlayerScripts

local Players = game:GetService("Players")

local ContextActionService = game:GetService("ContextActionService")

local player = Players.LocalPlayer

local function doTeleport(_actionName, inputState, _inputObject)

	local character = player.Character

	if character and character.Parent and inputState == Enum.UserInputState.Begin then

		-- Move the character 10 studs forwards in the direction they're facing

		local currentPivot = character:GetPivot()

		character:PivotTo(currentPivot * CFrame.new(0, 0, -10))

	end

end

ContextActionService:BindAction("Teleport", doTeleport, true, Enum.KeyCode.F)

```

Provide feedback

---

PivotTo

Simulation Access

PVInstance:PivotTo (targetCFrame :[CFrame](/docs/reference/engine/datatypes/CFrame) ) : ()

Parameters

|

targetCFrame :[CFrame](/docs/reference/engine/datatypes/CFrame)

 |

Returns

()

Code Samples

Simple Character Teleportation

```

-- This code should be placed in a LocalScript under StarterPlayerScripts

local Players = game:GetService("Players")

local ContextActionService = game:GetService("ContextActionService")

local player = Players.LocalPlayer

local function doTeleport(_actionName, inputState, _inputObject)

	local character = player.Character

	if character and character.Parent and inputState == Enum.UserInputState.Begin then

		-- Move the character 10 studs forwards in the direction they're facing

		local currentPivot = character:GetPivot()

		character:PivotTo(currentPivot * CFrame.new(0, 0, -10))

	end

end

ContextActionService:BindAction("Teleport", doTeleport, true, Enum.KeyCode.F)

```

Provide feedback

---

Jump to

▼

PVInstance

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[Origin](#Origin)

[Pivot Offset](#Pivot-Offset)

[Methods](#methods)

[GetPivot()](#GetPivot)

[PivotTo()](#PivotTo)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
