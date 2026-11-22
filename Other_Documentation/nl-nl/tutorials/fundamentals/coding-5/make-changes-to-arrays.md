<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/fundamentals/coding-5/make-changes-to-arrays -->

Wijzigingen aanbrengen in arrays | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. [Woordenboeken en arrays](/docs/nl-nl/tutorials/fundamentals/coding-5/landing)

# Wijzigingen aanbrengen in arrays

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De inhoud van een array moet vaak worden gewijzigd, bijvoorbeeld wanneer je een item uit de inventaris van een speler moet verwijderen. Luau heeft ingebouwde functies  voor gebruik met tabellen om dit gemakkelijker te maken.

Dit artikel beschrijft vooraf gebouwde functies voor tabellen zoals toevoegen en verwijderen, terwijl het uitlegt hoe je naar een waarde kunt zoeken.

Om deze vaardigheden toe te passen, maak je een script dat helpt bij het beheren van de inventaris van een speler.

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-5/coding4_arrayFunctions.jpg)

## [Waarden aan arrays toevoegen](#waarden-aan-arrays-toevoegen)[](#waarden-aan-arrays-toevoegen)

Om een nieuwe waarde aan een array toe te voegen, gebruik je table.insert(array, valueToInsert) . De tweede parameter kan elke waarde zijn, zoals een string, nummer of een heel object, zoals [Player](/docs/nl-nl/reference/engine/classes/Player)  of [IntValue](/docs/nl-nl/reference/engine/classes/IntValue) .

Om te oefenen, maak je een script dat de items van de speler in een tabel opslaat en daar vervolgens aan toevoegt. Aangezien dit voorbeeld slechts een script is, kan het met elk bestand of project worden gebruikt. Het testen van de code zal worden gedaan met behulp van het Output-venster.

1.

Maak een lege array genaamd playerItems .

```

local playerItems = {}

```

2.

