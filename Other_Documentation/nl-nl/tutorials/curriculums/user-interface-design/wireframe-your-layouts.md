<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/curriculums/user-interface-design/wireframe-your-layouts -->

Wireframe je lay-outs | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Wireframe je lay-outs

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Wireframing je lay-outs  is het proces van het ontwerpen van de structuur en flow van de informatie die je wilt communiceren via UI in verschillende workflows. Deze kritieke stap van de tutorial stelt je in staat om te itereren op de indeling van je UI-elementen, pijnpunten te ontdekken en de ervaring van de speler te verbeteren voordat je tijd en middelen investeert in een problematisch ontwerp dat niet werkt voor je spel.

Met behulp van het [voorbeeld laser tag spel](https://www.roblox.com/games/14817965191/Laser-Tag-1A)  .rbxl  bestand als referentie, laat deze sectie van het gebruikersinterface-curriculum je zien hoe je je UI-elementen op het scherm kunt structureren, inclusief richtlijnen over:

-

Het plannen van een visuele hiërarchie voor je UI die spelers intuïtief naar de functies en informatie leidt die ze nodig hebben om succesvol te zijn in je spel.

-

Het blokkeren van UI-elementen met basisvormen om de compositie van je UI-elementen naast de kern UI en aanraakbediening van Roblox te beoordelen.

-

Het ontwikkelen van gebruikersflows om rekening te houden met de noodzakelijke acties die spelers moeten ondernemen om hun doelen te bereiken.

Nadat je deze sectie hebt voltooid, leer je hoe je je UI in Studio kunt construeren en configureren die respect heeft voor je kunststijl en wireframes.

## [Plan een visuele hiërarchie](#plan-een-visuele-hiërarchie)[](#plan-een-visuele-hiërarchie)

Een visuele hiërarchie is een organisatie structuur die UI-elementen benadrukt op basis van hun volgorde van belangrijkheid. Het plannen van een visuele hiërarchie voor de verschillende workflows in je spel is belangrijk omdat het spelers voorbereidt op succes bij het bereiken van hun doelen, wat vooral noodzakelijk is voor de snelle gameplay van first-person shooter games waarin doelen van moment tot moment veranderen.

Effectieve visuele hiërarchieën begeleiden spelers door de functies en informatie die ze nodig hebben om aan je gameplay-eisen te voldoen, afhankelijk van waar ze van nature op het scherm kijken om workflows te voltooien. Bijvoorbeeld, de visuele hiërarchie van het voorbeeld laser tag spel moet spelers begeleiden door de volgende categorieën van UI-elementen terwijl ze de kaart navigeren en spelers van het vijandige team taggen:

1.

Informatie over het doel van het spel.

2.

Informatie over de blaster.

3.

Informatie over de status van de speler.

De locatie die elke van deze categorieën op het scherm in het uiteindelijke ontwerp heeft, benadrukt hun volgorde van belangrijkheid:

-

De eerste categorie bevindt zich dicht bij de bovenkant  omdat het UI-elementen bevat die de meeste betekenis hebben voor hoe je het spel wint.

-

De tweede categorie neemt het grootste deel van de schermruimte in beslag dicht bij het midden  omdat het als het brandpunt fungeert om de aandacht van spelers naar de actie in 3D-ruimte te trekken, en het heeft de meeste betekenis voor het spelen van het spel.

-

De derde categorie bevindt zich dicht bij de zijkanten  omdat spelers deze perifere informatie kunnen lezen zonder hun aandacht van de gameplay af te leiden.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/user-interface-design/Section2/VisualHierarchy.png)

Voor sommige gamegenres hoef je slechts één categorie informatie tegelijk weer te geven omdat het de enige soort informatie is die belangrijk is voor de speler tijdens die workflow. Echter, voor first-person shooter games moeten spelers UI-elementen van meerdere categorieën tegelijkertijd zien omdat ze allemaal informatie bieden die de speler nodig heeft om succesvol te zijn, zoals de score van hun team, de cooldown-periode voor hun blaster, en of ze uit een ronde zijn getagd.

