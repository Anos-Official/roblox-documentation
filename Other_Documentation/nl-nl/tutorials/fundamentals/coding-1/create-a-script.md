<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/fundamentals/coding-1/create-a-script -->

Maak een script | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. [Variabelen en objecten](/docs/nl-nl/tutorials/fundamentals/coding-1/landing)

# Maak een script

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Coderen  is het proces van het creëren van instructies voor computers om te volgen. Net zoals mensen verschillende talen gebruiken, zoals Engels en Spaans, doen programma's dat ook. Roblox gebruikt de programmeertaal Luau .

Dit artikel behandelt hoe je kunt beginnen met coderen in Roblox, en introduceert veelvoorkomende concepten zoals scripts, datatypes en variabelen. Aan het einde kun je code typen die berichten weergeeft in Roblox Studio.

## [Code met scripts](#code-met-scripts)[](#code-met-scripts)

In Roblox Studio worden regels Luau-code vastgehouden in scripts . Deze scripts geven het spel sets instructies over hoe spelers gezondheidspunten te geven, een regen van vuurballen te creëren, of iets anders dat je maar kunt bedenken.

### [Maak een script](#maak-een-script)[](#maak-een-script)

Scripts worden meestal gemaakt in ServerScriptService , een speciale map die alleen bedoeld is voor het opslaan van scripts.

1.

In Explorer, beweeg de muis over ServerScriptService  om de +  knop te zien.

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-1/hover-over-serverscriptservice_400x400.png)

2.

Klik op de +  knop en selecteer Script . Een nieuw script wordt aangemaakt en de scripteditor opent.

3.

Klik met de rechtermuisknop op Script en selecteer Hernoemen . Noem het script * PracticeScript* . Scripts een naam geven helpt jou en eventuele teamgenoten te onthouden wat elk script doet.

### [Hallo wereld](#hallo-wereld)[](#hallo-wereld)

Nieuwe scripts bevatten een printfunctie bovenaan de scripteditor. Printfuncties  tonen tekst op het scherm. Het is een van de eerste functies die veel mensen leren, en je zult het vaak gebruiken. Deze code zorgt ervoor dat "Hallo wereld!" op het scherm verschijnt.

Om het script de volgende keer dat je Roblox Studio opent te vinden, klik je op de naam van het script boven de 3D-weergave, of dubbelklik je op de naam van het script in Explorer.

### [Test uitvoer](#test-uitvoer)[](#test-uitvoer)

Je kunt het resultaat van het uitvoeren van de standaardcode zien met het Output  venster. Als je het nog nooit eerder hebt gebruikt, moet je het inschakelen.

1.

Open vanuit het venster menu van Studio het [Output](/docs/nl-nl/studio/output)  venster.

2.

Om het script te testen, [start een playtest](/docs/nl-nl/studio/testing-modes#spelen-testen) . Hallo wereld!  verschijnt in de uitvoer.

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-1/helloworld-output_800x150.png)

3.

Klik op Stop  om de playtest te beëindigen. Je kunt nu terugkeren naar het Script  tabblad.

## [Identificeer datatypes](#identificeer-datatypes)[](#identificeer-datatypes)

Programmeertalen classificeren verschillende soorten waarden in datatypes . Een datatype is bijvoorbeeld een getal . Getal datatypes zijn vanzelfsprekend omdat ze alleen uit cijfers bestaan.

Een ander datatype is een string . Strings kunnen cijfers, letters en tekens bevatten. Kijk nog eens naar de standaardcode in het nieuwe script; de woorden en aanhalingstekens binnen de haakjes zijn een voorbeeld van een string  datatype.

Strings zoals "Hallo Wereld"  staan altijd binnen aanhalingstekens, "zoals dit" . Meer voorbeelden van strings zijn hieronder. Let op hoe ze een mix van letters en cijfers bevatten.

-

"Je bent net bij het spel gekomen!"

-

"Er zijn nog 50 spelers over"

-

"10"

## [Maak variabelen](#maak-variabelen)[](#maak-variabelen)

Variabelen  zijn containers voor informatie die het programma kan gebruiken en wijzigen, zoals spelersnamen of punten.

Declareren  van een variabele is wat programmeurs het proces noemen van het creëren van een nieuwe variabele. In Luau, om een nieuwe variabele te declareren, typ je local , en vervolgens de naam voor de nieuwe variabele. Een variabele die een spelersnaam kan bevatten, zou er als volgt uitzien: local playerName

Wanneer je nieuwe variabelen declareert, vereisen sommige programmeertalen dat je ook aangeeft welk datatype de variabele kan gebruiken. Bijvoorbeeld, een variabele in Java zou zijn String name = "Pavel" . Luau vereist alleen een naam.

In Luau kunnen variabelen globaal of lokaal zijn. Je zult meestal lokale  variabelen gebruiken. Lokale variabelen kunnen alleen binnen het script of de codechunk waar ze zijn gemaakt worden gebruikt. Globale variabelen kunnen potentieel door andere scripts worden gebruikt, maar te veel globale variabelen kunnen je spel traag en onresponsief maken. Het is beter om de gewoonte te hebben om variabelen lokaal te maken, tenzij dat nodig is.

