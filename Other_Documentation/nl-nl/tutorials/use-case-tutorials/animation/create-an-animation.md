<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/animation/create-an-animation -->

Maak karakteranimaties | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Animatie
6. /
7. In Studio

# Maak karakteranimaties

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Karakteranimaties  omvatten een reeks belangrijke poses die programmatisch samenkomen om je personages te laten lijken alsof ze zich in hun omgeving bewegen. Terwijl Roblox een set standaard karakteranimaties voor elk spel biedt, helpt het maken van aangepaste animaties voor je personages spelers om hun unieke persoonlijkheden te begrijpen aan de hand van hoe ze zich gedragen en interageren met andere personages.

Met het [Walking Character Animations](https://www.roblox.com/games/134383324873456/Walking-Character-Animation)  .rbxl  bestand als startpunt, laat deze tutorial je zien hoe je een loopcyclus karakteranimatie van begin tot eind kunt maken, inclusief begeleiding over:

-

Het toevoegen van een vooraf gebouwde karakterrig aan de 3D-ruimte die je kunt verplaatsen en roteren in verschillende belangrijke poses.

-

Het ontleden van een referentieafbeelding om je animatiebeslissingen te begeleiden en ervoor te zorgen dat elke pose de persoonlijkheid van je karakter weerspiegelt.

-

Het herhalen van de animatie om te testen hoe deze eruitziet bij verschillende snelheden, hoeken en easing-stijlen.

-

Het publiceren van de animatie zodat je deze kunt gebruiken in verschillende projecten in verschillende scripts en contexten.

Nadat je deze tutorial hebt voltooid, heb je een asset-ID voor je animatie en vaardigheden om aanvullende soorten animaties te maken die voldoen aan de behoeften van je eigen personages en spellen.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Ref-All.jpg)

## [Voeg rig toe](#voeg-rig-toe)[](#voeg-rig-toe)

Rigs , of verzamelingen van onderdelen die zijn verbonden door gewrichten zoals [Bone](/docs/nl-nl/reference/engine/classes/Bone)  of [Motor6D](/docs/nl-nl/reference/engine/classes/Motor6D)  objecten, zijn noodzakelijk om karakteranimaties te maken omdat ze de interne structuur bevatten die je nodig hebt om lichaamsdelen in verschillende poses te verplaatsen en te roteren. Terwijl je [je eigen rigs kunt maken](/docs/nl-nl/art/modeling/rig-a-humanoid-model)  met externe 3D-modelleringshulpmiddelen, biedt Studio verschillende vooraf gebouwde [standaard](/docs/nl-nl/avatar/character-bodies/specifications#standaard-r15-rigs)  en [geavanceerde](/docs/nl-nl/avatar/character-bodies/specifications#geavanceerde-r15-rigs)  R15 rigs die je kunt openen via de [Rig Generator](/docs/nl-nl/studio/rig-builder)  tool.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Masculine-Skinned-Rig.jpg) R15 Mannelijke Geklede Rig

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Masculine-Block-Rig.jpg) R15 Mannelijke Blok Rig

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Feminine-Rthro-Rig.jpg) R15 Vrouwelijke Rthro Rig

De rig die je kiest om te animeren is je eerste belangrijke ontwerpbeschikking omdat de vorm van het lichaam direct invloed heeft op hoe  je het karakter animeert. Bijvoorbeeld, een mannelijke blokkarakter heeft veel massa door zijn lichaam met een minimale bewegingsvrijheid, dus het karakter kan zijn gewicht verschuiven terwijl hij met een langzame, korte stap loopt. Omgekeerd heeft een vrouwelijke rthro rig meer massa bij de heupen met een veel realistischere bewegingsvrijheid, dus het karakter kan wiegen terwijl ze hun gewicht verdelen met een snelle, lange stap.

De rest van de tutorial biedt een diepgaande analyse van de verschillende ontwerpbeschikkingen en technieken die je kunt gebruiken bij het animeren van verschillende soorten rigs. Terwijl je deze beslissingen voor een rthro mannelijke rig beoordeelt, leer je hoe je je methoden kunt aanpassen om te voldoen aan de vereisten van je eigen personages en wereld.

Om een vooraf gebouwde rig aan de 3D-ruimte toe te voegen:

1.

Klik op de Home  of Avatar  tab in de werkbalk en klik op Character .

2.

