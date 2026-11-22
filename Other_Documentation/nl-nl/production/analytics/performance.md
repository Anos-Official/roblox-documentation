<!-- Source: https://create.roblox.com/docs/nl-nl/production/analytics/performance -->

Prestaties | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Analytics](/docs/nl-nl/production/analytics)

# Prestaties

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het Prestaties  dashboard biedt actuele client- en serverstatistieken voor je game. Houd deze pagina in de gaten voor en na het bijwerken van je game om prestatieproblemen vroegtijdig te identificeren.

![Een overzicht van het prestatiedashboard.](https://prod.docsiteassets.roblox.com/assets/analytics/performance/perf-dash-overview.png)

## [Bekijk prestatiemetrics](#bekijk-prestatiemetrics)[](#bekijk-prestatiemetrics)

Om toegang te krijgen tot het prestatiedashboard, moet je de eigenaar van de game zijn of [analytische groepsrechten](/docs/nl-nl/production/analytics/analytics-dashboard#grant-group-permission)  hebben.

1.

Navigeer in de Creator Hub  naar de [Creations](https://create.roblox.com/dashboard/creations)  pagina.

2.

Selecteer in de linkerbovenhoek je account of de groep die de game bezit.

3.

Selecteer de game.

4.

Selecteer in de Monitoring  dropdown Prestaties .

Het dashboard begint met het huidige aantal gebruikers, het aantal servers waarop ze zijn verspreid, en een apparaatverdeling. Voor het dashboard om client- en server grafieken  zoals de onderstaande weer te geven, moet je game minimaal 100 dagelijkse actieve gebruikers (DAU) hebben.

Het dashboard bevat twee tabbladen, Client  en Server , samen met menu's om het datumbereik en het tijdsinterval aan te passen. Je kunt ook het Plaats  menu gebruiken om individuele plaatsen te onderzoeken in plaats van de hele game.

![Een gemarkeerd overzicht van de gebruikersinterface van het prestatiedashboard.](https://prod.docsiteassets.roblox.com/assets/analytics/performance/perf-dash-ui.png)

Het Filteren op  menu laat je wisselen tussen gemiddelden of percentielwaarden.

 ![Een weergave van het filters menu.](https://prod.docsiteassets.roblox.com/assets/analytics/performance/perf-dash-filter.png)

Bij het bekijken van grafieken of filteren:

-

P90  verwijst naar het aantal waarden dat binnen het 90e percentiel valt. Als de P90 server heartbeat 59 is, draaien 90% van de servers op of onder 59 FPS.

-

Evenzo verwijst P10  naar het 10e percentiel. Als de P10 server heartbeat 40 is, draaien 10% van de servers op of onder 40 FPS.

-

P50  is de mediaan. De helft van alle waarden valt erboven, de helft eronder.

Om de bron van een regressie te helpen identificeren, kun je alle clientprestatiemetrics uitsplitsen op Plaatsversie  en je laatste update vergelijken met eerdere versies.

Om te filteren op plaatsversie, selecteer je Plaatsversie  in het Uitsplitsen op  dropdownmenu. De grafieken worden automatisch bijgewerkt om je nieuwste versie naast alle eerdere versies weer te geven. Je kunt ook het hoofdfiltermenu gebruiken om de nieuwste plaatsversie over het hele dashboard te isoleren.

Met deze uitsplitsing kun je snel zien of je laatste release wijzigingen heeft zoals lagere framerates of een toename van out-of-memory exits in vergelijking met eerdere versies.

 ![Een weergave van het Uitsplitsen op Versie Filter menu.](https://prod.docsiteassets.roblox.com/assets/analytics/performance/perf-place-version-filter.png)

## [Clientgrafieken](#clientgrafieken)[](#clientgrafieken)

Het Client  tabblad bevat de volgende grafieken, die allemaal zijn uitgesplitst op platform of besturingssysteem:

| Grafiek | | Beschrijving |
| --- | --- |
| Gelijktijdige gebruikers | | Lijngrafiek die het aantal gebruikers in je game toont. |
| Sessietijd | | Duur dat gebruikers in je game doorbrengen. |
| Client framerate | | Lijngrafiek die clientframes per seconde toont. Voortdurend lage framerates of grote dalingen kunnen op problemen wijzen. Voor informatie over het onderzoeken van de clientframerate, zie [Client Compute](/docs/nl-nl/performance-optimization/identify#clientberekeningen) . |
| Client crashpercentage | | Lijngrafiek die clientcrashes toont, verdeeld naar beëindigde sessies per apparaattype. Pieken in het crashpercentage, vooral na een update van de game, duiden vaak op een probleem. |
| Onverwachte out-of-memory exits | | Lijngrafiek die toont hoe vaak gebruikers crashen door out-of-memory fouten, of afsluiten via een laaggeheugenwaarschuwing. Hoewel deze grafiek mogelijk niet alle out-of-memory crashes dekt vanwege telemetriebeperkingen, is deze richtinggevend nauwkeurig. Een piek na een update duidt op een regressie in het geheugengebruik die ervoor zorgt dat je gebruikers crashen. |
| Client crashaantal | | Lijngrafiek die het aantal crashes per apparaattype toont. Als je onbetrouwbare crashdata hebt vanwege een kleine steekproefgrootte, raden we aan ook het crashaantal te monitoren. |
| Client geheugengebruik | | Lijngrafiek die het geheugengebruik van de client per apparaattype toont. Voortdurende stijgingen kunnen wijzen op een geheugenlek. Zie [Geheugen](/docs/nl-nl/performance-optimization/identify#clientgeheugen) . |
| Percentage client geheugengebruik | | Lijngrafiek die het percentage van het beschikbare apparaatgeheugen toont dat de client gebruikt. Bijvoorbeeld, als de Android-lijn 100% nadert, lopen de meeste Android-apparaten die je game draaien het risico om zonder geheugen te komen en te crashen. |
| Client CPU-tijd | | Gestapelde gebiedsgrafiek die milliseconden (ms) verwerkings tijd per frame toont. Je wilt dat je client CPU-tijd zo laag mogelijk is, omdat dit direct invloed heeft op je framerates. Om een clientframerate van 60 te behalen, moet je CPU-tijd onder de 16 ms zijn. |

### [Crashpercentage](#crashpercentage)[](#crashpercentage)

Het client crashpercentage meet het aantal crashes gedeeld door het aantal beëindigde sessies. Wanneer het aantal beëindigde sessies laag is, kunnen de uitsplitsingen van het crashpercentage onbetrouwbaar worden. In deze gevallen toont de grafiek een stippellijn in plaats van een doorlopende lijn, wat aangeeft dat het datapunt onbetrouwbaar is en dat het crashpercentage kan variëren. Als je een stippellijn op je grafiek ziet, raden we aan het totale crashaantal te controleren in plaats van het client crashpercentage.

 ![Een weergave van het clientcrashes dashboard.](https://prod.docsiteassets.roblox.com/assets/analytics/performance/perf-client-crashes.png)

Als je geheugenproblemen hebt, bekijk dan de [prestatieoptimalisatie](/docs/nl-nl/performance-optimization)  gids.

## [Servergrafieken](#servergrafieken)[](#servergrafieken)

Het Server  tabblad bevat de volgende grafieken:

| Grafiek | | Beschrijving |
| Server CPU-tijd | | Gestapelde gebiedsgrafiek die milliseconden (ms) verwerkings tijd per frame toont. Om een serverframerate van 60 te behalen, moet je CPU-tijd onder de 16 ms zijn. Zie [Server Compute](/docs/nl-nl/performance-optimization/identify#serverberekeningen) . |
| Server framerate | | Lijngrafiek die de serverframerate in FPS toont. Idealiter is deze waarde altijd 60. De serverframerate is beperkt tot 60, en dalingen kunnen de clientframerate verlagen en de latentie verhogen. Zie [Script Computation](/docs/nl-nl/performance-optimization/improve#scriptberekeningen) . |
| Server geheugengebruik | | Gestapelde gebiedsgrafiek die het geheugengebruik van de server in MB toont. Probeer deze waarde onder de 50% van het [totaal servergeheugen](/docs/nl-nl/performance-optimization/identify#servergeheugen)  te houden. De grafiek toont echter niet het totale servergeheugen, dus een andere goede richtlijn is om onder de 3 GB te blijven. Als dit nummer hoog blijft of voortdurend in de loop van de tijd toeneemt, onderzoek dan manieren om [geheugengebruik te verbeteren](/docs/nl-nl/performance-optimization/improve#scriptgeheugengebruik) . |
| Servergeheugen naar leeftijd | | Gestapelde gebiedsgrafiek die het geheugengebruik van de server naar serverleeftijd toont. Als het geheugengebruik aanzienlijk toeneemt gedurende de levensduur van de server, onderzoek dan mogelijke geheugenlekken in de categorieën met de meeste groei, met name [scripts](/docs/nl-nl/performance-optimization/improve#scriptgeheugengebruik) , [fysica](/docs/nl-nl/performance-optimization/improve#fysica-geheugengebruik)  en [rendering](/docs/nl-nl/performance-optimization/improve#rendering) . |
| Gebruik van cores per server | | Lijngrafiek die het gebruik van server CPU-cores toont. Laag coregebruik in combinatie met hoge server CPU-tijd is een indicator dat je [multithreading](/docs/nl-nl/scripting/multithreading)  moet onderzoeken. Als het coregebruik hoog blijft nadat je hebt geoptimaliseerd, kun je meer server CPU reserveren met [Extended Services for Compute](/docs/nl-nl/cloud-services/extended-services#uitgebreide-diensten-voor-rekenkracht) . |
| Reken efficiëntie | | Lijngrafiek die de efficiëntie van je game vergelijkt met het Roblox-gemiddelde. Waarden boven de 100% geven een hogere efficiëntie aan dan de basislijn. Bijdragende factoren zijn het maximale aantal spelers per server (hoe hoger, hoe efficiënter) en server CPU-tijd per frame (hoe lager, hoe efficiënter). Hogere reken efficiëntie betekent een lagere ecologische impact, maar deze metric is geen indicatie van een goede of slechte spelerservaring. |

Voor een diepgaande weergave van servercrashes en out-of-memory snapshots, zie [Server crashes grafiek](/docs/nl-nl/production/analytics/crashes) .

De server CPU- en geheugengrafieken zijn standaard ingesteld op de Algemene  weergave, maar hebben dropdownmenu's voor individuele procesgroepen, zoals fysica, rendering en scripts. De som van deze categorieën is niet  allesomvattend; de server voert een kleine en doorgaans onbeduidende hoeveelheid extra werk per frame uit die niet in enige categorie is opgenomen. Daarom zijn de totale milliseconden en MB-waarden iets lager dan de werkelijkheid, maar dicht genoeg om je een duidelijk begrip van de serverprestaties te geven.

Als een categorie hoger is dan normaal of een onevenredig grote hoeveelheid tijd lijkt in te nemen, gebruik dan het dropdownmenu om verder in te zoomen op de groep en processen te identificeren die problemen kunnen veroorzaken.

 ![De server CPU-tijd grafiek die de fysica dropdown toont.](https://prod.docsiteassets.roblox.com/assets/analytics/performance/perf-dash-drilldown.png)

Om een groep of proces uit een grafiek uit te sluiten, klik op het label in de legenda.

-

CPU-categorieën en taken komen overeen met die in de [MicroProfiler](/docs/nl-nl/performance-optimization/microprofiler) , zodat je [server dumps](/docs/nl-nl/performance-optimization/microprofiler#profiel-de-server)  kunt maken, de Timers  modus kunt selecteren en vervolgens het Groepen  menu kunt gebruiken om te filteren op de problematische procesgroep.

Bijvoorbeeld, als je een potentieel probleem ziet met het samenstellen  proces onder de Fysica  groep, kun je het onder dezelfde naam in de MicroProfiler vinden:

 ![De MicroProfiler die het samenstellen proces binnen de Fysica groep toont.](https://prod.docsiteassets.roblox.com/assets/analytics/performance/perf-dash-micro.png)

-

Geheugentags komen overeen met die in [Enum.DeveloperMemoryTag](/docs/nl-nl/reference/engine/enums/DeveloperMemoryTag) , met de opmerkelijke uitzondering van CoreMemory:Total , wat gelijk is aan [Enum.DeveloperMemoryTag.Internal](/docs/nl-nl/reference/engine/enums/DeveloperMemoryTag#Internal) . Je kunt de [Developer Console](/docs/nl-nl/studio/optimization/memory-usage#geheugen)  gebruiken om tags op overmatig gebruik te controleren. Deze afbeelding toont hoe je de Developer Console kunt gebruiken om een probleem met PlaceMemory:GraphicsTexture  dat je in het dashboard ziet te onderzoeken:

 ![De Developer Console die de server geheugengebruikweergave toont.](https://prod.docsiteassets.roblox.com/assets/analytics/performance/perf-dash-dev.png)

## [Roblox-updates](#roblox-updates)[](#roblox-updates)

Elke Roblox-update bevat veel wijzigingen, waaronder functies en bugfixes. Roblox-update  annotaties stellen je in staat om de prestaties van je game te vergelijken met recente updates van het Roblox-platform.

 ![Een weergave van de Roblox-updateannotaties op het prestatiedashboard.](https://prod.docsiteassets.roblox.com/assets/analytics/performance/perf-dash-roblox-updates.png)

Sommige platforms worden onmiddellijk na de versie beschikbaar wordt gesteld aan 100% van de gebruikers vrijgegeven. Andere platforms worden geleidelijk uitgerold en hebben extra tijd nodig om de adoptie op te schalen; deze ontvangen een enkele annotatie zodra een versie beschikbaar is, zodat je het vroegst beschikbare signaal krijgt zonder visuele rommel toe te voegen.

Onmiddellijke Uitrol

-

Windows

-

macOS

-

Xbox

Geleidelijke Uitrol

-

iOS

-

Google

-

Amazon

-

Samsung

-

PlayStation

-

Meta Quest

## [Probleemoplossing](#probleemoplossing)[](#probleemoplossing)

Als je een potentieel probleem opmerkt, gebruik dan de volgende stappen om het op te lossen en te verhelpen:

1.

Controleer je recente updates en overweeg ze terug te draaien als de impact op de metrics ernstig is.

2.

Zie [Identificeer prestatieproblemen](/docs/nl-nl/performance-optimization/identify)  en [Verbeter prestaties](/docs/nl-nl/performance-optimization/improve)  voor informatie over het oplossen van problemen met servercompute, clientcompute en geheugengebruik.

3.

Gebruik ingebouwde testtools om verder in te zoomen op problemen:

-

[Developer Console](/docs/nl-nl/studio/developer-console)  voor het bekijken van fout- en logberichten en gedetailleerde informatie over geheugen en netwerken.

-

[Script Profiler](/docs/nl-nl/studio/optimization/scriptprofiler)  voor het identificeren van scripts die de meeste middelen verbruiken.

-

De [MicroProfiler](/docs/nl-nl/performance-optimization/microprofiler)  voor het visueel bekijken van niet-geoptimaliseerde delen van je game.

4.

Verzamel gebruikersfeedback van je community.

## [Client API-aanroepen na join](#client-api-aanroepen-na-join)[](#client-api-aanroepen-na-join)

Deze metric is alleen beschikbaar voor een klein aantal topgames.

De Client API-aanroepen in de eerste 60 seconden na join  metric meet het totale aantal verzoeken (API-aanroepen) dat je game doet naar Roblox-services tijdens de kritieke eerste minuut nadat een gebruiker succesvol is aangesloten.

Deze aanroepen gebeuren automatisch voor elke gebruiker die zich aansluit, dus het monitoren van deze metric kan je helpen de efficiëntie van laadtijden en de prestaties van de backend te begrijpen.

### [Toegang tot de metric](#toegang-tot-de-metric)[](#toegang-tot-de-metric)

1.

Navigeer naar je game-overzicht op de Creator Hub.

2.

Klik op de Snapshot  grafiek op Verkennen .

3.

Kies in de Selecteer een metric  dropdown Client API-aanroepen in de eerste 60 seconden na join .

![Grafiek van de client API-aanroepen metric](https://prod.docsiteassets.roblox.com/assets/analytics/performance/client-api-calls.png)

### [Monitor de metric](#monitor-de-metric)[](#monitor-de-metric)

Het primaire doel tijdens de eerste 60 seconden van een speler die zich aansluit, is om de assets van je game (mesh, afbeeldingen, geluiden, enz.) te streamen en te laden. Idealiter is de assetleveringsservice de meest aangeroepen API tijdens deze belangrijke tijdspanne.

De metric wordt elk uur bijgewerkt, zodat je deze snel kunt controleren na het publiceren van een nieuwe versie van je game.

| Voorwaarde | | Implicatie | | Actie |
| Assetlevering is de meest aangeroepen API. | | Efficiënt.  Je game prioriteert correct het laden van noodzakelijke assets. | | Blijf monitoren. |
| Een andere service (bijv. inventaris, vrienden of gebruikers) is de meest aangeroepen API. | | Potentiële inefficiëntie of bug.  Je game voert zware, niet-kritische API-aanroepen te vroeg in de joinvolgorde uit, wat mogelijk het laadproces vertraagt. | | Onderzoek en refactor de scripts die tijdens de initiële join worden uitgevoerd om het laden van assets te prioriteren. |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
