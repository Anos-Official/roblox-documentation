<!-- Source: https://create.roblox.com/docs/en-us/performance-optimization/microprofiler/modes -->

MicroProfiler modes | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/performance-optimization/microprofiler/modes.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Performance optimization](/docs/en-us/performance-optimization)
6. /
7. [MicroProfiler](/docs/en-us/performance-optimization/microprofiler)

# MicroProfiler modes

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/performance-optimization/microprofiler/modes.md)

The MicroProfiler includes several modes, which can help you visualize your game's performance characteristics in different ways. After opening the MicroProfiler, use the Modes  menu to switch between them.

Frame mode  and detailed mode  are covered under [MicroProfiler basics](/docs/en-us/performance-optimization/microprofiler#microprofiler-basics) .

## [Timers mode](#timers-mode)[](#timers-mode)

Timers mode  is an alternative way of visualizing the data in the detailed view: as a list of labels with processing times and call counts. Horizontal bar graphs in some columns help you spot the busiest tasks.

 ![Timers mode.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-timers-mode.png)

Controls are similar to detailed view:

-

Left-click and hold to pan up and down.

-

Left-click a label to add it to the line graph in the lower-right.

-

Use the Groups  menu to filter the list.

-

Use the Timers  menu to customize the columns.

All of the information in this view is visible when you hover over a label in the detailed view.

## [Counters mode](#counters-mode)[](#counters-mode)

Counters mode is a lengthy list of categories and statistics, including instance count and memory usage (in bytes) for the various tasks.

 ![Counters mode with a single graph.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-counters-mode.png)

-

Just like the detailed view, left-click and hold to pan up and down.

-

Left-click in the Graph  column to add a small usage graph with minimum and maximum values. Left-click the graph again to expand it.

-

Right-click a graph to close it.

-

You can't filter this view, but you can left-click on a category (for example, memory ) to collapse it.

While counters mode can be useful, the [Developer Console](/docs/en-us/studio/optimization/memory-usage)  is the best way to [identify memory issues](/docs/en-us/performance-optimization/identify#client-memory) . You might also find the [X-ray view](/docs/en-us/performance-optimization/microprofiler#web-only-features)  helpful for identifying when problematic memory allocation occurs.

## [Groups mode](#groups-mode)[](#groups-mode)

Only available in the web UI. Similar to timers mode, groups mode provides average, max, and total task times for each group, broken down by thread, to help you identify how broad categories of tasks are impacting your frame times.

 ![MicroProfiler web UI showing groups mode.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-groups-mode.png)

## [Threads mode](#threads-mode)[](#threads-mode)

Only available in the web UI. Similar to timers mode, threads mode provides average and total task times for each thread, broken down by group, to help you identify how your game is distributing tasks across threads.

 ![MicroProfiler web UI showing threads mode.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-threads-mode.png)

## [Hidden mode](#hidden-mode)[](#hidden-mode)

Only available in the desktop UI. Hidden mode keeps the MicroProfiler menu open, but hides the bar graph. It's useful for reducing visual clutter, [saving frame data](/docs/en-us/performance-optimization/microprofiler#save-frame-data) , and pausing and unpausing while you observe the line graph.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