Selecteer een rigtype, lichaamsvorm en vervolgens een avataroptie. Deze tutorial gebruikt bijvoorbeeld een R15  rigtype, een mannelijke  lichaamsvorm en een Rthro Avatar . De rig wordt weergegeven in de viewport.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Add-Rig-2.jpg)

## [Pose rig](#pose-rig)[](#pose-rig)

Elke animatie bestaat uit een reeks belangrijke poses op verschillende frames, waarna Studio programmatisch interpoleert , of "invult", de tussenliggende frames om een soepele beweging te creëren. Bijvoorbeeld, als je een belangrijke pose zou maken van een arm die naar de lucht reikt op het 0:00 frame, en dan een andere belangrijke pose van dezelfde arm die naar de grond reikt op het 0:09 frame, vult Studio de frames 0:01-0:08 tussen de poses in.

Dit proces wordt tweening  of inbetweening  genoemd, en het betekent dat je niet elke frame handmatig hoeft te animeren. In plaats daarvan kun je gewoon de belangrijke poses animeren die je wilt dat je karakter maakt om hun persoonlijkheid te benadrukken, en vervolgens de geïnterpoleerde frames bewerken totdat je tevreden bent met het eindresultaat.

Loopcycli voor humanoïde karakters hebben doorgaans 4 belangrijke poses die herhalen voor elke stap van de voet:

-

Contact  - Het moment waarop één voet de grond raakt voor het karakter, en de andere op het punt staat om achter het karakter op te tillen. Beide voeten ondersteunen het gewicht van het karakter.

-

Laag  - Het moment waarop de voorste voet volledig het gewicht van het karakter ondersteunt, en het achterste been van de grond komt.

-

Passeren  - Het midden van de stap wanneer het achterste been het voorste been passeert, en het gewicht van het karakter begint te verschuiven van de ene voet naar de andere.

-

Hoog  - Het moment waarop het karakter zijn lichaam op zijn nieuwe achterste voet tilt, en de nieuwe voorste voet op het punt staat om de grond te raken.

Om te demonstreren hoe dit werkt, laten we de volgende loopcyclusreferentie bekijken waar een gele humanoïde robot eerst met zijn linkervoet een stap zet, en dan met zijn rechtervoet. Let op dat de linkerarm en het linkerbeen van de robot paars zijn om te onderscheiden hoe elke kant van het lichaam beweegt tijdens de loopcyclus.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Ref-Feet.jpg)

Terwijl de robot overgaat van de Contact  naar de Laag  pose, valt zijn gewicht naar voren en trekt het lichaam van de robot naar de grond. Nadat de robot zichzelf heeft opgevangen en weer rechtop staat, valt zijn gewicht naar achteren en lanceert zijn lichaam naar voren terwijl de robot overgaat van de Passeren  naar de Hoog  pose. Als je naar het hoofd van het karakter kijkt tijdens de loopcyclus, kun je zien hoe het valt en stijgt met elke stap.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Ref-Head.jpg)

Hoewel het centrale idee van deze belangrijke poses hetzelfde blijft voor alle loopcycli, benadrukken verschillende karakters verschillende delen van de cyclus, afhankelijk van hoe ze zich voelen of wie ze zijn, zoals hun persoonlijkheid, leeftijd, genderexpressie en welzijn. Bijvoorbeeld:

-

Een oudere karakter kan naar voren gebogen zijn en langzame stappen zetten die nauwelijks de grond verlaten.

-

Een timide karakter kan zijn armen ingetrokken houden en zijn hoofd naar beneden houden om oogcontact te vermijden.

-

Een koud karakter kan zijn armen over elkaar slaan en gemeten stappen zetten terwijl ze om zich heen kijken naar warmte.

Animatie is een kunstvorm, en de ontwerpbeschikkingen die je maakt voor je karakter kunnen er anders uitzien dan de ontwerpbeschikkingen binnen deze tutorial voor de mannelijke Rthro rig. Terwijl de volgende instructie zich richt op hoe je de belangrijke poses voor de loopcyclus van een zelfverzekerd karakter kunt recreëren, voel je vrij om de leerervaringen aan te passen aan de ontwerpeisen voor je eigen spellen.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Ref-Masculine-Rig.jpg)

### [Linker stap](#linker-stap)[](#linker-stap)

