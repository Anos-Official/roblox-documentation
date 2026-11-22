<!-- Source: https://create.roblox.com/docs/nl-nl/art/modeling/skin-a-humanoid-model -->

Een humanoïde model skinnen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Animatie
6. /
7. In Blender

# Een humanoïde model skinnen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een humanoïde geskinnde mesh is een karaktermodel dat, wanneer geposeerd of geanimeerd, op natuurlijke wijze buigt en uitrekt bij de gewrichten. Je kunt een geskinnde mesh maken met een externe modelleertool zoals [Blender](https://www.blender.org)  of [Maya](https://www.autodesk.com/products/maya/overview) .

Dit is een geavanceerde gids voor het skinnen van een humanoïde model naar een R15-model in Blender met behulp van het humanoïde model dat is voltooid in [Rig een humanoïde model](/docs/nl-nl/art/modeling/rig-a-humanoid-model) . Voordat je een humanoïde model gaat skinnen, moet je je ook vertrouwd maken met de basisconcepten in [Skin een eenvoudige mesh](/docs/nl-nl/art/modeling/skin-a-simple-mesh) .

Om een humanoïde model in Blender te skinnen, moet je:

-

[Blender instellen](#blender-instellen)  met een gerigged model om het gewichtsschilderproces te optimaliseren met instellingen voor botvisualisatie en Auto Normalize.

-

[Gewicht schilderen](#gewicht-schilderen)  van de vertices van je mesh-objecten door de invloed van je vertices tussen twee of meer botten van een humanoïde rig-architectuur in balans te brengen.

Deze gids gebruikt het humanoïde model dat is gerigged in [Rig een humanoïde model](/docs/nl-nl/art/modeling/rig-a-humanoid-model)  en [Blender versie 3.0](https://www.blender.org/download/releases/3-0/) . Als je een andere versie van Blender gebruikt, kunnen er kleine verschillen zijn in de gebruikersinterface en instellingen.

## [Blender instellen](#blender-instellen)[](#blender-instellen)

Deze gids gebruikt het gerigged model dat is voltooid in [Rig een humanoïde model](/docs/nl-nl/art/modeling/rig-a-humanoid-model) . Je kunt ook het gerigged model [Blender-project](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/lola-rigged-r15.blend)  downloaden om deze gids te volgen.

Om het proces van het skinnen van een rigide karakter te optimaliseren, stel je eerst het volgende in je Blender-project in:

-

Open het Blender-project en configureer de [botvisualisatie](#botvisualisatie)  instellingen.

-

Schakel [Auto Normalize](#auto-normaliseren)  in om het gewichtsschilderproces te optimaliseren.

### [Botvisualisatie](#botvisualisatie)[](#botvisualisatie)

Standaard toont Blender botobjecten als octaëdrische vormen. Deze oorspronkelijke vorm is nuttig bij het positioneren van botten, maar kan in de weg zitten tijdens het gewicht schilderen. Om de visualisatie tijdens het gewicht schilderproces te helpen, verander je je botvisualisatie naar stokken.

Om de visualisatie van je botten bij te werken:

1.

Klik in Objectmodus op de armature .

2.

In de Object Data Properties , wijzig de waarde van Display As  naar Sticks .

### [Auto normaliseren](#auto-normaliseren)[](#auto-normaliseren)

De Auto Normalize-instelling dwingt de invloed op je vertices om gelijk te zijn aan één. Dit maakt het gewicht schilderen van meerdere meshes en botten efficiënter door ervoor te zorgen dat elke vertex in je karakter volledig wordt beïnvloed door ten minste één bot. Zie de documentatie van Blender over de [Auto Normalize](https://docs.blender.org/manual/en/latest/sculpt_paint/weight_paint/tool_settings/options.html)  voor meer informatie.

Auto Normalize voorkomt ook gevallen waarin een vertex volledig wordt beïnvloed door meerdere botten en kan veelvoorkomende fouten bij het gewicht schilderen voorkomen.

Zonder Auto Normalize is het niet duidelijk totdat je test dat dit volledig beïnvloede hoofd ook door een ander bot wordt beïnvloed vanwege een schilderfout.

Met Auto Normalize verwijdert het schilderen van invloed naar een onjuist bot de bestaande invloed van het oorspronkelijke bot. Dit maakt fouten gemakkelijker te ontdekken en op te lossen.

Studio ondersteunt niet meer dan 4 botten om invloed uit te oefenen op een enkele vertex. Dit kan voorkomen in complexe rigs of per ongeluk met Auto Normalize uitgeschakeld.

Om Auto Normalize in te schakelen:

1.

In Objectmodus , selecteer de armature .

2.

Houd Shift  ingedrukt en selecteer een mesh-object  op je model.

3.

Klik bovenaan het 3D-venster op de dropdown voor de modus en schakel over naar Weight Paint -modus.

4.

Aan de rechterkant van het venster, vouw het Tool -tabblad uit.

5.

Onder Options , schakel Auto Normalize  in.

## [Gewicht schilderen](#gewicht-schilderen)[](#gewicht-schilderen)

Gewicht schilderen past specifieke gewichten of invloeden toe die botten zullen hebben over delen van een mesh met behulp van een schilderworkflow. Er zijn ook aanvullende manieren om invloeden toe te passen via gewicht schilderen of andere tools, waarvan sommige worden behandeld in [Skin een eenvoudige mesh](/docs/nl-nl/art/modeling/skin-a-simple-mesh) . Zie aanvullende online bronnen zoals Blender's [Character Rigging](https://www.youtube.com/watch?v=f2pTkW-1JkE)  en [Vertex Groups](https://www.youtube.com/watch?v=dKZrzG5r13g)  fundamentele gidsen voor meer informatie over skinning en het toepassen van gewichten.

Deze gids behandelt één proces van gewicht schilderen van de hoofd- en arm-meshes van een humanoïde model. Deze technieken voor gewicht schilderen kunnen worden gebruikt om de rest van het model te gewicht schilderen.

Pas geen invloeden toe op de Root of HumanoidRootNode ouderbotten in een humanoïde rig. Toegevoegde invloeden worden verwijderd bij het importeren in Studio.

### [Schilder de hoofdmesh](#schilder-de-hoofdmesh)[](#schilder-de-hoofdmesh)

De hoofdmesh is verbonden met de bovenste torso bij de onderste vertices van de nek. Om een realistische buiging in het model te creëren, moet de hoofdmesh invloed delen met het Hoofd-bot en het Bovenste Torso-bot nabij de neklijn.

Om te beginnen met gewicht schilderen van het Hoofd-meshobject:

1.

Klik in Objectmodus op de armature  en houd Shift  ingedrukt terwijl je op het Hoofd-meshobject  klikt.

2.

In de dropdown voor de modus, schakel over naar Weight Paint -modus.

3.

Houd Shift  ingedrukt en klik op het Bovenste Torso-bot . Het hoofd zou volledig blauw moeten zijn, aangezien de Bovenste Torso nog geen invloed heeft op de hoofdvertices.

Een veelvoorkomende fout is om gewichten toe te passen met het onjuiste bot geselecteerd. Zorg ervoor dat je Shift  selecteert en de juiste botten deselecteert bij het toepassen van gewichten. De naam van het bot dat momenteel wordt geschilderd, wordt weergegeven in het Venster.

4.

Rechtsboven in het Venster, open het Tool -menu en stel de borstelsterkte  in op 1 .

5.

Met het Bovenste Torso-bot geselecteerd, schilder  je het Hoofd van je model bij de neklijn. Je kunt tijdelijk de Bovenste Torso-mesh  in de Outliner verbergen om directe toegang tot de onderkant van de nek te hebben.

6.

Controleer op elk moment de toegepaste invloeden door Shift  ingedrukt te houden en het Bovenste Torso-bot te deselecteren en het Hoofd-bot te selecteren. Druk op R  om het Hoofd-bot met je muis te draaien en te testen hoe het meshobject invloeden deelt tussen het Hoofd- en Bovenste Torso-bot.

7.

Als er extra schilderen nodig is, houd Shift  ingedrukt en selecteer het bot waarvan je invloed wilt toevoegen of verwijderen, en gebruik de Borstel-tool om toe te passen.

Het eindresultaat van het gewicht schilderen van het hoofd van het model moet de invloeden van de hoofdmesh in balans brengen met het Hoofd-bot en het Bovenste Torso-bot:

![](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/skinning-humanoid/head-example-headbone-selected.png) Het Hoofd-bot beïnvloedt volledig de Head_Geo-mesh van de nek omhoog.

![](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/skinning-humanoid/head-example-uppertorso-selected.png) Het Bovenste Torso-bot beïnvloedt volledig de Head_Geo-mesh van de nek omlaag.

### [Schilder de arm-meshes](#schilder-de-arm-meshes)[](#schilder-de-arm-meshes)

Vergelijkbaar met het proces voor het balanceren van invloeden tussen het Hoofd-bot en het Bovenste Torso-bot, vereisen armen en benen een vergelijkbaar gewicht schilderproces.

De rechterarm omvat de Rechter Hand, Rechter Onderarm en Rechter Bovenarm, elk met hun bijbehorende botten. De volgende instructies bieden richtlijnen voor het schilderen van invloeden op alle arm-meshobjecten. Je kunt deze technieken vervolgens toepassen op de rest van de meshes in je model.

#### [Hand](#hand)[](#hand)

Te beginnen met de Rechter Hand, kun je de invloeden van de mesh balanceren tussen het Hand-bot  en het Onderarm-bot  om een natuurlijke buiging bij de pols te creëren.

Om invloeden naar de rechterhand te gewicht schilderen:

1.

Klik vanuit Objectmodus op de armature , houd Shift  ingedrukt en klik op de rechter hand  geometrie.

2.

In de dropdown voor de modus, schakel over naar Weight Paint -modus. Met het handbot geselecteerd in deze modus, kun je op R  drukken en de huidige rotatie van het handmeshobject testen.

3.

Rechtsboven in het Venster, open het Tool -menu en stel de borstelsterkte  in op 1 .

4.

Met het Onderarm-bot geselecteerd, schilder  je de hand van je model bij de pols. Je kunt tijdelijk de Onderarm-mesh  in de Outliner verbergen om betere toegang tot de pols te krijgen.

5.

Tijdens en na het gewicht schilderen van de hand, druk op R  met het bot geselecteerd om de rotatie en flexibiliteit te testen.

Je kunt extra botten toevoegen en skinnen, zoals vingers, als je extra controle over je geskinnde mesh wilt.

Extra botobjecten die zijn geskinnd aan een mesh maar geen naam van een Humanoid-botobject delen (zoals LowerTorso, LeftFoot, Right UpperArm) worden in Studio geïmporteerd als een [Bone](/docs/nl-nl/reference/engine/classes/Bone)  met dezelfde naam die het in de 3D-modelleringssoftware is toegewezen.

#### [Onderarm](#onderarm)[](#onderarm)

Nadat de pols van de rechterhand is gewichts geschilderd, kun je doorgaan met het balanceren van de invloeden van de Onderarm-mesh tussen het Onderarm-bot  en het Bovenarm-bot  om een natuurlijke buiging bij de elleboog te creëren.

Om invloeden naar de onderarm te gewicht schilderen:

1.

Schakel terug naar Objectmodus.

2.

Klik op de armature  en houd Shift  ingedrukt en klik op de rechter onderarm  geometrie.

3.

In de dropdown voor de modus, schakel over naar Weight Paint -modus.

4.

Houd Shift  ingedrukt en deselecteer andere botten behalve het Onderarm-bot. Je kunt de huidige rotatie van het gemarkeerde Onderarm-bot testen door op R  te drukken.

5.

Houd Shift  ingedrukt en selecteer het Bovenarm-bot.

6.

Met het Bovenarm-bot geselecteerd, schilder  je de onderarm van je model bij de elleboog. Je kunt tijdelijk de Bovenarm-mesh  in de Outliner verbergen om betere toegang tot de elleboog te krijgen.

7.

Tijdens en na het gewicht schilderen van de onderarm, druk op R  met het onderarm-bot geselecteerd om de rotatie en flexibiliteit te testen.

#### [Bovenarm](#bovenarm)[](#bovenarm)

Nadat de elleboog van de rechteronderarm is gewichts geschilderd, kun je doorgaan met het balanceren van de invloeden van de Bovenarm-mesh tussen het Bovenarm-bot  en het Bovenste Torso-bot  om een natuurlijke buiging bij de oksel te creëren.

Om invloeden naar de bovenarm te gewicht schilderen:

1.

Schakel terug naar Objectmodus.

2.

Klik op de armature  en houd Shift  ingedrukt en klik op de rechter bovenarm  geometrie.

3.

In de dropdown voor de modus, schakel over naar Weight Paint -modus.

4.

Houd Shift  ingedrukt en deselecteer andere botten behalve het Bovenarm-bot. Je kunt de huidige rotatie van het gemarkeerde Bovenarm-bot testen door op R  te drukken.

5.

Druk op R  en sleep je muis om de Bovenarm te draaien zodat de arm horizontaal is. Dit maakt het gemakkelijker om toegang te krijgen tot de vertices van de oksel.

6.

Houd Shift  ingedrukt en selecteer het Bovenste Torso-bot.

7.

Met het Bovenste Torso-bot geselecteerd, schilder  je de bovenarm van je model bij de oksel. Je kunt tijdelijk de Bovenste Torso-mesh  in de Outliner verbergen om betere toegang tot de elleboog te krijgen.

8.

Tijdens en na het gewicht schilderen van de onderarm, druk op R  met het bovenarm-bot geselecteerd om de rotatie en flexibiliteit te testen.

#### [Schouder](#schouder)[](#schouder)

Nadat de oksel is gewichts geschilderd, kun je doorgaan met het balanceren van de invloeden van de Bovenste Torso-mesh tussen het Bovenste Torso-bot  en het Bovenarm-bot  om een natuurlijke buiging bij de schouder te creëren wanneer de arm wordt bewogen. Aangezien deze beweging subtiel is, hoef je alleen een gedeeltelijke sterkte-invloed op deze vertices toe te passen.

Om een gedeeltelijke sterkte-invloed naar de bovenste torso te gewicht schilderen:

1.

Schakel terug naar Objectmodus.

2.

Klik op de armature  en houd Shift  ingedrukt en klik op de bovenste torso  geometrie.

3.

In de dropdown voor de modus, schakel over naar Weight Paint -modus.

4.

Houd Shift  ingedrukt en deselecteer andere botten behalve het Bovenarm-bot. Je kunt de huidige rotatie van het gemarkeerde Bovenarm-bot testen door op R  te drukken.

5.

Rechtsboven in het Venster, open het Tool -menu en stel de borstelsterkte  in op .25 . Je wilt dit misschien aanpassen op basis van de resultaten bij het testen.

6.

Met het Bovenste Torso-bot geselecteerd, schilder  je de bovenste torso van je model bij de schouder.

7.

Tijdens en na het gewicht schilderen van de onderarm, druk op R  met het bovenarm-bot geselecteerd om de rotatie en flexibiliteit van je invloeden op de bovenste torso te testen.

![](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/skinning-humanoid/Candywrap-Example.png)

Bij het draaien van armen naar hun volledige bewegingsbereik kan er een candy-wrap-effect optreden tussen de schouder en torso waar de skinning volume verliest en niet natuurlijk deformeert. Dit effect is in veel gevallen mogelijk niet te vermijden.

Je kunt doorgaan met het gewicht schilderen van de rest van de ledematen van je model met behulp van deze processen. Wanneer je klaar bent, kun je je geskinnde model [exporteren](/docs/nl-nl/art/modeling/export-requirements)  als een .fbx  met behulp van de exportinstellingen van Blender voor gebruik in Studio. Ter referentie kun je een [Blender-project](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/lola-skinned-s15.blend)  downloaden met het model volledig geskinnd.

Aangezien dit referentiemodel nog geen [binnen- en buitenkooi mesh-gegevens](/docs/nl-nl/avatar/character-bodies/specifications#inner-and-outer-cages)  heeft, kan dit model geen gelaagde accessoires uitrusten.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
