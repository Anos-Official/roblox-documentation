<!-- Source: https://create.roblox.com/docs/nl-nl/production/publishing/publish-games-and-places -->

Maak en publiceer games en plaatsen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Projecten](/docs/nl-nl/projects)
6. /
7. [Games and places](/docs/nl-nl/production/publishing/publish-games-and-places)

# Maak en publiceer games en plaatsen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Wanneer je Studio opent en een nieuwe game maakt, begint je project met een enkele plaats  waar spelers in laden wanneer ze voor het eerst de game betreden. Games kunnen één of meerdere plaatsen hebben die elk alle componenten voor dat deel van de game bevatten, inclusief de specifieke omgeving, 3D-objecten en scripts.

Plaatsen zijn vergelijkbaar met scènes in Unity of kaarten in Unreal Engine.

Veel makers creëren extra plaatsen binnen een game om middelen voor verschillende gameplay-gebieden te organiseren. Bijvoorbeeld, als je wilt dat spelers zich bij een kerker voegen voordat ze [teleporteren](/docs/nl-nl/projects/teleport)  naar een uitgestrekte woestijn of een spookachtig eiland, kun je de middelen voor elk gebied in hun eigen plaats organiseren.

![](https://prod.docsiteassets.roblox.com/assets/publishing/experiences-places-assets/Experience-Hierarchy.png)

Elke plaats wordt vertegenwoordigd door een datamodel dat opslaat en organiseert:

-

Alle objecten die de 3D-wereld van een plaats vormen, zoals delen, meshes, terrein en verlichting.

-

Alle objecten die het runtime-gedrag kunnen beheersen, zoals scripts.

Het begrijpen van zowel de algemene structuur van het datamodel van een plaats als hoe de Roblox-engine het gebruikt als de bron van waarheid voor de status van een plaats is belangrijk om te begrijpen waar je verschillende soorten objecten kunt opslaan en configureren. Voor meer informatie, zie [datamodel](/docs/nl-nl/projects/data-model) .

## [Maak games](#maak-games)[](#maak-games)

Wanneer je een nieuwe game maakt, opent deze een startplaats waar alle spelers in laden wanneer ze de game betreden. De startplaats vertegenwoordigt de algehele game totdat je extra plaatsen toevoegt voor verschillende gameplay-gebieden.

Om een game te maken:

1.

Open Studio.

2.

In de sectie Open een sjabloon , selecteer een sjabloon met de objecten waarmee je wilt beginnen voor je game, zoals:

-

Basisplaat  — Begint met een [SpawnLocation](/docs/nl-nl/reference/engine/classes/SpawnLocation)  en een basisplaat.

-

Platformer  — Begint met aanpasbare platforms, muntophalingen, en dubbele sprongen, dashen, rollen en lange sprong karaktermechanica!

-

Racen  — Begint met een werkende raceauto en aanpasbare baanobjecten.

Wanneer Studio het sjabloon opent, heb je nu Place1  dat je algehele game vertegenwoordigt.

## [Publiceer games](#publiceer-games)[](#publiceer-games)

Wanneer je een game publiceert, slaat Roblox het datamodel van je startplaats op als een .rblx -bestand in de cloud. Dit is een belangrijk proces omdat het de game verbindt met je account, waardoor je er vanaf elke computer toegang toe hebt en eraan kunt werken.

Standaard zijn nieuwe games alleen toegankelijk voor jou als maker, gebruikers met Bewerken -toegang en groepsleden met de juiste [rollen en machtigingen](/docs/nl-nl/projects/groups#rollen-en-machtigingen) . Wanneer je klaar bent om live te gaan voor iedereen, kun je [je game aan het publiek uitbrengen](#breng-games-uit)  en [je doelgroep specificeren](#doelgroep) .

Wanneer je games maakt en samenwerkt als onderdeel van een [groep](/docs/nl-nl/projects/groups) , is de mogelijkheid voor groepsleden om games te playtesten/bewerken/publiceren, standaard afhankelijk van hun rolmachtigingen. Groepsleden of eigenaren met voldoende machtigingen kunnen echter de toegang per game aanpassen. Voor meer informatie, zie [Configureer games](/docs/nl-nl/projects/configure-games) .

Om een game voor de eerste keer te publiceren:

1.

In de linkerbovenhoek van je computer, navigeer naar Bestand  > Publiceren . Het venster Game details  wordt weergegeven.

 ![](https://prod.docsiteassets.roblox.com/assets/publishing/Games-Details.png)

2.

In het venster:

1.

Upload een [pictogram](/docs/nl-nl/production/publishing/experience-icons)  en [thumbnail](/docs/nl-nl/production/publishing/thumbnails)  om weer te geven op de hoofdpagina van de details van je game.

2.

Vul in het veld Naam  de naam van je game in.

3.

Vul in het veld Promotionele tekst  optionele tekst in om korte secundaire informatie weer te geven. Dit is een [bètafunctie](https://devforum.roblox.com/t/beta-promotional-text/4973915) . Tijdens de bèta kunnen de plaatsingen van promotionele tekst in het product veranderen.

4.

Stel de dropdownmenu's Genre  en de optionele Subgenre  in op welk type gameplay spelers kunnen verwachten. Voor meer informatie, zie [Genres](/docs/nl-nl/production/publishing/experience-genres) .

5.

Vul in het veld Beschrijving  een samenvatting in van wat spelers van je game kunnen verwachten.

6.

Klik op de knop Opslaan . Roblox publiceert je game naar de cloud met een unieke UniverseID .

 ![](https://prod.docsiteassets.roblox.com/assets/publishing/Publish.png)

3.

OPTIONEEL

 Je kunt [vroegere testers uitnodigen](#nodig-vroege-testers-uit)  om je game te previewen.

Metadata best practices

De naam en beschrijving van je game creëren een belangrijke eerste indruk en dragen bij aan hoe gemakkelijk spelers je game kunnen vinden via Roblox's dynamische [ontdekkings](/docs/nl-nl/discovery)  systemen.

#### Game naam

Alle games moeten voldoen aan de volgende best practices voor naamgeving:

-

Houd de naam consistent  – Het te vaak hernoemen van een game vermindert de kans dat spelers deze kunnen vinden met een eerdere naam.

-

Vermijd spammen  – Frequent herhalen van woorden of zinnen kan leiden tot een lagere ranking van je game.

Obby Madness

Obby Madness OBBY OBBY OBBY OBBY OBBY

-

Gebruik versieringen voorzichtig  – Het versieren van de naam met een of twee goed geplaatste emoji's is niet schadelijk, maar verkeerd geplaatste of overmatige versieringen kunnen spelers verwarren die snel de game willen identificeren.

🌍 Evolution Simulator  🌍

🐒🐬🐊 Ev 🌍 luti 🌍 n Simulator  🌷🍀🌿

#### Game beschrijving

Een goed geschreven beschrijving promoot het genre en de unieke kwaliteiten van je game, terwijl het ook de beste context biedt voor zowel spelers als Roblox's dynamische ontdekkingssystemen.

-

Samenvatten van je game  – Samenvat wat je game inhoudt in de eerste zin, aangezien dit je kans is om de meest nauwkeurige indruk van het genre en de inhoud te presenteren.

Competeer met racers van over de wereld in enkele van de gekste banen die je ooit hebt gezien!

Vecht tegen horden zombies met knuppels, geweren, zwaarden en een heleboel wapens die verborgen zijn in uitdagende doolhoven.

-

Bied sleutelwoorden aan  – Voeg alle sleutelwoorden toe die relevant kunnen zijn voor je game. Dit maakt het gemakkelijker voor spelers en Roblox om de thema's en genres die in je game worden gepresenteerd te begrijpen.

Hou je van een sheriff ? Sluit je aan en bevrijd onze stad van dieven  en boeven ! Arresteer  de slechteriken, gooi ze in de gevangenis , en heb zelfs een wapens -blazende schietpartij  buiten de saloon.

Open je eigen restaurant , maak heerlijke eten , krijg veel klanten , en breid uit! Verdien ervaring onderweg en leer meer recepten . Als je van koken  en het starten van je eigen bedrijf  houdt, is dit je kans om een tycoon  te worden!

-

Vermijd spammen  – Vermijd het herhalen van sleutelwoorden of het toevoegen van irrelevante sleutelwoorden. Dit kan leiden tot een lagere ranking van je game.

Speel onze leuke granny obby game. Obby obby obby obby obby obby obby adopt me bloxburg arsenal ninja legends parkour tycoon battle disaster survival super hero simulator run jump gun rpg pokemon wild west space alien piggy baldi granny murder mystery prison life jail break mario zelda dungeon quest.

Roblox ondersteunt plaatsen tot 100 MB (104.857.600 bytes). Boven deze limiet kunnen Opslaan naar Roblox  en Publiceren naar Roblox  mislukken. De gegevens die Studio naar Roblox uploadt, zijn iets kleiner dan het .rbxl -bestandsformaat, dus je kunt je plaats exporteren naar .rbxl  om een idee van de grootte te krijgen.

Zeer weinig plaatsen, zelfs de meest complexe, bereiken deze limiet, en wanneer ze dat doen, is het vaak te wijten aan inefficiënties in de plaats. Zie [Probleemoplossing](/docs/nl-nl/projects/place-files#troubleshoot-place-file-size) .

### [Maak extra plaatsen](#maak-extra-plaatsen)[](#maak-extra-plaatsen)

Nadat je je game hebt gepubliceerd, kun je extra plaatsen toevoegen voor verschillende gameplay-gebieden. Om een nieuwe plaats binnen een bestaande game te maken:

1.

Open een bestaand plaatsbestand of maak een nieuwe plaats vanuit een sjabloon in Studio.

2.

Selecteer Bestand  > Publiceer als .

3.

In het venster Publiceer ervaring , klik op de tegel voor de game waaraan je de plaats wilt toevoegen.

4.

Selecteer Toevoegen als een nieuwe plaats , klik vervolgens op Maak .

Of je nu kiest voor een enkele grote plaats of veel kleinere plaatsen is voornamelijk een kwestie van persoonlijke voorkeur. Voor meer informatie, zie [Ontwerp voor prestaties - Streaming en teleportatie](/docs/nl-nl/performance-optimization/design#streaming-en-teleportatie) .

### [Wijzig startplaats](#wijzig-startplaats)[](#wijzig-startplaats)

De startplaats van een game kan niet onmiddellijk worden verwisseld met een andere plaats, maar je kunt de huidige startplaats overschrijven.

Om de startplaats te wijzigen:

1.

OPTIONEEL

 Sla je huidige  startplaats op als een .rbxl -bestand of naar een nieuwe plaats binnen de game.

2.

Navigeer naar het [Creator Dashboard](https://create.roblox.com/dashboard/creations)  en selecteer de game met de startplaats die je wilt wijzigen.

3.

In de navigatie aan de linkerkant, navigeer naar Configuraties  > Plaatsen .

4.

Klik op Bewerken in Studio  voor de beoogde nieuwe  startplaats. Studio opent en laadt die specifieke plaats.

 ![](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Experience-Change-Start-Place.png)

5.

In de linkerbovenhoek van Studio, ga naar Bestand  > Publiceer als .

Selecteer niet Publiceren  omdat dit de plaats over zichzelf zou publiceren.

6.

Klik op de tegel voor dezelfde game, kies vervolgens de huidige  startplaats. Klik op Overschrijven .

 ![](https://prod.docsiteassets.roblox.com/assets/publishing/experiences-places-assets/Publish-Window-Select-Start-Place.png)

7.

OPTIONEEL

 Als de game live is, is het aan te raden om de [servers opnieuw op te starten](/docs/nl-nl/projects/update-games#servers-opnieuw-opstarten) .

### [Nodig vroege testers uit](#nodig-vroege-testers-uit)[](#nodig-vroege-testers-uit)

Je kunt tot 10 vrienden van vergelijkbare leeftijd uitnodigen om je game te previewen terwijl je deze bouwt. Dit stelt je in staat om vroegtijdige feedback te krijgen voordat  je je game publiekelijk uitbrengt en [inhoudsbeoordelingen](/docs/nl-nl/production/promotion/content-ratings)  ontvangt. Voor een overzicht van welke leeftijdsgroepen je game kunnen previewen op basis van jouw leeftijd, bekijk de volgende tabel. Als je iemand wilt uitnodigen om je game te previewen buiten dat bereik, moet je [vertrouwde vrienden](https://en.help.roblox.com/hc/en-us/articles/37725513985812-Unlocking-trusted-friends)  worden.

| ** Jouw leeftijd** | | ** Vrienden die je kunt toevoegen** | | ** Vertrouwde vrienden die je kunt toevoegen** |
| --- | --- |
| Onder 9 | | N.v.t. | | N.v.t. |
| 9-12 | | 9-15, plus onder-9 vrienden met ouderlijke goedkeuring | | Elke leeftijd, maar onder 9 heeft ouderlijke goedkeuring nodig |
| 13-15 | | 9-17 | | Elke leeftijd, maar onder 9 heeft ouderlijke goedkeuring nodig |
| 16-17 | | 13+ | | Elke leeftijd, maar onder 9 heeft ouderlijke goedkeuring nodig |
| 18+ | | 16+ | | Elke leeftijd, maar onder 9 heeft ouderlijke goedkeuring nodig |

Wanneer vroege testers een game previewen, zien ze een watermerk dat hen vertelt dat ze in een preview zijn en dat de Gemeenschapsnormen nog steeds van toepassing zijn. Bovendien blijven dezelfde in-game rapportage- en veiligheidstools die beschikbaar zijn in gepubliceerde games actief, wat betekent dat elke zorgwekkende inhoud of gedrag nog steeds kan worden gemeld en beoordeeld, ook al heeft de game geen volledige inhoudsbeoordeling ondergaan.

Vroege testers onder de 16 kunnen geen game previewen die hoger is beoordeeld dan de inhoudsrijping die hun ouder toestaat, en vroege testers onder de 18 kunnen geen game previewen die een Beperkte inhoudsrijping heeft.

Om vroege testers uit te nodigen om je game te previewen:

1.

In de linkerbovenhoek van je computer, navigeer naar Bestand  > Nodig vroege testers uit . Het venster Nodig vroege testers uit  wordt weergegeven.

2.

Gebruik de zoekbalk in het venster om tot 10 vrienden van vergelijkbare leeftijd of vertrouwde vrienden te selecteren die je wilt uitnodigen om je game te previewen, en klik vervolgens op de knop Nodig uit  in de rechterbenedenhoek van het venster. Elke vroege tester die je hebt geselecteerd, ontvangt een uitnodiging om je game te previewen.

 ![](https://prod.docsiteassets.roblox.com/assets/publishing/Early-testers.png)

3.

Als je nog geen [leeftijdscontrole](https://about.roblox.com/age-estimation)  of [leeftijdsverificatie](/docs/nl-nl/production/publishing/account-verification)  hebt voltooid, vraagt Roblox je om een leeftijdscontrole te voltooien.

4.

OPTIONEEL

 Je kunt je vroege testers beheren door op de knop Beheer samenwerkers  te klikken in de rechterbovenhoek van Studio. Een lijst van je huidige vroege testers wordt weergegeven met de datum waarop je hen hebt uitgenodigd om je game te previewen. Vanaf hier kun je:

-

Extra vroege testers toevoegen met behulp van de zoekbalk.

-

Vroege testers verwijderen door op de X-knop in hun rij te klikken.

## [Breng games uit](#breng-games-uit)[](#breng-games-uit)

Standaard zijn de games die je publiceert alleen toegankelijk voor jou als maker, gebruikers met Bewerken -toegang en groepsleden met de juiste [rollen en machtigingen](/docs/nl-nl/projects/groups#rollen-en-machtigingen) . Wanneer je klaar bent om je game aan extra gebruikers uit te brengen, zorg ervoor dat je voldoet aan de uitgavevereisten hieronder voor je doelgroep, en dan:

1.

In de linkerbovenhoek van je computer, navigeer naar Bestand  > Publiceren . Het venster Publiceren  wordt weergegeven.

2.

Om vroege testers uit te nodigen voordat je je game uitbrengt, klik op de knop Nodig uit , anders klik je op de knop Doorgaan . Het venster wordt bijgewerkt met de eerste vraag van de [Inhoudsbeoordelingsvragenlijst](/docs/nl-nl/production/promotion/content-ratings)  om te zien of je game [leeftijdsgebonden inhoud](https://en.help.roblox.com/hc/en-us/articles/15869919570708-Restricted-Content-Policy)  bevat.

1.

Als je game geen leeftijdsgebonden inhoud bevat, antwoord dan met Nee , klik vervolgens op de knop Publiceren . Je game ontvangt een Inhoud kan variëren  inhoudsrijping, en het wordt alleen uitgebracht voor leeftijdsgecontroleerde Roblox-gebruikers van 16 jaar en ouder. Je kunt later de volledige vragenlijst invullen op het Creator Hub als je je bereik wilt uitbreiden naar Roblox Kids, Select, of specifieke regio's die meer nauwkeurige inhoudsbeoordelingen vereisen.

2.

Als je game leeftijdsgebonden inhoud bevat, antwoord dan met Ja , en voltooi de volledige vragenlijst. Wanneer je klaar bent, klik je op de knop Publiceren . Je game ontvangt de juiste inhoudsbeoordelingen en wordt alleen uitgebracht voor [leeftijdsgecontroleerde](https://about.roblox.com/age-estimation)  Roblox-gebruikers van 16 jaar en ouder of [leeftijdsgeverifieerde](/docs/nl-nl/production/publishing/account-verification)  Roblox-gebruikers van 18 jaar en ouder, afhankelijk van de inhoud binnen je game.

 ![](https://prod.docsiteassets.roblox.com/assets/publishing/Publish-Rating.png)

3.

OPTIONEEL

 Vergroot je publiek door ofwel [je game te promoten met advertenties](/docs/nl-nl/production/promotion/advertise-on-roblox)  of [leeftijdsverificatie](/docs/nl-nl/production/publishing/account-verification)  te voltooien om het proces te starten om gebruikers onder de 16 jaar te bereiken.

 ![](https://prod.docsiteassets.roblox.com/assets/publishing/Publish-Grow.png)

Je kunt tot 5 games per dag uitbrengen die nog nooit eerder zijn uitgebracht. Deze limiet wordt dagelijks gereset. Het intrekken van de openbare toegang tot een uitgebracht spel en het vervolgens opnieuw uitbrengen telt niet  mee voor deze limiet.

### [Doelgroep](#doelgroep)[](#doelgroep)

Je kunt de doelgroep van een game instellen op het Creator Hub:

1.

In het [Creator Dashboard](https://create.roblox.com/dashboard/creations) , selecteer je game.

2.

In de navigatie aan de linkerkant, navigeer naar Publicatie-instellingen  > Beheer publiek .

3.

Klik in de rechterbovenhoek op de knop Beheer toegang , en stel je doelgroep in met behulp van de volgende tabbladen en instellingen:

| ** Tabblad** | | ** Instellingen** |
| Playtest | |
-

Vroege testers  - Je game kan alleen worden gespeeld door gebruikers met Bewerken -toegang en de vroege testers die je uitnodigt. Deze instelling is altijd ingeschakeld.

-

Playtesters  - Wanneer ingeschakeld, kan je game alleen worden gespeeld door gebruikers met Bewerken  of Playtest -toegang en de vroege testers die je uitnodigt.

 |
| Openbaar | |
-

Vrienden  - Wanneer ingeschakeld, kan je game alleen worden gespeeld door je vrienden en degenen die zijn gespecificeerd in het Playtest-tabblad. Wanneer uitgeschakeld, kan je game door iedereen op Roblox worden gespeeld, afhankelijk van leeftijds- en geografische beperkingen.

 |

4.

Klik op Wijzigingen opslaan .

5.

OPTIONEEL

 Voor Openbare  games kun je ervoor kiezen om je game uit te sluiten van de categorie Aanbevolen voor jou  op Roblox voor een meer beperkte reikwijdte en blootstelling.

1.

In het [Creator Dashboard](https://create.roblox.com/dashboard/creations) , selecteer je game.

2.

Navigeer naar Publiek  > Geavanceerde instellingen .

3.

In de sectie Aanbevelingen , schakel Uitsluiten van aanbevelingen  in.

### [Uitgavevereisten](#uitgavevereisten)[](#uitgavevereisten)

Uitgavevereisten zijn van toepassing op alle  uitgave-acties:

-

Een game voor de eerste keer uitbrengen.

-

Een uitgebracht spel bijwerken, zoals het uitbrengen van een nieuwe versie van een plaats.

-

Uitbrengen naar een andere game via Publiceer als .

-

Je doelgroepinstellingen wijzigen.

Om een game uit te brengen voor leeftijden 16+  en Vertrouwde vrienden :

-

Heb een account dat in goede staat is en minstens 2 dagen oud is.

-

Voltooi een leeftijdscontrole via [gezichtsleeftijdschatting](https://about.roblox.com/age-estimation)  of [overheids-ID](/docs/nl-nl/production/publishing/account-verification#verifi%C3%ABren-via-overheidsidentificatie) .

-

Beantwoord de vraag over leeftijdsgebonden inhoud die als eerste wordt weergegeven in de [Inhoudsbeoordelingsvragenlijst](/docs/nl-nl/production/promotion/content-ratings) :

-

Beantwoord Nee  om een Inhoud kan variëren  inhoudsrijping te ontvangen. De game wordt alleen uitgebracht voor leeftijdsgecontroleerde Roblox-gebruikers van 16 jaar en ouder.

-

Beantwoord Ja , en voltooi de vragenlijst. De game ontvangt inhoudsbeoordelingen op basis van je antwoorden en wordt uitgebracht voor leeftijdsgecontroleerde Roblox-gebruikers van 16 jaar en ouder of leeftijdsgeverifieerde Roblox-gebruikers van 18 jaar en ouder, afhankelijk van de inhoud binnen je game.

Om een game uit te brengen voor alle leeftijden , inclusief [Roblox Kids en Select](/docs/nl-nl/production/publishing/kids-and-select) , moet je voldoen aan alle voorgaande vereisten plus :

-

Verifieer je account via [gezichtsleeftijdschatting](https://about.roblox.com/age-estimation)  als je onder de 18 jaar bent, of via [overheids-ID](/docs/nl-nl/production/publishing/account-verification#verifi%C3%ABren-via-overheidsidentificatie)  als je 18 jaar of ouder bent.

-

Schakel [2FA](https://en.help.roblox.com/hc/en-us/articles/212459863-Add-2-Step-Verification-to-Your-Account)  in op je Roblox-account.

-

Voldoen aan één  van de volgende:

-

Houd een actieve [Roblox Plus](/docs/nl-nl/production/monetization/roblox-plus)  of [Roblox Premium](https://www.roblox.com/premium/membership)  abonnement voor 2 opeenvolgende maanden.

-

Betaal een eenmalige, terugbetaalbare [vergoeding](#optionele-vergoedingen) .

-

De game moet de [evaluatieprocedure](/docs/nl-nl/production/publishing/kids-and-select#voor-alle-leeftijden-inclusief-kids-en-select-accounts)  voor Kids  en Select  accounts doorstaan.

-

Voltooi de volledige [Inhoudsbeoordelingsvragenlijst](/docs/nl-nl/production/promotion/content-ratings)  en ontvang een Minimale, Milde of Gematigde (9+) inhoudsrijping.

### [Optionele vergoedingen](#optionele-vergoedingen)[](#optionele-vergoedingen)

Als je geen Roblox Plus of Roblox Premium-abonnement hebt voor 2 opeenvolgende maanden en je wilt een game uitbrengen voor gebruikers van alle leeftijden, heb je de optie om een publicatie- of versnelde beoordelingsvergoeding te betalen.

#### [Publicatievergoeding](#publicatievergoeding)[](#publicatievergoeding)

De publicatievergoeding  is een eenmalige, terugbetaalbare vergoeding van 1.000 Robux per game die je in staat stelt om je game uit te brengen en het bereik ervan uit te breiden naar gebruikers van alle leeftijden. Deze vergoeding is bedoeld om het duur en logistiek moeilijk te maken voor kwaadwillenden om grote aantallen accounts aan te maken en het platform te overspoelen met spam.

Als je game 25 zeer betrokken spelers gedurende 60 dagen zonder moderatie behoudt, ontvang je een terugbetaling van de publicatievergoeding. Als je game echter permanent wordt gemodereerd of verwijderd omdat deze niet voldoet aan Roblox's [Gemeenschapsnormen](https://en.help.roblox.com/hc/articles/203313410)  binnen de 60-dagenperiode, wordt de vergoeding niet  terugbetaald.

Om de publicatievergoeding te betalen:

1.

In het [Creator Hub](https://create.roblox.com/dashboard/creations) , selecteer de game die je wilt uitbrengen voor gebruikers van alle leeftijden.

2.

In de navigatie aan de linkerkant, navigeer naar Publiek  > Bereik .

3.

Onder Ervaring bereik , navigeer naar de sectie Terugbetaalbare publicatievergoeding , klik vervolgens op de blauwe knop Betalen . Een pop-updialoog wordt weergegeven.

4.

Klik op de knop Betaal 1.000  om je betaling te bevestigen.

#### [Versnelde beoordelingsvergoeding](#versnelde-beoordelingsvergoeding)[](#versnelde-beoordelingsvergoeding)

De versnelde beoordelings  vergoeding is een eenmalige, terugbetaalbare vergoeding van 50.000 Robux per game die je in staat stelt om de veiligheid en nalevingsbeoordelingen te versnellen die nodig zijn om je game uit te brengen voor gebruikers van alle leeftijden. Deze vergoeding is bedoeld om lanceerflexibiliteit en financiële verantwoordelijkheid te bieden voor gekwalificeerde makers die nog niet aan de vereiste voor zeer betrokken leeftijdsgecontroleerde spelers voor Kids en Select-accounts voldoen.

Hoewel de versnelde beoordelingsvergoeding de veiligheid en nalevingsbeoordelingen voor makers die een tijdgebonden lancering plannen of een campagne buiten het platform uitvoeren versnelt en precies moeten weten wanneer hun game klaar zal zijn voor alle leeftijden, moeten alle games blijven voldoen aan dezelfde normen als andere Roblox Kids en Select games .

Na 90 dagen kun je een terugbetaling aanvragen. Zolang je game in goede staat blijft en 25 zeer betrokken spelers behoudt, kun je je vergoeding terugtrekken en de geschiktheid voor Roblox Kids en Select behouden. Als je game deze organische mijlpalen nog niet heeft bereikt, kun je de vergoeding in stand houden om je geschiktheid voor Kids en Select-publiek te behouden. Als je game echter permanent wordt gemodereerd of verwijderd omdat deze niet voldoet aan Roblox's [Gemeenschapsnormen](https://en.help.roblox.com/hc/articles/203313410) , wordt de vergoeding niet  terugbetaald.

Om de versnelde beoordelingsvergoeding te betalen:

1.

In het [Creator Hub](https://create.roblox.com/dashboard/creations) , selecteer de game die je wilt versnellen voor een veiligheidsbeoordeling.

2.

In de navigatie aan de linkerkant, navigeer naar Publiek  > Bereik .

3.

Onder Ervaring bereik , navigeer naar de blauwe waarschuwing, klik vervolgens op de grijze knop Betalen . Een pop-updialoog wordt weergegeven.

4.

Klik op de knop Betaal 50.000  om je betaling te bevestigen.

Als een kleine overtreding wordt gevonden tijdens de 48-uurs beoordeling, moet je de juiste aanpassingen aan je game maken en deze opnieuw indienen. De 48-uurs klok begint opnieuw vanaf het moment van herindiening.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
