<!-- Source: https://create.roblox.com/docs/input -->

Input | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/input.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Input](/docs/input)

# Input

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/input/index.md)

Every game needs to receive user input for players to interact and view their environment. Roblox supports nearly all forms of input, including [mouse/keyboard](/docs/input/mouse-and-keyboard) , [touch](/docs/input/mobile) , [gamepads](/docs/input/gamepad) , and VR.

## [Cross-platform input](#cross-platform-input)[](#cross-platform-input)

Roblox is inherently [cross‑platform](/docs/projects/cross-platform) , as players can discover and join games on their phone or tablet, then later continue where they left off on their PC or console. Input is especially important as part of your cross‑platform development plan.

To simplify this process, Roblox provides the [Input Action System](/docs/input/input-action-system)  to define actions  such as "jump," "sprint," or "shoot" and set up bindings  for multiple hardware inputs to drive those actions. This frees you from thinking of all the technical aspects of hardware inputs and allows you to simply define which inputs perform which actions.

 ![](https://prod.docsiteassets.roblox.com/assets/publishing/cross-platform/Input-Actions-Jump.png)

## [Input type detection](#input-type-detection)[](#input-type-detection)

In cross‑platform development, it's important that you determine and respond to the primary  input type a player is using, normally to ensure that [UI elements](/docs/ui#ui-objects)  like on‑screen buttons and menus work elegantly across devices.

For example, a touch‑enabled device assumes touch is the default input and that touch buttons may appear for actions, but if a player connects an additional bluetooth keyboard/mouse or gamepad, you can assume they want to switch to that as the primary  input type and possibly use touch as a backup input for on‑screen UI. The read‑only [UserInputService.PreferredInput](/docs/reference/engine/classes/UserInputService#PreferredInput)  property is a convenient way to test for and adapt to multiple input types across multiple device types, based on anticipated player behavior.

Behavior Benefits

The value of [PreferredInput](/docs/reference/engine/classes/UserInputService#PreferredInput)  changes based on built‑in device inputs and the player's most recent interaction with a connected gamepad or keyboard/mouse. Examples include:

| Real-World Scenario | | PreferredInput |
| --- | --- |
| Player is using a phone with no other connected input devices; no possibility of an input type change. | | [Touch](/docs/reference/engine/enums/PreferredInput) |
| Player is using a mobile device with a bluetooth keyboard & mouse connected, but no gamepad is connected. | | [KeyboardAndMouse](/docs/reference/engine/enums/PreferredInput) |
| Player is using a tablet with a bluetooth gamepad connected, but no keyboard or mouse is connected. | | [Gamepad](/docs/reference/engine/enums/PreferredInput) |
| Player is using an Xbox or PlayStation with a bluetooth keyboard & mouse connected and has most recently interacted with the keyboard or mouse. | | [KeyboardAndMouse](/docs/reference/engine/enums/PreferredInput) |
| Player is on a Windows or Mac PC with a gamepad connected and has most recently interacted with the gamepad. | | [Gamepad](/docs/reference/engine/enums/PreferredInput) |

The following [LocalScript](/docs/reference/engine/classes/LocalScript)  is a template for initially detecting the preferred input and responding to changes during gameplay.

PreferredInput detection

```

local UserInputService = game:GetService("UserInputService")

local function preferredInputChanged()

	local preferredInput = UserInputService.PreferredInput

	if preferredInput == Enum.PreferredInput.Touch then

		-- Player is on touch-enabled device with no other input types available/connected

		print("Touch")

	elseif preferredInput == Enum.PreferredInput.Gamepad then

		-- Player has connected or most recently interacted with a gamepad

		print("Gamepad")

	elseif preferredInput == Enum.PreferredInput.KeyboardAndMouse then

		-- Player has connected or most recently interacted with a keyboard or mouse

		print("KeyboardAndMouse")

	end

end

preferredInputChanged()

UserInputService:GetPropertyChangedSignal("PreferredInput"):Connect(function()

	preferredInputChanged()

end)

```

## [Default bindings](#default-bindings)[](#default-bindings)

Roblox provides default input bindings for movement, camera control, and basic environment interaction — Roblox players are familiar with these controls, so you should only override them in specific cases. Also note that the reserved  inputs cannot be overridden and will always operate with their intended purpose.

Roblox Reserved Character Interface / Inventory Camera

| Action | | Mouse/Keyboard | | Gamepad | | Touch |
| Open Roblox menu | | Esc | | Start  button ([ButtonStart](/docs/reference/engine/enums/KeyCode) ) | | N/A |
| [Developer Console](/docs/studio/developer-console) | | F9 | | N/A | | N/A |
| Fullscreen mode (Windows)
Show desktop (Mac) | | F11 | | N/A | | N/A |
| Record video (Windows) | | F12 | | N/A | | N/A |
| Take screenshot | | PrintScreen | | N/A | | N/A |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
