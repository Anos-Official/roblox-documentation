<!-- Source: https://create.roblox.com/docs/nl-nl/ui/size-modifiers -->

Grootte-modifiers en beperkingen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Gebruikersinterface](/docs/nl-nl/ui)

# Grootte-modifiers en beperkingen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Naast de basis [grootte](/docs/nl-nl/ui/position-and-size)  van UI-objecten, kun je grootte-modifiers gebruiken om een object proportioneel te [schalen](#schalen)  of het [automatisch te laten aanpassen](#automatische-sizing) . Je kunt ook [groottebeperkingen](#beperkingen)  invoegen om de aspectverhouding  te controleren, of om een minimum en maximum grootte  of tekstgrootte  in te stellen.

## [Schalen](#schalen)[](#schalen)

Een [UIScale](/docs/nl-nl/reference/engine/classes/UIScale)  object slaat een numerieke waarde op die de [AbsoluteSize](/docs/nl-nl/reference/engine/classes/GuiBase2d#AbsoluteSize)  eigenschap van het bovenliggende [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  vermenigvuldigt. Bijvoorbeeld, als je wilt dat een object twee keer zo groot is als het momenteel is, kun je een [UIScale](/docs/nl-nl/reference/engine/classes/UIScale)  object invoegen met een [Scale](/docs/nl-nl/reference/engine/classes/UIScale#Scale)  eigenschap van 2 .

Deze modifier is nuttig voor het "inzoomen" tijdens het ontwerpen van een gedetailleerde gebruikersinterface in Studio, omdat het het object en al zijn kinderen proportioneel schaalt, inclusief eventuele toegepaste [verschijning-modifiers](/docs/nl-nl/ui/appearance-modifiers)  zoals [UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke)  of [UICorner](/docs/nl-nl/reference/engine/classes/UICorner) . Het is ook nuttig om de grootte van een object te [tweeneren](/docs/nl-nl/ui/animation) , bijvoorbeeld om de grootte van een knop iets te vergroten wanneer een speler zijn muis eroverheen beweegt.

 ![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIScale-Example.png)

## [Automatische sizing](#automatische-sizing)[](#automatische-sizing)

De [AutomaticSize](/docs/nl-nl/reference/engine/classes/GuiObject#AutomaticSize)  eigenschap past automatisch de grootte van een bovenliggend [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  aan op basis van de grootte van zijn afgeleiden. Je kunt deze eigenschap in verschillende gevallen gebruiken, waaronder:

-

Het uitbreiden van een [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  om tekst die in veel talen is [gelokaliseerd](/docs/nl-nl/production/localization)  te passen.

-

Gebruikers toestaan om [tekst in te voeren](/docs/nl-nl/ui/text-input)  binnen een [TextBox](/docs/nl-nl/reference/engine/classes/TextBox) , waarbij de grootte automatisch wordt aangepast op basis van de hoeveelheid ingevoerde tekst.

-

De grootte van tekstobjecten automatisch aanpassen met behulp van [rijke tekstmarkup](/docs/nl-nl/ui/rich-text) , inclusief lettertype en grootte.

Je kunt de [AutomaticSize](/docs/nl-nl/reference/engine/classes/GuiObject#AutomaticSize)  eigenschap inschakelen voor elk [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject) . Standaard is deze ingesteld op [None](/docs/nl-nl/reference/engine/enums/AutomaticSize) , maar je kunt de waarde wijzigen om specifieke controle te hebben over welke richting(en) het [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  zich aanpast om zijn inhoud te passen.

[ScrollingFrame](/docs/nl-nl/reference/engine/classes/ScrollingFrame)  gebruikt de [AutomaticCanvasSize](/docs/nl-nl/reference/engine/classes/ScrollingFrame#AutomaticCanvasSize)  eigenschap in plaats van [AutomaticSize](/docs/nl-nl/reference/engine/classes/GuiObject#AutomaticSize) . Het gedraagt zich hetzelfde, maar past de [CanvasSize](/docs/nl-nl/reference/engine/classes/ScrollingFrame#CanvasSize)  van het frame aan, niet de basis [Size](/docs/nl-nl/reference/engine/classes/GuiObject#Size) .

Om automatische sizing in te schakelen:

1.

Klik in het [Explorer](/docs/nl-nl/studio/explorer)  venster op een willekeurig [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject) , zoals een [Frame](/docs/nl-nl/reference/engine/classes/Frame) , [TextBox](/docs/nl-nl/reference/engine/classes/TextBox) , of [ImageLabel](/docs/nl-nl/reference/engine/classes/ImageLabel) .

2.

Navigeer in het [Properties](/docs/nl-nl/studio/properties)  venster naar de [AutomaticSize](/docs/nl-nl/reference/engine/classes/GuiObject#AutomaticSize)  eigenschap ([AutomaticCanvasSize](/docs/nl-nl/reference/engine/classes/ScrollingFrame#AutomaticCanvasSize)  voor [ScrollingFrame](/docs/nl-nl/reference/engine/classes/ScrollingFrame) ) en stel deze in op een van de volgende opties:

-

[X](/docs/nl-nl/reference/engine/enums/AutomaticSize)  — Past de inhoud horizontaal aan.

-

[Y](/docs/nl-nl/reference/engine/enums/AutomaticSize)  — Past de inhoud verticaal aan.

-

[XY](/docs/nl-nl/reference/engine/enums/AutomaticSize)  — Past de inhoud zowel horizontaal als verticaal aan.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/GuiObject-AutomaticSize.png)

Zodra automatische sizing is ingesteld, let op dat andere objecteigenschappen als volgt werken:

AnchorPoint Grootte TextWrapped

Vergelijkbaar met het concept van [grootte](/docs/nl-nl/ui/position-and-size#grootte)  van een object, houdt [AutomaticSize](/docs/nl-nl/reference/engine/classes/GuiObject#AutomaticSize)  rekening met de [AnchorPoint](/docs/nl-nl/reference/engine/classes/GuiObject#AnchorPoint)  eigenschap bij het aanpassen van de inhoud. Bijvoorbeeld, de volgende video toont drie [TextLabels](/docs/nl-nl/reference/engine/classes/TextLabel)  die automatisch worden aangepast vanaf hun ankerpunt.

-

Het bovenste label heeft een [AnchorPoint](/docs/nl-nl/reference/engine/classes/GuiObject#AnchorPoint)  waarde van [(0, 0.5)](/docs/nl-nl/reference/engine/datatypes/Vector2#new)  wat het aan de middelste van de linkerkant verankert.

-

Het middelste label heeft een [AnchorPoint](/docs/nl-nl/reference/engine/classes/GuiObject#AnchorPoint)  waarde van [(0.5, 0.5)](/docs/nl-nl/reference/engine/datatypes/Vector2#new)  wat het in het midden verankert.

-

Het onderste label heeft een [AnchorPoint](/docs/nl-nl/reference/engine/classes/GuiObject#AnchorPoint)  waarde van [(1, 0.5)](/docs/nl-nl/reference/engine/datatypes/Vector2#new)  wat het aan de middelste van de rechterkant verankert.

## [Beperkingen](#beperkingen)[](#beperkingen)

Er zijn drie soorten beperkingen  die je kunt gebruiken voor een gebruikersinterface-object: [grootte](#grootte) , [tekstgrootte](#tekstgrootte) , en [aspect verhouding](#aspectverhouding) . Om een beperking te gebruiken, moet je deze instellen als een kind  van het [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  dat je wilt beperken.

### [Grootte](#grootte)[](#grootte)

De [UISizeConstraint](/docs/nl-nl/reference/engine/classes/UISizeConstraint)  specificeert een minimum en maximum grootte voor een [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject) . Deze beperking zorgt ervoor dat het [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  niet te klein of te groot wordt op verschillende schermformaten.

Bijvoorbeeld, als je de [MinSize](/docs/nl-nl/reference/engine/classes/UISizeConstraint#MinSize)  eigenschap instelt op (200, 200)  en de [MaxSize](/docs/nl-nl/reference/engine/classes/UISizeConstraint#MaxSize)  eigenschap op (400, 400) , kan het [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  niet kleiner schalen dan 200×200 pixels of groter dan 400×400 pixels.

Wanneer een UI-object onder controle staat van zowel een lay-outstructuur zoals [UIListLayout](/docs/nl-nl/reference/engine/classes/UIListLayout)  als een [UISizeConstraint](/docs/nl-nl/reference/engine/classes/UISizeConstraint) , zal de beperking de lay-out overschrijven  en de grootte van het object controleren.

### [Tekstgrootte](#tekstgrootte)[](#tekstgrootte)

De [UITextSizeConstraint](/docs/nl-nl/reference/engine/classes/UITextSizeConstraint)  specificeert een minimum en maximum lettergrootte voor een [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  met tekst, zoals een [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel) , [TextButton](/docs/nl-nl/reference/engine/classes/TextButton) , of [TextBox](/docs/nl-nl/reference/engine/classes/TextBox) . Deze beperking zorgt ervoor dat de tekst  binnen een [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  niet onleesbaar of te groot wordt.

Als je de [TextScaled](/docs/nl-nl/reference/engine/classes/TextLabel#TextScaled)  eigenschap van het bovenliggende [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  inschakelt, schaalt de tekstgrootte mee met de grootte van de container en respecteert het beperkingen, zelfs als het object kleiner of groter wordt dan de [MinTextSize](/docs/nl-nl/reference/engine/classes/UITextSizeConstraint#MinTextSize)  en [MaxTextSize](/docs/nl-nl/reference/engine/classes/UITextSizeConstraint#MaxTextSize)  waarden.

Bijvoorbeeld, het volgende [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel)  object heeft een [UITextSizeConstraint](/docs/nl-nl/reference/engine/classes/UITextSizeConstraint)  met een [MinTextSize](/docs/nl-nl/reference/engine/classes/UITextSizeConstraint#MinTextSize)  waarde van 50  en een MaxTextSize waarde van 80 . Zelfs wanneer de [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel)  kleiner wordt, wordt het lettertype nooit kleiner dan 50 pixels, en wanneer het object groot wordt, overschrijdt het lettertype nooit 80 pixels.

Gebruik geen [MinTextSize](/docs/nl-nl/reference/engine/classes/UITextSizeConstraint#MinTextSize)  eigenschap waarden lager dan 9  of de tekst zal moeilijk leesbaar zijn voor veel kijkers.

### [Aspectverhouding](#aspectverhouding)[](#aspectverhouding)

De [UIAspectRatioConstraint](/docs/nl-nl/reference/engine/classes/UIAspectRatioConstraint)  handhaaft een breedte‑tot‑hoogte  aspectverhouding op een [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject) , ongeacht de kernmaat, zelfs als die maat als een percentage van de bovenliggende is ingesteld. Bijvoorbeeld, deze beperking invoegen als een kind van een [Frame](/docs/nl-nl/reference/engine/classes/Frame)  en de [AspectRatio](/docs/nl-nl/reference/engine/classes/UIAspectRatioConstraint#AspectRatio)  eigenschap instellen op 2  (2:1 ) houdt de breedte van het frame op twee keer die van de hoogte. Evenzo, het instellen van deze beperking's [AspectRatio](/docs/nl-nl/reference/engine/classes/UIAspectRatioConstraint#AspectRatio)  eigenschap op 0.5  (0.5:1 ) houdt de breedte van het frame op de helft van die van de hoogte.

Het instellen van deze beperking's [AspectRatio](/docs/nl-nl/reference/engine/classes/UIAspectRatioConstraint#AspectRatio)  op de standaardwaarde van 1  (1:1 ) is een handige manier om niet-proportionele schaling/strekken van een [ImageLabel](/docs/nl-nl/reference/engine/classes/ImageLabel)  met een vierkante afbeeldingselement te voorkomen, zoals een [avatar-miniatuur](/docs/nl-nl/projects/assets#rbxthumb) .

Wanneer een UI-object onder controle staat van zowel een lay-outstructuur zoals [UIListLayout](/docs/nl-nl/reference/engine/classes/UIListLayout)  als een [UIAspectRatioConstraint](/docs/nl-nl/reference/engine/classes/UIAspectRatioConstraint) , zal de beperking de lay-out overschrijven  en de grootte van het object controleren.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
