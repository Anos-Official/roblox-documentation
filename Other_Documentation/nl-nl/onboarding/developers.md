<!-- Source: https://create.roblox.com/docs/nl-nl/onboarding/developers -->

Inwerken voor ontwikkelaars | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Platform](/docs/nl-nl/get-started)
4. /
5. [Get started for experienced creators](/docs/nl-nl/onboarding)

# Inwerken voor ontwikkelaars

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Deze pagina behandelt de basisprincipes van Roblox die ingenieurs die van andere engines komen het vaakst nodig hebben in hun eerste weken. Elke sectie legt het kernidee uit en linkt naar de gedetailleerde gids.

## [Veelvoorkomende termen](#veelvoorkomende-termen)[](#veelvoorkomende-termen)

-

Spel:  Een verzameling plaatsen waar spelers zich aansluiten via de startplaats  van het spel. Datastores, geheimen, analyses en in-game aankopen zijn allemaal beperkt tot het spel, dat je ook een ervaring of een universum kunt noemen.

-

Plaats:  Een scène of zone binnen een spel, met zijn eigen datamodel. Elke server draait één plaats, en het verplaatsen van spelers tussen plaatsen vereist een [teleport](/docs/nl-nl/projects/teleport) .

-

Instantie:  Een knooppunt in het datamodel, met eigenschappen, methoden en gebeurtenissen. [Parts](/docs/nl-nl/reference/engine/classes/Part)  en [Models](/docs/nl-nl/reference/engine/classes/Model)  zijn de meest voorkomende instanties voor het bouwen van fysieke objecten.

-

Asset:  Geüpload inhoud met een wereldwijd unieke asset-ID, zoals een afbeelding, mesh, geluid of animatie. Sommige assettypes, zoals modellen en animaties, kunnen ter plaatse worden bijgewerkt, terwijl andere, zoals afbeeldingen en geluiden, vereisen dat er een nieuwe asset wordt geüpload.

-

Script:  Code die is opgeslagen als een instantie in het datamodel. Het kopiëren van een script maakt een volledige, onafhankelijke kop, geen verwijzing naar een bronbestand.

Voor meer informatie over hoe spellen en plaatsen zich verhouden, zie [Spellen en plaatsen](/docs/nl-nl/production/publishing/publish-games-and-places) .

## [Structuur van het datamodel](#structuur-van-het-datamodel)[](#structuur-van-het-datamodel)

Het [datamodel](/docs/nl-nl/projects/data-model)  is de boom van instanties die een plaats vormt. De top-level services hebben elk een specifiek doel en replicatiegedrag:

