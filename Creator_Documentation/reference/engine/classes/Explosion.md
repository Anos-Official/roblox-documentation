<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/Explosion -->

Explosion | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Explosion.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [Explosion](/docs/en-us/reference/engine/classes/Explosion)

English

Feedback

Engine Class

Explosion

---

## Summary

Properties

|

[BlastPressure](#BlastPressure) :[number](/docs/en-us/luau/numbers)

 |
| --- | --- |
|

[BlastRadius](#BlastRadius) :[number](/docs/en-us/luau/numbers)

 |
|

[DestroyJointRadiusPercent](#DestroyJointRadiusPercent) :[number](/docs/en-us/luau/numbers)

 |
|

[ExplosionType](#ExplosionType) :[Enum.ExplosionType](/docs/en-us/reference/engine/enums/ExplosionType)

 |
|

[LocalTransparencyModifier](#LocalTransparencyModifier) :[number](/docs/en-us/luau/numbers)

 |
|

[Position](#Position) :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

 |
|

[TimeScale](#TimeScale) :[number](/docs/en-us/luau/numbers)

 |
|

[Visible](#Visible) :[boolean](/docs/en-us/luau/booleans)

 |

Events

|

[Hit](#Hit) (part :  [BasePart](/docs/en-us/reference/engine/classes/BasePart) , distance :  [number](/docs/en-us/luau/numbers) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Explosion Instantiation

```

local explosion = Instance.new("Explosion")

explosion.BlastRadius = 60

explosion.ExplosionType = Enum.ExplosionType.Craters -- damages terrain

explosion.Position = Vector3.new(0, 10, 0)

explosion.Parent = workspace

```

---

API Reference

Properties

BlastPressure

Read Parallel

Capabilities: AvatarBehavior

Explosion.BlastPressure :[number](/docs/en-us/luau/numbers)

Code Samples

Custom Explosion

```

local function customExplosion(position, radius, maxDamage)

	local explosion = Instance.new("Explosion")

	explosion.BlastPressure = 0 -- this could be set higher to still apply velocity to parts

	explosion.DestroyJointRadiusPercent = 0 -- joints are safe

	explosion.BlastRadius = radius

	explosion.Position = position

	-- set up a table to track the models hit

	local modelsHit = {}

	-- listen for contact

	explosion.Hit:Connect(function(part, distance)

		local parentModel = part.Parent

		if parentModel then

			-- check to see if this model has already been hit

			if modelsHit[parentModel] then

				return

			end

			-- log this model as hit

			modelsHit[parentModel] = true

			-- look for a humanoid

			local humanoid = parentModel:FindFirstChild("Humanoid")

			if humanoid then

				local distanceFactor = distance / explosion.BlastRadius -- get the distance as a value between 0 and 1

				distanceFactor = 1 - distanceFactor -- flip the amount, so that lower == closer == more damage

				humanoid:TakeDamage(maxDamage * distanceFactor) -- TakeDamage to respect ForceFields

			end

		end

	end)

	explosion.Parent = game.Workspace

	-- Roblox removes explosions after a few seconds, but does not destroy them.

	-- To ensure our .Hit connection gets disconnected, destroy the explosion once it's removed.

	explosion.AncestryChanged:Connect(function()

		if not explosion.Parent then

			explosion:Destroy()

		end

	end)

end

customExplosion(Vector3.new(0, 10, 0), 12, 50)

```

Provide feedback

---

BlastRadius

Read Parallel

Capabilities: AvatarBehavior

Explosion.BlastRadius :[number](/docs/en-us/luau/numbers)

Code Samples

Explosion Instantiation

```

local explosion = Instance.new("Explosion")

explosion.BlastRadius = 60

explosion.ExplosionType = Enum.ExplosionType.Craters -- damages terrain

explosion.Position = Vector3.new(0, 10, 0)

explosion.Parent = workspace

```

Provide feedback

---

DestroyJointRadiusPercent

Read Parallel

Capabilities: AvatarBehavior

Explosion.DestroyJointRadiusPercent :[number](/docs/en-us/luau/numbers)

Code Samples

Non lethal explosions

```

local function onDescendantAdded(instance)

	if instance:IsA("Explosion") then

		local explosion = instance

		explosion.DestroyJointRadiusPercent = 0

		local destroyJointRadiusPercent = 1

		explosion.Hit:Connect(function(part, distance)

			-- check the part is in range to break joints

			if distance <= destroyJointRadiusPercent * explosion.BlastRadius then

				-- make sure the part does not belong to a character

				if not game.Players:GetPlayerFromCharacter(part.Parent) then

					part:BreakJoints()

				end

			end

		end)

	end

end

workspace.DescendantAdded:Connect(onDescendantAdded)

```

Custom Explosion

```

local function customExplosion(position, radius, maxDamage)

	local explosion = Instance.new("Explosion")

	explosion.BlastPressure = 0 -- this could be set higher to still apply velocity to parts

	explosion.DestroyJointRadiusPercent = 0 -- joints are safe

	explosion.BlastRadius = radius

	explosion.Position = position

	-- set up a table to track the models hit

	local modelsHit = {}

	-- listen for contact

	explosion.Hit:Connect(function(part, distance)

		local parentModel = part.Parent

		if parentModel then

			-- check to see if this model has already been hit

			if modelsHit[parentModel] then

				return

			end

			-- log this model as hit

			modelsHit[parentModel] = true

			-- look for a humanoid

			local humanoid = parentModel:FindFirstChild("Humanoid")

			if humanoid then

				local distanceFactor = distance / explosion.BlastRadius -- get the distance as a value between 0 and 1

				distanceFactor = 1 - distanceFactor -- flip the amount, so that lower == closer == more damage

				humanoid:TakeDamage(maxDamage * distanceFactor) -- TakeDamage to respect ForceFields

			end

		end

	end)

	explosion.Parent = game.Workspace

	-- Roblox removes explosions after a few seconds, but does not destroy them.

	-- To ensure our .Hit connection gets disconnected, destroy the explosion once it's removed.

	explosion.AncestryChanged:Connect(function()

		if not explosion.Parent then

			explosion:Destroy()

		end

	end)

end

customExplosion(Vector3.new(0, 10, 0), 12, 50)

```

Provide feedback

---

ExplosionType

Read Parallel

Capabilities: AvatarBehavior

Explosion.ExplosionType :[Enum.ExplosionType](/docs/en-us/reference/engine/enums/ExplosionType)

Code Samples

Stop Explosions from Damaging Terrain

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

Provide feedback

---

LocalTransparencyModifier

Hidden

Not Replicated

Read Parallel

Capabilities: AvatarBehavior

Explosion.LocalTransparencyModifier :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Position

Read Parallel

Capabilities: AvatarBehavior

Explosion.Position :[Vector3](/docs/en-us/reference/engine/datatypes/Vector3)

Code Samples

Explosion Instantiation

```

local explosion = Instance.new("Explosion")

explosion.BlastRadius = 60

explosion.ExplosionType = Enum.ExplosionType.Craters -- damages terrain

explosion.Position = Vector3.new(0, 10, 0)

explosion.Parent = workspace

```

Provide feedback

---

TimeScale

Read Parallel

Capabilities: AvatarBehavior

Explosion.TimeScale :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Visible

Read Parallel

Capabilities: AvatarBehavior

Explosion.Visible :[boolean](/docs/en-us/luau/booleans)

Code Samples

Explosion Custom Visuals

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

Provide feedback

---

Events

Hit

Capabilities: AvatarBehavior

Explosion.Hit (

part :[BasePart](/docs/en-us/reference/engine/classes/BasePart) , distance :[number](/docs/en-us/luau/numbers)

) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

part :[BasePart](/docs/en-us/reference/engine/classes/BasePart)

 |
|

distance :[number](/docs/en-us/luau/numbers)

 |

Code Samples

Custom Explosion

```

local function customExplosion(position, radius, maxDamage)

	local explosion = Instance.new("Explosion")

	explosion.BlastPressure = 0 -- this could be set higher to still apply velocity to parts

	explosion.DestroyJointRadiusPercent = 0 -- joints are safe

	explosion.BlastRadius = radius

	explosion.Position = position

	-- set up a table to track the models hit

	local modelsHit = {}

	-- listen for contact

	explosion.Hit:Connect(function(part, distance)

		local parentModel = part.Parent

		if parentModel then

			-- check to see if this model has already been hit

			if modelsHit[parentModel] then

				return

			end

			-- log this model as hit

			modelsHit[parentModel] = true

			-- look for a humanoid

			local humanoid = parentModel:FindFirstChild("Humanoid")

			if humanoid then

				local distanceFactor = distance / explosion.BlastRadius -- get the distance as a value between 0 and 1

				distanceFactor = 1 - distanceFactor -- flip the amount, so that lower == closer == more damage

				humanoid:TakeDamage(maxDamage * distanceFactor) -- TakeDamage to respect ForceFields

			end

		end

	end)

	explosion.Parent = game.Workspace

	-- Roblox removes explosions after a few seconds, but does not destroy them.

	-- To ensure our .Hit connection gets disconnected, destroy the explosion once it's removed.

	explosion.AncestryChanged:Connect(function()

		if not explosion.Parent then

			explosion:Destroy()

		end

	end)

end

customExplosion(Vector3.new(0, 10, 0), 12, 50)

```

Provide feedback

---

Jump to

▼

Explosion

[Summary](#summary)

[Properties](#summary-properties)

[Events](#summary-events)

[Properties](#properties)

[BlastPressure](#BlastPressure)

[BlastRadius](#BlastRadius)

[DestroyJointRadiusPercent](#DestroyJointRadiusPercent)

[ExplosionType](#ExplosionType)

[LocalTransparencyModifier](#LocalTransparencyModifier)

[Position](#Position)

[TimeScale](#TimeScale)

[Visible](#Visible)

[Events](#events)

[Hit](#Hit)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
