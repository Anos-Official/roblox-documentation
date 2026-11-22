<!-- Source: https://create.roblox.com/docs/nl-nl/production/game-design/onboarding-techniques -->

Onboarding technieken | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Game-ontwerp](/docs/nl-nl/production/game-design)
6. /
7. Je ervaring bouwen

# Onboarding technieken

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Onboarding technieken zijn strategieën die worden gebruikt om spelers zo snel en naadloos mogelijk door de onboarding funnel te leiden. Drie populaire onboarding technieken zijn:

-

Visuele elementen

-

Contextuele tutorials

-

Getimede hints

Elk van deze technieken kan worden geoptimaliseerd met behulp van Configs  en Experiments . Bijvoorbeeld, je kunt Experiments  gebruiken om A/B-tests uit te voeren of een vertraging van 5 seconden of 10 seconden voor een getimede hint leidt tot een betere funnel voltooiing. Zodra je de winnende timing hebt geïdentificeerd, gebruik je Configs  om die waarde wereldwijd in realtime bij te werken, zodat je je onboarding flow onmiddellijk kunt optimaliseren zonder je servers opnieuw op te starten.

## [Visuele elementen](#visuele-elementen)[](#visuele-elementen)

Visuele elementen  zijn activa of effecten die in een spel verschijnen om spelers te helpen begrijpen hoe ze moeten spelen, waar ze naartoe moeten gaan, waar ze op moeten letten of welke acties ze moeten ondernemen. Vanwege deze kenmerken gedijen visuele elementen wanneer ze worden gebruikt in combinatie met de onboarding funnel van een spel.

Visuele elementen kunnen statisch of geanimeerd zijn, verschijnen binnen de omgeving of de UI overlappen. Deze elementen zijn meestal tijdelijk en blijven alleen bestaan zolang ze hun intentie aan de speler communiceren.

Wanneer ze correct worden gebruikt, helpen visuele elementen die zijn geïntegreerd met een onboarding funnel:

-

Verbeteren van de duidelijkheid

-

Verhogen van de toegankelijkheid

-

Verbeteren van de onderdompeling

-

Faciliteren van feedback

Voorbeelden van visuele elementen in onboarding zijn:

-

Een bewegende pijl die naar een knop in de UI wijst

-

Deeltjeseffecten boven een interessant item in de wereld

-

Een gloeiende lijn in de wereld die spelers naar een bestemming leidt

-

Een bord in de wereld dat de kernloop van een spel weergeeft.

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/visual-elements-1.png) Directionele pijlen en iconen in * Creatures of Sonaria.*

### [Verbeter de duidelijkheid](#verbeter-de-duidelijkheid)[](#verbeter-de-duidelijkheid)

Spelers die niet begrijpen wat ze in de eerste paar minuten moeten doen, zullen waarschijnlijk stoppen, maar dat geldt ook voor spelers die zich vervelen door lange en prescriptieve tutorials. Het gebruik van visuele elementen in onboarding funnels stelt je in staat om spelers te leren wat ze moeten weten, terwijl ze ook snel naar het plezier kunnen gaan. Wanneer informatie efficiënt moet worden gecommuniceerd, worden visuele elementen gebruikt om de duidelijkheid op drie manieren te verbeteren:

-

Prominentie

-

Hoogtepunten

-

Hints

#### [Prominentie](#prominentie)[](#prominentie)

Prominente visuals zijn moeilijker over het hoofd te zien, te negeren of verkeerd te interpreteren dan alleen tekst. Sommige spellen presenteren pop-upberichten met tekst terwijl spelers vooruitgang boeken. Afhankelijk van factoren zoals locatie, kleur en contrast, en hoe gefocust de speler is op wat ze aan het doen zijn in het spel, kunnen die tekstprompts gemakkelijk over het hoofd worden gezien. Als spelers ze niet opmerken, zijn ze van geen nut. Het plaatsen van visuele elementen in de wereld, waar spelers ze tegenkomen terwijl ze spelen, is een oplossing voor dit probleem.

In * Color or Die*  is een bord dat de kernoverlevingsmechaniek van het spel uitlegt, direct in het gezichtsveld van de spelers geplaatst terwijl ze hun eerste verfemmer verzamelen om te beginnen met spelen. Het is onmogelijk om het te missen, maar het voorkomt niet dat de speler het spel begint.

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/visual-elements-2.png) Prominent visueel element in * Color or Die.*

