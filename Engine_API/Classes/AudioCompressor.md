<!-- Source: https://create.roblox.com/docs/reference/engine/classes/AudioCompressor -->

AudioCompressor | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/AudioCompressor.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [AudioCompressor](/docs/reference/engine/classes/AudioCompressor)

English

Feedback

Engine Class

AudioCompressor

---

## Summary

Properties

|

[Attack](#Attack) :[number](/docs/luau/numbers)

 |
| --- | --- |
|

[Bypass](#Bypass) :[boolean](/docs/luau/booleans)

 |
|

[MakeupGain](#MakeupGain) :[number](/docs/luau/numbers)

 |
|

[Ratio](#Ratio) :[number](/docs/luau/numbers)

 |
|

[Release](#Release) :[number](/docs/luau/numbers)

 |
|

[Threshold](#Threshold) :[number](/docs/luau/numbers)

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

Sidechain Compression

```

local deviceOutput: AudioDeviceOutput = Instance.new("AudioDeviceOutput")

deviceOutput.Parent = workspace

local explosionPlayer: AudioPlayer = Instance.new("AudioPlayer")

explosionPlayer.Parent = workspace

explosionPlayer.AssetId = "rbxassetid://1835333184"

local ambiencePlayer = Instance.new("AudioPlayer")

ambiencePlayer.AssetId = "rbxassetid://9112854440"

local compressor = Instance.new("AudioCompressor")

local wireToCompressor = Instance.new("Wire")

local wireToSidechain = Instance.new("Wire")

local wireToOutput = Instance.new("Wire")

ambiencePlayer.Parent = workspace

compressor.Parent = workspace

wireToCompressor.Parent = workspace

wireToSidechain.Parent = workspace

wireToOutput.Parent = workspace

wireToCompressor.SourceInstance = ambiencePlayer

wireToCompressor.TargetInstance = compressor

wireToSidechain.SourceInstance = explosionPlayer

wireToSidechain.TargetInstance = compressor

wireToSidechain.TargetName = "Sidechain"

wireToOutput.SourceInstance = compressor

wireToOutput.TargetInstance = deviceOutput

ambiencePlayer:Play()

```

---

API Reference

Properties

Attack

Read Parallel

Capabilities: Audio

AudioCompressor.Attack :[number](/docs/luau/numbers)

Provide feedback

---

Bypass

Read Parallel

Capabilities: Audio

AudioCompressor.Bypass :[boolean](/docs/luau/booleans)

Provide feedback

---

MakeupGain

Read Parallel

Capabilities: Audio

AudioCompressor.MakeupGain :[number](/docs/luau/numbers)

Provide feedback

---

Ratio

Read Parallel

Capabilities: Audio

AudioCompressor.Ratio :[number](/docs/luau/numbers)

Provide feedback

---

Release

Read Parallel

Capabilities: Audio

AudioCompressor.Release :[number](/docs/luau/numbers)

Provide feedback

---

Threshold

Read Parallel

Capabilities: Audio

AudioCompressor.Threshold :[number](/docs/luau/numbers)

Provide feedback

---

Methods

GetConnectedWires

Capabilities: Audio

AudioCompressor:GetConnectedWires (pin :[string](/docs/luau/strings) ) : {[Wire](/docs/reference/engine/classes/Wire) }

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

AudioCompressor:GetInputPins () :[{any}](/docs/luau/tables#arrays)

Returns

[{any}](/docs/luau/tables#arrays)

Provide feedback

---

GetOutputPins

Capabilities: Audio

AudioCompressor:GetOutputPins () :[{any}](/docs/luau/tables#arrays)

Returns

[{any}](/docs/luau/tables#arrays)

Provide feedback

---

Events

WiringChanged

Capabilities: Audio

AudioCompressor.WiringChanged (

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

AudioCompressor

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[Attack](#Attack)

[Bypass](#Bypass)

[MakeupGain](#MakeupGain)

[Ratio](#Ratio)

[Release](#Release)

[Threshold](#Threshold)

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
