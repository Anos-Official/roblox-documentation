<!-- Source: https://create.roblox.com/docs/tutorials/curriculums/coding/work-with-variables -->

Work with variables | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/tutorials/curriculums/coding/work-with-variables.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Tutorials](/docs/en-us/tutorials)

# Work with variables

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/tutorials/curriculums/coding/work-with-variables.md)

In coding, variables  are placeholder words for different types of information in your game, such as player names, a team's score, or words for a story game. In this chapter, let's explore how to open the main script for the core gameplay and add code to ask players questions and use their answers for your story.

## [Open script](#open-script)[](#open-script)

Roblox creators write their code inside of scripts  that tell Studio how and when to add custom behavior to games, such as triggering different types of events, saving player information, or spawning enemies. Roblox scripts use the [Luau](https://luau.org)  programming language, which you can learn more about later in the [Coding fundamentals](/docs/../../fundamentals/coding-1)  series.

The Story Game template uses a single script named StoryManager  to control the core gameplay of the game. This script already contains some code that's necessary for showing the full story to the player, but you will add more to display your interactive story.

To open the StoryManager  script:

1.

In the Explorer  window, click the arrow next to StarterGui  to see everything it contains. GameGui  displays.

2.

Click the arrow next to GameGui  to see everything it contains. The StoryManager  script displays at the top along with a few other things that aren't important for this lesson.

 ![](https://prod.docsiteassets.roblox.com/assets/education/story-games/StoryManager.png)

3.

Double-click the StoryManager  script. The script's code displays.

```

-- GLOBAL VARIABLES

local storyMaker = require(script:WaitForChild("StoryMaker"))

-- Code controlling the game

local playing = true

while playing do

	storyMaker:Reset()

	-- Code story between the dashes

	-- =============================================

	-- =============================================

	-- Add the story variable between the parenthesis below

	storyMaker:Write()

	-- Play again?

	playing = storyMaker:PlayAgain()

end

```

Notice how a large portion of the code uses the --  symbol, which is called a comment . Coders use comments to leave notes, and they don't change the way the script runs. For this lesson, you are going to create your code between the dashed line comments so that you can focus on creating your interactive story in one spot.

## [Ask players questions](#ask-players-questions)[](#ask-players-questions)

As a best practice, coders create variables with names that describe the type of information they store. For example, if you were working on a game where players are split into teams:

-

The team  variable stores information about the player's team .

-

The teamColor  variable stores information about the player's team color .

-

The teamScore  variable stores information for the player's team score .

Variables can store all sorts of information, such as small numbers, true or false answers, and strings. String type variables are special because they can store whole sentences, including the questions that you want to ask your players.

Using your placeholder words from the previous chapter, you can create string type variables with the same placeholder names that describe what type of word that you are going to ask the player for as they play your story game.

To create variables for your player questions:

1.

Click below the dashed line comments and create a local variable for the first word you want players to replace with their own answer. For example:

```

-- =============================================

   local name1

-- =============================================

```

2.

Set the variable using the =  symbol to the provided storyMaker:GetInput()  method that displays your questions in the giant book. You must type this method exactly as it is with its specific capitalization in order for the code to work. For example:

```

-- =============================================

   local name1 = storyMaker:GetInput()

-- =============================================

```

3.

Create a string in between the parenthesis with the question you want to ask your players. Remember, strings are always in quotation marks!

```

-- =============================================

   local name1 = storyMaker:GetInput("What is your favorite name?")

-- =============================================

```

## [Use their answers](#use-their-answers)[](#use-their-answers)

Now that you have a question that players can answer, it's time to code your story and add behavior that replaces your placeholder word with their answer.

To create variables for your story and to use player answers:

1.

Under your question, create a new variable named story. Remember, variables are lowercase!

```

-- =============================================

   local name1 = storyMaker:GetInput("What is your favorite name?")

   local story

-- =============================================

```

2.

Set your string type variable to the first sentence of your story before your first placeholder, leaving a space after the last word and before the quotation mark. If your placeholder word happens to be in the middle of a sentence, you can add the rest of the sentence in a later chapter of the tutorial.

```

-- =============================================

   local name1 = storyMaker:GetInput("What is your favorite name?")

   local story = ("In a tree on a hill lives the great wizard ")

-- =============================================

```

3.

Combine the first string of the story with the player's answer using .. . Combining things together is called concatenation .

1.

On the same line as the story  variable, add two periods.

2.

Add a space, then type the name of the variable that stores the player's first answer.

```

-- =============================================

   local name1 = storyMaker:GetInput("What is your favorite name?")

   local story = ("In a tree on a hill lives the great wizard " .. name1)

-- =============================================

```

4.

Show this first part of the story to players by calling the story variable from the provided storyMaker:Write()  method that writes your story in the giant book.

```

-- =============================================

   local name1 = storyMaker:GetInput("What is your favorite name?")

   local story = ("In a tree on a hill lives the great wizard " .. name1)

-- =============================================

-- =============================================

storyMaker:Write(story)

```

Now's a good point to stop momentarily, playtest the game in the next chapter, and make sure the story is working!

[Next](/docs/tutorials/curriculums/coding/test-and-save)[Previous](/docs/tutorials/curriculums/coding/get-started)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
