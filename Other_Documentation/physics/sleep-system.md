<!-- Source: https://create.roblox.com/docs/physics/sleep-system -->

Sleep system | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/physics/sleep-system.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/workspace)
6. /
7. [Physics](/docs/physics)

# Sleep system

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/physics/sleep-system.md)

Each [assembly](/docs/physics/assemblies)  in the Roblox Engine corresponds to a single rigid body . The position and velocity of each rigid body describe where it's located and how fast it's moving, and one of the primary engine tasks is to update the positions and velocities of each assembly.

Assemblies can be connected together with [mechanical constraints](/docs/physics/mechanical-constraints)  and [mover constraints](/docs/physics/mover-constraints)  to form mechanisms such as cars or airplanes. As the number of assemblies and constraints in a mechanism increases, the time required to simulate the mechanism also increases. Fortunately, this increase is offset when the sleep system  determines that the engine can skip simulation of non‑moving assemblies.

## [Sleep states](#sleep-states)[](#sleep-states)

Each assembly can be in one of three states: [awake](#awake) , [sleeping](#sleeping) , or [sleep‑checking](#sleep-checking) .

### [Awake](#awake)[](#awake)

An awake  assembly is moving or accelerating, and is therefore simulated. Assemblies enter this state from situations outlined in [sleeping](#sleeping)  and [sleep‑checking](#sleep-checking) , as well as [additional wake situations](#additional-wake-situations) .

### [Sleeping](#sleeping)[](#sleeping)

A sleeping  assembly is neither moving nor accelerating, and is therefore not simulated.

An assembly is determined to be non-moving by checking its linear velocity  and rotational velocity . If its linear velocity is less than the [Linear Velocity](#threshold-reference)  threshold and its rotational velocity is less than the [Rotational Velocity](#threshold-reference)  threshold, the assembly is considered to be non-moving.

In some cases, simply checking for non-movement would cause an assembly to incorrectly enter the sleeping state. For example, if a ball is thrown straight up, its velocity approaches zero as it reaches its maximum height, making it a candidate to sleep and never fall back down. To handle such cases, the engine considers an assembly to be accelerating if its linear acceleration  or rotational acceleration  are greater than the [Linear Acceleration](#threshold-reference)  and [Rotational Acceleration](#threshold-reference)  thresholds, respectively, and will prevent the assembly from falling asleep.

If an assembly falls asleep when you expect it to remain awake, it's commonly because the assembly is moving too slowly. In addition to automatic checks outlined in [sleep‑checking](#sleep-checking)  and [sleeping](#sleeping) , you can forcibly wake up an assembly through the conditions outlined in [additional wake situations](#additional-wake-situations) .

### [Sleep-checking](#sleep-checking)[](#sleep-checking)

A non-moving assembly that shares a constraint with at least one [awake](#awake)  neighboring assembly is put into the sleep-checking  state and is not simulated. On each worldstep, a sleep-checking assembly checks whether:

-

Its linear acceleration  is greater than the [Wake Linear Acceleration](#threshold-reference)  threshold.

-

Its rotational acceleration  is greater than the [Wake Rotational Acceleration](#threshold-reference)  threshold.

-

A neighboring assembly's linear velocity  is greater than the [Neighbor Linear Velocity](#threshold-reference)  threshold.

-

A neighboring assembly's rotational velocity  is greater than the [Neighbor Rotational Velocity](#threshold-reference)  threshold.

If any of these conditions is true, or under any of the [additional wake situations](#additional-wake-situations) , the sleep-checking assembly enters the [awake](#awake)  state.

## [Threshold reference](#threshold-reference)[](#threshold-reference)

The following table provides the various velocity and acceleration thresholds used to determine if an assembly is moving or accelerating.

| Threshold | | Value | | State change |
| --- | --- |
| Linear Velocity | | 0.33 studs/s | | [awake](#awake)  ⟩ [sleeping](#sleeping) |
| Rotational Velocity | | 0.42 studs/s | | [awake](#awake)  ⟩ [sleeping](#sleeping) |
| Linear Acceleration | | 0.24 studs/s² | | [awake](#awake)  ⟩ [sleeping](#sleeping) |
| Rotational Acceleration | | 0.24 studs/s² | | [awake](#awake)  ⟩ [sleeping](#sleeping) |
| Neighbor Linear Velocity | | 0.48 studs/s | | [sleep-checking](#sleep-checking)  ⟩ [awake](#awake) |
| Neighbor Rotational Velocity | | 0.59 studs/s | | [sleep-checking](#sleep-checking)  ⟩ [awake](#awake) |
| Wake Linear Acceleration | | 16.9 studs/s² | | [awake](#awake)  ⟩ [sleeping](#sleeping) |
| Wake Rotational Acceleration | | 16.9 studs/s² | | [awake](#awake)  ⟩ [sleeping](#sleeping) |

Rotational velocity and acceleration thresholds reflect the velocity and acceleration of a point located on the assembly bounding sphere (a sphere that contains all of the parts in an assembly) that moves rigidly with the assembly.

For a given angular velocity, the rotational velocity of an assembly is proportional to the assembly bounding sphere radius. This means that larger assemblies can rotate at a lower angular velocity without falling asleep.

## [Actuated joints](#actuated-joints)[](#actuated-joints)

Sometimes developers want to move parts very slowly using an actuated joint , a constraint that applies force or motion to drive connected parts, such as a [HingeConstraint](/docs/reference/engine/classes/HingeConstraint)  using a [Motor](/docs/reference/engine/enums/ActuatorType#Motor) . To support these scenarios, assemblies connected to actuated joints use a stricter sleep velocity threshold. This delays when those assemblies fall asleep, allowing slow, controlled motion without the physics system prematurely putting them to sleep.

The following are considered actuated joints:

| Constraint | | Configuration | | Required nonzero properties |
| [AlignOrientation](/docs/reference/engine/classes/AlignOrientation) | | [RigidityEnabled](/docs/reference/engine/classes/AlignOrientation#RigidityEnabled)  = false | |
-

[MaxAngularVelocity](/docs/reference/engine/classes/AlignOrientation#MaxAngularVelocity)

-

[MaxTorque](/docs/reference/engine/classes/AlignOrientation#MaxTorque)

-

[Responsiveness](/docs/reference/engine/classes/AlignOrientation#Responsiveness)

 |
| [AlignPosition](/docs/reference/engine/classes/AlignPosition) | | [RigidityEnabled](/docs/reference/engine/classes/AlignPosition#RigidityEnabled)  = false | |
-

[MaxVelocity](/docs/reference/engine/classes/AlignPosition#MaxVelocity)

-

[Responsiveness](/docs/reference/engine/classes/AlignPosition#Responsiveness)

 |
| [AngularVelocity](/docs/reference/engine/classes/AngularVelocity) | | — | |
-

[AngularVelocity](/docs/reference/engine/classes/AngularVelocity#AngularVelocity)

-

[MaxTorque](/docs/reference/engine/classes/AngularVelocity#MaxTorque)

 |
| [AnimationConstraint](/docs/reference/engine/classes/AnimationConstraint) | | [IsKinematic](/docs/reference/engine/classes/AnimationConstraint#IsKinematic)  = false | |
-

[MaxForce](/docs/reference/engine/classes/AnimationConstraint#MaxForce)

-

[MaxTorque](/docs/reference/engine/classes/AnimationConstraint#MaxTorque)

 |
| [CylindricalConstraint](/docs/reference/engine/classes/CylindricalConstraint) | | [ActuatorType](/docs/reference/engine/classes/CylindricalConstraint#ActuatorType)  = [Motor](/docs/reference/engine/enums/ActuatorType#Motor) | |
-

[Velocity](/docs/reference/engine/classes/CylindricalConstraint#Velocity)

-

[MotorMaxAcceleration](/docs/reference/engine/classes/CylindricalConstraint#MotorMaxAcceleration)

-

[MotorMaxForce](/docs/reference/engine/classes/CylindricalConstraint#MotorMaxForce)

 |
| [ActuatorType](/docs/reference/engine/classes/CylindricalConstraint#ActuatorType)  = [Servo](/docs/reference/engine/enums/ActuatorType#Servo) | |
-

[Speed](/docs/reference/engine/classes/CylindricalConstraint#Speed)

-

[ServoMaxForce](/docs/reference/engine/classes/CylindricalConstraint#ServoMaxForce)

-

[Responsiveness](/docs/reference/engine/classes/CylindricalConstraint#Responsiveness)

 |
| [CylindricalConstraint](/docs/reference/engine/classes/CylindricalConstraint) | | [AngularActuatorType](/docs/reference/engine/classes/CylindricalConstraint#AngularActuatorType)  = [Motor](/docs/reference/engine/enums/ActuatorType#Motor) | |
-

[AngularVelocity](/docs/reference/engine/classes/CylindricalConstraint#AngularVelocity)

-

[MotorMaxAngularAcceleration](/docs/reference/engine/classes/CylindricalConstraint#MotorMaxAngularAcceleration)

-

[MotorMaxTorque](/docs/reference/engine/classes/CylindricalConstraint#MotorMaxTorque)

 |
| [AngularActuatorType](/docs/reference/engine/classes/CylindricalConstraint#AngularActuatorType)  = [Servo](/docs/reference/engine/enums/ActuatorType#Servo) | |
-

[AngularSpeed](/docs/reference/engine/classes/CylindricalConstraint#AngularSpeed)

-

[ServoMaxTorque](/docs/reference/engine/classes/CylindricalConstraint#ServoMaxTorque)

-

[Responsiveness](/docs/reference/engine/classes/CylindricalConstraint#Responsiveness)

 |
| [HingeConstraint](/docs/reference/engine/classes/HingeConstraint) | | [ActuatorType](/docs/reference/engine/classes/HingeConstraint#ActuatorType)  = [Motor](/docs/reference/engine/enums/ActuatorType#Motor) | |
-

[AngularVelocity](/docs/reference/engine/classes/HingeConstraint#AngularVelocity)

-

[MotorMaxAcceleration](/docs/reference/engine/classes/HingeConstraint#MotorMaxAcceleration)

-

[MotorMaxTorque](/docs/reference/engine/classes/HingeConstraint#MotorMaxTorque)

 |
| [ActuatorType](/docs/reference/engine/classes/HingeConstraint#ActuatorType)  = [Servo](/docs/reference/engine/enums/ActuatorType#Servo) | |
-

[AngularSpeed](/docs/reference/engine/classes/HingeConstraint#AngularSpeed)

-

[ServoMaxTorque](/docs/reference/engine/classes/HingeConstraint#ServoMaxTorque)

-

[Responsiveness](/docs/reference/engine/classes/HingeConstraint#Responsiveness)

 |
| [LinearVelocity](/docs/reference/engine/classes/LinearVelocity) | | [VelocityConstraintMode](/docs/reference/engine/classes/LinearVelocity#VelocityConstraintMode)  = [Line](/docs/reference/engine/enums/VelocityConstraintMode#Line) | |
-

[LineVelocity](/docs/reference/engine/classes/LinearVelocity#LineVelocity)

-

If [ForceLimitsEnabled](/docs/reference/engine/classes/LinearVelocity#ForceLimitsEnabled) , also [MaxForce](/docs/reference/engine/classes/LinearVelocity#MaxForce)

 |
| [VelocityConstraintMode](/docs/reference/engine/classes/LinearVelocity#VelocityConstraintMode)  = [Plane](/docs/reference/engine/enums/VelocityConstraintMode#Plane) | |
-

[PlaneVelocity](/docs/reference/engine/classes/LinearVelocity#PlaneVelocity)

-

If [ForceLimitsEnabled](/docs/reference/engine/classes/LinearVelocity#ForceLimitsEnabled) :
-

[Magnitude](/docs/reference/engine/enums/ForceLimitMode#Magnitude) : [MaxForce](/docs/reference/engine/classes/LinearVelocity#MaxForce)

-

[PerAxis](/docs/reference/engine/enums/ForceLimitMode#PerAxis) : [MaxPlanarAxesForce](/docs/reference/engine/classes/LinearVelocity#MaxPlanarAxesForce)

 |
| [VelocityConstraintMode](/docs/reference/engine/classes/LinearVelocity#VelocityConstraintMode)  = [Vector](/docs/reference/engine/enums/VelocityConstraintMode#Vector) | |
-

[VectorVelocity](/docs/reference/engine/classes/LinearVelocity#VectorVelocity)

-

If [ForceLimitsEnabled](/docs/reference/engine/classes/LinearVelocity#ForceLimitsEnabled) :
-

[Magnitude](/docs/reference/engine/enums/ForceLimitMode#Magnitude) : [MaxForce](/docs/reference/engine/classes/LinearVelocity#MaxForce)

-

[PerAxis](/docs/reference/engine/enums/ForceLimitMode#PerAxis) : [MaxAxesForce](/docs/reference/engine/classes/LinearVelocity#MaxAxesForce)

 |
| [PrismaticConstraint](/docs/reference/engine/classes/PrismaticConstraint) | | [ActuatorType](/docs/reference/engine/classes/PrismaticConstraint#ActuatorType)  = [Motor](/docs/reference/engine/enums/ActuatorType#Motor) | |
-

[Velocity](/docs/reference/engine/classes/PrismaticConstraint#Velocity)

-

[MotorMaxAcceleration](/docs/reference/engine/classes/PrismaticConstraint#MotorMaxAcceleration)

-

[MotorMaxForce](/docs/reference/engine/classes/PrismaticConstraint#MotorMaxForce)

 |
| [ActuatorType](/docs/reference/engine/classes/PrismaticConstraint#ActuatorType)  = [Servo](/docs/reference/engine/enums/ActuatorType#Servo) | |
-

[Speed](/docs/reference/engine/classes/PrismaticConstraint#Speed)

-

[ServoMaxForce](/docs/reference/engine/classes/PrismaticConstraint#ServoMaxForce)

-

[Responsiveness](/docs/reference/engine/classes/PrismaticConstraint#Responsiveness)

 |
| [RopeConstraint](/docs/reference/engine/classes/RopeConstraint) | | [WinchEnabled](/docs/reference/engine/classes/RopeConstraint#WinchEnabled)  = true | |
-

[WinchForce](/docs/reference/engine/classes/RopeConstraint#WinchForce)

-

[WinchSpeed](/docs/reference/engine/classes/RopeConstraint#WinchSpeed)

 |

## [Additional wake situations](#additional-wake-situations)[](#additional-wake-situations)

In addition to situations outlined in [sleep‑checking](#sleep-checking)  and [sleeping](#sleeping) , an assembly enters the [awake](#awake)  state when:

-

It collides with another assembly moving faster than 1 studs/s.

-

Any physics-related property of any [BasePart](/docs/reference/engine/classes/BasePart)  within the assembly changes, including:

-

[Anchored](/docs/reference/engine/classes/BasePart#Anchored)

-

[AssemblyLinearVelocity](/docs/reference/engine/classes/BasePart#AssemblyLinearVelocity) /[AssemblyAngularVelocity](/docs/reference/engine/classes/BasePart#AssemblyAngularVelocity)

-

[CanCollide](/docs/reference/engine/classes/BasePart#CanCollide) /[CanTouch](/docs/reference/engine/classes/BasePart#CanTouch)

-

[CustomPhysicalProperties](/docs/reference/engine/classes/BasePart#CustomPhysicalProperties)

-

[EnableFluidForces](/docs/reference/engine/classes/BasePart#EnableFluidForces)

-

[Massless](/docs/reference/engine/classes/BasePart#Massless)

-

[RootPriority](/docs/reference/engine/classes/BasePart#RootPriority)

-

A non-zero impulse is applied to any [BasePart](/docs/reference/engine/classes/BasePart)  within the assembly via [ApplyImpulse()](/docs/reference/engine/classes/BasePart#ApplyImpulse) , [ApplyImpulseAtPosition()](/docs/reference/engine/classes/BasePart#ApplyImpulseAtPosition) , or [ApplyAngularImpulse()](/docs/reference/engine/classes/BasePart#ApplyAngularImpulse) .

-

Any physics-related property changes on the [Workspace](/docs/reference/engine/classes/Workspace)  that would affect the assembly, including:

-

[Gravity](/docs/reference/engine/classes/Workspace#Gravity)

-

[FluidForces](/docs/reference/engine/classes/Workspace#FluidForces)

-

[GlobalWind](/docs/reference/engine/classes/Workspace#GlobalWind)

-

[AirDensity](/docs/reference/engine/classes/Workspace#AirDensity)

-

A new [Constraint](/docs/reference/engine/classes/Constraint)  is created with an [Attachment](/docs/reference/engine/classes/Attachment)  that is parented to a [BasePart](/docs/reference/engine/classes/BasePart)  within the assembly.

-

Any property changes for a [Constraint](/docs/reference/engine/classes/Constraint)  with an [Attachment](/docs/reference/engine/classes/Attachment)  that is parented to a [BasePart](/docs/reference/engine/classes/BasePart)  within the assembly.

-

The [CurrentAngle](/docs/reference/engine/classes/Motor#CurrentAngle)  property changes for a [Motor](/docs/reference/engine/classes/Motor)  that is connected to a [BasePart](/docs/reference/engine/classes/BasePart)  within the assembly.

-

The assembly contains a [VehicleSeat](/docs/reference/engine/classes/VehicleSeat)  with a seated player character.

-

The assembly is within the [BlastRadius](/docs/reference/engine/classes/Explosion#BlastRadius)  of an [Explosion](/docs/reference/engine/classes/Explosion) .

## [Debug visualization](#debug-visualization)[](#debug-visualization)

During playtesting, you can visualize assembly sleep states by toggling on Awake parts  from the [Visualization Options](/docs/studio/overview#visualization-options)  widget in the upper‑right corner of the 3D viewport.

 ![A close up view of the 3D viewport with the Visualization Options button indicated in the upper-right corner.](https://prod.docsiteassets.roblox.com/assets/studio/general/Visualization-Options.png)

Once enabled, simulated parts will be outlined by their current sleep state, with [awake](#awake)  parts outlined in red, [sleep‑checking](#sleep-checking)  parts outlined in orange, and [sleeping](#sleeping)  parts un‑outlined.

Simulated parts outlined by the color representing their current sleep state

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
