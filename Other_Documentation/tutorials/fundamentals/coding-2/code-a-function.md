<!-- Source: https://create.roblox.com/docs/tutorials/fundamentals/coding-2/code-a-function -->

Code a function | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/tutorials/fundamentals/coding-2/code-a-function.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Tutorials](/docs/en-us/tutorials)
4. /
5. [Functions and events](/docs/tutorials/fundamentals/coding-2/functions-and-events)

# Code a function

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/tutorials/fundamentals/coding-2/code-a-function.md)

Functions  are sets of instructions that can be used many times in a script. There are pre-made functions (also called methods) like print()  and [task.wait()](/docs/reference/engine/libraries/task#wait)  that are built into most programming languages. Coders can also create their own custom functions for code they want to use more than once, but don't feel like writing over and over. In Luau, this is done by typing: local function nameOfTheFunction()

Functions can be thought of like a recipe. They're both lists of specific instructions. For example, you could use a function to teach a robot how to make spaghetti. First, make a local function  that lists the steps to prep the meal. Then, whenever you want dinner, just say, "Robot, run makeSpaghetti()".

The steps to make dinner might look like this:

1.

Boil water

2.

Add pasta

3.

Cook 15 minutes

4.

Add sauce

5.

Serve on a plate

While the code version might look like something like this:

## [Create a function](#create-a-function)[](#create-a-function)

To practice, your first function will print your favorite food in the Output window. First set up the script you're going to use, if you don't remember how, here's a reminder:

1.

Create a new script in ServerScriptService .

2.

Rename the script * FunctionsPractice* .

3.

Delete "Hello World" .

4.

Add comment at the top. For example: -- Prints your favorite food

Next, you create and name the function. All functions should have names that help you remember what their purpose is. Functions names are camelCased, with the first letter lowercase and next words capitalized.

Examples: addPoints() , restartGame() , rainFlamingLlamas()

-

Type local function printFood() , then press Enter  on your keyboard. It should autocomplete the function to look like:

```

local function printFood()

end

```

Type end  yourself if the code doesn't autocomplete for some reason. If the function doesn't have an end , your code won't run.

### [Add code to functions](#add-code-to-functions)[](#add-code-to-functions)

All of the code for your function has to be typed between the lines local function printFood()  and end . Any code not between those two points won't run when the function does.

```

local function printFood()

	-- Code here runs when the function is called

end

-- Code here will not run

```

Information that is inside the function, or can be used by the function, is in scope .

-

Between local function printFood()  and end , use print()  to state your favorite food.

```

local function printFood()

	print("Curry!")

end

```

As you typed, your code should have indented automatically. This makes it easier for you and others to see the start and end of a function. If it didn't auto indent, you can press Tab  at the beginning of the line to quickly indent it.

### [Tell the function to run](#tell-the-function-to-run)[](#tell-the-function-to-run)

There's one more thing we need to do before the function will work, and that's to tell it to run, also known as calling  a function. Functions won't run until they are called. To call a function, type the function's name including the () .

1.

Under end , type printFood() .

2.

Test the code. Your favorite food should appear in the [Output](/docs/studio/output)  window.

### [Troubleshooting tips](#troubleshooting-tips)[](#troubleshooting-tips)

If your code doesn't run, check for errors such as the following:

-

Check that print("Your Food Here")  is between local function printFood()  and end .

-

Make sure that your food is a string, with quotations on "each side" .

-

Check that the function is called after it's been created. printFood()  should be below end .

[Next](/docs/tutorials/fundamentals/coding-2/use-parameters-and-events)[Previous](/docs/tutorials/fundamentals/coding-1/parents-and-children)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
