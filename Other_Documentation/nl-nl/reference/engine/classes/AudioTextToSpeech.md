<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/AudioTextToSpeech -->

AudioTextToSpeech | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [AudioTextToSpeech](/docs/nl-nl/reference/engine/classes/AudioTextToSpeech)

Nederlands

Feedback

Engine-klasse

AudioTextToSpeech

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/AudioTextToSpeech)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[AutoLocalize](#AutoLocalize) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |
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

[Pitch](#Pitch) :[number](/docs/nl-nl/luau/numbers)

 |
|

[PlaybackSpeed](#PlaybackSpeed) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Speed](#Speed) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Text](#Text) :[string](/docs/nl-nl/luau/strings)

 |
|

[TimeLength](#TimeLength) :[number](/docs/nl-nl/luau/numbers)

 |
|

[TimePosition](#TimePosition) :[number](/docs/nl-nl/luau/numbers)

 |
|

[VoiceId](#VoiceId) :[string](/docs/nl-nl/luau/strings)

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

[GetWaveformAsync](#GetWaveformAsync) (timeRange :  [NumberRange](/docs/nl-nl/reference/engine/datatypes/NumberRange) , samples :  [number](/docs/nl-nl/luau/numbers) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

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

Tekst als Spraak Uitvoeren

```

local audioTextToSpeech: AudioTextToSpeech = Instance.new("AudioTextToSpeech")

audioTextToSpeech.Parent = workspace

audioTextToSpeech.Text = "Hallo! Tekst omzetten in spraak is leuk!"

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

	audioTextToSpeech.Text = "Ik kan tot " .. count .. " tellen omdat ik heel slim ben"

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

API-referentie

Eigenschappen

AutoLocalize

Parallel lezen

Mogelijkheden: Audio

AudioTextToSpeech.AutoLocalize :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

IsLoaded

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Audio

AudioTextToSpeech.IsLoaded :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

IsPlaying

Roblox Security

Parallel lezen

Mogelijkheden: Audio

AudioTextToSpeech.IsPlaying :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Looping

Parallel lezen

Mogelijkheden: Audio

AudioTextToSpeech.Looping :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Pitch

Parallel lezen

Mogelijkheden: Audio

AudioTextToSpeech.Pitch :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

PlaybackSpeed

Parallel lezen

Mogelijkheden: Audio

AudioTextToSpeech.PlaybackSpeed :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Speed

Parallel lezen

Mogelijkheden: Audio

AudioTextToSpeech.Speed :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Text

Parallel lezen

Mogelijkheden: Audio

AudioTextToSpeech.Text :[string](/docs/nl-nl/luau/strings)

Feedback geven

---

TimeLength

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Audio

AudioTextToSpeech.TimeLength :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

TimePosition

Parallel lezen

Mogelijkheden: Audio

AudioTextToSpeech.TimePosition :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

VoiceId

Parallel lezen

Mogelijkheden: Audio

AudioTextToSpeech.VoiceId :[string](/docs/nl-nl/luau/strings)

Feedback geven

---

Volume

Parallel lezen

Mogelijkheden: Audio

AudioTextToSpeech.Volume :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Methoden

GetConnectedWires

Mogelijkheden: Audio

AudioTextToSpeech:GetConnectedWires (pin :[string](/docs/nl-nl/luau/strings) ) : {[Wire](/docs/nl-nl/reference/engine/classes/Wire) }

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

AudioTextToSpeech:GetInputPins () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

GetOutputPins

Mogelijkheden: Audio

AudioTextToSpeech:GetOutputPins () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

GetWaveformAsync

Opbrengst

Mogelijkheden: Audio

AudioTextToSpeech:GetWaveformAsync (

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

LoadAsync

Opbrengst

Mogelijkheden: Audio

AudioTextToSpeech:LoadAsync () :[Enum.AssetFetchStatus](/docs/nl-nl/reference/engine/enums/AssetFetchStatus)

Teruggaves

[Enum.AssetFetchStatus](/docs/nl-nl/reference/engine/enums/AssetFetchStatus)

Feedback geven

---

Pause

Mogelijkheden: Audio

AudioTextToSpeech:Pause () : ()

Teruggaves

()

Feedback geven

---

Play

Mogelijkheden: Audio

AudioTextToSpeech:Play () : ()

Teruggaves

()

Feedback geven

---

Unload

Mogelijkheden: Audio

AudioTextToSpeech:Unload () : ()

Teruggaves

()

Feedback geven

---

Evenementen

Ended

Mogelijkheden: Audio

AudioTextToSpeech.Ended () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Feedback geven

---

Looped

Mogelijkheden: Audio

AudioTextToSpeech.Looped () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Feedback geven

---

WiringChanged

Mogelijkheden: Audio

AudioTextToSpeech.WiringChanged (

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

AudioTextToSpeech

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

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

[Methoden](#methods)

[GetConnectedWires()](#GetConnectedWires)

[GetInputPins()](#GetInputPins)

[GetOutputPins()](#GetOutputPins)

[GetWaveformAsync()](#GetWaveformAsync)

[LoadAsync()](#LoadAsync)

[Pause()](#Pause)

[Play()](#Play)

[Unload()](#Unload)

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
