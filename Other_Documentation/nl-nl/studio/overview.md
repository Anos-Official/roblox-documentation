<!-- Source: https://create.roblox.com/docs/nl-nl/studio/overview -->

Studio-interface | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Studio](/docs/nl-nl/studio)

# Studio-interface

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

## [Werkbalk en mezzanine](#werkbalk-en-mezzanine)[](#werkbalk-en-mezzanine)

De werkbalk  en mezzanine  bevinden zich bovenaan Studio.

![Mezzanine en werkbalk aangegeven in Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Mezzanine.png)

De linkerkant van de mezzanine bevat gemakkelijk toegankelijke [testbesturingselementen](/docs/nl-nl/studio/testing-modes#playtest-options) .

![Testbesturingselementen aangegeven in de mezzanine van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Controls.png)

De rechterkant van de mezzanine bevat knoppen/menu's voor [samenwerking](/docs/nl-nl/projects/collaboration) , delen, [Assistent](/docs/nl-nl/assistant/guide) , maker notificaties en accountopties.

![Andere opties aangegeven in de mezzanine van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Right.png)

In het midden van de mezzanine bevinden zich de standaard tooltabs van Home , Model , Avatar , UI , Script  en Plugins . Je kunt ook [aangepaste tabs](#aangepaste-tabs)  toevoegen voor jouw specifieke behoeften.

![Standaard tabs aangegeven in de mezzanine van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Default-Tabs.png)

Home Model Avatar UI Script Plugins

De Home  tab bevat de kern [transform](/docs/nl-nl/parts#onderdelen-transformeren)  tools, [onderdeel invoeger](/docs/nl-nl/parts#onderdelen-invoegen) , de [kleur](/docs/nl-nl/parts#kleur)  en [materiaal](/docs/nl-nl/parts#materiaal)  widgets, de [groep](/docs/nl-nl/parts#groeperen)  en [vergrendel](/docs/nl-nl/parts#vergrendelen)  tools, en de [anker](/docs/nl-nl/parts#verankeren)  schakelaar. Bevat ook de [Terrain Editor](/docs/nl-nl/studio/terrain-editor) .

### [Uiterlijk](#uiterlijk)[](#uiterlijk)

Je kunt het uiterlijk van de werkbalk aanpassen door met de rechtermuisknop op een leeg gebied binnen de mezzanine/werkbalk te klikken en te kiezen uit de volgende opties:

-

Beheer tabs  — Toont een pop-upvenster met de volgende opties:

![De Beheer Tabs pop-up in Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Manage-Tabs-Popup.png)

1.

Toon of verberg de tab.

2.

Met een geselecteerde tab, herschik deze ten opzichte van de andere tabs.

3.

Verwijder een geselecteerde [aangepaste tab](#aangepaste-tabs) .

4.

Kies tussen tabs Centraal  uitlijnen of Links  uitlijnen (naast de [testbesturingselementen](/docs/nl-nl/studio/testing-modes#playtest-options) ).

-

Werkbalk samenvouwen  — Maximaliseert de ruimte door de werkbalk te verbergen terwijl de mezzanine zichtbaar blijft. Als je met de muis over een tab in de mezzanine beweegt, wordt de werkbalk tijdelijk zichtbaar.

-

Compacte werkbalk  — Maakt de werkbalk aanzienlijk compacter door kleinere pictogrammen en labels, ideaal voor laptops of kleinere monitoren.

-

Toon labels  — Schakelt de tekstlabels onder tools aan of uit.

### [Aangepaste tabs](#aangepaste-tabs)[](#aangepaste-tabs)

Naast de standaard tooltabs kun je aangepaste tabs  toevoegen voor jouw specifieke behoeften, hetzij via de interface van Studio of door lokale .json -bestanden te bewerken.

Studio JSON

De gemakkelijkste manier om aangepaste tabs te maken is via de workflow van Studio.

1.

Klik op de +  knop rechts van de standaard tabs, typ een naam voor de nieuwe tab en druk op Enter .

 ![Knop om een aangepaste tab toe te voegen aangegeven in de mezzanine van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Add-Custom-Tab.png)

Als alternatief voor het maken van een nieuwe, lege tab, kun je een bestaande tab dupliceren door er met de rechtermuisknop op te klikken en Tab dupliceren  te selecteren. In tegenstelling tot standaard tabs kunnen tools binnen gedupliceerde tabs vrij worden gewijzigd.

2.

Klik op de knop of klik met de rechtermuisknop in een leeg gebied van de werkbalk en selecteer Voeg tools toe .

 ![Knop om een nieuwe tool toe te voegen aan een aangepaste tab in de werkbalk van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Custom-Tab-Add-Tool.png)

3.

In het pop-upvenster, zoek naar een tool en schakel het selectievakje in om toe te voegen. Nieuwe tools verschijnen rechts van andere tools, maar je kunt met de rechtermuisknop op een tool klikken en Verplaats links  of Verplaats rechts  selecteren om deze ten opzichte van andere tools te herschikken. Je kunt ook een scheidingslijn invoegen door met de rechtermuisknop in een leeg gebied van de werkbalk te klikken en Voeg scheidingslijn toe  te selecteren.

 ![Aangepaste tab gevuld met tools.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Custom-Tab-Filled.png)

Als je een tool uit een aangepaste tab wilt verwijderen, klik er dan met de rechtermuisknop op en selecteer Verwijder tool .

## [3D-viewport](#3d-viewport)[](#3d-viewport)

De 3D-viewport vertegenwoordigt de [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  van een plaats. Van hieruit kun je de camera door de virtuele wereld bewegen, objecten met de muis manipuleren en een spel testen zonder Studio te verlaten.

![Een voorbeeld van een viewportweergave van een woestijnomgeving met meerdere stenen pilaren. Een van de pilaren toont bewegingsvisualisaties van de Verplaats tool.](https://prod.docsiteassets.roblox.com/assets/studio/general/Editor-Window.jpg) 3D-viewport in Roblox Studio

### [Camera-besturingselementen](#camera-besturingselementen)[](#camera-besturingselementen)

Binnen de viewport kun je de camera bewegen met de volgende besturingselementen.

| Sleutels/Sneltoetsen | | Actie |
| --- | --- |
| W  A  S  D | | Verplaatst de camera vooruit/links/achteruit/rechts. |
| Q  E | | Verplaatst de camera omlaag/omhoog. |
| Shift | | In combinatie met een van de bewegingssleutels, verandert de camerasnelheid. |
| F | | Focust de camera op een geselecteerd onderdeel. |
| Rechtermuisknop | | Wanneer ingedrukt, verplaatst het slepen van de muis het camerabeeld. |
| Muis Scrollwiel
Ctrl =  of ⌘ =
Ctrl -  of ⌘ -  of O | | Zoomt de camera in of uit.
Zoomt de camera in.
Zoomt de camera uit. |
| ,  / . | | Rotates de camera links/rechts. Als een onderdeel/model in focus is via de F  sneltoets, roteert de camera tegen de klok in/ met de klok mee rond dat gefocuste object. |
| Middenmuisknop | | Wanneer ingedrukt, verplaatst het slepen van de muis de camera. |
| Rechtermuisknop  & Muis Scrollwiel | | Het indrukken van de rechtermuisknop en het scrollen van het muiswiel omhoog  verhoogt de camerascrollsnelheid. Omgekeerd, het indrukken van de rechtermuisknop en het scrollen van het muiswiel omlaag  vermindert de camerascrollsnelheid.

Deze functie is momenteel in beta. Schakel het in via Bestand  ⟩ Bèta-functies  ⟩ Nieuwe Studio Camera Besturing .

 |

### [Objectselectie](#objectselectie)[](#objectselectie)

Wanneer je over onderdelen en modellen in de viewport beweegt, worden ze omrand om hun potentiële selectie aan te geven. Je kunt een omrand object selecteren door erop te klikken, of je kunt meerdere objecten selecteren door Shift , Ctrl  of ⌘  ingedrukt te houden terwijl je erover beweegt en erop klikt.

 ![Een magazijnomgeving met de trap en meerdere palletdozen met een blauwe markering om aan te geven dat ze zijn geselecteerd in de 3D-viewport.](https://prod.docsiteassets.roblox.com/assets/studio/general/Editor-Window-Object-Selection.jpg)

In complexere omgevingen of wanneer je inzoomt, zullen objecten vaak uit het zicht worden verborgen door andere objecten ervoor. Om verborgen objecten te selecteren zonder de camera te verplaatsen, houd Alt  of ⌥  ingedrukt en klik om selectie-cycling  naar het volgende verder gelegen object achter het momenteel geselecteerde object uit te voeren.

Wanneer een of meer objecten of [modellen](/docs/nl-nl/parts/models)  zijn geselecteerd in het [Explorer](/docs/nl-nl/studio/explorer)  venster, kun je al hun kinderen  selecteren door met de rechtermuisknop te klikken en Hiërarchie  ⟩ Selecteer Kinderen  te kiezen uit het contextmenu. Evenzo selecteert het kiezen van Selecteer Ouder(s)  de directe ouders  van die objecten.

Om het uiterlijk van selectielijnen en -dozen rond objecten aan te passen, stel je jouw gewenste opties in de sectie Selectievisualisatie  binnen het Selectie  paneel van de instellingen van Studio in.

 ![Een magazijnomgeving met de selectieomtrek en begrenzingsdoos van een touwobject gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/studio/general/Selected-Object-Bounding-Box.jpg)

### [Visualisatie-opties](#visualisatie-opties)[](#visualisatie-opties)

In de rechterbovenhoek van de 3D-viewport kun je snel veelvoorkomende visualisatie-opties met betrekking tot [on-screen UI](/docs/nl-nl/ui/on-screen-containers)  overlays, [lichtbronnen](/docs/nl-nl/effects/light-sources) , fysica-simulatie, karakter [padvinding](/docs/nl-nl/characters/pathfinding) , en meer in- of uitschakelen. Het menu bevat ook een controle voor het bekijken/instellen van de camerascrollsnelheid.

 ![Een close-up van de 3D-viewport met de knop Visualisatie-opties aangegeven in de rechterbovenhoek.](https://prod.docsiteassets.roblox.com/assets/studio/general/Visualization-Options.png)

## [Veelgebruikte tools](#veelgebruikte-tools)[](#veelgebruikte-tools)

Veelgebruikte vensters zijn onder andere het [Explorer](/docs/nl-nl/studio/explorer) , het [Eigenschappen](/docs/nl-nl/studio/properties)  venster, [Asset Manager](/docs/nl-nl/projects/assets/manager) , [Toolbox](/docs/nl-nl/projects/assets/toolbox) , en anderen.

### [Explorer](#explorer)[](#explorer)

Het [Explorer](/docs/nl-nl/studio/explorer)  venster, standaard zichtbaar en toegankelijk vanuit het Venster  menu of de Home  tab, toont een hiërarchische lijst van elk object en elke service binnen de plaats, gezamenlijk aangeduid als het datamodel . Veelgebruikte services in de hiërarchie zijn [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  die de [3D-viewport](#3d-viewport)  weerspiegelt, evenals [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  en [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage) .

 ![Explorer-hiërarchie die Camera, Terrain en SignModel toont als kinderen van Workspace; Board en Post als kinderen van SignModel](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Parent-Child-Hierarchy.png)

### [Eigenschappen](#eigenschappen)[](#eigenschappen)

Het [Eigenschappen](/docs/nl-nl/studio/properties)  venster, standaard zichtbaar en toegankelijk vanuit het Venster  menu of de Home  tab, laat je de eigenschappen van een geselecteerd object aanpassen om te veranderen hoe het eruitziet en zich gedraagt. Objecteigenschappen zijn verdeeld in secties; bijvoorbeeld, een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  bevat secties zoals Uiterlijk  waarmee je de kleur, het materiaal, de transparantie en meer kunt wijzigen.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Sections-Example.png)

Onderaan het venster kun je aangepaste [attributen](/docs/nl-nl/studio/properties#instantie-attributen)  voor een object definiëren, vergelijkbaar met de standaard eigenschappen. Attributen en hun waarden worden opgeslagen met jouw plaats/assets en zijn een ideale manier voor teamleden om tijdens runtime met verschillende waarden te experimenteren, zelfs als ze de onderliggende code niet begrijpen.

 ![Een close-up van de Attributen sectie van het Eigenschappen venster.](https://prod.docsiteassets.roblox.com/assets/studio/properties/Attributes-Example.png)

### [Asset Manager](#asset-manager)[](#asset-manager)

De [Asset Manager](/docs/nl-nl/projects/assets/manager) , toegankelijk vanuit het Venster  menu of de Home  tab, laat je plaatsen, afbeeldingen, meshes, audio en meer beheren. Het biedt ook een mechanisme om grote groepen assets in bulk te importeren.

### [Toolbox](#toolbox)[](#toolbox)

De [Toolbox](/docs/nl-nl/projects/assets/toolbox) , toegankelijk vanuit het Venster  menu of de Home  tab, bevat een selectie van modellen, afbeeldingen, meshes, audio, plugins, video's en lettertypen gemaakt door Roblox of leden van de Roblox-community. Het bevat ook al jouw creaties die je persoonlijk [op de Creator Store](/docs/nl-nl/production/creator-store)  hebt verspreid of die zijn verspreid door [groepen](/docs/nl-nl/projects/groups)  waartoe je behoort.

 ![Het Toolbox venster.](https://prod.docsiteassets.roblox.com/assets/studio/toolbox/Model-Search-Example.png)

### [Output](#output)[](#output)

Het [Output](/docs/nl-nl/studio/output)  venster, toegankelijk vanuit het Venster  menu of de Script  tab, toont fouten die zijn vastgelegd van het uitvoeren van scripts, berichten van de Roblox Engine, berichten van aanroepen naar [print()](/docs/nl-nl/reference/engine/globals/LuaGlobals#print) , en fouten van aanroepen naar [warn()](/docs/nl-nl/reference/engine/globals/RobloxGlobals#warn) .

### [Opdrachtbalk](#opdrachtbalk)[](#opdrachtbalk)

De Opdrachtbalk , toegankelijk vanuit de werkbalk van de Script  tab of het Venster  ⟩ Script  menu, laat je Luau-code uitvoeren buiten scripts. Om snel naar de opdrachtbalk te springen, druk je op Ctrl 9  (Windows) of ⌘ 9  (Mac).

De meeste functies die hieronder zijn beschreven zijn in bèta en moeten worden ingeschakeld via Bestand  ⟩ Bèta-functies  ⟩ Multi-line Command Bar .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/general/Command-Bar.png)

Functies omvatten:

-

Multiline bewerking  — Druk op Enter  om nieuwe regels in te voegen terwijl je typt. De balk begint met 2 regels, groeit tot 10 regels naarmate er nieuwe regels worden ingevoegd, en krimpt wanneer regels worden verwijderd. Wanneer je klaar bent om de inhoud van de balk uit te voeren, klik je op de Uitvoeren  knop of gebruik je de sneltoets Ctrl Enter  (⌘ Enter ).

-

Opdrachtgeschiedenis  — De laatste 10 uitgevoerde opdrachten zijn zichtbaar door op de Geschiedenis  knop te klikken en naar de Recent  tab te navigeren. Door op een opdracht in de lijst te klikken, wordt deze in de balk geladen, of je kunt door de lijst navigeren met ↑ / ↓  en de gemarkeerde opdracht invoegen met Enter . Alternatief kun je door opdrachten scrubben met Ctrl / ⌘  + ↑ / ↓  wanneer de opdrachtbalk is geselecteerd.

-

Opgeslagen opdrachten  — Je kunt opdrachten expliciet opslaan met de Opslaan  knop of de standaard sneltoets Ctrl B  (⌘ B ). Opgeslagen opdrachten zijn toegankelijk via de Opgeslagen  tab in de pop-uplijst, en de mechanismen voor het laden van opgeslagen opdrachten uit de lijst zijn hetzelfde als die in de opdrachtgeschiedenis.

-

Integratie met de Script Editor  — De opdrachtbalk is een ingebouwde scripteditor en ondersteunt een breed subset van de [Script Editor](/docs/nl-nl/studio/script-editor)  functies van Studio, inclusief [autocompletion](/docs/nl-nl/studio/script-editor#autocomplete-functies) , Luau [linting](https://luau.org/lint) , [ga naar declaratie](/docs/nl-nl/studio/script-editor#ga-naar-declaratie) , [functie filter](/docs/nl-nl/studio/script-editor#scriptfunctiefilter) , [Code Assist](/docs/nl-nl/studio/script-editor#code-assistent) , en [multi-cursor](/docs/nl-nl/studio/script-editor#multi-cursor) .

## [Lay-out aanpassing](#lay-out-aanpassing)[](#lay-out-aanpassing)

De drag-and-drop interface van Studio laat je gemakkelijk de vensterlay-out aanpassen om het beste bij jouw workflows te passen.

### [Vensters verplaatsen](#vensters-verplaatsen)[](#vensters-verplaatsen)

Je kunt elk venster verplaatsen door op de kopbalk  te klikken en te slepen. Terwijl je het venster begint te slepen, onthult de interface lege dockinggebied  regio's. Als je de muisaanwijzer in een leeg gebied sleept, verschijnt er een zwevende positie-selector  in dat gebied. Het slepen van de aanwijzer over het "centrum" van de zwevende selector richt het lege gebied aan als de bestemming van het gesleepte venster, wat wordt aangegeven door het gebied dat donkerder wordt en omrand is.

![Muisaanwijzer die boven het 'centrum' pictogram van de positie-selector in een leeg dockinggebied zweeft, wat dat gebied aangeeft als de bestemming van het gesleepte venster.](https://prod.docsiteassets.roblox.com/assets/studio/general/Docking-Position-Selector-Empty.png) Muisaanwijzer die boven het "centrum" pictogram van de positie-selector in een leeg dockinggebied zweeft

Als je de muisaanwijzer in een bevolkt  gebied sleept, zoals de 3D-viewport, verschijnt er een zwevende positie-selector met meerdere opties voor de bestemming van het venster. Bijvoorbeeld, als je de aanwijzer over het "linker" pictogram sleept, wordt het venster aan de linkerkant van het gebied geplaatst.

Viewport links Viewport rechts

![Muisaanwijzer die boven het 'linker helft' pictogram van de positie-selector in een bevolkt gebied zweeft, wat de linkerkant van het gebied aangeeft als de bestemming van het gesleepte venster.](https://prod.docsiteassets.roblox.com/assets/studio/general/Docking-Position-Selector-Left.png)

### [Vensters groeperen](#vensters-groeperen)[](#vensters-groeperen)

Als je een venster in een bevolkt  gebied sleept en het "centrum" pictogram van de [positie-selector](#vensters-verplaatsen)  kiest, wordt het gesleepte venster in dat gebied gegroepeerd als een tab. Dit stelt je in staat om tabgroepen van veelgebruikte vensters in te stellen.

![Een voorbeeld van een Explorer-venster als je het centrum pictogram van de positie-selectie kiest. Het bevat drie tabs onderaan het venster: het Explorer-venster, het Eigenschappen-venster en het Terrain Editor-venster.](https://prod.docsiteassets.roblox.com/assets/studio/general/Docking-Grouped-Tabs.png) Drie vensters gegroepeerd als tabs

### [Vensters vastpinnen](#vensters-vastpinnen)[](#vensters-vastpinnen)

Om de schermruimte voor de 3D-viewport te maximaliseren, kun je vensters (of een hele [groep](#vensters-groeperen)  vensters) aan de randen van het totale Studio-venster vastpinnen . Eenmaal vastgepind, kun je tijdelijk elk venster openen door op de tab te klikken — dit verstoort andere vensters niet, en het uitgebreide venster wordt automatisch samengevouwen wanneer je in een ander venster klikt of opnieuw op de tab klikt.

![Een voorbeeld van een 3D-viewport waar de Explorer, Eigenschappen en Terrain Editor vensters aan de rechterkant van het Studio-venster zijn vastgepind.](https://prod.docsiteassets.roblox.com/assets/studio/general/Docking-Pinned-Tabs.png) Drie vensters vastgepind aan de rechterkant van het Studio-venster

Om een venster of een hele [groep](#vensters-groeperen)  vensters vast te pinnen, klik je op de "samenvouw" knop. Om een vastgepind venster/groep los te maken, open je het door op de tab te klikken, en klik je vervolgens op de "uitvouw" knop.

 ![Een close-up van het Explorer-venster met de Samenvouw-knop gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/studio/general/Docking-Expand-Collapse.png)

### [Vensters drijven](#vensters-drijven)[](#vensters-drijven)

Om een venster vrij van andere vensters te laten drijven, sleep je het eenvoudig zonder een pictogram van de zwevende [positie-selector](#vensters-verplaatsen)  te selecteren.

## [Vensters schermafbeeldingen](#vensters-schermafbeeldingen)[](#vensters-schermafbeeldingen)

Je kunt een afbeelding vastleggen van een individueel Studio-venster, zoals het [Output](/docs/nl-nl/studio/output)  venster, een venster van een plugin, of de viewport, zonder de rest van Studio vast te leggen. Dit is nuttig om het volledige Output-venster met je team te delen of een probleem te rapporteren aan de maker van een plugin.

1.

Druk op Ctrl Shift 2 , of voer de actie Screenshot Plugin  uit vanuit de snelle acties van Studio.

2.

Selecteer het venster dat je wilt vastleggen. De vastgelegde afbeelding wordt naar je klembord gekopieerd. Dialoogvensters kunnen niet worden vastgelegd.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
