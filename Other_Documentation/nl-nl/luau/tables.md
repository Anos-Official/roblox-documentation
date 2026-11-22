<!-- Source: https://create.roblox.com/docs/nl-nl/luau/tables -->

Tabellen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)
6. /
7. [Luau-referentie](/docs/nl-nl/luau)
8. /
9. Typen

# Tabellen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het table  gegevenstype kan meerdere waarden van elk type dat niet nil  is opslaan, inclusief [booleans](/docs/nl-nl/luau/booleans) , [getallen](/docs/nl-nl/luau/numbers) , [strings](/docs/nl-nl/luau/strings) , [functies](/docs/nl-nl/luau/functions)  en andere tabellen. Constructeer tabellen met accolades ({} ):

```

-- Constructeer een lege tabel toegewezen aan variabele "t"

local t = {}

print(t) -- {}

```

Je kunt een tabel gebruiken als een [array](#arrays)  of [woordenboek](#woordenboeken) . Arrays gebruiken een geordende lijst van getallen als indices, maar woordenboeken kunnen getallen, strings en objecten als indices hebben.

Voor meer informatie over ingebouwde functies voor het werken met tabellen, zie de [table](/docs/nl-nl/reference/engine/libraries/table)  bibliotheek.

## [Arrays](#arrays)[](#arrays)

Een array  is een geordende lijst van waarden. Arrays zijn nuttig voor het opslaan van verzamelingen gegevens, zoals een groep spelers met speciale rechten.

### [Arrays maken](#arrays-maken)[](#arrays-maken)

Om een array te maken met een Luau-tabel, declareer je de waarden in volgorde, gescheiden door komma's.

```

-- Constructeer een array met drie items

local testArray = {"Een string", 3.14159, true}

print(testArray)

```

### [Lezen uit arrays](#lezen-uit-arrays)[](#lezen-uit-arrays)

Om uit een array te lezen, voeg je een paar vierkante haken toe na de referentie en geef je het indexnummer van het element binnenin op ([pos] ):

```

-- Constructeer een array met drie items

local testArray = {"Een string", 3.14159, true}

print(testArray[1]) -- Een string

print(testArray[2]) -- 3.14159

print(testArray[3]) -- true

```

In tegenstelling tot sommige talen, gebruikt Luau 1-gebaseerde indexering voor arrays, dus het eerste item in de array is [1] , niet [0] .

### [Schrijven naar arrays](#schrijven-naar-arrays)[](#schrijven-naar-arrays)

Om de waarde van een array op een index te definiëren of te herschrijven, declareer je het indexnummer in vierkante haken ([index] ) gevolgd door =  en de waarde:

```

local testArray = {"Een string", 3.14159, true}

testArray[2] = 12345

testArray[4] = "Nieuwe string"

print(testArray[2]) -- 12345

print(testArray[4]) -- Nieuwe string

```

### [Itereren over arrays](#itereren-over-arrays)[](#itereren-over-arrays)

Om over een array te itereren, kun je een for -lus gebruiken. Omdat de arrays numerieke indices hebben, kun je ook een numerieke for -lus gebruiken van 1  tot de lengte van de array (#array ).

```

local testArray = {"Een string", 3.14159, true, "Nieuwe string"}

-- Loop met algemene iteratie

for index, value in testArray do

	print(index, value)

end

-- Itereren met de array lengte operator (#)

for index = 1, #testArray do

	print(index, testArray[index])

end

```

### [Items invoegen](#items-invoegen)[](#items-invoegen)

Er zijn twee ingebouwde manieren om een item aan het einde  van een array toe te voegen:

-

Geef een referentie naar de array en de itemwaarde door aan Luau's [table.insert()](/docs/nl-nl/reference/engine/libraries/table#insert)  functie.

-

Voeg het nieuwe item toe aan de array met de array[#array+1]  syntaxis.

```

local testArray = {"Een string", 3.14159}

table.insert(testArray, "Nieuwe string")

testArray[#testArray+1] = "Nog een nieuwe string"

print(testArray[3]) -- Nieuwe string

print(testArray[4]) -- Nog een nieuwe string

```

Om een item tussen het begin en het einde van een array in te voegen, geef je een positie waarde op als het tweede argument van [table.insert()](/docs/nl-nl/reference/engine/libraries/table#insert) . Dit voegt het nieuwe item in en duwt de volgende items één indexpositie omhoog.

```

local testArray = {"Eerste item", "Volgend item"}

table.insert(testArray, 2, "NIEUW ITEM #2")

print(testArray[1]) -- Eerste item

print(testArray[2]) -- NIEUW ITEM #2

print(testArray[3]) -- Volgend item

```

### [Items verwijderen](#items-verwijderen)[](#items-verwijderen)

Om een item uit een array te verwijderen, gebruik je [table.remove()](/docs/nl-nl/reference/engine/libraries/table#remove) . Dit verwijdert het item op de opgegeven positie en verplaatst eventuele volgende items één indexpositie terug.

```

local testArray = {"Eerste item", "Volgend item", "Laatste item"}

table.remove(testArray, 2)

print(testArray[1]) -- Eerste item

print(testArray[2]) -- Laatste item

```

## [Woordenboeken](#woordenboeken)[](#woordenboeken)

Woordenboeken zijn een uitbreiding van arrays. Woordenboeken slaan een set van sleutel-waarde paren op, waarbij de sleutels elk getal, string of object kunnen zijn.

### [Woordenboeken maken](#woordenboeken-maken)[](#woordenboeken-maken)

Om een woordenboektabel te maken, definieer je elke sleutel  gevolgd door =  en de waarde . Scheid elk sleutel-waarde paar met een komma:

```

local testDictionary = {

	fruitNaam = "Citroen",

	fruitKleur = "Geel",

	zure = true

}

```

De sleutels voor woordenboeken kunnen getallen, strings en objecten zijn. Bijvoorbeeld, een sleutel kan ook een [Instance](/docs/nl-nl/reference/engine/classes/Instance)  zijn. Om objecten als sleutels te gebruiken, declareer je de sleutel in vierkante haken ([key] ):

```

local part = Instance.new("Part")

local testDictionary = {

	partType = "Blok",

	[part] = true

}

```

### [Lezen uit woordenboeken](#lezen-uit-woordenboeken)[](#lezen-uit-woordenboeken)

Om uit een woordenboek te lezen, voeg je een paar haken toe na de referentie en geef je de sleutelnaam op. Verwijs direct naar een string sleutel met (["key"] ) of (.key ), of gebruik in plaats daarvan een variabele waarde ([key] ).

```

local part = Instance.new("Part")

local testDictionary = {

	partType = "Blok",

	[part] = true

}

-- Voeg aanhalingstekens toe voor string sleutels

print(testDictionary["partType"]) -- Blok

-- Of gebruik . om string sleutels zonder spaties te indexeren

print(testDictionary.partType) -- Blok

-- Laat aanhalingstekens weg voor niet-string sleutels

print(testDictionary[part]) -- true

```

### [Schrijven naar woordenboeken](#schrijven-naar-woordenboeken)[](#schrijven-naar-woordenboeken)

Om de waarde van een nieuwe of bestaande woordenboek sleutel te definiëren of te herschrijven, declareer je de sleutelnaam in haken ([key] ) of, als de sleutel een string is, gebruik je (.key ) gevolgd door =  en de waarde:

```

local testDictionary = {

	fruitNaam = "Citroen",

	zure = true

}

-- Wijzig de waarde van bestaande sleutels

testDictionary["fruitNaam"] = "Kers"

testDictionary.zure = false

-- Voeg een nieuw sleutel-waarde paar toe

testDictionary.fruitAantal = 10

print(testDictionary.fruitNaam) -- Kers

print(testDictionary.zure) -- false

print(testDictionary.fruitAantal) -- 10

```

### [Itereren over woordenboeken](#itereren-over-woordenboeken)[](#itereren-over-woordenboeken)

Om over een woordenboek te itereren, gebruik je een for -lus:

```

local testDictionary = {

	fruitNaam = "Citroen",

	fruitKleur = "Geel",

	zure = true

}

for key, value in testDictionary do

	print(key, value)

end

--[[ Resultaat:

fruitNaam Citroen

zure true

fruitKleur Geel

]]

```

### [Sleutel-waarde paren verwijderen](#sleutel-waarde-paren-verwijderen)[](#sleutel-waarde-paren-verwijderen)

Om een sleutel-waarde paar uit een woordenboek te verwijderen of te wissen, stel je de waarde voor een sleutel in op nil .

```

local testDictionary = {

	fruitNaam = "Citroen",

	fruitKleur = "Geel",

	zure = true

}

testDictionary.zure = nil

for key, value in testDictionary do

	print(key, value)

end

--[[ Resultaat:

fruitNaam Citroen

fruitKleur Geel

]]

```

## [Tabellen als referenties](#tabellen-als-referenties)[](#tabellen-als-referenties)

Als je een tabel in een nieuwe variabele opslaat, maakt Luau geen kopie van die tabel. In plaats daarvan wordt de variabele een referentie , of pointer, naar de originele tabel. Elke referentie naar een tabel weerspiegelt eventuele wijzigingen in de originele tabel:

```

local origineleArray = {10, 20}

local arrayReferentie = origineleArray

print("Origineel:", origineleArray[1], origineleArray[2])

print("Referentie:", arrayReferentie[1], arrayReferentie[2])

-- Wijzig waarden in de originele array

origineleArray[1] = 1000

origineleArray[2] = 2000

print("Referentie:", arrayReferentie[1], arrayReferentie[2])

--[[ Resultaat:

Origineel: 10 20

Referentie: 10 20

Referentie: 1000 2000

]]

```

## [Tabellen klonen](#tabellen-klonen)[](#tabellen-klonen)

### [Shallow clones](#shallow-clones)[](#shallow-clones)

Om een tabel te kopiëren zonder geneste tabellen, biedt Luau de [table.clone()](/docs/nl-nl/reference/engine/libraries/table#clone)  methode.

```

local origineel = {

	sleutel = "waarde",

	motor = "Roblox",

	spelerID = 505306092

}

local kloon = table.clone(origineel)

```

### [Deep clones](#deep-clones)[](#deep-clones)

Om een complexere tabel met geneste tabellen erin te kopiëren, moet je een recursieve functie gebruiken die lijkt op de volgende:

```

-- De functie die wordt gebruikt voor het diep klonen van een tabel

local function deepClone(origineel)

	-- Definieer de nieuwe tabel voor de kopie

	local kloon = table.clone(origineel)

	-- Loop door de originele tabel om te controleren op tabelwaarden

	-- Als een tabel wordt gevonden als waarde, diep kloon deze naar de sleutel (index)

	for key, value in origineel do

		if type(value) == "table" then

			kloon[key] = deepClone(value)

		end

	end

	-- Geef de voltooide kopie van de diep gekloonde tabel terug

	return kloon

end

```

Met de functie op zijn plaats, kun je een diepe kopie maken als volgt:

```

local origineel = {

	sleutel = "waarde",

	spelerInfo = {

		spelerID = 505306092,

		spelerNaam = "SpelerNaam"

	},

	anderInfo = {

		{

			{1, 3, 5, 7, 9}

		}

	}

}

local kloon = deepClone(origineel)

```

## [Tabellen bevriezen](#tabellen-bevriezen)[](#tabellen-bevriezen)

Het bevriezen van een tabel maakt deze alleen-lezen, wat nuttig is voor het creëren van constante waarden die je niet wilt wijzigen. Bevriezen is permanent; er is geen "debevriezen" of "ontdooien" methode. Om te controleren of een tabel bevroren is, gebruik je [table.isfrozen()](/docs/nl-nl/reference/engine/libraries/table#isfrozen) .

### [Shallow freezes](#shallow-freezes)[](#shallow-freezes)

Om een tabel te bevriezen zonder geneste tabellen, biedt Luau de [table.freeze()](/docs/nl-nl/reference/engine/libraries/table#freeze)  methode.

```

local doel = {

	sleutel = "waarde",

	motor = "Roblox",

	spelerID = 505306092

}

table.freeze(doel)

doel.spelerID = 1 --> poging om een alleen-lezen tabel te wijzigen

```

### [Deep freezes](#deep-freezes)[](#deep-freezes)

Om een complexere tabel met geneste tabellen erin te bevriezen, gebruik je een recursieve functie die lijkt op de volgende:

```

local function deepFreeze(doel)

	-- Shallow freeze de tabel

	table.freeze(doel)

	-- Controleer elke sleutel van de tabel en bevries deze als het een tabel is

	for _, value in doel do

		-- Zorg ervoor dat de waarde niet bevroren is; als dat al zo is, zal er een fout optreden

		if type(value) == "table" and table.isfrozen(value) == false then

			deepFreeze(value)

		end

	end

end

```

Met de functie op zijn plaats, kun je een tabel diep bevriezen als volgt:

```

local doel = {

	sleutel = "waarde",

	spelerInfo = {

		spelerID = 505306092,

		spelerNaam = "SpelerNaam"

	},

	anderInfo = {

		{

			{1, 3, 5, 7, 9}

		}

	}

}

deepFreeze(doel)

doel.spelerInfo.spelerID = 1 --> poging om een alleen-lezen tabel te wijzigen

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
