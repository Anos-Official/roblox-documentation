<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/fundamentals/coding-6/create-with-module-scripts -->

Maak met modulescripts | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. [Code ordenen](/docs/nl-nl/tutorials/fundamentals/coding-6/landing)

# Maak met modulescripts

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

![](https://prod.docsiteassets.roblox.com/assets/education/coding-6/creating-with-module-scripts/creating-modules-hero.jpeg)

Om je kennis van modulescripts toe te passen, maak je een modulescript waarmee spelers sleutels kunnen oppakken en deze kunnen gebruiken om schatkisten te openen.

## [Projectopzet](#projectopzet)[](#projectopzet)

Dit project bevat een startkaart met een leaderboard en gescripte ophaalobjecten voor de sleutels en schatkisten.

### [Laad het startproject](#laad-het-startproject)[](#laad-het-startproject)

1.

Download het startproject.

 [Downloaden](https://prod.docsiteassets.roblox.com/assets/education/coding-6/creating-with-module-scripts/Intro_to_Module_Scripts_-_Starter_Project.rbxl)

2.

Open in Roblox Studio het gedownloade bestand: Intro to Module Scripts - Starter Project.rbxl .

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-6/creating-with-module-scripts/module-template-example.jpeg)

### [Maak een modulescript](#maak-een-modulescript)[](#maak-een-modulescript)

Om ervoor te zorgen dat spelers schatten uit kisten kunnen krijgen, maak je een modulescript genaamd TreasureManager. Het gebruik van een modulescript verbindt de ophaalobjecten en leaderboards met elkaar.

1.

Maak in ServerStorage  een nieuwe ModuleScript  en hernoem deze naar TreasureManager .

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-6/creating-with-module-scripts/create-module-script.png)

2.

Hernoem in TreasureManager  de standaard module tabel door module  in beide plaatsen te vervangen door TreasureManager .

```

local TreasureManager = {}

return TreasureManager

```

## [Gebruik functies in modulescripts](#gebruik-functies-in-modulescripts)[](#gebruik-functies-in-modulescripts)

Om te testen hoe functies werken in modulescripts, maak je een nieuwe functie genaamd getKey() . Wanneer de getKey()  functie vanuit een ander script wordt aangeroepen, ontvangt deze een sleutelonderdeel om te vernietigen en voegt deze 1 toe aan het aantal sleutels in de inventaris van de speler.

### [Maak een modulefunctie voor sleutels](#maak-een-modulefunctie-voor-sleutels)[](#maak-een-modulefunctie-voor-sleutels)

1.

Dit modulescript zal een combinatie van module- en lokale functies gebruiken, typ twee  opmerkingen om je te helpen ze gescheiden te houden.

```

local TreasureManager = {}

------------------ Lokale Functies

------------------ Module Functies

return TreasureManager

```

2.

Onder de opmerking Module Functies , voeg een nieuwe modulefunctie toe aan TreasureManager  genaamd getKey() .

Gebruik twee parameters:

-

keyPart  - het onderdeel dat vernietigd moet worden.

-

whichCharacter  - de speler die het sleutelonderdeel aanraakte.

```

local TreasureManager = {}

------------------ Lokale Functies

------------------ Module Functies

function TreasureManager.getKey(keyPart, whichCharacter)

end

return TreasureManager

```

3.

In getKey() , vernietig keyPart .

```

function TreasureManager.getKey(keyPart, whichCharacter)

	keyPart:Destroy()

end

```

### [Gebruik de modulefunctie](#gebruik-de-modulefunctie)[](#gebruik-de-modulefunctie)

Nu kan de modulefunctie getKey()  in andere scripts worden gebruikt. Om die functie te testen, open je een vooraf gemaakt script en roep je het aan.

1.

Open het sleutelscript in Workspace  ⟩ Keys  ⟩ KeyScript .

2.

Sla in keyScript het modulescript op in een variabele genaamd treasureManager  en stel deze gelijk aan: require(ServerStorage:WaitForChild("TreasureManager"))

```

local ServerStorage = game:GetService("ServerStorage")

-- Vereis het modulescript hieronder ⯆

local treasureManager = require(ServerStorage:WaitForChild("TreasureManager"))

local keys = script.Parent

local keysFolder = keys.Parts

local keysArray = keysFolder:GetChildren()

```

