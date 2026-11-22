<!-- Source: https://create.roblox.com/docs/en-us/physics/mover-constraints -->

Mover constraints | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/physics/mover-constraints.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/en-us/workspace)
6. /
7. [Physics](/docs/en-us/physics)
8. /
9. [Mover constraints](/docs/en-us/physics/mover-constraints)

# Mover constraints

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/physics/mover-constraints.md)

The physics engine includes the following [Constraints](/docs/en-us/reference/engine/classes/Constraint)  that apply force or torque to move one or more assemblies. In addition, various [mechanical constraints](/docs/en-us/physics/mechanical-constraints)  are available which behave as conceptual mechanical connections, including hinges, springs, ropes, and more.

[Linear Velocity](/docs/en-us/physics/constraints/linear-velocity)

[LinearVelocity](/docs/en-us/reference/engine/classes/LinearVelocity)  applies force on an assembly to maintain a constant velocity along a 3D vector, line, or 2D plane

[Angular Velocity](/docs/en-us/physics/constraints/angular-velocity)

[AngularVelocity](/docs/en-us/reference/engine/classes/AngularVelocity)  applies torque on an assembly to maintain a constant angular velocity

[Align Position](/docs/en-us/physics/constraints/align-position)

[AlignPosition](/docs/en-us/reference/engine/classes/AlignPosition)  applies force to move two attachments together, or to move one attachment to a goal position

[Align Orientation](/docs/en-us/physics/constraints/align-orientation)

[AlignOrientation](/docs/en-us/reference/engine/classes/AlignOrientation)  applies torque to align two attachments, or to align one attachment with a goal orientation

[Vector Force](/docs/en-us/physics/constraints/vector-force)

[VectorForce](/docs/en-us/reference/engine/classes/VectorForce)  applies constant linear force on an assembly

[Torque](/docs/en-us/physics/constraints/torque)

[Torque](/docs/en-us/reference/engine/classes/Torque)  applies constant torque on an assembly from its center of mass

[Line Force](/docs/en-us/physics/constraints/line-force)

[LineForce](/docs/en-us/reference/engine/classes/LineForce)  applies force along the theoretical line connecting its two attachments

[Animation Constraint](/docs/en-us/physics/constraints/animation)

[AnimationConstraint](/docs/en-us/reference/engine/classes/AnimationConstraint)  constrains its [Attachments](/docs/en-us/reference/engine/classes/Attachment)  by an offset transform [CFrame](/docs/en-us/reference/engine/datatypes/CFrame) .

## [Constraint visualization](#constraint-visualization)[](#constraint-visualization)

To accurately visualize constraints in Studio, you can toggle the following from the View  menu or through the respective shortcut:

-

Show Welds  (Alt W  or ⌥ W ) — Show [WeldConstraints](/docs/en-us/reference/engine/classes/WeldConstraint)  separately from the visualization of other constraints.

-

Show Constraint Details  (Alt D  or ⌥ D ) — Show complete visual details of non-weld constraints.

