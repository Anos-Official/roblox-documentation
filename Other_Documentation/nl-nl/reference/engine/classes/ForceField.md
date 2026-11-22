<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/ForceField -->

ForceField | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [ForceField](/docs/nl-nl/reference/engine/classes/ForceField)

Nederlands

Feedback

Engine-klasse

ForceField

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/ForceField)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[Visible](#Visible) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

ForceField Instantie

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

API-referentie

Eigenschappen

Visible

Parallel lezen

Mogelijkheden: AvatarBehavior

ForceField.Visible :[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

Aangepaste ForceField Effect

```

local Players = game:GetService("Players")

local FORCE_FIELD_DURATION = 15

local function createCustomForcefield(player, duration)

	local character = player.Character

	if character then

		local humanoid = character:FindFirstChild("Humanoid")

		if humanoid then

			-- vind de torso

			local torsoName = humanoid.RigType == Enum.HumanoidRigType.R15 and "UpperTorso" or "Torso"

			local torso = character:FindFirstChild(torsoName)

			if torso then

				-- maak een forcefield

				local forceField = Instance.new("ForceField")

				forceField.Visible = false -- niet zichtbaar

				-- maak een deeltjes effect

				local particleEmitter = Instance.new("ParticleEmitter")

				particleEmitter.Enabled = true

				particleEmitter.Parent = torso

				-- luister naar het verwijderen van het forcefield

				forceField.AncestryChanged:Connect(function(_child, parent)

					if not parent then

						if particleEmitter and particleEmitter.Parent then

							particleEmitter:Destroy()

						end

					end

				end)

				-- maak het forcefield ouder en stel het in om te vervallen

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

Feedback geven

---

Ga naar

▼

ForceField

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Eigenschappen](#properties)

[Visible](#Visible)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
