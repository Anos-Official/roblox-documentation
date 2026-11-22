<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/fundamentals/coding-6/intro-to-module-scripts -->

Introductie tot module scripts | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. [Code ordenen](/docs/nl-nl/tutorials/fundamentals/coding-6/landing)

# Introductie tot module scripts

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Naarmate projecten complexer worden, wordt het belangrijk om na te denken over hoe scripts zijn georganiseerd. Goede organisatiepraktijken kunnen ervoor zorgen dat code niet tussen scripts wordt gedupliceerd of moeilijk te beheren wordt.

Een betere manier om code te organiseren en te hergebruiken is met module scripts , een uniek type script dat een set functies en variabelen opslaat die zijn ontworpen om een gedeeld doel te bereiken, zoals het beheren van het geld van spelers of vijanden. Code binnen module scripts kan door andere scripts worden gebruikt. Op die manier kun je dezelfde functie aanroepen die munten geeft vanuit meerdere verschillende scripts telkens wanneer een speler een quest voltooit of een pickup vindt.

Door veelgebruikte code in module scripts op te slaan, wordt het onderhouden en organiseren van code gemakkelijker, omdat wijzigingen slechts in één module script hoeven te worden aangebracht, in plaats van dat meerdere scripts moeten worden bijgewerkt.

Normale scripts moeten worden gebruikt voor zelfstandige elementen van een game, zoals het aanraken van een pickup, terwijl module scripts nuttig zijn voor het opslaan van code die door meerdere onafhankelijke scripts kan worden hergebruikt, zoals het belonen van punten.

## [Basisprincipes van module scripts](#basisprincipes-van-module-scripts)[](#basisprincipes-van-module-scripts)

Module scripts zijn eigenlijk hun eigen aparte object in vergelijking met scriptobjecten. In Roblox kunnen module scripts worden aangeduid met een paarse  icoon.

### [Maak een module script](#maak-een-module-script)[](#maak-een-module-script)

ModuleScripts worden vaak geplaatst in ServerScriptService  wanneer ze worden gebruikt door server-side scripts en ReplicatedStorage  wanneer ze worden gebruikt door client-side lokale scripts (zoals GUI-interacties).

1.

Maak een ModuleScript  in ServerScriptService .

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-6/intro-to-module-scripts/create-module-script.png)

### [Structuur van module scripts](#structuur-van-module-scripts)[](#structuur-van-module-scripts)

Wanneer ze worden gemaakt, begint elk module script met de onderstaande code:

```

local Module = {}

return Module

```

De regel local Module = {}  creëert een tabel, of container van code, waarin de gedeelde functies en variabelen van het module kunnen worden opgeslagen. Deze tabel moet worden hernoemd naar het doel van de module, zoals RewardManager  of ParticleController . In tegenstelling tot andere variabelen die camel case zijn (myVariable ), wordt aanbevolen om module tabellen pascal case te gebruiken en met een hoofdletter te beginnen (MyModule ).

```

local RewardManager = {}

return RewardManager

```

Zodat andere scripts de niet-lokale functies of variabelen van een module kunnen gebruiken, eindigt elke module met return MyModule . Wanneer een ander script probeert code van de module te verkrijgen, laat return dat script toegang krijgen tot de code die in de module tabel is opgeslagen.

### [Toevoegen aan module scripts](#toevoegen-aan-module-scripts)[](#toevoegen-aan-module-scripts)

Om een functie of variabele aan de module toe te voegen die in een ander script kan worden gebruikt, typ je de naam van de module tabel, gevolgd door een punt, en de naam van de functie of variabele, zoals in TestModule.myVariable . Het gebruik van de puntoperator is een andere manier om code in een tabel toe te voegen, waardoor andere scripts toegang hebben tot die code telkens wanneer de module tabel wordt geretourneerd.

```

local TestModule = {}

-- Voegt een variabele toe aan de 'TestModule' tabel

TestModule.myVariable = 100

-- Voegt een functie toe aan de 'TestModule' tabel

function TestModule.doTask(player)

	-- Plaatsvervangende code

end

return TestModule

```

Alles wat aan de module tabel wordt toegevoegd, moet worden getypt tussen local MyModule = {}  en return MyModule , anders kan de code een fout veroorzaken.

### [Scope in module scripts](#scope-in-module-scripts)[](#scope-in-module-scripts)

Voor een module functie of variabele om in een extern script te worden gebruikt, moet je niet  local  typen.

Typen local  voor variabelen en functies betekent dat ze alleen  bruikbaar zijn door dat script. Hoewel dit een goede praktijk is voor de meeste scripts om fouten en probleemoplossing te verminderen, kun je module script functies en variabelen niet lokaal maken.

Elke code die alleen  door dat module script wordt gebruikt, moet nog steeds local  bevatten. Bijvoorbeeld, de onderstaande code bevat de lokale variabele difficultyModifier , die alleen in dat module script kan worden gebruikt, en de functie getCoinReward() , die in scripts buiten de module kan worden gebruikt.

