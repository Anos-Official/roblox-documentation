<!-- Source: https://create.roblox.com/docs/en-us/matchmaking -->

Matchmaking | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/matchmaking.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Matchmaking](/docs/en-us/matchmaking)

# Matchmaking

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/matchmaking/index.md)

Matchmaking is the process of matching players to servers based on player characteristics like age, language, skill level, and other gameplay preferences.

## [How matchmaking works](#how-matchmaking-works)[](#how-matchmaking-works)

When a player tries to join your game, the matchmaking service finds all eligible servers that the player can join, scores these servers using signals, and matches the player to the server with the highest score.

The matchmaking flow works like this:

1.

A player requests to join a place.

2.

Matchmaking finds eligible servers that the player can join, filtering out servers that are full, private, reserved, or about to be shut down.

3.

Matchmaking scores all eligible servers to determine the most compatible server for the player.

4.

Matchmaking matches the player to the server with the highest score.

5.

The player joins the winning server.

 Roblox default matchmaking  ![The default Roblox matchmaking flow.](https://prod.docsiteassets.roblox.com/assets/matchmaking/Default_Matchmaking.png)  Custom matchmaking  ![The custom matchmaking flow.](https://prod.docsiteassets.roblox.com/assets/matchmaking/Custom_Matchmaking.png)

## [Scoring](#scoring)[](#scoring)

The matchmaking scoring algorithm uses the weighted sum (WS) of signal values to assign scores to servers.

For more information on scoring, see [Server scoring](/docs/en-us/matchmaking/scoring) .

## [Attributes](#attributes)[](#attributes)

Attributes are properties used in matchmaking scoring. An attribute can be a number, like a player's age and skill level rating, or a string, like a player's language.

Attributes can be numerical or categorical:

-

Numerical attributes  compare the difference between the joining player's attribute and the server's aggregated value, with larger differences lowering or increasing the score. For example, the closer the skill level of a player is to the average skill level of the server, the higher the numerical signal's score is. This score is then multiplied by the signal's weight.

-

Categorical attributes  are based on how common the joining player's attribute is when compared to the other players in the server. For example, if a high percentage of the players inside a server have the same preferred language as the joining player, the score increases. This score is then also multiplied by the signal's weight.

For a list of all existing attributes, see [Existing attributes](/docs/en-us/matchmaking/attributes-and-signals#existing-attributes) . For more information about custom attributes, see [Custom attributes](/docs/en-us/matchmaking/attributes-and-signals#custom-attributes) .

## [Signals](#signals)[](#signals)

Signals used in server scoring can either be the default ones already provided by Roblox, or custom ones you create yourself.

Roblox signals use existing attributes that Roblox already has access to, like player location, age group, and latency. Custom signals, however, need to use custom attributes to access data from your data stores. In order to create a custom signal, you must first create a custom attribute.

For a list of all existing Roblox signals, see [Existing signals](/docs/en-us/matchmaking/attributes-and-signals#existing-signals) . For more information about custom signals, see [Custom signals](/docs/en-us/matchmaking/attributes-and-signals#custom-signals) .

## [Custom matchmaking](#custom-matchmaking)[](#custom-matchmaking)

When a player joins your game, matchmaking assigns a score to each running server based on the weighted sum of the server's signal values. You can customize this process by adjusting the weight of each of your signals to change how much each signal matters in the scoring of servers. Increasing the weight of the latency signal, for example, means the matchmaking algorithm prioritizes servers with lower ping for smoother gameplay.

After adjusting signal weights, you can preview the impact of these new weights on matchmaking server selection by evaluating them on mock servers.

For more information about how to customize matchmaking and simulate the results, see [Customize your matchmaking configuration](/docs/en-us/matchmaking/customize-matchmaking) .

## [Analytics](#analytics)[](#analytics)

Matchmaking analytics helps you track the success of your matchmaking configurations and find opportunities to optimize them.

For more information about matchmaking analytics, see [Analytics](/docs/en-us/matchmaking/analytics) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
