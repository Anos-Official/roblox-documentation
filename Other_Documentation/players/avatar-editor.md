<!-- Source: https://create.roblox.com/docs/players/avatar-editor -->

Avatar Editor Service | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/players/avatar-editor.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Players](/docs/players)
6. /
7. Player UI

# Avatar Editor Service

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/players/avatar-editor.md)

The Avatar Editor Service lets you access and make changes to a user's avatar within a game. The Avatar Editor Service can also access a user's inventory and the [Marketplace](https://www.roblox.com/catalog)  to save outfits and purchase avatar items to the user's account.

We recommend implementing the Avatar Editor Service with an in-game avatar editor for a complete character customization experience. See the [Simple Avatar Editor Demo](https://www.roblox.com/games/9376329300/Simple-Avatar-Editor-Demo)  reference place for an example of this feature.

To begin using the Avatar Editor Service, you must first [request access](#request-access)  to the user's inventory. After access is successfully granted, you can perform the following actions:

-

[Read user's inventory](#read-user-inventory)  to get a list of items owned by the user.

-

[Search the Marketplace](#search-the-marketplace) , using a variety of properties to filter and sort.

-

[Equip avatar items and save outfits](#save-avatars-and-outfits)  to the user's avatar.

-

[Prompt the user to purchase](#purchase-items)  an Marketplace item.

## [Request access](#request-access)[](#request-access)

To begin accessing a user's inventory, you need to prompt the user to allow access through [PromptAllowInventoryReadAccess()](/docs/reference/engine/classes/AvatarEditorService#PromptAllowInventoryReadAccess) . You need to perform this request once per session.

Use the following code sample to initiate the access prompt and listen for the user response:

```

local AvatarEditorService = game:GetService("AvatarEditorService")

AvatarEditorService:PromptAllowInventoryReadAccess()

local result = AvatarEditorService.PromptAllowInventoryReadAccessCompleted:Wait()

if result == Enum.AvatarPromptResult.Success then

  -- Access granted!

end

```

The user receives the following prompt:

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-editor-service/Avatar-Editor-Access-Items.png)

Once the user accepts the prompt, the [AvatarEditorService](/docs/reference/engine/classes/AvatarEditorService)  can begin accessing the user's inventory.

## [Read user inventory](#read-user-inventory)[](#read-user-inventory)

Once access is granted by the user, you can read their inventory with the [GetInventory()](/docs/reference/engine/classes/AvatarEditorService#GetInventory)  function, supplying an array of [AvatarAssetTypes](/docs/reference/engine/enums/AvatarAssetType)  to filter by. This function returns an [InventoryPages](/docs/reference/engine/classes/InventoryPages)  object containing the user owned items.

Use the following code sample to print a list of specific accessories in a user's inventory:

```

local AvatarEditorService = game:GetService("AvatarEditorService")

AvatarEditorService:PromptAllowInventoryReadAccess()

local result = AvatarEditorService.PromptAllowInventoryReadAccessCompleted:Wait()

if result == Enum.AvatarPromptResult.Success then

  -- Access granted!

  local assetTypes = {

    Enum.AvatarAssetType.BackAccessory,

    Enum.AvatarAssetType.ShoulderAccessory,

    Enum.AvatarAssetType.WaistAccessory

  }

  local pagesObject = AvatarEditorService:GetInventory(assetTypes)

  local currentPage = pagesObject:GetCurrentPage()

  for _, item in currentPage do

    print(item)

  end

end

```

## [Search the Marketplace](#search-the-marketplace)[](#search-the-marketplace)

[AvatarEditorService](/docs/reference/engine/classes/AvatarEditorService)  includes functions and events which let you search the Roblox catalog. To search, supply your query with a [CatalogSearchParams](/docs/reference/engine/datatypes/CatalogSearchParams)  object that includes one or more of the following properties:

| Property | | Description |
| --- | --- |
| AssetTypes | | An array of [Enum.AvatarAssetType](/docs/reference/engine/enums/AvatarAssetType)  such as Enum.AvatarAssetType.BackAccessory. |
| BundleTypes | | An array of [Enum.BundleType](/docs/reference/engine/enums/BundleType)  such as Enum.BundleType.BodyParts. |
| CategoryFilter | | A [Enum.CatalogCategoryFilter](/docs/reference/engine/enums/CatalogCategoryFilter)  describing the various catalog categories like "Featured" or "Community Creations". By default this is set to [Enum.CatalogCategoryFilter.None](/docs/reference/engine/enums/CatalogCategoryFilter#None) |
| MaxPrice | | An integer describing the maximum price to filter. |
| MinPrice | | An integer describing the minimum price to filter. By default, MinPrice is ** 0** . |
| SearchKeyword | | A string to query against item descriptions in the catalog. |
| SortType | | A [Enum.CatalogSortType](/docs/reference/engine/enums/CatalogSortType)  that describes how the results are ordered. By default this is set to [Enum.CatalogSortType.Relevance](/docs/reference/engine/enums/CatalogSortType#Relevance) . |
| IncludeOffSale | | A boolean describing whether the results of the search include off sale items. By default this is set to false. |
| CreatorId | | An integer to specify a given creator. You can use either a UserId or a GroupId. |
| CreatorName | | A string used to search by items created by a given creator. You can use either a User Name or a Group Name. |

The following code sample constructs a [CatalogSearchParams](/docs/reference/engine/datatypes/CatalogSearchParams)  object for Back  and Shoulder  asset types, and passes that through a [SearchCatalog()](/docs/reference/engine/classes/AvatarEditorService#SearchCatalog)  call:

```

local AvatarEditorService = game:GetService("AvatarEditorService")

local catalogSearchParams = CatalogSearchParams.new()

local assetTypes = {

  Enum.AvatarAssetType.BackAccessory,

  Enum.AvatarAssetType.ShoulderAccessory

}

catalogSearchParams.AssetTypes = assetTypes

local pagesObject =

--This function returns a CatalogPages object containing the results.

AvatarEditorService:SearchCatalog(catalogSearchParams)

local currentPage = pagesObject:GetCurrentPage()

for _, item in currentPage do

  print(item)

end

```

## [Save avatars and outfits](#save-avatars-and-outfits)[](#save-avatars-and-outfits)

When used alongside an in-game avatar editor, [AvatarEditorService](/docs/reference/engine/classes/AvatarEditorService)  can save and update avatar items and outfits to the Roblox platform. Users don't receive catalog items they don't own when saving an avatar or outfit.

Any [HumanoidDescription](/docs/reference/engine/classes/HumanoidDescription)  can be saved to the user's current avatar with [PromptSaveAvatar()](/docs/reference/engine/classes/AvatarEditorService#PromptSaveAvatar) . This may include:

-

Pre-defined avatar configurations that you've built using existing catalog items.

-

Any configuration that the user has chosen through an in-game avatar editor.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-editor-service/Avatar-Editor-Equip-Items.png)

Since [AvatarEditorService:PromptSaveAvatar()](/docs/reference/engine/classes/AvatarEditorService#PromptSaveAvatar)  does not yield, you can get the result by listening to the [AvatarEditorService.PromptSaveAvatarCompleted](/docs/reference/engine/classes/AvatarEditorService#PromptSaveAvatarCompleted)  event.

The following code will save a current [HumanoidDescription](/docs/reference/engine/classes/HumanoidDescription)  using [PromptSaveAvatar()](/docs/reference/engine/classes/AvatarEditorService#PromptSaveAvatar)  and checks for a successful [AvatarEditorService.PromptSaveAvatarCompleted](/docs/reference/engine/classes/AvatarEditorService#PromptSaveAvatarCompleted)  event:

```

local AvatarEditorService = game:GetService("AvatarEditorService")

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local character = player.Character or player.CharacterAdded:Wait()

local humanoid = character:WaitForChild("Humanoid")

local currentDescription = humanoid:GetAppliedDescription()

AvatarEditorService:PromptSaveAvatar(currentDescription, humanoid.RigType)

local result = AvatarEditorService.PromptSaveAvatarCompleted:Wait()

if result == Enum.AvatarPromptResult.Success then

  -- Avatar saved!

end

```

To save any [HumanoidDescription](/docs/reference/engine/classes/HumanoidDescription)  as an outfit (without overwriting the user's current avatar), use [AvatarEditorService:PromptCreateOutfit()](/docs/reference/engine/classes/AvatarEditorService#PromptCreateOutfit) .

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-editor-service/Avatar-Editor-Save-Outfit.png)

Once called, you can get the result of [AvatarEditorService:PromptCreateOutfit()](/docs/reference/engine/classes/AvatarEditorService#PromptCreateOutfit)  by listening to the [AvatarEditorService.PromptCreateOutfitCompleted](/docs/reference/engine/classes/AvatarEditorService#PromptCreateOutfitCompleted)  event.

The following code sample creates an outfit with [AvatarEditorService:PromptCreateOutfit()](/docs/reference/engine/classes/AvatarEditorService#PromptCreateOutfit)  and listens for a successful [AvatarEditorService.PromptCreateOutfitCompleted](/docs/reference/engine/classes/AvatarEditorService#PromptCreateOutfitCompleted)  event:

```

local AvatarEditorService = game:GetService("AvatarEditorService")

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local character = player.Character or player.CharacterAdded:Wait()

local humanoid = character:WaitForChild("Humanoid")

local currentDescription = humanoid:GetAppliedDescription()

AvatarEditorService:PromptCreateOutfit(currentDescription, humanoid.RigType)

local result = AvatarEditorService.PromptCreateOutfitCompleted:Wait()

if result == Enum.AvatarPromptResult.Success then

  -- Outfit saved!

end

```

## [Purchase items](#purchase-items)[](#purchase-items)

When saving either an avatar or an outfit that uses catalog items, the user doesn't receive any items that they do not own. Before saving an avatar or outfit, check if the user owns the asset with [MarketplaceService:PlayerOwnsAsset()](/docs/reference/engine/classes/MarketplaceService#PlayerOwnsAsset)  and provide them with an option to purchase the item with [MarketplaceService:PromptPurchase()](/docs/reference/engine/classes/MarketplaceService#PromptPurchase) .

If you don't wish to implement item purchases, you can instead allow users to favorite non-owned items with [AvatarEditorService:PromptSetFavorite()](/docs/reference/engine/classes/AvatarEditorService#PromptSetFavorite) .

Be aware that you can't earn Robux [commissions](/docs/marketplace/marketplace-fees-and-commissions#commissions)  if the user decides to purchase those items outside of your game.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
