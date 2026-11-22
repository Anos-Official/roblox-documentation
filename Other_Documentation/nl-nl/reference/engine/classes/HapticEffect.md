<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/HapticEffect -->

HapticEffect | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [HapticEffect](/docs/nl-nl/reference/engine/classes/HapticEffect)

Nederlands

Feedback

Engine-klasse

HapticEffect

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/HapticEffect)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Looped](#Looped) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |
|

[Position](#Position) :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |
|

[Radius](#Radius) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Type](#Type) :[Enum.HapticEffectType](/docs/nl-nl/reference/engine/enums/HapticEffectType)

 |

Methoden

|

[Play](#Play) () : ()

 |
|

[GetWaveformKeys](#GetWaveformKeys) () :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[SetWaveformKeys](#SetWaveformKeys) (keys :  [{any}](/docs/nl-nl/luau/tables#arrays) ) : ()

 |
|

[Stop](#Stop) () : ()

 |

Evenementen

|

[Ended](#Ended) () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

Looped

Parallel lezen

Mogelijkheden: Input

HapticEffect.Looped :[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

Lus

```

local Workspace = game:GetService("Workspace")

local effect = Instance.new("HapticEffect")

effect.Type = Enum.HapticEffectType.GameplayExplosion

effect.Looped = true

effect.Parent = Workspace

-- Start de haptische effect

effect:Play()

-- Stop het effect na twee seconden

task.wait(2)

effect:Stop()

```

Feedback geven

---

Position

Parallel lezen

Mogelijkheden: Input

HapticEffect.Position :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Codevoorbeelden

Positie

```

local Workspace = game:GetService("Workspace")

local effect = Instance.new("HapticEffect")

-- Stel de positie en straal van impact in

effect.Position = Vector3.new(0.5, 0.5, 0)

effect.Radius = 1

effect.Parent = Workspace

effect:Play()

```

Feedback geven

---

Radius

Parallel lezen

Mogelijkheden: Input

HapticEffect.Radius :[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

Straal

```

local Workspace = game:GetService("Workspace")

local effect = Instance.new("HapticEffect")

-- Stel de positie en straal van impact in

effect.Position = Vector3.new(0.5, 0.5, 0)

effect.Radius = 1

effect.Parent = Workspace

-- Speel het haptische effect af

effect:Play()

```

Feedback geven

---

Type

Parallel lezen

Mogelijkheden: Input

HapticEffect.Type :[Enum.HapticEffectType](/docs/nl-nl/reference/engine/enums/HapticEffectType)

Feedback geven

---

Methoden

Play

Mogelijkheden: Input

HapticEffect:Play () : ()

Teruggaves

()

Codevoorbeelden

Spelen

```

local Workspace = game:GetService("Workspace")

local effect = Instance.new("HapticEffect")

effect.Type = Enum.HapticEffectType.GameplayExplosion

effect.Parent = Workspace

-- Speel het haptische effect af

effect:Play()

```

Feedback geven

---

GetWaveformKeys

Mogelijkheden: Input

HapticEffect:GetWaveformKeys () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Codevoorbeelden

Krijg Golfvorm Sleutels

```

local Workspace = game:GetService("Workspace")

local effect = Instance.new("HapticEffect")

effect.Type = Enum.HapticEffectType.Custom

effect.Parent = Workspace

effect:SetWaveformKeys({

	FloatCurveKey.new(0, 0.4, Enum.KeyInterpolationMode.Linear),

	FloatCurveKey.new(200, 1.0, Enum.KeyInterpolationMode.Linear),

})

-- Lees de golfvorm terug, schaal het naar halve sterkte, en schrijf het terug.

-- Tijd is in milliseconden; waarde is van 0 (geen haptiek) tot 1 (volledige intensiteit).

local keys = effect:GetWaveformKeys()

for i, key in keys do

	keys[i] = FloatCurveKey.new(key.Time, key.Value * 0.5, key.Interpolation)

end

effect:SetWaveformKeys(keys)

```

Feedback geven

---

SetWaveformKeys

Mogelijkheden: Input

HapticEffect:SetWaveformKeys (keys :[{any}](/docs/nl-nl/luau/tables#arrays) ) : ()

Parameters

|

keys :[{any}](/docs/nl-nl/luau/tables#arrays)

 |

Teruggaves

()

Codevoorbeelden

Stel Golfvorm Sleutels In

```

local Workspace = game:GetService("Workspace")

local effect = Instance.new("HapticEffect")

-- Stel het effecttype in op aangepast om een golfvorm te definiëren

effect.Type = Enum.HapticEffectType.Custom

effect.Parent = Workspace

-- Definieer de aangepaste golfvormcurve via een tabel van FloatCurveKeys

-- Tijdwaarden zijn in milliseconden; waarden variëren van 0 (geen haptiek) tot 1 (volledige intensiteit)

local rampUpWaveform = {

	FloatCurveKey.new(0, 0.3, Enum.KeyInterpolationMode.Linear),

	FloatCurveKey.new(100, 0.4, Enum.KeyInterpolationMode.Linear),

	FloatCurveKey.new(300, 0.8, Enum.KeyInterpolationMode.Linear),

	FloatCurveKey.new(400, 1.0, Enum.KeyInterpolationMode.Linear)

}

-- Stel de golfvorm in via de methode van het effect

effect:SetWaveformKeys(rampUpWaveform)

```

Feedback geven

---

Stop

Mogelijkheden: Input

HapticEffect:Stop () : ()

Teruggaves

()

Codevoorbeelden

Stop

```

local Workspace = game:GetService("Workspace")

local effect = Instance.new("HapticEffect")

effect.Type = Enum.HapticEffectType.GameplayExplosion

effect.Looped = true

effect.Parent = Workspace

-- Start het haptische effect

effect:Play()

-- Stop het effect na twee seconden

task.wait(2)

effect:Stop()

```

Feedback geven

---

Evenementen

Ended

Mogelijkheden: Input

HapticEffect.Ended () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Feedback geven

---

Ga naar

▼

HapticEffect

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[Looped](#Looped)

[Position](#Position)

[Radius](#Radius)

[Type](#Type)

[Methoden](#methods)

[Play()](#Play)

[GetWaveformKeys()](#GetWaveformKeys)

[SetWaveformKeys()](#SetWaveformKeys)

[Stop()](#Stop)

[Evenementen](#events)

[Ended](#Ended)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
