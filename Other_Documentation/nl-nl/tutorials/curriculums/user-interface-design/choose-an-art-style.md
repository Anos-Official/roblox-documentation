<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/curriculums/user-interface-design/choose-an-art-style -->

Kies een kunststijl | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Kies een kunststijl

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Kiezen van een kunststijl  is het proces van het plannen van een esthetische richting voor je UI-elementen. Het is belangrijk om je ontwerpproces te beginnen met een kunststijl, omdat kunststijlen visuele basisregels bieden waar je naar kunt verwijzen om ervoor te zorgen dat je UI intuïtief informatie aan spelers biedt over wat ze kunnen doen in je spel.

Met behulp van het [voorbeeld laser tag spel](https://www.roblox.com/games/14817965191/Laser-Tag-1A)  .rbxl  bestand als referentie, laat deze sectie van het gebruikersinterface-curriculum je zien hoe je betekenisvolle beslissingen kunt nemen over hoe je je UI-elementen ontwerpt volgens het genre van je spel, inclusief richtlijnen over:

-

Het identificeren van noodzakelijke UI-elementen op basis van wat je aan spelers wilt communiceren gedurende je spel.

-

Het selecteren van een kleurthema dat genre-specifieke kleurconventies versterkt die intuïtief zijn voor je publiek.

-

Het schetsen van eenvoudige iconen die gemakkelijk te ontcijferen zijn op elk schermformaat.

-

Het vaststellen van een volgorde van knoppen die overeenkomt met de waarschijnlijkheid van verschillende spelerswerkstromen.

-

Het bepalen van een tekstsysteem dat zorgt voor leesbaarheid op doelapparaten.

Nadat je deze sectie hebt voltooid, leer je hoe je de structuur en flow van de informatie die je aan spelers wilt communiceren via UI binnen je spel ontwerpt.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/user-interface-design/Section1/Intro.jpg)

## [Identificeer je UI-elementen](#identificeer-je-ui-elementen)[](#identificeer-je-ui-elementen)

De eerste stap in het kiezen van een kunststijl voor je UI is het identificeren van welke UI-elementen je nodig hebt voor de verschillende soorten informatie die je aan je publiek wilt communiceren. Dit werk aan het begin van je ontwerpproces is cruciaal omdat het je in staat stelt om UI-elementen te categoriseren op basis van hun functionele doel, semantische beslissingen te nemen op basis van waar en wanneer spelers met elk UI-element gaan interageren, en te plannen waar je UI-elementen in je spel kunt hergebruiken.

Er zijn veel verschillende manieren om te brainstormen welke UI-elementen noodzakelijk zijn voor je gameplay-eisen, maar het wordt aanbevolen om te beginnen met het visualiseren van wat een speler moet weten zodra ze je spel betreden. Bijvoorbeeld, wanneer een speler het voorbeeld laser tag spel opent, kan hij of zij zichzelf de volgende vragen stellen:

-

Wat is het doel van het spel?

-

Hoe weet ik wie er in mijn team zit?

-

Hoe houd ik de punten van mijn team bij?

-

Hoe selecteer ik een blaster?

-

Hoe weet ik waar de blaster een laser schiet?

-

Als ik op een mobiel apparaat ben, hoe schiet ik dan met mijn blaster?

-

Nadat ik een laser heb geschoten, wanneer kan ik weer schieten?

-

Hoe weet ik wanneer ik de ronde begin?

-

Hoe weet ik wanneer ik iemand succesvol heb getagd met mijn blaster?

-

Hoe weet ik wanneer het vijandige team mij succesvol tagt?

Door deze vragen te gebruiken om te begrijpen welke informatie essentieel is voor spelers om succesvol te zijn, kun je de UI-behoeften van het voorbeeld laser tag spel indelen in drie categorieën:

1.

Informatie over het doel van het spel.

2.

Informatie over de blaster.

3.

Informatie over de status van de speler.

Het sorteren van de UI-behoeften van je spel in categorieën is nuttig omdat je je kunststijl kunt formuleren rond elke groep om te versterken welke informatie elke categorie moet onderwijzen aan spelers. Bijvoorbeeld, als je wilt dat je UI spelers vertelt welke acties ze kunnen ondernemen met betrekking tot de gezondheidstoestand van hun personage, kun je een kunststijl kiezen met UI-elementen die prioriteit geven aan de kleur groen en/of plus-iconen, zodat spelers snel hun functie kunnen herkennen.

