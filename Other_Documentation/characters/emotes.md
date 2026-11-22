<!-- Source: https://create.roblox.com/docs/characters/emotes -->

Emotes | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/characters/emotes.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Characters](/docs/characters)

# Emotes

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/characters/emotes.md)

Emotes are expressive character [animations](/docs/animation)  that are accessible by using chat commands ("/e cheer") or by accessing the emotes menu  on the top right of any game. All users have access to default emotes, such as dance , point , and cheer . Additional avatar emotes can be purchased and equipped from the [Marketplace](https://www.roblox.com/catalog) .

In your game, you can perform the following emote customizations:

-

[Open and close](#open-and-close)  a user's emotes menu programmatically.

-

[Add or remove](#add-and-remove-emotes)  emotes options from a user's menu.

-

[Disable](#disable)  access to the menu.

-

[Play](#play-emotes)  an emote, targeting a specific user character.

## [Emotes menu](#emotes-menu)[](#emotes-menu)

You can open and close a user's emote menu manually, customize the menu to display specific emotes, or disable the menu completely.

### [Open and close](#open-and-close)[](#open-and-close)

To manually open or close a player's emote menu, call [GuiService:SetEmotesMenuOpen()](/docs/reference/engine/classes/GuiService#SetEmotesMenuOpen)  with a boolean value of true or false.

The following code sample will open the emotes menu for the user:

```

-- Open the emote Menu

local GuiService = game:GetService("GuiService")

GuiService:SetEmotesMenuOpen(true)

```

If you need to detect whether the emotes menu is open, call [GuiService:GetEmotesMenuOpen()](/docs/reference/engine/classes/GuiService#GetEmotesMenuOpen) . This returns a boolean indicating the menu's current state.

### [Add and remove emotes](#add-and-remove-emotes)[](#add-and-remove-emotes)

Customize the emote menu by setting emotes from the catalog and then equipping emotes to a [Humanoid](/docs/reference/engine/classes/Humanoid) . Set emotes with the [HumanoidDescription:SetEmotes()](/docs/reference/engine/classes/HumanoidDescription#SetEmotes)  method and equip up to 8 emotes to the emotes menu using [HumanoidDescription:SetEquippedEmotes()](/docs/reference/engine/classes/HumanoidDescription#SetEquippedEmotes) .

Use the following code sample in a [LocalScript](/docs/reference/engine/classes/LocalScript)  within the [StarterCharacterScripts](/docs/reference/engine/classes/StarterCharacterScripts)  folder to set and equip emotes in your game:

```

local Players = game:GetService("Players")

local humanoid = Players.LocalPlayer.Character.Humanoid

local humanoidDescription = humanoid.HumanoidDescription

-- Set custom emotes within a table

local emoteTable = {

  ["Hello"] = {3576686446},

  ["Stadium"] = {3360686498},

  ["Tilt"] = {3360692915},

  ["Shrug"] = {3576968026},

  ["Salute"] = {3360689775},

  ["Point"] = {3576823880}

}

humanoidDescription:SetEmotes(emoteTable)

-- Equip emotes in a specific order

local equippedEmotes = {"Hello", "Stadium", "Tilt", "Shrug", "Salute", "Point"}

humanoidDescription:SetEquippedEmotes(equippedEmotes)

```

Key names, such as "Shrug" or "Salute" are customizable and will appear to the player as written. Emotes will also show up in the order they were set, starting at the top of the wheel and continuing clockwise.

### [Disable](#disable)[](#disable)

Disable the emotes menu with [StarterGui:SetCoreGuiEnabled()](/docs/reference/engine/classes/StarterGui#SetCoreGuiEnabled) . Disabling the emotes menu will not prevent emotes from being performed with a chat command.

The following sample code will disable the emotes menu:

```

local StarterGui = game:GetService("StarterGui")

StarterGui:SetCoreGuiEnabled(Enum.CoreGuiType.EmotesMenu, false)

```

In addition to disabling the menu, you can disable loading of user-owned emotes by setting the [StarterPlayer.UserEmotesEnabled](/docs/reference/engine/classes/StarterPlayer#UserEmotesEnabled)  property within StarterPlayer  ⟩ Character  to false . This specific property can only be set in Studio and cannot be set by scripts.

## [Play emotes](#play-emotes)[](#play-emotes)

To manually play an emote that a character has in its [HumanoidDescription](/docs/reference/engine/classes/HumanoidDescription) , call [Humanoid:PlayEmote()](/docs/reference/engine/classes/Humanoid#PlayEmote) , passing the string name of the emote. This call will return true to indicate that the emote was played successfully, or false otherwise.

Use the following code sample to play the Shrug emote:

```

local Players = game:GetService("Players")

local humanoid = Players.LocalPlayer.Character.Humanoid

humanoid:PlayEmote("Shrug")

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
