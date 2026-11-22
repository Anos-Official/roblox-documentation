<!-- Source: https://create.roblox.com/docs/nl-nl/studio/developer-console -->

Ontwikkelaarsconsole | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Studio](/docs/nl-nl/studio)
4. /
5. [Ontwikkelaarsforum](/docs/nl-nl/studio/developer-console)

# Ontwikkelaarsconsole

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De Ontwikkelaarsconsole  is een hulpmiddel voor het debuggen van je game wanneer je test in Studio of het in productie draait. Het toont logberichten en fouten vergelijkbaar met het [Output](/docs/nl-nl/studio/output)  venster en gedetailleerde informatie over [Geheugen](#geheugen) , [Netwerk](#netwerk) , en meer.

Je kunt de console openen tijdens een test- of live game-sessie met een van de volgende manieren:

-

Druk op F9 .

-

Typ /console  in de chat.

-

Gebruik het in-game menu:

1.

Open het in-game Roblox Menu .

 ![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Roblox-Menu-Button.png)

2.

Selecteer het tabblad Instellingen .

3.

Scroll naar beneden naar Ontwikkelaarsconsole  en klik op Openen .

## [Console secties](#console-secties)[](#console-secties)

De sneltoetsbalk bovenaan de console toont het aantal kritieke fouten en waarschuwingen, het geheugengebruik van de client en de gemiddelde pingtijd; klik op een van deze om naar de bijbehorende sectie in de console te springen. Onder de sneltoetsbalk bevindt zich een reeks hulpmiddelen zoals hieronder beschreven.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/console/Console-Summary-Bar.png)

### [Log](#log)[](#log)

Het Log  hulpmiddel toont diagnostische berichten van scripts.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/console/Log-Sections.png)

Client/server schakelen Outputfilters Opdrachtbalk

Met de client-server schakelaar kun je schakelen tussen Client  en Server  weergaven:

-

De Client  weergave toont output van client-side [LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript)  en/of [Scripts](/docs/nl-nl/reference/engine/classes/Script)  met [RunContext](/docs/nl-nl/reference/engine/classes/Script#RunContext)  ingesteld op [Enum.RunContext.Client](/docs/nl-nl/reference/engine/enums/RunContext#Client) . Iedereen die een game speelt kan lokale outputberichten bekijken.

-

De Server  weergave toont output van server-side [Scripts](/docs/nl-nl/reference/engine/classes/Script)  ([RunContext](/docs/nl-nl/reference/engine/classes/Script#RunContext)  ingesteld op [Enum.RunContext.Server](/docs/nl-nl/reference/engine/enums/RunContext#Server)  of [Enum.RunContext.Legacy](/docs/nl-nl/reference/engine/enums/RunContext#Legacy) ). Alleen de game-eigenaar of [groep](/docs/nl-nl/projects/groups)  leden met bewerkingsrechten kunnen serveroutputberichten bekijken.

### [Geheugen](#geheugen)[](#geheugen)

De Ontwikkelaarsconsole  biedt twee hulpmiddelen voor het monitoren van geheugengebruik, waaronder:

-

Geheugen  — Bekijk het realtime geheugengebruik per gebruikscategorie, inclusief geheugengebruik door zowel je aangepaste componenten als de interne processen van de engine.

-

Luau heap  — Maak snapshots van het heap-geheugen, wat verwijst naar de geheugentoewijzing aan je scripts. Dit hulpmiddel biedt verschillende weergaven van geheugentoewijzing om je te helpen de huidige geheugentoewijzing en problemen vanuit verschillende perspectieven te identificeren, zoals objecttypes en engineklassen. Het stelt je ook in staat om meerdere snapshots te maken om verschillen in geheugengebruik in de loop van de tijd te vergelijken.

Voor meer informatie, zie [Geheugengebruik](/docs/nl-nl/studio/optimization/memory-usage)

### [Netwerk](#netwerk)[](#netwerk)

Het Netwerk  hulpmiddel toont het aantal webaanroepen dat de game heeft gedaan. Dit omvat expliciete aanroepen gedaan via [HttpService](/docs/nl-nl/reference/engine/classes/HttpService)  en webverzoeken gedaan door Roblox-services zoals [DataStoreService](/docs/nl-nl/reference/engine/classes/DataStoreService) . Het Netwerk  hulpmiddel heeft twee secties:

-

De Samenvatting  sectie geeft een samenvatting van alle webaanroepen per type. Elk type heeft details over het aantal verzoeken, het aantal mislukte verzoeken en de tijd die het verzoek heeft gekost.

-

De Details  sectie geeft elke individuele webaanroep weer. Elke rij toont de HTTP-methode, zoals GET  of POST , samen met de statuscode, tijd om uit te voeren, verzoektype en verzoek-URL. Klik op een webaanroep om de responsdetails te zien, bijvoorbeeld:

{"Version":"1.1":"Content":{"Headers":[]},"StatusCode":"OK","ReasonPhrase":"OK","Headers":[],"TrailingHeaders":[],"RequestMessage":null,"IsSuccessStatusCode":true}

### [Script Profiler](#script-profiler)[](#script-profiler)

Het Script Profiler  hulpmiddel stelt je in staat om profileringssessies van alle draaiende scripts op te nemen en hun CPU-tijdkosten te bekijken met aangepaste opname- en weergave-instellingen. Het is nuttig voor het identificeren van scripts die de meeste CPU-bronnen verbruiken en de prestaties vertragen. Voor meer informatie, zie [Script Profiler](/docs/nl-nl/studio/optimization/scriptprofiler) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
