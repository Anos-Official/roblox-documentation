<!-- Source: https://create.roblox.com/docs/en-us/tutorials/use-case-tutorials/scripting/intermediate-scripting/create-player-tools -->

Create player tools | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/tutorials/use-case-tutorials/scripting/intermediate-scripting/create-player-tools.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Tutorials](/docs/en-us/tutorials)
4. /
5. Scripting
6. /
7. Intermediate gameplay

# Create player tools

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/tutorials/use-case-tutorials/scripting/intermediate-scripting/create-player-tools.md)

Tools are a simple way to manage items that the player can hold in their hand and use in-game. They can range from weapons such as swords to food items.

In this tutorial, you'll learn how to create a tool in the shape of a laser blaster that will play sound effects when equipped or activated.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/title-image.jpg)

## [Create the tool](#create-the-tool)[](#create-the-tool)

The [Tool](/docs/en-us/reference/engine/classes/Tool)  object is the basis of any tool in Roblox, so you'll need to create one. It's easier to change how tools look by adding objects such as Parts and MeshParts to the tool in the workspace where they are visible.

1.

Insert a Tool  into the workspace and name it Blaster .

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/explorer-blaster.png)

2.

Insert a [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  into the tool.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/explorer-MeshPart.png)

3.

Set the MeshId  property to rbxassetid://92656610 .

4.

Set the TextureId  property to rbxassetid://92658105 .

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/properties-MeshPart.png)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/viewport-mesh.jpg)

5.

The tool needs a part named Handle  for the player to hold. Change the name of the MeshPart to Handle .

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/explorer-handle.png)

If you don't include a part named ** Handle**  in the tool, it will drop to the ground when a player tries to equip it.

## [Store the tool](#store-the-tool)[](#store-the-tool)

Tools can be kept in the 3D world as collectable tools  or given to all players as starter tools .

### [Collectable tool](#collectable-tool)[](#collectable-tool)

The blaster is currently a child of Workspace  so it will be collectable. A player can pick up the tool by touching it, causing it to become a child of the character model; the tool will then be equipped and placed in their hotbar.

During gameplay, unequipped tools are stored within the player's hierarchy in the Backpack and then moved to their character model when equipped. Any tool that becomes a child of a character will be automatically equipped.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/explorer-unequipped.png) Tripmine Unequipped

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/explorer-equipped-character.png) Tripmine Equipped

### [Starter tool](#starter-tool)[](#starter-tool)

Storing a tool in [StarterPack](/docs/en-us/reference/engine/classes/StarterPack)  will place it in a player's [Backpack](/docs/en-us/reference/engine/classes/Backpack)  when they join or respawn.

1.

Move the Blaster  to StarterPack  in the Explorer .

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/explorer-starterpack.png)

2.

Play the game to test the tool. Click on the hotbar at the bottom of the screen or press 1  on the keyboard to equip the tool.

## [Tool properties](#tool-properties)[](#tool-properties)

### [Position / orientation](#position--orientation)[](#position--orientation)

A tool's position and orientation can be changed using the grip  properties. GripPos  changes the position of the grip, whereas GripForward , GripRight  and GripUp  affect the rotation.

Currently the player is holding the center of the blaster instead of the grip.

1.

Set the GripPos  property of the tool to 0, -0.4, 1.1 .

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/property-grippos.png)

2.

[Initiate a playtest](/docs/en-us/studio/testing-modes#playtesting)  to test the tool. Notice how the tool is now being gripped in a different position.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/viewport-weapon-pos-2.jpg) Before

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/viewport-weapon-pos-1.jpg) After

### [Hotbar icon](#hotbar-icon)[](#hotbar-icon)

By default, the tool name  will be displayed on the hotbar icon. It's good practice to change the icon to be an image of the tool. Set the TextureId  property of the tool to rbxassetid://92628145 .

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/viewport-blaster-icon-2.png) Before

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/viewport-blaster-icon.png) After

### [Tooltip](#tooltip)[](#tooltip)

A tooltip  is a small text description that appears when the mouse hovers over a tool in the hotbar. They typically include the name of the tool and/or a brief description of its function. Change the ToolTip  property to Blaster .

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/viewport-tooltip.png)

## [Use scripts with tools](#use-scripts-with-tools)[](#use-scripts-with-tools)

A tool has three key events you can connect to: [Equipped](/docs/en-us/reference/engine/classes/Tool#Equipped) , [Unequipped](/docs/en-us/reference/engine/classes/Tool#Unequipped)  and [Activated](/docs/en-us/reference/engine/classes/Tool#Activated) .

| Event | | Description |
| --- | --- |
| **[Equipped](/docs/en-us/reference/engine/classes/Tool#Equipped)** | | Fired when a tool is equipped by the player, for example when a tool is selected in the hotbar. |
| **[Unequipped](/docs/en-us/reference/engine/classes/Tool#Unequipped)** | | Fired when a tool is unequipped by the player, for example when a tool is deselected in the hotbar. |
| **[Activated](/docs/en-us/reference/engine/classes/Tool#Activated)** | | Fired when a tool is activated by the player, for example when a player left-clicks. |

These methods only work in [LocalScripts](/docs/en-us/reference/engine/classes/LocalScript)  because only the player's device knows when input happens, such as a mouse button being clicked or a screen being touched.

## [Add the sounds](#add-the-sounds)[](#add-the-sounds)

To see these events in action, you can play a sound when they fire. First, you'll need to create Sound objects to use for this.

1.

Insert two [Sound](/docs/en-us/reference/engine/classes/Sound)  objects into the Handle .

2.

Rename one sound Equip  and set its SoundId property to rbxassetid://282906960 .

3.

Rename the other sound Activate  and set its SoundId property to rbxassetid://130113322 .

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/explorer-sounds.png)

## [Add the code](#add-the-code)[](#add-the-code)

The example code below plays the Equip  sound when the tool is equipped and the Fire  sound when activated.

1.

Insert a LocalScript  into the tool and name it ToolController .

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-player-tools/explorer-toolcontroller.png)

2.

Insert the following lines of code into the script.

```

local tool = script.Parent

local function toolEquipped()

	tool.Handle.Equip:Play()

end

local function toolActivated()

	tool.Handle.Activate:Play()

end

tool.Equipped:Connect(toolEquipped)

tool.Activated:Connect(toolActivated)

```

3.

Test the blaster sound effects by equipping and clicking to activate the tool.

Now you know how to create and script a basic tool, try creating other simple tools such as a flashlight or speaker.

[Next](/docs/en-us/tutorials/use-case-tutorials/scripting/intermediate-scripting/hit-detection-with-lasers)[Previous](/docs/en-us/tutorials/use-case-tutorials/scripting/intermediate-scripting/create-a-health-pickup)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
