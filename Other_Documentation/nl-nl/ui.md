<!-- Source: https://create.roblox.com/docs/nl-nl/ui -->

Gebruikersinterface | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Gebruikersinterface](/docs/nl-nl/ui)

# Gebruikersinterface

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Je kunt snel hoogwaardige grafische gebruikersinterfaces maken met minimale scriptingvereisten met behulp van ingebouwde [UI-objecten](#ui-objecten) . Afhankelijk van waar je het maakt, wordt de UI ofwel [op het scherm](#op-screen-ui)  of [binnen de 3D-wereld van een spel](#in-game-ui)  weergegeven.

## [Op-screen UI](#op-screen-ui)[](#op-screen-ui)

[Op-screen containers](/docs/nl-nl/ui/on-screen-containers)  bevatten UI-objecten die je op het scherm van een speler wilt weergeven, waaronder [frames](/docs/nl-nl/ui/frames) , [labels](/docs/nl-nl/ui/labels) , [knoppen](/docs/nl-nl/ui/buttons)  en meer. Alle op-screen UI-objecten en code worden opgeslagen en gewijzigd op de client.

![Voorbeeld ScreenGui met verschillende GuiObject-kinderen, waaronder een Frame, TextLabel, TextBox en ImageButton.](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/ScreenGui-Example.jpg)

## [In-game UI](#in-game-ui)[](#in-game-ui)

[In-game containers](/docs/nl-nl/ui/in-experience-containers)  zoals [SurfaceGuis](/docs/nl-nl/reference/engine/classes/SurfaceGui)  en [BillboardGuis](/docs/nl-nl/reference/engine/classes/BillboardGui)  bevatten UI-objecten die je binnen de 3D-wereld van je spel wilt weergeven.

## [UI-objecten](#ui-objecten)[](#ui-objecten)

De meeste UI-elementen zijn [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject) , 2D grafische gebruikersinterface-objecten die je aan containers kunt koppelen. De vier meest voorkomende zijn [frames](/docs/nl-nl/ui/frames) , [labels](/docs/nl-nl/ui/labels) , [knoppen](/docs/nl-nl/ui/buttons)  en [tekstinvoer](/docs/nl-nl/ui/text-input)  objecten.

 ![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/ScreenGui-Example.jpg)

| Object | | Beschrijving |
| --- | --- |
| [Frame](/docs/nl-nl/ui/frames) | | [Frames](/docs/nl-nl/reference/engine/classes/Frame)  fungeren als containers voor andere UI-objecten. Wanneer je frames manipuleert, manipuleer je ook de objecten die ze bevatten. |
| [Label](/docs/nl-nl/ui/labels) | | [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel)  en [ImageLabel](/docs/nl-nl/reference/engine/classes/ImageLabel)  objecten stellen je in staat om aanpasbare tekst en afbeeldingen weer te geven. |
| [Button](/docs/nl-nl/ui/buttons) | | [TextButton](/docs/nl-nl/reference/engine/classes/TextButton)  en [ImageButton](/docs/nl-nl/reference/engine/classes/ImageButton)  objecten stellen gebruikers in staat om een actie uit te lokken. |
| [Text Input](/docs/nl-nl/ui/text-input) | | [TextBox](/docs/nl-nl/reference/engine/classes/TextBox)  objecten stellen gebruikers in staat om tekst in te voeren. |

Met de eigenschappen [Position](/docs/nl-nl/reference/engine/classes/GuiObject#Position) , [Size](/docs/nl-nl/reference/engine/classes/GuiObject#Size) , [AnchorPoint](/docs/nl-nl/reference/engine/classes/GuiObject#AnchorPoint)  en [ZIndex](/docs/nl-nl/reference/engine/classes/GuiObject#ZIndex)  heb je volledige controle over hoe je [positioneert](/docs/nl-nl/ui/position-and-size#positie) , [grootte](/docs/nl-nl/ui/position-and-size#grootte)  en [laag](/docs/nl-nl/ui/position-and-size#zindex)  [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject) . Je kunt ook [tweening](/docs/nl-nl/ui/animation)  gebruiken om een [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  soepel van de ene staat naar de andere over te brengen en dynamische visuele feedback te geven.

## [Lay-out en ontwerp](#lay-out-en-ontwerp)[](#lay-out-en-ontwerp)

Naast basis eigenschappen voor het aanpassen van positie en grootte, biedt Roblox ook lay-outstructuren zoals [lijst/flex](/docs/nl-nl/ui/list-flex-layouts)  en [grid](/docs/nl-nl/ui/grid-table-layouts) , evenals [grootte-modifiers](/docs/nl-nl/ui/size-modifiers)  en [verschijnings-modifiers](/docs/nl-nl/ui/appearance-modifiers) .

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIListLayout-Example.png)[UIListLayout](/docs/nl-nl/reference/engine/classes/UIListLayout)  voor horizontale of verticale itemsequenties

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-Color-Solid.png)[UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke)  op [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-Color-Gradient.png)[UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke)  met [UIGradient](/docs/nl-nl/reference/engine/classes/UIGradient)

## [Universele styling](#universele-styling)[](#universele-styling)

[Universele styling](/docs/nl-nl/ui/styling)  is een Roblox-oplossing voor stylesheets, vergelijkbaar met CSS, waarmee je overrides voor UI-instantie-eigenschappen kunt declareren en wereldwijd kunt toepassen. Deze engine-niveau ondersteuning is de basis voor de [Style Editor](/docs/nl-nl/ui/styling/editor)  en de end-to-end token-pijplijn.

## [Interactieve frameworks](#interactieve-frameworks)[](#interactieve-frameworks)

Naast de kern [gebruikersinterface-objecten](#ui-objecten)  bieden de volgende frameworks ingebouwde en aanpasbare interactiviteit voor je spellen.

### [Proximity prompts](#proximity-prompts)[](#proximity-prompts)

[Proximity prompts](/docs/nl-nl/ui/proximity-prompts)  zijn unieke ingebouwde UI-objecten die gebruikersinteractie aanmoedigen om een actie te triggeren wanneer ze in de buurt komen van in-game objecten zoals deuren, lichtschakelaars en knoppen.

### [UI-dragdetectoren](#ui-dragdetectoren)[](#ui-dragdetectoren)

[UI-dragdetectoren](/docs/nl-nl/ui/ui-drag-detectors)  vergemakkelijken en moedigen interactie aan met 2D-gebruikersinterface-elementen zoals schuifregelaars, spinners en meer.

### [3D-dragdetectoren](#3d-dragdetectoren)[](#3d-dragdetectoren)

[3D-dragdetectoren](/docs/nl-nl/ui/3D-drag-detectors)  moedigen fysieke interactie aan met 3D-objecten in een spel, zoals het openen van deuren en lades, het schuiven van een onderdeel, het oppakken en gooien van een bowlingbal, het terugtrekken en afvuren van een katapult, en nog veel meer.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
