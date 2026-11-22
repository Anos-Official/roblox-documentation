<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/ui/interactive-ui -->

Maak interactieve UI | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Gebruikersinterfaces

# Maak interactieve UI

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een HUD  (Heads-Up Display ) in je game toont doorgaans niet-interactieve UI-elementen zoals de gezondheidsmeter die wordt gedemonstreerd in [Maak HUD-meters](/docs/nl-nl/tutorials/use-case-tutorials/ui/create-hud-meters) . Daarnaast vereist bijna elke game interactieve  UI, zoals knoppen die reageren op speleractivatie, animaties wanneer ze worden geactiveerd, en het in-/uitfaden van menu's met andere interactieve bedieningselementen, enzovoort.

 ![In-game weergave met een instellingenknop en instellingenmenu met volumeschuifregelaars.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/Intro.png)

Met [UI Fundamentals - HUD Meter](https://www.roblox.com/games/104506915856758/UI-Fundamentals-HUD-Meter)  als startpunt en [UI Fundamentals - Interactiviteit](https://www.roblox.com/games/138499606610292/UI-Fundamentals-Interactivity)  als een voltooide referentie, demonstreert deze tutorial:

-

Hoe je een instellingenknop aan de bovenrand van het scherm plaatst.

-

Ontwerp van een instellingenmenu met interactieve versleepbare schuifregelaars.

-

Gebruik van een [ModuleScripts](/docs/nl-nl/reference/engine/classes/ModuleScript)  om "controller" modules te vormen voor uitbreidbare controle van UI-objecten met stateful declaraties.

-

Hoe je knoppen verbindt met speleractivatie om het instellingenmenu in/uit te schakelen.

-

Hoe je versleepbare UI-schuifregelaars verbindt om het volume van geluidseffecten en achtergrondgeluid afzonderlijk aan te passen.

## [Schakel de Apparaatemulator in](#schakel-de-apparaatemulator-in)[](#schakel-de-apparaatemulator-in)

Zoals opgemerkt in [Maak HUD-meters](/docs/nl-nl/tutorials/use-case-tutorials/ui/create-hud-meters) , hebben telefoons en tablets de minste schermruimte, dus het is belangrijk dat je UI-elementen op kleinere schermen passen en duidelijk zichtbaar zijn voor spelers. Als je dit nog niet hebt gedaan, schakel dan de [Apparaatemulator](/docs/nl-nl/studio/testing-modes#device-emulation)  in Studio in:

1.

Open de [UI Fundamentals - HUD Meter](https://www.roblox.com/games/104506915856758/UI-Fundamentals-HUD-Meter)  sjabloon in Studio.

2.

Schakel in het Test  menu van Studio de Apparaatemulator  in.

3.

Selecteer in de balk direct boven het hoofdvenster een telefoonemulatie zoals iPhone X  of Samsung Galaxy A51 . Stel vervolgens de weergavegrootte in op Aanpassen aan Venster  om de maximale ruimte in Studio te benutten.

 ![Instellingen van de Apparaatemulator aangegeven bovenaan het venster.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/Device-Emulator-Phone.png)

## [Maak de instellingenknop](#maak-de-instellingenknop)[](#maak-de-instellingenknop)

[GuiButtons](/docs/nl-nl/reference/engine/classes/GuiButton)  zijn interactieve gebruikersinterface-elementen met ingebouwde functionaliteit zoals het multi-platform [Activated](/docs/nl-nl/reference/engine/classes/GuiButton#Activated)  evenement dat wordt geactiveerd wanneer de knop wordt geklikt of getikt. De [GuiButton](/docs/nl-nl/reference/engine/classes/GuiButton)  klasse breidt zich uit naar twee variaties, [TextButton](/docs/nl-nl/reference/engine/classes/TextButton)  en [ImageButton](/docs/nl-nl/reference/engine/classes/ImageButton) , en deze tutorial gebruikt een "tandwiel" vormige [ImageButton](/docs/nl-nl/reference/engine/classes/ImageButton)  om het instellingenmenu open of gesloten te schakelen.

 ![Roblox-component gebruikt voor de instellingenknop.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/Settings-Button-Design-Components.png)

Om de instellingenknop te construeren:

1.

Zoek in het Explorer  venster HUDContainer  binnen [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui) .

 ![Explorer venster toont de geselecteerde HUDContainer.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer.png)

2.

Voeg een [ImageButton](/docs/nl-nl/reference/engine/classes/ImageButton)  toe aan HUDContainer  en hernoem deze naar SettingsButton .

 ![Explorer venster toont nieuwe ImageButton die is toegevoegd en hernoemd naar SettingsButton.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsButton.png)  ![Nieuwe ImageButton in het venster.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/Settings-Button-Design-Initial.png)

3.

Selecteer de nieuwe knop en stel het volgende in het Eigenschappen  venster in:

-

[AnchorPoint](/docs/nl-nl/reference/engine/classes/ImageButton#AnchorPoint)  = 0.5, 0.25  (horizontaal centrum en verticaal bovenste kwart)

-

[BackgroundTransparency](/docs/nl-nl/reference/engine/classes/ImageButton#BackgroundTransparency)  = 1  (volledig transparant)

-

[Position](/docs/nl-nl/reference/engine/classes/ImageButton#Position)  = 0.5, 0, 0, 0  (boven-centrale positionering)

-

[Size](/docs/nl-nl/reference/engine/classes/ImageButton#Size)  = 0.1, 0, 0.1, 0  (10% van de schermhoogte zodra de beeldverhouding is beperkt)

-

[Image](/docs/nl-nl/reference/engine/classes/ImageButton#Image)  = rbxassetid://104919049969988  (asset ID van "tandwiel" symbool)

4.

Voeg een [UIAspectRatioConstraint](/docs/nl-nl/reference/engine/classes/UIAspectRatioConstraint)  toe aan de knop met standaard eigenschappen (1:1 breedte tot hoogte).

 ![Explorer venster toont een nieuwe UIAspectRatioConstraint toegevoegd aan de SettingsButton knop.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsButton-UIAspectRatioConstraint.png)

5.

Om de maximale pixelhoogte van de knop te beperken, voeg een [UISizeConstraint](/docs/nl-nl/reference/engine/classes/UISizeConstraint)  toe en stel de [MaxSize](/docs/nl-nl/reference/engine/classes/UISizeConstraint#MaxSize)  in op inf, 44 .

![Explorer venster toont een nieuwe UISizeConstraint toegevoegd aan de SettingsButton knop.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsButton-UISizeConstraint.png)

![Eigenschappen venster toont verwachte waarden voor de nieuwe UISizeConstraint.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsButton-UISizeConstraint-Values.png)

 ![Eindresultaat van de instellingenknop in het bovenste midden van het scherm.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/Settings-Button-Design-Finalized.png)

## [Maak het instellingenmenu](#maak-het-instellingenmenu)[](#maak-het-instellingenmenu)

De nieuwe [instellingenknop](#maak-de-instellingenknop)  zal worden gescript om een instellingenmenu open en gesloten te schakelen, zodat spelers op aanvraag toegang hebben tot instellingen of andere informatie. In deze tutorial zal het menu interactieve schuifregelaars bevatten om de volumenniveaus van achtergrondgeluid en geluidseffecten onafhankelijk aan te passen.

 ![Basiscomponenten gebruikt voor het instellingenmenu.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/Settings-Menu-Design-Components.png)

### [Maak het bovenliggende frame](#maak-het-bovenliggende-frame)[](#maak-het-bovenliggende-frame)

Zoals opgemerkt in [Maak HUD-meters](/docs/nl-nl/tutorials/use-case-tutorials/ui/create-hud-meters) , dient een [Frame](/docs/nl-nl/reference/engine/classes/Frame)  als een container voor andere UI-objecten. Het hele instellingenmenu zal worden geconstrueerd met een enkel bovenliggend frame, waardoor het eenvoudig te beheren is als een stateful object dat anders reageert op invoer, afhankelijk van de huidige staat.

1.

Voeg een [Frame](/docs/nl-nl/reference/engine/classes/Frame)  toe aan HUDContainer  en hernoem deze naar SettingsMenu .

 ![Explorer venster toont nieuw frame toegevoegd en hernoemd naar SettingsMenu.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu.png)

2.

Selecteer SettingsMenu  en stel de volgende eigenschappen in:

-

[AnchorPoint](/docs/nl-nl/reference/engine/classes/Frame#AnchorPoint)  = 0.5  (centraal anker)

-

[BackgroundColor3](/docs/nl-nl/reference/engine/classes/Frame#BackgroundColor3)  = 30, 30, 60  (marineblauw)

-

[BackgroundTransparency](/docs/nl-nl/reference/engine/classes/Frame#BackgroundTransparency)  = 0.25  (75% ondoorzichtig)

-

[Position](/docs/nl-nl/reference/engine/classes/Frame#Position)  = 0.5, 0, 0.5, 0  (centrum van het scherm)

-

[Size](/docs/nl-nl/reference/engine/classes/Frame#Size)  = 0.75, 0, 0.75, 0  (75% breedte/hoogte van het ingesloten schermgebied)

 ![Frame opnieuw gepositioneerd, gewijzigd in grootte en gestyled met een transparante marineblauwe achtergrond.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/Settings-Menu-Design-Parent-Frame.png)

3.

Voeg een [UIAspectRatioConstraint](/docs/nl-nl/reference/engine/classes/UIAspectRatioConstraint)  toe aan SettingsMenu  en stel de [AspectRatio](/docs/nl-nl/reference/engine/classes/UIAspectRatioConstraint#AspectRatio)  eigenschap in op 2.5 . (2.5:1 breedte tot hoogte).

![Explorer venster toont een nieuwe UISizeConstraint toegevoegd aan het SettingsMenu frame.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu-UIAspectRatioConstraint.png)

![Eigenschappen venster toont verwachte waarden voor de nieuwe UISizeConstraint.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu-UIAspectRatioConstraint-Values.png)

4.

Voeg een [UICorner](/docs/nl-nl/reference/engine/classes/UICorner)  modifier toe aan SettingsMenu  en stel de [CornerRadius](/docs/nl-nl/reference/engine/classes/UICorner#CornerRadius)  in op 0.1, 0 .

![Explorer venster toont een nieuwe UICorner toegevoegd aan het SettingsMenu frame.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu-UICorner.png)

![Eigenschappen venster toont verwachte waarden voor de nieuwe UICorner modifier.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu-UICorner-Values.png)

5.

Om de pixelbreedte en -hoogte van SettingsMenu  te beperken, voeg een [UISizeConstraint](/docs/nl-nl/reference/engine/classes/UISizeConstraint)  toe. Stel de [MaxSize](/docs/nl-nl/reference/engine/classes/UISizeConstraint#MaxSize)  in op 800, inf  en de [MinSize](/docs/nl-nl/reference/engine/classes/UISizeConstraint#MinSize)  op 350, 0 .

![Explorer venster toont een nieuwe UISizeConstraint toegevoegd aan het SettingsMenu frame.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu-UISizeConstraint.png)

![Eigenschappen venster toont verwachte waarden voor de nieuwe UISizeConstraint.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu-UISizeConstraint-Values.png)

 ![Frame gestyled met afgeronde hoeken.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/Settings-Menu-Design-Parent-Frame-Finalized.png)

### [Construct een schuifregelaar](#construct-een-schuifregelaar)[](#construct-een-schuifregelaar)

Om spelers in staat te stellen volumenniveaus aan te passen, zal het instellingenmenu twee versleepbare schuifwidgets  bevatten die worden aangedreven door [UIDragDetector](/docs/nl-nl/reference/engine/classes/UIDragDetector) , een handig object dat interactie met 2D-gebruikersinterface-elementen vergemakkelijkt.

Om een bovenliggende container voor de eerste schuifregelaar te maken:

1.

Voeg een nieuw [Frame](/docs/nl-nl/reference/engine/classes/Frame)  toe aan de SettingsMenu  container en hernoem deze naar EffectsVolumeSlider .

 ![Explorer venster toont een nieuw frame toegevoegd aan het SettingsMenu frame, hernoemd naar EffectsVolumeSlider.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu-EffectsVolumeSlider.png)

2.

Selecteer het EffectsVolumeSlider  frame en stel de volgende eigenschappen in:

-

[AnchorPoint](/docs/nl-nl/reference/engine/classes/Frame#AnchorPoint)  = 0.5  (centraal anker)

-

[BackgroundTransparency](/docs/nl-nl/reference/engine/classes/Frame#BackgroundTransparency)  = 1  (volledig transparant)

-

[Position](/docs/nl-nl/reference/engine/classes/Frame#Position)  = 0.5, 0, 0.35, 0  (horizontaal centrum en 35% van de bovenkant van de container)

-

[Size](/docs/nl-nl/reference/engine/classes/Frame#Size)  = 0.8, 0, 0.1, 0  (80% van de breedte van de container en 10% van de hoogte)

 ![Leeg frame toegevoegd om schuifelementen te bevatten.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/Settings-Menu-Design-Slider-Frame-Measurements.png)

3.

Voeg een nieuwe [UIListLayout](/docs/nl-nl/reference/engine/classes/UIListLayout)  toe aan EffectsVolumeSlider . Deze lay-outmodifier is een krachtige manier om broeder [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  automatisch te rangschikken in horizontale rijen of verticale kolommen binnen hun bovenliggende container, inclusief de mogelijkheid om [flex](/docs/nl-nl/ui/list-flex-layouts)  concepten toe te passen.

 ![Explorer venster toont een nieuwe UIListLayout toegevoegd aan het EffectsVolumeSlider frame.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu-EffectsVolumeSlider-UIListLayout.png)

4.

Stel de volgende eigenschappen in voor de nieuwe [UIListLayout](/docs/nl-nl/reference/engine/classes/UIListLayout) :

-

[Padding](/docs/nl-nl/reference/engine/classes/UIListLayout#Padding)  = 0.06, 0  (6% padding tussen lijst elementen)

-

[FillDirection](/docs/nl-nl/reference/engine/classes/UIListLayout#FillDirection)  = [Horizontal](/docs/nl-nl/reference/engine/enums/FillDirection#Horizontal)  (links-naar-rechts rangschikking van elementen)

-

[HorizontalFlex](/docs/nl-nl/reference/engine/classes/UIListLayout#HorizontalFlex)  = [Fill](/docs/nl-nl/reference/engine/enums/UIFlexAlignment#Fill)  (vergroten van elementen in de breedte om de hele bovenliggende container te vullen, waarbij hun gedefinieerde breedte wordt overschreven)

-

[VerticalAlignment](/docs/nl-nl/reference/engine/classes/UIListLayout#VerticalAlignment)  = [Center](/docs/nl-nl/reference/engine/enums/VerticalAlignment#Center)  (elementen centreren langs hun verticale midden)

#### [Schuifregelaar icoon](#schuifregelaar-icoon)[](#schuifregelaar-icoon)

Een eenvoudig icoon met een audio-notitie en "burst" symbool helpt spelers de functie van de schuifregelaar te identificeren wanneer ze het instellingenmenu openen.

 ![Icoon die de functie van de schuifregelaar in het instellingenmenu aangeeft.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/Settings-Menu-Design-Slider-Icon.png)

1.

Voeg een [ImageLabel](/docs/nl-nl/reference/engine/classes/ImageLabel)  toe aan het EffectsVolumeSlider  frame en hernoem deze naar Icon . Dit icoon helpt spelers te begrijpen welk aspect van de game de schuifregelaar bedient.

 ![Explorer venster toont een ImageLabel toegevoegd aan het EffectsVolumeSlider frame.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu-EffectsVolumeSlider-Icon.png)

Let op dat het label een broeder  van de [UIListLayout](/docs/nl-nl/reference/engine/classes/UIListLayout)  moet zijn, niet een kind ervan.

2.

Selecteer Icon  en stel de volgende eigenschappen in:

-

[BackgroundTransparency](/docs/nl-nl/reference/engine/classes/ImageLabel#BackgroundTransparency)  = 1  (volledig transparant)

-

[Size](/docs/nl-nl/reference/engine/classes/ImageLabel#Size)  = 2.5, 0, 2.5, 0  (250% hoogte van het bovenliggende frame zodra de beeldverhouding is beperkt)

-

[Image](/docs/nl-nl/reference/engine/classes/ImageLabel#Image)  = rbxassetid://90019827067389  (asset ID van audio-notitie en "burst" symbool)

3.

Voeg een [UIAspectRatioConstraint](/docs/nl-nl/reference/engine/classes/UIAspectRatioConstraint)  toe aan Icon  en laat de eigenschappen als de standaardwaarden (1:1 breedte tot hoogte).

 ![Explorer venster toont een UIAspectRatioConstraint toegevoegd aan de ImageLabel.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu-EffectsVolumeSlider-Icon-UIAspectRatioConstraint.png)  ![Voltooid icoon in het instellingenmenu.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/Settings-Menu-Design-Slider-Icon-Finalized.png)

#### [Bereik frame](#bereik-frame)[](#bereik-frame)

Direct rechts van het [icoon](#schuifregelaar-icoon)  moet het interactieve gedeelte van de schuifregelaar worden contained binnen een andere [Frame](/docs/nl-nl/reference/engine/classes/Frame) .

 ![Doelgrootte en positie van het interactieve gedeelte van de schuifregelaar.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/Settings-Menu-Design-Range-Frame-Measurements.png)

1.

Voeg een nieuw [Frame](/docs/nl-nl/reference/engine/classes/Frame)  toe aan het EffectsVolumeSlider  frame en hernoem deze naar SliderFrame . Let op dat het een directe broeder  van de [UIListLayout](/docs/nl-nl/reference/engine/classes/UIListLayout)  lay-outmodifier moet zijn.

 ![Explorer venster toont een kind Frame toegevoegd aan het EffectsVolumeSlider frame.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu-EffectsVolumeSlider-SliderFrame.png)

2.

Selecteer SliderFrame  en stel de volgende eigenschappen in:

-

[BackgroundColor3](/docs/nl-nl/reference/engine/classes/Frame#BackgroundColor3)  = 0  (zwart)

-

[BackgroundTransparency](/docs/nl-nl/reference/engine/classes/Frame#BackgroundTransparency)  = 0.75  (25% ondoorzichtig)

-

[LayoutOrder](/docs/nl-nl/reference/engine/classes/Frame#LayoutOrder)  = 1

-

[Size](/docs/nl-nl/reference/engine/classes/Frame#Size)  = 1, 0, 1, 0  (100% breedte/hoogte van het bovenliggende frame)

Het is niet nodig om positionele  wijzigingen zoals [AnchorPoint](/docs/nl-nl/reference/engine/classes/Frame#AnchorPoint)  of [Position](/docs/nl-nl/reference/engine/classes/Frame#Position)  toe te wijzen, aangezien de [UIListLayout](/docs/nl-nl/reference/engine/classes/UIListLayout)  de positionering van zijn broeders beheert, in dit geval ze horizontaal van links naar rechts rangschikt en ze verticaal gecentreerd houdt ten opzichte van elkaar.

De [LayoutOrder](/docs/nl-nl/reference/engine/classes/Frame#LayoutOrder)  eigenschap is belangrijk bij het werken met lay-outmodifiers zoals [UIListLayout](/docs/nl-nl/reference/engine/classes/UIListLayout) , omdat het de volgorde bepaalt waarin broeders ten opzichte van elkaar worden geplaatst. Het wijzigen naar 1  voor SliderFrame  zorgt ervoor dat het rechts van Icon  wordt geplaatst, dat een standaard [LayoutOrder](/docs/nl-nl/reference/engine/classes/Frame#LayoutOrder)  van 0  heeft.

3.

Voeg de volgende modifiers toe aan SliderFrame :

-

[UICorner](/docs/nl-nl/reference/engine/classes/UICorner)  met zijn [CornerRadius](/docs/nl-nl/reference/engine/classes/UICorner#CornerRadius)  eigenschap ingesteld op 0.5, 0  ("pil" vorm)

-

[UISizeConstraint](/docs/nl-nl/reference/engine/classes/UISizeConstraint)  met zijn [MaxSize](/docs/nl-nl/reference/engine/classes/UISizeConstraint#MaxSize)  eigenschap ingesteld op inf, 30  (maximaal 30 pixels in hoogte)

-

[UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke)  met zijn [Color](/docs/nl-nl/reference/engine/classes/UIStroke#Color)  ingesteld op 0 , [Thickness](/docs/nl-nl/reference/engine/classes/UIStroke#Thickness)  op 3 , en [Transparency](/docs/nl-nl/reference/engine/classes/UIStroke#Transparency)  op 0.25  (75% ondoorzichtig zwarte omtrek)

 ![Slider frame gepositioneerd rechts van het icoon.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/Settings-Menu-Design-Range-Frame-Outline.png)

#### [Interactieve handgreep](#interactieve-handgreep)[](#interactieve-handgreep)

Met de [schuifcontainer](#bereik-frame)  geconstrueerd, kun je nu een versleepbare handgreep  maken voor spelers om mee te interageren tijdens het spel.

 ![Interactieve schuifhandgreep gepositioneerd binnen het bereikframe.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/Settings-Menu-Design-Slider-Handle.png)

1.

Voeg een nieuw [Frame](/docs/nl-nl/reference/engine/classes/Frame)  toe aan de SliderFrame  container en hernoem deze naar Handle .

 ![Explorer venster toont een kind Frame toegevoegd aan het SliderFrame frame en hernoemd naar Handle.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu-EffectsVolumeSlider-SliderFrame-Handle.png)

2.

Selecteer Handle  en stel de volgende eigenschappen in:

-

[AnchorPoint](/docs/nl-nl/reference/engine/classes/Frame#AnchorPoint)  = 0.5  (centraal anker)

-

[Position](/docs/nl-nl/reference/engine/classes/Frame#Position)  = 0.5, 0, 0.5, 0  (horizontaal en verticaal centrum van het bovenliggende frame)

-

[Size](/docs/nl-nl/reference/engine/classes/Frame#Size)  = 1.2, 0, 1.2, 0  (120% hoogte van het bovenliggende frame zodra de beeldverhouding is beperkt)

-

[ZIndex](/docs/nl-nl/reference/engine/classes/Frame#ZIndex)  = 3  (laag handgreep visueel voor andere schuifelementen)

3.

Voeg de volgende modifiers toe aan Handle :

-

[UIAspectRatioConstraint](/docs/nl-nl/reference/engine/classes/UIAspectRatioConstraint)  met zijn standaard eigenschappen (1:1 breedte tot hoogte)

-

[UICorner](/docs/nl-nl/reference/engine/classes/UICorner)  met zijn [CornerRadius](/docs/nl-nl/reference/engine/classes/UICorner#CornerRadius)  eigenschap ingesteld op 0.5, 0  (ronde vorm)

-

[UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke)  met zijn [Color](/docs/nl-nl/reference/engine/classes/UIStroke#Color)  ingesteld op [0, 150, 255]  en [Thickness](/docs/nl-nl/reference/engine/classes/UIStroke#Thickness)  op 8  (dikke blauwe omtrek)

4.

Voeg een [UIDragDetector](/docs/nl-nl/reference/engine/classes/UIDragDetector)  object toe aan Handle . Dit handige object vergemakkelijkt en moedigt interactie met 2D-gebruikersinterface-elementen aan.

 ![Explorer venster toont een UIDragDetector toegevoegd aan het Handle frame.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu-EffectsVolumeSlider-SliderFrame-Handle-UIDragDetector.png)

5.

Stel de volgende eigenschappen in voor de nieuwe [UIDragDetector](/docs/nl-nl/reference/engine/classes/UIDragDetector) :

-

[DragStyle](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragStyle)  = [TranslateLine](/docs/nl-nl/reference/engine/enums/UIDragDetectorDragStyle#TranslateLine)  (1D beweging langs de [DragAxis](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragAxis)  van de detector.)

-

[ResponseStyle](/docs/nl-nl/reference/engine/classes/UIDragDetector#ResponseStyle)  = [Scale](/docs/nl-nl/reference/engine/enums/UIDragDetectorResponseStyle#Scale)  (verplaatsen op basis van schaalwaarden van de positie van de ouder van de detector)

6.

Om ervoor te zorgen dat het lineaire sleepbereik van de handgreep beperkt is tot zijn container, koppel je de [BoundingUI](/docs/nl-nl/reference/engine/classes/UIDragDetector#BoundingUI)  eigenschap aan de SliderFrame  container:

1.

Selecteer de [UIDragDetector](/docs/nl-nl/reference/engine/classes/UIDragDetector) .

2.

Klik op zijn [BoundingUI](/docs/nl-nl/reference/engine/classes/UIDragDetector#BoundingUI)  eigenschap in het Eigenschappen  venster.

3.

Terug in het Explorer  venster, klik op de bovenliggende SliderFrame .

 ![Diagram toont het proces van het koppelen van de BoundingUI eigenschap van de detector aan de SliderFrame container.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/Link-UIDragDetector-BoundingUI.png)

De [BoundingUI](/docs/nl-nl/reference/engine/classes/UIDragDetector#BoundingUI)  eigenschap koppeling weerspiegelt nu de SliderFrame  container:

 ![Eigenschappen venster toont de BoundingUI eigenschap van de detector gekoppeld aan de SliderFrame container.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu-EffectsVolumeSlider-SliderFrame-Handle-UIDragDetector-Values.png)

Als je nu de game test, kun je de handgreep naar links en rechts slepen binnen zijn bovenliggende container:

#### [Binnenvulling](#binnenvulling)[](#binnenvulling)

Om duidelijker aan te geven dat de schuifregelaar een bereik van 0% tot 100% bedient, kun je een binnenvulling  aan de linkerkant van de container toevoegen die synchroniseert met de variabele positie van de handgreep.

 ![Binnenvullingsgedeelte van de schuifregelaar toegevoegd aan SliderFrame.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/Settings-Menu-Design-Slider-Inner-Fill.png)

1.

Voeg een nieuw [Frame](/docs/nl-nl/reference/engine/classes/Frame)  toe aan de SliderFrame  container en hernoem deze naar InnerFill .

 ![Explorer venster toont een kind Frame toegevoegd aan het SliderFrame frame en hernoemd naar InnerFill.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu-EffectsVolumeSlider-SliderFrame-InnerFill.png)

2.

Stel de volgende eigenschappen in voor het InnerFill  frame:

-

[AnchorPoint](/docs/nl-nl/reference/engine/classes/Frame#AnchorPoint)  = 0, 0.5  (linker rand en verticale centrum)

-

[BackgroundColor3](/docs/nl-nl/reference/engine/classes/Frame#BackgroundColor3)  = [0, 150, 255]  (blauw dat overeenkomt met de handgreep van de schuifregelaar)

-

[BackgroundTransparency](/docs/nl-nl/reference/engine/classes/Frame#BackgroundTransparency)  = 0.35  (65% ondoorzichtig)

-

[Position](/docs/nl-nl/reference/engine/classes/Frame#Position)  = 0, 0, 0.5, 0

-

[Size](/docs/nl-nl/reference/engine/classes/Frame#Size)  = 0.5, 0, 1, 0  (50% breedte en 100% hoogte van het bovenliggende frame)

-

[ZIndex](/docs/nl-nl/reference/engine/classes/Frame#ZIndex)  = 2  (laag visueel voor de vulling/omtrek van het bovenliggende frame)

3.

Om de "pil" vorm van de bovenliggende SliderFrame  container te matchen, voeg een [UICorner](/docs/nl-nl/reference/engine/classes/UICorner)  modifier toe en stel zijn [CornerRadius](/docs/nl-nl/reference/engine/classes/UICorner#CornerRadius)  eigenschap in op 0.5, 0 .

![Explorer venster toont een UICorner modifier toegevoegd aan het InnerFill frame.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu-EffectsVolumeSlider-SliderFrame-InnerFill-UICorner.png)

![Eigenschappen venster toont verwachte waarden voor de nieuwe UICorner.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu-EffectsVolumeSlider-SliderFrame-InnerFill-UICorner-Values.png)

 ![InnerFill frame gestyled met blauwe achtergrond en afgeronde hoeken.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/Settings-Menu-Design-Slider-Inner-Fill-Finalized.png)

### [Dupliceer de schuifregelaar](#dupliceer-de-schuifregelaar)[](#dupliceer-de-schuifregelaar)

Met de [eerste schuifregelaar](#construct-een-schuifregelaar)  geconstrueerd, kun je deze eenvoudig dupliceren en enkele visuele aspecten wijzigen om een ander doel aan te geven, in dit geval het volumenniveau van achtergrondgeluid gesymboliseerd door een icoon van muzikale noten.

 ![Doelpositie van de achtergrondgeluid schuifregelaar.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/Settings-Menu-Design-BackgroundVolumeSlider-Measurements.png)

1.

Selecteer het voltooide EffectsVolumeSlider  object.

 ![Explorer venster toont het geselecteerde voltooide EffectsVolumeSlider.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu-EffectsVolumeSlider-Full.png)

2.

Dupliceer het (Ctrl D  of ⌘ D ) en hernoem de duplicaat naar BackgroundVolumeSlider .

 ![Explorer venster toont de gedupliceerde schuifregelaar hernoemd naar BackgroundVolumeSlider.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu-BackgroundVolumeSlider.png)

3.

Wijzig de [Position](/docs/nl-nl/reference/engine/classes/Frame#Position)  van de duplicaat naar 0.5, 0, 0.7, 0  om deze onder de eerste schuifregelaar te verplaatsen.

 ![BackgroundVolumeSlider gepositioneerd onder EffectsVolumeSlider.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/Settings-Menu-Design-BackgroundVolumeSlider-Initial.png)

4.

Breid de bovenliggende tak van BackgroundVolumeSlider  uit, selecteer het Icon  afbeeldingslabel en wijzig de [Image](/docs/nl-nl/reference/engine/classes/ImageLabel#Image)  eigenschap naar rbxassetid://101125859760167  (asset ID van symbool met muzikale noten).

![Explorer venster toont het Icon label binnen BackgroundVolumeSlider.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu-BackgroundVolumeSlider-Icon.png)

![Eigenschappen venster toont verwachte waarden voor het Icon label.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu-BackgroundVolumeSlider-Icon-Values.png)

 ![BackgroundVolumeSlider met gewijzigde icoonafbeelding.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/Settings-Menu-Design-BackgroundVolumeSlider-Icon.png)

5.

Breid de SliderFrame  ⟩ Handle  tak uit, selecteer de [UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke)  modifier binnenin, en stel zijn [Color](/docs/nl-nl/reference/engine/classes/UIStroke#Color)  eigenschap in op [255, 0, 125]  (magenta).

![Explorer venster toont de UIStroke modifier binnen de handgreep van BackgroundVolumeSlider.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu-BackgroundVolumeSlider-SliderFrame-Handle-UIStroke.png)

![Eigenschappen venster toont verwachte waarden voor de UIStroke modifier.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu-BackgroundVolumeSlider-SliderFrame-Handle-UIStroke-Values.png)

 ![BackgroundVolumeSlider met gewijzigde icoonafbeelding.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/Settings-Menu-Design-BackgroundVolumeSlider-Handle.png)

6.

Selecteer het InnerFill  frame binnen SliderFrame  en wijzig de [BackgroundColor3](/docs/nl-nl/reference/engine/classes/Frame#BackgroundColor3)  eigenschap naar dezelfde magenta kleur ([255, 0, 125] ) .

![Explorer venster toont het InnerFill frame binnen de SliderFrame container van BackgroundVolumeSlider.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu-BackgroundVolumeSlider-SliderFrame-InnerFill.png)

![Eigenschappen venster toont verwachte waarden voor het InnerFill frame.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu-BackgroundVolumeSlider-SliderFrame-InnerFill-Values.png)

 ![BackgroundVolumeSlider met gewijzigde InnerFill kleur.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/Settings-Menu-Design-BackgroundVolumeSlider-Inner-Fill.png)

### [Maak de sluitknop](#maak-de-sluitknop)[](#maak-de-sluitknop)

Het laatste element van het instellingenmenu is een sluitknop  die spelers een extra invoer biedt om het menu te sluiten (de SettingsButton  in het bovenste midden zal hetzelfde doel dienen).

 ![Instellingenmenu met sluitknop aangegeven in de rechterbovenhoek.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/Settings-Menu-Design-Close-Button.png)

1.

Voeg een nieuwe [ImageButton](/docs/nl-nl/reference/engine/classes/ImageButton)  toe aan de SettingsMenu  container en hernoem deze naar CloseButton .

 ![Explorer venster toont een nieuwe ImageButton toegevoegd aan SettingsMenu en hernoemd naar CloseButton.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu-CloseButton.png)  ![Lege ImageButton gepositioneerd in de rechterbovenhoek van het instellingenmenu.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/Settings-Menu-Design-Close-Button-Initial.png)

2.

Selecteer CloseButton  en stel de volgende eigenschappen in:

-

[AnchorPoint](/docs/nl-nl/reference/engine/classes/ImageButton#AnchorPoint)  = 1, 0  (rechterbovenhoek)

-

[BackgroundTransparency](/docs/nl-nl/reference/engine/classes/ImageButton#BackgroundTransparency)  = 1  (volledig transparant)

-

[Position](/docs/nl-nl/reference/engine/classes/ImageButton#Position)  = 1, -10, 0, 10  (10 pixels van de rechterbovenhoek)

-

[Size](/docs/nl-nl/reference/engine/classes/ImageButton#Size)  = 0.15, 0, 0.15, 0  (15% van de framehoogte zodra de beeldverhouding is beperkt)

-

[Image](/docs/nl-nl/reference/engine/classes/ImageButton#Image)  = rbxassetid://5577404210  (asset ID van het sluitknop symbool)

-

[ImageTransparency](/docs/nl-nl/reference/engine/classes/ImageButton#ImageTransparency)  = 0.25  (75% ondoorzichtig)

3.

Voeg een [UIAspectRatioConstraint](/docs/nl-nl/reference/engine/classes/UIAspectRatioConstraint)  toe aan de knop met standaard eigenschappen (1:1 breedte tot hoogte).

 ![Explorer venster toont een UIAspectRatioConstraint toegevoegd aan de CloseButton knop.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsMenu-CloseButton-UIAspectRatioConstraint.png)  ![Voltooide sluitknop in de rechterbovenhoek van het instellingenmenu.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/Settings-Menu-Design-Close-Button-Finalized.png)

## [Maak de controlemodules](#maak-de-controlemodules)[](#maak-de-controlemodules)

Een uitbreidbare controlemodule  setup maakt het beheer van interactieve UI eenvoudiger dan individuele scripts die binnen elk object zijn geplaatst. [ModuleScripts](/docs/nl-nl/reference/engine/classes/ModuleScript)  vergemakkelijken deze uitbreidbare functionaliteit door je in staat te stellen code tussen scripts aan beide zijden van de client-server grens of aan dezelfde kant van de grens te hergebruiken.

### [Stateful object controller](#stateful-object-controller)[](#stateful-object-controller)

De volgende stateful object controller module laat je gedrag aan UI-objecten zoals SettingsButton  en SettingsMenu  hechten, en eenvoudig schakelen/tweeneren tussen verschillende staten. Om de module te maken:

1.

Voeg een [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  toe aan de [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  container en hernoem deze naar StatefulObjectController .

 ![Explorer venster toont de StatefulObjectController module binnen de ReplicatedStorage container.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/ReplicatedStorage-StatefulObjectController.png)

2.

Plak de volgende code in de module:

StatefulObjectController

```

local TweenService = game:GetService("TweenService")

local StatefulObjectController = {}

StatefulObjectController.__index = StatefulObjectController

export type StateName = string

export type State = {

	transition: TweenInfo,

	properties: { [string]: any },

}

function StatefulObjectController.hydrate(props: {

		object: Instance,

		states: { [StateName]: State },

		initialStateName: StateName

	})

	local object, states, initialStateName = props.object, props.states, props.initialStateName

	local self = setmetatable({

		states = states,

		currentStateName = initialStateName,

		tweens = {},

	}, StatefulObjectController)

	-- Maak tweens voor hergebruik om te voorkomen dat er elke keer nieuwe tweens worden gemaakt wanneer de staat verandert

	for stateName, state in states do

		self.tweens[stateName] = TweenService:Create(object, state.transition, state.properties)

	end

	self:setState(self.currentStateName)

	return self

end

function StatefulObjectController:setState(stateName: StateName)

	local stateTween: Tween = self.tweens[stateName]

	if not stateTween then

		warn(string.format("Poging om %s in te stellen op onbekende staat '%s'", self.object:GetFullName(), stateName))

		return

	end

	self.currentStateName = stateName

	-- Zorg ervoor dat andere tweens niet conflicteren

	for _, tween in self.tweens do

		tween:Cancel()

	end

	stateTween:Play()

end

return StatefulObjectController

```

Code Uitleg

| Regels | | Doel |
| --- | --- |
| 6 ‑ 10 | | Definieert en exporteert de Luau types om autocompletion en linting te verbeteren bij het gebruik van deze module. |
| 12 ‑ 33 | | Functie die wordt gebruikt om gedrag aan een stateful UI-object te initialiseren en te hechten, waarbij een [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  als object , een tabel van staten en hun respectieve [TweenInfo](/docs/nl-nl/reference/engine/datatypes/TweenInfo)  gegevens, en een initiële staat naam worden geaccepteerd. Binnen deze functie construeren regels 26 ‑ 28  [Tweens](/docs/nl-nl/reference/engine/classes/Tween)  voor elke staat, en regel 30  roept de setState()  functie van de module aan om het object op de initiële staat in te stellen. |
| 35 ‑ 50 | | Functie die wordt gebruikt om de staat van een stateful object in te stellen/wijzigen. Binnen de functie zorgen regels 42  ervoor dat de currentStateName  van het object wordt ingesteld op de staat die wordt ingesteld, regels 45 ‑ 47  annuleren eventuele lopende tweens om conflicten te voorkomen, en regel 49  voert de tween(s) van de staat uit. |

### [Slider controller](#slider-controller)[](#slider-controller)

Een aanvullende module initialiseert en controleert de twee volumeschuifregelaars. Het stelt je ook in staat om een callbackfunctie aan elke schuifregelaar te koppelen om spelerinteractie met de schuifregelaar te detecteren en gewenste wijzigingen in de game toe te passen.

1.

Voeg een [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  toe aan de [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  container en hernoem deze naar SliderController .

 ![Explorer venster toont de SliderController module binnen de ReplicatedStorage container.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/ReplicatedStorage-SliderController.png)

2.

Plak de volgende code in de module:

SliderController

```

local SliderController = {}

SliderController.__index = SliderController

export type Value = number

export type OnChanged = (Value) -> ()

function SliderController.hydrate(props: {

		object: Instance,

		onChanged: OnChanged,

		initialValue: Value?

	})

	local object, onChanged, initialValue = props.object, props.onChanged, props.initialValue

	local handle = object:FindFirstChild("Handle", true)

	if not handle then

		warn(string.format("Poging om schuifregelaar %s te hydrateren maar kon Handle niet vinden", object:GetFullName()))

	end

	local innerFill = object:FindFirstChild("InnerFill", true)

	if not innerFill then

		warn(string.format("Poging om schuifregelaar %s te hydrateren maar kon InnerFill niet vinden", object:GetFullName()))

	end

	local dragDetector = handle:FindFirstChildWhichIsA("UIDragDetector")

	if not dragDetector then

		warn(string.format("Poging om schuifregelaar %s te hydrateren maar kon UIDragDetector niet vinden", object:GetFullName()))

	end

	local self = setmetatable({

		handle = handle,

		innerFill = innerFill,

		dragDetector = dragDetector,

		value = initialValue or 0.5,

		onChanged = onChanged,

	}, SliderController)

	-- Stel initiële waarde in

	self:setValue(self.value)

	-- Verbind detector met speler manipulatie

	self.dragConnection = dragDetector.DragContinue:Connect(function()

		self:setValue(handle.Position.X.Scale)

	end)

	return self

end

function SliderController:setValue(value: Value)

	local clampedValue = math.clamp(value, 0, 1)

	self.value = clampedValue

	-- Update de positie van de handgreep en de grootte van het binnenframe om overeen te komen

	self.handle.Position = UDim2.fromScale(clampedValue, 0.5)

	self.innerFill.Size = UDim2.fromScale(clampedValue, 1)

	-- Voer de callback van de gebruiker uit met de laatste waarde

	local changeSuccess, changeResult = pcall(self.onChanged, clampedValue)

	if not changeSuccess then

		warn("Fout in schuifcallback:", changeResult)

	end

end

return SliderController

```

Code Uitleg

| Regels | | Doel |
| 7 ‑ 46 | | Functie die wordt gebruikt om gedrag aan een schuifregelaar element te initialiseren en te hechten, waarbij de bovenliggende [Frame](/docs/nl-nl/reference/engine/classes/Frame)  van de schuifregelaar als object , een onChanged  callbackfunctie om schuifwijzigingen te verwerken, en een initiële waarde voor de positie van de handgreep van de schuifregelaar worden geaccepteerd. Binnen de functie bevestigen regels 14 ‑ 27  dat de schuifregelaar's [handgreep](#interactieve-handgreep) , [binnenvulling](#binnenvulling) , en [UIDragDetector](/docs/nl-nl/reference/engine/classes/UIDragDetector)  elementen bestaan. Regel 38  roept de setValue()  functie van de module aan en regels 41 ‑ 43  verbinden het [DragContinue](/docs/nl-nl/reference/engine/classes/UIDragDetector#DragContinue)  evenement van de drag detector met de setValue()  functie van de module (zie volgende rij voor details). |
| 48 ‑ 61 | | Functie die wordt gebruikt om de waarde van de schuifregelaar in te stellen. Binnen de functie zorgen regels 53 ‑ 54  ervoor dat de positie van de handgreep en de grootte van de binnenvulling zijn gesynchroniseerd, en regel 57  geeft de gewijzigde waarde door aan de callbackfunctie zodat je de waarde kunt gebruiken zoals nodig. |

## [Maak het instellingen script](#maak-het-instellingen-script)[](#maak-het-instellingen-script)

Met de [instellingenknop](#maak-de-instellingenknop)  en [instellingenmenu](#maak-het-instellingenmenu)  voltooid, kun je alles aan elkaar koppelen met een enkel script dat gebruikmaakt van de [controlemodules](#maak-de-controlemodules) .

1.

Voeg een nieuw [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  toe aan HUDContainer  en hernoem deze naar SettingsScript  om het doel ervan te beschrijven. Let op dat dit script op hetzelfde niveau (broeder) moet zijn als SettingsMenu  en SettingsButton , de top-level UI-objecten die het zal beheren.

 ![Explorer venster toont het SettingsScript script binnen de HUDContainer container.](https://prod.docsiteassets.roblox.com/assets/tutorials/interactive-ui/StarterGui-HUDContainer-SettingsScript.png)

2.

Plak de volgende code in het script:

SettingsScript

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local SoundService = game:GetService("SoundService")

local SliderController = require(ReplicatedStorage.SliderController)

local StatefulObjectController = require(ReplicatedStorage.StatefulObjectController)

local HUDContainer = script.Parent

-- Initialiseer instellingenknop

local settingsButton = StatefulObjectController.hydrate({

	object = HUDContainer:FindFirstChild("SettingsButton"),

	states = {

		menuOpen = {

			transition = TweenInfo.new(0.5, Enum.EasingStyle.Exponential, Enum.EasingDirection.Out),

			properties = {

				Rotation = 45,

			},

		},

		menuClosed = {

			transition = TweenInfo.new(0.5, Enum.EasingStyle.Exponential, Enum.EasingDirection.Out),

			properties = {

				Rotation = 0,

			},

		},

	},

	initialStateName = "menuClosed"

})

-- Initialiseer instellingenmenu frame

local settingsMenu = StatefulObjectController.hydrate({

	object = HUDContainer:FindFirstChild("SettingsMenu"),

	states = {

		menuOpen = {

			transition = TweenInfo.new(0.5, Enum.EasingStyle.Bounce, Enum.EasingDirection.Out),

			properties = {

				Position = UDim2.fromScale(0.5, 0.5),

				Visible = true,

			},

		},

		menuClosed = {

			transition = TweenInfo.new(0),

			properties = {

				Position = UDim2.fromScale(0.5, 0.4),

				Visible = false,

			},

		},

	},

	initialStateName = "menuClosed"

})

-- Initialiseer effecten volume schuifregelaar

local effectsAudio = SoundService:FindFirstChild("Effects")

local effectsVolumeSlider = SliderController.hydrate({

	object = HUDContainer:FindFirstChild("EffectsVolumeSlider", true),

	initialValue = effectsAudio and effectsAudio.Volume or 0.5,

	onChanged = function(value: SliderController.Value)

		if effectsAudio then

			effectsAudio.Volume = value

		end

	end,

})

-- Initialiseer achtergrond volume schuifregelaar

local backgroundAudio = SoundService:FindFirstChild("Background")

local backgroundVolumeSlider = SliderController.hydrate({

	object = HUDContainer:FindFirstChild("BackgroundVolumeSlider", true),

	initialValue = backgroundAudio and backgroundAudio.Volume or 0.5,

	onChanged = function(value: SliderController.Value)

		if backgroundAudio then

			backgroundAudio.Volume = value

		end

	end,

})

-- Verbind knoppen met spelerinteractie

HUDContainer:FindFirstChild("SettingsButton").Activated:Connect(function()

	local targetState = if settingsButton.currentStateName == "menuClosed"

		then "menuOpen"

		else "menuClosed"

	settingsButton:setState(targetState)

	settingsMenu:setState(targetState)

end)

HUDContainer:FindFirstChild("CloseButton", true).Activated:Connect(function()

	settingsButton:setState("menuClosed")

	settingsMenu:setState("menuClosed")

end)

```

3.

Raadpleeg de volgende secties om te verkennen hoe het script gebruikmaakt van de [controlemodules](#maak-de-controlemodules) .

Instellingenknop

Regels 10 - 27  initialiseren en hechten gedrag aan de [instellingenknop](#maak-de-instellingenknop)  als volgt:

| Regels | | Doel |
| 10 ‑ 11 | | Een lokale referentie settingsButton  wordt gedeclareerd en gehydrateerd met de StatefulObjectController.hydrate()  functie, en de SettingsButton  knop binnen HUDContainer  wordt verwezen als het object om te hydrateren. |
| 12 ‑ 25 | | Een states  tabel wordt doorgegeven met twee unieke staten, menuOpen  en menuClosed . Elke staat bevat een overgang om te verklaren (via een [TweenInfo](/docs/nl-nl/reference/engine/datatypes/TweenInfo) ) hoe de specifieke staat zijn doel-eigenschappen in de properties  tabel zal bereiken. In dit geval verklaart menuOpen  een staatsovergang naar 45° voor de [Rotation](/docs/nl-nl/reference/engine/classes/ImageButton#Rotation)  van de knop met een [Exponential](/docs/nl-nl/reference/engine/enums/EasingStyle#Exponential)  tween van ½ seconde, terwijl menuClosed  de knop effectief terugbrengt naar zijn standaardrotatie van 0 . |
| 26 | | De initiёle  staat van de knop wordt ingesteld op menuClosed  (dit kan worden ingesteld op elke staat naam binnen de states  tabel). |

Verderop in het script (regels 76 - 86 ), worden knoppen verbonden met spelerinteractie om UI-staatwijzigingen te activeren:

| Regels | | Doel |
| 76 ‑ 82 | | SettingsButton  is verbonden met het [Activated](/docs/nl-nl/reference/engine/classes/GuiButton#Activated)  evenement van de [GuiButton](/docs/nl-nl/reference/engine/classes/GuiButton)  klasse om een anonieme functie aan te roepen. Binnen de anonieme functie schakelen regels 77 ‑ 79  een targetState  variabele tussen menuOpen  en menuClosed . Regel 80  roept vervolgens setState()  aan om de staat van de knop in te stellen op targetState  en regel 81  doet hetzelfde voor SettingsMenu  zodat het opent of sluit met de activatie van SettingsButton . |
| 83 ‑ 86 | | CloseButton  is verbonden met het [Activated](/docs/nl-nl/reference/engine/classes/GuiButton#Activated)  evenement om een anonieme functie aan te roepen die de staat van zowel SettingsButton  als SettingsMenu  op menuClosed  instelt. |

Instellingenmenu

Regels 30 - 49  initialiseren en hechten gedrag aan het [instellingenmenu](#maak-het-instellingenmenu)  als volgt:

| Regels | | Doel |
| 30 ‑ 31 | | Een lokale referentie settingsMenu  wordt gedeclareerd en gehydrateerd met de StatefulObjectController.hydrate()  functie en het SettingsMenu  frame binnen HUDContainer  wordt verwezen als het object om te hydrateren. |
| 32 ‑ 46 | | Vergelijkbaar met de instellingenknop, wordt een states  tabel doorgegeven met twee unieke staten, menuOpen  en menuClosed . Hier verklaart menuOpen  een staatsovergang naar [UDim2.fromScale(0.5, 0.5)](/docs/nl-nl/reference/engine/datatypes/UDim2#fromScale)  voor de [Position](/docs/nl-nl/reference/engine/classes/Frame#Position)  van het frame met een [Bounce](/docs/nl-nl/reference/engine/enums/EasingStyle#Bounce)  tween van ½ seconde, evenals een [Visible](/docs/nl-nl/reference/engine/classes/Frame#Visible)  staat van true . In tegenstelling tot dat, verklaart menuClosed  een positionele staatsovergang naar [UDim2.fromScale(0.5, 0.4)](/docs/nl-nl/reference/engine/datatypes/UDim2#fromScale)  en [Visible](/docs/nl-nl/reference/engine/classes/Frame#Visible)  naar false , maar de [TweenInfo](/docs/nl-nl/reference/engine/datatypes/TweenInfo)  met 0  duur op regel 41  zorgt ervoor dat de staatsovergang onmiddellijk plaatsvindt. |
| 48 | | De initiёle staat van het frame wordt ingesteld op menuClosed . |

Verderop in het script (regels 76 - 86 ), wordt het instellingenmenu gekoppeld aan spelerinteractie:

| Regels | | Doel |
| 81 | | Stelt dezelfde targetState  voor SettingsMenu  in om te synchroniseren met de activatie van SettingsButton . |
| 85 | | Stelt de staat van SettingsMenu  in op menuClosed  wanneer CloseButton  wordt geactiveerd. |

Volume Schuifregelaars

Regels 51 - 73  initialiseren en hechten gedrag aan EffectsVolumeSlider  en BackgroundVolumeSlider  als volgt:

| Regels | | Doel |
| 52 | | Stelt een lokale referentie in naar de Effects  [SoundGroup](/docs/nl-nl/reference/engine/classes/SoundGroup)  binnen [SoundService](/docs/nl-nl/reference/engine/classes/SoundService) . Een [SoundGroup](/docs/nl-nl/reference/engine/classes/SoundGroup)  stelt je in staat om meerdere [Sounds](/docs/nl-nl/reference/engine/classes/Sound)  met elkaar te relateren en het volume van elk geluid in de groep te regelen via de [Volume](/docs/nl-nl/reference/engine/classes/SoundGroup#Volume)  eigenschap van de groep. |
| 53 ‑ 54 | | Een lokale referentie effectsVolumeSlider  wordt gedeclareerd en gehydrateerd met de SliderController.hydrate()  functie en het EffectsVolumeSlider  frame binnen HUDContainer  ⟩ SettingsMenu  wordt verwezen als het object om te hydrateren. Let op dat de tweede parameter van true  voor [FindFirstChild()](/docs/nl-nl/reference/engine/classes/Instance#FindFirstChild)  de methode vertelt om recursief naar beneden te kijken in de HUDContainer  tak om EffectsVolumeSlider  te vinden. |
| 55 | | De initiёle waarde van de schuifregelaar wordt ingesteld op het huidige [Volume](/docs/nl-nl/reference/engine/classes/SoundGroup#Volume)  van de Effects  geluidsgroep, of 0.5  als fallback. |
| 56 ‑ 60 | | Stelt de callbackfunctie in om schuifwaarde wijzigingen toe te passen op het volume van de Effects  geluidsgroep. |
| 64 ‑ 73 | | Bijna hetzelfde als regels 52 - 61 , behalve om het BackgroundVolumeSlider  frame binnen HUDContainer  ⟩ SettingsMenu  te hydrateren en schuifwaarde wijzigingen toe te passen op het volume van de Background  geluidsgroep. |

Met SettingsScript  op zijn plaats, biedt de game nu een volledig operationeel voorbeeld van interactieve UI dat een gerelateerde set UI-objecten koppelt aan spelerinteractie.

Als je interactieve UI niet overeenkomt met het uiterlijk of gedrag dat in deze tutorial wordt weergegeven, onthoud dan dat je [UI Fundamentals - Interactiviteit](https://www.roblox.com/games/138499606610292/UI-Fundamentals-Interactivity)  kunt inspecteren als een voltooide referentiesjabloon.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
