<!-- Source: https://create.roblox.com/docs/en-us/physics/mechanical-constraints -->

Mechanical constraints | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/physics/mechanical-constraints.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/en-us/workspace)
6. /
7. [Physics](/docs/en-us/physics)
8. /
9. [Mechanical constraints](/docs/en-us/physics/mechanical-constraints)

# Mechanical constraints

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/physics/mechanical-constraints.md)

The physics engine includes the following [Constraints](/docs/en-us/reference/engine/classes/Constraint)  that behave as conceptual mechanical connections, including hinges, springs, ropes, and more. In addition, various [mover constraints](/docs/en-us/physics/mover-constraints)  are available to exert directional or rotational force upon [assemblies](/docs/en-us/physics/assemblies) .

[Ball Socket](/docs/en-us/physics/constraints/ball-socket)

[BallSocketConstraint](/docs/en-us/reference/engine/classes/BallSocketConstraint)  forces its two attachments into the same position and allows them to freely rotate about all three axes, with optional limits to restrict both tilt and twist

[Hinge](/docs/en-us/physics/constraints/hinge)

[HingeConstraint](/docs/en-us/reference/engine/classes/HingeConstraint)  allows its two attachments to rotate about one axis, with optional assigned power for motor or servo behavior

[Prismatic](/docs/en-us/physics/constraints/prismatic)

[PrismaticConstraint](/docs/en-us/reference/engine/classes/PrismaticConstraint)  allows two attachments to slide along one axis but not rotate, with optional assigned power for mechanisms like sliding doors and elevator platforms

[Cylindrical](/docs/en-us/physics/constraints/cylindrical)

[CylindricalConstraint](/docs/en-us/reference/engine/classes/CylindricalConstraint)  allows its attachments to slide along one axis and rotate about another axis, with optional assigned angular and/or linear power

[Spring](/docs/en-us/physics/constraints/spring)

[SpringConstraint](/docs/en-us/reference/engine/classes/SpringConstraint)  applies a force on its attachments based on spring and damper behavior, with an optional minimum/maximum length

[Torsion Spring](/docs/en-us/physics/constraints/torsion-spring)

[TorsionSpringConstraint](/docs/en-us/reference/engine/classes/TorsionSpringConstraint)  applies torque based on a relative angle and relative angular velocity, in an attempt to bring two axes from two parts together

[Universal](/docs/en-us/physics/constraints/universal)

[UniversalConstraint](/docs/en-us/reference/engine/classes/UniversalConstraint)  ensures two axes on two assemblies remain perpendicular, useful for applications such as vehicle power transmission to rear drive shafts, robotics, and more

[Rope](/docs/en-us/physics/constraints/rope)

[RopeConstraint](/docs/en-us/reference/engine/classes/RopeConstraint)  prevents two attachments from separating further than a defined length, with optional behavior as an extending or contracting winch

[Rod](/docs/en-us/physics/constraints/rod)

[RodConstraint](/docs/en-us/reference/engine/classes/RodConstraint)  keeps two attachments separated by a defined length, with optional limits on rotational tilt

[Plane](/docs/en-us/physics/constraints/plane)

[PlaneConstraint](/docs/en-us/reference/engine/classes/PlaneConstraint)  moves two attachments into a position/orientation along a plane, and both attachments remain free to translate and rotate unless otherwise constrained

[Weld](/docs/en-us/physics/constraints/weld)

[WeldConstraint](/docs/en-us/reference/engine/classes/WeldConstraint)  connects two [BaseParts](/docs/en-us/reference/engine/classes/BasePart)  and ensures they stay in the same relative position and orientation to each other, even if they are not touching

[Rigid](/docs/en-us/physics/constraints/rigid)

[RigidConstraint](/docs/en-us/reference/engine/classes/RigidConstraint)  connects two [Attachments](/docs/en-us/reference/engine/classes/Attachment)  or [Bones](/docs/en-us/reference/engine/classes/Bone)  and ensures they stay in the same relative position/orientation to each other, even if they are not touching

[No Collision](/docs/en-us/physics/constraints/no-collision)

[NoCollisionConstraint](/docs/en-us/reference/engine/classes/NoCollisionConstraint)  prevents collisions between two specific parts, but those parts may still register collisions with the rest of the world

## [Constraint visualization](#constraint-visualization)[](#constraint-visualization)

To accurately visualize constraints in Studio, you can toggle the following from the View  menu or through the respective shortcut:

-

Show Welds  (Alt W  or ⌥ W ) — Show [WeldConstraints](/docs/en-us/reference/engine/classes/WeldConstraint)  separately from the visualization of other constraints.

-

Show Constraint Details  (Alt D  or ⌥ D ) — Show complete visual details of non-weld constraints.

In addition to the above visualization, you can view colored outlines around mechanisms (groups of parts that share simulation step and [network ownership](/docs/en-us/physics/network-ownership) ) by toggling on Mechanisms  from the [Visualization Options](/docs/en-us/studio/overview#visualization-options)  widget in the upper‑right corner of the 3D viewport.

## [Create constraints](#create-constraints)[](#create-constraints)

All mechanical constraints must connect one or two [Attachments](/docs/en-us/reference/engine/classes/Attachment)  or [Bones](/docs/en-us/reference/engine/classes/Bone) , except for [WeldConstraint](/docs/en-us/physics/constraints/weld)  and [NoCollisionConstraint](/docs/en-us/physics/constraints/no-collision) . When connected to [Bones](/docs/en-us/reference/engine/classes/Bone) , the constraint will use their animated position and orientation.

To create a mechanical constraint, you can either insert one from the Constraint  picker/button or through the [Explorer](/docs/en-us/studio/explorer)  window.

Constraint Picker Explorer

1.

In Studio's Model  tab toolbar, click‑hold over the small corner arrow on a constraint button to open its picker menu, then select the desired constraint.

 ![Constraint pickers indicated in Studio's toolbar](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Constraint-Pickers.png)

2.

In the 3D viewport, hover over any [Part](/docs/en-us/reference/engine/classes/Part)  or [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  and click to add a new [Attachment](/docs/en-us/reference/engine/classes/Attachment)  to the part at the visualized point. Alternatively, hover over and click an existing [Attachment](/docs/en-us/reference/engine/classes/Attachment)  or [Bone](/docs/en-us/reference/engine/classes/Bone)  to use it for the constraint.

3.

Most mechanical constraints require a secondary  attachment in their functionality, so the tool will typically prompt you to repeat the previous step on another [Part](/docs/en-us/reference/engine/classes/Part) , [MeshPart](/docs/en-us/reference/engine/classes/MeshPart) , [Attachment](/docs/en-us/reference/engine/classes/Attachment) , or [Bone](/docs/en-us/reference/engine/classes/Bone) .

![SpringConstraint connecting two attachments on separate blocks. One block is green and the other is blue.](https://prod.docsiteassets.roblox.com/assets/physics/constraints/Creation-Diagram.jpg) Completed [SpringConstraint](/docs/en-us/physics/constraints/spring)  connecting two attachments

## [Physical simulation](#physical-simulation)[](#physical-simulation)

To simulate physics while [moving](/docs/en-us/parts#move)  or [rotating](/docs/en-us/parts#rotate)  parts, you can switch from Geometric  mode to Physical  mode in Studio's toolbar, effectively forcing parts to obey physical limitations. For example, if two parts are attached by a [RopeConstraint](/docs/en-us/reference/engine/classes/RopeConstraint)  and you drag one part around the scene, the other part will follow as the rope becomes taut.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Mode-Physical.png)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
