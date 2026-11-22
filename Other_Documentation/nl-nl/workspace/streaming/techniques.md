<!-- Source: https://create.roblox.com/docs/nl-nl/workspace/streaming/techniques -->

Technieken en conversie | Documentatie - Roblox Creator Hub

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

# Technieken en conversie

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Deze gids schetst verschillende technieken voor het efficiënt en effectief gebruiken van in-game [instance streaming](/docs/nl-nl/workspace/streaming) . Hoewel er geen "one size fits all" oplossing is voor het ontwerpen van een streaming spel, zullen deze algemene stappen je het grootste deel van de weg helpen.

Als je een niet-streaming spel naar streaming converteert, zorg er dan voor dat je de [AI streaming conversie vaardigheid](#ai-streaming-conversie-vaardigheid)  bekijkt, die spellen automatisch naar streaming kan converteren.

## [Streaming eigenschappen](#streaming-eigenschappen)[](#streaming-eigenschappen)

Zodra [StreamingEnabled](/docs/nl-nl/reference/engine/classes/Workspace#StreamingEnabled)  is ingeschakeld voor het [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  object in Studio, stel je de gerelateerde eigenschappen in op de volgende aanbevolen waarden:

| Eigenschap | | Aanbeveling |
| --- | --- |
| [EnableSLIMAvatars](/docs/nl-nl/reference/engine/classes/Workspace#EnableSLIMAvatars) | | Gebruik [Enabled](/docs/nl-nl/reference/engine/enums/RolloutState#Enabled)  om R15 avatars weer te geven als lichte, geanimeerde stand-ins wanneer dat gepast is. Zie [SLIM avatars](#slim-avatars)  voor meer info. |
| [ModelStreamingBehavior](/docs/nl-nl/reference/engine/classes/Workspace#ModelStreamingBehavior) | | Gebruik [Improved](/docs/nl-nl/reference/engine/enums/ModelStreamingBehavior#Improved)  om de meest efficiënte streaming voor [Models](/docs/nl-nl/reference/engine/classes/Model)  met [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  afstammelingen in te schakelen. |
| [StreamingIntegrityMode](/docs/nl-nl/reference/engine/classes/Workspace#StreamingIntegrityMode) | | Gebruik [PauseOutsideLoadedArea](/docs/nl-nl/reference/engine/enums/StreamingIntegrityMode#PauseOutsideLoadedArea)  om de integriteit van het spel in balans te houden zonder onnodig of te vaak te pauzeren. |
| [StreamingMinRadius](/docs/nl-nl/reference/engine/classes/Workspace#StreamingMinRadius) | | Gebruik de standaardwaarde van 64  om te maximaliseren hoeveel de engine het spel kan verkleinen voor low-end apparaten. |
| [StreamingTargetRadius](/docs/nl-nl/reference/engine/classes/Workspace#StreamingTargetRadius) | | Gebruik de standaardwaarde van 1024  om een goede balans te vinden tussen zichtbaarheid voor spelers op high-end apparaten en een redelijke geheugendruk. |
| [StreamOutBehavior](/docs/nl-nl/reference/engine/classes/Workspace#StreamOutBehavior) | | Gebruik [Opportunistic](/docs/nl-nl/reference/engine/enums/StreamOutBehavior#Opportunistic)  om de client in staat te stellen om agressief ongebruikte inhoud te verwijderen, wat het geheugengebruik aanzienlijk vermindert en helpt om out-of-memory crashes te voorkomen. |

## [Model niveau van detail](#model-niveau-van-detail)[](#model-niveau-van-detail)

[Model.LevelOfDetail](/docs/nl-nl/reference/engine/classes/Model#LevelOfDetail)  helpt om niet-gestreamde [Model](/docs/nl-nl/reference/engine/classes/Model)  inhoud in te vullen met lichte composiet- of imposter-meshes, waardoor de wereld visueel compleet lijkt. [SLIM](/docs/nl-nl/workspace/streaming/slim)  (Scalable Lightweight Interactive Models) zijn bijzonder effectief, omdat spelers vaak niet kunnen onderscheiden of een SLIM-mesh de volledig gestreamde originele is.

Voor de beste resultaten:

-

Groepeer delen die ruimtelijk en logisch gerelateerd zijn, bijvoorbeeld alle delen van een auto.

-

Stel [LevelOfDetail](/docs/nl-nl/reference/engine/classes/Model#LevelOfDetail)  in op [SLIM](/docs/nl-nl/reference/engine/enums/ModelLevelOfDetail#SLIM)  voor modellen die statische  meshes en delen bevatten. Modellen die tijdens runtime worden gewijzigd of animaties afspelen worden niet ondersteund.

-

Houd de ruimtelijke omvang van elk model onder ~64 kubieke studs om de kans te vergroten dat het hele daadwerkelijke model samen wordt gestreamd. Als een model zeer grote afmetingen heeft, splits het dan op in kleinere modulaire modellen en pas een geschikte [LevelOfDetail](/docs/nl-nl/reference/engine/classes/Model#LevelOfDetail)  toe op elk model.

![](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/SLIM-Disabled.jpg)[Disabled](/docs/nl-nl/reference/engine/enums/ModelLevelOfDetail#Disabled) /[Automatic](/docs/nl-nl/reference/engine/enums/ModelLevelOfDetail#Automatic)

![](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/SLIM-Enabled.jpg)[SLIM](/docs/nl-nl/reference/engine/enums/ModelLevelOfDetail#SLIM)

## [Modelstructuur](#modelstructuur)[](#modelstructuur)

Naast het instellen van [model niveau van detail](#model-niveau-van-detail) , heeft de structuur en instellingen van je [Models](/docs/nl-nl/reference/engine/classes/Model)  een significante impact op hoe goed streaming presteert. Terwijl je een bestaand spel bouwt of converteert:

-

Gebruik atomische modellen voor logische groepering  — Wanneer een script toegang nodig heeft tot alle delen binnen een model, stel je de [ModelStreamingMode](/docs/nl-nl/reference/engine/classes/Model#ModelStreamingMode)  in op [Atomic](/docs/nl-nl/reference/engine/enums/ModelStreamingMode#Atomic) . Dit stelt client-side scripts in staat om veilig toegang te krijgen tot instanties binnen het model zonder overmatig gebruik van [WaitForChild()](/docs/nl-nl/reference/engine/classes/Instance#WaitForChild)  (hoewel dergelijke scripts nog steeds [WaitForChild()](/docs/nl-nl/reference/engine/classes/Instance#WaitForChild)  moeten gebruiken voor het algehele atomische model).

Atomiciteit garanties zijn alleen van toepassing tijdens de initiële replicatie. Zodra een atomisch model naar de client is gerepliceerd, worden alle nieuwe  instanties die onder dat model zijn toegevoegd niet  atomisch gerepliceerd en worden in plaats daarvan gestreamd volgens het normale [streaming gedrag](/docs/nl-nl/workspace/streaming#technisch-gedrag) . Systemen die dynamisch atomische modellen wijzigen, moeten laat binnenkomende instanties expliciet afhandelen waar nodig.

-

Minimaliseer persistente modellen  — [Persistente](/docs/nl-nl/workspace/streaming#persistent)  modellen laden na join en streamen nooit uit, waardoor ze permanent geheugen innemen. Stel de [ModelStreamingMode](/docs/nl-nl/reference/engine/classes/Model#ModelStreamingMode)  van een model in op [Persistent](/docs/nl-nl/reference/engine/enums/ModelStreamingMode#Persistent)  alleen als het moet  beschikbaar en toegankelijk zijn voor scripts op elk moment.

-

Decompositie van container modellen  — Een veelvoorkomend niet-streaming patroon is een enkel enorm [Model](/docs/nl-nl/reference/engine/classes/Model)  dat veel NPC's, props of vergelijkbare groeperingen bevat. Onder streaming verminderen container modellen de streaming efficiëntie en zijn ze niet optimaal voor [model niveau van detail](#model-niveau-van-detail)  dat het beste werkt met dicht bij elkaar gegroepeerde instanties. Decompose container modellen in kleinere modellen met fysiek dicht bij elkaar of logisch gerelateerde delen.

-

Vlak diep geneste modelhiërarchieën  — Het nestelen van een [persistente](/docs/nl-nl/workspace/streaming#persistent)  model binnen een [atomisch](/docs/nl-nl/workspace/streaming#atomisch)  model dwingt effectief het atomische model om zich als persistent te gedragen. Vlakke hiërarchieën zijn gemakkelijker te begrijpen onder streaming.

## [SLIM avatars](#slim-avatars)[](#slim-avatars)

Platform avatars buiten het momenteel gestreamde gebied zijn standaard niet zichtbaar, maar het inschakelen van [Workspace.EnableSLIMAvatars](/docs/nl-nl/reference/engine/classes/Workspace#EnableSLIMAvatars)  rendert R15 avatars als lichte, geanimeerde stand-ins wanneer dat gepast is. Effectief:

-

Rendert de engine een SLIM-versie wanneer een daadwerkelijk avatar model uitstreamt.

-

Wisselt tussen SLIM en full-resolution representaties op basis van beschikbare middelen, zelfs binnen de streamingradius.

-

Beperkt SLIM-animaties op basis van scene belangrijkheid en beschikbare bandbreedte.

SLIM avatars ondersteunen R15 spelerpersonages met een lichaam, dynamisch hoofd, [standaard](/docs/nl-nl/avatar/character-bodies/specifications#standaard-r15-rigs)  of [geavanceerd](/docs/nl-nl/avatar/character-bodies/specifications#geavanceerde-r15-rigs)  R15 rig, en rigide/gelaagde accessoires. R6 avatars, NPC's en avatars met aangepaste verhoudingen zijn uitgesloten. Voor de volledige lijst van ondersteunde en uitgesloten avatarconfiguraties, prestatiegegevens en probleemoplossingstips, zie [SLIM avatars](/docs/nl-nl/workspace/streaming/slim#enabling-slim-for-avatars) .

## [Script patronen](#script-patronen)[](#script-patronen)

De volgende script patronen worden het meest beïnvloed door streaming. De juiste strategie hangt af van de intentie van de code, dus elk patroon vermeldt meerdere opties waar dat gepast is.

### [Directe index naar afstammelingen](#directe-index-naar-afstammelingen)[](#directe-index-naar-afstammelingen)

Indexeren in [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  afstammelingen met de .  operator gooit een fout als een instantie in het pad momenteel niet is gestreamd. Hetzelfde geldt voor [FindFirstChild()](/docs/nl-nl/reference/engine/classes/Instance#FindFirstChild) , [FindFirstChildWhichIsA()](/docs/nl-nl/reference/engine/classes/Instance#FindFirstChildWhichIsA)  en [FindFirstChildOfClass()](/docs/nl-nl/reference/engine/classes/Instance#FindFirstChildOfClass)  die nil  retourneren als het kind niet is gestreamd.

Afstammeling Lookup

```

local house1 = workspace:FindFirstChild("House1") -- nil als "House1" niet is gestreamd

local door = workspace.House1.Door -- Gebroken als "House1" of "Door" niet is gestreamd

```

Een vergelijkbaar patroon is het direct benaderen van de [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  of andere karakterafstammelingen binnen een [Player.CharacterAdded](/docs/nl-nl/reference/engine/classes/Player#CharacterAdded)  verbinding. Onder streaming is het karaktermodel aan [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  gekoppeld voordat al zijn afstammelingen zijn gerepliceerd, dus directe indexering faalt.

Karakter Afstammelingen

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

player.CharacterAdded:Connect(function(character)

	local humanoid = character.Humanoid

end)

```

Strategie #1 Strategie #2 Strategie #3

Als het script geen vooruitgang kan boeken zonder een instantie, wacht er dan op met [WaitForChild()](/docs/nl-nl/reference/engine/classes/Instance#WaitForChild) :

Afstammeling Lookup

```

local house1 = workspace:WaitForChild("House1")

local door = house1:WaitForChild("Door")

```

### [Instanties die op afstand worden verzonden](#instanties-die-op-afstand-worden-verzonden)[](#instanties-die-op-afstand-worden-verzonden)

Een [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent) /[RemoteFunction](/docs/nl-nl/reference/engine/classes/RemoteFunction)  signaal en de instantie waarnaar het verwijst, reizen onafhankelijk, zodat het signaal op de client kan aankomen voordat de instantie aanwezig is — of de instantie is misschien helemaal niet aanwezig. Twee waarschijnlijke oorzaken zijn:

-

Onder streaming kan er een kleine vertraging zijn tussen wanneer een deel/model op de server wordt gemaakt en wanneer het naar clients wordt gerepliceerd. Effectief kan een deel dat door een [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent) /[RemoteFunction](/docs/nl-nl/reference/engine/classes/RemoteFunction)  wordt verwezen, simpelweg nog niet bestaan, zelfs niet binnen een gestreamd gebied.

-

Het verzenden van een deel/model referentie van server naar client via een [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  of [RemoteFunction](/docs/nl-nl/reference/engine/classes/RemoteFunction)  vereist dat de instantie naar de ontvangende client is gerepliceerd. Het verzenden van een instantiepad als een string heeft hetzelfde probleem, omdat het pad kan verwijzen naar een niet-bestaande locatie op de client:

Client Script

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

remoteEvent.OnClientEvent:Connect(function(data)

	local checkpoint = data.checkpoint -- Fouten als "checkpoint" niet is gestreamd

	local level = workspace.Levels[data.levelPath] -- Fouten als pad niet is gestreamd

end)

```

Strategie #1 Strategie #2 Strategie #3

Als het ontvangende clientscript de instantie nodig heeft om verder te gaan, voeg dan [WaitForChild()](/docs/nl-nl/reference/engine/classes/Instance#WaitForChild)  toe voordat je het gebruikt. Merk op dat dit oneindig kan wachten als de instantie nooit wordt gestreamd, dus overweeg om een time-out toe te voegen als de tweede parameter van [WaitForChild()](/docs/nl-nl/reference/engine/classes/Instance#WaitForChild) .

### [Client desynchronisatie](#client-desynchronisatie)[](#client-desynchronisatie)

Client-side desynchronisatie moet worden behandeld als een uitzondering, niet als een standaard ontwerppatroon. Het introduceren van client-only kopieën of het lokaal herplaatsen van instanties kan ernstige problemen veroorzaken. Controleer je code op plaatsen die afhankelijk zijn van deze soorten wijzigingen die op de client blijven bestaan.

Bijvoorbeeld, het lokaal herplaatsen van een instantie van [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  naar [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  kan die instantie in aanmerking brengen om uit te streamen. Evenzo, het lokaal klonen van een instantie ([Instance:Clone()](/docs/nl-nl/reference/engine/classes/Instance#Clone) ) van [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  naar [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  creëert een client-only kopie die niet langer deel uitmaakt van de server replicatiepijplijn en geen eigenschapsupdates van de originele server-eigen instantie zal ontvangen.

Hetzelfde concept geldt wanneer je [Instance:Destroy()](/docs/nl-nl/reference/engine/classes/Instance#Destroy)  op de client aanroept voor een server-eigen object. Dit verwijdert de instantie lokaal, maar de server heeft deze nog steeds, dus deze zal opnieuw worden gestreamd met zijn oorspronkelijke staat wanneer dat mogelijk is.

### [Proactieve streaming](#proactieve-streaming)[](#proactieve-streaming)

Wanneer de volgende bestemming van een speler kan worden voorspeld, maak dan server-side aanroepen naar [Player:RequestStreamAroundAsync()](/docs/nl-nl/reference/engine/classes/Player#RequestStreamAroundAsync)  om tijdelijke gebieden voor tijdelijke laadtijd te streamen, of gebruik [Player:AddReplicationFocus()](/docs/nl-nl/reference/engine/classes/Player#AddReplicationFocus)  op een beperkte  basis voor gebieden die geladen moeten blijven totdat ze expliciet worden vrijgegeven.

Bijvoorbeeld, wanneer een speler karakter op het punt staat te teleporteren door een [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  wijziging naar het huis van een andere speler op een verre locatie, kun je het bestemmingsgebied vooraf ophalen om pop-in te minimaliseren en een soepelere overgang te bieden. Het volgende script toont hoe een client-naar-server [remote event](/docs/nl-nl/scripting/events/remote)  kan worden afgevuurd om een speler karakter te verplaatsen met een vooraf ophalen methode. Als het vooraf ophalen verzoek succesvol is wanneer de functie retourneert, zou de minimale straal rond de doel locatie aanwezig moeten zijn op de client.

Server Script - Teleporteer Speler Karakter

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local teleportEvent = ReplicatedStorage:WaitForChild("TeleportEvent")

local function teleportPlayer(player, teleportTarget)

	-- Vraag streaming aan rond de doel locatie

	player:RequestStreamAroundAsync(teleportTarget)

	-- Teleporteer karakter

	local character = player.Character

	if character and character.Parent then

		local currentPivot = character:GetPivot()

		character:PivotTo(currentPivot * CFrame.new(teleportTarget))

	end

end

-- Roep teleport functie aan wanneer de client het remote event afvuurt

teleportEvent.OnServerEvent:Connect(teleportPlayer)

```

### [Instantie-eigenschap lezen](#instantie-eigenschap-lezen)[](#instantie-eigenschap-lezen)

Zodra een instantie uitstreamt, worden de eigenschapsupdates niet langer gerepliceerd naar die client. Het lezen van eigenschappen zoals [BasePart.Position](/docs/nl-nl/reference/engine/classes/BasePart#Position)  blijft succesvol, maar retourneert de laatst gerepliceerde waarde die willekeurig verouderd kan zijn.

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

-- Positie kan verouderd zijn als "target" is gestreamd

local dist = (target.Position - player.Character.HumanoidRootPart.Position).Magnitude

```

Strategie #1 Strategie #2 Strategie #3

Verplaats de logica naar de server, aangezien server-side scripts alle instanties op elk moment zien. Dit is over het algemeen de meest betrouwbare optie voor afstandscontroles en andere positiegevoelige logica.

### [Wachten op het kritieke pad](#wachten-op-het-kritieke-pad)[](#wachten-op-het-kritieke-pad)

Sommige niet-streaming spellen laden hun kaart door deze te klonen van [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  naar [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) , en wachten vervolgens op de client voordat ze een laadscreen afschaffen en gereedheid signaleren. Onder streaming blijft dit oneindig hangen — het karakter van de client is nog niet gespawned, dus er is geen [replicatiefocus](/docs/nl-nl/workspace/streaming#replicatiefocus) , en de ruimtelijke kaart instantie streamt nooit in.

Strategie #1 Strategie #2

Verplaats de laadscreen logica zodat deze niet afhankelijk is van een specifieke ruimtelijke instantie die aanwezig is, bijvoorbeeld door gereedheid te signaleren zodra het karakter is gespawned en het onmiddellijke omringende gebied is gestreamd.

### [Signaalverandering afhandeling](#signaalverandering-afhandeling)[](#signaalverandering-afhandeling)

Signalen zoals [Instance.ChildAdded](/docs/nl-nl/reference/engine/classes/Instance#ChildAdded) /[Instance.ChildRemoved](/docs/nl-nl/reference/engine/classes/Instance#ChildRemoved)  en [CollectionService](/docs/nl-nl/reference/engine/classes/CollectionService)  signalen zoals [GetInstanceAddedSignal()](/docs/nl-nl/reference/engine/classes/CollectionService#GetInstanceAddedSignal)  of [GetInstanceRemovedSignal()](/docs/nl-nl/reference/engine/classes/CollectionService#GetInstanceRemovedSignal)  worden ook geactiveerd bij stream in/uit, ononderscheidbaar van echte spawns/verwijderingen. Ontvangende scripts kunnen het verschil niet alleen aan het signaal vertellen, dus logica die aanneemt dat een signaal overeenkomt met een "echte" gebeurtenis moet worden bijgewerkt.

Strategie #1 Strategie #2

Controleer scripts op eventuele signaallisteners die kunnen breken of aanzienlijk kunnen veranderen wanneer ze worden geactiveerd door stream in en/of stream uit. Bijvoorbeeld, als je audio of visuele effecten afspeelt wanneer een vijand NPC aanvankelijk in de wereld spawnt, wijs dan elke vijand een [attribuut](/docs/nl-nl/studio/properties#instantie-attributen)  zoals Spawned  toe bij de eerste spawn, en sla het opnieuw afspelen van dezelfde audio/effecten over bij toekomstige stream-ins van de vijand.

Attribuut Tracking

```

local CollectionService = game:GetService("CollectionService")

local TAG_NAME = "Enemy"

CollectionService:GetInstanceAddedSignal(TAG_NAME):Connect(function(enemy)

	if not enemy:GetAttribute("Spawned") then

		-- Stel "Spawned" attribuut in op vijand voor initiële spawn

		enemy:SetAttribute("Spawned", true)

		-- Speel audio/visuele effecten af voor deze initiële spawn

		playSpawnEffects(enemy)

	end

end)

```

### [Iteratie over collecties](#iteratie-over-collecties)[](#iteratie-over-collecties)

Client-side collectie iteraties zoals [Instance:GetChildren()](/docs/nl-nl/reference/engine/classes/Instance#GetChildren)  en [Instance:GetDescendants()](/docs/nl-nl/reference/engine/classes/Instance#GetDescendants)  retourneren alleen de gestreamde subset van afstammelingen. Dit geldt zelfs wanneer de ouder zelf altijd wordt gerepliceerd, zoals een [Folder](/docs/nl-nl/reference/engine/classes/Folder)  direct onder [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  waarvan de ruimtelijke afstammelingen in en uit streamen.

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

-- Map "Homes" is altijd gerepliceerd maar zijn kinderen streamen in en uit

-- Deze lus kan huizen missen die momenteel niet zijn gestreamd

for _, home in workspace.Homes:GetChildren() do

	if home.Settings.Owner.Value == player.Name then

		return home

	end

end

```

Strategie #1 Strategie #2 Strategie #3

Als een volledige enumeratie vereist is, voer dan de scan op de server uit en geef het resultaat door aan de speler via een [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  indien nodig.

### [Ruimtelijke queries](#ruimtelijke-queries)[](#ruimtelijke-queries)

Client-side ruimtelijke queries zoals [WorldRoot:Raycast()](/docs/nl-nl/reference/engine/classes/WorldRoot#Raycast) , [WorldRoot:GetPartBoundsInBox()](/docs/nl-nl/reference/engine/classes/WorldRoot#GetPartBoundsInBox) , en [Model:GetBoundingBox()](/docs/nl-nl/reference/engine/classes/Model#GetBoundingBox)  weerspiegelen alleen gestreamde inhoud. Of dat een probleem is, hangt af van waar de query voor wordt gebruikt.

Strategie #1 Strategie #2 Strategie #3 Strategie #4

Gebruik de server voor queries waarvan het resultaat de volledige wereld moet weerspiegelen, bijvoorbeeld een raycast die controleert of de speler zicht heeft op een verre doel.

### [Andere patronen](#andere-patronen)[](#andere-patronen)

De volgende patronen kunnen ook van toepassing zijn en moeten zorgvuldig worden overwogen:

-

Een [Sound](/docs/nl-nl/reference/engine/classes/Sound)  of [AudioPlayer](/docs/nl-nl/reference/engine/classes/AudioPlayer)  die aan een 3D-object is gekoppeld, stopt wanneer dat object uitstreamt. Voor ambient audio die moet blijven bestaan, koppel de emitter aan een [persistente](/docs/nl-nl/workspace/streaming#persistent)  model of aan een niet-streaming container.

-

In-game [UI](/docs/nl-nl/ui/in-experience-containers)  objecten zoals [BillboardGui](/docs/nl-nl/reference/engine/classes/BillboardGui)  of [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui)  evenals [visuele effecten](/docs/nl-nl/effects)  zoals [Beams](/docs/nl-nl/reference/engine/classes/Beam)  of [Highlights](/docs/nl-nl/reference/engine/classes/Highlight)  waarvan de adornee of bevestiging uitstreamt, stoppen gewoon met renderen. Dit kan het beoogde gedrag zijn, maar je moet het verifiëren.

-

[BasePart.Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched)  evenementen, [ProximityPrompts](/docs/nl-nl/reference/engine/classes/ProximityPrompt) , [DragDetectors](/docs/nl-nl/reference/engine/classes/DragDetector) , en [ClickDetectors](/docs/nl-nl/reference/engine/classes/ClickDetector)  werken niet voor spelers wiens client het bijbehorende deel/model niet heeft gestreamd. Als interactie mogelijk moet zijn vanuit elke afstand, moet het model [persistent](/docs/nl-nl/workspace/streaming#persistent)  zijn of moet de interactie een ander mechanisme hebben.

-

Voor [PathfindingService](/docs/nl-nl/reference/engine/classes/PathfindingService)  en client-side padfinding, ziet de padvinder alleen gestreamde geometrie op de client en kan het door obstakels routeren die op de server bestaan. Voor strategieën, zie [Pathfinding - Strategieën](/docs/nl-nl/characters/pathfinding#streamingcompatibiliteit)  voor strategieën.

## [Realistische testomstandigheden](#realistische-testomstandigheden)[](#realistische-testomstandigheden)

Zodra [scripts zijn bijgewerkt](#script-patronen) , test het spel grondig. Streaming bugs manifesteren zich vaak alleen aan de randen van het gestreamde gebied of tijdens overgangen, dus alleen testen nabij spawn of op doelradius is niet voldoende.

-

Test met [Workspace.StreamingTargetRadius](/docs/nl-nl/reference/engine/classes/Workspace#StreamingTargetRadius)  ingesteld op de minimale waarde (64 ). Sommige streaming bugs verschijnen alleen wanneer het gestreamde gebied klein is.

-

Speel door de volledige traversiepatronen van het spel, teleport tussen verre gebieden, en bezoek gebieden opnieuw nadat je ze hebt verlaten. Dit zijn de situaties die het meest gebruik maken van stream in en stream uit.

-

Gebruik de [streaming debug overlay](/docs/nl-nl/workspace/streaming#runtime-debugging)  om de actieve streaminginstellingen, momenteel geladen regio's en runtime streamingstatus te monitoren.

-

Kijk naar het [Output](/docs/nl-nl/studio/output)  venster en de [Developer Console](/docs/nl-nl/studio/developer-console)  voor fouten, aangezien veel van de [script patronen](#script-patronen)  fouten produceren in plaats van stille misgedragingen. Let vooral op fouten van de vorm attempt to index nil with ...  die vaak wijzen op een ontbrekende [WaitForChild()](/docs/nl-nl/reference/engine/classes/Instance#WaitForChild)  aanroep.

-

Equip en activeer [Tools](/docs/nl-nl/reference/engine/classes/Tool) , vuurt wapens af en activeer verschillende game-interacties.

## [AI streaming conversie vaardigheid](#ai-streaming-conversie-vaardigheid)[](#ai-streaming-conversie-vaardigheid)

Om te helpen bij streaming conversie en optimalisatie, biedt Roblox een AI streaming vaardigheid  die je spel evalueert, aanbevolen configuraties toepast en compatibiliteitsproblemen oplost, inclusief:

Model & Wereld Aanpassingen Script & Replicatie Fixes Ingebouwde Guardrails

-

Configureert streaminginstellingen naar de [aanbevolen basislijnen](#streaming-eigenschappen) .

-

Stelt [niveau van detail](#model-niveau-van-detail)  voor modellen in op [SLIM](/docs/nl-nl/workspace/streaming/slim)  waar van toepassing.

-

Refactoriseert [modelstructuren](#modelstructuur)  om optimale groottes en visuele kwaliteit te bereiken.

Zelfs als je spel al gebruik maakt van streaming, zal de vaardigheid je bestaande setup scannen, potentiële problemen of verbeterpunten identificeren en automatisch fixes toepassen om het verder te optimaliseren.

Om de AI vaardigheid in je spel te gebruiken:

1.

BELANGRIJK

 Maak een back-up van je spel. Het conversieproces kan complex zijn, dus je moet altijd  een back-up opslaan (Bestand  ⟩ Publiceer naar Roblox Als ) voordat je de vaardigheid uitvoert.

2.

Je kunt deze vaardigheid rechtstreeks in Assistant uitvoeren of met behulp van een LLM naar keuze via het [Model Context Protocol (MCP)](/docs/nl-nl/studio/mcp)  in Studio. Hogere AI-modellen met grote contextvensters worden aanbevolen; voor een typische conversie kan een frontier-model 20-30 minuten duren en ongeveer 200.000 tokens aan context gebruiken.

1.

[Schakel de MCP-server in Studio in en verbind deze](/docs/nl-nl/studio/mcp) .

2.

Open je spel in Studio.

3.

Open Assistant Instellingen  ⟩ Vaardigheden  en zorg ervoor dat rbx-convert-to-streaming  is ingeschakeld.

4.

Vraag Assistant (of je LLM verbonden via MCP) om de vaardigheid te gebruiken.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
