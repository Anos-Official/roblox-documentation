<!-- Source: https://create.roblox.com/docs/animation/using -->

Use animations | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/animation/using.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Animation](/docs/animation)

# Use animations

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/animation/using.md)

Once you have [created an animation](/docs/animation/editor) , you need to use scripts to include them in your game. You can either [play animations manually](#play-animations-from-scripts)  from scripts or [replace default animations](#replace-default-animations)  for player characters.

## [Play animations from scripts](#play-animations-from-scripts)[](#play-animations-from-scripts)

In some cases, you'll need to play an animation directly from inside a script, such as when a user presses a certain key or picks up a special item.

### [Humanoids](#humanoids)[](#humanoids)

To play an animation on a rig containing a [Humanoid](/docs/reference/engine/classes/Humanoid)  object, such as typical playable characters, follow this basic pattern:

1.

Ensure that the local player's [Humanoid](/docs/reference/engine/classes/Humanoid)  contains an [Animator](/docs/reference/engine/classes/Animator)  object.

2.

Create a new [Animation](/docs/reference/engine/classes/Animation)  instance with the proper [AnimationId](/docs/reference/engine/classes/Animation#AnimationId) .

3.

Load the animation via [Animator:LoadAnimation()](/docs/reference/engine/classes/Animator#LoadAnimation)  to create an [AnimationTrack](/docs/reference/engine/classes/AnimationTrack) .

4.

Play the track with [AnimationTrack:Play()](/docs/reference/engine/classes/AnimationTrack#Play) .

For example, the following [LocalScript](/docs/reference/engine/classes/LocalScript) , when placed in [StarterPlayerScripts](/docs/reference/engine/classes/StarterPlayerScripts) , loads a "kick" animation onto the player's character and plays it. The script also utilizes the [GetMarkerReachedSignal()](/docs/reference/engine/classes/AnimationTrack#GetMarkerReachedSignal)  method to detect when a specific [animation event](/docs/animation/events)  occurs.

LocalScript - Play Custom Animation on Player Character

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local character = player.Character or player.CharacterAdded:Wait()

-- Ensure that the character's humanoid contains an "Animator" object

local humanoid = character:WaitForChild("Humanoid")

local animator = humanoid:WaitForChild("Animator")

-- Create a new "Animation" instance and assign an animation asset ID

local kickAnimation = Instance.new("Animation")

kickAnimation.AnimationId = "rbxassetid://2515090838"

-- Load the animation onto the animator

local kickAnimationTrack = animator:LoadAnimation(kickAnimation)

-- If a named event was defined for the animation, connect it to "GetMarkerReachedSignal()"

kickAnimationTrack:GetMarkerReachedSignal("KickEnd"):Connect(function(paramString)

	print(paramString)

end)

task.wait(4)

-- Play the animation track

kickAnimationTrack:Play()

```

### [Non-humanoids](#non-humanoids)[](#non-humanoids)

To play animations on rigs that do not  contain a [Humanoid](/docs/reference/engine/classes/Humanoid) , you must create an [AnimationController](/docs/reference/engine/classes/AnimationController)  with a child [Animator](/docs/reference/engine/classes/Animator) . For example, the following [Script](/docs/reference/engine/classes/Script)  (assumed to be a direct child of the rig) loads a "kick" animation and plays it.

Script - Play Custom Animation on Character Rig

```

local rig = script.Parent

-- Create a new "Animation" instance and assign an animation asset ID

local kickAnimation = Instance.new("Animation")

kickAnimation.AnimationId = "rbxassetid://2515090838"

-- Create a new "AnimationController" and "Animator"

local animationController = Instance.new("AnimationController")

animationController.Parent = rig

local animator = Instance.new("Animator")

animator.Parent = animationController

-- Load the animation onto the animator

local kickAnimationTrack = animator:LoadAnimation(kickAnimation)

-- If a named event was defined for the animation, connect it to "GetMarkerReachedSignal()"

kickAnimationTrack:GetMarkerReachedSignal("KickEnd"):Connect(function(paramString)

	print(paramString)

end)

task.wait(4)

-- Play the animation track

kickAnimationTrack:Play()

```

## [Replace default animations](#replace-default-animations)[](#replace-default-animations)

By default, Roblox player characters include common animations like running, climbing, swimming, and jumping. You can replace these [default animations](#default-character-animations)  with animations from the [catalog](#catalog-animations)  or with your own [custom](/docs/animation/editor)  animations.

1.

Obtain the asset ID  of the new animation as follows:

-

For a custom animation built with the [Animation Editor](/docs/animation/editor) , follow the [export](/docs/animation/editor#exporting-an-animation)  instructions.

-

Copy an appropriate ID from the [catalog animation reference](#catalog-animations)  below. For example, to replace the default run animation with the [Ninja Run](https://www.roblox.com/catalog/658830056/Ninja-Run)  variant, use 656118852 .

2.

In the [Explorer](/docs/studio/explorer)  window, add a new [Script](/docs/reference/engine/classes/Script)  to ServerScriptService .

1.

Hover over ServerScriptService  and click the ⊕ button.

2.

From the contextual menu, insert a Script .

3.

In the new script, paste the following code:

Script - Replace Default Character Animations

```

local Players = game:GetService("Players")

local function onCharacterAdded(character)

	-- Get animator on humanoid

	local humanoid = character:WaitForChild("Humanoid")

	local animator = humanoid:WaitForChild("Animator")

	-- Stop all animation tracks

	for _, playingTrack in animator:GetPlayingAnimationTracks() do

		playingTrack:Stop(0)

	end

	local animateScript = character:WaitForChild("Animate")

	--animateScript.run.RunAnim.AnimationId = "rbxassetid://"

	--animateScript.walk.WalkAnim.AnimationId = "rbxassetid://"

	--animateScript.jump.JumpAnim.AnimationId = "rbxassetid://"

	--animateScript.idle.Animation1.AnimationId = "rbxassetid://"

	--animateScript.idle.Animation2.AnimationId = "rbxassetid://"

	--animateScript.fall.FallAnim.AnimationId = "rbxassetid://"

	--animateScript.swim.Swim.AnimationId = "rbxassetid://"

	--animateScript.swimidle.SwimIdle.AnimationId = "rbxassetid://"

	--animateScript.climb.ClimbAnim.AnimationId = "rbxassetid://"

end

local function onPlayerAdded(player)

	player.CharacterAppearanceLoaded:Connect(onCharacterAdded)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

4.

For each line that references a [default character animation](#default-character-animations) , uncomment it and paste the replacement ID after rbxassetid:// . For example, to change the default run animation to the [Ninja Run](https://www.roblox.com/catalog/658830056/Ninja-Run)  variant:

Script - Replace Default Character Animations

```

local Players = game:GetService("Players")

local function onCharacterAdded(character)

	-- Get animator on humanoid

	local humanoid = character:WaitForChild("Humanoid")

	local animator = humanoid:WaitForChild("Animator")

	-- Stop all animation tracks

	for _, playingTrack in animator:GetPlayingAnimationTracks() do

		playingTrack:Stop(0)

	end

	local animateScript = character:WaitForChild("Animate")

	animateScript.run.RunAnim.AnimationId = "rbxassetid://656118852"

	--animateScript.walk.WalkAnim.AnimationId = "rbxassetid://"

	--animateScript.jump.JumpAnim.AnimationId = "rbxassetid://"

	--animateScript.idle.Animation1.AnimationId = "rbxassetid://"

	--animateScript.idle.Animation2.AnimationId = "rbxassetid://"

	--animateScript.fall.FallAnim.AnimationId = "rbxassetid://"

	--animateScript.swim.Swim.AnimationId = "rbxassetid://"

	--animateScript.swimidle.SwimIdle.AnimationId = "rbxassetid://"

	--animateScript.climb.ClimbAnim.AnimationId = "rbxassetid://"

end

local function onPlayerAdded(player)

	player.CharacterAppearanceLoaded:Connect(onCharacterAdded)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

## [Set animation weights](#set-animation-weights)[](#set-animation-weights)

You can use multiple animations for the same action. For example, there are two idle  variations in the code sample for [replacing default animations](#replace-default-animations) .

When multiple animations exist for a character state, the Animate  script randomly chooses which one to play, but you can influence the outcome by setting the animation's Weight  value under the following formula:

-

animation weight / total weight of all state animations

In the following example, idle.Animation1  will play ⅓ of the time the character is idle, while idle.Animation2  will play ⅔ of the time.

Script - Replace Default Character Animations

```

animateScript.idle.Animation1.AnimationId = "rbxassetid://656117400"

	animateScript.idle.Animation2.AnimationId = "rbxassetid://656118341"

	animateScript.idle.Animation1.Weight.Value = 5

	animateScript.idle.Animation2.Weight.Value = 10

```

## [Animation references](#animation-references)[](#animation-references)

### [Default character animations](#default-character-animations)[](#default-character-animations)

The following table contains all of the default character animations that you can [replace](#replace-default-animations)  with [catalog](#catalog-animations)  animations or your own [custom](/docs/animation/editor)  animations. Note that Idle  has two variations which you can [weight](#set-animation-weights)  to play more or less frequently.

| Character action | | Animate script reference |
| --- | --- |
| Run | | animateScript.run.RunAnim.AnimationId |
| Walk | | animateScript.walk.WalkAnim.AnimationId |
| Jump | | animateScript.jump.JumpAnim.AnimationId |
| Idle | |

animateScript.idle.Animation1.AnimationId
 animateScript.idle.Animation2.AnimationId

 |
| Fall | | animateScript.fall.FallAnim.AnimationId |
| Swim | |

animateScript.swim.Swim.AnimationId

 |
| Swim (Idle) | |

animateScript.swimidle.SwimIdle.AnimationId

 |
| Climb | | animateScript.climb.ClimbAnim.AnimationId |

### [Catalog animations](#catalog-animations)[](#catalog-animations)

When using avatar animation bundles to [replace default animations](#replace-default-animations) , use the following references for the respective asset IDs. For example, if you want to apply the [Ninja Jump](https://www.roblox.com/catalog/658832070/Ninja-Jump)  animation, use 656117878 . Note that Idle  has multiple variations.

| [Astronaut](https://www.roblox.com/bundles/34/Astronaut-Animation-Pack) | |

Run
891636393

Walk
891636393

Jump
891627522

Idle
891621366, 891633237, 1047759695

Fall
891617961

Swim
891639666

Swim (Idle)
891663592

Climb
891609353

 |
| [Bubbly](https://www.roblox.com/bundles/39/Bubbly-Animation-Package) | |

Run
910025107

Walk
910034870

Jump
910016857

Idle
910004836, 910009958, 1018536639

Fall
910001910

Swim
910028158

Swim (Idle)
910030921

Climb
909997997

 |
| [Cartoony](https://www.roblox.com/bundles/56/Cartoony-Animation-Package) | |

Run
742638842

Walk
742640026

Jump
742637942

Idle
742637544, 742638445, 885477856

Fall
742637151

Swim
742639220

Swim (Idle)
742639812

Climb
742636889

 |
| [Elder](https://www.roblox.com/bundles/48/Elder-Animation-Package) | |

Run
845386501

Walk
845403856

Jump
845398858

Idle
845397899, 845400520, 901160519

Fall
845396048

Swim
845401742

Swim (Idle)
845403127

Climb
845392038

 |
| [Knight](https://www.roblox.com/bundles/68/Knight-Animation-Package) | |

Run
657564596

Walk
657552124

Jump
658409194

Idle
657595757, 657568135, 885499184

Fall
657600338

Swim
657560551

Swim (Idle)
657557095

Climb
658360781

 |
| [Levitation](https://www.roblox.com/bundles/79/Levitation-Animation-Pack) | |

Run
616010382

Walk
616013216

Jump
616008936

Idle
616006778, 616008087, 886862142

Fall
616005863

Swim
616011509

Swim (Idle)
616012453

Climb
616003713

 |
| [Mage](https://www.roblox.com/bundles/63/Mage-Animation-Package) | |

Run
707861613

Walk
707897309

Jump
707853694

Idle
707742142, 707855907, 885508740

Fall
707829716

Swim
707876443

Swim (Idle)
707894699

Climb
707826056

 |
| [Ninja](https://www.roblox.com/bundles/75/Ninja-Animation-Package) | |

Run
656118852

Walk
656121766

Jump
656117878

Idle
656117400, 656118341, 886742569

Fall
656115606

Swim
656119721

Swim (Idle)
656121397

Climb
656114359

 |
| [Pirate](https://www.roblox.com/bundles/55/Pirate-Animation-Package) | |

Run
750783738

Walk
750785693

Jump
750782230

Idle
750781874, 750782770, 885515365

Fall
750780242

Swim
750784579

Swim (Idle)
750785176

Climb
750779899

 |
| [Robot](https://www.roblox.com/bundles/82/Robot-Animation-Pack) | |

Run
616091570

Walk
616095330

Jump
616090535

Idle
616088211, 616089559, 885531463

Fall
616087089

Swim
616092998

Swim (Idle)
616094091

Climb
616086039

 |
| [Rthro](https://www.roblox.com/bundles/356/Rthro-Animation-Package) | |

Run
2510198475

Walk
2510202577

Jump
2510197830

Idle
2510197257, 2510196951, 3711062489

Fall
2510195892

Swim
2510199791

Swim (Idle)
2510201162

Climb
2510192778

 |
| [Stylish](https://www.roblox.com/bundles/83/Stylish-Animation-Pack) | |

Run
616140816

Walk
616146177

Jump
616139451

Idle
616136790, 616138447, 886888594

Fall
616134815

Swim
616143378

Swim (Idle)
616144772

Climb
616133594

 |
| [Superhero](https://www.roblox.com/bundles/81/Superhero-Animation-Pack) | |

Run
616117076

Walk
616122287

Jump
616115533

Idle
616111295, 616113536, 885535855

Fall
616108001

Swim
616119360

Swim (Idle)
616120861

Climb
616104706

 |
| [Toy](https://www.roblox.com/bundles/43/Toy-Animation-Pack) | |

Run
782842708

Walk
782843345

Jump
782847020

Idle
782841498, 782845736, 980952228

Fall
782846423

Swim
782844582

Swim (Idle)
782845186

Climb
782843869

 |
| [Vampire](https://www.roblox.com/bundles/33/Vampire-Animation-Pack) | |

Run
1083462077

Walk
1083473930

Jump
1083455352

Idle
1083445855, 1083450166, 1088037547

Fall
1083443587

Swim
1083464683

Swim (Idle)
1083467779

Climb
1083439238

 |
| [Werewolf](https://www.roblox.com/bundles/32/Werewolf-Animation-Pack) | |

Run
1083216690

Walk
1083178339

Jump
1083218792

Idle
1083195517, 1083214717, 1099492820

Fall
1083189019

Swim
1083222527

Swim (Idle)
1083225406

Climb
1083182000

 |
| [Zombie](https://www.roblox.com/bundles/80/Zombie-Animation-Pack) | |

Run
616163682

Walk
616168032

Jump
616161997

Idle
616158929, 616160636, 885545458

Fall
616157476

Swim
616165109

Swim (Idle)
616166655

Climb
616156119

 |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
