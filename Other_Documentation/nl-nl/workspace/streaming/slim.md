<!-- Source: https://create.roblox.com/docs/nl-nl/workspace/streaming/slim -->

SLIM | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Projecten](/docs/nl-nl/projects)
6. /
7. [Architectuur](/docs/nl-nl/projects/data-model)
8. /
9. [Instantiestreaming](/docs/nl-nl/workspace/streaming)

# SLIM

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

SLIM  (Scalable Lightweight Interactive Models) is een automatisch optimalisatiesysteem dat lichte, geoptimaliseerde representaties van [Models](/docs/nl-nl/reference/engine/classes/Model)  en platformavatars genereert met behulp van cloud-gebaseerde transcoding (het omzetten van assets naar efficiëntere formaten). Wanneer ingeschakeld, combineert SLIM meerdere onderdelen in minder draw calls (renderopdrachten die naar de GPU worden verzonden) en genereert het meerdere detailniveaus, waardoor de engine intelligent de beste representatie kan selecteren op basis van afstand, apparaatspecificaties en beschikbare middelen.

![](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/SLIM-Disabled.jpg) Zonder SLIM — gestreamde modellen zijn onzichtbaar

![](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/SLIM-Enabled.jpg) Met SLIM — geoptimaliseerde stand-ins blijven zichtbaar

SLIM biedt drie belangrijke voordelen:

-

Visuele kwaliteit

 — Afstandmodellen lijken gedetailleerder dan het legacy model niveau-van-detail systeem, met een betere trouw aan het origineel.

-

Consistente overgangen

 — Alle onderdelen binnen een model schakelen gelijktijdig detailniveaus, waardoor schokkende per-onderdeel overgangen worden geëlimineerd.

-

Prestaties

 — Composietmesh vermindert dramatisch het aantal draw calls, het aantal driehoeken en het geheugengebruik, waardoor rijkere scènes mogelijk zijn op alle apparaatsniveaus.

Verken SLIM in deze gepubliceerde games:

