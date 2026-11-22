<!-- Source: https://create.roblox.com/docs/nl-nl/production/game-design/balance-virtual-economies -->

Balanceren van virtuele economieën | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Game-ontwerp](/docs/nl-nl/production/game-design)
6. /
7. Inkomsten genereren met je ervaring

# Balanceren van virtuele economieën

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Virtuele economieën op Roblox zijn complexe systemen die de echte economieën nabootsen, waar spelers handelen, verdienen en virtuele valuta en middelen uitgeven. Het balanceren van deze virtuele economieën is van vitaal belang om een eerlijke en boeiende ervaring te waarborgen die spelers gemotiveerd houdt zonder de virtuele goederen te over- of onderwaarderen. Gebalanceerde virtuele economieën hebben de volgende best practices:

-

Gegevensgestuurde inhoud

-

Middelenplanning

-

Impactschatting

-

Middelenafvoer

Gebruik [Experimenten](/docs/nl-nl/production/experiments)  om verschillende prijsniveaus en kortingsstrategieën A/B te testen om de "Gouden Zone" van je winkel te vinden. Zodra je de meest effectieve prijzen hebt geïdentificeerd, gebruik je [Configuraties](/docs/nl-nl/production/configs)  om flashverkopen te activeren of je virtuele economie in realtime in balans te brengen zonder je servers opnieuw op te starten.

## [Gegevensgestuurde inhoud](#gegevensgestuurde-inhoud)[](#gegevensgestuurde-inhoud)

Het gebruik van gegevens om te begrijpen hoe spelers omgaan met en de inhoud van je ervaring consumeren, is de sleutel tot het behouden van een gebalanceerde economie. Bij het opbouwen van de database van je ervaring, zorg ervoor dat je het volgende bijhoudt:

-

Wie welk item koopt.

-

Welke acties valuta opleveren.

-

Hoeveel valuta wordt verdiend versus gekocht.

-

Of verdiende of gekochte valuta wordt gebruikt voor itemaankopen.

-

Wanneer en welke items worden gebruikt.

-

Hoe vaak spelers interactie hebben met specifieke functies en het tijdstip van die interacties.

Deze gegevenspunten zijn cruciale overwegingen bij het plannen van evenementen. Hoewel het uitvoeren van evenementen kan helpen om spelers betrokken te houden tussen grote inhoudsupdates, is het essentieel om prioriteit te geven aan gegevensregistratie voor in-game acties, inhoudsconsumptie, itemverkoop en itemgebruik.

Om meer te leren over het plannen en creëren van evenementen, zie [Inhoudsupdates](/docs/nl-nl/production/game-design/content-updates)  en [LiveOps-essentials](/docs/nl-nl/production/game-design/liveops-essentials) .

## [Middelenplanning](#middelenplanning)[](#middelenplanning)

Middelenplanning  houdt in dat je in balans brengt hoe virtuele middelen worden gecreëerd en hoe ze worden uitgegeven. Dit concept wordt het beste geïllustreerd in de fictieve ervaring * Feline Fishing Fun* , waar spelers vissen voor hun middelen. * Feline Fishing Fun*  heeft de volgende kenmerken:

-

De valuta die wordt gebruikt om items in de winkel te kopen, wordt Goud (G)  genoemd.

-

Goud wordt verdiend door vissen van verschillende zeldzaamheden en waarden te vangen en deze aan verkopers te verkopen.

-

Goudpakketten kunnen ook in de winkel worden gekocht.

-

Er zijn drie soorten vissen van verschillende zeldzaamheden en waarden die spelers een kans hebben om in de rivier te vangen:

-

Meerval: 70% kans om te vangen, 10G

-

Forel: 20% kans om te vangen, 20G

-

Zalm: 10% kans om te vangen, 30G

De ontwikkelaars van * Feline Fishing Fun*  plannen een evenement waarbij een speciale Gouden Zalm 24 uur beschikbaar zal zijn, met een kans van 0,1% om gevangen te worden, en het zal 1000 Goud waard zijn. Dit soort evenement verleidt spelers om te vissen voor een kans om het te verwerven en integreert soepel met de [kernloop](/docs/nl-nl/production/game-design/core-loops)  van vissen in de ervaring.

Als de ontwikkelaars het evenement lanceren zonder de economische impact van verhoogd vissen te schatten, onthult gegevensvisualisatie dat de hoeveelheid Goud die uit de winkel wordt gekocht vlak blijft, terwijl de uitgaven stijgen. Deze onderschatting van het verhoogde vissen leidt tot een aanzienlijke overschot aan Goud in de virtuele economie. Als gevolg hiervan besteden spelers met overvloedig Goud vrijelijk, waardoor er weinig prikkel is om meer te kopen, wat leidt tot een daling van de inkomsten nadat het evenement is afgelopen.

