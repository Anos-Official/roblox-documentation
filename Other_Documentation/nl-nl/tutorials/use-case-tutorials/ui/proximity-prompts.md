<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/ui/proximity-prompts -->

Nabijheidsaanwijzingen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Gebruikersinterfaces

# Nabijheidsaanwijzingen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Je kunt interactieve nabijheidsaanwijzingen maken die verschijnen wanneer gebruikers objecten in de 3D-ruimte naderen, en vervolgens acties activeren op gebruikersinvoer.

Deze tutorial gebruikt het [Dungeon Delve](https://www.roblox.com/games/6749940622/Dungeon-Delve-Learn)  project als showcase. Om mee te doen, open het in Studio voordat je verdergaat.

 ![Bewerken in Studio optie vanaf de hoofdpagina van het spel](https://prod.docsiteassets.roblox.com/assets/tutorials/proximity-prompts/Dungeon-Delve-Edit-Place.png)

## [Maak een aanwijzing](#maak-een-aanwijzing)[](#maak-een-aanwijzing)

Aanwijzingen op het scherm worden gegenereerd door een [ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt)  object dat is gekoppeld aan een [Attachment](/docs/nl-nl/reference/engine/classes/Attachment) , [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  of [Model](/docs/nl-nl/reference/engine/classes/Model) .

1.

Selecteer het PrisonDoor  model in de 3D-weergave of vanuit de Explorer  (Workspace  → PromptObjects  → PrisonDoor ).

![](https://prod.docsiteassets.roblox.com/assets/tutorials/proximity-prompts/Proximity-Prompts-Select-Door-View.jpg)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/proximity-prompts/Proximity-Prompts-Select-PrisonDoor.png)

2.

Vouw de boom uit en selecteer het Door  object.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/proximity-prompts/Proximity-Prompts-Select-Door.png)

3.

Het plaatsen van een aanwijzing op een [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  geeft je meer controle over waar het interactiepunt zich bevindt, in tegenstelling tot het direct plaatsen op het onderdeel/model. Voeg een nieuwe Attachment  toe en hernoem deze naar PromptAttachment .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/proximity-prompts/Proximity-Prompts-Insert-PromptAttachment.png)

4.

Zoek de Position  eigenschap van de nieuwe attachment en stel deze in op -2.25 , -0.5 , -0.5 . Dit zal het voor de sleutelgat van de deur plaatsen.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/proximity-prompts/Proximity-Prompts-PromptAttachment-View.jpg)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/proximity-prompts/Proximity-Prompts-PromptAttachment-Position.png)

5.

Hover over PromptAttachment  en voeg een nieuw ProximityPrompt  object toe.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/proximity-prompts/Proximity-Prompts-Insert-ProximityPrompt.png)

### [Verschijning van de aanwijzing](#verschijning-van-de-aanwijzing)[](#verschijning-van-de-aanwijzing)

Aanwijzingen bestaan uit drie primaire elementen, die elk kunnen worden gecontroleerd door de volgende eigenschappen:

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/proximity-prompts/ProximityPrompt-Diagram.png)

-

ObjectText  — Een optionele naam voor het object waarmee wordt gecommuniceerd.

-

ActionText  — Een optionele actienaam die aan de gebruiker wordt getoond.

-

KeyboardKeyCode  — De toetsenbordtoets die de aanwijzing activeert.

-

GamepadKeyCode  — De gamepadknop die de aanwijzing activeert.

Om de verschijning van de aanwijzing voor de gevangenisdeur aan te passen, maak je de volgende wijzigingen:

1.

Zoek in het Properties  venster de ObjectText  eigenschap en typ Deur .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/proximity-prompts/ProximityPrompt-ObjectText.png)

2.

Voor de ActionText  eigenschap, typ Kies Slot .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/proximity-prompts/ProximityPrompt-ActionText.png)

### [Activeringsafstand](#activeringsafstand)[](#activeringsafstand)

Aanwijzingen verschijnen wanneer de character  van de gebruiker zich binnen het gedefinieerde MaxActivationDistance  bereik van het ouderobject van de aanwijzing bevindt.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/proximity-prompts/Proximity-Prompts-MaxActivationDistance-View.jpg)

De standaardwaarde werkt in de meeste gevallen goed, maar je kunt de gebruikersinteractie dichter bij het slot brengen door MaxActivationDistance  in te stellen op 4 .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/proximity-prompts/ProximityPrompt-MaxActivationDistance.png)

### [Houdduur](#houdduur)[](#houdduur)

