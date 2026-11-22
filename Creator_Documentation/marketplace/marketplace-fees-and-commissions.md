<!-- Source: https://create.roblox.com/docs/en-us/marketplace/marketplace-fees-and-commissions -->

Marketplace fees and commissions | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/marketplace/marketplace-fees-and-commissions.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. Marketplace

# Marketplace fees and commissions

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/marketplace/marketplace-fees-and-commissions.md)

You can create and sell bodies, heads, clothing, accessories, emotes, makeup, animation packs, and backgrounds on the [Marketplace](https://www.roblox.com/catalog) . After you pay any applicable upload fees, you can upload your new asset for marketplace approval. Once the moderation team reviews and approves your asset, you can set your item for sell on the Marketplace.

You receive a commission every time users purchase your item. If users purchase your item within a game using the [Avatar Inspect Menu](/docs/en-us/players/avatar-inspect-menu) , [Avatar Editor Service](/docs/en-us/players/avatar-editor) , or [MarketplaceService](/docs/en-us/reference/engine/classes/MarketplaceService) , the game owner also receives a commission. For information on viewing your sales data, see [Sales Data analytics](/docs/en-us/production/analytics/analytics-dashboard#sales-data) .

## [Upload fees](#upload-fees)[](#upload-fees)

To upload an avatar asset to the Marketplace, you must:

1.

Verify your account through your own [government ID](/docs/en-us/production/publishing/account-verification#verify-through-government-id)  or a linked [parental account](https://about.roblox.com/parental-controls)  with government ID verification.

2.

Pay a standard upload fee of 80 Robux  per submission.

-

Items that use an [emissive mask](/docs/en-us/art/modeling/surface-appearance#emissive-mask)  require an upload fee of 500 Robux .

-

[Backgrounds](/docs/en-us/avatar/backgrounds)  require an upload fee of 200 Robux .

In general, upload fees are not refunded if an item is rejected through moderation. If your asset clears the uploading process, your asset is ready to publish to the Marketplace.

## [Publishing advance](#publishing-advance)[](#publishing-advance)

A publishing advance is a refundable upfront fee that you pay at the time of publishing an item. The publishing advance does not apply for free Limited items  which require a [per-unit fee](#per-unit-fee) . Items taken off-sale and put back on-sale do not require another publishing advance.

The publishing advance depends on the type of Marketplace item, whether it's Limited or not, and whether it uses an [emissive mask](/docs/en-us/art/modeling/surface-appearance#emissive-mask) . The pricing calculator lists current publishing advances and free item publishing fees, which you can view below.

[View Current Publishing Advances and Fees](https://create.roblox.com/dashboard/creations/pricing)

Publishing advance example scenario

For an example of how the publishing advance is recouped, the following table represents a hypothetical situation where the publishing advance is 1000 Robux , and the item is sold in a game at 400 Robux :

|  | | Creator Receives | | Roblox Receives | | Affiliate Receives |
| --- | --- |
|  | | 30% Creator Commission | | Publishing Advance Rebate (from Platform Commission) | | 30% Platform Commission | | 40% Affiliate (game owner) Commission |
| Unit 1 sold | | 120 Robux | | 120 Robux | | ← Given to creator | | 160 Robux |
| Unit 2 sold | | 120 Robux | | 120 Robux | | ← Given to creator | | 160 Robux |
| Unit 3 sold | | 120 Robux | | 120 Robux | | ← Given to creator | | 160 Robux |
| Unit 4 sold  | | 120 Robux | | 120 Robux | | ← Given to creator | | 160 Robux |
| Unit 5 sold | | 120 Robux | | 120 Robux | | ← Given to creator | | 160 Robux |
| Unit 6 sold | | 120 Robux | | 120 Robux | | ← Given to creator | | 160 Robux |
| Unit 7 sold | | 120 Robux | | 120 Robux | | ← Given to creator | | 160 Robux |
| Unit 8 sold
* Creator has received 960 Robux in total publishing advance rebates* | | 120 Robux | | 120 Robux | | ← Given to creator | | 160 Robux |
| Unit 9 sold
* Creator has received 1000 Robux in total publishing advance rebates* | | 120 Robux | | 40 Robux | | 80 Robux | | 160 Robux |
| Unit 10 sold
* No more publishing advance rebate* | | 120 Robux | | 0 Robux | | 120 Robux | | 160 Robux |
| Continues with each unit sold | | … | | … | | … | | … |

See the following guidelines:

-

Publishing advance rebates are subject to revenue share.

-

Once per day, Roblox processes and reimburses rebates from your sales and adds them to your transaction report.

-

If you see the rebate on your transaction report, the credit has been applied to your account.

-

The 30 day escrow does not apply for rebates.

-

You can access this data on the Creator Dashboard's [My Transactions](https://www.roblox.com/transactions)  report, by filtering Type of Transaction  to Publishing Advance Rebates .

 ![Transaction report filtered by Publishing Advance Rebates.](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Transaction-Report.png)

-

If a sale occurs after Roblox processes rebates, you may need to wait until the next day's processing to receive the rebate credit and see the rebate in the transaction report.

## [Commissions](#commissions)[](#commissions)

When you or your group sell avatar items on the platform, a portion of the sales is split between you or your group and Roblox. If the item is sold within a game, the revenue share will additionally be split with the owner of the game. Both individual accounts and groups must  follow [Marketplace Creator Requirements](/docs/en-us/marketplace/marketplace-policy#creator-requirements)  to keep items listed on the Marketplace and eligible for commissions.

| Marketplace Purchase | | In-game Purchase |
| Creator receives 30% | |
-

Creator receives 30%

-

Game owner receives 40%

 |

There is a 30 day escrow hold for each purchase. Roblox holds the commission from the sale of your items for 30 days starting from the date of sale and your Robux share of the sale.

Limited items that are sold for free follow a different per-unit payout structure. See [Per-Unit Fee](#per-unit-fee)  for more information.

### [Progressive revenue share](#progressive-revenue-share)[](#progressive-revenue-share)

Avatar items sold in the Marketplace use a progressive revenue share system: the more an item is priced above its asset type's [price floor](#price-ranges) , the greater the share of revenue the creator earns.

Additional guidelines:

-

Progressive revenue share only applies to purchases in the Marketplace . In-game purchases receive the base 30% commission.

-

The revenue share % is progressive. For example, an item priced at 1.15x the price floor will receive ~33% of the creator revenue share.

-

[Regional pricing](/docs/en-us/production/monetization/regional-pricing)  adjustments do not affect revenue share percentage. Revenue share is based solely on the listed price relative to current floor.

| Price floor multiple | | Total creator revenue share |
| 1 | | 30% |
| 1.3 | | 37% |
| 1.5 | | 41% |
| 2 | | 50% |
| 2.5 | | 57% |
| 3 | | 62% |
| 3.5 | | 65% |
| 4 | | 67% |
| 5 | | 69% |
| 6 | | 70% |
| 8 | | 70% |
| 10 | | 70% |

Progressive commission example scenario

The following is an example of a hypothetical breakdown of various item prices and expected creator share returns. The price floor in this scenario is set to 100.

| Item price
 * (Price floor at 100)* | | Revenue share % | | Creator share |
| 100 | | 30% | | 30 |
| 130 | | 37% | | 48 |
| 150 | | 41% | | 62 |
| 200 | | 50% | | 100 |
| 250 | | 57% | | 142 |
| 300 | | 62% | | 186 |
| 350 | | 65% | | 228 |
| 400 | | 67% | | 268 |
| 500 | | 69% | | 345 |
| 600 | | 70% | | 420 |
| 800 | | 70% | | 560 |
| 1000 | | 70% | | 700 |

## [Limiteds](#limiteds)[](#limiteds)

When setting assets on sale, you can [configure your creation](/docs/en-us/marketplace/publish-to-marketplace#marketplace-settings)  as a Limited  item to set an available quantity for that asset.

At this time, only Roblox-created Limiteds are tradeable.

### [Per-unit fee](#per-unit-fee)[](#per-unit-fee)

When publishing free Limiteds, you must provide a per-unit fee depending on the quantity being published and other factors like the type of asset being uploaded. This payment depends on a range of market-based factors and may change over time.

As a hypothetical case where Limited hat items are 100 Robux per-unit, if 200 Limited hats are listed at a 0  Robux price, the creator pays 20,000  Robux to list this free Limited item. For free Limiteds, Roblox keeps the entire per-unit fee .

### [Reselling](#reselling)[](#reselling)

If reselling is enabled by the original creator, [Roblox Plus](/docs/en-us/production/monetization/roblox-plus)  or [Premium](https://www.roblox.com/premium/membership)  members can resell purchased Limited items. Every time a creator's item is resold, the creator benefits from a 10% original creator commission. After purchasing a Limited, there is up to a 30 day holding period when the item cannot be resold.

Reselling community-created Limiteds is not available for accounts based in Japan.

Selling Limiteds : As a reminder, when selling anything on Roblox, the item creator, the seller, and Roblox receive a split of every transaction as follows:

-

30% to creator

-

40% to seller/affiliate

-

30% to Roblox

Reselling community-created Limiteds : The following is the breakdown of the earning percentages for community-created Limited resales:

-

50% to reseller

-

10% to creator

-

10% to seller/affiliate

-

30% to Roblox

Similar to other commission and payment breakdowns, a single party can receive one or more commissions for a single transaction, such as the case where the original creator is also the reseller.

Robux acquired from trading or selling items that you didn't create are not considered earned and are ineligible for the Developer Exchange program. For more information on earning Robux, see [Earned Robux & DevEx Rates](https://en.help.roblox.com/hc/en-us/articles/203314100-Developer-Exchange-DevEx-FAQs#h_01FTN4PJV8AS4JHD2YHS363TDE) .

### [Rate limits](#rate-limits)[](#rate-limits)

To protect against automated purchases, Roblox sets purchase limits for Limiteds sold in-game or in the Marketplace. For Limiteds, the following applies:

-

Users are subject to the following purchase rate limits:

-

9 successful purchases per minute per user.

-

1 purchase request every 2 seconds per item per user.

-

A maximum of 3 successful purchases per user per item.

-

For in-game purchases, users must be in the game for 60 seconds to successfully complete a purchase.

## [Timed options](#timed-options)[](#timed-options)

At this time, timed options are available for 3D shirts, pants, and sweater categories.

Timed options allows users to purchase your items for a period of time of either 3, 7, or 14 days at a cheaper cost. You can enable or disable timed options for your Marketplace assets [in bulk](#in-bulk)  or [per item](#per-item) .

![Example of timed options displaying for end user viewing marketplace item](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Timed-Options-Mobile-Marketplace.png) With timed options enabled, users gain access to multiple purchase options for each available time range.

### [In bulk](#in-bulk)[](#in-bulk)

To toggle timed options for multiple assets:

1.

Navigate to your [Creations](https://create.roblox.com/dashboard/creations)  page > Avatar items.

2.

Filter by avatar asset type, such as Clothing .

3.

On the top right, select the Timed option  button.

 ![Timed options button on top right of Creations page](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Timed-Options-Bulk-A.png)

4.

Follow the prompts to confirm the bulk selection and timed option settings.

 ![Confirmation prompt for setting timed options for all assets](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Timed-Options-Bulk-B.png)

### [Per item](#per-item)[](#per-item)

To toggle timed options for individual assets:

1.

In your [Creations](https://create.roblox.com/dashboard/creations)  tab, navigate to the individual asset's Manage Item  page.

2.

Toggle the timed option for your asset.  ![Individual timed option toggle on the specific asset sale setting page](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Timed-Options-Per-Item.png)

3.

When complete, click the Save Changes  button.

## [Price ranges](#price-ranges)[](#price-ranges)

Depending on the 3D asset type, you must set the price of the item within the marketplace price range. If you are selling a [Limited](#limiteds)  item, you can set your item price as 0 , or any value after the Limiteds Price Floor .

[View Current Marketplace Ranges](https://create.roblox.com/dashboard/creations/pricing)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
