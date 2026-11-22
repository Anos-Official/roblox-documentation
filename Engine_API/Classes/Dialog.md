<!-- Source: https://create.roblox.com/docs/reference/engine/classes/Dialog -->

Dialog | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Dialog.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [Dialog](/docs/reference/engine/classes/Dialog)

English

Feedback

Engine Class

Dialog

---

## Summary

Properties

|

[BehaviorType](#BehaviorType) :[Enum.DialogBehaviorType](/docs/reference/engine/enums/DialogBehaviorType)

 |
| --- | --- |
|

[ConversationDistance](#ConversationDistance) :[number](/docs/luau/numbers)

 |
|

[GoodbyeChoiceActive](#GoodbyeChoiceActive) :[boolean](/docs/luau/booleans)

 |
|

[GoodbyeDialog](#GoodbyeDialog) :[string](/docs/luau/strings)

 |
|

[InitialPrompt](#InitialPrompt) :[string](/docs/luau/strings)

 |
|

[InUse](#InUse) :[boolean](/docs/luau/booleans)

 |
|

[Purpose](#Purpose) :[Enum.DialogPurpose](/docs/reference/engine/enums/DialogPurpose)

 |
|

[Tone](#Tone) :[Enum.DialogTone](/docs/reference/engine/enums/DialogTone)

 |
|

[TriggerDistance](#TriggerDistance) :[number](/docs/luau/numbers)

 |
|

[TriggerOffset](#TriggerOffset) :[Vector3](/docs/reference/engine/datatypes/Vector3)

 |

Methods

|

[GetCurrentPlayers](#GetCurrentPlayers) () : Instances

 |

Events

|

[DialogChoiceSelected](#DialogChoiceSelected) (player :  [Instance](/docs/reference/engine/datatypes/Instance) , dialogChoice :  [Instance](/docs/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Properties

BehaviorType

Read Parallel

Capabilities: UI

Dialog.BehaviorType :[Enum.DialogBehaviorType](/docs/reference/engine/enums/DialogBehaviorType)

Code Samples

Behavior Type

```

local Workspace = game:GetService("Workspace")

local singlePlayerPartSetup = Instance.new("Part")

singlePlayerPartSetup.Name = "SinglePlayerPart"

singlePlayerPartSetup.Parent = Workspace

local multiplePlayersPartSetup = Instance.new("Part")

multiplePlayersPartSetup.Name = "MultiplePlayersPart"

multiplePlayersPartSetup.Parent = Workspace

local singlePlayerDialog = Instance.new("Dialog")

local singlePlayerPart = Workspace.SinglePlayerPart

singlePlayerDialog.BehaviorType = Enum.DialogBehaviorType.SinglePlayer

singlePlayerDialog.InitialPrompt = "Only one person can interact with me at once."

singlePlayerDialog.Parent = singlePlayerPart

local multiplePlayersDialog = Instance.new("Dialog")

local multiplePlayersPart = Workspace.MultiplePlayersPart

multiplePlayersDialog.BehaviorType = Enum.DialogBehaviorType.MultiplePlayers

multiplePlayersDialog.InitialPrompt = "Any number of players can interact with me at once."

multiplePlayersDialog.Parent = multiplePlayersPart

```

Provide feedback

---

ConversationDistance

Read Parallel

Capabilities: UI

Dialog.ConversationDistance :[number](/docs/luau/numbers)

Provide feedback

---

GoodbyeChoiceActive

Read Parallel

Capabilities: UI

Dialog.GoodbyeChoiceActive :[boolean](/docs/luau/booleans)

Provide feedback

---

GoodbyeDialog

Read Parallel

Capabilities: UI

Dialog.GoodbyeDialog :[string](/docs/luau/strings)

Provide feedback

---

InitialPrompt

Read Parallel

Capabilities: UI

Dialog.InitialPrompt :[string](/docs/luau/strings)

Provide feedback

---

InUse

Read Parallel

Capabilities: UI

Dialog.InUse :[boolean](/docs/luau/booleans)

Provide feedback

---

Purpose

Read Parallel

Capabilities: UI

Dialog.Purpose :[Enum.DialogPurpose](/docs/reference/engine/enums/DialogPurpose)

Provide feedback

---

Tone

Read Parallel

Capabilities: UI

Dialog.Tone :[Enum.DialogTone](/docs/reference/engine/enums/DialogTone)

Provide feedback

---

TriggerDistance

Read Parallel

Capabilities: UI

Dialog.TriggerDistance :[number](/docs/luau/numbers)

Provide feedback

---

TriggerOffset

Read Parallel

Capabilities: UI

Dialog.TriggerOffset :[Vector3](/docs/reference/engine/datatypes/Vector3)

Provide feedback

---

Methods

GetCurrentPlayers

Capabilities: UI

Dialog:GetCurrentPlayers () : Instances

Returns

Instances

Code Samples

Dialog:GetCurrentPlayers

```

local dialog = script.Parent

local function onChoiceSelected(_player, _choice)

	local currentPlayers = dialog:GetCurrentPlayers()

	print("The current players in the dialog:")

	for _, player in ipairs(currentPlayers) do

		print(player)

	end

end

dialog.DialogChoiceSelected:Connect(onChoiceSelected)

```

Provide feedback

---

Events

DialogChoiceSelected

Capabilities: UI

Dialog.DialogChoiceSelected (

player :[Instance](/docs/reference/engine/datatypes/Instance) , dialogChoice :[Instance](/docs/reference/engine/datatypes/Instance)

) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

player :[Instance](/docs/reference/engine/datatypes/Instance)

 |
|

dialogChoice :[Instance](/docs/reference/engine/datatypes/Instance)

 |

Provide feedback

---

Jump to

▼

Dialog

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[BehaviorType](#BehaviorType)

[ConversationDistance](#ConversationDistance)

[GoodbyeChoiceActive](#GoodbyeChoiceActive)

[GoodbyeDialog](#GoodbyeDialog)

[InitialPrompt](#InitialPrompt)

[InUse](#InUse)

[Purpose](#Purpose)

[Tone](#Tone)

[TriggerDistance](#TriggerDistance)

[TriggerOffset](#TriggerOffset)

[Methods](#methods)

[GetCurrentPlayers()](#GetCurrentPlayers)

[Events](#events)

[DialogChoiceSelected](#DialogChoiceSelected)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
