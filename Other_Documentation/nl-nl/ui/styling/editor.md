<!-- Source: https://create.roblox.com/docs/nl-nl/ui/styling/editor -->

Stijl Editor | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Gebruikersinterface](/docs/nl-nl/ui)
6. /
7. UI-styling

# Stijl Editor

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De ingebouwde Stijl Editor  is een uitgebreide tool waarmee je UI-stijlen voor Roblox-spellen kunt maken, beheren en toepassen via een combinatie van [tokens](#stijl-tokens) , [ontwerpsheets](#ontwerpsheets) , [stijlregels](#stijlregels)  en [thema's](#stijl-themas) .

Toegang tot de Stijl Editor  via het UI -tabblad.

 ![Stijl Editor tool aangegeven in het UI-tabblad van de Studio-toolbar](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Style-Editor.png)

Zodra je het opent, klik je op de knop Ontwerp Maken  om een basisstijlset te genereren.

 ![Knop Ontwerp Maken in het openingsdialoogvenster van de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Create-Design-Entry.png)

Het maken van een ontwerpstijlset via de Stijl Editor genereert een BaseStyleSheet  in een Design -map binnen [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) . Dit basisblad synchroniseert specifieke engine-niveau standaardinstellingen zoals de [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  standaard van [163, 162, 165]  met standaardinstellingen die voortkomen uit invoerworkflows in Studio. Het wordt ten zeerste aanbevolen om het basisstijlblad niet  te verwijderen of te proberen te wijzigen — bouw in plaats daarvan tokens en stijlregels rond een ontwerpsheet om aan je UI-doelen te voldoen.

Bovendien wordt er een StyleSheet -blad gegenereerd in de Design -map dat een [StyleDerive](/docs/nl-nl/reference/engine/classes/StyleDerive)  naar het basisstijlblad bevat. Als je ervoor kiest om die [StyleDerive](/docs/nl-nl/reference/engine/classes/StyleDerive)  te verwijderen, kunnen ongestylede waarden voor [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  onverwachte waarden worden, bijvoorbeeld een standaard [Size](/docs/nl-nl/reference/engine/classes/GuiObject#Size)  van 0, 0, 0, 0 .

## [Stijl tokens](#stijl-tokens)[](#stijl-tokens)

Stijl tokens , gedefinieerd via [attributen](/docs/nl-nl/studio/properties#instantie-attributen)  van een token [StyleSheet](/docs/nl-nl/reference/engine/classes/StyleSheet) , vertegenwoordigen UI-eigenschapsvariabelen die in verschillende stijlen en componenten kunnen worden gebruikt; bijvoorbeeld, er kan een gemeenschappelijke kleur zijn voor een [Frame.BackgroundColor3](/docs/nl-nl/reference/engine/classes/Frame#BackgroundColor3) , [TextLabel.TextColor3](/docs/nl-nl/reference/engine/classes/TextLabel#TextColor3) , en [UIStroke.Color](/docs/nl-nl/reference/engine/classes/UIStroke#Color) . Tokens zijn vergelijkbaar met [CSS-variabelen](/docs/nl-nl/ui/styling/css-comparisons#variabelen) .

Hoewel niet vereist voor UI-styling, worden tokens ten zeerste aanbevolen voor uitbreidbaar UI-ontwerp en stijlupdates in de loop van de tijd. Je moet beginnen met het maken van de volgende tokens om te begrijpen hoe ze zich verhouden tot andere aspecten van universele styling.

1.

Maak een nieuwe tokenstijlblad:

1.

In de linkerkolom van de Stijl Editor, beweeg de muis over Tokens , klik op de ⊕ , en selecteer Nieuwe Token StijlSheet .

2.

Hernoem het nieuwe blad naar TokenSheet .

 ![Nieuw tokenblad gemaakt in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-TokenSheet-New.png)

2.

Met het nieuwe tokenblad geselecteerd, maak je verschillende tokens door op Voeg een Token toe…  in het hoofdvenster te klikken. Deze tokens zullen door deze gids heen worden gebruikt voor zowel [regels](#stijlregels)  als [thema's](#stijl-themas) .

 ![Token toevoegingsveld in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-TokenSheet-Add-Token.png)

| Token Naam | | Type | | Waarde |
| --- | --- |
| Goud | | [Color3](/docs/nl-nl/reference/engine/datatypes/Color3) | | #ffcc00 |
| Magenta | | [Color3](/docs/nl-nl/reference/engine/datatypes/Color3) | | #ff0099 |
| Oranje | | [Color3](/docs/nl-nl/reference/engine/datatypes/Color3) | | #dd6030 |
| Oswald | | [Font](/docs/nl-nl/reference/engine/datatypes/Font) | | Oswald |
| Rad20 | | [UDim](/docs/nl-nl/reference/engine/datatypes/UDim) | | 0, 20 |
| RectL | | [UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2) | | 0, 300, 0, 160 |
| SquareL | | [UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2) | | 0, 200, 0, 200 |
| Text24 | | number | | 24 |
| Text32 | | number | | 32 |

 ![Tokens toegevoegd aan TokenSheet in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-TokenSheet-Tokens.png)

## [Ontwerpsheets](#ontwerpsheets)[](#ontwerpsheets)

Een ontwerpstijlblad aggregeert [stijlregels](#stijlregels)  en kan worden gekoppeld aan [DataModel](/docs/nl-nl/reference/engine/classes/DataModel) -bomen om stijl-eigenschappen toe te passen op UI-instanties. Slechts één [StyleSheet](/docs/nl-nl/reference/engine/classes/StyleSheet)  kan van toepassing zijn op een gegeven boom, hoewel je [thema's](#stijl-themas)  kunt gebruiken om gerelateerde stijlen in je UI te wisselen, een concept dat later in deze gids wordt behandeld.

Een voorgevuld ontwerpsheet genaamd StyleSheet  wordt gemaakt via de knop Ontwerp Maken . Het bevat klasseregels voor veelvoorkomende UI-objecten zoals [Frame](/docs/nl-nl/reference/engine/classes/Frame)  en [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel) . Het bevat ook twee [StyleDerive](/docs/nl-nl/reference/engine/classes/StyleDerive) -instanties die [tokens](#stijl-tokens)  en stijlen van het basisstijlblad afleiden (erfgen) voor gebruik in je aangepaste stylingconfiguraties.

 ![Initiële configuratie van het ontwerpsheet in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Initial-Config.png)

Zodra je een ontwerpsheet hebt, kun je een test [op‑scherm container](/docs/nl-nl/ui/on-screen-containers)  instellen om te gebruiken met de Stijl Editor, of een [in‑game container](/docs/nl-nl/ui/in-experience-containers)  als dat gewenst is.

1.

Beweeg de muis over [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui)  in de [Explorer](/docs/nl-nl/studio/explorer)  en voeg een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  in.

2.

Bevestig dat er een nieuwe [StyleLink](/docs/nl-nl/reference/engine/classes/StyleLink) -instantie verschijnt onder de [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  met zijn [StyleSheet](/docs/nl-nl/reference/engine/classes/StyleLink#StyleSheet) -eigenschap ingesteld op het StyleSheet -ontwerpsheet.

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/StarterGui-ScreenGui-StyleLink.png)

![](https://prod.docsiteassets.roblox.com/assets/studio/properties/StyleLink-StyleSheet.png)

Als de [StyleLink](/docs/nl-nl/reference/engine/classes/StyleLink)  niet is gemaakt, kun je er snel een maken door de [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  in de [Explorer](/docs/nl-nl/studio/explorer)  te selecteren, evenals het StyleSheet -ontwerpsheet in de linkerkolom van de Stijl Editor. Klik vervolgens op de knop Voeg StyleLink toe  in het rechterbovenste gedeelte van het hoofdvenster van de editor.

## [Stijlregels](#stijlregels)[](#stijlregels)

Stijl regels  zijn van toepassing op elke instantie die overeenkomt met de definitie van de [Selector](/docs/nl-nl/reference/engine/classes/StyleRule#Selector)  van de regel om kenmerken zoals de klassenaam, instantie-tag en hiërarchische relaties te matchen. Op hoog niveau werkt het matchen en wijzigen van instanties via de definitie van de [Selector](/docs/nl-nl/reference/engine/classes/StyleRule#Selector)  door middel van:

-

Roblox [klasse](#klasse-regel)  selectors die alle instanties van een gegeven UI-klasse targeten, bijvoorbeeld [Frame](/docs/nl-nl/reference/engine/classes/Frame) , [ImageLabel](/docs/nl-nl/reference/engine/classes/ImageLabel) , [TextButton](/docs/nl-nl/reference/engine/classes/TextButton) , enz.

-

Instanties [tag](#tag-regel)  selectors die specifieke UI-objecten targeten die zijn [getagd](/docs/nl-nl/studio/properties#instantie-tags)  via [CollectionService](/docs/nl-nl/reference/engine/classes/CollectionService) .

-

Instantie [modifiers](#ui-modifier)  toegepast via phantom [UIComponents](/docs/nl-nl/reference/engine/classes/UIComponent)  zoals [UICorner](/docs/nl-nl/reference/engine/classes/UICorner)  of [UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke) .

-

[GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  [staat](#staat-regel)  selectors die overeenkomen met een van de vier [Enum.GuiState](/docs/nl-nl/reference/engine/enums/GuiState)  enum-waarden zoals [Hover](/docs/nl-nl/reference/engine/enums/GuiState#Hover) .

-

Instantienaamselectie volgens de waarde van de UI-object [Instance.Name](/docs/nl-nl/reference/engine/classes/Instance#Name) .

### [Klasse regel](#klasse-regel)[](#klasse-regel)

Een stijl klasse  selector target alle instanties van een gegeven UI-klasse. De volgende regelopstelling stijlt alle [Frames](/docs/nl-nl/reference/engine/classes/Frame)  met een uniforme achtergrondkleur en grootte.

1.

In de linkerkolom van de Stijl Editor, selecteer Frame  in de UI Elementen -tak.

 ![Standaard klasse stijl in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Class-Rule-New-Class.png)

2.

Koppel twee eerder gemaakte [stijl tokens](#stijl-tokens)  aan twee [Frame](/docs/nl-nl/reference/engine/classes/Frame) -eigenschappen:

| Eigenschap | | Stijl Token |
| [BackgroundColor3](/docs/nl-nl/reference/engine/classes/Frame#BackgroundColor3) | | $Magenta |
| [Size](/docs/nl-nl/reference/engine/classes/Frame#Size) | | $SquareL |

1.

Klik op Voeg een Eigenschap toe…  in het hoofdvenster en selecteer de benodigde eigenschap. Merk op dat je trefwoorden kunt typen om sneller eigenschappen in het dropdownmenu te vinden.

2.

In plaats van een statische waarde in te voeren, klik je op de ⋮ -knop en selecteer je Koppel Token .

3.

Klik op de $  die in het waardeveld verschijnt en selecteer de juiste bijbehorende token.

![Token koppelworkflow in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Class-Rule-Configure.png)

 ![Klasse regel geconfigureerd met tokens in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Class-Rule-Tokens.png)

3.

Voeg een nieuwe [Frame](/docs/nl-nl/reference/engine/classes/Frame)  in de [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  die je eerder [hebt gemaakt en gelinkt](#ontwerpsheets) . De stijlen die je hebt gedefinieerd, zouden automatisch op deze moeten worden toegepast.

 ![Eind gestylede klasse regel in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Class-Rule-Result.png)

### [Tag regel](#tag-regel)[](#tag-regel)

Instantie tag  selectors targeten specifieke UI-objecten die zijn [getagd](/docs/nl-nl/studio/properties#instantie-tags)  via [CollectionService](/docs/nl-nl/reference/engine/classes/CollectionService) . De volgende regelopstelling stijlt een [TextButton](/docs/nl-nl/reference/engine/classes/TextButton)  die is getagd als ButtonPrimary  met een aangepaste achtergrondkleur, lettertype en tekstgrootte.

1.

In de linkerkolom van de Stijl Editor, beweeg de muis over het StyleSheet -blad, klik op de ⋮ -knop en navigeer naar Nieuw  ⟩ Tag .

 ![Creatie van tagregel in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Tag-Rule-New.png)

2.

Hernoem de nieuwe tagregel naar .ButtonPrimary  (let op de leidende . ).

 ![Tagregel hernoemd in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Tag-Rule-Renamed.png)

3.

Koppel drie eerder gemaakte [stijl tokens](#stijl-tokens)  aan drie [TextButton](/docs/nl-nl/reference/engine/classes/TextButton) -eigenschappen:

| Eigenschap | | Stijl Token |
| [BackgroundColor3](/docs/nl-nl/reference/engine/classes/TextButton#BackgroundColor3) | | $Gold |
| [FontFace](/docs/nl-nl/reference/engine/classes/TextButton#FontFace) | | $Oswald |
| [TextSize](/docs/nl-nl/reference/engine/classes/TextButton#TextSize) | | $Text32 |

1.

Klik op Voeg een Eigenschap toe…  in het hoofdvenster en selecteer de benodigde eigenschap. Vergeet niet dat je trefwoorden kunt typen om sneller eigenschappen in het dropdownmenu te vinden.

2.

In plaats van een statische waarde in te voeren, klik je op de ⋮ -knop en selecteer je Koppel Token .

3.

Klik op de $  die in het waardeveld verschijnt en selecteer de juiste bijbehorende token.

![Token koppelworkflow in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Tag-Rule-Configure.png)

 ![Tagregel geconfigureerd met tokens in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Tag-Rule-Tokens.png)

4.

Voeg een nieuwe [TextButton](/docs/nl-nl/reference/engine/classes/TextButton)  in de [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  die je eerder [hebt gemaakt en gelinkt](#ontwerpsheets)  en [tag](/docs/nl-nl/studio/properties#instantie-tags)  deze als ButtonPrimary . Een handige snelkoppeling is als volgt:

1.

Zorg ervoor dat de nieuwe [TextButton](/docs/nl-nl/reference/engine/classes/TextButton)  is geselecteerd in de [Explorer](/docs/nl-nl/studio/explorer) .

2.

Met de .ButtonPrimary  tagregel geselecteerd in de linkerkolom van de Stijl Editor, klik je op Pas Tag toe  in het hoofdvenster. De stijlen die je hebt gedefinieerd, zouden automatisch op de knop moeten worden toegepast.

![Tag koppelworkflow in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Tag-Rule-Apply-Tag.png)

 ![Eind gestylede tagregel in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Tag-Rule-Result.png)

### [UI modifier](#ui-modifier)[](#ui-modifier)

Instantie modifier selectors passen phantom [UIComponents](/docs/nl-nl/reference/engine/classes/UIComponent)  zoals [UICorner](/docs/nl-nl/reference/engine/classes/UICorner)  of [UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke)  toe om een object verder te stylen. De volgende regelopstelling stijlt een [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel)  met een aangepaste tekstgrootte en afgeronde hoeken.

1.

In de linkerkolom van de Stijl Editor, selecteer TextLabel  in de UI Elementen -tak.

 ![Standaard klasse stijl in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Modifier-Rule-New-Class.png)

2.

Koppel een eerder gemaakt [stijl token](#stijl-tokens)  aan de [TextSize](/docs/nl-nl/reference/engine/classes/TextLabel#TextSize) -eigenschap:

1.

Klik op Voeg een Eigenschap toe…  in het hoofdvenster en selecteer de [TextSize](/docs/nl-nl/reference/engine/classes/TextLabel#TextSize) -eigenschap. Vergeet niet dat je trefwoorden kunt typen om sneller eigenschappen in het dropdownmenu te vinden.

2.

In plaats van een statische waarde in te voeren, klik je op de ⋮ -knop en selecteer je Koppel Token .

3.

Klik op de $  die in het waardeveld verschijnt en selecteer de $Text32  token.

![Token koppelworkflow in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Modifier-Rule-Configure.png)

 ![Klasse regel geconfigureerd met tokens in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Modifier-Rule-Tokens.png)

Een pseudo-instantie  is vereist om afgeronde hoeken te configureren en toe te passen op andere elementen. Om er een te maken:

1.

In de linkerkolom, beweeg de muis over TextLabel , klik op de ⋮ -knop en navigeer naar Nieuw  ⟩ Pseudo Instantie  ⟩ UICorner .

 ![Creatie van een pseudo-instantie in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Modifier-Rule-Pseudo-Instance-New.png)

Een nieuwe UICorner  pseudo-instantie verschijnt onder het TextLabel -element in de linkerkolom.

 ![Resultaat van de pseudo-instantie in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Modifier-Rule-Pseudo-Instance-Created.png)

2.

Met de nieuwe UICorner -instantie geselecteerd in de linkerkolom, koppel een eerder gemaakt [stijl token](#stijl-tokens)  aan de [CornerRadius](/docs/nl-nl/reference/engine/classes/UICorner#CornerRadius) -eigenschap:

1.

Klik op Voeg een Eigenschap toe…  in het hoofdvenster en selecteer de [CornerRadius](/docs/nl-nl/reference/engine/classes/UICorner#CornerRadius) -eigenschap.

2.

In plaats van een statische waarde in te voeren, klik je op de ⋮ -knop en selecteer je Koppel Token .

3.

Klik op de $  die in het waardeveld verschijnt en selecteer de $Rad20  token.

 ![Pseudo-instantie geconfigureerd met tokens in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Modifier-Rule-Pseudo-Instance-Tokens.png)

3.

Voeg een nieuwe [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel)  in de [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  die je eerder [hebt gemaakt en gelinkt](#ontwerpsheets) . De stijlen die je hebt gedefinieerd, zouden automatisch op deze moeten worden toegepast.

 ![Eind gestylede modifierregel in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Modifier-Rule-Result.png)

### [Staat regel](#staat-regel)[](#staat-regel)

[GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  staat  selectors komen overeen met een van de vier [GuiState](/docs/nl-nl/reference/engine/enums/GuiState)  enum-waarden zoals [Hover](/docs/nl-nl/reference/engine/enums/GuiState) , waardoor je automatisch stijlwijzigingen voor interactieve staten kunt configureren. De volgende regelopstelling creëert een hoverstaat van -4  graden rotatie voor alle [ImageButtons](/docs/nl-nl/reference/engine/classes/ImageButton) .

1.

In de linkerkolom van de Stijl Editor, selecteer ImageButton  in de UI Elementen -tak.

 ![Standaard klasse stijl in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-State-Rule-New-Class.png)

2.

Klik op de ⋮ -knop en navigeer naar Nieuw  ⟩ GuiState  ⟩ Hover .

 ![Creatie van staatregel in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-State-Rule-New.png)

Een nieuwe Hover  staat modifier-instantie verschijnt onder het ImageButton -element in de linkerkolom.

 ![Resultaat van de staatregel in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-State-Rule-Created.png)

3.

Met de nieuwe Hover  modifier geselecteerd in de linkerkolom, klik op Voeg een Eigenschap toe…  in het hoofdvenster en selecteer [Rotation](/docs/nl-nl/reference/engine/classes/ImageButton#Rotation) . Vergeet niet dat je trefwoorden kunt typen om sneller eigenschappen in het dropdownmenu te vinden.

4.

Voer -4  in het waardeveld van de eigenschap in.

 ![Staatregel geconfigureerd met tokens in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-State-Rule-Tokens.png)

5.

Voeg een nieuwe [ImageButton](/docs/nl-nl/reference/engine/classes/ImageButton)  in de [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  die je eerder [hebt gemaakt en gelinkt](#ontwerpsheets) . Wanneer je over de knop in de viewport beweegt, zou deze 4 graden tegen de klok in moeten draaien.

 ![Eind gestylede staatregel in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-State-Rule-Result.png)

## [Stijl queries](#stijl-queries)[](#stijl-queries)

Stijl queries , vergelijkbaar met [CSS-container- en mediaqueries](/docs/nl-nl/ui/styling/css-comparisons#queries) , stellen je in staat om voorwaardelijke logica op je UI toe te passen op basis van de grootte van de container, het invoertype of andere factoren. De Stijl Editor biedt een gestroomlijnde workflow om zowel de querylogica (voorwaarden) als de resulterende stijlen als een uniforme set te creëren.

### [Ingebouwde queries](#ingebouwde-queries)[](#ingebouwde-queries)

Sommige [StyleQuery](/docs/nl-nl/reference/engine/classes/StyleQuery) -voorwaarden zijn zeer gebruikelijk, zoals het wijzigen van eigenschappen op basis van de [ViewportDisplaySize](/docs/nl-nl/reference/engine/classes/GuiService#ViewportDisplaySize) . Om dit te vereenvoudigen, bevat de Stijl Editor ingebouwde  queries waarmee je voorwaardelijke regels kunt maken zonder dat je een pseudo- of echte instantie van een [StyleQuery](/docs/nl-nl/reference/engine/classes/StyleQuery)  nodig hebt; in plaats daarvan gebruik je eenvoudig een queryregel met een vooraf gedefinieerde selector zoals ViewportDisplaySizeSmall .

De volgende stappen demonstreren hoe je ingebouwde queries voor een [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel)  kunt genereren om om te gaan met [Small](/docs/nl-nl/reference/engine/enums/DisplaySize#Small) , [Medium](/docs/nl-nl/reference/engine/enums/DisplaySize#Medium) , en [Large](/docs/nl-nl/reference/engine/enums/DisplaySize#Large)  viewportgroottes.

1.

In de linkerkolom van de Stijl Editor, beweeg de muis over TextLabel , klik op de ⋮ -knop en navigeer naar Nieuw  ⟩ StyleQuery  ⟩ Builtin  ⟩ ViewportDisplaySize .

 ![Creatie van een ingebouwde StyleQuery in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Query-New-Builtin.png)

Dit creëert een Queries -map onder de TextLabel -regel met drie queryregels:

-

@ViewportDisplaySizeLarge  — Definieer eigenschappen die van toepassing zijn wanneer de viewport [Large](/docs/nl-nl/reference/engine/enums/DisplaySize#Large)  is.

-

@ViewportDisplaySizeMedium  — Definieer eigenschappen die van toepassing zijn wanneer de viewport [Medium](/docs/nl-nl/reference/engine/enums/DisplaySize#Medium)  is.

-

@ViewportDisplaySizeSmall  — Definieer eigenschappen die van toepassing zijn wanneer de viewport [Small](/docs/nl-nl/reference/engine/enums/DisplaySize#Small)  is.

 ![Hiërarchie van een StyleQuery binnen een klasse regel.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Query-Builtin-Hierarchy.png)

2.

Klik op Voeg een Eigenschap toe…  onder elke queryregel en stel de specifieke [Text](/docs/nl-nl/reference/engine/classes/TextLabel#Text) -string in die moet worden weergegeven wanneer die query actief is:

| Query Regel | | Eigenschap | | Waarde |
| @ViewportDisplaySizeLarge | | [Text](/docs/nl-nl/reference/engine/classes/TextLabel#Text) | | Grote Tekst |
| @ViewportDisplaySizeMedium | | [Text](/docs/nl-nl/reference/engine/classes/TextLabel#Text) | | Gemiddelde Tekst |
| @ViewportDisplaySizeSmall | | [Text](/docs/nl-nl/reference/engine/classes/TextLabel#Text) | | Kleine Tekst |

3.

Om de queries te verifiëren, gebruik de [Apparaatemulator](/docs/nl-nl/studio/testing-modes#device-emulation)  om te testen hoe de UI reageert op verschillende resoluties op drie verschillende apparaten:

1.

Voeg een nieuwe [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel)  in de [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui) .

2.

Wijzig het Apparaat  in de [Apparaatemulator](/docs/nl-nl/studio/testing-modes#device-emulation)  om de tekst in realtime te zien veranderen.

| Grootte | | Voorbeeld Emulaties |
| [Large](/docs/nl-nl/reference/engine/enums/DisplaySize#Large) | | PS5 , PS4 , Xbox One |
| [Medium](/docs/nl-nl/reference/engine/enums/DisplaySize#Medium) | | Gemiddelde Laptop , HD 720 |
| [Small](/docs/nl-nl/reference/engine/enums/DisplaySize#Small) | | iPhone XR , iPad 7e Generatie |

### [Aangepaste query](#aangepaste-query)[](#aangepaste-query)

Je kunt een stijlquery aan elke bestaande regel toevoegen om responsieve UI te creëren die zich aanpast aan zijn container. De volgende opstelling configureert een [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel)  om automatisch zijn uiterlijk te veranderen wanneer het zich uitbreidt tot een breedte van 400 pixels of meer.

1.

In de linkerkolom van de Stijl Editor, beweeg de muis over TextLabel , klik op de ⋮ -knop en navigeer naar Nieuw  ⟩ StyleQuery  ⟩ Aangepast .

 ![Creatie van een aangepaste StyleQuery in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Query-New-Custom.png)

Deze actie creëert een Queries -map onder de TextLabel -regel met twee gekoppelde items:

-

::StyleQuery  pseudo-instantie regel waar je de Voorwaarden  definieert.

-

@StyleQuery  regel waar je de Eigenschappen  definieert die moeten worden toegepast wanneer aan die voorwaarden is voldaan.

 ![Hiërarchie van een StyleQuery binnen een klasse regel.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Query-Custom-Hierarchy.png)

2.

Selecteer de bovenliggende TextLabel -regel in het hoofdvenster en definieer de volgende standaard eigenschappen:

| Eigenschap | | Waarde |
| [BackgroundColor3](/docs/nl-nl/reference/engine/classes/TextLabel#BackgroundColor3) | | $Magenta |
| [Text](/docs/nl-nl/reference/engine/classes/TextLabel#Text) | | Standaard Tekst |

3.

Selecteer de ::StyleQuery -regel in het hoofdvenster, klik op Voeg een Voorwaarde toe… , en configureer het volgende:

| Voorwaarde | | Waarde |
| MinSize | | 400, 0 |

Zie [StyleQuery.IsActive](/docs/nl-nl/reference/engine/classes/StyleQuery#IsActive)  als referentie voor andere voorwaarden die beschikbaar zijn via de ::StyleQuery -regel.

4.

Selecteer de @StyleQuery -regel in het hoofdvenster en stel de eigenschappen in die moeten worden toegepast wanneer de query actief is:

| Eigenschap | | Waarde |
| [BackgroundColor3](/docs/nl-nl/reference/engine/classes/TextLabel#BackgroundColor3) | | $Gold |
| [Text](/docs/nl-nl/reference/engine/classes/TextLabel#Text) | | Grote Tekst |

Om de query te verifiëren, kun je handmatig een [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel)  in de viewport aanpassen.

1.

Voeg een nieuwe [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel)  in de [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui) .

2.

Pas de breedte aan om de stijl in realtime te zien wisselen.

0–400 Pixel Breedte Meer dan 400 Pixel Breedte

Terwijl de breedte van de [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel)  kleiner is, wordt de MinSize -voorwaarde niet voldaan en gebruikt het label zijn standaard achtergrondkleur en tekst.

![TextLabel verschijnt magenta met 'Standaard Tekst' op een telefoonviewport.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Query-Test-Small.png)

Hoewel handmatig aanpassen een snelle manier is om responsieve logica te controleren, kun je ook de ingebouwde emulatietools van Studio gebruiken voor nauwkeurigere tests:

-

Gebruik de [Apparaatemulator](/docs/nl-nl/studio/testing-modes#device-emulation)  om te testen hoe je UI reageert op specifieke schermresoluties en [ViewportDisplaySize](/docs/nl-nl/reference/engine/classes/GuiService#ViewportDisplaySize) -voorwaarden.

-

Gebruik de [Controller Emulator](/docs/nl-nl/studio/testing-modes#controller-simulation)  om de [PreferredInput](/docs/nl-nl/reference/engine/classes/UserInputService#PreferredInput) -logica te verifiëren, zoals het wisselen van stijlen wanneer een gamepad wordt gedetecteerd.

## [Stijl overgangen](#stijl-overgangen)[](#stijl-overgangen)

Stijl overgangen , vergelijkbaar met [CSS-overgangen](/docs/nl-nl/ui/styling/css-comparisons#overgangen) , laten je eigenschapswaarden over een bepaalde duur tweenen.

### [Standaard](#standaard)[](#standaard)

Om veel UI-eigenschappen met dezelfde parameters te tweenen, kun je een standaardovergang instellen die van toepassing is op alle  eigenschappen, tenzij een andere overgang expliciet is ingesteld voor een specifieke eigenschap.

1.

Selecteer TextButton  in de UI Elementen -tak en voeg vervolgens in het hoofdvenster drie nieuwe eigenschappen toe met de volgende waarden:

| Eigenschap | | Waarde |
| [AutoButtonColor](/docs/nl-nl/reference/engine/classes/TextButton#AutoButtonColor) | | false |
| [BackgroundColor3](/docs/nl-nl/reference/engine/classes/TextButton#BackgroundColor3) | | #335FFF |
| [Rotation](/docs/nl-nl/reference/engine/classes/TextButton#Rotation) | | 0 |

 ![Klasse stijl in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-New-Class.png)

2.

Beweeg de muis over de bovenliggende TextButton -rij, klik op de ⋮-knop en navigeer naar Voeg toe  ⟩ Overgang .

 ![Voeg standaardovergang toe aan een regel in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-Add-Default-Transition.png)

Een standaardovergang van 1, Quad, Out, 0  wordt direct onder de TextButton -regel ingevoegd, wat een overgang van 1 seconde aangeeft, easing-stijl [Quad](/docs/nl-nl/reference/engine/enums/EasingStyle#Quad) , easing-richting [Out](/docs/nl-nl/reference/engine/enums/EasingDirection#Out) , en geen vertraging.

 ![Standaardovergang gemarkeerd in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-Default-Transition-Added.png)

3.

Beweeg de muis over de bovenliggende TextButton -rij, klik op de ⋮ -knop en navigeer naar Nieuw  ⟩ GuiState  ⟩ Hover .

 ![Creatie van staatregel in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-Default-New-State.png)

4.

Voor de nieuwe Hover -modifier, voeg je twee nieuwe eigenschappen toe als de doelen  voor de hoverstaat.

| Eigenschap | | Waarde |
| [BackgroundColor3](/docs/nl-nl/reference/engine/classes/TextButton#BackgroundColor3) | | #33AAFF |
| [Rotation](/docs/nl-nl/reference/engine/classes/TextButton#Rotation) | | -5 |

 ![Eigenschappen op hoverstaatregel in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-State-Properties.png)

5.

Voeg een nieuwe [TextButton](/docs/nl-nl/reference/engine/classes/TextButton)  in de [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  die je eerder [hebt gemaakt en gelinkt](#ontwerpsheets) . Wanneer je over de knop in de viewport beweegt, zou deze geleidelijk moeten oplichten en 5 graden tegen de klok in moeten draaien.

 ![Eind gestylede staatregel in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-Result.png)

### [Token-gekoppeld](#token-gekoppeld)[](#token-gekoppeld)

Om overgangsgedragingen over meerdere regels te hergebruiken, kun je tokens  definiëren die het [TweenInfo](/docs/nl-nl/reference/engine/datatypes/TweenInfo) -gegevenstype vertegenwoordigen. De volgende regelopstelling creëert een hoverstaat om alle [TextButtons](/docs/nl-nl/reference/engine/classes/TextButton)  naar/van -5 graden rotatie en een lichtere achtergrondkleur te laten overgaan.

1.

Als je dat nog niet hebt gedaan, maak een [tokenstijlblad](#stijl-tokens)  genaamd TokenSheet .

 ![Nieuw tokenblad gemaakt in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-TokenSheet-New.png)

2.

Met het nieuwe tokenblad geselecteerd, maak je twee nieuwe tokens door op Voeg een Token toe…  in het hoofdvenster te klikken.

| Token Naam | | Type | | Tween Parameters |
| CubicOut | | [TweenInfo](/docs/nl-nl/reference/engine/datatypes/TweenInfo) | |
-

Duur  = 1.25

-

EasingStyle  = Cubic

-

EasingDirection  = Out

-

Vertraging  = 0

 |
| QuadInOut | | [TweenInfo](/docs/nl-nl/reference/engine/datatypes/TweenInfo) | |
-

Duur  = 0.5

-

EasingStyle  = Quad

-

EasingDirection  = InOut

-

Vertraging  = 0

 |

 ![Tokens toegevoegd aan TokenSheet in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-Tokens-Defined.png)

3.

Selecteer TextButton  in de UI Elementen -tak en voeg vervolgens in het hoofdvenster drie nieuwe eigenschappen toe met de volgende waarden:

| Eigenschap | | Waarde |
| [AutoButtonColor](/docs/nl-nl/reference/engine/classes/TextButton#AutoButtonColor) | | false |
| [BackgroundColor3](/docs/nl-nl/reference/engine/classes/TextButton#BackgroundColor3) | | #335FFF |
| [Rotation](/docs/nl-nl/reference/engine/classes/TextButton#Rotation) | | 0 |

 ![Klasse stijl in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-New-Class.png)

4.

Voor elke nieuwe eigenschap, behalve [AutoButtonColor](/docs/nl-nl/reference/engine/classes/TextButton#AutoButtonColor) , beweeg je de muis over de rij, klik je op de ⋮ -knop en selecteer je Voeg toe  ⟩ Overgang .

 ![Voeg overgang toe aan een eigenschap in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-Add-Transition.png)

5.

Beweeg de muis over de nieuwe Overgang -rij onder elke eigenschap, klik op de ⋮ -knop en selecteer Koppel Token . Klik vervolgens in plaats van een statische waarde in te voeren op de $  die in het waardeveld verschijnt en selecteer de juiste overgangstoken.

 ![Token koppelworkflow in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-Tokens-Link.png)

| Eigenschap Overgang | | Overgang Token |
| [BackgroundColor3](/docs/nl-nl/reference/engine/classes/TextButton#BackgroundColor3) | | $CubicOut |
| [Size](/docs/nl-nl/reference/engine/classes/TextButton#Size) | | $QuadInOut |

 ![Overgangstokens gekoppeld in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-Tokens-Linked.png)

6.

Beweeg de muis over de bovenliggende TextButton -rij, klik op de ⋮ -knop en navigeer naar Nieuw  ⟩ GuiState  ⟩ Hover .

 ![Creatie van staatregel in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-New-State.png)

7.

Voor de nieuwe Hover -modifier, voeg je twee nieuwe eigenschappen toe als de doelen  voor de hoverstaat.

| Eigenschap | | Waarde |
| [BackgroundColor3](/docs/nl-nl/reference/engine/classes/TextButton#BackgroundColor3) | | #33AAFF |
| [Rotation](/docs/nl-nl/reference/engine/classes/TextButton#Rotation) | | -5 |

 ![Eigenschappen op hoverstaatregel in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-State-Properties.png)

8.

Voeg een nieuwe [TextButton](/docs/nl-nl/reference/engine/classes/TextButton)  in de [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  die je eerder [hebt gemaakt en gelinkt](#ontwerpsheets) . Wanneer je over de knop in de viewport beweegt, zou deze geleidelijk moeten oplichten en 5 graden tegen de klok in moeten draaien.

 ![Eind gestylede staatregel in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-Result.png)

## [Stijl thema's](#stijl-themas)[](#stijl-themas)

Stijl thema's  bestaan uit sets van specifieke tokens die kunnen worden gewisseld, bijvoorbeeld kleur tokens die een "lichte" en "donkere" thema definiëren.

### [Thema creatie](#thema-creatie)[](#thema-creatie)

Voor uitbreidbaarheid zijn thema's georganiseerd in mappen. Terwijl een enkele map voldoende kan zijn voor de meeste doeleinden, ben je vrij om thema's in mappen zoals "kleuren" of "lettertypen" te organiseren als dat gewenst is.

1.

Maak een nieuwe themamap:

1.

In de linkerkolom van de Stijl Editor, beweeg de muis over Thema's , klik op de ⊕ , en selecteer Nieuwe Thema .

2.

Hernoem het nieuwe Map -item naar Algemeen .

 ![Nieuwe themamap gemaakt in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Themes-New-Folder.png)

2.

Maak een nieuw themastijlblad:

1.

Beweeg de muis over de nieuwe Algemeen -map, klik op de ⋮ -knop en selecteer Nieuwe Thema StijlSheet .

2.

Hernoem het naar ThemaA .

 ![Nieuw thema gemaakt in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Themes-New-Theme.png)

### [Thema tokens](#thema-tokens)[](#thema-tokens)

Zodra een thema is geconstrueerd, kun je de tokens koppelen aan verschillende UI-objecteigenschappen zoals de [BackgroundColor3](/docs/nl-nl/reference/engine/classes/TextButton#BackgroundColor3)  van een [TextButton](/docs/nl-nl/reference/engine/classes/TextButton) . Themasheets moeten een gemeenschappelijke set tokens gebruiken om correct te functioneren.

Met ThemaA  geselecteerd in de linkerkolom van de Stijl Editor:

1.

Koppel drie eerder gemaakte [stijl tokens](#stijl-tokens)  aan drie nieuwe thematokens:

| Thema Token | | Stijl Token |
| AchtergrondKleur | | $Gold |
| KnopLettertype | | $Oswald |
| KnopTekstGrootte | | $Text32 |

1.

Klik op Voeg een Token toe…  in het hoofdvenster en voer de naam van het thematoken in.

2.

Klik op de $  die in het waardeveld verschijnt en selecteer de bijbehorende stijl token.

 ![Thema geconfigureerd met tokens in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Themes-ThemeA-Tokens.png)

2.

In de linkerkolom van de Stijl Editor, selecteer TextButton  in de UI Elementen -tak.

 ![Standaard klasse stijl in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Themes-New-Class.png)

3.

Koppel de tokens van het thema aan drie nieuwe [TextButton](/docs/nl-nl/reference/engine/classes/TextButton) -eigenschappen:

| Eigenschap | | Thema Token |
| [BackgroundColor3](/docs/nl-nl/reference/engine/classes/TextButton#BackgroundColor3) | | $AchtergrondKleur |
| [FontFace](/docs/nl-nl/reference/engine/classes/TextButton#FontFace) | | $KnopLettertype |
| [TextSize](/docs/nl-nl/reference/engine/classes/TextButton#TextSize) | | $KnopTekstGrootte |

1.

Klik op Voeg een Eigenschap toe…  in het hoofdvenster en selecteer de benodigde eigenschap.

2.

In plaats van een statische waarde in te voeren, klik je op de ⋮ -knop en selecteer je Koppel Token .

3.

Klik op de $  die in het waardeveld verschijnt en selecteer de juiste thematoken.

![Token koppelworkflow in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Themes-Theme-Configure.png)

Wanneer je de tokens van het thema koppelt, zoek dan naar $[Token] in ThemaA  in de hover-over om te weten dat de token afkomstig is van het thema  en niet van het globale tokenblad (vergeet niet dat het thema al de globale tokens afleidt).

 ![Klasse regel geconfigureerd met thematokens in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Themes-Class-Tokens.png)

### [Thema duplicatie](#thema-duplicatie)[](#thema-duplicatie)

Zodra je een thema algemeen hebt vastgesteld, kun je het dupliceren  en verschillende tokens wijzigen om een unieke themastijl te definiëren.

1.

In de linkerkolom van de Stijl Editor, beweeg de muis over het ThemaA -thema, klik op de ⋮ -knop en selecteer Dupliceer .

2.

Hernoem het gedupliceerde thema naar ThemaB .

 ![Thema gedupliceerd in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Themes-Duplicated-Theme.png)

3.

Koppel twee van de thematokens aan twee verschillende stijl tokens:

| Thema Token | | Stijl Token |
| AchtergrondKleur | | $Magenta |
| KnopTekstGrootte | | $Text24 |

1.

Klik rechts van het waardeveld van de eigenschap op de ⋮ -knop en selecteer Koppel Token los .

2.

Klik opnieuw op ⋮  en selecteer Koppel Token .

3.

Klik in het waardeveld op de $  en selecteer de nieuwe bijbehorende stijl token.

 ![Thema geconfigureerd met tokens in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Themes-ThemeB-Tokens.png)

### [Thema wisselen](#thema-wisselen)[](#thema-wisselen)

Zodra je [meerdere thema's](#thema-duplicatie)  hebt, kun je tussen hen wisselen via de themamap, of via een script zoals uiteengezet in [SetDerives()](/docs/nl-nl/reference/engine/classes/StyleSheet#SetDerives) .

1.

In de linkerkolom van de Stijl Editor, selecteer de Algemeen -map in de Thema's -tak.

2.

In het hoofdvenster, wissel tussen de thema's met de keuzerondjes.

ThemaA ThemaB

![ThemaA gewisseld in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Themes-Swapping-ThemeA.png)![](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Themes-ThemeA-Result.png)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
