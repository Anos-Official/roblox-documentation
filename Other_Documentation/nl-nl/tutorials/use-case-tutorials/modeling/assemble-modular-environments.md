<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/modeling/assemble-modular-environments -->

Assembleer modulaire omgevingen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Modellering

# Assembleer modulaire omgevingen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een modulaire omgeving  is een 3D-ruimte die bestaat uit herbruikbare assets die naadloos in verschillende configuraties in elkaar klikken om variaties van een groter complex object te creëren. Bijvoorbeeld, de [Modern City-sjabloon](https://www.roblox.com/games/13165709401/Modern-City)  van Studio is een modulaire omgeving die gebruikmaakt van herbruikbare muren, ramen en deuren uit zowel een [modulaire bouwkit](https://create.roblox.com/store/asset/13168370735/Modular-Building-Kit-Modern-City)  als een [materialenpakket](https://create.roblox.com/store/asset/13168345645/Modern-City-Materials-Pack)  om bouwvariaties te creëren die een heel stadscentrum vormen.

Het assembleren van modulaire omgevingen is nuttig omdat je niet elke individuele asset handmatig in je spel hoeft te maken. In plaats daarvan hoef je slechts een paar assets te maken die je kunt hergebruiken en aanpassen om variëteit in de scène te creëren. Dit proces versnelt niet alleen hoe snel je grote omgevingen kunt bouwen, maar het kan ook helpen om elk afzonderlijk object samenhangend te laten aanvoelen binnen je spel.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/Overview-Asset-Kit.png) Voorbeeld Modulaire Bouwkit

![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/Overview-City-Template.png) Studio's Modern City-sjabloon

Met dezelfde modulaire bouwkitstukken die de Modern City-sjabloon van Studio hebben gebouwd, leidt deze gids je door het belang van consistente pivotpuntlocaties zodat modulaire assets kunnen uitlijnen en in elkaar klikken, laat je zien hoe je modulaire assets kunt combineren om een realistisch gebouw te creëren, en demonstreert hoe je modulaire assets kunt aanpassen om variëteit binnen je omgeving te creëren.

## [Het belang van consistente pivotpuntlocaties](#het-belang-van-consistente-pivotpuntlocaties)[](#het-belang-van-consistente-pivotpuntlocaties)

Elk object in Studio beweegt en roteert op basis van de locatie van zijn pivotpunt. Standaard beginnen onderdelen en meshes met een pivotpuntlocatie in het midden van het object, dus wanneer je ze verplaatst, bewegen ze vanuit het midden van het object naar buiten. De standaard pivotpuntlocatie is nuttig voor symmetrische schaling en rotatie, maar het wordt problematisch wanneer je objecten van verschillende vormen op een voorspelbare en uniforme manier wilt laten in elkaar klikken.

Bijvoorbeeld, de volgende twee onderdelen hebben beide een grootte van [10, 10, 1] en behouden hun standaard pivotpuntlocaties. Als je het gele onderdeel in stappen van 5 studs op de X-as verplaatst, beweegt het van zijn midden naar zijn rand en kan het gemakkelijk uitlijnen en in elkaar klikken met elke kant van het blauwe onderdeel.

  ![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/Pivot-Points-Aligned-Diagram.jpg)

Als je echter het gele onderdeel roteert en het blijft verplaatsen in stappen van 5 studs op de X-as, kan het niet uitlijnen en in elkaar klikken met een van de zijden van het blauwe onderdeel. Dit komt omdat de breedte van het gele onderdeel nu één stud is, dus wanneer het 5 studs van zijn midden beweegt, beweegt het 0,5 studs van het midden + 4,5 studs op het wereldrooster, wat resulteert in 0,5 studs overlap aan beide zijden van het blauwe onderdeel.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/Pivot-Points-Misaligned-Diagram.jpg)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/Pivot-Points-Misaligned-TopView.png)

Als je ze weer wilt uitlijnen, kun je de waarde voor de stud-incrementbeweging wijzigen of de positie handmatig aanpassen totdat ze zijn uitgelijnd, maar dit proces wordt snel vervelend en onhoudbaar, vooral wanneer je het voor veel objecten van verschillende groottes, unieke pivotpuntlocaties of complexe geometrie, zoals meshes die je in externe modelleringstools maakt, moet toepassen.

