<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/curriculums/coding/customize-strings -->

Pas strings aan | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Pas strings aan

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Met de eerste zin van je verhaal die klaar is en werkt in Studio, is het tijd om je string aan te passen met interpunctie en regelafbrekingen. Zodra je tevreden bent met hoe het eruitziet en leest voor spelers, kun je meer zinnen toevoegen en de rest van je verhaal afmaken.

## [Voeg interpunctie toe](#voeg-interpunctie-toe)[](#voeg-interpunctie-toe)

Wanneer je je spel test, bevat je eerste zin geen interpunctie om spelers te laten weten dat de zin compleet is. Om dit op te lossen, kun je een andere string toevoegen met dezelfde concatenatie om je woorden met je interpunctie te verbinden.

Om interpunctie toe te voegen:

1.

Typ op dezelfde regel als de story -variabele twee punten.

2.

Voeg een andere string toe met een leesteken, zoals een punt of uitroepteken, gevolgd door een extra spatie zodat je volgende zin niet onmiddellijk na het leesteken begint.

```

-- =============================================

   local name1 = storyMaker:GetInput("Wat is je favoriete naam?")

   local story = ("In een boom op een heuvel woont de grote tovenaar " .. name1 .. "! ")

-- =============================================

-- =============================================

storyMaker:Write(story)

```

## [Voeg regelafbrekingen toe](#voeg-regelafbrekingen-toe)[](#voeg-regelafbrekingen-toe)

Een regelafbreking verplaatst de cursor naar de volgende regel tekst. Dit is handig wanneer je wilt dat elke zin aan de linkerkant van de pagina begint, en de leesbaarheid van je verhaal in het grote boek verbetert.

Om een regelafbreking toe te voegen:

1.

Typ op dezelfde regel als de story -variabele \n .

```

-- =============================================

   local name1 = storyMaker:GetInput("Wat is je favoriete naam?")

   local story = ("In een boom op een heuvel woont de grote tovenaar " .. name1 .. "! \n")

-- =============================================

-- =============================================

storyMaker:Write(story)

```

2.

OPTIONEEL

 Je kunt meer dan één regelafbreking toevoegen door zoveel \n  toe te voegen als je nodig hebt. Bijvoorbeeld, de volgende codevoorbeelden voegen drie regelafbrekingen toe.

```

-- =============================================

   local name1 = storyMaker:GetInput("Wat is je favoriete naam?")

   local story = ("In een boom op een heuvel woont de grote tovenaar " .. name1 .. "! \n\n\n")

-- =============================================

-- =============================================

storyMaker:Write(story)

```

## [Voeg meer zinnen toe](#voeg-meer-zinnen-toe)[](#voeg-meer-zinnen-toe)

Nu je eerste zin interpunctie en eventuele regelafbrekingen bevat, kun je meer zinnen aan je verhaal toevoegen en spelers meer vragen stellen voor je tijdelijke woorden.

Om meer zinnen toe te voegen:

1.

Maak onder je eerste variabele een nieuwe variabele voor je tweede tijdelijke woord en stel een vraag die gerelateerd is aan wat voor soort tijdelijk woord het is. Bijvoorbeeld:

```

-- =============================================

   local name1 = storyMaker:GetInput("Wat is je favoriete naam?")

   local food1

   local story = ("In een boom op een heuvel woont de grote tovenaar " .. name1 .. "! \n\n\n")

-- =============================================

-- =============================================

storyMaker:Write(story)

```

2.

Gebruik hetzelfde proces als je eerste variabele, stel de variabele in en gebruik de gegeven storyMaker:GetInput() -methode die je vragen in het grote boek weergeeft. Bijvoorbeeld:

```

-- =============================================

   local name1 = storyMaker:GetInput("Wat is je favoriete naam?")

   local food1 = storyMaker:GetInput("Wat eet je graag?")

   local story = ("In een boom op een heuvel woont de grote tovenaar " .. name1 .. "! \n\n\n")

-- =============================================

-- =============================================

storyMaker:Write(story)

```

3.

Combineer de eerste string van het verhaal met het antwoord van de speler met behulp van .. .

1.

Typ op dezelfde regel als de story -variabele twee punten.

2.

Voeg een spatie toe, typ dan de naam van de variabele die het tweede antwoord van de speler opslaat.

3.

Voeg nog twee punten toe, en eindig de zin met een leesteken.

```

-- =============================================

   local name1 = storyMaker:GetInput("Wat is je favoriete naam?")

   local food1 = storyMaker:GetInput("Wat eet je graag?")

   local story = ("In een boom op een heuvel woont de grote tovenaar " .. name1 .. "! \n\n\n" .. "Elke ochtend houdt de tovenaar ervan om een enorme kom met honinggebrande " .. food1 .. " te eten. ")

-- =============================================

-- =============================================

storyMaker:Write(story)

```

4.

Herhaal dit proces voor je hele verhaal, en test je spel met de stappen uit het vorige hoofdstuk om ervoor te zorgen dat je code goed werkt.

[Volgende](/docs/nl-nl/tutorials/curriculums/coding/next-steps)[Vorige](/docs/nl-nl/tutorials/curriculums/coding/test-and-save)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
