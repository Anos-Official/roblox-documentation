<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/fundamentals/coding-3/multiple-conditions -->

Meerdere voorwaarden | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. [Voorwaarden](/docs/nl-nl/tutorials/fundamentals/coding-3/landing)

# Meerdere voorwaarden

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Controle structuren kunnen meer dan één voorwaarde hebben. De sleutelwoorden else  en elseif  kunnen extra scenario's creëren voor wat er moet gebeuren onder verschillende voorwaarden. De syntaxis ziet er als volgt uit:

In dit project worden else  en elseif  gebruikt om een parkourcursus te coderen waarbij hardlopers prijzen ontvangen afhankelijk van hun finishtijd.

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-3/coding3Hero_ifElseIf.jpg)

## [Code meerdere voorwaarden](#code-meerdere-voorwaarden)[](#code-meerdere-voorwaarden)

Voor dit project zou je een unieke if-statement voor elke medaille kunnen schrijven om spelers te belonen, maar dat kost veel tijd. Neem bijvoorbeeld de imaginaire code hieronder.

Alle if-statements

```

if finishTime < 5  then

	-- Krijg een gouden medaille

end

if finishTime >= 5 and <= 10 then

	-- Krijg een zilveren medaille

end

if finishTime > 10 and <= 15 then

	-- Krijg een bronzen medaille

end

```

Een leesbaardere en efficiëntere manier om dit te coderen is door een enkele if-statement te gebruiken en het sleutelwoord elseif  te gebruiken om alternatieve voorwaarden te bieden om te testen of de vorige voorwaarden niet waar zijn.

Gebruikt elseif en else

```

if finishTime < 5  then

	-- Krijg een gouden medaille

elseif finishTime >= 5 and <= 10 then

	-- Krijg een zilveren medaille

elseif finishTime > 10 and <= 15 then

	-- Krijg een bronzen medaille

end

```

Wanneer de if/then-statement wordt uitgevoerd, begint deze bovenaan en voert alleen de code uit voor de eerste  waarheidsgetrouwe voorwaarde die wordt gevonden.

## [Stel de racebaan in](#stel-de-racebaan-in)[](#stel-de-racebaan-in)

Begin met het plaatsen van het startpunt van de cursus en de finishlijn, en maak vervolgens een script om de speler te timen en verschillende medailles toe te kennen.

1.

Maak een verankerd onderdeel genaamd FinishLine. Om het testen sneller te maken, plaats je het begin en het einde dicht bij elkaar. Je kunt de finishlijn verplaatsen nadat je het script hebt voltooid.

