<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/TweenBase -->

TweenBase | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [TweenBase](/docs/nl-nl/reference/engine/classes/TweenBase)

Nederlands

Feedback

Engine-klasse

TweenBase

Niet maakbaar

Niet doorzoekbaar

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/TweenBase)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[PlaybackState](#PlaybackState) :[Enum.PlaybackState](/docs/nl-nl/reference/engine/enums/PlaybackState)

 |
| --- | --- |

Methoden

|

[Cancel](#Cancel) () : ()

 |
|

[Pause](#Pause) () : ()

 |
|

[Play](#Play) () : ()

 |

Evenementen

|

[Completed](#Completed) (playbackState :  [Enum.PlaybackState](/docs/nl-nl/reference/engine/enums/PlaybackState) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Overgenomen door

[Tween](/docs/nl-nl/reference/engine/classes/Tween)

---

API-referentie

Eigenschappen

PlaybackState

Alleen-lezen

Niet gerepliceerd

Parallel lezen

TweenBase.PlaybackState :[Enum.PlaybackState](/docs/nl-nl/reference/engine/enums/PlaybackState)

Codevoorbeelden

Tween Afspeelstaat

```

local TweenService = game:GetService("TweenService")

local part = Instance.new("Part")

part.Position = Vector3.new(0, 10, 0)

part.Anchored = true

part.Parent = workspace

local goal = {}

goal.Orientation = Vector3.new(0, 90, 0)

local tweenInfo = TweenInfo.new(1, Enum.EasingStyle.Quad, Enum.EasingDirection.InOut, 2, true, 0.5)

local tween = TweenService:Create(part, tweenInfo, goal)

local function onPlaybackChanged()

	print("De status van de tween is veranderd naar:", tween.PlaybackState)

end

local playbackChanged = tween:GetPropertyChangedSignal("PlaybackState")

playbackChanged:Connect(onPlaybackChanged)

tween:Play()

```

Feedback geven

---

Methoden

Cancel

TweenBase:Cancel () : ()

Teruggaves

()

Codevoorbeelden

Tween Annuleren

```

local TweenService = game:GetService("TweenService")

local part = Instance.new("Part")

part.Position = Vector3.new(0, 10, 0)

part.Anchored = true

part.Parent = workspace

local goal = {}

goal.Position = Vector3.new(0, 50, 0)

local tweenInfo = TweenInfo.new(5)

local tween = TweenService:Create(part, tweenInfo, goal)

tween:Play()

task.wait(2.5)

tween:Cancel()

local playTick = tick()

tween:Play()

tween.Completed:Wait()

local timeTaken = tick() - playTick

print("Tween duurde " .. tostring(timeTaken) .. " secs om te voltooien")

-- De tween zal 5 seconden duren om te voltooien omdat de tween-variabelen zijn gereset door tween:Cancel()

```

Feedback geven

---

Pause

TweenBase:Pause () : ()

Teruggaves

()

Codevoorbeelden

Een Tween Pauzeren

```

local TweenService = game:GetService("TweenService")

local part = Instance.new("Part")

part.Position = Vector3.new(0, 10, 0)

part.Anchored = true

part.BrickColor = BrickColor.new("Heldere groen")

part.Parent = workspace

local goal = {}

goal.Position = Vector3.new(50, 10, 0)

local tweenInfo = TweenInfo.new(10, Enum.EasingStyle.Linear)

local tween = TweenService:Create(part, tweenInfo, goal)

tween:Play()

task.wait(3)

part.BrickColor = BrickColor.new("Heldere rood")

tween:Pause()

task.wait(2)

part.BrickColor = BrickColor.new("Heldere groen")

tween:Play()

```

Feedback geven

---

Play

TweenBase:Play () : ()

Teruggaves

()

Codevoorbeelden

Tween Creatie

```

local TweenService = game:GetService("TweenService")

local part = Instance.new("Part")

part.Position = Vector3.new(0, 10, 0)

part.Color = Color3.new(1, 0, 0)

part.Anchored = true

part.Parent = game.Workspace

local goal = {}

goal.Position = Vector3.new(10, 10, 0)

goal.Color = Color3.new(0, 1, 0)

local tweenInfo = TweenInfo.new(5)

local tween = TweenService:Create(part, tweenInfo, goal)

tween:Play()

```

Tween Conflict

```

local TweenService = game:GetService("TweenService")

local part = Instance.new("Part")

part.Position = Vector3.new(0, 10, 0)

part.Anchored = true

part.Parent = game.Workspace

local tweenInfo = TweenInfo.new(5)

-- maak twee conflicterende tweens (beide proberen het part.Position te animeren)

local tween1 = TweenService:Create(part, tweenInfo, { Position = Vector3.new(0, 10, 20) })

local tween2 = TweenService:Create(part, tweenInfo, { Position = Vector3.new(0, 30, 0) })

-- luister naar hun voltooiingsstatus

tween1.Completed:Connect(function(playbackState)

	print("tween1: " .. tostring(playbackState))

end)

tween2.Completed:Connect(function(playbackState)

	print("tween2: " .. tostring(playbackState))

end)

-- probeer ze beide af te spelen

tween1:Play()

tween2:Play()

```

Feedback geven

---

Evenementen

Completed

TweenBase.Completed (playbackState :[Enum.PlaybackState](/docs/nl-nl/reference/engine/enums/PlaybackState) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

playbackState :[Enum.PlaybackState](/docs/nl-nl/reference/engine/enums/PlaybackState)

 |

Codevoorbeelden

Tween Voltooid

```

local Players = game:GetService("Players")

local TweenService = game:GetService("TweenService")

local SLOW_DURATION = 10

local function slowCharacter(humanoid)

	local goal = {}

	goal.WalkSpeed = 0

	local tweenInfo = TweenInfo.new(SLOW_DURATION)

	local tweenSpeed = TweenService:Create(humanoid, tweenInfo, goal)

	tweenSpeed:Play()

	return tweenSpeed

end

local function onCharacterAdded(character)

	local humanoid = character:WaitForChild("Humanoid")

	local initialSpeed = humanoid.WalkSpeed

	local tweenSpeed = slowCharacter(humanoid)

	tweenSpeed.Completed:Wait()

	humanoid.WalkSpeed = initialSpeed

end

local function onPlayerAdded(player)

	player.CharacterAdded:Connect(onCharacterAdded)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Tween Conflict

```

local TweenService = game:GetService("TweenService")

local part = Instance.new("Part")

part.Position = Vector3.new(0, 10, 0)

part.Anchored = true

part.Parent = game.Workspace

local tweenInfo = TweenInfo.new(5)

-- maak twee conflicterende tweens (beide proberen het part.Position te animeren)

local tween1 = TweenService:Create(part, tweenInfo, { Position = Vector3.new(0, 10, 20) })

local tween2 = TweenService:Create(part, tweenInfo, { Position = Vector3.new(0, 30, 0) })

-- luister naar hun voltooiingsstatus

tween1.Completed:Connect(function(playbackState)

	print("tween1: " .. tostring(playbackState))

end)

tween2.Completed:Connect(function(playbackState)

	print("tween2: " .. tostring(playbackState))

end)

-- probeer ze beide af te spelen

tween1:Play()

tween2:Play()

```

Verifiëren of een Tween is Voltooid

```

local TweenService = game:GetService("TweenService")

local part = Instance.new("Part")

part.Position = Vector3.new(0, 50, 0)

part.Anchored = true

part.Parent = workspace

local goal = {}

goal.Position = Vector3.new(0, 0, 0)

local tweenInfo = TweenInfo.new(3)

local tween = TweenService:Create(part, tweenInfo, goal)

local function onTweenCompleted(playbackState)

	if playbackState == Enum.PlaybackState.Completed then

		local explosion = Instance.new("Explosion")

		explosion.Position = part.Position

		explosion.Parent = workspace

		part:Destroy()

		task.delay(2, function()

			if explosion then

				explosion:Destroy()

			end

		end)

	end

end

tween.Completed:Connect(onTweenCompleted)

tween:Play()

```

Feedback geven

---

Ga naar

▼

TweenBase

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[PlaybackState](#PlaybackState)

[Methoden](#methods)

[Cancel()](#Cancel)

[Pause()](#Pause)

[Play()](#Play)

[Evenementen](#events)

[Completed](#Completed)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
