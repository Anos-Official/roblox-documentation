<!-- Source: https://create.roblox.com/docs/physics/constraints/rigid -->

Rigid | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/physics/constraints/rigid.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/workspace)
6. /
7. [Physics](/docs/physics)
8. /
9. [Mechanical constraints](/docs/physics/mechanical-constraints)

# Rigid

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/physics/constraints/rigid.md)

A [RigidConstraint](/docs/reference/engine/classes/RigidConstraint)  connects two [Attachments](/docs/reference/engine/classes/Attachment)  or [Bones](/docs/reference/engine/classes/Bone)  and ensures they stay in the same relative position/orientation to each other. This flexibility gives it additional functionality beyond [WeldConstraint](/docs/reference/engine/classes/WeldConstraint) , such as attaching accessories to [Attachments](/docs/reference/engine/classes/Attachment)  on a character rig.

To attach two [BaseParts](/docs/reference/engine/classes/BasePart)  together, versus two [Attachments](/docs/reference/engine/classes/Attachment)  or [Bones](/docs/reference/engine/classes/Bone) , see [WeldConstraint](/docs/physics/constraints/weld) .

When creating a [RigidConstraint](/docs/reference/engine/classes/RigidConstraint)  using Studio's [Constraint](/docs/physics/mechanical-constraints#create-constraints)  button, the tool behaves differently depending on whether you click on existing [BaseParts](/docs/reference/engine/classes/BasePart) , [Attachments](/docs/reference/engine/classes/Attachment) , or [Bones](/docs/reference/engine/classes/Bone)  after the tool is activated:

-

Clicking on an existing [BasePart](/docs/reference/engine/classes/BasePart)  creates a new [Attachment](/docs/reference/engine/classes/Attachment)  upon it as the intended [RigidConstraint.Attachment0](/docs/reference/engine/classes/RigidConstraint#Attachment0)  or [RigidConstraint.Attachment1](/docs/reference/engine/classes/RigidConstraint#Attachment1) .

-

Clicking on an existing [Attachment](/docs/reference/engine/classes/Attachment)  or [Bone](/docs/reference/engine/classes/Bone)  uses that instance as the intended [RigidConstraint.Attachment0](/docs/reference/engine/classes/RigidConstraint#Attachment0)  or [RigidConstraint.Attachment1](/docs/reference/engine/classes/RigidConstraint#Attachment1) .

Following the second valid click, a new [RigidConstraint](/docs/reference/engine/classes/RigidConstraint)  is created to connect the two new attachments. If either the first or second click is not  made on a [BasePart](/docs/reference/engine/classes/BasePart) , [Attachment](/docs/reference/engine/classes/Attachment) , or [Bone](/docs/reference/engine/classes/Bone) , the workflow is canceled and no constraint is created.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
