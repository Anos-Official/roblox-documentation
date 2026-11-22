<!-- Source: https://create.roblox.com/docs/cloud-services/memory-stores/observability -->

Memory store observability | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/cloud-services/memory-stores/observability.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Cloud services](/docs/cloud-services/data-stores-vs-memory-stores)
6. /
7. [Memory stores](/docs/cloud-services/memory-stores)

# Memory store observability

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/cloud-services/memory-stores/observability.md)

The memory stores observability dashboard provides real-time charts on your memory usage and API requests. It also has a built-in alert system that notifies you by email when an issue arises to help you troubleshoot in sync. For further information about specific errors, you can view your [Error Report](/docs/production/analytics/error-report)  to find the error logs.

## [Access the dashboard](#access-the-dashboard)[](#access-the-dashboard)

The memory stores observability dashboard is available for any game using [MemoryStoreService](/docs/reference/engine/classes/MemoryStoreService) , but you must either be the game owner or have [analytics group permissions](/docs/production/analytics/analytics-dashboard#grant-group-permission)  to access the dashboard.

To access the dashboard:

1.

Navigate to the [Creations](https://create.roblox.com/dashboard/creations)  page on the Creator Dashboard .

2.

Expand the account switcher in the upper-left and select your account or the group owning the target game.

3.

Select the game.

4.

In the Monitoring  dropdown, select Memory Stores .

## [Available charts](#available-charts)[](#available-charts)

The dashboard includes two categories of line graphs:

-

Quota Usage  charts for tracking your usage compared to the [dynamically allocated quotas](/docs/cloud-services/memory-stores#limits-and-quotas) , which are calculated based on the number of users in your game.

-

Memory Usage  on your memory usage per minute in bytes compared to how much your allocated quota left.

-

API Request Unit  on your total request units per minute compared to how much your allocated quota left. This chart can be broken down by each API method.

-

API Usage and Performance  charts for monitoring the API usage pattern and performance based on API method and response status.

-

Request Count by API  on API request count per minute by API method, such as [MemoryStoreQueue:ReadAsync()](/docs/reference/engine/classes/MemoryStoreQueue#ReadAsync)  or [MemoryStoreSortedMap:UpdateAsync()](/docs/reference/engine/classes/MemoryStoreSortedMap#UpdateAsync) .

-

Request Count by Status  on API request count by [response status](#response-status-codes) .

-

Request by API x Status  on response statuses returned by all or a specific API method.

The chart contains data for the past 30 days, and you can select to view a custom time range with the selector at the top of the page. If you select a time range earlier than 30 days, the system returns a Request Failed  error.

## [Response status codes](#response-status-codes)[](#response-status-codes)

The Observability Dashboard's Request Count by Status  and Requests by API x Status  charts include status codes of API responses that you can use to understand and troubleshoot errors. For a table that lists and describes all of these status codes, see [Observability](/docs/cloud-services/memory-stores#observability) . In addition, for information on how to resolve these errors, or the specific quota or limit that an error relates to, see [Troubleshooting](/docs/cloud-services/memory-stores#troubleshooting)  and [Limits and Quotas](/docs/cloud-services/memory-stores#limits-and-quotas) , respectively.

## [Notification alerts](#notification-alerts)[](#notification-alerts)

The email alert system automatically detects and sends you alerts of memory store usage issues that can harm the performance of your game. There are two types of alerts:

-

Warnings  are alerts with lower priority about issues that can potentially impact your game. You should resolve them before they become critical issues. The dashboard flags these alerts by highlighting the chart in yellow with a warning message.

-

Criticals  are alerts with higher priority on issues directly impacting your game. You should resolve these issues as soon as possible to prevent degraded performance. The dashboard flags these alerts by highlighting the chart in red with an error message.

When your game triggers two types of alerts at the same time, the dashboard displays the alert header message and highlights the chart region for your attention as Critical .

Currently, the system has four built-in alerts for memory usage and API requests. If your game exceeds an alerting threshold, the system notifies you at most once a day for each alert. When receiving an email alert, you should view the dashboard and take actions to prevent degraded performance.

### [Memory usage alerts](#memory-usage-alerts)[](#memory-usage-alerts)

The system sends the following memory usage alerts:

-

A Warning  alert when your game's memory usage has exceeded 70% of the total quota within the past hour.

 ![](https://prod.docsiteassets.roblox.com/assets/data/memory-store/Memory-Usage-Warning.png)

-

A Critical  alert when your game exceeded the memory size quota for the past hour.

 ![](https://prod.docsiteassets.roblox.com/assets/data/memory-store/Memory-Usage-Critical.png)

These issues usually occur when you overpopulate a memory store data structure with too much data, which can consume the quota quickly even if you only send requests on a few keys. For example, if you set a long expiration time on keys or don't clean up processed data, extra data can fill up your memory quota.

To prevent and resolve these issues, apply [best practices](/docs/cloud-services/memory-stores#best-practices)  to keep track of data structures you're actively using and set up a mechanism for cleaning up processed data.

### [API request alerts](#api-request-alerts)[](#api-request-alerts)

The system sends the following API request alerts:

-

A Critical  alert when the number of your memory store request failures has exceeded 20% within the past hour.

 ![](https://prod.docsiteassets.roblox.com/assets/data/memory-store/Request-Failure-Critical.png)

-

A Critical  alert when more than 10% of your memory store requests are being throttled for the past hour.

-

This alert is based on the number of DataStructureRequestsOverLimit  + TotalRequestsOverLimit , which are error responses indicating that your game is throttled because it sends too many requests.

-

This alert isn't related to the request size, only quantity.

 ![](https://prod.docsiteassets.roblox.com/assets/data/memory-store/Request-Throttled-Critical.png)

All API requests have corresponding [response status codes](#response-status-codes) , so you can view the ratio of Success  responses to all error responses using the Request Count by Status  chart for [troubleshooting](/docs/cloud-services/memory-stores#troubleshooting) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
