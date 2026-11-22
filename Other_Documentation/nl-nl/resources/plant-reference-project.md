<!-- Source: https://create.roblox.com/docs/nl-nl/resources/plant-reference-project -->

Plant referentieproject | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Voorbeelden en projecten](/docs/nl-nl/samples)

# Plant referentieproject

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

[Plant](https://www.roblox.com/games/14353060924/Plant)  is een referentiespel waarin spelers zaden planten en water geven, zodat ze later de resulterende planten kunnen oogsten en verkopen.

![Plant projectbanner](https://prod.docsiteassets.roblox.com/assets/resources/plant/Project-Banner.jpg)

Het project richt zich op veelvoorkomende gebruiksscenario's die je kunt tegenkomen bij het ontwikkelen van een spel op Roblox. Waar van toepassing, vind je opmerkingen over afwegingen, compromissen en de rationale van verschillende implementatiekeuzes, zodat je de beste beslissing kunt nemen voor je eigen spellen.

## [Verkrijg het bestand](#verkrijg-het-bestand)[](#verkrijg-het-bestand)

1.

Navigeer naar de [Plant](https://www.roblox.com/games/14353060924/Plant)  spelpagina.

2.

Klik op de ⋯  knop en Bewerken in Studio .

## [Gebruiksscenario's](#gebruiksscenarios)[](#gebruiksscenarios)

[Plant](https://www.roblox.com/games/14353060924/Plant)  behandelt de volgende gebruiksscenario's:

-

Sessiedata en persistentie van spelerdata

-

Beheer van UI-weergaven

-

Client-server netwerken

-

Eerste keer gebruikerservaring (FTUE)

-

Aankopen met harde en zachte valuta

Daarnaast lost dit project kleinere sets van problemen op die van toepassing zijn op veel spellen, waaronder:

-

Aanpassing van een gebied in de plaats dat is gekoppeld aan een speler

-

Beheer van de bewegingssnelheid van de speler

-

Het creëren van een object dat personages volgt

-

Detecteren in welk deel van de wereld een personage zich bevindt

Let op dat er verschillende gebruiksscenario's in dit spel zijn die te klein, te niche of niet interessant genoeg zijn om een oplossing voor een ontwerpprobleem te demonstreren; deze worden niet behandeld.

## [Projectstructuur](#projectstructuur)[](#projectstructuur)

De eerste beslissing bij het maken van een spel is het bepalen van de structuur van het [project](/docs/nl-nl/../projects) , wat voornamelijk inhoudt waar specifieke instanties in het [datamodel](/docs/nl-nl/projects/data-model)  moeten worden geplaatst en hoe de toegangspunten voor zowel client- als servercode moeten worden georganiseerd en gestructureerd.

### [Datamodel](#datamodel)[](#datamodel)

De volgende tabel beschrijft in welke containerservices in het datamodel instanties zijn geplaatst.

| Service | | Types van instanties |
| --- | --- |
| [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) | |

Bevat statische modellen die de 3D-wereld vertegenwoordigen, specifiek delen van de wereld die niet aan een speler toebehoren. Je hoeft deze instanties niet dynamisch te creëren, te wijzigen of te vernietigen tijdens runtime, dus het is acceptabel om ze hier te laten.

Er is ook een lege [Folder](/docs/nl-nl/reference/engine/classes/Folder) , waaraan de boerderijmodellen van spelers tijdens runtime zullen worden toegevoegd.

 |
| [Lighting](/docs/nl-nl/reference/engine/classes/Lighting) | |

Atmosferische en lichteffecten.

 |
| [ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst) | |

Bevat de kleinste mogelijke subset van instanties die nodig zijn om het laadscherm weer te geven en het spel te initialiseren. Hoe meer instanties er in [ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst)  worden geplaatst, hoe langer de wachttijd is voordat ze kunnen repliceren voordat de code in [ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst)  kan draaien.

-

In de Instanties  map bevindt zich de GUI voor het laadscherm.

-

In de Bron  map bevindt zich de code voor het laadscherm en de code die nodig is om te wachten tot de rest van het spel is geladen. De start  [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  is het toegangspunt voor alle client-side code in het project.

 |
| [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) | |

Fungeert als een opslagcontainer voor alle instanties waarvoor toegang vereist is op zowel de client als de server.

-

In de Afhankelijkheden  map bevinden zich enkele derde partij bibliotheken die door het project worden gebruikt.

-

In de Instanties  map bevindt zich een breed scala aan geprefabriceerde instanties.

-

In de Bron  map bevindt zich alle code die niet  vereist is voor het laadproces en die toegankelijk moet zijn vanuit zowel de client als de server.

 |
| [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService) | |

Bevat een [Script](/docs/nl-nl/reference/engine/classes/Script)  die fungeert als het toegangspunt voor alle server-side code in het project.

 |
| [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage) | |

Fungeert als een opslagcontainer voor alle instanties die niet naar de client hoeven te worden gerepliceerd.

-

In de Instanties  map bevindt zich een sjabloon Boerderij  model. Een kopie hiervan wordt in [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  geplaatst wanneer de speler het spel betreedt, waar het naar alle spelers zal worden gerepliceerd.

-

In de Bron  map bevindt zich alle code die exclusief is voor de server.

 |
| [SoundService](/docs/nl-nl/reference/engine/classes/SoundService) | |

Bevat de [Sound](/docs/nl-nl/reference/engine/classes/Sound)  objecten die worden gebruikt voor geluidseffecten in het spel. Onder [SoundService](/docs/nl-nl/reference/engine/classes/SoundService)  hebben deze [Sound](/docs/nl-nl/reference/engine/classes/Sound)  objecten geen positie en worden ze niet gesimuleerd in 3D-ruimte.

 |

### [Toegangspunten](#toegangspunten)[](#toegangspunten)

De meeste projecten organiseren code binnen herbruikbare [ModuleScripts](/docs/nl-nl/reference/engine/classes/ModuleScript)  die door de hele codebase kunnen worden geïmporteerd. [ModuleScripts](/docs/nl-nl/reference/engine/classes/ModuleScript)  zijn herbruikbaar, maar ze worden niet zelfstandig uitgevoerd; ze moeten worden geïmporteerd door een [Script](/docs/nl-nl/reference/engine/classes/Script)  of [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript) . Veel Roblox-projecten hebben een groot aantal [Script](/docs/nl-nl/reference/engine/classes/Script)  en [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  objecten, elk gerelateerd aan een gedrag of specifiek systeem in het spel, wat meerdere toegangspunten creëert.

Voor de [Plant](https://www.roblox.com/games/14353060924/Plant)  microgame is een andere aanpak geïmplementeerd via een enkele [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  die het toegangspunt is voor alle clientcode, en een enkele [Script](/docs/nl-nl/reference/engine/classes/Script)  die het toegangspunt is voor alle servercode. De juiste aanpak voor jouw project hangt af van je vereisten, maar een enkel toegangspunt biedt meer controle over de volgorde waarin systemen worden uitgevoerd.

De volgende lijsten beschrijven de afwegingen van beide benaderingen:

Enkel toegangspunt Meerdere toegangspunten

-

Een enkele [Script](/docs/nl-nl/reference/engine/classes/Script)  en een enkele [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  dekken respectievelijk server- en clientcode.

-

Grotere controle over de volgorde waarin verschillende systemen worden gestart omdat alle code vanuit een enkel script wordt geïnitialiseerd.

-

Kan objecten per referentie tussen systemen doorgeven.

### [Hoog niveau systeemarchitectuur](#hoog-niveau-systeemarchitectuur)[](#hoog-niveau-systeemarchitectuur)

De top-level systemen in het project worden hieronder gedetailleerd. Sommige van deze systemen zijn aanzienlijk complexer dan andere, en in veel gevallen is hun functionaliteit geabstraheerd over een hiërarchie van andere klassen.

 ![Plant project systemen architectuurdiagram](https://prod.docsiteassets.roblox.com/assets/resources/plant/Architecture-Systems.png)

Elk van deze systemen is een "singleton", in die zin dat het een niet-instantiëerbare klasse is die in plaats daarvan wordt geïnitialiseerd door het relevante client- of server start  script. Je kunt later in deze gids meer lezen over het [singleton patroon](#singletons) .

#### [Server](#server)[](#server)

De volgende systemen zijn gekoppeld aan de server.

| Systeem | | Beschrijving |
| Netwerk | |

-

Creëert alle [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  en [RemoteFunction](/docs/nl-nl/reference/engine/classes/RemoteFunction)  instanties.

-

Exposeert methoden voor het verzenden en luisteren naar berichten van de client.

-

Typevalidatie voor argumenten die tijdens runtime van de client worden ontvangen.

 |
| PlayerDataServer | |

-

Slaat persistente spelerdata op en laadt deze met behulp van [DataStoreService](/docs/nl-nl/reference/engine/classes/DataStoreService) .

-

Slaat spelerdata in het geheugen op en repliceert mutaties naar de client.

-

Exposeert signalen en methoden voor het abonneren op, opvragen en bijwerken van spelerdata.

 |
| Markt | |

-

Behandelt transacties met zachte valuta van de client.

-

Exposeert een methode om geoogste planten te verkopen.

 |
| CollisionGroupManager | |

-

Wijs speler karaktermodellen toe aan [botsingsgroepen](/docs/nl-nl/workspace/collisions#botsingsfiltering) .

-

Configureert botsingsgroepen zodat spelerkarakters niet kunnen botsen met plantenwagens.

 |
| FarmManagerServer | |

-

Hercreëert het boerderijmodel van een speler op basis van hun spelerdata wanneer ze het spel betreden.

-

Verwijdert het boerderijmodel wanneer een speler vertrekt.

-

Werkt de spelerdata bij wanneer de boerderij van een speler verandert.

-

Exposeert een methode om toegang te krijgen tot de Boerderij  klasse die is gekoppeld aan een bepaalde speler.

 |
| PlayerObjectsContainer | |

-

Creëert verschillende objecten die zijn gekoppeld aan de levensduur van een speler en biedt een methode om deze op te halen.

 |
| TagPlayers | |

-

Voegt [CollectionService](/docs/nl-nl/reference/engine/classes/CollectionService)  tags toe aan alle speler- en karakterobjecten.

 |
| FtueManagerServer | |

-

Voert tijdens de FTUE elke fase uit en wacht tot deze is voltooid.

 |
| CharacterSpawner | |

-

Respawnt karakters wanneer ze sterven. Let op dat [Players.CharacterAutoLoads](/docs/nl-nl/reference/engine/classes/Players#CharacterAutoLoads)  is uitgeschakeld zodat het spawnen wordt gepauzeerd totdat de gegevens van de speler zijn geladen.

 |

#### [Client](#client)[](#client)

De volgende systemen zijn gekoppeld aan de client.

| Systeem | | Beschrijving |
| Netwerk | |

-

Wacht tot de server alle [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  en [RemoteFunction](/docs/nl-nl/reference/engine/classes/RemoteFunction)  instanties heeft gemaakt.

-

Exposeert methoden voor het verzenden en luisteren naar berichten naar en van de server.

-

Handhaaft runtime parameter typevalidatie.

-

Voert [pcall()](/docs/nl-nl/reference/engine/globals/LuaGlobals#pcall)  uit op externe functies.

 |
| PlayerDataClient | |

-

Slaat de lokale spelerdata in het geheugen op.

-

Exposeert methoden en signalen voor het opvragen en abonneren op wijzigingen in spelerdata.

 |
| MarktClient | |

-

Exposeert een methode om de server te verzoeken een item voor zachte valuta aan te schaffen.

 |
| LocalWalkJumpManager | |

-

Exposeert methoden om de [WalkSpeed](/docs/nl-nl/reference/engine/classes/Humanoid#WalkSpeed)  of [JumpHeight](/docs/nl-nl/reference/engine/classes/Humanoid#JumpHeight)  van een karakter te wijzigen via vermenigvuldigers om conflicten te vermijden wanneer deze waarden vanuit meerdere plaatsen worden gewijzigd.

 |
| FarmManagerClient | |

-

Luistert naar specifieke [CollectionService](/docs/nl-nl/reference/engine/classes/CollectionService)  tags die op instanties worden toegepast en creëert "componenten" die gedrag aan deze instanties toevoegen. Een "component" verwijst naar een klasse die wordt gemaakt wanneer een [CollectionService](/docs/nl-nl/reference/engine/classes/CollectionService)  tag aan een instantie wordt toegevoegd en wordt vernietigd wanneer deze wordt verwijderd; deze worden gebruikt voor de CTA-prompts in de boerderij en verschillende klassen die de boerderijstatus aan de speler doorgeven.

 |
| UISetup | |

-

Initialiseert alle UI-lagen.

-

Configureert bepaalde lagen zodat ze alleen zichtbaar zijn in fysieke secties van de wereld.

-

Verbindt een speciaal camera-effect voor wanneer menu's zijn ingeschakeld.

 |
| FtueManagerClient | |

-

Configureert FTUE-fasen op de client.

 |
| CharacterSprint | |

-

Gebruikt LocalWalkJumpManager  om de [WalkSpeed](/docs/nl-nl/reference/engine/classes/Humanoid#WalkSpeed)  te verhogen wanneer een spelerkarakter buiten zijn boerderij is.

 |

Een opmerkelijke opmerking voor het singleton patroon is de Netwerk  [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  die logica bevat die zowel op de client als de server draait, geïnitialiseerd via aparte startServer()  en startClientAsync()  methoden. Dit is een patroon dat je over het algemeen zou moeten vermijden, omdat het server-side logica onnodig aan de client blootstelt en bestanden complexer kan maken dan nodig. In dit geval biedt echter een verenigde [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  setup een meer gestroomlijnde interface voor wat een hoog aangeraakt deel van de codebase is.

## [Client-server communicatie](#client-server-communicatie)[](#client-server-communicatie)

De meeste Roblox-spellen omvatten een element van communicatie tussen de client en de server. Dit kan inhouden dat de client de server vraagt om een bepaalde actie uit te voeren en de server updates naar de client repliceert.

In dit project wordt client-server communicatie zo generiek mogelijk gehouden door het gebruik van [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  en [RemoteFunction](/docs/nl-nl/reference/engine/classes/RemoteFunction)  objecten te beperken om de hoeveelheid speciale regels die moeten worden bijgehouden te verminderen. Dit project gebruikt de volgende methoden, in volgorde van voorkeur:

-

Replicatie via het [speler datasysteem](#replicatie-via-speler-datasysteem) .

-

Replicatie via [attributen](#replicatie-via-attributen) .

-

Replicatie via [tags](#replicatie-via-tags) .

-

Berichten [direct](#bericht-direct-via-netwerk-module)  via de Netwerk  module.

### [Replicatie via speler datasysteem](#replicatie-via-speler-datasysteem)[](#replicatie-via-speler-datasysteem)

Het speler datasysteem  stelt gegevens in staat om aan de speler te worden gekoppeld die tussen opslagsessies aanhoudt. Dit systeem biedt replicatie van client naar server en een set API's die kunnen worden gebruikt om gegevens op te vragen en zich te abonneren op wijzigingen, waardoor het ideaal is voor het repliceren van wijzigingen in de spelerstatus van de server naar de client.

Bijvoorbeeld, in plaats van een op maat gemaakte UpdateCoins  [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  te activeren om de client te vertellen hoeveel munten deze heeft, kun je het volgende aanroepen en de client laten abonneren via het PlayerDataClient.updated  evenement.

```

PlayerDataServer.setValue(player, "coins", 5)

```

Natuurlijk is dit alleen nuttig voor server-naar-client replicatie en voor waarden die je wilt behouden tussen sessies, maar dit geldt voor een verrassend aantal gevallen in het project, waaronder:

-

De huidige FTUE-fase

-

De inventaris van de speler

-

Het aantal munten dat de speler heeft

-

De status van de boerderij van de speler

### [Replicatie via attributen](#replicatie-via-attributen)[](#replicatie-via-attributen)

In situaties waarin de server een aangepaste waarde naar de client moet repliceren die specifiek is voor een gegeven [Instance](/docs/nl-nl/reference/engine/classes/Instance) , kun je gebruik maken van [attributen](/docs/nl-nl/studio/properties#instantie-attributen) . Roblox repliceert automatisch attribuutwaarden, zodat je geen codepaden hoeft te onderhouden om de status die aan een object is gekoppeld te repliceren. Een ander voordeel is dat deze replicatie samen met de instantie zelf plaatsvindt.

Dit is bijzonder nuttig voor instanties die tijdens runtime zijn gemaakt, aangezien attributen die op een nieuwe instantie zijn ingesteld voordat deze aan het datamodel wordt gekoppeld, atomisch met de instantie zelf worden gerepliceerd. Dit omzeilt de noodzaak om code te schrijven om te "wachten" op extra gegevens die via een [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  of [StringValue](/docs/nl-nl/reference/engine/classes/StringValue)  moeten worden gerepliceerd.

Je kunt ook direct attributen lezen vanuit het datamodel, zowel vanaf de client als de server, met de [GetAttribute()](/docs/nl-nl/reference/engine/classes/Instance#GetAttribute)  methode, en je kunt je abonneren op wijzigingen met de [GetAttributeChangedSignal()](/docs/nl-nl/reference/engine/classes/Instance#GetAttributeChangedSignal)  methode. In het [Plant](https://www.roblox.com/games/14353060924/Plant)  project wordt deze aanpak gebruikt voor, onder andere, het repliceren van de huidige status van planten naar clients.

### [Replicatie via tags](#replicatie-via-tags)[](#replicatie-via-tags)

[CollectionService](/docs/nl-nl/reference/engine/classes/CollectionService)  stelt je in staat om een stringtag toe te passen op een [Instance](/docs/nl-nl/reference/engine/classes/Instance) . Dit is nuttig voor het categoriseren van instanties en het repliceren van die categorisering naar de client.

Bijvoorbeeld, de CanPlant  tag wordt op de server toegepast om de client te signaleren dat een bepaalde pot een plant kan ontvangen.

### [Bericht direct via netwerkmodule](#bericht-direct-via-netwerkmodule)[](#bericht-direct-via-netwerkmodule)

Voor situaties waarin geen van de vorige opties van toepassing is, kun je aangepaste netwerkoproepen gebruiken via de Netwerk  module. Dit is de enige optie in het project die client-naar-server communicatie mogelijk maakt en is daarom het meest nuttig voor het verzenden van clientverzoeken en het ontvangen van een serverantwoord.

[Plant](https://www.roblox.com/games/14353060924/Plant)  gebruikt directe netwerkoproepen voor een verscheidenheid aan clientverzoeken, waaronder:

-

Water geven aan een plant

-

Een zaadje planten

-

Een item kopen

Het nadeel van deze aanpak is dat elk individueel bericht enige op maat gemaakte configuratie vereist, wat de complexiteit van het project kan verhogen, hoewel dit waar mogelijk is vermeden, vooral voor server-naar-client communicatie.

## [Klassen en singletons](#klassen-en-singletons)[](#klassen-en-singletons)

Klassen in het [Plant](https://www.roblox.com/games/14353060924/Plant)  project, net als instanties op Roblox, kunnen worden gemaakt en vernietigd. De syntaxis van de klasse is geïnspireerd op de idiomatische Lua-aanpak van [object-georiënteerd programmeren](https://www.lua.org/pil/16.1.html)  met een aantal wijzigingen om ondersteuning voor [strikte typechecking](#strikte-type-inferentie)  mogelijk te maken.

### [Instantiering](#instantiering)[](#instantiering)

Veel klassen in het project zijn gekoppeld aan een of meer [Instances](/docs/nl-nl/reference/engine/classes/Instance) . Objecten van een gegeven klasse worden gemaakt met behulp van een new()  methode, consistent met hoe instanties in Roblox worden gemaakt met [Instance.new()](/docs/nl-nl/reference/engine/datatypes/Instance#new) .

Dit patroon wordt over het algemeen gebruikt voor objecten waarvan de klasse een fysieke representatie in het datamodel heeft, en de klasse breidt zijn functionaliteit uit. Een goed voorbeeld is BeamBetween  dat een [Beam](/docs/nl-nl/reference/engine/classes/Beam)  object creëert tussen twee gegeven [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  objecten en die bevestigingen zo oriënteert dat de straal altijd omhoog wijst. Deze instanties kunnen worden gekloond van een geprefabriceerde versie in [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  of als argument aan new()  worden doorgegeven en binnen het object onder self  worden opgeslagen.

### [Bijbehorende instanties](#bijbehorende-instanties)[](#bijbehorende-instanties)

Zoals hierboven opgemerkt, hebben veel klassen in dit project een datamodelrepresentatie, een instantie die overeenkomt met de klasse en door deze wordt gemanipuleerd.

In plaats van deze instanties te creëren wanneer een klasse-object wordt geïnstantieerd, kiest de code er over het algemeen voor om [Clone()](/docs/nl-nl/reference/engine/classes/Instance#Clone)  een geprefabriceerde versie van de [Instance](/docs/nl-nl/reference/engine/classes/Instance)  die is opgeslagen onder [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  of [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage) . Hoewel het mogelijk zou zijn om de eigenschappen van deze instanties te serialiseren en ze vanaf nul in de new()  functies van de klasse te creëren, zou dit het bewerken van de objecten zeer omslachtig maken en ze moeilijker te begrijpen voor een lezer. Bovendien is het klonen van een instantie over het algemeen een snellere operatie dan het creëren van een nieuwe instantie en het aanpassen van de eigenschappen tijdens runtime.

### [Samenstelling](#samenstelling)[](#samenstelling)

Hoewel overerving mogelijk is in Luau met behulp van [metatables](/docs/nl-nl/luau/metatables) , kiest het project ervoor om klassen elkaar uit te laten breiden via samenstelling . Bij het combineren van klassen via samenstelling wordt het "kind" object geïnstantieerd in de new()  methode van de klasse en wordt het als lid onder self  opgenomen.

Voor een voorbeeld hiervan in actie, zie de CloseButton  klasse die de Button  klasse omhult.

### [Opruimen](#opruimen)[](#opruimen)

Net zoals een [Instance](/docs/nl-nl/reference/engine/classes/Instance)  kan worden vernietigd met de [Destroy()](/docs/nl-nl/reference/engine/classes/Instance#Destroy)  methode, kunnen klassen die kunnen worden geïnstantieerd ook worden vernietigd. De destructor-methode voor projectklassen is destroy()  met een kleine d  voor camelCase  consistentie in de methoden van de codebase, evenals om onderscheid te maken tussen de klassen van het project en Roblox-instanties.

De rol van de destroy()  methode is om alle instanties die door het object zijn gemaakt te vernietigen, alle verbindingen te ontkoppelen en destroy()  aan te roepen op alle kindobjecten. Dit is bijzonder belangrijk voor verbindingen omdat instanties met actieve verbindingen niet worden opgeruimd door de Luau garbage collector, zelfs als er geen verwijzingen naar de instantie of verbindingen met de instantie meer zijn.

### [Singletons](#singletons)[](#singletons)

Singletons, zoals de naam al aangeeft, zijn klassen waarvoor slechts één object ooit kan bestaan. Ze zijn het equivalent van de [Services](/docs/nl-nl/scripting/services)  van Roblox in het project. In plaats van een referentie naar het singleton-object op te slaan en deze rond te geven in de Luau-code, maakt [Plant](https://www.roblox.com/games/14353060924/Plant)  gebruik van het feit dat het vereisen van een [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  de geretourneerde waarde cachet. Dit betekent dat het vereisen van dezelfde singleton [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  vanuit verschillende plaatsen consistent hetzelfde geretourneerde object oplevert. De enige uitzondering op deze regel zou zijn als verschillende omgevingen (client of server) de [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  benaderen.

Singletons worden onderscheiden van instantiëerbare klassen door het feit dat ze geen new()  methode hebben. In plaats daarvan wordt het object samen met zijn methoden en status rechtstreeks geretourneerd via de [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript) . Aangezien singletons niet worden geïnstantieerd, wordt de self  syntaxis niet gebruikt en worden methoden in plaats daarvan met een punt (. ) in plaats van een dubbele punt (: ) aangeroepen.

## [Strikte type-inferentie](#strikte-type-inferentie)[](#strikte-type-inferentie)

[Luau](/docs/nl-nl/../luau)  ondersteunt geleidelijke typing, wat betekent dat je vrij bent om optionele type-definities aan sommige of al je code toe te voegen. In dit project wordt strikte  typechecking gebruikt voor elk script. Dit is de minst permissieve optie voor Roblox's [Script Analysis](/docs/nl-nl/studio/script-editor#scriptanalyse)  tool en dus het meest waarschijnlijk om typefouten voor runtime te vangen.

Sterke typing is ongetwijfeld krachtig, maar het is nog steeds een evoluerende functie in de Luau-taal en Studio. Als gevolg hiervan zijn er een aantal beperkingen die, op het moment van schrijven, workaround vereisten die in de volgende secties worden gedetailleerd.

### [Getypte klassen syntaxis](#getypte-klassen-syntaxis)[](#getypte-klassen-syntaxis)

De gevestigde aanpak voor het creëren van klassen in Lua is [goed gedocumenteerd](https://www.lua.org/pil/16.1.html) , echter is het niet goed geschikt voor sterke Luau-typing. In Luau is de eenvoudigste manier om het type van een klasse te krijgen de [typeof()](/docs/nl-nl/reference/engine/globals/RobloxGlobals#typeof)  methode:

```

type ClassType = typeof(Class.new())

```

Dit werkt, maar het is niet erg nuttig wanneer je klasse wordt geïnitialiseerd met waarden die alleen tijdens runtime bestaan, bijvoorbeeld [Player](/docs/nl-nl/reference/engine/classes/Player)  objecten. Bovendien is de aanname die wordt gedaan in idiomatische Lua klasse syntaxis dat het declareren van een methode op een klasse self  altijd een instantie van die klasse zal zijn; dit is niet een aanname die de type-inferentie-engine kan maken.

Om strikte type-inferentie te ondersteunen, gebruikt het [Plant](https://www.roblox.com/games/14353060924/Plant)  project een oplossing die op verschillende manieren verschilt van idiomatische Lua klasse syntaxis, waarvan sommige misschien niet intuïtief aanvoelen:

-

De definitie van self  is gedupliceerd, zowel in de type-declaratie als in de constructor. Dit introduceert een onderhoudsbelasting, maar waarschuwingen worden gemarkeerd als de twee definities uit sync raken met elkaar.

-

Klassenmethoden worden gedeclareerd met een punt, zodat self  expliciet kan worden gedeclareerd als type ClassType . Methoden kunnen nog steeds met een dubbele punt worden aangeroepen zoals verwacht.

```

--!strict

local MyClass = {}

MyClass.__index = MyClass

export type ClassType = typeof(setmetatable(

	{} :: {

		property: number,

	},

	MyClass

))

function MyClass.new(property: number): ClassType

	local self = {

		property = property,

	}

	setmetatable(self, MyClass)

	return self

end

function MyClass.addOne(self: ClassType)

	self.property += 1

end

return MyClass

```

### [Typecast types na logische guards](#typecast-types-na-logische-guards)[](#typecast-types-na-logische-guards)

Op het moment van schrijven is het type van een waarde niet verlaagd na een guard-voorwaardelijke verklaring. Bijvoorbeeld, na de guard hieronder, is het type van optionalParameter  niet verlaagd naar number .

```

--!strict

local function foo(optionalParameter: number?)

	if not optionalParameter then

		return

	end

	print(optionalParameter + 1)

end

```

Om dit te mitigeren, worden nieuwe variabelen gemaakt na deze guards met hun type expliciet gecast.

```

--!strict

local function foo(optionalParameter: number?)

	if not optionalParameter then

		return

	end

	local parameter = optionalParameter :: number

	print(parameter + 1)

end

```

### [Traverseer DataModel hiërarchieën](#traverseer-datamodel-hiërarchieën)[](#traverseer-datamodel-hiërarchieën)

In sommige gevallen moet de codebase de datamodelhiërarchie van een boom van objecten die tijdens runtime zijn gemaakt, doorlopen. Dit vormt een interessante uitdaging voor typechecking. Op het moment van schrijven is het niet mogelijk om een generieke datamodelhiërarchie als type te definiëren. Als gevolg hiervan zijn er gevallen waarin de enige type-informatie die beschikbaar is voor een datamodelstructuur het type van de bovenste instantie is.

Een benadering van deze uitdaging is om naar any  te casten en vervolgens te verfijnen. Bijvoorbeeld:

```

local function enableVendor(vendor: Model)

	local zonePart: BasePart = (vendor :: any).ZonePart

end

```

Het probleem met deze aanpak is dat het de leesbaarheid beïnvloedt. In plaats daarvan gebruikt het project een gener modulaire module genaamd getInstance  voor het doorlopen van datamodelhiërarchieën die intern naar any  cast.

```

local function enableVendor(vendor: Model)

	local zonePart: BasePart = getInstance(vendor, "ZonePart")

end

```

Naarmate de type-engine's begrip van het datamodel evolueert, is het mogelijk dat patronen zoals deze niet langer nodig zullen zijn.

## [Gebruikersinterface](#gebruikersinterface)[](#gebruikersinterface)

[Plant](https://www.roblox.com/games/14353060924/Plant)  bevat een verscheidenheid aan complexe en eenvoudige 2D-gebruikersinterfaces. Deze omvatten niet-interactieve heads-up display (HUD) items zoals de munten teller en complexe interactieve menu's zoals de winkel.

### [UI-aanpak](#ui-aanpak)[](#ui-aanpak)

Je kunt Roblox [UI](/docs/nl-nl/../ui)  losjes vergelijken met de HTML DOM, omdat het een hiërarchie van objecten is die beschrijft wat de gebruiker zou moeten zien. Benaderingen voor het creëren en bijwerken van een Roblox UI zijn grofweg verdeeld in imperatieve  en declaratieve  praktijken.

| Benadering | | Voordelen en nadelen |
| Imperatief | |

In de imperatieve benadering wordt UI behandeld als elke andere instantiehiërarchie op Roblox. De UI-structuur wordt vóór runtime in Studio gemaakt en aan het datamodel toegevoegd, meestal direct in [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui) . Vervolgens manipuleert de code tijdens runtime specifieke delen van de UI om de status weer te geven die de maker vereist.

Deze benadering heeft enkele voordelen. Je kunt de UI vanaf nul in Studio maken en deze in het datamodel opslaan. Dit is een eenvoudige en visuele bewerkingservaring die de creatie van UI kan versnellen. Omdat imperatieve UI-code zich alleen bezighoudt met wat moet worden gewijzigd, maakt het ook eenvoudige UI-wijzigingen gemakkelijk te implementeren.

Een opmerkelijk nadeel is dat, aangezien imperatieve UI-benaderingen vereisen dat de status handmatig wordt geïmplementeerd in de vorm van transformaties, complexe representaties van status erg moeilijk te vinden en te debuggen kunnen worden. Het is gebruikelijk dat er fouten optreden bij het ontwikkelen van imperatieve UI-code, vooral wanneer de status en de UI desynchroniseren door meerdere updates die op een onverwachte volgorde interageren.

Een andere uitdaging met imperatieve benaderingen is dat het moeilijker is om UI op te splitsen in betekenisvolle componenten die eenmaal kunnen worden gedeclareerd en hergebruikt. Omdat de hele UI-boom op bewerkingstijd wordt gedeclareerd, kunnen veelvoorkomende patronen in meerdere delen van het datamodel worden herhaald.

 |
| Declaratief | |

In de declaratieve benadering worden de gewenste status van UI-instanties expliciet gedeclareerd, en de efficiënte implementatie van deze status wordt geabstraheerd door bibliotheken zoals [Roact](https://github.com/Roblox/roact/)  of [Fusion](https://github.com/Elttob/Fusion) .

Het voordeel van deze benadering is dat de implementatie van status triviaal wordt en je alleen hoeft te beschrijven hoe je wilt dat je UI eruitziet. Dit maakt het identificeren en oplossen van bugs aanzienlijk gemakkelijker.

Het belangrijkste nadeel is dat je de hele UI-boom in code moet declareren. Bibliotheken zoals Roact en Fusion hebben syntaxis om dit gemakkelijker te maken, maar het blijft een tijdrovend proces en een minder intuïtieve bewerkingservaring bij het samenstellen van UI.

 |

[Plant](https://www.roblox.com/games/14353060924/Plant)  gebruikt een imperatieve  benadering onder de veronderstelling dat het direct tonen van de transformaties een effectievere overzicht geeft van hoe UI wordt gemaakt en gemanipuleerd op Roblox. Dit zou niet mogelijk zijn met een declaratieve benadering. Sommige herhaalde UI-structuren en logica zijn ook geabstraheerd in herbruikbare [componenten](#laag-en-componenten)  om een veelvoorkomende valkuil in imperatief UI-ontwerp te vermijden.

### [Hoog-niveau architectuur](#hoog-niveau-architectuur)[](#hoog-niveau-architectuur)

 ![Plant project UI architectuurdiagram](https://prod.docsiteassets.roblox.com/assets/resources/plant/Architecture-UI.png)

### [Laag en componenten](#laag-en-componenten)[](#laag-en-componenten)

In [Plant](https://www.roblox.com/games/14353060924/Plant)  zijn alle UI-structuren ofwel een Layer  of een Component .

-

Layer  wordt gedefinieerd als een top-level groepering singleton die geprefabriceerde UI-structuren in [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  omhult. Een laag kan een aantal componenten bevatten, of het kan zijn eigen logica volledig encapsuleren. Voorbeelden van lagen zijn het inventaris menu of de indicator van het aantal munten in de heads-up display.

-

Component  is een herbruikbaar UI-element. Wanneer een nieuw componentobject wordt geïnstantieerd, kloont het een geprefabriceerd sjabloon uit [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) . Componenten kunnen op hun beurt ook andere componenten bevatten. Voorbeelden van componenten zijn een generieke knopklasse of het concept van een lijst met items.

### [Weergavebeheer](#weergavebeheer)[](#weergavebeheer)

Een veelvoorkomend probleem bij het beheren van UI is weergavebeheer. Dit project heeft een reeks menu's en HUD-items, waarvan sommige luisteren naar gebruikersinvoer, en zorgvuldig beheer van wanneer ze zichtbaar of ingeschakeld zijn, is vereist.

[Plant](https://www.roblox.com/games/14353060924/Plant)  benadert dit probleem met zijn UIHandler  systeem dat beheert wanneer een UI-laag zichtbaar of niet zichtbaar moet zijn. Alle UI-lagen in het spel worden gecategoriseerd als HUD  of Menu  en hun zichtbaarheid wordt beheerd door de volgende regels:

-

De ingeschakelde status van Menu  en HUD  lagen kan worden omgeschakeld.

-

Ingeschakelde HUD  lagen worden alleen weergegeven als er geen Menu  lagen zijn ingeschakeld.

-

Ingeschakelde Menu  lagen worden opgeslagen in een stapel, en slechts één Menu  laag is tegelijkertijd zichtbaar. Wanneer een Menu  laag is ingeschakeld, wordt deze aan de voorkant van de stapel ingevoegd en weergegeven. Wanneer een Menu  laag is uitgeschakeld, wordt deze uit de stapel verwijderd en wordt de volgende ingeschakelde Menu  laag in de wachtrij weergegeven.

Deze aanpak is intuïtief omdat het mogelijk maakt om menu's met geschiedenis te navigeren. Als een menu wordt geopend vanuit een ander menu, zal het sluiten van het nieuwe menu het oude menu weer tonen.

UI-laag singletons registreren zichzelf bij de UIHandler  en krijgen een signaal dat afgaat wanneer hun zichtbaarheid moet veranderen.

## [Verdere lezing](#verdere-lezing)[](#verdere-lezing)

Vanuit dit grondige overzicht van het [Plant](https://www.roblox.com/games/14353060924/Plant)  project, wil je misschien de volgende gidsen verkennen die dieper ingaan op gerelateerde concepten en onderwerpen.

-

[Client-Server Model](/docs/nl-nl/projects/client-server)  — Een overzicht van het client-server model in Roblox.

-

[Luau](/docs/nl-nl/../luau)  — Details over Luau , de door Roblox gemaakte scripttaal afgeleid van [Lua 5.1](https://www.lua.org/pil/5.1.html) .

-

[Remote Events en Callbacks](/docs/nl-nl/scripting/events/remote)  — Alles over externe netwerk evenementen en callbacks voor communicatie over de client-server grens.

-

[UI](/docs/nl-nl/../ui)  — Details over gebruikersinterface-objecten en ontwerp op Roblox.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