Deze techniek is een efficiënte manier om de kernmechaniek van een spel snel en duidelijk uit te leggen. Vergelijk het visuele element met hoe dezezelfde informatie eruit zou zien als tekst:

Wanneer het monster nadert, ga dan tegen een muur staan die dezelfde kleur heeft als je avatar. Het monster zal in de war zijn en je niet kunnen zien. Als je tegen een muur van een andere kleur staat, zal het je opmerken en ben je in gevaar.

Spelers lezen over het algemeen niet graag instructies en slaan tekstprompts over om naar de gameplay te gaan. Het visueel presenteren van instructies met zo min mogelijk klikken of tikken bereidt die ongeduldige spelers beter voor dan welke hoeveelheid tekst dan ook die ze zouden weigeren te lezen.

#### [Hoogtepunten](#hoogtepunten)[](#hoogtepunten)

Iets dat spelers zouden moeten bekijken, benadrukken is effectiever dan het in tekst te beschrijven. Hoe meer tekst een speler moet lezen, hoe waarschijnlijker het is dat ze de informatie verkeerd interpreteren of vergeten. Goed ontworpen visuals zijn moeilijker verkeerd te begrijpen en gemakkelijker te onthouden omdat ze minder interpretatie vereisen.

Overweeg de volgende zin:

Open je inventaris door op de rugzak  knop te klikken.

Dit vereist dat spelers een rugzak  knop interpreteren en deze vervolgens in de UI zoeken. Overweeg in plaats daarvan de impact van het hebben van een pijl die naar de knop wijst en hen precies vertelt waar ze moeten klikken.

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/visual-elements-3.png) Hoogtepunten in * Hello Kitty Cafe.*

In dit voorbeeld van * Hello Kitty Cafe*  is de gewenste knop in de schijnwerpers gezet terwijl de rest van het scherm is verduisterd. Een roze omtrek benadrukt de knop en een pijl wijst ernaar. Er is geen misverstand over wat de speler als volgende moet klikken.

#### [Hints](#hints)[](#hints)

Visuele hints kunnen spelers op koers houden. Nieuwe spelers weten niet altijd wat belangrijk is om op te letten en zijn enthousiast om te verkennen. Persistente visuele elementen die op het scherm blijven totdat de speler een stap van de tutorial heeft voltooid, helpen spelers te voorkomen dat ze worden afgeleid door andere gameplaymechanismen, de omgeving of de UI. Zelfs als ze ervoor kiezen om te verkennen, blijven de hints bestaan om hen te begeleiden wanneer ze klaar zijn om terug te keren.

Visuele elementen zijn niet beperkt tot het vertellen van spelers waar ze naartoe moeten gaan of wat ze moeten klikken. Ze kunnen ook functionaliteit impliceren, zoals het waarschuwen van spelers dat items in de wereld interactief zijn.

In Jailbreak worden spelers niet expliciet verteld wat ze moeten doen om uit de gevangenis te ontsnappen, maar visuele hints in de wereld trekken hun aandacht en impliceren interactiviteit. Zonder deze hints kunnen nieuwe spelers moeite hebben om ontsnappingsroutes te vinden. Visuele hints bieden net genoeg informatie om spelers in staat te stellen het probleem zelf op te lossen en zich slim te voelen omdat ze het hebben uitgezocht.

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/visual-elements-4.png) Voetafdrukken wijzen op een mogelijke ontsnappingsroute in * Jailbreak.*

