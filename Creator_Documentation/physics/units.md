<!-- Source: https://create.roblox.com/docs/en-us/physics/units -->

Roblox units | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/physics/units.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/en-us/workspace)
6. /
7. [Physics](/docs/en-us/physics)

# Roblox units

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/physics/units.md)

This article outlines Roblox physical units and how they convert to metric units. Understanding units is useful whenever you work with physics, as in the following examples:

-

Tuning linear/angular velocities, forces, torques, stiffness, and damping of [mechanical constraints](/docs/en-us/physics/mechanical-constraints)  and [mover constraints](/docs/en-us/physics/mover-constraints) .

-

Adjusting the density of [custom materials](/docs/en-us/parts/materials#custom-materials) .

## [Unit conversions](#unit-conversions)[](#unit-conversions)

Primary Units Derived Units Gravity Physical Limits

In general, you can use the conversions in the following table to relate Roblox's primary units for time, length, and mass to their metric counterparts.

| Unit | | Roblox | | Metric |
| --- | --- |
| Time | | 1 second \text{1 second} 1 second | | 1 second \text{1 second} 1 second |
| Length | | 1 stud \text{1 stud} 1 stud | | 28 cm \text{28 cm} 28 cm |
| Mass | | 1 RMU \text{1 RMU} 1 RMU * | | 21.952 kg \text{21.952 kg} 21.952 kg |

* RMU = Roblox Mass Unit

## [Unit consistency](#unit-consistency)[](#unit-consistency)

Internally, the Roblox physics engine does not use unit conversions. You're free to define your own unit interpretations for studs (length) and RMUs (mass), but these should be used in a consistent manner throughout the game. For example, if you decide that one stud equals one foot (30.483 cm), the unit density of water implies an RMU is equal to 62.4 lbs (28.3 kg):

1 (g/cm³) × (30.48³ cm³/ft³) = \text{1 (g/cm³)} × \text{(30.48³ cm³/ft³)} = 1 (g/cm³) × (30.48³ cm³/ft³) =
 28,317 (g/ft³) × (0.00220462 lbs/g) = \text{28,317 (g/ft³)} × \text{(0.00220462 lbs/g)} = 28,317 (g/ft³) × (0.00220462 lbs/g) =
 62.4 (lbs/ft³) = \text{62.4 (lbs/ft³)} = 62.4 (lbs/ft³) =
 1 (RMU/stud³) \text{1 (RMU/stud³)} 1 (RMU/stud³)

Overall, it's recommended that you use standard Roblox units because it makes a game work as expected in all scenarios, such as compatibility with VR controls.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
