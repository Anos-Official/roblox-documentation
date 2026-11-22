<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/StarterPlayer -->

StarterPlayer | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/StarterPlayer.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [StarterPlayer](/docs/en-us/reference/engine/classes/StarterPlayer)

English

Feedback

Engine Class

StarterPlayer

Not Creatable

Service

---

## Summary

Properties

|

[AllowCustomAnimations](#AllowCustomAnimations) :[boolean](/docs/en-us/luau/booleans)

 |
| --- | --- |
|

[AutoJumpEnabled](#AutoJumpEnabled) :[boolean](/docs/en-us/luau/booleans)

 |
|

[AvatarJointUpgrade](#AvatarJointUpgrade) :[Enum.RolloutState](/docs/en-us/reference/engine/enums/RolloutState)

 |
|

[CameraMaxZoomDistance](#CameraMaxZoomDistance) :[number](/docs/en-us/luau/numbers)

 |
|

[CameraMinZoomDistance](#CameraMinZoomDistance) :[number](/docs/en-us/luau/numbers)

 |
|

[CameraMode](#CameraMode) :[Enum.CameraMode](/docs/en-us/reference/engine/enums/CameraMode)

 |
|

[CharacterBreakJointsOnDeath](#CharacterBreakJointsOnDeath) :[boolean](/docs/en-us/luau/booleans)

 |
|

[CharacterJumpHeight](#CharacterJumpHeight) :[number](/docs/en-us/luau/numbers)

 |
|

[CharacterJumpPower](#CharacterJumpPower) :[number](/docs/en-us/luau/numbers)

 |
|

[CharacterMaxSlopeAngle](#CharacterMaxSlopeAngle) :[number](/docs/en-us/luau/numbers)

 |
|

[CharacterUseJumpPower](#CharacterUseJumpPower) :[boolean](/docs/en-us/luau/booleans)

 |
|

[CharacterWalkSpeed](#CharacterWalkSpeed) :[number](/docs/en-us/luau/numbers)

 |
|

[ClassicDeath](#ClassicDeath) :[boolean](/docs/en-us/luau/booleans)

 |
|

[CreateDefaultPlayerModule](#CreateDefaultPlayerModule) :[boolean](/docs/en-us/luau/booleans)

 |
|

[DevCameraOcclusionMode](#DevCameraOcclusionMode) :[Enum.DevCameraOcclusionMode](/docs/en-us/reference/engine/enums/DevCameraOcclusionMode)

 |
|

[DevComputerCameraMovementMode](#DevComputerCameraMovementMode) :[Enum.DevComputerCameraMovementMode](/docs/en-us/reference/engine/enums/DevComputerCameraMovementMode)

 |
|

[DevComputerMovementMode](#DevComputerMovementMode) :[Enum.DevComputerMovementMode](/docs/en-us/reference/engine/enums/DevComputerMovementMode)

 |
|

[DevTouchCameraMovementMode](#DevTouchCameraMovementMode) :[Enum.DevTouchCameraMovementMode](/docs/en-us/reference/engine/enums/DevTouchCameraMovementMode)

 |
|

[DevTouchMovementMode](#DevTouchMovementMode) :[Enum.DevTouchMovementMode](/docs/en-us/reference/engine/enums/DevTouchMovementMode)

 |
|

[EnableDynamicHeads](#EnableDynamicHeads) :[Enum.LoadDynamicHeads](/docs/en-us/reference/engine/enums/LoadDynamicHeads)

 |
|

[EnableMouseLockOption](#EnableMouseLockOption) :[boolean](/docs/en-us/luau/booleans)

 |
|

[HealthDisplayDistance](#HealthDisplayDistance) :[number](/docs/en-us/luau/numbers)

 |
|

[LoadCharacterAppearance](#LoadCharacterAppearance) :[boolean](/docs/en-us/luau/booleans)

 |
|

[LoadCharacterLayeredClothing ](#LoadCharacterLayeredClothing-) :[Enum.LoadCharacterLayeredClothing](/docs/en-us/reference/engine/enums/LoadCharacterLayeredClothing)

 |
|

[LuaCharacterController](#LuaCharacterController) :[Enum.CharacterControlMode](/docs/en-us/reference/engine/enums/CharacterControlMode)

 |
|

[NameDisplayDistance](#NameDisplayDistance) :[number](/docs/en-us/luau/numbers)

 |
|

[UserEmotesEnabled](#UserEmotesEnabled) :[boolean](/docs/en-us/luau/booleans)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Properties

AllowCustomAnimations

Hidden

Roblox Script Security

Read Parallel

Capabilities: Players

StarterPlayer.AllowCustomAnimations :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

AutoJumpEnabled

Read Parallel

Capabilities: Players

StarterPlayer.AutoJumpEnabled :[boolean](/docs/en-us/luau/booleans)

Code Samples

Auto-Jump Toggle

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local button = script.Parent

local function update()

	-- Update button text

	if player.AutoJumpEnabled then

		button.Text = "Auto-Jump is ON"

	else

		button.Text = "Auto-Jump is OFF"

	end

	-- Reflect the property in the player's character, if they have one

	if player.Character then

		local human = player.Character:FindFirstChild("Humanoid")

		if human then

			human.AutoJumpEnabled = player.AutoJumpEnabled

		end

	end

end

local function onActivated()

	-- Toggle auto-jump

	player.AutoJumpEnabled = not player.AutoJumpEnabled

	-- Update everything else

	update()

end

button.Activated:Connect(onActivated)

update()

```

Provide feedback

---

AvatarJointUpgrade

Not Replicated

Roblox Script Security

Read Parallel

Capabilities: Players

StarterPlayer.AvatarJointUpgrade :[Enum.RolloutState](/docs/en-us/reference/engine/enums/RolloutState)

Provide feedback

---

CameraMaxZoomDistance

Read Parallel

Capabilities: Players

StarterPlayer.CameraMaxZoomDistance :[number](/docs/en-us/luau/numbers)

Code Samples

Setting Camera Zoom Distance

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

player.CameraMaxZoomDistance = 50

player.CameraMinZoomDistance = 75

```

Provide feedback

---

CameraMinZoomDistance

Read Parallel

Capabilities: Players

StarterPlayer.CameraMinZoomDistance :[number](/docs/en-us/luau/numbers)

Code Samples

Setting Camera Zoom Distance

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

player.CameraMaxZoomDistance = 50

player.CameraMinZoomDistance = 75

```

Provide feedback

---

CameraMode

Read Parallel

Capabilities: Players

StarterPlayer.CameraMode :[Enum.CameraMode](/docs/en-us/reference/engine/enums/CameraMode)

Code Samples

Playing in First Person

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

player.CameraMode = Enum.CameraMode.LockFirstPerson

```

Provide feedback

---

CharacterBreakJointsOnDeath

Read Parallel

Capabilities: Players

StarterPlayer.CharacterBreakJointsOnDeath :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

CharacterJumpHeight

Read Parallel

Capabilities: Players

StarterPlayer.CharacterJumpHeight :[number](/docs/en-us/luau/numbers)

Provide feedback

---

CharacterJumpPower

Read Parallel

Capabilities: Players

StarterPlayer.CharacterJumpPower :[number](/docs/en-us/luau/numbers)

Provide feedback

---

CharacterMaxSlopeAngle

Read Parallel

Capabilities: Players

StarterPlayer.CharacterMaxSlopeAngle :[number](/docs/en-us/luau/numbers)

Provide feedback

---

CharacterUseJumpPower

Read Parallel

Capabilities: Players

StarterPlayer.CharacterUseJumpPower :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

CharacterWalkSpeed

Read Parallel

Capabilities: Players

StarterPlayer.CharacterWalkSpeed :[number](/docs/en-us/luau/numbers)

Provide feedback

---

ClassicDeath

Read Parallel

Capabilities: Players

StarterPlayer.ClassicDeath :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

CreateDefaultPlayerModule

Read Parallel

Capabilities: Players, PluginOrOpenCloud

StarterPlayer.CreateDefaultPlayerModule :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

DevCameraOcclusionMode

Read Parallel

Capabilities: Players

StarterPlayer.DevCameraOcclusionMode :[Enum.DevCameraOcclusionMode](/docs/en-us/reference/engine/enums/DevCameraOcclusionMode)

Provide feedback

---

DevComputerCameraMovementMode

Read Parallel

Capabilities: Players

StarterPlayer.DevComputerCameraMovementMode :[Enum.DevComputerCameraMovementMode](/docs/en-us/reference/engine/enums/DevComputerCameraMovementMode)

Provide feedback

---

DevComputerMovementMode

Read Parallel

Capabilities: Players

StarterPlayer.DevComputerMovementMode :[Enum.DevComputerMovementMode](/docs/en-us/reference/engine/enums/DevComputerMovementMode)

Provide feedback

---

DevTouchCameraMovementMode

Read Parallel

Capabilities: Players

StarterPlayer.DevTouchCameraMovementMode :[Enum.DevTouchCameraMovementMode](/docs/en-us/reference/engine/enums/DevTouchCameraMovementMode)

Provide feedback

---

DevTouchMovementMode

Read Parallel

Capabilities: Players

StarterPlayer.DevTouchMovementMode :[Enum.DevTouchMovementMode](/docs/en-us/reference/engine/enums/DevTouchMovementMode)

Provide feedback

---

EnableDynamicHeads

Not Scriptable

Read Parallel

Capabilities: Players

StarterPlayer.EnableDynamicHeads :[Enum.LoadDynamicHeads](/docs/en-us/reference/engine/enums/LoadDynamicHeads)

Provide feedback

---

EnableMouseLockOption

Read Parallel

Capabilities: Players

StarterPlayer.EnableMouseLockOption :[boolean](/docs/en-us/luau/booleans)

Code Samples

Enabling a Player's Mouse Lock

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

while true do

	player.DevEnableMouseLock = not player.DevEnableMouseLock

	task.wait(5)

end

```

Provide feedback

---

HealthDisplayDistance

Read Parallel

Capabilities: Players

StarterPlayer.HealthDisplayDistance :[number](/docs/en-us/luau/numbers)

Code Samples

Hiding Player Health and Names

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

player.HealthDisplayDistance = 0

player.NameDisplayDistance = 0

```

Provide feedback

---

LoadCharacterAppearance

Read Parallel

Capabilities: Players

StarterPlayer.LoadCharacterAppearance :[boolean](/docs/en-us/luau/booleans)

Code Samples

Disabling a Player's Appearance

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

player.CanLoadCharacterAppearance = false

```

Provide feedback

---

LoadCharacterLayeredClothing

Not Replicated

Not Scriptable

Read Parallel

Capabilities: Players

StarterPlayer.LoadCharacterLayeredClothing :[Enum.LoadCharacterLayeredClothing](/docs/en-us/reference/engine/enums/LoadCharacterLayeredClothing)

Provide feedback

---

LuaCharacterController

Read Parallel

Capabilities: Players

StarterPlayer.LuaCharacterController :[Enum.CharacterControlMode](/docs/en-us/reference/engine/enums/CharacterControlMode)

Provide feedback

---

NameDisplayDistance

Read Parallel

Capabilities: Players

StarterPlayer.NameDisplayDistance :[number](/docs/en-us/luau/numbers)

Code Samples

Hiding Player Health and Names

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

player.HealthDisplayDistance = 0

player.NameDisplayDistance = 0

```

Provide feedback

---

UserEmotesEnabled

Read Parallel

Capabilities: Players

StarterPlayer.UserEmotesEnabled :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

Jump to

▼

StarterPlayer

[Summary](#summary)

[Properties](#summary-properties)

[Properties](#properties)

[AllowCustomAnimations](#AllowCustomAnimations)

[AutoJumpEnabled](#AutoJumpEnabled)

[AvatarJointUpgrade](#AvatarJointUpgrade)

[CameraMaxZoomDistance](#CameraMaxZoomDistance)

[CameraMinZoomDistance](#CameraMinZoomDistance)

[CameraMode](#CameraMode)

[CharacterBreakJointsOnDeath](#CharacterBreakJointsOnDeath)

[CharacterJumpHeight](#CharacterJumpHeight)

[CharacterJumpPower](#CharacterJumpPower)

[CharacterMaxSlopeAngle](#CharacterMaxSlopeAngle)

[CharacterUseJumpPower](#CharacterUseJumpPower)

[CharacterWalkSpeed](#CharacterWalkSpeed)

[ClassicDeath](#ClassicDeath)

[CreateDefaultPlayerModule](#CreateDefaultPlayerModule)

[DevCameraOcclusionMode](#DevCameraOcclusionMode)

[DevComputerCameraMovementMode](#DevComputerCameraMovementMode)

[DevComputerMovementMode](#DevComputerMovementMode)

[DevTouchCameraMovementMode](#DevTouchCameraMovementMode)

[DevTouchMovementMode](#DevTouchMovementMode)

[EnableDynamicHeads](#EnableDynamicHeads)

[EnableMouseLockOption](#EnableMouseLockOption)

[HealthDisplayDistance](#HealthDisplayDistance)

[LoadCharacterAppearance](#LoadCharacterAppearance)

[LoadCharacterLayeredClothing ](#LoadCharacterLayeredClothing-)

[LuaCharacterController](#LuaCharacterController)

[NameDisplayDistance](#NameDisplayDistance)

[UserEmotesEnabled](#UserEmotesEnabled)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
