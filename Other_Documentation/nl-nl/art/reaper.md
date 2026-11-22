<!-- Source: https://create.roblox.com/docs/nl-nl/art/reaper -->

Reaper | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Assets](/docs/nl-nl/assets)
4. /
5. Software van derden

# Reaper

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Reaper is een Digital Audio Workstation (DAW) met een breed scala aan audio-bewerkingshulpmiddelen waarmee je audio-streams kunt maken, manipuleren en exporteren. Het draait op Linux-, macOS- en Windows-systemen en deze cross-platform applicatie is een populaire keuze voor makers die aangepaste muziek en geluidseffecten voor Roblox-spellen willen maken.

Hoewel dit geenszins een uitputtende lijst is, biedt de volgende gids hoog niveau informatie over essentiële Reaper-tools en functies voor audio-bewerking, evenals richtlijnen voor best practices voor het ontwerpen van audio-bestanden voor Studio.

De gratis proefmodus van Reaper is volledig functioneel en uitbreidbaar, zodat je de software kunt uitproberen en kunt zien of je een licentie wilt kopen voor gebruik in commerciële projecten.

Om de nieuwste versie van Reaper te downloaden, ga naar [Reaper.fm](https://www.reaper.fm/download.php) .

## [Basisprincipes](#basisprincipes)[](#basisprincipes)

Voordat je kijkt naar alle gebruikelijke workflows voor het maken van aangepaste audio voor Studio, laten we de fundamentele interface-elementen van Reaper bekijken die belangrijk zijn voor het navigeren door de applicatie en het vinden van de juiste menu's en bedieningselementen voor jouw specifieke audio-bewerkingsopdracht.

### [Werkbalk](#werkbalk)[](#werkbalk)

 ![Reaper's UI met de hoofdwerkbalk gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/reaper/Toolbar.png)

De Werkbalk  bevat verschillende tools waarmee je acties kunt uitvoeren die gebruikelijk zijn in de meeste audio-workflows, zoals:

-

Een project openen of opslaan.

-

Toegang krijgen tot de instellingen van je project.

-

Een metronoom inschakelen.

-

Ripple-bewerking configureren.

-

Het gedrag van audio-track snapping uitschakelen.

Naarmate je meer vertrouwd raakt met Reaper, kun je de Werkbalk aanpassen met extra commando's en acties voor je eigen workflows.

### [Trackbedieningspaneel](#trackbedieningspaneel)[](#trackbedieningspaneel)

 ![Reaper's UI met het Trackbedieningspaneel gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/reaper/TrackControlPanel.png)

Het Trackbedieningspaneel  regelt het gedrag van je audio-tracks, zoals het volume, de gain en de effecten van plugins voor elke track, evenals hun relaties met andere audio-tracks. Er is slechts één audio-track in de voorbeeldafbeelding, maar je kunt zoveel audio-tracks toevoegen als je nodig hebt voor je project.

### [Tijdlijn](#tijdlijn)[](#tijdlijn)

 ![Reaper's UI met de Tijdlijn gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/reaper/Timeline.png)

De Tijdlijn  meet de lengte van je project en biedt visuele markeringen om je te helpen hele of segmenten van audio-tracks ten opzichte van elkaar te positioneren. De Tijdlijn in de voorbeeldafbeelding meet tijd in zowel maten/ritmes als minuten/seconden, maar je kunt de eenheden van meting aanpassen aan je eigen projectvereisten.

### [Arrangeergebied](#arrangeergebied)[](#arrangeergebied)

 ![Reaper's UI met het Arrangeergebied gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/reaper/ArrangeArea.png)

Het Arrangeergebied  stelt je in staat om audio-tracks binnen je project te bekijken en te bewerken met behulp van de groene scrubber, ook wel de cursor genoemd. Dit gebied vertegenwoordigt de belangrijkste werkruimte voor audio-manipulatie.

### [Transportbalk](#transportbalk)[](#transportbalk)

 ![Reaper's UI met de Transportbalk gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/reaper/TransportBar.png)

De Transportbalk  stelt je in staat om audio-opnames en afspelen te regelen, zoals:

-

Naar het begin of het einde van een audio-track springen.

-

Extra audio opnemen.

-

De maatsoort, het tempo of de afspeelsnelheid aanpassen.

Het wordt aanbevolen om te experimenteren met sneltoetsen voor deze acties om je workflows efficiënter te maken.

### [Mixerbedieningspaneel](#mixerbedieningspaneel)[](#mixerbedieningspaneel)

 ![Reaper's UI met het Mixerbedieningspaneel gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/reaper/MixerControlPanel.png)

Het Mixerbedieningspaneel  biedt een andere manier om je tracks te bekijken. Het hebben van de volumemeters horizontaal in de mixer kan zorgen voor meer visuele duidelijkheid over welke elementen het luidst zijn in je arrangement, maar dit is simpelweg een visuele voorkeur. Alle functies van Reaper kunnen worden gebruikt met de mixer gesloten, en veel geluidontwerpers gebruiken deze weergave zelfs niet.

### [FX-plugins](#fx-plugins)[](#fx-plugins)

 ![Reaper's UI met het FX-plugins venster gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/reaper/FXPlugins.png)

Vergelijkbaar met plugins in Studio, stelt het Plugins-venster  je in staat om extra functies of functionaliteit aan Reaper toe te voegen om audio-bewerking en workflows gemakkelijker te maken. Reaper biedt meer dan 200 fx-plugins met de creatiesuite voor jouw gemak, en je kunt extra plugins van derden importeren.

## [Veelvoorkomende workflows](#veelvoorkomende-workflows)[](#veelvoorkomende-workflows)

Nu je weet hoe je door de gebruikersinterface navigeert, laten we eens nader kijken naar de meest voorkomende audio-bewerkingsworkflows waarmee je audio-streams voor Roblox-spellen kunt maken, manipuleren en exporteren.

Voor meer informatie over een van deze workflows, zie de officiële [Up and Running: A Reaper User Guide](https://www.reaper.fm/userguide.php)  documentatie.

### [Fade ins en outs maken](#fade-ins-en-outs-maken)[](#fade-ins-en-outs-maken)

In audio-ontwerp is het gebruikelijk om een klein gedeelte van een audio-bestand te knippen, en deze vervolgens in en uit te laten vervagen om de overgang van het geluid van begin tot eind te verzachten. Dit proces is belangrijk omdat omgevingsgeluiden in de echte wereld vaak niet abrupt beginnen en stoppen; als dat wel het geval was, zou het extreem schokkend aanvoelen.

Laten we bijvoorbeeld de volgende twee audioclips van een windvlaag bekijken; de eerste audioclip bevat fade ins en outs om het geluid natuurlijker te laten aanvoelen, terwijl de tweede de initiële snede behoudt. Terwijl je naar beide luistert, let op hoe de eerste clip realistisch aanvoelt, terwijl de andere abrupt aanvoelt. Zonder deze overgangen zou het geluid de onderdompeling van een speler in een spel verstoren.

|  | |  |
| --- | --- |
| Audio met overgangen | | Audio zonder overgangen |

Om fade ins en outs te maken:

1.

Importeer je audio-bestand.

1.

Selecteer een .mp3 , .ogg  of .wav  bestand op je computer.

2.

Sleep het audio-bestand naar het Arrangeergebied .

2.

Snijd het voorbeeld totdat je een gedeelte van het geluid hebt dat je in je spel wilt laten horen.

1.

Beweeg de muisaanwijzer over de linkerkant van je audio-bestand totdat je cursor verandert in een dubbelzijdige pijl.

2.

Klik en sleep het audio-voorbeeld naar waar je je fade in wilt laten beginnen.

3.

Op een vergelijkbare manier, klik en sleep de rechterkant van je audio-bestand naar waar je je fade out wilt laten eindigen.

3.

Laat het voorbeeld in en uit overgaan.

1.

Beweeg de muisaanwijzer over de bovenlinkerhoek van je audio-voorbeeld totdat je cursor verandert in een kromme pijl.

2.

Klik en sleep het audio-voorbeeld naar waar je je fade in wilt laten eindigen.

3.

Op een vergelijkbare manier, klik en sleep de bovenrechterhoek van je audio-voorbeeld naar waar je je fade out wilt laten beginnen.

4.

OPTIONEEL

 Wijzig het type van de overgangscurve.

1.

Klik met de rechtermuisknop op je fade in of out curve. Een pop-upmenu verschijnt met meerdere curve-types.

2.

Selecteer een nieuwe curve. Het geluid vervaagt in of uit volgens het nieuwe curve-type.

### [Audio comprimeren](#audio-comprimeren)[](#audio-comprimeren)

In audio-ontwerp verwijzen de dynamiek van een geluid naar het volume van het geluid en hoe dat volume in de loop van de tijd verandert. Bijvoorbeeld:

-

Het geluid van een explosie is dynamisch  omdat het extreem luid begint en vervolgens in enkele seconden vervaagt naar een stille echo.

-

Het geluid van een waterval is niet-dynamisch  omdat, zelfs als je de waterval enkele minuten zou opnemen, het waarschijnlijk ongeveer hetzelfde volume zou blijven.

Hoewel beide voorbeelden hun tijd en plaats in projecten hebben, stelt het comprimeren van audio je in staat om het dynamische bereik van een geluid te verminderen door het volume van luide pieken binnen een bepaalde verhouding te verlagen. Dit resulteert in de luidste delen van een geluid die meer vergelijkbaar worden in volume met de stilste delen van een geluid.

|  | |  |
| Audio met compressie | | Audio zonder compressie |

Dit is belangrijk omdat zonder compressie sommige geluiden aanzienlijk luider kunnen zijn dan andere en belangrijke audio-indicatoren in je spellen kunnen overschaduwen, vooral wanneer ze worden afgespeeld via luidsprekers die moeite hebben met brede dynamische bereiken, zoals mobiele apparaten.

Om audio te comprimeren:

1.

Navigeer in het Trackbedieningspaneel  naar de audio-track die je wilt comprimeren en klik vervolgens op de FX -knop. Het Plugins-venster  verschijnt.

2.

Zoek naar ReaComp , wat staat voor Reaper Compressor, selecteer het resultaat en klik op de Toevoegen -knop. Een nieuw compressor-venster verschijnt.

 ![Reaper's Plugins Window met de ReaComp plugin gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/reaper/Compress-ReaComp.png)

3.

Verlaag de Drempel  naar de hoogste piek die je wilt dat je audio kan hebben voordat deze begint te worden gecomprimeerd.

 ![Reaper's Compressor UI met de Drempel-toggle gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/reaper/Compress-Threshold.png)

4.

Speel je audio af terwijl je naar het compressor-venster kijkt. Een felrode sectie verschijnt wanneer geluiden boven je ingestelde drempel komen. In de voorbeeldafbeelding leest de rode meter ongeveer -8; dit betekent dat de luide delen van het geluid met ongeveer 8 decibel zijn verlaagd.

 ![Reaper's Compressor UI met de compressiebalk gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/reaper/Compress-CompressionBar.png)

5.

Voor verdere compressieconfiguraties:

1.

Verhoog de Verhouding  om het effect van volumevermindering meer uitgesproken te maken.

2.

Pas je Aanval  en Vrijgave  tijden aan om te veranderen hoe snel de compressor begint en stopt met het comprimeren van je audio-track.

### [Frequenties equalizeren](#frequenties-equalizeren)[](#frequenties-equalizeren)

Terwijl je je audio bewerkt, wordt het af en toe noodzakelijk om aanpassingen te maken aan de frequentiebalans, zodat je dingen kunt doen zoals:

-

Het volume van de heldere, hoge frequenties verhogen.

-

Het volume van de basachtige, lage frequenties verlagen.

-

Een schelle, harde toon uit het middenbereik van frequenties verwijderen.

Dit proces wordt equalizeren  genoemd, en het is belangrijk omdat het je in staat stelt om realistische akoestiek voor verschillende gameplay-gebieden na te bootsen. Bijvoorbeeld, als een speler onder water is, zouden hoge frequenties van nature gedempt zijn en lage frequenties zouden gemakkelijk hoorbaar zijn, maar als de speler naar een open ruimte buiten zou bewegen, zou er geen demping optreden en zouden hoge frequenties weer hoorbaar zijn.

Laten we dit in de praktijk bekijken met twee audioclips van een regen geluid; de eerste audioclip bevat een verlaagde hoge shelf terwijl de tweede geen equalizing bevat. Terwijl je naar beide luistert, let op hoe de eerste clip gedempt en warm aanvoelt, alsof het tegen het raam slaat terwijl je binnen bent, en de tweede clip koud aanvoelt, alsof je buiten bent.

|  | |  |
| Audio met equalizing frequenties | | Audio zonder equalizing frequenties |

Frequenties equalizeren is een kunstvorm, en het kost tijd om uit te vinden welke configuraties werken om aan de behoeften van je spellen te voldoen. Het wordt aanbevolen om vaak te experimenteren totdat je vindt wat het beste klinkt voor jou.

Om frequenties in een geluid te equalizeren:

1.

Navigeer in het Trackbedieningspaneel  naar de audio-track waarvan je de frequenties wilt equalizeren en klik vervolgens op de FX -knop. Het Plugins-venster  verschijnt.

2.

Zoek naar ReaEQ , wat staat voor Reaper Equalizer, selecteer het resultaat en klik op de Toevoegen -knop. Een nieuw equalizer-venster verschijnt met vier ingeschakelde banden.

 ![Reaper's Plugins Window met de ReaEQ plugin gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/reaper/Equalize-ReaEQ.png)

3.

Selecteer een van de ingeschakelde banden en stel Type  in op basis van welke frequenties je wilt equalizeren. De meeste gebruiksgevallen gebruiken een van de volgende:

-

Low Shelf  - Verplaatst de gain onder de frequentie-instelling. Dit is meestal de eerste band.

-

High Shelf  - Verplaatst de gain boven de frequentie-instelling. Dit is meestal de laatste band.

-

Band  - Het volume wordt verhoogd of verlaagd aan beide zijden van de frequentie, en het bereik wordt bepaald door de bandbreedte-instelling.

-

Low Pass  - Filtert frequenties boven de frequentie-instelling.

-

High Pass  - Filtert frequenties onder de frequentie-instelling.

 ![Reaper's Equalizer UI met de eerste band gemarkeerd en de Type dropdown ingesteld op Low Shelf](https://prod.docsiteassets.roblox.com/assets/art/3p-software/reaper/Equalize-Type.png)

4.

Speel je audio af terwijl je naar het equalizer-venster kijkt en maak de nodige aanpassingen voor de geluidskwaliteit die je wilt.

### [Ruis verminderen](#ruis-verminderen)[](#ruis-verminderen)

Wanneer je audio opneemt, is het bijna onmogelijk om volledig te voorkomen dat er extra ongewenste ruis wordt vastgelegd, zoals het gezoem van een airconditioning, straatverkeer of vliegtuigen die boven je vliegen. Om deze reden is het belangrijk om ruis in je audioclips te verminderen, zodat spelers zich kunnen concentreren op wat het belangrijkst is zonder afleiding.

|  | |  |
| Audio met ruisreductie | | Audio zonder ruisreductie |

Hoewel subtiele ruisreductie misschien onnodig lijkt, wordt de subtiele ruis veel opvallender wanneer meerdere gelaagde geluiden tegelijkertijd worden afgespeeld, zoals de voetstappen van een personage, dialoog en een omgevingsachtergrond. Dit proces zorgt ervoor dat al onze audio opvalt, vooral wanneer spelers een koptelefoon dragen.

Om ruis te verminderen:

1.

Navigeer in het Trackbedieningspaneel  naar de audio-track waarvan je de frequenties wilt equalizeren en klik vervolgens op de FX -knop. Het Plugins-venster  verschijnt.

2.

Zoek naar ReaFir , wat staat voor Reaper Finite Impulse Responser, selecteer het resultaat en klik op de Toevoegen -knop. Een nieuw finite impulse response-venster verschijnt.

 ![Reaper's Plugins Window met de ReaFir plugin gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/reaper/Noise-ReaFir.png)

3.

Configureer de volgende instellingen:

1.

Stel Modus  in op Aftrekken . Nieuwe instellingen worden weergegeven.

2.

Schakel Automatisch ruisprofiel opbouwen  in.

 ![Reaper's Plugins Window met de instellingen voor ruisreductie gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/reaper/Noise-Subtract.png)

4.

Speel het deel van je geluid af dat de ruis bevat die je wilt verminderen gedurende enkele seconden, maar speel niet  het deel van het geluid dat je wilt behouden. Deze stap leert de plugin wat de ongewenste frequenties zijn.

5.

Wanneer de plugin het spectrum van je ruis heeft geleerd, schakel je Automatisch ruisprofiel opbouwen  uit.

6.

Speel je audio opnieuw af om het met verminderde ruis te horen.

### [Audio-variaties maken](#audio-variaties-maken)[](#audio-variaties-maken)

Voor audio-ontwerp in spellen is het belangrijk om variaties van geluiden te creëren die spelers vaak zullen horen tijdens hun gameplay, zoals voetstappen, zwaardzwaaien of feedback bij het verzamelen. Op dezelfde manier dat geluiden in de echte wereld bijna nooit exact hetzelfde herhalen, verbeteren variaties in geluid de onderdompeling van de speler en leiden ze tot een dynamische spelerservaring.

|  | |  |
| Audio met variaties | | Audio zonder variaties |

Er zijn veel manieren om variatie in je audio te creëren, maar de volgende stapsgewijze instructie richt zich op een paar eenvoudige stappen die je kunt nemen om drie alternatieven in minder dan drie minuten te creëren.

Om variaties in je audio te creëren:

1.

Dupliceer in het Arrangeergebied  je audio-clip totdat je drie exacte kopieën hebt. De eerste kopie blijft je originele geluid, terwijl de andere twee je variaties worden.

 ![Reaper's Arrange Area met drie kopieën van een audio-segment.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/reaper/Variations-Copies.png)

2.

Klik met de rechtermuisknop op de tweede kopie en selecteer in het contextmenu Item-eigenschappen… . Het Media Item Properties -venster verschijnt voor de tweede kopie.

 ![](https://prod.docsiteassets.roblox.com/assets/art/3p-software/reaper/Variations-ItemProperties.png)

3.

Verhoog of verlaag in het veld Pitch-aanpassing  de toonhoogte van het geluid.

4.

Klik op de Toepassen -knop.

5.

Klik met de rechtermuisknop op de derde kopie en selecteer in het contextmenu Item-eigenschappen… . Het Media Item Properties -venster verschijnt voor de derde kopie.

6.

Verhoog of verlaag in het veld Afspeelsnelheid  de afspeelsnelheid.

7.

Klik op de Toepassen -knop en speel je originele en beide variaties af om het verschil tussen alle drie te horen.

### [Audio in een lus zetten](#audio-in-een-lus-zetten)[](#audio-in-een-lus-zetten)

Voor een stapsgewijze tutorial van een officiële Roblox-geluidontwerper over het in een lus zetten van geluiden voor spellen, zie [Creating Perfect Audio Loops](https://devforum.roblox.com/t/creating-perfect-audio-loops/2849057) .

Wanneer je een omgevingsgeluid in de echte wereld opneemt, loopt het bijna nooit perfect in een lus. Zelfs monotone, niet-dynamische geluiden zoals het gezoem van een airconditioner zullen klikken en knallen wanneer ze in een lus draaien, waardoor de onderdompeling van de speler wordt verbroken en ze uit hun gameplay worden gehaald.

|  | |  |
| Audio met naadloze lussen | | Audio zonder naadloze lussen |

Dit wordt duidelijker wanneer er meerdere omgevingstracks zijn die bovenop elkaar worden gestapeld. Stel bijvoorbeeld dat je een verkenningsspel hebt met kikkers die kwaken, insecten die tsjirpen, wind die zachtjes voorbij waait en een vrolijke achtergrondtrack. Terwijl deze geluiden in een lus draaien, kunnen er scherpe volumepieken en/of frequentiesprongen optreden.

In het beste geval irriteert dit spelers, maar in het slechtste geval kan het ervoor zorgen dat ze het spel helemaal verlaten. Met een beetje extra moeite kun je naadloze lussen creëren die de gewenste sfeer behouden zonder onderbreking.

Om een lus te maken:

1.

Zorg ervoor dat je audio-clip lang genoeg is om het risico te vermijden dat het te duidelijk is als het in een lus draait. Voor de meeste gebruiksgevallen moet het minstens 15 seconden zijn.

2.

Zoek in het Arrangeergebied  een klein punt in het geluid waar je golfvorm(en) de Z-as of 0  kruisen. Dit betekent dat het geluid geen amplitude heeft, zodat het niet knalt of klikt wanneer het geluid in een lus draait.

 ![Een audio-track met de cursor over het luspunt.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/reaper/Loop-LoopPoint.png)

3.

Druk op S  om de track te splitsen. Je audio-track is nu in twee segmenten gesneden.

 ![Een audio-track met twee segmenten, gescheiden op het luspunt.](https://prod.docsiteassets.roblox.com/assets/art/3p-software/reaper/Loop-Split.png)

4.

Verplaats de tweede clip zodat deze vóór de eerste clip wordt afgespeeld en een lichte overlap heeft die wordt aangegeven door de rode omtrek.

5.

Speel je audio af om het naadloos in een lus te horen.

### [Audio exporteren](#audio-exporteren)[](#audio-exporteren)

Nadat je je audio hebt bewerkt, kun je deze exporteren voor gebruik in Studio. De volgende instellingen voldoen aan de vereisten van de meeste gebruiksgevallen, maar naarmate je een meer gevorderde gebruiker van Reaper wordt, kun je de instellingen voor je eigen projecten aanpassen.

Om audio te exporteren:

1.

Klik en sleep in het Arrangeergebied  over je audio-voorbeeld om te markeren wat je wilt exporteren.

2.

Navigeer in de menubalk naar Bestand  > Renderen… . Het Renderen naar Bestand -venster verschijnt.

 ![](https://prod.docsiteassets.roblox.com/assets/art/3p-software/reaper/FileRender.png)

3.

Configureer de volgende instellingen:

1.

Stel Bron  in op Master mix .

2.

Stel Grens  in op Tijdselectie  om je selectie in het Arrangeergebied te exporteren.

3.

Stel Directory  in op de locatie waar je je bestand wilt downloaden.

4.

Stel Naam  in op wat je je bestand wilt noemen.

5.

Stel Samplefrequentie  in op 48000  Hz  om een hoog kwaliteitsniveau bij standaard toonhoogte te waarborgen, terwijl je ook de bestandsgrootte optimaal klein houdt voor een lagere geheugendruk.

Als je een hogere kwaliteit wilt en van plan bent om het geluid dynamisch tijdens runtime naar beneden te stemmen, kun je de kwaliteit verhogen naar 96,000  Hz .

6.

Stel Kanalen  in op Stereo  voor 2 kanalen of Mono  voor 1 kanaal.

7.

Stel Primair uitvoerformaat  in op OGG vorbis . Dit is het voorkeursbestandstype voor spellen, omdat het geen extra stilte aan het begin of het einde van je audio toevoegt.

Gebruik het .mp3  uitvoerformaat niet, omdat dit enkele milliseconden stilte aan het begin van je audio zal toevoegen.

8.

Stel VBR-kwaliteit  in op 0.9  om de kwaliteit te verhogen.

9.

Klik onderaan het venster op Render 1 bestand . Een nieuw venster verschijnt met een voorbeeld van hoe je audio eruit ziet.

 ![](https://prod.docsiteassets.roblox.com/assets/art/3p-software/reaper/RenderToFileSettings.png)

Voor informatie over hoe je je nieuwe aangepaste audio-bestanden in spellen kunt gebruiken, zie de [Audio](/docs/nl-nl/audio)  gidsen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
