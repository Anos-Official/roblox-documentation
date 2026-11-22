<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/VideoPlayer -->

VideoPlayer | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [VideoPlayer](/docs/nl-nl/reference/engine/classes/VideoPlayer)

Nederlands

Feedback

Engine-klasse

VideoPlayer

Niet doorzoekbaar

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/VideoPlayer)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[AutoLoadInStudio](#AutoLoadInStudio) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |
|

[AutoPlayInStudio](#AutoPlayInStudio) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[IsLoaded](#IsLoaded) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[IsPlaying](#IsPlaying) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[Looping](#Looping) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[MaximumResolution](#MaximumResolution) :[Enum.VideoSampleSize](/docs/nl-nl/reference/engine/enums/VideoSampleSize)

 |
|

[PlaybackSpeed](#PlaybackSpeed) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Resolution](#Resolution) :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

[TimeLength](#TimeLength) :[number](/docs/nl-nl/luau/numbers)

 |
|

[TimePosition](#TimePosition) :[number](/docs/nl-nl/luau/numbers)

 |
|

[VideoContent](#VideoContent) :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

 |
|

[Volume](#Volume) :[number](/docs/nl-nl/luau/numbers)

 |

Methoden

|

[GetConnectedWires](#GetConnectedWires) (pin :  [string](/docs/nl-nl/luau/strings) ) : {[Wire](/docs/nl-nl/reference/engine/classes/Wire) }

 |
|

[GetInputPins](#GetInputPins) () :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[GetOutputPins](#GetOutputPins) () :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[LoadAsync](#LoadAsync) () :[Enum.AssetFetchStatus](/docs/nl-nl/reference/engine/enums/AssetFetchStatus)

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

Evenementen

|

[DidEnd](#DidEnd) () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[DidLoop](#DidLoop) () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[PlayFailed](#PlayFailed) (error :  [Enum.AssetFetchStatus](/docs/nl-nl/reference/engine/enums/AssetFetchStatus) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[WiringChanged](#WiringChanged) (connected :  [boolean](/docs/nl-nl/luau/booleans) , pin :  [string](/docs/nl-nl/luau/strings) , wire :  [Wire](/docs/nl-nl/reference/engine/classes/Wire) , instance :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Videospeler (Serverzijde)

```

-- Dit moet in een "Script" staan met RunContext ingesteld op "Legacy" of "Server"

-- Maak waar de video op wordt weergegeven

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

-- Maak waar een video asset vandaan komt

local videoSource = Instance.new("VideoPlayer")

videoSource.VideoContent = Content.fromUri("rbxassetid://5608359401")

videoSource.Looping = true

videoSource.Parent = videoScreenPart

-- Maak waar de audio van de video vandaan komt

local speakerPart = Instance.new("Part")

speakerPart.Anchored = true

speakerPart.Parent = workspace

local audioEmitter = Instance.new("AudioEmitter")

audioEmitter.Parent = speakerPart

-- Maak en verbind draden zodat de video visueel wordt weergegeven en audio uitzendt

local videoWire = Instance.new("Wire")

videoWire.SourceInstance = videoSource

videoWire.TargetInstance = videoDisplay

videoWire.Parent = videoSource

local audioWire = Instance.new("Wire")

audioWire.SourceInstance = videoSource

audioWire.TargetInstance = audioEmitter

audioWire.Parent = videoSource

-- Speel de video af

-- Opmerking: Het afspelen van een video op de server garandeert niet dat deze is geladen of gesynchroniseerd voor alle clients, afspelen op de client heeft de voorkeur

videoSource:Play()

```

Videospeler (Client Side)

```

local videoSource = Instance.new("VideoPlayer")

videoSource.VideoContent = Content.fromUri("rbxassetid://5608359401")

videoSource.Parent = script.Parent

-- Speel de video af nadat deze is geladen

videoSource:GetPropertyChangedSignal("IsLoaded"):Connect(function()

	if videoSource.IsLoaded then

		print("Video is geladen, start afspelen over 2 seconden.")

		wait(2)

		videoSource:Play()

	end

end)

-- Laad de video om deze klaar te hebben wanneer we het nodig hebben

videoSource:LoadAsync()

wait(5)

-- Ontlaad de video om middelen te besparen

videoSource:Unload()

```

---

API-referentie

Eigenschappen

AutoLoadInStudio

Niet gerepliceerd

Niet scriptbaar

Roblox-scriptbeveiliging

Parallel lezen

Mogelijkheden: Audio, UI

VideoPlayer.AutoLoadInStudio :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

AutoPlayInStudio

Niet gerepliceerd

Niet scriptbaar

Roblox-scriptbeveiliging

Parallel lezen

Mogelijkheden: Audio, UI

VideoPlayer.AutoPlayInStudio :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

IsLoaded

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Audio, UI

VideoPlayer.IsLoaded :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

IsPlaying

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Audio, UI

VideoPlayer.IsPlaying :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Looping

Parallel lezen

Mogelijkheden: Audio, UI

VideoPlayer.Looping :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

MaximumResolution

Verborgen

Parallel lezen

Mogelijkheden: Audio, UI, InternalTest

VideoPlayer.MaximumResolution :[Enum.VideoSampleSize](/docs/nl-nl/reference/engine/enums/VideoSampleSize)

Feedback geven

---

PlaybackSpeed

Parallel lezen

Mogelijkheden: Audio, UI

VideoPlayer.PlaybackSpeed :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Resolution

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Audio, UI

VideoPlayer.Resolution :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Feedback geven

---

TimeLength

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Audio, UI

VideoPlayer.TimeLength :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

TimePosition

Parallel lezen

Mogelijkheden: Audio, UI

VideoPlayer.TimePosition :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

VideoContent

Parallel lezen

Mogelijkheden: Audio, UI

VideoPlayer.VideoContent :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

Feedback geven

---

Volume

Parallel lezen

Mogelijkheden: Audio, UI

VideoPlayer.Volume :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Methoden

GetConnectedWires

Mogelijkheden: Audio, UI

VideoPlayer:GetConnectedWires (pin :[string](/docs/nl-nl/luau/strings) ) : {[Wire](/docs/nl-nl/reference/engine/classes/Wire) }

Parameters

|

pin :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

{[Wire](/docs/nl-nl/reference/engine/classes/Wire) }

Feedback geven

---

GetInputPins

Mogelijkheden: Audio, UI

VideoPlayer:GetInputPins () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

GetOutputPins

Mogelijkheden: Audio, UI

VideoPlayer:GetOutputPins () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

LoadAsync

Opbrengst

Mogelijkheden: Audio, UI

VideoPlayer:LoadAsync () :[Enum.AssetFetchStatus](/docs/nl-nl/reference/engine/enums/AssetFetchStatus)

Teruggaves

[Enum.AssetFetchStatus](/docs/nl-nl/reference/engine/enums/AssetFetchStatus)

Feedback geven

---

Pause

Mogelijkheden: Audio, UI

VideoPlayer:Pause () : ()

Teruggaves

()

Feedback geven

---

Play

Mogelijkheden: Audio, UI

VideoPlayer:Play () : ()

Teruggaves

()

Feedback geven

---

Unload

Mogelijkheden: Audio, UI

VideoPlayer:Unload () : ()

Teruggaves

()

Feedback geven

---

Evenementen

DidEnd

Mogelijkheden: Audio, UI

VideoPlayer.DidEnd () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Feedback geven

---

DidLoop

Mogelijkheden: Audio, UI

VideoPlayer.DidLoop () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Feedback geven

---

PlayFailed

Mogelijkheden: Audio, UI

VideoPlayer.PlayFailed (error :[Enum.AssetFetchStatus](/docs/nl-nl/reference/engine/enums/AssetFetchStatus) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

error :[Enum.AssetFetchStatus](/docs/nl-nl/reference/engine/enums/AssetFetchStatus)

 |

Feedback geven

---

WiringChanged

Mogelijkheden: Audio, UI

VideoPlayer.WiringChanged (

connected :[boolean](/docs/nl-nl/luau/booleans) , pin :[string](/docs/nl-nl/luau/strings) , wire :[Wire](/docs/nl-nl/reference/engine/classes/Wire) , instance :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

connected :[boolean](/docs/nl-nl/luau/booleans)

 |
|

pin :[string](/docs/nl-nl/luau/strings)

 |
|

wire :[Wire](/docs/nl-nl/reference/engine/classes/Wire)

 |
|

instance :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Feedback geven

---

Ga naar

▼

VideoPlayer

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

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

[Methoden](#methods)

[GetConnectedWires()](#GetConnectedWires)

[GetInputPins()](#GetInputPins)

[GetOutputPins()](#GetOutputPins)

[LoadAsync()](#LoadAsync)

[Pause()](#Pause)

[Play()](#Play)

[Unload()](#Unload)

[Evenementen](#events)

[DidEnd](#DidEnd)

[DidLoop](#DidLoop)

[PlayFailed](#PlayFailed)

[WiringChanged](#WiringChanged)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
