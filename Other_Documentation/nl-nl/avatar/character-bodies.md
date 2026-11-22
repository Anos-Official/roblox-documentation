<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/character-bodies -->

Lichaamsdelen van personages | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Lichamen

# Lichaamsdelen van personages

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Lichaamsdelen  voor avatars zijn modellen met technische componenten die samenwerken om een personage te creëren dat kan interageren met objecten in de 3D-ruimte en cosmetica, kleding en accessoires kan dragen. Er zijn vier hoofdlagen van het avatarlichaam die bepalen hoe het personage eruitziet en beweegt op het platform:

-

Lichaamsdelen & texturen  die het visuele uiterlijk van het personage vormen.

-

Rigging armatuur  die bepaalt hoe het personage beweegt.

-

Gegevens voor gezichtsanimatie  in het hoofd van het personage die de persoonlijkheid en emoties van het personage uitdrukt.

-

Cage meshes & attachments  die bepalen hoe het personage accessoires bevestigt en kleding draagt.

Hoewel je elke laag handmatig kunt maken in externe modelleringstools zoals [Blender](https://www.blender.org/)  of [Maya](https://www.autodesk.com/products/maya/overview) , hebben sommige strikte configuratievereisten om te voldoen aan de technische [karakter specificaties](/docs/nl-nl/avatar/character-bodies/specifications)  van Roblox die garanderen dat je avatar consistent gedraagt van game tot game. Voordat je je eerste aangepaste lichaamsmodel maakt, wordt aanbevolen om:

1.

De [essentiële componenten](#componenten-van-het-lichaamsmodel)  van een avatar's lichaamsmodel te begrijpen en hoe ze samenwerken op het platform.

2.

Alle [bronnen](#bronnen)  te bekijken die Roblox biedt om het [creatieproces](#creatieproces)  te standaardiseren en te versnellen, zoals Blender- en Maya-projectbestanden, Studio-tools en stapsgewijze handleidingen.

3.

De [basis tutorial voor het maken van personages](/docs/nl-nl/art/characters/creating)  te volgen die gebruikmaakt van Roblox-sjablonen in samenwerking met veelvoorkomende Blender-modellerings- en textureringshulpmiddelen.

Zodra je een aangepast lichaamsmodel hebt, kun je het importeren in Studio en de Avatar Setup-tool gebruiken om je creatie om te zetten in een avatarasset die klaar is om te worden verkocht op de [Marketplace](/docs/nl-nl/marketplace) .

## [Componenten van het lichaamsmodel](#componenten-van-het-lichaamsmodel)[](#componenten-van-het-lichaamsmodel)

Alle lichaamsmodellen voor avatars bestaan uit verschillende fundamentele componenten die gebruikers de functionaliteit en flexibiliteit bieden om met hun wereld te interageren. Veel van deze componenten zijn nooit zichtbaar voor de gebruiker, maar ze maken krachtige avatarfuncties mogelijk die sociale en omgevingsinteracties verbeteren. Bij het maken van avatar-personages worden al deze componenten meestal eerst gemaakt in je modelleringsoftware en vervolgens omgezet naar hun juiste Roblox Studio-instantie bij import.

Elk avatar-personage bestaat uit de volgende gerenderde en niet-gerenderde componenten:

Gerenderd Niet-Gerenderd

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Component-Body-Parts.png)  15 afzonderlijke meshes van lichaamsdelen vormen de vorm en contouren van het personage.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Component-Texture-Map.png) Textuurafbeeldingskaarten passen een oppervlaktekleur en uiterlijk toe op de huid van het personage.

### [Lichaamsdelen](#lichaamsdelen)[](#lichaamsdelen)

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Body-Parts-Visual.png)  Elk avatar-personage bestaat uit 15 afzonderlijke meshobjecten

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Body-Parts-Data-Model.png) Deze meshes moeten een standaard naamgevingsconventie volgen

