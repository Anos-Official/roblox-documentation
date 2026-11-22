<!-- Source: https://create.roblox.com/docs/nl-nl/ui/proximity-prompts -->

Proximity prompts | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Gebruikersinterface](/docs/nl-nl/ui)
6. /
7. UI-objecten

# Proximity prompts

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

[ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt)  objecten moedigen gebruikersinteractie aan om een actie te activeren wanneer ze in-game objecten zoals deuren, lichtschakelaars en knoppen benaderen. Met dit object kun je:

-

Aangeven met welke objecten een gebruiker in het spel kan interageren.

-

De actie weergeven die een gebruiker kan ondernemen op het object, en vervolgens de actie activeren via gebruikersinvoer zoals het indrukken of vasthouden van een toets.

-

De juiste invoer voor alle invoertypen weergeven, zoals toetsenbord-, gamepad- en touchscreenknoppen.

Bekijk de [Dungeon Delve](https://www.roblox.com/games/6074153281/Dungeon-Delve)  voorbeeldplaats voor de volledig werkende voorbeelden van proximity prompts die in de bovenstaande video worden getoond.

## [Proximity prompts maken](#proximity-prompts-maken)[](#proximity-prompts-maken)

Je moet proximity prompts koppelen aan het onderdeel, model of bijlage waarmee je wilt dat een gebruiker interageert. Om een proximity prompt toe te voegen aan een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) , [Model](/docs/nl-nl/reference/engine/classes/Model)  of [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  object:

1.

In het [Explorer](/docs/nl-nl/studio/explorer)  venster, beweeg de muis over de [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) , [Model](/docs/nl-nl/reference/engine/classes/Model)  of [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  en klik op de ⊕ knop. Een contextmenu wordt weergegeven.

2.

Kies in het menu een ProximityPrompt .

 ![Explorer hiërarchie die een ProximityPrompt toont die aan een Attachment is gekoppeld](https://prod.docsiteassets.roblox.com/assets/ui/proximity-prompt/ProximityPrompt-New.png)

## [Proximity prompts aanpassen](#proximity-prompts-aanpassen)[](#proximity-prompts-aanpassen)

Je kunt een proximity prompt aanpassen op basis van hoe je wilt dat deze [verschijnt](#uiterlijk) , wanneer je wilt dat deze [zichtbaar](#zichtbaarheid)  is, en wat je wilt dat een gebruiker doet om de [actie te activeren](#interactiviteit) .

### [Uiterlijk](#uiterlijk)[](#uiterlijk)

Proximity prompts moeten drie dingen communiceren:

-

Het object  waarmee een gebruiker kan interageren.

-

De actie  die wordt geactiveerd wanneer ze interageren met de proximity prompt.

-

De toets  die een gebruiker moet indrukken of vasthouden.

Je kunt deze specificeren via de volgende eigenschappen:

-

[ObjectText](/docs/nl-nl/reference/engine/classes/ProximityPrompt#ObjectText)  Een optionele naam voor het object waarmee een gebruiker kan interageren.

-

[ActionText](/docs/nl-nl/reference/engine/classes/ProximityPrompt#ActionText)  Een optionele naam voor de actie die een gebruiker zal activeren.

-

[KeyboardKeyCode](/docs/nl-nl/reference/engine/classes/ProximityPrompt#KeyboardKeyCode)  De toetsenbordtoets die een gebruiker moet indrukken of vasthouden om de actie te activeren.

-

[GamepadKeyCode](/docs/nl-nl/reference/engine/classes/ProximityPrompt#GamepadKeyCode)  De gamepadtoets die een gebruiker moet indrukken of vasthouden om de actie te activeren.

 ![Diagram dat de basis elementen van een ProximityPrompt aangeeft](https://prod.docsiteassets.roblox.com/assets/ui/proximity-prompt/Prompt-Diagram.png)

### [Zichtbaarheid](#zichtbaarheid)[](#zichtbaarheid)

Je kunt controleren wanneer de proximity prompt zichtbaar is via de [MaxActivationDistance](/docs/nl-nl/reference/engine/classes/ProximityPrompt#MaxActivationDistance) , [RequiresLineOfSight](/docs/nl-nl/reference/engine/classes/ProximityPrompt#RequiresLineOfSight) , en [Exclusivity](/docs/nl-nl/reference/engine/classes/ProximityPrompt#Exclusivity)  eigenschappen.

#### [MaxActivationDistance](#maxactivationdistance)[](#maxactivationdistance)

De [MaxActivationDistance](/docs/nl-nl/reference/engine/classes/ProximityPrompt#MaxActivationDistance)  eigenschap stelt je in staat om het bereik rondom het [ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt)  object te definiëren dat de zichtbaarheid van de proximity prompt activeert. Zodra het karakter van een gebruiker dat bereik binnenkomt, wordt de proximity prompt zichtbaar.

 ![Diagram dat aangeeft hoe de afstand van een karakter tot een ProximityPrompt object van invloed is op of de prompt op het scherm verschijnt](https://prod.docsiteassets.roblox.com/assets/ui/proximity-prompt/MaxActivationDistance.jpg)

#### [RequiresLineOfSight](#requireslineofsight)[](#requireslineofsight)

De [RequiresLineOfSight](/docs/nl-nl/reference/engine/classes/ProximityPrompt#RequiresLineOfSight)  eigenschap activeert de zichtbaarheid van de proximity prompt wanneer er een duidelijke weg is van de camera  naar het [ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt)  object. Standaard is deze eigenschap ingesteld op waar.

#### [Exclusiviteit](#exclusiviteit)[](#exclusiviteit)

Als het karakter van een gebruiker binnen het bereik van meerdere proximity prompts is, hangt de zichtbaarheid van elke proximity prompt af van welke proximity prompt de camera aanwijst, evenals de waarde van de [Exclusivity](/docs/nl-nl/reference/engine/classes/ProximityPrompt)  eigenschap van elke proximity prompt.

OnePerButton OneGlobally AlwaysShow

![ProximityPrompt objecten ingesteld op exclusiviteit van OnePerButton](https://prod.docsiteassets.roblox.com/assets/ui/proximity-prompt/Exclusivity-OnePerButton.jpg) Slechts één proximity prompt is zichtbaar per invoertoetscode. Als meerdere proximity prompts binnen bereik verschillende toetscodes gebruiken, zijn ze allemaal zichtbaar. Als meerdere proximity prompts binnen bereik dezelfde toetscode gebruiken, is er echter slechts één proximity prompt zichtbaar op elk gegeven moment, afhankelijk van de kijkrichting van de camera.

### [Interactiviteit](#interactiviteit)[](#interactiviteit)

Je kunt aanpassen hoe een gebruiker interactie heeft met een proximity prompt via de [HoldDuration](/docs/nl-nl/reference/engine/classes/ProximityPrompt#HoldDuration)  en [ClickablePrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt#ClickablePrompt)  eigenschappen.

#### [HoldDuration](#holdduration)[](#holdduration)

De [HoldDuration](/docs/nl-nl/reference/engine/classes/ProximityPrompt#HoldDuration)  eigenschap bepaalt hoe veel seconden een gebruiker moet drukken op een toets voordat de actie van de proximity prompt wordt geactiveerd. Als deze eigenschap een waarde van 0  heeft, wordt de actie van de proximity prompt onmiddellijk geactiveerd.

#### [ClickablePrompt](#clickableprompt)[](#clickableprompt)

De [ClickablePrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt#ClickablePrompt)  eigenschap specificeert of een gebruiker op een proximity prompt kan klikken om de actie te activeren. Wanneer ingesteld op waar , kan een gebruiker interageren met de proximity prompt door direct op de proximity prompt te klikken of  door de opgegeven toets in te drukken. Wanneer ingesteld op onwaar , kan een gebruiker alleen interageren met de proximity prompt door de opgegeven toets in te drukken.

Let op dat als een gebruiker een telefoon of tablet gebruikt, ze altijd kunnen interageren met de proximity prompt door direct op de proximity prompt te klikken, ongeacht de waarde van de [ClickablePrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt#ClickablePrompt)  eigenschap.

## [Script proximity prompts](#script-proximity-prompts)[](#script-proximity-prompts)

Je kunt verbinding maken met proximity prompt evenementen, hetzij op het [ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt)  object zelf of globaal via [ProximityPromptService](/docs/nl-nl/reference/engine/classes/ProximityPromptService) . De [ProximityPromptService](/docs/nl-nl/reference/engine/classes/ProximityPromptService)  stelt je in staat om al het gedrag van proximity prompts vanuit één locatie te beheren, waardoor de noodzaak voor dubbele code in je spel wordt voorkomen.

| Evenement | | Beschrijving |
| --- | --- |
| [PromptTriggered](/docs/nl-nl/reference/engine/classes/ProximityPromptService#PromptTriggered) | | Wordt geactiveerd wanneer een speler interactie heeft met een proximity prompt (na de duur voor een prompt met een niet-nul [HoldDuration](/docs/nl-nl/reference/engine/classes/ProximityPrompt#HoldDuration) ). |
| [PromptTriggerEnded](/docs/nl-nl/reference/engine/classes/ProximityPromptService#PromptTriggerEnded) | | Wordt geactiveerd wanneer de speler stopt met interactie met een proximity prompt. |
| [PromptButtonHoldBegan](/docs/nl-nl/reference/engine/classes/ProximityPromptService#PromptButtonHoldBegan) | | Wordt geactiveerd wanneer een speler begint met interactie met een proximity prompt met een niet-nul [HoldDuration](/docs/nl-nl/reference/engine/classes/ProximityPrompt#HoldDuration)  waarde. |
| [PromptButtonHoldEnded](/docs/nl-nl/reference/engine/classes/ProximityPromptService#PromptButtonHoldEnded) | | Wordt geactiveerd wanneer een speler stopt met interactie met een proximity prompt met een niet-nul [HoldDuration](/docs/nl-nl/reference/engine/classes/ProximityPrompt#HoldDuration)  waarde. |
| [PromptShown](/docs/nl-nl/reference/engine/classes/ProximityPromptService#PromptShown) | | Wordt geactiveerd in [LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript)  wanneer een proximity prompt zichtbaar wordt gemaakt. |
| [PromptHidden](/docs/nl-nl/reference/engine/classes/ProximityPromptService#PromptHidden) | | Wordt geactiveerd in [LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript)  wanneer een prompt verborgen is. |

Het volgende codevoorbeeld bevat een basisstructuur voor het gebruik van [ProximityPromptService](/docs/nl-nl/reference/engine/classes/ProximityPromptService) :

```

local ProximityPromptService = game:GetService("ProximityPromptService")

-- Detecteer wanneer prompt wordt geactiveerd

local function onPromptTriggered(promptObject, player)

end

-- Detecteer wanneer prompt vasthouden begint

local function onPromptHoldBegan(promptObject, player)

end

-- Detecteer wanneer prompt vasthouden eindigt

local function onPromptHoldEnded(promptObject, player)

end

-- Verbind prompt evenementen met verwerkingsfuncties

ProximityPromptService.PromptTriggered:Connect(onPromptTriggered)

ProximityPromptService.PromptButtonHoldBegan:Connect(onPromptHoldBegan)

ProximityPromptService.PromptButtonHoldEnded:Connect(onPromptHoldEnded)

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
