<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/ClickDetector -->

ClickDetector | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [ClickDetector](/docs/nl-nl/reference/engine/classes/ClickDetector)

Nederlands

Feedback

Engine-klasse

ClickDetector

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/ClickDetector)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[CursorIcon](#CursorIcon) : ContentId

 |
| --- | --- |
|

[CursorIconContent](#CursorIconContent) :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

 |
|

[MaxActivationDistance](#MaxActivationDistance) :[number](/docs/nl-nl/luau/numbers)

 |

Evenementen

|

[MouseClick](#MouseClick) (playerWhoClicked :  [Player](/docs/nl-nl/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[mouseClick](#mouseClick) (playerWhoClicked :  [Player](/docs/nl-nl/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Verouderd

 |
|

[MouseHoverEnter](#MouseHoverEnter) (playerWhoHovered :  [Player](/docs/nl-nl/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[MouseHoverLeave](#MouseHoverLeave) (playerWhoHovered :  [Player](/docs/nl-nl/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |
|

[RightMouseClick](#RightMouseClick) (playerWhoClicked :  [Player](/docs/nl-nl/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Overgenomen door

[DragDetector](/docs/nl-nl/reference/engine/classes/DragDetector)

Codevoorbeelden

Voorbeeld ClickDetector

```

local clickDetector = script.Parent

local function onClicked(player)

	-- Toon een bericht aan de speler

	local msg = Instance.new("Message")

	msg.Parent = player:FindFirstChild("PlayerGui")

	msg.Text = "Hallo, " .. player.Name

	wait(2.5)

	msg:Destroy()

end

-- Verbind de functie met de MouseClick gebeurtenis

clickDetector.MouseClick:Connect(onClicked)

```

Deel Verankerd Wisselen

```

local part = script.Parent

-- Maak een ClickDetector zodat we kunnen zien wanneer het deel wordt geklikt

local cd = Instance.new("ClickDetector", part)

-- Deze functie werkt bij hoe het deel eruit ziet op basis van de verankerde staat

local function updateVisuals()

	if part.Anchored then

		-- Wanneer het deel verankerd is...

		part.BrickColor = BrickColor.new("Heldere rood")

		part.Material = Enum.Material.DiamondPlate

	else

		-- Wanneer het deel niet verankerd is...

		part.BrickColor = BrickColor.new("Heldere geel")

		part.Material = Enum.Material.Wood

	end

end

local function onToggle()

	-- Wissel de verankerde eigenschap

	part.Anchored = not part.Anchored

	-- Werk de visuele staat van de baksteen bij

	updateVisuals()

end

-- Werk bij, en begin dan met luisteren naar klikken

updateVisuals()

cd.MouseClick:Connect(onToggle)

```

---

API-referentie

Eigenschappen

CursorIcon

Parallel lezen

Mogelijkheden: Input

ClickDetector.CursorIcon : ContentId

Feedback geven

---

CursorIconContent

Parallel lezen

Mogelijkheden: Input

ClickDetector.CursorIconContent :[Content](/docs/nl-nl/reference/engine/datatypes/Content)

Feedback geven

---

MaxActivationDistance

Parallel lezen

Mogelijkheden: Input

ClickDetector.MaxActivationDistance :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Evenementen

MouseClick

Mogelijkheden: Input

ClickDetector.MouseClick (playerWhoClicked :[Player](/docs/nl-nl/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

playerWhoClicked :[Player](/docs/nl-nl/reference/engine/classes/Player)

 |

Feedback geven

---

mouseClick

Verouderd

Details weergeven

---

MouseHoverEnter

Mogelijkheden: Input

ClickDetector.MouseHoverEnter (playerWhoHovered :[Player](/docs/nl-nl/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

playerWhoHovered :[Player](/docs/nl-nl/reference/engine/classes/Player)

 |

Codevoorbeelden

Hoveren Over en Af van een ClickDetector

```

local clickDetector = script.Parent:FindFirstChildOfClass("ClickDetector")

clickDetector.MouseHoverEnter:Connect(function(player)

	print(player.Name .. " heeft over mijn ouder heen gehangen!")

end)

clickDetector.MouseHoverLeave:Connect(function(player)

	print(player.Name .. " heeft van mijn ouder afgegaan!")

end)

```

Feedback geven

---

MouseHoverLeave

Mogelijkheden: Input

ClickDetector.MouseHoverLeave (playerWhoHovered :[Player](/docs/nl-nl/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

playerWhoHovered :[Player](/docs/nl-nl/reference/engine/classes/Player)

 |

Codevoorbeelden

Hoveren Over en Af van een ClickDetector

```

local clickDetector = script.Parent:FindFirstChildOfClass("ClickDetector")

clickDetector.MouseHoverEnter:Connect(function(player)

	print(player.Name .. " heeft over mijn ouder heen gehangen!")

end)

clickDetector.MouseHoverLeave:Connect(function(player)

	print(player.Name .. " heeft van mijn ouder afgegaan!")

end)

```

Feedback geven

---

RightMouseClick

Mogelijkheden: Input

ClickDetector.RightMouseClick (playerWhoClicked :[Player](/docs/nl-nl/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

playerWhoClicked :[Player](/docs/nl-nl/reference/engine/classes/Player)

 |

Feedback geven

---

Ga naar

▼

ClickDetector

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[CursorIcon](#CursorIcon)

[CursorIconContent](#CursorIconContent)

[MaxActivationDistance](#MaxActivationDistance)

[Evenementen](#events)

[MouseClick](#MouseClick)

[mouseClick](#mouseClick)

[MouseHoverEnter](#MouseHoverEnter)

[MouseHoverLeave](#MouseHoverLeave)

[RightMouseClick](#RightMouseClick)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
