<!-- Source: https://create.roblox.com/docs/studio/overview -->

Studio interface | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/studio/overview.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Studio](/docs/en-us/studio)

# Studio interface

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/studio/overview.md)

## [Toolbar and mezzanine](#toolbar-and-mezzanine)[](#toolbar-and-mezzanine)

The toolbar  and mezzanine  reside at the top of Studio.

![Mezzanine and toolbar indicated in Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Mezzanine.png)

The left side of the mezzanine contains easily-accessible [testing controls](/docs/studio/testing-modes#playtest-options) .

![Testing controls indicated in Studio's mezzanine.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Controls.png)

The right side of the mezzanine contains buttons/menus for [collaboration](/docs/projects/collaboration) , sharing, [Assistant](/docs/assistant/guide) , creator notifications, and account options.

![Other options indicated in Studio's mezzanine.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Right.png)

In the center of the mezzanine are the default tool tabs of Home , Model , Avatar , UI , Script , and Plugins . You can also add [custom tabs](#custom-tabs)  for your specific needs.

![Default tabs indicated in Studio's mezzanine.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Default-Tabs.png)

Home Model Avatar UI Script Plugins

The Home  tab contains the core [transform](/docs/parts#transform-parts)  tools, [part inserter](/docs/parts#insert-parts) , the [color](/docs/parts#color)  and [material](/docs/parts#material)  widgets, the [group](/docs/parts#group)  and [lock](/docs/parts#lock)  tools, and [anchor](/docs/parts#anchor)  toggle. Also contains the [Terrain Editor](/docs/studio/terrain-editor) .

### [Appearance](#appearance)[](#appearance)

You can customize the appearance of the toolbar by right-clicking in an empty area within the mezzanine/toolbar and selecting from the following options:

-

Manage tabs  — Reveals a popup window with the following options:

![The Manage Tabs popup in Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Manage-Tabs-Popup.png)

1.

Show or hide the tab.

2.

With a tab selected, reorder it relative to the other tabs.

3.

Delete a selected [custom tab](#custom-tabs) .

4.

Choose between tabs Center  alignment or Left  alignment (next to the [testing controls](/docs/studio/testing-modes#playtest-options) ).

-

Collapse toolbar  — Maximizes space by hiding the toolbar while keeping the mezzanine visible. Hovering over a tab in the mezzanine temporarily reveals the toolbar.

-

Compact toolbar  — Makes the toolbar considerably more compact through smaller icons and labels, ideal for laptops or smaller monitors.

-

Show labels  — Toggles the text labels below tools on or off.

### [Custom tabs](#custom-tabs)[](#custom-tabs)

Beyond the default tool tabs, you can add custom tabs  for your specific needs, either through Studio's interface or by editing local .json  files.

Studio JSON

The easiest way to create custom tabs is through Studio's workflow.

1.

Click the +  button to the right of the default tabs, then type in a name for the new tab and press Enter .

 ![Button to add custom tab indicated in Studio's mezzanine.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Add-Custom-Tab.png)

Alternatively to creating a new, empty tab, you can duplicate any existing tab by right‑clicking it and selecting Duplicate tab . Unlike default tabs, tools within duplicated tabs can be freely modified.

2.

Click the button or right‑click in an empty region of the toolbar and select Add tools .

 ![Button to add new tool to a custom tab in Studio's toolbar.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Custom-Tab-Add-Tool.png)

3.

In the popup window, search for a tool and toggle its checkbox to add. New tools appear to the right of other tools, but you can right‑click any tool and select Move left  or Move right  to reorder it relative to other tools. You can also insert a divider by right‑clicking in an empty region of the toolbar and selecting Add divider .

 ![Custom tab populated with tools.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Custom-Tab-Filled.png)

If you need to remove a tool from a custom tab, right‑click it and select Remove tool .

## [3D viewport](#3d-viewport)[](#3d-viewport)

The 3D viewport represents the [Workspace](/docs/reference/engine/classes/Workspace)  of a place. From here, you can move the camera around the virtual world, manipulate objects with the mouse, and playtest a game without leaving Studio.

![An example viewport display of a desert environment with multiple stone pillars. One of the pillars displays movement visual aids from the Move tool.](https://prod.docsiteassets.roblox.com/assets/studio/general/Editor-Window.jpg) 3D viewport in Roblox Studio

### [Camera controls](#camera-controls)[](#camera-controls)

Inside the viewport, you can move the camera with the following controls.

| Keys/Shortcuts | | Action |
| --- | --- |
| W  A  S  D | | Moves the camera forward/left/back/right. |
| Q  E | | Moves the camera down/up. |
| Shift | | In combination with any movement key, changes the camera speed. |
| F | | Focuses the camera on a selected part. |
| Right Mouse Button | | When pressed, dragging the mouse moves the camera view around. |
| Mouse Scroll Wheel
Ctrl =  or ⌘ =
Ctrl -  or ⌘ -  or O | | Zooms the camera in or out.
Zooms the camera in.
Zooms the camera out. |
| ,  / . | | Rotates the camera left/right. If a part/model is in focus via the F  shortcut, rotates the camera counterclockwise/clockwise around that focused object. |
| Middle Mouse Button | | When pressed, dragging the mouse pans the camera. |
| Right Mouse Button  & Mouse Scroll Wheel | | Pressing the right mouse button and scrolling the mouse wheel up  increases the camera scroll speed. Conversely, pressing the right mouse button and scrolling the mouse wheel down  reduces the camera scroll speed.

This feature is currently in beta. Enable it through File  ⟩ Beta Features  ⟩ New Studio Camera Controls .

 |

### [Object selection](#object-selection)[](#object-selection)

As you hover over parts and models in the viewport, they are outlined to indicate their potential selection. You can select an outlined object by clicking it, or you can select multiple objects by holding Shift , Ctrl , or ⌘  as you hover over and click them.

 ![A warehouse environment with the stairs and multiple pallet box objects with a blue highlight to signify that they are selected in the 3D viewport.](https://prod.docsiteassets.roblox.com/assets/studio/general/Editor-Window-Object-Selection.jpg)

In more complex environments or when zoomed in, objects will commonly be hidden from your view by other objects in front. To select hidden objects without moving the camera around, hold Alt  or ⌥  and click to perform selection cycling  to the next further object behind the currently selected object.

When one or more objects or [models](/docs/parts/models)  are selected in the [Explorer](/docs/studio/explorer)  window, you can select all of their children  by right-clicking and choosing Hierarchy  ⟩ Select Children  from the context menu. Similarly, choosing Select Parent(s)  selects the direct parents  of those objects.

To customize the appearance of selection lines and boxes around objects, set your desired options in the Selection Visualization  section within the Selection  panel of Studio's settings.

 ![A warehouse environment with rope object's selection outline and bounding box highlighted.](https://prod.docsiteassets.roblox.com/assets/studio/general/Selected-Object-Bounding-Box.jpg)

### [Visualization options](#visualization-options)[](#visualization-options)

In the upper-right corner of the 3D viewport, you can quickly toggle or set common visualization options related to [on‑screen UI](/docs/ui/on-screen-containers)  overlays, [light sources](/docs/effects/light-sources) , physics simulation, character [pathfinding](/docs/characters/pathfinding) , and more. The menu also contains a control for viewing/setting the camera scroll speed.

 ![A close up view of the 3D viewport with the Visualization Options button indicated in the upper-right corner.](https://prod.docsiteassets.roblox.com/assets/studio/general/Visualization-Options.png)

## [Frequently-used tools](#frequently-used-tools)[](#frequently-used-tools)

Commonly used windows include the [Explorer](/docs/studio/explorer) , the [Properties](/docs/studio/properties)  window, [Asset Manager](/docs/projects/assets/manager) , [Toolbox](/docs/projects/assets/toolbox) , and others.

### [Explorer](#explorer)[](#explorer)

The [Explorer](/docs/studio/explorer)  window, visible by default and accessible from Studio's Window  menu or Home  tab, shows a hierarchical list of every object and service inside the place, collectively referred to as its data model . Frequently used services in the hierarchy include [Workspace](/docs/reference/engine/classes/Workspace)  which mirrors the [3D viewport](#3d-viewport) , as well as [ReplicatedStorage](/docs/reference/engine/classes/ReplicatedStorage)  and [ServerStorage](/docs/reference/engine/classes/ServerStorage) .

 ![Explorer hierarchy showing Camera, Terrain, and SignModel as children of Workspace; Board and Post as children of SignModel](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Parent-Child-Hierarchy.png)

### [Properties](#properties)[](#properties)

The [Properties](/docs/studio/properties)  window, visible by default and accessible from Studio's Window  menu or Home  tab, lets you adjust properties of a selected object to change how it looks and behaves. Object properties are divided into sections; for example, a [MeshPart](/docs/reference/engine/classes/MeshPart)  includes sections like Appearance  which allows you to change its color, material, transparency, and more.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Sections-Example.png)

At the bottom of the window, you can define custom [attributes](/docs/studio/properties#instance-attributes)  for an object, similar to its default properties. Attributes and their values are saved with your place/assets and they're an ideal way for team members to experiment with different values during runtime, even if they don't understand the underlying code.

 ![A close up view of the Attributes section of the Properties window.](https://prod.docsiteassets.roblox.com/assets/studio/properties/Attributes-Example.png)

### [Asset Manager](#asset-manager)[](#asset-manager)

The [Asset Manager](/docs/projects/assets/manager) , accessible from Studio's Window  menu or Home  tab, lets you manage places, images, meshes, audio, and more. It also provides a mechanism to bulk import large groups of assets.

### [Toolbox](#toolbox)[](#toolbox)

The [Toolbox](/docs/projects/assets/toolbox) , accessible from Studio's Window  menu or Home  tab, contains a selection of models, images, meshes, audio, plugins, videos, and fonts made by Roblox or Roblox community members. It also includes all of the creations that you've personally [distributed on the Creator Store](/docs/production/creator-store)  or those which were distributed by [groups](/docs/projects/groups)  you belong to.

 ![The Toolbox window.](https://prod.docsiteassets.roblox.com/assets/studio/toolbox/Model-Search-Example.png)

### [Output](#output)[](#output)

The [Output](/docs/studio/output)  window, accessible from Studio's Window  menu or Script  tab, displays errors captured from running scripts, messages from Roblox Engine, messages from calls to [print()](/docs/reference/engine/globals/LuaGlobals#print) , and errors from calls to [warn()](/docs/reference/engine/globals/RobloxGlobals#warn) .

### [Command Bar](#command-bar)[](#command-bar)

The Command Bar , accessible from Studio's Script  tab toolbar or the Window  ⟩ Script  menu, lets you execute Luau code outside of scripts. To quickly jump to the command bar at any time, press Ctrl 9  (Windows) or ⌘ 9  (Mac).

Most of the features outlined below are in beta and must be enabled through File  ⟩ Beta Features  ⟩ Multi-line Command Bar .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/general/Command-Bar.png)

Features include:

-

Multiline editing  — Press Enter  to insert new lines while typing. The bar starts with 2 lines, grows up to 10 lines as new lines are inserted, and shrinks as lines are deleted. When you're ready to run/execute the contents of the bar, click the Run  button or use the shortcut Ctrl Enter  (⌘ Enter ).

-

Command history  — The last 10 executed commands are visible by clicking the History  button and navigating to the Recent  tab. Clicking on a command in the list loads it into the bar, or you can navigate the list with ↑ / ↓  and insert the highlighted command with Enter . Alternatively, you can scrub through commands with Ctrl / ⌘  + ↑ / ↓  when the command bar is selected.

-

Saved commands  — You can explicitly save commands with the Save  button or the default shortcut Ctrl B  (⌘ B ). Saved commands can be accessed through the Saved  tab in the popup list, and the mechanics of loading saved commands from the list are the same as those in the command history.

-

Script Editor integration  — The command bar is an embedded script editor and supports a wide subset of Studio's [Script Editor](/docs/studio/script-editor)  features, including [autocomplete](/docs/studio/script-editor#autocomplete-features) , Luau [linting](https://luau.org/lint) , [go to declaration](/docs/studio/script-editor#go-to-declaration) , [function filter](/docs/studio/script-editor#script-function-filter) , [Code Assist](/docs/studio/script-editor#code-assist) , and [multi‑cursor](/docs/studio/script-editor#multi-cursor) .

## [Layout customization](#layout-customization)[](#layout-customization)

Studio's drag-and-drop interface lets you easily customize window layout to best suit your workflows.

### [Reposition windows](#reposition-windows)[](#reposition-windows)

You can reposition any window by click-dragging its header bar . As you begin dragging the window, the interface reveals empty docking area  regions. If you drag the mouse pointer into any empty region, a floating position selector  appears in that region. Dragging the pointer over the "center" of the floating selector targets the empty region as the dragged window's destination, indicated by the region darkening and becoming outlined.

![Mouse pointer hovering over the 'center' icon of the position selector in an empty docking area, showing that region as the dragged window's destination.](https://prod.docsiteassets.roblox.com/assets/studio/general/Docking-Position-Selector-Empty.png) Mouse pointer hovering over the "center" icon of the position selector in an empty docking area

If you drag the mouse pointer into a populated  region such as the 3D viewport, a floating position selector appears with multiple options for the window's destination. For example, dragging the pointer over the "left" icon will position the window on the region's left side.

Viewport left Viewport right

![Mouse pointer hovering over the 'left half' icon of the position selector in a populated region, showing the left side of the region as the dragged window's destination.](https://prod.docsiteassets.roblox.com/assets/studio/general/Docking-Position-Selector-Left.png)

### [Group windows](#group-windows)[](#group-windows)

If you drag a window into a populated  region and choose the "center" icon of the [position selector](#reposition-windows) , the dragged window will group into that region as a tab. This allows you to set up tab groups of commonly used windows.

![An example of an Explorer window if you choose the center icon of the position selection. It includes three tabs at the bottom of the window: the Explorer window, the Properties window, and the Terrain Editor window.](https://prod.docsiteassets.roblox.com/assets/studio/general/Docking-Grouped-Tabs.png) Three windows grouped together as tabs

### [Pin windows](#pin-windows)[](#pin-windows)

To maximize screen space for the 3D viewport, you can pin  windows (or an entire [group](#group-windows)  of windows) to the edges of the overall Studio window. Once pinned, you can temporarily open any window by clicking its tab — this does not disturb other windows, and the expanded window will automatically collapse when you click in another window or click its tab again.

![An example 3D viewport where the Explorer, Properties, and Terrain Editor windows are pinned to the right of the Studio window.](https://prod.docsiteassets.roblox.com/assets/studio/general/Docking-Pinned-Tabs.png) Three windows pinned to the right side of the Studio window

To pin a window or an entire [group](#group-windows)  of windows, click the "collapse" button. Alternatively, to un‑pin a pinned window/group, open it by clicking its tab, then click the "expand" button.

 ![A close up view of the Explorer window with the Collapse button highlighted.](https://prod.docsiteassets.roblox.com/assets/studio/general/Docking-Expand-Collapse.png)

### [Float windows](#float-windows)[](#float-windows)

To float a window freely of other windows, simply drag‑and‑drop it without selecting any icon from the floating [position selector](#reposition-windows) .

## [Window screenshots](#window-screenshots)[](#window-screenshots)

You can capture an image of an individual Studio window, such as the [Output](/docs/studio/output)  window, a plugin's window, or the viewport, without capturing the rest of Studio. This is useful for sharing the full Output window with your team or reporting an issue to a plugin's creator.

1.

Press Ctrl Shift 2 , or run the Screenshot Plugin  action from Studio's quick actions.

2.

Select the window you want to capture. The captured image is copied to your clipboard. Dialogs can't be captured.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