Nadat je de UI-behoeften van je spel in categorieën hebt gesorteerd, kun je een lijst maken van de UI-elementen die nodig zijn om aan de vereisten van elke categorie te voldoen. Ter illustratie gebruikt het voorbeeld laser tag spel de volgende tabel van UI-elementen om de vorige lijst van potentiële spelersvragen aan te pakken. Terwijl je door deze tutorial werkt, zal het UI-curriculum blijven verwijzen naar deze lijst en belangrijke ontwerpbeschikkingen benadrukken die verband houden met elke categorie van UI-elementen.

| Categorie | | UI-elementen |
| --- | --- |
| Informatie over het doel van het spel | |
-

Doelprompt

-

Puntenteller van het team

-

Teamindicator

 |
| Informatie over de blaster | |
-

Blasterselector

-

Doelwit

-

Hitmarker

-

Cooldownmeter

-

Schietknop voor mobiele apparaten

 |
| Informatie over de status van de speler | |
-

Forcefield-scherm wanneer de speler de ronde aan het joinen of opnieuw joinen is

-

Respawn-scherm wanneer de speler is getagd

-

Indicator wanneer vijandige spelers zijn getagd

 |

Nu je een lijst van UI-elementen voor je spel hebt, is het tijd om stylistische en semantische keuzes te maken voor elke groep UI-elementen, te beginnen met een kleurthema.

## [Selecteer een kleurthema](#selecteer-een-kleurthema)[](#selecteer-een-kleurthema)

Een kleurthema , of kleurenpalet, is een selectie van kleuren die elk een boodschap communiceren door consistente toepassing binnen je spel, zoals het gebruik van een heldere kleur om aan te geven wanneer iets selecteerbaar is. Het toepassen van een kleurthema op je UI-elementen is belangrijk, vooral wanneer je vertrouwt op kleurconventies binnen het genre van je spel, omdat het spelers in staat stelt om je UI snel te begrijpen met minimale inspanning.

In het [Environmental Art Curriculum](/docs/nl-nl/tutorials/curriculums/environmental-art)  is elk deel van de laser tag omgeving kleurgecodeerd vanuit een bovenaanzicht om te differentiëren welke gebied van de kaart dicht bij de respectieve spawnzone van elk team ligt: mint  voor het team dat aan de linkerkant van de kaart samenkomt, en carnation pink  voor het team dat aan de rechterkant van de kaart samenkomt. Deze specifieke kleuren zijn nuttig omdat ze complementair  zijn, wat betekent dat ze elkaar goed contrasteren, en spelers in staat stellen om gemakkelijk hun omgeving te scannen en zich te oriënteren, ongeacht welke richting ze in het gebouw staan.

![De deur aan de mintgroene kant van de kaart.](https://prod.docsiteassets.roblox.com/assets/tutorials/user-interface-design/Section1/GreenLeft.jpg) Pastel Blauw-groen

![De deur aan de carnation pink kant van de kaart.](https://prod.docsiteassets.roblox.com/assets/tutorials/user-interface-design/Section1/PinkRight.jpg) Carnation Pink

Het voorbeeld laser tag spel gebruikt ditzelfde kleurthema in zijn UI om informatie te benadrukken die betrekking heeft op elk team, zoals de teamindicator van elke speler binnen de 3D-ruimte, of de puntenteller van het team die over het scherm wordt weergegeven. Deze consistentie helpt spelers om snel informatie over het doel van het spel te begrijpen tijdens de snelle gameplay van een first-person shooter spel, vooral omdat spelers snel beslissingen moeten nemen terwijl ze door de omgeving navigeren.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Creating-Teams/Objective-UI.jpg) Een preview van de puntenteller van het team in het voorbeeld laser tag spel.

Bij het selecteren van een kleurthema voor je eigen spel, overweeg het volgende:

-

De kracht van een kleurthema hangt af van het helpen van spelers om snelle mentale associaties te maken tussen elke kleur en hun functie. Om deze reden, beperk je kleurthema  tot alleen de belangrijkste informatie die je wilt dat spelers associëren met je UI-elementen.

-

Om ervoor te zorgen dat spelers met kleurenblindheid de boodschap van je kleurthema kunnen begrijpen, verlaat je niet altijd op kleur alleen  om UI-elementen te onderscheiden. Combineer in plaats daarvan kleuren met iconen, vormen en/of animaties om ervoor te zorgen dat je UI effectief communiceert met elke speler.

-

Het is belangrijker dat je UI leesbaar is dan esthetisch aantrekkelijk. Om deze reden, prioriteer eenvoudige UI  met kleuren die leesbaar blijven over zowel lichte als donkere elementen in de 3D-wereld.

Om de richtlijnen in het laatste punt te benadrukken, maakt het voorbeeld laser tag spel gebruik van de neutrale kleuren zwart en wit voor bijna elk ander UI-element dat over het 2D-scherm wordt weergegeven. Zwart en wit contrasteren goed met elkaar, en ze zijn gemakkelijk te lezen terwijl de rest van het scherm een anders kleurrijke 3D-omgeving weergeeft.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/user-interface-design/Section1/PlayerInfoPreview.png)

