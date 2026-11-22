<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/scripting/basic-scripting/score-points -->

Punten scoren | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Scripting
6. /
7. Basisspel

# Punten scoren

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

In eerdere tutorials heb je een verscheidenheid aan game-functies gemaakt, waaronder [vervagende platforms](/docs/nl-nl/tutorials/use-case-tutorials/scripting/basic-scripting/fading-trap)  en [dodelijke lava](/docs/nl-nl/tutorials/use-case-tutorials/scripting/basic-scripting/deadly-lava) . Deze tutorial verbindt deze elementen tot een speelbare game waarin gebruikers zien wie het langst kan overleven. Elke seconde dat ze in leven blijven, wordt er een punt aan hun score toegevoegd.

## [Opzetten](#opzetten)[](#opzetten)

Als eerste moet je de scène voor je game instellen. Dupliceer de [vervagende platforms](/docs/nl-nl/tutorials/use-case-tutorials/scripting/basic-scripting/fading-trap)  die je in de vorige tutorial hebt gemaakt en laat gebruikers strijden om zo lang mogelijk op het bord van platforms te blijven.

Je kunt ook [dodelijke lava](/docs/nl-nl/tutorials/use-case-tutorials/scripting/basic-scripting/deadly-lava)  gebruiken om gebruikers te doden wanneer ze van de platforms vallen, of ze gewoon naar hun ondergang laten vallen. Zorg ervoor dat je een SpawnLocation  plaatst op een plek waar gebruikers op de platforms kunnen springen om te beginnen met spelen.

