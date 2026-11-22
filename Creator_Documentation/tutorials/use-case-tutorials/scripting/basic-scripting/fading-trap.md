<!-- Source: https://create.roblox.com/docs/en-us/tutorials/use-case-tutorials/scripting/basic-scripting/fading-trap -->

Fading trap | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/tutorials/use-case-tutorials/scripting/basic-scripting/fading-trap.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Tutorials](/docs/en-us/tutorials)
4. /
5. Scripting
6. /
7. Basic gameplay

# Fading trap

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/tutorials/use-case-tutorials/scripting/basic-scripting/fading-trap.md)

In [Deadly Lava](/docs/en-us/tutorials/use-case-tutorials/scripting/basic-scripting/deadly-lava) , you learned how to trigger code based on user behavior. This tutorial shows you how to make a platform which fades away when a user steps on it.

## [Set up](#set-up)[](#set-up)

If you followed [Deadly Lava](/docs/en-us/tutorials/use-case-tutorials/scripting/basic-scripting/deadly-lava) , you can place your fading platform above the lava floor that users can't jump across.

1.

Insert a part and move it into place in your world. Name it FadingPlatform .

2.

Resize it so a user can jump on it.

3.

Make sure it's Anchored .

![](https://prod.docsiteassets.roblox.com/assets/tutorials/fading-trap/partInPlace.jpg)

4.

Insert a Script  into the part, rename it to FadeOnTouch , and remove the default code.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/fading-trap/scriptInPlace.png)

5.

Create a variable for the platform and an empty function connected to the platform's Touched  event.

```

local platform = script.Parent

local function fade()

end

platform.Touched:Connect(fade)

```

## [Fade the platform](#fade-the-platform)[](#fade-the-platform)

Having the platform vanish in an instant would be no fun at all as users would find it impossible to get across the gap. Instead, the platform should fade away  before users fall through it to give them a chance to jump off.

You could change the Transparency  property and wait a very short time over and over again to get this effect, but a gradual fade would require at least 10 changes between 0 and 1. That's 20 lines of very repetitive code.

This can be achieved much more effectively using a for  loop which repeats code a specific number of times. Each loop of the code is known as an iteration . A for loop is defined with three things, separated by commas:

![](https://prod.docsiteassets.roblox.com/assets/tutorials/fading-trap/forLoop.jpg)

-

Control variable  - The variable created and used to count the loops. In this example, it's count  and the starting value is 1.

-

End value  - The value it has to get to for the loop to stop. In this example, it's 10.

-

Step increment

OPTIONAL

 - Determines what to add to the control variable each loop. If left out, it defaults to 1, so in this example it's unnecessary.

In FadeOnTouch :

1.

In the function, create a for  loop starting from 1  which iterates 10  times.

2.

Inside the for loop, set the Transparency  property to the control variable divided by 10 .

3.

Call the [task.wait()](/docs/en-us/reference/engine/libraries/task#wait)  function with a time of 0.1 .

```

local platform = script.Parent

local function fade()

	for count = 1, 10 do

		platform.Transparency = count / 10

		task.wait(0.1)

	end

end

platform.Touched:Connect(fade)

```

When the loop runs, count increases by 1 with each iteration. This means that the platform's Transparency  will increase by 0.1 every 0.1 seconds, reaching full transparency after 1 second.

## [Reappear](#reappear)[](#reappear)

After the platform has vanished, users should fall through it. The platform should also come back a few seconds after it fades - otherwise, users would never get to try the jump again if they failed. The CanCollide property controls whether users can fall through a part.

1.

Set the CanCollide  property of the platform to false  after the for loop.

2.

Wait for a few seconds using the [task.wait()](/docs/en-us/reference/engine/libraries/task#wait)  function.

3.

Set the CanCollide  property back to true .

4.

Set the Transparency  property back to 0 .

```

local platform = script.Parent

local function fade()

   for count = 1, 10 do

      platform.Transparency = count / 10

      task.wait(0.1)

   end

   platform.CanCollide = false

   task.wait(3)

   platform.CanCollide = true

   platform.Transparency = 0

end

platform.Touched:Connect(fade)

```

## [Debounce variable](#debounce-variable)[](#debounce-variable)

In [Deadly Lava](/docs/en-us/tutorials/use-case-tutorials/scripting/basic-scripting/deadly-lava) , you learned that the Touched  event runs each time a user's body part comes into contact with the part. This behavior causes issues when a user runs across the fading platform: the function will run multiple times, resetting the loop each time.

For the code to work properly, the function should only run once when the user touches the platform for the first time. Ensuring that an action is only triggered once when it would otherwise be triggered multiple times is known as debouncing .

To debounce a function, a [boolean](/docs/en-us/luau/booleans)  variable can be used to keep track of when the platform has already been touched. Booleans can only contain true  and false  values. Create a variable called isTouched  and set it to false .

```

local platform = script.Parent

local isTouched = false

local function fade()

	for count = 1, 10 do

		platform.Transparency = count / 10

		task.wait(0.1)

	end

	platform.CanCollide = false

	task.wait(3)

	platform.CanCollide = true

	platform.Transparency = 0

end

platform.Touched:Connect(fade)

```

## [Check the variable](#check-the-variable)[](#check-the-variable)

An if statement can be used to only run the code in the fade function if the isTouched  debouncing variable is false. Wrap the body of the fade function in an if  statement with the condition not isTouched .

```

local platform = script.Parent

local isTouched = false

local function fade()

	if not isTouched then

		for count = 1, 10 do

            platform.Transparency = count / 10

            task.wait(0.1)

	    end

		platform.CanCollide = false

		task.wait(3)

		platform.CanCollide = true

		platform.Transparency = 0

	end

end

platform.Touched:Connect(fade)

```

The Luau not  operator reverses the value of whatever follows it. In conditional terms, this means that the first if statement behaves the same as the statements which follow.

```

if not isTouched then

end

if isTouched == false then

end

if isTouched == nil then

end

```

## [Toggle the debounce](#toggle-the-debounce)[](#toggle-the-debounce)

Currently, the code in the fade  function will always run because isTouched  is false and not isTouched  evaluates to true. To complete the debounce routine, you'll need to toggle the variable's value in two places.

1.

Set isTouched  to true  inside the if  statement, before the platform begins to fade.

2.

Set it back to false  once the platform has reappeared.

```

local function fade()

  if not isTouched then

    isTouched = true

    for count = 1, 10 do

      platform.Transparency = count / 10

      task.wait(0.1)

    end

    platform.CanCollide = false

    task.wait(3)

    platform.CanCollide = true

    platform.Transparency = 0

    isTouched = false

  end

end

platform.Touched:Connect(fade)

```

And that's it! Test your code now, and you should find that the platform fades away when the user jumps on it and comes back a few seconds later.

You can duplicate this platform across a wider gap to create a challenging obstacle and change the speed at which they fade to balance the difficulty.

## [Final code](#final-code)[](#final-code)

```

local platform = script.Parent

local isTouched = false

local function fade()

	if not isTouched then

		isTouched = true

		for count = 1, 10 do

		    platform.Transparency = count / 10

		    task.wait(0.1)

	    end

		platform.CanCollide = false

		task.wait(3)

		platform.CanCollide = true

		platform.Transparency = 0

		isTouched = false

	end

end

platform.Touched:Connect(fade)

```

[Next](/docs/en-us/tutorials/use-case-tutorials/scripting/basic-scripting/score-points)[Previous](/docs/en-us/tutorials/use-case-tutorials/scripting/basic-scripting/deadly-lava)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
