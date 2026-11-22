<!-- Source: https://create.roblox.com/docs/nl-nl/workspace/collisions -->

Botsingen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)
6. /
7. Ruimtelijke gegevens

# Botsingen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een botsing vindt plaats wanneer twee 3D-objecten contact maken binnen de 3D-wereld. Voor aangepaste botsingsverwerking heeft [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  een set van [botsingsevents](#botsingsevents)  en [botsingsfiltering](#botsingsfiltering)  technieken, zodat je kunt bepalen welke fysieke assemblages met elkaar botsen.

## [Botsingsevents](#botsingsevents)[](#botsingsevents)

Botsing events  vinden plaats wanneer twee [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  elkaar aanraken of stoppen met aanraken in de 3D-wereld. Je kunt deze botsingen detecteren via de [Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched)  en [TouchEnded](/docs/nl-nl/reference/engine/classes/BasePart#TouchEnded)  events die plaatsvinden, ongeacht de waarde van de [CanCollide](/docs/nl-nl/reference/engine/classes/BasePart#CanCollide)  eigenschap van elk onderdeel. Houd bij het overwegen van botsingsverwerking op onderdelen het volgende in gedachten:

-

De [CanTouch](/docs/nl-nl/reference/engine/classes/BasePart#CanTouch)  eigenschap van een onderdeel bepaalt of het botsingsevents activeert. Als deze is ingesteld op false , zullen noch [Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched)  noch [TouchEnded](/docs/nl-nl/reference/engine/classes/BasePart#TouchEnded)  worden geactiveerd.

-

De [CanCollide](/docs/nl-nl/reference/engine/classes/BasePart#CanCollide)  eigenschap van een onderdeel beïnvloedt of het fysiek  zal botsen met andere onderdelen en krachten op hen zal uitoefenen. Zelfs als [CanCollide](/docs/nl-nl/reference/engine/classes/BasePart#CanCollide)  is uitgeschakeld voor een onderdeel, kun je aanraking en niet-aanraking detecteren via de [Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched)  en [TouchEnded](/docs/nl-nl/reference/engine/classes/BasePart#TouchEnded)  events.

-

De [Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched)  en [TouchEnded](/docs/nl-nl/reference/engine/classes/BasePart#TouchEnded)  events worden alleen geactiveerd als gevolg van fysieke  beweging, niet van een [Position](/docs/nl-nl/reference/engine/classes/BasePart#Position)  of [CFrame](/docs/nl-nl/reference/engine/classes/BasePart#CFrame)  wijzigingen die ervoor zorgen dat een onderdeel een ander onderdeel doorkruist of stopt met doorkruisen.

-

De top-level [Terrain](/docs/nl-nl/reference/engine/classes/Terrain)  klasse erft van [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) , zodat je een [botsingsgroep](#botsingsgroepen)  aan [Terrain](/docs/nl-nl/reference/engine/classes/Terrain)  kunt toewijzen om te bepalen of andere [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  met [Terrain](/docs/nl-nl/parts/terrain)  voxels botsen.

Voor prestatieoptimalisatie, stel [CanTouch](/docs/nl-nl/reference/engine/classes/BasePart#CanTouch)  in op false  voor objecten die geen botsingen vereisen.

### [Aangeraakt](#aangeraakt)[](#aangeraakt)

Het [Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched)  event wordt geactiveerd wanneer een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  in contact komt met een ander, of met een [Terrain](/docs/nl-nl/parts/terrain)  voxel. Het wordt alleen geactiveerd als gevolg van fysieke simulatie  en zal niet worden geactiveerd wanneer de [Position](/docs/nl-nl/reference/engine/classes/BasePart#Position)  of [CFrame](/docs/nl-nl/reference/engine/classes/BasePart#CFrame)  van het onderdeel expliciet is ingesteld zodat het een ander onderdeel of voxel doorkruist.

Het volgende codepatroon toont hoe het [Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched)  event kan worden verbonden met een aangepaste onTouched()  functie. Merk op dat het event het otherPart  argument naar de functie verzendt, wat het andere onderdeel aangeeft dat betrokken is bij de botsing.

Deel Botsing

```

local part = workspace.Part

local function onTouched(otherPart)

	print(part.Name .. " botste tegen " .. otherPart.Name)

end

part.Touched:Connect(onTouched)

```

Merk op dat het [Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched)  event meerdere keren snel achter elkaar kan worden geactiveerd op basis van subtiele fysieke botsingen, zoals wanneer een bewegend object "tot rust komt" in een rustpositie of wanneer een botsing een [multi-part model](#modelbotsingen)  betreft. Om te voorkomen dat er meer [Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched)  events worden geactiveerd dan nodig, kun je een eenvoudig debounce-systeem implementeren dat een "cooldown"-periode afdwingt via een instantie [attribuut](/docs/nl-nl/studio/properties#instantie-attributen) .

Deel Botsing Met Cooldown

```

local part = workspace.Part

local COOLDOWN_TIME = 1

local function onTouched(otherPart)

	if not part:GetAttribute("Touched") then

		print(part.Name .. " botste tegen " .. otherPart.Name)

		part:SetAttribute("Touched", true)  -- Stel attribuut in op true

		task.wait(COOLDOWN_TIME)  -- Wacht op cooldown duur

		part:SetAttribute("Touched", false)  -- Reset attribuut

	end

end

part.Touched:Connect(onTouched)

```

### [TouchEnded](#touchended)[](#touchended)

Het [TouchEnded](/docs/nl-nl/reference/engine/classes/BasePart#TouchEnded)  event wordt geactiveerd wanneer de gehele botsingsgrenzen van een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  de grenzen van een ander [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  of een gevulde [Terrain](/docs/nl-nl/parts/terrain)  voxel verlaat. Het wordt alleen geactiveerd als gevolg van fysieke simulatie  en zal niet worden geactiveerd wanneer de [Position](/docs/nl-nl/reference/engine/classes/BasePart#Position)  of [CFrame](/docs/nl-nl/reference/engine/classes/BasePart#CFrame)  van het onderdeel expliciet is ingesteld zodat het stopt met doorkruisen van een ander onderdeel of voxel.

Het volgende codepatroon toont hoe het [TouchEnded](/docs/nl-nl/reference/engine/classes/BasePart#TouchEnded)  event kan worden verbonden met een aangepaste onTouchEnded()  functie. Net als bij [Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched) , verzendt het event het otherPart  argument naar de functie, wat het andere onderdeel aangeeft dat betrokken is.

Niet-Botsing Detectie

```

local part = workspace.Part

local function onTouchEnded(otherPart)

	print(part.Name .. " raakt niet langer " .. otherPart.Name aan)

end

part.TouchEnded:Connect(onTouchEnded)

```

### [Botsingssamenvattingen](#botsingssamenvattingen)[](#botsingssamenvattingen)

[Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched)  vertelt je dat  er een botsing heeft plaatsgevonden, maar niet waar het is gebeurd, uit welke richting het kwam, of hoe hard het was. Voor gedetailleerde contactgegevens van de fysica-engine, roep je [BindToCollisionSummaries()](/docs/nl-nl/reference/engine/classes/BasePart#BindToCollisionSummaries)  aan op een onderdeel. Het neemt een callback en retourneert een [RBXScriptConnection](/docs/nl-nl/reference/engine/datatypes/RBXScriptConnection)  die je kunt loskoppelen wanneer je de gegevens niet langer nodig hebt. Dit is een aparte API van [Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched) , dus roep het niet aan vanuit een [Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched)  handler.

De callback wordt eenmaal per frame uitgevoerd, nadat de fysica-stap is voltooid. Het ontvangt een tabel met een samenvatting van elke botsing waarbij het onderdeel betrokken was tijdens dat frame. Elke samenvatting beschrijft één contactpatch tussen het geabonneerde onderdeel en een ander onderdeel. Samenvattingen zijn bevroren en kunnen niet worden gewijzigd. Elke heeft deze velden:

| Veld | | Type | | Beschrijving |
| --- | --- |
| Time | | number | | Simulatietijd van de substap. |
| Part0 | | [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) | | Het geabonneerde onderdeel. |
| Part1 | | [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) | | Het andere onderdeel in het paar. |
| Point | | [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) | | Gemiddeld contactpunt, in wereldruimte. |
| Normal | | [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) | | Eenheidsnormaal. Het wijst altijd weg van Part0 . |
| RelativeVelocity | | [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) | | Snelheid van Part1  ten opzichte van Part0  op het contactpunt, gemeten voordat de oplosser de botsing oplost. |
| Area | | number | | Geschatte oppervlakte van de contactpatch. |

Om de frontale impact snelheid te krijgen, neem je het scalair product van RelativeVelocity  en Normal . Om glijdende botsingen of schuiven te detecteren, gebruik je de tangentiële component van RelativeVelocity . Als je een waarde wilt die dichter bij een kracht ligt, combineer dan de snelheid met de [AssemblyMass](/docs/nl-nl/reference/engine/classes/BasePart#AssemblyMass)  van de onderdelen.

Impact-gebaseerde effecten

```

local part = workspace.Part

local function onCollision(summaries)

	for _, summary in summaries do

		local impactSpeed = summary.RelativeVelocity:Dot(summary.Normal)

		if impactSpeed > 10 then

			print("Harde impact bij", summary.Point, "met snelheid", impactSpeed)

		end

	end

end

local connection = part:BindToCollisionSummaries(onCollision)

-- Later, wanneer je de samenvattingen niet langer nodig hebt

connection:Disconnect()

```

Houd het volgende in gedachten wanneer je botsingssamenvattingen gebruikt:

-

Samenvattingen worden alleen gegenereerd op de [netwerk eigenaar](/docs/nl-nl/physics/network-ownership)  die de fysica-simulatie uitvoert, wat een client of de server kan zijn. Ze worden niet gerepliceerd. Als andere clients op de hoogte moeten zijn van een botsing, verwerk dan de samenvatting en stuur alleen de gegevens die ze nodig hebben via je eigen [remote event](/docs/nl-nl/scripting/events/remote) .

-

Onderdelen met [CanCollide](/docs/nl-nl/reference/engine/classes/BasePart#CanCollide)  ingesteld op false  produceren geen botsingssamenvattingen.

-

Complexe niet-convexe onderdelen kunnen meer dan één samenvatting voor hetzelfde paar onderdelen produceren.

-

Contacten tussen twee slapende onderdelen worden niet geregistreerd.

-

De verwerkingskosten groeien met het aantal geabonneerde onderdelen, niet met het totale aantal botsingen in de plaats.

## [Botsingsfiltering](#botsingsfiltering)[](#botsingsfiltering)

Botsing filtering  definieert welke fysieke onderdelen met elkaar botsen. Je kunt filtering configureren voor talrijke objecten via [botsingsgroepen](#botsingsgroepen)  of je kunt botsingen op een [deel-tot-deel](#deel-tot-deel-filtering)  basis regelen met [NoCollisionConstraint](/docs/nl-nl/reference/engine/classes/NoCollisionConstraint)  instanties.

### [Botsingsgroepen](#botsingsgroepen)[](#botsingsgroepen)

Botsing groepen  stellen je in staat om [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  aan specifieke groepen toe te wijzen en te specificeren of ze al dan niet botsen met die in andere groepen. Onderdelen binnen niet-botsende groepen passeren elkaar volledig, zelfs als beide onderdelen hun [CanCollide](/docs/nl-nl/reference/engine/classes/BasePart#CanCollide)  eigenschap op true  hebben ingesteld. Botsingsgroepen worden gemaakt en geconfigureerd op basis van [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  of [WorldModel](/docs/nl-nl/reference/engine/classes/WorldModel) .

In de bovenstaande video bevinden de draaiende objecten zich in verschillende botsingsgroepen zodat ze botsen met objecten van een andere kleur, maar niet met objecten van hun eigen kleur

Je kunt botsingsgroepen eenvoudig instellen via de Botsingsgroepen  editor van Studio, toegankelijk via het Venster  ⟩ 3D  menu.

#### [Groepen registreren](#groepen-registreren)[](#groepen-registreren)

[Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  slaat zijn eigen configureerbare staat van botsingsgroepen op. Bovendien kan elke [WorldModel](/docs/nl-nl/reference/engine/classes/WorldModel)  ervoor kiezen om zijn eigen botsingsgroepen te gebruiken voor queries.

Studio Editor Scripting

De editor bevat één Standaard  botsingsgroep die niet kan worden hernoemd of verwijderd. Alle [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  behoren automatisch tot deze standaardgroep, tenzij ze aan een andere groep zijn toegewezen, wat betekent dat ze met alle andere objecten in de Standaard  groep zullen botsen.

Om een nieuwe botsingsgroep te maken:

1.

Standaard worden groepen geregistreerd op [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) , maar als je ten minste één [WorldModel](/docs/nl-nl/reference/engine/classes/WorldModel)  in je plaats hebt, verschijnt er een keuzedropdown bovenaan de botsingsgroepeneditor. Gebruik de dropdown om botsingsgroepen over verschillende [WorldModel](/docs/nl-nl/reference/engine/classes/WorldModel)  instanties te configureren.

 ![Workspace aangegeven als de momenteel actieve wereld van de botsingsgroepeditor](https://prod.docsiteassets.roblox.com/assets/studio/collision-groups-editor/Active-World-Dropdown.png)

Voor elke [WorldModel](/docs/nl-nl/reference/engine/classes/WorldModel)  kun je Gebruik Workspace-botsingsgroepen  inschakelen om het te laten gebruik maken van [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  botsingsgroepen voor zijn queries.

 ![Checkbox aangegeven om de UseWorkspaceCollisionGroups eigenschap van een WorldModel in te schakelen](https://prod.docsiteassets.roblox.com/assets/studio/collision-groups-editor/WorldModel-Use-Workspace-Collision-Groups.png)

2.

Klik op de Groep Toevoegen  knop bovenaan het editorpaneel, voer een nieuwe groepsnaam in en druk op Enter . De nieuwe groep verschijnt in beide kolommen van de lijstweergave, of in zowel de linkerkolom als de bovenste rij van de tabelweergave.

Lijstweergave Tabelweergave

![Nieuwe groep toegevoegd aan de Botsingsgroepeneditor in Lijstweergave](https://prod.docsiteassets.roblox.com/assets/studio/collision-groups-editor/New-Group-List-View.png)

3.

Herhaal het proces indien nodig, kies een unieke en beschrijvende naam voor elke groep. Merk op dat je de naam van een groep tijdens de ontwikkeling kunt wijzigen door in het veld te klikken, of door deze te selecteren en op de hernoemen  knop te klikken.

 ![Knop en veld aangegeven voor het hernoemen van een groep in de Botsingsgroepeneditor](https://prod.docsiteassets.roblox.com/assets/studio/collision-groups-editor/Rename-Group.png)

#### [Groepsbotsingen configureren](#groepsbotsingen-configureren)[](#groepsbotsingen-configureren)

Studio Editor Scripting

Onder standaardconfiguratie botsen objecten in alle groepen met elkaar. Om te voorkomen dat objecten in één groep botsen met objecten in een andere groep, vink  het vakje in de respectieve rij/kolom uit.

In het volgende voorbeeld zullen objecten in de Cubes  groep niet  botsen met objecten in de Doors  groep.

Lijstweergave Tabelweergave

![Groep geconfigureerd in Lijstweergave van de Botsingsgroepeneditor](https://prod.docsiteassets.roblox.com/assets/studio/collision-groups-editor/Configure-Groups-List-View.png)

#### [Objecten aan groepen toewijzen](#objecten-aan-groepen-toewijzen)[](#objecten-aan-groepen-toewijzen)

Studio Editor Scripting

Om objecten toe te wijzen aan groepen die je hebt [geregistreerd](#groepen-registreren)  via de Studio-editor:

1.

Selecteer een of meer [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  die kwalificeren als onderdeel van een botsingsgroep.

2.

Wijs ze toe aan de groep door op de ⊕  knop voor de rij te klikken. Objecten kunnen slechts tot één botsingsgroep tegelijk behoren, dus ze in een nieuwe groep plaatsen verwijdert ze uit hun huidige groep.

 ![Plusknop aangegeven in de Botsingsgroepeneditor voor het toevoegen van geselecteerde onderdelen aan een groep](https://prod.docsiteassets.roblox.com/assets/studio/collision-groups-editor/Add-To-Group.png)

Zodra toegewezen, wordt de nieuwe groep weergegeven onder de [CollisionGroup](/docs/nl-nl/reference/engine/classes/BasePart#CollisionGroup)  eigenschap van het object.

 ![Gekozen botsingsgroep aangegeven als de CollisionGroup eigenschap van het onderdeel](https://prod.docsiteassets.roblox.com/assets/physics/collisions/BasePart-CollisionGroup.png)

#### [StudioSelectable groep](#studioselectable-groep)[](#studioselectable-groep)

Tools in Studio gebruiken het botsingsfilteringssysteem om te bepalen welke objecten kandidaten zijn voor selectie bij het klikken in de 3D-weergave. Objecten waarvan de toegewezen botsingsgroep niet  botst met StudioSelectable  worden genegeerd.

Als je bijvoorbeeld checkpoints hebt in een racegame waarvan de effectieve gebieden zijn gedefinieerd door grote transparante onderdelen, kun je ze toewijzen aan een Checkpoints  botsingsgroep en die groep vervolgens niet-botsbaar maken met StudioSelectable  zodat ze niet in de weg staan tijdens het bewerken van de onderliggende kaartgeometrie.

 ![Checkpoints groep geconfigureerd om niet-botsbaar te zijn met de StudioSelectable groep](https://prod.docsiteassets.roblox.com/assets/studio/collision-groups-editor/StudioSelectable-Off.png)

Voor plugin-code is het aan te raden om "StudioSelectable"  als het botsingsgroepfilter van je [RaycastParams](/docs/nl-nl/reference/engine/datatypes/RaycastParams)  toe te wijzen bij het vinden van onderdelen onder de cursor. Dit stelt je plugins in staat om overeen te komen met de selectiemechanica die makers hebben geleerd te verwachten van ingebouwde Studio-tools.

Aanbevolen Plugin Selectie Raycast

```

local UserInputService = game:GetService("UserInputService")

local raycastParams = RaycastParams.new()

raycastParams.CollisionGroup = "StudioSelectable"  -- Om de conventie te volgen

raycastParams.BruteForceAllSlow = true  -- Zodat onderdelen met CanQuery van "false" geselecteerd kunnen worden

local mouseLocation = UserInputService:GetMouseLocation()

local mouseRay = workspace.CurrentCamera:ViewportPointToRay(mouseLocation.X, mouseLocation.Y)

local filteredSelectionHit = workspace:Raycast(mouseRay.Origin, mouseRay.Direction * 10000, raycastParams)

```

### [Deel-tot-deel filtering](#deel-tot-deel-filtering)[](#deel-tot-deel-filtering)

Om botsingen tussen twee specifieke onderdelen te voorkomen zonder [botsingsgroepen](#botsingsgroepen)  op te zetten, zoals tussen een voertuigwiel en zijn chassis, overweeg de [No Collision](/docs/nl-nl/physics/mechanical-constraints#nocollisionconstraint)  constraint. Voordelen zijn onder andere:

-

Botsingsgroepen en/of configuratiescripts zijn niet vereist, zodat je eenvoudig modellen kunt maken en delen met aangepaste botsingsfiltering.

-

Verbonden onderdelen zullen niet met elkaar botsen, maar ze kunnen nog steeds met andere objecten botsen.

### [Schakel karakterbotsingen uit](#schakel-karakterbotsingen-uit)[](#schakel-karakterbotsingen-uit)

Roblox-spelerkarakters botsen standaard met elkaar. Dit kan leiden tot interessante maar onbedoelde gameplay, zoals karakters die op elkaar springen om specifieke gebieden te bereiken. Als dit gedrag ongewenst is, kun je het voorkomen via het volgende [Script](/docs/nl-nl/reference/engine/classes/Script)  in [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService) .

Script - Schakel Karakterbotsingen Uit

```

local Players = game:GetService("Players")

workspace:RegisterCollisionGroup("Characters")

workspace:CollisionGroupSetCollidable("Characters", "Characters", false)

local function onDescendantAdded(descendant)

	-- Stel botsingsgroep in voor elk onderdeel afgeleid van

	if descendant:IsA("BasePart") then

		descendant.CollisionGroup = "Characters"

	end

end

local function onCharacterAdded(character)

	-- Verwerk bestaande en nieuwe afgeleiden voor fysica-instelling

	for _, descendant in character:GetDescendants() do

		onDescendantAdded(descendant)

	end

	character.DescendantAdded:Connect(onDescendantAdded)

end

Players.PlayerAdded:Connect(function(player)

	-- Detecteer wanneer het karakter van de speler is toegevoegd

	player.CharacterAdded:Connect(onCharacterAdded)

end)

```

## [Modelbotsingen](#modelbotsingen)[](#modelbotsingen)

[Model](/docs/nl-nl/reference/engine/classes/Model)  objecten zijn containers voor onderdelen in plaats van afgeleid van [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) , dus ze kunnen niet direct verbinding maken met [BasePart.Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched)  of [BasePart.TouchEnded](/docs/nl-nl/reference/engine/classes/BasePart#TouchEnded)  events. Om te bepalen of een model een botsingsevent activeert, moet je door zijn kinderen lopen en de aangepaste onTouched()  en onTouchEnded()  functies aan elk kind [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  verbinden.

Voor samengevoegde onderdelen door [solide modellering](/docs/nl-nl/parts/solid-modeling)  in plaats van [Model](/docs/nl-nl/reference/engine/classes/Model)  objecten, zie [mesh en solide modelbotsingen](#mesh-en-solide-modelbotsingen) .

Het volgende codevoorbeeld verbindt alle [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  van een multi-part model met botsingsevents en houdt het totale aantal botsingen met andere onderdelen bij.

Model Botsing

```

local model = script.Parent

local numTouchingParts = 0

local function onTouched(otherPart)

	-- Negeer instanties van het model die met zichzelf overlappen

	if otherPart:IsDescendantOf(model) then return end

	-- Verhoog het aantal modelonderdelen dat aanraakt

	numTouchingParts += 1

	print(model.Name, "overlapte met", otherPart.Name, "| Modelonderdelen die aanraken:", numTouchingParts)

end

local function onTouchEnded(otherPart)

	-- Negeer instanties van het model die niet meer overlappen met zichzelf

	if otherPart:IsDescendantOf(model) then return end

	-- Verlaag het aantal modelonderdelen dat aanraakt

	numTouchingParts -= 1

	print(model.Name, "is niet meer overlapt met", otherPart.Name, "| Modelonderdelen die aanraken:", numTouchingParts)

end

for _, child in model:GetChildren() do

	if child:IsA("BasePart") then

		child.Touched:Connect(onTouched)

		child.TouchEnded:Connect(onTouchEnded)

	end

end

```

## [Mesh en solide modelbotsingen](#mesh-en-solide-modelbotsingen)[](#mesh-en-solide-modelbotsingen)

[MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  en [PartOperation](/docs/nl-nl/reference/engine/classes/PartOperation)  (onderdelen samengevoegd door [solide modellering](/docs/nl-nl/parts/solid-modeling) ) zijn subklassen van [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) , zodat meshes en solide gemodelleerde onderdelen dezelfde [botsingsevents](#botsingsevents)  en [botsingsfiltering](#botsingsfiltering)  opties erven als reguliere onderdelen. Omdat meshes en solide gemodelleerde onderdelen meestal complexere geometrieën hebben, hebben ze een onderscheidende [CollisionFidelity](/docs/nl-nl/reference/engine/classes/TriangleMeshPart#CollisionFidelity)  eigenschap die bepaalt hoe nauwkeurig de fysieke grenzen overeenkomen met de visuele representatie voor botsingsverwerking.

De [CollisionFidelity](/docs/nl-nl/reference/engine/classes/TriangleMeshPart#CollisionFidelity)  eigenschap heeft de volgende opties, in volgorde van nauwkeurigheid en prestatie-impact van laag naar hoog:

-

Doos  — Creëert een begrenzende botsingsdoos, ideaal voor kleine of niet-interactieve objecten.

-

Hul  — Genereert een convexe hul, geschikt voor objecten met minder uitgesproken indeukingen of holtes.

-

Standaard  — Produceert een benaderende botsingsvorm die concaviteit ondersteunt, geschikt voor complexe objecten met semi-gedetailleerde interactiebehoeften.

-

Nauwkeurige Convexe Decompositie  — Biedt de meest nauwkeurige nauwkeurigheid, maar nog steeds geen 1:1 representatie van het visuele. Deze optie heeft de duurste prestatiekosten en duurt langer voor de engine om te berekenen.

Originele Mesh Standaard Doos Hul Nauwkeurig

![Originele mesh van kasteel toren](https://prod.docsiteassets.roblox.com/assets/physics/collisions/Collision-Fidelity-MeshPart.jpg)

Om de botsingsnauwkeurigheid in Studio te bekijken, schakel je Botsingsnauwkeurigheid  in via de [Visualisatie-opties](/docs/nl-nl/studio/overview#visualisatie-opties)  widget in de rechterbovenhoek van de 3D-weergave.

Voor meer informatie over de prestatie-impact van botsingsnauwkeurigheid opties en hoe deze te mitigeren, zie [prestatieoptimalisatie](/docs/nl-nl/performance-optimization/improve#fysica-berekeningen) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
