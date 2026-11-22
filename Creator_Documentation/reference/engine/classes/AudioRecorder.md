<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/AudioRecorder -->

AudioRecorder | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/AudioRecorder.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [AudioRecorder](/docs/en-us/reference/engine/classes/AudioRecorder)

English

Feedback

Engine Class

AudioRecorder

Not Browsable

---

## Summary

Properties

|

[IsRecording](#IsRecording) :[boolean](/docs/en-us/luau/booleans)

 |
| --- | --- |
|

[TimeLength](#TimeLength) :[number](/docs/en-us/luau/numbers)

 |

Methods

|

[CanRecordAsync](#CanRecordAsync) () :[boolean](/docs/en-us/luau/booleans)

 |
|

[Clear](#Clear) () : ()

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

[GetTemporaryContent](#GetTemporaryContent) () :[Content](/docs/en-us/reference/engine/datatypes/Content)

 |
|

[GetUnrecordableInstancesAsync](#GetUnrecordableInstancesAsync) () : {[Instance](/docs/en-us/reference/engine/datatypes/Instance) }

 |
|

[RecordAsync](#RecordAsync) () : ()

 |
|

[Stop](#Stop) () : ()

 |

Events

|

[WiringChanged](#WiringChanged) (connected :  [boolean](/docs/en-us/luau/booleans) , pin :  [string](/docs/en-us/luau/strings) , wire :  [Wire](/docs/en-us/reference/engine/classes/Wire) , instance :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Audio Recorder

```

local Workspace = game:GetService("Workspace")

local audioRecorder = Instance.new("AudioRecorder")

audioRecorder.Parent = Workspace

local audioPlayer = Instance.new("AudioPlayer")

audioPlayer.Asset = "rbxassetid://5829815715"

audioPlayer.Volume = 0.8

audioPlayer.Parent = Workspace

-- Wire AudioPlayer into the AudioRecorder

local wire1 = Instance.new("Wire")

wire1.SourceInstance = audioPlayer

wire1.TargetInstance = audioRecorder

wire1.Parent = audioRecorder

-- There is no exact way to determine when audio buffer enters in to trigger the recording properly

-- Recording will have pre-head empty silence compared to the original asset

audioPlayer:Play()

audioRecorder:RecordAsync() -- Start recording the AudioPlayer

print("Recording...")

task.wait(5)

audioRecorder:Stop() -- Stop recording

print("Stopped recording!")

audioPlayer:Stop()

audioPlayer.TimePosition = 0

-- Create output to listen the results

local audioOutput = Instance.new("AudioDeviceOutput")

audioOutput.Parent = Workspace

local wire2 = Instance.new("Wire")

wire2.SourceInstance = audioPlayer

wire2.TargetInstance = audioOutput

wire2.Parent = audioOutput

-- Get the recorded content and play it in the AudioPlayer

local resultUri = audioRecorder:GetTemporaryContent().Uri

audioPlayer.Asset = resultUri

if not audioPlayer.IsReady then

	audioPlayer:GetPropertyChangedSignal("IsReady"):Wait()

end

audioPlayer:Play()

```

---

API Reference

Properties

IsRecording

Roblox Security

Read Parallel

Capabilities: Audio

AudioRecorder.IsRecording :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

TimeLength

Read Only

Not Replicated

Read Parallel

Capabilities: Audio

AudioRecorder.TimeLength :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Methods

CanRecordAsync

Yields

Capabilities: Audio

AudioRecorder:CanRecordAsync () :[boolean](/docs/en-us/luau/booleans)

Returns

[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

Clear

Capabilities: Audio

AudioRecorder:Clear () : ()

Returns

()

Provide feedback

---

GetConnectedWires

Capabilities: Audio

AudioRecorder:GetConnectedWires (pin :[string](/docs/en-us/luau/strings) ) : {[Wire](/docs/en-us/reference/engine/classes/Wire) }

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

AudioRecorder:GetInputPins () :[{any}](/docs/en-us/luau/tables#arrays)

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

GetOutputPins

Capabilities: Audio

AudioRecorder:GetOutputPins () :[{any}](/docs/en-us/luau/tables#arrays)

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

GetTemporaryContent

Capabilities: Audio

AudioRecorder:GetTemporaryContent () :[Content](/docs/en-us/reference/engine/datatypes/Content)

Returns

[Content](/docs/en-us/reference/engine/datatypes/Content)

Provide feedback

---

GetUnrecordableInstancesAsync

Yields

Capabilities: Audio

AudioRecorder:GetUnrecordableInstancesAsync () : {[Instance](/docs/en-us/reference/engine/datatypes/Instance) }

Returns

{[Instance](/docs/en-us/reference/engine/datatypes/Instance) }

Provide feedback

---

RecordAsync

Yields

Capabilities: Audio

AudioRecorder:RecordAsync () : ()

Returns

()

Provide feedback

---

Stop

Capabilities: Audio

AudioRecorder:Stop () : ()

Returns

()

Provide feedback

---

Events

WiringChanged

Capabilities: Audio

AudioRecorder.WiringChanged (

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

AudioRecorder

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[IsRecording](#IsRecording)

[TimeLength](#TimeLength)

[Methods](#methods)

[CanRecordAsync()](#CanRecordAsync)

[Clear()](#Clear)

[GetConnectedWires()](#GetConnectedWires)

[GetInputPins()](#GetInputPins)

[GetOutputPins()](#GetOutputPins)

[GetTemporaryContent()](#GetTemporaryContent)

[GetUnrecordableInstancesAsync()](#GetUnrecordableInstancesAsync)

[RecordAsync()](#RecordAsync)

[Stop()](#Stop)

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
