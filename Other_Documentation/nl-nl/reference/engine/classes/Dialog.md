<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Dialog -->

Dialog | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [Dialog](/docs/nl-nl/reference/engine/classes/Dialog)

Nederlands

Feedback

Engine-klasse

Dialog

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Dialog)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[BehaviorType](#BehaviorType) :[Enum.DialogBehaviorType](/docs/nl-nl/reference/engine/enums/DialogBehaviorType)

 |
| --- | --- |
|

[ConversationDistance](#ConversationDistance) :[number](/docs/nl-nl/luau/numbers)

 |
|

[GoodbyeChoiceActive](#GoodbyeChoiceActive) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[GoodbyeDialog](#GoodbyeDialog) :[string](/docs/nl-nl/luau/strings)

 |
|

[InitialPrompt](#InitialPrompt) :[string](/docs/nl-nl/luau/strings)

 |
|

[InUse](#InUse) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[Purpose](#Purpose) :[Enum.DialogPurpose](/docs/nl-nl/reference/engine/enums/DialogPurpose)

 |
|

[Tone](#Tone) :[Enum.DialogTone](/docs/nl-nl/reference/engine/enums/DialogTone)

 |
|

[TriggerDistance](#TriggerDistance) :[number](/docs/nl-nl/luau/numbers)

 |
|

[TriggerOffset](#TriggerOffset) :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |

Methoden

|

[GetCurrentPlayers](#GetCurrentPlayers) () : Instances

 |

Evenementen

|

[DialogChoiceSelected](#DialogChoiceSelected) (player :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) , dialogChoice :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

BehaviorType

Parallel lezen

Mogelijkheden: UI

Dialog.BehaviorType :[Enum.DialogBehaviorType](/docs/nl-nl/reference/engine/enums/DialogBehaviorType)

Codevoorbeelden

Gedragstype

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

singlePlayerDialog.InitialPrompt = "Slechts één persoon kan op hetzelfde moment met mij interageren."

singlePlayerDialog.Parent = singlePlayerPart

local multiplePlayersDialog = Instance.new("Dialog")

local multiplePlayersPart = Workspace.MultiplePlayersPart

multiplePlayersDialog.BehaviorType = Enum.DialogBehaviorType.MultiplePlayers

multiplePlayersDialog.InitialPrompt = "Elke hoeveelheid spelers kan op hetzelfde moment met mij interageren."

multiplePlayersDialog.Parent = multiplePlayersPart

```

Feedback geven

---

ConversationDistance

Parallel lezen

Mogelijkheden: UI

Dialog.ConversationDistance :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

GoodbyeChoiceActive

Parallel lezen

Mogelijkheden: UI

Dialog.GoodbyeChoiceActive :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

GoodbyeDialog

Parallel lezen

Mogelijkheden: UI

Dialog.GoodbyeDialog :[string](/docs/nl-nl/luau/strings)

Feedback geven

---

InitialPrompt

Parallel lezen

Mogelijkheden: UI

Dialog.InitialPrompt :[string](/docs/nl-nl/luau/strings)

Feedback geven

---

InUse

Parallel lezen

Mogelijkheden: UI

Dialog.InUse :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Purpose

Parallel lezen

Mogelijkheden: UI

Dialog.Purpose :[Enum.DialogPurpose](/docs/nl-nl/reference/engine/enums/DialogPurpose)

Feedback geven

---

Tone

Parallel lezen

Mogelijkheden: UI

Dialog.Tone :[Enum.DialogTone](/docs/nl-nl/reference/engine/enums/DialogTone)

Feedback geven

---

TriggerDistance

Parallel lezen

Mogelijkheden: UI

Dialog.TriggerDistance :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

TriggerOffset

Parallel lezen

Mogelijkheden: UI

Dialog.TriggerOffset :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

Methoden

GetCurrentPlayers

Mogelijkheden: UI

Dialog:GetCurrentPlayers () : Instances

Teruggaves

Instances

Codevoorbeelden

Dialog:GetCurrentPlayers

```

local dialog = script.Parent

local function onChoiceSelected(_player, _choice)

	local currentPlayers = dialog:GetCurrentPlayers()

	print("De huidige spelers in de dialoog:")

	for _, player in ipairs(currentPlayers) do

		print(player)

	end

end

dialog.DialogChoiceSelected:Connect(onChoiceSelected)

```

Feedback geven

---

Evenementen

DialogChoiceSelected

Mogelijkheden: UI

Dialog.DialogChoiceSelected (

player :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) , dialogChoice :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

player :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
|

dialogChoice :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Feedback geven

---

Ga naar

▼

Dialog

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

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

[Methoden](#methods)

[GetCurrentPlayers()](#GetCurrentPlayers)

[Evenementen](#events)

[DialogChoiceSelected](#DialogChoiceSelected)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
