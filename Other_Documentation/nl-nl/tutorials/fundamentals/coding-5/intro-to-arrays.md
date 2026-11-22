<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/fundamentals/coding-5/intro-to-arrays -->

Introductie tot arrays | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. [Woordenboeken en arrays](/docs/nl-nl/tutorials/fundamentals/coding-5/landing)

# Introductie tot arrays

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Gegevensstructuren  zijn hoe programmeurs hele sets gegevens opslaan en organiseren. In Luau worden gegevensstructuren gemaakt met tabellen. Tabellen  kunnen een onbeperkt aantal waarden bevatten.

Dit artikel behandelt het gebruik van arrays , een specifiek type tabel, om een sprekend personage te creëren.

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-5/coding4_introToTables.jpg)

## [Tabellen](#tabellen)[](#tabellen)

Tabellen  zijn gegevenstypen die meerdere waarden kunnen bevatten. In tegenstelling tot andere gegevenstypen die een enkele waarde opslaan, hebben tabellen geen vaste grootte en kunnen ze een mix van verschillende gegevenstypen bevatten. Met tabellen kun je items in de inventaris van een speler opslaan of een lijst maken van duizenden spelersnamen.

### [Arrays](#arrays)[](#arrays)

Er zijn verschillende soorten tabellen. Een type is een array , die lijsten van waarden in een specifieke volgorde opslaat. Om een array te maken, maak je een variabele en wijs je deze toe met accolades { } . Scheid waarden binnen de accolades met komma's, zoals hieronder:

local myArray = {"item1", "item2", 10, workspace.Part, myVariable}

### [Maak een sprekend personage](#maak-een-sprekend-personage)[](#maak-een-sprekend-personage)

Om arrays te verkennen, ga je werken met een niet-speelbaar personage (NPC) dat, wanneer erop geklikt, een andere zin dialoog toont.

Dit project maakt gebruik van een vooraf gemaakte NPC-model, dat een gedeeltelijk script en Prompt Detector bevat, maar geen dialoog heeft.

1.

Download het sjabloon NPC.

 [Downloaden](https://prod.docsiteassets.roblox.com/assets/education/coding-5/TemplateNPC.rbxm)

2.

Importeer de NPC in Explorer door met de rechtermuisknop op Workspace  ⟩ Invoegen vanuit bestand  te klikken en het gedownloade bestand te selecteren.

## [Code een dialoogarray](#code-een-dialoogarray)[](#code-een-dialoogarray)

Deze stappen gebruiken een array om verschillende zinnen op te slaan die de NPC kan zeggen wanneer spelers ermee interageren.

1.

Ga in de Explorer  naar NPC  ⟩ ProximityPrompt  ⟩ ChatManager .

2.

Maak in ChatManager, waar gemarkeerd in het script, een lege array  aan om dialoogopties op te slaan.

```

-- Doorloopt chatdialoog wanneer prompt wordt gebruikt

local Chat = game:GetService("Chat")

local prompt = script.Parent

local npc = prompt.Parent

local characterParts = npc.CharacterParts

local head = characterParts.Head

-- Voeg hier array toe

local dialogueArray = {}

local function speak()

	local dialogue = "Ik heb één ding te zeggen!"

	Chat:Chat(head, dialogue)

end

prompt.Triggered:Connect(speak)

```

Deze les gebruikt de legacy chat API en is strikt bedoeld om te demonstreren hoe je arrays gebruikt. Gebruik in echte games [TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService) .

3.

Typ binnen de accolades {}  van de zojuist gemaakte array ten minste drie strings van dialoog, gescheiden door komma's.

```

local dialogueArray = {"Hallo!", "Ken ik jou?", "Tot ziens!"}

```

## [Gebruik array-indexen](#gebruik-array-indexen)[](#gebruik-array-indexen)

Elke waarde in de array krijgt een index -nummer. Indexen worden toegewezen aan waarden in de volgorde waarin de waarden zijn opgeslagen. De eerste waarde staat op index 1, de tweede op index 2, enzovoort.

Sommige programmeertalen, zoals Java, beginnen indexen bij 0.

In de zojuist gemaakte array staat "Hallo!"  op index 1, en "Tot ziens!"  staat op index 3.

| Index | | Waarde |
| --- | --- |
| 1 | | Hallo! |
| 2 | | Vandaag is een geweldige dag! |
| 3 | | Tot ziens! |

## [Gebruik specifieke indexwaarden](#gebruik-specifieke-indexwaarden)[](#gebruik-specifieke-indexwaarden)

Gebruik indexwaarden om specifieke stukjes dialoog aan de NPC toe te wijzen. Om een waarde op een specifieke index te gebruiken, voeg je de index in haakjes direct achter de naam van de array toe, zoals dialogueArray[1] .

1.

Vervang de standaard stringwaarde van de dialogue -variabele door index 2. Index 2 is de tweede string.

```

local dialogueArray = {"Hallo!", "Ken ik jou?", "Tot ziens!"}

local function speak()

	local dialogue = dialogueArray[2]

	Chat:Chat(head, dialogue)

end

```

Als een index niet bestaat, verschijnt er een nil -fout in de Output. Bijvoorbeeld, aangezien deze array slechts drie waarden heeft, zal het gebruik van dialogueArray[4]  resulteren in een fout.

2.

Speeltest en klik op de NPC. De tweede arraywaarde zou in de chatbubble moeten verschijnen. Probeer de code te wijzigen om elke waarde in de tabel te testen.

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-5/introArrays_showSpeech.jpg)

