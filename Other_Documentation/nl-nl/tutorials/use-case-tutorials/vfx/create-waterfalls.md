<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/vfx/create-waterfalls -->

Watervallen maken met VFX | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. VFX

# Watervallen maken met VFX

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een waterval  is een punt in een rivier of stroom waar water over een of meer verticale afdalingen in een waterlichaam stroomt. Spellen bevatten vaak watervallen voor visuele esthetiek, zoals om de omgeving te verbeteren of een visueel aandachtspunt te creëren, of voor functionele gameplay-doeleinden, zoals om middelen te verbergen of spelers tussen verschillende gebieden in de plaats zelf te laten overgaan.

Met behulp van het [Waterfall Island](https://www.roblox.com/games/16454663889/Use-Case-Tutorials-Volcano-Island)  .rbxl  bestand als referentie, laat deze tutorial je zien hoe je een waterval kunt maken met VFX-objecten die het gedrag van echte fysieke verschijnselen vertegenwoordigen, inclusief richtlijnen over:

-

Het opdelen van referentiemateriaal in individuele componenten met verschillende visuele en gedragskenmerken.

-

Het configureren van cascades die met verschillende snelheden vallen om water te emuleren dat zich verspreidt terwijl het van een klif afdaalt.

-

Het configureren van spetters om water te emuleren dat aerosolachtig wordt wanneer cascades de onderliggende plonspoel raken.

-

Het configureren van wit water om turbulent belucht water te emuleren waar de uitstroming tegen rotsen botst.

-

Het configureren van schuim om een capillaire golf te emuleren die de oppervlaktespanning doorbreekt.

-

Het configureren van mist om mistdamp te emuleren die zich van het impactpunt omhoog en weg verheft, waardoor een regenboog ontstaat die spelers vanuit elke hoek kunnen zien.

Je kunt je eigen texturen maken in externe textuurcreatietools en meedoen met je eigen ontwerp. Voor informatie over het importeren van texturen voor gebruik in Studio, zie [Asset Manager](/docs/nl-nl/projects/assets/manager) .

## [Referentie ontleden](#referentie-ontleden)[](#referentie-ontleden)

Om geloofwaardige watervallen te creëren, is het belangrijk om echte natuurlijke kenmerken als referentie te gebruiken in het ontwerpproces, omdat dit je in staat stelt om het onderwerp op te splitsen in individuele componenten met verschillende visuele en gedragskenmerken. Bijvoorbeeld, het voorbeeld [Waterfall Island](https://www.roblox.com/games/16454663889/Use-Case-Tutorials-Volcano-Island)  spel verwijst naar Snoqualmie Falls in de staat Washington om alle textuur- en VFX-ontwerpbeslissingen met betrekking tot de waterval en het omliggende terrein te informeren.

 ![Een verre kijk op Snoqualmie Falls.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Falls-NoComponents.png)

Hoewel een waterval een continue en verbonden stroom water is die meerdere toestanden van materie met dynamische vloeistof- en luchtbeweging omvat, is het nuttig om dit complexe systeem op te splitsen in individuele componenten, zodat je kunt plannen hoe je verschillende VFX-objecten kunt gebruiken om hun tegenhangers in de echte wereld na te bootsen. Ter illustratie, deze tutorial splitst de voorbeeldwaterval op in vijf unieke componenten:

-

Cascades  – Het water dat van de klif afdaalt.

-

Spetters  – Het water dat zich verspreidt wanneer cascades de onderliggende plonspoel raken.

-

Wit Water  – Het turbulente water dat ontstaat wanneer de waterbron de rand van de klif nadert.

-

Schuim  – Het beluchte water dat zich horizontaal verspreidt bij de botsing van de cascades en de plonspoel.

-

Mist  – Het wolkachtige water dat in de lucht verdampt als gevolg van de algehele waterval.

![Snoqualmie Falls met alle vijf componenten gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Falls-Components.png)

![De voorbeeldwaterval met dezelfde vijf componenten gemarkeerd om de referentieafbeelding met het eindresultaat te vergelijken.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Sample-Components.png)

De volgende secties bieden een diepgaande analyse van de verschillende ontwerpbeslissingen en technieken die je kunt gebruiken om elk van deze watervalcomponenten te recreëren die de hoofdval in de 3D-ruimte van het voorbeeld vormen. Terwijl je deze beslissingen bekijkt en experimenteert met verschillende [Beam](/docs/nl-nl/reference/engine/classes/Beam)  en [ParticleEmitter](/docs/nl-nl/reference/engine/classes/ParticleEmitter)  eigenschappen, leer je hoe je VFX kunt gebruiken om te voldoen aan de unieke omgevingsvereisten voor je eigen spellen.

## [Cascades configureren](#cascades-configureren)[](#cascades-configureren)

Een cascade  is het vallende water dat over de rand van kliffen of hellingen in onderliggende plonspoelen valt. Cascades vallen met verschillende snelheden, afhankelijk van zowel hun watervolume als de schaal van hun val in de plonspoel. Bijvoorbeeld, de hoofdval van het voorbeeld lijkt langzamer te vallen omdat er een groot volume water over een grote afstand valt, maar de tweede val van het voorbeeld lijkt sneller te vallen omdat er een kleiner volume water over een korte afstand valt.

Hoofdval

Tweede val

Bovendien hebben watervallen vaak lagen van cascades die met verschillende snelheden vallen omdat het water zich verspreidt terwijl het in de plonspoel daalt. Om dit principe te demonstreren, gebruikt het voorbeeld meerdere [Beam](/docs/nl-nl/reference/engine/classes/Beam)  objecten met naadloze texturen die tussen [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  objecten met verschillende snelheden en lengtes renderen. Naast het bieden van een realistischere valbeweging voor de hoofdval, creëert deze techniek ook een illusie van parallax om de cascade een gevoel van diepte en volume te geven, ook al is het slechts een 2D-afbeelding.

Deze waterval lijkt natuurlijk omdat het water met verschillende snelheden daalt en zich verspreidt.

Deze waterval lijkt onnatuurlijk omdat het water met dezelfde snelheid daalt en zich verspreidt.

Om de cascades voor de hoofdval in het voorbeeld [Waterfall Island](https://www.roblox.com/games/16454663889/Use-Case-Tutorials-Volcano-Island)  plaatsbestand te recreëren:

1.

Maak de uitstroming voor het cascaderende water.

1.

In het Explorer  venster, maak een Map  in de Workspace  om alle uitstromingsobjecten te bevatten, en hernoem de map naar Outflow .

2.

Voeg twee blok  onderdelen toe aan de Outflow  map, en hernoem ze respectievelijk naar OutflowStart  en OutflowStop .

3.

Verplaats OutflowStart  naar waar je wilt dat de uitstroming begint, en verplaats OutflowStop  naar de rand van de klif.

 ![Een schuine bovenaanzicht van het uitstromende water met twee blokonderdelen gepositioneerd waar de uitstromingtextuur zou moeten renderen.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Cascades-1C.png)

4.

Voeg een attachment toe aan zowel OutflowStart  als OutflowStop , en draai de attachments totdat de gele visuele hulp omhoog wijst.

 ![Een schuine bovenaanzicht van het uitstromende water met twee blokonderdelen die attachments bevatten waar de gele visuele hulpmiddelen omhoog wijzen.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Cascades-1D.png)

5.

Voeg een Beam  toe aan de Outflow  map, en hernoem deze naar OutflowWater .

6.

Wijs de attachment van elk onderdeel toe aan OutflowWater .

1.

In het Explorer  venster, selecteer OutflowWater .

2.

In het Properties  venster,

1.

Stel Attachment0  in op de attachment in OutflowStart .

2.

Stel Attachment1  in op de attachment in OutflowStop . De beam rendert zijn standaardtextuur tussen de twee attachments.

 ![Een schuine bovenaanzicht van het uitstromende water met twee blokonderdelen die de standaard beamtextuur tussen de attachments renderen.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Cascades-1F.png)

7.

Pas het visuele uiterlijk van de beam aan zodat het eruitziet als stromend water dat naar de rand van de klif beweegt.

1.

In het Explorer  venster, controleer of OutflowWater  nog steeds is geselecteerd.

2.

In het Properties  venster,

1.

Stel Texture  in op rbxassetid://4787437624  om een nieuwe textuur te renderen die eruitziet als stromend schuim.

2.

Stel Width0  in op 60  om de textuur vanaf de as waar het begint te renderen te verbreden.

3.

Stel Width1  in op 20  om de textuur naar de rand van de klif te versmallen.

4.

Stel TextureSpeed  in op 0.4  om de stroom van de textuur te vertragen.

5.

Stel TextureLength  in op 64  om de lengte van de textuur uit te rekken.

6.

Stel TextureMode  in op Wrap  om de textuur te herhalen over de totale lengte van de beam in de 3D-wereld tussen de attachments gedeeld door zijn TextureLength . Dit zorgt ervoor dat de textuur er veel realistischer uitziet voor stromend water.

7.

Stel Color  in op een kleurvolgorde die afwisselend van donker en lichtblauw naar wit gaat.

1.

Klik op de Color  eigenschap, en klik vervolgens op de ⋯  knop. Een kleurvolgorde pop-up verschijnt.

 ![Een close-up van het Properties venster van Studio met de ellipsknop van de Color eigenschap gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Cascades-1G1.png)

Elke driehoek op de onderste as van de kleurvolgorde is een keypoint  die de kleurwaarde van de eigenschap op dat punt van de levensduur van het deeltje bepaalt.

2.

Stel de volgende tijd- en waarde-eigenschappen in door de kleurvolgorde:

-

Time  = 0 , RGB Value  = 208, 247, 255

-

Time  = 0.135 , RGB Value  = 146, 235, 255

-

Time  = 0.248 , RGB Value  = 255, 255, 255

-

Time  = 0.384 , RGB Value  = 128, 183, 202

-

Time  = 0.757 , RGB Value  = 166, 213, 248

-

Time  = 1 , RGB Value  = 255, 255, 255

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Cascades-1G2.png)

8.

Stel Transparency  in op een getallenreeks die ervoor zorgt dat het water levendiger wordt naarmate het de rand van de klif nadert.

1.

Klik op de Transparency  eigenschap, en klik vervolgens op de ⋯  knop. Een getallenreeks pop-up verschijnt. Standaard is de grafiek een rechte lijn en blijft de afbeelding dezelfde transparantie van links naar rechts.

 ![Een close-up van de transparantie getallenreeks grafiek.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Cascades-1H1.png)

Elke vierkant aan het begin en het einde van de getallenreeks is een keypoint  die de transparantie waarde van de eigenschap op dat punt van de textuur van links naar rechts bepaalt.

2.

Stel de volgende tijd- en waarde-eigenschappen in door de getallenreeks:

-

Time  = 0 , Value  = 1

-

Time  = 0.375 , Value  = 0.725

-

Time  = 0.615 , Value  = 0

-

Time  = 0.92 , Value  = 1

-

Time  = 1 , Value  = 1

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Cascades-1H2.png)

9.

Schaal elk onderdeel om ervoor te zorgen dat de textuur de breedte van de uitstromingspoel bedekt. De uitstroming lijkt nu vanuit alle hoeken naar de rand van de klif te stromen.

2.

Maak het snel stromende cascaderende water van de hoofdval.

1.

In het Explorer  venster, maak een Map  in de Workspace  om alle cascaderende waterobjecten te bevatten, en hernoem de map naar Cascades .

2.

Voeg twee blok  onderdelen toe aan de Cascades  map, en hernoem ze respectievelijk naar MainDropStart  en MainDropStop .

3.

Verplaats MainDropStart  naar de rand van de klif, en verplaats MainDropStop  naar waar het onder de plonspoel is.

 ![Een schuine zijaanzicht van de klif met twee blokonderdelen gepositioneerd waar de snel stromende cascade textuur zou moeten renderen.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Cascades-2C.png)

4.

Configureer attachments voor alle cascaderende waterbeams van de hoofdval om hun texturen te renderen.

1.

Voeg een attachment toe aan MainDropStart , en draai de attachment totdat de gele visuele hulp van de klif af wijst.

2.

Voeg een attachment toe aan MainDropStop , en draai de attachment totdat de gele visuele hulp naar de klif wijst.

 ![Een schuine zijaanzicht van de klif met twee blokonderdelen die attachments bevatten. Het blokonderdeel aan de bovenkant van de klif bevat een gele visuele hulp die van de klif af wijst, en het blokonderdeel aan de onderkant van de klif bevat een gele visuele hulp die naar de klif wijst.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Cascades-2D.png)

5.

Voeg een Beam  toe aan de Cascades  map, en hernoem deze naar FastDrop .

6.

Wijs de attachment van elk onderdeel toe aan FastDrop .

1.

In het Explorer  venster, selecteer FastDrop .

2.

In het Properties  venster,

1.

Stel Attachment0  in op de attachment in MainDropStart .

2.

Stel Attachment1  in op de attachment in MainDropStop . De beam rendert zijn standaardtextuur tussen de twee attachments.

 ![Een schuine zijaanzicht van de klif met twee blokonderdelen die de standaard beamtextuur tussen de attachments renderen.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Cascades-2F.png)

7.

Pas het visuele uiterlijk van de beam aan zodat het eruitziet als snel stromend cascaderend water van de hoofdval.

1.

In het Explorer  venster, controleer of FastDrop  nog steeds is geselecteerd.

2.

In het Properties  venster,

1.

Stel Texture  in op rbxassetid://16808804567  om een nieuwe textuur te renderen die eruitziet als stromend water.

2.

Stel Width0  in op 5  om de textuur vanaf de as waar het begint te renderen te verbreden.

3.

Stel Width1  in op 10  om de textuur te verbreden wanneer het de plonspoel bereikt.

4.

Stel CurveSize0  in op 10  om de textuur van de klif af te buigen.

5.

Stel CurveSize1  in op 20  om de textuur in de plonspoel te buigen.

6.

Stel TextureSpeed  in op 1.3  om de textuur snel te laten stromen.

7.

Stel TextureLength  in op 2  om de lengte van de textuur iets uit te rekken.

8.

Stel Color  in op een kleurvolgorde die afwisselend van donker en lichtblauw naar wit gaat.

-

Time  = 0 , RGB Value  = 208, 247, 255

-

Time  = 0.135 , RGB Value  = 210, 246, 255

-

Time  = 0.25 , RGB Value  = 255, 255, 255

-

Time  = 0.384 , RGB Value  = 163, 187, 202

-

Time  = 0.757 , RGB Value  = 214, 229, 248

-

Time  = 1 , RGB Value  = 255, 255, 255

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Cascades-2G8.png)

1.

Stel Transparency  in op een getallenreeks die ervoor zorgt dat het cascaderende water levendiger is tussen de attachmentpunten.

-

Time  = 0 , Value  = 1

-

Time  = 0.115 , Value  = 0

-

Time  = 0.835 , Value  = 0

-

Time  = 0.881 , Value  = .994

-

Time  = 1 , Value  = 1

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Cascades-2G9.png)

