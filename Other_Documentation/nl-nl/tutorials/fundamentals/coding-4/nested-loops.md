<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/fundamentals/coding-4/nested-loops -->

Geneste loops | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. [Loops](/docs/nl-nl/tutorials/fundamentals/coding-4/landing)

# Geneste loops

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Geneste loops stellen je in staat om taken in batches te herhalen. Bijvoorbeeld, het bakken van drie batches van zes cupcakes, of het toewijzen van wapens aan spelers in twee teams.

## [Hoe geneste loops werken](#hoe-geneste-loops-werken)[](#hoe-geneste-loops-werken)

Wanneer loops genest zijn, gaan scripts regel voor regel totdat ze de volgende loop bereiken. De binnenste loop zal draaien totdat aan de voorwaarde is voldaan voordat het terugkeert naar de buitenste loop.

### [Logica van geneste loops](#logica-van-geneste-loops)[](#logica-van-geneste-loops)

Het volgende diagram toont de stappen die een loop neemt.

|
-

Buitenste loop: code draait regel voor regel totdat het de binnenste loop bereikt.

-

Buitenste loop: code draait regel voor regel totdat het de binnenste loop bereikt.

-

Buitenste loop: code draait regel voor regel totdat het de binnenste loop bereikt.

 | | ![](https://prod.docsiteassets.roblox.com/assets/education/coding-4/NestedLoopsDiagram300x500.png) |
| --- | --- |

### [Voorbeeld van geneste loops](#voorbeeld-van-geneste-loops)[](#voorbeeld-van-geneste-loops)

Geneste loops kunnen enigszins abstract lijken, dus een visueel voorbeeld kan helpen. Voor deze oefening, kopieer en plak een voorbeeldscript en voer het uit in Studio. Dit script zal torens van onderdelen maken. De buitenste loop zal bepalen hoeveel onderdelen er gemaakt moeten worden, terwijl de binnenste loop de daadwerkelijke batch zal creëren.

1.

Maak een nieuw script in ServerScriptService  genaamd PartMaker. Kopieer de onderstaande code.

```

local numberOfBatches = 7

local partsPerBatch = 5

local partsMade = 0

-- Maakt een enkele kubus

local function createPart()

  local part = Instance.new("Part")

  part.Size = Vector3.new(2, 2, 2)

  part.CFrame = CFrame.new(20, 0, 20)

  part.Color = currentColor

  part.Parent = workspace

end

-- Buitenste loop

for partBatch = 1, numberOfBatches do

  print("Bovenste buitenste loop: part batch " .. partBatch)

  currentColor = Color3.fromRGB(math.random(0, 255), math.random(0, 255), math.random(0, 255))

  -- Binnenste loop

  for partNumber = 1, partsPerBatch do

    createPart()

    print("Binnenste loop: part " .. partNumber)

    partsMade += 1

    task.wait(0.5)

  end

  print("Onderste buitenste loop: " .. partsMade .. " onderdelen tot nu toe gemaakt.")

  task.wait(2)

end

```

2.

Kijk hoe het script een andere batch gekleurde onderdelen genereert. Na het doorlopen van een batch, pauzeert het 2 seconden. De print-instructie in de buitenste loop zal slechts één keer worden uitgevoerd per voltooide binnenste loop.

## [Geneste for loop toren](#geneste-for-loop-toren)[](#geneste-for-loop-toren)

Elke loop heeft zijn eigen set code, dus kan verantwoordelijk zijn voor verschillende taken. Een ding dat geneste loops kunnen doen, is de plaatsing veranderen waar een object verschijnt om een toren te creëren zoals in deze video. Er zijn drie verschillende loops, één voor het controleren waar langs de breedte, lengte en hoogte van de toren de kubus verschijnt.

## [Code een kubusmaker script](#code-een-kubusmaker-script)[](#code-een-kubusmaker-script)

Om te oefenen met geneste loops, maak je een script dat een toren van kubussen creëert. Voor het kubustoren script, codeer eerst een functie die een enkele kubus genereert. De toren zal worden gebouwd door deze functie herhaaldelijk aan te roepen.

### [Stel het script in](#stel-het-script-in)[](#stel-het-script-in)

Voor het kubustoren script, codeer eerst een functie die een enkele kubus genereert. De toren zal worden gebouwd door deze functie herhaaldelijk aan te roepen.

1.

Verwijder  het PartMaker script of schakel het uit (in de script-eigenschappen, vink Uitgeschakeld aan). Als je dat niet doet, zijn er twee scripts die tegelijkertijd onderdelen maken op dezelfde plaats.

2.

Maak een nieuw script genaamd TowerBuilder. Voeg variabelen voor torengrootte en kubusgrootte bovenaan toe.

```

local TOWER_SIZE = 4

local CUBE_SIZE = 2

```

Let op hoe de variabelen hierboven allemaal in hoofdletters zijn geschreven. Dit worden constanten  genoemd, of variabelen die niet veranderen. Om ze te onderscheiden van variabelen die binnen het script zullen worden gewijzigd, typ je ze met hoofdletters en underscores.

3.

Voeg een lokale functie genaamd makeCube()  toe die een enkele vierkante kubus maakt met behulp van CUBE_SIZE .

```

local TOWER_SIZE = 4

local CUBE_SIZE = 2

-- Maakt individuele kubussen

local function makeCube()

  local cube = Instance.new("Part")

  cube.Size = Vector3.new(CUBE_SIZE, CUBE_SIZE, CUBE_SIZE)

end

```

4.

Stel de kleur van de kubus in op een variabele die zal worden bijgewerkt in de geneste loops.

```

local function makeCube()

  local cube = Instance.new("Part")

  cube.Size = Vector3.new(CUBE_SIZE, CUBE_SIZE, CUBE_SIZE)

  cube.Color = currentColor

end

```

5.

Tot slot, parent  de nieuwe kubus aan de workspace zodat deze verschijnt.

```

local function makeCube()

    local cube = Instance.new("Part")

    cube.Size = Vector3.new(CUBE_SIZE, CUBE_SIZE, CUBE_SIZE)

    cube.Color = currentColor

    cube.Parent = workspace

end

```

In Roblox-code, zodra een object door een script is gemaakt, is het aan te raden om het aan het einde te parenten. Het is sneller om wijzigingen aan een instantie aan te brengen voordat er een fysiek object in de 3D-wereld is.

### [Spawnen in verschillende richtingen](#spawnen-in-verschillende-richtingen)[](#spawnen-in-verschillende-richtingen)

Om een toren te creëren, spawn je kubussen op specifieke punten door de X, Y, Z-eigenschappen van elke nieuwe kubus in te stellen. X en Z zijn zij aan zij. Y is omhoog en omlaag.

1.

In makeCube() , voeg parameters toe voor spawnX , spawnY , en spawnZ . Deze nummers zullen de spawnlocatie van elke nieuwe kubus instellen.

```

-- Maakt individuele kubussen

local function makeCube(spawnX, spawnY, spawnZ)

    local cube = Instance.new("Part")

    cube.Size = Vector3.new(CUBE_SIZE, CUBE_SIZE, CUBE_SIZE)

    cube.Color = currentColor

    cube.Parent = workspace

end

```

2.

Stel binnen de functie de CFrame-eigenschap van de kubus in op een nieuwe CFrame met behulp van de parameters spawnX , spawnY , spawnZ .

```

local function makeCube(spawnX, spawnY, spawnZ)

    local cube = Instance.new("Part")

    cube.Size = Vector3.new(CUBE_SIZE, CUBE_SIZE, CUBE_SIZE)

    cube.Color = currentColor

    cube.CFrame = CFrame.new(spawnX, spawnY, spawnZ)

    cube.Parent = workspace

end

```

In Roblox is CFrame een datatype dat wordt gebruikt om 3D-positie en oriëntatie op te slaan. Het wordt gebruikt om objecten in een wereld te plaatsen.

### [Spawnen met geneste loops](#spawnen-met-geneste-loops)[](#spawnen-met-geneste-loops)

Het script zal in totaal drie loops hebben, één voor de lengte, breedte en hoogte van de toren. Om een volledige verdieping te voltooien voordat je omhoog gaat, begin je met het instellen van de Y-coördinaat in de eerste, buitenste loop.

1.

Onder de makeCube()  functie, maak een for-loop om in te stellen hoe hoog  elke kubus spawnt.

-

Controlevariabele : heightIndex = 1

-

Eindpunt : TOWER_SIZE

-

Voeg binnen de loop toe: local spawnY = (heightIndex - 1) * CUBE_SIZE

```

-- Bouwt toren

for heightIndex = 1, TOWER_SIZE do

    local spawnY = (heightIndex - 1) * CUBE_SIZE

end

```

De berekening voor spawnY  zorgt ervoor dat de eerste kubus op grondhoogte spawnt en vervolgens over de ruimte van een enkele kubus beweegt elke keer. De grond is op niveau 0, wat de reden is dat 1 van de heightIndex  moet worden afgetrokken.

2.

Met de eerste loop voor hoogte voltooid, begin je met de tweede. Binnen de eerste for-loop, voeg een nieuwe for-loop toe voor waar de kubus langs de lengte van de toren moet worden geplaatst.

-

Controlevariabele : lengthIndex = 1

-

Eindpunt : TOWER_SIZE

-

Voeg binnen die loop toe: local spawnX = lengthIndex * CUBE_SIZE

```

for heightIndex = 1, TOWER_SIZE do

    local spawnY = (heightIndex - 1) * CUBE_SIZE

    for lengthIndex = 1, TOWER_SIZE do

        local spawnX = lengthIndex * CUBE_SIZE

    end

end

```

Bij het werken met geneste loops is het belangrijk om ervoor te zorgen dat de code goed is ingesprongen. Dit helpt om je code leesbaar en georganiseerd te houden.

3.

Binnen de tweede  loop, voeg een derde  for-loop toe voor de breedte  van de toren. In deze laatste loop, roep makeCube()  aan en geef de X, Y, Z parameters door.

-

Controlevariabele : widthIndex = 1

-

Eindpunt : TOWER_SIZE

-

Voeg binnen de loop toe:

-

local spawnZ = widthIndex * CUBE_SIZE

-

makeCube(spawnX, spawnY, spawnZ)

-

Een wachttijd van 0.25 zodat je kunt zien hoe de toren wordt gebouwd.

```

-- Bouwt toren

for heightIndex = 1, TOWER_SIZE do

    local spawnY = (heightIndex - 1) * CUBE_SIZE

    for lengthIndex = 1, TOWER_SIZE do

        local spawnX = lengthIndex * CUBE_SIZE

        for widthIndex = 1, TOWER_SIZE do

            local spawnZ = widthIndex * CUBE_SIZE

            makeCube(spawnX, spawnY, spawnZ)

            task.wait(0.25)

        end

    end

end

```

4.

Om elke verdieping een willekeurige kleur te geven, wijzig currentColor  naar willekeurige RGB -nummers in dezelfde loop waarin je een nieuwe verdieping creëert.

```

for heightIndex = 1, TOWER_SIZE do

    local spawnY = (heightIndex - 1) * CUBE_SIZE

    currentColor = Color3.fromRGB(math.random(0, 255), math.random(0, 255), math.random(0, 255))

    for lengthIndex = 1, TOWER_SIZE do

        local spawnX = lengthIndex * CUBE_SIZE

        for widthIndex = 1, TOWER_SIZE do

            local spawnZ = widthIndex * CUBE_SIZE

            makeCube(spawnX, spawnY, spawnZ)

            task.wait(0.25)

        end

    end

end

```

5.

Voer het project uit en wacht om te zien dat een volledige toren is gemaakt zonder fouten in het Output-venster.

## [Optionele uitdagingen](#optionele-uitdagingen)[](#optionele-uitdagingen)

Hieronder staan verschillende zelfgestuurde uitdagingen die geneste loops op verschillende manieren gebruiken. Probeer zelf te coderen voordat je naar de oplossing kijkt.

### [Onderdelen laten vervagen](#onderdelen-laten-vervagen)[](#onderdelen-laten-vervagen)

Terwijl de toren wordt gebouwd, laat de onderdelen vervagen in transparantie van links naar rechts.

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-4/Fade_480x320.png)