![](https://prod.docsiteassets.roblox.com/assets/education/coding-3/raceCourse_showPartCraeted.jpg) Finish Onderdeel

![](https://prod.docsiteassets.roblox.com/assets/education/coding-3/raceCourse_showDistanceBetween.jpg) Hele Cursus

2.

In FinishLine, voeg een script toe genaamd RaceManager. Voeg vervolgens een variabele toe om op te slaan hoeveel seconden zijn verstreken sinds de race begon en een tweede variabele om naar FinishLine te verwijzen.

```

local finishLine = script.Parent

local timePassed = 0

```

3.

Maak een functie genaamd finish() .

```

local timePassed = 0

local finishLine = script.Parent

local function finish()

end

```

4.

Op je eigen:

-

Code een functie genaamd partTouched()  die finish()  uitvoert wanneer een speler het aanraakt.

-

Verbind het finishlijnonderdeel met partTouched() .

-

Vergelijk je code met het onderstaande voorbeeld.

```

local function finish()

	print("Raakte de finishlijn aan")

end

local function partTouched(otherPart)

	local character = otherPart.Parent

	local humanoid = character:FindFirstChildWhichIsA("Humanoid")

	if humanoid then

		finish()

	end

end

finishLine.Touched:Connect(partTouched)

```

5.

Speeltest en controleer of finish()  wordt aangeroepen wanneer je de finishlijn aanraakt.

### [Voorkom dat finish() herhaald wordt](#voorkom-dat-finish-herhaald-wordt)[](#voorkom-dat-finish-herhaald-wordt)

Op dit moment, telkens wanneer een speler de finishlijn aanraakt, wordt finish()  continu aangeroepen zolang de speler het onderdeel aanraakt.

Gebruik een boolean , een variabele die waar of niet waar opslaat, om ervoor te zorgen dat finish() slechts één keer wordt aangeroepen.

1.

Maak een nieuwe variabele genaamd raceActive  en stel deze in op true .

```

local timePassed = 0

local finishLine = script.Parent

local raceActive = true

-- Wordt uitgevoerd telkens wanneer de speler het finishlijnonderdeel aanraakt

local function finish()

```

2.

Voeg een tweede voorwaarde toe aan de if-statement om te controleren of raceActive waar is voordat je finish()  aanroept.

```

local function partTouched(otherPart)

	local character = otherPart.Parent

	local humanoid = character:FindFirstChildWhichIsA("Humanoid")

	if humanoid and raceActive == true then

		finish()

	end

end

```

3.

Om te voorkomen dat finish()  opnieuw wordt aangeroepen, stel je raceActive  in op false .

```

local function finish()

	print("Raakte de finishlijn aan")

	raceActive = false

end

```

4.

Speeltest je spel om te controleren of je je testprintstatement slechts één keer ziet.

### [Houd de tijd bij](#houd-de-tijd-bij)[](#houd-de-tijd-bij)

Net als een if-statement kan een while-lus ook een voorwaarde gebruiken om te zien of deze moet draaien. Om de speler te timen, maak je een timer met een while true do-lus die alleen draait wanneer de boolean raceActive  waar is.

1.

Typ onderaan het script while raceActive == true do . Druk op Enter om automatisch aan te vullen en voeg de end  toe.

```

finishLine.Touched:Connect(partTouched)

while raceActive == true do

end

```

Zorg ervoor dat de lus aan de onderkant  van het script staat. Hoewel deze while true do-lus uiteindelijk stopt, moet deze toch aan de onderkant van het script blijven. Dit zorgt ervoor dat de vorige code wordt uitgevoerd voordat de lus wordt bereikt.

2.

Om de spelers te timen, voeg je in de lus 1 toe aan de variabele timePassed  elke seconde. Voeg een printstatement toe om je werk te testen.

```

finishLine.Touched:Connect(partTouched)

while raceActive == true do

	task.wait(1)

	timePassed += 1

	print(timePassed)

end

```

3.

Speeltest het spel en controleer of je elke seconde in het Output  venster ziet verschijnen.

## [Ken medailles toe aan spelers](#ken-medailles-toe-aan-spelers)[](#ken-medailles-toe-aan-spelers)

Om te eindigen, gebruik een if-statement met meerdere voorwaarden om spelers een andere prijsmedaille toe te kennen op basis van hun prestaties. Gebruik een if-statement en twee elseif-statements om de finishtijd van de speler te controleren en hen de juiste medaille toe te kennen.

1.

Om te bevestigen dat elke medaille kan worden toegekend, gebruik printstatements.

```

local function finish()

	raceActive = false

	print("Je bent gefinisht in " .. timePassed)

end

```

2.

Om een gouden medaille toe te kennen, codeer je een if-statement die timePassed  vergelijkt met de gewenste finishtijd. Dit voorbeeld controleert of de tijd van de speler minder dan of gelijk aan 10 seconden was.

```

local function finish()

	raceActive = false

	print("Je bent gefinisht in " .. timePassed)

	if timePassed <= 10 then

		print("Je krijgt een gouden medaille!")

	end

end

```

3.

Speeltest en bevestig dat de gouden medaille kan worden toegekend.

### [Voeg aanvullende voorwaarden toe](#voeg-aanvullende-voorwaarden-toe)[](#voeg-aanvullende-voorwaarden-toe)

Nu je de gouden medaille hebt getest, codeer je voorwaarden voor de andere medailles met behulp van het elseif -sleutelwoord.

1.

Voor de zilveren medaille, gebruik elseif  en het volgende gewenste tijdsbereik. In dit voorbeeld is het bereik groter dan 10 seconden maar minder dan of gelijk aan 20 seconden.

```

local function finish()

	raceActive = false

	print("Je bent gefinisht in " .. timePassed)

	if timePassed <= 10 then

		print("Je krijgt een gouden medaille!")

	elseif timePassed > 10 and timePassed <= 20 then

		print("Je krijgt een zilveren medaille!")

	end

end

```

2.

Gebruik hetzelfde patroon voor de bronzen medaille. Controleer je code met het onderstaande voorbeeld.

```

local function finish()

	raceActive = false

	print("Je bent gefinisht in " .. timePassed)

	if timePassed <= 10 then

		print("Je krijgt een gouden medaille!")

	elseif timePassed > 10 and timePassed <= 20 then

		print("Je krijgt een zilveren medaille!")

	elseif  timePassed > 20 and timePassed <= 30 then

		print("Je krijgt een bronzen medaille!")

	end

end

```

3.

Speeltest voor de zilveren en bronzen medailles.

### [Probleemoplossing tips](#probleemoplossing-tips)[](#probleemoplossing-tips)

Als je de zilveren en bronzen medailles niet ziet verschijnen, probeer dan een van de onderstaande oplossingen.

-

Elke elseif  moet een then hebben na zijn voorwaarde.

-

In partTouched() , zorg ervoor dat de tweede voorwaarde van de if-statement ==  gebruikt, zoals in raceActive == true .

-

Controleer of elke elseif  in scope is. Elke elseif -voorwaarde moet tussen de eerste regel van de if/then-statement en de laatste end  staan.

### [Voeg de else-voorwaarde toe](#voeg-de-else-voorwaarde-toe)[](#voeg-de-else-voorwaarde-toe)

Als de speler geen van de medailles heeft verdiend, moet je hen aanmoedigen om het opnieuw te proberen. In dit geval kun je een else -statement gebruiken, die wordt uitgevoerd als geen andere  voorwaarden waar zijn, om hen een bericht te tonen.

Het wordt aanbevolen dat elke if-statement een else heeft, voor het geval de code niets waar vindt.

1.

Onder de laatste elseif  en boven end , begin een nieuwe regel en typ else . Voeg geen  then toe. Onder else, gebruik een printstatement om hen aan te moedigen het opnieuw te proberen. Houd raceActive = false  van de eerdere stap.

```

local function finish()

	raceActive = false

	print("Je bent gefinisht in " .. timePassed)

	if timePassed <= 10 then

		print("Je krijgt een gouden medaille!")

	elseif timePassed > 10 and timePassed <= 20 then

		print("Je krijgt een zilveren medaille!")

	elseif  timePassed > 20 and timePassed <= 30 then

		print("Je krijgt een bronzen medaille!")

	else

		print("Probeer het opnieuw!")

	end

end

```

Het onderstaande voorbeeld controleert alleen de medailleberichten. timePassed  is boven de 30, dus het else-bericht wordt afgedrukt.

Een else -statement moet altijd de laatste  controle zijn in een controle structuur.

2.

Speeltest om het else-bericht te zien.

## [Samenvatting](#samenvatting)[](#samenvatting)

Controle structuren kunnen meer dan één scenario hebben. Gebruik if-statements om de initiële verklaring in te stellen om te controleren, en voeg vervolgens zoveel elseif -voorwaarden toe als nodig is. Gebruik ten slotte else  om aan te geven wat er moet gebeuren als alle gegeven voorwaarden onwaar zijn.

Vanaf de bovenkant worden alle voorwaarden gecontroleerd, en alleen de eerste waarheidsgetrouwe voorwaarde zal de code uitvoeren. De resterende voorwaarden worden niet gecontroleerd, noch zal hun code worden uitgevoerd.

Na het voltooien van het project kun je het script uitbreiden om nieuwe elementen op een paar extra manieren toe te voegen.

-

Voeg code toe zodat spelers de race kunnen herhalen door de startlijn aan te raken wanneer ze gefinisht zijn.

-

Ontwerp een manier om de tijd tijdens een race weer te geven. Je kunt de tijd op een onderdeel weergeven met behulp van een Surface GUI, zoals in de [Maak een Getimede Brug tutorial](/docs/nl-nl/tutorials/fundamentals/coding-4/create-a-timed-bridge) .

Voltooid script

```

local timePassed = 0

local finishLine = script.Parent

-- Gebruikt om finish() en timer te voorkomen van herhalen wanneer de race voorbij is

local raceActive = true

-- Wordt uitgevoerd wanneer de speler de finishlijn aanraakt en toont hen een prijs

local function finish()

	raceActive = false

	print("Je bent gefinisht in " .. timePassed)

	if timePassed <= 10 then

		print("Je krijgt een gouden medaille!")

	elseif timePassed > 10 and timePassed <= 20 then

		print("Je krijgt een zilveren medaille!")

	elseif  timePassed > 20 and timePassed <= 30 then

		print("Je krijgt een bronzen medaille!")

	else

		print("Probeer het opnieuw!")

	end

end

-- Controleert of een speler het onderdeel aanraakt wanneer een race actief is

local function partTouched(otherPart)

	local character = otherPart.Parent

	local humanoid = character:FindFirstChildWhichIsA("Humanoid")

	if humanoid and raceActive == true then

		finish()

	end

end

finishLine.Touched:Connect(partTouched)

-- Houdt de racetijd bij terwijl de race actief is. Moet onderaan het script staan.

while raceActive == true do

	task.wait(1)

	timePassed += 1

	print(timePassed)

end

```

[Volgende](/docs/nl-nl/tutorials/fundamentals/coding-3/give-points)[Vorige](/docs/nl-nl/tutorials/fundamentals/coding-3/powerups-with-if-statements)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
