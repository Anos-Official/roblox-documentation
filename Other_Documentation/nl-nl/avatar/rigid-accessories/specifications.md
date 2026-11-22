<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/rigid-accessories/specifications -->

Specificaties voor rigide accessoires | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Accessories and clothing
6. /
7. Stijve accessoires

# Specificaties voor rigide accessoires

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Rigide accessoires vereisen een specifieke set componenten en configuratiestandaarden om ervoor te zorgen dat ze aan de lichamen van personages kunnen worden bevestigd en optimalisaties voor prestaties en kwaliteit bevatten. Omdat je veel van deze vereisten moet toepassen terwijl je het rigide accessoire ontwerpt en modelleert in een extern modelleerprogramma zoals [Blender](https://www.blender.org/)  of [Maya](https://www.autodesk.com/products/maya/overview) , is het belangrijk om deze specificaties vroeg en vaak te bekijken terwijl je werkt.

Wanneer je klaar bent om je rigide accessoire te exporteren, raadpleeg dan alle [exportinstellingseisen](/docs/nl-nl/avatar/rigid-accessories/export)  voor Blender en Maya.

Voor andere soorten 3D-modellen:

-

[Algemene mesh](/docs/nl-nl/art/modeling/specifications)  specificaties.

-

[Gelaagd accessoire](/docs/nl-nl/avatar/layered-accessories/specifications)  specificaties.

## [Geometrie en budgetten](#geometrie-en-budgetten)[](#geometrie-en-budgetten)

-

Enkele mesh  - Rigide accessoires moeten een enkele mesh zijn.

-

Budgetten  - Rigide accessoires mogen niet meer dan 4k  driehoeken bevatten.

-

Waterdicht  - Alle geometrie moet waterdicht zijn zonder blootgestelde gaten of achterkant.

-

Gebruik quads  waar mogelijk. Vermijd vlakken met 5 of meer zijden.

-

Meshgrootte  - Meshes moeten voldoen aan de maximale grootte-eisen (in studs, gecentreerd op het bevestigingspunt) volgens het type rigide accessoire dat je ontwerpt en de [lichaamschaal](#lichaamschaal)  waarvoor je het rigide accessoire ontwerpt.

### [Lichaamschaal](#lichaamschaal)[](#lichaamschaal)

Roblox ondersteunt 3 soorten lichaamschalen voor personages: Normaal , Slank  en Klassiek . Bij het ontwerpen van een rigide accessoire mag de grootte van het accessoire de volgende afmetingen niet overschrijden, afhankelijk van de lichaamschaal en het type rigide accessoire. De grootte van een rigide accessoire wordt gemeten op basis van de bevestigingsoriëntatie.

Bij het modelleren van rigide accessoires is het belangrijk om een [mannequin](/docs/nl-nl/avatar/resources#mannequin-modellen)  te gebruiken om ervoor te zorgen dat je verhoudingen passen. Wanneer je de [Importer](/docs/nl-nl/studio/importer#avatar-general)  gebruikt om een mannequin te importeren:

-

Gebruik Rig Scale  > Rthro  om je model te importeren als een Normaal  lichaamsformaat.

-

Gebruik Rig Scale  > Rthro Narrow  om je model te importeren als een Slank  lichaamsformaat.

-

Gebruik Rig Scale  > Default  om je model te importeren als een Klassiek  lichaamsformaat.

Je kunt tools zoals de [Accessory Fitting Tool](/docs/nl-nl/avatar/accessory-fitting-tool)  gebruiken om de schaal van je mesh op een mannequin binnen een gevisualiseerde grens te visualiseren en aan te passen voordat je het asset uploadt en publiceert op de Marketplace. Voor een demonstratie, zie [Converteer rigide accessoires](/docs/nl-nl/avatar/rigid-accessories/import#stijve-accessoires-converteren) .

#### [Normaal](#normaal)[](#normaal)

![](https://prod.docsiteassets.roblox.com/assets/art/resources/Body-Scale-Rthro-Normal.png)

Een Rthro Normaal lichaamsformaat [downloadbare mannequin](/docs/nl-nl/avatar/resources#referenties)  die ongeveer 5.75-6.5 studs hoog is.

| Asset Type | | Breedte (X) | | Hoogte (Y) | | Diepte (Z) |
| --- | --- |
| Hoed | | 1.87 | | 2.5 | | 1.87 |
| Haar | | 1.87 | | 3.12*
 (Niet gecentreerd: 1.25 omhoog, 1.875 omlaag) | | 2.18*
 (Niet gecentreerd: 0.9375 voorkant, 1.25 achter) |
| Gezicht | | 1.87 | | 1.25 | | 1.25 |
| Wenkbrauw en Wimpers | | 1.5 | | 0.5 | | 0.5 |
| Hals | | 2.95 | | 3.68 | | 2.16 |
| Schouder (bevestigd aan NeckAttachment) | | 6.90 | | 3.68 | | 3.24 |
| Schouder (bevestigd aan RightCollarAttachment, LeftCollarAttachment) | | 2.95 | | 3.68 | | 3.24 |
| Schouder (bevestigd aan RightShoulderAttachment, LeftShoulderAttachment) | | 2.67 | | 4.40 | | 3.09 |
| Voorkant | | 2.95 | | 3.68 | | 3.24 |
| Achterkant | | 9.86 | | 8.59 | | 4.87*
 (Niet gecentreerd: 1.623 voorkant, 3.246 achter) |
| Heup | | 3.94 | | 4.29*
 (Niet gecentreerd: 1.842 omhoog, 2.457 omlaag) | | 7.57 |

#### [Slank](#slank)[](#slank)

![](https://prod.docsiteassets.roblox.com/assets/art/resources/Body-Scale-Rthro-Slender.png)

Een Rthro Slank (Narrow) lichaamsformaat [downloadbare mannequin](/docs/nl-nl/avatar/resources#referenties)  die ongeveer 5.25-6.25 studs hoog is.

| Asset Type | | Breedte (X) | | Hoogte (Y) | | Diepte (Z) |
| Hoed | | 1.78 | | 2.5 | | 1.78 |
| Haar | | 1.78 | | 3.12*
 (Niet gecentreerd: 1.25 omhoog, 1.875 omlaag) | | 2.08*
 (Niet gecentreerd: 1.892 voorkant, 1.189 achter) |
| Gezicht | | 1.78 | | 1.25 | | 1.18 |
| Wenkbrauw en Wimpers | | 1.5 | | 0.5 | | 0.5 |
| Hals | | 2.59 | | 3.39 | | 1.92 |
| Schouder (bevestigd aan NeckAttachment) | | 6.05 | | 3.39 | | 2.88 |
| Schouder (bevestigd aan RightCollarAttachment, LeftCollarAttachment) | | 2.59 | | 3.39 | | 2.88 |
| Schouder (bevestigd aan RightShoulderAttachment, LeftShoulderAttachment) | | 2.37 | | 3.96 | | 2.75 |
| Voorkant | | 2.59 | | 3.39 | | 2.88 |
| Achterkant | | 8.64 | | 7.91 | | 4.32*
 (Niet gecentreerd: 1.443 voorkant, 2.886 achter) |
| Heup | | 3.76 | | 3.29*
 (Niet gecentreerd: 1.414 omhoog, 1.885 omlaag) | | 6.73 |

#### [Klassiek](#klassiek)[](#klassiek)

![](https://prod.docsiteassets.roblox.com/assets/art/resources/Body-Scale-Classic.png)

Een Klassiek lichaamsformaat [downloadbare mannequin](/docs/nl-nl/avatar/resources#referenties)  die ongeveer 4.75 studs hoog is.

| Asset Type | | Breedte (X) | | Hoogte (Y) | | Diepte (Z) |
| Hoed | | 3 | | 4 | | 3 |
| Haar | | 3 | | 5*
 (Niet gecentreerd: 2 omhoog, 3 omlaag) | | 3.5*
 (Niet gecentreerd: 1.5 voorkant, 2 achter) |
| Gezicht | | 3 | | 2 | | 2 |
| Wenkbrauw en Wimpers | | 1.5 | | 0.5 | | 0.5 |
| Hals | | 3 | | 3 | | 2 |
| Schouder (bevestigd aan NeckAttachment) | | 7 | | 3 | | 3 |
| Schouder (ander) | | 3 | | 3 | | 3 |
| Voorkant | | 3 | | 3 | | 3 |
| Achterkant | | 10 | | 7 | | 4.5*
 (Niet gecentreerd: 1.5 voorkant, 3 achter) |
| Heup | | 4 | | 3.5*
 (Niet gecentreerd: 1.5 omhoog, 2 omlaag) | | 7 |

### [AvatarPartScaleType](#avatarpartscaletype)[](#avatarpartscaletype)

Roblox vertegenwoordigt de lichaamschaal in de engine door een AvatarPartScaleType  [StringValue](/docs/nl-nl/reference/engine/classes/StringValue)  object binnen elk avatar karakterdeel en bijbehorend accessoire. In de meeste gevallen hoeven assetmakers deze waardeobjecten niet rechtstreeks te benaderen of te wijzigen, aangezien tools zoals de [Accessory Fitting Tool](/docs/nl-nl/avatar/accessory-fitting-tool)  automatisch het juiste waardeobject genereren bij het maken van accessoires.

In gevallen waarin je de huidige lichaamschaal van een lichaamsdeel of accessoire moet identificeren, definieert de volgende tabel de AvatarPartScaleType  waarde voor elk type lichaamsgrootte. Wanneer je je rigide accessoire importeert, gebruik dan de [Rig Scale](/docs/nl-nl/studio/importer)  van de Importer om automatisch een schaal op je accessoire toe te passen.

| Lichaamschaal | | AvatarPartScaleType waarde |
| Klassiek | | Classic |
| Normaal | | ProportionsNormal |
| Slank | | ProportionsSlender |

## [Texturen](#texturen)[](#texturen)

-

Rigide accessoire texturen moeten voldoen aan de algemene [textuurspecificaties](/docs/nl-nl/art/modeling/texture-specifications)  van Roblox. Hoge resolutie texturen worden automatisch omgezet naar lagere resolutie texturen om de prestaties te optimaliseren.

-

Rigide accessoire texturen voor Marketplace-assets mogen niet groter zijn dan 2048x2048 resolutie.

## [Bevestigingspunten](#bevestigingspunten)[](#bevestigingspunten)

[Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  objecten bepalen waar een accessoiremodel aan een punt op een karakterlichaam wordt bevestigd. Of je nu rigide of [gelaagde](/docs/nl-nl/avatar/layered-accessories)  accessoires maakt, de [Accessory Fitting Tool](/docs/nl-nl/avatar/accessory-fitting-tool)  (AFT) voegt automatisch de juiste [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  toe en configureert deze met de volgende specificaties:

-

Eén bevestiging  - Elk rigide accessoire vereist minimaal één bevestigingspunt aan het bijbehorende lichaamsdeel.

-

Naamgevingsconventie  - De naam van de [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  moet voldoen aan een specifieke naamgevingsconventie, afhankelijk van het [Accessory.AccessoryType](/docs/nl-nl/reference/engine/classes/Accessory#AccessoryType) . De AFT genereert automatisch een geschikte naam voor de [Attachment](/docs/nl-nl/reference/engine/classes/Attachment) .

-

Hoofdplaatsing  - Voor accessoires die aan het hoofd worden bevestigd, zoals hoeden en haar, moet het bevestigingspunt zo worden gepositioneerd dat het op het zichtbare oppervlak van de hoofdmesh past. Bevestigingspunten die van het zichtbare hoofd afdrijven, schenden de [Marketplace-beleid](/docs/nl-nl/marketplace/marketplace-policy#algemene-richtlijnen-voor-creatie) .

Als je bevestigingen handmatig in Studio instelt of configureert, gebruik dan de volgende namen voor je [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  object volgens het type accessoire:

| Accessoire type | | Bevestigingsnaam |
| Hoed | | HatAttachment |
| Haar | | HairAttachment |
| Achterkant | | BodyBackAttachment |
| Heup | | WaistFrontAttachment , WaistCenterAttachment , WaistBackAttachment |
| Schouder | | RightShoulderAttachment , RightCollarAttachment , NeckAttachment , LeftCollarAttachment , LeftShoulderAttachment |
| Gezicht, Wimper, Wenkbrauw | | FaceFrontAttachment , FaceCenterAttachment |
| Hals | | NeckAttachment |
| Voorkant | | BodyFrontAttachment |

Het importeren van bevestigingsobjecten vanuit een extern hulpmiddel wordt niet ondersteund voor rigide accessoires, maar wordt wel ondersteund voor [karakterlichamen](/docs/nl-nl/avatar/character-bodies/specifications#bevestigingen) .

-

Schouders en Kragen  - Hoewel ze zich op vergelijkbare locaties bevinden, interageren schouder- en kraagbevestigingspunten anders met de armaturen van het karakterlichaam voor rigide accessoires.

-

Items die RightShoulderAttachment  of LeftShoulderAttachment  gebruiken, bewegen mee met de arm van het karakter.

-

Items die RightCollarAttachment  of LeftCollarAttachment  gebruiken, bewegen niet mee met de arm van het karakter.

## [Marketplace-eisen](#marketplace-eisen)[](#marketplace-eisen)

Rigide accessoires moeten voldoen aan de volgende eisen voordat je ze naar de Marketplace uploadt:

-

Zorg ervoor dat je rigide accessoires voldoen aan de [Marketplace-beleidsregels](/docs/nl-nl/marketplace/marketplace-policy) .

-

Zorg ervoor dat je rigide accessoires voldoen aan de [aangepaste mesh specificaties](/docs/nl-nl/art/modeling/specifications)  van Roblox, waar van toepassing.

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
