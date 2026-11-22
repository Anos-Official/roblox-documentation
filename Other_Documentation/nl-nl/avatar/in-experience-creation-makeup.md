<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/in-experience-creation-makeup -->

In-experience creatie voor make-up | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. In-game creation

# In-experience creatie voor make-up

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De volgende gids is van toepassing op makers die bekend zijn met scripting en Roblox Studio en van plan zijn ervaringen te ontwikkelen die gebruikers gegenereerde make-up assets mogelijk maken.

Je kunt een ervaring publiceren die spelers in staat stelt om make-up assets in realtime te creëren, aan te passen en aan te schaffen, naast [in-experience avatar lichaamscreatie](/docs/nl-nl/avatar/in-experience-creation) . Wanneer ze worden aangeschaft, worden make-up assets direct opgeslagen in de Roblox inventaris van de speler.

Ervaringseigenaren die in-experience make-up creatie implementeren, profiteren van [Marketplace commissies](/docs/nl-nl/marketplace/marketplace-fees-and-commissions#commissies)  als de uitgever  van de make-up asset, terwijl de speler die deze creëert de maker  van de asset is.

Make-up assets die in-experience zijn gemaakt, worden niet vermeld op de Marketplace en kunnen niet worden doorverkocht of verhandeld.

Make-up wordt alleen ondersteund op R15-personages met [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  hoofden. Voordat je in-experience make-up creatie implementeert, maak je vertrouwd met [Avatar make-up](/docs/nl-nl/avatar/makeup) , dat het maken van make-up assets in Studio behandelt. Je kunt in-experience make-up creatie testen in de [Avatar Creator](https://www.roblox.com/games/124012682058672/Roblox-Avatar-Creator)  demo van Roblox.

## [Hoe in-experience make-up creatie te implementeren](#hoe-in-experience-make-up-creatie-te-implementeren)[](#hoe-in-experience-make-up-creatie-te-implementeren)

Gebruik de volgende instructies en codeverwijzingen om spelers aan te sporen om make-up assets op het hoofd van hun avatar te schilderen, samen te stellen en aan te schaffen.

Voordat je begint, maak je vertrouwd met het volgende:

-

[Avatar creatietokens](/docs/nl-nl/avatar/in-experience-creation#genereer-een-avatar-creatietoken)  — Ervaringen die make-up creatie implementeren, vereisen ten minste één creatietoken waarvan het creatietype overeenkomt met het type make-up asset dat je van plan bent te creëren.

-

API-klassen

-

[AvatarCreationService](/docs/nl-nl/reference/engine/classes/AvatarCreationService)  — Behandelt het aanmoedigen en valideren van avatar asset creatie.

-

[EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage)  — Behandelt runtime creatie en manipulatie van texturen.

-

[EditableMesh](/docs/nl-nl/reference/engine/classes/EditableMesh)  — Behandelt runtime manipulatie van mesh-geometrie.

-

[WrapDeformer](/docs/nl-nl/reference/engine/classes/WrapDeformer)  — Behandelt runtime manipulatie van onzichtbare buitenste kooi-geometrie die avatar-personages in staat stelt om [3D-kleding en accessoires](/docs/nl-nl/avatar/layered-accessories)  te dragen, inclusief gelaagde wenkbrauw- en wimper-meshes.

-

[WrapTarget](/docs/nl-nl/reference/engine/classes/WrapTarget)  — Vertegenwoordigt de binding tussen een kooi-mesh en een doel-mesh, en stelt textuur-ruimte conversie tussen de twee bloot.

-

[WrapTextureTransfer](/docs/nl-nl/reference/engine/classes/WrapTextureTransfer)  — Faciliteert een decal, inclusief een make-up decal, die rond een ouder-mesh wikkelt op basis van zijn [WrapTarget](/docs/nl-nl/reference/engine/classes/WrapTarget) .

### [Kies een single-asset of multi-asset flow](#kies-een-single-asset-of-multi-asset-flow)[](#kies-een-single-asset-of-multi-asset-flow)

Make-up creatie ondersteunt twee prompts, afhankelijk van of je één make-up asset creëert of verschillende lagen in één outfit samenstelt:

-

[AvatarCreationService:PromptCreateAvatarAssetAsync()](/docs/nl-nl/reference/engine/classes/AvatarCreationService#PromptCreateAvatarAssetAsync)  — Creëert een enkele, individueel gemaakte make-up asset. Geef een van de vijf ondersteunde [Enum.AvatarAssetType](/docs/nl-nl/reference/engine/enums/AvatarAssetType)  waarden door: [FaceMakeup](/docs/nl-nl/reference/engine/enums/AvatarAssetType#FaceMakeup) , [LipMakeup](/docs/nl-nl/reference/engine/enums/AvatarAssetType#LipMakeup) , of [EyeMakeup](/docs/nl-nl/reference/engine/enums/AvatarAssetType#EyeMakeup)  voor een geschilderde textuur, of [EyebrowAccessory](/docs/nl-nl/reference/engine/enums/AvatarAssetType#EyebrowAccessory)  of [EyelashAccessory](/docs/nl-nl/reference/engine/enums/AvatarAssetType#EyelashAccessory)  voor een gelaagde mesh-accessoire. Het creatietype van het token moet overeenkomen met het assetType  dat je doorgeeft.

-

[AvatarCreationService:PromptCreateMakeupAsync()](/docs/nl-nl/reference/engine/classes/AvatarCreationService#PromptCreateMakeupAsync)  — Stelt twee of meer  make-uplaag in een enkele aankoopsoutfit samen. Elke laag levert zijn eigen creatietoken en [Enum.AvatarAssetType](/docs/nl-nl/reference/engine/enums/AvatarAssetType) , plus een sorteervolgorde voor compositie, en de hele outfit deelt één hoofdkleur. Als je alleen één make-up asset hoeft te creëren, gebruik dan in plaats daarvan PromptCreateAvatarAssetAsync()  — PromptCreateMakeupAsync()  vereist ten minste twee invoeren.

PromptCreateMakeupAsync()  neemt een lijst van make-up asset invoeren, waarbij elke invoer omvat:

-

Een creatietoken-ID voor die laag.

-

De instantie waaruit de asset moet worden gemaakt.

-

Het AvatarAssetType  van de laag als een [Enum.AvatarAssetType](/docs/nl-nl/reference/engine/enums/AvatarAssetType) .

-

Een sorteervolgorde die de compositie controleert wanneer meerdere lagen overlappen.

Het retourneert een Enum.PromptCreateMakeupResult  voor de outfit als geheel (Success , PartialSuccess , CreationFailure , PermissionDenied , Timeout , NoUserInput , of UnknownFailure ), plus een per-asset resultaat zodat je kunt zien welke individuele lagen zijn geslaagd wanneer het algehele resultaat PartialSuccess  is.

### [Genereer een avatar creatietoken](#genereer-een-avatar-creatietoken)[](#genereer-een-avatar-creatietoken)

Elke make-up asset type vereist zijn eigen [avatar creatietoken](/docs/nl-nl/production/monetization/avatar-creation-token)  waarvan het creatietype overeenkomt met de [Enum.AvatarAssetType](/docs/nl-nl/reference/engine/enums/AvatarAssetType)  die je doorgeeft aan PromptCreateAvatarAssetAsync() , of overeenkomt met elk type asset van de laag wanneer je PromptCreateMakeupAsync()  gebruikt. Genereer de vereiste tokens voordat je de indieningsinvoeren bouwt, en kopieer vervolgens elke token-ID voor de server-side prompt.

 ![Selecteer Token Type dropdown ingesteld op Eye Makeup, met een contextmenu van een token dat de optie Copy Token ID toont](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-iec-makeup/Avatar-Creation-Token-Type-Makeup.png)

De volgende stappen gebruiken geprojecteerd schilderen op het hoofd van de speler als het belangrijkste pad. Als je in plaats daarvan een auteurshoop of een andere door de ervaring beheerde mesh in zijn eigen UV-ruimte schildert, volg dan [Verplaats een textuur tussen kooi-ruimte en doel-ruimte](#verplaats-een-textuur-tussen-kooi-ruimte-en-doel-ruimte) , en voeg je weer samen met het hoofdpad bij [Maak de decal en dien deze in voor creatie](#maak-de-decal-en-dien-deze-in-voor-creatie) .

### [Schilder een make-up textuur op het hoofd van de speler](#schilder-een-make-up-textuur-op-het-hoofd-van-de-speler)[](#schilder-een-make-up-textuur-op-het-hoofd-van-de-speler)

In tegenstelling tot schilderen op een gloednieuwe asset, kun je over het algemeen geen [EditableMesh](/docs/nl-nl/reference/engine/classes/EditableMesh)  rechtstreeks van het hoofd van de lokale speler lezen om op te schilderen — de hoofdmesh is onderhevig aan hetzelfde toestemmingsmodel als andere door spelers beheerde instanties. De uitzondering is wanneer de ervaring de hoofdmesh bezit (bijvoorbeeld een door de ervaring beheerde NPC of een lichaam dat de ervaring zelf heeft gemaakt); in dat geval kun je [EditableMesh](/docs/nl-nl/reference/engine/classes/EditableMesh)  rechtstreeks gebruiken, op dezelfde manier als je zou doen voor [avatar lichaamscreatie](/docs/nl-nl/avatar/in-experience-creation) . Anders bereid je een [WrapTextureTransfer](/docs/nl-nl/reference/engine/classes/WrapTextureTransfer)  voor en gebruik je deze als het projectiedoel bij het tekenen:

1.

Roep [WrapTextureTransfer:PrepareProjectionMeshDataAsync()](/docs/nl-nl/reference/engine/classes/WrapTextureTransfer#PrepareProjectionMeshDataAsync)  aan om de projectiemeshgegevens voor het hoofd van de speler voor te bereiden en op te slaan. Dit moet zijn voltooid voordat je enige geprojecteerde teken- of monsteroproepen tegen die overdracht maakt. Als de onderliggende hoofdmesh verandert, bereid de [WrapTextureTransfer](/docs/nl-nl/reference/engine/classes/WrapTextureTransfer)  opnieuw voor voordat je verder gaat met schilderen.

2.

Geef de voorbereide [WrapTextureTransfer](/docs/nl-nl/reference/engine/classes/WrapTextureTransfer)  door als de projectiebron aan [DrawImageProjected()](/docs/nl-nl/reference/engine/classes/EditableImage#DrawImageProjected)  of [SampleImageProjected()](/docs/nl-nl/reference/engine/classes/EditableImage#SampleImageProjected) . Deze methoden accepteren een [WrapTextureTransfer](/docs/nl-nl/reference/engine/classes/WrapTextureTransfer)  als alternatief voor een [EditableMesh](/docs/nl-nl/reference/engine/classes/EditableMesh) , zodat je rechtstreeks tegen de werkelijke hoofdvorm van de speler kunt schilderen in plaats van tegen een generieke mesh.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-iec-makeup/Makeup-Texture-Paint-Projection.png)

```

local AssetService = game:GetService("AssetService")

-- Geef een WrapTextureTransfer door die je al hebt gemaakt voor het hoofd van de speler.

local function paintMakeupLayer(textureTransfer: WrapTextureTransfer, brushConfig, projectionParams)

	local success, err = pcall(function()

		textureTransfer:PrepareProjectionMeshDataAsync()

	end)

	if not success then

		warn("Het voorbereiden van de projectiemeshgegevens is mislukt:", err)

		return

	end

	local makeupTexture = AssetService:CreateEditableImage()

	if not makeupTexture then

		warn("Niet genoeg bewerkbare geheugen om een make-up textuur te creëren")

		return

	end

	makeupTexture:DrawImageProjected(textureTransfer, projectionParams, brushConfig)

	return makeupTexture

end

```

### [Verplaats een textuur tussen kooi-ruimte en doel-ruimte](#verplaats-een-textuur-tussen-kooi-ruimte-en-doel-ruimte)[](#verplaats-een-textuur-tussen-kooi-ruimte-en-doel-ruimte)

Direct schilderen op een door de speler beheerd hoofd via een voorbereide [WrapTextureTransfer](/docs/nl-nl/reference/engine/classes/WrapTextureTransfer) , zoals beschreven in [Schilder een make-up textuur op het hoofd van de speler](#schilder-een-make-up-textuur-op-het-hoofd-van-de-speler) , begint niet in de doel UV-ruimte van de hoofdmesh — het projectiepunt werkt de hele tijd in de gedeelde kooi UV-indeling, zodat het resultaat al een kooi-ruimte textuur is die klaar is om in te dienen.

Conversie tussen kooi/doel is in plaats daarvan belangrijk wanneer je werkt met een auteurshoop of een door de ervaring beheerde mesh die je rechtstreeks in zijn eigen native doel UV-ruimte kunt schilderen:

-

[WrapTarget:CreateTextureInTargetSpaceAsync()](/docs/nl-nl/reference/engine/classes/WrapTarget#CreateTextureInTargetSpaceAsync)  — Maakt een herbruikbare kooi-ruimte textuur op die mesh's doel UV-indeling als een [EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage)  die je kunt bewerken.

-

[WrapTarget:CreateTextureInCageSpaceAsync()](/docs/nl-nl/reference/engine/classes/WrapTarget#CreateTextureInCageSpaceAsync)  — Maakt de bewerkte doel-ruimte textuur weer terug op de kooi UV-ruimte als een [EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage)  die je kunt uploaden.

Gebruik CreateTextureInTargetSpaceAsync()  om een herbruikbare kooi-ruimte make-up textuur in die mesh's doelruimte voor bewerking te brengen, en gebruik vervolgens CreateTextureInCageSpaceAsync()  om het bewerkte resultaat terug te converteren naar kooi-ruimte voordat je het indient als een make-up asset.

Voor make-up, beperk de kooi-ruimte conversie tot het make-upgebied in plaats van de hele kooi. Roep [AvatarCreationService:GetValidationRules()](/docs/nl-nl/reference/engine/classes/AvatarCreationService#GetValidationRules)  aan en lees MakeupRules.WrapTextureTransferUVBounds , dat MinBound  en MaxBound  als [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)  waarden biedt. Geef ze door aan CreateTextureInCageSpaceAsync()  als MinUVBounds  en MaxUVBounds . Zonder deze opties, haalt de methode grenzen af van de hele kooi in plaats van het make-upgebied te gebruiken. Elke grens moet eindig zijn, en de maximum moet groter zijn dan de minimum op beide assen.

```

local AvatarCreationService = game:GetService("AvatarCreationService")

local validationRules = AvatarCreationService:GetValidationRules()

local makeupBounds = validationRules.MakeupRules.WrapTextureTransferUVBounds

local cageSpaceTexture = wrapTarget:CreateTextureInCageSpaceAsync(targetSpaceTexture, {

	MinUVBounds = makeupBounds.MinBound,

	MaxUVBounds = makeupBounds.MaxBound,

})

```

### [Maak de decal en dien deze in voor creatie](#maak-de-decal-en-dien-deze-in-voor-creatie)[](#maak-de-decal-en-dien-deze-in-voor-creatie)

Gezicht-, lip- en oogmake-up zijn geschilderde texturen, terwijl wenkbrauwen en wimpers individueel gemaakte gelaagde mesh-accessoires zijn, op dezelfde manier als andere [3D-kleding en accessoires](/docs/nl-nl/avatar/layered-accessories) . Bouw elke laag's indieningsinvoer dienovereenkomstig:

-

Voor een voltooide kooi-ruimte make-up textuur als een [EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage) , wikkel deze in een [Decal](/docs/nl-nl/reference/engine/classes/Decal)  met [AssetService:CreateDecalAsync()](/docs/nl-nl/reference/engine/classes/AssetService#CreateDecalAsync) , en plaats vervolgens de [WrapTextureTransfer](/docs/nl-nl/reference/engine/classes/WrapTextureTransfer)  die je hebt gebruikt om deze te schilderen als de enige kind van die [Decal](/docs/nl-nl/reference/engine/classes/Decal) .

-

Voor een wenkbrauw- of wimperlaag, gebruik je de gemaakte [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  instantie rechtstreeks.

Combineer de resulterende instantie met de bijbehorende token-ID van [Genereer een avatar creatietoken](#genereer-een-avatar-creatietoken) , het assettype en de laagvolgorde. Het volgende voorbeeld neemt die invoeren, van beide soorten, en kiest automatisch de juiste API: [AvatarCreationService:PromptCreateAvatarAssetAsync()](/docs/nl-nl/reference/engine/classes/AvatarCreationService#PromptCreateAvatarAssetAsync)  voor een enkele invoer, of [AvatarCreationService:PromptCreateMakeupAsync()](/docs/nl-nl/reference/engine/classes/AvatarCreationService#PromptCreateMakeupAsync)  wanneer je twee of meer lagen in één outfit samenstelt.

Beide prompts tonen de speler een laatste bevestigingsscherm voordat de asset voor creatie en moderatie wordt ingediend.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-iec-makeup/Makeup-Creation-Publish-Prompt.png)

```

local AssetService = game:GetService("AssetService")

local AvatarCreationService = game:GetService("AvatarCreationService")

type MakeupEntry = {

	tokenId: string,

	instance: Instance,

	assetType: Enum.AvatarAssetType,

	sortOrder: number,

}

-- Gezicht-, lip- en oogmake-up: wikkel de voltooide textuur in een Decal en plaats de

-- WrapTextureTransfer die is gebruikt om deze te schilderen, als het enige kind van de Decal.

local function createMakeupTextureEntry(

	tokenId: string,

	texture: EditableImage,

	textureTransfer: WrapTextureTransfer,

	assetType: Enum.AvatarAssetType,

	sortOrder: number

): MakeupEntry

	local decal = AssetService:CreateDecalAsync({

		TextureContent = Content.fromObject(texture),

	})

	decal.Face = Enum.NormalId.Front

	textureTransfer.Parent = decal

	return {

		tokenId = tokenId,

		instance = decal,

		assetType = assetType,

		sortOrder = sortOrder,

	}

end

-- Wenkbrauwen en wimpers: geef de gemaakte gelaagde mesh Accessory rechtstreeks door.

local function createMakeupAccessoryEntry(

	tokenId: string,

	accessory: Accessory,

	assetType: Enum.AvatarAssetType,

	sortOrder: number

): MakeupEntry

	return {

		tokenId = tokenId,

		instance = accessory,

		assetType = assetType,

		sortOrder = sortOrder,

	}

end

local function submitMakeupEntries(entries: {MakeupEntry}, player: Player, headColor: Color3?)

	local assetEntries = {}

	for _, entry in entries do

		table.insert(assetEntries, {

			TokenId = entry.tokenId,

			Instance = entry.instance,

			AvatarAssetType = entry.assetType,

			SortOrder = entry.sortOrder,

		})

	end

	if #assetEntries == 1 then

		local entry = assetEntries[1]

		local success, result, assetIdOrErrorMessage = pcall(function()

			return AvatarCreationService:PromptCreateAvatarAssetAsync(

				entry.TokenId,

				player,

				entry.Instance,

				entry.AvatarAssetType

			)

		end)

		if success and result == Enum.PromptCreateAssetResult.Success then

			print("Succesvol geüpload met AssetId:", assetIdOrErrorMessage)

		else

			print("Creëren van make-up asset niet succesvol:", assetIdOrErrorMessage)

		end

	else

		local success, result, perAssetResults = pcall(function()

			return AvatarCreationService:PromptCreateMakeupAsync(player, assetEntries, headColor)

		end)

		if success and result == Enum.PromptCreateMakeupResult.Success then

			print("Make-up outfit succesvol gemaakt")

		else

			print("Resultaat van het maken van make-up outfit:", result, perAssetResults)

		end

	end

end

```

## [Beheer moderatie](#beheer-moderatie)[](#beheer-moderatie)

Nadat een make-up asset is gemaakt, gaat deze door moderatie voordat deze veilig kan worden gebruikt in-experience.

-

Luister naar [AvatarAssetModerationCompleted](/docs/nl-nl/reference/engine/classes/AvatarCreationService#AvatarAssetModerationCompleted)  om te weten wanneer een individuele make-up asset die is gemaakt met PromptCreateAvatarAssetAsync()  de moderatie heeft voltooid.

-

Voor een multi-laag outfit die is gemaakt met PromptCreateMakeupAsync() , wordt AvatarAssetModerationCompleted  nog steeds eenmaal geactiveerd voor elke individuele make-up asset in de outfit, en [AvatarOutfitModerationCompleted](/docs/nl-nl/reference/engine/classes/AvatarCreationService#AvatarOutfitModerationCompleted)  wordt bovendien eenmaal geactiveerd voor de outfit als geheel. Luister naar beide: gebruik het per-asset evenement als je het moderatieresultaat van een specifieke laag wilt weten, en het outfit-niveau evenement om te weten wanneer de hele look veilig is om in-experience te gebruiken.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
