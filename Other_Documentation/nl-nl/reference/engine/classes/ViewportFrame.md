<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/ViewportFrame -->

ViewportFrame | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [GuiBase](/docs/nl-nl/reference/engine/classes/GuiBase)
8. /
9. [GuiBase2d](/docs/nl-nl/reference/engine/classes/GuiBase2d)
10. /
11. [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)
12. /
13. [ViewportFrame](/docs/nl-nl/reference/engine/classes/ViewportFrame)

Nederlands

Feedback

Engine-klasse

ViewportFrame

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/ViewportFrame)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Ambient](#Ambient) :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

 |
| --- | --- |
|

[CurrentCamera](#CurrentCamera) :[Camera](/docs/nl-nl/reference/engine/classes/Camera)

 |
|

[ImageColor3](#ImageColor3) :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

 |
|

[ImageTransparency](#ImageTransparency) :[number](/docs/nl-nl/luau/numbers)

 |
|

[LightColor](#LightColor) :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

 |
|

[LightDirection](#LightDirection) :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |

Overgenomen leden

51  overgenomen van [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)

12  overgenomen van [GuiBase2d](/docs/nl-nl/reference/engine/classes/GuiBase2d)

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

ViewportFrame - Maak GUI

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local playerGui = player:WaitForChild("PlayerGui")

local screenGui = Instance.new("ScreenGui")

screenGui.Parent = playerGui

local viewportFrame = Instance.new("ViewportFrame")

viewportFrame.Size = UDim2.new(0.3, 0, 0.4, 0)

viewportFrame.Position = UDim2.new(0, 15, 0, 15)

viewportFrame.BackgroundColor3 = Color3.new(0, 0, 0)

viewportFrame.BorderColor3 = Color3.new(0.6, 0.5, 0.4)

viewportFrame.BorderSizePixel = 2

viewportFrame.BackgroundTransparency = 0.25

viewportFrame.Parent = screenGui

local part = Instance.new("Part")

part.Material = Enum.Material.Concrete

part.Color = Color3.new(0.25, 0.75, 1)

part.Position = Vector3.new(0, 0, 0)

part.Parent = viewportFrame

local viewportCamera = Instance.new("Camera")

viewportFrame.CurrentCamera = viewportCamera

viewportCamera.Parent = viewportFrame

viewportCamera.CFrame = CFrame.new(Vector3.new(0, 2, 12), part.Position)

```

ViewportFrame - Camera Besturen

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local playerGui = player:WaitForChild("PlayerGui")

local screenGui = Instance.new("ScreenGui")

screenGui.Parent = playerGui

local TweenService = game:GetService("TweenService")

local viewportFrame = Instance.new("ViewportFrame")

viewportFrame.Size = UDim2.new(0.3, 0, 0.4, 0)

viewportFrame.Position = UDim2.new(0, 15, 0, 15)

viewportFrame.BackgroundColor3 = Color3.new(0, 0, 0)

viewportFrame.BorderColor3 = Color3.new(0.6, 0.5, 0.4)

viewportFrame.BorderSizePixel = 2

viewportFrame.BackgroundTransparency = 0.25

viewportFrame.Parent = screenGui

local part = Instance.new("Part")

part.Material = Enum.Material.Concrete

part.Color = Color3.new(0.25, 0.75, 1)

part.Position = Vector3.new(0, 0, 0)

part.Parent = viewportFrame

local viewportCamera = Instance.new("Camera")

viewportFrame.CurrentCamera = viewportCamera

viewportCamera.Parent = viewportFrame

viewportCamera.CFrame = CFrame.new(Vector3.new(0, 2, 12), part.Position)

task.wait(2)

local cameraGoal = {

	CFrame = CFrame.new(Vector3.new(0, 6, 4), part.Position),

}

local tweenInfo = TweenInfo.new(2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)

local tween = TweenService:Create(viewportCamera, tweenInfo, cameraGoal)

tween:Play()

```

---

API-referentie

Eigenschappen

Ambient

Parallel lezen

Mogelijkheden: UI

ViewportFrame.Ambient :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

Feedback geven

---

CurrentCamera

Niet gerepliceerd

Parallel lezen

Mogelijkheden: UI

ViewportFrame.CurrentCamera :[Camera](/docs/nl-nl/reference/engine/classes/Camera)

Feedback geven

---

ImageColor3

Parallel lezen

Mogelijkheden: UI

ViewportFrame.ImageColor3 :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

Feedback geven

---

ImageTransparency

Parallel lezen

Mogelijkheden: UI

ViewportFrame.ImageTransparency :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

LightColor

Parallel lezen

Mogelijkheden: UI

ViewportFrame.LightColor :[Color3](/docs/nl-nl/reference/engine/datatypes/Color3)

Feedback geven

---

LightDirection

Parallel lezen

Mogelijkheden: UI

ViewportFrame.LightDirection :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Feedback geven

---

Ga naar

▼

ViewportFrame

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Eigenschappen](#properties)

[Ambient](#Ambient)

[CurrentCamera](#CurrentCamera)

[ImageColor3](#ImageColor3)

[ImageTransparency](#ImageTransparency)

[LightColor](#LightColor)

[LightDirection](#LightDirection)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
