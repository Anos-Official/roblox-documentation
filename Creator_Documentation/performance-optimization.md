<!-- Source: https://create.roblox.com/docs/en-us/performance-optimization -->

Performance optimization | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/performance-optimization.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Performance optimization](/docs/en-us/performance-optimization)

# Performance optimization

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/performance-optimization/index.md)

Performance optimization is the process of building and iterating on a game to improve frame rate, memory usage, and load times. Players expect games to perform well, so taking the time to understand and improve your game's performance can be critical to its success.

The first step in performance optimization is to [design for performance](/docs/en-us/performance-optimization/design) , which means following a set of best practices as you build  a new game. After you publish a game, the optimization process follows a common cycle:

1.

[Identify performance Issues](/docs/en-us/performance-optimization/identify)  - Use Roblox's built-in tools to find performance problems and identify root causes.

2.

[Improve performance](/docs/en-us/performance-optimization/improve)  - After you find an issue, see if it's a common one and how you might mitigate it. You might also want to take proactive action.

3.

[Monitor performance](/docs/en-us/performance-optimization/monitor)  - Use analytics tools to monitor the impact of your changes and watch for indicators of any performance issues.

![A diagram showing the flow from designing, identifying, improving, and monitoring performance.](https://prod.docsiteassets.roblox.com/assets/optimization/Perf-Flow.png)

## [Why performance matters](#why-performance-matters)[](#why-performance-matters)

To put it simply, performant games are more fun. When a game has a consistent, smooth frame rate, even basic actions like running and jumping feel more precise and enjoyable. Aiming can go from feeling impossible to feeling completely natural. A game with a small memory footprint and fast load times might always have plenty of other people to play with.

Performance optimization also lets you expand your ambitions. If your game runs well, you might be able to make it more expansive or beautiful or add new systems to it.

From a business perspective, performant games often have higher user engagement, better user retention, and make more money.

## [Measure performance](#measure-performance)[](#measure-performance)

-

Frame rate  is the number of unique frames that the client presents to the user, measured in frames per second (FPS). The cause of low frame rates is typically expensive computational operations—in other words, overtaxing the CPU, GPU, or both.

Because the server doesn't render frames, it doesn't * technically*  have a frame rate, but server heartbeat is essentially the same thing: the number of times per second that the server updates its simulation of the world. A low server heartbeat reduces the frame rate for all clients and increases latency.

On the client, low or inconsistent frame rates reduce the smoothness and responsiveness of the game. By default, Roblox games target 60 FPS, which is one frame every 16.67 milliseconds with proper frame pacing.

-

Memory usage  is the amount of RAM or swap that your game uses. Even if a game has low starting memory usage, memory leaks can cause that amount to increase over time.

On the server, excessive memory usage can cause crashes, which disconnect all players from the game.

Excessive memory usage causes client crashes, too, but it also prevents users on lower-end devices from playing your game in the first place. Reducing memory usage can greatly expand your addressable audience, especially on mobile.

-

Join time  is the total time from when a player clicks the play button to when the world is rendered and they can move.

Long join times hurt user acquisition and retention—players may leave before ever entering your experience.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
