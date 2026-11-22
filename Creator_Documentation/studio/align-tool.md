<!-- Source: https://create.roblox.com/docs/en-us/studio/align-tool -->

Align tool | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/studio/align-tool.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Studio](/docs/en-us/studio)

# Align tool

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/studio/align-tool.md)

The Align  tool, accessible from Studio's Model  tab toolbar or the Window  ⟩ 3D  menu, lets you align objects or groups of objects along the X , Y , or Z  axes.

 ![Align tool highlighted in Studio's toolbar.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Align.png)

Primary benefits include:

-

Aligning the center or edge of multiple objects in one action.

-

Aligning entire [Models](/docs/en-us/reference/engine/classes/Model)  or parts within them relative to other parts, all while keeping the model intact.

-

Dynamically previewing the point of alignment before confirming.

## [Mode](#mode)[](#mode)

You can set the alignment mode to either Min , Center , or Max .

![The Min icon in the toolbar.](https://prod.docsiteassets.roblox.com/assets/studio/align-tool/Icon-Min.png) Min

![The Center icon in the toolbar.](https://prod.docsiteassets.roblox.com/assets/studio/align-tool/Icon-Center.png) Center

![The Max icon in the toolbar.](https://prod.docsiteassets.roblox.com/assets/studio/align-tool/Icon-Max.png) Max

Min Center Max

![An angled side view of a small red cube, large blue cube, and a small purple cube that are aligned with the Min button on the world Z axis. A translucent orange rectangle represents where the objects align in context to each other.](https://prod.docsiteassets.roblox.com/assets/studio/align-tool/Mode-Min.jpg)

## [Align In](#align-in)[](#align-in)

The World  or Local  option specifies which relative coordinates to align on. This is especially useful for aligning parts which don't share the same orientation or rotation.

The X , Y , and Z  checkboxes let you select which axes to align on. Note that you can select multiple axes in a single alignment operation.

Before Alignment Max / World Z Max / Local Z

![An angled side view of a small red cube, large blue cube, and a small purple cube that are unaligned.](https://prod.docsiteassets.roblox.com/assets/studio/align-tool/Align-In-Before.jpg)

## [Relative To](#relative-to)[](#relative-to)

An alignment operation can be relative to either the Selection Bounds  or the Active Object .

### [Selection Bounds](#selection-bounds)[](#selection-bounds)

Selection Bounds  aligns the selected objects relative to the bounding box around them.

Before Alignment Min / World X Max / World X

![An angled side view of a small red cube, large blue cube, and a small purple cube that are unaligned. A translucent red rectangle represents where the objects' collective bounding box.](https://prod.docsiteassets.roblox.com/assets/studio/align-tool/Relative-To-Selection-Bounds-Before.jpg)

### [Active Object](#active-object)[](#active-object)

Active Object  aligns the objects relative to the last selected object . This object is outlined in orange and it will not move during the operation. While parts are selected, you can switch the active object by clicking on a different object.

Before Alignment Min / World X Max / World X

![An angled side view of a small red cube, large blue cube, and a small purple cube that are unaligned. The large blue cube has a yellow outline to represent that it's the active object.](https://prod.docsiteassets.roblox.com/assets/studio/align-tool/Relative-To-Active-Object-Before.jpg)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
