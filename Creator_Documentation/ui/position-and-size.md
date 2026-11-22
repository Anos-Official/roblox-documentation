<!-- Source: https://create.roblox.com/docs/en-us/ui/position-and-size -->

Position and size UI objects | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/ui/position-and-size.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [User interface](/docs/en-us/ui)

# Position and size UI objects

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/ui/position-and-size.md)

Unless UI objects are under control of a [layout structure](#layout-structures)  or a [size modifier/constraint](/docs/en-us/ui/size-modifiers) , you have complete control over their [position](#position)  and [size](#size) . You can also set the Z‑index [layering](#zindex)  order in which objects overlap.

## [Core properties](#core-properties)[](#core-properties)

All [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject)  share a core set of properties to [position](#position) , [size](#size) , [anchor](#anchorpoint) , and [layer](#zindex)  them within an on‑screen or in-game container.

### [Position](#position)[](#position)

The [Position](/docs/en-us/reference/engine/classes/GuiObject#Position)  property is a [UDim2](/docs/en-us/reference/engine/datatypes/UDim2)  coordinate set that positions the object along the X  and Y  axes. A [UDim2](/docs/en-us/reference/engine/datatypes/UDim2)  is represented by both [Scale](/docs/en-us/reference/engine/datatypes/UDim#Scale)  and [Offset](/docs/en-us/reference/engine/datatypes/UDim#Offset)  values for each axis:

-

[Scale](/docs/en-us/reference/engine/datatypes/UDim#Scale)  values represent a percentage  of the container's size along the corresponding axis, additive of any [Offset](/docs/en-us/reference/engine/datatypes/UDim#Offset)  values.

-

[Offset](/docs/en-us/reference/engine/datatypes/UDim#Offset)  values represent how many pixels  to shift the object on the corresponding axis, additive of any [Scale](/docs/en-us/reference/engine/datatypes/UDim#Scale)  values.

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/UDim2-Components.png)

To edit the position of a selected [GuiObject](/docs/en-us/reference/engine/classes/GuiObject) , click the Position  field in the [Properties](/docs/en-us/studio/properties)  window and enter a new [UDim2](/docs/en-us/reference/engine/datatypes/UDim2)  coordinate set.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/GuiObject-Position.png)  ![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Scale-Offset-Positioning.png)

Brackets and spaces are optional  when entering a [UDim2](/docs/en-us/reference/engine/datatypes/UDim2)  in Studio — you can simply enter the four values separated by commas, for instance 0.25,40,0.1,20 , and Studio will infer the intended value set.

Studio also infers the intended value set when a single number is entered. For example, entering simply 0.5  will be converted to {0.5, 0},{0.5, 0}  since 0.5  is likely a Scale  value of 50%. Conversely, entering 20  will be converted to {0, 20},{0, 20}  since 20  is likely an Offset  value of 20 pixels and not a scale of 2000%.

### [Size](#size)[](#size)

The [Size](/docs/en-us/reference/engine/classes/GuiObject#Size)  property is a [UDim2](/docs/en-us/reference/engine/datatypes/UDim2)  coordinate set that sizes the object along the X  and Y  axes. A [UDim2](/docs/en-us/reference/engine/datatypes/UDim2)  is represented by both [Scale](/docs/en-us/reference/engine/datatypes/UDim#Scale)  and [Offset](/docs/en-us/reference/engine/datatypes/UDim#Offset)  values for each axis:

-

Scale  — Values that represent a percentage  of the container's size along the corresponding axis, additive to any Offset  values.

-

Offset  — Values that represent the object's pixel  size along the corresponding axis, additive to any Scale  values.

To edit the size of a selected [GuiObject](/docs/en-us/reference/engine/classes/GuiObject) , click the Size  field in the [Properties](/docs/en-us/studio/properties)  window and enter a new [UDim2](/docs/en-us/reference/engine/datatypes/UDim2)  coordinate set.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/GuiObject-Size.png)  ![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Scale-Sizing.png)

Brackets and spaces are optional  when entering a [UDim2](/docs/en-us/reference/engine/datatypes/UDim2)  in Studio — you can simply enter the four values separated by commas, for instance 0.75,0,0.25,0 , and Studio will infer the intended value set.

Studio also infers the intended value set when a single number is entered. For example, entering simply 0.5  will be converted to {0.5, 0},{0.5, 0}  since 0.5  is likely a Scale  value of 50%. Conversely, entering 20  will be converted to {0, 20},{0, 20}  since 20  is likely an Offset  value of 20 pixels and not a scale of 2000%.

### [AnchorPoint](#anchorpoint)[](#anchorpoint)

The [AnchorPoint](/docs/en-us/reference/engine/classes/GuiObject#AnchorPoint)  property defines the origin point  from where the object changes [position](#position)  and [size](#size) . The default [AnchorPoint](/docs/en-us/reference/engine/classes/GuiObject#AnchorPoint)  values are (0, 0)  which places the anchor in the top‑left corner of the object.

[AnchorPoint](/docs/en-us/reference/engine/classes/GuiObject#AnchorPoint)  values are a fraction  from 0  to 1 , relative to the [size](#size)  of the object, meaning an object with [AnchorPoint](/docs/en-us/reference/engine/classes/GuiObject#AnchorPoint)  values of (0.5, 0.5)  places the anchor point halfway (50%) through the object both horizontally and vertically, and any changes to its [position](#position)  or [size](#size)  both move and scale outward from this point.

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Anchor-Points.png)

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Anchor-Point-Scaling.png)

To view and edit the anchor point of a selected [GuiObject](/docs/en-us/reference/engine/classes/GuiObject) :

1.

In the [Properties](/docs/en-us/studio/properties)  window, click inside the AnchorPoint  field.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/GuiObject-AnchorPoint.png)

2.

Enter a new [Vector2](/docs/en-us/reference/engine/datatypes/Vector2)  coordinate and press Enter .

Studio infers the intended value pair when a single number is entered. For example, entering simply 0.5  will be converted to 0.5, 0.5  for a center anchor point.

### [ZIndex](#zindex)[](#zindex)

The [ZIndex](/docs/en-us/reference/engine/classes/GuiObject#ZIndex)  property defines the layer order in which [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject)  render and overlap each other. If you want to create new rendering layers, you must set the [ZIndex](/docs/en-us/reference/engine/classes/GuiObject#ZIndex)  property to different positive or negative integer values for each object.

For UI containers like [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui) , the default [ZIndexBehavior](/docs/en-us/reference/engine/classes/ScreenGui#ZIndexBehavior)  always renders children above their parents, and each child's [ZIndex](/docs/en-us/reference/engine/classes/GuiObject#ZIndex)  is used to decide the order in which it renders over others.

To edit an object's [ZIndex](/docs/en-us/reference/engine/classes/GuiObject#ZIndex) , locate ZIndex  in the [Properties](/docs/en-us/studio/properties)  window and enter a new integer value.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/GuiObject-ZIndex.png)

## [Layout structures](#layout-structures)[](#layout-structures)

Layout structures let you quickly organize and display [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject) , for example into a horizontal or vertical [list](/docs/en-us/ui/list-flex-layouts) , a [grid](/docs/en-us/ui/grid-table-layouts#grid-layout)  of equally‑sized tiles, a [page sequence](/docs/en-us/ui/page-layouts) , and more. Layouts typically override or influence the [position](#position) /[size](#size)  of objects under their control.

| Layout | | Description |
| --- | --- |
| [List](/docs/en-us/ui/grid-table-layouts#grid-layout) | | [UIListLayout](/docs/en-us/reference/engine/classes/UIListLayout)  positions sibling [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject)  into horizontal rows or vertical columns within their parent container. |
| [Grid](/docs/en-us/ui/grid-table-layouts#grid-layout) | | [UIGridLayout](/docs/en-us/reference/engine/classes/UIGridLayout)  positions sibling [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject)  in a grid of uniform cells of the same size within their parent container. |
| [Table](/docs/en-us/ui/grid-table-layouts#table-layout) | | [UITableLayout](/docs/en-us/reference/engine/classes/UITableLayout)  positions sibling [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject)  and their children into table format. |
| [Page](/docs/en-us/ui/page-layouts) | | [UIPageLayout](/docs/en-us/reference/engine/classes/UIPageLayout)  organizes its sibling [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject)  into unique pages that you can transition to through scripting. |

## [Cross-platform factors](#cross-platform-factors)[](#cross-platform-factors)

Roblox is inherently [cross‑platform](/docs/en-us/projects/cross-platform) , as players can discover and join games on their phone or tablet, then later continue where they left off on their PC or console. You should design your Roblox games to be accessible and enjoyable on all  platforms that you choose to support, instead of optimizing for one platform and neglecting others.

### [Reserved zones](#reserved-zones)[](#reserved-zones)

On mobile devices, the default controls occupy a portion of the bottom-left and bottom-right corners of the screen. When you design a game's UI, avoid placing important info or virtual buttons in these zones.

 ![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Touch-Reserved-Zones.png)

### [Thumb zones](#thumb-zones)[](#thumb-zones)

Most mobile players use two thumbs — one on the virtual thumbstick and one on the jump button. Depending on the physical size of the device and the player's hands, reaching too far from the bottom corners becomes uncomfortable or impossible, so you should avoid placing frequently‑used buttons outside of easy‑to‑reach zones.

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Thumb-Zones-Phone-Reachable.png)

Button comfortably within reach of player's right thumb

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Thumb-Zones-Phone-Non-Reachable.png)

Button difficult to reach unless player stretches hand or thumb

Remember that comfortable thumb zones differ between phones and tablets because tablets have a larger screen. A button placed 40% below the screen's top edge is reachable on a phone but almost unreachable on a tablet.

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Thumb-Zones-Tablet-Reachable.png)

Button 40% from top edge of phone, within reach of player's thumb

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Thumb-Zones-Tablet-Non-Reachable.png)

Button 40% from top edge of tablet, difficult to reach without stretching

A reliable approach on both phones and tablets is relative  positioning of custom buttons near frequently‑used controls like the default jump button, placing them within easy reach.

 ![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Custom-Buttons-Near-Jump.png)

The following code, placed in a client-side script within [StarterPlayerScripts](/docs/en-us/reference/engine/classes/StarterPlayerScripts) , fetches the position of the jump button and creates a placeholder [button](/docs/en-us/ui/buttons)  20 pixels to its left.

Client Script - Custom Button Near Jump Button

```

local Players = game:GetService("Players")

local UserInputService = game:GetService("UserInputService")

local player = Players.LocalPlayer

local playerGui = player:WaitForChild("PlayerGui")

if UserInputService.TouchEnabled then

	-- Wait for jump button to be fully loaded

	while not (playerGui:FindFirstChild("JumpButton", true) and playerGui:FindFirstChild("JumpButton", true).IsLoaded) do

		task.wait()

	end

	local jumpButton = playerGui:FindFirstChild("JumpButton", true)

	-- Place new custom button to left of jump button

	local customButton = Instance.new("ImageButton")

	customButton.AnchorPoint = Vector2.new(1, 1)

	customButton.Size = UDim2.fromOffset(jumpButton.Size.X.Offset * 0.8, jumpButton.Size.Y.Offset * 0.8)

	customButton.Position = jumpButton.Position + UDim2.fromOffset(-20, jumpButton.Size.Y.Offset)

	customButton.Parent = jumpButton.Parent

else

	warn("Device is not touch-enabled or Studio is not emulating a touch-enabled device!")

end

```

### [Context-based UI](#context-based-ui)[](#context-based-ui)

Screen space is limited on mobile devices, so you should show only the most vital information during active gameplay. For example, if your game includes a special input action to open doors and treasure chests, it doesn't make sense to constantly show an "open" button on the screen. Instead, use a [proximity prompt](/docs/en-us/ui/proximity-prompts)  or similar method to accept input only when the character approaches a door or chest.

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Contextual-Button.png) Custom button that you display only when character is near a door or chest

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
