<!-- Source: https://create.roblox.com/docs/nl-nl/art/modeling/cage-meshes/create-cages -->

Maak kooien in Blender | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Assets](/docs/nl-nl/assets)
4. /
5. Modellering
6. /
7. Cage meshes

# Maak kooien in Blender

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een kooi-mesh  stelt je in staat om een onzichtbaar oppervlak te definiëren voor een zichtbaar render-mesh. In Studio kun je kooi-meshes combineren om een mesh rond te wikkelen, uit te rekken, te verkleinen of op andere manieren te vervormen over een doel-mesh.

Je moet deze soorten vervormbare meshes maken met behulp van een externe modelleringstool, zoals [Blender](https://www.blender.org)  of [Maya](https://www.autodesk.com/products/maya/overview) , en ze importeren in Studio. Deze tutorial gebruikt Blender en biedt een [Blender-projectbestand](#maak-een-kooi)  als referentie.

 ![Een render-mesh van een kubus met een checker-textuur in Blender naast een wireframe-kopie die door een kooi in een twist is hervormd.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Blender-Cage-Mesh-Hero.png)

Minimaal vereisen kooi-meshes een [WrapTarget](/docs/nl-nl/reference/engine/classes/WrapTarget)  en een [WrapLayer](/docs/nl-nl/reference/engine/classes/WrapLayer)  om te kunnen interageren. Voor een uitleg over de twee soorten kooi-meshes, zie [Kooi-types](#kooi-types) .

## [Kooi-types](#kooi-types)[](#kooi-types)

Bij het werken met kooimeshes zijn er twee soorten meshes: een doel-mesh  en een gelaagde mesh .

![Een eenvoudige grijze gedraaide vorm in Studio: de doel-mesh waar een gelaagde mesh naar vervormt.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Target-Mesh-Example.png) Doel-mesh

![Een rood-witte checker kubus in Studio: de gelaagde mesh in zijn geauthoreerde vorm, vóór vervorming.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Layered-Mesh-Example.png) Gelaagde mesh

![De checker kubus hervormd in de gedraaide doelvorm in Studio: het samengestelde resultaat.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Composed-Mesh-Example.png) Samengesteld resultaat

| Type kooi-mesh | | Configuratie in Blender | | Naamvereiste |
| --- | --- |
| ** Doel-mesh**
De basis-mesh waar een gelaagde mesh naar vervormt. | | ![De Blender Outliner toont een Cube-Target groep met een Cube render-mesh en een Cube_OuterCage kooi.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Blender-Outliner-Target.png)
-

Een gerenderd mesh-object.

-

Een buitenste kooi-mesh-object.

-

Een UV-kaart die overeenkomt met alle gelaagde meshes die over het doel zullen wikkelen en vervormen.

 | | Naam de kooi naar de render-mesh met de suffix _OuterCage , zoals Cube_OuterCage .
Een _OuterCage  op zichzelf importeert als een [WrapTarget](/docs/nl-nl/reference/engine/classes/WrapTarget) . |
| ** Gelaagde mesh**
Wikkelt en past zich aan rond een doel-mesh. | | ![De Blender Outliner toont een Gelaagde-Mesh groep met een Gelaagde-Mesh render-mesh en zijn Gelaagde-Mesh_InnerCage en Gelaagde-Mesh_OuterCage kooien.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Blender-Outliner-Layer.png)
-

Een gerenderd mesh-object.

-

Een binnenste kooi-mesh-object.

-

Een buitenste kooi-mesh-object.

 | | Naam elke kooi naar de render-mesh met de suffixes _InnerCage  en _OuterCage , zoals Shirt_InnerCage  en Shirt_OuterCage .
De twee kooi-meshes samen importeren als een [WrapLayer](/docs/nl-nl/reference/engine/classes/WrapLayer) . |

## [Maak een kooi](#maak-een-kooi)[](#maak-een-kooi)

Maak je kooi-meshes nadat je je render-mesh hebt gefinaliseerd. Als je later de topologie van de render-mesh of zijn UV's wijzigt, moet je mogelijk de kooi opnieuw aanpassen.

Als referentie, download het [.blend](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Cage-Mesh-Examples.blend)  project om deze exacte modellen en andere voorbeelden te zien. Dit project bevat drie configuraties van doel-kooi-meshes en twee configuraties van gelaagde kooi-meshes.

 ![De Blender Outliner voor het referentieproject, toont drie doel-meshes (kubus, afgevlakt en bol) en twee gelaagde meshes, elk met zijn kooien.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Blender-Project-Outliner.png)

### [Kooi een doel-mesh](#kooi-een-doel-mesh)[](#kooi-een-doel-mesh)

Het volgende voorbeeld maakt een buitenste kooi op de standaard Blender-kubus. De kubus heeft 10 loop cuts op elke as, wat extra vertices toevoegt voor later sculpten.

Om de buitenste kooi te maken:

1.

Dupliceer je render-mesh om als startpunt voor de kooi te gebruiken. In dit voorbeeld wordt de kubus gedupliceerd.

2.

Hernoem de duplicaat met de suffix _OuterCage , zoals Cube_OuterCage .

 ![De Blender Outliner toont een Cube render-mesh met een Cube_OuterCage kooi-object eronder.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Generic-Mesh-Rename.png)

3.

(Optioneel) Afhankelijk van de complexiteit van je gerenderde model, vereenvoudig de duplicaat-mesh naar een laag aantal vertices, aangezien een kooi een grove schaal moet zijn in plaats van een gedetailleerde kopie. Bijvoorbeeld, een gedetailleerd avatar-hoofd wordt omhuld met een veel eenvoudigere mesh:

![Een dicht avatar-karakter hoofd render-mesh in de Blender viewport.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Head-Example.png) Een avatar-karakter hoofd mesh kan tot 12.000 vertices bevatten.

![De laag-poly kooi-mesh van hetzelfde avatar-hoofd in de Blender viewport.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Cage-Example.png) Een avatar-karakter hoofd kooi bevat slechts 335 vertices.

4.

Pas de kooi aan zodat deze net buiten het render-oppervlak zit en het volledig omsluit, zo dicht mogelijk bij het oppervlak voor nauwkeurige layering. Overschakelen naar Wireframe  viewport shading helpt je de render-mesh eronder te zien.

 ![De buitenste kooi, weergegeven met een gele selectieomtrek, die de kubus render-mesh volledig omsluit in de Blender viewport.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Generic-Mesh-Resize.png)

5.

Bevestig in het UV Editing-tabblad dat de kooi-mesh UV-coördinaten heeft — je moet ervoor zorgen dat alle toekomstige gelaagde mesh-kooi's dezelfde UV-mapping delen.

![De UV-indeling van de buitenste kooi, die overeenkomt met de render-mesh.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/UV-OuterCage.png) Buitenste kooi UV's moeten overeenkomen met de UV's van alle gelaagde mesh-kooi's die erop zullen vervormen.

6.

Bevestig dat je Outliner de render-mesh toont met een enkele _OuterCage  eronder, die overeenkomt met de volgende configuratie.

 ![De Blender Outliner toont een Cube-Target groep met een Cube render-mesh en een Cube_OuterCage kooi.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Blender-Outliner-Target.png)

Je kunt ook een doel kooi met volledig andere geometrie maken. Zolang de kooi-mesh dezelfde UV-kaart deelt, kan een gelaagde mesh erop vervormen — dit is wat ervoor zorgt dat een enkele gelaagde mesh op veel verschillend gevormde doelen past. De volgende gedraaide mesh, bijvoorbeeld, gebruikt dezelfde UV-indeling als de kubus, zodat dezelfde gelaagde mesh op beide doelen kan vervormen.

![Een gedraaide-kubus doel-mesh in de Blender viewport naast zijn UV-indeling, die identiek is aan de UV-indeling van de kubusdoel.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Blender-Different-Target-Mesh-Example.png) Een anders gevormd doel waarvan de kooi dezelfde UV-indeling deelt.

Voeg geen kooi-vertices toe of verwijder ze nadat je een kooi hebt ingesteld, en wijzig de UV's niet. Destructieve bewerkingen breken vertex-pairing en veroorzaken importfouten of onjuiste vervorming.

### [Kooi een gelaagde mesh](#kooi-een-gelaagde-mesh)[](#kooi-een-gelaagde-mesh)

De gelaagde mesh is de mesh waarvan je verwacht dat deze zich vervormt naar de vorm van het doel. Een gelaagde mesh vereist zowel een binnenste als een buitenste kooi: de binnenste kooi  definieert het oppervlak dat zich aanpast aan het doel, en de buitenste kooi  definieert het oppervlak waarover extra lagen wikkelen.

Het kan het gemakkelijkst zijn om de kooi-mesh die je voor de doel-mesh hebt gemaakt te dupliceren om ervoor te zorgen dat al je kooi-meshes identieke UV's hebben. Vergeet niet dat je de geometrie van je kooi-meshes kunt wijzigen, maar niet de UV-mapping.

Om de binnenste en buitenste kooien te maken:

1.

Dupliceer je render-mesh om als startpunt voor de binnenste kooi te gebruiken.

1.

Als je al je doel-kooi-mesh hebt gemaakt, zorg er dan voor dat de UV's van je gelaagde kooi overeenkomen.

2.

Hernoem de duplicaat met de suffix _InnerCage , zoals Layered-Mesh_InnerCage .

3.

Pas de binnenste kooi aan zodat deze net binnen het render-oppervlak zit.

 ![De binnenste kooi van de gelaagde mesh, weergegeven als een oranje wireframe, die tegen het render-oppervlak zit in de Blender viewport.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Blender-InnerCage-Example.png)

4.

Dupliceer de _InnerCage  en hernoem de kopie met de suffix _OuterCage , zoals Layered-Mesh_OuterCage .

5.

Pas de buitenste kooi aan zodat deze net buiten het render-oppervlak zit en het volledig omsluit. De buitenste kooi is het oppervlak waarover extra lagen wikkelen.

 ![De buitenste kooi van de gelaagde mesh, weergegeven als een wireframe, die het render-oppervlak in de Blender viewport omsluit.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Blender-OuterCage-Example.png)

6.

Bevestig dat beide kooien dezelfde UV-indeling delen als de doel-mesh, aangezien Roblox de gelaagde mesh met het doel koppelt op basis van UV.

7.

Bevestig dat je Outliner de render-mesh toont met zowel een _InnerCage  als een _OuterCage  eronder, die overeenkomt met de volgende configuratie.

 ![De Blender Outliner toont een Gelaagde-Mesh groep met een Gelaagde-Mesh render-mesh en zijn Gelaagde-Mesh_InnerCage en Gelaagde-Mesh_OuterCage kooien.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Blender-Outliner-Layer.png)

### [Gelaagde accessoires voor avatars](#gelaagde-accessoires-voor-avatars)[](#gelaagde-accessoires-voor-avatars)

Roblox avatar-items, zoals karakterlichamen (doel-meshes) en Marketplace-kleding (gelaagde meshes), moeten allemaal een gemeenschappelijke kooi delen om universele compatibiliteit met accessoires en kleding te waarborgen. Als je avatars of gelaagde accessoires maakt, maak dan geen eigen kooi-meshes  — Roblox biedt [downloadbare kooi-sjablonen](/docs/nl-nl/avatar/resources#projectbestanden)  die je kunt aanpassen. Alternatief kun je de [Avatar Setup-tool](/docs/nl-nl/../../../avatar-setup)  van Roblox gebruiken om automatisch een door Roblox ondersteunde kooi voor je accessoires te genereren.

Voor meer informatie over het maken van gelaagde accessoires, zie de volgende bronnen:

-

[Overzicht van gelaagde accessoires](/docs/nl-nl/avatar/layered-accessories)

-

[Beste praktijken voor het kooien van gelaagde accessoires](/docs/nl-nl/avatar/layered-accessories/caging-best-practices)

## [Exporteer en importeer](#exporteer-en-importeer)[](#exporteer-en-importeer)

Voordat je exporteert, pas de [juiste exportinstellingen](/docs/nl-nl/art/modeling/export-requirements#blender)  voor Studio toe. Bij het exporteren van .fbx , stel Toepassen Schaal  in op FBX Eenheidsschaal  zodat je model dezelfde schaal behoudt in Studio. Voor meer informatie, zie [Schaal aanpassen (FBX)](/docs/nl-nl/art/blender#schaal-aanpassen-fbx) .

1.

Exporteer de render-mesh en zijn kooien samen als een enkel .fbx  of .gltf  bestand. Studio importeert kooien uit beide formaten gelijk, dus gebruik degene die je modelleringstoepassing het meest betrouwbaar exporteert.

2.

Importeer het bestand met de [3D Importer](/docs/nl-nl/studio/importer)  en zorg ervoor dat Gebruikt Kooien  is ingeschakeld.

1.

Als Gebruikt Kooien  niet standaard is ingeschakeld, detecteert de 3D Importer mogelijk je kooi-meshes niet. Controleer de [naamvereisten](#kooi-types)  en exporteer opnieuw.

 ![De 3D Importer preview toont de gelaagde mesh met zijn binnenste en buitenste kooien gedetecteerd en Gebruikt Kooien ingeschakeld.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Importer-Cages-Detected.png)

3.

Bevestig na het importeren dat Studio de verwachte objecten heeft gemaakt: een [WrapTarget](/docs/nl-nl/reference/engine/classes/WrapTarget)  voor een alleen-buitenste-kooi-mesh, of een [WrapLayer](/docs/nl-nl/reference/engine/classes/WrapLayer)  voor een mesh met beide kooien.

![De Studio Explorer toont een Cube-Target model met een Cube MeshPart en een kind WrapTarget object.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Explorer-TargetMesh.png) Een alleen-buitenste-kooi-mesh importeert met een [WrapTarget](/docs/nl-nl/reference/engine/classes/WrapTarget) .

![De Studio Explorer toont een Gelaagde-Mesh model met een Gelaagde-Mesh MeshPart en een kind WrapLayer object.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Explorer-LayerMesh.png) Een mesh met beide kooien importeert met een [WrapLayer](/docs/nl-nl/reference/engine/classes/WrapLayer) .

4.

Zodra je zowel een doel ([WrapTarget](/docs/nl-nl/reference/engine/classes/WrapTarget) ) als een vervormende mesh ([WrapLayer](/docs/nl-nl/reference/engine/classes/WrapLayer) ) hebt, zie [Toepassen van vervorming](/docs/nl-nl/art/modeling/cage-meshes/apply-deformation)  om de mesh op het doel te hervormen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
