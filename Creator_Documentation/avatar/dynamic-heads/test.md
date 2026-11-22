<!-- Source: https://create.roblox.com/docs/en-us/avatar/dynamic-heads/test -->

Test dynamic heads in Studio | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar/dynamic-heads/test.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. Animations
6. /
7. Dynamic heads

# Test dynamic heads in Studio

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar/dynamic-heads/test.md)

If you are looking to quickly test a character's head animation, use [Avatar Setup](/docs/en-us/avatar-setup)  to load your character and use the presets to preview various facial animations and head accessories.

Manually test your dynamic head creations by importing character models with dynamic heads into Studio and using the generated [FaceControls](/docs/en-us/reference/engine/classes/FaceControls)  instance to pose or animate the face.

When importing a dynamic head into Studio, Studio creates a [FaceControls](/docs/en-us/reference/engine/classes/FaceControls)  instance you can use to access and combine these individual poses to create expressions and animations. Unlike typical rigged models, you cannot access the facial [Bones](/docs/en-us/reference/engine/classes/Bone)  of a head mesh directly in Studio.

To set up dynamic heads with facial animation data in your game:

1.

[Import a model with a dynamic head](/docs/en-us/avatar/character-bodies/import) . You can either create your own or use one of the provided reference model files.

2.

