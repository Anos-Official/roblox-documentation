<!-- Source: https://create.roblox.com/docs/en-us/production/monetization/paid-access-robux -->

Paid access in Robux | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/production/monetization/paid-access-robux.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Earn](/docs/en-us/production/monetization)

# Paid access in Robux

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/production/monetization/paid-access-robux.md)

Paid access  lets you charge users a one-time fee in Robux to access a game on desktop, mobile, VR, and most gaming consoles. Users who purchase access continue to have access to the game even if you increase the price or disable paid access.

Paid access can limit the number of users who join your game, as some users might not want to pay a fee for access.

Some developers temporarily enable paid access to create a closed beta so that their most engaged users can have early access to a game to help with testing and feedback. If you choose to do this, make sure to let users know that they're purchasing a beta version of your game.

Games with paid access are not available on Xbox.

## [Eligibility](#eligibility)[](#eligibility)

To charge users for paid access in Robux, you must:

-

Have a verified email address.

-

Have an account that is at least 30 days old.

## [Pricing](#pricing)[](#pricing)

You can charge users anywhere from 25 to 1000 Robux for paid access to your game.

## [Payouts](#payouts)[](#payouts)

Payouts for purchases of paid access in Robux are held in escrow for up to 7 days before they're paid out and deposited into the bank linked to your Roblox account.

## [Refunds](#refunds)[](#refunds)

Refunds are not available for users who purchase paid access in Robux.

## [Enable paid access in the Creator Hub](#enable-paid-access-in-the-creator-hub)[](#enable-paid-access-in-the-creator-hub)

To enable paid access in the Creator Hub:

1.

Go to Creations  and select a game.

2.

Go to Audience  ⟩ Access Settings .

3.

Under Payment , select Requires Robux  and enter the amount of Robux you want users to pay for access. The price you enter affects the amount of Robux you earn per sale.

4.

Under Devices , select which devices you want to enable paid access for.

5.

Click Save Changes .

## [Enable paid access in Roblox Studio](#enable-paid-access-in-roblox-studio)[](#enable-paid-access-in-roblox-studio)

To enable paid access in Roblox Studio:

1.

Open Studio's File  ⟩ Experience Settings  window.

2.

Under Monetization , click Configure on Creator Hub .

3.

Follow the steps to [enable paid access in the Creator Hub](#enable-paid-access-in-the-creator-hub) .

## [Demo mode](#demo-mode)[](#demo-mode)

Demo mode  lets users try your paid access game before purchasing it. When demo mode is enabled, any user can join your game even if they haven't paid for access. You can then use scripting to detect whether a user owns the game and tailor their gameplay accordingly, for example by limiting access to certain areas or features until they purchase.

### [Enable demo mode](#enable-demo-mode)[](#enable-demo-mode)

On the Access Settings  page for your game, toggle Enable Demo Mode  on under the Robux payment section.

After toggling demo mode on or off, there is a cooldown period before you can change the setting again. Plan accordingly before enabling or disabling the feature.

### [Control the demo experience in scripts](#control-the-demo-experience-in-scripts)[](#control-the-demo-experience-in-scripts)

Use [MarketplaceService:PlayerOwnsAssetAsync()](/docs/en-us/reference/engine/classes/MarketplaceService#PlayerOwnsAssetAsync)  to check whether a user has purchased access to your game. Users who haven't purchased access are in demo mode, and you can limit what content they can see or interact with.

Place your access checks in a [Script](/docs/en-us/reference/engine/classes/Script)  under [ServerScriptService](/docs/en-us/reference/engine/classes/ServerScriptService) . Verify access on the server before allowing restricted actions, rather than only hiding client UI.

The following code sample shows how to gate content behind a purchase check:

```

local MarketplaceService = game:GetService("MarketplaceService")

local Players = game:GetService("Players")

local PLACE_ID = game.PlaceId

local function setAccess(player: Player)

  local success, ownsAccess = pcall(function()

    return MarketplaceService:PlayerOwnsAssetAsync(player, PLACE_ID)

  end)

  if not success then

    warn("Failed to check ownership for", player.Name)

    ownsAccess = false

  end

  if ownsAccess then

    -- Grant full access to the game

  else

    -- Player is in demo mode: grant only demo access

  end

end

Players.PlayerAdded:Connect(function(player)

  task.spawn(setAccess, player)

end)

for _, player in Players:GetPlayers() do

  task.spawn(setAccess, player)

end

```

If a demo player purchases access during the same session, run the ownership check again on the server before granting full access.

## [Policies](#policies)[](#policies)

Robux paid access games must:

-

Follow the [Community Standards](https://en.help.roblox.com/hc/en-us/articles/203313410)  and [Terms of Use](https://en.help.roblox.com/hc/articles/115004647846) .

-

Be public and available to all users.

-

Not have [private servers](/docs/en-us/production/monetization/private-servers) .

-

Not allow users to download copies of any places within the game. Copying a game is automatically disabled when you enable paid access.

-

Run properly and be playable. If a large number of users reports that a game is broken, the game might be quarantined and earnings still in escrow refunded to users.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
