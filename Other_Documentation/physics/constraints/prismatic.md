<!-- Source: https://create.roblox.com/docs/physics/constraints/prismatic -->

Prismatic | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/physics/constraints/prismatic.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/workspace)
6. /
7. [Physics](/docs/physics)
8. /
9. [Mechanical constraints](/docs/physics/mechanical-constraints)

# Prismatic

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/physics/constraints/prismatic.md)

For an overview on creating, visualizing, and simulating mechanical constraints, including [PrismaticConstraint](/docs/reference/engine/classes/PrismaticConstraint) , see [Mechanical constraints](/docs/physics/mechanical-constraints) . Also see [Roblox units](/docs/physics/units)  to understand how Roblox units compare to metric units.

A [PrismaticConstraint](/docs/reference/engine/classes/PrismaticConstraint)  creates a rigid joint between two attachments, allowing them to slide along one axis but not rotate. The constraint can also be [powered](#linear-power)  for mechanisms like sliding doors and elevator platforms.

Orientation of a prismatic's attachments affects how it will move. To ensure movement occurs along the desired axis, each attachment's [Axis](/docs/reference/engine/classes/Attachment#Axis) , visualized by the yellow arrow, should point in the same direction.

## [Linear power](#linear-power)[](#linear-power)

If a prismatic's [ActuatorType](/docs/reference/engine/classes/PrismaticConstraint)  is set to [Motor](/docs/reference/engine/enums/ActuatorType) , it attempts to translate the attachments with the goal of reaching [Velocity](/docs/reference/engine/classes/PrismaticConstraint) . You can further control this translation through both [MotorMaxAcceleration](/docs/reference/engine/classes/PrismaticConstraint)  and [MotorMaxForce](/docs/reference/engine/classes/PrismaticConstraint) .

If a prismatic's [ActuatorType](/docs/reference/engine/classes/PrismaticConstraint)  is set to [Servo](/docs/reference/engine/enums/ActuatorType) , it attempts to translate the attachments to a set separation specified by [TargetPosition](/docs/reference/engine/classes/PrismaticConstraint) . This translation is controlled by [Speed](/docs/reference/engine/classes/PrismaticConstraint) , [LinearResponsiveness](/docs/reference/engine/classes/PrismaticConstraint) , and [ServoMaxForce](/docs/reference/engine/classes/PrismaticConstraint) .

ActuatorType = Motor

ActuatorType = Servo

## [Limits](#limits)[](#limits)

You can set limits to restrict the sliding range a prismatic. Enabling the [LimitsEnabled](/docs/reference/engine/classes/PrismaticConstraint)  property exposes the [LowerLimit](/docs/reference/engine/classes/PrismaticConstraint)  and [UpperLimit](/docs/reference/engine/classes/PrismaticConstraint)  values, as well as [Restitution](/docs/reference/engine/classes/PrismaticConstraint)  which defines the elasticity of the attachments when they reach either limit.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