1.

Stel ZOffset  in op 2  om de textuur iets van de klif af te verplaatsen.

2.

Schakel FaceCamera  in om ervoor te zorgen dat het cascaderende water zichtbaar is, ongeacht de hoek van de speler ten opzichte van het water.

3.

Maak het langzaam stromende cascaderende water van de hoofdval.

1.

Dupliceer FastDrop , en hernoem de gedupliceerde beam naar SlowDrop .

2.

Pas het visuele uiterlijk van de beam aan zodat het eruitziet als langzaam stromend cascaderend water van de hoofdval.

1.

In het Explorer  venster, selecteer SlowDrop .

2.

In het Properties  venster,

1.

Stel Width1  in op 20  om de textuur nog breder te maken wanneer het de plonspoel bereikt.

2.

Stel TextureLength  in op 1.5  om de lengte van de textuur iets te verkorten.

3.

Stel TextureSpeed  in op 1  om de textuur minder snel te laten stromen.

4.

Stel ZOffset  in op 0  om de textuur direct van de rand van de klif te laten stromen.

4.

In het Explorer  venster, selecteer alle blokonderdelen in de Outflow  map, en stel in het Properties  venster Transparency  in op 1  om de blokken onzichtbaar te maken.

## [Spetters configureren](#spetters-configureren)[](#spetters-configureren)

