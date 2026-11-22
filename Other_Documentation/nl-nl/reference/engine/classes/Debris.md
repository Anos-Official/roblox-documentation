<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Debris -->

Debris | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [Debris](/docs/nl-nl/reference/engine/classes/Debris)

Nederlands

Feedback

Engine-klasse

Debris

Niet maakbaar

Service

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Debris)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[MaxItems](#MaxItems) :[number](/docs/nl-nl/luau/numbers)

Verouderd

 |
| --- | --- |

Methoden

|

[AddItem](#AddItem) (item :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) , lifetime :  [number](/docs/nl-nl/luau/numbers) ) : ()

 |
|

[addItem](#addItem) (item :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) , lifetime :  [number](/docs/nl-nl/luau/numbers) ) : ()

Verouderd

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Debris VoegItemToe

```

local Debris = game:GetService("Debris")

local ball = Instance.new("Part")

ball.Anchored = false

ball.Shape = Enum.PartType.Ball

ball.TopSurface = Enum.SurfaceType.Smooth

ball.BottomSurface = Enum.SurfaceType.Smooth

ball.Size = Vector3.new(1, 1, 1)

local RNG = Random.new()

local MAX_VELOCITY = 10

while true do

	local newBall = ball:Clone()

	newBall.BrickColor = BrickColor.random()

	newBall.CFrame = CFrame.new(0, 30, 0)

	newBall.Velocity =

		Vector3.new(RNG:NextNumber(-MAX_VELOCITY, MAX_VELOCITY), 0, RNG:NextNumber(-MAX_VELOCITY, MAX_VELOCITY))

	newBall.Parent = game.Workspace

	Debris:AddItem(newBall, 2)

	task.wait(0.1)

end

```

---

API-referentie

Eigenschappen

MaxItems

Verouderd

Details weergeven

---

Methoden

AddItem

Mogelijkheden: Basic

Debris:AddItem (

item :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) , lifetime :[number](/docs/nl-nl/luau/numbers)

) : ()

Parameters

|

item :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
|

lifetime :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 10 |

Teruggaves

()

Codevoorbeelden

Debris VoegItemToe

```

local Debris = game:GetService("Debris")

local ball = Instance.new("Part")

ball.Anchored = false

ball.Shape = Enum.PartType.Ball

ball.TopSurface = Enum.SurfaceType.Smooth

ball.BottomSurface = Enum.SurfaceType.Smooth

ball.Size = Vector3.new(1, 1, 1)

local RNG = Random.new()

local MAX_VELOCITY = 10

while true do

	local newBall = ball:Clone()

	newBall.BrickColor = BrickColor.random()

	newBall.CFrame = CFrame.new(0, 30, 0)

	newBall.Velocity =

		Vector3.new(RNG:NextNumber(-MAX_VELOCITY, MAX_VELOCITY), 0, RNG:NextNumber(-MAX_VELOCITY, MAX_VELOCITY))

	newBall.Parent = game.Workspace

	Debris:AddItem(newBall, 2)

	task.wait(0.1)

end

```

Feedback geven

---

addItem

Verouderd

Details weergeven

---

Ga naar

▼

Debris

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[MaxItems](#MaxItems)

[Methoden](#methods)

[AddItem()](#AddItem)

[addItem()](#addItem)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
