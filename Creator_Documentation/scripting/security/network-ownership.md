<!-- Source: https://create.roblox.com/docs/en-us/scripting/security/network-ownership -->

Network ownership, movement validation, and physics | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/scripting/security/network-ownership.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Scripting](/docs/en-us/scripting)
6. /
7. Security

# Network ownership, movement validation, and physics

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/scripting/security/network-ownership.md)

The following content covers various concepts and tactics to improve security and mitigate cheating in your Roblox games. It's highly recommended that all developers read through these to ensure that your games are secure and fair for all users. Check the sidebar for additional security topics.

[Network ownership](/docs/en-us/physics/network-ownership)  is one of the more nuanced and commonly misunderstood aspects of the Roblox engine. When a player has network ownership of a part or assembly, they have complete authority over the physics simulation for those objects. By default, the server grants network ownership of unanchored parts to clients with nearby player characters to distribute the load of the physics simulation. This system improves responsiveness but creates significant security implications that every developer must understand.

## [Understanding network ownership](#understanding-network-ownership)[](#understanding-network-ownership)

When a client has network ownership over parts (including their character), they have access to:

Assembly manipulation:

-

Teleport to any position.

-

This can be used to quickly gain ownership and control of as many unanchored parts and assemblies as the server will allow.

-

Manipulate their movement and state, such as flying or changing their speed.

-

Exploiters can set their Humanoid WalkSpeed to any value. Properties can be modified locally without firing any events on the local client, and without such property changes capable of being read from local scripts.

-

Play arbitrary animations and manipulate animation state.

-

Bypass physical obstacles and alter their collision.

Physics manipulation

-

Control the position and rotation of any unanchored parts or mechanisms, including replicating Inf  or NaN  components in [CFrames](/docs/en-us/reference/engine/datatypes/CFrame) . Set part velocities to extreme values (including Inf  or NaN ), which can interfere with the physics of other unanchored parts/assemblies, even those that are not owned by the exploiter. This is often used to fling other player characters and nearby parts. Manipulate the firing of Touched events, including not firing Touched at all.

Should your game necessitate gameplay-critical fully unanchored parts or assemblies, consider using the network ownership API to manually set ownership or turn off automatic ownership.

## [Movement validation](#movement-validation)[](#movement-validation)

In competitive games, server-side validation of player movement is crucial for simulation integrity, as clients control character movement and physics. However, a universal solution doesn't exist due to varying gameplay mechanics.

Traditional methods often fall short in complex scenarios. Simple distance-over-time calculations may suffice for competitive shooters but fail in physics-intensive games involving vehicles, flight, or intricate interactions. Validation must also account for network latency.

[Server authority](/docs/en-us/../../projects/server-authority)  is currently in beta and will be released soon. The most reliable solution for preventing physics and movement exploits is server authority, which moves physics simulation and movement validation entirely to the server. This eliminates the fundamental security weakness of client-controlled movement by ensuring all movement decisions are made on the server with authoritative validation.

Until server authority becomes available, developers implementing client-side validation must understand that effective approaches vary dramatically. Basic heuristics can flag innocent players with unstable connections, and straightforward speed calculations break down in games with complex movement systems. Position updates are subject to internet latency, requiring averaging over time. Many developers find that leaky bucket-style accumulators work well for handling burst movements while preventing sustained violations.

Practical implementation often requires projecting movement onto specific planes (e.g., XZ for ground-based movement) to avoid penalizing legitimate vertical movement while detecting horizontal teleportation. Games with legitimate teleportation mechanics need explicit exemption systems. Validation frequency, tolerance levels, and enforcement strategies should be tuned to each game's specific requirements.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