Bij het overwegen van het implementeren van hints in je onboarding funnel, wees dan doelbewust in het bepalen wie ze zal zien en wanneer ze verschijnen. Voor meer informatie over het gebruik van hints, zie [Getimede hints](#getimede-hints) .

### [Verhoog de toegankelijkheid](#verhoog-de-toegankelijkheid)[](#verhoog-de-toegankelijkheid)

Visuele elementen zijn breder toegankelijk dan tekst. Visuals zoals pijlen en deeltjeseffecten communiceren zonder woorden en vereisen geen vertaling om door een wereldwijd publiek te worden begrepen. Dit helpt spelers die afhankelijk zijn van lokalisatie in andere talen, evenals UI-ontwerpers die zich geen zorgen hoeven te maken over een tekststring die langer wordt na vertaling.

Voor spellen die aantrekkelijk zijn voor jongere spelers, kan leren zonder woorden helpen voor degenen die nog leren lezen of die niet de woordenschat hebben om beschrijvingen van complexere systemen te begrijpen.

Het gebruik van visuele elementen zorgt ook voor toegankelijkheid op verschillende platforms, zoals mobiele apparaten, waar tekst te klein kan zijn om comfortabel te lezen. Visuele elementen zijn ook gemakkelijker te interpreteren, vooral voor spelers die visueel gehandicapt zijn.

Voor meer informatie over het ontwerpen van toegankelijke visuele elementen, zie deze video over [kleurcontrast](https://www.youtube.com/watch?v=syQcaeRqqc4) .

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/visual-elements-5.png) Directionele pijlen in * Winds of Fortune.*

### [Verbeter de onderdompeling](#verbeter-de-onderdompeling)[](#verbeter-de-onderdompeling)

Visuele elementen kunnen spelers helpen om ondergedompeld te blijven in de gameplay. Directionele sporen, bijvoorbeeld, bieden richting terwijl ze spelers de vrijheid geven om te verkennen en andere keuzes te maken. Ze suggereren sterk een actie, maar vereisen het niet. Terwijl de meeste spelers de aanwijzingen zullen volgen, maakt de beschikbaarheid van keuze de tutorial minder geforceerd dan wanneer ze geen andere opties hadden, en stelt het spelers in staat om ondergedompeld te blijven in het spel en in hun eigen tempo te verkennen.

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/visual-elements-6.png) Directioneel spoor in * Hello Kitty Cafe.*

### [Faciliteer feedback](#faciliteer-feedback)[](#faciliteer-feedback)

Visuele elementen kunnen worden gebruikt als feedback buiten tutorials en onboarding funnels. Feedback vindt plaats wanneer een speler een actie onderneemt en het spel reageert op een manier die de resultaten van de actie communiceert. Visuele elementen kunnen worden gebruikt om feedback te communiceren en spelers bruikbare informatie te geven om hen te helpen hun volgende keuze te maken.

Als voorbeeld, wanneer spelers in gevecht zijn in * Winds of Fortune* :

-

VFX-flitsen geven aan dat de zwaardzwaaien van de speler hun doel hebben geraakt

-

Rode cijfers vliegen van een vijand wanneer ze worden geraakt, wat schadepunten aangeeft

-

Een rode schermeffect pulserend, waarschuwt de speler dat hun gezondheid laag aan het worden is

-

Gezondheidsmeters worden bijgewerkt voor de speler en vijand

-

Wanneer een vijand wordt verslagen, vliegen munten eruit om de speler te laten weten dat ze beloningen hebben ontvangen

-

Als het verslaan van de vijand een questdoel is, wordt de teller bijgewerkt wanneer de vijand sterft

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/visual-elements-7.png) Visuele feedback in * Winds of Fortune.*

Al deze feedback vertelt spelers wanneer ze de vijand succesvol hebben geraakt, wanneer ze zelf schade hebben opgelopen, welke beloningen ze ontvangen van de overwinning, en of ze vooruitgang hebben geboekt in hun quest. De combinatie van deze visuele elementen zorgt ervoor dat de meeste spelers begrijpen wat er aan de hand is zonder dat er een meer expliciete gevechtstutorial nodig is.

Elke keer dat een speler een actie onderneemt in een spel, is het van cruciaal belang om duidelijke feedback te geven. Anders weten spelers misschien niet dat de actie die ze hebben ondernomen iets heeft gedaan, en vragen ze zich af of ze iets verkeerd hebben gedaan, of zich afvragen of het spel buggy is.

Voor meer informatie over feedback en andere best practices voor gebruikerservaring (UX), zie [UI en UX](/docs/nl-nl/production/game-design/ui-ux-design)

## [Contextuele tutorials](#contextuele-tutorials)[](#contextuele-tutorials)

Ook bekend als just in time  tutorials, zijn contextuele tutorials  tutorials die worden geactiveerd door normaal spel, zoals het betreden van een nieuwe kaartzone of het oppakken van een nieuw wapen. Door te wachten tot spelers zich natuurlijk engageren, personaliseren contextuele tutorials de instructie, wat hun relevantie en nut binnen de bredere onboarding funnel maximaliseert. Contextuele tutorials faciliteren:

