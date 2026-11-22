<!-- Source: https://create.roblox.com/docs/nl-nl/studio/controller-emulator -->

Controller Emulator | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Studio](/docs/nl-nl/studio)
4. /
5. [Device Simulator](/docs/nl-nl/studio/device-simulator)

# Controller Emulator

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Controller Emulator  is een widget in Roblox Studio die de apparaten emuleert die spelers gebruiken om jouw ervaring te besturen: gamepads, VR-headsets en controllers, handhelds en TV-afstandsbedieningen. Het toont een afbeelding van het apparaat dat je kiest, verzendt echte invoerevenementen wanneer je erop klikt of een toegewezen toets indrukt, en verlicht de bedieningselementen wanneer er invoer binnenkomt, zodat je een gamepad-eerste besturingsschema of een VR-interactie kunt testen zonder dat je deze bezit.

Het emuleren van invoer is gescheiden van het simuleren van een apparaat. [Device Simulator](/docs/nl-nl/studio/device-simulator)  verandert het scherm, het platform en de hardware waarvan jouw ervaring gelooft dat het erop draait. Controller Emulator verandert wat erin is aangesloten. De twee worden meestal samen gebruikt.

## [Open Controller Emulator](#open-controller-emulator)[](#open-controller-emulator)

Of:

1.

Klik op Virtuele controller  in de werkbalk van de Device Simulator, of

2.

Klik op Controller  in het tabblad Emulatie  van de werkbalk.

De widget vereist een open plaats. Terwijl je in een playtest bent, verbindt het openen van de widget het geëmuleerde apparaat en het sluiten ervan ontkoppelt het, zodat je de controller halverwege de sessie kunt in- en uitpluggen.

## [Emuleer een apparaat](#emuleer-een-apparaat)[](#emuleer-een-apparaat)

