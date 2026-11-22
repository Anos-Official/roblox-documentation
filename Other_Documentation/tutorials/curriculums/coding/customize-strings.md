<!-- Source: https://create.roblox.com/docs/tutorials/curriculums/coding/customize-strings -->

Customize strings | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/tutorials/curriculums/coding/customize-strings.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Tutorials](/docs/en-us/tutorials)

# Customize strings

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/tutorials/curriculums/coding/customize-strings.md)

With the first sentence of your story done and working in Studio, it's time to customize your string with punctuation and line breaks. Once you are happy with how it looks and reads to players, you can add more sentences and finish the rest of your story.

## [Add punctuation](#add-punctuation)[](#add-punctuation)

When you playtest your game, your first sentence doesn't include any punctuation to let players know the sentence is complete. To fix this, you can add another string using the same process of concatenation to connect your words with your punctuation.

To add punctuation:

1.

On the same line as the story  variable, type two periods.

2.

Add another string with a punctuation mark, such as a period or exclamation point, then an extra space so your next sentence doesn't start immediately after the punctuation mark.

```

-- =============================================

   local name1 = storyMaker:GetInput("What is your favorite name?")

   local story = ("In a tree on a hill lives the great wizard " .. name1 .. "! ")

-- =============================================

-- =============================================

storyMaker:Write(story)

```

## [Add line breaks](#add-line-breaks)[](#add-line-breaks)

A line break moves the cursor to the next line of text. This is helpful when you want every sentence to start from the left-side of the page, and enhance your story's readability in the giant book.

To add a line break:

1.

On the same line as the story  variable, type \n .

```

-- =============================================

   local name1 = storyMaker:GetInput("What is your favorite name?")

   local story = ("In a tree on a hill lives the great wizard " .. name1 .. "! \n")

-- =============================================

-- =============================================

storyMaker:Write(story)

```

2.

OPTIONAL

 You can add more than one line break by adding as many \n  as you need. For example, the following code sample adds in three line breaks.

```

-- =============================================

   local name1 = storyMaker:GetInput("What is your favorite name?")

   local story = ("In a tree on a hill lives the great wizard " .. name1 .. "! \n\n\n")

-- =============================================

-- =============================================

storyMaker:Write(story)

```

## [Add more sentences](#add-more-sentences)[](#add-more-sentences)

Now that your first sentence includes punctation and any applicable line breaks, you can add more sentences to your story and ask players more questions for your placeholder words.

To add more sentences:

1.

Under your first variable, create a new variable for your second placeholder and ask a question related to what type of placeholder word it is. For example:

```

-- =============================================

   local name1 = storyMaker:GetInput("What is your favorite name?")

   local food1

   local story = ("In a tree on a hill lives the great wizard " .. name1 .. "! \n\n\n")

-- =============================================

-- =============================================

storyMaker:Write(story)

```

2.

Using the same process as your first variable, set the variable and use the provided storyMaker:GetInput()  method that displays your questions in the giant book. For example:

```

-- =============================================

   local name1 = storyMaker:GetInput("What is your favorite name?")

   local food1 = storyMaker:GetInput("What do you like to eat?")

   local story = ("In a tree on a hill lives the great wizard " .. name1 .. "! \n\n\n")

-- =============================================

-- =============================================

storyMaker:Write(story)

```

3.

Combine the first string of the story with the player's answer using .. .

1.

On the same line as the story  variable, add two periods.

2.

Add a space, then type the name of the variable that stores the player's second answer.

3.

Add two more periods, then finish the sentence with a punctuation mark.

```

-- =============================================

   local name1 = storyMaker:GetInput("What is your favorite name?")

   local food1 = storyMaker:GetInput("What do you like to eat?")

   local story = ("In a tree on a hill lives the great wizard " .. name1 .. "! \n\n\n" .. "Every morning, the wizard loves eating a giant bowl of honey roasted " .. food1 .. ". ")

-- =============================================

-- =============================================

storyMaker:Write(story)

```

4.

Repeat this process for your entire story, then playtest your game using the steps from the previous chapter to make sure your code works properly.

[Next](/docs/tutorials/curriculums/coding/next-steps)[Previous](/docs/tutorials/curriculums/coding/test-and-save)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
