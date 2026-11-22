<!-- Source: https://create.roblox.com/docs/ui/grid-table-layouts -->

Grid and table layouts | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/ui/grid-table-layouts.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [User interface](/docs/ui)
6. /
7. Layout structures

# Grid and table layouts

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/ui/grid-table-layouts.md)

In comparison to [UIListLayout](/docs/reference/engine/classes/UIListLayout) , [UIGridLayout](/docs/reference/engine/classes/UIGridLayout)  and [UITableLayout](/docs/reference/engine/classes/UITableLayout)  allow for more structured and organized layouts. These are most appropriate for interfaces like a shop inventory where each item can be presented in a grid of equally‑sized tiles, or items can be sorted into related rows/columns.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGridLayout-Example.jpg)[UIGridLayout](/docs/reference/engine/classes/UIGridLayout)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UITableLayout-Example.jpg)[UITableLayout](/docs/reference/engine/classes/UITableLayout)

## [Grid layout](#grid-layout)[](#grid-layout)

[UIGridLayout](/docs/reference/engine/classes/UIGridLayout)  positions sibling [GuiObjects](/docs/reference/engine/classes/GuiObject)  in a grid of uniform cells of the same size within their parent container. Cells are added by row or column based on the layout's [FillDirection](/docs/reference/engine/classes/UIGridLayout#FillDirection)  until the next cell doesn't fit, then a new row or column begins. For further control, you can use the [FillDirectionMaxCells](/docs/reference/engine/classes/UIGridLayout#FillDirectionMaxCells)  property to set the maximum number of cells per row or column.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGridLayout-Example.jpg)

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/UIGridLayout.png)

By default, [UIGridLayout](/docs/reference/engine/classes/UIGridLayout)  positions sibling [GuiObjects](/docs/reference/engine/classes/GuiObject)  in order of their [LayoutOrder](/docs/reference/engine/classes/GuiObject#LayoutOrder)  where lower values go before higher values, and equal values sort depending on the order in which you added them. If you change the layout's [SortOrder](/docs/reference/engine/classes/UIGridStyleLayout#SortOrder)  to [Enum.SortOrder.Name](/docs/reference/engine/enums/SortOrder#Name) , siblings sort in alphabetical order.

Once you insert a [UIGridLayout](/docs/reference/engine/classes/UIGridLayout) , it either overrides or influences the [Position](/docs/reference/engine/classes/GuiObject#Position)  and/or [Size](/docs/reference/engine/classes/GuiObject#Size)  of all sibling UI objects, so changes to those properties within the [Properties](/docs/studio/properties)  window or within a script will not have the normal effect.

[UIGridLayout](/docs/reference/engine/classes/UIGridLayout)  respects any [constraints](/docs/ui/size-modifiers)  you place on objects within the grid. For example, if an object has a [UISizeConstraint](/docs/reference/engine/classes/UISizeConstraint)  with a [MinSize](/docs/reference/engine/classes/UISizeConstraint#MinSize)  property that is higher than the grid's [CellSize](/docs/reference/engine/classes/UIGridLayout#CellSize)  property, the object will span multiple cells.

## [Table layout](#table-layout)[](#table-layout)

[UITableLayout](/docs/reference/engine/classes/UITableLayout)  positions sibling [GuiObjects](/docs/reference/engine/classes/GuiObject)  and their children into table format. The default [FillDirection](/docs/reference/engine/classes/UITableLayout#FillDirection)  of [Vertical](/docs/reference/engine/enums/FillDirection)  means that siblings are first positioned into rows, and children of those siblings are positioned horizontally to form columns, such that each cell within a row has the same height and each cell within a column has the same width.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UITableLayout-Example.jpg)

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/UITableLayout.png)

This pattern mimics the standard HTML row/column structure:

```

<table>

	<tbody>

		<tr> <!-- Row1 -->

			<td>Label 1</td> <!-- TextLabel1 -->

			<td>Label 2</td> <!-- TextLabel2 -->

			<td>Label 3</td> <!-- TextLabel3 -->

		</tr>

		<tr> <!-- Row2 -->

			<td>Label 4</td> <!-- TextLabel4 -->

			<td>Label 5</td> <!-- TextLabel5 -->

			<td>Label 6</td> <!-- TextLabel6 -->

		</tr>

		<tr> <!-- Row3 -->

			<td>Label 7</td> <!-- TextLabel7 -->

			<td>Label 8</td> <!-- TextLabel8 -->

			<td>Label 9</td> <!-- TextLabel9 -->

		</tr>

	</tbody>

</table>

```

Unless you enable the layout's [FillEmptySpaceColumns](/docs/reference/engine/classes/UITableLayout#FillEmptySpaceColumns)  or [FillEmptySpaceRows](/docs/reference/engine/classes/UITableLayout#FillEmptySpaceRows)  properties, the size of the sibling [GuiObjects](/docs/reference/engine/classes/GuiObject)  determines the dimensions of the cells. For example, a [TextLabel](/docs/reference/engine/classes/TextLabel)  of size [UDim2.new(0.25, 0, 0.1, 0)](/docs/reference/engine/datatypes/UDim2#new)  will create a table cell of 25% width and 10% height inside the parent container.

Once you insert a [UITableLayout](/docs/reference/engine/classes/UITableLayout) , it either overrides or influences the [Position](/docs/reference/engine/classes/GuiObject#Position)  and/or [Size](/docs/reference/engine/classes/GuiObject#Size)  of all sibling UI objects, so changes to those properties within the [Properties](/docs/studio/properties)  window or within a script will not have the normal effect.

[UITableLayout](/docs/reference/engine/classes/UITableLayout)  respects and is responsive to any [UISizeConstraint](/docs/reference/engine/classes/UISizeConstraint)  you place on objects within the table. For example, if an object has a [UISizeConstraint](/docs/reference/engine/classes/UISizeConstraint)  with a [MinSize](/docs/reference/engine/classes/UISizeConstraint#MinSize)  property within a header cell, the rest of the cells within the column will be the same size as the header cell.

Note that if the [MaxSize](/docs/reference/engine/classes/UISizeConstraint#MaxSize)  property restricts a cell's size from filling the allotted space of a row or column that is wider than the cell, the object aligns to the top‑left of the cell.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
