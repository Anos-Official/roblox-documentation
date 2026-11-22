<!-- Source: https://create.roblox.com/docs/reference/engine/classes/PolicyService -->

PolicyService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/PolicyService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [PolicyService](/docs/reference/engine/classes/PolicyService)

English

Feedback

Engine Class

PolicyService

Not Creatable

Service

Not Replicated

---

## Summary

Methods

|

[CanViewBrandProjectAsync](#CanViewBrandProjectAsync) (player :  [Player](/docs/reference/engine/classes/Player) , brandProjectId :  [string](/docs/luau/strings) ) :[boolean](/docs/luau/booleans)

 |
| --- | --- |
|

[GetPolicyInfoForPlayerAsync](#GetPolicyInfoForPlayerAsync) (player :  [Instance](/docs/reference/engine/datatypes/Instance) ) :[Dictionary](/docs/luau/tables#dictionaries)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Methods

CanViewBrandProjectAsync

Yields

Capabilities: Basic

PolicyService:CanViewBrandProjectAsync (

player :[Player](/docs/reference/engine/classes/Player) , brandProjectId :[string](/docs/luau/strings)

) :[boolean](/docs/luau/booleans)

Parameters

|

player :[Player](/docs/reference/engine/classes/Player)

 |
|

brandProjectId :[string](/docs/luau/strings)

 |

Returns

[boolean](/docs/luau/booleans)

Code Samples

Server-side code sample

```

-- In ServerScriptService

local Players = game:GetService("Players")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local PolicyService = game:GetService("PolicyService")

-- Pre-created RemoteEvent in ReplicatedStorage

local RemoteEvent = ReplicatedStorage:WaitForChild("RemoteEvent")

local brandedAsset = ReplicatedStorage:WaitForChild("BrandedAsset")

local defaultAsset = Instance.new("Part")

Players.PlayerAdded:Connect(function(player)

	-- PolicyService:CanViewBrandProjectAsync can only be called from the Server

	local success, canView = pcall(function()

		return PolicyService:CanViewBrandProjectAsync(player, "BRP-0123456789")

	end)

	if success and canView then

		RemoteEvent:FireClient(player, brandedAsset)

	else

		RemoteEvent:FireClient(player, defaultAsset)

	end

end)

```

Client-side code sample

```

-- In StarterPlayerScripts

local Players = game:GetService("Players")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- Pre-created RemoteEvent in ReplicatedStorage

local RemoteEvent = ReplicatedStorage:WaitForChild("RemoteEvent")

RemoteEvent.OnClientEvent:Connect(function(partToLoad)

	local clonedPart = partToLoad:Clone()

	clonedPart.Parent = workspace

end)

```

Provide feedback

---

GetPolicyInfoForPlayerAsync

Yields

Capabilities: Basic

PolicyService:GetPolicyInfoForPlayerAsync (player :[Instance](/docs/reference/engine/datatypes/Instance) ) :[Dictionary](/docs/luau/tables#dictionaries)

Parameters

|

player :[Instance](/docs/reference/engine/datatypes/Instance)

 |

Returns

[Dictionary](/docs/luau/tables#dictionaries)

Code Samples

Getting Policy Information for a Player

```

local PolicyService = game:GetService("PolicyService")

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local success, result = pcall(function()

	return PolicyService:GetPolicyInfoForPlayerAsync(player)

end)

if not success then

	warn("PolicyService error: " .. result)

elseif result.ArePaidRandomItemsRestricted then

	warn("Player cannot interact with paid random item generators")

end

```

Getting Policy Information for a Player

```

local PolicyService = game:GetService("PolicyService")

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local success, result = pcall(function()

	return PolicyService:GetPolicyInfoForPlayerAsync(player)

end)

if not success then

	warn("PolicyService error: " .. result)

elseif not result.IsEligibleToPurchaseCommerceProduct then

	warn("Player is not eligible to purchase commerce products")

end

```

Provide feedback

---

Jump to

▼

PolicyService

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[CanViewBrandProjectAsync()](#CanViewBrandProjectAsync)

[GetPolicyInfoForPlayerAsync()](#GetPolicyInfoForPlayerAsync)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