## [Schets eenvoudige iconen](#schets-eenvoudige-iconen)[](#schets-eenvoudige-iconen)

Een icoon  is een symbool dat een actie, object of concept in een spel vertegenwoordigt. Het schetsen van iconen die eenvoudig en intuïtief zijn, is belangrijk omdat het eindresultaat spelers in staat stelt om gemakkelijk te herkennen wat ze kunnen doen en wat je hen wilt vertellen via je UI zonder tekst te gebruiken, wat het scherm kan rommelen en de aandacht kan afleiden van inhoud die belangrijk is. Dit proces is nog crucialer als je publiek je spel benadert via een klein scherm op mobiele apparaten.

Eenvoudige iconen hebben idealiter een duidelijke stijl die verschilt van je 3D-elementen, terwijl ze toch de algehele wereld van je spel aanvullen. Bijvoorbeeld, in de uiteindelijke omgeving van het [Environmental Art Curriculum](/docs/nl-nl/tutorials/curriculums/environmental-art) , hebben zowel modulaire als prop 3D-assets een schone, high-tech kunststijl die gebruik maakt van rechthoekige vormen met zachte, afgeronde hoeken. Van de afgeschuinde panelen langs de vloer tot de bijna ronde ramen in het plafond, bevat niets een scherpe rand.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/SAPackages-Intro.jpg)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section3/SettingParameters-CanCollide.png)

Om deze kunststijl aan te vullen terwijl ze uniek blijven, bevatten alle UI-elementen die je later in deze tutorial zult leren maken een futuristische esthetiek en ronde hoeken zonder de vormtaal van de 3D-assets in de omgeving te evenaren. Dit houdt de betekenis van elk icoon distinct van andere informatie in zowel de 2D- als 3D-ruimte.

Om dit concept te demonstreren, zie de volgende twee afbeeldingen van het voorbeeld laser tag spel van de doelwit dat spelers vertelt waar hun blaster op het scherm schiet, en de knop die spelers in staat stelt om hun blaster op mobiele apparaten te schieten. Beide iconen hebben zachte hoeken om samenhangend te zijn met de algehele wereld, maar hun hexagonale en cirkelvormige vormen onderscheiden hen van alles wat een speler met de iconen in het spel zou kunnen associëren.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/user-interface-design/Section3/CrosshairIcon.jpg)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/user-interface-design/Section3/BlastButtonIcon-Default.jpg)

Bij het schetsen van eenvoudige iconen voor je eigen spel, overweeg het volgende:

-

Eenvoudige iconen zijn leesbaar, zelfs wanneer ze klein zijn. Om deze reden, beperk details op je iconen  die onherkenbaar zouden worden op mobiele apparaten.

-

Iconen zijn krachtig omdat ze een boodschap kunnen communiceren, ongeacht de taal van de speler. Zolang het de begrip van de speler over je UI niet beïnvloedt, vervang onnodige tekst door iconen  om de lokalisatie-inspanningen te verbeteren.

-

Veel spellen van hetzelfde genre gebruiken iconen die stylistisch vergelijkbaar zijn, zoals een zwaardicoon dat kracht vertegenwoordigt, of een kolf die magie vertegenwoordigt. Omarm de symboliek binnen het genre van je spel  zodat spelers je iconen kunnen begrijpen zonder aanvullende begeleiding.

