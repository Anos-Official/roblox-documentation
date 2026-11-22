<!-- Source: https://create.roblox.com/docs/nl-nl/input/gamepad -->

Gamepad-invoer | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Input](/docs/nl-nl/input)

# Gamepad-invoer

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Roblox accepteert invoer van gamepads zoals Xbox- en PlayStation-controllers. Om [cross-platform](/docs/nl-nl/projects/cross-platform)  invoer, inclusief gamepads, te vereenvoudigen, biedt Roblox het [Input Action System](/docs/nl-nl/input/input-action-system)  om acties  zoals "springen", "rennen" of "schieten" te definiëren en bindingen  voor meerdere hardware-invoeren in te stellen om die acties aan te sturen.

Bij het binden van gamepad-invoeren, zie [gemeenschappelijke besturingsschema's](#gemeenschappelijke-besturingsschemas)  om een consistente gamepad-ervaring voor spelers te creëren. Nadat de invoer is ingesteld, kun je de ervaring van de speler verbeteren door [haptische feedback](#haptische-feedback)  op ondersteunde controllers op te nemen.

Terwijl je ondersteuning voor gamepads opbouwt, vergeet niet regelmatig te testen met een aangesloten gamepad of de [Controller Emulator](#controller-emulatie)  in Studio.

## [Invoertype-detectie](#invoertype-detectie)[](#invoertype-detectie)

In cross-platform ontwikkeling is het belangrijk dat je het [PreferredInput](/docs/nl-nl/reference/engine/classes/UserInputService#PreferredInput)  type bepaalt en hierop reageert dat een speler gebruikt, normaal gesproken om ervoor te zorgen dat [UI elementen](/docs/nl-nl/ui#ui-objecten)  zoals knoppen en menu's op het scherm elegant werken en interactie tussen apparaten ondersteunen.

Bijvoorbeeld, een console gaat ervan uit dat gamepads de standaardinvoer zijn, maar een speler op PC of laptop kan er ook voor kiezen om een bluetooth-gamepad aan te sluiten. In dit geval blijft muis/toetsenbord een geldige invoer voor die speler, maar je kunt aannemen dat ze willen overschakelen naar de aangesloten gamepad als het primaire  invoertype.

Zie [invoertype-detectie](/docs/nl-nl/input#invoertype-detectie)  voor meer informatie.

Voor alternatieve gamepad-detectiemethoden, zie de [UserInputService.GamepadEnabled](/docs/nl-nl/reference/engine/classes/UserInputService#GamepadEnabled)  eigenschap en de [GamepadConnected](/docs/nl-nl/reference/engine/classes/UserInputService#GamepadConnected) /[GamepadDisconnected](/docs/nl-nl/reference/engine/classes/UserInputService#GamepadDisconnected)  evenementen.

## [Gemeenschappelijke besturingsschema's](#gemeenschappelijke-besturingsschemas)[](#gemeenschappelijke-besturingsschemas)

Bij het overwegen van specifieke besturingsbindingen voor het [Input Action System](/docs/nl-nl/input/input-action-system) , is het het beste om consistentie te waarborgen tussen verschillende games. De volgende invoerbindingen helpen spelers om zich onmiddellijk vertrouwd en comfortabel te voelen met gamepadbesturing.

| Invoer | | Veelvoorkomende gebruiksscenario's |
| --- | --- |
| [ButtonA](/docs/nl-nl/reference/engine/enums/KeyCode) | | Accepteert speler prompts of GUI-selecties. Alternatief gebruikt voor primaire acties zoals springen. |
| [ButtonB](/docs/nl-nl/reference/engine/enums/KeyCode) | | Annuleert speler prompts of GUI-selecties. Alternatief gebruikt voor secundaire acties zoals een dodging, rollen of rennen. |
| [Thumbstick1](/docs/nl-nl/reference/engine/enums/KeyCode) | | Over het algemeen geassocieerd met karakterbeweging. |
| [Thumbstick2](/docs/nl-nl/reference/engine/enums/KeyCode) | | Over het algemeen geassocieerd met camerabeweging. |
| [ButtonL2](/docs/nl-nl/reference/engine/enums/KeyCode) , [ButtonR2](/docs/nl-nl/reference/engine/enums/KeyCode) | | Over het algemeen gebruikt voor primaire acties, zoals schieten. |
| [ButtonL1](/docs/nl-nl/reference/engine/enums/KeyCode) , [ButtonR1](/docs/nl-nl/reference/engine/enums/KeyCode) , [ButtonX](/docs/nl-nl/reference/engine/enums/KeyCode) , [ButtonY](/docs/nl-nl/reference/engine/enums/KeyCode) | | Secundaire acties zoals herladen, richten of toegang krijgen tot een inventaris of minimap. |

Xbox PlayStation

![](https://prod.docsiteassets.roblox.com/assets/scripting/input/Gamepad-Inputs-Xbox.png)

## [Haptische feedback](#haptische-feedback)[](#haptische-feedback)

Veel gamepad-controllers hebben motoren ingebouwd om haptische feedback te bieden. Het toevoegen van rumbles en trillingen kan de ervaring van een speler aanzienlijk verbeteren en subtiele feedback bieden naast visuals of audio.

Roblox ondersteunt haptics voor PlayStation-gamepads, Xbox-gamepads en de Quest Touch-controller. Haptische feedback wordt beheerd via [HapticEffect](/docs/nl-nl/reference/engine/classes/HapticEffect)  instanties die kunnen worden ingesteld op een specifieke [Type](/docs/nl-nl/reference/engine/classes/HapticEffect#Type)  zoals [GameplayCollision](/docs/nl-nl/reference/engine/enums/HapticEffectType)  of [UIClick](/docs/nl-nl/reference/engine/enums/HapticEffectType) .

Zodra een [HapticEffect](/docs/nl-nl/reference/engine/classes/HapticEffect)  is ingesteld, kun je deze initiëren via de [Play()](/docs/nl-nl/reference/engine/classes/HapticEffect#Play)  methode, bijvoorbeeld:

```

local Workspace = game:GetService("Workspace")

local effect = Instance.new("HapticEffect")

effect.Type = Enum.HapticEffectType.GameplayExplosion

effect.Parent = Workspace

-- Speel het haptische effect af

effect:Play()

```

## [Controller-emulatie](#controller-emulatie)[](#controller-emulatie)

Gebruik de [Controller Emulator](/docs/nl-nl/studio/controller-emulator)  om gamepad-invoer direct in Studio te testen zonder een fysieke controller aangesloten. Het toont een afbeelding van het geëmuleerde apparaat en verlicht de bedieningselementen zodra invoer arriveert, wat helpt te bevestigen dat je [UserInputService](/docs/nl-nl/reference/engine/classes/UserInputService)  handlers en [Input Action System](/docs/nl-nl/input/input-action-system)  bindingen reageren zoals je verwacht.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
