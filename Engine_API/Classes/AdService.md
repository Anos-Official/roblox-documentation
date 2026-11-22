<!-- Source: https://create.roblox.com/docs/reference/engine/classes/AdService -->

AdService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/AdService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [AdService](/docs/reference/engine/classes/AdService)

English

Feedback

Engine Class

AdService

Not Creatable

Service

---

## Summary

Methods

|

[CreateAdRewardFromDevProductId](#CreateAdRewardFromDevProductId) (devProductId :  [number](/docs/luau/numbers) ) :[AdReward](/docs/reference/engine/datatypes/AdReward)

 |
| --- | --- |
|

[GetAdAvailabilityNowAsync](#GetAdAvailabilityNowAsync) (adFormat :  [Enum.AdFormat](/docs/reference/engine/enums/AdFormat) ) : GetAdAvailabilityNowResult

 |
|

[GetCampaignEligibilityAsync](#GetCampaignEligibilityAsync) (campaignId :  [string](/docs/luau/strings) , player :  [Player](/docs/reference/engine/classes/Player) ? ) : GetCampaignEligibilityResult

 |
|

[RegisterAdOpportunityAsync](#RegisterAdOpportunityAsync) (instance :  [Instance](/docs/reference/engine/datatypes/Instance) , placementId :  [number](/docs/luau/numbers) ? ) : ()

 |
|

[RegisterDisclosureButton](#RegisterDisclosureButton) (disclosureButton :  [GuiButton](/docs/reference/engine/classes/GuiButton) , adIntegrationPlacementId :  [string](/docs/luau/strings) ) : ()

 |
|

[ShowRewardedVideoAdAsync](#ShowRewardedVideoAdAsync) (player :  [Player](/docs/reference/engine/classes/Player) , reward :  [AdReward](/docs/reference/engine/datatypes/AdReward) , placementId :  [number](/docs/luau/numbers) ? ) :[Enum.ShowAdResult](/docs/reference/engine/enums/ShowAdResult)

 |
|

[ShowVideoAd](#ShowVideoAd) () : ()

Deprecated

 |
|

[UnregisterAdOpportunity](#UnregisterAdOpportunity) (instance :  [Instance](/docs/reference/engine/datatypes/Instance) ) : ()

 |

Events

|

[VideoAdClosed](#VideoAdClosed) (adShown :  [boolean](/docs/luau/booleans) ) :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Deprecated

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Methods

CreateAdRewardFromDevProductId

Capabilities: Monetization

AdService:CreateAdRewardFromDevProductId (devProductId :[number](/docs/luau/numbers) ) :[AdReward](/docs/reference/engine/datatypes/AdReward)

Parameters

|

devProductId :[number](/docs/luau/numbers)

 |

Returns

[AdReward](/docs/reference/engine/datatypes/AdReward)

Provide feedback

---

GetAdAvailabilityNowAsync

Yields

Capabilities: Monetization

AdService:GetAdAvailabilityNowAsync (adFormat :[Enum.AdFormat](/docs/reference/engine/enums/AdFormat) ) : GetAdAvailabilityNowResult

Parameters

|

adFormat :[Enum.AdFormat](/docs/reference/engine/enums/AdFormat)

 |

Returns

GetAdAvailabilityNowResult

Provide feedback

---

GetCampaignEligibilityAsync

Yields

Capabilities: Monetization

AdService:GetCampaignEligibilityAsync (

campaignId :[string](/docs/luau/strings) , player :[Player](/docs/reference/engine/classes/Player) ?

) : GetCampaignEligibilityResult

Parameters

|

campaignId :[string](/docs/luau/strings)

 |
|

player :[Player](/docs/reference/engine/classes/Player) ?

Default Value: nil |

Returns

GetCampaignEligibilityResult

Code Samples

Example Ad Integration

```

local AdService = game:GetService("AdService")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Players = game:GetService("Players")

local YOUR_CAMPAIGN_ID = "123" -- Enter your ad integration campaign ID from ads manager here.

local AD_INTEGRATION_IDS = {

	-- Enter your ad integration placement ID's for each asset you registered as part of your

	-- ad integration campaign.

	BrandedBuilding = "abc-123",

	BrandedScreenGui = "xyz-789",

}

-- Verify that the LocalPlayer is eligible to see your campaign

local success, result = pcall(function()

	return AdService:GetCampaignEligibilityAsync(YOUR_CAMPAIGN_ID)

end)

if success and result.IsEligible then

	-- All ad integration assets should be hidden by default. Once you know that the

	-- player is eligible, then it's safe to start showing the ad integration assets.

	local brandedBuildingModel = ReplicatedStorage.adIntegration.building

	local brandedBuildingModelDisclosureBillboardGui = brandedBuildingModel.disclosureBillboardGui

	-- Don't forget to register your ad disclosure buttons so players know who is paying for the ad!

	AdService:RegisterDisclosureButton(

		brandedBuildingModelDisclosureBillboardGui.adDisclosureButton,

		AD_INTEGRATION_IDS.BrandedBuilding

	)

	brandedBuildingModelDisclosureBillboardGui.Parent = Players.LocalPlayer.PlayerGui

	brandedBuildingModel.Parent = game.Workspace

	local brandedScreenGui = ReplicatedStorage.adIntegration.screenGui

	AdService:RegisterDisclosureButton(brandedScreenGui.adDisclosureButton, AD_INTEGRATION_IDS.BrandedScreenGui)

	brandedScreenGui.Parent = Players.LocalPlayer.PlayerGui

end

```

Provide feedback

---

RegisterAdOpportunityAsync

Yields

Capabilities: Monetization

AdService:RegisterAdOpportunityAsync (

instance :[Instance](/docs/reference/engine/datatypes/Instance) , placementId :[number](/docs/luau/numbers) ?

) : ()

Parameters

|

instance :[Instance](/docs/reference/engine/datatypes/Instance)

 |
|

placementId :[number](/docs/luau/numbers) ?

 |

Returns

()

Code Samples

Track ad opportunities

```

local AdService = game:GetService("AdService")

local playerGui = game:GetService("Players").LocalPlayer:WaitForChild("PlayerGui")

-- Create the ScreenGui and the Button

local screenGui = Instance.new("ScreenGui", playerGui)

local adButton = Instance.new("TextButton", screenGui)

-- Register the button with AdService

local success, err = pcall(function()

	-- The second parameter is an optional Placement ID (Number) parameter generated in the Creator Hub.

	-- If you choose not to provide a Placement ID, the ad opportunity is tracked under the default placement.

	AdService:RegisterAdOpportunityAsync(adButton, 1234567891234567)

end)

if not success then

	warn("Failed to register ad opportunity:", err)

end

```

Provide feedback

---

RegisterDisclosureButton

Capabilities: Monetization

AdService:RegisterDisclosureButton (

disclosureButton :[GuiButton](/docs/reference/engine/classes/GuiButton) , adIntegrationPlacementId :[string](/docs/luau/strings)

) : ()

Parameters

|

disclosureButton :[GuiButton](/docs/reference/engine/classes/GuiButton)

 |
|

adIntegrationPlacementId :[string](/docs/luau/strings)

 |

Returns

()

Provide feedback

---

ShowRewardedVideoAdAsync

Yields

Capabilities: UI, Monetization

AdService:ShowRewardedVideoAdAsync (

player :[Player](/docs/reference/engine/classes/Player) , reward :[AdReward](/docs/reference/engine/datatypes/AdReward) , placementId :[number](/docs/luau/numbers) ?

) :[Enum.ShowAdResult](/docs/reference/engine/enums/ShowAdResult)

Parameters

|

player :[Player](/docs/reference/engine/classes/Player)

 |
|

reward :[AdReward](/docs/reference/engine/datatypes/AdReward)

 |
|

placementId :[number](/docs/luau/numbers) ?

 |

Returns

[Enum.ShowAdResult](/docs/reference/engine/enums/ShowAdResult)

Code Samples

Show Rewarded Video Ads

```

-- In a script on the client:

local AdService = game:GetService("AdService")

local Players = game:GetService("Players")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local rewardedVideoButton: GuiButton =

	Players.LocalPlayer.PlayerGui:WaitForChild("myAdGui"):WaitForChild("watchRewardedVideoButton")

local watchRewardedVideoAdRemoteEvent: RemoteEvent = ReplicatedStorage:WaitForChild("watchRewardedVideoAd")

-- The client doesn't have an ad ready yet; hide the button

rewardedVideoButton.Visible = false

local success, result = pcall(function()

	return AdService:GetAdAvailabilityNowAsync(Enum.AdFormat.RewardedVideo)

end)

if success and result.AdAvailabilityResult == Enum.AdAvailabilityResult.IsAvailable then

	-- Show the button if an ad is avilable

	rewardedVideoButton.Visible = true

end

rewardedVideoButton.Activated:Connect(function()

	watchRewardedVideoAdRemoteEvent:FireServer()

	-- The IsAvailable result is only good for a single ad play. To play another ad, you would have to call

	-- GetAdAvailabilityNowAsync and check availability again.

	rewardedVideoButton.Visible = false

end)

-- In a script on the server:

local AdService = game:GetService("AdService")

local MarketplaceService = game:GetService("MarketplaceService")

local Players = game:GetService("Players")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local watchRewardedVideoAdRemoteEvent: RemoteEvent = ReplicatedStorage:WaitForChild("watchRewardedVideoAd")

local REWARDED_VIDEO_PRODUCT_ID = 123 -- Enter your dev product ID here

local function grantReward(player: Player)

	print(`giving a reward to {player.Name}!`)

end

MarketplaceService.ProcessReceipt = function(receiptInfo)

	local player = Players:GetPlayerByUserId(receiptInfo.PlayerId)

	if not player then

		return Enum.ProductPurchaseDecision.NotProcessedYet

	end

	if receiptInfo.ProductId == REWARDED_VIDEO_PRODUCT_ID then

		if receiptInfo.ProductPurchaseChannel == Enum.ProductPurchaseChannel.AdReward then

			print(`player {receiptInfo.PlayerId} earned my rewarded video reward by watching an ad`)

		else

			print(`player {receiptInfo.PlayerId} purchased my rewarded video product with Robux`)

		end

		-- Give the player their reward

		grantReward(player)

	else

		-- Handle other products

	end

	return Enum.ProductPurchaseDecision.PurchaseGranted

end

watchRewardedVideoAdRemoteEvent.OnServerEvent:Connect(function(player)

	local reward = AdService:CreateAdRewardFromDevProductId(REWARDED_VIDEO_PRODUCT_ID)

	AdService:ShowRewardedVideoAdAsync(player, reward)

end)

```

Provide feedback

---

ShowVideoAd

Deprecated

Show details

---

UnregisterAdOpportunity

Capabilities: Monetization

AdService:UnregisterAdOpportunity (instance :[Instance](/docs/reference/engine/datatypes/Instance) ) : ()

Parameters

|

instance :[Instance](/docs/reference/engine/datatypes/Instance)

 |

Returns

()

Provide feedback

---

Events

VideoAdClosed

Deprecated

Show details

---

Jump to

▼

AdService

[Summary](#summary)

[Methods](#summary-methods)

[Events](#summary-events)

[Methods](#methods)

[CreateAdRewardFromDevProductId()](#CreateAdRewardFromDevProductId)

[GetAdAvailabilityNowAsync()](#GetAdAvailabilityNowAsync)

[GetCampaignEligibilityAsync()](#GetCampaignEligibilityAsync)

[RegisterAdOpportunityAsync()](#RegisterAdOpportunityAsync)

[RegisterDisclosureButton()](#RegisterDisclosureButton)

[ShowRewardedVideoAdAsync()](#ShowRewardedVideoAdAsync)

[ShowVideoAd()](#ShowVideoAd)

[UnregisterAdOpportunity()](#UnregisterAdOpportunity)

[Events](#events)

[VideoAdClosed](#VideoAdClosed)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
