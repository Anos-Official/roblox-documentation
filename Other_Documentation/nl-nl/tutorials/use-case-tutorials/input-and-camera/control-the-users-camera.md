<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/input-and-camera/control-the-users-camera -->

Beheer de camera van de gebruiker | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Input en camera

# Beheer de camera van de gebruiker

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het uitzicht van de gebruiker op de wereld wordt weergegeven door een [Camera](/docs/nl-nl/reference/engine/classes/Camera)  object. Je kunt het cameragedrag op verschillende manieren aanpassen aan jouw spel. Bijvoorbeeld, de camera kan reageren op gebeurtenissen in de wereld, zoals trillen wanneer een monster voorbijloopt, of vergrendeld zijn aan de zijkant van het personage van de gebruiker, zoals in een side-scroller.

## [Maak een first-person camera](#maak-een-first-person-camera)[](#maak-een-first-person-camera)

Een first-person camera is een weergave waarbij de camera vergrendeld blijft met het hoofd van het personage, wat nauwkeuriger is in vergelijking met het echte leven. Het is gebruikelijk in schiet- en verhaallijnen waar het doel is om de gebruiker zich ondergedompeld te laten voelen in de wereld.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/controlling-the-players-camera/FirstPersonCameraExample.jpg) First Person Camera

![](https://prod.docsiteassets.roblox.com/assets/tutorials/controlling-the-players-camera/ThirdPersonCameraExample.jpg) Classic Roblox Camera

In Studio bevat het [StarterPlayer](/docs/nl-nl/reference/engine/classes/StarterPlayer)  object een aantal eigenschappen die het cameragedrag van de gebruiker beïnvloeden. De CameraMode  eigenschap bepaalt hoe de camera zich gedraagt.

1.

Selecteer StarterPlayer .

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/controlling-the-players-camera/StarterPlayerSelection.png)

2.

Verander CameraMode in LockFirstPerson . Dit zorgt ervoor dat de camera van de gebruiker niet van hun hoofd weg beweegt.

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/controlling-the-players-camera/CameraModeProperty.png)

3.

Speel de test om de first-person camera in actie te zien.

Als je cursor vastzit in het midden van het scherm tijdens het testen, kun je je muis vrijmaken door op de Escape  toets te drukken of druk op Shift F5  om de test te beëindigen.

## [Maak een side-scrolling camera](#maak-een-side-scrolling-camera)[](#maak-een-side-scrolling-camera)

Een side-scrolling weergave houdt de camera op een vaste positie ten opzichte van de zijkant van het personage, waardoor de wereld een tweedimensionaal gevoel krijgt.

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/controlling-the-players-camera/SidescrollingCameraExample.jpg)

### [Script de camera](#script-de-camera)[](#script-de-camera)

1.

Breid StarterPlayer uit, en voeg in StarterPlayerScripts een LocalScript  toe met de naam CameraManager .

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/controlling-the-players-camera/CameraManagerScript.png)

2.

Kopieer en plak aan de bovenkant van het script de volgende code om de Players service  te verkrijgen, en verkrijg vervolgens in een nieuwe variabele de lokale gebruiker.

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

```

3.

Maak een functie genaamd updateCamera . Dit bevat de logica die nodig is om een nieuwe positie voor de camera te verkrijgen en in te stellen.

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local function updateCamera()

end

```

4.

Binnen de functie, verkrijg het karaktermodel van de gebruiker en controleer of het bestaat met behulp van een if-statement.

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local function updateCamera()

    local character = player.Character

    if character then

    end

end

```

Alleen een gebruiker kan hun eigen camera-configuratie zien, dus het wordt altijd vanuit een client-script bestuurd.

### [Richt de camera](#richt-de-camera)[](#richt-de-camera)

Alle karaktermodellen bevatten een onderdeel genaamd HumanoidRootPart , dat kan worden gebruikt om de positie van het karakter in de wereld te verkrijgen. Dit stelt de positie in waar de camera naar wijst.

1.

Gebruik FindFirstChild  om de HumanoidRootPart te verkrijgen en controleer of deze bestaat met behulp van een if-statement.

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local function updateCamera()

    local character = player.Character

    if character then

        local root = character:FindFirstChild("HumanoidRootPart")

        if root then

        end

    end

end

```

