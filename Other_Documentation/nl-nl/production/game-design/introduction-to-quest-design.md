<!-- Source: https://create.roblox.com/docs/nl-nl/production/game-design/introduction-to-quest-design -->

Inleiding tot questontwerp | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Game-ontwerp](/docs/nl-nl/production/game-design)
6. /
7. Je ervaring bouwen

# Inleiding tot questontwerp

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Inleiding tot quests, prestaties en dagelijkse taken

Quests zijn een game-mechanisme waarbij spelers doelstellingen voltooien om beloningen te verdienen, zoals items, valuta of badges. Quests bieden spelers nieuwe doelen en prikkels, wat hen kan motiveren om langer en vaker te spelen, waardoor hun [betrokkenheid](/docs/nl-nl/production/analytics/engagement)  toeneemt. Ze kunnen ook verveling verminderen en een gevoel van vooruitgang en prestatie bieden, wat leidt tot betere [retentie](/docs/nl-nl/production/analytics/retention) .

Voor kant-en-klare functionaliteit om quests te creëren, zie het [Missions](/docs/nl-nl/resources/feature-packages/missions)  featurepakket.

## [Queststructuur](#queststructuur)[](#queststructuur)

Structuurgewijs bestaan quests uit drie componenten:

-

Doelstelling:  De doelstelling is een taak die de speler moet voltooien om de beloning te verdienen. Het verzamelen van items, het verslaan van monsters en het reizen naar interessante punten op een kaart zijn enkele veelvoorkomende voorbeelden van questdoelstellingen. Quests kunnen bestaan uit enkele doelstellingen of meerdere.

-

Hoeveelheid:  De hoeveelheid is een modifier op de doelstelling: verzamel 100 appels, versla 5 monsters, bezoek 10 huizen van spelers. Hoeveelheid is een manier om de moeilijkheidsgraad van een quest te wijzigen, waarbij grotere hoeveelheden meer inspanning van de spelers vereisen om de doelstelling te voltooien.

-

Beloning:  De beloning is de prikkel voor spelers om de quest te voltooien. Veelvoorkomende beloningen zijn ervaringspunten (XP), valuta zoals gouden munten, consumables zoals gezondheidsdranken en andere waardevolle items. Over het algemeen geldt: hoe uitdagender de quest, hoe waardevoller de beloningen, zodat spelers het gevoel hebben dat de inspanning om de quest te voltooien de moeite waard is.

De structuur van een quest kan variëren van een enkele taak tot meerdere taken, die allemaal door een speler moeten worden voltooid om de beloning te verdienen. Ze kunnen ook extra quests ontgrendelen na voltooiing, wat een questketen  wordt genoemd.

Er zijn twee veelvoorkomende soorten quests:

-

Prestaties:  Ook bekend als badges op Roblox, zijn dit quests met één taak die vaak aanzienlijke tijd en moeite vereisen om te voltooien. Het verdienen van een bijzonder uitdagende prestatie is een bron van trots, en badges stellen spelers in staat om hun prestaties aan anderen te tonen. Prestaties kunnen ook fungeren als een indicator van de voortgang van de speler, die mijlpalen vertegenwoordigt die ze gedurende hun reis hebben bereikt. Om te leren hoe je prestaties in je game kunt implementeren, zie [Badges](/docs/nl-nl/production/publishing/badges) .

