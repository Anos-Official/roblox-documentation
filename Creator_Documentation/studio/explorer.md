<!-- Source: https://create.roblox.com/docs/en-us/studio/explorer -->

Explorer window | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/studio/explorer.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Studio](/docs/en-us/studio)

# Explorer window

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/studio/explorer.md)

The Explorer  window, accessible from Studio's Window  menu or Home  tab toolbar, shows a hierarchical list of every instance inside a game. At the highest level of the hierarchy are the services; [Workspace](/docs/en-us/reference/engine/classes/Workspace) , for example, is where visible 3D content such as [parts](/docs/en-us/parts)  are stored.

 ![Explorer highlighted in Studio's toolbar.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Explorer.png)

## [Parent-child hierarchy](#parent-child-hierarchy)[](#parent-child-hierarchy)

All children of a parent object appear under its branch when expanded. Click the arrow next to a parent branch — or press the → / ←  arrow keys when a parent is selected — to expand/collapse only that branch.

![Explorer hierarchy showing Camera, Terrain, and SignModel as children of Workspace; Board and Post as children of SignModel](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Parent-Child-Hierarchy.png)

![Only the topmost parent expanded with click](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Branch-Expanded.png)

To expand or collapse all  branches within a multi‑nested hierarchy, hold Shift  when clicking the expand/collapse arrow.

To change the parent of one or more children (reparent), simply drag and drop them onto the new parent.

 ![Dragging one object over another to reparent it](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Reparent-Object.png)

## [Object insertion](#object-insertion)[](#object-insertion)

While primitive [parts](/docs/en-us/parts)  can be [inserted](/docs/en-us/parts#insert-parts)  from the Home  or Model  tab toolbars, you can select from a full array of objects by hovering over the intended parent and clicking the ⊕ button (shortcut of Ctrl I  on Windows or ⌘ I  on Mac).

 ![Hovering over Workspace object to reveal insertion button](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Workspace-Add-Object.png)

You can further customize insertion behavior by clicking the ⋯  button to the right of the search field:

 ![Additional customization options for insertion workflow](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Insert-Object-Options.png)

| Option | | Description |
| --- | --- |
| Increment names for new instances | | When enabled, inserted/pasted/duplicated instances of the same type will have numbered names for differentiation. |
| Expand hierarchy when selecting | | When enabled, inserting/pasting an instance or selecting an object in the [3D viewport](/docs/en-us/studio/overview#3d-viewport)  will expand the Explorer  hierarchy to reveal that instance. When disabled, the top‑level parent within the hierarchy will be highlighted, but it won't expand to reveal the selected instance. |

To keep the hierarchy cleaner, services such as [VoiceChatService](/docs/en-us/reference/engine/classes/VoiceChatService)  are hidden by default. You can show hidden services by right‑clicking in the window and selecting Show Services…  from the context menu. Similarly, you can hide a visible service by right‑clicking it and selecting Hide Service in Explorer .

## [Duplicate and paste](#duplicate-and-paste)[](#duplicate-and-paste)

Objects can be quickly duplicated into the same branch, while items copied to the clipboard can be pasted into the top‑level [Workspace](/docs/en-us/reference/engine/classes/Workspace)  or directly into one or more existing parents.

| Action | | Windows | | Mac | | Description |
| Duplicate | | Ctrl D | | ⌘ D | | Duplicates the selected objects into the same branch. |
| Paste | | Ctrl V | | ⌘ V | | Pastes the clipboard contents into the top‑level [Workspace](/docs/en-us/reference/engine/classes/Workspace)  branch. |
| Paste Into | | Ctrl Shift V | | ⌘ Shift V | | Pastes the clipboard contents into the selected object(s). Using this action on multiple selected objects is a convenient way to paste the same clipboard items into multiple parents, such as a common [Texture](/docs/en-us/reference/engine/classes/Texture)  into several different [Parts](/docs/en-us/reference/engine/classes/Part) . |

When pasting 3D objects copied to the clipboard, you can maintain their original [CFrame](/docs/en-us/reference/engine/datatypes/CFrame)  position by right‑clicking the target parent instance in the hierarchy and selecting Paste Options  ⟩ Paste Into At Original Location .

## [Contextual options](#contextual-options)[](#contextual-options)

Right-clicking on an instance opens the options menu, contextually adjusted for the object type. For example, right‑clicking a [Model](/docs/en-us/reference/engine/classes/Model)  reveals standard options like Copy  and Duplicate , and also options specific to [Models](/docs/en-us/reference/engine/classes/Model)  like Ungroup . In contrast, right‑clicking a service like [Lighting](/docs/en-us/reference/engine/classes/Lighting)  reveals a more concise menu of actions valid for services.

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Context-Menu-Model.png)

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Context-Menu-Service.png)

## [Folder organization](#folder-organization)[](#folder-organization)

Like directories/folders on a computer, the [Folder](/docs/en-us/reference/engine/classes/Folder)  object is a useful way to organize objects. For instance, if you want to store all environmental audio assets in a logical place, you can create a folder and place multiple [AudioPlayer](/docs/en-us/reference/engine/classes/AudioPlayer)  objects within it.

 ![Multiple Sound objects grouped inside a Folder object](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Folder-Children.png)

You can organize objects into folders as follows:

-

Create a [Folder](/docs/en-us/reference/engine/classes/Folder)  instance through a standard [insertion](#object-insertion)  method, then drag and drop existing objects into it.

-

Select multiple objects, right-click them, and then select Group As a Folder  from the context menu (shortcut of Alt Ctrl G  on Windows or ⌥ ⌘ G  on Mac).

## [Search methods](#search-methods)[](#search-methods)

Through the search  input near the top of the window, you can find instances by [name](#name-search) , [property](#property-search) , class/subclass/tag [bespoke](#bespoke-search)  queries, and [ancestry](#ancestry-search)  queries. You can also [combine parameters](#combined)  for advanced logical searches. Quickly access this input by pressing Ctrl Shift X  (Windows) or ⌘ Shift X  (Mac).

 ![Example search query and search options](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Search-Diagram.png)

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-A.png)

Navigate up and down through search results

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-B.png)

Select all search results (Ctrl A  on Windows or ⌘ A  on Mac)

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-C.png)