Dit is waarom het hebben van een consistente pivotlocatie voor modulaire assets van vitaal belang is, zodat ze op vooraf bepaalde, incrementele afstanden ten opzichte van elkaar kunnen verbinden wanneer je raster-snapping inschakelt. Bijvoorbeeld, elke mesh in de Modern City voorbeeld modulaire bouwkit heeft een minimale lengte van 7,5 studs en een maximale lengte die deelbaar is door 7,5 studs, zodat elke mesh naadloos kan uitlijnen en verbinden zonder overlap, zelfs wanneer je ze roteert.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/Pivot-Points-Stud-Diagram.png)

Modulaire assets kunnen bestaan uit een bijna oneindige variëteit aan verschillende vormen, maten en silhouetten en verschillende doeleinden belichamen, zoals muren, hoeken of decoratieve toevoegingen, dus waar dat consistente pivotpunt moet zijn, is verschillend voor elke modulaire bouwkit. Voor de Modern City voorbeeld modulaire bouwkit heeft elke mesh een consistente pivotlocatie, hetzij in de meest voorwaartse, onderste hoek, of op een locatie die hen in staat stelt om op een logische positie op het gebouw in te klikken, zoals balkons, kroonlijsten en luifels.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/Pivot-Points-Railing.jpg)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/Pivot-Points-Cornice.jpg)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/Pivot-Points-Awning.jpg)

Voor informatie over hoe je pivotlocaties kunt configureren voor onderdelen en modellen die je binnen Studio maakt, zie [Pivot Tools](/docs/nl-nl/studio/pivot-tools#edit-pivot) . Voor informatie over hoe je pivotlocaties kunt configureren voor meshes die je in externe modelleringstools maakt, zie de pivotpuntdocumentatie voor [Blender](https://docs.blender.org/manual/en/2.80/scene_layout/object/editing/transform/control/pivot_point/index.html)  of [Maya](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2022/ENU/Maya-Basics/files/GUID-150B390E-840B-4FE3-B8E9-8DEBCE7CEC97-htm.html) .

## [Configureer snapgedrag](#configureer-snapgedrag)[](#configureer-snapgedrag)

De standaardinstellingen van Studio stellen je in staat om objecten vrij te verplaatsen en te roteren naar elke fractie van een stud of graad, respectievelijk. Omdat modulaire bouwkits echter afhankelijk zijn van assets die op exacte intervallen in elkaar klikken, moet je deze standaardinstellingen aanpassen aan de vereisten van elke modulaire bouwkit . Bijvoorbeeld, de Modern City voorbeeld [modulaire bouwkit](https://create.roblox.com/store/asset/13168370735/Modular-Building-Kit-Modern-City)  vereist dat elke mesh roteert in stappen van 7,5 studs en 45 graden met botsingen uit. Dit zorgt ervoor dat wanneer je meshes rond de 3D-omgeving verplaatst en roteert, ze kunnen verbinden en duidelijke uitlijning met elkaar behouden terwijl het gebouw groeit.

Om de Studio-instellingen voor ideaal snapgedrag voor de voorbeeld modulaire bouwkit te configureren, kijk in de werkbalk en:

1.

Schakel Botsingen  uit.

2.

Schakel Roteren  snapping in en stel het in op 45 .

3.

Schakel Verplaatsen  snapping in en stel het in op 7.5 .

## [Combineer modulaire assets](#combineer-modulaire-assets)[](#combineer-modulaire-assets)

Wanneer je begint met het assembleren van modulaire assets tot een groter complex object, is het nuttig om één kernobject te kiezen waarvan je de positiecoördinaten gedurende het hele proces kunt refereren. Dit zorgt ervoor dat elk aanvullend object snel uitlijnt naar de juiste pivotlocatie voordat je ze naar een andere positie verplaatst.

Om modulaire assets samen te voegen om een gebouw te creëren met de voorbeeld modulaire bouwkit:

1.

Selecteer een van de onderste modulaire meshes. Dit voorbeeld gebruikt een deur.

2.

Plaats deze mesh in de viewport op een locatie binnen je spel waar je een gebouw wilt creëren.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/Combining-Core-Mesh.jpg)

3.

Kopieer in het Eigenschappen -venster de Positie -coördinaten.

4.

Selecteer in de viewport een enkele mesh die je wilt verbinden met je eerste mesh.

5.

Plak in het Eigenschappen -venster de Positie -coördinaten van de eerste mesh. De tweede mesh wordt bovenop de eerste mesh weergegeven.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/Combining-Overlapping-Meshes.jpg)

