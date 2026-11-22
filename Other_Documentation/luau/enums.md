<!-- Source: https://create.roblox.com/docs/luau/enums -->

Enums | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/luau/enums.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Scripting](/docs/scripting)
6. /
7. [Luau reference](/docs/luau)
8. /
9. Types

# Enums

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/luau/enums.md)

Enums are not a [built-in Luau type](https://luau.org/typecheck#builtin-types)  and they exist only in Roblox, but they're conceptually similar to other Luau data types and are something you'll work with frequently in Roblox development.

The enumeration  data type, or [Enum](/docs/reference/engine/datatypes/Enum) , is a fixed list of items. You can access enums through the global object called [Enum](/docs/reference/engine/datatypes/Enum) . For a full list and their respective items, see [Enums](/docs/reference/engine/enums) .

## [Enum items](#enum-items)[](#enum-items)

To get all items of an enum, call the [GetEnumItems()](/docs/reference/engine/datatypes/Enum#GetEnumItems)  method on it. The following code sample demonstrates how to call [GetEnumItems()](/docs/reference/engine/datatypes/Enum#GetEnumItems)  on the [Enum.PartType](/docs/reference/engine/enums/PartType)  enum.

```

local partTypes = Enum.PartType:GetEnumItems()

for index, enumItem in partTypes do

	print(enumItem)

end

--[[

	Enum.PartType.Ball

	Enum.PartType.Block

	Enum.PartType.Cylinder

	Enum.PartType.Wedge

	Enum.PartType.CornerWedge

]]

```

## [Data type](#data-type)[](#data-type)

The [EnumItem](/docs/reference/engine/datatypes/EnumItem)  is the data type for items in enums. An [EnumItem](/docs/reference/engine/datatypes/EnumItem)  has three properties:

-

Name  — The name of the [EnumItem](/docs/reference/engine/datatypes/EnumItem) .

-

Value  — The numerical index of the [EnumItem](/docs/reference/engine/datatypes/EnumItem) .

-

EnumType  — The parent [Enum](/docs/reference/engine/datatypes/Enum)  of the [EnumItem](/docs/reference/engine/datatypes/EnumItem) .

Some properties of objects can only be items of certain enums. For example, the [Shape](/docs/reference/engine/classes/Part#Shape)  property of a [Part](/docs/reference/engine/classes/Part)  object is an item of the [Enum.PartType](/docs/reference/engine/enums/PartType)  enum. The following code sample demonstrates how to print the properties of the [Enum.PartType.Cylinder](/docs/reference/engine/enums/PartType#Cylinder)  enum item.

```

print(Enum.PartType.Cylinder.Name) --> "Cylinder"

print(Enum.PartType.Cylinder.Value) --> 2

print(Enum.PartType.Cylinder.EnumType) --> PartType

```

To assign an [EnumItem](/docs/reference/engine/datatypes/EnumItem)  as the value of a property, use the full [Enum](/docs/reference/engine/datatypes/Enum)  declaration. You can also use the item's [Name](/docs/reference/engine/datatypes/EnumItem#Name)  property as a string.

```

local Workspace = game:GetService("Workspace")

local part = Instance.new("Part") -- Create a new part

part.Shape = Enum.PartType.Cylinder -- By full enum item declaration (best practice)

part.Shape = "Cylinder" -- By enum item's name as a string

part.Parent = Workspace

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
