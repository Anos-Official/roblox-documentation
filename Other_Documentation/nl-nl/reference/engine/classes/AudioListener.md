<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/AudioListener -->

AudioListener | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [AudioListener](/docs/nl-nl/reference/engine/classes/AudioListener)

Nederlands

Feedback

Engine-klasse

AudioListener

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/AudioListener)  om deze pagina in het Engels te bekijken.

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

[PositionInstance](#PositionInstance) :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
|

[PositionType](#PositionType) :[Enum.ListenerPositionType](/docs/nl-nl/reference/engine/enums/ListenerPositionType)

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

[GetAudibilityFor](#GetAudibilityFor) (emitter :  [AudioEmitter](/docs/nl-nl/reference/engine/classes/AudioEmitter) ) :[number](/docs/nl-nl/luau/numbers)

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

[GetInteractingEmitters](#GetInteractingEmitters) () : {[AudioEmitter](/docs/nl-nl/reference/engine/classes/AudioEmitter) }

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

Camera Luisteraar

```

local listener = Instance.new("AudioListener")

local output = Instance.new("AudioDeviceOutput")

local wire = Instance.new("Wire")

listener.Parent = workspace.Camera

wire.Parent = listener

output.Parent = wire

wire.SourceInstance = listener

wire.TargetInstance = output

```

---

API-referentie

Eigenschappen

AcousticSimulationEnabled

Parallel lezen

Mogelijkheden: Audio

AudioListener.AcousticSimulationEnabled :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

AngleAttenuation

Roblox Security

Parallel lezen

Mogelijkheden: Audio

AudioListener.AngleAttenuation : BinaryString

Feedback geven

---

AudioInteractionGroup

Parallel lezen

Mogelijkheden: Audio

AudioListener.AudioInteractionGroup :[string](/docs/nl-nl/luau/strings)

Feedback geven

---

DistanceAttenuation

Roblox Security

Parallel lezen

Mogelijkheden: Audio

AudioListener.DistanceAttenuation : BinaryString

Feedback geven

---

PositionInstance

Parallel lezen

Mogelijkheden: Audio

AudioListener.PositionInstance :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

Feedback geven

---

PositionType

Parallel lezen

Mogelijkheden: Audio

AudioListener.PositionType :[Enum.ListenerPositionType](/docs/nl-nl/reference/engine/enums/ListenerPositionType)

Feedback geven

---

SimulationFidelity

Verouderd

Details weergeven

---

Methoden

GetAngleAttenuation

Mogelijkheden: Audio

AudioListener:GetAngleAttenuation () :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Teruggaves

[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Feedback geven

---

GetAudibilityFor

Mogelijkheden: Audio

AudioListener:GetAudibilityFor (emitter :[AudioEmitter](/docs/nl-nl/reference/engine/classes/AudioEmitter) ) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

emitter :[AudioEmitter](/docs/nl-nl/reference/engine/classes/AudioEmitter)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

GetConnectedWires

Mogelijkheden: Audio

AudioListener:GetConnectedWires (pin :[string](/docs/nl-nl/luau/strings) ) : {[Wire](/docs/nl-nl/reference/engine/classes/Wire) }

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

AudioListener:GetDistanceAttenuation () :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Teruggaves

[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Feedback geven

---

GetInputPins

Mogelijkheden: Audio

AudioListener:GetInputPins () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

GetInteractingEmitters

Mogelijkheden: Audio

AudioListener:GetInteractingEmitters () : {[AudioEmitter](/docs/nl-nl/reference/engine/classes/AudioEmitter) }

Teruggaves

{[AudioEmitter](/docs/nl-nl/reference/engine/classes/AudioEmitter) }

Feedback geven

---

GetOutputPins

Mogelijkheden: Audio

AudioListener:GetOutputPins () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

SetAngleAttenuation

Mogelijkheden: Audio

AudioListener:SetAngleAttenuation (curve :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

Parameters

|

curve :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |

Teruggaves

()

Codevoorbeelden

Camera Luisteraar

```

local Workspace = game:GetService("Workspace")

local currentCamera = Workspace.CurrentCamera

local listener = Instance.new("AudioListener")

listener.Parent = currentCamera

local wire = Instance.new("Wire")

wire.Parent = listener

local output = Instance.new("AudioDeviceOutput")

output.Parent = wire

listener:SetAngleAttenuation({

	[0] = 1, -- Geluidsemitters direct voor de luisteraar zullen op volle sterkte zijn

	[180] = 0.5 -- Geluidsemitters direct achter de luisteraar zullen op halve sterkte zijn

})

wire.SourceInstance = listener

wire.TargetInstance = output

```

Feedback geven

---

SetDistanceAttenuation

Mogelijkheden: Audio

AudioListener:SetDistanceAttenuation (curve :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

Parameters

|

curve :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |

Teruggaves

()

Feedback geven

---

Evenementen

WiringChanged

Mogelijkheden: Audio

AudioListener.WiringChanged (

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

AudioListener

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[AcousticSimulationEnabled](#AcousticSimulationEnabled)

[AngleAttenuation](#AngleAttenuation)

[AudioInteractionGroup](#AudioInteractionGroup)

[DistanceAttenuation](#DistanceAttenuation)

[PositionInstance](#PositionInstance)

[PositionType](#PositionType)

[SimulationFidelity](#SimulationFidelity)

[Methoden](#methods)

[GetAngleAttenuation()](#GetAngleAttenuation)

[GetAudibilityFor()](#GetAudibilityFor)

[GetConnectedWires()](#GetConnectedWires)

[GetDistanceAttenuation()](#GetDistanceAttenuation)

[GetInputPins()](#GetInputPins)

[GetInteractingEmitters()](#GetInteractingEmitters)

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
