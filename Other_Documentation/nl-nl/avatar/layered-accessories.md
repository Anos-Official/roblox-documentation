<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/layered-accessories -->

Gelaagde accessoires | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Accessories and clothing
6. /
7. Layered accessories

# Gelaagde accessoires

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een hoog niveau overzicht van gelaagde accessoires op Roblox.

Maak en verkoop je eerste basis gelaagde accessoire.

Gelaagde accessoires , vaak aangeduid als gelaagde kleding , zijn 3D-assets die zich uitstrekken en passen op het lichaam van een avatar volgens hun rigging armatuur en cage meshes. Wanneer gebruikers gelaagde accessoires op de Marketplace kopen, zoals jassen, jurken en cardigans, verwachten ze dat deze meebewegen met de animaties van het karakter en op de juiste manier over bestaande kledinglagen die het karakter draagt, worden geplaatst.

Er zijn drie hoofdlagen van een gelaagd accessoire die bepalen hoe het accessoire eruitziet en functioneert op het platform:

-

Mesh & texturen  die het visuele uiterlijk van het gelaagde accessoire vormen.

-

Rigging armatuur  die bepaalt hoe het karakter beweegt en animeert met het gelaagde accessoire.

-

Cage meshes & attachments  die bepalen hoe het gelaagde accessoire zich uitstrekt, past en over het lichaam van het karakter wordt gelegd.

Hoewel je de meeste van deze lagen handmatig kunt maken in externe modelleringstools zoals [Blender](https://www.blender.org/)  of [Maya](https://www.autodesk.com/products/maya/overview) , hebben cage meshes en attachments strikte configuratievereisten om te voldoen aan de technische [specificaties voor gelaagde accessoires](/docs/nl-nl/avatar/layered-accessories/specifications)  van Roblox, die garanderen dat je gelaagde accessoires consistent functioneren van spel tot spel. Voordat je je eerste aangepaste gelaagde accessoire maakt, wordt aanbevolen om:

1.

De [essentiële componenten](#componenten-van-gelaagde-accessoires)  van een gelaagd accessoire te begrijpen en hoe ze samenwerken.

2.

Alle [bronnen](#bronnen)  te bekijken die Roblox biedt om het [creatieproces](#creatieproces)  te standaardiseren en te versnellen, zoals Blender- en Maya-projectbestanden, Studio-tools en stapsgewijze handleidingen.

3.

De [basis tutorial voor het maken van gelaagde accessoires](/docs/nl-nl/art/accessories/creating)  te volgen die behandelt hoe je je eigen avatar-klaar sweater vanaf nul in Blender maakt.

Zodra je een aangepast gelaagd accessoire hebt, kun je het importeren in Studio en de Avatar Setup-tool gebruiken om je creatie te verwerken tot een avatarasset die klaar is om te worden verkocht op de [Marketplace](/docs/nl-nl/marketplace) .

In tegenstelling tot gelaagde accessoires die zich uitstrekken en wikkelen over een doel totdat ze passen over het lichaam van het karakter, vervormen rigide accessoires niet en hechten ze zich alleen aan een specifiek punt op de avatar. Voor meer informatie, zie [Rigide accessoires](/docs/nl-nl/avatar/rigid-accessories) .

Als je een game-ontwikkelaar bent en op zoek bent naar informatie over het handmatig uitrusten of configureren van gelaagde accessoires binnen een spel, zoals het implementeren van gelaagde accessoires op een niet-standaard karaktermodel, zie dan [Karakter uiterlijk](/docs/nl-nl/characters/appearance) .

## [Componenten van gelaagde accessoires](#componenten-van-gelaagde-accessoires)[](#componenten-van-gelaagde-accessoires)

Alle gelaagde accessoires zijn opgebouwd uit dezelfde fundamentele componenten die gebruikers in staat stellen om 3D-items uit te rusten die zich uitstrekken, passen en over een doelkarakter en bestaande kledingstukken met consistente gedragingen kunnen worden gelegd ongeacht  het [lichaamstype](/docs/nl-nl/avatar/character-bodies/specifications#lichaamschaal)  van het karakter.

### [Mesh onderdeel](#mesh-onderdeel)[](#mesh-onderdeel)

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Mesh-Jumpsuit-Example.png)  Mesh-object van het gelaagde accessoire jumpsuit.

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Mesh-ShoulderPads-Example.png) Mesh-object van het gelaagde accessoire schouderpads.

Alle gelaagde accessoires vereisen een enkel mesh-object dat de geometrie van het accessoire vertegenwoordigt. In Studio wordt dit mesh-object weergegeven als een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  genest onder een enkele [Model](/docs/nl-nl/reference/engine/classes/Model) .

### [Texturen](#texturen)[](#texturen)

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Texture-Jumpsuit-Example.png)  2D textuurkaart voor het gelaagde accessoire jumpsuit.

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Texture-ShoulderPads-Example.png) 2D textuurkaart voor het gelaagde accessoire schouderpads.

