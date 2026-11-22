<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/BasePlayerGui -->

BasePlayerGui | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [BasePlayerGui](/docs/nl-nl/reference/engine/classes/BasePlayerGui)

Nederlands

Feedback

Engine-klasse

BasePlayerGui

Niet maakbaar

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/BasePlayerGui)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[GetGuiObjectsAtPosition](#GetGuiObjectsAtPosition) (x :  [number](/docs/nl-nl/luau/numbers) , y :  [number](/docs/nl-nl/luau/numbers) ) : Instances

 |
| --- | --- |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Overgenomen door

[CoreGui](/docs/nl-nl/reference/engine/classes/CoreGui) , [PlayerGui](/docs/nl-nl/reference/engine/classes/PlayerGui) , [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui)

---

API-referentie

Methoden

GetGuiObjectsAtPosition

Mogelijkheden: UI

BasePlayerGui:GetGuiObjectsAtPosition (

x :[number](/docs/nl-nl/luau/numbers) , y :[number](/docs/nl-nl/luau/numbers)

) : Instances

Parameters

|

x :[number](/docs/nl-nl/luau/numbers)

 |
|

y :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

Instances

Codevoorbeelden

Geselecteerde GUIs op een Positie

```

local UserInputService = game:GetService("UserInputService")

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local playerGui = player:WaitForChild("PlayerGui")

-- Maak een Map en ScreenGui om de highlight Frames te bevatten

local highlights = Instance.new("Folder")

highlights.Name = "Highlights"

highlights.Parent = playerGui

local highlightsContainer = Instance.new("ScreenGui")

highlightsContainer.Name = "Container"

highlightsContainer.Parent = highlights

highlightsContainer.DisplayOrder = 99999

-- Creëert een semi-transparante gele Frame bovenop de gui met dezelfde AbsoluteSize en AbsolutePosition

local function highlightAsFrame(gui)

	local highlight = Instance.new("Frame")

	highlight.Name = "Highlight"

	highlight.Parent = highlightsContainer

	highlight.Size = UDim2.new(0, gui.AbsoluteSize.X, 0, gui.AbsoluteSize.Y)

	highlight.Position = UDim2.new(0, gui.AbsolutePosition.X, 0, gui.AbsolutePosition.Y)

	highlight.BackgroundColor3 = Color3.fromRGB(255, 255, 10) -- Geel

	highlight.BackgroundTransparency = 0.75

	highlight.BorderSizePixel = 0

	highlight.LayoutOrder = gui.LayoutOrder - 1

end

-- Gebruik GetGuiObjectsAtPosition om alle GuiObjects op de positie van de invoer te krijgen en te highlighten

local function highlightGui(input, _gameProcessed)

	local pos = input.Position

	local guisAtPosition = playerGui:GetGuiObjectsAtPosition(pos.X, pos.Y)

	highlightsContainer:ClearAllChildren()

	for _, gui in ipairs(guisAtPosition) do

		if gui:IsA("GuiObject") then

			highlightAsFrame(gui)

		end

	end

end

-- Voer highlightGui uit bij InputBegan als de invoer van het type MouseButton1 of Touch is

local function InputBegan(input, gameProcessed)

	local inputType = input.UserInputType

	local touch = Enum.UserInputType.Touch

	local mouse1 = Enum.UserInputType.MouseButton1

	if inputType == touch or inputType == mouse1 then

		highlightGui(input, gameProcessed)

	end

end

UserInputService.InputBegan:Connect(InputBegan)

```

Feedback geven

---

Ga naar

▼

BasePlayerGui

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[GetGuiObjectsAtPosition()](#GetGuiObjectsAtPosition)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
