<!-- Source: https://create.roblox.com/docs/en-us/tutorials/fundamentals/coding-5/return-values-from-tables -->

Return values from tables | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/tutorials/fundamentals/coding-5/return-values-from-tables.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Tutorials](/docs/en-us/tutorials)
4. /
5. [Dictionaries and arrays](/docs/en-us/tutorials/fundamentals/coding-5/landing)

# Return values from tables

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/tutorials/fundamentals/coding-5/return-values-from-tables.md)

A common need in many data structures is to return values. This article will cover searching a table using pairs()  or ipairs()  for half of any table element, such as the key or value, to find and return the other half.

The example uses an array listing ships waiting to be repaired. ipairs()  is used to return a ship's place in line.

## [Dictionary search example](#dictionary-search-example)[](#dictionary-search-example)

Have you ever searched for a lost pet in house going room by room? On your own code a function to search through a dictionary named house to see which room holds a lost puppy.

1.

Copy the dictionary below to act as the house.

```

local house = {

	kitchen = "pile of Junk",

	livingRoom = "kitten",

	bedroom1 = "nobody there",

	bedroom2 = "puppy",

}

```

2.

Create a new function called findPet()  to search the dictionary. Include parameters for what dictionary to search, and what value to search for.

3.

Use pairs()  to iterate through the dictionary. Try coding your own before checking your work in the solution below.

```

local function findPet(whereToSearch, searchFor)

	for place, value in pairs(whereToSearch) do

	end

end

```

4.

As the for loop iterates through the dictionary, use return  to pass back the room where the pet was found.

[Next](/docs/en-us/tutorials/fundamentals/coding-6/landing)[Previous](/docs/en-us/tutorials/fundamentals/coding-5/pairs-and-ipairs)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
