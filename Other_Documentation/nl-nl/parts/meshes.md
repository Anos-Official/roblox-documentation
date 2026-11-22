<!-- Source: https://create.roblox.com/docs/nl-nl/parts/meshes -->

Meshes | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)

# Meshes

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

[MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  objecten zijn afstammelingen van de [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  klasse. Ze vertegenwoordigen meshes , die verzamelingen zijn van vertices, randen en vlakken die een 3D-object vormen. In tegenstelling tot onderdelen, die je direct in Studio kunt maken, moet je een externe modelleerapplicatie zoals Blender of Maya gebruiken om meshes te maken, en deze vervolgens importeren in Studio als [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  objecten.

Na het importeren van een mesh in Studio, kun je de renderingsinstellingen aanpassen, zoals texturen, detailniveau en botsingsnauwkeurigheid. Naast het importeren van je eigen meshes, kun je ook bladeren en selecteren uit door gebruikers geüploade meshes via de [Creator Store](/docs/nl-nl/production/creator-store) .

Roblox ondersteunt veel soorten meshes, zolang ze voldoen aan de [algemene mesh-specificaties](/docs/nl-nl/art/modeling/specifications) . Een basis mesh bestaat uit ten minste één mesh-object en één textuur:

![Een boom mesh-object zonder textuur.](https://prod.docsiteassets.roblox.com/assets/art/Basic-Mesh-Example.png) Een mesh-object bepaalt de vorm en geometrie van het 3D-object

![De textuurafbeelding voor de bladeren van de boom in de vorige afbeelding.](https://prod.docsiteassets.roblox.com/assets/art/Basic-Texture-Example.png) Een textuurafbeelding past een oppervlakte-uiterlijk en kleur toe

![Een boom mesh-object met de bladeren textuur toegepast.](https://prod.docsiteassets.roblox.com/assets/art/Basic-Mesh-Combined-Example.png) De mesh en textuur combineren om een uniek aangepast 3D-object te maken

Studio ondersteunt ook meshes met componenten voor het maken van avatar karaktermodellen of accessoires, zoals [rigging en skinning](#rigging-en-skinning)  gegevens.

Je kunt [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  activa verkopen als avatarlichamen, accessoires en kleding op de Marketplace. Zie [Avatar](/docs/nl-nl/avatar)  voor meer informatie.

## [Importeren van meshes](#importeren-van-meshes)[](#importeren-van-meshes)

Je kunt meshes in Studio importeren met behulp van de [Importer](/docs/nl-nl/studio/importer) . Met deze tool kun je meshes vooraf bekijken en onderzoeken voordat je ze in je werkruimte of Toolbox  importeert, zoals het verifiëren van textuur, rigging, skinning en animatiegegevens. Het markeert ook problemen en weigert meshes met fouten.

Als het mesh-bestand dat je importeert objecten bevat die specifieke naamgevingsconventies gebruiken of gezichtsanimatiegegevens bevat, detecteert de Importer deze automatisch en converteert ze in de volgende objecten in plaats van [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) :

-

[Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  — Objecten met _Att  aan het einde van hun namen.

-

[WrapTarget](/docs/nl-nl/reference/engine/classes/WrapTarget)  — Objecten met _OuterCage  aan het einde van hun namen.

-

[WrapLayer](/docs/nl-nl/reference/engine/classes/WrapLayer)  — Objecten met zowel _InnerCage  als _OuterCage  aan het einde van hun namen.

-

[FaceControls](/docs/nl-nl/reference/engine/classes/FaceControls)  — Objecten die avatar karakterhoofden bevatten en de bijbehorende gezichtsanimatiegegevens.

Als je meerdere meshes wilt importeren samen met niet-3D activa, zoals afbeeldingen en audio, kun je de [Asset Manager](/docs/nl-nl/projects/assets/manager)  gebruiken; houd er echter rekening mee dat het geen ondersteuning biedt voor het importeren van meshes met rigging, skinning en animatiegegevens, accessoires of karakters met gezichtsanimaties.

## [Aanpassen van meshes](#aanpassen-van-meshes)[](#aanpassen-van-meshes)

In tegenstelling tot basis onderdelen hebben meshes meer aanpassingsopties die je kunt aanpassen voor geavanceerde renderingsnauwkeurigheid.

### [Textuur](#textuur)[](#textuur)

Texturen  dragen bij aan het visuele uiterlijk van meshes door 2D-details zoals kleur en patronen toe te voegen. Studio stelt je in staat om één textuur toe te passen met de [MeshPart.TextureID](/docs/nl-nl/reference/engine/classes/MeshPart#TextureID)  eigenschap, of tot vier fysiek-gebaseerde render (PBR) texturen toe te passen binnen een [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  kindobject van de mesh of gemaakt met een [MaterialVariant](/docs/nl-nl/reference/engine/classes/MaterialVariant)  en ingesteld in de [MeshPart.MaterialVariant](/docs/nl-nl/reference/engine/classes/MeshPart#MaterialVariant)  eigenschap van de mesh. PBR-texturen stellen je in staat om realistische schaduwen en verlichting weer te geven door meerdere soorten textuurafbeeldingen, of kaarten, op een enkel object te gebruiken.

PBR Textures Single Texture

Studio ondersteunt vier PBR-textuurkaarten, elk corresponderend met een visuele eigenschap van het oppervlak van een object. Het combineren van meerdere textuurkaarten kan kleur, ruwheid en reflectiviteit in elke verlichtingsomgeving nauwkeuriger simuleren en de visuele elementen van je activa en omgeving verbeteren. Voor meer informatie over PBR-texturen en de textuurkaarten, zie [PBR Textures](/docs/nl-nl/art/modeling/surface-appearance) .

![Voorbeeld van SurfaceAppearance toegepast op een Bush Mesh](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-Example-1.jpg)

![Voorbeeld van SurfaceAppearance toegepast op een Rock Mesh](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-Example-3.jpg)

Je kunt PBR-texturen toepassen met een van de volgende objecten:

-

[SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  — Past PBR-texturen toe op het mesh-oppervlak en beïnvloedt de geometrie niet.

-

[MaterialVariant](/docs/nl-nl/reference/engine/classes/MaterialVariant)  — Vertegenwoordigt een aangepast materiaal dat niet alleen PBR-texturen op het mesh-oppervlak toepast, maar ook fysieke eigenschappen toevoegt.

Om PBR-texturen aan een mesh toe te voegen:

SurfaceAppearance MaterialVariant

1.

In het [Explorer](/docs/nl-nl/studio/explorer)  venster, beweeg de muis over het [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  object. Klik op de ⊕  knop en selecteer [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance) .

2.

In het [Properties](/docs/nl-nl/studio/properties)  venster, bewerk de eigenschappen die overeenkomen met de PBR-textuurkaarten.

Als je zowel [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  als een kindobject toevoegt en de [MaterialVariant](/docs/nl-nl/reference/engine/classes/MaterialVariant)  in de eigenschappen van de mesh instelt, past Studio alleen de textuurkaartinstellingen van het [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  object toe op de mesh. De mesh heeft nog steeds alle andere instellingen van het [MaterialVariant](/docs/nl-nl/reference/engine/classes/MaterialVariant)  object, zoals aangepaste fysieke eigenschappen.

### [Detailniveau](#detailniveau)[](#detailniveau)

Je kunt het detailniveau van een mesh dynamisch regelen met de [Enum.RenderFidelity](/docs/nl-nl/reference/engine/enums/RenderFidelity)  eigenschap. De standaardwaarde is [Automatic](/docs/nl-nl/reference/engine/enums/RenderFidelity#Automatic) , wat betekent dat het detail van de mesh is gebaseerd op de afstand tot de camera, zoals uiteengezet in de volgende tabel.

| Afstand van de camera | | Rendernauwkeurigheid | | Voorbeeld |
| --- | --- |
| Minder dan 250 studs | | Hoogste | | ![Een potion mesh-object dat is gerenderd in het hoogste detailniveau.](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Render-Fidelity-High.jpg) |
| 250-500 studs | | Medium | | ![Een potion mesh-object dat is gerenderd in een gemiddeld detailniveau. De randen zijn minder glad dan in de vorige afbeelding.](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Render-Fidelity-Medium.jpg) |
| 500 of meer studs | | Laagste | | ![Een potion mesh-object dat is gerenderd in het laagste detailniveau. De randen zijn minder glad dan in de vorige afbeelding, en de vloeistof is niet langer glanzend.](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Render-Fidelity-Low.jpg) |

### [Botsingsnauwkeurigheid](#botsingsnauwkeurigheid)[](#botsingsnauwkeurigheid)

Botsingsnauwkeurigheid  bepaalt hoe nauwkeurig de visuele weergave van een mesh overeenkomt met zijn fysieke grenzen. De [MeshPart.CollisionFidelity](/docs/nl-nl/reference/engine/classes/MeshPart#CollisionFidelity)  eigenschap heeft de volgende opties:

-

Box  — Creëert een begrenzende botsingsdoos, ideaal voor kleine of niet-interactieve objecten.

-

Hull  — Genereert een convexe omhulsel, geschikt voor objecten met minder uitgesproken indeukingen of holtes.

-

Default  — Produceert een benaderende botsingsvorm die concaviteit ondersteunt, geschikt voor complexe objecten met semi-gedetailleerde interactiebehoeften.

-

PreciseConvexDecomposition  — Biedt de meest nauwkeurige nauwkeurigheid, maar is nog steeds geen 1:1 weergave van het visuele. Deze optie heeft de hoogste prestatiekosten en duurt langer voor de engine om te berekenen.

-

Tunable  — Door [MeshPart.CollisionFidelity](/docs/nl-nl/reference/engine/classes/MeshPart#CollisionFidelity)  in te stellen op [Tunable](/docs/nl-nl/reference/engine/enums/CollisionFidelity#Tunable)  verschijnt er een [CollisionPrecision](/docs/nl-nl/reference/engine/classes/MeshPart#CollisionPrecision)  schuifregelaar in het Properties  venster. Naar boven schuiven produceert nauwkeurigere, duurdere botsingsgeometrie, terwijl naar beneden schuiven grovere, goedkopere geometrie produceert, allemaal zonder over te schakelen naar een andere nauwkeurigheidsoptie. De standaardwaarde van [CollisionPrecision](/docs/nl-nl/reference/engine/classes/MeshPart#CollisionPrecision)  is niet vast; de engine kiest intelligent de juiste precisie en dus kosten, op basis van de grootte van de mesh.

Original Mesh Default Box Hull Precise Tunable

![Originele mesh van kasteel toren](https://prod.docsiteassets.roblox.com/assets/physics/collisions/Collision-Fidelity-MeshPart.jpg)

Om de botsingsnauwkeurigheid in Studio te bekijken, schakel je Botsingsnauwkeurigheid  in via de [Visualisatie-opties](/docs/nl-nl/studio/overview#visualisatie-opties)  widget in de rechterbovenhoek van het 3D-venster.

Voor meer informatie over de prestatie-impact van botsingsnauwkeurigheidsopties en hoe deze te verminderen, zie [Verbeter prestaties](/docs/nl-nl/performance-optimization/improve#fysica-berekeningen) . Voor een diepgaande uitleg over hoe je een botsingsnauwkeurigheidsoptie kiest die een balans vindt tussen je precisie- en prestatievereisten, zie [Stel fysica- en renderparameters in](/docs/nl-nl/tutorials/curriculums/environmental-art/optimize-your-experience#review-physics-and-rendering-parameters) .

## [Rigging en skinning](#rigging-en-skinning)[](#rigging-en-skinning)

Rigging  is het proces van het verbinden van een mesh met een interne poseerbare skeletstructuur. Gerigged meshes stellen de mesh-oppervlakken in staat om te draaien en te bewegen met behulp van interne botten binnen een model, zoals de knie of elleboog van een karakter. Skinning  van een gerigged mesh stelt het gerigged mesh-object in staat om te vervormen, uit te rekken en te buigen op een meer realistische manier.

Zonder skinning draait het hele hoofdmesh op een enkele as

Met skinning buigt het hoofdmesh natuurlijk bij de nek, en de onderkant van de nek blijft verbonden met de torso

Voor meer informatie over rigging en skinning, zie [Rigging en skinning](/docs/nl-nl/art/modeling/rigging) . Na het riggen van een mesh kun je animatie en poses toevoegen met de Animatie-editor . Zie [Maak een animatie](/docs/nl-nl/animation/editor#maak-een-animatie)  voor meer informatie. 3D-activa op de Marketplace, zoals avatar kleding en lichamen, vereisen ook rigging en skinning. Zie [Avatar](/docs/nl-nl/avatar)  voor meer informatie over de vereisten voor Marketplace-activa.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
