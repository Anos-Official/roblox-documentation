<!-- Source: https://create.roblox.com/docs/nl-nl/production/monetization/passes -->

Toegangspassen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Verdienen](/docs/nl-nl/production/monetization)

# Toegangspassen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Toegangspassen  stellen je in staat om gebruikers een eenmalige Robux-kosten te laten betalen voor toegang tot speciale privileges in je game, zoals toegang tot een beperkt gebied, een in-game avatar-item of een permanente power-up.

Voor items die een speler meerdere keren kan kopen, zoals drankjes, tijdelijke power-ups of in-game valuta, zie [Ontwikkelaarsproducten](/docs/nl-nl/production/monetization/developer-products) .

## [Maak een toegangspas aan](#maak-een-toegangspas-aan)[](#maak-een-toegangspas-aan)

Voordat je een toegangspas aanmaakt, zorg ervoor dat je game is [gepubliceerd](/docs/nl-nl/production/publishing/publish-games-and-places)  en toegankelijk is op Roblox.

Om een toegangspas aan te maken:

1.

Ga naar [Creaties](https://create.roblox.com/dashboard/creations)  en selecteer een game.

2.

Ga naar Monetisatie  ⟩ Toegangspassen .

3.

Klik op Maak toegangspas aan .

4.

Upload een afbeelding om weer te geven als het pictogram van de toegangspas. Zorg ervoor dat de afbeelding niet groter is dan 512x512 pixels, geen belangrijke details buiten de cirkelvormige grenzen bevat en in het formaat .jpg , .png  of .bmp  is.

5.

Voer een naam en een beschrijving voor de toegangspas in.

6.

Selecteer een categorie voor de toegangspas. De categorie wordt gebruikt om items in je in-game winkel te organiseren.

7.

Klik op Maak toegangspas aan .

![Goede cirkelvormige uitsnijding](https://prod.docsiteassets.roblox.com/assets/monetization/passes/Circular-Trimming-Good.png)

Bevat relevante inhoud

![Slechte cirkelvormige uitsnijding](https://prod.docsiteassets.roblox.com/assets/monetization/passes/Circular-Trimming-Bad.png)

Snijdt belangrijke inhoud af

Als je de toegangspas als een willekeurige beloning wilt gebruiken, bekijk dan het [Beleid voor willekeurige virtuele items](/docs/nl-nl/production/monetization/paid-random-items) .

## [Verkrijg de toegangspas-ID](#verkrijg-de-toegangspas-id)[](#verkrijg-de-toegangspas-id)

Om scripting te gebruiken, heb je een toegangspas-ID nodig. Om de toegangspas-ID te verkrijgen:

1.

Ga naar Monetisatie  ⟩ Toegangspassen .

2.

Beweeg met de muis over de miniatuur van een toegangspas, klik op de ⋯  knop en selecteer Kopieer Asset-ID  uit het contextmenu.

 ![](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Options-Button-Pass.png)

## [Verkoop een toegangspas](#verkoop-een-toegangspas)[](#verkoop-een-toegangspas)

Vanaf 30 mei 2026 worden cross-game toegangspasverkopen uitgeschakeld. Als je game afhankelijk is van cross-game verkoopmechanismen, raden we aan om voor deze datum [Robux-overdrachten](/docs/nl-nl/production/monetization/robux-transfers)  te integreren om onderbrekingen van de service te voorkomen.

Als je [prijsoptimalisatie](/docs/nl-nl/production/monetization/price-optimization)  gebruikt, zorg er dan voor dat het script op de client draait, zodat gebruikers gepersonaliseerde toegangspasprijzen zien.

Je kunt toegangspassen op twee manieren verkopen:

-

[Binnen je game](#binnen-je-game)

-

[Buiten je game](#buiten-je-game)

### [Binnen je game](#binnen-je-game)[](#binnen-je-game)

Om een toegangspas binnen een game te implementeren en te verkopen, roep je [MarketplaceService](/docs/nl-nl/reference/engine/classes/MarketplaceService)  functies aan.

Gebruik [GetProductInfo()](/docs/nl-nl/reference/engine/classes/MarketplaceService#GetProductInfo)  om informatie over een toegangspas op te halen, zoals naam en prijs, en om die toegangspas aan gebruikers weer te geven. Je kunt de toegangspas bijvoorbeeld binnen de marktplaats van je game verkopen. Voor toegangspassen moet de tweede parameter [Enum.InfoType.GamePass](/docs/nl-nl/reference/engine/enums/InfoType#GamePass)  zijn.

```

local MarketplaceService = game:GetService("MarketplaceService")

-- Vervang de tijdelijke ID door je toegangspas-ID

local productId = 000000

local success, productInfo = pcall(function()

	return MarketplaceService:GetProductInfo(productId, Enum.InfoType.GamePass)

end)

if success and productInfo then

	-- Controleer of het product te koop is

	if productInfo.IsForSale then

	-- Toon productinformatie

	-- Vervang de print-instructies door UI-code om de toegangspas weer te geven

  	print("Toegangspas Naam: " .. productInfo.Name)

  	print("Prijs in Robux: " .. productInfo.PriceInRobux)

  	print("Beschrijving: " .. productInfo.Description)

	else

		print("Dit product is niet te koop")

	end

end

```

Gebruik [PromptGamePassPurchase()](/docs/nl-nl/reference/engine/classes/MarketplaceService#PromptGamePassPurchase)  om een aankoop van de toegangspas aan te vragen als de gebruiker de toegangspas nog niet in zijn inventaris heeft. Je kunt deze functie aanroepen wanneer een gebruiker acties uitvoert, zoals het indrukken van een knop of het praten met een verkoper NPC.

```

local MarketplaceService = game:GetService("MarketplaceService")

local Players = game:GetService("Players")

-- Vervang de tijdelijke ID door je toegangspas-ID

local passID = 0000000

-- Vraag aankoop van de toegangspas aan

local function promptPurchase()

	local player = Players.LocalPlayer

	local hasPass = false

	local success, message = pcall(function()

		hasPass = MarketplaceService:UserOwnsGamePassAsync(player.UserId, passID)

	end)

	if not success then

		warn("Fout bij het controleren of de speler de toegangspas heeft: " .. tostring(message))

		return

	end

	if hasPass then

		-- Toon een bericht dat de gebruiker al de toegangspas bezit

	else

		-- Vraag aankoop van de toegangspas aan

		MarketplaceService:PromptGamePassPurchase(player, passID)

	end

end

```

Gebruik [PromptGamePassPurchaseFinished](/docs/nl-nl/reference/engine/classes/MarketplaceService#PromptGamePassPurchaseFinished)  om een voltooide toegangspasaanvraag en aankoop te verwerken en de gebruiker de privileges die aan de toegangspas zijn gekoppeld toe te wijzen.

Plaats het script in de [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService)  zodat de server de passprivileges van de gebruiker beheert.

```

local MarketplaceService = game:GetService("MarketplaceService")

-- Vervang de tijdelijke ID door je toegangspas-ID

local passID = 0000000  -- Verander dit in je toegangspas-ID

-- Verwerk een voltooide aanvraag en aankoop

local function onPromptPurchaseFinished(player, purchasedPassID, purchaseSuccess)

	if purchaseSuccess and purchasedPassID == passID then

		print(player.Name .. " heeft de toegangspas met ID " .. passID .. " gekocht")

		-- Ken de gebruiker de mogelijkheid of bonus toe die aan de toegangspas is gerelateerd

	end

end

-- Verbind PromptGamePassPurchaseFinished evenementen met de functie

MarketplaceService.PromptGamePassPurchaseFinished:Connect(onPromptPurchaseFinished)

```

Wanneer een speler een [gratis proefperiode](#gratis-proefperiodes)  start, wordt [PromptGamePassPurchaseFinished](/docs/nl-nl/reference/engine/classes/MarketplaceService#PromptGamePassPurchaseFinished)  ook geactiveerd met purchaseSuccess  ingesteld op true . Voordat je permanente items, valuta of opgeslagen gegevens toekent, bevestig de aankoop met [GetPassOwnershipAsync](/docs/nl-nl/reference/engine/classes/MarketplaceService#GetPassOwnershipAsync) .

Hoewel Roblox zelf de aankoopgeschiedenis van toegangspassen door specifieke gebruikers niet  registreert, kun je verzoeken om [verkoopgegevens te downloaden](/docs/nl-nl/production/analytics/analytics-dashboard#verkoopgegevens) . Als je de aankoopgeschiedenis van gebruikers wilt bijhouden, is het jouw verantwoordelijkheid om [de gegevens op te slaan](/docs/nl-nl/cloud-services/data-stores) .

### [Buiten je game](#buiten-je-game)[](#buiten-je-game)

Roblox toont je Gedeclareerde  toegangspassen buiten je game, inclusief op de Roblox-startpagina, in zoekresultaten en op de pagina na aankoop nadat een speler Robux heeft gekocht. Een speler kan je toegangspas kopen en vervolgens je game betreden met de toegangspas al verleend.

Om een toegangspas in aanmerking te laten komen voor externe verkopen:

1.

Ga in de Creator Hub  naar Monetisatie  ⟩ Winkel .

2.

Markeer de toegangspas als Gedeclareerd .

Toegangspassen vereisen geen [ProcessReceipt](/docs/nl-nl/reference/engine/classes/MarketplaceService#ProcessReceipt)  fix, maar ze moeten Gedeclareerd  zijn om buiten je game te verschijnen. We raden aan om een aangepast pictogram aan elke toegangspas toe te voegen, zodat spelers deze op externe oppervlakken kunnen herkennen; als je er geen toevoegt, toont Roblox een standaardpictogram.

## [Ken passprivileges toe](#ken-passprivileges-toe)[](#ken-passprivileges-toe)

Je moet handmatig passprivileges toekennen aan gebruikers die je toegangspassen kopen. Om dit te doen, gebruik je [PlayerAdded](/docs/nl-nl/reference/engine/classes/Players#PlayerAdded)  wanneer een gebruiker je game betreedt om te controleren of ze de toegangspas al bezitten en om hen de passprivileges toe te kennen.

Tijdens een [gratis proefperiode](#gratis-proefperiodes)  retourneert [UserOwnsGamePassAsync](/docs/nl-nl/reference/engine/classes/MarketplaceService#UserOwnsGamePassAsync)  true . Gebruik die methode voor tijdelijke toegang controles. Voor permanente toekenningen, roep [GetPassOwnershipAsync](/docs/nl-nl/reference/engine/classes/MarketplaceService#GetPassOwnershipAsync)  aan en controleer het Owned  veld.

Plaats het script in de [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService)  zodat de server de passprivileges van de gebruiker beheert.

```

local MarketplaceService = game:GetService("MarketplaceService")

local Players = game:GetService("Players")

-- Vervang de tijdelijke ID door je toegangspas-ID

local passID = 0000000

local function onPlayerAdded(player)

	local hasPass = false

	-- Controleer of de gebruiker de toegangspas al bezit

	local success, message = pcall(function()

		hasPass = MarketplaceService:UserOwnsGamePassAsync(player.UserId, passID)

	end)

	if not success then

		-- Geef een waarschuwing en verlaat de functie

		warn("Fout bij het controleren of de speler de toegangspas heeft: " .. tostring(message))

		return

	end

	if hasPass then

		-- Ken de gebruiker de mogelijkheid of bonus toe die aan de toegangspas is gerelateerd

		print(player.Name .. " bezit de toegangspas met ID " .. passID)

	end

end

-- Verbind PlayerAdded evenementen met de functie

Players.PlayerAdded:Connect(onPlayerAdded)

```

## [Gratis proefperiodes](#gratis-proefperiodes)[](#gratis-proefperiodes)

Gratis proefperiodes  geven spelers de volledige voordelen van een toegangspas voor één game-sessie voordat ze deze kopen. Elke speler kan één gratis proefperiode per toegangspas starten, en er kan slechts één gratis proefperiode tegelijk actief zijn.

Vanaf 2 december 2026 zijn gratis proefperiodes beschikbaar voor spelers voor elke toegangspas die ze ingeschakeld hebben. Nieuwe toegangspassen hebben standaard gratis proefperiodes uitgeschakeld.

Je kunt ook gratis proefperiodes configureren met de [Open Cloud game passes API](/docs/nl-nl/cloud/api/game-passes) .

### [Gratis proefperiodes inschakelen](#gratis-proefperiodes-inschakelen)[](#gratis-proefperiodes-inschakelen)

Om gratis proefperiodes voor een of meer toegangspassen in te schakelen:

1.

Ga naar [Creaties](https://create.roblox.com/dashboard/creations)  en selecteer een game.

2.

Ga naar Monetisatie  ⟩ Winkel  ⟩ Gratis proefperiodes .

3.

Schakel gratis proefperiodes in voor elke toegangspas die je wilt dat spelers uitproberen.

Je kunt ook een toegangspas selecteren vanuit Monetisatie  ⟩ Toegangspassen , de verkoopinstellingen openen en daar gratis proefperiodes inschakelen. Om gratis proefperiodes uit te schakelen, zet je de instelling uit voor elke toegangspas op dezelfde pagina's.

### [Hoe gratis proefperiodes werken](#hoe-gratis-proefperiodes-werken)[](#hoe-gratis-proefperiodes-werken)

Wanneer gratis proefperiodes zijn ingeschakeld voor een toegangspas, zien spelers die deze nog niet bezitten een Probeer  knop in de winkel. Nadat een speler een proefperiode start:

1.

De proefperiode duurt voor één game-sessie.

2.

Een knop in de rechterbovenhoek van het scherm geeft aan dat de proefperiode actief is. Voordat de sessie eindigt, verandert de knop in Kopen  zodat de speler de toegangspas tijdens de proefperiode kan kopen.

3.

Als de speler de toegangspas tijdens de proefperiode koopt, behouden ze deze. Als de sessie eindigt zonder aankoop, wordt de toegang ingetrokken.

Als een sessie onverwacht eindigt vanwege een systeemfout en de speler binnen een uur opnieuw inlogt, gaat de gratis proefperiode door.

Spelers die al een toegangspas bezitten, komen niet in aanmerking voor de gratis proefperiode en zien geen proefaanbieding.

### [Update je code voor gratis proefperiodes](#update-je-code-voor-gratis-proefperiodes)[](#update-je-code-voor-gratis-proefperiodes)

Toegang controles blijven werken tijdens een proefperiode, maar je moet elke code die permanente items, valuta of opgeslagen gegevens toekent bijwerken wanneer het eigendom true  wordt.

| Evenement | | Gedrag | | Aanbevolen actie |
| --- | --- |
| Speler start een proefperiode | | [PromptGamePassPurchaseFinished](/docs/nl-nl/reference/engine/classes/MarketplaceService#PromptGamePassPurchaseFinished)  wordt op de client en server geactiveerd met purchaseSuccess  ingesteld op true | | Roep [GetPassOwnershipAsync](/docs/nl-nl/reference/engine/classes/MarketplaceService#GetPassOwnershipAsync)  aan en bevestig dat Owned  true  is voordat je permanente beloningen toekent |
| Proefperiode is actief | | [UserOwnsGamePassAsync](/docs/nl-nl/reference/engine/classes/MarketplaceService#UserOwnsGamePassAsync)  retourneert true | | Gebruik bestaande tijdelijke toegang controles zoals gebruikelijk |
| Proefperiode eindigt | | Geen evenement wordt geactiveerd. Eigendom controles retourneren false | | Controleer opnieuw het eigendom wanneer toegang belangrijk is in plaats van het eigendom voor de sessie op te slaan |

Gebruik [GetPassOwnershipAsync](/docs/nl-nl/reference/engine/classes/MarketplaceService#GetPassOwnershipAsync)  om een aangekochte toegangspas te onderscheiden van een actieve proefperiode. Aan de client kan de methode alleen de lokale speler opvragen. Aan de server kan het elke speler opvragen.

| Veld | | Beschrijving |
| Owned | | Of de speler de toegangspas heeft gekocht. |
| Active | | Of de speler momenteel toegang heeft via een aankoop of een actieve proefperiode. Komt overeen met [UserOwnsGamePassAsync](/docs/nl-nl/reference/engine/classes/MarketplaceService#UserOwnsGamePassAsync) . |
| StartTime  en EndTime | | Inbegrepen terwijl een proefperiode actief is. |

```

local MarketplaceService = game:GetService("MarketplaceService")

-- Vervang de tijdelijke ID door je toegangspas-ID

local passID = 0000000

local function grantPermanentRewardIfOwned(player)

	local success, ownership = pcall(function()

		return MarketplaceService:GetPassOwnershipAsync(player, passID)

	end)

	if not success then

		warn("Fout bij het controleren van pass eigendom: " .. tostring(ownership))

		return

	end

	-- Ken alleen permanente beloningen toe voor aangekochte toegangspassen, niet voor gratis proefperiodes

	if ownership.Owned then

		-- Ken permanente items, valuta of opgeslagen gegevens hier toe

	elseif ownership.Active then

		-- Speler is in een gratis proefperiode; ken alleen tijdelijke toegang toe

	end

end

MarketplaceService.PromptGamePassPurchaseFinished:Connect(function(player, purchasedPassID, purchaseSuccess)

	if purchaseSuccess and purchasedPassID == passID then

		grantPermanentRewardIfOwned(player)

	end

end)

```

Geef geen eenmalige aankoopbonussen, permanente valuta of gegevensopslagontgrendelingen wanneer een proefperiode begint. Als je pass eigendom voor een hele sessie opslaat, kunnen spelers proefvoordelen behouden nadat de proefperiode eindigt, of de toegang verliezen tot inhoud die afhankelijk was van een verouderde eigendom controle.

In Studio playtests duren gratis proefperiodes één uur, zodat je de start-, actieve en vervaldynamiek kunt testen voordat je publiceert.

### [Veelvoorkomende patronen om bij te werken](#veelvoorkomende-patronen-om-bij-te-werken)[](#veelvoorkomende-patronen-om-bij-te-werken)

De meeste passcode gaat ervan uit dat zodra een speler een toegangspas bezit, ze deze voor altijd bezitten. Een gratis proefperiode geeft de toegangspas voor een beperkte tijd, dus de volgende veelvoorkomende patronen kunnen spelers de voordelen laten behouden nadat de proefperiode eindigt. Een speler in een proefperiode zou precies moeten krijgen wat een koper krijgt, en eigendom kan ook eindigen voor kopers, bijvoorbeeld na een terugbetaling. De oplossing voor al deze patronen is hetzelfde: pas passvoordelen toe vanuit een live eigendom controle, en sla ze niet op.

#### [Eigendom opslaan of cachen](#eigendom-opslaan-of-cachen)[](#eigendom-opslaan-of-cachen)

Het meest voorkomende patroon slaat "bezit toegangspas" op de eerste keer dat [UserOwnsGamePassAsync](/docs/nl-nl/reference/engine/classes/MarketplaceService#UserOwnsGamePassAsync)  true  retourneert, in opgeslagen gegevens of in een tabel voor de sessie, en leest die waarde in plaats van de API opnieuw aan te roepen. Nadat de proefperiode eindigt, blijft de opgeslagen waarde true .

Vermijd: opgeslagen waarde slaat de controle over

```

if data.Passes[passID] or MarketplaceService:UserOwnsGamePassAsync(player.UserId, passID) then

	data.Passes[passID] = true

	grantPassBenefits(player)

end

```

Roep UserOwnsGamePassAsync  elke keer aan wanneer toegang belangrijk is, zoals bij binnenkomst, bij spawnen en wanneer het voordeel wordt gebruikt. Roblox cachet het resultaat intern, dus herhaalde aanroepen zijn goedkoop, en het resultaat verandert in false  wanneer de proefperiode eindigt. Als een aanroep mislukt, ontzeg dan de toegang en probeer het opnieuw bij de volgende controle.

In plaats daarvan: controleer eigendom wanneer toegang belangrijk is

```

local function ownsPass(player)

	local success, hasPass = pcall(function()

		return MarketplaceService:UserOwnsGamePassAsync(player.UserId, passID)

	end)

	return success and hasPass

end

local function onCharacterAdded(player)

	if ownsPass(player) then

		giveTool(player, "Dark Blade")

		setSpeed(player, MAX_SPEED)

	end

end

```

#### [Opslaan wat de toegangspas toekent](#opslaan-wat-de-toegangspas-toekent)[](#opslaan-wat-de-toegangspas-toekent)

Sommige toegangspassen schrijven hun voordeel in opgeslagen gegevens, zoals een item in de inventaris, een maximaal upgrade, een ontgrendeling of valuta. Zelfs met een live controle bij elke binnenkomst, blijft het opgeslagen voordeel bestaan nadat de proefperiode eindigt. Het wissen van een eigendomsvlag helpt niet als het voordeel zelf ergens anders is opgeslagen.

Vermijd: voordeel geschreven naar opgeslagen gegevens

```

if ownsPass(player) then

	data.Inventory["Dark Blade"] = true

	data.Upgrades.Speed = MAX_SPEED

	data.Coins += BONUS_COINS

end

```

Pas het voordeel tijdens runtime toe vanuit ownsPass , zoals in het vorige voorbeeld, zodat het elke sessie opnieuw wordt opgebouwd en eindigt wanneer het eigendom eindigt. Als de toegangspas iets toekent dat spelers behouden en gebruiken, zoals valuta, verkoop het dan als een [ontwikkelaarsproduct](/docs/nl-nl/production/monetization/developer-products)  in plaats daarvan.

Als je game al passvoordelen heeft opgeslagen, stop dan met het opslaan van nieuwe en verwijder alleen items die je hebt geregistreerd als toegekend door de toegangspas, zoals items gemarkeerd met de toegangspas-ID. Verwijder geen item van elke speler die de toegangspas niet bezit, omdat ze het misschien hebben verdiend of verhandeld.

#### [Toekennen vanuit het aankoop signaal](#toekennen-vanuit-het-aankoop-signaal)[](#toekennen-vanuit-het-aankoop-signaal)

[PromptGamePassPurchaseFinished](/docs/nl-nl/reference/engine/classes/MarketplaceService#PromptGamePassPurchaseFinished)  wordt ook geactiveerd met purchaseSuccess  ingesteld op true  wanneer een proefperiode begint. Vanuit dit signaal, pas dezelfde runtime voordelen toe die je toepast bij binnenkomst, en sla niets op.

#### [Giften en ruilen](#giften-en-ruilen)[](#giften-en-ruilen)

Het gedrag van gaven en ruilen voor gratis proefperiodes wordt nog bevestigd.

-

Giften.  Een speler in een proefperiode lijkt een eigenaar, omdat UserOwnsGamePassAsync  true  retourneert. Als je geschenkenstroom een geschenk weigert wanneer de ontvanger de toegangspas al heeft, controleer dan de Owned  van de ontvanger vanuit [GetPassOwnershipAsync](/docs/nl-nl/reference/engine/classes/MarketplaceService#GetPassOwnershipAsync)  in plaats daarvan, zodat een speler in een proefperiode de toegangspas nog steeds als geschenk kan ontvangen.

-

Ruilen.  Een ruil slaat meestal het item op in de inventaris van de andere speler, waar het niet langer afhankelijk is van de toegangspas. Het eigendom van de toegangspas kan op elk moment eindigen, bijvoorbeeld wanneer een proefperiode eindigt, een aankoop wordt terugbetaald, of een speler de toegangspas uit zijn inventaris verwijdert, en het verhandelde item blijft bij het andere account. Als je wilt dat spelers een item verhandelen, verkoop het dan als een [ontwikkelaarsproduct](/docs/nl-nl/production/monetization/developer-products)  in plaats van het via een toegangspas toe te kennen.

#### [Checklist](#checklist)[](#checklist)

Voordat je gratis proefperiodes voor een toegangspas inschakelt, controleer of:

-

Eigendom komt van een UserOwnsGamePassAsync  aanroep elke keer dat toegang belangrijk is, nooit van een opgeslagen of gecachte waarde.

-

Passvoordelen worden runtime toegepast en nooit opgeslagen, zodat ze eindigen wanneer het eigendom eindigt.

-

PromptGamePassPurchaseFinished  dezelfde voordelen toepast als bij binnenkomst.

-

Giftenstromen de Owned  van de ontvanger controleren, en je verkoopt items die spelers kunnen verhandelen als ontwikkelaarsproducten, niet via een toegangspas.

### [Statistieken van gratis proefperiodes](#statistieken-van-gratis-proefperiodes)[](#statistieken-van-gratis-proefperiodes)

Om statistieken van gratis proefperiodes te bekijken:

1.

Ga naar [Creaties](https://create.roblox.com/dashboard/creations)  en selecteer een game.

2.

Ga naar Monetisatie  ⟩ Winkel  ⟩ Gratis proefperiodes .

De pagina toont de inkomsten uit gratis proefperiodes, hoe vaak proefperiodes worden weergegeven en gestart, en hoe vaak ze worden omgezet in een aankoop, zowel in het algemeen als per toegangspas. Aankopen tijdens of na een proefperiode gebruiken je gebruikelijke passinkomsten.

## [Personaliseer je in-game winkel](#personaliseer-je-in-game-winkel)[](#personaliseer-je-in-game-winkel)

Je kunt productintelligentie-API's gebruiken om toegangspassen te sorteren en aan gebruikers aan te bevelen. Het personaliseren van je in-game winkel helpt om de meest relevante items voor elke gebruiker naar voren te brengen, wat de betrokkenheid en inkomsten verhoogt. Door toegangspassen af te stemmen op gebruikersvoorkeuren, kun je hun ontdekking verbeteren, de conversieratio's verhogen en nieuwe monetisatiekansen ontgrendelen.

### [Rangschik toegangspassen voor verkoop](#rangschik-toegangspassen-voor-verkoop)[](#rangschik-toegangspassen-voor-verkoop)

[RankProductsAsync](/docs/nl-nl/reference/engine/classes/MarketplaceService#RankProductsAsync)  neemt een lijst van product-ID's en retourneert een gepersonaliseerde geordende lijst van die producten. Je kunt deze methode gebruiken om je gebruikers gepersonaliseerde itemaanbevelingen in je in-game winkel te bieden.

Omdat RankProductsAsync  een strikte snelheidlimiet heeft, moet je aanbevelingen één keer bij het inloggen van de game laden in plaats van het herhaaldelijk aan te roepen.

 Voorbeeld: Drie "Kracht" items gerangschikt voor de gebruiker  ![Drie items gerangschikt voor de gebruiker.](https://prod.docsiteassets.roblox.com/assets/monetization/developer-products/RankedItems.png)

```

local MarketplaceService = game:GetService("MarketplaceService")

-- Maak de array van producten die je wilt rangschikken

local productIdentifiers = {

    {InfoType = Enum.InfoType.GamePass, Id = 123},

    {InfoType = Enum.InfoType.Product, Id = 456},

    {InfoType = Enum.InfoType.Product, Id = 789}

}

-- Optioneel: Wikkel de aanroep in een asynchrone taak zodat als de aanvraag traag is,

-- het de UI / game niet bevriest

task.spawn(function()

    -- Gebruik een pcall om fouten netjes af te handelen

    local success, result = pcall(function()

        return MarketplaceService:RankProductsAsync(productIdentifiers)

    end)

    if not success then

        -- Als het mislukt, is 'result' het foutbericht.

        warn("Mislukt om producten te rangschikken:", result)

    end

    -- Laad de teruggegeven items in de winkel.

    for i, rankedItem in ipairs(rankedProducts) do

        local productIdentifier = rankedItem.ProductIdentifier

        local productInfo = rankedItem.ProductInfo

        -- ...

        -- Logica om productInfo in de winkel toe te voegen

    end

end)

```

### [Toon je top toegangspassen](#toon-je-top-toegangspassen)[](#toon-je-top-toegangspassen)

Als je game in de afgelopen 28 dagen geen itemverkopen heeft gehad, retourneert RecommendTopProductsAsync  een lege lijst. Ten minste één aankoop binnen de laatste 28 dagen is vereist voor deze API om aanbevelingen te genereren.

[RecommendTopProductsAsync](/docs/nl-nl/reference/engine/classes/MarketplaceService#RecommendTopProductsAsync)  neemt een array van [InfoType](/docs/nl-nl/reference/engine/enums/InfoType)  waarden en retourneert tot 50 items waarmee een gebruiker het meest waarschijnlijk zal interageren en kopen. Je kunt deze methode gebruiken om een "Top Picks" sectie in je in-game winkel te creëren.

Als er geen aanbevelingen kunnen worden bepaald, retourneert RecommendTopProductsAsync  0 items. Alle toegangspassen die de gebruiker al bezit, worden ook niet geretourneerd.

In zeldzame gevallen kunnen aanroepen naar het rangmodel traag zijn. Om te helpen voorkomen dat gebruikers later worden toegevoegd, raden we aan om task.spawn  te gebruiken om de aanroep naar RecommendTopProducts  niet-blokkerend te maken.

 Voorbeeld: Een "Top Picks" tabblad in een in-game winkel  ![Top Picks tabblad van een in-game winkel.](https://prod.docsiteassets.roblox.com/assets/monetization/developer-products/StoreTopPicks.png)

```

local MarketplaceService = game:GetService("MarketplaceService")

-- Maak een array van producttypes om op te nemen. In dit geval zowel toegangspassen als ontwikkelaarsproducten

local productTypes = {Enum.InfoType.GamePass, Enum.InfoType.Product}

-- Optioneel: Wikkel de aanroep in een asynchrone taak zodat als de aanvraag traag is,

-- het de UI / game niet bevriest

task.spawn(function()

    -- Gebruik een pcall om fouten netjes af te handelen

    local success, result = pcall(function()

        return MarketplaceService:RecommendTopProductsAsync(productTypes)

    end)

    if not success then

        -- Als het mislukt, is 'result' het foutbericht.

        warn("Mislukt om producten te rangschikken:", result)

    end

    -- Laad de teruggegeven items in de winkel. Zorg ervoor dat je alle

    -- niet-geschikte items uit topRankedItems filtert, zoals ontwikkelaarsproducten die

    -- de gebruiker niet langer kan kopen

    for i, rankedItem in ipairs(rankedProducts) do

        local productIdentifier = rankedItem.ProductIdentifier

        local productInfo = rankedItem.ProductInfo

        -- ...

        -- Logica om productInfo in de winkel toe te voegen

    end

end)

```

## [Promoot een toegangspas](#promoot-een-toegangspas)[](#promoot-een-toegangspas)

Gepromote toegangspassen worden gratis aan gebruikers gegeven.

Om meer gebruikers te helpen je game te ontdekken, kun je ervoor kiezen om je toegangspassen te laten presenteren op de [Koop Robux](https://www.roblox.com/upgrades/robux)  pagina van Roblox. Je aanmelden om je toegangspassen te promoten kan helpen om de tijd en Robux die gebruikers in je game doorbrengen te verhogen. Er is geen limiet aan het aantal toegangspassen dat je kunt promoten.

Gebruikers krijgen toegangspassen te zien die relevant zijn voor hun speelgeschiedenis en betrokkenheid op het platform. Ze krijgen geen toegangspassen te zien die ze al bezitten.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/passes/PromotedPass.png)

Wanneer gebruikers een in aanmerking komend Robux-pakket kopen, ontvangen ze de gepromote toegangspas en worden ze gevraagd om hun toegangspas te claimen door je game te betreden.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/passes/PromotedPass2.png)

Voor de beste resultaten raden we aan om een unieke toegangspas te creëren die specifiek is voor de Koop Robux  pagina.

Om je aan te melden om een van je toegangspassen te promoten:

1.

Ga naar Monetisatie  ⟩ Toegangspassen .

2.

Selecteer de toegangspas die je wilt promoten.

3.

Selecteer Promoties .

4.

Schakel Dit item opnemen in de bonuspool  in.

5.

Klik op Wijzigingen opslaan . De toegangspas wordt getoond aan relevante gebruikers op de Koop Robux  pagina.

De gepromote toegangspas:

-

Kan niet te koop zijn of te koop zijn. Als ze te koop zijn, moet hun Robux-waarde groter zijn dan 49 Robux en minder dan 801 Robux.

-

Moet een thumbnail bevatten.

-

Mag geen [betaalde willekeurige items](/docs/nl-nl/production/monetization/paid-random-items)  toekennen.

-

Moet voldoen aan de [Gemeenschapsnormen](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards) .

## [Toegangspasanalyses](#toegangspasanalyses)[](#toegangspasanalyses)

Gebruik toegangspasanalyses om het succes van individuele toegangspassen te analyseren, trends te identificeren en potentiële toekomstige inkomsten te voorspellen.

Met analyses kun je:

-

Je top toegangspassen over een geselecteerde periode bekijken.

-

Tot acht best verkopende items op een tijdreeksdiagram tonen om de totale verkopen en netto-inkomsten te analyseren.

-

Je catalogus volgen en items sorteren op verkopen en netto-inkomsten.

-

Bekijken hoeveel toegangspassen door gebruikers zijn verworven via promotie op de Koop Robux  pagina.

-

Bekijken hoeveel gebruikers je game zijn binnengekomen nadat ze de toegangspas via de Koop Robux  pagina hebben verworven.

Om toegangspasanalyses te openen:

1.

Ga naar [Creaties](https://create.roblox.com/dashboard/creations)  en selecteer een game.

2.

Ga naar Monetisatie  ⟩ Toegangspassen .

3.

Selecteer het Analyses  tabblad.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/passes/passes-analytics-2.png)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
