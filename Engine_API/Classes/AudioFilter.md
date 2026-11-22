<!-- Source: https://create.roblox.com/docs/reference/engine/classes/AudioFilter -->

AudioFilter | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/AudioFilter.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [AudioFilter](/docs/reference/engine/classes/AudioFilter)

English

Feedback

Engine Class

AudioFilter

---

## Summary

Properties

|

[Bypass](#Bypass) :[boolean](/docs/luau/booleans)

 |
| --- | --- |
|

[FilterType](#FilterType) :[Enum.AudioFilterType](/docs/reference/engine/enums/AudioFilterType)

 |
|

[Frequency](#Frequency) :[number](/docs/luau/numbers)

 |
|

[Gain](#Gain) :[number](/docs/luau/numbers)

 |
|

[Q](#Q) :[number](/docs/luau/numbers)

 |

Methods

|

[GetConnectedWires](#GetConnectedWires) (pin :  [string](/docs/luau/strings) ) : {[Wire](/docs/reference/engine/classes/Wire) }

 |
|

[GetGainAt](#GetGainAt) (frequency :  [number](/docs/luau/numbers) ) :[number](/docs/luau/numbers)

 |
|

[GetInputPins](#GetInputPins) () :[{any}](/docs/luau/tables#arrays)

 |
|

[GetOutputPins](#GetOutputPins) () :[{any}](/docs/luau/tables#arrays)

 |

Events

|

[WiringChanged](#WiringChanged) (connected :  [boolean](/docs/luau/booleans) , pin :  [string](/docs/luau/strings) , wire :  [Wire](/docs/reference/engine/classes/Wire) , instance :  [Instance](/docs/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

Emitter Filtering

```

-- This assumes the workspace contains a Part with an AudioEmitter and an AudioPlayer, and the camera has an AudioListener

local RunService = game:GetService("RunService")

local part: BasePart = workspace.Part

local camera: Camera = workspace.CurrentCamera

local audioPlayer: AudioPlayer = part.AudioPlayer

local audioEmitter: AudioEmitter = part.AudioEmitter

local audioListener: AudioListener = camera.AudioListener

local raycastParams = RaycastParams.new()

raycastParams.FilterDescendantsInstances = { audioEmitter.Parent }

raycastParams.FilterType = Enum.RaycastFilterType.Exclude

-- Create a new AudioFilter

local filter: AudioFilter = Instance.new("AudioFilter")

filter.FilterType = Enum.AudioFilterType.Lowpass12dB

filter.Frequency = 22000

filter.Q = math.sqrt(2) / 2 -- This Q value produces a flat lowpass for the 12dB slope type

filter.Parent = part

-- Put the AudioFilter between the player and the emitter

local function wireTo(source: Instance, target: Instance): Wire

	local wire = Instance.new("Wire")

	wire.SourceInstance = source

	wire.TargetInstance = target

	wire.Parent = target

end

wireTo(audioPlayer, filter)

wireTo(filter, audioEmitter)

-- Update the filter based on the positions of the emitter and listener

RunService.Heartbeat:Connect(function()

	local emitterPos: Vector3 = part.Position

	local listenerPos: Vector3 = camera.CFrame.Position

	local raycastResult = workspace:Raycast(emitterPos, (listenerPos - emitterPos), raycastParams)

	filter.Frequency = if raycastResult then 500 else 22000

end)

```

---

API Reference

Properties

Bypass

Read Parallel

Capabilities: Audio

AudioFilter.Bypass :[boolean](/docs/luau/booleans)

Provide feedback

---

FilterType

Read Parallel

Capabilities: Audio

AudioFilter.FilterType :[Enum.AudioFilterType](/docs/reference/engine/enums/AudioFilterType)

Provide feedback

---

Frequency

Read Parallel

Capabilities: Audio

AudioFilter.Frequency :[number](/docs/luau/numbers)

Provide feedback

---

Gain

Read Parallel

Capabilities: Audio

AudioFilter.Gain :[number](/docs/luau/numbers)

Provide feedback

---

Q

Read Parallel

Capabilities: Audio

AudioFilter.Q :[number](/docs/luau/numbers)

Provide feedback

---

Methods

GetConnectedWires

Capabilities: Audio

AudioFilter:GetConnectedWires (pin :[string](/docs/luau/strings) ) : {[Wire](/docs/reference/engine/classes/Wire) }

Parameters

|

pin :[string](/docs/luau/strings)

 |

Returns

{[Wire](/docs/reference/engine/classes/Wire) }

Provide feedback

---

GetGainAt

Capabilities: Audio

AudioFilter:GetGainAt (frequency :[number](/docs/luau/numbers) ) :[number](/docs/luau/numbers)

Parameters

|

frequency :[number](/docs/luau/numbers)

 |

Returns

[number](/docs/luau/numbers)

Provide feedback

---

GetInputPins

Capabilities: Audio

AudioFilter:GetInputPins () :[{any}](/docs/luau/tables#arrays)

Returns

[{any}](/docs/luau/tables#arrays)

Provide feedback

---

GetOutputPins

Capabilities: Audio

AudioFilter:GetOutputPins () :[{any}](/docs/luau/tables#arrays)

Returns

[{any}](/docs/luau/tables#arrays)

Provide feedback

---

Events

WiringChanged

Capabilities: Audio

AudioFilter.WiringChanged (

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

AudioFilter

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[Bypass](#Bypass)

[FilterType](#FilterType)

[Frequency](#Frequency)

[Gain](#Gain)

[Q](#Q)

[Methods](#methods)

[GetConnectedWires()](#GetConnectedWires)

[GetGainAt()](#GetGainAt)

[GetInputPins()](#GetInputPins)

[GetOutputPins()](#GetOutputPins)

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
