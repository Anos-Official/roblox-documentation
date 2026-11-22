<!-- Source: https://create.roblox.com/docs/physics/constraints/universal -->

Universal | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/physics/constraints/universal.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/workspace)
6. /
7. [Physics](/docs/physics)
8. /
9. [Mechanical constraints](/docs/physics/mechanical-constraints)

# Universal

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/physics/constraints/universal.md)

For an overview on creating, visualizing, and simulating mechanical constraints, including [UniversalConstraint](/docs/reference/engine/classes/UniversalConstraint) , see [Mechanical constraints](/docs/physics/mechanical-constraints) . Also see [Roblox units](/docs/physics/units)  to understand how Roblox units compare to metric units.

A [UniversalConstraint](/docs/reference/engine/classes/UniversalConstraint)  ensures two axes on two assemblies remain perpendicular. Example applications include vehicle power transmission to the rear drive shafts, robotics, and more.

## [Orientations](#orientations)[](#orientations)

Orientation of a universal's two attachments affects how it will move. To ensure it behaves correctly, the [SecondaryAxis](/docs/reference/engine/classes/Attachment#SecondaryAxis)  of the attachments, visualized by the orange arrows, should be perpendicular  to each other. Note that a green L-shaped indicator appears when the axes are properly oriented.

Axes Perpendicular Axes Misoriented

![Secondary axes perpendicular for correct behavior](https://prod.docsiteassets.roblox.com/assets/physics/constraints/Universal-Attachments-Correct.jpg)

## [Limits](#limits)[](#limits)

Enabling the [LimitsEnabled](/docs/reference/engine/classes/UniversalConstraint#LimitsEnabled)  property exposes the [MaxAngle](/docs/reference/engine/classes/UniversalConstraint#MaxAngle)  limit to restrict tilt within a cone, as well as [Restitution](/docs/reference/engine/classes/UniversalConstraint#Restitution)  which defines the elasticity of the attachments when they reach the limit.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