Voeg inventarisitems toe aan de array door [table.insert()](/docs/nl-nl/reference/engine/libraries/table#insert)  te typen. Typ in de haakjes playerItems , de tabel waaraan je wilt toevoegen, gevolgd door een string voor elk item. Voeg ten minste drie waarden toe.

3.

Voer het script uit. Elk item wordt afgedrukt met zijn index.

## [Waarden uit arrays verwijderen](#waarden-uit-arrays-verwijderen)[](#waarden-uit-arrays-verwijderen)

Om een waarde te verwijderen, bijvoorbeeld als een speler een item heeft gebruikt of iemand in een lijst van actieve spelers een spel verlaat, gebruik je [table.remove()](/docs/nl-nl/reference/engine/libraries/table#remove) . Afhankelijk van de opgegeven parameters kan de functie ofwel de laatste waarde van een tabel verwijderen, of op een specifieke index.

### [Verwijder de laatste waarde](#verwijder-de-laatste-waarde)[](#verwijder-de-laatste-waarde)

Soms moet een script een specifiek item verwijderen. Bijvoorbeeld, het verwijderen van het eerste item in de inventaris van een speler, of het kiezen van de eerste speler in een lijst. Om de laatste waarde in een array te verwijderen, gebruik je [table.remove(arrayName)](/docs/nl-nl/reference/engine/libraries/table#remove) . In dit geval is de enige parameter die nodig is de tabel zelf.

1.

Gebruik de array van items uit het vorige voorbeeld. Typ vervolgens om de laatste waarde uit de tabel te verwijderen, in dit geval "Sleeping Bag" , [table.remove(playerItems)](/docs/nl-nl/reference/engine/libraries/table#remove)

2.

Voer het project uit. In het Output-venster zou de laatste waarde, "Sleeping Bag" , niet moeten worden afgedrukt.

### [Verwijder op index](#verwijder-op-index)[](#verwijder-op-index)

Om een waarde op een specifiek punt in de array te verwijderen, voer je in de tweede parameter de index in die je wilt verwijderen, zoals table.remove(arrayName, 1) .

1.

Gebruik dezelfde tabel, typ [table.remove()](/docs/nl-nl/reference/engine/libraries/table#remove) . Voer in de parameters de naam van de tabel en 1 , de waarde die je wilt verwijderen, in.

De tweede parameter voor [table.remove()](/docs/nl-nl/reference/engine/libraries/table#remove)  accepteert alleen een numerieke index. Typen zoals "Potion"  zal een fout veroorzaken.

2.

Voer het project uit. Controleer of de eerste waarde, "Potion", is verwijderd.

Merk ook op dat alle indexwaarden zijn veranderd of zijn verschoven. Het verwijderen van een waarde uit een array zal de grootte van de array veranderen en de indexwaarden omlaag  verschuiven na de verwijderde waarde. "Bread"  is nu index 1, en "Sleeping Bag"  is nu index 2.

## [Zoek naar waarden in een array](#zoek-naar-waarden-in-een-array)[](#zoek-naar-waarden-in-een-array)

Om specifieke waarden in arrays te vinden, zoals de naam van een winnende speler, gebruik je de functie [table.find()](/docs/nl-nl/reference/engine/libraries/table#find) . Alternatief kun je je eigen zoekfunctie coderen met behulp van for -lussen en if -verklaringen.

### [Vind en retourneer een enkele waarde](#vind-en-retourneer-een-enkele-waarde)[](#vind-en-retourneer-een-enkele-waarde)

Om een waarde in een array te vinden, maak je een functie genaamd findValue()  die door een array gaat en stopt de eerste keer dat het een overeenkomende waarde vindt.

Zodra het de waarde vindt, zal de functie het return -trefwoord gebruiken om de index van die waarde terug te geven. Met een index kun je het uit de array verwijderen.

1.

Kopieer de array genaamd playerItems  hieronder.

```

local playerItems = {

	"Potion",

	"Bread",

	"Bread",

	"Sleeping Bag"

}

```

2.

Codeer een nieuwe functie genaamd findValue()  met twee parameters:

-

whichArray  - de array om doorheen te zoeken.

-

itemName  - de specifieke string om op te controleren.

```

local function findValue(whichArray, itemName)

end

```

3.

In findValue() , gebruik een for-lus om te controleren of een waarde in de array overeenkomt met itemName . Als de waarde overeenkomt, gebruik dan het trefwoord return  om de waarde die is gevonden in currentIndex  terug te geven.

```

local function findValue(whichArray, itemName)

	for currentIndex = 1, #whichArray do

		if whichArray[currentIndex] == itemName then

			return currentIndex

		end

	end

end

```

4.

Test de zoekfunctie door een variabele genaamd valueFound  te maken en findValue()  aan te roepen. Geef de array door om te zoeken, en welke waarde het moet zoeken. Voer  de code uit om te bevestigen dat de verwachte uitvoer index 2 is.

### [Verwijder een waarde](#verwijder-een-waarde)[](#verwijder-een-waarde)

Als een waarde is gevonden met behulp van de vindfunctie, kan deze worden verwijderd. Controleer of een waarde is gevonden met een if-verklaring.

1.

Controleer of een waarde in valueFound  zit; zo ja, verwijder de waarde met [table.remove()](/docs/nl-nl/reference/engine/libraries/table#remove) .

```

if valueFound then

	table.remove(playerItems, valueFound)

end

```

2.

Print de array uit met de onderstaande code.

```

for index = 1, #playerItems do

	local itemString = playerItems[index]

	print("Index " .. index .. ": " .. itemString)

end

```

3.

Speeltest en controleer of de eerste "Bread" -waarde uit de array is verwijderd. Probeer andere waarden te verwijderen door de tweede parameter in findValue()  te wijzigen.

Merk op dat omdat deze functie eenmaal is aangeroepen, alleen de eerste instantie van "Bread"  is verwijderd. De volgende sectie behandelt hoe je alle instanties kunt vinden en verwijderen.

## [Vind en verwijder alle specifieke waarden](#vind-en-verwijder-alle-specifieke-waarden)[](#vind-en-verwijder-alle-specifieke-waarden)

Terwijl de vorige code alleen de eerste instantie van een gevonden waarde kon verwijderen, zal deze codefragment alle voorkomens uit een array vinden en verwijderen. Bijvoorbeeld, als een speler al zijn brood in een in-game winkel wilde verkopen.

1.

Gebruik een array genaamd playerItems  met ten minste vier waarden en een set van duplicaten .

```

local playerItems = {

	"Potion",

	"Bread",

	"Bread",

	"Sleeping Bag"

}

```

2.

Om door de array te gaan, maak je een for-lus die achteruit  door playerItems  gaat, beginnend bij #playerItems , eindigend bij 1, en met een stap van -1.

```

for index = #playerItems, 1, -1 do

end

```

Vergeet niet dat het verwijderen van items later indexen doet verschuiven. Door aan het einde te beginnen, voorkom je dat je een waarde overslaat die mogelijk is verschoven als je aan het begin was begonnen.

3.

Gebruik in de lus een if-verklaring om te controleren of de waarde in playerItems[index]  gelijk is aan "Bread" , en als dat zo is, verwijder het item.

```

for index = #playerItems, 1, -1 do

	if playerItems[index] == "Bread" then

		table.remove(playerItems, index)

	end

end

```

4.

Gebruik de onderstaande code om een tweede for-lus toe te voegen die de array afdrukt.

```

for index = 1, #playerItems do

	local itemString = playerItems[index]

	print("Index " .. index .. ": " .. itemString)

end

```

5.

Voer het script uit en controleer of alle waarden genaamd "Bread" zijn verwijderd.

## [Samenvatting](#samenvatting)[](#samenvatting)

Waarden kunnen aan een array worden toegevoegd of verwijderd, maar wees voorzichtig met het verschuiven van indexen. Gebruik lussen om door een tabel te itereren om alle instanties van een waarde te verwijderen, of alleen de eerste gevonden instantie.

Het trefwoord return  kan worden gebruikt om een lus te stoppen en informatie terug te sturen waar nodig.

Een voltooide versie van het script kan hieronder worden geraadpleegd.

Het volgende project bevat alle scripts in deze tutorial. Download het [voltooide project](https://prod.docsiteassets.roblox.com/assets/education/coding-5/Making_Changes_to_Arrays_-_Final_Project.rbxl) .

Let op dat alle scripts zich in ServerScriptService  bevinden en uitgeschakeld  zijn. Om een script te gebruiken, vink je in de eigenschappen het veld Uitgeschakeld uit en voer je Studio uit.

Voor een complete lijst van alle tabelfuncties, ga naar [Table API](/docs/nl-nl/reference/engine/libraries/table)

[Volgende](/docs/nl-nl/tutorials/fundamentals/coding-5/intro-to-dictionaries)[Vorige](/docs/nl-nl/tutorials/fundamentals/coding-5/loops-and-arrays)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