-

Verhoogde leerretentie:  Spelers leren het beste door de context van een situatie te begrijpen en door te interageren met tutorials die worden geactiveerd door hun eerste interactie met een gamefunctie. Wanneer spelers acties oefenen terwijl ze deze leren, behouden ze kennis beter.

-

Snellere onboarding:  Het is belangrijk om spelers snel naar de leuke delen van een spel te leiden om ze betrokken te houden. Contextuele tutorials stellen ontwerpers in staat om lange onboarding systemen te vermijden en onnodige tutorials uit te stellen, waardoor spelers sneller plezier kunnen hebben.

-

Verminderde cognitieve belasting:  In de eerste paar minuten van een spel moeten nieuwe spelers vaak veel dingen leren, zoals interacties, mechanismen en doelen. Hoe meer ze moeten leren, hoe moeilijker het wordt om alles te onthouden, wat de kans vergroot dat ze zich overweldigd voelen en stoppen. Het uitstellen van niet-essentiële informatie naar toekomstige sessies vermindert wat ze in de eerste sessie moeten leren en onthouden, waardoor ze zich kunnen concentreren op de essentie.

Traditionele tutorialflows begeleiden spelers in een vaste volgorde door de functies van een spel, zodat ze essentiële vaardigheden en kennis leren. Hoewel deze methode effectief kan zijn voor hoge niveauconcepten, kan het leiden tot verveling of frustratie door de keuze van de speler te beperken. Contextuele tutorials verbeteren het spel door minder cruciale instructies uit te stellen en snel de controle aan de speler te geven, door alleen specifieke instructies te geven aan de relevante spelers.

### [Gebruikscases](#gebruikscases)[](#gebruikscases)

In [* Squishmallows*](https://www.roblox.com/games/7941853407/)  worden contextuele tutorials gebruikt om spelers effectief te leren hoe en wanneer ze het combinatie station moeten gebruiken. Wanneer een speler twee identieke Squishmallows in hun inventaris heeft, wordt een contextuele tutorial geactiveerd en laat het spelers zien hoe ze drie * Squishmallows*  bij het combinatie station kunnen combineren om een grotere te creëren.

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/contextual-tutorial-1.png) Contextuele combinatie station tutorial in * Squishmallows* .

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/contextual-tutorial-2.png) Contextuele combinatie station tutorial in * Squishmallows* .

Als de ontwikkelaars deze tutorial in de onboarding ervaring hadden opgenomen, zou het te lang en irrelevant maken, en spelers zouden de informatie kunnen vergeten voordat ze deze kunnen gebruiken. Het presenteren van de tutorial wanneer spelers de vereiste * Squishmallows*  hebben, moedigt onmiddellijke actie aan het combinatie station aan en helpt spelers het proces voor toekomstig gebruik te onthouden.

Contextuele tutorials leren ook niet-kernconcepten, waardoor spelers deze functies zelf kunnen leren. In * Squishmallows*  leggen deze tutorials de marktplaats uit waar spelers Squishmallows aan elkaar verkopen voor in-game valuta. Aangezien de marktplaats voornamelijk dient voor mid- en late-game spelers die zeldzame of hoog-niveau Squishmallows verhandelen, introduceren de ontwikkelaars nieuwe spelers aan de marktplaats via contextuele tutorials wanneer ze deze zelf vinden.

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/contextual-tutorial-3.png) Contextuele markttutorial in * Squishmallows* .

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/contextual-tutorial-4.png) Contextuele markttutorial in * Squishmallows* .

## [Getimede hints](#getimede-hints)[](#getimede-hints)

Getimede hints  zijn tutorial elementen die verschijnen voor spelers die moeite hebben na een vooraf bepaalde tijd om hen te helpen snel en naadloos door de onboarding funnel te komen. Spelers die extra hulp nodig hebben, kunnen vaak worden geïdentificeerd door te timen hoe lang het duurt voordat ze instructies volgen of taken voltooien.

Naast het helpen van spelers door de onboarding tutorial, kan het tonen van tijdige hints aan spelers ook:

-

