<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/AudioChannelMixer -->

AudioChannelMixer | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [AudioChannelMixer](/docs/nl-nl/reference/engine/classes/AudioChannelMixer)

Nederlands

Feedback

Engine-klasse

AudioChannelMixer

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/AudioChannelMixer)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Layout](#Layout) :[Enum.AudioChannelLayout](/docs/nl-nl/reference/engine/enums/AudioChannelLayout)

 |
| --- | --- |

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

Kanalen Splitsen & Mixen

```

local Workspace = game:GetService("Workspace")

local function wireUp(source: Instance, target: Instance, sourceName: string?, targetName: string?)

	local wire = Instance.new("Wire", source)

	wire.SourceInstance = source

	wire.TargetInstance = target

	if sourceName then

		wire.SourceName = sourceName

	end

	if targetName then

		wire.TargetName = targetName

	end

	return wire

end

local listener = Instance.new("AudioListener")

listener.Parent = Workspace.CurrentCamera

local output = Instance.new("AudioDeviceOutput")

output.Parent = Workspace

local splitter = Instance.new("AudioChannelSplitter")

splitter.Parent = Workspace

local mixer = Instance.new("AudioChannelMixer")

mixer.Parent = Workspace

-- Stuur wat de luisteraar hoort naar een splitter en stuur een mix naar de uiteindelijke output

wireUp(listener, splitter)

wireUp(mixer, output)

-- Stel zowel de splitter als mixer in om een quadrophonische indeling te gebruiken

splitter.Layout = Enum.AudioChannelLayout.Quad

mixer.Layout = Enum.AudioChannelLayout.Quad

-- Geef elk van de vier kanalen zijn eigen toonhoogteverschuiver

local frontLeft = Instance.new("AudioPitchShifter")

frontLeft.Name = "Voor Links"

frontLeft.Pitch = 1.25

frontLeft.Parent = Workspace

local backLeft = Instance.new("AudioPitchShifter")

backLeft.Name = "Achter Links"

backLeft.Pitch = 0.5

backLeft.Parent = Workspace

local frontRight = Instance.new("AudioPitchShifter")

frontRight.Name = "Voor Rechts"

frontRight.Pitch = 1.5

frontRight.Parent = Workspace

local backRight = Instance.new("AudioPitchShifter")

backRight.Name = "Achter Rechts"

backRight.Pitch = 0.75

backRight.Parent = Workspace

wireUp(splitter, frontLeft, "Links")

wireUp(splitter, backLeft, "AchterLinks")

wireUp(splitter, frontRight, "Rechts")

wireUp(splitter, backRight, "AchterRechts")

wireUp(frontLeft, mixer, nil, "Links")

wireUp(backLeft, mixer, nil, "AchterLinks")

wireUp(frontRight, mixer, nil, "Rechts")

wireUp(backRight, mixer, nil, "AchterRechts")

-- Configureer een onderdeel om audio uit te zenden

local part = Instance.new("Part")

part.Shape = Enum.PartType.Ball

part.Size = Vector3.new(4, 4, 4)

part.Material = Enum.Material.SmoothPlastic

part.CastShadow = false

part.Position = Vector3.new(0, 4, -12)

part.Anchored = true

part.Parent = Workspace

local analyzer = Instance.new("AudioAnalyzer")

analyzer.Parent = part

local emitter = Instance.new("AudioEmitter")

emitter.Parent = part

local assetPlayer = Instance.new("AudioPlayer")

assetPlayer.Looping = true

assetPlayer.Asset = "rbxassetid://97799489309320"

assetPlayer.Parent = emitter

wireUp(assetPlayer, emitter)

wireUp(assetPlayer, analyzer)

-- Begin met het afspelen van de audio

assetPlayer:Play()

-- Pas de kleur van het onderdeel aan terwijl de audio speelt

while true do

	local peak = math.sqrt(analyzer.PeakLevel)

	part.Color = Color3.new(peak, peak, peak)

	task.wait()

end

```

---

API-referentie

Eigenschappen

Layout

Parallel lezen

Mogelijkheden: Audio

AudioChannelMixer.Layout :[Enum.AudioChannelLayout](/docs/nl-nl/reference/engine/enums/AudioChannelLayout)

Feedback geven

---

Methoden

GetConnectedWires

Mogelijkheden: Audio

AudioChannelMixer:GetConnectedWires (pin :[string](/docs/nl-nl/luau/strings) ) : {[Wire](/docs/nl-nl/reference/engine/classes/Wire) }

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

AudioChannelMixer:GetInputPins () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

GetOutputPins

Mogelijkheden: Audio

AudioChannelMixer:GetOutputPins () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

Evenementen

WiringChanged

Mogelijkheden: Audio

AudioChannelMixer.WiringChanged (

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

AudioChannelMixer

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[Layout](#Layout)

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
