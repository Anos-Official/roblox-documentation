<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/AudioEmitter -->

AudioEmitter | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [AudioEmitter](/docs/nl-nl/reference/engine/classes/AudioEmitter)

Nederlands

Feedback

Engine-klasse

AudioEmitter

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/AudioEmitter)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[AcousticSimulationEnabled](#AcousticSimulationEnabled) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |
|

[AngleAttenuation](#AngleAttenuation) : BinaryString

 |
|

[AudioInteractionGroup](#AudioInteractionGroup) :[string](/docs/nl-nl/luau/strings)

 |
|

[DistanceAttenuation](#DistanceAttenuation) : BinaryString

 |
|

[DistanceAttenuationBounds](#DistanceAttenuationBounds) :[NumberRange](/docs/nl-nl/reference/engine/datatypes/NumberRange)

 |
|

[DistanceAttenuationMode](#DistanceAttenuationMode) :[Enum.DistanceAttenuationMode](/docs/nl-nl/reference/engine/enums/DistanceAttenuationMode)

 |
|

[PositionInstance](#PositionInstance) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
|

[PositionType](#PositionType) :[Enum.EmitterPositionType](/docs/nl-nl/reference/engine/enums/EmitterPositionType)

 |
|

[SimulationFidelity](#SimulationFidelity) :[Enum.AudioSimulationFidelity](/docs/nl-nl/reference/engine/enums/AudioSimulationFidelity)

Verouderd

 |

Methoden

|

[GetAngleAttenuation](#GetAngleAttenuation) () :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |
|

[GetAudibilityFor](#GetAudibilityFor) (listener :  [AudioListener](/docs/nl-nl/reference/engine/classes/AudioListener) ) :[number](/docs/nl-nl/luau/numbers)

 |
|

[GetConnectedWires](#GetConnectedWires) (pin :  [string](/docs/nl-nl/luau/strings) ) : {[Wire](/docs/nl-nl/reference/engine/classes/Wire) }

 |
|

[GetDistanceAttenuation](#GetDistanceAttenuation) () :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |
|

[GetInputPins](#GetInputPins) () :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[GetInteractingListeners](#GetInteractingListeners) () : {[AudioListener](/docs/nl-nl/reference/engine/classes/AudioListener) }

 |
|

[GetOutputPins](#GetOutputPins) () :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[SetAngleAttenuation](#SetAngleAttenuation) (curve :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

 |
|

[SetDistanceAttenuation](#SetDistanceAttenuation) (curve :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

 |

Evenementen

|

[WiringChanged](#WiringChanged) (connected :  [boolean](/docs/nl-nl/luau/booleans) , pin :  [string](/docs/nl-nl/luau/strings) , wire :  [Wire](/docs/nl-nl/reference/engine/classes/Wire) , instance :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Een asset op meerdere 3D-locaties tegelijk afspelen

```

local part1: BasePart = workspace.Speakers.Left

local part2: BasePart = workspace.Speakers.Right

local player: AudioPlayer = workspace.AudioPlayer

local leftEmitter = Instance.new("AudioEmitter")

local rightEmitter = Instance.new("AudioEmitter")

local toLeft = Instance.new("Wire")

local toRight = Instance.new("Wire")

leftEmitter.Parent = part1

rightEmitter.Parent = part2

toLeft.Parent = leftEmitter

toLeft.SourceInstance = player

toLeft.TargetInstance = leftEmitter

toRight.Parent = rightEmitter

toRight.SourceInstance = player

toRight.TargetInstance = rightEmitter

player:Play()

```

---

API-referentie

Eigenschappen

AcousticSimulationEnabled

Parallel lezen

Mogelijkheden: Audio

AudioEmitter.AcousticSimulationEnabled :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

AngleAttenuation

Roblox Security

Parallel lezen

Mogelijkheden: Audio

AudioEmitter.AngleAttenuation : BinaryString

Feedback geven

---

AudioInteractionGroup

Parallel lezen

Mogelijkheden: Audio

AudioEmitter.AudioInteractionGroup :[string](/docs/nl-nl/luau/strings)

Feedback geven

---

DistanceAttenuation

Roblox Security

Parallel lezen

Mogelijkheden: Audio

AudioEmitter.DistanceAttenuation : BinaryString

Feedback geven

---

DistanceAttenuationBounds

Parallel lezen

Mogelijkheden: Audio

AudioEmitter.DistanceAttenuationBounds :[NumberRange](/docs/nl-nl/reference/engine/datatypes/NumberRange)

Feedback geven

---

DistanceAttenuationMode

Parallel lezen

Mogelijkheden: Audio

AudioEmitter.DistanceAttenuationMode :[Enum.DistanceAttenuationMode](/docs/nl-nl/reference/engine/enums/DistanceAttenuationMode)

Feedback geven

---

PositionInstance

Parallel lezen

Mogelijkheden: Audio

AudioEmitter.PositionInstance :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Feedback geven

---

PositionType

Parallel lezen

Mogelijkheden: Audio

AudioEmitter.PositionType :[Enum.EmitterPositionType](/docs/nl-nl/reference/engine/enums/EmitterPositionType)

Feedback geven

---

SimulationFidelity

Verouderd

Details weergeven

---

Methoden

GetAngleAttenuation

Mogelijkheden: Audio

AudioEmitter:GetAngleAttenuation () :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Teruggaves

[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Feedback geven

---

GetAudibilityFor

Mogelijkheden: Audio

AudioEmitter:GetAudibilityFor (listener :[AudioListener](/docs/nl-nl/reference/engine/classes/AudioListener) ) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

listener :[AudioListener](/docs/nl-nl/reference/engine/classes/AudioListener)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

GetConnectedWires

Mogelijkheden: Audio

AudioEmitter:GetConnectedWires (pin :[string](/docs/nl-nl/luau/strings) ) : {[Wire](/docs/nl-nl/reference/engine/classes/Wire) }

Parameters

|

pin :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

{[Wire](/docs/nl-nl/reference/engine/classes/Wire) }

Feedback geven

---

GetDistanceAttenuation

Mogelijkheden: Audio

AudioEmitter:GetDistanceAttenuation () :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Teruggaves

[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Feedback geven

---

GetInputPins

Mogelijkheden: Audio

AudioEmitter:GetInputPins () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

GetInteractingListeners

Mogelijkheden: Audio

AudioEmitter:GetInteractingListeners () : {[AudioListener](/docs/nl-nl/reference/engine/classes/AudioListener) }

Teruggaves

{[AudioListener](/docs/nl-nl/reference/engine/classes/AudioListener) }

Feedback geven

---

GetOutputPins

Mogelijkheden: Audio

AudioEmitter:GetOutputPins () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

SetAngleAttenuation

Mogelijkheden: Audio

AudioEmitter:SetAngleAttenuation (curve :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

Parameters

|

curve :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |

Teruggaves

()

Feedback geven

---

SetDistanceAttenuation

Mogelijkheden: Audio

AudioEmitter:SetDistanceAttenuation (curve :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

Parameters

|

curve :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |

Teruggaves

()

Codevoorbeelden

Aangepaste Afstand Attenuatie

```

local Players = game:GetService("Players")

local emitterPart = Instance.new("Part")

emitterPart.Anchored = true

emitterPart.Position = Vector3.new(0, 0, 0)

emitterPart.Parent = workspace

local emitter: AudioEmitter = Instance.new("AudioEmitter")

emitter.Parent = emitterPart

local curve = {}

curve[10] = 1 -- Binnen een afstand van 10 studs, horen luisteraars deze emitter op volle volume

curve[100] = 0.4 -- Op een afstand van 100 studs, horen luisteraars deze emitter op 40% volume

curve[300] = 0 -- Op elke afstand verder dan 300 studs, kunnen luisteraars deze emitter niet horen

emitter:SetDistanceAttenuation(curve)

-- Repliceer de rolloff curve van de oude stemimplementatie

-- Standaard stem zonder de nieuwe audio API gebruikt kwadratische rolloff variërend van 7 tot 80 studs

local MIN_DISTANCE = 7

local MAX_DISTANCE = 80

local CURVE_STEP_SIZE = 2

local voiceCurve = {}

for i = MIN_DISTANCE, MAX_DISTANCE, CURVE_STEP_SIZE do

	voiceCurve[i] = ((i - MIN_DISTANCE) - (MAX_DISTANCE - MIN_DISTANCE)) ^ 2 / (MAX_DISTANCE - MIN_DISTANCE) ^ 2

end

voiceCurve[MAX_DISTANCE] = 0

local function setVoiceCurve(character)

	local voiceEmitter: AudioEmitter = character:WaitForChild("AudioEmitter")

	voiceEmitter:SetDistanceAttenuation(voiceCurve)

end

for _, player in Players:GetPlayers() do

	if player.Character then

		setVoiceCurve(player.Character)

	end

	player.CharacterAdded:Connect(setVoiceCurve)

end

```

Feedback geven

---

Evenementen

WiringChanged

Mogelijkheden: Audio

AudioEmitter.WiringChanged (

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

AudioEmitter

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[AcousticSimulationEnabled](#AcousticSimulationEnabled)

[AngleAttenuation](#AngleAttenuation)

[AudioInteractionGroup](#AudioInteractionGroup)

[DistanceAttenuation](#DistanceAttenuation)

[DistanceAttenuationBounds](#DistanceAttenuationBounds)

[DistanceAttenuationMode](#DistanceAttenuationMode)

[PositionInstance](#PositionInstance)

[PositionType](#PositionType)

[SimulationFidelity](#SimulationFidelity)

[Methoden](#methods)

[GetAngleAttenuation()](#GetAngleAttenuation)

[GetAudibilityFor()](#GetAudibilityFor)

[GetConnectedWires()](#GetConnectedWires)

[GetDistanceAttenuation()](#GetDistanceAttenuation)

[GetInputPins()](#GetInputPins)

[GetInteractingListeners()](#GetInteractingListeners)

[GetOutputPins()](#GetOutputPins)

[SetAngleAttenuation()](#SetAngleAttenuation)

[SetDistanceAttenuation()](#SetDistanceAttenuation)

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