De eerste stap voor een loopcyclus is het creëren van de vier belangrijke poses die de linker stap van het karakter vormen, of de stap die ze zetten om vooruit te bewegen met hun linkervoet. Terwijl je elke pose voltooit, overweeg hoe het gewicht van het karakter verschuift van een evenwichtige verdeling tussen beide voeten naar balanceren op één voet, en hoe dat de beweging door de rest van hun lichaam beïnvloedt.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/LeftStepSequence.jpg)

#### [Contact](#contact)[](#contact)

De Contact  pose voor de linker stapsequentie vertegenwoordigt het moment waarop de linkervoet de grond raakt voor het karakter terwijl de rechtervoet op het punt staat om achter het karakter op te tillen. Beide armen van het karakter zwaaien in de tegenovergestelde richting van hun respectieve benen; bijvoorbeeld, omdat de linkervoet voor het karakter staat, is hun linkerarm achter het karakter.

Dit is een belangrijk moment in de stap van een karakter omdat beide voeten het gewicht van het karakter gelijkmatig ondersteunen terwijl ze in beweging zijn.

Om een eerste versie van de Contact-pose voor de linker voetcyclus te maken:

1.

Klik op de Avatar  tab in de werkbalk en klik op Clip Editor . Het [Animatie-editor](/docs/nl-nl/animation/editor)  venster wordt weergegeven.

2.

Selecteer je rig. Een contextmenu wordt weergegeven.

3.

Vul in het veld Animatienaam  een naam in voor je animatie en klik vervolgens op de Maak  knop.

4.

OPTIONEEL

 Stel de tijdlijn in op 24 frames per seconde.

1.

Klik in de afspeelhulpmiddelen van de editor op het tandwielpictogram.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Gear-Icon.png)

2.

Stel vanuit het contextmenu de Frame Rate  in op 24 fps .

5.

Voeg een keyframe toe voor elk van de lichaamsdelen van de rig aan de tracklijst van de editor.

1.

Klik in de Animatie-editor  op de +  knop. Een contextmenu wordt weergegeven.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-Contact-2A.png)

2.

Selecteer Voeg alle lichaamsdelen toe . De tracklijst van de editor wordt bijgewerkt met alle lichaamsdelen van de rig.

3.

Klik met de rechtermuisknop op de bovenste balk onder de tijdlijn en selecteer in het contextmenu Voeg keyframe toe . De editor voegt een keyframe toe voor elk lichaamsdeel in de tijdlijn.

6.

Pose het bovenlichaam van de rig in een gebogen positie.

1.

Selecteer het Roteren  gereedschap in de werkbalk.

2.

Selecteer en kantel het lichaamsdeel UpperTorso  in de viewport zodat de torso iets naar voren is gebogen.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-Contact-3A.jpg)

3.

Selecteer en kantel het lichaamsdeel Head  zodat het gezicht van de rig recht vooruit kijkt.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-Contact-3B.jpg)

7.

Pose de benen van de rig zodat de linkervoet de grond raakt voor de rig terwijl de rechtervoet de grond raakt achter de rig.

1.

Selecteer en kantel in de viewport de lichaamsdelen LeftUpperLeg , LeftLowerLeg  en LeftFoot  totdat het linkerbeen gebogen is terwijl de linkervoet iets is opgetild.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-Contact-4A.jpg)

2.

Herhaal dit proces voor de lichaamsdelen RightUpperLeg , RightLowerLeg  en RightFoot  totdat het rechterbeen gebogen is terwijl de tenen van de voet de grond raken.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-Contact-4B.jpg)

8.

Pose de armen van de rig zodat elke respectieve arm zo ver mogelijk naar voren of achter de rig zwaait voor de stap van het karakter.

1.

Selecteer en kantel in de viewport de lichaamsdelen LeftUpperArm  en LeftLowerArm  totdat de linkerarm zichtbaar is en iets gebogen achter de rig.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-Contact-5A.jpg)

2.

Herhaal dit proces voor de lichaamsdelen RightUpperArm  en RightLowerArm  totdat de rechterarm iets gebogen is voor de rig.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-Contact-5B.jpg)

9.

Sla de animatie op.

1.

Selecteer in de Media- en afspeelbediening  de ellipsknop. Een contextmenu wordt weergegeven.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-Contact-6A.png)

2.

Selecteer Opslaan .

Totdat je een animatie publiceert, wordt deze lokaal opgeslagen in je plaatsbestand en kan deze niet in andere spellen worden gebruikt. Wanneer je een animatie opslaat, wordt je spel niet  opgeslagen.

#### [Laag](#laag)[](#laag)

