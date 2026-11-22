<!-- Source: https://create.roblox.com/docs/en-us/production/analytics/custom-fields -->

Custom fields | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/production/analytics/custom-fields.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Analytics](/docs/en-us/production/analytics)
4. /
5. Event types

# Custom fields

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/production/analytics/custom-fields.md)

You can use up to three custom fields  to filter your [economy](/docs/en-us/production/analytics/economy-events) , [funnel](/docs/en-us/production/analytics/funnel-events) , and [custom](/docs/en-us/production/analytics/custom-events)  events by unique dimensions specific to your game. Some examples include:

-

Levels — 1, 2, 3, . . .

-

Player class — Warrior, Mage, Archer

-

Weapon type — SMG, Pistol, Rocket Launcher

The customFields  parameter is a dictionary that lets you send up to three custom values using the provided [Enum.AnalyticsCustomFieldKeys](/docs/en-us/reference/engine/enums/AnalyticsCustomFieldKeys)  as keys by accessing them as Enum.AnalyticsCustomFieldKeys.CustomField{01, 02, 03}.Name . Anything other than CustomField01.Name , CustomField02.Name , and CustomField03.Name  is ignored. You can have up to 8,000 unique combinations of values across the three custom fields.

The values  assigned to custom fields must be strings . If you need to log another data type like a boolean or number, pass it in string format.

Using a fantasy-related game as an example, you can track an economy event regarding equipment type, player class, and level with the following:

Tracking Custom Fields

```

local AnalyticsService = game:GetService("AnalyticsService")

AnalyticsService:LogEconomyEvent(

    player,

    Enum.AnalyticsEconomyFlowType.Sink,

    "Coins", -- Currency name

    80, -- Cost

    20, -- Balance after transaction

    Enum.AnalyticsEconomyTransactionType.Shop.Name,

    "Obsidian Sword", -- Item SKU

    {

        [Enum.AnalyticsCustomFieldKeys.CustomField01.Name] = "Category - Weapon",

        [Enum.AnalyticsCustomFieldKeys.CustomField02.Name] = "Class - Warrior",

        [Enum.AnalyticsCustomFieldKeys.CustomField03.Name] = "Level - 10",

    } -- Custom field dictionary

)

```

Including the dimension name in the value is not required, but can help you remember the context later when reviewing your charts. Other keys in the customFields  table are ignored.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
