<!-- Source: https://create.roblox.com/docs/nl-nl/art/characters/export-avatar-animations-from-maya -->

Exporteer avataranimaties vanuit Maya | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Assets](/docs/nl-nl/assets)
4. /
5. Animatie

# Exporteer avataranimaties vanuit Maya

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Avataranimaties  zijn animaties die je kunt maken en toewijzen om af te spelen voor elke avataractie, zoals lopen, zwemmen of dansen. Naast het gebruik van de [Animatie-editor](/docs/nl-nl/animation/editor)  of [Animatie-opname](/docs/nl-nl/animation/capture)  tools binnen Studio, kun je avataranimaties maken met behulp van derde-partij modellering en animatietools zoals [Maya](https://www.autodesk.com/products/maya/overview) , en vervolgens je avataranimaties rechtstreeks in Studio importeren om toe te passen op elke avatar met Roblox. Door deze gids te gebruiken als een checklist van de specifieke instellingen waaraan je rig en animatie moeten voldoen voor het exportproces, kun je ervoor zorgen dat je animaties succesvol worden geïmporteerd.

![Een humanoïde mannequin in Maya met IK-controles.](https://prod.docsiteassets.roblox.com/assets/animation/exporting-avatar-animations-from-maya/Overview-Mannequin.jpg) Mannequin referentie

Voorbeeld loopanimatie

Deze gids maakt gebruik van een downloadbaar [R15-Mannequin-Rig.ma](https://prod.docsiteassets.roblox.com/assets/animation/exporting-avatar-animations-from-maya/R15-Mannequin-Rig.ma)  bestand dat een mannequin bevat met een [standaard R15 rig](/docs/nl-nl/avatar/character-bodies/specifications#standaard-r15-rigs)  die je kunt gebruiken als referentie om animaties te maken en te exporteren. Als je ervoor kiest om te animeren op je eigen standaard R15 rig, gelden dezelfde rigconfiguratie en exportinstellingen.

## [Configureer de rig](#configureer-de-rig)[](#configureer-de-rig)

Voordat je je avataranimatie vanuit Maya exporteert, moet je je rig configureren zodat deze compatibel is met de importvereisten van Studio, inclusief ervoor zorgen dat de rig een specifieke hiërarchie en naamgevingsconventies volgt, zodat Studio het bestand als een avataranimatie kan herkennen, en dat het translatiekanaal van de rig is gedempt, zodat de rootnode niet beweegt met de animatie.

### [Hiërarchie en naamgevingsconventies](#hiërarchie-en-naamgevingsconventies)[](#hiërarchie-en-naamgevingsconventies)

Studio vereist een specifieke hiërarchie en naamgevingsconventies voor de interne gewrichtenstructuur van een humanoïde rig, zodat het kan herkennen wat je importeert als een avataranimatie. Als je de downloadbare standaard R15 rig niet gebruikt om je animaties te maken, zorg er dan voor dat je rig de volgende gewrichtenhiërarchie en naamgevingsconventie exact volgt:

-

Root

-

HumanoidRootPart

-

LowerTorso

-

UpperTorso

-

Head (die de basis van de nek vertegenwoordigt)

-

LeftUpperArm

-

LeftLowerArm

-

LeftHand

-

RightUpperArm

-

RightLowerArm

-

RightHand

-

LeftUpperLeg

-

LeftLowerLeg

-

LeftFoot

-

RightUpperLeg

-

RightLowerLeg

-

RightFoot

### [Dempen van het translatiekanaal](#dempen-van-het-translatiekanaal)[](#dempen-van-het-translatiekanaal)

Roblox avataranimaties kunnen een karakter niet verplaatsen wanneer ze worden afgespeeld; in plaats daarvan animeren avataranimaties rigs op hun wereldpositie. Als je avataranimatie een locomotietype animatie is waarbij de rootnode in de ruimte beweegt, zoals een karakter dat vooruit beweegt terwijl hun loopanimatie wordt afgespeeld, moet je het translatiekanaal van de rig dempen zodat de animatie wordt afgespeeld zonder de rig te verplaatsen bij export.

Om het translatiekanaal te dempen:

1.

Open de Graph Editor .

1.

Klik in de menubalk op Windows . Een contextmenu wordt weergegeven.

2.

Beweeg de muis over Workspaces  en klik vervolgens op Animation . De Graph Editor  wordt weergegeven.

 ![Een close-up van het Windows dropdownmenu in Maya. Het menu-item Workspaces is gemarkeerd, evenals het submenu Animation.](https://prod.docsiteassets.roblox.com/assets/animation/exporting-avatar-animations-from-maya/Opening-GraphEditor-and-TimeSlider.jpg)

2.

Verplaats de Tijdmarker  naar frame 0.

 ![Een close-up van de Graph Editor in Maya. De Tijdmarker voor de rechterhand van een karakter staat op frame 0 en is gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/animation/exporting-avatar-animations-from-maya/Time-Marker.jpg)

3.

Selecteer in de Outliner  de rootnode. Als je het referentiebestand gebruikt, is dit TSM3_root .

4.

Klik met de rechtermuisknop op de waarde Translate Z  in de Channel Box . Een contextmenu wordt weergegeven.

5.

Selecteer Mute Selected . De kleur van het kanaalvak van de waarde Translate Z verandert in oranje om te bevestigen dat het is gedempt.

![Een close-up van de Channel Box in Maya. Het menu-item Mute Selected in het contextmenu van stap 4 is gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/animation/exporting-avatar-animations-from-maya/Mute-Selected.jpg)

![Een close-up van de Channel Box in Maya. De kleur van het kanaalvak van de eigenschap Translate Z is oranje om aan te geven dat deze is gedempt. De rest van de waarden zijn in cyaanblauw om aan te geven dat ze ongedempt blijven.](https://prod.docsiteassets.roblox.com/assets/animation/exporting-avatar-animations-from-maya/Muted-TranslateZ.jpg)

Wanneer je de animatie afspeelt, beweegt de rootnode van het karakter niet meer in de ruimte, en het karakter animeert ter plaatse bij de oorsprong van de scène.

## [Exporteer de animatie](#exporteer-de-animatie)[](#exporteer-de-animatie)

Nu je rig ter plaatse animeert en een hiërarchie en naamgevingsgegevens heeft die compatibel zijn met Studio, kun je de animatie exporteren in een .fbx  formaat. Maya laadt deze mogelijkheid niet standaard, dus je moet een FBX-plug-in inschakelen om de extra instellingen te verkrijgen die nodig zijn om het bestand in een formaat te exporteren dat Studio kan herkennen.

Om je avataranimatie vanuit Maya te exporteren:

1.

Installeer de FBX-plug-in.

1.

Klik in de menubalk op Windows . Een contextmenu wordt weergegeven.

2.

Beweeg de muis over Instellingen/Voorkeuren  en klik vervolgens op Plug-in Manager . Het venster Plug-in Manager  wordt weergegeven.

 ![Een close-up van het Windows dropdownmenu in Maya. Het menu-item Instellingen/Voorkeuren is gemarkeerd, evenals het submenu Plug-in Manager.](https://prod.docsiteassets.roblox.com/assets/animation/exporting-avatar-animations-from-maya/Plugin-Manager.jpg)

3.

Voer in het zoekveld fbxmaya  in. De fbxmaya.mll  plug-in wordt weergegeven.

4.

Schakel de opties Loaded  en Auto load  in.

 ![De Plug-in Manager met een close-up van het fbxmaya-bestand. De instellingen Loaded en Auto load zijn gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/animation/exporting-avatar-animations-from-maya/Loaded-and-AutoLoad-Radio-Buttons.jpg)

2.

Klik in de menubalk op Bestand . Een contextmenu wordt weergegeven.

3.

Selecteer Exporteer Alles . Het venster Exporteer Alles  wordt weergegeven.

 ![Een close-up van het Bestands dropdownmenu in Maya. Het menu-item Exporteer Alles is gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/animation/exporting-avatar-animations-from-maya/Export-All.png)

4.

Onderaan het venster,

1.

Voer in het veld Bestandsnaam  een naam in voor je avataranimatie.

2.

Klik op het dropdownmenu Bestanden van type , en selecteer FBX-export . Het Opties-paneel  werkt zijn instellingen bij.

5.

Klik in het Opties -paneel op het dropdownmenu Animatie  voor aanvullende animatie-instellingen, en in de sectie Bake Animation ,

1.

Schakel Bake Animation  in.

2.

Controleer of de velden Start  en Einde  overeenkomen met de frames die je wilt exporteren voor je animatielus.

3.

Stel Stap  in op 1 .

 ![Een close-up van het Opties-paneel. De instellingen voor Bake Animation zijn gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/animation/exporting-avatar-animations-from-maya/Bake-Animation.jpg)

6.

Klik op het dropdownmenu Geavanceerde opties  voor aanvullende exportinstellingen, en in de sectie FBX-bestandsformaat ,

1.

Stel Type  in op Binaire .

2.

Stel indien nodig Versie  in op FBX 2020 .

 ![Een close-up van het Opties-paneel. De instellingen voor FBX-bestandsformaat zijn gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/animation/exporting-avatar-animations-from-maya/FBX-File-Format.jpg)

7.

Klik rechtsonder op de knop Exporteer Alles . Na een moment verschijnt het avataranimatie .fbx  bestand in je bestandsbrowser.

## [Test de animatie in Studio](#test-de-animatie-in-studio)[](#test-de-animatie-in-studio)

Zodra je je avataranimatie .fbx  bestand hebt, kun je deze testen binnen Studio om ervoor te zorgen dat de animatie zonder fouten wordt afgespeeld.

Om de animatie in Studio te testen:

1.

Open een vooraf gebouwde karakter rig.

1.

Klik op het Avatar  tabblad in de werkbalk en klik op Karakter .

2.

Selecteer een rig die je wilt gebruiken als test. De rig wordt weergegeven binnen de viewport.

2.

Verbind de rig met de Animatie-editor .

1.

Klik op het Avatar  tabblad in de werkbalk en klik op Clip Editor . Het [Animatie-editor](/docs/nl-nl/animation/editor)  venster wordt weergegeven.

2.

Klik in de viewport op je rig. Een dialoogvenster wordt weergegeven in de editor.

3.

Voer in het veld Animatienaam  een nieuwe animatienaam in en klik vervolgens op de knop Aanmaken . Het editorvenster toont de media- en afspeelbesturingselementen, tijdlijn en tracklijst.

3.

Importeer je avataranimatie in de rig.

1.

Navigeer naar de Media- en afspeelbesturingselementen  en klik op de ⋯  knop. Een contextmenu wordt weergegeven.

2.

Beweeg de muis over Importeren  en selecteer vervolgens Van FBX-animatie . Een bestandsbrowser wordt weergegeven.

 ![Een close-up van het Animatie-editor venster. Het ellips contextmenu wordt weergegeven, en het submenu-item Van FBX-animatie is gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/animation/exporting-avatar-animations-from-maya/Importing-From-FBX-Animation.jpg)

3.

Selecteer de FBX-animatie die je zojuist vanuit Maya hebt geëxporteerd en klik op Openen . De keyframes van de animatie worden geladen in de Animatie-editor .

4.

Navigeer naar de Media- en afspeelbesturingselementen  en klik op de Afspelen-knop  om de avataranimatie af te spelen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
