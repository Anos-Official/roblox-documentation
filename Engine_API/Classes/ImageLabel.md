<!-- Source: https://create.roblox.com/docs/reference/engine/classes/ImageLabel -->

ImageLabel | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/ImageLabel.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [GuiBase](/docs/reference/engine/classes/GuiBase)
8. /
9. [GuiBase2d](/docs/reference/engine/classes/GuiBase2d)
10. /
11. [GuiObject](/docs/reference/engine/classes/GuiObject)
12. /
13. [GuiLabel](/docs/reference/engine/classes/GuiLabel)
14. /
15. [ImageLabel](/docs/reference/engine/classes/ImageLabel)

English

Feedback

Engine Class

ImageLabel

---

## Summary

Properties

|

[Image](#Image) : ContentId

 |
| --- | --- |
|

[ImageColor3](#ImageColor3) :[Color3](/docs/reference/engine/datatypes/Color3)

 |
|

[ImageContent](#ImageContent) :[Content](/docs/reference/engine/datatypes/Content)

 |
|

[ImageRectOffset](#ImageRectOffset) :[Vector2](/docs/reference/engine/datatypes/Vector2)

 |
|

[ImageRectSize](#ImageRectSize) :[Vector2](/docs/reference/engine/datatypes/Vector2)

 |
|

[ImageTransparency](#ImageTransparency) :[number](/docs/luau/numbers)

 |
|

[IsLoaded](#IsLoaded) :[boolean](/docs/luau/booleans)

 |
|

[ResampleMode](#ResampleMode) :[Enum.ResamplerMode](/docs/reference/engine/enums/ResamplerMode)

 |
|

[ScaleType](#ScaleType) :[Enum.ScaleType](/docs/reference/engine/enums/ScaleType)

 |
|

[SliceCenter](#SliceCenter) :[Rect](/docs/reference/engine/datatypes/Rect)

 |
|

[SliceScale](#SliceScale) :[number](/docs/luau/numbers)

 |
|

[TileSize](#TileSize) :[UDim2](/docs/reference/engine/datatypes/UDim2)

 |

Inherited Members

51  inherited from [GuiObject](/docs/reference/engine/classes/GuiObject)

12  inherited from [GuiBase2d](/docs/reference/engine/classes/GuiBase2d)

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Properties

Image

Read Parallel

Capabilities: UI

ImageLabel.Image : ContentId

Provide feedback

---

ImageColor3

Read Parallel

Capabilities: UI

ImageLabel.ImageColor3 :[Color3](/docs/reference/engine/datatypes/Color3)

Provide feedback

---

ImageContent

Read Parallel

Capabilities: UI

ImageLabel.ImageContent :[Content](/docs/reference/engine/datatypes/Content)

Provide feedback

---

ImageRectOffset

Read Parallel

Capabilities: UI

ImageLabel.ImageRectOffset :[Vector2](/docs/reference/engine/datatypes/Vector2)

Provide feedback

---

ImageRectSize

Read Parallel

Capabilities: UI

ImageLabel.ImageRectSize :[Vector2](/docs/reference/engine/datatypes/Vector2)

Provide feedback

---

ImageTransparency

Read Parallel

Capabilities: UI

ImageLabel.ImageTransparency :[number](/docs/luau/numbers)

Code Samples

Oscillate ImageTransparency

```

local RunService = game:GetService("RunService")

local imageLabel = script.Parent

local function onRenderStep()

	-- Oscillate ImageTransparency from 0 to 1 using a sine wave

	imageLabel.ImageTransparency = math.sin(workspace.DistributedGameTime * math.pi) * 0.5 + 0.5

end

RunService.RenderStepped:Connect(onRenderStep)

```

Provide feedback

---

IsLoaded

Read Only

Not Replicated

Read Parallel

Capabilities: UI

ImageLabel.IsLoaded :[boolean](/docs/luau/booleans)

Code Samples

Image Load Time

```

local imageLabel = script.Parent

local startTime = workspace.DistributedGameTime

-- Wait for the image to load

while not imageLabel.IsLoaded do

	task.wait()

end

-- Measure and display how long it took to load

local deltaTime = workspace.DistributedGameTime - startTime

print(("Image loaded in %.3f seconds"):format(deltaTime))

```

Provide feedback

---

ResampleMode

Read Parallel

Capabilities: UI

ImageLabel.ResampleMode :[Enum.ResamplerMode](/docs/reference/engine/enums/ResamplerMode)

Provide feedback

---

ScaleType

Read Parallel

Capabilities: UI

ImageLabel.ScaleType :[Enum.ScaleType](/docs/reference/engine/enums/ScaleType)

Provide feedback

---

SliceCenter

Read Parallel

Capabilities: UI

ImageLabel.SliceCenter :[Rect](/docs/reference/engine/datatypes/Rect)

Provide feedback

---

SliceScale

Read Parallel

Capabilities: UI

ImageLabel.SliceScale :[number](/docs/luau/numbers)

Provide feedback

---

TileSize

Read Parallel

Capabilities: UI

ImageLabel.TileSize :[UDim2](/docs/reference/engine/datatypes/UDim2)

Code Samples

Image ScaleType Demo

```

local imageLabel = script.Parent

-- Set the source image to be a 64x64 padlock

imageLabel.Image = "rbxassetid://284402752"

imageLabel.BackgroundTransparency = 0

imageLabel.BackgroundColor3 = Color3.new(1, 1, 1) -- White

imageLabel.ImageColor3 = Color3.new(0, 0, 0) -- Black

local function resizeInACircle()

	for theta = 0, 2, 0.02 do

		imageLabel.Size =

			UDim2.new(0, 100 + math.cos(theta * 2 * math.pi) * 50, 0, 100 + math.sin(theta * 2 * math.pi) * 50)

		task.wait()

	end

end

while true do

	-- Stretch simply stretches the source image to fit

	-- the UI element's space

	imageLabel.ScaleType = Enum.ScaleType.Stretch

	resizeInACircle()

	-- Tile will render the source image multiple times

	-- enough to fill the UI element's space

	imageLabel.ScaleType = Enum.ScaleType.Tile

	imageLabel.TileSize = UDim2.new(0, 64, 0, 64)

	resizeInACircle()

	-- Slice will turn the image into a nine-slice UI.

	imageLabel.ScaleType = Enum.ScaleType.Slice

	imageLabel.SliceCenter = Rect.new(30, 30, 34, 34)

	resizeInACircle()

end

```

Provide feedback

---

Jump to

▼

ImageLabel

[Summary](#summary)

[Properties](#summary-properties)

[Properties](#properties)

[Image](#Image)

[ImageColor3](#ImageColor3)

[ImageContent](#ImageContent)

[ImageRectOffset](#ImageRectOffset)

[ImageRectSize](#ImageRectSize)

[ImageTransparency](#ImageTransparency)

[IsLoaded](#IsLoaded)

[ResampleMode](#ResampleMode)

[ScaleType](#ScaleType)

[SliceCenter](#SliceCenter)

[SliceScale](#SliceScale)

[TileSize](#TileSize)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