Bij het plannen van een visuele hiërarchie voor de workflows in je eigen spel, overweeg het volgende:

-

Als je UI-elementen van verschillende categorieën door elkaar op het scherm groepeert, weten spelers niet waar ze moeten kijken voor wat ze nodig hebben. Om spelers te helpen je spel te navigeren, groepeer UI-elementen van dezelfde categorie samen .

-

Als je te veel categorieën op het scherm tegelijk hebt, weten spelers misschien niet op welke informatie ze moeten letten. Om te voorkomen dat spelers overweldigd worden door rommel, toon UI-elementen contextueel voor verschillende workflows .

-

Evenzo, als er te veel UI-elementen per categorie zijn, kan dit spelers afleiden van het begrijpen hoe ze een actie of proces moeten voltooien. Om deze reden is het belangrijk om je kunststijl te gebruiken om visuele nadruk te geven aan je ideale interactievolgordes .

Voor een volledige beoordeling van de visuele hiërarchie voor het voorbeeld laser tag spel, zie de volgende tabel:

| Categorie | | UI-elementen | | Visuele hiërarchie |
| --- | --- |
| Informatie over het doel van het spel | |
-

Doelprompt

-

Team puntenteller

-

Teamindicator

 | |
-

Bovenaan het scherm

-

Bovenaan het scherm

-

Boven elke speler in de 3D-ruimte

 |
| Informatie over de blaster | |
-

Blasterselector

-

Doelwit

-

Hitmarker

-

Cooldownmeter

-

Schietknop voor mobiele apparaten

 | |
-

Midden van het scherm

-

Midden van het scherm

-

Binnen het doelwit

-

Boven de blaster

-

Dichtbij de rechterduim van de speler

 |
| Informatie over de status van de speler | |
-

Force field scherm wanneer de speler zich bij de ronde voegt of opnieuw aansluit

-

Respawn scherm wanneer de speler is getagd

-

Indicator wanneer vijandige spelers zijn getagd

 | |
-

Zijkanten van het scherm

-

Zijkanten van het scherm

-

Boven elke speler in de 3D-ruimte

 |

