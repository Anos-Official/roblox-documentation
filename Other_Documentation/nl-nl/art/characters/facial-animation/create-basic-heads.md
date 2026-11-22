<!-- Source: https://create.roblox.com/docs/nl-nl/art/characters/facial-animation/create-basic-heads -->

Maak basis dynamische hoofden | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Avataritems

# Maak basis dynamische hoofden

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Deze tutorial behandelt geavanceerde onderwerpen.  Voordat je begint, moet je kennis hebben van modelleren, UV-mapping, rigging, animatie en hoe je een karakter in [Blender](https://www.blender.org)  of [Maya](https://www.autodesk.com/products/maya/overview)  instelt.

Dynamische hoofden zijn karakterhoofden die componenten bevatten waarmee je:

-

Standaard aangepaste gezichtsuitdrukkingen kunt instellen.

-

Gezichtsaccessoires kunt uitrusten, zoals wenkbrauwen en wimpers, die vervormen met je gezichtsuitdrukkingen.

-

Emoties kunt activeren die zowel gezichts- als lichaamsanimaties combineren.

Je kunt een bestaand model maken of aanpassen om een dynamisch hoofd te worden in externe modelleringsoftware, zoals [Blender](https://www.blender.org)  of [Maya](https://www.autodesk.com/products/maya/overview) . Bij het maken van een dynamisch hoofd moet je ervoor zorgen dat je karakterlichaamsmodel aan de volgende vereisten voldoet:

-

Het karakterlichaam moet voldoen aan de [modelleringseisen](#modelleringseisen)  van Roblox en moet geschikte hoofdgeometrie bevatten, zoals ogen, een mond en tanden.

-

Het hoofd van het karakterlichaam moet een [rig](#rig-en-skin-het-hoofd)  of interne gewrichtstructuur bevatten om de verschillende vervormingen van de vertices aan te sturen om gezichtsuitdrukkingen te creëren.

-

Het karakterlichaam moet hun gezichtsposes [opgeslagen hebben in de animatietijdlijn](#pose-de-gewrichten)  en [gemapt zijn op het hoofdmesh](#map-elke-pose) . Typische dynamische hoofden bevatten [50 standaard basisposes](/docs/nl-nl/avatar/dynamic-heads/facs-poses-reference)  die een breed scala aan uitdrukkingen mogelijk maken.

Om je te helpen aan deze vereisten te voldoen, behandelt deze tutorial de processen van het toevoegen van gezichtsgewrichten, het poseren ervan in gezichtsuitdrukkingen en het mappen van 5 basis FACS-poses op een Cubie-referentiekarakter in Blender, evenals hoe je het model kunt exporteren voor import in Studio.

Deze tutorial gebruikt [Blender versie 5.2](https://www.blender.org/download/releases/5-2/) . Als je een andere versie van Blender gebruikt, kunnen er kleine verschillen zijn in de gebruikersinterface en instellingen.

## [Referentiebestanden](#referentiebestanden)[](#referentiebestanden)

De volgende referentiebestanden voor dynamische hoofden bevatten alle controlepunten door deze tutorial:

Het referentie Cubie karaktermodel is alleen voor educatieve doeleinden. Het voldoet niet aan de technische avatar [lichaamspecificaties](/docs/nl-nl/avatar/character-bodies/specifications)  om klaar te zijn voor de Marketplace.

| Referentiebestanden | | Beschrijving |
| --- | --- |
| [Cubie-Model-Only.blend](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-dynamic-heads/reference-files/Cubie-Model-Only.blend) | | Een Blender-projectbestand met een Cubie-karaktermodel met een [standaard R15 rig](/docs/nl-nl/avatar/character-bodies/specifications#standaard-r15-rigs)  zonder gezichtsdata. |
| [Cubie-Eye-Bones-Skinned.blend](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-dynamic-heads/reference-files/Cubie-Eye-Bones-Skinned.blend) | | Een Blender-projectbestand met het voorbeeld Cubie-karaktermodel met geskinte ooggewrichten zonder pose- of mappingdata. |
| [Cubie-Eye-Poses-Mapped.blend](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-dynamic-heads/reference-files/Cubie-Eye-Poses-Mapped.blend) | | Een Blender-projectbestand met het Cubie-karaktermodel met de 5 voorbeeldposes opgeslagen en gemapt. |
| [Cubie-Complete.fbx](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-dynamic-heads/reference-files/Cubie-Complete.fbx) | | Een Cubie-karaktermodel met een volledig gerigged gezicht en meer dan 50 opgeslagen en gemapte poses. Je kunt dit bestand importeren in Studio of openen in je favoriete 3D-modelleringssoftware. |
| [Cubie-Texture_ALB.png](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-dynamic-heads/reference-files/Cubie_Head_ALB.png) | | Een Cubie-textuurafbeeldingsbestand. Nadat je het Cubie-model in Studio hebt geïmporteerd, kun je dit bestand toevoegen als de TextureID  van het hoofdonderdeel. |
| [Cubie-Complete.ma](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-dynamic-heads/reference-files/Cubie-Complete.ma) | | Een Cubie Maya-project dat als aanvullende referentie wordt verstrekt. |

## [Modelleringseisen](#modelleringseisen)[](#modelleringseisen)

Veel karakterlichaamsmodellen die een hoofd met duidelijke gelaatskenmerken bevatten, vereisen kleine modelleringaanpassingen om compatibel te zijn als een dynamisch hoofd. Wanneer je je avatar-karakters modelleert, controleer dan of elk hoofdmesh voldoet aan de avatar [lichaamspecificaties](/docs/nl-nl/avatar/character-bodies/specifications)  voor Studio-import, evenals de volgende vereisten:

-

Gezichtsonderdelen  - Zorg ervoor dat je duidelijke gelaatskenmerken opneemt, zoals ogen, bovenste tanden, onderste tanden en een tong.

-

Lipvertices  - Als je wilt dat je karakter zijn mond gebruikt, scheid dan de lipvertices zodat de mond kan openen.

-

Interne componenten  - Als je karakter interne mondcomponenten heeft, zoals een tong en tanden, modelleer dan een mondzak binnen het hoofdmesh om deze kenmerken te bevatten. Als je karakter oogkassen gebruikt, modelleer dan een vergelijkbare oogzak om deze kenmerken te bevatten.

-

Geen extra data  - Zorg ervoor dat alle kindergezichtsonderdelen van de Head_Geo  geen geschiedenis of bevroren transformaties bevatten.

-

Buitenste kooi  - Zorg ervoor dat het karaktermodel een buitenste kooi heeft om gezichtsaccessoires en gelaagde accessoires te ondersteunen. Voor meer informatie, zie [Lichaamspecificaties - Binnenste en buitenste kooien](/docs/nl-nl/avatar/character-bodies/specifications#inner-and-outer-cages) .

Je kunt de rest van dit proces voor het maken van een hoofd volgen met een gerigged Cubie-karakter dat aan deze modelleringseisen voldoet. Deze versie bevat geen gezichtsrigging of posedata, zodat je het als startpunt voor deze tutorial kunt gebruiken.

## [Rig en skin het hoofd](#rig-en-skin-het-hoofd)[](#rig-en-skin-het-hoofd)

Rigging  is het proces van het verbinden van een mesh met een interne rig, zodat de meshoppervlakken kunnen draaien en bewegen terwijl de gewrichten draaien en bewegen, en skinning  is het proces van het toewijzen van welke delen van het meshoppervlak bewegen en draaien met specifieke gewrichten. Dynamische hoofden vereisen beide processen, zodat de oppervlakken van het hoofdmesh kunnen bewegen met gewrichten om gezichtsuitdrukkingen te creëren.

De volgende instructies richten zich op het riggen en skinen van Cubie's ogen en oogleden, maar je kunt deze technieken toepassen op de rest van de gezichtskenmerken van het karakter die articulatie vereisen, zoals de mond, wangen en kaak van het karakter. Nadat je gewrichten hebt toegevoegd en skindata hebt toegepast, kun je vervolgens controles maken om het poseren efficiënter te maken.

Het rigging- en skinningproces hangt af van het karaktermodel en verschilt tussen tools en 3D-modellers. Het is belangrijk om het volledige bereik van gezichtsposes dat je karakter nodig heeft te plannen om extra aanpassingen aan je hoofddelen later te vermijden.

### [Voeg gewrichten toe](#voeg-gewrichten-toe)[](#voeg-gewrichten-toe)

Elke poseerbare gezichtskenmerk van je hoofd vereist doorgaans minstens één gewricht, maar complexe kenmerken, zoals ogen en mond, kunnen meerdere gewrichten vereisen om bepaalde poses mogelijk te maken. In tegenstelling tot de rest van het [lichaam van het karakter](/docs/nl-nl/avatar/character-bodies/specifications#rigging) , vereist Studio geen specifieke gewrichthiërarchie voor een dynamisch hoofd. Om ervoor te zorgen dat de gezichtsrig goed werkt, moet de rig echter een RootFaceJoint -gewricht en aanvullende gezichtsgewrichten bevatten om de buiging en vervorming van de gezichtgeometrie aan te sturen.

De specifieke hoofdgewrichten die je karakter nodig heeft, zijn afhankelijk van de poses die je voor je karakter bedoelt. De volgende voorbeelden behandelen het proces voor het toevoegen van 1 gewricht voor elk oog en 4 gewrichten voor de oogleden om knipperen, knipogen en kijkrichting mogelijk te maken. Bij het maken van een gezichtsrig, gebruik je waar mogelijk minder dan 50 gezichtsgewrichten en houd je de gewrichten georganiseerd en specifiek voor hun bijbehorende gezichtskenmerken. Over het algemeen kunnen hoge aantallen vertices en gewrichten de prestaties van je game beïnvloeden.

Deze tutorial biedt een [referentie Cubie-model](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-dynamic-heads/reference-files/Cubie-Complete.fbx)  dat een complete rig bevat met 30+ gezichtsgewrichten met skindata. Je kunt dit gebruiken als referentie voor unieke gewrichtplaatsen die niet in deze tutorial worden behandeld, zoals wangen, lippen en kaken.

#### [RootFaceJoint](#rootfacejoint)[](#rootfacejoint)

De RootFaceJoint  is een gewricht dat onder het hoofdgewricht van de [R15 rigging armature](/docs/nl-nl/avatar/character-bodies/specifications#rigging)  is geparent. Dit rootgewricht moet alle andere gezichtsgewrichten parenten. In Blender kun je snel een gewricht toevoegen door een kindgewricht uit het hoofdgewricht te extruderen , en vervolgens de gewrichtnaam als een eigenschap in het Head_Geo -mesh te mappen.

Het RootFaceJoint -object wordt vaak DynamicHead  genoemd in de referentietemplates en voorbeelden, maar je kunt elke naam gebruiken zolang je de [rootjoint mapt](#map-elke-pose)  in aangepaste eigenschappen. Dit stelt Studio in staat om dat gewricht correct te lokaliseren en alle kindergewrichten binnen de [FaceControls](/docs/nl-nl/reference/engine/classes/FaceControls) -instantie te verbergen bij import.

Om een RootFaceJoint -object toe te voegen:

1.

Open in Blender het [gerigged Cubie karakter](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-dynamic-heads/reference-files/Cubie-Model-Only.blend)  project.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-dynamic-heads/Open-Project.png)

2.

Klik op een gewricht om de armature te selecteren, schakel vervolgens over naar de Bewerken -modus.

3.

Klik in de Outliner op het Hoofd -gewricht.

4.

Druk in de viewport op E  en sleep je muis omhoog om een extra kindgewricht uit het Hoofd -gewricht te extruderen.

5.

Terug in de Outliner, hernoem dit gewricht naar DynamicHead . Je zult dit gewricht later bij naam verwijzen in de [mapping](#map-elke-pose)  sectie.

#### [Ogen](#ogen)[](#ogen)

Elk oog vereist één gewricht, hoewel je ervoor kunt kiezen om later een controllergewricht te maken dat beide ogen tegelijk kan aansturen. Om ervoor te zorgen dat je gewrichten symmetrisch zijn gepositioneerd, kun je X-Axis-symmetrie  inschakelen in de rechterbovenhoek van de viewport. Dit verplaatst gewrichten die dezelfde naam delen met tegenhanger-suffixen langs de X-as.

Om gewrichten aan de ogen van het karakter toe te voegen:

1.

Terwijl je nog in de Bewerken -modus bent, navigeer je naar de bovenbalk van de viewport, klik dan op Toevoegen  > Enkel Gewricht . Doe dit twee keer.

2.

Hernoem één gewricht naar LeftEye  en het andere naar RightEye .

3.

Pas de gewrichten aan zodat ze naar voren gericht, horizontaal en rond de iris van de ogen van het karakter zijn:

1.

Schakel in de rechterbovenhoek van de viewport X-Axis-symmetrie  in.

2.

Gebruik de Verplaatsen -tool om het linker- of rechtergewricht in het midden van de ogen van het model te positioneren.

3.

Breid het Item -paneel uit, en met de gewrichten geselecteerd:

1.

Kopieer de Hoofd Y -locatie naar de Staart Y -locatie.

2.

Stel Staart Z  in op 0.2  centimeter om de Staart Z-coördinaten met een offset van 0.2  centimeter van de Hoofd Z-coördinaten in te stellen.

4.

Parent de nieuwe gewrichten aan je RootFaceJoint .

1.

Houd Shift  ingedrukt en klik op zowel de LeftEye  als de RightEye  gewrichten.

2.

Terwijl je Shift  nog steeds ingedrukt houdt, klik op het DynamicHead -gewricht.

3.

Klik met de rechtermuisknop in de viewport en selecteer Parent  > Make  > With Offset  in het contextmenu.

#### [Oogleden](#oogleden)[](#oogleden)

Bij het toevoegen van gewrichten kun je snel gewrichten maken die onder het RootFaceJoint -gewricht zijn geparent door bestaande gezichtsgewrichten te selecteren en te dupliceren. Dit maakt automatisch gewrichten die onder het RootFaceJoint -gewricht zijn geparent.

Om gewrichten aan de oogleden van het karakter toe te voegen:

1.

Terwijl je nog in de Bewerken -modus bent, houd Shift  ingedrukt en klik op zowel de LeftEye  als de RightEye  gewrichten.

2.

Houd Shift  + D  ingedrukt en klik om de gewrichten in dezelfde positie te dupliceren. Doe dit vier keer om in totaal 8 nieuwe gewrichten te maken.

3.

Met X-Axis-symmetrie  nog steeds ingeschakeld, positioneer je elk gewricht in de hoeken van de ogen.

4.

Hernoem in de Outliner alle gewrichten om hun specifieke positie weer te geven met de volgende namen:

-

LeftUpperOuterEyelid

-

RightUpperOuterEyelid

-

LeftLowerOuterEyelid

-

RightLowerOuterEyelid

-

LeftUpperInnerEyelid

-

RightUpperInnerEyelid

-

LeftLowerInnerEyelid

-

RightLowerInnerEyelid

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-dynamic-heads/Eyelid-Naming.png)

### [Skin gewrichten](#skin-gewrichten)[](#skin-gewrichten)

Je kunt skindata toepassen op een karakterrig met verschillende methoden. Het volgende voorbeeld gebruikt Blender's Weight Paint -modus om te schilderen welke vertices een enkel gewricht kan aansturen. Skinning is doorgaans een tijdrovende stap voor complexe karakters en een achtergrond in skinning en gezichtsposeren wordt aanbevolen.

Bij het toepassen van gedetailleerde of gedeelde invloeden voor complexe modellen, is het aan te raden om [Auto Normalize](/docs/nl-nl/art/modeling/skin-a-simple-mesh#auto-normaliseren)  in te schakelen om invloedconflicten tussen gewrichten te voorkomen.

Wanneer je gewrichten aan het karakter parent met Automatische Gewichten , kunnen sommige van je vertices al invloeden hebben. Test altijd je invloeden om ervoor te zorgen dat de invloedstoewijzingen correct zijn.

#### [Ogen](#ogen-1)[](#ogen-1)

Beide ogen in het voorbeeldproject vereisen volledige invloeden op de pupil binnen de ooggeometrie. Afhankelijk van het ontwerp van de ogen, moet je mogelijk invloeden aanpassen om realistische oogposes te creëren.

Om invloed aan je ooggewrichten toe te voegen:

1.

Schakel X-Axis-symmetrie  uit zodat je alleen de LeftEye -gewricht beïnvloedt.

2.

Schakel over naar de Object -modus, klik op een gewricht om de armature te selecteren, houd vervolgens Shift  ingedrukt en klik op het Head_Geo -mesh.

3.

Schakel over naar de Weight Paint -modus, schakel vervolgens in de rechterbovenhoek van de viewport Wireframe -modus in om de vertices beter te visualiseren.

4.

Houd Shift  + Ctrl  ingedrukt en klik op het LeftEye -gewricht om het te selecteren. De naam van het momenteel geselecteerde gewricht wordt linksboven in de viewport weergegeven.

5.

Schilder invloed op de vertices binnen het oog. Zorg ervoor dat de pupillen rood zijn, of volledig beïnvloed door het geselecteerde gewricht.

6.

Schakel over naar de Object -modus, schakel Viewport Shading  in om het mesh beter te visualiseren, klik vervolgens op een gewricht om de armature te selecteren.

7.

Schakel over naar de Pose -modus en test de invloeden van het ooggewricht door het gewricht vast te pakken en te verplaatsen. Het mesh volgt op de juiste manier.

8.

Herhaal deze stappen voor het RightEye -gewricht.

#### [Oogleden](#oogleden-1)[](#oogleden-1)

Ooglidgewrichten vereisen hun eigen aparte invloeden. Terwijl de voorbeeldposes alleen de bovenste oogleden manipuleren, is het belangrijk om de onderste hoeken van de oogleden te kunnen aansturen voor andere poses, zoals LeftCheekRaiser  en RightCheekRaiser .

Om invloed aan de ooglidgewrichten toe te voegen:

1.

Schakel over naar de Object -modus, klik op een gewricht om de armature te selecteren, houd vervolgens Shift  ingedrukt en klik op het Head_Geo -mesh.

2.

Schakel over naar de Weight Paint -modus, schakel vervolgens in de rechterbovenhoek van de viewport Wireframe -modus in om de vertices beter te visualiseren.

3.

Houd Shift  + Ctrl  ingedrukt en klik op het LeftUpperOuterEyelid -gewricht om het te selecteren.

4.

Schilder indien nodig invloeden op de dichtstbijzijnde vertices bij het gewricht.

5.

Herhaal dit proces voor elk ooglidgewricht.

6.

Schakel over naar de Object -modus, schakel Viewport Shading  in om het mesh beter te visualiseren, klik vervolgens op een gewricht om de armature te selecteren.

7.

Schakel over naar de Pose -modus en test de invloeden van het ooggewricht door het gewricht vast te pakken en te verplaatsen. Het mesh volgt op de juiste manier.

Het [Cubie-Eye-Bones-Skinned.blend](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-dynamic-heads/reference-files/Cubie-Eye-Bones-Skinned.blend)  projectbestand is beschikbaar als je alle werkzaamheden in de tutorial tot dit controlepunt wilt refereren.

### [Maak controles](#maak-controles)[](#maak-controles)

Aangezien het maken van hoofden vereist dat je verschillende poses achtereenvolgens opslaat, kunnen controles, hoewel niet vereist, je helpen om je gewrichten snel en effectief te poseren. Je kunt controles maken door externe controllergewrichten toe te voegen die de interne aansturen, waardoor het gemakkelijker wordt om gewrichten te benaderen, te poseren of terug te zetten naar een neutrale transformatie.

Je kunt controles op veel verschillende manieren maken. Het volgende voorbeeld gebruikt Bone Constraints  en eenvoudige geometrische vormen die zijn opgenomen in het referentie Blender-project om snel gemakkelijk toegankelijke controllergewrichten voor de gezichtsgewrichten van het karakter op te zetten. Voor meer informatie over rigging en constraints, zie de documentatie van Blender voor details over [karakter rigging](https://www.youtube.com/watch?v=-gIL6VZ-bkE)  en [object constraints](https://www.youtube.com/watch?v=fx33sPEAZEk) .

Sommige gezichtskenmerken, zoals de lippen, kaken en tong van een karakter, hebben mogelijk een enkel controllergewricht nodig dat meerdere gezichtsgewrichten tegelijk aanstuurt. Voor een voorbeeld van dit type implementatie, zie het [Cubie-Complete.fbx](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-dynamic-heads/reference-files/Cubie-Complete.fbx)  referentiebestand.

Om te beginnen met het maken van gezichtsgewrichtcontroles:

1.

Schakel over naar de Object -modus en selecteer de armature.

2.

Houd Shift  + D  ingedrukt om de armature te dupliceren, hernoem de duplicaat naar Controller .

3.

Schakel over naar de Bewerken -modus, selecteer alle niet-gezichtsgewrichten, klik met de rechtermuisknop in de viewport en selecteer Verwijder Geselecteerde Gewrichten  in het contextmenu.

4.

Batch hernoem de gewrichten om _Con  als suffix toe te voegen om ze als controllergewrichten aan te duiden:

1.

Houd Shift  ingedrukt en klik op alle controllergewrichten in de Outliner.

2.

Navigeer naar Bewerken  > Batch Hernoemen . Het Batch Hernoemen -dialoogvenster wordt weergegeven.

3.

In het dialoogvenster:

1.

Klik op de Geselecteerde  knop.

2.

Stel het dropdownmenu in op Gewrichten .

3.

Stel Type  in op Stel Naam In .

4.

Stel Methode  in op Suffix .

5.

Stel Naam  in op _Con .

6.

Klik op de OK -knop.

5.

Stel gewrichtsconstraints in voor elk gezichtsgewricht dat een controller vereist.

1.

Schakel over naar de Object -modus, selecteer de originele armature.

2.

Schakel over naar de Pose -modus, klik op het LeftEye -gewricht en navigeer naar het tabblad Bone Constraints  in de Properties Editor.

3.

Klik op het dropdownmenu Bone Constraint , voeg Kopieer Locatie  en Kopieer Rotatie  toe, en stel in elke constraint:

1.

Stel de Doel  in op Controller .

2.

Stel Gewricht  in op LeftEye_Con .

4.

In de Kopieer Rotatie -constraint:

1.

Schakel in As  X , Y  en Z  uit.

2.

Schakel in Inverted Axis  X , Y  en Z  in.

3.

Stel Mix  in op Offset (Legacy) .

5.

Herhaal dit constraintproces voor elk gezichtsgewricht dat een controller vereist.

6.

OPTIONEEL

 Maak aangepaste gewrichtsvormen voor gemakkelijker toegang tot de controlegewrichten.

1.

Schakel over naar de Object -modus, selecteer het Controller -armatureobject.

2.

Schakel over naar de Pose -modus, selecteer vervolgens LeftEye_Con .

3.

Navigeer naar het tabblad Bone Properties  in de Properties Editor > Viewport Display  > Custom Shape , stel vervolgens Custom Object  in op WDG_Eye.001 . In het referentieproject delen de vormobjecten vergelijkbare namen met de gezichtsgewrichten.

4.

Stel de X -rotatie in op -90 , evenals eventuele extra schaling indien nodig.

5.

Herhaal dit proces voor al je controllergewrichten. Je kunt de originele gezichtsgewrichten op dit punt verbergen.

7.

OPTIONEEL

 Pas kleurthema's toe op je controllergewrichten, zodat je de gezichtsgewrichten gemakkelijker kunt visualiseren.

1.

Blijf in de Pose -modus, navigeer naar de Outliner en selecteer LeftEye_Con .

2.

Navigeer naar het tabblad Bone Properties  in de Properties Editor > Viewport Display  > Bone Color , en selecteer een themakleurset.

3.

Herhaal dit proces voor elk controllergewricht, gebruik dezelfde kleur voor de volgende:

-

Eén voor LeftEye  en RightEye .

-

Eén voor LeftUpperOuterEyelid  en LeftLowerOuterEyelid .

-

Eén voor LeftUpperInnerEyelid  en LeftLowerInnerEyelid .

-

Eén voor RightUpperInnerEyelid  en RightLowerInnerEyelid .

-

Eén voor RightUpperOuterEyelid  en RightLowerOuterEyelid .

8.

Test je controllers in de Pose -modus.

## [Pose de gewrichten](#pose-de-gewrichten)[](#pose-de-gewrichten)

Poseren  is het proces van het manipuleren van de gewrichten van je hoofdmesh in een specifieke positie per animatieframe. Nadat het hoofd van het model is gerigged, kun je beginnen met het proces van het opslaan van poses in de tijdlijn. Deze gegevens stellen Studio in staat om elke gezichtsbeweging te benaderen en gezichtsposes te animeren of te mengen om dynamische uitdrukkingen te creëren.

Bij het poseren van de gewrichten van het hoofdmesh van je karakter naar nieuwe posities, volg je het [Facial Action Coding System](/docs/nl-nl/avatar/dynamic-heads/facs-poses-reference)  (FACS) als referentie voor je gezichtsuitdrukkingsposes. FACS is een uitgebreid, anatomisch gebaseerd systeem voor het beschrijven van alle visueel waarneembare gezichtsbewegingen, en het maakt het mogelijk dat alle gezichtsanimaties deelbaar zijn tussen karakters. Dit betekent dat zodra je een gezichtsanimatie hebt gemaakt, je deze kunt hergebruiken voor elk karakter met een [animeerbaar hoofd](/docs/nl-nl/avatar/dynamic-heads)  met een [FaceControls](/docs/nl-nl/reference/engine/classes/FaceControls) -instantie.

Er zijn [50 basisposes](/docs/nl-nl/avatar/dynamic-heads/facs-poses-reference)  die je in Roblox kunt gebruiken om een breed scala aan gezichts-emoties voor je karakters weer te geven, maar slechts een specifieke  [17 poses](/docs/nl-nl/avatar/dynamic-heads/specifications#facs-poses)  zijn vereist om een dynamisch hoofd op de Marketplace te verkopen. Wanneer je beslist welke poses je nodig hebt, onthoud dan dat de namen van FACS-poses altijd zijn gebaseerd op de oriëntatie van het karakter, niet de camera. Bijvoorbeeld, LeftEyeClosed  sluit het linker oog van het karakter, dat zich rechts van het camerabeeld bevindt.

Je hebt mogelijk niet elke basispose voor je karakter nodig. Bijvoorbeeld, een eenvoudige robot die zijn mond opent en knippert, kan alleen JawDrop , LeftEyeClosed  en RightEyeClosed  hebben. Het wordt aanbevolen om de basisposes die je van plan bent te gebruiken met je hoofd in alfabetische volgorde op te slaan, en gebruik daarna eventuele frames voor [combinatieposes](#combinatieposes) .

Elk frame binnen de animatietijdlijn van je modelleringssoftware kan één unieke FACS-pose bevatten, dus wanneer je meerdere FACS-poses wilt maken, moet je elke FACS-pose opslaan op een ander frame. Je moet ook een frame opnemen waarop je karakter een neutrale gezichtsuitdrukking heeft met de gezichtscontrollers en gewrichten ingesteld op hun standaardwaarden. Dit zorgt ervoor dat Studio de gewrichtspositieverschillen tussen de neutrale uitdrukking van je karakter en elke FACS-pose kan berekenen.

Om deze reden is het belangrijk om Frame 0 in te stellen als de neutrale uitdrukking van je karakter, en FACS-poses te beginnen met Frame 1. De volgende afbeelding is een voorbeeld van de animatietijdlijn van Blender met 5 frames. Frame 0 heeft de neutrale uitdrukking van het karakter, en frames 1-4 hebben FACS-posegegevens.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-dynamic-heads/Animation-Timeline.png)

De volgende stappen schetsen het proces van het poseren van 5 poses met de gezichtsgewrichten die in onze referentie zijn gemaakt, maar je kunt deze stappen toepassen voor eventuele extra poses voor een expressiever hoofd. Om je gezichtsgewrichten in Blender te poseren:

1.

Zorg ervoor dat de afspeelkop van de animatietijdlijn is ingesteld op het juiste frame.

1.

Als je de Neutrale pose  van het karakter instelt, stel deze dan in op frame 0 .

2.

Als je EyesLookLeft  poseert, stel deze dan in op frame 1 .

3.

Als je EyesLookRight  poseert, stel deze dan in op frame 2 .

4.

Als je LeftEyeClosed  poseert, stel deze dan in op frame 3.

5.

Als je RightEyeClosed  poseert, stel deze dan in op frame 4 .

2.

In de Pose -modus, stel de pose in op de maximale positie die je pose realistisch wilt gebruiken:

1.

Als je de Neutrale  pose van het karakter instelt, stel dan de gezichtscontrollers en gewrichten in op hun standaardwaarden,

2.

Als je EyesLookLeft  poseert, selecteer dan beide oogcontrollergewrichten en sleep de ogen naar links van het karakter.

3.

Als je EyesLookRight  poseert, selecteer dan beide oogcontrollergewrichten en sleep de ogen naar rechts van het karakter.

4.

Als je LeftEyeClosed  poseert, selecteer dan beide oogcontrollergewrichten en sleep de linker oogleden naar beneden om de onderste oogleden te ontmoeten.

5.

Als je RightEyeClosed  poseert, selecteer dan beide oogcontrollergewrichten en sleep de rechter oogleden naar beneden om de onderste oogleden te ontmoeten.

3.

Druk in de viewport op A  om alle gewrichten te selecteren.

4.

Klik met de rechtermuisknop in de viewport en selecteer Voeg Sleutelframe In met Sleutelset  > Locatie en Rotatie . Dit zorgt ervoor dat elk frame de positionele en roterende informatie voor alle gewrichten bevat.

Wanneer alle poses zijn opgeslagen in je tijdlijn, stel je het Begin en Einde van de animatietijdlijn in om het aantal frames met opgeslagen poses weer te geven. Stel altijd Begin  in op 0  en, in dit specifieke voorbeeld, kun je het Einde  instellen op 4  als je alleen de 4 niet-neutrale voorbeeldposes aan het mappen bent.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-dynamic-heads/Animation-Frame-Range.png)

### [Combinatieposes](#combinatieposes)[](#combinatieposes)

Je kunt 2-3 basis FACS-poses combineren in een enkel animatieframe om complexe gezichtsuitdrukkingen weer te geven. Wanneer je echter FACS-poses combineert die dezelfde gezichtsregio's aansturen, kunnen de gezichtskenmerken ofwel botsen of de vorm van het karakter vervormen.

Bijvoorbeeld, zowel LeftEyeClosed  als LeftCheekRaiser  sturen beweging aan rond het linker oog van het karakter: LeftEyeClosed  sluit het oog, en LeftCheekRaiser  tilt de wang omhoog en duwt het onderste ooglid omhoog, wat een knijpachtige effect veroorzaakt. Wanneer je beide poses combineert met een of meer op 100% van hun waarden, botsen het onderste ooglid en het bovenste ooglid:

Beide FACS-poses verlichten gelijktijdig naar 100% van hun standaardwaarden.

LeftEyeClosed verlicht naar 100% van zijn standaardwaarde, en LeftCheekRaiser begint op 100%.

LeftCheekRaiser verlicht naar 100% van zijn standaardwaarde, en LeftEyeClosed begint op 100%.

Een combinatiepose , of correctieve , is de combinatie van 2-3 FACS-poses die dezelfde gezichtskenmerken in een enkel animatieframe aansturen met een correctief verschil van 100% van hun standaardwaarden . Door een combinatiepose te definiëren en te mappen naar je hoofd, kun je corrigeren hoe je wilt dat de twee of meer FACS-poses combineren. Bijvoorbeeld, als je een correctieve toevoegt voor elk van de vorige gebruiksgevallen, maken de onderste en bovenste oogleden contact met elkaar zonder te botsen:

Met een correctieve pose verlichten beide FACS-poses gelijktijdig naar 100% van hun standaardwaarden.

LeftEyeClosed verlicht naar 100% van zijn standaardwaarde, en LeftCheekRaiser begint op 100%.

LeftCheekRaiser verlicht naar 100% van zijn standaardwaarde, en LeftEyeClosed begint op 100%.

Bij import berekent Studio het correctieve verschil voor combinatieposes in de [FaceControls](/docs/nl-nl/reference/engine/classes/FaceControls) -instantie van het hoofd, en de [FaceControls](/docs/nl-nl/reference/engine/classes/FaceControls) -instantie corrigeert de basisposewaarden terwijl ze combineren in de [Animatie-editor](/docs/nl-nl/animation/editor) .

## [Map elke pose](#map-elke-pose)[](#map-elke-pose)

Als je je poses niet mapt, lege strings achterlaat, of probeert het hoofd in Studio te importeren met meerdere frames per FACS-posesnaam, zal het hoofd falen in het [importproces](/docs/nl-nl/avatar/dynamic-heads/test) .

Nadat je elke FACS-pose die je karakter nodig heeft hebt geposeerd, moet je elke animatieframe die je poseert  mappen naar de bijbehorende FACS-basis- of combinatieposenaam. Mappen slaat de gewrichtsposities en vertalingen op binnen de hoofd [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) , en wanneer je begint met het animeren van je hoofd binnen de Animatie-editor , gebruikt de [FaceControls](/docs/nl-nl/reference/engine/classes/FaceControls) -instantie deze opgeslagen gegevens om de gezichtskenmerken van je karakter naar de toepasselijke FACS-pose te transformeren.

Naast je gezichtsposes, moet je de RootFaceJoint  mappen zodat Studio het correct kan lokaliseren en alle kindergewrichten binnen de [FaceControls](/docs/nl-nl/reference/engine/classes/FaceControls) -instantie kan verbergen bij import. Vergeet niet, slechts een specifieke  [17 poses](/docs/nl-nl/avatar/dynamic-heads/specifications#facs-poses)  zijn vereist om een dynamisch hoofd op de Marketplace te verkopen.

Om je opgeslagen poses en de RootFaceJoint  te mappen:

1.

Schakel over naar de Object -modus, selecteer vervolgens Head_Geo .

2.

In het tabblad Object Properties  van de Properties Editor, navigeer naar de sectie Aangepaste Eigenschappen , klik vervolgens op de Nieuwe  knop. Een nieuwe aangepaste eigenschap verschijnt onder de Nieuwe  knop.

Gebruik je Maya?

Als je Maya gebruikt, kun je de RootFaceJoint  en gezichtsposedata mappen met de Extra Attributen  in een vergelijkbaar formaat als Blender's Aangepaste Eigenschappen . Om attributen toe te voegen:

1.

Selecteer het Head_Geo -object en navigeer naar de Attribuuteditor.

2.

Onder het dropdownmenu Attributen , selecteer Voeg Attributen Toe... .

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-dynamic-heads/Mapping-New-Button.png)

3.

Klik rechts van de nieuwe aangepaste eigenschap op het Tandwielpictogram . Het pop-upvenster Eigenschap Bewerken  verschijnt.

4.

In het pop-upvenster:

1.

Klik op het dropdownmenu Type , selecteer vervolgens String .

2.

In het veld Eigenschapsnaam :

-

Als je de RootFaceJoint  mapt, voer dan RootFaceJoint  in.

-

Als je een pose mapt, voer dan het frame nummer  in dat je mapt, bijvoorbeeld Frame0 .

3.

Laat de velden Standaardwaarde  en Beschrijving  leeg, klik vervolgens op de OK -knop. De nieuwe aangepaste eigenschap wordt bijgewerkt met je nieuwe eigenschapsnaam.

5.

In het veld rechts van de naam van de aangepaste eigenschap:

-

Als je de RootFaceJoint  mapt, voer dan DynamicHead  in.

-

Als je een basispose mapt, voer dan de bijbehorende [FACS-basispose](/docs/nl-nl/avatar/dynamic-heads/facs-poses-reference)  of combinatieposenaam exact in zoals deze is gespeld.

-

Als je een combinatiepose mapt, voer dan elke basispose die je combineert in, gescheiden door een onderstreping, zoals Funneler_JawDrop_Pucker .

6.

Druk op Enter .

Terwijl je dit proces herhaalt, wordt elke extra aangepaste eigenschap die je maakt weergegeven in de sectie Aangepaste Eigenschappen  van het tabblad Object Properties  van de Properties Editor.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-dynamic-heads/Custom-Properties-Example.png)

Het [Cubie-Eye-Poses-Mapped.blend](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-dynamic-heads/reference-files/Cubie-Eye-Poses-Mapped.blend)  projectbestand is beschikbaar als je alle werkzaamheden in de tutorial tot dit controlepunt wilt refereren. Zorg ervoor dat je de Animatie-offset-eigenschap instelt op 0  wanneer je het karakter importeert, zodat het Frame 0 op de tijdlijn omvat.

![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-dynamic-heads/Animation-Offset-Importing.png)

## [Exporteer je karakter](#exporteer-je-karakter)[](#exporteer-je-karakter)

Nadat je het hoofd van je karakter hebt geposeerd en gemapt, kun je het karaktermodel exporteren als een .fbx  om in Studio te importeren, zodat je toegang hebt tot de 4 oogposes met de [FaceControls](/docs/nl-nl/reference/engine/classes/FaceControls) -instantie in Studio. Je kunt ook het volledig geconfigureerde Cubie-hoofd .fbx  refereren om toegang te krijgen tot alle 50+ basisposes.

Om het basis hoofdmodel als een .fbx  te exporteren:

1.

Maak in de Outliner alle objecten zichtbaar, maak ze selecteerbaar en selecteer vervolgens alles in je project onder de Objecten -collectie.

2.

Klik in de bovenbalk op Bestand  > Exporteren  > FBX (.fbx) . Het venster Blender-bestandsweergave  verschijnt.

3.

In de sectie Inbegrepen ,

1.

Schakel Beperk tot  > Geselecteerde Objecten  in. Merk op dat deze stap optioneel is als je geen extra collecties in je Blender-project hebt.

2.

Schakel Aangepaste Eigenschappen  in.

4.

In de sectie Armature  schakel je Voeg Bladgewrichten toe  uit.

5.

Schakel Animatie  in en breid deze uit, schakel vervolgens NLA-strips , Alle Acties  en Forceer Start/Einde Sleutelframes  uit.

6.

Klik op de knop Exporteer FBX  en sla de .fbx  op in de directory van jouw keuze.

Op dit punt kun je nu de .fbx  in Studio importeren als een karakter met een ondersteunde animeerbare hoofd. Voor instructies voor modelimport en gebruik, zie [Test hoofden in Studio](/docs/nl-nl/avatar/dynamic-heads/test) .

Bij het importeren van Cubie in Studio, zorg ervoor dat je ook de hoofdtextuur opslaat [Cubie-Texture_ALB.png](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-dynamic-heads/reference-files/Cubie_Head_ALB.png)  die je kunt toepassen op het hoofdmesh van het geïmporteerde karakter als een TextureID.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
