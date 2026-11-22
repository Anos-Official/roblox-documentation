<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/fundamentals/coding-3/give-points -->

Else/if oefening met het geven van punten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. [Voorwaarden](/docs/nl-nl/tutorials/fundamentals/coding-3/landing)

# Else/if oefening met het geven van punten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Dit project zal gebruik maken van voorwaardelijke verklaringen om een onderdeel te creëren dat punten op een leaderboard geeft of aftrekt, afhankelijk van welke kleur het onderdeel heeft wanneer het wordt aangeraakt. Als het blauw is, krijgt de speler een paar punten. Als het groen is, krijgt de speler veel punten. Ten slotte, als het rood is, worden er punten afgetrokken.

## [Stel het project in](#stel-het-project-in)[](#stel-het-project-in)

Het puntgevende onderdeel kan aan elk project worden toegevoegd waar punten relevant zijn. Bijvoorbeeld, een avonturenspel waarin spelers punten verzamelen.

### [Punt tracking](#punt-tracking)[](#punt-tracking)

Om dit project op te zetten, heb je een leaderboard nodig om de punten bij te houden en een onderdeel dat van kleur verandert. De code voor het leaderboard zal worden verstrekt.

1.

Maak een nieuw script in ServerScriptService  met de naam Leaderboard. Kopieer en plak de onderstaande code in het script.

```

--In ServerScriptService, maak een script met de naam PlayerSetup met de onderstaande inhoud.

local Players = game:GetService("Players")

local function onPlayerJoin(player)

	local leaderstats = Instance.new("Folder")

	leaderstats.Name = "leaderstats"

	leaderstats.Parent = player

	-- Voorbeeld van een IntValue

	local points = Instance.new("IntValue")

	points.Name = "Points"

	points.Value = 0

	points.Parent = leaderstats

end

-- Voer onPlayerJoin uit wanneer het PlayerAdded-evenement wordt geactiveerd

Players.PlayerAdded:Connect(onPlayerJoin)

```

### [Kleurveranderend onderdeel](#kleurveranderend-onderdeel)[](#kleurveranderend-onderdeel)

Het script zal door drie verschillende kleuren voor het onderdeel cyclus. Elke kleur heeft een variabele om de RGB-waarde op te slaan, een gegevenstype dat een set van drie getallen (rood, groen, blauw) bevat die kleuren creëren.

1.

Maak een onderdeel met de naam PointPart met een bijgevoegd script met de naam PointScript.

2.

In PointScript, gebruik script.Parent  om naar het onderdeel te verwijzen.

```

local pointPart = script.Parent

```

3.

