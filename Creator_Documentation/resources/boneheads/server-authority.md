<!-- Source: https://create.roblox.com/docs/en-us/resources/boneheads/server-authority.md -->

---
title: "Server Authority core"
url: /docs/en-us/resources/boneheads/server-authority
last_updated: 2026-11-20T18:47:28Z
description: "Explains how Boneheads uses Server Authority, validated client intent, and server-owned systems to keep shared physics consistent for every player."
---

# Server Authority core

A round of [**Boneheads**](https://github.com/Roblox/resources/tree/main/experiences/boneheads) looks like chaotic co-play. Players stretch their oversized limbs across pressure plates, steal objects from each other, exchange clothing, and throw props hard enough to knock off another player's head. Interference is baked into the gameplay, but it means that multiple players compete to handle useful objects in the courtyard, turning a comedy about clumsy skeletons into a networking nightmare.

This game chose to handle the chaotic shared spectacle by setting `Class.Workspace.AuthorityMode|AuthorityMode` to `Enum.AuthorityMode.Server|Server`, bringing character abilities, physics, input, and every system capable of affecting the world under a single [authoritative](/docs/en-us/projects/server-authority.md) umbrella.

> **Warning:**`Class.Workspace.AuthorityMode|AuthorityMode` is a protected setting that must be manually set in Roblox Studio. It can't be set in a script or stored with the project code. If you forget it, you'll be testing a completely different game than you think.
## Clients express intent, not outcome

Network latency in [**Boneheads**](https://github.com/Roblox/resources/tree/main/experiences/boneheads) is managed by players expressing **intent** while the server maintains the **outcome**. Picking up or stealing an object, moving the aim cursor, and charging a throw can respond immediately. When a player device's opinion of the world diverges from the server, that device [rolls back](/docs/en-us/projects/server-authority.md#rollback-and-resimulation) to the last known authoritative server state. These corrections are small and frequent enough that players don't consciously notice them, and they keep the game fair and fun for everybody.

_While a player holds an object, their local client works out an aim point from the camera and the current input. The aim point is streamed to the server through a `Class.RemoteEvent` which keeps aiming responsive because nothing waits for a client/server round trip before it updates._

## Server controls world-changing systems

Several systems rewrite the courtyard in ways every player has to agree on. Those systems start from server scripts so one side owns the resulting state:

###### Characters

Custom avatar spawning, limb scaling, head welding, and skeleton tinting.

###### Clothing & accessories

Clothing setup and accessory equip or unequip.

###### Carrying & stealing

Carryable transfers, including stealing an item from another player's hands.

###### Off with their heads!

Projectile knockoffs that eject another player's head after a hard impact.

###### Recovery & respawn

Death-plane recovery that returns a body or loose head to a spawn.

[Puzzle mechanisms](/docs/en-us/resources/boneheads/puzzle-mechanics.md) are a separate case. Levers, plates, targets, counters, gates, and doors don't call into each other; instead, each one reports its own state with a replicated `_activated` [attribute](/docs/en-us/studio/properties.md#instance-attributes) and other mechanisms read those attributes as inputs. A pressure plate reports that something is resting on it, a counter gate tracks how many of its inputs are active, and a door opens once every configured input agrees.