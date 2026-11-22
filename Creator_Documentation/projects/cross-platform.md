<!-- Source: https://create.roblox.com/docs/en-us/projects/cross-platform -->

Cross-platform development | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/projects/cross-platform.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Projects](/docs/en-us/projects)

# Cross-platform development

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/projects/cross-platform.md)

Roblox is inherently cross‑platform , as players can discover and join games on their phone or tablet, then later continue where they left off on their PC or console. To support an expanding suite of platforms, you should build user interfaces that seamlessly adapt to the input type (touch, gamepad, mouse/keyboard), screen size, and device orientation. This guide, the [adaptive design](/docs/en-us/production/publishing/adaptive-design)  guide, and the linked resources can help you design a true cross‑platform game that's compatible, accessible, and enjoyable on all  platforms.

To explore a pre-made game that showcases the following cross‑platform design concepts, check out the [Interactivity Showcase](https://www.roblox.com/games/132115384567250/) .

## [Input](#input)[](#input)

A carefully designed game should support all primary input types, including mouse and keyboard, touch, and gamepads.

### [Cross-platform actions](#cross-platform-actions)[](#cross-platform-actions)

Support all primary input types (mouse/keyboard, touch, and gamepads) using the [Input Action System](/docs/en-us/input/input-action-system) .

To simplify cross‑platform inputs, Roblox provides the [Input Action System](/docs/en-us/input/input-action-system)  to define actions  such as "jump," "sprint," or "shoot" and set up bindings  for multiple hardware inputs to drive those actions. You do not need to think about all the technical aspects of hardware inputs and when to listen for specific input triggers; you simply define which inputs perform which actions.

 ![](https://prod.docsiteassets.roblox.com/assets/publishing/cross-platform/Input-Actions-Jump.png)

### [Input type detection](#input-type-detection)[](#input-type-detection)

Ensure that UI elements respond and adapt to the player's primary  input type as detailed in [input type detection](/docs/en-us/input#input-type-detection) . Also consider [assistive hints](#assistive-hints)  to help players understand specific input changes.

In cross-platform development, it's important that you determine and respond to the primary input type a player is using, normally to ensure that [UI elements](/docs/en-us/ui#ui-objects)  like on‑screen buttons and menus work elegantly and support interaction across devices.

For example, a touch‑enabled device assumes touch is the default  input and that touch buttons may appear for actions, but a player may choose to connect a bluetooth gamepad. In this case, touch remains a valid input, but you can assume the player wants to switch to the connected gamepad as the primary  input type and possibly use touch as a backup input for on‑screen UI.

If you're using the [Input Action System](/docs/en-us/input/input-action-system) , the [PreferredBinding](/docs/en-us/reference/engine/classes/InputAction#PreferredBinding)  property complements primary input detection: just as [PreferredInput](/docs/en-us/reference/engine/classes/UserInputService#PreferredInput)  reports the player's current primary input type, [PreferredBinding](/docs/en-us/reference/engine/classes/InputAction#PreferredBinding)  reports the specific [InputBinding](/docs/en-us/reference/engine/classes/InputBinding)  that matches the player's current device. Both update automatically as the player switches devices, so you can drive device‑aware UI without writing device‑switch logic yourself.

### [Assistive hints](#assistive-hints)[](#assistive-hints)

Based on the [primary input type](#input-type-detection) , it's recommended that you include assistive UI hints  whenever possible. For example, when selecting tools to equip, display input‑specific hints such as 1 – 5  when the player is using a keyboard, or gamepad trigger hints when the player is using a gamepad.

For no-code assistive hints that automatically update when the player switches devices, use [InputActionLabel](/docs/en-us/reference/engine/classes/InputActionLabel)  and point it at any [InputAction](/docs/en-us/reference/engine/classes/InputAction)  to display the correct input per platform. See [displaying bindings](/docs/en-us/input/input-action-system#displaying-bindings)  for full details.

For more granular control, or if you need to customize hint display beyond what [InputActionLabel](/docs/en-us/reference/engine/classes/InputActionLabel)  offers, you can use the [UserInputService](/docs/en-us/reference/engine/classes/UserInputService)  methods below to manually gather platform‑specific images and strings:

Keyboard Input Gamepad Input

![](https://prod.docsiteassets.roblox.com/assets/publishing/cross-platform/Inventory-Selection-Keyboard.jpg)

The [GetImageForKeyCode()](/docs/en-us/reference/engine/classes/UserInputService#GetImageForKeyCode)  and [GetStringForKeyCode()](/docs/en-us/reference/engine/classes/UserInputService#GetStringForKeyCode)  methods are helpful in gathering a platform‑specific image or string to use in a UI hint, such as the following examples:

| Key Code | | Xbox Image | | PlayStation Image | | String |
| --- | --- |
| [Enum.KeyCode.ButtonA](/docs/en-us/reference/engine/enums/KeyCode#ButtonA) | | ![](https://prod.docsiteassets.roblox.com/assets/publishing/cross-platform/ButtonA-Xbox.png) | | ![](https://prod.docsiteassets.roblox.com/assets/publishing/cross-platform/ButtonA-PS.png) | | ButtonA |
| [Enum.KeyCode.ButtonX](/docs/en-us/reference/engine/enums/KeyCode#ButtonX) | | ![](https://prod.docsiteassets.roblox.com/assets/publishing/cross-platform/ButtonX-Xbox.png) | | ![](https://prod.docsiteassets.roblox.com/assets/publishing/cross-platform/ButtonX-PS.png) | | ButtonX |
| [Enum.KeyCode.One](/docs/en-us/reference/engine/enums/KeyCode#One) | | n/a | | n/a | | 1 |
| [Enum.KeyCode.Five](/docs/en-us/reference/engine/enums/KeyCode#Five) | | n/a | | n/a | | 5 |

## [User interface](#user-interface)[](#user-interface)

A well-designed user interface is essential for players on all platforms to interact with your game.

### [Position and size](#position-and-size)[](#position-and-size)

Ensure that all UI elements are visible on all screen sizes and orientations.

Ensure that all buttons/controls are interactable and that they are not blocked or obscured by [device cutouts or Roblox UI elements](/docs/en-us/ui/position-and-size#cross-platform-factors) .

All UI elements should be [positioned](/docs/en-us/ui/position-and-size#position)  and [sized](/docs/en-us/ui/position-and-size#size)  appropriately to ensure visibility and interactivity across multiple screen sizes. Positioning UI elements by [Scale](/docs/en-us/reference/engine/datatypes/UDim#Scale)  is a common approach since it's based on a percentage  of the screen's X  and Y  bounds, not a pixel value (pixels can vary arbitrarily by both number and density across devices). You can also utilize the element's [AnchorPoint](/docs/en-us/reference/engine/classes/GuiObject#AnchorPoint)  to set its positional origin. For example, the UI container holding the gem/coin counters in the following image is positioned at an X  scale of 1  (right) and Y  scale of 0  (top) with an upper‑right anchor point.

 ![](https://prod.docsiteassets.roblox.com/assets/publishing/cross-platform/Position-Scale.jpg)

[Scale](/docs/en-us/reference/engine/datatypes/UDim#Scale)  is also recommended for sizing  UI elements, such as making a UI container span 75% width on every screen. However, 75% would render to a huge size on 4K TVs for console players, so it's recommended that you explore [screen size adaptation](#screen-size-adaptation)  as a way to adapt UI layouts across different viewports.

### [Screen size adaptation](#screen-size-adaptation)[](#screen-size-adaptation)

Adapt UI to various display sizes by checking and listening for changes to the viewport display size.

With a multitude of possible screen sizes accessible to the Roblox platform, attempting to predict screen size by pixels often leads to misinterpretation. To assist in determining a player's screen size to adapt the size/position of UI elements, Roblox provides the read‑only [ViewportDisplaySize](/docs/en-us/reference/engine/classes/GuiService#ViewportDisplaySize)  property which represents the internally‑categorized rendering size of the viewport.

| [ViewportDisplaySize](/docs/en-us/reference/engine/classes/GuiService#ViewportDisplaySize) | | Summary |
| [Small](/docs/en-us/reference/engine/enums/DisplaySize#Small) | | Most tablet/mobile/handheld devices |
| [Medium](/docs/en-us/reference/engine/enums/DisplaySize#Medium) | | Most laptops and monitors |
| [Large](/docs/en-us/reference/engine/enums/DisplaySize#Large) | | Most TVs or larger |

For more native customization, you can use the UI [Style Editor](/docs/en-us/ui/styling/editor)  to configure [Style Queries](/docs/en-us/ui/styling/editor#style-queries)  for both [ViewportDisplaySize](/docs/en-us/reference/engine/classes/GuiService#ViewportDisplaySize)  and [PreferredInput](/docs/en-us/reference/engine/classes/UserInputService#PreferredInput)  values. Using intrinsic selectors like @ViewportDisplaySizeSmall  or @PreferredInputTouch  allows your UI to automatically swap tokens for text sizes, container dimensions, and other measurements as the player's device environment or primary input method changes.

### [Layout containers](#layout-containers)[](#layout-containers)

Use layouts to organize individual UI components and ensure that containers adjust responsively to the children elements within them.

For easier UI organization, you should use layout components  to organize children. When using layout [containers](/docs/en-us/ui/frames) , make sure that the children are legible, [accessible](#accessibility) , and non‑cluttered. A common layout component is [UIListLayout](/docs/en-us/reference/engine/classes/UIListLayout) , which positions sibling [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject)  into rows or columns and adjusts accordingly whenever you add or remove a sibling object.

You should also consider the distribution and relative positioning of elements within layout containers for the best user experience. Integrating [flex](/docs/en-us/ui/list-flex-layouts#flex-layouts)  into a list layout is a powerful way to [equally fill/distribute](/docs/en-us/ui/list-flex-layouts#equal-fill-or-distribution)  or [align/stretch](/docs/en-us/ui/list-flex-layouts#alignment)  items across their line, or [flex specific items](/docs/en-us/ui/list-flex-layouts#flex-individual-items)  across a variable space.

 ![UIListLayouts illustrating FillDirection of either horizontal or vertical.](https://prod.docsiteassets.roblox.com/assets/engine-api/classes/UIListLayout/FillDirection.png)

### [Accessibility](#accessibility)[](#accessibility)

Ensure that all text is legible on all screens. Also make sure all UI has [sufficient contrast](/docs/en-us/production/publishing/accessibility#color-contrast)  and that [nothing relies solely on color](/docs/en-us/production/publishing/accessibility#color-non-reliance)  to distinguish an action or outcome.

Even with UI elements [properly sized](#position-and-size)  across all device screen sizes, the overall game should meet [accessibility standards](/docs/en-us/production/publishing/accessibility)  for players with impaired vision or color blindness. Text size can factor heavily into the legibility of text‑based UI, so you should include a [text size constraint](/docs/en-us/ui/size-modifiers#text-size)  to ensure text doesn't become illegible (too small) or visually too large on larger screens like 4K TVs.

For more tips on accessibility, see [accessibility guidelines](/docs/en-us/production/publishing/accessibility) .

## [Final tips & tricks](#final-tips--tricks)[](#final-tips--tricks)

As you work toward a full cross‑platform game, consider the following tips and tricks:

-

Device emulation is essential to designing an optimal game on Roblox. Utilize the built‑in [Device Emulator](/docs/en-us/studio/testing-modes#device-emulation)  and [Controller Emulator](/docs/en-us/studio/testing-modes#controller-emulation)  to emulate various devices and gamepads directly in Studio.

-

Roblox's [UI styling](/docs/en-us/ui/styling)  pipeline, similar to CSS, lets you declare and globally apply overrides to UI instance properties. Along with the integrated [Style Editor](/docs/en-us/ui/styling/editor) , you can set up a complete and easy‑to‑modify user interface.

-

Once your game is effectively cross-platform, explore native features like haptic feedback on [mobile](/docs/en-us/input/mobile#haptic-feedback)  and [gamepads](/docs/en-us/input/gamepad#haptic-feedback) , touch gestures such as [TouchSwipe](/docs/en-us/reference/engine/classes/UserInputService#TouchSwipe)  and [TouchPinch](/docs/en-us/reference/engine/classes/UserInputService#TouchPinch) , or accelerometer and gyroscope functionality on [AccelerometerEnabled](/docs/en-us/reference/engine/classes/UserInputService#AccelerometerEnabled)  and [GyroscopeEnabled](/docs/en-us/reference/engine/classes/UserInputService#GyroscopeEnabled)  devices.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
