<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/UITableLayout -->

UITableLayout | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/UITableLayout.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

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
11. [UILayout](/docs/en-us/reference/engine/classes/UILayout)
12. /
13. [UIGridStyleLayout](/docs/en-us/reference/engine/classes/UIGridStyleLayout)
14. /
15. [UITableLayout](/docs/en-us/reference/engine/classes/UITableLayout)

English

Feedback

Engine Class

UITableLayout

---

## Summary

Properties

|

[FillEmptySpaceColumns](#FillEmptySpaceColumns) :[boolean](/docs/en-us/luau/booleans)

 |
| --- | --- |
|

[FillEmptySpaceRows](#FillEmptySpaceRows) :[boolean](/docs/en-us/luau/booleans)

 |
|

[MajorAxis](#MajorAxis) :[Enum.TableMajorAxis](/docs/en-us/reference/engine/enums/TableMajorAxis)

 |
|

[Padding](#Padding) :[UDim2](/docs/en-us/reference/engine/datatypes/UDim2)

 |

Inherited Members

7  inherited from [UIGridStyleLayout](/docs/en-us/reference/engine/classes/UIGridStyleLayout)

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Build UI Table

```

local frame = script.Parent

-- Table data

local headerWidth = { 200, 80, 80 }

local headers = {

	"Name",

	"Job",

	"Cash",

}

local data = {

	{ "Bob", "Waiter", 100 },

	{ "Lisa", "Police", 200 },

	{ "George", "-", 50 },

}

-- First, build the table layout

local uiTableLayout = Instance.new("UITableLayout")

uiTableLayout.FillDirection = Enum.FillDirection.Vertical

uiTableLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center

uiTableLayout.VerticalAlignment = Enum.VerticalAlignment.Center

uiTableLayout.FillEmptySpaceColumns = false

uiTableLayout.FillEmptySpaceRows = false

uiTableLayout.Padding = UDim2.new(0, 5, 0, 5)

uiTableLayout.SortOrder = Enum.SortOrder.LayoutOrder

frame.Size = UDim2.new(0, 0, 0, 40) -- The Size of the parent frame is the cell size

uiTableLayout.Parent = frame

-- Next, create column headers

local headerFrame = Instance.new("Frame")

headerFrame.Name = "Headers"

headerFrame.Parent = frame

for i = 1, #headers do

	local headerText = headers[i]

	local headerCell = Instance.new("TextLabel")

	headerCell.Text = headerText

	headerCell.Name = headerText

	headerCell.LayoutOrder = i

	headerCell.Size = UDim2.new(0, 0, 0, 24)

	headerCell.Parent = headerFrame

	local headerSize = Instance.new("UISizeConstraint")

	headerSize.MinSize = Vector2.new(headerWidth[i], 0)

	headerSize.Parent = headerCell

end

-- Finally, add data rows by iterating over each row and the columns in that row

for index, value in ipairs(data) do

	local rowData = value

	local rowFrame = Instance.new("Frame")

	rowFrame.Name = "Row" .. index

	rowFrame.Parent = frame

	for col = 1, #value do

		local cellData = rowData[col]

		local cell = Instance.new("TextLabel")

		cell.Text = cellData

		cell.Name = headers[col]

		cell.TextXAlignment = Enum.TextXAlignment.Left

		if tonumber(cellData) then -- If this cell is a number, right-align it instead

			cell.TextXAlignment = Enum.TextXAlignment.Right

		end

		cell.ClipsDescendants = true

		cell.Size = UDim2.new(0, 0, 0, 24)

		cell.Parent = rowFrame

	end

end

```

---

API Reference

Properties

FillEmptySpaceColumns

Read Parallel

Capabilities: UI

UITableLayout.FillEmptySpaceColumns :[boolean](/docs/en-us/luau/booleans)

Code Samples

Build UI Table

```

local frame = script.Parent

-- Table data

local headerWidth = { 200, 80, 80 }

local headers = {

	"Name",

	"Job",

	"Cash",

}

local data = {

	{ "Bob", "Waiter", 100 },

	{ "Lisa", "Police", 200 },

	{ "George", "-", 50 },

}

-- First, build the table layout

local uiTableLayout = Instance.new("UITableLayout")

uiTableLayout.FillDirection = Enum.FillDirection.Vertical

uiTableLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center

uiTableLayout.VerticalAlignment = Enum.VerticalAlignment.Center

uiTableLayout.FillEmptySpaceColumns = false

uiTableLayout.FillEmptySpaceRows = false

uiTableLayout.Padding = UDim2.new(0, 5, 0, 5)

uiTableLayout.SortOrder = Enum.SortOrder.LayoutOrder

frame.Size = UDim2.new(0, 0, 0, 40) -- The Size of the parent frame is the cell size

uiTableLayout.Parent = frame

-- Next, create column headers

local headerFrame = Instance.new("Frame")

headerFrame.Name = "Headers"

headerFrame.Parent = frame

for i = 1, #headers do

	local headerText = headers[i]

	local headerCell = Instance.new("TextLabel")

	headerCell.Text = headerText

	headerCell.Name = headerText

	headerCell.LayoutOrder = i

	headerCell.Size = UDim2.new(0, 0, 0, 24)

	headerCell.Parent = headerFrame

	local headerSize = Instance.new("UISizeConstraint")

	headerSize.MinSize = Vector2.new(headerWidth[i], 0)

	headerSize.Parent = headerCell

end

-- Finally, add data rows by iterating over each row and the columns in that row

for index, value in ipairs(data) do

	local rowData = value

	local rowFrame = Instance.new("Frame")

	rowFrame.Name = "Row" .. index

	rowFrame.Parent = frame

	for col = 1, #value do

		local cellData = rowData[col]

		local cell = Instance.new("TextLabel")

		cell.Text = cellData

		cell.Name = headers[col]

		cell.TextXAlignment = Enum.TextXAlignment.Left

		if tonumber(cellData) then -- If this cell is a number, right-align it instead

			cell.TextXAlignment = Enum.TextXAlignment.Right

		end

		cell.ClipsDescendants = true

		cell.Size = UDim2.new(0, 0, 0, 24)

		cell.Parent = rowFrame

	end

end

```

Provide feedback

---

FillEmptySpaceRows

Read Parallel

Capabilities: UI

UITableLayout.FillEmptySpaceRows :[boolean](/docs/en-us/luau/booleans)

Code Samples

Build UI Table

```

local frame = script.Parent

-- Table data

local headerWidth = { 200, 80, 80 }

local headers = {

	"Name",

	"Job",

	"Cash",

}

local data = {

	{ "Bob", "Waiter", 100 },

	{ "Lisa", "Police", 200 },

	{ "George", "-", 50 },

}

-- First, build the table layout

local uiTableLayout = Instance.new("UITableLayout")

uiTableLayout.FillDirection = Enum.FillDirection.Vertical

uiTableLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center

uiTableLayout.VerticalAlignment = Enum.VerticalAlignment.Center

uiTableLayout.FillEmptySpaceColumns = false

uiTableLayout.FillEmptySpaceRows = false

uiTableLayout.Padding = UDim2.new(0, 5, 0, 5)

uiTableLayout.SortOrder = Enum.SortOrder.LayoutOrder

frame.Size = UDim2.new(0, 0, 0, 40) -- The Size of the parent frame is the cell size

uiTableLayout.Parent = frame

-- Next, create column headers

local headerFrame = Instance.new("Frame")

headerFrame.Name = "Headers"

headerFrame.Parent = frame

for i = 1, #headers do

	local headerText = headers[i]

	local headerCell = Instance.new("TextLabel")

	headerCell.Text = headerText

	headerCell.Name = headerText

	headerCell.LayoutOrder = i

	headerCell.Size = UDim2.new(0, 0, 0, 24)

	headerCell.Parent = headerFrame

	local headerSize = Instance.new("UISizeConstraint")

	headerSize.MinSize = Vector2.new(headerWidth[i], 0)

	headerSize.Parent = headerCell

end

-- Finally, add data rows by iterating over each row and the columns in that row

for index, value in ipairs(data) do

	local rowData = value

	local rowFrame = Instance.new("Frame")

	rowFrame.Name = "Row" .. index

	rowFrame.Parent = frame

	for col = 1, #value do

		local cellData = rowData[col]

		local cell = Instance.new("TextLabel")

		cell.Text = cellData

		cell.Name = headers[col]

		cell.TextXAlignment = Enum.TextXAlignment.Left

		if tonumber(cellData) then -- If this cell is a number, right-align it instead

			cell.TextXAlignment = Enum.TextXAlignment.Right

		end

		cell.ClipsDescendants = true

		cell.Size = UDim2.new(0, 0, 0, 24)

		cell.Parent = rowFrame

	end

end

```

Provide feedback

---

MajorAxis

Read Parallel

Capabilities: UI

UITableLayout.MajorAxis :[Enum.TableMajorAxis](/docs/en-us/reference/engine/enums/TableMajorAxis)

Code Samples

Build UI Table

```

local frame = script.Parent

-- Table data

local headerWidth = { 200, 80, 80 }

local headers = {

	"Name",

	"Job",

	"Cash",

}

local data = {

	{ "Bob", "Waiter", 100 },

	{ "Lisa", "Police", 200 },

	{ "George", "-", 50 },

}

-- First, build the table layout

local uiTableLayout = Instance.new("UITableLayout")

uiTableLayout.FillDirection = Enum.FillDirection.Vertical

uiTableLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center

uiTableLayout.VerticalAlignment = Enum.VerticalAlignment.Center

uiTableLayout.FillEmptySpaceColumns = false

uiTableLayout.FillEmptySpaceRows = false

uiTableLayout.Padding = UDim2.new(0, 5, 0, 5)

uiTableLayout.SortOrder = Enum.SortOrder.LayoutOrder

frame.Size = UDim2.new(0, 0, 0, 40) -- The Size of the parent frame is the cell size

uiTableLayout.Parent = frame

-- Next, create column headers

local headerFrame = Instance.new("Frame")

headerFrame.Name = "Headers"

headerFrame.Parent = frame

for i = 1, #headers do

	local headerText = headers[i]

	local headerCell = Instance.new("TextLabel")

	headerCell.Text = headerText

	headerCell.Name = headerText

	headerCell.LayoutOrder = i

	headerCell.Size = UDim2.new(0, 0, 0, 24)

	headerCell.Parent = headerFrame

	local headerSize = Instance.new("UISizeConstraint")

	headerSize.MinSize = Vector2.new(headerWidth[i], 0)

	headerSize.Parent = headerCell

end

-- Finally, add data rows by iterating over each row and the columns in that row

for index, value in ipairs(data) do

	local rowData = value

	local rowFrame = Instance.new("Frame")

	rowFrame.Name = "Row" .. index

	rowFrame.Parent = frame

	for col = 1, #value do

		local cellData = rowData[col]

		local cell = Instance.new("TextLabel")

		cell.Text = cellData

		cell.Name = headers[col]

		cell.TextXAlignment = Enum.TextXAlignment.Left

		if tonumber(cellData) then -- If this cell is a number, right-align it instead

			cell.TextXAlignment = Enum.TextXAlignment.Right

		end

		cell.ClipsDescendants = true

		cell.Size = UDim2.new(0, 0, 0, 24)

		cell.Parent = rowFrame

	end

end

```

Provide feedback

---

Padding

Read Parallel

Capabilities: UI

UITableLayout.Padding :[UDim2](/docs/en-us/reference/engine/datatypes/UDim2)

Code Samples

Build UI Table

```

local frame = script.Parent

-- Table data

local headerWidth = { 200, 80, 80 }

local headers = {

	"Name",

	"Job",

	"Cash",

}

local data = {

	{ "Bob", "Waiter", 100 },

	{ "Lisa", "Police", 200 },

	{ "George", "-", 50 },

}

-- First, build the table layout

local uiTableLayout = Instance.new("UITableLayout")

uiTableLayout.FillDirection = Enum.FillDirection.Vertical

uiTableLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center

uiTableLayout.VerticalAlignment = Enum.VerticalAlignment.Center

uiTableLayout.FillEmptySpaceColumns = false

uiTableLayout.FillEmptySpaceRows = false

uiTableLayout.Padding = UDim2.new(0, 5, 0, 5)

uiTableLayout.SortOrder = Enum.SortOrder.LayoutOrder

frame.Size = UDim2.new(0, 0, 0, 40) -- The Size of the parent frame is the cell size

uiTableLayout.Parent = frame

-- Next, create column headers

local headerFrame = Instance.new("Frame")

headerFrame.Name = "Headers"

headerFrame.Parent = frame

for i = 1, #headers do

	local headerText = headers[i]

	local headerCell = Instance.new("TextLabel")

	headerCell.Text = headerText

	headerCell.Name = headerText

	headerCell.LayoutOrder = i

	headerCell.Size = UDim2.new(0, 0, 0, 24)

	headerCell.Parent = headerFrame

	local headerSize = Instance.new("UISizeConstraint")

	headerSize.MinSize = Vector2.new(headerWidth[i], 0)

	headerSize.Parent = headerCell

end

-- Finally, add data rows by iterating over each row and the columns in that row

for index, value in ipairs(data) do

	local rowData = value

	local rowFrame = Instance.new("Frame")

	rowFrame.Name = "Row" .. index

	rowFrame.Parent = frame

	for col = 1, #value do

		local cellData = rowData[col]

		local cell = Instance.new("TextLabel")

		cell.Text = cellData

		cell.Name = headers[col]

		cell.TextXAlignment = Enum.TextXAlignment.Left

		if tonumber(cellData) then -- If this cell is a number, right-align it instead

			cell.TextXAlignment = Enum.TextXAlignment.Right

		end

		cell.ClipsDescendants = true

		cell.Size = UDim2.new(0, 0, 0, 24)

		cell.Parent = rowFrame

	end

end

```

Provide feedback

---

Jump to

▼

UITableLayout

[Summary](#summary)

[Properties](#summary-properties)

[Properties](#properties)

[FillEmptySpaceColumns](#FillEmptySpaceColumns)

[FillEmptySpaceRows](#FillEmptySpaceRows)

[MajorAxis](#MajorAxis)

[Padding](#Padding)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
