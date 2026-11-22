<!-- Source: https://create.roblox.com/docs/players/tools -->

In-game tools | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/players/tools.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Players](/docs/players)

# In-game tools

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/players/tools.md)

In-game [Tools](/docs/reference/engine/classes/Tool)  are interactive tools that players can equip in sessions, such as weapons, magic wands, flashlights, keys, and more. You can design tools and include them in a player's inventory or place them around the world as pickups.

## [Create an in-game tool](#create-an-in-game-tool)[](#create-an-in-game-tool)

The [Tool](/docs/reference/engine/classes/Tool)  object is the basis of any tool in Roblox, so you'll need to create one. It's easier to preview how a tool looks by designing it in the [Workspace](/docs/reference/engine/classes/Workspace) , and later you can make it an [inventory](#player-inventory)  item or an [earned/purchased](#earnedpurchased-tool)  item.

1.

In the [Explorer](/docs/studio/explorer)  hierarchy, hover over [Workspace](/docs/reference/engine/classes/Workspace) , click the ⊕  button, and insert a [Tool](/docs/reference/engine/classes/Tool) .

 ![Tool object created in the workspace](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Workspace-Tool.png)

2.

With the new [Tool](/docs/reference/engine/classes/Tool)  selected, access the [Properties](/docs/studio/properties)  window and customize how the tool will appear in the player's inventory:

-

[TextureId](/docs/reference/engine/classes/Tool#TextureId)  — Specifies the image asset ID for the tool in a player's inventory.

-

[ToolTip](/docs/reference/engine/classes/Tool#ToolTip)  — The on-hover tooltip name for the tool in a player's inventory.

 ![](https://prod.docsiteassets.roblox.com/assets/players/in-experience-tools/Tool-Inventory.jpg)

3.

Decide whether the tool will be a [physical tool in the 3D environment](#physical-tool)  (most common) or a [non‑physical](#non-physical-tool)  tool that simply occupies a player's inventory and responds to their input.

### [Physical tool](#physical-tool)[](#physical-tool)

After creating the [Tool](/docs/reference/engine/classes/Tool)  instance for a physical tool, you'll need to [add parts/meshes](#add-partsmeshes)  to compose its appearance in the 3D world. You'll also need to include a [handle](#set-the-handle)  which player characters [grip](#adjust-the-grip-positionorientation) .

#### [Add parts/meshes](#add-partsmeshes)[](#add-partsmeshes)

In-game tools can consist of one or more [Parts](/docs/reference/engine/classes/Part)  and/or [MeshParts](/docs/reference/engine/classes/MeshPart) . If you construct the tool of multiple pieces, remember to connect them all together using [WeldConstraints](/docs/reference/engine/classes/WeldConstraint)  or other [mechanical constraints](/docs/physics/mechanical-constraints)  so that the tool stays intact as a unit while the player carries it around.

 ![Constraint pickers indicated in Studio's toolbar](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Constraint-Pickers.png)

When constructing tools, make sure that no parts are [Anchored](/docs/reference/engine/classes/BasePart#Anchored) . If you anchor the tool in 3D space, player characters will get stuck in place when they pick up or equip the tool.

If you want to place collectible tools as pickups around the 3D world and anchor them in specific places, such as floating slightly above the ground, you can anchor them but you'll need to add a [Script](/docs/reference/engine/classes/Script)  to each tool which unanchors its parts upon collection. See [collectible tools](#collectible-tool)  for details.

#### [Set the handle](#set-the-handle)[](#set-the-handle)

To enable players to carry tools around, one part of the tool needs to be named Handle . This is where the tool will attach to the character model's RightHand  [body part](/docs/avatar/character-bodies/specifications#body-parts)  (R15) or Right Arm  part (R6).

If the tool is composed of just one [MeshPart](/docs/reference/engine/classes/MeshPart) , simply name that part Handle . Otherwise, you can include a separate part named Handle  as a direct child  of the parent [Tool](/docs/reference/engine/classes/Tool)  and then attach it to another part with a [WeldConstraint](/docs/reference/engine/classes/WeldConstraint)  or [mechanical constraint](/docs/physics/mechanical-constraints) .

The following example shows a tool with three instances: the Handle  mesh, a [RopeConstraint](/docs/reference/engine/classes/RopeConstraint) , and a lantern mesh which hangs from the rope.

 ![](https://prod.docsiteassets.roblox.com/assets/players/in-experience-tools/Tool-Handle-Example.jpg)

Make sure to include only one  part named Handle . If you include multiple parts named Handle , one will be randomly chosen as the attachment point for the character's hand, potentially causing issues such as the character holding a sword's blade instead of its hilt.

#### [Adjust the grip position/orientation](#adjust-the-grip-positionorientation)[](#adjust-the-grip-positionorientation)

The tool's [Grip](/docs/reference/engine/classes/Tool#Grip)  property is a [CFrame](/docs/reference/engine/datatypes/CFrame)  which specifies how the tool is positioned and oriented relative to the character holding it.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Tool-Grip.png)

Since the ideal grip position/orientation is different for every tool, you'll need to experiment with the values until your tool's grip looks correct. The following example shows possible incorrect and correct [Grip](/docs/reference/engine/classes/Tool#Grip)  settings for the hanging lantern:

![](https://prod.docsiteassets.roblox.com/assets/players/in-experience-tools/Tool-Grip-Incorrect.jpg) Lantern dragging on ground with [Grip.Position](/docs/reference/engine/classes/Tool#Grip)  of (0, -2, 0)  and [Grip.Orientation](/docs/reference/engine/classes/Tool#Grip)  of (-90, 0, 0)

![](https://prod.docsiteassets.roblox.com/assets/players/in-experience-tools/Tool-Grip-Correct.jpg) Lantern in front of character with [Grip.Position](/docs/reference/engine/classes/Tool#Grip)  of (0, -1.5, 0)  and [Grip.Orientation](/docs/reference/engine/classes/Tool#Grip)  of (25, 0, 0)

### [Non-physical tool](#non-physical-tool)[](#non-physical-tool)

A non-physical [Tool](/docs/reference/engine/classes/Tool)  simply occupies a player's [inventory](#player-inventory)  and responds to their input. For example, a roleplaying game might feature a series of magical spells that players can "cast" through their inventory.

 ![](https://prod.docsiteassets.roblox.com/assets/players/in-experience-tools/Tool-Inventory-Non-Physical.jpg)

Non-physical tools don't require any 3D composition and do not utilize a Handle  part, so you should disable  the tool's [RequiresHandle](/docs/reference/engine/classes/Tool#RequiresHandle)  property:

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Tool-RequiresHandle.png)

## [Add tools to a game](#add-tools-to-a-game)[](#add-tools-to-a-game)

Once you finish [creating](#create-an-in-game-tool)  your in-game tool, you'll need to place it in the correct area of the [Explorer](/docs/studio/explorer)  hierarchy. Where you place the tool in the hierarchy depends on its intended usage.

### [Player inventory](#player-inventory)[](#player-inventory)

If you want all players to start out with a tool in their inventory, put it inside the [StarterPack](/docs/reference/engine/classes/StarterPack)  container. When any player spawns, the system copies the tool to their [Backpack](/docs/reference/engine/classes/Backpack) . From there, the player can equip the tool by clicking its inventory icon or by pressing the associated hotkey such as 1  or 2 .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/StarterPack-Tools.png)

Note that tools are copied to the player's inventory ([Backpack](/docs/reference/engine/classes/Backpack) ) in the order they were added to [StarterPack](/docs/reference/engine/classes/StarterPack) . For a more controlled ordering, you can add a [LocalScript](/docs/reference/engine/classes/LocalScript)  to [StarterPack](/docs/reference/engine/classes/StarterPack)  which temporarily moves the tools to [ReplicatedStorage](/docs/reference/engine/classes/ReplicatedStorage)  then re‑parents them to [Backpack](/docs/reference/engine/classes/Backpack)  in the order specified in the order  table.

Reorder Inventory

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local order = {"WaterSpell", "FireSpell", "AirSpell", "EarthSpell"}

local backpack = script.Parent

for _, item in backpack:GetChildren() do

	if item:IsA("Tool") then

		item.Parent = ReplicatedStorage

	end

end

-- Re-parent tools to backpack in the specified order

for i = 1, #order do

	local tool = ReplicatedStorage:FindFirstChild(order[i])

	if tool then

		tool.Parent = backpack

	end

end

```

As noted above, tools placed in [StarterPack](/docs/reference/engine/classes/StarterPack)  clone to all  players. To more specifically control which tools clone to which players, see [StarterGear](/docs/reference/engine/classes/StarterGear) .

### [Collectible tool](#collectible-tool)[](#collectible-tool)

If you want to allow players to collect physical tools as they explore the 3D world, place the tools in the [Workspace](/docs/reference/engine/classes/Workspace)  just like normal 3D objects. Collected tools will be automatically equipped and added to the player's inventory (you do not need to add extra collision detection for characters to grab the tool).

As noted in the [add parts/meshes](#add-partsmeshes)  section, tool parts should not typically be [Anchored](/docs/reference/engine/classes/BasePart#Anchored) , since player characters will get stuck in place when they pick up or equip an anchored tool. However, if you want to anchor a collectible tool to a specific place in the 3D world, such as floating slightly above the ground, you can add the following [Script](/docs/reference/engine/classes/Script)  to the tool to unanchor its parts upon collection.

Unanchor Tool on Equip/Collect

```

local tool = script.Parent

tool.Equipped:Connect(function()

	for _, part in tool:GetDescendants() do

		if part:IsA("BasePart") and part.Anchored then

			part.Anchored = false

		end

	end

end)

```

### [Earned/purchased tool](#earnedpurchased-tool)[](#earnedpurchased-tool)

If you want to set tools as awards for when players accomplish tasks, or offer tools for sale in an in‑game store, put those tools inside [ReplicatedStorage](/docs/reference/engine/classes/ReplicatedStorage) . From there, you can [Clone()](/docs/reference/engine/classes/Instance#Clone)  a tool to the player's [Backpack](/docs/reference/engine/classes/Backpack)  at the proper time.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-Tools.png)

Clone Tool to Player's Inventory

```

local Players = game:GetService("Players")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local player = Players.LocalPlayer

local backpack = player:WaitForChild("Backpack")

-- Create a clone of the tool

local tool = ReplicatedStorage:FindFirstChild("WaterSpell")

if tool then

	local clone = tool:Clone()

	clone.Parent = backpack  -- Adds clone to the player's backpack

end

```

## [Implement tool effects](#implement-tool-effects)[](#implement-tool-effects)

After [adding tools to your game](#add-tools-to-a-game) , you can implement scripts to enable players to use their tools and perform the desired actions. The following tool‑specific events indicate the state of the tool and the player's input with it.

-

[Equipped()](/docs/reference/engine/classes/Tool#Equipped)  — Fires when the player selects the tool from their backpack.

-

[Unequipped()](/docs/reference/engine/classes/Tool#Unequipped)  — Fires when the player switches tools or drops the tool.

-

[Activated()](/docs/reference/engine/classes/Tool#Activated)  — Fires when the player starts activating the tool (clicks, taps, or presses the back‑right trigger on a gamepad).

-

[Deactivated()](/docs/reference/engine/classes/Tool#Deactivated)  — Fires when the player stops the activation input (releases the button or touch).

Tool Events Template

```

local tool = script.Parent

local function onEquip()

	print(tool.Name, "tool equipped")

end

local function onUnequip()

	print(tool.Name, "tool unequipped")

end

local function onActivate()

	print(tool.Name, "tool activated")

end

local function onDeactivate()

	print(tool.Name, "tool deactivated")

end

tool.Equipped:Connect(onEquip)

tool.Unequipped:Connect(onUnequip)

tool.Activated:Connect(onActivate)

tool.Deactivated:Connect(onDeactivate)

```

Tool events only fire in client‑side [LocalScripts](/docs/reference/engine/classes/LocalScript)  because only the player's device knows when [input](/docs/input)  happens. As a result, most tools require both a [LocalScript](/docs/reference/engine/classes/LocalScript)  and a server‑side [Script](/docs/reference/engine/classes/Script)  where each handles certain aspects of the tool's behavior and a [RemoteEvent](/docs/reference/engine/classes/RemoteEvent)  passes information from the client to the server (see [remote events and callbacks](/docs/scripting/events/remote)  for more information).

As follows are example tools and their behaviors managed by either a [LocalScript](/docs/reference/engine/classes/LocalScript)  or a [Script](/docs/reference/engine/classes/Script) :

| Tool | | [LocalScript](/docs/reference/engine/classes/LocalScript) | | [Script](/docs/reference/engine/classes/Script) |
| --- | --- |
| Creator's Wand | | Detects where the player activates the tool ([Activated()](/docs/reference/engine/classes/Tool#Activated) ). | | Creates a new part at the location within the 3D world where the player touched or clicked. |
| Invisibility Cloak | | Detects when the player equips the tool ([Equipped()](/docs/reference/engine/classes/Tool#Equipped) ) or unequips the tool ([Unequipped()](/docs/reference/engine/classes/Tool#Unequipped) ). | | Makes the player invisible to all other players while the cloak is equipped and restores the player to full visibility when the cloak is unequipped. |
| Mega‑Bow | | Detects how long the player activates the tool (time between [Activated()](/docs/reference/engine/classes/Tool#Activated)  and [Deactivated()](/docs/reference/engine/classes/Tool#Deactivated) ). | | Shoots a magical arrow with greater or lesser power, depending on the detected activation time. |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
