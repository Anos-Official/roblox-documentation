<!-- Source: https://create.roblox.com/docs/en-us/tutorials/fundamentals/coding-3/powerups-with-if-statements -->

Evaluate multiple statements | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/tutorials/fundamentals/coding-3/powerups-with-if-statements.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Tutorials](/docs/en-us/tutorials)
4. /
5. [Conditionals](/docs/en-us/tutorials/fundamentals/coding-3/landing)

# Evaluate multiple statements

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/tutorials/fundamentals/coding-3/powerups-with-if-statements.md)

If statements can have multiple requirements that need to be true before running code. The keyword and  allows you to combine statements. The following code evaluates first if two plus two equals six and then if four does not equal six. If both statements are true, the code will run.

## [Create a powerup](#create-a-powerup)[](#create-a-powerup)

Powerups are in-game items that give players special abilities like flying, invisibility, or speed. This powerup will boost the player's walking speed every time the powerup is touched. Continuously applying boosts can make the player go way too fast, so and  will be used to control the upper walking speed limit.

### [Set up the powerup](#set-up-the-powerup)[](#set-up-the-powerup)

Use this code with a simple part or a model, such as a crystal, coin, or glowing neon orb.

1.

Create a new part named Powerup  and insert a script named WalkSpeedManager .

2.

Declare a variable named speedBoost  and assign the script's parent object.

```

-- Gives a temporary speed boost when touched

local speedBoost = script.Parent

```

3.

Set up a function named onTouch  and connect it to the parent object's Touched  event. Then playtest and check your work.

```

local speedBoost = script.Parent

local function onTouch(otherPart)

	print("Something touched speedBoost")

end

speedBoost.Touched:Connect(onTouch)

```

4.

The WalkSpeed property is found on Humanoid objects. Use the same pattern used when creating a trap part and create a conditional that checks for Humanoid objects.

Looks for Humanoid parts

```

local function onTouch(otherPart)

	local character = otherPart.Parent

	local humanoid = character:FindFirstChildWhichIsA("Humanoid")

	if humanoid then

		print("A Humanoid was found")

	end

end

```

## [Speed players up](#speed-players-up)[](#speed-players-up)

The speed boost will make avatars walk faster every time the speed boost is touched. That will quickly become very, very fast. The keyword and  will ensure players can't go too fast by only enabling the speed boost if the player is under a certain speed.

1.

If a Humanoid is found, take the current WalkSpeed value and add 10 to it. Playtest, and your avatar will get faster every time it touches the speed boost.

Increases current WalkSpeed

```

local function onTouch(otherPart)

	local character = otherPart.Parent

	local humanoid = character:FindFirstChildWhichIsA("Humanoid")

	if humanoid then

		humanoid.WalkSpeed += 10

	end

end

speedBoost.Touched:Connect(onTouch)

```

2.

In the if statement, use the keyword and  to add a second condition that the current WalkSpeed value is less than 50. After adding the boost, the fastest WalkSpeed value will be 60.

Checks if current WalkSpeed is 50 or less

```

if humanoid and humanoid.WalkSpeed <= 50 then

	humanoid.WalkSpeed += 10

end

```

### [Fine tune the speed boost](#fine-tune-the-speed-boost)[](#fine-tune-the-speed-boost)

OnTouch is called every time the speed boost is touched. Every step or slightest bounce triggers the Touched event and calls the connected function. The part's property, CanTouch  can keep the Touched event from firing. Take advantage of CanTouch and turn off the speed boost for one second every time it's been activated.

1.

After applying the boost, set the part's CanTouch property to false. Playtest and make sure the boost only applies once.

Disables the speed boost

```

local speedBoost = script.Parent

local function onTouch(otherPart)

	local character = otherPart.Parent

	local humanoid = character:FindFirstChildWhichIsA("Humanoid")

	if humanoid and humanoid.WalkSpeed <= 50 then

		humanoid.WalkSpeed += 10

		speedBoost.CanTouch = false

	end

end

speedBoost.Touched:Connect(onTouch)

```

2.

Use task.wait(1)  to pause the script for one second, then set CanTouch to true. Playtest and make sure the speed boost can be reapplied after one second.

Finished script

```

local speedBoost = script.Parent

local function onTouch(otherPart)

	local character = otherPart.Parent

	local humanoid = character:FindFirstChildWhichIsA("Humanoid")

	if humanoid and humanoid.WalkSpeed <= 50 then

		humanoid.WalkSpeed += 10

		speedBoost.CanTouch = false

		task.wait(1)

		speedBoost.CanTouch = true

	end

end

speedBoost.Touched:Connect(onTouch)

```

3.

Play with the values in the finished script. WalkSpeed can go up to 100. The default WalkSpeed value is 16.

## [Summary](#summary)[](#summary)

The keyword and  can be used to require multiple conditions before running a code chunk, such as a value being more than 0 and less than 100. Or that if there is a Humanoid and its WalkSpeed is less or equal to 50.

[Next](/docs/en-us/tutorials/fundamentals/coding-3/multiple-conditions)[Previous](/docs/en-us/tutorials/fundamentals/coding-3/traps-with-if-statements)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
