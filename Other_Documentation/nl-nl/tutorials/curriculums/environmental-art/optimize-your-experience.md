<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/curriculums/environmental-art/optimize-your-experience -->

Optimaliseer je spel | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Optimaliseer je spel

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Je spel optimaliseren  is het proces van het configureren van je assets en Studio-instellingen om je frame rate en prestatie-niveaus hoog te houden voor apparaten met geheugen- en grafische verwerkingsunit (GPU) beperkingen. Dit proces zorgt ervoor dat bijna elke gebruiker dezelfde gameplay- en visuele ervaring heeft terwijl ze je omgeving bekijken.

Met behulp van het [Environment Art - Optimaliseren](https://www.roblox.com/games/14447845297/Environment-Art-Optimizing)  .rbxl  bestand als referentie, laat deze sectie van het curriculum voor milieukunst je zien hoe je je plaatsbestand kunt beoordelen en configureren voor optimale graphics, inclusief richtlijnen over:

-

Het beoordelen van de fysica- en renderparameters van elk asset om te bevestigen dat ze geheugen en engine-prestaties behouden.

-

Het culleren van overtollige texturen, geometrie of transparanties die onnodig de hoeveelheid berekeningen verhogen die de Roblox Engine moet uitvoeren om je assets te renderen.

Hoewel de Roblox Engine het meeste optimalisatiewerk voor je doet, kun je deze optimalisatie-inspanningen ondersteunen door de [Microprofiler](/docs/nl-nl/performance-optimization/microprofiler)  te gebruiken om te zien waar het meer tijd kost om specifieke frames te renderen. Met deze informatie kun je weloverwogen beslissingen nemen over welke assets je aandacht nodig hebben met betrekking tot hun parameters of overtollige inhoud. [Scene-analyse](/docs/nl-nl/performance-optimization/scene-analysis)  is een ander krachtig hulpmiddel voor het controleren van het gebruik van middelen.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section5/Overview.jpg)

## [Beoordeel fysica- en renderparameters](#beoordeel-fysica--en-renderparameters)[](#beoordeel-fysica--en-renderparameters)

In [Stel een assetbibliotheek samen](/docs/nl-nl/tutorials/curriculums/environmental-art/assemble-an-asset-library)  heb je geleerd hoe belangrijk het is om fysica- en renderparameters in te stellen die ervoor zorgen dat je assets hun hoge visuele kwaliteit behouden op apparaten met geheugen- en GPU-beperkingen. Het is echter gebruikelijk dat je tijdens het bouwen van je omgeving deze parameters aanpast op basis van de contextuele positie en het doel van een asset binnen je spel. Bijvoorbeeld, veel van de begroeiing in de uiteindelijke voorbeeld laser tag omgeving werpt schaduwen ondanks een prestatiekost omdat het bijdraagt aan de realiteit van de omgeving.

