<!-- Source: https://create.roblox.com/docs/production/game-design/onboarding-techniques -->

Onboarding techniques | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/production/game-design/onboarding-techniques.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Game design](/docs/production/game-design)
6. /
7. Build your experience

# Onboarding techniques

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/production/game-design/onboarding-techniques.md)

Onboarding techniques are strategies used to help direct players through the onboarding funnel as quickly and seamlessly as possible. Three popular onboarding techniques include:

-

Visual elements

-

Contextual tutorials

-

Timed hints

Each of these techniques can be optimized using Configs  and Experiments . For example, you can use Experiments  to A/B test whether a 5-second or 10-second delay for a timed hint leads to better funnel completion. Once you've identified the winning timing, leverage Configs  to update that value globally in real-time, allowing you to optimize your onboarding flow instantly without restarting your servers.

## [Visual elements](#visual-elements)[](#visual-elements)

Visual elements  are assets or effects that appear in a game to help players understand how to play, where to go, what to pay attention to, or what actions to take. Because of these characteristics, visual elements thrive when used in conjunction with a game's onboarding funnel.

Visual elements can be static or animated, appear within the environment, or overlay the UI. These elements are usually temporary and persist only as long as they communicate their intent to the player.

When utilized correctly, visual elements integrated with an onboarding funnel helps:

-

Improve clarity

-

Increase accessibility

-

Enhance immersion

-

Facilitate feedback

Examples of visual elements in onboarding include:

-

A bouncing arrow pointing at a button in the UI

-

Particle effects over an item of interest in the world

-

A glowing trail in the world that directs players to a destination

-

An in-world sign displaying a game's core loop.

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/visual-elements-1.png) Directional arrows and icons in * Creatures of Sonaria.*

### [Improve clarity](#improve-clarity)[](#improve-clarity)

Players who don't understand what to do in the first few minutes are likely to quit, but so are players who are bored by lengthy and prescriptive tutorials. Utilizing visual elements in onboarding funnels enables you to teach players what they need to know, while also allowing them to get to the fun quickly. When information must be communicated efficiently, visual elements are used to improve clarity in three ways:

-

Prominence

-

Highlights

-

Hints

#### [Prominence](#prominence)[](#prominence)

Prominent visuals can be harder to overlook, ignore, or misinterpret than text alone. Some games present pop-up messages with text as players make progress. Depending on factors like location, color and contrast, and how focused the player is on what they're doing in the game, those text prompts can be easily overlooked. If players don't notice them, they are of no benefit. Placing visual elements in the world, where players encounter them as they are playing, is one solution to this problem.

In * Color or Die* , a sign explaining the game's core survival mechanic is placed directly in players' line of sight as they collect their first paint bucket to begin playing. It's impossible to miss, but doesn't prevent the player from starting the game.

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/visual-elements-2.png) Prominent visual element in * Color or Die.*

This technique is an efficient way of explaining the core mechanic of a game quickly and clearly. Compare the visual element to what this same information could look like as text:

When the monster approaches, stand against a wall that's the same color as your avatar. The monster will be confused and unable to see you. If you stand against a wall of a different color, it will notice you and you will be in danger.

Players generally don't like to read instructions and skip through text prompts to get to gameplay. Presenting instructions visually with as few clicks or taps as possible prepares those impatient players better than any amount of text that they would refuse to read.

#### [Highlights](#highlights)[](#highlights)

Highlighting something that players should look at is more effective than describing it in text. The more text a player is asked to read, the more likely they are to misinterpret or forget the information. Well-designed visuals can be harder to misunderstand and easier to retain due to requiring less interpretation.

Consider the following sentence:

Open your inventory by clicking on the backpack  button.

This requires players to interpret a backpack  button and then search for it in the UI. Instead, consider the impact of having an arrow point at the button telling them exactly where they need to click.

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/visual-elements-3.png) Highlights in * Hello Kitty Cafe.*

In this example from * Hello Kitty Cafe* , the desired button is spotlighted while the rest of the screen is dimmed. A pink outline highlights the button and an arrow points at it. There is no mistaking what the player is expected to click next.

#### [Hints](#hints)[](#hints)

Visual hints can keep players on track. New players don't always know what's important to pay attention to and are excited to explore. Persistent visual elements that stay on-screen until the player has completed a step of the tutorial helps keep players from being distracted by other gameplay mechanics, the environment, or UI. Even if they choose to explore, the hints remain to guide them when they are ready to return.

Visual elements are not limited to telling players where to go or what to click. They can also imply functionality, such as alerting players that items in the world can be interacted with.

