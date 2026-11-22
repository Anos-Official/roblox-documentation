<!-- Source: https://create.roblox.com/docs/nl-nl/performance-optimization/test-on-hardware -->

Testen op hardware | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Prestatieoptimalisatie](/docs/nl-nl/performance-optimization)

# Testen op hardware

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Roblox Studio biedt nuttige emulatietools voor [het testen van verschillende apparaten](/docs/nl-nl/studio/testing-modes) , maar emulatie kan niet volledig repliceren wat er op echte hardware gebeurt. Frame rates, geheugenbelasting, thermische throttling en invoerlatenz gedragen zich allemaal anders op fysieke apparaten. Testen op hardware helpt je problemen te ontdekken die alleen onder echte wereldomstandigheden naar voren komen.

## [Waarom testen op apparaten](#waarom-testen-op-apparaten)[](#waarom-testen-op-apparaten)

Studio draait de client en server samen op je ontwikkelingsmachine, die doorgaans veel krachtiger is dan de apparaten die je spelers gebruiken. Dit creëert blinde vlekken met de apparaten die je spelersbasis doorgaans gebruikt:

-

Geheugen  — De [apparaatemulator](/docs/nl-nl/studio/testing-modes)  is nuttig voor het controleren van beeldverhoudingen en bedieningselementen, maar is niet nauwkeurig voor geheugengebruik. Op een echt apparaat concurreren het besturingssysteem, achtergrond-apps en de Roblox-engine zelf allemaal om beperkte RAM.

-

Frame rate  — Een high-end pc kan inefficiënte code of andere problemen verwerken die ernstige frame drops veroorzaken op mobiele of low-end hardware. Problemen zijn gemakkelijker op te merken (en te reproduceren) op beperkte apparaten.

-

Thermische throttling  — Telefoons, tablets en zelfs dunne laptops verlagen de CPU- en GPU-kloksnelheden als ze oververhit raken tijdens langdurig gamen.

-

Invoer en latentie  — Aanraakresponsiviteit, pollingfrequenties van gamepads en netwerkgedrag via mobiele verbindingen kunnen alleen op echte hardware worden gevalideerd.

## [Populaire apparaten in de spelersbasis](#populaire-apparaten-in-de-spelersbasis)[](#populaire-apparaten-in-de-spelersbasis)

De meerderheid van de Roblox-spelers bevindt zich op apparaten met lagere specificaties, met enkele uitzonderingen voor specifieke genres of competitieve games. Het begrijpen van het apparaatlandschap helpt je prioriteit te geven aan wat je moet testen, en je kunt het [Performance Dashboard](/docs/nl-nl/production/analytics/performance)  gebruiken om nauwkeurigere statistieken van je spelersbasis te krijgen.

Roblox is van nature cross-play, wat betekent dat het een breed scala aan apparaten ondersteunt, en de apparaatsamenstelling verschilt tussen landen, leeftijdsgroepen, genres en meer. Om het breedste publiek te bereiken, moet je game goed presteren op het volledige scala aan apparaten.

De volgende zijn algemene apparaatsstatistieken binnen de gebruikersbasis:

-

Android  vertegenwoordigt ongeveer 65% van de spelersbasis van een typische game.

-

~60% van die spelers heeft 2–4 GB  RAM.

-

~35% heeft 4–8 GB  RAM.

-

~5% heeft meer dan 8 GB RAM.

-

