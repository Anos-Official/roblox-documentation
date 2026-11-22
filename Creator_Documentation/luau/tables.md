<!-- Source: https://create.roblox.com/docs/en-us/luau/tables -->

Tables | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/luau/tables.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Scripting](/docs/en-us/scripting)
6. /
7. [Luau reference](/docs/en-us/luau)
8. /
9. Types

# Tables

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/luau/tables.md)

The table  data type can store multiple values of any type that isn't nil , including [booleans](/docs/en-us/luau/booleans) , [numbers](/docs/en-us/luau/numbers) , [strings](/docs/en-us/luau/strings) , [functions](/docs/en-us/luau/functions) , and other tables. Construct tables with curly braces ({} ):

```

-- Construct an empty table assigned to variable "t"

local t = {}

print(t) -- {}

```

You can use a table as an [array](#arrays)  or [dictionary](#dictionaries) . Arrays use an ordered list of numbers as indices, but dictionaries can have numbers, strings, and objects as indices.

For more information on built-in functions for working with tables, see the [table](/docs/en-us/reference/engine/libraries/table)  library.

## [Arrays](#arrays)[](#arrays)

An array  is an ordered list of values. Arrays are useful for storing collections of data, such as a group of players with special permissions.

### [Create arrays](#create-arrays)[](#create-arrays)

To create an array using a Luau table, declare the values in sequential order, separated by commas.

```

-- Construct an array with three items

local testArray = {"A string", 3.14159, true}

print(testArray)

```

### [Read from arrays](#read-from-arrays)[](#read-from-arrays)

To read from an array, add a pair of square brackets after its reference and specify the index number of the element inside ([pos] ):

```

-- Construct an array with three items

local testArray = {"A string", 3.14159, true}

print(testArray[1]) -- A string

print(testArray[2]) -- 3.14159

print(testArray[3]) -- true

```

Unlike some languages, Luau uses 1-based indexing for arrays, so the first item in the array is [1] , not [0] .

### [Write to arrays](#write-to-arrays)[](#write-to-arrays)

To define or rewrite the value of an array at an index, declare the index number in square brackets ([index] ) followed by =  and the value:

```

local testArray = {"A string", 3.14159, true}

testArray[2] = 12345

testArray[4] = "New string"

print(testArray[2]) --12345

print(testArray[4]) -- New string

```

### [Iterate over arrays](#iterate-over-arrays)[](#iterate-over-arrays)

To iterate over an array, you can use a for  loop. Because the arrays have numerical indices, you can also use a numeric for  loop from 1  to the length of the array (#array ).

```

local testArray = {"A string", 3.14159, true, "New string"}

-- Loop using general iteration

for index, value in testArray do

	print(index, value)

end

-- Iterate using the array length operator (#)

for index = 1, #testArray do

	print(index, testArray[index])

end

```

### [Insert items](#insert-items)[](#insert-items)

There are two built-in ways to insert an item to the end  of an array:

-

Pass a reference to the array and the item value to Luau's [table.insert()](/docs/en-us/reference/engine/libraries/table#insert)  function.

-

Add the new item to the array using the array[#array+1]  syntax.

```

local testArray = {"A string", 3.14159}

table.insert(testArray, "New string")

testArray[#testArray+1] = "Another new string"

print(testArray[3]) -- New string

print(testArray[4]) -- Another new string

```

To insert an item between the start and end of an array, include a position value as the second argument of [table.insert()](/docs/en-us/reference/engine/libraries/table#insert) . This inserts the new item and pushes the following items up one index position.

```

local testArray = {"First item", "Next item"}

table.insert(testArray, 2, "NEW ITEM #2")

print(testArray[1]) -- First item

print(testArray[2]) -- NEW ITEM #2

print(testArray[3]) -- Next item

```

### [Remove items](#remove-items)[](#remove-items)

To remove an item from an array, use [table.remove()](/docs/en-us/reference/engine/libraries/table#remove) . This removes the item at the specified position and moves any following items back one index position.

```

local testArray = {"First item", "Next item", "Last item"}

table.remove(testArray, 2)

print(testArray[1]) -- First item

print(testArray[2]) -- Last item

```

## [Dictionaries](#dictionaries)[](#dictionaries)

Dictionaries are an extension of arrays. Dictionaries store a set of key-value pairs, where the keys can be any number, string, or object.

### [Create dictionaries](#create-dictionaries)[](#create-dictionaries)

To create a dictionary table, define each key  followed by =  and the value . Separate each key-value pair with a comma:

```

local testDictionary = {

	fruitName = "Lemon",

	fruitColor = "Yellow",

	sour = true

}

```

The keys for dictionaries can be numbers, strings, and objects. For example, a key may also be an [Instance](/docs/en-us/reference/engine/classes/Instance) . To use objects as keys, declare the key in square brackets ([key] ):

```

local part = Instance.new("Part")

local testDictionary = {

	partType = "Block",

	[part] = true

}

```

### [Read from dictionaries](#read-from-dictionaries)[](#read-from-dictionaries)

To read from a dictionary, add a pair of brackets after its reference and specify the key name. Directly reference a string key using either (["key"] ) or (.key ), or instead use a variable value ([key] ).

```

local part = Instance.new("Part")

local testDictionary = {

	partType = "Block",

	[part] = true

}

-- Include quotes for string keys

print(testDictionary["partType"]) -- Block

-- Or use . to index string keys without spaces

print(testDictionary.partType) -- Block

-- Omit quotes for non-string keys

print(testDictionary[part]) -- true

```

### [Write to dictionaries](#write-to-dictionaries)[](#write-to-dictionaries)

To define or rewrite the value of a new or existing dictionary key, declare the key name in brackets ([key] ) or, if the key is a string, use (.key ) followed by =  and the value:

```

local testDictionary = {

	fruitName = "Lemon",

	sour = true

}

-- Change value of existing keys

testDictionary["fruitName"] = "Cherry"

testDictionary.sour = false

-- Insert new key-value pair

testDictionary.fruitCount = 10

print(testDictionary.fruitName) -- Cherry

print(testDictionary.sour) -- false

print(testDictionary.fruitCount) -- 10

```

### [Iterate over dictionaries](#iterate-over-dictionaries)[](#iterate-over-dictionaries)

To iterate over a dictionary, use a for  loop:

```

local testDictionary = {

	fruitName = "Lemon",

	fruitColor = "Yellow",

	sour = true

}

for key, value in testDictionary do

	print(key, value)

end

--[[ Resulting output:

fruitName Lemon

sour true

fruitColor Yellow

]]

```

### [Remove key-value pairs](#remove-key-value-pairs)[](#remove-key-value-pairs)

To remove or erase a key-value pair from a dictionary, set its value for a key to nil .

```

local testDictionary = {

	fruitName = "Lemon",

	fruitColor = "Yellow",

	sour = true

}

testDictionary.sour = nil

for key, value in testDictionary do

	print(key, value)

end

--[[ Resulting output:

fruitName Lemon

fruitColor Yellow

]]

```

## [Tables as references](#tables-as-references)[](#tables-as-references)

If you store a table in a new variable, Luau doesn't create a copy of that table. Instead, the variable becomes a reference , or pointer, to the original table. Any reference to a table reflects any changes to the original table:

```

local originalArray = {10, 20}

local arrayReference = originalArray

print("Original:", originalArray[1], originalArray[2])

print("Reference:", arrayReference[1], arrayReference[2])

-- Change values in original array

originalArray[1] = 1000

originalArray[2] = 2000

print("Reference:", arrayReference[1], arrayReference[2])

--[[ Resulting output:

Original: 10 20

Reference: 10 20

Reference: 1000 2000

]]

```

## [Clone tables](#clone-tables)[](#clone-tables)

### [Shallow clones](#shallow-clones)[](#shallow-clones)

To copy a table without any nested tables, Luau offers the [table.clone()](/docs/en-us/reference/engine/libraries/table#clone)  method.

```

local original = {

	key = "value",

	engine = "Roblox",

	playerID = 505306092

}

local clone = table.clone(original)

```

### [Deep clones](#deep-clones)[](#deep-clones)

To copy a more complex table with nested tables inside it, you'll need to use a recursive function similar to the following:

```

-- The function used for deep cloning a table

local function deepClone(original)

	-- Define the new table for the copy

	local clone = table.clone(original)

	-- Loop through the original table to check for table values

	-- If a table is found as a value, deep clone it to the key (index)

	for key, value in original do

		if type(value) == "table" then

			clone[key] = deepClone(value)

		end

	end

	-- Return the finalized copy of the deep cloned table

	return clone

end

```

With the function in place, you can make a deep copy as follows:

```

local original = {

	key = "value",

	playerInfo = {

		playerID = 505306092,

		playerName = "PlayerName"

	},

	otherInfo = {

		{

			{1, 3, 5, 7, 9}

		}

	}

}

local clone = deepClone(original)

```

## [Freeze tables](#freeze-tables)[](#freeze-tables)

Freezing a table makes it read-only, which is useful for creating constant values that you don't want to change. Freezing is permanent; there's no "unfreeze" or "thaw" method. To check if a table is frozen, use [table.isfrozen()](/docs/en-us/reference/engine/libraries/table#isfrozen) .

### [Shallow freezes](#shallow-freezes)[](#shallow-freezes)

To freeze a table without any nested tables, Luau offers the [table.freeze()](/docs/en-us/reference/engine/libraries/table#freeze)  method.

```

local target = {

	key = "value",

	engine = "Roblox",

	playerID = 505306092

}

table.freeze(target)

target.playerID = 1 --> attempt to modify a readonly table

```

### [Deep freezes](#deep-freezes)[](#deep-freezes)

To freeze a more complex table with nested tables inside it, use a recursive function similar to the following:

```

local function deepFreeze(target)

	-- Shallow freeze the table

	table.freeze(target)

	-- Check each key of the table and freeze it if it's a table

	for _, value in target do

		-- Make sure the value isn't frozen; if it already is, an error will occur

		if type(value) == "table" and table.isfrozen(value) == false then

			deepFreeze(value)

		end

	end

end

```

With the function in place, you can deep freeze a table as follows:

```

local target = {

	key = "value",

	playerInfo = {

		playerID = 505306092,

		playerName = "PlayerName"

	},

	otherInfo = {

		{

			{1, 3, 5, 7, 9}

		}

	}

}

deepFreeze(target)

target.playerInfo.playerID = 1 --> attempt to modify a readonly table

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
