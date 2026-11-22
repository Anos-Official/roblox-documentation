<!-- Source: https://create.roblox.com/docs/nl-nl/ui/scrolling-frames -->

Scrollende frames | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Gebruikersinterface](/docs/nl-nl/ui)
6. /
7. UI-objecten

# Scrollende frames

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een [ScrollingFrame](/docs/nl-nl/reference/engine/classes/ScrollingFrame)  bestaat uit een aanpasbaar canvas  en scrollbalken  met ingebouwde scrollinteractiviteit en verschillende manieren om aan te passen hoe de scrolling werkt. [ScrollingFrame](/docs/nl-nl/reference/engine/classes/ScrollingFrame)  is ideaal voor het weergeven van veel informatie in een beperkte ruimte en werkt goed met [lijst](/docs/nl-nl/ui/list-flex-layouts)  en [rooster](/docs/nl-nl/ui/grid-table-layouts)  lay-outs.

 ![Voorbeeld van een ScrollingFrame op het scherm met een tabbladcategoriebalk en een lijst van magische items die de speler kan overwegen om aan te schaffen.](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/ScrollingFrame-Example.jpg)

## [Canvas](#canvas)[](#canvas)

Het canvas  is het primaire gebied van een [ScrollingFrame](/docs/nl-nl/reference/engine/classes/ScrollingFrame)  dat andere [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  kan bevatten. Het scrollgedrag past zich automatisch aan in de volgende scenario's:

| Frame-instelling | | Resultaat |
| --- | --- |
| De [CanvasSize](/docs/nl-nl/reference/engine/classes/ScrollingFrame#CanvasSize)  van het frame is hoger dan de totale hoogte; specifiek de totale [CanvasSize.Y](/docs/nl-nl/reference/engine/classes/ScrollingFrame#CanvasSize)  overschrijdt de totale [Size.Y](/docs/nl-nl/reference/engine/classes/ScrollingFrame#Size) . | | Verticale scrolling is ingeschakeld en er verschijnt een verticale scrollbalk. |
| De [CanvasSize](/docs/nl-nl/reference/engine/classes/ScrollingFrame#CanvasSize)  van het frame is breder dan de totale breedte; specifiek de totale [CanvasSize.X](/docs/nl-nl/reference/engine/classes/ScrollingFrame#CanvasSize)  overschrijdt de totale [Size.X](/docs/nl-nl/reference/engine/classes/ScrollingFrame#Size) . | | Horizontale scrolling is ingeschakeld en er verschijnt een horizontale scrollbalk. |
| De [AutomaticCanvasSize](/docs/nl-nl/reference/engine/classes/ScrollingFrame#AutomaticCanvasSize)  van het frame is ingesteld op [Y](/docs/nl-nl/reference/engine/enums/AutomaticSize)  of [XY](/docs/nl-nl/reference/engine/enums/AutomaticSize)  en de totale hoogte van de inhoud (kind [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject) ) overschrijdt de totale [Size.Y](/docs/nl-nl/reference/engine/classes/ScrollingFrame#Size) . | | Verticale scrolling is ingeschakeld en er verschijnt een verticale scrollbalk. |
| De [AutomaticCanvasSize](/docs/nl-nl/reference/engine/classes/ScrollingFrame#AutomaticCanvasSize)  van het frame is ingesteld op [X](/docs/nl-nl/reference/engine/enums/AutomaticSize)  of [XY](/docs/nl-nl/reference/engine/enums/AutomaticSize)  en de totale breedte van de inhoud (kind [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject) ) overschrijdt de totale [Size.X](/docs/nl-nl/reference/engine/classes/ScrollingFrame#Size) . | | Horizontale scrolling is ingeschakeld en er verschijnt een horizontale scrollbalk. |

De [CanvasPosition](/docs/nl-nl/reference/engine/classes/ScrollingFrame#CanvasPosition)  eigenschap weerspiegelt de huidige  positionele offset van het canvas binnen het frame, in pixels, en stelt de positie van de scrollbalken dienovereenkomstig in. Let op dat deze eigenschap niets doet als scrollbalken niet zichtbaar zijn.

## [Insets](#insets)[](#insets)

De [CanvasSize](/docs/nl-nl/reference/engine/classes/ScrollingFrame#CanvasSize)  van een scrollend frame kan worden beïnvloed door de [VerticalScrollBarInset](/docs/nl-nl/reference/engine/classes/ScrollingFrame#VerticalScrollBarInset)  en/of [HorizontalScrollBarInset](/docs/nl-nl/reference/engine/classes/ScrollingFrame#HorizontalScrollBarInset)  eigenschappen. In het volgende voorbeelddiagram gebruikt een verticaal scrollend frame een canvasbreedte van 100%. Met [VerticalScrollBarInset](/docs/nl-nl/reference/engine/classes/ScrollingFrame#VerticalScrollBarInset)  ingesteld op [None](/docs/nl-nl/reference/engine/enums/ScrollBarInset)  (standaard), strekt het canvas zich uit tot de volledige breedte van het scrollende frame, waardoor een klein deel van de inhoud onder de scrollbalk wordt verborgen. In tegenstelling tot dat, zorgt een instelling van [VerticalScrollBarInset](/docs/nl-nl/reference/engine/classes/ScrollingFrame#VerticalScrollBarInset)  van [Always](/docs/nl-nl/reference/engine/enums/ScrollBarInset)  of [ScrollBar](/docs/nl-nl/reference/engine/enums/ScrollBarInset)  ervoor dat het canvas met de [ScrollBarThickness](/docs/nl-nl/reference/engine/classes/ScrollingFrame#ScrollBarThickness)  hoeveelheid wordt ingekort, zodat het canvas rand‑tot‑rand met de scrollbalk aansluit.

Geen (Standaard) Altijd / ScrollBar

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/ScrollingFrame-Canvas-No-Inset.png)

## [Scrollbalken](#scrollbalken)[](#scrollbalken)

De scrollbalken  van het frame weerspiegelen de huidige canvaspositie en bieden automatische sleep-om-te-scrollen interactiviteit. Voor verticale scrollbalken schakelt de [VerticalScrollBarPosition](/docs/nl-nl/reference/engine/classes/ScrollingFrame#VerticalScrollBarPosition)  eigenschap de positie van de balk in naar links of rechts van het canvas, maar horizontale scrollbalken kunnen alleen onder het canvas worden gepositioneerd.

De constructie van de scrollbalk bestaat uit drie asset-eigenschappen:

-

[TopImage](/docs/nl-nl/reference/engine/classes/ScrollingFrame#TopImage)  — Weergegeven bovenaan een verticale scrollbalk, of aan de linkerkant van een horizontale scrollbalk (90° tegen de klok in gedraaid voor een horizontale scrollbalk).

-

[MidImage](/docs/nl-nl/reference/engine/classes/ScrollingFrame#MidImage)  — Beslaat het gebied tussen [TopImage](/docs/nl-nl/reference/engine/classes/ScrollingFrame#TopImage)  en [BottomImage](/docs/nl-nl/reference/engine/classes/ScrollingFrame#BottomImage)  (90° tegen de klok in gedraaid voor een horizontale scrollbalk).

-

[BottomImage](/docs/nl-nl/reference/engine/classes/ScrollingFrame#BottomImage)  — Weergegeven onderaan een verticale scrollbalk, of aan de rechterkant van een horizontale scrollbalk (90° tegen de klok in gedraaid voor een horizontale scrollbalk).

 ![Diagram dat de drie afbeeldingsasset-elementen toont die de scrollbalk van een scrollend frame construeren.](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/ScrollingFrame-Scroll-Bar-Elements.png)

Elke afbeelding schaalt op basis van de [ScrollBarThickness](/docs/nl-nl/reference/engine/classes/ScrollingFrame#ScrollBarThickness)  eigenschap, die de breedte van een verticale scrollbalk of de hoogte van een horizontale scrollbalk verandert.

Aanvullende visuele aanpassingen kunnen worden gedaan via de [ScrollBarImageColor3](/docs/nl-nl/reference/engine/classes/ScrollingFrame#ScrollBarImageColor3)  en [ScrollBarImageTransparency](/docs/nl-nl/reference/engine/classes/ScrollingFrame#ScrollBarImageTransparency)  eigenschappen, die de afbeeldingsassets van de balk tinten en respectievelijk de doorzichtigheid wijzigen.

## [Afkapping](#afkapping)[](#afkapping)

Standaard knippen [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  containers de  inhoud (afgeleide [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject) ) via de [ClipsDescendants](/docs/nl-nl/reference/engine/classes/GuiObject#ClipsDescendants)  boolean. Als je wilt dat afgeleiden buiten de grenzen van een container verschijnen, stel je eenvoudig [ClipsDescendants](/docs/nl-nl/reference/engine/classes/GuiObject#ClipsDescendants)  in op false .

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/ClipsDescendants-On.png)[ClipsDescendants](/docs/nl-nl/reference/engine/classes/GuiObject#ClipsDescendants)  = true

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/ClipsDescendants-Off.png)[ClipsDescendants](/docs/nl-nl/reference/engine/classes/GuiObject#ClipsDescendants)  = false

Belangrijk is dat [StarterGui.ClipsDescendantsSupportsRotation](/docs/nl-nl/reference/engine/classes/StarterGui#ClipsDescendantsSupportsRotation)  true  moet zijn voor knippen om te werken op geroteerde  afgeleiden (niet-nul [Rotation](/docs/nl-nl/reference/engine/classes/GuiObject#Rotation) ) binnen de container. Echter, knippen door  een geroteerde container (de knipcontainer zelf is geroteerd) of door afgeronde hoeken ([UICorner](/docs/nl-nl/reference/engine/classes/UICorner) ) wordt niet ondersteund. Als je knippen nodig hebt op geroteerde of afgeronde containers, overweeg dan [CanvasGroup](/docs/nl-nl/reference/engine/classes/CanvasGroup) .

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Clipping-Descendants-Rotated.png)[ClipsDescendants](/docs/nl-nl/reference/engine/classes/GuiObject#ClipsDescendants)  = true
[Rotation](/docs/nl-nl/reference/engine/classes/GuiObject#Rotation)  = 0

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Clipping-Parent-Rotated.png)[ClipsDescendants](/docs/nl-nl/reference/engine/classes/GuiObject#ClipsDescendants)  = true
[Rotation](/docs/nl-nl/reference/engine/classes/GuiObject#Rotation)  = 10

## [Elasticiteit](#elasticiteit)[](#elasticiteit)

Standaard vertonen [ScrollingFrames](/docs/nl-nl/reference/engine/classes/ScrollingFrame)  elastisch scrollgedrag op apparaten met aanraakfunctionaliteit, wat betekent dat gebruikers het canvas iets verder kunnen slepen dan de grenzen en, bij het loslaten, het canvas terugveert naar de minimum- of maximumlimiet. Als je het elastische gedrag volledig wilt verwijderen en ervoor wilt zorgen dat het canvas nooit voorbij zijn grenzen scrollt, stel dan de [ElasticBehavior](/docs/nl-nl/reference/engine/classes/ScrollingFrame#ElasticBehavior)  eigenschap in op [Never](/docs/nl-nl/reference/engine/enums/ElasticBehavior) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
