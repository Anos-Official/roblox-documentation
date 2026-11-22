<!-- Source: https://create.roblox.com/docs/nl-nl/ui/frames -->

Frames | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Gebruikersinterface](/docs/nl-nl/ui)
6. /
7. UI-objecten

# Frames

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Basis [Frames](/docs/nl-nl/reference/engine/classes/Frame)  fungeren als containers voor andere [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  zoals [labels](/docs/nl-nl/ui/labels)  en [knoppen](/docs/nl-nl/ui/buttons) . Je kunt frames toepassen om weer te geven op het [scherm](/docs/nl-nl/ui/on-screen-containers)  van een gebruiker of op een [oppervlak](/docs/nl-nl/ui/in-experience-containers)  binnen het spel.

 ![Voorbeeld Frame op het scherm met een TextLabel, TextBox en ImageButton.](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/Frame-Example.jpg)

Frames zijn ideale containers voor responsieve lay-outs zoals [lijst- en flexlay-outs](/docs/nl-nl/ui/list-flex-layouts) , waarmee je de grootte van het frame kunt wijzigen en dynamisch kunt aanpassen hoe lay-outitems erin passen. [Frames](/docs/nl-nl/reference/engine/classes/Frame)  zijn ook kern [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject) , zodat je eigenschappen kunt aanpassen zoals [BackgroundColor3](/docs/nl-nl/reference/engine/classes/GuiObject#BackgroundColor3) , [Transparency](/docs/nl-nl/reference/engine/classes/GuiObject#Transparency) , een [achtergrondverloop](/docs/nl-nl/ui/appearance-modifiers#verloop)  of [rand](/docs/nl-nl/ui/appearance-modifiers#omtrek)  kunt toepassen, en meer.

Afgezien van hun gebruik als containers, kun je [Frames](/docs/nl-nl/reference/engine/classes/Frame)  ook gebruiken voor UI-ontwerp. Bijvoorbeeld, als een visuele scheiding tussen andere UI-elementen, kun je een frame schalen om dun en lang te zijn totdat het een lijn wordt.

Zie ook [scrollende frames](/docs/nl-nl/ui/scrolling-frames) , [viewport-frames](/docs/nl-nl/ui/viewport-frames)  en [videoframes](/docs/nl-nl/ui/video-frames)  als speciale frametypes met unieke ingebouwde mogelijkheden.

## [Afkapping](#afkapping)[](#afkapping)

Standaard knippen [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  containers de  inhoud (afgeleide [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject) ) via de [ClipsDescendants](/docs/nl-nl/reference/engine/classes/GuiObject#ClipsDescendants)  boolean. Als je wilt dat afgeleiden buiten de grenzen van een container verschijnen, stel je eenvoudig [ClipsDescendants](/docs/nl-nl/reference/engine/classes/GuiObject#ClipsDescendants)  in op false .

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/ClipsDescendants-On.png)[ClipsDescendants](/docs/nl-nl/reference/engine/classes/GuiObject#ClipsDescendants)  = true

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/ClipsDescendants-Off.png)[ClipsDescendants](/docs/nl-nl/reference/engine/classes/GuiObject#ClipsDescendants)  = false

Belangrijk is dat [StarterGui.ClipsDescendantsSupportsRotation](/docs/nl-nl/reference/engine/classes/StarterGui#ClipsDescendantsSupportsRotation)  true  moet zijn voor knippen om te werken op geroteerde  afgeleiden (niet-nul [Rotation](/docs/nl-nl/reference/engine/classes/GuiObject#Rotation) ) binnen de container. Echter, knippen door  een geroteerde container (de knipcontainer zelf is geroteerd) of door afgeronde hoeken ([UICorner](/docs/nl-nl/reference/engine/classes/UICorner) ) wordt niet ondersteund. Als je knippen nodig hebt op geroteerde of afgeronde containers, overweeg dan [CanvasGroup](/docs/nl-nl/reference/engine/classes/CanvasGroup) .

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Clipping-Descendants-Rotated.png)[ClipsDescendants](/docs/nl-nl/reference/engine/classes/GuiObject#ClipsDescendants)  = true
[Rotation](/docs/nl-nl/reference/engine/classes/GuiObject#Rotation)  = 0

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Clipping-Parent-Rotated.png)[ClipsDescendants](/docs/nl-nl/reference/engine/classes/GuiObject#ClipsDescendants)  = true
[Rotation](/docs/nl-nl/reference/engine/classes/GuiObject#Rotation)  = 10

## [Automatische sizing](#automatische-sizing)[](#automatische-sizing)

Frames kunnen worden ingesteld om [automatisch te schalen](/docs/nl-nl/ui/size-modifiers#automatische-sizing)  afhankelijk van hun inhoud. Om dit te bereiken, stel je de [Size](/docs/nl-nl/reference/engine/classes/Frame#Size)  van het frame in op de minimale  breedte en/of hoogte, en stel je de [AutomaticSize](/docs/nl-nl/reference/engine/classes/Frame#AutomaticSize)  eigenschap in op [X](/docs/nl-nl/reference/engine/enums/AutomaticSize) , [Y](/docs/nl-nl/reference/engine/enums/AutomaticSize) , of [XY](/docs/nl-nl/reference/engine/enums/AutomaticSize) , afhankelijk van welke assen automatische sizing moet toepassen. Eenmaal ingesteld, zal het frame automatisch worden aangepast op basis van de grootte van [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  en lay-outs erin.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
