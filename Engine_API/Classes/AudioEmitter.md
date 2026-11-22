<!-- Source: https://create.roblox.com/docs/reference/engine/classes/AudioEmitter -->

AudioEmitter | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/AudioEmitter.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [AudioEmitter](/docs/reference/engine/classes/AudioEmitter)

English

Feedback

Engine Class

AudioEmitter

---

## Summary

Properties

|

[AcousticSimulationEnabled](#AcousticSimulationEnabled) :[boolean](/docs/luau/booleans)

 |
| --- | --- |
|

[AngleAttenuation](#AngleAttenuation) : BinaryString

 |
|

[AudioInteractionGroup](#AudioInteractionGroup) :[string](/docs/luau/strings)

 |
|

[DistanceAttenuation](#DistanceAttenuation) : BinaryString

 |
|

[DistanceAttenuationBounds](#DistanceAttenuationBounds) :[NumberRange](/docs/reference/engine/datatypes/NumberRange)

 |
|

[DistanceAttenuationMode](#DistanceAttenuationMode) :[Enum.DistanceAttenuationMode](/docs/reference/engine/enums/DistanceAttenuationMode)

 |
|

[PositionInstance](#PositionInstance) :[Instance](/docs/reference/engine/datatypes/Instance)

 |
|

[PositionType](#PositionType) :[Enum.EmitterPositionType](/docs/reference/engine/enums/EmitterPositionType)

 |
|

[SimulationFidelity](#SimulationFidelity) :[Enum.AudioSimulationFidelity](/docs/reference/engine/enums/AudioSimulationFidelity)

Deprecated

 |

Methods

|

[GetAngleAttenuation](#GetAngleAttenuation) () :[Dictionary](/docs/luau/tables#dictionaries)

 |
|

[GetAudibilityFor](#GetAudibilityFor) (listener :  [AudioListener](/docs/reference/engine/classes/AudioListener) ) :[number](/docs/luau/numbers)

 |
|

[GetConnectedWires](#GetConnectedWires) (pin :  [string](/docs/luau/strings) ) : {[Wire](/docs/reference/engine/classes/Wire) }

 |
|

[GetDistanceAttenuation](#GetDistanceAttenuation) () :[Dictionary](/docs/luau/tables#dictionaries)

 |
|

[GetInputPins](#GetInputPins) () :[{any}](/docs/luau/tables#arrays)

 |
|

[GetInteractingListeners](#GetInteractingListeners) () : {[AudioListener](/docs/reference/engine/classes/AudioListener) }

 |
|

[GetOutputPins](#GetOutputPins) () :[{any}](/docs/luau/tables#arrays)

 |
|

[SetAngleAttenuation](#SetAngleAttenuation) (curve :  [Dictionary](/docs/luau/tables#dictionaries) ) : ()

 |
|

[SetDistanceAttenuation](#SetDistanceAttenuation) (curve :  [Dictionary](/docs/luau/tables#dictionaries) ) : ()

 |

Events

|

[WiringChanged](#WiringChanged) (connected :  [boolean](/docs/luau/booleans) , pin :  [string](/docs/luau/strings) , wire :  [Wire](/docs/reference/engine/classes/Wire) , instance :  [Instance](/docs/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

Playing one asset from multiple 3d locations at once

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

API Reference

Properties

AcousticSimulationEnabled

Read Parallel

Capabilities: Audio

AudioEmitter.AcousticSimulationEnabled :[boolean](/docs/luau/booleans)

Provide feedback

---

AngleAttenuation

Roblox Security

Read Parallel

Capabilities: Audio

AudioEmitter.AngleAttenuation : BinaryString

Provide feedback

---

AudioInteractionGroup

Read Parallel

Capabilities: Audio

AudioEmitter.AudioInteractionGroup :[string](/docs/luau/strings)

Provide feedback

---

DistanceAttenuation

Roblox Security

Read Parallel

Capabilities: Audio

AudioEmitter.DistanceAttenuation : BinaryString

Provide feedback

---

DistanceAttenuationBounds

Read Parallel

Capabilities: Audio

AudioEmitter.DistanceAttenuationBounds :[NumberRange](/docs/reference/engine/datatypes/NumberRange)

Provide feedback

---

DistanceAttenuationMode

Read Parallel

Capabilities: Audio

AudioEmitter.DistanceAttenuationMode :[Enum.DistanceAttenuationMode](/docs/reference/engine/enums/DistanceAttenuationMode)

Provide feedback

---

PositionInstance

Read Parallel

Capabilities: Audio

AudioEmitter.PositionInstance :[Instance](/docs/reference/engine/datatypes/Instance)

Provide feedback

---

PositionType

Read Parallel

Capabilities: Audio

AudioEmitter.PositionType :[Enum.EmitterPositionType](/docs/reference/engine/enums/EmitterPositionType)

Provide feedback

---

SimulationFidelity

Deprecated

Show details

---

Methods

GetAngleAttenuation

Capabilities: Audio

AudioEmitter:GetAngleAttenuation () :[Dictionary](/docs/luau/tables#dictionaries)

Returns

[Dictionary](/docs/luau/tables#dictionaries)

Provide feedback

---

GetAudibilityFor

Capabilities: Audio

AudioEmitter:GetAudibilityFor (listener :[AudioListener](/docs/reference/engine/classes/AudioListener) ) :[number](/docs/luau/numbers)

Parameters

|

listener :[AudioListener](/docs/reference/engine/classes/AudioListener)

 |

Returns

[number](/docs/luau/numbers)

Provide feedback

---

GetConnectedWires

Capabilities: Audio

AudioEmitter:GetConnectedWires (pin :[string](/docs/luau/strings) ) : {[Wire](/docs/reference/engine/classes/Wire) }

Parameters

|

pin :[string](/docs/luau/strings)

 |

Returns

{[Wire](/docs/reference/engine/classes/Wire) }

Provide feedback

---

GetDistanceAttenuation

Capabilities: Audio

AudioEmitter:GetDistanceAttenuation () :[Dictionary](/docs/luau/tables#dictionaries)

Returns

[Dictionary](/docs/luau/tables#dictionaries)

Provide feedback

---

GetInputPins

Capabilities: Audio

AudioEmitter:GetInputPins () :[{any}](/docs/luau/tables#arrays)

Returns

[{any}](/docs/luau/tables#arrays)

Provide feedback

---

GetInteractingListeners

Capabilities: Audio

AudioEmitter:GetInteractingListeners () : {[AudioListener](/docs/reference/engine/classes/AudioListener) }

Returns

{[AudioListener](/docs/reference/engine/classes/AudioListener) }

Provide feedback

---

GetOutputPins

Capabilities: Audio

AudioEmitter:GetOutputPins () :[{any}](/docs/luau/tables#arrays)

Returns

[{any}](/docs/luau/tables#arrays)

Provide feedback

---

SetAngleAttenuation

Capabilities: Audio

AudioEmitter:SetAngleAttenuation (curve :[Dictionary](/docs/luau/tables#dictionaries) ) : ()

Parameters

|

curve :[Dictionary](/docs/luau/tables#dictionaries)

 |

Returns

()

Provide feedback

---

SetDistanceAttenuation

Capabilities: Audio

AudioEmitter:SetDistanceAttenuation (curve :[Dictionary](/docs/luau/tables#dictionaries) ) : ()

Parameters

|

curve :[Dictionary](/docs/luau/tables#dictionaries)

 |

Returns

()

Code Samples

Custom Distance Attenuation

```

local Players = game:GetService("Players")

local emitterPart = Instance.new("Part")

emitterPart.Anchored = true

emitterPart.Position = Vector3.new(0, 0, 0)

emitterPart.Parent = workspace

local emitter: AudioEmitter = Instance.new("AudioEmitter")

emitter.Parent = emitterPart

local curve = {}

curve[10] = 1 -- Within a distance of 10 studs, listeners hear this emitter at full volume

curve[100] = 0.4 -- At a distance of 100 studs, listeners hear this emitter at 40% volume

curve[300] = 0 -- At any distance farther than 300 studs, listeners cannot hear this emitter

emitter:SetDistanceAttenuation(curve)

-- Replicate the rolloff curve from the old voice implementation

-- Default voice without the new audio API uses quadratic rolloff ranging from 7 to 80 studs

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

Provide feedback

---

Events

WiringChanged

Capabilities: Audio

AudioEmitter.WiringChanged (

connected :[boolean](/docs/luau/booleans) , pin :[string](/docs/luau/strings) , wire :[Wire](/docs/reference/engine/classes/Wire) , instance :[Instance](/docs/reference/engine/datatypes/Instance)

) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

connected :[boolean](/docs/luau/booleans)

 |
|

pin :[string](/docs/luau/strings)

 |
|

wire :[Wire](/docs/reference/engine/classes/Wire)

 |
|

instance :[Instance](/docs/reference/engine/datatypes/Instance)

 |

Provide feedback

---

Jump to

▼

AudioEmitter

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[AcousticSimulationEnabled](#AcousticSimulationEnabled)

[AngleAttenuation](#AngleAttenuation)

[AudioInteractionGroup](#AudioInteractionGroup)

[DistanceAttenuation](#DistanceAttenuation)

[DistanceAttenuationBounds](#DistanceAttenuationBounds)

[DistanceAttenuationMode](#DistanceAttenuationMode)

[PositionInstance](#PositionInstance)

[PositionType](#PositionType)

[SimulationFidelity](#SimulationFidelity)

[Methods](#methods)

[GetAngleAttenuation()](#GetAngleAttenuation)

[GetAudibilityFor()](#GetAudibilityFor)

[GetConnectedWires()](#GetConnectedWires)

[GetDistanceAttenuation()](#GetDistanceAttenuation)

[GetInputPins()](#GetInputPins)

[GetInteractingListeners()](#GetInteractingListeners)

[GetOutputPins()](#GetOutputPins)

[SetAngleAttenuation()](#SetAngleAttenuation)

[SetDistanceAttenuation()](#SetDistanceAttenuation)

[Events](#events)

[WiringChanged](#WiringChanged)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
