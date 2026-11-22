<!-- Source: https://create.roblox.com/docs/en-us/avatar/dynamic-heads/facs-poses-reference -->

FACS poses reference | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar/dynamic-heads/facs-poses-reference.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Avatar](/docs/en-us/avatar)
4. /
5. Animations
6. /
7. Dynamic heads

# FACS poses reference

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar/dynamic-heads/facs-poses-reference.md)

The [Facial Action Coding System](https://en.wikipedia.org/wiki/Facial_Action_Coding_System)  (FACS) is a comprehensive, anatomically-based system for describing all visually discernible facial movement. This system breaks down all facial expressions into individual types of muscle movement, such as LeftEyeClosed  or MouthLeft . You can [configure](/docs/en-us/art/characters/facial-animation/create-basic-heads#pose-the-joints)  and store these muscle movements, or poses , within the head model through a third-party modeling software, such as [Blender](https://www.blender.org)  or [Maya](https://www.autodesk.com/products/maya/overview) . When you import the head model into Studio, you can then access and [animate](/docs/en-us/art/characters/facial-animation/animate-heads)  these poses to create lively facial expressions.

The following is a list of 50 base poses that you can use in Roblox to portray a wide range of face emotions. Except for the first neutral pose, the order of poses you save to your character model doesn't matter since this information is set during the [mapping](/docs/en-us/art/characters/facial-animation/create-basic-heads#map-each-pose)  process as a custom property.

If you intend to publish your avatar to the Marketplace, your avatar head must include the required [17 facial base poses](/docs/en-us/avatar/dynamic-heads/specifications#facs-poses) . Marketplace validation rejects assets that do not include these 17 required base poses.

You can combine multiple FACS base poses together in one animation frame to create complex facial expressions. However, some combinations of poses might collide unless you also add a [corrective](/docs/en-us/art/characters/facial-animation/create-basic-heads#combination-poses)  to their full default values.

## [LeftEyeClosed](#lefteyeclosed)[](#lefteyeclosed)

If publishing to the Marketplace, your avatar asset must include this pose.

[LeftEyeClosed](/docs/en-us/reference/engine/classes/FaceControls#LeftEyeClosed)  closes the character's left eyelid.

## [RightEyeClosed](#righteyeclosed)[](#righteyeclosed)

If publishing to the Marketplace, your avatar asset must include this pose.

[RightEyeClosed](/docs/en-us/reference/engine/classes/FaceControls#RightEyeClosed)  closes the character's right eyelid.

## [EyesLookDown](#eyeslookdown)[](#eyeslookdown)

If publishing to the Marketplace, your avatar asset must include this pose.

[EyesLookDown](/docs/en-us/reference/engine/classes/FaceControls#EyesLookDown)  makes the eyes gaze down.

## [JawDrop](#jawdrop)[](#jawdrop)

If publishing to the Marketplace, your avatar asset must include this pose.

[JawDrop](/docs/en-us/reference/engine/classes/FaceControls#JawDrop)  lowers the jaw downward, opening the mouth.

## [Pucker](#pucker)[](#pucker)

If publishing to the Marketplace, your avatar asset must include this pose.

[Pucker](/docs/en-us/reference/engine/classes/FaceControls#Pucker)  makes a kiss-like shape with the mouth.

## [LeftLipCornerPuller](#leftlipcornerpuller)[](#leftlipcornerpuller)

If publishing to the Marketplace, your avatar asset must include this pose.

[LeftLipCornerPuller](/docs/en-us/reference/engine/classes/FaceControls#LeftLipCornerPuller)  raises the corners of the mouth upwards in a smile.

## [RightLipCornerPuller](#rightlipcornerpuller)[](#rightlipcornerpuller)

If publishing to the Marketplace, your avatar asset must include this pose.

[RightLipCornerPuller](/docs/en-us/reference/engine/classes/FaceControls#RightLipCornerPuller)  raises the corners of the mouth upwards in a smile.

## [ChinRaiser](#chinraiser)[](#chinraiser)

If publishing to the Marketplace, your avatar asset must include this pose.

[ChinRaiser](/docs/en-us/reference/engine/classes/FaceControls#ChinRaiser)  raises the chin up; moves the lower lip upwards.

When you use [ChinRaiser](/docs/en-us/reference/engine/classes/FaceControls#ChinRaiser)  and the character's mouth is closed, the character's lower lip collides with their upper lip. When you need to keep the mouth closed while raising the chin, use [ChinRaiserUpperLip](#chinraiserupperlip)  and [ChinRaiser](/docs/en-us/reference/engine/classes/FaceControls#ChinRaiser)  together to raise both the lower and upper lip, and avoid a collision. Note that if you use this method, you must set both [ChinRaiser](/docs/en-us/reference/engine/classes/FaceControls#ChinRaiser)  and [ChinRaiserUpperLip](#chinraiserupperlip)  to the same value so the lips move the same distance upwards.

## [ChinRaiserUpperLip](#chinraiserupperlip)[](#chinraiserupperlip)

If publishing to the Marketplace, your avatar asset must include this pose.

[ChinRaiserUpperLip](/docs/en-us/reference/engine/classes/FaceControls#ChinRaiserUpperLip)  raises the upper lip up when ChinRaiser is engaged and it is touching the upper lip.

## [LeftCheekRaiser](#leftcheekraiser)[](#leftcheekraiser)

If publishing to the Marketplace, your avatar asset must include this pose.

[LeftCheekRaiser](/docs/en-us/reference/engine/classes/FaceControls#LeftCheekRaiser)  squints the character's left eye.

## [RightCheekRaiser](#rightcheekraiser)[](#rightcheekraiser)

If publishing to the Marketplace, your avatar asset must include this pose.

[RightCheekRaiser](/docs/en-us/reference/engine/classes/FaceControls#RightCheekRaiser)  squints the character's right eye.

## [LeftInnerBrowRaiser](#leftinnerbrowraiser)[](#leftinnerbrowraiser)

If publishing to the Marketplace, your avatar asset must include this pose.

[LeftInnerBrowRaiser](/docs/en-us/reference/engine/classes/FaceControls#LeftInnerBrowRaiser)  raises the interior half of the character's left brow upwards.

## [RightInnerBrowRaiser](#rightinnerbrowraiser)[](#rightinnerbrowraiser)

If publishing to the Marketplace, your avatar asset must include this pose.

[RightInnerBrowRaiser](/docs/en-us/reference/engine/classes/FaceControls#RightInnerBrowRaiser)  raises the interior half of the character's right brow upwards.

## [LeftLipCornerDown](#leftlipcornerdown)[](#leftlipcornerdown)

If publishing to the Marketplace, your avatar asset must include this pose.

[LeftLipCornerDown](/docs/en-us/reference/engine/classes/FaceControls#LeftLipCornerDown)  lowers the corners of the mouth downwards in a frown.

## [RightLipCornerDown](#rightlipcornerdown)[](#rightlipcornerdown)

If publishing to the Marketplace, your avatar asset must include this pose.

[RightLipCornerDown](/docs/en-us/reference/engine/classes/FaceControls#RightLipCornerDown)  lowers the corners of the mouth downwards in a frown.

## [LeftLowerLipDepressor](#leftlowerlipdepressor)[](#leftlowerlipdepressor)

If publishing to the Marketplace, your avatar asset must include this pose.

[LeftLowerLipDepressor](/docs/en-us/reference/engine/classes/FaceControls#LeftLowerLipDepressor)  lowers the lower lip downwards away from the upper lip, revealing the lower teeth.

## [RightLowerLipDepressor](#rightlowerlipdepressor)[](#rightlowerlipdepressor)

If publishing to the Marketplace, your avatar asset must include this pose.

[RightLowerLipDepressor](/docs/en-us/reference/engine/classes/FaceControls#RightLowerLipDepressor)  lowers the lower lip down away from the upper lip revealing the lower teeth.

## [EyesLookLeft](#eyeslookleft)[](#eyeslookleft)

[EyesLookLeft](/docs/en-us/reference/engine/classes/FaceControls#EyesLookLeft)  makes the eyes gaze left.

## [EyesLookRight](#eyeslookright)[](#eyeslookright)

[EyesLookRight](/docs/en-us/reference/engine/classes/FaceControls#EyesLookRight)  makes the eyes gaze right.

## [EyesLookUp](#eyeslookup)[](#eyeslookup)

[EyesLookUp](/docs/en-us/reference/engine/classes/FaceControls#EyesLookUp)  makes the eyes gaze up.

## [LeftLipStretcher](#leftlipstretcher)[](#leftlipstretcher)

[LeftLipStretcher](/docs/en-us/reference/engine/classes/FaceControls#LeftLipStretcher)  stretches the corners of the mouth apart.

## [LeftUpperLipRaiser](#leftupperlipraiser)[](#leftupperlipraiser)

[LeftUpperLipRaiser](/docs/en-us/reference/engine/classes/FaceControls#LeftUpperLipRaiser)  raises the character's left upper lip away from the lower lip revealing the upper teeth.

## [LipsTogether](#lipstogether)[](#lipstogether)

[LipsTogether](/docs/en-us/reference/engine/classes/FaceControls#LipsTogether)  brings the character's lips together. However, if the character's mouth is closed, their lips are already together and they collide.

This pose's main use case is in connection with the [JawDrop](#jawdrop)  property. If you set [JawDrop](#jawdrop)  and [LipsTogether](/docs/en-us/reference/engine/classes/FaceControls#LipsTogether)  to 100% of their default values, the character's lips stay together as the jaw drops.

In addition, if you set [JawDrop](#jawdrop)  to 100% of its default value, and ease [LipsTogether](/docs/en-us/reference/engine/classes/FaceControls#LipsTogether)  in and out of 100% of its default value, the character's lips open and close.

## [RightLipStretcher](#rightlipstretcher)[](#rightlipstretcher)

[RightLipStretcher](/docs/en-us/reference/engine/classes/FaceControls#RightLipStretcher)  stretches the corners of the mouth apart.

## [RightUpperLipRaiser](#rightupperlipraiser)[](#rightupperlipraiser)

[RightUpperLipRaiser](/docs/en-us/reference/engine/classes/FaceControls#RightUpperLipRaiser)  raises the right upper lip away from the lower lip, revealing the upper teeth.

## [FlatPucker](#flatpucker)[](#flatpucker)

[FlatPucker](/docs/en-us/reference/engine/classes/FaceControls#FlatPucker)  brings the corners of the mouth inward and presses the lips back against the teeth. This pose is also known as lip tightener.

## [Funneler](#funneler)[](#funneler)

[Funneler](/docs/en-us/reference/engine/classes/FaceControls#Funneler)  makes an 'O' shape with the mouth.

## [LowerLipSuck](#lowerlipsuck)[](#lowerlipsuck)

[LowerLipSuck](/docs/en-us/reference/engine/classes/FaceControls#LowerLipSuck)  rolls the lower lip up over the teeth.

## [LipPresser](#lippresser)[](#lippresser)

[LipPresser](/docs/en-us/reference/engine/classes/FaceControls#LipPresser)  presses the lips together.

## [MouthLeft](#mouthleft)[](#mouthleft)

[MouthLeft](/docs/en-us/reference/engine/classes/FaceControls#MouthLeft)  moves the mouth to the character's left. This property doesn't move the character's jaw, teeth, or tongue, only their mouth. If you want to move those additional facial features, use [JawLeft](#jawleft)  instead.

## [MouthRight](#mouthright)[](#mouthright)

[MouthRight](/docs/en-us/reference/engine/classes/FaceControls#MouthRight)  moves the mouth to the character's right. This property doesn't move the character's jaw, teeth, or tongue to the right, only their mouth. If you want to move those additional facial features, use [JawRight](#jawright)  instead.

## [UpperLipSuck](#upperlipsuck)[](#upperlipsuck)

[UpperLipSuck](/docs/en-us/reference/engine/classes/FaceControls#UpperLipSuck)  rolls the upper lip around the teeth.

## [LeftCheekPuff](#leftcheekpuff)[](#leftcheekpuff)

[LeftCheekPuff](/docs/en-us/reference/engine/classes/FaceControls#LeftCheekPuff)  puffs up the character's left cheek.

## [LeftDimpler](#leftdimpler)[](#leftdimpler)

[LeftDimpler](/docs/en-us/reference/engine/classes/FaceControls#LeftDimpler)  moves the corners of the left side of the mouth back toward the teeth.

## [RightCheekPuff](#rightcheekpuff)[](#rightcheekpuff)

[RightCheekPuff](/docs/en-us/reference/engine/classes/FaceControls#RightCheekPuff)  puffs up the character's right cheek.

## [RightDimpler](#rightdimpler)[](#rightdimpler)

[RightDimpler](/docs/en-us/reference/engine/classes/FaceControls#RightDimpler)  moves the corners of the right side of the mouth back toward the teeth.

## [JawLeft](#jawleft)[](#jawleft)

[JawLeft](/docs/en-us/reference/engine/classes/FaceControls#JawLeft)  moves the character's jaw, teeth, tongue, and lower lip to their left. If you just want to move the character's mouth to their left, use [MouthLeft](#mouthleft)  instead.

## [JawRight](#jawright)[](#jawright)

[JawRight](/docs/en-us/reference/engine/classes/FaceControls#JawRight)  moves the character's jaw, teeth, tongue, and lower lip to their right. If you just want to move the character's mouth to their right, use [MouthRight](#mouthright)  instead.

## [Corrugator](#corrugator)[](#corrugator)

[Corrugator](/docs/en-us/reference/engine/classes/FaceControls#Corrugator)  brings the left and right brows inward together.

## [LeftBrowLowerer](#leftbrowlowerer)[](#leftbrowlowerer)

[LeftBrowLowerer](/docs/en-us/reference/engine/classes/FaceControls#LeftBrowLowerer)  lowers the character's left brow down.

## [LeftOuterBrowRaiser](#leftouterbrowraiser)[](#leftouterbrowraiser)

[LeftOuterBrowRaiser](/docs/en-us/reference/engine/classes/FaceControls#LeftOuterBrowRaiser)  raises the outer part of the character's left brow upwards.

## [LeftNoseWrinkler](#leftnosewrinkler)[](#leftnosewrinkler)

[LeftNoseWrinkler](/docs/en-us/reference/engine/classes/FaceControls#LeftNoseWrinkler)  raises the character's left nostril, pulls the brow down slightly, and wrinkles the left side of the nose.

## [RightBrowLowerer](#rightbrowlowerer)[](#rightbrowlowerer)

[RightBrowLowerer](/docs/en-us/reference/engine/classes/FaceControls#RightBrowLowerer)  lowers the character's right brow down.

## [RightOuterBrowRaiser](#rightouterbrowraiser)[](#rightouterbrowraiser)

[RightOuterBrowRaiser](/docs/en-us/reference/engine/classes/FaceControls#RightOuterBrowRaiser)  raises the outer part of the character's right brow upwards.

## [RightNoseWrinkler](#rightnosewrinkler)[](#rightnosewrinkler)

[RightNoseWrinkler](/docs/en-us/reference/engine/classes/FaceControls#RightNoseWrinkler)  raises the character's right nostril, pulls the brow down slightly, and wrinkles the right side of the nose.

## [LeftEyeUpperLidRaiser](#lefteyeupperlidraiser)[](#lefteyeupperlidraiser)

[LeftEyeUpperLidRaiser](/docs/en-us/reference/engine/classes/FaceControls#LeftEyeUpperLidRaiser)  raises the character's left eyelid upwards to reveal more of the eye white above the iris.

## [RightEyeUpperLidRaiser](#righteyeupperlidraiser)[](#righteyeupperlidraiser)

[RightEyeUpperLidRaiser](/docs/en-us/reference/engine/classes/FaceControls#RightEyeUpperLidRaiser)  raises the character's right eyelid upwards to reveal more of the eye white above the iris.

## [TongueDown](#tonguedown)[](#tonguedown)

[TongueDown](/docs/en-us/reference/engine/classes/FaceControls#TongueDown)  bends the tongue down. This pose is only visible if you combine it with [TongueOut](#tongueout) , otherwise the tongue only bends down within the character's mouth.

## [TongueOut](#tongueout)[](#tongueout)

[TongueOut](/docs/en-us/reference/engine/classes/FaceControls#TongueOut)  sticks the tip of the tongue out of the mouth.

## [TongueUp](#tongueup)[](#tongueup)

[TongueUp](/docs/en-us/reference/engine/classes/FaceControls#TongueUp)  bends the tongue up. This pose is only visible if you combine it with [TongueOut](#tongueout) , otherwise the tongue only bends up within the character's mouth.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
