<!-- Source: https://create.roblox.com/docs/en-us/workspace/camera/free-camera -->

Free camera mode | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/workspace/camera/free-camera.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/en-us/workspace)
6. /
7. [Camera](/docs/en-us/workspace/camera)

# Free camera mode

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/workspace/camera/free-camera.md)

Roblox provides a custom debug free camera mode  (freecam) to experience owners and editors, which detaches the camera from your character so you can fly it freely through your experience for capturing scenes the default camera can't reach. It's especially useful for capturing cinematic screenshots and videos, as well as spectating players in live games and debugging issues.

## [Availability](#availability)[](#availability)

You can use free camera mode in two places:

-

Roblox Studio  - freecam is available during [playtesting](/docs/en-us/studio/testing-modes#playtesting)  sessions.

-

The live client  - you must be the experience owner, or be granted edit permissions in the experience.

Currently, freecam can only be toggled on with a keyboard (Left Shift  + P ). Once active, it can be controlled with either keyboard and mouse or a gamepad.

## [How to toggle](#how-to-toggle)[](#how-to-toggle)

Press Left Shift  + P  to toggle free camera mode on or off. When enabled, the camera detaches from your character and your on-screen UI is automatically hidden so you get an unobstructed view of the scene.

## [Input Action System](#input-action-system)[](#input-action-system)

The enhanced free camera capabilities described on this page — including the [configuration menu](#configuration-menu)  and [cinematic post-processing](#custom-post-processing)  — run on the [Input Action System](/docs/en-us/input/input-action-system)  (IAS) and are available only when your experience is opted into the upgraded IAS player scripts.

To opt in, set [Workspace.PlayerScriptsUseInputActionSystem](/docs/en-us/reference/engine/classes/Workspace#PlayerScriptsUseInputActionSystem)  to [Enabled](/docs/en-us/reference/engine/enums/RolloutState)  to allow free camera controls to run on IAS so inputs sink cleanly alongside your default gameplay actions.

## [Camera controls](#camera-controls)[](#camera-controls)

In freecam mode, the camera can move and rotate to your desired positioning independent of the character and scene. The following controls are available to control the camera:

| Action | | Keyboard & Mouse | | Gamepad |
| --- | --- |
| Move forward / left / back / right | | W  A  S  D | | Left thumbstick |
| Change elevation (up / down) | | E  / Q | | R2  / L2 |
| Rotate / pan the view | | Hold the right mouse button and drag, or pan on a trackpad | | Right thumbstick |
| Zoom (field of view) | | Mouse scroll wheel, or trackpad pinch | | X  / Y |
| Roll (tilt left / right) | | Z  / C  — double-tap either key to reset roll | | L1  / R1  — double-tap to reset roll |
| Move slower for precise framing | | Hold Shift  while moving | | — |
| Open the configuration menu | | ↑  (up arrow) | | D-pad Up |

### [Movement](#movement)[](#movement)

Use W  A  S  D  (or the left thumbstick) to fly the camera through your scene.

### [Elevation](#elevation)[](#elevation)

Use E  and Q  (or R2  / L2 ) to raise and lower the camera vertically.

### [Rotation](#rotation)[](#rotation)

Hold the right mouse button and drag (or use the right thumbstick) to rotate and pan the view toward your subject.

### [Field of view](#field-of-view)[](#field-of-view)

Scroll the mouse wheel (or press X  / Y  on a gamepad) to zoom the field of view. Narrowing the field of view produces a tighter, more telephoto framing on distant subjects.

### [Roll](#roll)[](#roll)

Use Z  and C  (or L1  / R1 ) to roll the camera for a Dutch-angle effect. Double-tap either roll control to snap the camera back to the default level.

## [Configuration menu](#configuration-menu)[](#configuration-menu)

Press ↑  (or D-pad Up) to open the on-screen config menu , which exposes deeper adjustments for fine-tuning your shot.

Navigate the menu with the following controls:

-

↑  ↓  move the selection through the list.

-

→  enters a group or selects an item to edit.

-

←  goes back to the previous level, or closes the menu from the top level.

-

When editing an item, ←  →  adjust the value and ↑  ↓  exit editing.

On a gamepad, use the D-pad in the corresponding directions.

### [Movement, rotation, roll, and field of view](#movement-rotation-roll-and-field-of-view)[](#movement-rotation-roll-and-field-of-view)

Each of these motion controls exposes two independent settings in the config menu:

-

Speed  controls how fast the value changes. Increase it to cover ground, zoom, tilt, or pan more quickly; decrease it for fine, precise adjustments.

-

Stiffness  controls how the camera settles into an input change. Higher stiffness is snappy and follows your input tightly with little smoothing; lower stiffness adds damping so the camera eases in and out gradually for smoother, more cinematic motion.

High speed  — the camera rotates quickly:

Low speed  — the camera rotates slowly for precise framing:

High stiffness  — the camera follows input tightly and stops sharply:

Low stiffness  — the camera eases in and out for smoother, more cinematic motion:

### [UI visibility](#ui-visibility)[](#ui-visibility)

Control which on-screen interface stays visible so you can capture a clean shot or keep key information on screen.

-

Screen GUIs  — toggle the experience's on-screen UI overlays. Set to On  to keep them visible, or Off  to hide them for an unobstructed view.

-

Leaderboard  — toggle the player leaderboard. Set to On  to keep it on screen, or Off  to hide it.

### [Player Lock](#player-lock)[](#player-lock)

Player Lock keeps the camera trained on a specific player's character as they move, so you can follow the action without manually tracking.

-

Enable  — turn Player Lock on or off. When on, the camera follows the chosen target; when off, the camera moves freely.

-

Target  — cycle through the players in the server to choose who the camera locks onto.

### [Custom post-processing](#custom-post-processing)[](#custom-post-processing)

Layer cinematic [post-processing effects](/docs/en-us/environment/post-processing-effects)  onto your shot. Enable  disables all existing post-processing effects in favor of custom freecam ones, and each effect below can then be toggled and fine-tuned on its own:

-

[Depth of Field](/docs/en-us/environment/post-processing-effects#depth-of-field)  blurs parts of the scene that aren't in focus — great for drawing the eye to a subject or softening a distant background.

-

[Bloom](/docs/en-us/environment/post-processing-effects#bloom)  exaggerates bright lights so light-colored areas glow, simulating a camera pointed at a strong light source.

-

[Blur](/docs/en-us/environment/post-processing-effects#blur)  applies a Gaussian blur across the entire view for soft, dreamy, or fully out-of-focus looks.

-

[Color Correction](/docs/en-us/environment/post-processing-effects#color-correction)  adjusts brightness, contrast, saturation, and tint to set the mood or grade the overall color of your shot.

-

[Sun Rays](/docs/en-us/environment/post-processing-effects#sun-rays)  casts a halo of light with rays around the sun, shaped by objects between the camera and the sun for realistic light and shadow.

-

[Color Grading](/docs/en-us/environment/post-processing-effects#color-grading)  changes how rendered colors map to the screen — switch between the vivid modern look and a less-saturated retro tone.

## [GUI visibility shortcuts](#gui-visibility-shortcuts)[](#gui-visibility-shortcuts)

Separate from the config menu's [UI visibility](#ui-visibility)  toggles, Roblox provides engine-level keyboard shortcuts that hide categories of on-screen UI, useful for capturing a clean shot without any interface. They work in the live client  and in a Studio playtest , and are available to the same audience as free camera — the experience owner or a user with edit permission (and always in Studio). Press the same shortcut again to restore.

These controls are currently available for keyboard only. Hold Ctrl  (or ⌘  on macOS) and Left Shift , then press:

| Shortcut | | Hides / shows |
| Ctrl Left Shift G | | The Roblox-provided Core UI , such as the top bar and menus. |
| Ctrl Left Shift C | | Developer-created [ScreenGuis](/docs/en-us/reference/engine/classes/ScreenGui)  (on-screen 2D UIs). |
| Ctrl Left Shift B | | Developer-created [BillboardGuis](/docs/en-us/reference/engine/classes/BillboardGui)  (world-space 3D billboards). |
| Ctrl Left Shift N | | Player nameplates (names and health bars). |

Ctrl Left Shift G  — toggle the Roblox Core UI:

Ctrl Left Shift C  — toggle the experience's on-screen GUIs:

Ctrl Left Shift B  — toggle developer-created BillboardGuis:

Ctrl Left Shift N  — toggle player nameplates:

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
