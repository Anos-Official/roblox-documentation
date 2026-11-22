<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/AudioFilter -->

AudioFilter | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [AudioFilter](/docs/nl-nl/reference/engine/classes/AudioFilter)

Nederlands

Feedback

Engine-klasse

AudioFilter

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/AudioFilter)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Bypass](#Bypass) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |
|

[FilterType](#FilterType) :[Enum.AudioFilterType](/docs/nl-nl/reference/engine/enums/AudioFilterType)

 |
|

[Frequency](#Frequency) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Gain](#Gain) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Q](#Q) :[number](/docs/nl-nl/luau/numbers)

 |

Methoden

|

[GetConnectedWires](#GetConnectedWires) (pin :  [string](/docs/nl-nl/luau/strings) ) : {[Wire](/docs/nl-nl/reference/engine/classes/Wire) }

 |
|

[GetGainAt](#GetGainAt) (frequency :  [number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers)

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

Emitter Filtering

```

-- Dit gaat ervan uit dat de workspace een Part bevat met een AudioEmitter en een AudioPlayer, en de camera heeft een AudioListener

local RunService = game:GetService("RunService")

local part: BasePart = workspace.Part

local camera: Camera = workspace.CurrentCamera

local audioPlayer: AudioPlayer = part.AudioPlayer

local audioEmitter: AudioEmitter = part.AudioEmitter

local audioListener: AudioListener = camera.AudioListener

local raycastParams = RaycastParams.new()

raycastParams.FilterDescendantsInstances = { audioEmitter.Parent }

raycastParams.FilterType = Enum.RaycastFilterType.Exclude

-- Maak een nieuwe AudioFilter

local filter: AudioFilter = Instance.new("AudioFilter")

filter.FilterType = Enum.AudioFilterType.Lowpass12dB

filter.Frequency = 22000

filter.Q = math.sqrt(2) / 2 -- Deze Q-waarde produceert een vlakke lowpass voor het 12dB hellingstype

filter.Parent = part

-- Plaats de AudioFilter tussen de speler en de emitter

local function wireTo(source: Instance, target: Instance): Wire

	local wire = Instance.new("Wire")

	wire.SourceInstance = source

	wire.TargetInstance = target

	wire.Parent = target

end

wireTo(audioPlayer, filter)

wireTo(filter, audioEmitter)

-- Werk de filter bij op basis van de posities van de emitter en listener

RunService.Heartbeat:Connect(function()

	local emitterPos: Vector3 = part.Position

	local listenerPos: Vector3 = camera.CFrame.Position

	local raycastResult = workspace:Raycast(emitterPos, (listenerPos - emitterPos), raycastParams)

	filter.Frequency = if raycastResult then 500 else 22000

end)

```

---

API-referentie

Eigenschappen

Bypass

Parallel lezen

Mogelijkheden: Audio

AudioFilter.Bypass :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

FilterType

Parallel lezen

Mogelijkheden: Audio

AudioFilter.FilterType :[Enum.AudioFilterType](/docs/nl-nl/reference/engine/enums/AudioFilterType)

Feedback geven

---

Frequency

Parallel lezen

Mogelijkheden: Audio

AudioFilter.Frequency :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Gain

Parallel lezen

Mogelijkheden: Audio

AudioFilter.Gain :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Q

Parallel lezen

Mogelijkheden: Audio

AudioFilter.Q :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Methoden

GetConnectedWires

Mogelijkheden: Audio

AudioFilter:GetConnectedWires (pin :[string](/docs/nl-nl/luau/strings) ) : {[Wire](/docs/nl-nl/reference/engine/classes/Wire) }

Parameters

|

pin :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

{[Wire](/docs/nl-nl/reference/engine/classes/Wire) }

Feedback geven

---

GetGainAt

Mogelijkheden: Audio

AudioFilter:GetGainAt (frequency :[number](/docs/nl-nl/luau/numbers) ) :[number](/docs/nl-nl/luau/numbers)

Parameters

|

frequency :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

GetInputPins

Mogelijkheden: Audio

AudioFilter:GetInputPins () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

GetOutputPins

Mogelijkheden: Audio

AudioFilter:GetOutputPins () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

Evenementen

WiringChanged

Mogelijkheden: Audio

AudioFilter.WiringChanged (

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

AudioFilter

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[Bypass](#Bypass)

[FilterType](#FilterType)

[Frequency](#Frequency)

[Gain](#Gain)

[Q](#Q)

[Methoden](#methods)

[GetConnectedWires()](#GetConnectedWires)

[GetGainAt()](#GetGainAt)

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
