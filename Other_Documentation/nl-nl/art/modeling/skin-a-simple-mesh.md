<!-- Source: https://create.roblox.com/docs/nl-nl/art/modeling/skin-a-simple-mesh -->

Een eenvoudige mesh skinnen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Animatie
6. /
7. In Blender

# Een eenvoudige mesh skinnen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een geskinnde mesh is een gerigged mesh die natuurlijk buigt en flexeert wanneer het interne skelet wordt geposeerd of geanimeerd. Je kunt een geskinnde mesh maken met een externe modelleringstool zoals [Blender](https://www.blender.org)  of [Maya](https://www.autodesk.com/products/maya/overview) . Skinning moet worden voltooid nadat het model is [gerigged](/docs/nl-nl/art/modeling/rigging) .

Deze gids behandelt het proces voor het riggen en vervolgens skinnen van een eenvoudig boommodel in Blender met 3 botten. Voor de basisprincipes van rigging, zie [Rig een eenvoudige mesh](/docs/nl-nl/art/modeling/rig-a-simple-mesh)  voordat je deze gids voortzet.

Om een eenvoudige mesh te skinnen, moet je:

-

[Blender instellen](#blender-instellen)  op de relatieve scène-eenheden van Studio voordat je een model importeert.

-

[Botten maken, schalen en positioneren](#botten-positioneren)  binnen een armatuur.

-

[Een mesh aan een armatuur koppelen](#armatuur-koppelen)  om het skelet aan het meshobject te binden.

-

[Gewicht schilderen](#gewicht-schilderen)  op de mesh om aan te geven welke delen van de mesh met welk bot zullen bewegen.

Deze gids maakt gebruik van een downloadbaar [voorbeeld boommodel](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/MapleLeafTree.fbx)  en [Blender versie 3.0](https://www.blender.org/download/releases/3-0/) . Als je een andere versie van Blender gebruikt, kunnen er kleine verschillen zijn in de gebruikersinterface en instellingen.

## [Blender instellen](#blender-instellen)[](#blender-instellen)

Om te beginnen met het maken van een geskinnde mesh, stel je eerst het volgende in je Blender-project in:

1.

Open een nieuw Algemeen  project in Blender.

2.

Selecteer de standaardvorm, camera en lichten, en druk vervolgens op Delete .

### [Een model importeren](#een-model-importeren)[](#een-model-importeren)

Voor deze gids importeer je een [esdoornboommodel](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/MapleLeafTree.fbx)  in Blender als je meshobject.

Om een model in Blender te importeren:

1.

Klik in de bovenbalk op Bestand . Een pop-upmenu verschijnt.

2.

Selecteer Importeren , en vervolgens het bestandsformaat van het model dat je importeert. Voor dit voorbeeld selecteer je FBX (.fbx)  en het .fbx  referentiemodel. Het model wordt weergegeven in de 3D-weergave.

 ![Viewport Display Settings](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Import-Model.jpg)

## [Een botstructuur maken](#een-botstructuur-maken)[](#een-botstructuur-maken)

Nu je model zich in Blender bevindt, voeg je een armatuur en botten  toe aan je meshobject. Een armatuur  is een skeletachtig riggingobject dat fungeert als een container voor botten, terwijl botten  objecten zijn die de beweging en vervorming van de groep van vertices, of vertexgroep , die het bot omringen, controleren.

### [Een armatuur toevoegen](#een-armatuur-toevoegen)[](#een-armatuur-toevoegen)

Een armatuur is een structuur die nodig is om botten aan je mesh toe te voegen. Nadat je een armatuur hebt toegevoegd, kun je een onbeperkt aantal botten binnen je meshobject maken en opnieuw positioneren.

Om een armatuur toe te voegen:

1.

Selecteer bovenaan de 3D-weergave Toevoegen  → Armatuur .

2.

Voor een betere visualisatie van de botten, navigeer in de linker navigatie van de Eigenschappen-editor  naar Armatuur Objecteigenschappen .

3.

In de sectie Viewportweergave , navigeer naar de eigenschap Weergeven als , en schakel Voor aan  in.

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Bone-Visualization.png)

### [Botten positioneren](#botten-positioneren)[](#botten-positioneren)

Wanneer je een armatuur aan je project toevoegt, voegt Blender ook één bot toe aan de armatuur op een standaardpositie en -schaal. Je kunt het bot draaien en schalen om de interne structuur van je meshobject nauwkeuriger weer te geven.

Om het bot opnieuw te positioneren:

1.

Klik op het botobject  om het te markeren.

2.

Klik bovenaan de 3D-weergave op de dropdown voor de modus en schakel over naar Bewerkmodus .

3.

Klik op de top van het bot  en druk op G . De top van het bot beweegt met je cursor.

4.

Trek dit bot om het uit te lijnen met het interne centrum van het model, en klik vervolgens om de positie van het bot in te stellen.

5.

Druk en houd het scrollwiel van je muis ingedrukt om de camera rond het meshobject te bewegen om verschillende weergaven en hoeken te zien en ervoor te zorgen dat het bot gecentreerd is binnen het meshobject.

### [Extra botten toevoegen](#extra-botten-toevoegen)[](#extra-botten-toevoegen)

In deze gids heb je 3 botten binnen je mesh nodig, zodat de boom op drie punten kan bewegen en draaien.

Om extra botten aan de armatuur toe te voegen:

1.

Terwijl je nog in Bewerkmodus  bent, klik op de punt van het bot.

2.

Druk op E  en sleep je muis omhoog. Dit verlengt een extra bot uit het oorspronkelijke wortelbot.

3.

Herhaal dit proces voor het tweede bot.

4.

Druk en houd het scrollwiel van je muis ingedrukt om de camera rond het meshobject te bewegen om verschillende weergaven en hoeken te zien en ervoor te zorgen dat de botten binnen het meshobject zijn. [Herpositioneer de botten](#botten-positioneren)  indien nodig.

5.

In de Outliner, vouw het Armatuur  object uit. De hiërarchie van de botten van de armatuur wordt weergegeven.

6.

In de Outliner, dubbelklik en hernoem  elk bot. De namen van de botobjecten blijven hetzelfde wanneer je het meshobject in Studio importeert.

## [Armatuur koppelen](#armatuur-koppelen)[](#armatuur-koppelen)

Nadat de botstructuur is gemaakt en gepositioneerd, moet je de armatuur aan het meshobject koppelen door de armatuur aan het meshobject te koppelen.

Deze gids maakt gebruik van de functie Automatische Gewichten  van Blender wanneer je een armatuur koppelt, omdat deze automatisch gewichten en invloeden aan je mesh toevoegt. Dit kan je tijd besparen tijdens het [gewicht schilderen](#gewicht-schilderen)  proces.

Om een armatuur aan een mesh te koppelen:

1.

Klik bovenaan de 3D-weergave op de dropdown voor de modus en schakel terug naar Objectmodus .

2.

Druk op Alt A  (Windows) of ⌥ A  (Mac) om elk object te deselecteren.

3.

Houd shift  ingedrukt en selecteer het meshobject  en vervolgens de armatuur . De volgorde van selectie is belangrijk.

4.

Klik met de rechtermuisknop op het meshobject  in de viewport. Een pop-upmenu verschijnt.

5.

Selecteer Ouder , en vervolgens Met Automatische Gewichten .

## [Gewicht schilderen](#gewicht-schilderen)[](#gewicht-schilderen)

Met je armatuur verbonden met het meshobject, kun je het proces van gewicht schilderen  gebruiken om de hoeveelheid invloed (gewicht) die de botten op specifieke vertices hebben te veranderen, zodat er natuurlijkere beweging en flexibiliteit mogelijk is.

Blender vertegenwoordigt de gewichtsterkte met een [blauw naar rood verloop](https://docs.blender.org/manual/en/latest/sculpt_paint/weight_paint/introduction.html#the-weighting-color-code) , waarbij blauw  een waarde van 0  vertegenwoordigt en rood  een volledig beïnvloedde waarde van 1 . Vertices op een meshobject die rood zijn geschilderd, worden volledig beïnvloed door de rotatie van dat specifieke bot, terwijl vertices die geel of groen zijn, gedeeltelijk worden beïnvloed door de rotatie van het bot.

Je kunt snel invloed toewijzen met de [Borsteltool](https://docs.blender.org/manual/en/latest/sculpt_paint/weight_paint/tools.html)  in Blender's Gewicht Schilderen  modus met behulp van de Tekenen , Toevoegen  of Aftrekken  borsteltools. Voor elke borstel kun je het invloedgewicht en de straal instellen in de Tools -instelling rechts van de Viewport .

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Brush-Settings.png)

Om het schilderproces te optimaliseren, [stel visualisatie en borstelinstellingen in](#instellen)  voordat je [invloeden schildert](#invloed-schilderen)  op de mesh.

### [Instellen](#instellen)[](#instellen)

Bij het toewijzen van invloeden voor complexe modellen, kun je de volgende Blender-instellingen configureren om het Gewicht Schilderen proces te optimaliseren.

#### [Botvisualisatie](#botvisualisatie)[](#botvisualisatie)

Standaard toont Blender botobjecten als octaëdrische vormen. Deze oorspronkelijke vorm is nuttig bij het positioneren van botten binnen de rig, maar kan in de weg zitten tijdens het schilderen. Om de visualisatie van het gewicht schilderen te helpen, verander je de visualisatie van je botten naar stokken.

Om de visualisatie van je botten bij te werken:

1.

Selecteer in Objectmodus  de Armatuur .

2.

Navigeer in de linker navigatie van de Eigenschappen-editor  naar Objectdata-eigenschappen .

3.

Verander de waarde van Weergeven als  naar Stick .

#### [Auto normaliseren](#auto-normaliseren)[](#auto-normaliseren)

De instelling [Auto Normaliseren](https://docs.blender.org/manual/en/latest/sculpt_paint/weight_paint/tool_settings/options.html)  dwingt de invloed op je vertices om gelijk te zijn aan één. Dit maakt gewicht schilderen efficiënter door ervoor te zorgen dat elke vertex in je karakter volledig wordt beïnvloed door ten minste één bot. In deze gids stelt Auto Normaliseren je in staat om eerst snel volledige invloed op de hele mesh toe te passen en vervolgens kleine aanpassingen met elk bot te maken.

Om Auto Normaliseren in te schakelen:

1.

Selecteer in Objectmodus  de Armatuur .

2.

Houd shift  ingedrukt en selecteer het meshobject .

3.

Klik bovenaan de 3D-weergave op de dropdown voor de modus en schakel over naar Gewicht Schilderen  modus.

Je moet het juiste object selecteren om toegang te krijgen tot specifieke modi, zoals het selecteren van een meshobject om toegang te krijgen tot Gewicht Schilderen  modus. Als je niet bekend bent met het schakelen tussen verschillende modi, raadpleeg dan [Objectmodi](https://docs.blender.org/manual/en/latest/editors/3dview/modes.html) .

4.

Klik aan de rechterkant van de viewport op het Tool -tabblad.

5.

Schakel onder de sectie Opties  Auto Normaliseren  in.

#### [Geprojecteerde borstel](#geprojecteerde-borstel)[](#geprojecteerde-borstel)

Een geprojecteerde borstel stelt je in staat om gemakkelijk invloed door een mesh toe te passen, in plaats van alleen op het oppervlak. Dit is nuttig bij het schilderen van invloeden op meshes die geometrisch gelaagd kunnen zijn, zoals het loof van de boom.

Om een geprojecteerde borstel in te stellen:

1.

Selecteer in Objectmodus  de Armatuur .

2.

Houd shift  ingedrukt en selecteer het meshobject .

3.

Klik bovenaan de 3D-weergave op de dropdown voor de modus en schakel over naar Gewicht Schilderen  modus.

4.

Klik aan de rechterkant van de viewport op het Tool -tabblad.

5.

Vouw de sectie Geavanceerd  uit en schakel Alleen Voorste Vlakken  uit.

6.

Vouw de sectie Afname  uit en selecteer Geprojecteerd .

### [Invloed schilderen](#invloed-schilderen)[](#invloed-schilderen)

Met de [geprojecteerde borstel](#geprojecteerde-borstel)  ingesteld, kun je nu beginnen met het toepassen van invloed op de boom. Maak gebruik van de instelling [Auto Normaliseren](#auto-normaliseren)  door volledige rode invloed op de hele boom naar het onderste bot te schilderen en vervolgens een gedeeltelijke invloed op de middelste en bovenste botten toe te wijzen.

#### [Onderste bot](#onderste-bot)[](#onderste-bot)

De onderste bot moet de beweging van de hele boom volledig beïnvloeden, beginnend vanaf de stam.

Om invloed op de onderste bot te schilderen:

1.

In Objectmodus , houd shift  ingedrukt, selecteer de botten en vervolgens het meshobject.

2.

Klik bovenaan de 3D-weergave op de dropdown voor de modus en schakel over naar Gewicht Schilderen  modus.

3.

Houd shift  ingedrukt en klik op de onderste bot.

4.

Gebruik de borsteltools om een rode invloed van het basis van het bot en de rest van de boom te schilderen.

Je kunt de straal van de borstel aanpassen in het ** Tool**  tabblad, of door F  ingedrukt te houden en je muis te slepen om de grootte te veranderen.

5.

Met het bot gemarkeerd, test of het bot het hele model beïnvloedt door op R  te drukken en de muis te draaien. Schilder op alle vertices die niet correct worden beïnvloed om invloed op hen toe te passen.

#### [Middelste bot](#middelste-bot)[](#middelste-bot)

De middelste bot vertegenwoordigt het grootste deel van het loof boven de onderste bot. Voor een subtieler effect, pas een invloed van 50% (groen) van de middelste bot naar boven toe toe.

Om invloed op de middelste bot te schilderen:

1.

In Gewicht Schilderen  modus, druk op Alt A  (Windows) of ⌥ A  (Mac) om het huidige botobject te deselecteren.

2.

Houd shift  ingedrukt en klik  op de middelste bot.

3.

Klik aan de rechterkant van de viewport op het Tool -tabblad.

4.

Verander de Gewicht  waarde naar .5 .

5.

Begin vanaf het gebied bij de middelste bot en schilder het middelste en bovenste gebied van de boom.

6.

Druk op R  om het bot te draaien en test de invloed vanuit verschillende hoeken.

#### [Bovenste bot](#bovenste-bot)[](#bovenste-bot)

De bovenste bot moet het bovenste bladgebied boven de middelste bot beïnvloeden. Schilder dit bovenste gebied met 25% invloed (teal) voor een natuurlijker effect.

Om invloed op de bovenste bot te schilderen:

1.

In Gewicht Schilderen  modus, druk op Alt A  (Windows) of ⌥ A  (Mac) om het huidige botobject te deselecteren.

2.

Houd shift  ingedrukt en klik op de bovenste bot.

3.

Klik aan de rechterkant van de viewport op het Tool -tabblad.

4.

Verander de Gewicht  waarde naar 0.25 .

5.

Begin vanaf het gebied bij de bovenste bot en schilder het bovenste gebied van de boom.

6.

Druk op R  om het bot te draaien en test de invloed vanuit verschillende hoeken.

Na het gewicht schilderen van elk bot, zou elk deel van deze boom nu beïnvloed moeten worden door de onderste, middelste of bovenste botten. De onderste bot controleert volledig de stam van de boom, terwijl de middelste en bovenste botten een verminderde invloed hebben op de takken en bladeren.

### [Testen](#testen)[](#testen)

Het is belangrijk om de invloeden van je bot gedurende  het gewicht schilderen proces constant te testen.

Blender stelt je in staat om botten te testen en te poseren terwijl  je schildert, als zowel de armatuur als de mesh zijn geselecteerd in Objectmodus voordat  je overschakelt naar Gewicht Schilderen modus. Deze hybride pose- en gewicht schilderfunctionaliteit werkt niet tenzij je zowel de armatuur als de mesh selecteert voordat je de Gewicht Schilderen modus ingaat.

Om je gewicht schilderen te testen:

1.

Selecteer in Objectmodus  de Armatuur .

2.

Houd shift  ingedrukt en selecteer het meshobject .

3.

Klik bovenaan de 3D-weergave op de dropdown voor de modus en schakel over naar Gewicht Schilderen  modus.

4.

Houd shift  ingedrukt en klik op het bot dat je wilt testen, druk vervolgens op R  om de rotatie te testen.

5.

Druk op Alt A  (⌥ A ) om het huidige bot te deselecteren, selecteer dan opnieuw en test een ander bot.

Om de rotatie van een geselecteerd bot naar neutraal te resetten, druk op Alt + R . Terwijl je draait, kun je ook het scrollwiel van je muis indrukken om de assen van je rotatie te veranderen. Het wordt aanbevolen om prioriteit te geven aan het testen van posities die je verwacht te gebruiken in je animaties en poses in Studio.

Je S1 boommodel is nu een geskinnde mesh en is klaar voor [export](/docs/nl-nl/art/modeling/export-requirements)  naar Studio. Het [Blender-projectbestand](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/MapleTreeS1.blend)  en de [eindexport](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/MapleLeafTree.fbx)  (.fbx ) zijn beschikbaar ter referentie.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