Wanneer cascades de dichtheid van de onderliggende plonspoel raken, wordt het water omhoog geduwd vanaf het impactpunt om spetters  te creëren. Terwijl dit aerosolachtige water omhoog wordt geduwd, breidt het zich uit en breekt het uit elkaar om druppels te produceren die in verschillende richtingen verspreiden.

Om dit proces te demonstreren, gebruikt het voorbeeld twee [ParticleEmitter](/docs/nl-nl/reference/engine/classes/ParticleEmitter)  objecten aan de basis van de hoofdval. De eerste deeltjesemitter stoot deeltjes uit die eruitzien als dichte spetters die het gewicht van het water vertegenwoordigen dat omhoog begint te worden geduwd wanneer de cascades de plonspoel raken. De tweede deeltjesemitter stoot deeltjes uit die eruitzien als druppels die het water vertegenwoordigen dat aerosolachtig wordt.

Wanneer je deze deeltjesemitters configureert om beide deeltjes tegelijkertijd maar met verschillende snelheden uit te stoten, emuleert het resulterende visuele effect het fysieke gedrag van spetters in de echte wereld. Dit soort details draagt bij aan de realiteit van je VFX en dompelt spelers onder in de 3D-ruimte.

![De 2D textuur die zwaar aerosolachtig water vertegenwoordigt voordat het uit elkaar valt.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Splashes-Dense.png) Dense Texture = rbxassetid://16829556885

