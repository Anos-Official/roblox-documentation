<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/AudioRecorder -->

AudioRecorder | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [AudioRecorder](/docs/nl-nl/reference/engine/classes/AudioRecorder)

Nederlands

Feedback

Engine-klasse

AudioRecorder

Niet doorzoekbaar

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/AudioRecorder)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[IsRecording](#IsRecording) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |
|

[TimeLength](#TimeLength) :[number](/docs/nl-nl/luau/numbers)

 |

Methoden

|

[CanRecordAsync](#CanRecordAsync) () :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[Clear](#Clear) () : ()

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

[GetTemporaryContent](#GetTemporaryContent) () :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

 |
|

[GetUnrecordableInstancesAsync](#GetUnrecordableInstancesAsync) () : {[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) }

 |
|

[RecordAsync](#RecordAsync) () : ()

 |
|

[Stop](#Stop) () : ()

 |

Evenementen

|

[WiringChanged](#WiringChanged) (connected :  [boolean](/docs/nl-nl/luau/booleans) , pin :  [string](/docs/nl-nl/luau/strings) , wire :  [Wire](/docs/nl-nl/reference/engine/classes/Wire) , instance :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Audio Recorder

```

local Workspace = game:GetService("Workspace")

local audioRecorder = Instance.new("AudioRecorder")

audioRecorder.Parent = Workspace

local audioPlayer = Instance.new("AudioPlayer")

audioPlayer.Asset = "rbxassetid://5829815715"

audioPlayer.Volume = 0.8

audioPlayer.Parent = Workspace

-- Verbind AudioPlayer met de AudioRecorder

local wire1 = Instance.new("Wire")

wire1.SourceInstance = audioPlayer

wire1.TargetInstance = audioRecorder

wire1.Parent = audioRecorder

-- Er is geen exacte manier om te bepalen wanneer de audiobuffer binnenkomt om de opname goed te starten

-- Opname zal vooraf lege stilte bevatten in vergelijking met het originele bestand

audioPlayer:Play()

audioRecorder:RecordAsync() -- Begin met opnemen van de AudioPlayer

print("Opnemen...")

task.wait(5)

audioRecorder:Stop() -- Stop met opnemen

print("Opname gestopt!")

audioPlayer:Stop()

audioPlayer.TimePosition = 0

-- Maak output om de resultaten te beluisteren

local audioOutput = Instance.new("AudioDeviceOutput")

audioOutput.Parent = Workspace

local wire2 = Instance.new("Wire")

wire2.SourceInstance = audioPlayer

wire2.TargetInstance = audioOutput

wire2.Parent = audioOutput

-- Verkrijg de opgenomen inhoud en speel deze af in de AudioPlayer

local resultUri = audioRecorder:GetTemporaryContent().Uri

audioPlayer.Asset = resultUri

if not audioPlayer.IsReady then

	audioPlayer:GetPropertyChangedSignal("IsReady"):Wait()

end

audioPlayer:Play()

```

---

API-referentie

Eigenschappen

IsRecording

Roblox Security

Parallel lezen

Mogelijkheden: Audio

AudioRecorder.IsRecording :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

TimeLength

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Audio

AudioRecorder.TimeLength :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Methoden

CanRecordAsync

Opbrengst

Mogelijkheden: Audio

AudioRecorder:CanRecordAsync () :[boolean](/docs/nl-nl/luau/booleans)

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Clear

Mogelijkheden: Audio

AudioRecorder:Clear () : ()

Teruggaves

()

Feedback geven

---

GetConnectedWires

Mogelijkheden: Audio

AudioRecorder:GetConnectedWires (pin :[string](/docs/nl-nl/luau/strings) ) : {[Wire](/docs/nl-nl/reference/engine/classes/Wire) }

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

AudioRecorder:GetInputPins () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

GetOutputPins

Mogelijkheden: Audio

AudioRecorder:GetOutputPins () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

GetTemporaryContent

Mogelijkheden: Audio

AudioRecorder:GetTemporaryContent () :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

Teruggaves

[Content](/docs/nl-nl/reference/engine/datatypes/Content)

Feedback geven

---

GetUnrecordableInstancesAsync

Opbrengst

Mogelijkheden: Audio

AudioRecorder:GetUnrecordableInstancesAsync () : {[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) }

Teruggaves

{[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) }

Feedback geven

---

RecordAsync

Opbrengst

Mogelijkheden: Audio

AudioRecorder:RecordAsync () : ()

Teruggaves

()

Feedback geven

---

Stop

Mogelijkheden: Audio

AudioRecorder:Stop () : ()

Teruggaves

()

Feedback geven

---

Evenementen

WiringChanged

Mogelijkheden: Audio

AudioRecorder.WiringChanged (

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

AudioRecorder

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[IsRecording](#IsRecording)

[TimeLength](#TimeLength)

[Methoden](#methods)

[CanRecordAsync()](#CanRecordAsync)

[Clear()](#Clear)

[GetConnectedWires()](#GetConnectedWires)

[GetInputPins()](#GetInputPins)

[GetOutputPins()](#GetOutputPins)

[GetTemporaryContent()](#GetTemporaryContent)

[GetUnrecordableInstancesAsync()](#GetUnrecordableInstancesAsync)

[RecordAsync()](#RecordAsync)

[Stop()](#Stop)

[Evenementen](#events)

[WiringChanged](#WiringChanged)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
