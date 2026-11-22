<!-- Source: https://create.roblox.com/docs/nl-nl/production/analytics/crashes -->

Server crashes grafiek | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Analytics](/docs/nl-nl/production/analytics)

# Server crashes grafiek

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De server crashes grafiek  en server out-of-memory momentopnamen  kunnen je helpen de oorzaak van servercrashes te identificeren en de stabiliteit van je game te verbeteren.

Wanneer een server detecteert dat hij zonder geheugen komt te zitten, legt de engine automatisch een compacte JSON  samenvatting van het datamodel vast voordat de server wordt afgesloten. Als je een piek in je server out-of-memory crashes ziet, kun je de grafiek en geheugenmomentopnamen gebruiken om het probleem te diagnosticeren:

-

Selecteer een momentopname : Gebruik de lijst met server out-of-memory momentopnamen om een crash te vinden, en bekijk vervolgens het geheugengebruik op basis van de laatste tijdstempel, plaats-ID, plaatsversie, serverversie of serveruptime om langdurige geheugenlekken te vinden of de crash te koppelen aan meldingen van spelers of je eigen testvenster.

-

Visualiseer het geheugengebruik : Klik op een momentopname om de treemapviewer te openen die knooppunten toont gewogen op geheugengebruik. Je kunt in knooppunten doordringen om te zien welke services, mappen of assets het geheugen tijdens de crash domineerden.

-

Onderzoek in Studio : Gebruik de kruimelpadnavigatie bovenaan de viewer om bovenliggende containers te markeren die mogelijk opgeblazen assets bevatten. Met deze context kun je in Studio springen om het specifieke script of de asset die het probleem veroorzaakt te onderzoeken en op te lossen.

 ![Een weergave van de server crashes grafiek.](https://prod.docsiteassets.roblox.com/assets/analytics/crashes/crashes-chart.png)

## [Toegang tot de grafiek](#toegang-tot-de-grafiek)[](#toegang-tot-de-grafiek)

Om toegang te krijgen tot de server crashes grafiek, moet je ofwel de eigenaar van de game zijn of [analytische groepsrechten](/docs/nl-nl/production/analytics/analytics-dashboard#grant-group-permission)  hebben.

1.

Navigeer naar de [Creations](https://create.roblox.com/dashboard/creations)  pagina op de Creator Hub .

2.

Selecteer onder het dropdownmenu Creator Hub  je account of de groep die de game bezit.

3.

Selecteer de game.

4.

Selecteer in het dropdownmenu Monitoring  de optie Crashes .

## [Gebruik de grafiek](#gebruik-de-grafiek)[](#gebruik-de-grafiek)

De server crashes grafiek biedt diepgaande zichtbaarheid in mogelijke oorzaken van servercrashes. Crashes worden onderverdeeld op basis van de crashreden:

-

Out-of-memory crashes  - Servers crashen door hoog geheugengebruik waar je direct actie op kunt ondernemen om het op te lossen.

-

Platform crashes  - Servers crashen door engine-niveau fouten of beschadigd geheugen wanneer ze in een niet-herstelbare staat komen. Roblox monitort en onderneemt directe actie om deze crashes op te lossen.

Als je een significante stijging in platformcrashes ziet, [dien een bugrapport in](https://devforum.roblox.com/t/how-to-post-a-bug-report/24388) .

Je kunt de menu's van de grafiek gebruiken om het datumbereik, het tijdsinterval en annotaties aan te passen, en het Plaats -menu om individuele plaatsen te onderzoeken in plaats van de hele game.

 ![Een close-up weergave van de filters van de server crashes grafiek.](https://prod.docsiteassets.roblox.com/assets/analytics/crashes/crashes-chart-filters.png)

Direct onder de grafiek staat een lijst van server out-of-memory momentopnamen die je kunt onderzoeken op basis van tijdstempel, serverversie, serveruptime, plaats-ID of plaatsversie. Wanneer je een van deze momentopnamen selecteert, wordt de treemapweergave weergegeven met knooppunten gewogen op geheugengebruik.

 ![Een close-up weergave van een voorbeeldmomentopnamenlijst en open geheugenmomentopname.](https://prod.docsiteassets.roblox.com/assets/analytics/crashes/memory-snapshot.png)

Om te demonstreren hoe je de grafiek en server out-of-memory momentopnamen kunt gebruiken om een geheugenlek te diagnosticeren:

1.

Identificeer de piek . Wanneer je merkt dat out-of-memory crashes pieken in je server crashes grafiek, filter dan op plaatsversie zodat je de locatie van je geheugenlek kunt bevestigen.

 ![Een voorbeeldweergave van de server crashes grafiek met een gemarkeerde piek.](https://prod.docsiteassets.roblox.com/assets/analytics/crashes/Investigate-Spike-Example.png)

2.

Selecteer een momentopname . Scroll naar beneden naar de geheugenmomentopnamen en bekijk de lijst op basis van de laatste tijdstempel of serveruptime. Als je een momentopname selecteert van een server die binnen enkele minuten na het opstarten is gecrasht, suggereert dit een enorme, acute geheugenpiek tijdens de initialisatie.

 ![Een voorbeeldweergave van de server crashes grafiek met een gemarkeerde piek.](https://prod.docsiteassets.roblox.com/assets/analytics/crashes/Select-Snapshot-Example.png)

3.

Visualiseer het geheugen . Open de momentopname in de treemapweergave, klik vervolgens op elk knooppunt om te zien welke services, mappen of assets het geheugen tijdens de crash domineerden. Bijvoorbeeld, de treemapweergave in de volgende video benadrukt Clouds als het grootste knooppunt, en toont vervolgens dat ParticleEmitter 50% van het Clouds knooppunt uitmaakt, wat aangeeft dat zware assets in het geheugen worden gekloond bij het opstarten maar niet goed zijn geparent of vernietigd.

4.

Onderzoek en los op . Je kunt de kruimelpadnavigatie van de viewer gebruiken om de context van het opgeblazen knooppunt te traceren. Aangezien bepaalde assets dynamisch worden gegenereerd tijdens runtime, gebruik je dit pad als startpunt in het Explorer-venster van Studio, voeg je opruimlogica toe en monitor je je volgende update om de oplossing te verifiëren.

 ![Een geheugenmomentopname met de kruimelpadnavigatie gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/analytics/crashes/Investigate-Fix-Example.png)

Je kunt ook de ruwe CSV-samenvatting van de geheugenmomentopnamen downloaden voor je eigen analyse, inclusief het voeden van de gegevens in je favoriete LLM of het schrijven van je eigen parser-script.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