OPTIONAL

 [Import face accessories](#import-face-accessories)  you want to deform with the facial expressions of your head. You can either create your own or use one of the provided reference accessory files.

3.

[Animate the head](#animate-heads)  in the Animation Editor  by either adding in individual animation tracks or by using the Face Animation Editor .

If you want to experiment with pre-made dynamic heads before [making your own](/docs/en-us/art/characters/facial-animation/create-basic-heads) , Roblox provides a reference game for you to see how dynamic heads interact with Studio's interface, as well as two reference models and accessories you can import directly into your own game:

| Reference files | | Description |
| --- | --- |
| [Head Animation In-Game Editor](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/reference-files/Dynamic-Head-Editor.rbxl) | | A reference game that allows you to preview a Goblin and Blocky head with various accessories using an editor. |
| [Head Schema Reference](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/reference-files/Dynamic-Head-Schema.rbxl) | | A reference game with a head Blocky model with [FaceControls](/docs/en-us/reference/engine/classes/FaceControls) . |
| [Goblin Character Model](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/reference-files/GoblinCharacter.zip) | | A Goblin character model with a dynamic head. |
| [Blocky Character Model](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/reference-files/BlockyCharacter.fbx) | | A Blocky character model with a dynamic head. |
| [Blocky Face Accessories and Clothing](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/reference-files/Blocky-Face-Accessories.zip) | | A .zip  file of Blocky-specific accessories, including:
-

Angled Eyebrows

-

Round Eyebrows

-

Straight Eyebrows

-

Long Eyelashes

-

Short Eyelashes

-

Long Ducktail Beard

-

Mutton Chops Beard and Hair

-

Shirt and Pants

 |

## [Import face accessories](#import-face-accessories)[](#import-face-accessories)

You can import and equip face accessories that you want to deform with the facial expressions of your dynamic head. For example, when you import and equip eyebrows as a face accessory, you can animate the eyebrows to move with the character's eyes.

When you import a face accessory, it imports as a [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  object by default. Using the [Accessory Fitting Tool](/docs/en-us/avatar/accessory-fitting-tool)  (AFT), you can convert the [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  into an [Accessory](/docs/en-us/reference/engine/classes/Accessory)  instance that is compatible with the dynamic head.

To import a face accessory:

1.

From Studio's File  menu, use the [Importer](/docs/en-us/studio/importer)  to import the custom model into the workspace.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/using-dynamic-heads-in-studio/Importing-Facial-Accessory-Final-Result.jpg)

2.

Using the AFT, convert the [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  into an [Accessory](/docs/en-us/reference/engine/classes/Accessory)  instance.

1.

In the toolbar's Avatar  tab, click Accessory  to open the AFT.

2.

In the Explorer  window, select the MeshPart  you imported as a face accessory. Its name displays in the Part  field.

3.

Click the Next  button.

4.

In the Clothing  category, select Face , then click the Next  button.

5.

OPTIONAL

 In the Edit  panel, use the adjustment options to ensure the accessory fits your model.

6.

In the Preview  panel, preview the new facial accessory on your head, then click the Next  button. The tool transforms the [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  into an [Accessory](/docs/en-us/reference/engine/classes/Accessory)  instance, and it displays in the Explorer  window.

You can preview the accessory on your imported model by making the [Accessory](/docs/en-us/reference/engine/classes/Accessory)  instance a child of your character [Model](/docs/en-us/reference/engine/classes/Model) . You can only equip character-specific face accessories with their designed character.

![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/using-dynamic-heads-in-studio/Facial-Accessory-In-Viewport.jpg) Equipped accessory in viewport

![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/using-dynamic-heads-in-studio/Facial-Accessory-In-Property-Panel.jpg) Equipped Accessory in Explorer

You can also save the [Accessory](/docs/en-us/reference/engine/classes/Accessory)  instance to your toolbox and use the asset ID at any time in your games. For information on equipping accessories by applying a [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription) , see [Customize characters with humanoid description](/docs/en-us/characters/appearance#set-multiple-accessories) .

### [AutoSkin property](#autoskin-property)[](#autoskin-property)

You can enable the [WrapLayer.AutoSkin](/docs/en-us/reference/engine/classes/WrapLayer#AutoSkin)  property in the accessory's [WrapLayer](/docs/en-us/reference/engine/classes/WrapLayer)  instance to apply the skinning of the head to the face accessory. This allows a face accessory to fit and follow a character's expressions without having to apply any skinning influences to it during the 3D modeling process.

The following options are available for the [WrapLayer.AutoSkin](/docs/en-us/reference/engine/classes/WrapLayer#AutoSkin)  property:

-

Disabled : Disables the Automatic Skinning Transfer process. This is the default value.

-

EnabledOverride : Enables the Auto-Skin Transfer process and allows Studio to override any existing skinning information found on the accessory. Choose this setting when you want to set or replace the existing skinning of an accessory using the Auto-Skin Transfer version.

-

EnabledPreserve : Enables the Automatic Skinning Transfer process but doesn't  allow it to override any existing skinning information found on the accessory. Choose this setting when you want to preserve and maintain any existing skinning of an accessory. If there isn't any skinning to maintain, the Auto-Skin Transfer creates new skinning automatically.

## [Animate heads](#animate-heads)[](#animate-heads)

Dynamic head [MeshParts](/docs/en-us/reference/engine/classes/MeshPart)  include a [FaceControls](/docs/en-us/reference/engine/classes/FaceControls)  instance that allows you to access your facial pose properties.

![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/using-dynamic-heads-in-studio/FaceControls-In-Explorer.jpg) FaceControls in Explorer

![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/using-dynamic-heads-in-studio/FaceControls-In-Property-Panel.jpg) FaceControls Property Panel

You can adjust these properties in the Animation Editor  to animate your head. For more information, see [Animate heads](/docs/en-us/art/characters/facial-animation/animate-heads) .

## [Troubleshooting](#troubleshooting)[](#troubleshooting)

When importing custom head models, the [Output window](/docs/en-us/studio/output)  displays an error or warning message if there were any issues during the configuration process.

### [Error messages](#error-messages)[](#error-messages)

Error messages indicate a failure to properly import a model with a head. Reference the following table for a summary of all head error messages and troubleshooting tips:

| Error message | | Troubleshooting |
| Failed importing head with facial animation. | | The .fbx  file is corrupted. |
| Found more than one joint named X. All joints must have unique names. | | Ensure that every joint that you import has a unique name. |
| Failed importing head with facial animation: Correctives can be for at most 3 control names. | | Studio found a corrective with more than 3 corrective poses. This isn't supported, so you need to delete the corrective. |
| Failed importing head with facial animation: Unrecognized FACS control name X. | | X is an unrecognized FACS pose name. Ensure that X is renamed to one of the [standard FACS poses](/docs/en-us/avatar/dynamic-heads/facs-poses-reference) . |
| Failed importing head with facial animation: Invalid corrective name X: Neutral cannot be part of a corrective. | | X is an invalid corrective name. Ensure you are following the correct naming format for correctives. |
| Failed importing head with facial animation: Found duplicate FACS control name X for corrective Y. | | X is an invalid corrective name. You can only include a base pose that is listed as part of a corrective once in the corrective name. |
| Failed importing head with facial animation: Couldn't parse the frame number in Extra Attribute named X. | | You must name any extra attributes "Frame0", "Frame1", etc. |
| Failed importing head with facial animation: Empty value found for Extra Attribute named X. | | The extra attribute X has no value. Add a base pose name or corrective, or delete the extra attribute. |
| Failed importing head with facial animation: Duplicate control name found. | | You set a FACS pose or corrective to multiple frames. Ensure that each FACS pose or corrective is set to only a single frame. |
| Failed importing head with facial animation: Head_Geo has no Extra Attributes that map FACS controls to animation frames. | | The "Head_Geo" mesh in the FBX file must have extra attributes in order to animate facial expressions. The imported avatar will not animate facial expressions. |
| Failed importing head with facial animation: No frame was set to "Neutral" in animation. | | Must have one frame set to "Neutral" in the animation timeline. |
| Failed importing head with facial animation: X has not been specified. This is needed for corrective Y. | | All base poses for a corrective must be set in the extra attributes. For example, if the Funneler_JawDrop  corrective is set, then there ** must**  be poses for Funneler  and JawDrop  alone. |
| Failed importing head with facial animation: Missing key frame X for Y. | | There is an extra attribute "FrameX" set to Y, but the animation timeline has no frame X. |
| Failed importing head with facial animation: No joints were found under DynamicHead. | | The .fbx  file doesn't have any joints under the RootFaceJoint joint. |
| Could not load FACS control data. | | There are corrupted joint parameters in the .fbx  file. |

### [Warning messages](#warning-messages)[](#warning-messages)

Warning messages indicate a potential issue with an imported head model. Reference the following table for a summary of all head warning messages and troubleshooting tips:

| Error message | | Troubleshooting |
| You have corrective X, but missing corrective Y to support it. This may cause odd deformations. | | You set a 3-corrective without setting the base 2-corrective. The imported head will animate, but there might be strange deformations. |
| Skipping attribute X: Y | | Studio found an extra attribute named X, but since it didn't match the format of "Frame#", it was ignored. |
| Control X is nearly identical to Neutral. | | The pose for X is very similar to Neutral. Studio reports this in case this was a mistake, but the import will be successful as long as there are no other failures. |
| Found only N base poses. Your character may not be able to express itself. | | You only defined a subset of base poses in the .fbx  file. The import will still be successful as long as there are no other failures. |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
