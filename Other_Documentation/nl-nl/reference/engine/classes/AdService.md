<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/AdService -->

AdService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [AdService](/docs/nl-nl/reference/engine/classes/AdService)

Nederlands

Feedback

Engine-klasse

AdService

Niet maakbaar

Service

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/AdService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[CreateAdRewardFromDevProductId](#CreateAdRewardFromDevProductId) (devProductId :  [number](/docs/nl-nl/luau/numbers) ) :[AdReward](/docs/nl-nl/reference/engine/datatypes/AdReward)

 |
| --- | --- |
|

[GetAdAvailabilityNowAsync](#GetAdAvailabilityNowAsync) (adFormat :  [Enum.AdFormat](/docs/nl-nl/reference/engine/enums/AdFormat) ) : GetAdAvailabilityNowResult

 |
|

[GetCampaignEligibilityAsync](#GetCampaignEligibilityAsync) (campaignId :  [string](/docs/nl-nl/luau/strings) , player :  [Player](/docs/nl-nl/reference/engine/classes/Player) ? ) : GetCampaignEligibilityResult

 |
|

[RegisterAdOpportunityAsync](#RegisterAdOpportunityAsync) (instance :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) , placementId :  [number](/docs/nl-nl/luau/numbers) ? ) : ()

 |
|

[RegisterDisclosureButton](#RegisterDisclosureButton) (disclosureButton :  [GuiButton](/docs/nl-nl/reference/engine/classes/GuiButton) , adIntegrationPlacementId :  [string](/docs/nl-nl/luau/strings) ) : ()

 |
|

[ShowRewardedVideoAdAsync](#ShowRewardedVideoAdAsync) (player :  [Player](/docs/nl-nl/reference/engine/classes/Player) , reward :  [AdReward](/docs/nl-nl/reference/engine/datatypes/AdReward) , placementId :  [number](/docs/nl-nl/luau/numbers) ? ) :[Enum.ShowAdResult](/docs/nl-nl/reference/engine/enums/ShowAdResult)

 |
|

[ShowVideoAd](#ShowVideoAd) () : ()

Verouderd

 |
|

[UnregisterAdOpportunity](#UnregisterAdOpportunity) (instance :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

 |

Evenementen

|

[VideoAdClosed](#VideoAdClosed) (adShown :  [boolean](/docs/nl-nl/luau/booleans) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Verouderd

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Methoden

CreateAdRewardFromDevProductId

Mogelijkheden: Monetization

AdService:CreateAdRewardFromDevProductId (devProductId :[number](/docs/nl-nl/luau/numbers) ) :[AdReward](/docs/nl-nl/reference/engine/datatypes/AdReward)

Parameters

|

devProductId :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

[AdReward](/docs/nl-nl/reference/engine/datatypes/AdReward)

Feedback geven

---

GetAdAvailabilityNowAsync

Opbrengst

Mogelijkheden: Monetization

AdService:GetAdAvailabilityNowAsync (adFormat :[Enum.AdFormat](/docs/nl-nl/reference/engine/enums/AdFormat) ) : GetAdAvailabilityNowResult

Parameters

|

adFormat :[Enum.AdFormat](/docs/nl-nl/reference/engine/enums/AdFormat)

 |

Teruggaves

GetAdAvailabilityNowResult

Feedback geven

---

GetCampaignEligibilityAsync

Opbrengst

Mogelijkheden: Monetization

AdService:GetCampaignEligibilityAsync (

campaignId :[string](/docs/nl-nl/luau/strings) , player :[Player](/docs/nl-nl/reference/engine/classes/Player) ?

) : GetCampaignEligibilityResult

Parameters

|

campaignId :[string](/docs/nl-nl/luau/strings)

 |
|

player :[Player](/docs/nl-nl/reference/engine/classes/Player) ?

Standaardwaarde: nil |

Teruggaves

GetCampaignEligibilityResult

Codevoorbeelden

Voorbeeld Advertentie-integratie

```

local AdService = game:GetService("AdService")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Players = game:GetService("Players")

local YOUR_CAMPAIGN_ID = "123" -- Voer hier je advertentie-integratiecampagne-ID in van de advertentiesmanager.

local AD_INTEGRATION_IDS = {

	-- Voer hier je advertentie-integratieplaatsings-ID's in voor elk activum dat je hebt geregistreerd als onderdeel van je

	-- advertentie-integratiecampagne.

	BrandedBuilding = "abc-123",

	BrandedScreenGui = "xyz-789",

}

-- Verifieer of de LocalPlayer in aanmerking komt om je campagne te zien

local success, result = pcall(function()

	return AdService:GetCampaignEligibilityAsync(YOUR_CAMPAIGN_ID)

end)

if success and result.IsEligible then

	-- Alle advertentie-integratie-activa moeten standaard verborgen zijn. Zodra je weet dat de

	-- speler in aanmerking komt, is het veilig om de advertentie-integratie-activa te tonen.

	local brandedBuildingModel = ReplicatedStorage.adIntegration.building

	local brandedBuildingModelDisclosureBillboardGui = brandedBuildingModel.disclosureBillboardGui

	-- Vergeet niet je advertentie-openbaarmakingsknoppen te registreren, zodat spelers weten wie voor de advertentie betaalt!

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

Feedback geven

---

RegisterAdOpportunityAsync

Opbrengst

Mogelijkheden: Monetization

AdService:RegisterAdOpportunityAsync (

instance :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) , placementId :[number](/docs/nl-nl/luau/numbers) ?

) : ()

Parameters

|

instance :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
|

placementId :[number](/docs/nl-nl/luau/numbers) ?

 |

Teruggaves

()

Codevoorbeelden

Volg advertentiekansen

```

local AdService = game:GetService("AdService")

local playerGui = game:GetService("Players").LocalPlayer:WaitForChild("PlayerGui")

-- Maak de ScreenGui en de Knop

local screenGui = Instance.new("ScreenGui", playerGui)

local adButton = Instance.new("TextButton", screenGui)

-- Registreer de knop bij AdService

local success, err = pcall(function()

	-- De tweede parameter is een optionele Plaatsings-ID (Nummer) parameter die is gegenereerd in de Creator Hub.

	-- Als je ervoor kiest om geen Plaatsings-ID op te geven, wordt de advertentiekans geregistreerd onder de standaardplaatsing.

	AdService:RegisterAdOpportunityAsync(adButton, 1234567891234567)

end)

if not success then

	warn("Registreren van advertentiekans mislukt:", err)

end

```

Feedback geven

---

RegisterDisclosureButton

Mogelijkheden: Monetization

AdService:RegisterDisclosureButton (

disclosureButton :[GuiButton](/docs/nl-nl/reference/engine/classes/GuiButton) , adIntegrationPlacementId :[string](/docs/nl-nl/luau/strings)

) : ()

Parameters

|

disclosureButton :[GuiButton](/docs/nl-nl/reference/engine/classes/GuiButton)

 |
|

adIntegrationPlacementId :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

()

Feedback geven

---

ShowRewardedVideoAdAsync

Opbrengst

Mogelijkheden: UI, Monetization

AdService:ShowRewardedVideoAdAsync (

player :[Player](/docs/nl-nl/reference/engine/classes/Player) , reward :[AdReward](/docs/nl-nl/reference/engine/datatypes/AdReward) , placementId :[number](/docs/nl-nl/luau/numbers) ?

) :[Enum.ShowAdResult](/docs/nl-nl/reference/engine/enums/ShowAdResult)

Parameters

|

player :[Player](/docs/nl-nl/reference/engine/classes/Player)

 |
|

reward :[AdReward](/docs/nl-nl/reference/engine/datatypes/AdReward)

 |
|

placementId :[number](/docs/nl-nl/luau/numbers) ?

 |

Teruggaves

[Enum.ShowAdResult](/docs/nl-nl/reference/engine/enums/ShowAdResult)

Codevoorbeelden

Toon Beloningen Video Advertenties

```

-- In een script op de client:

local AdService = game:GetService("AdService")

local Players = game:GetService("Players")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local rewardedVideoButton: GuiButton =

	Players.LocalPlayer.PlayerGui:WaitForChild("myAdGui"):WaitForChild("watchRewardedVideoButton")

local watchRewardedVideoAdRemoteEvent: RemoteEvent = ReplicatedStorage:WaitForChild("watchRewardedVideoAd")

-- De client heeft nog geen advertentie klaar; verberg de knop

rewardedVideoButton.Visible = false

local success, result = pcall(function()

	return AdService:GetAdAvailabilityNowAsync(Enum.AdFormat.RewardedVideo)

end)

if success and result.AdAvailabilityResult == Enum.AdAvailabilityResult.IsAvailable then

	-- Toon de knop als er een advertentie beschikbaar is

	rewardedVideoButton.Visible = true

end

rewardedVideoButton.Activated:Connect(function()

	watchRewardedVideoAdRemoteEvent:FireServer()

	-- De IsAvailable resultaat is alleen goed voor een enkele advertentie weergave. Om een andere advertentie te spelen, moet je

	-- GetAdAvailabilityNowAsync aanroepen en de beschikbaarheid opnieuw controleren.

	rewardedVideoButton.Visible = false

end)

-- In een script op de server:

local AdService = game:GetService("AdService")

local MarketplaceService = game:GetService("MarketplaceService")

local Players = game:GetService("Players")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local watchRewardedVideoAdRemoteEvent: RemoteEvent = ReplicatedStorage:WaitForChild("watchRewardedVideoAd")

local REWARDED_VIDEO_PRODUCT_ID = 123 -- Voer hier je ontwikkelingsproduct-ID in

local function grantReward(player: Player)

	print(`een beloning geven aan {player.Name}!`)

end

MarketplaceService.ProcessReceipt = function(receiptInfo)

	local player = Players:GetPlayerByUserId(receiptInfo.PlayerId)

	if not player then

		return Enum.ProductPurchaseDecision.NotProcessedYet

	end

	if receiptInfo.ProductId == REWARDED_VIDEO_PRODUCT_ID then

		if receiptInfo.ProductPurchaseChannel == Enum.ProductPurchaseChannel.AdReward then

			print(`speler {receiptInfo.PlayerId} heeft mijn beloningen video beloning verdiend door een advertentie te bekijken`)

		else

			print(`speler {receiptInfo.PlayerId} heeft mijn beloningen video product gekocht met Robux`)

		end

		-- Geef de speler hun beloning

		grantReward(player)

	else

		-- Behandel andere producten

	end

	return Enum.ProductPurchaseDecision.PurchaseGranted

end

watchRewardedVideoAdRemoteEvent.OnServerEvent:Connect(function(player)

	local reward = AdService:CreateAdRewardFromDevProductId(REWARDED_VIDEO_PRODUCT_ID)

	AdService:ShowRewardedVideoAdAsync(player, reward)

end)

```

Feedback geven

---

ShowVideoAd

Verouderd

Details weergeven

---

UnregisterAdOpportunity

Mogelijkheden: Monetization

AdService:UnregisterAdOpportunity (instance :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

Parameters

|

instance :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Teruggaves

()

Feedback geven

---

Evenementen

VideoAdClosed

Verouderd

Details weergeven

---

Ga naar

▼

AdService

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Methoden](#methods)

[CreateAdRewardFromDevProductId()](#CreateAdRewardFromDevProductId)

[GetAdAvailabilityNowAsync()](#GetAdAvailabilityNowAsync)

[GetCampaignEligibilityAsync()](#GetCampaignEligibilityAsync)

[RegisterAdOpportunityAsync()](#RegisterAdOpportunityAsync)

[RegisterDisclosureButton()](#RegisterDisclosureButton)

[ShowRewardedVideoAdAsync()](#ShowRewardedVideoAdAsync)

[ShowVideoAd()](#ShowVideoAd)

[UnregisterAdOpportunity()](#UnregisterAdOpportunity)

[Evenementen](#events)

[VideoAdClosed](#VideoAdClosed)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
