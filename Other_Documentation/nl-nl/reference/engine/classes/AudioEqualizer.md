<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/AudioEqualizer -->

AudioEqualizer | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [AudioEqualizer](/docs/nl-nl/reference/engine/classes/AudioEqualizer)

Nederlands

Feedback

Engine-klasse

AudioEqualizer

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/AudioEqualizer)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Bypass](#Bypass) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |
|

[HighGain](#HighGain) :[number](/docs/nl-nl/luau/numbers)

 |
|

[LowGain](#LowGain) :[number](/docs/nl-nl/luau/numbers)

 |
|

[MidGain](#MidGain) :[number](/docs/nl-nl/luau/numbers)

 |
|

[MidRange](#MidRange) :[NumberRange](/docs/nl-nl/reference/engine/datatypes/NumberRange)

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

Listener Equalization

```

local function wireUp(source: Instance, target: Instance): Wire

	local wire = Instance.new("Wire")

	wire.Parent = target

	wire.SourceInstance = source

	wire.TargetInstance = target

	return wire

end

local function getCFrameFrom(inst: Instance): CFrame?

	local parent = inst.Parent

	if not parent then

		return nil

	elseif parent:IsA("Model") then

		return parent.WorldPivot

	elseif parent:IsA("BasePart") then

		return parent.CFrame

	elseif parent:IsA("Attachment") then

		return parent.WorldCFrame

	elseif parent:IsA("Camera") then

		return parent.CFrame

	else

		return nil

	end

end

local function rescale(value: number, oldRange: NumberRange, newRange: NumberRange): number

	local clamped = math.clamp(value, oldRange.Min, oldRange.Max)

	local normalized = clamped - oldRange.Min / (oldRange.Max - oldRange.Min)

	return normalized * (newRange.Max - newRange.Min) + newRange.Min

end

local assetPlayer = Instance.new("AudioPlayer")

assetPlayer.AssetId = "rbxassetid://142376088"

assetPlayer.Parent = workspace

local equalizer = Instance.new("AudioEqualizer")

equalizer.MidRange = NumberRange.new(400, 3000)

equalizer.Parent = workspace

local emitterPart = Instance.new("Part")

emitterPart.Anchored = true

emitterPart.Position = Vector3.new(0, 5, 0)

emitterPart.Parent = workspace

local emitter = Instance.new("AudioEmitter")

emitter.Parent = emitterPart

local listener = Instance.new("AudioListener")

listener.Parent = workspace.CurrentCamera

local output = Instance.new("AudioDeviceOutput")

output.Parent = workspace

wireUp(assetPlayer, equalizer)

wireUp(equalizer, emitter)

wireUp(listener, output)

assetPlayer.Looping = true

assetPlayer:Play()

while true do

	local emitterFrame = getCFrameFrom(emitter)

	local listenerFrame = getCFrameFrom(listener)

	if emitterFrame and listenerFrame then

		local towardEmitter = emitterFrame.Position - listenerFrame.Position

		local look = towardEmitter.Unit:Dot(listenerFrame.LookVector) -- varieert van [-1, 1]

		look = rescale(look, NumberRange.new(-1, 1), NumberRange.new(-20, 0))

		local distance = math.max(towardEmitter.Magnitude, 1)

		local rolloff = 1 / distance -- varieert van [0, 1]

		rolloff = rescale(rolloff, NumberRange.new(0, 1), NumberRange.new(-10, 10))

		equalizer.HighGain = look + rolloff

		equalizer.LowGain = rolloff

	end

	task.wait()

end

```

---

API-referentie

Eigenschappen

Bypass

Parallel lezen

Mogelijkheden: Audio

AudioEqualizer.Bypass :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

HighGain

Parallel lezen

Mogelijkheden: Audio

AudioEqualizer.HighGain :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

LowGain

Parallel lezen

Mogelijkheden: Audio

AudioEqualizer.LowGain :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

MidGain

Parallel lezen

Mogelijkheden: Audio

AudioEqualizer.MidGain :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

MidRange

Parallel lezen

Mogelijkheden: Audio

AudioEqualizer.MidRange :[NumberRange](/docs/nl-nl/reference/engine/datatypes/NumberRange)

Feedback geven

---

Methoden

GetConnectedWires

Mogelijkheden: Audio

AudioEqualizer:GetConnectedWires (pin :[string](/docs/nl-nl/luau/strings) ) : {[Wire](/docs/nl-nl/reference/engine/classes/Wire) }

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

AudioEqualizer:GetInputPins () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

GetOutputPins

Mogelijkheden: Audio

AudioEqualizer:GetOutputPins () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Feedback geven

---

Evenementen

WiringChanged

Mogelijkheden: Audio

AudioEqualizer.WiringChanged (

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

AudioEqualizer

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[Bypass](#Bypass)

[HighGain](#HighGain)

[LowGain](#LowGain)

[MidGain](#MidGain)

[MidRange](#MidRange)

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