6.

Selecteer in de werkbalk de Verplaats -tool en verplaats de tweede mesh naar een nieuwe locatie aan een van de zijden van de eerste mesh. Het klikt in stappen van 7,5 in langs dezelfde as.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/Combining-Additional-Mesh.jpg)

Het proces van het combineren van modulaire meshes vereist dat je slechts één mesh tegelijk verplaatst. Als je meerdere meshes tegelijk selecteert, gemiddeld Studio hun pivotpuntlocaties samen, waardoor de opzettelijke consistente pivotpuntlocaties die de meshes nodig hebben om uit te lijnen en in elkaar te klikken, effectief worden verwijderd.

7.

Herhaal dit proces voor elke mesh die je wilt laten samenstellen in je gebouw, door continu de positiecoördinaten van de eerste mesh te plakken voor elke aanvullende mesh om ervoor te zorgen dat de startpivotlocatie hetzelfde blijft voor elke mesh van het gebouw.

## [Pas modulaire assets aan](#pas-modulaire-assets-aan)[](#pas-modulaire-assets-aan)

Om ervoor te zorgen dat elk object er uniek uitziet en aanvoelt ten opzichte van elkaar, is het belangrijk om je modulaire assets aan te passen om visuele variëteit te creëren. Terwijl de volgende secties aanpassingsstrategieën voor de voorbeeld modulaire bouwkit verkennen, zoals het gebruik van alternatieve materialen voor de muren en afwerkingen, experimenteren met verschillende tinten voor deze versieringen, het verwijderen van herhaling voor materialen die op grote oppervlakken tegelen, en het aankleden van objecten met decoratieve props, kun je soortgelijke methoden gebruiken voor elke modulaire bouwkit die je gebruikt om modulaire omgevingen te creëren.

### [Gebruik aangepaste materialen](#gebruik-aangepaste-materialen)[](#gebruik-aangepaste-materialen)

Elke mesh binnen de voorbeeld modulaire bouwkit gebruikt een [aangepast materiaal](/docs/nl-nl/parts/materials#aangepaste-materialen)  uit het voorbeeld [materialenpakket](https://create.roblox.com/store/asset/13168345645/Modern-City-Materials-Pack)  dat je kunt gebruiken om het uiterlijk en de fysieke eigenschappen van de muren van je gebouwen te veranderen. Bijvoorbeeld, standaard beginnen alle muren met een PaintedBrick  aangepast materiaal, maar je kunt het veranderen in verschillende vormen van alternatieve baksteen, beton en pleister, en vervolgens een unieke tintkleur aan het materiaal instellen om elk gebouw een uniek uiterlijk te geven.

Om alternatieve aangepaste materialen voor wandmeshes te gebruiken:

1.

Houd in de viewport Alt Shift  (⌥ Shift ) ingedrukt en klik op een mesh van je gebouw met een baksteenmateriaal.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/Customizing-MassSelection.jpg)

2.

Klik in het Eigenschappen -venster op het dropdownmenu MaterialVariant . Alle alternatieve aangepaste materialen worden weergegeven.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/Customizing-MaterialVariants.jpg)

3.

Selecteer een alternatieve materiaalvariant. Alle actieve wandmeshes werken hun materiaal bij in de viewport.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/Customizing-NewCustomMaterial.jpg)

4.

OPTIONEEL

 Om het nieuwe aangepaste materiaal verder aan te passen, selecteer je een nieuwe tintkleur.

1.

Klik in het Eigenschappen -venster op BrickColor  of Color . De hexagonkaart of kleurenpop-up wordt respectievelijk weergegeven.

2.

Selecteer een nieuwe kleur. Alle actieve wandmeshes werken hun tintkleur bij in de viewport.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/Customizing-NewColor.jpg)

