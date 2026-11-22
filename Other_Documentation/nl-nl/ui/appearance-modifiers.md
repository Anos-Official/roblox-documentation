<!-- Source: https://create.roblox.com/docs/nl-nl/ui/appearance-modifiers -->

UI-uiterlijk modifiers | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Gebruikersinterface](/docs/nl-nl/ui)

# UI-uiterlijk modifiers

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Door gebruik te maken van uiterlijk modifiers  kun je het uiterlijk van je [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  verder aanpassen.

-

Pas een [verloop](#verloop)  toe op de achtergrond van een object.

-

Pas een [omtrek](#omtrek)  toe op tekst of een rand.

-

Stel [afgeronde hoeken](#hoeken)  in voor een object.

-

Verhoog de [padding](#padding)  tussen de randen van een object.

-

Voeg een [schaduw](#schaduw)  toe achter een object.

## [Verloop](#verloop)[](#verloop)

Het [UIGradient](/docs/nl-nl/reference/engine/classes/UIGradient)  object past een kleur- en transparantieverloop toe op zijn bovenliggende [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject) .

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Example.png)

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/UIGradient.png)

Je kunt het verloop configureren door:

-

De [kleuren](#kleurvolgorde)  in te stellen via een [ColorSequence](/docs/nl-nl/reference/engine/datatypes/ColorSequence)  in de [Color](/docs/nl-nl/reference/engine/classes/UIGradient#Color)  eigenschap van het verloop.

-

De [transparantie](#transparantie)  in te stellen via een [NumberSequence](/docs/nl-nl/reference/engine/datatypes/NumberSequence)  in de [Transparency](/docs/nl-nl/reference/engine/classes/UIGradient#Transparency)  eigenschap van het verloop.

-

Het [type](#type)  van het verloop te kiezen via de [Type](/docs/nl-nl/reference/engine/classes/UIGradient#Type)  eigenschap.

-

Het [startpunt](#offset-en-rotatie)  van het verloop te kiezen (binnen of buiten de grenzen van de bovenliggende) via de [Offset](/docs/nl-nl/reference/engine/classes/UIGradient#Offset)  eigenschap.

-

De [hoek](#offset-en-rotatie)  van het verloop te kiezen via de [Rotation](/docs/nl-nl/reference/engine/classes/UIGradient#Rotation)  eigenschap.

-

De [schaal](#schaal)  van het verloop te kiezen via de [Scale](/docs/nl-nl/reference/engine/classes/UIGradient#Scale)  eigenschap.

-

Het gedrag van de [randmonsters](#tegelmodus)  van het verloop te kiezen via de [TileMode](/docs/nl-nl/reference/engine/classes/UIGradient#TileMode)  eigenschap.

### [Kleurvolgorde](#kleurvolgorde)[](#kleurvolgorde)

Om de kleurvolgorde van een verloop in te stellen:

1.

Selecteer het [UIGradient](/docs/nl-nl/reference/engine/classes/UIGradient)  in het [Explorer](/docs/nl-nl/studio/explorer)  venster.

2.

Klik in het [Properties](/docs/nl-nl/studio/properties)  venster in het veld van de [Color](/docs/nl-nl/reference/engine/classes/UIGradient#Color)  eigenschap, en klik vervolgens op de ⋯  knop rechts van het invoerveld.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/UIGradient-Open-ColorSequence-Window.png)

3.

Elke driehoek op de onderste as van de kleurvolgorde is een sleutelpunt  dat de kleurwaarde op dat punt bepaalt.

 ![Kleurvolgorde popup van wit naar wit](https://prod.docsiteassets.roblox.com/assets/studio/general/ColorSequence-White-Keypoints-Labeled.png)

1.

Klik op een sleutelpunt in de kleurvolgorde om het te selecteren of opnieuw te positioneren, of voeg een ander sleutelpunt toe door ergens op de grafiek te klikken.

2.

Klik op het kleine vierkantje naast Kleur  om het Kleuren  pop-upvenster te openen, en selecteer vervolgens de gewenste kleur voor het sleutelpunt.

3.

Herhaal deze stappen indien nodig om kleuren over de grafiek toe te voegen/aan te passen.

### [Transparantie](#transparantie)[](#transparantie)

Om de transparantie van een verloop over zijn bereik aan te passen:

1.

Selecteer het [UIGradient](/docs/nl-nl/reference/engine/classes/UIGradient)  in het [Explorer](/docs/nl-nl/studio/explorer)  venster.

2.

Klik in het [Properties](/docs/nl-nl/studio/properties)  venster in het veld van de [Transparency](/docs/nl-nl/reference/engine/classes/UIGradient#Transparency)  eigenschap, en klik vervolgens op de ⋯  knop rechts van het invoerveld.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/UIGradient-Open-NumberSequence-Window.png)

3.

Elk vierkant over de getalvolgorde grafiek is een sleutelpunt  dat de transparantiewaarde op dat punt bepaalt.

 ![Sleutelpunten gelabeld in getalvolgorde popup](https://prod.docsiteassets.roblox.com/assets/studio/general/NumberSequence-0-0-Keypoints-Labeled.png)

1.

Klik op een sleutelpunt in de getalvolgorde om het te selecteren of opnieuw te positioneren, of voeg een ander sleutelpunt toe door ergens op de grafiek te klikken.

2.

Voer een specifieke tijd/waarde combinatie in via de Tijd  en Waarde  invoervelden.

3.

Herhaal deze stappen indien nodig om transparantieniveaus over de grafiek toe te voegen/aan te passen.

### [Type](#type)[](#type)

Deze verloopfunctie is momenteel in beta. Schakel het in via Bestand  ⟩ Bèta-functies  ⟩ Verbeterde UIGradients .

De [Type](/docs/nl-nl/reference/engine/classes/UIGradient#Type)  eigenschap van een verloop stelt het type in uit [Linear](/docs/nl-nl/reference/engine/enums/GradientType#Linear) , [Radial](/docs/nl-nl/reference/engine/enums/GradientType#Radial) , [Elliptical](/docs/nl-nl/reference/engine/enums/GradientType#Elliptical) , of [Conical](/docs/nl-nl/reference/engine/enums/GradientType#Conical) .

-

[Linear](/docs/nl-nl/reference/engine/enums/GradientType#Linear)  — De kleur/transparantievolgorde verandert in een rechte lijn over het element. De richting wordt gecontroleerd door zijn [rotatie](#offset-en-rotatie)  en de positie door zijn [offset](#offset-en-rotatie) . Dit is de standaardinstelling.

-

[Radial](/docs/nl-nl/reference/engine/enums/GradientType#Radial)  — De kleur/transparantievolgorde straalt naar buiten vanuit het midden van het element, optioneel verschoven door [Offset](/docs/nl-nl/reference/engine/classes/UIGradient#Offset) . De straal wordt gedefinieerd door het gemiddelde van de breedte en hoogte van het element gedeeld door twee, effectief (breedte+hoogte)/4 \text{(breedte+hoogte)/4} (breedte+hoogte)/4 . [Rotation](/docs/nl-nl/reference/engine/classes/UIGradient#Rotation)  heeft geen effect op een radiaal verloop.

-

[Elliptical](/docs/nl-nl/reference/engine/enums/GradientType#Elliptical)  — De kleur/transparantievolgorde straalt naar buiten vanuit het midden van het element in een ellips, optioneel verschoven door [Offset](/docs/nl-nl/reference/engine/classes/UIGradient#Offset) . De horizontale en verticale stralen van de ellips zijn de helft van de breedte en hoogte van het element, zodat de ellips in de grenzen van het element past. [Rotation](/docs/nl-nl/reference/engine/classes/UIGradient#Rotation)  roteert de assen van de ellips.

-

[Conical](/docs/nl-nl/reference/engine/enums/GradientType#Conical)  — De kleur/transparantievolgorde draait met de klok mee rond het midden van het element, optioneel verschoven door [Offset](/docs/nl-nl/reference/engine/classes/UIGradient#Offset) . [Rotation](/docs/nl-nl/reference/engine/classes/UIGradient#Rotation)  controleert de start- en eindhoek van de draaiing. Standaard draait dit van 0  tot 360  graden, maar [Scale](/docs/nl-nl/reference/engine/classes/UIGradient#Scale)  waarden minder dan 1  kunnen die hoek verkleinen.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Type-Linear.png)[Type](/docs/nl-nl/reference/engine/classes/UIGradient#Type)  = [Linear](/docs/nl-nl/reference/engine/enums/GradientType#Linear)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Type-Radial.png)[Type](/docs/nl-nl/reference/engine/classes/UIGradient#Type)  = [Radial](/docs/nl-nl/reference/engine/enums/GradientType#Radial)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Type-Elliptical.png)[Type](/docs/nl-nl/reference/engine/classes/UIGradient#Type)  = [Elliptical](/docs/nl-nl/reference/engine/enums/GradientType#Elliptical)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Type-Conical.png)[Type](/docs/nl-nl/reference/engine/classes/UIGradient#Type)  = [Conical](/docs/nl-nl/reference/engine/enums/GradientType#Conical)

### [Offset en rotatie](#offset-en-rotatie)[](#offset-en-rotatie)

De [Offset](/docs/nl-nl/reference/engine/classes/UIGradient#Offset)  en [Rotation](/docs/nl-nl/reference/engine/classes/UIGradient#Rotation)  eigenschappen laten je de controlepunten van het verloop en de hoek aanpassen. Zoals geïllustreerd in de volgende diagrammen, is [Offset](/docs/nl-nl/reference/engine/classes/UIGradient#Offset)  gebaseerd op een percentage  van de breedte of hoogte van de bovenliggende, en zowel positieve als negatieve waarden zijn geldig.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Offset-X-0.png)[Offset.X](/docs/nl-nl/reference/engine/classes/UIGradient#Offset)  = 0

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Offset-X-Pos-0.25.png)[Offset.X](/docs/nl-nl/reference/engine/classes/UIGradient#Offset)  = 0.25

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Offset-X-Neg-0.25.png)[Offset.X](/docs/nl-nl/reference/engine/classes/UIGradient#Offset)  = -0.25

Evenzo, wanneer je het verloop roteert, draaien de controlepunten ook:

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Rotation-0.png)[Rotation](/docs/nl-nl/reference/engine/classes/UIGradient#Rotation)  = 0

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Rotation-Pos-45.png)[Rotation](/docs/nl-nl/reference/engine/classes/UIGradient#Rotation)  = 45

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Rotation-Neg-90.png)[Rotation](/docs/nl-nl/reference/engine/classes/UIGradient#Rotation)  = -90

### [Schaal](#schaal)[](#schaal)

Deze verloopfunctie is momenteel in beta. Schakel het in via Bestand  ⟩ Bèta-functies  ⟩ Verbeterde UIGradients .

De [Scale](/docs/nl-nl/reference/engine/classes/UIGradient#Scale)  van een verloop vermenigvuldigt de omvang van het verloop, en controleert hoeveel van de kleur/transparantievolgorde zichtbaar is binnen het element.

-

Wanneer [Scale](/docs/nl-nl/reference/engine/classes/UIGradient#Scale)  minder dan 1  is, beslaat het verloop minder dan de volledige omvang. De resterende kleur/transparantie wordt ingevuld volgens de [TileMode](/docs/nl-nl/reference/engine/classes/UIGradient#TileMode)  eigenschap.

-

Wanneer [Scale](/docs/nl-nl/reference/engine/classes/UIGradient#Scale)  groter dan 1  is, beslaat het verloop meer dan de volledige omvang en is slechts een deel van de kleur/transparantie zichtbaar.

-

Voor [Elliptical](/docs/nl-nl/reference/engine/enums/GradientType#Elliptical)  verlopen, beïnvloedt [Scale](/docs/nl-nl/reference/engine/classes/UIGradient#Scale)  beide stralen van de ellips.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Scale-1.0.png)[Scale](/docs/nl-nl/reference/engine/classes/UIGradient#Scale)  = 1

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Scale-0.25.png)[Scale](/docs/nl-nl/reference/engine/classes/UIGradient#Scale)  = 0.25

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-Scale-1.8.png)[Scale](/docs/nl-nl/reference/engine/classes/UIGradient#Scale)  = 1.8

### [Tegelmodus](#tegelmodus)[](#tegelmodus)

Deze verloopfunctie is momenteel in beta. Schakel het in via Bestand  ⟩ Bèta-functies  ⟩ Verbeterde UIGradients .

De [TileMode](/docs/nl-nl/reference/engine/classes/UIGradient#TileMode)  eigenschap stelt in hoe het verloop herhaalt wanneer de volledige volgorde de bovenliggende niet volledig bedekt.

-

[Clamp](/docs/nl-nl/reference/engine/enums/GradientTileMode#Clamp)  — Standaardmodus waarbij de kleur/transparantie waarden aan het begin en einde van de volgorde oneindig uitbreiden, zodat de startwaarden elk gebied vóór het verloop vullen en de eindwaarden elk gebied erna vullen.

-

[Repeat](/docs/nl-nl/reference/engine/enums/GradientTileMode#Repeat)  — Het verloop herhaalt door de kleur/transparantie volgorde naadloos van einde naar begin te wikkelen. Dit kan een zichtbare naad produceren als de eerste en laatste kleur/transparantie waarden in de volgorde verschillen.

-

[Mirror](/docs/nl-nl/reference/engine/enums/GradientTileMode#Mirror)  — Het verloop reflecteert bij elke grens zodat de kleur/transparantie volgorde ping‑pongt. Dit produceert een soepele herhaling zonder naad, aangezien de richting omkeert bij elke tegelrand.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-TileMode-Clamp.png)[TileMode](/docs/nl-nl/reference/engine/classes/UIGradient#TileMode)  = [Clamp](/docs/nl-nl/reference/engine/enums/GradientTileMode#Clamp)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-TileMode-Repeat.png)[TileMode](/docs/nl-nl/reference/engine/classes/UIGradient#TileMode)  = [Repeat](/docs/nl-nl/reference/engine/enums/GradientTileMode#Repeat)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGradient-TileMode-Mirror.png)[TileMode](/docs/nl-nl/reference/engine/classes/UIGradient#TileMode)  = [Mirror](/docs/nl-nl/reference/engine/enums/GradientTileMode#Mirror)

## [Omtrek](#omtrek)[](#omtrek)

De [UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke)  instantie past een omtrek toe op tekst of een rand. Belangrijke kenmerken zijn:

-

Aanpasbare [kleur](#kleur-of-verloop)  en [dikte](#dikte)  van de omtrek.

-

Mogelijkheid om de omtrek [transparantie](#transparantie-1)  onafhankelijk van de transparantie van de bovenliggende in te stellen.

-

Aanpasbare [positie en/of offset](#randpositieoffset)  ten opzichte van de rand van de bovenliggende.

-

Drie [hoekstijlen](#hoekstijl)  (rond, afgeschuind of schuin).

-

Ondersteuning voor omtrek [verloop](#kleur-of-verloop)  via de [UIGradient](/docs/nl-nl/reference/engine/classes/UIGradient)  instantie.

### [Dikte](#dikte)[](#dikte)

Je kunt de omtrekdikte instellen via de [Thickness](/docs/nl-nl/reference/engine/classes/UIStroke#Thickness)  eigenschap, die wordt gemeten in pixels (standaard) of geschaald ten opzichte van de bovenliggende, afhankelijk van de [StrokeSizingMode](/docs/nl-nl/reference/engine/classes/UIStroke#StrokeSizingMode)  van de modifier. Als de omtrek op tekst is en [StrokeSizingMode](/docs/nl-nl/reference/engine/classes/UIStroke#StrokeSizingMode)  is ingesteld op [ScaledSize](/docs/nl-nl/reference/engine/enums/StrokeSizingMode#ScaledSize) , is de dikte relatief aan de lettergrootte.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-Thickness-4.png)[UIStroke.Thickness](/docs/nl-nl/reference/engine/classes/UIStroke#Thickness)  = 4

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-Thickness-12.png)[UIStroke.Thickness](/docs/nl-nl/reference/engine/classes/UIStroke#Thickness)  = 12

Vermijd het [tweeneren](/docs/nl-nl/ui/animation)  van de [Thickness](/docs/nl-nl/reference/engine/classes/UIStroke#Thickness)  eigenschap van een [UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke)  instantie die op tekst  objecten is toegepast. Dit rendert en slaat veel glyph-groottes per frame op, wat mogelijk prestatieproblemen of knipperende tekst veroorzaakt.

### [Kleur of verloop](#kleur-of-verloop)[](#kleur-of-verloop)

Je kunt de omtrekkleur instellen via de [Color](/docs/nl-nl/reference/engine/classes/UIStroke#Color)  eigenschap, evenals een kind [UIGradient](/docs/nl-nl/reference/engine/classes/UIGradient)  instantie invoegen om verloopomtrekken te creëren.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-Color-Solid.png)[UIStroke.Color](/docs/nl-nl/reference/engine/classes/UIStroke#Color)  = (0, 95, 225)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-Color-Gradient.png)[UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke)  met [UIGradient](/docs/nl-nl/reference/engine/classes/UIGradient)  kind

Zowel het bovenliggende object als [UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke)  kunnen kind [UIGradient](/docs/nl-nl/reference/engine/classes/UIGradient)  instanties hebben, waardoor je onafhankelijk verloop kunt instellen op de omtrek  en vulling .

### [Tekstomtrek of rand](#tekstomtrek-of-rand)[](#tekstomtrek-of-rand)

Afhankelijk van het type bovenliggende, werkt [UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke)  als een tekstomtrek  of als een rand . Wanneer je [UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke)  aan een tekstobject zoals [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel)  koppelt, past het toe op de omtrek van de tekst; wanneer je [UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke)  aan andere [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  koppelt, past het toe op de rand.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-As-Text-Outline.png)[TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel)  met [UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke)  kind

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-As-Border.png)[Frame](/docs/nl-nl/reference/engine/classes/Frame)  met [UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke)  en [UICorner](/docs/nl-nl/reference/engine/classes/UICorner)  kinderen

Wanneer toegepast op een tekstobject, kun je het standaardgedrag van de omtrek overschrijven via de [ApplyStrokeMode](/docs/nl-nl/reference/engine/classes/UIStroke#ApplyStrokeMode)  eigenschap, waardoor je de omtrek op de grenzen van het object kunt toepassen in plaats van op de tekst zelf. Je kunt zelfs de tekstomtrek en rand onafhankelijk regelen door twee [UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke)  instanties aan een tekstobject te koppelen, waarvan de ene is ingesteld op Contextueel  en de andere op Rand .

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-As-Text-Outline.png)[UIStroke.ApplyStrokeMode](/docs/nl-nl/reference/engine/classes/UIStroke#ApplyStrokeMode)  = [Contextual](/docs/nl-nl/reference/engine/enums/ApplyStrokeMode#Contextual)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-Stroke-Mode-Border.png)[UIStroke.ApplyStrokeMode](/docs/nl-nl/reference/engine/classes/UIStroke#ApplyStrokeMode)  = [Border](/docs/nl-nl/reference/engine/enums/ApplyStrokeMode#Border)

### [Randpositie/offset](#randpositieoffset)[](#randpositieoffset)

[BorderStrokePosition](/docs/nl-nl/reference/engine/classes/UIStroke#BorderStrokePosition)  stelt de positie van de omtrek in ten opzichte van de rand van de bovenliggende en [BorderOffset](/docs/nl-nl/reference/engine/classes/UIStroke#BorderOffset)  laat je een extra offset voor de positie van de omtrek specificeren.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-BorderStrokePosition-Center.png)[BorderStrokePosition](/docs/nl-nl/reference/engine/classes/UIStroke#BorderStrokePosition)  = [Center](/docs/nl-nl/reference/engine/enums/BorderStrokePosition#Center)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-BorderStrokePosition-Inner.png)[BorderStrokePosition](/docs/nl-nl/reference/engine/classes/UIStroke#BorderStrokePosition)  = [Inner](/docs/nl-nl/reference/engine/enums/BorderStrokePosition#Inner)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-BorderStrokePosition-Outer.png)[BorderStrokePosition](/docs/nl-nl/reference/engine/classes/UIStroke#BorderStrokePosition)  = [Outer](/docs/nl-nl/reference/engine/enums/BorderStrokePosition#Outer)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-BorderOffset-Out.png)[BorderOffset](/docs/nl-nl/reference/engine/classes/UIStroke#BorderOffset)  = (0.15, 0)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-BorderOffset-In.png)[BorderOffset](/docs/nl-nl/reference/engine/classes/UIStroke#BorderOffset)  = (0, -16)

### [Transparantie](#transparantie-1)[](#transparantie-1)

De [Transparency](/docs/nl-nl/reference/engine/classes/UIStroke#Transparency)  eigenschap stelt de omtrektransparantie onafhankelijk in van de [BackgroundTransparency](/docs/nl-nl/reference/engine/classes/GuiObject#BackgroundTransparency)  of [TextTransparency](/docs/nl-nl/reference/engine/classes/TextLabel#TextTransparency)  van het bovenliggende object. Dit stelt je in staat om tekst en randen te renderen die "hol" zijn (bestaande uit alleen een omtrek).

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-Transparency-A.png)[TextLabel.TextTransparency](/docs/nl-nl/reference/engine/classes/TextLabel#TextTransparency)  = 0
[UIStroke.Transparency](/docs/nl-nl/reference/engine/classes/UIStroke#Transparency)  = 0.5

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-Transparency-B.png)[TextLabel.TextTransparency](/docs/nl-nl/reference/engine/classes/TextLabel#TextTransparency)  = 1
[UIStroke.Transparency](/docs/nl-nl/reference/engine/classes/UIStroke#Transparency)  = 0

### [Hoekstijl](#hoekstijl)[](#hoekstijl)

De [LineJoinMode](/docs/nl-nl/reference/engine/classes/UIStroke#LineJoinMode)  eigenschap laat je controleren hoe hoeken worden geïnterpreteerd. Het accepteert een waarde van [Round](/docs/nl-nl/reference/engine/enums/LineJoinMode#Round) , [Bevel](/docs/nl-nl/reference/engine/enums/LineJoinMode#Bevel) , of [Miter](/docs/nl-nl/reference/engine/enums/LineJoinMode#Miter) .

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-LineJoinMode-Round.png)[LineJoinMode](/docs/nl-nl/reference/engine/classes/UIStroke#LineJoinMode)  = [Round](/docs/nl-nl/reference/engine/enums/LineJoinMode#Round)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-LineJoinMode-Bevel.png)[LineJoinMode](/docs/nl-nl/reference/engine/classes/UIStroke#LineJoinMode)  = [Bevel](/docs/nl-nl/reference/engine/enums/LineJoinMode#Bevel)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIStroke-LineJoinMode-Miter.png)[LineJoinMode](/docs/nl-nl/reference/engine/classes/UIStroke#LineJoinMode)  = [Miter](/docs/nl-nl/reference/engine/enums/LineJoinMode#Miter)

### [Laagstructuur](#laagstructuur)[](#laagstructuur)

Om meerdere broeder [UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke)  instanties op een [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  van voor naar achter te stapelen, kun je de [ZIndex](/docs/nl-nl/reference/engine/classes/UIStroke#ZIndex)  eigenschap gebruiken. Degenen met een lagere [ZIndex](/docs/nl-nl/reference/engine/classes/UIStroke#ZIndex)  renderen onder (achter) degenen met een hogere [ZIndex](/docs/nl-nl/reference/engine/classes/UIStroke#ZIndex) .

Houd er rekening mee dat de rendervolgorde voor [UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke)  instanties met dezelfde [ZIndex](/docs/nl-nl/reference/engine/classes/UIStroke#ZIndex)  niet gedefinieerd is. Pas geen meerdere [UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke)  instanties met dezelfde index toe als hun rendervolgorde belangrijk is.

## [Hoeken](#hoeken)[](#hoeken)

De [UICorner](/docs/nl-nl/reference/engine/classes/UICorner)  instantie past vervorming toe op de hoeken van zijn bovenliggende [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject) . Je kunt de toegepaste straal regelen via de [CornerRadius](/docs/nl-nl/reference/engine/classes/UICorner#CornerRadius)  eigenschap met behulp van [Scale](/docs/nl-nl/reference/engine/datatypes/UDim#Scale)  of [Offset](/docs/nl-nl/reference/engine/datatypes/UDim#Offset) .

[Scale](/docs/nl-nl/reference/engine/datatypes/UDim#Scale)  rondt de hoeken af tot een percentage  gebaseerd op de totale lengte van de kortste  rand van de bovenliggende, wat betekent dat een schaal van 0.5  of hoger de bovenliggende in een "pil" vorm vervormt, ongeacht de breedte of hoogte. [Offset](/docs/nl-nl/reference/engine/datatypes/UDim#Offset)  rondt de hoeken af tot een specifiek aantal pixels , ongeacht de breedte/hoogte van de bovenliggende.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UICorner-Scale-0.25.png)[Scale](/docs/nl-nl/reference/engine/datatypes/UDim#Scale)  = 0.25  · [Offset](/docs/nl-nl/reference/engine/datatypes/UDim#Offset)  = 0

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UICorner-Scale-0.5.png)[Scale](/docs/nl-nl/reference/engine/datatypes/UDim#Scale)  = 0.5  · [Offset](/docs/nl-nl/reference/engine/datatypes/UDim#Offset)  = 0

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UICorner-Offset-32.png)[Scale](/docs/nl-nl/reference/engine/datatypes/UDim#Scale)  = 0  · [Offset](/docs/nl-nl/reference/engine/datatypes/UDim#Offset)  = 32

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UICorner-Offset-64.png)[Scale](/docs/nl-nl/reference/engine/datatypes/UDim#Scale)  = 0  · [Offset](/docs/nl-nl/reference/engine/datatypes/UDim#Offset)  = 64

Je kunt ook individuele hoeken  regelen via de [TopLeftRadius](/docs/nl-nl/reference/engine/classes/UICorner#TopLeftRadius) , [TopRightRadius](/docs/nl-nl/reference/engine/classes/UICorner#TopRightRadius) , [BottomRightRadius](/docs/nl-nl/reference/engine/classes/UICorner#BottomRightRadius) , en [BottomLeftRadius](/docs/nl-nl/reference/engine/classes/UICorner#BottomLeftRadius)  eigenschappen.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UICorner-Mixed-1.png)[TopLeftRadius](/docs/nl-nl/reference/engine/classes/UICorner#TopLeftRadius)  = (0, 0)
[TopRightRadius](/docs/nl-nl/reference/engine/classes/UICorner#TopRightRadius)  = (0, 48)
[BottomRightRadius](/docs/nl-nl/reference/engine/classes/UICorner#BottomRightRadius)  = (0, 48)
[BottomLeftRadius](/docs/nl-nl/reference/engine/classes/UICorner#BottomLeftRadius)  = (0, 0)

## [Padding](#padding)[](#padding)

Een [UIPadding](/docs/nl-nl/reference/engine/classes/UIPadding)  object past boven-, onder-, links- en/of rechtspadding toe op de inhoud van de bovenliggende [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject) . Bijvoorbeeld, je kunt de tekst binnen een tekstlabel naar beneden of omhoog verplaatsen door een offset toe te passen op de [PaddingBottom](/docs/nl-nl/reference/engine/classes/UIPadding#PaddingBottom)  eigenschap van de modifier.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIPadding-PaddingBottom-Default.png)[TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel)  zonder [UIPadding](/docs/nl-nl/reference/engine/classes/UIPadding)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIPadding-PaddingBottom-Offset-Negative.png)[PaddingBottom](/docs/nl-nl/reference/engine/classes/UIPadding#PaddingBottom)  = (0, -20)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIPadding-PaddingBottom-Offset-Positive.png)[PaddingBottom](/docs/nl-nl/reference/engine/classes/UIPadding#PaddingBottom)  = (0, 30)

## [Schaduw](#schaduw)[](#schaduw)

Een [UIShadow](/docs/nl-nl/reference/engine/classes/UIShadow)  object rendert een schaduw voor zijn bovenliggende UI-instantie. Een schaduw kan de rechthoekige vorm van de bovenliggende volgen of de glyphs van een tekstobject. Vormen schaduwen kunnen buiten of binnen de bovenliggende verschijnen, en maskeren het gebied direct achter de bovenliggende. Zowel vormen als tekstschaduwen kunnen een kleurverloop gebruiken.

Als de bovenliggende een [UICorner](/docs/nl-nl/reference/engine/classes/UICorner)  of een niet-nul [GuiObject.Rotation](/docs/nl-nl/reference/engine/classes/GuiObject#Rotation)  heeft, volgt zijn vormschaduw dezelfde hoeken of rotatie. [UIShadow](/docs/nl-nl/reference/engine/classes/UIShadow)  ondersteunt geen [Path2D](/docs/nl-nl/reference/engine/classes/Path2D)  of texturen.

Sommige functies zijn momenteel in beta. Schakel ze in via Bestand  ⟩ Bèta-functies  ⟩ Verbeterde UIShadows .

### [Vorm- en tekstschaduwen](#vorm--en-tekstschaduwen)[](#vorm--en-tekstschaduwen)

De [Mode](/docs/nl-nl/reference/engine/classes/UIShadow#Mode)  eigenschap bepaalt wat de schaduw werpt, en beide modi kunnen naast elkaar bestaan onder dezelfde bovenliggende.

-

[Shape](/docs/nl-nl/reference/engine/enums/ApplyShadowMode#Shape)  is de standaard. De schaduw volgt het rechthoekige gebied van elke [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject) .

-

[Text](/docs/nl-nl/reference/engine/enums/ApplyShadowMode#Text)  volgt de tekstglyphs van een [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel) , [TextButton](/docs/nl-nl/reference/engine/classes/TextButton) , of [TextBox](/docs/nl-nl/reference/engine/classes/TextBox) . Andere UI-objecten renderen geen schaduw in deze modus.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-Mode-Shape.png)[Mode](/docs/nl-nl/reference/engine/classes/UIShadow#Mode)  = [Shape](/docs/nl-nl/reference/engine/enums/ApplyShadowMode#Shape)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-Mode-Text.png)[Mode](/docs/nl-nl/reference/engine/classes/UIShadow#Mode)  = [Text](/docs/nl-nl/reference/engine/enums/ApplyShadowMode#Text)

[Spread](/docs/nl-nl/reference/engine/classes/UIShadow#Spread) , [Inset](/docs/nl-nl/reference/engine/classes/UIShadow#Inset) , en [ShowBehindParent](/docs/nl-nl/reference/engine/classes/UIShadow#ShowBehindParent)  hebben geen effect in tekstmodus.

### [Vervaging](#vervaging)[](#vervaging)

De [BlurRadius](/docs/nl-nl/reference/engine/classes/UIShadow#BlurRadius)  eigenschap bepaalt de vervaging van de schaduw. Een grotere waarde maakt de randen van de schaduw zachter. Houd er rekening mee dat de schaalfactor  van deze [UDim](/docs/nl-nl/reference/engine/datatypes/UDim)  eigenschap relatief is aan de breedte of hoogte van de bovenliggende, welke ook het kortste is.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-BlurRadius-Scale-0.png)[BlurRadius](/docs/nl-nl/reference/engine/classes/UIShadow#BlurRadius)  = (0, 0)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-BlurRadius-Scale-0.75.png)[BlurRadius](/docs/nl-nl/reference/engine/classes/UIShadow#BlurRadius)  = (0.75, 0)

### [Kleur en transparantie](#kleur-en-transparantie)[](#kleur-en-transparantie)

De [Color](/docs/nl-nl/reference/engine/classes/UIShadow#Color)  eigenschap bepaalt de kleur van de schaduw, terwijl [Transparency](/docs/nl-nl/reference/engine/classes/UIShadow#Transparency)  de transparantie van de schaduw instelt met 0  als volledig ondoorzichtig en 1  als volledig doorzichtig.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-Color-White-Transparency-0.6.png)[Color](/docs/nl-nl/reference/engine/classes/UIShadow#Color)  = (255, 255, 255)  · [Transparency](/docs/nl-nl/reference/engine/classes/UIShadow#Transparency)  = 0.6

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-Color-Maroon-Transparency-0.png)[Color](/docs/nl-nl/reference/engine/classes/UIShadow#Color)  = (50, 0, 35)  · [Transparency](/docs/nl-nl/reference/engine/classes/UIShadow#Transparency)  = 0

Voor een meerkleurige schaduw, voeg een [UIGradient](/docs/nl-nl/reference/engine/classes/UIGradient)  toe als kind van de [UIShadow](/docs/nl-nl/reference/engine/classes/UIShadow) . Het verloop beïnvloedt de schaduw zonder de vulling van de bovenliggende te veranderen.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-Color-Gradient.png) Een [UIGradient](/docs/nl-nl/reference/engine/classes/UIGradient)  past een cyan-naar-paarse verloop toe op de vormschaduw.

### [Offset en spreiding](#offset-en-spreiding)[](#offset-en-spreiding)

De [Offset](/docs/nl-nl/reference/engine/classes/UIShadow#Offset)  eigenschap verplaatst de schaduw ten opzichte van de positie van de bovenliggende, terwijl [Spread](/docs/nl-nl/reference/engine/classes/UIShadow#Spread)  de schaduw uitbreidt of verkleint ten opzichte van de grootte van de bovenliggende.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-Offset-Offset.png)[Offset](/docs/nl-nl/reference/engine/classes/UIShadow#Offset)  = {0, -14}, {0, 6}

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-Offset-Scale.png)[Offset](/docs/nl-nl/reference/engine/classes/UIShadow#Offset)  = {0.1, 0}, {-0.15, 0}

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-Spread-Offset.png)[Spread](/docs/nl-nl/reference/engine/classes/UIShadow#Spread)  = {0, 10}, {0, 10}

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-Spread-Scale.png)[Spread](/docs/nl-nl/reference/engine/classes/UIShadow#Spread)  = {0.3, 0}, {0.3, 0}

### [Ingebedde schaduwen](#ingebedde-schaduwen)[](#ingebedde-schaduwen)

Stel [Inset](/docs/nl-nl/reference/engine/classes/UIShadow#Inset)  in op true  om de schaduw bovenop en binnen de bovenliggende te renderen in plaats van erachter. Positieve [Spread](/docs/nl-nl/reference/engine/classes/UIShadow#Spread)  waarden breiden een ingesloten schaduw uit naar het midden van de bovenliggende.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-Inset-False.png)[Inset](/docs/nl-nl/reference/engine/classes/UIShadow#Inset)  = false

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-Inset-True.png)[Inset](/docs/nl-nl/reference/engine/classes/UIShadow#Inset)  = true

### [Inhoud achter een transparante bovenliggende onthullen](#inhoud-achter-een-transparante-bovenliggende-onthullen)[](#inhoud-achter-een-transparante-bovenliggende-onthullen)

Standaard is [ShowBehindParent](/docs/nl-nl/reference/engine/classes/UIShadow#ShowBehindParent)  true , zodat de gehele vormschaduw wordt gerenderd, inclusief het gedeelte direct achter de bovenliggende. Stel het in op false  om dat gedeelte van de schaduw te maskeren. Dit voorkomt dat de schaduw de inhoud verduistert die zichtbaar is door een transparante bovenliggende.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-ShowBehindParent-True.png)[ShowBehindParent](/docs/nl-nl/reference/engine/classes/UIShadow#ShowBehindParent)  = true

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIShadow-ShowBehindParent-False.png)[ShowBehindParent](/docs/nl-nl/reference/engine/classes/UIShadow#ShowBehindParent)  = false

Deze eigenschap heeft geen effect op ingesloten of tekstschaduwen.

### [Schaduwen stapelen](#schaduwen-stapelen)[](#schaduwen-stapelen)

Voeg meerdere [UIShadow](/docs/nl-nl/reference/engine/classes/UIShadow)  instanties toe aan dezelfde bovenliggende om effecten te combineren. De [ZIndex](/docs/nl-nl/reference/engine/classes/UIShadow#ZIndex)  eigenschap controleert hun rendervolgorde. Schaduwen met lagere waarden renderen achter schaduwen met hogere waarden.

De rendervolgorde van schaduwen die dezelfde [ZIndex](/docs/nl-nl/reference/engine/classes/UIShadow#ZIndex)  delen is niet gedefinieerd. Ken elke broeder schaduw een andere waarde toe wanneer hun volgorde belangrijk is.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
