<!-- Source: https://create.roblox.com/docs/nl-nl/luau/enums -->

Enums | Documentatie - Roblox Creator Hub

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

# Enums

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Enums zijn geen [ingebouwde Luau-typen](https://luau.org/typecheck#builtin-types)  en ze bestaan alleen in Roblox, maar ze zijn conceptueel vergelijkbaar met andere Luau-gegevens typen en zijn iets waar je vaak mee zult werken in Roblox-ontwikkeling.

Het enumeratie  gegevenstype, of [Enum](/docs/nl-nl/reference/engine/datatypes/Enum) , is een vaste lijst van items. Je kunt enums benaderen via het globale object genaamd [Enum](/docs/nl-nl/reference/engine/datatypes/Enum) . Voor een volledige lijst en hun respectieve items, zie [Enums](/docs/nl-nl/reference/engine/enums) .

## [Enum-items](#enum-items)[](#enum-items)

Om alle items van een enum te krijgen, roep je de [GetEnumItems()](/docs/nl-nl/reference/engine/datatypes/Enum#GetEnumItems)  methode aan. Het volgende codevoorbeeld laat zien hoe je [GetEnumItems()](/docs/nl-nl/reference/engine/datatypes/Enum#GetEnumItems)  aanroept op de [Enum.PartType](/docs/nl-nl/reference/engine/enums/PartType)  enum.

```

local partTypes = Enum.PartType:GetEnumItems()

for index, enumItem in partTypes do

	print(enumItem)

end

--[[

	Enum.PartType.Ball

	Enum.PartType.Block

	Enum.PartType.Cylinder

	Enum.PartType.Wedge

	Enum.PartType.CornerWedge

]]

```

## [Gegevenstype](#gegevenstype)[](#gegevenstype)

De [EnumItem](/docs/nl-nl/reference/engine/datatypes/EnumItem)  is het gegevenstype voor items in enums. Een [EnumItem](/docs/nl-nl/reference/engine/datatypes/EnumItem)  heeft drie eigenschappen:

-

Name  — De naam van de [EnumItem](/docs/nl-nl/reference/engine/datatypes/EnumItem) .

-

Value  — De numerieke index van de [EnumItem](/docs/nl-nl/reference/engine/datatypes/EnumItem) .

-

EnumType  — De bovenliggende [Enum](/docs/nl-nl/reference/engine/datatypes/Enum)  van de [EnumItem](/docs/nl-nl/reference/engine/datatypes/EnumItem) .

Sommige eigenschappen van objecten kunnen alleen items van bepaalde enums zijn. Bijvoorbeeld, de [Shape](/docs/nl-nl/reference/engine/classes/Part#Shape)  eigenschap van een [Part](/docs/nl-nl/reference/engine/classes/Part)  object is een item van de [Enum.PartType](/docs/nl-nl/reference/engine/enums/PartType)  enum. Het volgende codevoorbeeld laat zien hoe je de eigenschappen van het [Enum.PartType.Cylinder](/docs/nl-nl/reference/engine/enums/PartType#Cylinder)  enum-item afdrukt.

```

print(Enum.PartType.Cylinder.Name) --> "Cylinder"

print(Enum.PartType.Cylinder.Value) --> 2

print(Enum.PartType.Cylinder.EnumType) --> PartType

```

Om een [EnumItem](/docs/nl-nl/reference/engine/datatypes/EnumItem)  als de waarde van een eigenschap toe te wijzen, gebruik je de volledige [Enum](/docs/nl-nl/reference/engine/datatypes/Enum)  declaratie. Je kunt ook de [Name](/docs/nl-nl/reference/engine/datatypes/EnumItem#Name)  eigenschap van het item als een string gebruiken.

```

local Workspace = game:GetService("Workspace")

local part = Instance.new("Part") -- Maak een nieuw onderdeel

part.Shape = Enum.PartType.Cylinder -- Door volledige enum-item declaratie (beste praktijk)

part.Shape = "Cylinder" -- Door de naam van het enum-item als een string

part.Parent = Workspace

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
