<!-- Source: https://create.roblox.com/docs/nl-nl/production/game-design/onboarding -->

Onboarding | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Game-ontwerp](/docs/nl-nl/production/game-design)
6. /
7. Je ervaring bouwen

# Onboarding

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Onboarding , ook wel bekend als de First-Time User Experience (FTUE), omvat de eerste paar minuten van gameplay die nieuwe spelers ervaren. De FTUE introduceert het spel, de interface en de mechanics, en kan tutorials bevatten die spelers leren hoe ze moeten spelen. Het succes van een FTUE wordt bepaald door hoe goed het twee metrics bereikt:

-

Dag 1 retentie

-

Onboarding doelen

## [Dag 1 retentie](#dag-1-retentie)[](#dag-1-retentie)

Dag 1 Retentie  wordt gemeten aan de hand van het aantal spelers dat de FTUE doorloopt, bekend als de Player Funnel . De trechter is aan de bovenkant het breedst en aan de onderkant het smalst, omdat minder spelers elke stap voltooien. Alle spellen verliezen een bepaald aantal spelers langs deze weg.

 ![Een diagram van een omgekeerde piramide die in vier secties is verdeeld die van boven naar beneden in grootte afnemen om de tunnel van steeds minder spelers die elke stap voltooien aan te geven.](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding/onboarding_1.png)

De onboarding ervaring heeft als doel om het afvallen tussen stappen te beperken en zoveel mogelijk nieuwe spelers te behouden. Om lekken in je trechter te identificeren en te "dichten", kun je [Experiments](/docs/nl-nl/production/experiments)  gebruiken. Door A/B-tests uit te voeren op specifieke tutorialstappen, kun je de causale impact van verschillende ontwerpen meten, zoals een kortere dialoogsequentie versus een begeleide pijl, om te zien welke versie leidt tot hogere voltooiingspercentages.

Spellen met hoge D1-retentiemetrics danken dat succes vaak aan het effectief bereiken van hun onboardingdoelen door constante iteratie en datagestuurd testen.

## [Onboarding doelen](#onboarding-doelen)[](#onboarding-doelen)

Veel van de meest succesvolle onboarding ervaringen volgen deze algemene praktijken:

-

Leer de basis

-

Kom snel bij het plezier

-

Laat spelers meer willen

### [Leer de basis](#leer-de-basis)[](#leer-de-basis)

Voor succesvolle onboarding moeten spelers de bedieningselementen voor navigatie en interactie begrijpen. Het weergeven van complexe, onbekende bedieningselementen op het scherm of het opnemen ervan in een tutorial kan nuttig zijn.

![Een close-up van de UI in het spel Super Striker League die toont welke knoppen je op je muis of toetsenbord moet indrukken om verschillende acties uit te voeren.](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding/onboarding_2.png)[* Super Striker League*](https://www.roblox.com/games/3360853050/)  bedieningselementen.

Naast de bedieningselementen moet onboarding ook kennis over de Core Loop  van het spel overbrengen, de repetitieve acties voor vooruitgang die het spel definiëren. Het is cruciaal dat spelers begrijpen * wat*  van hen wordt verwacht en * waarom*  ze het zouden moeten doen.

### [Kom snel bij het plezier](#kom-snel-bij-het-plezier)[](#kom-snel-bij-het-plezier)

Nieuwe spelers beslissen meestal binnen enkele minuten over hun interesse in een spel. Om ze te behouden, moet je snel waarde demonstreren door middel van:

-

Spelvoortgang

-

Sociale motivatoren

-

Startitems en valuta

#### [Voortgang](#voortgang)[](#voortgang)

Voortgang  wordt gevoeld wanneer een speler beter wordt, toegang krijgt tot nieuwe systemen en doelen bereikt. Een geweldige manier om dit te faciliteren is door * Player XP-gebaseerde levelingsystemen* .

![Een grafiek van de ervaring die een speler nodig heeft om in een spel te levelen. De curve stijgt exponentieel van links naar rechts.](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding/onboarding_3.png) Player XP Level Up curve.

Het laag houden van drempels voor de vroege levels van een speler stelt hen in staat om snel te levelen en onmiddellijk het plezier van voortgang te voelen. Je kunt Configs  gebruiken om deze XP-drempels in realtime af te stemmen. Dit stelt je in staat om de voortgangscurve te verzachten of beloningen aan te passen op basis van het gedrag van live spelers zonder servers opnieuw te hoeven opstarten of een volledige update te pushen.

#### [Sociale motivatoren](#sociale-motivatoren)[](#sociale-motivatoren)

Sociale spelers geven vaak de voorkeur aan onboarding ervaringen die mogelijkheden voor samenwerking en competitie bieden. Als je spel sterk afhankelijk is van sociale interactie, overweeg dan om Experiments  te gebruiken om verschillende matchmakingparameters tijdens de FTUE te testen om te zien welke sociale groeperingen leiden tot betere langdurige betrokkenheid.

#### [Startitems en valuta](#startitems-en-valuta)[](#startitems-en-valuta)

Het aanbieden van gratis items zoals uitrusting of zachte valuta stelt spelers in staat om vroeg met je systemen in contact te komen. Het vinden van de juiste balans is echter van vitaal belang. Het doel is om spelers de kans te geven om te genieten van de nut of zelfexpressie die door die items wordt geboden om toekomstige speeltijd aan te moedigen.

Door Experiments  te gebruiken, kun je verschillende startbedragen van valuta aan verschillende groepen nieuwe spelers geven om te zien welke leidt tot hogere retentie. Zodra je de ideale balans hebt gevonden, stellen Configs  je in staat om die startwaarde wereldwijd en onmiddellijk voor alle toekomstige spelers bij te werken.

Voor meer informatie over core loops, zie [Core loops](/docs/nl-nl/production/game-design/core-loops) .

### [Laat spelers meer willen](#laat-spelers-meer-willen)[](#laat-spelers-meer-willen)

Aan het einde van de onboarding moeten spelers zich bewust zijn van het volledige scala aan beschikbare content. Het effectief ontwerpen van deze twee kenmerken houdt spelers terugkomen:

-

Doelen

-

Momenten van vreugde

#### [Doelen](#doelen)[](#doelen)

Het bieden van korte, middellange en lange termijn doelen helpt spelers om toekomstige speelsessies te conceptualiseren en hun toekomstige succes voor te stellen. Deze doelen kunnen verschillende vormen aannemen: vaardigheidsbomen, seizoenspassen, quests, verzamelingen, en meer. Het zichtbaar maken van deze doelen op zeer zichtbare plaatsen, hetzij in de spelwereld of de UI, biedt een frequente herinnering aan spelers waar ze naar toe werken.

Om te leren hoe je dit kunt bereiken via seizoenspassen, zie [Seizoen Pass Ontwerp](/docs/nl-nl/production/game-design/season-pass-design) .

![Een pop-up UI in het spel Jailbreak die verschillende items toont die een speler kan verdienen als ze door een seizoen spelen. De seizoenspas exclusieve items zijn gemarkeerd met een felle kleur om de aandacht te trekken.](https://prod.docsiteassets.roblox.com/assets/game-design/onboarding/onboarding_4.png) Seizoen Pas in * Jailbreak* .

#### [Momenten van vreugde](#momenten-van-vreugde)[](#momenten-van-vreugde)

Vreugde kan worden opgewekt door beloningen, leuke animaties en feestelijke visuele effecten wanneer een speler een mijlpaal bereikt. Het beëindigen van de onboarding ervaring met een opzettelijk ontworpen moment van vreugde laat spelers zich voldaan voelen en enthousiast om terug te keren voor hun volgende sessie.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
