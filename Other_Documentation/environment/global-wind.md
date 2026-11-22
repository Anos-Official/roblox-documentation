<!-- Source: https://create.roblox.com/docs/environment/global-wind -->

Global wind | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/environment/global-wind.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Environment](/docs/environment)

# Global wind

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/environment/global-wind.md)

The [GlobalWind](/docs/reference/engine/classes/Workspace#GlobalWind)  vector sets the direction and strength that wind blows through a game, affecting [terrain grass](/docs/parts/terrain#grass-animation)  and [dynamic clouds](/docs/environment/clouds) . You can set it as a [constant vector](#global-wind-vector) , or adjust it through [scripting](#scripted-effects)  to create cyclical gusts of wind. Additionally, you can influence [particles](#particle-influence)  to follow the global wind vector.

## [Global wind vector](#global-wind-vector)[](#global-wind-vector)

Global wind is controlled through The [GlobalWind](/docs/reference/engine/classes/Workspace#GlobalWind)  vector is a property of [Workspace](/docs/reference/engine/classes/Workspace)  and you can edit it directly in Studio, or set it through [scripting](#scripted-effects) .

To set the global wind vector in Studio:

1.

In the Explorer  window, select the top-level [Workspace](/docs/reference/engine/classes/Workspace)  service.

 ![Workspace object shown in Explorer window of Studio](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Workspace.png)

2.

In the Properties  window, locate the [GlobalWind](/docs/reference/engine/classes/Workspace#GlobalWind)  property and set an X , Y , and Z  value for its direction and strength.

 ![GlobalWind property shown in Properties window of Studio](https://prod.docsiteassets.roblox.com/assets/studio/properties/Workspace-GlobalWind.png)

Note that the speed of [animated grass](/docs/parts/terrain#grass-animation)  — but not its vector direction — will be reduced if the player has toggled on the Reduce Motion  [accessibility](/docs/production/publishing/accessibility#reduced-motion)  setting from the Roblox or in-game Settings  menu.

## [Particle Influence](#particle-influence)[](#particle-influence)

Particles emitted by a [ParticleEmitter](/docs/reference/engine/classes/ParticleEmitter)  will follow the global wind vector as long as the emitter's [WindAffectsDrag](/docs/reference/engine/classes/ParticleEmitter#WindAffectsDrag)  property is enabled and its [Drag](/docs/reference/engine/classes/ParticleEmitter#Drag)  property is greater than 0 , which is useful for [simulating rain](/docs/effects/particle-emitters#simulate-rain) . [Fire](/docs/reference/engine/classes/Fire)  and [Smoke](/docs/reference/engine/classes/Smoke)  instances follow the wind vector by default.

 ![Drag and WindAffectsDrag properties shown in Properties window of Studio](https://prod.docsiteassets.roblox.com/assets/studio/properties/ParticleEmitter-WindAffectsDrag.png)

## [Wind direction widget](#wind-direction-widget)[](#wind-direction-widget)

To make it easier to tune global wind, you can use the Wind Direction  widget, accessible from Studio's View  menu. The widget lets you visualize how wind is blowing using a wind sock model, and you can dynamically set the wind's Speed , Yaw , and Pitch  by clicking the desired aspect name and sliding the slider along the bottom, or you can adjust yaw or pitch by manipulating the green ring and blue arrow on the animated portion. You can also click and drag the widget to reposition it anywhere in the 3D viewport.

 ![Wind Direction widget showing in 3D viewport of Studio](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/aero-fluid-dynamics/Wind-Direction-Widget.jpg)

## [Scripted effects](#scripted-effects)[](#scripted-effects)

Scripting of the [GlobalWind](/docs/reference/engine/classes/Workspace#GlobalWind)  property opens up a whole range of possibilities. For example, you can use the following code sample to cause cyclical gusts of wind that ease in and out using the [math.sin()](/docs/reference/engine/libraries/math#sin)  function.

Script - Cyclical Wind Gusts

```

local gustCycleDelay = 5  -- Max duration between gust cycles in seconds

local gustCycleDuration = 3.5  -- Duration of each gust cycle in seconds

-- During each gust cycle, a portion of "gust" will be added to "baseWind" in a ramped fashion

local baseWind = Vector3.new(5, 0, 2)  -- Base wind speed and direction

local gust = Vector3.new(25, 0, 10)  -- Gust speed and direction

local gustIntervals = 100  -- Number of iterations used to calculate each gust interval

local dg = gustCycleDuration / gustIntervals

local dgf = dg / gustCycleDuration

-- Set global wind to base wind initially

workspace.GlobalWind = baseWind

-- Wait delay amount before starting gusts

task.wait(gustCycleDelay)

while true do

	for i = 1, gustIntervals do

		local f = math.sin(math.pi * dgf * i)  -- Use sin() function to ramp gust

		workspace.GlobalWind = baseWind + f * gust  -- Set global wind to base wind + gust

		task.wait(dg)

	end

	workspace.GlobalWind = baseWind  -- Reset global wind to base wind at end of gust cycle

	task.wait(math.random() * gustCycleDelay)  -- Wait a random fraction of delay before next gust cycle

end

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
