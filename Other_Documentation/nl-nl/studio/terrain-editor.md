<!-- Source: https://create.roblox.com/docs/nl-nl/studio/terrain-editor -->

Terrainer | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Studio](/docs/nl-nl/studio)

# Terrainer

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De Terrainer , toegankelijk vanuit het Home -tabblad van Studio of het Window  ⟩ 3D -menu, stelt je in staat om [milieu-terrein](/docs/nl-nl/parts/terrain)  te genereren en te manipuleren via de [Create](#create-tab)  en [Edit](#edit-tab)  toolsets.

 ![Terrainer aangegeven in de werkbalk van Studio](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Terrain-Editor.png)

Voor gedetailleerde instructies over het werken met terrein, zie de [milieu-terrein](/docs/nl-nl/parts/terrain)  gids. Om tot 62 aangepaste materialen op terrein te schilderen, zie [Aangepaste terreinmaterialen](/docs/nl-nl/parts/custom-terrain-materials) .

## [Create-tab](#create-tab)[](#create-tab)

De Create -tab bevat de [Import](#import) , [Generate](#generate)  en [Clear](#clear)  tools.

### [Import](#import)[](#import)

De Import -tool importeert een [hoogtekaart](/docs/nl-nl/parts/terrain#hoogtekaarten-en-kleurkaarten)  en optionele [kleurkaart](/docs/nl-nl/parts/terrain#hoogtekaarten-en-kleurkaarten)  en past deze toe op een geselecteerd gebied.

 ![Import-tool aangegeven in de Create-tab van de Terrainer](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Create-Tab-Import.png)

![Voorbeeld hoogtekaart afbeelding](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Terrain-Heightmap.png) Hoogtekaart

![Voorbeeld kleurkaart afbeelding](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Terrain-Colormap.png) Kleurkaart

![Terrein gegenereerd uit de voorbeeld hoogtekaart en kleurkaart](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Terrain-Colormap-Result.jpg) Gegenereerd terrein

| Selectie-instellingen |
| --- | --- |
| Grootte, positie en snap-instellingen zoals beschreven voor de [Select](#select)  tool. |
| Hoogtekaart-instellingen |
| Hoogtekaart | | Importeert een hoogtekaart van een lokaal afbeeldingsbestand. |
| Kleurkaart | | Importeert een kleurkaart van een lokaal afbeeldingsbestand om samen met een hoogtekaart te gebruiken. |
| Standaardmateriaal | | Geeft één consistent materiaal op dat op het gehele gegenereerde terrein wordt toegepast. Dit wordt overschreven door materialen op basis van de kleurkaart, indien geïmporteerd. |

### [Generate](#generate)[](#generate)

De Generate -tool genereert proceduraal terrein binnen een geselecteerd gebied. Dit is nuttig als je een grote kaart wilt maken en vervolgens de terrein details wilt verfijnen met behulp van de tools in het [Edit](#edit-tab)  tabblad.

 ![Generate-tool aangegeven in de Create-tab van de Terrainer](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Create-Tab-Generate.png)

| Selectie-instellingen |
| Grootte, positie en snap-instellingen zoals beschreven voor de [Select](#select)  tool. |
| Biome-instellingen |
| Biomen | | Bevat de geselecteerde biomen in het gegenereerde terrein. |
| Blending | | Past aan hoe de biomen in elkaar overlopen, met hogere waarden die iets soepeler zijn. |
| Grotten | | Bevat grotten in het gegenereerde terrein. |
| Biomegrootte | | Stelt de grootte van de biomen binnen de totale terrein grootte in. |
| Seed | | Een nummer dat Studio genereert om de vorm van het terrein te bepalen. Wanneer je dit nummer verandert, genereert Studio een nieuw terrein met dezelfde instellingen. |

### [Clear](#clear)[](#clear)

De Clear -tool onthult een knop die al het terrein binnen de gehele plaats wist.

 ![Clear-tool aangegeven in de Create-tab van de Terrainer](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Create-Tab-Clear.png)

## [Edit-tab](#edit-tab)[](#edit-tab)

De Edit -tab bevat de [Select](#select) , [Transform](#transform) , [Fill](#fill) , [Sea Level](#sea-level) , [Draw](#draw) , [Sculpt](#sculpt) , [Smooth](#smooth) , [Paint](#paint)  en [Flatten](#flatten)  tools.

### [Select](#select)[](#select)

De Select -tool is een universele tool voor het selecteren van rechthoekige gebieden van terrein. Met de tool ingeschakeld, selecteer je een gebied door te klikken en te slepen in de 3D-weergave, verplaats je het met de move -draggers en bewerk je de grootte met de scale -handgrepen. Alternatief kun je waarden invoeren in de X / Y / Z -invoeren van de tool om een specifieke positie en grootte in te stellen.

 ![Select-tool aangegeven in de Edit-tab van de Terrainer](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Edit-Tab-Select.png)

| Selectie-instellingen |
| Grootte | | Stelt specifieke X / Y / Z  waarden in voor de grootte van de selectie, in studs. |
| Positie | | Stelt specifieke X / Y / Z  waarden in voor de positie van de selectie. |
| Snap naar Voxels | | Snapt de selectiegrenzen naar de dichtstbijzijnde voxel. |

![Verplaatsdraggers en schaalhandgrepen op een geselecteerd gebied](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Select-Region-Labeled.jpg) Verplaatsdraggers en schaalhandgrepen op een geselecteerd gebied

Studio ondersteunt ook de volgende toetsenbord- en muiskortcuts, ervan uitgaande dat de Select -tool actief is en er niets is geselecteerd in de [Explorer](/docs/nl-nl/studio/explorer)  hiërarchie.

| Windows | | Mac | | Actie |
| Ctrl C | | ⌘ C | | Kopieert terrein binnen het geselecteerde gebied naar het klembord. |
| Ctrl V | | ⌘ V | | Plakt terrein dat naar het klembord is gekopieerd en wisselt naar de [Transform](#transform)  tool zodat het nieuwe terrein kan worden getransformeerd. |
| Ctrl X | | ⌘ X | | Knipt terrein binnen het geselecteerde gebied naar het klembord. |
| Ctrl D | | ⌘ D | | Dupliceert terrein binnen het geselecteerde gebied en wisselt naar de [Transform](#transform)  tool zodat het nieuwe terrein kan worden getransformeerd. |
| Delete | | Delete | | Verwijdert terrein binnen het geselecteerde gebied. |
| Shift | | Shift | | Wanneer ingedrukt tijdens het slepen van een scale -handgreep, schaalt het gebied proportioneel over alle andere assen. |
| Ctrl | | ⌘ | | Wanneer ingedrukt tijdens het slepen van een scale -handgreep, schaalt het gebied gelijkmatig in zowel de positieve als negatieve richting langs die as. |

### [Transform](#transform)[](#transform)

De Transform -tool manipuleert gehele [geselecteerde](#select)  gebieden naar een nieuwe positie, grootte of oriëntatie. Met de tool ingeschakeld, transformeer je een geselecteerd gebied met de move -draggers, rotate -ringen en scale -handgrepen. Alternatief kun je waarden invoeren in de X / Y / Z -invoeren van de tool om een specifieke positie, grootte en rotatie in te stellen.

 ![Transform-tool aangegeven in de Edit-tab van de Terrainer](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Edit-Tab-Transform.png)

| Transform-instellingen |
| Grootte | | Stelt specifieke X / Y / Z  waarden in voor de grootte van de selectie in studs. |
| Positie | | Stelt specifieke X / Y / Z  waarden in voor de positie van de selectie. |
| Rotatie | | Stelt specifieke X / Y / Z  waarden in voor de rotatie van de selectie in graden. |
| Leeg samenvoegen | | Wanneer ingeschakeld, zullen luchtvoxels in de selectie bestaande voxels op de bestemming overschrijven. |
| Live Edit | | Wanneer ingeschakeld, wordt het terrein constant bijgewerkt terwijl het wordt getransformeerd. Om alleen een wireframevoorbeeld van de transformatie te bekijken, schakel je de live bewerkingsmodus uit en druk je tijdens het transformeren op Enter / Return  of klik je op de Toepassen -knop om de wijzigingen toe te passen. |
| Snap naar Voxels | | Snapt de selectiegrenzen naar de dichtstbijzijnde voxel. |

![Verplaatsdraggers, roteerringen en schaalhandgrepen op een geselecteerd gebied](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Transform-Region-Labeled.jpg) Verplaatsdraggers, roteerringen en schaalhandgrepen op een geselecteerd gebied

Controleer voordat je een gebied roteert met de visuele rotate -ringen de rotatie-snap-instelling in de werkbalk van Studio. Schakel de rotatie-snap volledig uit voor vrije rotatie.

Net als bij het [selecteren](#select)  van een gebied, schaalt het vasthouden van Shift  terwijl je een scale -handgreep sleept het gebied proportioneel over alle andere assen, en het vasthouden van Ctrl  of ⌘  terwijl je sleept schaalt het gebied gelijkmatig in zowel de positieve als negatieve richting langs die as.

### [Fill](#fill)[](#fill)

De Fill -tool vult een geheel [geselecteerd](#select)  gebied met een specifiek materiaal, of vervangt al het materiaal binnen het gebied door een ander materiaal.

 ![Fill-tool aangegeven in de Edit-tab van de Terrainer](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Edit-Tab-Fill.png)

| Selectie-instellingen |
| Grootte, positie en snap-instellingen zoals beschreven voor de [Select](#select)  tool. |
| Materiaal-instellingen |
| Vulmodus | | Schakelt de tool tussen Vullen  en Vervangen  modus. |
| Bronmateriaal | | In Vullen  modus, het gewenste vulmateriaal. In Vervangen  modus, het materiaal om te vervangen. |
| Doelmateriaal | | In Vervangen  modus, het materiaal om het bronmateriaal mee te vervangen. |

![Gebied gevuld met zoutmateriaal](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Fill-Region.jpg) Geselecteerd gebied gevuld met zoutmateriaal

### [Sea Level](#sea-level)[](#sea-level)

De Sea Level -tool stelt je in staat om een consistent waterniveau te creëren of al het water binnen een gebied te verwijderen.

 ![Sea Level-tool aangegeven in de Edit-tab van de Terrainer](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Edit-Tab-Sea-Level.png)

| Zee-niveau-instellingen |
| Grootte | | Stelt specifieke X / Y / Z  waarden in voor de grootte van de selectie in studs. |
| Positie | | Stelt specifieke X / Y / Z  waarden in voor de positie van de selectie. |
| Snap naar Voxels | | Snapt de selectiegrenzen naar de dichtstbijzijnde voxel. |

### [Draw](#draw)[](#draw)

De Draw -tool voegt  of trekt  terrein af met behulp van de borstel. Deze tool functioneert in een duale modus waarbij het ingedrukt houden van Ctrl  of ⌘  de "aftrek"-modus in plaats van de standaard "voeg toe"-modus inschakelt. Bovendien activeert het ingedrukt houden van Shift  tijdelijk de [Smooth](#smooth)  tool.

 ![Draw-tool aangegeven in de Edit-tab van de Terrainer](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Edit-Tab-Draw.png)

| Borstel-instellingen |
| Borstelmodus | | Schakelt de tool tussen Toevoegen  en Aftrekken  modus. Ook ingeschakeld door Ctrl  of ⌘  ingedrukt te houden. |
| Borstelvorm | | Stelt de borstelvorm in op een bol , doos  of cilinder .
![Borstelvorm iconen in de Terrainer](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Brush-Shape-Icons.png) |
| Borstelgrootte | | Stelt de borstelgrootte in van 1 tot 64. Als je een borstelvorm van doos  of cilinder  kiest, verschijnt er ook een Hoogte -slider/invoer om de borstelhoogte proportioneel of onafhankelijk van de basisgrootte aan te passen. |
| Pivot-positie | | Stelt het verticale draaipunt van de borstel in op de onderkant, het midden of de bovenkant van waar de borstel verbinding maakt met bestaand terrein. |
| Snapping | | Of snapping uit is of naar de dichtstbijzijnde voxel. |
| Vlakvergrendeling | | Schakelt in of uit of een visueel vlak moet worden ingeschakeld waar de borstel aan vergrendelt. In Auto -modus kantelt en roteert het vlak met de camera. In Handmatig -modus verschijnt de optie Bewerk Vlak , waarmee je een specifieke positie/orientatie kunt instellen via de visuele draggers of X / Y / Z -invoeren. |
| Negeer Water | | Negeert water bij het toevoegen of aftrekken van terrein. |
| Negeer Onderdelen | | Negeert [onderdelen](/docs/nl-nl/parts)  met betrekking tot borstelplaatsing terwijl de muisaanwijzer over de oppervlakken van onderdelen beweegt. |
| Materiaal-instellingen |
| Auto Materiaal | | Gebruikt hetzelfde terreinmateriaal in de nabijheid van de borstel bij het toevoegen van nieuw terrein. |
| Bronmateriaal | | Stelt het [materiaal](/docs/nl-nl/parts/terrain#terreinmaterialen)  in voor Toevoegen  modus. |

### [Sculpt](#sculpt)[](#sculpt)

De Sculpt -tool voegt  of trekt  terrein af met behulp van de borstel. In tegenstelling tot de [Draw](#draw)  tool, bevat deze tool een sterkte -slider/invoer om een zachtere manipulatie van het terrein mogelijk te maken. Deze tool functioneert in een duale modus waarbij het ingedrukt houden van Ctrl  of ⌘  de "aftrek"-modus inschakelt in plaats van de standaard "voeg toe"-modus, en het ingedrukt houden van Shift  tijdelijk de [Smooth](#smooth)  tool activeert.

 ![Sculpt-tool aangegeven in de Edit-tab van de Terrainer](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Edit-Tab-Sculpt.png)

| Optie | | Beschrijving |
| Borstelmodus | | Schakelt de tool tussen Toevoegen  en Aftrekken  modus. Ook ingeschakeld door Ctrl  of ⌘  ingedrukt te houden. |
| Borstelvorm | | Stelt de borstelvorm in op een bol , doos  of cilinder .
![Borstelvorm iconen in de Terrainer](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Brush-Shape-Icons.png) |
| Borstelgrootte | | Stelt de borstelgrootte in van 1 tot 64. Als je een borstelvorm van doos  of cilinder  kiest, verschijnt er ook een Hoogte -slider/invoer om de borstelhoogte proportioneel of onafhankelijk van de basisgrootte aan te passen. |
| Sterkte | | Stelt de borstelsterkte in van 0.1 tot 1. |
| Vlakvergrendeling | | Schakelt in of uit of een visueel vlak moet worden ingeschakeld waar de borstel aan vergrendelt. In Auto -modus kantelt en roteert het vlak met de camera. In Handmatig -modus verschijnt de optie Bewerk Vlak , waarmee je een specifieke positie/orientatie kunt instellen via de visuele draggers of X / Y / Z -invoeren. |
| Negeer Water | | Negeert water bij het toevoegen of aftrekken van terrein. |
| Negeer Onderdelen | | Negeert [onderdelen](/docs/nl-nl/parts)  met betrekking tot borstelplaatsing terwijl de muisaanwijzer over de oppervlakken van onderdelen beweegt. |
| Auto Materiaal | | Gebruikt hetzelfde terreinmateriaal in de nabijheid van de borstel bij het toevoegen van nieuw terrein. |
| Bronmateriaal | | Stelt het [materiaal](/docs/nl-nl/parts/terrain#terreinmaterialen)  in voor Toevoegen  modus. |

### [Smooth](#smooth)[](#smooth)

De Smooth -tool maakt abrupte randen in terrein glad met behulp van de borstel. Deze tool kan worden gebruikt in standalone modus, of je kunt deze inschakelen door Shift  ingedrukt te houden terwijl je de [Draw](#draw)  of [Sculpt](#sculpt)  tools gebruikt.

 ![Smooth-tool aangegeven in de Edit-tab van de Terrainer](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Edit-Tab-Smooth.png)

| Optie | | Beschrijving |
| Borstelvorm | | Stelt de borstelvorm in op een bol , doos  of cilinder .
![Borstelvorm iconen in de Terrainer](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Brush-Shape-Icons.png) |
| Borstelgrootte | | Stelt de borstelgrootte in van 1 tot 64. Als je een borstelvorm van doos  of cilinder  kiest, verschijnt er ook een Hoogte -slider/invoer om de borstelhoogte proportioneel of onafhankelijk van de basisgrootte aan te passen. |
| Sterkte | | Stelt de borstelsterkte in van 0.1 tot 1. |
| Pivot-positie | | Stelt het verticale draaipunt van de borstel in op de onderkant, het midden of de bovenkant van waar de borstel verbinding maakt met bestaand terrein. |
| Snapping | | Of snapping uit is of naar de dichtstbijzijnde voxel. |
| Vlakvergrendeling | | Schakelt in of uit of een visueel vlak moet worden ingeschakeld waar de borstel aan vergrendelt. In Auto -modus kantelt en roteert het vlak met de camera. In Handmatig -modus verschijnt de optie Bewerk Vlak , waarmee je een specifieke positie/orientatie kunt instellen via de visuele draggers of X / Y / Z -invoeren. |
| Negeer Water | | Negeert water bij het gladmaken van terrein. |
| Negeer Onderdelen | | Negeert [onderdelen](/docs/nl-nl/parts)  met betrekking tot borstelplaatsing terwijl de muisaanwijzer over de oppervlakken van onderdelen beweegt. |

### [Paint](#paint)[](#paint)

De Paint -tool, met behulp van de borstel, schildert  een terrein [materiaal](/docs/nl-nl/parts/terrain#terreinmaterialen)  over een bestaand materiaal of vervangt  het ene materiaal door een ander materiaal.

 ![Paint-tool aangegeven in de Edit-tab van de Terrainer](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Edit-Tab-Paint.png)

| Optie | | Beschrijving |
| Borstelvorm | | Stelt de borstelvorm in op een bol , doos  of cilinder .
![Borstelvorm iconen in de Terrainer](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Brush-Shape-Icons.png) |
| Borstelgrootte | | Stelt de borstelgrootte in van 1 tot 64. Als je een borstelvorm van doos  of cilinder  kiest, verschijnt er ook een Hoogte -slider/invoer om de borstelhoogte proportioneel of onafhankelijk van de basisgrootte aan te passen. |
| Pivot-positie | | Stelt het verticale draaipunt van de borstel in op de onderkant, het midden of de bovenkant van waar de borstel verbinding maakt met bestaand terrein. |
| Snapping | | Of snapping uit is of naar de dichtstbijzijnde voxel. |
| Vlakvergrendeling | | Schakelt in of uit of een visueel vlak moet worden ingeschakeld waar de borstel aan vergrendelt. In Auto -modus kantelt en roteert het vlak met de camera. In Handmatig -modus verschijnt de optie Bewerk Vlak , waarmee je een specifieke positie/orientatie kunt instellen via de visuele draggers of X / Y / Z -invoeren. |
| Negeer Water | | Negeert water bij het afvlakken van terrein. |
| Negeer Onderdelen | | Negeert [onderdelen](/docs/nl-nl/parts)  met betrekking tot borstelplaatsing terwijl de muisaanwijzer over de oppervlakken van onderdelen beweegt. |
| Materiaalmodus | | Schakelt de tool tussen Schilderen  en Vervangen  modus. In Schilderen  modus, kies het gewenste schildermateriaal uit de selectietegels van de tool. In Vervangen  modus, kies zowel het bron materiaal om te vervangen als het doel materiaal waarmee het vervangen moet worden. |

### [Flatten](#flatten)[](#flatten)

De Flatten -tool maakt terrein vlak naar een consistent niveau over een gevisualiseerd vlak. Standaard verlaagt de tool terrein boven het vlak en  verhoogt terrein onder het vlak naar het vlak, maar je kunt ervoor kiezen om selectief te verlagen of  te verhogen via de Flatten Mode -optie van de tool.

 ![Flatten-tool aangegeven in de Edit-tab van de Terrainer](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Edit-Tab-Flatten.png)

| Optie | | Beschrijving |
| Borstelvorm | | Stelt de borstelvorm in op een bol , doos  of cilinder .
![Borstelvorm iconen in de Terrainer](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Brush-Shape-Icons.png) |
| Flatten Mode | | Erode naar Vlak ¹ maakt terrein boven het vlak vlak. Groeien naar Vlak ² vult terrein onder het vlak in. Flatten All ³ verwijdert terrein boven het vlak en vult terrein onder het vlak in.
![Flatten Mode iconen in de Terrainer](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Flatten-Mode-Icons.png) |
| Borstelgrootte | | Stelt de borstelgrootte in van 1 tot 64. Als je een borstelvorm van doos  of cilinder  kiest, verschijnt er ook een Hoogte -slider/invoer om de borstelhoogte proportioneel of onafhankelijk van de basisgrootte aan te passen. |
| Sterkte | | Stelt de borstelsterkte in van 0.1 tot 1. |
| Pivot-positie | | Stelt het verticale draaipunt van de borstel in op de onderkant, het midden of de bovenkant van waar de borstel verbinding maakt met bestaand terrein. |
| Snapping | | Of snapping uit is of naar de dichtstbijzijnde voxel. |
| Flatten Vlak | | Als ingesteld op Vast , maakt het terrein vlak naar een vast visueel vlak in Y  wereldruimte. |
| Negeer Water | | Negeert water bij het afvlakken van terrein. |
| Negeer Onderdelen | | Negeert [onderdelen](/docs/nl-nl/parts)  met betrekking tot borstelplaatsing terwijl de muisaanwijzer over de oppervlakken van onderdelen beweegt. |

## [Studio-sneltoetsen](#studio-sneltoetsen)[](#studio-sneltoetsen)

Voor tools die de borstel  gebruiken ([Draw](#draw) , [Sculpt](#sculpt) , [Smooth](#smooth) , [Flatten](#flatten) , [Paint](#paint) ), ondersteunt Studio de volgende toetsenbord- en muiskortcuts.

| Windows | | Mac | | Actie |
| Ctrl | | ⌘ | | Wanneer ingedrukt tijdens het gebruik van de [Draw](#draw)  en [Sculpt](#sculpt)  tools, schakelt de alternatieve borstelmodus in. Bijvoorbeeld, schakelt de "aftrek"-modus in plaats van de standaard "voeg toe"-modus. |
| Shift | | Shift | | Wanneer ingedrukt tijdens het gebruik van de [Draw](#draw)  en [Sculpt](#sculpt)  tools, activeert tijdelijk de [Smooth](#smooth)  tool. |
| B | | B | | Wanneer ingedrukt tijdens het slepen van de muis of het gebruik van het scrollwiel, past de basisgrootte van de borstel aan. |
| Ctrl B | | ⌘ B | | Wanneer ingedrukt tijdens het slepen van de muis of het gebruik van het scrollwiel, past de hoogte van de borstel aan. Geldt alleen als de vorm van de borstel is ingesteld op doos  of cilinder . |
| Shift B | | Shift B | | Wanneer ingedrukt tijdens het slepen van de muis of het gebruik van het scrollwiel, past de sterkte van de borstel aan. Geldt alleen bij het gebruik van de [Sculpt](#sculpt) , [Smooth](#smooth)  of [Flatten](#flatten)  tool. |
| Alt | | ⌥ | | Wanneer ingedrukt tijdens het klikken met de muis, toont de materiaalkeuzer. |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
