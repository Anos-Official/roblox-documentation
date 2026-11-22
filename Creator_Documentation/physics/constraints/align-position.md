<!-- Source: https://create.roblox.com/docs/en-us/physics/constraints/align-position -->

AlignPosition | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/physics/constraints/align-position.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/en-us/workspace)
6. /
7. [Physics](/docs/en-us/physics)
8. /
9. [Mover constraints](/docs/en-us/physics/mover-constraints)

# AlignPosition

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/physics/constraints/align-position.md)

For an overview on creating, visualizing, and simulating mover constraints, including [AlignPosition](/docs/en-us/reference/engine/classes/AlignPosition) , see [mover constraints](/docs/en-us/physics/mover-constraints) . Also see [Roblox units](/docs/en-us/physics/units)  to understand how Roblox units compare to metric units.

An [AlignPosition](/docs/en-us/reference/engine/classes/AlignPosition)  constraint applies force to move two attachments together, or to move one attachment to a goal position. As indicated by the name, it only affects the position  of the attachments, not their orientation (to align attachments by orientation , see [AlignOrientation](/docs/en-us/physics/constraints/align-orientation) ).

By default, the constraint only applies force to [Attachment0](/docs/en-us/reference/engine/classes/Constraint#Attachment0) , although this behavior can be controlled through the constraint's [reactionary force](#reactionary-force) .

## [Force location](#force-location)[](#force-location)

By default, force is applied to the parent of [Attachment0](/docs/en-us/reference/engine/classes/Constraint#Attachment0)  at that attachment's location, meaning that if the parent's center of mass is not aligned with the direction of the force, torque will be applied as well as force. Alternatively, force can be applied to the parents' center of mass by toggling on [ApplyAtCenterOfMass](/docs/en-us/reference/engine/classes/AlignPosition#ApplyAtCenterOfMass) .

## [Force magnitude](#force-magnitude)[](#force-magnitude)

You can configure the [AlignPosition](/docs/en-us/reference/engine/classes/AlignPosition)  constraint to apply the maximum force that constraints allow through the [RigidityEnabled](/docs/en-us/reference/engine/classes/AlignPosition#RigidityEnabled)  property. When true , the physics solver reacts as quickly as possible to complete the alignment. When false , the force is determined by [MaxForce](/docs/en-us/reference/engine/classes/AlignPosition#MaxForce) , [MaxVelocity](/docs/en-us/reference/engine/classes/AlignPosition#MaxVelocity) , and [Responsiveness](/docs/en-us/reference/engine/classes/AlignPosition#Responsiveness) .

## [Reactionary force](#reactionary-force)[](#reactionary-force)

By default, the constraint only applies force to [Attachment0](/docs/en-us/reference/engine/classes/Constraint#Attachment0)  while [Attachment1](/docs/en-us/reference/engine/classes/Constraint#Attachment1)  remains unaffected. If desired, force can be applied to both  attachments in equal and opposite directions  by enabling [ReactionForceEnabled](/docs/en-us/reference/engine/classes/AlignPosition#ReactionForceEnabled) .

## [Attachment mode](#attachment-mode)[](#attachment-mode)

The [Mode](/docs/en-us/reference/engine/classes/AlignPosition#Mode)  property specifies whether the constraint uses one  or two  attachments in calculating its goal. By default, this is [TwoAttachment](/docs/en-us/reference/engine/enums/PositionAlignmentMode#TwoAttachment) , meaning that the constraint disregards [Position](/docs/en-us/reference/engine/classes/AlignPosition#Position)  and attempts to move [Attachment0](/docs/en-us/reference/engine/classes/Constraint#Attachment0)  to the position of [Attachment1](/docs/en-us/reference/engine/classes/Constraint#Attachment1) . If set to [OneAttachment](/docs/en-us/reference/engine/enums/PositionAlignmentMode#OneAttachment) , the constraint disregards [Attachment1](/docs/en-us/reference/engine/classes/Constraint#Attachment1)  and attempts to move [Attachment0](/docs/en-us/reference/engine/classes/Constraint#Attachment0)  to [Position](/docs/en-us/reference/engine/classes/AlignPosition#Position) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