2.

De positie van de HumanoidRootPart is eigenlijk 2 studs onder het hoofd van de gebruiker. Om dit te verhelpen, voeg je een nieuwe [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  met een hoogte van 2 studs  toe aan de positie van de root.

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local HEIGHT_OFFSET = 2

local function updateCamera()

    local character = player.Character

    if character then

        local root = character:FindFirstChild("HumanoidRootPart")

        if root then

            local rootPosition = root.Position + Vector3.new(0, HEIGHT_OFFSET, 0)

        end

    end

end

```

Scheid individuele nummers in variabelen om ze later gemakkelijker aan te passen.

### [Stel de camera positie in](#stel-de-camera-positie-in)[](#stel-de-camera-positie-in)

De camera heeft ook een positie nodig. Om het uitzicht van de gebruiker een 2D side-scrolling uitstraling te geven, moet de camera direct naar de zijkant van het personage kijken. Plaats de camera aan de zijkant van de gebruiker door diepte toe te voegen aan alleen de Z-as  van de positie van de camera met behulp van een [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) .

```

local player = Players.LocalPlayer

local CAMERA_DEPTH = 24

local HEIGHT_OFFSET = 2

local function updateCamera()

    local character = player.Character

    if character then

        local root = character:FindFirstChild("HumanoidRootPart")

        if root then

            local rootPosition = root.Position + Vector3.new(0, HEIGHT_OFFSET, 0)

            local cameraPosition = Vector3.new(rootPosition.X, rootPosition.Y, CAMERA_DEPTH)

        end

    end

end

```

### [Update CurrentCamera](#update-currentcamera)[](#update-currentcamera)

Nu de variabelen voor de positie van de camera en het doel van de camera klaar zijn, is het tijd om de positie van de camera bij te werken. Je kunt de camera van de gebruiker benaderen via de CurrentCamera  eigenschap van Workspace. De camera heeft een [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  eigenschap om zijn positie te bepalen.

Je kunt [CFrame.lookAt()](/docs/nl-nl/reference/engine/datatypes/CFrame#lookAt)  gebruiken om de camera bij te werken. Het neemt twee posities en creëert een CFrame dat zich op de eerste positie bevindt en naar de tweede wijst. Gebruik [CFrame.lookAt()](/docs/nl-nl/reference/engine/datatypes/CFrame#lookAt)  om een CFrame te creëren dat is gepositioneerd op cameraPosition  en gericht is naar rootPosition .

```

local player = Players.LocalPlayer

local camera = workspace.CurrentCamera

local CAMERA_DEPTH = 24

local HEIGHT_OFFSET = 2

local function updateCamera()

    local character = player.Character

    if character then

        local root = character:FindFirstChild("HumanoidRootPart")

        if root then

            local rootPosition = root.Position + Vector3.new(0, HEIGHT_OFFSET, 0)

            local cameraPosition = Vector3.new(rootPosition.X, rootPosition.Y, CAMERA_DEPTH)

            camera.CFrame = CFrame.lookAt(cameraPosition, rootPosition)

        end

    end

end

```

### [Synchroniseer de camera](#synchroniseer-de-camera)[](#synchroniseer-de-camera)

De laatste stap is om deze functie herhaaldelijk uit te voeren om de camera in sync te houden met de gebruiker. De afbeelding die de gebruiker ziet, wordt constant vernieuwd. De splitseconde die nodig is om alle berekeningen uit te voeren, wordt de render stap  genoemd.

[RunService:BindToRenderStep()](/docs/nl-nl/reference/engine/classes/RunService#BindToRenderStep)  maakt het eenvoudig om een functie bij elke frame uit te voeren door deze drie parameters te accepteren:

-

name  - De naam van deze binding, die uniek moet zijn zodat deze niet in conflict komt met andere functies met dezelfde naam.

-

priority  - Hoe hoger het nummer, hoe hoger de prioriteit. Deze functie moet na  de standaard camera-update van Roblox worden uitgevoerd, dus de prioriteit is ingesteld op 1 niveau hoger dan de RenderPriority van de interne camera.

-

function  - De functie die aan de render stap moet worden gebonden.

1.

Gebruik [RunService:BindToRenderStep()](/docs/nl-nl/reference/engine/classes/RunService#BindToRenderStep)  om de updateCamera  functie aan de render stap te binden.

```

local Players = game:GetService("Players")

local RunService = game:GetService("RunService")

local player = Players.LocalPlayer

local camera = workspace.CurrentCamera

local CAMERA_DEPTH = 24

local HEIGHT_OFFSET = 2

local function updateCamera()

    local character = player.Character

    if character then

        local root = character:FindFirstChild("HumanoidRootPart")

        if root then

            local rootPosition = root.Position + Vector3.new(0, HEIGHT_OFFSET, 0)

            local cameraPosition = Vector3.new(rootPosition.X, rootPosition.Y, CAMERA_DEPTH)

            camera.CFrame = CFrame.lookAt(cameraPosition, rootPosition)

        end

    end

end

RunService:BindToRenderStep("SidescrollingCamera", Enum.RenderPriority.Camera.Value + 1, updateCamera)

```

2.

Speel je code. Gebruik de A  en D  toetsen om je personage van links naar rechts te bewegen.

## [Maak een isometrische camera](#maak-een-isometrische-camera)[](#maak-een-isometrische-camera)

De basisstructuur van het verkrijgen van de positie van de gebruiker en het bijwerken van de positie van de camera elke frame kan worden aangepast aan veel andere camerastijlen, zoals een isometrische camera . Een isometrische camera is een 3D-weergave die iets naar beneden wijst onder een vaste hoek naar het personage van de gebruiker.

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/controlling-the-players-camera/IsometricCameraExample.jpg)

### [Wijzig positie en uitzicht](#wijzig-positie-en-uitzicht)[](#wijzig-positie-en-uitzicht)

1.

Gebruik de code van het vorige voorbeeld, wijzig cameraPosition  om dezelfde hoeveelheid aan alle 3 dimensies toe te voegen.

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/controlling-the-players-camera/VectorComponentDemonstration.jpg)

```

local function updateCamera()

    local character = player.Character

    if character then

        local root = character:FindFirstChild("HumanoidRootPart")

        if root then

            local rootPosition = root.Position + Vector3.new(0, HEIGHT_OFFSET, 0)

            local cameraPosition = rootPosition + Vector3.new(CAMERA_DEPTH, CAMERA_DEPTH, CAMERA_DEPTH)

            camera.CFrame = CFrame.lookAt(cameraPosition, rootPosition)

        end

    end

end

RunService:BindToRenderStep("IsometricCamera", Enum.RenderPriority.Camera.Value + 1, updateCamera)

```

2.

Het wijzigen van de [FieldOfView](/docs/nl-nl/reference/engine/classes/Camera#FieldOfView)  eigenschap van de camera simuleert het in- en uitzoomen, wat de weergave een platter uiterlijk kan geven. Probeer het in te stellen op een waarde van 20  om in te zoomen, en verhoog de afstand van de camera tot de gebruiker om dit te compenseren.

```

local Players = game:GetService("Players")

local RunService = game:GetService("RunService")

local player = Players.LocalPlayer

local camera = workspace.CurrentCamera

local CAMERA_DEPTH = 64

local HEIGHT_OFFSET = 2

camera.FieldOfView = 20

local function updateCamera()

```

Door de manier waarop de camera zich gedraagt te veranderen, kun je een geheel nieuwe uitstraling voor je spel bereiken. Kijk of je de cameraPosition  kunt veranderen om een top-down camera met hetzelfde script te bereiken. Probeer instellingen aan te passen om een resultaat te krijgen dat je leuk vindt!

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
