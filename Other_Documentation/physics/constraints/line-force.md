<!-- Source: https://create.roblox.com/docs/physics/constraints/line-force -->

LineForce | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/physics/constraints/line-force.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/workspace)
6. /
7. [Physics](/docs/physics)
8. /
9. [Mover constraints](/docs/physics/mover-constraints)

# LineForce

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/physics/constraints/line-force.md)

For an overview on creating, visualizing, and simulating mover constraints, including [LineForce](/docs/reference/engine/classes/LineForce) , see [mover constraints](/docs/physics/mover-constraints) . Also see [Roblox units](/docs/physics/units)  to understand how Roblox units compare to metric units.

The [LineForce](/docs/reference/engine/classes/LineForce)  constraint applies force along the theoretical line connecting its two [Attachments](/docs/reference/engine/classes/Attachment) . As the end points (attachments) move, the direction of force will change accordingly.

## [Force location](#force-location)[](#force-location)

By default, force is applied to either parent at its attachment location. If desired, force can be focused at each parent's center of mass by toggling on [ApplyAtCenterOfMass](/docs/reference/engine/classes/LineForce#ApplyAtCenterOfMass) .

ApplyAtCenterOfMass = false

ApplyAtCenterOfMass = true

## [Inverse square law](#inverse-square-law)[](#inverse-square-law)

When [InverseSquareLaw](/docs/reference/engine/classes/LineForce#InverseSquareLaw)  is true, the force magnitude is multiplied by the inverse square of the distance, meaning the force will increase exponentially as the two attachments get closer together, like magnets. When using this setting, it's recommended that you set a [MaxForce](/docs/reference/engine/classes/LineForce#MaxForce)  threshold to prevent infinite force if the attachments align precisely.

InverseSquareLaw = false

InverseSquareLaw = true

## [Reactionary force](#reactionary-force)[](#reactionary-force)

By default, the constraint only applies force to [Attachment0](/docs/reference/engine/classes/Constraint#Attachment0) , while [Attachment1](/docs/reference/engine/classes/Constraint#Attachment1)  remains unaffected. However, force can be applied to both attachments in equal and opposite directions  by enabling [ReactionForceEnabled](/docs/reference/engine/classes/LineForce#ReactionForceEnabled) .

ReactionForceEnabled = false

ReactionForceEnabled = true

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
