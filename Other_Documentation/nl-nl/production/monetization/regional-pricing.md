<!-- Source: https://create.roblox.com/docs/nl-nl/production/monetization/regional-pricing -->

Regionale prijzen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Verdienen](/docs/nl-nl/production/monetization)
6. /
7. [Managed pricing](/docs/nl-nl/production/monetization/managed-pricing)

# Regionale prijzen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Met Beheerde Prijzen kunt u regio-specifieke prijzen  voor uw artikelen aanbieden en een inclusievere en toegankelijkere wereldwijde economie opbouwen. Nadat u een standaard wereldwijde prijs voor een artikel heeft bepaald, gebruikt Roblox een verscheidenheid aan signalen, zoals de koopkracht van de regio, wisselkoersen en lokaal bestedingsgedrag, om de meest geschikte prijs voor dat artikel regio per regio vast te stellen.

U kunt kiezen welke van uw artikelen u regionaal wilt prijzen. Wanneer u Beheerde Prijzen voor een artikel in uw game inschakelt, past Roblox automatisch de prijs van dat artikel aan voor gebruikers op basis van hun economische locatie.

Economische locatie is niet altijd hetzelfde als accountlocatie. Om de economische locatie van een gebruiker te bepalen, kijkt Roblox naar signalen, waaronder VPN-gebruik, factureringsgeschiedenis en accountgeschiedenis. Als hun economische locatie niet kan worden bepaald, zien gebruikers in plaats daarvan de standaard wereldwijde prijs voor het artikel.

