<!-- Source: https://create.roblox.com/docs/reference/engine/classes/Seat -->

Seat | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Seat.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [PVInstance](/docs/reference/engine/classes/PVInstance)
8. /
9. [BasePart](/docs/reference/engine/classes/BasePart)
10. /
11. [FormFactorPart](/docs/reference/engine/classes/FormFactorPart)
12. /
13. [Part](/docs/reference/engine/classes/Part)
14. /
15. [Seat](/docs/reference/engine/classes/Seat)

English

Feedback

Engine Class

Seat

---

## Summary

Properties

|

[Disabled](#Disabled) :[boolean](/docs/luau/booleans)

 |
| --- | --- |
|

[Occupant](#Occupant) :[Humanoid](/docs/reference/engine/classes/Humanoid)

 |

Methods

|

[Sit](#Sit) (humanoid :  [Instance](/docs/reference/engine/datatypes/Instance) ) : ()

 |

Inherited Members

1  inherited from [Part](/docs/reference/engine/classes/Part)

2  inherited from [FormFactorPart](/docs/reference/engine/classes/FormFactorPart)

106  inherited from [BasePart](/docs/reference/engine/classes/BasePart)

4  inherited from [PVInstance](/docs/reference/engine/classes/PVInstance)

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

Detecting Seat Occupant

```

local Players = game:GetService("Players")

local seat = Instance.new("Seat")

seat.Anchored = true

seat.Position = Vector3.new(0, 1, 0)

seat.Parent = workspace

local currentPlayer = nil

local function onOccupantChanged()

	local humanoid = seat.Occupant

	if humanoid then

		local character = humanoid.Parent

		local player = Players:GetPlayerFromCharacter(character)

		if player then

			print(player.Name .. " has sat down")

			currentPlayer = player

			return

		end

	end

	if currentPlayer then

		print(currentPlayer.Name .. " has got up")

		currentPlayer = nil

	end

end

seat:GetPropertyChangedSignal("Occupant"):Connect(onOccupantChanged)

```

---

API Reference

Properties

Disabled

Read Parallel

Capabilities: Basic, AvatarBehavior

Simulation Access

Seat.Disabled :[boolean](/docs/luau/booleans)

Provide feedback

---

Occupant

Read Only

Not Replicated

Read Parallel

Capabilities: Basic, AvatarBehavior

Simulation Access

Seat.Occupant :[Humanoid](/docs/reference/engine/classes/Humanoid)

Provide feedback

---

Methods

Sit

Capabilities: Basic, AvatarBehavior

Seat:Sit (humanoid :[Instance](/docs/reference/engine/datatypes/Instance) ) : ()

Parameters

|

humanoid :[Instance](/docs/reference/engine/datatypes/Instance)

 |

Returns

()

Provide feedback

---

Jump to

▼

Seat

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[Disabled](#Disabled)

[Occupant](#Occupant)

[Methods](#methods)

[Sit()](#Sit)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
