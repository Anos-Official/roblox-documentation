<!-- Source: https://create.roblox.com/docs/nl-nl/art/modeling -->

Aangepaste 3D-assets | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Assets](/docs/nl-nl/assets)
4. /
5. Modellering

# Aangepaste 3D-assets

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Meshes zijn aangepaste 3D-assets  waarmee je de omgeving en personages van je game kunt personaliseren en stylen. In tegenstelling tot onderdelen, die je direct in Studio kunt maken, moet je een externe modelleringstoepassing zoals [Blender](https://www.blender.org)  of [Maya](https://www.autodesk.com/products/maya/overview)  gebruiken om meshes te ontwerpen en te modelleren, en deze vervolgens in Studio importeren. Studio vertegenwoordigt geïmporteerde meshes als [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  objecten, afstammelingen van de [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  klasse.

Veel 3D-assets bestaan uit verschillende meshes die aan een enkel [Model](/docs/nl-nl/reference/engine/classes/Model)  object zijn gekoppeld.

Meshes vallen doorgaans in een van de drie toepassingscategorieën in games:

-

Meshes voor het decoreren van de omgeving van je game , zoals planten, gebouwen en voertuigen.

-

Meshes voor individuele lichaamsdelen  voor avatars of niet-speler personages (NPC's).

-

Meshes voor cosmetische accessoires  die personages kunnen uitrusten en dragen, zoals kleding, rekwisieten en wapens.

Elke mesh type moet voldoen aan specificaties afhankelijk van hoe je de mesh op het platform gaat gebruiken. Bijvoorbeeld, terwijl alle meshes moeten voldoen aan algemene mesh-specificaties, moeten meshes voor personages ook voldoen aan personagespecificaties die rekening houden met rigging en skinning gegevens. Voor een volledige lijst van specificaties voor verschillende soorten meshes, zie [Resources](#resources) .

Bovendien, als je aan bepaalde accountvereisten voldoet, kun je collecties van meshes publiceren en verkopen die aan een enkel [Model](/docs/nl-nl/reference/engine/classes/Model)  object zijn gekoppeld. Bijvoorbeeld, je kunt avatar-klaar modellen op de Marketplace publiceren en een commissie verdienen voor elke verkoop, of je kunt modellen verkopen in de Creator Store en 100% van de netto-opbrengsten van elke transactie verdienen.

Voor meer informatie over het monetariseren van meshes, zie [Monetize avatar items](/docs/nl-nl/monetize-avatar)  en [Creator Store - Distribute and sell assets](/docs/nl-nl/production/creator-store#verspreiden-en-verkopen-van-assets) .

![Een rommelige interieurkamer met een kaars op de voorgrond en spookachtige binnenverlichting van de Mystery of Duvall Drive game](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Mystery-of-Duvall-Example.png) Gebruik aangepaste meshes en modellen om je omgevingen sfeer en diepte te geven

![Een zwevend buitenaards wezen in de ruimte, uit de Beyond The Dark game](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Beyond-The-Dark-Example.png) Ontwerp een aangepast personage dat uniek is voor jouw game

![Een Roblox-avatar die een glanzende pufferjack en jeans draagt](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Layered-Clothing-Example.png) Creëer aangepaste accessoires, kleding en personages die iedereen kan dragen en gebruiken

## [Ondersteunde 3D-assets](#ondersteunde-3d-assets)[](#ondersteunde-3d-assets)

Roblox ondersteunt veel soorten aangepaste 3D-assets, zolang ze voldoen aan de [algemene mesh-specificaties](/docs/nl-nl/art/modeling/specifications) . Een basis aangepaste 3D-asset bestaat uit ten minste één [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  object en één textuur:

![Een eenvoudige witte boom mesh zonder textuur](https://prod.docsiteassets.roblox.com/assets/art/Basic-Mesh-Example.png) Een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  object stelt de vorm en geometrie van de 3D-asset in

![Verschillende kleurkaarten die worden gebruikt om texturen toe te passen op de boomschors, en binnenste, middelste en buitenste bladeren](https://prod.docsiteassets.roblox.com/assets/art/Basic-Texture-Example.png) Een textuurafbeelding past een oppervlakte-uiterlijk en kleur toe

![De boom mesh en de afbeeldingskaarten gecombineerd om een enkele boom te creëren](https://prod.docsiteassets.roblox.com/assets/art/Basic-Mesh-Combined-Example.png) De mesh en textuur combineren om een unieke aangepaste 3D-asset te maken

Studio ondersteunt ook aangepaste 3D-assets die [rigging en skinning](#rigging-en-skinning)  gegevens, [PBR-texturen](#pbr-texturen) , en andere [Studio-gerelateerde objecten](#studio-gerelateerde-objecten)  zoals cage meshes en attachments bevatten. Veel van deze verschillende componenten zijn vereist als je avatar-personagemodellen of accessoires maakt.

### [Rigging en skinning](#rigging-en-skinning)[](#rigging-en-skinning)

Een gerigde mesh  is een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  object met een interne poseerbare skeletstructuur en botstructuur. Gerigde meshes stellen de mesh-oppervlakken in staat om te draaien en te bewegen waar interne botgewrichten binnen een model zijn geplaatst, zoals de knie of elleboog van een personage. Skinning van een gerigde mesh stelt de mesh in staat om organisch te buigen, imiterend de natuurlijke manier waarop gewrichten in het echte leven zouden bewegen.

Zonder skinning draait de hele hoofdmesh op een enkele as

Met skinning buigt de hoofdmesh natuurlijk bij de nek, en de onderkant van de nek blijft verbonden met de romp

Voor meer informatie over rigging en skinning, zie [Rigging en skinning](/docs/nl-nl/art/modeling/rigging) .

### [PBR-texturen](#pbr-texturen)[](#pbr-texturen)

Fysiek-gebaseerde rendering  (PBR) texturen stellen je in staat om realistische schaduwen en verlichting weer te geven door meerdere soorten textuurafbeeldingen, of kaarten , op een enkele 3D-asset te gebruiken. Het combineren van meerdere textuurkaarten kan kleur, ruwheid en reflectiviteit in elke verlichtingsomgeving nauwkeuriger simuleren, en kan de visuele elementen van je assets en omgeving verbeteren.

![Een realistisch uitziende bladachtige struik met schaduwen en diepte.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-Example-1.jpg)

![Een realistisch uitziende steen met mos op de top.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-Example-3.jpg)

Voor meer informatie over PBR-texturen, zie [PBR-texturen](/docs/nl-nl/art/modeling/surface-appearance) .

### [Studio-gerelateerde objecten](#studio-gerelateerde-objecten)[](#studio-gerelateerde-objecten)

Studio converteert automatisch bepaalde soorten objecten die in 3D-modelleringsbestanden worden aangetroffen naar specifieke werkruimte-objecten in de game. Deze worden meestal gebruikt bij het maken van een personage of accessoire, en het configureren van deze in je modelleringstoepassing kan soms de primaire manier zijn om deze Studio-objecten correct in te stellen.

De volgende objecten worden automatisch in Studio aangemaakt als ze door de 3D-importeur worden gedetecteerd:

-

[Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  - Aangemaakt wanneer Studio mesh-objecten detecteert die _Att  aan het einde van hun naam hebben.

-

[WrapTarget](/docs/nl-nl/reference/engine/classes/WrapTarget)  - Aangemaakt wanneer Studio mesh-objecten detecteert die _OuterCage  aan het einde van hun naam hebben.

-

[WrapLayer](/docs/nl-nl/reference/engine/classes/WrapLayer)  - Aangemaakt wanneer Studio een mesh-object detecteert met _InnerCage  en een vergelijkbaar genoemd mesh-object met _OuterCage  aan het einde van hun namen.

-

[FaceControls](/docs/nl-nl/reference/engine/classes/FaceControls)  - Aangemaakt wanneer Studio een avatar-personagehoofd en de juiste gezichtsanimatiegegevens in het model detecteert.

Voor meer informatie over hoe de [WrapTarget](/docs/nl-nl/reference/engine/classes/WrapTarget)  en [WrapLayer](/docs/nl-nl/reference/engine/classes/WrapLayer)  objecten meshes hervormen en stapelen, zie [Cage meshes](/docs/nl-nl/art/modeling/cage-meshes) .

## [Resources](#resources)[](#resources)

Er zijn verschillende bronnen beschikbaar voor makers van alle achtergronden om aan de slag te gaan met aangepaste 3D-assets.

Als je geïnteresseerd bent in specifieke onderwerpen over avatarcreatie, gebruik dan de volgende tabel om gidsen en bronnen te vinden die het beste bij jouw behoeften passen:

| Onderwerp | | Resources |
| --- | --- |
| Referentiebestanden | | [Voorbeeldmodellen, projectkits en sjablonen](/docs/nl-nl/art/modeling/project-files) |
| Technische specificaties | | [.FBX exportinstellingen](/docs/nl-nl/art/modeling/export-requirements)
[Algemene mesh-specificaties](/docs/nl-nl/art/modeling/specifications)
 [Avatarspecificaties](/docs/nl-nl/avatar/character-bodies/specifications)
[Accessoirespecificaties](/docs/nl-nl/avatar/rigid-accessories)
[Marketplace-beleid](/docs/nl-nl/marketplace/marketplace-policy) |
| Lichamen en kledingcreatie | | [Overzicht accessoires](/docs/nl-nl/avatar/rigid-accessories)
[Overzicht lichamen](/docs/nl-nl/avatar/character-bodies)
[Creëren van gezichtsaccessoires](/docs/nl-nl/art/characters/facial-animation/create-face-accessories)
[Accessoire Fitting Tool](/docs/nl-nl/avatar/accessory-fitting-tool)
[Accessoirespecificaties](/docs/nl-nl/avatar/rigid-accessories/specifications)
[Marketplace-vereisten](/docs/nl-nl/marketplace/marketplace-policy) |
| Texturering | | [Textuurspecificaties](/docs/nl-nl/art/modeling/texture-specifications)
[PBR-texturen](/docs/nl-nl/art/modeling/surface-appearance) |
| Rigging en skinning | | [Overzicht rigging en skinning](/docs/nl-nl/art/modeling/rigging)
[Basis mesh rigging](/docs/nl-nl/art/modeling/rig-a-simple-mesh)
[Rigging van gezichtsbotten](/docs/nl-nl/art/characters/facial-animation/create-basic-heads#rig-en-skin-het-hoofd)
[Skinning van gezichtsbotten](/docs/nl-nl/art/characters/facial-animation/create-basic-heads#skin-gewrichten)
[Avatarriggingvereisten](/docs/nl-nl/avatar/character-bodies/specifications#rigging)
[Automatische skinningoverdracht](/docs/nl-nl/avatar/automatic-skinning-transfer) |
| Gezichtsanimatie en live hoofden | | [Basis hoofdcreatie](/docs/nl-nl/art/characters/facial-animation/create-basic-heads)
[Creëren van gezichtsaccessoires](/docs/nl-nl/art/characters/facial-animation/create-face-accessories)
[FACS pose referenties](/docs/nl-nl/avatar/dynamic-heads/facs-poses-reference) |
| Testen en validatie | | [Calisthenics Tool](/docs/nl-nl/art/modeling/calisthenics-tool)
[Kledingvalidatietool](/docs/nl-nl/art/accessories/validation-tool) |
| Publiceren en Marketplace | | [Uploaden naar Marketplace](/docs/nl-nl/marketplace/publish-to-marketplace)
[Marketplace-beleid](/docs/nl-nl/marketplace/marketplace-policy)
[Vergoedingen en commissies](/docs/nl-nl/marketplace/marketplace-fees-and-commissions) |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