![](https://prod.docsiteassets.roblox.com/assets/game-design/balancing-virtual-economies/balancing-virtual-economies-1.png) Een ongebalanceerd evenement in * Feline Fishing Fun* .

## [Impactschatting](#impactschatting)[](#impactschatting)

Het schatten van de potentiële impact van een evenement op de economie van een ervaring is van groot belang om balans te waarborgen. Een veelgebruikte methode om de potentiële impact te meten, is via Verwachte Waarde  (EV) berekeningen.

De EV van een item wordt gedefinieerd als een voorspelde waarde van een variabele, berekend als de som van alle mogelijke waarden, elk vermenigvuldigd met de kans op optreden. Het begrijpen van Verwachte Waarde is cruciaal voor het behouden van een gebalanceerde economie wanneer er waarde te behalen is uit een probabilistisch gebaseerd systeem, zoals het vissysteem van * Feline Fishing Fun* .

Hieronder staan afbeeldingen van een eenvoudige EV-calculator ingesteld in een spreadsheet. Dit is een standaardformaat dat kan worden toegepast op conceptueel vergelijkbare situaties.

![](https://prod.docsiteassets.roblox.com/assets/game-design/balancing-virtual-economies/balancing-virtual-economies-2.png) Spreadsheet voor EV-calculator zonder evenement.

Als er een groep waardevolle items is die een speler een kans heeft om te verkrijgen, vermenigvuldig je de waarde van dat item met de procentuele kans om het te verwerven. Voor het vissysteem van * Feline Fishing Fun*  ziet dit er als volgt uit:

-

Meerval = 10 Goud x 70% = 7G

-

Forel = 20 Goud x 20% = 4G

-

Zalm = 30 Goud x 10% = 3G

Door de resultaten op te tellen, is de EV van een enkele vispoging 7G + 4G + 3G  = 14G . Door 14G te vermenigvuldigen met 1.000 vispogingen per dag, krijg je 14.000 Goud verdiend met vissen op een normale dag zonder evenement.

![](https://prod.docsiteassets.roblox.com/assets/game-design/balancing-virtual-economies/balancing-virtual-economies-3.png) Spreadsheet voor EV-calculator aangepast voor evenement.

Hoewel het onmogelijk is om precies te weten hoeveel spelers op een bepaalde dag van een evenement zullen deelnemen, helpt elk opvolgend evenement bij toekomstige schattingen. Voor het vis evenement van * Feline Fishing Fun* , wanneer je de juiste waarde van de Gouden Zalm bepaalt, voeg je deze toe aan de EV-calculator en vergelijk je de resulterende EV met de EV van een dag zonder evenement. Door het normale aankooptempo van items en de tijd die spelers nodig hebben om nuttige items te kopen te begrijpen, kun je bepalen hoeveel valuta te veel is.

## [Middelenafvoer](#middelenafvoer)[](#middelenafvoer)

Een middelenafvoer  is een economisch systeem dat is ontworpen om middelen uit omloop te verwijderen. Bij het ontwerpen van nieuwe bronnen van valuta is het van cruciaal belang om plannen te hebben voor hoe je verschillende hoeveelheden overtollige valuta kunt "afvoeren". Veelvoorkomende voorbeelden zijn:

-

Speciale evenement cosmetische items, zoals beperkte tijd gouden accessoires.

-

Een opeenvolgend evenement dat vereist dat de valuta die in het vorige evenement is verdiend, wordt uitgegeven.

-

Een evenementwinkel  die tijdens evenementen verschijnt en een klein voordeel biedt aan spelers die valuta uitgeven terwijl het evenement aan de gang is.

De veiligste oplossing om de economie van een ervaring te beschermen, is om een evenement een unieke evenementvaluta te laten genereren die alleen wordt gebruikt om items uit een speciale evenementwinkel te kopen.  Dit zorgt ervoor dat de belangrijkste economie van de ervaring onaangetast blijft.

Middelenafvoeren zorgen ervoor dat spelers een leuke en lonende tijd hebben tijdens het evenement, terwijl ook de waarde en integriteit van de bestaande valuta behouden blijft. Een gebalanceerd Gouden Zalm evenement in * Feline Fishing Fun*  zal eruitzien als de onderstaande grafiek, met Goudbronnen en -afvoeren relatief verhoogd tijdens het evenement, maar dicht bij elkaar bewegend.

![](https://prod.docsiteassets.roblox.com/assets/game-design/balancing-virtual-economies/balancing-virtual-economies-4.png) Een gebalanceerd evenement in * Feline Fishing Fun* .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
