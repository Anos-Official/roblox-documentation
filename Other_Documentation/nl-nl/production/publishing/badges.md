<!-- Source: https://create.roblox.com/docs/nl-nl/production/publishing/badges -->

Badges | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Ontdekking](/docs/nl-nl/discovery)
6. /
7. Grafiekenpagina

# Badges

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een badge  is een speciale prijs die je aan spelers kunt geven wanneer ze een doel binnen jouw game bereiken, zoals het voltooien van een moeilijke opdracht of het spelen gedurende een bepaalde tijd. Zodra een speler een badge ontvangt, wordt deze weergegeven binnen de Badges -categorie van hun inventaris.

![Voorbeeldbadges in de inventaris van een speler](https://prod.docsiteassets.roblox.com/assets/publishing/badges/Badges-Inventory.png) Voorbeeldbadges in de inventaris van een speler

## [Badges maken](#badges-maken)[](#badges-maken)

Je kunt tot 5 badges gratis maken in een periode van 24 uur (GMT) voor elke game die je bezit. Als je meer badges wilt maken binnen de 24 uur, kost elke extra badge 100 Robux.

Om een badge te maken:

1.

Navigeer naar het [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Beweeg met de muis over de thumbnail van een game, klik op de ⋯ -knop en selecteer Create Badge .

 ![](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Options-Button-Experience-Private.png)

3.

Op de aanmaakpagina klik je op de knop Upload Image  en selecteer/bevestig je de afbeelding die je wilt gebruiken als het pictogram van de badge. Houd bij het maken van een afbeelding voor een badge het volgende in gedachten:

-

Gebruik een sjabloon van 512×512 pixels .

-

Het uploadproces snijdt en crop de badge-afbeelding tot een cirkelvormig pictogram, dus vermijd het plaatsen van belangrijke details buiten de cirkelvormige grenzen.

![Goede cirkelvormige uitsnijding](https://prod.docsiteassets.roblox.com/assets/publishing/badges/Circular-Trimming-Good.png)

Hoofdinhoud inbegrepen

![Slechte cirkelvormige uitsnijding](https://prod.docsiteassets.roblox.com/assets/publishing/badges/Circular-Trimming-Bad.png)

Tekstinhoud bijgesneden

4.

Vul de volgende velden in:

-

Naam  — Een titel voor de badge.

-

Beschrijving  — Een beschrijving van wat de speler moet doen om de badge te verdienen.

-

Badge is ingeschakeld  — Of de badge ingeschakeld zal zijn wanneer deze wordt aangemaakt. Uitgeschakelde badges worden niet weergegeven onder de Badges -sectie van de hoofdpagina van de game en kunnen niet door spelers worden verdiend.

5.

Klik op de knop Create Badge . De nieuwe badge wordt weergegeven binnen de sectie Engagement  ⟩ Badges  op het [Creator Dashboard](https://create.roblox.com/dashboard/creations) . Als de nieuwe badge is ingeschakeld, wordt deze ook weergegeven onder de Badges -sectie van de hoofdpagina van de game.

![](https://prod.docsiteassets.roblox.com/assets/publishing/badges/Badge-Experience-Page.png) Badge op de hoofdpagina van de game

## [Badges herschikken](#badges-herschikken)[](#badges-herschikken)

Wanneer een badge voor het eerst wordt aangemaakt, wordt deze aan het einde van de badge-lijst geplaatst. Je kunt tot 50 badges tegelijk herschikken met behulp van de drag-and-drop-interface.

Om badges te herschikken:

1.

Navigeer naar de bijbehorende game.

2.

In het zijpaneel onder de kop Engagement , navigeer naar de pagina Badges .

3.

Selecteer Reorder  om naar de herschikkingspagina te navigeren.

 ![Badge herschikkingsknop](https://prod.docsiteassets.roblox.com/assets/publishing/badges/Reorder-Button.png)

4.

Op de herschikkingspagina sleep je badges naar de gewenste volgorde.

 ![Badge slepen en neerzetten om te herschikken](https://prod.docsiteassets.roblox.com/assets/publishing/badges/Reordering.png)

5.

Selecteer Opslaan  om deze volgorde op te slaan. De opgegeven volgorde zou nu op de detailpagina van de game moeten verschijnen.

## [Badge-scripts](#badge-scripts)[](#badge-scripts)

Veelvoorkomende badge-scripting workflows omvatten [het toekennen van badges](#badges-toekennen) , controleren of een speler eerder een badge heeft [verdiend](#verdiende-badges-controleren)  in jouw game, en [badge-informatie ophalen](#badge-informatie-ophalen) .

### [Badge-ID's vinden](#badge-ids-vinden)[](#badge-ids-vinden)

De ID van een badge is de unieke identificatie. Je hebt deze ID nodig bij het implementeren van workflows zoals [het toekennen van de badge](#badges-toekennen)  aan een speler.

1.

Ga naar het [Creator Dashboard](https://create.roblox.com/dashboard/creations)  en navigeer naar de sectie Badges  van de bijbehorende game onder Engagement .

2.

Beweeg met de muis over de thumbnail van een badge, klik op de ⋯ -knop en selecteer Copy Asset ID  in het contextmenu.

 ![](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Options-Button-Badge.png)

### [Badges toekennen](#badges-toekennen)[](#badges-toekennen)

Je kunt badges toekennen aan spelers in jouw game door de [BadgeService:AwardBadgeAsync()](/docs/nl-nl/reference/engine/classes/BadgeService#AwardBadgeAsync) -methode aan te roepen in een server-side [Script](/docs/nl-nl/reference/engine/classes/Script) . [BadgeService:GetBadgeInfoAsync()](/docs/nl-nl/reference/engine/classes/BadgeService#GetBadgeInfoAsync)  retourneert eigenschappen van de badge, waaronder IsEnabled , wat bevestigt of de badge aan een speler kan worden toegekend. Je kunt een badge in- of uitschakelen via het formulier Configure Badge  op het [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

Hier is een voorbeeld van een veilige functie voor het toekennen van badges aan spelers.

```

local BadgeService = game:GetService("BadgeService")

local function awardBadge(player, badgeId)

	-- Haal badge-informatie op

	local success, badgeInfo = pcall(function()

		return BadgeService:GetBadgeInfoAsync(badgeId)

	end)

	if success then

		-- Bevestig dat de badge kan worden toegekend

		if badgeInfo.IsEnabled then

			-- Ken badge toe

			local awarded, errorMessage = pcall(BadgeService.AwardBadgeAsync, BadgeService, player.UserId, badgeId)

			if not awarded then

				warn("Fout bij het toekennen van de badge:", errorMessage)

			end

		end

	else

		warn("Fout bij het ophalen van badge-informatie: " .. badgeInfo)

	end

end

```

### [Verdiende badges controleren](#verdiende-badges-controleren)[](#verdiende-badges-controleren)

Het volgende script controleert wanneer een speler de game binnenkomt, en gebruikt vervolgens de [BadgeService:UserHasBadgeAsync()](/docs/nl-nl/reference/engine/classes/BadgeService#UserHasBadgeAsync) -methode om te verifiëren of die speler de badge bezit met de [bijbehorende ID](#badge-ids-vinden)  die is ingesteld in de variabele BADGE_ID . Je kunt ook badge-eigendom in batches verifiëren met de [BadgeService:GetUserBadgesAsync()](/docs/nl-nl/reference/engine/classes/BadgeService#GetUserBadgesAsync) -methode.

```

local BadgeService = game:GetService("BadgeService")

local Players = game:GetService("Players")

local BADGE_ID = 00000000  -- Verander dit in jouw badge-ID

local function onPlayerAdded(player)

  -- Controleer of de speler de badge heeft

	local success, hasBadge = pcall(BadgeService.UserHasBadgeAsync, BadgeService, player.UserId, BADGE_ID)

  -- Als er een fout is, geef een waarschuwing en verlaat de functie

	if not success then

		warn("Fout bij het controleren of de speler de badge heeft")

		return

	end

	if hasBadge then

		-- Behandel het badge-eigendom van de speler zoals nodig

	end

end

-- Verbind "PlayerAdded"-evenementen met de "onPlayerAdded()"-functie

Players.PlayerAdded:Connect(onPlayerAdded)

```

### [Badge-informatie ophalen](#badge-informatie-ophalen)[](#badge-informatie-ophalen)

Om informatie over een badge te krijgen, zoals de beschrijving of het pictogram asset ID, roep je de [BadgeService:GetBadgeInfoAsync()](/docs/nl-nl/reference/engine/classes/BadgeService#GetBadgeInfoAsync) -methode aan met een [badge-ID](#badge-ids-vinden) . Bijvoorbeeld:

```

local BadgeService = game:GetService("BadgeService")

local BADGE_ID = 00000000  -- Verander dit in jouw badge-ID

-- Haal badge-informatie op

local success, result = pcall(BadgeService.GetBadgeInfoAsync, BadgeService, BADGE_ID)

-- Geef de informatie weer

if success then

	print("Badge:", result.Name)

	print("Ingeschakeld:", result.IsEnabled)

	print("Beschrijving:", result.Description)

	print("Pictogram:", "rbxassetid://" .. result.IconImageId)

else

	warn("Fout bij het ophalen van badge-informatie:", result)

end

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
