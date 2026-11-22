<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/AudioCompressor -->

AudioCompressor | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [AudioCompressor](/docs/nl-nl/reference/engine/classes/AudioCompressor)

Nederlands

Feedback

Engine-klasse

AudioCompressor

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/AudioCompressor)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Attack](#Attack) :[number](/docs/nl-nl/luau/numbers)

 |
| --- | --- |
|

[Bypass](#Bypass) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[MakeupGain](#MakeupGain) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Ratio](#Ratio) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Release](#Release) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Threshold](#Threshold) :[number](/docs/nl-nl/luau/numbers)

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

Evenementen

|

[WiringChanged](#WiringChanged) (connected :  [boolean](/docs/nl-nl/luau/booleans) , pin :  [string](/docs/nl-nl/luau/strings) , wire :  [Wire](/docs/nl-nl/reference/engine/classes/Wire) , instance :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Sidechain Compressie

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

API-referentie

Eigenschappen

Attack

Parallel lezen

Mogelijkheden: Audio

AudioCompressor.Attack :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Bypass

Parallel lezen

Mogelijkheden: Audio

AudioCompressor.Bypass :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

MakeupGain

Parallel lezen

Mogelijkheden: Audio

AudioCompressor.MakeupGain :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Ratio

Parallel lezen

Mogelijkheden: Audio

AudioCompressor.Ratio :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Release

Parallel lezen

Mogelijkheden: Audio

AudioCompressor.Release :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Threshold

Parallel lezen

Mogelijkheden: Audio

AudioCompressor.Threshold :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Methoden

GetConnectedWires

Mogelijkheden: Audio

AudioCompressor:GetConnectedWires (pin :[string](/docs/nl-nl/luau/strings) ) : {[Wire](/docs/nl-nl/reference/engine/classes/Wire) }

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

AudioCompressor:GetInputPins () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

GetOutputPins

Mogelijkheden: Audio

AudioCompressor:GetOutputPins () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

Evenementen

WiringChanged

Mogelijkheden: Audio

AudioCompressor.WiringChanged (

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

AudioCompressor

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[Attack](#Attack)

[Bypass](#Bypass)

[MakeupGain](#MakeupGain)

[Ratio](#Ratio)

[Release](#Release)

[Threshold](#Threshold)

[Methoden](#methods)

[GetConnectedWires()](#GetConnectedWires)

[GetInputPins()](#GetInputPins)

[GetOutputPins()](#GetOutputPins)

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
