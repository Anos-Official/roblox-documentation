<!-- Source: https://create.roblox.com/docs/en-us/parts -->

Parts | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/parts.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/en-us/workspace)
6. /
7. [Parts](/docs/en-us/parts)

# Parts

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/parts/index.md)

[Parts](/docs/en-us/reference/engine/classes/Part)  are descendants of the [BasePart](/docs/en-us/reference/engine/classes/BasePart)  class and are Roblox's primitive building blocks with properties like position, size, orientation, and color. You can use basic parts as is, or you can apply [solid modeling](/docs/en-us/parts/solid-modeling)  operations to combine parts into more complex shapes.

For advanced and intricate 3D models, you can also import third-party model files as [MeshParts](/docs/en-us/reference/engine/classes/MeshPart)  as outlined in [Meshes](/docs/en-us/parts/meshes) .

![A single gray sphere part](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Basic-Part-Sphere.png) Basic sphere part

![A bright blue hollow bowl that was made with solid modeling operations.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Part-Example-CSG.jpg) Bowl created with solid modeling

![A high-quality treasure chest mesh with a texture.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Mesh-Example.jpg) Mesh with texture

By default, parts are rigid bodies that follow real-world physical mechanics, including gravity, collision, and momentum. You can connect related parts together as a single [assembly](/docs/en-us/physics/assemblies)  using a [WeldConstraint](/docs/en-us/reference/engine/classes/WeldConstraint) , or a joint like [Motor6D](/docs/en-us/reference/engine/classes/Motor6D)  or [Bone](/docs/en-us/reference/engine/classes/Bone) . As an assembly, the connected parts act as a single rigid entity, referencing a common position, orientation, and scale.

You can use a [Model](/docs/en-us/reference/engine/classes/Model)  container to group related parts together and access the group as a single assembly in the [Explorer](/docs/en-us/studio/explorer) . See [Models](/docs/en-us/parts/models)  for more information.

## [Basic part types](#basic-part-types)[](#basic-part-types)

[Part](/docs/en-us/reference/engine/classes/Part)  objects can take the shape of blocks, spheres, cylinders, wedges, or corner wedges. In addition, [TrussPart](/docs/en-us/reference/engine/classes/TrussPart)  acts as a truss beam that characters can climb like a ladder.

![A single Block part.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Basic-Part-Block.png) Block

![A single Sphere part.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Basic-Part-Sphere.png) Sphere

![A single Cylinder part.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Basic-Part-Cylinder.png) Cylinder

![A single Wedge part.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Basic-Part-Wedge.png) Wedge

![A single Corner Wedge part.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Basic-Part-Corner-Wedge.png) Corner Wedge

## [Part properties](#part-properties)[](#part-properties)

