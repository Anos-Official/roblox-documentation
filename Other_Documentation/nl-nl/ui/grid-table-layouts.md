<!-- Source: https://create.roblox.com/docs/nl-nl/ui/grid-table-layouts -->

Raster- en tabelindelingen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Gebruikersinterface](/docs/nl-nl/ui)
6. /
7. Lay-outstructuren

# Raster- en tabelindelingen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

In vergelijking met [UIListLayout](/docs/nl-nl/reference/engine/classes/UIListLayout)  bieden [UIGridLayout](/docs/nl-nl/reference/engine/classes/UIGridLayout)  en [UITableLayout](/docs/nl-nl/reference/engine/classes/UITableLayout)  meer gestructureerde en georganiseerde indelingen. Deze zijn het meest geschikt voor interfaces zoals een winkelinventaris waar elk item kan worden gepresenteerd in een raster van gelijkmatig grote tegels, of items kunnen worden gesorteerd in gerelateerde rijen/kolommen.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGridLayout-Example.jpg)[UIGridLayout](/docs/nl-nl/reference/engine/classes/UIGridLayout)

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UITableLayout-Example.jpg)[UITableLayout](/docs/nl-nl/reference/engine/classes/UITableLayout)

## [Rasterindeling](#rasterindeling)[](#rasterindeling)

