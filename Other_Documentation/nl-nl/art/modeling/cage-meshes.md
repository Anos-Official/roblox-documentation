<!-- Source: https://create.roblox.com/docs/nl-nl/art/modeling/cage-meshes -->

Kooi-meshes | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Assets](/docs/nl-nl/assets)
4. /
5. Modellering
6. /
7. Cage meshes

# Kooi-meshes

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Kooi-meshes  zijn onzichtbare oppervlakken van een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  die andere ondersteunde meshes in staat stellen om zich over elkaar uit te rekken en te vervormen. Met kooi-meshes kun je een set meshes maken die dynamisch kunnen worden vergroot, hervormd en over een andere mesh van elke vorm of grootte kunnen worden gestapeld.

Ze drijven gelaagde accessoires  aan — 3D-accessoires zoals jassen, jurken en vesten die zich aanpassen aan het lichaam van een karakter en natuurlijk op elkaar stapelen — en je kunt ze ook toepassen op elke [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) , zolang alle kooi-meshes [dezelfde UV-mapping delen](#hoe-kooi's-paar) .

Hervorm volume Vervorm elke vorm Gelaagde accessoires

![Een mesh's buitenste kooi in Blender naast een gewone kubus en een checker-mesh waarvan het volume de kooi heeft hervormd in Studio.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Outer-Cage-Hero.png) Een buitenste kooi is een onzichtbaar oppervlak dat het volume van een mesh kan hervormen.

Een kooi-mesh is een vereenvoudigde kopie van een render-mesh die een omhulseloppervlak definieert. In tegenstelling tot Roblox's [botsingsysteem](/docs/nl-nl/workspace/collisions) , dat universeel werkt, kunnen kooi-meshes alleen werken met andere gepaarde kooi-meshes.

Om één mesh over een andere te passen, koppelt Roblox de vertices van de ene kooi aan die van de andere op basis van hun UV-coördinaten, en hervormt vervolgens de render-mesh zodat de kooi overeenkomt met de doelkooi. Kooi-meshes worden doorgaans geconfigureerd in een modelleringstool zoals [Blender](https://www.blender.org)  of [Maya](https://www.autodesk.com/products/maya/overview) .

In specifieke gevallen kun je ook kooi-meshes programmatisch creëren en hervormen tijdens runtime, zoals in ervaringen die gebruikers in staat stellen om avatar-items te bouwen en aan te passen. Zie [Avatar in-experience creatie](/docs/nl-nl/avatar/in-experience-creation) .

## [Componenten van kooi-meshes](#componenten-van-kooi-meshes)[](#componenten-van-kooi-meshes)

In Studio zijn kooi-meshes kinderen van een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  en worden ze weergegeven door afstammelingen van de [BaseWrap](/docs/nl-nl/reference/engine/classes/BaseWrap) -klasse:

| Type kooi-mesh | | In Blender | | In Studio |
| --- | --- |
|

[WrapTarget](/docs/nl-nl/reference/engine/classes/WrapTarget)
 Het initiële gelaagde oppervlak dat andere gepaarde kooi-meshes kan targeten.
Elke vervorming van de kooi vereist een doel-mesh.

 | | ![De Blender Outliner toont een render-mesh met een enkele _OuterCage.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Blender-Outliner-Target.png)

Een render-mesh met een enkele _OuterCage  mesh.

 | | ![De Studio Explorer toont een MeshPart met een kind WrapTarget-object.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/WrapTarget-Explorer.png)

Een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  met een kind [WrapTarget](/docs/nl-nl/reference/engine/classes/WrapTarget) .

 |
|

[WrapLayer](/docs/nl-nl/reference/engine/classes/WrapLayer)
 Laat zijn ouder [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  zich wikkelen rond een [WrapTarget](/docs/nl-nl/reference/engine/classes/WrapTarget) , zoals een gelaagd kledingaccessoire dat zich om een avatar-lichaam wikkelt.
 Alle doelen en lagen moeten identieke UV's delen.

 | | ![De Blender Outliner toont een render-mesh met een _InnerCage en een _OuterCage.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Blender-Outliner-Layer.png)

Een render-mesh met een _InnerCage  en een _OuterCage  mesh.

 | | ![De Studio Explorer toont een MeshPart met een kind WrapLayer-object.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/WrapLayer-Explorer.png)

Een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  met een kind [WrapLayer](/docs/nl-nl/reference/engine/classes/WrapLayer) .

 |

Omdat een kooi zich gedraagt als een component van zijn ouder, is een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  de enige geldige ouder voor deze objecten. Je maakt kooi-meshes samen met je render-mesh in een modelleringstoepassing zoals [Blender](https://www.blender.org)  of [Maya](https://www.autodesk.com/products/maya/overview)  en importeert ze samen.

Wanneer je een model importeert dat kooi-meshes bevat, zorg ervoor dat Uses Cages  is ingeschakeld in de [3D Importer](/docs/nl-nl/studio/importer#importinstellingen)  zodat Studio de kooien detecteert en de kooi-objecten voor je aanmaakt.

## [Hoe kooien paren](#hoe-kooien-paren)[](#hoe-kooien-paren)

Roblox koppelt kooien op basis van hun UV-coördinaten  in plaats van op positie, zodat twee kooien die een UV-indeling delen over elkaar kunnen wikkelen, zelfs wanneer hun vormen verschillen. Dit is wat het mogelijk maakt dat een enkel accessoire past op lichamen van volledig verschillende vormen en maten zonder het voor elk afzonderlijk te herontwerpen.

 ![Een gedeelde UV-indeling in de Blender UV-editor, weergegeven als een uitgepakte kubus kruis.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/UV-Map.png)

De volgende vormen zijn volledig verschillend, maar ze delen allemaal dezelfde UV-kaart hierboven, zodat een enkele gelaagde mesh zich op elk van hen kan vervormen.

![Een kubus in de Blender viewport.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Cube-shape.png) Kubus

![Een bol in de Blender viewport.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Sphere-shape.png) Bol — gevormd uit een kubus

![Een afgevlakte, gedraaide vorm in de Blender viewport.](https://prod.docsiteassets.roblox.com/assets/modeling/cage-meshes/Flatten-Shape.png) Afgevlakt — gesculpteerd uit een kubus

## [Maak gelaagde assets](#maak-gelaagde-assets)[](#maak-gelaagde-assets)

Gebruik de volgende gidsen om gelaagde assets te maken. Elke gids bevat downloadbare bestanden en basisimplementatiestappen om mee te volgen.

-

[Maak kooien in Blender](/docs/nl-nl/art/modeling/cage-meshes/create-cages)  — maak de buitenste en binnenste kooien voor een model en importeer ze in Studio.

-

[Pas vervorming toe](/docs/nl-nl/art/modeling/cage-meshes/apply-deformation)  — vervorm een gelaagde mesh op een doel met een [WrapLayer](/docs/nl-nl/reference/engine/classes/WrapLayer) .

-

[Maak je eigen gelaagde accessoire](/docs/nl-nl/art/accessories/creating)  — maak een gelaagd accessoire met behulp van de door Roblox geleverde referentiekooien.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
