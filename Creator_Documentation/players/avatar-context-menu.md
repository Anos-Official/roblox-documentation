<!-- Source: https://create.roblox.com/docs/en-us/players/avatar-context-menu -->

Avatar Context Menu | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/players/avatar-context-menu.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Players](/docs/en-us/players)
6. /
7. Player UI

# Avatar Context Menu

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/players/avatar-context-menu.md)

The Avatar Context Menu  (ACM) makes it easier for users to interact with each other. When the ACM is enabled in your game, a user can walk up to another user's character and click on them to open a small menu with several default options. The player can send a friend request, begin a private chat, view the user's profile, or wave.

After [enabling](#enable-the-avatar-context-menu)  the ACM in your game, you can customize the ACM in the following ways:

-

Programmatically [open and close](#open-and-close-the-acm)  the ACM for specific users.

-

[Add](#add-menu-options)  custom options and [remove](#remove-menu-options)  existing options to the ACM.

-

[Customize the ACM appearance](#customize-menu-appearance)  to create a unique user interface.

## [Enable the Avatar Context Menu](#enable-the-avatar-context-menu)[](#enable-the-avatar-context-menu)

The Avatar Context Menu must be enabled using the [StarterGui:SetCore()](/docs/en-us/reference/engine/classes/StarterGui#SetCore)  option "AvatarContextMenuEnabled" in a [LocalScript](/docs/en-us/reference/engine/classes/LocalScript) . The ACM is best used in games where there is no predefined behavior for clicking on other users.

Use the following code sample to enable the ACM in a [LocalScript](/docs/en-us/reference/engine/classes/LocalScript) :

```

-- Run in a LocalScript, ideally within "StarterPlayerScripts"

local StarterGui = game:GetService("StarterGui")

StarterGui:SetCore("AvatarContextMenuEnabled", true)

```

If you need to detect whether the ACM is enabled, you can use the following code to return a boolean on the current status of the ACM:

```

---Returns a boolean indicating if the ACM is currently enabled.

StarterGui:GetCore(AvatarContextMenuEnabled)

```

## [Open and close the ACM](#open-and-close-the-acm)[](#open-and-close-the-acm)

Once enabled, you can open and close the ACM programmatically with [StarterGui](/docs/en-us/reference/engine/classes/StarterGui) .

To programmatically open the ACM, use the following code:

```

-- Use StarterGui:SetCore where targetPlayer is a valid Player object

StarterGui:SetCore("AvatarContextMenuTarget", targetPlayer)

```

To programmatically close the ACM, use the following code:

```

StarterGui:SetCore("AvatarContextMenuTarget", nil)

```

## [Menu options](#menu-options)[](#menu-options)

You can [add](#add-menu-options)  and [remove](#remove-menu-options)  actions through scripting. By default, the menu has the following options:

| Menu option | | Description |
| --- | --- |
| Friend | | Sends a friend request to the selected user. |
| Chat | | Opens a private conversation with the selected user in the in-game chat. |
| View | | Opens a window to inspect the selected user's appearance. |
| Wave | | Initiates a wave animation to the selected user.  |

Once the ACM is open, the user can scroll and select other users on the character selection carousel. Characters are sorted based on distance to the selected character. The menu only updates when opened and the list of available users will repeat when scrolling.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/context-menu/ACM-User-Selector.png)

### [Add menu options](#add-menu-options)[](#add-menu-options)

Once enabled, game-specific actions can be added to the ACM. For example, a game might allow for trade requests, add-to-party options, or other special interactions.

The following example shows how to add a custom action to the Avatar Context Menu:

```

local Players = game:GetService("Players")

local StarterGui = game:GetService("StarterGui")

local player = Players.LocalPlayer

-- Connect a function to a "BindableEvent"

local bindableEvent = Instance.new("BindableEvent")

local function onCustomACMAction(targetPlayer)

	-- At this point, you could call InvokeServer() on a RemoteFunction to alert the server of the selection

	print("ACM event selected by " .. player.Name .. " on " .. targetPlayer.Name)

end

bindableEvent.Event:Connect(onCustomACMAction)

-- Add the ACM option using SetCore() with "AddAvatarContextMenuOption"

local options = {"Custom ACM Action", bindableEvent}

StarterGui:SetCore("AddAvatarContextMenuOption", options)

```

### [Remove menu options](#remove-menu-options)[](#remove-menu-options)

You can remove custom and the default Add Friend, Chat, View, and Wave options from the ACM by referencing the custom Action name or the default [Enum.AvatarContextMenuOption](/docs/en-us/reference/engine/enums/AvatarContextMenuOption)  enum.

Use the following code to remove a default and custom menu option:

```

-- Remove the "Custom ACM Action" option

StarterGui:SetCore("RemoveAvatarContextMenuOption", "Custom ACM Action")

-- Remove the default "Friend" option by referencing the AvatarContextMenuOption.Friend Enum

StarterGui:SetCore("RemoveAvatarContextMenuOption", Enum.AvatarContextMenuOption.Friend)

```

You can not make edits to the ACM while it is open. Your code should verify that an action is still relevant in case the action was removed from the menu. For example, if a marketplace area adds an option to send trade requests, you should verify both users are still in the marketplace.

## [Customize menu appearance](#customize-menu-appearance)[](#customize-menu-appearance)

To change the appearance of the Avatar Context Menu, call [StarterGui:SetCore()](/docs/en-us/reference/engine/classes/StarterGui#SetCore)  with the option "AvatarContextMenuTheme", providing a table of parameters and values to adjust the menu appearance.

The ACM user interface includes the following sections:

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/context-menu/ACM-Sections-Labeled.png)

A. Name Tag: The user name of the character being interacted with.

B. Button Frame: Contains all of the ACM buttons.

C. Buttons: Individual buttons for the default or custom ACM actions.

### [Appearance parameters](#appearance-parameters)[](#appearance-parameters)

These are the customization parameters with the ACM:

#### [Background](#background)[](#background)

| BackgroundColor | | A [Color3](/docs/en-us/reference/engine/datatypes/Color3)  for the overall background of the ACM (most useful when not using a background image). |
| BackgroundTransparency | | Transparency value (0–1) for the overall background of the ACM (most useful when not using a background image). |
| BackgroundImage | | A valid asset ID of an image for the ACM background. |
| BackgroundImageTransparency | | Transparency value (0–1) for the background image. |
| BackgroundImageScaleType | | A [Enum.ScaleType](/docs/en-us/reference/engine/enums/ScaleType)  enum for background image scaling. |
| BackgroundImageSliceCenter | | A [Rect](/docs/en-us/reference/engine/datatypes/Rect)  specifying the center of a nine-slice image when BackgroundImageScaleType is set to [Enum.ScaleType.Slice](/docs/en-us/reference/engine/enums/ScaleType#Slice) . |

#### [Name tag](#name-tag)[](#name-tag)

| NameTagColor | | A [Color3](/docs/en-us/reference/engine/datatypes/Color3)  for the bar showing which player is being interacted with. |
| NameUnderlineColor | | A [Color3](/docs/en-us/reference/engine/datatypes/Color3)  for the thin line between the name tag and action buttons. |

#### [Button frame](#button-frame)[](#button-frame)

| ButtonFrameColor | | A [Color3](/docs/en-us/reference/engine/datatypes/Color3)  for the section (frame) containing the action buttons. |
| ButtonFrameTransparency  | | Transparency value (0–1) for the button frame section. |

#### [Button](#button)[](#button)

| ButtonColor | | A [Color3](/docs/en-us/reference/engine/datatypes/Color3)  for the background of the ACM action buttons. |
| ButtonTransparency | | Transparency value (0–1) for the background color of the action buttons. |
| ButtonHoverColor | | A [Color3](/docs/en-us/reference/engine/datatypes/Color3)  for the "hover" state of the action buttons. |
| ButtonHoverTransparency | | Transparency value (0–1) for the "hover" color of the action buttons. |
| ButtonUnderlineColor | | A [Color3](/docs/en-us/reference/engine/datatypes/Color3)  for the thin line which separates each action button. |
| ButtonImage | | A valid asset ID of an image for the background of buttons. |
| ButtonImageScaleType | | A [Enum.ScaleType](/docs/en-us/reference/engine/enums/ScaleType)  enum for button image scaling. |
| ButtonImageSliceCenter | | A [Rect](/docs/en-us/reference/engine/datatypes/Rect)  specifying the center of a nine-slice image when ButtonImageScaleType is set to [Enum.ScaleType.Slice](/docs/en-us/reference/engine/enums/ScaleType#Slice) . |

#### [Text](#text)[](#text)

| Font | | A [Enum.Font](/docs/en-us/reference/engine/enums/Font)  enum value for the name tag and button text. |
| TextColor | | A [Color3](/docs/en-us/reference/engine/datatypes/Color3)  for all text within the ACM. |
| TextScale | | A float value to scale the default text sizes of each element. |

#### [Various image](#various-image)[](#various-image)

| LeaveMenuImage | | An asset ID of an image for the ACM close button. |
| ScrollLeftImage | | An asset ID of an image for the carousel "scroll left" button. |
| ScrollRightImage | | A valid asset ID of an image for the carousel "scroll right" button. |

#### [Selected character](#selected-character)[](#selected-character)

| SelectedCharacterIndicator | | The [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  which floats above a character's head to indicate they are selected. |

#### [Size and position](#size-and-position)[](#size-and-position)

| Size | | A [UDim2](/docs/en-us/reference/engine/datatypes/UDim2)  for the overall size of the ACM. |
| MinSize | | A [Vector2](/docs/en-us/reference/engine/datatypes/Vector2)  specifying the minimum size of the ACM. |
| MaxSize | | A [Vector2](/docs/en-us/reference/engine/datatypes/Vector2)  specifying the maximum size of the ACM. |
| AspectRatio | | A float value specifying the relative width and height of the ACM. |
| AnchorPoint | | The [AnchorPoint](/docs/en-us/reference/engine/classes/GuiObject#AnchorPoint)  of the ACM. |
| OnScreenPosition | | A [UDim2](/docs/en-us/reference/engine/datatypes/UDim2)  specifying the on-screen position of the ACM (the position where it tweens to when opened). |
| OffScreenPosition | | A [UDim2](/docs/en-us/reference/engine/datatypes/UDim2)  specifying the off-screen position of the ACM (the position where it tweens from/to when opened/closed). |

### [Example customization](#example-customization)[](#example-customization)

The following code sample customizes the ACM theme using some basic parameters:

```

local StarterGui = game:GetService("StarterGui")

StarterGui:SetCore("AvatarContextMenuTheme", {

	BackgroundImage = "",

	BackgroundTransparency = 0.5,

	BackgroundColor = Color3.fromRGB(111, 145, 242),

	NameTagColor = Color3.fromRGB(0, 0, 200),

	NameUnderlineColor = Color3.fromRGB(213, 233, 255),

	ButtonFrameColor = Color3.fromRGB(15, 24, 65),

	ButtonFrameTransparency = 0.2,

	ButtonUnderlineColor = Color3.fromRGB(213, 233, 255),

	Font = Enum.Font.SciFi

})

```

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/context-menu/Custom-ACM.png)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
