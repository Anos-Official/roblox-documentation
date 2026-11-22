<!-- Source: https://create.roblox.com/docs/en-us/physics/constraints/torque -->

Torque | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/physics/constraints/torque.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/en-us/workspace)
6. /
7. [Physics](/docs/en-us/physics)
8. /
9. [Mover constraints](/docs/en-us/physics/mover-constraints)

# Torque

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/physics/constraints/torque.md)

For an overview on creating, visualizing, and simulating mover constraints, including [Torque](/docs/en-us/reference/engine/classes/Torque) , see [mover constraints](/docs/en-us/physics/mover-constraints) . Also see [Roblox units](/docs/en-us/physics/units)  to understand how Roblox units compare to metric units.

A [Torque](/docs/en-us/reference/engine/classes/Torque)  constraint applies constant torque on an assembly from its center of mass.

Because the [Torque](/docs/en-us/reference/engine/classes/Torque)  constraint applies constant  torque and angular acceleration, very high speeds may result if no other forces are involved. If you want to maintain a more steady velocity over time, use an [AngularVelocity](/docs/en-us/physics/constraints/angular-velocity)  constraint. Alternatively, if you only need initial  velocity, set the [AssemblyAngularVelocity](/docs/en-us/reference/engine/classes/BasePart#AssemblyAngularVelocity)  property directly on the assembly.

## [Relativity](#relativity)[](#relativity)

By default, torque is applied relative to [Attachment0](/docs/en-us/reference/engine/classes/Constraint#Attachment0) . If the parent assembly rotates, the torque will change direction to match the adjusted orientation of the attachment.

If [RelativeTo](/docs/en-us/reference/engine/classes/Torque#RelativeTo)  is set to World , torque will be applied in world coordinates, independent of the parent or attachment orientations.

If [RelativeTo](/docs/en-us/reference/engine/classes/Torque#RelativeTo)  is set to Attachment1 , torque will be applied relative to [Attachment1](/docs/en-us/reference/engine/classes/Constraint#Attachment1)  and, if the attachment rotates, change to match its orientation.

RelativeTo = Attachment0

RelativeTo = World

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
