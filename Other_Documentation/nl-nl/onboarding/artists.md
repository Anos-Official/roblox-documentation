<!-- Source: https://create.roblox.com/docs/nl-nl/onboarding/artists -->

Inwerken voor artiesten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Platform](/docs/nl-nl/get-started)
4. /
5. [Get started for experienced creators](/docs/nl-nl/onboarding)

# Inwerken voor artiesten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Deze pagina geeft een samenvatting, op hoog niveau, van de enginevereisten en conventies die het belangrijkst zijn voor artiesten die van andere engines komen, en elke sectie linkt naar de gedetailleerde specificaties.

![Een realistische, loofrijke struik met PBR-texturen.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-Example-1.jpg)

![Een realistische, mosachtige steen met PBR-texturen.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-Example-3.jpg)

## [PBR en materialen](#pbr-en-materialen)[](#pbr-en-materialen)

Roblox gebruikt een metalness en roughness  PBR-werkstroom, geen specular en glossiness werkstroom. Een volledige PBR-materiaal gebruikt deze textuurkaarten:

-

Kleur (albedo) , met een optionele alpha-kanaal voor transparantie.

-

Normaal , in OpenGL tangent-space formaat (Y+), met een MikkTSpace tangent basis.

-

Ruwheid .

-

Metalness .

Voor formaten, resoluties en kanaaldetails, zie [Textuurspecificaties](/docs/nl-nl/art/modeling/texture-specifications)  en [Oppervlakte-uiterlijk](/docs/nl-nl/art/modeling/surface-appearance) .

Materialen op Roblox komen in twee vormen:

-

Een materiaal , ingesteld op een onderdeel of met een aangepaste [MaterialVariant](/docs/nl-nl/reference/engine/classes/MaterialVariant) , definieert hoe een oppervlak eruitziet en hoe het fysiek gedraagt, inclusief dichtheid, wrijving, elasticiteit en geluid. Voor details, zie [Materialen](/docs/nl-nl/parts/materials) .

-