Voor meer informatie over het prioriteren van UI-elementen op het scherm, zie [UI & UX Design](/docs/nl-nl/production/game-design/ui-ux-design#prioritering) .

## [Blokkeer UI-elementen](#blokkeer-ui-elementen)[](#blokkeer-ui-elementen)

Nu je een visuele hiërarchie in gedachten hebt, kun je individuele UI-elementen blokkeren met behulp van basisvormen om de compositie van je aangepaste UI-indeling naast de kern UI van Roblox op meerdere apparaten te beoordelen. Dit proces stelt je in staat om te zien waar je je ontwerp moet aanpassen zodat het effectief is op alle schermformaten die spelers kunnen gebruiken om toegang te krijgen tot je spel, zoals op mobiele telefoons, tablets, laptops en tv-schermen.

Voordat je begint, moet je uitzoeken hoeveel schermruimte beschikbaar is voor je aangepaste UI-elementen, rekening houdend met de kern UI van Roblox. Bijvoorbeeld, standaard toont Roblox de volgende UI-elementen in elk spel:

-

Een lijst van spelers binnen het spel.

-

De gezondheidsbalk van het personage.

-

De rugzak van het personage.

-

Een chatvenster.

-

Een capture-knop.

-

Een pop-upmenu van karakteremotes.

![](https://prod.docsiteassets.roblox.com/assets/ui/misc/CoreGui-Elements.jpg)

Je kunt [deactiveren](/docs/nl-nl/players/disable-ui)  welke van deze elementen niet voldoen aan de gameplay-eisen van je eigen spel om schermruimte te besparen voor je aangepaste UI. Bijvoorbeeld, het voorbeeld laser tag spel heeft geen rugzak nodig omdat spelers alleen de mogelijkheid hebben om een enkele blaster te selecteren. Echter, als spelers meerdere blasters tegelijk konden selecteren, zou het spel deze kern UI kunnen uitschakelen om ervoor te zorgen dat er altijd ruimte is voor de blasterselector wanneer spelers respawnen, en dan een andere locatie bieden om uit je inventaris te selecteren.

Naast de kern UI van Roblox, moet je ook rekening houden met de noodzakelijke schermruimte voor de standaard aanraakbediening van Roblox. Bijvoorbeeld, wanneer spelers je spel openen met een mobiel apparaat, verschijnt er een virtuele duimstick in de linkerbenedenhoek van het scherm, en een springknop verschijnt in de rechterbenedenhoek van het scherm. Dit zorgt ervoor dat spelers altijd in staat zijn om je spel te navigeren, zelfs wanneer ze geen toegang hebben tot een toetsenbord of controller.

 ![](https://prod.docsiteassets.roblox.com/assets/ui/misc/Touch-Reserved-Zones.png)

Door rekening te houden met zowel de kern UI-elementen van Roblox die noodzakelijk zijn voor de gameplay van je spel, als de mogelijkheid van aanraakbediening, kun je je aangepaste UI-elementen blokkeren in één ontwerp  dat zich aanpast aan verschillende apparaten. Dit is belangrijk omdat het betekent dat je geen aparte versies van je UI hoeft te onderhouden terwijl je je spel bijwerkt.

Om deze methode te demonstreren, bekijk de volgende twee afbeeldingen van hoe het voorbeeld laser tag spel de aangepaste UI-elementen blokkeert voor zowel mobiele als pc-apparaten. Beide afbeeldingen bevatten:

-

Basisvormen om aangepaste UI weer te geven omdat het ontwerp het mogelijk maakt om gemakkelijk door verschillende iteraties te gaan voordat het uiteindelijke ontwerp wordt bereikt.

-

Grijstinten die het oog in staat stellen om informatie te volgen zonder de afleiding van een kleurrijke achtergrondomgeving.

-

De open staat van het chatvenster en de lijst van actieve spelers en het chatvenster om te zien hoeveel ruimte ze op het scherm innemen.

-

Ruimte voor mobiele bedieningselementen, zelfs als ze niet nodig zijn voor pc-apparaten.

Wanneer je je lay-outs op deze manier ontwerpt, terwijl je nadenkt over hoeveel UI-elementen tegelijkertijd op het scherm kunnen bestaan, maak je je toekomstbestendig voor alle potentiële lay-outs volgens de apparaten en workflows van spelers.

Mobiel PC

![](https://prod.docsiteassets.roblox.com/assets/tutorials/user-interface-design/Section2/MobileBlockIn.png)

Bij het blokkeren van UI-elementen voor je lay-outs, overweeg het volgende:

-

Waar en hoe je je UI blokkeert kan de compositie van je lay-outs beïnvloeden. Streef naar balans en symmetrie  in de hoeveelheid en grootte van je aangepaste UI-elementen naast de kern UI van Roblox.

-

Interactie met UI die ver van de onderste hoeken van sommige mobiele en tabletapparaten is, is ofwel ongemakkelijk of onmogelijk. Plaats interactieve elementen in gemakkelijk bereikbare zones  nabij de natuurlijke rustpositie voor duimen.

-

Wanneer spelers door je omgeving navigeren, kan de 3D-ruimte afleiden van je on-screen UI. Test je lay-outs tegen een verscheidenheid aan mogelijke achtergronden  om ervoor te zorgen dat je on-screen UI-elementen duidelijk en leesbaar blijven.

## [Ontwikkel gebruikersflows](#ontwikkel-gebruikersflows)[](#ontwikkel-gebruikersflows)

Een gebruikersflow is een verzameling paden die spelers in een spel kunnen nemen om een taak te voltooien, zoals het kiezen van een wapen, het kopen van een item of het genezen van een personage. Gebruikersflows beginnen meestal waar je verwacht dat spelers de taak beginnen, en eindigen met de laatste actie of prestatie die spelers bereiken aan het einde van de taak. Bovendien houden effectieve gebruikersflows ook rekening met ongebruikelijke paden die spelers mogelijk zelf willen nemen om hetzelfde doel te bereiken.

De volgende flowchart toont de gebruikersflow van een speler die het voorbeeld laser tag spel binnenkomt en speelt. Wanneer een speler het spel opent, voegt hij zich bij een lobby. Als de ronde nog niet aan de gang is, wacht hij tot de ronde begint, anders voegt hij zich bij een team dat momenteel het spel speelt. Als de eindvoorwaarde niet is bereikt, zoals het bereiken van een tijdslimiet of het taggen van 10 spelers per team, selecteren spelers hun blaster en ervaren ze de belangrijkste gameplay van het taggen of getagd worden door het vijandige team, het uitrusten van een nieuwe blaster binnen de arena, of respawnen nadat ze zijn getagd. Zodra spelers de eindvoorwaarde hebben bereikt, voltooien ze de ronde en voegen ze zich weer bij de lobby.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/user-interface-design/Section2/UserFlowChart.jpg)

Het is belangrijk om gebruikersflows te ontwikkelen voor alles wat spelers in je spel kunnen doen, omdat het je in staat stelt te beoordelen waar en hoe je wilt dat ze taken voltooien, en te anticiperen waar je pijnpunten kunt verlichten voor iedereen die hun eigen pad volgt. Bijvoorbeeld, als je aanvullende gebruikersflows voor het voorbeeld laser tag spel zou ontwikkelen, wat gebeurt er wanneer spelers:

-

Een ronde verlaten voordat de eindvoorwaarde is bereikt?

-

Het spel verlaten terwijl ze zich bij een team voegen?

-

Een telefoontje ontvangen midden in een ronde?

-

Hun verbinding met de ronde verliezen voor minder dan 15 seconden?

Door alle potentiële acties die spelers kunnen ondernemen of scenario's die zich kunnen voordoen terwijl spelers taken voltooien te visualiseren, kun je beter bepalen hoe de lay-out van je UI-elementen hun ervaring negatief beïnvloedt, en vervolgens aanpassingen maken voordat je je ontwerpen in Studio implementeert. Als taken intuïtief, onopdringerig en handig aanvoelen, is de kans groter dat spelers tijd in je spel doorbrengen en later terugkomen.

Bij het ontwikkelen van gebruikersflows voor je eigen spel, overweeg het volgende:

-

Wat je wilt dat spelers in je spel doen en wat ze willen doen, kan volledig verschillend zijn. Het is het beste om je lay-outs te testen met meerdere soorten spelers  om een begrip te krijgen van de paden die ze willen nemen om hun doelen te bereiken.

-

Flowcharts kunnen moeilijk te lezen en ineffectief worden als ze proberen meerdere scenario's tegelijk binnen het diagram vast te leggen. Om je aandacht op elke taak te richten, beperk flowcharts tot één primaire taak tegelijk .

-

Interactiepatronen variëren afhankelijk van of spelers aanraakbediening, gamepads of computermuizen gebruiken om met je spel te interageren. Als je ontwerpt voor meerdere apparaten, ontwikkel unieke gebruikersflows voor elk apparaat  zodat je pijnpunten kunt identificeren en workflows kunt vereenvoudigen.

Nadat je het ontwerp van je wireframes hebt afgerond, is het tijd om naar Studio te gaan en je UI tot leven te brengen.

[Volgende](/docs/nl-nl/tutorials/curriculums/user-interface-design/implement-designs-in-studio)[Vorige](/docs/nl-nl/tutorials/curriculums/user-interface-design/choose-an-art-style)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
