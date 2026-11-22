<!-- Source: https://create.roblox.com/docs/en-us/physics/constraints/align-orientation -->

AlignOrientation | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/physics/constraints/align-orientation.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/en-us/workspace)
6. /
7. [Physics](/docs/en-us/physics)
8. /
9. [Mover constraints](/docs/en-us/physics/mover-constraints)

# AlignOrientation

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/physics/constraints/align-orientation.md)

For an overview on creating, visualizing, and simulating mover constraints, including [AlignOrientation](/docs/en-us/reference/engine/classes/AlignOrientation) , see [mover constraints](/docs/en-us/physics/mover-constraints) . Also see [Roblox units](/docs/en-us/physics/units)  to understand how Roblox units compare to metric units.

The [AlignOrientation](/docs/en-us/reference/engine/classes/AlignOrientation)  constraint applies torque to align two attachments, or to align one attachment with a goal orientation. As indicated by the name, it only affects the orientation  of the attachments, not their position (to align attachments positionally , see [AlignPosition](/docs/en-us/physics/constraints/align-position) ).

By default, the constraint only applies torque to [Attachment0](/docs/en-us/reference/engine/classes/Constraint#Attachment0) , although this behavior can be controlled through the constraint's [reactionary torque](#reactionary-torque) .

## [Affected axes](#affected-axes)[](#affected-axes)

The axes affected by torque are controlled through the constraint's [AlignType](/docs/en-us/reference/engine/classes/AlignOrientation#AlignType)  property. When set to [AllAxes](/docs/en-us/reference/engine/enums/AlignType#AllAxes)  (default), the constraint will apply torque about all 3 axes to achieve alignment. When set to [PrimaryAxisParallel](/docs/en-us/reference/engine/enums/AlignType#PrimaryAxisParallel) , [PrimaryAxisPerpendicular](/docs/en-us/reference/engine/enums/AlignType#PrimaryAxisPerpendicular) , or [PrimaryAxisLookAt](/docs/en-us/reference/engine/enums/AlignType#PrimaryAxisLookAt) , torque will only occur when the primary  axes become misaligned.

## [Torque magnitude](#torque-magnitude)[](#torque-magnitude)

You can configure the [AlignOrientation](/docs/en-us/reference/engine/classes/AlignOrientation)  constraint to apply the maximum torque that constraints allow through the [RigidityEnabled](/docs/en-us/reference/engine/classes/AlignOrientation#RigidityEnabled)  property. When true , the physics solver reacts as quickly as possible to complete the alignment. When false , the torque is determined by [MaxTorque](/docs/en-us/reference/engine/classes/AlignOrientation#MaxTorque) , [MaxAngularVelocity](/docs/en-us/reference/engine/classes/AlignOrientation#MaxAngularVelocity) , and [Responsiveness](/docs/en-us/reference/engine/classes/AlignOrientation#Responsiveness) .

## [Reactionary torque](#reactionary-torque)[](#reactionary-torque)

By default, the constraint only applies torque to [Attachment0](/docs/en-us/reference/engine/classes/Constraint#Attachment0)  while [Attachment1](/docs/en-us/reference/engine/classes/Constraint#Attachment1)  remains unaffected. If desired, torque can be applied to both  attachments in equal and opposite directions  by enabling [ReactionTorqueEnabled](/docs/en-us/reference/engine/classes/AlignOrientation#ReactionTorqueEnabled) .

## [Attachment mode](#attachment-mode)[](#attachment-mode)

The [Mode](/docs/en-us/reference/engine/classes/AlignOrientation#Mode)  property specifies whether the constraint uses one  or two  attachments in calculating its goal. By default, this is [TwoAttachment](/docs/en-us/reference/engine/enums/OrientationAlignmentMode#TwoAttachment) , meaning that the constraint attempts to match the orientation of [Attachment0](/docs/en-us/reference/engine/classes/Constraint#Attachment0)  with the orientation of [Attachment1](/docs/en-us/reference/engine/classes/Constraint#Attachment1) , disregarding [CFrame](/docs/en-us/reference/engine/classes/AlignOrientation#CFrame) , [PrimaryAxis](/docs/en-us/reference/engine/classes/AlignOrientation#PrimaryAxis) , and [SecondaryAxis](/docs/en-us/reference/engine/classes/AlignOrientation#SecondaryAxis) .

If set to [OneAttachment](/docs/en-us/reference/engine/enums/OrientationAlignmentMode#OneAttachment) , the constraint disregards [Attachment1](/docs/en-us/reference/engine/classes/Constraint#Attachment1)  and attempts to match the orientation of [Attachment0](/docs/en-us/reference/engine/classes/Constraint#Attachment0)  with the orientation of [CFrame](/docs/en-us/reference/engine/classes/AlignOrientation#CFrame) , or match the attachment's [Axis](/docs/en-us/reference/engine/classes/Attachment#Axis)  and [SecondaryAxis](/docs/en-us/reference/engine/classes/Attachment#SecondaryAxis)  with the constraint's [PrimaryAxis](/docs/en-us/reference/engine/classes/AlignOrientation#PrimaryAxis)  and [SecondaryAxis](/docs/en-us/reference/engine/classes/AlignOrientation#SecondaryAxis)  properties respectively.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