Texturen zijn afbeeldingsbestanden die het oppervlak van je gelaagde accessoire definiëren. Je kunt texturen maken binnen een textuurverfprogramma of 3D-modelleringssoftware.

In Studio moet je texturen importeren als afbeeldingsbestanden en ze instellen op [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  objecten door een kind [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  object of de [TextureID](/docs/nl-nl/reference/engine/classes/MeshPart#TextureID)  eigenschap van de mesh.

### [Rigging armatuur](#rigging-armatuur)[](#rigging-armatuur)

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Rigging-Example.png)  Om ervoor te zorgen dat het gelaagde accessoire kan vervormen met het lichaam van het karakter, moet het gewogen zijn aan een rigging armatuur.

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Rigging-Pose-Example.png) Wanneer de rigging armatuur correct is ingesteld, beweegt en buigt het gelaagde accessoire zoals het karakter beweegt in de 3D-ruimte.

Binnen het fysieke lichaam van de avatar bevindt zich een niet-gerenderde rigging armatuur die het karakter in staat stelt zijn ledematen te articuleren. Vaak aangeduid als gewrichten of botten, omvat een rigging armatuur skinning-gegevens die verbindingen tussen ledematen organisch laten buigen, zoals de knieën en ellebogen van het karakter. In Studio worden deze rigging- en skinning-gegevens opgeslagen in de mesh-geometrie.

De rigging armatuur definieert ook hoe gelaagde accessoires bewegen en vervormen terwijl het karakter zich in de 3D-ruimte beweegt. Met rigging- en skinningtechnieken kun je gebieden van je gelaagde accessoires configureren om natuurlijk mee te bewegen met de gewrichten van het karakter, zoals een mouw van een shirt die de natuurlijke beweging van de elleboog en schouder van het karakter volgt tijdens een loopcyclus.

### [Cage meshes](#cage-meshes)[](#cage-meshes)

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Inner-Cage-Example.png)  De binnenste cage definieert het binnenoppervlak van het kledingstuk waar de kleding overheen wikkelt.

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Outer-Cage-Example.png) De buitenste cage definieert het buitenoppervlak van het kledingstuk waar extra kleding overheen kan wikkelen en lagen.

Cage meshes stellen de binnen- en buitenoppervlakken van een gelaagd accessoire in. Bijvoorbeeld, de binnenste cage van een t-shirt definieert hoe een gelaagd accessoire t-shirt zich uitstrekt en past over een karakterlichaam, en de buitenste cage definieert hoe andere gelaagde accessoires zich kunnen uitstrekken en passen over het t-shirt zelf.

In Studio worden deze cages weergegeven door [WrapLayer](/docs/nl-nl/reference/engine/classes/WrapLayer)  objecten.

### [Attachments](#attachments)[](#attachments)

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Attachment-Jumpsuit-Example.png)  Het bevestigingspunt van het gelaagde accessoire jumpsuit.

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Attachment-ShoulderPads-Example.png) Het bevestigingspunt van het gelaagde accessoire schouderpads.

