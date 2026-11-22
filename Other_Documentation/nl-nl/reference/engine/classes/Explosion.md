<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/Explosion -->

Explosion | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [Explosion](/docs/nl-nl/reference/engine/classes/Explosion)

Nederlands

Feedback

Engine-klasse

Explosion

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/Explosion)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[BlastPressure](#BlastPressure) :[number](/docs/nl-nl/luau/numbers)

 |
| --- | --- |
|

[BlastRadius](#BlastRadius) :[number](/docs/nl-nl/luau/numbers)

 |
|

[DestroyJointRadiusPercent](#DestroyJointRadiusPercent) :[number](/docs/nl-nl/luau/numbers)

 |
|

[ExplosionType](#ExplosionType) :[Enum.ExplosionType](/docs/nl-nl/reference/engine/enums/ExplosionType)

 |
|

[LocalTransparencyModifier](#LocalTransparencyModifier) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Position](#Position) :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

 |
|

[TimeScale](#TimeScale) :[number](/docs/nl-nl/luau/numbers)

 |
|

[Visible](#Visible) :[boolean](/docs/nl-nl/luau/booleans)

 |

Evenementen

|

[Hit](#Hit) (part :  [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) , distance :  [number](/docs/nl-nl/luau/numbers) ) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

Explosie Instantiatie

```

local explosion = Instance.new("Explosion")

explosion.BlastRadius = 60

explosion.ExplosionType = Enum.ExplosionType.Craters -- beschadigt terrein

explosion.Position = Vector3.new(0, 10, 0)

explosion.Parent = workspace

```

---

API-referentie

Eigenschappen

BlastPressure

Parallel lezen

Mogelijkheden: AvatarBehavior

Explosion.BlastPressure :[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

Aangepaste Explosie

```

local function customExplosion(position, radius, maxDamage)

	local explosion = Instance.new("Explosion")

	explosion.BlastPressure = 0 -- dit kan hoger worden ingesteld om nog steeds snelheid op onderdelen toe te passen

	explosion.DestroyJointRadiusPercent = 0 -- gewrichten zijn veilig

	explosion.BlastRadius = radius

	explosion.Position = position

	-- stel een tabel in om de modellen die geraakt zijn bij te houden

	local modelsHit = {}

	-- luister naar contact

	explosion.Hit:Connect(function(part, distance)

		local parentModel = part.Parent

		if parentModel then

			-- controleer of dit model al is geraakt

			if modelsHit[parentModel] then

				return

			end

			-- log dit model als geraakt

			modelsHit[parentModel] = true

			-- zoek naar een humanoïde

			local humanoid = parentModel:FindFirstChild("Humanoid")

			if humanoid then

				local distanceFactor = distance / explosion.BlastRadius -- krijg de afstand als een waarde tussen 0 en 1

				distanceFactor = 1 - distanceFactor -- draai de hoeveelheid om, zodat lager == dichterbij == meer schade

				humanoid:TakeDamage(maxDamage * distanceFactor) -- TakeDamage om rekening te houden met ForceFields

			end

		end

	end)

	explosion.Parent = game.Workspace

	-- Roblox verwijdert explosies na een paar seconden, maar vernietigt ze niet.

	-- Om ervoor te zorgen dat onze .Hit verbinding wordt losgekoppeld, vernietig de explosie zodra deze is verwijderd.

	explosion.AncestryChanged:Connect(function()

		if not explosion.Parent then

			explosion:Destroy()

		end

	end)

end

customExplosion(Vector3.new(0, 10, 0), 12, 50)

```

Feedback geven

---

BlastRadius

Parallel lezen

Mogelijkheden: AvatarBehavior

Explosion.BlastRadius :[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

Explosie Instantiatie

```

local explosion = Instance.new("Explosion")

explosion.BlastRadius = 60

explosion.ExplosionType = Enum.ExplosionType.Craters -- beschadigt terrein

explosion.Position = Vector3.new(0, 10, 0)

explosion.Parent = workspace

```

Feedback geven

---

DestroyJointRadiusPercent

Parallel lezen

Mogelijkheden: AvatarBehavior

Explosion.DestroyJointRadiusPercent :[number](/docs/nl-nl/luau/numbers)

Codevoorbeelden

Niet dodelijke explosies

```

local function onDescendantAdded(instance)

	if instance:IsA("Explosion") then

		local explosion = instance

		explosion.DestroyJointRadiusPercent = 0

		local destroyJointRadiusPercent = 1

		explosion.Hit:Connect(function(part, distance)

			-- controleer of het onderdeel binnen bereik is om gewrichten te breken

			if distance <= destroyJointRadiusPercent * explosion.BlastRadius then

				-- zorg ervoor dat het onderdeel niet toebehoort aan een karakter

				if not game.Players:GetPlayerFromCharacter(part.Parent) then

					part:BreakJoints()

				end

			end

		end)

	end

end

workspace.DescendantAdded:Connect(onDescendantAdded)

```

Aangepaste Explosie

```

local function customExplosion(position, radius, maxDamage)

	local explosion = Instance.new("Explosion")

	explosion.BlastPressure = 0 -- dit kan hoger worden ingesteld om nog steeds snelheid op onderdelen toe te passen

	explosion.DestroyJointRadiusPercent = 0 -- gewrichten zijn veilig

	explosion.BlastRadius = radius

	explosion.Position = position

	-- stel een tabel in om de modellen die geraakt zijn bij te houden

	local modelsHit = {}

	-- luister naar contact

	explosion.Hit:Connect(function(part, distance)

		local parentModel = part.Parent

		if parentModel then

			-- controleer of dit model al is geraakt

			if modelsHit[parentModel] then

				return

			end

			-- log dit model als geraakt

			modelsHit[parentModel] = true

			-- zoek naar een humanoïde

			local humanoid = parentModel:FindFirstChild("Humanoid")

			if humanoid then

				local distanceFactor = distance / explosion.BlastRadius -- krijg de afstand als een waarde tussen 0 en 1

				distanceFactor = 1 - distanceFactor -- draai de hoeveelheid om, zodat lager == dichterbij == meer schade

				humanoid:TakeDamage(maxDamage * distanceFactor) -- TakeDamage om rekening te houden met ForceFields

			end

		end

	end)

	explosion.Parent = game.Workspace

	-- Roblox verwijdert explosies na een paar seconden, maar vernietigt ze niet.

	-- Om ervoor te zorgen dat onze .Hit verbinding wordt losgekoppeld, vernietig de explosie zodra deze is verwijderd.

	explosion.AncestryChanged:Connect(function()

		if not explosion.Parent then

			explosion:Destroy()

		end

	end)

end

customExplosion(Vector3.new(0, 10, 0), 12, 50)

```

Feedback geven

---

ExplosionType

Parallel lezen

Mogelijkheden: AvatarBehavior

Explosion.ExplosionType :[Enum.ExplosionType](/docs/nl-nl/reference/engine/enums/ExplosionType)

Codevoorbeelden

Stop Explosies van het Beschadigen van Terrein

```

local function onDescendantAdded(instance)

	if instance:IsA("Explosion") then

		instance.ExplosionType = Enum.ExplosionType.NoCraters

		instance:GetPropertyChangedSignal("ExplosionType"):Connect(function()

			instance.ExplosionType = Enum.ExplosionType.NoCraters

		end)

	end

end

workspace.DescendantAdded:Connect(onDescendantAdded)

```

Feedback geven

---

LocalTransparencyModifier

Verborgen

Niet gerepliceerd

Parallel lezen

Mogelijkheden: AvatarBehavior

Explosion.LocalTransparencyModifier :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Position

Parallel lezen

Mogelijkheden: AvatarBehavior

Explosion.Position :[Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)

Codevoorbeelden

Explosie Instantiatie

```

local explosion = Instance.new("Explosion")

explosion.BlastRadius = 60

explosion.ExplosionType = Enum.ExplosionType.Craters -- beschadigt terrein

explosion.Position = Vector3.new(0, 10, 0)

explosion.Parent = workspace

```

Feedback geven

---

TimeScale

Parallel lezen

Mogelijkheden: AvatarBehavior

Explosion.TimeScale :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Visible

Parallel lezen

Mogelijkheden: AvatarBehavior

Explosion.Visible :[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

Explosie Aangepaste Visuals

```

local function customExplosion(position)

	local explosion = Instance.new("Explosion")

	explosion.Position = position

	explosion.Visible = false

	local attachment = Instance.new("Attachment")

	attachment.Position = position

	attachment.Parent = workspace.Terrain

	local particleEmitter = Instance.new("ParticleEmitter")

	particleEmitter.Enabled = false

	particleEmitter.Parent = attachment

	particleEmitter.Speed = NumberRange.new(5, 30)

	particleEmitter.SpreadAngle = Vector2.new(-90, 90)

	explosion.Parent = workspace

	particleEmitter:Emit(20)

	task.delay(5, function()

		if attachment then

			attachment:Destroy()

		end

	end)

end

customExplosion(Vector3.new(0, 10, 0))

```

Feedback geven

---

Evenementen

Hit

Mogelijkheden: AvatarBehavior

Explosion.Hit (

part :[BasePart](/docs/nl-nl/reference/engine/classes/BasePart) , distance :[number](/docs/nl-nl/luau/numbers)

) :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

part :[BasePart](/docs/nl-nl/reference/engine/classes/BasePart)

 |
|

distance :[number](/docs/nl-nl/luau/numbers)

 |

Codevoorbeelden

Aangepaste Explosie

```

local function customExplosion(position, radius, maxDamage)

	local explosion = Instance.new("Explosion")

	explosion.BlastPressure = 0 -- dit kan hoger worden ingesteld om nog steeds snelheid op onderdelen toe te passen

	explosion.DestroyJointRadiusPercent = 0 -- gewrichten zijn veilig

	explosion.BlastRadius = radius

	explosion.Position = position

	-- stel een tabel in om de modellen die geraakt zijn bij te houden

	local modelsHit = {}

	-- luister naar contact

	explosion.Hit:Connect(function(part, distance)

		local parentModel = part.Parent

		if parentModel then

			-- controleer of dit model al is geraakt

			if modelsHit[parentModel] then

				return

			end

			-- log dit model als geraakt

			modelsHit[parentModel] = true

			-- zoek naar een humanoïde

			local humanoid = parentModel:FindFirstChild("Humanoid")

			if humanoid then

				local distanceFactor = distance / explosion.BlastRadius -- krijg de afstand als een waarde tussen 0 en 1

				distanceFactor = 1 - distanceFactor -- draai de hoeveelheid om, zodat lager == dichterbij == meer schade

				humanoid:TakeDamage(maxDamage * distanceFactor) -- TakeDamage om rekening te houden met ForceFields

			end

		end

	end)

	explosion.Parent = game.Workspace

	-- Roblox verwijdert explosies na een paar seconden, maar vernietigt ze niet.

	-- Om ervoor te zorgen dat onze .Hit verbinding wordt losgekoppeld, vernietig de explosie zodra deze is verwijderd.

	explosion.AncestryChanged:Connect(function()

		if not explosion.Parent then

			explosion:Destroy()

		end

	end)

end

customExplosion(Vector3.new(0, 10, 0), 12, 50)

```

Feedback geven

---

Ga naar

▼

Explosion

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Evenementen](#summary-events)

[Eigenschappen](#properties)

[BlastPressure](#BlastPressure)

[BlastRadius](#BlastRadius)

[DestroyJointRadiusPercent](#DestroyJointRadiusPercent)

[ExplosionType](#ExplosionType)

[LocalTransparencyModifier](#LocalTransparencyModifier)

[Position](#Position)

[TimeScale](#TimeScale)

[Visible](#Visible)

[Evenementen](#events)

[Hit](#Hit)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
