<!-- Source: https://create.roblox.com/docs/physics/network-ownership -->

Network ownership | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/physics/network-ownership.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [3D workspace](/docs/workspace)
6. /
7. [Physics](/docs/physics)

# Network ownership

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/physics/network-ownership.md)

In order to support complex physical mechanisms while also aiming for a smooth and responsive experience for players, the Roblox [physics](/docs/physics)  engine utilizes a distributed physics  system in which computations are distributed between the server and all connected clients. Within this system, the engine assigns network ownership  of physically simulated [BaseParts](/docs/reference/engine/classes/BasePart)  to either a client or server to divide the work of calculating physics.

Clients experience more responsive  physics interactions with parts that they own, since there's no latency from communication with the server. Network ownership also improves server performance because physics computations can be split up among individual clients, allowing the server to prioritize other tasks.

## [BasePart ownership](#basepart-ownership)[](#basepart-ownership)

By default, the server retains ownership of any [BasePart](/docs/reference/engine/classes/BasePart) . Additionally, the server always  owns anchored [BaseParts](/docs/reference/engine/classes/BasePart)  and you cannot manually change their ownership.

Based on a client's hardware capacity and the player's [Player.Character](/docs/reference/engine/classes/Player#Character)  proximity to an unanchored [BasePart](/docs/reference/engine/classes/BasePart) , the engine automatically assigns ownership of that part to the client. Thus, parts close to a player's character are more likely to become player-owned.

## [Assembly ownership](#assembly-ownership)[](#assembly-ownership)

If a physics-based mechanism has no anchored parts, [setting ownership](#setting-ownership)  on an [assembly](/docs/physics/assemblies)  within that mechanism sets the same ownership for every assembly  in the mechanism.

If you anchor a lone assembly that is not  part of a broader mechanism, its ownership goes to the server, since the server always owns anchored [BaseParts](/docs/reference/engine/classes/BasePart) . Upon unanchoring the same assembly, its previous ownership state is lost and it reverts to automatic handling by the engine.

If you anchor one assembly within a broader mechanism of assemblies, its ownership goes to the server, but ownership of the other assemblies remains unchanged. Unanchoring the same assembly reverts its previously set ownership.

## [Setting ownership](#setting-ownership)[](#setting-ownership)

In games with complex physics interactions or in cases where you need to assign direct control, you can set ownership through a server-side call to [BasePart:SetNetworkOwner()](/docs/reference/engine/classes/BasePart#SetNetworkOwner) .

While you can manually call [SetNetworkOwner(nil)](/docs/reference/engine/classes/BasePart#SetNetworkOwner)  for the server for gameplay-critical objects that the client should not be able to manipulate, you should do so conservatively since it may result in jittery physics interactions for clients.

 Also note that the server always  owns anchored [BaseParts](/docs/reference/engine/classes/BasePart)  and you cannot manually change their ownership.

Consider a vehicle that has a [VehicleSeat](/docs/reference/engine/classes/VehicleSeat)  object for the driver and a [Seat](/docs/reference/engine/classes/Seat)  object for a passenger, with both included in the vehicle assembly. With the default ownership rules, if a player character sits in the [Seat](/docs/reference/engine/classes/Seat)  (passenger) and then another player jumps into the [VehicleSeat](/docs/reference/engine/classes/VehicleSeat)  (driver), the passenger  gains physical ownership of the entire vehicle because they entered first. The driver will have to wait several network cycles before their input is recognized and the vehicle will feel less responsive.

The following [Script](/docs/reference/engine/classes/Script)  fixes this by manually assigning network ownership to the driver. In it, the [VehicleSeat](/docs/reference/engine/classes/VehicleSeat)  sets its [Occupant](/docs/reference/engine/classes/VehicleSeat#Occupant)  to the [Humanoid](/docs/reference/engine/classes/Humanoid)  sitting on it, so the script listens for the seat's [Changed](/docs/reference/engine/classes/Instance#Changed)  event to catch when a player sits in the seat. When the driver leaves the seat, the vehicle's network ownership is reverted to automatic with [BasePart:SetNetworkOwnershipAuto()](/docs/reference/engine/classes/BasePart#SetNetworkOwnershipAuto) .

```

local Players = game:GetService("Players")

local vehicleSeat = script.Parent

vehicleSeat.Changed:Connect(function(prop)

	if prop == "Occupant" then

		local humanoid = vehicleSeat.Occupant

		if humanoid then

			-- Get the player from the character

			local player = Players:GetPlayerFromCharacter(humanoid.Parent)

			if player then

				vehicleSeat:SetNetworkOwner(player)

			end

		else

			-- Reset ownership when seat is unoccupied

			vehicleSeat:SetNetworkOwnershipAuto()

		end

	end

end)

```

For smooth performance and responsive behavior, ensure you also assign ownership of any loose [BaseParts](/docs/reference/engine/classes/BasePart)  on top of a vehicle to the same client that controls the vehicle.

## [Visualizing ownership](#visualizing-ownership)[](#visualizing-ownership)

To assist with network ownership debugging, Studio can render colored outlines around objects when playtesting.

| Outline color | | Description |
| --- | --- |
|  | | (green) | | Your client owns the part and is simulating it. |
|  | | (red) | | The part is within a "buffer zone" where your client is simulating it but it's still owned by something else. Your client might get ownership after this, or it may reject. |
|
 | | (white/grey) | | Server or another client owns the part through either automatic network ownership or from explicit assignment through [part:SetNetworkOwner()](/docs/reference/engine/classes/BasePart#SetNetworkOwner) . |
|  | | (black) | | The part is owned by neither the server nor the client. Physics will not apply to this part. |

Note that in a [multi-client simulation](/docs/studio/testing-modes#multi-client-simulation) , each client is assigned a unique color to indicate their ownership; this is mirrored in the [Server](/docs/studio/testing-modes#toggle-clientserver)  view, helping you determine which client owns which part(s) at any given time.

To enable network ownership visualization:

1.

Click on the visualization options  button in the upper-right corner of the 3D viewport.

 ![A close up view of the 3D viewport with the Visualization Options button indicated in the upper-right corner.](https://prod.docsiteassets.roblox.com/assets/studio/general/Visualization-Options.png)

2.

In the dropdown menu, toggle on Network owners .

## [Security concerns](#security-concerns)[](#security-concerns)

Roblox cannot verify physics calculations when a client has ownership over a [BasePart](/docs/reference/engine/classes/BasePart) . Clients can exploit this and send bad data to the server, such as teleporting the [BasePart](/docs/reference/engine/classes/BasePart) , making it go through walls or fly around.

Additionally, [BasePart.Touched](/docs/reference/engine/classes/BasePart#Touched)  events are tied to network ownership, meaning that a client can fire [Touched](/docs/reference/engine/classes/BasePart#Touched)  events on a [BasePart](/docs/reference/engine/classes/BasePart)  it owns and send it to the server, even if the server doesn't see it touch anything. For example, a client can make a sword deal damage to another player across the map by firing the event through script injections, so it's important to check the validity of such events fired by clients.

See [Security Tactics and Cheat Mitigation](/docs/scripting/security/security-tactics)  for detailed security tactics and cheat mitigation tactics for Roblox games.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