![De 2D textuur die zwaar aerosolachtig water vertegenwoordigt terwijl het uit elkaar valt.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Splashes-Droplets.png) Droplets Texture = rbxassetid://17082061238

Om de spetters aan de basis van de hoofdval in het voorbeeld [Waterfall Island](https://www.roblox.com/games/16454663889/Use-Case-Tutorials-Volcano-Island)  plaatsbestand te recreëren:

1.

In het Explorer  venster, maak een Map  in de Workspace  om alle spetterobjecten te bevatten, en hernoem de map naar Splashes .

2.

Voeg een blok  onderdeel toe aan Splashes , en hernoem deze naar MainDropSplashes .

3.

Positioneer en schaal MainDropSplashes  naar het volledige oppervlak waar de cascade de plonspoel raakt.

 ![Een close-up van de onderkant van de klif met een blokonderdeel gepositioneerd op het punt waar de cascades de plonspoel raken.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Splashes-3.png)

4.

Maak de dichte spetter waar het cascaderende water van de hoofdval de plonspoel raakt.

1.

Voeg een ParticleEmitter  toe aan MainDropSplashes , en hernoem de emitter naar SplashDense .

2.

Selecteer SplashDense , en stel in het Properties  venster,

1.

Stel Texture  in op rbxassetid://16829556885  om deeltjes te renderen die eruitzien als dichte spetters.

2.

Stel Color  in op een kleurvolgorde die begint met blauw en dan wit wordt.

-

Time  = 0 , RGB Value  = 189, 246, 255

-

Time  = 1 , RGB Value  = 255, 255, 255

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Splashes-4B2.png)

1.

Stel Size  in op een getallenreeks die gestaag in grootte toeneemt met een variatievenster.

-

Time  = 0 , Value  = 1.81 , Envelope  = 0.562

-

Time  = 1 , Value  = 5.75 , Envelope  = 1.31

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Splashes-4B3.png)

1.

Stel Transparency  in op een getallenreeks waarin deeltjes beginnen als transparant, dan ondoorzichtig worden, en vervolgens weer transparant worden over hun levensduur met een groot variatievenster.

-

Time  = 0 , Value  = 1 , Envelope  = 0

-

Time  = 0.5 , Value  = 0.181 , Envelope  = 0.181

-

Time  = 1 , Value  = 1 , Envelope  = 0

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Splashes-4B4.png)

1.

Stel Lifetime  in op 0.25, 0.35  om de levensduur van elk deeltje willekeurig in te stellen tussen 250 en 350 milliseconden.

2.

Stel Rate  in op 30  om 30 deeltjes per seconde uit te stoten.

3.

Stel Rotation  in op -45, 45  om elk deeltje willekeurig te oriënteren tussen -45 en 45 graden per seconde.

4.

Stel RotSpeed  in op -40, 40  om elk deeltje willekeurig uit te stoten tussen -45 en 40 graden per seconde.

5.

Stel Speed  in op 20, 35  om elk deeltje willekeurig uit te stoten tussen 20 en 35 studs per seconde.

6.

Stel SpreadAngle  in op 50, 50  om deeltjes in een hoek langs de X- en Z-as uit te stoten.

7.

Stel Acceleration  in op 0, -40, 0  om de zwaartekracht te simuleren en deeltjes naar beneden te trekken.

8.

Stel LightEmission  in op 0.5  om de deeltjes te verlichten.

9.

Stel LightInfluence  in op 0.1  om aanzienlijk te verminderen hoeveel het omgevingslicht de kleur van de deeltjes beïnvloedt.

