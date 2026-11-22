<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/accessory-fitting-tool -->

Accessoire Pasvorm Tool | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)

# Accessoire Pasvorm Tool

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De Accessoire Pasvorm Tool  (APT) is een ingebouwde Studio-tool die je in staat stelt om je aangepaste modellen te testen op meerdere combinaties van karakterlichamen, animaties en accessoires voordat je het uiteindelijke [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  object genereert. Bij het testen van je accessoires kun je kleine pas- en positioneringswijzigingen aanbrengen om ervoor te zorgen dat je het best mogelijke resultaat krijgt.

De APT handelt automatisch de conversie van de aangepaste [Model](/docs/nl-nl/reference/engine/classes/Model)  of [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  op basis van je menu-selecties, waardoor je [gelaagde accessoires](/docs/nl-nl/avatar/layered-accessories)  of [starre accessoires](/docs/nl-nl/avatar/rigid-accessories)  kunt maken. Na het genereren van een accessoire creëert de APT de juiste [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  objecthiërarchie met eventuele bijgewerkte pasbewerkingen, stelt de juiste AccessoryType  eigenschap in en genereert de benodigde lichaamsbevestigingspunten.

![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Rigid-Example.png) Test en bewerk de oriëntatie en plaatsing van je starre accessoires.

![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Layered-Example.png) Test en bewerk de kooien van je gelaagde accessoires.

Als je van plan bent om een accessoire op de Marketplace te verkopen, zorg er dan voor dat het ontwerp van je accessoiremodel voldoet aan de [Marketplace-beleidsregels](/docs/nl-nl/marketplace/marketplace-policy) .

## [Accessoires instellen](#accessoires-instellen)[](#accessoires-instellen)

De eerste fase van de pasvormworkflow stelt je in staat om het type accessoire te configureren om de juiste pasvormtools correct in te vullen en het juiste accessoireobject te genereren. Bij het selecteren van het type accessoire zijn de volgende opties beschikbaar:

-

Kleding : Gelaagde accessoires die een binnen- en buitenkooi gebruiken om zich uit te rekken en rond een karakterlichaam en bestaande kledingstukken te wikkelen.

-

Accessoire : Starre accessoires die aan een specifiek bevestigingspunt van een karakterlichaam worden bevestigd en in die positie en oriëntatie statisch blijven.

Zorg ervoor dat je de [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  of [Model](/docs/nl-nl/reference/engine/classes/Model)  die je van plan bent om in een accessoire om te zetten, selecteerbaar hebt in je project voordat je de APT gebruikt. Ter referentie kun je de APT testen met een referentie [gelaagd accessoire](https://prod.docsiteassets.roblox.com/assets/accessories/reference-files/Additional-FBX-assets.zip)  of [starre accessoire](https://prod.docsiteassets.roblox.com/assets/accessories/reference-files/Bow-rigid.rbxm)  aangepast model.

Om je accessoires in te stellen:

1.

Klik in het Avatar  tabblad van de werkbalk op Accessoire  om de APT te openen. Het Accessoire Pasvorm Tool  paneel wordt weergegeven.

2.

In het paneel:

1.

Selecteer het Onderdeel  veld, selecteer vervolgens in het Explorer  venster het respectieve [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  of [Model](/docs/nl-nl/reference/engine/classes/Model)  object van je accessoire. Het tekstveld wordt gevuld met de naam van het object.

2.

Klik in het paneel op de Volgende  knop. De Asset Type  pagina wordt weergegeven.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating-rigid/AFT-Select-Mesh-Bow.png)

3.

Op de Asset Type  pagina:

1.

Selecteer het juiste type activa voor je accessoire:

-

Als je activa een gelaagd accessoire is, selecteer dan Kleding .

-

Als je activa een starre accessoire is, selecteer dan Accessoire .

2.

Gebruik het dropdownmenu om het AssetType  van je accessoire te kiezen.

3.

Stel het lichaamstype in op de [lichaamsverhouding](/docs/nl-nl/avatar/character-bodies/specifications#lichaamschaal)  die je hebt bepaald tijdens het sculpten en dimensioneren van het activa tijdens het creatieproces.

-

Classic : Stelt de schaal van het accessoire in op klassieke verhoudingen.

-

Proporties Slank : Stelt de AvatarPartScaleType  waarde in op ProportionsSlender .

-

Proporties Normaal : Stelt de AvatarPartScaleType  waarde in op ProportionsNormal .

Deze instelling heeft geen invloed op gelaagde accessoires, en het heeft alleen invloed op starre accessoires als het specifieke lichaamsdeel een andere AvatarPartScaleType  [StringValue](/docs/nl-nl/reference/engine/classes/StringValue)  object heeft. Voor meer informatie, zie [Starre Accessoires - AvatarPartScaleType](/docs/nl-nl/avatar/rigid-accessories/specifications#avatarpartscaletype) .

4.

Klik op de Volgende  knop. Een voorbeeldpaneel wordt weergegeven met een standaard karakter dat je accessoire draagt.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/AFT-Select-Type-Pants.png)  ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating-rigid/AFT-Add-Avatar-Panel-Bow.png)

## [Accessoires testen](#accessoires-testen)[](#accessoires-testen)

Nadat je de initiële details van het accessoire hebt opgegeven, toont de APT een voorbeeldpaneel. Met het voorbeeldpaneel kun je testen hoe je accessoire eruitziet op verschillende combinaties van karakterlichamen, starre accessoires, gelaagde accessoires, animaties en aangepaste activa in je spel. Als je problemen met de pasvorm van je accessoire opmerkt, kun je de [bewerk](#accessoire-pasvorm-bewerken)  tools gebruiken om kleine aanpassingen aan je accessoire te maken.

Op elk moment van het testproces kun je [een playtest starten](/docs/nl-nl/studio/testing-modes#spelen-testen)  om een instantie van je spel te lanceren waarbij je avatar wordt vervangen door het momenteel geselecteerde karakterlichaam en accessoires van de APT.

### [Met verschillende lichamen](#met-verschillende-lichamen)[](#met-verschillende-lichamen)

Je kunt verschillende karakterlichamen selecteren om de pasvorm en het dragen van je accessoires te testen. De APT biedt verschillende standaard karakterlichaam modellen die je kunt gebruiken om ervoor te zorgen dat je accessoires passen zoals verwacht.

![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Body-Example-1.png) Bazooka Bones karaktervoorbeeld

![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Body-Example-2.png) Magma Fiend karaktervoorbeeld

Om je accessoire met een ander karakterlichaam te testen:

1.

Navigeer in de catalogus van de tool naar Avatars  > Standaard .

2.

Klik op een van de karaktermodeltegels. Het voorbeeld wordt geladen met het geselecteerde karaktermodel.

1.

Als er twee karaktertegels zijn geselecteerd, klik dan op een geselecteerde tegel om deze te deselecteren.

2.

In de karaktervoorbeeld, klik  en sleep  om te roteren en rechtermuisklik  om te pannen om je karakter te inspecteren.

### [Met andere gelaagde accessoires](#met-andere-gelaagde-accessoires)[](#met-andere-gelaagde-accessoires)

Je kunt meerdere gelaagde accessoires selecteren om de pasvorm en layering van je kooienaccessoires te testen. De APT biedt verschillende standaard karaktermodellen die je kunt gebruiken om ervoor te zorgen dat je accessoires passen zoals verwacht.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Clothing-Examples.png)

Om je accessoire met een ander gelaagd accessoire te testen:

1.

Navigeer in de catalogus van de tool naar Kleding  > Standaard .

2.

Klik op een of meer van de beschikbare catalogusitems. Het karaktervoorbeeld wordt geladen met het geselecteerde kledingaccessoire.

1.

Klik in de catalogus op een actieve tegel om het activa te deselecteren.

2.

In de karaktervoorbeeld, sleep  en drop  de accessoireboxen om de laagvolgorde te wijzigen.

3.

In de karaktervoorbeeld, klik  en sleep  om te roteren en rechtermuisklik  om te pannen om je karakter te inspecteren.

### [Met animaties](#met-animaties)[](#met-animaties)

Je kunt verschillende animaties selecteren om de beweging van je accessoires te testen. De APT biedt verschillende standaard animatie-activa die je kunt gebruiken om ervoor te zorgen dat je accessoires passen zoals verwacht wanneer een model verschillende bewegingen uitvoert.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Animation-Examples.png)

Om je accessoire met verschillende animaties te testen:

1.

Navigeer in de catalogus van de tool naar Animaties  > Standaard .

2.

Klik op een van de animatie-activa tegels.

1.

Druk in de catalogus op het afspeel- en pauze-icoon om de afspeelcontrole te regelen.

2.

In de karaktervoorbeeld, klik  en sleep  om te roteren en rechtermuisklik  om te pannen om je karakter te inspecteren.

### [Met aangepaste activa](#met-aangepaste-activa)[](#met-aangepaste-activa)

Je kunt aangepaste karakterlichaam modellen, gelaagde accessoires en animaties die deel uitmaken van je werkruimte aan de APT voorbeeldcatalogus toevoegen. Gebruik deze functionaliteit om te verifiëren dat je accessoire werkt met andere aangepaste modellen of accessoires waarmee ze mogelijk in je spel interageren.

Om aangepaste activa toe te voegen:

1.

Klik op het ⊕ icoon naast de cataloguszoekopdracht. Er verschijnt een prompt waarmee je een ondersteund object kunt kiezen.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Custom-Asset-Icon.png)

2.

Selecteer een [Accessory](/docs/nl-nl/reference/engine/classes/Accessory) , [Model](/docs/nl-nl/reference/engine/classes/Model) , [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) , [Animation](/docs/nl-nl/reference/engine/classes/Animation)  of [Folder](/docs/nl-nl/reference/engine/classes/Folder)  binnen de 3D viewport of het Explorer  venster. Het activa wordt weergegeven in de overeenkomstige Aangepast  categorie.

## [Accessoire pasvorm bewerken](#accessoire-pasvorm-bewerken)[](#accessoire-pasvorm-bewerken)

De APT vult verschillende pasvormtools in, afhankelijk van het type accessoire dat je aan het maken bent.

### [Gelaagde accessoires](#gelaagde-accessoires)[](#gelaagde-accessoires)

Bij het bewerken van gelaagde accessoires worden de volgende tools in de viewport weergegeven:

| Icon | | Beschrijving |
| --- | --- |
| ![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Cage-Editing-Icon.png) | | Schakelt de [Kooi Bewerken](#kooi-bewerken)  interface in de viewport in voor het aanbrengen van kleine innerlijke of uiterlijke kooiwijzigingen aan je kleding. |
| ![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Autoskin-Icon.png) | | Schakelt [auto-skinning](/docs/nl-nl/avatar/automatic-skinning-transfer#automatische-skinning-overdracht-inschakelen)  in tussen EnabledPreserved  en EnabledOverride . Afhankelijk van het activa en de skinningkwaliteit kan auto-skinning betere resultaten opleveren.
-

EnabledPreserved  gebruikt de oorspronkelijke skinninggegevens van het activa die zijn toegepast in een modelleringsoftware.

-

EnabledOverride  draagt skinninggegevens over van de avatar-karakter in plaats van de oorspronkelijke skinninggegevens van het activa te gebruiken.

 |
| ![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Expand-Button.png) | | Toont een knop om Mannequin in Beeld te Brengen  die de mannequin in het midden van de camera plaatst. |
| ![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Center-Mannequin.png) | | Centreert de camera op de mannequin. |

#### [Kooi bewerken](#kooi-bewerken)[](#kooi-bewerken)

Wanneer de Kooi Bewerken interface is ingeschakeld, worden aanvullende tools in de viewport weergegeven samen met de vertices van de geselecteerde kooi boven de mannequin. Dit stelt je in staat om positionele bewerkingen aan de kooi aan te brengen en te veranderen hoe een gelaagd accessoire op een karakterlichaam past.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Cage-Editing-Example.png)

Je kunt deze kooi bewerkingstools gebruiken voor kleine tot gematigde kooi-bewerkingen, maar als je activa grote pas- of sculptuurwijzigingen vereisen, wordt aanbevolen om de kooi-meshes rechtstreeks in een derde-partij modelleringsoftware te bewerken en vervolgens het bijgewerkte model opnieuw in Studio te importeren.

Gebruik de volgende kooi bewerkingstools om te helpen visualiseren en bewerken van eventuele kooi-vertices:

| Icon | | Beschrijving |
| ![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Cage-Editing-Icon.png) | | Schakelt de selectie voor de binnen- en buitenkooi-vertices in. Wanneer geselecteerd, zijn de vertices van die specifieke kooi beschikbaar om te bewerken. |
| ![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Autoskin-Icon.png) | | Stelt de straal van invloed in bij het bewerken van vertices van de kooi-mesh. Bij het bewerken van een kooi-vertex volgen nabijgelegen vertices de wijzigingen voor efficiënte kooi-bewerking.

Een hogere Falloff Distance past invloed toe op vertices verder weg van de oorsprong. |
| ![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Expand-Button.png) | | Toont aanvullende knoppen:
-

Breng Mannequin in Beeld - centreert de camera op de mannequin.

-

Reset Binnen/Buiten Kooi - reset eventuele wijzigingen die zijn aangebracht aan de geselecteerde kooi.

 |
| ![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Center-Mannequin.png) | | Stelt de opaciteit van de mesh of de kooi-vertices in, zodat je beter bepaalde vertices en hoeken van je gelaagde accessoire kunt zien en benaderen. |

Om wijzigingen aan te brengen in de vertices van de momenteel geselecteerde kooi:

1.

Schakel in de werkbalk de Verplaatsen  snapping uit. Dit stelt je in staat om gedetailleerde wijzigingen aan de positie van een vertex aan te brengen.

2.

Selecteer een vertex en gebruik de Verplaatsen  tool om deze opnieuw te positioneren. Wijzigingen aan de kooi worden onmiddellijk toegepast en weergegeven in het voorbeeldpaneel.

1.

Gebruik de opaciteit schuifregelaars om de wijzigingen aan je kooi beter te visualiseren.

2.

Stel de Falloff Distance  in afhankelijk van het aantal vertices dat tegelijkertijd wordt aangepast.  ![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Edit-Vertex-Example.png)

### [Starre accessoires](#starre-accessoires)[](#starre-accessoires)

Bij het passen van starre accessoires verschijnt er een begrenzingsdoos rond de mannequin die de mogelijke plaatsing van dat specifieke type accessoire aangeeft. Je kunt objecten binnen deze begrenzingsdoos positioneren, roteren en schalen om ervoor te zorgen dat je accessoire op verschillende karaktermodellen past.

![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Bounding-Box-Example-1.png) Pas de pasvorm van je starre accessoire aan binnen de begrenzingsdoos.

![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Bounding-Box-Example-2.png) Als het accessoire buiten de juiste ruimte is, wordt de begrenzingsdoos rood.

### [Accessoire maken](#accessoire-maken)[](#accessoire-maken)

De APT past eventuele pasvormwijzigingen toe en genereert de juiste [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  instantie in de werkruimte, afhankelijk van het type accessoire dat is geselecteerd en eventuele toegepaste configuraties.

Wanneer je klaar bent om je accessoire te genereren, selecteer je Genereer MeshPart Accessoire .

![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/LC-Hierarchy.png) Hiërarchie gegenereerd voor gelaagde accessoires.

![](https://prod.docsiteassets.roblox.com/assets/accessories/accessory-fitting-tool/Rigid-Hierarchy.png) Hiërarchie gegenereerd voor starre accessoires.

Met een accessoire dat succesvol is gemaakt, kun je nu het volgende proberen:

-

Begin het proces van [uploaden en publiceren](/docs/nl-nl/marketplace/publish-to-marketplace)  van de accessoire naar de Marketplace.

-

Gebruik de accessoire in je huidige spel door deze uit te rusten op karaktermodellen met [HumanoidDescription](/docs/nl-nl/characters/appearance#handmatig-aangepast-uiterlijk) , of door de accessoire onder het juiste karakter [Model](/docs/nl-nl/reference/engine/classes/Model)  object te slepen en neer te zetten.

-

Sla de accessoire op in je [Toolbox](/docs/nl-nl/projects/assets/toolbox)  of maak deze openbaar in de [Creator Store](/docs/nl-nl/production/creator-store)  om deze binnen een van je spellen te gebruiken of te delen met andere makers.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
