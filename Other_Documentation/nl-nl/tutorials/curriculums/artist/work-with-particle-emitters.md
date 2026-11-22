<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/curriculums/artist/work-with-particle-emitters -->

Werken met deeltjesemitters | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Werken met deeltjesemitters

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Deeltjesemitters  creëren speciale effecten door 2D-afbeeldingen, ook wel deeltjes genoemd, in de 3D-wereld uit te stoten. Door aan te passen hoe de deeltjes eruitzien en zich gedragen terwijl ze in de omgeving worden uitgezonden, kun je visuele kunst creëren die je spellen uniek en boeiend maakt voor potentiële spelers.

Om dit te demonstreren, bekijk de Mansion of Wonder -sjabloon die de volgende drie afbeeldingen gebruikt om VFX-kunst in verschillende gebieden van de kermisattractie te creëren:

![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/particle-emitters/particle-star.png)
![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/particle-emitters/Short-Arrow-Down.png)

![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/particle-emitters/particle-flame.png)
![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/particle-emitters/Short-Arrow-Down.png)

![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/particle-emitters/particle-portal.png)
![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/particle-emitters/Short-Arrow-Down.png)

Met exact dezelfde technieken, laten we in dit hoofdstuk verkennen hoe we de deeltjesemitter voor de laserstraal en explosie van de kermisattractie kunnen vinden, en vervolgens hun eigenschappen kunnen aanpassen totdat je de saaie startdeeltjes transformeert in je eigen VFX-creaties.

## [Vind voorbeeldemitters](#vind-voorbeeldemitters)[](#vind-voorbeeldemitters)

De sjabloon van deze les biedt twee basisdeeltjesemitters waarmee spelers tijdens de kermisattractie interactie hebben:

-

Eén voor de laserstraal  die door de lucht vliegt wanneer spelers hun blaster afschieten.

-

Een andere voor de explosie  wanneer de laserstraal een spook of slijm vijand raakt.

Beide deeltjesemitters beginnen met eenvoudige witte deeltjes, zodat je je voortgang in realtime kunt zien terwijl je hun visuele uiterlijk en gedrag gedurende dit hoofdstuk aanpast.

Om de voorbeelddeeltjesemitters te vinden:

1.

Gebruik de volgende camerabesturingen om je camera te verplaatsen en een goed zicht te krijgen op de twee deeltjesemitterstands nabij de voorkant van het landhuis. De eerste deeltjesemitter die je gaat aanpassen is de laserstraal deeltjesemitter aan de linkerkant met de witte sprankels.

| Actie | | Besturing |
| --- | --- |
| Verplaatsen | | W  A  S  D |
| Draaien | | Houd de rechtermuisknop ingedrukt om rond het geselecteerde object te draaien. |
| Inzoomen | | Gebruik het scrollwiel van je muis. |
| Focussen | | Druk op F  om je op het geselecteerde object te focussen. |

 ![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/particle-emitters/particle-holder.png)

2.

Zoek de laserstraal deeltjesemitter.

1.

Ga in het Explorer -venster naar de zoekbalk en typ BlastParticles .

2.

Klik in je zoekresultaten op het resultaat van de deeltjesemitter.

 ![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/particle-emitters/select-blaster-shot.png)

Als je de Explorer  en Properties  vensters niet ziet, schakel ze dan in via het Venster  menu van Studio.

## [Pas laserstraal aan](#pas-laserstraal-aan)[](#pas-laserstraal-aan)

Wanneer je iets selecteert in de 3D-weergave of het Explorer -venster, wordt het Properties -venster bijgewerkt om alle eigenschappen weer te geven die je direct kunt aanpassen binnen de interface van Studio. Bijvoorbeeld, wanneer je de BlastParticles  deeltjesemitter in de vorige sectie selecteerde, werd het Properties -venster bijgewerkt met alle eigenschappen voor die specifieke deeltjesemitter.

Om je kennis van het aanpassen van eigenschappen te introduceren, laten we beginnen met het aanpassen van de kleur en afbeelding van de deeltjes van de laserstraal. Naarmate je meer vertrouwd raakt met dit proces, kun je experimenteren met meer eigenschappen.

### [Kleur](#kleur)[](#kleur)