De fysieke geometrie van een avatar bestaat uit 15 afzonderlijke mesh-lichaamsdelen die de vorm en contouren van het personage definiëren:

-

Hoofd

-

Boven- en onderlichaam

-

Linker bovenarm, onderarm en hand

-

Rechter bovenarm, onderarm en hand

-

Linker bovenbeen, onderbeen en voet

-

Rechter bovenbeen, onderbeen en voet

In Studio worden deze geometrieën weergegeven als [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  objecten en zijn ze genest onder een enkel [Model](/docs/nl-nl/reference/engine/classes/Model) .

### [Texturen](#texturen)[](#texturen)

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Textures-Brown.png)  Texturen passen kleur en oppervlakte-details toe op je personagemodel.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Textures-Blue.png) De opaciteit van een textuurafbeeldingskaart kan worden gecombineerd met de [MeshPart.Color](/docs/nl-nl/reference/engine/classes/MeshPart#Color)  om aangepaste huidtinten op personages toe te passen.

Texturen zijn afbeeldingsbestanden die het oppervlakte-uiterlijk van je personage definiëren. Je kunt texturen maken met een textuurverfprogramma of 3D-modelleringssoftware. In Studio moet je texturen importeren als afbeeldingsbestanden en ze instellen op [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  objecten door een kind [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  object of de [TextureID](/docs/nl-nl/reference/engine/classes/MeshPart#TextureID)  eigenschap van de mesh.

Wanneer je delen van het lichaamsmodel van je personage textuurt, zorg er dan voor dat je personagemodel een bescheidenheidlaag over gevoelige gebieden bevat. Zie [Community Standards](https://en.help.roblox.com/hc/en-us/articles/203313410#safety)  voor meer informatie over de beleidsregels van Roblox.

### [Rigging armatuur](#rigging-armatuur)[](#rigging-armatuur)

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Rigging-Visual.png)  De rigging armatuur bevat ten minste 16 botten, 1 voor elk lichaamsdeel en een wortelbeen. Hogere-fidelity rigs kunnen tot 37 extra botten bevatten.

![](https://prod.docsiteassets.roblox.com/assets/avatar/specifications/High-Fidelity-LeftHand.png) Botten moeten een specifieke hiërarchie en naamgevingsconventie volgen

Binnen het fysieke lichaam van de avatar bevindt zich een niet-gerenderde rigging armatuur die het personage in staat stelt zijn ledematen te articuleren. Vaak aangeduid als gewrichten of botten, bevat een rigging armatuur skinning-gegevens die verbindingen tussen ledematen organisch laten buigen, zoals de knieën en ellebogen van het personage.

[Standaard avatar rigs](/docs/nl-nl/avatar/character-bodies/specifications#standaard-r15-rigs)  (R15) vereisen 15 poseerbare gewrichten om de 15 lichaamsdelen van het personage te articuleren. Als je echter hogere-fidelity personages wilt maken met een groter niveau van realisme, zijn er tot 37 extra optionele gewrichten voor [geavanceerde R15 rigs](/docs/nl-nl/avatar/character-bodies/specifications#geavanceerde-r15-rigs)  die je kunt maken voor gearticuleerde handen, schouders en wervelkolombewegingen.

In Studio wordt elk gewricht van de rigging armatuur weergegeven door [Bone](/docs/nl-nl/reference/engine/classes/Bone)  objecten die de lichaamsdeel [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  objecten van het personage met elkaar verbinden. [Bone](/docs/nl-nl/reference/engine/classes/Bone)  objecten moeten een specifieke hiërarchie en naamgevingsconventie volgen zodat de avatar correct functioneert in Studio en op de Marketplace. Voor meer informatie, zie [Rigging](/docs/nl-nl/avatar/character-bodies/specifications#rigging) .

### [Gegevens voor gezichtsanimatie](#gegevens-voor-gezichtsanimatie)[](#gegevens-voor-gezichtsanimatie)

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Facial-Rig-Visual.png)  Elk avatar-personage gezicht is gerigged en geskinnd om verschillende uitdrukkingen te creëren

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Facial-Properties.png) Elke pose is gekoppeld aan een posenaam binnen de Aangepaste Eigenschappen (Extra Attributen in Maya) van het Head_Geo object

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Facial-Animation-Timeline.png) Elke vereiste gezichtspositie wordt opgeslagen als een keyframe in de animatietijdlijn.

Gegevens voor gezichtsanimatie van de rigging armatuur van het personage of gezichtsgewrichten stellen avatars in staat om emoties uit te drukken met hun ogen, mond en tanden. Elk personage bevat gezichtsgewrichten, skinning-gegevens, animatietijdlijngegevens en gekoppelde posegegevens die deze uitdrukkingen mogelijk maken. In Studio worden deze gezichtsanimatie-elementen weergegeven door een [FaceControls](/docs/nl-nl/reference/engine/classes/FaceControls)  instantie.

### [Cage meshes](#cage-meshes)[](#cage-meshes)

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Cage-Mesh-Visual.png)  Hoofd- en bovenlichaam cage mesh-objecten (wireframe)

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Cage-Mesh-Data-Model.png) Cage-objecten moeten bestaan voor elk van de 15 lichaamsdelen

Cage meshes stellen de onzichtbare buitenrand in voor gelaagde accessoires om over lichaamsdelen te rekken en passen, waardoor kleding over modellen van verschillende vormen en maten kan passen zonder dat je het kledingitem elke keer opnieuw hoeft te modelleren. In Studio worden buitenste cage mesh-objecten weergegeven door een [WrapTarget](/docs/nl-nl/reference/engine/classes/WrapTarget)  instantie.

Als je je eigen niet-sjabloon personagemodel aan het cagen bent, is het belangrijk om een van Roblox's body cage [projectbestanden](/docs/nl-nl/avatar/resources#mannequin-modellen)  te gebruiken om ervoor te zorgen dat je een standaard cage mesh van Roblox gebruikt. Het verwijderen of toevoegen van vertices aan deze standaard mesh kan problemen veroorzaken met de pasvorm van de kleding en import.

### [Bevestigingen](#bevestigingen)[](#bevestigingen)

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Attachments-Visual.png)  Elk personage heeft gemeenschappelijke bevestigingspunten voor het uitrusten van rigide cosmetica

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Attachments-Data-Model.png) Elk avatar-personage moet hun bijbehorende 19 bevestigingspunten bevatten

Bevestigingspunten stellen de specifieke punten in waar rigide accessoires en in-game uitrustbare objecten aan het lichaam van het personage worden bevestigd. Deze worden niet gerenderd op het platform, maar worden visueel weergegeven als sferen in 3D-modelleringssoftware wanneer je gebruikmaakt van Roblox's R15 Rig and Attachments  [projectbestand](/docs/nl-nl/avatar/resources#projectbestanden) .

Wanneer je een rig importeert met deze visuele representaties, worden de sferen gemaakt als [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  objecten met gestandaardiseerde namen.

Wanneer gebruikers een gelaagd accessoire dragen, is het gelaagde accessoire niet direct aan de bevestiging bevestigd, maar verwijst het wel naar het bijbehorende bevestigingspunt tijdens ragdoll- en afgehaktanimaties.

## [Creatieproces](#creatieproces)[](#creatieproces)

Bij het ontwerpen van een lichaamsmodel in [Blender](https://www.blender.org/)  of [Maya](https://www.autodesk.com/products/maya/overview)  moet je alle avatarcomponenten exporteren in een enkele .fbx  of .gltf  voor import in Studio. Aangezien 3D-creatie geen lineair proces is en altijd herhaling en testen vereist, kan het proces van het maken van een avatar-personagemodel verschillen tussen individuen en verschillende creatieworkflows.

Over het algemeen volgt het creatieproces deze typische workflows:

Basiscreatie met Sjablonen
Pas een [personage lichaamsmodel-sjabloon](/docs/nl-nl/art/characters/creating)  aan dat al alle noodzakelijke componenten bevat.![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Workflow-Bodies-Templates.png)

Geavanceerde Creatie vanaf Nul
Maak personages vanaf nul, waardoor volledige aanpassing van de componenten van het avatar-personage mogelijk is.![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Workflow-Bodies-Traditional.png)

Zorg ervoor dat alle assets die je maakt voldoen aan Roblox's [Community Standards](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards)  en alle toepasselijke [Marketplace-beleidsregels](/docs/nl-nl/marketplace/marketplace-policy) .

## [Bronnen](#bronnen)[](#bronnen)

Er zijn verschillende bronnen beschikbaar voor makers van alle achtergronden om te beginnen met het maken van personages. Bekijk de volgende tabel voor specifieke onderwerpen en bronnen:

| Onderwerp | | Bronnen |
| --- | --- |
| Handleidingen | | [Basis tutorial voor het maken van personages](/docs/nl-nl/art/characters/creating) |
| Referentiebestanden | | [Avatar-referenties en projectbestanden](/docs/nl-nl/avatar/character-bodies/project-files)
[Voorbeeld mesh/modelobjecten](/docs/nl-nl/art/modeling/project-files) |
| Technische specificaties | | [.FBX exportinstellingen](/docs/nl-nl/avatar/character-bodies/export)
[Avatar specificaties](/docs/nl-nl/avatar/character-bodies/specifications)
[Algemene mesh specificaties](/docs/nl-nl/art/modeling/specifications)
[Accessoire specificaties](/docs/nl-nl/avatar/rigid-accessories/specifications)
[Marketplace beleid](/docs/nl-nl/marketplace/marketplace-policy) |
| Cosmetica creatie | | [Overzicht van accessoires](/docs/nl-nl/avatar/rigid-accessories)
[Creëren van gezichtaccessoires](/docs/nl-nl/art/characters/facial-animation/create-face-accessories)
[Accessoire Fitting Tool](/docs/nl-nl/avatar/accessory-fitting-tool)
[Accessoire specificaties](/docs/nl-nl/avatar/rigid-accessories/specifications)
[Marketplace vereisten](/docs/nl-nl/marketplace/marketplace-policy) |
| Texturering | | [Textureringseisen](/docs/nl-nl/art/modeling/texture-specifications)
[PBR-texturen](/docs/nl-nl/art/modeling/surface-appearance) |
| Rigging en skinning | | [Overzicht van rigging en skinning](/docs/nl-nl/art/modeling/rigging)
[Vereisten voor humanoïde rigs](/docs/nl-nl/avatar/character-bodies/specifications#rigging)
[Rigging van gezichtsbotten](/docs/nl-nl/art/characters/facial-animation/create-basic-heads#rig-en-skin-het-hoofd)
[Automatische Skinning Transfer](/docs/nl-nl/avatar/automatic-skinning-transfer)
[Skinning van gezichtsbotten](/docs/nl-nl/art/characters/facial-animation/create-basic-heads#skin-gewrichten) |
| Gezichtsanimatie en live hoofden | | [Basis hoofdcreatie](/docs/nl-nl/art/characters/facial-animation/create-basic-heads)
[Creëren van gezichtaccessoires](/docs/nl-nl/art/characters/facial-animation/create-face-accessories)
[FACS pose referenties](/docs/nl-nl/avatar/dynamic-heads/facs-poses-reference) |
| Testen en validatie | | [Calisthenics Tool](/docs/nl-nl/art/modeling/calisthenics-tool)
[Kledingvalidatietool](/docs/nl-nl/art/accessories/validation-tool) |
| Publiceren en Marketplace | | [Uploaden naar Marketplace](/docs/nl-nl/marketplace/publish-to-marketplace)
[Marketplace beleid](/docs/nl-nl/marketplace/marketplace-policy)
[Vergoedingen en commissies](/docs/nl-nl/marketplace/marketplace-fees-and-commissions) |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
