<!-- Source: https://create.roblox.com/docs/nl-nl/luau/control-structures -->

Controle structuren | Documentatie - Roblox Creator Hub

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

# Controle structuren

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Controle structuren  zijn uitspraken die de stroom van Luau-code-uitvoering beheren. Er zijn vier hoofdtypen controle structuren:

-

Een [if then else](#if-uitspraken)  uitspraak voert code uit alleen als een opgegeven voorwaarde waar  is. De code-uitvoering herhaalt zich niet.

-

Een [while loop](#while-loops)  voert code uit alleen als een opgegeven voorwaarde waar  is, en herhaalt de uitvoering zolang de voorwaarde waar  blijft.

-

Een [repeat loop](#repeat-loops)  voert code uit, en herhaalt de uitvoering als de voorwaarde waar  is.

-

Een [for loop](#for-loops)  voert code een vastgesteld aantal keren uit, afhankelijk van opgegeven invoer.

De voorwaarde voor if  uitspraken, while  loops, en repeat  loops kan elke Luau-expressie of waarde zijn. Als een waarde niet vals  of nil  is, dan evalueert Luau deze als waar  in voorwaardelijke uitspraken. In tegenstelling tot andere scripttalen beschouwt Luau zowel nul als de lege string als waar .

## [If uitspraken](#if-uitspraken)[](#if-uitspraken)

De basis if  uitspraak test zijn voorwaarde. Als de voorwaarde waar is, dan voert Luau de code tussen then  en end  uit.

Je kunt een elseif  uitspraak gebruiken om te testen op aanvullende voorwaarden als de if  voorwaarde vals is. Je kunt een else  uitspraak gebruiken om code uit te voeren als alle if  en elseif  voorwaarden falen. De elseif  en else  delen zijn beide optioneel, maar je kunt geen van beide gebruiken zonder een initiële if  uitspraak.

In een keten van if , elseif , en else  voorwaarden test Luau de voorwaarden van boven naar beneden, stopt bij de eerste waar  voorwaarde, en voert de code uit die daarop volgt.

```

if 2 + 2 == 5 then

	print("Twee plus twee is vijf") -- Print niet omdat de voorwaarde vals is

elseif 2 + 3 == 5 then

	print("Twee plus drie is vijf") -- Twee plus drie is vijf

else

	print("Alle voorwaarden zijn gefaald") -- Print niet omdat de vorige voorwaarde waar is

end

```

## [While loops](#while-loops)[](#while-loops)

Een while — do  loop evalueert of een opgegeven voorwaarde waar of vals is. Als de voorwaarde vals  of nil  is, dan eindigt de loop, en slaat Luau de code in de loop over. Als de voorwaarde waar  is, dan voert Luau de code in de loop uit en herhaalt het proces.

```

local tijdOver = 10

while tijdOver > 0 do

	print("Seconden over: " .. tijdOver)

	task.wait(1)

	tijdOver -= 1

end

print("Timer heeft nul bereikt!")

--[[ Resultaat:

Seconden over: 10

Seconden over: 9

Seconden over: 8

Seconden over: 7

Seconden over: 6

Seconden over: 5

Seconden over: 4

Seconden over: 3

Seconden over: 2

Seconden over: 1

Timer heeft nul bereikt!

]]

```

### [Oneindige loops](#oneindige-loops)[](#oneindige-loops)

Je kunt een while — do  loop gebruiken om oneindige game loops te schrijven door waar  als de voorwaarde in te stellen.

```

while true do

	print("Lopen...")

	task.wait(0.5)

end

--[[ Resultaat:

Lopen...

Lopen...

Lopen...

Lopen...

...

]]

```

Zorg ervoor dat je altijd een vertraging zoals [task.wait()](/docs/nl-nl/reference/engine/libraries/task#wait)  in een oneindige loop opneemt. Het weglaten ervan bevriest het spel en crasht Studio.

## [Repeat loops](#repeat-loops)[](#repeat-loops)

De repeat — until  loop herhaalt totdat een voorwaarde waar is. De voorwaardelijke test evalueert na  het uitvoeren van het codeblok, zodat het codeblok altijd minstens één keer wordt uitgevoerd. In tegenstelling tot andere talen omvat de Luau-scope van een lokale variabele die binnen een repeat — until  loop is gedeclareerd de voorwaarde.

```

local huidigGoblinAantal = 18

-- Spawnen goblins tot een maximum van 25 in het spel

repeat

	spawnGoblin()

	huidigGoblinAantal += 1

	print("Huidig goblin aantal: " .. huidigGoblinAantal)

until huidigGoblinAantal == 25

print("Goblins zijn opnieuw bevolkt!")

--[[ Resultaat:

Huidig goblin aantal: 19

Huidig goblin aantal: 20

Huidig goblin aantal: 21

Huidig goblin aantal: 22

Huidig goblin aantal: 23

Huidig goblin aantal: 24

Huidig goblin aantal: 25

Goblins zijn opnieuw bevolkt!

]]

```

## [For loops](#for-loops)[](#for-loops)

Een for loop voert code een vastgesteld aantal keren uit, hetzij op basis van een [numerieke teller](#numerieke-for-loops)  of het aantal [items in een collectie](#generieke-for-loops) .

### [Numerieke for loops](#numerieke-for-loops)[](#numerieke-for-loops)

Een for — do  loop bepaalt het aantal keren dat de loop moet worden uitgevoerd met behulp van een teller. De loop wordt gedeclareerd met een startwaarde, eindwaarde en optionele increment.

Luau stelt de teller gelijk aan de startwaarde, voert het codeblok in de for  loop uit, en voegt vervolgens de increment toe aan de teller. Als de increment positief is, herhaalt het proces zich totdat de teller gelijk is aan of groter is dan de eindwaarde. Als de increment negatief is, herhaalt het proces zich totdat de teller gelijk is aan of kleiner is dan de eindwaarde.

De optionele increment is standaard 1 . Het hoeft geen geheel getal te zijn.

```

for teller = 1, 3 do

	print(teller)

end

--[[ Resultaat:

1

2

3

]]

for teller = 1, 6, 2 do

	print(teller)

end

--[[ Resultaat:

1

3

5

]]

for teller = 2, 0, -0.5 do

	print(teller)

end

--[[ Resultaat:

2

1.5

1

0.5

0

]]

```

### [Generieke for loops](#generieke-for-loops)[](#generieke-for-loops)

De generieke for  loop iterates over items in een collectie in plaats van een reeks getallen. Met generieke for  loops kun je code uitvoeren voor elk item in de collectie, en kun je elk item gemakkelijk in de code gebruiken.

For loops hebben een functie of iterator nodig om over verschillende soorten collecties te itereren. De globale ipairs()  retourneert een iterator voor arrays, en de globale pairs()  retourneert een iterator voor woordenboeken. De [string](/docs/nl-nl/reference/engine/libraries/string)  bibliotheek biedt [string.gmatch()](/docs/nl-nl/reference/engine/libraries/string#gmatch)  om over strings te itereren.

### [Gegeneraliseerde iteratie](#gegeneraliseerde-iteratie)[](#gegeneraliseerde-iteratie)

In Luau kun je over een tabel itereren met behulp van het in  sleutelwoord direct op de tabel, in plaats van een iteratorfunctie zoals ipairs()  te gebruiken:

```

for i, v in {1, 2, 3, 4, 5} do

	print(i, v)

end

```

Gegeneraliseerde iteratie laat je ook de __iter  metamethode gebruiken om een aangepaste iteratorfunctie te maken. Dit geforceerde voorbeeld iterates over een array in omgekeerde volgorde, van het laatste element naar het eerste:

```

local mijnTabel = {1, 2, 3, 4, 5}

mijnMetatabel = {

	__iter = function(t)

		local i = #t + 1

		return function()

			i -= 1

			if i > 0 then

				return i, t[i]

			end

		end

	end,

}

setmetatable(mijnTabel, mijnMetatabel)

for i, v in mijnTabel do

	print(i, v)

end

--[[ Resultaat:

5 5

4 4

3 3

2 2

1 1

]]

```

#### [Arrays](#arrays)[](#arrays)

De ipairs()  functie retourneert een iterator die door numerieke indices in een tabel iterates en een index  en value  voor elk element retourneert. Dit maakt het geschikt voor arrays, waar alle indices numeriek zijn.

```

local array = {"a", "b", "c", "d", "e"}

for index, value in ipairs(array) do

	print(index, value)

end

--[[ Resultaat:

1 a

2 b

3 c

4 d

5 e

]]

```

#### [Woordenboeken](#woordenboeken)[](#woordenboeken)

De pairs()  functie retourneert een iterator die door alle indices (inclusief numerieke indices) in een tabel iterates en een key  en value  voor elke invoer in het woordenboek retourneert. De volgorde van het doorlopen van elementen in een woordenboektabel is willekeurig. Dit maakt het geschikt voor het itereren over woordenboeken, waar items buiten volgorde met niet-numerieke indices zijn opgeslagen.

```

local woordenboek = {

	[1] = "a",

	["Hallo"] = "b",

	[5] = "c",

	[true] = "d",

	["Wereld"] = "f",

	[false] = "e"

}

for key, value in pairs(woordenboek) do

	print(key, value)

end

--[[ Resultaat:

Hallo b

true d

false e

Wereld f

5 c

1 a

]]

```

## [Break loops](#break-loops)[](#break-loops)

Om een loop te dwingen te eindigen, gebruik je het break  sleutelwoord. Het volgende codevoorbeeld toont hoe je een oneindige while — do  loop kunt onderbreken.

```

local secondenVerstreken = 0

local timeout = 5

while true do

	task.wait(1)

	secondenVerstreken += 1

	print("Verstreken seconden:", secondenVerstreken)

	if secondenVerstreken == timeout then

		break

	end

end

print("Vijf seconden verstreken. Tijd om verder te gaan!")

--[[ Resultaat:

1

2

3

4

5

Vijf seconden verstreken. Tijd om verder te gaan!

]]

```

## [Continue loops](#continue-loops)[](#continue-loops)

Om een loop te dwingen te itereren en opnieuw te beginnen, gebruik je het continue  sleutelwoord. Een for  loop zal de teller itereren; while  en repeat — until  zullen de loopvoorwaarde controleren voordat ze doorgaan. Het volgende codevoorbeeld haalt alle kinderen van een [Instance](/docs/nl-nl/reference/engine/classes/Instance)  van een specifieke [ClassName](/docs/nl-nl/reference/engine/classes/Instance#ClassName) .

```

local function GetChildrenOfClass(parent: Instance, className: string): {Instance}

	local children = {}

	for _, child in parent:GetChildren() do

		if child.ClassName ~= className then continue end  -- Itereert de loop

		table.insert(children, child)

	end

	return children

end

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
