<!-- Source: https://create.roblox.com/docs/nl-nl/production/analytics/retention -->

Retentie | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Analytics](/docs/nl-nl/production/analytics)

# Retentie

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Retentie  meet hoeveel gebruikers terugkeren naar je game na hun eerste bezoek in 1 dag, 7 dagen en 30 dagen.

## [Bekijk retentiemetrics](#bekijk-retentiemetrics)[](#bekijk-retentiemetrics)

Om de retentie-analyse van je game te bekijken:

1.

Ga naar [Creations](https://create.roblox.com/dashboard/creations)  en selecteer een game.

2.

In het Analytics -menu aan de linkerkant, selecteer Retentie .

Om de analytics voor groepsbezit games te bekijken, moet je [groepsmachtigingen voor analytics](/docs/nl-nl/production/analytics/analytics-dashboard)  hebben.

De x-as van je [retentiecohorten](#begrijp-je-nieuwe-gebruikerscohorten)  is gebaseerd op de eerste speeldatum van een nieuwe gebruiker. Dit biedt een nauwkeuriger beeld van hoe de wijzigingen die je op een specifieke dag aanbrengt, de retentie van die nieuwe gebruikerscohort in de loop van de tijd beïnvloeden.

Bijvoorbeeld, de datum 06/20 op alle drie de grafieken toont je dezelfde cohort:

-

D1 retentie : Gebruikers die de game voor het eerst speelden op 06/20 en de volgende dag terugkeerden naar de game.

-

D7 retentie : Gebruikers die de game voor het eerst speelden op 06/20 en na 1 week terugkeerden naar de game.

-

D30 retentie : Gebruikers die de game voor het eerst speelden op 06/20 en na 1 maand terugkeerden naar de game.

De gegevens voor de meest recente datums op je D7- en D30-grafieken kunnen leeg zijn. Voor een gebruikerscohort dat de game voor het eerst speelde op 06/20, verschijnen hun D7-retentiedata op 06/27 (na 7 dagen), terwijl hun D30-retentiedata op 07/20 verschijnen (na 30 dagen).

In het volgende voorbeeld is er een dip rond 05/13 op alle retentiegrafieken. Dit geeft aan dat gebruikers die op 05/13 zijn verworven, lagere D1-, D7- en D30-retentie hadden. Dit is een typische en tijdelijke uitkomst na een grote instroom van nieuwe gebruikers.

![](https://prod.docsiteassets.roblox.com/assets/analytics/retention/AnalyticsRetentionChart.png) In dit voorbeeld is er een dip rond 05/13 op alle retentiegrafieken. Dit geeft aan dat gebruikers die op 05/13 zijn verworven, lagere D1-, D7- en D30-retentie hadden. Dit is een typische en tijdelijke uitkomst na een grote instroom van nieuwe gebruikers.

## [Begrijp je nieuwe gebruikerscohorten](#begrijp-je-nieuwe-gebruikerscohorten)[](#begrijp-je-nieuwe-gebruikerscohorten)

Je kunt de tabel met nieuwe gebruikersretentiecohorten onderaan je retentiedashboard vinden. Je kunt zowel dagelijkse als wekelijkse cohorten bekijken:

-

Dagelijkse cohorten  laten je zien hoeveel nieuwe gebruikers zijn behouden gedurende hun eerste 10 dagen.

-

Wekelijkse cohorten  laten je de retentie over een periode van 10 weken volgen door gebruikers te groeperen op basis van de week waarin ze zijn begonnen (maandag - zondag).

Cohorten zijn nuttig voor het volgen van de impact van grote updates, evenementen of marketingcampagnes die je uitvoert. Je kunt bijvoorbeeld meten of nieuwe gebruikers die tijdens een groot evenement zijn begonnen met het spelen van je game, langer blijven dan gebruikers die voor het evenement zijn begonnen.

![](https://prod.docsiteassets.roblox.com/assets/analytics/retention/CohortAnalysis.png)

Voor elke cohort kun je ook belangrijke down-funnel metrics analyseren, waaronder:

-

7D speeltijd per gebruiker (cumulatief)

-

7D conversieratio van spelers (cumulatief)

-

7D omzet per gebruiker (cumulatief)

-

30D omzet per gebruiker (cumulatief)

Deze metrics stellen je in staat om te zien of de nieuwe gebruikers die tijdens een groot evenement met het spelen van je game zijn begonnen, beter monetiseren dan andere gebruikerscohorten.

![](https://prod.docsiteassets.roblox.com/assets/analytics/retention/CohortAnalysis2.png)

## [Verbeter de retentie op dag 1](#verbeter-de-retentie-op-dag-1)[](#verbeter-de-retentie-op-dag-1)

De retentie op dag 1 is het percentage nieuwe gebruikers dat terugkomt naar je game na hun eerste bezoek. Om deze metric te verbeteren, richt je je op de kernloop  van je game, de ervaring van nieuwe gebruikers  en de prestaties .

### [Kernloop](#kernloop)[](#kernloop)

De kernloop zijn de acties die gebruikers herhalen in je game om vooruitgang te boeken in een enkele sessie.

-

Voor een huisdieradoptiespel kan een kernloop het adopteren, trainen en levelen van huisdieren omvatten.

-

Voor een tycoonspel kan een kernloop het beheren van een bedrijf, het balanceren van middelen en het concurreren met andere gebruikers omvatten.

Het volgende voorbeeld is een pad om je kernloop te verbeteren:

1.

Identificeer de kernstappen  die gebruikers in de loop uitvoeren en maak ze duidelijk en leuk.

2.

Balanceer de uitdaging  van je kernloop om frustratie en verveling bij gebruikers te voorkomen.

3.

Beloon gebruikers  voor het voltooien van je kernloop met feedback, valuta, items en prestaties.

Om meer te leren over hoe je kernlopen ontwerpt, zie [Kernlopen](/docs/nl-nl/production/game-design/core-loops) .

### [Ervaring van nieuwe gebruikers](#ervaring-van-nieuwe-gebruikers)[](#ervaring-van-nieuwe-gebruikers)

Ervaring van nieuwe gebruikers (FTUE)  is hoe nieuwe gebruikers je kernloop voor de eerste keer ervaren. Om je FTUE te verbeteren:

1.

Gebruik een korte tutorial  of contextuele informatie zoals tooltips om gebruikers door je kernloop te begeleiden. Vermijd lange tutorials om gebruikers zo snel mogelijk naar het plezier te brengen.

2.

Lever een vreugdevol moment  nadat gebruikers je kernloop voor de eerste keer hebben voltooid.

3.

Geef een preview van de vooruitgang  die gebruikers kunnen maken als ze je kernloop meerdere keren voltooien.

Je kunt ook analytics gebruiken om je FTUE te verbeteren:

1.

Lijst de stappen van je kernloop . Voor een huisdieradoptiespel kunnen de stappen zijn:

-

Adopteer een huisdier.

-

Train een huisdier.

-

Level een huisdier.

2.

Volg de voltooiingsgraad van elke stap . Gebruik speciale in-game items om de voltooiing van elke stap te markeren. Volg zowel positieve als negatieve ervaringen. Als de FTUE bijvoorbeeld een gevecht met een NPC omvat, volg dan of gebruikers vaker winnen of verliezen.

3.

Identificeer en los grote afhaakmomenten op . Als het bezoeken van de dierenwinkel bijvoorbeeld de hoogste afhaakgraad heeft, kun je de wrijving in deze stap verminderen door de dierenwinkel gemakkelijker te vinden te maken.

Vermijd een complexe of tijdrovende FTUE, omdat je gebruikers zo snel mogelijk naar het plezier wilt brengen, idealiter binnen 5 minuten of minder na het betreden van je game.

Om meer te leren over hoe je je FTUE ontwerpt, zie [Onboarding](/docs/nl-nl/production/game-design/onboarding) .

### [Prestaties](#prestaties)[](#prestaties)

Prestaties  is hoe goed je game draait op verschillende apparaten en platforms. Om je prestaties te verbeteren:

1.

Test op verschillende apparaten en platforms  om eventuele bugs op te lossen die de prestaties kunnen beïnvloeden.

2.

Monitor crashpercentages, frame rates en fouten  elke keer dat je je game bijwerkt.

3.

Stel een gebruikersgemeenschap op  die kan helpen bij het identificeren van bugs en crashes.

## [Verbeter de retentie op dag 7](#verbeter-de-retentie-op-dag-7)[](#verbeter-de-retentie-op-dag-7)

De retentie op dag 7 is het percentage nieuwe gebruikers dat terugkomt naar je game na hun eerste bezoek op de 8e dag (dag 7). Om deze metric te verbeteren, richt je je op het progressiesysteem  van je game.

### [Progressiesysteem](#progressiesysteem)[](#progressiesysteem)

Het progressiesysteem is hoe gebruikers doelen bereiken en beloningen verdienen in je game, zoals levelen en nieuwe content ontgrendelen. Om een gezond progressiesysteem op te bouwen:

1.

Stel duidelijke gebruikersdoelen in : Korte-termijndoelen kunnen onmiddellijke voldoening en feedback bieden, en lange-termijndoelen kunnen gebruikers richtingen geven om naar toe te werken over een langere periode.

2.

Voeg variëteit in content toe : Een verscheidenheid aan content, zoals nieuwe modi, inventarisitems en sociale functies, kan voorkomen dat gebruikers zich vervelen.

3.

Balanceer de moeilijkheid : Als gebruikers te snel vooruitgang boeken, kunnen ze zonder content komen te zitten om te verkennen. Als ze te langzaam vooruitgang boeken, kunnen ze zich vervelen en gefrustreerd raken en de motivatie verliezen om te blijven.

Je kunt analytics gebruiken om je progressiesysteem te verbeteren:

1.

Identificeer je progressiesysteem . Bijvoorbeeld:

-

Verdienen van in-game valuta voor een tycoonspel.

-

Ontgrendelen van nieuwe items om te verzamelen voor een itemverzamelspel.

-

Beheersen van casts of vaardigheden voor een magische wereldgame.

2.

Meet de gebruikersverdeling  door het aantal gebruikers voor elk progressieniveau bij te houden om te zien hoe lang het duurt voordat een gebruiker het volgende niveau bereikt door elke gebruiker een speciaal in-game item te geven zodra ze naar het volgende niveau gaan.

3.

Los het progressiesysteem op . Als gebruikers te snel of te langzaam levelen, evalueer dan de moeilijkheden van de taken in je progressiesysteem en pas ze aan om ervoor te zorgen dat gebruikers de juiste hoeveelheid tijd aan elk niveau besteden.

## [Verbeter de retentie op dag 30](#verbeter-de-retentie-op-dag-30)[](#verbeter-de-retentie-op-dag-30)

De retentie op dag 30 is het percentage nieuwe gebruikers dat terugkomt naar je game na hun eerste bezoek op de 31e dag (dag 30). Om deze metric te verbeteren, richt je je op het eindingssysteem  van je game.

### [Eindingssysteem](#eindingssysteem)[](#eindingssysteem)

Het eindingssysteem is wat beschikbaar is voor gebruikers nadat ze de belangrijkste doelstellingen van je game hebben voltooid of hogere niveaus hebben bereikt. Om het te verbeteren:

1.

Voeg meer content toe : Regelmatige updates kunnen gebruikers terug laten komen. Een veelvoorkomende frequentie is om kleinere updates van de bestaande mechanics elke 2-4 weken uit te brengen, en grotere updates van nieuwe functies elke 2-3 maanden.

2.

Voeg sociale mechanics toe : Sociale mechanics kunnen gebruikers motiveren om betrokken te blijven bij je game en interactie te hebben met andere gebruikers terwijl ze wachten op nieuwe content. Veelvoorkomende sociale systemen en elementen zijn onder andere ruilen, feesten, gilden en competitieve systemen zoals PvP (speler tegen speler), toernooien en ranglijsten.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
