<!-- Source: https://create.roblox.com/docs/en-us/art/accessories/body-scale.md -->

---
title: "Body scale and proportions"
url: /docs/en-us/art/accessories/body-scale
last_updated: 2026-07-20T22:27:25Z
description: "Avatars come in 3 different standard sizes, Classic, Rthro, Rthro Slender."
---

# Body scale and proportions

Roblox supports three common avatar sizes, known as **Classic**, **Rthro**, and **Rthro Slender**. This standard sizing helps keep avatar characters consistent, allowing developers to create games and environments that can fit commonly sized character models.

When modeling rigid accessories, like a helmet that contours around a character's head, it's important to use a mannequin to help ensure your proportions fit. The asset provided in this tutorial example was originally modeled using **Rthro** proportions. Layered clothing, such as clothing, don't require body scale specification, since layered assets automatically stretch and deform over any body scale.

If you are modeling your asset, visit the [references resources](/docs/en-us/avatar/resources.md#references) to download any of the following mesh mannequin:

_ Classic blocky body scale.  Roughly 4.75 studs tall._

_ Normal body scale.  Roughly 5.75-6.5 studs tall, with wider shoulders and narrower hips._

_ Slender body scale.  Roughly 5.25-6.25 studs tall, with narrower shoulders and wider hips._

See the [accessory specifications](/docs/en-us/avatar/rigid-accessories/specifications.md#body-scale) and the [body specifications](/docs/en-us/avatar/character-bodies/specifications.md#body-scale) for specific range values and other geometry requirements.

## AvatarPartScaleType

Roblox represents body scale in the engine by an `AvatarPartScaleType` `Class.StringValue` object within each avatar character part and associated accessory. In most cases, asset creators do not need to directly access or modify this value object since tools, such as the [Accessory Fitting Tool](/docs/en-us/avatar/accessory-fitting-tool.md), automatically generate the appropriate value object on accessory creation.

In cases where you may need to identify the current body scale of a body part or accessory, the following table defines the `AvatarPartScaleType` value for each type of body size. When importing your model, use the Importer's [Rig Scale](/docs/en-us/studio/importer.md) to automatically apply a scale to your custom asset.

| Body Scale | AvatarPartScaleType value |
| --- | --- |
| Classic | `Classic` |
| Normal | `ProportionsNormal` |
| Slender | `ProportionsSlender` |