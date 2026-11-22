<!-- Source: https://create.roblox.com/docs/reference/engine/classes/GamepadService -->

GamepadService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/GamepadService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [GamepadService](/docs/reference/engine/classes/GamepadService)

English

Feedback

Engine Class

GamepadService

Not Creatable

Service

Not Replicated

---

## Summary

Properties

|

[GamepadCursorEnabled](#GamepadCursorEnabled) :[boolean](/docs/luau/booleans)

 |
| --- | --- |

Methods

|

[DisableGamepadCursor](#DisableGamepadCursor) () : ()

 |
|

[EnableGamepadCursor](#EnableGamepadCursor) (guiObject :  [GuiObject](/docs/reference/engine/classes/GuiObject) ? ) : ()

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Properties

GamepadCursorEnabled

Roblox Script Security

Read Parallel

Capabilities: Input

GamepadService.GamepadCursorEnabled :[boolean](/docs/luau/booleans)

Code Samples

GamepadService - Gamepad Cursor Enabled Property

```

local gamepadService = game.GamepadService

gamepadService:GetPropertyChangedSignal("GamepadCursorEnabled"):Connect(function()

	local enabled = gamepadService.GamepadCursorEnabled

	if enabled then

	-- Custom code when the virtual cursor is enabled

	else

		-- Custom code when the virtual cursor is disabled

	end

end)

```

Provide feedback

---

Methods

DisableGamepadCursor

Capabilities: Input

GamepadService:DisableGamepadCursor () : ()

Returns

()

Code Samples

GamepadService - Disable Gamepad Cursor

```

local gamepadService = game.GamepadService

local userInputService = game.UserInputService

userInputService.InputBegan:Connect(function(inputObject, gameProcessed)

	if inputObject.KeyCode == Enum.KeyCode.ButtonB then

		gamepadService:DisableGamepadCursor()

	end

end)

```

Provide feedback

---

EnableGamepadCursor

Capabilities: Input

GamepadService:EnableGamepadCursor (guiObject :[GuiObject](/docs/reference/engine/classes/GuiObject) ? ) : ()

Parameters

|

guiObject :[GuiObject](/docs/reference/engine/classes/GuiObject) ?

Default Value: nil |

Returns

()

Code Samples

GamepadService - Enable Gamepad Cursor

```

local gamepadService = game.GamepadService

local userInputService = game.UserInputService

local startObject = script.Parent

userInputService.InputBegan:Connect(function(inputObject, gameProcessed)

	if inputObject.KeyCode == Enum.KeyCode.ButtonA then

		gamepadService:EnableGamepadCursor(startObject)

	end

end)

```

Provide feedback

---

Jump to

▼

GamepadService

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[GamepadCursorEnabled](#GamepadCursorEnabled)

[Methods](#methods)

[DisableGamepadCursor()](#DisableGamepadCursor)

[EnableGamepadCursor()](#EnableGamepadCursor)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
