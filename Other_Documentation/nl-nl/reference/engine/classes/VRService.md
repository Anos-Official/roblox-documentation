<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/VRService -->

VRService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [VRService](/docs/nl-nl/reference/engine/classes/VRService)

Nederlands

Feedback

Engine-klasse

VRService

Niet maakbaar

Service

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/VRService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[AutomaticScaling](#AutomaticScaling) :[Enum.VRScaling](/docs/nl-nl/reference/engine/enums/VRScaling)

 |
| --- | --- |
|

[AvatarGestures](#AvatarGestures) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[ControllerModels](#ControllerModels) :[Enum.VRControllerModelMode](/docs/nl-nl/reference/engine/enums/VRControllerModelMode)

 |
|

[FadeOutViewOnCollision](#FadeOutViewOnCollision) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[GuiInputUserCFrame](#GuiInputUserCFrame) :[Enum.UserCFrame](/docs/nl-nl/reference/engine/enums/UserCFrame)

 |
|

[LaserPointer](#LaserPointer) :[Enum.VRLaserPointerMode](/docs/nl-nl/reference/engine/enums/VRLaserPointerMode)

 |
|

[ThirdPersonFollowCamEnabled](#ThirdPersonFollowCamEnabled) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[VREnabled](#VREnabled) :[boolean](/docs/nl-nl/luau/booleans)

 |

Methoden

|

[GetTouchpadMode](#GetTouchpadMode) (pad :  [Enum.VRTouchpad](/docs/nl-nl/reference/engine/enums/VRTouchpad) ) :[Enum.VRTouchpadMode](/docs/nl-nl/reference/engine/enums/VRTouchpadMode)

 |
|

[GetUserCFrame](#GetUserCFrame) (type :  [Enum.UserCFrame](/docs/nl-nl/reference/engine/enums/UserCFrame) ) :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

 |
|

[GetUserCFrameEnabled](#GetUserCFrameEnabled) (type :  [Enum.UserCFrame](/docs/nl-nl/reference/engine/enums/UserCFrame) ) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[RecenterUserHeadCFrame](#RecenterUserHeadCFrame) () : ()

 |
|

[RequestNavigation](#RequestNavigation) (cframe :  [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame) , inputUserCFrame :  [Enum.UserCFrame](/docs/nl-nl/reference/engine/enums/UserCFrame) ) : ()

 |
|

[SetTouchpadMode](#SetTouchpadMode) (pad :  [Enum.VRTouchpad](/docs/nl-nl/reference/engine/enums/VRTouchpad) , mode :  [Enum.VRTouchpadMode](/docs/nl-nl/reference/engine/enums/VRTouchpadMode) ) : ()

 |

Evenementen

|

[NavigationRequested](#NavigationRequested) (cframe :  [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame) , inputUserCFrame :  [Enum.UserCFrame](/docs/nl-nl/reference/engine/enums/UserCFrame) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[TouchpadModeChanged](#TouchpadModeChanged) (pad :  [Enum.VRTouchpad](/docs/nl-nl/reference/engine/enums/VRTouchpad) , mode :  [Enum.VRTouchpadMode](/docs/nl-nl/reference/engine/enums/VRTouchpadMode) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[UserCFrameChanged](#UserCFrameChanged) (type :  [Enum.UserCFrame](/docs/nl-nl/reference/engine/enums/UserCFrame) , value :  [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[UserCFrameEnabled](#UserCFrameEnabled) (type :  [Enum.UserCFrame](/docs/nl-nl/reference/engine/enums/UserCFrame) , enabled :  [boolean](/docs/nl-nl/luau/booleans) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

VRService

```

local VRService = game:GetService("VRService")

local part = workspace.Part

local handOffset = VRService:GetUserCFrame(Enum.UserCFrame.LeftHand)

-- Houd rekening met de hoofdschaling

handOffset = handOffset.Rotation + handOffset.Position * workspace.CurrentCamera.HeadScale

part.CFrame = workspace.CurrentCamera.CFrame * handOffset

```

---

API-referentie

Eigenschappen

AutomaticScaling

Parallel lezen

Mogelijkheden: Input

VRService.AutomaticScaling :[Enum.VRScaling](/docs/nl-nl/reference/engine/enums/VRScaling)

Feedback geven

---

AvatarGestures

Parallel lezen

Mogelijkheden: Input

VRService.AvatarGestures :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

ControllerModels

Parallel lezen

Mogelijkheden: Input

VRService.ControllerModels :[Enum.VRControllerModelMode](/docs/nl-nl/reference/engine/enums/VRControllerModelMode)

Feedback geven

---

FadeOutViewOnCollision

Parallel lezen

Mogelijkheden: Input

VRService.FadeOutViewOnCollision :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

GuiInputUserCFrame

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Input

VRService.GuiInputUserCFrame :[Enum.UserCFrame](/docs/nl-nl/reference/engine/enums/UserCFrame)

Codevoorbeelden

VRService.GuiInputUserCFrame

```

local VRService = game:GetService("VRService")

if VRService.VREnabled then

	print(VRService.GuiInputUserCFrame.Name)

else

	print("Geen VR-apparaat gedetecteerd!")

end

```

Feedback geven

---

LaserPointer

Parallel lezen

Mogelijkheden: Input

VRService.LaserPointer :[Enum.VRLaserPointerMode](/docs/nl-nl/reference/engine/enums/VRLaserPointerMode)

Feedback geven

---

ThirdPersonFollowCamEnabled

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Input

VRService.ThirdPersonFollowCamEnabled :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

VREnabled

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Input

VRService.VREnabled :[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

VR Hoofd Tracking

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

	-- Stel de initiële CFrame in

	head.CFrame = VRService:GetUserCFrame(Enum.UserCFrame.Head)

	-- Volg de beweging van de VR-headset en spiegel deze voor het hoofd van het karakter

	VRService.UserCFrameChanged:Connect(TrackHead)

end

```

Feedback geven

---

Methoden

GetTouchpadMode

Mogelijkheden: Input

VRService:GetTouchpadMode (pad :[Enum.VRTouchpad](/docs/nl-nl/reference/engine/enums/VRTouchpad) ) :[Enum.VRTouchpadMode](/docs/nl-nl/reference/engine/enums/VRTouchpadMode)

Parameters

|

pad :[Enum.VRTouchpad](/docs/nl-nl/reference/engine/enums/VRTouchpad)

 |

Teruggaves

[Enum.VRTouchpadMode](/docs/nl-nl/reference/engine/enums/VRTouchpadMode)

Codevoorbeelden

VRService:GetTouchpadMode

```

local VRService = game:GetService("VRService")

VRService:GetTouchpadMode(Enum.VRTouchpad.Left)

```

Feedback geven

---

GetUserCFrame

Mogelijkheden: Input

VRService:GetUserCFrame (type :[Enum.UserCFrame](/docs/nl-nl/reference/engine/enums/UserCFrame) ) :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

Parameters

|

type :[Enum.UserCFrame](/docs/nl-nl/reference/engine/enums/UserCFrame)

 |

Teruggaves

[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

Codevoorbeelden

VRService:GetUserCFrame

```

local Workspace = game:GetService("Workspace")

local VRService = game:GetService("VRService")

local camera = Workspace.CurrentCamera

local part = script.Parent.Part

local handOffset = VRService:GetUserCFrame(Enum.UserCFrame.LeftHand)

-- Houd rekening met headscale

handOffset = handOffset.Rotation + handOffset.Position * camera.HeadScale

part.CFrame = camera.CFrame * handOffset

```

Feedback geven

---

GetUserCFrameEnabled

Mogelijkheden: Input

VRService:GetUserCFrameEnabled (type :[Enum.UserCFrame](/docs/nl-nl/reference/engine/enums/UserCFrame) ) :[boolean](/docs/nl-nl/luau/booleans)

Parameters

|

type :[Enum.UserCFrame](/docs/nl-nl/reference/engine/enums/UserCFrame)

 |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

VRService:GetUserCFrameEnabled

```

local VRService = game:GetService("VRService")

local isEnabled = VRService:GetUserCFrameEnabled(Enum.UserCFrame.Head)

if isEnabled then

	print("VR-apparaat is ingeschakeld!")

else

	print("VR-apparaat is gedeactiveerd!")

end

```

Feedback geven

---

RecenterUserHeadCFrame

Mogelijkheden: Input

VRService:RecenterUserHeadCFrame () : ()

Teruggaves

()

Codevoorbeelden

VRService:RecenterUserHeadCFrame

```

local VRService = game:GetService("VRService")

VRService:RecenterUserHeadCFrame()

```

Feedback geven

---

RequestNavigation

Mogelijkheden: Input

VRService:RequestNavigation (

cframe :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame) , inputUserCFrame :[Enum.UserCFrame](/docs/nl-nl/reference/engine/enums/UserCFrame)

) : ()

Parameters

|

cframe :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

 |
|

inputUserCFrame :[Enum.UserCFrame](/docs/nl-nl/reference/engine/enums/UserCFrame)

 |

Teruggaves

()

Codevoorbeelden

VRService:RequestNavigation

```

local VRService = game:GetService("VRService")

local destination = workspace:FindFirstChild("NavigationDestination")

VRService:RequestNavigation(Enum.UserCFrame.Head, destination.CFrame)

```

Feedback geven

---

SetTouchpadMode

Mogelijkheden: Input

VRService:SetTouchpadMode (

pad :[Enum.VRTouchpad](/docs/nl-nl/reference/engine/enums/VRTouchpad) , mode :[Enum.VRTouchpadMode](/docs/nl-nl/reference/engine/enums/VRTouchpadMode)

) : ()

Parameters

|

pad :[Enum.VRTouchpad](/docs/nl-nl/reference/engine/enums/VRTouchpad)

 |
|

mode :[Enum.VRTouchpadMode](/docs/nl-nl/reference/engine/enums/VRTouchpadMode)

 |

Teruggaves

()

Codevoorbeelden

VRService:SetTouchpadMode

```

local VRService = game:GetService("VRService")

VRService:SetTouchpadMode(Enum.VRTouchpad.Left, Enum.VRTouchpadMode.Touch)

```

Feedback geven

---

Evenementen

NavigationRequested

Mogelijkheden: Input

VRService.NavigationRequested (

cframe :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame) , inputUserCFrame :[Enum.UserCFrame](/docs/nl-nl/reference/engine/enums/UserCFrame)

) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

cframe :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

 |
|

inputUserCFrame :[Enum.UserCFrame](/docs/nl-nl/reference/engine/enums/UserCFrame)

 |

Codevoorbeelden

VRService.NavigationRequested

```

local VRService = game:GetService("VRService")

VRService.NavigationRequested:Connect(function(cframe, inputUserCFrame)

	print(inputUserCFrame.Name .. " heeft een aanvraag gedaan met CFrame: " .. cframe)

end)

```

Feedback geven

---

TouchpadModeChanged

Mogelijkheden: Input

VRService.TouchpadModeChanged (

pad :[Enum.VRTouchpad](/docs/nl-nl/reference/engine/enums/VRTouchpad) , mode :[Enum.VRTouchpadMode](/docs/nl-nl/reference/engine/enums/VRTouchpadMode)

) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

pad :[Enum.VRTouchpad](/docs/nl-nl/reference/engine/enums/VRTouchpad)

 |
|

mode :[Enum.VRTouchpadMode](/docs/nl-nl/reference/engine/enums/VRTouchpadMode)

 |

Codevoorbeelden

VRService.TouchpadModeChanged

```

local VRService = game:GetService("VRService")

VRService.TouchpadModeChanged:Connect(function(pad, mode)

	print(pad.Name .. " Touchpad veranderd naar status: " .. mode.Name)

end)

```

Feedback geven

---

UserCFrameChanged

Mogelijkheden: Input

VRService.UserCFrameChanged (

type :[Enum.UserCFrame](/docs/nl-nl/reference/engine/enums/UserCFrame) , value :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

type :[Enum.UserCFrame](/docs/nl-nl/reference/engine/enums/UserCFrame)

 |
|

value :[CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)

 |

Codevoorbeelden

VRService.UserCFrameChanged

```

local VRService = game:GetService("VRService")

VRService.UserCFrameChanged:Connect(function(userCFrameType, cframeValue)

	print(userCFrameType.Name .. " is veranderd. Geüpdatete Frame: " .. tostring(cframeValue))

end)

```

Feedback geven

---

UserCFrameEnabled

Mogelijkheden: Input

VRService.UserCFrameEnabled (

type :[Enum.UserCFrame](/docs/nl-nl/reference/engine/enums/UserCFrame) , enabled :[boolean](/docs/nl-nl/luau/booleans)

) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

type :[Enum.UserCFrame](/docs/nl-nl/reference/engine/enums/UserCFrame)

 |
|

enabled :[boolean](/docs/nl-nl/luau/booleans)

 |

Codevoorbeelden

VRService.UserCFrameEnabled

```

local VRService = game:GetService("VRService")

VRService.UserCFrameEnabled:Connect(function(type, enabled)

	if enabled then

		print(type.Name .. " is ingeschakeld!")

	else

		print(type.Name .. " is uitgeschakeld!")

	end

end)

```

Feedback geven

---

Ga naar

▼

VRService

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[AutomaticScaling](#AutomaticScaling)

[AvatarGestures](#AvatarGestures)

[ControllerModels](#ControllerModels)

[FadeOutViewOnCollision](#FadeOutViewOnCollision)

[GuiInputUserCFrame](#GuiInputUserCFrame)

[LaserPointer](#LaserPointer)

[ThirdPersonFollowCamEnabled](#ThirdPersonFollowCamEnabled)

[VREnabled](#VREnabled)

[Methoden](#methods)

[GetTouchpadMode()](#GetTouchpadMode)

[GetUserCFrame()](#GetUserCFrame)

[GetUserCFrameEnabled()](#GetUserCFrameEnabled)

[RecenterUserHeadCFrame()](#RecenterUserHeadCFrame)

[RequestNavigation()](#RequestNavigation)

[SetTouchpadMode()](#SetTouchpadMode)

[Evenementen](#events)

[NavigationRequested](#NavigationRequested)

[TouchpadModeChanged](#TouchpadModeChanged)

[UserCFrameChanged](#UserCFrameChanged)

[UserCFrameEnabled](#UserCFrameEnabled)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
