<!-- Source: https://create.roblox.com/docs/nl-nl/art/modeling/cage-meshes/apply-deformation -->

Toepassen van vervorming | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Assets](/docs/nl-nl/assets)
4. /
5. Modellering
6. /
7. Cage meshes

# Toepassen van vervorming

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Zodra een doelformaat omhulde mesh en een gelaagde omhulde mesh in je ervaring zijn geïmporteerd, kun je een vervorming toepassen door beide [MeshParts](/docs/nl-nl/reference/engine/classes/MeshPart)  binnen een [Model](/docs/nl-nl/reference/engine/classes/Model)  te koppelen en een [WeldConstraint](/docs/nl-nl/reference/engine/classes/WeldConstraint)  toe te voegen.

 ![Een grijs gedraaide doelvorm, een rood-wit geblokte kubus, en de geblokte kubus opnieuw gevormd om overeen te komen met de gedraaide doelvorm, in Studio.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Apply-Deformation-Hero.png)

## [Vervorm een mesh](#vervorm-een-mesh)[](#vervorm-een-mesh)

Download de referentiebestanden om mee te volgen. Het Blender-project bevat elke vorm, en elke .fbx  importeert als een kant-en-klaar doel of gelaagde mesh met zijn omhulsels.

| ** Bestand** | | ** Beschrijving** |
| --- | --- |
| [Cage-Mesh-Examples.blend](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Cage-Mesh-Examples.blend) | | Een Blender-project met elk doel en gelaagde mesh in deze gids, met hun omhulsels. |
| [Cube_Target.fbx](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Cube_Target.fbx) | | Een kubusdoel, klaar om te importeren als een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  met een [WrapTarget](/docs/nl-nl/reference/engine/classes/WrapTarget) . |
| [Sphere_Target.fbx](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Sphere_Target.fbx) | | Een sferisch doel, klaar om te importeren als een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  met een [WrapTarget](/docs/nl-nl/reference/engine/classes/WrapTarget) . |
| [Cube-Flattened_Target.fbx](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Cube-Flattened_Target.fbx) | | Een afgevlakte kubusdoel, klaar om te importeren als een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  met een [WrapTarget](/docs/nl-nl/reference/engine/classes/WrapTarget) . |
| [Layered-Mesh1.fbx](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Layered-Mesh1.fbx) | | Een gelaagde mesh met binnen- en buitenomhulsels, klaar om te importeren als een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  met een [WrapLayer](/docs/nl-nl/reference/engine/classes/WrapLayer) . |
| [Layered-Mesh2.fbx](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Layered-Mesh2.fbx) | | Een tweede gelaagde mesh, klaar om te importeren als een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  met een [WrapLayer](/docs/nl-nl/reference/engine/classes/WrapLayer) . |

1.