5.

Maak de druppels waar het cascaderende water van de hoofdval de plonspoel raakt.

1.

Dupliceer SplashDense , en hernoem deze naar SplashDroplets .

2.

Selecteer SplashDroplets , en stel in het Properties  venster,

1.

Stel Texture  in op rbxassetid://17082061238  om deeltjes te renderen die eruitzien als druppels.

2.

Stel Size  in op een getallenreeks die snel in grootte toeneemt met een variatievenster.

-

Time  = 0 , Value  = 1.81 , Envelope  = 0.562

-

Time  = 1 , Value  = 8.69 , Envelope  = 1.31

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Splashes-5B2.png)

1.

Stel Transparency  in op een getallenreeks waarin deeltjes beginnen als transparant, snel ondoorzichtig worden, en dan langzaam weer transparant worden nabij het midden van hun levensduur.

-

Time  = 0 , Value  = 1 , Envelope  = 0

-

Time  = 0.104 , Value  = 0.0625 , Envelope  = 0.0625

-

Time  = 0.429 , Value  = 0.0562 , Envelope  = 0.0562

-

Time  = 1 , Value  = 1 , Envelope  = 0

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Splashes-5B3.png)

1.

Stel Lifetime  in op 0.15, 0.6  om de levensduur van elk deeltje willekeurig in te stellen tussen 150 en 600 milliseconden.

2.

Stel Rate  in op 20  om 20 deeltjes per seconde uit te stoten.

6.

In het Explorer  venster, selecteer alle blokonderdelen in de Splashes  map, en stel in het Properties  venster Transparency  in op 1  om de blokken onzichtbaar te maken.

## [Wit water configureren](#wit-water-configureren)[](#wit-water-configureren)

Wit water  ontstaat wanneer de waterbron turbulenter wordt naarmate deze snelheid krijgt wanneer deze zijn afdaling nadert en tegen objecten in zijn pad botst. Dit resulteert in belucht, webachtig water dat wit lijkt door meer luchtbellen in de waterbron.

Om dit proces na te bootsen, gebruikt het voorbeeld twee [ParticleEmitter](/docs/nl-nl/reference/engine/classes/ParticleEmitter)  objecten die deeltjes uitstoten die eruitzien als zwaar beluchte spetters waar de uitstroming tegen de rotsen aan de rand van de klif botst. De emitter gebruikt geen ingebouwde verlichting, en prioriteert in plaats daarvan witte en grijze tinten met verschillende vallende snelheden om de hoeveelheid lucht in het water te demonstreren.

![De 2D textuur die zwaar aerosolachtig water vertegenwoordigt terwijl het tegen rotsen botst.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Splashes-WhiteWater.png) Wit Water Textuur = rbxassetid://16808075391

Om het witte water te recreëren waar de uitstroming tegen de rotsen van de klif botst in het voorbeeld [Waterfall Island](https://www.roblox.com/games/16454663889/Use-Case-Tutorials-Volcano-Island)  plaatsbestand:

1.

In het Explorer  venster, maak een Map  in de Workspace  om alle witte waterobjecten te bevatten, en hernoem de map naar WhiteWater .

2.

Voeg een blok  onderdeel toe aan WhiteWater , en hernoem deze naar MainDropWW .

3.

Positioneer en schaal MainDropWW  naar het volledige oppervlak waar de uitstroming begint te stromen over de klif.

 ![Een schuine zijaanzicht van de bovenkant van de klif met een blokonderdeel gepositioneerd op het punt waar de uitstroming begint te stromen over de klif.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/WW-3.png)

4.

Maak het minder turbulente witte water waar de hoofduitstroming tegen de omliggende rotsen botst.

1.

Voeg een ParticleEmitter  toe aan MainDropWW , en hernoem de emitter naar GentleWW .

2.

Selecteer GentleWW , en stel in het Properties  venster,

1.

Stel Texture  in op rbxassetid://16808075391  om deeltjes te renderen die eruitzien als webachtige spetters.

2.

Stel Color  in op een kleurvolgorde die begint met blauw en dan wit wordt.

-

Time  = 0 , RGB Value  = 189, 246, 255

-

Time  = 1 , RGB Value  = 255, 255, 255

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Splashes-4B2.png)

1.

Stel Size  in op een getallenreeks die gestaag in grootte toeneemt met een variatievenster.

-

Time  = 0 , Value  = 1.13 , Envelope  = 0.562

-

Time  = 1 , Value  = 5.56 , Envelope  = 0.563

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/WW-4A3.png)

1.

Stel Transparency  in op een getallenreeks waarin deeltjes beginnen als transparant, ongeveer halverwege ondoorzichtig worden, en dan lichte pieken hebben om weer transparant te worden over hun levensduur.

-

Time  = 0 , Value  = 1 , Envelope  = 0

-

Time  = 0.143 , Value  = 0.462 , Envelope  = 0.0625

-

Time  = 0.336 , Value  = 0.462 , Envelope  = 0.0562

-

Time  = 0.622 , Value  = 0.788 , Envelope  = 0.0538

-

Time  = 1 , Value  = 1 , Envelope  = 0

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/WW-4A4.png)

1.

Stel ZOffset  in op 2  om de textuur iets van de klif af te verplaatsen.

2.

Stel Lifetime  in op 1.25, 1.5  om de levensduur van elk deeltje willekeurig in te stellen tussen 1250 en 1500 milliseconden.