In addition to the above visualization, you can view colored outlines around mechanisms (groups of parts that share simulation step and [network ownership](/docs/en-us/physics/network-ownership) ) by toggling on Mechanisms  from the [Visualization Options](/docs/en-us/studio/overview#visualization-options)  widget in the upper‑right corner of the 3D viewport.

## [Create constraints](#create-constraints)[](#create-constraints)

Mover constraints typically connect one or two [Attachments](/docs/en-us/reference/engine/classes/Attachment)  or [Bones](/docs/en-us/reference/engine/classes/Bone) . When connected to [Bones](/docs/en-us/reference/engine/classes/Bone) , the constraint will use their animated position and orientation.

To create a mechanical constraint, you can either insert one from the Constraint  picker/button or through the [Explorer](/docs/en-us/studio/explorer)  window.

Constraint Picker Explorer

1.

In Studio's Model  tab toolbar, click‑hold over the small corner arrow on a constraint button to open its picker menu, then select the desired constraint.

 ![Constraint pickers indicated in Studio's toolbar](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Constraint-Pickers.png)

2.

In the 3D viewport, hover over any [Part](/docs/en-us/reference/engine/classes/Part)  or [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  and click to add a new [Attachment](/docs/en-us/reference/engine/classes/Attachment)  to the part at the visualized point. Alternatively, hover over and click an existing [Attachment](/docs/en-us/reference/engine/classes/Attachment)  or [Bone](/docs/en-us/reference/engine/classes/Bone)  to use it for the constraint.

3.

Some mover constraints utilize or support a secondary  attachment in their functionality, so the tool might prompt you to repeat the previous step on another [Part](/docs/en-us/reference/engine/classes/Part) , [MeshPart](/docs/en-us/reference/engine/classes/MeshPart) , or [Attachment](/docs/en-us/reference/engine/classes/Attachment) , or [Bone](/docs/en-us/reference/engine/classes/Bone) .

![AngularVelocity using one attachment](https://prod.docsiteassets.roblox.com/assets/physics/constraints/Constraint-AngularVelocity-Labeled.jpg)[AngularVelocity](/docs/en-us/physics/constraints/angular-velocity)  using one attachment

![AlignPosition using two attachments](https://prod.docsiteassets.roblox.com/assets/physics/constraints/Constraint-AlignPosition-Labeled.jpg)[AlignPosition](/docs/en-us/physics/constraints/align-position)  using two attachments

## [Physical simulation](#physical-simulation)[](#physical-simulation)

To simulate physics while [moving](/docs/en-us/parts#move)  or [rotating](/docs/en-us/parts#rotate)  parts, you can switch from Geometric  mode to Physical  mode in Studio's toolbar, effectively forcing parts to obey physical limitations. For example, if two parts are attached by a [RopeConstraint](/docs/en-us/reference/engine/classes/RopeConstraint)  and you drag one part around the scene, the other part will follow as the rope becomes taut.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Mode-Physical.png)

## [Legacy mover conversion](#legacy-mover-conversion)[](#legacy-mover-conversion)

If your game relies on legacy [BodyMover](/docs/en-us/reference/engine/classes/BodyMover) ‑based constraints, review the following notes when converting to modern mover constraints.

BodyPosition  ⟩ AlignPosition

[AlignPosition](/docs/en-us/reference/engine/classes/AlignPosition)  satisfies the majority of use cases covered by the deprecated [BodyPosition](/docs/en-us/reference/engine/classes/BodyPosition)  mover. To sync with how the legacy mover treated each component independently and allowed a different force along each dimension, the [ForceLimitMode](/docs/en-us/reference/engine/classes/AlignPosition#ForceLimitMode)  property of [AlignPosition](/docs/en-us/reference/engine/classes/AlignPosition)  allows the constraint to operate in [Magnitude](/docs/en-us/reference/engine/enums/ForceLimitMode)  mode or [PerAxis](/docs/en-us/reference/engine/enums/ForceLimitMode)  mode:

-

In [Magnitude](/docs/en-us/reference/engine/enums/ForceLimitMode)  mode, the existing behavior is preserved and [MaxForce](/docs/en-us/reference/engine/classes/AlignPosition#MaxForce)  is interpreted as a magnitude.

-

In [PerAxis](/docs/en-us/reference/engine/enums/ForceLimitMode)  mode, the force along each axis can be specified independently. Because the maximum force is specified as a vector, the reference frame of the force can also be specified through the [ForceRelativeTo](/docs/en-us/reference/engine/classes/AlignPosition#ForceRelativeTo)  property with [World](/docs/en-us/reference/engine/enums/ActuatorRelativeTo) , [Attachment0](/docs/en-us/reference/engine/enums/ActuatorRelativeTo) , and [Attachment1](/docs/en-us/reference/engine/enums/ActuatorRelativeTo)  options. Additionally, the formulation for the internal controller is modified to match that of [BodyPosition](/docs/en-us/reference/engine/classes/BodyPosition) .

BodyGyro  ⟩ AlignOrientation

[AlignOrientation](/docs/en-us/reference/engine/classes/AlignOrientation)  satisfies the majority of use cases covered by the deprecated [BodyGyro](/docs/en-us/reference/engine/classes/BodyGyro)  mover. The [AlignType](/docs/en-us/reference/engine/classes/AlignOrientation#AlignType)  modes of [AlignOrientation](/docs/en-us/reference/engine/classes/AlignOrientation)  provide sufficient freedom for most applications and the combination of multiple constraints can replicate the vector torque limit. Additionally, the [PrimaryAxisLookAt](/docs/en-us/reference/engine/enums/AlignType)  mode forces the primary axis of the constraint's first attachment ([Attachment0](/docs/en-us/reference/engine/classes/AlignOrientation#Attachment0) ) to always point towards the second attachment ([Attachment1](/docs/en-us/reference/engine/classes/AlignOrientation#Attachment1) ), making it a lot easier to add things such as motion tracking security cameras or guided missiles.

BodyVelocity  ⟩ LinearVelocity

[LinearVelocity](/docs/en-us/reference/engine/classes/LinearVelocity)  satisfies the majority of use cases covered by the deprecated [BodyVelocity](/docs/en-us/reference/engine/classes/BodyVelocity)  mover. Although the legacy mover allows for a [MaxForce](/docs/en-us/reference/engine/classes/BodyVelocity#MaxForce)  vector, the typical application of that vector force was to zero a particular component, allowing the constraint to be disabled along that dimension. [LinearVelocity](/docs/en-us/reference/engine/classes/LinearVelocity)  achieves a similar effect by operating in distinct [VelocityConstraintMode](/docs/en-us/reference/engine/classes/LinearVelocity#VelocityConstraintMode)  modes that corresponded to one ([Line](/docs/en-us/reference/engine/enums/VelocityConstraintMode) ), two ([Plane](/docs/en-us/reference/engine/enums/VelocityConstraintMode) ), and three ([Vector](/docs/en-us/reference/engine/enums/VelocityConstraintMode) ) dimensions.

Additionally, the [ForceLimitMode](/docs/en-us/reference/engine/classes/LinearVelocity#ForceLimitMode)  property with the option of [PerAxis](/docs/en-us/reference/engine/enums/ForceLimitMode)  accommodates any applications of the vector force with all non‑zero components, such as an increase in the force along a single axis to counteract gravity.

BodyAngularVelocity  ⟩ AngularVelocity

Although [AngularVelocity](/docs/en-us/reference/engine/classes/AngularVelocity)  has some discrepancies with the deprecated [BodyAngularVelocity](/docs/en-us/reference/engine/classes/BodyAngularVelocity)  mover, specific cases related to those discrepancies have not been highlighted by the community, nor internally.

As a separate improvement, [AngularVelocity](/docs/en-us/reference/engine/classes/AngularVelocity)  works with [Attachments](/docs/en-us/reference/engine/classes/Attachment)  and the [RelativeTo](/docs/en-us/reference/engine/classes/AngularVelocity#RelativeTo)  property lets you specify the [CFrame](/docs/en-us/reference/engine/datatypes/CFrame)  in which the force is specified, for example [World](/docs/en-us/reference/engine/enums/ActuatorRelativeTo)  or [Attachment1](/docs/en-us/reference/engine/enums/ActuatorRelativeTo) .

BodyForce / BodyThrust  ⟩ VectorForce

[VectorForce](/docs/en-us/reference/engine/classes/VectorForce)  satisfies all use cases offered by the deprecated [BodyForce](/docs/en-us/reference/engine/classes/BodyForce)  and [BodyThrust](/docs/en-us/reference/engine/classes/BodyThrust)  movers. The modern constraint works with [Attachments](/docs/en-us/reference/engine/classes/Attachment)  and its [RelativeTo](/docs/en-us/reference/engine/classes/VectorForce#RelativeTo)  property lets you apply force to a relative offset from center, similar to how [BodyThrust.Location](/docs/en-us/reference/engine/classes/BodyThrust#Location)  worked.

RocketPropulsion  ⟩ LineForce / AlignOrientation

A combination of [LineForce](/docs/en-us/reference/engine/classes/LineForce)  and [AlignOrientation](/docs/en-us/reference/engine/classes/AlignOrientation)  satisfies the majority of use cases covered by the deprecated [RocketPropulsion](/docs/en-us/reference/engine/classes/RocketPropulsion)  mover. In the example of a guided missile, [LineForce](/docs/en-us/reference/engine/classes/LineForce)  can be used to control the "follow target" behavior of [RocketPropulsion](/docs/en-us/reference/engine/classes/RocketPropulsion)  while [AlignOrientation](/docs/en-us/reference/engine/classes/AlignOrientation)  and its [LookAtPosition](/docs/en-us/reference/engine/classes/AlignOrientation#LookAtPosition)  property can be used to control the "face target" behavior.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
