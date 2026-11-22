<!-- Source: https://create.roblox.com/docs/players/disable-ui -->

Disable default UI | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/players/disable-ui.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Players](/docs/players)
6. /
7. Player UI

# Disable default UI

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/players/disable-ui.md)

All Roblox games include several UI elements that are enabled by default. If you don't need any of these elements or if you want to replace them with your own creations, you can use the [SetCoreGuiEnabled()](/docs/reference/engine/classes/StarterGui#SetCoreGuiEnabled)  method in a client‑side script with the associated [Enum.CoreGuiType](/docs/reference/engine/enums/CoreGuiType)  option.

| Default UI | | Associated enum |
| --- | --- |
| Dynamically updated [Players](/docs/reference/engine/classes/Players)  list, commonly used as a [leaderboard](/docs/players/leaderboards) . | | [Enum.CoreGuiType.PlayerList](/docs/reference/engine/enums/CoreGuiType#PlayerList) |
| The character's [Health](/docs/reference/engine/classes/Humanoid#Health)  bar. Does not appear if the character's [Humanoid](/docs/reference/engine/classes/Humanoid)  is at full health. | | [Enum.CoreGuiType.Health](/docs/reference/engine/enums/CoreGuiType#Health) |
| The character's [Backpack](/docs/reference/engine/classes/Backpack)  which contains [in-game tools](/docs/players/tools) . Does not appear if there are no [Tools](/docs/reference/engine/classes/Tool)  in the backpack. | | [Enum.CoreGuiType.Backpack](/docs/reference/engine/enums/CoreGuiType#Backpack) |
| The [text chat](/docs/chat/in-experience-text-chat)  window. | | [Enum.CoreGuiType.Chat](/docs/reference/engine/enums/CoreGuiType#Chat) |
| Popup menu of character [emotes](/docs/characters/emotes) . | | [Enum.CoreGuiType.EmotesMenu](/docs/reference/engine/enums/CoreGuiType#EmotesMenu) |
| A window displaying a player's perspective or view of their own character. Does not appear unless the player has enabled Self View  from the Roblox menu. | | [Enum.CoreGuiType.SelfView](/docs/reference/engine/enums/CoreGuiType#SelfView) |
| A capture screenshot  button along the right side of the screen. Does not appear unless the player has enabled Captures  from the Roblox menu. | | [Enum.CoreGuiType.Captures](/docs/reference/engine/enums/CoreGuiType#Captures) |
| The Avatar Switcher  allows users to change their platform avatar. | | [Enum.CoreGuiType.AvatarSwitcher](/docs/reference/engine/enums/CoreGuiType#AvatarSwitcher) |

 ![Core UI elements in every Roblox game.](https://prod.docsiteassets.roblox.com/assets/ui/misc/CoreGui-Elements.jpg)

Client Script - Disable Default UI Elements

```

local StarterGui = game:GetService("StarterGui")

-- Disable default health bar and backpack

StarterGui:SetCoreGuiEnabled(Enum.CoreGuiType.Health, false)

StarterGui:SetCoreGuiEnabled(Enum.CoreGuiType.Backpack, false)

```

Additionally, devices with touch capabilities include a virtual thumbstick and a jump button by default. If desired, you can hide these elements by setting [GuiService.TouchControlsEnabled](/docs/reference/engine/classes/GuiService#TouchControlsEnabled)  to false  in a client‑side script.

 ![UI elements for touch-capable devices in every Roblox game.](https://prod.docsiteassets.roblox.com/assets/ui/misc/TouchGui-Elements.png)

Client Script - Disable Touch Controls

```

local GuiService = game:GetService("GuiService")

GuiService.TouchControlsEnabled = false

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
