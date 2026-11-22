<!-- Source: https://create.roblox.com/docs/en-us/tutorials/curriculums/core/building/create-basic-visual-effects -->

Create basic visual effects | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/tutorials/curriculums/core/building/create-basic-visual-effects.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Tutorials](/docs/en-us/tutorials)

# Create basic visual effects

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/tutorials/curriculums/core/building/create-basic-visual-effects.md)

A static world can feel lifeless. Visual effects  add motion, make the environment feel more dynamic, and help draw players' attention to important areas.

In this section, you'll use particle emitters  to create two effects. The first is a glowing flare on top of the tallest sea stack that draws players' eyes upward, and the second is a layer of drifting dust motes that adds atmosphere and depth to the environment.

Particle emitters are primarily configured through numeric properties, making them a good fit for Assistant. Use the Build with Assistant  tabs to generate a set of working starting values, then adjust the colors and NumberSequence  curves yourself until the effect looks the way you want.

## [Create a flare](#create-a-flare)[](#create-a-flare)

The sample [Island Jump - Final](https://www.roblox.com/games/14238807008/Island-Jump-Completed-Sample)  game puts a giant flare on top of its tallest platform. Because the rest of the world is still, the flare becomes a focal point, making players naturally want to climb toward it.

Build with Assistant Build it Yourself

Create the flare

```

In Workspace > World, create a new folder named VFX if it doesn't exist.

Inside the VFX folder, create a block Part named VFX_Flare with Size 20, 20, 20, CFrame.Position 400, 331, 79, and CFrame.Orientation 0, 0, 0. Set Transparency to 1 so the part is invisible, and enable Anchored.

Inside VFX_Flare, create an Attachment.

Inside that Attachment, create a ParticleEmitter named Emitter_Flare with these properties:

- Texture: rbxassetid://8983307836

- Color: Color3.fromRGB(127, 84, 59)

- LightEmission: 1

- ZOffset: 1

- Lifetime: NumberRange.new(10, 10)

- Rate: 0.45

- RotSpeed: NumberRange.new(20, 20)

- Speed: NumberRange.new(0, 0)

- Size: a NumberSequence that starts at 0, grows slowly early in the lifetime, then quickly rises to 10 and stays at 10 for the rest of the lifetime.

- Transparency: a NumberSequence that stays near 0 (visible) for most of the lifetime, then bounces between values toward the end and settles at 1.

Also inside VFX_Flare (a sibling of the Attachment), create a PointLight with Brightness 2 and Range 36.

```

After running the prompt, open the Size  and Transparency  sequences in the Properties window and tweak the curves yourself until the pulsing feels right.

## [Create the dust particles](#create-the-dust-particles)[](#create-the-dust-particles)

The second type of particle emitter the sample game uses to add dynamic movement to the game is one that dust particles throughout the atmosphere. These particles surround the player, adding a sense of texture and depth to the air itself.

Build with Assistant Build it Yourself

Create the dust motes

```

In Workspace > World > VFX, create a block Part named VFX_DustMotes with Size 645, 355, 275, CFrame.Position 198, 168, 26, and CFrame.Orientation 0, 0, 0. Set Transparency to 1 so the part is invisible. Disable CanCollide. Enable Anchored.

Inside VFX_DustMotes, create a ParticleEmitter named Emitter_DustMotes with these properties:

- Texture: rbxassetid://14302399641

- Color: Color3.fromRGB(192, 241, 255)

- ZOffset: -5

- Lifetime: NumberRange.new(1, 10)

- Rate: 50000

- Rotation: NumberRange.new(-45, 45)

- RotSpeed: NumberRange.new(-60, -60)

- Speed: NumberRange.new(1, 5)

- Acceleration: Vector3.new(1, -1, 1)

- Size: a NumberSequence that rises to about 0.25 shortly after creation, then fades gradually to 0.

- Transparency: a NumberSequence that begins fully transparent, becomes more opaque (with an envelope of about 0.1) in the middle of the lifetime, then slowly fades out to 1.

```

After running, open the Size and Transparency sequences and tune the curves by eye until the dust feels right.

![The final version of the dust particles against a bright blue sky.](https://prod.docsiteassets.roblox.com/assets/tutorials/core-building-and-scripting/Dust-Motes-Sky.jpg) Faint dust particles in the air looking up at the sky from the platforms

[Next](/docs/en-us/tutorials/curriculums/core/building/customize-global-lighting)[Previous](/docs/en-us/tutorials/curriculums/core/scripting/script-an-upgrade-button)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
