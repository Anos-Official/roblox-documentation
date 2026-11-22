<!-- Source: https://create.roblox.com/docs/reference/engine/classes/AudioPlayer -->

AudioPlayer | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/AudioPlayer.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [AudioPlayer](/docs/reference/engine/classes/AudioPlayer)

English

Feedback

Engine Class

AudioPlayer

---

## Summary

Properties

|

[Asset](#Asset) : ContentId

 |
| --- | --- |
|

[AssetId](#AssetId) :[string](/docs/luau/strings)

Deprecated

 |
|

[AudioContent](#AudioContent) :[Content](/docs/reference/engine/datatypes/Content)

 |
|

[AutoLoad](#AutoLoad) :[boolean](/docs/luau/booleans)

 |
|

[AutoPlay](#AutoPlay) :[boolean](/docs/luau/booleans)

 |
|

[IsPlaying](#IsPlaying) :[boolean](/docs/luau/booleans)

 |
|

[IsReady](#IsReady) :[boolean](/docs/luau/booleans)

 |
|

[Looping](#Looping) :[boolean](/docs/luau/booleans)

 |
|

[LoopRegion](#LoopRegion) :[NumberRange](/docs/reference/engine/datatypes/NumberRange)

 |
|

[PlaybackRegion](#PlaybackRegion) :[NumberRange](/docs/reference/engine/datatypes/NumberRange)

 |
|

[PlaybackSpeed](#PlaybackSpeed) :[number](/docs/luau/numbers)

 |
|

[TimeLength](#TimeLength) :[number](/docs/luau/numbers)

 |
|

[TimePosition](#TimePosition) :[number](/docs/luau/numbers)

 |
|

[Volume](#Volume) :[number](/docs/luau/numbers)

 |

Methods

|

[Cancel](#Cancel) (actionId :  [number](/docs/luau/numbers) ? ) :[boolean](/docs/luau/booleans)

 |
|

[GetConnectedWires](#GetConnectedWires) (pin :  [string](/docs/luau/strings) ) : {[Wire](/docs/reference/engine/classes/Wire) }

 |
|

[GetInputPins](#GetInputPins) () :[{any}](/docs/luau/tables#arrays)

 |
|

[GetOutputPins](#GetOutputPins) () :[{any}](/docs/luau/tables#arrays)

 |
|

[GetWaveformAsync](#GetWaveformAsync) (timeRange :  [NumberRange](/docs/reference/engine/datatypes/NumberRange) , samples :  [number](/docs/luau/numbers) ) :[{any}](/docs/luau/tables#arrays)

 |
|

[Play](#Play) (atTime :  [number](/docs/luau/numbers) ? ) :[number](/docs/luau/numbers) ?

 |
|

[Stop](#Stop) (atTime :  [number](/docs/luau/numbers) ? ) :[number](/docs/luau/numbers) ?

 |

Events

|

[Ended](#Ended) () :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |
|

[Looped](#Looped) () :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |
|

[WiringChanged](#WiringChanged) (connected :  [boolean](/docs/luau/booleans) , pin :  [string](/docs/luau/strings) , wire :  [Wire](/docs/reference/engine/classes/Wire) , instance :  [Instance](/docs/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

Outputting Audio to Device

```

local audioPlayer: AudioPlayer = Instance.new("AudioPlayer")

audioPlayer.Parent = workspace

audioPlayer.AssetId = "rbxassetid://9112854440"

local deviceOutput = Instance.new("AudioDeviceOutput")

deviceOutput.Parent = workspace

local wire = Instance.new("Wire")

wire.Parent = workspace

wire.SourceInstance = audioPlayer

wire.TargetInstance = deviceOutput

audioPlayer:Play()

```

---

API Reference

Properties

Asset

Read Parallel

Capabilities: Audio

AudioPlayer.Asset : ContentId

Provide feedback

---

AssetId

Deprecated

Show details

---

AudioContent

Read Parallel

Capabilities: Audio

AudioPlayer.AudioContent :[Content](/docs/reference/engine/datatypes/Content)

Provide feedback

---

AutoLoad

Read Parallel

Capabilities: Audio

AudioPlayer.AutoLoad :[boolean](/docs/luau/booleans)

Provide feedback

---

AutoPlay

Read Parallel

Capabilities: Audio

AudioPlayer.AutoPlay :[boolean](/docs/luau/booleans)

Provide feedback

---

IsPlaying

Roblox Security

Read Parallel

Capabilities: Audio

AudioPlayer.IsPlaying :[boolean](/docs/luau/booleans)

Provide feedback

---

IsReady

Read Only

Not Replicated

Read Parallel

Capabilities: Audio

AudioPlayer.IsReady :[boolean](/docs/luau/booleans)

Provide feedback

---

Looping

Read Parallel

Capabilities: Audio

AudioPlayer.Looping :[boolean](/docs/luau/booleans)

Provide feedback

---

LoopRegion

Read Parallel

Capabilities: Audio

AudioPlayer.LoopRegion :[NumberRange](/docs/reference/engine/datatypes/NumberRange)

Provide feedback

---

PlaybackRegion

Read Parallel

Capabilities: Audio

AudioPlayer.PlaybackRegion :[NumberRange](/docs/reference/engine/datatypes/NumberRange)

Provide feedback

---

PlaybackSpeed

Read Parallel

Capabilities: Audio

AudioPlayer.PlaybackSpeed :[number](/docs/luau/numbers)

Provide feedback

---

TimeLength

Read Only

Not Replicated

Read Parallel

Capabilities: Audio

AudioPlayer.TimeLength :[number](/docs/luau/numbers)

Provide feedback

---

TimePosition

Read Parallel

Capabilities: Audio

AudioPlayer.TimePosition :[number](/docs/luau/numbers)

Provide feedback

---

Volume

Read Parallel

Capabilities: Audio

AudioPlayer.Volume :[number](/docs/luau/numbers)

Provide feedback

---

Methods

Cancel

Capabilities: Audio

AudioPlayer:Cancel (actionId :[number](/docs/luau/numbers) ? ) :[boolean](/docs/luau/booleans)

Parameters

|

actionId :[number](/docs/luau/numbers) ?

 |

Returns

[boolean](/docs/luau/booleans)

Provide feedback

---

GetConnectedWires

Capabilities: Audio

AudioPlayer:GetConnectedWires (pin :[string](/docs/luau/strings) ) : {[Wire](/docs/reference/engine/classes/Wire) }

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

AudioPlayer:GetInputPins () :[{any}](/docs/luau/tables#arrays)

Returns

[{any}](/docs/luau/tables#arrays)

Provide feedback

---

GetOutputPins

Capabilities: Audio

AudioPlayer:GetOutputPins () :[{any}](/docs/luau/tables#arrays)

Returns

[{any}](/docs/luau/tables#arrays)

Provide feedback

---

GetWaveformAsync

Yields

Capabilities: Audio

AudioPlayer:GetWaveformAsync (

timeRange :[NumberRange](/docs/reference/engine/datatypes/NumberRange) , samples :[number](/docs/luau/numbers)

) :[{any}](/docs/luau/tables#arrays)

Parameters

|

timeRange :[NumberRange](/docs/reference/engine/datatypes/NumberRange)

 |
|

samples :[number](/docs/luau/numbers)

 |

Returns

[{any}](/docs/luau/tables#arrays)

Provide feedback

---

Play

Capabilities: Audio

AudioPlayer:Play (atTime :[number](/docs/luau/numbers) ? ) :[number](/docs/luau/numbers) ?

Parameters

|

atTime :[number](/docs/luau/numbers) ?

 |

Returns

[number](/docs/luau/numbers) ?

Provide feedback

---

Stop

Capabilities: Audio

AudioPlayer:Stop (atTime :[number](/docs/luau/numbers) ? ) :[number](/docs/luau/numbers) ?

Parameters

|

atTime :[number](/docs/luau/numbers) ?

 |

Returns

[number](/docs/luau/numbers) ?

Provide feedback

---

Events

Ended

Capabilities: Audio

AudioPlayer.Ended () :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Provide feedback

---

Looped

Capabilities: Audio

AudioPlayer.Looped () :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Provide feedback

---

WiringChanged

Capabilities: Audio

AudioPlayer.WiringChanged (

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

AudioPlayer

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[Asset](#Asset)

[AssetId](#AssetId)

[AudioContent](#AudioContent)

[AutoLoad](#AutoLoad)

[AutoPlay](#AutoPlay)

[IsPlaying](#IsPlaying)

[IsReady](#IsReady)

[Looping](#Looping)

[LoopRegion](#LoopRegion)

[PlaybackRegion](#PlaybackRegion)

[PlaybackSpeed](#PlaybackSpeed)

[TimeLength](#TimeLength)

[TimePosition](#TimePosition)

[Volume](#Volume)

[Methods](#methods)

[Cancel()](#Cancel)

[GetConnectedWires()](#GetConnectedWires)

[GetInputPins()](#GetInputPins)

[GetOutputPins()](#GetOutputPins)

[GetWaveformAsync()](#GetWaveformAsync)

[Play()](#Play)

[Stop()](#Stop)

[Events](#events)

[Ended](#Ended)

[Looped](#Looped)

[WiringChanged](#WiringChanged)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
