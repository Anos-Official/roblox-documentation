<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/fundamentals/coding-4/intro-to-for-loops -->

Introductie tot for loops | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. [Loops](/docs/nl-nl/tutorials/fundamentals/coding-4/landing)

# Introductie tot for loops

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Er zijn verschillende manieren om code herhaaldelijk uit te voeren. Als je wilt dat de code slechts een bepaald aantal keren wordt uitgevoerd, gebruik dan een for loop . Dit artikel behandelt de logica achter for loops en demonstreert enkele praktische voorbeelden, zoals het coderen van een aftelling.

## [Hoe for loops werken](#hoe-for-loops-werken)[](#hoe-for-loops-werken)

For loops gebruiken drie waarden om te bepalen hoe vaak ze worden uitgevoerd: een controle  variabele, een eind  waarde en een incrementeer  waarde. Begonnen vanaf de waarde van de controle variabele, zullen de for loops elke keer dat ze code binnen de loop uitvoeren, omhoog of omlaag tellen totdat ze de eindwaarde overschrijden. Positieve incrementeerwaarden tellen omhoog, en negatieve incrementeerwaarden tellen omlaag.

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-4/forLoop_annotatedExample.png)

Verschillende programmeertalen kunnen andere terminologie gebruiken voor for loops. In C# of JavaScript kan de eindwaarde bijvoorbeeld de voorwaarde worden genoemd.

## [Stappen in een for loop](#stappen-in-een-for-loop)[](#stappen-in-een-for-loop)

Om for loops te begrijpen, is het nuttig om een stroomdiagram te zien dat de logica toont van hoe ze vorderen.

Eerst vergelijkt de for loop de controle variabele met de eindwaarde.

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-4/forLoopDiagram_generic1.png)

Na het uitvoeren van de code wordt de incrementeerwaarde toegevoegd aan de controle variabele. De loop controleert vervolgens de controle variabele en begint opnieuw.

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-4/forLoopDiagram_generic2.png)

Zodra de controle variabele de eindwaarde overschrijdt, stopt de loop. Als een loop bijvoorbeeld een eindwaarde van 10 heeft, stopt de for loop zodra de controle variabele 10 heeft overschreden.

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-4/forLoopDiagram_generic3.png)

## [Code een aftelling](#code-een-aftelling)[](#code-een-aftelling)

Om te zien hoe een for loop werkt, gebruik je deze stappen om een for loop te coderen die begint bij 10 en aftelt naar 0, één nummer tegelijk. Elke keer dat de loop draait, print hij de huidige waarde binnen de controle variabele.

1.

Maak in ServerScriptService  een nieuw script genaamd PracticeLoop. Begin in het script met het typen van het sleutelwoord for .

```

for

```

2.

Maak een controle variabele  genaamd count  en stel een startwaarde in van 10.

```

for count = 10

```

3.

Stel de eindwaarde  in op 0 door , 0  te typen. Zorg ervoor dat je een komma toevoegt om de waarden te scheiden.

```

for count = 10, 0

```

4.

Maak een incrementeerwaarde  van -1 door , -1  te typen. Nadat de loop zijn actie heeft voltooid, voegt hij de incrementeerwaarde toe aan de controle variabele, count. Omdat de incrementeerwaarde negatief is, wordt deze afgetrokken wanneer deze aan de controle variabele wordt toegevoegd.

```

for count = 10, 0, -1

```

Een for loop heeft niet expliciet een incrementeerwaarde nodig. Zonder een incrementeerwaarde zal de loop standaard 1 toevoegen na elke loop.

for count = 10, 0

5.

Om de for loop te voltooien, typ je do en druk je op Enter  om end  toe te voegen. Elke code die tussen do  en end  is getypt, wordt elke keer uitgevoerd wanneer de loop herhaalt.

```

for count = 10, 0, -1 do

end

```

6.

Binnen de loop, print de waarde van de controle variabele, count .

7.

Voer het project uit en kijk naar het Output-venster om de for loop te zien.

Merk op dat de loop de huidige waarde van count elke keer print wanneer hij door een iteratie  gaat. Een iteratie is het volledige proces van het controleren van de controle waarde, het uitvoeren van code en het bijwerken van de incrementeerwaarde. De controle variabele begint bij 10 en telt af naar 0, dus de loop doorloopt 11 iteraties voordat hij stopt.

### [Probleemoplossing tips](#probleemoplossing-tips)[](#probleemoplossing-tips)

Op dit punt, als de loop niet werkt zoals bedoeld, probeer dan een van de volgende opties hieronder.

-

Controleer of je twee komma's  hebt die de getallen in je for loop scheiden. Extra of ontbrekende komma's zorgen ervoor dat de loop niet start.

-

De playground print elk nummer zodra je het uitvoert. In Studio, voeg task.wait(1)  binnen de loop toe om één seconde te pauzeren tussen de nummers.

## [Verschillende voorbeelden van for loops](#verschillende-voorbeelden-van-for-loops)[](#verschillende-voorbeelden-van-for-loops)

Het wijzigen van de drie waarden van een for loop zal de werking van de loop veranderen. Hieronder staan verschillende voorbeelden van for loops met verschillende start-, eind- en incrementeerwaarden. Probeer ze in scripts te plaatsen en kijk wat er gebeurt.

### [Tellen met één omhoog](#tellen-met-één-omhoog)[](#tellen-met-één-omhoog)

### [Tellen met even getallen omhoog](#tellen-met-even-getallen-omhoog)[](#tellen-met-even-getallen-omhoog)

### [Als for loops helemaal niet draaien](#als-for-loops-helemaal-niet-draaien)[](#als-for-loops-helemaal-niet-draaien)

Als de controle variabele begint boven  de eindwaarde, zoals in het onderstaande voorbeeld, zal de for loop helemaal niet draaien.

In dit geval telt de for loop omhoog en controleert of count groter is dan 0. Wanneer de for loop zijn eerste controle uitvoert, ziet hij dat 10 groter is dan 0, en dus stopt hij de loop zonder iets te printen.

## [Samenvatting](#samenvatting)[](#samenvatting)

Een for loop is een veelvoorkomend type loop dat wordt gebruikt wanneer een set instructies een specifiek aantal keren moet worden herhaald. Om een for loop te maken, gebruik je drie variabelen met de onderstaande syntaxis:

In het bovenstaande voorbeeld begint de loop bij 0. Voor elke loop print hij de count variabele, voegt 1 toe aan count, en voltooit uiteindelijk de loop wanneer count gelijk is aan 10.

[Volgende](/docs/nl-nl/tutorials/fundamentals/coding-4/glow-lights-with-for-loops)[Vorige](/docs/nl-nl/tutorials/fundamentals/coding-4/repeat-code-with-while-loops)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
