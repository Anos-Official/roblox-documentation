<!-- Source: https://create.roblox.com/docs/production/analytics/performance -->

Performance | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/production/analytics/performance.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Analytics](/docs/en-us/production/analytics)

# Performance

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/production/analytics/performance.md)

The Performance  dashboard provides up-to-the-minute client and server metrics for your game. Monitor this page before and after updating your game to identify performance issues early.

![An overview of the performance dashboard.](https://prod.docsiteassets.roblox.com/assets/analytics/performance/perf-dash-overview.png)

## [View performance metrics](#view-performance-metrics)[](#view-performance-metrics)

To access the performance dashboard, you must either be the game owner or have [analytics group permissions](/docs/production/analytics/analytics-dashboard#grant-group-permission) .

1.

In the Creator Hub , navigate to the [Creations](https://create.roblox.com/dashboard/creations)  page.

2.

In the upper-left corner, select your account or the group that owns the game.

3.

Select the game.

4.

In the Monitoring  dropdown, select Performance .

The dashboard begins with the current number of users, the number of servers they are spread across, and a device breakdown. For the dashboard to show client and server charts  like the ones below, your game must have at least 100 daily active users (DAU).

The dashboard contains two tabs, Client  and Server , along with menus to adjust date range and time interval. You can also use the Place  menu to examine individual places rather than the entire game.

![A marked up view of the performance dashboard UI.](https://prod.docsiteassets.roblox.com/assets/analytics/performance/perf-dash-ui.png)

The Filter By  menu lets you swap between averages or percentile values.

 ![A view of the filters menu.](https://prod.docsiteassets.roblox.com/assets/analytics/performance/perf-dash-filter.png)

When reviewing charts or filtering:

-

P90  refers to the number of values that fall within the 90th percentile. If P90 server heartbeat is 59, then 90% of servers are running at or below 59 FPS.

-

Similarly, P10  refers to the 10th percentile. If P10 server heartbeat is 40, then 10% of servers are running at or below 40 FPS.

-

P50  is the median. Half of all values fall above it, half below.

To help identify the source of a regression, you can break down all client performance metrics by Place Version  and compare your latest update against previous versions.

To filter by place version, select Place Version  in the Breakdown by  drop-down menu. The charts will automatically update to show your newest version alongside all earlier versions. You can also use the main filter menu to isolate the newest place version across the entire dashboard.

With this breakdown, you can quickly see whether your latest release has changes such as lower frame rates or an increase in out-of-memory exits compared to earlier versions.

 ![A view of the Break Down by Version Filter menu.](https://prod.docsiteassets.roblox.com/assets/analytics/performance/perf-place-version-filter.png)

## [Client charts](#client-charts)[](#client-charts)

The Client  tab includes the following charts, all of which are broken down by platform or operating system:

| Chart | | Description |
| --- | --- |
| Concurrent users | | Line graph showing the number of users in your game. |
| Session time | | Duration that users spend in your game. |
| Client frame rate | | Line graph showing client frames per second. Persistent low frame rates or large drops may signal issues. For information on investigating client frame rate, see [Client Compute](/docs/performance-optimization/identify#client-compute) . |
| Client crash rate | | Line graph showing client crashes, divided by ended sessions by device type. Spikes in crash rate, particularly following an update to the game, often indicate an issue. |
| Unexpected out-of-memory exits | | Line graph showing how often users crash due to out-of-memory errors, or exit via low memory warning. While this chart might not cover all out-of-memory crashes due to telemetry limitations, it is directionally accurate. A spike after an update indicates a regression in memory usage that causes your users to crash. |
| Client crash count | | Line graph showing the crash rate count by device type. If you have noisy crash rate data due to low sample size, we recommend monitoring the crash rate count as well. |
| Client memory usage | | Line graph showing client memory usage by device type. Continual increases can indicate a memory leak. See [Memory](/docs/performance-optimization/identify#client-memory) . |
| Client memory usage percentage | | Line graph showing percentage of available device memory the client is using. For example, if the Android line approaches 100%, the majority of Android devices running your game are at risk of running out of memory and crashing. |
| Client CPU time | | Stacked area chart showing milliseconds (ms) of processing time per frame. You want your client CPU time as low as possible, as it directly impacts your frame rates. To hit a client frame rate of 60, your CPU time must be below 16 ms. |

### [Crash rate](#crash-rate)[](#crash-rate)

Client crash rate measures the number of crashes divided by the number of ended sessions. When the number of ended sessions is low, crash rate breakdowns can become unstable. In these cases, the chart will show a dashed line instead of a solid line, indicating that the data point is noisy and that the crash rate might vary. If you see a dashed line on your chart, we recommend checking the total crash count instead of the client crash rate.

 ![A view of the client crashes dashboard.](https://prod.docsiteassets.roblox.com/assets/analytics/performance/perf-client-crashes.png)

If you have memory issues, check out the [performance optimization](/docs/performance-optimization)  guide.

## [Server charts](#server-charts)[](#server-charts)

The Server  tab includes the following charts:

| Chart | | Description |
| Server CPU time | | Stacked area chart showing milliseconds (ms) of processing time per frame. To hit a server frame rate of 60, your CPU time must be below 16 ms. See [Server Compute](/docs/performance-optimization/identify#server-compute) . |
| Server frame rate | | Line graph showing server frame rate in FPS. Ideally, this value is always 60. Server frame rate is capped at 60, and drops can reduce client frame rate and increase latency. See [Script Computation](/docs/performance-optimization/improve#script-computation) . |
| Server memory usage | | Stacked area chart showing server memory usage in MB. Try to keep this value below 50% of the [total server memory](/docs/performance-optimization/identify#server-memory) . However, the chart doesn't show the total server memory, so another good guideline is to stay below 3 GB. If this number stays high or continually increases over time, investigate ways to [improve memory usage](/docs/performance-optimization/improve#script-memory-usage) . |
| Server memory by age | | Stacked area chart showing server memory usage by server age. If memory usage increases significantly over the lifespan of the server, investigate possible memory leaks in the categories with the most growth, particularly [scripts](/docs/performance-optimization/improve#script-memory-usage) , [physics](/docs/performance-optimization/improve#physics-memory-usage) , and [rendering](/docs/performance-optimization/improve#rendering) . |
| Cores used per server | | Line graph showing server CPU core count usage. Low core count usage combined with high server CPU time is an indicator that you should investigate [multithreading](/docs/scripting/multithreading) . If core usage stays high after you optimize, you can reserve more server CPU with [Extended Services for Compute](/docs/cloud-services/extended-services#extended-services-for-compute) . |
| Compute efficiency | | Line graph showing the efficiency of your game compared to the Roblox average. Values above 100% indicate higher efficiency than the baseline. Contributing factors include maximum number of players per server (higher is more efficient) and server CPU time per frame (lower is more efficient). Higher compute efficiency means lower environmental impact, but this metric is not indicative of a good or bad player experience. |

For a deep dive view on server crashes and out-of-memory snapshots, see [Server crashes chart](/docs/production/analytics/crashes) .

The server CPU and memory charts default to the Overall  view, but have dropdown menus for individual process groups, such as physics, rendering, and scripts. The sum of these categories is not  comprehensive; the server performs a small and typically insignificant amount of additional work per frame that isn't included in any category. As such, the overall millisecond and MB values are slightly lower than reality, but close enough to give you a clear understanding of server performance.

If a category is higher than usual or appears to be taking up a disproportionate amount of time, use the dropdown menu to drill down on the group and identify processes that could be causing issues.

 ![The server CPU time chart showing the physics dropdown.](https://prod.docsiteassets.roblox.com/assets/analytics/performance/perf-dash-drilldown.png)

To exclude a group or process from a chart, click its label in the legend.

-

CPU categories and tasks map to the ones in the [MicroProfiler](/docs/performance-optimization/microprofiler) , so you can take [server dumps](/docs/performance-optimization/microprofiler#profile-the-server) , select Timers  mode, and then use the Groups  menu to filter by the problematic process group.

For example, if you spot a potential problem with the assemble  process under the Physics  group, you can find it under the same name in the MicroProfiler:

 ![The MicroProfiler showing the assemble process within the Physics group.](https://prod.docsiteassets.roblox.com/assets/analytics/performance/perf-dash-micro.png)

-

Memory tags map to the ones in [Enum.DeveloperMemoryTag](/docs/reference/engine/enums/DeveloperMemoryTag) , with the notable exception of CoreMemory:Total , which is equivalent to [Enum.DeveloperMemoryTag.Internal](/docs/reference/engine/enums/DeveloperMemoryTag#Internal) . You can use the [Developer Console](/docs/studio/optimization/memory-usage#memory)  to check tags for excessive usage. This image shows how you might use the Developer Console to investigate an issue with PlaceMemory:GraphicsTexture  that you see in the dashboard:

 ![The Developer Console showing the server memory view.](https://prod.docsiteassets.roblox.com/assets/analytics/performance/perf-dash-dev.png)

## [Roblox updates](#roblox-updates)[](#roblox-updates)

Each Roblox update contains many changes including features and bug fixes. Roblox update  annotations allow you to cross‑reference your game's performance with recent Roblox platform updates.

 ![A view of the Roblox updates annotations on the Performance dashboard.](https://prod.docsiteassets.roblox.com/assets/analytics/performance/perf-dash-roblox-updates.png)

Some platforms release to 100% of users immediately after the version is made available. Other platforms roll out gradually and require additional time to ramp up adoption; these receive a single annotation once a version is made available, giving you the earliest available signal without adding visual clutter.

Immediate Rollout

-

Windows

-

macOS

-

Xbox

Gradual Rollout

-

iOS

-

Google

-

Amazon

-

Samsung

-

PlayStation

-

Meta Quest

## [Troubleshooting](#troubleshooting)[](#troubleshooting)

If you spot a potential problem, use the following steps to remediate and fix it:

1.

Check your recent updates and consider rolling them back if the impact to metrics is severe.

2.

See [Identify performance issues](/docs/performance-optimization/identify)  and [Improve performance](/docs/performance-optimization/improve)  for information on troubleshooting problems with server compute, client compute, and memory usage.

3.

Use built-in testing tools to further drill down on problems:

-

[Developer Console](/docs/studio/developer-console)  for viewing error and log messages and detailed information on memory and networking.

-

[Script Profiler](/docs/studio/optimization/scriptprofiler)  for identifying scripts that take up the most resources.

-

The [MicroProfiler](/docs/performance-optimization/microprofiler)  for viewing unoptimized portions of your game visually.

4.

Gather user feedback from your community.

## [Client API calls after join](#client-api-calls-after-join)[](#client-api-calls-after-join)

This metric is only available for a small number of top games.

The Client API Calls in First 60s After Join  metric measures the total number of requests (API calls) your game makes to Roblox services during the critical first minute after a user successfully joins.

These calls happen automatically for every user who joins, so monitoring this metric can help you understand load-time efficiency and backend performance.

### [Access the metric](#access-the-metric)[](#access-the-metric)

1.

Navigate to your game overview on the Creator Hub.

2.

On the Snapshot  graph, click Explore .

3.

In the Select a metric  dropdown, choose Client API Calls in First 60s After Join .

![Graph of the client API calls metric](https://prod.docsiteassets.roblox.com/assets/analytics/performance/client-api-calls.png)

### [Monitor the metric](#monitor-the-metric)[](#monitor-the-metric)

The primary goal during the first 60 seconds of a player joining is to stream and load your game's assets (meshes, images, sounds, etc.). Ideally, the asset delivery service is the most-called API during this key time span.

The metric is updated hourly so that you can quickly check it after publishing a new version of your game.

| Condition | | Implication | | Action |
| Asset delivery is the most-hit API. | | Efficient.  Your game is correctly prioritizing the loading of necessary assets. | | Continue monitoring. |
| A different service (e.g. inventory, friends, or users) is the most-hit API. | | Potential inefficiency or bug.  Your game is executing heavy, non-critical API calls too early in the join sequence, potentially delaying the load process. | | Investigate and refactor the scripts that execute during the initial join to prioritize asset loading. |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
