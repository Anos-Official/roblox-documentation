<!-- Source: https://create.roblox.com/docs/nl-nl/luau/luau-csharp-comparison -->

Luau en C# vergelijking | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Meer informatie](/docs/nl-nl/learn)

# Luau en C# vergelijking

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Roblox gebruikt de Luau programmeertaal. De volgende codevoorbeelden en tabellen geven enkele van de verschillen tussen de syntaxis voor C# en Luau aan.

## [Regels voor het einde van een regel](#regels-voor-het-einde-van-een-regel)[](#regels-voor-het-einde-van-een-regel)

Je hebt geen puntkomma's nodig in Luau, maar ze breken de syntaxis niet.

## [Gereserveerde sleutelwoorden](#gereserveerde-sleutelwoorden)[](#gereserveerde-sleutelwoorden)

De volgende tabel heeft de gereserveerde sleutelwoorden van Luau gekoppeld aan hun C# equivalent. Let op dat niet alle C# sleutelwoorden worden weergegeven.

| Luau | | C# |
| --- | --- |
| and | |  |
| break | | break |
| do | | do |
| if | | if |
| else | | else |
| elseif | | else if |
| then | |  |
| end | |  |
| true | | true |
| false | | false |
| for | | for  of foreach |
| function | |  |
| in | | in |
| local | |  |
| nil | | null |
| not | |  |
| or | |  |
| repeat | |  |
| return | | return |
| until | |  |
| while | | while |

## [Opmerkingen](#opmerkingen)[](#opmerkingen)

Opmerkingen in Luau

```

-- Enkele regel opmerking

--[[ Resultaat:

	Blockopmerking

--]]

```

Opmerkingen in C#

```

// Enkele regel opmerking

/*

	Blockopmerking

*/

```

## [Strings](#strings)[](#strings)

Strings in Luau

```

-- Multi-regel string

local multiLineString = [[Dit is een string die,

wanneer afgedrukt, verschijnt

op meerdere regels]]

-- Concatenatie

local s1 = "Dit is een string "

local s2 = "gemaakt met twee delen."

local endString = s1 .. s2

```

Strings in C#

```

// Multi-regel string

string multiLineString1 = "Dit is een string die,\nwanneer afgedrukt, verschijnt\n op meerdere regels.";

string multiLineString2 = @"Dit is een string die,

wanneer afgedrukt, verschijnt

op meerdere regels";

// Concatenatie

string s1 = "Dit is een string ";

string s2 = "gemaakt met twee delen.";

string endString = s1 + s2;

```

## [Tabellen](#tabellen)[](#tabellen)

Om meer te leren over tabellen in Luau, zie [Tabellen](/docs/nl-nl/luau/tables) .

### [Woordeboektabellen](#woordeboektabellen)[](#woordeboektabellen)

Je kunt tabellen in Luau gebruiken als woordenboeken, net zoals in C#.

Woordeboektabellen in Luau

```

local dictionary = {

	val1 = "dit",

	val2 = "is"

}

print(dictionary.val1)  -- Geeft 'dit' weer

print(dictionary["val1"])  -- Geeft 'dit' weer

dictionary.val1 = nil  -- Verwijdert 'val1' uit de tabel

dictionary["val3"] = "een woordenboek"  -- Overschrijft 'val3' of stelt een nieuwe sleutel-waarde paar in

```

Woordeboektabellen in C#

```

Dictionary dictionary = new Dictionary()

{

	{ "val1", "dit" },

	{ "val2", "is" }

};

Console.WriteLine(dictionary["val1"]);  // Geeft 'dit' weer

dictionary.Remove("val1");  // Verwijdert 'val1' uit het woordenboek

dictionary["val3"] = "een woordenboek";  // Overschrijft 'val3' of stelt een nieuwe sleutel-waarde paar in

dictionary.Add("val3", "een woordenboek");  // Creëert een nieuw sleutel-waarde paar

```

### [Numeriek-geïndexeerde tabellen](#numeriek-geïndexeerde-tabellen)[](#numeriek-geïndexeerde-tabellen)

Je kunt tabellen in Luau gebruiken als arrays, net zoals in C#. Indexen beginnen bij 1  in Luau en 0  in C#.

Numeriek-geïndexeerde tabellen in Luau

```

local npcAttributes = {"sterk", "intelligent"}

print(npcAttributes[1])  -- Geeft 'sterk' weer

print(#npcAttributes)  -- Geeft de grootte van de lijst weer

-- Voeg toe aan de lijst

table.insert(npcAttributes, "bescheiden")

-- Een andere manier...

npcAttributes[#npcAttributes+1] = "bescheiden"

-- Voeg toe aan het begin van de lijst

table.insert(npcAttributes, 1, "moedig")

-- Verwijder item op een gegeven index

table.remove(npcAttributes, 3)

```

