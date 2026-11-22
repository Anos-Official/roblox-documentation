<!-- Source: https://create.roblox.com/docs/nl-nl/luau/type-coercion -->

Type coercion | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)
6. /
7. [Luau-referentie](/docs/nl-nl/luau)
8. /
9. Functies

# Type coercion

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Als Luau probeert een waarde of [variabele](/docs/nl-nl/luau/variables)  te gebruiken in een bewerking, zoals [wiskunde](#wiskunde) , [concatenatie](#concatenatie)  of [toewijzing](#toewijzing) , maar de waarde niet het type is dat de bewerking verwacht, dan converteert ( coerceert  ) Luau de waarde om het datatype te veranderen. Coercion gebeurt tijdens de uitvoering van die bewerking en verandert de waarde van een variabele niet.

## [Wiskunde](#wiskunde)[](#wiskunde)

Luau coerces strings naar nummers in [wiskundige bewerkingen](/docs/nl-nl/luau/operators#aritmetisch) . Dit gedrag is ingebouwd in Luau. Als de types niet compatibel zijn voor wiskunde, gooit Luau een fout en voert het de rest van het script niet uit. Bijvoorbeeld, je kunt geen string bij een nummer optellen als de string geen nummer vertegenwoordigt.

```

print(100 + "7") -- 107

print(100 - "7") -- 93

print("1000" + 234) -- 1234

print("1000" - 234) -- 766

print("hello" + 234) -- fout: poging om wiskunde (optellen) uit te voeren met string en nummer

```

## [Concatenatie](#concatenatie)[](#concatenatie)

Bij concatenatie coerces Luau nummers naar strings. Om een nummer naar een string te converteren zonder coercion, gebruik de [string.format()](/docs/nl-nl/reference/engine/libraries/string#format)  functie.

```

print("Pi is " .. math.pi) --> Pi is 3.1415926535898

print("Pi is " .. 3.1415927) --> Pi is 3.1415927

-- Rondt af op drie decimalen

print("Pi is " .. string.format("%.3f", 3.1415927)) -- Pi is 3.142

```

## [Toewijzing](#toewijzing)[](#toewijzing)

Sommige eigenschappen verwachten bepaalde datatypes, zoals een [Enum](#enums)  of string, maar je kunt een waarde van een ander type aan deze eigenschappen toewijzen en Luau converteert de waarde naar het type dat de eigenschap verwacht.

### [Enums](#enums)[](#enums)

Luau coerces nummers en strings van enumwaarden naar de volledige enumnaam. Bijvoorbeeld, je kunt de waarde van de [Part.Material](/docs/nl-nl/reference/engine/classes/Part#Material)  eigenschap benoemen met een nummer, string of volledige enumnaam, en de print()  functie print altijd de volledige enumnaam. Het is een best practice om expliciet te zijn en de volledige enumnaam te gebruiken. Voor meer informatie over Enums, zie [Enums](/docs/nl-nl/luau/enums) .

```

local Workspace = game:GetService("Workspace")

local part1 = Instance.new("Part")

part1.Material = 816

part1.Parent = Workspace

print(part1.Material) -- Enum.Material.Concrete

local part2 = Instance.new("Part")

part2.Material = "Concrete"

part2.Parent = Workspace

print(part2.Material) -- Enum.Material.Concrete

-- Dit is een best practice omdat het het meest expliciet is

local part3 = Instance.new("Part")

part3.Material = Enum.Material.Concrete

part3.Parent = Workspace

print(part3.Material) -- Enum.Material.Concrete

```

### [Tijd van de dag](#tijd-van-de-dag)[](#tijd-van-de-dag)

De [Lighting.TimeOfDay](/docs/nl-nl/reference/engine/classes/Lighting#TimeOfDay)  eigenschap, die definieert of het nacht, dag of een andere tijd is, is een stringrepresentatie van het [DateTime](/docs/nl-nl/reference/engine/datatypes/DateTime)  datatype. Als je een nummer toewijst aan [Lighting.TimeOfDay](/docs/nl-nl/reference/engine/classes/Lighting#TimeOfDay) , converteert Luau het naar de stringrepresentatie van [DateTime](/docs/nl-nl/reference/engine/datatypes/DateTime) .

```

local Lighting = game:GetService("Lighting")

Lighting.TimeOfDay = "05:00:00"

print(Lighting.TimeOfDay) -- 05:00:00

Lighting.TimeOfDay = 5

print(Lighting.TimeOfDay) -- 05:00:00

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