De Laag  pose voor de linker stapsequentie vertegenwoordigt het moment waarop de linkervoet volledig het gewicht van het karakter ondersteunt terwijl ze naar de grond vallen, en hun rechterbeen van de grond komt om de ongelijke gewichtsverdeling tussen hun benen te compenseren.

Deze belangrijke pose in zowel de linker als de rechter stapsequenties is wanneer het karakter zo laag bij de grond is als ze zullen zijn in hun stap omdat ze naar voren vallen voordat hun voorste voet hun afdaling stopt. De voorwaartse beweging van dit proces zorgt er ook voor dat het bovenlichaam en het hoofd naar de grond hellen, wat je kunt overdrijven voor meer energieke karakters.

Om een eerste versie van de Laag-pose voor de linker voetcyclus te maken:

1.

Klik en sleep in het Explorer  venster de scrubber naar het 3e frame.

2.

Pose het bovenlichaam van de rig zodat het nog meer naar de grond leunt dan de vorige pose.

1.

Selecteer en kantel in de viewport het lichaamsdeel UpperTorso  zodat de torso aanzienlijk naar voren is gebogen.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-Low-2A.jpg)

2.

Selecteer en kantel het lichaamsdeel Head  zodat het gezicht van de rig naar de grond kijkt.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-Low-2B.jpg)

3.

Pose de benen van de rig zodat het lichaamsgewicht van de rig wordt ondersteund door zijn linkervoet.

1.

Selecteer en kantel in de viewport de lichaamsdelen LeftUpperLeg , LeftLowerLeg  en LeftFoot  totdat het linkerbeen bijna gebogen is in een hoek van 90 graden met een voet plat op de grond.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-Low-3A.jpg)

2.

Herhaal dit proces voor de lichaamsdelen RightUpperLeg , RightLowerLeg  en RightFoot  totdat het rechterbeen bijna recht achter de rig is met de onderkant van de voet naar de lucht gekanteld.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-Low-3B.jpg)

4.

Beweeg de rig naar beneden zodat zijn linkervoet de grond raakt.

1.

Selecteer in de viewport het lichaamsdeel LowerTorso .

2.

Beweeg het naar beneden totdat de linkervoet van de rig parallel aan de grond is.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-Low-4.jpg)

5.

Pose de armen van de rig zodat ze dichter bij de torso zwaaien.

1.

Selecteer en kantel in de viewport de lichaamsdelen LeftUpperArm  en LeftLowerArm  totdat de linkerarm dichter bij de taille van het karakter is.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-Low-5A.jpg)

2.

Herhaal dit proces voor de lichaamsdelen RightUpperArm  en RightLowerArm  totdat de rechterarm dichter bij de taille van het karakter is.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-Low-5B.jpg)

6.

Sla de animatie op.

#### [Passeren](#passeren)[](#passeren)

De Passeren  pose voor de linker stapsequentie vertegenwoordigt het moment waarop het rechterbeen het linkerbeen passeert, en het gewicht van het karakter begint te verschuiven van de linkervoet naar de rechtervoet. Beide armen van het karakter vallen naar de taille terwijl ze in tegenovergestelde richtingen zwaaien, wat ervoor zorgt dat het karakter lijkt alsof ze rechtop staan zoals een flamingo.

Om een eerste versie van de Passeren-pose voor de linker voetcyclus te maken:

1.

Klik en sleep in het Explorer  venster de scrubber naar het 6e frame.

2.

Pose het bovenlichaam van de rig in een rechte positie.

1.

Selecteer en kantel in de viewport het lichaamsdeel UpperTorso  zodat de torso ongeveer 90 graden met de grond is.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-Passing-2A.jpg)

2.

Selecteer en kantel het lichaamsdeel Head  zodat het gezicht van de rig weer recht vooruit kijkt.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-Passing-2B.jpg)

3.

Pose de benen van de rig zodat het karakter zijn gewicht balanceert op zijn linkervoet terwijl het rechterbeen naar voren zwaait.

1.

Selecteer en kantel in de viewport de lichaamsdelen LeftUpperLeg , LeftLowerLeg  en LeftFoot  totdat het linkerbeen bijna recht is met een platte voet op de grond.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-Passing-3A.jpg)

2.

Herhaal dit proces voor de lichaamsdelen RightUpperLeg , RightLowerLeg  en RightFoot  totdat het rechterbeen gebogen is in een hoek van 45 graden met de voorkant van de voet naar de grond gekanteld.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-Passing-3B.jpg)

