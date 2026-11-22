<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/HapticEffect -->

HapticEffect | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/HapticEffect.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [HapticEffect](/docs/en-us/reference/engine/classes/HapticEffect)

English

Feedback

Engine Class

HapticEffect

---

## Summary

Properties

|

[Looped](#Looped) :[boolean](/docs/en-us/luau/booleans)

 |
| --- | --- |
|

[Position](#Position) :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

 |
|

[Radius](#Radius) :[number](/docs/en-us/luau/numbers)

 |
|

[Type](#Type) :[Enum.HapticEffectType](/docs/en-us/reference/engine/enums/HapticEffectType)

 |

Methods

|

[Play](#Play) () : ()

 |
|

[GetWaveformKeys](#GetWaveformKeys) () :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[SetWaveformKeys](#SetWaveformKeys) (keys :  [{any}](/docs/en-us/luau/tables#arrays) ) : ()

 |
|

[Stop](#Stop) () : ()

 |

Events

|

[Ended](#Ended) () :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Properties

Looped

Read Parallel

Capabilities: Input

HapticEffect.Looped :[boolean](/docs/en-us/luau/booleans)

Code Samples

Looped

```

local Workspace = game:GetService("Workspace")

local effect = Instance.new("HapticEffect")

effect.Type = Enum.HapticEffectType.GameplayExplosion

effect.Looped = true

effect.Parent = Workspace

-- Start the haptic effect

effect:Play()

-- After two seconds, stop the effect

task.wait(2)

effect:Stop()

```

Provide feedback

---

Position

Read Parallel

Capabilities: Input

HapticEffect.Position :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Code Samples

Position

```

local Workspace = game:GetService("Workspace")

local effect = Instance.new("HapticEffect")

-- Set the position and radius of impact

effect.Position = Vector3.new(0.5, 0.5, 0)

effect.Radius = 1

effect.Parent = Workspace

effect:Play()

```

Provide feedback

---

Radius

Read Parallel

Capabilities: Input

HapticEffect.Radius :[number](/docs/en-us/luau/numbers)

Code Samples

Radius

```

local Workspace = game:GetService("Workspace")

local effect = Instance.new("HapticEffect")

-- Set the position and radius of impact

effect.Position = Vector3.new(0.5, 0.5, 0)

effect.Radius = 1

effect.Parent = Workspace

-- Play the haptic effect

effect:Play()

```

Provide feedback

---

Type

Read Parallel

Capabilities: Input

HapticEffect.Type :[Enum.HapticEffectType](/docs/en-us/reference/engine/enums/HapticEffectType)

Provide feedback

---

Methods

Play

Capabilities: Input

HapticEffect:Play () : ()

Returns

()

Code Samples

Play

```

local Workspace = game:GetService("Workspace")

local effect = Instance.new("HapticEffect")

effect.Type = Enum.HapticEffectType.GameplayExplosion

effect.Parent = Workspace

-- Play the haptic effect

effect:Play()

```

Provide feedback

---

GetWaveformKeys

Capabilities: Input

HapticEffect:GetWaveformKeys () :[{any}](/docs/en-us/luau/tables#arrays)

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Code Samples

Get Waveform Keys

```

local Workspace = game:GetService("Workspace")

local effect = Instance.new("HapticEffect")

effect.Type = Enum.HapticEffectType.Custom

effect.Parent = Workspace

effect:SetWaveformKeys({

	FloatCurveKey.new(0, 0.4, Enum.KeyInterpolationMode.Linear),

	FloatCurveKey.new(200, 1.0, Enum.KeyInterpolationMode.Linear),

})

-- Read the waveform back, scale it to half strength, and write it back.

-- Time is in milliseconds; value is from 0 (no haptic) to 1 (full intensity).

local keys = effect:GetWaveformKeys()

for i, key in keys do

	keys[i] = FloatCurveKey.new(key.Time, key.Value * 0.5, key.Interpolation)

end

effect:SetWaveformKeys(keys)

```

Provide feedback

---

SetWaveformKeys

Capabilities: Input

HapticEffect:SetWaveformKeys (keys :[{any}](/docs/en-us/luau/tables#arrays) ) : ()

Parameters

|

keys :[{any}](/docs/en-us/luau/tables#arrays)

 |

Returns

()

Code Samples

Set Waveform Keys

```

local Workspace = game:GetService("Workspace")

local effect = Instance.new("HapticEffect")

-- Set effect type to custom in order to define a waveform

effect.Type = Enum.HapticEffectType.Custom

effect.Parent = Workspace

-- Define the custom waveform curve through a table of FloatCurveKeys

-- Time values are in milliseconds; values range from 0 (no haptic) to 1 (full intensity)

local rampUpWaveform = {

	FloatCurveKey.new(0, 0.3, Enum.KeyInterpolationMode.Linear),

	FloatCurveKey.new(100, 0.4, Enum.KeyInterpolationMode.Linear),

	FloatCurveKey.new(300, 0.8, Enum.KeyInterpolationMode.Linear),

	FloatCurveKey.new(400, 1.0, Enum.KeyInterpolationMode.Linear)

}

-- Set waveform through the effect's method

effect:SetWaveformKeys(rampUpWaveform)

```

Provide feedback

---

Stop

Capabilities: Input

HapticEffect:Stop () : ()

Returns

()

Code Samples

Stop

```

local Workspace = game:GetService("Workspace")

local effect = Instance.new("HapticEffect")

effect.Type = Enum.HapticEffectType.GameplayExplosion

effect.Looped = true

effect.Parent = Workspace

-- Start the haptic effect

effect:Play()

-- After two seconds, stop the effect

task.wait(2)

effect:Stop()

```

Provide feedback

---

Events

Ended

Capabilities: Input

HapticEffect.Ended () :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Provide feedback

---

Jump to

▼

HapticEffect

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[Looped](#Looped)

[Position](#Position)

[Radius](#Radius)

[Type](#Type)

[Methods](#methods)

[Play()](#Play)

[GetWaveformKeys()](#GetWaveformKeys)

[SetWaveformKeys()](#SetWaveformKeys)

[Stop()](#Stop)

[Events](#events)

[Ended](#Ended)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