Voorkom fouten door WaitForChild()  te gebruiken in plaats van de puntoperator om het script te laten wachten totdat TreasureManager  is geladen voordat het verder gaat. Voor scripts in ServerScriptService of ServerStorage is het veilig om in plaats daarvan de puntoperator te gebruiken, zoals in [ServerStorage.TreasureManager](/docs/nl-nl/reference/engine/classes/ServerStorage#TreasureManager) .

3.

Er is al een functie genaamd partTouched()  om te controleren of een speler het onderdeel aanraakt. Binnen partTouched() :

-

Roep de getKey()  modulefunctie aan om de sleutel te vernietigen.

-

Geef keyPart  en whichCharacter  door.

```

local ServerStorage = game:GetService("ServerStorage")

-- Vereis het modulescript hieronder ⯆

local treasureManager = require(ServerStorage:WaitForChild("TreasureManager"))

local keys = script.Parent

local keysFolder = keys.Parts

local keysArray = keysFolder:GetChildren()

local function partTouched(otherPart, keyPart)

	local whichCharacter = otherPart.Parent

	local humanoid = whichCharacter:FindFirstChildWhichIsA("Humanoid")

	if humanoid then

		-- Geef de speler een sleutel en vernietig het sleutelonderdeel

		-- =============================================

		treasureManager.getKey(keyPart, whichCharacter)

		-- =============================================

	end

end

```

4.

Voer het project uit en controleer of het aanraken van een sleutel deze vernietigt.

### [Probleemoplossingstips](#probleemoplossingstips)[](#probleemoplossingstips)

Probleem:  Ontvang een foutmelding met: "Infinite yield possible" .

-

Controleer de spelling van je modulescript in een script. Als een modulescript, zoals TreasureManager , anders is gespeld, zal er een fout optreden.

Probleem:  Ontvang een foutmelding met: "attempt to index global" .

-

Controleer de regel die de vereiste voor het modulescript in keyScript  bevat. Als de module geen vereiste bevat, kan deze geen functies en variabelen uit dat modulescript gebruiken.

Probleem:  Script wordt niet uitgevoerd of kan geen sleutels oppakken.

-

Zorg ervoor dat alle code in het modulescript tussen local TreasureManager = {}  en return TreasureManager  staat. De return moet de laatste regel code in een modulescript zijn.

-

Controleer of er twee haakjes aan het einde van de regel met vereisen staan, zoals in WaitForChild("TreasureManager")) .

## [Maak een Lokale Functie](#maak-een-lokale-functie)[](#maak-een-lokale-functie)

Op dit moment houdt een leaderboard het aantal sleutels en schatten van een speler bij. Om de leaderboardnummers te wijzigen, gebruik je een lokale functie in het modulescript. Een lokale functie wordt gebruikt omdat het wijzigen van de waarden van een speler's sleutels of schatten alleen nodig zal zijn in het TreasureManager-script, niet ergens anders.

1.

Open in ServerStorage  het TreasureManager  script.

2.

Maak lokale variabelen om het volgende te doen:

-

Verkrijg de Players-service zodat het script kan werken met de leaderboardstatistieken van de speler.

-

Sla het aantal sleutels op dat de speler ontvangt na het aanraken van keyPart .

```

local TreasureManager = {}

local Players = game:GetService("Players")

local keyDrop = 1

------------------ Lokale Functies

------------------ Module Functies

function TreasureManager.getKey(keyPart, whichCharacter)

	keyPart:Destroy()

end

return TreasureManager

```

3.

Kopieer en plak deze twee lokale functies in de sectie Lokale Functies .

-

getPlayerKeys()  retourneert de waarde van de Lockpicks  leaderstat van de speler.

-

getPlayerTreasure()  retourneert de waarde van de Treasure  leaderstat van de speler.

```

------------------ Lokale Functies

local function getPlayerKeys(whichCharacter)

	local player = Players:GetPlayerFromCharacter(whichCharacter)

	local leaderstats = player:FindFirstChild("leaderstats")

	return leaderstats:WaitForChild("Lockpicks")

end

local function getPlayerTreasure(whichCharacter)

	local player = Players:GetPlayerFromCharacter(whichCharacter)

	local leaderstats = player:FindFirstChild("leaderstats")

	return leaderstats:WaitForChild("Treasure")

end

------------------ Module Functies

```

