<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/AudioPlayer -->

AudioPlayer | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [AudioPlayer](/docs/nl-nl/reference/engine/classes/AudioPlayer)

Nederlands

Feedback

Engine-klasse

AudioPlayer

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/AudioPlayer)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Asset](#Asset) : ContentId

 |
| --- | --- |
|

[AssetId](#AssetId) :[string](/docs/nl-nl/luau/strings)

Verouderd

 |
|

[AudioContent](#AudioContent) :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

 |
|

[AutoLoad](#AutoLoad) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[AutoPlay](#AutoPlay) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[IsPlaying](#IsPlaying) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[IsReady](#IsReady) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[Looping](#Looping) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[LoopRegion](#LoopRegion) :[NumberRange](/docs/nl-nl/reference/engine/datatypes/NumberRange)

 |
|

[PlaybackRegion](#PlaybackRegion) :[NumberRange](/docs/nl-nl/reference/engine/datatypes/NumberRange)

 |
|

[PlaybackSpeed](#PlaybackSpeed) :[number](/docs/nl-nl/luau/numbers)

 |
|

[TimeLength](#TimeLength) :[number](/docs/nl-nl/luau/numbers)

 |
|

[TimePosition](#TimePosition) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Volume](#Volume) :[number](/docs/nl-nl/luau/numbers)

 |

Methoden

|

[Cancel](#Cancel) (actionId :  [number](/docs/nl-nl/luau/numbers) ? ) :[boolean](/docs/nl-nl/luau/booleans)

 |
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

[GetWaveformAsync](#GetWaveformAsync) (timeRange :  [NumberRange](/docs/nl-nl/reference/engine/datatypes/NumberRange) , samples :  [number](/docs/nl-nl/luau/numbers) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[Play](#Play) (atTime :  [number](/docs/nl-nl/luau/numbers) ? ) :[number](/docs/nl-nl/luau/numbers) ?

 |
|

[Stop](#Stop) (atTime :  [number](/docs/nl-nl/luau/numbers) ? ) :[number](/docs/nl-nl/luau/numbers) ?

 |

Evenementen

|

[Ended](#Ended) () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[Looped](#Looped) () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[WiringChanged](#WiringChanged) (connected :  [boolean](/docs/nl-nl/luau/booleans) , pin :  [string](/docs/nl-nl/luau/strings) , wire :  [Wire](/docs/nl-nl/reference/engine/classes/Wire) , instance :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Audio naar Apparaat Afspelen

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

API-referentie

Eigenschappen

Asset

Parallel lezen

Mogelijkheden: Audio

AudioPlayer.Asset : ContentId

Feedback geven

---

AssetId

Verouderd

Details weergeven

---

AudioContent

Parallel lezen

Mogelijkheden: Audio

AudioPlayer.AudioContent :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

Feedback geven

---

AutoLoad

Parallel lezen

Mogelijkheden: Audio

AudioPlayer.AutoLoad :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

AutoPlay

Parallel lezen

Mogelijkheden: Audio

AudioPlayer.AutoPlay :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

IsPlaying

Roblox Security

Parallel lezen

Mogelijkheden: Audio

AudioPlayer.IsPlaying :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

IsReady

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Audio

AudioPlayer.IsReady :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Looping

Parallel lezen

Mogelijkheden: Audio

AudioPlayer.Looping :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

LoopRegion

Parallel lezen

Mogelijkheden: Audio

AudioPlayer.LoopRegion :[NumberRange](/docs/nl-nl/reference/engine/datatypes/NumberRange)

Feedback geven

---

PlaybackRegion

Parallel lezen

Mogelijkheden: Audio

AudioPlayer.PlaybackRegion :[NumberRange](/docs/nl-nl/reference/engine/datatypes/NumberRange)

Feedback geven

---

PlaybackSpeed

Parallel lezen

Mogelijkheden: Audio

AudioPlayer.PlaybackSpeed :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

TimeLength

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Audio

AudioPlayer.TimeLength :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

TimePosition

Parallel lezen

Mogelijkheden: Audio

AudioPlayer.TimePosition :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Volume

Parallel lezen

Mogelijkheden: Audio

AudioPlayer.Volume :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Methoden

Cancel

Mogelijkheden: Audio

AudioPlayer:Cancel (actionId :[number](/docs/nl-nl/luau/numbers) ? ) :[boolean](/docs/nl-nl/luau/booleans)

Parameters

|

actionId :[number](/docs/nl-nl/luau/numbers) ?

 |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

GetConnectedWires

Mogelijkheden: Audio

AudioPlayer:GetConnectedWires (pin :[string](/docs/nl-nl/luau/strings) ) : {[Wire](/docs/nl-nl/reference/engine/classes/Wire) }

Parameters

|

pin :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

{[Wire](/docs/nl-nl/reference/engine/classes/Wire) }

Feedback geven

---

GetInputPins

Mogelijkheden: Audio

AudioPlayer:GetInputPins () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

GetOutputPins

Mogelijkheden: Audio

AudioPlayer:GetOutputPins () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

GetWaveformAsync

Opbrengst

Mogelijkheden: Audio

AudioPlayer:GetWaveformAsync (

timeRange :[NumberRange](/docs/nl-nl/reference/engine/datatypes/NumberRange) , samples :[number](/docs/nl-nl/luau/numbers)

) :[{any}](/docs/nl-nl/luau/tables#arrays)

Parameters

|

timeRange :[NumberRange](/docs/nl-nl/reference/engine/datatypes/NumberRange)

 |
|

samples :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

Play

Mogelijkheden: Audio

AudioPlayer:Play (atTime :[number](/docs/nl-nl/luau/numbers) ? ) :[number](/docs/nl-nl/luau/numbers) ?

Parameters

|

atTime :[number](/docs/nl-nl/luau/numbers) ?

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers) ?

Feedback geven

---

Stop

Mogelijkheden: Audio

AudioPlayer:Stop (atTime :[number](/docs/nl-nl/luau/numbers) ? ) :[number](/docs/nl-nl/luau/numbers) ?

Parameters

|

atTime :[number](/docs/nl-nl/luau/numbers) ?

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers) ?

Feedback geven

---

Evenementen

Ended

Mogelijkheden: Audio

AudioPlayer.Ended () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Feedback geven

---

Looped

Mogelijkheden: Audio

AudioPlayer.Looped () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Feedback geven

---

WiringChanged

Mogelijkheden: Audio

AudioPlayer.WiringChanged (

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

AudioPlayer

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

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

[Methoden](#methods)

[Cancel()](#Cancel)

[GetConnectedWires()](#GetConnectedWires)

[GetInputPins()](#GetInputPins)

[GetOutputPins()](#GetOutputPins)

[GetWaveformAsync()](#GetWaveformAsync)

[Play()](#Play)

[Stop()](#Stop)

[Evenementen](#events)

[Ended](#Ended)

[Looped](#Looped)

[WiringChanged](#WiringChanged)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
