<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/StarterPlayer -->

StarterPlayer | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [StarterPlayer](/docs/nl-nl/reference/engine/classes/StarterPlayer)

Nederlands

Feedback

Engine-klasse

StarterPlayer

Niet maakbaar

Service

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/StarterPlayer)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[AllowCustomAnimations](#AllowCustomAnimations) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |
|

[AutoJumpEnabled](#AutoJumpEnabled) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[AvatarJointUpgrade](#AvatarJointUpgrade) :[Enum.RolloutState](/docs/nl-nl/reference/engine/enums/RolloutState)

 |
|

[CameraMaxZoomDistance](#CameraMaxZoomDistance) :[number](/docs/nl-nl/luau/numbers)

 |
|

[CameraMinZoomDistance](#CameraMinZoomDistance) :[number](/docs/nl-nl/luau/numbers)

 |
|

[CameraMode](#CameraMode) :[Enum.CameraMode](/docs/nl-nl/reference/engine/enums/CameraMode)

 |
|

[CharacterBreakJointsOnDeath](#CharacterBreakJointsOnDeath) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[CharacterJumpHeight](#CharacterJumpHeight) :[number](/docs/nl-nl/luau/numbers)

 |
|

[CharacterJumpPower](#CharacterJumpPower) :[number](/docs/nl-nl/luau/numbers)

 |
|

[CharacterMaxSlopeAngle](#CharacterMaxSlopeAngle) :[number](/docs/nl-nl/luau/numbers)

 |
|

[CharacterUseJumpPower](#CharacterUseJumpPower) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[CharacterWalkSpeed](#CharacterWalkSpeed) :[number](/docs/nl-nl/luau/numbers)

 |
|

[ClassicDeath](#ClassicDeath) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[CreateDefaultPlayerModule](#CreateDefaultPlayerModule) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[DevCameraOcclusionMode](#DevCameraOcclusionMode) :[Enum.DevCameraOcclusionMode](/docs/nl-nl/reference/engine/enums/DevCameraOcclusionMode)

 |
|

[DevComputerCameraMovementMode](#DevComputerCameraMovementMode) :[Enum.DevComputerCameraMovementMode](/docs/nl-nl/reference/engine/enums/DevComputerCameraMovementMode)

 |
|

[DevComputerMovementMode](#DevComputerMovementMode) :[Enum.DevComputerMovementMode](/docs/nl-nl/reference/engine/enums/DevComputerMovementMode)

 |
|

[DevTouchCameraMovementMode](#DevTouchCameraMovementMode) :[Enum.DevTouchCameraMovementMode](/docs/nl-nl/reference/engine/enums/DevTouchCameraMovementMode)

 |
|

[DevTouchMovementMode](#DevTouchMovementMode) :[Enum.DevTouchMovementMode](/docs/nl-nl/reference/engine/enums/DevTouchMovementMode)

 |
|

[EnableDynamicHeads](#EnableDynamicHeads) :[Enum.LoadDynamicHeads](/docs/nl-nl/reference/engine/enums/LoadDynamicHeads)

 |
|

[EnableMouseLockOption](#EnableMouseLockOption) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[HealthDisplayDistance](#HealthDisplayDistance) :[number](/docs/nl-nl/luau/numbers)

 |
|

[LoadCharacterAppearance](#LoadCharacterAppearance) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[LoadCharacterLayeredClothing ](#LoadCharacterLayeredClothing-) :[Enum.LoadCharacterLayeredClothing](/docs/nl-nl/reference/engine/enums/LoadCharacterLayeredClothing)

 |
|

[LuaCharacterController](#LuaCharacterController) :[Enum.CharacterControlMode](/docs/nl-nl/reference/engine/enums/CharacterControlMode)

 |
|

[NameDisplayDistance](#NameDisplayDistance) :[number](/docs/nl-nl/luau/numbers)

 |
|

[UserEmotesEnabled](#UserEmotesEnabled) :[boolean](/docs/nl-nl/luau/booleans)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

AllowCustomAnimations

Verborgen

Roblox-scriptbeveiliging

Parallel lezen

Mogelijkheden: Players

StarterPlayer.AllowCustomAnimations :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

AutoJumpEnabled

Parallel lezen

Mogelijkheden: Players

StarterPlayer.AutoJumpEnabled :[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

Auto-Jump Toggle

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local button = script.Parent

local function update()

	-- Werk de knoptekst bij

	if player.AutoJumpEnabled then

		button.Text = "Auto-Jump is AAN"

	else

		button.Text = "Auto-Jump is UIT"

	end

	-- Reflecteer de eigenschap in het karakter van de speler, als ze er een hebben

	if player.Character then

		local human = player.Character:FindFirstChild("Humanoid")

		if human then

			human.AutoJumpEnabled = player.AutoJumpEnabled

		end

	end

end

local function onActivated()

	-- Schakel auto-jump in of uit

	player.AutoJumpEnabled = not player.AutoJumpEnabled

	-- Werk alles bij

	update()

end

button.Activated:Connect(onActivated)

update()

```

Feedback geven

---

AvatarJointUpgrade

Niet gerepliceerd

Roblox-scriptbeveiliging

Parallel lezen

Mogelijkheden: Players

StarterPlayer.AvatarJointUpgrade :[Enum.RolloutState](/docs/nl-nl/reference/engine/enums/RolloutState)

Feedback geven

---

CameraMaxZoomDistance

Parallel lezen

Mogelijkheden: Players

StarterPlayer.CameraMaxZoomDistance :[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

Instellen van de camera zoomafstand

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

player.CameraMaxZoomDistance = 50

player.CameraMinZoomDistance = 75

```

Feedback geven

---

CameraMinZoomDistance

Parallel lezen

Mogelijkheden: Players

StarterPlayer.CameraMinZoomDistance :[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

Instellen van de camera zoomafstand

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

player.CameraMaxZoomDistance = 50

player.CameraMinZoomDistance = 75

```

Feedback geven

---

CameraMode

Parallel lezen

Mogelijkheden: Players

StarterPlayer.CameraMode :[Enum.CameraMode](/docs/nl-nl/reference/engine/enums/CameraMode)

Codevoorbeelden

Spelen in Eerste Persoon

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

player.CameraMode = Enum.CameraMode.LockFirstPerson

```

Feedback geven

---

CharacterBreakJointsOnDeath

Parallel lezen

Mogelijkheden: Players

StarterPlayer.CharacterBreakJointsOnDeath :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

CharacterJumpHeight

Parallel lezen

Mogelijkheden: Players

StarterPlayer.CharacterJumpHeight :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

CharacterJumpPower

Parallel lezen

Mogelijkheden: Players

StarterPlayer.CharacterJumpPower :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

CharacterMaxSlopeAngle

Parallel lezen

Mogelijkheden: Players

StarterPlayer.CharacterMaxSlopeAngle :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

CharacterUseJumpPower

Parallel lezen

Mogelijkheden: Players

StarterPlayer.CharacterUseJumpPower :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

CharacterWalkSpeed

Parallel lezen

Mogelijkheden: Players

StarterPlayer.CharacterWalkSpeed :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

ClassicDeath

Parallel lezen

Mogelijkheden: Players

StarterPlayer.ClassicDeath :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

CreateDefaultPlayerModule

Parallel lezen

Mogelijkheden: Players, PluginOrOpenCloud

StarterPlayer.CreateDefaultPlayerModule :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

DevCameraOcclusionMode

Parallel lezen

Mogelijkheden: Players

StarterPlayer.DevCameraOcclusionMode :[Enum.DevCameraOcclusionMode](/docs/nl-nl/reference/engine/enums/DevCameraOcclusionMode)

Feedback geven

---

DevComputerCameraMovementMode

Parallel lezen

Mogelijkheden: Players

StarterPlayer.DevComputerCameraMovementMode :[Enum.DevComputerCameraMovementMode](/docs/nl-nl/reference/engine/enums/DevComputerCameraMovementMode)

Feedback geven

---

DevComputerMovementMode

Parallel lezen

Mogelijkheden: Players

StarterPlayer.DevComputerMovementMode :[Enum.DevComputerMovementMode](/docs/nl-nl/reference/engine/enums/DevComputerMovementMode)

Feedback geven

---

DevTouchCameraMovementMode

Parallel lezen

Mogelijkheden: Players

StarterPlayer.DevTouchCameraMovementMode :[Enum.DevTouchCameraMovementMode](/docs/nl-nl/reference/engine/enums/DevTouchCameraMovementMode)

Feedback geven

---

DevTouchMovementMode

Parallel lezen

Mogelijkheden: Players

StarterPlayer.DevTouchMovementMode :[Enum.DevTouchMovementMode](/docs/nl-nl/reference/engine/enums/DevTouchMovementMode)

Feedback geven

---

EnableDynamicHeads

Niet scriptbaar

Parallel lezen

Mogelijkheden: Players

StarterPlayer.EnableDynamicHeads :[Enum.LoadDynamicHeads](/docs/nl-nl/reference/engine/enums/LoadDynamicHeads)

Feedback geven

---

EnableMouseLockOption

Parallel lezen

Mogelijkheden: Players

StarterPlayer.EnableMouseLockOption :[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

Het inschakelen van de muisvergrendeling van een speler

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

while true do

	player.DevEnableMouseLock = not player.DevEnableMouseLock

	task.wait(5)

end

```

Feedback geven

---

HealthDisplayDistance

Parallel lezen

Mogelijkheden: Players

StarterPlayer.HealthDisplayDistance :[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

Spelen van Gezondheid en Namen Verbergen

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

player.HealthDisplayDistance = 0

player.NameDisplayDistance = 0

```

Feedback geven

---

LoadCharacterAppearance

Parallel lezen

Mogelijkheden: Players

StarterPlayer.LoadCharacterAppearance :[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

Het Uitschakelen van de Uiterlijk van een Speler

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

player.CanLoadCharacterAppearance = false

```

Feedback geven

---

LoadCharacterLayeredClothing

Niet gerepliceerd

Niet scriptbaar

Parallel lezen

Mogelijkheden: Players

StarterPlayer.LoadCharacterLayeredClothing :[Enum.LoadCharacterLayeredClothing](/docs/nl-nl/reference/engine/enums/LoadCharacterLayeredClothing)

Feedback geven

---

LuaCharacterController

Parallel lezen

Mogelijkheden: Players

StarterPlayer.LuaCharacterController :[Enum.CharacterControlMode](/docs/nl-nl/reference/engine/enums/CharacterControlMode)

Feedback geven

---

NameDisplayDistance

Parallel lezen

Mogelijkheden: Players

StarterPlayer.NameDisplayDistance :[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

Spelen van Gezondheid en Namen Verbergen

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

player.HealthDisplayDistance = 0

player.NameDisplayDistance = 0

```

Feedback geven

---

UserEmotesEnabled

Parallel lezen

Mogelijkheden: Players

StarterPlayer.UserEmotesEnabled :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Ga naar

▼

StarterPlayer

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Eigenschappen](#properties)

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

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
