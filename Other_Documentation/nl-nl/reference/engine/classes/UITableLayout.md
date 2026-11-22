<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/UITableLayout -->

UITableLayout | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [UIBase](/docs/nl-nl/reference/engine/classes/UIBase)
8. /
9. [UIComponent](/docs/nl-nl/reference/engine/classes/UIComponent)
10. /
11. [UILayout](/docs/nl-nl/reference/engine/classes/UILayout)
12. /
13. [UIGridStyleLayout](/docs/nl-nl/reference/engine/classes/UIGridStyleLayout)
14. /
15. [UITableLayout](/docs/nl-nl/reference/engine/classes/UITableLayout)

Nederlands

Feedback

Engine-klasse

UITableLayout

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/UITableLayout)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[FillEmptySpaceColumns](#FillEmptySpaceColumns) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |
|

[FillEmptySpaceRows](#FillEmptySpaceRows) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[MajorAxis](#MajorAxis) :[Enum.TableMajorAxis](/docs/nl-nl/reference/engine/enums/TableMajorAxis)

 |
|

[Padding](#Padding) :[UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)

 |

Overgenomen leden

7  overgenomen van [UIGridStyleLayout](/docs/nl-nl/reference/engine/classes/UIGridStyleLayout)

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Bouw UI Tabel

```

local frame = script.Parent

-- Tabelgegevens

local headerWidth = { 200, 80, 80 }

local headers = {

	"Naam",

	"Baan",

	"Geld",

}

local data = {

	{ "Bob", "Ober", 100 },

	{ "Lisa", "Politie", 200 },

	{ "George", "-", 50 },

}

-- Eerst, bouw de tabelindeling

local uiTableLayout = Instance.new("UITableLayout")

uiTableLayout.FillDirection = Enum.FillDirection.Vertical

uiTableLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center

uiTableLayout.VerticalAlignment = Enum.VerticalAlignment.Center

uiTableLayout.FillEmptySpaceColumns = false

uiTableLayout.FillEmptySpaceRows = false

uiTableLayout.Padding = UDim2.new(0, 5, 0, 5)

uiTableLayout.SortOrder = Enum.SortOrder.LayoutOrder

frame.Size = UDim2.new(0, 0, 0, 40) -- De grootte van het bovenliggende frame is de celgrootte

uiTableLayout.Parent = frame

-- Vervolgens, maak kolomkoppen

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

-- Ten slotte, voeg gegevensrijen toe door over elke rij en de kolommen in die rij te itereren

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

		if tonumber(cellData) then -- Als deze cel een getal is, rechts uitlijnen in plaats van links

			cell.TextXAlignment = Enum.TextXAlignment.Right

		end

		cell.ClipsDescendants = true

		cell.Size = UDim2.new(0, 0, 0, 24)

		cell.Parent = rowFrame

	end

end

```

---

API-referentie

Eigenschappen

FillEmptySpaceColumns

Parallel lezen

Mogelijkheden: UI

UITableLayout.FillEmptySpaceColumns :[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

Bouw UI Tabel

```

local frame = script.Parent

-- Tabelgegevens

local headerWidth = { 200, 80, 80 }

local headers = {

	"Naam",

	"Baan",

	"Geld",

}

local data = {

	{ "Bob", "Ober", 100 },

	{ "Lisa", "Politie", 200 },

	{ "George", "-", 50 },

}

-- Eerst, bouw de tabelindeling

local uiTableLayout = Instance.new("UITableLayout")

uiTableLayout.FillDirection = Enum.FillDirection.Vertical

uiTableLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center

uiTableLayout.VerticalAlignment = Enum.VerticalAlignment.Center

uiTableLayout.FillEmptySpaceColumns = false

uiTableLayout.FillEmptySpaceRows = false

uiTableLayout.Padding = UDim2.new(0, 5, 0, 5)

uiTableLayout.SortOrder = Enum.SortOrder.LayoutOrder

frame.Size = UDim2.new(0, 0, 0, 40) -- De grootte van het bovenliggende frame is de celgrootte

uiTableLayout.Parent = frame

-- Vervolgens, maak kolomkoppen

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

-- Ten slotte, voeg gegevensrijen toe door over elke rij en de kolommen in die rij te itereren

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

		if tonumber(cellData) then -- Als deze cel een getal is, rechts uitlijnen in plaats van links

			cell.TextXAlignment = Enum.TextXAlignment.Right

		end

		cell.ClipsDescendants = true

		cell.Size = UDim2.new(0, 0, 0, 24)

		cell.Parent = rowFrame

	end

end

```

Feedback geven

---

FillEmptySpaceRows

Parallel lezen

Mogelijkheden: UI

UITableLayout.FillEmptySpaceRows :[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

Bouw UI Tabel

```

local frame = script.Parent

-- Tabelgegevens

local headerWidth = { 200, 80, 80 }

local headers = {

	"Naam",

	"Baan",

	"Geld",

}

local data = {

	{ "Bob", "Ober", 100 },

	{ "Lisa", "Politie", 200 },

	{ "George", "-", 50 },

}

-- Eerst, bouw de tabelindeling

local uiTableLayout = Instance.new("UITableLayout")

uiTableLayout.FillDirection = Enum.FillDirection.Vertical

uiTableLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center

uiTableLayout.VerticalAlignment = Enum.VerticalAlignment.Center

uiTableLayout.FillEmptySpaceColumns = false

uiTableLayout.FillEmptySpaceRows = false

uiTableLayout.Padding = UDim2.new(0, 5, 0, 5)

uiTableLayout.SortOrder = Enum.SortOrder.LayoutOrder

frame.Size = UDim2.new(0, 0, 0, 40) -- De grootte van het bovenliggende frame is de celgrootte

uiTableLayout.Parent = frame

-- Vervolgens, maak kolomkoppen

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

-- Ten slotte, voeg gegevensrijen toe door over elke rij en de kolommen in die rij te itereren

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

		if tonumber(cellData) then -- Als deze cel een getal is, rechts uitlijnen in plaats van links

			cell.TextXAlignment = Enum.TextXAlignment.Right

		end

		cell.ClipsDescendants = true

		cell.Size = UDim2.new(0, 0, 0, 24)

		cell.Parent = rowFrame

	end

end

```

Feedback geven

---

MajorAxis

Parallel lezen

Mogelijkheden: UI

UITableLayout.MajorAxis :[Enum.TableMajorAxis](/docs/nl-nl/reference/engine/enums/TableMajorAxis)

Codevoorbeelden

Bouw UI Tabel

```

local frame = script.Parent

-- Tabelgegevens

local headerWidth = { 200, 80, 80 }

local headers = {

	"Naam",

	"Baan",

	"Geld",

}

local data = {

	{ "Bob", "Ober", 100 },

	{ "Lisa", "Politie", 200 },

	{ "George", "-", 50 },

}

-- Eerst, bouw de tabelindeling

local uiTableLayout = Instance.new("UITableLayout")

uiTableLayout.FillDirection = Enum.FillDirection.Vertical

uiTableLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center

uiTableLayout.VerticalAlignment = Enum.VerticalAlignment.Center

uiTableLayout.FillEmptySpaceColumns = false

uiTableLayout.FillEmptySpaceRows = false

uiTableLayout.Padding = UDim2.new(0, 5, 0, 5)

uiTableLayout.SortOrder = Enum.SortOrder.LayoutOrder

frame.Size = UDim2.new(0, 0, 0, 40) -- De grootte van het bovenliggende frame is de celgrootte

uiTableLayout.Parent = frame

-- Vervolgens, maak kolomkoppen

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

-- Ten slotte, voeg gegevensrijen toe door over elke rij en de kolommen in die rij te itereren

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

		if tonumber(cellData) then -- Als deze cel een getal is, rechts uitlijnen in plaats van links

			cell.TextXAlignment = Enum.TextXAlignment.Right

		end

		cell.ClipsDescendants = true

		cell.Size = UDim2.new(0, 0, 0, 24)

		cell.Parent = rowFrame

	end

end

```

Feedback geven

---

Padding

Parallel lezen

Mogelijkheden: UI

UITableLayout.Padding :[UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)

Codevoorbeelden

Bouw UI Tabel

```

local frame = script.Parent

-- Tabelgegevens

local headerWidth = { 200, 80, 80 }

local headers = {

	"Naam",

	"Baan",

	"Geld",

}

local data = {

	{ "Bob", "Ober", 100 },

	{ "Lisa", "Politie", 200 },

	{ "George", "-", 50 },

}

-- Eerst, bouw de tabelindeling

local uiTableLayout = Instance.new("UITableLayout")

uiTableLayout.FillDirection = Enum.FillDirection.Vertical

uiTableLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center

uiTableLayout.VerticalAlignment = Enum.VerticalAlignment.Center

uiTableLayout.FillEmptySpaceColumns = false

uiTableLayout.FillEmptySpaceRows = false

uiTableLayout.Padding = UDim2.new(0, 5, 0, 5)

uiTableLayout.SortOrder = Enum.SortOrder.LayoutOrder

frame.Size = UDim2.new(0, 0, 0, 40) -- De grootte van het bovenliggende frame is de celgrootte

uiTableLayout.Parent = frame

-- Vervolgens, maak kolomkoppen

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

-- Ten slotte, voeg gegevensrijen toe door over elke rij en de kolommen in die rij te itereren

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

		if tonumber(cellData) then -- Als deze cel een getal is, rechts uitlijnen in plaats van links

			cell.TextXAlignment = Enum.TextXAlignment.Right

		end

		cell.ClipsDescendants = true

		cell.Size = UDim2.new(0, 0, 0, 24)

		cell.Parent = rowFrame

	end

end

```

Feedback geven

---

Ga naar

▼

UITableLayout

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Eigenschappen](#properties)

[FillEmptySpaceColumns](#FillEmptySpaceColumns)

[FillEmptySpaceRows](#FillEmptySpaceRows)

[MajorAxis](#MajorAxis)

[Padding](#Padding)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
