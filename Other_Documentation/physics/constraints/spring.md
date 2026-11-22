<!-- Source: https://create.roblox.com/docs/physics/constraints/spring -->

Spring | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/physics/constraints/spring.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/workspace)
6. /
7. [Physics](/docs/physics)
8. /
9. [Mechanical constraints](/docs/physics/mechanical-constraints)

# Spring

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/physics/constraints/spring.md)

For an overview on creating, visualizing, and simulating mechanical constraints, including [SpringConstraint](/docs/reference/engine/classes/SpringConstraint) , see [Mechanical constraints](/docs/physics/mechanical-constraints) . Also see [Roblox units](/docs/physics/units)  to understand how Roblox units compare to metric units.

A [SpringConstraint](/docs/reference/engine/classes/SpringConstraint)  applies a force on its attachments based on spring and damper behavior. You can customize a spring's [damping](#damping)  and [stiffness](#stiffness) , as well as set minimum and maximum [limits](#limits)  on the spring's length.

## [Free length](#free-length)[](#free-length)

[FreeLength](/docs/reference/engine/classes/SpringConstraint#FreeLength)  defines the natural resting length of the spring. If the attachments are further apart than the free length, they are forced together; if the attachments are closer together than the free length, they are forced apart.

## [Damping](#damping)[](#damping)

The [Damping](/docs/reference/engine/classes/SpringConstraint#Damping)  value controls how fast the spring's oscillation dies down. A value of 0 allows the spring to oscillate endlessly, while higher values bring the spring to a rest more quickly.

## [Stiffness](#stiffness)[](#stiffness)

[Stiffness](/docs/reference/engine/classes/SpringConstraint#Stiffness)  sets the strength of the spring. Higher values create a spring that responds with more force when its attachments are closer together or further apart than [FreeLength](/docs/reference/engine/classes/SpringConstraint#FreeLength) .

Stiffness = 25

Stiffness = 500

## [Limits](#limits)[](#limits)

Enabling the [LimitsEnabled](/docs/reference/engine/classes/SpringConstraint#LimitsEnabled)  property exposes the [MinLength](/docs/reference/engine/classes/SpringConstraint#MinLength)  and [MaxLength](/docs/reference/engine/classes/SpringConstraint#MaxLength)  values for setting the minimum and maximum length of the spring. If the spring's attachments reach these limits, they stop moving apart from one another without restitution.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