In Jailbreak, players are not told explicitly what to do in order to escape the prison, but visual hints in the world grab their attention and imply interactivity. Without these hints, new players might struggle to locate escape routes. Visual hints provide just enough information to allow players to solve the problem themselves, and feel clever for figuring it out.

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/visual-elements-4.png) Footprints hint at a possible escape route in * Jailbreak.*

When considering implementing hints into your onboarding funnel, be intentional in determining who will see them and when they appear. For more on utilizing hints, see [Timed hints](#timed-hints) .

### [Increase accessibility](#increase-accessibility)[](#increase-accessibility)

Visual elements are more broadly accessible than text. Visuals like arrows and particle effects communicate without words and don't require translation to be understood by a global audience. This helps players who rely on localization into other languages, as well as UI designers who don't have to worry about a text string getting longer after translation.

For games that appeal to younger players, teaching without words can help those that are still learning to read or who don't have the vocabulary to understand descriptions of more complex systems.

Using visual elements also ensures accessibility on various platforms, such as mobile devices, where text can be too small to read comfortably. Visual elements are also easier to interpret, especially for players who are visually impaired.

For more information about designing accessible visual elements, see this video on [color contrast](https://www.youtube.com/watch?v=syQcaeRqqc4) .

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/visual-elements-5.png) Directional arrows in * Winds of Fortune.*

### [Enhance immersion](#enhance-immersion)[](#enhance-immersion)

Visual elements can help players stay immersed in gameplay. Directional trails, for example, provide direction while allowing players the freedom to explore and make other choices. They strongly suggest an action, but don't require it. While most players will follow the directions, the availability of choice makes the tutorial feel less forced than if they had no other options, and allows players to stay immersed in the game and explore at their own pace.

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/visual-elements-6.png) Directional trail in * Hello Kitty Cafe.*

### [Facilitate feedback](#facilitate-feedback)[](#facilitate-feedback)

Visual elements can be used as feedback outside of tutorials and onboarding funnels. Feedback occurs when a player takes an action and the game responds in a way that communicates the results of the action. Visual elements can be used to communicate feedback and provide players with actionable information to help them make their next choice.

As an example, when players are in combat in * Winds of Fortune* :

-

VFX flashes indicate that the player's sword swings have hit their target

-

Red numbers fly off an enemy when they are hit, indicating damage points

-

A red screen effect throbs, alerting the player that their health is getting low

-

Health meters update for the player and enemy

-

When an enemy is defeated, coins fly out to let the player know that they have received rewards

-

If defeating the enemy is a quest objective, the counter updates when the enemy dies

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/visual-elements-7.png) Visual Feedback in * Winds of Fortune.*

All of this feedback tells players when they have successfully hit the enemy, when they have taken damage themselves, what rewards they receive from victory, and whether they've made progress on their quest. The combination of these visual elements ensures most players understand what's happening without a needing more explicit combat tutorial.

Anytime a player takes an action in a game, it's imperative to provide clear feedback. Otherwise, players may not know that the action they took did anything, and wonder if they did something wrong, or wonder if the game is buggy.

For more information about feedback and other User Experience (UX) best practices, see [UI and UX](/docs/production/game-design/ui-ux-design)

## [Contextual tutorials](#contextual-tutorials)[](#contextual-tutorials)

Also known as just in time  tutorials, contextual tutorials  are tutorials triggered by normal play, such as entering a new map zone or picking up a new weapon. By waiting for players to engage naturally, contextual tutorials personalize instruction, which maximizes their relevance and utility within the broader onboarding funnel. Contextual tutorials facilitate:

-

Increased learning retention:  Players learn best by understanding the context of a situation and by interacting with tutorials that are triggered by their first interaction with a game feature. When players practice actions while learning them, they retain knowledge better.

-

Faster onboarding:  It's important to lead players to the enjoyable parts of a game quickly to keep them engaged.Contextual tutorials allow designers to avoid lengthy onboarding systems and delay unneeded tutorials, enabling players to begin having fun more quickly.

-

Reduced cognitive load:  In the first few minutes of a game, new players often must learn many things like interactions, mechanics, and goals. The more they have to learn, the harder it becomes to retain it all, increasing the likelihood of feeling overwhelmed and quitting. Delaying non-essential information to future sessions reduces what they must learn and remember in the first session, allowing them to focus on the essentials.

