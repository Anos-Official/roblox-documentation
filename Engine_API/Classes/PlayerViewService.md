<!-- Source: https://create.roblox.com/docs/reference/engine/classes/PlayerViewService -->

PlayerViewService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/PlayerViewService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [PlayerViewService](/docs/reference/engine/classes/PlayerViewService)

English

Feedback

Engine Class

PlayerViewService

Not Creatable

Service

Not Replicated

---

## Summary

Methods

|

[GetDeviceCameraCFrame](#GetDeviceCameraCFrame) (player :  [Player](/docs/reference/engine/classes/Player) ) :[CFrame](/docs/reference/engine/datatypes/CFrame)

 |
| --- | --- |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Methods

GetDeviceCameraCFrame

Capabilities: SensitiveInput

PlayerViewService:GetDeviceCameraCFrame (player :[Player](/docs/reference/engine/classes/Player) ) :[CFrame](/docs/reference/engine/datatypes/CFrame)

Parameters

|

player :[Player](/docs/reference/engine/classes/Player)

Default Value: nil |

Returns

[CFrame](/docs/reference/engine/datatypes/CFrame)

Code Samples

PlayerViewService:GetDeviceCameraCFrame()

```

local PlayerViewService = game:GetService("PlayerViewService")

local RunService = game:GetService("RunService")

local Workspace = game:GetService("Workspace")

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local camera = Workspace.CurrentCamera

local function updatePictureInPictureCamera()

	camera.CFrame = PlayerViewService:GetDeviceCameraCFrame(player)

end

RunService:BindToRenderStep(

	"PictureInPictureCamera",

	Enum.RenderPriority.Camera.Value + 1,

	updatePictureInPictureCamera

)

```

Provide feedback

---

Jump to

▼

PlayerViewService

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[GetDeviceCameraCFrame()](#GetDeviceCameraCFrame)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
