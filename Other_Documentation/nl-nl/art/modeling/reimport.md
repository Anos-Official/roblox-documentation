<!-- Source: https://create.roblox.com/docs/nl-nl/art/modeling/reimport -->

Herimporteren | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Assets](/docs/nl-nl/assets)

# Herimporteren

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Herimporteren  stelt je in staat om bestaande aangepaste modellen en hun texturen bij te werken vanuit een extern 3D-bestand. In tegenstelling tot reguliere [importeren](/docs/nl-nl/studio/importer#bestanden-importeren) , die gloednieuwe instanties creëert, werkt de herimportfunctie bestaande objecten niet-destructief bij om de iteratieve aard van 3D-ontwikkeling te ondersteunen.

Naast asset-updates onthoudt herimporteren het bestand en de instellingen die zijn gebruikt om de oorspronkelijke asset te importeren. Dit betekent dat je een geïmporteerde asset eenvoudig kunt bijwerken met een enkele klik of sneltoets zonder door alle initiële importinstellingen te gaan. Dit geheugen blijft behouden tussen Studio-sessies.

## [Ondersteunde instanties](#ondersteunde-instanties)[](#ondersteunde-instanties)

Herimporteren ondersteunt de volgende toegangspunten in de Verkenner. Herimporteren ondersteunt ook [pakketten](/docs/nl-nl/projects/assets/packages) , waardoor je batches van asset-instanties tegelijk kunt herimporteren.

-

[Model](/docs/nl-nl/reference/engine/classes/Model)  - De herimportfunctie scant de container, werkt alle gewijzigde [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  en [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  instanties bij en voegt nieuw gemaakte toe, terwijl je bestaande eigenschappen onveranderd blijven. Herimporteren vervangt meshes op basis van mesh-namen die zijn opgeslagen in Studio en het externe 3D-bestand (zie [MeshPart-detectie](#meshpart-detectie) ). Het vervangt afbeeldingen voor PBR-texturen op basis van bestandsnamen (zie [SurfaceAppearance-detectie](#surfaceappearance-detectie) ).

-

[SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  of [Decal](/docs/nl-nl/reference/engine/classes/Decal)  (direct geselecteerd) - Herimporteren uploadt alle textuurkaarten die in dezelfde map als het geselecteerde bestand zijn gevonden in één bewerking.

Het geheugen van herimporteren is lokaal voor je apparaat. Een Herimport-ID wordt opgeslagen op de [Model](/docs/nl-nl/reference/engine/classes/Model)  instantie en lokaal verwezen. Houd rekening met het volgende:

-

Bestandslocaties worden nooit opgeslagen in het plaatsbestand.

-

Herimporteren ondersteunt verschillende herimportpaden op verschillende apparaten voor dezelfde instantie.

-

Herimporteren ondersteunt kopiëren-plakken, opslaan en laden van .rbxm / .rbxl , en [Asset Manager](/docs/nl-nl/projects/assets/manager)  workflows.

### [MeshPart-detectie](#meshpart-detectie)[](#meshpart-detectie)

Herimporteren werkt meshes bij op basis van het pad en de naam van het 3D-bronbestand, en het pad en de naam van het mesh-object in Studio. Herimporteren werkt alleen de mesh-inhoud en transformatie-eigenschappen bij en behoudt andere Roblox-specifieke eigenschappen, waaronder [CollisionFidelity](/docs/nl-nl/reference/engine/classes/MeshPart#CollisionFidelity)  en [RenderFidelity](/docs/nl-nl/reference/engine/classes/MeshPart#RenderFidelity) . Als de binnenkomende mesh geen textuur heeft toegewezen, behoudt herimporteren de bestaande [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  textuur in plaats van deze te wissen.

Herimporteren is afhankelijk van het overeenkomen van mesh-namen tussen Studio en het 3D-bronbestand:

-

Als een mesh's pad/naam  in het 3D-bronbestand overeenkomt  met een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  pad/naam  in Studio, werkt herimporteren de overeenkomende [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  bij.

-

Als een mesh's pad/naam  in het 3D-bronbestand niet bestaat  als [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  pad/naam  in Studio, maakt herimporteren een nieuwe [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  binnen de [Model](/docs/nl-nl/reference/engine/classes/Model) .

-

Als een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  pad/naam  in Studio niet bestaat  in het 3D-bronbestand, wijzigt herimporteren de [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  in Studio niet.

#### [Bekende asset-cache](#bekende-asset-cache)[](#bekende-asset-cache)

Studio gebruikt een bekende asset-cache  die helpt bij het detecteren van dubbele imports in dezelfde Studio-sessie. Als een geïmporteerde of hergeïmporteerde asset wordt gedetecteerd, hergebruikt Roblox de bestaande asset-ID in plaats van een nieuwe asset te creëren en te uploaden.

Als je probeert een enkele mesh-object te herimporteren, maar het 3D-bestand bevat een groter aantal meshes of texturen, past Roblox alleen een enkele asset-upload toe voor dat object.

#### [Duplicaten](#duplicaten)[](#duplicaten)

Herimporteren detecteert dubbele meshes en uploadt geen overeenkomende meshes die hetzelfde zijn in zowel Studio als het 3D-bronbestand opnieuw. In het scenario waarin een mesh in Blender wordt hernoemd van Mesh1  naar Mesh2 , maakt herimporteren een nieuwe [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  genaamd Mesh2  en past geen wijzigingen toe op de oorspronkelijke Mesh1 .

#### [Pivotpunten](#pivotpunten)[](#pivotpunten)

In gevallen waarin je mogelijk het pivotpunt van de [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  wilt gebruiken en niet het [Model](/docs/nl-nl/reference/engine/classes/Model) , klik met de rechtermuisknop op een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  met herimportinformatie en selecteer Herimporteren  ⟩ Herimporteren ten opzichte van deze . Dit activeert een herimport voor het hele model met het pivotpunt van de rechtermuisklikte [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  als anker in plaats van het pivotpunt van de [Model](/docs/nl-nl/reference/engine/classes/Model) . Je kunt dit gebruiken voor modellen die aangepaste pivots hebben door te herimporteren ten opzichte van een mesh die in het 3D-bestand niet van positie is veranderd.

### [SurfaceAppearance-detectie](#surfaceappearance-detectie)[](#surfaceappearance-detectie)

Herimporteren kan snel de texturen van een model met [PBR-texturen](/docs/nl-nl/art/modeling/surface-appearance)  in batch bijwerken op basis van de naamgevingsconventie van de afbeeldingsbestanden.

Herimporteren detecteert een set bekende achtervoegsels voor kleur-, metalness-, normaal-, ruwheid- en emissieve kaarten. Je kunt de volledige lijst van ondersteunde achtervoegsels in de volgende tabel vinden:

| Kaarttype | | Achtervoegsels | | Voorbeeld |
| --- | --- |
| [Kleur](/docs/nl-nl/art/modeling/surface-appearance#kleur-albedo) | | color , col , diffuse , diff , albedo , alb , base | | Tree_Color.png |
| [Metalness](/docs/nl-nl/art/modeling/surface-appearance#metaalheid) | | metal , metallic , metalness , mtl , met | | Tree_Metal.png |
| [Ruwheid](/docs/nl-nl/art/modeling/surface-appearance#ruwheid) | | rough , roughness , rgh | | Tree_Rough.png |
| [Normaal](/docs/nl-nl/art/modeling/surface-appearance#normaal) | | normal , nor , nrm , nrml , norm | | Tree_Normal.png |
| [Emissieve Masker](/docs/nl-nl/art/modeling/surface-appearance#emissief-masker) | | emissive , emission , emiss , emit , glow , illum , selfillum , light , luminance , emissivemask | | Tree_Emissive.png |

Wanneer je een asset met een geselecteerde [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  herimporteert, verschijnt er een bestandsdialoog waarmee je een nieuw afbeeldingsbestand kunt selecteren om als PBR-textuur te gebruiken. Herimporteren detecteert automatisch andere PBR-afbeeldingen in de map op basis van naamgeving en koppelt ze aan het [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  object.

Textuurbestanden zonder een erkend materiaalkaartachtervoegsel worden geaccepteerd als de kleurkaart voor [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  herimport.

## [Herimporteren van modellen](#herimporteren-van-modellen)[](#herimporteren-van-modellen)

Wanneer je een asset in Studio brengt via de [importeur](/docs/nl-nl/studio/importer#bestanden-importeren) , slaat herimporteren automatisch het bestands pad, importpreset en uploadinventaris op, zodat daaropvolgende herimporten geen handmatige configuratie vereisen.

Om een geconfigureerde [Model](/docs/nl-nl/reference/engine/classes/Model)  te herimporteren:

1.

Klik met de rechtermuisknop op de [Model](/docs/nl-nl/reference/engine/classes/Model)  en selecteer Herimporteren  ⟩ Herimporteren  in het contextmenu.

-

Alternatief, wanneer je het object selecteert, gebruik de herimport sneltoets Alt Shift R .

-

Een laadindicator verschijnt na het selecteren van herimporteren. Als er problemen zijn, verschijnt er een foutdialoog met een Configureer Herimportinstellingen  knop die de Configureer  dialoog opent.

Als een [Model](/docs/nl-nl/reference/engine/classes/Model)  geen opgeslagen herimportconfiguratie heeft (bijvoorbeeld een model dat op een ander apparaat is geïmporteerd of voordat herimporteren beschikbaar was), opent het activeren van Herimporteren  de Configureer  dialoog in plaats van de herimport te starten. Je kunt het ook op elk moment rechtstreeks openen via Herimporteren  ⟩ Configureren . In deze dialoog kun je het bestands pad, uploaddoel en importpresets instellen.

Aangezien herimporteren afhankelijk is van het overeenkomen van mesh-paden/namen om een [Model](/docs/nl-nl/reference/engine/classes/Model)  bij te werken vanuit een 3D-bestand, is het belangrijk om unieke namen van meshes en hun paden in je externe 3D-tools te behouden. In Studio moet je ook de naamgeving/bomenstructuur van de [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  objecten binnen je model behouden zodat herimporteren correct kan bijwerken.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
