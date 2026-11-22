<!-- Source: https://create.roblox.com/docs/reference/engine/classes/Lighting -->

Lighting | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Lighting.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [Lighting](/docs/reference/engine/classes/Lighting)

English

Feedback

Engine Class

Lighting

Not Creatable

Service

---

## Summary

Properties

|

[Ambient](#Ambient) :[Color3](/docs/reference/engine/datatypes/Color3)

 |
| --- | --- |
|

[Brightness](#Brightness) :[number](/docs/luau/numbers)

 |
|

[ClockTime](#ClockTime) :[number](/docs/luau/numbers)

 |
|

[ColorShift_Bottom](#ColorShift_Bottom) :[Color3](/docs/reference/engine/datatypes/Color3)

 |
|

[ColorShift_Top](#ColorShift_Top) :[Color3](/docs/reference/engine/datatypes/Color3)

 |
|

[EnvironmentDiffuseScale](#EnvironmentDiffuseScale) :[number](/docs/luau/numbers)

 |
|

[EnvironmentSpecularScale](#EnvironmentSpecularScale) :[number](/docs/luau/numbers)

 |
|

[ExposureCompensation](#ExposureCompensation) :[number](/docs/luau/numbers)

 |
|

[ExtendLightRangeTo120](#ExtendLightRangeTo120) :[Enum.RolloutState](/docs/reference/engine/enums/RolloutState)

 |
|

[FogColor](#FogColor) :[Color3](/docs/reference/engine/datatypes/Color3)

 |
|

[FogEnd](#FogEnd) :[number](/docs/luau/numbers)

 |
|

[FogStart](#FogStart) :[number](/docs/luau/numbers)

 |
|

[GeographicLatitude](#GeographicLatitude) :[number](/docs/luau/numbers)

 |
|

[GlobalShadows](#GlobalShadows) :[boolean](/docs/luau/booleans)

 |
|

[LightingStyle](#LightingStyle) :[Enum.LightingStyle](/docs/reference/engine/enums/LightingStyle)

 |
|

[OutdoorAmbient](#OutdoorAmbient) :[Color3](/docs/reference/engine/datatypes/Color3)

 |
|

[Outlines](#Outlines) :[boolean](/docs/luau/booleans)

Deprecated

 |
|

[PrioritizeLightingQuality](#PrioritizeLightingQuality) :[boolean](/docs/luau/booleans)

 |
|

[ShadowColor](#ShadowColor) :[Color3](/docs/reference/engine/datatypes/Color3)

Deprecated

 |
|

[ShadowSoftness](#ShadowSoftness) :[number](/docs/luau/numbers)

 |
|

[Technology](#Technology) :[Enum.Technology](/docs/reference/engine/enums/Technology)

Deprecated

 |
|

[TimeOfDay](#TimeOfDay) :[string](/docs/luau/strings)

 |

Methods

|

[GetMinutesAfterMidnight](#GetMinutesAfterMidnight) () :[number](/docs/luau/numbers)

 |
|

[getMinutesAfterMidnight](#getMinutesAfterMidnight) () :[number](/docs/luau/numbers)

Deprecated

 |
|

[GetMoonDirection](#GetMoonDirection) () :[Vector3](/docs/reference/engine/datatypes/Vector3)

 |
|

[GetMoonPhase](#GetMoonPhase) () :[number](/docs/luau/numbers)

Deprecated

 |
|

[GetSunDirection](#GetSunDirection) () :[Vector3](/docs/reference/engine/datatypes/Vector3)

 |
|

[SetMinutesAfterMidnight](#SetMinutesAfterMidnight) (minutes :  [number](/docs/luau/numbers) ) : ()

 |
|

[setMinutesAfterMidnight](#setMinutesAfterMidnight) (minutes :  [number](/docs/luau/numbers) ) : ()

Deprecated

 |

Events

|

[LightingChanged](#LightingChanged) (skyChanged :  [boolean](/docs/luau/booleans) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Properties

Ambient

Read Parallel

Capabilities: Environment

Lighting.Ambient :[Color3](/docs/reference/engine/datatypes/Color3)

Provide feedback

---

Brightness

Read Parallel

Capabilities: Environment

Lighting.Brightness :[number](/docs/luau/numbers)

Provide feedback

---

ClockTime

Not Replicated

Read Parallel

Capabilities: Environment

Lighting.ClockTime :[number](/docs/luau/numbers)

Provide feedback

---

ColorShift_Bottom

Read Parallel

Capabilities: Environment

Lighting.ColorShift_Bottom :[Color3](/docs/reference/engine/datatypes/Color3)

Provide feedback

---

ColorShift_Top

Read Parallel

Capabilities: Environment

Lighting.ColorShift_Top :[Color3](/docs/reference/engine/datatypes/Color3)

Provide feedback

---

EnvironmentDiffuseScale

Read Parallel

Capabilities: Environment

Lighting.EnvironmentDiffuseScale :[number](/docs/luau/numbers)

Provide feedback

---

EnvironmentSpecularScale

Read Parallel

Capabilities: Environment

Lighting.EnvironmentSpecularScale :[number](/docs/luau/numbers)

Provide feedback

---

ExposureCompensation

Read Parallel

Capabilities: Environment

Lighting.ExposureCompensation :[number](/docs/luau/numbers)

Provide feedback

---

ExtendLightRangeTo120

Not Scriptable

Read Parallel

Capabilities: Environment

Lighting.ExtendLightRangeTo120 :[Enum.RolloutState](/docs/reference/engine/enums/RolloutState)

Provide feedback

---

FogColor

Read Parallel

Capabilities: Environment

Lighting.FogColor :[Color3](/docs/reference/engine/datatypes/Color3)

Provide feedback

---

FogEnd

Read Parallel

Capabilities: Environment

Lighting.FogEnd :[number](/docs/luau/numbers)

Provide feedback

---

FogStart

Read Parallel

Capabilities: Environment

Lighting.FogStart :[number](/docs/luau/numbers)

Provide feedback

---

GeographicLatitude

Read Parallel

Capabilities: Environment

Lighting.GeographicLatitude :[number](/docs/luau/numbers)

Provide feedback

---

GlobalShadows

Read Parallel

Capabilities: Environment

Lighting.GlobalShadows :[boolean](/docs/luau/booleans)

Provide feedback

---

LightingStyle

Read Parallel

Capabilities: Environment

Lighting.LightingStyle :[Enum.LightingStyle](/docs/reference/engine/enums/LightingStyle)

Provide feedback

---

OutdoorAmbient

Read Parallel

Capabilities: Environment

Lighting.OutdoorAmbient :[Color3](/docs/reference/engine/datatypes/Color3)

Provide feedback

---

Outlines

Deprecated

Show details

---

PrioritizeLightingQuality

Read Parallel

Capabilities: Environment

Lighting.PrioritizeLightingQuality :[boolean](/docs/luau/booleans)

Provide feedback

---

ShadowColor

Deprecated

Show details

---

ShadowSoftness

Read Parallel

Capabilities: Environment

Lighting.ShadowSoftness :[number](/docs/luau/numbers)

Provide feedback

---

Technology

Deprecated

Show details

---

TimeOfDay

Read Parallel

Capabilities: Environment

Lighting.TimeOfDay :[string](/docs/luau/strings)

Provide feedback

---

Methods

GetMinutesAfterMidnight

Write Parallel

Capabilities: Environment

Lighting:GetMinutesAfterMidnight () :[number](/docs/luau/numbers)

Returns

[number](/docs/luau/numbers)

Provide feedback

---

getMinutesAfterMidnight

Deprecated

Show details

---

GetMoonDirection

Write Parallel

Capabilities: Environment

Lighting:GetMoonDirection () :[Vector3](/docs/reference/engine/datatypes/Vector3)

Returns

[Vector3](/docs/reference/engine/datatypes/Vector3)

Provide feedback

---

GetMoonPhase

Deprecated

Show details

---

GetSunDirection

Write Parallel

Capabilities: Environment

Lighting:GetSunDirection () :[Vector3](/docs/reference/engine/datatypes/Vector3)

Returns

[Vector3](/docs/reference/engine/datatypes/Vector3)

Provide feedback

---

SetMinutesAfterMidnight

Capabilities: Environment

Lighting:SetMinutesAfterMidnight (minutes :[number](/docs/luau/numbers) ) : ()

Parameters

|

minutes :[number](/docs/luau/numbers)

 |

Returns

()

Code Samples

Set Minutes After Midnight

```

local Lighting = game:GetService("Lighting")

local TIME_SPEED = 60  -- 1 min = 1 hour

local START_TIME = 9  -- 9 AM

local minutesAfterMidnight = START_TIME * 60

local waitTime = 60 / TIME_SPEED

while true do

	minutesAfterMidnight = minutesAfterMidnight + 1

	Lighting:SetMinutesAfterMidnight(minutesAfterMidnight)

	task.wait(waitTime)

end

```

Provide feedback

---

setMinutesAfterMidnight

Deprecated

Show details

---

Events

LightingChanged

Capabilities: Environment

Lighting.LightingChanged (skyChanged :[boolean](/docs/luau/booleans) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

skyChanged :[boolean](/docs/luau/booleans)

 |

Provide feedback

---

Jump to

▼

Lighting

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[Ambient](#Ambient)

[Brightness](#Brightness)

[ClockTime](#ClockTime)

[ColorShift_Bottom](#ColorShift_Bottom)

[ColorShift_Top](#ColorShift_Top)

[EnvironmentDiffuseScale](#EnvironmentDiffuseScale)

[EnvironmentSpecularScale](#EnvironmentSpecularScale)

[ExposureCompensation](#ExposureCompensation)

[ExtendLightRangeTo120](#ExtendLightRangeTo120)

[FogColor](#FogColor)

[FogEnd](#FogEnd)

[FogStart](#FogStart)

[GeographicLatitude](#GeographicLatitude)

[GlobalShadows](#GlobalShadows)

[LightingStyle](#LightingStyle)

[OutdoorAmbient](#OutdoorAmbient)

[Outlines](#Outlines)

[PrioritizeLightingQuality](#PrioritizeLightingQuality)

[ShadowColor](#ShadowColor)

[ShadowSoftness](#ShadowSoftness)

[Technology](#Technology)

[TimeOfDay](#TimeOfDay)

[Methods](#methods)

[GetMinutesAfterMidnight()](#GetMinutesAfterMidnight)

[getMinutesAfterMidnight()](#getMinutesAfterMidnight)

[GetMoonDirection()](#GetMoonDirection)

[GetMoonPhase()](#GetMoonPhase)

[GetSunDirection()](#GetSunDirection)

[SetMinutesAfterMidnight()](#SetMinutesAfterMidnight)

[setMinutesAfterMidnight()](#setMinutesAfterMidnight)

[Events](#events)

[LightingChanged](#LightingChanged)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