4.

Om het aantal sleutels van de speler te verhogen, in de getKey()  modulefunctie:

-

Maak een local  variabele om getPlayerKeys(whichCharacter)  aan te roepen.

-

Voeg de waarde van keyDrop  toe aan playerKeys .

```

------------------ Module Functies

function TreasureManager.getKey(keyPart, whichCharacter)

	local playerKeys = getPlayerKeys(whichCharacter)

	playerKeys.Value = playerKeys.Value + keyDrop

	keyPart:Destroy()

end

```

5.

Voer het project uit. Controleer of het aanraken van een sleutel deze vernietigt en 1 toevoegt aan de sleutels van de speler in het leaderboard.

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-6/creating-with-module-scripts/show-leaderboard-key.jpg)

Als dat nodig is, controleer je script tegen het onderstaande voor eventuele probleemoplossingsproblemen.

Huidige TreasureManager Script

```

local TreasureManager = {}

local Players = game:GetService("Players")

local keyDrop = 1

------------------ Lokale Functies

local function getPlayerKeys(whichCharacter)

   local player = Players:GetPlayerFromCharacter(whichCharacter)

   local leaderstats = player:FindFirstChild("leaderstats")

   return leaderstats:WaitForChild("Lockpicks")

end

local function getPlayerTreasure(whichCharacter)

   local player = Players:GetPlayerFromCharacter(whichCharacter)

   local leaderstats = player:FindFirstChild("leaderstats")

   return leaderstats:WaitForChild("Treasure")

end

------------------ Module Functies

function TreasureManager.getKey(keyPart, whichCharacter)

   local playerKeys = getPlayerKeys(whichCharacter)

   playerKeys.Value = playerKeys.Value + keyDrop

   keyPart:Destroy()

end

return TreasureManager

```

## [Verkrijg informatie uit modulescripts](#verkrijg-informatie-uit-modulescripts)[](#verkrijg-informatie-uit-modulescripts)

Het TreasureManager  modulescript zal worden gebruikt wanneer spelers een schatkist aanraken om te controleren of ze minstens één sleutel hebben voordat ze deze openen en hen goud geven.

### [Controleer of kisten geopend kunnen worden](#controleer-of-kisten-geopend-kunnen-worden)[](#controleer-of-kisten-geopend-kunnen-worden)

1.

Eerst in ServerStorage  ⟩ TreasureManager  script, stel variabelen in voor hoeveel sleutels het kost om een kist te openen, en hoeveel goud elke kist bevat.

```

local TreasureManager = {}

local Players = game:GetService("Players")

local keyDrop = 1

local chestPickCost = 1

local chestReward = 100

------------------ Lokale Functies

local function getPlayerKeys(whichCharacter)

	local player = Players:GetPlayerFromCharacter(whichCharacter)

	local leaderstats = player:FindFirstChild("leaderstats")

	return leaderstats:WaitForChild("Lockpicks")

end

```

2.

Om een functie te maken die controleert of een speler een kist kan openen, voeg je in de sectie Module Functies  een nieuwe functie toe aan de TreasureManager  tabel genaamd canOpenChest()  met de parameter whichCharacter .

```

------------------ Module Functies

function TreasureManager.canOpenChest(whichCharacter)

end

function TreasureManager.getKey(keyPart, whichCharacter)

	local playerKeys = getPlayerKeys(whichCharacter)

	playerKeys.Value = playerKeys.Value + keyDrop

	keyPart:Destroy()

end

```

3.

Kopieer en plak de onderstaande code in canOpenChest()  om true  terug te geven als de speler genoeg sleutels heeft, en false  als dat niet het geval is.

```

function TreasureManager.canOpenChest(whichCharacter)

	local playerKeys = getPlayerKeys(whichCharacter)

	if playerKeys.Value >= chestPickCost then

		return true

	else

		return false

	end

end

```

### [Geef spelers schatten](#geef-spelers-schatten)[](#geef-spelers-schatten)

Zodat de speler een kist kan openen, maak je een functie in TreasureManager  die hen schatten toekent.

1.

Voeg een nieuwe modulefunctie toe aan TreasureManager  genaamd openChest() .