De codeoplossing is hieronder.

```

local TOWER_SIZE = 6

local CUBE_SIZE = 2

-- Maakt individuele kubussen

local function makeCube(spawnX, spawnY, spawnZ)

    local cube = Instance.new("Part")

    cube.Size = Vector3.new(CUBE_SIZE, CUBE_SIZE, CUBE_SIZE)

    cube.Color = currentColor

    cube.Transparency = cubeTransparency -- Stelt transparantie in

    cube.CFrame = CFrame.new(spawnX, spawnY, spawnZ)

    cube.Parent = workspace

end

-- Bouwt toren

for heightIndex = 1, TOWER_SIZE do

    local spawnY = (heightIndex - 1) * CUBE_SIZE

    currentColor = Color3.fromRGB(math.random(0, 255), math.random(0, 255), math.random(0, 255))

    for lengthIndex = 1, TOWER_SIZE do

        local spawnX = lengthIndex * CUBE_SIZE

	cubeTransparency = (lengthIndex - 1) * 0.10 --Updates elke loop beginnend bij 0

        for widthIndex = 1, TOWER_SIZE do

            local spawnZ = widthIndex * CUBE_SIZE

            makeCube(spawnX, spawnY, spawnZ)

            task.wait(0.05)

        end

    end

end

```

