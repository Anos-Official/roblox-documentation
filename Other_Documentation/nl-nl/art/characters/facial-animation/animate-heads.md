<!-- Source: https://create.roblox.com/docs/nl-nl/art/characters/facial-animation/animate-heads -->

Hoofden animeren | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Assets](/docs/nl-nl/assets)
4. /
5. Animatie

# Hoofden animeren

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Als je snel de hoofdanimatie van een karakter wilt testen, gebruik dan de [Avatar Setup-tool](/docs/nl-nl/avatar-setup)  om je karakter te laden en gebruik de presets om verschillende gezichtsanimaties en hoofdaccessoires te bekijken.

Je kunt de [Animatie-editor](/docs/nl-nl/animation/editor)  gebruiken om ondersteunde hoofden op de volgende manieren te animeren:

-

Je kunt handmatig waarden instellen voor elke gezichtspositie op afzonderlijke [animatietracks](#gebruik-animatietracks) .

-

Je kunt de [Face Animation Editor](#gebruik-de-face-animation-editor)  gebruiken om toegang te krijgen tot gezichtsregelaars waarmee je snel unieke uitdrukkingen op de tijdlijn kunt maken en opslaan.

-

Je kunt de [Animatie-opname voor gezichten](/docs/nl-nl/animation/capture#gezicht)  extensie gebruiken om automatisch gezichtsbewegingen te volgen en op te nemen met een webcam die je beweging omzet in keyframes op de tijdlijn.

Bij alle methoden resulteert het creëren en combineren van meerdere gezichtsuitdrukkingen over een bepaalde tijd in een gezichtsanimatie. Aangezien je geen gezichtsanimaties kunt importeren, zijn deze methoden de enige manieren om ze te creëren en te gebruiken.

Nadat je een hoofd hebt gemaakt en gepubliceerd dat gezichtsanimatie ondersteunt naar Roblox, kun je de animatie vanuit een script afspelen of de standaardanimatie van een karakter vervangen door je nieuwe animatie. Deze animaties kunnen je karakters levendiger en expressiever maken, zoals het spelen van een gekke uitdrukking wanneer een karakter loopt, of een geïrriteerde uitdrukking wanneer een karakter stilzit.

 ![Een weergave van Studio waar de Face Animation Editor, Animatie-editor en viewport zichtbaar zijn. De viewport toont een close-up van een blokachtige mannelijke avatar die met zijn linkeroog knippert.](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/animating-dynamic-heads/Overview.png)

## [Animaties maken](#animaties-maken)[](#animaties-maken)

Nadat je de Animatie-editor  hebt [geopend](/docs/nl-nl/animation/editor#open-the-animation-editor)  en het karaktermodel met een hoofd hebt geselecteerd waarvoor je een animatie wilt maken, kun je een hoofdanimatie maken door animatietracks of de Face Animation Editor  te gebruiken.

Voor details over het gebruik van Animatie-opname om gezichtsbewegingen als keyframes vast te leggen, zie [Animatie-opname - Gezicht](/docs/nl-nl/animation/capture#gezicht) .

### [Gebruik animatietracks](#gebruik-animatietracks)[](#gebruik-animatietracks)

Vergelijkbaar met het invoegen van andere objecten zoals [MeshParts](/docs/nl-nl/reference/engine/classes/MeshPart)  of [Bones](/docs/nl-nl/reference/engine/classes/Bone)  als animatietracks, kun je handmatig één FACS-waarde tegelijk aan de tracklijst toevoegen om een enkel lichaamsdeel te manipuleren, zoals de ogen, kaak of tong van het karakter. De [Animatie-editor](/docs/nl-nl/animation/editor)  vertegenwoordigt FACS-waarden als een percentage tussen 0 en 1, en deze waarden zijn direct gekoppeld aan [FaceControls](/docs/nl-nl/reference/engine/classes/FaceControls) -waarden. Hoewel dit proces nauwkeurige controle over individuele waarden biedt, verbetert de [Face Animation Editor](#gebruik-de-face-animation-editor)  deze workflow en laat je snel waarden voor meerdere gezichtskenmerken tegelijk op de animatietijdlijn wijzigen.

Om een animatie te maken door individuele FACS-waarden in te voegen:

1.

Klik in de tracklijst  van de Animatie-editor  op het pluspictogram . Een contextmenu toont aanvullende tracks die je aan de tracklijst kunt toevoegen.

2.

Beweeg de muis over Brows , Ogen , Kaak , Mond  of Tong . Een contextmenu toont alle gemapte FACS-poses voor dat gebied van het gezicht.

 ![Een close-up van de Animatie-editor met het contextmenu en de submenu's uitgebreid. Het pluspictogram is gemarkeerd om aan te geven hoe je het contextmenu opent.](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/animating-dynamic-heads/FACS-Popup.jpg)

3.

Selecteer een FACS-pose. Een animatietrack voor die FACS-pose verschijnt in de tracklijst.

4.

Voer in de waardeninvoer een getal in tussen 0  en 1  om het lichaamsdeel in een nieuwe positie te manipuleren. Als je bijvoorbeeld LeftEyeClosed  op 1 verandert, sluit het linkeroog van het karakter.

 ![Een close-up van de tracklijst in de Animatie-editor. De waardeninvoer is gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/animating-dynamic-heads/Animation-Track-Values-Input.jpg)

### [Gebruik de Face Animation Editor](#gebruik-de-face-animation-editor)[](#gebruik-de-face-animation-editor)

De Face Animation Editor  is een intuïtieve, visuele manier om automatisch keyframes te creëren terwijl je regelaars  aanpast om de gewenste gezichtsuitdrukking te bereiken. Wanneer je bijvoorbeeld de duim van de LeftEyeClosed -regelaar helemaal naar beneden sleept, sluit het linkeroog van het karakter en verschijnt er een nieuwe animatietrack voor LeftEyeClosed  met een waarde van 1  in de tracklijst.

Sommige regelaars beïnvloeden meerdere FACS-waarden in hetzelfde gebied, afhankelijk van de waarde van de regelaar die je aanpast. Wanneer je bijvoorbeeld de duim van de LeftEyeClosed -regelaar helemaal omhoog aanpast om een waarde van 0  te hebben, verschijnt er een nieuwe animatietrack voor LeftEyeUpperLidRaiser  in de tracklijst met een waarde van 1 . Dit stelt je in staat om het oog van gesloten naar open te manipuleren, terwijl je ook het bovenste ooglid optilt, allemaal binnen één regelaar.

Je kunt meerdere regelaars instellen om een complete gezichtsuitdrukking te creëren, en vervolgens meerdere uitdrukkingen op verschillende frames van de tijdlijn maken om complexe animaties te creëren. Je kunt bijvoorbeeld LeftEyeClosed  en RightEyeClosed  samenvoegen zodat het karakter langzaam knippert, of LeftLipCornerPuller  of RightLipCornerPuller  voor een glimlach aan één kant van het gezicht.

Wanneer je de duim van het sleepvak tussen de ogen sleept, kun je de richting bepalen waarin de ogen van het karakter kijken. Dit creëert verschillende FACS-eigenschapstracks in de tracklijst, afhankelijk van hoe je de ogen aanpast.

Linksonder in het paneel bevat de Face Animation Editor  ook de volgende bedieningselementen:

| Bedieningselement | | Beschrijving |
| --- | --- |
| Symmetrie-schakelaar | | Laat je een regelaar aan één kant van het gezicht gebruiken om ook de bijbehorende regelaar aan de andere kant van het gezicht naar dezelfde waarde aan te passen. Dit is nuttig om symmetrische gezichtsuitdrukkingen te creëren, zoals een volle glimlach. |
| Focus Gezicht-schakelaar | | Focust de viewport op het gezicht van de avatar zonder de camera handmatig aan te passen. Dit is nuttig wanneer je camera ver weg is van de avatar die je wilt animeren, of als je navigeert van het animeren van de ene avatar naar de andere. |
| Reset Alles-knop | | Reset alle FACS-posewaarden op je huidige framepositie terug naar hun standaardwaarde van 0. Dit is nuttig wanneer je snel een enkele frame opnieuw wilt animeren. |

Om een animatie voor je hoofd te maken met de Face Animation Editor :

1.

Klik in de tracklijst  van de Animatie-editor  op de Gezicht -knop. De Face Animation Editor  verschijnt links van de tracklijst.

 ![Een close-up van de tracklijst in de Animatie-editor. De Gezicht-knop is gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/animating-dynamic-heads/Face-Button.jpg)

2.

Pas in de Face Animation Editor  de regelaars aan voor de lichaamsdelen die je wilt manipuleren. Animatietracks voor elk gezichtsdeel dat je manipuleert, worden automatisch weergegeven in de tracklijst, samen met keyframes voor je huidige positie in de tijdlijn. Het gezicht van het karakter wordt ook bijgewerkt in de viewport.

-

Om een stap op een regelaar ongedaan te maken, druk op Ctrl Z  (⌘ Z ).

-

Om een stap op een regelaar opnieuw uit te voeren, druk op Ctrl Y  (⌘ Y ).

-

Om een regelaar naar de standaardwaarde te resetten, klik met de rechtermuisknop op de regelaar. Een contextmenu verschijnt. Selecteer Reset Geselecteerd .

3.

OPTIONEEL

 Pas de scrubber aan naar een nieuwe positie verderop in de tijdlijn, navigeer vervolgens terug naar de Face Animation Editor  en pas de regelaars aan om een nieuwe gezichtsuitdrukking te creëren. Wanneer je de animatie afspeelt, zal de eerste gezichtsuitdrukking overgaan in de tweede gezichtsuitdrukking.

4.

Wanneer je klaar bent met het maken van je animatie, navigeer naar de Media- en afspeelbedieningselementen  en klik op de … -knop. Een pop-upmenu verschijnt.

5.

Selecteer Opslaan  of Opslaan als  om de animatie op te slaan. De animatie wordt weergegeven in het Explorer -venster als een kind van het AnimSaves -object (zelf een kind van de rig).

## [Animaties exporteren](#animaties-exporteren)[](#animaties-exporteren)

Wanneer je een hoofd dat animatie ondersteunt naar Studio exporteert, wordt het beschikbaar voor gebruik in al je games. Dit betekent dat je slechts één keer een hoofdanimatie hoeft te maken, en deze vervolgens zo vaak kunt hergebruiken voor zoveel karakters als je wilt, zolang het karakter een [animeerbaar hoofd](/docs/nl-nl/avatar/dynamic-heads)  heeft.

Je kunt hoofdanimaties exporteren met dezelfde workflow die is beschreven voor [het exporteren van animaties](/docs/nl-nl/animation/editor#exporteer-een-animatie) .

## [Scriptanimaties](#scriptanimaties)[](#scriptanimaties)

Zodra je een animatie hebt gemaakt, moet je een script gebruiken om deze in je game af te spelen. Net als bij generieke animaties, kun je animaties voor hoofden handmatig vanuit je scripts afspelen of automatisch door de standaardanimaties voor spelerskarakters te vervangen. Voor meer informatie, zie [Gebruik animaties](/docs/nl-nl/animation/using) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
