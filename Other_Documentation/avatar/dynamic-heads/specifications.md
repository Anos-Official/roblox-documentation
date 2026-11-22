<!-- Source: https://create.roblox.com/docs/avatar/dynamic-heads/specifications -->

Dynamic head specifications | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar/dynamic-heads/specifications.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. Animations
6. /
7. Dynamic heads

# Dynamic head specifications

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar/dynamic-heads/specifications.md)

Character body models with dynamic heads require a specific set of components and configuration standards so that the entire model works as expected across the platform, including universal support for head accessories and facial animation, and so that the characters can be sold on the Marketplace.

Before you start the export process, verify that your model meets the following modeling specifications and guidelines for proper Studio compatibility.

Validation for dynamic heads uses a specialized process that may require you to adjust your existing dynamic head asset. For more information, see [Dynamic head validation](/docs/avatar/dynamic-heads/validate) .

[Avatar Setup](/docs/avatar-setup)  automatically generates components for your avatar characters, including the head cage and facial animation  required for the Marketplace. You can save time by submitting character models without avatar components into Avatar Setup, then modifying the output. If necessary, you can download your output as a .gltf , then adjust the FACS or cage data in your third-party modeling tool.

For issues or feedback regarding Avatar Setup, submit a [bug report](https://devforum.roblox.com/c/bug-reports/10) .

## [Outer cage](#outer-cage)[](#outer-cage)

Like all avatar character [body parts](/docs/avatar/character-bodies/specifications#body-parts) , dynamic heads require an outer cage to ensure layered accessories work properly. In addition, dynamic head outer cages serve to establish facial landmarks  for the eyes and mouth of the face for the validation process.

For information on how to improve or resolve errors with your dynamic head's outer cage, see [Dynamic head caging best practices](/docs/avatar/dynamic-heads/caging-best-practices) .

### [Facial landmarks](#facial-landmarks)[](#facial-landmarks)

During validation, Roblox projects the cage eye/mouth regions to the base mesh to identify the eyes and mouth regions of your character head. Roblox expects the following 3 distinct landmarks in your cages:

-

Left eye landmark

-

Right eye landmark

-

Mouth landmark

Even for non-humanoid faces that don't include visual eyes or mouths, it's important to ensure that these landmarks still exist and can be projected over your base mesh. For more information on this process, see [Dynamic head validation](/docs/avatar/dynamic-heads/validate) .

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Cage-Landmark-A.png) Example face cage UV

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Cage-Landmark-B.png) Highlighted vertices of cage are used to track eyes/mouth on base mesh

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Cage-Landmark-C.png) Landmarks from cage applied to base mesh, used as an indicator for basic animation support during validation

The mouth landmark vertices are on the second loop  of vertices from the mouth opening. This precision can help prevent issues with [landmark validation](/docs/avatar/dynamic-heads/validate#step-2-landmark-projection) .

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Mouth-Vertices-Warning.png)

## [FACS poses](#facs-poses)[](#facs-poses)

Dynamic heads support facial animation and can include many different base poses to meet the needs of your character design. That being said, avatar character bodies require at least the following 17 [FACS poses](/docs/avatar/dynamic-heads/facs-poses-reference)  to support avatar chat:

-

LeftEyeClosed

-

RightEyeClosed

-

EyesLookDown

-

JawDrop

-

Pucker

-

LeftLipCornerPuller

-

RightLipCornerPuller

-

ChinRaiser

-

ChinRaiserUpperLip

-

LeftCheekRaiser

-

RightCheekRaiser

-

LeftInnerBrowRaiser

-

RightInnerBrowRaiser

-

LeftLipCornerDown

-

RightLipCornerDown

-

LeftLowerLipDepressor

-

RightLowerLipDepressor

While these 17 poses are a requirement, it's recommended to include as many facial poses as possible in your asset to improve expressiveness and facial animation fidelity for facial animations.

To pass the dynamic head [validation process](/docs/avatar/dynamic-heads/validate) , your character's head must successfully perform the following 5 facial actions. If the dynamic head can't deform at the points of the cage's [facial landmarks](#facial-landmarks)  for these actions, validation fails for the asset.

| Action Unit Test | | Non-Zero Control Values |
| --- | --- |
| Left eye blink | | LeftEyeClosed  = 1
EyesLookDown  = 1 |
| Right eye blink | | RightEyeClosed  = 1
EyesLookDown  = 1 |
| Mouth opens | | JawDrop  = 1 |
| Happy expression  | | Pucker  = 1
LeftLipCornerPuller  = 1
RightLipCornerPuller  = 1 |
| Sad expression | | ChinRaiser  = 1
ChinRaiserUpperLip  = 1
LeftCheekRaiser  = 0.85
RightCheekRaiser  = 0.85
LeftInnerBrowRaiser  = 1
RightInnerBrowRaiser  = 1
LeftLipCornerDown  = 1
RightLipCornerDown  = 1
LeftLowerLipDepressor  = 1
RightLowerLipDepressor  = 1 |

## [Marketplace requirements](#marketplace-requirements)[](#marketplace-requirements)

Along with the other technical requirements listed, your character bodies with dynamic heads must meet the following additional specifications before uploading them to the Marketplace to sell:

-

Ensure that your character bodies adhere to [Marketplace policies](/docs/marketplace/marketplace-policy) .

-

Whenever applicable, ensure that your character bodies adhere to Roblox's [custom mesh specifications](/docs/art/modeling/specifications)  and [character body specifications](/docs/avatar/character-bodies/specifications) .

-

Object [Material](/docs/reference/engine/classes/MeshPart#Material)  is set to Plastic .

-

Object [Transparency](/docs/reference/engine/classes/MeshPart#Transparency)  is set to 0 .

-

Object [VertexColor](/docs/reference/engine/classes/MeshPart#VertexColor)  is the default 1, 1, 1 .

-

If your character's head includes separate eyelash and eyebrow assets, you must add them to your character body model as [Accessory](/docs/reference/engine/classes/Accessory)  objects. For more information, see [Publish bodies with eyelashes and eyebrows](/docs/art/accessories/publish-eyebrows-eyelashes) .

-

Your [Model](/docs/reference/engine/classes/Model)  instance doesn't contain extraneous objects, like [Script](/docs/reference/engine/classes/Script)  or additional [Part](/docs/reference/engine/classes/Part)  instances.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