4.

Beweeg de rig omhoog zodat zijn linkervoet de grond raakt.

1.

Selecteer in de viewport het lichaamsdeel LowerTorso .

2.

Beweeg het omhoog totdat de linkervoet van de rig parallel aan de grond is.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-Passing-4.jpg)

5.

Pose de armen van de rig zodat ze aan weerszijden van de taille van het karakter vallen.

1.

Selecteer en kantel in de viewport de lichaamsdelen LeftUpperArm  en LeftLowerArm  totdat de linkerarm bijna recht is aan de linkerkant van het karakter.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-Passing-5A.jpg)

2.

Herhaal dit proces voor de lichaamsdelen RightUpperArm  en RightLowerArm  totdat de rechterarm bijna recht is aan de rechterkant van het karakter.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-Passing-5B.jpg)

6.

Sla de animatie op.

#### [Hoog](#hoog)[](#hoog)

De Hoog  pose voor de linker stapsequentie vertegenwoordigt het moment waarop het karakter zijn lichaam op zijn linkervoet tilt terwijl zijn rechtervoet op het punt staat de grond te raken. Het grootste deel van het gewicht van het karakter balanceert op zijn tenen, die op hun beurt van de grond afduwen om hen naar voren te stuwen.

Deze belangrijke pose in zowel de linker als de rechter stapsequenties is wanneer het karakter zo hoog boven de grond is als ze zullen zijn in hun stap omdat ze zich afduwen van de vloer. Let op dat de voorwaartse beweging van dit proces ook ervoor zorgt dat het bovenlichaam en het hoofd naar de lucht hellen, wat je kunt overdrijven voor meer optimistische karakters.

Om een eerste versie van de Hoog-pose voor de linker voetcyclus te maken:

1.

Klik en sleep in het Explorer  venster de scrubber naar het 9e frame.

2.

Pose het bovenlichaam van de rig zodat de borst naar de lucht gericht is.

1.

Selecteer en kantel in de viewport het lichaamsdeel UpperTorso  zodat het karakter iets naar achteren is gekanteld.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-High-2A.jpg)

2.

Selecteer en kantel het lichaamsdeel Head  zodat het gezicht van de rig naar de lucht kijkt.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-High-2B.jpg)

3.

Pose de benen van de rig zodat het gewicht van het karakter naar voren verschuift van de tenen van zijn linkervoet naar de dij van zijn rechterbeen.

1.

Selecteer en kantel in de viewport de lichaamsdelen LeftUpperLeg , LeftLowerLeg  en LeftFoot  totdat het linkerbeen bijna recht is met de voet bijna loodrecht op de grond.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-High-3A.jpg)

2.

Herhaal dit proces voor de lichaamsdelen RightUpperLeg , RightLowerLeg  en RightFoot  totdat het rechterbeen gebogen is in een bijna 90 graden hoek voor het karakter.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-High-3B.jpg)

4.

Beweeg de rig omhoog zodat zijn linkervoet de grond raakt.

1.

Selecteer in de viewport het lichaamsdeel LowerTorso .

2.

Beweeg het iets omhoog totdat de tenen van de linkervoet de grond raken.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-High-4.jpg)

5.

Pose de armen van de rig zodat ze verder van de torso zwaaien.

1.

Selecteer en kantel in de viewport de lichaamsdelen LeftUpperArm  en LeftLowerArm  totdat de linkerarm verder van de taille van het karakter is.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-High-5A.jpg)

2.

Herhaal dit proces voor de lichaamsdelen RightUpperArm  en RightLowerArm  totdat de rechterarm verder van de taille van het karakter is.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-High-5B.jpg)

6.

Sla de animatie op.

### [Rechter stap](#rechter-stap)[](#rechter-stap)

De tweede stap voor een loopcyclus is het creëren van de vier belangrijke poses die de rechter stap van het karakter vormen, of de stap die ze zetten om vooruit te bewegen met hun rechtervoet. Terwijl deze tutorial zich richt op het recreëren van hetzelfde proces als de linker voetsequentie van het karakter, kun je subtiele aanpassingen maken die persoonlijkheid aan je loopcyclus toevoegen, zoals een leun naar rechts of extra pep in hun rechter stap.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/RightStepReference.jpg)

#### [Contact](#contact-1)[](#contact-1)

