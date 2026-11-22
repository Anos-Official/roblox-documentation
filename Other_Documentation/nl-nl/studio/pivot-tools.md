<!-- Source: https://create.roblox.com/docs/nl-nl/studio/pivot-tools -->

Pivot-tools | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Studio](/docs/nl-nl/studio)

# Pivot-tools

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De pivot -tools en gerelateerde eigenschappen geven je volledige controle over de punten waaromheen objecten draaien en vertalen.

## [Interactieve Studio-tools](#interactieve-studio-tools)[](#interactieve-studio-tools)

De interactieve Studio-tools bevinden zich in de werkbalk van het Model -tabblad.

 ![Pivot-tool gemarkeerd in de werkbalk van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Pivot.png)

Wanneer Pivot  is ingeschakeld, kun je het pivotpunt van een [deel](/docs/nl-nl/parts)  of [model](/docs/nl-nl/parts/models)  verplaatsen of draaien. Eenmaal ingesteld, vindt rotatie en schaling plaats rond het pivotpunt. Voor meer informatie, zie [een primaire part instellen](/docs/nl-nl/parts/models#stel-een-primair-onderdeel-in) .

De volgende diagrammen tonen voorbeeldlocaties van pivots in relatie tot de objectgrenzen.

Midden Hoek Buiten Objectgrenzen

![Een blauwe kubus met zijn pivotpunt in het midden van de kubus. Een groene cirkel vertegenwoordigt de rotatie van het object in relatie tot zijn pivotpunt.](https://prod.docsiteassets.roblox.com/assets/studio/pivot-tools/Edit-Pivot-Center-A.jpg)

Wanneer je de pivot van een [model](/docs/nl-nl/parts/models)  draait, draait ook de omtrekdoos van het model.

Oriëntatie = (0, 90, 0) Oriëntatie = (0, 135, 0) Oriëntatie = (0, 180, 0)

![Een model van een paarse, blauwe en rode blok met zijn pivotpunt op de rand van de omtrekdoos van het model. Een groene cirkel vertegenwoordigt de rotatie van het object in relatie tot zijn pivotpunt.](https://prod.docsiteassets.roblox.com/assets/studio/pivot-tools/Edit-Pivot-Model-A.jpg)

Je kunt een [PrimaryPart](/docs/nl-nl/reference/engine/classes/Model#PrimaryPart)  voor modellen specificeren, wat een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  binnen het model is dat je kunt gebruiken als basis voor de positie. Wat betreft pivotpunten:

1.

Wanneer je een [PrimaryPart](/docs/nl-nl/reference/engine/classes/Model#PrimaryPart)  aan een model toewijst, verandert de bestaande pivot in het pivotpunt van de [PrimaryPart](/docs/nl-nl/reference/engine/classes/Model#PrimaryPart) . Als je later de [PrimaryPart](/docs/nl-nl/reference/engine/classes/Model#PrimaryPart)  ongedaan maakt of wist, wordt het pivotpunt teruggezet naar het midden  van de omtrekdoos van het model.

2.

Als je de [PrimaryPart](/docs/nl-nl/reference/engine/classes/Model#PrimaryPart)  uit een model verwijdert , blijft het pivotpunt op dezelfde locatie en verandert niet  naar zijn vorige positie. Dit voorkomt een plotselinge "sprongetje" als je delen uit het model verwijdert.

Initiële Pivot Punt A. PrimaryPart Toegewezen B. PrimaryPart Verwijderd

![](https://prod.docsiteassets.roblox.com/assets/studio/pivot-tools/PrimaryPart-1.jpg)

### [Snap](#snap)[](#snap)

Het Snap -vakje, beschikbaar door de kleine hoekpijl op de Pivot -knop ingedrukt te houden, schakelt in of uit of het pivotpunt vastklikt aan hotspots  zoals hoeken, randen of centra wanneer je het verplaatst met de Bewerk Pivot -tool. Wanneer vastklikken is ingeschakeld, worden hotspots weergegeven als kleine magenta punten.

![](https://prod.docsiteassets.roblox.com/assets/studio/pivot-tools/Hotspots-Part.jpg) Hotspots op een deel

![](https://prod.docsiteassets.roblox.com/assets/studio/pivot-tools/Hotspots-Model.jpg) Hotspots op een model

### [Reset](#reset)[](#reset)

De Reset -knop verplaatst het pivotpunt naar het midden  van de omtrekdoos van een object of model. Deze bewerking is nuttig nadat je de samenstelling van een model hebt gewijzigd en je het pivotpunt in het midden van de nieuwe omtrekdoos wilt plaatsen.

 ![Pivot Reset-tool gemarkeerd in de werkbalk van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Pivot-Reset.png)

## [Pivot-eigenschappen](#pivot-eigenschappen)[](#pivot-eigenschappen)

Naast de interactieve tools kunnen pivotwaarden rechtstreeks worden ingesteld in het [Eigenschappen](/docs/nl-nl/studio/properties)  venster.

| Eigenschap | | Beschrijving |
| --- | --- |
| Oorspronkelijke Positie | | Huidige wereldlocatie van het object op basis van zijn pivotpunt in plaats van zijn omtrekdoos. Nuttig voor het instellen van de precieze locatie van een [Model](/docs/nl-nl/reference/engine/classes/Model) . |
| Oorspronkelijke Oriëntatie | | Huidige oriëntatie van het object rond zijn pivotpunt in plaats van zijn omtrekdoos. |
| Pivot Offset Positie | | Precieze locatie van de pivot ten opzichte van het object.¹ |
| Pivot Offset Oriëntatie | | Precieze pivotoriëntatie.¹ |
| Wereld Pivot Positie | | De precieze wereldlocatie van de pivot voor [Models](/docs/nl-nl/reference/engine/classes/Model)  zonder een [PrimaryPart](/docs/nl-nl/reference/engine/classes/Model#PrimaryPart) . Als een [PrimaryPart](/docs/nl-nl/reference/engine/classes/Model#PrimaryPart)  is ingesteld, gebruikt het model Pivot Offset Positie  omdat de pivot relatief wordt aan dat deel.¹ |
| Wereld Pivot Oriëntatie | | De precieze wereldoriëntatie voor [Models](/docs/nl-nl/reference/engine/classes/Model)  zonder een [PrimaryPart](/docs/nl-nl/reference/engine/classes/Model#PrimaryPart) . Als een [PrimaryPart](/docs/nl-nl/reference/engine/classes/Model#PrimaryPart)  is ingesteld, gebruikt het model Pivot Offset Oriëntatie  omdat de pivot relatief wordt aan dat deel.¹ |

 1  Het wijzigen van deze eigenschap zal het object niet verplaatsen of draaien.

## [Pivots manipuleren in scripts](#pivots-manipuleren-in-scripts)[](#pivots-manipuleren-in-scripts)

Naast de Studio-tools kunnen pivotpunten worden benaderd en gemanipuleerd in scripts.

| Functie of Eigenschap | | Beschrijving |
| [GetPivot()](/docs/nl-nl/reference/engine/classes/PVInstance#GetPivot) | | Vraagt de huidige wereldlocatie van het pivotpunt van een object op als een [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame) . Dit retourneert de positie van een object in 3D-ruimte, ongeacht of het een individueel deel of een [Model](/docs/nl-nl/reference/engine/classes/Model)  is. |
| [PivotTo()](/docs/nl-nl/reference/engine/classes/PVInstance#PivotTo) | | Verplaatst het object zodat zijn pivot zich op de opgegeven [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  bevindt. Dit maakt uniforme objectbeweging mogelijk van zowel individuele delen als modellen. |
| [BasePart.PivotOffset](/docs/nl-nl/reference/engine/classes/BasePart#PivotOffset) | | De [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  die de pivot-offset specificeert; effectief de offset van de pivot ten opzichte van de [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  van de [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) .² |
| [Model.WorldPivot](/docs/nl-nl/reference/engine/classes/BasePart#PivotOffset) | | Voor [Models](/docs/nl-nl/reference/engine/classes/Model)  zonder een [PrimaryPart](/docs/nl-nl/reference/engine/classes/Model#PrimaryPart) , de [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  die de pivot van het model in de wereldruimte specificeert. Als een [PrimaryPart](/docs/nl-nl/reference/engine/classes/Model#PrimaryPart)  is ingesteld, gebruikt het model [BasePart.PivotOffset](/docs/nl-nl/reference/engine/classes/BasePart#PivotOffset)  omdat de pivot relatief wordt aan dat deel.² |

 2  Het wijzigen van deze eigenschap zal het object niet verplaatsen of draaien.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
