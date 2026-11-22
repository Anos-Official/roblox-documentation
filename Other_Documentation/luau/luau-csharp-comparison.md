<!-- Source: https://create.roblox.com/docs/luau/luau-csharp-comparison -->

Luau and C# comparison | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/luau/luau-csharp-comparison.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Learn](/docs/en-us/learn)

# Luau and C# comparison

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/luau/luau-csharp-comparison.md)

Roblox uses the Luau programming language. The following code samples and tables indicate some of the differences between syntaxes for C# and Luau.

## [Line endings](#line-endings)[](#line-endings)

You don't need semicolons in Luau, but they don't break the syntax.

## [Reserved keywords](#reserved-keywords)[](#reserved-keywords)

The following table has Luau's reserved keywords mapped to their C# equivalent. Note it doesn't show all C# keywords.

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
| for | | for  or foreach |
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

## [Comments](#comments)[](#comments)

Comments in Luau

```

-- Single line comment

--[[ Resulting output:

	Block comment

--]]

```

Comments in C#

```

// Single line comment

/*

	Block comment

*/

```

## [Strings](#strings)[](#strings)

Strings in Luau

```

-- Multi-line string

local multiLineString = [[This is a string that,

when printed, appears

on multiple lines]]

-- Concatenation

local s1 = "This is a string "

local s2 = "made with two parts."

local endString = s1 .. s2

```

Strings in C#

```

// Multi-line string

string multiLineString1 = "This is a string that,\nwhen printed, appears\n on multiple lines.";

string multiLineString2 = @"This is a string that,

when printed, appears

on multiple lines";

// Concatenation

string s1 = "This is a string ";

string s2 = "made with two parts.";

string endString = s1 + s2;

```

## [Tables](#tables)[](#tables)

To learn more about tables in Luau, see [Tables](/docs/luau/tables) .

### [Dictionary tables](#dictionary-tables)[](#dictionary-tables)

You can use tables in Luau as dictionaries just like in C#.

Dictionary Tables in Luau

```

local dictionary = {

	val1 = "this",

	val2 = "is"

}

print(dictionary.val1)  -- Outputs 'this'

print(dictionary["val1"])  -- Outputs 'this'

dictionary.val1 = nil  -- Removes 'val1' from table

dictionary["val3"] = "a dictionary"  -- Overwrites 'val3' or sets new key-value pair

```

Dictionary Tables in C#

```

Dictionary dictionary = new Dictionary()

{

	{ "val1", "this" },

	{ "val2", "is" }

};

Console.WriteLine(dictionary["val1"]);  // Outputs 'this'

dictionary.Remove("val1");  // Removes 'val1' from dictionary

dictionary["val3"] = "a dictionary";  // Overwrites 'val3' or sets new key-value pair

dictionary.Add("val3", "a dictionary");  // Creates a new key-value pair

```

### [Numerically-indexed tables](#numerically-indexed-tables)[](#numerically-indexed-tables)

You can use tables in Luau as arrays just like in C#. Indices start at 1  in Luau and 0  in C#.

Numerically-Indexed Tables in Luau

```

local npcAttributes = {"strong", "intelligent"}

print(npcAttributes[1])  -- Outputs 'strong'

print(#npcAttributes)  -- Outputs the size of the list

-- Append to the list

table.insert(npcAttributes, "humble")

-- Another way...

npcAttributes[#npcAttributes+1] = "humble"

-- Insert at the beginning of the list

table.insert(npcAttributes, 1, "brave")

-- Remove item at a given index

table.remove(npcAttributes, 3)

```

Numerically-Indexed Tables in C#

```

List npcAttributes = new List{"strong", "intelligent"};

Console.WriteLine(npcAttributes[0]);  // Outputs 'strong'

Console.WriteLine(npcAttributes.Count);  // Outputs the size of the list

// Append to the list

npcAttributes.Add("humble");

// Another way...

npcAttributes.Insert(npcAttributes.Count, "humble");

// Insert at the beginning of the list

npcAttributes.Insert(0, "brave");

// Remove item at a given index

npcAttributes.Remove(2);

```

## [Operators](#operators)[](#operators)

### [Conditional operators](#conditional-operators)[](#conditional-operators)

| Operator | | Luau | | C# |
| Equal To | | == | | == |
| Greater Than | | > | | > |
| Less Than | | < | | < |
| Greater Than or Equal To | | >= | | >= |
| Less Than or Equal To | | <= | | <= |
| Not Equal To | | ~= | | != |
| And | | and | | && |
| Or | | or | | || |

### [Arithmetic operators](#arithmetic-operators)[](#arithmetic-operators)

|  | | Luau | | C# |
| Addition | | + | | + |
| Subtraction | | - | | - |
| Multiplication | | * | | * |
| Division | | / | | / |
| Modulus | | % | | % |
| Exponentiation | | ^ | | ** |

## [Variables](#variables)[](#variables)

In Luau, variables don't specify their type when you declare them. Luau variables don't have access modifiers, although you may prefix "private" variables with an underscore for readability.

Variables in Luau

```

local stringVariable = "value"

-- "Public" declaration

local variableName

-- "Private" declaration - parsed the same way

local _variableName

```

