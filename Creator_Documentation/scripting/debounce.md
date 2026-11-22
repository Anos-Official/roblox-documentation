<!-- Source: https://create.roblox.com/docs/en-us/scripting/debounce -->

Debounce patterns | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/scripting/debounce.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Learn](/docs/en-us/learn)

# Debounce patterns

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/scripting/debounce.md)

A debounce  pattern is a coding technique that prevents a function from running too many times or an input from triggering multiple times. The following scripting scenarios illustrate debounce as a best practice.

## [Detect collisions](#detect-collisions)[](#detect-collisions)

Suppose you want to create a hazardous trap part that inflicts 10 damage when touched. An initial implementation might use a basic [BasePart.Touched](/docs/en-us/reference/engine/classes/BasePart#Touched)  connection and a damagePlayer  function like this:

Script - Damage Player

```

local part = script.Parent

local function damagePlayer(otherPart)

	print(part.Name .. " collided with " .. otherPart.Name)

	local humanoid = otherPart.Parent:FindFirstChildWhichIsA("Humanoid")

	if humanoid then

		humanoid.Health -= 10  -- Reduce player health

	end

end

part.Touched:Connect(damagePlayer)

```

While logical at first glance, testing will show that the [Touched](/docs/en-us/reference/engine/classes/BasePart#Touched)  event fires multiple times in quick succession based on subtle physical collisions.

 ![](https://prod.docsiteassets.roblox.com/assets/scripting/scripts/Touched-Event-No-Debounce.png)

To avoid causing excessive damage on initial contact, you can add a debounce system which enforces a cooldown period on damage through an [instance attribute](/docs/en-us/studio/properties#instance-attributes) .

Script - Damage Player Using Debounce

```

local part = script.Parent

local RESET_TIME = 1

local function damagePlayer(otherPart)

	print(part.Name .. " collided with " .. otherPart.Name)

	local humanoid = otherPart.Parent:FindFirstChildWhichIsA("Humanoid")

	if humanoid then

		if not part:GetAttribute("Touched") then

			part:SetAttribute("Touched", true)  -- Set attribute to true

			humanoid.Health -= 10  -- Reduce player health

			task.wait(RESET_TIME)  -- Wait for reset duration

			part:SetAttribute("Touched", false)  -- Reset attribute

		end

	end

end

part.Touched:Connect(damagePlayer)

```

## [Trigger sounds](#trigger-sounds)[](#trigger-sounds)

Debounce is also useful when working with sound effects, such as playing a sound when two parts collide ([Touched](/docs/en-us/reference/engine/classes/BasePart#Touched) ), or playing a sound on the [Activated](/docs/en-us/reference/engine/classes/GuiButton#Activated)  event when a user interacts with an on-screen button. In both cases, calling [Sound:Play()](/docs/en-us/reference/engine/classes/Sound#Play)  starts playback from the beginning of its track and — without a debounce system — the sound may play multiple times in quick succession.

To prevent sound overlap, you can debounce using the [IsPlaying](/docs/en-us/reference/engine/classes/Sound#IsPlaying)  property of the [Sound](/docs/en-us/reference/engine/classes/Sound)  object:

Script - Play Collision Sound Using Debounce

```

local projectile = script.Parent

local function playSound()

	-- Find child sound on the part

	local sound = projectile:FindFirstChild("Impact")

	-- Play the sound only if it's not already playing

	if sound and not sound.IsPlaying then

		sound:Play()

	end

end

projectile.Touched:Connect(playSound)

```

Script - Play Button Click Using Debounce

```

local button = script.Parent

local function onButtonActivated()

	-- Find child sound on the button

	local sound = button:FindFirstChild("Click")

	-- Play the sound only if it's not already playing

	if sound and not sound.IsPlaying then

		sound:Play()

	end

end

button.Activated:Connect(onButtonActivated)

```

## [Pickup effects](#pickup-effects)[](#pickup-effects)

Games often include collectible pickups in the 3D world such as medkits, ammo packs, and more. If you design these pickups to remain in the world for players to grab again and again, a "cooldown" time should be added before the pickup refreshes and reactivates.

Similar to [detecting collisions](#detect-collisions) , you can manage the debounce state with an [instance attribute](/docs/en-us/studio/properties#instance-attributes) , and visualize the cooldown period by changing the part's [Transparency](/docs/en-us/reference/engine/classes/BasePart#Transparency) .

Script - Health Pickup Using Debounce

```

local part = script.Parent

part.Anchored = true

part.CanCollide = false

local COOLDOWN_TIME = 5

local function healPlayer(otherPart)

	local humanoid = otherPart.Parent:FindFirstChildWhichIsA("Humanoid")

	if humanoid then

		if not part:GetAttribute("CoolingDown") then

			part:SetAttribute("CoolingDown", true)  -- Set attribute to true

			humanoid.Health += 25  -- Increase player health

			part.Transparency = 0.75  -- Make part semi-transparent to indicate cooldown state

			task.wait(COOLDOWN_TIME)  -- Wait for cooldown duration

			part.Transparency = 0  -- Reset part to fully opaque

			part:SetAttribute("CoolingDown", false)  -- Reset attribute

		end

	end

end

part.Touched:Connect(healPlayer)

```

This cooldown concept can be applied to other scenarios as well, such as creating a "reload" time for a rocket launcher to limit how frequently players can fire rockets.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
