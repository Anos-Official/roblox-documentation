<!-- Source: https://create.roblox.com/docs/en-us/scripting -->

Scripting | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/scripting.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Scripting](/docs/en-us/scripting)

# Scripting

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/scripting/index.md)

Scripts are plain text files that let you add custom, dynamic behavior to your games. You can use scripts to trigger in-game events, respond to player input, save player data, create leaderboards, spawn enemies, control NPC behavior, and much, much more.

This section is for creators with some coding experience who want to know the specifics of scripting in Roblox.

If you've never written code before and want an introduction to programming, see [Coding fundamentals](/docs/en-us/tutorials/fundamentals/coding-1/coding-fundamentals) , which covers concepts like variables, functions, conditionals, loops, and arrays. For a more guided, step-by-step approach, see the [Basic gameplay](/docs/en-us/tutorials/use-case-tutorials/scripting/basic-scripting/intro-to-scripting)  tutorial.

## [Luau](#luau)[](#luau)

Roblox scripts use the [Luau](https://luau.org)  programming language, which is derived from [Lua 5.1](https://www.lua.org/manual/5.1/) .

-

Compared to Lua 5.1, Luau adds performance enhancements and many useful features, including an optional typing system, string interpolation, and generalized iteration for tables.

-

All valid Lua 5.1 code is valid Luau code, but the opposite is not true.

Most books and online resources for Lua are still broadly applicable to Luau. For a detailed summary of differences, see [Compatibility](https://luau.org/compatibility)  in the Luau documentation. For language syntax, see the [Luau reference](/docs/en-us/luau) .

### [Luau basics](#luau-basics)[](#luau-basics)

Luau is gradually typed, so you don't need to specify a type when you create a variable. You can use [type()](/docs/en-us/reference/engine/globals/LuaGlobals#type)  to check object type:

```

logMessage = "User has more than 10 items!"

print(logMessage) --> User has more than 10 items!

print(type(logMessage)) --> string

```

Luau has global and local [scopes](/docs/en-us/luau/scope) , but it's almost always better to declare variables and functions locally with the local  keyword:

```

local logMessage = "User has more than 10 items!"

local function printMessage()

	print(logMessage)

end

printMessage() --> User has more than 10 items!

```

Luau uses nil  to represent nonexistence or nothingness, which evaluates as false  in conditional statements:

```

local messageToUser

print(messageToUser) --> nil

print(type(messageToUser)) --> nil

if messageToUser then

	-- statement evaluates to false

end

```

As you might have noticed, --  starts a one-line comment. --[[]]  creates a block comment:

```

--[[

    Shuts off the cosmic moon ray immediately.

    Should only be called within 15 minutes of midnight Mountain Standard

    Time to avoid damage to the cosmic moon ray.

]]

local function stopCosmicMoonRay()

	-- add this later, it might prove important

end

```

[Tables](/docs/en-us/luau/tables)  are the generic term for arrays and dictionaries. Arrays are one-based rather than zero-based, so the first item is [1] . You declare arrays and dictionaries with a single set of curly braces:

```

local myArray = {"chips", "sparkling water", "salsa"}

local myDictionary = {

	snack = "chips",

	drink = "sparkling water",

	dip = "salsa"

}

print(myArray[1]) --> chips

print(myDictionary.dip) --> salsa

```

You can iterate over tables using for  loops with the [ipairs()](/docs/en-us/reference/engine/globals/LuaGlobals#ipairs)  function for arrays and the [pairs()](/docs/en-us/reference/engine/globals/LuaGlobals#pairs)  function for dictionaries, but Luau also lets you omit these functions for cleaner syntax:

```

for index, value in ipairs(myArray) do -- standard Lua

	print(index, value)

end

for key, value in pairs(myDictionary) do -- standard Lua

	print(key, value)

end

for key, value in myDictionary do -- Luau generalized iteration

	print(key, value)

end

```

## [Your first script](#your-first-script)[](#your-first-script)

1.

In Roblox Studio, hover over ServerScriptService  in the [Explorer](/docs/en-us/studio/explorer)  window and click + .

2.

Select Script  to add a new script.

3.

Right-click the script and rename it to HelloScript .

4.

Double-click the script to open it in the [Script Editor](/docs/en-us/studio/script-editor) .

5.

Add the following code to the file:

```

local helloArray = {"h", "e", "l", "l", "o"}

local worldArray = {"w", "o", "r", "l", "d"}

for index, value in helloArray do

	print(value)

end

print(table.concat(worldArray))

```

6.

Ensure that the [Output](/docs/en-us/studio/output)  window is open.

7.

[Run your game](/docs/en-us/studio/testing-modes#playtesting)  and note the output:

```

h

e

l (x2)

o

world

```

## [Get comfortable](#get-comfortable)[](#get-comfortable)

A big part of adapting to a new development environment is configuring it to meet your needs and understanding the tools at your disposal:

-

The Script Editor  section of [Studio Settings](/docs/en-us/studio/setup#customization)  lets you adjust quality of life features like font, colors, indentation, autocomplete, brackets, and tooltips. You might also want to enable dark mode in the Studio  section.

-

Holding Ctrl  or Command  and clicking on a function or variable takes you to its declaration in your codebase (or its online documentation). Using [Find and Find All](/docs/en-us/studio/script-editor#find-and-replace)  can help you navigate larger projects.

-

The [Output](/docs/en-us/studio/output)  window is the most basic tool for understanding the behavior of your scripts. Use the ⋯  menu to enable Show Context  and Show Source .

-

The [Script Analysis](/docs/en-us/studio/script-editor#script-analysis)  window shows a summary of errors and warnings, but you might find its utility limited; the Script Editor already highlights these issues as you type.

-

Logging capabilities are minimal, with no concept of log levels like DEBUG  or FATAL . Use [print()](/docs/en-us/reference/engine/globals/LuaGlobals#print)  and [warn()](/docs/en-us/reference/engine/globals/RobloxGlobals#warn) .

For more information about configuring Studio for scripting, see [Script Editor](/docs/en-us/studio/script-editor) .

Many developers prefer to use an external text editor and version control system rather than the built-in editor. See [Script Sync](/docs/en-us/scripting/sync)  and [third-party tools](/docs/en-us/projects/external-tools) .

## [Your second script](#your-second-script)[](#your-second-script)

1.

In Roblox Studio, add a script to ReplicatedStorage  in the [Explorer](/docs/en-us/studio/explorer)  window and rename it to OhNo .

2.

Add the following code to the file:

```

print("Hello script types and locations!")

```

3.

[Run your game](/docs/en-us/studio/testing-modes#playtesting) .

4.

Note how the output is no different than when you ran [your first script](#your-first-script) .

To understand why the script didn't run, see [Script Types and Locations](/docs/en-us/scripting/locations) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
