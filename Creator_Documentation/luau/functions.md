<!-- Source: https://create.roblox.com/docs/en-us/luau/functions -->

Functions | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/luau/functions.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Scripting](/docs/en-us/scripting)
6. /
7. [Luau reference](/docs/en-us/luau)
8. /
9. Features

# Functions

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/luau/functions.md)

Functions  are [blocks of code](/docs/en-us/luau/scope)  that you can execute multiple times on command. You can also connect them to [events](#event-handlers)  or assign them as [callbacks](#callbacks) .

## [Basic functions](#basic-functions)[](#basic-functions)

A function definition includes:

-

The [scope](/docs/en-us/luau/scope)  of the function: global or local  (or [const](/docs/en-us/luau/variables#const-variables)  for a local function whose name you can't reassign).

-

The function  keyword.

-

The name of the function in camelCase .

-

The parameters of the function in parentheses (() ).

-

The block of code, or "body", of the function.

-

The end  keyword.

The body of the function executes when you call the function. To call a function, type its name followed by parentheses. You can define a variable to accept the return value or use the return value in place of a variable.

```

-- This function has no parameters and returns nil

local function addOneAndTwo()

	local result = 1 + 2

	print(result)

end

-- Calling a function without a return

addOneAndTwo() -- 3

```

### [Parameters](#parameters)[](#parameters)

Parameters are variables that you make available to the function and are only used in the function's [scope](/docs/en-us/luau/scope) . Functions have no parameters by default. If you call a function with more parameters than it expects, Luau ignores the extra parameters. If you call a function with fewer parameters than it expects, Luau passes nil  for all missing parameters.

```

-- This function has two parameters: num1 and num2

local function addNumbers(num1, num2)

	print(num1 + num2)

end

addNumbers(2, 3) -- 5

addNumbers(5, 6, 7) -- 11

addNumbers(9) -- attempt to perform arithmetic (add) on number and nil

```

### [Return](#return)[](#return)

In the body of the function, the return  keyword returns a result from a computation. You can return multiple values from one function. return  ends function execution, and Luau expects the end  keyword to follow the return  statements, so writing code between the return  command and the end  command throws an error.

```

-- This function returns one return value

local function addNumbers(num1, num2)

	local result = num1 + num2

	return result

end

print(addNumbers(1, 2)) -- 3

local seven = addNumbers(3, 4)

print(seven) -- 7

-- This function returns multiple values: sum and difference

local function addAndSubtract(num1, num2)

	local sum = num1 + num2

	local difference = num1 - num2

	return sum, difference

end

-- Calling a function and expecting multiple return values

local sum, difference = addAndSubtract(2, 3)

print(sum) -- 5

print(difference) -- -1

```

## [Methods](#methods)[](#methods)

Methods are functions that are members of an object, such as a [class](/docs/en-us/reference/engine/classes)  or [table](/docs/en-us/luau/tables) . They expect the object itself (self ) as the first argument. When you call a method, use the colon notation (: ) instead of dot notation (. ) to pass self  as the first argument automatically.

All objects in Roblox descend from [Instance](/docs/en-us/reference/engine/classes/Instance)  and have commonly used methods including [Instance:Destroy()](/docs/en-us/reference/engine/classes/Instance#Destroy) , [Instance:Clone()](/docs/en-us/reference/engine/classes/Instance#Clone) , and [Instance:FindFirstChild()](/docs/en-us/reference/engine/classes/Instance#FindFirstChild) .

```

local Workspace = game:GetService("Workspace")

-- Destroying a part with dot notation (function)

local firstPart = Instance.new("Part")

firstPart.Parent = Workspace

print(firstPart.Parent) -- Workspace

firstPart.Destroy(firstPart)

print(firstPart.Parent) -- nil

-- Destroying a part with colon notation (method)

local secondPart = Instance.new("Part")

secondPart.Parent = Workspace

print(secondPart.Parent) -- Workspace

secondPart:Destroy()

print(secondPart.Parent) -- nil

```

The statement table:Method()  is functionally identical to table.Method(table) , and when defining a method, function table:Method()  is identical to function table.Method(self) . This behavior extends to [Instance](/docs/en-us/reference/engine/classes/Instance)  methods, since they are also derived from tables.

### [Define methods](#define-methods)[](#define-methods)

To create a method in a table, use the name of the method as the key and the method function as the value. In the definition of the method, the self  parameter refers to the method's parent table. When you call a method using colon notation, you pass the table itself as the first argument. You can define parameters for a method, but you need to list them after the self  parameter.

In the following example, the testButton  table has a method as the value of the changeEnabled  key. You can verify that self  refers to the method's parent table by printing the value of self.enabled .

```

local testButton = {

	enabled = true,

	changeEnabled = function(self, isEnabled)

		self.enabled = isEnabled

		print(self.enabled)

	end

}

print(testButton.enabled) -- true

-- Call the method

testButton:changeEnabled(false) -- false

```

## [Callbacks](#callbacks)[](#callbacks)

Callbacks are functions that execute in response to another function or process.

### [Basic callbacks](#basic-callbacks)[](#basic-callbacks)

Functions can be passed into other functions, for example, an [anonymous](#anonymous-functions)  function can be used to implement a callback that [table.sort()](/docs/en-us/reference/engine/libraries/table#sort)  then uses to sort a list of [Players](/docs/en-us/reference/engine/classes/Player)  from [Players.GetPlayers()](/docs/en-us/reference/engine/classes/Players#GetPlayers) .

```

local Players = game:GetService("Players")

local sortedPlayers = Players:GetPlayers()

table.sort(sortedPlayers, function(a, b)

	-- Use an anonymous callback to sort players by name

	return a.Name < b.Name

end)

```

In the Roblox API, callbacks refer to a write-only function member, callbacks yield until they return. Widely used callbacks include:

-

[MarketplaceService.ProcessReceipt](/docs/en-us/reference/engine/classes/MarketplaceService#ProcessReceipt) , which handles developer products purchases.

-

[BindableFunction.OnInvoke](/docs/en-us/reference/engine/classes/BindableFunction#OnInvoke) , which calls the function when a script calls BindableFunction:Invoke(...) .

-

[RemoteFunction.OnClientInvoke](/docs/en-us/reference/engine/classes/RemoteFunction#OnClientInvoke) , which calls the function when the server calls RemoteFunction:FireClient(player, ...)  or RemoteFunction:FireAllClients(...) .

-

[RemoteFunction.OnServerInvoke](/docs/en-us/reference/engine/classes/RemoteFunction#OnServerInvoke) , which calls the function when a client calls RemoteFunction:InvokeServer(...) .

To set a callback, assign a function to it. For example, [BindableFunction.OnInvoke](/docs/en-us/reference/engine/classes/BindableFunction#OnInvoke)  is a callback of [BindableFunction](/docs/en-us/reference/engine/classes/BindableFunction) . You can set a named or [anonymous](#anonymous-functions)  function to it, and you can call (invoke ) that function by calling the :Invoke()  method on the callback. The arguments you pass to :Invoke()  forward to the callback, and the return value from the callback function returns to the caller of :Invoke() .

```

local bindableFunction = Instance.new("BindableFunction")

bindableFunction.OnInvoke = function(number)

	return 2 * number

end

print(bindableFunction:Invoke(42)) -- 84

```

## [Function techniques](#function-techniques)[](#function-techniques)

### [Event handlers](#event-handlers)[](#event-handlers)

You can assign a function, known as an event handler , to execute when an event fires. For example, you can create a function called onPlayerAdded()  to the [Players.PlayerAdded](/docs/en-us/reference/engine/classes/Players#PlayerAdded)  event to print the name of whatever player joins. For more information, see [Events](/docs/en-us/scripting/events) .

```

local Players = game:GetService("Players")

local function onPlayerAdded(player)

	print(player.Name .. " joined the game!")

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

### [Anonymous functions](#anonymous-functions)[](#anonymous-functions)

You can create functions without names, known as anonymous functions , to use as [callbacks](#callbacks)  and [event handlers](#event-handlers) . Like named functions, anonymous functions need to start and end with the function  and end  keywords, but you don't need the local  keyword to indicate local scope because they always have local scope.

In the following example, the callback for the [task.delay()](/docs/en-us/reference/engine/libraries/task#delay)  function and the event handler for the [Players.PlayerAdded](/docs/en-us/reference/engine/classes/Players#PlayerAdded)  event are both anonymous functions.

```

-- Anonymous function in a callback to task.delay()

task.delay(2, function(exactTimeElapsed)

	print(exactTimeElapsed) -- 2.0064592329945

end)

-- Anonymous function in an event handler

local Players = game:GetService("Players")

Players.PlayerAdded:Connect(function(player)

	print(player.Name .. " joined the game!")

end)

```

### [Functions in module scripts](#functions-in-module-scripts)[](#functions-in-module-scripts)

You can reuse functions across multiple scripts by storing them in [ModuleScripts](/docs/en-us/reference/engine/classes/ModuleScript) . Functions are a Luau data type, so you can store them in tables with other data.

### [Variadic functions](#variadic-functions)[](#variadic-functions)

A variadic function accepts any number of arguments. For example, Globals.LuaGlobals.print()  is a variadic function.

```

print(2, "+", 2, "=", 2 + 2) --2 + 2 = 4

print(string.format("The %s is a %s!", "cake", "lie")) -- The cake is a lie!

print(string.char(115, 101, 99, 114, 101, 116)) -- secret

```

#### [Define variadic functions](#define-variadic-functions)[](#define-variadic-functions)

To define a variadic function, you use the ...  token as the last or only parameter (not to be confused with .. , the concatenation [operator](/docs/en-us/luau/operators) ). You can put the ...  values in a table for ease of use.

The variadic token ...  can only be used within functions defined as variadic; functions or callbacks defined within a variadic function cannot  use the same ... , even if they are variadic themselves.

...  does not behave like a regular variable, and can only be passed into other functions, returned, or put into a table.

```

local function variadic(named, ...)

	local arguments = {...} -- pack the extra arguments into a table

	print("Named argument =", named)

	for i, value in arguments do

		print("Input No.", i, "=", value)

	end

end

variadic(10, "Hi", 20, "Variadic Function")

--[[ Resulting output:

Named argument = 10

Input No. 1 = Hi

Input No. 2 = 20

Input No. 3 = Variadic Function

]]

```

#### [Forward arguments](#forward-arguments)[](#forward-arguments)

You can define variadic functions as wrappers around other functions to pass, or forward, arguments from the wrapper to the other functions.

```

local function printAround(functionToPrintAround, ...)

	print("Before")

	functionToPrintAround(...)

	print("After")

end

local function addNumbers(x, y, z)

	print("x =", x)

	print("y + z =", y + z)

end

printAround(addNumbers, 1, 2, 3)

--[[ Resulting output:

Before

x = 1

y + z = 5

After

]]

```

#### [Call a variadic function with arrays](#call-a-variadic-function-with-arrays)[](#call-a-variadic-function-with-arrays)

If you want to pass a table array of values to a global variadic function, such as print() , you can use the global unpack()  function to pass the values of the table instead of the table itself.

```

local squares = {1, 4, 9, 16, 25}

print("The first 5 square numbers are:", unpack(squares))

-- The first 5 square numbers are 1 4 9 16 25

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
