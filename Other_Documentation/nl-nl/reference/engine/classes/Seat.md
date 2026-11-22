<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Seat -->

Seat | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [PVInstance](/docs/nl-nl/reference/engine/classes/PVInstance)
8. /
9. [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)
10. /
11. [FormFactorPart](/docs/nl-nl/reference/engine/classes/FormFactorPart)
12. /
13. [Part](/docs/nl-nl/reference/engine/classes/Part)
14. /
15. [Seat](/docs/nl-nl/reference/engine/classes/Seat)

Nederlands

Feedback

Engine-klasse

Seat

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Seat)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Disabled](#Disabled) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |
|

[Occupant](#Occupant) :[Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)

 |

Methoden

|

[Sit](#Sit) (humanoid :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

 |

Overgenomen leden

1  overgenomen van [Part](/docs/nl-nl/reference/engine/classes/Part)

2  overgenomen van [FormFactorPart](/docs/nl-nl/reference/engine/classes/FormFactorPart)

106  overgenomen van [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)

4  overgenomen van [PVInstance](/docs/nl-nl/reference/engine/classes/PVInstance)

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Detecteren van Zitplaats Bezetter

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

			print(player.Name .. " is gaan zitten")

			currentPlayer = player

			return

		end

	end

	if currentPlayer then

		print(currentPlayer.Name .. " is opgestaan")

		currentPlayer = nil

	end

end

seat:GetPropertyChangedSignal("Occupant"):Connect(onOccupantChanged)

```

---

API-referentie

Eigenschappen

Disabled

Parallel lezen

Mogelijkheden: Basic, AvatarBehavior

Toegang tot simulatie

Seat.Disabled :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Occupant

Alleen-lezen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: Basic, AvatarBehavior

Toegang tot simulatie

Seat.Occupant :[Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)

Feedback geven

---

Methoden

Sit

Mogelijkheden: Basic, AvatarBehavior

Seat:Sit (humanoid :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

Parameters

|

humanoid :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Teruggaves

()

Feedback geven

---

Ga naar

▼

Seat

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[Disabled](#Disabled)

[Occupant](#Occupant)

[Methoden](#methods)

[Sit()](#Sit)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
