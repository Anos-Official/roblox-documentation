<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/curriculums/core/building/greybox-a-playable-area -->

Greybox een speelgebied | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Greybox een speelgebied

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Greyboxing  is het proces van het bouwen van een level met eenvoudige vormen voordat je tijd investeert in scripting of het maken van definitieve kunstassets. Het helpt je om gameplay te testen, lay-outproblemen te identificeren en snel wijzigingen aan te brengen terwijl de omgeving nog gemakkelijk te wijzigen is.

In deze sectie ga je de zee-stapelplatforms greyboxen die het speelgebied van het spel vormen. Zodra de lay-out goed aanvoelt, kun je beginnen met scripting.

## [Plan het speelgebied](#plan-het-speelgebied)[](#plan-het-speelgebied)

In het uiteindelijke spel verzamelen spelers munten om hun sprongkracht te vergroten en hogere platforms te bereiken. Je zult dit voortgangssysteem later in de tutorial implementeren, maar het is belangrijk om hier rekening mee te houden terwijl je je omgeving greyboxet. Als algemene regel zou het hoogteverschil tussen platforms geleidelijk moeten toenemen om spelers aan te moedigen munten te verzamelen en door te gaan met voortgang.

Als referentie gebruikt het voorbeeld [Island Jump - Building](https://www.roblox.com/games/14239096301/Island-Jump-Building)  zeven hoogte-niveaus. Het eerste platform ligt zo laag dat spelers slechts een paar munten nodig hebben om het te bereiken. De daaropvolgende hoogteverschillen nemen toe tot 8, 20, 35, 55, 81 en 110 studs, wat een constante gevoel van voortgang door het spel creëert.

Een stud is de primaire lengtemaat van Studio, gelijk aan ongeveer 28 cm. Als je je eigen lay-out maakt in plaats van de Assistant-prompt te gebruiken of de voorbeeldlay-out opnieuw te creëren, zorg er dan voor dat elk nieuw hoogte-niveau dat een sprongupgrade vereist, minstens 30 studs boven het vorige ligt.

 ![Een verre blik op de greybox-geometrie van het voorbeeld eilandjump-spel. Elk niveau van hoogteverschil tussen zee-stapels is gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/tutorials/block-out-a-playable-area/Platform-Levels.jpg)

## [Voeg de platforms toe](#voeg-de-platforms-toe)[](#voeg-de-platforms-toe)

Nu je een plan hebt voor het hoogteverschil tussen platforms, voeg je tijdelijke [Part](/docs/nl-nl/reference/engine/classes/Part)  objecten toe om de zee-stapels weer te geven. Onderdelen zijn de basisbouwstenen van Roblox, met eigenschappen die hun vorm, grootte, kleur en andere fysieke kenmerken regelen.

Voor dit project gebruik je cilinder  onderdelen om spelers een vlakke bovenkant te geven om op te landen tijdens het springen.

** Een vergelijking tussen de greybox van het voorbeeld Island Jump-spel en de definitieve geometrie**

![De greybox-geometrie van het voorbeeld Island Jump-spel.](https://prod.docsiteassets.roblox.com/assets/tutorials/block-out-a-playable-area/Add-Platforms-Greybox.jpg)

![De definitieve geometrie van het voorbeeld Island Jump-spel.](https://prod.docsiteassets.roblox.com/assets/tutorials/block-out-a-playable-area/Add-Platforms-Final.jpg)

### [Maak een organisatiestructuur](#maak-een-organisatiestructuur)[](#maak-een-organisatiestructuur)

Voordat je onderdelen toevoegt, maak je twee containers om het project georganiseerd te houden. Roblox biedt [Folder](/docs/nl-nl/reference/engine/classes/Folder)  objecten voor het groeperen van gerelateerde instanties en [Model](/docs/nl-nl/reference/engine/classes/Model)  objecten voor het groeperen van 3D-objecten. In deze tutorial maak je een World -map om de omgeving te bevatten en een Blockout_Parts -model binnen die map om de greybox-platforms te bevatten.

1.

Maak in de Explorer  een map genaamd World  binnen Workspace .

2.

Maak een model genaamd Blockout_Parts  binnen de nieuwe map.

In Studio zijn namen hoofdlettergevoelig. Je moet World  en Blockout_Parts  precies spellen zoals weergegeven, anders zullen de scripts die je later toevoegt niet werken.

### [Voeg onderdelen in](#voeg-onderdelen-in)[](#voeg-onderdelen-in)

Nu je een organisatiestructuur hebt, voeg je de cilinders voor je platforms toe. Je kunt een Assistant-prompt gebruiken, je eigen lay-out handmatig bouwen of de lay-out van het voorbeeldspel opnieuw creëren.

Bouw met Assistant Maak het zelf Recreëer het voorbeeld

Om de Assistant de hele greybox in één stap te laten genereren, kopieer je de prompt die overeenkomt met of je een unieke lay-out wilt of een exacte kopie van het voorbeeldspel.

Maak je eigen lay-out

```

Maak meerdere cilinderonderdelen binnen Workspace > World > Blockout_Parts om platforms te vormen.

Begin met één grote, platte cilinder in het midden van het eiland, voeg dan minstens zeven andere cilinders toe die allemaal beginnen op dezelfde verticale basis maar in hoogte variëren (zoals hoge gebouwen) om een opwaartse route te creëren.

Pas Grootte, Positie en Oriëntatie aan zodat de bovenste oppervlakken vlak en begaanbaar zijn, en stel alle Onderdelen in op Geankerd.

```

Recreëer het voorbeeld

```

Maak de volgende cilinderonderdelen binnen Workspace > World > Blockout_Parts:

1. Level_1 (Grootte 12, 131, 131; CFrame.Positie -23, -4, 9; CFrame.Oriëntatie 0, 0, 90)

2. Level_2 (Grootte 20, 81, 81; CFrame.Positie -8, 0, 24; CFrame.Oriëntatie 0, 0, 90)

3. Level_3a (Grootte 40, 44, 44; CFrame.Positie 42, 10, 9; CFrame.Oriëntatie 0, 0, 90)

4. Level_3b (Grootte 40, 34, 34; CFrame.Positie 87, 10, 4; CFrame.Oriëntatie 0, 0, 90)

5. Level_3c (Grootte 40, 44, 44; CFrame.Positie 97, 10, 49; CFrame.Oriëntatie 0, 0, 90)

6. Level_4a (Grootte 75, 39, 39; CFrame.Positie 112, 27.5, 46.5; CFrame.Oriëntatie 0, 0, 90)

7. Level_4b (Grootte 75, 65, 65; CFrame.Positie 137, 27.5, 69; CFrame.Oriëntatie 0, 0, 90)

8. Level_4c (Grootte 75, 60, 60; CFrame.Positie 159.5, 27.5, 91.5; CFrame.Oriëntatie 0, 0, 90)

9. Level_4d (Grootte 75, 30, 30; CFrame.Positie 207, 27.5, 106.5; CFrame.Oriëntatie 0, 0, 90)

10. Level_4e (Grootte 75, 61, 61; CFrame.Positie 250, 27.5, 74; CFrame.Oriëntatie 0, 0, 90)

11. Level_5a (Grootte 130, 60, 60; CFrame.Positie 268, 55, 50; CFrame.Oriëntatie 0, 0, 90)

12. Level_5b (Grootte 130, 25, 25; CFrame.Positie 256, 55, 2.5; CFrame.Oriëntatie 0, 0, 90)

13. Level_5c (Grootte 130, 25, 25; CFrame.Positie 276, 55, -17.5; CFrame.Oriëntatie 0, 0, 90)

14. Level_5d (Grootte 130, 54, 54; CFrame.Positie 322, 55, -21; CFrame.Oriëntatie 0, 0, 90)

15. Level_6a (Grootte 211, 79, 79; CFrame.Positie 367, 94.5, -41; CFrame.Oriëntatie 0, 0, 90)

16. Level_6b (Grootte 211, 24, 24; CFrame.Positie 387, 94.5, 11.5; CFrame.Oriëntatie 0, 0, 90)

17. Level_6c (Grootte 211, 44, 44; CFrame.Positie 397, 94.5, 51.5; CFrame.Oriëntatie 0, 0, 90)

18. Level_7 (Grootte 321, 61, 61; CFrame.Positie 407, 149.5, 79; CFrame.Oriëntatie 0, 0, 90)

Zorg ervoor dat alle Onderdelen geankerd, correct gepositioneerd en georiënteerd zijn om een continue level lay-out te vormen.

```

### [Align onderdelen](#align-onderdelen)[](#align-onderdelen)

Als je de waarden van het voorbeeld Island Jump - Building  spel hebt gebruikt bij het invoegen van je zee-stapelplatforms, kun je deze stap overslaan.

Als je je eigen lay-out maakt, is het vaak gemakkelijker om de hoogtes van platforms te beheren wanneer elk platform dezelfde basisverhoging deelt en alleen in grootte varieert. De [Align Tool](/docs/nl-nl/studio/align-tool)  kan dit in één klik doen door de onderkant  rand op de Y  as uit te lijnen.

1.

Selecteer in de Explorer  al je platforms.

2.

Klik in de Model  werkbalk op Align .

3.

In het Align Tool venster:

1.

Stel Mode  in op Min .

2.

Stel Align In  in op World  en Y .

3.

Stel Relative To  in op Selection Bounds .

4.

Klik op Align .

![Een onderwaterzicht van veel cilinders die zijn uitgelijnd langs hun onderrand.](https://prod.docsiteassets.roblox.com/assets/tutorials/block-out-a-playable-area/Platforms-Aligned-Underwater.jpg) Alle platforms zijn uitgelijnd aan hun onderrand

### [Maak een holle tunnel](#maak-een-holle-tunnel)[](#maak-een-holle-tunnel)

Om meer visuele variatie toe te voegen, snijd je een tunnel door een van de zee-stapels met behulp van de solide modellering  tools van Studio. Voor deze tutorial gebruik je Negate  om het gat te creëren en Union  om de onderdelen in één vorm te combineren. Voor meer informatie over alle solide modelleringstools, zie [solide modellering](/docs/nl-nl/parts/solid-modeling) .

Bouw met Assistant Bouw het zelf

Maak een holle tunnel

```

Maak een holle tunnelstructuur met deze stappen:

1. Maak een cilinderonderdeel genaamd Tunnel met Grootte 24, 65, 69 en CFrame.Positie 137, 77, 69 en CFrame.Oriëntatie 0, 0, 90. Stel Geankerd in op waar.

2. Maak een blokonderdeel genaamd Hollow_Part met Grootte 24.5, 72, 22 en CFrame.Positie 134.5, 77, 71 en CFrame.Oriëntatie 0, 135, 90. Stel Geankerd in op waar. Dit onderdeel moet de cilinder doorkruisen om de holle ruimte te definiëren.

3. Negate de Hollow_Part zodat het een aftrekvorm wordt.

4. Selecteer zowel het Tunnel-onderdeel als de genegate Hollow_Part, en voer vervolgens een Union-bewerking uit zodat de holle vorm uit de cilinder wordt gesneden.

5. Hernoem de resulterende unie naar Level_4b_Union.

6. Zoek het bestaande Level_4b-platform, dupliceer het en hernoem de duplicaat naar Level_4b_Top.

7. Stel Level_4b_Top in op Grootte 74, 65, 69 en CFrame.Positie 137, 126, 69 en CFrame.Oriëntatie 0, 0, 90. Zorg ervoor dat het Geankerd is en boven de tunnel is gepositioneerd.

Zorg ervoor dat alle Onderdelen goed zijn uitgelijnd en dat het eindresultaat een cilinder tunnel is met een open doorgang en een platform bovenop.

```

## [Speeltest de lay-out](#speeltest-de-lay-out)[](#speeltest-de-lay-out)

Voordat je begint met scripting, speeltest je de lay-out om eventuele problemen op te vangen terwijl het nog gemakkelijk is om wijzigingen aan te brengen.

Start een speeltest vanuit het Test  tabblad en simuleer de starttoestand van de speler.

1.

Zoek je karakter in de Explorer  en selecteer Humanoid .

2.

Schakel UseJumpPower  in.

3.

Stel in het Eigenschappen  venster JumpPower  in op 0 .

4.

Terwijl je hogere platforms bereikt, verhoog je JumpPower  in stappen van 30  om het verzamelen van sprongupgrades te simuleren en zorg ervoor dat elk niveau bereikbaar is.

 ![Spronginstellingen met de JumpPower en UseJumpPower eigenschappen gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/tutorials/block-out-a-playable-area/Humanoid-Jump-Settings.png)

In de volgende sectie leer je hoe je de algehele gameplay kunt scripten.

[Volgende](/docs/nl-nl/tutorials/curriculums/core/scripting/script-game-behavior)[Vorige](/docs/nl-nl/tutorials/curriculums/core/building/create-an-environment-with-terrain)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