Numeriek-geïndexeerde tabellen in C#

```

List npcAttributes = new List{"sterk", "intelligent"};

Console.WriteLine(npcAttributes[0]);  // Geeft 'sterk' weer

Console.WriteLine(npcAttributes.Count);  // Geeft de grootte van de lijst weer

// Voeg toe aan de lijst

npcAttributes.Add("bescheiden");

// Een andere manier...

npcAttributes.Insert(npcAttributes.Count, "bescheiden");

// Voeg toe aan het begin van de lijst

npcAttributes.Insert(0, "moedig");

// Verwijder item op een gegeven index

npcAttributes.Remove(2);

```

## [Operators](#operators)[](#operators)

### [Voorwaardelijke operators](#voorwaardelijke-operators)[](#voorwaardelijke-operators)

| Operator | | Luau | | C# |
| Gelijk Aan | | == | | == |
| Groter Dan | | > | | > |
| Kleiner Dan | | < | | < |
| Groter Dan of Gelijk Aan | | >= | | >= |
| Kleiner Dan of Gelijk Aan | | <= | | <= |
| Niet Gelijk Aan | | ~= | | != |
| En | | and | | && |
| Of | | or | | || |

### [Aritmetische operators](#aritmetische-operators)[](#aritmetische-operators)

|  | | Luau | | C# |
| Optelling | | + | | + |
| Aftrekking | | - | | - |
| Vermenigvuldiging | | * | | * |
| Deling | | / | | / |
| Modulus | | % | | % |
| Exponentiatie | | ^ | | ** |

## [Variabelen](#variabelen)[](#variabelen)

In Luau geven variabelen hun type niet aan wanneer je ze declareert. Luau-variabelen hebben geen toegangsspecifiers, hoewel je "private" variabelen kunt prefixen met een underscore voor de leesbaarheid.

Variabelen in Luau

```

local stringVariable = "waarde"

-- "Publieke" declaratie

local variableName

-- "Private" declaratie - op dezelfde manier geparsed

local _variableName

```

Variabelen in C#

```

string stringVariable = "waarde";

// Publieke declaratie

public string variableName

// Private declaratie

string variableName;

```

## [Scope](#scope)[](#scope)

In Luau kun je variabelen en logica in een striktere scope schrijven dan hun functie of klasse door de logica binnen do  en end  sleutelwoorden te nestelen, vergelijkbaar met accolades {}  in C#. Voor meer details, zie [Scope](/docs/nl-nl/luau/scope) .

Scope in Luau

```

local outerVar = 'Buitenste scope tekst'

do

    -- Wijzig 'outerVar'

    outerVar = 'Binnenste scope gewijzigde tekst'

    -- Introduceer een lokale variabele

    local innerVar = 'Binnenste scope tekst'

    print('1: ' .. outerVar)    -- print "1: Binnenste scope gewijzigde tekst"

    print('2: ' .. innerVar)    -- print "2: Binnenste scope tekst"

end

print('3: ' .. outerVar)        -- print "3: "Binnenste scope gewijzigde tekst"

-- Proberen om 'innerVar' hier af te drukken zou falen

```

Scope in C#

```

var outerVar = "Buitenste scope tekst";

{

	// Wijzig 'outerVar'

	outerVar = "Binnenste scope gewijzigde tekst";

	// Introduceer een lokale variabele

	var innerVar = "Binnenste scope tekst";

	Console.WriteLine("1: " + outerVar);    // print "1: Binnenste scope gewijzigde tekst"

	Console.WriteLine("2: " + innerVar);    // print "2: Binnenste scope tekst"

}

Console.WriteLine("3: " + outerVar);		// print "3: "Binnenste scope gewijzigde tekst"

// Proberen om 'innerVar' hier af te drukken zou falen

```

## [Voorwaardelijke uitspraken](#voorwaardelijke-uitspraken)[](#voorwaardelijke-uitspraken)

Voorwaardelijke uitspraken in Luau

```

-- Eén voorwaarde

if boolExpression then

	doSomething()

end

-- Meerdere voorwaarden

if not boolExpression then

	doSomething()

elseif otherBoolExpression then

	doSomething()

else

	doSomething()

end

```

Voorwaardelijke uitspraken in C#

```

// Eén voorwaarde

if (boolExpression) {

	doSomething();

}

// Meerdere voorwaarden

if (!boolExpression) {

	doSomething();

}

else if (otherBoolExpression) {

	doSomething();

}

else {

	doSomething();

}

```

