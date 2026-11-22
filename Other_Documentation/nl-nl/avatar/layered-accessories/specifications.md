<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/layered-accessories/specifications -->

Specificaties voor gelaagde accessoires | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Accessories and clothing
6. /
7. Layered accessories

# Specificaties voor gelaagde accessoires

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Gelaagde accessoires vereisen een specifieke set componenten en configuratiestandaarden om ervoor te zorgen dat ze kunnen rekken en passen op de lichamen van personages en bevatten optimalisaties voor prestaties en kwaliteit. Omdat je veel van deze vereisten moet toepassen terwijl je het gelaagde accessoire ontwerpt en modelleert in een extern modelleerprogramma zoals [Blender](https://www.blender.org/)  of [Maya](https://www.autodesk.com/products/maya/overview) , is het belangrijk om deze specificaties vroeg en vaak te bekijken terwijl je werkt.

Wanneer je klaar bent om je gelaagde accessoire te exporteren, raadpleeg dan alle [exportinstellingseisen](/docs/nl-nl/avatar/layered-accessories/export)  voor Blender en Maya.

Voor andere soorten 3D-modellen:

-

[Algemene mesh](/docs/nl-nl/art/modeling/specifications)  specificaties.

-

[Stijve accessoires](/docs/nl-nl/avatar/rigid-accessories/specifications)  specificaties.

## [Geometrie en budgetten](#geometrie-en-budgetten)[](#geometrie-en-budgetten)

-

Enkele mesh  - Gelaagde accessoires moeten een enkele mesh zijn.

-

Budgetten  - Gelaagde accessoires mogen niet meer dan 4k  driehoeken bevatten.

-

Waterdicht  - Alle geometrie moet waterdicht zijn zonder blootgestelde gaten of achterkantvlakken.

-

Gebruik quads  waar mogelijk. Vermijd vlakken met 5 of meer zijden.

-

Meshgrootte  - Meshes moeten voldoen aan de volgende maximale grootte-eisen (in studs, gecentreerd op het bevestigingspunt) afhankelijk van het type gelaagd accessoire dat je ontwerpt.

| Type asset | | Breedte (X) | | Hoogte (Y) | | Diepte (Z) |
| --- | --- |
| T-Shirt, Shirt, Trui, Jas, Broek, Korte broek, Jurk & Rok | | 8 | | 8 | | 8 |
| Wenkbrauw en Wimpers | | 1.5 | | 0.5 | | 0.5 |

## [Texturen](#texturen)[](#texturen)

-

Texturen voor gelaagde accessoires moeten voldoen aan de algemene [textuurspecificaties](/docs/nl-nl/art/modeling/texture-specifications)  van Roblox. Hoge resolutietexturen worden automatisch omgezet naar lagere resolutietexturen om de prestaties te optimaliseren.

-

Texturen voor gelaagde accessoires voor Marketplace-assets mogen niet groter zijn dan 2048x2048 resolutie.

## [Bevestigingspunten](#bevestigingspunten)[](#bevestigingspunten)

[Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  objecten voor gelaagde accessoires bepalen aan welk lichaamsdeel het accessoire is bevestigd wanneer het lichaam van het personage ragdoll of verminkt in een spel. Of je nu [stijve](/docs/nl-nl/avatar/rigid-accessories)  of gelaagde accessoires maakt, de [Accessory Fitting Tool](/docs/nl-nl/avatar/accessory-fitting-tool)  (AFT) van Studio voegt automatisch de juiste [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  toe en configureert deze met de volgende specificaties:

-

Eén bevestiging  - Elk gelaagd accessoire vereist minimaal één bevestigingspunt aan het bijbehorende lichaamsdeel.

-

Naamgevingsconventie  - De naam van de [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  moet voldoen aan een specifieke naamgevingsconventie afhankelijk van het [Accessory.AccessoryType](/docs/nl-nl/reference/engine/classes/Accessory#AccessoryType) . De AFT genereert automatisch een geschikte naam voor [Attachment](/docs/nl-nl/reference/engine/classes/Attachment) .

Als je bevestigingen handmatig instelt of configureert in Studio, gebruik dan de volgende namen voor je [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  object afhankelijk van het type accessoire:

| Accessoire Type | | Bevestigingsnaam |
| Hoed | | HatAttachment |
| Achterkant | | BodyBackAttachment |
| Heup | | WaistFrontAttachment , WaistCenterAttachment , WaistBackAttachment |
| Schouder | | RightShoulderAttachment , RightCollarAttachment , NeckAttachment , LeftCollarAttachment , LeftShoulderAttachment |
| Gezicht, Wimper, Wenkbrauw | | FaceFrontAttachment , FaceCenterAttachment |
| Hals | | NeckAttachment |
| Voorkant | | BodyFrontAttachment |
| Gelaagde tops (Shirt, TShirt, Trui, Jas) | | BodyFrontAttachment |
| Gelaagde onderkleding (Broek, Korte broek, Jurk/Rok) | | WaistCenterAttachment |

De Importer herkent automatisch mesh-objecten als bevestigingspunten als de objecten de affix \_Att  bevatten. Dit geldt alleen bij het importeren van meshes met cage-gegevens, zoals gelaagde accessoires of lichaam van personages.

## [Gezichtsaccessoires](#gezichtsaccessoires)[](#gezichtsaccessoires)

Gezichtsaccessoires, zoals wenkbrauwen en wimpers, zijn unieke gelaagde accessoires die je kunt bundelen met een avatar lichaam upload. Wenkbrauwen en wimpers kunnen niet als zelfstandige accessoires worden geüpload en moeten worden gebundeld met een [lichaam van een personage](/docs/nl-nl/avatar/character-bodies)  of [make-up assets](/docs/nl-nl/avatar/makeup/specifications) . Voor meer informatie over het bundelen van je gezichtsaccessoires met avatar modellen, zie [Publiceer lichamen met wimpers en wenkbrauwen](/docs/nl-nl/art/accessories/publish-eyebrows-eyelashes) .

-

Naamgevingsconventie bij bundeling  - Wanneer je deze assets bij een avatar lichaam upload, moeten de objecten van het gelaagde accessoire de volgende naamgevingsconventies gebruiken:

-

EyebrowAccessory

-

EyelashAccessory

-

HairAccessory

## [Laagbare eigenschappen](#laagbare-eigenschappen)[](#laagbare-eigenschappen)

Gelaagde accessoires vereisen aanvullende configuratie in een 3D-modelleringssoftware, zoals [Blender](https://www.blender.org)  of [Maya](https://www.autodesk.com/products/maya/overview) . Om het laag-effect te bereiken, moeten je gelaagde accessoires voldoen aan de volgende vereisten:

-

Gelaagde accessoires moeten [gewogen en gebonden](#rigging-en-skinning)  zijn aan een [R15 rigging armature](/docs/nl-nl/avatar/character-bodies/specifications#rigging) .

-

Gelaagde accessoires moeten een [binnenste mesh-cage](#binnenste-cage)  en een [buitenste mesh-cage](#buitenste-cage)  bevatten.

-

Gelaagde accessoires moeten blijven voldoen aan alle toepasselijke [aangepaste mesh-eisen](/docs/nl-nl/art/modeling/specifications) , zoals best practices voor waterdichtheid, texturen en polycount budgetten.

Zie [Maak je eerste gelaagde accessoire](/docs/nl-nl/art/accessories/creating)  voor een stapsgewijze handleiding over het toepassen van deze vereisten op een referentieasset in Blender. Zodra het .fbx  bestand is [geëxporteerd](/docs/nl-nl/avatar/layered-accessories/export) , zie [Accessory Fitting Tool](/docs/nl-nl/avatar/accessory-fitting-tool)  voor instructies over het omzetten van je model in een [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  object.

### [Rigging en skinning](#rigging-en-skinning)[](#rigging-en-skinning)

Rigging en skinning van gelaagde accessoires stelt ze in staat om natuurlijk te bewegen en te vervormen met de lichamen van personages terwijl ze zich in de 3D-ruimte bewegen. Je kunt je gelaagde accessoires handmatig riggen en skinnen met behulp van externe 3D-modelleringsgereedschappen, of [automatische skinning-overdracht](/docs/nl-nl/avatar/automatic-skinning-transfer)  gebruiken om de skinning-gegevens van een accessoire tijdens runtime te genereren.

Wanneer je externe 3D-modelleringsgereedschappen gebruikt om je accessoires te skinnen, houd er dan rekening mee dat Joint Influences  (Maya) of Bone Assignments  (Blender) per vertex beperkt moeten zijn tot 4 .

Voor meer informatie over basis skinning in een externe 3D-modelleringssoftware, zoals Blender's [Automatische Gewichten](https://docs.blender.org/manual/en/latest/animation/armatures/skinning/parenting.html#with-automatic-weights) , zie de [Skin een eenvoudige mesh](/docs/nl-nl/art/modeling/skin-a-simple-mesh)  tutorial voor instructies over rigging, het toepassen van gewichten en het skinnen van een basis mesh.

### [Cage meshes](#cage-meshes)[](#cage-meshes)

Cage meshes , of cages , zijn niet-gerenderde meshes die de binnenste en buitenste oppervlakken van een gelaagd accessoire definiëren, en ze zijn fundamenteel voor de laagbare eigenschappen. Voor een basisoverzicht van caging, zie [Maak je eerste gelaagde accessoire - Caging setup](/docs/nl-nl/art/accessories/creating/caging-setup)  en het relevante gedeelte van de tutorialvideo op [8:32](https://www.youtube.com/watch?v=C-DwGRBHvmE&t=512s) :

Roblox biedt sjabloon cage meshes in [gelaagde accessoire projectbestanden](/docs/nl-nl/avatar/layered-accessories/project-files)  die je kunt gebruiken terwijl je je eigen aangepaste gelaagde accessoires maakt. Houd er rekening mee dat de buitenste cage standaard identiek is aan de binnenste cage en dat alleen de buitenste cage moet worden aangepast om over je aangepaste gelaagde accessoire te passen. Als beste praktijk moet de vorm van de binnenste en buitenste cage overeenkomen voordat je de buitenste cage bewerkt om je asset volledig te bedekken.

De vertexen en UV's van de binnenste en buitenste cage meshes mogen niet worden verwijderd of verwijderd, omdat ze worden gebruikt om coördinaten tussen andere cages te matchen.

Gelaagde accessoires met ongeldige cage-configuraties kunnen falen bij validatie en zijn onderhevig aan moderatie. Voor voorbeelden en instructies over hoe je cagingproblemen kunt oplossen, zie [Caging best practices](/docs/nl-nl/avatar/layered-accessories/caging-best-practices) .

#### [Binnenste cage](#binnenste-cage)[](#binnenste-cage)

De binnenste cage is een mesh die het binnenste oppervlak van je accessoiremodel definieert en hoe je gelaagde accessoire zich uitstrekt en past over een lichaam van een personage. Het object van de binnenste cage mesh moet dezelfde naam hebben als het accessoiremodel, aangevuld met _InnerCage .

![](https://prod.docsiteassets.roblox.com/assets/accessories/lc-requirements-innercage.png)

![](https://prod.docsiteassets.roblox.com/assets/accessories/lc-requirements-innercage-outliner.png)

#### [Buitenste cage](#buitenste-cage)[](#buitenste-cage)

De buitenste cage is een mesh die het buitenste oppervlak van je accessoiremodel definieert en hoe andere gelaagde accessoires zich kunnen uitstrekken en passen over je gelaagde accessoire. Het object van de buitenste cage mesh moet dezelfde naam hebben als het accessoiremodel, aangevuld met _OuterCage .

![](https://prod.docsiteassets.roblox.com/assets/accessories/lc-requirements-outercage.png)

![](https://prod.docsiteassets.roblox.com/assets/accessories/lc-requirements-outercage-outliner.png)

Avatar [lichaam van personages](/docs/nl-nl/avatar/character-bodies)  moeten een buitenste cage bevatten om compatibel te zijn met gelaagde accessoires. Alle lichaam van personages op de [Marketplace](https://www.roblox.com/catalog)  bevatten een goed geconfigureerde buitenste cage en zijn compatibel met gelaagde accessoires.

## [Marketplace vereisten](#marketplace-vereisten)[](#marketplace-vereisten)

Gelaagde accessoires moeten voldoen aan de volgende vereisten voordat je ze naar de Marketplace uploadt:

-

Zorg ervoor dat je gelaagde accessoires voldoen aan de [Marketplace-beleid](/docs/nl-nl/marketplace/marketplace-policy) .

-

Zorg ervoor dat je gelaagde accessoires voldoen aan de [aangepaste mesh-specificaties](/docs/nl-nl/art/modeling/specifications)  van Roblox, waar van toepassing.

-

Object [Material](/docs/nl-nl/reference/engine/classes/MeshPart#Material)  is ingesteld op Plastic .

-

Object [Transparency](/docs/nl-nl/reference/engine/classes/MeshPart#Transparency)  is ingesteld op 0.

-

Object [VertexColor](/docs/nl-nl/reference/engine/classes/MeshPart#VertexColor)  is de standaard 1, 1, 1 .

-

Je [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  object bevat geen overbodige objecten, zoals [Script](/docs/nl-nl/reference/engine/classes/Script)  of extra [Part](/docs/nl-nl/reference/engine/classes/Part)  objecten.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
