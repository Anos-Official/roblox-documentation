<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/ClickDetector -->

ClickDetector | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/ClickDetector.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [ClickDetector](/docs/en-us/reference/engine/classes/ClickDetector)

English

Feedback

Engine Class

ClickDetector

---

## Summary

Properties

|

[CursorIcon](#CursorIcon) : ContentId

 |
| --- | --- |
|

[CursorIconContent](#CursorIconContent) :[Content](/docs/en-us/reference/engine/datatypes/Content)

 |
|

[MaxActivationDistance](#MaxActivationDistance) :[number](/docs/en-us/luau/numbers)

 |

Events

|

[MouseClick](#MouseClick) (playerWhoClicked :  [Player](/docs/en-us/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[mouseClick](#mouseClick) (playerWhoClicked :  [Player](/docs/en-us/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Deprecated

 |
|

[MouseHoverEnter](#MouseHoverEnter) (playerWhoHovered :  [Player](/docs/en-us/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[MouseHoverLeave](#MouseHoverLeave) (playerWhoHovered :  [Player](/docs/en-us/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[RightMouseClick](#RightMouseClick) (playerWhoClicked :  [Player](/docs/en-us/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Inherited by

[DragDetector](/docs/en-us/reference/engine/classes/DragDetector)

Code Samples

ClickDetector Example

```

local clickDetector = script.Parent

local function onClicked(player)

	-- Show a message to the player

	local msg = Instance.new("Message")

	msg.Parent = player:FindFirstChild("PlayerGui")

	msg.Text = "Hello, " .. player.Name

	wait(2.5)

	msg:Destroy()

end

-- Connect the function to the MouseClick event

clickDetector.MouseClick:Connect(onClicked)

```

Part Anchored Toggle

```

local part = script.Parent

-- Create a ClickDetector so we can tell when the part is clicked

local cd = Instance.new("ClickDetector", part)

-- This function updates how the part looks based on its Anchored state

local function updateVisuals()

	if part.Anchored then

		-- When the part is anchored...

		part.BrickColor = BrickColor.new("Bright red")

		part.Material = Enum.Material.DiamondPlate

	else

		-- When the part is unanchored...

		part.BrickColor = BrickColor.new("Bright yellow")

		part.Material = Enum.Material.Wood

	end

end

local function onToggle()

	-- Toggle the anchored property

	part.Anchored = not part.Anchored

	-- Update visual state of the brick

	updateVisuals()

end

-- Update, then start listening for clicks

updateVisuals()

cd.MouseClick:Connect(onToggle)

```

---

API Reference

Properties

CursorIcon

Read Parallel

Capabilities: Input

ClickDetector.CursorIcon : ContentId

Provide feedback

---

CursorIconContent

Read Parallel

Capabilities: Input

ClickDetector.CursorIconContent :[Content](/docs/en-us/reference/engine/datatypes/Content)

Provide feedback

---

MaxActivationDistance

Read Parallel

Capabilities: Input

ClickDetector.MaxActivationDistance :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Events

MouseClick

Capabilities: Input

ClickDetector.MouseClick (playerWhoClicked :[Player](/docs/en-us/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

playerWhoClicked :[Player](/docs/en-us/reference/engine/classes/Player)

 |

Provide feedback

---

mouseClick

Deprecated

Show details

---

MouseHoverEnter

Capabilities: Input

ClickDetector.MouseHoverEnter (playerWhoHovered :[Player](/docs/en-us/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

playerWhoHovered :[Player](/docs/en-us/reference/engine/classes/Player)

 |

Code Samples

Hovering Over and Off a ClickDetector

```

local clickDetector = script.Parent:FindFirstChildOfClass("ClickDetector")

clickDetector.MouseHoverEnter:Connect(function(player)

	print(player.Name .. " hovered over my parent!")

end)

clickDetector.MouseHoverLeave:Connect(function(player)

	print(player.Name .. " hovered off my parent!")

end)

```

Provide feedback

---

MouseHoverLeave

Capabilities: Input

ClickDetector.MouseHoverLeave (playerWhoHovered :[Player](/docs/en-us/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

playerWhoHovered :[Player](/docs/en-us/reference/engine/classes/Player)

 |

Code Samples

Hovering Over and Off a ClickDetector

```

local clickDetector = script.Parent:FindFirstChildOfClass("ClickDetector")

clickDetector.MouseHoverEnter:Connect(function(player)

	print(player.Name .. " hovered over my parent!")

end)

clickDetector.MouseHoverLeave:Connect(function(player)

	print(player.Name .. " hovered off my parent!")

end)

```

Provide feedback

---

RightMouseClick

Capabilities: Input

ClickDetector.RightMouseClick (playerWhoClicked :[Player](/docs/en-us/reference/engine/classes/Player) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

playerWhoClicked :[Player](/docs/en-us/reference/engine/classes/Player)

 |

Provide feedback

---

Jump to

▼

ClickDetector

[Summary](#summary)

[Properties](#summary-properties)

[Events](#summary-events)

[Properties](#properties)

[CursorIcon](#CursorIcon)

[CursorIconContent](#CursorIconContent)

[MaxActivationDistance](#MaxActivationDistance)

[Events](#events)

[MouseClick](#MouseClick)

[mouseClick](#mouseClick)

[MouseHoverEnter](#MouseHoverEnter)

[MouseHoverLeave](#MouseHoverLeave)

[RightMouseClick](#RightMouseClick)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
