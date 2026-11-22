<!-- Source: https://create.roblox.com/docs/input/gamepad -->

Gamepad input | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/input/gamepad.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Input](/docs/input)

# Gamepad input

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/input/gamepad.md)

Roblox accepts input from gamepads such as Xbox and PlayStation controllers. To simplify [cross‑platform](/docs/projects/cross-platform)  inputs, including gamepads, Roblox provides the [Input Action System](/docs/input/input-action-system)  to define actions  such as "jump," "sprint," or "shoot" and set up bindings  for multiple hardware inputs to drive those actions.

When binding gamepad inputs, see [common control schemas](#common-control-schemas)  to create a consistent gamepad experience for players. After inputs are set, you can enhance the player's experience by including [haptic feedback](#haptic-feedback)  on supported controllers.

As you build out support for gamepads, remember to test frequently using a connected gamepad or the [Controller Emulator](#controller-emulation)  in Studio.

## [Input type detection](#input-type-detection)[](#input-type-detection)

In cross‑platform development, it's important that you determine and respond to the [PreferredInput](/docs/reference/engine/classes/UserInputService#PreferredInput)  type a player is using, normally to ensure that [UI elements](/docs/ui#ui-objects)  like on-screen buttons and menus work elegantly and support interaction across devices.

For example, a console assumes that gamepads are the default input, but a player on PC or laptop may also choose to connect a bluetooth gamepad. In this case, mouse/keyboard remains a valid input for that player, but you can assume they want to switch to the connected gamepad as the primary  input type.

See [input type detection](/docs/input#input-type-detection)  for more information.

For alternative gamepad detection methods, see the [UserInputService.GamepadEnabled](/docs/reference/engine/classes/UserInputService#GamepadEnabled)  property and the [GamepadConnected](/docs/reference/engine/classes/UserInputService#GamepadConnected) /[GamepadDisconnected](/docs/reference/engine/classes/UserInputService#GamepadDisconnected)  events.

## [Common control schemas](#common-control-schemas)[](#common-control-schemas)

When considering specific control bindings for the [Input Action System](/docs/input/input-action-system) , it's best to establish consistency across different games. The following input bindings will help players immediately feel familiar and comfortable with gamepad controls.

| Input | | Common use cases |
| --- | --- |
| [ButtonA](/docs/reference/engine/enums/KeyCode) | | Accepts player prompts or GUI selections. Alternatively used for primary actions such as jumping. |
| [ButtonB](/docs/reference/engine/enums/KeyCode) | | Cancels player prompts or GUI selections. Alternatively used for secondary actions such as a dodge, roll, or sprint. |
| [Thumbstick1](/docs/reference/engine/enums/KeyCode) | | Generally associated with character movement. |
| [Thumbstick2](/docs/reference/engine/enums/KeyCode) | | Generally associated with camera movement. |
| [ButtonL2](/docs/reference/engine/enums/KeyCode) , [ButtonR2](/docs/reference/engine/enums/KeyCode) | | Generally used for primary actions, such as shooting.  |
| [ButtonL1](/docs/reference/engine/enums/KeyCode) , [ButtonR1](/docs/reference/engine/enums/KeyCode) , [ButtonX](/docs/reference/engine/enums/KeyCode) , [ButtonY](/docs/reference/engine/enums/KeyCode) | | Secondary actions such as reloading, targeting, or accessing an inventory or minimap. |

Xbox PlayStation

![](https://prod.docsiteassets.roblox.com/assets/scripting/input/Gamepad-Inputs-Xbox.png)

## [Haptic feedback](#haptic-feedback)[](#haptic-feedback)

Many gamepad controllers have motors built in to provide haptic feedback. Adding rumbles and vibrations can greatly enhance a player's experience and provide subtle feedback beyond visuals or audio.

Roblox supports haptics for PlayStation gamepads, Xbox gamepads, and the Quest Touch controller. Haptic feedback is managed through [HapticEffect](/docs/reference/engine/classes/HapticEffect)  instances which can be set to a specific [Type](/docs/reference/engine/classes/HapticEffect#Type)  such as [GameplayCollision](/docs/reference/engine/enums/HapticEffectType)  or [UIClick](/docs/reference/engine/enums/HapticEffectType) .

Once a [HapticEffect](/docs/reference/engine/classes/HapticEffect)  is in place, you can initiate it through the [Play()](/docs/reference/engine/classes/HapticEffect#Play)  method, for instance:

```

local Workspace = game:GetService("Workspace")

local effect = Instance.new("HapticEffect")

effect.Type = Enum.HapticEffectType.GameplayExplosion

effect.Parent = Workspace

-- Play the haptic effect

effect:Play()

```

## [Controller emulation](#controller-emulation)[](#controller-emulation)

Use [Controller Emulator](/docs/studio/controller-emulator)  to test gamepad input directly in Studio without a physical controller connected. It shows a picture of the emulated device and lights up its controls as input arrives, which helps confirm that your [UserInputService](/docs/reference/engine/classes/UserInputService)  handlers and [Input Action System](/docs/input/input-action-system)  bindings react the way you expect.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