Geef twee argumenten door:

-

chestPart  - het kistonderdeel dat vernietigd moet worden.

-

whichCharacter  - de speler aan wie schatten moeten worden gegeven.

```

function TreasureManager.openChest(chestPart, whichCharacter)

end

```

2.

Om de sleutels van een speler af te trekken en hen schatten toe te kennen, kopieer en plak je de onderstaande code in openChest() . Deze code gebruikt de eerder gemaakte variabelen, zoals chestReward , het aantal schatten dat per kist wordt gegeven.

```

function TreasureManager.openChest(chestPart, whichCharacter)

	local playerKeys = getPlayerKeys(whichCharacter)

	local playerTreasure = getPlayerTreasure(whichCharacter)

	playerKeys.Value = playerKeys.Value - chestPickCost

	playerTreasure.Value = playerTreasure.Value + chestReward

	chestPart.Parent:Destroy()

end

```

### [Roep de kistfuncties aan](#roep-de-kistfuncties-aan)[](#roep-de-kistfuncties-aan)

Nu de twee modulefuncties, canOpenChest()  en openChest() , zijn gemaakt, kunnen ze door de kistonderdelen worden aangeroepen wanneer een speler ze aanraakt met behulp van de vooraf gemaakte partTouched()  functie.

1.

Open in Workspace  ⟩ Chests  het ChestScript .

2.

Maak een nieuwe variabele genaamd treasureManager  en vereis het TreasureManager  modulescript in ServerStorage .

```

local ServerStorage = game:GetService("ServerStorage")

-- Vereis het modulescript hieronder

local treasureManager = require(ServerStorage:WaitForChild("TreasureManager"))

local chests = script.Parent

local chestsFolder = chests.Parts

local chestsArray = chestsFolder:GetChildren()

```

3.

In partTouched() , onder de if humanoid  verklaring, maak een nieuwe variabele genaamd canOpen  en stel deze gelijk aan:

treasureManager.canOpenChest(whichCharacter)

```

local function partTouched(otherPart, chestPart)

	local whichCharacter = otherPart.Parent

	local humanoid = whichCharacter:FindFirstChildWhichIsA("Humanoid")

	if humanoid then

		-- Controleer of de speler een kist kan openen, laat ze dan schatten krijgen

		-- =============================================

		local canOpen = treasureManager.canOpenChest(whichCharacter)

		-- =============================================

	end

end

```

4.

Maak vervolgens een if-verklaring om te controleren of canOpen  waar is.

-

Als dat zo is, roep dan de openChest()  functie van TreasureManager aan.

-

Geef vervolgens twee parameters door: chestPart , de kist die vernietigd moet worden, en whichCharacter , de speler die schatten moet krijgen.

```

local function partTouched(otherPart, chestPart)

	local whichCharacter = otherPart.Parent

	local humanoid = whichCharacter:FindFirstChildWhichIsA("Humanoid")

	if humanoid then

		-- Controleer of de speler een kist kan openen, laat ze dan schatten krijgen

		-- =============================================

		local canOpen = treasureManager.canOpenChest(whichCharacter)

		if canOpen == true then

			treasureManager.openChest(chestPart, whichCharacter)

		end

		-- =============================================

	end

end

```

5.

Voer het project uit. Controleer of:

-

Als je minstens 1 sleutel hebt, het aanraken van een kist deze vernietigt en schatten toekent.

-

Als je 0 sleutels hebt, je een schatkist niet kunt openen.

### [Probleemoplossingstips](#probleemoplossingstips-1)[](#probleemoplossingstips-1)

-

Zorg ervoor dat in ChestScript  functies die vanuit het modulescript worden aangeroepen, zoals canOpenChest() , precies zo zijn gespeld als ze in het TreasureManager  script worden gevonden. Elke afwijking zal een fout veroorzaken.

-

Controleer of gekopieerde en geplakte functies, zoals treasureManager.openChest() , precies zijn zoals in de les getoond. Elke afwijking kan subtiele fouten in het script veroorzaken.

## [Voltooide scripts](#voltooide-scripts)[](#voltooide-scripts)

Voltooid TreasureManager Script

