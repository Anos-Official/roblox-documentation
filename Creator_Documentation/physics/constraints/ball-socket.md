<!-- Source: https://create.roblox.com/docs/en-us/physics/constraints/ball-socket -->

BallSocket | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/physics/constraints/ball-socket.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/en-us/workspace)
6. /
7. [Physics](/docs/en-us/physics)
8. /
9. [Mechanical constraints](/docs/en-us/physics/mechanical-constraints)

# BallSocket

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/physics/constraints/ball-socket.md)

For an overview on creating, visualizing, and simulating mechanical constraints, including [BallSocketConstraint](/docs/en-us/reference/engine/classes/BallSocketConstraint) , see [Mechanical constraints](/docs/en-us/physics/mechanical-constraints) . Also see [Roblox units](/docs/en-us/physics/units)  to understand how Roblox units compare to metric units.

A [BallSocketConstraint](/docs/en-us/reference/engine/classes/BallSocketConstraint)  forces its two attachments into the same position and allows them to freely rotate about all three axes. However, you can enable limits to restrict both tilt and twist.

## [Limits](#limits)[](#limits)

You can set limits to restrict both tilt  and twist  of a ball socket, similar to how a human's head can tilt and turn within a limited axial range. Enabling the [LimitsEnabled](/docs/en-us/reference/engine/classes/BallSocketConstraint#LimitsEnabled)  property exposes the [UpperAngle](/docs/en-us/reference/engine/classes/BallSocketConstraint#UpperAngle)  value to restrict tilt  within a cone; it also exposes the [TwistLimitsEnabled](/docs/en-us/reference/engine/classes/BallSocketConstraint#TwistLimitsEnabled)  property which, when enabled, lets you restrict twist  rotation through the [TwistLowerAngle](/docs/en-us/reference/engine/classes/BallSocketConstraint#TwistLowerAngle)  and [TwistUpperAngle](/docs/en-us/reference/engine/classes/BallSocketConstraint#TwistUpperAngle)  limits.

Constraint with [LimitsEnabled](/docs/en-us/reference/engine/classes/BallSocketConstraint#LimitsEnabled)  set to true  and [UpperAngle](/docs/en-us/reference/engine/classes/BallSocketConstraint#UpperAngle)  set to 15

Constraint with [LimitsEnabled](/docs/en-us/reference/engine/classes/BallSocketConstraint#LimitsEnabled)  and [TwistLimitsEnabled](/docs/en-us/reference/engine/classes/BallSocketConstraint#TwistLimitsEnabled)  set to true , [TwistLowerAngle](/docs/en-us/reference/engine/classes/BallSocketConstraint#TwistLowerAngle)  set to -60 , and [TwistUpperAngle](/docs/en-us/reference/engine/classes/BallSocketConstraint#TwistUpperAngle)  set to 0

Enabling [LimitsEnabled](/docs/en-us/reference/engine/classes/BallSocketConstraint#LimitsEnabled)  also exposes the [Restitution](/docs/en-us/reference/engine/classes/BallSocketConstraint#Restitution)  value which defines the elasticity of the attachments at their tilt and/or twist limits.

When [LimitsEnabled](/docs/en-us/reference/engine/classes/BallSocketConstraint#LimitsEnabled)  is enabled, orientation of a ball socket's attachments affects how it rotates. To ensure rotation occurs around the desired axis, each attachment's [Axis](/docs/en-us/reference/engine/classes/Attachment#Axis) , visualized by the yellow arrow, should point in the same direction.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