| Service | | Wat daar hoort |
| --- | --- |
| [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) | | De enige 3D-wereld van de plaats. Wanneer je het in Studio bewerkt, bewerk je het zicht van de server op de wereld, en een deel ervan wordt gerepliceerd naar elke client. |
| [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) | | Modules, clientcode, effecten en andere instanties die zowel de client als de server altijd nodig hebben. |
| [ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst) | | Inhoud die als eerste naar clients wordt gerepliceerd, meestal laadschermen. |
| [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage) | | Server-only instanties waar clients geen constante toegang toe nodig hebben, zoals kaarten die je in en uit de workspace wisselt. |
| [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService) | | Server-only scripts en modules. |
| [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui) | | [ScreenGuis](/docs/nl-nl/reference/engine/classes/ScreenGui)  en andere UI die naar elke speler wordt gekopieerd. |
| [StarterPlayer](/docs/nl-nl/reference/engine/classes/StarterPlayer) | | Scripts en instellingen voor spelers en personages, hoewel grotere projecten meestal de code in [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  houden. |

 ![Het bewerken van het datamodel naast het runtime datamodel, dat laat zien hoe StarterGui, StarterPack, StarterCharacterScripts en StarterPlayerScripts naar elke speler en elk personage worden gekopieerd tijdens runtime.](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Data-Model-Mapping.png)

De hiërarchie in de Explorer  is voornamelijk organisatorisch:

-

Onderdelen gebruiken wereldruimte-transformaties, niet transformaties ten opzichte van hun ouder. Om onderdelen aan elkaar te bevestigen, gebruik je beperkingen, meestal een [WeldConstraint](/docs/nl-nl/reference/engine/classes/WeldConstraint) . Voor details, zie [Mechanische beperkingen](/docs/nl-nl/physics/mechanical-constraints) .

-

[Attachments](/docs/nl-nl/reference/engine/classes/Attachment)  zijn een uitzondering, omdat ze zich positioneren ten opzichte van hun ouderonderdeel.

-

[Models](/docs/nl-nl/reference/engine/classes/Model)  gebruiken hun [PrimaryPart](/docs/nl-nl/reference/engine/classes/Model#PrimaryPart)  als referentiepunt voor het verplaatsen en draaien van het hele model.

## [Scriptingmodel](#scriptingmodel)[](#scriptingmodel)

In de meeste gevallen heb je slechts twee soorten scripts nodig:

-

Een [Script](/docs/nl-nl/reference/engine/classes/Script)  met zijn [RunContext](/docs/nl-nl/reference/engine/classes/BaseScript#RunContext)  ingesteld op [Server](/docs/nl-nl/reference/engine/enums/RunContext)  of [Client](/docs/nl-nl/reference/engine/enums/RunContext) .

-

Een [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript) , dat een waarde retourneert die andere scripts laden met require() . Gebruik modules voor gedeelde bibliotheken, functies en gegevens.

Vermijd de Legacy  runcontext en [LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript) . Hun gedrag hangt af van waar ze zijn geplaatst, wat het organiseren van code moeilijker maakt. Voor aanbevolen locaties, zie [Scripttypes en locaties](/docs/nl-nl/scripting/locations) .

Server scripts repliceren nooit naar clients. Modules repliceren naar clients wanneer ze in een container staan die clients kunnen openen, zoals [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) . Houd server-only modules in [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService)  of [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage) .

## [Netwerken en replicatie](#netwerken-en-replicatie)[](#netwerken-en-replicatie)

Roblox gebruikt een [client-servermodel](/docs/nl-nl/projects/client-server) :

-

Wijzigingen die de server aan instanties aanbrengt, inclusief eigenschappen, attributen en tags, repliceren automatisch naar clients.

-

Wijzigingen die een client aanbrengt, repliceren niet naar de server, met een paar uitzonderingen. De belangrijkste uitzonderingen zijn de fysica voor onderdelen die de client [bezit](/docs/nl-nl/physics/network-ownership) , zoals zijn eigen personage, en invoer van het [invoersysteem](/docs/nl-nl/input/input-action-system) .

-

De engine verdeelt de fysicasimulatie tussen de server en clients. Clients simuleren de onderdelen die ze bezitten en sturen posities en snelheden naar de server.

Om te communiceren tussen de client en server, gebruik je [remote events en callbacks](/docs/nl-nl/scripting/events/remote) :

-

[RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  en [RemoteFunction](/docs/nl-nl/reference/engine/classes/RemoteFunction)  zijn betrouwbaar en geordend.

-

[UnreliableRemoteEvent](/docs/nl-nl/reference/engine/classes/UnreliableRemoteEvent)  is onbetrouwbaar en ongeordend, voor frequente updates waarbij een verloren bericht niet uitmaakt.

-

Remotes zijn standaard niet beveiligd. Valideer altijd de gegevens die de server van clients ontvangt.

 ![Een diagram van één client die communiceert met de server.](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Remote-Flow-Client-Server.png)

### [Serverautoriteit](#serverautoriteit)[](#serverautoriteit)

Voor competitieve spellen maakt [serverautoriteit](/docs/nl-nl/projects/server-authority)  de server autoritatief over fysica en gameplay, terwijl clients hun eigen personages en nabijgelegen fysica-objecten voorspellen. Wanneer een client verkeerd voorspelt, wordt deze teruggedraaid en opnieuw gesimuleerd.

## [Invoer](#invoer)[](#invoer)

Behandel invoer met het [invoersysteem](/docs/nl-nl/input/input-action-system) . Je definieert acties, zoals springen of sprinten, in [InputContext](/docs/nl-nl/reference/engine/classes/InputContext)  instanties en bindt ze aan toetsen, knoppen en aanraakbedieningen met [InputBinding](/docs/nl-nl/reference/engine/classes/InputBinding)  instanties. Wanneer je serverautoriteit gebruikt, moet elke [InputContext](/docs/nl-nl/reference/engine/classes/InputContext)  een afstammeling zijn van een [Player](/docs/nl-nl/reference/engine/classes/Player) , zodat de engine weet welke speler het bezit. Een benadering is om je contexten in [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  te houden en ze naar elke speler te klonen vanuit een server script. Voor details, zie [Invoeren acties](/docs/nl-nl/projects/server-authority#invoergebeurtenissen) .

 ![Een InputContext-instantie genaamd PlayContext binnen ReplicatedStorage.](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-InputContext.png)

## [Streaming](#streaming)[](#streaming)

[Instantie streaming](/docs/nl-nl/workspace/streaming)  laadt delen van de workspace naar elke client terwijl spelers door de wereld bewegen, wat de laadtijden en het geheugen laag houdt op alle apparaten.

-

Instanties in [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  repliceren volledig wanneer een speler zich aansluit, voordat scripts worden uitgevoerd, zodat ze onmiddellijk veilig toegankelijk zijn.

-

Instanties in de workspace streamen in en uit. Clientcode moet omgaan met instanties die nog niet zijn geladen.

-

Instanties die door beperkingen zijn verbonden, streamen samen om de fysica stabiel te houden.

Elke [Model](/docs/nl-nl/reference/engine/classes/Model)  heeft een [ModelStreamingMode](/docs/nl-nl/reference/engine/classes/Model#ModelStreamingMode)  die controleert hoe het streamt:

| Modus | | Gedrag | | Goed voor |
| [Default](/docs/nl-nl/reference/engine/enums/ModelStreamingMode#Default) | | Onderdelen streamen individueel, zodat een model gedeeltelijk kan worden geladen. | | Statische omgevingsstukken |
| [Atomic](/docs/nl-nl/reference/engine/enums/ModelStreamingMode#Atomic) | | Het hele model streamt in één keer wanneer een van zijn onderdelen nodig is. | | Personages, voertuigen en andere discrete, dynamische objecten |
| [Persistent](/docs/nl-nl/reference/engine/enums/ModelStreamingMode#Persistent) | | Altijd gestreamd, en nooit gestreamd uit. | | Lobbies, menu's en herkenningspunten die altijd zichtbaar moeten zijn |
| [PersistentPerPlayer](/docs/nl-nl/reference/engine/enums/ModelStreamingMode#PersistentPerPlayer) | | Persistent voor spelers die je toevoegt met [Model:AddPersistentPlayer()](/docs/nl-nl/reference/engine/classes/Model#AddPersistentPlayer) , en atomair voor iedereen die niet is toegevoegd. | | Inhoud die slechts enkele spelers altijd nodig hebben |

Assets zoals texturen, meshes en audio streamen ook tijdens runtime. Afbeeldingen worden eerst op een lage resolutie geladen en verbeteren vervolgens op basis van het apparaat en hoe groot ze op het scherm verschijnen.

## [Gegevenspersistentie](#gegevenspersistentie)[](#gegevenspersistentie)

[DataStoreService](/docs/nl-nl/reference/engine/classes/DataStoreService)  slaat spelergegevens op tussen sessies. De API's zijn laag niveau, dus lees [Datastores](/docs/nl-nl/cloud-services/data-stores)  en [Spelergegevens en aankopen](/docs/nl-nl/cloud-services/data-stores/player-data-purchasing)  voordat je je opslagsysteem ontwerpt. Deze gidsen behandelen veelvoorkomende valkuilen zoals snelheidslimieten, sessievergrendeling en het veilig afhandelen van aankopen.

Datastores zijn beperkt tot het spel. Om testgegevens uit productie te houden, gebruik je een apart spel voor ontwikkeling. Voor details, zie [Omgevingen](/docs/nl-nl/projects/file-based-workflows#omgevingen) .

## [Veelvoorkomende taken oplossen](#veelvoorkomende-taken-oplossen)[](#veelvoorkomende-taken-oplossen)

### [Gedrag hergebruiken tussen instanties](#gedrag-hergebruiken-tussen-instanties)[](#gedrag-hergebruiken-tussen-instanties)

Omdat gekopieerde scripts onafhankelijke kopieën zijn, vermijd het om een kopie van hetzelfde script in elke instantie te plaatsen die het nodig heeft. Tag in plaats daarvan instanties met [CollectionService](/docs/nl-nl/reference/engine/classes/CollectionService)  en schrijf één script, ondersteund door een [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript) , dat gedrag aan elke getagde instantie hecht.

### [Gebruik een aangepast personage](#gebruik-een-aangepast-personage)[](#gebruik-een-aangepast-personage)

Personages kunnen het platformavatar, het platformrig met een aangepaste uitstraling, of een volledig aangepast rig gebruiken. Om het standaard spawn-systeem te behouden maar het personage te vervangen, plaats je een model genaamd StarterCharacter  in [StarterPlayer](/docs/nl-nl/reference/engine/classes/StarterPlayer) .

### [Overschrijf de standaard besturingsscripts](#overschrijf-de-standaard-besturingsscripts)[](#overschrijf-de-standaard-besturingsscripts)

Roblox voegt standaard camera- en besturingsscripts toe aan elke speler. Om ze te vervangen:

1.

Schakel [Workspace.PlayerScriptsUseInputActionSystem](/docs/nl-nl/reference/engine/classes/Workspace#PlayerScriptsUseInputActionSystem)  in, wat de standaard spelerscripts onder [StarterPlayer](/docs/nl-nl/reference/engine/classes/StarterPlayer)  verplaatst.

2.

Stel [StarterPlayer.CreateDefaultPlayerModule](/docs/nl-nl/reference/engine/classes/StarterPlayer#CreateDefaultPlayerModule)  in op false , zodat de standaard camera- en besturingsscripts niet worden toegevoegd.

3.

Voeg je eigen camera- en besturingsscripts toe.

### [Maak shader-achtige effecten](#maak-shader-achtige-effecten)[](#maak-shader-achtige-effecten)

Roblox ondersteunt geen aangepaste shaders. Gebruik in plaats daarvan:

-

[SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  of [MaterialVariant](/docs/nl-nl/reference/engine/classes/MaterialVariant)  voor [PBR-materialen](/docs/nl-nl/art/modeling/surface-appearance) .

-

[SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  of het [Neon](/docs/nl-nl/reference/engine/enums/Material#Neon)  materiaal voor emissieve oppervlakken.

-

Gebruik het [ForceField](/docs/nl-nl/reference/engine/enums/Material#ForceField)  materiaal voor intersectie-effecten.

-

Voor speciale gevallen, genereer dynamische texturen en geometrie met [EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage)  en [EditableMesh](/docs/nl-nl/reference/engine/classes/EditableMesh) .

## [Prestaties](#prestaties)[](#prestaties)

De prestaties op Roblox hangen voornamelijk af van de inhoud die je toevoegt en de tijd die je scripts elke frame nodig hebben. Test regelmatig op je doelhardware en stel vroeg budgetten in voor scènecomplexiteit (driehoeken, tekenopdrachten en dynamische lichten), fysica, replicatie en script tijd per frame. De meeste prestatieproblemen komen voort uit inhoud die verkeerd is geconfigureerd, en het laat oplossen ervan betekent vaak dat je assets opnieuw moet bewerken.

-

Automatische kwaliteit:  De meeste spelers gebruiken automatische grafische kwaliteit, die 10 niveaus heeft. Naarmate het niveau daalt om de framerates hoog te houden, verlaagt de engine de renderafstand, geometrische kwaliteit zoals detailniveau en SLIM, schaduwkwaliteit, verlichtingkwaliteit, schaduwen, deeltjesemissie en streamingradius. De tekenafstand daalt nooit onder de 500 studs, schaduwen worden uitgeschakeld onder niveau 4, en terreinwater en stralen zien er op elk niveau hetzelfde uit. Roblox past deze waarden continu aan, dus ontwerp niet rond exacte cijfers. Om een voorbeeld te bekijken, wijzig je Editor Quality Level  in de Studio-instellingen en test je op zowel de laagste als de hoogste niveaus. Voor details, zie [Grafische kwaliteitsniveaus](/docs/nl-nl/performance-optimization/design#grafische-kwaliteitsniveaus) .

-

Textuurstreaming:  Texturen streamen en schalen automatisch om aan geheugenbudgetten en schermgrootte te voldoen.

-

Occlusie-culling:  De engine slaat automatisch tekenopdrachten over voor onderdelen, meshes en terrein die achter andere objecten verborgen zijn. Het structureren van niveaus met muren en andere zichtblokkades stelt je in staat om de scènecomplexiteit te beheren. Eenvoudige verborgen blokonderdelen binnen muren maken occlusietests goedkoper dan vertrouwen op gedetailleerde meshes. Voor meer manieren om tekenopdrachten te verminderen, zie [Rendering](/docs/nl-nl/performance-optimization/improve#rendering) .

-

Scripting:  Luau is snel genoeg voor complexe, dynamische gameplaycode. Je hoeft geen garbage collection te vermijden of objecten te poolen, en het creëren van instanties tijdens runtime is snel.

-

Verlichting:  Scènes kunnen veel lichten gebruiken. Roblox schaalt de verlichtingkwaliteit automatisch op basis van het apparaat en valt terug op een goedkopere verlichtingsroute in complexe scènes.

Voor tools om problemen te meten en op te lossen, zie [Prestatieoptimalisatie](/docs/nl-nl/performance-optimization) .

## [Tools en AI](#tools-en-ai)[](#tools-en-ai)

-

Externe editors:  Gebruik VS Code of een andere editor met [Script Sync](/docs/nl-nl/scripting/sync)  of [Rojo](/docs/nl-nl/projects/rojo) . Voeg de Luau Language Server en de selene linter toe voor typecontrole en linting. Voor teamopstellingen, zie [Vergelijk bestand-gebaseerde workflows](/docs/nl-nl/projects/file-based-workflows) .

-

Studio MCP-server:  De meeste professionele ontwikkelaars willen hun eigen AI-tools en agent-harnassen gebruiken, zoals een coderingsagent in een terminal of editor. De [Studio MCP-server](/docs/nl-nl/studio/mcp)  verbindt die tools met Studio, zodat ze direct in je open sessie kunnen bouwen en testen.

-

Assistent:  [Assistent](/docs/nl-nl/assistant/guide)  is de ingebouwde AI-hulp van Studio voor het schrijven van code en bouwen, voor wanneer je AI-hulp wilt zonder je eigen tools op te zetten.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
