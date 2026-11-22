<!-- Source: https://create.roblox.com/docs/nl-nl/ui/position-and-size -->

Positie en grootte van UI-objecten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Gebruikersinterface](/docs/nl-nl/ui)

# Positie en grootte van UI-objecten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Tenzij UI-objecten onder controle staan van een [lay-outstructuur](#lay-outstructuren)  of een [grootte-modifier/beperking](/docs/nl-nl/ui/size-modifiers) , heb je volledige controle over hun [positie](#positie)  en [grootte](#grootte) . Je kunt ook de Z-index [laagvolgorde](#zindex)  instellen waarin objecten elkaar overlappen.

## [Kern eigenschappen](#kern-eigenschappen)[](#kern-eigenschappen)

Alle [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  delen een kernset van eigenschappen om ze te [positioneren](#positie) , [schalen](#grootte) , [anker](#anchorpoint)  en [laag](#zindex)  binnen een on-screen of in-game container.

### [Positie](#positie)[](#positie)

De [Position](/docs/nl-nl/reference/engine/classes/GuiObject#Position)  eigenschap is een [UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)  coördinaten set die het object positioneert langs de X  en Y  assen. Een [UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)  wordt weergegeven door zowel [Scale](/docs/nl-nl/reference/engine/datatypes/UDim#Scale)  als [Offset](/docs/nl-nl/reference/engine/datatypes/UDim#Offset)  waarden voor elke as:

-

[Scale](/docs/nl-nl/reference/engine/datatypes/UDim#Scale)  waarden vertegenwoordigen een percentage  van de grootte van de container langs de overeenkomstige as, optellend bij eventuele [Offset](/docs/nl-nl/reference/engine/datatypes/UDim#Offset)  waarden.

-

[Offset](/docs/nl-nl/reference/engine/datatypes/UDim#Offset)  waarden vertegenwoordigen hoeveel pixels  het object op de overeenkomstige as moet verschuiven, optellend bij eventuele [Scale](/docs/nl-nl/reference/engine/datatypes/UDim#Scale)  waarden.

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/UDim2-Components.png)

Om de positie van een geselecteerd [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  te bewerken, klik je op het Positie  veld in het [Eigenschappen](/docs/nl-nl/studio/properties)  venster en voer je een nieuwe [UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)  coördinaten set in.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/GuiObject-Position.png)  ![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Scale-Offset-Positioning.png)

Haken en spaties zijn optioneel  bij het invoeren van een [UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)  in Studio — je kunt eenvoudig de vier waarden gescheiden door komma's invoeren, bijvoorbeeld 0.25,40,0.1,20 , en Studio zal de bedoelde waarde set afleiden.

Studio leidt ook de bedoelde waarde set af wanneer een enkel getal wordt ingevoerd. Bijvoorbeeld, simpelweg 0.5  invoeren zal worden omgezet naar {0.5, 0},{0.5, 0}  aangezien 0.5  waarschijnlijk een Schaal  waarde van 50% is. Omgekeerd, het invoeren van 20  zal worden omgezet naar {0, 20},{0, 20}  aangezien 20  waarschijnlijk een Offset  waarde van 20 pixels is en geen schaal van 2000%.

### [Grootte](#grootte)[](#grootte)

De [Size](/docs/nl-nl/reference/engine/classes/GuiObject#Size)  eigenschap is een [UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)  coördinaten set die het object schaalt langs de X  en Y  assen. Een [UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)  wordt weergegeven door zowel [Scale](/docs/nl-nl/reference/engine/datatypes/UDim#Scale)  als [Offset](/docs/nl-nl/reference/engine/datatypes/UDim#Offset)  waarden voor elke as:

-

Schaal  — Waarden die een percentage  van de grootte van de container langs de overeenkomstige as vertegenwoordigen, optellend bij eventuele Offset  waarden.

-

Offset  — Waarden die de pixel  grootte van het object langs de overeenkomstige as vertegenwoordigen, optellend bij eventuele Schaal  waarden.

Om de grootte van een geselecteerd [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  te bewerken, klik je op het Grootte  veld in het [Eigenschappen](/docs/nl-nl/studio/properties)  venster en voer je een nieuwe [UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)  coördinaten set in.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/GuiObject-Size.png)  ![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Scale-Sizing.png)

Haken en spaties zijn optioneel  bij het invoeren van een [UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)  in Studio — je kunt eenvoudig de vier waarden gescheiden door komma's invoeren, bijvoorbeeld 0.75,0,0.25,0 , en Studio zal de bedoelde waarde set afleiden.

Studio leidt ook de bedoelde waarde set af wanneer een enkel getal wordt ingevoerd. Bijvoorbeeld, simpelweg 0.5  invoeren zal worden omgezet naar {0.5, 0},{0.5, 0}  aangezien 0.5  waarschijnlijk een Schaal  waarde van 50% is. Omgekeerd, het invoeren van 20  zal worden omgezet naar {0, 20},{0, 20}  aangezien 20  waarschijnlijk een Offset  waarde van 20 pixels is en geen schaal van 2000%.

### [AnchorPoint](#anchorpoint)[](#anchorpoint)

De [AnchorPoint](/docs/nl-nl/reference/engine/classes/GuiObject#AnchorPoint)  eigenschap definieert het oorspronkingspunt  waarvandaan het object van positie verandert [positie](#positie)  en [grootte](#grootte) . De standaard [AnchorPoint](/docs/nl-nl/reference/engine/classes/GuiObject#AnchorPoint)  waarden zijn (0, 0)  wat het anker in de linkerbovenhoek van het object plaatst.

[AnchorPoint](/docs/nl-nl/reference/engine/classes/GuiObject#AnchorPoint)  waarden zijn een fracties  van 0  tot 1 , relatief aan de [grootte](#grootte)  van het object, wat betekent dat een object met [AnchorPoint](/docs/nl-nl/reference/engine/classes/GuiObject#AnchorPoint)  waarden van (0.5, 0.5)  het ankerpunt halverwege (50%) door het object plaatst, zowel horizontaal als verticaal, en eventuele wijzigingen in zijn [positie](#positie)  of [grootte](#grootte)  zowel verplaatst als schaalt vanaf dit punt.

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Anchor-Points.png)

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Anchor-Point-Scaling.png)

Om het ankerpunt van een geselecteerd [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  te bekijken en te bewerken:

1.

In het [Eigenschappen](/docs/nl-nl/studio/properties)  venster, klik je in het AnchorPoint  veld.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/GuiObject-AnchorPoint.png)

2.

Voer een nieuwe [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)  coördinaat in en druk op Enter .

Studio leidt het bedoelde waarde paar af wanneer een enkel getal wordt ingevoerd. Bijvoorbeeld, simpelweg 0.5  invoeren zal worden omgezet naar 0.5, 0.5  voor een centraal ankerpunt.

### [ZIndex](#zindex)[](#zindex)

De [ZIndex](/docs/nl-nl/reference/engine/classes/GuiObject#ZIndex)  eigenschap definieert de laagvolgorde waarin [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  renderen en elkaar overlappen. Als je nieuwe renderlagen wilt maken, moet je de [ZIndex](/docs/nl-nl/reference/engine/classes/GuiObject#ZIndex)  eigenschap instellen op verschillende positieve of negatieve gehele waarden voor elk object.

Voor UI-containers zoals [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui) , renderen de standaard [ZIndexBehavior](/docs/nl-nl/reference/engine/classes/ScreenGui#ZIndexBehavior)  altijd kinderen boven hun ouders, en de [ZIndex](/docs/nl-nl/reference/engine/classes/GuiObject#ZIndex)  van elk kind wordt gebruikt om de volgorde te bepalen waarin het boven andere renderen.

Om de [ZIndex](/docs/nl-nl/reference/engine/classes/GuiObject#ZIndex)  van een object te bewerken, zoek je ZIndex  in het [Eigenschappen](/docs/nl-nl/studio/properties)  venster en voer je een nieuwe gehele waarde in.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/GuiObject-ZIndex.png)

## [Lay-outstructuren](#lay-outstructuren)[](#lay-outstructuren)

Lay-outstructuren stellen je in staat om [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  snel te organiseren en weer te geven, bijvoorbeeld in een horizontale of verticale [lijst](/docs/nl-nl/ui/list-flex-layouts) , een [rooster](/docs/nl-nl/ui/grid-table-layouts#rasterindeling)  van gelijkmatig grote tegels, een [pagina-sequentie](/docs/nl-nl/ui/page-layouts) , en meer. Lay-outs overschrijven of beïnvloeden doorgaans de [positie](#positie) /[grootte](#grootte)  van objecten onder hun controle.

| Lay-out | | Beschrijving |
| --- | --- |
| [Lijst](/docs/nl-nl/ui/grid-table-layouts#rasterindeling) | | [UIListLayout](/docs/nl-nl/reference/engine/classes/UIListLayout)  positioneert broeder [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  in horizontale rijen of verticale kolommen binnen hun oudercontainer. |
| [Rooster](/docs/nl-nl/ui/grid-table-layouts#rasterindeling) | | [UIGridLayout](/docs/nl-nl/reference/engine/classes/UIGridLayout)  positioneert broeder [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  in een rooster van uniforme cellen van dezelfde grootte binnen hun oudercontainer. |
| [Tabel](/docs/nl-nl/ui/grid-table-layouts#tabelindeling) | | [UITableLayout](/docs/nl-nl/reference/engine/classes/UITableLayout)  positioneert broeder [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  en hun kinderen in tabelvorm. |
| [Pagina](/docs/nl-nl/ui/page-layouts) | | [UIPageLayout](/docs/nl-nl/reference/engine/classes/UIPageLayout)  organiseert zijn broeder [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  in unieke pagina's waar je door middel van scripting naar kunt overgaan. |

## [Cross-platform factoren](#cross-platform-factoren)[](#cross-platform-factoren)

Roblox is inherent [cross-platform](/docs/nl-nl/projects/cross-platform) , aangezien spelers games kunnen ontdekken en zich kunnen aansluiten op hun telefoon of tablet, en later kunnen doorgaan waar ze waren gebleven op hun pc of console. Je moet je Roblox-games ontwerpen zodat ze toegankelijk en plezierig zijn op alle  platforms die je kiest te ondersteunen, in plaats van te optimaliseren voor één platform en andere te verwaarlozen.

### [Gereserveerde zones](#gereserveerde-zones)[](#gereserveerde-zones)

Op mobiele apparaten nemen de standaardbedieningen een deel van de linkerbenedenhoek en rechterbenedenhoek van het scherm in beslag. Wanneer je een UI voor een game ontwerpt, moet je vermijden belangrijke informatie of virtuele knoppen in deze zones te plaatsen.

 ![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Touch-Reserved-Zones.png)

### [Duimzones](#duimzones)[](#duimzones)

De meeste mobiele spelers gebruiken twee duimen — één op de virtuele duimstick en één op de springknop. Afhankelijk van de fysieke grootte van het apparaat en de handen van de speler, wordt het ongemakkelijk of onmogelijk om te ver weg te reiken vanaf de onderste hoeken, dus je moet vermijden vaak gebruikte knoppen buiten gemakkelijk bereikbare zones te plaatsen.

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Thumb-Zones-Phone-Reachable.png)

Knop comfortabel binnen bereik van de rechterduim van de speler

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Thumb-Zones-Phone-Non-Reachable.png)

Knop moeilijk te bereiken tenzij de speler zijn hand of duim uitstrekt

Vergeet niet dat comfortabele duimzones verschillen tussen telefoons en tablets omdat tablets een groter scherm hebben. Een knop die 40% onder de bovenrand van het scherm is geplaatst, is bereikbaar op een telefoon maar bijna onbereikbaar op een tablet.

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Thumb-Zones-Tablet-Reachable.png)

Knop 40% van de bovenrand van de telefoon, binnen bereik van de duim van de speler

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Thumb-Zones-Tablet-Non-Reachable.png)

Knop 40% van de bovenrand van de tablet, moeilijk te bereiken zonder te rekken

Een betrouwbare aanpak op zowel telefoons als tablets is relatieve  positionering van aangepaste knoppen nabij vaak gebruikte bedieningselementen zoals de standaard springknop, en ze binnen gemakkelijk bereik te plaatsen.

 ![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Custom-Buttons-Near-Jump.png)

De volgende code, geplaatst in een client-side script binnen [StarterPlayerScripts](/docs/nl-nl/reference/engine/classes/StarterPlayerScripts) , haalt de positie van de springknop op en maakt een tijdelijke [knop](/docs/nl-nl/ui/buttons)  20 pixels naar links ervan.

Client Script - Aangepaste Knop Dichtbij Springknop

```

local Players = game:GetService("Players")

local UserInputService = game:GetService("UserInputService")

local player = Players.LocalPlayer

local playerGui = player:WaitForChild("PlayerGui")

if UserInputService.TouchEnabled then

	-- Wacht tot de springknop volledig is geladen

	while not (playerGui:FindFirstChild("JumpButton", true) and playerGui:FindFirstChild("JumpButton", true).IsLoaded) do

		task.wait()

	end

	local jumpButton = playerGui:FindFirstChild("JumpButton", true)

	-- Plaats nieuwe aangepaste knop links van de springknop

	local customButton = Instance.new("ImageButton")

	customButton.AnchorPoint = Vector2.new(1, 1)

	customButton.Size = UDim2.fromOffset(jumpButton.Size.X.Offset * 0.8, jumpButton.Size.Y.Offset * 0.8)

	customButton.Position = jumpButton.Position + UDim2.fromOffset(-20, jumpButton.Size.Y.Offset)

	customButton.Parent = jumpButton.Parent

else

	warn("Apparaat is niet touch-enabled of Studio emuleert geen touch-enabled apparaat!")

end

```

### [Context-gebaseerde UI](#context-gebaseerde-ui)[](#context-gebaseerde-ui)

De schermruimte is beperkt op mobiele apparaten, dus je moet alleen de meest vitale informatie tonen tijdens actieve gameplay. Bijvoorbeeld, als je game een speciale invoeractie heeft om deuren en schatkisten te openen, heeft het geen zin om constant een "open" knop op het scherm te tonen. Gebruik in plaats daarvan een [proximity prompt](/docs/nl-nl/ui/proximity-prompts)  of een vergelijkbare methode om invoer alleen te accepteren wanneer het personage zich dicht bij een deur of kist bevindt.

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Contextual-Button.png) Aangepaste knop die je alleen toont wanneer het personage dicht bij een deur of kist is

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
