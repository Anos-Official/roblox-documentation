<!-- Source: https://create.roblox.com/docs/en-us/ui/on-screen-containers -->

On-screen UI containers | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/ui/on-screen-containers.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [User interface](/docs/en-us/ui)

# On-screen UI containers

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/ui/on-screen-containers.md)

The [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  container holds [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject)  to display on a player's screen, including [frames](/docs/en-us/ui/frames) , [labels](/docs/en-us/ui/labels) , [buttons](/docs/en-us/ui/buttons) , and more. All on‑screen UI objects and code are stored and changed on the client.

![Example ScreenGui with various GuiObject children, including a Frame, TextLabel, TextBox, and ImageButton.](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/ScreenGui-Example.jpg)

For UI containers that hold [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject)  that you want to display within  the 3D world, such as on the face of a part, see [In-game UI Containers](/docs/en-us/ui/in-experience-containers) .

To display a [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  and its child [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject)  to every player who joins the game, place it inside the [StarterGui](/docs/en-us/reference/engine/classes/StarterGui)  container. When a player joins a game and their character first spawns, the [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  and its contents clone into the [PlayerGui](/docs/en-us/reference/engine/classes/PlayerGui)  container for that player, located within the [Players](/docs/en-us/reference/engine/classes/Players)  container.

 ![Diagram of how a ScreenGui clones from StarterGui to a player's PlayerGui](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/StarterGui-To-PlayerGui.png)

By default, [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject)  inside a [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  within [StarterGui](/docs/en-us/reference/engine/classes/StarterGui)  appear as an overlay of the [3D viewport](/docs/en-us/studio/overview#3d-viewport) , simulating their appearance and position in a running game. To hide all such screen overlays, toggle off GUI overlay  from the [Visualization Options](/docs/en-us/studio/overview#visualization-options)  widget in the upper‑right corner of the 3D viewport.

If [Players.CharacterAutoLoads](/docs/en-us/reference/engine/classes/Players#CharacterAutoLoads)  is disabled, the contents of [StarterGui](/docs/en-us/reference/engine/classes/StarterGui)  will not be cloned until [Player:LoadCharacterAsync()](/docs/en-us/reference/engine/classes/Player#LoadCharacterAsync)  is called.

As a game grows in scope, you may require multiple screen interfaces such as a title screen, settings menu, shop interface, and more. In such cases, you can place multiple unique [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  containers inside [StarterGui](/docs/en-us/reference/engine/classes/StarterGui)  and toggle each container's [Enabled](/docs/en-us/reference/engine/classes/ScreenGui#Enabled)  property depending on whether it should be visible and active (while false , contents will not render, process user input, or update in response to changes).

 ![Explorer hierarchy showing multiple ScreenGui containers, one enabled and the others disabled, in order to control which are visible at a given time.](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/ScreenGuis-Enabled.png)

The [Enabled](/docs/en-us/reference/engine/classes/ScreenGui#Enabled)  property can be initially toggled through the [Properties](/docs/en-us/studio/properties)  window and/or you can set it during playtime from a client‑side script by [accessing](#access-player-ui)  the player's [PlayerGui](/docs/en-us/reference/engine/classes/PlayerGui)  and setting it to true  or false  for the desired container(s).

When using multiple [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  interfaces, you can layer them by Z‑index through their [DisplayOrder](/docs/en-us/reference/engine/classes/ScreenGui#DisplayOrder)  property. See [Display Order](#display-order)  for more information.

## [Container properties](#container-properties)[](#container-properties)

The following properties let you customize the [screen insets](#screen-insets)  across multiple devices, the [display order](#display-order)  when using multiple screen containers, and more.

### [Screen insets](#screen-insets)[](#screen-insets)

Modern phones take advantage of the entire screen but typically include notches, cutouts, and other elements that occupy screen space. Every Roblox game also includes the top bar controls  for quick access to the main menu, [chat](/docs/en-us/chat/in-experience-text-chat) , [leaderboard](/docs/en-us/players/leaderboards) , and more.

 ![Mobile device showing Roblox top bar buttons and device cutout.](https://prod.docsiteassets.roblox.com/assets/engine-api/enums/ScreenInsets/Top-Bar-Cutout.png)

To ensure players can see and access all UI easily and without obstruction, Roblox provides the [ScreenInsets](/docs/en-us/reference/engine/classes/ScreenGui#ScreenInsets)  property which controls the safe area  insets for the contents of a [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui) .

CoreUISafeInsets DeviceSafeInsets TopbarSafeInsets None

The default of [CoreUISafeInsets](/docs/en-us/reference/engine/enums/ScreenInsets)  keeps all descendant [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject)  inside the core UI safe area, clear of the top bar buttons and other screen cutouts. This setting is recommended if the [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  contains interactive UI elements.

![Mobile device showing the core UI safe area.](https://prod.docsiteassets.roblox.com/assets/engine-api/enums/ScreenInsets/CoreUISafeInsets.png)

### [Display order](#display-order)[](#display-order)

When using multiple [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  interfaces, you can layer them by Z‑index through their [DisplayOrder](/docs/en-us/reference/engine/classes/ScreenGui#DisplayOrder)  property. For example, to display a modal settings menu on one [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  in front of the game's main user interface on another [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui) , assign a higher [DisplayOrder](/docs/en-us/reference/engine/classes/ScreenGui#DisplayOrder)  to the modal's than the underlying interface's.

### [Reset on spawn](#reset-on-spawn)[](#reset-on-spawn)

The [ResetOnSpawn](/docs/en-us/reference/engine/classes/ScreenGui#ResetOnSpawn)  boolean property determines if the [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  resets (deletes itself and re‑clones into the player's [PlayerGui](/docs/en-us/reference/engine/classes/PlayerGui) ) every time the player's character respawns.

| Condition | | Resets |
| --- | --- |
| [ResetOnSpawn](/docs/en-us/reference/engine/classes/ScreenGui#ResetOnSpawn)  is true  (default). | |

YES

 |
| The [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  is an indirect  descendant of [StarterGui](/docs/en-us/reference/engine/classes/StarterGui) ; for example it's placed inside a [Folder](/docs/en-us/reference/engine/classes/Folder)  located within [StarterGui](/docs/en-us/reference/engine/classes/StarterGui) . | |

YES

 |
| [ResetOnSpawn](/docs/en-us/reference/engine/classes/ScreenGui#ResetOnSpawn)  is false  and  the [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  is a direct  descendant of [StarterGui](/docs/en-us/reference/engine/classes/StarterGui) . | |

NO

 |

## [Access player UI](#access-player-ui)[](#access-player-ui)

As noted, parenting a [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  to [StarterGui](/docs/en-us/reference/engine/classes/StarterGui)  clones it and its child [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject)  into a player's [PlayerGui](/docs/en-us/reference/engine/classes/PlayerGui)  container when they join the game and their character first spawns.

If you need to control a player's UI container during playtime, for example to show/hide a specific [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  or any of its children, access it as follows from a [LocalScript](/docs/en-us/reference/engine/classes/LocalScript) :

LocalScript - Accessing a Player's UI

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local playerGui = player.PlayerGui

local titleScreen = playerGui:WaitForChild("TitleScreen")

local settingsMenu = playerGui:WaitForChild("SettingsMenu")

titleScreen.Enabled = false  -- Hide title screen

settingsMenu.Enabled = true  -- Show settings menu

```

## [Disable default UI](#disable-default-ui)[](#disable-default-ui)

All Roblox games include several UI elements that are enabled by default. If you don't need any of these elements or if you want to replace them with your own creations, you can use the [SetCoreGuiEnabled()](/docs/en-us/reference/engine/classes/StarterGui#SetCoreGuiEnabled)  method in a client‑side script with the associated [Enum.CoreGuiType](/docs/en-us/reference/engine/enums/CoreGuiType)  option.

| Default UI | | Associated enum |
| Dynamically updated [Players](/docs/en-us/reference/engine/classes/Players)  list, commonly used as a [leaderboard](/docs/en-us/players/leaderboards) . | | [Enum.CoreGuiType.PlayerList](/docs/en-us/reference/engine/enums/CoreGuiType#PlayerList) |
| The character's [Health](/docs/en-us/reference/engine/classes/Humanoid#Health)  bar. Does not appear if the character's [Humanoid](/docs/en-us/reference/engine/classes/Humanoid)  is at full health. | | [Enum.CoreGuiType.Health](/docs/en-us/reference/engine/enums/CoreGuiType#Health) |
| The character's [Backpack](/docs/en-us/reference/engine/classes/Backpack)  which contains [in-game tools](/docs/en-us/players/tools) . Does not appear if there are no [Tools](/docs/en-us/reference/engine/classes/Tool)  in the backpack. | | [Enum.CoreGuiType.Backpack](/docs/en-us/reference/engine/enums/CoreGuiType#Backpack) |
| The [text chat](/docs/en-us/chat/in-experience-text-chat)  window. | | [Enum.CoreGuiType.Chat](/docs/en-us/reference/engine/enums/CoreGuiType#Chat) |
| Popup menu of character [emotes](/docs/en-us/characters/emotes) . | | [Enum.CoreGuiType.EmotesMenu](/docs/en-us/reference/engine/enums/CoreGuiType#EmotesMenu) |
| A window displaying a player's perspective or view of their own character. Does not appear unless the player has enabled Self View  from the Roblox menu. | | [Enum.CoreGuiType.SelfView](/docs/en-us/reference/engine/enums/CoreGuiType#SelfView) |
| A capture screenshot  button along the right side of the screen. Does not appear unless the player has enabled Captures  from the Roblox menu. | | [Enum.CoreGuiType.Captures](/docs/en-us/reference/engine/enums/CoreGuiType#Captures) |
| The Avatar Switcher  allows users to change their platform avatar. | | [Enum.CoreGuiType.AvatarSwitcher](/docs/en-us/reference/engine/enums/CoreGuiType#AvatarSwitcher) |

 ![Core UI elements in every Roblox game.](https://prod.docsiteassets.roblox.com/assets/ui/misc/CoreGui-Elements.jpg)

Client Script - Disable Default UI Elements

```

local StarterGui = game:GetService("StarterGui")

-- Disable default health bar and backpack

StarterGui:SetCoreGuiEnabled(Enum.CoreGuiType.Health, false)

StarterGui:SetCoreGuiEnabled(Enum.CoreGuiType.Backpack, false)

```

Additionally, devices with touch capabilities include a virtual thumbstick and a jump button by default. If desired, you can hide these elements by setting [GuiService.TouchControlsEnabled](/docs/en-us/reference/engine/classes/GuiService#TouchControlsEnabled)  to false  in a client‑side script.

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
