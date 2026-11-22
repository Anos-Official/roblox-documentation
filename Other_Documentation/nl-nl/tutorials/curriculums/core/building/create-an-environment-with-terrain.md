<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/curriculums/core/building/create-an-environment-with-terrain -->

Maak een omgeving met terrein | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Maak een omgeving met terrein

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een omgeving met terrein creëren  stelt je in staat om organische materialen te genereren en aan te passen binnen de 3D-ruimte die eruitzien en zich gedragen als natuurlijke materialen uit de echte wereld. Met de tools in de [Terrain Editor](/docs/nl-nl/studio/terrain-editor)  leert deze sectie je hoe je terrein kunt genereren en sculpturen voor een klein eiland waar spelers spawnen en beginnen met navigeren in je spel.

Dit is het enige hoofdstuk waarin je rechtstreeks in Studio moet werken in plaats van op Assistant te vertrouwen. Het creëren van terrein is een creatief proces, en het is moeilijk om penseelstreken, vormen en materiaalanpassingen exact te reproduceren met AI.

Maak je geen zorgen als je omgeving niet perfect overeenkomt met het voorbeeld [Island Jump](https://www.roblox.com/games/14239096301/)  spel. Zolang je terrein de gameplay en doelen van je spel ondersteunt, zijn verschillen in uiterlijk zowel normaal als te verwachten.

## [Maak het eiland](#maak-het-eiland)[](#maak-het-eiland)

De eerste stap in het creëren van je omgeving is het maken van een klein eiland waar spelers naartoe spawnen wanneer ze het spel starten.

1.

Klik in de Terrain Editor op het tabblad Bewerken  en klik vervolgens op de Tekenen  tool.

2.

Stel de Borstelgrootte  in op 32 .

3.

Stel het Bronmateriaal  in op Zand .

4.

Klik in het viewport nabij je spawnlocatie om een bol zand te plaatsen.

 ![Het venster van Studio's Terrain Editor met zowel het tabblad Bewerken als de knop Tekenen gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/studio/terrain-editor/Edit-Tab-Draw.png)

Als je de bol niet kunt zien, zoom dan je camera uit totdat je spawnlocatie kleiner is.

## [Vorm het eiland](#vorm-het-eiland)[](#vorm-het-eiland)

Als je het eiland in zijn huidige bolvorm houdt, zouden spelers het moeilijk hebben om te navigeren zonder van het eiland te vallen.

1.

Schakel over naar de Vlak maken  tool.

2.

Stel de Borstelgrootte  in op 18 .

3.

Stel het Vlak maken Vlak  in op Vast .

4.

Stel het Vaste Y-vlak  in op 0 .

5.

Klik en sleep over de bovenkant van de bol totdat je een vlakke oppervlakte hebt.

Schakel nu over naar de Sculpt  tool. Stel het Bronmateriaal  in op Zand . Klik en sleep met je muis rond de randen van het eiland en onder de waterlijn om het eiland er natuurlijker uit te laten zien.

De Tekenen  tool voegt materiaal toe of trekt materiaal af op basis van de positie van de borstel, terwijl de Sculpt  tool alleen terrein laat groeien of erodeert dat al bestaat. Gebruik Tekenen om nieuwe vormen te creëren en Sculpt om ze te verfijnen.

## [Maak water](#maak-water)[](#maak-water)

Om een groot wateroppervlak te creëren, gebruikt deze tutorial de Vullen  tool, die al het materiaal binnen een geselecteerd gebied vervangt door een ander materiaal.

1.

Schakel over naar de Vullen  tool.

2.

Stel onder Selectie-instellingen  in:

1.

Grootte  op 1800, 5, 1800  (zodat het water de horizon bereikt).

2.

Positie  op 0, -15, 0  (zodat het water onder de top van het eiland zit).

3.

Stel onder Materiaaleinstellungen  in:

1.

Vulmodus  op Vervangen .

2.

Bronmateriaal  op Lucht .

3.

Doelmateriaal  op Water .

4.

Klik op Vervangen  om het water rond het eiland te genereren.

## [Pas materialen toe](#pas-materialen-toe)[](#pas-materialen-toe)

Nu je de basisvorm van je eiland hebt gemaakt, gebruik je de Verf  tool om grasmaterialen op het terrein toe te passen en het eiland een natuurlijker uiterlijk te geven.

1.

Schakel over naar de Verf  tool.

2.

Stel de Materiaalmodus  in op Verf .

3.

Stel het Bronmateriaal  in op Bladerig Gras .

4.

Sleep over het midden van het eiland om een grasveld aan te leggen, terwijl je de randen zandig laat.

Voeg afwerkingsdetails toe.

1.

Verander de Borstelgrootte  in 3 .

2.

Verander het Materiaal  in Gras .

3.

Sleep langs de randen van het bladerige gebied om zichtbare sprieten toe te voegen. Zorg ervoor dat je ruimte in het midden laat voor de spawnlocatie en de eerste paar platforms die je in het volgende hoofdstuk zult bouwen.

Plaats ten slotte het spawnpunt.

1.

Selecteer in de Explorer  SpawnLocation .

2.

Gebruik de Verplaatsen  tool van de werkbalk om het spawnpunt naar de rand van het eiland te slepen, zodat er ruimte is voor een lanceerplatform. Het voorbeeldspel gebruikt een positie van -127, -3, 9 , maar overal nabij de rand werkt.

Voor een meer aangepaste uitstraling kun je standaard terreintexturen vervangen door aangepaste textuurassets met behulp van [Materiaaloverschrijvingen](/docs/nl-nl/parts/materials#material-overrides) .

## [Speeltest](#speeltest)[](#speeltest)

Zodra je tevreden bent met het uiterlijk van je eiland, speeltest je je spel om de schaal van het eiland te controleren.

Klik op Test  in het dropdownmenu in de werkbalk en klik vervolgens op Speel . Ren rond het eiland en kijk hoe het aanvoelt. Wanneer je klaar bent, klik op Stop .

 ![Testoptie in het dropdownmenu voor testmodi van Studio's mezzanine.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Mode-Test.png)

Als je personage in de verkeerde richting spawnt, zoals naar de oceaan in plaats van naar het midden van het eiland, draai dan het [SpawnLocation](/docs/nl-nl/reference/engine/classes/SpawnLocation)  object en speel opnieuw totdat ze spawnen zoals je wilt.

Als volgende leer je hoe je een speelbare ruimte kunt creëren voor spelers om te volgen om het hoogste platform te bereiken.

[Volgende](/docs/nl-nl/tutorials/curriculums/core/building/greybox-a-playable-area)[Vorige](/docs/nl-nl/tutorials/curriculums/core/building/create-a-project)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