```

local RewardManager = {}

-- Alleen bruikbaar in het module script

local rewardCoins = 50

-- Alleen bruikbaar in het module script

local difficultyModifier = {

	easy = 0.5,

	normal = 1,

	hard = 2

}

-- Bruikbaar in andere scripts

function RewardManager.getCoinReward(difficulty)

	local coins = difficultyModifier[difficulty] * rewardCoins

	return coins

end

return RewardManager

```

## [Gebruik modules in andere scripts](#gebruik-modules-in-andere-scripts)[](#gebruik-modules-in-andere-scripts)

Op zichzelf kan een module script geen code uitvoeren — het moet in een ander script worden geladen met behulp van het trefwoord [require()](/docs/nl-nl/reference/engine/globals/LuaGlobals#require) . De functie [require()](/docs/nl-nl/reference/engine/globals/LuaGlobals#require)  accepteert één argument, de locatie van het module script in de Explorer.

Om een module te gebruiken, stel je in een apart script een variabele gelijk aan require(moduleScript) .

```

local MyModule = require(ServerStorage.ModuleScript)

```

Nu bevat de variabele MyModule  de module tabel die in dat module script is gemaakt. Om functies en variabelen uit die tabel te gebruiken, typ je de naam van de variabele, gevolgd door een punt, en de exacte naam van wat je wilt gebruiken in dat module script, zoals MyModule.myFunction() . Wanneer het script wordt uitgevoerd en die regel bereikt, krijgt het toegang tot die specifieke functie of variabele die in de module tabel is opgeslagen.

```

local MyModule = require(ServerStorage.ModuleScript)

MyModule.myFunction()

```

## [Voorbeeld van RewardManager](#voorbeeld-van-rewardmanager)[](#voorbeeld-van-rewardmanager)

ModuleScript - RewardManager

```

local RewardManager = {}

-- Alleen bruikbaar in het module script

local rewardCoins = 50

-- Alleen bruikbaar in het module script

local difficultyModifier = {

 easy = 0.5,

 normal = 1,

 hard = 2

}

-- Bruikbaar in andere scripts

function RewardManager.getCoinReward(difficulty)

 local coins = difficultyModifier[difficulty] * rewardCoins

 return coins

end

return RewardManager

```

Script - TreasureChestScript

```

local ServerStorage = game:GetService("ServerStorage")

-- Laad module script

local RewardManager = require(ServerStorage.RewardManager)

-- Roept functie aan van module script

local coins = RewardManager.getCoinReward("easy")

print("Moet " .. coins .. " munten toekennen")

```

Als je in een ander script bent, zorg er dan voor dat de functie of variabele van het module script exact  hetzelfde is gespeld als gevonden in dat module. Om te helpen, kun je de exacte functie- of variabelenaam uit de module kopiëren en deze vervolgens gewoon plakken in het normale script waar het zal worden gebruikt.

## [Algemene probleemoplossing](#algemene-probleemoplossing)[](#algemene-probleemoplossing)

Enkele van de tips hier behandelen veelvoorkomende problemen bij het werken met module scripts. Houd er rekening mee dat module scripts een gecompliceerd onderwerp kunnen zijn met meer nuance. Voor meer details, zie deze meer technische gids over [Module Scripts](/docs/nl-nl/scripting/module) .

Probleem:  Ontvang een foutmelding met de tekst: "Infinite yield possible"  of "not a valid member" .

-

Controleer de spelling van het module script waar het wordt geladen. [require()](/docs/nl-nl/reference/engine/globals/LuaGlobals#require)  moet het exacte pad en de spelling van het module script bevatten, dat mogelijk anders is genoemd dan de module tabel.

Probleem:  Ontvang een foutmelding met de tekst: "attempt to index global" .

-

Zorg ervoor dat in alle scripts die een module script gebruiken, het wordt geladen met de functie [require()](/docs/nl-nl/reference/engine/globals/LuaGlobals#require) . Zo niet, kan dat script geen functies en variabelen van het module script gebruiken.

## [Samenvatting](#samenvatting)[](#samenvatting)

Module scripts  in Roblox zijn een methode die programmeurs gebruiken om code te organiseren en te hergebruiken. Een module script wordt vaak opgeslagen in ServerStorage (of ReplicatedStorage voor client-gebaseerde interacties). Van daaruit kunnen andere scripts functies en variabelen aanroepen die in dat module script zijn opgeslagen.

Bijvoorbeeld, een game kan punten toekennen aan spelers voor het verzamelen van objecten. Een module script kan de code afhandelen om punten te geven. Vervolgens kunnen scripts voor verschillende soorten objecten gewoon de functie van het module script aanroepen. Dit vermindert de noodzaak om code tussen scripts te hergebruiken, waardoor de code gemakkelijker te begrijpen en te onderhouden is.

[Volgende](/docs/nl-nl/tutorials/fundamentals/coding-6/create-with-module-scripts)[Vorige](/docs/nl-nl/tutorials/fundamentals/coding-6/landing)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