Each part has a variety of properties that you can customize through the [Properties](/docs/en-us/studio/properties)  window.

 ![A close up view of the Properties window with the Appearance and Transform properties highlighted.](https://prod.docsiteassets.roblox.com/assets/studio/properties/Sections-Example.png)

The following are commonly utilized properties:

-

[Anchored](/docs/en-us/reference/engine/classes/BasePart)  controls if physics affects the position of the part. When this property is set to true, the part never changes position due to gravity or any other force. You should anchor most parts in your game or gravity and physics will affect your parts as soon as the game runs.

To view lighted outlines around the base of anchored parts in order to visualize which parts cannot move under gravity or physics, toggle on Anchored parts  from the [Visualization Options](/docs/en-us/studio/overview#visualization-options)  widget in the upper‑right corner of the 3D viewport.

-

[CanCollide](/docs/en-us/reference/engine/classes/BasePart)  controls whether or not a part can collide with other parts. When this property is set to true, the part is impenetrable and the physics engine accounts for it within your game. Conversely, when this property is set to false, the part can pass through anything, and the physics engine does not  account for it.

-

[Transparency](/docs/en-us/reference/engine/classes/BasePart)  sets a part's visibility to any value between the default value of 0 (fully visible) and 1 (fully transparent). If you have many partially transparent parts, they can slow down performance. To alleviate this, merge them using [solid modeling](/docs/en-us/parts/solid-modeling) .

## [Insert parts](#insert-parts)[](#insert-parts)

The Part  insertion button, accessible from the Home  and Model  tab toolbars, inserts a new part into the workspace. Click‑holding over the small corner arrow on the button lets you select either Block , Sphere , Wedge , Corner Wedge , or Cylinder .

 ![Part tool and its part type picker menu.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Insert-Part-Widget.png)

To insert a [TrussPart](/docs/en-us/reference/engine/classes/TrussPart)  (not available on the insertion menu), use the [Explorer](/docs/en-us/studio/explorer)  as outlined [here](/docs/en-us/studio/explorer#insert-and-parent) .

## [Select parts](#select-parts)[](#select-parts)

As you hover over parts in the 3D viewport, they are outlined to indicate their potential selection. You can select an outlined part by clicking it, or you can select multiple parts by holding Shift , Ctrl , or ⌘  as you hover over and click them. For advanced methods of selecting parts in the viewport, see [object selection](/docs/en-us/studio/overview#object-selection) .

 ![Multiple models selected in 3D viewport](https://prod.docsiteassets.roblox.com/assets/studio/general/Editor-Window-Object-Selection.jpg)

## [Transform parts](#transform-parts)[](#transform-parts)

You can move, scale, and rotate selected parts either through modeling tools or by setting a new position, size, or orientation in the [Properties](#part-properties)  window.

 ![Transform tools indicated in Studio's toolbar.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Transform-Tools.png)

![Move draggers shown on part in 3D viewport.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Transform-Move-SM.png) Move

![Scale draggers shown on part in 3D viewport.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Transform-Scale-SM.png) Scale

![Rotate draggers shown on part in 3D viewport.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Transform-Rotate-SM.png) Rotate

When using the tools, you can move, scale, or rotate parts in either world  orientation or local  orientation by pressing Ctrl L  on Windows or ⌘ L  on Mac. When you enable local orientation, the arrow axis indicators change to a part's local orientation, and an L  indicator displays.

World Local

![An angled block part with draggers in World orientation mode.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Move-World-Orientation.png)

Tool transform snapping  increments are based on studs  for moving/scaling or degrees  for rotating, each adjustable in the toolbar. While transforming, you can temporarily toggle snapping by holding the Shift  key.

 ![Transform snapping tools indicated in Studio's toolbar.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Transform-Snapping.png)

To quickly jump to the move/scale  increment input, press Shift 2 . To quickly jump to the rotate  increment input, press Alt R  (Windows) or ⌥ R  (Mac).

### [Move](#move)[](#move)

You can move a selected part to a new position using the Move  tool (default shortcut 2 ) or by cursor dragging . While moving a part, you can temporarily toggle snapping by holding Shift .

Move Tool Cursor Drag

To move a part by an axis dragger along the X , Y , or Z  axis, click/drag an arrow pointing along the desired axis of movement.

![A block part with the Move tool's visual aids.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Transform-Move.png)

After releasing the drag, the numerical distance indicator  remains visible. If desired, fine‑tune the distance that was moved by clicking inside the indicator and entering any number.

![A moved part showing the distance moved in an indicator/input field](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Transform-Move-Indicator.png)

If you drag a part by its [pivot](/docs/en-us/studio/pivot-tools)  point while the Move  tool is selected, the pivot will "soft snap" to surfaces and edges of nearby parts.

![A block part with an offset pivot soft-snapping to the surface of a nearby part.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Transform-Move-Pivot-Snap.png)

### [Scale](#scale)[](#scale)

To scale (resize) a selected part along the X , Y , or Z  axis, use the Scale  tool (default shortcut 3 ) and click/drag a handle. While dragging, you can temporarily toggle snapping by holding Shift .

 ![A block part with the Scale tool's visual aids.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Transform-Scale.png)

### [Rotate](#rotate)[](#rotate)

To rotate a selected part around the X , Y , or Z  axis, use the Rotate  tool (default shortcut 4 ) and click/drag a rotation ring. While dragging, you can temporarily toggle snapping by holding Shift .

 ![A block part with the Rotate tool's visual aids.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Transform-Rotate.png)

In addition to using the Rotate  tool, you can quickly rotate selected objects 90° about their X  axis by pressing Ctrl T  (⌘ T ) or 90° about their Y  axis by pressing Ctrl R  (⌘ R ).

## [Other actions](#other-actions)[](#other-actions)

### [Group](#group)[](#group)

You can group objects into a [model](/docs/en-us/parts/models)  by selecting them and clicking the Group  button. This action has a default shortcut of Ctrl G  (Windows) or ⌘ G  (Mac).

Alternatively, you can group objects into a [folder](/docs/en-us/studio/explorer#organizing-by-folders)  by click‑holding over the small corner arrow on the button and selecting Group as Folder  (default shortcut of Alt Ctrl G  or ⌥ ⌘ G ).

 ![Group tool indicated in Studio's toolbar](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Group.png)

To ungroup  an existing model or folder, select Ungroup  from the Edit  menu (default shortcut of Ctrl U  or ⌘ U ).

### [Anchor](#anchor)[](#anchor)

The Anchor  toggle controls whether the part will be immovable  by physics. When [Anchored](/docs/en-us/reference/engine/classes/BasePart#Anchored) , a part will never change position due to gravity, other parts collisions, overlapping other parts, or any other physics-related causes. This action has a default shortcut of Alt A  (Windows) or ⌥ A  (Mac).

 ![Anchor toggle indicated in Studio's toolbar](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Anchor.png)

If you prefer a click-to-toggle workflow in the 3D viewport, click‑hold over the small corner arrow on the Anchor  button and enable Click object to anchor . Once enabled, the tool operates as a "key" for both states — clicking on an unanchored object in the viewport anchors it, while clicking on an anchored object unanchors it.

### [Color](#color)[](#color)

While a part is gray by default, you can change it to any color through the following methods.

Color Button Color Popup RGB Value

Clicking the Color  button applies the selected color to all selected parts. You can choose a color by click‑holding over the small corner arrow on the Color  button to reveal a hexagonal picker.

![Color widget's hexagonal picker.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Color-Picker.png)

If you prefer a fill/paint workflow in the 3D viewport, enable Click object to apply color  at the bottom of the hexagonal picker popup and then click parts in the viewport to apply the chosen color.

### [Material](#material)[](#material)

Similar to [color](#color) , you can customize a part's [material](/docs/en-us/parts/materials)  to simulate real‑world materials such as wood, glass, or fabric. Click‑holding over the small corner arrow on the Material  button reveals the [material](/docs/en-us/parts/materials)  picker.

 ![Material widget's picker highlighted.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Material-Picker.png)

When selecting a material, consider the following:

-

Material affects the physical traits of a part, not just its appearance . For example, the [Concrete](/docs/en-us/reference/engine/enums/Material#Concrete)  material is heavier than the [Plastic](/docs/en-us/reference/engine/enums/Material#Plastic)  material, so a concrete brick will have higher density than a plastic brick and sink in water faster.

-

Some materials have special physical effects. For example, parts will appear to glow if they are set to the [Neon](/docs/en-us/reference/engine/enums/Material#Neon)  material.

![An angled red block part with a smooth plastic material.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Material-SmoothPlastic.png) SmoothPlastic

![An angled red block part with a glowing neon material.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Material-Neon.png) Neon

See [Materials](/docs/en-us/parts/materials)  for more information on how to apply both default and custom materials to parts.

### [Lock](#lock)[](#lock)

The Lock  toggle controls whether the part can be selected from the 3D viewport. This action has a default shortcut of Alt L  (Windows) or ⌥ L  (Mac).

 ![Lock tool indicated in Studio's toolbar](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Lock.png)

If you prefer a click-to-toggle workflow in the 3D viewport, click‑hold over the small corner arrow on the Lock  button and enable Click object to lock . Once enabled, the tool operates as a "key" for both states — clicking on an unlocked object in the viewport locks it, while clicking on a locked object unlocks it.

To unlock all objects, select Unlock All  from the Edit  menu.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
