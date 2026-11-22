<!-- Source: https://create.roblox.com/docs/en-us/production/game-design/contextual-purchases -->

Contextual purchases | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/production/game-design/contextual-purchases.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Game design](/docs/en-us/production/game-design)
6. /
7. Monetize your experience

# Contextual purchases

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/production/game-design/contextual-purchases.md)

Contextual purchases  are strategic events that occur outside an experience's [shop](https://create.roblox.com/docs/production/game-design/monetization-foundations)  that prompt players to purchase items. Contextual purchases are designed opportunistically, operating under a "right item, right time" framework, where designers anticipate the wants of their players at key stages of the experience and provide a purchasable solution.

Approaches to contextual purchases can be divided into the following categories:

-

In-play

-

Pre-play

-

Lobby

-

Complementary

-

UI

## [In-play](#in-play)[](#in-play)

In-play  contextual purchases refer to presenting a purchase opportunity when a player is actively participating in an in-experience activity. Carefully consider the timing of any in-play contextual purchases to avoid negatively impacting a player's session.

[Dress to Impress](https://www.roblox.com/games/15101393044/Dress-To-Impress)  does this by offering players a purchase opportunity during the intermission between rounds. During this time, players can choose to spend Theme Props, which are purchasable in the dialog, to select the theme for the next round.

![](https://prod.docsiteassets.roblox.com/assets/game-design/contextual-purchases/contextual-purchases-DTI2.png) In-play contextual purchase opportunity in Dress to Impress.

![](https://prod.docsiteassets.roblox.com/assets/game-design/contextual-purchases/contextual-purchases-DTI.png) "Buy Robux" purchase flow.

This approach mimics the "continue countdown" option used by traditional arcade games. Make sure that your in-play contextual purchase opportunities account for players having time to finish the entire "buy Robux" purchase flow, which can take several seconds to complete. If it isn't feasible to design gameplay pauses to accommodate these transactions taking place, in-play contextual purchases might not be appropriate for your experience.

## [Pre-play](#pre-play)[](#pre-play)

Pre-play  contextual purchases refer to presenting a purchase opportunity when a player is waiting to participate in an in-experience activity. This often occurs in instance-based experiences where gameplay occurs in isolated and repeated loops.

[Doors](https://www.roblox.com/games/6516141723/DOORS)  does this well by presenting players with pre-play contextual purchase opportunity before each round in the Pre-Run Shop. In * Doors* , the shop in the lobby only sells Knobs, the in-game currency, explicitly telling players that it's "used to purchase items before each run".

Before each run, after exiting the lobby, players enter an elevator, where they're presented with an opportunity to spend their Knobs on consumable items that will aid them in the coming instance of gameplay. The Pre-Run Shop clearly states the benefits of each item, and is intentionally placed to provide a convenient and focused pre-play contextual purchase experience.

![](https://prod.docsiteassets.roblox.com/assets/game-design/contextual-purchases/contextual-purchases-3.png)* Doors*  Lobby shop

![](https://prod.docsiteassets.roblox.com/assets/game-design/contextual-purchases/contextual-purchases-4.png) Pre-play contextual purchase opportunity

## [Lobby](#lobby)[](#lobby)

Lobby  contextual purchases advertise wares, sales and store related events on 3D objects in the experience's lobby. This technique can be seen in [Super Striker League](https://www.roblox.com/games/3360853050/Super-Striker-League) .

![](https://prod.docsiteassets.roblox.com/assets/game-design/contextual-purchases/contextual-purchases-5.png)* Super Striker League*  Lobby.

If utilizing lobby contextual purchases in your experience, ensure your players understand whether the items displayed in the 3D object are all of the items available for purchase. If additional items are available for purchase elsewhere, consider having the lobby contextual purchase interaction open up the main shop of the experience.

![](https://prod.docsiteassets.roblox.com/assets/game-design/contextual-purchases/contextual-purchases-6.png) Lobby contextual purchase opportunity.

![](https://prod.docsiteassets.roblox.com/assets/game-design/contextual-purchases/contextual-purchases-7.png) Full * Super Striker League*  shop.

## [Complementary](#complementary)[](#complementary)

Complementary  contextual purchases are opportunities for players to purchase multiple items that have related effects. In [Bee Swarm Simulator](https://www.roblox.com/games/1537690962/Bee-Swarm-Simulator) , players collect pollen to convert into honey. The store sells a Bee Pollen Pass, which enables players to collect twice the normal amount of pollen, and offers a Honey Speed Pass right below it, which enables players to convert pollen into honey at twice the rate.

![](https://prod.docsiteassets.roblox.com/assets/game-design/contextual-purchases/contextual-purchases-8.png)* Bee Swarm Simulator*  shop.

A complementary contextual purchase opportunity would be to prompt the player to also purchase the other pass they didn't initially choose, due to the passes' complementary nature. Communicating the complementary nature of two or more items in a shop can also be helpful for newer players learning about the experience.

Be thoughtful about how many sales prompts you decide to use. Using this strategy for every possible complementary item might distract from players' browsing experience and from their immersion in the environment. To alleviate the risk of overusing complementary messaging, consider packaging some of the items together in a bundle.

## [UI](#ui)[](#ui)

Contextual cues in the UI  can take a variety of forms and can be versatile tools in recommending purchases. Common UI purchase opportunities are communicated through badges, event windows, and announcements.

![](https://prod.docsiteassets.roblox.com/assets/game-design/contextual-purchases/contextual-purchases-9.png) UI shop badge in * BotClash Simulator* .

Loading screens offer prominent space to display a purchase opportunity when players' attention is focused and not yet distracted by other UI elements or gameplay. If you choose to use a space like this for purchase offers, make sure you also provide sufficient context for the player to properly gauge the value of the item. It wouldn't be appropriate to have a starter pack appear on the loading screen the very first time a player loads the experience, but it could be become appropriate in future sessions.

![](https://prod.docsiteassets.roblox.com/assets/game-design/contextual-purchases/contextual-purchases-12.png) Loading screen purchase opportunity in * Adopt Me* .

A basic modal offer is also commonly used to promote items and features. In * Adopt Me* , the player is offered a Modern Mansion when looking around their basic house after starting their play session. When using modals like these, be sure to implement logic that prevents multiple modals from layering on top of each other so your UI remains clear and effective.

![](https://prod.docsiteassets.roblox.com/assets/game-design/contextual-purchases/contextual-purchases-13.png) Modal offer in * Adopt Me* .

For more about UI and UX design, see [UI and UX](/docs/en-us/production/game-design/ui-ux-design) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
