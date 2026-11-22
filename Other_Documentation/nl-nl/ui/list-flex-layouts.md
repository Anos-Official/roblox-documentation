<!-- Source: https://create.roblox.com/docs/nl-nl/ui/list-flex-layouts -->

Lijsten en flex-layouts | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Gebruikersinterface](/docs/nl-nl/ui)
6. /
7. Lay-outstructuren

# Lijsten en flex-layouts

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De [UIListLayout](/docs/nl-nl/reference/engine/classes/UIListLayout)  plaatst broers en zussen [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  in horizontale rijen of verticale kolommen binnen hun bovenliggende container. Telkens wanneer je een broertje of zusje toevoegt of verwijdert, past de lay-out zich dienovereenkomstig aan.

 ![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIListLayout-Example.png)

Zodra je een [UIListLayout](/docs/nl-nl/reference/engine/classes/UIListLayout)  invoegt, overschrijft of beïnvloedt het de [Position](/docs/nl-nl/reference/engine/classes/GuiObject#Position) , [Rotation](/docs/nl-nl/reference/engine/classes/GuiObject#Rotation) , en/of [Size](/docs/nl-nl/reference/engine/classes/GuiObject#Size)  van alle broers en zussen UI-objecten, zodat wijzigingen in die eigenschappen binnen het [Eigenschappen](/docs/nl-nl/studio/properties)  venster of binnen een script niet het normale effect hebben.

## [Vulrichting](#vulrichting)[](#vulrichting)

De [FillDirection](/docs/nl-nl/reference/engine/classes/UIListLayout#FillDirection)  eigenschap bepaalt de richting waarin de broers en zussen van de lijstlay-out worden weergegeven.

 ![UIListLayouts die de FillDirection illustreren van ofwel horizontaal of verticaal.](https://prod.docsiteassets.roblox.com/assets/engine-api/classes/UIListLayout/FillDirection.png)

De volgorde wordt bepaald door de [SortOrder](/docs/nl-nl/reference/engine/classes/UIListLayout#SortOrder)  eigenschap van de lay-out, die ofwel oplopend numeriek  kan zijn, gebaseerd op de [LayoutOrder](/docs/nl-nl/reference/engine/classes/GuiObject#LayoutOrder)  gehele waarde van elk item, of alfanumeriek  op basis van de [Name](/docs/nl-nl/reference/engine/classes/Instance#Name)  van het item.

 ![Voorbeelden van lijstlay-outs die numerieke LayoutOrder-sorting of alfanumerieke Name-sorting illustreren.](https://prod.docsiteassets.roblox.com/assets/engine-api/classes/UIListLayout/SortOrder.png)

Om elementen om te keren, zoals een rechts-naar-links volgorde in een horizontale lijst, moet je de sortering omkeren. Als bijvoorbeeld vier items zijn geordend op [LayoutOrder](/docs/nl-nl/reference/engine/classes/GuiObject#LayoutOrder)  van 0 , 1 , 2 , 3  respectievelijk, negatief elke waarde om een volgorde van 0 , -1 , -2 , -3  te vormen.

## [Uitlijning](#uitlijning)[](#uitlijning)

De [HorizontalAlignment](/docs/nl-nl/reference/engine/classes/UIListLayout#HorizontalAlignment)  en [VerticalAlignment](/docs/nl-nl/reference/engine/classes/UIListLayout#VerticalAlignment)  eigenschappen bepalen de respectieve X  en Y  uitlijning van zowel de broers en zussen van de lijst ten opzichte van elkaar en de algehele grenzen van de lijst binnen zijn container. Bijvoorbeeld, een horizontaal gevulde lijst met [VerticalAlignment](/docs/nl-nl/reference/engine/classes/UIListLayout#VerticalAlignment)  van [Center](/docs/nl-nl/reference/engine/enums/VerticalAlignment)  centreert de broers en zussen van de lijst met elkaar en  centreert de lijst verticaal in zijn container.

 ![Lijstlay-out die de VerticalAlignment van Center illustreert.](https://prod.docsiteassets.roblox.com/assets/engine-api/classes/UIListLayout/VerticalAlignment-Center.png)

[HorizontalAlignment](/docs/nl-nl/reference/engine/classes/UIListLayout#HorizontalAlignment)  en [VerticalAlignment](/docs/nl-nl/reference/engine/classes/UIListLayout#VerticalAlignment)  verschillen iets van [itemlijnuitlijning](#itemlijnuitlijning)  in een [flex](#flex-layouts)  lay-out, waarmee je items in dezelfde lijn kunt uitlijnen zonder dezelfde uitlijning op de algehele grenzen van de lijst in zijn container toe te passen.

## [Wikkelen](#wikkelen)[](#wikkelen)

De [Wraps](/docs/nl-nl/reference/engine/classes/UIListLayout#Wraps)  boolean controleert of broers en zussen binnen de bovenliggende container naar een andere regel wikkelen wanneer hun standaardgrootte de breedte/hoogte van de grenzen van de container overschrijdt.

 ![Diagram dat laat zien hoe Wraps van invloed is op hoe broers en zussen worden verdeeld binnen de grenzen van de bovenliggende container.](https://prod.docsiteassets.roblox.com/assets/engine-api/classes/UIListLayout/Wraps.png)

## [Opvulling](#opvulling)[](#opvulling)

De [Padding](/docs/nl-nl/reference/engine/classes/UIListLayout#Padding)  eigenschap bepaalt de hoeveelheid lege ruimte tussen  elk lijstitem, ingesteld op ofwel een schaal (percentage van de grootte van de container in de huidige richting) of een offset (statische spatiële waarde vergelijkbaar met pixelgrootte).

Deze eigenschap past geen opvulling rondom  de algehele grenzen van de lijst toe; zie [UIPadding](/docs/nl-nl/reference/engine/classes/UIPadding)  om boven-, onder-, links- en/of rechtsopvulling toe te passen op de inhoud van de bovenliggende container.

## [Flex-layouts](#flex-layouts)[](#flex-layouts)

Integreren van flex  in een [UIListLayout](/docs/nl-nl/reference/engine/classes/UIListLayout)  is een krachtige manier om [gelijkmatig te vullen/distribueren](#gelijkmatig-vullen-of-distribueren)  of [uit te lijnen/strekken](#itemlijnuitlijning)  lijstitems over hun lijn, of [flex specifieke items](#flex-individuele-items)  over een variabele ruimte.

Hoewel flex een krachtig hulpmiddel is, moet je het niet zonder doel toepassen op een [UIListLayout](/docs/nl-nl/reference/engine/classes/UIListLayout) , omdat het een lichte prestatiekost met zich meebrengt boven niet-flex, vooral bij het wijzigen van de lay-out of dynamisch toevoegen/verwijderen van flex-items.

Bovendien kan een [gridlay-out](/docs/nl-nl/ui/grid-table-layouts#rasterindeling)  verkieslijk zijn wanneer items strikt moeten uitlijnen op een grid in zowel de X  als Y  richtingen, aangezien gridlay-outs een consistente celgrootte afdwingen terwijl flexlay-outs een variabel aantal items per lijn kunnen gebruiken.

### [Gelijkmatig vullen of distribueren](#gelijkmatig-vullen-of-distribueren)[](#gelijkmatig-vullen-of-distribueren)

Wanneer de lijstlay-out's [vulrichting](#vulrichting)  is ingesteld op [Horizontal](/docs/nl-nl/reference/engine/enums/FillDirection) , specificeert de [HorizontalFlex](/docs/nl-nl/reference/engine/classes/UIListLayout#HorizontalFlex)  eigenschap hoe extra horizontale ruimte in de bovenliggende container moet worden verdeeld. Evenzo, wanneer de vulrichting is ingesteld op [Vertical](/docs/nl-nl/reference/engine/enums/FillDirection) , specificeert de [VerticalFlex](/docs/nl-nl/reference/engine/classes/UIListLayout#VerticalFlex)  eigenschap hoe extra verticale ruimte moet worden verdeeld.

HorizontalFlex VerticalFlex

![UIListLayout voorbeelden die laten zien hoe elke HorizontalFlex optie de grootte en spatiëring van broers en zussen UI-objecten beïnvloedt.](https://prod.docsiteassets.roblox.com/assets/engine-api/classes/UIListLayout/HorizontalFlex-Options.png)

Een praktische toepassing van [HorizontalFlex](/docs/nl-nl/reference/engine/classes/UIListLayout#HorizontalFlex)  is een tabblad venster  interface waar flex de tabbladbalk gelijkmatig vult, ongeacht het aantal tabbladen. Geen enkele benadering is gemakkelijker dan flex in dit geval, omdat het automatisch de breedte van elk tabblad berekent zonder door de ontwikkelaar gedefinieerde breedte-instellingen, en het past zich automatisch aan als het aantal tabbladen verandert.

3 Tabs 6 Tabs

![](https://prod.docsiteassets.roblox.com/assets/engine-api/classes/UIListLayout/HorizontalFlex-Tabs-3.png)

### [Itemlijnuitlijning](#itemlijnuitlijning)[](#itemlijnuitlijning)

De [ItemLineAlignment](/docs/nl-nl/reference/engine/classes/UIListLayout#ItemLineAlignment)  eigenschap definieert de kruis-richting  uitlijning van broers en zussen binnen een lijn, waardoor je objecten van verschillende breedtes/hoogtes kunt uitlijnen of objecten van kleinere breedte/hoogte de hele lijn kunt laten vullen.

 ![Voorbeelden van opties voor ItemLineAlignment in een horizontale vulrichting.](https://prod.docsiteassets.roblox.com/assets/engine-api/classes/UIListLayout/ItemLineAlignment.png)

Een praktische gebruiksgeval voor [ItemLineAlignment](/docs/nl-nl/reference/engine/classes/UIListLayout#ItemLineAlignment)  is om een reeks inconsistent geconfigureerde tegels uit te rekken om hun hele rij te vullen ([Stretch](/docs/nl-nl/reference/engine/enums/ItemLineAlignment) ), waardoor de lay-out coherenter wordt.

Ongelijke Lay-out Vollinge Lijnen

![](https://prod.docsiteassets.roblox.com/assets/engine-api/classes/UIListLayout/ItemLineAlignment-Start.png) Tegels met variërende inhoudshoogtes resulteren in een ongelijke en verspringende lay-out

### [Flex individuele items](#flex-individuele-items)[](#flex-individuele-items)

Hoewel het flexen van een hele lay-out een krachtige functie is, zijn bepaalde lay-outs beter geschikt voor individueel itemflexen . In dergelijke lay-outs behouden sommige elementen in de lijst hun kernmaat terwijl andere items flexen om variabele ruimtes te vullen. Een praktische toepassing is een schuifbalk-widget met uniforme [labels](/docs/nl-nl/ui/labels)  aan beide uiteinden en een flexibele schuifbalk die de volledige breedte ertussen vult.

 ![Voorbeeld van UIFlexItem toegepast op een specifiek GuiObject onder controle van een UIListLayout.](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIFlexItem-Example.png)

Om één specifiek lijstitem als flexibel in te stellen, voeg je een [UIFlexItem](/docs/nl-nl/reference/engine/classes/UIFlexItem)  toe als een kind van het flexibele item, en stel je de [FlexMode](/docs/nl-nl/reference/engine/classes/UIFlexItem#FlexMode)  eigenschap in op [Fill](/docs/nl-nl/reference/engine/enums/UIFlexMode#Fill) , [Grow](/docs/nl-nl/reference/engine/enums/UIFlexMode#Grow) , [Shrink](/docs/nl-nl/reference/engine/enums/UIFlexMode#Shrink) , of [Custom](/docs/nl-nl/reference/engine/enums/UIFlexMode#Custom) .

![Voorbeeldhiërarchie van een UIFlexItem dat is gekoppeld aan een GuiObject onder controle van een UIListLayout.](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIFlexItem-Hierarchy.png)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
