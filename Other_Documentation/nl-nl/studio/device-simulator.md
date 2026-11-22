<!-- Source: https://create.roblox.com/docs/nl-nl/studio/device-simulator -->

Apparaatsimulator | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Studio](/docs/nl-nl/studio)
4. /
5. [Device Simulator](/docs/nl-nl/studio/device-simulator)

# Apparaatsimulator

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Apparaatsimulator  is een werkbalk in Roblox Studio die laat zien hoe jouw ervaring eruitziet en zich gedraagt op een apparaat dat je niet voor je hebt. Het simuleert de schermafmetingen, pixeldichtheid, het on-screen toetsenbord en het platform van een apparaat. De bedieningselementen bevinden zich in een werkbalk boven het 3D-venster in plaats van in een apart paneel, zodat je ze kunt bereiken terwijl je aan het playtesten bent.

Apparaatsimulator is in [beta](https://devforum.roblox.com/t/studio-beta-new-device-simulator-toolbar-and-network-simulator/4861695) , en de functionaliteit kan veranderen. Om het in te schakelen, open je Bestand  en selecteer je Beta-functies , schakel dan Nieuwe Apparaatsimulator  in en herstart Studio.

## [Open Apparaatsimulator](#open-apparaatsimulator)[](#open-apparaatsimulator)

De werkbalk verschijnt boven het 3D-venster wanneer een plaats is geopend. Het blijft beschikbaar in zowel bewerkings- als speelmodi, zodat je het gesimuleerde apparaat kunt wijzigen midden in een playtest zonder te stoppen, te schakelen of opnieuw te starten.

## [Simuleer een apparaat](#simuleer-een-apparaat)[](#simuleer-een-apparaat)

De linkerkant van de werkbalk bevat één knop per apparaatscategorie, gevolgd door een chip die het actieve apparaat benoemt.

 ![Apparaatsimulator werkbalk met een geselecteerde iPhone boven het Studio-venster.](https://prod.docsiteassets.roblox.com/assets/studio/device-simulator/device-simulator-toolbar.png)

| Categorie | | Wat het simuleert |
| --- | --- |
| Telefoon | | Telefoons en tablets, inclusief aanraakinvoer en het on-screen toetsenbord. |
| Desktop | | Desktop- en laptopresoluties. |
| Console | | Console-uitgangsresoluties en gamepad-eerste invoer. |
| Headset | | VR-headsets. |

Door op een categorie te klikken, schakel je over naar het standaardapparaat van die categorie. Een categorie is uitgeschakeld wanneer er geen apparaat in beschikbaar is om te simuleren. Door op de apparaatchip te klikken, open je het apparaatsmenu, waar apparaten zijn gegroepeerd om de afweging die je test expliciet te maken:

-

Telefoon : Vlaggenschip , Middenklasse  en Instapniveau , zodat je een lay-out kunt doorlopen langs de prestatieladder.

-

Desktop , Console  en Headset : één groep ingebouwde apparaten per categorie.

-

Aangepast : apparaten die je zelf hebt gemaakt, in elke categorie.

-

Huidig apparaat : geen simulatie. Je eigen monitor en invoer, vermeld onder Desktop .

De laatste rij van het menu, Beheer apparaten , opent de Apparaatbeheerder.

### [Apparaatbedieningselementen](#apparaatbedieningselementen)[](#apparaatbedieningselementen)

De rechterkant van de werkbalk bevat acties die van toepassing zijn op het gesimuleerde apparaat. Welke verschijnen hangt af van wat je simuleert.

| Bedieningselement | | Beschikbaar voor | | Beschrijving |
| Draaien | | Telefoons en tablets | | Draait het gesimuleerde apparaat naar de volgende oriëntatie. |
| Mock Android terugknop | | Android-apparaten | | Stuurt een druk op de terugknop. Ingeschakeld terwijl de clientweergave actief is. |
| Aanraakbedieningselementen | | Telefoons en tablets | | Geeft de toetsenbord- en muiskortcuts weer die staan voor multi-touch gebaren tijdens het playtesten. |
| Virtuele controller | | Alle apparaten | | Schakelt [Controller Emulator](/docs/nl-nl/studio/controller-emulator)  in, die gamepads, VR-controllers en TV-afstandsbedieningen emuleert. |
| Schermvergroting | | Tijdens het simuleren van een apparaat | | Kiest hoe het gesimuleerde scherm op jouw monitor wordt weergegeven. |

### [Simuleer aanraakinvoer](#simuleer-aanraakinvoer)[](#simuleer-aanraakinvoer)

Een muis heeft één contactpunt, dus gebaren die er twee nodig hebben, worden toegewezen aan modifier-toetsen. Open Aanraakbedieningselementen  om de sneltoetsen voor jouw platform te zien:

-

Knijpen + draaien : Alt + slepen

-

Twee-vinger pan : Alt + Shift + slepen

## [Schermvergroting](#schermvergroting)[](#schermvergroting)

Een gesimuleerd 1080-pixel-hoge telefoonscherm en jouw 1080-pixel-hoge monitor hebben hetzelfde aantal pixels, maar heel verschillende fysieke afmetingen, zodat een UI-element dat comfortabel is op de ene, onleesbaar kan zijn op de andere. Het Schermvergroting  menu kiest welke van die eigenschappen het venster behoudt:

 ![Schermvergroting menu met opties voor fysieke grootte, werkelijke resolutie, passen in venster, kalibratie en autodetectie.](https://prod.docsiteassets.roblox.com/assets/studio/device-simulator/device-simulator-display-scaling.png)

| Modus | | Beschrijving |
| Fysieke grootte | | Komt overeen met de werkelijke grootte van het gesimuleerde scherm, zodat on-screen elementen zo groot zijn als ze zouden zijn in de hand van een speler. |
| Werkelijke resolutie | | Maakt één gesimuleerd pixel gelijk aan één van de pixels van jouw monitor. |
| Passen in venster | | Schaalt het gesimuleerde scherm om het beschikbare venster te vullen. |

Fysieke grootte  geldt alleen als Studio weet hoe groot jouw eigen monitor is, wat het niet direct kan lezen. Twee menu-items leveren dat nummer:

-

Auto-detectie van schaling  komt overeen met de pixeldichtheid en schalingsfactor die jouw besturingssysteem rapporteert voor jouw display. Het uitschakelen valt terug op jouw opgeslagen handmatige kalibratie. Dit item verschijnt alleen in Fysieke grootte  modus, omdat het geen effect heeft in de andere twee.

-

Kalibreer fysieke schaling  meet jouw display met de hand. Sleep de schuifregelaar totdat de afbeelding op het scherm overeenkomt met de breedte van een studenten-ID of bibliotheekkaart. Kalibreren schakelt autodetectie uit en schakelt over naar Fysieke grootte .

Beide waarden blijven behouden tussen sessies, dus eenmaal kalibreren is genoeg.

## [Beheer apparaten](#beheer-apparaten)[](#beheer-apparaten)

Beheer apparaten  in het apparaatsmenu opent de Apparaatbeheerder, met één tab per categorie: Mobiel , Desktop , Console  en Headset . Het opent op de tab die overeenkomt met het apparaat dat je simuleert.

 ![Apparaatbeheerder toont apparaatscategorieën, standaard- en aangepaste apparaten, en configuratievelden voor aangepaste apparaten.](https://prod.docsiteassets.roblox.com/assets/studio/device-simulator/device-manager.png)

### [Toon en verberg standaardapparaten](#toon-en-verberg-standaardapparaten)[](#toon-en-verberg-standaardapparaten)

De Standaard  lijst bevat de ingebouwde apparaten van Roblox. Gebruik Voeg apparaten toe  om te kiezen welke van hen in het apparaatsmenu van de werkbalk verschijnen, en verberg de rest om het menu te beperken tot de apparaten waarmee je daadwerkelijk test. Het verbergen van een apparaat verwijdert het niet, zodat je het op elk moment opnieuw kunt toevoegen. Aangepaste apparaten blijven altijd zichtbaar, net als het apparaat dat je momenteel simuleert.

 ![Dialoogvenster Apparaten toevoegen met selectievakjes die bepalen welke apparaten in de Standaardlijst verschijnen.](https://prod.docsiteassets.roblox.com/assets/studio/device-simulator/device-manager-add-devices.png)

### [Maak aangepaste apparaten](#maak-aangepaste-apparaten)[](#maak-aangepaste-apparaten)

Voeg een aangepast apparaat toe om hardware te modelleren waarvoor Roblox geen profiel levert, of om een enkele eigenschap te isoleren, zoals dezelfde telefoon met de helft van het geheugen. Dupliceer  kopieert een standaardapparaat als startpunt.

| Veld | | Beschrijving | | Geaccepteerde waarden |
| Naam | | De naam die in het apparaatsmenu wordt weergegeven. | | Verplicht, uniek, 200 tekens of minder. |
| Platform | | Het platform dat de ervaring tijdens runtime rapporteert. | | Platform van het gesimuleerde apparaat. |
| Afmetingen | | Schermbreedte en -hoogte in pixels. | | Breedte 1 tot 7680, hoogte 1 tot 4320. |
| Pixeldichtheid | | Pixels per inch, wat de fysieke grootte-schaal aanstuurt. | | 72 tot 10.000. |
| Toetsenbordhoogte | | Hoeveel van het scherm het on-screen toetsenbord bedekt, per oriëntatie. | | Portret en landschap, 0 tot 4320. |

## [Simuleer controllerinvoer](#simuleer-controllerinvoer)[](#simuleer-controllerinvoer)

Het simuleren van een apparaat vertelt je hoe jouw ervaring eruitziet op die hardware. Het geeft je geen bijpassende controller in je handen. [Controller Emulator](/docs/nl-nl/studio/controller-emulator)  werkt samen met Apparaatsimulator om de gamepads, VR-controllers, handhelds en TV-afstandsbedieningen te emuleren die bij de hardware worden geleverd, zodat je invoer kunt testen zonder het te bezitten. Het selecteren van een console, headset, handheld of Android TV-apparaat hier schakelt de Controller Emulator automatisch over naar de bijpassende controller van dat apparaat.

## [Simuleer netwerkcondities](#simuleer-netwerkcondities)[](#simuleer-netwerkcondities)

Het simuleren van een apparaat vertelt je hoe jouw ervaring eruitziet op die hardware. Het vertelt je niet hoe het aanvoelt op de verbinding van die hardware. [Netwerksimulator](/docs/nl-nl/studio/network-simulator)  bevindt zich in dezelfde werkbalk en vormt het verkeer tijdens een playtest, zodat je kunt testen tegen hoge latentie, jitter en pakketverlies zonder een tweede apparaat of een vertraagde router.

## [Voorbeeldwerkstromen](#voorbeeldwerkstromen)[](#voorbeeldwerkstromen)

-

Controleer een lay-out over verschillende formaten.  Klik op telefoon, dan tablet, dan console, en kijk hoe het venster zich aanpast aan elk. Veilige gebieden, overflow en verankeringsproblemen komen onmiddellijk naar voren.

-

Test de onderkant van het prestatieniveau.  Simuleer een Instapniveau  telefoon in plaats van een Vlaggenschip , en bevestig dat jouw UI nog steeds leesbaar is bij die pixeldichtheid en dat jouw ervaring nog steeds binnen dat geheugenschema past.

-

Valideer aanraak-UX.  Simuleer een aanraakapparaat en gebruik de aanraak-sneltoetsen om te bevestigen dat jouw invoer komt waar je het verwacht.

-

Controleer het on-screen toetsenbord.  Simuleer een telefoon, focus op een tekstveld, en bevestig dat het toetsenbord de bedieningselementen die de speler nodig heeft tijdens het typen niet bedekt.

-

Verifieer fysieke afmetingen.  Kalibreer de fysieke schaling eenmaal, en vergelijk dan een telefoon met een tablet in Fysieke grootte  modus om te zien of jouw tikdoelen en tekst groot genoeg zijn op het kleinere scherm.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