3.

Stel Rate  in op 12  om 12 deeltjes per seconde uit te stoten.

4.

Stel Rotation  in op -45, 45  om elk deeltje willekeurig te oriënteren tussen -45 en 45 graden per seconde.

5.

Stel RotSpeed  in op -40, 40  om elk deeltje willekeurig uit te stoten tussen -45 en 40 graden per seconde.

6.

Stel Speed  in op 15, 18  om elk deeltje willekeurig uit te stoten tussen 20 en 35 studs per seconde.

7.

Stel SpreadAngle  in op 5, 5  om deeltjes in een kleine hoek langs de X- en Z-as uit te stoten.

8.

Stel Acceleration  in op 0, -35, 0  om de zwaartekracht te simuleren en deeltjes naar beneden te trekken.

9.

Stel Drag  in op 0.25  om deeltjes hun snelheid te laten verliezen met exponentiële afname.

10.

Stel LightEmission  in op 0.6  om de deeltjes te verlichten.

11.

Stel LightInfluence  in op 0.1  om aanzienlijk te verminderen hoeveel het omgevingslicht de kleur van de deeltjes beïnvloedt.

5.

Maak het meer turbulente witte water waar de hoofduitstroming tegen de omliggende rotsen botst.

1.

Dupliceer GentleWW , en hernoem deze naar TurbulentWW .

2.

Selecteer TurbulentWW , en stel in het Properties  venster,

1.

Stel Size  in op een getallenreeks die subtiel in grootte toeneemt met een variatievenster.

-

Time  = 0 , Value  = 1.6 , Envelope  = 0.562

-

Time  = 1 , Value  = 2.63 , Envelope  = 0.563

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/WW-5B1.png)

1.

Stel Transparency  in op een getallenreeks waarin deeltjes beginnen als transparant, ondoorzichtig worden, en dan weer transparant worden nabij het midden van hun levensduur.

-

Time  = 0 , Value  = 1 , Envelope  = 0

-

Time  = 0.156 , Value  = 0.0437 , Envelope  = 0.0437

-

Time  = 0.55 , Value  = 0.075 , Envelope  = 0.0252

-

Time  = 1 , Value  = 1 , Envelope  = 0

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/WW-5B2.png)

1.

Stel Lifetime  in op 0.25, 0.5  om de levensduur van elk deeltje willekeurig in te stellen tussen 250 en 500 milliseconden.

2.

Stel Rate  in op 20  om 20 deeltjes per seconde uit te stoten.

3.

Stel Speed  in op 5, 6  om elk deeltje willekeurig uit te stoten tussen 5 en 6 studs per seconde.

4.

Stel Acceleration  in op 0, -15, 0  om de zwaartekracht te simuleren en deeltjes naar beneden te trekken.

6.

In het Explorer  venster, selecteer alle blokonderdelen in de WhiteWater  map, en stel in het Properties  venster Transparency  in op 1  om de blokken onzichtbaar te maken.

## [Schuim configureren](#schuim-configureren)[](#schuim-configureren)

In tegenstelling tot spetters die omhoog worden geduwd wanneer cascades de plonspoel raken, is schuim  belucht water dat zich naar buiten ripples vanaf de basis van het impactpunt. Vergelijkbaar met spetters, breidt schuim zich uit en breekt het uit elkaar in webachtige druppels terwijl het aerosolachtig wordt.

Om dit effect na te bootsen, gebruikt het voorbeeld een [ParticleEmitter](/docs/nl-nl/reference/engine/classes/ParticleEmitter)  object om deeltjes uit te stoten die eruitzien als schuimrimpels, en het stoot ze langzaam parallel aan de plonspoel uit. Dit stelt het deeltje in staat om het visuele en gedragsmatige effect van een capillaire golf die de oppervlaktespanning van de onderliggende waterpoel doorbreekt na te bootsen.

![De 2D textuur die het aerosolachtige water vertegenwoordigt dat zich weg ripples vanaf waar de cascades de plonspoel raken.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Foam-Texture.png) Foam Ripples Texture = rbxassetid://16811365086

Om het schuim aan de basis van de hoofdval in het voorbeeld [Waterfall Island](https://www.roblox.com/games/16454663889/Use-Case-Tutorials-Volcano-Island)  plaatsbestand te recreëren:

1.

In het Explorer  venster, maak een Map  in de Workspace  om alle schuimobjecten te bevatten, en hernoem de map naar Foam .

2.

Voeg een blok  onderdeel toe aan Foam , en hernoem deze naar MainDropFoam .

3.

Positioneer en schaal MainDropFoam  naar het volledige oppervlak waar het dichtste deel van de hoofdcascade de plonspoel raakt.

 ![Een schuine zijaanzicht van de onderkant van de klif met een blokonderdeel gepositioneerd op het punt waar de cascades de plonspoel raken.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Foam-2B.png)

4.

Voeg een ParticleEmitter  toe aan MainDropFoam , en hernoem de emitter naar FoamRipples .

5.

In het Explorer  venster, selecteer FoamRipples , en stel in het Properties  venster,

1.

Stel Texture  in op rbxassetid://16811365086  om deeltjes te renderen die eruitzien als schuimrimpels.

2.

Stel Orientation  in op VelocityPerpendicular  om deeltjes perpendiculair aan de richting van hun beweging uit te stoten.

3.

Stel Transparency  in op een getallenreeks waarin deeltjes beginnen als transparant, snel ondoorzichtig worden, en dan snel weer transparant worden aan het einde van hun levensduur.

-

Time  = 0 , Value  = 1 , Envelope  = 0

-

Time  = 0.143 , Value  = 0.119 , Envelope  = 0.1

-

Time  = 0.664 , Value  = 0.125 , Envelope  = 0.112

-

Time  = 1 , Value  = 1 , Envelope  = 0

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Foam-2D4.png)

