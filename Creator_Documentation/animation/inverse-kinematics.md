<!-- Source: https://create.roblox.com/docs/en-us/animation/inverse-kinematics -->

Inverse Kinematics | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/animation/inverse-kinematics.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Animation](/docs/en-us/animation)
6. /
7. Create animations

# Inverse Kinematics

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/animation/inverse-kinematics.md)

[Inverse Kinematics](https://en.wikipedia.org/wiki/Inverse_kinematics)  (IK) is a common technique in computer animation to efficiently make characters move and interact realistically with their environment. The process of creating a realistic movement for a character often requires many iterations and minor adjustments of the various joints. With IK, you can pose and animate multiple character parts by posing or adjusting a single object.

This animation technique can provide solutions to the following examples:

Grab and pose a character's hand while automatically adjusting the related limbs, such as the wrist, elbow, and shoulder.

Make a character's feet interact realistically on different surfaces and slopes.

Grab and move a single target object to quickly create realistic interactions with your character and props.

## [IKControl](#ikcontrol)[](#ikcontrol)

You can use an [IKControl](/docs/en-us/reference/engine/classes/IKControl)  to procedurally add IK to your character rigs outside of the Animation Editor . Studio allows you to programmatically apply IK to all characters to create realistic movement and interactions in your game.

When adding an [IKControl](/docs/en-us/reference/engine/classes/IKControl) , set the [required properties](#required-properties)  correctly to avoid unexpected and unnatural animation results. As with all animation, [test your IKControls](#test-ikcontrols)  to ensure that you achieve the desired behavior.

### [Required properties](#required-properties)[](#required-properties)

When adding a [IKControl](/docs/en-us/reference/engine/classes/IKControl)  to your character's [Humanoid](/docs/en-us/reference/engine/classes/Humanoid)  or [AnimationController](/docs/en-us/reference/engine/classes/AnimationController) , you must set the following required properties to enable IK:

| Property | | Description |
| --- | --- |
| [Type](/docs/en-us/reference/engine/classes/IKControl#Type) | | Specifies the behavior type of the IK control. See [Enum.IKControlType](/docs/en-us/reference/engine/enums/IKControlType)  for the list of behavior options. Common behavior types are Position  or Transform . |
| [EndEffector](/docs/en-us/reference/engine/classes/IKControl#EndEffector) | | A [BasePart](/docs/en-us/reference/engine/classes/BasePart)  or [Bone](/docs/en-us/reference/engine/classes/Bone)  in your character rig that tracks toward the [Target](/docs/en-us/reference/engine/classes/IKControl#Target) . For example, you can set a LeftHand  bone as a [EndEffector](/docs/en-us/reference/engine/classes/IKControl#EndEffector)  to reach a doorknob object set as the [Target](/docs/en-us/reference/engine/classes/IKControl#Target) . |
| [Target](/docs/en-us/reference/engine/classes/IKControl#Target) | | The object the [EndEffector](/docs/en-us/reference/engine/classes/IKControl#EndEffector)  reaches or points toward. A [Target](/docs/en-us/reference/engine/classes/IKControl#Target)  can be any object with a world position. |
| [ChainRoot](/docs/en-us/reference/engine/classes/IKControl#ChainRoot) | | Defines the chain of [BaseParts](/docs/en-us/reference/engine/classes/BasePart)  or [Bones](/docs/en-us/reference/engine/classes/Bone)  that the [IKControl](/docs/en-us/reference/engine/classes/IKControl)  affects. All connected parts between the [ChainRoot](/docs/en-us/reference/engine/classes/IKControl#ChainRoot)  and the [EndEffector](/docs/en-us/reference/engine/classes/IKControl#EndEffector)  are affected by the [IKControl](/docs/en-us/reference/engine/classes/IKControl)  using the behavior type defined.
 For example, if your character's LeftHand  is set as the [Target](/docs/en-us/reference/engine/classes/IKControl#Target) , you can apply IK to the entire left arm by setting [ChainRoot](/docs/en-us/reference/engine/classes/IKControl#ChainRoot)  to the LeftUpperArm . To apply IK just to the parts below the elbow, set [ChainRoot](/docs/en-us/reference/engine/classes/IKControl#ChainRoot)  to the LeftLowerArm . |

### [Test IKControls](#test-ikcontrols)[](#test-ikcontrols)

You can add and edit [IKControl](/docs/en-us/reference/engine/classes/IKControl)  programmatically or directly through the Explorer . You can even add and make changes to [IKControl](/docs/en-us/reference/engine/classes/IKControl)  during a Play test to quickly check how various properties affect a character's movements.

To quickly test your [IKControl](/docs/en-us/reference/engine/classes/IKControl)  using an [Attachment](/docs/en-us/reference/engine/classes/Attachment)  as a target:

1.

From Studio's mezzanine, [initiate a playtest](/docs/en-us/studio/testing-modes#playtesting) .

2.

In the Explorer  window, navigate to Workspace  → your user's [Model](/docs/en-us/reference/engine/classes/Model) . This [Model](/docs/en-us/reference/engine/classes/Model)  instance is named as your current Roblox account.

3.

Click the ⊕  icon next to your character model's HumanoidRootPart  and add an Attachment .

 ![](https://prod.docsiteassets.roblox.com/assets/animation/inverse-kinematics/IK-Add-Attachment.png)

4.

Select the Attachment  and use the Move  tool to position the object in front of your character in the viewport.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/inverse-kinematics/IK-Move-Attachment.png)

5.

In the Explorer  window, select the ⊕  icon next to your character's [Humanoid](/docs/en-us/reference/engine/classes/Humanoid)  and add an IKControl .

 ![](https://prod.docsiteassets.roblox.com/assets/animation/inverse-kinematics/IK-Humanoid-Add.png)

6.

Select the [IKControl](/docs/en-us/reference/engine/classes/IKControl)  and set the following property values in the Properties  window:

1.

Type : Select Transform  from the dropdown.

2.

EndEffector : Select your model's LeftHand  [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  in the Explorer .

3.

Target : Select the newly created Attachment  object in the Explorer .

4.

ChainRoot : Select your model's LeftUpperArm  [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  in the Explorer .

![](https://prod.docsiteassets.roblox.com/assets/animation/inverse-kinematics/IK-IKControl-Property.png) IKControl Properties

![](https://prod.docsiteassets.roblox.com/assets/animation/inverse-kinematics/IK-Explorer-Humanoid.png) Explorer - Character Model

Your character's left arm should now reach for the target [Attachment](/docs/en-us/reference/engine/classes/Attachment) . You can experiment with moving the [Attachment](/docs/en-us/reference/engine/classes/Attachment)  or editing the [IKControl](/docs/en-us/reference/engine/classes/IKControl)  properties to achieve different results.

### [Add constraints](#add-constraints)[](#add-constraints)

You can use [Constraints](/docs/en-us/reference/engine/classes/Constraint)  to restrict how joints can move when reaching its target. Constraints can ensure joints like the elbows and knees bend naturally, or to make the mechanical joints rotate in a specific orientation.

![](https://prod.docsiteassets.roblox.com/assets/animation/inverse-kinematics/elbow-unnatural-pose.png) Elbow bending unnaturally

![](https://prod.docsiteassets.roblox.com/assets/animation/inverse-kinematics/elbow-natural-pose.png) Elbow bending correctly

To add constraints to your character using [IKControl](/docs/en-us/reference/engine/classes/IKControl) , your [IKControl](/docs/en-us/reference/engine/classes/IKControl)  and constraint must meet the following conditions:

-

The attachments referenced in the constraint's [Attachment0](/docs/en-us/reference/engine/classes/Constraint#Attachment0) /[Attachment1](/docs/en-us/reference/engine/classes/Constraint#Attachment1)  properties attaches to the same parts as the [Motor6D](/docs/en-us/reference/engine/classes/Motor6D)  [Part0](/docs/en-us/reference/engine/classes/Motor6D#Part0) /[Part1](/docs/en-us/reference/engine/classes/Motor6D#Part1) .

-

The relative positions of [Attachment0](/docs/en-us/reference/engine/classes/Constraint#Attachment0) /[Attachment1](/docs/en-us/reference/engine/classes/Constraint#Attachment1)  must equal the corresponding positions of the [Motor6D](/docs/en-us/reference/engine/classes/Motor6D)  [C0](/docs/en-us/reference/engine/classes/Motor6D#C0) /[C1](/docs/en-us/reference/engine/classes/Motor6D#C1)  CFrames.

-

The constraint and the IKControl share the same parent [Model](/docs/en-us/reference/engine/classes/Model) .

The following instructions describe the process of adding a [HingeConstraint](/docs/en-us/reference/engine/classes/HingeConstraint)  to restrict the rotation of a character's elbow and adding a [BallSocketConstraint](/docs/en-us/reference/engine/classes/BallSocketConstraint)  to the wrist to limit the rotation angle.

#### [Elbow](#elbow)[](#elbow)

Characters with [R15 rigs](/docs/en-us/avatar/character-bodies/specifications#rigging)  already include attachments in their joints that you can use to apply the elbow constraint. For the elbow, both the LeftUpperArm and the LeftLowerArm include a LeftElbowRigAttachment . Along with adding a constraint, you also need to add additional child attachments to each part's LeftElbowRigAttachment  to specify which axis the elbow can rotate about.

To add the [HingeConstraint](/docs/en-us/reference/engine/classes/HingeConstraint)  and child attachments:

1.

In the Explorer  window, locate your model's LeftLowerArm  and click the ⊕ button .

2.

Add a HingeConstraint  with the name LeftElbowConstraint .

3.

In the Explorer  window, navigate to the LeftUpperArm.LeftElbowRigAttachment  and add an attachment:

1.

Click the ⊕ button  to add an Attachment  with the name LeftElbowConstraintAttachment0 .

2.

In the viewport, select the attachment and use the Rotate tool  to rotate the attachment so the yellow PrimaryAxis  is the axis of your elbow's expected rotation.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/inverse-kinematics/elbow-primary-axis.png)

3.

Set the LeftElbowConstraint.Attachment0  property to this new attachment.

4.

In the Explorer  window, navigate to your model's LeftLowerArm.LeftElbowRigAttachment  add an attachment:

1.

Click the ⊕ button  and add an Attachment  with the name LeftElbowConstraintAttachment1 .

2.

Set the LeftUpperArm.LeftElbowConstraint.Attachment1  property to this new attachment.

3.

Copy the LeftElbowConstraintAttachment0.CFrameOrientation  property and paste it as the LeftElbowConstraint.Attachment1.CFrameOrientation  value.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/inverse-kinematics/elbow-natural-pose.png)

If you see a red arrow on the constraint's visualization, that means your attachment orientations are violating the hinge constraint. Go back and make sure the LeftElbowConstraintAttachment1  has the same orientation as the LeftElbowConstraintAttachment0 .

Test your IKControl to verify the elbow only rotates about its hinge axis:

#### [Wrists](#wrists)[](#wrists)

Even with the elbow constraint, the IKControl can still produce unrealistic poses with the wrists.

![](https://prod.docsiteassets.roblox.com/assets/animation/inverse-kinematics/wrist-unnatural-pose.png) The wrist bends unnaturally at certain orientations

You can improve this by adding a [BallSocketConstraint](/docs/en-us/reference/engine/classes/BallSocketConstraint)  to limit the rotation of the wrist. While this is similar to the process for adding a [HingeConstraint](/docs/en-us/reference/engine/classes/HingeConstraint)  to the elbow, you can use the [LimitsEnabled](/docs/en-us/reference/engine/classes/BallSocketConstraint#LimitsEnabled)  property on this constraint to further control the range of motion of the wrist.

To add a [BallSocketConstraint](/docs/en-us/reference/engine/classes/BallSocketConstraint)  for the wrist:

1.

In the Explorer  window, locate your model's LeftHand  and click the ⊕ button .

1.

Add a BallSocketConstraint  with the name LeftWristConstraint .

2.

Locate your model's LeftLowerArm.LeftWristRigAttachment  and add an attachment:

1.

Click the ⊕ button  and add an Attachment  with the name LeftWristConstraintAttachment0 .

2.

In the viewport, select the attachment and use the Rotate tool  to rotate the attachment so the yellow PrimaryAxis points toward the model's fingertips.  ![](https://prod.docsiteassets.roblox.com/assets/animation/inverse-kinematics/wrist-primary-axis.png)

3.

Set the LeftWristConstraint.Attachment0  property to the new LeftWristConstraintAttachment0 .

3.

Locate your model's LeftHand.LeftWristRigAttachment  and add an attachment:

1.

Click the ⊕ button  and add an Attachment  with the name LeftWristConstraintAttachment1 .

2.

Copy the LeftWristConstraintAttachment0.CFrameOrientation  property and paste it as the LeftWristConstraintAttachment1.CFrameOrientation  property.

3.

Set the LeftWristConstraint.Attachment1  property to this new LeftWristConstraintAttachment1 .

4.

In the Explorer  window, select the LeftWristConstraint .

5.

In the Properties  window, set the following:

1.

Enable LimitsEnabled .

2.

Set UpperAngle  to 80 . This controls how much the constraint's axis can rotate, and 80 degrees is approximately how much the wrist should be able to bend.

6.

Depending on your character you may want to tweak the direction the cone is pointing in. You can do this by using the Rotate tool  to rotate the constraint's Attachment0 .

When selecting the LeftWristConstraint , a green cone appears visualizing the wrist's range of motion.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/inverse-kinematics/wrist-cone.png)

With the constraint set up, test the IKControl with the hand pointing down in front of the character and the wrist should rotate and bend more realistically.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
