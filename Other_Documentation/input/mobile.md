<!-- Source: https://create.roblox.com/docs/input/mobile -->

Mobile input | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/input/mobile.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Input](/docs/input)

# Mobile input

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/input/mobile.md)

The majority of Roblox sessions are played on mobile devices, so it's important to consider the mobile [device orientation](#device-orientation)  and other [cross‑platform](/docs/projects/cross-platform)  factors when designing a game for a wide audience.

To simplify cross‑platform inputs, including player interaction with virtual buttons, Roblox provides the [Input Action System](/docs/input/input-action-system)  to define actions  such as "jump," "sprint," or "shoot" and set up bindings  for multiple hardware inputs to drive those actions.

Roblox also supports native mobile features like [haptic feedback](#haptic-feedback) , touch gestures such as [TouchSwipe](/docs/reference/engine/classes/UserInputService#TouchSwipe)  and [TouchPinch](/docs/reference/engine/classes/UserInputService#TouchPinch) , or accelerometer and gyroscope functionality on [AccelerometerEnabled](/docs/reference/engine/classes/UserInputService#AccelerometerEnabled)  and [GyroscopeEnabled](/docs/reference/engine/classes/UserInputService#GyroscopeEnabled)  devices.

## [Input type detection](#input-type-detection)[](#input-type-detection)

In cross‑platform development, it's important that you determine and respond to the [PreferredInput](/docs/reference/engine/classes/UserInputService#PreferredInput)  type a player is using, normally to ensure that [UI elements](/docs/ui#ui-objects)  like on-screen buttons and menus work elegantly and support interaction across devices.

For example, a touch-enabled device assumes touch is the default input and that touch-buttons may appear for actions, but a player may choose to connect a bluetooth gamepad. In this case, touch remains a valid input, but you can assume the player wants to switch to the connected gamepad as the primary  input type and possibly use touch as a backup input for on-screen UI.

See [input type detection](/docs/input#input-type-detection)  for more information.

## [Device orientation](#device-orientation)[](#device-orientation)

By default, Roblox games run in landscape  mode, allowing the game to switch between landscape "left" and landscape "right" as the player's device rotates. However, games can be locked to a particular orientation if desired.

There are five different orientation modes, including two sensor-based modes and three locked modes.¹ Each of these can be set as the default  orientation through [StarterGui.ScreenOrientation](/docs/reference/engine/classes/StarterGui#ScreenOrientation) , accessible through Studio's [Properties](/docs/studio/properties)  window.

| Sensor Modes |
| --- | --- |
| [LandscapeSensor](/docs/reference/engine/enums/ScreenOrientation) | | The default Roblox setting in which the game always appears in landscape mode (no portrait mode) and the device detects its physical orientation to ensure the game view is always oriented upward. |
| [Sensor](/docs/reference/engine/enums/ScreenOrientation) | | The device detects its physical orientation to ensure the game view is always oriented upward, switching between landscape and portrait mode as needed. |
| Locked Modes |
| [LandscapeLeft](/docs/reference/engine/enums/ScreenOrientation) | | On devices with a virtual home/nav bar, its touch region is at the bottom of the display. On devices with a physical home button, the home button is to the left of the display. |
| [LandscapeRight](/docs/reference/engine/enums/ScreenOrientation) | | On devices with a virtual home/nav bar, its touch region is at the bottom of the display. On devices with a physical home button, the home button is to the right of the display. |
| [Portrait](/docs/reference/engine/enums/ScreenOrientation) | | On devices with a virtual home/nav bar, its touch region is at the bottom of the display. On devices with a physical home button, the home button is below the display. |

 ¹ Roblox does not include a "portrait upside-down" mode since many devices do not natively support that orientation

Beyond the default [StarterGui.ScreenOrientation](/docs/reference/engine/classes/StarterGui#ScreenOrientation)  property, you can change orientation during gameplay through [PlayerGui.ScreenOrientation](/docs/reference/engine/classes/PlayerGui#ScreenOrientation) . This can be useful when a game needs to enforce an orientation, such as locking the view to [Portrait](/docs/reference/engine/enums/ScreenOrientation)  for a minigame.

The following code in a [LocalScript](/docs/reference/engine/classes/LocalScript)  sets the screen orientation to portrait after a short delay:

LocalScript - Change Screen Orientation to Portrait

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local playerGui = player.PlayerGui

task.wait(5)

playerGui.ScreenOrientation = Enum.ScreenOrientation.Portrait

```

Finally, you can detect changes to screen orientation during gameplay by listening to value changes on the [PlayerGui.CurrentScreenOrientation](/docs/reference/engine/classes/PlayerGui#CurrentScreenOrientation)  property.

LocalScript - Detect Screen Orientation Changes

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local playerGui = player.PlayerGui

local function onOrientationChange()

	print("Orientation changed to", playerGui.ScreenOrientation)

end

playerGui:GetPropertyChangedSignal("ScreenOrientation"):Connect(onOrientationChange)

```

## [Haptic feedback](#haptic-feedback)[](#haptic-feedback)

Most mobile devices have motors built in to provide haptic feedback. Adding rumbles and vibrations can greatly enhance a player's experience and provide subtle feedback beyond visuals or audio.

Roblox supports haptics for haptic-capable devices including most iPhone, Pixel, and Samsung Galaxy devices. Haptic feedback is managed through [HapticEffect](/docs/reference/engine/classes/HapticEffect)  instances which can be set to a specific [Type](/docs/reference/engine/classes/HapticEffect#Type)  such as [GameplayCollision](/docs/reference/engine/enums/HapticEffectType)  or [UIClick](/docs/reference/engine/enums/HapticEffectType) .

Once a [HapticEffect](/docs/reference/engine/classes/HapticEffect)  is in place, you can initiate it through the [Play()](/docs/reference/engine/classes/HapticEffect#Play)  method, for instance:

```

local Workspace = game:GetService("Workspace")

local effect = Instance.new("HapticEffect")

effect.Type = Enum.HapticEffectType.GameplayExplosion

effect.Parent = Workspace

-- Play the haptic effect

effect:Play()

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
