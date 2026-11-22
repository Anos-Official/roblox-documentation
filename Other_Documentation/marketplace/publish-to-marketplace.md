<!-- Source: https://create.roblox.com/docs/marketplace/publish-to-marketplace -->

Publish to Marketplace | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/marketplace/publish-to-marketplace.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. Marketplace

# Publish to Marketplace

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/marketplace/publish-to-marketplace.md)

In order to publish and sell assets on the Marketplace, your account or group must first meet [Roblox's Creator and Group requirements](/docs/marketplace/marketplace-policy#creator-and-group-requirements) . Users who satisfy the requirements and have not hit their [publishing limits](#upload-and-publish-limits) , can upload and sell their assets in the following general steps:

1.

[Upload the asset](#upload-an-asset)  through Studio for validation and moderation.

2.

[Publish the asset](#publish-an-asset)  to the Marketplace after configuring metadata and Marketplace settings.

The following publishing instructions apply to 3D accessories and clothing assets. For other asset types:

-

For information on 2D classic clothing, see [Classic clothing](/docs/avatar/classic-clothing) .

-

For information on locomotion animation sets, see [Animation packs](/docs/avatar/animation-packs) .

-

For information on backgrounds for avatars, see [Backgrounds](/docs/avatar/backgrounds) .

## [Upload and publish limits](#upload-and-publish-limits)[](#upload-and-publish-limits)

There are limits on the number of assets you can upload to Roblox and enable for sale on the Marketplace:

|  | | Limiteds | | Bodies or Heads |
| --- | --- |
| Uploading and moderation | | No limit | | No limit |
| Publishing - Enabling on sale † | | No limit for paid Limiteds. 50 per day for free Limiteds. | | No limit |

†* For assets that can be taken off-sale, only the first time the asset is enabled for sale counts against this limit.*

## [Upload an asset](#upload-an-asset)[](#upload-an-asset)

When uploading your asset, Studio checks your asset for technical issues, such as an incorrect hierarchy or accessory structure. You should also add a [custom thumbnail](/docs/marketplace/custom-thumbnails)  to your asset before uploading to customize how the item displays on the Marketplace.

-

After uploading your asset, the item is placed in the moderation queue before you can enable it on sale. See [Moderation](/docs/marketplace/moderation)  for more information on this process.

-

For details on upfront payments and fees when publishing assets to the marketplace, see [Fees and commissions](/docs/marketplace/marketplace-fees-and-commissions) .

Test all of your assets thoroughly before uploading them to ensure they adhere to Roblox's [Marketplace policy](/docs/marketplace/marketplace-policy) . If you need to fix a 3D accessory or layered clothing item after uploading, see [Update an existing item](#update-an-existing-item) .

To upload your asset:

1.

In Studio, add the Marketplace item to your workspace.

-

For accessories and clothing, the item must be an [Accessory](/docs/reference/engine/classes/Accessory)  object. For information on the required specifications, see [Rigid accessory specifications](/docs/avatar/rigid-accessories/specifications)  and [Layered clothing specifications](/docs/avatar/layered-accessories/specifications) .

-

Upload clothing and accessories as an [Accessory](/docs/reference/engine/classes/Accessory) . For information on converting your [Model](/docs/reference/engine/classes/Model)  into an [Accessory](/docs/reference/engine/classes/Accessory) , see [Accessory Fitting Tool](/docs/avatar/accessory-fitting-tool) .

-

If uploading shoes, each shoe must be their own accessory object:

-

Name the respective shoe accessories LeftShoeAccessory  and RightShoeAccessory .

-

Select both left and right shoe accessories and right-click ⟩ Group as a Model  before step 2.

-

For bodies and heads, the item must be a [Model](/docs/reference/engine/classes/Model) . For information on the required specifications, see [Avatar character specifications](/docs/avatar/character-bodies/specifications) .

-

You can add a default skin color to your body by adding a [BodyColors](/docs/reference/engine/classes/BodyColors)  object to your model.

2.

In the Explorer  window, right-click the object and select Save to Roblox .

3.

In Submit As , select Avatar Asset .

4.

In the Asset type  dropdown menu, select the appropriate marketplace asset type. Validation begins upon selection.

If you don't see this dropdown, your account might not have access to upload assets to the Marketplace. For more information, see [Creator requirements](/docs/marketplace/marketplace-policy#creator-requirements) .

![](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Publishing-Clothes.png) Uploading a clothing accessory asset

![](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Publishing-Body.png) Uploading a body asset bundle

5.

Once validation completes successfully, an item description dialog displays. Fill out the following fields and follow [metadata best practices](/docs/production/publishing/publish-games-and-places#publish-games)  when possible.

-

Title : The name of your asset in the Marketplace.

-

Creator : You can set your user or any associated groups as the creator of this asset. The creator can access the Marketplace asset to set prices, benefits, and access sales information.

6.

Click Submit  to pay any applicable upload fee and submit your asset for moderation approval.

After uploading the asset, you can find it in the Creations  tab of the [Creator Hub](https://create.roblox.com/dashboard/creations?activeTab=HairAccessory&filterIndex=0)  in a pre-published state where you can view the current moderation status or edit the title and description.

 ![List of Hat assets on the Creator Hub with current status listed below each entry.](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Creation-Page.png)

### [Organize avatar items](#organize-avatar-items)[](#organize-avatar-items)

In Creations  ⟩ Avatar Items , you can organize and browse your avatar items in the following ways:

-

Folders : In the All  tab, create a folder, then add items to it from each item's menu. Use folders to group items however you like, such as by collection, by drop, or by work in progress. Folders work for both user and group creations, hold avatar assets and bundles, and are single-level with no nesting. An item can be in more than one folder.

-

Recents : The Recents  view under the All  tab shows your 50 most recently uploaded avatar items and bundles.

-

Marketplace categories : By default, items are grouped by the same Marketplace categories that shoppers browse, rather than by asset type. Items are classified automatically, and one category can include several asset types; for example, layered clothing shirts and pants can both be classified as a Bodysuit . Newly uploaded items can take a short time to be classified, but appear in Recents  in the meantime. To group items by asset type instead, turn off Categorize by Taxonomy  in the top-right corner.

### [Update an existing item](#update-an-existing-item)[](#update-an-existing-item)

You can update a rigid or layered accessory that you've already uploaded, including items that are published on the Marketplace. The update keeps the item's asset ID, sales history, and existing owners, and owners receive the updated version automatically. An update must be the same asset type as the original item.

To update an existing item:

1.

In Studio, open your item and make your fixes.

2.

In the Explorer  window, right-click the object and select Save to Roblox .

3.

Turn on Update an existing asset  and enter the asset ID of the item you're replacing.

4.

Click Submit  to pay the upload fee and submit the update for moderation.

Keep the following in mind when updating items:

-

You can change anything before an item is published. After an item is published, updates are intended for fixes, such as fit, cages, small mesh or texture issues, or the thumbnail. The updated item must still look like the item owners bought, so substantial design changes aren't allowed.

-

Each update costs the same upload fee as a new item of that type, and every update to a published item goes through [moderation](/docs/marketplace/moderation)  before it goes live.

-

If an update isn't approved, you receive a notification in your inbox. Your original item stays unchanged, so you can adjust your changes and submit again.

### [Troubleshooting](#troubleshooting)[](#troubleshooting)

During the upload process, you might encounter issues that prevent an item from uploading. These might occur due to technical issues with the asset itself, or problems with the metadata of the asset, such as invalid ownership, or inappropriate text strings.

For technical issues during the validation step, hover over the error to see the specific failure output. Most issues may require adjusting your model in your third-party modeling application and re-importing into Studio.

See the modeling specifications for [rigid accessories](/docs/avatar/rigid-accessories/specifications) , [layered accessories](/docs/avatar/layered-accessories/specifications) , and [character bodies](/docs/avatar/character-bodies/specifications)  for technical requirements.

![An example error indicating a missing FaceControls object from an Avatar Head.](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Error-Example.png) An error that displays when a FaceControls object is not detected for head animation

For other validation issues, keep in mind the following common uploading conflicts:

-

Studio's text filter identifies inappropriate strings in the name or description.

-

Your item uses an AssetID  or TextureID  that belongs to an existing asset in the Marketplace, or doesn't belong to you or an appropriate group.

-

Your item uses an AssetID  or TextureID  that is still pending moderation.

## [Publish an asset](#publish-an-asset)[](#publish-an-asset)

You can access uploaded assets in your [Creator Dashboard](https://create.roblox.com/dashboard/creations) . Each item has a Manage Item  page where you can modify metadata, configure sale-related settings, and publish your asset to the Marketplace.

If you discover that your rigid or layered accessory is broken or doesn't work as expected, you can [update the existing item](#update-an-existing-item)  with a fix. Other item types, such as bundles, can't be updated after upload.

If a Roblox update breaks an existing asset, [submit a help ticket](https://www.roblox.com/support)  with a link to the broken item and an .rbxm  of the correct version.

Before publishing your asset, it's important to consider if you want to sell your asset as a Limited or Non-Limited item.

If your item uses licensed IP, navigate to the Item Attributes  section of the Manage Item  page, then select your approved license from the license dropdown before publishing. For information on how to request a license and how revenue share applies, see [Marketplace licenses](/docs/ip-licensing/creators#marketplace-licenses) .

### [Metadata](#metadata)[](#metadata)

You can adjust the metadata for any of your creations at any time. Keep in mind that the metadata, such as the title and description, should follow [general best practices](/docs/production/publishing/publish-games-and-places#publish-games)  to avoid moderation and improve discoverability.

 ![Manage Item page with example asset.](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Manage-Item-Page.png)

On the Manage Item page, you can update the following fields:

-

Title : The name of your asset in the Marketplace. You can modify this after publishing.

-

Description : The description of your asset in the Marketplace.

### [Item attributes](#item-attributes)[](#item-attributes)

In Item Attributes  you can set the Availability  of your asset as a Non-Limited  or a Limited  item. Each availability type changes the available item attribute fields you can modify.

-

Non-Limited  items allow for unlimited copies to be purchased.

-

Limited  items allow only a fixed quantity of items to be purchased, allowing you to sell a set number of exclusive or event-specific digital items.

| Item availability | | Sale properties |
| Non-Limited
 | | — Unlimited copies available to purchase
— Can't limit number of copies per user
— Can't sell free items
— Can't resell |
| Limited
 | | — Limits total number of copies sold
— Can limit number of original copies per user
— Can sell free items, per-unit fee applies
— Resellable |

Before selecting either option, familiarize yourself with the various [fee and commission structures](/docs/marketplace/marketplace-fees-and-commissions)  involved with different types of items and any applicable country policy limitations.

 ![Item Attribute settings.](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Item-Attributes.png)

The following item attributes only apply if you set your asset as a Limited item:

-

Quantity : The number of assets that are available on the Marketplace. The maximum quantity for paid Limiteds is 3000, while free Limiteds do not have a quantity maximum. After publishing a free Limited, you can increase its quantity by [restocking](/docs/marketplace/marketplace-fees-and-commissions#restocking)  the item.

-

Limit copies per user : (Optional) Sets the number of times a user can purchase this asset.

-

Copy limits are based on ownership. If a user owns the maximum limit of copies in their inventory, they can no longer purchase the asset from the original listing. If the user no longer owns the maximum number of copies, they can purchase the copies from the original listing.

-

After publishing, you can only increase, but not decrease, this value.

-

Free Item : Sets the selling price of this item to zero. Free Limiteds utilize a [per-unit fee structure](/docs/marketplace/marketplace-fees-and-commissions#per-unit-fee) .

-

Resellable : If enabled, users can resell your Limited item. If resold, you are eligible for [resell commissions](/docs/marketplace/marketplace-fees-and-commissions#reselling) . You can change the Resellable status  on a published item. If enabled on an item, it can not be disabled in the future.

-

The resellable attribute is not available for accounts based in Japan.

-

Enabling reselling permanently disables [restocking](/docs/marketplace/marketplace-fees-and-commissions#restocking)  for the item.

##### Limit copies per user

If you are selling a Limited item, you can enable Limit Copies Per User  to set the number of times a user can purchase this asset. This only affects the purchases from the original listing and users can still purchase additional copies of the same Limited asset from resellers. You can't change this setting after publishing.

Copy limits are based on ownership. If a user owns the maximum limit of copies in their inventory, they can no longer purchase the asset from the original listing. If the user no longer owns the maximum number of copies, they can purchase the copies from the original listing.

### [Pricing](#pricing)[](#pricing)

In the pricing section, you can set various price settings. When listing your Marketplace item, you must set your price within the appropriate [dynamic price range](/docs/marketplace/marketplace-fees-and-commissions#price-ranges)  for that asset type.

 ![Price settings fields.](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Pricing-Settings.png)

You can set two types of price controls based on the price floor:

-

Amount Above Price Floor (required)  is the amount of Robux that the item will be above the current price floor. For example, if the floor is 50 Robux and you input 5 Robux here, the price will be 55 Robux. You can also choose to set this value to zero if you want your item to always be priced at the floor price.

-

Do Not Price Below (optional)  is the lowest price a creator's item can go. It is optional and will always be respected. This input is helpful if you care about what the lowest price your item can be sold for. For example, if you input 200 Robux here, your item price will never drop below 200 Robux regardless of what the price floor is.

If you had a Marketplace listing before the implementation of the dynamic price range, the following price controls now apply until changed:

-

Amount Above Price Floor  defaults to 0 Robux.

-

Do Not Price Below  defaults to the existing price of the item.

When setting a price, you can see the percentage breakdown of commissions in the dialog box. A similar breakdown on fees, when applicable, is provided at the bottom of the prompt. See [Marketplace fees and commissions](/docs/marketplace/marketplace-fees-and-commissions)  for more information on the fees and commissions for Marketplace items.

##### Regional Pricing for Avatar items

Regional Pricing allows you to offer your item to users at region-specific prices. After you determine the item's global price, Roblox uses a variety of signals like a region's purchasing power, currency exchange rates, and local spending behavior to set the most appropriate price for the item region by region.

Regional Pricing is opted-in by default. You can opt-out any time. For more information, see [Regional Pricing](/docs/production/monetization/regional-pricing) .

### [Sale location](#sale-location)[](#sale-location)

The Sale Location  option sets where you can sell your asset beyond the Marketplace. In some cases, you may want to limit the availability of your asset to certain games, or only the Marketplace.

 ![Sale location fields.](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Sale-Location.png)

Games that sell Marketplace items receive an additional [commission](/docs/marketplace/marketplace-fees-and-commissions)  including transactions made through the [Inspect Menu](/docs/players/avatar-inspect-menu)  or [through the API](/docs/players/avatar-editor)  within a game.

The following location options are available for all items:

| Location | | Description |
| Marketplace and All Experiences | | Users can purchase this item in the Marketplace or any games that offer Marketplace purchases. This is the default setting. |
| Experience By Place ID (API Only) | | Users can only purchase the original stock of this item in the games associated with the provided Place ID. Only one Place ID per game is required and creators can update and change Place IDs at any time.

After saving a new Place ID, the game owner must manually [enable the avatar item](/docs/production/monetization/avatar-items)  for their game. |

### [Publish item](#publish-item)[](#publish-item)

When first publishing your asset, select the Publish Item  button at the end of the form to pay the [publishing fee](/docs/marketplace/marketplace-fees-and-commissions#publishing-advance)  and list your item on sale.

### [On sale toggle](#on-sale-toggle)[](#on-sale-toggle)

 ![On-sale toggle at top-right of page.](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Sale-Toggle.png)

You can disable the sale of a published asset by disabling the On Sale  at the top of the Manage Item  page.

After enabling an item for sale, you can take the item off-sale by disabling the toggle. A publishing fee is not required to re-enable.

To permanently archive your asset, see [Archive assets](/docs/marketplace/moderation#archive-assets) .

### [Schedule item sale](#schedule-item-sale)[](#schedule-item-sale)

To schedule the sale of your asset in the Manage Item  page, click Schedule Sale  under the On Sale  toggle and enter a Sale Start  date and an optional Sale End  date. If you don't enter an end date, the item is on sale indefinitely.

You can use scheduling to sell both Limited and Non-Limited assets.

You can schedule sales up to 30 days in advance.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