De Contact  pose voor de rechter stapsequentie vertegenwoordigt het moment waarop de rechtervoet de grond raakt voor het karakter terwijl de linkervoet op het punt staat om achter het karakter op te tillen. Het grootste deel van het proces voor het creëren van deze pose is hetzelfde als de linker stapsequentie, maar het is nuttig om de rig eerst in dezelfde verticale oriëntatie te positioneren als de Contact-pose voor de linker stapsequentie, zodat het karakter een consistentere gang heeft.

Om een eerste versie van de Contact-pose voor de rechter voetcyclus te maken:

1.

Klik en sleep in het Explorer  venster de scrubber naar het 12e frame.

2.

Beweeg de rig naar beneden zodat het karakter in dezelfde start verticale positie is als de Contact-pose van de linker stap.

1.

Selecteer in de viewport het lichaamsdeel LowerTorso .

2.

Beweeg het naar beneden totdat het hoofd van de rig onder de paarse referentielijn is.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-Contact-2.jpg)

3.

Pose het bovenlichaam van de rig in dezelfde gebogen positie als de Contact-pose van de linker stap.

1.

Selecteer en kantel in de viewport het lichaamsdeel UpperTorso  zodat de torso iets naar voren is gebogen.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-Contact-3A.jpg)

2.

Selecteer en kantel het lichaamsdeel Head  zodat het gezicht van de rig recht vooruit kijkt.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-Contact-3B.jpg)

4.

Pose de benen van de rig zodat de rechtervoet de grond raakt voor de rig terwijl de linkervoet de grond raakt achter de rig.

1.

Selecteer en kantel in de viewport de lichaamsdelen LeftUpperLeg , LeftLowerLeg  en LeftFoot  totdat het linkerbeen gebogen is terwijl de tenen van de voet de grond raken.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-Contact-4A.jpg)

2.

Herhaal dit proces voor de lichaamsdelen RightUpperLeg , RightLowerLeg  en RightFoot  totdat het rechterbeen gebogen is terwijl de voet iets is opgetild.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-Contact-4B.jpg)

5.

Pose de armen van de rig zodat elke respectieve arm zo ver mogelijk naar voren of achter de rig zwaait voor de stap van het karakter.

1.

Selecteer en kantel in de viewport de lichaamsdelen LeftUpperArm  en LeftLowerArm  totdat de linkerarm zichtbaar is en iets gebogen is voor de rig.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-Contact-5A.jpg)

2.

Herhaal dit proces voor de lichaamsdelen RightUpperArm  en RightLowerArm  totdat de rechterarm iets gebogen is achter de rig.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-Contact-5B.jpg)

6.

Sla de animatie op.

#### [Laag](#laag-1)[](#laag-1)

De Laag  pose voor de rechter stapsequentie vertegenwoordigt het moment waarop de rechtervoet volledig het gewicht van het karakter ondersteunt terwijl ze naar de grond vallen, en hun linkervoet van de grond komt om de ongelijke gewichtsverdeling tussen hun benen te compenseren. Net als bij de vorige pose, hoewel niet verplicht, is het nuttig om de rig in dezelfde verticale oriëntatie te positioneren als de Laag-pose voor de linker stapsequentie, zodat het karakter niet meer naar voren valt op hun rechterbeen dan op hun linker.

Om een eerste versie van de Laag-pose voor de rechter voetcyclus te maken:

1.

Klik en sleep in het Explorer  venster de scrubber naar het 15e frame.

2.

Beweeg de rig naar beneden zodat het karakter in dezelfde start verticale positie is als de Laag-pose van de linker stap.

1.

Selecteer in de viewport het lichaamsdeel LowerTorso .

2.

Beweeg het naar beneden totdat het hoofd van de rig iets boven de grijze referentielijn is.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-Low-2.jpg)

3.

Pose het bovenlichaam van de rig in dezelfde gebogen positie als de Laag-pose van de linker stap.

1.

Selecteer en kantel in de viewport het lichaamsdeel UpperTorso  zodat de torso aanzienlijk naar voren is gebogen.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-Low-3A.jpg)

2.

Selecteer en kantel het lichaamsdeel Head  zodat het gezicht van de rig naar de grond kijkt.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-Low-3B.jpg)

4.

Pose de benen van de rig zodat het lichaamsgewicht van de rig wordt ondersteund door zijn rechterbeen.

1.

Selecteer en kantel in de viewport de lichaamsdelen LeftUpperLeg , LeftLowerLeg  en LeftFoot  totdat het linkerbeen bijna recht achter de rig is met de onderkant van de voet naar de lucht gekanteld.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-Low-4A.jpg)