Variables in C#

```

string stringVariable = "value";

// Public declaration

public string variableName

// Private declaration

string variableName;

```

## [Scope](#scope)[](#scope)

In Luau, you can write variables and logic in a tighter scope than their function or class by nesting the logic within do  and end  keywords, similar to curly brackets {}  in C#. For more details, see [Scope](/docs/luau/scope) .

Scoping in Luau

```

local outerVar = 'Outer scope text'

do

    -- Modify 'outerVar'

    outerVar = 'Inner scope modified text'

    -- Introduce a local variable

    local innerVar = 'Inner scope text'

    print('1: ' .. outerVar)    -- prints "1: Inner scope modified text"

    print('2: ' .. innerVar)    -- prints "2: Inner scope text"

end

print('3: ' .. outerVar)        -- prints "3: "Inner scope modified text"

-- Attempting to print 'innerVar' here would fail

```

Scoping in C#

```

var outerVar = "Outer scope text";

{

	// Modify 'outerVar'

	outerVar = "Inner scope modified text";

	// Introduce a local variable

	var innerVar = "Inner scope text";

	Console.WriteLine("1: " + outerVar);    // prints "1: Inner scope modified text"

	Console.WriteLine("2: " + innerVar);    // prints "2: Inner scope text"

}

Console.WriteLine("3: " + outerVar);		// prints "3: "Inner scope modified text"

// Attempting to print 'innerVar' here would fail

```

## [Conditional statements](#conditional-statements)[](#conditional-statements)

Conditional Statements in Luau

```

-- One condition

if boolExpression then

	doSomething()

end

-- Multiple conditions

if not boolExpression then

	doSomething()

elseif otherBoolExpression then

	doSomething()

else

	doSomething()

end

```

Conditional Statements in C#

```

// One condition

if (boolExpression) {

	doSomething();

}

// Multiple conditions

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

### [Conditional operator](#conditional-operator)[](#conditional-operator)

Conditional Operator in Luau

```

local max = if x > y then x else y

```

Conditional Operator in C#

```

int max = (x > y) ? x : y;

```

## [Loops](#loops)[](#loops)

To learn more about loops in Luau, see [Control Structures](/docs/luau/control-structures) .

### [While and repeat loops](#while-and-repeat-loops)[](#while-and-repeat-loops)

While and Repeat Loops in Luau

```

while boolExpression do

	doSomething()

end

repeat

	doSomething()

until not boolExpression

```

While and Repeat Loops in C#

```

while (boolExpression) {

	doSomething();

}

do {

	doSomething();

} while (boolExpression)

```

### [For loops](#for-loops)[](#for-loops)

Generic For Loops in Luau

```

-- Forward loop

for i = 1, 10 do

	doSomething()

end

-- Reverse loop

for i = 10, 1, -1 do

	doSomething()

end

```

Generic For Loops in C#

```

// Forward loop

for (int i = 1; i <= 10; i++) {

	doSomething();

}

// Reverse loop

for (int i = 10; i >= 1; i--) {

	doSomething();

}

```

For Loops Over Tables in Luau

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

For Loops Over Lists in C#

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

Luau also supports [generalized iteration](/docs/luau/control-structures#generalized-iteration) , which further simplifies working with tables.

## [Functions](#functions)[](#functions)

To learn more about functions in Luau, see [Functions](/docs/luau/functions) .

### [Generic functions](#generic-functions)[](#generic-functions)

Generic Functions in Luau

```

-- Generic function

local function increment(number)

	return number + 1

end

```

Generic Functions in C#

```

// Generic function

int increment(int number) {

	return number + 1;

}

```

### [Variable argument number](#variable-argument-number)[](#variable-argument-number)

Variable Argument Number in Luau

```

-- Variable argument number

local function variableArguments(...)

	print(...)

end

```

Variable Argument Number in C#

```

// Variable argument number

void variableArguments(params string[] inventoryItems) {

	for (item in inventoryItems) {

		Console.WriteLine(item);

	}

}

```

### [Named arguments](#named-arguments)[](#named-arguments)

Named Arguments in Luau

```

-- Named arguments

local function namedArguments(args)

	return args.name .. "'s birthday: " .. args.dob

end

namedArguments{name="Bob", dob="4/1/2000"}

```

Named Arguments in C#

```

// Named arguments

string namedArguments(string name, string dob) {

	return name + "'s birthday: " + dob;

}

namedArguments(name: "Bob", dob: "4/1/2000");

```

## [Try-catch structures](#try-catch-structures)[](#try-catch-structures)

Try/Catch Structures in Luau

```

local function fireWeapon()

	if not weaponEquipped then

		error("No weapon equipped!")

	end

	-- Proceed...

end

local success, errorMessage = pcall(fireWeapon)

if not success then

	print(errorMessage)

end

```

Try/Catch Structures in C#

```

void fireWeapon() {

	if (!weaponEquipped) {

		// Use a user-defined exception

		throw new InvalidWeaponException("No weapon equipped!");

	}

	// Proceed...

}

try {

	fireWeapon();

} catch (InvalidWeaponException ex) {

	// An error was raised

}

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
