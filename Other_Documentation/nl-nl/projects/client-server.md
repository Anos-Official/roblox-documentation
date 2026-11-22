<!-- Source: https://create.roblox.com/docs/nl-nl/projects/client-server -->

Client-server runtime | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Projecten](/docs/nl-nl/projects)
6. /
7. [Architectuur](/docs/nl-nl/projects/data-model)

# Client-server runtime

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

## [Server](#server)[](#server)

Roblox-spellen zijn standaard multiplayer en draaien in een client-servermodel. De Roblox server  is de uiteindelijke autoriteit voor het onderhouden van de status van het spel en is verantwoordelijk voor het synchroniseren van alle verbonden clients met de server.

![Een servergroep met verbindingen naar drie clientapparaten.](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Client-Server-Model.png) Server met verbindingen naar drie clientapparaten

## [Client](#client)[](#client)

Wanneer een spel draait, kopieert Roblox een versie van het "bewerk" datamodel dat je hebt gebouwd en gepubliceerd vanuit Studio en draait het op de Roblox-servers als het "runtime" datamodel.

Verbonden clients ontvangen ook een kopie van het runtime datamodel en elke initialisatie van de speler vindt plaats, zoals het initialiseren van de rugzak (inventaris) van een speler of de lokale gebruikersinterface. Wanneer een spel [Workspace.StreamingEnabled](/docs/nl-nl/reference/engine/classes/Workspace#StreamingEnabled)  op true is ingesteld, stuurt de server aanvankelijk alleen een subset van de inhoud onder [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  die het dichtst bij de client staat. De client rendert vervolgens de 3D-wereld en begint met het uitvoeren van eventuele toepasselijke scripts.

![Een diagram dat objecten tussen 'bewerken' en 'runtime' datamodellen in kaart brengt.](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Data-Model-Mapping.png)

## [Replicatie](#replicatie)[](#replicatie)

De server werkt voortdurend verbonden clients bij, waardoor alles gesynchroniseerd blijft over de server en clients via een proces dat replicatie  wordt genoemd, wat het datamodel, de fysica-simulatie en chatberichten synchroniseert. Replicatielogica bestaat zowel op de client als de server om synchronisatie te waarborgen.

Data Fysica Chat

Wijzigingen in het datamodel kunnen optreden in verschillende gevallen, zoals wanneer iets in de 3D-wereld wordt gemaakt of een eigenschap van de 3D-wereld verandert. Dit gebeurt meestal wanneer een script op de server of client een wijziging aanbrengt die op de andere kant van de client-servergrens moet worden weerspiegeld. De volgende diagrammen tonen veelvoorkomende scenario's voor datareplicatie.

Client → Server

![Een diagram van één client die communiceert met de server.](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Remote-Flow-Client-Server.png) Communicatie van een client naar de server. Bijvoorbeeld, een client drukt op de P -toets om een onzichtbaarheidsdrankje te drinken en vertelt de server om dat personage onzichtbaar te maken voor alle andere spelers.

Server → Client

![Een diagram van de server die communiceert met één client.](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Remote-Flow-Server-Client.png) Communicatie van de server naar één specifieke client. Bijvoorbeeld, een speler voegt zich bij het spel en de server vult de inventaris van die speler met een set items.

Server → Alle Clients

![Een diagram van de server die communiceert met alle verbonden clients.](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Remote-Flow-Server-All-Clients.png) Communicatie tussen de server en alle verbonden clients. Bijvoorbeeld, het weergeven van een afteltimer voor alle deelnemers aan een race.

De meeste spelers op Roblox hebben tussen de 100–300 milliseconden netwerkvertraging. Roblox Studio playtesting draait standaard zonder vertraging, maar je kunt de instellingen voor Netwerk Simulatie  wijzigen in de Netwerk  sectie van [Studio-instellingen](/docs/nl-nl/studio/setup#aanpassing)  (Alt S  op Windows; ⌥ S  op Mac). Gebruik een minimale vertraging van 50–150 milliseconden in zowel de inkomende als uitgaande richtingen om beter te simuleren hoe netwerkvertraging je spel zal beïnvloeden.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