Een [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  definieert alleen hoe een mesh eruitziet. Gebruik het voor gedetailleerde oppervlakken zoals personages en heldenprops, waar het uiterlijk belangrijker is dan het fysieke gedrag.

Elke driehoek kan slechts één materiaal hebben. Als een mesh meerdere materialen nodig heeft, zoals huid en stof op een personage, splits het dan in aparte meshes per materiaal.

## [Meshes](#meshes)[](#meshes)

-

Driehoekbudget:  Een individuele mesh mag niet meer dan 20.000 driehoeken hebben, wat ongeveer 65.535 vertices is, en avataritems hebben hun eigen, lagere budgetten. Als je een mesh boven de limiet importeert, decimeert Studio deze automatisch om te passen, dus verlaag zelf het aantal driehoeken als je het resultaat wilt beheersen. Voor alle vereisten, zie [Mesh-specificaties](/docs/nl-nl/art/modeling/specifications) .

-

Grootte:  Elke dimensie van een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  kan maximaal 2.048 studs zijn. Studio schaalt automatisch grotere imports naar beneden om te passen, dus splits zeer grote omgevingsstukken in meshes die niet groter zijn dan 2.048 studs in welke dimensie dan ook.

-

Niveau van detail:  Het [RenderFidelity](/docs/nl-nl/reference/engine/classes/MeshPart#RenderFidelity)  van elke mesh verlaagt automatisch zijn [niveau van detail](/docs/nl-nl/parts/meshes#detailniveau)  naarmate het verder van de camera beweegt. In games die [instance streaming](/docs/nl-nl/workspace/streaming)  gebruiken, kan [SLIM](/docs/nl-nl/workspace/streaming/slim)  ook lichte versies van modellen genereren en renderen wanneer ze buiten de streamingradius zijn.

 ![Een boom mesh en zijn textuurkaarten gecombineerd om een enkele boom te creëren.](https://prod.docsiteassets.roblox.com/assets/art/Basic-Mesh-Combined-Example.png)

## [Verlichting](#verlichting)[](#verlichting)

Stel de algehele uitstraling in met [Lighting.LightingStyle](/docs/nl-nl/reference/engine/classes/Lighting#LightingStyle) :

-

[Realistic](/docs/nl-nl/reference/engine/enums/LightingStyle#Realistic)  produceert naturalistische verlichting en genereert schaduwen en omgevingsocclusie dynamisch. Het gebruikt geen gebakken schaduwen of gebakken omgevingsocclusie.

-

[Soft](/docs/nl-nl/reference/engine/enums/LightingStyle#Soft)  produceert een gestileerde, zachtere, meer ambient uitstraling met minder precieze lichten.

Roblox schaalt de lichtkwaliteit automatisch. Naarmate de prestaties dat vereisen, vallen apparaten terug op het goedkopere Soft-verlichtingspad, wat het vaakst gebeurt op low-end mobiele apparaten. [Lighting.PrioritizeLightingQuality](/docs/nl-nl/reference/engine/classes/Lighting#PrioritizeLightingQuality)  controleert of de lichtkwaliteit of het zichtbereik als eerste wordt verlaagd. Voor alle verlichtingsproperties, zie [Verlichting](/docs/nl-nl/environment/lighting) .

-

Interieurs  krijgen dynamische reflecties van automatisch gegenereerde probes, die voornamelijk invloed hebben op reflecties en, in mindere mate, diffuse verlichting.

-

Exterieurs  zijn afhankelijk van lichten, de [skybox](/docs/nl-nl/environment/skybox) , en [atmosfeer](/docs/nl-nl/environment/atmosphere)  in plaats van een dynamisch reflectiesysteem.

-

Kleine of dunne details , zoals een kap over een gezicht, kunnen mogelijk geen betrouwbare zelfschaduwen werpen. Om de uitstraling te garanderen die je wilt, bak je kritische zelfschaduwen en omgevingsocclusie in de kleurkaart.

## [Personages](#personages)[](#personages)

Er zijn twee soorten personages:

-

Platformavatars  volgen de avatarvereisten van Roblox voor polygonen, skelet, materialen en bijlagen. Ze werken in verschillende games en kunnen de kleding en accessoires gebruiken die spelers meenemen. Voor vereisten, zie [Specificaties van het lichaam van personages](/docs/nl-nl/avatar/character-bodies/specifications) .

-

Aangepaste personages  hoeven zich niet aan de avatarvereisten te houden. Hun rigs kunnen willekeurig zijn, en hun budgetten zijn hetzelfde als elke andere mesh.

Platformavatars gebruiken de R15  rig, die 15 lichaamsdelen heeft die elk overeenkomen met één gewricht. Deze één-op-één mapping stelt spelers in staat om individuele lichaamsdelen uit de Marketplace te ruilen. Avatars gebruiken ook kooien , standaard meshes die het oppervlak van een personage beschrijven, zodat [gelaagde kleding](/docs/nl-nl/avatar/layered-accessories/specifications)  kan uitrekken om op elk lichaam te passen.

Voor meer articulatie ondersteunen geavanceerde R15  rigs, soms R15+ genoemd, tot 37 extra optionele botten, zoals vingers, sleutelbeenderen en wervelgewrichten. Ze bouwen voort op de standaard R15 rig, dus ze gebruiken dezelfde technologie-stack. Voor de vereiste hiërarchie en naamgeving, zie [Geavanceerde R15 rigs](/docs/nl-nl/avatar/character-bodies/specifications#geavanceerde-r15-rigs) . Aangepaste personages zijn helemaal niet beperkt tot R15; hun gewrichtenaantal en structuur zijn alleen beperkt door de prestaties op je doelapparaten.

 ![Een Roblox-avatar die een glanzende, puffy jas en jeans draagt.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Layered-Clothing-Example.png)

## [Rigs en animatie](#rigs-en-animatie)[](#rigs-en-animatie)

-

Skinning:  Een vertex kan maximaal door vier botten of gewrichten worden beïnvloed. Voor alle riggingvereisten, zie [Mesh-specificaties](/docs/nl-nl/art/modeling/specifications#rigging-en-skinning) .

-

Fysica:  Gewrichten, onderdelen en meshonderdelen kunnen fysiek worden gesimuleerd, maar er is geen stofsimulatie.

-

Gezichtsanimatie:  Gezichtsanimatie is gewricht-gebaseerd. Hoofden animeren met gezichtsgewrichten en skinning, geposeerd om overeen te komen met het Facial Action Coding System (FACS), en Roblox ondersteunt geen blend shape-animatie. Voor details, zie [Dynamische hoofden](/docs/nl-nl/avatar/dynamic-heads) .

### [Animatiewerkstroom](#animatiewerkstroom)[](#animatiewerkstroom)

-

Importeer vanuit je modelleertool:  Een .fbx  export kan één animatietrack bevatten. Om meerdere animaties binnen te halen, exporteer je elke animatie afzonderlijk. Voor vereisten, zie [Animaties](/docs/nl-nl/art/modeling/specifications#animaties) .

-

Animeer in Studio:  De [Animatie-editor](/docs/nl-nl/animation/editor)  maakt keyframe-animaties op elke rig, met [inverse kinematica](/docs/nl-nl/animation/inverse-kinematics)  en een [curve-editor](/docs/nl-nl/animation/curve-editor) . [Animatie-opname](/docs/nl-nl/animation/capture)  genereert lichaam en gezicht keyframes van opgenomen of geüploade video.

-

Speel animaties in een game:  Nadat je een animatie hebt gepubliceerd, speel je deze af vanuit een script of vervang je de standaardanimaties van een personage. Voor details, zie [Gebruik animaties](/docs/nl-nl/animation/using) .

-

Bouw animatielogica:  De [Animatiegrafiek-editor](/docs/nl-nl/animation/graph-editor)  bouwt gedragingen zoals blend trees in een node-gebaseerde editor in plaats van scripts.

## [Asset-werkstroom voor teams](#asset-werkstroom-voor-teams)[](#asset-werkstroom-voor-teams)

Teams houden vaak de canonieke versies van personages, bouwkits en set dressing als [pakketten](/docs/nl-nl/projects/assets/packages)  in een speciale assetplaats. Artiesten bewerken de pakketten daar, en elke plaats die ze gebruikt kan updaten naar de nieuwste versie. Nadat een leidinggevende een wijziging heeft goedgekeurd, kopiëren artiesten deze naar de gedeelde ontwikkelplaats of publiceren ze de pakketupdate. Voor de volledige teamopstelling, zie [Omgevingen](/docs/nl-nl/projects/file-based-workflows#omgevingen) .

## [Omgevingsprops](#omgevingsprops)[](#omgevingsprops)

-

Importeer en iterate:  Breng props binnen met de [3D Importer](/docs/nl-nl/studio/importer) . Wanneer je een prop in je modelleertool wijzigt, gebruik je [Reimport](/docs/nl-nl/art/modeling/reimport)  om de bestaande instanties en texturen ter plaatse bij te werken, met dezelfde importinstellingen.

-

Botsing:  Stel de [botsingsnauwkeurigheid](/docs/nl-nl/parts/meshes#botsingsnauwkeurigheid)  van elke mesh in op de eenvoudigste vorm die werkt. Box  is geschikt voor kleine of niet-interactieve objecten, Hull  is geschikt voor vormen zonder diepe holtes, en Default  ondersteunt concaafvormen.

-

Oppervlakken:  Gebruik een [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  voor gedetailleerde, unieke props, en een [materiaal](/docs/nl-nl/parts/materials)  of [MaterialVariant](/docs/nl-nl/reference/engine/classes/MaterialVariant)  voor betegelde oppervlakken zoals muren en vloeren.

-

Herbruik:  Zet props die op veel plaatsen verschijnen om in pakketten, zodat elke kopie samen wordt bijgewerkt. Voor de teamopstelling, zie [Asset-werkstroom voor teams](#asset-werkstroom-voor-teams) .

## [Terrein](#terrein)[](#terrein)

Terrein is een raster van voxels , 4×4×4 studcellen die elk een materiaal hebben. Sculpt en verf het met de [Terrein-editor](/docs/nl-nl/studio/terrain-editor) , genereer het vanuit [hoogtekaarten en kleurkaarten](/docs/nl-nl/parts/terrain#hoogtekaarten-en-kleurkaarten) , of maak het aan vanuit scripts.

-

Materialen:  Terrein wordt geleverd met een set standaardmaterialen. Je kunt ook [aangepaste terreinmaterialen](/docs/nl-nl/parts/custom-terrain-materials)  schilderen, of [aangepaste materialen](/docs/nl-nl/parts/materials#aangepaste-materialen)  als overrides toepassen.

-

Uiterlijk:  Je kunt de kleuren van het terrein, het uiterlijk van water en de animatie van gras aanpassen. Voor alle opties, zie [Milieu-terrein](/docs/nl-nl/parts/terrain) .

## [Visuele effecten](#visuele-effecten)[](#visuele-effecten)

Effectobjecten worden gerenderd wanneer je ze aan een onderdeel of een bijlage koppelt. Voor een overzicht, zie [Effecten](/docs/nl-nl/effects) .

-

[Lichtbronnen](/docs/nl-nl/effects/light-sources) :  Punt-, spot- en oppervlakteverlichting.

-

[Deeltjesemitter](/docs/nl-nl/effects/particle-emitters) :  Deeltjes zoals vuur, rook, vonken en magie. Een [flipbook](/docs/nl-nl/effects/particle-emitters#flipbooks)  textuur animeert een deeltje gedurende zijn levensduur, met een 2×2, 4×4, 8×8 of aangepaste frame-indeling. Laat ruimte tussen frames. Klanten schakelen flipbooks uit wanneer ze weinig geheugen hebben, dus hergebruik flipbook-texturen en houd hun resolutie zo laag mogelijk.

-

[Stralen](/docs/nl-nl/effects/beams)  en [sporen](/docs/nl-nl/effects/trails) :  Texturen getekend tussen twee bijlagen, of tussen en achter twee bijlagen terwijl ze bewegen.

-

[Hoogtepunten](/docs/nl-nl/effects/highlighting) :  Contouren en vullingen die de aandacht op objecten vestigen.

-

Scherm- en luchteffecten:  [Post-processing effecten](/docs/nl-nl/environment/post-processing-effects) , [atmosfeer](/docs/nl-nl/environment/atmosphere) , en de [skybox](/docs/nl-nl/environment/skybox)  stellen de algehele sfeer in.

## [Audio](#audio)[](#audio)

-

Importvereisten:  Een audiobestand moet een enkele track zijn in .mp3 , .ogg , .wav , of .flac  formaat, minder dan 20 MB en 7 minuten lang, met een samplefrequentie van 48 kHz of minder. ID-geverifieerde makers kunnen elke 30 dagen 2.000 audio-assets importeren, en niet-geverifieerde makers kunnen 100 importeren. Voor details, zie [Audio-assets](/docs/nl-nl/audio/assets) .

-

Gelicentieerde bibliotheek:  De Creator Store heeft meer dan 100.000 gratis, professioneel geproduceerde geluidseffecten en muziekstukken van audio- en muziekpartners.

-

Afspelen:  [Audio-objecten](/docs/nl-nl/audio/objects)  spelen geluiden positioneel in de wereld of niet-positioneel af, en [audio-effecten](/docs/nl-nl/audio/effects)  verwerken ze, zoals met galm of equalization. Voor een overzicht, zie [Audio](/docs/nl-nl/audio) .

-

Auteurschap:  Voor tips over het maken van geluiden in een digitale audio workstation, zie [Reaper](/docs/nl-nl/art/reaper) .

## [Plugins en tools](#plugins-en-tools)[](#plugins-en-tools)

Je kunt community-plugins installeren vanuit de [Creator Store](/docs/nl-nl/production/creator-store#vind-assets) , of je eigen bouwen. Voor details, zie [Studio-plugins](/docs/nl-nl/studio/plugins) . Roblox biedt ook deze tools voor artiesten:

-

[Avatar Setup](/docs/nl-nl/avatar-setup) :  Verwerkt aangepaste modellen in avatarlichamen en accessoires, en voegt de componenten toe die ze nodig hebben.

-

[Reimport](/docs/nl-nl/art/modeling/reimport) :  Werkt geïmporteerde meshes en texturen ter plaatse bij vanuit je bronbestanden.

-

[Projectbestanden](/docs/nl-nl/art/modeling/project-files) :  Blender, Maya, en .fbx  sjablonen en referentiebestanden.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