Zorg ervoor dat je werkruimte twee 3D-objecten bevat: een doel [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  en een gelaagde [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) .

1.

Bevestig dat het doel een [WrapTarget](/docs/nl-nl/reference/engine/classes/WrapTarget)  heeft en de vervormende mesh een [WrapLayer](/docs/nl-nl/reference/engine/classes/WrapLayer) .

![De Studio Explorer toont de doel MeshPart met een kind WrapTarget-object.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/WrapTarget-Explorer.png) Doel: een [WrapTarget](/docs/nl-nl/reference/engine/classes/WrapTarget)

![De Studio Explorer toont de gelaagde MeshPart met een kind WrapLayer-object.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/WrapLayer-Explorer.png) Vervormende mesh: een [WrapLayer](/docs/nl-nl/reference/engine/classes/WrapLayer)

2.

(Optioneel) Als je meerdere vervormingen test of toepast, maak dan een kopie van je gelaagde mesh om ervoor te zorgen dat je later een originele kopie hebt.

2.

In de Explorer, koppel zowel de doel- als de gelaagde [MeshParts](/docs/nl-nl/reference/engine/classes/MeshPart)  in één [Model](/docs/nl-nl/reference/engine/classes/Model) .

 ![De Studio Explorer toont de doel- en gelaagde MeshParts gegroepeerd in één Model.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Group-And-Align.png)

3.

Voeg een [WeldConstraint](/docs/nl-nl/reference/engine/classes/WeldConstraint)  toe aan de gelaagde [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) , en:

1.

Stel Part0  in op de gelaagde mesh.

2.

Stel Part1  in op de doelmesh.

 ![De WeldConstraint-eigenschappen met Part0 ingesteld op de gelaagde mesh en Part1 ingesteld op de doel.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/WeldConstraint-First-Layer.png)

4.

In het eigenschappenvenster, wijzig [WrapLayer.Order](/docs/nl-nl/reference/engine/classes/WrapLayer#Order)  van de standaardwaarde naar een ander nummer, zoals 2  of 5 .

1.

Het wijzigen van deze eigenschap activeert de vervorming in de 3D-werkruimte, zodat de gelaagde mesh zich vormt naar de vorm van het doel.

2.

Als de volgorde onjuist is met andere lagen, zoals een T-shirt dat over een trui valt, kun je deze eigenschap op elk moment wijzigen.

 ![De WrapLayer-eigenschappen met de Order-eigenschap ingesteld.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/WrapLayer-Order-Property.png)

5.

(Optioneel) De vervorming blijft behouden nadat deze is berekend, zodat je de gedupliceerde gelaagde mesh en de [WeldConstraint](/docs/nl-nl/reference/engine/classes/WeldConstraint)  kunt verwijderen en [WrapLayer.Order](/docs/nl-nl/reference/engine/classes/WrapLayer#Order)  kunt resetten, waardoor er een enkele vervormde mesh overblijft. Dit is nuttig om je werkruimte te vereenvoudigen bij het toepassen van meerdere vervormingen.

 ![Een grijze kubusdoel naast de geblokte gelaagde mesh die erop vervormd is, in Studio.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Basic-Deformation.png)

6.

Experimenteer verder. Probeer de referentiegelaagde meshes op de andere doelvormen te vervormen, of [vervorm meerdere meshes naar een enkel doel](#vervorm-meerdere-meshes-naar-een-enkel-doel) .

## [Vervorm meerdere meshes naar een enkel doel](#vervorm-meerdere-meshes-naar-een-enkel-doel)[](#vervorm-meerdere-meshes-naar-een-enkel-doel)

Je kunt blijven gelaagde meshes aan een doel toevoegen door het proces van het toevoegen van een gelaagde mesh en een lasverbinding te herhalen. Elke keer dat een gelaagde mesh aan een doel wordt toegevoegd, berekent Roblox het oppervlak van de mesh opnieuw, zodat je voortdurend aan je doelmesh kunt toevoegen.

Elke mesh die je op een doel stapelt, moet dezelfde UV-indeling delen als het doel. Roblox koppelt elke laag aan het doel op basis van UV, dus niet-overeenkomende UV's vervormen niet correct.

1.

Met je bestaande vervormde mesh in de werkruimte, voeg een nieuwe gelaagde [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  toe aan je [Model](/docs/nl-nl/reference/engine/classes/Model) .

 ![De Studio Explorer toont een tweede gelaagde MeshPart die aan het Model is toegevoegd naast de eerste.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Add-Second-WrapLayer.png)

2.

Voeg een [WeldConstraint](/docs/nl-nl/reference/engine/classes/WeldConstraint)  toe aan de nieuwe gelaagde [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) , en:

1.

Stel Part0  in op de originele gelaagde mesh.

2.

Stel Part1  in op de nieuwe gelaagde mesh.

 ![De WeldConstraint-eigenschappen met Part0 ingesteld op de eerste gelaagde mesh en Part1 ingesteld op de tweede.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/WeldConstraint-Second-Layer.png)

3.

Wijzig [WrapLayer.Order](/docs/nl-nl/reference/engine/classes/WrapLayer#Order)  in het eigenschappenvenster. Het wijzigen van deze eigenschap activeert de vervorming, en de mesh vormt zich naar het doel. De [WrapLayer.Order](/docs/nl-nl/reference/engine/classes/WrapLayer#Order)  van elke laag bepaalt welke bovenop wordt weergegeven.

![De tweede laag die bovenop de eerste wordt weergegeven in Studio.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Ordering-Example-1.png) De [WrapLayer.Order](/docs/nl-nl/reference/engine/classes/WrapLayer#Order)  van de eerste laag is 1  en die van de tweede laag is 2 , zodat de tweede laag bovenop wordt weergegeven.

![De eerste laag die bovenop de tweede wordt weergegeven in Studio.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Ordering-Example-2.png) Het bijwerken van de [WrapLayer.Order](/docs/nl-nl/reference/engine/classes/WrapLayer#Order)  van de eerste laag naar 2 , en het instellen van de tweede laag op 1 , brengt de eerste laag bovenop.

## [Vervorm een accessoire op een avatar](#vervorm-een-accessoire-op-een-avatar)[](#vervorm-een-accessoire-op-een-avatar)

Alle Roblox-avatar delen dezelfde standaard lichaamsomhulsel. Omdat omhulsels op basis van UV worden gekoppeld, past een accessoire dat is omhulsel naar die gedeelde indeling op elk avatarlichaam. Let op dat de voorbeeldmeshes in deze gids hun eigen omhulsels gebruiken, zodat ze niet compatibel zijn met de standaard lichaamsomhulsel van Roblox.

![Hoofd- en bovenlichaam omhulsel meshes weergegeven als draadmodellen op een avatar.](https://prod.docsiteassets.roblox.com/assets/art/avatar/Cage-Mesh-Visual.png)  Hoofd- en Bovenlichaam omhulsel meshobjecten (draadmodel)

![De Explorer toont omhulselobjecten op elk van de 15 avatar lichaamsdelen.](https://prod.docsiteassets.roblox.com/assets/art/avatar/Cage-Mesh-Data-Model.png) Omhulselobjecten moeten bestaan voor elk van de 15 lichaamsdelen

Bij het maken van avatarpersonages en avataraccessoires is een vergelijkbaar proces van layering van toepassing op de lichaamsomhulsels van een [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid) -personage, en de gelaagde accessoire-pijplijn stelt de gelaagde mesh automatisch samen. Dit maakt het mogelijk om aan te passen aan verschillende lichaamstypes en het overdragen van skinning-gegevens via [WrapLayer.AutoSkin](/docs/nl-nl/reference/engine/classes/WrapLayer#AutoSkin) .

Als je je eigen aangepaste niet-Marktplaats-personages maakt die gebruikmaken van een unieke omhulsel / UV-oplossing, zie dan [Gelaagde accessoires op niet-R15](/docs/nl-nl/characters/appearance#gelaagde-accessoires-op-niet-r15) .

Voor een overzicht van het maken van je eerste gelaagde accessoire, zie de volgende video:

Voor de volledige avatarworkflow, zie [Gelaagde accessoires](/docs/nl-nl/avatar/layered-accessories) , de [Accessoire Pasvorm Tool](/docs/nl-nl/avatar/accessory-fitting-tool) , en [Automatische Skinning Overdracht](/docs/nl-nl/avatar/automatic-skinning-transfer) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
