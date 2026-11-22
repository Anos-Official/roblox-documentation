<!-- Source: https://create.roblox.com/docs/nl-nl/cloud-services/memory-stores/observability -->

Geheugenopslag observability | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Clouddiensten](/docs/nl-nl/cloud-services/data-stores-vs-memory-stores)
6. /
7. [Geheugenopslag](/docs/nl-nl/cloud-services/memory-stores)

# Geheugenopslag observability

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het geheugenopslag observability-dashboard biedt realtime grafieken over je geheugengebruik en API-verzoeken. Het heeft ook een ingebouwd alarmsysteem dat je per e-mail op de hoogte stelt wanneer er een probleem optreedt, zodat je in sync kunt troubleshooten. Voor meer informatie over specifieke fouten kun je je [Foutenrapport](/docs/nl-nl/production/analytics/error-report)  bekijken om de foutlogboeken te vinden.

## [Toegang tot het dashboard](#toegang-tot-het-dashboard)[](#toegang-tot-het-dashboard)

Het geheugenopslag observability-dashboard is beschikbaar voor elk spel dat [MemoryStoreService](/docs/nl-nl/reference/engine/classes/MemoryStoreService)  gebruikt, maar je moet ofwel de eigenaar van het spel zijn of [analytische groepsrechten](/docs/nl-nl/production/analytics/analytics-dashboard#grant-group-permission)  hebben om toegang te krijgen tot het dashboard.

Om toegang te krijgen tot het dashboard:

1.

Navigeer naar de [Creaties](https://create.roblox.com/dashboard/creations)  pagina op het Creator Dashboard .

2.

Vouw de accountwisselaar in de linkerbovenhoek uit en selecteer je account of de groep die het doelspel bezit.

3.

Selecteer het spel.

4.

Selecteer in de dropdown Monitoring  de optie Geheugenopslag .

## [Beschikbare grafieken](#beschikbare-grafieken)[](#beschikbare-grafieken)

Het dashboard bevat twee categorieën lijn grafieken:

-

Quota Gebruik  grafieken voor het bijhouden van je gebruik in vergelijking met de [dynamisch toegewezen quota](/docs/nl-nl/cloud-services/memory-stores#limieten-en-quotum) , die zijn berekend op basis van het aantal gebruikers in je spel.

-

Geheugengebruik  over je geheugengebruik per minuut in bytes in vergelijking met hoeveel van je toegewezen quota over is.

-

API Verzoekeenheid  over je totale verzoekeenheden per minuut in vergelijking met hoeveel van je toegewezen quota over is. Deze grafiek kan worden uitgesplitst per API-methode.

-

API Gebruik en Prestaties  grafieken voor het monitoren van het API-gebruikspatroon en de prestaties op basis van API-methode en responsstatus.

-

Verzoektelling per API  over het aantal API-verzoeken per minuut per API-methode, zoals [MemoryStoreQueue:ReadAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreQueue#ReadAsync)  of [MemoryStoreSortedMap:UpdateAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreSortedMap#UpdateAsync) .

-

Verzoektelling per Status  over het aantal API-verzoeken per [responsstatus](#responsstatuscodes) .

-

Verzoek per API x Status  over responsstatussen die zijn geretourneerd door alle of een specifieke API-methode.

De grafiek bevat gegevens van de afgelopen 30 dagen, en je kunt ervoor kiezen om een aangepast tijdsbereik te bekijken met de selector bovenaan de pagina. Als je een tijdsbereik selecteert dat eerder is dan 30 dagen, retourneert het systeem een Verzoek Mislukt  fout.

## [Responsstatuscodes](#responsstatuscodes)[](#responsstatuscodes)

De Verzoektelling per Status  en Verzoeken per API x Status  grafieken van het Observability Dashboard bevatten statuscodes van API-responsen die je kunt gebruiken om fouten te begrijpen en op te lossen. Voor een tabel die al deze statuscodes opsomt en beschrijft, zie [Observability](/docs/nl-nl/cloud-services/memory-stores#observability) . Daarnaast, voor informatie over hoe je deze fouten kunt oplossen, of de specifieke quota of limiet waar een fout betrekking op heeft, zie respectievelijk [Probleemoplossing](/docs/nl-nl/cloud-services/memory-stores#probleemoplossing)  en [Limieten en Quota](/docs/nl-nl/cloud-services/memory-stores#limieten-en-quotum) .

## [Meldingsalerts](#meldingsalerts)[](#meldingsalerts)

Het e-mailalarmsysteem detecteert automatisch en stuurt je waarschuwingen over problemen met het gebruik van geheugenopslag die de prestaties van je spel kunnen schaden. Er zijn twee soorten waarschuwingen:

-

Waarschuwingen  zijn waarschuwingen met een lagere prioriteit over problemen die mogelijk invloed kunnen hebben op je spel. Je moet ze oplossen voordat ze kritieke problemen worden. Het dashboard markeert deze waarschuwingen door de grafiek geel te markeren met een waarschuwingsbericht.

-

Kritieke  waarschuwingen zijn waarschuwingen met een hogere prioriteit over problemen die direct invloed hebben op je spel. Je moet deze problemen zo snel mogelijk oplossen om verslechterde prestaties te voorkomen. Het dashboard markeert deze waarschuwingen door de grafiek rood te markeren met een foutmelding.

Wanneer je spel tegelijkertijd twee soorten waarschuwingen activeert, toont het dashboard de waarschuwingskoptekst en markeert het de grafiekregio voor jouw aandacht als Kritiek .

Momenteel heeft het systeem vier ingebouwde waarschuwingen voor geheugengebruik en API-verzoeken. Als je spel een waarschuwingsdrempel overschrijdt, stelt het systeem je maximaal eenmaal per dag op de hoogte voor elke waarschuwing. Wanneer je een e-mailwaarschuwing ontvangt, moet je het dashboard bekijken en acties ondernemen om verslechterde prestaties te voorkomen.

### [Geheugengebruik waarschuwingen](#geheugengebruik-waarschuwingen)[](#geheugengebruik-waarschuwingen)

Het systeem stuurt de volgende waarschuwingen voor geheugengebruik:

-

Een Waarschuwing  wanneer het geheugengebruik van je spel 70% van de totale quota heeft overschreden binnen het afgelopen uur.

 ![](https://prod.docsiteassets.roblox.com/assets/data/memory-store/Memory-Usage-Warning.png)

-

Een Kritieke  waarschuwing wanneer je spel de geheugengroottequota voor het afgelopen uur heeft overschreden.

 ![](https://prod.docsiteassets.roblox.com/assets/data/memory-store/Memory-Usage-Critical.png)

Deze problemen doen zich meestal voor wanneer je een geheugenopslaggegevensstructuur overbevolkt met te veel gegevens, wat de quota snel kan verbruiken, zelfs als je alleen verzoeken op een paar sleutels verzendt. Bijvoorbeeld, als je een lange vervaltijd op sleutels instelt of verwerkte gegevens niet opruimt, kunnen extra gegevens je geheugenquota vullen.

Om deze problemen te voorkomen en op te lossen, pas je [beste praktijken](/docs/nl-nl/cloud-services/memory-stores#beste-praktijken)  toe om bij te houden welke gegevensstructuren je actief gebruikt en stel je een mechanisme in voor het opruimen van verwerkte gegevens.

### [API-verzoek waarschuwingen](#api-verzoek-waarschuwingen)[](#api-verzoek-waarschuwingen)

Het systeem stuurt de volgende waarschuwingen voor API-verzoeken:

-

Een Kritieke  waarschuwing wanneer het aantal mislukkingen van je geheugenopslagverzoeken meer dan 20% heeft overschreden binnen het afgelopen uur.

 ![](https://prod.docsiteassets.roblox.com/assets/data/memory-store/Request-Failure-Critical.png)

-

Een Kritieke  waarschuwing wanneer meer dan 10% van je geheugenopslagverzoeken wordt vertraagd voor het afgelopen uur.

-

Deze waarschuwing is gebaseerd op het aantal DataStructureRequestsOverLimit  + TotalRequestsOverLimit , wat foutreacties zijn die aangeven dat je spel wordt vertraagd omdat het te veel verzoeken verzendt.

-

Deze waarschuwing is niet gerelateerd aan de verzoekgrootte, alleen aan de hoeveelheid.

 ![](https://prod.docsiteassets.roblox.com/assets/data/memory-store/Request-Throttled-Critical.png)

Alle API-verzoeken hebben bijbehorende [responsstatuscodes](#responsstatuscodes) , zodat je de verhouding van Succes -responsen tot alle foutresponsen kunt bekijken met de grafiek Verzoektelling per Status  voor [probleemoplossing](/docs/nl-nl/cloud-services/memory-stores#probleemoplossing) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
