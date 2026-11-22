<!-- Source: https://create.roblox.com/docs/production/promotion/rewarded-video-ads -->

Rewarded video ads | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/production/promotion/rewarded-video-ads.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Advertise](/docs/production/promotion/advertise)

# Rewarded video ads

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/production/promotion/rewarded-video-ads.md)

With rewarded video ads, you can implement a reward mechanism inside your game to incentivize users to watch click-to-play video ads. A rewarded video is a full-screen ad that lasts anywhere from 6 to 30 seconds and that rewards the user with an item after they have finished watching it.

Rewarded video ads let you:

-

Monetize a greater number of your users.

-

Increase your ad revenue per user and bring in demand from hundreds of brands.

-

Improve user playtime and deliver greater engagement from your game.

This page covers setup, implementation, analytics, and eligibility. For placement, reward strategy, and performance tips, see the [Rewarded video playbook](/docs/production/promotion/rewarded-video-playbook) .

## [Implement rewarded video ads](#implement-rewarded-video-ads)[](#implement-rewarded-video-ads)

Rewards must be developer products . You can't reward users with Robux.

Video ads shouldn't negatively impact the user's character during gameplay. To make sure their character isn't harmed, you can pause damage while an ad plays or only show ads in safe zones like the game lobby.

To implement rewarded video ads:

1.

