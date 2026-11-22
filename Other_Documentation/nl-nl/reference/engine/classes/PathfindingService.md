<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/PathfindingService -->

PathfindingService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [PathfindingService](/docs/nl-nl/reference/engine/classes/PathfindingService)

Nederlands

Feedback

Engine-klasse

PathfindingService

Niet maakbaar

Service

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/PathfindingService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[EmptyCutoff](#EmptyCutoff) :[number](/docs/nl-nl/luau/numbers)

Verouderd

 |
| --- | --- |

Methoden

|

[ComputeRawPathAsync](#ComputeRawPathAsync) (start :  [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) , finish :  [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) , maxDistance :  [number](/docs/nl-nl/luau/numbers) ) :[Path](/docs/nl-nl/reference/engine/classes/Path)

Verouderd

 |
|

[ComputeSmoothPathAsync](#ComputeSmoothPathAsync) (start :  [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) , finish :  [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) , maxDistance :  [number](/docs/nl-nl/luau/numbers) ) :[Path](/docs/nl-nl/reference/engine/classes/Path)

Verouderd

 |
|

[CreatePath](#CreatePath) (agentParameters :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[Path](/docs/nl-nl/reference/engine/classes/Path)

 |
|

[FindPathAsync](#FindPathAsync) (start :  [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) , finish :  [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) ) :[Path](/docs/nl-nl/reference/engine/classes/Path)

Verouderd

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Het Gebruik van de Padvinding Service

```

local PathfindingService = game:GetService("PathfindingService")

local agentParams = {

	AgentRadius = 2.0,

	AgentHeight = 5.0,

	AgentCanJump = false,

}

local currentWaypointIdx = 1

local path = PathfindingService:CreatePath(agentParams)

local humanoidRootPart = script.Parent:FindFirstChild("HumanoidRootPart")

local targetPosition = Vector3.new(50, 0, 50)

path:ComputeAsync(humanoidRootPart.Position, targetPosition)

-- Wanneer het pad geblokkeerd is...

local function OnPathBlocked(blockedWaypointIdx)

	-- Controleer of het obstakel verderop in het pad ligt

	if blockedWaypointIdx > currentWaypointIdx then

		-- Herbereken het pad

		path:ComputeAsync(humanoidRootPart.Position, targetPosition)

		if path.Status == Enum.PathStatus.Success then

			-- Verkrijg de bijgewerkte waypointlijst met path:GetWaypoints()

			-- en Ga verder met lopen naar het doel

		else

			-- Fout, pad niet gevonden

		end

	end

end

path.Blocked:Connect(OnPathBlocked)

```

---

API-referentie

Eigenschappen

EmptyCutoff

Verouderd

Details weergeven

---

Methoden

ComputeRawPathAsync

Verouderd

Details weergeven

---

ComputeSmoothPathAsync

Verouderd

Details weergeven

---

CreatePath

Mogelijkheden: Basic

PathfindingService:CreatePath (agentParameters :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[Path](/docs/nl-nl/reference/engine/classes/Path)

Parameters

|

agentParameters :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Standaardwaarde: nil |

Teruggaves

[Path](/docs/nl-nl/reference/engine/classes/Path)

Codevoorbeelden

Een Pad Maken met de Pathfinding Service

```

local Workspace = game:GetService("Workspace")

local PathfindingService = game:GetService("PathfindingService")

-- Dit model bevat een start, eind en drie paden waar de speler op kan lopen: Sneeuw, Metaal en Bladgras

local PathOptionsModel = script.Parent.PathOptions

local startPosition = PathOptionsModel.Start.Position

local finishPosition = PathOptionsModel.End.Position

-- Maak een pad dat Sneeuw en Metaal materialen vermijdt

-- Dit zorgt ervoor dat het gemaakte pad de Sneeuw en Metaal paden vermijdt en de

-- gebruiker naar het Bladgras pad leidt

local path = PathfindingService:CreatePath({

	AgentRadius = 3,

	AgentHeight = 6,

	AgentCanJump = false,

	Costs = {

		Snow = math.huge,

		Metal = math.huge,

	},

})

-- Bereken het pad

local success, errorMessage = pcall(function()

	path:ComputeAsync(startPosition, finishPosition)

end)

-- Bevestig dat de berekening succesvol was

if success and path.Status == Enum.PathStatus.Success then

	-- Voor elk waypoint, maak een onderdeel om het pad te visualiseren

	for _, waypoint in path:GetWaypoints() do

		local part = Instance.new("Part")

		part.Position = waypoint.Position

		part.Size = Vector3.new(0.5, 0.5, 0.5)

		part.Color = Color3.new(1, 0, 1)

		part.Anchored = true

		part.CanCollide = false

		part.Parent = Workspace

	end

else

	print(`Pad kan niet worden berekend, fout: {errorMessage}`)

end

```

Feedback geven

---

FindPathAsync

Verouderd

Details weergeven

---

Ga naar

▼

PathfindingService

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[EmptyCutoff](#EmptyCutoff)

[Methoden](#methods)

[ComputeRawPathAsync()](#ComputeRawPathAsync)

[ComputeSmoothPathAsync()](#ComputeSmoothPathAsync)

[CreatePath()](#CreatePath)

[FindPathAsync()](#FindPathAsync)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
