<!-- Source: https://create.roblox.com/docs/nl-nl/luau/scope -->

Bereik | Documentatie - Roblox Creator Hub

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

# Bereik

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

In scripting is een codeblok het lichaam van een [besturingsstructuur](/docs/nl-nl/luau/control-structures)  of [functie](/docs/nl-nl/luau/functions) . Het bereik  van een variabele of functie is het codeblok dat er toegang toe heeft, en het kan globaal  of lokaal  zijn. Alle blokken kunnen toegang krijgen tot globale variabelen en functies. Een blok kan toegang krijgen tot lokale variabelen en functies in zijn bovenliggende blok, maar niet in een van zijn kindblokken.

Variabelen en functies hebben standaard een globaal bereik, maar het is bijna altijd beter om ze met lokaal bereik te declareren omdat Luau lokale variabelen en functies sneller benadert dan globale. Om een variabele of functie lokaal bereik te geven, zet je het trefwoord local  voor de naam wanneer je deze declareert.

Scripts kunnen geen toegang krijgen tot globale en lokale variabelen of functies in andere scripts. Als je waarden en functies tussen scripts wilt delen, gebruik dan [ModuleScripts](/docs/nl-nl/reference/engine/classes/ModuleScript) .

```

local helloWorld = 'Hello World!'

local function printHelloWorld()

	print(helloWorld)

end

printHelloWorld() -- Hello World!

```

 ![](https://prod.docsiteassets.roblox.com/assets/scripting/scripts/Scope-Diagram.png)

-

Blok B kan  de lokale variabele in blok A benaderen.

-

Blok C kan  de lokale variabelen en functies in de blokken A en B benaderen.

-

Blok A kan niet  de lokale variabelen en functies in de blokken B of C benaderen.

-

Blok B kan niet  de lokale variabele in blok C benaderen.

## [Globaal bereik](#globaal-bereik)[](#globaal-bereik)

Nadat je een globale variabele of functie hebt gedeclareerd, kan elk codeblok in hetzelfde [script](/docs/nl-nl/scripting)  er toegang toe krijgen. Variabelen en functies hebben globaal bereik, tenzij je ze declareert met het trefwoord local .

In de volgende code heeft testVar  globaal bereik binnen de lokale functie testFunc() . Wanneer Luau testFunc()  aanroept, wijst het testVar  de waarde 64  toe. testVar  heeft globaal bereik, zodat de functie print()  buiten testFunc()  er toegang toe kan krijgen en 64  kan afdrukken.

Voorbeeld van globale functies en variabelen

```

local function testFunc()  -- lokaal bereik

	testVar = 64  -- globaal bereik

end

testFunc()

print(testVar) -- 64

```

In de volgende code begint de globale variabele x  bij 0 , wordt met 1  verhoogd bij elke iteratie van de [for -lus](/docs/nl-nl/luau/control-structures#for-loops) , en wordt daarna opnieuw afgedrukt met een eindwaarde van 4.

```

x = 0  -- Globale variabele "x"

for i = 1, 4 do

	x += 1

	print("Globale 'x' = " .. x)

end

print("Globale 'x' = " .. x)

--[[ Resultaat:

Globale 'x' = 1

Globale 'x' = 2

Globale 'x' = 3

Globale 'x' = 4

Globale 'x' = 4

]]

```

Het is gemakkelijker om globale variabelen en functies te declareren omdat je niet zoveel hoeft te typen, maar globale variabelen en functies hebben de volgende nadelen in vergelijking met lokale:

-

Luau benadert globale variabelen en functies met een hashlookup, waardoor het duur is in termen van prestaties. Het gebruik van een globale variabele in een tijdkritieke lus kan ervoor zorgen dat deze meer dan 10% langzamer presteert dan het gebruik van een lokale variabele in dezelfde lus.

-

Luau verwijdert lokale variabelen nadat hun bereik eindigt, waardoor het geheugengebruik wordt verminderd.

-

Je kunt globale variabelen en functies binnen hetzelfde script benaderen, maar niet tussen meerdere scripts. Daarom biedt een globale variabele of functie geen enkel voordeel ten opzichte van een lokale equivalent binnen bereik, een [upvalue](#vangen) , of een [schaduw](#schaduw) .

## [Lokaal bereik](#lokaal-bereik)[](#lokaal-bereik)

Luau kan alleen toegang krijgen tot een lokale variabele of functie in het codeblok waar je deze declareert. Het creëren van een variabele met lokaal bereik geeft je striktere controle over wanneer en waar de waarde verandert.

In de volgende code hebben de functie testFunc()  en de variabele testVar  lokaal bereik. Alleen de code binnen testFunc()  kan toegang krijgen tot de variabele testVar . De variabele testVar  heeft geen waarde buiten testFunc() , dus het aanroepen van print(testVar)  binnen testFunc()  drukt de waarde van testVar  af, maar het aanroepen van print(testVar)  buiten testFunc()  drukt nil  af.

```

local function testFunc()  -- lokaal bereik

	local testVar = 64  -- lokaal bereik

	print(testVar) -- 64

end

testFunc()

print(testVar) -- nil

```

In de volgende code heeft de lokale variabele x  de waarde 0  op regel 1. Terwijl Luau door de [for -lus](/docs/nl-nl/luau/control-structures#for-loops)  iterates, heeft een andere lokale variabele x  de waarde 1 . Vervolgens drukt Luau de initiële variabele x  af met een onveranderde waarde van 0 .

```

local x = 0  -- Lokale variabele "x"

for i = 1, 4 do

	local x = 1  -- Andere variabele "x", lokaal voor deze "for" lus

	print("Lus 'x' = " .. x)

end

print("Initiële 'x' = " .. x)

--[[ Resultaat:

Lus 'x' = 1

Lus 'x' = 1

Lus 'x' = 1

Lus 'x' = 1

Initiële 'x' = 0

]]

```

const  variabelen en functies volgen dezelfde bereikregels als local  variabelen. Je kunt ze in elk blok declareren, inclusief binnen een andere functie. Voor meer informatie over const , zie [Const-variabelen](/docs/nl-nl/luau/variables#const-variabelen) .

### [Vangen](#vangen)[](#vangen)

Nadat je een lokale variabele hebt gedeclareerd en toegewezen, kun je deze lezen in zijn bereikniveau en functies waarvan de bereiken zijn ingesloten door hetzelfde bereik dat de lokale variabele bevat. Deze techniek staat bekend als vangen .

In de volgende code vangt de functie f  de lokale variabele x . De variabele x  in f()  is een upvalue .

```

local x = 5

local function f()

	print(x)

end

f() -- 5

print(x) -- 5

```

### [Schaduw](#schaduw)[](#schaduw)

Nadat je een lokale variabele hebt gedeclareerd en toegewezen, kun je deze lezen in zijn bereikniveau en afgeleide bereikniveaus. Als je de variabele in een afgeleid bereikniveau opnieuw declareert en toewijst, creëer je een nieuwe lokale variabele met dezelfde naam maar een andere waarde dan de meest recente toewijzing. De nieuwe lokale variabele beïnvloedt de lokale variabele van de vorige toewijzing niet. Deze techniek, bekend als schaduwen , helpt je de naam van een variabele opnieuw te gebruiken zonder de waarde ervan opnieuw te gebruiken.

In de volgende code schaduwt Luau de variabele x . De variabele x  in f()  is een schaduw  variabele.

```

local x = 5

local function f()

	local x = 7

	print(x)

end

f() -- 7

print(x) -- 5

```

Je kunt ook een lokale variabele opnieuw declareren zonder er een waarde aan toe te wijzen, zodat je de variabele zowel in zijn bereikniveau als in afgeleide bereikniveaus opnieuw kunt toewijzen. Het opnieuw declareren van een lokale variabele zonder er een waarde aan toe te wijzen, stelt de waarde in op nil .

In de volgende code schaduwt Luau de lokale variabele fruitName  in de functie getFruitByColor() . De functie declareert fruitName  opnieuw als een nieuwe schaduwvariabele en stelt de waarde in op nil . De functie heeft een afgeleid bereikniveau, een [for -lus](/docs/nl-nl/luau/control-structures#for-loops) , die een waarde aan fruitName  toewijst. Na de for-lus retourneert de functie de schaduwvariabele fruitName . Gedurende de hele functie is fruitName  dezelfde lokale variabele die de initiële lokale variabele fruitName  niet overschrijft.

```

local fruitName = "Chocolate"

local fruitTable = {

	Lemon = "Yellow",

	Apple = "Red",

	Orange = "Orange"

}

local function getFruitByColor(color)

	local fruitName

	for key, value in fruitTable do

		if value == color then

			fruitName = key

		end

	end

	return fruitName

end

local fruit = getFruitByColor("Yellow")

print(fruit) -- Lemon

print(fruit .. ", niet " .. fruitName) -- Lemon, niet Chocolate

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
