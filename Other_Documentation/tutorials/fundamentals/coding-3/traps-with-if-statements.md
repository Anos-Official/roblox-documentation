<!-- Source: https://create.roblox.com/docs/tutorials/fundamentals/coding-3/traps-with-if-statements -->

If/then practice with traps | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/tutorials/fundamentals/coding-3/traps-with-if-statements.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Tutorials](/docs/en-us/tutorials)
4. /
5. [Conditionals](/docs/tutorials/fundamentals/coding-3/landing)

# If/then practice with traps

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/tutorials/fundamentals/coding-3/traps-with-if-statements.md)

Traps that decrease players' health are a fun game-play element that can be coded with conditional statements. Practice using conditionals by creating a part that sets the player's health to zero when touched.

## [Set up the trap](#set-up-the-trap)[](#set-up-the-trap)

Traps work exceptionally well in games with movement-based challenges, like obbies. These steps will start by setting up the necessary variables and functions. Do as much as you can without looking at the code boxes first.

1.

Create and name a trap part. Insert a script into the part.

2.

In the script, add a descriptive comment and then use a variable to reference the script's parent.

```

-- If a player touches this part, set their health to 0

local trapPart = script.Parent

```

3.

Create a function named onTouch()  with a parameter named otherPart .

```

-- If a player touches this part, set their health to 0

local trapPart = script.Parent

local function onTouch(otherPart)

end

```

4.

Connect the function to the trap part's Touched  event to run whenever something touches the part.

```

local trapPart = script.Parent

local function onTouch(otherPart)

end

trapPart.Touched:Connect(onTouch)

```

## [Check for player touch](#check-for-player-touch)[](#check-for-player-touch)

Remember, the parameter otherPart  records whatever touches the trap part, which might be a part of a player or just the baseplate.

To ensure the trap will only destroy players and won't destroy random decor items, use an if/then statement to check if whatever is in otherPart  contains a Humanoid object.

Humanoids are present in player avatars and many NPCs. Humanoids have several unique properties. One such property is Health.

### [Find a specific object](#find-a-specific-object)[](#find-a-specific-object)

The function FindFirstChildWhichIsA()  can be used to look for specific object types, which is handy because we're looking for a Humanoid-type object. Players will likely touch the trap with only a part of their avatar, so a variable must be set up to find the parent of the touching part and search it for a Humanoid.

1.

In onTouch() , type local character = otherPart.Parent .

```

local trapPart = script.Parent

local function onTouch(otherPart)

   -- Finds otherPart's parent object

  local character = otherPart.Parent

end

trapPart.Touched:Connect(onTouch)

```

2.

Check to see if character  has a [Humanoid](/docs/reference/engine/classes/Humanoid)  by typing:

local humanoid = character:FindFirstChildWhichIsA("Humanoid")

```

local trapPart = script.Parent

local function onTouch(otherPart)

  local character = otherPart.Parent

  local humanoid = character:FindFirstChildWhichIsA("Humanoid")

end

trapPart.Touched:Connect(onTouch)

```

### [Check with an if statement](#check-with-an-if-statement)[](#check-with-an-if-statement)

If a Humanoid is found, then set the Humanoid's Health to zero.

1.

Use an if statement to check if a Humanoid was successfully assigned to local humanoid .

```

local trapPart = script.Parent

local function onTouch(otherPart)

   local character = otherPart.Parent

   local humanoid = character:FindFirstChildWhichIsA("Humanoid")

   -- Evaluates if a Humanoid was found

   if humanoid then

   end

end

trapPart.Touched:Connect(onTouch)

```

2.

Add a print statement and check the code so far.

```

local trapPart = script.Parent

local function onTouch(otherPart)

   local character = otherPart.Parent

   local humanoid = character:FindFirstChildWhichIsA("Humanoid")

   -- Evaluates if a Humanoid was found

   if humanoid then

      print("Found a Humanoid")

   end

end

trapPart.Touched:Connect(onTouch)

```

3.

Run  the code and check that you can see the output whenever a player touches the part.

## [Change the player's health](#change-the-players-health)[](#change-the-players-health)

If the statement is true, you can use the same humanoid variable to set the player's health to 0.

1.

Between then  and end , type humanoid.Health = 0 .

Completed script

```

local trapPart = script.Parent

local function onTouch(otherPart)

   local character = otherPart.Parent

   local humanoid = character:FindFirstChildWhichIsA("Humanoid")

   -- Evaluates if a Humanoid was found

   if humanoid then

      print("Found a Humanoid")

      humanoid.Health = 0

   end

end

trapPart.Touched:Connect(onTouch)

```

2.

Test the trap.

## [Summary](#summary)[](#summary)

This trap part used conditionals to detect Humanoid parts and set the Humanoid's health to zero. This script is an improvement on the previous trap script, which destroyed any touching object no matter what it was.

It does, however, still have a few flaws. Humanoids aren't just in players. Humanoids are also found in non-playable characters. The script is also only good at setting the player's health to zero. You can experiment with subtracting a small amount of health, but it's likely to subtract the health faster than desired. Later lessons provide further improvements to give greater control over how much health is subtracted from players.

[Next](/docs/tutorials/fundamentals/coding-3/powerups-with-if-statements)[Previous](/docs/tutorials/fundamentals/coding-3/intro-to-if-statements)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
