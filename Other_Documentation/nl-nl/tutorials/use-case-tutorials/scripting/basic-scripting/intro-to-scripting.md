<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/scripting/basic-scripting/intro-to-scripting -->

Inleiding tot scripting | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Scripting
6. /
7. Basisspel

# Inleiding tot scripting

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

In [Inleiding tot Roblox Studio](/docs/nl-nl/tutorials/first-experience)  heb je geleerd hoe je onderdelen kunt maken en manipuleren in Roblox Studio. In deze tutorial leer je hoe je een script  op onderdelen kunt toepassen om een platform te laten verschijnen en verdwijnen. Je kunt dit gebruiken in een platformgame om een kloof te overbruggen, waarbij gebruikers uitgedaagd worden om hun sprongen zorgvuldig te timen om aan de andere kant te komen.

## [Zet de scène](#zet-de-scène)[](#zet-de-scène)

Allereerst heb je een Part  nodig die als platform fungeert. Het maken en verplaatsen van onderdelen zou je bekend moeten zijn van [Inleiding tot Roblox Studio](/docs/nl-nl/tutorials/first-experience) . Je hebt geen ingewikkelde wereld nodig, behalve het platform — je hebt gewoon een kloof nodig die je gebruikers niet gemakkelijk kunnen overbruggen.

1.

Voeg een Part  toe en hernoem deze naar DisappearingPlatform .

2.

Verander de grootte zodat deze groot genoeg is voor een gebruiker om op te springen.

3.

Verplaats het naar een geschikte locatie zodat je het kunt bereiken en erop kunt springen tijdens het testen van je game.

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/intro-to-scripting/partInPlace.jpg)

4.

Stel de Anchored  eigenschap in op true  in het Properties  venster.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/intro-to-scripting/anchoredProperty.png)

Vergeet niet dat het instellen van de Anchored-eigenschap van een onderdeel op true  ervoor zorgt dat het op zijn plaats blijft, ongeacht wat er gebeurt. Je platform valt naar beneden als het niet is verankerd.

## [Voeg een script toe](#voeg-een-script-toe)[](#voeg-een-script-toe)

Code in Roblox is geschreven in een taal genaamd [Luau](/docs/nl-nl/luau)  die je in scripts binnen verschillende containers in de Explorer  kunt plaatsen. Als je een script onder een Part  plaatst, zal Roblox de code van het script uitvoeren wanneer het onderdeel in het spel wordt geladen.

1.

Beweeg de muis over het DisappearingPlatform  onderdeel in het Explorer  venster en klik op de +  knop om een nieuw script in het platform in te voegen. Hernoem je nieuwe script naar Disappear .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/intro-to-scripting/scriptInPlace.jpg)

2.

Verwijder de standaardcode binnenin.

Vergeet niet om onderdelen en scripts direct na het maken ervan te hernoemen  zodat je het overzicht niet verliest in de Explorer .

## [Eerste variabele](#eerste-variabele)[](#eerste-variabele)

Het is een goed idee om je script te beginnen met het maken van een variabele  voor het platform. Een variabele is een naam  die is gekoppeld aan een waarde . Zodra een variabele is gemaakt, kan deze keer op keer worden gebruikt. Je kunt de waarde indien nodig wijzigen.

In Luau wordt een variabele als volgt gemaakt: local variableName = variableValue .

De term local  betekent dat de variabele alleen zal worden gebruikt in het blok van het script waar het is gedeclareerd. Het =  teken wordt gebruikt om de waarde van de variabele in te stellen. Namen voor variabelen worden meestal geschreven in camel case . Dit is kleine letters met elk woord na het eerste met een hoofdletter, justLikeThis .

Kopieer de volgende code om een variabele  voor het platform te maken genaamd platform , waarbij de waarde script.Parent  is.

```

local platform = script.Parent

```

script.Parent  wordt gebruikt om het object te vinden waarin het script zich bevindt. Zoals je misschien al had geraden, verwijst script  naar het script waarin je schrijft en de Parent  van het script is waar het zich bevindt.

## [Verdwijning functie](#verdwijning-functie)[](#verdwijning-functie)

Tijd om het platform te laten verdwijnen. Het is altijd het beste om code voor het bereiken van een specifieke actie te groeperen in een functie . Een functie is een benoemd blok code dat je helpt je code te organiseren en het op meerdere plaatsen te gebruiken zonder het opnieuw te schrijven. Maak een functie  in het script en noem deze disappear .

```

local platform = script.Parent

local function disappear()

end

```

De eerste nieuwe regel declareert  de functie — het geeft het begin van de functie aan en noemt deze disappear . De code voor een functie gaat tussen de eerste regel en end .

De haakjes zijn voor het opnemen van aanvullende informatie indien nodig. Je leert meer over het doorgeven van informatie aan functies in een latere cursus.

## [Onderdeel eigenschappen](#onderdeel-eigenschappen)[](#onderdeel-eigenschappen)

Wanneer het platform verdwijnt, moet het onzichtbaar zijn en moeten gebruikers erdoorheen vallen — maar je kunt het platform niet gewoon vernietigen, omdat het later weer moet verschijnen.

Onderdelen hebben verschillende eigenschappen  die hier kunnen worden gebruikt. Vergeet niet dat je de eigenschappen van een onderdeel kunt zien als je het selecteert en naar het Properties  venster kijkt.

