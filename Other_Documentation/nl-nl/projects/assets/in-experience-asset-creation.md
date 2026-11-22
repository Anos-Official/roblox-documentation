<!-- Source: https://create.roblox.com/docs/nl-nl/projects/assets/in-experience-asset-creation -->

Creatie van in-game assets | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Assets](/docs/nl-nl/assets)

# Creatie van in-game assets

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Met de functie voor het creëren van in-game assets kun je je gebruikers toestaan om creaties die ze in je game hebben gemaakt op te slaan in hun inventarissen. Je gebruikers kunnen deze in-game creaties gebruiken zoals elke andere asset. Bovendien dragen deze creaties bij aan je game wanneer ze op het Roblox-platform worden weergegeven, zodat elke gebruiker de attributielink kan gebruiken om naar je game te komen en hun eigen creaties te maken.

Bijvoorbeeld, je kunt gebruikers in staat stellen om aangepaste wezens als huisdieren in je game te creëren en hen toestaan om hun favoriete huisdieren op te slaan in hun inventarissen. Je hebt volledige controle over welke objecten gebruikers kunnen aanpassen en opslaan vanuit je game. Gebruikers kunnen op hun beurt hun creaties op hun profielen weergeven met attributie naar jouw game, wat de zichtbaarheid van je game vergroot.

## [Ondersteunde assettypes en limieten](#ondersteunde-assettypes-en-limieten)[](#ondersteunde-assettypes-en-limieten)

