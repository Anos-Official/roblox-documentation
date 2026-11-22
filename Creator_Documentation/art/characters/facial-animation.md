<!-- Source: https://create.roblox.com/docs/en-us/art/characters/facial-animation.md -->

---
title: "Heads"
url: /docs/en-us/art/characters/facial-animation
last_updated: 2026-06-16T15:58:01Z
description: "Facial animations enable avatars to create dynamic facial expressions."
---

# Heads

Heads are a fundamental component of an avatar character body. Roblox avatar heads, such as those available on the Marketplace, contains components that allow you to:

- Set default custom facial expressions.
- Trigger emotes that combine both face and body animations.
- Equip face accessories that deform with your facial expressions. For example, facial hair moves accordingly when the character changes facial expressions.

## Create basic heads

> **Warning:** When creating heads intended for the Marketplace, ensure that your head meets Roblox's [head specifications](/docs/en-us/art/head-specifications.md).

Using third-party modeling tools, you can either modify a rigged character model to meet head requirements, or create a head from scratch. For step-by-step instructions on how to add face bones, apply skinning, posing, and mapping poses on a head model in Blender, see [Create basic heads](/docs/en-us/art/characters/facial-animation/create-basic-heads.md). This guide includes several reference files you can use to compare and track your progress.

### Resources

Heads designated for the Marketplace require specific components to ensure universal support across Roblox's platform. Heads are often the most complex part of an avatar character. Use the following docs to best equip your assets to pass validation and work well with other assets:

- Understand how Roblox tests facial animations in the [validation process](/docs/en-us/art/head-validation.md) and learn common issues that you can self-resolve.
- Similar to character bodies and clothing, Marketplace heads must also follow [Roblox's specifications](/docs/en-us/art/head-specifications.md).
- Ensure that you are following Roblox's [head caging best practices](/docs/en-us/art/face-caging-best-practices.md) to ensure the best results for clothing, validation, and makeup.
- Use the [FACS poses reference](/docs/en-us/art/characters/facial-animation/facs-poses-reference.md) when posing and mapping your head.

## Create face accessories

Similar to creating heads, you can design and model face accessories using a third-party modeling software and import the models as a cosmetic `Class.Accessory` in Studio. When created correctly, equipped accessories stretch and deform as the head animates and emotes.

See [Create face accessories](/docs/en-us/art/characters/facial-animation/create-face-accessories.md) for step-by-step instructions on setting up a reference model as a face accessory. This guide includes several project files you can use for reference and covers details on time-saving steps, such as auto-skin transfer.

## Test heads

Testing is an important part of the iterative creation process. To test heads in Studio, see [Testing in Studio](/docs/en-us/art/facial-animation/use-heads-in-studio.md).

## Animate heads

If you're interested in animating a head, for use in-experience or to further test your character's face rig, see [Animate heads](/docs/en-us/art/characters/facial-animation/animate-heads.md).