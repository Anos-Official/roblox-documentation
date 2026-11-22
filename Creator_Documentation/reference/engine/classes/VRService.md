<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/VRService -->

VRService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/VRService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [VRService](/docs/en-us/reference/engine/classes/VRService)

English

Feedback

Engine Class

VRService

Not Creatable

Service

---

## Summary

Properties

|

[AutomaticScaling](#AutomaticScaling) :[Enum.VRScaling](/docs/en-us/reference/engine/enums/VRScaling)

 |
| --- | --- |
|

[AvatarGestures](#AvatarGestures) :[boolean](/docs/en-us/luau/booleans)

 |
|

[ControllerModels](#ControllerModels) :[Enum.VRControllerModelMode](/docs/en-us/reference/engine/enums/VRControllerModelMode)

 |
|

[FadeOutViewOnCollision](#FadeOutViewOnCollision) :[boolean](/docs/en-us/luau/booleans)

 |
|

[GuiInputUserCFrame](#GuiInputUserCFrame) :[Enum.UserCFrame](/docs/en-us/reference/engine/enums/UserCFrame)

 |
|

[LaserPointer](#LaserPointer) :[Enum.VRLaserPointerMode](/docs/en-us/reference/engine/enums/VRLaserPointerMode)

 |
|

[ThirdPersonFollowCamEnabled](#ThirdPersonFollowCamEnabled) :[boolean](/docs/en-us/luau/booleans)

 |
|

[VREnabled](#VREnabled) :[boolean](/docs/en-us/luau/booleans)

 |

Methods

|

[GetTouchpadMode](#GetTouchpadMode) (pad :  [Enum.VRTouchpad](/docs/en-us/reference/engine/enums/VRTouchpad) ) :[Enum.VRTouchpadMode](/docs/en-us/reference/engine/enums/VRTouchpadMode)

 |
|

[GetUserCFrame](#GetUserCFrame) (type :  [Enum.UserCFrame](/docs/en-us/reference/engine/enums/UserCFrame) ) :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

 |
|

[GetUserCFrameEnabled](#GetUserCFrameEnabled) (type :  [Enum.UserCFrame](/docs/en-us/reference/engine/enums/UserCFrame) ) :[boolean](/docs/en-us/luau/booleans)

 |
|

[RecenterUserHeadCFrame](#RecenterUserHeadCFrame) () : ()

 |
|

[RequestNavigation](#RequestNavigation) (cframe :  [CFrame](/docs/en-us/reference/engine/datatypes/CFrame) , inputUserCFrame :  [Enum.UserCFrame](/docs/en-us/reference/engine/enums/UserCFrame) ) : ()

 |
|

[SetTouchpadMode](#SetTouchpadMode) (pad :  [Enum.VRTouchpad](/docs/en-us/reference/engine/enums/VRTouchpad) , mode :  [Enum.VRTouchpadMode](/docs/en-us/reference/engine/enums/VRTouchpadMode) ) : ()

 |

Events

|

[NavigationRequested](#NavigationRequested) (cframe :  [CFrame](/docs/en-us/reference/engine/datatypes/CFrame) , inputUserCFrame :  [Enum.UserCFrame](/docs/en-us/reference/engine/enums/UserCFrame) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[TouchpadModeChanged](#TouchpadModeChanged) (pad :  [Enum.VRTouchpad](/docs/en-us/reference/engine/enums/VRTouchpad) , mode :  [Enum.VRTouchpadMode](/docs/en-us/reference/engine/enums/VRTouchpadMode) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[UserCFrameChanged](#UserCFrameChanged) (type :  [Enum.UserCFrame](/docs/en-us/reference/engine/enums/UserCFrame) , value :  [CFrame](/docs/en-us/reference/engine/datatypes/CFrame) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[UserCFrameEnabled](#UserCFrameEnabled) (type :  [Enum.UserCFrame](/docs/en-us/reference/engine/enums/UserCFrame) , enabled :  [boolean](/docs/en-us/luau/booleans) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

VRService

```

local VRService = game:GetService("VRService")

local part = workspace.Part

local handOffset = VRService:GetUserCFrame(Enum.UserCFrame.LeftHand)

-- Account for headscale

handOffset = handOffset.Rotation + handOffset.Position * workspace.CurrentCamera.HeadScale

part.CFrame = workspace.CurrentCamera.CFrame * handOffset

```

---

API Reference

Properties

AutomaticScaling

Read Parallel

Capabilities: Input

VRService.AutomaticScaling :[Enum.VRScaling](/docs/en-us/reference/engine/enums/VRScaling)

Provide feedback

---

AvatarGestures

Read Parallel

Capabilities: Input

VRService.AvatarGestures :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

ControllerModels

Read Parallel

Capabilities: Input

VRService.ControllerModels :[Enum.VRControllerModelMode](/docs/en-us/reference/engine/enums/VRControllerModelMode)

Provide feedback

---

FadeOutViewOnCollision

Read Parallel

Capabilities: Input

VRService.FadeOutViewOnCollision :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

GuiInputUserCFrame

Not Replicated

Read Parallel

Capabilities: Input

VRService.GuiInputUserCFrame :[Enum.UserCFrame](/docs/en-us/reference/engine/enums/UserCFrame)

Code Samples

VRService.GuiInputUserCFrame

```

local VRService = game:GetService("VRService")

if VRService.VREnabled then

	print(VRService.GuiInputUserCFrame.Name)

else

	print("No VR device detected!")

end

```

Provide feedback

---

LaserPointer

Read Parallel

Capabilities: Input

VRService.LaserPointer :[Enum.VRLaserPointerMode](/docs/en-us/reference/engine/enums/VRLaserPointerMode)

Provide feedback

---

ThirdPersonFollowCamEnabled

Read Only

Not Replicated

Read Parallel

Capabilities: Input

VRService.ThirdPersonFollowCamEnabled :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

VREnabled

Read Only

Not Replicated

Read Parallel

Capabilities: Input

VRService.VREnabled :[boolean](/docs/en-us/luau/booleans)

Code Samples

VR Head Tracking

```

local VRService = game:GetService("VRService")

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local character = player.CharacterAdded:Wait()

local head = character:WaitForChild("Head")

local function TrackHead(inputType, value)

	if inputType == Enum.UserCFrame.Head then

		head.CFrame = value

	end

end

if VRService.VREnabled then

	-- Set the initial CFrame

	head.CFrame = VRService:GetUserCFrame(Enum.UserCFrame.Head)

	-- Track VR headset movement and mirror for character's head

	VRService.UserCFrameChanged:Connect(TrackHead)

end

```

Provide feedback

---

Methods

GetTouchpadMode

Capabilities: Input

VRService:GetTouchpadMode (pad :[Enum.VRTouchpad](/docs/en-us/reference/engine/enums/VRTouchpad) ) :[Enum.VRTouchpadMode](/docs/en-us/reference/engine/enums/VRTouchpadMode)

Parameters

|

pad :[Enum.VRTouchpad](/docs/en-us/reference/engine/enums/VRTouchpad)

 |

Returns

[Enum.VRTouchpadMode](/docs/en-us/reference/engine/enums/VRTouchpadMode)

Code Samples

VRService:GetTouchpadMode

```

local VRService = game:GetService("VRService")

VRService:GetTouchpadMode(Enum.VRTouchpad.Left)

```

Provide feedback

---

GetUserCFrame

Capabilities: Input

VRService:GetUserCFrame (type :[Enum.UserCFrame](/docs/en-us/reference/engine/enums/UserCFrame) ) :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

Parameters

|

type :[Enum.UserCFrame](/docs/en-us/reference/engine/enums/UserCFrame)

 |

Returns

[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

Code Samples

VRService:GetUserCFrame

```

local Workspace = game:GetService("Workspace")

local VRService = game:GetService("VRService")

local camera = Workspace.CurrentCamera

local part = script.Parent.Part

local handOffset = VRService:GetUserCFrame(Enum.UserCFrame.LeftHand)

-- Account for headscale

handOffset = handOffset.Rotation + handOffset.Position * camera.HeadScale

part.CFrame = camera.CFrame * handOffset

```

Provide feedback

---

GetUserCFrameEnabled

Capabilities: Input

VRService:GetUserCFrameEnabled (type :[Enum.UserCFrame](/docs/en-us/reference/engine/enums/UserCFrame) ) :[boolean](/docs/en-us/luau/booleans)

Parameters

|

type :[Enum.UserCFrame](/docs/en-us/reference/engine/enums/UserCFrame)

 |

Returns

[boolean](/docs/en-us/luau/booleans)

Code Samples

VRService:GetUserCFrameEnabled

```

local VRService = game:GetService("VRService")

local isEnabled = VRService:GetUserCFrameEnabled(Enum.UserCFrame.Head)

if isEnabled then

	print("VR device is enabled!")

else

	print("VR device is disabled!")

end

```

Provide feedback

---

RecenterUserHeadCFrame

Capabilities: Input

VRService:RecenterUserHeadCFrame () : ()

Returns

()

Code Samples

VRService:RecenterUserHeadCFrame

```

local VRService = game:GetService("VRService")

VRService:RecenterUserHeadCFrame()

```

Provide feedback

---

RequestNavigation

Capabilities: Input

VRService:RequestNavigation (

cframe :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame) , inputUserCFrame :[Enum.UserCFrame](/docs/en-us/reference/engine/enums/UserCFrame)

) : ()

Parameters

|

cframe :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

 |
|

inputUserCFrame :[Enum.UserCFrame](/docs/en-us/reference/engine/enums/UserCFrame)

 |

Returns

()

Code Samples

VRService:RequestNavigation

```

local VRService = game:GetService("VRService")

local destination = workspace:FindFirstChild("NavigationDestination")

VRService:RequestNavigation(Enum.UserCFrame.Head, destination.CFrame)

```

Provide feedback

---

SetTouchpadMode

Capabilities: Input

VRService:SetTouchpadMode (

pad :[Enum.VRTouchpad](/docs/en-us/reference/engine/enums/VRTouchpad) , mode :[Enum.VRTouchpadMode](/docs/en-us/reference/engine/enums/VRTouchpadMode)

) : ()

Parameters

|

pad :[Enum.VRTouchpad](/docs/en-us/reference/engine/enums/VRTouchpad)

 |
|

mode :[Enum.VRTouchpadMode](/docs/en-us/reference/engine/enums/VRTouchpadMode)

 |

Returns

()

Code Samples

VRService:SetTouchpadMode

```

local VRService = game:GetService("VRService")

VRService:SetTouchpadMode(Enum.VRTouchpad.Left, Enum.VRTouchpadMode.Touch)

```

Provide feedback

---

Events

NavigationRequested

Capabilities: Input

VRService.NavigationRequested (

cframe :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame) , inputUserCFrame :[Enum.UserCFrame](/docs/en-us/reference/engine/enums/UserCFrame)

) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

cframe :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

 |
|

inputUserCFrame :[Enum.UserCFrame](/docs/en-us/reference/engine/enums/UserCFrame)

 |

Code Samples

VRService.NavigationRequested

```

local VRService = game:GetService("VRService")

VRService.NavigationRequested:Connect(function(cframe, inputUserCFrame)

	print(inputUserCFrame.Name .. " made request with CFrame: " .. cframe)

end)

```

Provide feedback

---

TouchpadModeChanged

Capabilities: Input

VRService.TouchpadModeChanged (

pad :[Enum.VRTouchpad](/docs/en-us/reference/engine/enums/VRTouchpad) , mode :[Enum.VRTouchpadMode](/docs/en-us/reference/engine/enums/VRTouchpadMode)

) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

pad :[Enum.VRTouchpad](/docs/en-us/reference/engine/enums/VRTouchpad)

 |
|

mode :[Enum.VRTouchpadMode](/docs/en-us/reference/engine/enums/VRTouchpadMode)

 |

Code Samples

VRService.TouchpadModeChanged

```

local VRService = game:GetService("VRService")

VRService.TouchpadModeChanged:Connect(function(pad, mode)

	print(pad.Name .. " Touchpad changed to state: " .. mode.Name)

end)

```

Provide feedback

---

UserCFrameChanged

Capabilities: Input

VRService.UserCFrameChanged (

type :[Enum.UserCFrame](/docs/en-us/reference/engine/enums/UserCFrame) , value :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

type :[Enum.UserCFrame](/docs/en-us/reference/engine/enums/UserCFrame)

 |
|

value :[CFrame](/docs/en-us/reference/engine/datatypes/CFrame)

 |

Code Samples

VRService.UserCFrameChanged

```

local VRService = game:GetService("VRService")

VRService.UserCFrameChanged:Connect(function(userCFrameType, cframeValue)

	print(userCFrameType.Name .. " changed. Updated Frame: " .. tostring(cframeValue))

end)

```

Provide feedback

---

UserCFrameEnabled

Capabilities: Input

VRService.UserCFrameEnabled (

type :[Enum.UserCFrame](/docs/en-us/reference/engine/enums/UserCFrame) , enabled :[boolean](/docs/en-us/luau/booleans)

) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

type :[Enum.UserCFrame](/docs/en-us/reference/engine/enums/UserCFrame)

 |
|

enabled :[boolean](/docs/en-us/luau/booleans)

 |

Code Samples

VRService.UserCFrameEnabled

```

local VRService = game:GetService("VRService")

VRService.UserCFrameEnabled:Connect(function(type, enabled)

	if enabled then

		print(type.Name .. " got enabled!")

	else

		print(type.Name .. " got disabled!")

	end

end)

```

Provide feedback

---

Jump to

▼

VRService

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[AutomaticScaling](#AutomaticScaling)

[AvatarGestures](#AvatarGestures)

[ControllerModels](#ControllerModels)

[FadeOutViewOnCollision](#FadeOutViewOnCollision)

[GuiInputUserCFrame](#GuiInputUserCFrame)

[LaserPointer](#LaserPointer)

[ThirdPersonFollowCamEnabled](#ThirdPersonFollowCamEnabled)

[VREnabled](#VREnabled)

[Methods](#methods)

[GetTouchpadMode()](#GetTouchpadMode)

[GetUserCFrame()](#GetUserCFrame)

[GetUserCFrameEnabled()](#GetUserCFrameEnabled)

[RecenterUserHeadCFrame()](#RecenterUserHeadCFrame)

[RequestNavigation()](#RequestNavigation)

[SetTouchpadMode()](#SetTouchpadMode)

[Events](#events)

[NavigationRequested](#NavigationRequested)

[TouchpadModeChanged](#TouchpadModeChanged)

[UserCFrameChanged](#UserCFrameChanged)

[UserCFrameEnabled](#UserCFrameEnabled)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
