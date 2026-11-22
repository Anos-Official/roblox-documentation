<!-- Source: https://create.roblox.com/docs/nl-nl/production/analytics/get-started -->

Aan de slag met analytics | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Analytics](/docs/nl-nl/production/analytics)

# Aan de slag met analytics

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Analytics helpen je te begrijpen hoe spelers met je game omgaan, zodat je betere ontwerpbeslissingen kunt nemen. In plaats van te vertrouwen op giswerk of anekdotische feedback, kun je statistieken gebruiken om patronen te identificeren, veranderingen te evalueren en je game continu te verbeteren.

Deze gids legt uit hoe je over analytics kunt nadenken: hoe statistieken vragen over je spelers kunnen beantwoorden, hoe ze je helpen betere vragen te stellen en hoe je ze kunt gebruiken bij het beslissen wat je als volgende wilt bouwen.

## [Gebruik statistieken om vragen over je spelers te beantwoorden](#gebruik-statistieken-om-vragen-over-je-spelers-te-beantwoorden)[](#gebruik-statistieken-om-vragen-over-je-spelers-te-beantwoorden)

Statistieken bieden signalen over wat spelers in je game doen. Door belangrijke gedragingen te volgen, kun je vragen beantwoorden zoals:

Genieten spelers van een specifiek deel van de game?

-

Kijk naar de retentie of voltooiingspercentages van de onboarding-inhoud in de vroege sessies.

-

Als je merkt dat veel spelers kort na het joinen vertrekken, kan die statistiek wijzen op een probleem met de onboarding, moeilijkheidspieken of onduidelijke doelen.

-

Meet hoe vaak spelers interactie hebben met recent toegevoegde systemen of inhoud.

-

