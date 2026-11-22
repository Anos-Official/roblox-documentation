<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/rigid-accessories -->

Stijve accessoires | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Accessories and clothing
6. /
7. Stijve accessoires

# Stijve accessoires

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een hoog niveau overzicht van stijve accessoires op Roblox.

Maak en verkoop je eerste basis stijve accessoire.

Stijve accessoires  zijn 3D-objecten die aan bevestigingspunten rond het lichaam van een avatar-personage worden bevestigd. Wanneer gebruikers stijve accessoires kopen op de [Marketplace](https://www.roblox.com/catalog) , zoals rekwisieten, wapens en hoeden, kunnen ze de positie en rotatie van het item aanpassen ten opzichte van het bevestigingspunt, afhankelijk van het lichaamstype van hun avatar.

Er zijn twee hoofdlagen van een stijve accessoire die bepalen hoe de accessoire eruitziet en functioneert op het platform:

-

Mesh & texturen  die het visuele uiterlijk van de stijve accessoire vormen.

-

Bevestigingen  die bepalen hoe de accessoire aan het lichaam van het personage wordt bevestigd.

Hoewel je de eerste van deze lagen handmatig kunt maken in externe modelleringstools zoals [Blender](https://www.blender.org/)  of [Maya](https://www.autodesk.com/products/maya/overview) , hebben bevestigingen strikte configuratievereisten om te voldoen aan de technische [specificaties voor stijve accessoires](/docs/nl-nl/avatar/rigid-accessories/specifications)  van Roblox, die garanderen dat je stijve accessoires consistent functioneren van spel tot spel. Voordat je je eerste aangepaste stijve accessoire maakt, wordt aanbevolen om:

1.

De [essentiële componenten](#componenten-van-stijve-accessoires)  van een stijve accessoire te begrijpen en hoe ze samenwerken.

2.

Alle [bronnen](#bronnen)  te bekijken die Roblox biedt om het [creatieproces](#creatieproces)  te standaardiseren en te versnellen, zoals Blender- en Maya-projectbestanden, Studio-tools en stapsgewijze handleidingen.

3.

De [basis tutorial voor het maken van stijve accessoires](/docs/nl-nl/art/accessories/creating-rigid)  te volgen die behandelt hoe je een eenvoudig 3D-model kunt omzetten in een stijve accessoire.

Zodra je een aangepast stijve accessoire hebt, kun je het importeren in Studio en de Avatar Setup-tool gebruiken om je creatie om te zetten in een avatarasset die klaar is om te worden verkocht op de [Marketplace](/docs/nl-nl/marketplace) .

In tegenstelling tot stijve accessoires die niet vervormen wanneer ze aan een specifiek punt op de avatar worden bevestigd, rekken gelaagde accessoires zich uit en wikkelen ze zich om een doel totdat ze passen over het lichaam van het personage. Voor meer informatie, zie [Gelaagde accessoires](/docs/nl-nl/avatar/layered-accessories) .

## [Componenten van stijve accessoires](#componenten-van-stijve-accessoires)[](#componenten-van-stijve-accessoires)

Alle stijve accessoires zijn opgebouwd uit dezelfde fundamentele componenten die gebruikers in staat stellen om 3D-items met consistente gedragingen volgens  het [lichaamstype](/docs/nl-nl/avatar/rigid-accessories/specifications#lichaamschaal)  van het personage uit te rusten.

Gelaagde accessoires vereisen [aanvullende componenten](/docs/nl-nl/avatar/layered-accessories)  om het gelaagde effect op het 3D-item toe te passen.

### [Mesh onderdeel](#mesh-onderdeel)[](#mesh-onderdeel)

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Mesh-Bow-Example.png) Mesh-object van de boog stijve accessoire.

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Mesh-Hair-Example.png) Mesh-object van de haar stijve accessoire.

Alle stijve accessoires vereisen een enkel mesh-object dat de geometrie van de accessoire vertegenwoordigt. In Studio wordt dit mesh-object weergegeven als een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  genest onder een enkele [Model](/docs/nl-nl/reference/engine/classes/Model) .

### [Texturen](#texturen)[](#texturen)

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Texture-Bow-Example.png)  2D textuurkaart voor de boog stijve accessoire.

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Texture-Hair-Example.png)  2D textuurkaart voor de haar stijve accessoire.

Texturen zijn afbeeldingsbestanden die het oppervlak van je stijve accessoire definiëren. Je kunt texturen maken binnen een textuurverfprogramma of 3D-modelleringssoftware.

In Studio moet je texturen importeren als afbeeldingsbestanden en ze instellen op [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) -objecten door een kind [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance) -object of de [TextureID](/docs/nl-nl/reference/engine/classes/MeshPart#TextureID) -eigenschap van het mesh.

### [Bevestigingen](#bevestigingen)[](#bevestigingen)

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Attachment-Bow-Example.png)  Het bevestigingspunt van de boog maakt het mogelijk dat de boog aan de rug van een personage wordt bevestigd.

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Attachment-Hair-Example.png)  Het bevestigingspunt van het haar maakt het mogelijk dat het haar aan het hoofd van een personage wordt bevestigd.

