<!-- Source: https://create.roblox.com/docs/en-us/physics/constraints/linear-velocity -->

LinearVelocity | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/physics/constraints/linear-velocity.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/en-us/workspace)
6. /
7. [Physics](/docs/en-us/physics)
8. /
9. [Mover constraints](/docs/en-us/physics/mover-constraints)

# LinearVelocity

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/physics/constraints/linear-velocity.md)

For an overview on creating, visualizing, and simulating mover constraints, including [LinearVelocity](/docs/en-us/reference/engine/classes/LinearVelocity) , see [mover constraints](/docs/en-us/physics/mover-constraints) . Also see [Roblox units](/docs/en-us/physics/units)  to understand how Roblox units compare to metric units.

A [LinearVelocity](/docs/en-us/reference/engine/classes/LinearVelocity)  constraint applies force on an assembly to maintain a constant velocity. It can be set to apply force along a [Vector3](/docs/en-us/reference/engine/datatypes/Vector3) , line, or 2D plane.

The [LinearVelocity](/docs/en-us/reference/engine/classes/LinearVelocity)  constraint applies a force that attempts to maintain a constant  linear velocity. If you want to control the amount of force applied, use a [VectorForce](/docs/en-us/physics/constraints/vector-force)  constraint. Alternatively, if you only need initial  linear velocity, set the [AssemblyLinearVelocity](/docs/en-us/reference/engine/classes/BasePart#AssemblyLinearVelocity)  property directly on the assembly.

## [Relativity](#relativity)[](#relativity)

Application of velocity can be controlled through the constraint's [RelativeTo](/docs/en-us/reference/engine/classes/LinearVelocity#RelativeTo)  property. If set to [World](/docs/en-us/reference/engine/enums/ActuatorRelativeTo) , force will be applied in world coordinates, independent of the parent or attachment orientations. If set to [Attachment0](/docs/en-us/reference/engine/enums/ActuatorRelativeTo)  or [Attachment1](/docs/en-us/reference/engine/enums/ActuatorRelativeTo) , force will be applied relative to [Attachment0](/docs/en-us/reference/engine/classes/Constraint#Attachment0)  or [Attachment1](/docs/en-us/reference/engine/classes/Constraint#Attachment1)  respectively.

RelativeTo = World

RelativeTo = Attachment0

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