De [Color](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Color)  eigenschap van een deeltjesemitter kleurt de textuur van elk deeltje naar een specifieke tint of een kleurverloop van het moment dat het wordt uitgezonden tot het moment dat het vervaagt. Deze les richt zich op het instellen van de deeltjes op een specifieke tint, maar je kunt meer leren over hoe je ze op een kleurverloop instelt in de [Deeltjesemitters](/docs/nl-nl/effects/particle-emitters#kleur)  gids nadat je de tutorial hebt voltooid.

Om de deeltjes van de laserstraal een nieuwe kleur te geven:

1.

Zoek in het Properties -venster de Kleur  eigenschap en dubbelklik op het lichtgrijze vakje aan de rechterkant. Een pop-up Kleuren  venster verschijnt.

 ![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/particle-emitters/select-color.png)

2.

Selecteer in het Kleuren  venster een kleur en klik vervolgens op de OK  knop. Als je bijvoorbeeld de Kleur  eigenschap instelt op 202, 210, 20 , zullen je deeltjes eruitzien als de onderstaande afbeelding.

 ![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/particle-emitters/show-color-change.png)

### [Textuur](#textuur)[](#textuur)

De [Texture](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Texture)  eigenschap van een deeltjesemitter vertelt de deeltjesemitter welke afbeelding, ook wel texturen  genoemd, in de omgeving moet worden uitgezonden. Texturen kunnen elke 2D-afbeelding zijn die je wilt, zoals een symbool of zelfs iets dat je hebt getekend. Bijvoorbeeld, de volgende video demonstreert hoe het veranderen van de textuur van een deeltjesemitter volledig verschillende effecten creëert.

Om de deeltjes van de laserstraal op een nieuwe textuur in te stellen:

1.

Kies een van de volgende afbeeldingen om te gebruiken als de textuur van de deeltjesemitter en kopieer vervolgens het assetID-nummer onder de afbeelding. Je kunt terugkeren naar dit startpakket van texturen wanneer je klaar bent om de explosie aan te passen.

![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/using-textures/star-1.png) rbxassetid://5860841663

![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/using-textures/swirl.png) rbxassetid://5857851812

![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/using-textures/heart.png) rbxassetid://5857851618

![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/using-textures/circle.png) rbxassetid://6711256324

![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/using-textures/smoke.png) rbxassetid://5833235272

![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/using-textures/star-2.png) rbxassetid://6772783963

![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/using-textures/spark.png) rbxassetid://5833323391

![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/using-textures/circle-2.png) rbxassetid://5857892330

![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/using-textures/scratch.png) rbxassetid://5857892405

![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/using-textures/trace.png) rbxassetid://5857931724

![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/using-textures/triangle.png) rbxassetid://5857851618

![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/using-textures/star-3.png) rbxassetid://5860841737

2.

Zoek in het Properties -venster de Textuur  eigenschap en klik erop om de tekst te markeren.

 ![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/using-textures/show-texture-property.png)

Als je niet dezelfde eigenschappen ziet als in de voorbeeldafbeelding, ga dan terug naar het Explorer -venster en selecteer opnieuw de BlastParticles  deeltjesemitter.

3.

Plak het assetID van je textuur door op Ctrl V  of ⌘ V  te drukken, afhankelijk van je computer, en druk vervolgens op Enter . Je deeltjesemitter stoot nu deeltjes uit die eruitzien als je textuur. Als je bijvoorbeeld de 5833323391  textuur gebruikt, zullen je deeltjes eruitzien als het voorbeeld hieronder.

 ![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/using-textures/texture-changed.png)

## [Pas explosie aan](#pas-explosie-aan)[](#pas-explosie-aan)

Nu je aangepaste VFX-kunst voor je laserstraal hebt, kun je verder gaan met het aanpassen van de explosie telkens wanneer de laserstraal een sinister slijm of griezelig spook raakt. Om te verifiëren dat je de eigenschappen van de explosie aanpast in plaats van de laserstraal, zorg ervoor dat je de explosie deeltjesemitter selecteert zodat het Properties -venster wordt bijgewerkt met de specifieke eigenschappen:

1.

Ga in het Explorer -venster naar de zoekbalk en typ ExplosionParticles .

2.

Klik in je zoekresultaten op het resultaat van de deeltjesemitter.

 ![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/particle-emitters/select-explosion.png)

Hoewel deze sectie zich richt op het aanpassen van de grootte en snelheid van de deeltjes van de explosie, voel je vrij om je eerdere kennis te gebruiken om ook hun kleur en textuur aan te passen.

### [Grootte](#grootte)[](#grootte)

De [Size](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Size)  eigenschap van een deeltjesemitter verandert de grootte van de textuur van elk deeltje naar een specifieke grootte of een grootte die verandert van het moment dat het wordt uitgezonden tot het moment dat het vervaagt. Deze les richt zich op het instellen van de deeltjes op een specifieke grootte, maar je kunt meer leren over hoe je ze op een veranderende grootte instelt in de [Deeltjesemitters](/docs/nl-nl/effects/particle-emitters#grootte)  gids nadat je de tutorial hebt voltooid.

Om de explosie deeltjes op een nieuwe grootte in te stellen:

1.

Zoek in het Properties -venster de Grootte  eigenschap.

2.

Voor de beste resultaten, stel de Grootte  in op een getal tussen 1  en 10 .

 ![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/make-final-touches/change-explode-size.png)

Als het om deeltjes gaat, is er geen "one size fits all"; verschillende deeltjes texturen zien er beter uit in verschillende groottes. Om dit te demonstreren, bekijk de volgende video om te zien hoe een stertextuur verandert naarmate de [Size](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Size)  waarde toeneemt.

### [Snelheid](#snelheid)[](#snelheid)

De [Speed](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Speed)  eigenschap van een deeltjesemitter verandert de snelheid waarmee de deeltjes uit de deeltjesemitter worden uitgezonden. Met andere woorden, je kunt deze eigenschap aanpassen om ervoor te zorgen dat de deeltjes snel of langzaam worden uitgezonden.

Om de explosie deeltjes op een nieuwe snelheid in te stellen:

1.

Zoek in het Properties -venster de Snelheid  eigenschap en stel deze in op een getal tussen 10  (langzaam) en 100  (snel).

 ![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/make-final-touches/change-speed.png)

2.

Gebruik je kennis uit het vorige hoofdstuk om het spel te testen en je deeltjes in actie te zien. Als er iets niet goed uitziet, kun je teruggaan en wijzigingen aanbrengen in je ontwerp.

## [Aanvullende eigenschappen](#aanvullende-eigenschappen)[](#aanvullende-eigenschappen)

Je VFX-kunst voor de laserstraal en explosie is bijna klaar! Terwijl je een paar eigenschappen van de deeltjesemitter hebt aangepast, zijn er nog veel meer die je kunt wijzigen om je werk te personaliseren. De volgende secties benadrukken er een paar, maar voel je vrij om ook te experimenteren met andere die hier niet zijn vermeld.

### [Lichtemissie](#lichtemissie)[](#lichtemissie)

De [LightEmission](/docs/nl-nl/reference/engine/classes/ParticleEmitter#LightEmission)  eigenschap laat de deeltjes gloeien. Hogere waarden van deze eigenschap kunnen ervoor zorgen dat de deeltjes zelfs in omgevingen met weinig licht gloeien.

![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/make-final-touches/light-emission-0.jpeg) 0

![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/make-final-touches/light-emission-0.5.jpeg) 0.5

![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/make-final-touches/light-emission-1.0.jpeg) 1

### [Rotatiesnelheid](#rotatiesnelheid)[](#rotatiesnelheid)

De [RotSpeed](/docs/nl-nl/reference/engine/classes/ParticleEmitter#RotSpeed)  eigenschap laat de deeltjes in de loop van de tijd draaien. Om te demonstreren hoe dit werkt, bekijk de volgende video om te zien hoe de rotatie van de rechte lijn textuur van de deeltjes verandert naarmate de [RotSpeed](/docs/nl-nl/reference/engine/classes/ParticleEmitter#RotSpeed)  eigenschap toeneemt.

### [Levensduur](#levensduur)[](#levensduur)

De [Lifetime](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Lifetime)  eigenschap verandert hoe lang in seconden de deeltjes zichtbaar zijn zodra ze uit de deeltjesemitter worden uitgezonden. Afhankelijk van je VFX-kunst, wil je misschien dat je deeltjes slechts een moment zichtbaar zijn (0.5  seconden), of dat ze in de lucht blijven hangen (2  seconden).

### [Gekalibreerde nummers](#gekalibreerde-nummers)[](#gekalibreerde-nummers)

Het randomiseren van eigenschappen kan ervoor zorgen dat de deeltjes minder repetitief aanvoelen. Je kunt randomisatie toevoegen aan sommige eigenschappen van de deeltjesemitter, zoals [Lifetime](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Lifetime)  en [RotSpeed](/docs/nl-nl/reference/engine/classes/ParticleEmitter#RotSpeed) , door een minimum- en maximumwaarde bereik voor de respectieve eigenschap toe te voegen.

Om nummers te randomiseren:

1.

Klik op de kleine pijl naast de naam van de eigenschap. De eigenschap vouwt uit.

 ![](https://prod.docsiteassets.roblox.com/assets/education/build-it-play-it-mansion-of-wonder/make-final-touches/show-random-options.png)

2.

Stel Min  in op de minimumwaarde die je wilt dat je deeltjes hebben.

3.

Stel Max  in op de maximumwaarde die je wilt dat je deeltjes hebben.

Gebruik je nieuwe kennis met deeltjesemitters om wat tijd te nemen om je VFX-kunst te verbeteren. Wanneer je klaar bent, ga je verder naar de volgende sectie om meer te leren over playtesting en hoe je je werk kunt opslaan in Roblox.

[Volgende](/docs/nl-nl/tutorials/curriculums/artist/test-and-save)[Vorige](/docs/nl-nl/tutorials/curriculums/artist/get-started)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
