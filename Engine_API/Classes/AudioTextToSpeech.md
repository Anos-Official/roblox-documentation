<!-- Source: https://create.roblox.com/docs/reference/engine/classes/AudioTextToSpeech -->

AudioTextToSpeech | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/AudioTextToSpeech.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [AudioTextToSpeech](/docs/reference/engine/classes/AudioTextToSpeech)

English

Feedback

Engine Class

AudioTextToSpeech

---

## Summary

Properties

|

[AutoLocalize](#AutoLocalize) :[boolean](/docs/luau/booleans)

 |
| --- | --- |
|

[IsLoaded](#IsLoaded) :[boolean](/docs/luau/booleans)

 |
|

[IsPlaying](#IsPlaying) :[boolean](/docs/luau/booleans)

 |
|

[Looping](#Looping) :[boolean](/docs/luau/booleans)

 |
|

[Pitch](#Pitch) :[number](/docs/luau/numbers)

 |
|

[PlaybackSpeed](#PlaybackSpeed) :[number](/docs/luau/numbers)

 |
|

[Speed](#Speed) :[number](/docs/luau/numbers)

 |
|

[Text](#Text) :[string](/docs/luau/strings)

 |
|

[TimeLength](#TimeLength) :[number](/docs/luau/numbers)

 |
|

[TimePosition](#TimePosition) :[number](/docs/luau/numbers)

 |
|

[VoiceId](#VoiceId) :[string](/docs/luau/strings)

 |
|

[Volume](#Volume) :[number](/docs/luau/numbers)

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
|

[GetWaveformAsync](#GetWaveformAsync) (timeRange :  [NumberRange](/docs/reference/engine/datatypes/NumberRange) , samples :  [number](/docs/luau/numbers) ) :[{any}](/docs/luau/tables#arrays)

 |
|

[LoadAsync](#LoadAsync) () :[Enum.AssetFetchStatus](/docs/reference/engine/enums/AssetFetchStatus)

 |
|

[Pause](#Pause) () : ()

 |
|

[Play](#Play) () : ()

 |
|

[Unload](#Unload) () : ()

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

Outputting Text as Speech

```

local audioTextToSpeech: AudioTextToSpeech = Instance.new("AudioTextToSpeech")

audioTextToSpeech.Parent = workspace

audioTextToSpeech.Text = "Hello! Converting text into speech is fun!"

audioTextToSpeech.VoiceId = "1"

local deviceOutput = Instance.new("AudioDeviceOutput")

deviceOutput.Parent = workspace

local wire = Instance.new("Wire")

wire.Parent = workspace

wire.SourceInstance = audioTextToSpeech

wire.TargetInstance = deviceOutput

local count = 0

local connection = nil

connection = audioTextToSpeech.Ended:Connect(function()

	audioTextToSpeech.Text = "I can count to " .. count .. " because I am very smart"

	audioTextToSpeech.VoiceId = "2"

	audioTextToSpeech.TimePosition = 0

	audioTextToSpeech:Play()

	count += 1

	if count > 10 then

		connection:Disconnect()

	end

end)

audioTextToSpeech:Play()

```

---

API Reference

Properties

AutoLocalize

Read Parallel

Capabilities: Audio

AudioTextToSpeech.AutoLocalize :[boolean](/docs/luau/booleans)

Provide feedback

---

IsLoaded

Read Only

Not Replicated

Read Parallel

Capabilities: Audio

AudioTextToSpeech.IsLoaded :[boolean](/docs/luau/booleans)

Provide feedback

---

IsPlaying

Roblox Security

Read Parallel

Capabilities: Audio

AudioTextToSpeech.IsPlaying :[boolean](/docs/luau/booleans)

Provide feedback

---

Looping

Read Parallel

Capabilities: Audio

AudioTextToSpeech.Looping :[boolean](/docs/luau/booleans)

Provide feedback

---

Pitch

Read Parallel

Capabilities: Audio

AudioTextToSpeech.Pitch :[number](/docs/luau/numbers)

Provide feedback

---

PlaybackSpeed

Read Parallel

Capabilities: Audio

AudioTextToSpeech.PlaybackSpeed :[number](/docs/luau/numbers)

Provide feedback

---

Speed

Read Parallel

Capabilities: Audio

AudioTextToSpeech.Speed :[number](/docs/luau/numbers)

Provide feedback

---

Text

Read Parallel

Capabilities: Audio

AudioTextToSpeech.Text :[string](/docs/luau/strings)

Provide feedback

---

TimeLength

Read Only

Not Replicated

Read Parallel

Capabilities: Audio

AudioTextToSpeech.TimeLength :[number](/docs/luau/numbers)

Provide feedback

---

TimePosition

Read Parallel

Capabilities: Audio

AudioTextToSpeech.TimePosition :[number](/docs/luau/numbers)

Provide feedback

---

VoiceId

Read Parallel

Capabilities: Audio

AudioTextToSpeech.VoiceId :[string](/docs/luau/strings)

Provide feedback

---

Volume

Read Parallel

Capabilities: Audio

AudioTextToSpeech.Volume :[number](/docs/luau/numbers)

Provide feedback

---

Methods

GetConnectedWires

Capabilities: Audio

AudioTextToSpeech:GetConnectedWires (pin :[string](/docs/luau/strings) ) : {[Wire](/docs/reference/engine/classes/Wire) }

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

AudioTextToSpeech:GetInputPins () :[{any}](/docs/luau/tables#arrays)

Returns

[{any}](/docs/luau/tables#arrays)

Provide feedback

---

GetOutputPins

Capabilities: Audio

AudioTextToSpeech:GetOutputPins () :[{any}](/docs/luau/tables#arrays)

Returns

[{any}](/docs/luau/tables#arrays)

Provide feedback

---

GetWaveformAsync

Yields

Capabilities: Audio

AudioTextToSpeech:GetWaveformAsync (

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

LoadAsync

Yields

Capabilities: Audio

AudioTextToSpeech:LoadAsync () :[Enum.AssetFetchStatus](/docs/reference/engine/enums/AssetFetchStatus)

Returns

[Enum.AssetFetchStatus](/docs/reference/engine/enums/AssetFetchStatus)

Provide feedback

---

Pause

Capabilities: Audio

AudioTextToSpeech:Pause () : ()

Returns

()

Provide feedback

---

Play

Capabilities: Audio

AudioTextToSpeech:Play () : ()

Returns

()

Provide feedback

---

Unload

Capabilities: Audio

AudioTextToSpeech:Unload () : ()

Returns

()

Provide feedback

---

Events

Ended

Capabilities: Audio

AudioTextToSpeech.Ended () :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Provide feedback

---

Looped

Capabilities: Audio

AudioTextToSpeech.Looped () :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Provide feedback

---

WiringChanged

Capabilities: Audio

AudioTextToSpeech.WiringChanged (

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

AudioTextToSpeech

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[AutoLocalize](#AutoLocalize)

[IsLoaded](#IsLoaded)

[IsPlaying](#IsPlaying)

[Looping](#Looping)

[Pitch](#Pitch)

[PlaybackSpeed](#PlaybackSpeed)

[Speed](#Speed)

[Text](#Text)

[TimeLength](#TimeLength)

[TimePosition](#TimePosition)

[VoiceId](#VoiceId)

[Volume](#Volume)

[Methods](#methods)

[GetConnectedWires()](#GetConnectedWires)

[GetInputPins()](#GetInputPins)

[GetOutputPins()](#GetOutputPins)

[GetWaveformAsync()](#GetWaveformAsync)

[LoadAsync()](#LoadAsync)

[Pause()](#Pause)

[Play()](#Play)

[Unload()](#Unload)

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
