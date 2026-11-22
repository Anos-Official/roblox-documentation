<!-- Source: https://create.roblox.com/docs/en-us/tutorials/fundamentals/coding-6/intro-to-module-scripts -->

Intro to module scripts | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/tutorials/fundamentals/coding-6/intro-to-module-scripts.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Tutorials](/docs/en-us/tutorials)
4. /
5. [Organize code](/docs/en-us/tutorials/fundamentals/coding-6/landing)

# Intro to module scripts

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/tutorials/fundamentals/coding-6/intro-to-module-scripts.md)

As projects become complex, it becomes important to think how scripts are organized. Good organization practices can ensure code isn't duplicated between scripts, or becomes hard to manage.

A better way to organize and reuse code is with module scripts , a unique type of script that stores a set of functions and variables designed to meet a shared purpose, like managing player money or enemies. Code within module scripts can be used by other scripts. That way, you can call the same function that gives coins from multiple different scripts whenever a player finishes a quest or finds a pickup.

By storing commonly used code in module scripts, it makes maintaining and organizing code easier since changes only need to be made to one module script, rather than updating multiple scripts.

Normal scripts should be used for standalone elements of a game, such as touching a pickup, while module scripts are useful for storing code that can be reused by multiple independent scripts, like rewarding points.

## [Module script basics](#module-script-basics)[](#module-script-basics)

Module scripts are actually their own separate object compared to script objects. In Roblox, module scripts can be denoted with a purple  icon.

### [Create a module script](#create-a-module-script)[](#create-a-module-script)

ModuleScripts are commonly placed in ServerScriptService  when used by server-side scripts and ReplicatedStorage  when used by client-side local scripts (such as GUI interactions).

1.

Create a ModuleScript  in ServerScriptService .

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-6/intro-to-module-scripts/create-module-script.png)

### [Structure of module scripts](#structure-of-module-scripts)[](#structure-of-module-scripts)

When created, every module script starts out with the code below:

```

local Module = {}

return Module

```

The line local Module = {}  creates a table, or container of code, where the module's shared functions and variables can be stored. This table should be renamed to the module's purpose, such as RewardManager  or ParticleController . As opposed to other variables which are camel case (myVariable ), module tables are recommended to use pascal case and start capitalized (MyModule ).

```

local RewardManager = {}

return RewardManager

```

So other scripts can use a module's non-local functions or variables, every module ends with return MyModule . Whenever another script tries to get code from the module, return lets that script access code stored inside the module table.

### [Add to module scripts](#add-to-module-scripts)[](#add-to-module-scripts)

To add a function or variable to the module which can be used in another script, type the module table's name, followed by a dot, and the name of the function or variable, like in TestModule.myVariable . Using the dot operator is another way of adding code into a table, allowing other scripts to access that code whenever the module table is returned.

```

local TestModule = {}

-- Adds a variable to 'TestModule' table

TestModule.myVariable = 100

-- Adds a function to 'TestModule' table

function TestModule.doTask(player)

	-- Placeholder code

end

return TestModule

```

Anything added to the module table should be typed between local MyModule = {}  and return MyModule , or else the code may create an error.

### [Scope in module scripts](#scope-in-module-scripts)[](#scope-in-module-scripts)

For a module function or variable to be used in an outside script, don't  type local .

Typing local  in front of variables and functions means they are only  usable by that script. While this is a good practice for most scripts for reducing errors and troubleshooting, you cannot make module script functions and variables local.

Any code used only  by that module script should still include local . For instance, the code below includes the local variable difficultyModifier , which can only be used in that module script, and the function getCoinReward() , which can be used in scripts outside the module.

```

local RewardManager = {}

-- Usable only in the module script

local rewardCoins = 50

-- Usable only in the module script

local difficultyModifier = {

	easy = 0.5,

	normal = 1,

	hard = 2

}

-- Usable in other scripts

function RewardManager.getCoinReward(difficulty)

	local coins = difficultyModifier[difficulty] * rewardCoins

	return coins

end

return RewardManager

```

## [Use modules in other scripts](#use-modules-in-other-scripts)[](#use-modules-in-other-scripts)

By itself, a module script can't run code — it needs to be loaded in another script using the keyword [require()](/docs/en-us/reference/engine/globals/LuaGlobals#require) . The function [require()](/docs/en-us/reference/engine/globals/LuaGlobals#require)  accepts one argument, the location of the module script in the Explorer.

To use a module, in a separate script, set a variable equal to require(moduleScript) .

```

local MyModule = require(ServerStorage.ModuleScript)

```

Now, the variable MyModule  contains the module table created in that module script. To use functions and variables from that table, type the variable name, followed by a dot, and the exact name of what to use in that module script, like MyModule.myFunction() . When the script runs and reaches that line, it'll access that specific function or variable stored in the module table.

```

local MyModule = require(ServerStorage.ModuleScript)

MyModule.myFunction()

```

## [RewardManager example](#rewardmanager-example)[](#rewardmanager-example)

ModuleScript - RewardManager

```

local RewardManager = {}

-- Usable only in the module script

local rewardCoins = 50

-- Usable only in the module script

local difficultyModifier = {

 easy = 0.5,

 normal = 1,

 hard = 2

}

-- Usable in other scripts

function RewardManager.getCoinReward(difficulty)

 local coins = difficultyModifier[difficulty] * rewardCoins

 return coins

end

return RewardManager

```

Script - TreasureChestScript

```

local ServerStorage = game:GetService("ServerStorage")

-- Load module script

local RewardManager = require(ServerStorage.RewardManager)

--Calls function from module script

local coins = RewardManager.getCoinReward("easy")

print("Should award " .. coins .. " coins")

```

If you're in another script, make sure that the module script function or variable is spelled exactly  the same as found in that module. To help, you can copy the exact function or variable name from the module and then just paste it in the normal script where it'll be used.

## [General troubleshooting](#general-troubleshooting)[](#general-troubleshooting)

Some of the tips here address common issues when working with module scripts. Keep in mind that module scripts can be a complicated topic with more nuance. For more details, see this more technical guide on [Module Scripts](/docs/en-us/scripting/module) .

Issue:  Get an error message including: "Infinite yield possible"  or "not a valid member" .

-

Check the spelling of the module script where it's loaded. [require()](/docs/en-us/reference/engine/globals/LuaGlobals#require)  must include the exact path and spelling of the module script, which may be named differently than the module table.

Issue:  Get an error message including: "attempt to index global" .

-

In any scripts using a module script, make sure it's loaded using the function [require()](/docs/en-us/reference/engine/globals/LuaGlobals#require) . If not, that script cannot use functions and variables from the module script.

## [Summary](#summary)[](#summary)

Module scripts  in Roblox are a method coders use to organize and reuse code. A module script is often stored in ServerStorage (or ReplicatedStorage for client-based interactions). From there, other scripts are able to call functions and variables stored in that module script.

For instance, one game may award points to players for collecting objects. A module script can handle code to give points. Then, scripts for different types of objects can just call the module script function. This reduces the need to reuse code between scripts, making code easier to understand and maintain.

[Next](/docs/en-us/tutorials/fundamentals/coding-6/create-with-module-scripts)[Previous](/docs/en-us/tutorials/fundamentals/coding-6/landing)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
