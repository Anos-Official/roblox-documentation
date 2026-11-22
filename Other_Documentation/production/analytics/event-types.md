<!-- Source: https://create.roblox.com/docs/production/analytics/event-types -->

Event types | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/production/analytics/event-types.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Analytics](/docs/en-us/production/analytics)
4. /
5. Event types

# Event types

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/production/analytics/event-types.md)

Event types help you identify opportunities to grow and monetize your game. They allow you to integrate event tracking into your game and visualize your in-game economy and player usage patterns on the Analytics dashboard

After you begin tracking these events from your game using [AnalyticsService](/docs/reference/engine/classes/AnalyticsService) , you unlock new [economy](/docs/production/analytics/economy-events) , [funnel](/docs/production/analytics/funnel-events) , [journey](/docs/production/analytics/journey-events) , and [custom](/docs/production/analytics/custom-events)  dashboards under Analytics on the Creator Dashboard. You can use these dashboards to identify growth opportunities and segment users by age, gender, platform, OS and custom fields. All of these features are free to use .

 ![Economy and Funnels dashboard pages populated with data.](https://prod.docsiteassets.roblox.com/assets/analytics/event-types/Overview-Economy-Funnels.png)

## [Event types](#event-types)[](#event-types)

Roblox provides four sets of analytic dashboards you can use to track different aspects of your game:

1.

Economy events  let you track your in-game economy, such as:

-

Top sinks  — What do users spend in-game resources on?

-

Top sources  — Where do users earn resources?

-

Average wallet balance  — How many resources are users holding?

2.

Funnel events  let you track your user's progress through key stages of your game, such as:

-

Onboarding  — Where do users drop off when getting started with your game?

-

Progression  — Where do users stop advancing through your game?

-

Shop  — Where do users abandon purchases?

3.

Journey events  let you track your user's progress through a series of stages that can branch and reconnect, such as:

-

Onboarding  — Where do users branch off into different first-time experiences?

-

Open-world progression  — Which routes do users take through non-linear content?

-

Shop paths  — Do users reach checkout through multiple different flows?

4.

Custom events  let you track metrics specific to your game, such as:

-

Adoption  — How many users click on a specific UI component?

-

User behavior  — What is the most frequently used ability on each map?

-

Core loop  — How do kill/death ratios compare across different weapons?

For more information on setting up these dashboards, see [Economy events](/docs/production/analytics/economy-events) , [Funnel events](/docs/production/analytics/funnel-events) , [Journey events](/docs/production/analytics/journey-events) , and [Custom events](/docs/production/analytics/custom-events) .

## [Validate your event tracking](#validate-your-event-tracking)[](#validate-your-event-tracking)

Once you add [economy](/docs/production/analytics/economy-events) , [funnel](/docs/production/analytics/funnel-events) , or [custom](/docs/production/analytics/custom-events)  events to your game, charts on the respective pages typically take 24 hours to appear. In the meantime, you can check if events are set up correctly using the View Events  tool:

1.

Navigate to the Economy , Funnel , or Custom  pages of your Analytics dashboard for your game.

2.

Click the View Events  button at the top of each page. A near real-time list of the most recent events displays.

3.

Refresh the page to update the list.

 ![View events report displaying multiple event entries sortable by event type, user ID and keyword.](https://prod.docsiteassets.roblox.com/assets/analytics/event-types/Event-Tracking.png)

If you see more events than you were expecting, verify that your calls to the [AnalyticsService](/docs/reference/engine/classes/AnalyticsService)  methods occur after  a successful operation. For example, you should call [LogEconomyEvent()](/docs/reference/engine/classes/AnalyticsService#LogEconomyEvent)  after a successful purchase, not when the user attempts a purchase (which could fail due to lack of funds).

You can also visit your game's [error report](/docs/production/analytics/error-report)  to see if there are any errors with your event tracking.

## [Event tracking limitations](#event-tracking-limitations)[](#event-tracking-limitations)

The following limitations apply when tracking your events with [AnalyticsService](/docs/reference/engine/classes/AnalyticsService) . Limitations reset daily. You will be able to send new events the next day once you stop sending previous events. Each event remains visible on the Creator Dashboard and automatically rolls off after 90 days from the last data received.

You can leverage [custom fields](/docs/production/analytics/custom-fields)  to additionally filter your analytic events.

For example, instead of tracking WarriorXP , MageXP , PaladinXP  as separate economy currencies, set XP  as one currency and set Warrior , Mage , Paladin , ... , as Custom Field 1. This allows you to break down these values on your dashboards and not use up your currency cardinality.

|  | | Limitation | | Maximum value | | Examples |
| --- | --- |
| Global Rate Limit | | Total [AnalyticsService](/docs/reference/engine/classes/AnalyticsService)  requests per minute | | 120 + (20 * CCU) | |  |
|  | |  | |  | |  |
| Economy, Funnel, and Custom events | | Number of [custom fields](/docs/production/analytics/custom-fields) | | 3 | | Class, Level, Weapon |
| Unique values per [custom field](/docs/production/analytics/custom-fields) | | Unlimited — After 8,000 combined values across all custom fields, values will be grouped as "Other" | | Warrior, Mage, Archer |
| Economy only | | Resource types | | 10 | | Coins, Gold, Credits |
| transactionTypes | | Unlimited — After 20, values will be grouped as "Other" | | IAP, Gameplay |
| itemSkus | | Unlimited — After 100, values will be grouped as "Other" | |  |
| Funnel only | | Number of funnels | | 10 | | Onboarding, Shop |
| Steps per funnel | | 100 | | Step 1, Step 2, Step 3 |
| Custom only | | eventNames | | 100 | | MonsterDefeated, KillDeathRatio, PetAdoption |

## [Instrument events with Studio MCP](#instrument-events-with-studio-mcp)[](#instrument-events-with-studio-mcp)

You can use the /rbx-instrument-analytics  skill with [Studio MCP](/docs/studio/mcp)  or [Assistant](/docs/assistant/guide)  to add analytics events to your game.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