4.

Stel Lifetime  in op 0.5, 0.7  om de levensduur van elk deeltje willekeurig in te stellen tussen 500 en 700 milliseconden.

5.

Stel Rate  in op 5  om 5 deeltjes per seconde uit te stoten.

6.

Stel Rotation  in op 0, 360  om elk deeltje willekeurig in een cirkel vanaf het emissiepunt te oriënteren.

7.

Stel RotSpeed  in op -15, 15  om elk deeltje willekeurig uit te stoten tussen -15 en 15 graden per seconde.

8.

Stel Speed  in op 0, .01  om elk deeltje willekeurig uit te stoten tussen 0 en .01 studs per seconde.

9.

Stel LightEmission  in op 0.25  om de deeltjes subtiel te verlichten.

10.

Stel LightInfluence  in op 0  om te voorkomen dat het omgevingslicht de kleur van de deeltjes beïnvloedt.

6.

In de Command Bar , voer de volgende string in om de grootte van elk deeltje van 5 naar 20 studs over hun levensduur met een klein variatievenster te vergroten:

```

workspace.Foam.MainDropFoam.FoamRipples.Size = NumberSequence.new{NumberSequenceKeypoint.new(0,5,0), NumberSequenceKeypoint.new(1,20,5)}

```

7.

In het Explorer  venster, selecteer alle blokonderdelen in de Foam  map, en stel in het Properties  venster Transparency  in op 1  om de blokken onzichtbaar te maken.

## [Mist configureren](#mist-configureren)[](#mist-configureren)

Wanneer cascades impact maken met de plonspoel, verdampt een deel van het water en condenseert in de koele, vochtige lucht om mist  te creëren. Mistdamp vangt het licht niet op dezelfde manier als harde oppervlakken; in plaats daarvan reflecteren ze licht op vaak onverwachte manieren om helder te verschijnen binnen de algehele omgeving totdat ze volledig verdampen.

Het voorbeeld emuleert dit proces door twee [ParticleEmitter](/docs/nl-nl/reference/engine/classes/ParticleEmitter)  objecten aan de basis van de val te gebruiken. De eerste deeltjesemitter stoot energiek deeltjes uit weg van het impactpunt en de klif, en de tweede stoot deeltjes uit die langzaam naar de lucht stijgen. De deeltjes van beide deeltjesemitters zijn helder aan het begin van hun levensduur, en worden langzaam transparant aan het einde van hun levensduur terwijl ze verdampen.

Vergelijkbaar met de echte wereld, stelt het verdampingsproces van de mist een regenboog in staat om te vormen terwijl licht weerkaatst op de kleine waterdruppels, wat het voorbeeld ook emuleert met een [ParticleEmitter](/docs/nl-nl/reference/engine/classes/ParticleEmitter)  object dat regenboogdeeltjes met een korte levensduur uitstoot. Deze deeltjes zijn altijd gericht naar de camera, ongeacht de hoek van de speler ten opzichte van de waterval, om een optische illusie te creëren van licht dat op de damp zelf valt.

![De 2D textuur die de mist vertegenwoordigt.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Mist-Texture.png) Mist Textuur = rbxassetid://16830667309

![De 2D textuur die de regenboog vertegenwoordigt.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Rainbow-Texture.png) Regenboog Textuur = rbxassetid://16828911033

Om de mist te recreëren die naar buiten en omhoog beweegt vanaf de basis van de hoofdval in het voorbeeld [Waterfall Island](https://www.roblox.com/games/16454663889/Use-Case-Tutorials-Volcano-Island)  plaatsbestand:

1.

In het Explorer  venster, maak een Map  in de Workspace  om alle mistgerelateerde objecten te bevatten, en hernoem de map naar Mist .

2.

Maak de mist die zich verspreidt vanaf de impact van de cascade op de plonspoel.

1.

Voeg een blok  onderdeel toe aan Mist , en hernoem deze naar BaseMist .

2.

Positioneer, oriënteer en schaal BaseMist  zodat deze weg wijst van het dichtste deel van de locatie waar de hoofdcascade de plonspoel raakt.

 ![Een schuine zijaanzicht van de onderkant van de klif met een blokonderdeel gepositioneerd op het punt waar de cascades de plonspoel raken. Het blokonderdeel is iets gekanteld zodat de bovenste kant van het blok van de klif af wijst.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Mist-2B.png)

3.

Voeg een ParticleEmitter  toe aan BaseMist , en hernoem de emitter naar Mist .

4.

Selecteer Mist , en stel in het Properties  venster,

1.

Stel Texture  in op rbxassetid://16830667309  om deeltjes te renderen die eruitzien als dikke mist.

2.

Stel Color  in op een kleurvolgorde die begint met blauw en dan wit wordt.

-

Time  = 0 , RGB Value  = 171, 244, 255

-

Time  = 0.339 , RGB Value  = 251, 254, 255

-

Time  = 1 , RGB Value  = 255, 255, 255

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Mist-2D2.png)

