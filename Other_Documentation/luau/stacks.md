<!-- Source: https://create.roblox.com/docs/luau/stacks -->

Stacks | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/luau/stacks.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Scripting](/docs/scripting)
6. /
7. [Luau reference](/docs/luau)
8. /
9. Data structures

# Stacks

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/luau/stacks.md)

A stack is a linear data structure with a collection of items that follows the Last-In-First-Out (LIFO) principle. The top of the stack is the item most recently added to the stack, and the bottom of the stack is the item that was least recently added.

You can think of the stack data structure as a stack of dinner plates: you start with one, and then you put another above it. When you take plates from the stack, the first  one you remove from the stack is the last  one you put on the top.

Stacks have two main operations: push  for adding an element to the top of the stack and pop  for removing the element from the top of the stack. A Stack can either have a fixed size or be dynamically resized. Stacks are helpful for design usage such as backtracking algorithms.

## [Implement stacks](#implement-stacks)[](#implement-stacks)

Though Luau doesn't have stacks as a built-in data structure, you can use [tables](/docs/luau/tables)  to implement stacks. The following code sample shows how to create a stack, push  an object to a stack, and pop  an object from the stack. To use this implementation for your game, you should save it as a [ModuleScript](/docs/reference/engine/classes/ModuleScript)  and store it in [ReplicatedStorage](/docs/reference/engine/classes/ReplicatedStorage) , so your stack is accessible for both client and server.

```

local Stack = {}

Stack.__index = Stack

function Stack.new()

	local self = setmetatable({}, Stack)

	self._stack = {}

	return self

end

-- Check if the stack is empty

function Stack:isEmpty()

	return #self._stack == 0

end

-- Put a new value onto the stack

function Stack:push(value)

	table.insert(self._stack, value)

end

-- Take a value off the stack

function Stack:pop()

	if self:isEmpty() then

		return nil

	end

	return table.remove(self._stack, #self._stack)

end

return Stack

```

The following code sample is a usage example as a [Script](/docs/reference/engine/classes/Script)  under [Workspace](/docs/reference/engine/classes/Workspace) . You can modify the code, type, and storage location to fit your own usage, as long as you have the previous implementation code sample properly stored.

Stack Usage Example

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Stack = require(ReplicatedStorage:WaitForChild("Stack"))

local s = Stack.new()

-- Change the stack 	Resulting stack		 Output

s:push(1)      			-- {1}

s:push(5)      			-- {1, 5}

s:push(10)     			-- {1, 5, 10}

print(s:pop()) 			-- {1, 5}            10

print(s:pop()) 			-- {1}               5

s:push(20)     			-- {1, 20}

print(s:pop()) 			-- {1}               20

print(s:pop()) 			-- {}                1

```

When running pop()  on a stack, make sure the stack is not empty.

If you run the previous code sample without changing anything, the expected output is:

Example Output

```

10

5

20

1

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
