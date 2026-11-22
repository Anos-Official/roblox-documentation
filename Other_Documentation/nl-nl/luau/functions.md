<!-- Source: https://create.roblox.com/docs/nl-nl/luau/functions -->

Functies | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)
6. /
7. [Luau-referentie](/docs/nl-nl/luau)
8. /
9. Functies

# Functies

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Functies  zijn [blokken code](/docs/nl-nl/luau/scope)  die je meerdere keren op commando kunt uitvoeren. Je kunt ze ook verbinden met [evenementen](#evenementhandlers)  of ze toewijzen als [callbacks](#callbacks) .

## [Basisfuncties](#basisfuncties)[](#basisfuncties)

Een functiedefinitie omvat:

-

De [scope](/docs/nl-nl/luau/scope)  van de functie: globaal of local  (of [const](/docs/nl-nl/luau/variables#const-variabelen)  voor een lokale functie waarvan je de naam niet kunt hertoewijzen).

-

Het function  sleutelwoord.

-

De naam van de functie in camelCase .

-

De parameters van de functie in haakjes (() ).

-

Het codeblok, of "lichaam", van de functie.

-

Het end  sleutelwoord.

Het lichaam van de functie wordt uitgevoerd wanneer je de functie aanroept. Om een functie aan te roepen, typ je de naam gevolgd door haakjes. Je kunt een variabele definiëren om de retourwaarde te accepteren of de retourwaarde gebruiken in plaats van een variabele.

```

-- Deze functie heeft geen parameters en retourneert nil

local function addOneAndTwo()

	local result = 1 + 2

	print(result)

end

-- Een functie aanroepen zonder een return

addOneAndTwo() -- 3

```

### [Parameters](#parameters)[](#parameters)

Parameters zijn variabelen die je beschikbaar maakt voor de functie en alleen in de [scope](/docs/nl-nl/luau/scope)  van de functie worden gebruikt. Functies hebben standaard geen parameters. Als je een functie aanroept met meer parameters dan het verwacht, negeert Luau de extra parameters. Als je een functie aanroept met minder parameters dan het verwacht, geeft Luau nil  door voor alle ontbrekende parameters.

```

-- Deze functie heeft twee parameters: num1 en num2

local function addNumbers(num1, num2)

	print(num1 + num2)

end

addNumbers(2, 3) -- 5

addNumbers(5, 6, 7) -- 11

addNumbers(9) -- poging om wiskunde (optellen) uit te voeren op nummer en nil

```

### [Return](#return)[](#return)

In het lichaam van de functie retourneert het return  sleutelwoord een resultaat van een berekening. Je kunt meerdere waarden uit één functie retourneren. return  beëindigt de uitvoering van de functie, en Luau verwacht dat het end  sleutelwoord volgt op de return -instructies, dus het schrijven van code tussen het return -commando en het end -commando veroorzaakt een fout.

```

-- Deze functie retourneert één returnwaarde

local function addNumbers(num1, num2)

	local result = num1 + num2

	return result

end

print(addNumbers(1, 2)) -- 3

local seven = addNumbers(3, 4)

print(seven) -- 7

-- Deze functie retourneert meerdere waarden: som en verschil

local function addAndSubtract(num1, num2)

	local sum = num1 + num2

	local difference = num1 - num2

	return sum, difference

end

-- Een functie aanroepen en meerdere returnwaarden verwachten

local sum, difference = addAndSubtract(2, 3)

print(sum) -- 5

print(difference) -- -1

```

## [Methoden](#methoden)[](#methoden)

Methoden zijn functies die leden zijn van een object, zoals een [klasse](/docs/nl-nl/reference/engine/classes)  of [tabel](/docs/nl-nl/luau/tables) . Ze verwachten het object zelf (self ) als het eerste argument. Wanneer je een methode aanroept, gebruik je de dubbele puntnotatie (: ) in plaats van de puntnotatie (. ) om self  automatisch als het eerste argument door te geven.

Alle objecten in Roblox zijn afgeleid van [Instance](/docs/nl-nl/reference/engine/classes/Instance)  en hebben veelgebruikte methoden zoals [Instance:Destroy()](/docs/nl-nl/reference/engine/classes/Instance#Destroy) , [Instance:Clone()](/docs/nl-nl/reference/engine/classes/Instance#Clone) , en [Instance:FindFirstChild()](/docs/nl-nl/reference/engine/classes/Instance#FindFirstChild) .

```

local Workspace = game:GetService("Workspace")

-- Een onderdeel vernietigen met puntnotatie (functie)

local firstPart = Instance.new("Part")

firstPart.Parent = Workspace

print(firstPart.Parent) -- Workspace

firstPart.Destroy(firstPart)

print(firstPart.Parent) -- nil

-- Een onderdeel vernietigen met dubbele puntnotatie (methode)

local secondPart = Instance.new("Part")

secondPart.Parent = Workspace

print(secondPart.Parent) -- Workspace

secondPart:Destroy()

print(secondPart.Parent) -- nil

```

De instructie table:Method()  is functioneel identiek aan table.Method(table) , en bij het definiëren van een methode is function table:Method()  identiek aan function table.Method(self) . Dit gedrag strekt zich uit tot [Instance](/docs/nl-nl/reference/engine/classes/Instance) -methoden, aangezien ze ook zijn afgeleid van tabellen.

### [Methoden definiëren](#methoden-definiëren)[](#methoden-definiëren)

Om een methode in een tabel te maken, gebruik je de naam van de methode als de sleutel en de methodefunctie als de waarde. In de definitie van de methode verwijst de self  parameter naar de bovenliggende tabel van de methode. Wanneer je een methode aanroept met dubbele puntnotatie, geef je de tabel zelf door als het eerste argument. Je kunt parameters voor een methode definiëren, maar je moet ze na de self  parameter opsommen.

In het volgende voorbeeld heeft de testButton  tabel een methode als de waarde van de changeEnabled  sleutel. Je kunt verifiëren dat self  verwijst naar de bovenliggende tabel van de methode door de waarde van self.enabled  af te drukken.

```

local testButton = {

	enabled = true,

	changeEnabled = function(self, isEnabled)

		self.enabled = isEnabled

		print(self.enabled)

	end

}

print(testButton.enabled) -- true

-- Roep de methode aan

testButton:changeEnabled(false) -- false

```

## [Callbacks](#callbacks)[](#callbacks)

Callbacks zijn functies die worden uitgevoerd als reactie op een andere functie of proces.

### [Basiscallbacks](#basiscallbacks)[](#basiscallbacks)

Functies kunnen worden doorgegeven aan andere functies, bijvoorbeeld, een [anonieme](#anonieme-functies)  functie kan worden gebruikt om een callback te implementeren die [table.sort()](/docs/nl-nl/reference/engine/libraries/table#sort)  vervolgens gebruikt om een lijst van [Players](/docs/nl-nl/reference/engine/classes/Player)  van [Players.GetPlayers()](/docs/nl-nl/reference/engine/classes/Players#GetPlayers)  te sorteren.

```

local Players = game:GetService("Players")

local sortedPlayers = Players:GetPlayers()

table.sort(sortedPlayers, function(a, b)

	-- Gebruik een anonieme callback om spelers op naam te sorteren

	return a.Name < b.Name

end)

```

In de Roblox API verwijzen callbacks naar een schrijf-only functie lid, callbacks wachten tot ze retourneren. Veelgebruikte callbacks zijn onder andere:

-

[MarketplaceService.ProcessReceipt](/docs/nl-nl/reference/engine/classes/MarketplaceService#ProcessReceipt) , dat de aankopen van ontwikkelaarsproducten afhandelt.

-

[BindableFunction.OnInvoke](/docs/nl-nl/reference/engine/classes/BindableFunction#OnInvoke) , dat de functie aanroept wanneer een script BindableFunction:Invoke(...)  aanroept.

-

[RemoteFunction.OnClientInvoke](/docs/nl-nl/reference/engine/classes/RemoteFunction#OnClientInvoke) , dat de functie aanroept wanneer de server RemoteFunction:FireClient(player, ...)  of RemoteFunction:FireAllClients(...)  aanroept.

-

[RemoteFunction.OnServerInvoke](/docs/nl-nl/reference/engine/classes/RemoteFunction#OnServerInvoke) , dat de functie aanroept wanneer een client RemoteFunction:InvokeServer(...)  aanroept.

Om een callback in te stellen, wijs je er een functie aan toe. Bijvoorbeeld, [BindableFunction.OnInvoke](/docs/nl-nl/reference/engine/classes/BindableFunction#OnInvoke)  is een callback van [BindableFunction](/docs/nl-nl/reference/engine/classes/BindableFunction) . Je kunt er een benoemde of [anonieme](#anonieme-functies)  functie aan toewijzen, en je kunt die functie (aanroepen ) door de :Invoke()  methode op de callback aan te roepen. De argumenten die je doorgeeft aan :Invoke()  worden doorgegeven aan de callback, en de retourwaarde van de callbackfunctie retourneert naar de aanroeper van :Invoke() .

```

local bindableFunction = Instance.new("BindableFunction")

bindableFunction.OnInvoke = function(number)

	return 2 * number

end

print(bindableFunction:Invoke(42)) -- 84

```

## [Functietechnieken](#functietechnieken)[](#functietechnieken)

### [Evenementhandlers](#evenementhandlers)[](#evenementhandlers)

Je kunt een functie, bekend als een evenementhandler , toewijzen om uit te voeren wanneer een evenement wordt geactiveerd. Bijvoorbeeld, je kunt een functie genaamd onPlayerAdded()  maken voor het [Players.PlayerAdded](/docs/nl-nl/reference/engine/classes/Players#PlayerAdded)  evenement om de naam van elke speler die zich aansluit af te drukken. Voor meer informatie, zie [Evenementen](/docs/nl-nl/scripting/events) .

```

local Players = game:GetService("Players")

local function onPlayerAdded(player)

	print(player.Name .. " is het spel binnengekomen!")

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

### [Anonieme functies](#anonieme-functies)[](#anonieme-functies)

Je kunt functies zonder namen maken, bekend als anonieme functies , om te gebruiken als [callbacks](#callbacks)  en [evenementhandlers](#evenementhandlers) . Net als benoemde functies moeten anonieme functies beginnen en eindigen met de function  en end  sleutelwoorden, maar je hebt het local  sleutelwoord niet nodig om de lokale scope aan te geven omdat ze altijd een lokale scope hebben.

In het volgende voorbeeld zijn de callback voor de [task.delay()](/docs/nl-nl/reference/engine/libraries/task#delay)  functie en de evenementhandler voor het [Players.PlayerAdded](/docs/nl-nl/reference/engine/classes/Players#PlayerAdded)  evenement beide anonieme functies.

```

-- Anonieme functie in een callback voor task.delay()

task.delay(2, function(exactTimeElapsed)

	print(exactTimeElapsed) -- 2.0064592329945

end)

-- Anonieme functie in een evenementhandler

local Players = game:GetService("Players")

Players.PlayerAdded:Connect(function(player)

	print(player.Name .. " is het spel binnengekomen!")

end)

```

### [Functies in modulescripts](#functies-in-modulescripts)[](#functies-in-modulescripts)

Je kunt functies hergebruiken in meerdere scripts door ze op te slaan in [ModuleScripts](/docs/nl-nl/reference/engine/classes/ModuleScript) . Functies zijn een Luau datatype, dus je kunt ze opslaan in tabellen met andere gegevens.

### [Variadische functies](#variadische-functies)[](#variadische-functies)

Een variadische functie accepteert een onbeperkt aantal argumenten. Bijvoorbeeld, Globals.LuaGlobals.print()  is een variadische functie.

```

print(2, "+", 2, "=", 2 + 2) --2 + 2 = 4

print(string.format("De %s is een %s!", "taart", "leugen")) -- De taart is een leugen!

print(string.char(115, 101, 99, 114, 101, 116)) -- geheim

```

#### [Variadische functies definiëren](#variadische-functies-definiëren)[](#variadische-functies-definiëren)

Om een variadische functie te definiëren, gebruik je het ...  token als de laatste of enige parameter (niet te verwarren met .. , de concatenatie [operator](/docs/nl-nl/luau/operators) ). Je kunt de ...  waarden in een tabel plaatsen voor gebruiksgemak.

Het variadische token ...  kan alleen worden gebruikt binnen functies die als variadisch zijn gedefinieerd; functies of callbacks die binnen een variadische functie zijn gedefinieerd kunnen  niet hetzelfde ...  gebruiken, zelfs als ze zelf variadisch zijn.

...  gedraagt zich niet als een reguliere variabele en kan alleen worden doorgegeven aan andere functies, geretourneerd of in een tabel geplaatst worden.

```

local function variadic(named, ...)

	local arguments = {...} -- pak de extra argumenten in een tabel

	print("Genoemde argument =", named)

	for i, value in arguments do

		print("Invoer Nr.", i, "=", value)

	end

end

variadic(10, "Hallo", 20, "Variadische Functie")

--[[ Resultaat:

Genoemde argument = 10

Invoer Nr. 1 = Hallo

Invoer Nr. 2 = 20

Invoer Nr. 3 = Variadische Functie

]]

```

#### [Argumenten doorgeven](#argumenten-doorgeven)[](#argumenten-doorgeven)

Je kunt variadische functies definiëren als wrappers rond andere functies om argumenten van de wrapper naar de andere functies door te geven of door te geven.

```

local function printAround(functionToPrintAround, ...)

	print("Vooraf")

	functionToPrintAround(...)

	print("Achteraf")

end

local function addNumbers(x, y, z)

	print("x =", x)

	print("y + z =", y + z)

end

printAround(addNumbers, 1, 2, 3)

--[[ Resultaat:

Vooraf

x = 1

y + z = 5

Achteraf

]]

```

#### [Een variadische functie aanroepen met arrays](#een-variadische-functie-aanroepen-met-arrays)[](#een-variadische-functie-aanroepen-met-arrays)

Als je een tabelarray van waarden naar een globale variadische functie wilt doorgeven, zoals print() , kun je de globale unpack()  functie gebruiken om de waarden van de tabel door te geven in plaats van de tabel zelf.

```

local squares = {1, 4, 9, 16, 25}

print("De eerste 5 kwadraten zijn:", unpack(squares))

-- De eerste 5 kwadraten zijn 1 4 9 16 25

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
