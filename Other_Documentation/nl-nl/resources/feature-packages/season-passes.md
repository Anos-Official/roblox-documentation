<!-- Source: https://create.roblox.com/docs/nl-nl/resources/feature-packages/season-passes -->

Seizoenpassenpakket | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Voorbeelden en projecten](/docs/nl-nl/samples)

# Seizoenpassenpakket

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Dit functiepakket is in bèta en vereist een aangepaste configuratie voor de unieke behoeften van jouw games. Zorg ervoor dat je de balans en functionaliteit van je seizoenpas test voordat je deze publiceert voor jouw publiek.

Het Seizoenpassen  functiepakket biedt kant-en-klare functionaliteit om beperkte tijd, op missies gebaseerde voortgangssystemen te creëren waarin spelers questdoelen kunnen voltooien om beloningen te verdienen die alleen beschikbaar zijn tijdens een vooraf gedefinieerde periode. Met de aanpassingsopties van het pakket kun je alle seizoenpassen personaliseren om nieuwe inhoud aan jouw publiek te leveren, de spelersbinding te bevorderen en inkomsten te genereren.

 ![](https://prod.docsiteassets.roblox.com/assets/resources/feature-packages/Season-Passes/Season-Passes-Intro.png)

Voor informatie over hoe je spelers kunt aanmoedigen om taken te voltooien, pass-ervaringpunten (XP) te verdienen en door beloningsniveaus te klimmen, zie [Seizoenpasontwerp](/docs/nl-nl/production/game-design/season-pass-design) .

## [Verkrijg pakket](#verkrijg-pakket)[](#verkrijg-pakket)

De Creator Store  is een tabblad van de Toolbox  dat je kunt gebruiken om alle assets te vinden die zijn gemaakt door Roblox en de Roblox-gemeenschap voor gebruik binnen jouw projecten, inclusief model-, afbeelding-, mesh-, audio-, plugin-, video- en lettertype-assets. Je kunt de Creator Store gebruiken om een of meer assets rechtstreeks in een open game toe te voegen, inclusief functiepakketten!

Elk functiepakket vereist het Core  functiepakket om goed te functioneren, en het Seizoenpassen  pakket vereist het Missions  functiepakket om de missies van een seizoen te definiëren. Zodra alle drie de pakketassets in jouw inventaris zijn, kun je ze hergebruiken in elk project op het platform.

Om de pakketten van jouw inventaris naar jouw game te krijgen:

1.

Voeg de Core , Missions  en Seizoenpassen  pakketten toe aan jouw inventaris binnen Studio door op de Toevoegen aan Inventaris  link in de volgende set componenten te klikken.

[

#### Core Feature Package

Het Core Feature Package biedt gedeelde datastore tabel logica voor alle functiepakketten.

](https://create.roblox.com/store/asset/94918533221001)

Toevoegen aan inventaris

[

#### Missions Feature Package

Het Missions Feature Package biedt functionaliteit om missies te creëren die spelers kunnen voltooien om beloningen te behalen en vooruitgang te boeken in jouw game.

](https://create.roblox.com/store/asset/89760436366160)

Toevoegen aan inventaris

[

#### Seizoenpassen Feature Package

Het Seizoenpassen Feature Package biedt functionaliteit om een beperkte tijd, op missies gebaseerd voortgangssysteem te creëren dat spelers kunnen voltooien om beloningen te verdienen.

](https://create.roblox.com/store/asset/89781974928804)

Toevoegen aan inventaris

2.

Open het [Toolbox](/docs/nl-nl/projects/assets/toolbox)  vanuit het Venster  menu of de Start  tabbladwerkbalk in Studio.

3.

In het Toolbox  venster, klik op het Inventaris  tabblad. De Mijn Modellen  sortering wordt weergegeven.

 ![Het Toolbox venster van Studio met het Inventaris tabblad gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/studio/toolbox/Inventory-Tab.png)

4.

Klik op de tegel Feature Package Core , de tegel Missions Feature Package , en vervolgens de tegel Seizoenpassen Feature Package . Alle drie de pakketmappen worden weergegeven in het Explorer  venster.

5.

Sleep de pakketmappen naar [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) .

6.

Sta datastore-aanroepen toe om de aankopen van spelers met de pakketten bij te houden.

1.

Open het Bestand  ⟩ Ervaringsinstellingen  venster in Studio.

2.

Navigeer naar het Beveiliging  tabblad, en schakel vervolgens Studio-toegang tot API-services inschakelen  in.

## [Configureer missie-afhankelijkheden](#configureer-missie-afhankelijkheden)[](#configureer-missie-afhankelijkheden)

Om seizoenen goed te laten functioneren, moet je logica toevoegen zodat het Seizoenpassen  functiepakket de voortgang van spelers kan bijhouden en zijn UI-componenten kan bijwerken. Voor de eenvoud gebruikt het onderstaande voorbeeld het Missions  functiepakket en roept SeasonPasses.addProgressToSeason()  aan nadat spelers missies hebben voltooid, maar je kunt de voortgang van spelers op elke gewenste manier bijhouden. Of je nu missies definieert of niet, je moet nog steeds het Missions  functiepakket aan jouw game toevoegen zodat de Seizoenpassen  code kan functioneren.

Missies hebben elk een set taken die moeten worden voltooid om de missie te voltooien, configuratieopties en optionele weergavemetadata. Voor een uitgebreide handleiding over hoe je missies en hun taken kunt configureren, zie [Definieer missies](/docs/nl-nl/resources/feature-packages/missions#definieer-missies) .

### [Voeg XP van missies toe aan seizoenen](#voeg-xp-van-missies-toe-aan-seizoenen)[](#voeg-xp-van-missies-toe-aan-seizoenen)

Dit voorbeeld gebruikt het Missions  functiepakket om missies te definiëren die spelers kunnen voltooien om ervaring (XP) te verdienen en door het seizoen te vorderen. Om spelers XP toe te kennen wanneer ze een gedefinieerde missie voltooien, moet je logica toevoegen aan het ReplicatedStorage.Missions.Server.Examples.MissionsExample  server script zodat het seizoenpasgegevens kan importeren en spelers kan belonen op basis van hun voortgang.

```

local SeasonPasses = require(ReplicatedStorage.SeasonPasses.Server.SeasonPasses)

local function completeHandler(player: Player, missionId: Types.MissionId)

	print(`{player} voltooide missie {missionId}`)

	if missionId == "Walking" then

		SeasonPasses.addProgressToSeason(player, 100)

	end

	if missionId == "Walking2" then

		SeasonPasses.addProgressToSeason(player, 100)

	end

	if missionId == "Walking3" then

		SeasonPasses.addProgressToSeason(player, 100)

	end

	if missionId == "Availability" then

		SeasonPasses.addProgressToSeason(player, 100)

	end

	if missionId == "Manual" then

		SeasonPasses.addProgressToSeason(player, 100)

	end

	if missionId == "Minutely" then

		SeasonPasses.addProgressToSeason(player, 100)

	end

end

```

### [Voeg seizoentier beloningsiconen toe](#voeg-seizoentier-beloningsiconen-toe)[](#voeg-seizoentier-beloningsiconen-toe)

Naast het toekennen van XP aan spelers wanneer ze missies voltooien, gebruikt het Seizoenpassen  functiepakket het Missions  functiepakket om unieke beloningsniveaus binnen een seizoen te definiëren. Als je een on-screen icoon wilt toevoegen voor een tierbeloning die spelers kunnen verdienen als ze genoeg XP hebben, voeg dan een asset-ID toe in de Missions  configuratie voor elke seizoentierbeloning.

```

Tier3Mission = {

		categoryId = "Algemeen",

		metadata = {

			displayName = "Tier 3 Missie",

			description = "Spring 10 keer",

			visibleAfterComplete = true,

			visibleBeforeUnlocked = true,

			rewards = {

				{

					icon = 16826775737,

					displayName = "Item",

				},

				{

					icon = 106912146245070,

					displayName = "Seizoen XP",

				},

			},

		},

	}

```

## [Configureer seizoenen](#configureer-seizoenen)[](#configureer-seizoenen)

Nadat je elke missie hebt ingesteld die je in een seizoen wilt opnemen, is het tijd om de seizoenpas zelf te configureren. In ReplicatedStorage.SeasonPasses.Configs.Season  is er een voorbeeld van een seizoensconfiguratie ter referentie, en de volgende codevoorbeelden zijn uit dat bestand.

### [Definieer passen](#definieer-passen)[](#definieer-passen)

[Passen](/docs/nl-nl/production/monetization/passes)  stellen je in staat om spelers een eenmalige Robux-kosten in rekening te brengen om toegang te krijgen tot de missies en potentiële beloningen van een seizoenpas. Nadat je een pas hebt gemaakt met een unieke asset-ID, kun je de details van de pas instellen in het premiumTrack  veld van jouw seizoen. Bijvoorbeeld, het volgende codevoorbeeld definieert een pas met een voorbeeld asset-ID van 928192647  om een seizoenpas voor te stellen, en geeft de seizoenpas een tracknaam van "Premium Track".

```

premiumTrack = {

        pricing = {

            gamePassId = 928192647,

        },

        trackMetadata = {

            trackName = "Premium Track",

        },

    },

```

Om de aankoop van de premium pas te testen, evenals hoe de aankoop de seizoen beïnvloedt, moet je de game publiceren naar Roblox en testen in de client. Studio simuleert geen pasaankopen.

### [Configureer niveaus en beloningen](#configureer-niveaus-en-beloningen)[](#configureer-niveaus-en-beloningen)

Seizoenniveaus vertegenwoordigen de mijlpalen die spelers moeten bereiken om beloningen te verdienen gedurende een seizoen. Om door de niveaus te klimmen, voltooien spelers missies om XP te verdienen, en wanneer ze genoeg XP verdienen, promoveren ze naar het volgende niveau en ontvangen ze beloningen voor het niveau dat ze net hebben voltooid. Niveaus hebben een upperBoundXP  eigenschap die de drempel van XP instelt die nodig is om de beloningen voor een niveau te claimen. Elk niveau kan twee soorten beloningen bieden:

-

Gratis  - Een beloning die spelers kunnen verdienen zonder de seizoenpas aan te schaffen.

-

Premium  - Een beloning die spelers alleen kunnen verdienen door de seizoenpas aan te schaffen.

Om dit te demonstreren, bekijk het volgende codevoorbeeld voor een seizoen met één niveau dat 100 XP vereist om een gratis ijslanzenbeloning en een premium explosiebeschermingsbeloning te verdienen. De icon  is de asset-ID van de UI-afbeelding die voor een beloning moet worden weergegeven, en de displayName  toont een naam voor de beloning. Let op dat de displayName  in de UI wordt weergegeven, maar de rewardId  is verborgen voor de speler en wordt voornamelijk gebruikt voor [datastore](/docs/nl-nl/cloud-services/data-stores)  doeleinden.

```

tiers = {

        [1] = {

            upperBoundXP = 100,

            freeReward = {

                icon = 128181721602852,

                displayName = "Ijslanze",

                rewardId = "iceLance",

            },

            premiumReward = {

                icon = 95882371958115,

                displayName = "Explosiebescherming",

                rewardId = "blastShield",

            },

        },

    }

```

Hoewel dit script ter illustratie is van hoe je één niveau tegelijk kunt configureren, bevatten de meeste seizoenen meer dan één niveau. Terwijl je meerdere niveaus en beloningen voor een seizoen definieert, zorg ervoor dat elke rewardId  numeriek is en in oplopende volgorde, zodat jouw niveaus worden weergegeven in de volgorde die je in de niveaulijst hebt gedefinieerd.

### [Definieer seizoensdetails](#definieer-seizoensdetails)[](#definieer-seizoensdetails)

Nu je een seizoenpas hebt met niveaus en beloningen, is het tijd om de details van jouw seizoen te definiëren:

-

title  - De naam van jouw seizoen.

-

description  - De beschrijving van jouw seizoen.

-

startUtc  - Het begin van het seizoen in gecoördineerde universele tijd.

-

endUtc  - Het einde van het seizoen in gecoördineerde universele tijd.

-

seasonId  - Hiermee kun je de XP bijhouden die een speler gedurende het gegeven seizoen verwerft.

Het pakket gebruikt startUtc  en endUtc  om de aftelling van het seizoen weer te geven.

```

startUtc = DateTime.fromUniversalTime(2024, 10, 01, 17, 0, 0),

endUtc = DateTime.fromUniversalTime(2025, 2, 28, 17, 0, 0),

title = "Seizoen 1",

description = "Naar Ruimte Stad",

seasonId = "season1",

```

## [Integreer serverlogica](#integreer-serverlogica)[](#integreer-serverlogica)

Bekijk ReplicatedStorage.SeasonPasses.Server.Examples.SeasonPassesExample , dat laat zien hoe jouw server zal interageren met het Seizoenpassen Feature Package . De onderstaande snippet is uit dat script.

Je moet voornamelijk een handlerfunctie maken voor het toekennen van geclaimde beloningen aan jouw spelers. Bijvoorbeeld, het volgende codevoorbeeld creëert een rewardClaimedHandlerFunction()  functie die bijhoudt wanneer spelers naar het volgende niveau vorderen, en hen dan ofwel alleen de gratis beloning, of zowel de gratis als premium beloningen toekent als ze de seizoenpas hebben aangeschaft.

Voor jouw doeleinden, vervang de [task.wait()](/docs/nl-nl/reference/engine/libraries/task#wait)  aanroep door logica die spelers in staat stelt om de beloningen te krijgen die ze in het seizoen hebben geclaimd. Deze functie moet  een boolean retourneren: true als de server de beloning heeft toegekend, false als dat niet het geval was.

```

local function rewardClaimedHandlerFunction(_player: Player, _rewardId: Types.RewardId): boolean

	task.wait(2)

	return true

end

local function initializeRewardClaimedHandlers()

	for tierId, tier in pairs(Season.tiers) do

		if tier then

			if tier.freeReward then

				SeasonPasses.setRewardClaimedHandler(tier.freeReward.rewardId, rewardClaimedHandlerFunction)

			end

			if tier.premiumReward then

				SeasonPasses.setRewardClaimedHandler(tier.premiumReward.rewardId, rewardClaimedHandlerFunction)

			end

		end

	end

end

```

## [Configureer constanten](#configureer-constanten)[](#configureer-constanten)

Constanten voor het Core  functiepakket bevinden zich op twee plaatsen:

-

Gedeelde constanten bevinden zich in ReplicatedStorage.FeaturePackagesCore.Configs.SharedConstants .

-

Pakket-specifieke constanten, in dit geval het Seizoenpassen  functiepakket, bevinden zich in ReplicatedStorage.SeasonPasses.Configs.Constants . De belangrijkste dingen die je mogelijk wilt aanpassen om aan de ontwerpeisen van jouw game te voldoen:

-

Geluidsasset-ID's

-

Aankoop effectduur en deeltjeskleuren Bovendien kun je strings voor vertaling vinden die zijn ondergebracht in één locatie: ReplicatedStorage.FeaturePackagesCore.Configs.TranslationStrings .

## [Pas UI-componenten aan](#pas-ui-componenten-aan)[](#pas-ui-componenten-aan)

Door de pakketobjecten te wijzigen, zoals kleuren, lettertype en transparantie, kun je de visuele presentatie van jouw seizoenpas prompts aanpassen. Houd er echter rekening mee dat als je een van de objecten hiërarchisch verplaatst, de code ze niet kan vinden, en je aanpassingen aan jouw code moet maken.

Een seizoen bestaat uit de volgende hoog-niveau componenten die programatisch worden toegevoegd aan de UI-componenten van het Missions Feature Package :

-

SeasonBottomFrame  – Het frame dat informatie bevat over elk track, een scrollend frame van de beloningen voor niveaus, en niveaugegevens.

-

SeasonDescriptionFrame  - Het frame in de header dat de seizoentitel, beschrijving en aftelling weergeeft.

-

TierRewardFrame  - Het frame dat een specifieke beloning voor een niveau weergeeft.

-

TierProgressFrame  - Het frame dat de voortgang weergeeft die de speler heeft gemaakt naar het huidige niveau waaraan ze werken.

-

PurchaseFrame  - Het frame dat de speler vraagt om een premium pas aan te schaffen.

-

SeasonProgressFrame  - Het frame dat de voortgangsbalk van de speler gedurende het hele seizoen weergeeft.

-

RewardsButtonFrame  - Het frame dat een knop toevoegt waarmee de informatie van het seizoen kan worden weergegeven via het SeasonBottomFrame .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
