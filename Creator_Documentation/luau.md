<!-- Source: https://create.roblox.com/docs/en-us/luau -->

Luau | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/luau.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Scripting](/docs/en-us/scripting)
6. /
7. [Luau reference](/docs/en-us/luau)

# Luau

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/luau/index.md)

[Luau](https://luau.org)  is the scripting language creators use in Roblox Studio. It is a fast, small, safe, gradually typed embeddable scripting language derived from [Lua 5.1](https://www.lua.org/manual/5.1/) .

Contributing your Luau scripts for AI training can help enhance Luau-focused AI tools in Studio. For more information, see [Empower Luau creation](https://create.roblox.com/data-collection) .

## [Support in Studio](#support-in-studio)[](#support-in-studio)

The Script Editor  in Studio supports Luau with autocompletion, syntax highlighting, static linting, type checking, and script analysis. It also shows documentation and function signatures for members of the [Roblox Engine API](/docs/en-us/reference/engine) .

## [Types](#types)[](#types)

Luau includes the following data types:

-

[Nil](/docs/en-us/luau/nil)  represents non-existence or nothingness. It's different from any other value or data type.

-

[Booleans](/docs/en-us/luau/booleans) , or bool , have a value of either false  or true .

-

[Numbers](/docs/en-us/luau/numbers) , or double , represent double-precision (64-bit) floating-point numbers.

-

[Strings](/docs/en-us/luau/strings)  are sequences of characters, such as letters, numbers, and symbols.

-

[Tables](/docs/en-us/luau/tables)  are [arrays](/docs/en-us/luau/tables#arrays)  or [dictionaries](/docs/en-us/luau/tables#dictionaries)  of any value except nil .

-

[Enums](/docs/en-us/luau/enums)  are fixed lists of items.

Luau is dynamically typed by default. Variables, function parameters, and return values can be any data type. This helps you write code faster because you don't need to provide types for each piece of data. You can still declare explicit types for variables in Luau and enable [strict type checking](/docs/en-us/luau/type-checking)  to make type issues obvious and easy to locate.

## [Data structures](#data-structures)[](#data-structures)

You can also implement the following data structures using primitive data types:

-

[Stacks](/docs/en-us/luau/stacks)  are Last-In-First-Out collections of items that you can implement using tables.

-

[Queues](/docs/en-us/luau/queues)  are First-In-First-Out collections of items that you can implement using tables.

-

[Metatables](/docs/en-us/luau/metatables)  are tables with advanced configurations that can achieve functionalities such as storing pairs of keys and values and calculating arithmetic operations.

## [Features](#features)[](#features)

In Luau, [variables](/docs/en-us/luau/variables)  and [functions](/docs/en-us/luau/functions)  can have global and local [scope](/docs/en-us/luau/scope)  within a script. Luau has logical, relational, and compound assignment [operators](/docs/en-us/luau/operators) . You can use [control structures](/docs/en-us/luau/control-structures)  and [functions](/docs/en-us/luau/functions)  to control when Luau executes code. Many operators and variable assignments perform [type coercion](/docs/en-us/luau/type-coercion)  to change values to the types that Luau expects.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
