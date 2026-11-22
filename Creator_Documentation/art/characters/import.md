<!-- Source: https://create.roblox.com/docs/en-us/art/characters/import.md -->

---
title: "Import character bodies"
url: /docs/en-us/art/characters/import
last_updated: 2026-06-16T15:58:04Z
description: "Use the Importer to add third-party models to Studio before testing, using, or uploading the character model."
---

# Import character bodies

Studio's Importer lets you import 3D assets into your projects, such as avatar clothing, accessories, and character bodies. The following instructions provide guidance on how to import a full character model into Studio as a `Model` object that you can save to use in your experience, share with others, or upload to the Marketplace.

> **Info:** If you are using a single-mesh character body for the Roblox Auto-Setup tool, see [Avatar auto-setup](/docs/en-us/avatar-setup.md).

While the 3D Importer provides object previews and error-checking to ensure that your asset meets Roblox's [general 3D requirements](/docs/en-us/art/modeling/specifications.md), it's important to ensure that your character model meets Roblox's [avatar character specifications](/docs/en-us/art/characters/specifications.md) to use or sell this asset as an avatar-ready character model, otherwise you can encounter errors at different points in the workflow.

To import your asset as a character model:

1. In the **Home** tab, click the **Import** button to open the 3D Importer. A file browser opens.
2. Select your rigged character's `.fbx` or `.gltf` file. The 3D Importer loads a preview of the character model.
  - If textures don't load for your asset, you can manually import your textures later.
  - For additional information on import settings and troubleshooting, see [3D importer](/docs/en-us/studio/importer.md).
3. In the **Rig General** section,
  1. Set **Rig Scale** to the appropriate [Body Scale](/docs/en-us/art/characters/specifications.md#body-scale) of your character.
  2. Set **Constraint Type** to **Joint Upgrade**.
4. **OPTIONAL** If you are importing a [higher-fidelity rig](/docs/en-us/art/characters/specifications.md#higher-fidelity-rigs), set **Rig Type** to **Custom Humanoid**.
5. Select **Import**. The asset populates in your workspace as a `Class.Model` with the appropriate textures applied as a `Class.SurfaceAppearance` or `Class.MeshPart.TextureID`.

**Manually add textures**

If textures didn't load correctly, add them manually. You may need to save and publish your experience in order to access the [Asset Manager](/docs/en-us/projects/assets/manager.md).

1. In the **Asset Manager**, click the **Import** button.
2. Upload your image files.
3. After moderation clears for your image, select the `Class.MeshPart` parented within your imported `Class.Model`.
4. If you are using a single basic texture, set the `Class.MeshPart.TextureID` property to your uploaded texture image.
5. If you are using PBR textures:
  1. Add a `Class.SurfaceAppearance` child to your `Class.MeshPart`.
  2. In the `Class.SurfaceAppearance` properties, click each property value and assign the appropriate texture image from the asset dropdown:
    1. Set the **ColorMap** to the **_ALB** texture image.
    2. Set the **MetalnessMap** to the **_MTL** texture image.
    3. Set the **NormalMap** to the **_NOR** texture image.
    4. Set the **RoughnessMap** to the **_RGH** texture image.

> **Success:** After successful import, your model object should populate in your project as a `Class.Model` with the appropriate textures applied.

After successful fitting and converting, your 3D model should populate in your project as an `Class.Model`.

_Avatar-ready character model in Workspace_

_Avatar-ready character model in Explorer_

> **Warning:** Character creation is a complex process that requires lots of testing and iteration. See [Test characters](/docs/en-us/art/characters/testing.md) for steps on importing your character model into a test place and verifying your avatar and related components.

With this new character `Class.Model`, you can perform any of the following:

- If your character includes a [higher-fidelity rig](/docs/en-us/art/characters/specifications.md#higher-fidelity-rigs), add a `Class.HumanoidRigDescription` and/or `Class.DigitsRigDescription` objects for Marketplace and animation requirements. You may need to use the [Adaptive Animation](/docs/en-us/characters/adaptive-animation.md) plugin to remap your joints and set a baseline t-pose reference to better support your animations.
- Begin the process of [uploading and publishing](/docs/en-us/marketplace/publish-to-marketplace.md#upload-an-asset) the character model to the Marketplace. This involves some additional validation and moderation steps.
- Use the model in your current experience and modify the model's appearance with [HumanoidDescription](/docs/en-us/characters/appearance.md#manually-modify-appearance).
  - Playtest as the character by renaming the `Class.Model` to `StarterCharacter` and moving the `Class.Model` to the `Class.StarterPlayer` folder in the **Explorer** before play testing.
- Save the model to your [Toolbox](/docs/en-us/projects/assets/toolbox.md) or make it public on the [Creator Store](/docs/en-us/production/creator-store.md) to share or use within any of your experiences.