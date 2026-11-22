<!-- Source: https://create.roblox.com/docs/input/mouse-and-keyboard -->

Mouse and keyboard input | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/input/mouse-and-keyboard.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Input](/docs/input)

# Mouse and keyboard input

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/input/mouse-and-keyboard.md)

A large percentage of Roblox sessions are played on devices with a mouse and keyboard, so it's important to support these inputs when designing a game for a wide audience.

To simplify [cross‑platform](/docs/projects/cross-platform)  inputs, including mouse/keyboard, Roblox provides the [Input Action System](/docs/input/input-action-system)  to define actions  such as "jump," "sprint," or "shoot" and set up bindings  for multiple hardware inputs to drive those actions.

Roblox also supports general mouse/keyboard input through [UserInputService](/docs/reference/engine/classes/UserInputService)  events like [InputBegan](/docs/reference/engine/classes/UserInputService#InputBegan)  and [InputEnded](/docs/reference/engine/classes/UserInputService#InputEnded)  and methods like [IsKeyDown()](/docs/reference/engine/classes/UserInputService#IsKeyDown)  to check if a particular key is pressed on a keyboard.

## [Input type detection](#input-type-detection)[](#input-type-detection)

In cross‑platform development, it's important that you determine and respond to the [PreferredInput](/docs/reference/engine/classes/UserInputService#PreferredInput)  type a player is using, normally to ensure that [UI elements](/docs/ui#ui-objects)  like on-screen buttons and menus work elegantly and support interaction across devices.

For example, a PC or laptop assumes mouse/keyboard is the default input, but a player may choose to connect a bluetooth gamepad. In this case, mouse/keyboard remains a valid input, but you can assume the player wants to switch to the connected gamepad as the primary  input type.

See [input type detection](/docs/input#input-type-detection)  for more information.

## [Generic mouse/key input](#generic-mousekey-input)[](#generic-mousekey-input)

Beyond the [Input Action System](/docs/input/input-action-system) , you can capture mouse and keyboard inputs using [UserInputService](/docs/reference/engine/classes/UserInputService) . The following [LocalScript](/docs/reference/engine/classes/LocalScript) , when placed in [StarterPlayerScripts](/docs/reference/engine/classes/StarterPlayerScripts) , captures the began and ended phases of key and mouse clicks and prints the result to the [Output](/docs/studio/output)  window.

LocalScript - Output Key/Mouse Began and Ended

```

local UserInputService = game:GetService("UserInputService")

local function onInputBegan(inputObject, processedEvent)

	-- Return if another script has already processed the input

	if processedEvent then return end

	print(inputObject.KeyCode.Name, "began!", inputObject.Position)

end

local function onInputEnded(inputObject, processedEvent)

	-- Return if another script has already processed the input

	if processedEvent then return end

	print(inputObject.KeyCode.Name, "ended!", inputObject.Position)

end

UserInputService.InputBegan:Connect(onInputBegan)

UserInputService.InputEnded:Connect(onInputEnded)

```

## [Mouse icon](#mouse-icon)[](#mouse-icon)

You can customize the appearance and behavior of a player's mouse icon within your game to create a cohesive style across all of your UI elements. This includes temporarily changing the player's mouse icon in specific circumstances, such as hovering over a button.

Change Icon Hide Icon Lock Icon

You can change the player's mouse icon in a [LocalScript](/docs/reference/engine/classes/LocalScript)  by setting the [MouseIcon](/docs/reference/engine/classes/UserInputService#MouseIcon)  property in [UserInputService](/docs/reference/engine/classes/UserInputService)  to a custom Roblox asset ID. For example, the following [LocalScript](/docs/reference/engine/classes/LocalScript)  changes the player's default mouse icon to a circle with a blue dot in the middle.

```

local UserInputService = game:GetService("UserInputService")

UserInputService.MouseIcon = "rbxassetid://3400146391"

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
