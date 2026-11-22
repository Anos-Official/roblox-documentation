<!-- Source: https://create.roblox.com/docs/nl-nl/studio/importer -->

Importeur | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Assets](/docs/nl-nl/assets)

# Importeur

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De Importeur stelt je in staat om 3D-modellen, afbeeldingen, geluiden en videobestanden in Studio te importeren. De import van 3D-modellen ondersteunt meshes met PBR-texturen, meshes met rigging, skinning en animatiedata, en meshes die zijn ontworpen als avataritems.

Importeer algemene 3D-aangepaste modellen in Studio.

Gebruik de Importeur om assets met avataritemcomponenten te importeren.

Om een asset te importeren:

1.

Selecteer Importeren  in het Bestand  menu van Studio.

2.

Selecteer in de bestandsbrowser het [ondersteunde bestandstype](#ondersteunde-bestandstypen)  dat je wilt importeren.

3.

Configureer je importinstellingen en controleer eventuele [waarschuwing- of foutmeldingen](#waarschuwingen-en-fouten) .

4.

Klik op Importeren .

5.

Na het importeren kun je met de rechtermuisknop op de geïmporteerde asset in de importeur klikken en het volgende doen:

1.

Kopieer asset-ID  - Kopieert de geüploade asset-ID naar je klembord. Voor modellen kopieert dit de asset-ID van de [Model](/docs/nl-nl/reference/engine/classes/Model) .

2.

Vind in Workspace  (alleen 3D-modellen) - Positioneert automatisch de camera naar de locatie van het geïmporteerde object in de workspace.

Om assets rechtstreeks te importeren met HTTP-verzoeken, zie de [Open Cloud gebruiksgids voor assets](/docs/nl-nl/cloud/guides/usage-assets) .

## [Ondersteunde bestandstypen](#ondersteunde-bestandstypen)[](#ondersteunde-bestandstypen)

Zorg ervoor dat het .fbx , .gltf  of .obj  3D-object voldoet aan de [meshvereisten](/docs/nl-nl/avatar/character-bodies/specifications)  van Studio om fouten of onverwacht gedrag te verminderen.

| Asset Type | | Details |
| --- | --- |
| Afbeelding | | Je kunt afbeeldingen in .png , .jpg , .gif , .tga  of .bmp  formaat importeren voor gebruik als [texturen/decal](/docs/nl-nl/parts/textures-decals)  op onderdelen, [afbeelding labels](/docs/nl-nl/ui/labels) , [mesh texturen](/docs/nl-nl/parts/meshes#textuur) , texturen voor [aangepaste materialen](/docs/nl-nl/parts/materials#aangepaste-materialen) , texturen voor [speciale effecten](/docs/nl-nl/effects) , en meer. |
| Mesh | | Je kunt meshes in het .fbx , .obj  of .gltf  formaat importeren.
De .fbx  en .gltf  formaten ondersteunen meerdere mesh-objecten en hiërarchieën, basis- en [PBR-texturen](/docs/nl-nl/art/modeling/surface-appearance) , cage mesh-objecten, [rigs](/docs/nl-nl/art/modeling/rigging) , [avatarcomponenten](/docs/nl-nl/avatar) , animatiedata en [vertexkleuren](/docs/nl-nl/art/blender#vertexverf) .  |
| Audio | | Je kunt audio-assets importeren in het .ogg , .mp3 , .flac  of .wav  formaat. Zie [Audio-assets](/docs/nl-nl/audio/assets#audio-importeren)  voor details. |
| Video | | Je kunt video-assets importeren in het .mp4  of .mov  formaat als aan alle [vereisten](/docs/nl-nl/ui/video-frames)  is voldaan. |

### [glTF importhiërarchie](#gltf-importhiërarchie)[](#gltf-importhiërarchie)

.gltf  en .glb  bestanden importeren met een andere hiërarchie dan .fbx  bestanden. De volgende tabel vergelijkt wat er in de Explorer verschijnt nadat je dezelfde mesh met cage meshes in elk formaat hebt geïmporteerd.

|  | | .fbx | | .gltf  / .glb |
| Topniveau | | Een [Model](/docs/nl-nl/reference/engine/classes/Model) . | | Een [Model](/docs/nl-nl/reference/engine/classes/Model) . |
| Mesh | | Een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  direct binnen het topniveau Model . | | Een [Model](/docs/nl-nl/reference/engine/classes/Model)  binnen het topniveau Model , met één [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  voor elke primitieve in de glTF-mesh. |
| Cage meshes | | Een [WrapLayer](/docs/nl-nl/reference/engine/classes/WrapLayer)  binnen de MeshPart . | | Een [WrapLayer](/docs/nl-nl/reference/engine/classes/WrapLayer)  binnen de MeshPart , plus een extra [Model](/docs/nl-nl/reference/engine/classes/Model)  voor elke oorspronkelijke binnen- en buiten-cageknoop. Je kunt deze extra modellen na import verwijderen. |

Bij een glTF-import, als een knooppunt en zijn mesh dezelfde naam hebben, zoals Cover , voegt de Importeur een _Node  suffix toe aan een van hen, zoals Cover_Node .

## [Importwachtrij](#importwachtrij)[](#importwachtrij)

Als je meerdere bestanden met de Importeur hebt geselecteerd, kun je de importwachtrij gebruiken om je verschillende imports in bulk te beheren.

 ![De interface van de Importeur, met een voorbeeld van de mesh in de linkerbovenhoek, een lijst van 3D-objecten onderaan links, en een lijst van in- en uitschakelbare eigenschappen aan de rechterkant.](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/3d-Import-Queue.png)

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-A.png)

De bovenste balk  stelt je in staat om nieuwe bestanden toe te voegen, de wachtrij te wissen, te zoeken en te filteren, en alle ingeschakelde assets te importeren.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-B.png)

De importwachtrij  toont alle toegevoegde bestanden, met snelle toegang dropdowns om maker, presets en bestandslocaties te wijzigen.

### [Bestanden aan de wachtrij toevoegen](#bestanden-aan-de-wachtrij-toevoegen)[](#bestanden-aan-de-wachtrij-toevoegen)

Om een bestandsbrowser te openen en extra bestanden aan de importwachtrij toe te voegen, kun je:

-

Klik op de Bestand toevoegen  knop in de bovenste balk van het importwachtrijvenster.

-

Selecteer Importeren  in het Bestand  menu van Studio.

### [Bestanden uit de wachtrij verwijderen](#bestanden-uit-de-wachtrij-verwijderen)[](#bestanden-uit-de-wachtrij-verwijderen)

Om alle bestanden uit de wachtrij te verwijderen, klik je op de Wachtrij wissen  knop met het bezemicoon. Om een individueel bestand uit de wachtrij te verwijderen, klik je met de rechtermuisknop op een item in de wachtrij en selecteer je Verwijder uit wachtrij .

### [Presetinstellingen toepassen](#presetinstellingen-toepassen)[](#presetinstellingen-toepassen)

Gebruik de Importpreset  kolom om een presetconfiguratie te selecteren die je op je asset wilt toepassen. Voor meer informatie, zie [Presets](#presets) .

Je kunt ook de instellingen van één item op alle items toepassen door met de rechtermuisknop op een item met de gewenste instellingen te klikken en Instellingen op alle toepassen  te selecteren.

### [Toegang tot individuele voorbeeldweergave en instellingen](#toegang-tot-individuele-voorbeeldweergave-en-instellingen)[](#toegang-tot-individuele-voorbeeldweergave-en-instellingen)

Als je een 3D-model importeert, klik dan op de individuele Asset  naam van een niet-geïmporteerd model om toegang te krijgen tot de [importvoorbeeldweergave](#importvoorbeeld-modellen)  voor dat item. Gebruik de importvoorbeeldweergave om je model te bekijken en te controleren, evenals om eventuele individuele [importinstellingen](#importinstellingen)  in te stellen.

### [Bestanden importeren](#bestanden-importeren)[](#bestanden-importeren)

Zorg ervoor dat elk item dat je wilt importeren een aangevinkt selectievakje heeft in de eerste kolom. Standaard zijn alle items geselecteerd als ze importeerbaar zijn.

Druk op de Importeren  knop om het importproces te starten.

## [Importvoorbeeld (Modellen)](#importvoorbeeld-modellen)[](#importvoorbeeld-modellen)

Het importvoorbeeldvenster verschijnt als je een enkel modelbestand importeert, of als je een individueel asset uit de importwachtrij hebt geselecteerd. Dit voorbeeldvenster biedt individuele bedieningselementen voor de verschillende objecten in je model.

Het voorbeeldvenster is verdeeld in meerdere secties:

 ![De interface van de Importeur, met een voorbeeld van de mesh in de linkerbovenhoek, een lijst van 3D-objecten onderaan links, en een lijst van in- en uitschakelbare eigenschappen aan de rechterkant.](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/3d-Importer-Panels.png)

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-A.png)

Het bestands pad  van je modelbestand. Klik op Bladeren  om te bewerken.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-B.png)

De preset  die op je import is toegepast. Gebruik de dropdown om meerdere presets te selecteren, of het hamburgermenu om een nieuwe preset in te stellen.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-C.png)

De 3D-voorbeeldweergave  van je model. Gebruik muisknoppen en iconen rechtsboven voor verschillende camera-opties en weergaven.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-D.png)

De objecthiërarchie  van het geïmporteerde object. Bevat mesh-objecten en andere ondersteunde componenten.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-E.png)

De importinstellingen  voor je import. Voor een complete lijst van instellingen, zie [Importinstellingen](#importinstellingen) .

### [Importinstellingen](#importinstellingen)[](#importinstellingen)

Afhankelijk van het object dat is geselecteerd in het hiërarchiepaneel, toont het inspectiepaneel de volgende groepen instellingen:

-

Algemeen bestand : Heeft invloed op het gehele geïmporteerde bestand.

-

Algemeen rig : Heeft invloed op het geselecteerde mesh-object als riggingdata aanwezig is.

-

Bestandstransformatie : Heeft invloed op de transformatie-eigenschappen van het geïmporteerde bestand.

-

Bestandsgeometrie : Heeft invloed op de geometrie-eigenschappen van het geïmporteerde bestand.

-

Algemeen object : Heeft invloed op het geselecteerde kindobject.

-

Objectgeometrie : Heeft invloed op de geometrie van het geselecteerde kindobject.

#### [Algemeen bestand](#algemeen-bestand)[](#algemeen-bestand)

De Importeur biedt de volgende instellingen voor alle meshes:

| Instelling | | Beschrijving |
| Naam | | Stelt de naam van de geïmporteerde asset in zoals deze in je project zal verschijnen. |
| Importeer alleen als model | | Als ingeschakeld, importeert de Importeur het model als een enkele asset, zelfs als het model meerdere kinderen bevat. Standaard is dit ingeschakeld .
Als uitgeschakeld, importeert de Importeur het model en alle afstammelingen, zoals de meerdere meshes, als individuele assets. |
| Upload naar Roblox | | Als ingeschakeld, voegt de Importeur het model toe aan je Toolbox  en Asset Manager  inventaris als een nieuwe asset. Standaard is dit ingeschakeld .
Als uitgeschakeld, voegt de Importeur het model niet toe aan je inventaris voor later gebruik. Dit is ideaal wanneer je een modelontwerp wilt testen en itereren zonder meerdere kopieën in de Toolbox en Asset Manager te maken. |
| Importeer als pakket | | Voegt je asset toe aan de workspace als een [pakket](/docs/nl-nl/projects/assets/packages) , een automatisch bijgewerkt, schaalbaar en deelbaar formaat dat wordt aanbevolen voor assets die opnieuw worden gebruikt of vaak worden verspreid. Standaard is dit uitgeschakeld . |
| Maker | | Stelt de maker of maker groep voor de asset in. |
| Toevoegen aan Workspace | | Als ingeschakeld, plaatst de Importeur het model in de [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) . Als je importeert vanuit een opgeslagen of gepubliceerde game, verleent deze instelling ook toestemming aan de game om de beperkte asset te gebruiken. Standaard is dit ingeschakeld .
Als uitgeschakeld, voegt deze instelling alleen het model toe aan je inventaris en verleent geen  toestemming aan de game om de asset te gebruiken. |
| Invoegen met scènepositie | | Als ingeschakeld, gebruikt de Importeur de huidige scènepositie bij het invoegen van het model in de workspace. Standaard is dit uitgeschakeld . |
| Behouden van nul-invloed botten | | Als ingeschakeld, houdt de importeur botten die geen invloed hebben op de mesh. Standaard is dit uitgeschakeld .
Als uitgeschakeld, verwijdert de importeur nul-invloed botten. |
| Pivot instellen op scène-oorsprong | | Als ingeschakeld, stelt de Importeur het draaipunt van het gehele model in op de scène-oorsprong. Standaard is dit ingeschakeld . |
| Verankerd | | Als ingeschakeld, stelt de Importeur de [Anchored](/docs/nl-nl/reference/engine/classes/BasePart#Anchored)  eigenschap in op true  voor alle geïmporteerde [MeshParts](/docs/nl-nl/reference/engine/classes/MeshPart) . Dit is uitgeschakeld voor meshes met rigdata / avatars. Standaard is dit uitgeschakeld . |
| Gebruikt Cage | | Als ingeschakeld, vindt de Importeur cage meshes in het model en converteert deze naar WrapInstance  objecten, zoals [WrapLayer](/docs/nl-nl/reference/engine/classes/WrapLayer)  of [WrapTarget](/docs/nl-nl/reference/engine/classes/WrapTarget) . Als uitgeschakeld, behandelt de Importeur ze als reguliere meshes. Als de Importeur aanvankelijk cage meshes in het model detecteert, is dit standaard ingeschakeld . |

#### [Algemeen rig](#algemeen-rig)[](#algemeen-rig)

De Importeur biedt de volgende instellingen voor meshes met riggingdata, typisch voor karakterlichamen of kledingaccessoires:

| Instelling | | Beschrijving |
| Rig Type | | Stelt het type rig in waarmee de mesh moet worden geassocieerd. De opties zijn:
- R15
- Aangepast
- Geen Rig
Standaard probeert de Importeur de meest geschikte instelling te selecteren op basis van de gedetecteerde rigging- en skinningdata van de mesh.  |
| Valideer UGC Body | | Na het importeren opent Studio de assets in de [Avatar Setup](/docs/nl-nl/avatar-setup)  tool, zodat je snel kunt beginnen met het testen en uploaden van avatar-assets naar de Marketplace. |
| Rig Schaal | | Als Rig Type is ingesteld op R15, biedt de importeur extra opties om [lichaamstype-schaal](/docs/nl-nl/avatar/character-bodies/specifications#lichaamschaal)  op te geven. De opties zijn:
- Standaard
- Rthro
- Rthro Smal |

#### [Bestands transformatie](#bestands-transformatie)[](#bestands-transformatie)

De Importeur biedt de volgende instellingen voor alle meshes:

| Instelling | | Beschrijving |
| Wereld Vooruit | | Stelt de voorwaartse as van het object in. Standaard is dit ingesteld op Voor . |
| Wereld Omhoog | | Stelt de opwaartse as van het object in. Standaard is dit ingesteld op Boven . |

#### [Bestands geometrie](#bestands-geometrie)[](#bestands-geometrie)

Bestandsgeometrie bevat informatie over de afmetingen en polycount van het gehele model. Je kunt de volgende instellingen voor alle meshes bewerken:

| Instelling | | Beschrijving |
| Schaal Eenheid | | Stelt in welke eenheden het bestand is gemodelleerd, zodat het correct is geconfigureerd bij importeren. Standaard is dit ingesteld op Studs . |
| Mesh samenvoegen | | Als ingeschakeld, voegt het alle MeshParts in het model samen tot één MeshPart en creëert één MeshPart in plaats van een Model. Standaard is dit uitgeschakeld . |
| Negatieve Vlakken Inverteren | | Inverteert de oriëntatie van negatieve vlakken in de mesh. Standaard is dit uitgeschakeld . |

#### [Algemeen object](#algemeen-object)[](#algemeen-object)

Bij het selecteren van een specifiek kindobject van je mesh, vult de Importeur de instellingen voor Algemeen Object in. Je kunt de volgende instellingen voor de geselecteerde kindobjecten bewerken:

| Instelling | | Beschrijving |
| Naam | | Stelt de naam van het geselecteerde kindobject binnen het model in. |
| Verankerd | | Als ingeschakeld, stelt het de [Anchored](/docs/nl-nl/reference/engine/classes/BasePart#Anchored)  eigenschap in op true  voor het geselecteerde kindobject. Standaard is dit uitgeschakeld . |
| Gebruik Geïmporteerd Pivot | | Als ingeschakeld, importeert het object met het draaipunt dat binnen het kindobject is ingesteld. Standaard is dit ingeschakeld . |

#### [Object geometrie](#object-geometrie)[](#object-geometrie)

Objectgeometrie bevat informatie over de afmetingen en polycount van het geselecteerde kindobject van het model. Je kunt de volgende instellingen voor de geselecteerde kindobjecten bewerken:

| Instelling | | Beschrijving |
| Maak Dubbelzijdig | | Als uitgeschakeld, stelt het de vertices in als eenzijdig. Eenzijdige vertices betekent dat je er van één kant doorheen kunt kijken.
Als ingeschakeld, stelt het de vertices in als dubbelzijdig. Dubbelzijdige vertices worden visueel aan beide zijden weergegeven. Dubbelzijdig is intensiever voor de prestaties.
Standaard is dit uitgeschakeld .  |
| Negeer Vertexkleuren | | Als ingeschakeld, negeert het de vertexkleurdata in het kindobject. Standaard is dit uitgeschakeld .  |

## [Presets](#presets)[](#presets)

Je kunt presets van verschillende importinstellingen opslaan om ze later snel toe te passen binnen de [importvoorbeeldweergave](#importvoorbeeld-modellen)  of [importwachtrij](#importwachtrij) .

Standaard kun je kiezen tussen twee presets:

-

Studio Standaard : Het standaard importgedrag.

-

Laatst Geïmporteerd : Gebruikt de instellingen die zijn toegepast op de meest recente import.

Je kunt het ⋯  menu naast de Presets dropdown gebruiken voor extra opties:

-

Reset alles : Verwijdert eventuele wijzigingen in de huidige configuratie en zet de instellingen terug naar de standaardstatus voor de huidige preset.

-

Opslaan selectie : Hiermee kun je eventuele nieuwe wijzigingen in de importinstellingen opslaan in de momenteel geselecteerde preset.

-

Opslaan als nieuw : Stelt de huidige instellingen in als een nieuwe preset. Een dialoogvenster wordt weergegeven waarin je een naam kunt instellen.

-

Instellen als standaard : Stelt de huidige preset in als de standaard voor alle toekomstige imports.

-

Hernoemen : Hernoemt de huidige preset.

-

Verwijderen : Verwijdert de huidige preset. Reset naar de Studio Standaard  preset.

## [Waarschuwingen en fouten](#waarschuwingen-en-fouten)[](#waarschuwingen-en-fouten)

Als Studio problemen met je model detecteert, wordt er een klein indicator in het hiërarchiepaneel of het instellingenpaneel weergegeven.

Als je een waarschuwingpictogram in de hiërarchie ziet, vouw dan de hiërarchie uit totdat je het specifieke kindobject bereikt om meer informatie over het probleem te zien. Waarschuwing- en foutmeldingen worden weergegeven in het instellingenpaneel of als een tooltip.

![Een waarschuwing bericht in oranje dat een fout over cages mismatch aangeeft.](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Warning-Settings-Panel.png) Waarschuwing- en foutmeldingen worden weergegeven in de juiste sectie in het inspectiepaneel.

![Een foutmelding in het rood met een pop-up bericht over ontbrekende texturen.](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Warning-Mouse-Over.png) Sommige fouten tonen een tooltip wanneer je met de muis over het foutpictogram beweegt.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
