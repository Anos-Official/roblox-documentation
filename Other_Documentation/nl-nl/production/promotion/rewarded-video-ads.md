<!-- Source: https://create.roblox.com/docs/nl-nl/production/promotion/rewarded-video-ads -->

Beloningsvideo-advertenties | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Adverteren](/docs/nl-nl/production/promotion/advertise)

# Beloningsvideo-advertenties

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Met beloningsvideo-advertenties kun je een beloningsmechanisme in je game implementeren om gebruikers te stimuleren om klik-om-te-kijken video-advertenties te bekijken. Een beloningsvideo is een fullscreen-advertentie die tussen de 6 en 30 seconden duurt en die de gebruiker beloont met een item nadat ze deze hebben bekeken.

Beloningsvideo-advertenties stellen je in staat om:

-

Een groter aantal van je gebruikers te monetiseren.

-

Je advertentie-inkomsten per gebruiker te verhogen en vraag van honderden merken aan te trekken.

-

De speeltijd van gebruikers te verbeteren en meer betrokkenheid bij je game te creëren.

Deze pagina behandelt de opzet, implementatie, analyses en geschiktheid. Voor plaatsing, beloningsstrategie en prestatie-tips, zie het [Beloningsvideo-handboek](/docs/nl-nl/production/promotion/rewarded-video-playbook) .

## [Implementeer beloningsvideo-advertenties](#implementeer-beloningsvideo-advertenties)[](#implementeer-beloningsvideo-advertenties)

Beloningen moeten ontwikkelaarsproducten  zijn. Je kunt gebruikers niet belonen met Robux.

Video-advertenties mogen de karakter van de gebruiker tijdens het spelen niet negatief beïnvloeden. Om ervoor te zorgen dat hun karakter niet wordt geschaad, kun je schade pauzeren terwijl een advertentie wordt afgespeeld of alleen advertenties tonen in veilige zones zoals de game-lobby.

Om beloningsvideo-advertenties te implementeren:

1.

