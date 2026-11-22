<!-- Source: https://create.roblox.com/docs/nl-nl/projects/cross-platform -->

Cross-platform ontwikkeling | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Projecten](/docs/nl-nl/projects)

# Cross-platform ontwikkeling

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Roblox is van nature cross‑platform , aangezien spelers games kunnen ontdekken en deelnemen op hun telefoon of tablet, en later kunnen doorgaan waar ze waren gebleven op hun pc of console. Om een groeiende reeks platforms te ondersteunen, moet je gebruikersinterfaces bouwen die naadloos aanpassen aan het type invoer (aanraking, gamepad, muis/toetsenbord), schermgrootte en apparaatoriëntatie. Deze gids, de [adaptive design](/docs/nl-nl/production/publishing/adaptive-design)  gids, en de gelinkte bronnen kunnen je helpen een echt cross‑platform spel te ontwerpen dat compatibel, toegankelijk en plezierig is op alle  platforms.

Om een vooraf gemaakt spel te verkennen dat de volgende cross‑platform ontwerpconcepten toont, bekijk de [Interactivity Showcase](https://www.roblox.com/games/132115384567250/) .

## [Invoer](#invoer)[](#invoer)

Een zorgvuldig ontworpen spel moet alle primaire invoertypen ondersteunen, waaronder muis en toetsenbord, aanraking en gamepads.

### [Cross-platform acties](#cross-platform-acties)[](#cross-platform-acties)

Ondersteun alle primaire invoertypen (muis/toetsenbord, aanraking en gamepads) met behulp van het [Input Action System](/docs/nl-nl/input/input-action-system) .

Om cross‑platform invoer te vereenvoudigen, biedt Roblox het [Input Action System](/docs/nl-nl/input/input-action-system)  om acties  zoals "springen", "rennen" of "schieten" te definiëren en bindingen  voor meerdere hardware-invoeren in te stellen om die acties aan te sturen. Je hoeft niet na te denken over alle technische aspecten van hardware-invoeren en wanneer je naar specifieke invoertriggers moet luisteren; je definieert eenvoudig welke invoeren welke acties uitvoeren.

 ![](https://prod.docsiteassets.roblox.com/assets/publishing/cross-platform/Input-Actions-Jump.png)

### [Invoertype detectie](#invoertype-detectie)[](#invoertype-detectie)

Zorg ervoor dat UI-elementen reageren en zich aanpassen aan het primaire  invoertype van de speler zoals beschreven in [invoertype detectie](/docs/nl-nl/input#invoertype-detectie) . Overweeg ook [ondersteunende hints](#ondersteunende-hints)  om spelers te helpen specifieke invoerwijzigingen te begrijpen.

Bij cross-platform ontwikkeling is het belangrijk dat je het primaire invoertype dat een speler gebruikt, bepaalt en erop reageert, normaal gesproken om ervoor te zorgen dat [UI-elementen](/docs/nl-nl/ui#ui-objecten)  zoals knoppen en menu's elegant werken en interactie ondersteunen tussen apparaten.

Bijvoorbeeld, een apparaat met aanraakfunctionaliteit gaat ervan uit dat aanraking de standaard  invoer is en dat aanraakknoppen kunnen verschijnen voor acties, maar een speler kan ervoor kiezen om een bluetooth gamepad aan te sluiten. In dit geval blijft aanraking een geldige invoer, maar je kunt aannemen dat de speler wil overschakelen naar de aangesloten gamepad als het primaire  invoertype en mogelijk aanraking als een back-up invoer voor de UI op het scherm gebruiken.

Als je het [Input Action System](/docs/nl-nl/input/input-action-system)  gebruikt, complementeert de [PreferredBinding](/docs/nl-nl/reference/engine/classes/InputAction#PreferredBinding)  eigenschap de detectie van primaire invoer: net zoals [PreferredInput](/docs/nl-nl/reference/engine/classes/UserInputService#PreferredInput)  het huidige primaire invoertype van de speler rapporteert, rapporteert [PreferredBinding](/docs/nl-nl/reference/engine/classes/InputAction#PreferredBinding)  de specifieke [InputBinding](/docs/nl-nl/reference/engine/classes/InputBinding)  die overeenkomt met het huidige apparaat van de speler. Beide worden automatisch bijgewerkt wanneer de speler van apparaat wisselt, zodat je apparaatbewuste UI kunt aansturen zonder zelf logica voor apparaatwisseling te schrijven.

### [Ondersteunende hints](#ondersteunende-hints)[](#ondersteunende-hints)

Op basis van het [primaire invoertype](#invoertype-detectie)  wordt aanbevolen dat je ondersteunende UI-hints  opneemt wanneer mogelijk. Bijvoorbeeld, wanneer je gereedschappen selecteert om uit te rusten, toon invoer-specifieke hints zoals 1 – 5  wanneer de speler een toetsenbord gebruikt, of gamepad-trigger hints wanneer de speler een gamepad gebruikt.

Voor no-code ondersteunende hints die automatisch worden bijgewerkt wanneer de speler van apparaat wisselt, gebruik [InputActionLabel](/docs/nl-nl/reference/engine/classes/InputActionLabel)  en wijs het aan een [InputAction](/docs/nl-nl/reference/engine/classes/InputAction)  om de juiste invoer per platform weer te geven. Zie [bindingen weergeven](/docs/nl-nl/input/input-action-system#weergeven-van-bindings)  voor volledige details.

Voor meer gedetailleerde controle, of als je de hintweergave verder wilt aanpassen dan wat [InputActionLabel](/docs/nl-nl/reference/engine/classes/InputActionLabel)  biedt, kun je de [UserInputService](/docs/nl-nl/reference/engine/classes/UserInputService)  methoden hieronder gebruiken om handmatig platform-specifieke afbeeldingen en strings te verzamelen:

Toetsenbordinvoer Gamepadinvoer

![](https://prod.docsiteassets.roblox.com/assets/publishing/cross-platform/Inventory-Selection-Keyboard.jpg)

De [GetImageForKeyCode()](/docs/nl-nl/reference/engine/classes/UserInputService#GetImageForKeyCode)  en [GetStringForKeyCode()](/docs/nl-nl/reference/engine/classes/UserInputService#GetStringForKeyCode)  methoden zijn nuttig om een platform-specifieke afbeelding of string te verzamelen voor gebruik in een UI-hint, zoals de volgende voorbeelden:

| Toetscode | | Xbox Afbeelding | | PlayStation Afbeelding | | String |
| --- | --- |
| [Enum.KeyCode.ButtonA](/docs/nl-nl/reference/engine/enums/KeyCode#ButtonA) | | ![](https://prod.docsiteassets.roblox.com/assets/publishing/cross-platform/ButtonA-Xbox.png) | | ![](https://prod.docsiteassets.roblox.com/assets/publishing/cross-platform/ButtonA-PS.png) | | ButtonA |
| [Enum.KeyCode.ButtonX](/docs/nl-nl/reference/engine/enums/KeyCode#ButtonX) | | ![](https://prod.docsiteassets.roblox.com/assets/publishing/cross-platform/ButtonX-Xbox.png) | | ![](https://prod.docsiteassets.roblox.com/assets/publishing/cross-platform/ButtonX-PS.png) | | ButtonX |
| [Enum.KeyCode.One](/docs/nl-nl/reference/engine/enums/KeyCode#One) | | n.v.t. | | n.v.t. | | 1 |
| [Enum.KeyCode.Five](/docs/nl-nl/reference/engine/enums/KeyCode#Five) | | n.v.t. | | n.v.t. | | 5 |

## [Gebruikersinterface](#gebruikersinterface)[](#gebruikersinterface)

Een goed ontworpen gebruikersinterface is essentieel voor spelers op alle platforms om met je spel te interageren.

### [Positie en grootte](#positie-en-grootte)[](#positie-en-grootte)

Zorg ervoor dat alle UI-elementen zichtbaar zijn op alle schermformaten en oriëntaties.

Zorg ervoor dat alle knoppen/bedieningen interactief zijn en dat ze niet worden geblokkeerd of verborgen door [apparaat uitsparingen of Roblox UI-elementen](/docs/nl-nl/ui/position-and-size#cross-platform-factoren) .

Alle UI-elementen moeten [gepositioneerd](/docs/nl-nl/ui/position-and-size#positie)  en [grootte](/docs/nl-nl/ui/position-and-size#grootte)  zijn om zichtbaarheid en interactiviteit over meerdere schermformaten te waarborgen. Het positioneren van UI-elementen met [Scale](/docs/nl-nl/reference/engine/datatypes/UDim#Scale)  is een veelgebruikte aanpak, aangezien het is gebaseerd op een percentage  van de X  en Y  grenzen van het scherm, niet op een pixelwaarde (pixels kunnen willekeurig variëren in zowel aantal als dichtheid tussen apparaten). Je kunt ook het [AnchorPoint](/docs/nl-nl/reference/engine/classes/GuiObject#AnchorPoint)  van het element gebruiken om de positionele oorsprong in te stellen. Bijvoorbeeld, de UI-container die de edelsteen/munt tellers in de volgende afbeelding vasthoudt, is gepositioneerd op een X  schaal van 1  (rechts) en Y  schaal van 0  (boven) met een bovenste-rechthoekige ankerpunt.

 ![](https://prod.docsiteassets.roblox.com/assets/publishing/cross-platform/Position-Scale.jpg)

[Scale](/docs/nl-nl/reference/engine/datatypes/UDim#Scale)  wordt ook aanbevolen voor grootte  van UI-elementen, zoals het maken van een UI-container die 75% breedte op elk scherm beslaat. Echter, 75% zou een enorme grootte renderen op 4K TV's voor console spelers, dus het wordt aanbevolen dat je [aanpassing van schermgrootte](#aanpassing-van-schermgrootte)  verkent als een manier om UI-indelingen aan te passen over verschillende weergaven.

### [Aanpassing van schermgrootte](#aanpassing-van-schermgrootte)[](#aanpassing-van-schermgrootte)

Pas UI aan verschillende weergaveformaten aan door te controleren en te luisteren naar wijzigingen in de viewport weergavegrootte.

Met een veelheid aan mogelijke schermformaten die toegankelijk zijn voor het Roblox-platform, leidt het vaak tot misinterpretatie om schermgrootte op pixels te voorspellen. Om te helpen bij het bepalen van de schermgrootte van een speler om de grootte/positie van UI-elementen aan te passen, biedt Roblox de alleen-lezen [ViewportDisplaySize](/docs/nl-nl/reference/engine/classes/GuiService#ViewportDisplaySize)  eigenschap die de intern gecategoriseerde rendergrootte van de viewport vertegenwoordigt.

| [ViewportDisplaySize](/docs/nl-nl/reference/engine/classes/GuiService#ViewportDisplaySize) | | Samenvatting |
| [Small](/docs/nl-nl/reference/engine/enums/DisplaySize#Small) | | De meeste tablet/mobiele/handheld apparaten |
| [Medium](/docs/nl-nl/reference/engine/enums/DisplaySize#Medium) | | De meeste laptops en monitoren |
| [Large](/docs/nl-nl/reference/engine/enums/DisplaySize#Large) | | De meeste TV's of groter |

Voor meer native aanpassing kun je de UI [Style Editor](/docs/nl-nl/ui/styling/editor)  gebruiken om [Style Queries](/docs/nl-nl/ui/styling/editor#stijl-queries)  voor zowel [ViewportDisplaySize](/docs/nl-nl/reference/engine/classes/GuiService#ViewportDisplaySize)  als [PreferredInput](/docs/nl-nl/reference/engine/classes/UserInputService#PreferredInput)  waarden te configureren. Het gebruik van intrinsieke selectors zoals @ViewportDisplaySizeSmall  of @PreferredInputTouch  stelt je in staat om je UI automatisch tokens te laten verwisselen voor tekstgroottes, containerafmetingen en andere metingen naarmate de apparaatomgeving of de primaire invoermethode van de speler verandert.

### [Lay-out containers](#lay-out-containers)[](#lay-out-containers)

Gebruik lay-outs om individuele UI-componenten te organiseren en zorg ervoor dat containers responsief aanpassen aan de kindelementen binnenin.

Voor een eenvoudigere organisatie van de UI moet je lay-outcomponenten  gebruiken om kinderen te organiseren. Wanneer je lay-out [containers](/docs/nl-nl/ui/frames)  gebruikt, zorg ervoor dat de kinderen leesbaar, [toegankelijk](#toegankelijkheid)  en niet rommelig zijn. Een veelvoorkomende lay-outcomponent is [UIListLayout](/docs/nl-nl/reference/engine/classes/UIListLayout) , die broeder [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  in rijen of kolommen positioneert en dienovereenkomstig aanpast telkens wanneer je een broederobject toevoegt of verwijdert.

Je moet ook de distributie en relatieve positionering van elementen binnen lay-outcontainers overwegen voor de beste gebruikerservaring. Het integreren van [flex](/docs/nl-nl/ui/list-flex-layouts#flex-layouts)  in een lijstlay-out is een krachtige manier om [gelijkmatig te vullen/distribueren](/docs/nl-nl/ui/list-flex-layouts#gelijkmatig-vullen-of-distribueren)  of [uit te lijnen/strekken](/docs/nl-nl/ui/list-flex-layouts#uitlijning)  items over hun lijn, of [flex specifieke items](/docs/nl-nl/ui/list-flex-layouts#flex-individuele-items)  over een variabele ruimte.

 ![UIListLayouts die de FillDirection illustreren van ofwel horizontaal of verticaal.](https://prod.docsiteassets.roblox.com/assets/engine-api/classes/UIListLayout/FillDirection.png)

### [Toegankelijkheid](#toegankelijkheid)[](#toegankelijkheid)

Zorg ervoor dat alle tekst leesbaar is op alle schermen. Zorg er ook voor dat alle UI [voldoende contrast](/docs/nl-nl/production/publishing/accessibility#kleurcontrast)  heeft en dat [niets uitsluitend op kleur vertrouwt](/docs/nl-nl/production/publishing/accessibility#kleurafhankelijkheid)  om een actie of uitkomst te onderscheiden.

Zelfs met UI-elementen [juist geconfigureerd](#positie-en-grootte)  over alle apparaatschermformaten, moet het algehele spel voldoen aan [toegankelijkheidsnormen](/docs/nl-nl/production/publishing/accessibility)  voor spelers met een verminderd gezichtsvermogen of kleurenblindheid. De tekstgrootte kan een grote rol spelen in de leesbaarheid van tekst-gebaseerde UI, dus je moet een [tekstgroottebeperking](/docs/nl-nl/ui/size-modifiers#tekstgrootte)  opnemen om ervoor te zorgen dat tekst niet onleesbaar (te klein) of visueel te groot wordt op grotere schermen zoals 4K TV's.

Voor meer tips over toegankelijkheid, zie [toegankelijkheidsrichtlijnen](/docs/nl-nl/production/publishing/accessibility) .

## [Laatste tips & trucs](#laatste-tips--trucs)[](#laatste-tips--trucs)

Terwijl je werkt aan een volledig cross‑platform spel, overweeg de volgende tips en trucs:

-

Apparaatemulatie is essentieel voor het ontwerpen van een optimaal spel op Roblox. Maak gebruik van de ingebouwde [Device Emulator](/docs/nl-nl/studio/testing-modes#device-emulation)  en [Controller Emulator](/docs/nl-nl/studio/testing-modes#controller-emulation)  om verschillende apparaten en gamepads direct in Studio te emuleren.

-

Roblox's [UI-styling](/docs/nl-nl/ui/styling)  pijplijn, vergelijkbaar met CSS, stelt je in staat om overrides voor UI-instantie-eigenschappen te declareren en wereldwijd toe te passen. Samen met de geïntegreerde [Style Editor](/docs/nl-nl/ui/styling/editor)  kun je een complete en eenvoudig aan te passen gebruikersinterface opzetten.

-

Zodra je spel effectief cross-platform is, verken native functies zoals haptische feedback op [mobiele](/docs/nl-nl/input/mobile#haptische-feedback)  en [gamepads](/docs/nl-nl/input/gamepad#haptische-feedback) , aanraakgebaren zoals [TouchSwipe](/docs/nl-nl/reference/engine/classes/UserInputService#TouchSwipe)  en [TouchPinch](/docs/nl-nl/reference/engine/classes/UserInputService#TouchPinch) , of versnellingsmeter en gyroscoopfunctionaliteit op [AccelerometerEnabled](/docs/nl-nl/reference/engine/classes/UserInputService#AccelerometerEnabled)  en [GyroscopeEnabled](/docs/nl-nl/reference/engine/classes/UserInputService#GyroscopeEnabled)  apparaten.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
