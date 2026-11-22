<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/GamepadService -->

GamepadService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [GamepadService](/docs/nl-nl/reference/engine/classes/GamepadService)

Nederlands

Feedback

Engine-klasse

GamepadService

Niet maakbaar

Service

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/GamepadService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[GamepadCursorEnabled](#GamepadCursorEnabled) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |

Methoden

|

[DisableGamepadCursor](#DisableGamepadCursor) () : ()

 |
|

[EnableGamepadCursor](#EnableGamepadCursor) (guiObject :  [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject) ? ) : ()

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

GamepadCursorEnabled

Roblox-scriptbeveiliging

Parallel lezen

Mogelijkheden: Input

GamepadService.GamepadCursorEnabled :[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

GamepadService - Eigenschap voor ingeschakelde gamepadcursor

```

local gamepadService = game.GamepadService

gamepadService:GetPropertyChangedSignal("GamepadCursorEnabled"):Connect(function()

	local enabled = gamepadService.GamepadCursorEnabled

	if enabled then

	-- Aangepaste code wanneer de virtuele cursor is ingeschakeld

	else

		-- Aangepaste code wanneer de virtuele cursor is uitgeschakeld

	end

end)

```

Feedback geven

---

Methoden

DisableGamepadCursor

Mogelijkheden: Input

GamepadService:DisableGamepadCursor () : ()

Teruggaves

()

Codevoorbeelden

GamepadService - Schakel Gamepad Cursor uit

```

local gamepadService = game.GamepadService

local userInputService = game.UserInputService

userInputService.InputBegan:Connect(function(inputObject, gameProcessed)

	if inputObject.KeyCode == Enum.KeyCode.ButtonB then

		gamepadService:DisableGamepadCursor()

	end

end)

```

Feedback geven

---

EnableGamepadCursor

Mogelijkheden: Input

GamepadService:EnableGamepadCursor (guiObject :[GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject) ? ) : ()

Parameters

|

guiObject :[GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject) ?

Standaardwaarde: nil |

Teruggaves

()

Codevoorbeelden

GamepadService - Schakel Gamepad Cursor In

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

Feedback geven

---

Ga naar

▼

GamepadService

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[GamepadCursorEnabled](#GamepadCursorEnabled)

[Methoden](#methods)

[DisableGamepadCursor()](#DisableGamepadCursor)

[EnableGamepadCursor()](#EnableGamepadCursor)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
