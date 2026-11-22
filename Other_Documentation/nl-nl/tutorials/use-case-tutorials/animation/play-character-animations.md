<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/animation/play-character-animations -->

Speel karakteranimaties | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Animatie
6. /
7. In Studio

# Speel karakteranimaties

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het spelen van karakteranimaties  is een belangrijk onderdeel van wat avatars en niet-speelbare personages (NPC's) expressief, realistisch en boeiend maakt voor je publiek. Naast het bieden van meeslepende visuals, geven karakteranimaties spelers feedback over hun acties, begeleiding over hoe ze zich in de omgeving kunnen bewegen, en belangrijke informatie over hun karakter en anderen.

Met het [Hazardous Space Station](https://www.roblox.com/games/134383324873456/Walking-Character-Animation)  .rbxl  bestand als referentie, laat deze tutorial je zien hoe je karakteranimaties kunt afspelen met behulp van twee verschillende technieken, inclusief begeleiding over:

-

Het verwisselen van standaard karakteranimatie asset-ID's met je eigen aangepaste animaties.

-

Het activeren van animaties als reactie op karakteracties binnen de 3D-ruimte.

Nadat je deze tutorial hebt voltooid, heb je de vaardigheden om animaties aan te passen voor een breed scala aan gameplay-situaties.

## [Wijzig standaardanimaties](#wijzig-standaardanimaties)[](#wijzig-standaardanimaties)

Elk karakter met een standaard [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  object, of het nu een door de speler bestuurde avatar of een niet-spelerspersonage (NPC) is, bevat een set standaardanimaties  die worden afgespeeld telkens wanneer het karakter specifieke in-game acties uitvoert, zoals rennen, klimmen en springen. Roblox biedt deze animaties standaard voor elk spel zonder extra scriptinginspanningen.

Standaard Valanimatie

Standaard Zwemanimatie

Standaard Klimanimatie

Als deze standaardanimaties echter niet voldoen aan de ontwerpeisen voor de omgeving, esthetiek of algehele narratief van jouw wereld, kun je ze vervangen door aangepaste animaties die van toepassing zijn op elke speler die jouw spel betreedt.

Om dit te demonstreren, leert de volgende sectie je hoe je de standaard loopanimatie kunt vervangen door een aangepaste loopcyclusanimatie van [Create Character Animations](/docs/nl-nl/tutorials/use-case-tutorials/animation/create-an-animation) . Met ditzelfde proces kun je elke standaardanimatie vervangen door je eigen animatie asset-ID's.

Standaard Loopanimatie

Aangepaste Loopanimatie

### [Maak script](#maak-script)[](#maak-script)

Elk karakter's [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  object bevat een kind [Animator](/docs/nl-nl/reference/engine/classes/Animator)  object dat alle standaardanimaties van het karakter opslaat. Om een van deze standaardanimaties in te stellen op nieuwe asset-ID's, moet je een script maken in de [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService)  zodat het de standaardwaarden van het [Animator](/docs/nl-nl/reference/engine/classes/Animator)  object kan refereren en overschrijven zodra spelers in het spel laden.

Om een script te maken dat de standaard animatie asset-ID's referentieert:

1.

In het Explorer  venster, voeg een nieuw script toe aan ServerScriptService .

1.

Beweeg de muis over ServerScriptService  en klik op de ⊕ knop.

2.

Kies in het contextmenu een Script .

2.

Plak in het nieuwe script de volgende code:

```

local Players = game:GetService("Players")

local function onCharacterAdded(character)

    local humanoid = character:WaitForChild("Humanoid")

    local animator = humanoid:WaitForChild("Animator")

    print("Animator gevonden!")

end

local function onPlayerAdded(player)

    player.CharacterAdded:Connect(onCharacterAdded)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Code Uitleg

Het ResetDefaultAnimations  script begint met het verkrijgen van de [Players](/docs/nl-nl/reference/engine/classes/Players)  service, die alle [Player](/docs/nl-nl/reference/engine/classes/Player)  objecten bevat voor spelers die verbinding maken met een server. Wanneer elk van de spelers' karakters in het spel laden, wacht de [onCharacterAdded](/docs/nl-nl/reference/engine/classes/Player#onCharacterAdded)  functie totdat het het [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  en [Animator](/docs/nl-nl/reference/engine/classes/Animator)  objecten van het karakter detecteert.

Wanneer het voor het eerst een [Animator](/docs/nl-nl/reference/engine/classes/Animator)  object detecteert, print het script "Animator gevonden!" om je te laten weten dat het script werkt zoals bedoeld.

### [Vervang asset-ID](#vervang-asset-id)[](#vervang-asset-id)

Nu je weet dat je script in staat is om te detecteren wanneer spelers laden en verbinding maken met de server, kun je je script aanpassen om specifiek te verwijzen naar de animatie-ID's die je wilt vervangen door je eigen aangepaste animaties.

De volgende tabel bevat alle standaard karakteranimaties die je kunt aanroepen en vervangen binnen het [Animator](/docs/nl-nl/reference/engine/classes/Animator)  object. Let op dat Idle twee variaties heeft die je kunt programmeren om vaker of minder vaak af te spelen.

| Karakteractie | | Animate Script Referentie |
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

Om de standaard loopanimatie asset-ID te vervangen:

1.

Roep de standaard loop animate script referentie aan, en vervang vervolgens de asset-ID door je eigen aangepaste animatie asset-ID. Bijvoorbeeld, de volgende code verwijst naar de loopcyclusanimatie van [Create Character Animations](/docs/nl-nl/tutorials/use-case-tutorials/animation/create-an-animation) .

```

local Players = game:GetService("Players")

local function onCharacterAdded(character)

    local humanoid = character:WaitForChild("Humanoid")

    local animator = humanoid:WaitForChild("Animator")

    print("Animator gevonden!")

    local animateScript = character:WaitForChild("Animate")

    animateScript.walk.WalkAnim.AnimationId = "rbxassetid://122652394532816"

end

local function onPlayerAdded(player)

    player.CharacterAdded:Connect(onCharacterAdded)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

2.

Speel je spel om te testen of je aangepaste loopanimatie de standaardanimatie overschrijft.

1.

Kies Test  in het dropdownmenu en klik op de Speel  knop aan de rechterkant om de playtest te starten.

 ![Testoptie in het dropdownmenu van de testmodi van de mezzanine van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Mode-Test.png)

2.

Loop rond in het ruimtevaartuig met je avatar.

## [Trigger animaties](#trigger-animaties)[](#trigger-animaties)

Terwijl de vorige techniek zich richt op het verwisselen van standaardanimaties die automatisch worden afgespeeld telkens wanneer een karakter specifieke in-game acties uitvoert, kun je programmatisch animaties activeren om af te spelen als reactie op elke  karakteractie binnen de 3D-ruimte, zoals het oppakken van een item of het oplopen van schade door een gevaar.

In dit voorbeeld, wanneer spelers de gouden platform aanraken, activeren ze een niet-standaard karakterdansanimatie.

Deze methode van het afspelen van animaties is nuttig omdat het spelers onmiddellijke feedback geeft over hoe ze met objecten in hun omgeving moeten omgaan. Om dit te demonstreren, laat de volgende sectie je zien hoe je een animatie kunt activeren telkens wanneer karakters te dicht bij gevaarlijke stoomlekkages komen als een manier om spelers subtiel te leren vermijden te dicht bij de muren te lopen.

### [Voeg volume toe](#voeg-volume-toe)[](#voeg-volume-toe)

Een van de meest voorkomende manieren om unieke gameplay-gedragingen te activeren, is door volumes  te gebruiken, of onzichtbare gebieden binnen de 3D-ruimte, om te detecteren wanneer karakters of objecten interactie hebben met specifieke gebieden van de omgeving. Wanneer je volumes koppelt aan scripts, kun je hun botsingfeedback gebruiken om programmatisch acties te activeren, zoals het verminderen van de gezondheid van de speler of het afspelen van een animatie.

![Een ver uitzicht op een kamer in een herenhuis. Een omtrek van een doos is in het midden van de kamer om het volume aan te geven dat gameplay-evenementen activeert.](https://prod.docsiteassets.roblox.com/assets/tutorials/playing-character-animations/Volume-Example.jpg) The Mystery of Duvall Drive gebruikt volumes om gameplay-evenementen te activeren die de visuele uitstraling van de kamer veranderen.

Bij het toevoegen van een volume aan je spel, is het belangrijk om het zo te schalen dat het alleen de ruimte dekt die je wilt gebruiken om je animatie te activeren. Als je je volume te klein maakt, kunnen spelers nooit met het gebied botsen om de animatie af te spelen; omgekeerd, als je je volume te groot maakt, zal de animatie afspelen voordat spelers het item of het gebied van interesse bereiken, en ze begrijpen misschien niet wat ze hebben gedaan om de animatie te activeren.

Om een volume rond een stoomlek toe te voegen dat een animatie zal activeren:

1.

In het Explorer  venster, voeg een nieuw blokdeel toe.

2.

Positioneer en wijzig de grootte van het blok totdat het het gebied bedekt dat je wilt gebruiken om je animatie te activeren.

3.

In het Properties  venster,

1.

Stel Naam  in op AnimationDetector .

2.

Stel Transparantie  in op 1  om het blok onzichtbaar te maken.

 ![Een omtrek van een blok is zichtbaar rond een stoomventiel om de positie van het volume aan te geven.](https://prod.docsiteassets.roblox.com/assets/tutorials/playing-character-animations/Insert-Volume-3.jpg)

### [Maak script](#maak-script-1)[](#maak-script-1)

Nu je een gedefinieerd gebied hebt voor het activeren van je animatie, is het tijd om een script te maken dat programmatisch detecteert wanneer spelers met het volume botsen. Je kunt dan luisteren naar botsingsevenementen om elke animatie te activeren die logisch is voor jouw gameplay-eisen.

Bijvoorbeeld, deze animatietechniek gebruikt een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  in plaats van een [Script](/docs/nl-nl/reference/engine/classes/Script)  om spelers onmiddellijke feedback te geven wanneer ze met het volume botsen. Als de server naar de botsing zou luisteren en de animatie zou afspelen, zou er een vertraging kunnen zijn tussen het aanraken van het volume door de speler op hun client en het zien van de animatie omdat van de replicatietijd van de server naar de client.

Om een lokaal script te maken dat detecteert wanneer het lokale karakter van de speler het volume aanraakt:

1.

In het Explorer  venster, voeg een nieuw script toe aan StarterCharacterScripts . Deze plaatsing zorgt ervoor dat het script en zijn kinderen worden gekloond in het spelerskarakter bij het joinen en  wanneer ze opnieuw in het spel respawnen.

1.

Vouw StarterPlayer  uit, beweeg de muis over zijn StarterCharacterScripts  kind en klik op de ⊕ knop.

2.

Kies in het contextmenu een LocalScript  en hernoem het naar TriggerAnimation .

2.

Plak in het nieuwe script de volgende code:

```

local Workspace = game:GetService("Workspace")

local animation = script:WaitForChild("Animation")

local humanoid = script.Parent:WaitForChild("Humanoid")

local animator = humanoid:WaitForChild("Animator")

local animationTrack = animator:LoadAnimation(animation)

local animationDetector = Workspace:WaitForChild("AnimationDetector")

local debounce = false

animationDetector.Touched:Connect(function(hit)

    if debounce then

 	   return

    end

    local hitCharacter = hit:FindFirstAncestorWhichIsA("Model")

    if hitCharacter ~= localCharacter then

 	   return

    end

    debounce = true

    animationTrack:Play()

    animationTrack.Ended:Wait()

    debounce = false

end)

```

Code Uitleg

Het TriggerAnimation  script begint met het verkrijgen van de [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  service, die alle objecten bevat die bestaan in de 3D-wereld. Dit is belangrijk omdat het script het [Part](/docs/nl-nl/reference/engine/classes/Part)  object moet refereren dat als je volume fungeert.

Voor elk spelerskarakter dat in het spel laadt of opnieuw respawnt, wacht het script op:

-

Het kind [Animation](/docs/nl-nl/reference/engine/classes/Animation)  object, dat je in de volgende sectie zult toevoegen.

-

Het [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  en [Animator](/docs/nl-nl/reference/engine/classes/Animator)  objecten van het karakter.

-

Het volume-object in de werkruimte met de naam AnimationDetector .

Wanneer iets met het volume botst, krijgt de Touched  event handler functie de eerste voorouder die een [Model](/docs/nl-nl/reference/engine/classes/Model)  is, wat het karakter zou moeten zijn als de [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  die met het volume botste een afstammeling is van een karaktermodel. Als dat zo is, controleert de functie of het [Model](/docs/nl-nl/reference/engine/classes/Model)  het lokale  karakter van de speler is. Als dat zo is, dan:

-

Zet debounce op true .

-

Speelt de animatie af en wacht tot deze eindigt.

-

Zet debounce terug op false .

Het instellen van debounce van false  naar true  en weer terug naar false  nadat de animatie is afgelopen, is een debounce-patroon dat voorkomt dat de animatie herhaaldelijk wordt geactiveerd terwijl spelers continu met het volume botsen. Voor meer informatie over dit debounce-patroon, zie [Detecteer botsingen](/docs/nl-nl/scripting/debounce#detecteer-botsingen) .

### [Voeg animatie toe](#voeg-animatie-toe)[](#voeg-animatie-toe)

Als je je spel op dit moment zou testen, zou je TriggerAnimation  script nog steeds niet in staat zijn om een animatie af te spelen als reactie op de botsing van de lokale speler met het volume. Dit komt omdat het wacht op een kind [Animation](/docs/nl-nl/reference/engine/classes/Animation)  object met een animatie asset-ID die het kan refereren, en dat [Animation](/docs/nl-nl/reference/engine/classes/Animation)  object bestaat momenteel niet.

Om een animatie toe te voegen die het lokale script kan refereren wanneer spelers met het volume botsen:

1.

In het Explorer  venster, voeg een nieuwe animatie toe aan TriggerAnimation .

1.

Beweeg de muis over TriggerAnimation  en klik op de ⊕ knop.

2.

Kies in het contextmenu een Animation .

2.

Selecteer het nieuwe animatieobject, en stel in het Properties  venster AnimationID  in op de animatie asset-ID die je wilt activeren wanneer spelers het volume aanraken. Bijvoorbeeld, het [Hazardous Space Station](https://www.roblox.com/games/134383324873456/Walking-Character-Animation)  voorbeeld verwijst naar rbxassetid://3716468774  om een animatie van een karakter dat achterover valt af te spelen.

3.

Speel je spel om te testen of je animatie afspeelt wanneer spelers in de buurt zijn van de eerste stoomlek.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
