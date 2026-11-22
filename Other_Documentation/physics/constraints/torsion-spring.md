<!-- Source: https://create.roblox.com/docs/physics/constraints/torsion-spring -->

TorsionSpring | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/physics/constraints/torsion-spring.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/workspace)
6. /
7. [Physics](/docs/physics)
8. /
9. [Mechanical constraints](/docs/physics/mechanical-constraints)

# TorsionSpring

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/physics/constraints/torsion-spring.md)

For an overview on creating, visualizing, and simulating mechanical constraints, including [TorsionSpringConstraint](/docs/reference/engine/classes/TorsionSpringConstraint) , see [Mechanical constraints](/docs/physics/mechanical-constraints) . Also see [Roblox units](/docs/physics/units)  to understand how Roblox units compare to metric units.

A [TorsionSpringConstraint](/docs/reference/engine/classes/TorsionSpringConstraint)  applies torque based on a relative angle and relative angular velocity. It attempts to bring two axes from two parts together and is useful for [hinged](/docs/physics/constraints/hinge)  swinging doors with a spring-back effect.

Correct orientation of a torsion spring's attachments is important. The constraint will attempt to bring the [SecondaryAxis](/docs/reference/engine/classes/Attachment#SecondaryAxis)  of each attachment, visualized by the orange arrows, into alignment. When building mechanisms like swinging doors, ensure that the secondary axes are perpendicular  to the intended axis of rotation.

## [Damping](#damping)[](#damping)

The [Damping](/docs/reference/engine/classes/TorsionSpringConstraint#Damping)  value controls how fast the spring's oscillation dies down. A value of 0 allows the spring to oscillate endlessly, while higher values bring the spring to a rest more quickly.

Damping = 0

Damping = 50

## [Stiffness](#stiffness)[](#stiffness)

[Stiffness](/docs/reference/engine/classes/TorsionSpringConstraint#Stiffness)  sets the torsional strength of the spring. Higher values create a spring that responds with more force.

## [Limits](#limits)[](#limits)

Enabling the [LimitsEnabled](/docs/reference/engine/classes/TorsionSpringConstraint#LimitsEnabled)  property exposes the [MaxAngle](/docs/reference/engine/classes/TorsionSpringConstraint#MaxAngle)  value to restrict the spring's range within a cone; it also exposes the [Restitution](/docs/reference/engine/classes/TorsionSpringConstraint#Restitution)  value which defines the elasticity of the attachments when they reach their limit.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
