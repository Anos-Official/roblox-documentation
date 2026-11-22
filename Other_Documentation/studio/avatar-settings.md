<!-- Source: https://create.roblox.com/docs/studio/avatar-settings -->

Avatar Settings | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/studio/avatar-settings.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Studio](/docs/en-us/studio)

# Avatar Settings

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/studio/avatar-settings.md)

The Avatar Settings  window, accessible from Studio's File  menu or the Avatar  tab, allows you to control the look and behavior of user avatars across your entire game.

 ![Avatar Settings indicated in Studio's toolbar](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Avatar-Settings.png)  ![Avatar Settings window layout](https://prod.docsiteassets.roblox.com/assets/studio/general/Avatar-Settings-Window.png)

Avatar Settings  modifies underlying game defaults that are not visible outside of the settings interface or accessible with scripts. This can lead to difficult-to-debug behaviors, especially when working across teams or on a universe with multiple place files. Test your changes by using the window's preview and by playtesting in Studio so that you fully understand the impact on player avatars before publishing changes to your live game.

The top bar of the Avatar Settings  window provides easy access to quickly set the avatar type, assign a preset, and enable preview.

| Setting | | Description |
| --- | --- |
| Preset | | Displays which settings preset is enabled and allows you to toggle between them (for descriptions of each setting, see [General](#general) ). If the preset displays -- , this indicates that the current settings are customized and do not match a preset. |
| Preview | | Toggles a preview lineup of avatars based off the avatar settings applied and creates an AvatarPreview  folder under [Workspace](/docs/reference/engine/classes/Workspace)  ⟩ [Camera](/docs/reference/engine/classes/Camera)  with four representative avatar types. You can add or remove avatars to the lineup by dragging them into or out of the folder. The folder is removed during Studio runtime playtesting and it is not saved to your place file. |
| ⋯ | | Sets player characters to R6 Only , R15 Only , or R15 and R6 . To convert a game from R6 Only  to R15 Only , see [Convert games from R6 Only to R15 Only](/docs/characters/r6-only-to-r15-only) . |

## [General](#general)[](#general)

The General  tab offers simple presets tailored to the needs of most games. In many cases, one of these presets will fit your game's avatar use-cases and additional configuration is not necessary. However, advanced developers can further customize avatar behavior using the more detailed settings available in the other tabs.

| Setting | | Description |
| Player Choice | | Loads player avatars without any modifications. |
| Consistent Gameplay | | Sets all avatars to the same height with the same box collider for consistent collision behavior. |

## [Body](#body)[](#body)

The Body  tab contains settings for body proportions, parts, scale.

| Setting | | Description |
| Scale | |
-

Player Choice  (default): Does not modify avatar character scale.

-

Custom Scale : Allows you to scale avatars to an absolute height in studs, but maintain their proportions. You can set a Minimum  and Maximum  range.

For reference, classic style avatars are around 5 studs tall. More humanoid style proportions are around 6 to 6.5 studs.

 |
| Appearance | |
-

Player Choice  (default): Does not modify avatar character appearance.

-

Custom Parts : Lets you override a user's default body part to a custom ID.

 |
| Build | |
-

Player Choice  (default): Does not modify avatar character proportions.

-

Custom Build : Provides customization options that limits the user's avatar body type, height, width, head size, and proportions.

 |

## [Clothing](#clothing)[](#clothing)

The Clothing  tab contains controls for layered and classic clothing.

| Setting | | Description |
| Clothing Scale | |
-

Player Choice  (default): Keep user's avatar clothing.

-

Custom Limit : Remove any clothing that exceeds the limit bounds of the avatar.

-

Limit Bounds : The amount of length, width, and depth padding beyond the avatar body’s bounding box, expressed as a percentage. This limit is shown as a blue box around each avatar in the preview lineup.
0% means no padding and items must be strictly within the bounding box of the body and 100% adds padding equal to the avatar's bounding box on all sides, allowing items to occupy up to three times the body size.

 |
| Custom Clothing | |
-

Player Choice  (default): Keep user's avatar clothing.

-

Custom Clothing : Lets you override a user's layered accessory equip slot or classic clothing type to a custom ID. If you check the box to override, but leave the Asset ID  field blank, it will remove all player clothing in that equip slot.

 |

## [Accessories](#accessories)[](#accessories)

The Accessories  tab contains settings related to accessories in your game.

| Setting | | Description |
| Accessory Scale | |
-

Player Choice  (default): Does not change the scale of user's equipped accessories.

-

Custom Limit : Allows you to Scale  accessories, or Remove  accessories that exceed limit bounds.

-

Limit Method : Allows you to Scale  accessories to fit within limit bounds, or Remove  accessories that exceed limit bounds.

-

Limit Bounds : The amount of length, width, and depth padding beyond the avatar body's bounding box, expressed as a percentage. The limit bounds are visualized as a blue box around each avatar in the preview lineup.
0% means no padding and items must be strictly within the bounding box of the body and 100% means pad by 100% of the bounding box on each side, so items can occupy an area three times the size of the body.

 |
| Custom Accessories | |
-

Player Choice  (default): Keep user's avatar accessories.

-

Custom Accessories : Lets you override a user's accessory types to a custom ID. If you check the box to override, but leave the Asset ID field blank, it will remove all player accessories of that category.

 |
| Accessory Behaviors | | Controls to enable/disable accessory behaviors like VFX , Sound , and Emissives . |

## [Movement](#movement)[](#movement)

The Movement  tab contains collision and animation settings, as well as ability configurations for the [Character Controller Library](/docs/characters/character-controller-library) .

| Setting | | Description |
| Collision | |
-

Default : Use the [OuterBox](/docs/reference/engine/enums/R15CollisionType#OuterBox)  method which calculates collisions based off the bounding boxes of avatar parts.

-

Single Collider : Use a single consistently sized box for collisions.

-

Size : Set the length, width, and depth of the collider box.

-

Hit & Touch Detection : Set hit and touch events to use avatar parts  or colliders .

-

Legacy : Use the [InnerBox](/docs/reference/engine/enums/R15CollisionType#InnerBox)  collision method (for backwards compatibility only).

 |
| Animation Packs | |
-

Player Choice  (default): Keep user's platform animation style, including style packs

-

Standard R15 : All avatars will use the standard R15 platform animations.

-

Standard R6 : All avatars will use the standard R6 platform animations.

 |
| Animation Clips | |
-

Player Choice  (default): Keep user's platform animations.

-

Custom Clips : Lets you override and preview any default animation type with a custom ID. These overrides are applied on top of your selection of Animation Pack .

 |
| Abilities | |
-

Legacy Humanoid  (default): Use legacy character abilities built on rigid [Humanoid](/docs/reference/engine/classes/Humanoid)  state machines.

-

Character Controller Library : Enables the [Character Controller Library](/docs/characters/character-controller-library)  and lets you toggle on/off default character abilities at runtime.

 |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
