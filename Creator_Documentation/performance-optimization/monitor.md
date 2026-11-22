<!-- Source: https://create.roblox.com/docs/en-us/performance-optimization/monitor -->

Monitor performance | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/performance-optimization/monitor.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Performance optimization](/docs/en-us/performance-optimization)

# Monitor performance

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/performance-optimization/monitor.md)

The [Performance Dashboard](/docs/en-us/production/analytics/performance)  is the best way to monitor the performance of your published games. The two tabs include real-time performance information for both clients and servers, and you can use date ranges to track the impact of your changes over time.

For example, imagine you've just added a new place to your game:

1.

You publish the updated game, and hours later, you notice a distinct uptick in client crash rate on the Performance Dashboard that seems to correlate with client memory usage.

2.

You test the new place in Studio and don't see any issues. Memory usage seems similar to other places in your game.

3.

You note that average player session time has increased dramatically since your update.

4.

You test again, but this time, you spend more time in the game and keep a closer eye on memory usage over time. Sure enough, usage is growing over time and could cause crashes on lower-end devices.

5.

You check the server tab and notice that server memory usage is growing over time, too. It's not a problem yet, but could become a problem soon.

6.

Under the Memory  tab of the Developer Console, in the PlaceScriptMemory  breakdown, you notice that the memory usage for one of your new scripts grows each time you interact with some key objects in the world. The script runs on both the client and the server.

7.

You check the script, which adds some user data to a large table, but never cleans the data up—it's growing infinitely.

8.

You fix the problem, publish the updated game, and client crash rate returns to its previous value.

In addition to the Performance Dashboard, you can connect to the [DataModel.ServerLowMemoryWarning](/docs/en-us/reference/engine/classes/DataModel#ServerLowMemoryWarning)  signal from a server script to get an early warning when a live server's memory usage grows too high, giving your code a chance to free up memory before a crash occurs.

Comparing the Performance Dashboard to other dashboards can help you correlate performance improvements (or regressions) to business metrics for a more complete idea of how a performant game impacts your bottom line. For more information, see [Analytics](/docs/en-us/production/analytics) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
