<!-- Source: https://create.roblox.com/docs/en-us/ui/list-flex-layouts -->

List and flex layouts | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/ui/list-flex-layouts.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [User interface](/docs/en-us/ui)
6. /
7. Layout structures

# List and flex layouts

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/ui/list-flex-layouts.md)

The [UIListLayout](/docs/en-us/reference/engine/classes/UIListLayout)  positions sibling [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject)  into horizontal rows or vertical columns within their parent container. Whenever you add or remove a sibling object, the layout adjusts accordingly.

 ![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIListLayout-Example.png)

Once you insert a [UIListLayout](/docs/en-us/reference/engine/classes/UIListLayout) , it either overrides or influences the [Position](/docs/en-us/reference/engine/classes/GuiObject#Position) , [Rotation](/docs/en-us/reference/engine/classes/GuiObject#Rotation) , and/or [Size](/docs/en-us/reference/engine/classes/GuiObject#Size)  of all sibling UI objects, so changes to those properties within the [Properties](/docs/en-us/studio/properties)  window or within a script will not have the normal effect.

## [Fill direction](#fill-direction)[](#fill-direction)

The [FillDirection](/docs/en-us/reference/engine/classes/UIListLayout#FillDirection)  property determines the direction in which the list layout's siblings will render.

 ![UIListLayouts illustrating FillDirection of either horizontal or vertical.](https://prod.docsiteassets.roblox.com/assets/engine-api/classes/UIListLayout/FillDirection.png)

Ordering is determined by the layout's [SortOrder](/docs/en-us/reference/engine/classes/UIListLayout#SortOrder)  property which can be either ascending numeric , based on each item's [LayoutOrder](/docs/en-us/reference/engine/classes/GuiObject#LayoutOrder)  integer value, or alphanumeric  based on the item's [Name](/docs/en-us/reference/engine/classes/Instance#Name) .

 ![List layout examples illustrating numerical LayoutOrder sorting or alphanumerical Name sorting.](https://prod.docsiteassets.roblox.com/assets/engine-api/classes/UIListLayout/SortOrder.png)

To reverse elements, such as right-to-left ordering in a horizontal list, you'll need to reverse the sorting. For example, if four items are ordered by [LayoutOrder](/docs/en-us/reference/engine/classes/GuiObject#LayoutOrder)  of 0 , 1 , 2 , 3  respectively, negate each value to form an order of 0 , -1 , -2 , -3 .

## [Alignment](#alignment)[](#alignment)

The [HorizontalAlignment](/docs/en-us/reference/engine/classes/UIListLayout#HorizontalAlignment)  and [VerticalAlignment](/docs/en-us/reference/engine/classes/UIListLayout#VerticalAlignment)  properties determine the respective X  and Y  alignment of both the list's siblings in relation to each other and the list's overall bounds within its container. For example, a horizontally-filled list with [VerticalAlignment](/docs/en-us/reference/engine/classes/UIListLayout#VerticalAlignment)  of [Center](/docs/en-us/reference/engine/enums/VerticalAlignment)  centrally aligns the list's siblings with each other and  centers the list vertically in its container.

 ![List layout illustrating VerticalAlignment of Center.](https://prod.docsiteassets.roblox.com/assets/engine-api/classes/UIListLayout/VerticalAlignment-Center.png)

[HorizontalAlignment](/docs/en-us/reference/engine/classes/UIListLayout#HorizontalAlignment)  and [VerticalAlignment](/docs/en-us/reference/engine/classes/UIListLayout#VerticalAlignment)  differ slightly from [item line alignment](#item-line-alignment)  in a [flex](#flex-layouts)  layout, with which you can align items in the same line without applying the same alignment to the list's overall bounds in its container.

## [Wrapping](#wrapping)[](#wrapping)

The [Wraps](/docs/en-us/reference/engine/classes/UIListLayout#Wraps)  boolean controls whether siblings within the parent container wrap to another line when their default size exceeds the width/height of the container's bounds.

 ![Diagram showing how Wraps affects how siblings are distributed within the parent container's bounds.](https://prod.docsiteassets.roblox.com/assets/engine-api/classes/UIListLayout/Wraps.png)

## [Padding](#padding)[](#padding)

The [Padding](/docs/en-us/reference/engine/classes/UIListLayout#Padding)  property determines the amount of empty space between  each list item, set to either a scale (percentage of the container's size in the current direction) or an offset (static spacing value similar to pixel size).

This property does not apply padding around  the list's overall bounds; see [UIPadding](/docs/en-us/reference/engine/classes/UIPadding)  to apply top, bottom, left, and/or right padding to the contents of the parent.

## [Flex layouts](#flex-layouts)[](#flex-layouts)

Integrating flex  into a [UIListLayout](/docs/en-us/reference/engine/classes/UIListLayout)  is a powerful way to [equally fill/distribute](#equal-fill-or-distribution)  or [align/stretch](#item-line-alignment)  list items across their line, or [flex specific items](#flex-individual-items)  across a variable space.

While flex is a powerful tool, you should not apply it to a [UIListLayout](/docs/en-us/reference/engine/classes/UIListLayout)  without purpose, as it adds a slight performance cost above non‑flex, especially when resizing the layout or dynamically adding/removing flex items.

Additionally, a [grid layout](/docs/en-us/ui/grid-table-layouts#grid-layout)  may be preferable when items should strictly align to a grid in both the X  and Y  directions, since grid layouts enforce a consistent cell size while flex layouts may use a variable number of items per line.

### [Equal fill or distribution](#equal-fill-or-distribution)[](#equal-fill-or-distribution)

When the list layout's [fill direction](#fill-direction)  is set to [Horizontal](/docs/en-us/reference/engine/enums/FillDirection) , the [HorizontalFlex](/docs/en-us/reference/engine/classes/UIListLayout#HorizontalFlex)  property specifies how to distribute extra horizontal space in the parent container. Similarly, when the fill direction is set to [Vertical](/docs/en-us/reference/engine/enums/FillDirection) , the [VerticalFlex](/docs/en-us/reference/engine/classes/UIListLayout#VerticalFlex)  property specifies how to distribute extra vertical space.

HorizontalFlex VerticalFlex

![UIListLayout examples showing how each HorizontalFlex option affects the size and spacing of sibling UI objects.](https://prod.docsiteassets.roblox.com/assets/engine-api/classes/UIListLayout/HorizontalFlex-Options.png)

One practical use of [HorizontalFlex](/docs/en-us/reference/engine/classes/UIListLayout#HorizontalFlex)  is a tabbed window  interface where flex fills the tab bar equally, regardless of the number of tabs. No approach is easier than flex in this case, because it automatically calculates the width of each tab without developer‑defined width settings, and it automatically adjusts if the number of tabs changes.

3 Tabs 6 Tabs

![](https://prod.docsiteassets.roblox.com/assets/engine-api/classes/UIListLayout/HorizontalFlex-Tabs-3.png)

### [Item line alignment](#item-line-alignment)[](#item-line-alignment)

The [ItemLineAlignment](/docs/en-us/reference/engine/classes/UIListLayout#ItemLineAlignment)  property defines the cross‑directional  alignment of siblings within a line, letting you align objects of different widths/heights or make objects of lesser width/height fill their entire line.

 ![Examples of options for ItemLineAlignment in a horizontal fill direction.](https://prod.docsiteassets.roblox.com/assets/engine-api/classes/UIListLayout/ItemLineAlignment.png)

One practical use case for [ItemLineAlignment](/docs/en-us/reference/engine/classes/UIListLayout#ItemLineAlignment)  is to stretch a series of inconsistently sized tiles to fill their entire row ([Stretch](/docs/en-us/reference/engine/enums/ItemLineAlignment) ), making the layout more cohesive.

Uneven Layout Filled Lines

![](https://prod.docsiteassets.roblox.com/assets/engine-api/classes/UIListLayout/ItemLineAlignment-Start.png) Tiles with varying content heights result in an uneven and staggered layout

### [Flex individual items](#flex-individual-items)[](#flex-individual-items)

While flexing an entire layout is a powerful utility, certain layouts are more suited to individual item flexing . In such layouts, some elements in the list maintain their core size while other items flex to fill variable spaces. One practical usage is a slider bar widget with uniform [labels](/docs/en-us/ui/labels)  on both ends and a flexible slider bar that fills the entire width between.

 ![Example of UIFlexItem applied to a specific GuiObject under control of a UIListLayout.](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIFlexItem-Example.png)

To set one specific list item as flexible, insert a [UIFlexItem](/docs/en-us/reference/engine/classes/UIFlexItem)  as a child of the flexible item, then set its [FlexMode](/docs/en-us/reference/engine/classes/UIFlexItem#FlexMode)  property to [Fill](/docs/en-us/reference/engine/enums/UIFlexMode#Fill) , [Grow](/docs/en-us/reference/engine/enums/UIFlexMode#Grow) , [Shrink](/docs/en-us/reference/engine/enums/UIFlexMode#Shrink) , or [Custom](/docs/en-us/reference/engine/enums/UIFlexMode#Custom) .

![Example hierarchy of a UIFlexItem parented to a GuiObject under control of a UIListLayout.](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIFlexItem-Hierarchy.png)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
