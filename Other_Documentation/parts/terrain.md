<!-- Source: https://create.roblox.com/docs/parts/terrain -->

Environmental terrain | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/parts/terrain.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/workspace)

# Environmental terrain

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/parts/terrain.md)

Studio's [Terrain Editor](/docs/studio/terrain-editor)  lets you generate and sculpt detailed and realistic terrain environments such as mountains, bodies of water, grass-covered hills, or a flat desert. Terrain is made up of grids of voxels  which are 4×4×4 stud regions in the 3D world with a set material.

 ![Terrain Editor indicated in Studio's toolbar](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Terrain-Editor.png)  ![Desert terrain with mountains in the distance](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Showcase.jpg)

Using the editor tools, you can easily [generate](#generate-terrain)  and edit terrain either at a [voxel](#detailed-editing)  or [region](#large-scale-editing)  level with the option of importing a [heightmap](#heightmaps-and-colormaps)  and [colormap](#heightmaps-and-colormaps) . For more precise, dynamic, or procedural terrain editing, you can also [script](#scripting)  terrain creation.

## [Terrain materials](#terrain-materials)[](#terrain-materials)

The following default materials are available for terrain. You can also paint [custom terrain materials](/docs/parts/custom-terrain-materials)  after you enable Expanded Terrain , or apply [custom materials](/docs/parts/materials#custom-materials)  as overrides. Materials affect both the shape and appearance of terrain in the world; for example, [animated grass](#grass-animation)  renders only on the [Grass](/docs/reference/engine/enums/Material#Grass)  material and the [Water](/docs/reference/engine/enums/Material#Water)  material [ripples and shimmers](#water-appearance)  with a subtle motion.

![Appearance of Asphalt material](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Asphalt.jpg) Asphalt

![Appearance of Basalt material](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Basalt.jpg) Basalt

![Appearance of Brick material](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Brick.jpg) Brick

![Appearance of Cobblestone material](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Cobblestone.jpg) Cobblestone

![Appearance of Concrete material](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Concrete.jpg) Concrete

![Appearance of Cracked Lava material](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Cracked-Lava.jpg) Cracked Lava

![Appearance of Glacier material](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Glacier.jpg) Glacier

![Appearance of Grass material](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Grass.jpg) Grass

![Appearance of Ground material](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Ground.jpg) Ground

![Appearance of Ice material](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Ice.jpg) Ice

![Appearance of Leafy Grass material](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Leafy-Grass.jpg) Leafy Grass

![Appearance of Limestone material](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Limestone.jpg) Limestone

![Appearance of Mud material](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Mud.jpg) Mud

![Appearance of Pavement material](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Pavement.jpg) Pavement

![Appearance of Rock material](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Rock.jpg) Rock

![Appearance of Salt material](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Salt.jpg) Salt

![Appearance of Sand material](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Sand.jpg) Sand

![Appearance of Sandstone material](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Sandstone.jpg) Sandstone

![Appearance of Slate material](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Slate.jpg) Slate

![Appearance of Snow material](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Snow.jpg) Snow

![Appearance of Water material](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Water.jpg) Water

![Appearance of Wood Planks material](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Wood-Planks.jpg) Wood Planks

![Air material icon (no visual appearance)](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Air.png) Air

### [Water appearance](#water-appearance)[](#water-appearance)

By default, terrain water ripples, oscillates, and shimmers with a subtle motion.

To customize the color and motion of water:

1.

In the Explorer  window, navigate to the [Workspace](/docs/reference/engine/classes/Workspace) , then select the [Terrain](/docs/reference/engine/classes/Terrain)  object.

 ![Terrain object shown in Explorer window of Studio](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Workspace-Terrain.png)

2.

In the Properties  window, customize the appearance of water through the following properties:

| Property | | Description |
| --- | --- |
| [WaterColor](/docs/reference/engine/classes/Terrain#WaterColor) | | Adjusts the overall hue of all terrain water in the game. |
| [WaterReflectance](/docs/reference/engine/classes/Terrain#WaterReflectance) | | Adjusts how much water surfaces reflect the sky and surrounding objects from a value of 1 (high) to 0 (none). |
| [WaterTransparency](/docs/reference/engine/classes/Terrain#WaterTransparency) | | Adjusts how transparent water is from a value of 1 (clear) to 0 (opaque). |
| [WaterWaveSize](/docs/reference/engine/classes/Terrain#WaterWaveSize) | | Adjusts the size of waves from a value of 1 (large) to 0 (none). |
| [WaterWaveSpeed](/docs/reference/engine/classes/Terrain#WaterWaveSpeed) | | Adjusts the speed of waves from a value of 100 (turbulent) to 0 (still). |

Some water properties are only visible while playtesting. To preview all properties while editing, open [Studio Settings](/docs/studio/setup#customization) , search for Editor Quality Level , and set it to the highest level.

### [Grass animation](#grass-animation)[](#grass-animation)

While most materials are static, you can add animated blades of grass to the [Grass](/docs/reference/engine/enums/Material#Grass)  terrain material. By default, grass sways gently in a simulated wind, and you can adjust the direction/strength of its animation through [global wind](/docs/environment/global-wind) .

Note that the speed of animated grass — but not its vector direction — will be reduced if the player has toggled on the Reduce Motion  [accessibility](/docs/production/publishing/accessibility#reduced-motion)  setting from the Roblox or in-game Settings  menu.

To add animated grass to the [Grass](/docs/reference/engine/enums/Material#Grass)  material:

1.

In the Explorer  window, navigate to the [Workspace](/docs/reference/engine/classes/Workspace) , then select the [Terrain](/docs/reference/engine/classes/Terrain)  object.

 ![Terrain object shown in Explorer window of Studio](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Workspace-Terrain.png)

2.

In the Properties  window, toggle on the [Decoration](/docs/reference/engine/classes/Terrain#Decoration)  property.

 ![Decoration property of Terrain object in Properties window of Studio](https://prod.docsiteassets.roblox.com/assets/studio/properties/Terrain-Decoration.png)

3.

Adjust the grass length by entering a value between 0.1  and 1  for the [GrassLength](/docs/reference/engine/classes/Terrain#GrassLength)  property.

 ![GrassLength property of Terrain object in Properties window of Studio](https://prod.docsiteassets.roblox.com/assets/studio/properties/Terrain-GrassLength.png)  ![GrassLength comparison depicted on rolling grassland hills.](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Terrain-GrassLength.jpg)

4.

Adjust the direction and strength of its animation through [global wind](/docs/environment/global-wind) .

### [Custom terrain colors](#custom-terrain-colors)[](#custom-terrain-colors)

Each terrain material is assigned a default color, but you can customize any material's color to better fit your game.

Default Fantasy Tundra

![Default terrain colors used in desert landscape](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Showcase.jpg)

To customize any material color other than water:

1.

In the Explorer  window, navigate to the [Workspace](/docs/reference/engine/classes/Workspace) , then select the [Terrain](/docs/reference/engine/classes/Terrain)  object.

 ![Terrain object shown in Explorer window of Studio](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Workspace-Terrain.png)

2.

In the Properties  window, expand [MaterialColors](/docs/reference/engine/classes/Terrain#MaterialColors) . All materials display with their RGB code.

 ![MaterialColors property shown in Properties window of Studio](https://prod.docsiteassets.roblox.com/assets/studio/properties/Terrain-MaterialColors-Expand.png)

3.

For any material, either input a new RGB code or click the color box to open the [colors popup](/docs/parts#color) .

## [Generate terrain](#generate-terrain)[](#generate-terrain)

Using the following tools and methods, you can generate large areas of terrain procedurally through tooling or scripting, or automatically based on a heightmap and colormap.

### [Generate tool](#generate-tool)[](#generate-tool)

The Generate  tool allows you to procedurally generate terrain in seconds. This is useful if you want to create a large map and fine-tune [terrain details](#detailed-editing) .

1.

In the editor window, navigate to the Create  tab and select the Generate  tool.

 ![Generate tool indicated in Create tab of Terrain Editor](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Create-Tab-Generate.png)

2.

In the 3D viewport, move/resize the selection region  in which to generate terrain. Alternatively, expand the tool's Selection Settings  and enter values into the X / Y / Z  inputs to set a specific size and position.

3.

In the tool's Biome Settings  section, choose the following biomes to include in the new terrain:

-

Arctic

-

Dunes

-

Canyons

-

Lavascape

-

Water

-

Mountains

-

Hills

-

Plains

-

Marsh

4.

Click the Generate  button.

### [Heightmaps and colormaps](#heightmaps-and-colormaps)[](#heightmaps-and-colormaps)

A heightmap  is a 2D representation of a 3D terrain map, as viewed directly from above. Brighter areas of a heightmap result in higher terrain, like mountains, while darker areas result in lower regions, like valleys.

An optional colormap , along with a heightmap, converts colors to terrain materials using a color key .

![Example heightmap image](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Terrain-Heightmap.png) Heightmap

![Example colormap image](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Terrain-Colormap.png) Colormap

![Terrain generated from the example heightmap and colormap](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Terrain-Colormap-Result.jpg) Generated terrain

1 pixel in a heightmap represents 4 studs in Studio, and Studio supports a maximum of 4096×4096 pixels in either .jpg  or .png  format.

To import a heightmap and optional colormap:

1.

In the editor window, navigate to the Create  tab and select the Import  tool.

 ![Import tool indicated in Create tab of Terrain Editor](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Create-Tab-Import.png)

2.

In the tool's Map Settings  section, click the import button and choose the image you want to import as a heightmap.

3.

In the tool's Material Settings  section, select a terrain material or, alternatively, upload a colormap.

Material Colormap

To apply one consistent material across all of the generated terrain, select the Material  tab and pick a terrain material.

4.

In the 3D viewport, move/resize the selection region  in which to generate terrain. Alternatively, enter values into the Select  tool fields to set a more specific position and size.

Minimum and maximum terrain heights depend on the darkest and lightest areas of the heightmap image in relation to the Y  size (height) of the selection region. For instance, if you choose a height of 128, pure black areas are 64 studs below the center position and pure white areas are 64 studs above the center position.

5.

Click the Generate  button.

### [Scripting](#scripting)[](#scripting)

You can script terrain generation using the [Terrain](/docs/reference/engine/classes/Terrain)  class. For example, to create terrain with grass material that fills a volume, you can use methods such as [FillBall()](/docs/reference/engine/classes/Terrain#FillBall) , [FillBlock()](/docs/reference/engine/classes/Terrain#FillBlock) , [FillCylinder()](/docs/reference/engine/classes/Terrain#FillCylinder) , [FillRegion()](/docs/reference/engine/classes/Terrain#FillRegion) , or [FillWedge()](/docs/reference/engine/classes/Terrain#FillWedge) .

Fill Block Volume

```

local Workspace = game:GetService("Workspace")

Workspace.Terrain:FillBlock(CFrame.new(0, 0, 0), Vector3.new(4, 4, 4), Enum.Material.Grass)

```

## [Large-scale editing](#large-scale-editing)[](#large-scale-editing)

The editor's Edit  tab contains tools for large-scale editing.

### [Select regions](#select-regions)[](#select-regions)

The Select  tool is the universal tool for selecting rectangular regions of terrain.

 ![Select tool indicated in Edit tab of Terrain Editor](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Edit-Tab-Select.png)

Select a region by clicking and dragging in the 3D viewport, reposition it with the move  draggers, and edit its size with the scale  handles. Alternatively, enter values into the tool's X / Y / Z  inputs to set a specific position and size.

![Move draggers and scale handles on a selected region](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Select-Region-Labeled.jpg) Move draggers and scale handles on a selected region

Studio also supports the following keyboard and mouse shortcuts, assuming the Select tool is active and nothing is selected in the Explorer  window.

| Windows | | Mac | | Action |
| Ctrl C | | ⌘ C | | Copy terrain within the selected region to the clipboard. |
| Ctrl V | | ⌘ V | | Paste terrain that has been copied to the clipboard and swap to the Transform tool so that the new terrain can be transformed. |
| Ctrl X | | ⌘ X | | Cut terrain within the selected region to the clipboard. |
| Ctrl D | | ⌘ D | | Duplicate terrain within the selected region and swap to the Transform tool so that the new terrain can be transformed. |
| Delete | | Delete | | Delete terrain within the selected region. |
| Shift | | Shift | | When held down while dragging any scale  handle, scales the region proportionally across all other axes. |
| Ctrl | | ⌘ | | When held down while dragging any scale  handle, scales the region equally in both the positive and negative direction along that axis. |

### [Transform regions](#transform-regions)[](#transform-regions)

The Transform  tool lets you manipulate entire selected regions to a new position, size, or orientation.

To transform a region:

1.

Select a region and then activate the Transform  tool. Note that the tool will be automatically activated if you paste or duplicate terrain.

 ![Transform tool indicated in Edit tab of Terrain Editor](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Edit-Tab-Transform.png)

2.

In the 3D viewport, transform the region with the move  draggers, rotate  rings, and scale  handles. Alternatively, enter values into the tool's X / Y / Z  inputs to set a specific position, size, and rotation.

 ![Move draggers, scale handles, and rotate rings on the Y axis of a selected region](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Transform-Region-Labeled.jpg)

Holding Shift  while dragging any scale  handle scales the region proportionally across all other axes, and holding Ctrl  or ⌘  while dragging scales the region equally in both the positive and negative direction along that axis.

Holding Shift  while dragging any rotate  ring toggles between rotation snapping or free‑form rotation.

By default, this tool uses Live Edit  mode to constantly update terrain as you transform it. To view only a wireframe preview of the terrain as you transform it, disable live edit mode and then, while transforming, press Enter / Return  or click the Apply  button to apply the changes.

### [Fill and replace regions](#fill-and-replace-regions)[](#fill-and-replace-regions)

The Fill  tool lets you fill an entire selected region with a specific material, or replace all material within the region with another material.

1.

Select a region, then activate the Fill  tool.

 ![Fill tool indicated in Edit tab of Terrain Editor](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Edit-Tab-Fill.png)

2.

In the tool's Material Settings  section:

-

To fill the region with a specific material, select Fill  and choose the desired material.

-

To replace all terrain of one material with another material, select Replace , then choose a source  material and target  material.

3.

Click the Apply  button or press Enter / Return .

![Region filled with Salt material](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Fill-Region.jpg) Selected region filled with Salt material

### [Set sea level](#set-sea-level)[](#set-sea-level)

The Sea Level  tool lets you create a consistent water level or remove all water within a region.

1.

Activate the Sea Level  tool.

 ![Sea Level tool indicated in Edit tab of Terrain Editor](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Edit-Tab-Sea-Level.png)

2.

Select the intended region by clicking and dragging the move  draggers and scale  handles in the 3D viewport. Alternatively, enter values into the tool's X / Y / Z  inputs to set a specific position and size.

3.

Click the Evaporate  button to remove water inside the selected region, or click the Create  button to fill the selected region with water.

## [Detailed editing](#detailed-editing)[](#detailed-editing)

The Edit  tab also contains tools for precision editing using a "brush" tool to draw, sculpt, smooth, flatten, or paint terrain.

 ![Detailed editing tools indicated in Edit tab of Terrain Editor](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Edit-Tab-Detail-Tools.png)

Each tool lets you choose from a sphere , box , or cylinder  brush shape and a base size between 1–64 studs.

 ![Brush shape and size controls in the Terrain Editor](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Brush-Shape-Size.png)

For tools which use the brush, Studio supports the following keyboard and mouse shortcuts.

| Windows | | Mac | | Action |
| Ctrl | | ⌘ | | When held down while using the [Draw](/docs/studio/terrain-editor#draw)  and [Sculpt](/docs/studio/terrain-editor#sculpt)  tools, toggles on the alternate brush mode. For example, toggles on "subtract" mode instead of the default "add" mode. |
| Shift | | Shift | | When held down while using the [Draw](/docs/studio/terrain-editor#draw)  and [Sculpt](/docs/studio/terrain-editor#sculpt)  tools, temporarily activates the [Smooth](/docs/studio/terrain-editor#smooth)  tool. |
| B | | B | | When held down while dragging the mouse or using the scroll wheel, adjusts the brush's base size . |
| Ctrl B | | ⌘ B | | When held down while dragging the mouse or using the scroll wheel, adjusts the brush's height . Only applies if the brush's shape is set to box  or cylinder . |
| Shift B | | Shift B | | When held down while dragging the mouse or using the scroll wheel, adjusts the brush's strength . Only applies when using the [Sculpt](/docs/studio/terrain-editor#sculpt) , [Smooth](/docs/studio/terrain-editor#smooth) , or [Flatten](/docs/studio/terrain-editor#flatten)  tool. |
| Alt | | ⌥ | | When held down on mouse click, shows the material picker. |

### [Draw](#draw)[](#draw)

The Draw  tool adds  or subtracts  terrain using the brush. This tool functions in a dual mode where holding down Ctrl  or ⌘  toggles on "subtract" mode instead of the default "add" mode. Additionally, holding down Shift  temporarily activates the [Smooth](/docs/studio/terrain-editor#smooth)  tool.

### [Sculpt](#sculpt)[](#sculpt)

The Sculpt  tool adds  or subtracts  terrain using the brush. Unlike the Draw tool, this tool includes a strength  slider to allow for more gentle manipulation of terrain.

Similar to the Draw tool, the Sculpt tool functions in a dual mode where holding down Ctrl  or ⌘  toggles on "subtract" mode instead of the default "add" mode. Additionally, holding down Shift  temporarily activates the Smooth tool.

### [Smooth](#smooth)[](#smooth)

The Smooth  tool smoothes out abrupt edges in terrain using the brush. This tool can be used in standalone mode, or you can toggle it on by holding Shift  while using the Draw or Sculpt tools.

### [Flatten](#flatten)[](#flatten)

The Flatten  tool flattens terrain to a consistent level across a visualized plane. By default, the tool lowers terrain above the plane and  raises terrain below to the plane, but you can opt to selectively lower or  raise through the tool's Flatten Mode  option.

### [Paint](#paint)[](#paint)

The Paint  tool, using the brush, paints  a terrain material over an existing material or replaces  one material with another material.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
