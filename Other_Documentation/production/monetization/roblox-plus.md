<!-- Source: https://create.roblox.com/docs/production/monetization/roblox-plus -->

Roblox Plus | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/production/monetization/roblox-plus.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Earn](/docs/production/monetization)

# Roblox Plus

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/production/monetization/roblox-plus.md)

Roblox Plus  gives you additional ways to earn from your games by rewarding engagement and purchases from Plus subscribers.

Users who subscribe to Plus get a range of benefits to enhance their purchasing power, access, and overall game on the platform:

-

Discounted purchases : Subscribers get 10% off eligible purchases, including in-game items, avatar items, and more. The discount increases to 20% starting in the third month. Roblox covers this discount for you.

-

Free paid private servers : Subscribers get access to paid private servers at no cost. You're still compensated when they spend time in your paid private servers.

-

Free Robux transfers : Subscribers can transfer Robux at no cost to sender or recipient. Transfers are subject to age restrictions and parental consent. Robux received through transfers are not eligible for the DevEx program.

-

[Marketplace access](/docs/marketplace/marketplace-policy#creator-requirements) : Subscribers can trade and resell limited items, and publish and sell avatar items. Premium subscribers have the same Marketplace access.

For more information about the benefits of Roblox Plus to end-users, see the [help center](https://en.help.roblox.com/hc/en-us/articles/47967913158164-Roblox-Plus) .

As a creator, you can earn from Roblox Plus subscribers through:

-

[In-game Robux purchases](#earn-from-in-game-purchases) : Subscribers receive a 10–20% discount on purchases, which is covered by Roblox so that your earnings per purchase are not reduced. Lower prices can encourage more frequent purchases, helping increase your overall revenue.

-

[Driving Plus sign-ups](#earn-from-in-game-plus-subscriptions) : Encourage engaged users to subscribe to Roblox Plus directly from your game using [PromptRobloxSubscriptionPurchase](/docs/reference/engine/classes/MarketplaceService#PromptRobloxSubscriptionPurchase) . You can earn up to 750 Robux for each new subscriber you bring in, with earnings starting once the subscription becomes paid (free trial periods are not included).

-

[Time spent in paid private servers](#earn-from-paid-private-server-time) : Earn up to 100 Robux per subscriber when they spend at least 60 minutes in your paid private servers each month.

-

[In-game Robux transfers](#earn-from-robux-transfers) : Earn 10% every time a Plus subscriber sends Robux to another user within your game using [PromptRobuxTransferAsync](/docs/reference/engine/classes/MarketplaceService#PromptRobuxTransferAsync) . This amount is eligible for the DevEx program.

## [Earn from in-game purchases](#earn-from-in-game-purchases)[](#earn-from-in-game-purchases)

With Roblox Plus, users receive a 10–20% discount on eligible Robux purchases. Because Roblox subsidizes these discounts, you earn the same amount per purchase as you would from non-subscribers. At the same time, lower prices for Plus subscribers can encourage more frequent purchases and increase your overall revenue.

Subscribers receive a 10% discount for their first two months, which increases to 20% starting in the third month. If a user cancels their Plus subscription and later resubscribes, their discount resets to 10% and increases again after two months.

Eligible Robux purchases include:

-

Developer products

-

Game passes

-

Developer subscriptions

-

Paid access games

-

Avatar items

Discounts do not apply to:

-

Items priced above 1,000,000 Robux

-

Marketplace publishing fees

-

Ad credits

-

Group fees

The following table shows how Roblox Plus discounts are subsidized by Roblox.

| User type | | Item price in Robux | | User spend | | Roblox subsidy | | Creator earnings | | Effective revenue share |
| --- | --- |
| Non-subscriber | | 100 | | 100 | | — | | 70 | | 70% |
| Plus subscriber (10% discount) | | 100 | | 90 | | 10 | | 70 | | 78% |
| Plus subscriber (20% discount) | | 100 | | 80 | | 20 | | 70 | | 88% |

If you hard-code prices, your in-game UI might display incorrect pricing to Plus subscribers.  While subscribers are still charged the discounted price, your game might show them the full price instead. This mismatch can cause confusion.

To display accurate, real-time pricing (including Plus discounts), you should use [MarketplaceService](/docs/reference/engine/classes/MarketplaceService)  functions like [GetProductInfoAsync](/docs/reference/engine/classes/MarketplaceService#GetProductInfoAsync)  and [GetDeveloperProductsAsync](/docs/reference/engine/classes/MarketplaceService#GetDeveloperProductsAsync) .

For implementation details, see [Sell a pass](/docs/production/monetization/passes#sell-a-pass)  and [Sell a developer product](/docs/production/monetization/developer-products#sell-a-developer-product) .

## [Earn from in-game Plus subscriptions](#earn-from-in-game-plus-subscriptions)[](#earn-from-in-game-plus-subscriptions)

You can encourage users to subscribe to Roblox Plus directly from your game with [PromptRobloxSubscriptionPurchase](/docs/reference/engine/classes/MarketplaceService#PromptRobloxSubscriptionPurchase) . For each user who becomes a subscriber through your game, you earn 250 Robux per month for their first three consecutive months , with up to 750 Robux for every newly acquired subscriber .

Any earnings are subject to a 60-day holding period.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/roblox-plus/Plus-Signup-Bonus.png)

Roblox Plus subscription prompts might appear in other places like paid private server pages or purchase modals, but you only earn a Robux payout when a user subscribes through your game using PromptRobloxSubscriptionPurchase .

To offer Plus subscriptions within your game and grant rewards to users:

1.

Detect when the user reaches the point in your game where you want to offer the Plus subscription.

2.

Check whether the user already has an active Plus subscription with [HasRobloxSubscription](/docs/reference/engine/classes/Player#HasRobloxSubscription) .

3.

If the user is already a subscriber:

1.

Grant them the reward immediately.

4.

If the user isn't a subscriber:

1.

Prompt them to purchase Roblox Plus with [PromptRobloxSubscriptionPurchase](/docs/reference/engine/classes/MarketplaceService#PromptRobloxSubscriptionPurchase) .

2.

Listen to [PromptRobloxSubscriptionPurchaseFinished](/docs/reference/engine/classes/MarketplaceService#PromptRobloxSubscriptionPurchaseFinished)  to detect when the purchase prompt UI has closed.

3.

Confirm the Plus subscription on the server with [HasRobloxSubscription](/docs/reference/engine/classes/Player#HasRobloxSubscription)  through the [GetPropertyChangedSignal](/docs/reference/engine/classes/Instance#GetPropertyChangedSignal)  before granting any rewards. This event verifies that the user's Plus subscription status has actually changed.

### [Examples](#examples)[](#examples)

The following examples show how to work with Roblox Plus in your game, including retrieving discount information, checking subscription status, prompting users to subscribe, and handling the purchase flow.

##### Example 1

Print Roblox Plus discount information for a game pass.

```

local MarketplaceService = game:GetService("MarketplaceService")

local PASS_ID = 12345678

local DiscountTypeDisplay = {

	RobloxPlusSubscription = "Roblox Plus Discount",

}

local productInfo = MarketplaceService:GetProductInfoAsync(PASS_ID, Enum.InfoType.GamePass)

print(string.format("Original Price: %d", productInfo.UserBasePriceInRobux))

for _, discount in ipairs(productInfo.PriceDiscountDetails) do

	local displayName = DiscountTypeDisplay[discount.Type] or "Other Discount"

	print(string.format("%s (%d%%): -%d", displayName, discount.Percent, discount.AmountInRobux))

end

print(string.format("You Pay: %d", productInfo.PriceInRobux))

```

##### Example 2

Check whether a user has an active Roblox Plus subscription and perform actions based on their subscription status.

```

local MarketplaceService = game:GetService("MarketplaceService")

local player = game.Players.LocalPlayer

local success, details = pcall(function()

    return MarketplaceService:GetRobloxSubscriptionDetailsAsync(player)

end)

if success and details.IsSubscribed then

    -- Check the length of the user's Plus subscription

    local threeMonths = 90 * 24 * 60 * 60

    if details.StartTime and (os.time() - details.StartTime.UnixTimestamp) > threeMonths then

        print("Awarding the '3-Month Subscription Veteran' skin!")

    end

    -- Check if user subscribed through the game

    if details.IsOriginExperience then

        print("Attribution confirmed: User subscribed via this game.")

    else

        print("User subscribed elsewhere: Website or another game.")

    end

end

```

##### Example 3

Prompt users to subscribe to Plus and handle the purchase flow in your game.

```

local MarketplaceService = game:GetService("MarketplaceService")

local Players = game:GetService("Players")

local teleporter = script.Parent

local showModal = true

local EXCLUSIVE_AREA_POSITION = Vector3.new(1200, 200, 60)

-- Grant the reward and teleport the subscribing user to the exclusive area

local function grantRewardAndTeleport(player)

	player:RequestStreamAroundAsync(EXCLUSIVE_AREA_POSITION)

	local character = player.Character

	if character and character.Parent then

		local currentPivot = character:GetPivot()

		character:PivotTo(currentPivot * CFrame.new(EXCLUSIVE_AREA_POSITION))

	end

end

-- Detect when the character touches the teleporter

teleporter.Touched:Connect(function(otherPart)

	local player = Players:GetPlayerFromCharacter(otherPart.Parent)

	if not player then

		return

	end

	if not player:GetAttribute("CharacterPartsTouching") then

		player:SetAttribute("CharacterPartsTouching", 0)

	end

	player:SetAttribute("CharacterPartsTouching", player:GetAttribute("CharacterPartsTouching") + 1)

	if player.HasRobloxSubscription then

		-- User already has Roblox Plus; grant the reward immediately

		grantRewardAndTeleport(player)

	else

		-- Prompt Roblox Plus subscription

		if not showModal then

			return

		end

		showModal = false

		task.delay(5, function()

			showModal = true

		end)

		MarketplaceService:PromptRobloxSubscriptionPurchase(player)

	end

end)

-- Detect when the character exits the teleporter

teleporter.TouchEnded:Connect(function(otherPart)

	local player = Players:GetPlayerFromCharacter(otherPart.Parent)

	if player and player:GetAttribute("CharacterPartsTouching") then

		player:SetAttribute("CharacterPartsTouching", player:GetAttribute("CharacterPartsTouching") - 1)

	end

end)

-- Grant the reward when the server confirms a membership change

-- Connect HasRobloxSubscription change for each player

Players.PlayerAdded:Connect(function(player)

	player:GetPropertyChangedSignal("HasRobloxSubscription"):Connect(function()

		if player.HasRobloxSubscription

			and player:GetAttribute("CharacterPartsTouching")

			and player:GetAttribute("CharacterPartsTouching") > 0

		then

			grantRewardAndTeleport(player)

		end

	end)

end)

```

##### Example 4

Detect when the user closes the purchase prompt UI.

```

local MarketplaceService = game:GetService("MarketplaceService")

local function onPromptRobloxSubscriptionPurchaseFinished(player, didTryPurchasing)

	if didTryPurchasing then

		-- User attempted to subscribe; wait for HasRobloxSubscription change to confirm

		print(player.Name, "attempted to subscribe to Roblox Plus")

	else

		print(player.Name, "closed the Roblox Plus subscription prompt without purchasing")

	end

end

MarketplaceService.PromptRobloxSubscriptionPurchaseFinished:Connect(onPromptRobloxSubscriptionPurchaseFinished)

```

## [Earn from paid private server time](#earn-from-paid-private-server-time)[](#earn-from-paid-private-server-time)

Roblox Plus subscribers can create a paid [private server](/docs/production/monetization/private-servers)  for free in your game. To make sure that you can still earn from this server, Roblox compensates you based on the time Plus subscribers spend in the paid private server they create within your game.

Payouts are based on the time a Plus subscriber spends in the paid private server they create themselves.  This means that if a Plus subscriber invites another Plus subscriber to their paid private server, only the server owner's time counts toward your earnings. Time spent by the invited subscriber does not count.

On the Plus subscription renewal day, Roblox evaluates paid private server usage over the previous 30 days for that subscriber. This evaluation occurs even if the subscriber cancels Plus instead of renewing. Roblox then determines the subscriber's top five paid private servers across Roblox , based on the amount of time they spent in each server during that period. The paid private server in your game qualifies if it's among those five and if the subscriber has spent a minimum of 60 cumulative minutes in it.

If a Plus subscriber, including a subscriber on a Free Plus Trial, spends at least 60 cumulative minutes over the last 30 days  in the paid private server they created within your game, you can earn up to 100 Robux for that subscriber  based on the server price.

In the following example, Private Servers A, B, and C qualify because the Plus subscriber spent at least 60 minutes in each server during the last 30 days. Private Servers D and E don't qualify because they don't meet the 60-minute threshold. These represent the subscriber's top five paid private servers across Roblox. Across the qualifying servers, the creator earns a combined 205 Robux from this Plus subscriber.

| Game's paid private server | | Server price | | Cumulative time (30 days prior to renewal) | | Creator earnings |
| Private Server A | | 100 Robux | | 120 minutes | | 70 Robux (70% revenue share on a 100 Robux server price) |
| Private Server B | | 200 Robux | | 80 minutes | | 100 Robux (70% revenue share on a 200 Robux server price, capped at 100 Robux) |
| Private Server C | | 50 Robux | | 70 minutes | | 35 Robux (70% revenue share on a 50 Robux server price) |
| Private Server D | | 60 Robux | | 15 minutes | | Not eligible (less than 60 minutes) |
| Private Server E | | 70 Robux | | 10 minutes | | Not eligible (less than 60 minutes) |

## [Earn from Robux transfers](#earn-from-robux-transfers)[](#earn-from-robux-transfers)

Robux transfers allow Plus subscribers to send Robux directly to other users. You can implement the Transfers API to prompt these transfers within your game and earn a share of each transfer.

When a Plus subscriber initiates a transfer prompted by [PromptRobuxTransferAsync](/docs/reference/engine/classes/MarketplaceService#PromptRobuxTransferAsync)  inside your game, you receive 10% of the transfer amount . For example, if a subscriber transfers 100 Robux to another user, the recipient receives 90 Robux (90%) and your game receives 10 Robux (10%).

Robux your game earns from transfers is eligible for the DevEx program . Roblox does not take a fee from these transfers.

When setting up transfers in your game, the amount must be between 10 and 500 Robux per transaction.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/roblox-plus/TransferRobuxPrompt.png)

For more information about implementing Robux transfers within your game, see [Robux transfers](/docs/production/monetization/robux-transfers) .

## [Track your Plus earnings](#track-your-plus-earnings)[](#track-your-plus-earnings)

You can track your earnings from users who subscribe to Roblox Plus through your in-game prompts, Robux transfers using the Transfers API, and time spent by Plus subscribers in your paid private servers, whether they join from within your game or outside of it.

To see a detailed breakdown of your Plus subscription incentives:

1.

In Creator Hub, go to Creations  and select a game.

2.

Go to Monetization  ⟩ Roblox Plus .

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/roblox-plus/Roblox-Plus-Analytics.png)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