Wanneer je fysica- en renderparameters wijzigt, is het nuttig om aan het einde van het ontwikkelingsproces alle parameters te beoordelen om te zien waar je een parameter kunt optimaliseren terwijl je esthetische doelen en gameplay-eisen behoudt. Ter illustratie, je kunt de [BasePart.CastShadow](/docs/nl-nl/reference/engine/classes/BasePart#CastShadow)  eigenschap voor de begroeiing nabij de randen van het speelgebied uitschakelen om prestaties te besparen zonder de gameplay of visuele ervaring van een gebruiker te verstoren.

![Een buitenaanzicht van het voorbeeld laser tag spel dat schaduwen werpt.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section5/ReviewingParameters-Disabled.jpg)[BasePart.CastShadow](/docs/nl-nl/reference/engine/classes/BasePart#CastShadow)  = Uitgeschakeld

![Een buitenaanzicht van het voorbeeld laser tag spel dat geen schaduwen werpt. Er is bijna geen verschil in dit uitzicht, maar het verbetert de prestaties.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section5/ReviewingParameters-Enabled.jpg)[BasePart.CastShadow](/docs/nl-nl/reference/engine/classes/BasePart#CastShadow)  = Ingeschakeld

## [Cull niet-essentiële inhoud](#cull-niet-essentiële-inhoud)[](#cull-niet-essentiële-inhoud)

Nadat je je fysica- en renderparameters hebt beoordeeld, kun je de assets zelf bekijken om te zien waar je niet-essentiële inhoud uit het spel kunt verwijderen die geen invloed heeft op je gameplay, zoals identieke texturen met verschillende asset-ID's, complexe geometrie met veel vertices, of transparanties die bovenop elkaar worden gestapeld afhankelijk van het camerastandpunt. De volgende secties beschrijven wat je kunt doen om deze inhoud te beoordelen en waarom het helpt bij optimalisatie-inspanningen.

### [Verwijder dubbele texturen](#verwijder-dubbele-texturen)[](#verwijder-dubbele-texturen)

Wanneer je overgaat van het ontwikkelen van je assets naar het bouwen van je omgeving, is het gebruikelijk om iteraties van meshes of texturen te maken terwijl je ontdekt wat nodig is voor je esthetische doelen of gameplay-eisen. Als je je assets niet omzet in [pakketten](/docs/nl-nl/projects/assets/packages) , maak je unieke asset-ID's wanneer je deze iteraties in Studio importeert, die de Roblox Engine moet refereren terwijl deze je assets binnen de omgeving rendert.

Bijvoorbeeld, als je de volgende twee brandkranen afzonderlijk in Studio zou importeren, zelfs als ze er precies hetzelfde uitzien, behandelt de Roblox Engine ze als twee objecten met unieke asset-ID's. Hoe meer unieke aanroepen de engine moet maken, hoe meer impact dit heeft op geheugen en prestaties. Om deze reden is het belangrijk om te bevestigen dat wanneer je een asset meerdere keren hergebruikt, elke instantie van die asset dezelfde asset-ID gebruikt, zodat de engine slechts één aanroep hoeft te doen om deze herhaaldelijk te renderen.

 ![Twee exact dezelfde brandkranen met unieke asset-ID's. Er is geen visueel verschil, maar de dubbele asset-ID's hebben een negatieve impact op de prestaties.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section5/RemovingTextures-Firehydrants.jpg)

### [Optimaliseer geometrie](#optimaliseer-geometrie)[](#optimaliseer-geometrie)

Als je merkt dat je meer aanpassingen moet maken om de frame rate op verschillende apparaten te verhogen, is het nuttig om te zien waar je je geometrie kunt optimaliseren door:

-

Groepen van meshes samen te voegen tot één asset.

-

Het aantal polygonen van assets met geometrische complexiteit te verlagen.

Om deze eerste techniek verder uit te leggen, vertegenwoordigt elke unieke asset in je spel een draw call op de GPU waarin het een signaal naar de GPU stuurt om informatie op te vragen zodat de Roblox Engine de asset correct kan renderen. Hoe meer unieke assets je hebt, hoe meer draw calls het systeem moet maken. Om deze reden, als je een groep meshes hebt die een groter onderdeel in je spel vormen, kun je ze samenvoegen in externe modelleringstools om de noodzaak voor meerdere draw calls te verminderen.

Ter illustratie, de uiteindelijke voorbeeld laser tag omgeving groepeert meerdere delen en meshes samen om de grote torens buiten het gebouw te creëren. Als je al deze individuele componenten samenvoegt, kun je het een enkele asset maken met slechts één asset-ID, en het aantal draw calls verlagen van 8 naar 1. Het is echter belangrijk op te merken dat deze techniek je vermogen om de visuele en fysieke kenmerken van elke component vrij te wijzigen, zoals de positie of het materiaal, verwijdert.

Bijvoorbeeld, in de volgende afbeelding blijft de linker toren meerdere assets onder een [Model](/docs/nl-nl/reference/engine/classes/Model)  object, en de rechter toren is een enkele asset. Je kunt elke component van de linker toren afzonderlijk aanpassen, maar wanneer je de rechter toren wijzigt, zoals het veranderen van de kleur naar zwart, beïnvloedt dit het geheel van het object. Dit is waarom het belangrijk is om deze techniek alleen te overwegen aan het einde van de ontwikkeling van je omgeving wanneer je weet waar je de prestaties kunt verbeteren zonder je esthetische doelen te beïnvloeden.

 ![Een vooraanzicht van de twee torens. De toren aan de linkerkant bevat meerdere assets onder een enkel model, terwijl de toren aan de rechterkant het aantal assets vermindert door alle textuurobjecten te verwijderen.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section5/OptimizingGeo-Towers.jpg)

Om de tweede techniek verder uit te leggen, hebben assets met geometrische complexiteit meer polygonen, wat betekent dat ze meer vertices hebben die de engine moet berekenen terwijl deze hun visuele uiterlijk rendert. Dit betekent dat assets met minder complexiteit en detail minder kostbaar zijn om te renderen, wat leidt tot een verbetering van zowel prestaties als geheugen.

Als je ervoor kiest om deze tweede techniek te gebruiken, is het belangrijk om te onthouden om je pakketten bij te werken met de nieuwe import in plaats van een nieuwe asset-ID te creëren, anders moet de Roblox Engine twee aparte aanroepen doen voor elke asset-ID.

### [Verwijder gelaagde transparanties](#verwijder-gelaagde-transparanties)[](#verwijder-gelaagde-transparanties)

Om een gevoel van realisme aan de omgeving te geven, bevat de uiteindelijke voorbeeld laser tag omgeving veel meshes met verschillende niveaus van transparantie, zoals de begroeiing in de buitenruimte, glas op de futuristische borden of plantenbakken. Wanneer de camera meerdere semi-transparante objecten bekijkt die voor of achter elkaar staan, moet de Roblox Engine de overlappende pixels meerdere keren renderen om rekening te houden met de transparante gebieden. Dit proces wordt hoge transparantie overdraw genoemd, en het heeft een aanzienlijke impact op de prestaties.

Bijvoorbeeld, overweeg het volgende uitzicht op een plantenbak in de voorbeeldomgeving. De engine moet de transparante gebieden van de bladeren tussen de plant die het dichtst bij de camera staat en de plant die het dichtst bij het buitengebied staat in lagen renderen, wat gelijk staat aan honderden duizenden overgetrokken pixels. Om een deel van deze impact te verlichten, is het belangrijk om de lay-out van alle semi-transparante objecten in je omgeving te beoordelen en ervoor te zorgen dat er niet te veel plaatsen zijn waar er veel lagen van overlap zijn, vooral in grote gebieden van het scherm.

![Een Rthro-avatar die naar een plantenbak kijkt met meerdere planten met transparantie tussen de bladeren.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section5/LayeredTransparencies-Left.jpg)

![Een zijaanzicht van de Rthro-avatar die naar een plantenbak kijkt met meerdere planten met transparantie tussen de bladeren, en voorbeeldlagen van overgetrokken pixels zijn gemarkeerd om te laten zien waar er overdrawn is in de omgeving.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section5/LayeredTransparencies-Right.jpg)

Wanneer je klaar bent met het beoordelen van al je inhoud om ervoor te zorgen dat deze optimaal is op verschillende apparaten, is je spel nu klaar voor publicatie!

We zijn benieuwd naar je ervaringen met het volgen van het Curriculum voor Milieukunst. Als je vragen, opmerkingen of aanvullende feedback over het proces hebt, laat dan een reactie achter op onze [Environmental Art Curriculum Q&A](https://devforum.roblox.com/t/feedback-on-environmental-art-curriculum/2592218) .

[Vorige](/docs/nl-nl/tutorials/curriculums/environmental-art/construct-your-world)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
