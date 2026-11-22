<!-- Source: https://create.roblox.com/docs/nl-nl/animation/using -->

Gebruik animaties | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Animatie](/docs/nl-nl/animation)

# Gebruik animaties

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Zodra je een [animatie hebt gemaakt](/docs/nl-nl/animation/editor) , moet je scripts gebruiken om ze in je spel op te nemen. Je kunt animaties ofwel [handmatig afspelen](#animaties-afspelen-vanuit-scripts)  vanuit scripts of [standaardanimaties vervangen](#standaardanimaties-vervangen)  voor spelerspersonages.

## [Animaties afspelen vanuit scripts](#animaties-afspelen-vanuit-scripts)[](#animaties-afspelen-vanuit-scripts)

In sommige gevallen moet je een animatie rechtstreeks vanuit een script afspelen, bijvoorbeeld wanneer een gebruiker een bepaalde toets indrukt of een speciaal item oppakt.

### [Humanoïden](#humanoïden)[](#humanoïden)

Om een animatie af te spelen op een rig die een [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  object bevat, zoals typische speelbare personages, volg je dit basispatroon:

1.

Zorg ervoor dat de [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  van de lokale speler een [Animator](/docs/nl-nl/reference/engine/classes/Animator)  object bevat.

2.

Maak een nieuwe [Animation](/docs/nl-nl/reference/engine/classes/Animation)  instantie met de juiste [AnimationId](/docs/nl-nl/reference/engine/classes/Animation#AnimationId) .

3.

Laad de animatie via [Animator:LoadAnimation()](/docs/nl-nl/reference/engine/classes/Animator#LoadAnimation)  om een [AnimationTrack](/docs/nl-nl/reference/engine/classes/AnimationTrack)  te creëren.

4.

Speel de track af met [AnimationTrack:Play()](/docs/nl-nl/reference/engine/classes/AnimationTrack#Play) .

Bijvoorbeeld, de volgende [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript) , wanneer geplaatst in [StarterPlayerScripts](/docs/nl-nl/reference/engine/classes/StarterPlayerScripts) , laadt een "kick" animatie op het personage van de speler en speelt deze af. Het script maakt ook gebruik van de [GetMarkerReachedSignal()](/docs/nl-nl/reference/engine/classes/AnimationTrack#GetMarkerReachedSignal)  methode om te detecteren wanneer een specifieke [animatie-evenement](/docs/nl-nl/animation/events)  plaatsvindt.

LocalScript - Speel Aangepaste Animatie op Speler Personage

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local character = player.Character or player.CharacterAdded:Wait()

-- Zorg ervoor dat het humanoïde van het personage een "Animator" object bevat

local humanoid = character:WaitForChild("Humanoid")

local animator = humanoid:WaitForChild("Animator")

-- Maak een nieuwe "Animation" instantie en wijs een animatie asset ID toe

local kickAnimation = Instance.new("Animation")

kickAnimation.AnimationId = "rbxassetid://2515090838"

-- Laad de animatie op de animator

local kickAnimationTrack = animator:LoadAnimation(kickAnimation)

-- Als er een benoemd evenement is gedefinieerd voor de animatie, verbind het met "GetMarkerReachedSignal()"

kickAnimationTrack:GetMarkerReachedSignal("KickEnd"):Connect(function(paramString)

	print(paramString)

end)

task.wait(4)

-- Speel de animatietrack af

kickAnimationTrack:Play()

```

### [Niet-humanoïden](#niet-humanoïden)[](#niet-humanoïden)

Om animaties af te spelen op rigs die geen  [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  bevatten, moet je een [AnimationController](/docs/nl-nl/reference/engine/classes/AnimationController)  maken met een kind [Animator](/docs/nl-nl/reference/engine/classes/Animator) . Bijvoorbeeld, de volgende [Script](/docs/nl-nl/reference/engine/classes/Script)  (aangenomen dat het een directe kind van de rig is) laadt een "kick" animatie en speelt deze af.

Script - Speel Aangepaste Animatie op Personage Rig

```

local rig = script.Parent

-- Maak een nieuwe "Animation" instantie en wijs een animatie asset ID toe

local kickAnimation = Instance.new("Animation")

kickAnimation.AnimationId = "rbxassetid://2515090838"

-- Maak een nieuwe "AnimationController" en "Animator"

local animationController = Instance.new("AnimationController")

animationController.Parent = rig

local animator = Instance.new("Animator")

animator.Parent = animationController

-- Laad de animatie op de animator

local kickAnimationTrack = animator:LoadAnimation(kickAnimation)

-- Als er een benoemd evenement is gedefinieerd voor de animatie, verbind het met "GetMarkerReachedSignal()"

kickAnimationTrack:GetMarkerReachedSignal("KickEnd"):Connect(function(paramString)

	print(paramString)

end)

task.wait(4)

-- Speel de animatietrack af

kickAnimationTrack:Play()

```

## [Standaardanimaties vervangen](#standaardanimaties-vervangen)[](#standaardanimaties-vervangen)

Standaard bevatten Roblox-spelerspersonages veelvoorkomende animaties zoals rennen, klimmen, zwemmen en springen. Je kunt deze [standaardanimaties](#standaard-personage-animaties)  vervangen door animaties uit de [catalogus](#catalogus-animaties)  of door je eigen [aangepaste](/docs/nl-nl/animation/editor)  animaties.

1.

Verkrijg de asset ID  van de nieuwe animatie als volgt:

-

Voor een aangepaste animatie gemaakt met de [Animatie-editor](/docs/nl-nl/animation/editor) , volg de [export](/docs/nl-nl/animation/editor#exporting-an-animation)  instructies.

-

Kopieer een geschikte ID uit de [catalogus animatie referentie](#catalogus-animaties)  hieronder. Bijvoorbeeld, om de standaard loopanimatie te vervangen door de [Ninja Run](https://www.roblox.com/catalog/658830056/Ninja-Run)  variant, gebruik 656118852 .

2.

Voeg in het [Explorer](/docs/nl-nl/studio/explorer)  venster een nieuwe [Script](/docs/nl-nl/reference/engine/classes/Script)  toe aan ServerScriptService .

1.

Beweeg over ServerScriptService  en klik op de ⊕ knop.

2.

Kies in het contextmenu een Script .

3.

Plak in het nieuwe script de volgende code:

Script - Vervang Standaard Personage Animaties

```

local Players = game:GetService("Players")

local function onCharacterAdded(character)

	-- Verkrijg animator op humanoïde

	local humanoid = character:WaitForChild("Humanoid")

	local animator = humanoid:WaitForChild("Animator")

	-- Stop alle animatietracks

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

Voor elke regel die verwijst naar een [standaard personage animatie](#standaard-personage-animaties) , verwijder de commentaar en plak de vervangings-ID na rbxassetid:// . Bijvoorbeeld, om de standaard loopanimatie te veranderen naar de [Ninja Run](https://www.roblox.com/catalog/658830056/Ninja-Run)  variant:

Script - Vervang Standaard Personage Animaties

```

local Players = game:GetService("Players")

local function onCharacterAdded(character)

	-- Verkrijg animator op humanoïde

	local humanoid = character:WaitForChild("Humanoid")

	local animator = humanoid:WaitForChild("Animator")

	-- Stop alle animatietracks

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

## [Stel animatiewaarden in](#stel-animatiewaarden-in)[](#stel-animatiewaarden-in)

Je kunt meerdere animaties voor dezelfde actie gebruiken. Bijvoorbeeld, er zijn twee idle  variaties in de codevoorbeeld voor [het vervangen van standaardanimaties](#standaardanimaties-vervangen) .

Wanneer meerdere animaties bestaan voor een karakterstatus, kiest het Animate  script willekeurig welke af te spelen, maar je kunt de uitkomst beïnvloeden door de Weight  waarde van de animatie in te stellen volgens de volgende formule:

-

animatiegewicht / totaal gewicht van alle statusanimaties

In het volgende voorbeeld zal idle.Animation1  ⅓ van de tijd afspelen wanneer het karakter idle is, terwijl idle.Animation2  ⅔ van de tijd zal afspelen.

Script - Vervang Standaard Personage Animaties

```

animateScript.idle.Animation1.AnimationId = "rbxassetid://656117400"

	animateScript.idle.Animation2.AnimationId = "rbxassetid://656118341"

	animateScript.idle.Animation1.Weight.Value = 5

	animateScript.idle.Animation2.Weight.Value = 10

```

## [Animatiereferenties](#animatiereferenties)[](#animatiereferenties)

### [Standaard personage animaties](#standaard-personage-animaties)[](#standaard-personage-animaties)

De volgende tabel bevat alle standaard personage animaties die je kunt [vervangen](#standaardanimaties-vervangen)  met [catalogus](#catalogus-animaties)  animaties of je eigen [aangepaste](/docs/nl-nl/animation/editor)  animaties. Let op dat Idle  twee variaties heeft die je kunt [wegen](#stel-animatiewaarden-in)  om vaker of minder vaak af te spelen.

| Personage actie | | Animate script referentie |
| --- | --- |
| Rennen | | animateScript.run.RunAnim.AnimationId |
| Lopen | | animateScript.walk.WalkAnim.AnimationId |
| Springen | | animateScript.jump.JumpAnim.AnimationId |
| Idle | |

animateScript.idle.Animation1.AnimationId
 animateScript.idle.Animation2.AnimationId

 |
| Vallen | | animateScript.fall.FallAnim.AnimationId |
| Zwemmen | |

animateScript.swim.Swim.AnimationId

 |
| Zwemmen (Idle) | |

animateScript.swimidle.SwimIdle.AnimationId

 |
| Klimmen | | animateScript.climb.ClimbAnim.AnimationId |

### [Catalogus animaties](#catalogus-animaties)[](#catalogus-animaties)

Bij het gebruik van avatar animatiebundels om [standaardanimaties te vervangen](#standaardanimaties-vervangen) , gebruik de volgende referenties voor de respectieve asset ID's. Bijvoorbeeld, als je de [Ninja Jump](https://www.roblox.com/catalog/658832070/Ninja-Jump)  animatie wilt toepassen, gebruik dan 656117878 . Let op dat Idle  meerdere variaties heeft.

| [Astronaut](https://www.roblox.com/bundles/34/Astronaut-Animation-Pack) | |

Rennen
891636393

Lopen
891636393

Springen
891627522

Idle
891621366, 891633237, 1047759695

Vallen
891617961

Zwemmen
891639666

Zwemmen (Idle)
891663592

Klimmen
891609353

 |
| [Bubbly](https://www.roblox.com/bundles/39/Bubbly-Animation-Package) | |

Rennen
910025107

Lopen
910034870

Springen
910016857

Idle
910004836, 910009958, 1018536639

Vallen
910001910

Zwemmen
910028158

Zwemmen (Idle)
910030921

Klimmen
909997997

 |
| [Cartoony](https://www.roblox.com/bundles/56/Cartoony-Animation-Package) | |

Rennen
742638842

Lopen
742640026

Springen
742637942

Idle
742637544, 742638445, 885477856

Vallen
742637151

Zwemmen
742639220

Zwemmen (Idle)
742639812

Klimmen
742636889

 |
| [Elder](https://www.roblox.com/bundles/48/Elder-Animation-Package) | |

Rennen
845386501

Lopen
845403856

Springen
845398858

Idle
845397899, 845400520, 901160519

Vallen
845396048

Zwemmen
845401742

Zwemmen (Idle)
845403127

Klimmen
845392038

 |
| [Knight](https://www.roblox.com/bundles/68/Knight-Animation-Package) | |

Rennen
657564596

Lopen
657552124

Springen
658409194

Idle
657595757, 657568135, 885499184

Vallen
657600338

Zwemmen
657560551

Zwemmen (Idle)
657557095

Klimmen
658360781

 |
| [Levitation](https://www.roblox.com/bundles/79/Levitation-Animation-Pack) | |

Rennen
616010382

Lopen
616013216

Springen
616008936

Idle
616006778, 616008087, 886862142

Vallen
616005863

Zwemmen
616011509

Zwemmen (Idle)
616012453

Klimmen
616003713

 |
| [Mage](https://www.roblox.com/bundles/63/Mage-Animation-Package) | |

Rennen
707861613

Lopen
707897309

Springen
707853694

Idle
707742142, 707855907, 885508740

Vallen
707829716

Zwemmen
707876443

Zwemmen (Idle)
707894699

Klimmen
707826056

 |
| [Ninja](https://www.roblox.com/bundles/75/Ninja-Animation-Package) | |

Rennen
656118852

Lopen
656121766

Springen
656117878

Idle
656117400, 656118341, 886742569

Vallen
656115606

Zwemmen
656119721

Zwemmen (Idle)
656121397

Klimmen
656114359

 |
| [Pirate](https://www.roblox.com/bundles/55/Pirate-Animation-Package) | |

Rennen
750783738

Lopen
750785693

Springen
750782230

Idle
750781874, 750782770, 885515365

Vallen
750780242

Zwemmen
750784579

Zwemmen (Idle)
750785176

Klimmen
750779899

 |
| [Robot](https://www.roblox.com/bundles/82/Robot-Animation-Pack) | |

Rennen
616091570

Lopen
616095330

Springen
616090535

Idle
616088211, 616089559, 885531463

Vallen
616087089

Zwemmen
616092998

Zwemmen (Idle)
616094091

Klimmen
616086039

 |
| [Rthro](https://www.roblox.com/bundles/356/Rthro-Animation-Package) | |

Rennen
2510198475

Lopen
2510202577

Springen
2510197830

Idle
2510197257, 2510196951, 3711062489

Vallen
2510195892

Zwemmen
2510199791

Zwemmen (Idle)
2510201162

Klimmen
2510192778

 |
| [Stylish](https://www.roblox.com/bundles/83/Stylish-Animation-Pack) | |

Rennen
616140816

Lopen
616146177

Springen
616139451

Idle
616136790, 616138447, 886888594

Vallen
616134815

Zwemmen
616143378

Zwemmen (Idle)
616144772

Klimmen
616133594

 |
| [Superhero](https://www.roblox.com/bundles/81/Superhero-Animation-Pack) | |

Rennen
616117076

Lopen
616122287

Springen
616115533

Idle
616111295, 616113536, 885535855

Vallen
616108001

Zwemmen
616119360

Zwemmen (Idle)
616120861

Klimmen
616104706

 |
| [Toy](https://www.roblox.com/bundles/43/Toy-Animation-Pack) | |

Rennen
782842708

Lopen
782843345

Springen
782847020

Idle
782841498, 782845736, 980952228

Vallen
782846423

Zwemmen
782844582

Zwemmen (Idle)
782845186

Klimmen
782843869

 |
| [Vampire](https://www.roblox.com/bundles/33/Vampire-Animation-Pack) | |

Rennen
1083462077

Lopen
1083473930

Springen
1083455352

Idle
1083445855, 1083450166, 1088037547

Vallen
1083443587

Zwemmen
1083464683

Zwemmen (Idle)
1083467779

Klimmen
1083439238

 |
| [Werewolf](https://www.roblox.com/bundles/32/Werewolf-Animation-Pack) | |

Rennen
1083216690

Lopen
1083178339

Springen
1083218792

Idle
1083195517, 1083214717, 1099492820

Vallen
1083189019

Zwemmen
1083222527

Zwemmen (Idle)
1083225406

Klimmen
1083182000

 |
| [Zombie](https://www.roblox.com/bundles/80/Zombie-Animation-Pack) | |

Rennen
616163682

Lopen
616168032

Springen
616161997

Idle
616158929, 616160636, 885545458

Vallen
616157476

Zwemmen
616165109

Zwemmen (Idle)
616166655

Klimmen
616156119

 |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
