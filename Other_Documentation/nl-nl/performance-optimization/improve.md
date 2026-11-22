<!-- Source: https://create.roblox.com/docs/nl-nl/performance-optimization/improve -->

Verbeter prestaties | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Prestatieoptimalisatie](/docs/nl-nl/performance-optimization)

# Verbeter prestaties

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Deze pagina beschrijft veelvoorkomende prestatieproblemen en best practices om deze te verhelpen.

## [Scriptberekeningen](#scriptberekeningen)[](#scriptberekeningen)

Dure bewerkingen in Luau-code duren langer om te verwerken en kunnen daardoor de framerate beïnvloeden. Tenzij het parallel wordt uitgevoerd, draait Luau-code synchroon en blokkeert de hoofdthread totdat het een functie tegenkomt die de thread laat wachten.

### [Veelvoorkomende problemen](#veelvoorkomende-problemen)[](#veelvoorkomende-problemen)

-

Intensieve bewerkingen op tabelstructuren  - Complexe bewerkingen zoals serialisatie, deserialisatie en diep klonen brengen hoge prestatiekosten met zich mee, vooral bij grote tabelstructuren. Dit geldt vooral als deze bewerkingen recursief zijn of het itereren over zeer grote datastructuren omvatten.

-

Hoge frequentie evenementen  - Het koppelen van dure bewerkingen aan frame-gebaseerde evenementen van [RunService](/docs/nl-nl/reference/engine/classes/RunService)  zonder de frequentie te beperken, betekent dat deze bewerkingen elke frame worden herhaald, wat vaak resulteert in een onnodige toename van de rekentijd. Deze evenementen omvatten:

-

