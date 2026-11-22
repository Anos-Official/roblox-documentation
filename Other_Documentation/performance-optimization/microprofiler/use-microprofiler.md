<!-- Source: https://create.roblox.com/docs/performance-optimization/microprofiler/use-microprofiler -->

MicroProfiler walkthrough | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/performance-optimization/microprofiler/use-microprofiler.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Performance optimization](/docs/performance-optimization)
6. /
7. [MicroProfiler](/docs/performance-optimization/microprofiler)

# MicroProfiler walkthrough

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/performance-optimization/microprofiler/use-microprofiler.md)

This walkthrough shows how to use the MicroProfiler to find a problematic aspect of a game and identify the root cause. Download the game, Open from File  in Studio, and follow along.

 [Download the game](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/RaycastSpam.rbxl)

## [Identify the issue](#identify-the-issue)[](#identify-the-issue)

1.

After you open the game in Studio, start testing it with F5  or the Play  button.

2.

The frame rate feels decent, but not as smooth as it should be for a game of this size and scope. Press Ctrl Shift F5  (⌘ Shift F5 ) to show the Performance Summary  overlay.

 ![Performance summary showing 45 FPS.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-tut-framerate.png)

Note that the frame rate is below 60 frames per second (FPS).

3.

Open the MicroProfiler by pressing Ctrl Alt F6  (⌘ ⌥ F6 ).

 ![The MicroProfiler after opening it.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-tut-bar-graph.png)

Note that the frame times are consistent —the bars are roughly the same height—so whatever is causing the low frame rate is running every single frame as opposed to running occasionally and causing frame time spikes.

4.

Pause the MicroProfiler by pressing Ctrl P  (⌘ P ). Pausing with the keyboard shortcut opens [detailed mode](/docs/performance-optimization/microprofiler/modes#detailed-mode) .

5.

Click and drag to pan the graph. Note how one particular task in the worker threads seems to be using a lot of processing time compared to the main thread. Hover over [RunService.Stepped](/docs/reference/engine/classes/RunService#Stepped)  and note how long it's taking to render.

 ![Detailed mode with long labels for processes.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-tut-stepped.png)

6.

Stacked bars in the timeline indicate a hierarchy of code, so keep hovering on lower and lower layers to try and identify the issue.

 ![On-hover details for various processes, with LocalScript highlighted.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-tut-localscript.png)  ![On-hover details for various processes, with Raycast highlighted.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-tut-raycast-label.png)

Note the LocalScript  label, which indicates the name of the script, and the Raycast  label, which indicates that the problem might be related to raycasting.

## [Create troubleshooting labels](#create-troubleshooting-labels)[](#create-troubleshooting-labels)

Now that the MicroProfiler has provided a starting point, you can troubleshoot the problematic code.

1.

Stop the play test and filter the Explorer window for localscript  to find the file.

 ![A view of filtering in the Explorer window.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-tut-explorer-filter.png)

A search for raycast  indicates that this portion of code is probably the culprit for the game's poor performance:

```

local RAYS_PER_SECOND = 1500

local function onStepped()

	for _ = 1, RAYS_PER_SECOND do

		local startPosition = getRandomPosition()

		local endPosition = getRandomPosition()

		local direction = endPosition - startPosition

		Workspace:Raycast(

         startPosition,

         endPosition

      )

	end

end

RunService.Stepped:Connect(onStepped)

```

Specifically, you can see that the code is casting 1,500 rays per second in random directions.

2.

To verify that this portion of code is causing the rendering delay, wrap the contents of the function with [debug.profilebegin()](/docs/reference/engine/libraries/debug#profilebegin)  and [debug.profileend()](/docs/reference/engine/libraries/debug#profileend) :

```

local function onStepped()

   debug.profilebegin("Raycast Spam")

   for _ = 1, RAYS_PER_SECOND do

      local startPosition = getRandomPosition()

      local endPosition = getRandomPosition()

      local direction = endPosition - startPosition

      Workspace:Raycast(

         startPosition,

         endPosition

      )

   end

   debug.profileend()

end

```

## [Confirm and fix the issue](#confirm-and-fix-the-issue)[](#confirm-and-fix-the-issue)

1.

Start testing the game, and open the MicroProfiler again.

2.

Note how the MicroProfiler now shows the custom label, indicating that this function was indeed the root cause.

 ![MicroProfiler detailed view with 'Raycast Spam' visible.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-tut-spam.png)

3.

Stop the play test.

4.

Delete or comment out the onStepped()  function and the RunService.Stepped:Connect(onStepped)  connection.

5.

Start testing the game again, and check the Performance Summary  again.

 ![Performance summary showing 60 FPS.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-tut-framerate2.png)

Note the huge improvement to frame rate and corresponding drop in frame times on the MicroProfiler graph.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