Traditional tutorial flows guide players in a fixed sequence through a game's features, ensuring that they learn essential skills and knowledge. While this method can be effective for high level concepts, it can lead to boredom or frustration due to restricting player choice. Contextual tutorials enhance the game by holding off on less crucial instructions and quickly handing control to the player, by only providing specific instructions to the relevant players.

### [Use cases](#use-cases)[](#use-cases)

In [* Squishmallows*](https://www.roblox.com/games/7941853407/) , contextual tutorials are used to effectively teach players how and when to use the combination station. When a player has two identical Squishmallows in their inventory, a contextual tutorial triggers, and shows players how to combine three * Squishmallows*  at the combination station in order to create a larger one.

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/contextual-tutorial-1.png) Contextual combination station tutorial in * Squishmallows* .

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/contextual-tutorial-2.png) Contextual combination station tutorial in * Squishmallows* .

If the developers included this tutorial in the onboarding experience, it would make it too long and irrelevant, and players may forget the information before they can use it. Presenting the tutorial when players have the required * Squishmallows*  encourages immediate action at the combination station, and helps players remember the process for future use.

Contextual tutorials also teach non-core concepts, letting players learn about these features by themselves. In * Squishmallows* , these tutorials explain the marketplace where players sell Squishmallows to each other for in-game currency. Since the marketplace mainly serves mid and late-game players trading rare or high-level Squishmallows, the developers introduce new players to the marketplace through contextual tutorials when they find it on their own.

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/contextual-tutorial-3.png) Contextual market tutorial in * Squishmallows* .

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/contextual-tutorial-4.png) Contextual market tutorial in * Squishmallows* .

## [Timed Hints](#timed-hints)[](#timed-hints)

Timed hints  are tutorial elements that appear to struggling players after a predetermined period of time to help them progress through the onboarding funnel as quickly and seamlessly as possible. Players who need additional help can often be identified by timing how long it takes them to follow instructions or complete tasks.

In addition to helping players through the onboarding tutorial, showing timely hints to players can also:

-

Increase retention:  Timed hints can increase the number of new players retained by a game by ensuring that struggling players get the extra help they need to succeed and have fun. New players needing additional help at first can become dedicated players in the future if they receive appropriate and well timed support.

-

Improve player agency:  Timed hints allow designers to create less structured tutorial sequences and add additional layers of assistance specifically for those who need it. This avoids annoying experienced players while giving newer players the opportunity to figure things out for themselves. Players who figure things out on their own tend to feel more successful and empowered, which helps them complete tutorials quickly and get to the fun faster.

-

Surface overlooked features:  Timed hints can also be used to draw attention to features in a game that weren't core enough to be included in onboarding, but are still worth surfacing. For example, if a player hasn't engaged with a game's trade feature in their first two sessions, highlighting the trade button in the UI would encourage them to click on it and experience the feature for the first time.

When deciding how and when to use timed hints, observing playtesters can provide valuable information about where such hints are needed and how long to wait before displaying them. Try to find a balance between displaying them so quickly that players feel that they haven't gotten the chance to figure it out on their own, and waiting so long that they get frustrated.

### [Use cases](#use-cases-1)[](#use-cases-1)

In [Plant](https://create.roblox.com/docs/resources/plant-reference-project) , players follow a simple loop of planting seeds, selling produce, and investing currency into larger pots and more valuable plants. A great candidate for timed hint utilization is in the UI when planting seeds. In order to plant a seed, players have to select the PLANT CABBAGE SEED  button.

While most players will have little trouble figuring out what to do, there's a chance that some players might get stuck. In this hypothetical situation, playtesting results determine that most players find and press the button within 10 seconds. Adding a highlight to the button at 11 seconds would give those remaining players the hint that they may need to continue, without annoying the majority of players who don't need it.

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/timed-hints-1.png) Timed hint opportunity in * Plant* .

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/timed-hints-2.png) Timed hint application in * Plant* .

Another potential place for a timed hint is during the player's first selling opportunity. After harvesting lettuce from their first few plants, players can take their wagon to one of three marketplace stands in order to sell their yield and gain the currency needed for upgrades.

Players may be confused about which marketplace to visit to complete the objective. To alleviate this, an arrow could be placed over the correct stall after players have had some time to explore.

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/timed-hints-3.png) Timed hint opportunity in * Plant* .

![](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding-techniques/timed-hints-4.png) Timed hint application in * Plant* .

In both hypothetical examples, the timed hints only appear after the majority of players have completed the objective, and only appear the first time the task is presented. Timed hints should be sufficient to help struggling players after only being shown once, and only be shown to those who need it.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
