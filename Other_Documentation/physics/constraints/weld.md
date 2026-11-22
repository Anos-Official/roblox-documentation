<!-- Source: https://create.roblox.com/docs/physics/constraints/weld -->

Weld | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/physics/constraints/weld.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/workspace)
6. /
7. [Physics](/docs/physics)
8. /
9. [Mechanical constraints](/docs/physics/mechanical-constraints)

# Weld

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/physics/constraints/weld.md)

A [WeldConstraint](/docs/reference/engine/classes/WeldConstraint)  connects two [BaseParts](/docs/reference/engine/classes/BasePart)  and ensures they stay in the same relative position and orientation to each other. Even if the two parts are not touching, you can weld them together.

To attach two [Attachments](/docs/reference/engine/classes/Attachment)  or [Bones](/docs/reference/engine/classes/Bone) , versus two [BaseParts](/docs/reference/engine/classes/BasePart) , see [RigidConstraint](/docs/physics/constraints/rigid) .

Unique to [WeldConstraint](/docs/reference/engine/classes/WeldConstraint)  are slight behavioral differences in how Studio handles creation and repositioning of welded parts.

Weld Creation Repositioning Welded Parts

When creating a [WeldConstraint](/docs/reference/engine/classes/WeldConstraint)  using Studio's [Constraint](/docs/physics/mechanical-constraints#create-constraints)  button, the tool behaves differently depending on how many [BaseParts](/docs/reference/engine/classes/BasePart)  are selected when the tool is activated:

-

If no [BaseParts](/docs/reference/engine/classes/BasePart)  are selected, the next two [BaseParts](/docs/reference/engine/classes/BasePart)  clicked will be connected by a new [WeldConstraint](/docs/reference/engine/classes/WeldConstraint) . If the same [BasePart](/docs/reference/engine/classes/BasePart)  is clicked twice, no constraint will be created.

-

If one [BasePart](/docs/reference/engine/classes/BasePart)  is already selected, the next [BasePart](/docs/reference/engine/classes/BasePart)  clicked will be connected to the selected one with a new [WeldConstraint](/docs/reference/engine/classes/WeldConstraint) .

-

If multiple [BaseParts](/docs/reference/engine/classes/BasePart)  are selected, those which are touching or overlapping will be automatically welded together by new [WeldConstraints](/docs/reference/engine/classes/WeldConstraint) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
