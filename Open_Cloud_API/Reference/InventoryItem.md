<!-- Source: https://create.roblox.com/docs/cloud/reference/InventoryItem -->

Inventories | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/cloud/reference/features/inventories.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs)
2. /
3. [Open Cloud API](/docs/en-us/cloud)

# Inventories

English

Filter

Filter

POST

Adds an item to the appropriate collection

/​v1/​collections/​items/​{itemType}/​{itemTargetId}

inventory.roblox.com

Cookie

DELETE

Removes an item to the appropriate collection

/​v1/​collections/​items/​{itemType}/​{itemTargetId}

inventory.roblox.com

Cookie

## Assets

GET

Gets a list of owners of an asset.

/​v2/​assets/​{assetId}/​owners

inventory.roblox.com

Cookie None

GET

Gets a list of owners of a collectible item.

/​v2/​collectible-​items/​{collectibleItemId}/​owners

inventory.roblox.com

Cookie

DELETE

Give up an asset owned by the authenticated user. Assets that are created by Roblox user or are limited edition are not eligible for deletion and will return NotEligibleForDelete.

/​v2/​inventory/​asset/​{assetId}

inventory.roblox.com

Cookie

## Interactions

GET

Return favorites categories for a user

/​v1/​users/​{userId}/​categories/​favorites

inventory.roblox.com

Cookie None

## Places

GET

Gets Created, MyGames, or OtherGames places inventory for a user

/​v1/​users/​{userId}/​places/​inventory

inventory.roblox.com

Cookie None

## Users

GET

List Inventory Items Beta

/​cloud/​v2/​users/​{user_id}/​inventory-​items

apis.roblox.com

API Key OAuth 2.0 HttpService

GET

Gets all collectible assets owned by the specified user.

/​v1/​users/​{userId}/​assets/​collectibles

inventory.roblox.com

Cookie None

GET

Return inventory categories for a user

/​v1/​users/​{userId}/​categories

inventory.roblox.com

Cookie None

GET

Gets whether a user owns an item of type itemType with id itemTargetId.

/​v1/​users/​{userId}/​items/​{itemType}/​{itemTargetId}/​is-​owned

inventory.roblox.com

Cookie None

## Not Recommended

GET

Get user's inventory by multiple Roblox.Platform.Assets.AssetType.

Recommended Alternatives

/​v2/​users/​{userId}/​inventory

inventory.roblox.com

Cookie None

GET

Gets user's inventory based on specific asset type

Recommended Alternatives

/​v2/​users/​{userId}/​inventory/​{assetTypeId}

inventory.roblox.com

Cookie None

GET

Given a package ID, returns the list of asset IDs for that package

Deprecated

Recommended Alternatives

/​v1/​packages/​{packageId}/​assets

inventory.roblox.com

Cookie None

GET

Gets whether the specified user's inventory can be viewed.

Recommended Alternatives

/​v1/​users/​{userId}/​can-​view-​inventory

inventory.roblox.com

Cookie None

GET

Gets owned items of the specified item type. Game Servers can make requests for any user, but can only make requests for game passes that belong to the place sending the request. Place creators can make requests as if they were the Game Server.

Recommended Alternatives

/​v1/​users/​{userId}/​items/​{itemType}/​{itemTargetId}

inventory.roblox.com

Cookie None

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
