<!-- Source: https://create.roblox.com/docs/en-us/luau/nil -->

Nil | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/luau/nil.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Scripting](/docs/en-us/scripting)
6. /
7. [Luau reference](/docs/en-us/luau)
8. /
9. Types

# Nil

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/luau/nil.md)

In Luau, nil  represents non-existence or nothingness. It's different from any other value or data type. You can use it to destroy a variable or remove a value in a table. It's the only value other than false  which doesn't evaluate to [true](/docs/en-us/luau/booleans) .

Luau has a garbage collector  that removes data that is no longer accessible by any script. For best performance, redefine large variables as nil  in long-running scripts when you don't need them anymore so the garbage collector removes them.

```

local variableToDelete = 5

print(variableToDelete) -- 5

variableToDelete = nil

print(variableToDelete) -- nil

local dictionaryTable = {

	Monday = 1,

	Tuesday = 2,

	Wednesday = 3

}

-- Output value of 'Tuesday' key

print(dictionaryTable.Tuesday) -- 2

-- Clear 'Tuesday' key

dictionaryTable.Tuesday = nil

-- Output value of key again

print(dictionaryTable.Tuesday) -- nil

```

You can use nil  to clear some properties of objects. For example, you can set the Parent  of an object to nil  to effectively remove the object from the game. To return the object to the game after you remove it, reassign the Parent . The following example demonstrates how to use nil  to remove a [Part](/docs/en-us/reference/engine/classes/Part) :

```

local Workspace = game:GetService("Workspace")

-- Create a new brick

local part = Instance.new("Part")

-- Parent new part to the workspace, making it viewable

part.Parent = Workspace

task.wait(1)

-- Remove the part from view but not from memory

part.Parent = nil

task.wait(1)

-- Part still exists because it's referenced by the variable "part", so it can be returned to view

part.Parent = Workspace

task.wait(1)

-- Remove the part from view again

part.Parent = nil

-- Clear part reference so it gets picked up by the garbage collector

part = nil

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
