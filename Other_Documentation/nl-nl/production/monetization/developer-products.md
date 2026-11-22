<!-- Source: https://create.roblox.com/docs/nl-nl/production/monetization/developer-products -->

Ontwikkelaarsproducten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Verdienen](/docs/nl-nl/production/monetization)

# Ontwikkelaarsproducten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een ontwikkelaarsproduct  is een item of vaardigheid die een gebruiker meer dan eens kan kopen, zoals in-game valuta, munitie of toverdranken.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/developer-products/Buy-Product-Example.jpg)

Voor items of vaardigheden die een gebruiker slechts een keer  zou moeten kopen, zoals een speciaal wapen of een permanente power-up, zie [Passes](/docs/nl-nl/production/monetization/passes) .

## [Maak een ontwikkelaarsproduct aan](#maak-een-ontwikkelaarsproduct-aan)[](#maak-een-ontwikkelaarsproduct-aan)

Voordat je een ontwikkelaarsproduct aanmaakt, zorg ervoor dat je game is [gepubliceerd](/docs/nl-nl/production/publishing/publish-games-and-places)  en toegankelijk is op Roblox.

Om een ontwikkelaarsproduct aan te maken:

1.

Ga naar [Creations](https://create.roblox.com/dashboard/creations)  en selecteer een game.

2.

Ga naar Monetization  ⟩ Developer Products .

3.

Klik op Create developer product .

4.

Upload een afbeelding om weer te geven als het producticoon. Zorg ervoor dat de afbeelding niet groter is dan 512x512 pixels, geen belangrijke details buiten de cirkelvormige grenzen bevat en in .jpg , .png  of .bmp  formaat is.

5.

Voer een naam en een beschrijving voor het product in.

6.

Selecteer een categorie voor het product. De categorie wordt gebruikt om items in je in-game winkel te organiseren.

7.

Stel de productprijs in Robux in. De minimale prijs is 1 Robux en de maximale prijs is 1 miljard Robux.

8.

Klik op Save Changes .

Als je het ontwikkelaarsproduct als een willekeurige beloning wilt gebruiken, bekijk dan het [beleid voor willekeurige virtuele items](/docs/nl-nl/production/monetization/paid-random-items) .

## [Verkrijg de ontwikkelaarsproduct-ID](#verkrijg-de-ontwikkelaarsproduct-id)[](#verkrijg-de-ontwikkelaarsproduct-id)

Om scripting te gebruiken, heb je een ontwikkelaarsproduct-ID nodig. Om de product-ID te verkrijgen:

1.

Ga naar Monetization  ⟩ Developer Products .

2.

Beweeg met de muis over de miniatuur van een product, klik op de ⋯  knop en selecteer Copy Asset ID  uit het contextmenu.

 ![](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Options-Button-Developer-Product.png)

## [Verkoop een ontwikkelaarsproduct](#verkoop-een-ontwikkelaarsproduct)[](#verkoop-een-ontwikkelaarsproduct)

Vanaf 30 mei 2026 worden cross-game ontwikkelaarsproductverkopen uitgeschakeld. Als je game afhankelijk is van cross-game verkoopmechanismen, raden we aan om voor deze datum [Robux-overdrachten](/docs/nl-nl/production/monetization/robux-transfers)  te integreren om onderbrekingen van de service te voorkomen.

Als je [prijsoptimalisatie](/docs/nl-nl/production/monetization/price-optimization)  gebruikt, zorg er dan voor dat het script op de client draait, zodat gebruikers gepersonaliseerde productprijzen zien.

Voordat je ontwikkelaarsproducten verkoopt, zorg ervoor dat je verkoopontvangsten correct verwerkt en gebruikers hun aangekochte producten verleent. Om dit te doen, moet je:

-

Gebruik de [ProcessReceipt](/docs/nl-nl/reference/engine/classes/MarketplaceService#ProcessReceipt)  API om aankoopontvangsten te controleren. ProcessReceipt  leest automatisch en erkent dat een gebruiker een product buiten de game heeft gekocht.

-

Valideer elke ontvangst voor User ID , Developer Product ID  en de status van de ontvangst.

-

Als de ontvangst de status Open  heeft, verleen de gebruiker de ontwikkelaarsitems die ze hebben gekocht.

-

Reageer op de ProcessReceipt  API met een bericht dat de ontvangst erkent en valideert dat de aangekochte items zijn verleend.

Je kunt ontwikkelaarsproducten op twee manieren verkopen:

-

[Binnen je game](#binnen-je-game)

-

[Buiten je game](#buiten-je-game)

### [Binnen je game](#binnen-je-game)[](#binnen-je-game)

Om een ontwikkelaarsproduct binnen een game te implementeren en te verkopen, roep je [MarketplaceService](/docs/nl-nl/reference/engine/classes/MarketplaceService)  functies aan.

Gebruik [GetProductInfo](/docs/nl-nl/reference/engine/classes/MarketplaceService#GetProductInfo)  om informatie over een ontwikkelaarsproduct op te halen, zoals naam en prijs, en om dat product vervolgens aan gebruikers weer te geven. Je kunt het product bijvoorbeeld binnen de marktplaats van je game verkopen. Voor ontwikkelaarsproducten moet de tweede parameter [Enum.InfoType.Product](/docs/nl-nl/reference/engine/enums/InfoType#Product)  zijn.

```

local MarketplaceService = game:GetService("MarketplaceService")

-- Vervang de tijdelijke ID door je ontwikkelaarsproduct-ID

local productId = 000000

local success, productInfo = pcall(function()

	return MarketplaceService:GetProductInfo(productId, Enum.InfoType.Product)

end)

if success and productInfo then

	-- Toon productinformatie

	-- Vervang de printstatements door UI-code om het product weer te geven

  print("Naam ontwikkelaarsproduct: " .. productInfo.Name)

  print("Prijs in Robux: " .. productInfo.PriceInRobux)

  print("Beschrijving: " .. productInfo.Description)

end

```

Gebruik [GetDeveloperProductsAsync](/docs/nl-nl/reference/engine/classes/MarketplaceService#GetDeveloperProductsAsync)  om alle ontwikkelaarsproducten op te halen die aan je game zijn gekoppeld. Deze functie retourneert een [Pages](/docs/nl-nl/reference/engine/classes/Pages)  object dat je kunt inspecteren en filteren om dingen zoals een in-game winkel of productlijst GUI te bouwen.

```

local MarketplaceService = game:GetService("MarketplaceService")

local success, developerProducts = pcall(function()

	return MarketplaceService:GetDeveloperProductsAsync()

end)

if success and developerProducts then

	local firstPage = developerProducts:GetCurrentPage()

	for _, developerProduct in firstPage do

			-- Vervang de printstatement door UI-code om het product weer te geven

			print(field .. ": " .. value)

	end

end

```

Gebruik [PromptProductPurchase](/docs/nl-nl/reference/engine/classes/MarketplaceService#PromptProductPurchase)  om productaankopen binnen je game aan te moedigen. Je kunt deze functie aanroepen wanneer een gebruiker acties uitvoert, zoals het indrukken van een knop of het praten met een verkoper NPC.

```

local MarketplaceService = game:GetService("MarketplaceService")

local Players = game:GetService("Players")

local player = Players.LocalPlayer

-- Vervang de tijdelijke ID door je ontwikkelaarsproduct-ID

local productId = 000000

local function promptProductPurchase()

    local success, errorMessage = pcall(function()

      MarketplaceService:PromptProductPurchase(player, productId)

    end)

    if success then

      print("Aankoopprompt succesvol weergegeven")

		end

end

```

Je kunt ook functies combineren binnen een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript) . Bijvoorbeeld, je kunt een UI-element zoals een knop of een verkoper NPC maken, en vervolgens [GetProductInfo()](/docs/nl-nl/reference/engine/classes/MarketplaceService#GetProductInfo)  gebruiken om een bestaand ontwikkelaarsproduct aan dat element te koppelen, controleren of het product te koop is, en [PromptProductPurchase()](/docs/nl-nl/reference/engine/classes/MarketplaceService#PromptProductPurchase)  gebruiken om een aankoopprompt te geven telkens wanneer de gebruiker erop klikt.

```

local MarketplaceService = game:GetService("MarketplaceService")

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local button = script.Parent

-- Vervang de tijdelijke ID door je ontwikkelaarsproduct-ID

local productId = 000000

	-- Haalt productinformatie op wanneer de gebruiker op de UI-knop klikt

button.MouseButton1Click:Connect(function()

	local success, productInfo = pcall(function()

		return MarketplaceService:GetProductInfo(productId, Enum.InfoType.Product)

	end)

	if success and productInfo then

		-- Controleert of het product te koop is

		if productInfo.IsForSale then

			print("Dit is te koop")

			-- Vraagt om productaankoop

			MarketplaceService:PromptProductPurchase(player, productId)

		else

			-- Meldt dat het product niet te koop is

			print("Dit product is momenteel niet te koop.")

		end

	else

		print("Fout bij het ophalen van productinformatie: " .. tostring(productInfo))

	end

end)

```

### [Buiten je game](#buiten-je-game)[](#buiten-je-game)

Om aankopen van ontwikkelaarsproducten buiten je game mogelijk te maken, moet je werken met de [ProcessReceipt](/docs/nl-nl/reference/engine/classes/MarketplaceService#ProcessReceipt)  API. Nadat een gebruiker een aankoop heeft gedaan in het Store  tabblad van je game-details pagina, moet je ProcessReceipt  gebruiken om hun aankoop te bevestigen en hen hun items te verlenen zodra ze je game betreden.

Gebruik niet  de [PromptProductPurchaseFinished](/docs/nl-nl/reference/engine/classes/MarketplaceService#PromptProductPurchaseFinished)  gebeurtenis om aankopen te verwerken. Je moet in plaats daarvan de ProcessReceipt  callback gebruiken.

Het afvuren van PromptProductPurchaseFinished  betekent niet dat een gebruiker met succes een item heeft gekocht.

#### [Schakel externe verkopen in](#schakel-externe-verkopen-in)[](#schakel-externe-verkopen-in)

Roblox toont je Gedeclareerde  ontwikkelaarsproducten en game-passen buiten je game, inclusief op de Roblox-startpagina, in zoekresultaten en op de pagina na aankoop nadat een speler Robux heeft gekocht. Een speler kan je item kopen en vervolgens je game betreden met het item al verleend.

Om een ontwikkelaarsproduct in aanmerking te laten komen voor externe verkopen:

1.

Ga in de Creator Hub  naar Monetization  ⟩ Shop .

2.

Markeer het ontwikkelaarsproduct als Gedeclareerd .

3.

Bevestig dat je [ProcessReceipt](/docs/nl-nl/reference/engine/classes/MarketplaceService#ProcessReceipt)  correct hebt geïmplementeerd voor het product.

Roblox controleert je [ProcessReceipt](/docs/nl-nl/reference/engine/classes/MarketplaceService#ProcessReceipt)  implementatie continu. Als er een probleem wordt gedetecteerd, stopt het ontwikkelaarsproduct met verschijnen op oppervlakken buiten je game totdat je het probleem oplost.

Game-passen vereisen geen ProcessReceipt  fix, maar ze moeten ook Gedeclareerd  zijn om buiten je game te verschijnen. We raden aan om een aangepast icoon aan elk ontwikkelaarsproduct toe te voegen, zodat spelers het op externe oppervlakken kunnen herkennen; als je er geen toevoegt, toont Roblox een standaardicoon.

Voor meer informatie over de ProcessReceipt  API en de implementatie ervan, zie de [ProcessReceipt](/docs/nl-nl/reference/engine/classes/MarketplaceService#ProcessReceipt)  pagina.

#### [Los een gemarkeerd ontwikkelaarsproduct op](#los-een-gemarkeerd-ontwikkelaarsproduct-op)[](#los-een-gemarkeerd-ontwikkelaarsproduct-op)

Als Roblox een probleem met [ProcessReceipt](/docs/nl-nl/reference/engine/classes/MarketplaceService#ProcessReceipt)  detecteert met een van je Gedeclareerde  ontwikkelaarsproducten, verschijnt er een banner in Creator Hub  ⟩ Monetization  ⟩ Shop  die linkt naar een rapport van de getroffen producten. Als geen van je ontwikkelaarsproducten een fix nodig heeft, verschijnt er geen banner of rapport.

Om een gemarkeerd ontwikkelaarsproduct op te lossen:

1.

Open het rapport vanuit de banner. Het rapport vermeldt elk Gedeclareerd  ontwikkelaarsproduct dat een ProcessReceipt  fix nodig heeft, samen met de productnaam en product-ID.

2.

Open je game in Roblox Studio en los de ProcessReceipt  implementatie voor het gemarkeerde product op.

3.

Publiceer je game.

4.

Selecteer in het rapport de gefixte producten en klik op Markeer als gefixt .

Gefixte producten verlaten het rapport en komen weer in aanmerking om buiten je game te verschijnen.

Een gemarkeerd ontwikkelaarsproduct verliest alleen de geschiktheid om buiten je game te verschijnen. Spelers kunnen het nog steeds kopen via je bestaande in-game aankoopstromen terwijl het gemarkeerd is.

#### [Beperkingen](#beperkingen)[](#beperkingen)

-

Om buiten je game te worden verkocht, moet een ontwikkelaarsproduct Gedeclareerd  zijn en moet [ProcessReceipt](/docs/nl-nl/reference/engine/classes/MarketplaceService#ProcessReceipt)  correct zijn geïmplementeerd.

-

Ongedeclareerde ontwikkelaarsproducten verschijnen nooit in de Shop  of buiten je game.

-

Het verkopen van een ontwikkelaarsproduct buiten je game verandert je standaard inkomsten of aankoopverwerking niet.

#### [Veelgestelde vragen](#veelgestelde-vragen)[](#veelgestelde-vragen)

Waarom zie ik geen banner of rapport in Creator Hub?

Je ziet alleen een banner als Roblox een Gedeclareerd ontwikkelaarsproduct detecteert dat een ProcessReceipt  fix nodig heeft. Als je geen banner ziet, is er geen actie nodig.

Is het ProcessReceipt-rapport van toepassing op game-passen?

Nee. Het ProcessReceipt  rapport is alleen van toepassing op ontwikkelaarsproducten. Zowel Gedeclareerde ontwikkelaarsproducten als game-passen kunnen buiten je game worden weergegeven en verkocht.

Verandert het inschakelen van externe verkopen hoeveel ik verdien?

Nee. Externe verkopen bieden spelers extra plaatsen om je items te vinden en te kopen. Je aankoopverwerking en standaard inkomsten blijven ongewijzigd.

## [Verwerk een aankoop van een ontwikkelaarsproduct](#verwerk-een-aankoop-van-een-ontwikkelaarsproduct)[](#verwerk-een-aankoop-van-een-ontwikkelaarsproduct)

Nadat een gebruiker een ontwikkelaarsproduct heeft gekocht, moet je de transactie verwerken en registreren. Om dit te doen, gebruik je een [Script](/docs/nl-nl/reference/engine/classes/Script)  binnen [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService)  met de ProcessReceipt  functie.

Voor meer informatie over de ProcessReceipt  API en de implementatie ervan, zie de [ProcessReceipt](/docs/nl-nl/reference/engine/classes/MarketplaceService#ProcessReceipt)  pagina.

```

local MarketplaceService = game:GetService("MarketplaceService")

local Players = game:GetService("Players")

local productFunctions = {}

-- Voorbeeld: product-ID 123123 brengt de gebruiker terug naar volledige gezondheid

productFunctions[123123] = function(receipt, player)

	local character = player.Character

	local humanoid = character and character:FindFirstChildWhichIsA("Humanoid")

	if humanoid then

		humanoid.Health = humanoid.MaxHealth

		-- Geeft aan dat de aankoop succesvol was

		return true

	end

end

-- Voorbeeld: product-ID 456456 geeft 100 gouden munten aan de gebruiker

productFunctions[456456] = function(receipt, player)

	local leaderstats = player:FindFirstChild("leaderstats")

	local gold = leaderstats and leaderstats:FindFirstChild("Gold")

	if gold then

		gold.Value += 100

		return true

	end

end

local function processReceipt(receiptInfo)

	local userId = receiptInfo.PlayerId

	local productId = receiptInfo.ProductId

	local player = Players:GetPlayerByUserId(userId)

	if player then

		-- Haalt de handlerfunctie op die is gekoppeld aan de ontwikkelaarsproduct-ID en probeert deze uit te voeren

		local handler = productFunctions[productId]

		local success, result = pcall(handler, receiptInfo, player)

		if success then

			-- De gebruiker heeft zijn items ontvangen

			-- Retourneert "PurchaseGranted" om de transactie te bevestigen

			return Enum.ProductPurchaseDecision.PurchaseGranted

		else

			warn("Fout bij het verwerken van de ontvangst:", receiptInfo, result)

		end

	end

	-- De items van de gebruiker konden niet worden verleend

	-- Retourneert "NotProcessedYet" en probeert het opnieuw de volgende keer dat de gebruiker de game betreedt

	return Enum.ProductPurchaseDecision.NotProcessedYet

end

-- Stelt de callback in

-- Dit kan slechts één keer worden gedaan door één server-side script

MarketplaceService.ProcessReceipt = processReceipt

```

De receiptInfo  tabel die aan de [ProcessReceipt()](/docs/nl-nl/reference/engine/classes/MarketplaceService#ProcessReceipt)  callbackfunctie wordt doorgegeven, bevat gedetailleerde informatie over de aankoop, zoals de ID van het aangekochte product, de gebruiker die de aankoop heeft gedaan en de valuta die ze hebben gebruikt.

receiptInfo  bevat ook het exacte bedrag in Robux dat de gebruiker voor het product heeft betaald, zelfs als je een [prijsoptimalisatietest](/docs/nl-nl/production/monetization/price-optimization)  uitvoert en verschillende gebruikers verschillende prijzen toont.

De functies voor het verwerken van elke product-ID moeten true  retourneren voor de transactie om succesvol te zijn. Als ze dat niet doen, wordt het product niet verleend aan de gebruiker die het heeft gekocht.

Hoewel Roblox zelf de aankoopgeschiedenis van ontwikkelaarsproducten door specifieke gebruikers niet  registreert, kun je verzoeken om [verkoopgegevens te downloaden](/docs/nl-nl/production/analytics/analytics-dashboard#verkoopgegevens) . Als je de aankoopgeschiedenis van specifieke gebruikers wilt bijhouden, is het jouw verantwoordelijkheid om [de gegevens op te slaan](/docs/nl-nl/cloud-services/data-stores) .

## [Personaliseer je in-game winkel](#personaliseer-je-in-game-winkel)[](#personaliseer-je-in-game-winkel)

Je kunt productintelligentie-API's gebruiken om ontwikkelaarsproducten te sorteren en aan gebruikers aan te bevelen. Het personaliseren van je in-game winkel helpt de meest relevante items voor elke gebruiker naar voren te brengen, wat de betrokkenheid en inkomsten verhoogt. Door ontwikkelaarsproducten af te stemmen op gebruikersvoorkeuren, kun je hun ontdekking verbeteren, conversieratio's verhogen en nieuwe monetisatiekansen ontsluiten.

### [Rangschik ontwikkelaarsproducten voor verkoop](#rangschik-ontwikkelaarsproducten-voor-verkoop)[](#rangschik-ontwikkelaarsproducten-voor-verkoop)

[RankProductsAsync](/docs/nl-nl/reference/engine/classes/MarketplaceService#RankProductsAsync)  neemt een lijst van product-ID's en retourneert een gepersonaliseerde geordende lijst van die producten. Je kunt deze methode gebruiken om je gebruikers gepersonaliseerde itemaanbevelingen in je in-game winkel te bieden.

Omdat RankProductsAsync  een strikte snelheidlimiet heeft, moet je aanbevelingen één keer bij het joinen van de game laden in plaats van het herhaaldelijk aan te roepen.

 Voorbeeld: Drie "Krachten" items gerangschikt voor de gebruiker  ![Drie items gerangschikt voor de gebruiker.](https://prod.docsiteassets.roblox.com/assets/monetization/developer-products/RankedItems.png)

```

local MarketplaceService = game:GetService("MarketplaceService")

-- Maak een array van producten die je wilt rangschikken

local productIdentifiers = {

    {InfoType = Enum.InfoType.GamePass, Id = 123},

    {InfoType = Enum.InfoType.Product, Id = 456},

    {InfoType = Enum.InfoType.Product, Id = 789}

}

-- Maak een beschermde aanroep om fouten af te handelen

local success, rankedProducts = pcall(function()

    return MarketplaceService:RankProductsAsync(productIdentifiers)

end)

if not success then

    error("Mislukt om producten te rangschikken")

end

-- Laad de geretourneerde items in de winkel

for i, rankedItem in ipairs(rankedProducts) do

    local productIdentifier = rankedItem.ProductIdentifier

    local productInfo = rankedItem.ProductInfo

    -- ...

    -- Logica om producten aan de winkel toe te voegen

end

```

### [Toon je beste ontwikkelaarsproducten](#toon-je-beste-ontwikkelaarsproducten)[](#toon-je-beste-ontwikkelaarsproducten)

Als je game in de afgelopen 28 dagen geen itemverkopen heeft gehad, retourneert RecommendTopProductsAsync  een lege lijst. Ten minste één aankoop binnen de laatste 28 dagen is vereist voor deze API om aanbevelingen te genereren.

[RecommendTopProductsAsync](/docs/nl-nl/reference/engine/classes/MarketplaceService#RecommendTopProductsAsync)  neemt een array van [InfoType](/docs/nl-nl/reference/engine/enums/InfoType)  waarden en retourneert tot 50 items waarmee een gebruiker het meest waarschijnlijk zal interageren en kopen. Je kunt deze methode gebruiken om een "Top Picks" sectie in je in-game winkel te creëren.

Als er geen aanbevelingen kunnen worden bepaald, retourneert RecommendTopProductsAsync  0 items.

In zeldzame gevallen kunnen oproepen naar het rangschikkingsmodel traag zijn. Om te helpen voorkomen dat gebruikers te lang moeten wachten, raden we aan om task.spawn  te gebruiken om de oproep naar RecommendTopProducts  niet-blokkerend te maken.

 Voorbeeld: Een "Top Picks" tabblad in een in-game winkel  ![Top Picks tabblad van een in-game winkel.](https://prod.docsiteassets.roblox.com/assets/monetization/developer-products/StoreTopPicks.png)

```

local MarketplaceService = game:GetService("MarketplaceService")

-- Maak een array van producttypes die je wilt opnemen in de aanbevelingen -- Dit voorbeeld omvat zowel passes als ontwikkelaarsproducten

local productTypes = {Enum.InfoType.GamePass, Enum.InfoType.Product}

-- Maak een beschermde aanroep om fouten af te handelen

local success, topRankedItems = pcall(function()

    return MarketplaceService:RecommendTopProductsAsync(productTypes)

end)

if not success then

    error("Mislukt om producten te rangschikken")

end

-- Laad de geretourneerde items in de winkel

-- Zorg ervoor dat je alle niet-geschikte items uit topRankedItems filtert, zoals ontwikkelaarsproducten die de gebruiker niet langer kan kopen

for i, rankedItem in ipairs(topRankedItems) do

    local productIdentifier = rankedItem.ProductIdentifier

    local productInfo = rankedItem.ProductInfo

    -- ...

    -- Logica om producten aan de winkel toe te voegen

end

```

## [Analyses van ontwikkelaarsproducten](#analyses-van-ontwikkelaarsproducten)[](#analyses-van-ontwikkelaarsproducten)

Gebruik analyses van ontwikkelaarsproducten om het succes van individuele producten te analyseren, trends te identificeren en potentiële toekomstige inkomsten te voorspellen.

Met analyses kun je:

-

Je beste ontwikkelaarsproducten over een geselecteerde periode bekijken.

-

Tot acht best verkopende items op een tijdreeksdiagram weergeven om de totale verkopen en netto-inkomsten te analyseren.

-

Je catalogus volgen en items sorteren op verkopen en netto-inkomsten.

Om analyses van ontwikkelaarsproducten te openen:

1.

Ga naar [Creations](https://create.roblox.com/dashboard/creations)  en selecteer een game.

2.

Ga naar Monetization  ⟩ Developer Products .

3.

Selecteer het tabblad Analytics .

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/developer-products/developer-products-analytics-2.png)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