Refresh search results

A name is a sequence of characters that are alphanumeric, _ , - , or . . In all of the following search methods, exercise caution when searching for instances whose names contain spaces, as the search logic may confuse spaces for a [combined search](#combined) . When searching for names with spaces, you should surround the full name with double quotes, for example tag:"Light Source"  to search by the full [tag](/docs/en-us/studio/properties#instance-tags)  name of Light Source .

### [Name search](#name-search)[](#name-search)

Typing in a basic string yields name  matched instances, case‑insensitive. For example, searching by the keyword script  finds all instances containing it, such as ServerScriptService  and LocalScript .

 ![Objects filtered by query of 'script'](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Search-By-Name.png)

### [Property search](#property-search)[](#property-search)

You can filter by property equality or value comparisons. Most properties are supported, it works with partial matches, ignores spacing, and is case‑insensitive.

Equality Value Comparisons Individual Fields Complete Units

Property equality  is searched through the operators =  or == .

| Example | | Result |
| ClassName = Decal | | All instances of class [Decal](/docs/en-us/reference/engine/classes/Decal) . |
| Locked = true | | [BaseParts](/docs/en-us/reference/engine/classes/BasePart)  with [Locked](/docs/en-us/reference/engine/classes/BasePart#Locked)  set to true . |
| Material == plas | | [BaseParts](/docs/en-us/reference/engine/classes/BasePart)  with [Material](/docs/en-us/reference/engine/classes/BasePart#Material)  of either [Plastic](/docs/en-us/reference/engine/enums/Material)  or [SmoothPlastic](/docs/en-us/reference/engine/enums/Material) . |

### [Bespoke search](#bespoke-search)[](#bespoke-search)

Classes, and subclasses, and tags are searched through various bespoke  queries, including:

-

is:[Class]  finds everything that is of class  [Class] . For example, is:Part  finds everything that is a [Part](/docs/en-us/reference/engine/classes/Part) .

-

is:[SubClass]  finds everything that is a subclass  of [SubClass] . For example, is:BasePart  finds everything that is a subclass of [BasePart](/docs/en-us/reference/engine/classes/BasePart) , such as [Part](/docs/en-us/reference/engine/classes/Part)  and [MeshPart](/docs/en-us/reference/engine/classes/MeshPart) .

-

tag:[TagName]  finds everything with a [CollectionService](/docs/en-us/reference/engine/classes/CollectionService)  tag of [TagName] . For example, tag:LightSource  finds everything that is tagged LightSource . You can add tags using the [Tags](/docs/en-us/studio/properties#instance-tags)  section of an instance's properties and tag names will autocomplete.

### [Ancestry search](#ancestry-search)[](#ancestry-search)

You can search within a specific scope using the .  operator, chain operators together for highly specific searches, or use *  as a wildcard.

-

[Parent].[Child]  finds named children inside a named parent. For example, workspace.Model  finds instances named Model  inside instances named workspace , similar to scripting.

-

Chaining .  operators adds specificity. For instance, Animals.Dog.Tail  finds objects named Tail  inside Dog  inside Animals .

-

*  acts as a wildcard, for instance:

| Example | | Result |
| Cart.* | | All children of an object named Cart . |
| Cart.Barrier.* | | All children of Barrier , itself a child of Cart . |
| Cart.*.* | | All grandchildren of Cart , excluding direct children of Cart . |
| Cart.*.Trim | | All grandchildren of Cart  that are named Trim . |

-

[Parent].**  finds all descendants of a parent. For example, CarModel.**  finds all descendants of CarModel .

### [Combined](#combined)[](#combined)

For advanced logical searches, you can combine queries through unions and grouping.

-

Multiple queries separated by spaces or and  operate on all  of the conditions.

| Example | | Result |
| Anchored=true CanCollide=true | | Every [BasePart](/docs/en-us/reference/engine/classes/BasePart)  that is anchored and can collide. |
| Cart.*.* Transparency < 1 | | All grandchildren of Cart  that are not fully transparent. |
| Anchored=false and CanCollide=false | | Every [BasePart](/docs/en-us/reference/engine/classes/BasePart)  that isn't anchored and can't collide. |

-

The or  conjunction operates just like the or  operator in code. Groups within parentheses, conjoined by or , find everything within multiple combined queries.

| Example | | Result |
| Cat or Dog | | Everything that has Cat  or Dog  in its name. |
| (Anchored=true CanCollide=true) or (Anchored=false CanCollide=false) | | Every [BasePart](/docs/en-us/reference/engine/classes/BasePart)  that either is anchored and can collide, or  isn't anchored and can't collide. |

## [Selection methods](#selection-methods)[](#selection-methods)

Within a [searched](#search-methods)  hierarchy, certain key shortcuts and mouse operations behave differently than they do within a non‑searched hierarchy.

### [Select all](#select-all)[](#select-all)

Within a non‑searched hierarchy, pressing Ctrl A  on Windows or ⌘ A  on Mac selects all instances. Within a [searched](#search-methods)  hierarchy, the same shortcut or the select all  button selects only the query‑matching objects, for example all objects matching Board  in a hierarchy searched for board .

 ![Image showing how only matching objects are selected in a searched hierarchy using the Select All shortcut](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Select-All-Searched.png)

### [Shift-select](#shift-select)[](#shift-select)

Clicking an object and Shift -clicking another object behaves differently within a non‑searched hierarchy versus a [searched](#search-methods)  hierarchy.

Non-Searched Hierarchy Searched Hierarchy

Within a non-searched hierarchy, Shift -clicking two objects at the same hierarchy level selects both of them and every object between which is also at the same hierarchy level, as shown in image 🅰  where LeftFoot  is initially clicked, LeftLowerArm  is Shift ‑clicked, and LeftHand  at same hierarchy level is also selected. Duplicating, copying, or pasting the selected objects will result in a deep copy of those objects and  all children.

If the first Shift -clicked object and the second Shift -clicked object are at different  hierarchy levels, all objects in between them will be selected, as shown in image 🅱  where LeftFoot  is initially clicked, LeftHand  is Shift ‑clicked, and everything between is also selected.

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Shift-Click-Non-Searched-A.png) Shift -click at same hierarchy level

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Shift-Click-Non-Searched-B.png) Shift -click at different hierarchy level

### [Drag select](#drag-select)[](#drag-select)

Clicking and dragging from an empty region of the window initiates a selection box. Within a non‑searched hierarchy, everything inside the box is selected. Within a [searched](#search-methods)  hierarchy, only query‑matching objects inside the box are selected.

![Image showing how only matching objects inside the selection box are selected within a searched hierarchy](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Drag-Select-Searched.png)

## [Key shortcuts](#key-shortcuts)[](#key-shortcuts)

| Shortcut | | Description |
| → | | With a collapsed branch selected, expands that branch. When pressed again, selects the first child  immediately under the parent node. |
| ← | | With any child of a branch selected, moves selection back to the parent node. When pressed again, collapses the entire branch. |
| Home | | Selects the topmost object in the hierarchy ([Workspace](/docs/en-us/reference/engine/classes/Workspace) ). |
| End | | Selects the bottommost object in the hierarchy. |
| PageUp | | Selects the object in the hierarchy that's above the topmost visible  hierarchy item. |
| PageDown | | Selects the object in the hierarchy that's below the bottommost visible  hierarchy item. |
| Ctrl Shift X
⌘ Shift X | | Jump to the [search input](#search-methods)  near the top of the window. |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