Zorg ervoor dat je voldoet aan de [geschiktheidseisen](#geschiktheidseisen) , waaronder 13 jaar of ouder zijn, een ID-geverifieerd Roblox-account hebben en een openbare game met minstens 2.000 unieke bezoekers per maand hebben.

2.

[Schakel beloningsvideo-advertenties in Creator Hub in](#video-advertentie-instelling) .

3.

Kies het item dat je wilt belonen aan gebruikers voor het bekijken van de advertentie. Je kunt een bestaand ontwikkelaarsproduct selecteren of een gloednieuwe maken.

4.

Maak [client-side](#client-side-implementatie)  en [server-side](#server-side-implementatie)  scripts. Het client-side script controleert of er een video-advertentie beschikbaar is om aan de gebruiker te tonen, terwijl het server-side script een ontwikkelaarsproduct omzet in een beloning, de gebruiker de video-advertentie toont en de gebruiker zijn beloning geeft.

Na implementatie kun je [analyses](#analyses)  gebruiken om belangrijke statistieken te begrijpen en je inkomsten uit beloningsvideo-advertenties te optimaliseren.

Inkomsten uit beloningsvideo-advertenties komen van impressies. Je totale inkomsten worden berekend door EPM (inkomsten per 1000 impressies) te vermenigvuldigen met het totale aantal impressies.

### [Video-advertentie-instelling](#video-advertentie-instelling)[](#video-advertentie-instelling)

Om een beloningsvideo-advertentie in je game in te stellen:

1.

Ga naar [Creations](https://create.roblox.com/dashboard/creations)  en selecteer een game.

2.

Ga naar Monetization  ⟩ Ads  ⟩ Settings .

3.

Onder Rewarded Video  ⟩ Serving , zet de Serving enabled  schakelaar aan.  ![](https://prod.docsiteassets.roblox.com/assets/promotion/ads-manager/EnableRewardedVideoAdsCreatorHub.png)

4.

Selecteer de beloning die je aan de gebruiker wilt geven. Als de beloning nog niet bestaat, [maak een nieuw ontwikkelaarsproduct in de Creator Hub](/docs/nl-nl/production/monetization/developer-products#maak-een-ontwikkelaarsproduct-aan) . Dit ontwikkelaarsproduct moet zijn gemaakt voor het specifieke universum waarin de plaats zich bevindt.

5.

Voeg een knop toe die de gebruiker moet indrukken voordat de video-advertentie begint te spelen.

### [Client-side implementatie](#client-side-implementatie)[](#client-side-implementatie)

Om de beloningsvideo-advertentie aan de client-side te implementeren:

1.

Voeg een nieuwe [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  toe aan de knop die je net in je game hebt ingevoegd.

2.

Gebruik [AdService:GetAdAvailabilityNowAsync()](/docs/nl-nl/reference/engine/classes/AdService#GetAdAvailabilityNowAsync)  om te controleren of er een advertentie beschikbaar is voordat je probeert deze te tonen.

Roep [GetAdAvailabilityNowAsync()](/docs/nl-nl/reference/engine/classes/AdService#GetAdAvailabilityNowAsync)  zo dicht mogelijk bij het moment op dat je van plan bent de advertentie te tonen. Als je bijvoorbeeld een "Bekijk video-advertentie om een beloning te krijgen" knop in een winkelmenu hebt, roep het dan alleen op wanneer de gebruiker het winkelmenu opent.

Codevoorbeeld voor beloningsvideo-advertentie (Client)

```

-- Services

local AdService = game:GetService("AdService")

local Players = game:GetService("Players")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- StarterGui ⟩ ScreenGui ⟩ ShopFrame ⟩ RewardedAdButton

local PlayerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

local ScreenGui = PlayerGui:WaitForChild("ScreenGui")

local ShopFrame = ScreenGui:WaitForChild("ShopFrame")

local RewardedAdButton = ShopFrame:WaitForChild("RewardedAdButton")

-- StarterGui ⟩ ScreenGui ⟩ OpenShopButton

local OpenShopButton = ScreenGui:WaitForChild("OpenShopButton")

-- Event om te communiceren tussen clients & server

local RewardedAdEvent = ReplicatedStorage:WaitForChild("RewardedAdEvent")

local INELIGIBLE_RESULTS = {

	Enum.AdAvailabilityResult.PlayerIneligible,

	Enum.AdAvailabilityResult.DeviceIneligible,

	Enum.AdAvailabilityResult.PublisherIneligible,

	Enum.AdAvailabilityResult.ExperienceIneligible,

}

local function isIneligible(result: Enum.AdAvailabilityResult)

	for _, inEligibleResult in ipairs(INELIGIBLE_RESULTS) do

		if result == inEligibleResult then

			return true

		end

	end

	return false

end

function checkForAds()

	local isSuccess, result = pcall(function()

		return AdService:GetAdAvailabilityNowAsync(Enum.AdFormat.RewardedVideo)

	end)

	if isSuccess and result.AdAvailabilityResult == Enum.AdAvailabilityResult.IsAvailable then

		RewardedAdButton.Visible = true

		return

	end

	if isIneligible(result.AdAvailabilityResult) then

		return

	end

end

RewardedAdEvent.OnClientEvent:Connect(function(isSuccess : boolean, result : Enum.ShowAdResult)

	if result == Enum.ShowAdResult.ShowCompleted then

		checkForAds()

	end

end)

OpenShopButton.MouseButton1Click:Connect(function()

	if ShopFrame.Visible then

		ShopFrame.Visible = false

		return

	end

	ShopFrame.Visible = true

	checkForAds()

end)

RewardedAdButton.MouseButton1Click:Connect(function()

	RewardedAdButton.Visible = false

	RewardedAdEvent:FireServer()

end)

```

### [Server-side implementatie](#server-side-implementatie)[](#server-side-implementatie)

Om de beloningsvideo-advertentie aan de server-side te implementeren:

1.

Maak een nieuwe [Script](/docs/nl-nl/reference/engine/classes/Script)  onder ServerScriptService .

2.

Gebruik de [CreateAdRewardFromDevProductId](/docs/nl-nl/reference/engine/classes/AdService#CreateAdRewardFromDevProductId)  methode om de ontwikkelaarsproduct-ID van de beloning door te geven en een AdReward  object te maken.

3.

Gebruik de [ShowRewardedVideoAdAsync](/docs/nl-nl/reference/engine/classes/AdService#ShowRewardedVideoAdAsync)  methode om de video-advertentie aan de gebruiker af te spelen.

-

OPTIONEEL

 Voeg een placementId  toe om individuele [video-advertentieplaatsingen](#plaatsingen)  in je game te volgen.

4.

Gebruik de [ProcessReceipt](/docs/nl-nl/reference/engine/classes/MarketplaceService#ProcessReceipt)  methode om de gebruiker zijn beloning te geven als ze de hele video-advertentie hebben bekeken.

Codevoorbeeld voor beloningsvideo-advertentie (Server)

```

-- Services

local AdService = game:GetService("AdService")

local MarketplaceService = game:GetService("MarketplaceService")

local Players = game:GetService("Players")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local RewardedAdEvent = ReplicatedStorage:WaitForChild("RewardedAdEvent")

-- Geef een ontwikkelaarsproduct-ID voor de video-advertentiebelon

-- Dit ontwikkelaarsproduct moet zijn gemaakt voor het specifieke universum waarin deze plaats zich bevindt

local DEV_PRODUCT_ID = 1919753834

RewardedAdEvent.OnServerEvent:Connect(function(player)

	local isSuccess, result = pcall(function()

		local reward = AdService:CreateAdRewardFromDevProductId(DEV_PRODUCT_ID)

		return AdService:ShowRewardedVideoAdAsync(player, reward)

	end)

	RewardedAdEvent:FireClient(player, isSuccess, result)

end)

MarketplaceService.ProcessReceipt = function(receiptInfo)

	local player = Players:GetPlayerByUserId(receiptInfo.PlayerId)

	if not player then

		return Enum.ProductPurchaseDecision.NotProcessedYet

	end

	if receiptInfo.ProductId == DEV_PRODUCT_ID then

    -- Voeg hier de logica voor het geven van beloningen toe

		return Enum.ProductPurchaseDecision.PurchaseGranted

	end

	return Enum.ProductPurchaseDecision.NotProcessedYet

end

```

## [Join met Beloning](#join-met-beloning)[](#join-met-beloning)

Join met Beloning is in gesloten bèta. Als je geïnteresseerd bent om het uit te proberen, neem dan contact op met [adproductops@roblox.com](/docs/nl-nl/mailto%3Aadproductops%40roblox.com) .

Join met Beloning is een beloningsvideo-plaatsing die op de Ervaringsdetails-pagina van je game wordt weergegeven, voordat een gebruiker zich aansluit. Een gebruiker kan ervoor kiezen om daar een advertentie te bekijken en een beloning te krijgen wanneer ze zich aansluiten. Dit is een aparte plaatsing van de in-ervaring beloningsvideo-stroom die hierboven is beschreven. Je hoeft [AdService](/docs/nl-nl/reference/engine/classes/AdService)  niet aan te roepen om de advertentie te tonen, omdat je de plaatsing in Creator Hub instelt.

Elke beloning is een [ontwikkelaarsproduct](/docs/nl-nl/production/monetization/developer-products) . Wanneer een gebruiker een beloning verdient, maakt Roblox een ontvangstbewijs voor dat ontwikkelaarsproduct, en de [ProcessReceipt](/docs/nl-nl/reference/engine/classes/MarketplaceService#ProcessReceipt)  callback van je game geeft het wanneer de gebruiker zich aansluit. Als de ProcessReceipt  callback van je game nog niet een ontwikkelaarsproduct geeft dat je als beloning wilt gebruiken, moet je code hiervoor toevoegen voordat je de beloning publiceert.

### [Stel een Join met Beloning-plaatsing in](#stel-een-join-met-beloning-plaatsing-in)[](#stel-een-join-met-beloning-plaatsing-in)

1.

Ga in het Creator Dashboard naar Creations  en selecteer een game.

2.

Ga naar Monetization  ⟩ Ads  ⟩ Placements .

3.

Klik op Create placement  en selecteer Join met Beloning .

4.

Tijdens de stap Plaatsing instellen , geef de plaatsing een naam en voeg een of meer beloningsitems toe. Elk beloningsitem is een ontwikkelaarsproduct met een afbeelding. Je kunt hetzelfde ontwikkelaarsproduct niet meer dan eens aan een plaatsing toevoegen.

5.

Klik op Doorgaan . De volgende stap toont een ProcessReceipt  codefragment met de ID's van de ontwikkelaarsproducten van je beloningsitems. Als je game deze producten nog niet geeft, kopieer dan het fragment in je server-side ProcessReceipt  code, en vervang de placeholder-opmerking door de code die de gebruiker elke beloning geeft.

6.

Klik op Creëren .

### [Test beloningen](#test-beloningen)[](#test-beloningen)

Nieuwe beloningen starten in testmodus, zodat je kunt controleren of elke beloning correct wordt gegeven voordat elke gebruiker deze kan zien.

Join met Beloning wordt alleen ondersteund op mobiele apparaten. Om een beloning te testen, open je de Ervaringsdetails-pagina van de game op een mobiel apparaat.

-

Wie kan een beloning in testmodus zien:  alleen gebruikers met bewerkingsrechten voor de game. Zij zien de optie Join met Beloning op de Ervaringsdetails-pagina van de game. Andere gebruikers zien geen beloningen die in testmodus zijn.

-

Één beloning tegelijk:  slechts één beloning op een plaatsing kan in testmodus zijn. Wanneer je een plaatsing maakt, begint het eerste beloningsitem in testmodus, en blijven de andere beloningsitems in concept totdat het hun beurt is.

Om een beloning te testen en deze uit de testmodus te verplaatsen:

1.

Meld je aan op een mobiel apparaat met een account dat bewerkingsrechten voor de game heeft, en open de Ervaringsdetails-pagina van de game.

2.

Bekijk de advertentie en sluit je aan bij de game. Controleer of je de beloning krijgt.

3.

Open in Creator Hub de beloningsitems van de plaatsing en klik op Publiceren  op de beloning. De beloning wordt actief, en alle in aanmerking komende gebruikers kunnen deze nu krijgen.

Nadat je een beloning hebt gepubliceerd, gaat de volgende conceptbeloning op de plaatsing automatisch in testmodus. Herhaal deze stappen voor elke beloning. Je kunt een beloning niet publiceren terwijl de afbeelding ervan nog in behandeling is.

### [Beheer beloningsitems](#beheer-beloningsitems)[](#beheer-beloningsitems)

Elk beloningsitem heeft een status, zoals concept, testmodus, actief of inactief. Gebruik de beloningsitems-lade op de plaatsing om:

-

Een beloning in of uit te schakelen. Een inactieve beloning inschakelen maakt deze actief voor alle gebruikers.

-

Klik op Test  op een conceptbeloning om deze in testmodus te verplaatsen. Als een andere beloning al in testmodus is, gaat die beloning terug naar concept.

-

Selecteer Testmodus inschakelen  in het menu van een beloning om een actieve of inactieve beloning terug in testmodus te verplaatsen.

Wanneer een plaatsing meer dan één actieve beloning heeft, kiest Roblox er elke keer dat de advertentie wordt weergegeven willekeurig één van. Beloningen in testmodus worden alleen getoond aan gebruikers met bewerkingsrechten voor de game.

### [Bekijk de prestaties van Join met Beloning](#bekijk-de-prestaties-van-join-met-beloning)[](#bekijk-de-prestaties-van-join-met-beloning)

Join met Beloning heeft zijn eigen rapportage, apart van je in-ervaring beloningsvideo-advertenties. Om het te bekijken:

1.

Ga in het Creator Dashboard naar Creations  en selecteer een game.

2.

Ga naar Monetization  ⟩ Ads  ⟩ Analytics .

3.

Filter op Beloningsvideo , en selecteer vervolgens Join met Beloning  als het type beloningsvideo.

Dit overzicht bevat alleen je Join met Beloning-plaatsingen, en het is alleen beschikbaar nadat je game ten minste één Join met Beloning-plaatsing heeft. Het toont:

-

Samenvattende totalen voor Inkomsten , Impressies  en EPM .

-

Grafieken van inkomsten en impressies in de loop van de tijd.

-

Een CTR  (click-through rate) grafiek, met een schaduwband die het verwachte CTR-bereik toont.

## [Plaatsingen](#plaatsingen)[](#plaatsingen)

Gebruik plaatsingen om de prestaties van individuele beloningsvideo-advertenties in je game te volgen.

Om een beloningsvideo-advertentieplaatsing te maken:

1.

Ga in het Creator Dashboard naar Creations  en selecteer een game.

2.

Ga naar Monetization  ⟩ Ads  ⟩ Placements .

3.

Klik op Create placement .

4.

Voer een naam in voor de plaatsing en klik op Create .

De nieuwe plaatsing wordt weergegeven in de Plaatsingstabel met een unieke Plaatsings-ID . Je kunt deze Plaatsings-ID gebruiken in de [ShowRewardedVideoAdAsync](/docs/nl-nl/reference/engine/classes/AdService#ShowRewardedVideoAsync)  methode om de individuele video-advertenties in je game te onderscheiden en statistieken bij te houden.

## [Advertentiekansen](#advertentiekansen)[](#advertentiekansen)

Gebruik [RegisterAdOpportunityAsync](/docs/nl-nl/reference/engine/classes/AdService#RegisterAdOpportunityAsync)  om bij te houden hoe vaak een gebruiker de kans heeft om een beloningsvideo-advertentie te bekijken, en de snelheid waarmee ze daadwerkelijk de video-advertentie bekijken.

Je kunt een Plaatsings-ID als optionele parameter opgeven om statistieken voor individuele advertentiekansen in je game bij te houden.

Codevoorbeeld voor het bijhouden van advertentiekansen

```

local AdService = game:GetService("AdService")

local playerGui = game:GetService("Players").LocalPlayer:WaitForChild("PlayerGui")

-- Maak de ScreenGui en de Knop

local screenGui = Instance.new("ScreenGui", playerGui)

local adButton = Instance.new("TextButton", screenGui)

-- Registreer de knop bij AdService

local success, err = pcall(function()

	-- De tweede parameter is een optionele Plaatsings-ID (Nummer) parameter die in de Creator Hub is gegenereerd.

	-- Als je ervoor kiest om geen Plaatsings-ID op te geven, wordt de advertentiekans onder de standaardplaatsing bijgehouden.

	AdService:RegisterAdOpportunityAsync(adButton, 1234567891234567)

end)

if not success then

	warn("Registreren van advertentiekans mislukt:", err)

end

```

## [Excludeer waarschijnlijke uitgaven](#excludeer-waarschijnlijke-uitgaven)[](#excludeer-waarschijnlijke-uitgaven)

Op basis van eerder gedrag en aankoopgewoonten zijn bepaalde gebruikers waarschijnlijker om aankopen in je game te doen. Om je risico op het verliezen van inkomsten te verminderen, kun je gebruikers die waarschijnlijk in je game zullen uitgeven uitsluiten van het zien van beloningsvideo-advertenties.

We raden aan om deze instelling alleen in te schakelen als je van plan bent om gebruikers de keuze te geven tussen het bekijken van een video-advertentie en het kopen van de beloning uit die advertentie. Als de beloning die je aanbiedt via de video-advertentie uniek is en niet beschikbaar is voor aankoop, raden we aan om deze instelling niet in te schakelen.

Om te voorkomen dat waarschijnlijke uitgaven beloningsvideo-advertenties zien:

1.

Ga in het Creator Dashboard naar Creations  en selecteer een game.

2.

Ga naar Monetization  ⟩ Ads  ⟩ Settings .

3.

Zet de schakelaar Sluit je meest waarschijnlijke kopers uit van Beloningsvideo-advertenties  aan.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/rewarded-video-ads/LikelySpenders.png)

## [Schat potentiële inkomsten](#schat-potentiële-inkomsten)[](#schat-potentiële-inkomsten)

Gebruik de calculator om je inkomsten te schatten voordat je beloningsvideo-advertenties in je game implementeert.

Potentiële inkomsten worden berekend door het aantal advertenties-geschikte gebruikers die je game in de afgelopen 7 dagen hebben bezocht, het aantal advertenties dat je per gebruiker zou kunnen tonen, en je verwachte EPM (inkomsten per 1000 impressies) te vermenigvuldigen.

Omdat het aantal dagelijkse advertentieweergaven per gebruiker de belangrijkste variabele is die je kunt beheersen wanneer je beloningsvideo-advertenties in je game implementeert, moet je een gebruikerservaring ontwerpen die gebruikers van nature aanmoedigt om advertenties te bekijken. Als je bijvoorbeeld wilt dat de meeste gebruikers minstens één advertentie per dag bekijken, maak je advertentieplaatsingen toegankelijk en gemakkelijk te vinden. Je kunt ook dagelijkse weergaven verhogen door beloningen aan te bieden die waardevol aanvoelen en aansluiten bij je kern gameplay-loop, waardoor gebruikers betrokken blijven en je totale advertentie-impressies worden verhoogd.

Om de calculator te gebruiken:

1.

Ga in het Creator Dashboard naar Creations  en selecteer een game.

2.

Ga naar Monetization  ⟩ Ads  ⟩ Eligibility .

3.

Onder Advertentieformaat , selecteer Beloningsvideo .

4.

Pas de schuifregelaar dagelijkse advertentieweergaven per gebruiker  aan om het nummer Wekelijkse potentiële beloningsvideo-advertentie-inkomsten  bij te werken en potentiële inkomsten te zien.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/rewarded-video-ads/OpportunityCalculator.png)

## [Analyses](#analyses)[](#analyses)

Gebruik analysemethoden om de effectiviteit van je beloningsvideo-advertenties te evalueren, test verschillende beloningstypes om de types te identificeren die het beste resoneren met je publiek, en meet hoe vaak gebruikers volledige video-advertenties bekijken om beloningen te claimen.

Om toegang te krijgen tot je beloningsvideo-advertentie-statistieken:

1.

Ga in het Creator Dashboard naar Creations  en selecteer een game.

2.

Ga naar Monetization  ⟩ Ads  ⟩ Analytics .

3.

Filter op Beloningsvideo  om alle beschikbare statistieken te zien.

| Statistiek | | Beschrijving |
| --- | --- |
| Inkomsten (Robux) | | Totaal bedrag aan inkomsten in Robux verdiend uit beloningsvideo-advertenties in je game.
 Verschillende lijnen tonen je deze statistiek voor verschillende advertentieplaatsingen in de game. |
| Monetization Funnel op Ervaringsniveau | | Deze statistiek toont je:

-

Aangevraagd : Het aantal advertenties aangevraagd door advertenties-geschikte gebruikers in je game.

-

Vervuld : Het aantal advertenties ontvangen door advertenties-geschikte gebruikers in je game.

-

Advertentiekansen : Het aantal kansen dat gebruikers hadden om een video-advertentie te bekijken.

-

Impressies : Het aantal impressies van de video-advertenties in je game. Het eerste frame van een video-advertentie dat aan een gebruiker wordt getoond, telt als een impressie.

-

Beloond : Het aantal video-advertentiebeloond dat aan gebruikers is gegeven.

  |
| Vulpercentage | | Het percentage van aanvragen waarvoor een advertentie als reactie is teruggegeven. |
| EPM (Inkomsten per Mille) | | Je effectieve Robux-inkomsten per duizend impressies. Berekend door totale inkomsten / het aantal impressies (in duizenden) in je game.
 Verschillende lijnen tonen je deze statistiek voor verschillende advertentieplaatsingen in de game. |
| Advertentiekansen | | Het aantal kansen dat gebruikers hadden om een video-advertentie te bekijken. Gebruik deze statistiek om bij te houden hoe vaak een gebruiker de kans had om een video-advertentie te bekijken en de snelheid waarmee ze daadwerkelijk die kans hebben genomen en de advertentie hebben bekeken.
 Verschillende lijnen tonen je deze statistiek voor verschillende advertentieplaatsingen in de game. |
| Impressies | | Het aantal beloningsvideo-advertenties dat in je game is getoond.
 Verschillende lijnen tonen je deze statistiek voor verschillende advertentieplaatsingen in de game. |
| Beloond | | Het aantal beloningen dat is gegeven voor het bekijken van video-advertenties in je game.
 Verschillende lijnen tonen je deze statistiek voor verschillende advertentieplaatsingen in de game. |
| DUV (Dagelijkse Unieke Kijkers) | | Het aantal unieke gebruikers die in een dag één of meer video-advertenties in je game hebben bekeken. Een weergave wordt gedefinieerd door een impressie.
 Deze gegevens worden met een vertraging van 1 dag bijgewerkt. |
| AEPDUV (Gemiddelde Inkomsten Per Dagelijkse Unieke Kijker) | | De inkomsten gegenereerd per dagelijkse unieke kijker voor beloningsvideo-advertenties.
 Deze gegevens worden met een vertraging van 1 dag bijgewerkt. |
| In aanmerking komende Dagelijkse Actieve Gebruiker | | Het aantal unieke dagelijkse gebruikers van je game die in aanmerking kwamen om beloningsvideo-advertenties te bekijken.
 Deze gegevens worden met een vertraging van 1 dag bijgewerkt. |
| DUV/eDAU | | Het percentage van advertenties-geschikte gebruikers die je game hebben bezocht en in een dag één of meer video-advertenties hebben bekeken. |
| Opt-In Percentage | | Het percentage van advertenties-geschikte gebruikers die betrokken zijn bij advertenties in je game. |
| Frequentie | | Het aantal advertenties dat een gebruiker per dag in je game ziet. |

## [Verminder risico's van je implementatie met experimenten](#verminder-risicos-van-je-implementatie-met-experimenten)[](#verminder-risicos-van-je-implementatie-met-experimenten)

Als je niet zeker weet hoe je community zal reageren op een nieuwe beloningsvideo-advertentieplaatsing, kun je [experimenten](/docs/nl-nl/production/experiments)  gebruiken om de plaatsing eerst uit te rollen naar een percentage van je gebruikers. Dit stelt je in staat om realtime veranderingen in betrokkenheid en retentie te meten voordat je de plaatsing aan je hele publiek uitrolt. Om advertentie-impressies, opt-in percentage en advertentie-inkomsten naast je andere statistieken bij te houden, kies je de [Beloningsvideo-inkomsten statistiekenset](/docs/nl-nl/production/experiments#metrics-voor-beloofde-video)  wanneer je het experiment maakt.

## [Geschiktheidseisen](#geschiktheidseisen)[](#geschiktheidseisen)

Om misbruik van het beloningsadvertentiesysteem te voorkomen en de best mogelijke gebruikerservaring te bieden, moet je de geschiktheidseisen volgen wanneer je beloningsvideo-advertenties implementeert.

| Games | | Games moeten:
-

Openbaar en onbeperkt zijn.

-

Geen vrije gebruikerscreatie, sterke taal, romantiek of sociale hangouts met privéruimtes aanbieden.

-

Een complete Maturity and Compliance Questionnaire  of Content Rating Questionnaire  hebben die is beoordeeld en goedgekeurd door Roblox. Als de beoordelingsstatus In afwachting  is, kun je een herbeoordeling aanvragen vanaf de advertentiegeschiktheidspagina van de game onder Monetization  ⟩ Ads  ⟩ Eligibility . Je ontvangt binnen 24 uur een reactie.

-

Gemiddeld minstens 2.000 unieke bezoekers per maand  hebben.

-

Voldoen aan de [Roblox gebruiksvoorwaarden](https://en.help.roblox.com/hc/en-us/articles/115004647846-Roblox-Terms-of-Use) , [gemeenschapsnormen](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards)  en [uitgever integriteitsvereisten](https://en.help.roblox.com/hc/en-us/articles/13722260778260-Advertising-Standards#publisher-integrity) .

 |
| Uitgevers | | Als uitgever moet je:
-

13 jaar of ouder zijn.

-

Een account hebben dat in goede staat is bij Roblox.

-

Tweefactorauthenticatie (2FA) hebben ingeschakeld en [je ID](/docs/nl-nl/production/publishing/account-verification#verifi%C3%ABren-via-overheidsidentificatie)  op je account hebben geverifieerd.

-

Een duidelijke actie implementeren die de gebruiker moet ondernemen voordat de video-advertentie voor hen wordt afgespeeld. Bijvoorbeeld, een knop die de gebruiker moet klikken.

-

Duidelijke en nauwkeurige openbaarmakingen geven voorafgaand aan elke trigger van de video, inclusief wat de beloning is en wat de gebruiker moet doen om deze te verdienen. Deze openbaarmakingen moeten ondubbelzinnig zijn voor de gebruiker. Bijvoorbeeld, je kunt tekst toevoegen die zegt “Bekijk de advertentie om 10 diamanten te verdienen!” aan de knop voor het afspelen van de video-advertentie.

-

De beloning onmiddellijk aan de gebruiker geven nadat de beloningsvideo-advertentie is afgelopen.

-

De gebruiker niet dwingen om de video-advertentie te starten als een voortgangsbelemmering in de game.

-

De zichtbaarheid van het scherm van de gebruiker niet overnemen of hun avatarbeweging verdoezelen.

-

Geen frauduleuze beloningen promoten of implementeren, inclusief gratis Robux of geld, om de gebruiker misleidend te stimuleren om de video-advertentie tot het einde te bekijken. Dit omvat ook het gebruik van onnauwkeurige beloningsbeschrijvingen of het implementeren van mechanismen die de beloning die aan de gebruiker is beloofd niet vervullen.

 |
| Beloningen | | De beloning voor het bekijken van een video-advertentie moet:
-

Worden gegeven na voltooiing van een video-advertentieweergave.

-

Een ontwikkelaarsproduct zijn dat normaal gesproken beschikbaar zou zijn voor aankoop met Robux in een in-game winkel.

-

Geen valuta inflateren of de economie van de game uit balans brengen.

-

Geen gerandomiseerd item zijn.

Voor richtlijnen over het kiezen van beloningen, zie [Kies beloningen](/docs/nl-nl/production/promotion/rewarded-video-playbook#choose-rewards)  in het beloningsvideo-handboek. |

Het opnieuw indienen van je Content Rating Questionnaire  zal tijdelijk je advertenties geschiktheid verwijderen terwijl de vragenlijst in behandeling is. Om herhaalde onderbrekingen te voorkomen, dien de vragenlijst alleen opnieuw in wanneer je een game-update publiceert die je eerdere antwoorden wijzigt.

Elke schending van de geschiktheidseisen kan leiden tot schorsing van het account, verwijdering van inhoud, intrekking van advertentie-uitbetalingen of verlies van geschiktheid om inkomsten uit advertenties te verdienen.

## [Beste praktijken](#beste-praktijken)[](#beste-praktijken)

Voor plaatsing, beloningsstrategie en een zelfaudit-checklist, zie het [Beloningsvideo-handboek](/docs/nl-nl/production/promotion/rewarded-video-playbook) .

Voor implementatie, volg deze technische praktijken:

-

Roep [GetAdAvailabilityNowAsync](/docs/nl-nl/reference/engine/classes/AdService#GetAdAvailabilityNowAsync)  zo dicht mogelijk bij het moment op dat je van plan bent de advertentie te tonen. Als je bijvoorbeeld een "Bekijk video-advertentie om een beloning te krijgen" knop in een winkelmenu hebt, roep GetAdAvailabilityNowAsync  dan alleen op wanneer de gebruiker het winkelmenu opent. Deze aanpak verbetert de prestaties door te voorkomen dat advertenties onnodig in het geheugen worden vastgehouden, en profiteert van CPM (kosten-per-duizend impressies) en inkomsten door het vulpercentage van advertenties te optimaliseren.

-

Roep na het beëindigen van een advertentie alleen [GetAdAvailabilityNowAsync()](/docs/nl-nl/reference/engine/classes/AdService#GetAdAvailabilityNowAsync)  op als je de gebruiker een andere kans biedt om een advertentie te bekijken. Dit helpt om vervulde aanvragen te vermijden die niet leiden tot impressies.

-

Gebruik [advertentiekansen](#advertentiekansen)  om bij te houden wanneer je een gebruiker de kans biedt om een video-advertentie voor een beloning te bekijken. Let op de verhouding tussen vervulde aanvragen, advertentiekansen en advertentie-impressies om te zien of advertenties moeilijk te vinden zijn of dat beloningen niet aantrekkelijk genoeg zijn.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
