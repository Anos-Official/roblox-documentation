<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/fundamentals/coding-5/pairs-and-ipairs -->

pairs en ipairs | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. [Woordenboeken en arrays](/docs/nl-nl/tutorials/fundamentals/coding-5/landing)

# pairs en ipairs

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Veel scripts moeten vaak door woordenboeken of arrays gaan. Maar soms weet je misschien niet het begin en het einde van deze datastructuren. Bijvoorbeeld, een woordenboek van spelers kan veranderen, of spelers kunnen een array-inventaris van verschillende groottes hebben.

In deze situaties kun je pairs()  en ipairs()  gebruiken. Deze kunnen worden gebruikt met een for-lus om door elk element te gaan zonder bekende start- en eindpunten.

Dit artikel behandelt het gebruik ervan en heeft een praktisch scriptvoorbeeld waarin je restaurantbestellingen bijhoudt in een kookspel.

## [Woordenboeken en pairs()](#woordenboeken-en-pairs)[](#woordenboeken-en-pairs)

pairs()  wordt gebruikt met woordenboeken . Een voorbeeld is hieronder te zien.

pairs()  kan worden gebruikt om met de sleutel, waarde of beide van een woordenboekelement te werken. In de for-lus hieronder is de eerste variabele de sleutel. De tweede variabele is de waarde. Het woordenboek waarmee je wilt werken, wordt doorgegeven aan pairs() .

Wanneer uitgevoerd, zal de code het volgende afdrukken. pairs()  garandeert geen volgorde, dus deze regels kunnen anders worden afgedrukt.

```

Je hebt:

43 Gouden Bakstenen

3 Wortels

2 Fakkels

```

## [Arrays en ipairs()](#arrays-en-ipairs)[](#arrays-en-ipairs)

ipairs()  wordt gebruikt met arrays . De "i" in ipairs()  staat voor "index." Gebruik ipairs()  en arrays in combinatie met een for-lus om met geordende waarden zoals ranglijsten te werken. Een voorbeeld is hieronder.

Wanneer uitgevoerd, zal de code het volgende afdrukken:

```

Winnaar #1 is Ali

Winnaar #2 is Ben

Winnaar #3 is Cammy

```

## [Oefening - Restaurant Soep Simulator](#oefening---restaurant-soep-simulator)[](#oefening---restaurant-soep-simulator)

Laten we wat soep maken voor een restaurant simulator waar spelers kiezen uit een lijst van mogelijke soep ingrediënten. De ingrediënten worden opgeslagen als sleutels, en de waarden beginnen als false zodat de spelers alleen krijgen wat ze selecteren.

Gebruik pairs()  om te zien wat is gekozen, en gebruik vervolgens ipairs()  om de lijst van ingrediënten af te drukken.

1.

Maak een nieuw woordenboek  genaamd menu . Voeg 3 - 5 sleutel-waarde paren toe waarbij de sleutel het ingrediënt is en de waarde false is.

```

local menu = {

	kool = false,

	vlees = false,

	tomaat = false,

	noedels = false,

}

```

2.

Onder het menu-woordenboek, voeg een lege array  toe die later zal worden gevuld met de keuzes van de klant.

```

-- Soep van de klant

local selectedIngredients = {}

```

3.

Gebruik pairs()  om te controleren of elk ingrediënt in het woordenboek als true of false is gemarkeerd. Als het true is, voeg het ingrediënt dan toe aan de soep.

```

-- Soep van de klant

local selectedIngredients = {}

-- Voegt de keuzes van de klant toe aan hun soep

for menuChoice, value in pairs(menu) do

	if value then

		table.insert(selectedIngredients, menuChoice)

	end

end

```

4.

Herhaal de bestelling terug naar de klant. In het script, codeer het volgende hieronder.

-

Controleer of er een menu-item in selectedIngredients  is. Zo ja, print "Je bestelde soep met: " .

-

Gebruik ipairs()  om door de selectedIngredients  array te gaan en elk ingrediënt af te drukken.

-

Test door ten minste één menu-item op true te zetten.

```

-- Drukt de soepbestelling af van "selectedIngredients"

if #selectedIngredients > 0 then

	print("Je bestelde soep met: ")

	for index, soupIngredient in ipairs(selectedIngredients) do

		print(soupIngredient)

	end

end

```

5.

In de if-verklaring die controleert of er een menu-item is, voeg een else-voorwaarde toe die klanten vertelt of er geen ingrediënten zijn geselecteerd.

De bovenstaande stap is een voorbeeld van foutcontrole in de informatica. Het is altijd een goede praktijk om te coderen wat er gebeurt als er een ontbrekende waarde mogelijk in je code is. Zo niet, dan is het mogelijk dat er een fout optreedt tijdens de uitvoering.

## [Optionele uitdagingen](#optionele-uitdagingen)[](#optionele-uitdagingen)

Hieronder staan enkele uitdagingen die van toepassing zijn op het gebruik van pairs en ipairs op verschillende manieren. Probeer te zien of je de code voor deze kunt opbouwen.

Uitdaging : Maak een Ober NPC In plaats van het Output-venster te gebruiken, gebruik de NPC van [Intro To Arrays](/docs/nl-nl/tutorials/fundamentals/coding-5/intro-to-arrays)  om een ober te maken die klantbestellingen opneemt.

Uitdaging : Laat Spelers Bestellingen Plaatsen Laat spelers een ingrediënt selecteren door een fysiek onderdeel aan te raken, zoals een nabijheidsprompt. Voor meer informatie, zie [Nabijheidsprompten](/docs/nl-nl/ui/proximity-prompts) .

Geavanceerde Uitdaging : Maak Me Een Soep Simulator Creëer een restaurant simulator waar spelers de koks zijn! Spelers moeten ingrediënten samenstellen om de bestelling te matchen die ze van de ober krijgen.

1.

Maak in-game props voor 3 - 5 verschillende ingrediënten.

2.

Maak 3 - 5 recepten met woordenboeken die vergelijkbaar zijn met die in deze les.

3.

Maak een array die alle recepten bevat.

4.

Selecteer willekeurig een recept en gebruik een NPC om spelers te vertellen wat de ingrediënten zijn.

5.

Maak een nieuw woordenboek om een recept te maken op basis van welke prop-ingrediënten de speler aanraakt.

6.

Vergelijk het recept van de speler met het recept dat door de NPC is gekozen.

7.

Verhoog de uitdaging door een extra voorwaarde toe te voegen, zoals een timer.

[Volgende](/docs/nl-nl/tutorials/fundamentals/coding-5/return-values-from-tables)[Vorige](/docs/nl-nl/tutorials/fundamentals/coding-5/intro-to-dictionaries)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
