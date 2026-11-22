<!-- Source: https://create.roblox.com/docs/physics/constraints/rope -->

Rope | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/physics/constraints/rope.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/workspace)
6. /
7. [Physics](/docs/physics)
8. /
9. [Mechanical constraints](/docs/physics/mechanical-constraints)

# Rope

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/physics/constraints/rope.md)

For an overview on creating, visualizing, and simulating mechanical constraints, including [RopeConstraint](/docs/reference/engine/classes/RopeConstraint) , see [Mechanical constraints](/docs/physics/mechanical-constraints) . Also see [Roblox units](/docs/physics/units)  to understand how Roblox units compare to metric units.

A [RopeConstraint](/docs/reference/engine/classes/RopeConstraint)  prevents two attachments from separating further than a defined [Length](/docs/reference/engine/classes/RopeConstraint#Length) . The attachments can move closer together than this length and both can freely rotate. [Restitution](/docs/reference/engine/classes/RopeConstraint#Restitution)  defines the elasticity of the attachments when they reach the separation limit specified by [Length](/docs/reference/engine/classes/RopeConstraint#Length) .

This constraint can also be powered to behave as a [motorized winch](#winch) .

## [Winch](#winch)[](#winch)

If a rope's [WinchEnabled](/docs/reference/engine/classes/RopeConstraint#WinchEnabled)  property is enabled, it attempts to translate the attachments to a set separation specified by [WinchTarget](/docs/reference/engine/classes/RopeConstraint#WinchTarget) , effectively the target length of the rope in studs. This translation is controlled by [WinchSpeed](/docs/reference/engine/classes/RopeConstraint#WinchSpeed) , [WinchResponsiveness](/docs/reference/engine/classes/RopeConstraint#WinchResponsiveness) , and [WinchForce](/docs/reference/engine/classes/RopeConstraint#WinchForce) .

[WinchSpeed](/docs/reference/engine/classes/RopeConstraint#WinchSpeed)  must be a positive  value, used to either contract or extend the rope length to [WinchTarget](/docs/reference/engine/classes/RopeConstraint#WinchTarget) . Setting a negative speed will revert to 0, not reverse the winch servo direction.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