![Spawnpunt boven een raster van vervagende platforms, boven een lavavloer](https://prod.docsiteassets.roblox.com/assets/tutorials/scoring-points/sceneInPlace.jpg)

## [Speler punten](#speler-punten)[](#speler-punten)

Roblox heeft een ingebouwde Leaderboard  voor het tonen van gebruikersstatistieken. Wanneer je spelerpunten via het leaderboard instelt, verschijnen ze aan de rechterkant van het scherm in de game.

 ![Leaderboard met gebruikersnaam en getoonde punten](https://prod.docsiteassets.roblox.com/assets/tutorials/scoring-points/leaderboard.jpg)

Je leert meer aanpasbare manieren om informatie weer te geven in latere tutorials, maar het leaderboard is de eenvoudigste manier om een zichtbaar scoringssysteem in Roblox te maken.

Het is het beste om scripts die de game-status instellen in ServerScriptService  te plaatsen, omdat ze automatisch worden uitgevoerd wanneer de game begint. Maak in ServerScriptService  een script genaamd SetupPoints .

 ![SetupPoints-script in plaats in ServerScriptService in het Explorer-venster](https://prod.docsiteassets.roblox.com/assets/tutorials/scoring-points/setupPointsScript.jpg)

## [Luister naar spelers](#luister-naar-spelers)[](#luister-naar-spelers)

In Roblox is een service  een object dat een reeks nuttige functies uitvoert. De [Players](/docs/nl-nl/reference/engine/classes/Players)  service heeft een gebeurtenis genaamd [PlayerAdded](/docs/nl-nl/reference/engine/classes/Players#PlayerAdded)  die je kunt gebruiken om punten in te stellen voor elke gebruiker die de game binnenkomt.

Je kunt toegang krijgen tot services met de [GetService](/docs/nl-nl/reference/engine/classes/ServiceProvider#GetService)  functie in het [game](/docs/nl-nl/reference/engine/classes/DataModel)  object. [game](/docs/nl-nl/reference/engine/classes/DataModel)  is een variabele die overal toegankelijk is en alles in je game bevat.

1.

Maak een variabele voor de Players-service met game:GetService("Players") .

2.

Maak een functie genaamd onPlayerAdded  met een parameter voor de binnenkomende speler.

3.

Verbind de onPlayerAdded  functie met de PlayerAdded-gebeurtenis.

```

local Players = game:GetService("Players")

local function onPlayerAdded(player)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Wanneer je een variabele declareert om een service te bevatten, is het het beste om deze de exacte naam van de service te geven ("Players" ), ook al betekent dit dat je gebruikelijke naamgevingsconventies voor variabelen moet doorbreken.

## [Maak een statistiekenmap](#maak-een-statistiekenmap)[](#maak-een-statistiekenmap)

Om de punten van een gebruiker in het leaderboard weer te geven, hoef je alleen maar een nieuwe [Folder](/docs/nl-nl/reference/engine/classes/Folder)  te maken in hun [Player](/docs/nl-nl/reference/engine/classes/Player)  object genaamd "leaderstats"  en hun punten daar in te plaatsen. Nieuwe objecten kunnen vanuit een script worden gemaakt via de [Instance.new()](/docs/nl-nl/reference/engine/datatypes/Instance#new)  functie.

1.

Maak een nieuw Folder  object met Instance.new("Folder") , en sla het resultaat op in een nieuwe variabele genaamd leaderstats .

```

local function onPlayerAdded(player)

	local leaderstats = Instance.new("Folder")

end

```

2.

Stel de Name-eigenschap van leaderstats  in op "leaderstats" .

3.

Parent leaderstats  aan player .

```

local Players = game:GetService("Players")

local function onPlayerAdded(player)

	local leaderstats = Instance.new("Folder")

   leaderstats.Name = "leaderstats"

   leaderstats.Parent = player

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Zorg ervoor dat je de map exact  de naam geeft zoals hier getoond ("leaderstats" ) of het zal niet werken!

## [Maak de punten](#maak-de-punten)[](#maak-de-punten)

Het leaderboard-systeem leest alle waarden in de leaderstats  map en toont wat het vindt.

Om een statistiek toe te voegen die de punten van een speler bijhoudt, kan een nieuw IntValue  object aan de leaderstats  map worden toegevoegd. De naam van het waarde-object wordt weergegeven naast de huidige waarde.

1.

Gebruik een variabele genaamd points  om een nieuw IntValue  object te maken met [Instance.new()](/docs/nl-nl/reference/engine/datatypes/Instance#new) .

2.

Stel de Name  in op "Points" .

3.

Stel de Value  in op 0 ; dit is wat het leaderboard aanvankelijk voor de speler zal weergeven.

4.

Parent het points  object aan de leaderstats  map.

```

local Players = game:GetService("Players")

local function onPlayerAdded(player)

  local leaderstats = Instance.new("Folder")

  leaderstats.Name = "leaderstats"

  leaderstats.Parent = player

  local points = Instance.new("IntValue")

  points.Name = "Points"

  points.Value = 0

  points.Parent = leaderstats

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Test je game en je zou het leaderboard in de rechterbovenhoek moeten zien met de namen van je gebruikers en een puntenscore ernaast.

## [Tel de tijd](#tel-de-tijd)[](#tel-de-tijd)

Elke gebruiker zou een punt moeten verdienen voor elke seconde dat ze in leven zijn. Een while  loop en de [task.wait()](/docs/nl-nl/reference/engine/libraries/task#wait)  functie kunnen worden gebruikt om de waarde van de punten elke seconde bij te werken.

1.

Maak aan het einde van het script een while  loop met true  als voorwaarde.

2.

In de loop, [task.wait()](/docs/nl-nl/reference/engine/libraries/task#wait)  voor 1 seconde.

```

Players.PlayerAdded:Connect(onPlayerAdded)

while true do

  task.wait(1)

end

```

## [Spelerslijst](#spelerslijst)[](#spelerslijst)

Om code voor elke gebruiker in de game uit te voeren, moet je door de array  van gebruikers itereren die wordt geretourneerd door de [GetPlayers](/docs/nl-nl/reference/engine/classes/Players#GetPlayers)  functie.

Een array is een lijst van items die in volgorde zijn opgeslagen. Elk item kan worden benaderd via zijn index  positie, beginnend vanaf 1 . Je kunt de lengte van een array krijgen door deze voor te plaatsen met # .

1.

Sla het resultaat van [Players:GetPlayers()](/docs/nl-nl/reference/engine/classes/Players#GetPlayers)  op in een playerList  variabele.

2.

Maak een for  loop met een startwaarde van 1 en een eindwaarde van #playerList , zodat je één iteratie van de loop per speler krijgt.

```

while true do

  task.wait(1)

  local playerList = Players:GetPlayers()

  for currentPlayer = 1, #playerList do

    -- Voeg hier je logica toe voor elke speler in de playerList

  end

end

```

## [Ken punten toe](#ken-punten-toe)[](#ken-punten-toe)

Om een punt toe te kennen aan elke gebruiker in de for-loop, moet je de gebruiker uit de array halen en 1 toevoegen aan het Points  object dat in hun leaderstats  map is opgeslagen.

Objecten die in een array zijn opgeslagen, worden benaderd met vierkante haken  - bijvoorbeeld, het eerste item in de playerList  array kan worden benaderd met playerList[1] . Als je playerList[currentPlayer]  in de for-loop schrijft, kun je met elke iteratie van de loop door elke gebruiker in de lijst bewegen.

1.

Sla de gebruiker op bij playerList[currentPlayer]  in een variabele genaamd player .

2.

Sla het Points  object van de gebruiker op in een variabele genaamd points .

3.

Stel de [Value](/docs/nl-nl/reference/engine/classes/IntValue#Value)  eigenschap van points  in op points.Value + 1 .

```

while true do

  task.wait(1)

  local playerList = Players:GetPlayers()

  for currentPlayer = 1, #playerList do

    local player = playerList[currentPlayer]

    local points = player.leaderstats.Points

    points.Value += 1

  end

end

```

Test je game en je zou moeten zien dat het leaderboard de score van je speler elke seconde met 1 laat toenemen.

## [Luister naar personages](#luister-naar-personages)[](#luister-naar-personages)

Het doel van de game is om te zien wie het langst kan overleven, dus gebruikers die sterven moeten hun punten teruggezet krijgen naar 0.

Je moet het Character  model van de gebruiker krijgen om te detecteren wanneer ze zijn gestorven. Dit model wordt alleen aan de game toegevoegd * nadat*  het [Player](/docs/nl-nl/reference/engine/classes/Player)  object is geladen en je kunt de [CharacterAdded](/docs/nl-nl/reference/engine/classes/Player#CharacterAdded)  gebeurtenis gebruiken om te luisteren wanneer het karakter klaar is voor gebruik. Maak een functie genaamd onCharacterAdded  met twee parameters: één voor het karakter, één voor de speler.

```

local Players = game:GetService("Players")

local function onCharacterAdded(character, player)

end

local function onPlayerAdded(player)

  local leaderstats = Instance.new("Folder")

```

Hoewel je de gebruiker in de parameters van de onCharacterAdded  functie hebt opgenomen, retourneert de daadwerkelijke [CharacterAdded](/docs/nl-nl/reference/engine/classes/Player#CharacterAdded)  gebeurtenis alleen het karakter, niet de bijbehorende gebruiker. Om het player  object ook door te geven, gebruik je een [anonieme functie](/docs/nl-nl/luau/functions#anonieme-functies)  voor de gebeurtenisverbinding.

```

local function onPlayerAdded(player)

  local leaderstats = Instance.new("Folder")

  leaderstats.Name = "leaderstats"

  leaderstats.Parent = player

  local points = Instance.new("IntValue")

  points.Name = "Points"

  points.Value = 0

  points.Parent = leaderstats

  player.CharacterAdded:Connect(function(character)

    onCharacterAdded(character, player)

  end)

end

```

## [Reset punten](#reset-punten)[](#reset-punten)

Wanneer een gebruiker sterft, activeert hun [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  automatisch een [Died](/docs/nl-nl/reference/engine/classes/Humanoid#Died)  gebeurtenis. Je kunt deze gebeurtenis gebruiken om te achterhalen wanneer je hun punten moet resetten.

De Humanoid bevindt zich binnen het Character-model, maar de inhoud van dat model wordt alleen samengesteld wanneer de gebruiker spawnt. Om je code veilig te laten wachten op het Humanoid-object om te laden, gebruik je de [WaitForChild()](/docs/nl-nl/reference/engine/classes/Instance#WaitForChild)  functie. Je kunt deze aanroepen op elk ouderobject, waarbij je de naam van het kind waar je op wacht als string doorgeeft. Maak een variabele om op de Humanoid te wachten met character:WaitForChild("Humanoid") .

```

local Players = game:GetService("Players")

local function onCharacterAdded(character, player)

  local humanoid = character:WaitForChild("Humanoid")

end

```

De functie die je moet verbinden met de Died-gebeurtenis is heel kort en zal hier alleen nodig zijn, dus je kunt opnieuw een anonieme functie gebruiken.

1.

Verbind een nieuwe anonieme functie met de Died  gebeurtenis van de Humanoid.

2.

In de anonieme functie, maak een variabele genaamd points  voor het Points  object van de speler.

3.

Stel de [Value](/docs/nl-nl/reference/engine/classes/IntValue#Value)  eigenschap van points  in op 0 .

```

local Players = game:GetService("Players")

local function onCharacterAdded(character, player)

  local humanoid = character:WaitForChild("Humanoid")

  humanoid.Died:Connect(function()

    local points = player.leaderstats.Points

    points.Value = 0

  end)

end

```

Test dit uit en je zult zien dat de score van de gebruiker reset wanneer ze sterven.

## [Controleer de speler](#controleer-de-speler)[](#controleer-de-speler)

Als gebruikers blijven punten verdienen, zelfs wanneer ze dood zijn, is dat niet in de geest van het spel, dus de code moet controleren of gebruikers in leven zijn voordat er een punt wordt toegekend.

Je moet beginnen met het definiëren van een attribuut  in de onPlayerAdded  functie dat kan worden gebruikt om te controleren of de gebruiker in leven is. Op dit moment is de gebruiker nog niet in leven en gespawned, omdat hun karaktermodel nog moet worden toegevoegd.

Attributen stellen je in staat om objecten in Roblox aan te passen met je eigen gegevens. Een attribuut bestaat uit een naam en een waarde. Je kunt er een maken op elk object met de [SetAttribute](/docs/nl-nl/reference/engine/classes/Instance#SetAttribute)  functie. Roep [SetAttribute](/docs/nl-nl/reference/engine/classes/Instance#SetAttribute)  aan op player  om een nieuw attribuut  genaamd "IsAlive"  met de waarde false  te creëren.

```

local function onPlayerAdded(player)

  local leaderstats = Instance.new("Folder")

  leaderstats.Name = "leaderstats"

  leaderstats.Parent = player

  local points = Instance.new("IntValue")

  points.Name = "Points"

  points.Value = 0

  points.Parent = leaderstats

  player:SetAttribute("IsAlive", false)

  player.CharacterAdded:Connect(function(character)

    onCharacterAdded(character, player)

  end)

end

```

Zodra het karaktermodel van de gebruiker respawnt, moet de waarde van IsAlive  worden veranderd in true  zodat de gebruiker weer punten kan gaan verdienen.

1.

In onCharacterAdded , stel het IsAlive  attribuut van player  in op true .

2.

In onCharacterDied , stel het IsAlive  attribuut van player  in op false .

```

local Players = game:GetService("Players")

local function onCharacterAdded(character, player)

  player:SetAttribute("IsAlive", true)

  local humanoid = character:WaitForChild("Humanoid")

  humanoid.Died:Connect(function()

    local points = player.leaderstats.Points

    points.Value = 0

    player:SetAttribute("IsAlive", false)

  end)

end

```

Ten slotte moet IsAlive  gecontroleerd  worden voordat er punten worden toegekend in de while  loop aan het einde van het script. De [GetAttribute](/docs/nl-nl/reference/engine/classes/Instance#GetAttribute)  functie neemt de naam van een attribuut en retourneert de waarde. In de while  loop, wikkel de code om een punt toe te kennen in een if  statement met de voorwaarde player:GetAttribute("IsAlive") .

```

while true do

  task.wait(1)

  local playerList = Players:GetPlayers()

  for currentPlayer = 1, #playerList do

    local player = playerList[currentPlayer]

    if player:GetAttribute("IsAlive") then

      local points = player.leaderstats.Points

      points.Value += 1

    end

  end

end

```

Test je game nu en je zou moeten zien dat de gebruiker elke seconde punten verdient zolang ze in leven zijn, en dat het op 0 blijft wanneer ze niet in leven zijn. Laat je vrienden met je meespelen en kijk wie de hoogste score kan behalen.

Dit is nog maar het begin: je kunt je game blijven verbeteren voor je gebruikers. Hier zijn enkele tips:

-

Plaats de code voor alle platforms in één script, waardoor het veel gemakkelijker wordt om bij te werken.

-

Maak een lobbygebied waar gebruikers wachten om naar het gamegebied te worden geteleporteerd, zodat gebruikers gelijktijdig kunnen beginnen.

-

Maak de winnaars van elke ronde bekend.

## [Eindcode](#eindcode)[](#eindcode)

```

local Players = game:GetService("Players")

local function onCharacterAdded(character, player)

  player:SetAttribute("IsAlive", true)

  local humanoid = character:WaitForChild("Humanoid")

  humanoid.Died:Connect(function()

    local points = player.leaderstats.Points

    points.Value = 0

    player:SetAttribute("IsAlive", false)

  end)

end

local function onPlayerAdded(player)

  local leaderstats = Instance.new("Folder")

  leaderstats.Name = "leaderstats"

  leaderstats.Parent = player

  local points = Instance.new("IntValue")

  points.Name = "Points"

  points.Value = 0

  points.Parent = leaderstats

  player:SetAttribute("IsAlive", false)

  player.CharacterAdded:Connect(function(character)

    onCharacterAdded(character, player)

  end)

end

Players.PlayerAdded:Connect(onPlayerAdded)

while true do

  task.wait(1)

  local playerList = Players:GetPlayers()

  for i = 1, #playerList do

    local player = playerList[i]

    if player:GetAttribute("IsAlive") then

      local points = player.leaderstats.Points

      points.Value += 1

    end

  end

end

```

[Vorige](/docs/nl-nl/tutorials/use-case-tutorials/scripting/basic-scripting/fading-trap)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