2.

Herhaal dit proces voor de lichaamsdelen RightUpperLeg , RightLowerLeg  en RightFoot  totdat het rechterbeen bijna gebogen is in een hoek van 90 graden met een voet plat op de grond.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-Low-4B.jpg)

5.

Pose de armen van de rig zodat ze dichter bij de torso zwaaien.

1.

Selecteer en kantel in de viewport de lichaamsdelen LeftUpperArm  en LeftLowerArm  totdat de linkerarm dichter bij de taille van het karakter is.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-Low-5A.jpg)

2.

Herhaal dit proces voor de lichaamsdelen RightUpperArm  en RightLowerArm  totdat de rechterarm dichter bij de taille van het karakter is.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-Low-5B.jpg)

6.

Sla de animatie op.

#### [Passeren](#passeren-1)[](#passeren-1)

De Passeren  pose voor de rechter stapsequentie vertegenwoordigt het moment waarop het linkerbeen het rechterbeen passeert, en het gewicht van het karakter begint te verschuiven van de rechtervoet naar de linkervoet.

Om een eerste versie van de Passeren-pose voor de rechter voetcyclus te maken:

1.

Klik en sleep in het Explorer  venster de scrubber naar het 18e frame.

2.

Beweeg de rig omhoog zodat het karakter in dezelfde start verticale positie is als de Passeren-pose van de linker stap.

1.

Selecteer in de viewport het lichaamsdeel LowerTorso .

2.

Beweeg het omhoog totdat het hoofd van de rig iets onder de paarse referentielijn is.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-Passing-2.jpg)

3.

Pose het bovenlichaam van de rig in dezelfde rechte positie als de Passeren-pose van de linker stap.

1.

Selecteer en kantel in de viewport het lichaamsdeel UpperTorso  zodat de torso ongeveer 90 graden met de grond is.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-Passing-3A.jpg)

2.

Selecteer en kantel het lichaamsdeel Head  zodat het gezicht van de rig weer recht vooruit kijkt.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-Passing-3B.jpg)

4.

Pose de benen van de rig zodat het karakter zijn gewicht balanceert op zijn rechterbeen terwijl het linkerbeen naar voren zwaait.

1.

Selecteer en kantel in de viewport de lichaamsdelen LeftUpperLeg , LeftLowerLeg  en LeftFoot  totdat het linkerbeen gebogen is in een hoek van 45 graden met de voorkant van de voet naar de grond gekanteld.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-Passing-4A.jpg)

2.

Herhaal dit proces voor de lichaamsdelen RightUpperLeg , RightLowerLeg  en RightFoot  totdat het rechterbeen bijna recht is met een platte voet op de grond.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-Passing-4B.jpg)

5.

Pose de armen van de rig zodat ze aan weerszijden van de taille van het karakter vallen.

1.

Selecteer en kantel in de viewport de lichaamsdelen LeftUpperArm  en LeftLowerArm  totdat de linkerarm bijna recht is aan de linkerkant van het karakter.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-Passing-5A.jpg)

2.

Herhaal dit proces voor de lichaamsdelen RightUpperArm  en RightLowerArm  totdat de rechterarm bijna recht is aan de rechterkant van het karakter.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-Passing-5B.jpg)

6.

Sla de animatie op.

#### [Hoog](#hoog-1)[](#hoog-1)

De Hoog  pose voor de rechter stapsequentie vertegenwoordigt het moment waarop het karakter zijn lichaam op zijn rechtervoet tilt terwijl zijn linkervoet op het punt staat de grond te raken.

Om een eerste versie van de Hoog-pose voor de rechter voetcyclus te maken:

1.

Klik en sleep in het Explorer  venster de scrubber naar het 21e frame.

2.

Beweeg de rig omhoog zodat het karakter in dezelfde start verticale positie is als de Hoog-pose van de linker stap.

1.

Selecteer in de viewport het lichaamsdeel LowerTorso .

2.

Beweeg het omhoog totdat het hoofd van de rig de paarse referentielijn overlapt.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-High-2.jpg)

3.

Pose het bovenlichaam van de rig in dezelfde gekantelde positie als de Hoog-pose van de linker stap.

1.

Selecteer en kantel in de viewport het lichaamsdeel UpperTorso  zodat het karakter iets naar achteren is gekanteld.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-High-3A.jpg)