[RunService.PreAnimation](/docs/nl-nl/reference/engine/classes/RunService#PreAnimation)

-

[RunService.PreRender](/docs/nl-nl/reference/engine/classes/RunService#PreRender)

-

[RunService.PreSimulation](/docs/nl-nl/reference/engine/classes/RunService#PreSimulation)

-

[RunService.PostSimulation](/docs/nl-nl/reference/engine/classes/RunService#PostSimulation)

-

[RunService.Heartbeat](/docs/nl-nl/reference/engine/classes/RunService#Heartbeat)

### [Mitigatie](#mitigatie)[](#mitigatie)

-

Roep code op bij [RunService](/docs/nl-nl/reference/engine/classes/RunService) -evenementen spaarzaam aan, beperk het gebruik tot gevallen waarin hoge frequentie-aanroep essentieel is (bijvoorbeeld, het bijwerken van de camera). Je kunt de meeste andere code in andere evenementen of minder vaak in een lus uitvoeren.

-

Verdeel grote of dure taken met behulp van [task.wait()](/docs/nl-nl/reference/engine/libraries/task#wait)  om het werk over meerdere frames te spreiden.

-

Identificeer en optimaliseer onnodig dure bewerkingen en gebruik [multithreading](/docs/nl-nl/scripting/multithreading)  voor computationeel dure taken die geen toegang tot het datamodel hoeven te hebben.

-

Bepaalde server-side scripts kunnen profiteren van [native code generatie](/docs/nl-nl/luau/native-code-gen) , een eenvoudige vlag die een script compileert naar machinecode in plaats van bytecode.

-

Als je servers nog steeds CPU-tekort hebben na optimalisatie, kun je meer reserveren met [Extended Services for Compute](/docs/nl-nl/cloud-services/extended-services#uitgebreide-diensten-voor-rekenkracht) .

### [MicroProfiler scopes](#microprofiler-scopes)[](#microprofiler-scopes)

| Scope | | Geassocieerde berekening |
| --- | --- |
| RunService.PreRender | | Code die wordt uitgevoerd op het PreRender-evenement |
| RunService.PreSimulation | | Code die wordt uitgevoerd op het Stepped-evenement |
| RunService.PostSimulation | | Code die wordt uitgevoerd op het Heartbeat-evenement |
| RunService.Heartbeat | | Code die wordt uitgevoerd op het Heartbeat-evenement |

Voor meer informatie over het debuggen van scripts met behulp van de MicroProfiler, zie de [debug](/docs/nl-nl/reference/engine/libraries/debug) -bibliotheek, die functies bevat voor het taggen van specifieke code en het verder verhogen van de specificiteit, zoals [debug.profilebegin](/docs/nl-nl/reference/engine/libraries/debug#profilebegin)  en [debug.profileend](/docs/nl-nl/reference/engine/libraries/debug#profileend) . Veel Roblox API-methoden die door scripts worden aangeroepen, hebben ook hun eigen bijbehorende MicroProfiler-tags die nuttige signalen kunnen bieden.

## [Scriptgeheugengebruik](#scriptgeheugengebruik)[](#scriptgeheugengebruik)

Geheugenlekken kunnen optreden wanneer je scripts schrijft die geheugen verbruiken dat de garbage collector niet correct kan vrijgeven wanneer het niet meer in gebruik is. Lekken zijn specifiek wijdverspreid op de server, omdat ze continu online kunnen zijn gedurende vele dagen, terwijl een clientsessie veel korter is.

De volgende geheugengegevens in de Developer Console  kunnen wijzen op een probleem dat verder onderzoek vereist:

-

LuaHeap  - Hoge of groeiende consumptie suggereert een geheugenlek.

-

InstanceCount  - Consistent groeiende aantallen instanties suggereren dat verwijzingen naar sommige instanties in je code niet worden opgeruimd door de garbage collector.

-

PlaceScriptMemory  - Biedt een script-voor-script overzicht van geheugengebruik.

### [Veelvoorkomende problemen](#veelvoorkomende-problemen-1)[](#veelvoorkomende-problemen-1)

-

Verbonden verbindingen laten staan  - De engine verzamelt nooit evenementen die zijn verbonden met een instantie en alle waarden die binnen de verbonden callback worden verwezen. Daarom zijn actieve verbindingen van evenementen en code binnen de verbonden instanties, verbonden functies en verwezen waarden, buiten het bereik van de geheugen-garbage collector, zelfs nadat de evenementen zijn afgevuurd.

Hoewel evenementen worden losgekoppeld wanneer de instantie waartoe ze behoren wordt vernietigd, is een veelgemaakte fout om aan te nemen dat dit ook geldt voor [Player](/docs/nl-nl/reference/engine/classes/Player) -objecten. Nadat een gebruiker een spel verlaat, vernietigt de engine niet automatisch hun representatieve [Player](/docs/nl-nl/reference/engine/classes/Player) -object en karaktermodel, dus verbindingen met het [Player](/docs/nl-nl/reference/engine/classes/Player) -object en instanties onder het karaktermodel, zoals [CharacterAdded](/docs/nl-nl/reference/engine/classes/Player#CharacterAdded) , blijven geheugen verbruiken als je ze niet loskoppelt in je scripts. Dit kan na verloop van tijd leiden tot zeer significante geheugenlekken op de server naarmate honderden gebruikers het spel binnenkomen en verlaten.

-

Tabellen  - Het invoegen van objecten in tabellen maar ze niet verwijderen wanneer ze niet meer nodig zijn, veroorzaakt onnodig geheugengebruik, vooral voor tabellen die gebruikersgegevens bijhouden wanneer ze binnenkomen. Bijvoorbeeld, de volgende codevoorbeeld maakt een tabel die gebruikersinformatie toevoegt elke keer dat een gebruiker binnenkomt:

Voorbeeld

```

local playerInfo = {}

Players.PlayerAdded:Connect(function(player)

  playerInfo[player] = {} -- wat info

end)

```

Als je deze vermeldingen niet verwijdert wanneer ze niet meer nodig zijn, blijft de tabel in grootte toenemen en verbruikt meer geheugen naarmate meer gebruikers de sessie binnenkomen. Elke code die over deze tabel iterates, wordt ook computationeel duurder naarmate de tabel in grootte toeneemt.

### [Mitigatie](#mitigatie-1)[](#mitigatie-1)

Om alle gebruikte waarden op te ruimen om geheugenlekken te voorkomen:

-

Verbreek alle verbindingen  - Ga door je codebase en zorg ervoor dat elke verbinding wordt opgeruimd via een van de volgende paden:

-

Handmatig loskoppelen met behulp van de [Disconnect()](/docs/nl-nl/reference/engine/datatypes/RBXScriptConnection#Disconnect) -functie.

-

De instantie vernietigen waartoe het evenement behoort met de [Destroy()](/docs/nl-nl/reference/engine/classes/Instance#Destroy) -functie.

-

Het scriptobject vernietigen waar de verbinding naar terugleidt.

-

Verwijder spelerobjecten en karakters na het verlaten  - Schakel [Workspace.PlayerCharacterDestroyBehavior](/docs/nl-nl/reference/engine/classes/Workspace#PlayerCharacterDestroyBehavior)  in om automatisch spelerobjecten en karaktermodellen te vernietigen nadat een gebruiker vertrekt. Als je dat liever hebt, kun je ze ook handmatig opruimen:

Voorbeeld opruimen van speler en karakter

```

local Players = game:GetService("Players")

Players.PlayerAdded:Connect(function(player)

  player.CharacterRemoving:Connect(function(character)

    task.defer(character.Destroy, character)

  end)

end)

Players.PlayerRemoving:Connect(function(player)

  task.defer(player.Destroy, player)

end)

```

## [Fysica-berekeningen](#fysica-berekeningen)[](#fysica-berekeningen)

Overmatige fysica-simulatie kan een belangrijke oorzaak zijn van verhoogde rekentijd per frame, zowel op de server als op de client.

### [Veelvoorkomende problemen](#veelvoorkomende-problemen-2)[](#veelvoorkomende-problemen-2)

-

Overmatige frequentie van fysica-tijdstappen  - Standaard is het stapgedrag in [adaptieve modus](/docs/nl-nl/physics/adaptive-timestepping) , waarbij fysica stappen op 60 Hz, 120 Hz of 240 Hz, afhankelijk van de complexiteit van het fysica-mechanisme.

Een vaste modus met verbeterde nauwkeurigheid van fysica is ook beschikbaar, die alle fysica-assemblages dwingt om op 240 Hz te stappen (vier keer per frame). Dit resulteert in aanzienlijk meer berekeningen per frame.

-

Overmatig aantal complexiteit van gesimuleerde objecten  - Hoe meer 3D-assemblages worden gesimuleerd, hoe langer de fysica-berekeningen duren per frame. Vaak hebben spellen objecten die worden gesimuleerd die dat niet hoeven te zijn of hebben ze mechanismen die meer beperkingen en gewrichten hebben dan nodig is.

-

Te precieze botsingsdetectie  - Mesh-onderdelen hebben een [CollisionFidelity](/docs/nl-nl/reference/engine/classes/MeshPart#CollisionFidelity) -eigenschap voor het detecteren van botsingen die een verscheidenheid aan modi biedt met verschillende niveaus van prestatie-impact. De modus voor precieze botsingsdetectie voor mesh-onderdelen heeft de duurste prestatiekosten en kost de engine meer tijd om te berekenen.

### [Mitigatie](#mitigatie-2)[](#mitigatie-2)

-

Veranker onderdelen die geen simulatie vereisen  - Veranker alle onderdelen die niet door fysica hoeven te worden aangedreven, zoals voor statische NPC's.

-

Gebruik adaptieve fysica-stappen  - Adaptieve stappen passen dynamisch de snelheid van fysica-berekeningen aan voor fysica-mechanismen, waardoor fysica-updates in sommige gevallen minder vaak kunnen worden uitgevoerd.

-

Verminder de complexiteit van mechanismen

-

Minimaliseer waar mogelijk het aantal fysica-beperkingen of gewrichten in een assemblage.

-

Verminder de hoeveelheid zelf-botsing binnen een mechanisme, bijvoorbeeld door limieten of geen-botsing beperkingen toe te passen op ragdoll-ledematen om te voorkomen dat ze met elkaar botsen.

-

Verminder het gebruik van precieze botsingsnauwkeurigheid voor meshes

-

Voor kleine of niet-interactieve objecten waar gebruikers zelden het verschil opmerken, gebruik box-nauwkeurigheid.

-

Voor kleine-middelgrote objecten, gebruik box- of hull-nauwkeurigheden, afhankelijk van de vorm.

-

Voor grote en zeer complexe objecten, bouw aangepaste botsingen met behulp van onzichtbare onderdelen wanneer mogelijk.

-

Voor objecten die geen botsingen vereisen, schakel botsingen uit en gebruik box- of hull-nauwkeurigheid, aangezien de botsingsgeometrie nog steeds in het geheugen wordt opgeslagen.

-

Je kunt botsingsgeometrie voor debugdoeleinden in Studio weergeven door Botsingsnauwkeurigheid  in te schakelen vanuit de [Visualisatie-opties](/docs/nl-nl/studio/overview#visualisatie-opties)  widget in de rechterbovenhoek van het 3D-venster.

Alternatief kun je de CollisionFidelity=PreciseConvexDecomposition  filter toepassen op de [Explorer](/docs/nl-nl/studio/explorer#property-filters)  die een telling toont van alle mesh-onderdelen met de precieze nauwkeurigheid en je in staat stelt ze gemakkelijk te selecteren.

-

Voor een diepgaande walkthrough over hoe je een botsingsnauwkeurigheidsoptie kiest die je precisie- en prestatievereisten in balans houdt, zie [Stel fysica- en renderparameters in](/docs/nl-nl/tutorials/curriculums/environmental-art/assemble-an-asset-library#botsingsnauwkeurigheid) .

### [MicroProfiler scopes](#microprofiler-scopes-1)[](#microprofiler-scopes-1)

| Scope | | Geassocieerde berekening |
| physicsStepped | | Algemene fysica-berekening |
| worldStep | | Discrete fysica-stappen die elke frame worden genomen |

## [Fysica-geheugengebruik](#fysica-geheugengebruik)[](#fysica-geheugengebruik)

Fysica-beweging en botsingsdetectie verbruiken geheugen. Mesh-onderdelen hebben een [CollisionFidelity](/docs/nl-nl/reference/engine/classes/MeshPart#CollisionFidelity) -eigenschap die de benadering bepaalt die wordt gebruikt om de botsingsgrenzen van de mesh te evalueren.

### [Veelvoorkomend probleem](#veelvoorkomend-probleem)[](#veelvoorkomend-probleem)

De standaard- en precieze botsingsdetectiemodi verbruiken aanzienlijk meer geheugen dan de twee andere modi met lagere botsingsvormen.

Als je hoge niveaus van geheugengebruik onder PhysicsParts  ziet, moet je mogelijk onderzoeken of je de [botsingsnauwkeurigheid](/docs/nl-nl/workspace/collisions#mesh-en-solide-modelbotsingen)  van objecten in je spel kunt verlagen.

### [Hoe te mitigeren](#hoe-te-mitigeren)[](#hoe-te-mitigeren)

Om het geheugen dat wordt gebruikt voor botsingsnauwkeurigheid te verminderen:

-

Voor onderdelen die geen botsingen nodig hebben, schakel je hun botsingen uit door [BasePart.CanCollide](/docs/nl-nl/reference/engine/classes/BasePart#CanCollide) , [BasePart.CanTouch](/docs/nl-nl/reference/engine/classes/BasePart#CanTouch)  en [BasePart.CanQuery](/docs/nl-nl/reference/engine/classes/BasePart#CanQuery)  op false  te zetten.

-

Verminder de nauwkeurigheid van botsingen met behulp van de [CollisionFidelity](/docs/nl-nl/reference/engine/classes/MeshPart#CollisionFidelity) -instelling. [Box](/docs/nl-nl/reference/engine/enums/CollisionFidelity#Box)  heeft de laagste geheugenkosten, en [Default](/docs/nl-nl/reference/engine/enums/CollisionFidelity#Default)  en [Precise](/docs/nl-nl/reference/engine/enums/CollisionFidelity#Precise)  zijn over het algemeen duurder.

-

Het is over het algemeen veilig om de botsingsnauwkeurigheid van elk klein verankerd onderdeel in te stellen op [Box](/docs/nl-nl/reference/engine/enums/CollisionFidelity#Box) .

-

Voor zeer complexe grote meshes, wil je misschien je eigen botsingsmesh bouwen uit kleinere objecten met box-botsingsnauwkeurigheid.

## [Humanoïden](#humanoïden)[](#humanoïden)

[Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  is een klasse die een breed scala aan functionaliteiten biedt voor speler- en niet-spelerkarakters (NPC's). Hoewel krachtig, komt een [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  met aanzienlijke rekentijd.

### [Veelvoorkomende problemen](#veelvoorkomende-problemen-3)[](#veelvoorkomende-problemen-3)

-

Alle HumanoidStateTypes ingeschakeld laten op NPC's  - Er zijn prestatiekosten verbonden aan het ingeschakeld laten van bepaalde [HumanoidStateTypes](/docs/nl-nl/reference/engine/enums/HumanoidStateType) . Schakel alles uit wat niet nodig is voor je NPC's. Bijvoorbeeld, tenzij je NPC een ladder gaat beklimmen, is het veilig om de [Climbing](/docs/nl-nl/reference/engine/enums/HumanoidStateType#Climbing) -toestand uit te schakelen.

-

Modellen met [Humanoids](/docs/nl-nl/reference/engine/classes/Humanoid)  vaak instantiëren, wijzigen en opnieuw laten spawnen  - Dit kan intensief zijn voor de engine om te verwerken, vooral als deze modellen gelaagde kleding  gebruiken. Dit kan ook bijzonder problematisch zijn in spellen waar avatars vaak opnieuw spawnen.

-

In de MicroProfiler zijn lange updateInvalidatedFastClusters -tags (meer dan 4 ms) vaak een signaal dat avatar-instantie/modificatie overmatige ongeldigverklaringen triggert.

-

Humanoïden gebruiken in gevallen waar ze niet nodig zijn  - Statische NPC's die niet bewegen, hebben over het algemeen geen behoefte aan de [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid) -klasse.

-

Animaties afspelen op een groot aantal NPC's vanaf de server  - NPC-animaties die op de server draaien, moeten op de server worden gesimuleerd en naar de client worden gerepliceerd. Dit kan onnodige overhead met zich meebrengen.

-

Onnodige grootte- en schaalveranderingen uitvoeren  - Grootte/schaalveranderingen zorgen ervoor dat FastCluster opnieuw moet worden opgebouwd. Probeer dit te verminderen tijdens de gameplay als je prestatieproblemen gerelateerd aan FastCluster ziet. Evenzo kunnen andere eigenschapswijzigingen ook ervoor zorgen dat FastCluster opnieuw moet worden opgebouwd, dus verminder deze wijzigingen in het algemeen zoveel mogelijk.

### [Mitigatie](#mitigatie-3)[](#mitigatie-3)

-

Speel NPC-animaties op de client  - In spellen met een groot aantal NPC's, overweeg om de [Animator](/docs/nl-nl/reference/engine/classes/Animator)  op de client te maken en de animaties lokaal uit te voeren. Dit vermindert de belasting op de server en de noodzaak voor onnodige replicatie. Het maakt ook extra optimalisaties mogelijk (zoals alleen animaties afspelen voor NPC's die dicht bij het personage zijn).

-

Gebruik prestatievriendelijke alternatieven voor Humanoïden  - NPC-modellen hoeven niet noodzakelijkerwijs een humanoïde object te bevatten.

-

Voor statische NPC's, gebruik een eenvoudige [AnimationController](/docs/nl-nl/reference/engine/classes/AnimationController) , omdat ze niet hoeven te bewegen maar gewoon animaties moeten afspelen.

-

Voor bewegende NPC's, overweeg om je eigen bewegingscontroller te implementeren en een [AnimationController](/docs/nl-nl/reference/engine/classes/AnimationController)  voor animaties te gebruiken, afhankelijk van de complexiteit van je NPC's.

-

Schakel ongebruikte humanoïde toestanden uit  - Gebruik [Humanoid:SetStateEnabled()](/docs/nl-nl/reference/engine/classes/Humanoid#SetStateEnabled)  om alleen noodzakelijke toestanden voor elke humanoïde in te schakelen.

-

Pool NPC-modellen met frequente respawns  - In plaats van een NPC volledig te vernietigen, stuur de NPC naar een pool van inactieve NPC's. Op deze manier, wanneer een nieuwe NPC moet respawnen, kun je eenvoudig een van de NPC's uit de pool reactiveren. Dit proces wordt pooling genoemd, wat het aantal keren dat personages moeten worden geïnstantieerd minimaliseert.

-

Spawn NPC's alleen wanneer gebruikers in de buurt zijn  - Spawn geen NPC's wanneer gebruikers niet binnen bereik zijn, en verwijder ze wanneer gebruikers hun bereik verlaten.

-

Vermijd wijzigingen aan de avatarhiërarchie nadat deze is geïnstantieerd  - Bepaalde wijzigingen aan een avatarhiërarchie hebben aanzienlijke prestatie-implicaties. Enkele optimalisaties zijn beschikbaar:

-

Voor aangepaste procedurele animaties, werk niet de [JointInstance.C0](/docs/nl-nl/reference/engine/classes/JointInstance#C0)  en [JointInstance.C1](/docs/nl-nl/reference/engine/classes/JointInstance#C1) -eigenschappen bij. Werk in plaats daarvan de [Motor6D.Transform](/docs/nl-nl/reference/engine/classes/Motor6D#Transform) -eigenschap bij.

-

Als je enige [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) -objecten aan de avatar moet bevestigen, doe dit dan buiten de hiërarchie van het avatar [Model](/docs/nl-nl/reference/engine/classes/Model) .

### [MicroProfiler scopes](#microprofiler-scopes-2)[](#microprofiler-scopes-2)

| Scope | | Geassocieerde berekening |
| stepHumanoid | | Humanoid controle en fysica |
| stepAnimation | | Humanoid en animator animatie |
| updateInvalidatedFastClusters | | Geassocieerd met het instantiëren of wijzigen van een avatar |

## [Rendering](#rendering)[](#rendering)

Een aanzienlijk deel van de tijd die de client elke frame besteedt, is aan het renderen van de scène in het huidige frame. De server doet geen rendering, dus deze sectie is exclusief voor de client.

### [Tekenopdrachten](#tekenopdrachten)[](#tekenopdrachten)

Een tekenopdracht is een set instructies van de engine naar de GPU om iets te renderen. Tekenopdrachten hebben aanzienlijke overhead. Over het algemeen geldt: hoe minder tekenopdrachten per frame, hoe minder rekentijd er wordt besteed aan het renderen van een frame.

Je kunt zien hoeveel tekenopdrachten er momenteel plaatsvinden met de Render Stats  ⟩ Timing -item in Studio. Je kunt Render Stats  in de client bekijken door Shift F2  in te drukken.

Hoe meer objecten er in je scène moeten worden getekend in een gegeven frame, hoe meer tekenopdrachten er naar de GPU worden gedaan. De Roblox-engine maakt echter gebruik van een proces dat * instancing*  wordt genoemd om identieke meshes met dezelfde textuureigenschappen samen te voegen in een enkele tekenopdracht. Specifiek worden meerdere meshes met de zelfde [MeshContent](/docs/nl-nl/reference/engine/classes/MeshPart#MeshContent)  in een enkele tekenopdracht behandeld wanneer:

-

[SurfaceAppearances](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  identiek zijn als ze aanwezig zijn, anders wanneer [TextureContents](/docs/nl-nl/reference/engine/classes/MeshPart#TextureContent)  identiek zijn.

-

Materialen zijn identiek wanneer zowel [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  als [MeshPart.TextureID](/docs/nl-nl/reference/engine/classes/MeshPart#TextureID)  niet bestaan.

### [Andere veelvoorkomende problemen](#andere-veelvoorkomende-problemen)[](#andere-veelvoorkomende-problemen)

-

Overmatige objectdichtheid  - Als een groot aantal objecten geconcentreerd is met een hoge dichtheid, vereist het renderen van dit gebied van de scène meer tekenopdrachten. Als je merkt dat je framerate daalt wanneer je naar een bepaald deel van de kaart kijkt, kan dit een goed signaal zijn dat de objectdichtheid in dit gebied te hoog is.

Objecten zoals decals, texturen en deeltjes batchen niet goed en introduceren extra tekenopdrachten. Besteed extra aandacht aan deze objecttypes in een scène. In het bijzonder kunnen eigenschapswijzigingen aan [ParticleEmitters](/docs/nl-nl/reference/engine/classes/ParticleEmitter)  een dramatische impact op de prestaties hebben.

-

Gemiste instancing-kansen  - Vaak bevat een scène dezelfde mesh die meerdere keren is gedupliceerd, maar elke kopie van de mesh heeft verschillende mesh- of textuurasset-ID's. Dit voorkomt instancing en kan leiden tot onnodige tekenopdrachten.

Een veelvoorkomende oorzaak van dit probleem is wanneer een hele scène in één keer wordt geïmporteerd, in plaats van dat individuele assets in Roblox worden geïmporteerd en vervolgens na de import worden gedupliceerd om de scène samen te stellen.

Zelfs een eenvoudig script zoals dit kan je helpen om mesh-onderdelen met dezelfde naam te identificeren die verschillende mesh-ID's gebruiken:

```

for _,descendant in workspace:GetDescendants() do

  if descendant:IsA("MeshPart") then

    print(descendant.Name .. ", " .. descendant.MeshId)

  end

end

```

De uitvoer (met Stack Lines  ingeschakeld) kan er ongeveer zo uitzien. Herhaalde regels geven hergebruik van dezelfde mesh aan, wat goed is. Unieke regels zijn niet per se slecht, maar afhankelijk van je naamgevingsschema, kunnen ze duiden op dubbele meshes in je spel:

```

LargeRock, rbxassetid://106420009602747 (x144) -- goed

LargeRock, rbxassetid://120109824668127

LargeRock, rbxassetid://134460273008628

LargeRock, rbxassetid://139288987285823

LargeRock, rbxassetid://71302144984955

LargeRock, rbxassetid://90621205713698

LargeRock, rbxassetid://113160939160788

LargeRock, rbxassetid://135944592365226 -- alle mogelijke duplicaten

```

-

Overmatige objectcomplexiteit  - Hoewel het niet zo belangrijk is als het aantal tekenopdrachten, beïnvloedt het aantal driehoeken in een scène hoe lang een frame nodig heeft om te renderen. Scènes met een zeer groot aantal zeer complexe meshes zijn een veelvoorkomend probleem, evenals scènes met de [MeshPart.RenderFidelity](/docs/nl-nl/reference/engine/classes/MeshPart#RenderFidelity) -eigenschap ingesteld op [Precise](/docs/nl-nl/reference/engine/enums/RenderFidelity#Precise)  op te veel meshes.

-

Overmatige schaduwcasting  - Het omgaan met schaduwen is een duur proces, en kaarten die een hoog aantal en dichtheid van lichtobjecten bevatten die schaduwen casten (of een hoog aantal en dichtheid van kleine onderdelen die door schaduwen worden beïnvloed) kunnen prestatieproblemen hebben.

-

Hoge transparantie-overdraw  - Het plaatsen van objecten met gedeeltelijke transparantie dicht bij elkaar dwingt de engine om de overlappende pixels meerdere keren te renderen, wat de prestaties kan schaden. Voor meer informatie over het identificeren en oplossen van dit probleem, zie [Verwijder gelaagde transparanties](/docs/nl-nl/tutorials/curriculums/environmental-art/optimize-your-experience#verwijder-gelaagde-transparanties) .

-

Onnodige beweging van gelaagde MeshPart  - Gelaagde MeshParts die deel uitmaken van een Model zonder een Humanoid worden gegroepeerd met behulp van ruimtelijk georganiseerde FastClusters. Wanneer deze MeshParts bewegen, moeten ze voortdurend aan deze ruimtelijke clusters worden toegevoegd en verwijderd, waardoor de clusters opnieuw moeten worden opgebouwd en de prestaties worden beïnvloed.

-

Een zeer effectieve oplossing is om een Humanoid binnen het Model in te voegen. De aanwezigheid van een Humanoid overschrijft het standaard ruimtelijke clusteringgedrag, waardoor het gebruik van een enkele, verenigde FastCluster voor het hele Model verplicht wordt. Hierdoor zijn positie-updates niet langer nodig om clusteropbouw te vereisen, waardoor de prestatieknelpunt wordt verminderd. Deze techniek moet uitsluitend worden gereserveerd voor MeshParts met verwachte beweging, omdat het geheugenoverhead kan introduceren en de voordelen van ruimtelijke optimalisatie kan tenietdoen. We raden aan om altijd je spel te profileren na het aanbrengen van dit soort wijzigingen. Zie [Tips voor humanoïde prestaties](#humano%C3%AFden)  voor aanvullende informatie.

-

Te veel onderdelen in een [Model](/docs/nl-nl/reference/engine/classes/Model)  - Te veel onderdelen in een Model kunnen vaker leiden tot opbouw vanwege de mogelijkheid dat de eigenschap van een onderdeel verandert, wat leidt tot de noodzaak van een volledige opbouw. Vind de juiste balans van onderdelen in een Model wanneer het FastCluster gebruikt.

### [Mitigatie](#mitigatie-4)[](#mitigatie-4)

-

Instancing identieke meshes en het verminderen van het aantal unieke meshes  - Als je ervoor zorgt dat alle identieke meshes dezelfde onderliggende asset-ID's hebben, kan de engine ze herkennen en in een enkele tekenopdracht renderen. Zorg ervoor dat je elke mesh in een kaart slechts één keer uploadt en deze vervolgens in Studio dupliceert voor hergebruik in plaats van grote kaarten als geheel te importeren, wat kan leiden tot identieke meshes met afzonderlijke content-ID's die door de engine als unieke assets worden herkend. [Pakketten](/docs/nl-nl/projects/assets/packages)  zijn een nuttig mechanisme voor objecthergebruik.

-

Culling  - Culling beschrijft het proces van het elimineren van tekenopdrachten voor objecten die niet bijdragen aan het uiteindelijke gerenderde frame. Standaard slaat de engine tekenopdrachten over voor objecten buiten het gezichtsveld van de camera (frustum culling) en onderdelen, meshes en terrein die door andere objecten uit het zicht zijn geblokkeerd (occlusie culling). In bepaalde scenario's, zoals binnenomgevingen, kun je mogelijk een kamer- of portaal systeem implementeren en objecten handmatig cullen om de tekenopdrachten of de algehele rekentijd verder te verminderen.

-

Verminderen van het detailniveau voor modellen  - Schakel [instantie-streaming](/docs/nl-nl/workspace/streaming)  in en stel de [LevelOfDetail](/docs/nl-nl/reference/engine/classes/Model#LevelOfDetail) -eigenschap van je wereldmodellen in op [SLIM](/docs/nl-nl/reference/engine/enums/ModelLevelOfDetail#SLIM)  om [geoptimaliseerde lichte SLIM-meshes](/docs/nl-nl/workspace/streaming/slim#enabling-slim-for-models)  te renderen naarmate de afstand van de camera toeneemt.

-

Verminderen van het detailniveau voor avatars  - Schakel instantie-streaming in en stel [Workspace.EnableSLIMAvatars](/docs/nl-nl/reference/engine/classes/Workspace#EnableSLIMAvatars)  in om platformavatars als [geoptimaliseerde lichte SLIM-representaties](/docs/nl-nl/workspace/streaming/slim#enabling-slim-for-avatars)  te renderen met volledige animatieondersteuning naarmate de afstand van de camera toeneemt.

-

Verminderen van rendernauwkeurigheid  - Stel [MeshPart.RenderFidelity](/docs/nl-nl/reference/engine/classes/MeshPart#RenderFidelity)  in op [Automatic](/docs/nl-nl/reference/engine/enums/RenderFidelity#Automatic)  of [Performance](/docs/nl-nl/reference/engine/enums/RenderFidelity#Performance) . Dit stelt meshes in staat om terug te vallen op minder complexe alternatieven, wat het aantal polygonen dat moet worden getekend kan verminderen.

-

Schaduwcasting uitschakelen op geschikte onderdelen en lichtobjecten  - De Roblox-engine degradeert automatisch de schaduwkwaliteit naarmate het grafische kwaliteitsniveau van de client afneemt, en schakelt uiteindelijk schaduwen volledig uit op kwaliteitsniveaus onder 4. Je kunt echter selectief schaduwcasting-eigenschappen op lichtobjecten en onderdelen uitschakelen om de prestaties te verbeteren terwijl schaduwen zijn ingeschakeld en de kans te vergroten dat schaduwen ingeschakeld blijven. Enkele voorbeelden van optimalisaties die je kunt maken, hetzij tijdens de bewerkingstijd of dynamisch tijdens de runtime:

-

Gebruik de [BasePart.CastShadow](/docs/nl-nl/reference/engine/classes/BasePart#CastShadow) -eigenschap om schaduwcasting uit te schakelen op kleine onderdelen waar schaduwen waarschijnlijk niet zichtbaar zijn. Deze strategie is bijzonder effectief wanneer toegepast op onderdelen die ver weg zijn van de camera van de gebruiker.

Dit kan resulteren in visuele artefacten op schaduwen.

-

Schakel schaduwen uit op bewegende objecten wanneer mogelijk.

-

Schakel [Light.Shadows](/docs/nl-nl/reference/engine/classes/Light#Shadows)  uit op lichtinstanties waar het object geen schaduwen hoeft te casten.

-

Beperk het bereik en de hoek van lichtinstanties.

-

Gebruik minder lichtinstanties.

-

Overweeg om lichten uit te schakelen die buiten een specifiek bereik liggen of op basis van kamer-voor-kamer voor binnenomgevingen.

### [MicroProfiler scopes](#microprofiler-scopes-3)[](#microprofiler-scopes-3)

| Scope | | Geassocieerde berekening |
| Prepare and Perform | | Algemene rendering |
| Perform/Scene/computeLightingPerform | | Lichtrooster en schaduwupdates |
| LightGridCPU | | Voxel lichtroosterupdates |
| ShadowMapSystem | | Schaduwmapping |
| Perform/Scene/UpdateView | | Voorbereiding voor rendering en deeltjesupdates |
| Perform/Scene/RenderView | | Rendering en post-processing |

## [Netwerken en replicatie](#netwerken-en-replicatie)[](#netwerken-en-replicatie)

Netwerken en replicatie beschrijft het proces waarbij gegevens worden verzonden tussen de server en verbonden clients. Informatie wordt elke frame tussen de client en server verzonden, maar grotere hoeveelheden informatie vereisen meer rekentijd.

### [Veelvoorkomende problemen](#veelvoorkomende-problemen-4)[](#veelvoorkomende-problemen-4)

-

Overmatige externe verkeer  - Het verzenden van een grote hoeveelheid gegevens via [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  of [RemoteFunction](/docs/nl-nl/reference/engine/classes/RemoteFunction) -objecten of ze zeer frequent aanroepen kan leiden tot een grote hoeveelheid CPU-tijd die wordt besteed aan het verwerken van binnenkomende pakketten elke frame. Veelvoorkomende fouten zijn onder andere:

-

Gegevens repliceren elke frame die niet gerepliceerd hoeven te worden.

-

Gegevens repliceren op gebruikersinvoer zonder enige mechanismen om het te beperken.

-

Meer gegevens verzenden dan nodig is. Bijvoorbeeld, het verzenden van de volledige inventaris van de speler wanneer ze een item kopen in plaats van alleen de details van het aangekochte item.

-

Creëren of verwijderen van complexe instantiebomen  - Wanneer er een wijziging wordt aangebracht in het datamodel op de server, wordt dit gerepliceerd naar verbonden clients. Dit betekent dat het creëren en vernietigen van grote instantieshiërarchieën zoals kaarten tijdens runtime zeer netwerkintensief kan zijn.

Een veelvoorkomende schuldige hier is de complexe animatiedata die door Animation Editor  plugins in rigs wordt opgeslagen. Als deze niet worden verwijderd voordat het spel wordt gepubliceerd en het geanimeerde model regelmatig wordt gekloond, zal een grote hoeveelheid gegevens onnodig worden gerepliceerd.

-

Server-side TweenService  - Als [TweenService](/docs/nl-nl/reference/engine/classes/TweenService)  wordt gebruikt om een object server-side te tween, wordt de getweende eigenschap elke frame naar elke client gerepliceerd. Dit resulteert niet alleen in een jitterige tween naarmate de latentie van de clients fluctueert, maar het veroorzaakt ook veel onnodig netwerkverkeer.

### [Mitigatie](#mitigatie-5)[](#mitigatie-5)

Je kunt de volgende tactieken toepassen om onnodige replicatie te verminderen:

-

Vermijd het verzenden van grote hoeveelheden gegevens tegelijk via externe evenementen . Stuur in plaats daarvan alleen noodzakelijke gegevens met een lagere frequentie. Bijvoorbeeld, voor de status van een karakter, repliceer het wanneer het verandert in plaats van elke frame.

-

Chunk complexe instantiebomen  zoals kaarten en laad ze in stukken om het werk van het repliceren hiervan over meerdere frames te verdelen.

-

Ruim animatiemetadata op , vooral de animatiemap van rigs, na importeren.

-

Beperk onnodige instant replicatie , vooral in gevallen waar de server geen kennis hoeft te hebben van de instanties die worden gemaakt. Dit omvat:

-

Visuele effecten zoals een explosie of een magische spreuk. De server hoeft alleen de locatie te weten om de uitkomst te bepalen, terwijl de clients visuele effecten lokaal kunnen creëren.

-

Eerste-persoon itemweergave modellen.

-

Tween-objecten op de client in plaats van op de server.

### [MicroProfiler scopes](#microprofiler-scopes-4)[](#microprofiler-scopes-4)

| Scope | | Geassocieerde berekening |
| ProcessPackets | | Verwerking voor binnenkomende netwerkpakketten, zoals evenementaanroepen en eigenschapswijzigingen |
| Allocate Bandwidth and Run Senders | | Uitgaande evenementen relevant op servers |

## [Asset-geheugengebruik](#asset-geheugengebruik)[](#asset-geheugengebruik)

Het hoogste impactmechanisme dat beschikbaar is voor makers om het geheugengebruik van de client te verbeteren, is het inschakelen van [instantie-streaming](/docs/nl-nl/workspace/streaming) .

### [Instantie-streaming](#instantie-streaming)[](#instantie-streaming)

Instantie-streaming laadt selectief delen van het datamodel die niet nodig zijn, wat kan leiden tot aanzienlijk verminderde laadtijden en de mogelijkheid van de client om crashes te voorkomen wanneer deze onder geheugendruk komt.

Als je geheugenproblemen ondervindt en instantie-streaming is uitgeschakeld, overweeg dan om je spel bij te werken om het te ondersteunen, vooral als je 3D-wereld groot is. Instantie-streaming is gebaseerd op afstand in 3D-ruimte, dus grotere werelden profiteren van nature meer van.

Als instantie-streaming is ingeschakeld, kun je de agressiviteit ervan verhogen. Overweeg bijvoorbeeld:

-

Verminder het gebruik van [Enum.ModelStreamingMode.Persistent](/docs/nl-nl/reference/engine/enums/ModelStreamingMode#Persistent)  waar mogelijk. Je moet mogelijk je scripts bijwerken als je het als een compatibiliteitsmaatregel gebruikt.

-

Verminder de Workspace.StreamingMinRadius  en Workspace.StreamingTargetRadius .

Voor meer informatie over streamingopties en hun voordelen, zie [streaming-eigenschappen](/docs/nl-nl/workspace/streaming#streaming-eigenschappen) .

### [Andere veelvoorkomende problemen](#andere-veelvoorkomende-problemen-1)[](#andere-veelvoorkomende-problemen-1)

-

Assetduplicatie  - Een veelgemaakte fout is om hetzelfde asset meerdere keren te uploaden, wat resulteert in verschillende asset-ID's. Dit kan ertoe leiden dat dezelfde inhoud meerdere keren in het geheugen wordt geladen.

-

Overmatige assetvolume  - Zelfs wanneer assets niet identiek zijn, zijn er gevallen waarin kansen om dezelfde asset te hergebruiken en geheugen te besparen worden gemist.

-

Audiobestanden  - Audiobestanden kunnen een verrassende bijdrage leveren aan geheugengebruik, vooral als je ze allemaal tegelijk in de client laadt in plaats van alleen te laden wat je nodig hebt voor een deel van het spel. Voor strategieën, zie [Laadtijden](#laadtijden) .

-

Hoge resolutie texturen  - Het grafische geheugengebruik voor een textuur is niet gerelateerd aan de grootte van de textuur op de schijf; het aantal pixels in de textuur bepaalt het geheugengebruik. Bijvoorbeeld, een 1024x1024 pixel textuur verbruikt vier keer zoveel grafisch geheugen als een 512x512 textuur.

Afbeeldingen die naar Roblox zijn geüpload, worden omgezet naar een vast formaat, dus er is geen geheugengebruikvoordeel bij het uploaden van afbeeldingen in een kleurmodel dat minder bytes per pixel bevat. Evenzo kan het comprimeren van afbeeldingen vóór uploaden of het verwijderen van het alfakanaal van afbeeldingen die het niet nodig hebben, de afbeeldingsgrootte op de schijf verkleinen, maar verbetert het niet het geheugengebruik.

Terwijl een spel laadt, begint de engine automatisch met lagere kwaliteit texturen en verhoogt vervolgens de kwaliteit op basis van beschikbare apparaatgeheugen, afstand van de camera, hoeveelheid schermruimte die de textuur in beslag neemt en andere factoren. Zelfs dan kan het strategisch dimensioneren van je texturen het geheugengebruik in je spel verbeteren.

### [Mitigatie](#mitigatie-6)[](#mitigatie-6)

-

Upload assets slechts één keer  - Hergebruik dezelfde asset-ID over objecten en zorg ervoor dat dezelfde assets, vooral meshes en afbeeldingen, niet meerdere keren afzonderlijk worden geüpload.

-

Zoek en repareer dubbele assets  - Zoek naar identieke mesh-onderdelen en texturen die meerdere keren zijn geüpload met verschillende ID's.

-

Hoewel er geen API is om automatisch de gelijkenis van assets te detecteren, kun je alle afbeeldingsasset-ID's in je plaats verzamelen (hetzij handmatig of met een script), ze downloaden en vergelijken met behulp van externe vergelijkingshulpmiddelen.

-

Voor mesh-onderdelen is de beste strategie om unieke mesh-ID's te nemen en ze op grootte te organiseren om handmatig duplicaten te identificeren.

-

In plaats van aparte texturen voor verschillende kleuren te gebruiken, upload je een enkele textuur en gebruik je de [SurfaceAppearance.Color](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#Color) -eigenschap om verschillende tinten toe te passen.

-

Importeer assets in de kaart afzonderlijk  - In plaats van een hele kaart in één keer te importeren, importeer en reconstrueer je assets in de kaart individueel en reconstrueer ze. De Importer doet geen enkele deduplicatie van meshes, dus als je een grote kaart met veel afzonderlijke vloertegels zou importeren, zou elk van die tegels als een afzonderlijk asset worden geïmporteerd (zelfs als ze duplicaten zijn). Dit kan leiden tot prestatie- en geheugenproblemen in de toekomst, aangezien elke mesh als individueel wordt behandeld en geheugen en tekenopdrachten in beslag neemt.

-

Beperk het aantal pixels van afbeeldingen  tot niet meer dan de noodzakelijke hoeveelheid. Tenzij een afbeelding een groot fysiek ruimte op het scherm in beslag neemt, heeft deze meestal maximaal 512x512 pixels nodig. De meeste kleinere afbeeldingen zouden kleiner moeten zijn dan 256x256 pixels.

-

Gebruik trim sheets  om maximale textuurhergebruik in 3D-kaarten te waarborgen. Voor stappen en voorbeelden over hoe je trim sheets kunt maken, zie [Maak trim sheets](/docs/nl-nl/resources/beyond-the-dark/building-architecture#maak-trim-sheets) .

Je kunt ook overwegen om sprite sheets te gebruiken om veel kleinere UI-afbeeldingen als één afbeelding te laden. Je kunt vervolgens [ImageLabel.ImageRectOffset](/docs/nl-nl/reference/engine/classes/ImageLabel#ImageRectOffset)  en [ImageLabel.ImageRectSize](/docs/nl-nl/reference/engine/classes/ImageLabel#ImageRectSize)  gebruiken om delen van de sheet weer te geven.

## [Laadtijden](#laadtijden)[](#laadtijden)

Voordat een speler kan beginnen met spelen, moet de client alles in [ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst)  en [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) , de initiële inhoud van [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) , en alle assets die je scripts vooraf laden ontvangen. Hoe meer inhoud de client moet downloaden en verwerken tijdens deze tijd, hoe langer spelers moeten wachten. Voor een uitsplitsing van elke stap in het joinproces, zie [Identificeer prestatieproblemen](/docs/nl-nl/performance-optimization/identify#laadtijden) .

### [Veelvoorkomende problemen](#veelvoorkomende-problemen-5)[](#veelvoorkomende-problemen-5)

-

Instantie-streaming uitgeschakeld  - Zonder [instantie-streaming](/docs/nl-nl/workspace/streaming)  moet de hele [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  naar de client repliceren voordat de speler kan binnenkomen, dus spellen met veel onderdelen, modellen en assets hebben proportioneel langere laadtijden.

-

Overmatige inhoud in ReplicatedStorage  - Alles in [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  wordt naar elke client gerepliceerd voordat de speler iets kan zien of ermee kan interageren, ongeacht of de client het onmiddellijk nodig heeft. Gratis modellen en geërfde assets kunnen stilletjes aanzienlijke bulk toevoegen.

-

Zware ReplicatedFirst-inhoud  - [ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst)  wordt gerepliceerd voordat iets anders en bestaat voornamelijk om een aangepaste laadscreen vast te houden. Elke extra asset of script daarin vertraagt de start van de hoofdreplicatiefase.

-

Overmatig gebruik van [PreloadAsync()](/docs/nl-nl/reference/engine/classes/ContentProvider#PreloadAsync)  - Veel spellen implementeren aangepaste laadscreens en gebruiken [ContentProvider:PreloadAsync()](/docs/nl-nl/reference/engine/classes/ContentProvider#PreloadAsync)  om assets aan te vragen, zodat afbeeldingen, geluiden en meshes op de achtergrond worden gedownload. Deze aanpak zorgt ervoor dat belangrijke delen van je spel volledig zijn geladen zonder pop-in, maar een veelgemaakte fout is het vooraf laden van meer assets dan daadwerkelijk nodig zijn.

Een voorbeeld van een slechte praktijk is het laden van de hele [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) . Hoewel dit pop-in van texturen kan voorkomen, verhoogt het aanzienlijk de laadtijden.

Een andere vergelijkbare praktijk is het gebruik van [ContentProvider.RequestQueueSize](/docs/nl-nl/reference/engine/classes/ContentProvider#RequestQueueSize)  om ervoor te zorgen dat alle aangevraagde assets zijn geladen. Dit presenteert echter hetzelfde probleem van aanzienlijk verhoogde laadtijden, terwijl het ook een onbetrouwbare methode is vanwege de fluctuerende aard ervan.

-

Dure opstartscripts  - Zware scriptuitvoering in [LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript)  die tijdens het joinproces draaien, zoals het synchroon laden van grote datastructuren, vertraagt de overgang van replicatie naar een speelbare staat.

### [Mitigatie](#mitigatie-7)[](#mitigatie-7)

-

Schakel instantie-streaming in  - Streaming verzendt alleen het deel van je wereld nabij het spawnpunt van de speler bij de eerste binnenkomst, en streamt de rest geleidelijk in naarmate de speler door je spel beweegt. Voor spellen die het nog niet gebruiken, is streaming een van de meest effectieve manieren om laadtijden te verminderen. Streaming is standaard ingeschakeld voor nieuwe plaatsen. Voor setup-stappen, eigenschapsreferentie en migratiebegeleiding, zie [Instantie-streaming](/docs/nl-nl/workspace/streaming) .

Het inschakelen van streaming verandert hoe je spel gegevens naar clients repliceert. Nadat je het hebt ingeschakeld, test je grondig alle scripts die toegang hebben tot [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) -inhoud wanneer een speler binnenkomt, omdat die instanties mogelijk nog niet op de client aanwezig zijn.

-

Houd ReplicatedStorage slank  - Bewaar alleen wat clients nodig hebben op het moment dat ze binnenkomen, zoals gedeelde [ModuleScripts](/docs/nl-nl/reference/engine/classes/ModuleScript)  die [LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript)  vereisen. Verplaats grote modellen, audio en andere assets die niet onmiddellijk nodig zijn naar [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage) , en verplaats ze naar de client alleen wanneer een speler ze nodig heeft. Controleer [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  regelmatig op inhoud die je niet meer gebruikt.

-

Houd ReplicatedFirst slank  - Beperk [ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst)  tot wat je laadscreen nodig heeft, zoals basis UI-elementen in plaats van grote texturen of 3D-modellen, en vermijd zware berekeningen in scripts die daaruit draaien. Voor een walkthrough van het bouwen van een aangepaste laadscreen, inclusief wanneer je [ReplicatedFirst:RemoveDefaultLoadingScreen()](/docs/nl-nl/reference/engine/classes/ReplicatedFirst#RemoveDefaultLoadingScreen)  moet aanroepen, zie [Laadscreens](/docs/nl-nl/players/loading-screens) .

-

Laad alleen noodzakelijke assets vooraf  - Gebruik [ContentProvider:PreloadAsync()](/docs/nl-nl/reference/engine/classes/ContentProvider#PreloadAsync)  alleen in noodzakelijke situaties, waaronder:

-

Afbeeldingen in de laadscreen.

-

Belangrijke afbeeldingen in je spelmenu, zoals achtergrondafbeeldingen en pictogrammen.

-

Belangrijke assets in het start- of spawngebied.

Als je een groot aantal assets moet laden, raden we aan om een Overslaan van laden -knop te bieden.

-

Stel niet-essentiële opstartwerkzaamheden uit  - Laad inhoud die een speler nog niet heeft bereikt, zoals UI-panelen die ze nog niet hebben geopend, alleen wanneer het voor het eerst nodig is. Voor initialisatiewerk dat vroeg moet plaatsvinden, verspreid het over meerdere frames in plaats van het allemaal tegelijk uit te voeren. Voor technieken, zie [Scriptberekeningen](#scriptberekeningen) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
