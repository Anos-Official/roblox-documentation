<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/UIScale -->

UIScale | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/UIScale.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [UIBase](/docs/en-us/reference/engine/classes/UIBase)
8. /
9. [UIComponent](/docs/en-us/reference/engine/classes/UIComponent)
10. /
11. [UIScale](/docs/en-us/reference/engine/classes/UIScale)

English

Feedback

Engine Class

UIScale

---

## Summary

Properties

|

[Scale](#Scale) :[number](/docs/en-us/luau/numbers)

 |
| --- | --- |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

UI Scale Demo

```

-- Lay out the images in a list

Instance.new("UIListLayout", script.Parent).SortOrder = Enum.SortOrder.LayoutOrder

-- Create some images of varying sizes using UIScale objects

for size = 0.2, 1.5, 0.2 do

	local image = Instance.new("ImageLabel")

	image.Image = "rbxassetid://284402752" -- an image of a Lock

	image.Parent = script.Parent

	image.Size = UDim2.new(0, 100, 0, 100)

	-- Scale the image by adding a UIScale with the size

	--  Note: this is a shorthand since we don't need a reference to the UIScale

	Instance.new("UIScale", image).Scale = size

end

```

---

API Reference

Properties

Scale

Read Parallel

Capabilities: UI

UIScale.Scale :[number](/docs/en-us/luau/numbers)

Code Samples

UI Scale Demo

```

-- Lay out the images in a list

Instance.new("UIListLayout", script.Parent).SortOrder = Enum.SortOrder.LayoutOrder

-- Create some images of varying sizes using UIScale objects

for size = 0.2, 1.5, 0.2 do

	local image = Instance.new("ImageLabel")

	image.Image = "rbxassetid://284402752" -- an image of a Lock

	image.Parent = script.Parent

	image.Size = UDim2.new(0, 100, 0, 100)

	-- Scale the image by adding a UIScale with the size

	--  Note: this is a shorthand since we don't need a reference to the UIScale

	Instance.new("UIScale", image).Scale = size

end

```

Provide feedback

---

Jump to

▼

UIScale

[Summary](#summary)

[Properties](#summary-properties)

[Properties](#properties)

[Scale](#Scale)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