De waarde van de HoldDuration  eigenschap bepaalt hoe snel de actie van de aanwijzing wordt geactiveerd, in seconden. Aangezien deze deur moet worden geopend om te ontgrendelen, wijzig de HoldDuration  eigenschap naar 4 .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/proximity-prompts/ProximityPrompt-HoldDuration.png)

## [Implementeer een actie](#implementeer-een-actie)[](#implementeer-een-actie)

De beste manier om aanwijzingsevents te detecteren is via [ProximityPromptService](/docs/nl-nl/reference/engine/classes/ProximityPromptService)  — dit stelt je in staat om events centraal te detecteren zonder een script aan elk aanwijzingobject te koppelen.

Een basisstructuur is als volgt:

```

local ProximityPromptService = game:GetService("ProximityPromptService")

-- Detecteer wanneer de aanwijzing wordt geactiveerd

local function onPromptTriggered(promptObject, player)

end

-- Detecteer wanneer de aanwijzing vasthouden begint

local function onPromptHoldBegan(promptObject, player)

end

-- Detecteer wanneer de aanwijzing vasthouden eindigt

local function onPromptHoldEnded(promptObject, player)

end

-- Verbind aanwijzingsevents met verwerkingsfuncties

ProximityPromptService.PromptTriggered:Connect(onPromptTriggered)

ProximityPromptService.PromptButtonHoldBegan:Connect(onPromptHoldBegan)

ProximityPromptService.PromptButtonHoldEnded:Connect(onPromptHoldEnded)

```

| Evenement | | Beschrijving |
| --- | --- |
| [PromptTriggered](/docs/nl-nl/reference/engine/classes/ProximityPromptService#PromptTriggered) | | Wordt geactiveerd wanneer een gebruiker interactie heeft met een aanwijzing (** na**  de duur voor een aanwijzing met een niet-nul [HoldDuration](/docs/nl-nl/reference/engine/classes/ProximityPrompt#HoldDuration) ). |
| [PromptButtonHoldBegan](/docs/nl-nl/reference/engine/classes/ProximityPromptService#PromptButtonHoldBegan) | | Wordt geactiveerd wanneer een gebruiker begint met interactie met een aanwijzing met een niet-nul [HoldDuration](/docs/nl-nl/reference/engine/classes/ProximityPrompt#HoldDuration) . |
| [PromptButtonHoldEnded](/docs/nl-nl/reference/engine/classes/ProximityPromptService#PromptButtonHoldEnded) | | Wordt geactiveerd wanneer een gebruiker stopt met interactie met een aanwijzing met een niet-nul [HoldDuration](/docs/nl-nl/reference/engine/classes/ProximityPrompt#HoldDuration) |

In het [Dungeon Delve](https://www.roblox.com/games/6749940622/Dungeon-Delve-Learn)  project worden deze evenementen beheerd door het PromptEvents  script binnen ServerScriptService .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/proximity-prompts/Proximity-Prompts-PromptEvents-Script.png)

Binnen het script roepen de bovenstaande evenementen eenvoudig functies aan binnen de ObjectActions  [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript) , die ook in ServerScriptService  is te vinden.

```

local ProximityPromptService = game:GetService("ProximityPromptService")

local ServerScriptService = game:GetService("ServerScriptService")

local ObjectActions = require(ServerScriptService.ObjectActions)

-- Detecteer wanneer de aanwijzing wordt geactiveerd

local function onPromptTriggered(promptObject, player)

	ObjectActions.promptTriggeredActions(promptObject, player)

end

-- Detecteer wanneer de aanwijzing vasthouden begint

local function onPromptHoldBegan(promptObject, player)

	ObjectActions.promptHoldBeganActions(promptObject, player)

end

-- Detecteer wanneer de aanwijzing vasthouden eindigt

local function onPromptHoldEnded(promptObject, player)

	ObjectActions.promptHoldEndedActions(promptObject, player)

end

-- Verbind aanwijzingsevents met verwerkingsfuncties

ProximityPromptService.PromptTriggered:Connect(onPromptTriggered)

ProximityPromptService.PromptButtonHoldBegan:Connect(onPromptHoldBegan)

ProximityPromptService.PromptButtonHoldEnded:Connect(onPromptHoldEnded)

```

Nabijheidsaanwijzingen zijn een handige en aanpasbare oplossing voor interactie met objecten in het spel. Bekijk de [ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt)  en [ProximityPromptService](/docs/nl-nl/reference/engine/classes/ProximityPromptService)  referentiepagina's voor nog meer manieren om het gedrag van aanwijzingen te controleren, en verken andere interactieve objecten in [Dungeon Delve](https://www.roblox.com/games/6749940622/Dungeon-Delve-Learn)  voor creatieve inspiratie.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