Als je niet weet welke soorten iconen gebruikelijk zijn binnen het genre van je spel, kijk dan eens naar de [Game UI Database](https://gameuidatabase.com/) . Deze gratis hulpmiddel voor UI-ontwerpers bevat screenshots van honderden spellen van verschillende genres die je kunt raadplegen tijdens je ontwerpproces.

## [Stel een interactievolgorde vast](#stel-een-interactievolgorde-vast)[](#stel-een-interactievolgorde-vast)

Een interactievolgorde  is de volgorde van interacties die spelers kunnen hebben met je UI. Aangezien er vaak meerdere interactieve UI-elementen op het scherm zijn, is het belangrijk om een intuïtieve interactievolgorde vast te stellen om spelers te helpen beslissingen te nemen terwijl ze verschillende werkstromen navigeren.

Er zijn doorgaans drie soorten interacties in een workflow:

-

Primaire Interactie  – De actie die een speler het meest waarschijnlijk zal uitvoeren.

-

Secundaire Interactie  – De actie die een speler waarschijnlijk zal uitvoeren als alternatief voor de primaire actie.

-

Tertiaire Interactie  – De actie die een speler het minst waarschijnlijk zal uitvoeren.

Elke interactietype moet een ander niveau van visuele nadruk hebben, afhankelijk van de waarschijnlijkheid dat een speler de actie uitvoert. Om dit concept te illustreren, bekijk de volgende afbeelding van de interactievolgorde voor de workflow om een blaster te selecteren in het voorbeeld laser tag spel, waarin A de primaire interactie vertegenwoordigt, B de secundaire interactie en C de tertiaire interactie.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/user-interface-design/Section1/BlasterInteractionOrder.png)

In deze workflow is de actie die een speler het meest waarschijnlijk zal uitvoeren het selecteren tussen de twee verschillende soorten blasters, dus de blasterknoppen zijn veel groter dan elk ander interactief element in het ontwerp. Dit niveau van visuele nadruk trekt de aandacht van de speler en leidt hun blik naar het midden van het algehele UI-element. Nadat de speler zijn of haar beslissing heeft genomen, is de logische volgende stap in de workflow om hun selectie te bevestigen en de ronde te starten. Om deze reden staat de SELECT-knop direct onder de primaire interactie.

Hoewel het onwaarschijnlijk is, kan de speler niet weten dat ze een van de blasterknoppen kunnen selecteren om te communiceren welke blaster ze willen gebruiken. Om in deze situatie te helpen, zijn er twee pijl tertiaire knoppen die de speler kan gebruiken om tussen hun keuzes te cyclus. Deze knoppen zijn subtiel en veel kleiner dan de elementen van de primaire en secundaire interacties, maar ze zijn ook waarneembaar voor de speler die richting nodig heeft over welke acties ze kunnen uitvoeren.

Als je deze primaire, secundaire en tertiaire interacties in een andere interactievolgorde zou plaatsen, zoals het verwisselen van de SELECT-knop met de linker pijlknop, zouden spelers geen duidelijke richting hebben over de volgorde van keuzes die ze moeten maken. Om deze reden, naast de visuele nadruk van een knopvolgorde, volgen effectieve workflows een visuele hiërarchie  die spelers door jouw ideale volgorde van beslissingen leidt op basis van de richting waarin ze waarschijnlijk informatie scannen, zoals van boven naar beneden en van links naar rechts.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/user-interface-design/Section1/BlasterFlow.png) Het succes van dit ontwerp is dat het natuurlijk is voor spelers die vertrouwd zijn met zowel van links naar rechts als van rechts naar links talen!

Bij het vaststellen van een interactievolgorde voor de workflows in je eigen spel, overweeg het volgende:

-

Spelers moeten een duidelijk begrip hebben van wanneer ze met je UI kunnen interageren om acties uit te voeren. Om deze reden wordt aanbevolen om ten minste één vorm van visuele feedback te bieden  voor interactieve UI-elementen, zoals het weergeven van een omtrek of het veranderen van de grootte, kleur of animatie van een knop wanneer deze in focus is.

-

Als labels op interactieve UI-elementen vaag of vergelijkbaar zijn met elkaar in dezelfde workflow, kunnen spelers verkeerd begrijpen hoe ze een actie of proces moeten voltooien. Om een negatieve spelerservaring te voorkomen, creëer labels die duidelijk, beknopt en van elkaar te onderscheiden zijn .

-

Als interactieve UI-elementen te groot zijn, kunnen ze afleiden van andere belangrijke informatie op het scherm. Omgekeerd, als ze te klein zijn, kunnen ze moeilijk te lezen of moeilijk te selecteren zijn, vooral als ze dicht bij elkaar staan op mobiele apparaten. Om deze reden is het essentieel om de grootte van je interactieve UI-elementen op verschillende schermformaten te controleren .

