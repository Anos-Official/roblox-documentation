<!-- Source: https://create.roblox.com/docs/physics/assemblies -->

Assemblies | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/physics/assemblies.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/workspace)
6. /
7. [Physics](/docs/physics)

# Assemblies

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/physics/assemblies.md)

An assembly  is one or more [parts](/docs/parts)  welded by a rigid [WeldConstraint](/docs/reference/engine/classes/WeldConstraint)  or connected through movable joints, like [Motor6Ds](/docs/reference/engine/classes/Motor6D) . You can group an assembly of parts in a [model](/docs/parts/models)  container to quickly organize the parts and related objects as a single asset.

![A light blue cube against a dark blue background that represents an assembly of 1 part.](https://prod.docsiteassets.roblox.com/assets/physics/assemblies/Assembly-Example-Block.png) 1 assembly; 1 part

![A humanoid character model against a dark blue background that represents an assembly of 18 parts.](https://prod.docsiteassets.roblox.com/assets/physics/assemblies/Assembly-Example-Avatar.png) 1 assembly; 18 parts

![A pirate that represents an assemble of 179 parts.](https://prod.docsiteassets.roblox.com/assets/physics/assemblies/Assembly-Example-Ship.png) 1 assembly; 179 parts

From a physics perspective, an assembly is considered a single rigid body , meaning no force can push or pull the connected parts from each other, and they will move as a single unit. All forces applied to a specific [BasePart](/docs/reference/engine/classes/BasePart)  are applied to its assembly — for instance, [BasePart:ApplyImpulse()](/docs/reference/engine/classes/BasePart#ApplyImpulse)  applies impulse to the assembly at [BasePart.AssemblyCenterOfMass](/docs/reference/engine/classes/BasePart#AssemblyCenterOfMass) .

The joints that combine multiple parts into assemblies are only active in the [Workspace](/docs/reference/engine/classes/Workspace)  or another [WorldModel](/docs/reference/engine/classes/WorldModel)  instance. If the parts are stored elsewhere, all of the welds/connections that combine parts into assemblies will be non-functional.

To view colored outlines around parts in order to visualize single rigid body assemblies, toggle on Assemblies  from the [Visualization Options](/docs/studio/overview#visualization-options)  widget in the upper‑right corner of the 3D viewport.

## [Assembly properties](#assembly-properties)[](#assembly-properties)

The following [BasePart](/docs/reference/engine/classes/BasePart)  properties show data regarding its assembly. Their values will be the same for any part in the same assembly, so it doesn't matter which part you use.

| Property | | Description |
| --- | --- |
| [BasePart.AssemblyLinearVelocity](/docs/reference/engine/classes/BasePart#AssemblyLinearVelocity) | | The linear velocity vector of the part's assembly. Setting the velocity directly may lead to unrealistic motion, so usage of a [VectorForce](/docs/reference/engine/classes/VectorForce)  or [LinearVelocity](/docs/reference/engine/classes/LinearVelocity)  constraint is preferred, or [BasePart:ApplyImpulse()](/docs/reference/engine/classes/BasePart#ApplyImpulse)  for an instantaneous change in linear velocity. |
| [BasePart.AssemblyAngularVelocity](/docs/reference/engine/classes/BasePart#AssemblyAngularVelocity) | | The angular velocity vector of the part's assembly. Setting the velocity directly may lead to unrealistic motion, so usage of a [Torque](/docs/reference/engine/classes/Torque)  or [AngularVelocity](/docs/reference/engine/classes/AngularVelocity)  constraint is preferred, or [BasePart:ApplyAngularImpulse()](/docs/reference/engine/classes/BasePart#ApplyAngularImpulse)  for an instantaneous change in angular velocity. |
| [BasePart.AssemblyCenterOfMass](/docs/reference/engine/classes/BasePart#AssemblyCenterOfMass) | | A read-only position calculated via the mass and position of all the parts in the assembly. A force applied to the center of mass will not cause angular acceleration, only linear. |
| [BasePart.AssemblyMass](/docs/reference/engine/classes/BasePart#AssemblyMass) | | The sum of the [BasePart.Mass](/docs/reference/engine/classes/BasePart#Mass)  of all parts in the assembly. If the assembly has an anchored part, the assembly's mass is considered infinite. |
| [BasePart.AssemblyRootPart](/docs/reference/engine/classes/BasePart#AssemblyRootPart) | | The part automatically chosen to represent the assembly's [root part](#assembly-root-part) . |

## [Assembly root part](#assembly-root-part)[](#assembly-root-part)

Every assembly has a root part  indicated by its [AssemblyRootPart](/docs/reference/engine/classes/BasePart#AssemblyRootPart)  property. This is the part that doesn't move when [Motor6D](/docs/reference/engine/classes/Motor6D)  transforms are updated, as well as the part used to keep consistent physics replication and network ownership.

You cannot explicitly set the root part, but the following factors affect probability from highest to lowest:

![](https://prod.docsiteassets.roblox.com/assets/misc/Arrow-Higher.png)

An [Anchored](/docs/reference/engine/classes/BasePart#Anchored)  part will always be assigned as the root part.

![](https://prod.docsiteassets.roblox.com/assets/misc/Arrow-High.png)

Parts with [Massless](/docs/reference/engine/classes/BasePart#Massless)  set to false  (default) take precedence.

![](https://prod.docsiteassets.roblox.com/assets/misc/Arrow-Low.png)

Higher [RootPriority](/docs/reference/engine/classes/BasePart#RootPriority)  values take precedence.

![](https://prod.docsiteassets.roblox.com/assets/misc/Arrow-Lower.png)

Precedence based on the part's size (largest face area), with multipliers for specific part types. [Seats](/docs/reference/engine/classes/Seat)  and [VehicleSeats](/docs/reference/engine/classes/VehicleSeat)  receive the highest multiplier, followed by parts named HumanoidRootPart , then parts named Torso .

## [Anchoring behavior](#anchoring-behavior)[](#anchoring-behavior)

When one of an assembly's parts is anchored, that part becomes the root part and all of the other parts become implicitly anchored with it. The following sequence illustrates this behavior.

1.

Below, four parts are welded together with [WeldConstraints](/docs/reference/engine/classes/WeldConstraint)  (green bars) to form a single assembly, as indicated by the matching colored outlines.

![](https://prod.docsiteassets.roblox.com/assets/physics/assemblies/Assembly-Anchor-Diagram-1.png) Four parts welded to become a single assembly

2.

If just one  part in the assembly is anchored, the assembly will not change, other than the root part potentially changing (the anchored part always has the highest [priority](#assembly-root-part)  for becoming the root part).

![](https://prod.docsiteassets.roblox.com/assets/physics/assemblies/Assembly-Anchor-Diagram-2.png) Anchored part (as indicated with an anchor icon) becomes the new root part

3.

If more than one part is anchored, the assembly will split . Below, both the left and top parts are anchored, so the original assembly splits into two assemblies as shown by the colored outlines. Also, the [WeldConstraint](/docs/reference/engine/classes/WeldConstraint)  between the two assemblies deactivates, since you cannot have an active weld between two anchored assemblies.

![](https://prod.docsiteassets.roblox.com/assets/physics/assemblies/Assembly-Anchor-Diagram-3.png) Two assemblies with anchored parts as their respective root parts

If you want to anchor all parts in an assembly, you only need to anchor the assembly's root part. Anchoring all parts is actually less performant, as it creates more assemblies.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
