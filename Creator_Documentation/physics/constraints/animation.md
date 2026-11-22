<!-- Source: https://create.roblox.com/docs/en-us/physics/constraints/animation -->

AnimationConstraint | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/physics/constraints/animation.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/en-us/workspace)
6. /
7. [Physics](/docs/en-us/physics)
8. /
9. [Mover constraints](/docs/en-us/physics/mover-constraints)

# AnimationConstraint

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/physics/constraints/animation.md)

For an overview on creating, visualizing, and simulating mover constraints, including [AnimationConstraint](/docs/en-us/reference/engine/classes/AnimationConstraint) , see [mover constraints](/docs/en-us/physics/mover-constraints) . Also see [Roblox units](/docs/en-us/physics/units)  to understand how Roblox units compare to metric units.

An [AnimationConstraint](/docs/en-us/reference/engine/classes/AnimationConstraint)  constrains its [Attachments](/docs/en-us/reference/engine/classes/Attachment)  by an offset [transform](#transform) . It can be either [kinematic](#kinematic)  for snap‑to behavior or it can follow the target trajectory using [force and torque](#force-and-torque) . limited by [MaxForce](/docs/en-us/reference/engine/classes/AnimationConstraint#MaxForce)  and [MaxTorque](/docs/en-us/reference/engine/classes/AnimationConstraint#MaxTorque) .

## [Transform](#transform)[](#transform)

The constraint's [Transform](/docs/en-us/reference/engine/classes/AnimationConstraint#Transform)  is the internal [CFrame](/docs/en-us/reference/engine/datatypes/CFrame)  that's manipulated when the constraint is being animated. How this transform is reached depends on the constraint's [kinematic](#kinematic)  setting.

## [Kinematic](#kinematic)[](#kinematic)

When the constraint's [IsKinematic](/docs/en-us/reference/engine/classes/AnimationConstraint#IsKinematic)  property is true , the connected parts snap to the [transform](#transform)  instantly and precisely without participating in physics simulation. When false , the connected parts follow the trajectory using [force and torque](#force-and-torque) .

## [Force and torque](#force-and-torque)[](#force-and-torque)

If the constraint is not  set to [kinematic](#kinematic) , the connected parts follow a trajectory toward the [transform](#transform)  using a maximum force/torque limited by [MaxForce](/docs/en-us/reference/engine/classes/AnimationConstraint#MaxForce)  and [MaxTorque](/docs/en-us/reference/engine/classes/AnimationConstraint#MaxTorque)  respectively.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