Meer dan 50% van de Roblox-spelers speelt op apparaten die tussen de 10.000–20.000  scoren op [Passmark](https://www.passmark.com/)  benchmarks.

Als je alleen op je ontwikkelingsmachine test, test je voor de minderheid van je publiek. Geef prioriteit aan [cross-platform compatibiliteit](/docs/nl-nl/projects/cross-platform)  en kies ten minste één low-end basisapparaat dat je doelspeler demografie vertegenwoordigt.

Voor een breder scala aan Android-testapparaten dat meer van de spelersbasis dekt, kies apparaten op verschillende prestatieniveaus van verschillende fabrikanten. Je zou bijvoorbeeld kunnen testen op een Infinix Smart 9, een Motorola Moto G05, een Oppo A18, een Amazon Fire HD 10 (2023) en een Samsung Galaxy S22 Ultra.

## [Teststrategieën](#teststrategieën)[](#teststrategieën)

Teststrategieën zijn afhankelijk van je game en je ontwikkelingsworkflow — er is geen enkele aanpak die voor elk project past. De volgende bieden een solide basis voor het integreren van hardwaretesten in je proces.

Multi-invoerapparaten kunnen je testdekking vergroten zonder dat je een volledige apparaatlab nodig hebt. Een handheld gamepad met een touchscreen stelt je bijvoorbeeld in staat om zowel aanraak- als gamepadinvoer op één stuk hardware te valideren. Telefoons met USB-C gamepad-adapters of laptops met touchscreen kunnen hetzelfde doel dienen.

### [Prestatie](#prestatie)[](#prestatie)

Prestatie testen op hardware richt zich op drie gebieden: frame rate (berekeningen), geheugen en laadtijd. Voor een volledige uitsplitsing van diagnostische tools, zie [Identificeer prestatieproblemen](/docs/nl-nl/performance-optimization/identify) .

Voor richtlijnen over het kiezen van een basislijn en het binnen de grenzen blijven, zie [Ontwerp voor prestaties](/docs/nl-nl/performance-optimization/design#apparaten-met-lage-specificaties) .

#### [Profiel op apparaat](#profiel-op-apparaat)[](#profiel-op-apparaat)

De [MicroProfiler](/docs/nl-nl/performance-optimization/microprofiler)  en de [Developer Console](/docs/nl-nl/studio/developer-console)  draaien beide op clientapparaten, niet alleen in Studio. Gebruik ze direct op hardware om nauwkeurige frame-tijd uitsplitsingen en geheugenmetingen te krijgen.

-

Open de Developer Console met F9  (of het in-game menu) om het geheugengebruik onder het Geheugen  tabblad te controleren.

-

Gebruik de MicroProfiler (Ctrl Alt F6  / ⌘ ⌥ F6 ) om frame-dumps op het apparaat vast te leggen en analyseer ze vervolgens op je ontwikkelingsmachine.

-

Schakel Prestatiestatistieken  in vanuit het instellingenmenu om een overlay van FPS, geheugen en ping te zien.

#### [Test op thermische throttling](#test-op-thermische-throttling)[](#test-op-thermische-throttling)

Voer je game uit op een mobiel apparaat voor een uitgebreide sessie (10–15 minuten actieve gameplay). Let op de afname van de frame rate in de loop van de tijd — een constante daling duidt vaak aan dat het apparaat thermisch throttled. Als je dit ziet, concentreer je dan op het verminderen van de aanhoudende GPU- of CPU-belasting in hete codepaden die door de MicroProfiler zijn geïdentificeerd.

#### [Valideer netwerkcondities](#valideer-netwerkcondities)[](#valideer-netwerkcondities)

Spelers op mobiele netwerken ervaren hogere latentie, jitter en pakketverlies dan bedrade verbindingen. Gebruik [netwerksimulatie](/docs/nl-nl/studio/testing-modes#netwerksimulatie)  in Studio voor snelle iteratie, maar bevestig het gedrag op een echt apparaat via mobiele of beperkte Wi-Fi.

#### [Monitor na publicatie](#monitor-na-publicatie)[](#monitor-na-publicatie)

Zodra je game live is, gebruik je het [Performance Dashboard](/docs/nl-nl/performance-optimization/monitor)  om de client frame rate, geheugengebruik en crashpercentages over apparaatscategorieën in de loop van de tijd te volgen. Een plotselinge stijging van het aantal crashes na een update wijst vaak op een geheugenregressie op low-end apparaten.

### [Gebruikerservaring](#gebruikerservaring)[](#gebruikerservaring)

Prestatiecijfers vertellen niet het volledige verhaal. Een game kan 60 FPS halen op een apparaat en toch gebroken aanvoelen als aanraakdoelen te klein zijn of de UI onleesbaar is. Voor uitgebreide richtlijnen voor cross-platform UI, zie [Cross-platform ontwikkeling](/docs/nl-nl/projects/cross-platform) .

Windows handhelds zoals de ROG Xbox Ally bieden veel nut bij het testen van de gebruikerservaring. Naast ingebouwde controllers hebben deze apparaten doorgaans touchscreens en ondersteunen ze invoer van een muis en toetsenbord (meest nuttig wanneer verbonden met een extern display). Windows handhelds hebben de neiging om dramatisch snellere hardware te hebben dan een midrange telefoon, dus ze zijn minder waardevol voor prestatietests.

#### [Aanraakdoelen en gebaren](#aanraakdoelen-en-gebaren)[](#aanraakdoelen-en-gebaren)

Test op echte telefoonschermen, niet alleen op geëmuleerde resoluties. Knoppen die comfortabel lijken op een desktopmonitor kunnen frustrerend klein zijn op een 5-inch display. Bevestig dat:

-

Interactieve elementen groot genoeg zijn om betrouwbaar aan te raken op verschillende schermformaten.

-

Gebaren zoals inzoomen en vegen niet conflicteren met je gameplaybedieningselementen.

-

On-screen thumbsticks en actieknoppen zich binnen comfortabele bereikzones bevinden.

#### [Schermleesbaarheid](#schermleesbaarheid)[](#schermleesbaarheid)

UI-elementen die scherp lijken op 1440p kunnen onleesbaar worden op een mobiel scherm met lage resolutie. Test de tekstgrootte, iconenhelderheid en contrast op je laagste ondersteunde apparaat op armlengte kijkafstand. Voor richtlijnen over adaptieve lay-outs, zie [Adaptief ontwerp](/docs/nl-nl/production/publishing/adaptive-design) .

#### [Invoerschakeling](#invoerschakeling)[](#invoerschakeling)

Spelers schakelen vaak van invoermethoden tijdens een sessie — een tabletspeler kan een Bluetooth-controller aansluiten, of een laptopspeler kan van trackpad naar muis schakelen. Bevestig dat je ervaring correct reageert op [wijzigingen in het invoertype](/docs/nl-nl/projects/cross-platform#invoertype-detectie)  en eventuele [ondersteunende hints](/docs/nl-nl/projects/cross-platform#ondersteunende-hints)  dienovereenkomstig bijwerkt.

#### [Laden en streamen](#laden-en-streamen)[](#laden-en-streamen)

Eerste indrukken zijn belangrijk. Tim de volledige join-to-gameplay flow op je basisapparaat over een typische verbinding. Als laadtijden enkele seconden overschrijden, overweeg dan om [instance streaming](/docs/nl-nl/workspace/streaming)  in te schakelen om de initiële laadtijden en geheugengebruik te verminderen. Test of streaming geen zichtbare pop-in veroorzaakt die de onderdompeling tijdens normale gameplaybeweging verstoort.

#### [Audio](#audio)[](#audio)

Test met zowel de luidspreker van het apparaat als met koptelefoons. Mobiele luidsprekers hebben een beperkt frequentiebereik en volume — geluidseffecten of stemlijnen die duidelijk zijn op desktopkoptelefoons kunnen modderig of onhoorbaar zijn op een telefoonspeaker.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