[![](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/SLIM-Demo-Models.png)](https://www.roblox.com/games/135885449743134/CPC-Slim-Template)  [City People Cars SLIM Template](https://www.roblox.com/games/135885449743134/CPC-Slim-Template)  — Wereldmodellen met SLIM ingeschakeld

[![](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/SLIM-Demo-Avatars.png)](https://www.roblox.com/games/81704282913046/SLIM-Platform-Avatars)  [SLIM Platform Avatars](https://www.roblox.com/games/81704282913046/SLIM-Platform-Avatars)  — 200 geanimeerde avatars gerenderd met SLIM

## [Vereisten](#vereisten)[](#vereisten)

SLIM vereist het volgende:

1.

[StreamingEnabled](/docs/nl-nl/reference/engine/classes/Workspace#StreamingEnabled)  moet ingeschakeld zijn op het [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  object. Zie ook [streaming eigenschappen](/docs/nl-nl/workspace/streaming/techniques#streaming-eigenschappen)  voor gerelateerde aanbevolen instellingen.

2.

De plaats moet opgeslagen zijn naar Roblox  (niet een lokaal .rbxl  bestand), aangezien SLIM cloud transcoding gebruikt om geoptimaliseerde assets te genereren. Als je lokaal test, publiceer de plaats en schakel dan SLIM in.

3.

[Team Create](/docs/nl-nl/projects/collaboration)  moet ingeschakeld zijn voor de game, aangezien SLIM afhankelijk is van bijbehorende eigenschappen voor cloud asset generatie.

## [Technisch gedrag](#technisch-gedrag)[](#technisch-gedrag)

Wanneer je een game publiceert of test met SLIM-ingeschakelde modellen, uploadt de engine modelgegevens naar een cloudservice die geoptimaliseerde composietmesh met meerdere detailniveaus genereert. Tijdens runtime halen clients deze assets van de CDN en selecteert de engine het juiste detailniveau op basis van afstand en apparaatspecificaties, waarbij elk SLIM-model wordt geclassificeerd in renderzones op basis van afstand van de camera:

 ![Diagram dat de vier SLIM renderzones toont, gekleurd in lichtblauw, teal, geel en vermiljoen, uitstralend vanuit een speler karakter.](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/SLIM-Zones.jpg)

| Bereik | | Data Model Status | | Rendering |
| --- | --- |
|  | | Volledige instanties gestreamd. | | Traditionele part-voor-part rendering. |
|  | | Volledige instanties gestreamd. | | De engine rendert de SLIM composiet wanneer dit efficiënter is. |
|  | | Instanties gestreamd. Slechts een minimale placeholder bestaat in het [DataModel](/docs/nl-nl/reference/engine/classes/DataModel) , niet de volledige modelhiërarchie. | | SLIM composiet rendering. |
|  | | Minimale placeholder in het [DataModel](/docs/nl-nl/reference/engine/classes/DataModel) . | | Niet gerenderd. |

## [SLIM voor modellen](#slim-voor-modellen)[](#slim-voor-modellen)

SLIM werkt het beste op modellen die statische wereldgeometrie  vertegenwoordigen — gebouwen, props, voertuigen, terreinfeatures en andere omgevingsobjecten die niet veranderen tijdens runtime. Het toevoegen of verwijderen van onderdelen, het wijzigen van materialen of het aanpassen van geometrie tijdens runtime voorkomt dat SLIM het model correct rendert. Zie [modelstructuur](/docs/nl-nl/workspace/streaming/techniques#modelstructuur)  voor algemene richtlijnen voor modelstructuur en [beperkingen](#beperkingen)  voor de volledige lijst van uitsluitingen.

Om SLIM op een model in te schakelen, stel je de [LevelOfDetail](/docs/nl-nl/reference/engine/classes/Model#LevelOfDetail)  eigenschap in op [SLIM](/docs/nl-nl/reference/engine/enums/ModelLevelOfDetail#SLIM)  in het [Eigenschappen](/docs/nl-nl/studio/properties)  venster.

 ![Het Eigenschappen venster met de LevelOfDetail eigenschap ingesteld op SLIM.](https://prod.docsiteassets.roblox.com/assets/studio/properties/Model-LevelOfDetail-SLIM.png)

Wanneer SLIM is ingesteld op een model, doet de engine:

1.

Serialiseert de rendering-relevante eigenschappen van het model (geometrie, materialen, texturen, transformaties) in een compacte representatie. Ondersteunde instantietypen binnen het model zijn [Part](/docs/nl-nl/reference/engine/classes/Part) , [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) , [Decal](/docs/nl-nl/reference/engine/classes/Decal) , [Texture](/docs/nl-nl/reference/engine/classes/Texture) , [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance) , [PartOperation](/docs/nl-nl/reference/engine/classes/PartOperation) , [NegateOperation](/docs/nl-nl/reference/engine/classes/NegateOperation) , en [SpecialMesh](/docs/nl-nl/reference/engine/classes/SpecialMesh) .

2.

Uploadt deze gegevens naar de cloud transcoding service bij de eerste publicatie of afspelen.

3.

De cloudservice genereert een gecompositeerde mesh met meerdere detailniveaus, verwijdert verborgen interne geometrie en optimaliseert texturen.

4.

Tijdens runtime halen clients de geoptimaliseerde SLIM asset op en renderen deze wanneer de engine het originele model streamt of wanneer SLIM efficiënter is dan het volledige model.

De initiële SLIM generatie kan enkele momenten duren voor complexe modellen. De cloudservice verwerkt assets op de achtergrond, dus als een model niet onmiddellijk als SLIM verschijnt na inschakeling, wacht dan 1–2 minuten en sluit opnieuw aan; de getranscodeerde asset blijft op de CDN en de client haalt deze op in de volgende sessie.

Converteren van Streaming Mesh

Als je game de legacy [StreamingMesh](/docs/nl-nl/reference/engine/enums/ModelLevelOfDetail#StreamingMesh)  instelling voor [Model.LevelOfDetail](/docs/nl-nl/reference/engine/classes/Model#LevelOfDetail)  gebruikt, kun je individuele modellen converteren door ze te selecteren en de eigenschap in het [Eigenschappen](/docs/nl-nl/studio/properties)  venster te wijzigen, of je kunt meerdere modellen tegelijk batch-converteren met een script zoals het volgende in de [Command Bar](/docs/nl-nl/studio/overview#opdrachtbalk) . Let op dat sommige modellen die werkten met [StreamingMesh](/docs/nl-nl/reference/engine/enums/ModelLevelOfDetail#StreamingMesh)  mogelijk aanpassingen nodig hebben voor SLIM, met name die met overlappende onderdelen of complexe [PartOperation](/docs/nl-nl/reference/engine/classes/PartOperation)  hiërarchieën.

Batch-Convert StreamingMesh to SLIM

```

for _, descendant in workspace:GetDescendants() do

    if descendant:IsA("Model") and descendant.LevelOfDetail ==

        Enum.ModelLevelOfDetail.StreamingMesh then

        descendant.LevelOfDetail = Enum.ModelLevelOfDetail.SLIM

    end

end

```

## [SLIM voor avatars](#slim-voor-avatars)[](#slim-voor-avatars)

Platformavatars buiten het momenteel gestreamde gebied zijn standaard niet zichtbaar. Het inschakelen van SLIM avatars rendert [standaard](/docs/nl-nl/avatar/character-bodies/specifications)  spelerkarakters — ongeacht hoeveel accessoires of kledinglagen ze hebben — als lichte, geanimeerde stand-ins die visuele trouw behouden tegen een fractie van de renderkosten.

Publiek op Grote Afstand Publiek in Dichte Nabijheid

![](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/SLIM-Avatars-Enabled-Far.jpg)

SLIM Ingeschakeld

~170.000 driehoeken

~4.000 clientinstanties

![](https://prod.docsiteassets.roblox.com/assets/optimization/streaming/SLIM-Avatars-Disabled-Far.jpg)

SLIM Uitgeschakeld

~2.600.000 driehoeken

~60.000 clientinstanties

De belangrijkste SLIM-specifieke eigenschap voor avatars is [Workspace.EnableSLIMAvatars](/docs/nl-nl/reference/engine/classes/Workspace#EnableSLIMAvatars)  die moet worden ingesteld op [Enabled](/docs/nl-nl/reference/engine/enums/RolloutState#Enabled)  in het Eigenschappen  venster, naast [LevelOfDetail](/docs/nl-nl/reference/engine/classes/Model#LevelOfDetail)  ingesteld op [SLIM](/docs/nl-nl/reference/engine/enums/ModelLevelOfDetail#SLIM)  op je niet-avatar wereldmodellen.

 ![Het Eigenschappen venster met de EnableSLIMAvatars eigenschap ingesteld op Ingeschakeld.](https://prod.docsiteassets.roblox.com/assets/studio/properties/Workspace-EnableSLIMAvatars.png)

Met [EnableSLIMAvatars](/docs/nl-nl/reference/engine/classes/Workspace#EnableSLIMAvatars)  ingeschakeld, doet de engine:

-

Rendert een SLIM-versie wanneer een daadwerkelijk avatar model streamt.

-

Wisselt tussen SLIM en full-resolution representaties op basis van beschikbare middelen, zelfs binnen de streamingradius.

-

Beperkt SLIM-animaties op basis van scene belangrijkheid en beschikbare bandbreedte.

Ondersteunde Avatars

-

R15 avatars met een lichaam, dynamisch hoofd, [standaard](/docs/nl-nl/avatar/character-bodies/specifications#standaard-r15-rigs)  of [geavanceerd](/docs/nl-nl/avatar/character-bodies/specifications#geavanceerde-r15-rigs)  R15 rig, en rigide/gelaagde accessoires.

-

Avatar wijzigingen gemaakt tussen de [CharacterAdded](/docs/nl-nl/reference/engine/classes/Player#CharacterAdded)  gebeurtenis en de [CharacterAppearanceLoaded](/docs/nl-nl/reference/engine/classes/Player#CharacterAppearanceLoaded)  gebeurtenis.

-

Avatars gedefinieerd door StarterHumanoid  of StarterCharacter  onder de [StarterPlayer](/docs/nl-nl/reference/engine/classes/StarterPlayer)  service.

Uitsluitingen van Avatars

-

R6 avatars.

-

NPC-personages (zelfs die met een standaard of geavanceerd R15 rig).

-

Avatars met aangepaste verhoudingen, lichaamsvergroting of door de ervaring toegepaste avatarinstellingen.

-

Avatar wijzigingen gemaakt na de [CharacterAppearanceLoaded](/docs/nl-nl/reference/engine/classes/Player#CharacterAppearanceLoaded)  gebeurtenis (gereedschappen uitrusten, accessoires wijzigen, [Highlight](/docs/nl-nl/reference/engine/classes/Highlight)  toevoegingen, enz.).

-

Avatar wijzigingen gemaakt door [StarterCharacterScripts](/docs/nl-nl/reference/engine/classes/StarterCharacterScripts) .

SLIM Avatars Testen

In tegenstelling tot [model SLIM](#slim-voor-modellen)  dat je alleen kunt testen door ver van een model te bewegen totdat het streamt, vereisen SLIM avatars meerdere spelers in de game om te observeren. Gebruik een van deze [testmodi](/docs/nl-nl/studio/testing-modes)  om SLIM avatars te testen:

-

[Team Test](/docs/nl-nl/studio/testing-modes#samenwerkend-testen)  — Sluit je aan met vrienden of alternatieve accounts om SLIM avatars op afstand te zien.

-

[Server en Clients](/docs/nl-nl/studio/testing-modes#multi-client-simulatie)  — Start twee of meer clientvensters waarin elke client avatar kopieën weergeeft die de anderen als SLIM renderen wanneer ze op afstand zijn.

Let op dat avatars getranscodeerd moeten zijn in een SLIM-ingeschakelde game voordat ze als SLIM verschijnen. Als avatars niet als SLIM worden gerenderd in je eerste test, sluit dan opnieuw aan na een moment om de transcoding te laten voltooien.

## [Beperkingen](#beperkingen)[](#beperkingen)

| Beperking | | Details |
| Streaming vereist | | SLIM functioneert alleen met [StreamingEnabled](/docs/nl-nl/reference/engine/classes/Workspace#StreamingEnabled)  ingesteld op true . Zonder streaming vallen SLIM-geschikte modellen terug op traditionele niveau-van-detail rendering. |
| Statische modellen alleen | | [Model SLIM](#slim-voor-modellen)  ondersteunt geen modellen die tijdens runtime zijn gewijzigd (onderdelen toegevoegd/verwijderd, eigenschappen gewijzigd) of modellen die animaties afspelen. |
| Humanoid instanties | | De engine sluit modellen met een [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  uit van statische [model SLIM](#slim-voor-modellen)  verwerking. Gebruik [SLIM avatars](#slim-voor-avatars)  voor geanimeerde spelerkarakters. |
| Avatar beperkingen | | [SLIM avatars](#slim-voor-avatars)  ondersteunen alleen R15 spelerkarakters. R6 rigs, NPC's en avatars met aangepaste verhoudingen vallen terug op standaard rendering. |
| Cloud afhankelijkheid | | De cloudservice genereert en slaat SLIM-assets op de CDN op. Offline of lokale tests zonder een gepubliceerde plaats produceren geen SLIM-resultaten. |
| Zero-scale modellen | | De engine sluit modellen met een [Scale](/docs/nl-nl/reference/engine/classes/Model#Scale)  van 0  uit van SLIM verwerking. |
| Platform beschikbaarheid | | Op platforms waar SLIM nog niet wordt ondersteund, vallen modellen ingesteld op [SLIM](/docs/nl-nl/reference/engine/enums/ModelLevelOfDetail#SLIM)  terug op [Disabled](/docs/nl-nl/reference/engine/enums/ModelLevelOfDetail#Disabled) . |

## [Debugging](#debugging)[](#debugging)

Om de status van SLIM-modellen beter te begrijpen, biedt Roblox verschillende debug tintmodi  in de DebugVisualizations  ⟩ SlimTintMode  dropdown van de [Developer Console](/docs/nl-nl/studio/developer-console) . Let op dat dit menu alleen beschikbaar is voor makers die Bewerken  rechten voor de game hebben.

 ![](https://prod.docsiteassets.roblox.com/assets/optimization/debug-visualizations/SLIM-Tint-Mode-Menu.jpg)

Er zijn meerdere tintmodi om uit te kiezen. Zie [Enum.SlimTintMode](/docs/nl-nl/reference/engine/enums/SlimTintMode)  voor de kleurtoewijzingen van elke modus.

LOD Data Model Status

[LOD](/docs/nl-nl/reference/engine/enums/SlimTintMode#LOD)  kleurt elke mesh op basis van het huidige detailniveau met behulp van een blauw-naar-rood warmtemap. Blauw geeft het laagste detail aan en warmere kleuren geven hoger detail aan.

Je kunt ook SLIM debugvisualisaties in Studio zien door een tintmodus te selecteren uit het [Visualisatie Opties](/docs/nl-nl/studio/overview#visualisatie-opties)  menu:

 ![Een close-up van het 3D viewport met de Visualisatie Opties knop aangegeven in de rechterbovenhoek.](https://prod.docsiteassets.roblox.com/assets/studio/general/Visualization-Options.png)

Naast de [LOD](/docs/nl-nl/reference/engine/enums/SlimTintMode#LOD) /[DataModelState](/docs/nl-nl/reference/engine/enums/SlimTintMode#DataModelState)  tintmodi, biedt Studio de [TranscoderStatus](/docs/nl-nl/reference/engine/enums/SlimTintMode#TranscoderStatus)  tintmodus. Tijdens het bewerken is alleen deze tintmodus beschikbaar in het visualisatie-opties menu; tijdens het spelen zijn alle tintmodi beschikbaar. Zie [Enum.SlimTranscoderStatus](/docs/nl-nl/reference/engine/enums/SlimTranscoderStatus)  voor de kleurtoewijzingen van elke status.

## [Probleemoplossing](#probleemoplossing)[](#probleemoplossing)

SLIM model verschijnt niet

-

Controleer of [StreamingEnabled](/docs/nl-nl/reference/engine/classes/Workspace#StreamingEnabled)  true  is.

-

Bevestig dat de plaats is gepubliceerd naar Roblox en dat [Team Create](/docs/nl-nl/projects/collaboration)  is ingeschakeld.

-

Controleer of [LevelOfDetail](/docs/nl-nl/reference/engine/classes/Model#LevelOfDetail)  is ingesteld op [SLIM](/docs/nl-nl/reference/engine/enums/ModelLevelOfDetail#SLIM)  voor het model.

-

Wacht 1–2 minuten na de eerste publicatie voor cloud transcoding om te voltooien, sluit dan opnieuw aan.

-

Zorg ervoor dat het model geen [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  instantie bevat.

Solide modellering operaties renderen niet correct in SLIM

[PartOperation](/docs/nl-nl/reference/engine/classes/PartOperation)  instanties voor [solide modellering](/docs/nl-nl/parts/solid-modeling)  (unies, intersecties, negaties) renderen mogelijk niet correct in sommige SLIM-modellen. Als een unie ontbreekt of vervormd lijkt in de SLIM-representatie, probeer dan de aangetaste [PartOperation](/docs/nl-nl/reference/engine/classes/PartOperation)  in zijn eigen model te scheiden of de CSG-operatie te vereenvoudigen.

Z-fighting of flikkeren op SLIM-modellen

Z-fighting kan optreden wanneer onderdelen in het originele model overlappende of coplanare vlakken hebben. Om dit op te lossen:

-

Verplaats overlappende onderdelen iets uit elkaar (zelfs 0.01  studs is voldoende).

-

Vermijd perfect vlakke oppervlakken tussen aangrenzende onderdelen in hetzelfde model.

Textuur of UV verschuivingen op SLIM-modellen

SLIM genereert UV-mapping opnieuw (hoe texturen op 3D-oppervlakken worden geprojecteerd) tijdens transcoding. Standaard Roblox-materialen kunnen iets andere tegelpatronen vertonen in vergelijking met het origineel. Om dit te verminderen:

-

Gebruik aangepaste texturen via [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  voor belangrijke oppervlakken.

-

Groepeer visueel gerelateerde onderdelen in hetzelfde model om consistente texturering te waarborgen.

SLIM avatars renderen niet

-

Controleer of [Workspace.EnableSLIMAvatars](/docs/nl-nl/reference/engine/classes/Workspace#EnableSLIMAvatars)  is ingesteld op [Enabled](/docs/nl-nl/reference/engine/enums/RolloutState#Enabled) .

-

Test met meerdere clients met behulp van [Server en Clients](/docs/nl-nl/studio/testing-modes#multi-client-simulatie)  testmodus (vereist minimaal 2 clients).

-

Zorg ervoor dat de avatar een [standaard](/docs/nl-nl/avatar/character-bodies/specifications#standaard-r15-rigs)  of [geavanceerd](/docs/nl-nl/avatar/character-bodies/specifications#geavanceerde-r15-rigs)  R15 rig gebruikt zonder aangepaste verhoudingen.

-

Bevestig dat de game de avatar niet wijzigt na de [Player.CharacterAppearanceLoaded](/docs/nl-nl/reference/engine/classes/Player#CharacterAppearanceLoaded)  gebeurtenis.

Visuele glitches op geanimeerde SLIM avatars

Volledige lichaams- of vingeranimaties kunnen af en toe visuele artefacten vertonen als gevolg van timing van botreplicatie. Dit is een bekend probleem dat actief wordt verbeterd. Als het probleem ernstig is, controleer dan of animatiescripts de bottransformaties niet buiten de standaard animatiepijplijn wijzigen.

Onnauwkeurige driehoektelling in renderstatistieken

Het renderstatistiekenpaneel kan onjuiste driehoekentellingen rapporteren wanneer SLIM avatars zijn ingeschakeld. Dit is een bekende rapportagebug en heeft geen invloed op de werkelijke renderprestaties.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
