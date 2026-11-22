<!-- Source: https://create.roblox.com/docs/nl-nl/characters/pathfinding -->

Padvinden | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Personages](/docs/nl-nl/characters)

# Padvinden

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Padvinden  is het proces van het verplaatsen van een karakter of object (agent) langs een logisch pad rond obstakels om een bestemming te bereiken, waarbij optioneel gevaarlijke materialen of gedefinieerde gebieden worden vermeden.

## [Navigatievisualisatie](#navigatievisualisatie)[](#navigatievisualisatie)

Om te helpen bij de lay-out en het debuggen van padvinden, kan Studio een navigatiemesh en [modificator](#padvindmodificatoren)  labels weergeven. Om ze in te schakelen, zet je Navigatiemesh  en Padvindmodificatoren  aan vanuit de [Visualisatie-opties](/docs/nl-nl/studio/overview#visualisatie-opties)  widget in de rechterbovenhoek van het 3D-venster.

 ![Een close-up van het 3D-venster met de Visualisatie-opties knop aangegeven in de rechterbovenhoek.](https://prod.docsiteassets.roblox.com/assets/studio/general/Visualization-Options.png)

Navigatiemesh Padvindmodificatoren

Met Navigatiemesh  ingeschakeld, tonen gekleurde gebieden waar een karakter kan lopen of zwemmen. Kleine pijlen geven gebieden aan die een karakter zal proberen te bereiken door te springen.

![Navigatiemesh weergegeven in Studio](https://prod.docsiteassets.roblox.com/assets/avatar/pathfinding/Navigation-Mesh.jpg)

## [Implementatie](#implementatie)[](#implementatie)

Hoewel padvinden op verschillende manieren kan worden geïmplementeerd via [PathfindingService](/docs/nl-nl/reference/engine/classes/PathfindingService)  en de bijbehorende methoden zoals [CreatePath()](/docs/nl-nl/reference/engine/classes/PathfindingService#CreatePath) , gebruikt deze sectie het volgende padvindscript voor het karakter van de speler.

Om te testen terwijl je leest:

1.

BELANGRIJK

 In de [Explorer](/docs/nl-nl/studio/explorer) , selecteer de [StarterPlayer](/docs/nl-nl/reference/engine/classes/StarterPlayer)  container. Stel vervolgens in het [Eigenschappen](/docs/nl-nl/studio/properties)  venster zowel [DevComputerMovementMode](/docs/nl-nl/reference/engine/classes/StarterPlayer#DevComputerMovementMode)  als [DevTouchMovementMode](/docs/nl-nl/reference/engine/classes/StarterPlayer#DevTouchMovementMode)  in op Scriptable .

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/StarterPlayer.png)

![](https://prod.docsiteassets.roblox.com/assets/studio/properties/StarterPlayer-DevComputerMovementMode-DevTouchMovementMode.png)

2.

Kopieer de volgende code in een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  binnen [StarterCharacterScripts](/docs/nl-nl/reference/engine/classes/StarterCharacterScripts) , of [haal dit pakket op](https://create.roblox.com/store/asset/95888831676289/Player-Path-Following-Script)  en plaats het in [StarterCharacterScripts](/docs/nl-nl/reference/engine/classes/StarterCharacterScripts) .

PlayerPathFollow (LocalScript in StarterCharacterScripts)

```

local PathfindingService = game:GetService("PathfindingService")

local Players = game:GetService("Players")

local RunService = game:GetService("RunService")

local DESTINATION = Vector3.new(20, 0.5, 20)

local GROUND_WAIT = 0.01

local VELOCITY_MULTIPLIER = 0.0625

local path = PathfindingService:CreatePath({

	AgentCanClimb = true,

	Costs = {

		Water = 20

	}

})

local character = script.Parent

local humanoid = character:WaitForChild("Humanoid")

local waypoints

local nextWaypointIndex

local blockedConnection

local currentWaypointReachedConnection

local currentWaypointPlaneNormal = Vector3.zero

local currentWaypointPlaneDistance = 0

local pathfinderWorking = false

local function disconnectCurrentWaypointReachedConnection()

	if not currentWaypointReachedConnection then return end

	currentWaypointReachedConnection:Disconnect()

	currentWaypointReachedConnection = nil

end

local function isCurrentWaypointReached()

	if humanoid.FloorMaterial == Enum.Material.Air then

		return false

	end

	local reached = false

	if currentWaypointPlaneNormal ~= Vector3.zero then

		-- Bereken de afstand van humanoid tot het bestemmingsvlak

		local dist = currentWaypointPlaneNormal:Dot(humanoid.RootPart.Position) - currentWaypointPlaneDistance

		-- Bereken de component van de humanoïde snelheid die naar het vlak is gericht

		local velocity = -currentWaypointPlaneNormal:Dot(humanoid.RootPart.Velocity)

		-- Bereken de drempel van het bestemmingsvlak op basis van de snelheid van de humanoïde

		local threshold = math.max(1.0, VELOCITY_MULTIPLIER * velocity)

		-- Beschouw waypoint als bereikt als minder dan drempel voor het vlak

		reached = dist < threshold

	else

		reached = true

	end

	if reached then

		currentWaypointPlaneNormal = Vector3.zero

		currentWaypointPlaneDistance = 0

		moveToNextWaypoint()

	end

end

local function calculateNextWaypointApproach()

	nextWaypointIndex += 1

	if nextWaypointIndex > #waypoints then

		return false

	end

	local currentWaypoint = waypoints[nextWaypointIndex - 1]

	local nextWaypoint = waypoints[nextWaypointIndex]

	-- Bouw bestemmingsvlak van volgende waypoint naar huidige

	currentWaypointPlaneNormal = currentWaypoint.Position - nextWaypoint.Position

	-- Zet normaal loodrecht op het Y-vlak wanneer niet omhoog klimmend

	if nextWaypoint.Label ~= "Climb" then

		currentWaypointPlaneNormal = Vector3.new(currentWaypointPlaneNormal.X, 0, currentWaypointPlaneNormal.Z)

	end

	if currentWaypointPlaneNormal.Magnitude > 0.000001 then

		currentWaypointPlaneNormal	= currentWaypointPlaneNormal.Unit

		currentWaypointPlaneDistance = currentWaypointPlaneNormal:Dot(nextWaypoint.Position)

	end

	return true

end

local function resetWaypointData()

	humanoid:Move(Vector3.zero)

	currentWaypointPlaneNormal	= Vector3.zero

	currentWaypointPlaneDistance = 0

	disconnectCurrentWaypointReachedConnection()

	pathfinderWorking = false

end

local function waitForGround()

	while humanoid.FloorMaterial == Enum.Material.Air do

		task.wait(GROUND_WAIT)

	end

end

function moveToNextWaypoint()

	if calculateNextWaypointApproach() then

		disconnectCurrentWaypointReachedConnection()

		currentWaypointReachedConnection = RunService.Heartbeat:Connect(isCurrentWaypointReached)

		local nextWaypointPosition = waypoints[nextWaypointIndex].Position

		local nextWaypointAction = waypoints[nextWaypointIndex].Action

		humanoid:Move(nextWaypointPosition - humanoid.RootPart.Position)

		if waypoints[nextWaypointIndex + 1] and waypoints[nextWaypointIndex + 1].Label == "UseBoat" then

			nextWaypointIndex += 1

			-- Roep je eigen aangepaste functie aan om de agent de boot te laten gebruiken

		elseif nextWaypointAction == Enum.PathWaypointAction.Jump then

			humanoid:ChangeState(Enum.HumanoidStateType.Jumping)

			while humanoid.FloorMaterial ~= Enum.Material.Air do

				task.wait(GROUND_WAIT)

			end

			humanoid:Move(nextWaypointPosition - humanoid.RootPart.Position)

		end

	else

		resetWaypointData()

	end

end

local function findStartingPoint(waypoints)

	nextWaypointIndex = 1

	while nextWaypointIndex + 1 <= #waypoints do

		local dist = waypoints[nextWaypointIndex + 1].Position - humanoid.RootPart.Position

		dist = Vector3.new(dist.X, 0, dist.Z)

		if dist.magnitude >= 2 then

			return

		end

		nextWaypointIndex += 1

	end

end

local function followPath()

	-- Bereken het pad

	pathfinderWorking = true

	waitForGround()

	local success, errorMessage = pcall(function()

		path:ComputeAsync(character.PrimaryPart.Position, DESTINATION)

	end)

	if not success or path.Status ~= Enum.PathStatus.Success then

		warn("Pad niet berekend!", errorMessage)

		return

	end

	-- Verkrijg de padwaypoints

	waypoints = path:GetWaypoints()

	-- Detecteer of het pad geblokkeerd raakt

	blockedConnection = path.Blocked:Connect(function(blockedWaypointIndex)

		-- Controleer of het obstakel verderop op het pad ligt

		if blockedWaypointIndex >= nextWaypointIndex then

			-- Stop met het detecteren van padblokkades totdat het pad opnieuw is berekend

			blockedConnection:Disconnect()

			resetWaypointData()

			-- Roep functie aan om nieuw pad opnieuw te berekenen

			followPath()

		end

	end)

	findStartingPoint(waypoints)

	moveToNextWaypoint()

end

followPath()

```

3.

Bewerk de DESTINATION  variabele (

LIJN 5

) naar een [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  bestemming binnen de 3D-wereld die het spelerkarakter kan bereiken.

4.

Ga verder door de volgende secties om meer te leren over padberekening en karakterbeweging.

### [Padcreatie](#padcreatie)[](#padcreatie)

Padvinden wordt geïnitieerd via [PathfindingService](/docs/nl-nl/reference/engine/classes/PathfindingService)  en zijn [CreatePath()](/docs/nl-nl/reference/engine/classes/PathfindingService#CreatePath)  methode (

LIJNEN 9–14

). Deze methode accepteert een optionele tabel van parameters die verfijnen hoe het karakter (agent) zich langs het pad beweegt.

| Sleutel | | Beschrijving | | Type | | Standaard |
| --- | --- |
| AgentRadius | | Agentradius, in studs. Nuttig voor het bepalen van de minimale scheiding van obstakels. | | integer | | 2 |
| AgentHeight | | Agenthoogte, in studs. Lege ruimte kleiner dan deze waarde, zoals de ruimte onder trappen, wordt gemarkeerd als niet-overbrugbaar. | | integer | | 5 |
| AgentCanJump | | Bepaalt of springen tijdens padvinden is toegestaan. | | boolean | | true |
| AgentCanClimb | | Bepaalt of klimmen [TrussParts](/docs/nl-nl/reference/engine/classes/TrussPart)  tijdens padvinden is toegestaan. Een klimbaar pad heeft een [Label](/docs/nl-nl/reference/engine/datatypes/PathWaypoint#Label)  genaamd Climb  en de [kosten](#materiaalkosten)  voor een klimbaar pad is standaard 1 . | | boolean | | false |
| WaypointSpacing | | Afstand tussen tussenliggende waypoints in het pad. Als ingesteld op [math.huge](/docs/nl-nl/reference/engine/libraries/math#huge) , zijn er geen tussenliggende waypoints. | | number | | 4 |
| Costs | | Tabel van materialen of gedefinieerde [PathfindingModifiers](/docs/nl-nl/reference/engine/classes/PathfindingModifier)  en hun kosten voor traversie. Nuttig om de agent bepaalde materialen/gebieden boven andere te laten verkiezen. Zie [modificatoren](#padvindmodificatoren)  voor details. | | table | | nil |

### [Padberekening](#padberekening)[](#padberekening)

Nadat je een geldig pad hebt gemaakt met [CreatePath()](/docs/nl-nl/reference/engine/classes/PathfindingService#CreatePath) , moet het berekend  worden door [Path:ComputeAsync()](/docs/nl-nl/reference/engine/classes/Path#ComputeAsync)  aan te roepen met een [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  voor zowel het startpunt als de bestemming (

LIJNEN 133–139

).

![Pad start/eind gemarkeerd over twee bruggen](https://prod.docsiteassets.roblox.com/assets/avatar/pathfinding/Path-Start-End.jpg)

Zodra de [Path](/docs/nl-nl/reference/engine/classes/Path)  is berekend, bevat deze een reeks waypoints  die het pad van begin tot eind volgen. Deze punten kunnen worden verzameld met de [Path:GetWaypoints()](/docs/nl-nl/reference/engine/classes/Path#GetWaypoints)  methode (

LIJN 142

). De geretourneerde array is gerangschikt in volgorde van waypoints van padstart tot pad eind.

![Waypoints aangegeven over berekend pad](https://prod.docsiteassets.roblox.com/assets/avatar/pathfinding/Waypoints.jpg) Waypoints aangegeven over berekend pad

De padvindengine heeft specifieke beperkingen, en padvindberekeningen kunnen om verschillende redenen mislukken. Als je implementatie niet werkt zoals verwacht, zie dan [beperkingen en faalfactoren](#beperkingen-en-faalfactoren)  voor mogelijke oorzaken.

### [Padbeweging](#padbeweging)[](#padbeweging)

Elke [PathWaypoint](/docs/nl-nl/reference/engine/datatypes/PathWaypoint)  bestaat uit zowel een [Position](/docs/nl-nl/reference/engine/datatypes/PathWaypoint#Position)  ([Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) ) als [Action](/docs/nl-nl/reference/engine/datatypes/PathWaypoint#Action)  ([PathWaypointAction](/docs/nl-nl/reference/engine/enums/PathWaypointAction) ). Om een karakter met een [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid) , zoals een typisch Roblox-karakter, te verplaatsen, is de beste manier om [Humanoid:Move()](/docs/nl-nl/reference/engine/classes/Humanoid#Move)  van waypoint naar waypoint aan te roepen en de callback isCurrentWaypointReached()  van het script te gebruiken (

LIJNEN 32–56

) om te detecteren wanneer het karakter elk waypoint bereikt.

Let op dat het script wacht tot de humanoïde de grond aanraakt voordat het de padvinder aanroept. Als het pad wordt berekend terwijl het karakter door de lucht valt, zal de padvinder proberen een geschikte startpositie voor het pad te bepalen.

### [Geblokkeerde paden](#geblokkeerde-paden)[](#geblokkeerde-paden)

Veel Roblox-werelden zijn dynamisch; onderdelen kunnen bewegen of vallen en vloeren kunnen instorten. Dit kan een berekend pad blokkeren en voorkomen dat het karakter zijn bestemming bereikt. Om dit te verhelpen, kun je de [Path.Blocked](/docs/nl-nl/reference/engine/classes/Path#Blocked)  gebeurtenis verbinden en het pad opnieuw berekenen rond wat het blokkeert (

LIJNEN 145–154

).

Paden kunnen ook ergens achter  de agent geblokkeerd raken, zoals een stapel puin die op een pad valt terwijl de agent wegloopt, maar dat betekent niet dat de agent moet stoppen met bewegen. De if blockedWaypointIndex >= nextWaypointIndex  controle zorgt ervoor dat het pad alleen opnieuw wordt berekend als het geblokkeerde waypoint voor  het huidige waypoint ligt.

## [Padvindmodificatoren](#padvindmodificatoren)[](#padvindmodificatoren)

Standaard retourneert [Path:ComputeAsync()](/docs/nl-nl/reference/engine/classes/Path#ComputeAsync)  het kortste  pad tussen het startpunt en de bestemming, met de uitzondering dat het probeert sprongen te vermijden. Dit ziet er in sommige situaties onnatuurlijk uit; bijvoorbeeld, een pad kan door moeraswater gaan in plaats van eromheen simpelweg omdat het pad door het water geometrisch korter is.

![Twee paden aangegeven met het kortere pad niet noodzakelijkerwijs logischer](https://prod.docsiteassets.roblox.com/assets/avatar/pathfinding/Paths-Shortest-Best.jpg)

Om padvinden nog verder te optimaliseren, kun je padvindmodificatoren  implementeren om slimmer te berekenen over verschillende [materialen](#materiaalkosten) , rond gedefinieerde [gebieden](#regios-configureren) , of om [obstakels te negeren](#obstakels-negeren) .

### [Materiaalkosten](#materiaalkosten)[](#materiaalkosten)

Bij het werken met [Terrain](/docs/nl-nl/reference/engine/classes/Terrain)  en [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  materialen, kun je een Costs  tabel opnemen binnen [CreatePath()](/docs/nl-nl/reference/engine/classes/PathfindingService#CreatePath)  om bepaalde materialen beter begaanbaar te maken dan andere. Alle materialen hebben een standaardkost van 1  en elk materiaal kan als niet-overbrugbaar worden gedefinieerd door de waarde in te stellen op [math.huge](/docs/nl-nl/reference/engine/libraries/math#huge) .

Sleutels in de Costs  tabel moeten string  namen zijn die de [Enum.Material](/docs/nl-nl/reference/engine/enums/Material)  namen vertegenwoordigen, bijvoorbeeld Water  voor [Enum.Material.Water](/docs/nl-nl/reference/engine/enums/Material#Water)  of CrackedLava  voor [Enum.Material.CrackedLava](/docs/nl-nl/reference/engine/enums/Material#CrackedLava) .

PlayerPathFollow (LocalScript)

```

local PathfindingService = game:GetService("PathfindingService")

local Players = game:GetService("Players")

local RunService = game:GetService("RunService")

local DESTINATION = Vector3.new(20, 0.5, 20)

local GROUND_WAIT = 0.01

local VELOCITY_MULTIPLIER = 0.0625

local path = PathfindingService:CreatePath({

	AgentCanClimb = true,

	Costs = {

		Water = 20, CrackedLava = 100, Slate = 20

	}

})

```

Om een materiaal zoals CrackedLava  als "laatste optie" in te stellen, wijs je het een hoge maar eindige materiaalkost toe, zoals 100  of 1000 . Aangezien er geen door de engine afgedwongen bovengrens is onder [math.huge](/docs/nl-nl/reference/engine/libraries/math#huge) , zal de padvinder alleen door het materiaal routeren als elke alternatieve optie duurder is.

### [Regio's configureren](#regios-configureren)[](#regios-configureren)

In sommige gevallen is [materiaalvoorkeur](#materiaalkosten)  niet genoeg. Bijvoorbeeld, je wilt misschien dat karakters een gedefinieerde regio  vermijden, ongeacht de materialen onder hun voeten. Dit kan worden bereikt door een [PathfindingModifier](/docs/nl-nl/reference/engine/classes/PathfindingModifier)  object aan een onderdeel toe te voegen.

1.

Maak een [Anchored](/docs/nl-nl/reference/engine/classes/BasePart#Anchored)  onderdeel rond de regio en stel de [CanCollide](/docs/nl-nl/reference/engine/classes/BasePart#CanCollide)  eigenschap in op false .

 ![Geankerd onderdeel dat een regio definieert om een padvindmodificator op toe te passen.](https://prod.docsiteassets.roblox.com/assets/avatar/pathfinding/GeyserBlocker-Block.jpg)

2.

Voeg een [PathfindingModifier](/docs/nl-nl/reference/engine/classes/PathfindingModifier)  instantie toe aan het onderdeel, zoek de [Label](/docs/nl-nl/reference/engine/classes/PathfindingModifier#Label)  eigenschap en wijs een betekenisvolle naam toe zoals DangerZone .

 ![PathfindingModifier instantie met Label eigenschap ingesteld op DangerZone.](https://prod.docsiteassets.roblox.com/assets/studio/properties/PathfindingModifier-Label.png)

3.

Voeg een bijpassende DangerZone  sleutel en bijbehorende numerieke waarde toe binnen de Costs  tabel van [CreatePath()](/docs/nl-nl/reference/engine/classes/PathfindingService#CreatePath) . Een modificator kan als niet-overbrugbaar worden gedefinieerd door de waarde in te stellen op [math.huge](/docs/nl-nl/reference/engine/libraries/math#huge) .

PlayerPathFollow (LocalScript)

```

local PathfindingService = game:GetService("PathfindingService")

local Players = game:GetService("Players")

local RunService = game:GetService("RunService")

local DESTINATION = Vector3.new(20, 0.5, 20)

local GROUND_WAIT = 0.01

local VELOCITY_MULTIPLIER = 0.0625

local path = PathfindingService:CreatePath({

	AgentCanClimb = true,

	Costs = {

		DangerZone = math.huge, Water = 20, CrackedLava = 20, Slate = 20

	}

})

```

### [Obstakels negeren](#obstakels-negeren)[](#obstakels-negeren)

In sommige gevallen is het nuttig om door solide obstakels te padvinden alsof ze niet bestaan. Dit stelt je in staat om een pad te berekenen door specifieke fysieke blokkades, in plaats van dat de berekening volledig mislukt.

1.

Maak een [Anchored](/docs/nl-nl/reference/engine/classes/BasePart#Anchored)  onderdeel rond het object en stel de [CanCollide](/docs/nl-nl/reference/engine/classes/BasePart#CanCollide)  eigenschap in op false .

 ![Geankerd onderdeel dat een regio definieert om een padvindmodificator op toe te passen.](https://prod.docsiteassets.roblox.com/assets/avatar/pathfinding/DoorPassThrough-Block.jpg)

2.

Voeg een [PathfindingModifier](/docs/nl-nl/reference/engine/classes/PathfindingModifier)  instantie toe aan het onderdeel en schakel de [PassThrough](/docs/nl-nl/reference/engine/classes/PathfindingModifier#PassThrough)  eigenschap in.

 ![PathfindingModifier instantie met PassThrough eigenschap ingeschakeld.](https://prod.docsiteassets.roblox.com/assets/studio/properties/PathfindingModifier-PassThrough.png)

Nu, wanneer een pad wordt berekend van de zombie NPC naar het spelerkarakter, strekt het pad zich uit voorbij de deur en kun je de zombie aanmoedigen om deze te doorkruisen. Zelfs als de zombie de deur niet kan openen, reageert hij alsof hij "hoort" dat het karakter achter de deur is.

 ![Zombie NPC pad dat door de eerder blokkeren deur gaat.](https://prod.docsiteassets.roblox.com/assets/avatar/pathfinding/Zombie-Full-Path.jpg)

## [Padvindlinks](#padvindlinks)[](#padvindlinks)

Soms is het nodig om een pad te vinden over een ruimte die normaal niet kan worden overbrugd, zoals over een afgrond, en een aangepaste actie uit te voeren om het volgende waypoint te bereiken. Dit kan worden bereikt via het [PathfindingLink](/docs/nl-nl/reference/engine/classes/PathfindingLink)  object.

Met het voorbeeld hierboven kun je de agent een boot laten gebruiken.

 ![PathfindingLink die laat zien hoe een agent een boot kan gebruiken.](https://prod.docsiteassets.roblox.com/assets/avatar/pathfinding/PathfindingLink-Path.jpg)

Om een [PathfindingLink](/docs/nl-nl/reference/engine/classes/PathfindingLink)  te maken met dit voorbeeld:

1.

OPTIONEEL

 Zet Padvindlinks  aan vanuit de [Visualisatie-opties](/docs/nl-nl/studio/overview#visualisatie-opties)  widget in de rechterbovenhoek van het 3D-venster. Dit helpt bij visualisatie en debugging bij het implementeren van padvindlinks.

2.

Maak twee [Attachments](/docs/nl-nl/reference/engine/classes/Attachment) , één op de zitplaats van de boot en één nabij het landingspunt van de boot.

 ![Attachments gemaakt voor het begin en einde van de padvindlink.](https://prod.docsiteassets.roblox.com/assets/avatar/pathfinding/PathfindingLink-Attachments.jpg)

3.

Maak een [PathfindingLink](/docs/nl-nl/reference/engine/classes/PathfindingLink)  object in de workspace, en wijs vervolgens de [Attachment0](/docs/nl-nl/reference/engine/classes/PathfindingLink#Attachment0)  en [Attachment1](/docs/nl-nl/reference/engine/classes/PathfindingLink#Attachment1)  eigenschappen toe aan de start- en eindattachments respectievelijk.

 ![Attachment0/Attachment1 eigenschappen van een PathfindingLink.](https://prod.docsiteassets.roblox.com/assets/studio/properties/PathfindingLink-Attachments.png)  ![PathfindingLink gevisualiseerd in de 3D-wereld.](https://prod.docsiteassets.roblox.com/assets/avatar/pathfinding/PathfindingLink-In-World.jpg)

4.

Wijs een betekenisvolle naam zoals UseBoat  toe aan de [Label](/docs/nl-nl/reference/engine/classes/PathfindingLink#Label)  eigenschap. Deze naam wordt gebruikt als een vlag in het padvindscript om een aangepaste actie te activeren wanneer de agent het startlinkpunt bereikt.

 ![Label eigenschap gespecificeerd voor PathfindingLink.](https://prod.docsiteassets.roblox.com/assets/studio/properties/PathfindingLink-Label.png)

5.

Voeg een Costs  tabel toe binnen [CreatePath()](/docs/nl-nl/reference/engine/classes/PathfindingService#CreatePath)  met zowel een Water  sleutel als een aangepaste sleutel die overeenkomt met de [Label](/docs/nl-nl/reference/engine/classes/PathfindingLink#Label)  eigenschap naam. Wijs de aangepaste sleutel een waarde lager  toe dan die van Water .

PlayerPathFollow (LocalScript)

```

local PathfindingService = game:GetService("PathfindingService")

local Players = game:GetService("Players")

local RunService = game:GetService("RunService")

local DESTINATION = Vector3.new(20, 0.5, 20)

local GROUND_WAIT = 0.01

local VELOCITY_MULTIPLIER = 0.0625

local path = PathfindingService:CreatePath({

	AgentCanClimb = true,

	Costs = {

		UseBoat = 2, Water = 20

	}

})

```

6.

In de moveToNextWaypoint()  functie (

LIJNEN 93–114

), kan een aangepaste controle voor de [Label](/docs/nl-nl/reference/engine/classes/PathfindingLink#Label)  modificatornaam worden gebruikt om een andere actie dan [Humanoid:Move()](/docs/nl-nl/reference/engine/classes/Humanoid#Move)  uit te voeren; in dit geval kun je een functie aanroepen om de agent in de boot te laten zitten, de boot over het water te verplaatsen, de agent op het landingspunt van de boot te laten uitstappen, en vervolgens het pad van de agent naar zijn uiteindelijke bestemming voort te zetten.

## [Streamingcompatibiliteit](#streamingcompatibiliteit)[](#streamingcompatibiliteit)

In-game [instantie streaming](/docs/nl-nl/workspace/streaming)  is een krachtige functie die 3D-inhoud dynamisch laadt en ontlaadt terwijl het karakter van een speler zich door de wereld beweegt. Terwijl ze de 3D-ruimte verkennen, worden nieuwe subsets van de ruimte naar hun apparaat gestreamd en sommige van de bestaande subsets kunnen eruit gestreamd worden.

Overweeg de volgende best practices voor het gebruik van [PathfindingService](/docs/nl-nl/reference/engine/classes/PathfindingService)  in streaming-geactiveerde games:

-

Streaming kan een bepaald pad blokkeren of deblokkeren terwijl een karakter erlangs beweegt. Bijvoorbeeld, terwijl een karakter door een bos rent, kan er ergens voor hen een boom in streamen en het pad blokkeren. Om padvinden naadloos te laten werken met streaming, is het sterk aanbevolen om de [geblokkeerde paden](#geblokkeerde-paden)  techniek te gebruiken en het pad opnieuw te berekenen wanneer dat nodig is.

-

Een veelgebruikte aanpak in padvinden is om de coördinaten van bestaande objecten te gebruiken voor [berekening](#padberekening) , zoals het instellen van een padbestemming op de positie van een bestaand TreasureChest  model in de wereld. Deze aanpak is volledig compatibel met server-side [Scripts](/docs/nl-nl/reference/engine/classes/Script)  aangezien de server te allen tijde een volledig overzicht van de wereld heeft, maar [LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript)  en [ModuleScripts](/docs/nl-nl/reference/engine/classes/ModuleScript)  die op de client draaien, kunnen mislukken als ze proberen een pad te berekenen naar een object dat niet is gestreamd.

Om dit probleem aan te pakken, overweeg dan om de bestemming in te stellen op de positie van een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  binnen een [permanent](/docs/nl-nl/workspace/streaming#model-streamingcontroles)  model. Permanente modellen worden kort na het joinen van de speler geladen en ze worden nooit uitgestreamd, zodat een client-side script kan verbinden met de [PersistentLoaded](/docs/nl-nl/reference/engine/classes/Workspace#PersistentLoaded)  gebeurtenis en veilig toegang kan krijgen tot het model voor het creëren van waypoints nadat de gebeurtenis is afgevuurd.

## [Beperkingen en faalfactoren](#beperkingen-en-faalfactoren)[](#beperkingen-en-faalfactoren)

De padvindengine heeft specifieke beperkingen om efficiënte verwerking en optimale prestaties te waarborgen. Bovendien kunnen padvind [berekeningen](#padberekening)  om verschillende redenen mislukken, zoals hieronder beschreven.

Padverzoek te lang  — De directe lijn‑of‑zicht afstand voor padvinden van het start- naar het eindpunt mag niet meer dan 3.000 studs bedragen.

Nodebudget uitgeput  — Een padvindberekening kan meer dan 20.000 knooppunten overschrijden, lang voordat de afstandsgrens van 3.000 studs is bereikt, vooral bij padvinden in een uitgestrekte open wereld of door complexe doolhoven.

Incompatibele agentparameters  — Een padvindberekening zal mislukken als de [creatieparameters](#padcreatie)  niet kunnen worden opgelost. Bijvoorbeeld, als de bestemming alleen  kan worden bereikt door de agent te laten springen, maar AgentCanJump  is false , of AgentHeight  is groter dan de hoogte van een pad dat kan worden overbrugd.

Verticale waypointlimieten  — Padvindberekeningen houden alleen rekening met paden binnen een bepaalde verticale grens. Potentiële waypoints met een globale Y  coördinaat van minder dan -65.536  studs of groter dan 65.536  studs worden genegeerd.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
