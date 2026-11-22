<!-- Source: https://create.roblox.com/docs/en-us/physics/constraints/cylindrical -->

Cylindrical | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/physics/constraints/cylindrical.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/en-us/workspace)
6. /
7. [Physics](/docs/en-us/physics)
8. /
9. [Mechanical constraints](/docs/en-us/physics/mechanical-constraints)

# Cylindrical

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/physics/constraints/cylindrical.md)

For an overview on creating, visualizing, and simulating mechanical constraints, including [CylindricalConstraint](/docs/en-us/reference/engine/classes/CylindricalConstraint) , see [Mechanical constraints](/docs/en-us/physics/mechanical-constraints) . Also see [Roblox units](/docs/en-us/physics/units)  to understand how Roblox units compare to metric units.

A [CylindricalConstraint](/docs/en-us/reference/engine/classes/CylindricalConstraint)  allows its attachments to slide along one axis and rotate about another axis. This constraint, along with a [SpringConstraint](/docs/en-us/physics/constraints/spring) , is ideal for building vehicle suspensions where the wheel shock can slide up and down while the wheel itself spins. This constraint can also be powered in both an [angular](#angular-power)  and [linear](#linear-power)  manner.

Orientation of the attachments affects how the cylindrical aspect will rotate. To ensure rotation occurs around the desired axis, each attachment's [Axis](/docs/en-us/reference/engine/classes/Attachment#Axis)  and [SecondaryAxis](/docs/en-us/reference/engine/classes/Attachment#SecondaryAxis) , visualized by the yellow and orange arrows, should point in the same direction.

## [Angular power](#angular-power)[](#angular-power)

If a cylindrical's [AngularActuatorType](/docs/en-us/reference/engine/classes/CylindricalConstraint#AngularActuatorType)  is set to [Motor](/docs/en-us/reference/engine/enums/ActuatorType) , it attempts to rotate the attachments with the goal of reaching its [AngularVelocity](/docs/en-us/reference/engine/classes/CylindricalConstraint#AngularVelocity) . You can further control this rotation through both [MotorMaxAngularAcceleration](/docs/en-us/reference/engine/classes/CylindricalConstraint#MotorMaxAngularAcceleration)  and [MotorMaxTorque](/docs/en-us/reference/engine/classes/CylindricalConstraint#MotorMaxTorque) .

If a cylindrical's [AngularActuatorType](/docs/en-us/reference/engine/classes/CylindricalConstraint#AngularActuatorType)  is set to [Servo](/docs/en-us/reference/engine/enums/ActuatorType) , it attempts to rotate to an angle specified by [TargetAngle](/docs/en-us/reference/engine/classes/CylindricalConstraint#TargetAngle) . This rotation is controlled by [AngularSpeed](/docs/en-us/reference/engine/classes/CylindricalConstraint#AngularSpeed) , [AngularResponsiveness](/docs/en-us/reference/engine/classes/CylindricalConstraint#AngularResponsiveness) , and [ServoMaxTorque](/docs/en-us/reference/engine/classes/CylindricalConstraint#ServoMaxTorque) .

## [Linear power](#linear-power)[](#linear-power)

If a cylindrical's [ActuatorType](/docs/en-us/reference/engine/classes/CylindricalConstraint)  is set to [Motor](/docs/en-us/reference/engine/enums/ActuatorType) , it attempts to translate the attachments with the goal of reaching [Velocity](/docs/en-us/reference/engine/classes/CylindricalConstraint) . You can further control this translation through both [MotorMaxAcceleration](/docs/en-us/reference/engine/classes/CylindricalConstraint)  and [MotorMaxForce](/docs/en-us/reference/engine/classes/CylindricalConstraint) .

If a cylindrical's [ActuatorType](/docs/en-us/reference/engine/classes/CylindricalConstraint)  is set to [Servo](/docs/en-us/reference/engine/enums/ActuatorType) , it attempts to translate the attachments to a set separation specified by [TargetPosition](/docs/en-us/reference/engine/classes/CylindricalConstraint) . This translation is controlled by [Speed](/docs/en-us/reference/engine/classes/CylindricalConstraint) , [LinearResponsiveness](/docs/en-us/reference/engine/classes/CylindricalConstraint) , and [ServoMaxForce](/docs/en-us/reference/engine/classes/CylindricalConstraint) .

## [Limits](#limits)[](#limits)

You can set limits to restrict both the sliding range  and rotation  of a cylindrical constraint.

Enabling the [LimitsEnabled](/docs/en-us/reference/engine/classes/CylindricalConstraint)  property exposes the [LowerLimit](/docs/en-us/reference/engine/classes/CylindricalConstraint)  and [UpperLimit](/docs/en-us/reference/engine/classes/CylindricalConstraint)  values, as well as [Restitution](/docs/en-us/reference/engine/classes/CylindricalConstraint)  which defines the elasticity of the attachments when they reach either limit.

Enabling the [AngularLimitsEnabled](/docs/en-us/reference/engine/classes/CylindricalConstraint#AngularLimitsEnabled)  property exposes the [LowerAngle](/docs/en-us/reference/engine/classes/CylindricalConstraint#LowerAngle)  and [UpperAngle](/docs/en-us/reference/engine/classes/CylindricalConstraint#UpperAngle)  limits, as well as [AngularRestitution](/docs/en-us/reference/engine/classes/CylindricalConstraint#AngularRestitution)  which defines the elasticity of the attachments when they reach either limit.

LimitsEnabled = true

AngularLimitsEnabled = true

## [Inclination angle](#inclination-angle)[](#inclination-angle)

[InclinationAngle](/docs/en-us/reference/engine/classes/CylindricalConstraint#InclinationAngle)  defines the direction of the rotation axis as an angle from the X  axis in the X / Y  plane of [Attachment0](/docs/en-us/reference/engine/classes/Constraint#Attachment0) , from -180 to 180. This lets you tilt the rotating element without changing the sliding axis.

InclinationAngle = 90

InclinationAngle = 30

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
