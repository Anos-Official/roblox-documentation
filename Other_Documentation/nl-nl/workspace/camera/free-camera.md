<!-- Source: https://create.roblox.com/docs/nl-nl/workspace/camera/free-camera -->

Vrije cameramodus | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)
6. /
7. [Camera](/docs/nl-nl/workspace/camera)

# Vrije cameramodus

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Roblox biedt een aangepaste debug vrije cameramodus  (freecam) voor ervaringseigenaren en editors, waarmee de camera van je karakter wordt losgekoppeld, zodat je deze vrij door je ervaring kunt laten vliegen om scènes vast te leggen die de standaardcamera niet kan bereiken. Het is vooral nuttig voor het maken van cinematische screenshots en video's, evenals voor het toekijken van spelers in live games en het debuggen van problemen.

## [Beschikbaarheid](#beschikbaarheid)[](#beschikbaarheid)

Je kunt de vrije cameramodus op twee plaatsen gebruiken:

-

Roblox Studio  - freecam is beschikbaar tijdens [playtesting](/docs/nl-nl/studio/testing-modes#spelen-testen)  sessies.

-

De live client  - je moet de eigenaar van de ervaring zijn, of bewerkingsrechten in de ervaring hebben gekregen.

Momenteel kan freecam alleen worden in- of uitgeschakeld met een toetsenbord (Linker Shift  + P ). Eenmaal actief, kan het worden bediend met een toetsenbord en muis of een gamepad.

## [Hoe te schakelen](#hoe-te-schakelen)[](#hoe-te-schakelen)

Druk op Linker Shift  + P  om de vrije cameramodus in of uit te schakelen. Wanneer ingeschakeld, wordt de camera losgekoppeld van je karakter en wordt je on-screen UI automatisch verborgen, zodat je een onbelemmerd uitzicht op de scène krijgt.

## [Invoersysteem](#invoersysteem)[](#invoersysteem)

De verbeterde mogelijkheden van de vrije camera die op deze pagina worden beschreven — inclusief het [configuratiemenu](#configuratiemenu)  en [cinematische post-processing](#aangepaste-post-processing)  — draaien op het [Invoersysteem](/docs/nl-nl/input/input-action-system)  (IAS) en zijn alleen beschikbaar wanneer je ervaring is ingeschreven voor de geüpgrade IAS-spelerscripts.

Om je in te schrijven, stel je [Workspace.PlayerScriptsUseInputActionSystem](/docs/nl-nl/reference/engine/classes/Workspace#PlayerScriptsUseInputActionSystem)  in op [Enabled](/docs/nl-nl/reference/engine/enums/RolloutState)  om vrije camerabesturingen op IAS te laten draaien, zodat invoer netjes samen met je standaard gameplay-acties wordt verwerkt.

## [Camerabesturingen](#camerabesturingen)[](#camerabesturingen)

In de freecam-modus kan de camera bewegen en draaien naar de gewenste positie, onafhankelijk van het karakter en de scène. De volgende besturingen zijn beschikbaar om de camera te bedienen:

| Actie | | Toetsenbord & Muis | | Gamepad |
| --- | --- |
| Vooruit / links / achteruit / rechts bewegen | | W  A  S  D | | Linker thumbstick |
| Verhoog de hoogte (omhoog / omlaag) | | E  / Q | | R2  / L2 |
| Roteren / pannen van het uitzicht | | Houd de rechtermuisknop ingedrukt en sleep, of pan op een trackpad | | Rechter thumbstick |
| Inzoomen (gezichtsveld) | | Muisscrollwiel, of trackpad knijpen | | X  / Y |
| Rol (kantelen naar links / rechts) | | Z  / C  — dubbelklik op een van de toetsen om de rol te resetten | | L1  / R1  — dubbelklik om de rol te resetten |
| Langzamer bewegen voor nauwkeurige framing | | Houd Shift  ingedrukt tijdens het bewegen | | — |
| Open het configuratiemenu | | ↑  (omhoog pijltje) | | D-pad Omhoog |

### [Beweging](#beweging)[](#beweging)

Gebruik W  A  S  D  (of de linker thumbstick) om de camera door je scène te laten vliegen.

### [Hoogte](#hoogte)[](#hoogte)

Gebruik E  en Q  (of R2  / L2 ) om de camera verticaal te verhogen en te verlagen.

### [Rotatie](#rotatie)[](#rotatie)

Houd de rechtermuisknop ingedrukt en sleep (of gebruik de rechter thumbstick) om het uitzicht naar je onderwerp te draaien en te pannen.

### [Gezichtsveld](#gezichtsveld)[](#gezichtsveld)

Scroll met het muiswiel (of druk op X  / Y  op een gamepad) om het gezichtsveld in te zoomen. Het verkleinen van het gezichtsveld zorgt voor een strakkere, meer telefoto-framing op verre onderwerpen.

### [Rol](#rol)[](#rol)

Gebruik Z  en C  (of L1  / R1 ) om de camera te rollen voor een Dutch-angle effect. Dubbelklik op een van de rolbesturingen om de camera terug te zetten naar het standaardniveau.

## [Configuratiemenu](#configuratiemenu)[](#configuratiemenu)

Druk op ↑  (of D-pad Omhoog) om het on-screen configuratiemenu  te openen, dat diepere aanpassingen voor het verfijnen van je opname blootlegt.

Navigeer door het menu met de volgende besturingen:

-

↑  ↓  verplaatst de selectie door de lijst.

-

→  gaat een groep in of selecteert een item om te bewerken.

-

←  gaat terug naar het vorige niveau, of sluit het menu vanaf het bovenste niveau.

-

Wanneer je een item bewerkt, ←  →  past de waarde aan en ↑  ↓  verlaat de bewerking.

Op een gamepad gebruik je de D-pad in de overeenkomstige richtingen.

### [Beweging, rotatie, rol en gezichtsveld](#beweging-rotatie-rol-en-gezichtsveld)[](#beweging-rotatie-rol-en-gezichtsveld)

Elk van deze bewegingsbesturingen biedt twee onafhankelijke instellingen in het configuratiemenu:

-

Snelheid  regelt hoe snel de waarde verandert. Verhoog het om sneller afstand te overbruggen, in te zoomen, te kantelen of te pannen; verlaag het voor fijne, nauwkeurige aanpassingen.

-

Stijfheid  regelt hoe de camera zich aanpast aan een invoerwijziging. Hogere stijfheid is snel en volgt je invoer nauwkeurig met weinig afvlakking; lagere stijfheid voegt demping toe, zodat de camera geleidelijk in- en uitzoomt voor soepelere, meer cinematische beweging.

Hoge snelheid  — de camera draait snel:

Lage snelheid  — de camera draait langzaam voor nauwkeurige framing:

Hoge stijfheid  — de camera volgt de invoer nauwkeurig en stopt scherp:

Lage stijfheid  — de camera beweegt geleidelijk in en uit voor soepelere, meer cinematische beweging:

### [UI-zichtbaarheid](#ui-zichtbaarheid)[](#ui-zichtbaarheid)

Beheer welke on-screen interface zichtbaar blijft, zodat je een schone opname kunt maken of belangrijke informatie op het scherm kunt houden.

-

Scherm GUI's  — schakel de on-screen UI overlays van de ervaring in of uit. Stel in op Aan  om ze zichtbaar te houden, of Uit  om ze te verbergen voor een onbelemmerd uitzicht.

-

Leaderboard  — schakel het spelersleaderboard in of uit. Stel in op Aan  om het op het scherm te houden, of Uit  om het te verbergen.

### [Speler Lock](#speler-lock)[](#speler-lock)

Speler Lock houdt de camera gericht op het karakter van een specifieke speler terwijl deze zich verplaatst, zodat je de actie kunt volgen zonder handmatig te volgen.

-

Inschakelen  — zet Speler Lock aan of uit. Wanneer het aan is, volgt de camera het gekozen doel; wanneer het uit is, beweegt de camera vrij.

-

Doel  — cyclus door de spelers op de server om te kiezen wie de camera op zich vergrendelt.

### [Aangepaste post-processing](#aangepaste-post-processing)[](#aangepaste-post-processing)

Laag cinematische [post-processing effecten](/docs/nl-nl/environment/post-processing-effects)  op je opname. Inschakelen  schakelt alle bestaande post-processing effecten uit ten gunste van aangepaste freecam-effecten, en elk effect hieronder kan vervolgens afzonderlijk worden in- en uitgeschakeld en fijn worden afgesteld:

-

[Diepte van het Veld](/docs/nl-nl/environment/post-processing-effects#depth-of-field)  vervaagt delen van de scène die niet in focus zijn — geweldig om de aandacht op een onderwerp te vestigen of een verre achtergrond te verzachten.

-

[Bloom](/docs/nl-nl/environment/post-processing-effects#bloom)  overdrijft heldere lichten zodat lichtgekleurde gebieden gloeien, wat simuleert dat een camera op een sterke lichtbron is gericht.

-

[Vervaging](/docs/nl-nl/environment/post-processing-effects#blur)  past een Gaussische vervaging toe over het hele uitzicht voor zachte, dromerige of volledig onscherpe looks.

-

[Kleurcorrectie](/docs/nl-nl/environment/post-processing-effects#kleurcorrectie)  past helderheid, contrast, verzadiging en tint aan om de sfeer te bepalen of de algehele kleur van je opname te bewerken.

-

[Zonnestralen](/docs/nl-nl/environment/post-processing-effects#zonnestralen)  werpt een halo van licht met stralen rond de zon, gevormd door objecten tussen de camera en de zon voor realistisch licht en schaduw.

-

[Kleurgradatie](/docs/nl-nl/environment/post-processing-effects#kleurgrading)  verandert hoe gerenderde kleuren op het scherm worden weergegeven — wissel tussen de levendige moderne look en een minder verzadigde retrotoon.

## [Sneltoetsen voor GUI-zichtbaarheid](#sneltoetsen-voor-gui-zichtbaarheid)[](#sneltoetsen-voor-gui-zichtbaarheid)

Afgezien van de toggles voor [UI-zichtbaarheid](#ui-zichtbaarheid)  in het configuratiemenu, biedt Roblox engine-niveau sneltoetsen die categorieën van on-screen UI verbergen, nuttig voor het maken van een schone opname zonder enige interface. Ze werken in de live client  en in een Studio playtest , en zijn beschikbaar voor hetzelfde publiek als de vrije camera — de eigenaar van de ervaring of een gebruiker met bewerkingsrechten (en altijd in Studio). Druk nogmaals op dezelfde sneltoets om te herstellen.

Deze besturingen zijn momenteel alleen beschikbaar voor toetsenbord. Houd Ctrl  (of ⌘  op macOS) en Linker Shift  ingedrukt, en druk vervolgens op:

| Sneltoets | | Verbergt / toont |
| Ctrl Linker Shift G | | De door Roblox geleverde Core UI , zoals de bovenste balk en menu's. |
| Ctrl Linker Shift C | | Door ontwikkelaars gemaakte [ScreenGuis](/docs/nl-nl/reference/engine/classes/ScreenGui)  (on-screen 2D UI's). |
| Ctrl Linker Shift B | | Door ontwikkelaars gemaakte [BillboardGuis](/docs/nl-nl/reference/engine/classes/BillboardGui)  (wereldruimte 3D billboards). |
| Ctrl Linker Shift N | | Speler naamplaten (namen en gezondheidsbalken). |

Ctrl Linker Shift G  — schakel de Roblox Core UI in of uit:

Ctrl Linker Shift C  — schakel de on-screen GUI's van de ervaring in of uit:

Ctrl Linker Shift B  — schakel door ontwikkelaars gemaakte BillboardGuis in of uit:

Ctrl Linker Shift N  — schakel speler naamplaten in of uit:

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
