<!-- Source: https://create.roblox.com/docs/nl-nl/resources/feature-packages/missions -->

Missiespakket | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Voorbeelden en projecten](/docs/nl-nl/samples)

# Missiespakket

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Dit functiepakket is in bèta.

Het Missies  functiepakket biedt kant-en-klare functionaliteit om missies te creëren die spelers kunnen voltooien om beloningen te behalen en vooruitgang in je spel te boeken. Alle missies moeten een ID, categorie en een lijst van taken hebben die spelers moeten voltooien om de missie te voltooien. De takenlijst kan echter leeg zijn, waardoor de beloningen van de missie onmiddellijk kunnen worden opgeëist.

Met de aanpassingsopties van het pakket kun je alle missies personaliseren om aan je unieke gameplay-eisen te voldoen, zoals:

-

Het creëren van missies die [nieuwe spelers](/docs/nl-nl/production/game-design/onboarding)  in je spel inwerken en de [D1-retentie](/docs/nl-nl/production/game-design/analytics-essentials#retention-metrics)  verbeteren.

-

Het richten op [D7- en D30-retentie](/docs/nl-nl/production/game-design/analytics-essentials#retention-metrics)  door middel- tot langetermijndoelen en een gevoel van vooruitgang toe te voegen.

-

Het verhogen van [betrokkenheid](/docs/nl-nl/production/game-design/analytics-essentials#engagement-metrics)  door de verschillende systemen in je spel naar voren te brengen en spelers te belonen voor interactie ermee.

 ![](https://prod.docsiteassets.roblox.com/assets/resources/feature-packages/Missions/Missions-Intro.png)

Voor informatie over hoe je spelers frisse doelen en prikkels kunt bieden zodat ze gemotiveerd zijn om langer te spelen en hun betrokkenheid te vergroten, zie [Inleiding tot Questontwerp](/docs/nl-nl/production/game-design/introduction-to-quest-design) .

## [Verkrijg pakket](#verkrijg-pakket)[](#verkrijg-pakket)

De Creator Store  is een tabblad van de Toolbox  dat je kunt gebruiken om alle assets te vinden die zijn gemaakt door Roblox en de Roblox-gemeenschap voor gebruik binnen je projecten, inclusief model-, afbeelding-, mesh-, audio-, plugin-, video- en lettertype-assets. Je kunt de Creator Store gebruiken om een of meer assets rechtstreeks in een open spel toe te voegen, inclusief functiepakketten!

Elk functiepakket vereist het Core  functiepakket om goed te functioneren. Zodra de Core  en Missions  functiepakket-assets in je inventaris zijn, kun je ze hergebruiken in elk project op het platform.

Om de pakketten van je inventaris naar je spel te krijgen:

1.

Voeg de Core  en Missions  toe aan je inventaris binnen Studio door op de link Toevoegen aan Inventaris  in de volgende set componenten te klikken.

[

#### Core Functiepakket

Het Core functiepakket biedt gedeelde datastores voor alle functiepakketten.

](https://create.roblox.com/store/asset/94918533221001)

Toevoegen aan inventaris

[

#### Missies Functiepakket

Het Missies Functiepakket biedt functionaliteit om missies te creëren die spelers kunnen voltooien om beloningen te behalen en vooruitgang in je spel te boeken.

](https://create.roblox.com/store/asset/89760436366160)

Toevoegen aan inventaris

2.

Open het [Toolbox](/docs/nl-nl/projects/assets/toolbox)  vanuit het Venster  menu of de werkbalk van het Start  tabblad in Studio.

3.

Klik in het Toolbox  venster op het tabblad Inventaris . De sortering Mijn Modellen  wordt weergegeven.

 ![Studio's Toolbox venster met het Inventaris tabblad gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/studio/toolbox/Inventory-Tab.png)

4.

Klik op de tegel Functiepakket Core , en vervolgens op de tegel Missies Functiepakket . Beide pakketmappen worden weergegeven in het Explorer  venster.

5.

Sleep de pakketmappen naar [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) .

## [Definieer missies](#definieer-missies)[](#definieer-missies)

Elke voltooibare missie omvat een set taken die moeten worden voltooid om de missie te voltooien, configuratieopties en optionele weergavemetadata, die allemaal kunnen worden gedefinieerd binnen ReplicatedStorage.Missions.Configs.Missions , met types geëxporteerd vanuit het Types  script in dezelfde map.

### [Vereiste velden](#vereiste-velden)[](#vereiste-velden)

De volgende velden zijn vereist voor elke missie.

| Naam | | Type | | Beschrijving |
| --- | --- |
| missionId | | string | | De belangrijkste sleutel van de Missies-tabel. Alle missies worden geïdentificeerd door hun eigen unieke string. |
| categoryId | | string | | Missies moeten tot een categorie behoren en worden in de UI per categorie gegroepeerd. |
| tasks | | table | | Een lijst van taken die de speler moet voltooien om de missie te voltooien. |

### [Ontgrendelvoorwaarden](#ontgrendelvoorwaarden)[](#ontgrendelvoorwaarden)

Standaard worden missies automatisch ontgrendeld voor spelers en kunnen ze precies één keer worden voltooid. Je kunt echter de volgende optionele  configuratieopties gebruiken om dit gedrag te wijzigen.

| Naam | | Type | | Beschrijving |
| prerequisites | | table | | Een lijst van andere missionIds die moeten worden voltooid voordat de missie kan worden ontgrendeld. |
| manualOnly | | bool | | Schakelt de automatische ontgrendeling van de missie uit. In plaats daarvan moet een functie worden aangeroepen om de missie te ontgrendelen. Andere ontgrendelvoorwaarden moeten ook worden vervuld. |
| availableAfterUtc | | bool | | De missie kan niet worden ontgrendeld voor de opgegeven tijd in UTC. |
| availableBeforeUtc | | bool | | De missie kan niet worden ontgrendeld na de opgegeven tijd in UTC. Als deze is ontgrendeld maar niet is voltooid voor deze tijd, zal de missie falen. |
| repeatable | | bool | | De missie wordt opnieuw ontgrendeld nadat deze is voltooid. |
| repeatLimit | | number | | Als de missie herhaalbaar is, kan deze niet meer dan dit aantal keren worden herhaald. |
| repeatCooldownSeconds | | number | | Als de missie herhaalbaar is, is er een vertraging voordat deze opnieuw wordt ontgrendeld. |
| expireSeconds | | number | | Als de missie is ontgrendeld en niet is voltooid binnen het opgegeven aantal seconden, zal deze in plaats daarvan falen. |
| expireCountOffline | | bool | | Als de missie expireSeconds  heeft en expireCountOffline  is ingesteld op waar, telt de tijd terwijl de speler niet daadwerkelijk in het spel is mee voor de vervaldatum van de missie. |

### [Metadata](#metadata)[](#metadata)

Missies hebben metadata die specificeert hoe ze worden weergegeven in de gebruikersinterface van de Missies. Je kunt de volgende optionele  velden gebruiken om de metadata aan te passen.

| Naam | | Type | | Beschrijving |
| displayName | | string | | Een naam die voor de missie in de gebruikersinterface wordt weergegeven in plaats van de missionId . |
| description | | string | | Een langere tekstblok dat aanvullende informatie of context over de missie biedt. |
| visibleAfterComplete | | bool | | Als ingesteld op waar, verschijnt de missie in de lijst van missies, zelfs nadat deze is voltooid, maar gemarkeerd als voltooid. |
| visibleAfterFailed | | bool | | Als ingesteld op waar, verschijnt de missie in de lijst van missies, zelfs nadat deze is mislukt, maar gemarkeerd als mislukt. |
| visibleBeforeUnlocked | | bool | | Als ingesteld op waar, is de missie zichtbaar maar vergrendeld in de lijst van missies voordat deze beschikbaar is voor voltooiing. |
| invisibleWhileActive | | bool | | Als ingesteld op waar, is de missie onzichtbaar, zelfs terwijl deze actief in uitvoering is. |
| rewards | | table | | Een lijst van beloningsweergave-informatie.
-

assetID  (number ) - De afbeelding ID die wordt weergegeven in de gebruikersinterface van de missies onder de beloningen voor een quest. Dit is vereist als er een beloning aanwezig is.

-

displayName  (string ) - De naam die wordt weergegeven in de gebruikersinterface van de missies onder het pictogram.

 |

## [Definieer taken](#definieer-taken)[](#definieer-taken)

Elke missie kan nul of meer taken hebben. Als een missie nul taken heeft, kan deze onmiddellijk worden opgeëist nadat deze is ontgrendeld; als een missie een of meer taken heeft, kan de speler, zodra de taken zijn voltooid, eventuele beloningen die aan de missie zijn gekoppeld, verzamelen. Elke taak heeft een taskId , wat de sleutel is die aan de taak voor een gegeven missie is gekoppeld.

Taken komen in twee types:

-

Tijdgebonden Taken  - Hiermee kun je de taak op verschillende tijdstippen starten en stoppen. Er moet een bepaalde hoeveelheid tijd verstrijken terwijl de timer van de taak loopt, dan is de taak voltooid.

-

Aantal Taken  - Hiermee kun je de voortgang van de taak verhogen of instellen. Wanneer de voortgang een bepaalde waarde bereikt, is de taak voltooid.

Beide taaktypes delen de volgende velden:

| Naam | | Type | | Beschrijving |
| taskType | | string | | Geeft aan of het taaktype tellen of tijdgebonden is. |
| counter | | object | | (Optioneel) De teller die deze taak bijhoudt. Tellers zijn speler-specifieke persistente opslag voor een nummer of een timer. Meerdere taken kunnen een enkele teller bijhouden; bijvoorbeeld, als meer dan één taak bijhoudt hoeveel munten een speler heeft verzameld, kunnen ze allemaal dezelfde “munten” teller delen. Deze taken kunnen onafhankelijk nieuwe verzamelde munten bijhouden, beginnend vanaf nul, of doorgaan met tellen vanaf de waarde van de teller (alle munten die al zijn verzameld).
-

counterId  (string ) - De ID van de te volgen teller. Gebruik deze ID om de waarde van de teller te krijgen of in te stellen.

-

continueFromCounter  (Optionele bool ) - Als ingesteld op waar, zal de voortgang van de taak direct overeenkomen met de waarde van de teller in plaats van de hoeveelheid die is toegenomen.

 |
| metadata | | object | | (Optioneel) Informatie over hoe de taak in de gebruikersinterface wordt weergegeven.
-

displayName  (string ) - Naam van de taak, gebruikt wanneer deze in de gebruikersinterface wordt weergegeven.

-

numericType  (Optionele string ) - hoe het voortgangsnummer in de taak moet worden weergegeven.
-

Breuk, bijv. 5/10 of 5k/50k

-

Percentage, bijv. 50% of 10%

-

LongFraction, bijv. 5/10 of 5000/50000

-

Boolean, bijv. Incompleet

 |
| callToAction | | object | | (Optioneel) Een knop die een callbackfunctie activeert.
-

callback  (function ) - Functie die wordt geactiveerd door de callToAction  knop.

-

buttonText  (string ) - De tekst die in de knop gebruikersinterface wordt weergegeven.

 |

### [Aantal taken velden](#aantal-taken-velden)[](#aantal-taken-velden)

Aantal taken hebben een vereiste waarde. Wanneer de voortgang van de taak deze hoeveelheid bereikt, is de taak voltooid.

| Naam | | Type | | Beschrijving |
| goalCount | | number | | (Optioneel) De voortgang die vereist is om de taak te voltooien. |

### [Tijdtaken velden](#tijdtaken-velden)[](#tijdtaken-velden)

Tijdtaken hebben een doelbedrag aan tijd die moet worden besteed, en worden gestart en gestopt. Wanneer het doelbedrag aan tijd is bereikt, is de taak voltooid.

| Naam | | Type | | Beschrijving |
| goalSeconds | | number | | Het aantal seconden dat moet verstrijken om de taak te voltooien. |
| startImmediately | | bool | | Als de taak moet beginnen met het tellen van tijd zodra deze is ontgrendeld, in plaats van alleen nadat deze is gestart. |
| includesOfflineTime | | bool | | Als de taak de tijd moet omvatten die is besteed terwijl de speler niet actief in het spel is. |

## [Configureer categorieën](#configureer-categorieën)[](#configureer-categorieën)

Categorieën hoeven niet expliciet te worden gedefinieerd om te worden gebruikt, aangezien de categorie voor een missie standaardwaarden heeft die zullen worden gebruikt. Je kunt deze waarden echter configureren in ReplicatedStorage.Missions.Configs.Categories  om extra effecten aan de categorie toe te voegen. Categorieën worden geïdentificeerd door unieke CategoryIds , dezelfde als die in de missiesconfiguratie worden genoemd.

| Naam | | Type | | Beschrijving |
| repeatDelaySeconds | | number | | (Optioneel) Als ingesteld, worden alle missies in de categorie gereset elke keer dat de opgegeven tijd verstrijkt, en kunnen ze opnieuw worden ontgrendeld, voltooid en hun beloningen opnieuw worden opgeëist. Dit is apart van herhaalbare missies, die herhaalbaar zijn binnen een gegeven categorie herhaling. |

## [Integreer serverlogica](#integreer-serverlogica)[](#integreer-serverlogica)

Bekijk ReplicatedStorage.Missions.Server.Examples.MissionsExample , dat laat zien hoe je server zal interageren met het Missies  functiepakket.

Je moet voornamelijk vier dingen aansluiten zodra je het Missies  functiepakket in je spel sleept:

1.

Definieer missies in je missiesconfiguratie.

2.

Voeg logica toe aan je spel om de voortgang van taken of de tellers waarmee de voortgang is verbonden bij te werken.

README

```

-- Verhoogt de voortgang op een missie Jumping met een Jumps-taak

Missions.addProgressToTask(player, "Jumping", "Jumps", 1)

-- Start de timer op een missie BattlingTime met een TimeInBattle-taak

Missions.startTimedTask(player, "BattlingTime", "TimeInBattle")

-- Stop de timer op een missie BattlingTime met een TimeInBattle-taak

Missions.stopTimedTask(player, "BattlingTime", "TimeInBattle")

-- Verhoogt de voortgang op alle taken die aan de Jumps-teller zijn gekoppeld

CounterSystem.addCounter(player, "Jumps", 1)

-- Start de timer op alle tijdgebonden taken die aan de TimeInBattle-teller zijn gekoppeld

CounterSystem.startTimer(player, "TimeInBattle")

-- Stop de timer op alle tijdgebonden taken die aan de TimeInBattle-teller zijn gekoppeld

CounterSystem.stopTimer(player, "TimeInBattle")

```

3.

Stel handlers voor het voltooien van missies in, en optioneel ontgrendel- of faalhandlers. Gebruik de voltooiingshandler om de beloningen van de missie in je spel toe te kennen.

README

```

local function completeHandler(player: Player, missionId: Types.MissionId)

     print(`{player} voltooide missie {missionId}`)

     -- Ken de beloningen van de speler toe.

 end

Missions.setCompletionHandler(missionId, completeHandler)

```

4.

Ontgrendel missies die niet automatisch worden ontgrendeld. De logica van het Missies  functiepakket zorgt ervoor dat aan alle vereisten voor de missie is voldaan voordat de missie is voltooid en de beloningen kunnen worden verzameld.

README

```

Missions.unlockMission(player, "Manual")

```

## [Configureer constanten](#configureer-constanten)[](#configureer-constanten)

Constanten voor het Core  functiepakket bevinden zich op twee plaatsen:

-

Gedeelde constanten bevinden zich in ReplicatedStorage.FeaturePackagesCore.Configs.SharedConstants .

-

Pakket-specifieke constanten, in dit geval het Missies  functiepakket, bevinden zich in ReplicatedStorage.Missions.Configs.Constants .

Daarnaast kun je strings voor vertaling vinden die zijn ondergebracht in één locatie: ReplicatedStorage.FeaturePackagesCore.Configs.TranslationStrings .

## [Pas UI-componenten aan](#pas-ui-componenten-aan)[](#pas-ui-componenten-aan)

Door de pakketobjecten te wijzigen, zoals kleuren, lettertype en transparantie, kun je de visuele presentatie van je missies UI aanpassen. Bijvoorbeeld, in ReplicatedStorage.Missions.Configs.Constants , kun je SingleTaskMode  inschakelen om een voortgangsbalk voor een taak direct op de missie zelf weer te geven voor missies die slechts één taak hebben.

Als je een van de objecten hiërarchisch verplaatst, kan de code ze niet vinden, en moet je aanpassingen maken in MissionsUI .

Bovendien, als je spel al een bestaande UI heeft die je wilt integreren met het Missies  functiepakket, bevat de client [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  MissionsClient  alle functies die nodig zijn om de informatie over de missies van een speler van de server te verzenden.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