![Een close-up van een prestatiebadge voor de Jailbreak-game die spelers beloont die de hoogste beloning in een drukke server behalen. De badge aan de linkerkant toont een lichtgekleurde blokachtige mannelijke avatar die naar rechts is gedraaid om naar de tekst te kijken die zegt 'Smooth Criminal'.](https://prod.docsiteassets.roblox.com/assets/game-design/introduction-to-quest-design/quest-design-0.png) Prestatiebadge in [* Jailbreak*](https://www.roblox.com/games/606849621/)

-

Dailies : Ook bekend als dagelijkse quests, zijn dit korte taken met bescheiden beloningen die beschikbaar zijn en binnen 24 uur moeten worden voltooid. Sommige dagelijkse questsystemen bieden elke dag dezelfde quests, terwijl andere quests roteren om spelers nieuwe doelstellingen te bieden en herhaling te voorkomen. Dailies hebben eenvoudige doelstellingen met lage vereisten voor voltooiing om spelers aan te moedigen de quests in een enkele speelsessie te voltooien.

![Een pop-up UI in de World // Zero-game die verschillende dagelijkse quests voor spelers weergeeft, samen met de beloningen die ze kunnen verdienen.](https://prod.docsiteassets.roblox.com/assets/game-design/introduction-to-quest-design/quest-design-1.png) Dagelijkse quests in [* World // Zero*](https://www.roblox.com/games/2727067538/)

Voor deze gemakkelijke quests zijn kleine beloningen gepast, vanwege de snelheid waarmee ze worden voltooid. Omdat ze dagelijks beschikbaar zijn, kunnen Dailies een betrouwbare bron van zachte valuta bieden en spelers aanmoedigen om elke dag in te loggen.

## [Gebruikscases](#gebruikscases)[](#gebruikscases)

Hoewel ze vergelijkbare mechanismen gebruiken om spelers taken en beloningen te geven, spelen quests, prestaties en dailies complementaire rollen in een game. Ze:

-

Bieden doelen

-

Brengen functies aan het licht

-

Onderwijzen via tutorials

-

Voeg variatie toe aan sessies

-

Creëren een resource drip

-

Verhogen de betrokkenheid

-

Faciliteren voortgang

-

Moedigen nieuwe gameplay aan

-

Leveren narratief

![Een diagram dat bijhoudt hoe quests, prestaties en dailies overlappen in het voldoen aan verschillende gameplay-eisen, zoals kortetermijndoelen, tutorials, voortgang en narratief.](https://prod.docsiteassets.roblox.com/assets/game-design/introduction-to-quest-design/quest-design-2.png) Overlap van rollen tussen quests, prestaties en dailies

### [Bied doelen](#bied-doelen)[](#bied-doelen)

Een manier om spelers betrokken te houden, is door hen een mix van korte, middellange en lange termijn doelen te bieden, waardoor ze frequent vooruitgang kunnen voelen en iets hebben om naar te streven.

Kortetermijndoelen  kunnen in een enkele speelsessie worden voltooid en bieden kleine, frequente momenten van prestatie. Omdat spelers ze binnen een enkele dag moeten voltooien, moeten dailies uitsluitend uit kortetermijndoelen bestaan.

Middellangetermijndoelen  vereisen dagen tot weken van spelen om te voltooien. De meeste quests, vooral die met meerdere doelstellingen, vallen ergens tussen kortetermijn- en middellangetermijndoelen.

Langetermijndoelen  vereisen maanden van spelen om te voltooien. Veel prestaties vertegenwoordigen langetermijndoelen omdat ze aanzienlijke tijd, moeite of vaardigheid vereisen om te verdienen.

### [Breng functies aan het licht](#breng-functies-aan-het-licht)[](#breng-functies-aan-het-licht)

Door quests te creëren die spelers vereisen om verschillende gebieden te verkennen of bepaalde taken te voltooien, kun je de aandacht vestigen op de volledige breedte van de functies en inhoud van de game. Dit kan vooral nuttig zijn voor games met grote werelden of complexe systemen, omdat spelers zich misschien niet realiseren wat de game allemaal te bieden heeft.

In dit voorbeeld van [* Squishmallows*](https://www.roblox.com/games/7941853407/)  wordt een van de vele locaties van de game, de camping, aan het licht gebracht. Deze quest kan de eerste keer zijn dat een speler leert dat er een camping in de wereld is, en de beloning moedigt hen aan om de kaart te verkennen om deze te vinden.

![Een pop-up UI in de Squishmallows-game die spelers informeert over wat ze moeten doen in een quest om een beloning te verkrijgen.](https://prod.docsiteassets.roblox.com/assets/game-design/introduction-to-quest-design/quest-design-8.png) Quests in * Squishmallows*

### [Onderwijs via tutorials](#onderwijs-via-tutorials)[](#onderwijs-via-tutorials)

Quests kunnen spelers ook leren hoe ze die functies moeten gebruiken door als tutorials te fungeren. Quest-gebaseerde tutorials hebben een aantal voordelen:

-

Quests bevorderen actief leren, waarbij spelers leren door te spelen, niet alleen door te lezen. Actief leren resulteert in een betere retentie van de instructies, zodat spelers zich beter herinneren wat ze moeten doen wanneer ze alleen zijn.

-

Complexe taken kunnen worden opgesplitst in eenvoudige, discrete stappen, elk een questdoelstelling.

-

Elke functie kan zijn eigen quest of questketen tutorial hebben, waardoor tutorials over de tijd verspreid kunnen worden.

-

Quests volgen de voortgang van de speler door de tutorial, wat waardevolle analytische gegevens oplevert over waar spelers mogelijk moeite mee hebben.

-

Spelers voelen zich goed over het leren spelen, omdat ze ervoor worden beloond.

![Een pop-up UI in de RoCitizens-game die spelers informeert over wat ze moeten doen in een tutorial quest om een beloning te verkrijgen.](https://prod.docsiteassets.roblox.com/assets/game-design/introduction-to-quest-design/quest-design-9.png) Tutorial quest in [* RoCitizens*](https://www.roblox.com/games/137877687/)

### [Voeg variatie toe aan sessies](#voeg-variatie-toe-aan-sessies)[](#voeg-variatie-toe-aan-sessies)

Hoe langer een speler een game speelt, hoe vertrouwder ze worden met de systemen en inhoud ervan. Wanneer spelers worden aangemoedigd om nieuwe dingen te proberen, is de kans kleiner dat ze in gameplay-routines vervallen die na verloop van tijd saai worden. Quests kunnen variatie aan de sessie van een speler toevoegen door hen aan te moedigen om zich bezig te houden met inhoud of systemen waarmee ze anders misschien niet in aanraking zouden komen, of om terug te keren naar systemen waarmee ze recentelijk niet zijn omgegaan. Dit kan vooral nuttig zijn voor games met repetitieve gameplay, of die minder frequente updates hebben, maar elke game kan profiteren van het betrokken houden van zijn spelers en ervoor zorgen dat al zijn gebieden actief blijven.

![Quest UI in de The Wild West-game die tegels in verschillende kleuren weergeeft om spelers te informeren over wat ze moeten doen voor de quest van elke tegel om een beloning te verkrijgen.](https://prod.docsiteassets.roblox.com/assets/game-design/introduction-to-quest-design/quest-design-3.png) Quests in [* The Wild West*](https://www.roblox.com/games/2317712696/)

### [Creëer resource drip](#creëer-resource-drip)[](#creëer-resource-drip)

Een resource drip  is een bron die kleine hoeveelheden virtuele middelen zoals valuta, XP of crafting-ingrediënten biedt die in de loop van de tijd optellen, waardoor spelers hun speelsessies en resource-uitgaven eromheen kunnen plannen.

Regelmatig zelfs kleine hoeveelheden verdienen, moedigt spelers aan om uit te geven omdat ze weten dat er altijd meer te vinden is. Wanneer bronnen schaars of te inspannend zijn, kan dit deelname aan de algehele economie ontmoedigen en leiden tot negatieve indrukken over de eerlijkheid van het ontwerp van de game.

De economie van een game is verbonden met de kernloop. Wanneer een speler zich bezighoudt met de kernmechanica van de game, verdient en besteedt hij van nature middelen. Spelers die geen middelen hebben om uit te geven, kunnen de aankopen niet doen die hun activiteit in de rest van de game mogelijk maken of verbeteren, zoals verbeterde tools en vaardigheden. Het faciliteren van investeringen in de economie van een game en een gezonde interactie met de kernloop kan ook leiden tot verbeterde retentie.

Om deze redenen kan het voordelig zijn om in de loop van de tijd middelen aan spelers te drip-feed, en een manier om dat te doen is via questbeloningen. Dailies zijn een uitstekende leveringsmechanisme voor valuta omdat de beloningen betrouwbaar, klein en waardevol genoeg zijn om spelers aan te moedigen elke dag terug te keren.

![Een pop-up UI in de Pet Simulator X! game die tegels in een top-down lijst weergeeft om spelers te informeren over wat ze moeten doen voor de quest van elke tegel om een beloning te verkrijgen.](https://prod.docsiteassets.roblox.com/assets/game-design/introduction-to-quest-design/quest-design-7.png) Dagelijkse quests in [* Pet Simulator X!*](https://www.roblox.com/games/6284583030/)

### [Verhoog de betrokkenheid](#verhoog-de-betrokkenheid)[](#verhoog-de-betrokkenheid)

Beperkte tijdsinhoud is elk type consumable of verzamelbare inhoud zoals quests, huisdieren of auto's die tijdelijk beschikbaar zijn voor spelers. Als spelers de inhoud niet verdienen of voltooien voordat de tijd om is, hebben ze misschien nooit meer een kans. Om die reden stimuleert beperkte tijdsinhoud de betrokkenheid, omdat spelers hun inspanningen verhogen in een haast om de klok te verslaan.

![Een close-up van de Ontdek-pagina met verschillende game-tegels die zijn gethematiseerd voor Halloween om de betrokkenheid van spelers voor het seizoen te inspireren.](https://prod.docsiteassets.roblox.com/assets/game-design/introduction-to-quest-design/quest-design-10.png) Beperkte tijd seizoensgebonden evenementen

Omdat het zo effectief is in het stimuleren van de betrokkenheid van spelers en monetisatie, is beperkte tijdsinhoud een essentieel element van de live-operaties (LiveOps) van een game. Net als andere vormen van beperkte tijdsinhoud creëren quests die slechts voor een korte tijd beschikbaar zijn een gevoel van urgentie en opwinding, waardoor spelers worden aangemoedigd om regelmatig in te loggen gedurende de duur van het evenement om de beperkte tijdsbeloningen te verdienen. Deze tijdelijke quests zijn gebruikelijk tijdens seizoensgebonden evenementen, zoals Halloween of jubileumvieringen.

Om meer te leren over live-operaties en het onderhouden en bijwerken van een live game, zie [LiveOps essentials](/docs/nl-nl/production/game-design/liveops-essentials) .

### [Faciliteer voortgang](#faciliteer-voortgang)[](#faciliteer-voortgang)

Een voortgangssysteem  kan spelers helpen om hen te laten slagen door betrokkenheid bij de [kernloop](/docs/nl-nl/production/game-design/core-loops)  van de game te bevorderen. Terwijl spelers zich bezighouden met de kernsystemen van de game, maken ze voortgang door de loop en maken ze vooruitgang op hun eigen doelen.

Quests kunnen fungeren als een voortgangssysteem door een gestructureerde manier te bieden om door de inhoud van de game te vorderen. Met elke voltooide quest verdienen spelers beloningen zoals wapens of vaardigheidspunten die hen helpen zich voor te bereiden op de volgende uitdaging.

[Seizoenspassen](/docs/nl-nl/production/game-design/season-pass-design)  zijn voortgangssystemen die quests incorporeren. In [* Dragon Adventures*](https://www.roblox.com/games/3475397644/)  voltooien spelers quests die "missies" worden genoemd om punten te verdienen voor beloningsniveaus. De quests zijn allemaal activiteiten die zijn gekoppeld aan de kernloopmechanica van het uitbroeden en opvoeden van draken. Terwijl spelers door de niveaus vorderen, ontgrendelen ze meer beloningen, culminerend in het ontgrendelen van een exclusieve draak als de laatste seizoensbeloning. Via deze UI kunnen spelers hun voortgang door de niveaus volgen naarmate de deadline voor het einde van het seizoen nadert.

![Missions UI in de Dragon Adventures-game die twee rijen tegels weergeeft om spelers te informeren over wat ze moeten doen voor verschillende beloningsniveaus om beloningen te verkrijgen voor ofwel de basis gameplay of met een seizoenspas.](https://prod.docsiteassets.roblox.com/assets/game-design/introduction-to-quest-design/quest-design-11.png) Seizoenspas voortgang in * Dragon Adventures*

### [Moedig nieuwe gameplay aan](#moedig-nieuwe-gameplay-aan)[](#moedig-nieuwe-gameplay-aan)

Quests kunnen spelers aanmoedigen om op interessantere en uitdagendere manieren te spelen die ze misschien nog niet eerder hebben geprobeerd. In dit voorbeeld van Jailbreak worden spelers verplicht om niet alleen een vijandelijke helikopter neer te schieten, maar dit te doen terwijl ze in een voertuig rijden – een uitdaging die ze anders misschien nooit zouden proberen. Zoals blijkt uit de "onmogelijk" beoordeling, vereist het behalen van deze badge waarschijnlijk veel pogingen, waarbij de speler zeer betrokken is.

![Een close-up van een prestatiebadge voor de Jailbreak-game die spelers beloont die een helikopter neerhalen terwijl ze in een voertuig rijden. De badge aan de linkerkant toont een lichtgekleurde blokachtige mannelijke avatar die naar links is gedraaid om naar de tekst te kijken die zegt 'Top Gun'.](https://prod.docsiteassets.roblox.com/assets/game-design/introduction-to-quest-design/quest-design-4.png) Prestatiebadge in * Jailbreak*

Deze alternatieve gameplaydoelen kunnen vooral boeiend zijn voor ervaren spelers die misschien alles hebben geprobeerd wat de game te bieden heeft. Zonder nieuwe uitdagingen raken zelfs de meest toegewijde spelers uiteindelijk verveeld en gaan ze verder met andere games. Prestaties zijn een manier om ze betrokken te houden tussen contentupdates.

### [Lever narratief](#lever-narratief)[](#lever-narratief)

Naast hun doelstellingen, hoeveelheden en beloningen, kunnen quests optioneel smaaktekst  bevatten die stukjes narratief en achtergrondverhaal over de wereld van de game biedt. Hoewel dit niet strikt noodzakelijk is, vooral in games zonder narratieve elementen, kunnen op verhaal gebaseerde quests de ervaring van de speler verrijken en hen meer ondergedompeld laten voelen in de 3D-wereld.

In [* Spellbound*](https://www.roblox.com/games/6468323505/)  accepteert de speler een quest van een NPC genaamd Moritor, die hulp nodig heeft bij het ophalen van een drankje om zijn kaalheid te genezen. De tekst vertelt de speler niet alleen wat te doen, maar ook waarom, en doet dit op een manier die bijdraagt aan de humoristische toon en ervaring van de game. Zelfs de beloning van de quest, een hoed, is thematisch verbonden met het verhaal.

![Quest UI in de vorm van een rode rol die zowel narratief van het blokachtige mannelijke personage rechts van de rol weergeeft, alsook een doelstelling prompt en beloningen die spelers zullen verdienen als ze de quest voltooien.](https://prod.docsiteassets.roblox.com/assets/game-design/introduction-to-quest-design/quest-design-5.png) Quest-narratief in * Spellbound*

## [Bronnen](#bronnen)[](#bronnen)

Voor een diepgaandere kijk op quests, bekijk deze workshopvideo's. Ze bevatten tips voor het ontwerpen, schrijven en produceren van quests, evenals het ontwikkelen van een spreadsheet om de ontwikkeling van quests efficiënter te maken.

Quests, prestaties en dagelijkse taken ontwerpen

Quests, prestaties en dagelijkse taken schrijven

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