### [Objecten laten regenen](#objecten-laten-regenen)[](#objecten-laten-regenen)

In plaats van onderdelen, probeer een daadwerkelijk object te spawnen. Het voorbeeld hier gebruikte cupcakes.

Probeer zelf:

-

Een object te creëren van basisonderdelen. Zorg ervoor dat je alle onderdelen aan elkaar last zodat het object niet uit elkaar valt.

-

Plaats het object in ServerStorage

-

Wijzig de PartMaker die je vond in de [Geneste Loop Voorbeeld](#geneste-loop-voorbeeld)  om je object in plaats van onderdelen te gebruiken.

Een voorbeeld is hier getoond.

Een codeoplossing met cupcakes is inbegrepen.

```

local numberOfBatches = 30

local cupcakesPerBatch = 6

local cupcakesBaked = 0

--Maakt een enkele cupcake

local function makeCupcake()

    local ServerStorage = game:GetService("ServerStorage")

    local cupcake = ServerStorage.Cupcake:Clone()

    local cup = cupcake.Cup

    local frosting = cupcake.Frosting

    cupcake:SetPrimaryPartCFrame(CFrame.new(0, 20, 0) * CFrame.Angles(0, 0, -90))

    frosting.Color = frostingColor

    cup.Color = cupColor

    cupcake.Parent = workspace

end

-- Buitenste loop

for cupcakeBatch = 1, numberOfBatches do

    print("Bovenste buitenste loop: cupcake batch " .. cupcakeBatch)

    frostingColor = Color3.fromRGB(math.random(0, 255), math.random(0, 255), math.random(0, 255))

    cupColor = Color3.fromRGB(math.random(0, 255), math.random(0, 255), math.random(0, 255))

    -- Binnenste loop

    for cupcakeNumber = 1, cupcakesPerBatch do

        makeCupcake()

        print("Binnenste loop: cupcake " .. cupcakeNumber)

        -- Houdt bij hoeveel cupcakes zijn gebakken

        cupcakesBaked += 1

        task.wait(0.5)

    end

    print("Onderste buitenste loop: " .. cupcakesBaked .. " cupcakes tot nu toe gebakken.")

end

```

## [Samenvatting](#samenvatting)[](#samenvatting)

Om complexere taken uit te voeren, zullen programmeurs het nuttig vinden om meerdere loops te combineren, en zelfs verschillende soorten loops. Alle loops kunnen genest zijn, wat betekent dat de ene loop binnen de andere is. Geneste loops volgen dezelfde logica als elke andere loop. Het begint in de eerste, buitenste loop, voert taken uit via binnenste loops, en cycled dan terug naar de eerste loop indien van toepassing.

[Volgende](/docs/nl-nl/tutorials/fundamentals/coding-5/landing)[Vorige](/docs/nl-nl/tutorials/fundamentals/coding-4/create-a-timed-bridge)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
