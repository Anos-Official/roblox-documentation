<!-- Source: https://create.roblox.com/docs/nl-nl/scripting/multithreading -->

Parallel Luau | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)
6. /
7. Geavanceerd

# Parallel Luau

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Met het Parallel Luau  programmeermodel kun je code gelijktijdig op meerdere threads uitvoeren, wat de prestaties van je game kan verbeteren. Terwijl je je game uitbreidt met meer inhoud, kun je dit model aannemen om de prestaties en veiligheid van je Luau-scripts te behouden.

## [Parallel programmeermodel](#parallel-programmeermodel)[](#parallel-programmeermodel)

Standaard worden scripts sequentieel uitgevoerd. Als je game complexe logica of inhoud heeft, zoals niet-speler personages (NPC's), raycasting-validatie en procedurele generatie, kan sequentiële uitvoering vertraging veroorzaken voor je gebruikers. Met het parallelle programmeermodel kun je [taken splitsen in meerdere scripts](#split-code-in-meerdere-threads)  en ze parallel uitvoeren. Dit zorgt ervoor dat je gamecode sneller draait, wat de gebruikerservaring verbetert.

Het parallelle programmeermodel voegt ook veiligheidsvoordelen toe aan je code. Door code in meerdere threads te splitsen, heeft het bewerken van code in één thread geen invloed op andere code die parallel draait. Dit vermindert het risico dat één bug in je code de hele game corrumpeert en minimaliseert de vertraging voor gebruikers op live servers wanneer je een update doorvoert.

Het aannemen van het parallelle programmeermodel betekent niet dat je alles in meerdere threads moet plaatsen. Bijvoorbeeld, de [server-side raycasting-validatie](#server-side-raycasting-validatie)  stelt elke individuele gebruiker in staat om een remote event parallel te ontvangen, maar vereist nog steeds dat de initiële code sequentieel wordt uitgevoerd om globale eigenschappen te wijzigen, wat een veelvoorkomend patroon is voor parallelle uitvoering.

Meestal moet je sequentiële en parallelle fasen combineren om de gewenste output te bereiken, aangezien er momenteel enkele bewerkingen zijn die niet in parallel worden ondersteund en die kunnen voorkomen dat scripts worden uitgevoerd, zoals het wijzigen van instanties in parallelle fasen. Voor meer informatie over het gebruiksniveau van API's in parallel, zie [threadveiligheid](#threadveiligheid) .

## [Split code in meerdere threads](#split-code-in-meerdere-threads)[](#split-code-in-meerdere-threads)

Om de scripts van je game gelijktijdig in meerdere threads uit te voeren, moet je ze splitsen in logische delen onder verschillende actoren  in het [datamodel](/docs/nl-nl/projects/data-model) . Actoren worden weergegeven door [Actor](/docs/nl-nl/reference/engine/classes/Actor)  instanties die afstammen van [DataModel](/docs/nl-nl/reference/engine/classes/DataModel) . Ze functioneren als eenheden van uitvoeringsisolatie die de belasting over meerdere cores die gelijktijdig draaien verdelen.

### [Plaats actor-instanties](#plaats-actor-instanties)[](#plaats-actor-instanties)

Je kunt actoren in geschikte containers plaatsen of ze gebruiken om de top-level instantie types van je 3D-entiteiten zoals NPC's en raycasters te vervangen, en vervolgens de bijbehorende scripts toe te voegen.

 ![Een voorbeeld van een Script onder een Actor](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ServerScriptService-Actor.png)

In de meeste situaties zou je een actor niet als kind van een andere actor in het datamodel moeten plaatsen. Als je echter besluit om een script genest binnen meerdere actoren voor je specifieke gebruiksgeval te plaatsen, is het script eigendom van de dichtstbijzijnde voorouderactor.

 ![Een boom van actoren en scripts die laat zien hoe een script eigendom is van zijn dichtstbijzijnde actor](https://prod.docsiteassets.roblox.com/assets/scripting/scripts/Actor-Tree.png)

### [Desynchroniseer threads](#desynchroniseer-threads)[](#desynchroniseer-threads)

Hoewel het plaatsen van scripts onder actoren hen de mogelijkheid geeft voor parallelle uitvoering, draait de code standaard nog steeds op de enkele thread sequentieel, wat de runtime-prestaties niet verbetert. Je moet [task.desynchronize()](/docs/nl-nl/reference/engine/libraries/task#desynchronize)  aanroepen, een yieldbare functie die de uitvoering van de huidige coroutine opschort om code parallel uit te voeren en deze hervat bij de volgende parallelle uitvoeringsmogelijkheid. Om een script terug te schakelen naar sequentiële uitvoering, roep je [task.synchronize()](/docs/nl-nl/reference/engine/libraries/task#synchronize)  aan.

Alternatief kun je de [RBXScriptSignal:ConnectParallel()](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal#ConnectParallel)  methode gebruiken wanneer je een signaalcallback wilt plannen om je code onmiddellijk parallel uit te voeren bij het triggeren. Je hoeft [task.desynchronize()](/docs/nl-nl/reference/engine/libraries/task#desynchronize)  niet aan te roepen binnen de signaalcallback.

Desynchroniseer een Thread

```

local RunService = game:GetService("RunService")

RunService.Heartbeat:ConnectParallel(function()

	...  -- Enkele parallelle code die een statusupdate berekent

	task.synchronize()

	...  -- Enkele sequentiële code die de status van instanties wijzigt

end)

```

Je kunt require()  niet gebruiken in een gedesynchroniseerde parallelle fase. Vereis scripts die je eerst in een sequentiële context wilt gebruiken.

Scripts die deel uitmaken van dezelfde actor worden altijd sequentieel uitgevoerd ten opzichte van elkaar, dus je hebt meerdere actoren nodig. Als je bijvoorbeeld alle parallel-geschikte gedragsscripts voor je NPC in één actor plaatst, worden ze nog steeds sequentieel op een enkele thread uitgevoerd, maar als je meerdere actoren hebt voor verschillende NPC-logica, draait elke actor parallel op zijn eigen thread. Voor meer informatie, zie [Best practices](#best-practices) .

![](https://prod.docsiteassets.roblox.com/assets/scripting/scripts/single-thread.png) Parallelle code in Actoren die sequentieel draaien op een enkele thread

![](https://prod.docsiteassets.roblox.com/assets/scripting/scripts/multi-thread.png) Parallelle code in Actoren die gelijktijdig draaien op meerdere threads

### [Threadveiligheid](#threadveiligheid)[](#threadveiligheid)

Tijdens de parallelle uitvoering kun je de meeste instanties van de [DataModel](/docs/nl-nl/reference/engine/classes/DataModel)  hiërarchie zoals gewoonlijk benaderen, maar sommige API-eigenschappen en functies zijn niet veilig om te lezen of te schrijven. Als je ze in je parallelle code gebruikt, kan de Roblox-engine deze toegang automatisch detecteren en voorkomen.

API-leden hebben een threadveiligheidsniveau dat aangeeft of en hoe je ze in je parallelle code kunt gebruiken, zoals de volgende tabel toont:

| Veiligheidsniveau | | Voor eigenschappen | | Voor functies |
| --- | --- |
| Onveilig | | Kan niet in parallel worden gelezen of geschreven. | | Kan niet in parallel worden aangeroepen. |
| Lezen Parallel | | Kan in parallel worden gelezen, maar niet geschreven. | | N.v.t. |
| Lokaal Veilig | | Kan binnen dezelfde Actor worden gebruikt; kan worden gelezen maar niet geschreven door andere [Actors](/docs/nl-nl/reference/engine/classes/Actor)  in parallel. | | Kan binnen dezelfde Actor worden aangeroepen; kan niet door andere [Actors](/docs/nl-nl/reference/engine/classes/Actor)  in parallel worden aangeroepen. |
| Veilig | | Kan worden gelezen en geschreven. | | Kan worden aangeroepen. |

Je kunt threadveiligheidstags voor API-leden vinden op de [API-referentie](/docs/nl-nl/reference/engine) . Bij het gebruik ervan moet je ook overwegen hoe API-aanroepen of eigenschapswijzigingen kunnen interageren tussen parallelle threads. Gewoonlijk is het veilig voor meerdere actoren om dezelfde gegevens te lezen als andere actoren, maar niet om de status van andere actoren te wijzigen.

Als een API-lid geen threadveiligheidsniveau specificeert, is het standaard threadveiligheidsniveau Onveilig .

## [Communicatie tussen threads](#communicatie-tussen-threads)[](#communicatie-tussen-threads)

In de context van multithreading kun je scripts in verschillende actoren nog steeds laten communiceren om gegevens uit te wisselen, taken te coördineren en activiteiten te synchroniseren. De engine ondersteunt de volgende mechanismen voor communicatie tussen threads:

-

[Actor messaging](#actor-messaging)  API voor het verzenden van berichten naar een actor met behulp van scripts.

-

[Gedeelde tabel](#gedeelde-tabel)  datastructuur voor het efficiënt delen van een grote hoeveelheid gegevens tussen meerdere actoren op een gedeelde status.

-

[Directe communicatie met het datamodel](#directe-communicatie-met-het-datamodel)  voor eenvoudige communicatie met beperkingen.

Je kunt meerdere mechanismen ondersteunen om aan je communicatiebehoeften tussen threads te voldoen. Bijvoorbeeld, je kunt een gedeelde tabel verzenden via de Actor Messaging API.

### [Actor messaging](#actor-messaging)[](#actor-messaging)

De actor messaging  API stelt een script, hetzij in een sequentiële of parallelle context, in staat om gegevens naar een actor in hetzelfde datamodel te verzenden. Communicatie via deze API is asynchroon, waarbij de verzender niet blokkeert totdat de ontvanger het bericht ontvangt.

Bij het verzenden van berichten met behulp van deze API, moet je een onderwerp  definiëren voor het categoriseren van het bericht. Elk bericht kan slechts naar één enkele actor worden verzonden, maar die actor kan intern meerdere callbacks aan een bericht binden. Alleen scripts die afstammelingen zijn van een actor kunnen berichten ontvangen.

De API heeft de volgende methoden:

-

[Actor:SendMessage()](/docs/nl-nl/reference/engine/classes/Actor#SendMessage)  voor het verzenden van een bericht naar een actor.

-

[Actor:BindToMessage()](/docs/nl-nl/reference/engine/classes/Actor#BindToMessage)  voor het binden van een Luau-callback aan een bericht met het opgegeven onderwerp in een sequentiële context.

-

[Actor:BindToMessageParallel()](/docs/nl-nl/reference/engine/classes/Actor#BindToMessageParallel)  voor het binden van een Luau-callback aan een bericht met het opgegeven onderwerp in een parallelle context.

Het volgende voorbeeld laat zien hoe je [Actor:SendMessage()](/docs/nl-nl/reference/engine/classes/Actor#SendMessage)  kunt gebruiken om een onderwerp te definiëren en een bericht aan de verzenderzijde te verzenden:

Voorbeeld Bericht Verzender

```

local Workspace = game:GetService("Workspace")

-- Stuur twee berichten naar de werkactor met een onderwerp van "Greeting"

local workerActor = Workspace.WorkerActor

workerActor:SendMessage("Greeting", "Hallo Wereld!")

workerActor:SendMessage("Greeting", "Welkom")

print("Berichten verzonden")

```

Het volgende voorbeeld laat zien hoe je [Actor:BindToMessageParallel()](/docs/nl-nl/reference/engine/classes/Actor#BindToMessageParallel)  kunt gebruiken om een callback te binden voor een bepaald onderwerp in een parallelle context aan de ontvangerzijde:

Voorbeeld Bericht Ontvanger

```

-- Verkrijg de actor waaraan dit script is gekoppeld

local actor = script:GetActor()

-- Bind een callback voor het "Greeting" bericht onderwerp

actor:BindToMessageParallel("Greeting", function(greetingString)

	print(actor.Name, "-", greetingString)

end)

print("Gebonden aan berichten")

```

### [Gedeelde tabel](#gedeelde-tabel)[](#gedeelde-tabel)

[SharedTable](/docs/nl-nl/reference/engine/datatypes/SharedTable)  is een tabelachtige datastructuur die toegankelijk is vanuit scripts die onder meerdere actoren draaien. Het is nuttig voor situaties die een grote hoeveelheid gegevens omvatten en een gemeenschappelijke gedeelde status tussen meerdere threads vereisen. Bijvoorbeeld, wanneer meerdere actoren werken aan een gemeenschappelijke wereldstatus die niet in het datamodel is opgeslagen.

Het verzenden van een gedeelde tabel naar een andere actor maakt geen kopie van de gegevens. In plaats daarvan stellen gedeelde tabellen veilige en atomische updates door meerdere scripts gelijktijdig mogelijk. Elke update aan een gedeelde tabel door één actor is onmiddellijk zichtbaar voor alle actoren. Gedeelde tabellen kunnen ook worden gekloond in een hulpbronnenefficiënt proces dat structurele delen in plaats van het kopiëren van de onderliggende gegevens gebruikt.

### [Directe communicatie met het datamodel](#directe-communicatie-met-het-datamodel)[](#directe-communicatie-met-het-datamodel)

Je kunt ook communicatie tussen meerdere threads direct faciliteren met behulp van het datamodel, waarbij verschillende actoren eigenschappen of attributen kunnen schrijven en vervolgens lezen. Om echter de threadveiligheid te behouden, kunnen scripts die parallel draaien over het algemeen niet naar het datamodel schrijven. Het direct gebruiken van het datamodel voor communicatie komt dus met beperkingen en kan scripts dwingen om vaak te synchroniseren, wat de prestaties van je scripts kan beïnvloeden.

## [Voorbeelden](#voorbeelden)[](#voorbeelden)

### [Server-side raycasting-validatie](#server-side-raycasting-validatie)[](#server-side-raycasting-validatie)

Voor een vecht- en strijdspel moet je [raycasting](/docs/nl-nl/workspace/raycasting)  inschakelen voor de wapens van je gebruikers. Met de client die de wapens simuleert om een goede latentie te bereiken, moet de server de hit bevestigen, wat inhoudt dat raycasts moeten worden uitgevoerd en een bepaalde hoeveelheid heuristiek moet worden berekend die de verwachte snelheid van het personage berekent en kijkt naar het verleden gedrag.

In plaats van een enkele gecentraliseerde script te gebruiken die verbinding maakt met een remote event dat clients gebruiken om hit-informatie te communiceren, kun je elk hit-validatieproces aan de serverzijde parallel uitvoeren, waarbij elke gebruikerskarakter een aparte remote event heeft.

Het server-side script dat onder de [Actor](/docs/nl-nl/reference/engine/classes/Actor)  van dat karakter draait, maakt verbinding met deze remote event met behulp van een parallelle verbinding om de relevante logica voor het bevestigen van de hit uit te voeren. Als de logica een bevestiging van een hit vindt, wordt de schade afgetrokken, wat inhoudt dat eigenschappen moeten worden gewijzigd, dus het draait aanvankelijk sequentieel.

```

local Workspace = game:GetService("Workspace")

local tool = script.Parent.Parent

local remoteEvent = Instance.new("RemoteEvent")  -- Maak een nieuwe remote event en plaats deze onder het gereedschap

remoteEvent.Name = "RemoteMouseEvent"  -- Hernoem het zodat het lokale script ernaar kan zoeken

remoteEvent.Parent = tool

local remoteEventConnection  -- Maak een referentie voor de remote event-verbinding

-- Functie die luistert naar een remote event

local function onRemoteMouseEvent(player: Player, clickLocation: CFrame)

	-- SEQUENTIEEL: Voer setupcode uit in sequentieel

	local character = player.Character

	-- Negeer het karakter van de gebruiker tijdens raycasting

	local params = RaycastParams.new()

	params.FilterType = Enum.RaycastFilterType.Exclude

	params.FilterDescendantsInstances = { character }

	-- PARALLEL: Voer de raycast parallel uit

	task.desynchronize()

	local origin = tool.Handle.CFrame.Position

	local epsilon = 0.01  -- Gebruikt om de ray iets uit te breiden aangezien de kliklocatie mogelijk iets verschoven is van het object

	local lookDirection = (1 + epsilon) * (clickLocation.Position - origin)

	local raycastResult = Workspace:Raycast(origin, lookDirection, params)

	if raycastResult then

		local hitPart = raycastResult.Instance

		if hitPart and hitPart.Name == "block" then

			local explosion = Instance.new("Explosion")

			-- SEQUENTIEEL: De onderstaande code wijzigt de status buiten de actor

			task.synchronize()

			explosion.DestroyJointRadiusPercent = 0  -- Maak de explosie niet dodelijk

			explosion.Position = clickLocation.Position

			-- Meerdere actoren kunnen hetzelfde deel in een raycast krijgen en besluiten het te vernietigen

			-- Dit is perfect veilig, maar het zou resulteren in twee explosies tegelijk in plaats van één

			-- De volgende dubbele controle zorgt ervoor dat de uitvoering eerst naar dit deel is gegaan

			if hitPart.Parent then

				explosion.Parent = Workspace

				hitPart:Destroy()  -- Vernietig het

			end

		end

	end

end

-- Verbind het signaal aanvankelijk sequentieel, aangezien sommige setupcode niet in parallel kan draaien

remoteEventConnection = remoteEvent.OnServerEvent:Connect(onRemoteMouseEvent)

```

### [Server-side procedurele terrein generatie](#server-side-procedurele-terrein-generatie)[](#server-side-procedurele-terrein-generatie)

Om een uitgestrekte wereld voor je game te creëren, kun je de wereld dynamisch bevolken. Procedurele generatie creëert doorgaans onafhankelijke terreinstukken, waarbij de generator relatief ingewikkelde berekeningen uitvoert voor objectplaatsing, materiaalgebruik en voxelvulling. Het uitvoeren van generatiecode in parallel kan de efficiëntie van het proces verbeteren. De volgende codevoorbeeld dient als een voorbeeld.

```

-- Parallelle uitvoering vereist het gebruik van actoren

-- Dit script kloont zichzelf; de originele initieert het proces, terwijl de klonen als werkers fungeren

local Workspace = game:GetService("Workspace")

local actor = script:GetActor()

if actor == nil then

	local workers = {}

	for i = 1, 32 do

		local actor = Instance.new("Actor")

		script:Clone().Parent = actor

		table.insert(workers, actor)

	end

	-- Plaats alle actoren onder zichzelf

	for _, actor in workers do

		actor.Parent = script

	end

	-- Geef de actoren de instructie om terrein te genereren door berichten te verzenden

	-- In dit voorbeeld worden actoren willekeurig gekozen

	task.defer(function()

		local rand = Random.new()

		local seed = rand:NextNumber()

		local sz = 10

		for x = -sz, sz do

			for y = -sz, sz do

				for z = -sz, sz do

					workers[rand:NextInteger(1, #workers)]:SendMessage("GenerateChunk", x, y, z, seed)

				end

			end

		end

	end)

	-- Verlaat het originele script; de rest van de code draait in elke actor

	return

end

function makeNdArray(numDim, size, elemValue)

	if numDim == 0 then

		return elemValue

	end

	local result = {}

	for i = 1, size do

		result[i] = makeNdArray(numDim - 1, size, elemValue)

	end

	return result

end

function generateVoxelsWithSeed(xd, yd, zd, seed)

	local matEnums = {Enum.Material.CrackedLava, Enum.Material.Basalt, Enum.Material.Asphalt}

	local materials = makeNdArray(3, 4, Enum.Material.CrackedLava)

	local occupancy = makeNdArray(3, 4, 1)

	local rand = Random.new()

	for x = 0, 3 do

		for y = 0, 3 do

			for z = 0, 3 do

				occupancy[x + 1][y + 1][z + 1] = math.noise(xd + 0.25 * x, yd + 0.25 * y, zd + 0.25 * z)

				materials[x + 1][y + 1][z + 1] = matEnums[rand:NextInteger(1, #matEnums)]

			end

		end

	end

	return {materials = materials, occupancy = occupancy}

end

-- Bind de callback om in de parallelle uitvoeringscontext te worden aangeroepen

actor:BindToMessageParallel("GenerateChunk", function(x, y, z, seed)

	local voxels = generateVoxelsWithSeed(x, y, z, seed)

	local corner = Vector3.new(x * 16, y * 16, z * 16)

	-- Momenteel moet WriteVoxels() in de sequentiële fase worden aangeroepen

	task.synchronize()

	Workspace.Terrain:WriteVoxels(

		Region3.new(corner, corner + Vector3.new(16, 16, 16)),

		4,

		voxels.materials,

		voxels.occupancy

	)

end)

```

## [Best practices](#best-practices)[](#best-practices)

Om de maximale voordelen van parallel programmeren toe te passen, raadpleeg de volgende best practices bij het toevoegen van je Luau-code:

-

Vermijd Lange Berekeningen  — Zelfs in parallel kunnen lange berekeningen de uitvoering van andere scripts blokkeren en vertraging veroorzaken. Vermijd het gebruik van parallel programmeren om een grote hoeveelheid lange, niet-yieldbare berekeningen af te handelen.

 ![Diagram dat laat zien hoe overbelasting van de parallelle uitvoeringsfase nog steeds vertraging kan veroorzaken](https://prod.docsiteassets.roblox.com/assets/scripting/scripts/ParallelExecutionDark.png)

-

Gebruik het Juiste Aantal Actoren  — Voor de beste prestaties, gebruik meer [Actors](/docs/nl-nl/reference/engine/classes/Actor) . Zelfs als het apparaat minder cores heeft dan [Actors](/docs/nl-nl/reference/engine/classes/Actor) , maakt de granulariteit een efficiëntere load balancing tussen de cores mogelijk.

 ![Demonstratie van hoe het gebruik van meer actoren de belasting over cores balanceert](https://prod.docsiteassets.roblox.com/assets/scripting/scripts/FewerVsMoreActorsDark.png)

Dit betekent niet dat je zoveel mogelijk [Actors](/docs/nl-nl/reference/engine/classes/Actor)  moet gebruiken. Je moet de code nog steeds verdelen in [Actors](/docs/nl-nl/reference/engine/classes/Actor)  op basis van logische eenheden in plaats van de code met verbonden logica in verschillende [Actors](/docs/nl-nl/reference/engine/classes/Actor)  te splitsen. Bijvoorbeeld, als je [raycasting-validatie](#server-side-raycasting-validatie)  parallel wilt inschakelen, is het redelijk om 64 [Actors](/docs/nl-nl/reference/engine/classes/Actor)  en meer te gebruiken in plaats van slechts 4, zelfs als je richt op 4-core systemen. Dit is waardevol voor de schaalbaarheid van het systeem en stelt het in staat om het werk te verdelen op basis van de mogelijkheden van de onderliggende hardware. Echter, je moet ook niet te veel [Actors](/docs/nl-nl/reference/engine/classes/Actor)  gebruiken, die moeilijk te onderhouden zijn.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