2.

Selecteer en kantel het lichaamsdeel Head  zodat het gezicht van de rig naar de lucht kijkt.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-High-3B.png)

4.

Pose de benen van de rig zodat het gewicht van het karakter naar voren verschuift van de tenen van zijn rechtervoet naar de dij van zijn linkerbeen.

1.

Selecteer en kantel in de viewport de lichaamsdelen LeftUpperLeg , LeftLowerLeg  en LeftFoot  totdat het linkerbeen gebogen is in een bijna 90 graden hoek voor het karakter.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-High-4A.jpg)

2.

Herhaal dit proces voor de lichaamsdelen RightUpperLeg , RightLowerLeg  en RightFoot  totdat het rechterbeen bijna recht is met de voet bijna loodrecht op de grond.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-High-4B.jpg)

5.

Pose de armen van de rig zodat ze verder van de torso zwaaien.

1.

Selecteer en kantel in de viewport de lichaamsdelen LeftUpperArm  en LeftLowerArm  totdat de linkerarm verder van de taille van het karakter is.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-High-5A.jpg)

2.

Herhaal dit proces voor de lichaamsdelen RightUpperArm  en RightLowerArm  totdat de rechterarm verder van de taille van het karakter is.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Right-High-5B.jpg)

6.

Sla de animatie op.

## [Test animatie](#test-animatie)[](#test-animatie)

Nadat je je eerste versie van je belangrijke poses hebt voltooid, is het belangrijk om je animatie te testen om te zien hoe deze samenvloeit. Als er inconsistenties of haperige overgangen zijn, kun je subtiele aanpassingen maken om ervoor te zorgen dat de animatie zo soepel is als het zou moeten zijn voor het lichaam en de persoonlijkheid van je karakter.

Met andere woorden, als je wilt dat je karakter gracieus en lichtvoetig is, moeten hun bewegingen vloeiend zijn en samenkomen. Als je echter wilt dat je karakter onhandig is en struikelt terwijl ze lopen, zijn soepele overgangen misschien minder wenselijk voor hoe je wilt dat ze zich in je spel presenteren.

Om je poses te testen:

1.

Klik op de lusknop in de afspeelhulpmiddelen van de Animatie-editor  om de animatie oneindig te herhalen.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Test-1.png)

2.

Klik op de afspeelknop om de animatie te starten.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Test-2.png)

3.

Beoordeel je animatie om te zien waar deze aanpassingen nodig heeft.

1.

Vertraag de snelheid van je animatie.

1.

Klik in de afspeelhulpmiddelen op het tandwielpictogram.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Gear-Icon.png)

1.

Stel vanuit het contextmenu de Afspeelsnelheid  in op 0.25x  of 0.5x .

2.

Evalueer de animatie vanuit meerdere hoeken.

1.

Schakel in het View  menu van Studio Toon weergave-selector  in.

2.

Klik in de viewport op een van de 14 vlakken van de weergave-selector om je camera naar een andere wereldoriëntatie te verplaatsen.

3.

Selecteer, verplaats en roteer je rig totdat de animatie overeenkomt met de persoonlijkheid van je karakter.

## [Publiceer animatie](#publiceer-animatie)[](#publiceer-animatie)

Om je animatie in je open spel af te spelen, evenals om deze op te slaan voor hergebruik in andere projecten, moet je de animatie naar de cloud publiceren. Dit proces creëert een unieke asset-ID voor je animatie die je in scripts kunt verwijzen, wat vooral belangrijk is als je een van de standaard karakteranimaties van Roblox wilt vervangen.

Om je animatie te publiceren:

1.

Klik in de linkerbovenhoek van de Animatie-editor  op de ellipsknop.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Left-Contact-6A.png)

2.

Selecteer in het contextmenu Publiceer naar Roblox . Het Assetconfiguratievenster  wordt weergegeven.

3.

Vul alle toepasselijke velden in en klik vervolgens op de Opslaan  knop.

4.

OPTIONEEL

 Je kunt de asset-ID van de animatie kopiëren om deze binnen scripts te gebruiken door op het kopieerpictogram te klikken.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Publish-4.png)

Nu je animatie in de cloud staat, kun je de asset vinden, bewerken en hergebruiken in al je projecten via het [Creator Dashboard](https://create.roblox.com/dashboard/creations)  onder Ontwikkelingsitems  ⟩ Animaties .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-character-animations/Creations-Animations.png)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