Verhoogde retentie:  Getimede hints kunnen het aantal nieuwe spelers dat door een spel wordt behouden verhogen door ervoor te zorgen dat worstelende spelers de extra hulp krijgen die ze nodig hebben om te slagen en plezier te hebben. Nieuwe spelers die in het begin extra hulp nodig hebben, kunnen in de toekomst toegewijde spelers worden als ze de juiste en goed getimede ondersteuning ontvangen.

-

Verbeterde spelersautonomie:  Getimede hints stellen ontwerpers in staat om minder gestructureerde tutorialsequenties te creëren en extra lagen van ondersteuning toe te voegen, specifiek voor degenen die het nodig hebben. Dit voorkomt dat ervaren spelers zich ergeren, terwijl nieuwere spelers de kans krijgen om dingen zelf uit te zoeken. Spelers die dingen zelf uitzoeken, voelen zich doorgaans succesvoller en empowered, wat hen helpt om tutorials snel te voltooien en sneller bij het plezier te komen.

-

Oppervlakte over het hoofd geziene functies:  Getimede hints kunnen ook worden gebruikt om aandacht te vestigen op functies in een spel die niet cruciaal genoeg waren om in de onboarding op te nemen, maar die het nog steeds waard zijn om te worden belicht. Bijvoorbeeld, als een speler in hun eerste twee sessies niet met de handelsfunctie van een spel heeft gecommuniceerd, zou het benadrukken van de handelsknop in de UI hen aanmoedigen om erop te klikken en de functie voor de eerste keer te ervaren.

Bij het beslissen hoe en wanneer je getimede hints gebruikt, kan het observeren van playtesters waardevolle informatie opleveren over waar dergelijke hints nodig zijn en hoe lang je moet wachten voordat je ze weergeeft. Probeer een balans te vinden tussen het zo snel weergeven dat spelers het gevoel hebben dat ze niet de kans hebben gekregen om het zelf uit te zoeken, en zo lang wachten dat ze gefrustreerd raken.

### [Gebruikscases](#gebruikscases-1)[](#gebruikscases-1)

In [Plant](https://create.roblox.com/docs/resources/plant-reference-project)  volgen spelers een eenvoudige cyclus van zaden planten, producten verkopen en valuta investeren in grotere potten en waardevollere planten. Een geweldige kandidaat voor het gebruik van getimede hints is in de UI wanneer zaden worden geplant. Om een zaadje te planten, moeten spelers op de knop PLANT KOOLZAAD  klikken.

Hoewel de meeste spelers weinig moeite zullen hebben om te begrijpen wat ze moeten doen, is er een kans dat sommige spelers vast komen te zitten. In deze hypothetische situatie bepalen de playtestresultaten dat de meeste spelers de knop binnen 10 seconden vinden en indrukken. Het toevoegen van een highlight aan de knop na 11 seconden zou die resterende spelers de hint geven dat ze misschien moeten doorgaan, zonder de meerderheid van de spelers die het niet nodig hebben te irriteren.

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/timed-hints-1.png) Getimede hint mogelijkheid in * Plant* .

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/timed-hints-2.png) Getimede hint toepassing in * Plant* .

Een andere mogelijke plaats voor een getimede hint is tijdens de eerste verkoopmogelijkheid van de speler. Na het oogsten van sla van hun eerste paar planten, kunnen spelers hun wagen naar een van de drie marktkramen brengen om hun oogst te verkopen en de valuta te verkrijgen die nodig is voor upgrades.

Spelers kunnen in de war zijn over welke marktplaats ze moeten bezoeken om het doel te voltooien. Om dit te verlichten, kan er een pijl boven de juiste kraam worden geplaatst nadat spelers enige tijd hebben gehad om te verkennen.

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/timed-hints-3.png) Getimede hint mogelijkheid in * Plant* .

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/timed-hints-4.png) Getimede hint toepassing in * Plant* .

In beide hypothetische voorbeelden verschijnen de getimede hints alleen nadat de meerderheid van de spelers het doel heeft voltooid, en verschijnen ze alleen de eerste keer dat de taak wordt gepresenteerd. Getimede hints moeten voldoende zijn om worstelende spelers te helpen na slechts één keer te zijn getoond, en alleen worden getoond aan degenen die het nodig hebben.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
