<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/fundamentals/coding-4/repeat-code-with-while-loops -->

Herhaal code met while-lussen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. [Loops](/docs/nl-nl/tutorials/fundamentals/coding-4/landing)

# Herhaal code met while-lussen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Veel dingen in computerwetenschappen of game-ontwikkeling herhalen zich vaak. Bijvoorbeeld, een app kan inhoud in een feed elke paar seconden bijwerken, of een spel kan spelers elke dag dat ze ingelogd zijn een prijs geven. Om dit gedrag te bereiken, gebruiken programmeurs vaak lussen .

In de computerwetenschappen is een lus  een codepatroon dat een set instructies herhaalt, vaak totdat aan een specifieke voorwaarde is voldaan. Om dit te oefenen, ga je een onderdeel coderen dat kleuren oneindig verandert. Latere lessen zullen laten zien hoe je de lus kunt stoppen.

## [Stel het onderdeel en script in](#stel-het-onderdeel-en-script-in)[](#stel-het-onderdeel-en-script-in)

Gebruik een willekeurig Roblox-project voor deze oefening. Wanneer je klaar bent, kan dit onderdeel worden gebruikt als een manier om een omgeving te versieren.

1.

Maak een nieuw onderdeel met een beschrijvende naam. Deze les gebruikt LoopingPart .

2.

Voeg in ServerScriptService  een nieuw script toe met de naam LoopingScript.

3.

Verwijder in het script Hello World  en schrijf een opmerking  die het doel van dit script aangeeft.

```

-- Verandert de kleur van LoopingPart elke paar seconden

```

## [Gebruik variabelen om een onderdeel op te slaan](#gebruik-variabelen-om-een-onderdeel-op-te-slaan)[](#gebruik-variabelen-om-een-onderdeel-op-te-slaan)

Variabelen kunnen ook verwijzingen naar objecten bevatten naast strings. Bijvoorbeeld, wanneer een script de verwijzing naar een onderdeel kent, kan het script dit veranderen.

In plaats van workspace.NameOfYourPart  keer op keer te typen, kan die hele regel in een lokale variabele worden opgeslagen. Lokale variabelen worden gemaakt door local  te typen en vervolgens de naam van de variabele.

Bijvoorbeeld: local nameOfVariable .

Een lokale variabele werkt alleen in het script waar het is gemaakt. Als een lokale variabele genaamd part1  is gemaakt in Script1, kan deze niet worden gebruikt in Script2. De meeste variabelen die je gebruikt, zullen lokale variabelen zijn.

1.

Maak onder de opmerking een lokale variabele door local loopingPart  te typen.

```

-- Verandert de kleur van LoopingPart elke paar seconden

local loopingPart

```

2.

Stel de variabele in op het lusonderdeel door = workspace.LoopingPart  op dezelfde regel te typen. Vergeet niet dat de =  operator de waarde van een variabele instelt op wat er aan de rechterkant van staat.

```

-- Verandert de kleur van LoopingPart elke paar seconden

local loopingPart = workspace.LoopingPart

```

Vergeet niet dat de =  operator de waarde van een variabele instelt op wat er aan de rechterkant van staat.

## [While-lussen](#while-lussen)[](#while-lussen)

Voordat je de while-lus voor het kleurveranderende onderdeel maakt, is het de moeite waard om de syntaxis ervan uit te leggen. Een while-lus heeft drie componenten:

-

Het while  sleutelwoord.

-

Een voorwaarde, altijd na het sleutelwoord.

-

Instructies, tussen de do  en end  sleutelwoorden.

In lussen kunnen voorwaarden een verscheidenheid aan logische uitspraken zijn. Enkele voorbeelden kunnen zijn of twee getallen hetzelfde zijn. Een lus zal draaien als de voorwaarde waar is.

Een voorwaarde van true  maakt dat een lus voor altijd draait. Het onderstaande voorbeeld telt hoe vaak het is uitgevoerd en stopt na drie. In latere lessen ga je voorwaarden coderen die stoppen wanneer er iets in de ervaring verandert.

## [Code een while-lus](#code-een-while-lus)[](#code-een-while-lus)

Vervolgens ga je de while-lus voor het kleurveranderende onderdeel instellen.

1.

Typ op de volgende regel while true do . Druk vervolgens op Enter  om automatisch aan te vullen en het woord end  toe te voegen.

```

-- Verandert de kleur van loopingPart elke paar seconden

local loopingPart = workspace.LoopingPart

-- Looping Code

while true do

end

```

Je hebt misschien opgemerkt dat de editor automatisch end  aan het script heeft toegevoegd en de volgende regel code heeft ingesprongen. Indentatie maakt code gemakkelijker te lezen. Instructies in een lus moeten altijd  ingesprongen zijn.

### [Voeg code toe in de lus](#voeg-code-toe-in-de-lus)[](#voeg-code-toe-in-de-lus)

