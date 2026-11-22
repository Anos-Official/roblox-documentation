<!-- Source: https://create.roblox.com/docs/reference/engine/classes/TeleportService -->

TeleportService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/TeleportService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [TeleportService](/docs/reference/engine/classes/TeleportService)

English

Feedback

Engine Class

TeleportService

Not Creatable

Service

---

## Summary

Properties

|

[CustomizedTeleportUI](#CustomizedTeleportUI) :[boolean](/docs/luau/booleans)

Deprecated

 |
| --- | --- |

Methods

|

[GetArrivingTeleportGui](#GetArrivingTeleportGui) () :[Instance](/docs/reference/engine/datatypes/Instance)

 |
|

[GetLocalPlayerTeleportData](#GetLocalPlayerTeleportData) () : Variant

 |
|

[GetPlayerPlaceInstanceAsync](#GetPlayerPlaceInstanceAsync) (userId :  [User](/docs/reference/engine/datatypes/User) ) :[Tuple](/docs/luau/tuples)

 |
|

[GetTeleportSetting](#GetTeleportSetting) (setting :  [string](/docs/luau/strings) ) : Variant

 |
|

[PromptExperienceDetailsAsync](#PromptExperienceDetailsAsync) (player :  [Player](/docs/reference/engine/classes/Player) , universeId :  [number](/docs/luau/numbers) ) :[Enum.PromptExperienceDetailsResult](/docs/reference/engine/enums/PromptExperienceDetailsResult)

 |
|

[ReserveServer](#ReserveServer) (placeId :  [number](/docs/luau/numbers) ) :[Tuple](/docs/luau/tuples)

Deprecated

 |
|

[ReserveServerAsync](#ReserveServerAsync) (placeId :  [number](/docs/luau/numbers) ) :[Tuple](/docs/luau/tuples)

Deprecated

 |
|

[SetTeleportGui](#SetTeleportGui) (gui :  [Instance](/docs/reference/engine/datatypes/Instance) ) : ()

 |
|

[SetTeleportSetting](#SetTeleportSetting) (setting :  [string](/docs/luau/strings) , value :  Variant ) : ()

 |
|

[Teleport](#Teleport) (placeId :  [number](/docs/luau/numbers) , player :  [Instance](/docs/reference/engine/datatypes/Instance) , teleportData :  Variant , customLoadingScreen :  [Instance](/docs/reference/engine/datatypes/Instance) ) : ()

Deprecated

 |
|

[TeleportAsync](#TeleportAsync) (placeId :  [number](/docs/luau/numbers) , players :  Instances , teleportOptions :  [Instance](/docs/reference/engine/datatypes/Instance) ) :[Instance](/docs/reference/engine/datatypes/Instance)

 |
|

[TeleportPartyAsync](#TeleportPartyAsync) (placeId :  [number](/docs/luau/numbers) , players :  Instances , teleportData :  Variant , customLoadingScreen :  [Instance](/docs/reference/engine/datatypes/Instance) ) :[string](/docs/luau/strings)

Deprecated

 |
|

[TeleportToPlaceInstance](#TeleportToPlaceInstance) (placeId :  [number](/docs/luau/numbers) , instanceId :  [string](/docs/luau/strings) , player :  [Instance](/docs/reference/engine/datatypes/Instance) , spawnName :  [string](/docs/luau/strings) , teleportData :  Variant , customLoadingScreen :  [Instance](/docs/reference/engine/datatypes/Instance) ) : ()

Deprecated

 |
|

[TeleportToPrivateServer](#TeleportToPrivateServer) (placeId :  [number](/docs/luau/numbers) , reservedServerAccessCode :  [string](/docs/luau/strings) , players :  Instances , spawnName :  [string](/docs/luau/strings) , teleportData :  Variant , customLoadingScreen :  [Instance](/docs/reference/engine/datatypes/Instance) ) : ()

Deprecated

 |
|

[TeleportToSpawnByName](#TeleportToSpawnByName) (placeId :  [number](/docs/luau/numbers) , spawnName :  [string](/docs/luau/strings) , player :  [Instance](/docs/reference/engine/datatypes/Instance) , teleportData :  Variant , customLoadingScreen :  [Instance](/docs/reference/engine/datatypes/Instance) ) : ()

Deprecated

 |

Events

|

[LocalPlayerArrivedFromTeleport](#LocalPlayerArrivedFromTeleport) (loadingGui :  [Instance](/docs/reference/engine/datatypes/Instance) , dataTable :  Variant ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |
|

[TeleportInitFailed](#TeleportInitFailed) (player :  [Instance](/docs/reference/engine/datatypes/Instance) , teleportResult :  [Enum.TeleportResult](/docs/reference/engine/enums/TeleportResult) , errorMessage :  [string](/docs/luau/strings) , placeId :  [number](/docs/luau/numbers) , teleportOptions :  [Instance](/docs/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Properties

CustomizedTeleportUI

Deprecated

Show details

---

Methods

GetArrivingTeleportGui

Capabilities: UI, Teleport

TeleportService:GetArrivingTeleportGui () :[Instance](/docs/reference/engine/datatypes/Instance)

Returns

[Instance](/docs/reference/engine/datatypes/Instance)

Code Samples

Handling a Teleport Loading GUI

```

local TeleportService = game:GetService("TeleportService")

local Players = game:GetService("Players")

local ReplicatedFirst = game:GetService("ReplicatedFirst")

local customLoadingScreen = TeleportService:GetArrivingTeleportGui()

if customLoadingScreen then

	local playerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

	ReplicatedFirst:RemoveDefaultLoadingScreen()

	customLoadingScreen.Parent = playerGui

	task.wait(5)

	customLoadingScreen:Destroy()

end

```

Provide feedback

---

GetLocalPlayerTeleportData

Capabilities: Teleport

TeleportService:GetLocalPlayerTeleportData () : Variant

Returns

Variant

Code Samples

Getting LocalPlayer Teleport Data

```

local TeleportService = game:GetService("TeleportService")

local teleportData = TeleportService:GetLocalPlayerTeleportData()

print("Local player arrived with this data:", teleportData)

```

Provide feedback

---

GetPlayerPlaceInstanceAsync

Yields

Capabilities: Teleport

TeleportService:GetPlayerPlaceInstanceAsync (userId :[User](/docs/reference/engine/datatypes/User) ) :[Tuple](/docs/luau/tuples)

Parameters

|

userId :[User](/docs/reference/engine/datatypes/User)

 |

Returns

[Tuple](/docs/luau/tuples)

Code Samples

Following Another Player

```

local TeleportService = game:GetService("TeleportService")

local Players = game:GetService("Players")

Players.PlayerAdded:Connect(function(player)

	local followId = player.FollowUserId

	if followId and followId ~= 0 then

		-- Is this player following anyone? If so, find out where they are

		local success, currentInstance, error, placeId, jobIdOrErr = pcall(function()

			return TeleportService:GetPlayerPlaceInstanceAsync(followId)

		end)

			-- followId is the user ID of the player that you want to retrieve the place and job ID for

		if success then

			-- Teleports player on success based off jobId

			TeleportService:TeleportToPlaceInstance(placeId, jobIdOrErr, player)

		else

			-- Posts a warning based off returning error

			warn(jobIdOrErr)

		end

	else

		warn(("Player %d is not following another player!"):format(player.UserId))

	end

end)

```

Provide feedback

---

GetTeleportSetting

Capabilities: Teleport

TeleportService:GetTeleportSetting (setting :[string](/docs/luau/strings) ) : Variant

Parameters

|

setting :[string](/docs/luau/strings)

 |

Returns

Variant

Provide feedback

---

PromptExperienceDetailsAsync

Yields

Capabilities: Teleport

TeleportService:PromptExperienceDetailsAsync (

player :[Player](/docs/reference/engine/classes/Player) , universeId :[number](/docs/luau/numbers)

) :[Enum.PromptExperienceDetailsResult](/docs/reference/engine/enums/PromptExperienceDetailsResult)

Parameters

|

player :[Player](/docs/reference/engine/classes/Player)

 |
|

universeId :[number](/docs/luau/numbers)

 |

Returns

[Enum.PromptExperienceDetailsResult](/docs/reference/engine/enums/PromptExperienceDetailsResult)

Code Samples

Show Experience Details to Player

```

local TeleportService = game:GetService("TeleportService")

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local success, result = pcall(function()

	TeleportService:PromptExperienceDetailsAsync(player, 8357232245)

end)

if not success then

	warn("Error prompting experience details: " .. tostring(result))

end

if result == Enum.PromptExperienceDetailsResult.PromptClosed then

	print("Player closed the experience details prompt")

elseif result == Enum.PromptExperienceDetailsResult.TeleportAttempted then

	print("Player chose to teleport to the experience")

end

```

Provide feedback

---

ReserveServer

Deprecated

Show details

---

ReserveServerAsync

Deprecated

Show details

---

SetTeleportGui

Capabilities: UI, Teleport

TeleportService:SetTeleportGui (gui :[Instance](/docs/reference/engine/datatypes/Instance) ) : ()

Parameters

|

gui :[Instance](/docs/reference/engine/datatypes/Instance)

 |

Returns

()

Code Samples

Teleporting the local player

```

local TeleportService = game:GetService("TeleportService")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Players = game:GetService("Players")

local playerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

local PLACE_ID = 0 -- replace here

local loadingGui = ReplicatedStorage:FindFirstChild("LoadingGui")

-- parent the loading gui for this place

loadingGui.Parent = playerGui

-- set the loading gui for the destination place

TeleportService:SetTeleportGui(loadingGui)

TeleportService:Teleport(PLACE_ID)

```

Provide feedback

---

SetTeleportSetting

Capabilities: Teleport

TeleportService:SetTeleportSetting (

setting :[string](/docs/luau/strings) , value : Variant

) : ()

Parameters

|

setting :[string](/docs/luau/strings)

 |
|

value : Variant

 |

Returns

()

Provide feedback

---

Teleport

Deprecated

Show details

---

TeleportAsync

Yields

Capabilities: UI, Teleport

TeleportService:TeleportAsync (

placeId :[number](/docs/luau/numbers) , players : Instances , teleportOptions :[Instance](/docs/reference/engine/datatypes/Instance)

) :[Instance](/docs/reference/engine/datatypes/Instance)

Parameters

|

placeId :[number](/docs/luau/numbers)

 |
|

players : Instances

 |
|

teleportOptions :[Instance](/docs/reference/engine/datatypes/Instance)

Default Value: nil |

Returns

[Instance](/docs/reference/engine/datatypes/Instance)

Provide feedback

---

TeleportPartyAsync

Deprecated

Show details

---

TeleportToPlaceInstance

Deprecated

Show details

---

TeleportToPrivateServer

Deprecated

Show details

---

TeleportToSpawnByName

Deprecated

Show details

---

Events

LocalPlayerArrivedFromTeleport

Capabilities: Teleport

TeleportService.LocalPlayerArrivedFromTeleport (

loadingGui :[Instance](/docs/reference/engine/datatypes/Instance) , dataTable : Variant

) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

loadingGui :[Instance](/docs/reference/engine/datatypes/Instance)

 |
|

dataTable : Variant

 |

Provide feedback

---

TeleportInitFailed

Capabilities: Teleport

TeleportService.TeleportInitFailed (

player :[Instance](/docs/reference/engine/datatypes/Instance) , teleportResult :[Enum.TeleportResult](/docs/reference/engine/enums/TeleportResult) , errorMessage :[string](/docs/luau/strings) , placeId :[number](/docs/luau/numbers) , teleportOptions :[Instance](/docs/reference/engine/datatypes/Instance)

) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

player :[Instance](/docs/reference/engine/datatypes/Instance)

 |
|

teleportResult :[Enum.TeleportResult](/docs/reference/engine/enums/TeleportResult)

 |
|

errorMessage :[string](/docs/luau/strings)

 |
|

placeId :[number](/docs/luau/numbers)

 |
|

teleportOptions :[Instance](/docs/reference/engine/datatypes/Instance)

 |

Provide feedback

---

Jump to

▼

TeleportService

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[CustomizedTeleportUI](#CustomizedTeleportUI)

[Methods](#methods)

[GetArrivingTeleportGui()](#GetArrivingTeleportGui)

[GetLocalPlayerTeleportData()](#GetLocalPlayerTeleportData)

[GetPlayerPlaceInstanceAsync()](#GetPlayerPlaceInstanceAsync)

[GetTeleportSetting()](#GetTeleportSetting)

[PromptExperienceDetailsAsync()](#PromptExperienceDetailsAsync)

[ReserveServer()](#ReserveServer)

[ReserveServerAsync()](#ReserveServerAsync)

[SetTeleportGui()](#SetTeleportGui)

[SetTeleportSetting()](#SetTeleportSetting)

[Teleport()](#Teleport)

[TeleportAsync()](#TeleportAsync)

[TeleportPartyAsync()](#TeleportPartyAsync)

[TeleportToPlaceInstance()](#TeleportToPlaceInstance)

[TeleportToPrivateServer()](#TeleportToPrivateServer)

[TeleportToSpawnByName()](#TeleportToSpawnByName)

[Events](#events)

[LocalPlayerArrivedFromTeleport](#LocalPlayerArrivedFromTeleport)

[TeleportInitFailed](#TeleportInitFailed)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
