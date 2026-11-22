<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/AudioChannelSplitter -->

AudioChannelSplitter | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/AudioChannelSplitter.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [AudioChannelSplitter](/docs/en-us/reference/engine/classes/AudioChannelSplitter)

English

Feedback

Engine Class

AudioChannelSplitter

---

## Summary

Properties

|

[Layout](#Layout) :[Enum.AudioChannelLayout](/docs/en-us/reference/engine/enums/AudioChannelLayout)

 |
| --- | --- |

Methods

|

[GetConnectedWires](#GetConnectedWires) (pin :  [string](/docs/en-us/luau/strings) ) : {[Wire](/docs/en-us/reference/engine/classes/Wire) }

 |
|

[GetInputPins](#GetInputPins) () :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[GetOutputPins](#GetOutputPins) () :[{any}](/docs/en-us/luau/tables#arrays)

 |

Events

|

[WiringChanged](#WiringChanged) (connected :  [boolean](/docs/en-us/luau/booleans) , pin :  [string](/docs/en-us/luau/strings) , wire :  [Wire](/docs/en-us/reference/engine/classes/Wire) , instance :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Splitting & Mixing Channels

```

local Workspace = game:GetService("Workspace")

local function wireUp(source: Instance, target: Instance, sourceName: string?, targetName: string?)

	local wire = Instance.new("Wire", source)

	wire.SourceInstance = source

	wire.TargetInstance = target

	if sourceName then

		wire.SourceName = sourceName

	end

	if targetName then

		wire.TargetName = targetName

	end

	return wire

end

local listener = Instance.new("AudioListener")

listener.Parent = Workspace.CurrentCamera

local output = Instance.new("AudioDeviceOutput")

output.Parent = Workspace

local splitter = Instance.new("AudioChannelSplitter")

splitter.Parent = Workspace

local mixer = Instance.new("AudioChannelMixer")

mixer.Parent = Workspace

-- Send what the listener hears to a splitter and send a mix to the final output

wireUp(listener, splitter)

wireUp(mixer, output)

-- Set up both the splitter and mixer to use a quadrophonic layout

splitter.Layout = Enum.AudioChannelLayout.Quad

mixer.Layout = Enum.AudioChannelLayout.Quad

-- Give each of the four channels its own pitch shifter

local frontLeft = Instance.new("AudioPitchShifter")

frontLeft.Name = "Front Left"

frontLeft.Pitch = 1.25

frontLeft.Parent = Workspace

local backLeft = Instance.new("AudioPitchShifter")

backLeft.Name = "Back Left"

backLeft.Pitch = 0.5

backLeft.Parent = Workspace

local frontRight = Instance.new("AudioPitchShifter")

frontRight.Name = "Front Right"

frontRight.Pitch = 1.5

frontRight.Parent = Workspace

local backRight = Instance.new("AudioPitchShifter")

backRight.Name = "Back Right"

backRight.Pitch = 0.75

backRight.Parent = Workspace

wireUp(splitter, frontLeft, "Left")

wireUp(splitter, backLeft, "BackLeft")

wireUp(splitter, frontRight, "Right")

wireUp(splitter, backRight, "BackRight")

wireUp(frontLeft, mixer, nil, "Left")

wireUp(backLeft, mixer, nil, "BackLeft")

wireUp(frontRight, mixer, nil, "Right")

wireUp(backRight, mixer, nil, "BackRight")

-- Configure a part to emit audio

local part = Instance.new("Part")

part.Shape = Enum.PartType.Ball

part.Size = Vector3.new(4, 4, 4)

part.Material = Enum.Material.SmoothPlastic

part.CastShadow = false

part.Position = Vector3.new(0, 4, -12)

part.Anchored = true

part.Parent = Workspace

local analyzer = Instance.new("AudioAnalyzer")

analyzer.Parent = part

local emitter = Instance.new("AudioEmitter")

emitter.Parent = part

local assetPlayer = Instance.new("AudioPlayer")

assetPlayer.Looping = true

assetPlayer.Asset = "rbxassetid://97799489309320"

assetPlayer.Parent = emitter

wireUp(assetPlayer, emitter)

wireUp(assetPlayer, analyzer)

-- Start playing the audio

assetPlayer:Play()

-- Adjust the part's color as the audio plays

while true do

	local peak = math.sqrt(analyzer.PeakLevel)

	part.Color = Color3.new(peak, peak, peak)

	task.wait()

end

```

---

API Reference

Properties

Layout

Read Parallel

Capabilities: Audio

AudioChannelSplitter.Layout :[Enum.AudioChannelLayout](/docs/en-us/reference/engine/enums/AudioChannelLayout)

Provide feedback

---

Methods

GetConnectedWires

Capabilities: Audio

AudioChannelSplitter:GetConnectedWires (pin :[string](/docs/en-us/luau/strings) ) : {[Wire](/docs/en-us/reference/engine/classes/Wire) }

Parameters

|

pin :[string](/docs/en-us/luau/strings)

 |

Returns

{[Wire](/docs/en-us/reference/engine/classes/Wire) }

Provide feedback

---

GetInputPins

Capabilities: Audio

AudioChannelSplitter:GetInputPins () :[{any}](/docs/en-us/luau/tables#arrays)

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

GetOutputPins

Capabilities: Audio

AudioChannelSplitter:GetOutputPins () :[{any}](/docs/en-us/luau/tables#arrays)

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

Events

WiringChanged

Capabilities: Audio

AudioChannelSplitter.WiringChanged (

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

AudioChannelSplitter

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[Layout](#Layout)

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