Met de while-lus gemaakt, kunnen instructies worden toegevoegd om de kleur van het onderdeel in de loop van de tijd te veranderen. Voeg binnen de lus een regel code toe voor elke kleur. Elke kleur gebruikt RGB-waarden, een manier om kleuren als getallen op te slaan in de computerwetenschappen.

1.

Stel tussen while true do  en end  de Color-eigenschap van het onderdeel in op [Color3.fromRGB()](/docs/nl-nl/reference/engine/datatypes/Color3#fromRGB) .

```

local loopingPart = workspace.LoopingPart

while true do

	loopingPart.Color = Color3.fromRGB()

end

```

2.

De kleur kan worden ingesteld met een kleurenkiezer in Studio. Om dit te doen, klik je met de linkermuisknop in de ()  naast fromRGB . Klik vervolgens op het kleurwielpictogram. Zodra je een gewenste kleur hebt, druk je op OK om de kleurwaarde automatisch aan de code toe te voegen.

```

local loopingPart = workspace.LoopingPart

while true do

	loopingPart.Color = Color3.fromRGB(82, 227, 255)

end

```

Indien gewenst, kan een kleur handmatig worden gemaakt door een waarde toe te wijzen in elk getal van 0 tot 255.

### [Laat het script wachten](#laat-het-script-wachten)[](#laat-het-script-wachten)

Als je nu een tweede regel van kleurveranderende code toevoegt, zou het de kleur van de baksteen zo snel veranderen dat je de eerste kleur misschien niet eens ziet. Om het script te laten wachten voordat de volgende regel code wordt uitgevoerd, gebruik je een [task.wait()](/docs/nl-nl/reference/engine/libraries/task#wait)  functie.

1.

Typ op de regel na het veranderen van de baksteenkleur task.wait(3) . Het getal dat in de ()  staat, is het aantal seconden dat het script zal wachten.

```

local loopingPart = workspace.LoopingPart

while true do

	loopingPart.Color = Color3.fromRGB(82, 227, 255)

	task.wait(3)

end

```

2.

Onder de wachtfunctie herhaal je hetzelfde proces van het toevoegen van een nieuwe kleur. Eindig het met een extra wachtfunctie.

```

while true do

	loopingPart.Color = Color3.fromRGB(82, 227, 255)

	task.wait(3)

	loopingPart.Color = Color3.fromRGB(177, 52, 255)

	task.wait(3)

end

```

Terwijl je meer code in de lus toevoegt, zorg ervoor dat alles in scope  is, wat betekent dat de code op de juiste plaats staat. Om ervoor te zorgen dat de code in de lus draait, moet deze tussen while true do  en vóór end  staan.

3.

Test de code en kijk of de kleuren veranderen.

Probleemoplossingsnotities
 Op dit punt, als het kleurveranderende onderdeel niet werkt zoals bedoeld, probeer dan een van de volgende opties hieronder.

Probleem : Kleuren worden overgeslagen

-

Zorg ervoor dat je een wachtfunctie hebt tussen elke kleurverandering, vooral op de laatste regel.

-

Controleer of alle kleurveranderings- en wachtcode tussen de while true do  en end  secties staat.

Probleem : Onderdeel is nog steeds grijs of verandert niet zoals bedoeld

-

Zorg ervoor dat alle RGB-waarden getallen van 0 tot 255 zijn, hele of decimale getallen zijn, en gescheiden zijn door komma's.

-

De getallen binnen de ()  van een wachtfunctie moeten groter zijn dan 1. Het is mogelijk dat als een wacht te kort is, je die kleur misschien niet ziet.

## [Voltooi het script voor kleurverandering](#voltooi-het-script-voor-kleurverandering)[](#voltooi-het-script-voor-kleurverandering)

```

-- Maak een variabele om het onderdeel op te slaan

local loopingPart = workspace.LoopingPart

-- Looping Code

while true do

	-- Verandert de kleur van loopingPart

	loopingPart.Color = Color3.fromRGB(82, 227, 255)

	-- Wacht 3 seconden voor de volgende instructie

	task.wait(3)

	loopingPart.Color = Color3.fromRGB(177, 52, 255)

	task.wait(3)

end

```

## [Samenvatting](#samenvatting)[](#samenvatting)

Lussen zijn een veelvoorkomend element in de meeste programmeertalen. Ze worden gebruikt om instructies te herhalen, soms totdat aan specifieke voorwaarden is voldaan. In dit artikel wordt de while-lus gebruikt om instructies voor altijd te herhalen. Om een while-lus te maken die voor altijd herhaalt, gebruik je de onderstaande syntaxis, zorg ervoor dat je instructies tussen de do  en end  sleutelwoorden opneemt.

```

while true do

	-- Instructies

end

```

[Volgende](/docs/nl-nl/tutorials/fundamentals/coding-4/intro-to-for-loops)[Vorige](/docs/nl-nl/tutorials/fundamentals/coding-4/landing)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
