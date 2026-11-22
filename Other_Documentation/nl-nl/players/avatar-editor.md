<!-- Source: https://create.roblox.com/docs/nl-nl/players/avatar-editor -->

Avatar Editor Service | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Spelers](/docs/nl-nl/players)
6. /
7. UI voor spelers

# Avatar Editor Service

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De Avatar Editor Service stelt je in staat om toegang te krijgen tot en wijzigingen aan te brengen in de avatar van een gebruiker binnen een spel. De Avatar Editor Service kan ook toegang krijgen tot de inventaris van een gebruiker en de [Marketplace](https://www.roblox.com/catalog)  om outfits op te slaan en avatar-items aan het account van de gebruiker aan te schaffen.

We raden aan om de Avatar Editor Service te implementeren met een in-game avatar-editor voor een complete ervaring in karakteraanpassing. Zie de [Simple Avatar Editor Demo](https://www.roblox.com/games/9376329300/Simple-Avatar-Editor-Demo)  referentieplaats voor een voorbeeld van deze functie.

Om te beginnen met het gebruik van de Avatar Editor Service, moet je eerst [toegang aanvragen](#toegang-aanvragen)  tot de inventaris van de gebruiker. Nadat de toegang met succes is verleend, kun je de volgende acties uitvoeren:

-

[Lees de inventaris van de gebruiker](#lees-de-inventaris-van-de-gebruiker)  om een lijst van items te krijgen die de gebruiker bezit.

-

[Zoek in de Marketplace](#zoek-in-de-marketplace) , met behulp van verschillende eigenschappen om te filteren en sorteren.

-

[Equip avatar-items en sla outfits op](#sla-avatars-en-outfits-op)  voor de avatar van de gebruiker.

-

[Vraag de gebruiker om een item aan te schaffen](#items-kopen)  in de Marketplace.

## [Toegang aanvragen](#toegang-aanvragen)[](#toegang-aanvragen)

Om toegang te krijgen tot de inventaris van een gebruiker, moet je de gebruiker vragen om toegang toe te staan via [PromptAllowInventoryReadAccess()](/docs/nl-nl/reference/engine/classes/AvatarEditorService#PromptAllowInventoryReadAccess) . Je moet deze aanvraag eenmaal per sessie uitvoeren.

Gebruik het volgende codevoorbeeld om de toegangsprompt te initiëren en te luisteren naar de reactie van de gebruiker:

```

local AvatarEditorService = game:GetService("AvatarEditorService")

AvatarEditorService:PromptAllowInventoryReadAccess()

local result = AvatarEditorService.PromptAllowInventoryReadAccessCompleted:Wait()

if result == Enum.AvatarPromptResult.Success then

  -- Toegang verleend!

end

```

De gebruiker ontvangt de volgende prompt:

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-editor-service/Avatar-Editor-Access-Items.png)

Zodra de gebruiker de prompt accepteert, kan [AvatarEditorService](/docs/nl-nl/reference/engine/classes/AvatarEditorService)  beginnen met het verkrijgen van toegang tot de inventaris van de gebruiker.

## [Lees de inventaris van de gebruiker](#lees-de-inventaris-van-de-gebruiker)[](#lees-de-inventaris-van-de-gebruiker)

Zodra de toegang door de gebruiker is verleend, kun je hun inventaris lezen met de functie [GetInventory()](/docs/nl-nl/reference/engine/classes/AvatarEditorService#GetInventory) , waarbij je een array van [AvatarAssetTypes](/docs/nl-nl/reference/engine/enums/AvatarAssetType)  opgeeft om op te filteren. Deze functie retourneert een [InventoryPages](/docs/nl-nl/reference/engine/classes/InventoryPages)  object dat de items bevat die de gebruiker bezit.

Gebruik het volgende codevoorbeeld om een lijst van specifieke accessoires in de inventaris van een gebruiker af te drukken:

```

local AvatarEditorService = game:GetService("AvatarEditorService")

AvatarEditorService:PromptAllowInventoryReadAccess()

local result = AvatarEditorService.PromptAllowInventoryReadAccessCompleted:Wait()

if result == Enum.AvatarPromptResult.Success then

  -- Toegang verleend!

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

## [Zoek in de Marketplace](#zoek-in-de-marketplace)[](#zoek-in-de-marketplace)

[AvatarEditorService](/docs/nl-nl/reference/engine/classes/AvatarEditorService)  bevat functies en evenementen waarmee je de Roblox-catalogus kunt doorzoeken. Om te zoeken, geef je je query op met een [CatalogSearchParams](/docs/nl-nl/reference/engine/datatypes/CatalogSearchParams)  object dat een of meer van de volgende eigenschappen bevat:

| Eigenschap | | Beschrijving |
| --- | --- |
| AssetTypes | | Een array van [Enum.AvatarAssetType](/docs/nl-nl/reference/engine/enums/AvatarAssetType)  zoals Enum.AvatarAssetType.BackAccessory. |
| BundleTypes | | Een array van [Enum.BundleType](/docs/nl-nl/reference/engine/enums/BundleType)  zoals Enum.BundleType.BodyParts. |
| CategoryFilter | | Een [Enum.CatalogCategoryFilter](/docs/nl-nl/reference/engine/enums/CatalogCategoryFilter)  die de verschillende cataloguscategorieën beschrijft, zoals "Uitgelicht" of "Community Creations". Standaard is dit ingesteld op [Enum.CatalogCategoryFilter.None](/docs/nl-nl/reference/engine/enums/CatalogCategoryFilter#None) . |
| MaxPrice | | Een geheel getal dat de maximale prijs beschrijft om op te filteren. |
| MinPrice | | Een geheel getal dat de minimale prijs beschrijft om op te filteren. Standaard is MinPrice ** 0** . |
| SearchKeyword | | Een string om te zoeken in de beschrijvingen van items in de catalogus. |
| SortType | | Een [Enum.CatalogSortType](/docs/nl-nl/reference/engine/enums/CatalogSortType)  die beschrijft hoe de resultaten zijn geordend. Standaard is dit ingesteld op [Enum.CatalogSortType.Relevance](/docs/nl-nl/reference/engine/enums/CatalogSortType#Relevance) . |
| IncludeOffSale | | Een boolean die beschrijft of de resultaten van de zoekopdracht off-sale items bevatten. Standaard is dit ingesteld op false. |
| CreatorId | | Een geheel getal om een bepaalde maker op te geven. Je kunt zowel een UserId als een GroupId gebruiken. |
| CreatorName | | Een string die wordt gebruikt om te zoeken naar items die zijn gemaakt door een bepaalde maker. Je kunt zowel een gebruikersnaam als een groepsnaam gebruiken. |

Het volgende codevoorbeeld construeert een [CatalogSearchParams](/docs/nl-nl/reference/engine/datatypes/CatalogSearchParams)  object voor Back  en Shoulder  assettypes, en geeft dat door aan een [SearchCatalog()](/docs/nl-nl/reference/engine/classes/AvatarEditorService#SearchCatalog)  aanroep:

```

local AvatarEditorService = game:GetService("AvatarEditorService")

local catalogSearchParams = CatalogSearchParams.new()

local assetTypes = {

  Enum.AvatarAssetType.BackAccessory,

  Enum.AvatarAssetType.ShoulderAccessory

}

catalogSearchParams.AssetTypes = assetTypes

local pagesObject =

--Deze functie retourneert een CatalogPages object dat de resultaten bevat.

AvatarEditorService:SearchCatalog(catalogSearchParams)

local currentPage = pagesObject:GetCurrentPage()

for _, item in currentPage do

  print(item)

end

```

## [Sla avatars en outfits op](#sla-avatars-en-outfits-op)[](#sla-avatars-en-outfits-op)

Wanneer gebruikt in combinatie met een in-game avatar-editor, kan [AvatarEditorService](/docs/nl-nl/reference/engine/classes/AvatarEditorService)  avatar-items en outfits opslaan en bijwerken op het Roblox-platform. Gebruikers ontvangen geen catalogusitems die ze niet bezitten wanneer ze een avatar of outfit opslaan.

Elke [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  kan worden opgeslagen op de huidige avatar van de gebruiker met [PromptSaveAvatar()](/docs/nl-nl/reference/engine/classes/AvatarEditorService#PromptSaveAvatar) . Dit kan omvatten:

-

Vooraf gedefinieerde avatarconfiguraties die je hebt gemaakt met bestaande catalogusitems.

-

Elke configuratie die de gebruiker heeft gekozen via een in-game avatar-editor.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-editor-service/Avatar-Editor-Equip-Items.png)

Aangezien [AvatarEditorService:PromptSaveAvatar()](/docs/nl-nl/reference/engine/classes/AvatarEditorService#PromptSaveAvatar)  niet yield, kun je het resultaat krijgen door te luisteren naar het [AvatarEditorService.PromptSaveAvatarCompleted](/docs/nl-nl/reference/engine/classes/AvatarEditorService#PromptSaveAvatarCompleted)  evenement.

De volgende code zal een huidige [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  opslaan met [PromptSaveAvatar()](/docs/nl-nl/reference/engine/classes/AvatarEditorService#PromptSaveAvatar)  en controleert op een succesvolle [AvatarEditorService.PromptSaveAvatarCompleted](/docs/nl-nl/reference/engine/classes/AvatarEditorService#PromptSaveAvatarCompleted)  evenement:

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

  -- Avatar opgeslagen!

end

```

Om een [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  als een outfit op te slaan (zonder de huidige avatar van de gebruiker te overschrijven), gebruik je [AvatarEditorService:PromptCreateOutfit()](/docs/nl-nl/reference/engine/classes/AvatarEditorService#PromptCreateOutfit) .

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-editor-service/Avatar-Editor-Save-Outfit.png)

Zodra deze is aangeroepen, kun je het resultaat van [AvatarEditorService:PromptCreateOutfit()](/docs/nl-nl/reference/engine/classes/AvatarEditorService#PromptCreateOutfit)  krijgen door te luisteren naar het [AvatarEditorService.PromptCreateOutfitCompleted](/docs/nl-nl/reference/engine/classes/AvatarEditorService#PromptCreateOutfitCompleted)  evenement.

Het volgende codevoorbeeld maakt een outfit met [AvatarEditorService:PromptCreateOutfit()](/docs/nl-nl/reference/engine/classes/AvatarEditorService#PromptCreateOutfit)  en luistert naar een succesvol [AvatarEditorService.PromptCreateOutfitCompleted](/docs/nl-nl/reference/engine/classes/AvatarEditorService#PromptCreateOutfitCompleted)  evenement:

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

  -- Outfit opgeslagen!

end

```

## [Items kopen](#items-kopen)[](#items-kopen)

Bij het opslaan van een avatar of outfit die gebruikmaakt van catalogusitems, ontvangt de gebruiker geen items die ze niet bezitten. Controleer voordat je een avatar of outfit opslaat of de gebruiker het asset bezit met [MarketplaceService:PlayerOwnsAsset()](/docs/nl-nl/reference/engine/classes/MarketplaceService#PlayerOwnsAsset)  en bied hen de optie om het item aan te schaffen met [MarketplaceService:PromptPurchase()](/docs/nl-nl/reference/engine/classes/MarketplaceService#PromptPurchase) .

Als je geen itemaankopen wilt implementeren, kun je in plaats daarvan gebruikers toestaan om niet-bezitte items als favoriet te markeren met [AvatarEditorService:PromptSetFavorite()](/docs/nl-nl/reference/engine/classes/AvatarEditorService#PromptSetFavorite) .

Houd er rekening mee dat je geen Robux [commissies](/docs/nl-nl/marketplace/marketplace-fees-and-commissions#commissions)  kunt verdienen als de gebruiker besluit die items buiten jouw spel aan te schaffen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
