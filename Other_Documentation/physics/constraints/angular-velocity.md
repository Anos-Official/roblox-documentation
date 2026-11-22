<!-- Source: https://create.roblox.com/docs/physics/constraints/angular-velocity -->

AngularVelocity | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/physics/constraints/angular-velocity.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/workspace)
6. /
7. [Physics](/docs/physics)
8. /
9. [Mover constraints](/docs/physics/mover-constraints)

# AngularVelocity

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/physics/constraints/angular-velocity.md)

For an overview on creating, visualizing, and simulating mover constraints, including [AngularVelocity](/docs/reference/engine/classes/AngularVelocity) , see [mover constraints](/docs/physics/mover-constraints) . Also see [Roblox units](/docs/physics/units)  to understand how Roblox units compare to metric units.

An [AngularVelocity](/docs/reference/engine/classes/AngularVelocity)  constraint applies torque on an assembly to maintain a constant angular velocity.

The [AngularVelocity](/docs/reference/engine/classes/AngularVelocity)  constraint applies torque that attempts to maintain a constant  angular velocity. If you want to control the amount of torque applied, use a [Torque](/docs/physics/constraints/torque)  constraint. Alternatively, if you only need initial  angular velocity, set the [AssemblyAngularVelocity](/docs/reference/engine/classes/BasePart#AssemblyAngularVelocity)  method directly on the assembly.

## [Relativity](#relativity)[](#relativity)

Application of velocity can be controlled through the constraint's [RelativeTo](/docs/reference/engine/classes/AngularVelocity#RelativeTo)  property. If set to [World](/docs/reference/engine/enums/ActuatorRelativeTo) , the angular velocity vector is used as is. If set to [Attachment1](/docs/reference/engine/enums/ActuatorRelativeTo)  and the constraint's [Attachment1](/docs/reference/engine/classes/Constraint#Attachment1)  property is set to another attachment, the angular velocity will be affected by that of the other attachment as seen by how the upper-left red part's velocity affects the attached blue part's velocity.

RelativeTo = World

RelativeTo = Attachment1

Setting [RelativeTo](/docs/reference/engine/classes/AngularVelocity#RelativeTo)  to [Attachment1](/docs/reference/engine/enums/ActuatorRelativeTo)  also exposes the [ReactionTorqueEnabled](/docs/reference/engine/classes/AngularVelocity#ReactionTorqueEnabled)  property.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
