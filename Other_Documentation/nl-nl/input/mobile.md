<!-- Source: https://create.roblox.com/docs/nl-nl/input/mobile -->

Mobiele invoer | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Input](/docs/nl-nl/input)

# Mobiele invoer

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De meerderheid van de Roblox-sessies wordt gespeeld op mobiele apparaten, dus het is belangrijk om rekening te houden met de mobiele [apparaatoriëntatie](#apparaatori%C3%ABntatie)  en andere [cross‑platform](/docs/nl-nl/projects/cross-platform)  factoren bij het ontwerpen van een game voor een breed publiek.

Om cross‑platform invoer te vereenvoudigen, inclusief de interactie van spelers met virtuele knoppen, biedt Roblox het [Input Action System](/docs/nl-nl/input/input-action-system)  om acties  zoals "springen", "rennen" of "schieten" te definiëren en bindingen  in te stellen voor meerdere hardware-invoeren om die acties aan te sturen.

Roblox ondersteunt ook native mobiele functies zoals [haptische feedback](#haptische-feedback) , aanrakinggebaren zoals [TouchSwipe](/docs/nl-nl/reference/engine/classes/UserInputService#TouchSwipe)  en [TouchPinch](/docs/nl-nl/reference/engine/classes/UserInputService#TouchPinch) , of versnellingsmeter- en gyroscoopfunctionaliteit op [AccelerometerEnabled](/docs/nl-nl/reference/engine/classes/UserInputService#AccelerometerEnabled)  en [GyroscopeEnabled](/docs/nl-nl/reference/engine/classes/UserInputService#GyroscopeEnabled)  apparaten.

## [Invoertype-detectie](#invoertype-detectie)[](#invoertype-detectie)

Bij cross‑platform ontwikkeling is het belangrijk dat je het [PreferredInput](/docs/nl-nl/reference/engine/classes/UserInputService#PreferredInput)  type bepaalt en hierop reageert dat een speler gebruikt, normaal gesproken om ervoor te zorgen dat [UI elementen](/docs/nl-nl/ui#ui-objecten)  zoals knoppen en menu's op het scherm elegant werken en interactie tussen apparaten ondersteunen.

Bijvoorbeeld, een apparaat met aanraakfunctionaliteit gaat ervan uit dat aanraking de standaardinvoer is en dat aanraakknoppen kunnen verschijnen voor acties, maar een speler kan ervoor kiezen om een bluetooth-gamepad aan te sluiten. In dit geval blijft aanraking een geldige invoer, maar je kunt aannemen dat de speler wil overschakelen naar de aangesloten gamepad als het primaire  invoertype en mogelijk aanraking als een back-upinvoer voor de UI op het scherm gebruiken.

Zie [invoertype-detectie](/docs/nl-nl/input#invoertype-detectie)  voor meer informatie.

## [Apparaatoriëntatie](#apparaatoriëntatie)[](#apparaatoriëntatie)

Standaard draaien Roblox-games in landschap  modus, waardoor de game kan schakelen tussen landschap "links" en landschap "rechts" naarmate het apparaat van de speler draait. Games kunnen echter worden vergrendeld in een bepaalde oriëntatie indien gewenst.

Er zijn vijf verschillende oriëntatiemodi, waaronder twee sensor-gebaseerde modi en drie vergrendelde modi.¹ Elk van deze kan worden ingesteld als de standaard  oriëntatie via [StarterGui.ScreenOrientation](/docs/nl-nl/reference/engine/classes/StarterGui#ScreenOrientation) , toegankelijk via het [Eigenschappen](/docs/nl-nl/studio/properties)  venster van Studio.

| Sensor Modi |
| --- | --- |
| [LandscapeSensor](/docs/nl-nl/reference/engine/enums/ScreenOrientation) | | De standaardinstelling van Roblox waarin de game altijd in landschapmodus verschijnt (geen portretmodus) en het apparaat zijn fysieke oriëntatie detecteert om ervoor te zorgen dat het gamebeeld altijd naar boven is gericht. |
| [Sensor](/docs/nl-nl/reference/engine/enums/ScreenOrientation) | | Het apparaat detecteert zijn fysieke oriëntatie om ervoor te zorgen dat het gamebeeld altijd naar boven is gericht, en schakelt tussen landschap- en portretmodus indien nodig. |
| Vergrendelde Modi |
| [LandscapeLeft](/docs/nl-nl/reference/engine/enums/ScreenOrientation) | | Op apparaten met een virtuele home/navigatiebalk bevindt het aanraakgebied zich onderaan het scherm. Op apparaten met een fysieke homeknop bevindt de homeknop zich links van het scherm. |
| [LandscapeRight](/docs/nl-nl/reference/engine/enums/ScreenOrientation) | | Op apparaten met een virtuele home/navigatiebalk bevindt het aanraakgebied zich onderaan het scherm. Op apparaten met een fysieke homeknop bevindt de homeknop zich rechts van het scherm. |
| [Portrait](/docs/nl-nl/reference/engine/enums/ScreenOrientation) | | Op apparaten met een virtuele home/navigatiebalk bevindt het aanraakgebied zich onderaan het scherm. Op apparaten met een fysieke homeknop bevindt de homeknop zich onder het scherm. |

 ¹ Roblox bevat geen "portret ondersteboven" modus omdat veel apparaten deze oriëntatie niet native ondersteunen

Naast de standaard [StarterGui.ScreenOrientation](/docs/nl-nl/reference/engine/classes/StarterGui#ScreenOrientation)  eigenschap, kun je de oriëntatie tijdens het spelen wijzigen via [PlayerGui.ScreenOrientation](/docs/nl-nl/reference/engine/classes/PlayerGui#ScreenOrientation) . Dit kan nuttig zijn wanneer een game een oriëntatie moet afdwingen, zoals het vergrendelen van het beeld op [Portrait](/docs/nl-nl/reference/engine/enums/ScreenOrientation)  voor een minigame.

De volgende code in een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  stelt de schermoriëntatie in op portret na een korte vertraging:

LocalScript - Wijzig Schermoriëntatie naar Portret

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local playerGui = player.PlayerGui

task.wait(5)

playerGui.ScreenOrientation = Enum.ScreenOrientation.Portrait

```

Ten slotte kun je wijzigingen in de schermoriëntatie tijdens het spelen detecteren door te luisteren naar waarde wijzigingen op de [PlayerGui.CurrentScreenOrientation](/docs/nl-nl/reference/engine/classes/PlayerGui#CurrentScreenOrientation)  eigenschap.

LocalScript - Detecteer Wijzigingen in Schermoriëntatie

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local playerGui = player.PlayerGui

local function onOrientationChange()

	print("Oriëntatie gewijzigd naar", playerGui.ScreenOrientation)

end

playerGui:GetPropertyChangedSignal("ScreenOrientation"):Connect(onOrientationChange)

```

## [Haptische feedback](#haptische-feedback)[](#haptische-feedback)

De meeste mobiele apparaten hebben motoren ingebouwd om haptische feedback te bieden. Het toevoegen van trillingen en vibraties kan de ervaring van een speler aanzienlijk verbeteren en subtiele feedback bieden naast visuele of audio-informatie.

Roblox ondersteunt haptiek voor haptische apparaten, waaronder de meeste iPhone-, Pixel- en Samsung Galaxy-apparaten. Haptische feedback wordt beheerd via [HapticEffect](/docs/nl-nl/reference/engine/classes/HapticEffect)  instanties die kunnen worden ingesteld op een specifieke [Type](/docs/nl-nl/reference/engine/classes/HapticEffect#Type)  zoals [GameplayCollision](/docs/nl-nl/reference/engine/enums/HapticEffectType)  of [UIClick](/docs/nl-nl/reference/engine/enums/HapticEffectType) .

Zodra een [HapticEffect](/docs/nl-nl/reference/engine/classes/HapticEffect)  is ingesteld, kun je deze starten via de [Play()](/docs/nl-nl/reference/engine/classes/HapticEffect#Play)  methode, bijvoorbeeld:

```

local Workspace = game:GetService("Workspace")

local effect = Instance.new("HapticEffect")

effect.Type = Enum.HapticEffectType.GameplayExplosion

effect.Parent = Workspace

-- Speel het haptische effect af

effect:Play()

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