1.

Stel Size  in op een getallenreeks die gestaag in grootte toeneemt.

-

Time  = 0 , Value  = 8 , Envelope  = 0

-

Time  = 1 , Value  = 10 , Envelope  = 0

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Mist-2D3.png)

1.

Stel Transparency  in op een getallenreeks waarin deeltjes beginnen als transparant, snel iets ondoorzichtig worden, en dan snel weer transparant worden aan het einde van hun levensduur.

-

Time  = 0 , Value  = 1 , Envelope  = 0

-

Time  = 0.0971 , Value  = 0.8 , Envelope  = 0.0625

-

Time  = 1 , Value  = 1 , Envelope  = 0

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Mist-2D4.png)

1.

Stel ZOffset  in op 2  om de textuur iets van de plonspoel af te verplaatsen.

2.

Stel Lifetime  in op 0.5, 1  om de levensduur van elk deeltje willekeurig in te stellen tussen 500 en 1000 milliseconden.

3.

Stel Rate  in op 20  om 20 deeltjes per seconde uit te stoten.

4.

Stel Rotation  in op -360, 360  om elk deeltje willekeurig in een cirkel te oriënteren.

5.

Stel RotSpeed  in op -50, 50  om elk deeltje willekeurig uit te stoten tussen -50 en 50 graden per seconde.

6.

Stel Speed  in op 35, 50  om elk deeltje willekeurig uit te stoten tussen 35 en 50 studs per seconde.

7.

Stel SpreadAngle  in op 25, 25  om deeltjes in een kleine hoek langs de X- en Z-as uit te stoten.

8.

Stel Acceleration  in op -10, -25, -10  om de impact van de spetter te simuleren die naar buiten explodeert vanaf de plonspoel.

9.

Stel Drag  in op 1.5  om deeltjes hun snelheid te laten verliezen met exponentiële afname.

3.

Maak de mist die omhoog stijgt vanaf de plonspoel.

1.

Dupliceer BaseMist , en hernoem deze naar RiseMist .

2.

Oriënteer RiseMist  zodat de bovenkant van het onderdeel dat deeltjes uitstoot naar de lucht wijst.

3.

Selecteer de kinderdeeltjesemitter, en stel in het Properties  venster,

1.

Stel Lifetime  in op 4  om de levensduur van elk deeltje op 4 seconden in te stellen.

2.

Stel Rate  in op 3  om 3 deeltjes per seconde uit te stoten.

3.

Stel RotSpeed  in op -10, 10  om elk deeltje willekeurig uit te stoten tussen -10 en 10 graden per seconde.

4.

Stel Speed  in op 25  om elk deeltje 25 studs per seconde uit te stoten.

5.

Stel Acceleration  in op 0, 0, 0  om de vorige simulatie te verwijderen.

6.

Stel Drag  in op 1  om deeltjes hun snelheid te laten verliezen met exponentiële afname.

4.

In de Command Bar , voer de volgende string in om de grootte van elk deeltje van 20 naar 20 studs over hun levensduur met een klein variatievenster te vergroten:

```

workspace.Mist.RiseMist.Mist.Size = NumberSequence.new{NumberSequenceKeypoint.new(0,20,1), NumberSequenceKeypoint.new(1,25,5)}

```

4.

Maak de regenboog.

1.

Voeg een blok  onderdeel toe aan Mist , en hernoem deze naar RainbowPart .

2.

Positioneer RainbowPart  iets boven de andere blokonderdelen.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Rainbow-4B.png)

3.

Voeg een ParticleEmitter  toe aan Rainbow , en hernoem de emitter naar Rainbow .

4.

Selecteer Rainbow , en stel in het Properties  venster,

1.

Stel Texture  in op rbxassetid://16828911033  om deeltjes te renderen die eruitzien als een vage regenboog.

2.

Stel Size  in op 25  om grote deeltjes te renderen.

3.

Stel Transparency  in op een getallenreeks waarin deeltjes beginnen als transparant, dan iets ondoorzichtig worden, en dan weer transparant worden over hun levensduur.

-

Time  = 0 , Value  = 1 , Envelope  = 0

-

Time  = 0.497 , Value  = 0.363 , Envelope  = 0.05

-

Time  = 1 , Value  = 1 , Envelope  = 0

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-waterfalls/Rainbow-4D.png)

1.

Stel Lifetime  in op 2, 4  om de levensduur van elk deeltje willekeurig in te stellen tussen 200 en 400 milliseconden.

2.

Stel Rate  in op 0.25  om elke 4 seconden een deeltje uit te stoten.

3.

Stel Rotation  in op -20  om elk deeltje een lichte hoek te geven.

4.

Stel Speed  in op 0  om elk deeltje 0 studs per seconde uit te stoten.

5.

Stel Drag  in op 1  om deeltjes hun snelheid te laten verliezen met exponentiële afname.

6.

Stel LightEmission  in op 1  om additieve menging te gebruiken om de deeltjes met de kleuren achter hen te renderen. Deze stap verwijdert ook de zwarte achtergrond van de textuur zelf.

7.

Stel LightInfluence  in op 0  om te voorkomen dat het omgevingslicht de kleur van de deeltjes beïnvloedt.

5.

In het Explorer  venster, selecteer alle blokonderdelen in de Mist  map, en stel in het Properties  venster Transparency  in op 1  om de blokken onzichtbaar te maken.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