Net als alle assets op het platform, zijn in-game creaties onderhevig aan [assetmoderatie](/docs/nl-nl/projects/assets#activa-moderatie) . Momenteel kun je gebruikers toestaan om de volgende soorten in-game inhoud te creëren:

-

Afbeeldingen  ([Enum.AssetType.Image](/docs/nl-nl/reference/engine/enums/AssetType#Image) ) van een [EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage)  die je game genereert of bewerkt tijdens runtime.

Het creëren van pakketten ([Enum.AssetType.Model](/docs/nl-nl/reference/engine/enums/AssetType#Model) ) vanuit een [Instance](/docs/nl-nl/reference/engine/classes/Instance)  wordt momenteel niet ondersteund.

Wanneer je je game uitvoert of test en de opslaanactie mislukt, geeft Studio foutmeldingen weer in het [Output-venster](/docs/nl-nl/studio/output)  of de [Developer Console](/docs/nl-nl/studio/developer-console) .

## [In-game platforminhoudcreatie inschakelen](#in-game-platforminhoudcreatie-inschakelen)[](#in-game-platforminhoudcreatie-inschakelen)

Om in-game creatie voor je gebruikers in te schakelen, gebruik je de [AssetService:PromptCreatePlatformContentAsync()](/docs/nl-nl/reference/engine/classes/AssetService#PromptCreatePlatformContentAsync)  API-methode in een server-side script, samen met andere creatielogica. Geef aan welke objecten in je game je deze functionaliteit wilt inschakelen, stel een aangepaste trigger in (zoals een UI-pictogram) voor het aanroepen van de methode, en luister naar client remote events voor het opslaan van assets.

[AssetService:PromptCreatePlatformContentAsync()](/docs/nl-nl/reference/engine/classes/AssetService#PromptCreatePlatformContentAsync)  neemt de volgende parameters:

-

Een [Player](/docs/nl-nl/reference/engine/classes/Player)  object dat de gebruiker vertegenwoordigt die een creatie indient.

-

Een Object , zoals een [EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage) , dat de inhoud voor creatie vertegenwoordigt.

-

Het [Enum.AssetType](/docs/nl-nl/reference/engine/enums/AssetType) , momenteel alleen [Enum.AssetType.Image](/docs/nl-nl/reference/engine/enums/AssetType#Image)  voor een afbeelding.

Wanneer de server [AssetService:PromptCreatePlatformContentAsync()](/docs/nl-nl/reference/engine/classes/AssetService#PromptCreatePlatformContentAsync)  aanroept, verschijnt er een Indienen  dialoogvenster op de client, zodat de gebruiker die de opslaanactie triggert een naam en beschrijving voor de asset kan invoeren. Roblox biedt de dialoog UI standaard aan, aangezien de opslaanworkflow een platformniveau-functionaliteit is.

Voordat je deze methode gebruikt, zorg ervoor dat:

-

Het script dat [AssetService:PromptCreatePlatformContentAsync()](/docs/nl-nl/reference/engine/classes/AssetService#PromptCreatePlatformContentAsync)  aanroept op de server draait.

-

Je plaats is gepubliceerd. Het testen van de prompt in Studio op een niet-gepubliceerde plaats mislukt.

-

Sta Mesh/Afbeelding API's toe  is ingeschakeld voor je ervaring.

[AssetService:PromptCreatePlatformContentAsync()](/docs/nl-nl/reference/engine/classes/AssetService#PromptCreatePlatformContentAsync)  vervangt de oudere [AssetService:PromptCreateAssetAsync()](/docs/nl-nl/reference/engine/classes/AssetService#PromptCreateAssetAsync) , die alleen het creëren van pakketten vanuit een [Instance](/docs/nl-nl/reference/engine/classes/Instance)  ondersteunt. Het creëren van pakketten wordt momenteel niet ondersteund via de nieuwe methode.

### [Maak een afbeelding van een EditableImage](#maak-een-afbeelding-van-een-editableimage)[](#maak-een-afbeelding-van-een-editableimage)

Je kunt gebruikers ook toestaan om afbeeldingen te publiceren die je game genereert tijdens runtime met behulp van [EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage) . Het volgende voorbeeld van een server-side script tekent procedureel een eenvoudig logo in een [EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage)  en vraagt elke speler om het als een afbeeldingsasset te publiceren wanneer ze de game betreden:

Voorbeeldscript voor het maken van een afbeelding

```

local AssetService = game:GetService("AssetService")

local Players = game:GetService("Players")

local BLUE = Color3.fromRGB(49, 86, 255)

local WHITE = Color3.new(1, 1, 1)

local SIZE = 400

local OUTER_SIZE = 200

local INNER_SIZE = 56

local ANGLE = 15 -- graden, met de klok mee

local function generateLogo()

	-- Ongerotate logo: witte vierkant met een blauw vierkant in het midden.

	local logo = AssetService:CreateEditableImage({

		Size = Vector2.new(OUTER_SIZE, OUTER_SIZE),

	})

	-- Eindcanvas: solide blauw.

	local canvas = AssetService:CreateEditableImage({

		Size = Vector2.new(SIZE, SIZE),

	})

	if not logo or not canvas then

		warn("Kon EditableImage niet maken. Zorg ervoor dat toegang tot de Editable Mesh / Image API's is ingeschakeld.")

		return nil

	end

	logo:DrawRectangle(

		Vector2.zero,

		Vector2.new(OUTER_SIZE, OUTER_SIZE),

		WHITE, 0, Enum.ImageCombineType.Overwrite

	)

	logo:DrawRectangle(

		Vector2.new((OUTER_SIZE - INNER_SIZE) / 2, (OUTER_SIZE - INNER_SIZE) / 2),

		Vector2.new(INNER_SIZE, INNER_SIZE),

		BLUE, 0, Enum.ImageCombineType.Overwrite

	)

	canvas:DrawRectangle(

		Vector2.zero,

		Vector2.new(SIZE, SIZE),

		BLUE, 0, Enum.ImageCombineType.Overwrite

	)

	-- Projecteer het logo op het canvas, geroteerd om zijn centrum.

	canvas:DrawImageTransformed(

		Vector2.new(SIZE / 2, SIZE / 2),

		Vector2.one,

		ANGLE,

		logo,

		{

			CombineType = Enum.ImageCombineType.BlendSourceOver,

			ResamplerMode = Enum.ResamplerMode.Default, -- gladde randen

		}

	)

	logo:Destroy()

	return canvas

end

Players.PlayerAdded:Connect(function(player)

	-- CoreGui moet geladen zijn voor de Prompt-methode om te werken.

	player.CharacterAdded:Wait()

	local logo = generateLogo()

	if not logo then

		return

	end

	local complete, result, assetId = pcall(function()

		return AssetService:PromptCreatePlatformContentAsync(player, logo, Enum.AssetType.Image)

	end)

	if complete then

		if result == Enum.PromptCreateAssetResult.Success then

			print("succesvol geüpload, AssetId:", assetId)

		else

			print("Ontvangen resultaat", result)

		end

	else

		print("fout")

		print(result)

	end

end)

```

[In-Experience Creatie Demo Arena](https://www.roblox.com/games/12992503026/In-Experience-Creation-Demo-Arena)  toont een voorbeeld van hoe je deze functie kunt gebruiken. Je kunt de demo joinen om door de in-game creatieworkflow als gebruiker te lopen, of de plaats in Studio bewerken om naar het ontwerp te verwijzen.

## [Post-creatie en attributie](#post-creatie-en-attributie)[](#post-creatie-en-attributie)

Nadat gebruikers een asset hebben gemaakt en opgeslagen vanuit je game, kunnen ze deze vinden op de volgende plaatsen:

-

Hun [Mijn Inventaris](https://en.help.roblox.com/hc/en-us/articles/360000463726-How-to-View-or-Hide-Your-Inventory-in-a-Browser)  pagina.

-

Het Creaties  tabblad van hun [Profiel](https://en.help.roblox.com/hc/en-us/articles/203313660-All-About-Profiles-Blurbs-and-Profile-Customization)  pagina.

-

Het Ontwikkelingsitems  tabblad onder hun Creator Dashboard [Creaties](https://create.roblox.com/dashboard/creations?activeTab=Model)  pagina.

-

Het Inventaris  tabblad van hun [Toolbox](/docs/nl-nl/projects/assets/toolbox)  in Studio.

Wanneer gebruikers in-game creaties zien op de profielen of inventarissen van hun vrienden, zien ze attributie naar de oorspronkelijke game waarin de asset is gemaakt. Gebruikers kunnen op de attributielink klikken om naar de gamepagina te worden omgeleid, zodat ze de game kunnen joinen en hun eigen creaties kunnen maken.

Attributie is momenteel gekoppeld aan een specifieke versie van de gemaakte asset. Als een gebruiker een pakket uit een game opslaat en verder bewerkt in Studio om een nieuwe versie te maken, wordt de attributie niet meer weergegeven voor de nieuwe versie.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
