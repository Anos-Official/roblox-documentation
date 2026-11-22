<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/dynamic-heads -->

Dynamische hoofden | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Animations
6. /
7. Dynamic heads

# Dynamische hoofden

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Dynamische hoofden  zijn gemodelleerde avatar hoofden die gezichtsanimaties en aangepaste uitdrukkingen ondersteunen. Wanneer gebruikers dynamische hoofden kopen op de [Marketplace](https://www.roblox.com/catalog) , kunnen ze emotes activeren die zowel gezichts- als lichaamsanimaties combineren.

Er zijn vier hoofdlagen van een dynamisch hoofd die bepalen hoe het hoofd eruitziet en functioneert op het platform:

-

Mesh & texturen  die het visuele uiterlijk van het hoofd vormen.

-

Gegevens voor gezichtsanimatie  die bepalen hoe het gezicht van het personage beweegt en de persoonlijkheid en emoties van het personage uitdrukt.

-

Cage meshes  die bepalen hoe het hoofd van het personage gezichtsaccessoires bevestigt die vervormen met gezichtsuitdrukkingen, zoals gezichtsbeharing die meebeweegt wanneer het personage van gezichtsuitdrukking verandert.

-

Bevestigingen  die bepalen hoe het hoofd van het personage accessoires zoals haar en hoeden bevestigt.

Hoewel je elke laag handmatig kunt maken in externe modelleringstools zoals [Blender](https://www.blender.org/)  of [Maya](https://www.autodesk.com/products/maya/overview) , hebben sommige strikte configuratievereisten om te voldoen aan de technische [dynamische hoofd specificaties](/docs/nl-nl/avatar/dynamic-heads/specifications)  van Roblox, die garanderen dat je dynamische hoofd consistent animeert van spel tot spel. Voordat je je eerste aangepaste dynamische hoofd maakt, wordt aanbevolen om:

1.

De [essentiële componenten](#componenten-van-dynamische-hoofden)  van een dynamisch hoofd te begrijpen en hoe ze samenwerken.

2.

Alle [bronnen](#bronnen)  te bekijken die Roblox biedt om het [creatieproces](#creatieproces)  te standaardiseren en te versnellen, zoals Blender- en Maya-projectbestanden, Studio-tools en stapsgewijze handleidingen.

3.

De [basis tutorial voor het maken van dynamische hoofden](/docs/nl-nl/art/characters/facial-animation/create-basic-heads)  te volgen die behandelt hoe je gezichtsgewrichten toevoegt, skinning-gegevens toepast, gewrichten in uitdrukkingen poseert en poses op een hoofdmodel in Blender in kaart brengt.

Zodra je een aangepast dynamisch hoofd hebt, kun je het samen met een lichaam in Studio importeren en de Avatar Setup-tool gebruiken om je creatie om te zetten in een avatarasset die klaar is om te worden verkocht op de [Marketplace](/docs/nl-nl/marketplace) .

## [Componenten van dynamische hoofden](#componenten-van-dynamische-hoofden)[](#componenten-van-dynamische-hoofden)

Alle dynamische hoofden zijn opgebouwd uit dezelfde fundamentele componenten die gebruikers in staat stellen gezichtsaccessoires te bevestigen die zich uitstrekken, passen en zich over het hoofd van een doelpersonage met consistente gedragingen leggen.

### [Mesh onderdeel](#mesh-onderdeel)[](#mesh-onderdeel)

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Character-Head-Geo.png)  Masculiene dynamische hoofd mesh object.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Character-Head-Geo-2.png)  Feminiene dynamische hoofd mesh object.

Alle dynamische hoofden vereisen een enkel mesh-object dat de geometrie van het hoofd vertegenwoordigt. In Studio wordt dit mesh-object weergegeven als een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  object genest onder een enkele [Model](/docs/nl-nl/reference/engine/classes/Model) .

### [Texturen](#texturen)[](#texturen)

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Textures-Brown.png)  Texturen passen kleur en oppervlakte details toe op je karaktermodel.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Textures-Blue.png) De doorzichtigheid van een textuurafbeelding kan worden gecombineerd met de [MeshPart.Color](/docs/nl-nl/reference/engine/classes/MeshPart#Color)  om aangepaste huidskleuren op personages toe te passen.

Texturen zijn afbeeldingsbestanden die het oppervlak van het hoofd van je karakter definiëren. Je kunt texturen maken met een textuurverfprogramma of 3D-modelleringssoftware. In Studio moet je texturen importeren als afbeeldingsbestanden en ze instellen op [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  objecten door een kind [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  object of de [TextureID](/docs/nl-nl/reference/engine/classes/MeshPart#TextureID)  eigenschap van het mesh.

### [Gegevens voor gezichtsanimatie](#gegevens-voor-gezichtsanimatie)[](#gegevens-voor-gezichtsanimatie)

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Facial-Rig-Visual.png)  Elk avatar karakter gezicht is gemodelleerd en geskinnd om verschillende uitdrukkingen te creëren

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Facial-Properties.png) Elke pose is in kaart gebracht naar een posenaam binnen de Aangepaste Eigenschappen (Extra Attributen in Maya) van het Head_Geo object

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Facial-Animation-Timeline.png) Elke vereiste gezichtspositie wordt opgeslagen als een keyframe in de animatietijdlijn.

Gegevens voor gezichtsanimatie van de gezichtsgewrichten van het personage stellen avatars in staat om emoties uit te drukken met hun ogen, mond en tanden. Elk personage bevat gezichtsgewrichten, skinning-gegevens, animatietijdlijngegevens en in kaart gebrachte pose-gegevens die deze uitdrukkingen mogelijk maken. In Studio worden deze elementen voor gezichtsanimatie weergegeven door een [FaceControls](/docs/nl-nl/reference/engine/classes/FaceControls)  instantie.

### [Cage meshes](#cage-meshes)[](#cage-meshes)

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Cage-Mesh-Visual-DH.png)  Hoofd geometrie en cage mesh objecten (wireframe)

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Cage-Mesh-Data-Model-2.png) Cage objecten moeten bestaan voor elk van de 15 lichaamsdelen, inclusief het dynamische hoofd

