<!-- Source: https://create.roblox.com/docs/nl-nl/parts/terrain -->

Milieu terrein | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)

# Milieu terrein

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Studio's [Terrein Editor](/docs/nl-nl/studio/terrain-editor)  stelt je in staat om gedetailleerde en realistische terreinomgevingen te genereren en te sculpten, zoals bergen, waterlichamen, met gras bedekte heuvels of een vlakke woestijn. Terrein bestaat uit grids van voxels  die 4×4×4 stud regio's in de 3D-wereld zijn met een bepaald materiaal.

 ![Terrein Editor aangegeven in de werkbalk van Studio](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Terrain-Editor.png)  ![Woestijn terrein met bergen in de verte](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Showcase.jpg)

Met de editor tools kun je eenvoudig [genereren](#genereer-terrein)  en terrein bewerken, hetzij op een [voxel](#gedetailleerde-bewerking)  of [regio](#grootschalige-bewerking)  niveau, met de optie om een [hoogtekaart](#hoogtekaarten-en-kleurkaarten)  en [kleurkaart](#hoogtekaarten-en-kleurkaarten)  te importeren. Voor meer precieze, dynamische of procedurele terreinbewerking kun je ook [script](#scripting)  gebruiken voor terreincreatie.

## [Terreinmaterialen](#terreinmaterialen)[](#terreinmaterialen)

De volgende standaardmaterialen zijn beschikbaar voor terrein. Je kunt ook [aangepaste terreinmaterialen](/docs/nl-nl/parts/custom-terrain-materials)  schilderen nadat je Uitgebreid Terrein  hebt ingeschakeld, of [aangepaste materialen](/docs/nl-nl/parts/materials#aangepaste-materialen)  als overrides toepassen. Materialen beïnvloeden zowel de vorm als het uiterlijk van terrein in de wereld; bijvoorbeeld, [geanimeerd gras](#grasanimatie)  wordt alleen weergegeven op het [Grass](/docs/nl-nl/reference/engine/enums/Material#Grass)  materiaal en het [Water](/docs/nl-nl/reference/engine/enums/Material#Water)  materiaal [golft en glinstert](#uiterlijk-van-water)  met een subtiele beweging.

![Uiterlijk van asfaltmateriaal](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Asphalt.jpg) Asfalt

![Uiterlijk van basaltmateriaal](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Basalt.jpg) Basalt

![Uiterlijk van baksteenmateriaal](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Brick.jpg) Baksteen

![Uiterlijk van kindermateriaal](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Cobblestone.jpg) Kindermateriaal

![Uiterlijk van betonmateriaal](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Concrete.jpg) Beton

![Uiterlijk van gebroken lavamateriaal](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Cracked-Lava.jpg) Gebroken Lava

![Uiterlijk van gletsjermateriaal](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Glacier.jpg) Gletsjer

![Uiterlijk van grasmateriaal](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Grass.jpg) Gras

![Uiterlijk van grondmateriaal](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Ground.jpg) Grond

![Uiterlijk van ijsmateriaal](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Ice.jpg) IJs

![Uiterlijk van bladachtig grasmateriaal](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Leafy-Grass.jpg) Bladachtig Gras

![Uiterlijk van kalksteenmateriaal](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Limestone.jpg) Kalksteen

![Uiterlijk van moddermateriaal](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Mud.jpg) Modder

![Uiterlijk van verhardingsmateriaal](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Pavement.jpg) Verharding

![Uiterlijk van steenmateriaal](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Rock.jpg) Steen

![Uiterlijk van zoutmateriaal](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Salt.jpg) Zout

![Uiterlijk van zandmateriaal](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Sand.jpg) Zand

![Uiterlijk van zandsteenmateriaal](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Sandstone.jpg) Zandsteen

![Uiterlijk van leisteenmateriaal](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Slate.jpg) Leisteen

![Uiterlijk van sneeuwmateriaal](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Snow.jpg) Sneeuw

![Uiterlijk van watermateriaal](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Water.jpg) Water

![Uiterlijk van houtplankmateriaal](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Wood-Planks.jpg) Houtplanken

![Luchtmateriaal pictogram (geen visueel uiterlijk)](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Material-Air.png) Lucht

### [Uiterlijk van water](#uiterlijk-van-water)[](#uiterlijk-van-water)

Standaard golft, oscilleert en glinstert het water in het terrein met een subtiele beweging.

Om de kleur en beweging van water aan te passen:

1.

In het Explorer  venster, navigeer naar het [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) , selecteer vervolgens het [Terrain](/docs/nl-nl/reference/engine/classes/Terrain)  object.

 ![Terreinobject weergegeven in het Explorer-venster van Studio](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Workspace-Terrain.png)

2.

In het Eigenschappen  venster, pas het uiterlijk van water aan via de volgende eigenschappen:

| Eigenschap | | Beschrijving |
| --- | --- |
| [WaterColor](/docs/nl-nl/reference/engine/classes/Terrain#WaterColor) | | Past de algehele tint van al het water in het terrein aan. |
| [WaterReflectance](/docs/nl-nl/reference/engine/classes/Terrain#WaterReflectance) | | Past aan hoeveel wateroppervlakken de lucht en omliggende objecten reflecteren van een waarde van 1 (hoog) tot 0 (geen). |
| [WaterTransparency](/docs/nl-nl/reference/engine/classes/Terrain#WaterTransparency) | | Past aan hoe transparant water is van een waarde van 1 (helder) tot 0 (opake). |
| [WaterWaveSize](/docs/nl-nl/reference/engine/classes/Terrain#WaterWaveSize) | | Past de grootte van golven aan van een waarde van 1 (groot) tot 0 (geen). |
| [WaterWaveSpeed](/docs/nl-nl/reference/engine/classes/Terrain#WaterWaveSpeed) | | Past de snelheid van golven aan van een waarde van 100 (turbulent) tot 0 (stil). |

Sommige water eigenschappen zijn alleen zichtbaar tijdens het playtesten. Om alle eigenschappen tijdens het bewerken te bekijken, open [Studio-instellingen](/docs/nl-nl/studio/setup#aanpassing) , zoek naar Editor Quality Level , en stel deze in op het hoogste niveau.

### [Grasanimatie](#grasanimatie)[](#grasanimatie)

Hoewel de meeste materialen statisch zijn, kun je geanimeerde grasplanten toevoegen aan het [Grass](/docs/nl-nl/reference/engine/enums/Material#Grass)  terreinmateriaal. Standaard wiegt gras zachtjes in een gesimuleerde wind, en je kunt de richting/sterkte van de animatie aanpassen via [globale wind](/docs/nl-nl/environment/global-wind) .

Let op dat de snelheid van geanimeerd gras — maar niet de vectorrichting — zal worden verminderd als de speler de Verminder Beweging  [toegankelijkheid](/docs/nl-nl/production/publishing/accessibility#verminderde-beweging)  instelling heeft ingeschakeld vanuit het Roblox of in-game Instellingen  menu.

Om geanimeerd gras toe te voegen aan het [Grass](/docs/nl-nl/reference/engine/enums/Material#Grass)  materiaal:

1.

In het Explorer  venster, navigeer naar het [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) , selecteer vervolgens het [Terrain](/docs/nl-nl/reference/engine/classes/Terrain)  object.

 ![Terreinobject weergegeven in het Explorer-venster van Studio](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Workspace-Terrain.png)

2.

In het Eigenschappen  venster, schakel de [Decoration](/docs/nl-nl/reference/engine/classes/Terrain#Decoration)  eigenschap in.

 ![Decoratie-eigenschap van het terreinobject in het eigenschappenvenster van Studio](https://prod.docsiteassets.roblox.com/assets/studio/properties/Terrain-Decoration.png)

3.

Pas de graslengte aan door een waarde tussen 0.1  en 1  in te voeren voor de [GrassLength](/docs/nl-nl/reference/engine/classes/Terrain#GrassLength)  eigenschap.

 ![GrassLength-eigenschap van het terreinobject in het eigenschappenvenster van Studio](https://prod.docsiteassets.roblox.com/assets/studio/properties/Terrain-GrassLength.png)  ![Vergelijking van GrassLength afgebeeld op glooiende graslandheuvels.](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Terrain-GrassLength.jpg)

4.

Pas de richting en sterkte van de animatie aan via [globale wind](/docs/nl-nl/environment/global-wind) .

### [Aangepaste terrein kleuren](#aangepaste-terrein-kleuren)[](#aangepaste-terrein-kleuren)

Elk terreinmateriaal heeft een standaardkleur, maar je kunt de kleur van elk materiaal aanpassen om beter bij je spel te passen.

Standaard Fantasy Tundra

![Standaard terrein kleuren gebruikt in woestijnlandschap](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Showcase.jpg)

Om de kleur van elk materiaal, behalve water, aan te passen:

1.

In het Explorer  venster, navigeer naar het [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) , selecteer vervolgens het [Terrain](/docs/nl-nl/reference/engine/classes/Terrain)  object.

 ![Terreinobject weergegeven in het Explorer-venster van Studio](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Workspace-Terrain.png)

2.

In het Eigenschappen  venster, vouw [MaterialColors](/docs/nl-nl/reference/engine/classes/Terrain#MaterialColors)  uit. Alle materialen worden weergegeven met hun RGB-code.

 ![MaterialColors-eigenschap weergegeven in het eigenschappenvenster van Studio](https://prod.docsiteassets.roblox.com/assets/studio/properties/Terrain-MaterialColors-Expand.png)

3.

Voor elk materiaal, voer een nieuwe RGB-code in of klik op het kleurvak om de [kleurenpopup](/docs/nl-nl/parts#kleur)  te openen.

## [Genereer terrein](#genereer-terrein)[](#genereer-terrein)

Met de volgende tools en methoden kun je grote gebieden van terrein procedureel genereren via tooling of scripting, of automatisch op basis van een hoogtekaart en kleurkaart.

### [Genereer tool](#genereer-tool)[](#genereer-tool)

De Genereer  tool stelt je in staat om terrein procedureel in enkele seconden te genereren. Dit is nuttig als je een grote kaart wilt maken en [terrein details](#gedetailleerde-bewerking)  wilt verfijnen.

1.

In het editorvenster, navigeer naar het Creëer  tabblad en selecteer de Genereer  tool.

 ![Genereer tool aangegeven in het Creëer tabblad van de Terrein Editor](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Create-Tab-Generate.png)

2.

In de 3D viewport, verplaats/verander de grootte van de selectieregio  waarin je terrein wilt genereren. Als alternatief, breid de Selectie-instellingen  van de tool uit en voer waarden in de X / Y / Z  invoervelden in om een specifieke grootte en positie in te stellen.

3.

In de Biome-instellingen  sectie van de tool, kies de volgende biomen om op te nemen in het nieuwe terrein:

-

Arctisch

-

Dunes

-

Canyons

-

Lavascape

-

Water

-

Bergen

-

Heuvels

-

Vlaktes

-

Moeras

4.

Klik op de Genereer  knop.

### [Hoogtekaarten en kleurkaarten](#hoogtekaarten-en-kleurkaarten)[](#hoogtekaarten-en-kleurkaarten)

Een hoogtekaart  is een 2D-representatie van een 3D-terreinkaart, zoals deze direct van bovenaf wordt bekeken. Heldere gebieden van een hoogtekaart resulteren in hoger terrein, zoals bergen, terwijl donkere gebieden resulteren in lagere regio's, zoals valleien.

Een optionele kleurkaart , samen met een hoogtekaart, converteert kleuren naar terreinmaterialen met behulp van een kleurensleutel .

![Voorbeeld hoogtekaart afbeelding](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Terrain-Heightmap.png) Hoogtekaart

![Voorbeeld kleurkaart afbeelding](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Terrain-Colormap.png) Kleurkaart

![Terrein gegenereerd uit de voorbeeld hoogtekaart en kleurkaart](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Terrain-Colormap-Result.jpg) Gegenereerd terrein

1 pixel in een hoogtekaart vertegenwoordigt 4 studs in Studio, en Studio ondersteunt een maximum van 4096×4096 pixels in zowel .jpg  als .png  formaat.

Om een hoogtekaart en optionele kleurkaart te importeren:

1.

In het editorvenster, navigeer naar het Creëer  tabblad en selecteer de Importeer  tool.

 ![Importeer tool aangegeven in het Creëer tabblad van de Terrein Editor](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Create-Tab-Import.png)

2.

In de Kaartinstellingen  sectie van de tool, klik op de importknop en kies de afbeelding die je wilt importeren als hoogtekaart.

3.

In de Materiaalinstellingen  sectie van de tool, selecteer een terreinmateriaal of, als alternatief, upload een kleurkaart.

Materiaal Kleurkaart

Om één consistent materiaal over het gehele gegenereerde terrein toe te passen, selecteer het Materiaal  tabblad en kies een terreinmateriaal.

4.

In de 3D viewport, verplaats/verander de grootte van de selectieregio  waarin je terrein wilt genereren. Als alternatief, voer waarden in de Selecteer  toolvelden in om een meer specifieke positie en grootte in te stellen.

Minimale en maximale terreinhoogtes zijn afhankelijk van de donkerste en lichtste gebieden van de hoogtekaart afbeelding in relatie tot de Y  grootte (hoogte) van de selectieregio. Bijvoorbeeld, als je een hoogte van 128 kiest, zijn pure zwarte gebieden 64 studs onder de middenpositie en pure witte gebieden zijn 64 studs boven de middenpositie.

5.

Klik op de Genereer  knop.

### [Scripting](#scripting)[](#scripting)

Je kunt terrein generatie scriptmatig uitvoeren met de [Terrain](/docs/nl-nl/reference/engine/classes/Terrain)  klasse. Bijvoorbeeld, om terrein te creëren met grasmateriaal dat een volume vult, kun je methoden gebruiken zoals [FillBall()](/docs/nl-nl/reference/engine/classes/Terrain#FillBall) , [FillBlock()](/docs/nl-nl/reference/engine/classes/Terrain#FillBlock) , [FillCylinder()](/docs/nl-nl/reference/engine/classes/Terrain#FillCylinder) , [FillRegion()](/docs/nl-nl/reference/engine/classes/Terrain#FillRegion) , of [FillWedge()](/docs/nl-nl/reference/engine/classes/Terrain#FillWedge) .

Vul Blok Volume

```

local Workspace = game:GetService("Workspace")

Workspace.Terrain:FillBlock(CFrame.new(0, 0, 0), Vector3.new(4, 4, 4), Enum.Material.Grass)

```

## [Grootschalige bewerking](#grootschalige-bewerking)[](#grootschalige-bewerking)

Het Bewerken  tabblad van de editor bevat tools voor grootschalige bewerking.

### [Selecteer regio's](#selecteer-regios)[](#selecteer-regios)

De Selecteer  tool is de universele tool voor het selecteren van rechthoekige regio's van terrein.

 ![Selecteer tool aangegeven in het Bewerken tabblad van de Terrein Editor](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Edit-Tab-Select.png)

Selecteer een regio door te klikken en te slepen in de 3D viewport, verplaats deze met de verplaats  draggers, en bewerk de grootte met de schaal  handgrepen. Als alternatief, voer waarden in de invoervelden van de tool in om een specifieke positie en grootte in te stellen.

![Verplaats draggers en schaal handgrepen op een geselecteerde regio](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Select-Region-Labeled.jpg) Verplaats draggers en schaal handgrepen op een geselecteerde regio

Studio ondersteunt ook de volgende toetsenbord- en muiskortcuts, ervan uitgaande dat de Selecteer tool actief is en er niets is geselecteerd in het Explorer  venster.

| Windows | | Mac | | Actie |
| Ctrl C | | ⌘ C | | Kopieer terrein binnen de geselecteerde regio naar het klembord. |
| Ctrl V | | ⌘ V | | Plak terrein dat naar het klembord is gekopieerd en wissel naar de Transform tool zodat het nieuwe terrein kan worden getransformeerd. |
| Ctrl X | | ⌘ X | | Snijd terrein binnen de geselecteerde regio naar het klembord. |
| Ctrl D | | ⌘ D | | Dupliceer terrein binnen de geselecteerde regio en wissel naar de Transform tool zodat het nieuwe terrein kan worden getransformeerd. |
| Delete | | Delete | | Verwijder terrein binnen de geselecteerde regio. |
| Shift | | Shift | | Wanneer ingedrukt tijdens het slepen van een schaal  handgreep, schaalt de regio proportioneel over alle andere assen. |
| Ctrl | | ⌘ | | Wanneer ingedrukt tijdens het slepen van een schaal  handgreep, schaalt de regio gelijkmatig in zowel de positieve als negatieve richting langs die as. |

### [Transformeer regio's](#transformeer-regios)[](#transformeer-regios)

De Transformeer  tool stelt je in staat om hele geselecteerde regio's naar een nieuwe positie, grootte of oriëntatie te manipuleren.

Om een regio te transformeren:

1.

Selecteer een regio en activeer vervolgens de Transformeer  tool. Let op dat de tool automatisch wordt geactiveerd als je terrein plakt of dupliceert.

 ![Transformeer tool aangegeven in het Bewerken tabblad van de Terrein Editor](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Edit-Tab-Transform.png)

2.

In de 3D viewport, transformeer de regio met de verplaats  draggers, rotate  ringen, en schaal  handgrepen. Als alternatief, voer waarden in de invoervelden van de tool in om een specifieke positie, grootte en rotatie in te stellen.

 ![Verplaats draggers, schaal handgrepen, en draai ringen op de Y-as van een geselecteerde regio](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Transform-Region-Labeled.jpg)

Houd Shift  ingedrukt terwijl je een schaal  handgreep sleept, schaalt de regio proportioneel over alle andere assen, en houd Ctrl  of ⌘  ingedrukt terwijl je sleept, schaalt de regio gelijkmatig in zowel de positieve als negatieve richting langs die as.

Houd Shift  ingedrukt terwijl je een rotate  ring sleept, schakelt tussen rotatiesnapping of vrije rotatie.

Standaard gebruikt deze tool de Live Edit  modus om het terrein constant bij te werken terwijl je het transformeert. Om alleen een wireframevoorbeeld van het terrein te bekijken terwijl je het transformeert, schakel de live edit modus uit en druk vervolgens, terwijl je transformeert, op Enter / Return  of klik op de Toepassen  knop om de wijzigingen toe te passen.

### [Vul en vervang regio's](#vul-en-vervang-regios)[](#vul-en-vervang-regios)

De Vul  tool stelt je in staat om een hele geselecteerde regio met een specifiek materiaal te vullen, of om al het materiaal binnen de regio door een ander materiaal te vervangen.

1.

Selecteer een regio, activeer vervolgens de Vul  tool.

 ![Vul tool aangegeven in het Bewerken tabblad van de Terrein Editor](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Edit-Tab-Fill.png)

2.

In de Materiaalinstellingen  sectie van de tool:

-

Om de regio met een specifiek materiaal te vullen, selecteer Vul  en kies het gewenste materiaal.

-

Om al het terrein van één materiaal door een ander materiaal te vervangen, selecteer Vervang , kies vervolgens een bron  materiaal en doel  materiaal.

3.

Klik op de Toepassen  knop of druk op Enter / Return .

![Regio gevuld met zoutmateriaal](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Fill-Region.jpg) Geselecteerde regio gevuld met zoutmateriaal

### [Stel zeespiegel in](#stel-zeespiegel-in)[](#stel-zeespiegel-in)

De Zeespiegel  tool stelt je in staat om een consistent waterniveau te creëren of al het water binnen een regio te verwijderen.

1.

Activeer de Zeespiegel  tool.

 ![Zeespiegel tool aangegeven in het Bewerken tabblad van de Terrein Editor](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Edit-Tab-Sea-Level.png)

2.

Selecteer de beoogde regio door te klikken en te slepen met de verplaats  draggers en schaal  handgrepen in de 3D viewport. Als alternatief, voer waarden in de invoervelden van de tool in om een specifieke positie en grootte in te stellen.

3.

Klik op de Verdampen  knop om water binnen de geselecteerde regio te verwijderen, of klik op de Creëren  knop om de geselecteerde regio met water te vullen.

## [Gedetailleerde bewerking](#gedetailleerde-bewerking)[](#gedetailleerde-bewerking)

Het Bewerken  tabblad bevat ook tools voor precisiebewerking met behulp van een "borstel" tool om terrein te tekenen, sculpten, glad te strijken, te egaliseren of te schilderen.

 ![Gedetailleerde bewerking tools aangegeven in het Bewerken tabblad van de Terrein Editor](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Edit-Tab-Detail-Tools.png)

Elke tool laat je kiezen uit een bol , doos , of cilinder  borstelvorm en een basisgrootte tussen 1–64 studs.

 ![Borstelvorm en grootte instellingen in de Terrein Editor](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Brush-Shape-Size.png)

Voor tools die de borstel gebruiken, ondersteunt Studio de volgende toetsenbord- en muiskortcuts.

| Windows | | Mac | | Actie |
| Ctrl | | ⌘ | | Wanneer ingedrukt tijdens het gebruik van de [Teken](/docs/nl-nl/studio/terrain-editor#draw)  en [Sculpt](/docs/nl-nl/studio/terrain-editor#sculpt)  tools, schakelt de alternatieve borstelmodus in. Bijvoorbeeld, schakelt "aftrekken" modus in in plaats van de standaard "toevoegen" modus. |
| Shift | | Shift | | Wanneer ingedrukt tijdens het gebruik van de [Teken](/docs/nl-nl/studio/terrain-editor#draw)  en [Sculpt](/docs/nl-nl/studio/terrain-editor#sculpt)  tools, activeert tijdelijk de [Glad](/docs/nl-nl/studio/terrain-editor#smooth)  tool. |
| B | | B | | Wanneer ingedrukt tijdens het slepen van de muis of het gebruik van het scrollwiel, past de basisgrootte van de borstel aan. |
| Ctrl B | | ⌘ B | | Wanneer ingedrukt tijdens het slepen van de muis of het gebruik van het scrollwiel, past de hoogte van de borstel aan. Geldt alleen als de borstelvorm is ingesteld op doos  of cilinder . |
| Shift B | | Shift B | | Wanneer ingedrukt tijdens het slepen van de muis of het gebruik van het scrollwiel, past de sterkte van de borstel aan. Geldt alleen bij het gebruik van de [Sculpt](/docs/nl-nl/studio/terrain-editor#sculpt) , [Glad](/docs/nl-nl/studio/terrain-editor#smooth) , of [Egaliseren](/docs/nl-nl/studio/terrain-editor#flatten)  tool. |
| Alt | | ⌥ | | Wanneer ingedrukt tijdens het klikken met de muis, toont de materiaalkiezer. |

### [Teken](#teken)[](#teken)

De Teken  tool voegt  of trekt  terrein af met behulp van de borstel. Deze tool functioneert in een duale modus waarbij het ingedrukt houden van Ctrl  of ⌘  de "aftrekken" modus inschakelt in plaats van de standaard "toevoegen" modus. Bovendien activeert het ingedrukt houden van Shift  tijdelijk de [Glad](/docs/nl-nl/studio/terrain-editor#smooth)  tool.

### [Sculpt](#sculpt)[](#sculpt)

De Sculpt  tool voegt  of trekt  terrein af met behulp van de borstel. In tegenstelling tot de Teken tool, bevat deze tool een sterkte  schuifregelaar om een meer zachte manipulatie van terrein mogelijk te maken.

Net als de Teken tool functioneert de Sculpt tool in een duale modus waarbij het ingedrukt houden van Ctrl  of ⌘  de "aftrekken" modus inschakelt in plaats van de standaard "toevoegen" modus. Bovendien activeert het ingedrukt houden van Shift  tijdelijk de Glad tool.

### [Glad](#glad)[](#glad)

De Glad  tool maakt abrupte randen in terrein glad met behulp van de borstel. Deze tool kan in standalone modus worden gebruikt, of je kunt deze inschakelen door Shift  ingedrukt te houden terwijl je de Teken of Sculpt tools gebruikt.

### [Egaliseren](#egaliseren)[](#egaliseren)

De Egaliseren  tool maakt terrein vlak tot een consistent niveau over een gevisualiseerde vlak. Standaard verlaagt de tool terrein boven het vlak en  verhoogt terrein onder het vlak naar het vlak, maar je kunt ervoor kiezen om selectief te verlagen of  te verhogen via de Egaliseren Modus  optie van de tool.

### [Schilderen](#schilderen)[](#schilderen)

De Schilderen  tool, met behulp van de borstel, schildert  een terreinmateriaal over een bestaand materiaal of vervangt  het ene materiaal door een ander materiaal.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
