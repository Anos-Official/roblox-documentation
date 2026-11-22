<!-- Source: https://create.roblox.com/docs/en-us/animation -->

Animation in Roblox | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/animation.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Animation](/docs/en-us/animation)

# Animation in Roblox

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/animation/index.md)

Animation  is the process of applying motion to your characters, objects, and environments to create an engaging and dynamic game. While there are many ways to make objects move and interact, animation in Roblox typically refers to customizing an expressive movement of a specific character or group of parts.

Animation can apply to any Roblox part or group of parts. Different types of objects can utilize various animation features. The following are the general categories of animatable objects:

-

Simple objects , such as a basic part, can only animate changes across the part's single position or rotation property.

-

Rigs , or parts connected by joints like [AnimationConstraints](/docs/en-us/reference/engine/classes/AnimationConstraint)  or [Bones](/docs/en-us/reference/engine/classes/Bone) , can articulate positional and rotational movement between their joints, like elbows and wrists. Rigged models can take advantage of animation features like [inverse kinematics](#inverse-kinematics)  to quickly and programmatically apply movement in response to environments and events.

-

[Standard](/docs/en-us/avatar/character-bodies/specifications#standard-r15-rigs)  and [advanced](/docs/en-us/avatar/character-bodies/specifications#advanced-r15-rigs)  R15 rigs can use animations from Roblox's character animation library and other movement features, regardless of if it's a player or non-player character model.

## [Animation Editor](#animation-editor)[](#animation-editor)

The [Animation Editor](/docs/en-us/animation/editor)  allows you to design and publish custom animations on rigs. You can move the joints that connect individual sections of a rig to create poses, and the editor smoothly animates the rig from pose-to-pose.

## [Inverse kinematics](#inverse-kinematics)[](#inverse-kinematics)

You can use [inverse kinematics](/docs/en-us/animation/inverse-kinematics)  APIs to automatically create animations and poses based on environmental and external events. With inverse kinematics, you can procedurally generate various animation events, such as having a character's head track a bird flying in the sky, or making a character's arm automatically reach for a door knob when nearby.

## [Animation events](#animation-events)[](#animation-events)

An [animation event](/docs/en-us/animation/events)  is a specific point in an animation that triggers an action. You can define animation event markers across the [Animation Editor](/docs/en-us/animation/editor)  timeline span, then use [AnimationTrack:GetMarkerReachedSignal()](/docs/en-us/reference/engine/classes/AnimationTrack#GetMarkerReachedSignal)  to detect those markers as the animation runs to perform specific actions, such as playing a sound effect whenever the user's foot touches the ground.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