Cage meshes stellen de onzichtbare buitenrand in voor gezichtsaccessoires om zich uit te rekken en over het hoofd van het personage te passen, waardoor gezichtsaccessoires vervormen terwijl het hoofd animeert en emoties toont. In Studio worden buitenste cage mesh objecten weergegeven door een [WrapTarget](/docs/nl-nl/reference/engine/classes/WrapTarget)  instantie.

Als je je eigen niet-sjabloon karaktermodel aan het cagen bent, is het belangrijk om een van Roblox's body cage [projectbestanden](/docs/nl-nl/avatar/resources#mannequin-modellen)  te gebruiken om ervoor te zorgen dat je een standaard cage mesh van Roblox gebruikt. Het verwijderen of toevoegen van vertices aan deze standaard mesh kan problemen veroorzaken met hoe gezichtsaccessoires vervormen en importeren.

### [Bevestigingen](#bevestigingen)[](#bevestigingen)

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/DH-Attachments-Visual.png)  Elk karakter heeft gemeenschappelijke bevestigingspunten voor het bevestigen van rigide cosmetica

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Attachments-Data-Model-2.png) Elk avatar karakter moet hun bijbehorende 19 bevestigingspunten bevatten, inclusief die op het dynamische hoofd

Bevestigingspunten stellen de specifieke punten in waar rigide accessoires en in-game te bevestigen objecten aan het hoofd van het personage worden bevestigd. Deze worden niet weergegeven op het platform, maar ze worden visueel weergegeven als sferen in 3D-modelleringssoftware wanneer je Roblox's R15 Rig en Bevestigingen  [projectbestand](/docs/nl-nl/avatar/resources#projectbestanden)  gebruikt.