Voor meer informatie, zie [engagementstatistieken](#engagementstatistieken) .

Waar stoppen spelers met voortgang?

-

Funnel- of voortgangsstatistieken kunnen laten zien waar spelers afvallen.

-

Voor meer informatie, zie [retentiestatistieken](#retentiestatistieken) .

Werken monetisatiesystemen zoals bedoeld?

-

Volg aankooppercentages, betrokkenheid bij winkels of beloningsinlossingen.

-

Voor meer informatie, zie [monetisatie-statistieken](#monetisatiestatistieken) .

Statistieken alleen bieden niet altijd de volledige uitleg, maar ze helpen onthullen waar je beter moet kijken. Zodra je begrijpt hoe je statistieken kunt gebruiken om vragen over je gebruikers te beantwoorden, duik je in specifieke gebruikerscohorten met behulp van [segmentatie en filtering](#segmentatie-en-filtering)  filters en test je eventuele veranderingen [geleidelijk](#maak-geleidelijke-veranderingen-en-meet-resultaten) .

### [Engagementstatistieken](#engagementstatistieken)[](#engagementstatistieken)

Engagementstatistieken onthullen hoe vaak en hoe lang spelers met je game interactie hebben. Drie van de belangrijkste engagementstatistieken zijn:

-

Dagelijkse actieve gebruikers (DAU):  De dagelijkse actieve gebruikersstatistiek volgt het aantal spelers dat op een bepaalde dag in je game is. Dit is een geweldige manier om de algehele gezondheid van je game in de loop van de tijd te begrijpen. Als je op een dag 1.000.000 spelers hebt en een paar dagen later zie je een daling naar 500.000, kun je een probleem identificeren en beginnen met troubleshooten.

-

Maandelijkse actieve gebruikers (MAU):  De maandelijkse actieve gebruikersstatistiek volgt het aantal spelers dat in een bepaalde maand in je game is. Deze statistiek toont een maand-op-maand trend en kan worden gebruikt om gebruikersactiviteit over grotere tijdsbestekken te vergelijken. Sommige maanden hebben bijvoorbeeld een toename van het aantal spelers door seizoensgebonden evenementen en feestdagen. Als je aantal maandelijkse actieve gebruikers lager is in oktober vorig jaar vergeleken met deze oktober, kan dat inzicht geven dat je Halloween-evenement je gemeenschap niet heeft tevreden gesteld.

-

Gemiddelde sessieduur:  De gemiddelde sessieduur is hoe lang een speler gemiddeld je game speelt vanaf het begin van hun sessie tot het moment dat ze uitloggen. Deze statistiek helpt je inhoud te ontwerpen die binnen dat tijdsvenster past, zodat je game door de meerderheid van je spelers kan worden genoten. De gemiddelde sessieduur dient ook als een gezondheidsstatistiek. Als de gemiddelde sessieduur fluctueert na een significante update of seizoensgebonden evenement, kan dat je informeren over hoe je nieuwste inhoud werd ontvangen.

Voor kant-en-klare functionaliteit om engagementbeloningen te creëren, zie het [Engagement rewards](/docs/nl-nl/resources/feature-packages/engagement-rewards)  featurepakket.

### [Retentiestatistieken](#retentiestatistieken)[](#retentiestatistieken)

Retentiestatistieken bepalen of spelers terugkeren naar je game. Drie van de belangrijkste retentiestatistieken zijn:

-

Dag 1 (D1) retentie:  Dag 1 retentie meet hoeveel spelers op je tweede dag (D1) terugkeren naar je game vanaf de eerste dag dat ze je game spelen (D0). Een lage D1 is indicatief voor lage retentie, vaak als gevolg van een slechte gebruikersonboarding. Dit betekent meestal dat de speler in de war of gefrustreerd is, of dat ze niet snel genoeg bij het plezier komen. Om meer te leren over hoe je een effectieve onboarding-ervaring ontwerpt, zie [Onboarding](/docs/nl-nl/production/game-design/onboarding) .

-

Dag 7 (D7) retentie:  D7 retentie volgt het aantal spelers dat na 7 dagen terugkeert naar je game. Als dit aantal laag is, is het vaak indicatief voor een slecht voortgangssysteem, waarbij spelers geen tastbare reden hebben om zichzelf te zien spelen in je game een week nadat ze zijn begonnen.

-

Dag 30 (D30) retentie:  D30 retentie volgt het aantal spelers dat na 30 dagen terugkeert naar je game. Als dit aantal laag is, is het vaak indicatief voor een gebrek aan eindgame-inhoud of een gebrek aan een einddoel. Overweeg of je genoeg inhoud aan het einde van je game hebt voor ervaren spelers, of het nu gaat om quests, sociale aspecten of narratieve elementen.

### [Monetisatiestatistieken](#monetisatiestatistieken)[](#monetisatiestatistieken)

Monetisatiestatistieken geven aan hoeveel inkomsten je game genereert. Drie van de belangrijkste monetisatiestatistieken zijn:

-

Gemiddelde opbrengst per dagelijkse actieve gebruiker (ARPDAU):  ARPDAU is het gemiddelde bedrag dat spelers in je game uitgeven. Dit is een goede momentopname van de algehele gezondheid van de game. Overweeg of er succesvolle systemen in je game zijn die je spelers aanmoedigen om uit te geven.

-

Conversieratio:  De conversieratio wordt beschouwd als een van de belangrijkste statistieken. De conversieratio is het percentage van alle gebruikers die op enige manier geld hebben uitgegeven in je game. De reden waarom dit een van de belangrijkste statistieken is, is dat als een speler een eerste aankoop doet, ze veel waarschijnlijker in de toekomst opnieuw een aankoop doen. Overweeg of je monetisatiepraktijken je spelers aanmoedigen om uit te geven.

-

Gemiddelde opbrengst per betalende gebruiker (ARPPU):  De ARPPU-statistiek volgt het totale bedrag dat door alle spelers in je game is uitgegeven, ook wel spend depth  genoemd. Dit vertelt je of spelers in je game gemotiveerd zijn om veel, weinig of ergens daartussenin uit te geven. Als dit aantal laag is, is het vaak indicatief voor de waarde van aankoopitems die niet correct is geoptimaliseerd.

Om te leren hoe je systemen ontwerpt die al deze statistieken verhogen en spelers aanmoedigen om geld uit te geven in je ervaring, zie [Monetisatiegrondslagen](/docs/nl-nl/production/game-design/monetization-foundations) .

### [Segmentatie en filtering](#segmentatie-en-filtering)[](#segmentatie-en-filtering)

Bij het bekijken van de analytics van je game, kun je je gebruikersgegevens filteren op segmenten  die je helpen het gedrag van een subset van gebruikers te begrijpen. Dit stelt je in staat om je statistieken te filteren op verschillende kenmerken, zoals:

Actieve betalende status

Het segmenteren van statistieken op Actieve betalende status  helpt je te begrijpen hoe de inkomsten zijn verdeeld onder betalende spelers.

In veel games genereert een kleine groep spelers een groot deel van de inkomsten. Gemiddeld is de top 15% van actieve betalende gebruikers goed voor ongeveer 50% van de inkomsten. Om dit in je eigen game-dashboard te analyseren:

1.

Ga naar Monetisatie  > Overzicht .

2.

Selecteer Verdeling op  > Actieve Betaler Status  in de grafiek. Controleer dit over verschillende Tijdintervallen .

![Dropdown-menu om toegang te krijgen tot de filter voor Actieve betalende status](https://prod.docsiteassets.roblox.com/assets/analytics/overview/Active-Payer-Status.png)

Op basis van deze informatie kun je kansen identificeren om je game te verbeteren voor verschillende groepen uitgaven:

-

Als de top 15% aanzienlijk minder bijdraagt dan verwacht, heb je mogelijk kansen om topuitgevers beter te behouden of te monetiseren.

-

Als de top 15% aanzienlijk meer bijdraagt, moet je mogelijk de waardepropositie voor middelgrote en lagere uitgaven versterken.

Je kunt ook Gemiddelde Opbrengst Per Betalende Gebruiker (ARPPU)  op dezelfde pagina bekijken. Topbetalers geven doorgaans meerdere keren meer uit dan andere segmenten. Als ARPPU laag of dalend is, kan het zijn dat je game niet genoeg aantrekkelijke manieren biedt voor top spelers om door te gaan met uitgeven.

Om de betrokkenheid te evalueren, ga je naar de Engagement-pagina en selecteer je Verdeling  op Betaler Status . Bekijk statistieken zoals DAU , WAU , MAU  en Gemiddelde Speeltijd  om te zien of dit betalerssegment in de loop van de tijd stabiel blijft.

Wanneer de gebruiker voor het eerst speelde

Het segmenteren van spelers op Wanneer de gebruiker voor het eerst speelde  helpt je de gezondheid van verschillende spelerscohorten te evalueren die op verschillende tijden met je game zijn begonnen.

In nieuw gelanceerde games komt het merendeel van de DAU van spelers die recentelijk zijn toegetreden, meestal binnen de eerste 30 dagen. Sterke acquisitiekanalen en vroege retentie zijn vooral belangrijk in deze fase.

Naarmate een game rijpt, hangt de langetermijngroei steeds meer af van het behouden en herbetrekken van bestaande spelers. In de loop van de tijd zouden oudere cohorten een groter aandeel van de actieve gebruikers moeten vertegenwoordigen. Om dit in je eigen game-dashboard te analyseren:

1.

Navigeer naar Analytics  > Engagement .

2.

Selecteer Verdeling op  > Wanneer de gebruiker voor het eerst speelde . Controleer je gegevens over verschillende Tijdintervallen .

![Dropdown-menu om toegang te krijgen tot de filter voor Wanneer de gebruiker voor het eerst speelde](https://prod.docsiteassets.roblox.com/assets/analytics/overview/When-User-First-Played.png)

Op basis van deze informatie kun je kansen identificeren om je game te verbeteren voor verschillende groepen gebruikers:

-

Stabiele of groeiende cohorten duiden op een gezonde langetermijnbetrokkenheid.

-

Daling van cohorten benadrukt gebieden die mogelijk aandacht nodig hebben.

Bijvoorbeeld, als de 0–30 dagen cohort stabiel blijft, maar de 181–365 dagen cohort afneemt, kan de acquisitie gezond zijn terwijl langetermijnspelers zich terugtrekken. In dit geval kun je overwegen om nieuwe inhoud, evenementen of gameplay-updates in te voeren om spelers aan te moedigen terug te keren.

Platform spender status

Het segmenteren van statistieken op Platform spender status  helpt je te begrijpen hoe spelers die Robux uitgeven op Roblox met je game omgaan.

Dit segment is ook relevant voor [Dagelijkse Engagementbeloningen](/docs/nl-nl/creator-rewards#dagelijkse-betrokkenheidsbeloningen) , die een bonus bieden elke dag dat een Actieve Spender  je game speelt. Om dit in je eigen game-dashboard te analyseren:

1.

Navigeer naar Analytics  > Acquisities .

2.

Onder Platform spender status , schakel de filter Actieve spender  in en klik op Toepassen .

![Filteropties die de status van Platform spender status benadrukken](https://prod.docsiteassets.roblox.com/assets/analytics/overview/Platform-Spender-Status.png)

1.

Bekijk Unieke gebruikers met plays per bron .

![Grafiek die de bron van unieke gebruikers weergeeft, zonder filter](https://prod.docsiteassets.roblox.com/assets/analytics/overview/Unique-Users-A.png) De grafiek Unieke gebruikers met plays per bron , ongefilterd.

![Grafiek die de bron van unieke gebruikers weergeeft, gefilterd op platform spender status.](https://prod.docsiteassets.roblox.com/assets/analytics/overview/Unique-Users-B.png) De grafiek Unieke gebruikers met plays per bron , gefilterd op Actieve platformuitgevers.

Actieve uitgaven behouden doorgaans beter dan gemiddelde spelers. Daling in dit segment kan wijzen op kansen om de betrokkenheid voor zeer betrokken spelers te verbeteren.

Aangezien Dagelijkse Engagementbeloningen vereisen dat actieve uitgaven minstens 10 minuten in je game besteden, moet je ook je Engagement  > Gemiddelde Speeltijd  statistieken verifiëren. Als de gemiddelde speeltijd dicht bij of onder deze drempel ligt, voldoen veel spelers mogelijk niet aan de vereiste.

![Grafiek die de gemiddelde speeltijd in de game weergeeft, gefilterd op platform spender status.](https://prod.docsiteassets.roblox.com/assets/analytics/overview/Average-Playtime.png) Deze grafiek geeft aan dat de gemiddelde actieve betaler niet lang genoeg blijft om in aanmerking te komen voor Dagelijkse Engagementbeloningen

Je wilt misschien ook het aandeel van Actieve Spenders binnen DAU, WAU of MAU in de loop van de tijd volgen. Daling in totale aantallen of percentage-aandeel kan wijzen op verschuivingen in je publiek of kansen om de betrokkenheid te versterken.

Voor een volledige lijst van statistiekfilters, zie [Dashboard filter op statistieken](/docs/nl-nl/production/analytics/analytics-dashboard#filteren-op-statistieken) .

## [Maak geleidelijke veranderingen en meet resultaten](#maak-geleidelijke-veranderingen-en-meet-resultaten)[](#maak-geleidelijke-veranderingen-en-meet-resultaten)

Analytics kunnen helpen kansen te identificeren om je game te verbeteren, maar veranderingen zijn het meest effectief wanneer ze geleidelijk worden geïntroduceerd en in de loop van de tijd worden gemeten.

In plaats van grote updates in één keer te maken, overweeg om kleinere aanpassingen te testen en te observeren hoe het gedrag van spelers verandert. Deze aanpak maakt het gemakkelijker om te begrijpen welke veranderingen een betekenisvolle impact hebben. Gebruik de volgende tools om deze workflow te ondersteunen:

-

[Ervaringsconfiguraties](/docs/nl-nl/production/configs)  - Hiermee kun je waarden in je game aanpassen zonder een nieuwe versie te publiceren. Je kunt configuraties gebruiken om gameplay-systemen, voortgangspercentages, beloningen of andere parameters af te stemmen terwijl je game live is.

-

[Experimenten](/docs/nl-nl/production/experiments)  - Hiermee kun je verschillende versies van een functie testen met aparte groepen spelers.

Door analytics, configuraties en experimenten samen te gebruiken, creëer je een continue verbetercyclus:

1.

Analyseer  statistieken om kansen te identificeren.

2.

Maak een gerichte verandering met behulp van configuraties  of experimenten .

3.

Monitor  de resultaten over relevante statistieken.

4.

Herhaal  om de game verder te verfijnen.

Dit proces helpt je om weloverwogen beslissingen te nemen en je game te verbeteren op basis van echt spelersgedrag.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
