<!-- Source: https://create.roblox.com/docs/avatar -->

Avatar, a system of expression | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Avatar](/docs/en-us/avatar)

# Avatar, a system of expression

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar/index.md)

Every Roblox user is represented by an avatar  — a fully customizable 3D character with cosmetics, clothing, and accessories that persist across games on the platform. At their core, avatars are deeply personal because they symbolize one's digital identity, uniquely crafted by individual purchases on the [Marketplace](https://www.roblox.com/catalog)  or in games, or from giveaways.

Each avatar is a system of components that work together to create a character that can interact with objects in the 3D space and wear cosmetics, clothing, and accessories. Broadly speaking, you can separate these components into those that make up who you are  and what you wear . Let's break it down.

## [Who you are](#who-you-are)[](#who-you-are)

There are four main layers of the avatar body that structure how the character looks and moves on the platform:

[Geometry](#geometry)
The avatar's visual appearance.

[Rigging armature](#rigging-armature)
How the avatar moves.

[Animations](#animations)
How the avatar expresses their personality.

[Attachment points and cage meshes](#attachment-points-and-cage-meshes)
How the avatar attaches accessories and wears clothing.

While you can create each of these layers manually, some have strict configuration requirements to meet Roblox's technical [character specifications](/docs/avatar/character-bodies/specifications)  that guarantee your avatar behaves consistently from game to game. To assist your creative process and ensure your avatars meet these specifications, Roblox provides the following:

-

[Avatar Setup](/docs/avatar-setup)  - Automatically processes 3D custom assets into avatar assets with all essential components for publishing to the Marketplace.

-

[Avatar references](/docs/avatar/resources#references)  with geometry and rigging armatures.

-

[Project files](/docs/avatar/resources#project-files)  for base rigs, attachment points, and cage meshes you can use in third-party modeling software.

-

[Mannequins](/docs/avatar/resources#mannequin-models)  you can use as a sizing reference.

-

[Customizable character templates](/docs/avatar/resources#templates)  with pre-baked avatar components.

### [Geometry](#geometry)[](#geometry)

The avatar's [physical body](/docs/avatar/character-bodies)  geometry is made up of 15 separate mesh body parts that define the shape and contours of the character:

-

Head

-

Upper and lower torso

-

Left upper arm, lower arm, and hand

-

Right upper arm, lower arm, and hand

-

Left upper leg, lower leg, and foot

-

Right upper leg, lower leg, and foot

When users purchase an avatar body, they can either equip it as a set or mix-and-match individual body parts from other purchases.

In Studio, these body parts are represented as [MeshPart](/docs/reference/engine/classes/MeshPart)  objects and are nested under a single [Model](/docs/reference/engine/classes/Model) .

[Create your first avatar body](/docs/art/characters/creating/modeling-best-practices)

![Avatar body geometry](https://prod.docsiteassets.roblox.com/assets/avatar-anatomy/static-sections/geometry.png)

### [Rigging armature](#rigging-armature)[](#rigging-armature)

Inside of the avatar's physical body is a non-rendered [rigging armature](/docs/avatar/character-bodies/specifications#rigging)  that allows the character to articulate its limbs. Often referred to as joints or bones, rigging armature includes skinning data that allows connections between limbs to bend organically, such as the character's knees and elbows.

Standard avatar rigs  require 15 poseable joints to articulate the character's 15 body parts. However, if you want to create higher-fidelity characters with a greater level of realism, there are up to 37 additional optional joints for advanced R15 rigs  that you can create for articulated hands, shoulders, and spine movements. Each joint must follow a specific hierarchy and naming convention for the avatar to function properly in Studio and on the Marketplace.

If your avatar's geometry doesn't have a rigging armature, Roblox provides [Avatar Setup](/docs/avatar-setup) , a tool that automatically generates a Marketplace-ready rig to the character's body model to enable movement and animation.

In Studio, each joint of the rigging armature is represented by [Bone](/docs/reference/engine/classes/Bone)  objects that connect the character's [MeshPart](/docs/reference/engine/classes/MeshPart)  objects together.

[Create your first character rig on an existing model](/docs/art/accessories/rig-and-cage-existing-models)

![Avatar rigging armature](https://prod.docsiteassets.roblox.com/assets/avatar-anatomy/static-sections/rigging.png)

### [Animations](#animations)[](#animations)

Using the avatar's rigging armature or face bones with [Facial Action Coding System](/docs/avatar/dynamic-heads/facs-poses-reference)  (FACS) data, you can create poses and interpolate between them to create the following types of custom animations:

-

Emotes  - [Full body animations](/docs/avatar/emotes)  that players purchase from the Marketplace to communicate and celebrate with others in a game, such as gestures, reactions, and dances.

-

Facial expressions  - [Facial animations](/docs/art/characters/facial-animation/animate-heads)  with the character's eyes, mouth, and teeth that players use to express emotions.

Roblox provides the following tooling to make the avatar animation process easier:

-

[Avatar Setup](/docs/avatar-setup)  - Automatically generate FACS poses, facial rigging, skinning, and animation data required for facial animation and avatar chat.

-

[Adaptive Animation](/docs/characters/adaptive-animation)  - Customize, modify, and map joints so that animations can play seamlessly between characters with unique body types, rigging armatures, and proportions.

-

[Animation Editor](/docs/animation/editor)  - Manually animate the rig by creating poses on different keyframes.

-

[Animation Capture](/docs/animation/capture)  - Record or upload video content to capture movement and expressions as keyframes.

-

[Face Animation Editor](/docs/art/characters/facial-animation/animate-heads#use-the-face-animation-editor)  - Use facial sliders to automatically create keyframes as you adjust sliders for different facial features.

In Studio, each emote is represented by an [Animation](/docs/reference/engine/classes/Animation)  object with its [AnimationId](/docs/reference/engine/classes/Animation#AnimationId)  property set to the assetID of your animation sequence, and FACS values map directly to a dynamic head's [FaceControls](/docs/reference/engine/classes/FaceControls)  object values.

[Create your first full body animation](/docs/tutorials/use-case-tutorials/animation/create-an-animation)[Create your first dynamic head](/docs/art/characters/facial-animation/create-basic-heads)

![Avatar body geometry](https://prod.docsiteassets.roblox.com/assets/avatar-anatomy/static-sections/geometry.png)

Walk animation Shrug emote Floss dance emote Facial expressions

Select an option to preview

### [Attachment points and cage meshes](#attachment-points-and-cage-meshes)[](#attachment-points-and-cage-meshes)

Outside of the avatar's physical body are two types of non-rendered components that allow the character to attach accessories to the body and wear clothing:

-

Attachment points  - Sets the specific points where accessories and in-game equipable objects attach to the character's body.

-

Cage meshes  - Sets the outer boundary for clothing to stretch and fit over the character's body.

If your avatar's geometry doesn't have attachment points or cage meshes, Roblox provides [Avatar Setup](/docs/avatar-setup) , a tool that automatically adds the required attachment points and cage meshes to your avatar. In addition, there are downloadable Blender, Maya, and .fbx  [project files](/docs/avatar/resources#project-files)  you can use to ensure you're using standard attachment points and cage meshes for humanoid bodies.

In Studio, outer cage mesh objects are represented by a [WrapTarget](/docs/reference/engine/classes/WrapTarget)  object, and attachment points are represented as [Attachment](/docs/reference/engine/classes/Attachment)  objects.

[Edit your first cage meshes on an existing model](/docs/art/accessories/rig-and-cage-existing-models)

![Avatar cage meshes and attachment points](https://prod.docsiteassets.roblox.com/assets/avatar-anatomy/static-sections/cages-attachments.png)

## [What you wear](#what-you-wear)[](#what-you-wear)

There are four main layers of what avatars can wear to express their unique style:

[Makeup](#makeup)
2D cosmetic items you can apply to the character's face.

[Rigid accessories](#rigid-accessories)
3D cosmetic items that attach on the character's body, such as hats, weapons, and props.

[Layered accessories](#layered-accessories)
3D cosmetic items that stretch and fit over the character's body, such as pants, t-shirts, and jackets.

[Classic clothing](#classic-clothing)
2D cosmetic images that wrap around the character's body.

Each of these layers have strict requirements so that users can equip these items to characters of various shapes and sizes.

### [Makeup](#makeup)[](#makeup)

[Makeup](/docs/avatar/makeup)  is a facial cosmetic item for additional creative expression, such as face paint, battle markings, camouflage, and traditional makeup art like eyeshadow, lipstick, and blush. Users can purchase makeup as a set on the Marketplace and apply it as a complete cohesive look, or swap out individual makeup components for others that match their own avatar's style.

Roblox provides [makeup templates](/docs/avatar/makeup#resources)  that you can use within your creation process, such as:

-

Template textures that you can use in 2D editing software to author makeup.

-

Template heads that you can use to view and test your makeup before export.

-

A reference experience you can use to import and test your makeup assets on characters with different skin tones and body types.

You can either use these templates as a pure reference to see how everything works, or you can use all of them at each step of your creation process.

In Studio, makeup is made up of multiple specialized texture layers baked into a [Decal](/docs/reference/engine/classes/Decal)  object, and each texture layer contains a unique makeup component like the lips or eyes region.

[Create your first makeup look](/docs/avatar/makeup)

![Avatar without makeup](https://prod.docsiteassets.roblox.com/assets/avatar-anatomy/makeup/no-makeup.png)

Eyes Face Lips

Toggle Eyes, Face, Lips to preview

### [Rigid accessories](#rigid-accessories)[](#rigid-accessories)

[Rigid accessories](/docs/avatar/rigid-accessories)  attach to the avatar according to the attachment points around the character's body. When users purchase rigid accessories on the Marketplace, they can adjust the position and rotation of the item away from the attachment point according to their avatar's body type.

Roblox provides a [step-by-step tutorial](/docs/art/accessories/creating-rigid)  on how to convert your custom 3D models into rigid accessories, as well as the [Accessory Fitting Tool](/docs/avatar/accessory-fitting-tool)  in Studio to test and edit your custom 3D models on multiple combinations of character bodies, animations, and accessories.

In Studio, rigid accessories are represented as [Accessory](/docs/reference/engine/classes/Accessory)  objects.

[Create your first rigid accessory](/docs/art/accessories/creating-rigid)

![Avatar without rigid accessories](https://prod.docsiteassets.roblox.com/assets/avatar-anatomy/rigid-accessories/no-accessories.png)

Back Neck Waist

Toggle Back, Neck, Waist to preview

### [Layered accessories](#layered-accessories)[](#layered-accessories)

[Layered accessories](/docs/avatar/layered-accessories) , often referred to as layered clothing, stretch and fit on the avatar according to their rigging armature and cage meshes. When users purchase layered accessories on the Marketplace, they expect it to move with the character's animations and layer appropriately on top of existing clothing the character is wearing.

Roblox provides a [step-by-step tutorial](/docs/art/accessories/creating)  on how to create a Studio-ready layered t-shirt in Blender, as well as the [Accessory Fitting Tool](/docs/avatar/accessory-fitting-tool)  in Studio to test and edit your custom 3D models on multiple combinations of character bodies, animations, and accessories.

In Studio, layered accessories are represented as [Accessory](/docs/reference/engine/classes/Accessory)  objects with a child [WrapLayer](/docs/reference/engine/classes/WrapLayer)  object.

[Create your first layered accessory](/docs/art/accessories/creating)

![Avatar without layered accessories](https://prod.docsiteassets.roblox.com/assets/avatar-anatomy/layered-accessories/no-clothing.png)

Jacket 1 Jacket 2 Jacket 3 Jacket 4

Select an option to preview

### [Classic clothing](#classic-clothing)[](#classic-clothing)

[Classic clothing](/docs/avatar/classic-clothing)  wraps around specific areas of the avatar's body, such as their front torso for t-shirts or their torso and legs for pants. This is the most basic type of avatar item to sell on Roblox as you just need an image editor and web browser for the creation process.

Roblox provides a [step-by-step video tutorial](https://www.youtube.com/watch?v=r_unfGZT5Ps)  on how to create a Studio-ready classic t-shirt using GNU Image Manipulation Program (GIMP), a free, third-party image editor.

In Studio, classic clothing is represented as [ShirtGraphic](/docs/reference/engine/classes/ShirtGraphic)  objects for t-shirts, [Shirt](/docs/reference/engine/classes/Shirt)  objects for shirts, and [Pants](/docs/reference/engine/classes/Pants)  objects for pants.

[Create your first classic clothing item](/docs/avatar/classic-clothing)

![Avatar without classic clothing](https://prod.docsiteassets.roblox.com/assets/avatar-anatomy/classic-clothing/no-clothes.png)

Pants Shirt

Toggle Pants, Shirt to preview

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
