<!-- Source: https://create.roblox.com/docs/nl-nl/projects/data-model -->

Gegevensmodel | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Projecten](/docs/nl-nl/projects)
6. /
7. [Architectuur](/docs/nl-nl/projects/data-model)

# Gegevensmodel

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Elke plaats wordt vertegenwoordigd door een gegevensmodel, een hiërarchie van objecten die alles over de plaats beschrijven. Het gegevensmodel bevat alle objecten die de 3D-wereld vormen, zoals onderdelen, terrein, verlichting en andere omgevingselementen. Het bevat ook objecten die het runtime-gedrag kunnen controleren, zoals scripts die eigenschappen wijzigen, methoden en functies aanroepen, en reageren op gebeurtenissen die dynamisch gedrag en interactiviteit mogelijk maken.

De Roblox-engine gebruikt het gegevensmodel als de bron van waarheid voor de status van een plaats, zodat het deze kan simuleren en weergeven op clientapparaten. Voor meer informatie over hoe de Roblox-engine het gegevensmodel interpreteert, zie [Client-Server Runtime](/docs/nl-nl/projects/client-server) .

## [Objecten](#objecten)[](#objecten)

Je plaatst en organiseert objecten in het gegevensmodel om een plaats in Roblox te beschrijven. Elk object in Roblox erft van de [Instance](/docs/nl-nl/reference/engine/classes/Instance) -klasse, die generieke eigenschappen, methoden en gebeurtenissen definieert die gemeenschappelijk zijn voor alle objecten. Objecten definiëren ook hun eigen kenmerken, afhankelijk van de functionaliteit die het object biedt. Er zijn veel categorieën van objecten met een breed scala aan toepassingen, maar je zult vaak werken met [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  en [LuaSourceContainer](/docs/nl-nl/reference/engine/classes/LuaSourceContainer)  objecten, die vaak onderdelen en scripts worden genoemd.

Voor een uitgebreide lijst van alle functies van de Roblox-engine, zie de [referentiedocumentatie](/docs/nl-nl/reference/engine) .

### [3D-bouwblokken](#3d-bouwblokken)[](#3d-bouwblokken)

[BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  is de kernklasse voor fysiek gesimuleerde 3D-bouwblokken in de wereld. Het definieert de eigenschappen en methoden die gemeenschappelijk zijn voor alle fysieke objecten met eigenschappen zoals positie, grootte en oriëntatie.

| Object | | Beschrijving |
| --- | --- |
| [Part](/docs/nl-nl/reference/engine/classes/Part) | | Een primitief [onderdeel](/docs/nl-nl/parts)  dat de vorm kan aannemen van een blok, bal, cilinder, wig of hoekwig. |
| [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) | | Een geïmporteerd [mesh](/docs/nl-nl/parts/meshes)  uit 3D-modelleringssoftware zoals Maya of Blender. |
| [TrussPart](/docs/nl-nl/reference/engine/classes/TrussPart) | | Een truss-balk waar karakters op kunnen klimmen als een ladder. |

Hoewel je theoretisch een volledig functionele Roblox-game kunt maken met alleen eenvoudige onderdelen, zul je waarschijnlijk [meshes](/docs/nl-nl/parts/meshes)  importeren en primitieve onderdelen combineren tot complexere objecten en structuren via [solide modellering](/docs/nl-nl/parts/solid-modeling) .

### [Scripts](#scripts)[](#scripts)

Je kunt interactiviteit en gedrag aan de 3D-wereld van je plaats toevoegen en logica definiëren met scripts. Je schrijft scripts in de Luau-programmeertaal om dingen te doen zoals onderdelen verplaatsen, andere scripts aanroepen en reageren op gebeurtenissen. Omdat Roblox werkt in een client-servermodel, kun je scripts op de server, client uitvoeren of ze laten communiceren over de netwerkgrens.

-

Een [Script](/docs/nl-nl/reference/engine/classes/Script)  object vertegenwoordigt een script dat alleen op de server kan draaien.

-

Een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  object vertegenwoordigt een script dat alleen op de client kan draaien.

-

Een [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  object vertegenwoordigt een herbruikbaar script dat je kunt [require()](/docs/nl-nl/reference/engine/globals/LuaGlobals#require)  vanuit zowel server- als clientscripts.

Om ervoor te zorgen dat scripts correct functioneren, moet je ze in de juiste containers in het gegevensmodel plaatsen. Voor meer informatie, zie de secties [Server](#server)  en [Client](#client) .

## [Objectorganisatie](#objectorganisatie)[](#objectorganisatie)

Hoewel je veel flexibiliteit hebt in hoe je je gegevensmodel organiseert, verwacht de Roblox-engine dat bepaalde objecten in bepaalde containerservices  worden geplaatst, wat objecten zijn die specifieke gedragingen hebben en de gedragingen van de objecten die ze bevatten kunnen beïnvloeden. De belangrijkste categorieën van containerservices zijn:

-

Workspace  — [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  slaat alle objecten op die in de 3D-wereld worden weergegeven.

-

Environment  — Containers zoals [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  en [SoundService](/docs/nl-nl/reference/engine/classes/SoundService)  die objecten bevatten voor omgevingsinstellingen en -elementen.

-

Replication  — Containers voor inhoud en logica die tussen de server en client worden gerepliceerd, zoals [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  en [ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst) .

-

Server  — Containers voor alleen serverzijde inhoud en logica, zoals [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService)  en [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage) .

-

Client  — Containers voor clientzijde inhoud en logica, zoals [StarterPlayer](/docs/nl-nl/reference/engine/classes/StarterPlayer)  en [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui) .

-

Chat  — Containers voor objecten die chatfuncties mogelijk maken, zoals [VoiceChatService](/docs/nl-nl/reference/engine/classes/VoiceChatService)  en [TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService) .

De Roblox-engine heeft veel meer services die ingebouwde functionaliteit bieden die je binnen je scripts kunt aanroepen. De Roblox-engine geeft deze services geen speciale behandeling in het gegevensmodel. Voor meer informatie, zie [services](/docs/nl-nl/scripting/services) .

Daarnaast kun je je objecten verder organiseren met de volgende objecten:

-

Mappen  — Een [Folder](/docs/nl-nl/reference/engine/classes/Folder)  is voor organisatorische doeleinden en definieert geen gedrag. Je kunt bijvoorbeeld mappen gebruiken om vergelijkbare objecten te groeperen, zoals een set scripts in serveropslag.

-

Modellen  — Een [Model](/docs/nl-nl/reference/engine/classes/Model)  is voornamelijk bedoeld voor geometrische groeperingen van onderdelen, zoals het groeperen van een bureau-set die een stoel, tafel en een lamp omvat. Om complexere sets te organiseren, kun je zelfs modellen binnen modellen nestelen.

### [Workspace](#workspace)[](#workspace)

[Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  bevat alle objecten die de 3D-wereld van een plaats vormen. Je kunt objecten aan de workspace toevoegen om je 3D-wereld aan te passen, zoals basisonderdelen, mesh-onderdelen en modellen. Clients renderen alles wat in deze container verschijnt en niets daarbuiten, zodat je kunt controleren wat gebruikers zien en mee kunnen interageren in je plaats. Hoewel ze niet daadwerkelijk worden weergegeven, kun je ook scripts toevoegen die zijn gekoppeld aan de onderdelen en modellen waarmee ze zijn geassocieerd. Standaard is de workspace vooraf gevuld met een [Terrain](/docs/nl-nl/reference/engine/classes/Terrain)  en [Camera](/docs/nl-nl/reference/engine/classes/Camera)  object.

#### Camera

[Camera](/docs/nl-nl/reference/engine/classes/Camera)  bepaalt hoe de client de 3D-wereld bekijkt. Standaard is er één camera in de workspace, maar je kunt meerdere camera-objecten toevoegen om verschillende perspectieven en weergaven te creëren. Elke client neemt deze instellingen en creëert zijn eigen camerabeeld dat de server niet direct kan wijzigen.

Bijvoorbeeld, je kunt een camera instellen om de bewegingen van de gebruiker te volgen of vast te blijven op een bepaalde locatie. Je kunt ook de kijkhoek, afstand en hoek aanpassen om verschillende visuele effecten te creëren van hoe gebruikers je 3D-wereld bekijken.

Voor meer informatie, zie [de camera aanpassen](/docs/nl-nl/workspace/camera) .

#### Terrain

[Terrain](/docs/nl-nl/reference/engine/classes/Terrain)  stelt je in staat om landschappen voor je plaats te creëren. Je kunt een materiaal op het terrein toepassen om gewenste natuurlijke omgevingen te simuleren, zoals gras, water, zand of een aangepast materiaal. Hoewel je slechts één terreinobject voor je 3D-wereld kunt hebben en één materiaal op dat terrein kunt toepassen, kun je de [Terrain Editor](/docs/nl-nl/studio/terrain-editor)  gebruiken om regio's van je terrein te bewerken.

Voor meer informatie, zie [milieu-terrein](/docs/nl-nl/parts/terrain) .

### [Environment](#environment)[](#environment)

Aangepaste verlichting kan je 3D-wereld veel meeslepender en realistischer maken. De [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  service bevat objecten die de globale verlichtingsinstellingen van je plaats regelen, zoals [Atmosphere](/docs/nl-nl/reference/engine/classes/Atmosphere)  voor het simuleren van atmosferische effecten of [Sky](/docs/nl-nl/reference/engine/classes/Sky)  om de zon, maan en sterren in je omgevingen te veranderen. Daarnaast kun je [lichtbronnen](/docs/nl-nl/effects/light-sources)  gebruiken om licht van specifieke objecten uit te stralen.

Het toevoegen van [audio](/docs/nl-nl/audio)  aan je games is ook cruciaal om je games naar nieuwe hoogten te tillen. Door strategisch gebruik te maken van positionele en niet-positionele audio, kun je spelers onderdompelen in je werelden, hen nuttige feedback geven voor hun acties en hun aandacht richten op wat ze moeten doen om succesvol te zijn in hun doelstellingen.

### [Replication](#replication)[](#replication)

Replicatie  is het proces waarbij de server de status van je plaats synchroniseert met alle verbonden clients. De Roblox-engine repliceert intelligent en automatisch gegevens, fysica en chatberichten tussen de server en client in veel gevallen, maar je kunt ook bepaalde objecten specificeren om te repliceren door ze in specifieke containers te plaatsen.

#### ReplicatedFirst

[ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst)  bevat objecten die je wilt repliceren naar een client wanneer deze je plaats binnenkomt. Het bevat doorgaans objecten die essentieel zijn om een speler te initialiseren, zoals client-side [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  objecten en de objecten die aan de scripts zijn gekoppeld. Alle inhoud in deze container wordt slechts één keer van de server naar de client gerepliceerd.

#### ReplicatedStorage

[ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  bevat objecten die beschikbaar zijn voor zowel de server als verbonden clients. Wijzigingen die op de client plaatsvinden, blijven bestaan, maar worden niet naar de server gerepliceerd. De server kan wijzigingen op de client overschrijven om consistentie te behouden. Deze container wordt doorgaans gebruikt voor [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  objecten die moeten worden gedeeld en toegankelijk zijn voor zowel [Script](/docs/nl-nl/reference/engine/classes/Script)  (serverzijde) als [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  (clientzijde) objecten. Daarnaast kun je deze container gebruiken om objecten te repliceren die niet in de 3D-wereld hoeven te bestaan totdat ze nodig zijn, zoals een [ParticleEmitter](/docs/nl-nl/reference/engine/classes/ParticleEmitter)  voor klonen en koppelen aan alle binnenkomende karaktermodellen.

Voor meer informatie over hoe replicatie werkt, zie [client-server runtime](/docs/nl-nl/projects/client-server) .

### [Server](#server)[](#server)

Het gegevensmodel definieert speciale containers voor serverzijde alleen objecten die nooit naar de client worden gerepliceerd. Dit stelt de server in staat om het gedrag en de status van de client te beïnvloeden zonder de objecten en logica van de server aan de client bloot te stellen.

Je kunt externe evenementen en functies gebruiken om client-side communicatie met de server mogelijk te maken.

#### ServerScriptService

[ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService)  bevat [Script](/docs/nl-nl/reference/engine/classes/Script)  objecten, [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  objecten die door serverscripts worden vereist, en andere scripting-gerelateerde objecten die alleen voor servergebruik zijn bedoeld. Als je scripts andere, niet-scriptingobjecten vereisen, moet je ze in [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage)  plaatsen. Scripts in deze container worden nooit naar clients gerepliceerd, wat je in staat stelt om veilige, server-side logica te hebben.

#### ServerStorage

[ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage)  bevat objecten die alleen voor servergebruik zijn bedoeld. Je kunt deze container gebruiken om objecten op te slaan die je wilt klonen en koppelen aan de workspace of andere containers tijdens runtime. Je kunt bijvoorbeeld grote objecten zoals kaarten in deze container opslaan totdat ze nodig zijn en ze alleen naar de workspace verplaatsen wanneer dat vereist is. Dit stelt je in staat om het netwerkverkeer van de client bij de eerste verbinding te verminderen.

Scripts worden niet uitgevoerd wanneer ze aan deze container zijn gekoppeld, maar scripts binnen [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService)  kunnen toegang krijgen tot en [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  objecten in deze container uitvoeren.

### [Client](#client)[](#client)

De clientcontainerservices zijn bedoeld voor objecten die naar elke verbonden client worden gerepliceerd. Deze categorie containers repliceert naar elke verbonden client en bevat doorgaans 3D-objecten en bijbehorende [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  objecten. Alle objecten die je in deze containers opslaat, zijn niet persistent tussen sessies en worden elke keer gereset wanneer een client opnieuw verbindt. Je kunt objecten in deze containers plaatsen, zoals speler-GUI's, client-side scripts en andere objecten die alleen relevant zijn voor de client.

Wanneer een client verbinding maakt met een server, luistert de [Players](/docs/nl-nl/reference/engine/classes/Players)  containerservice naar gebruikers die je plaats binnenkomen en maakt een [Player](/docs/nl-nl/reference/engine/classes/Player)  object voor elke client. De server kopieert de objecten van de clientcontainers in het bewerkingsgegevensmodel naar de overeenkomstige locatie in het runtime-gegevensmodel binnen het [Players](/docs/nl-nl/reference/engine/classes/Players)  object. De volgende tabel beschrijft de oorspronkelijke container waarin het zich bevindt in de container en de resulterende container waar ze naar de client worden gekopieerd:

| Bewerk gegevensmodel | | Runtime gegevensmodel | | Opmerkingen |
| [StarterPack](/docs/nl-nl/reference/engine/classes/StarterPack) | | Player.Backpack | | Scripts die de inventaris van de speler instellen en doorgaans [Tool](/docs/nl-nl/reference/engine/classes/Tool)  objecten bevatten, maar vaak ook lokale scripts. |
| [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui) | | Player.PlayerGui | | Scripts die de lokale GUI van de speler kunnen beheren. Wanneer een speler opnieuw verschijnt, worden de inhoud van PlayerGui leeggemaakt. De server kopieert de objecten binnen StarterGui naar de PlayerGui. |
| [StarterPlayerScripts](/docs/nl-nl/reference/engine/classes/StarterPlayerScripts) | | Player.PlayerScripts | | Algemene scripts voor de client. Als je bijvoorbeeld speciale effecten op de client wilt creëren wanneer aan bepaalde voorwaarden wordt voldaan, kun je een lokaal script in deze container plaatsen om dat te doen. De server kan deze container niet openen. |
| [StarterCharacterScripts](/docs/nl-nl/reference/engine/classes/StarterCharacterScripts) | | Player.Character | | Scripts die naar de client worden gekopieerd wanneer ze verschijnen. Deze scripts blijven niet bestaan wanneer de speler opnieuw verschijnt. |
| [ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst) | |  | | De inhoud van deze container wordt als eerste naar alle clients gerepliceerd (maar niet terug naar de server), voordat iets anders gebeurt. |

Voor meer informatie over bewerkings- en runtime-gegevensmodellen, zie [client-server runtime](/docs/nl-nl/projects/client-server#client) .

Je voegt [Player](/docs/nl-nl/reference/engine/classes/Player)  objecten niet expliciet toe aan de [Players](/docs/nl-nl/reference/engine/classes/Players)  containerservice.

### [Chat](#chat)[](#chat)

#### TextChatService

[TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService)  vertegenwoordigt de service die verschillende, in-game tekstchat-taken beheert, zoals het beheren van kanalen, het decoreren van berichten, het filteren van tekst, het creëren van commando's en het ontwikkelen van aangepaste chatinterfaces.

Voor meer informatie, zie [overzicht van tekstchat](/docs/nl-nl/chat/in-experience-text-chat) .

#### VoiceChatService

[VoiceChatService](/docs/nl-nl/reference/engine/classes/VoiceChatService)  vertegenwoordigt de op nabijheid gebaseerde spraakchatfunctie die realistische communicatie simuleert op basis van hoe dicht je bij andere gebruikers bent. Je kunt deze service gebruiken om de functie in en uit te schakelen.

Voor meer informatie, zie [spraakchat](/docs/nl-nl/chat/voice-chat) .

## [Mappen en modellen](#mappen-en-modellen)[](#mappen-en-modellen)

Er zijn twee primaire methoden voor het groeperen van objecten in het gegevensmodel: mappen  en modellen . Beide zijn containers voor objecten, maar ze hebben verschillende doeleinden.

-

Mappen  zijn het beste voor het opslaan van secties van een omgeving, zoals de lobby of een gevechtsarena.

-

Modellen  worden gebruikt voor sets van objecten, zoals een bureau-set die een stoel, tafel en een lamp omvat. Om complexere sets te organiseren, nest je modellen binnen modellen.

Je moet altijd je objecten beschrijvend benoemen. Dit maakt het gemakkelijk om objecten later te vinden en te wijzigen indien nodig.

![Het Explorer-venster met een demonstratie van een maporganisatie structuur.](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Example-Organized-Folders-In-Workspace.png) Objecten georganiseerd in [Mappen](/docs/nl-nl/reference/engine/classes/Folder)

![Het Explorer-venster met een demonstratie van een modelorganisatie structuur in verschillende services.](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Example-Maps-In-Workspace-ServerStorage.png) Verschillende "kaart" modellen om te wisselen tussen [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  en [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