### [Gebruik variabelen en strings samen](#gebruik-variabelen-en-strings-samen)[](#gebruik-variabelen-en-strings-samen)

Tijd om je eigen variabelen te declareren. Deze stappen gebruiken een string om de naam van je favoriete dier op te slaan.

1.

Verwijder print("Hallo wereld!") . Het is een goede gewoonte om onnodige code niet in je scripts te laten staan.

2.

Declareer een nieuwe variabele door eerst local  te typen, en vervolgens de variabele myAnimal  te noemen.

Declareert een nieuwe variabele

```

local myAnimal

```

Variabelen kunnen geen spaties bevatten. Wees voorzichtig om geen spaties op te nemen, anders werkt de code niet zoals bedoeld.

### [Noem variabelen](#noem-variabelen)[](#noem-variabelen)

Variabelen kunnen van alles worden genoemd, maar goede namen beschrijven altijd hun doel. Generieke namen maken je code moeilijk te lezen en later bij te werken. Programmeurs gebruiken ook verschillende hoofdlettergebruik stijlen om zichzelf te herinneren hoe de variabele binnen het script wordt gebruikt. Een goede standaardstijl is camelCase .

Om in camelCase te schrijven:

-

Begin met een kleine letter

-

Laat spaties weg

-

Hoofdletter de extra woorden

Goede Variabele Namen

-

playerPoints

-

numberStorageArray

Slechte Variabele Namen

-

myVariable  - Beschrijft niet het doel van de variabele

-

player name  - De opgenomen spatie zal problemen veroorzaken

### [Wijs waarden toe aan variabelen](#wijs-waarden-toe-aan-variabelen)[](#wijs-waarden-toe-aan-variabelen)

Nieuwe variabelen zijn leeg. Om het een waarde te wijzen , of iets in de container te plaatsen, gebruik je het =  symbool. In dit geval wijs je de variabele de naam van je favoriete dier toe.

1.

Typ na de variabelenaam = .

Gelijk wijst waarden toe

```

local myAnimal =

```

2.

Typ op dezelfde regel een string die je favoriete dier bevat. Vergeet de aanhalingstekens niet.

Wijst "Stekelvarkens" toe aan myAnimal

```

local myAnimal = "Stekelvarkens"

```

### [Gebruik print() voor je eigen berichten](#gebruik-print-voor-je-eigen-berichten)[](#gebruik-print-voor-je-eigen-berichten)

Printfuncties tonen tekst op het scherm, zoals je eerder zag. Het is een van de eerste functies die veel mensen leren, omdat het een eenvoudige manier is om het script een opdracht te geven. Om je variabele te zien, gebruik je de [print()](/docs/nl-nl/reference/engine/globals/LuaGlobals#print)  functie.

1.

Typ op een nieuwe regel print() .

Voegt lege print() toe

```

local myAnimal = "Stekelvarkens"

print()

```

2.

Typ de naam van je variabele binnen de haakjes.

Als je een rode fout in de uitvoereditor ziet, betekent dit dat er een fout in de code zit. Elke fout heeft een unieke manier om zichzelf te beschrijven. Probeer de informatie van de fout te gebruiken om je code te corrigeren.

3.

Test je code met de afspeelknop. Je zou de naam van je dier in het Output venster moeten zien.

### [Combineer strings](#combineer-strings)[](#combineer-strings)

Je kunt elke string in de uitvoer weergeven met print() ; je kunt zelfs meerdere strings afdrukken die zijn opgeslagen in variabelen of direct binnen de functie zijn getypt. Concatenatie  is het combineren van strings. Om de string die aan je variabele is toegewezen en een tweede string te concatenateren, gebruik je twee punten .. . Het volgende voorbeeld concateneert twee variabelen en twee getypte strings.

Speel met het afdrukken van verschillende combinaties van strings.

## [Samenvatting](#samenvatting)[](#samenvatting)

Nieuwe scripts kunnen worden gemaakt door op de + knop naast de naam van een object te klikken. ServerScriptService is een veelvoorkomende plaats om nieuwe scripts te maken. Nieuwe scripts bevatten de standaardcode print("Hallo wereld!") . Deze code toont Hallo wereld!  in het Output venster, waar je de resultaten van je code kunt zien en of er fouten zijn opgetreden.

"Hallo wereld!" is een voorbeeld van een string datatype. Strings kunnen elke combinatie van tekens bevatten die je op je toetsenbord kunt typen. Concatenatie is wanneer meerdere strings worden gecombineerd.

Variabelen zijn containers die kunnen worden toegewezen om verschillende datatypes vast te houden, zoals strings en getallen.

[Volgende](/docs/nl-nl/tutorials/fundamentals/coding-1/object-properties)[Vorige](/docs/nl-nl/tutorials/fundamentals/coding-1/landing)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