De dropdown bovenaan de widget selecteert het apparaat dat je wilt emuleren.

 ![Controller Emulator toont Quest 3-controllers, toetsenbordtoewijzingen en bedieningselementen voor het bewegen van de headset en controllers.](https://prod.docsiteassets.roblox.com/assets/studio/device-simulator/controller-emulator-vr-input.png)

| Apparaat | | Emuleert |
| --- | --- |
| Generieke Gamepad | | Een gamepad zonder specifieke knopbenamingen van een leverancier. |
| PS4 | | Een PlayStation 4-controller. |
| PS5 | | Een PlayStation 5-controller. |
| Xbox | | Een Xbox-controller. |
| Generieke Handheld | | Een handheld PC met ingebouwde bedieningselementen. |
| TV Afstandsbediening | | Een Android TV-afstandsbediening, inclusief het richtpad en de centrale en terugknoppen. |
| Quest2 / Quest3 | | Meta Quest-headsets en controllers. |

Jouw ervaring ziet het bijbehorende gamepadtype, zodat code die vertakt op [Enum.GamepadType](/docs/nl-nl/reference/engine/enums/GamepadType)  of de knoppenset van een controller leest, zich gedraagt zoals het zou doen met het echte apparaat aangesloten.

## [Stuur invoer](#stuur-invoer)[](#stuur-invoer)

Invoer kan uit drie plaatsen komen, en de widget toont wat van elk van hen is aangekomen: terwijl invoer wordt ontvangen, inclusief van een echte controller die je hebt aangesloten, wordt de bijbehorende bediening op de afbeelding van het apparaat gemarkeerd. Dat is de snelste manier om te bevestigen dat de invoer die jouw ervaring heeft ontvangen, de invoer is die je bedoelde te verzenden.

### [Apparaatbedieningselementen](#apparaatbedieningselementen)[](#apparaatbedieningselementen)

Knoppen, triggers en thumbsticks op de afbeelding van het apparaat zijn interactief. Klik of sleep ze om invoer te verzenden. Triggers en thumbsticks rapporteren analoge waarden, niet alleen ingedrukt en losgelaten, zodat je een gedeeltelijke trek of een langzame stickbeweging kunt testen.

### [Toetsenbord](#toetsenbord)[](#toetsenbord)

Terwijl de widget focus heeft, wordt toetsenbordinvoer doorgestuurd naar het geëmuleerde apparaat met behulp van de huidige toewijzingen. Dit is wat je in staat stelt om een besturingsschema met snelheid te testen, met beide handen, zoals een speler het zou gebruiken. Zie [Bewerk toewijzingen](#bewerk-toewijzingen)  om te veranderen welke toets welk bedieningselement aanstuurt.

### [Headset- en handposes](#headset--en-handposes)[](#headset--en-handposes)

VR heeft geen enkele controle om op te klikken. De invoer is een hoofdpose en twee handposes, dus wanneer een VR-apparaat wordt geëmuleerd, voegt de widget bedieningselementen toe voor het bewegen ervan.

Headset , Linker Controller  en Rechter Controller  hebben elk een schakelaar. Geactiveerde delen reageren op jouw toetsenbord en muis, en gedeactiveerde delen blijven stil. Het onafhankelijk bewegen van het hoofd en één hand is wat je in staat stelt om te testen of een interactie afhankelijk is van waar de speler naar kijkt.

| Actie | | Invoer |
| Bewegen | | Shift + W / A / S / D |
| Vlieg omhoog/omlaag | | Shift + E / Q |
| Draaien | | Muisklik |
| Kantelen | | Rechtermuisklik + muisklik |
| Wissel controllers | | Shift + Links / Rechts |
| Schakel cursorvergrendeling in/uit | | Alt + 1 |
| Schakel muisimulatie in/uit | | Alt + Esc |

Klik op de 3D-weergave om te interageren met de VR-scène.

Vertalingsgevoeligheid  schaalt hoe ver de geactiveerde delen bewegen per toetsdruk, van 1 tot 10. Verlaag het wanneer je een hand tegen een klein doelwit plaatst, en verhoog het om door de scène te navigeren. Posities resetten  brengt het hoofd en beide handen terug naar hun standaardpose tijdens een playtest, wat de snelste manier is om uit een pose te komen waar je niet handmatig uit kunt komen.

## [Bewerk toewijzingen](#bewerk-toewijzingen)[](#bewerk-toewijzingen)

Elk geëmuleerd apparaat heeft zijn eigen toetsenbordtoewijzingen, zodat W  iets anders kan betekenen op een gamepad dan op een TV-afstandsbediening. Klik op Bewerk toewijzingen  om de toewijzingseditor te openen, die de afbeelding van het apparaat toont met elk bedieningselement gelabeld door de toets die momenteel aan het is toegewezen.

 ![Controller Emulator toewijzingseditor toont de toetsenbordtoets die aan elk gamepadbedieningselement is toegewezen.](https://prod.docsiteassets.roblox.com/assets/studio/device-simulator/controller-emulator-mappings.png)

Om een bedieningselement opnieuw toe te wijzen, klik je op het label, en druk je op de toets of toetsen die je eraan wilt toewijzen. Wanneer je met de muis over een label beweegt, wordt het bedieningselement dat het aanstuurt op de afbeelding gemarkeerd, zodat je kunt zien welk fysiek bedieningselement je op het punt staat opnieuw toe te wijzen.

-

Als de toets die je indrukt al aan een ander bedieningselement is toegewezen, wordt de oudere toewijzing verwijderd en krijg je een waarschuwing te zien welke dat is, in plaats van stilletjes twee bedieningselementen op één toets te laten staan.

-

Opslaan  bevestigt je wijzigingen aan het apparaat.

-

Herstel standaardinstellingen  brengt het apparaat terug naar zijn oorspronkelijke toewijzingen, na een bevestiging.

Toewijzingen worden per apparaat opgeslagen en blijven behouden tussen sessies.

## [Koppel met de Device Simulator](#koppel-met-de-device-simulator)[](#koppel-met-de-device-simulator)

Controller Emulator volgt het apparaat dat je simuleert. Het selecteren van een console, headset, handheld of Android TV-apparaat in [Device Simulator](/docs/nl-nl/studio/device-simulator)  schakelt Controller Emulator over naar de bijbehorende controller, zodat de gesimuleerde hardware en de geëmuleerde invoer consistent blijven zonder dat je beide hoeft in te stellen.

## [Voorbeeldwerkstromen](#voorbeeldwerkstromen)[](#voorbeeldwerkstromen)

-

Test een gamepad-eerste besturingsschema.  Simuleer een console in Device Simulator en zijn controller hier, en stuur je ervaring volledig vanaf de geëmuleerde pad. Alles wat je niet kunt bereiken is een gat in je gamepad-navigatie.

-

Bevestig dat invoer aankomt.  Kijk naar de afbeelding van het apparaat terwijl je speelt. Als een bedieningselement niet oplicht, ligt het probleem boven jouw invoerafhandeling.

-

Test analoge drempels.  Sleep een trigger of thumbstick langzaam en controleer waar jouw dode zones en activeringsdrempels daadwerkelijk afgaan.

-

Test een VR-interactie één hand tegelijk.  Deactiveer de headset en één controller, en beweeg de overgebleven hand in positie om bereik, grijppunten en of de interactie afhankelijk is van de blik te controleren.

-

Test TV-afstandsbediening navigatie.  Simuleer een Android TV-apparaat en bevestig dat jouw UI volledig navigeerbaar is met een richtpad, een centrale knop en een terugknop.

-

Valideer aangepaste toewijzingen.  Herbind de bedieningselementen die je het meest gebruikt en speel met het toetsenbord, wat sneller is dan op de afbeelding klikken voor alles wat met timing te maken heeft.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