Bevestigingspunten definiëren waar accessoires aan het lichaam van een personage worden bevestigd. In Studio worden bevestigingspunten weergegeven door [Attachment](/docs/nl-nl/reference/engine/classes/Attachment) -objecten.

Je kunt automatisch bevestigingspunten genereren voor je stijve accessoires met behulp van de [Accessory Fitting Tool](/docs/nl-nl/avatar/accessory-fitting-tool) .

## [Creatieproces](#creatieproces)[](#creatieproces)

Bij het ontwerpen van een stijve accessoire in [Blender](https://www.blender.org/)  of [Maya](https://www.autodesk.com/products/maya/overview)  moet je alle avatarcomponenten exporteren in een enkele .fbx  of .gltf  voor import in Studio. Aangezien 3D-creatie geen lineair proces is en altijd herhaling en testen vereist, kan het proces van het maken van een stijve accessoire verschillen tussen individuen en verschillende creatieworkflows.

Over het algemeen volgt het creatieproces de volgende workflow:

Workflow voor Stijve Accessoires![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Workflow-Rigid.png)

## [Bronnen](#bronnen)[](#bronnen)

Er zijn verschillende bronnen beschikbaar voor makers van alle achtergronden om te beginnen met het maken van stijve accessoires. Bekijk de volgende tabel voor specifieke onderwerpen en bronnen:

| Onderwerp | | Bronnen |
| --- | --- |
| Handleidingen | | [Creatie van stijve accessoires](/docs/nl-nl/art/accessories/creating-rigid) |
| Referentiebestanden | | [Referentiebestanden voor accessoires en kleding](/docs/nl-nl/art/modeling/project-files) |
| Technische specificaties | | [.FBX exportinstellingen](/docs/nl-nl/art/modeling/export-requirements)
[Algemene mesh-specificaties](/docs/nl-nl/art/modeling/specifications)
[Specificaties voor stijve accessoires](/docs/nl-nl/avatar/rigid-accessories/specifications)
[Marketplace beleid](/docs/nl-nl/marketplace/marketplace-policy) |
| Cosmetische creatie | | [Overzicht van stijve accessoires](/docs/nl-nl/avatar/rigid-accessories)
[Overzicht van gelaagde kleding](/docs/nl-nl/avatar/layered-accessories)
[Accessory Fitting Tool](/docs/nl-nl/avatar/accessory-fitting-tool)
[Specificaties voor stijve accessoires](/docs/nl-nl/avatar/rigid-accessories/specifications)
[Marketplace vereisten](/docs/nl-nl/marketplace/marketplace-policy) |
| Texturering | | [Textureringseisen](/docs/nl-nl/art/modeling/texture-specifications)
[PBR-texturen](/docs/nl-nl/art/modeling/surface-appearance) |
| Rigging en skinning | | [Overzicht van rigging en skinning](/docs/nl-nl/art/modeling/rigging)
[Vereisten voor humanoïde rigs](/docs/nl-nl/avatar/character-bodies/specifications#rigging)
[Rig gezichtsbeenderen](/docs/nl-nl/art/characters/facial-animation/create-basic-heads#rig-en-skin-het-hoofd)
[Automatische huidoverdracht](/docs/nl-nl/avatar/automatic-skinning-transfer)
[Skin gezichtsbeenderen](/docs/nl-nl/art/characters/facial-animation/create-basic-heads#skin-gewrichten) |
| Publiceren en Marketplace | | [Uploaden naar Marketplace](/docs/nl-nl/marketplace/publish-to-marketplace)
[Marketplace Beleid](/docs/nl-nl/marketplace/marketplace-policy)
[Vergoedingen en commissies](/docs/nl-nl/marketplace/marketplace-fees-and-commissions) |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