### [Gebruik SurfaceAppearance-objecten](#gebruik-surfaceappearance-objecten)[](#gebruik-surfaceappearance-objecten)

Elke mesh met een afwerking in de voorbeeld modulaire bouwkit bevat een [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  object dat aangepaste texturen gebruikt om de versieringen van elk gebouw realistischer te laten aanvoelen. Om elk gebouw in je spel uniek te laten aanvoelen, kun je elk [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  object vervangen door een ander in de SurfaceAppearance -map in de werkruimte, inclusief materialen zoals beton, pleister en hout, en vervolgens een unieke tintkleur voor de afwerking instellen voor extra variëteit.

Om [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  objecten voor afwerkingsmeshes te vervangen:

1.

Selecteer in de viewport een mesh met een afwerking.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/SurfaceAppearance-DefaultTrim.jpg)

2.

Breid in het Explorer -venster het bovenliggende model uit, en vervolgens de kindermesh totdat het [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  object zichtbaar is.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/SurfaceAppearance-Concrete.jpg)

3.

Verwijder het [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  object. Het visuele uiterlijk van de mesh wordt bijgewerkt in de viewport.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/SurfaceAppearance-Delete.jpg)

4.

Kopieer in de SurfaceAppearance -map een alternatief [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  object dat je wilt gebruiken voor de afwerking.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/SurfaceAppearance-Objects.jpg)

5.

Navigeer terug naar het afwerkingsmodel en plak het nieuwe [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  object in de kindermesh. Het visuele uiterlijk van de mesh wordt bijgewerkt in de viewport.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/SurfaceAppearance-Wood.jpg)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/SurfaceAppearance-NewTrim.jpg)

6.

Herhaal dit proces voor elke afwerkingsmesh op je gebouw.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/SurfaceAppearance-Final.jpg)

7.

OPTIONEEL

 Om het nieuwe [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  object verder aan te passen, selecteer je een nieuwe tintkleur.

1.

Houd in de viewport Alt Shift  (⌥ Shift ) ingedrukt en klik op een mesh van je gebouw met een afwerking.

2.

Klik in het Eigenschappen -venster op BrickColor  of Color . De hexagonkaart of kleurenpop-up wordt respectievelijk weergegeven.

3.

Selecteer een nieuwe kleur. Alle actieve afwerkingsmeshes werken hun tintkleur bij in de viewport.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/SurfaceAppearance-NewColor.jpg)

### [Verminder zichtbare herhaling](#verminder-zichtbare-herhaling)[](#verminder-zichtbare-herhaling)

Wanneer je grote objecten bouwt die gebruikmaken van tegelmaterialen zoals bakstenen en beton, kan het tegelpatroon snel zichtbare herhaling onthullen. Om de zichtbare tegeling van deze materialen te helpen verminderen, kun je een grunge-decal of textuur maken en deze als een kind van je wandmeshes toevoegen om deze bovenop de actieve materialen van de muur te overlayen. Deze aanpassingsstrategie heeft het voordeel dat het extra realisme aan je gebouw toevoegt, waardoor de kwaliteit van je 3D-omgeving snel verbetert. Voor informatie over hoe je texturen kunt toepassen en aanpassen, zie [Texturen en decals](/docs/nl-nl/parts/textures-decals) .

![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/WithoutTexture.jpg) Muur zonder grunge textuur overlay

![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/WithTexture.jpg) Muur met grunge textuur overlay

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/Textures-Building.jpg)

### [Voeg decoratieve props toe](#voeg-decoratieve-props-toe)[](#voeg-decoratieve-props-toe)

Als laatste stap om objecten in hun grotere modulaire omgeving distinct te laten aanvoelen, kun je een aanzienlijke hoeveelheid karakter aan elk object toevoegen door ze te kleden met decoratieve props. Bijvoorbeeld, de voorbeeld modulaire bouwkit bevat assets zoals brandtrappen, balkonramen, airconditioners en groenvoorzieningen die je kunt uitproberen om elk gebouw te verfraaien en het een bewoonde uitstraling te geven. Zelfs het opnemen van een paar decoratieve props kan een enorme hoeveelheid verhaal aan je scène toevoegen.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/assembling-modular-environments/DecorativeProps-Building.jpg)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