Bevestigingspunten voor gelaagde accessoires bepalen aan welk lichaamsdeel het accessoire is bevestigd wanneer het karakterlichaam ragdolls of wordt afgebroken in een spel. In Studio worden bevestigingspunten weergegeven door [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  objecten.

Je kunt automatisch bevestigingspunten genereren voor je gelaagde accessoires met behulp van de [Accessory Fitting Tool](/docs/nl-nl/avatar/accessory-fitting-tool) .

## [Creatieproces](#creatieproces)[](#creatieproces)

Bij het ontwerpen van een gelaagd accessoire in [Blender](https://www.blender.org/)  of [Maya](https://www.autodesk.com/products/maya/overview) , moet je alle componenten van de avatar exporteren in een enkele .fbx  of .gltf  voor import in Studio. Aangezien 3D-creatie geen lineair proces is en altijd herhaling en testen vereist, kan het proces van het maken van een gelaagd accessoire verschillen tussen individuen en verschillende creatieworkflows.

Over het algemeen volgt het creatieproces de volgende workflow:

Workflow voor gelaagde accessoires![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Workflow-Layered.png)

## [Bronnen](#bronnen)[](#bronnen)

Er zijn verschillende bronnen beschikbaar voor makers van alle achtergronden om te beginnen met het maken van gelaagde accessoires. Bekijk de volgende tabel voor specifieke onderwerpen en bronnen:

| Onderwerp | | Bronnen |
| --- | --- |
| Handleidingen | | [Maak je eerste gelaagde accessoire](/docs/nl-nl/art/accessories/creating) |
| Referentiebestanden | | [Referentiebestanden voor accessoires en kleding](/docs/nl-nl/art/modeling/project-files) |
| Technische specificaties | | [.FBX exportinstellingen](/docs/nl-nl/art/modeling/export-requirements)
[Algemene mesh-specificaties](/docs/nl-nl/art/modeling/specifications)
[Specificaties voor accessoires](/docs/nl-nl/avatar/rigid-accessories/specifications)
[Marketplace beleid](/docs/nl-nl/marketplace/marketplace-policy) |
| Cosmetische creatie | | [Overzicht van accessoires](/docs/nl-nl/avatar/rigid-accessories)
[Overzicht van gelaagde kleding](/docs/nl-nl/avatar/layered-accessories)
[Maak gezichtaccessoires](/docs/nl-nl/art/characters/facial-animation/create-face-accessories)
[Accessory Fitting Tool](/docs/nl-nl/avatar/accessory-fitting-tool)
[Specificaties voor accessoires](/docs/nl-nl/avatar/rigid-accessories/specifications)
[Vereisten voor de Marketplace](/docs/nl-nl/marketplace/marketplace-policy) |
| Texturering | | [Textureringseisen](/docs/nl-nl/art/modeling/texture-specifications)
[PBR-texturen](/docs/nl-nl/art/modeling/surface-appearance) |
| Rigging en skinning | | [Overzicht van rigging en skinning](/docs/nl-nl/art/modeling/rigging)
[Vereisten voor humanoïde rigging](/docs/nl-nl/avatar/character-bodies/specifications#rigging)
[Rigging van gezichtsbotten](/docs/nl-nl/art/characters/facial-animation/create-basic-heads#rig-en-skin-het-hoofd)
[Auto skin transfer](/docs/nl-nl/avatar/automatic-skinning-transfer)
[Skin gezichtsbotten](/docs/nl-nl/art/characters/facial-animation/create-basic-heads#skin-gewrichten) |
| Testen en validatie | | [Calisthenics-tool](/docs/nl-nl/art/modeling/calisthenics-tool)
[Validatietool voor kleding](/docs/nl-nl/art/accessories/validation-tool) |
| Publiceren en Marketplace | | [Uploaden naar Marketplace](/docs/nl-nl/marketplace/publish-to-marketplace)
[Marketplace beleid](/docs/nl-nl/marketplace/marketplace-policy)
[Vergoedingen en commissies](/docs/nl-nl/marketplace/marketplace-fees-and-commissions) |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
