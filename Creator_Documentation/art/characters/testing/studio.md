<!-- Source: https://create.roblox.com/docs/en-us/art/characters/testing/studio.md -->

---
title: "Test in Studio"
url: /docs/en-us/art/characters/testing/studio
last_updated: 2026-09-03T17:44:40Z
description: "Verify the important aspects of your character model in a custom Studio test game."
---

# Test in Studio

Test your character model in Studio to understand how it looks and feels within a Roblox game. To test your custom character in Studio, first [import the character model](/docs/en-us/avatar/character-bodies/import.md) into your Studio project.

You can test in Studio using the [Avatar Setup](/docs/en-us/avatar-setup.md) tool to preview and test various components of your avatar character.

You can also playtest your character in the [Avatar Test Place](https://www.roblox.com/games/13176231501/Avatar-Test-Place). This game provides a wide variety of environmental and clothing tests to ensure that your character model and related components work as expected.

## Set up test place

The following is the general testing process setting up the Avatar Test place:

1. Download and open the [Avatar Test place](https://www.roblox.com/games/13176231501/Avatar-Test-Place) in Studio.
2. Import your avatar model into Studio.
3. Set your model as the starter character.
4. Launch a playtest of the game.

### Open in Studio

In order to use the [Avatar Test place](https://www.roblox.com/games/13176231501/Avatar-Test-Place), you must first download it from Roblox. You can save the game locally and make any changes that may help your testing workflow. Roblox may update this game periodically to add or improve features.

To download the Avatar Test place:

1. Navigate to the [Avatar Test place](https://www.roblox.com/games/13176231501/Avatar-Test-Place).
2. In the button next to the game's title, select **…** > **Edit**. The page navigates to the Studio launcher.

### Import

After you open the test place in Studio, import your custom character model.

1. From Studio's **File** menu, select **Import**. A file browser displays.
2. Select your custom character `.fbx` file.
3. Verify the following:
  1. With the highest level object selected, ensure **Rig Type** is set to **R15**.
  2. If using the template files, set **Rig Scale** to **Rthro**. Otherwise, use the appropriate rig scale for your [character body type](/docs/en-us/avatar/character-bodies/specifications.md#body-scale).
  3. Check for any red errors that may block import into Studio.
  4. Verify any yellow warnings that may indicate a quality issue with your avatar components.
  > **Warning:** The Importer may incorrectly report some cage meshes as not watertight. You can ignore these warnings for those cage objects.
4. Click **Import**. The character's model populates into the workspace.

> **Warning:** If an error or warning message displays in the **Output** window, see [Troubleshooting](/docs/en-us/avatar/dynamic-heads/test.md#troubleshooting) for guidance on how to handle your specific error or warning message.
### Add SurfaceAppearance

If you exported your textures separately, or if the Importer fails to pick up your PBR textures, you can add them manually.

To add individual image texture files:

1. Open the **Asset Manager**. You may need to publish your game first.
2. **Bulk Upload** the image map assets.
3. In the **Explorer**, expand the **Head_Geo** and check if a `Class.SurfaceAppearance` object exists.
  - If `Class.SurfaceAppearance` is present, continue to step 4.
  - If `Class.SurfaceAppearance` is not present, select the ⊕ next to the Head_Geo and add a `Class.SurfaceAppearance` object.
4. Set each property to the corresponding uploaded image map
5. Copy the `Class.SurfaceAppearance` with the populated image map with `Ctrl``C` (`⌘``C`).
6. Hold `Shift` and click all of your model's MeshParts to select all of your character's geometry.
7. Use `Ctrl``Shift``V` (`⌘``Shift``V`) to paste into all of the head geometries. An updated `Class.SurfaceAppearance` populates in each `Class.MeshPart` object.

### Set model as StarterPlayer

In order to play as the character during a playtest, rename and move the model instance:

1. In the **Explorer** window, rename the character **model** as `StarterCharacter`.
2. In the **Explorer** window, navigate to the `Class.StarterPlayer` directory. If a `StarterCharacter` model already exists, remove it.
3. Click and drag the model under the directory.

After you rename and add your model, [playtest](/docs/en-us/studio/testing-modes.md#playtesting) the test place as the custom model.

## Use test place

The Avatar Test place includes several features in the interface and environment to quickly perform comprehensive tests of your avatar characters. You can use the [test checklist](#checklist) to ensure you are reviewing all the important aspects of your avatar character.

When playtesting, use the following UI buttons on the right side to open various testing tools and options:

| Button | Description |
| --- | --- |
| <br>Avatars and facial animation | Use this menu to swap between the custom avatar and control avatars. An additional button option allows you to loop through various facial animations to test your character's face expressions. |
| <br>Emotes and animations | Use this menu to test various animations on your avatar character. |
| <br>Skin tone color palette | Use this menu to select a new skin tone for your character. See [Custom Skin Tones](../../../assets/art/avatar/basic-creation/Testing-UI-Emote.png) for more details on this implementation with template character models. |
| <br>Clothes and accessories | Use this menu to select various clothing items to try on. |
| <br>Movement settings | Use this menu to change movement settings for your character model, such as **jump height** and **walk speed**. |
| <br>Body proportion settings | Use this menu to change various aspects of your character's body proportions. |
| <br>Lighting presets | Use this menu to change the environment lighting to various presets, such as **Mountains - Sunset**, or **Indoor - Midday**. |

### Checklist

Use the following checklists to ensure that you are comprehensively testing each component of your avatar. Use the Avatar menu to switch between your custom avatar and a control avatar to verify expected behavior.

#### Movement and animation

_Testing guitar animation emote_

_Testing water movement_

_Testing ramp movement_

Check the following for any anomalies:

| Function | How to test |
| --- | --- |
| Walking | Move the character around the environment, ramps, and platforms. |
| Sitting | Move to any of the seats in the environment and press `E` to sit. |
| Climbing | Move to any of the trusses and ladders. Your character automatically begins climbing when near. |
| Swimming | Use the pool of water at the top of the ramp area to verify your swimming animation. |
| Jumping | Press `Space` to jump. |
| Dying | Use any of the death cubes to set your character to a ragdoll state and respawn. |
| Facial Animation | Use the **Face UI menu** to toggle a face animation cycle. |
| Emotes and Animation | Use the **Emote UI menu** to access and play the available emotes. |

If you see unexpected behavior with your character's movement, there may be some issues with the rigging or skinning of your character. It may require revisiting the rigging and armature components of your avatar model in your modeling application.

#### Lighting and color

_Testing skin tones_

_Testing environmental lighting_

Check the following for any anomalies:

| Function | How to test |
| --- | --- |
| Skin tone | Use the **Skin Tone UI** menu to test various skin tones for texturing and lighting compatibility. |
| Environmental lighting | Use the **Lighting UI menu** and the environment to check how your character's surface appearance displays in various conditions. |

If you see unexpected behavior with your character's appearance in various lighting and color selections, there may be some issues with the texturing of your character. It may require re-adjusting the texturing components of your avatar model in your modeling application.

#### Clothing and accessories

_Test a mix of clothing and accessories_

_Use the UI menu or pedestals to equip or reset clothing and accessories_

Check the following for any anomalies:

| Function | How to test |
| --- | --- |
| Equipping accessories | Use the **Clothes and Accessories UI menu** or environmental pedestals to equip rigid accessories to your character. |
| Equipping clothing | Use the **Clothes and Accessories UI menu** or environmental pedestals to equip rigid accessories to your character. Test your clothing in motion and in animations to verify the fit. |

If you see unexpected behavior with your character wearing clothes or equipping rigid accessories, there may be issues with the caging or attachment points of your character. You may need to re-adjust the cage mesh shapes or attachment objects of your avatar model in your modeling application.

> **Warning:** Clothes can layer in unconventional orders, such as a jacket worn below a tshirt. You can reset the equipped clothing and try various combinations of clothing options and ordering.