<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/ui/create-hud-meters -->

Maak HUD-meters | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Gebruikersinterfaces

# Maak HUD-meters

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een HUD  of Heads-Up Display  is een set UI-elementen die altijd zichtbaar of toegankelijk zijn tijdens het spelen, zoals scoreweergaven, gezondheidsmeters en menu-knoppen. Het opnemen van een HUD is essentieel voor de meeste games omdat het informatie weergeeft die spelers helpt om succesvol te zijn in hun speeldoelen.

Een veelvoorkomend HUD-element is een gezondheidsmeter met een pictogram aan de linkerkant, die kan worden aangepast tot een timerbalk, voortgangsbalk of iets dergelijks.

 ![In-game view showing custom health meter in upper-right region.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Intro.png)

Met [Hazardous Space Station](https://www.roblox.com/games/99416825187098/Hazardous-Space-Station)  als startpunt en [UI Fundamentals - HUD Meter](https://www.roblox.com/games/104506915856758/UI-Fundamentals-HUD-Meter)  als een voltooide referentie, laat deze tutorial zien:

-

Opzetten en gebruiken van de Device Emulator  om je ontwerp op meerdere geëmuleerde schermen te testen.

-

Gebruik van [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui)  als zowel een ontwerp- als opslagcontainer.

-

Hoe je UI-elementen kunt positioneren/formatteren rond ingebouwde Roblox-controles en apparaatsnotches/eilanden, zoals de cameraknip op moderne telefoons.

-

Hoe je de standaard Roblox-gezondheidsmeter kunt vervangen door je eigen meter en deze kunt koppelen aan het gezondheidsniveau van het personage.

-

Hoe je het middenstuk van de gezondheidsmeter kunt animeren en de kleur kunt instellen tussen vijf kleurverloop-kernpunten (rood, oranje, geel, limoen, groen).

## [Schakel de Device Emulator in](#schakel-de-device-emulator-in)[](#schakel-de-device-emulator-in)

Roblox is van nature [cross-platform](/docs/nl-nl/projects/cross-platform) , omdat spelers games kunnen ontdekken en joinen op hun telefoon of tablet, en later kunnen doorgaan waar ze waren gebleven op hun pc of console. Mobiele apparaten (telefoons en tablets) hebben de minste schermruimte, dus het is belangrijk dat je UI-elementen passen op kleinere schermen en dat ze duidelijk zichtbaar zijn voor spelers.

De beste manier om UI-ontwerpen op verschillende platforms te testen is met de [Device Emulator](/docs/nl-nl/studio/testing-modes#device-emulation)  van Studio. Deze tool biedt een vooraf ingestelde selectie van apparaten en stelt je in staat om je eigen aangepaste presets toe te voegen.

1.

Open de [Hazardous Space Station](https://www.roblox.com/games/99416825187098/Hazardous-Space-Station)  template in Studio.

2.

Schakel in het Test -menu van Studio de Device Emulator  in.

3.

Selecteer in de balk direct boven het hoofdvenster een telefoonemulatie zoals iPhone X  of Samsung Galaxy A51 . Stel vervolgens de weergavegrootte in op Fit to Window  om de maximale ruimte in Studio te benutten.

 ![Device Emulator settings options indicated at top of viewport window.](https://prod.docsiteassets.roblox.com/assets/studio/general/Device-Emulator-Phone.png)

## [Maak een schermcontainer](#maak-een-schermcontainer)[](#maak-een-schermcontainer)

Een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  container houdt UI-objecten ([GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject) ) vast om weer te geven op het scherm van een speler (in deze tutorial, de gehele gezondheidsmeter). Om een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  en zijn kindobjecten weer te geven aan elke speler die de game join, plaats je het binnen de [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui)  container. Wanneer een speler zich aansluit en hun personage voor het eerst spawnt, worden de [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  en zijn inhoud gekloond naar de [PlayerGui](/docs/nl-nl/reference/engine/classes/PlayerGui)  container voor die speler, die zich binnen de [Players](/docs/nl-nl/reference/engine/classes/Players)  container bevindt.

 ![Diagram of how a ScreenGui clones from StarterGui to a player's PlayerGui](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/StarterGui-To-PlayerGui.png)

Om een lege [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  in te voegen:

1.

Zoek in het Explorer -venster de [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui)  container.

 ![Explorer window showing the StarterGui container.](https://prod.docsiteassets.roblox.com/assets/studio/explorer/StarterGui.png)

2.

Hover over de container, klik op de ⊕ knop en voeg een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  in.

 ![ScreenGui inserted into the StarterGui container.](https://prod.docsiteassets.roblox.com/assets/studio/explorer/StarterGui-ScreenGui.png)

3.

Hernoem de nieuwe container naar HUDContainer  om het doel ervan weer te geven.

 ![ScreenGui renamed to HUDContainer.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer.png)

### [Maak gebruik van veilige gebieden](#maak-gebruik-van-veilige-gebieden)[](#maak-gebruik-van-veilige-gebieden)

Moderne telefoons maken gebruik van het volledige scherm, maar bevatten doorgaans inkepingen, uitsparingen en andere elementen die schermruimte innemen. Elke Roblox-game bevat ook de bovenste balkcontroles  voor snelle toegang tot het hoofdmenu, [chat](/docs/nl-nl/chat/in-experience-text-chat) , [leaderboard](/docs/nl-nl/players/leaderboards) , en meer.

 ![Mobile device showing Roblox top bar buttons and device cutout.](https://prod.docsiteassets.roblox.com/assets/engine-api/enums/ScreenInsets/Top-Bar-Cutout.png)

Om ervoor te zorgen dat spelers alle UI kunnen zien en toegang hebben zonder obstructie, biedt Roblox de [ScreenInsets](/docs/nl-nl/reference/engine/classes/ScreenGui#ScreenInsets)  eigenschap die de veilige gebied  insets voor de inhoud van een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  beheert. Elk UI-object dat je binnen een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  positioneert, is relatief ten opzichte van de insetgrenzen.

 ![Mobile device showing the core UI safe area.](https://prod.docsiteassets.roblox.com/assets/engine-api/enums/ScreenInsets/CoreUISafeInsets.png)

Terwijl de standaardwaarde van [CoreUISafeInsets](/docs/nl-nl/reference/engine/enums/ScreenInsets)  ervoor zorgt dat alle UI-objecten vrij blijven van Roblox UI en apparaatscutouts, kan [DeviceSafeInsets](/docs/nl-nl/reference/engine/enums/ScreenInsets)  een betere optie zijn om beperkte schermruimte te benutten, zoals hieronder geïllustreerd.

CoreUISafeInsets DeviceSafeInsets

[CoreUISafeInsets](/docs/nl-nl/reference/engine/enums/ScreenInsets)  houdt de meter vrij van alle obstructies, maar het voegt een grote ruimte toe tussen de meter en de fysieke bovenrand van het scherm.

![ScreenInsets set to CoreUISafeInsets.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-CoreUISafeInsets.png)

1.

Selecteer in het Explorer -venster HUDContainer .

 ![Explorer window showing the HUDContainer selected.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer.png)

2.

Stel in het [Properties](/docs/nl-nl/studio/properties)  venster de [ScreenInsets](/docs/nl-nl/reference/engine/classes/ScreenGui#ScreenInsets)  eigenschap in op [DeviceSafeInsets](/docs/nl-nl/reference/engine/enums/ScreenInsets) .

 ![ScreenInsets set to DeviceSafeInsets in the Properties window.](https://prod.docsiteassets.roblox.com/assets/studio/properties/ScreenGui-ScreenInsets-DeviceSafeInsets.png)

### [Stel randopvulling in](#stel-randopvulling-in)[](#stel-randopvulling-in)

Met [ScreenInsets](/docs/nl-nl/reference/engine/classes/ScreenGui#ScreenInsets)  ingesteld op [DeviceSafeInsets](/docs/nl-nl/reference/engine/enums/ScreenInsets) , kan de inhoud nu direct tot de fysieke bovenrand van het scherm reiken. Een kleine hoeveelheid opvulling  kan echter helpen om de gezondheidsmeter (en andere objecten binnen de container) iets van de schermranden weg te duwen voor een schoner uiterlijk en om te voorkomen dat ze worden afgesneden.

 ![Screen container with padding around all edges.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/ScreenGui-With-Padding.png)

Een manier om opvulling toe te passen op een UI-container is door het invoegen van een [UIPadding](/docs/nl-nl/reference/engine/classes/UIPadding)  modifier:

1.

Voeg een [UIPadding](/docs/nl-nl/reference/engine/classes/UIPadding)  modifier toe aan HUDContainer .

 ![HUDContainer with UIPadding modifier inserted.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer-UIPadding.png)

2.

Selecteer het nieuwe [UIPadding](/docs/nl-nl/reference/engine/classes/UIPadding)  object en voer een waarde in van 0, 16  voor alle randen van de container ([PaddingBottom](/docs/nl-nl/reference/engine/classes/UIPadding#PaddingBottom) , [PaddingLeft](/docs/nl-nl/reference/engine/classes/UIPadding#PaddingLeft) , [PaddingRight](/docs/nl-nl/reference/engine/classes/UIPadding#PaddingRight) , [PaddingTop](/docs/nl-nl/reference/engine/classes/UIPadding#PaddingTop) ). Dit past 16 pixels opvulling rondom de container toe, ongeacht de resolutie van het scherm.

 ![Properties window showing the UIPadding modifier with 0, 16 set for all edges.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer-UIPadding-Values.png)

## [Construct de gezondheidsmeter](#construct-de-gezondheidsmeter)[](#construct-de-gezondheidsmeter)

Met de [schermcontainer geconfigureerd](#maak-een-schermcontainer) , kun je beginnen met het construeren van de gezondheidsmeter met behulp van Roblox UI-objecten zoals [frames](/docs/nl-nl/ui/frames)  en een [afbeeldingslabel](/docs/nl-nl/ui/labels) .

 ![Basic components used for the health meter.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Components.png)

### [Maak het bovenliggende frame](#maak-het-bovenliggende-frame)[](#maak-het-bovenliggende-frame)

Net als bij ontwerptoepassingen zoals Figma en Photoshop, dient een [Frame](/docs/nl-nl/reference/engine/classes/Frame)  in Roblox als een container voor andere UI-objecten. Voor deze tutorial zal de gehele gezondheidsmeter worden contained in een enkel bovenliggend frame, waardoor het eenvoudig is om het opnieuw te positioneren over verschillende HUD-indelingen.

1.

Voeg een [Frame](/docs/nl-nl/reference/engine/classes/Frame)  toe aan HUDContainer . Het nieuwe frame verschijnt in de linkerbovenhoek als een leeg wit vierkant.

 ![New frame in viewport.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Parent-Frame.png)

Als het nieuwe frame niet in het viewport verschijnt, zorg er dan voor dat je GUI overlay  hebt ingeschakeld vanuit de [Visualisatie Opties](/docs/nl-nl/studio/overview#visualisatie-opties)  widget in de rechterbovenhoek van het 3D viewport.

2.

Hernoem de nieuwe frame-instantie naar MeterBar .

 ![New frame inserted and renamed to MeterBar.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer-MeterBar.png)

### [Positioneer het frame](#positioneer-het-frame)[](#positioneer-het-frame)

In Roblox wordt de positie van een UI-object weergegeven door een [UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)  coördinaten set die [Scale](/docs/nl-nl/reference/engine/datatypes/UDim#Scale)  en [Offset](/docs/nl-nl/reference/engine/datatypes/UDim#Offset)  waarden bevat voor zowel de X  als Y  assen:

-

[Scale](/docs/nl-nl/reference/engine/datatypes/UDim#Scale)  waarden vertegenwoordigen een percentage  van de grootte van de container langs de overeenkomstige as, optellend bij eventuele [Offset](/docs/nl-nl/reference/engine/datatypes/UDim#Offset)  waarden.

-

[Offset](/docs/nl-nl/reference/engine/datatypes/UDim#Offset)  waarden vertegenwoordigen hoeveel pixels  het object op de overeenkomstige as moet verschuiven, optellend bij eventuele [Scale](/docs/nl-nl/reference/engine/datatypes/UDim#Scale)  waarden.

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/UDim2-Components.png)

 ![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Scale-Offset-Positioning.png)

Om een UI-object in de rechterbovenhoek van de schermcontainer te positioneren, is [Scale](/docs/nl-nl/reference/engine/datatypes/UDim#Scale)  de beste benadering omdat een X  waarde van 1  (100%) de rechterrand van de container vertegenwoordigt, ongeacht de fysieke pixelgrootte van het scherm. Evenzo vertegenwoordigt een Y  schaalwaarde van 0  (0%) de bovenrand van de container.

 ![Scale ranges for the X and Y axes of a container.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/ScreenGui-Axis-Ranges.png)

Bovendien moet je een bovenste rechter [ankerpunt](/docs/nl-nl/ui/position-and-size#anchorpoint)  voor het bovenliggende frame instellen om het oorsprongspunt te definiëren. Acceptabele waarden liggen tussen 0  en 1 , relatief ten opzichte van de grootte van het object, dus een ankerwaarde van 1, 0  plaatst het ankerpunt van het frame in de rechterbovenhoek.

 ![Frame anchor point in its upper-right corner.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Parent-Frame-Anchor.png)

1.

Selecteer in het Explorer -venster het MeterBar  frame dat je eerder hebt ingevoegd.

 ![Explorer window showing the MeterBar frame selected.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer-MeterBar.png)

2.

Voer in het Properties -venster 1, 0, 0, 0  in voor [Position](/docs/nl-nl/reference/engine/classes/Frame#Position)  en druk op Enter . Studio zal automatisch de haakjes toevoegen om de [UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)  van {1, 0},{0, 0}  te vormen.

3.

Voer 1, 0  in voor de [AnchorPoint](/docs/nl-nl/reference/engine/classes/Frame#AnchorPoint)  eigenschap. Het frame zou nu in de rechterbovenhoek van het [veilige gebied van het apparaat](#maak-gebruik-van-veilige-gebieden)  moeten zijn gepositioneerd, iets ingedrukt vanaf de rand als gevolg van de [opvulling](#stel-randopvulling-in) .

 ![Frame repositioned in upper-right corner of container.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Parent-Frame-Repositioned.png)

### [Wijzig de grootte van het frame](#wijzig-de-grootte-van-het-frame)[](#wijzig-de-grootte-van-het-frame)

Net als de positie wordt de [Size](/docs/nl-nl/reference/engine/classes/Frame#Size)  van een UI-object weergegeven door een [UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)  coördinaten set die [Scale](/docs/nl-nl/reference/engine/datatypes/UDim#Scale)  en [Offset](/docs/nl-nl/reference/engine/datatypes/UDim#Offset)  waarden bevat voor zowel de X  als Y  assen.

Standaard is de grootte van het nieuwe frame {0, 100},{0, 100} , wat betekent 100 pixels  in zowel breedte (X ) als hoogte (Y ). Hoewel een strikte pixelwaarde in bepaalde gevallen nuttig is, schalen veel UI-elementen responsiever over meerdere schermen wanneer ze zijn ingesteld op een percentage  van de totale grootte van de schermcontainer.

1.

Met het MeterBar  frame geselecteerd, open je het Properties -venster en ga je naar de [Size](/docs/nl-nl/reference/engine/classes/Frame#Size)  eigenschap.

2.

Voer een waarde in van 0.35, 0, 0.05, 0  om een percentagegrootte van 35% breed en 5% hoog in te stellen zonder extra pixel-offsets.

 ![Frame resized to 35% wide and 5% tall.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Parent-Frame-Resized.png)

### [Style het frame](#style-het-frame)[](#style-het-frame)

Standaard zijn [Frames](/docs/nl-nl/reference/engine/classes/Frame)  gevuld met solide wit. De uiteindelijke gezondheidsmeter moet een donkerdere en iets doorzichtige vulling hebben, evenals een donkere rand, zodat deze beter opvalt tegen zowel lichte als donkere achtergronden.

 ![Frame styled with opacity, border, and rounded corners.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Parent-Frame-Preview.png)

1.

Met het MeterBar  frame geselecteerd, voer je 0  in voor de [BackgroundColor3](/docs/nl-nl/reference/engine/classes/Frame#BackgroundColor3)  eigenschap. Studio zal dit automatisch omzetten naar de RGB-waarde van [0, 0, 0] .

2.

Voer 0.75  in voor de [BackgroundTransparency](/docs/nl-nl/reference/engine/classes/Frame#BackgroundTransparency)  eigenschap. In Roblox varieert de transparantie van 0  voor volledig ondoorzichtig tot 1  voor volledig transparant, dus 0.75  is gelijk aan 25% opaciteit in andere toepassingen zoals Figma of Photoshop.

 ![Frame restyled with dark background and 25% opacity.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Parent-Frame-Opaque.png)

3.

Voeg een [UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke)  object toe, een krachtige UI-modifier die een [aanpasbare rand](/docs/nl-nl/ui/appearance-modifiers#omtrek)  aan het frame toevoegt.

 ![Explorer window showing the MeterBar frame with a child UIStroke modifier.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer-MeterBar-UIStroke.png)

4.

Met de nieuwe [UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke)  geselecteerd, stel je de volgende eigenschappen in:

-

[Thickness](/docs/nl-nl/reference/engine/classes/UIStroke#Thickness)  = 3

-

[Transparency](/docs/nl-nl/reference/engine/classes/UIStroke#Transparency)  = 0.25  (75% ondoorzichtig)

 ![Frame restyled with a UIStroke modifier.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Parent-Frame-Stroked.png)

Om de styling van het meterframe te voltooien, kun je de hoeken afronden om een "pil" vorm te vormen in plaats van een scherpe rechthoek.

1.

Voeg een [UICorner](/docs/nl-nl/reference/engine/classes/UICorner)  instantie toe aan het MeterBar  frame.

 ![Explorer window showing the MeterBar frame with a child UICorner modifier.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer-MeterBar-UICorner.png)

2.

Met de nieuwe [UICorner](/docs/nl-nl/reference/engine/classes/UICorner)  geselecteerd, stel je de [CornerRadius](/docs/nl-nl/reference/engine/classes/UICorner#CornerRadius)  in op 0.5, 0 . Het gebruik van een schaal  waarde van 0.5  (50%) in plaats van een pixelwaarde is vooral handig voor de meterbalk omdat het zorgt voor een volledig afgeronde curve, ongeacht hoe hoog of breed de container wordt.

 ![Frame corners rounded with a UICorner modifier.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Parent-Frame-Rounded.png)

### [Maak de binnenste vulling](#maak-de-binnenste-vulling)[](#maak-de-binnenste-vulling)

Nu het omhulsel van de gezondheidsmeter compleet is, kun je een binnenste vulling  toevoegen om de variabele gezondheid van het personage weer te geven. Aangezien het alleen een solide opgevulde regio hoeft te zijn, is een sub-kind [Frame](/docs/nl-nl/reference/engine/classes/Frame)  binnen het bovenliggende frame geschikt.

 ![Inner fill frame added to parent frame to represent the character's variable health.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Inner-Fill-Preview.png)

1.

Voeg een kind [Frame](/docs/nl-nl/reference/engine/classes/Frame)  toe aan het MeterBar  frame.

2.

Hernoem de nieuwe frame-instantie naar InnerFill .

 ![Explorer window showing the parent MeterBar frame with a child frame named InnerFill.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer-MeterBar-InnerFill.png)

3.

Met InnerFill  geselecteerd, stel je de volgende eigenschappen in:

-

[AnchorPoint](/docs/nl-nl/reference/engine/classes/Frame#AnchorPoint)  = 0, 0.5  (linker rand en verticale midden)

-

[Position](/docs/nl-nl/reference/engine/classes/Frame#Position)  = 0, 0, 0.5, 0

-

[Size](/docs/nl-nl/reference/engine/classes/Frame#Size)  = 1, 0, 1, 0

Aangezien kinderen van frames worden gepositioneerd en geformatteerd ten opzichte van hun ouder, zorgt het gebruik van schaal ervoor dat het binnenste frame de volledige breedte en hoogte van de ouder opvult, beginnend vanaf de linker rand van de ouder.

 ![Inner fill frame repositioned and resized to fill entire parent frame.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Inner-Fill-Resized.png)

4.

Om de "pil" vorm van het bovenliggende frame te matchen, voeg je een extra [UICorner](/docs/nl-nl/reference/engine/classes/UICorner)  toe aan InnerFill .

 ![Explorer window showing the InnerFill frame with a child UICorner modifier.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer-MeterBar-InnerFill-UICorner.png)

5.

Met de nieuwe [UICorner](/docs/nl-nl/reference/engine/classes/UICorner)  modifier geselecteerd, stel je de [CornerRadius](/docs/nl-nl/reference/engine/classes/UICorner#CornerRadius)  eigenschap in op 0.5, 0  om de "pil" vorm van het bovenliggende MeterBar  frame te matchen.

 ![Inner fill frame corners rounded with a UICorner modifier.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Inner-Fill-Rounded.png)

6.

Om beter weer te geven dat een volle meter goede gezondheid aangeeft, selecteer je InnerFill  en stel je de [BackgroundColor3](/docs/nl-nl/reference/engine/classes/Frame#BackgroundColor3)  eigenschap in op [0, 225, 50]  (in een latere taak zul je [script](#luister-naar-gezondheidsveranderingen)  deze kleur laten veranderen op basis van de werkelijke gezondheid).

 ![Inner fill frame recolored green to represent good health.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Inner-Fill-Colored.png)

### [Voeg het pictogram toe](#voeg-het-pictogram-toe)[](#voeg-het-pictogram-toe)

Om het doel van de meter duidelijker aan te geven, kun je een [afbeeldingslabel](/docs/nl-nl/ui/labels)  aan de linkerkant toevoegen, in dit geval een rode hart die vaak gezondheid of leven symboliseert.

 ![Image label of heart added to more clearly indicate a health meter.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Icon-Preview.png)

1.

Voeg een [ImageLabel](/docs/nl-nl/reference/engine/classes/ImageLabel)  toe aan het MeterBar  frame. Dit object stelt je in staat om een 2D-afbeeldingselement toe te passen dat als een decal naar Roblox is geüpload.

2.

Hernoem de nieuwe label-instantie naar Icon .

 ![Explorer window showing the MeterBar frame with a child ImageLabel.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer-MeterBar-Icon.png)

3.

Met Icon  geselecteerd, stel je de [ZIndex](/docs/nl-nl/reference/engine/classes/ImageLabel#ZIndex)  eigenschap in op 2 . Terwijl nieuw ingevoegde UI-objecten altijd voor eerder ingevoegde objecten worden gelaagd, zorgt deze wijziging ervoor dat het pictogram altijd voor de frame-elementen van de meter wordt weergegeven.

 ![Properties window showing the ZIndex of the ImageLabel set to 2.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer-MeterBar-Icon-Values.png)

4.

Zoek de [Image](/docs/nl-nl/reference/engine/classes/ImageLabel#Image)  eigenschap van het pictogram en voer rbxassetid://91715286435585  in, de referentie naar een vooraf geüpload hartafbeelding (indien gewenst, kun je [je eigen afbeelding importeren](/docs/nl-nl/projects/assets/manager#asset-import)  en de asset-ID gebruiken).

 ![Image label of heart added to MeterBar frame.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Icon-Large.png)

5.

Om ervoor te zorgen dat het pictogram [ImageLabel](/docs/nl-nl/reference/engine/classes/ImageLabel)  altijd een 1:1 beeldverhouding behoudt, voeg je een [UIAspectRatioConstraint](/docs/nl-nl/reference/engine/classes/UIAspectRatioConstraint)  toe. Hoewel deze [constraint](/docs/nl-nl/ui/size-modifiers#beperkingen)  aanpasbare eigenschappen heeft om de beeldverhouding te beheersen, kun je de standaardwaarden intact laten.

 ![Explorer window showing the ImageLabel with a child UIAspectRatioConstraint.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer-MeterBar-Icon-UIAspectRatioConstraint.png)

6.

Met Icon  geselecteerd, rond je het uiterlijk en de positie af door de volgende eigenschappen te wijzigen:

-

[AnchorPoint](/docs/nl-nl/reference/engine/classes/ImageLabel#AnchorPoint)  = 0.5, 0.5  (centraal anker)

-

[BackgroundTransparency](/docs/nl-nl/reference/engine/classes/ImageLabel#BackgroundTransparency)  = 1  (100% transparant)

-

[Position](/docs/nl-nl/reference/engine/classes/ImageLabel#Position)  = 0, 0, 0.5, 0  (linkerkant van de meter en verticale midden)

-

[Size](/docs/nl-nl/reference/engine/classes/ImageLabel#Size)  = 2, 0, 2, 0  (200% van de totale grootte van het MeterBar  frame, beperkt tot 1:1 door de [UIAspectRatioConstraint](/docs/nl-nl/reference/engine/classes/UIAspectRatioConstraint) )

 ![Image label of heart repositioned and resized with background fill made transparent.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Meter-Design-Icon-Finalized.png)

### [Beperk de grootte](#beperk-de-grootte)[](#beperk-de-grootte)

Hoewel een [schaalhoogte](#wijzig-de-grootte-van-het-frame)  van 0.05  (5%) er goed uitziet op moderne telefoons en gamingmonitoren met een 16:9 beeldverhouding of breder, kan de meter er iets te hoog uitzien op tablet schermen en oudere telefoons. Je kunt dit controleren door een tablet zoals iPad 7e Generatie  te emuleren vanuit de Device Emulator .

 ![Device Emulator set to emulate a tablet device.](https://prod.docsiteassets.roblox.com/assets/studio/general/Device-Emulator-Tablet.png)  ![Emulation on tablet device with meter bar taller than desired.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Emulation-Tablet-Unconstrained.png)

Om de hoogte van de meterbalk consistenter te houden met bredere schermen, kun je een [UISizeConstraint](/docs/nl-nl/reference/engine/classes/UISizeConstraint)  toepassen om de maximale pixelhoogte te beperken.

1.

Voeg een [UISizeConstraint](/docs/nl-nl/reference/engine/classes/UISizeConstraint)  toe aan het MeterBar  frame.

 ![Explorer window showing the MeterBar frame with a child UISizeConstraint.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer-MeterBar-UISizeConstraint.png)

2.

Met de nieuwe constraint geselecteerd, stel je de [MaxSize](/docs/nl-nl/reference/engine/classes/UISizeConstraint#MaxSize)  eigenschap in op inf, 20  om de hoogte te beperken tot 20 pixels terwijl er geen breedtebeperkingen worden opgelegd.

 ![Properties window showing the MaxSize of the UISizeConstraint set to inf, 20.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterGui-HUDContainer-MeterBar-UISizeConstraint-Values.png)

Nu behoudt de meterbalk een consistenter hoogte tussen bredere en hogere schermen.

Telefoon Tablet

![Emulation on phone.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Emulation-Phone-Constrained.png)

## [Vervang de standaard gezondheidsmeter](#vervang-de-standaard-gezondheidsmeter)[](#vervang-de-standaard-gezondheidsmeter)

Roblox-games bevatten een standaard gezondheidsmeter die zichtbaar wordt wanneer personages schade oplopen. Als je de standaard meter zichtbaar houdt, zal deze dupliceren en mogelijk overlappen met de aangepaste meter.

 ![Default health meter overlapping and duplicating the custom health meter.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Default-Health-Meter.png)

### [Schakel de standaard meter uit](#schakel-de-standaard-meter-uit)[](#schakel-de-standaard-meter-uit)

Om de standaard gezondheidsmeter uit te schakelen, gebruik je een client script  ([LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript) ) binnen [StarterPlayerScripts](/docs/nl-nl/reference/engine/classes/StarterPlayerScripts)  dat [StarterGui:SetCoreGuiEnabled()](/docs/nl-nl/reference/engine/classes/StarterGui#SetCoreGuiEnabled)  aanroept.

1.

Zoek in het Explorer -venster de [StarterPlayer](/docs/nl-nl/reference/engine/classes/StarterPlayer)  container en zoek de [StarterPlayerScripts](/docs/nl-nl/reference/engine/classes/StarterPlayerScripts)  container daarin.

 ![Explorer window showing the StarterPlayerScripts container inside the StarterPlayer container.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterPlayer-StarterPlayerScripts.png)

2.

Voeg een nieuw [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  toe aan de container en hernoem het naar HideDefaultHealthMeter  om het doel ervan te beschrijven. Scripts binnen [StarterPlayerScripts](/docs/nl-nl/reference/engine/classes/StarterPlayerScripts)  worden automatisch uitgevoerd wanneer de lokale speler een game join, waardoor het een ideale container is om een script uit te voeren dat de standaard meter permanent verbergt.

 ![Explorer window showing the new HideDefaultHealthMeter client script inside the StarterPlayerScripts container.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterPlayer-StarterPlayerScripts-HideDefaultHealthMeter.png)

3.

Wanneer je een nieuw script invoegt, opent het automatisch in een nieuw scripteditor-tabblad (als dat niet gebeurt, dubbelklik dan op het script in het Explorer -venster).

Plak de volgende code in het HideDefaultHealthMeter  script:

HideDefaultHealthMeter

```

local StarterGui = game:GetService("StarterGui")

-- Verberg standaard gezondheidsmeter

StarterGui:SetCoreGuiEnabled(Enum.CoreGuiType.Health, false)

```

Code Uitleg

| Regel | | Doel |
| --- | --- |
| 1 | | Verkrijgt een referentie naar een kern [service](/docs/nl-nl/scripting/services) , [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui) , die dezelfde container vertegenwoordigt waar je de aangepaste gezondheidsmeter hebt gemaakt en waarvan de inhoud in de [PlayerGui](/docs/nl-nl/reference/engine/classes/PlayerGui)  container voor elke speler die de game join, wordt gekloond. |
| 4 | | Roep de methode [SetCoreGuiEnabled()](/docs/nl-nl/reference/engine/classes/StarterGui#SetCoreGuiEnabled)  van de service aan en instrueert de standaard gezondheidsmeter om uitgeschakeld te worden (false ). |

Als je nu de game test en schade oploopt, zul je merken dat de standaard meter is uitgeschakeld en verborgen (je zult de aangepaste meter [script](#luister-naar-gezondheidsveranderingen)  om de gezondheidsveranderingen in de volgende sectie weer te geven).

 ![Default health meter disabled.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/Default-Health-Meter-Disabled.png)

### [Luister naar gezondheidsveranderingen](#luister-naar-gezondheidsveranderingen)[](#luister-naar-gezondheidsveranderingen)

Alle standaard Roblox-personagemodellen bevatten een [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  klasse die speciale gedragingen en functionaliteit aan het personage biedt, zoals het instellen van de loop-/ren-snelheid en het beheren van de gezondheid. [Health](/docs/nl-nl/reference/engine/classes/Humanoid#Health)  veranderingen op de server [repliceren](/docs/nl-nl/projects/client-server#replicatie)  naar de client van elke speler en je kunt deze veranderingen detecteren om zowel de grootte als de kleur van de aangepaste gezondheidsmeter bij te werken.

1.

Zoek in het Explorer -venster de [StarterCharacterScripts](/docs/nl-nl/reference/engine/classes/StarterCharacterScripts)  container binnen [StarterPlayer](/docs/nl-nl/reference/engine/classes/StarterPlayer) .

 ![Explorer window showing the StarterCharacterScripts container inside the StarterPlayer container.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterPlayer-StarterCharacterScripts.png)

2.

Voeg een nieuw [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  toe aan de container en hernoem het naar UpdateCustomMeter  om het doel ervan te beschrijven. Scripts binnen [StarterCharacterScripts](/docs/nl-nl/reference/engine/classes/StarterCharacterScripts)  worden automatisch uitgevoerd elke keer dat het personage van de speler spawnt, waardoor het een ideale container is om een script uit te voeren dat de gezondheidsmeter volledig reset bij elke respawn.

 ![Explorer window showing the new UpdateCustomMeter client script inside the StarterCharacterScripts container.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-hud-meters/StarterPlayer-StarterCharacterScripts-UpdateCustomMeter.png)

3.

Plak de volgende code in het editorvenster voor het UpdateCustomMeter  script:

UpdateCustomMeter

```

local Players = game:GetService("Players")

-- Referentie naar lokale speler, personage en humanoïde

local player = Players.LocalPlayer

local character = player.Character

local humanoid = character:WaitForChild("Humanoid")

-- Referentie naar meterbalk binnenste frame

local playerGui = player:WaitForChild("PlayerGui")

local meterBarInner = playerGui.HUDContainer.MeterBar.InnerFill

-- Kleurverloop sequentie kleuren (rood, oranje, geel, limoen, groen)

local gradient = {

	Color3.fromRGB(225, 50, 0),

	Color3.fromRGB(255, 100, 0),

	Color3.fromRGB(255, 200, 0),

	Color3.fromRGB(150, 225, 0),

	Color3.fromRGB(0, 225, 50)

}

-- Functie om kleur in kleurverloop sequentie te krijgen van fractiepunt

local function getColorFromSequence(fraction: number): Color3

	-- Elke kleur in het kleurverloop definieert het begin en/of einde van een sectie

	local numSections = #gradient - 1

	-- Elke sectie vertegenwoordigt een deel van 1

	local sectionSize = 1 / numSections

	-- Bepaal in welke sectie de gevraagde fractie valt

	local sectionStartIndex = 1 + math.clamp(fraction, 0, 1) // sectionSize

	-- Verkrijg de kleuren aan het begin en einde van de sectie

	local sectionColorStart = gradient[sectionStartIndex]

	local sectionColorEnd = gradient[sectionStartIndex + 1] or sectionColorStart

	-- Normaliseer fractie tot een getal van 0 tot 1 binnen de sectie

	local fractionOfSection = math.clamp(fraction, 0, 1) % sectionSize / sectionSize

	-- Lerp tussen begin en einde op basis van de genormaliseerde fractie

	return sectionColorStart:Lerp(sectionColorEnd, fractionOfSection)

end

local function onHealthChanged()

	-- Bereken nieuwe gezondheid als percentage van max

	local healthFraction = math.max(0, humanoid.Health / humanoid.MaxHealth)

	-- Stel de balk in op nieuwe grootte/kleurdoelen

	meterBarInner.Size = UDim2.new(healthFraction, 0, 1, 0)

	meterBarInner.BackgroundColor3 = getColorFromSequence(healthFraction)

end

-- Luister naar veranderingen in de gezondheid van de humanoïde

humanoid.HealthChanged:Connect(onHealthChanged)

-- Stel aanvankelijk (of reset) de balkgrootte/kleur in op de huidige gezondheid

onHealthChanged()

```

Code Uitleg

| Regels | | Doel |
| 4 ‑ 6 | | Verkrijgt referenties naar de lokale [Player](/docs/nl-nl/reference/engine/classes/Player) , hun [Character](/docs/nl-nl/reference/engine/classes/Player#Character)  model, en de [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  klasse daarin. |
| 9 ‑ 10 | | Verkrijgt een referentie naar het InnerFill  object van de meter dat moet worden aangepast in grootte en kleur naarmate de gezondheid van het personage verandert. |
| 13 ‑ 19 | | Declareert een array van vijf kleuren (rood, oranje, geel, limoen, groen) om de meter op verschillende punten opnieuw te kleuren; bijvoorbeeld, groen voor 100% gezondheid, geel voor 50%, rood voor 0%, of een mengsel op een fractie tussen de kernpunten. |
| 22 ‑ 41 | | Helperfunctie die de kleurblend tussen een van de kleurverloop-kernpunten retourneert. |
| 43 ‑ 50 | | Functie die alle veranderingen in de gezondheid afhandelt. Hier berekent het de nieuwe gezondheid als een percentage van de [MaxHealth](/docs/nl-nl/reference/engine/classes/Humanoid#MaxHealth)  van het personage, past InnerFill  aan naar dat schaalpercentage, en kleurt het opnieuw naar de kleur die wordt geretourneerd door de getColorFromSequence()  functie. |
| 53 | | De belangrijkste [evenement](/docs/nl-nl/scripting/events)  verbinding die [Health](/docs/nl-nl/reference/engine/classes/Humanoid#Health)  veranderingen detecteert die van de server zijn gerepliceerd en roept de onHealthChanged()  functie aan. |
| 56 | | Initieel (bij het spawnen of respawnen van het personage) roept de onHealthChanged()  functie aan om InnerFill  in te stellen op de juiste percentagegrootte en kleur. Gewoonlijk zal dit de volledige breedte en groen zijn. |

Als je nu de game test, zul je merken dat de aangepaste meter correct de grootte en kleur bijwerkt naarmate het personage schade oploopt:

Standaard bevat het Roblox-gezondheidsmetersysteem een geleidelijke genezingseffect dat personages in staat stelt om langzaam gezondheid te regenereren. Als je dit effect wilt uitschakelen, voeg dan een leeg [Script](/docs/nl-nl/reference/engine/classes/Script)  genaamd Health  toe aan de [StarterCharacterScripts](/docs/nl-nl/reference/engine/classes/StarterCharacterScripts)  container. Dit voorkomt dat het standaard interne script voor elke speler wordt geladen, waardoor het regeneratie-effect effectief wordt verwijderd.

### [Animeer de meterbalk](#animeer-de-meterbalk)[](#animeer-de-meterbalk)

Om een extra niveau van verfijning aan de aangepaste meter toe te voegen, kun je gezondheidsveranderingen animeren door middel van tweening , waarbij de grootte en kleur van de meterbalk geleidelijk over ½ seconde veranderen.

1.

Open het scripteditor-tabblad voor het UpdateCustomMeter  script dat je eerder hebt bewerkt.

2.

Selecteer alle regels (Ctrl A  of ⌘ A ) en plak ze vervolgens over elkaar (Ctrl V  of ⌘ V ) met de volgende code:

UpdateCustomMeter

```

local Players = game:GetService("Players")

local TweenService = game:GetService("TweenService")

-- Referentie naar lokale speler, personage en humanoïde

local player = Players.LocalPlayer

local character = player.Character

local humanoid = character:WaitForChild("Humanoid")

-- Tween-eigenschappen

local tweenInfo = TweenInfo.new(0.5, Enum.EasingStyle.Exponential, Enum.EasingDirection.Out)

-- Referentie naar meterbalk binnenste frame

local playerGui = player:WaitForChild("PlayerGui")

local meterBarInner = playerGui.HUDContainer.MeterBar.InnerFill

-- Kleurverloop sequentie kleuren (rood, oranje, geel, limoen, groen)

local gradient = {

	Color3.fromRGB(225, 50, 0),

	Color3.fromRGB(255, 100, 0),

	Color3.fromRGB(255, 200, 0),

	Color3.fromRGB(150, 225, 0),

	Color3.fromRGB(0, 225, 50)

}

-- Functie om kleur in kleurverloop sequentie te krijgen van fractiepunt

local function getColorFromSequence(fraction: number): Color3

	-- Elke kleur in het kleurverloop definieert het begin en/of einde van een sectie

	local numSections = #gradient - 1

	-- Elke sectie vertegenwoordigt een deel van 1

	local sectionSize = 1 / numSections

	-- Bepaal in welke sectie de gevraagde fractie valt

	local sectionStartIndex = 1 + math.clamp(fraction, 0, 1) // sectionSize

	-- Verkrijg de kleuren aan het begin en einde van de sectie

	local sectionColorStart = gradient[sectionStartIndex]

	local sectionColorEnd = gradient[sectionStartIndex + 1] or sectionColorStart

	-- Normaliseer fractie tot een getal van 0 tot 1 binnen de sectie

	local fractionOfSection = math.clamp(fraction, 0, 1) % sectionSize / sectionSize

	-- Lerp tussen begin en einde op basis van de genormaliseerde fractie

	return sectionColorStart:Lerp(sectionColorEnd, fractionOfSection)

end

local function onHealthChanged()

	-- Bereken nieuwe gezondheid als percentage van max

	local healthFraction = math.max(0, humanoid.Health / humanoid.MaxHealth)

	-- Tween de balk naar nieuwe grootte/kleurdoelen

	local tweenGoal = {

		Size = UDim2.new(healthFraction, 0, 1, 0),

		BackgroundColor3 = getColorFromSequence(healthFraction)

	}

	local meterBarTween = TweenService:Create(meterBarInner, tweenInfo, tweenGoal)

	meterBarTween:Play()

end

-- Luister naar veranderingen in de gezondheid van de humanoïde

humanoid.HealthChanged:Connect(onHealthChanged)

-- Initieel stel (of reset) de balkgrootte/kleur in op de huidige gezondheid

onHealthChanged()

```

Belangrijke toevoegingen/wijzigingen

| Regels | | Doel |
| 2 | | Verkrijgt een referentie naar [TweenService](/docs/nl-nl/reference/engine/classes/TweenService)  om tweeningfunctionaliteit binnen het script te implementeren. |
| 10 | | Creëert een [TweenInfo](/docs/nl-nl/reference/engine/datatypes/TweenInfo)  constructor die de beoogde duur van de tween, [easingstijl](/docs/nl-nl/ui/animation#stijl) , en [easingrichting](/docs/nl-nl/ui/animation#richting)  definieert. |
| 52 ‑ 57 | | In plaats van simpelweg de grootte en kleur van de balk in te stellen zoals in de [vorige versie](#luister-naar-gezondheidsveranderingen) , declareert een tweenGoal  tabel met de doelgrootte/kleur, creëert een nieuwe tween met behulp van de tweenInfo  en tweenGoal  parameters, en speelt de nieuwe tween af. |

Als je nu de game test, zul je merken dat de aangepaste meter tussen elke verandering in gezondheid tweent:

### [Voeg een schade-effect toe](#voeg-een-schade-effect-toe)[](#voeg-een-schade-effect-toe)

Het standaard gezondheidsmetersysteem bevat een korte, subtiele rode tint op de schermranden wanneer het personage schade oploopt. Door de [standaard meter uit te schakelen](#schakel-de-standaard-meter-uit) , wordt dit effect verwijderd, maar je kunt het vervangen door je eigen implementatie.

1.

Open het scripteditor-tabblad voor het UpdateCustomMeter  script dat je eerder hebt bewerkt.

2.

Selecteer alle regels en plak ze met de volgende code over elkaar:

UpdateCustomMeter

```

local Workspace = game:GetService("Workspace")

local Players = game:GetService("Players")

local TweenService = game:GetService("TweenService")

-- Referentie naar lokale speler, personage en humanoïde

local player = Players.LocalPlayer

local character = player.Character

local humanoid = character:WaitForChild("Humanoid")

-- Tween-eigenschappen

local tweenInfo = TweenInfo.new(0.5, Enum.EasingStyle.Exponential, Enum.EasingDirection.Out)

-- Variabele om de gezondheid van het personage op te slaan/cache

local cachedHealth = humanoid.Health / humanoid.MaxHealth

-- Verkrijg (of maak nieuwe) kleurcorrectie-effect binnen de camera van de speler

local colorCorrection = Workspace.CurrentCamera:FindFirstChildWhichIsA("ColorCorrectionEffect") or Instance.new("ColorCorrectionEffect", Workspace.CurrentCamera)

colorCorrection.Name = "DamageColorEffect"

-- Referentie naar meterbalk binnenste frame

local playerGui = player:WaitForChild("PlayerGui")

local meterBarInner = playerGui.HUDContainer.MeterBar.InnerFill

-- Kleurverloop sequentie kleuren (rood, oranje, geel, limoen, groen)

local gradient = {

	Color3.fromRGB(225, 50, 0),

	Color3.fromRGB(255, 100, 0),

	Color3.fromRGB(255, 200, 0),

	Color3.fromRGB(150, 225, 0),

	Color3.fromRGB(0, 225, 50)

}

-- Functie om kleur in kleurverloop sequentie te krijgen van fractiepunt

local function getColorFromSequence(fraction: number): Color3

	-- Elke kleur in het kleurverloop definieert het begin en/of einde van een sectie

	local numSections = #gradient - 1

	-- Elke sectie vertegenwoordigt een deel van 1

	local sectionSize = 1 / numSections

	-- Bepaal in welke sectie de gevraagde fractie valt

	local sectionStartIndex = 1 + math.clamp(fraction, 0, 1) // sectionSize

	-- Verkrijg de kleuren aan het begin en einde van de sectie

	local sectionColorStart = gradient[sectionStartIndex]

	local sectionColorEnd = gradient[sectionStartIndex + 1] or sectionColorStart

	-- Normaliseer fractie tot een getal van 0 tot 1 binnen de sectie

	local fractionOfSection = math.clamp(fraction, 0, 1) % sectionSize / sectionSize

	-- Lerp tussen begin en einde op basis van de genormaliseerde fractie

	return sectionColorStart:Lerp(sectionColorEnd, fractionOfSection)

end

local function onHealthChanged()

	-- Bereken nieuwe gezondheid als percentage van max

	local healthFraction = math.max(0, humanoid.Health / humanoid.MaxHealth)

	-- Tween de balk naar nieuwe grootte/kleurdoelen

	local tweenGoal = {

		Size = UDim2.new(healthFraction, 0, 1, 0),

		BackgroundColor3 = getColorFromSequence(healthFraction)

	}

	local meterBarTween = TweenService:Create(meterBarInner, tweenInfo, tweenGoal)

	meterBarTween:Play()

	-- Toon schade-effect als de nieuwe gezondheid lager is dan de gecachete gezondheid

	if healthFraction < cachedHealth then

		-- Cache nieuwe gezondheidswaarde

		cachedHealth = healthFraction

		-- Stel kleurcorrectie in op rood als de initiële tint voordat je tweent

		colorCorrection.TintColor = Color3.fromRGB(255, 25, 25)

		colorCorrection.Saturation = 2.5

		-- Tween de tint terug naar wit (neutraal en geen tintverandering van normaal)

		local colorCorrectionTweenGoal = {

			TintColor = Color3.fromRGB(255, 255, 255),

			Saturation = 0

		}

		local colorCorrectionTween = TweenService:Create(colorCorrection, tweenInfo, colorCorrectionTweenGoal)

		colorCorrectionTween:Play()

	end

end

-- Luister naar veranderingen in de gezondheid van de humanoïde

humanoid.HealthChanged:Connect(onHealthChanged)

-- Initieel stel (of reset) de balkgrootte/kleur in op de huidige gezondheid

onHealthChanged()

```

Belangrijke toevoegingen/wijzigingen

| Regels | | Doel |
| 14 | | Stelt een tijdelijke referentie (cachedHealth ) in om de hoeveelheid gezondheid van het personage tussen veranderingen bij te houden, zodat je kunt vergelijken of een verandering lager is (schade). |
| 17 ‑ 18 | | Bij de initiële spawnen van het personage, maakt een nieuwe [ColorCorrectionEffect](/docs/nl-nl/reference/engine/classes/ColorCorrectionEffect)  aan binnen de huidige [Camera](/docs/nl-nl/reference/engine/classes/Camera)  van de speler, of verkrijgt een referentie naar dezelfde instantie bij latere respawns. Door dit [post-processing effect](/docs/nl-nl/environment/post-processing-effects)  aan de camera van de speler te koppelen, wordt het alleen toegepast op hun lokale scherm, niet op het scherm van elke speler op de server. |
| 68 ‑ 83 | | Voert eerst een voorwaardelijke controle uit om te bevestigen dat de gezondheidsverandering lager is dan de waarde van cachedHealth , wat schade aangeeft; als dat zo is, stelt het cachedHealth  in op de nieuwe waarde. Vervolgens stelt het de tint van de [ColorCorrectionEffect](/docs/nl-nl/reference/engine/classes/ColorCorrectionEffect)  in op [255, 25, 25]  (rood) met een hogere verzadiging, en tweent vervolgens de tint terug naar de standaard neutrale witte tint ([255, 255, 255] ) zonder verzadiging. |

Als je nu de game test, zul je merken dat het scherm kort rood flitst telkens wanneer het personage schade oploopt:

Als je besluit de aangepaste meterbalk voor een ander doel aan te passen, zoals een mana-meter of vergiftigingsmeter, kun je de [TintColor](/docs/nl-nl/reference/engine/classes/ColorCorrectionEffect#TintColor)  op regel 73  wijzigen in iets geschikters voor het evenement, zoals lichtblauw ([200, 225, 255] )  of giftig groen ([0, 255, 75] ) .

Als je gezondheidsmeter niet overeenkomt met het uiterlijk of gedrag dat in deze tutorial wordt weergegeven, herinner je dan dat je [UI Fundamentals - HUD Meter](https://www.roblox.com/games/104506915856758/UI-Fundamentals-HUD-Meter)  kunt inspecteren als een voltooide referentietemplate.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
