<!-- Source: https://create.roblox.com/docs/nl-nl/workspace/streaming -->

Instantie streaming | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Projecten](/docs/nl-nl/projects)
6. /
7. [Architectuur](/docs/nl-nl/projects/data-model)
8. /
9. [Instantiestreaming](/docs/nl-nl/workspace/streaming)

# Instantie streaming

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

In-game instantie streaming  stelt de Roblox-engine in staat om dynamisch 3D-inhoud en gerelateerde instanties in de [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  in en uit te laden. Dit kan de algehele spelerservaring op verschillende manieren verbeteren, waaronder:

-

Snellere toetredingstijden

 — Spelers kunnen beginnen met spelen in een deel van de wereld terwijl meer van de wereld op de achtergrond wordt geladen.

-

Geheugen efficiëntie

 — Spellen kunnen worden gespeeld op apparaten met minder geheugen, aangezien inhoud dynamisch in en uit wordt gestreamd. Meer meeslepende en gedetailleerde werelden kunnen op een breder scala van apparaten worden gespeeld.

-

Verbeterde prestaties

 — Betere frame rates en prestaties, aangezien de server minder tijd en bandbreedte kan besteden aan het synchroniseren van wijzigingen tussen de wereld en de spelers daarin. Clients besteden minder tijd aan het bijwerken van instanties die momenteel niet relevant zijn voor de speler.

-

Niveau van detail

 — Wanneer geconfigureerd, blijven verre modellen, platformavatars en terrein zichtbaar, zelfs wanneer ze niet naar clients worden gestreamd, waardoor het spel geoptimaliseerd blijft zonder volledig in te boeten op achtergrondvisuals. [SLIM](/docs/nl-nl/workspace/streaming/slim)  biedt het hoogste niveau van detail voor zowel modellen als avatars.

Instantie streaming wordt geregeld via de [Workspace.StreamingEnabled](/docs/nl-nl/reference/engine/classes/Workspace#StreamingEnabled)  eigenschap, die standaard is ingeschakeld voor nieuwe plaatsen die in Studio zijn gemaakt. Deze eigenschap kan niet in een script worden ingesteld.

 ![Het eigenschappenvenster met de StreamingEnabled-eigenschap ingeschakeld.](https://prod.docsiteassets.roblox.com/assets/studio/properties/Workspace-StreamingEnabled.png)

Zodra je deze technische gids hebt doorgenomen, wordt aanbevolen dat je de [streamingtechnieken](/docs/nl-nl/workspace/streaming/techniques)  gids bekijkt over hoe je streaming efficiënt en effectief kunt gebruiken, en de [SLIM](/docs/nl-nl/workspace/streaming/slim)  gids voor het inschakelen van hoog-fidelity niveau van detail voor modellen en avatars.

## [Technisch gedrag](#technisch-gedrag)[](#technisch-gedrag)

### [Omvang](#omvang)[](#omvang)

Streaminglogica en -functies zijn uitsluitend van toepassing op instanties die afstammelingen zijn van [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) , terwijl instanties die zijn opgeslagen in andere containers zoals [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  en [ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst)  niet in aanmerking komen voor streaming. Bijvoorbeeld, het plaatsen van een [atomisch](#atomisch)  model onder [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  garandeert geen atomische replicatie.

### [Stream in](#stream-in)[](#stream-in)

Wanneer een speler zich bij een spel voegt met instantie streaming ingeschakeld:

1.

Instanties in de [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  worden gerepliceerd naar de client met uitzondering van  de volgende:

![](https://prod.docsiteassets.roblox.com/assets/misc/Wait.png)

[BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  ([Parts](/docs/nl-nl/reference/engine/classes/Part)  en [MeshParts](/docs/nl-nl/reference/engine/classes/MeshPart) )

![](https://prod.docsiteassets.roblox.com/assets/misc/Wait.png)

[Models](/docs/nl-nl/reference/engine/classes/Model)  ingesteld op [Atomisch](#atomisch) , [Persistent](#persistent)  of [PersistentPerPlayer](#persistentperplayer) ; zie [per-model streamingcontroles](#model-streamingcontroles)

![](https://prod.docsiteassets.roblox.com/assets/misc/Wait.png)

[Models](/docs/nl-nl/reference/engine/classes/Model)  ingesteld op [Niet-atomisch](#niet-atomisch)  (standaard) wanneer [Workspace.ModelStreamingBehavior](/docs/nl-nl/reference/engine/classes/Workspace#ModelStreamingBehavior)  is ingesteld op [Improved](/docs/nl-nl/reference/engine/enums/ModelStreamingBehavior#Improved)

![](https://prod.docsiteassets.roblox.com/assets/misc/Wait.png)

Afstammelingen van de bovenstaande instanties

2.

Tijdens het spel kan de server instanties in de bovenstaande uitgestelde categorieën naar de client streamen op basis van de [streaming-eigenschappen](#streaming-eigenschappen)  van het spel, de positie van de speler, de prestaties van het clientapparaat en andere voorwaarden.

### [Stream uit](#stream-uit)[](#stream-uit)

Tijdens het spel kan een client regio's van [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  uit de [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  van de speler verwijderen op basis van het gedrag dat is ingesteld door [Workspace.StreamOutBehavior](/docs/nl-nl/reference/engine/classes/Workspace#StreamOutBehavior) . Het proces begint met regio's die het verst van de [replicatiefoci](#replicatiefocus)  verwijderd zijn en beweegt dichterbij, indien nodig. Regio's binnen het bereik van [Workspace.StreamingMinRadius](/docs/nl-nl/reference/engine/classes/Workspace#StreamingMinRadius)  worden nooit uitgestreamd.

Merk op dat een [Model](/docs/nl-nl/reference/engine/classes/Model)  zonder [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  afstammelingen, zoals een die slechts als een "container" voor niet-[BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  instanties zoals scripts wordt gebruikt, vrijgesteld  is van streaming uit tenzij  het een afstammeling van een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  wordt.

Instanties die zijn gemaakt  of gekloneerd  door client-side scripts zijn vrijgesteld van streaming uit, tenzij ze zijn gepaard onder een server-gecreëerde instantie.

Wanneer een instantie uitstreamt, wordt deze aan nil  gekoppeld, zodat elke bestaande Luau-status opnieuw verbinding maakt als de instantie weer instreamt. Als gevolg hiervan worden verwijderingssignalen zoals [ChildRemoved](/docs/nl-nl/reference/engine/classes/Instance#ChildRemoved)  of [DescendantRemoving](/docs/nl-nl/reference/engine/classes/Instance#DescendantRemoving)  geactiveerd op zijn ouder  of voorouder , maar de instantie zelf wordt niet vernietigd in dezelfde zin als een [Instance:Destroy()](/docs/nl-nl/reference/engine/classes/Instance#Destroy)  aanroep. Lokale wijzigingen aan instantie-eigenschappen (wijzigingen die bestaan op een client en niet zijn gerepliceerd naar de server) kunnen verloren gaan als de instanties uitstreamen en later weer instreamen.

### [Assemblies](#assemblies)[](#assemblies)

Fysieke [assemblies](/docs/nl-nl/physics/assemblies)  streamen in  als complete eenheden, inclusief hun bijbehorende [Constraints](/docs/nl-nl/reference/engine/classes/Constraint)  en [Attachments](/docs/nl-nl/reference/engine/classes/Attachment) , wat helpt om consistente fysica-updates op clients te waarborgen. De enige uitzondering is wanneer de assembly is [geankerd](/docs/nl-nl/physics/assemblies#gedrag-bij-verankering) , in welk geval alleen de [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  binnen de streamingradius samen met hun bijbehorende [Constraints](/docs/nl-nl/reference/engine/classes/Constraint)  en [Attachments](/docs/nl-nl/reference/engine/classes/Attachment)  worden gestreamd.

Assemblies streamen niet uit  totdat al hun [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  in aanmerking komen om uit te streamen.

Vermijd het creëren van bewegende assemblies met onnodig grote aantallen instanties, aangezien al deze instanties die in unison streamen netwerk/CPU-pieken kunnen veroorzaken.

## [Streaming-eigenschappen](#streaming-eigenschappen)[](#streaming-eigenschappen)

De volgende eigenschappen regelen hoe instantie streaming van toepassing is op jouw spel. Al deze eigenschappen zijn niet-scriptable  en moeten worden ingesteld op het [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  object in Studio.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Workspace-Streaming.png)

| Eigenschap | | Beschrijving |
| --- | --- |
| [EnableSLIMAvatars](/docs/nl-nl/reference/engine/classes/Workspace#EnableSLIMAvatars) | | Regelt of een [SLIM](/docs/nl-nl/workspace/streaming/slim#enabling-slim-for-avatars)  model wordt gegenereerd voor avatarpersonages in het spel. Wanneer ingeschakeld, renderen avatars met behulp van SLIM op dezelfde manier als het instellen van [Model.LevelOfDetail](/docs/nl-nl/reference/engine/classes/Model#LevelOfDetail)  op [SLIM](/docs/nl-nl/reference/engine/enums/ModelLevelOfDetail#SLIM)  werkt voor andere modellen. Zie [SLIM](/docs/nl-nl/workspace/streaming/slim)  voor details. |
| [ModelStreamingBehavior](/docs/nl-nl/reference/engine/classes/Workspace#ModelStreamingBehavior) | | Regelt hoe [Niet-atomische](#niet-atomisch)  (standaard) modellen in en uit streamen.

AANBEVOLEN

 Gebruik [Improved](/docs/nl-nl/reference/engine/enums/ModelStreamingBehavior#Improved)  om de meest efficiënte streaming voor [Models](/docs/nl-nl/reference/engine/classes/Model)  met [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  afstammelingen in te schakelen. |
| [PredictiveStreamingMode](/docs/nl-nl/reference/engine/classes/Workspace#PredictiveStreamingMode) | | Opt-in voor [voorspellende streaming](#voorspellende-streaming)  die enginesignalen gebruikt om proactief gebieden te streamen die een speler waarschijnlijk binnenkort nodig heeft, zoals respawnlocaties of regio's die de speler onlangs heeft verlaten via [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  wijziging. Voorspellingen zijn optioneel, vervallen na een korte tijd als ze niet worden gebruikt, en worden overgeslagen op clients met beperkte middelen. |
| [StreamingIntegrityMode](/docs/nl-nl/reference/engine/classes/Workspace#StreamingIntegrityMode) | | Het spel kan zich op ongewenste manieren gedragen als een speler zich in een regio van de wereld beweegt die niet naar hen is gestreamd. Deze eigenschap biedt een manier om die potentieel problematische situaties te vermijden.

AANBEVOLEN

 Gebruik [PauseOutsideLoadedArea](/docs/nl-nl/reference/engine/enums/StreamingIntegrityMode#PauseOutsideLoadedArea)  om de integriteit van het spel in balans te houden zonder onnodig of te vaak te pauzeren. Je kunt ook [de pauzescherm](#pauzescherm-aanpassing)  aanpassen. |
| [StreamingMinRadius](/docs/nl-nl/reference/engine/classes/Workspace#StreamingMinRadius) | | Deze eigenschap geeft de straal aan rond de [replicatiefoci](#replicatiefocus)  waarin instanties met de hoogste prioriteit in streamen. Wees voorzichtig bij het verhogen van de standaard, aangezien dit meer geheugen en meer serverbandbreedte vereist ten koste van andere componenten.

AANBEVOLEN

 Gebruik de standaardwaarde van 64  om te maximaliseren hoeveel de engine het spel kan schalen voor low-end apparaten. |
| [StreamingTargetRadius](/docs/nl-nl/reference/engine/classes/Workspace#StreamingTargetRadius) | | Deze eigenschap regelt de maximale afstand van de [replicatiefoci](#replicatiefocus)  waarbinnen instanties in streamen. Merk op dat de engine is toegestaan om eerder geladen instanties buiten de doelradius te behouden, mits het geheugen dat toelaat.
Een kleinere [StreamingTargetRadius](/docs/nl-nl/reference/engine/classes/Workspace#StreamingTargetRadius)  vermindert de serverbelasting, aangezien de server geen extra instanties zal streamen buiten de ingestelde waarde. De doelradius is echter ook de maximale afstand die spelers in staat zullen zijn om de volledige details van jouw spel te zien, dus je moet een waarde kiezen die een goede balans tussen deze creëert.

AANBEVOLEN

 Gebruik de standaardwaarde van 1024  om een goede balans te vinden tussen zichtbaarheid voor spelers op high-end apparaten en een redelijke geheugendruk. |
| [StreamOutBehavior](/docs/nl-nl/reference/engine/classes/Workspace#StreamOutBehavior) | | Deze eigenschap stelt het [streaming uit](#stream-uit)  gedrag in volgens de waarde van [Enum.StreamOutBehavior](/docs/nl-nl/reference/engine/enums/StreamOutBehavior) . Als ingesteld op [LowMemory](/docs/nl-nl/reference/engine/enums/StreamOutBehavior#LowMemory)  (standaard), streamt de client alleen regio's uit die verder zijn dan de minimale straal in een situatie met laag geheugen. Als ingesteld op [Opportunistic](/docs/nl-nl/reference/engine/enums/StreamOutBehavior#Opportunistic) , kunnen regio's buiten [StreamingTargetRadius](/docs/nl-nl/reference/engine/classes/Workspace#StreamingTargetRadius)  op de client worden verwijderd, zelfs wanneer er geen geheugendruk is (in deze modus verwijdert de client nooit instanties die binnen de doelradius zijn, behalve in situaties met laag geheugen).

AANBEVOLEN

 Gebruik [Opportunistic](/docs/nl-nl/reference/engine/enums/StreamOutBehavior#Opportunistic)  om de client in staat te stellen agressief ongewenste inhoud te verzamelen, wat het geheugengebruik aanzienlijk vermindert en helpt om uit-geheugen crashes te voorkomen. |

[StreamingTargetRadius](/docs/nl-nl/reference/engine/classes/Workspace#StreamingTargetRadius)  moet groter zijn dan [StreamingMinRadius](/docs/nl-nl/reference/engine/classes/Workspace#StreamingMinRadius) . 3D-inhoud tussen de doelradius en de minimale straal fungeert als een buffer voor het geval de client tijdelijk stopt met het ontvangen van nieuwe inhoud van de server. Als de minimale straal en de doelradius gelijk zijn, is er geen buffer, wat kan leiden tot een toename van netwerkpauzes of een anderszins suboptimale spelerservaring.

## [Replicatiefocus](#replicatiefocus)[](#replicatiefocus)

Standaard vindt streaming plaats rond het [PrimaryPart](/docs/nl-nl/reference/engine/classes/Model#PrimaryPart)  van het lokale personage van de speler, hoewel je een ander replicatiefocuspunt kunt specificeren via [Player.ReplicationFocus](/docs/nl-nl/reference/engine/classes/Player#ReplicationFocus) .

Je kunt ook extra replicatiefoci toevoegen en verwijderen via [Player:AddReplicationFocus()](/docs/nl-nl/reference/engine/classes/Player#AddReplicationFocus)  en [Player:RemoveReplicationFocus()](/docs/nl-nl/reference/engine/classes/Player#RemoveReplicationFocus)  om dynamisch streaming in meerdere gebieden van het spel in te schakelen.

Wees voorzichtig bij het toevoegen van extra replicatiefoci, aangezien elke extra focus de serverbelasting voor streaming en het bijwerken van regio's verhoogt. Bijvoorbeeld, een enkele speler met negen dynamisch bewegende foci kan servernetwerk- en streamingverwerking genereren die vergelijkbaar is met tien spelers die zich door het spel bewegen.

Ook op de client kan een te groot aantal foci voor een speler de mogelijkheid van de engine beperken om zich aan te passen aan geheugengebonden beperkingen en het waarschijnlijker maken dat clients door het besturingssysteem worden beëindigd vanwege te veel geheugengebruik.

Fysica-simulatie Beweging tussen zones Verre gezichtspunten

Client-side fysica-simulatie, inclusief voorspelling en hersimulaties wanneer [serverautoriteit](/docs/nl-nl/projects/server-authority)  is geïmplementeerd, vindt alleen plaats in gestreamde gebieden, zelfs voor lokaal gemaakte instanties en voor [Persistent](/docs/nl-nl/reference/engine/enums/ModelStreamingMode#Persistent)  instanties. Als je instanties hebt die je wilt blijven simuleren, zelfs wanneer ze ver van het personage zijn, maak dan een extra replicatiefocus in de buurt van die instanties.

## [Voorspellende streaming](#voorspellende-streaming)[](#voorspellende-streaming)

Voorspellende streaming is een opt-in functie die enginesignalen gebruikt om de beweging van spelers te anticiperen en proactief gebieden te streamen die de speler waarschijnlijk binnenkort nodig heeft. Wanneer ingeschakeld door [PredictiveStreamingMode](/docs/nl-nl/reference/engine/classes/Workspace#PredictiveStreamingMode)  in te stellen op [Enabled](/docs/nl-nl/reference/engine/enums/PredictiveStreamingMode#Enabled) , kan het streamingpauzes en visuele pop-in verminderen zonder enige codewijzigingen.

Voorspellende streaming is additief . Het creëert kleine, tijdelijke streamingfoci naast je bestaande [replicatiefoci](#replicatiefocus) , streamt een kleine hoeveelheid extra inhoud en verandert je spel-logica of streamingcontracten niet. Als een voorspelling niet nodig is, vervalt het voorspelde gebied na een korte tijd en laadt de engine de inhoud niet meer. De engine houdt ook rekening met het geheugen en de prestaties van de client, en slaat voorspellingen over op apparaten met beperkte middelen.

Wanneer [PredictiveStreamingMode](/docs/nl-nl/reference/engine/classes/Workspace#PredictiveStreamingMode)  is ingesteld op [Enabled](/docs/nl-nl/reference/engine/enums/PredictiveStreamingMode#Enabled) , zijn de volgende voorspellende functies actief:

| Functie | | Beschrijving |
| Spawn pre-fetching | | Wanneer een speler sterft, creëert de engine kleine, tijdelijke streamingfoci op mogelijke spawnlocaties, zodat waarschijnlijke respawngebieden beginnen te streamen voordat het spelerpersonage verschijnt, waardoor pauzes en ontbrekende inhoud onmiddellijk na respawn worden verminderd. |
| [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  retouroptimalisatie | | Wanneer een speler [CFrames](/docs/nl-nl/reference/engine/datatypes/CFrame)  weg is van een gebied, creëert de engine een kleine, tijdelijke streamingfocus op de locatie die ze hebben verlaten. Dit helpt dat gebied gestreamd te houden als de speler kort daarna terugkeert, een veelvoorkomend scenario bij het bewegen tussen gebouwen, subniveaus, winkels of hubs. |

Voorspellende streaming werkt naadloos samen met handmatig gemaakte pre-fetches ([Player:RequestStreamAroundAsync()](/docs/nl-nl/reference/engine/classes/Player#RequestStreamAroundAsync) ) en meerdere replicatiefoci ([Player:AddReplicationFocus()](/docs/nl-nl/reference/engine/classes/Player#AddReplicationFocus) ). Als je al een pre-fetch of replicatiefocus op een specifieke locatie hebt gemaakt, voegt voorspellende streaming daar geen extra streamingfocus aan toe.

## [Model streamingcontroles](#model-streamingcontroles)[](#model-streamingcontroles)

Om problemen met streaming op basis van per-model te vermijden en het gebruik van [WaitForChild()](/docs/nl-nl/reference/engine/classes/Instance#WaitForChild)  te minimaliseren, kun je aanpassen hoe [Models](/docs/nl-nl/reference/engine/classes/Model)  en hun afstammelingen streamen via hun [ModelStreamingMode](/docs/nl-nl/reference/engine/classes/Model#ModelStreamingMode)  eigenschap.

### [Niet-atomisch](#niet-atomisch)[](#niet-atomisch)

Standaard zijn modellen [Nonatomic](/docs/nl-nl/reference/engine/enums/ModelStreamingMode#Nonatomic)  en streamen ze in/uit op basis van of [Workspace.ModelStreamingBehavior](/docs/nl-nl/reference/engine/classes/Workspace#ModelStreamingBehavior)  is ingesteld op [Legacy](/docs/nl-nl/reference/engine/enums/ModelStreamingBehavior#Legacy)  (standaard) of [Improved](/docs/nl-nl/reference/engine/enums/ModelStreamingBehavior#Improved) .

###### Legacy

Wanneer [Workspace.ModelStreamingBehavior](/docs/nl-nl/reference/engine/classes/Workspace#ModelStreamingBehavior)  is ingesteld op [Legacy](/docs/nl-nl/reference/engine/enums/ModelStreamingBehavior#Legacy)  (standaard), wordt de [Model](/docs/nl-nl/reference/engine/classes/Model)  container en zijn niet -[BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  afstammelingen zoals [Scripts](/docs/nl-nl/reference/engine/classes/Script)  gerepliceerd naar de client wanneer de speler zich aanmeldt. Vervolgens, wanneer in aanmerking komende, streamen de [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  afstammelingen van het model in.

 ![](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/Model-Stream-In-Default.png)

###### Verbeterd

Wanneer [Workspace.ModelStreamingBehavior](/docs/nl-nl/reference/engine/classes/Workspace#ModelStreamingBehavior)  is ingesteld op [Improved](/docs/nl-nl/reference/engine/enums/ModelStreamingBehavior#Improved) , varieert het streaminggedrag van modellen afhankelijk van of het model [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  afstammelingen bevat of geen  [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  afstammelingen bevat:

-

Een model met [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  afstammelingen streamt in  alleen wanneer één  van zijn [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  afstammelingen in aanmerking komt om in te streamen. Op dat moment streamt het model en de in aanmerking komende [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  in, samen met de niet -[BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  afstammelingen van het model.

Wanneer de allerlaatste resterende [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  van het model uit  streamt, zal het model zelf ook samen met deze uitstreamen.

 ![](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/Model-Stream-In-Improved-Spatial.png)

-

Een model zonder [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  afstammelingen, zoals een die slechts als een "container" voor niet-[BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  instanties zoals scripts wordt gebruikt, wordt kort na de aanmelding van de speler naar de client gerepliceerd. Dit type model is vrijgesteld  van streaming uit tenzij  het een afstammeling van een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  wordt.

 ![](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/Model-Stream-In-Improved-Non-Spatial.png)

### [Atomisch](#atomisch)[](#atomisch)

Als een [Model](/docs/nl-nl/reference/engine/classes/Model)  is ingesteld op [Atomic](/docs/nl-nl/reference/engine/enums/ModelStreamingMode#Atomic) , worden al zijn initiële afstammelingen samen gestreamd wanneer een afstammeling [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  in aanmerking komt om te worden gestreamd. Als gevolg hiervan zou een client-side script dat toegang nodig heeft tot instanties binnen  het model [WaitForChild()](/docs/nl-nl/reference/engine/classes/Instance#WaitForChild)  op het model zelf moeten gebruiken, maar niet op een afstammeling [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  of [Part](/docs/nl-nl/reference/engine/classes/Part) , aangezien deze samen met het model worden verzonden.

Een atomisch model wordt alleen uitgestreamd wanneer al zijn afstammelingen in aanmerking komen om uit te streamen, op welk punt het hele model samen uitstreamt.

 ![Een diagram dat atomische modelstreaming samen met kinderen toont.](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/Model-Streaming-Mode-Atomic.png)

### [Persistent](#persistent)[](#persistent)

[Persistent](/docs/nl-nl/reference/engine/enums/ModelStreamingMode#Persistent)  modellen zijn niet onderhevig aan normale streaming in of uit. Ze worden als een complete atomische eenheid verzonden kort nadat de speler zich aanmeldt en voordat het [Workspace.PersistentLoaded](/docs/nl-nl/reference/engine/classes/Workspace#PersistentLoaded)  evenement wordt geactiveerd. Persistente modellen en hun afstammelingen worden nooit uitgestreamd, maar om streaming in veilig te verwerken binnen een client-side script, moet je wachten tot het [PersistentLoaded](/docs/nl-nl/reference/engine/classes/Workspace#PersistentLoaded)  evenement wordt geactiveerd.

 ![Een diagram dat persistente modelstreaming samen met kinderen toont.](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/Model-Streaming-Mode-Persistent.png)

Persistente modellen zijn bedoeld voor zeer zeldzame omstandigheden, zoals wanneer een klein aantal onderdelen altijd aanwezig moet zijn op clients zodat client-side scripts toegang hebben. Indien mogelijk moeten server-side [Scripts](/docs/nl-nl/reference/engine/classes/Script)  worden gebruikt, of client scripts moeten tolerant zijn voor onderdelen die in en uit streamen. Persistente modellen zijn niet  bedoeld om streaming te omzeilen, en overmatig gebruik kan de prestaties negatief beïnvloeden.

### [PersistentPerPlayer](#persistentperplayer)[](#persistentperplayer)

Modellen ingesteld op [PersistentPerPlayer](/docs/nl-nl/reference/engine/enums/ModelStreamingMode#PersistentPerPlayer)  gedragen zich hetzelfde als [Persistent](/docs/nl-nl/reference/engine/enums/ModelStreamingMode#Persistent)  voor spelers die zijn toegevoegd met [Model:AddPersistentPlayer()](/docs/nl-nl/reference/engine/classes/Model#AddPersistentPlayer) . Voor andere spelers is het gedrag hetzelfde als [Atomic](/docs/nl-nl/reference/engine/enums/ModelStreamingMode#Atomic) . Je kunt een model van spelerspersistentie terugdraaien via [Model:RemovePersistentPlayer()](/docs/nl-nl/reference/engine/classes/Model#RemovePersistentPlayer) .

## [Pauzescherm aanpassing](#pauzescherm-aanpassing)[](#pauzescherm-aanpassing)

Aangenomen dat [Workspace.StreamingIntegrityMode](/docs/nl-nl/reference/engine/classes/Workspace#StreamingIntegrityMode)  is ingesteld op de aanbevolen [PauseOutsideLoadedArea](/docs/nl-nl/reference/engine/enums/StreamingIntegrityMode#PauseOutsideLoadedArea) , zal het spel pauzeren als een speler zich in een regio van de wereld beweegt die niet naar hen is gestreamd. In deze gevallen geeft de [Player.GameplayPaused](/docs/nl-nl/reference/engine/classes/Player#GameplayPaused)  eigenschap de huidige pauzestatus van de speler aan, die kan worden gebruikt met een [GetPropertyChangedSignal()](/docs/nl-nl/reference/engine/classes/Instance#GetPropertyChangedSignal)  verbinding om een aangepaste GUI weer te geven of te verbergen.

LocalScript

```

local Players = game:GetService("Players")

local GuiService = game:GetService("GuiService")

local player = Players.LocalPlayer

-- Standaard pauzescherm uitschakelen

GuiService:SetGameplayPausedNotificationEnabled(false)

local function onPauseStateChanged()

	if player.GameplayPaused then

		-- Toon aangepaste GUI

	else

		-- Verberg aangepaste GUI

	end

end

player:GetPropertyChangedSignal("GameplayPaused"):Connect(onPauseStateChanged)

```

## [Runtime debugging](#runtime-debugging)[](#runtime-debugging)

De engine bevat meerdere on-screen debugpanelen die op de client kunnen worden ingeschakeld met sneltoetsen. Om streaming debuginformatie te openen:

1.

Open de Netwerkstatistieken  debugoverlay. In een live ervaring, druk op Shift F3 . Wanneer je in Studio speelt, druk op Shift Ctrl F3  (Windows) of Shift ⌘ F3  (Mac).

2.

Zodra de debugoverlay is geopend, druk herhaaldelijk op Shift 1  om door de beschikbare panelen te cyclusen. Het vierde paneel is de Streaming  debugweergave die nuttige runtime-informatie weergeeft:

-

Actieve streaminginstellingen

-

Momenteel geladen (gestreamde) regio's

-

Streaminggedrag en -status

Zodra ingeschakeld, verschijnen gekleurde gemarkeerde regio's in de 3D-weergave:

| Kleur | | Beschrijving |
|  | |  Minder dan [StreamingMinRadius](/docs/nl-nl/reference/engine/classes/Workspace#StreamingMinRadius) |
|  | |  Groter dan of gelijk aan [StreamingMinRadius](/docs/nl-nl/reference/engine/classes/Workspace#StreamingMinRadius)  en minder dan [StreamingTargetRadius](/docs/nl-nl/reference/engine/classes/Workspace#StreamingTargetRadius) |
|  | |  Gelijk aan [StreamingTargetRadius](/docs/nl-nl/reference/engine/classes/Workspace#StreamingTargetRadius) |
|  | |  Groter dan [StreamingTargetRadius](/docs/nl-nl/reference/engine/classes/Workspace#StreamingTargetRadius) |

Om de mogelijkheid om de standaardcamera aanzienlijk ver weg te zoomen tijdens het debuggen te vergroten, verhoog tijdelijk [StarterPlayer.CameraMaxZoomDistance](/docs/nl-nl/reference/engine/classes/StarterPlayer#CameraMaxZoomDistance)  tijdens de bewerkingsmodus of [Player.CameraMaxZoomDistance](/docs/nl-nl/reference/engine/classes/Player#CameraMaxZoomDistance)  tijdens runtime. Een waarde van 1000 , bijvoorbeeld, stelt je in staat om de camera naar buiten te trekken om het grootste deel van de 3D-wereld te bekijken terwijl je nog steeds het personage navigeert.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
