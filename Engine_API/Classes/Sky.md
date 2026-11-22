<!-- Source: https://create.roblox.com/docs/reference/engine/classes/Sky -->

Sky | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Sky.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [Sky](/docs/reference/engine/classes/Sky)

English

Feedback

Engine Class

Sky

---

## Summary

Properties

|

[CelestialBodiesShown](#CelestialBodiesShown) :[boolean](/docs/luau/booleans)

 |
| --- | --- |
|

[MoonAngularSize](#MoonAngularSize) :[number](/docs/luau/numbers)

 |
|

[MoonTextureContent](#MoonTextureContent) :[Content](/docs/reference/engine/datatypes/Content)

 |
|

[MoonTextureId](#MoonTextureId) : ContentId

 |
|

[SkyboxBackContent](#SkyboxBackContent) :[Content](/docs/reference/engine/datatypes/Content)

 |
|

[SkyboxBk](#SkyboxBk) : ContentId

 |
|

[SkyboxDn](#SkyboxDn) : ContentId

 |
|

[SkyboxDownContent](#SkyboxDownContent) :[Content](/docs/reference/engine/datatypes/Content)

 |
|

[SkyboxFrontContent](#SkyboxFrontContent) :[Content](/docs/reference/engine/datatypes/Content)

 |
|

[SkyboxFt](#SkyboxFt) : ContentId

 |
|

[SkyboxLeftContent](#SkyboxLeftContent) :[Content](/docs/reference/engine/datatypes/Content)

 |
|

[SkyboxLf](#SkyboxLf) : ContentId

 |
|

[SkyboxOrientation](#SkyboxOrientation) :[Vector3](/docs/reference/engine/datatypes/Vector3)

 |
|

[SkyboxRightContent](#SkyboxRightContent) :[Content](/docs/reference/engine/datatypes/Content)

 |
|

[SkyboxRt](#SkyboxRt) : ContentId

 |
|

[SkyboxUp](#SkyboxUp) : ContentId

 |
|

[SkyboxUpContent](#SkyboxUpContent) :[Content](/docs/reference/engine/datatypes/Content)

 |
|

[StarCount](#StarCount) :[number](/docs/luau/numbers)

 |
|

[SunAngularSize](#SunAngularSize) :[number](/docs/luau/numbers)

 |
|

[SunTextureContent](#SunTextureContent) :[Content](/docs/reference/engine/datatypes/Content)

 |
|

[SunTextureId](#SunTextureId) : ContentId

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Properties

CelestialBodiesShown

Read Parallel

Capabilities: Environment

Sky.CelestialBodiesShown :[boolean](/docs/luau/booleans)

Provide feedback

---

MoonAngularSize

Read Parallel

Capabilities: Environment

Sky.MoonAngularSize :[number](/docs/luau/numbers)

Provide feedback

---

MoonTextureContent

Read Parallel

Capabilities: Environment

Sky.MoonTextureContent :[Content](/docs/reference/engine/datatypes/Content)

Provide feedback

---

MoonTextureId

Read Parallel

Capabilities: Environment

Sky.MoonTextureId : ContentId

Provide feedback

---

SkyboxBackContent

Read Parallel

Capabilities: Environment

Sky.SkyboxBackContent :[Content](/docs/reference/engine/datatypes/Content)

Provide feedback

---

SkyboxBk

Read Parallel

Capabilities: Environment

Sky.SkyboxBk : ContentId

Provide feedback

---

SkyboxDn

Read Parallel

Capabilities: Environment

Sky.SkyboxDn : ContentId

Provide feedback

---

SkyboxDownContent

Read Parallel

Capabilities: Environment

Sky.SkyboxDownContent :[Content](/docs/reference/engine/datatypes/Content)

Provide feedback

---

SkyboxFrontContent

Read Parallel

Capabilities: Environment

Sky.SkyboxFrontContent :[Content](/docs/reference/engine/datatypes/Content)

Provide feedback

---

SkyboxFt

Read Parallel

Capabilities: Environment

Sky.SkyboxFt : ContentId

Provide feedback

---

SkyboxLeftContent

Read Parallel

Capabilities: Environment

Sky.SkyboxLeftContent :[Content](/docs/reference/engine/datatypes/Content)

Provide feedback

---

SkyboxLf

Read Parallel

Capabilities: Environment

Sky.SkyboxLf : ContentId

Provide feedback

---

SkyboxOrientation

Read Parallel

Capabilities: Environment

Sky.SkyboxOrientation :[Vector3](/docs/reference/engine/datatypes/Vector3)

Code Samples

Skybox Orientation with Tween

```

local Lighting = game:GetService("Lighting")

local RunService = game:GetService("RunService")

local TweenService = game:GetService("TweenService")

local sky = Lighting:FindFirstChild("Sky")

local ROTATION_SPEED = 4 -- In degrees per second

local MAX_TILT = 2 -- In degrees

local TILT_SPEED = 4

local currentTilt = Instance.new("NumberValue")

currentTilt.Value = -MAX_TILT

local tweenGoal = { Value = MAX_TILT }

local tweenInfo = TweenInfo.new(TILT_SPEED, Enum.EasingStyle.Cubic, Enum.EasingDirection.InOut, -1, true)

local tween = TweenService:Create(currentTilt, tweenInfo, tweenGoal)

tween:Play()

RunService.Heartbeat:Connect(function(deltaTime)

	sky.SkyboxOrientation =

		Vector3.new(currentTilt.Value, (sky.SkyboxOrientation.Y + ROTATION_SPEED * deltaTime) % 360, 0)

end)

```

Provide feedback

---

SkyboxRightContent

Read Parallel

Capabilities: Environment

Sky.SkyboxRightContent :[Content](/docs/reference/engine/datatypes/Content)

Provide feedback

---

SkyboxRt

Read Parallel

Capabilities: Environment

Sky.SkyboxRt : ContentId

Provide feedback

---

SkyboxUp

Read Parallel

Capabilities: Environment

Sky.SkyboxUp : ContentId

Provide feedback

---

SkyboxUpContent

Read Parallel

Capabilities: Environment

Sky.SkyboxUpContent :[Content](/docs/reference/engine/datatypes/Content)

Provide feedback

---

StarCount

Read Parallel

Capabilities: Environment

Sky.StarCount :[number](/docs/luau/numbers)

Provide feedback

---

SunAngularSize

Read Parallel

Capabilities: Environment

Sky.SunAngularSize :[number](/docs/luau/numbers)

Provide feedback

---

SunTextureContent

Read Parallel

Capabilities: Environment

Sky.SunTextureContent :[Content](/docs/reference/engine/datatypes/Content)

Provide feedback

---

SunTextureId

Read Parallel

Capabilities: Environment

Sky.SunTextureId : ContentId

Provide feedback

---

Jump to

▼

Sky

[Summary](#summary)

[Properties](#summary-properties)

[Properties](#properties)

[CelestialBodiesShown](#CelestialBodiesShown)

[MoonAngularSize](#MoonAngularSize)

[MoonTextureContent](#MoonTextureContent)

[MoonTextureId](#MoonTextureId)

[SkyboxBackContent](#SkyboxBackContent)

[SkyboxBk](#SkyboxBk)

[SkyboxDn](#SkyboxDn)

[SkyboxDownContent](#SkyboxDownContent)

[SkyboxFrontContent](#SkyboxFrontContent)

[SkyboxFt](#SkyboxFt)

[SkyboxLeftContent](#SkyboxLeftContent)

[SkyboxLf](#SkyboxLf)

[SkyboxOrientation](#SkyboxOrientation)

[SkyboxRightContent](#SkyboxRightContent)

[SkyboxRt](#SkyboxRt)

[SkyboxUp](#SkyboxUp)

[SkyboxUpContent](#SkyboxUpContent)

[StarCount](#StarCount)

[SunAngularSize](#SunAngularSize)

[SunTextureContent](#SunTextureContent)

[SunTextureId](#SunTextureId)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
