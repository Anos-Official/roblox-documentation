<!-- Source: https://create.roblox.com/docs/reference/engine/classes/ViewportFrame -->

ViewportFrame | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/ViewportFrame.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [GuiBase](/docs/reference/engine/classes/GuiBase)
8. /
9. [GuiBase2d](/docs/reference/engine/classes/GuiBase2d)
10. /
11. [GuiObject](/docs/reference/engine/classes/GuiObject)
12. /
13. [ViewportFrame](/docs/reference/engine/classes/ViewportFrame)

English

Feedback

Engine Class

ViewportFrame

---

## Summary

Properties

|

[Ambient](#Ambient) :[Color3](/docs/reference/engine/datatypes/Color3)

 |
| --- | --- |
|

[CurrentCamera](#CurrentCamera) :[Camera](/docs/reference/engine/classes/Camera)

 |
|

[ImageColor3](#ImageColor3) :[Color3](/docs/reference/engine/datatypes/Color3)

 |
|

[ImageTransparency](#ImageTransparency) :[number](/docs/luau/numbers)

 |
|

[LightColor](#LightColor) :[Color3](/docs/reference/engine/datatypes/Color3)

 |
|

[LightDirection](#LightDirection) :[Vector3](/docs/reference/engine/datatypes/Vector3)

 |

Inherited Members

51  inherited from [GuiObject](/docs/reference/engine/classes/GuiObject)

12  inherited from [GuiBase2d](/docs/reference/engine/classes/GuiBase2d)

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

ViewportFrame - Create GUI

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

ViewportFrame - Control Camera

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

API Reference

Properties

Ambient

Read Parallel

Capabilities: UI

ViewportFrame.Ambient :[Color3](/docs/reference/engine/datatypes/Color3)

Provide feedback

---

CurrentCamera

Not Replicated

Read Parallel

Capabilities: UI

ViewportFrame.CurrentCamera :[Camera](/docs/reference/engine/classes/Camera)

Provide feedback

---

ImageColor3

Read Parallel

Capabilities: UI

ViewportFrame.ImageColor3 :[Color3](/docs/reference/engine/datatypes/Color3)

Provide feedback

---

ImageTransparency

Read Parallel

Capabilities: UI

ViewportFrame.ImageTransparency :[number](/docs/luau/numbers)

Provide feedback

---

LightColor

Read Parallel

Capabilities: UI

ViewportFrame.LightColor :[Color3](/docs/reference/engine/datatypes/Color3)

Provide feedback

---

LightDirection

Read Parallel

Capabilities: UI

ViewportFrame.LightDirection :[Vector3](/docs/reference/engine/datatypes/Vector3)

Provide feedback

---

Jump to

▼

ViewportFrame

[Summary](#summary)

[Properties](#summary-properties)

[Properties](#properties)

[Ambient](#Ambient)

[CurrentCamera](#CurrentCamera)

[ImageColor3](#ImageColor3)

[ImageTransparency](#ImageTransparency)

[LightColor](#LightColor)

[LightDirection](#LightDirection)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
