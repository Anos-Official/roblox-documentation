<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/AudioDeviceInput -->

AudioDeviceInput | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [AudioDeviceInput](/docs/nl-nl/reference/engine/classes/AudioDeviceInput)

Nederlands

Feedback

Engine-klasse

AudioDeviceInput

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/AudioDeviceInput)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[AccessType](#AccessType) :[Enum.AccessModifierType](/docs/nl-nl/reference/engine/enums/AccessModifierType)

 |
| --- | --- |
|

[Active](#Active) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[IsReady](#IsReady) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[Muted](#Muted) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[Player](#Player) :[Player](/docs/nl-nl/reference/engine/classes/Player)

 |
|

[Volume](#Volume) :[number](/docs/nl-nl/luau/numbers)

 |

Methoden

|

[GetConnectedWires](#GetConnectedWires) (pin :  [string](/docs/nl-nl/luau/strings) ) : {[Wire](/docs/nl-nl/reference/engine/classes/Wire) }

 |
|

[GetInputPins](#GetInputPins) () :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[GetOutputPins](#GetOutputPins) () :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[GetUserIdAccessList](#GetUserIdAccessList) () :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[SetUserIdAccessList](#SetUserIdAccessList) (userIds :  [{any}](/docs/nl-nl/luau/tables#arrays) ) : ()

 |

Evenementen

|

[WiringChanged](#WiringChanged) (connected :  [boolean](/docs/nl-nl/luau/booleans) , pin :  [string](/docs/nl-nl/luau/strings) , wire :  [Wire](/docs/nl-nl/reference/engine/classes/Wire) , instance :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

AccessType

Parallel lezen

Mogelijkheden: Audio, Input

AudioDeviceInput.AccessType :[Enum.AccessModifierType](/docs/nl-nl/reference/engine/enums/AccessModifierType)

Feedback geven

---

Active

Roblox-scriptbeveiliging

Parallel lezen

Mogelijkheden: Audio, Input

AudioDeviceInput.Active :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

IsReady

Alleen-lezen

Niet gerepliceerd

Roblox-scriptbeveiliging

Parallel lezen

Mogelijkheden: Audio, Input

AudioDeviceInput.IsReady :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Muted

Parallel lezen

Mogelijkheden: Audio, Input

AudioDeviceInput.Muted :[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

Druk-om-te-praten

```

local players = game:GetService("Players")

local userInput = game:GetService("UserInputService")

local audioIn: AudioDeviceInput = players.LocalPlayer:WaitForChild("AudioDeviceInput")

audioIn.Muted = true

local pushToTalkKey = Enum.KeyCode.V

userInput.InputBegan:Connect(function(input: InputObject)

	-- Als de toets is ingedrukt

	if input.KeyCode == pushToTalkKey then

		audioIn.Muted = false

	end

end)

userInput.InputEnded:Connect(function(input: InputObject)

	-- Als de toets is losgelaten

	if input.KeyCode == pushToTalkKey then

		audioIn.Muted = true

	end

end)

```

Feedback geven

---

Player

Parallel lezen

Mogelijkheden: Audio, Input, Players

AudioDeviceInput.Player :[Player](/docs/nl-nl/reference/engine/classes/Player)

Feedback geven

---

Volume

Parallel lezen

Mogelijkheden: Audio, Input

AudioDeviceInput.Volume :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Methoden

GetConnectedWires

Mogelijkheden: Audio, Input

AudioDeviceInput:GetConnectedWires (pin :[string](/docs/nl-nl/luau/strings) ) : {[Wire](/docs/nl-nl/reference/engine/classes/Wire) }

Parameters

|

pin :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

{[Wire](/docs/nl-nl/reference/engine/classes/Wire) }

Feedback geven

---

GetInputPins

Mogelijkheden: Audio, Input

AudioDeviceInput:GetInputPins () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

GetOutputPins

Mogelijkheden: Audio, Input

AudioDeviceInput:GetOutputPins () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

GetUserIdAccessList

Mogelijkheden: Audio, Input

AudioDeviceInput:GetUserIdAccessList () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

SetUserIdAccessList

Mogelijkheden: Audio, Input

AudioDeviceInput:SetUserIdAccessList (userIds :[{any}](/docs/nl-nl/luau/tables#arrays) ) : ()

Parameters

|

userIds :[{any}](/docs/nl-nl/luau/tables#arrays)

 |

Teruggaves

()

Feedback geven

---

Evenementen

WiringChanged

Mogelijkheden: Audio, Input

AudioDeviceInput.WiringChanged (

connected :[boolean](/docs/nl-nl/luau/booleans) , pin :[string](/docs/nl-nl/luau/strings) , wire :[Wire](/docs/nl-nl/reference/engine/classes/Wire) , instance :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

connected :[boolean](/docs/nl-nl/luau/booleans)

 |
|

pin :[string](/docs/nl-nl/luau/strings)

 |
|

wire :[Wire](/docs/nl-nl/reference/engine/classes/Wire)

 |
|

instance :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Feedback geven

---

Ga naar

▼

AudioDeviceInput

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[AccessType](#AccessType)

[Active](#Active)

[IsReady](#IsReady)

[Muted](#Muted)

[Player](#Player)

[Volume](#Volume)

[Methoden](#methods)

[GetConnectedWires()](#GetConnectedWires)

[GetInputPins()](#GetInputPins)

[GetOutputPins()](#GetOutputPins)

[GetUserIdAccessList()](#GetUserIdAccessList)

[SetUserIdAccessList()](#SetUserIdAccessList)

[Evenementen](#events)

[WiringChanged](#WiringChanged)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
