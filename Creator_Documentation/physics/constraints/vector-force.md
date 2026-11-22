<!-- Source: https://create.roblox.com/docs/en-us/physics/constraints/vector-force -->

VectorForce | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/physics/constraints/vector-force.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/en-us/workspace)
6. /
7. [Physics](/docs/en-us/physics)
8. /
9. [Mover constraints](/docs/en-us/physics/mover-constraints)

# VectorForce

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/physics/constraints/vector-force.md)

For an overview on creating, visualizing, and simulating mover constraints, including [VectorForce](/docs/en-us/reference/engine/classes/VectorForce) , see [mover constraints](/docs/en-us/physics/mover-constraints) . Also see [Roblox units](/docs/en-us/physics/units)  to understand how Roblox units compare to metric units.

The [VectorForce](/docs/en-us/reference/engine/classes/VectorForce)  constraint applies constant linear force on an assembly. The direction and strength of the force is determined by a [Vector3](/docs/en-us/reference/engine/datatypes/Vector3)  and can be relative to an attachment on the part, another attachment, or the world coordinate system.

Because the [VectorForce](/docs/en-us/reference/engine/classes/VectorForce)  constraint applies constant  force and acceleration, very high speeds may result if no other forces are involved. If you want to maintain a more steady velocity over time, use a [LinearVelocity](/docs/en-us/physics/constraints/linear-velocity)  constraint. Alternatively, if you only need initial  velocity, set the [AssemblyLinearVelocity](/docs/en-us/reference/engine/classes/BasePart#AssemblyLinearVelocity)  property directly on the assembly.

## [Force location](#force-location)[](#force-location)

By default, force is applied to the assembly at the location of [Attachment0](/docs/en-us/reference/engine/classes/Constraint#Attachment0) . Thus, if its center of mass is not aligned with the direction/point of force, torque will be applied as well. If desired, force can be focused at the center of mass by toggling on [ApplyAtCenterOfMass](/docs/en-us/reference/engine/classes/VectorForce#ApplyAtCenterOfMass) .

ApplyAtCenterOfMass = false

ApplyAtCenterOfMass = true

## [Relativity](#relativity)[](#relativity)

By default, force is applied relative to [Attachment0](/docs/en-us/reference/engine/classes/Constraint#Attachment0) . If the parent assembly rotates, the force will change direction to match the adjusted orientation of the attachment; visualize this behavior in how the thruster of a rocket pushes it forward, regardless of the rocket's rotation.

If [RelativeTo](/docs/en-us/reference/engine/classes/VectorForce#RelativeTo)  is set to World , force will be applied in world coordinates, independent of the parent or attachment orientations; visualize this behavior as a directional force like the wind blowing against an object.

If [RelativeTo](/docs/en-us/reference/engine/classes/VectorForce#RelativeTo)  is set to Attachment1 , force will be applied relative to [Attachment1](/docs/en-us/reference/engine/classes/Constraint#Attachment1)  and, if the attachment rotates, the force will change to match its orientation.

RelativeTo = Attachment0

RelativeTo = World

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