Wanneer je een rig importeert met deze visuele representaties, worden de sferen gemaakt als [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  objecten met gestandaardiseerde namen.

Wanneer gebruikers een gelaagd accessoire dragen, is het gelaagde accessoire niet direct aan de bevestiging bevestigd, maar verwijst het wel naar het bijbehorende bevestigingspunt tijdens ragdoll- en verminkingsanimaties.

## [Creatieproces](#creatieproces)[](#creatieproces)

Bij het ontwerpen van een dynamisch hoofd in [Blender](https://www.blender.org/)  of [Maya](https://www.autodesk.com/products/maya/overview) , moet je alle avatarcomponenten exporteren in een enkele .fbx  of .gltf  voor import in Studio. Aangezien 3D-creatie geen lineair proces is en altijd herhaling en testen vereist, kan het proces van het creëren van een dynamisch hoofd verschillen tussen individuen en verschillende creatieworkflows. Sommigen kiezen ervoor om een gemodelleerd karaktermodel aan te passen om te voldoen aan de [dynamische hoofd specificaties](/docs/nl-nl/avatar/dynamic-heads/specifications)  van Roblox, terwijl anderen de voorkeur geven om er een vanaf nul te maken.

Over het algemeen volgt het creatieproces de volgende workflow:

Dynamisch Hoofd Workflow![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Workflow-DH.png)

Zorg ervoor dat alle assets die je maakt voldoen aan Roblox's [Community Standards](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards)  en eventuele toepasselijke [Marketplace-beleidsregels](/docs/nl-nl/marketplace/marketplace-policy) .

## [Bronnen](#bronnen)[](#bronnen)

Er zijn verschillende bronnen beschikbaar voor makers van alle achtergronden om te beginnen met het maken van dynamische hoofden. Bekijk de volgende tabel voor specifieke onderwerpen en bronnen:

| Onderwerp | | Bronnen |
| --- | --- |
| Tutorials | | [Basis tutorial voor het maken van dynamische hoofden](/docs/nl-nl/art/characters/facial-animation/create-basic-heads)
[Basis tutorial voor het maken van gezichtsaccessoires](/docs/nl-nl/art/characters/facial-animation/create-face-accessories) |
| Referentiebestanden | | [Avatar referenties en projectbestanden](/docs/nl-nl/avatar/character-bodies/project-files)
[Voorbeeld mesh/model objecten](/docs/nl-nl/art/modeling/project-files)
[Beste praktijken voor het cagen van dynamische hoofden](/docs/nl-nl/avatar/dynamic-heads/caging-best-practices)
[FACS pose referenties](/docs/nl-nl/avatar/dynamic-heads/facs-poses-reference) |
| Technische specificaties | | [Dynamische hoofd specificaties](/docs/nl-nl/avatar/dynamic-heads/specifications)
[Algemene mesh specificaties](/docs/nl-nl/art/modeling/specifications)
[Marketplace beleid](/docs/nl-nl/marketplace/marketplace-policy) |
| Cosmetische creatie | | [Overzicht van accessoires](/docs/nl-nl/avatar/rigid-accessories)
[Het maken van gezichtsaccessoires](/docs/nl-nl/art/characters/facial-animation/create-face-accessories)
[Accessoire Fitting Tool](/docs/nl-nl/avatar/accessory-fitting-tool)
[Accessoire specificaties](/docs/nl-nl/avatar/rigid-accessories/specifications)
[Marketplace vereisten](/docs/nl-nl/marketplace/marketplace-policy) |
| Texturering | | [PBR texturen](/docs/nl-nl/art/modeling/surface-appearance) |
| Rigging en skinning | | [Overzicht van rigging en skinning](/docs/nl-nl/art/modeling/rigging)
[Humanoïde rig vereisten](/docs/nl-nl/avatar/character-bodies/specifications#rigging)
[Rigging van gezichtsbotten](/docs/nl-nl/art/characters/facial-animation/create-basic-heads#rig-en-skin-het-hoofd)
[Skinning van gezichtsbotten](/docs/nl-nl/art/characters/facial-animation/create-basic-heads#skin-gewrichten)
[Automatische Skinning Transfer](/docs/nl-nl/avatar/automatic-skinning-transfer) |
| Animatie | | [Animeer dynamische hoofden](/docs/nl-nl/art/characters/facial-animation/animate-heads) |
| Testen en validatie | | [Test dynamische hoofden](/docs/nl-nl/avatar/dynamic-heads/test)
[Validatieproces](/docs/nl-nl/avatar/dynamic-heads/validate) |
| Publiceren en Marketplace | | [Uploaden naar Marketplace](/docs/nl-nl/marketplace/publish-to-marketplace)
[Marketplace beleid](/docs/nl-nl/marketplace/marketplace-policy)
[Vergoedingen en commissies](/docs/nl-nl/marketplace/marketplace-fees-and-commissions) |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
