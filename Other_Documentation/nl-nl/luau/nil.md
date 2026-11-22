<!-- Source: https://create.roblox.com/docs/nl-nl/luau/nil -->

Nil | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)
6. /
7. [Luau-referentie](/docs/nl-nl/luau)
8. /
9. Typen

# Nil

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

In Luau vertegenwoordigt nil  niet-bestaande of nietsheid. Het is anders dan elke andere waarde of gegevenstype. Je kunt het gebruiken om een variabele te vernietigen of een waarde in een tabel te verwijderen. Het is de enige waarde naast false  die niet evalueert naar [true](/docs/nl-nl/luau/booleans) .

Luau heeft een garbage collector  die gegevens verwijdert die niet langer toegankelijk zijn voor een script. Voor de beste prestaties, definieer grote variabelen opnieuw als nil  in langlopende scripts wanneer je ze niet meer nodig hebt, zodat de garbage collector ze kan verwijderen.

```

local variableToDelete = 5

print(variableToDelete) -- 5

variableToDelete = nil

print(variableToDelete) -- nil

local dictionaryTable = {

    Monday = 1,

    Tuesday = 2,

    Wednesday = 3

}

-- Geef de waarde van de 'Tuesday' sleutel weer

print(dictionaryTable.Tuesday) -- 2

-- Wis de 'Tuesday' sleutel

dictionaryTable.Tuesday = nil

-- Geef de waarde van de sleutel opnieuw weer

print(dictionaryTable.Tuesday) -- nil

```

Je kunt nil  gebruiken om enkele eigenschappen van objecten te wissen. Bijvoorbeeld, je kunt de Parent  van een object op nil  zetten om het object effectief uit het spel te verwijderen. Om het object terug te brengen naar het spel nadat je het hebt verwijderd, wijs je de Parent  opnieuw toe. Het volgende voorbeeld laat zien hoe je nil  kunt gebruiken om een [Part](/docs/nl-nl/reference/engine/classes/Part)  te verwijderen:

```

local Workspace = game:GetService("Workspace")

-- Maak een nieuwe steen

local part = Instance.new("Part")

-- Voeg de nieuwe part toe aan de workspace, zodat deze zichtbaar is

part.Parent = Workspace

task.wait(1)

-- Verwijder de part uit het zicht maar niet uit het geheugen

part.Parent = nil

task.wait(1)

-- De part bestaat nog steeds omdat deze wordt verwezen door de variabele "part", dus kan deze weer zichtbaar worden gemaakt

part.Parent = Workspace

task.wait(1)

-- Verwijder de part opnieuw uit het zicht

part.Parent = nil

-- Wis de referentie naar de part zodat deze door de garbage collector kan worden opgepakt

part = nil

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
