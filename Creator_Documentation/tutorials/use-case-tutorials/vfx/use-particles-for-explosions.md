<!-- Source: https://create.roblox.com/docs/en-us/tutorials/use-case-tutorials/vfx/use-particles-for-explosions -->

Create explosions with VFX | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/tutorials/use-case-tutorials/vfx/use-particles-for-explosions.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Tutorials](/docs/en-us/tutorials)
4. /
5. VFX

# Create explosions with VFX

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/tutorials/use-case-tutorials/vfx/use-particles-for-explosions.md)

Previously, you worked with particles that played continuously, like [smoke from a volcano](/docs/en-us/tutorials/use-case-tutorials/vfx/custom-particle-effects) . Particles can also be used in a single burst, such as explosions. This tutorial will show you how to create a trap that emits a burst of particles and kills a player.

## [Emitter setup](#emitter-setup)[](#emitter-setup)

The explosion will use a ParticleEmitter with some changed properties that will create a burst.

1.

Design a dangerous looking trap. Then, insert a ParticleEmitter  named Explosion  into the part.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/using-particles-for-explosions/burstParticles_partExample.png)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/using-particles-for-explosions/burstParticles_createExplosion.png)

2.

Create an electric spark effect using these properties.

| Property | | Value | | Description |
| --- | --- |
| ** Texture** | | rbxassetid://6101261905 | | Electric spark texture. |
| ** Drag** | | 10 | | How fast particles lose speed. |
| ** Lifetime** | | 0.2, 0.6 | | Makes explosion particles exist for a short time. |
| ** Speed** | | 20, 40 | | Compensates for the short lifetime. |
| ** SpreadAngle** | | 180, 180 | | Fires particles in all directions. |

3.

So the trap doesn't emit particles constantly toggle Enabled  to off .

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/using-particles-for-explosions/burstParticles_toggleEnabled.png)

## [Test particle bursts](#test-particle-bursts)[](#test-particle-bursts)

To test the particle burst, you can use a Studio plugin developed by Roblox.

1.

Go to the Marketplace page for the [Emit() Plugin](https://www.roblox.com/library/303835976/ParticleEmitter-Emit-n)  Plugin. On that page, click the Install  button.

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/using-particles-for-explosions/burstParticles_pluginInstall.png)

2.

When Studio opens, the plugin should install automatically.

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/using-particles-for-explosions/burstParticles_confirmPluginInstall.png)

3.

Select the Explosion  emitter and notice the plugin UI that appears in the top left of the 3D viewport. In the number box, type 100  (the amount of particles to emit) and press Enter .

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/using-particles-for-explosions/burstParticles_enterEmitRate.png)

4.

Press the Emit  button to test the emitter.

## [Color and transparency](#color-and-transparency)[](#color-and-transparency)

Some extra steps can make the explosion look more impressive.

1.

Open the sequence window for the emitter's Color  by clicking the three dots next to the property. Then, create keypoints in the window to make a color gradient.

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/using-particles-for-explosions/burstParticles_colorSequence.png)

2.

For Transparency , use a number sequence  that increases transparency over a smooth curve to show a gradual fade out.

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/using-particles-for-explosions/burstParticles_transparencyGradient.png)

A finished particle effect may look like below.

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/using-particles-for-explosions/burstParticles_transparencyGradientExample.jpg)

## [Script setup](#script-setup)[](#script-setup)

With the emitter complete, the explosion can now be played through a script. The script works by checking for players touching the trap. Whenever it detects someone, the particles will emit and the player will die.

1.

In the trap part, add a new Script  named PlayExplosion .

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/using-particles-for-explosions/burstParticles_explorerCreateScript.png)

2.

Set up variables to store the part and emitter. Then, include a variable named EMIT_AMOUNT  that stores the number of particles emitted per explosion.

```

local trapObject = script.Parent

local particleEmitter = trapObject.Explosion

local EMIT_AMOUNT = 100

```

3.

Code an event to check if a [Humanoid](/docs/en-us/reference/engine/classes/Humanoid)  touches the part. If so, set that humanoid's health to 0, forcing them to respawn.

```

local trapObject = script.Parent

local particleEmitter = trapObject.Explosion

local EMIT_AMOUNT = 100

local function killPlayer(otherPart)

	local character = otherPart.Parent

	local humanoid = character:FindFirstChildWhichIsA("Humanoid")

	if humanoid then

		humanoid.Health = 0

	end

end

trapObject.Touched:Connect(killPlayer)

```

## [Play the explosion](#play-the-explosion)[](#play-the-explosion)

In scripts, particles are emitted using the [Emit()](/docs/en-us/reference/engine/classes/ParticleEmitter#Emit)  function. This creates a one-time burst of a number of particles.

1.

Call the Emit()  function and pass in EMIT_AMOUNT , the variable created earlier.

```

local trapObject = script.Parent

local particleEmitter = trapObject.Explosion

local EMIT_AMOUNT = 100

local function killPlayer(otherPart)

	local character = otherPart.Parent

	local humanoid = character:FindFirstChildWhichIsA("Humanoid")

	if humanoid then

		humanoid.Health = 0

		particleEmitter:Emit(EMIT_AMOUNT)

	end

end

trapObject.Touched:Connect(killPlayer)

```

2.

Test the script by walking into the trap.

With just a few changes to the example in this tutorial, you can create a variety of different effects. Some alternatives include sparkles for gathering collectable objects, or explosions to indicate a projectile's impact.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
