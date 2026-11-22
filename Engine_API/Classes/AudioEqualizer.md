<!-- Source: https://create.roblox.com/docs/reference/engine/classes/AudioEqualizer -->

AudioEqualizer | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/AudioEqualizer.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [AudioEqualizer](/docs/reference/engine/classes/AudioEqualizer)

English

Feedback

Engine Class

AudioEqualizer

---

## Summary

Properties

|

[Bypass](#Bypass) :[boolean](/docs/luau/booleans)

 |
| --- | --- |
|

[HighGain](#HighGain) :[number](/docs/luau/numbers)

 |
|

[LowGain](#LowGain) :[number](/docs/luau/numbers)

 |
|

[MidGain](#MidGain) :[number](/docs/luau/numbers)

 |
|

[MidRange](#MidRange) :[NumberRange](/docs/reference/engine/datatypes/NumberRange)

 |

Methods

|

[GetConnectedWires](#GetConnectedWires) (pin :  [string](/docs/luau/strings) ) : {[Wire](/docs/reference/engine/classes/Wire) }

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

Listener Equalization

```

local function wireUp(source: Instance, target: Instance): Wire

	local wire = Instance.new("Wire")

	wire.Parent = target

	wire.SourceInstance = source

	wire.TargetInstance = target

	return wire

end

local function getCFrameFrom(inst: Instance): CFrame?

	local parent = inst.Parent

	if not parent then

		return nil

	elseif parent:IsA("Model") then

		return parent.WorldPivot

	elseif parent:IsA("BasePart") then

		return parent.CFrame

	elseif parent:IsA("Attachment") then

		return parent.WorldCFrame

	elseif parent:IsA("Camera") then

		return parent.CFrame

	else

		return nil

	end

end

local function rescale(value: number, oldRange: NumberRange, newRange: NumberRange): number

	local clamped = math.clamp(value, oldRange.Min, oldRange.Max)

	local normalized = clamped - oldRange.Min / (oldRange.Max - oldRange.Min)

	return normalized * (newRange.Max - newRange.Min) + newRange.Min

end

local assetPlayer = Instance.new("AudioPlayer")

assetPlayer.AssetId = "rbxassetid://142376088"

assetPlayer.Parent = workspace

local equalizer = Instance.new("AudioEqualizer")

equalizer.MidRange = NumberRange.new(400, 3000)

equalizer.Parent = workspace

local emitterPart = Instance.new("Part")

emitterPart.Anchored = true

emitterPart.Position = Vector3.new(0, 5, 0)

emitterPart.Parent = workspace

local emitter = Instance.new("AudioEmitter")

emitter.Parent = emitterPart

local listener = Instance.new("AudioListener")

listener.Parent = workspace.CurrentCamera

local output = Instance.new("AudioDeviceOutput")

output.Parent = workspace

wireUp(assetPlayer, equalizer)

wireUp(equalizer, emitter)

wireUp(listener, output)

assetPlayer.Looping = true

assetPlayer:Play()

while true do

	local emitterFrame = getCFrameFrom(emitter)

	local listenerFrame = getCFrameFrom(listener)

	if emitterFrame and listenerFrame then

		local towardEmitter = emitterFrame.Position - listenerFrame.Position

		local look = towardEmitter.Unit:Dot(listenerFrame.LookVector) -- ranges from [-1, 1]

		look = rescale(look, NumberRange.new(-1, 1), NumberRange.new(-20, 0))

		local distance = math.max(towardEmitter.Magnitude, 1)

		local rolloff = 1 / distance -- ranges from [0, 1]

		rolloff = rescale(rolloff, NumberRange.new(0, 1), NumberRange.new(-10, 10))

		equalizer.HighGain = look + rolloff

		equalizer.LowGain = rolloff

	end

	task.wait()

end

```

---

API Reference

Properties

Bypass

Read Parallel

Capabilities: Audio

AudioEqualizer.Bypass :[boolean](/docs/luau/booleans)

Provide feedback

---

HighGain

Read Parallel

Capabilities: Audio

AudioEqualizer.HighGain :[number](/docs/luau/numbers)

Provide feedback

---

LowGain

Read Parallel

Capabilities: Audio

AudioEqualizer.LowGain :[number](/docs/luau/numbers)

Provide feedback

---

MidGain

Read Parallel

Capabilities: Audio

AudioEqualizer.MidGain :[number](/docs/luau/numbers)

Provide feedback

---

MidRange

Read Parallel

Capabilities: Audio

AudioEqualizer.MidRange :[NumberRange](/docs/reference/engine/datatypes/NumberRange)

Provide feedback

---

Methods

GetConnectedWires

Capabilities: Audio

AudioEqualizer:GetConnectedWires (pin :[string](/docs/luau/strings) ) : {[Wire](/docs/reference/engine/classes/Wire) }

Parameters

|

pin :[string](/docs/luau/strings)

 |

Returns

{[Wire](/docs/reference/engine/classes/Wire) }

Provide feedback

---

GetInputPins

Capabilities: Audio

AudioEqualizer:GetInputPins () :[{any}](/docs/luau/tables#arrays)

Returns

[{any}](/docs/luau/tables#arrays)

Provide feedback

---

GetOutputPins

Capabilities: Audio

AudioEqualizer:GetOutputPins () :[{any}](/docs/luau/tables#arrays)

Returns

[{any}](/docs/luau/tables#arrays)

Provide feedback

---

Events

WiringChanged

Capabilities: Audio

AudioEqualizer.WiringChanged (

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

AudioEqualizer

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[Bypass](#Bypass)

[HighGain](#HighGain)

[LowGain](#LowGain)

[MidGain](#MidGain)

[MidRange](#MidRange)

[Methods](#methods)

[GetConnectedWires()](#GetConnectedWires)

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
