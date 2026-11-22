<!-- Source: https://create.roblox.com/docs/physics -->

Physics | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/physics.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/workspace)
6. /
7. [Physics](/docs/physics)

# Physics

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/physics/index.md)

Roblox uses a rigid body physics engine. [BaseParts](/docs/reference/engine/classes/BasePart)  are subject to physical forces as long as they are not [Anchored](/docs/reference/engine/classes/BasePart#Anchored) . You can create physical [assemblies](#assemblies)  using attachments and constraints, and you can detect and control [collisions](#collisions)  between objects using events and collision filtering.

## [Assemblies](#assemblies)[](#assemblies)

An [assembly](/docs/physics/assemblies)  is one or more [BaseParts](/docs/reference/engine/classes/BasePart)  connected by rigid constraints or motors (animated rigid joints). Assemblies can be set to an initial linear or angular velocity, or their behavior can be affected through [constraints](#constraints) .

![A light blue cube against a dark blue background that represents an assembly of 1 part.](https://prod.docsiteassets.roblox.com/assets/physics/assemblies/Assembly-Example-Block.png) 1 assembly; 1 part

![A humanoid character model against a dark blue background that represents an assembly of 18 parts.](https://prod.docsiteassets.roblox.com/assets/physics/assemblies/Assembly-Example-Avatar.png) 1 assembly; 18 parts

![A pirate that represents an assemble of 179 parts.](https://prod.docsiteassets.roblox.com/assets/physics/assemblies/Assembly-Example-Ship.png) 1 assembly; 179 parts

## [Constraints](#constraints)[](#constraints)

Non-anchored assemblies react to force from gravity and collisions, but physical force can also be applied and simulated through [mechanical constraints](/docs/physics/mechanical-constraints)  or [mover constraints](/docs/physics/mover-constraints) .

Mechanical Mover

Mechanical constraints include familiar objects like [hinges](/docs/physics/constraints/hinge) , [springs](/docs/physics/constraints/spring) , and [ropes](/docs/physics/constraints/rope)  which can be used to build mechanisms. Each is summarized in the [mechanical constraints](/docs/physics/mechanical-constraints)  guide.

## [Collisions](#collisions)[](#collisions)

Collision events automatically occur when two [BaseParts](/docs/reference/engine/classes/BasePart)  touch or stop touching in the 3D world. You can [detect](/docs/workspace/collisions)  these collisions through the [Touched](/docs/reference/engine/classes/BasePart#Touched)  and [TouchEnded](/docs/reference/engine/classes/BasePart#TouchEnded)  events which occur regardless of either part's [CanCollide](/docs/reference/engine/classes/BasePart#CanCollide)  property value.

Through [collision filtering](/docs/workspace/collisions#collision-filtering)  techniques such as collision groups or part‑to‑part filtering, you can control which physical assemblies collide with others.

See the [collisions](/docs/workspace/collisions)  guide for more details on detecting and filtering collisions.

## [Network ownership](#network-ownership)[](#network-ownership)

In order to support complex physical mechanisms while also aiming for a smooth and responsive experience for players, the Roblox physics engine utilizes a distributed physics  system in which computations are distributed between the server and all connected clients. Within this system, the engine assigns network ownership  of physically simulated [BaseParts](/docs/reference/engine/classes/BasePart)  to either a client or server to divide the work of calculating physics. See the [network ownership](/docs/physics/network-ownership)  guide for further details.

## [Adaptive timestepping](#adaptive-timestepping)[](#adaptive-timestepping)

The engine emphasizes best performance by automatically assigning assemblies to one of three simulation rates. For scenarios featuring complex mechanisms like tanks, you can improve stability by setting a fixed timestep. See the [adaptive timestepping](/docs/physics/adaptive-timestepping)  guide for more information.

## [Sleep system](#sleep-system)[](#sleep-system)

When an assembly is not moving or accelerating, the Roblox physics engine improves performance by automatically stops simulating the assembly. See the [sleep system](/docs/physics/sleep-system)  guide for details.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