Make sure you meet the [eligibility requirements](#eligibility-requirements) , including being 13+ years of age, having an ID-verified Roblox account, and have a public game with at least 2 thousand unique visitors per month.

2.

[Enable rewarded video ads in Creator Hub](#video-ad-setup) .

3.

Choose the item you want to reward users with for watching the ad. You can select an existing developer product or create a brand new one.

4.

Create [client-side](#client-side-implementation)  and [server-side](#server-side-implementation)  scripts. The client-side script checks if a video ad is available to be played to the user, while the server-side script turns a developer product into a reward, shows the user the video ad, and grants the user their reward.

After implementation, you can use [analytics](#analytics)  to understand key metrics and optimize your rewarded video ad earnings.

Earnings from rewarded video ads come from impressions. Your total earnings are calculated by multiplying EPM (earnings per 1000 impressions) by the total number of impressions.

### [Video ad setup](#video-ad-setup)[](#video-ad-setup)

To set up a rewarded video ad inside your game:

1.

Go to [Creations](https://create.roblox.com/dashboard/creations)  and select a game.

2.

Go to Monetization  ⟩ Ads  ⟩ Settings .

3.

Under Rewarded Video  ⟩ Serving , turn on the Serving enabled  toggle.  ![](https://prod.docsiteassets.roblox.com/assets/promotion/ads-manager/EnableRewardedVideoAdsCreatorHub.png)

4.

Select the reward you want to grant the user. If the reward doesn't already exist, [create a new developer product in the Creator Hub](/docs/production/monetization/developer-products#create-a-developer-product) . This developer product must have been created for the specific universe the place is in.

5.

Insert a button that the user must press before the video ad starts playing.

### [Client-side implementation](#client-side-implementation)[](#client-side-implementation)

To implement the rewarded video ad on the client-side:

1.

Add a new [LocalScript](/docs/reference/engine/classes/LocalScript)  to the button you just inserted into your game.

2.

Use [AdService:GetAdAvailabilityNowAsync()](/docs/reference/engine/classes/AdService#GetAdAvailabilityNowAsync)  to check whether an ad is available before attempting to show it.

Call [GetAdAvailabilityNowAsync()](/docs/reference/engine/classes/AdService#GetAdAvailabilityNowAsync)  as close as possible to the moment you plan to show the ad. For example, if you have a "Watch video ad to get a reward" button in a shop menu, only call it when the user opens the shop menu.

Code example for rewarded video ad (Client)

```

-- Services

local AdService = game:GetService("AdService")

local Players = game:GetService("Players")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- StarterGui ⟩ ScreenGui ⟩ ShopFrame ⟩ RewardedAdButton

local PlayerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

local ScreenGui = PlayerGui:WaitForChild("ScreenGui")

local ShopFrame = ScreenGui:WaitForChild("ShopFrame")

local RewardedAdButton = ShopFrame:WaitForChild("RewardedAdButton")

-- StarterGui ⟩ ScreenGui ⟩ OpenShopButton

local OpenShopButton = ScreenGui:WaitForChild("OpenShopButton")

-- Event to communicate between clients & server

local RewardedAdEvent = ReplicatedStorage:WaitForChild("RewardedAdEvent")

local INELIGIBLE_RESULTS = {

	Enum.AdAvailabilityResult.PlayerIneligible,

	Enum.AdAvailabilityResult.DeviceIneligible,

	Enum.AdAvailabilityResult.PublisherIneligible,

	Enum.AdAvailabilityResult.ExperienceIneligible,

}

local function isIneligible(result: Enum.AdAvailabilityResult)

	for _, inEligibleResult in ipairs(INELIGIBLE_RESULTS) do

		if result == inEligibleResult then

			return true

		end

	end

	return false

end

function checkForAds()

	local isSuccess, result = pcall(function()

		return AdService:GetAdAvailabilityNowAsync(Enum.AdFormat.RewardedVideo)

	end)

	if isSuccess and result.AdAvailabilityResult == Enum.AdAvailabilityResult.IsAvailable then

		RewardedAdButton.Visible = true

		return

	end

	if isIneligible(result.AdAvailabilityResult) then

		return

	end

end

RewardedAdEvent.OnClientEvent:Connect(function(isSuccess : boolean, result : Enum.ShowAdResult)

	if result == Enum.ShowAdResult.ShowCompleted then

		checkForAds()

	end

end)

OpenShopButton.MouseButton1Click:Connect(function()

	if ShopFrame.Visible then

		ShopFrame.Visible = false

		return

	end

	ShopFrame.Visible = true

	checkForAds()

end)

RewardedAdButton.MouseButton1Click:Connect(function()

	RewardedAdButton.Visible = false

	RewardedAdEvent:FireServer()

end)

```

### [Server-side implementation](#server-side-implementation)[](#server-side-implementation)

To implement the rewarded video ad on the server-side:

1.

Create a new [Script](/docs/reference/engine/classes/Script)  under ServerScriptService .

2.

Use the [CreateAdRewardFromDevProductId](/docs/reference/engine/classes/AdService#CreateAdRewardFromDevProductId)  method to pass the developer product ID of the reward and create an AdReward  object.

3.

Use the [ShowRewardedVideoAdAsync](/docs/reference/engine/classes/AdService#ShowRewardedVideoAdAsync)  method to play the video ad to the user.

-

OPTIONAL

 Add a placementId  to track individual [video ad placements](#placements)  inside your game.

4.

Use the [ProcessReceipt](/docs/reference/engine/classes/MarketplaceService#ProcessReceipt)  method to grant the user their reward if they have watched the entire video ad.

Code example for rewarded video ad (Server)

```

-- Services

local AdService = game:GetService("AdService")

local MarketplaceService = game:GetService("MarketplaceService")

local Players = game:GetService("Players")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local RewardedAdEvent = ReplicatedStorage:WaitForChild("RewardedAdEvent")

-- Provide a developer product ID for the video ad reward

-- This developer product must be created for the specific universe that this place is in

local DEV_PRODUCT_ID = 1919753834

RewardedAdEvent.OnServerEvent:Connect(function(player)

	local isSuccess, result = pcall(function()

		local reward = AdService:CreateAdRewardFromDevProductId(DEV_PRODUCT_ID)

		return AdService:ShowRewardedVideoAdAsync(player, reward)

	end)

	RewardedAdEvent:FireClient(player, isSuccess, result)

end)

MarketplaceService.ProcessReceipt = function(receiptInfo)

	local player = Players:GetPlayerByUserId(receiptInfo.PlayerId)

	if not player then

		return Enum.ProductPurchaseDecision.NotProcessedYet

	end

	if receiptInfo.ProductId == DEV_PRODUCT_ID then

    -- Include the logic for granting rewards here

		return Enum.ProductPurchaseDecision.PurchaseGranted

	end

	return Enum.ProductPurchaseDecision.NotProcessedYet

end

```

## [Join with Reward](#join-with-reward)[](#join-with-reward)

Join with Reward is in closed beta. If you're interested in trying it, contact [adproductops@roblox.com](/docs/mailto%3Aadproductops%40roblox.com) .

Join with Reward is a rewarded video placement that shows on your game's Experience Details Page, before a user joins. A user can choose to watch an ad there and get a reward when they join. This is a separate placement from the in-experience rewarded video flow described above. You don't need to call [AdService](/docs/reference/engine/classes/AdService)  to show the ad, because you set up the placement in Creator Hub.

Each reward is a [developer product](/docs/production/monetization/developer-products) . When a user earns a reward, Roblox creates a receipt for that developer product, and your game's [ProcessReceipt](/docs/reference/engine/classes/MarketplaceService#ProcessReceipt)  callback grants it when the user joins. If your game's ProcessReceipt  callback doesn't already grant a developer product you want to use as a reward, you need to add code for it before you publish the reward.

### [Set up a Join with Reward placement](#set-up-a-join-with-reward-placement)[](#set-up-a-join-with-reward-placement)

1.

In the Creator Dashboard, go to Creations  and select a game.

2.

Go to Monetization  ⟩ Ads  ⟩ Placements .

3.

Click Create placement  and select Join with Reward .

4.

On the Placement setup  step, name the placement and add one or more reward items. Each reward item is a developer product with an image. You can't add the same developer product to a placement more than once.

5.

Click Continue . The next step shows a ProcessReceipt  code snippet with the IDs of your reward items' developer products. If your game doesn't already grant these products, copy the snippet into your server-side ProcessReceipt  code, then replace the placeholder comment with the code that gives the user each reward.

6.

Click Create .

### [Test rewards](#test-rewards)[](#test-rewards)

New rewards start in test mode, so you can check that each one is granted correctly before every user can see it.

Join with Reward is only supported on mobile devices. To test a reward, open the game's Experience Details Page on a mobile device.

-

Who can see a reward in test mode:  only users with edit access to the game. They see the Join with Reward option on the game's Experience Details Page. Other users don't see rewards that are in test mode.

-

One reward at a time:  only one reward on a placement can be in test mode. When you create a placement, the first reward item starts in test mode, and the other reward items stay in draft until it's their turn.

To test a reward and move it out of test mode:

1.

On a mobile device, sign in with an account that has edit access to the game, and open the game's Experience Details Page.

2.

Watch the ad and join the game. Check that you get the reward.

3.

In Creator Hub, open the placement's reward items and click Publish  on the reward. The reward becomes active, and all eligible users can now get it.

After you publish a reward, the next draft reward on the placement moves into test mode automatically. Repeat these steps for each reward. You can't publish a reward while its image is still under review.

### [Manage reward items](#manage-reward-items)[](#manage-reward-items)

Each reward item has a status, such as draft, test mode, active, or inactive. Use the reward items drawer on the placement to:

-

Turn a reward on or off. Turning on an inactive reward makes it active for all users.

-

Click Test  on a draft reward to move it into test mode. If another reward is already in test mode, that reward moves back to draft.

-

Select Enable test mode  from a reward's menu to move an active or inactive reward back into test mode.

When a placement has more than one active reward, Roblox picks one of them at random each time it serves the ad. Rewards in test mode are only shown to users with edit access to the game.

### [View Join with Reward performance](#view-join-with-reward-performance)[](#view-join-with-reward-performance)

Join with Reward has its own reporting, separate from your in-experience rewarded video ads. To view it:

1.

In the Creator Dashboard, go to Creations  and select a game.

2.

Go to Monetization  ⟩ Ads  ⟩ Analytics .

3.

Filter by Rewarded Video , then select Join with Reward  as the rewarded video type.

This view only includes your Join with Reward placements, and it's only available after your game has at least one Join with Reward placement. It shows:

-

Summary totals for Earnings , Impressions , and EPM .

-

Earnings and impressions charts over time.

-

A CTR  (click-through rate) chart, with a shaded band that shows the expected CTR range.

## [Placements](#placements)[](#placements)

Use placements to track the performance of individual rewarded video ads inside your game.

To create a rewarded video ad placement:

1.

In the Creator Dashboard, go to Creations  and select a game.

2.

Go to Monetization  ⟩ Ads  ⟩ Placements .

3.

Click Create placement .

4.

Enter a name for the placement and click Create .

The new placement populates on the Placement table with a unique Placement ID . You can use this Placement ID in the [ShowRewardedVideoAsync](/docs/reference/engine/classes/AdService#ShowRewardedVideoAsync)  method to differentiate between and track metrics for the individual video ads inside your game.

## [Ad opportunities](#ad-opportunities)[](#ad-opportunities)

Use [RegisterAdOpportunityAsync](/docs/reference/engine/classes/AdService#RegisterAdOpportunityAsync)  to track how many times a user has the opportunity to watch a rewarded video ad, and the rate at which they actually watch the video ad.

You can provide a Placement ID as an optional parameter to track metrics for individual ad opportunities in your game.

Code example for tracking ad opportunities

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

## [Exclude likely spenders](#exclude-likely-spenders)[](#exclude-likely-spenders)

Based on past behavior and purchasing habits, certain users are more likely to make purchases in your game. To reduce your risk of losing revenue, you can exclude users who are likely to spend in your game from seeing rewarded video ads.

We recommend that you only enable this setting if you plan to let users choose between watching a video ad and purchasing the reward from that ad. If the reward you're offering through the video ad is unique and isn't available for purchase, we recommend that you do not enable this setting.

To prevent likely spenders from seeing rewarded video ads:

1.

In the Creator Dashboard, go to Creations  and select a game.

2.

Go to Monetization  ⟩ Ads  ⟩ Settings .

3.

Turn on the Exclude your most likely purchasers from Rewarded Video Ads  toggle.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/rewarded-video-ads/LikelySpenders.png)

## [Estimate potential earnings](#estimate-potential-earnings)[](#estimate-potential-earnings)

Use the calculator to estimate your earnings before you implement rewarded videos ad in your game.

Potential earnings are calculated by multiplying the number of ads-eligible users who have visited your game in the last 7 days, the number of ads you might show per user, and your projected EPM (earnings per 1000 impressions).

Because the number of daily ad views per user is the main variable you can control when you implement rewarded video ads in your game, you should design a user experience that naturally encourages users to watch ads. For example, if you want most users to watch at least one ad a day, make your ad placements accessible and easy to find. You can also boost daily views by offering rewards that feel valuable and connect to your core gameplay loop, keeping users engaged and boosting your total ad impressions.

To use the calculator:

1.

In the Creator Dashboard, go to Creations  and select a game.

2.

Go to Monetization  ⟩ Ads  ⟩ Eligibility .

3.

Under Ad format , select Rewarded video .

4.

Adjust the daily ad views per user  slider. to update the Weekly potential rewarded video ads earning  number and see potential earnings.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/rewarded-video-ads/OpportunityCalculator.png)

## [Analytics](#analytics)[](#analytics)

Use analytics metrics to evaluate the effectiveness of your rewarded video ads, test different reward types to identify the ones that best resonate with your audience, and measure how often users watch entire video ads to claim rewards.

To access your rewarded video ad metrics:

1.

In the Creator Dashboard, go to Creations  and select a game.

2.

Go to Monetization  ⟩ Ads  ⟩ Analytics .

3.

Filter by Rewarded Video  to see all of the available metrics.

| Metric | | Description |
| --- | --- |
| Earnings (Robux) | | Total revenue amount in Robux earned from rewarded video ads in your game.
 Different lines show you this metric for different ad placements inside the game. |
| Monetization Funnel at Experience level | | This metric shows you:

-

Requested : The number of ads requested by ads-eligible users in your game.

-

Filled : The number of ads received by ads-eligible users in your game.

-

Ad Opportunities : The number of opportunities users had to watch a video ad.

-

Impressions : The number of impressions from the video ads in your game. The first frame of a video ad shown to a user counts as an impression.

-

Rewarded : The number of video ad rewards granted to users.

  |
| Fill Rate | | The percentage of requests that had an ad returned as a reponse. |
| EPM (Earnings per Mille) | | Your effective Robux earnings per thousand impressions. Calculated by total earnings / the number of impressions (in thousands) in your game.
 Different lines show you this metric for different ad placements inside the game. |
| Ad Opportunities | | The number of opportunities users had to watch a video ad. Use this metric to track how many times a user had the chance to watch a video ad and the rate at which they actually took that chance and watched the ad.
 Different lines show you this metric for different ad placements inside the game. |
| Impressions | | The number of rewarded video ads shown in your game.
 Different lines show you this metric for different ad placements inside the game. |
| Rewarded | | The number of rewards granted for video ad views in your game.
 Different lines show you this metric for different ad placements inside the game. |
| DUV (Daily Unique Viewers) | | The number of unique users who have viewed one or more video ads in your game in a day. A view is defined by an impression.
 This data is updated with 1 day delay. |
| AEPDUV (Average Earning Per Daily Unique Viewer) | | The earnings generated per daily unique viewer for rewarded video ads.
 This data is updated with 1 day delay. |
| Eligible Daily Active User | | The number of unique daily users to your game who were eligible to view rewarded video ads.
 This data is updated with 1 day delay. |
| DUV/eDAU | | The percentage of ads-eligible users who visited your game and viewed one or more video ads in a day. |
| Opt-In Rate | | The percentage of ads-eligible users who are engaging with ads in your game. |
| Frequency | | The number of ads a user is seeing per day in your game. |

## [De-risk your implementation with experiments](#de-risk-your-implementation-with-experiments)[](#de-risk-your-implementation-with-experiments)

If you're unsure how your community will react to a new rewarded video ad placement, you can use [experiments](/docs/production/experiments)  to roll the placement out to a percentage of your users first. This lets you measure real-time changes in engagement and retention before rolling the placement out to your entire audience. To track ad impressions, opt-in rate, and ad earnings alongside your other metrics, choose the [Rewarded Video Earnings metric set](/docs/production/experiments#rewarded-video-metrics)  when you create the experiment.

## [Eligibility requirements](#eligibility-requirements)[](#eligibility-requirements)

To prevent abuse of the rewarded ad system and to provide the best user experience possible, you must follow the eligibility requirements when you implement rewarded video ads.

| Games | | Games must:
-

Be public and unrestricted.

-

Offer no free-form user creation, strong language, romance, or social hangouts with private spaces.

-

Have a complete Maturity and Compliance Questionnaire  or Content Rating Questionnaire  that has been reviewed and approved by Roblox. If the review status is Pending , you can request a re-review from the game's advertising eligibility page under Monetization  ⟩ Ads  ⟩ Eligibility . You'll receive a response within 24 hours.

-

Have an average of at least 2,000 unique visitors per month .

-

Comply with the [Roblox terms of use](https://en.help.roblox.com/hc/en-us/articles/115004647846-Roblox-Terms-of-Use) , [community standards](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards) , and [publisher integrity requirements](https://en.help.roblox.com/hc/en-us/articles/13722260778260-Advertising-Standards#publisher-integrity) .

 |
| Publishers | | As a publisher, you must:
-

Be 13+ years of age.

-

Have an account that is in good standing with Roblox.

-

Have enabled two-step verification (2FA) and [verified your ID](/docs/production/publishing/account-verification#verify-through-government-id)  on your account.

-

Implement a clear action that the user has to take before the video ad is played for them. For example, a button that the user has to click.

-

Provide clear and accurate disclosures prior to each trigger of the video, including what the reward is and what the user is required to do to earn it. These disclosures must be unambiguous to the user. For example, you can add text that says “Watch the ad to earn 10 diamonds!” to the video ad play button.

-

Issue the reward to the user immediately after the rewarded video ad has finished playing.

-

Not force the user to initiate the video ad as a progress gate in the game.

-

Not take over the user's screen visibility or obscure their avatar motion.

-

Not promote or implement fraudulent rewards, including free Robux or money, to deceptively incentivize the user to watch the video ad to completion. This also includes using inaccurate reward descriptions or implementing mechanisms that don't fulfill the reward promised to the user.

 |
| Rewards | | The reward for watching a video ad should:
-

Be granted upon completion of a video ad view.

-

Be a developer product which would normally be available to purchase with Robux inside an in-game shop.

-

Not inflate currency or unbalance the game's economy.

-

Not be a randomized item.

For guidance on choosing rewards, see [Choose rewards](/docs/production/promotion/rewarded-video-playbook#choose-rewards)  in the rewarded video playbook. |

Resubmitting your Content Rating Questionnaire  will temporarily remove your ads eligibility while the questionnaire is under review. To avoid repeated interruptions, only resubmit the questionnaire when you publish a game update that changes your previous responses.

Any violation of the eligilibity requirements can result in account suspension, removal of content, revocation of ad payouts, or loss of eligibility to earn from ads.

## [Best practices](#best-practices)[](#best-practices)

For placement, reward strategy, and a self-audit checklist, see the [Rewarded video playbook](/docs/production/promotion/rewarded-video-playbook) .

For implementation, follow these technical practices:

-

Call [GetAdAvailabilityNowAsync](/docs/reference/engine/classes/AdService#GetAdAvailabilityNowAsync)  as close as possible to the moment you plan to show the ad. For example, if you have a "Watch video ad to get a reward" button in a shop menu, only call GetAdAvailabilityNowAsync  when the user opens the shop menu. This approach improves performance by preventing ads from unnecessarily being held in memory, and benefits CPM (cost-per-thousand impressions) and earnings by optimizing the ad fill rate.

-

After an ad finishes, only call [GetAdAvailabilityNowAsync()](/docs/reference/engine/classes/AdService#GetAdAvailabilityNowAsync)  if you offer the user another opportunity to watch an ad. This helps avoid filled requests that don't lead to impressions.

-

Use [ad opportunities](#ad-opportunities)  to track when you offer a user a chance to watch a video ad for a reward. Watch the ratio between filled requests, ad opportunities, and ad impressions to see whether ads are hard to find or rewards aren't compelling enough.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