### [Voorwaardelijke operator](#voorwaardelijke-operator)[](#voorwaardelijke-operator)

Voorwaardelijke operator in Luau

```

local max = if x > y then x else y

```

Voorwaardelijke operator in C#

```

int max = (x > y) ? x : y;

```

## [Lussen](#lussen)[](#lussen)

Om meer te leren over lussen in Luau, zie [Besturingsstructuren](/docs/nl-nl/luau/control-structures) .

### [While- en repeat-lussen](#while--en-repeat-lussen)[](#while--en-repeat-lussen)

While- en Repeat-lussen in Luau

```

while boolExpression do

	doSomething()

end

repeat

	doSomething()

until not boolExpression

```

While- en Repeat-lussen in C#

```

while (boolExpression) {

	doSomething();

}

do {

	doSomething();

} while (boolExpression)

```

### [For-lussen](#for-lussen)[](#for-lussen)

Generieke For-lussen in Luau

```

-- Voorwaartse lus

for i = 1, 10 do

	doSomething()

end

-- Achterwaartse lus

for i = 10, 1, -1 do

	doSomething()

end

```

Generieke For-lussen in C#

```

// Voorwaartse lus

for (int i = 1; i <= 10; i++) {

	doSomething();

}

// Achterwaartse lus

for (int i = 10; i >= 1; i--) {

	doSomething();

}

```

For-lussen over tabellen in Luau

```

local abcList = {"a", "b", "c"}

for i, v in ipairs(abcList) do

	print(v)

end

local abcDictionary = { a=1, b=2, c=3 }

for k, v in pairs(abcDictionary) do

	print(k, v)

end

```

For-lussen over lijsten in C#

```

List<string> abcList = new List<string>{"a", "b", "c"};

foreach (string v in abcList) {

	Console.WriteLine(v);

}

Dictionary<string, int> abcDictionary = new Dictionary<string, int>

{ {"a", 1}, {"b", 2}, {"c", 3} };

foreach (KeyValuePair<string, int> entry in abcDictionary) {

	Console.WriteLine(entry.Key + " " + entry.Value);

}

```

Luau ondersteunt ook [gegeneraliseerde iteratie](/docs/nl-nl/luau/control-structures#gegeneraliseerde-iteratie) , wat het werken met tabellen verder vereenvoudigt.

## [Functies](#functies)[](#functies)

Om meer te leren over functies in Luau, zie [Functies](/docs/nl-nl/luau/functions) .

### [Generieke functies](#generieke-functies)[](#generieke-functies)

Generieke functies in Luau

```

-- Generieke functie

local function increment(number)

	return number + 1

end

```

Generieke functies in C#

```

// Generieke functie

int increment(int number) {

	return number + 1;

}

```

### [Variabelen aantal argumenten](#variabelen-aantal-argumenten)[](#variabelen-aantal-argumenten)

Variabelen aantal argumenten in Luau

```

-- Variabelen aantal argumenten

local function variableArguments(...)

	print(...)

end

```

Variabelen aantal argumenten in C#

```

// Variabelen aantal argumenten

void variableArguments(params string[] inventoryItems) {

	for (item in inventoryItems) {

		Console.WriteLine(item);

	}

}

```

### [Genoemde argumenten](#genoemde-argumenten)[](#genoemde-argumenten)

Genoemde argumenten in Luau

```

-- Genoemde argumenten

local function namedArguments(args)

	return args.name .. "'s verjaardag: " .. args.dob

end

namedArguments{name="Bob", dob="4/1/2000"}

```

Genoemde argumenten in C#

```

// Genoemde argumenten

string namedArguments(string name, string dob) {

	return name + "'s verjaardag: " + dob;

}

namedArguments(name: "Bob", dob: "4/1/2000");

```

## [Try-catch structuren](#try-catch-structuren)[](#try-catch-structuren)

Try/Catch structuren in Luau

```

local function fireWeapon()

	if not weaponEquipped then

		error("Geen wapen uitgerust!")

	end

	-- Ga verder...

end

local success, errorMessage = pcall(fireWeapon)

if not success then

	print(errorMessage)

end

```

Try/Catch structuren in C#

```

void fireWeapon() {

	if (!weaponEquipped) {

		// Gebruik een door de gebruiker gedefinieerde uitzondering

		throw new InvalidWeaponException("Geen wapen uitgerust!");

	}

	// Ga verder...

}

try {

	fireWeapon();

} catch (InvalidWeaponException ex) {

	// Er is een fout opgetreden

}

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
