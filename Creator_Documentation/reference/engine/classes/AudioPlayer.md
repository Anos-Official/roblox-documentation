<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/AudioPlayer -->

AudioPlayer | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/AudioPlayer.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [AudioPlayer](/docs/en-us/reference/engine/classes/AudioPlayer)

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

[AssetId](#AssetId) :[string](/docs/en-us/luau/strings)

Deprecated

 |
|

[AudioContent](#AudioContent) :[Content](/docs/en-us/reference/engine/datatypes/Content)

 |
|

[AutoLoad](#AutoLoad) :[boolean](/docs/en-us/luau/booleans)

 |
|

[AutoPlay](#AutoPlay) :[boolean](/docs/en-us/luau/booleans)

 |
|

[IsPlaying](#IsPlaying) :[boolean](/docs/en-us/luau/booleans)

 |
|

[IsReady](#IsReady) :[boolean](/docs/en-us/luau/booleans)

 |
|

[Looping](#Looping) :[boolean](/docs/en-us/luau/booleans)

 |
|

[LoopRegion](#LoopRegion) :[NumberRange](/docs/en-us/reference/engine/datatypes/NumberRange)

 |
|

[PlaybackRegion](#PlaybackRegion) :[NumberRange](/docs/en-us/reference/engine/datatypes/NumberRange)

 |
|

[PlaybackSpeed](#PlaybackSpeed) :[number](/docs/en-us/luau/numbers)

 |
|

[TimeLength](#TimeLength) :[number](/docs/en-us/luau/numbers)

 |
|

[TimePosition](#TimePosition) :[number](/docs/en-us/luau/numbers)

 |
|

[Volume](#Volume) :[number](/docs/en-us/luau/numbers)

 |

Methods

|

[Cancel](#Cancel) (actionId :  [number](/docs/en-us/luau/numbers) ? ) :[boolean](/docs/en-us/luau/booleans)

 |
|

[GetConnectedWires](#GetConnectedWires) (pin :  [string](/docs/en-us/luau/strings) ) : {[Wire](/docs/en-us/reference/engine/classes/Wire) }

 |
|

[GetInputPins](#GetInputPins) () :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[GetOutputPins](#GetOutputPins) () :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[GetWaveformAsync](#GetWaveformAsync) (timeRange :  [NumberRange](/docs/en-us/reference/engine/datatypes/NumberRange) , samples :  [number](/docs/en-us/luau/numbers) ) :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[Play](#Play) (atTime :  [number](/docs/en-us/luau/numbers) ? ) :[number](/docs/en-us/luau/numbers) ?

 |
|

[Stop](#Stop) (atTime :  [number](/docs/en-us/luau/numbers) ? ) :[number](/docs/en-us/luau/numbers) ?

 |

Events

|

[Ended](#Ended) () :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[Looped](#Looped) () :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[WiringChanged](#WiringChanged) (connected :  [boolean](/docs/en-us/luau/booleans) , pin :  [string](/docs/en-us/luau/strings) , wire :  [Wire](/docs/en-us/reference/engine/classes/Wire) , instance :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

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

AudioPlayer.AudioContent :[Content](/docs/en-us/reference/engine/datatypes/Content)

Provide feedback

---

AutoLoad

Read Parallel

Capabilities: Audio

AudioPlayer.AutoLoad :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

AutoPlay

Read Parallel

Capabilities: Audio

AudioPlayer.AutoPlay :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

IsPlaying

Roblox Security

Read Parallel

Capabilities: Audio

AudioPlayer.IsPlaying :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

IsReady

Read Only

Not Replicated

Read Parallel

Capabilities: Audio

AudioPlayer.IsReady :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

Looping

Read Parallel

Capabilities: Audio

AudioPlayer.Looping :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

LoopRegion

Read Parallel

Capabilities: Audio

AudioPlayer.LoopRegion :[NumberRange](/docs/en-us/reference/engine/datatypes/NumberRange)

Provide feedback

---

PlaybackRegion

Read Parallel

Capabilities: Audio

AudioPlayer.PlaybackRegion :[NumberRange](/docs/en-us/reference/engine/datatypes/NumberRange)

Provide feedback

---

PlaybackSpeed

Read Parallel

Capabilities: Audio

AudioPlayer.PlaybackSpeed :[number](/docs/en-us/luau/numbers)

Provide feedback

---

TimeLength

Read Only

Not Replicated

Read Parallel

Capabilities: Audio

AudioPlayer.TimeLength :[number](/docs/en-us/luau/numbers)

Provide feedback

---

TimePosition

Read Parallel

Capabilities: Audio

AudioPlayer.TimePosition :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Volume

Read Parallel

Capabilities: Audio

AudioPlayer.Volume :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Methods

Cancel

Capabilities: Audio

AudioPlayer:Cancel (actionId :[number](/docs/en-us/luau/numbers) ? ) :[boolean](/docs/en-us/luau/booleans)

Parameters

|

actionId :[number](/docs/en-us/luau/numbers) ?

 |

Returns

[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

GetConnectedWires

Capabilities: Audio

AudioPlayer:GetConnectedWires (pin :[string](/docs/en-us/luau/strings) ) : {[Wire](/docs/en-us/reference/engine/classes/Wire) }

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

AudioPlayer:GetInputPins () :[{any}](/docs/en-us/luau/tables#arrays)

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

GetOutputPins

Capabilities: Audio

AudioPlayer:GetOutputPins () :[{any}](/docs/en-us/luau/tables#arrays)

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

GetWaveformAsync

Yields

Capabilities: Audio

AudioPlayer:GetWaveformAsync (

timeRange :[NumberRange](/docs/en-us/reference/engine/datatypes/NumberRange) , samples :[number](/docs/en-us/luau/numbers)

) :[{any}](/docs/en-us/luau/tables#arrays)

Parameters

|

timeRange :[NumberRange](/docs/en-us/reference/engine/datatypes/NumberRange)

 |
|

samples :[number](/docs/en-us/luau/numbers)

 |

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

Play

Capabilities: Audio

AudioPlayer:Play (atTime :[number](/docs/en-us/luau/numbers) ? ) :[number](/docs/en-us/luau/numbers) ?

Parameters

|

atTime :[number](/docs/en-us/luau/numbers) ?

 |

Returns

[number](/docs/en-us/luau/numbers) ?

Provide feedback

---

Stop

Capabilities: Audio

AudioPlayer:Stop (atTime :[number](/docs/en-us/luau/numbers) ? ) :[number](/docs/en-us/luau/numbers) ?

Parameters

|

atTime :[number](/docs/en-us/luau/numbers) ?

 |

Returns

[number](/docs/en-us/luau/numbers) ?

Provide feedback

---

Events

Ended

Capabilities: Audio

AudioPlayer.Ended () :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Provide feedback

---

Looped

Capabilities: Audio

AudioPlayer.Looped () :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Provide feedback

---

WiringChanged

Capabilities: Audio

AudioPlayer.WiringChanged (

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