[UIGridLayout](/docs/nl-nl/reference/engine/classes/UIGridLayout)  plaatst broeder [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  in een raster van uniforme cellen van dezelfde grootte binnen hun bovenliggende container. Cellen worden toegevoegd per rij of kolom op basis van de [FillDirection](/docs/nl-nl/reference/engine/classes/UIGridLayout#FillDirection)  van de indeling totdat de volgende cel niet past, waarna een nieuwe rij of kolom begint. Voor verdere controle kun je de [FillDirectionMaxCells](/docs/nl-nl/reference/engine/classes/UIGridLayout#FillDirectionMaxCells)  eigenschap gebruiken om het maximale aantal cellen per rij of kolom in te stellen.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UIGridLayout-Example.jpg)

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/UIGridLayout.png)

Standaard plaatst [UIGridLayout](/docs/nl-nl/reference/engine/classes/UIGridLayout)  broeder [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  in volgorde van hun [LayoutOrder](/docs/nl-nl/reference/engine/classes/GuiObject#LayoutOrder)  waarbij lagere waarden vóór hogere waarden komen, en gelijke waarden worden gesorteerd afhankelijk van de volgorde waarin je ze hebt toegevoegd. Als je de [SortOrder](/docs/nl-nl/reference/engine/classes/UIGridStyleLayout#SortOrder)  van de indeling wijzigt naar [Enum.SortOrder.Name](/docs/nl-nl/reference/engine/enums/SortOrder#Name) , worden broeders alfabetisch gesorteerd.

Zodra je een [UIGridLayout](/docs/nl-nl/reference/engine/classes/UIGridLayout)  invoegt, overschrijft of beïnvloedt het de [Position](/docs/nl-nl/reference/engine/classes/GuiObject#Position)  en/of [Size](/docs/nl-nl/reference/engine/classes/GuiObject#Size)  van alle broeder UI-objecten, zodat wijzigingen in die eigenschappen binnen het [Eigenschappen](/docs/nl-nl/studio/properties)  venster of binnen een script niet het normale effect zullen hebben.

[UIGridLayout](/docs/nl-nl/reference/engine/classes/UIGridLayout)  respecteert alle [beperkingen](/docs/nl-nl/ui/size-modifiers)  die je plaatst op objecten binnen het raster. Bijvoorbeeld, als een object een [UISizeConstraint](/docs/nl-nl/reference/engine/classes/UISizeConstraint)  heeft met een [MinSize](/docs/nl-nl/reference/engine/classes/UISizeConstraint#MinSize)  eigenschap die hoger is dan de [CellSize](/docs/nl-nl/reference/engine/classes/UIGridLayout#CellSize)  eigenschap van het raster, zal het object meerdere cellen beslaan.

## [Tabelindeling](#tabelindeling)[](#tabelindeling)

[UITableLayout](/docs/nl-nl/reference/engine/classes/UITableLayout)  plaatst broeder [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  en hun kinderen in tabelvorm. De standaard [FillDirection](/docs/nl-nl/reference/engine/classes/UITableLayout#FillDirection)  van [Vertical](/docs/nl-nl/reference/engine/enums/FillDirection)  betekent dat broeders eerst in rijen worden geplaatst, en kinderen van die broeders worden horizontaal geplaatst om kolommen te vormen, zodat elke cel binnen een rij dezelfde hoogte heeft en elke cel binnen een kolom dezelfde breedte heeft.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/UITableLayout-Example.jpg)

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/UITableLayout.png)

Dit patroon imiteert de standaard HTML rij/kolomstructuur:

```

<table>

	<tbody>

		<tr> <!-- Rij1 -->

			<td>Label 1</td> <!-- TextLabel1 -->

			<td>Label 2</td> <!-- TextLabel2 -->

			<td>Label 3</td> <!-- TextLabel3 -->

		</tr>

		<tr> <!-- Rij2 -->

			<td>Label 4</td> <!-- TextLabel4 -->

			<td>Label 5</td> <!-- TextLabel5 -->

			<td>Label 6</td> <!-- TextLabel6 -->

		</tr>

		<tr> <!-- Rij3 -->

			<td>Label 7</td> <!-- TextLabel7 -->

			<td>Label 8</td> <!-- TextLabel8 -->

			<td>Label 9</td> <!-- TextLabel9 -->

		</tr>

	</tbody>

</table>

```

Tenzij je de [FillEmptySpaceColumns](/docs/nl-nl/reference/engine/classes/UITableLayout#FillEmptySpaceColumns)  of [FillEmptySpaceRows](/docs/nl-nl/reference/engine/classes/UITableLayout#FillEmptySpaceRows)  eigenschappen van de indeling inschakelt, bepaalt de grootte van de broeder [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  de afmetingen van de cellen. Bijvoorbeeld, een [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel)  van grootte [UDim2.new(0.25, 0, 0.1, 0)](/docs/nl-nl/reference/engine/datatypes/UDim2#new)  zal een tabelcel creëren van 25% breedte en 10% hoogte binnen de bovenliggende container.

Zodra je een [UITableLayout](/docs/nl-nl/reference/engine/classes/UITableLayout)  invoegt, overschrijft of beïnvloedt het de [Position](/docs/nl-nl/reference/engine/classes/GuiObject#Position)  en/of [Size](/docs/nl-nl/reference/engine/classes/GuiObject#Size)  van alle broeder UI-objecten, zodat wijzigingen in die eigenschappen binnen het [Eigenschappen](/docs/nl-nl/studio/properties)  venster of binnen een script niet het normale effect zullen hebben.

[UITableLayout](/docs/nl-nl/reference/engine/classes/UITableLayout)  respecteert en is responsief voor elke [UISizeConstraint](/docs/nl-nl/reference/engine/classes/UISizeConstraint)  die je plaatst op objecten binnen de tabel. Bijvoorbeeld, als een object een [UISizeConstraint](/docs/nl-nl/reference/engine/classes/UISizeConstraint)  heeft met een [MinSize](/docs/nl-nl/reference/engine/classes/UISizeConstraint#MinSize)  eigenschap binnen een headercel, zullen de rest van de cellen binnen de kolom dezelfde grootte hebben als de headercel.

Let op dat als de [MaxSize](/docs/nl-nl/reference/engine/classes/UISizeConstraint#MaxSize)  eigenschap de grootte van een cel beperkt om de toegewezen ruimte van een rij of kolom die breder is dan de cel te vullen, het object zich uitlijnt naar de bovenkant links van de cel.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
