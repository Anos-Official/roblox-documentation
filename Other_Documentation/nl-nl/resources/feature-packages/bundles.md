<!-- Source: https://create.roblox.com/docs/nl-nl/resources/feature-packages/bundles -->

Bundelpakket | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Voorbeelden en projecten](/docs/nl-nl/samples)

# Bundelpakket

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het Bundels  functiepakket biedt kant-en-klare functionaliteit om collecties van items met korting aan spelers te verkopen. Je kunt kiezen of je spelers toestaat om bundels te kopen met een aangepaste in-game valuta of Robux, welk type bundel je wilt gebruiken, welke set items je wilt verkopen en hoe je spelers wilt aanmoedigen tijdens hun gameplay.

Met de aanpassingsopties van het pakket kun je je bundels afstemmen op de ontwerp- en monetisatie-doelen van je games, zoals:

-

Gericht zijn op een lage [conversieratio](/docs/nl-nl/production/game-design/analytics-essentials#monetization-metrics)  door korting te geven op starterspakketten die waarde bieden aan nieuwe spelers en vroege uitgaven aanmoedigen.

-

Het verhogen van de [uitgave diepte](/docs/nl-nl/production/game-design/analytics-essentials#monetization-metrics)  door items in verschillende prijsklassen te bundelen om een breed scala aan spelers aan te spreken.

-

Het monetiseren van live operaties (LiveOps) [evenementen](/docs/nl-nl/production/game-design/liveops-essentials#contentcadans)  door tijdelijke bundels van exclusieve items aan te bieden.

 ![](https://prod.docsiteassets.roblox.com/assets/resources/feature-packages/Bundles/Bundles-Intro.png)

Voor informatie over hoe je strategisch aankoopmogelijkheden kunt bieden om aan de behoeften van spelers te voldoen op belangrijke momenten in je ervaring, zie [Contextuele Aankopen](/docs/nl-nl/production/game-design/contextual-purchases) .

## [Verkrijg pakket](#verkrijg-pakket)[](#verkrijg-pakket)

De Creator Store  is een tabblad van de Toolbox  dat je kunt gebruiken om alle assets te vinden die zijn gemaakt door Roblox en de Roblox-gemeenschap voor gebruik binnen je projecten, inclusief model-, afbeelding-, mesh-, audio-, plugin-, video- en lettertype-assets. Je kunt de Creator Store gebruiken om een of meer assets rechtstreeks in een open spel toe te voegen, inclusief functiepakketten!

Elk functiepakket vereist het Core  functiepakket om goed te functioneren. Zodra de Core  en Bundles  functiepakket-assets in je inventaris zijn, kun je ze hergebruiken in elk project op het platform.

Om de pakketten van je inventaris naar je spel te krijgen:

1.

Voeg het Core  en Bundles  functiepakket toe aan je inventaris binnen Studio door op de link Toevoegen aan Inventaris  te klikken in de volgende set componenten.

[

#### Core Functiepakket

Het Core functiepakket biedt gedeelde datastores voor alle functiepakketten.

](https://create.roblox.com/store/asset/94918533221001)

Toevoegen aan inventaris

[

#### Bundles Functiepakket

Het Bundles Functiepakket biedt functionaliteit om collecties van items met korting aan spelers te verkopen.

](https://create.roblox.com/store/asset/72975253516300)

Toevoegen aan inventaris

2.

Open het [Toolbox](/docs/nl-nl/projects/assets/toolbox)  venster vanuit het Venster  menu of de Start  tabblad werkbalk.

3.

In het Toolbox  venster, klik op het Inventaris  tabblad. De Mijn Modellen  sortering wordt weergegeven.

 ![Studio's Toolbox venster met het Inventaris tabblad gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/studio/toolbox/Inventory-Tab.png)

4.

Klik op de tegel Feature Package Core , en vervolgens op de tegel Bundle Feature Package . Beide pakketmappen worden weergegeven in het Explorer  venster.

5.

Sleep de pakketmappen naar [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) .

6.

Sta datastores toe om aankopen van spelers met de pakketten bij te houden.

1.

Open het Bestand  ⟩ Ervaringsinstellingen  venster in Studio.

2.

Navigeer naar het Beveiliging  tabblad, en schakel vervolgens Studio-toegang tot API-services inschakelen  in.

## [Definieer valuta](#definieer-valuta)[](#definieer-valuta)

Als je niet van plan bent om in-game valuta voor enige bundels in rekening te brengen, kun je deze sectie overslaan en bundels configureren via devProductId .

Als je spel een eigen valutasysteem heeft, kun je deze registreren met het Core  functiepakket door ze te definiëren in ReplicatedStorage.FeaturePackagesCore.Configs.Currencies . Er is al een voorbeeld van een Gems-valuta in dit bestand; vervang het door je eigen.

Valuta

```

Gems = {

        displayName = "Gems",

        symbol = "💎",

        icon = nil,

    },

```

Het Currencies  script vertelt het Core  functiepakket enkele metadata over je valuta:

-

(vereist) displayName  - De naam van je valuta. Als je geen symbool of pictogram opgeeft, wordt deze naam gebruikt in aankoopknoppen (d.w.z. "100 Gems").

-

(optioneel) symbol  - Als je een tekstteken hebt om als pictogram voor je valuta te gebruiken, wordt dit in plaats van de displayName  in aankoopknoppen gebruikt (d.w.z. "💎100").

-

(optioneel) icon  - Als je een AssetId  afbeelding pictogram voor je valuta hebt, wordt dit in plaats van de displayName  in aankoopknoppen gebruikt (d.w.z. afbeelding wordt links van de prijs geplaatst "🖼️100")

Als je zowel een symbool als een pictogram voor je valuta opgeeft, gebruikt het pakket het pictogram in plaats van het symbool.

Zodra je valuta is ingesteld, moet je handmatig de prijs, valuta en pictogram van de bundel voor de heads-up display specificeren in plaats van dat deze informatie van het bijbehorende ontwikkelaarsproduct van de bundel wordt opgehaald.

Bundels

```

-- Als je een dev-product wilt gebruiken, moet je een unieke devProductId opgeven, die alleen door één bundel wordt gebruikt.

    -- We zullen de bundelprijs en het pictogram van het ontwikkelaarsproduct ophalen

    pricing = {

        priceType = CurrencyTypes.PriceType.Marketplace,

        devProductId = 1795621566,

    },

    -- Anders, als je in-game valuta in plaats van een dev-product wilt gebruiken, kun je het volgende gebruiken:

    -- Prijs hier is in de in-game valuta, niet Robux

    pricing = {

        priceType = CurrencyTypes.PriceType.InExperience,

        price = 79,

        currencyId = "Gems",

        icon = 18712203759,

    },

```

Je moet ook het BundlesExample  script verwijzen om setInExperiencePurchaseHandler  aan te roepen.

BundlesExample

```

local function awardInExperiencePurchase(

    _player: Player,

    _bundleId: Types.BundleId,

    _currencyId: CurrencyTypes.CurrencyId,

    _price: number

)

    -- Controleer of de speler genoeg valuta heeft om de bundel te kopen

    -- Werk spelerdata bij, geef items, enz.

    -- Trek de valuta van de speler af

    task.wait(2)

    return true

end

local function initializePurchaseHandlers()

    local bundles = Bundles.getBundles()

    for bundleId, bundle in bundles do

        -- Bundel is niet geassocieerd met een ontwikkelaarsproduct als het geen marktplaatsprijs type heeft

        if not bundle or bundle.pricing.priceType ~= "Marketplace" then

            continue

        end

        Bundles.setPurchaseHandler(bundleId, awardMarketplacePurchase)

        receiptHandlers[bundle.pricing.devProductId] = receiptHandler

    end

    -- Als je in-game valuta hebt die je gebruikt voor bundels, stel dan hier de handler in

    for currencyId, _ in Currencies do

        Bundles.setInExperiencePurchaseHandler(currencyId, awardInExperiencePurchase)

    end

end

```

Specifiek moet je awardInExperiencePurchase  invullen, die wordt aangeroepen door een lus door Currencies  binnen het voorbeeld initializePurchaseHandlers  (d.w.z. elke currencyId is verbonden met de handler via Bundles.setInExperiencePurchaseHandler(currencyId, awardInExperiencePurchase) ).

## [Definieer bundels](#definieer-bundels)[](#definieer-bundels)

Alle bundels die in je spel kunnen worden aangeboden, kunnen worden gedefinieerd binnen ReplicatedStorage.Bundles.Configs.Bundles , met types geëxporteerd vanuit het Types  script in dezelfde map.

Als je een devProductId  gebruikt, moet je de hoofd devProductId  van de bundel bijwerken om overeen te komen met degene in je spel. Dit is wat zal worden gevraagd via [MarketplaceService](/docs/nl-nl/reference/engine/classes/MarketplaceService)  om de bundel zelf aan te kopen. Het wordt sterk aanbevolen om een nieuw ontwikkelaarsproduct voor de bundel te gebruiken om het gemakkelijker te maken om afzonderlijke verkopen bij te houden.

Als je een bundel met meerdere items wilt, en als deze al worden vertegenwoordigd door ontwikkelaarsproducten in je spel, hoef je de itemprijs/assetId/naam niet expliciet in te stellen, deze zullen via productinformatie worden opgehaald:

README

```

{

        itemType = ItemTypes.ItemType.DevProduct,

        devProductId = <DEV_PRODUCT_ID>,

        metadata = {

            caption = {

                text = "x1",

                color = Color3.fromRGB(236, 201, 74),

            } -- Bijschrift is optioneel! Je kunt dit veld ook weglaten

        }

    },

```

Anders kun je die itemdetails handmatig configureren:

README

```

{

        itemType = ItemTypes.ItemType.Robux,

        priceInRobux = 49,

        icon = <IMAGE_ASSET_ID>,

        metadata = {

            caption = {

                text = "x1",

                color = Color3.fromRGB(236, 201, 74),

            } -- Bijschrift is optioneel! Je kunt dit veld ook weglaten

        }

    },

```

Bijvoorbeeld, je hele bundel zal er waarschijnlijk zo uitzien:

README

```

local starterBundle: Types.RelativeTimeBundle = {

        bundleType = Types.BundleType.RelativeTime,

        -- Als je een dev-product wilt gebruiken, moet je een unieke devProductId opgeven, die alleen door één bundel wordt gebruikt.

        -- We zullen de bundelprijs en het pictogram van het ontwikkelaarsproduct ophalen

        pricing = {

            priceType = CurrencyTypes.PriceType.Marketplace,

            devProductId = <DEV_PRODUCT_ID>,

        },

        -- Anders, als je in-game valuta in plaats van een dev-product wilt gebruiken, kun je het volgende gebruiken:

        -- Prijs hier is in de in-game valuta, niet Robux

        -- pricing = {

        --  priceType = CurrencyTypes.PriceType.InExperience,

        --  price = 79,

        --  currencyId = <CURRENCY_ID>,

        --  icon = <IMAGE_ASSET_ID>,

        -- },

        includedItems = {

            [1] = {

                -- Het item zelf wordt niet verkocht via een ontwikkelaarsproduct, dus geef aan hoeveel het waard is in Robux en geef een pictogram

                -- De priceInRobux helpt Bundles om de relatieve waarde van de bundelprijs ten opzichte van de som van de inhoud weer te geven

                itemType = ItemTypes.ItemType.Robux,

                priceInRobux = 49,

                icon = <IMAGE_ASSET_ID>,

                -- Alternatief, als dit een dev-product heeft, laat dan de prijs en het pictogram hierboven weg en stel gewoon de devProductId in

                -- De prijs en het pictogram worden van het ontwikkelaarsproduct opgehaald

                -- devProductId = <ITEM_DEV_PRODUCT_ID>

                -- Er zijn meer optionele metadata-velden die UI-specifiek zijn indien nodig

                metadata = {

                    caption = {

                        text = "x1",

                        color = Color3.fromRGB(236, 201, 74),

                    },

                },

            },

            [2] = {

                itemType = ItemTypes.ItemType.Robux,

                priceInRobux = 99,

                icon = <IMAGE_ASSET_ID>,

                metadata = {

                    caption = {

                        text = "x1",

                        color = Color3.fromRGB(236, 201, 74),

                    },

                },

            },

            [3] = {

                itemType = ItemTypes.ItemType.Robux,

                priceInRobux = 149,

                icon = <IMAGE_ASSET_ID>,

                metadata = {

                    caption = {

                        text = "x1",

                        color = Color3.fromRGB(236, 201, 74),

                    },

                },

            },

        },

        singleUse = true, -- Eenmaal gekocht of verlopen, niet meer geldig, zelfs niet als je spel probeert te vragen (onPlayerAdded). Je kunt dit op false zetten tijdens het testen in studio.

        durationInSeconds = 900, -- 15 minuten

        includesOfflineTime = false, -- Tel alleen de tijd die in het spel is verstreken

        metadata = {

            displayName = "STARTER BUNDLE",

            description = "Bespaar 75% en krijg een voorsprong!",

        },

    }

```

## [Integreer serverlogica](#integreer-serverlogica)[](#integreer-serverlogica)

Bekijk ReplicatedStorage.Bundles.Server.Examples.BundlesExample , dat laat zien hoe je server zal interageren met het Bundles  functiepakket en de bovenstaande methoden op het [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript) . De onderstaande snippets zijn afkomstig uit dat script.

Je moet voornamelijk vier dingen aansluiten zodra je het Bundles  functiepakket in je spel sleept:

1.

Verbind aankoophandlers via Bundles.setPurchaseHandler  om de functies op te geven die moeten worden aangeroepen om items toe te kennen wanneer een aankoop wordt verwerkt.

BundlesExample

```

local function awardMarketplacePurchase(_player: Player, _bundleId: Types.BundleId, _receiptInfo: { [string]: any })

     -- Werk spelerdata bij, geef items, enz.

     -- ... EN registreer receiptInfo.PurchaseId zodat we kunnen controleren of de gebruiker deze bundel al heeft

     task.wait(2)

     return Enum.ProductPurchaseDecision.PurchaseGranted

 end

 local function awardInExperiencePurchase(

     _player: Player,

     _bundleId: Types.BundleId,

     _currencyId: CurrencyTypes.CurrencyId,

     _price: number

 )

     -- Controleer of de speler genoeg valuta heeft om de bundel te kopen

     -- Werk spelerdata bij, geef items, enz.

     -- Trek de valuta van de speler af

     task.wait(2)

     return true

 end

 local function initializePurchaseHandlers()

     local bundles = Bundles.getBundles()

     for bundleId, bundle in bundles do

         -- Bundel is niet geassocieerd met een ontwikkelaarsproduct als het geen marktplaatsprijs type heeft

         if not bundle or bundle.pricing.priceType ~= "Marketplace" then

             continue

         end

         Bundles.setPurchaseHandler(bundleId, awardMarketplacePurchase)

         receiptHandlers[bundle.pricing.devProductId] = receiptHandler

     end

     -- Als je in-game valuta hebt die je gebruikt voor bundels, stel dan hier de handler in

     for currencyId, _ in Currencies do

         Bundles.setInExperiencePurchaseHandler(currencyId, awardInExperiencePurchase)

     end

 end

```

2.

Verbind je logica voor [MarketplaceService.ProcessReceipt](/docs/nl-nl/reference/engine/classes/MarketplaceService#ProcessReceipt) , maar dit kan elders worden gedaan als je spel al ontwikkelaarsproducten te koop heeft. In wezen, wanneer een ontwikkelaarsproductontvangst wordt verwerkt, zullen ze nu Bundles.getBundleByDevProduct  aanroepen om te controleren of het product tot een bundel behoort. Als dat zo is, roept het script vervolgens Bundles.processReceipt  aan.

BundlesExample

```

-- Verwerk ontvangst van de marktplaats om te bepalen of de speler in rekening moet worden gebracht of niet

local function processReceipt(receiptInfo): Enum.ProductPurchaseDecision

    local userId, productId = receiptInfo.PlayerId, receiptInfo.ProductId

    local player = Players:GetPlayerByUserId(userId)

    if not player then

        return Enum.ProductPurchaseDecision.NotProcessedYet

    end

    local handler = receiptHandlers[productId] -- Verkrijg de handler voor het product

    local success, result = pcall(handler, receiptInfo, player) -- Roep de handler aan om te controleren of de aankooplogica succesvol is

    if not success or not result then

        warn("Verwerking van ontvangst mislukt:", receiptInfo, result)

        return Enum.ProductPurchaseDecision.NotProcessedYet

    end

    return Enum.ProductPurchaseDecision.PurchaseGranted

end

local function receiptHandler(receiptInfo: { [string]: any }, player: Player)

    local bundleId, _bundle = Bundles.getBundleByProductId(receiptInfo.ProductId)

    if bundleId then

        -- Deze aankoop behoort tot een bundel, laat Bundles het afhandelen

        local purchaseDecision = Bundles.processReceiptAsync(player, bundleId, receiptInfo)

        return purchaseDecision == Enum.ProductPurchaseDecision.PurchaseGranted

    end

    -- Deze aankoop behoort niet tot een bundel,

    -- ... Behandel al je bestaande logica hier als je die hebt

    return false

 end

```

3.

Verbind Players.PlayerAdded:Connect(Bundles.OnPlayerAdded)  zodat het Bundles  functiepakket opnieuw alle actieve bundels die nog niet zijn verlopen voor een speler aanbiedt.

README

```

local function onPlayerAdded(player: Player)

    -- Vertel Bundles wanneer de speler zich aanmeldt, zodat het hun gegevens kan herladen

    Bundles.onPlayerAdded(player)

    -- Als je een starterbundel had die je aan alle nieuwe gebruikers wilde aanbieden, zou je dat hier kunnen vragen

    -- ... Bundles zal afhandelen of de speler het al heeft gekocht of dat het is verlopen, aangezien het niet herhaalbaar is

    -- Bundles.promptIfValidAsync(player, "StarterBundle")

    -- Dit hier aanroepen is alleen voor het voorbeeld, je kunt dit aanroepen wanneer of waar je maar wilt

    onPromptBundleXYZEvent(player)

end

```

4.

Vraag bundels aan. Hoewel dit afhangt van de gameplay, biedt het voorbeeld spelers een StarterBundle onPlayerAdded .

-

De logica van het Bundles  functiepakket zorgt ervoor dat elke speler geen herhaalaanbod krijgt als ze de bundel al hebben gekocht, of als ze het aanbod al hebben laten verlopen (op basis van bundelconfiguratie).

-

Wanneer je een bundel aan een speler wilt aanbieden, roep je Bundles.promptIfValidAsync(player, bundleId)  aan.

README

```

local function onPromptBundleXYZEvent(player: Player)

    -- Verbind met welk spel evenement je wilt gebruiken om te bepalen wanneer een speler de bundel wordt aangeboden

    -- ... Dit zal zijn wanneer je aan je geschiktheidscriteria hebt voldaan om een speler de bundel aan te bieden

    -- ... Bijvoorbeeld, als je een bundel wilt aanbieden wanneer een speler zich aanmeldt, of wanneer een speler een niveau omhoog gaat

    task.spawn(Bundles.promptIfValidAsync, player, <Some_Bundle_Id>)

    -- ... Als je meerdere bundels maakt, minimaliseert het gebruik van task.spawn() om de bovenstaande functieaanroep te omhullen discrepanties tussen aftellingen

end

```

Bij het toekennen van aankopen, zorg ervoor dat je ook receiptInfo.PurchaseId  controleert en registreert in je datastores.

Overweeg de volgende richtlijnen voor best practices met betrekking tot redundante registraties van ReceiptIds:

-

Terwijl het Bundles  functiepakket ReceiptIds registreert om te voorkomen dat dezelfde ontvangst twee keer wordt verwerkt, moet je ook ReceiptIds registreren in je tabellen, zodat als de aankoopstroom mislukt nadat de aankoophandler al is voltooid, je weet bij een volgende poging om items niet opnieuw toe te kennen.

-

Het Bundles  functiepakket registreert de ReceiptId niet als de aankoop op een bepaald moment mislukt, dus je moet ervoor zorgen dat je de ReceiptId in je tabellen registreert voordat je de ontvangst verwerkt als onderdeel van je purchaseHandler.

-

Deze redundantie helpt ervoor te zorgen dat alle aankooplogica op de juiste manier is afgehandeld en dat je datastore en de datastore van het Bundles  functiepakket uiteindelijk consistent zijn, waarbij je datastore de bron van waarheid is.

## [Configureer constanten](#configureer-constanten)[](#configureer-constanten)

Constanten voor het Core  functiepakket bevinden zich op twee plaatsen:

-

Gedeelde constanten bevinden zich in ReplicatedStorage.FeaturePackagesCore.Configs.SharedConstants .

-

Pakket-specifieke constanten, in dit geval het Bundles  functiepakket, bevinden zich in ReplicatedStorage.Bundles.Configs.Constants .

De belangrijkste dingen die je misschien wilt aanpassen om aan de ontwerpvereisten van je spel te voldoen:

-

Geluidsasset-ID's

-

Duur van het aankoop effect en de kleuren van de deeltjes

-

Inklapbaarheid van de heads-up display

Bovendien kun je strings voor vertaling vinden die in één locatie zijn opgesplitst: ReplicatedStorage.FeaturePackagesCore.Configs.TranslationStrings .

## [Pas UI-componenten aan](#pas-ui-componenten-aan)[](#pas-ui-componenten-aan)

Door de pakketobjecten te wijzigen, zoals kleuren, lettertype en transparantie, kun je de visuele presentatie van je bundelaanbiedingen aanpassen. Houd er echter rekening mee dat als je een van de objecten hiërarchisch verplaatst, de code ze niet kan vinden, en je aanpassingen aan je code moet maken.

Een prompt bestaat uit twee hoofdelementen:

-

PromptItem  – Het individuele component dat wordt herhaald voor elk item binnen een bundel (itemafbeelding, bijschrift, naam, prijs).

-

Prompt  – Het promptvenster zelf.

De heads-up display bestaat ook uit twee componenten:

-

HudItem  – Een individueel component dat elke menu-optie in de heads-up display vertegenwoordigt.

-

Hud  – Om programmatig te worden gevuld met HudItems .

Als je meer controle wilt hebben over de heads-up display, in plaats van alleen de bestaande HUD UI binnen ReplicatedStorage.Bundles.Objects.BundlesGui  te gebruiken, kun je dingen verplaatsen om aan je eigen ontwerpvereisten te voldoen. Zorg er gewoon voor dat je het gedrag van de clientscript in het ReplicatedStorage.Bundles.Client.UIController  script bijwerkt.

## [API-referentie](#api-referentie)[](#api-referentie)

### [Types](#types)[](#types)

#### [RelativeTime](#relativetime)[](#relativetime)

Zodra de RelativeTime  bundel aan een speler wordt aangeboden, blijft deze beschikbaar totdat de tijdsduur is verstreken. Dit type wordt weergegeven op de heads-up display van de speler en vraagt automatisch in toekomstige sessies totdat de bundel verloopt of de speler deze koopt.

Een veelvoorkomend voorbeeld van dit bundeltype is een eenmalig starterspakket dat gedurende 24 uur aan alle nieuwe spelers wordt weergegeven.

| Naam | | Type | | Beschrijving |
| --- | --- |
| includeOfflineTime | | bool | | (Optioneel)  Als dit niet is ingesteld, telt alleen de tijd die in het spel is doorgebracht mee voor de resterende aanbiedingsduur. |
| singleUse | | bool | | (Optioneel)  Als dit niet is ingesteld, kan de aankoop opnieuw worden geactiveerd nadat deze is gekocht of verlopen.
Als dit is ingesteld, zal het, eenmaal gekocht of verlopen, nooit meer kunnen worden aangeboden, zelfs niet als je Bundles.promptIfValidAsync  met de bundleId aanroept. |

#### [FixedTime](#fixedtime)[](#fixedtime)

Zodra de FixedTime  bundel aan een speler wordt aangeboden, blijft deze beschikbaar tot het einde van de ingestelde gecoördineerde universele tijd (UTC). Dit type wordt weergegeven op de heads-up display van de speler en vraagt automatisch in toekomstige sessies totdat de bundel verloopt of de speler deze koopt.

Een veelvoorkomend voorbeeld van dit bundeltype is een vakantieaanbieding die slechts een bepaalde maand beschikbaar is.

#### [OneTime](#onetime)[](#onetime)

Een OneTime  bundel is alleen beschikbaar op het moment dat deze aan een speler wordt aangeboden. Het wordt niet weergegeven op de heads-up display van de speler, en zodra een speler de prompt sluit, kan deze niet opnieuw worden geopend totdat deze opnieuw door de server wordt aangeboden.

Een veelvoorkomend voorbeeld van dit bundeltype is een aanbieding om meer in-game valuta te kopen op het moment dat een speler zonder komt te zitten.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
