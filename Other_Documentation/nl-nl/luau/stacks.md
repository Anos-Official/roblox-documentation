<!-- Source: https://create.roblox.com/docs/nl-nl/luau/stacks -->

Stacks | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)
6. /
7. [Luau-referentie](/docs/nl-nl/luau)
8. /
9. Gegevensstructuren

# Stacks

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een stack is een lineaire datastructuur met een verzameling items die het Last-In-First-Out (LIFO) principe volgt. De bovenkant van de stack is het item dat het meest recent aan de stack is toegevoegd, en de onderkant van de stack is het item dat het minst recent is toegevoegd.

Je kunt de stack datastructuur zien als een stapel dinerborden: je begint met één bord, en dan leg je er een ander bovenop. Wanneer je borden van de stapel neemt, is het eerste  bord dat je van de stapel haalt het laatste  bord dat je bovenop hebt gelegd.

Stacks hebben twee hoofdoperaties: push  voor het toevoegen van een element aan de bovenkant van de stack en pop  voor het verwijderen van het element van de bovenkant van de stack. Een stack kan een vaste grootte hebben of dynamisch worden aangepast. Stacks zijn nuttig voor ontwerpgebruik zoals backtracking-algoritmen.

## [Implementeer stacks](#implementeer-stacks)[](#implementeer-stacks)

Hoewel Luau geen stacks heeft als een ingebouwde datastructuur, kun je [tabellen](/docs/nl-nl/luau/tables)  gebruiken om stacks te implementeren. Het volgende codevoorbeeld laat zien hoe je een stack kunt maken, een object naar een stack kunt pushen  en een object van de stack kunt poppen . Om deze implementatie voor je game te gebruiken, moet je het opslaan als een [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  en het in [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  opslaan, zodat je stack toegankelijk is voor zowel client als server.

```

local Stack = {}

Stack.__index = Stack

function Stack.new()

	local self = setmetatable({}, Stack)

	self._stack = {}

	return self

end

-- Controleer of de stack leeg is

function Stack:isEmpty()

	return #self._stack == 0

end

-- Plaats een nieuwe waarde op de stack

function Stack:push(value)

	table.insert(self._stack, value)

end

-- Neem een waarde van de stack

function Stack:pop()

	if self:isEmpty() then

		return nil

	end

	return table.remove(self._stack, #self._stack)

end

return Stack

```

Het volgende codevoorbeeld is een gebruiksvoorbeeld als een [Script](/docs/nl-nl/reference/engine/classes/Script)  onder [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) . Je kunt de code, het type en de opslaglocatie aanpassen aan je eigen gebruik, zolang je de vorige implementatiecode correct hebt opgeslagen.

Stack Usage Example

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Stack = require(ReplicatedStorage:WaitForChild("Stack"))

local s = Stack.new()

-- Wijzig de stack 	Resulting stack		 Output

s:push(1)      			-- {1}

s:push(5)      			-- {1, 5}

s:push(10)     			-- {1, 5, 10}

print(s:pop()) 			-- {1, 5}            10

print(s:pop()) 			-- {1}               5

s:push(20)     			-- {1, 20}

print(s:pop()) 			-- {1}               20

print(s:pop()) 			-- {}                1

```

Wanneer je pop()  op een stack uitvoert, zorg ervoor dat de stack niet leeg is.

Als je het vorige codevoorbeeld uitvoert zonder iets te veranderen, is de verwachte output:

Example Output

```

10

5

20

1

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
