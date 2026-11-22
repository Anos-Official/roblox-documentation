<!-- Source: https://create.roblox.com/docs/en-us/resources/boneheads/character-controller.md -->

---
title: "Character controls"
url: /docs/en-us/resources/boneheads/character-controller
last_updated: 2026-11-20T18:47:27Z
description: "Explains how Boneheads builds carrying, dropping, throwing, wearing, and emotes as custom Character Controller Library abilities."
---

# Character controls

[**Boneheads**](https://github.com/Roblox/resources/tree/main/experiences/boneheads) uses the [Character Controller Library](/docs/en-us/characters/character-controller-library.md) (CCL) for all player input and custom abilities: picking up or stealing an object, charging a throw, exchanging a head or an item of clothing, waving at a friend, and more. Custom abilities run alongside standard abilities such as running and jumping. Climbing, swimming, sprinting, crouching, slipping, falling over, and standing up are disabled as CCL abilities, not as `Class.Humanoid` states.

Under [Server Authority](/docs/en-us/projects/server-authority.md), CCL ability callbacks can run in both the predicted client and the authoritative server simulation. Pickup, stealing, and clothing changes stay on the server. Throw release runs in both simulations, and the server result wins when they disagree.

| Ability | Default Action Slot | Associated Inputs |
| --- | --- | --- |
| [**Carry**](#grab-drop-and-throw-with-one-input), [**Drop**](#grab-drop-and-throw-with-one-input), [**Throw**](#grab-drop-and-throw-with-one-input) | `5` | `Enum.KeyCode.MouseLeftButton\|MouseLeftButton`, `Enum.KeyCode.ButtonR2\|ButtonR2` |
| [**Wear**](#swap-heads-and-clothing-on-the-server) | `6` | `Enum.KeyCode.Q\|Q`, `Enum.KeyCode.ButtonY\|ButtonY` |
| [**Emote**](#emote-with-built-in-ground-sensor) | `7` | `Enum.KeyCode.X\|X`, `Enum.KeyCode.ButtonR1\|ButtonR1` |

## Grab, drop, and throw with one input

Three custom abilities share `InputName = "Interact"` and action slot `5`. **Carry** uses `Press` mode and runs when the input begins. If the character's hands are empty, the server searches for the nearest free carryable, then searches for an object held by another player. **Carry** also sets a `0.3`‑second `DropDebounce` label so that **Drop** and **Throw** can't start on the same press that picked the object up.

```lua
local ACTION_SLOT = 5

local Carry: AvatarAbilities.AbilityDefinition = {
	Name = "Carry",
	Input = {
		InputName = "Interact",
		Mode = "Press",
		ActionSlot = ACTION_SLOT,
		CustomIcon = "rbxassetid://71984145361462",
		CustomIconActive = "rbxassetid://101534439290003",
	},
	State = {
		handsEmptyAtStart = Constants.INVALID_STATE_VALUE,
	},
	RunsWhile = Rule.Any("DropDebounce", "Carrying"),
	TimedLabels = {
		OnStart = { DropDebounce = 0.3 },
	},
}
```

**Drop** and **Throw** use `Hold` mode and start only while the `Carrying` sensor is active and the `DropDebounce` label is absent. Both abilities create a `0.2`‑second timed label (`DropWindow` and `ThrowThreshold` respectively) so that, when the player releases the input, a hold duration of less than `0.2` seconds drops the object while a longer hold duration begins the throw charge‑up.

```lua
local ACTION_SLOT = 5

local Drop: AvatarAbilities.AbilityDefinition = {
	Name = "Drop",
	Input = {
		InputName = "Interact",
		Mode = "Hold",
		ActionSlot = ACTION_SLOT,
		CustomIcon = "rbxassetid://71984145361462",
		CustomIconActive = "rbxassetid://101534439290003",
	},
	StartsWhen = Rule.All("Carrying", Rule.Not("DropDebounce")),
	RunsWhile = Rule.All("Carrying"),
	TimedLabels = {
		OnStart = { DropWindow = 0.2 },
	},
}
```

```lua
local ACTION_SLOT = 5

local Throw: AvatarAbilities.AbilityDefinition = {
	Name = "Interact",
	Input = {
		InputName = "Interact",
		Mode = "Hold",
		ActionSlot = ACTION_SLOT,
		CustomIcon = "rbxassetid://71984145361462",
		CustomIconActive = "rbxassetid://101534439290003",
	},

	State = {
		chargeStart = Constants.INVALID_STATE_VALUE,
	},
	StartsWhen = Rule.All("Carrying", Rule.Not("DropDebounce")),
	RunsWhile = Rule.All("Carrying"),
	TimedLabels = {
		OnStart = { ThrowThreshold = 0.2 },
	},
}
```

## Swap heads and clothing on the server

**Wear** uses `Hold` mode on action slot `6`. Its world changes run only on the server, inside `OnStart()`. A held head or non‑clothing prop moves into the head slot and ejects the current head. With empty hands, a worn head moves into the hands. Otherwise the server defers clothing removal unless a pickup is already pending.

```lua
local ACTION_SLOT = 6

local Wear: AvatarAbilities.AbilityDefinition = {
	Name = "Wear",
	Input = {
		InputName = "Wear",
		Mode = "Hold",
		ActionSlot = ACTION_SLOT,
		CustomIcon = "rbxassetid://116517673048325",
		CustomIconActive = "rbxassetid://108395972232389",
	},
}
```

## Emote with built-in ground sensor

**Emote** uses `Toggle` mode on action slot `7`. It starts only while the character is grounded (`Sensor.Ground`), is stationary (`Not(Sensor.IsMoving)`), and is outside a cooldown (`Not("EmoteCooldown")`).

The client opens the menu when the ability starts and defers closing it when the ability stops. The server validates the client‑side selection and plays the animation in that handler. `OnUpdate()` stops the emote ability when the character starts moving and, when the ability stops, `TimedLabels.OnStop` sets a `0.1`‑second `EmoteCooldown`.

```lua
local ACTION_SLOT = 7
local STOP_ABILITY_VALUE = -1

local Emote: AvatarAbilities.AbilityDefinition = {
	Name = ABILITY_NAME,
	RunsWhile = All(Sensor.Ground),
	StartsWhen = All(Not("EmoteCooldown"), Sensor.Ground, Not(Sensor.IsMoving)),
	RequiresSensors = { Sensor.Ground, Sensor.IsMoving },
	Updates = "onSensorChange",
	Input = {
		InputName = ABILITY_NAME,
		Mode = "Toggle",
		ActionSlot = ACTION_SLOT,
		CustomIcon = "rbxassetid://121802838137152",
		CustomIconActive = "rbxassetid://90425900536225",
	},
	TimedLabels = {
		OnStop = { EmoteCooldown = 0.1 },
	},
}
```