Om prijsarbitrage te voorkomen wanneer gebruikers artikelen met verschillende beheerde prijzen cadeau doen of verhandelen, kunt u [in-game transfers beheren met de GetUsersPriceLevelsAsync  API](#bescherm-uw-handel-en-cadeaus) .

Regionale prijzen zullen nooit meer dan 70% van uw standaardprijs worden afgeprijsd, en ze zullen nooit de standaardprijs overschrijden die u voor uw artikel heeft ingesteld.

Bijvoorbeeld, als uw artikel een standaardprijs van 100 Robux heeft, kan de laagste prijs voor het artikel 30 Robux zijn en de hoogste is 100 Robux, ongeacht de regio van de gebruiker.

## [Schakel regionale prijzen in](#schakel-regionale-prijzen-in)[](#schakel-regionale-prijzen-in)

Regionale prijzen worden periodiek bijgewerkt om veranderingen in wereldwijde economische trends weer te geven.

### [Voor passen](#voor-passen)[](#voor-passen)

Regionale prijzen zijn standaard ingeschakeld voor alle nieuwe en bestaande passen via [Beheerde prijzen](/docs/nl-nl/production/monetization/managed-pricing) .

Om beheerde prijzen voor een pas uit te schakelen:

1.

Ga naar [Creations](https://create.roblox.com/dashboard/creations)  en selecteer een game.

2.

Ga naar Monetization  ⟩ Passes .

3.

Selecteer een of meer bestaande passen.

4.

Klik op Beheerde Prijzen Uitschakelen .

5.

OPTIONAL

 Om beheerde prijzen per land of regio te bekijken, selecteert u een pas en gaat u naar de Verkoop  pagina. De lijst Top Landen/Regio's  wordt bijgewerkt om de aangepaste prijzen weer te geven op basis van de standaardprijs van de pas. Om prijzen voor alle landen en regio's te bekijken, klikt u op Bekijk alle landen .

### [Voor ontwikkelaarsproducten](#voor-ontwikkelaarsproducten)[](#voor-ontwikkelaarsproducten)

Om beheerde prijzen voor een ontwikkelaarsproduct in te schakelen:

1.

Controleer of uw ontwikkelaarsproducten [dynamisch-geprogrammeerde prijzen](#controleer-op-dynamische-prijzen)  hebben.

2.

[Implementeer de GetUsersPriceLevelsAsync  methode](#bescherm-uw-handel-en-cadeaus)  om artikeltransfers te reguleren op basis van de prijsniveaus van gebruikers.

3.

Ga naar [Creations](https://create.roblox.com/dashboard/creations)  en selecteer een game.

4.

Ga naar Monetization  ⟩ Developer Products .

5.

Selecteer een of meer bestaande producten, of maak een nieuw product aan.

6.

Klik op Beheerde Prijzen Inschakelen .

7.

OPTIONAL

 Om Beheerde Prijzen per land of regio te bekijken, selecteert u een product en gaat u naar de Basisinstellingen  pagina. De lijst Top Landen/Regio's  wordt bijgewerkt om de aangepaste prijzen weer te geven op basis van de standaardprijs van het product. Om Beheerde Prijzen voor alle landen en regio's te bekijken, klikt u op Bekijk alle landen .

### [Voor abonnementen](#voor-abonnementen)[](#voor-abonnementen)

Beheerde prijzen zijn standaard ingeschakeld voor abonnementen die in Robux zijn geprijsd en kunnen niet worden uitgeschakeld. Voor meer informatie, zie [Abonnementen maken](/docs/nl-nl/production/monetization/subscriptions#abonnementen-maken) .

Beheerde prijzen zijn niet beschikbaar voor abonnementen die in lokale valuta zijn geprijsd.

### [Voor Avatar-artikelen](#voor-avatar-artikelen)[](#voor-avatar-artikelen)

Om Beheerde Prijzen voor een Avatar-artikel in te schakelen, zie [Prijzen](/docs/nl-nl/marketplace/publish-to-marketplace#prijzen)  op de pagina Publiceren naar Marketplace.

## [Controleer op dynamische prijzen](#controleer-op-dynamische-prijzen)[](#controleer-op-dynamische-prijzen)

Als u Beheerde Prijzen alleen toepast op passen die te koop zijn op uw game-details pagina, hoeft u geen hard-coded prijzen te controleren.

Wanneer u Beheerde Prijzen inschakelt, past de prijs van het artikel zich aan voor gebruikers in verschillende regio's, of het nu te koop is binnen of buiten uw game. Als u echter de prijs hard-coded in de UI van uw game heeft ingesteld, wordt dat nummer niet bijgewerkt omdat het niet dynamisch is of toegankelijk is voor Roblox. Als gevolg hiervan worden gebruikers de juiste regio-specifieke prijs in rekening gebracht, maar toont de UI nog steeds de hard-coded waarde.

De dynamische prijscontroletool  werkt alle artikelen die te koop zijn binnen uw game bij met een nep Robux-prijs of een nep economische locatie om u te helpen identificeren welke prijzen hard-coded zijn in de UI van uw game en welke dynamisch-geprogrammeerd zijn met [MarketplaceService](/docs/nl-nl/reference/engine/classes/MarketplaceService)  en worden aangeroepen vanuit een clientscript. Nadat u de hard-coded passen heeft geïdentificeerd, kunt u ze bijwerken om MarketplaceService -functies te gebruiken.

Om de dynamische prijscontroletool te gebruiken:

1.

Ga naar Monetization .

-

Voor passen, ga naar Passes .

-

Voor ontwikkelaarsproducten, ga naar Developer Products .

2.

Klik op …  en selecteer Dynamische Prijscontrole .

3.

Onder Voeg testaccounts toe , voer tot vijf Roblox-gebruikers in om hard-coded prijzen te controleren.

4.

Selecteer een testtype.

-

Prijs vastgezet  werkt alle dynamisch-geprogrammeerde prijzen bij met een vast nep Robux-bedrag.

-

Locatie vastgezet  werkt alle dynamisch-geprogrammeerde prijzen bij met een regio-specifieke prijs voor een nep economische locatie.

5.

Klik op Inschakelen . Na een paar minuten, ga naar uw game om de hard-coded prijzen te identificeren.

Om de dynamische prijscontroletool uit te schakelen, gaat u naar de pagina Dynamische Prijscontrole  en klikt u op Uitschakelen .

Voor meer informatie over hard-coded versus dynamisch-geprogrammeerde productprijzen, zie [Controleer op dynamische prijzen](/docs/nl-nl/production/monetization/price-optimization#controleer-op-dynamische-prijzen)  op de pagina Prijsoptimalisatie. Voor meer informatie over het verkopen van passen en ontwikkelaarsproducten met MarketplaceService -functies, zie [Verkoop een pas binnen uw game](/docs/nl-nl/production/monetization/passes#binnen-je-game)  en [Verkoop een ontwikkelaarsproduct binnen uw game](/docs/nl-nl/production/monetization/developer-products#binnen-je-game) .

## [Toon regionale prijzen in uw game](#toon-regionale-prijzen-in-uw-game)[](#toon-regionale-prijzen-in-uw-game)

Met Beheerde Prijzen kan de prijs die een gebruiker ziet variëren op basis van hun locatie. Als u prijzen weergeeft in een aangepaste in-game UI, zoals een [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel) , kunt u productinformatie opvragen tijdens runtime om ervoor te zorgen dat de weergegeven prijs overeenkomt met de prijs die in de aankoopprompt wordt getoond.

Om de regionale prijs voor een enkel ontwikkelaarsproduct of pas weer te geven, gebruikt u [GetProductInfoAsync](/docs/nl-nl/reference/engine/classes/MarketplaceService#GetProductInfoAsync) .

Om de regionale prijs voor alle ontwikkelaarsproducten weer te geven, gebruikt u [GetDeveloperProductsAsync](/docs/nl-nl/reference/engine/classes/MarketplaceService#GetDeveloperProductsAsync) .

## [Bescherm uw handel en cadeaus](#bescherm-uw-handel-en-cadeaus)[](#bescherm-uw-handel-en-cadeaus)

Beheerde prijzen kunnen invloed hebben op in-game transfers zoals handelen en cadeau doen. Vanwege prijsverschillen tussen regio's kan prijsarbitrage (het uitbuiten van prijsverschillen tussen dezelfde producten om winst te genereren) plaatsvinden. Om het potentieel voor prijsarbitrage te beheren, kunt u de [GetUsersPriceLevelsAsync](/docs/nl-nl/reference/engine/classes/MarketplaceService#GetUsersPriceLevelsAsync)  API gebruiken, waarmee u de relatieve prijsniveaus van gebruikers kunt bepalen, zodat u logica kunt implementeren om artikeltransfers op basis van deze niveaus te reguleren.

GetUsersPriceLevelsAsync  geeft een numerieke waarde tussen 1 en 1000 terug die het prijsniveau van een gebruiker aangeeft. Deze waarde is ontworpen om het percentage van de volledige prijs weer te geven dat een gebruiker naar verwachting zal betalen. Het prijsniveau 1000 vertegenwoordigt de volledige wereldprijs, terwijl lagere prijsniveaus aangeven dat de gebruiker doorgaans een lagere prijs betaalt vanwege hun economische locatie.

Een lager prijsniveau verschil betekent dat er een kleiner prijsverschil is tussen de volledige wereldprijs en de beheerde prijs van de gebruiker. Een hoger prijsniveau verschil betekent dat er een groter prijsverschil is tussen de twee. Bijvoorbeeld:

-

Gebruiker A heeft het prijsniveau 1000, wat de volledige wereldprijs vertegenwoordigt. Deze gebruiker betaalt 100% van de basisprijs voor een artikel.

-

Gebruiker B heeft het prijsniveau 500, wat 50% van de volledige wereldprijs vertegenwoordigt. Deze gebruiker betaalt 50% van de basisprijs voor een artikel.

-

Zodra u het prijsniveau van elke gebruiker kent, kunt u ervoor kiezen om het cadeau doen of handelen tussen Gebruiker A en Gebruiker B goed te keuren of te blokkeren op basis van hun prijsniveau verschil van 500.

### [Implementeer GetUsersPriceLevelsAsync](#implementeer-getuserspricelevelsasync)[](#implementeer-getuserspricelevelsasync)

We raden aan om de resultaten van uw GetUsersPriceLevelsAsync  API-aanroepen na een gebruikerssessie niet  te cachen. De prijsniveaus van gebruikers kunnen veranderen. Vertrouwen op gecachte gegevens kan leiden tot onnauwkeurige transferlogica en potentiële misbruik of uitbuiting van het systeem.

Om ervoor te zorgen dat u de meest actuele prijsinformatie voor elke gebruiker heeft, doet u altijd oproepen naar GetUsersPriceLevelsAsync  bij het joinen van de speler.

Om de prijsniveaus van gebruikers die betrokken zijn bij een artikeltransfer te krijgen, roept u de functie GetUsersPriceLevelsAsync  aan in de MarketplaceService . Deze functie neemt een array van gebruikers-ID's als argument en retourneert een array van PriceLevelInfo  objecten met de volgende velden:

```

type PriceLevelInfo = {

    UserId: number,

    PriceLevel: number

}

```

Na het implementeren van de functie, gebruikt u de geretourneerde prijsniveaus om te kiezen of u een artikeltransfer wilt toestaan. U kunt bijvoorbeeld gebruikers met een hoger prijsniveau toestaan om artikelen cadeau te doen aan gebruikers met een lager prijsniveau, maar alleen handelen toestaan tussen gebruikers die hetzelfde prijsniveau hebben. Zie de [beschikbare voorbeelden](#voorbeelden)  voor meer informatie.

Voor meer informatie over de GetUsersPriceLevelsAsync  API, zie [MarketplaceService](/docs/nl-nl/reference/engine/classes/MarketplaceService#GetUsersPriceLevelsAsync) .

### [Voorbeelden](#voorbeelden)[](#voorbeelden)

Voorbeelden van hoe u GetUsersPriceLevelsAsync  kunt gebruiken met regionale prijzen.

##### Voorbeeld 1: Controleer de prijsniveaus voor een lijst van gebruikers

Dit voorbeeld laat zien hoe u prijsniveaus voor een lijst van gebruikers kunt ophalen, wat u kan helpen kiezen of u een artikeltransfer wilt toestaan.

```

-- Verkrijg de MarketplaceService

local MarketplaceService = game:GetService("MarketplaceService")

-- Definieer een functie om prijsniveaus voor een lijst van gebruikers op te halen en maakt een lookup-tabel van UserId naar PriceLevel

local function getPriceLevelsLookup(userIds)

    local success, result = pcall(function()

        return MarketplaceService:GetUsersPriceLevelsAsync(userIds)

    end)

    if success then

        -- Map elke PriceLevelInfo naar een UserId -> PriceLevel lookup-tabel

        local lookup = {}

        for _, userData in ipairs(result) do

            lookup[userData.UserId] = userData.PriceLevel

        end

        return lookup

    else

        warn("Fout bij het ophalen van prijsniveaus:", result)

        return nil

    end

end

-- Voorbeeld met placeholder-ID's

local user1Id = 123456789

local user2Id = 987654321

-- Roep de functie aan en sla het resultaat op

local priceLevels = getPriceLevelsLookup({user1Id, user2Id})

-- Als het succesvol is, print elk gebruikersniveau

if priceLevels then

    print("Prijsniveau voor Gebruiker 1:", priceLevels[user1Id])

    print("Prijsniveau voor Gebruiker 2:", priceLevels[user2Id])

else

    print("Mislukt om prijsniveaus op te halen.")

end

```

##### Voorbeeld 2: Vergelijk het prijsniveau van een verzender met het prijsniveau van een ontvanger

Dit voorbeeld laat u een voorbeeldimplementatie  zien van hoe u het prijsniveau van een verzender kunt controleren tegen het prijsniveau van de ontvanger. Dit kan u helpen om het cadeau doen van gebruikers in hoger geprijsde regio's aan gebruikers in lager geprijsde regio's te beheren.

```

-- Verkrijg de MarketplaceService

local MarketplaceService = game:GetService("MarketplaceService")

-- Definieer een functie om prijsniveaus voor een lijst van gebruikers op te halen en maakt een lookup-tabel van UserId naar PriceLevel

local function getPriceLevelsLookup(userIds)

    local success, result = pcall(function()

        return MarketplaceService:GetUsersPriceLevelsAsync(userIds)

    end)

    if success then

        -- Map elke PriceLevelInfo naar een UserId -> PriceLevel lookup-tabel

        local lookup = {}

        for _, userData in ipairs(result) do

            lookup[userData.UserId] = userData.PriceLevel

        end

        return lookup

    else

        warn("Fout bij het ophalen van prijsniveaus:", result)

        return nil

    end

end

-- Definieer een functie die controleert of de verzender een hoger of gelijk prijsniveau heeft dan de ontvanger

-- De parameters zijn de Speler die het item verzendt en de Speler die het item ontvangt

-- De functie retourneert true als het prijsniveau van de verzender groter is dan of gelijk aan het prijsniveau van de ontvanger

function isSenderPriceLevelHigherOrEqualforGifting(sender, recipient)

	local priceLevelsLookup = getPriceLevelsLookup({ sender.UserId, recipient.UserId })

	if not priceLevelsLookup then

		error("MarketplaceService:GetUsersPriceLevelsAsync is mislukt. Kan gebruikersprijsniveaus niet ophalen.")

	end

	local senderPriceLevel = priceLevelsLookup[sender.UserId]

	local recipientPriceLevel = priceLevelsLookup[recipient.UserId]

	return senderPriceLevel >= recipientPriceLevel

end

```

##### Voorbeeld 3: Controleer of twee gebruikers hetzelfde prijsniveau hebben

Dit voorbeeld laat u een voorbeeldimplementatie  zien van hoe u kunt controleren of twee gebruikers hetzelfde prijsniveau hebben. Dit kan u helpen om te handelen en een eerlijke uitwisseling tussen gebruikers uit verschillende regio's te waarborgen.

```

-- Verkrijg de MarketplaceService

local MarketplaceService = game:GetService("MarketplaceService")

-- Definieer een functie om prijsniveaus voor een lijst van gebruikers op te halen en maakt een lookup-tabel van UserId naar PriceLevel

local function getPriceLevelsLookup(userIds)

    local success, result = pcall(function()

        return MarketplaceService:GetUsersPriceLevelsAsync(userIds)

    end)

    if success then

        -- Map elke PriceLevelInfo naar een UserId -> PriceLevel lookup-tabel

        local lookup = {}

        for _, userData in ipairs(result) do

            lookup[userData.UserId] = userData.PriceLevel

        end

        return lookup

    else

        warn("Fout bij het ophalen van prijsniveaus:", result)

        return nil

    end

end

-- Definieer een functie die controleert of twee gebruikers hetzelfde prijsniveau hebben

-- De parameters zijn de twee gebruikers wiens prijsniveaus u wilt vergelijken

-- De functie retourneert true als beide gebruikers hetzelfde prijsniveau hebben

function haveSamePriceLevelForTrading(userA, userB)

	local priceLevelsLookup = getPriceLevelsLookup({ userA.UserId, userB.UserId })

	if not priceLevelsLookup then

		error("MarketplaceService:GetUsersPriceLevelsAsync is mislukt. Kan gebruikersprijsniveaus niet ophalen.")

	end

	local userAPriceLevel = priceLevelsLookup[userA.UserId]

	local userBPriceLevel = priceLevelsLookup[userB.UserId]

	return userAPriceLevel == userBPriceLevel

end

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