```

local TreasureManager = {}

local Players = game:GetService("Players")

local keyDrop = 1

local chestPickCost = 1

local chestReward = 100

------------------ Lokale Functies

local function getPlayerKeys(whichCharacter)

   local player = Players:GetPlayerFromCharacter(whichCharacter)

   local leaderstats = player:FindFirstChild("leaderstats")

   return leaderstats:WaitForChild("Lockpicks")

end

local function getPlayerTreasure(whichCharacter)

   local player = Players:GetPlayerFromCharacter(whichCharacter)

   local leaderstats = player:FindFirstChild("leaderstats")

   return leaderstats:WaitForChild("Treasure")

end

------------------ Module Functies

function TreasureManager.openChest(chestPart, whichCharacter)

   local playerKeys = getPlayerKeys(whichCharacter)

   local playerTreasure = getPlayerTreasure(whichCharacter)

   playerKeys.Value = playerKeys.Value - chestPickCost

   playerTreasure.Value = playerTreasure.Value + chestReward

   chestPart.Parent:Destroy()

end

function TreasureManager.canOpenChest(whichCharacter)

   local playerKeys = getPlayerKeys(whichCharacter)

   if playerKeys.Value >= chestPickCost then

   return true

   else

   return false

   end

end

function TreasureManager.getKey(keyPart, whichCharacter)

   local playerKeys = getPlayerKeys(whichCharacter)

   playerKeys.Value = playerKeys.Value + keyDrop

   keyPart:Destroy()

end

return TreasureManager

```

Voltooid ChestScript

```

local ServerStorage = game:GetService("ServerStorage")

-- Vereis het modulescript hieronder ⯆

local treasureManager = require(ServerStorage:WaitForChild("TreasureManager"))

local chests = script.Parent

local chestsFolder = chests.Parts

local chestsArray = chestsFolder:GetChildren()

local function partTouched(otherPart, chestPart)

   local whichCharacter = otherPart.Parent

   local humanoid = whichCharacter:FindFirstChildWhichIsA("Humanoid")

   if humanoid then

      -- Controleer of de speler een kist kan openen, laat ze dan schatten krijgen

      -- =============================================

      local canOpen = treasureManager.canOpenChest(whichCharacter)

      if canOpen == true then

         treasureManager.openChest(chestPart, whichCharacter)

      end

      -- =============================================

   end

end

-- Koppelt elk kistonderdeel aan de aanraakfunctie zodat het op alle onderdelen werkt

for chestIndex = 1, #chestsArray do

   local chestPart = chestsArray[chestIndex]:WaitForChild("Collider")

   chestPart.Touched:Connect(function(otherPart)

   partTouched(otherPart, chestPart)

   end)

end

```

Voltooid keyScript

```

local ServerStorage = game:GetService("ServerStorage")

-- Vereis het modulescript hieronder ⯆

local treasureManager = require(ServerStorage:WaitForChild("TreasureManager"))

local keys = script.Parent

local keysFolder = keys.Parts

local keysArray = keysFolder:GetChildren()

local function partTouched(otherPart, keyPart)

   local whichCharacter = otherPart.Parent

   local humanoid = whichCharacter:FindFirstChildWhichIsA("Humanoid")

   if humanoid then

      -- Geef de speler een sleutel en vernietig het sleutelonderdeel

      -- =============================================

      treasureManager.getKey(keyPart, whichCharacter)

      -- =============================================

   end

end

-- Koppelt elk sleutelonderdeel aan de aanraakfunctie zodat het op alle onderdelen werkt

for keyIndex = 1, #keysArray do

   local keyPart = keysArray[keyIndex]

   keyPart.Touched:Connect(function(otherPart)

      partTouched(otherPart, keyPart)

   end)

end

```

## [Samenvatting](#samenvatting)[](#samenvatting)

Een veelvoorkomende toepassing van het gebruik van modulescripts in Roblox-spellen is om veelvoorkomende taken te beheren die door spelers worden gebruikt, zoals het toekennen van punten. Voor dit voorbeeld is er een modulescript genaamd TreasureManager gemaakt om spelers sleutels en schatten te geven telkens wanneer ze met in-game objecten interageren.

[Volgende](/docs/nl-nl/tutorials/fundamentals/coding-6/coding-concept-abstraction)[Vorige](/docs/nl-nl/tutorials/fundamentals/coding-6/intro-to-module-scripts)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