In [Implement in Studio](/docs/nl-nl/tutorials/curriculums/user-interface-design/implement-designs-in-studio)  leer je hoe je [UIAspectRatioConstraint](/docs/nl-nl/reference/engine/classes/UIAspectRatioConstraint)  objecten kunt gebruiken om ervoor te zorgen dat UI-elementen een specifieke beeldverhouding behouden, ongeacht welk apparaat spelers gebruiken om toegang te krijgen tot je spel. Naast het vergemakkelijken van je ontwerpproces, kan deze techniek je ook helpen om te voldoen aan de Web Content Accessibility Guidelines' [Touch Target Size and Spacing](https://w3c.github.io/Mobile-A11y-TF-Note/#targetSize)  aanbeveling om een aanraakzone voor interactieve UI-elementen te creëren die minstens 9x9 mm is op mobiele apparaten.

## [Bepaal een tekstsysteem](#bepaal-een-tekstsysteem)[](#bepaal-een-tekstsysteem)

Een textsysteem  is een set regels over lettertypen en stijl voor alle woorden in je UI, zoals "altijd vetgedrukte koppen" of "gebruik groene tekst bij het verwijzen naar een gezondheidsstatistiek." Het vroegtijdig bepalen van een tekstsysteem in je ontwerpproces stelt je in staat om een structuur te hebben die je consistent kunt toepassen in je spel, zodat spelers weten wat ze kunnen verwachten terwijl ze zoeken naar de informatie die ze nodig hebben.

Hoewel textsystemen kunnen variëren afhankelijk van het genre van het spel of de vereisten van de 3D-wereld, is de belangrijkste regel die alle textsystemen moeten volgen om ervoor te zorgen dat al je UI-tekst duidelijk en gemakkelijk te lezen is . Door deze regel als basis te gebruiken voor alle beslissingen met betrekking tot je textsysteem, kun je de toegankelijkheid en gebruikerservaring voor spelers die je UI lezen verbeteren door rekening te houden met de verschillende manieren waarop spelers met je tekst kunnen interageren, zoals:

-

Het apparaat dat spelers mogelijk gebruiken om toegang te krijgen tot je spel.

-

De taal waarin spelers je gelokaliseerde tekst kunnen lezen.

-

De mogelijke onderliggende achtergrond achter de tekst op het scherm.

Bijvoorbeeld, het volgende schermresponsontwerp van wanneer een speler is getagd, schaalt naar een kleinere of grotere lettergrootte afhankelijk van het apparaat van de speler, bevat voldoende ruimte aan beide zijden van de Engelse tekst voor talen met langere vertalingen, en bevat een contrasterende achtergrond zodat spelers de tekst kunnen lezen, ongeacht welke kleur er op hun achtergrond staat.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/user-interface-design/Section1/RespawningPreview.png)

Bij het bepalen van een tekstsysteem voor je eigen spel, overweeg het volgende:

-

Tekst is moeilijk te lezen wanneer het opgaat in de ruis van zijn achtergrond. Om de leesbaarheid van je UI te verbeteren, weergeef tekst bovenop een contrasterende kleur of met een omtrek .

-

Als je je tekst niet schaalt voor verschillende apparaten, neemt de tekst ofwel te veel ruimte in of wordt deze klein en onleesbaar op het scherm van de speler. Om discrepanties in je tekst op te vangen, test je ontwerp op meerdere apparaten  gedurende het ontwerpproces.

-

Woorden kunnen verder gaan dan je oorspronkelijke ontwerp wanneer je ze in andere talen lokaliseert. Om de samenstelling van je ontwerp te verbeteren, verwijs naar de meeste ruimte die je tekst op het scherm kan innemen .

-

Hoewel sommige lettertypen bij de esthetiek van je spel kunnen passen, kunnen ze moeilijk te lezen zijn in grote hoeveelheden. Om deze reden, gebruik gestileerde tekst spaarzaam , zoals voor titels of waarschuwingsberichten.

Zodra je een plan hebt voor de kunststijl van je UI, kun je doorgaan naar de volgende sectie van de tutorial om te leren hoe je de lay-out van elk element in verschillende spelerswerkstromen kunt wireframen.

[Volgende](/docs/nl-nl/tutorials/curriculums/user-interface-design/wireframe-your-layouts)[Vorige](/docs/nl-nl/tutorials/curriculums/user-interface-design)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
