<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/VideoPlayer -->

VideoPlayer | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/VideoPlayer.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [VideoPlayer](/docs/en-us/reference/engine/classes/VideoPlayer)

English

Feedback

Engine Class

VideoPlayer

Not Browsable

---

## Summary

Properties

|

[AutoLoadInStudio](#AutoLoadInStudio) :[boolean](/docs/en-us/luau/booleans)

 |
| --- | --- |
|

[AutoPlayInStudio](#AutoPlayInStudio) :[boolean](/docs/en-us/luau/booleans)

 |
|

[IsLoaded](#IsLoaded) :[boolean](/docs/en-us/luau/booleans)

 |
|

[IsPlaying](#IsPlaying) :[boolean](/docs/en-us/luau/booleans)

 |
|

[Looping](#Looping) :[boolean](/docs/en-us/luau/booleans)

 |
|

[MaximumResolution](#MaximumResolution) :[Enum.VideoSampleSize](/docs/en-us/reference/engine/enums/VideoSampleSize)

 |
|

[PlaybackSpeed](#PlaybackSpeed) :[number](/docs/en-us/luau/numbers)

 |
|

[Resolution](#Resolution) :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

 |
|

[TimeLength](#TimeLength) :[number](/docs/en-us/luau/numbers)

 |
|

[TimePosition](#TimePosition) :[number](/docs/en-us/luau/numbers)

 |
|

[VideoContent](#VideoContent) :[Content](/docs/en-us/reference/engine/datatypes/Content)

 |
|

[Volume](#Volume) :[number](/docs/en-us/luau/numbers)

 |

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
|

[LoadAsync](#LoadAsync) () :[Enum.AssetFetchStatus](/docs/en-us/reference/engine/enums/AssetFetchStatus)

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

[DidEnd](#DidEnd) () :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[DidLoop](#DidLoop) () :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[PlayFailed](#PlayFailed) (error :  [Enum.AssetFetchStatus](/docs/en-us/reference/engine/enums/AssetFetchStatus) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[WiringChanged](#WiringChanged) (connected :  [boolean](/docs/en-us/luau/booleans) , pin :  [string](/docs/en-us/luau/strings) , wire :  [Wire](/docs/en-us/reference/engine/classes/Wire) , instance :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Video Player (Server Side)

```

-- This should be in a "Script" with RunContext set to "Legacy" or "Server"

-- Create what the video is displayed on

local videoScreenPart = Instance.new("Part")

videoScreenPart.Anchored = true

videoScreenPart.Size = Vector3.new(12, 6, 1)

videoScreenPart.CFrame = CFrame.new(0, 5, 0)

videoScreenPart.Parent = workspace

local videoScreenUI = Instance.new("SurfaceGui")

videoScreenUI.Parent = videoScreenPart

local videoDisplay = Instance.new("VideoDisplay")

videoDisplay.Size = UDim2.new(1, 0, 1, 0)

videoDisplay.Parent = videoScreenUI

-- Create where a video asset originates from

local videoSource = Instance.new("VideoPlayer")

videoSource.VideoContent = Content.fromUri("rbxassetid://5608359401")

videoSource.Looping = true

videoSource.Parent = videoScreenPart

-- Create where the video's audio emits from

local speakerPart = Instance.new("Part")

speakerPart.Anchored = true

speakerPart.Parent = workspace

local audioEmitter = Instance.new("AudioEmitter")

audioEmitter.Parent = speakerPart

-- Create and connect wires so that the video visually renders and emits audio

local videoWire = Instance.new("Wire")

videoWire.SourceInstance = videoSource

videoWire.TargetInstance = videoDisplay

videoWire.Parent = videoSource

local audioWire = Instance.new("Wire")

audioWire.SourceInstance = videoSource

audioWire.TargetInstance = audioEmitter

audioWire.Parent = videoSource

-- Play the video

-- Note: Playing a video on the server does not guarantee it is loaded or synced for all clients, playing on the client is preferred

videoSource:Play()

```

Video Player (Client Side)

```

local videoSource = Instance.new("VideoPlayer")

videoSource.VideoContent = Content.fromUri("rbxassetid://5608359401")

videoSource.Parent = script.Parent

-- Play the video after it has loaded

videoSource:GetPropertyChangedSignal("IsLoaded"):Connect(function()

	if videoSource.IsLoaded then

		print("Video has loaded, starting playback in 2 seconds.")

		wait(2)

		videoSource:Play()

	end

end)

-- Load the video to have it ready when we need it

videoSource:LoadAsync()

wait(5)

-- Unload the video to save resources

videoSource:Unload()

```

---

API Reference

Properties

AutoLoadInStudio

Not Replicated

Not Scriptable

Roblox Script Security

Read Parallel

Capabilities: Audio, UI

VideoPlayer.AutoLoadInStudio :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

AutoPlayInStudio

Not Replicated

Not Scriptable

Roblox Script Security

Read Parallel

Capabilities: Audio, UI

VideoPlayer.AutoPlayInStudio :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

IsLoaded

Read Only

Not Replicated

Read Parallel

Capabilities: Audio, UI

VideoPlayer.IsLoaded :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

IsPlaying

Read Only

Not Replicated

Read Parallel

Capabilities: Audio, UI

VideoPlayer.IsPlaying :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

Looping

Read Parallel

Capabilities: Audio, UI

VideoPlayer.Looping :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

MaximumResolution

Hidden

Read Parallel

Capabilities: Audio, UI, InternalTest

VideoPlayer.MaximumResolution :[Enum.VideoSampleSize](/docs/en-us/reference/engine/enums/VideoSampleSize)

Provide feedback

---

PlaybackSpeed

Read Parallel

Capabilities: Audio, UI

VideoPlayer.PlaybackSpeed :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Resolution

Read Only

Not Replicated

Read Parallel

Capabilities: Audio, UI

VideoPlayer.Resolution :[Vector2](/docs/en-us/reference/engine/datatypes/Vector2)

Provide feedback

---

TimeLength

Read Only

Not Replicated

Read Parallel

Capabilities: Audio, UI

VideoPlayer.TimeLength :[number](/docs/en-us/luau/numbers)

Provide feedback

---

TimePosition

Read Parallel

Capabilities: Audio, UI

VideoPlayer.TimePosition :[number](/docs/en-us/luau/numbers)

Provide feedback

---

VideoContent

Read Parallel

Capabilities: Audio, UI

VideoPlayer.VideoContent :[Content](/docs/en-us/reference/engine/datatypes/Content)

Provide feedback

---

Volume

Read Parallel

Capabilities: Audio, UI

VideoPlayer.Volume :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Methods

GetConnectedWires

Capabilities: Audio, UI

VideoPlayer:GetConnectedWires (pin :[string](/docs/en-us/luau/strings) ) : {[Wire](/docs/en-us/reference/engine/classes/Wire) }

Parameters

|

pin :[string](/docs/en-us/luau/strings)

 |

Returns

{[Wire](/docs/en-us/reference/engine/classes/Wire) }

Provide feedback

---

GetInputPins

Capabilities: Audio, UI

VideoPlayer:GetInputPins () :[{any}](/docs/en-us/luau/tables#arrays)

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

GetOutputPins

Capabilities: Audio, UI

VideoPlayer:GetOutputPins () :[{any}](/docs/en-us/luau/tables#arrays)

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

LoadAsync

Yields

Capabilities: Audio, UI

VideoPlayer:LoadAsync () :[Enum.AssetFetchStatus](/docs/en-us/reference/engine/enums/AssetFetchStatus)

Returns

[Enum.AssetFetchStatus](/docs/en-us/reference/engine/enums/AssetFetchStatus)

Provide feedback

---

Pause

Capabilities: Audio, UI

VideoPlayer:Pause () : ()

Returns

()

Provide feedback

---

Play

Capabilities: Audio, UI

VideoPlayer:Play () : ()

Returns

()

Provide feedback

---

Unload

Capabilities: Audio, UI

VideoPlayer:Unload () : ()

Returns

()

Provide feedback

---

Events

DidEnd

Capabilities: Audio, UI

VideoPlayer.DidEnd () :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Provide feedback

---

DidLoop

Capabilities: Audio, UI

VideoPlayer.DidLoop () :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Provide feedback

---

PlayFailed

Capabilities: Audio, UI

VideoPlayer.PlayFailed (error :[Enum.AssetFetchStatus](/docs/en-us/reference/engine/enums/AssetFetchStatus) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

error :[Enum.AssetFetchStatus](/docs/en-us/reference/engine/enums/AssetFetchStatus)

 |

Provide feedback

---

WiringChanged

Capabilities: Audio, UI

VideoPlayer.WiringChanged (

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

VideoPlayer

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[AutoLoadInStudio](#AutoLoadInStudio)

[AutoPlayInStudio](#AutoPlayInStudio)

[IsLoaded](#IsLoaded)

[IsPlaying](#IsPlaying)

[Looping](#Looping)

[MaximumResolution](#MaximumResolution)

[PlaybackSpeed](#PlaybackSpeed)

[Resolution](#Resolution)

[TimeLength](#TimeLength)

[TimePosition](#TimePosition)

[VideoContent](#VideoContent)

[Volume](#Volume)

[Methods](#methods)

[GetConnectedWires()](#GetConnectedWires)

[GetInputPins()](#GetInputPins)

[GetOutputPins()](#GetOutputPins)

[LoadAsync()](#LoadAsync)

[Pause()](#Pause)

[Play()](#Play)

[Unload()](#Unload)

[Events](#events)

[DidEnd](#DidEnd)

[DidLoop](#DidLoop)

[PlayFailed](#PlayFailed)

[WiringChanged](#WiringChanged)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