## [Wijzig dialoogregels](#wijzig-dialoogregels)[](#wijzig-dialoogregels)

Wanneer de speler met de NPC interageert, zal de NPC altijd dezelfde regel zeggen. Dat is saai. Gebruik in plaats daarvan een variabele om bij te houden welke indexwaarde moet worden gebruikt.

Telkens wanneer een speler met de NPC interageert, verhoog je de waarde van de variabele met 1 om de volgende regel dialoog weer te geven.

1.

Om bij te houden welke index momenteel is, voeg je een nieuwe variabele genaamd dialogueIndex  toe. Stel de variabele in op 1 om te beginnen bij het begin van de array.

```

local dialogueArray = {"Hallo!", "Ken ik jou?", "Tot ziens!"}

local dialogueIndex = 1

```

2.

In speak() , vervang  het indexnummer in dialogueArray[2]  door de variabele die je zojuist hebt gemaakt.

```

local function speak()

	local dialogue = dialogueArray[dialogueIndex]

	Chat:Chat(head, dialogue)

end

```

3.

Voeg onderaan de functie 1 toe aan dialogueIndex . De volgende keer dat speak()  wordt aangeroepen, wordt de dialoog de volgende string weergegeven.

```

local function speak()

	local dialogue = dialogueArray[dialogueIndex]

	Chat:Chat(head, dialogue)

	dialogueIndex += 1

end

```

4.

Speeltest en klik op de NPC om elke dialoogstring uit de array te zien.

Merk op dat er een fout  in het Output-venster verschijnt zodra het script het einde van de array bereikt.

Je zult dit in de volgende sectie oplossen, zodat de dialoog opnieuw begint vanaf het begin nadat de laatste string is weergegeven.

## [Arraygroottes](#arraygroottes)[](#arraygroottes)

Je kunt de grootte van de array gebruiken om te weten wanneer je de gewenste index opnieuw op 1 moet instellen. Vind de grootte  van een array door # , zonder spaties, voor de naam van de array te typen.

Bijvoorbeeld: #dialogueArray

Controleer de grootte van de array tegen de huidige waarde van de variabele om te weten wanneer het tijd is om weer bij het begin te beginnen.

### [Herstart de dialoog](#herstart-de-dialoog)[](#herstart-de-dialoog)

