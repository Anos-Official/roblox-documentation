<!-- Source: https://create.roblox.com/docs/en-us/physics/constraints/hinge -->

Hinge | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/physics/constraints/hinge.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/en-us/workspace)
6. /
7. [Physics](/docs/en-us/physics)
8. /
9. [Mechanical constraints](/docs/en-us/physics/mechanical-constraints)

# Hinge

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/physics/constraints/hinge.md)

For an overview on creating, visualizing, and simulating mechanical constraints, including [HingeConstraint](/docs/en-us/reference/engine/classes/HingeConstraint) , see [Mechanical constraints](/docs/en-us/physics/mechanical-constraints) . Also see [Roblox units](/docs/en-us/physics/units)  to understand how Roblox units compare to metric units.

A [HingeConstraint](/docs/en-us/reference/engine/classes/HingeConstraint)  allows its two attachments to rotate about one axis, forcing them into the same position and X  axis alignment. This constraint can also be powered to behave like a [motor](#angular-power)  or [servo](#angular-power) , and you can set limits to restrict the hinge's rotational range.

Orientation of a hinge's attachments affects how it rotates. To ensure rotation occurs around the desired axis, each attachment's [Axis](/docs/en-us/reference/engine/classes/Attachment#Axis) , visualized by the yellow arrow, should point in the same direction.

### [Angular power](#angular-power)[](#angular-power)

If a hinge's [ActuatorType](/docs/en-us/reference/engine/classes/HingeConstraint#ActuatorType)  is set to [Motor](/docs/en-us/reference/engine/enums/ActuatorType) , it attempts to rotate the attachments with the goal of reaching its [AngularVelocity](/docs/en-us/reference/engine/classes/HingeConstraint#AngularVelocity) . You can further control this rotation through both [MotorMaxAcceleration](/docs/en-us/reference/engine/classes/HingeConstraint#MotorMaxAcceleration)  and [MotorMaxTorque](/docs/en-us/reference/engine/classes/HingeConstraint#MotorMaxTorque) .

If a hinge's [ActuatorType](/docs/en-us/reference/engine/classes/HingeConstraint#ActuatorType)  is set to [Servo](/docs/en-us/reference/engine/enums/ActuatorType) , it attempts to rotate to an angle specified by [TargetAngle](/docs/en-us/reference/engine/classes/HingeConstraint#TargetAngle) . This rotation is controlled by both [AngularSpeed](/docs/en-us/reference/engine/classes/HingeConstraint#AngularSpeed)  and [ServoMaxTorque](/docs/en-us/reference/engine/classes/HingeConstraint#ServoMaxTorque) .

ActuatorType = Motor

ActuatorType = Servo

### [Limits](#limits)[](#limits)

You can set limits to restrict the rotation of a hinge, useful for mechanisms like doors which should only swing open or closed within a set range. Enabling the [LimitsEnabled](/docs/en-us/reference/engine/classes/HingeConstraint#LimitsEnabled)  property exposes the [LowerAngle](/docs/en-us/reference/engine/classes/HingeConstraint#LowerAngle)  and [UpperAngle](/docs/en-us/reference/engine/classes/HingeConstraint#UpperAngle)  limits, as well as [Restitution](/docs/en-us/reference/engine/classes/HingeConstraint#Restitution)  which defines the elasticity of the attachments when they reach either limit.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