Een onderdeel kan onzichtbaar worden gemaakt door de [Transparency](/docs/nl-nl/reference/engine/classes/BasePart#Transparency)  eigenschap te wijzigen. Transparantie kan een waarde zijn tussen 0 en 1, waarbij 1 volledig transparant en dus onzichtbaar is.

De Transparantie-eigenschap van de kubus wijzigen

De CanCollide  eigenschap bepaalt of andere onderdelen (en gebruikers) door het onderdeel heen kunnen gaan. Als je het op false  instelt, zullen gebruikers door het platform vallen.

De CanCollide-eigenschap van de kubus wijzigen

Net als script.Parent , worden eigenschappen benaderd met behulp van een punt . Waarden worden toegewezen met een gelijkteken.

1.

In de disappear  functie, stel de CanCollide  eigenschap van het platform in op false .

2.

Op de volgende regel, stel de Transparency  eigenschap in op 1 .

```

local platform = script.Parent

local function disappear()

    platform.CanCollide = false

    platform.Transparency = 1

end

```

Je zult merken dat Studio automatisch je code inspringt  binnen een functie. Zorg er altijd voor dat je je code op deze manier inspringt — het helpt aan te geven waar de functie begint en eindigt, wat je code leesbaarder maakt.

## [Roep de functie aan](#roep-de-functie-aan)[](#roep-de-functie-aan)

Zodra je een functie hebt gedeclareerd, kun je deze uitvoeren door de naam ervan met haakjes ernaast te schrijven. Bijvoorbeeld, disappear()  zal de disappear  functie uitvoeren. Dit staat bekend als het aanroepen  van een functie.

1.

Roep  de disappear  functie aan aan het einde van het script.

```

local platform = script.Parent

local function disappear()

    platform.CanCollide = false

    platform.Transparency = 1

end

disappear()

```

2.

[Start een playtest](/docs/nl-nl/studio/testing-modes#spelen-testen) . Als je code werkt, zou het platform verdwenen moeten zijn tegen de tijd dat de gebruiker in het spel verschijnt.

## [Verschijn functie](#verschijn-functie)[](#verschijn-functie)

Je kunt het platform gemakkelijk weer laten verschijnen door een functie te schrijven die het tegenovergestelde doet van de disappear  functie.

1.

Verwijder de disappear()  regel uit het script.

2.

Declareer een nieuwe functie genaamd appear .

3.

In de functie-inhoud, stel de CanCollide  eigenschap in op true  en de Transparency  eigenschap in op 0 .

```

local platform = script.Parent

local function disappear()

    platform.CanCollide = false

    platform.Transparency = 1

end

local function appear()

    platform.CanCollide = true

    platform.Transparency = 0

end

```

## [Loop code](#loop-code)[](#loop-code)

Het platform moet constant verdwijnen en weer verschijnen, met een paar seconden tussen elke verandering. Het is onmogelijk om een oneindig aantal functieaanroepen te schrijven — gelukkig, met een while loop , hoef je dat niet te doen.

Een while loop voert de code erin uit zolang de verklaring  na while  waar blijft. Deze specifieke loop moet voor altijd draaien, dus de verklaring moet gewoon true  zijn. Maak een while true  loop aan het einde van je script.

```

local platform = script.Parent

local function disappear()

    platform.CanCollide = false

    platform.Transparency = 1

end

local function appear()

    platform.CanCollide = true

    platform.Transparency = 0

end

while true do

end

```

## [Wissel het platform](#wissel-het-platform)[](#wissel-het-platform)

In de while loop moet je code schrijven om een paar seconden te wachten tussen het verdwijnen en weer verschijnen van het platform.

De ingebouwde functie [task.wait()](/docs/nl-nl/reference/engine/libraries/task#wait)  kan hiervoor worden gebruikt. In de haakjes is het aantal seconden dat je moet wachten nodig: bijvoorbeeld task.wait(3) .

Wat je ook doet, maak nooit een while true  loop zonder een task.wait()  op te nemen — en test je code niet voordat je er een in hebt gezet! Als je niet wacht, zal je game bevriezen  omdat Studio nooit de kans krijgt om de loop te verlaten en iets anders te doen.

Drie seconden is een redelijke starttijd voor de lengte van de tijd tussen elke platformstatus.

1.

In de while loop, roep de task.wait()  functie aan met 3  in de haakjes.

2.

Roep de disappear  functie aan.

3.

Roep de task.wait()  functie opnieuw aan met 3  in de haakjes.

4.

Roep de appear  functie aan.

```

while true do

   task.wait(3)

   disappear()

   task.wait(3)

   appear()

end

```

De code voor het platform is nu compleet! Test je code nu en je zou moeten ontdekken dat het platform na drie seconden verdwijnt en drie seconden later weer verschijnt in een lus.

Je zou dit platform kunnen dupliceren om een bredere kloof te overbruggen, maar je moet de wachttijden in elk script wijzigen. Anders zullen de platforms allemaal tegelijkertijd verdwijnen en zullen gebruikers nooit kunnen oversteken.

## [Eindcode](#eindcode)[](#eindcode)

```

local platform = script.Parent

local function disappear()

    platform.CanCollide = false

    platform.Transparency = 1

end

local function appear()

    platform.CanCollide = true

    platform.Transparency = 0

end

while true do

   task.wait(3)

   disappear()

   task.wait(3)

   appear()

end

```

[Volgende](/docs/nl-nl/tutorials/use-case-tutorials/scripting/basic-scripting/deadly-lava)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