Gebruik de grootte van de array om te controleren wanneer het tijd is om terug te keren naar het eerste stuk dialoog.

1.

Voeg een if-statement toe en controleer of dialogueIndex  gelijk is aan #dialogueArray , de totale grootte van deze array. Als dat zo is, stel dan dialogueIndex  in op 1.

```

local function speak()

	local dialogue = dialogueArray[dialogueIndex]

	Chat:Chat(head, dialogue)

	if dialogueIndex == #dialogueArray then

		dialogueIndex = 1

	end

	dialogueIndex += 1

end

```

2.

Als dialogueIndex  niet aan het einde is, moet het nog steeds 1 aan dialogueIndex  toevoegen. Verplaats dialogueIndex += 1  onder een else-statement.

```

local function speak()

	local dialogue = dialogueArray[dialogueIndex]

	Chat:Chat(head, dialogue)

	dialogueIndex = if dialogueIndex == #dialogueArray then 1 else dialogueIndex + 1

end

```

3.

Speel en bevestig dat je door de dialoog kunt cyclusen en deze opnieuw kunt starten.

## [Samenvatting](#samenvatting)[](#samenvatting)

Gegevensstructuren zijn hoe sets gegevens worden opgeslagen. Luau gebruikt tabellen om gegevensstructuren te creëren. Arrays zijn een type tabel die geordende lijsten van informatie kan bevatten. Elke waarde binnen de array krijgt een indexnummer, beginnend met index 1.

Dit script gebruikte een array om een lijst van mogelijke dialoogregels voor een niet-speelbaar personage (NPC) te creëren.

Voltooid script

```

-- Doorloopt chatdialoog wanneer prompt wordt gebruikt

local Chat = game:GetService("Chat")

local prompt = script.Parent

local npc = prompt.Parent

local characterParts = npc.CharacterParts

local head = characterParts.Head

-- Voeg hier array toe

local dialogueArray = {"Hallo!", "Ken ik jou?", "Tot ziens!"}

local dialogueIndex = 1

local function speak()

	local dialogue = dialogueArray[dialogueIndex]

	Chat:Chat(head, dialogue)

	dialogueIndex = if dialogueIndex == #dialogueArray then 1 else dialogueIndex + 1

end

prompt.Triggered:Connect(speak)

```

### [Probleemoplossingstips](#probleemoplossingstips)[](#probleemoplossingstips)

Als het personage niet door de array van dialoog gaat, probeer dan de volgende probleemoplossingstips.

-

Controleer de if-statement dat dialogueIndex  weer op 1 wordt ingesteld. Controleer in de else-statement of dialogueIndex  1 aan zichzelf heeft toegevoegd.

-

Zorg ervoor dat er geen spaties na de # staan bij het verkrijgen van de grootte van de array in #dialogueArray .

## [Optionele uitdagingen](#optionele-uitdagingen)[](#optionele-uitdagingen)

Probeer een van de onderstaande optionele uitdagingen.

-

Code het script zodat de dialoog van de NPC achteruit door de array gaat. De dialoogindex moet beginnen bij de lengte van de array en elke keer aftrekken in plaats van optellen.

-

In plaats van dialoog in volgorde weer te geven, laat de NPC elke keer een willekeurige regel dialoog tonen met behulp van [Random.new()](/docs/nl-nl/reference/engine/datatypes/Random#new) . Een voorbeeldscript is hieronder opgenomen ter referentie.

```

local randomGenerator = Random.new()

-- Toont een nieuwe dialoog telkens wanneer de NPC wordt geklikt

local function speak()

	local randomIndex = randomGenerator:NextInteger(1, #dialogueArray)

	local dialogue = dialogueArray[randomIndex]

	Chat:Chat(head, dialogue)

end

```

[Volgende](/docs/nl-nl/tutorials/fundamentals/coding-5/loops-and-arrays)[Vorige](/docs/nl-nl/tutorials/fundamentals/coding-5/landing)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
