<!-- Source: https://create.roblox.com/docs/reference/engine/classes/ForceField -->

ForceField | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/ForceField.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [ForceField](/docs/reference/engine/classes/ForceField)

English

Feedback

Engine Class

ForceField

---

## Summary

Properties

|

[Visible](#Visible) :[boolean](/docs/luau/booleans)

 |
| --- | --- |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

ForceField Instantiation

```

local Players = game:GetService("Players")

local FORCE_FIELD_DURATION = 15

local function giveForcefield(player, duration)

	local character = player.Character

	if character then

		local forceField = Instance.new("ForceField")

		forceField.Visible = true

		forceField.Parent = character

		if duration then

			task.delay(duration, function()

				if forceField then

					forceField:Destroy()

				end

			end)

		end

	end

end

local function onPlayerAdded(player)

	player.CharacterAdded:Connect(function(_character)

		giveForcefield(player, FORCE_FIELD_DURATION)

	end)

end

Players.PlayerAdded(onPlayerAdded)

```

---

API Reference

Properties

Visible

Read Parallel

Capabilities: AvatarBehavior

ForceField.Visible :[boolean](/docs/luau/booleans)

Code Samples

Custom ForceField Effect

```

local Players = game:GetService("Players")

local FORCE_FIELD_DURATION = 15

local function createCustomForcefield(player, duration)

	local character = player.Character

	if character then

		local humanoid = character:FindFirstChild("Humanoid")

		if humanoid then

			-- find the torso

			local torsoName = humanoid.RigType == Enum.HumanoidRigType.R15 and "UpperTorso" or "Torso"

			local torso = character:FindFirstChild(torsoName)

			if torso then

				-- create a forcefield

				local forceField = Instance.new("ForceField")

				forceField.Visible = false -- not visible

				-- create a particle effect

				local particleEmitter = Instance.new("ParticleEmitter")

				particleEmitter.Enabled = true

				particleEmitter.Parent = torso

				-- listen for the forcefield being removed

				forceField.AncestryChanged:Connect(function(_child, parent)

					if not parent then

						if particleEmitter and particleEmitter.Parent then

							particleEmitter:Destroy()

						end

					end

				end)

				-- parent the forcefield and set it to expire

				forceField.Parent = character

				if duration then

					task.delay(duration, function()

						if forceField then

							forceField:Destroy()

						end

					end)

				end

			end

		end

	end

end

local function onPlayerAdded(player)

	player.CharacterAdded:Connect(function(_character)

		createCustomForcefield(player, FORCE_FIELD_DURATION)

	end)

end

Players.PlayerAdded(onPlayerAdded)

```

Provide feedback

---

Jump to

▼

ForceField

[Summary](#summary)

[Properties](#summary-properties)

[Properties](#properties)

[Visible](#Visible)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
