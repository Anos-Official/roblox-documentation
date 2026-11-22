<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/AudioListener -->

AudioListener | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/AudioListener.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [AudioListener](/docs/en-us/reference/engine/classes/AudioListener)

English

Feedback

Engine Class

AudioListener

---

## Summary

Properties

|

[AcousticSimulationEnabled](#AcousticSimulationEnabled) :[boolean](/docs/en-us/luau/booleans)

 |
| --- | --- |
|

[AngleAttenuation](#AngleAttenuation) : BinaryString

 |
|

[AudioInteractionGroup](#AudioInteractionGroup) :[string](/docs/en-us/luau/strings)

 |
|

[DistanceAttenuation](#DistanceAttenuation) : BinaryString

 |
|

[PositionInstance](#PositionInstance) :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |
|

[PositionType](#PositionType) :[Enum.ListenerPositionType](/docs/en-us/reference/engine/enums/ListenerPositionType)

 |
|

[SimulationFidelity](#SimulationFidelity) :[Enum.AudioSimulationFidelity](/docs/en-us/reference/engine/enums/AudioSimulationFidelity)

Deprecated

 |

Methods

|

[GetAngleAttenuation](#GetAngleAttenuation) () :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |
|

[GetAudibilityFor](#GetAudibilityFor) (emitter :  [AudioEmitter](/docs/en-us/reference/engine/classes/AudioEmitter) ) :[number](/docs/en-us/luau/numbers)

 |
|

[GetConnectedWires](#GetConnectedWires) (pin :  [string](/docs/en-us/luau/strings) ) : {[Wire](/docs/en-us/reference/engine/classes/Wire) }

 |
|

[GetDistanceAttenuation](#GetDistanceAttenuation) () :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |
|

[GetInputPins](#GetInputPins) () :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[GetInteractingEmitters](#GetInteractingEmitters) () : {[AudioEmitter](/docs/en-us/reference/engine/classes/AudioEmitter) }

 |
|

[GetOutputPins](#GetOutputPins) () :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[SetAngleAttenuation](#SetAngleAttenuation) (curve :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) : ()

 |
|

[SetDistanceAttenuation](#SetDistanceAttenuation) (curve :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) : ()

 |

Events

|

[WiringChanged](#WiringChanged) (connected :  [boolean](/docs/en-us/luau/booleans) , pin :  [string](/docs/en-us/luau/strings) , wire :  [Wire](/docs/en-us/reference/engine/classes/Wire) , instance :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Camera Listener

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

API Reference

Properties

AcousticSimulationEnabled

Read Parallel

Capabilities: Audio

AudioListener.AcousticSimulationEnabled :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

AngleAttenuation

Roblox Security

Read Parallel

Capabilities: Audio

AudioListener.AngleAttenuation : BinaryString

Provide feedback

---

AudioInteractionGroup

Read Parallel

Capabilities: Audio

AudioListener.AudioInteractionGroup :[string](/docs/en-us/luau/strings)

Provide feedback

---

DistanceAttenuation

Roblox Security

Read Parallel

Capabilities: Audio

AudioListener.DistanceAttenuation : BinaryString

Provide feedback

---

PositionInstance

Read Parallel

Capabilities: Audio

AudioListener.PositionInstance :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

Provide feedback

---

PositionType

Read Parallel

Capabilities: Audio

AudioListener.PositionType :[Enum.ListenerPositionType](/docs/en-us/reference/engine/enums/ListenerPositionType)

Provide feedback

---

SimulationFidelity

Deprecated

Show details

---

Methods

GetAngleAttenuation

Capabilities: Audio

AudioListener:GetAngleAttenuation () :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Returns

[Dictionary](/docs/en-us/luau/tables#dictionaries)

Provide feedback

---

GetAudibilityFor

Capabilities: Audio

AudioListener:GetAudibilityFor (emitter :[AudioEmitter](/docs/en-us/reference/engine/classes/AudioEmitter) ) :[number](/docs/en-us/luau/numbers)

Parameters

|

emitter :[AudioEmitter](/docs/en-us/reference/engine/classes/AudioEmitter)

 |

Returns

[number](/docs/en-us/luau/numbers)

Provide feedback

---

GetConnectedWires

Capabilities: Audio

AudioListener:GetConnectedWires (pin :[string](/docs/en-us/luau/strings) ) : {[Wire](/docs/en-us/reference/engine/classes/Wire) }

Parameters

|

pin :[string](/docs/en-us/luau/strings)

 |

Returns

{[Wire](/docs/en-us/reference/engine/classes/Wire) }

Provide feedback

---

GetDistanceAttenuation

Capabilities: Audio

AudioListener:GetDistanceAttenuation () :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Returns

[Dictionary](/docs/en-us/luau/tables#dictionaries)

Provide feedback

---

GetInputPins

Capabilities: Audio

AudioListener:GetInputPins () :[{any}](/docs/en-us/luau/tables#arrays)

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

GetInteractingEmitters

Capabilities: Audio

AudioListener:GetInteractingEmitters () : {[AudioEmitter](/docs/en-us/reference/engine/classes/AudioEmitter) }

Returns

{[AudioEmitter](/docs/en-us/reference/engine/classes/AudioEmitter) }

Provide feedback

---

GetOutputPins

Capabilities: Audio

AudioListener:GetOutputPins () :[{any}](/docs/en-us/luau/tables#arrays)

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

SetAngleAttenuation

Capabilities: Audio

AudioListener:SetAngleAttenuation (curve :[Dictionary](/docs/en-us/luau/tables#dictionaries) ) : ()

Parameters

|

curve :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |

Returns

()

Code Samples

Camera Listener

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

	[0] = 1, -- Emitters directly in front of the listener will be full volume

	[180] = 0.5 -- Emitters directly behind the listener will be half volume

})

wire.SourceInstance = listener

wire.TargetInstance = output

```

Provide feedback

---

SetDistanceAttenuation

Capabilities: Audio

AudioListener:SetDistanceAttenuation (curve :[Dictionary](/docs/en-us/luau/tables#dictionaries) ) : ()

Parameters

|

curve :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |

Returns

()

Provide feedback

---

Events

WiringChanged

Capabilities: Audio

AudioListener.WiringChanged (

connected :[boolean](/docs/en-us/luau/booleans) , pin :[string](/docs/en-us/luau/strings) , wire :[Wire](/docs/en-us/reference/engine/classes/Wire) , instance :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

connected :[boolean](/docs/en-us/luau/booleans)

 |
|

pin :[string](/docs/en-us/luau/strings)

 |
|

wire :[Wire](/docs/en-us/reference/engine/classes/Wire)

 |
|

instance :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |

Provide feedback

---

Jump to

▼

AudioListener

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[AcousticSimulationEnabled](#AcousticSimulationEnabled)

[AngleAttenuation](#AngleAttenuation)

[AudioInteractionGroup](#AudioInteractionGroup)

[DistanceAttenuation](#DistanceAttenuation)

[PositionInstance](#PositionInstance)

[PositionType](#PositionType)

[SimulationFidelity](#SimulationFidelity)

[Methods](#methods)

[GetAngleAttenuation()](#GetAngleAttenuation)

[GetAudibilityFor()](#GetAudibilityFor)

[GetConnectedWires()](#GetConnectedWires)

[GetDistanceAttenuation()](#GetDistanceAttenuation)

[GetInputPins()](#GetInputPins)

[GetInteractingEmitters()](#GetInteractingEmitters)

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
