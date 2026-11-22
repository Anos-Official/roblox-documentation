<!-- Source: https://create.roblox.com/docs/en-us/tutorials/fundamentals/coding-6/coding-concept-algorithms -->

Coding concept - algorithms | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/tutorials/fundamentals/coding-6/coding-concept-algorithms.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Tutorials](/docs/en-us/tutorials)
4. /
5. [Organize code](/docs/en-us/tutorials/fundamentals/coding-6/landing)

# Coding concept - algorithms

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/tutorials/fundamentals/coding-6/coding-concept-algorithms.md)

An algorithm  uses a series of steps to determine an outcome. Steps can be a set of directions, comparisons, or even a mathematical formula.

Your daily life is full of algorithms that you use without thinking about it. They help you make decisions, create things, and solve problems.

Real life examples:

-

Checking if you have enough money to buy a snack.

-

Getting dressed in the morning.

-

Drawing stick figures.

Coding examples:

-

Checking if a skill level is high enough to use an item.

-

Sorting a list of items into alphabetical order.

-

A player standing on lava loses 5 health every second. If they reach 0, they respawn.

For an offline activity, try using this combination of art and computer science to create an algorithm that makes stick figures.

-

Have everyone draw a stick figure.

-

Have everyone write down the steps they took.

-

Pair up students and have one student direct the second student using the directions they wrote down previously.

## [Create algorithms in code](#create-algorithms-in-code)[](#create-algorithms-in-code)

In real life, we don't usually think about the algorithms we use everyday. Computers however, need algorithms to be coded step-by-step and use at least one of three methods to solve a problem or produce an outcome.

| Methodology | | Example |
| --- | --- |
| Selection  - Uses conditional statements such as if/then to determine an output. | |

```

if time == 0 then

	stopLightColor = red

end

```

 |
|

Sequencing  - A set of precise steps.

 | |

```

local function createBridge()

  create new block

  size block

  set color

  rotate

  set location

  parent to workspace

end

```

 |
|

Iteration  - Repeats parts of the code as necessary, such as in for loops or multiplication.

 | |

```

for countDown = 10, 1, -1 do

	time -= 1

	task.wait(1)

end

```

 |

## [Combine algorithms](#combine-algorithms)[](#combine-algorithms)

Much like larger problems can be broken into smaller problems, some algorithms can be broken down into a series of smaller algorithms.

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-6/coding-concept-algorithms/square-and-child-squares.png)

Think of your real-life morning time algorithm to get dressed. If that's your main algorithm, it might use one algorithm for picking out your clothes, and a second algorithm for putting clothes on.

Getting Dressed Pseudocode

```

-- First algorithm for picking clothes

local function pickClothes()

    pick top clothing

    pick bottom clothing

    pick Socks

    pick Shoes

end

-- Second algorithm for putting clothes on

local function putOnClothes()

    put on top clothing

    put on bottom clothing

    put on socks

    put on shoes

end

-- Main algorithm, calls pickClothes()and putOnClothes()

local function getDressed()

    pickClothes()

    putOnClothes()

end

```

For an optional challenge, try and figure out what are additional algorithms pickClothes()  might use?

-

Check the weather.

-

Check if clothes are clean.

-

Check if clothes match.

## [Summary](#summary)[](#summary)

Algorithms  are predefined steps that provide an outcome. In daily life, algorithms solve problems like getting dressed, going to work, or making a cake. In code, algorithms solve problems like managing websites, handling traffic congestion, or running game mechanics. To complete their goal, algorithms will often call on other algorithms.

Algorithms use three different ways to come to a conclusion; selection , iteration , and sequencing . Selection uses conditionals such as if/then statements. Iteration repeats parts of the code as necessary. Sequencing uses a series of steps to produce a result.

[Previous](/docs/en-us/tutorials/fundamentals/coding-6/coding-concept-abstraction)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