Maak variabelen aan om de verschillende kleuren op te slaan. Elke variabele moet worden ingesteld op [Color3.fromRGB()](/docs/nl-nl/reference/engine/datatypes/Color3#fromRGB) , wat een kleurwaarde creëert.

-

Blauw  (Enkele punten): (0, 0, 255)

-

Groen  (Veel punten): (0, 255, 0)

-

Rood  (Verlies punten): (255, 0, 0)

```

local pointPart = script.Parent

-- Kleuren

local blue = Color3.fromRGB(0, 0, 255)

local green = Color3.fromRGB(0, 255, 0)

local red = Color3.fromRGB(255, 0, 0)

```

4.

Voeg variabelen toe voor een klein aantal punten, een groter aantal punten en een derde voor het verwijderen van punten.

```

-- Kleuren

local blue = Color3.fromRGB(0, 0, 255)

local green = Color3.fromRGB(0, 255, 0)

local red = Color3.fromRGB(255, 0, 0)

-- Puntwaarden

local smallPoints = 10

local largePoints = 50

local losePoints = 100

```

### [Voeg de spelersservice toe](#voeg-de-spelersservice-toe)[](#voeg-de-spelersservice-toe)

Om punten toe te kennen, moet je toegang krijgen tot de informatie van de speler die is opgeslagen in de Explorer onder Spelers, en die is gescheiden van het karakterobject. Hier kunnen informatie zoals leaderboard-statistieken worden gevonden.

Je kunt dit doen door de Players -service aan je script toe te voegen. Services  zijn extra sets van vooraf gebouwde functies die door Roblox-engineers zijn gemaakt om je tijd te besparen.

1.

Verkrijg de Players -service door te typen:

local Players = game:GetService("Players")

```

-- Puntwaarden

local smallPoints = 10

local largePoints = 50

local losePoints = 100

-- Benodigde services

local Players = game:GetService("Players")

```

### [Functies en evenementen](#functies-en-evenementen)[](#functies-en-evenementen)

PointsScript heeft twee functies nodig. De eerste functie zal punten geven en aftrekken. De tweede functie zal controleren of een speler het onderdeel heeft aangeraakt. Deze functies zullen vervolgens worden verbonden met een aanraakgebeurtenis, die wordt uitgevoerd telkens wanneer dat onderdeel wordt aangeraakt.

1.

Maak een nieuwe functie met de naam givePoints()  en een parameter met de naam player . Voeg binnenin een printstatement toe voor testdoeleinden.

```

local Players = game:GetService("Players")

-- Geeft of trekt punten af

local function givePoints(player)

	print("Geef speler punten")

end

```

2.

Onder dat, maak een tweede functie met de naam partTouched()  met een parameter met de naam otherPart .

```

-- Geeft of trekt punten af

local function givePoints(player)

	print("Geef speler punten")

end

-- Controleert of de speler het onderdeel heeft aangeraakt

local function partTouched(otherPart)

end

```

3.

Binnen de functie, gebruik de functie GetPlayerFromCharacter()  om te controleren of er een speler in de otherPart-variabele is.

```

-- Controleert of de speler het onderdeel heeft aangeraakt

local function partTouched(otherPart)

	local player = Players:GetPlayerFromCharacter(otherPart.Parent)

end

```

4.

Als een speler het onderdeel heeft aangeraakt, wordt deze opgeslagen in de player-variabele. Zo niet, dan blijft de variabele leeg. Op eigen gelegenheid:

-

Controleer binnen de functie of de speler een waarde heeft. Als dat zo is, roep dan givePoints(player)  aan.

-

Onder de functie, verbind partTouched()  met het Touched-evenement van pointPart .

```

-- Controleert of de speler het onderdeel heeft aangeraakt

local function partTouched(otherPart)

	-- Krijgt de speler als iemand het onderdeel heeft aangeraakt

	local player = Players:GetPlayerFromCharacter(otherPart.Parent)

	if player then

		givePoints(player)

	end

end

pointPart.Touched:Connect(partTouched)

```

5.

Voer  het project uit. Telkens wanneer een speler het onderdeel aanraakt, zou je een bericht in het Output-venster moeten zien met de tekst: "Geef speler punten"

Probleemoplossingstips:

-

Controleer of "Players"  in game:GetService("Players")  met hoofdletters is geschreven en tussen aanhalingstekens staat.

-

partTouched()  moet zijn verbonden met het Touched -evenement van pointPart.

## [Maak kleurcycli](#maak-kleurcycli)[](#maak-kleurcycli)

Om door kleuren te cyclusen, zal het script een while-loop gebruiken die de kleur van het onderdeel elke paar seconden verandert. De voorwaarde voor deze loop zal waar zijn, zodat deze oneindig kan draaien.

1.

Aan het einde van het script, maak een nieuwe while-loop waar de voorwaarde waar is, wat betekent dat de loop altijd draait.

```

-- Controleert of de speler het onderdeel heeft aangeraakt

local function partTouched(otherPart)

	-- Krijgt de speler als iemand het onderdeel heeft aangeraakt

	local player = Players:GetPlayerFromCharacter(otherPart.Parent)

	if player then

		givePoints(player)

	end

end

pointPart.Touched:Connect(partTouched)

-- Loopt door kleuren

while true do

end

```

Als de while true do-loop niet onderaan het script staat, zal elke code daaronder nooit worden uitgevoerd. Aangezien de while-loop niet stopt, blijft deze de loop uitvoeren in plaats van de code daaronder.

2.

Op eigen gelegenheid, codeer een while true do-loop die pointPart verandert in de kleurvariabelen die je hebt gemaakt. Vergeet niet om [task.wait()](/docs/nl-nl/reference/engine/libraries/task#wait)  tussen de kleuren te gebruiken. Wanneer je klaar bent, controleer je code dan tegen de onderstaande versie.

```

-- Loopt door 3 kleuren, wacht tussen elke kleur

while true do

	pointPart.Color = blue

	task.wait(3)

	pointPart.Color = green

	task.wait(2)

	pointPart.Color = red

	task.wait(1)

end

```

3.

Speeltest en controleer of alle drie de kleuren zonder onderbreking cyclusen.

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-3/colorPoint_loopingColors.gif)

### [Probleemoplossingstips](#probleemoplossingstips)[](#probleemoplossingstips)

Op dit punt, als de kleurcyclus niet werkt zoals bedoeld, probeer dan een van de onderstaande opties.

-

Controleer of de while-loop aan de onderkant  van het script staat, onder het Touched-evenement. Als de loop niet onderaan staat, voorkomt dit dat andere delen van het script correct worden uitgevoerd.

-

Controleer of elke kleur binnen [Color3.fromRGB()](/docs/nl-nl/reference/engine/datatypes/Color3#fromRGB)  correct is geschreven. Er moeten drie getallen tussen 0 en 255 zijn, gescheiden door komma's, zoals (255, 50, 0) .

## [Geef spelers punten](#geef-spelers-punten)[](#geef-spelers-punten)

Spelers krijgen punten op basis van de huidige kleur van het onderdeel wanneer ze het aanraken.

### [Vind de huidige kleur](#vind-de-huidige-kleur)[](#vind-de-huidige-kleur)

Telkens wanneer een speler het onderdeel aanraakt, moet het script de huidige kleur van het onderdeel weten om later punten toe te kennen.

1.

Zoek givePoints() . Vervang je testbericht door een variabele voor de huidige kleur van pointPart. Deze variabele bepaalt hoeveel punten de speler krijgt (of verliest).

```

local function givePoints(player)

	local currentColor = pointPart.Color

end

```

2.

Om de punten van een speler te beïnvloeden, heeft die functie toegang nodig tot het leaderboard van de speler. Maak een variabele aan om het op te slaan.

```

local function givePoints(player)

	local currentColor = pointPart.Color

	local playerStats = player:WaitForChild("leaderstats")

end

```

3.

Voeg nu een variabele toe om de waarde van de punten van de speler te krijgen, die een kind is van hun leaderboard.

```

local function givePoints(player)

	local currentColor = pointPart.Color

	local playerStats = player:WaitForChild("leaderstats")

	local playerPoints = playerStats:WaitForChild("Points")

end

```

### [Geef of trek punten af](#geef-of-trek-punten-af)[](#geef-of-trek-punten-af)

Vervolgens gebruik je if en elseif om punten toe te kennen of af te trekken, afhankelijk van de kleur van het onderdeel wanneer het wordt aangeraakt. Vergeet niet dat blauw een klein aantal punten geeft, groen veel punten geeft en rood punten aftrekt.

1.

Binnen givePoints() , onder de variabelen, gebruik een if-verklaring om te controleren of de huidige kleur blauw is en als dat zo is, voeg dan smallPoints  toe aan de huidige puntenwaarde van de speler.

```

local function givePoints(player)

	local currentColor = pointPart.Color

	local playerStats = player:WaitForChild("leaderstats")

	local playerPoints = playerStats:WaitForChild("Points")

	if currentColor == blue then

		playerPoints.Value += smallPoints

	end

end

```

2.

Om voor groen te controleren, voeg een else if-voorwaarde toe. Als het groen is, voeg dan de largePoints -variabele toe aan de punten van de speler.

```

if currentColor == blue then

	playerPoints.Value += smallPoints

elseif currentColor == green then

	playerPoints.Value += largePoints

end

```

3.

Gebruik een else-verklaring om punten af te trekken als pointsPart noch blauw noch groen was.

```

if currentColor == blue then

	playerPoints.Value += smallPoints

elseif currentColor == green then

	playerPoints.Value += largePoints

else

	playerPoints.Value -= losePoints

end

```

4.

Tot slot, vernietig  het onderdeel na de if-verklaring, zodat het script geen punten meer kan geven.

```

if currentColor == blue then

	playerPoints.Value += smallPoints

elseif currentColor == green then

	playerPoints.Value += largePoints

else

	playerPoints.Value -= losePoints

end

pointPart:Destroy()

```

5.

Speeltest en controleer of elke kleur punten geeft zoals verwacht. Zorg ervoor dat je alle drie  voorwaarden test.

## [Geef spelers feedback](#geef-spelers-feedback)[](#geef-spelers-feedback)

Het PointPart werkt, maar spelers merken misschien niet op dat er iets is gebeurd, tenzij ze toevallig naar hun leaderboard kijken. Los dit op door deeltjes te creëren wanneer het PointPart wordt vernietigd.

Feedback toevoegen wanneer spelers een onderdeel gebruiken, zoals geluiden, schokken of deeltjes, maakt interacties met objecten bevredigender voor spelers.

### [Maak een deeltjes effect](#maak-een-deeltjes-effect)[](#maak-een-deeltjes-effect)

Het deeltjes effect zal dezelfde kleur hebben als het onderdeel wanneer het wordt aangeraakt. Aangezien de kleuren in variabelen zijn opgeslagen, is het gemakkelijk om ze opnieuw te gebruiken.

1.

In givePoints()  aan de onderkant, maak een nieuwe ParticleEmitter  instantie. Zorg ervoor dat de naam van de instantie precies zo is gespeld als weergegeven.

```

local particle = Instance.new("ParticleEmitter")

end

```

2.

ParticleEmitters gebruiken kleursequenties om hun kleur-eigenschap te regelen. Maak een nieuwe ColorSequence en geef de huidige kleur van het onderdeel door.

```

-- Vernietig onderdeel

pointPart:Destroy()

-- Maak deeltjes

local particle = Instance.new("ParticleEmitter")

particle.Color = ColorSequence.new(currentColor)

```

3.

De deeltjes moeten aan de speler die het heeft aangeraakt worden gekoppeld. Maak een variabele aan om het karaktermodel van de speler te krijgen. Koppel vervolgens de deeltjes aan het hoofd van de speler.

```

local particle = Instance.new("ParticleEmitter")

particle.Color = ColorSequence.new(currentColor)

local playerCharacter = player.Character

particle.Parent = playerCharacter:WaitForChild("Head")

```

4.

Gebruik [task.wait()](/docs/nl-nl/reference/engine/libraries/task#wait)  voor een snelle seconde, en vernietig dan de deeltjes.

```

local particle = Instance.new("ParticleEmitter")

particle.Color = ColorSequence.new(currentColor)

local playerCharacter = player.Character

particle.Parent = playerCharacter:WaitForChild("Head")

task.wait(1)

particle:Destroy()

```

5.

Speeltest het spel en zorg ervoor dat de deeltjes kort de speler volgen na het aanraken van elke kleur.

### [Probleemoplossingstips](#probleemoplossingstips-1)[](#probleemoplossingstips-1)

Op dit punt, als de deeltjes niet werken zoals bedoeld, probeer dan een van de onderstaande opties.

-

Zorg ervoor dat bij het maken van een nieuwe instantie ParticleEmitter precies zo is gespeld als weergegeven en tussen aanhalingstekens staat.

-

Zorg ervoor dat je :  gebruikt tussen playerCharacter  en WaitForChild()  zonder spaties ertussen bij het koppelen van de deeltjes.

## [Voltooi PointScript](#voltooi-pointscript)[](#voltooi-pointscript)

Een voltooide versie van het script kan hieronder worden geraadpleegd.

```

local pointPart = script.Parent

--local storage = game:GetService("ServerStorage")

-- Geeft enkele punten

local blue = Color3.fromRGB(0, 0, 255)

-- Geeft meer punten

local green = Color3.fromRGB(0, 255, 0)

-- Laat spelers punten verliezen

local red = Color3.fromRGB(255, 0, 0)

-- goud gegeven aan spelers

local smallPoints = 10

local largePoints = 50

local losePoints = 100

local Players = game:GetService("Players")

local function givePoints(player)

	local currentColor = pointPart.Color

	local playerStats = player:WaitForChild("leaderstats")

	local playerPoints = playerStats:WaitForChild("Points")

	-- Geeft de speler goud op basis van de kleur van het onderdeel

	if currentColor == blue then

		playerPoints.Value += smallPoints

	elseif currentColor == green then

		playerPoints.Value += largePoints

	else

		playerPoints.Value -= losePoints

	end

	-- Vernietig het onderdeel, wacht een seconde en vernietig dan het deeltje

	pointPart:Destroy()

	-- Creëert een sprankeleffect en vernietigt het

	local playerCharacter = player.Character

	local particle = Instance.new("ParticleEmitter")

	particle.Color = ColorSequence.new(currentColor)

	particle.Parent = playerCharacter:WaitForChild("Head")

	task.wait(1)

	particle:Destroy()

end

local function partTouched(otherPart)

	local player = Players:GetPlayerFromCharacter(otherPart.Parent)

	if player then

		givePoints(player)

	end

end

pointPart.Touched:Connect(partTouched)

-- Verandert de kleur van het onderdeel op basis van variabelen. Moet onderaan het script staan.

while true do

	pointPart.Color = blue

	task.wait(4)

	pointPart.Color = green

	task.wait(3)

	pointPart.Color = red

	task.wait(2)

end

```

[Volgende](/docs/nl-nl/tutorials/fundamentals/coding-4/landing)[Vorige](/docs/nl-nl/tutorials/fundamentals/coding-3/multiple-conditions)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
