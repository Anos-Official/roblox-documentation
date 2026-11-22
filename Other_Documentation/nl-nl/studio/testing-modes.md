<!-- Source: https://create.roblox.com/docs/nl-nl/studio/testing-modes -->

Studio testmodi | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Studio](/docs/nl-nl/studio)

# Studio testmodi

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Vanwege het onderliggende [client-server model](/docs/nl-nl/projects/client-server)  van de Roblox Engine is het belangrijk dat je je game in verschillende modi test voordat je deze [publiekelijk vrijgeeft](/docs/nl-nl/production/publishing/publish-games-and-places#breng-games-uit) . Alle testopties zijn toegankelijk in het linker gedeelte van de mezzanine.

 ![Testbedieningen aangegeven in de mezzanine van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Controls.png)

## [Spelen testen](#spelen-testen)[](#spelen-testen)

Er zijn drie veelvoorkomende opties voor het testen van een game. Kies de gewenste optie uit het dropdownmenu en klik op de Speel -knop ernaast om de playtest te starten.

 ![Testoptie in het dropdownmenu van testmodi in de mezzanine van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Mode-Test.png)

| Modus | | Sneltoets | | Beschrijving |
| --- | --- |
| Test | | F5 | | Begint met het simuleren van de game, waarbij je avatar wordt geplaatst bij een [SpawnLocation](/docs/nl-nl/reference/engine/classes/SpawnLocation)  of coördinaten rond (0, 100, 0) . |
| Test Hier | |  | | Begint met het simuleren van de game, waarbij je avatar voor de huidige positie van de camera wordt geplaatst. |
| Uitvoeren | | F8 | | Begint met het simuleren van de game, maar plaatst je avatar niet. De simulatie begint bij de huidige camerastand en je kunt navigeren met de Studio camera besturingselementen. |

Zodra een playtest actief is, worden er extra opties beschikbaar in de mezzanine.

 ![Extra opties beschikbaar tijdens een playtest vanuit de mezzanine van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Options.png)

| Actie | | Sneltoets | | Beschrijving |
| Pauze  / Hervatten | |  | | Laat je [pauzeren/hervatten van fysica en animaties](#pauzehervatten) . |
| Stop | | Shift F5 | | Stop de simulatie van de game en reset alle objecten en instanties naar hoe ze waren voordat de playtest begon. |
| Client  / Server | |  | | Tijdens het spelen in een "solo" modus (Test  of Test Hier ) schakelt het tussen Client -modus en Server -modus. Zie [schakel client/server](/docs/nl-nl/studio/testing-modes#schakel-clientserver)  voor details. |

### [Schakel client/server](#schakel-clientserver)[](#schakel-clientserver)

Wanneer je test in de Test  of Test Hier  modus, draait Studio twee aparte simulaties — één [client](/docs/nl-nl/projects/client-server#client)  simulatie en één [server](/docs/nl-nl/projects/client-server#server)  simulatie — die een nauwkeuriger beeld kunnen geven van hoe de game in productie zal functioneren.

Tijdens solo playtesting kun je schakelen tussen Client  en Server  modi door op de Client/Server  schakelknoop te klikken. Wanneer je schakelt, verandert de knop om de huidige simulatiemodus weer te geven.

![](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Client.png) Client

![](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Server.png) Server

Afhankelijk van de simulatiemodus verandert de controle over je karakter en de camera als volgt:

Client Modus Server Modus

![](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Client-Server-Toggle-3D-Client.jpg) In Client  modus is het 3D-venster omringd door een blauwe  rand en de simulatie gebruikt je karakterbesturing en camera-instellingen. Deze testmodus is een nauwkeurige simulatie van de game die draait op de Roblox-applicatie, zonder meerdere spelers.

Binnen de [Explorer](/docs/nl-nl/studio/explorer)  vensterhiërarchie bestaan bepaalde objecten alleen in hun verwachte containers.

![Explorer-venster dat items toont die alleen op de client bestaan](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Client-Server-Toggle-Explorer-Client.png) In Client  modus zijn de verwachte client-side objecten aanwezig in de hiërarchie, inclusief die gekopieerd van [StarterPack](/docs/nl-nl/reference/engine/classes/StarterPack)  naar de [Backpack](/docs/nl-nl/reference/engine/classes/Backpack)  van de speler en van [StarterPlayer](/docs/nl-nl/reference/engine/classes/StarterPlayer)  naar de [PlayerScripts](/docs/nl-nl/reference/engine/classes/PlayerScripts)  van de speler.

![Explorer-venster dat items toont die alleen op de server bestaan](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Client-Server-Toggle-Explorer-Server.png) In Server  modus zijn de verwachte server-side objecten aanwezig in de hiërarchie, inclusief scripts in [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService)  en objecten die je in [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage)  hebt geplaatst.

In het [Output](/docs/nl-nl/studio/output)  venster zijn berichten gelabeld als blauw  (client) of groen  (server), wat aangeeft of ze afkomstig zijn van de client of server. Voor berichten die zijn uitgevoerd vanuit [ModuleScripts](/docs/nl-nl/reference/engine/classes/ModuleScript) , wordt de labelkleur bepaald door of de module is aangeroepen vanuit een client-side [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  of vanuit een server-side [Script](/docs/nl-nl/reference/engine/classes/Script) .

 ![Output-venster dat een groene label voor serveroutput en een blauwe label voor clientoutput toont](https://prod.docsiteassets.roblox.com/assets/studio/general/Output-Window-Client-Server-Labels.png)

### [Pauze/hervatten](#pauzehervatten)[](#pauzehervatten)

Tijdens solo playtesting is de Pauze/Hervatten  knop nuttig voor het debuggen van tijdelijke scènes en mechanismen, zonder de rendering uit te schakelen.

 ![Pauze/Hervatten knop aangegeven in de mezzanine van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Pause.png)

Standaard heeft pauzeren en hervatten effect op zowel de client als  de server. Als je alleen de client of  server wilt pauzeren of hervatten:

1.

Stel de [client/server-schakelaar](#schakel-clientserver)  in op basis van welke simulatie je wilt pauzeren/hervatten.

2.

Klik op de kleine pijl op de Pauze/Hervatten  knop en selecteer de alternatieve optie Pauze/Hervatten Client  of Pauze/Hervatten Server . Door op de knop te klikken, pauzeer of hervat je alleen die kant van de simulatie.

Wanneer de simulatie is gepauzeerd, kun je vooruit stappen  met 1/60ste van een seconde (60 Hz) door op de Stap Vooruit  knop te klikken. Net als de Pauze/Hervatten  knop aan de linkerkant, laat klikken op de kleine pijl je stappen selecteren voor alleen de client of  server op basis van de [client/server-schakelaar](#schakel-clientserver) .

 ![Stap Vooruit knop aangegeven in de mezzanine van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Step-Forward.png)

Let op de volgende technische details met betrekking tot pauzeren/hervatten:

-

Hoewel [Animations](/docs/nl-nl/reference/engine/classes/Animation)  niet op fysica zijn gebaseerd, pauzeren deze werkbalkknoppen ook animaties.

-

Pauzeren of hervatten heeft geen effect op draaiende scripts.

-

Alleen de [RunService](/docs/nl-nl/reference/engine/classes/RunService)  callbacks [PreAnimation](/docs/nl-nl/reference/engine/classes/RunService#PreAnimation) , [PreSimulation](/docs/nl-nl/reference/engine/classes/RunService#PreSimulation) , [PostSimulation](/docs/nl-nl/reference/engine/classes/RunService#PostSimulation) , en [Stepped](/docs/nl-nl/reference/engine/classes/RunService#Stepped)  pauzeren of hervatten via deze werkbalkknoppen. Andere callbacks ([PreRender](/docs/nl-nl/reference/engine/classes/RunService#PreRender) , [Heartbeat](/docs/nl-nl/reference/engine/classes/RunService#Heartbeat) , en [RenderStepped](/docs/nl-nl/reference/engine/classes/RunService#RenderStepped) ) blijven doorgaan, waardoor de normale functionaliteit van camerascripts, gerenderde visualisaties en plugins behouden blijft.

## [Multi-client simulatie](#multi-client-simulatie)[](#multi-client-simulatie)

De Server & Clients  optie in het dropdownmenu laat je meerdere sessies van Studio starten, één als de server en de andere als client. Deze testmodus is een waardevol hulpmiddel om te vergelijken hoe een client "andere" clients binnen de game ziet.

1.

Met de Server & Clients  optie geselecteerd in het dropdownmenu, kies je het aantal clientsessies om te testen. Gewoonlijk zijn 1–2 clients voldoende, hoewel je tot acht kunt simuleren.

 ![Server & Clients optie in het dropdownmenu van testmodi in de mezzanine van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Mode-Server-Clients.png)

2.

Druk op de Speel -knop of F7  om de client-server simulatie te starten.

3.

Wanneer je klaar bent met testen, druk je op de Eind Sessies  knop vanuit een van de simulatiesessies om alle gesimuleerde clients en de gesimuleerde server te sluiten.

 ![Eind Sessie aangegeven in de mezzanine van Studio](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-End-Session.png)

## [Feest simulatie](#feest-simulatie)[](#feest-simulatie)

De Feest Simulator  stelt je in staat om games te testen en te debuggen die gebruik maken van feestgerelateerde API's direct binnen Studio, zonder dat je hoeft te publiceren en meerdere apparaten te coördineren. Dit hulpmiddel stelt je in staat om feesten te configureren en te emuleren voor testspelers in je [Server & Clients](#multi-client-simulatie)  playtests.

Tijdens het spelen test, wijst de Feest Simulator automatisch alle testspelers toe aan de geconfigureerde gesimuleerde feesten.

 ![Feest Emulator die gesimuleerde feesten en verschillende toewijzingsopties weergeeft](https://prod.docsiteassets.roblox.com/assets/studio/general/Party-Simulator.png)

Als de Feest Simulator is ingeschakeld:

-

Elke [Player.PartyId](/docs/nl-nl/reference/engine/classes/Player#PartyId)  eigenschap weerspiegelt de toewijzingen van de Feest Simulator.

-

[SocialService:GetPartyAsync()](/docs/nl-nl/reference/engine/classes/SocialService#GetPartyAsync)  retourneert een gesimuleerde tabel van feestgegevens.

-

[SocialService:GetPlayersByPartyId()](/docs/nl-nl/reference/engine/classes/SocialService#GetPlayersByPartyId)  retourneert een lijst van [Player](/docs/nl-nl/reference/engine/classes/Player)  instanties die zijn toegewezen aan de opgegeven [Player.PartyId](/docs/nl-nl/reference/engine/classes/Player#PartyId) .

Je kunt het aantal lokale testspelers op elk moment aanpassen met de [Server & Clients](#multi-client-simulatie)  instelling van Studio. Wanneer het aantal testspelers verandert, werkt de emulator automatisch bij om spelers in de configuratie op te nemen of te verwijderen.

## [Samenwerkend testen](#samenwerkend-testen)[](#samenwerkend-testen)

Als je aan een game werkt met anderen in [samenwerkings](/docs/nl-nl/projects/collaboration)  modus, kun je testen met andere medewerkers als volgt:

1.

Selecteer Team Test  in het dropdownmenu en druk op de Speel -knop om een nieuwe Studio-sessie te openen met je karakter ingevoegd.

 ![Team Test optie in het dropdownmenu van testmodi in de mezzanine van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Mode-Team-Test.png)

2.

Andere medewerkers kunnen zich dan aansluiten door op de Speel -knop vanuit de mezzanine in hun Studio-sessie te drukken.

Slechts één team test sessie kan op elk moment draaien. Om een sessie te sluiten en alle testers eruit te zetten, klik je op de Eind Sessie  knop.

### [Medewerker logs](#medewerker-logs)[](#medewerker-logs)

Tijdens een Team Test wordt de clientoutput van elke medewerker gedeeld met de sessie, zodat je team samen kan debuggen. Alleen clientoutput wordt gedeeld, en alleen terwijl een medewerker in de Team Test is; het verlaten van de Team Test stopt het delen.

1.

Klik op de contextfilter dropdown bovenaan het Output  venster. Een Bronnen  sectie toont iedereen in de sessie.

2.

Vink een naam aan om de output van die medewerker te tonen, of vink Alle  aan om iedereen te tonen, inclusief mensen die later aansluiten. Hun berichten verschijnen met hun naam ervoor, zoals [builderman] 12 vijanden geladen .

Let op de volgende gedragingen:

-

Niemand wordt getoond wanneer een Team Test begint. Je eigen output wordt nooit beïnvloed door wie je selecteert in Bronnen ; het blijft volgen je gebruikelijke context- en berichttypefilters.

-

De Remote Client  optie in de contextfilter toont of verbergt de output van alle anderen tegelijk, apart van je eigen Client  output.

-

Berichttypefilters (Output , Info , Waarschuwing , Fout ) en de tekstfilter zijn ook van toepassing op de berichten van medewerkers.

-

Wanneer de Team Test eindigt, herstelt Studio de output die je had voordat de sessie begon.

-

De Bronnen  sectie toont alleen de clientoutput van medewerkers, niet de output van de Team Test server.

Scripts, plugins en commandobalkcode kunnen ook de recente loggeschiedenis van een medewerker lezen met [LogService:GetLogHistoryAsync()](/docs/nl-nl/reference/engine/classes/LogService#GetLogHistoryAsync) , waarbij je de [Player.User](/docs/nl-nl/reference/engine/classes/Player#User)  van de medewerker doorgeeft. Om de loggeschiedenis van de Team Test server te lezen, geef je User.fromId(0)  door. Deze methode werkt alleen tijdens een Team Test (het is uitgeschakeld in solo playtesting en live games), retourneert tot de 512 meest recente berichten in hetzelfde formaat als [LogService:GetLogHistory()](/docs/nl-nl/reference/engine/classes/LogService#GetLogHistory) , en yield. Het haalt logs op via het netwerk en kan fouten geven, dus wikkel aanroepen in pcall .

```

local LogService = game:GetService("LogService")

local Players = game:GetService("Players")

for _, player in Players:GetPlayers() do

	local ok, history = pcall(LogService.GetLogHistoryAsync, LogService, player.User)

	if not ok then

		warn(`Kon de logs van {player.Name} niet lezen: {history}`)

		continue

	end

	for _, entry in history do

		if entry.messageType == Enum.MessageType.MessageError then

			print(`[{player.Name}] {entry.message}`)

		end

	end

end

-- De loggeschiedenis van de Team Test server

local ok, serverHistory = pcall(LogService.GetLogHistoryAsync, LogService, User.fromId(0))

if ok then

	print(`De server heeft {#serverHistory} logentries`)

end

```

## [Apparaatsimulatie](#apparaatsimulatie)[](#apparaatsimulatie)

Gebruik [Device Simulator](/docs/nl-nl/studio/device-simulator)  om een preview te krijgen van hoe jouw ervaring eruitziet en zich gedraagt op een apparaat dat je niet voor je hebt, inclusief de schermafmetingen, pixel dichtheid, on-screen toetsenbord en aanraakinvoer. Device Simulator werkt samen met [Controller Emulator](/docs/nl-nl/studio/controller-emulator)  om de gamepads, VR-controllers, handhelds en TV-afstandsbedieningen te emuleren die spelers gebruiken om jouw ervaring te besturen.

## [Netwerksimulatie](#netwerksimulatie)[](#netwerksimulatie)

Gebruik [Network Simulator](/docs/nl-nl/studio/network-simulator)  om latentie, jitter en pakketverlies toe te voegen aan Studio [playtest](#spelen-testen)  verbindingen en om de netwerkcondities te reproduceren die spelers tegenkomen op bedrade, Wi-Fi en mobiele verbindingen. Dit is vooral nuttig voor het testen van games die gebruik maken van [Server Authority](/docs/nl-nl/projects/server-authority) , aangezien voorspelling en rollback/her-simulatie mechanismen gevoelig zijn voor netwerkomstandigheden, en voor het testen van [UnreliableRemoteEvents](/docs/nl-nl/reference/engine/classes/UnreliableRemoteEvent) , die mogelijk verloren gaan of in de verkeerde volgorde aankomen.

## [Gescripte testen](#gescripte-testen)[](#gescripte-testen)

Naast de interactieve testtools hierboven, biedt Studio services die je in staat stellen om testen programmatisch aan te sturen vanuit een plugin of build-pijplijn. Alle drie de services zijn alleen voor Studio en doen niets wanneer ze worden uitgevoerd in een gepubliceerde ervaring.

| Service | | Doel |
| [StudioDeviceSimulatorService](/docs/nl-nl/reference/engine/classes/StudioDeviceSimulatorService) | | Scriptable [apparaatsimulatie](/docs/nl-nl/studio/device-simulator) . Blader door apparaatsjablonen, schakel het actieve apparaat, overschrijf resolutie en DPI, controleer oriëntatie en schaling, en maak aangepaste apparaatsprofielen die op schijf worden opgeslagen. |
| [StudioTestService](/docs/nl-nl/reference/engine/classes/StudioTestService) | | Programmatic [multi-client simulatie](#multi-client-simulatie) . Start een server met tot 8 gesimuleerde clients, voeg spelers toe tijdens de sessie, geef argumenten door aan de test, trigger clientontkoppelingen en beëindig tests vanuit de server. |
| [VirtualInput](/docs/nl-nl/reference/engine/classes/VirtualInput) | | Gesimuleerde muis-, toetsenbord- en pointergebeurtenissen die precies zoals echte hardware-invoer worden verwerkt. Verkrijg een instantie van [UserInputService:CreateVirtualInput()](/docs/nl-nl/reference/engine/classes/UserInputService#CreateVirtualInput) . |

Deze services maken cross-device multiplayer testen mogelijk (door te cyclusen door apparaatsprofielen en een multiplayer test bij elk te starten), stress testen van spelers die zich aansluiten/afmelden, regressietesten van oriëntatie en end-to-end UI flow automatisering.

## [VR-headsets](#vr-headsets)[](#vr-headsets)

Als je ondersteuning wilt bieden voor virtual reality (VR) headsets voor je game, zorg er dan voor dat je VR in Studio test of [emuleert](#vr-emulatie) .

### [VR-emulatie](#vr-emulatie)[](#vr-emulatie)

VR-emulatie  stelt je in staat om VR-games in Studio te testen zonder een fysieke headset. Net als bij het emuleren van elk ander apparaat, gebruik je [Device Simulator](/docs/nl-nl/studio/device-simulator)  om een Headset  apparaat te kiezen, zoals Meta Quest 2  of Meta Quest 3 . [Controller Emulator](/docs/nl-nl/studio/controller-emulator)  selecteert automatisch de juiste controller voor de headset.

![De Controller Emulator met een Quest 3-controller.](https://prod.docsiteassets.roblox.com/assets/studio/general/Controller-Emulator-VR.png)

![Emulator met een Quest 3-emulatie.](https://prod.docsiteassets.roblox.com/assets/studio/general/Emulator-Viewport-VR.jpg)

De combinatie van een headset en meerdere controllers, elk met bewegingsdetectie, maakt VR-emulatie complexer:

-

Voor bewegingsdetectie-emulatie, druk op Alt 1  (⌥ 1 ) om de muis te vergrendelen en te ontgrendelen van het venster.

-

Gebruik Shift ←  of Shift →  om te schakelen tussen veelvoorkomende combinaties van de headset, de linker controller en de rechter controller. Bijvoorbeeld, je kunt de Headset  optie gebruiken om om je heen te kijken terwijl je vooruit loopt met de knop van de linker controller, maar dan overschakelen naar de Rechter Controller  wanneer je bewegingsbesturingen moet gebruiken om op een doel te richten.

### [Headsetconfiguratie](#headsetconfiguratie)[](#headsetconfiguratie)

Studio ondersteunt testen voor alle VR-headsets die compatibel zijn met [OpenXR](https://www.khronos.org/openxr/) , de open-source industriestandaard die toegang biedt tot VR.

Momenteel wordt testen in VR alleen ondersteund op Windows.

Om Studio testen in VR in te schakelen, moet je je headset op je pc aansluiten en de OpenXR-runtime voordat  je Studio start configureren. Als je Studio al hebt gestart, sluit het dan af en voltooi eerst de configuratiestappen.

Als je maar één VR-headset hebt, configureert het installeren van de bijbehorende VR-app automatisch de runtime voor je. Als je meerdere headsets hebt, moet je de runtime handmatig instellen en ervoor zorgen dat je alleen  de headset configureert die je wilt gebruiken voor testen.

De volgende stappen zijn voor de twee meest voorkomende VR-apps:

-

SteamVR voor headsets zoals de HTC Vive en Valve Index.

-

Oculus voor headsets zoals de Meta Quest en Oculus Rift.

Steam VR Oculus VR

1.

Installeer en open de SteamVR-app op je computer.

2.

Onder SteamVR-instellingen , selecteer het tabblad Ontwikkelaar . Selecteer vervolgens Geavanceerde instellingen weergeven .

3.

Stel SteamVR in als OpenXR-runtime.

4.

Zet de controllers aan door op de Systeem  knop te drukken totdat je een piep hoort.

-

Om de controller uit te schakelen, houd je de Systeem  knop ingedrukt totdat je hetzelfde piepgeluid hoort.

Als je de stappen correct volgt, zouden de statusiconen op de SteamVR-app en de statuslampjes op de hardware allemaal groen moeten zijn, wat aangeeft dat de configuratie is voltooid.

Wanneer je de SteamVR-app afsluit, schakelen de controllers automatisch uit. De controllers schakelen ook automatisch uit na een periode van inactiviteit.

### [Roblox Quest-app](#roblox-quest-app)[](#roblox-quest-app)

Je kunt je game testen in de Roblox-app op Quest zonder je headset aan je computer te koppelen. Gebruik de volgende stappen om toegang te krijgen tot je game op je headset in deze modus:

1.

In Studio, [publiceer je game](/docs/nl-nl/production/publishing/publish-games-and-places#publiceer-games) .

2.

Gebruik je [Creator Dashboard](https://create.roblox.com/dashboard/creations)  of de link in Studio om de gamepagina in je webbrowser te openen.

3.

Voeg de game op de gamepagina toe aan je favorieten door op het Favoriet -icoon te klikken.

4.

Gebruik je headset om de standalone Roblox-app te openen.

5.

Scroll naar beneden naar de Favorieten  sectie op de startpagina en speel je game.

### [Studio VR-modus](#studio-vr-modus)[](#studio-vr-modus)

Na het [configureren van je headset](#headsetconfiguratie) , kun je de Studio VR-testmodus inschakelen via de volgende stappen:

1.

In het Bestand  menu, selecteer Studio-instellingen .

2.

Selecteer Rendering .

3.

Zet onder Algemene  instellingen VR-modus inschakelen  aan.

Je kunt nu je game testen met je VR-headset met behulp van een van de beschikbare [playtestopties](#spelen-testen) . Tijdens een VR-testsessie, als de kabel van je headset losraakt of je de Roblox Studio Beta-app op de headset sluit, moet je Studio opnieuw opstarten om de test opnieuw uit te voeren.

## [Speleremulatie](#speleremulatie)[](#speleremulatie)

Voor gedetailleerde emulatie van game [lokalisatie](/docs/nl-nl/production/localization)  en inhoudsbeleid, kun je testen via de Speler Emulator , toegankelijk vanuit het Test  menu van Studio.

Met het emulatorvenster open, schakel je Testprofiel inschakelen  in. Emulatie blijft ingeschakeld (geactiveerd of gedeactiveerd) zelfs als je het venster sluit.

Verder naar beneden in het venster zijn veelgebruikte opties:

| Optie | | Beschrijving |
| Locale | | Laat je een [gelokaliseerde](/docs/nl-nl/production/localization)  taal emuleren tijdens het playtesten. |
| Pseudolocalize | | Vervangt karakters door vergelijkbare maar iets andere karakters, zodat het gemakkelijk is om te identificeren welke strings door het [vertalingssysteem](/docs/nl-nl/production/localization)  gaan. Dit inschakelen helpt je om ongelokaliseerde  tekst te identificeren zonder de emulatie-taal te hoeven veranderen. Bijvoorbeeld:
-

Bloxy Cola  ⟩ ßℓôж¥ Çôℓá

-

Dominus Empyreus  ⟩ Ðô₥ïñúƨ É₥ƥ¥řèúƨ

 |
| Elongate | | Verlengt tekststrings met een factor die via de schuifregelaar is gedefinieerd. Bijvoorbeeld:
-

Bloxy Cola  ⟩ Bloooxyy Coolaa  (50% langer)

-

Dominus Empyreus  ⟩ Doomiinuus Eempyyreus  (30% langer)

Het gebruik van verlenging helpt je om plaatsen te identificeren waar je gebruikersinterfaces mogelijk niet in staat zijn om tekst te verwerken die langer is dan de standaard vertaalde tekst. Let op dat Spaans gemiddeld 30% langer is dan Engels en het equivalent voor Duits zelfs langer is. Let ook op dat dit alleen van invloed is op tekst die door het [vertalingssysteem](/docs/nl-nl/production/localization)  gaat. |
| Regio | | Laat je het land/regio van een speler emuleren tijdens het playtesten; deze selectie kan invloed hebben op andere schakelaars en selectievakjes in het venster zoals uiteengezet in [GetPolicyInfoForPlayerAsync()](/docs/nl-nl/reference/engine/classes/PolicyService#GetPolicyInfoForPlayerAsync) . |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
