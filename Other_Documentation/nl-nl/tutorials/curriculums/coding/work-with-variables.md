<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/curriculums/coding/work-with-variables -->

Werken met variabelen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Werken met variabelen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

In codering zijn variabelen  plaatsvervangende woorden voor verschillende soorten informatie in je spel, zoals spelersnamen, de score van een team of woorden voor een verhaalspel. In dit hoofdstuk gaan we onderzoeken hoe je het hoofdscript voor de kern gameplay opent en code toevoegt om spelers vragen te stellen en hun antwoorden te gebruiken voor jouw verhaal.

## [Open script](#open-script)[](#open-script)

Roblox-makers schrijven hun code in scripts  die Studio vertellen hoe en wanneer ze aangepaste gedragingen aan spellen moeten toevoegen, zoals het activeren van verschillende soorten evenementen, het opslaan van spelersinformatie of het spawnen van vijanden. Roblox-scripts gebruiken de [Luau](https://luau.org)  programmeertaal, waar je later meer over kunt leren in de [Basisprincipes van coderen](/docs/nl-nl/../../fundamentals/coding-1)  serie.

De Story Game-sjabloon gebruikt een enkel script genaamd StoryManager  om de kern gameplay van het spel te controleren. Dit script bevat al wat code die nodig is om het volledige verhaal aan de speler te tonen, maar je zult meer toevoegen om jouw interactieve verhaal weer te geven.

Om het StoryManager  script te openen:

1.

Klik in het Explorer -venster op de pijl naast StarterGui  om alles te zien wat het bevat. GameGui  wordt weergegeven.

2.

Klik op de pijl naast GameGui  om alles te zien wat het bevat. Het StoryManager  script wordt bovenaan weergegeven, samen met een paar andere dingen die niet belangrijk zijn voor deze les.

 ![](https://prod.docsiteassets.roblox.com/assets/education/story-games/StoryManager.png)

3.

Dubbelklik op het StoryManager  script. De code van het script wordt weergegeven.

```

-- GLOBAL VARIABLES

local storyMaker = require(script:WaitForChild("StoryMaker"))

-- Code die het spel bestuurt

local playing = true

while playing do

	storyMaker:Reset()

	-- Code verhaal tussen de streepjes

	-- =============================================

	-- =============================================

	-- Voeg de verhaalvariabele tussen de haakjes hieronder toe

	storyMaker:Write()

	-- Opnieuw spelen?

	playing = storyMaker:PlayAgain()

end

```

Let op hoe een groot deel van de code het --  symbool gebruikt, wat een opmerking  wordt genoemd. Programmeurs gebruiken opmerkingen om aantekeningen achter te laten, en ze veranderen niet de manier waarop het script draait. Voor deze les ga je jouw code tussen de streepjes opmerkingen maken, zodat je je kunt concentreren op het creëren van jouw interactieve verhaal op één plek.

## [Stel spelers vragen](#stel-spelers-vragen)[](#stel-spelers-vragen)

Als beste praktijk creëren programmeurs variabelen met namen die het type informatie beschrijven dat ze opslaan. Bijvoorbeeld, als je aan een spel werkt waarin spelers in teams worden verdeeld:

-

De team  variabele slaat informatie op over het team  van de speler.

-

De teamColor  variabele slaat informatie op over de teamkleur  van de speler.

-

De teamScore  variabele slaat informatie op voor de teamscore  van de speler.

Variabelen kunnen allerlei soorten informatie opslaan, zoals kleine getallen, waar of niet waar antwoorden, en strings. String-variabelen zijn speciaal omdat ze hele zinnen kunnen opslaan, inclusief de vragen die je aan je spelers wilt stellen.

Met behulp van jouw plaatsvervangende woorden uit het vorige hoofdstuk, kun je string-variabelen maken met dezelfde plaatsvervangende namen die beschrijven welk type woord je de speler gaat vragen terwijl ze jouw verhaalspel spelen.

Om variabelen voor jouw spelersvragen te maken:

1.

Klik onder de streepjes opmerkingen en maak een lokale variabele voor het eerste woord dat je wilt dat spelers vervangen door hun eigen antwoord. Bijvoorbeeld:

```

-- =============================================

   local name1

-- =============================================

```

2.

Stel de variabele in met het =  symbool op de gegeven storyMaker:GetInput()  methode die jouw vragen in het grote boek weergeeft. Je moet deze methode precies zo typen als hij is, met de specifieke hoofdletters, zodat de code werkt. Bijvoorbeeld:

```

-- =============================================

   local name1 = storyMaker:GetInput()

-- =============================================

```

3.

Maak een string tussen de haakjes met de vraag die je aan jouw spelers wilt stellen. Vergeet niet, strings staan altijd tussen aanhalingstekens!

```

-- =============================================

   local name1 = storyMaker:GetInput("Wat is jouw favoriete naam?")

-- =============================================

```

## [Gebruik hun antwoorden](#gebruik-hun-antwoorden)[](#gebruik-hun-antwoorden)

Nu je een vraag hebt die spelers kunnen beantwoorden, is het tijd om jouw verhaal te coderen en gedrag toe te voegen dat jouw plaatsvervangende woord vervangt door hun antwoord.

Om variabelen voor jouw verhaal te maken en de antwoorden van spelers te gebruiken:

1.

Onder jouw vraag, maak een nieuwe variabele genaamd verhaal. Vergeet niet, variabelen zijn klein geschreven!

```

-- =============================================

   local name1 = storyMaker:GetInput("Wat is jouw favoriete naam?")

   local story

-- =============================================

```

2.

Stel jouw string-variabele in op de eerste zin van jouw verhaal vóór jouw eerste plaatsvervangend woord, waarbij je een spatie laat na het laatste woord en vóór het aanhalingsteken. Als jouw plaatsvervangende woord zich toevallig in het midden van een zin bevindt, kun je de rest van de zin in een later hoofdstuk van de tutorial toevoegen.

```

-- =============================================

   local name1 = storyMaker:GetInput("Wat is jouw favoriete naam?")

   local story = ("In een boom op een heuvel woont de grote tovenaar ")

-- =============================================

```

3.

Combineer de eerste string van het verhaal met het antwoord van de speler met behulp van .. . Het samenvoegen van dingen wordt concatenatie  genoemd.

1.

Voeg op dezelfde regel als de story  variabele twee punten toe.

2.

Voeg een spatie toe en typ de naam van de variabele die het eerste antwoord van de speler opslaat.

```

-- =============================================

   local name1 = storyMaker:GetInput("Wat is jouw favoriete naam?")

   local story = ("In een boom op een heuvel woont de grote tovenaar " .. name1)

-- =============================================

```

4.

Toon dit eerste deel van het verhaal aan de spelers door de verhaalvariabele aan te roepen vanuit de gegeven storyMaker:Write()  methode die jouw verhaal in het grote boek schrijft.

```

-- =============================================

   local name1 = storyMaker:GetInput("Wat is jouw favoriete naam?")

   local story = ("In een boom op een heuvel woont de grote tovenaar " .. name1)

-- =============================================

-- =============================================

storyMaker:Write(story)

```

Dit is een goed moment om even te stoppen, het spel in het volgende hoofdstuk te testen en ervoor te zorgen dat het verhaal werkt!

[Volgende](/docs/nl-nl/tutorials/curriculums/coding/test-and-save)[Vorige](/docs/nl-nl/tutorials/curriculums/coding/get-started)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
