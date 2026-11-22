<!-- Source: https://create.roblox.com/docs/tutorials/fundamentals/coding-6/coding-concept-abstraction -->

Coding concept - abstraction | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/tutorials/fundamentals/coding-6/coding-concept-abstraction.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Tutorials](/docs/en-us/tutorials)
4. /
5. [Organize code](/docs/tutorials/fundamentals/coding-6/landing)

# Coding concept - abstraction

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/tutorials/fundamentals/coding-6/coding-concept-abstraction.md)

Abstractions  in computer science provide a simplified representation of something larger. They pull out only the most necessary information and hide everything else.

Functions  are reusable abstractions. When called, users get the benefits of the function without having to rewrite or even look at the code for the entire function.

A common example in coding languages is print() . Most of its code is hidden, so the coder can focus on what needs to be printed and not the rest of the code.

## [Why create abstractions](#why-create-abstractions)[](#why-create-abstractions)

Abstractions keeps programs organized, reduces complexity, and makes code easier to update.

### [Shop example](#shop-example)[](#shop-example)

Say that you have an in-game shop that sells just two different backpacks. The code for the second backpack was copied with slight changes, such as a different name and selling price.

![](https://prod.docsiteassets.roblox.com/assets/education/coding-6/coding-concept-abstraction/backpack-yellow.png) Yellow Backpack - 10 Robux

![](https://prod.docsiteassets.roblox.com/assets/education/coding-6/coding-concept-abstraction/backpack-violet.png) Violet Backpack - 25 Robux

Here, the code is not  abstracted. Each backpack has a script of its own. What would happen if you tried to add the following?

-

20 more backpacks.

-

The ability for some bags to hold more items than other bags.

-

A holiday sale, 25% off all backpacks.

## [Design abstractions](#design-abstractions)[](#design-abstractions)

Having separate backpack scripts makes adding and updating backpacks time consuming. Instead, create an abstraction so you don't have to make updates in so many different places.

To design an abstraction decide:

-

Which parts of the code will be reused.

-

What elements will be different each time.

The abstraction should pull out the information that changes, and hide the rest. In the backpack example, the differences are the backpack's name, price, and number of items it can carry. So an example of an abstraction, you can design is a function that takes in the backpack's name and returns it's price and capacity.

| ![](https://prod.docsiteassets.roblox.com/assets/education/coding-6/coding-concept-abstraction/no-abstraction-backpacks.png) | | ![](https://prod.docsiteassets.roblox.com/assets/education/coding-6/coding-concept-abstraction/abstraction-backpacks.png) |
| --- | --- |
|

No Abstraction

 | |

Abstraction

 |
|

Four different backpacks, four different places to update.

 | |

Use a function to search a table for unique information. Only one place to update.

 |

Check for Understanding - Using Abstractions

 What are other game mechanics you can create abstractions for?

Possible Examples

-

Trap parts - Allowing for different harm values

-

Creating a function for awarding random power-ups

-

Creating character classes

## [Summary](#summary)[](#summary)

Abstractions  provide a simplified representation of something larger by leaving out details. When deciding whether to create an abstraction, look for code that is often reused but with small changes each time. For example, a generic item like a backpack can be abstracted to a reusable function that looks up price and capacity.

Taking time to plan and structure code with abstractions helps coders focus on what's important. This investment in time keeps programs better organized and makes updating them easier.

Galactic Speedway - The Settings script has only the variables for unique features of the driftspeeder. The rest of the code is hidden. This allows students new to coding to stay focused without getting lost.

Story Game Creator Challenge - Students call getInput()  from the StoryMaker module script to create questions for players to answer. Students can practice typing strings and ask as many questions as they like, but don't need to see the code in the StoryMaker module.

[Next](/docs/tutorials/fundamentals/coding-6/coding-concept-algorithms)[Previous](/docs/tutorials/fundamentals/coding-6/create-with-module-scripts)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
