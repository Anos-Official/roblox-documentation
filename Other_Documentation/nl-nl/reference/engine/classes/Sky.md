<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Sky -->

Sky | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [Sky](/docs/nl-nl/reference/engine/classes/Sky)

Nederlands

Feedback

Engine-klasse

Sky

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Sky)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[CelestialBodiesShown](#CelestialBodiesShown) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |
|

[MoonAngularSize](#MoonAngularSize) :[number](/docs/nl-nl/luau/numbers)

 |
|

[MoonTextureContent](#MoonTextureContent) :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

 |
|

[MoonTextureId](#MoonTextureId) : ContentId

 |
|

[SkyboxBackContent](#SkyboxBackContent) :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

 |
|

[SkyboxBk](#SkyboxBk) : ContentId

 |
|

[SkyboxDn](#SkyboxDn) : ContentId

 |
|

[SkyboxDownContent](#SkyboxDownContent) :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

 |
|

[SkyboxFrontContent](#SkyboxFrontContent) :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

 |
|

[SkyboxFt](#SkyboxFt) : ContentId

 |
|

[SkyboxLeftContent](#SkyboxLeftContent) :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

 |
|

[SkyboxLf](#SkyboxLf) : ContentId

 |
|

[SkyboxOrientation](#SkyboxOrientation) :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |
|

[SkyboxRightContent](#SkyboxRightContent) :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

 |
|

[SkyboxRt](#SkyboxRt) : ContentId

 |
|

[SkyboxUp](#SkyboxUp) : ContentId

 |
|

[SkyboxUpContent](#SkyboxUpContent) :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

 |
|

[StarCount](#StarCount) :[number](/docs/nl-nl/luau/numbers)

 |
|

[SunAngularSize](#SunAngularSize) :[number](/docs/nl-nl/luau/numbers)

 |
|

[SunTextureContent](#SunTextureContent) :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

 |
|

[SunTextureId](#SunTextureId) : ContentId

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

CelestialBodiesShown

Parallel lezen

Mogelijkheden: Environment

Sky.CelestialBodiesShown :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

MoonAngularSize

Parallel lezen

Mogelijkheden: Environment

Sky.MoonAngularSize :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

MoonTextureContent

Parallel lezen

Mogelijkheden: Environment

Sky.MoonTextureContent :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

Feedback geven

---

MoonTextureId

Parallel lezen

Mogelijkheden: Environment

Sky.MoonTextureId : ContentId

Feedback geven

---

SkyboxBackContent

Parallel lezen

Mogelijkheden: Environment

Sky.SkyboxBackContent :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

Feedback geven

---

SkyboxBk

Parallel lezen

Mogelijkheden: Environment

Sky.SkyboxBk : ContentId

Feedback geven

---

SkyboxDn

Parallel lezen

Mogelijkheden: Environment

Sky.SkyboxDn : ContentId

Feedback geven

---

SkyboxDownContent

Parallel lezen

Mogelijkheden: Environment

Sky.SkyboxDownContent :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

Feedback geven

---

SkyboxFrontContent

Parallel lezen

Mogelijkheden: Environment

Sky.SkyboxFrontContent :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

Feedback geven

---

SkyboxFt

Parallel lezen

Mogelijkheden: Environment

Sky.SkyboxFt : ContentId

Feedback geven

---

SkyboxLeftContent

Parallel lezen

Mogelijkheden: Environment

Sky.SkyboxLeftContent :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

Feedback geven

---

SkyboxLf

Parallel lezen

Mogelijkheden: Environment

Sky.SkyboxLf : ContentId

Feedback geven

---

SkyboxOrientation

Parallel lezen

Mogelijkheden: Environment

Sky.SkyboxOrientation :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Codevoorbeelden

Skybox Oriëntatie met Tween

```

local Lighting = game:GetService("Lighting")

local RunService = game:GetService("RunService")

local TweenService = game:GetService("TweenService")

local sky = Lighting:FindFirstChild("Sky")

local ROTATION_SPEED = 4 -- In graden per seconde

local MAX_TILT = 2 -- In graden

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

Feedback geven

---

SkyboxRightContent

Parallel lezen

Mogelijkheden: Environment

Sky.SkyboxRightContent :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

Feedback geven

---

SkyboxRt

Parallel lezen

Mogelijkheden: Environment

Sky.SkyboxRt : ContentId

Feedback geven

---

SkyboxUp

Parallel lezen

Mogelijkheden: Environment

Sky.SkyboxUp : ContentId

Feedback geven

---

SkyboxUpContent

Parallel lezen

Mogelijkheden: Environment

Sky.SkyboxUpContent :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

Feedback geven

---

StarCount

Parallel lezen

Mogelijkheden: Environment

Sky.StarCount :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

SunAngularSize

Parallel lezen

Mogelijkheden: Environment

Sky.SunAngularSize :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

SunTextureContent

Parallel lezen

Mogelijkheden: Environment

Sky.SunTextureContent :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

Feedback geven

---

SunTextureId

Parallel lezen

Mogelijkheden: Environment

Sky.SunTextureId : ContentId

Feedback geven

---

Ga naar

▼

Sky

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Eigenschappen](#properties)

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

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
