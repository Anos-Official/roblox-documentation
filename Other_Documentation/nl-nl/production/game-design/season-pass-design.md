<!-- Source: https://create.roblox.com/docs/nl-nl/production/game-design/season-pass-design -->

Seizoenpas ontwerp | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Game-ontwerp](/docs/nl-nl/production/game-design)
6. /
7. Inkomsten genereren met je ervaring

# Seizoenpas ontwerp

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een * seizoenpas*  is een tijdgebonden, op missies gebaseerde voortgangssysteem dat deel uitmaakt van de contentcadans van een ervaring. Spelers voltooien missieobjectieven om beloningen te verdienen gedurende de vooraf gedefinieerde periode of "seizoen".

Seizoenpassen zijn tijdgebonden ontwerpstrategieën die in Roblox-ervaringen worden gebruikt om nieuwe content te leveren, de spelersretentie te bevorderen en inkomsten te genereren. Seizoenpassen moedigen spelers aan om taken te voltooien, ervaring punten (XP) te verdienen en door beloningsniveaus te klimmen. Bij het maken van een seizoenpas is het van cruciaal belang om:

-

Doelen te identificeren

-

Parameters te creëren

-

Missies te ontwerpen

-

Effectief samen te werken

![](https://prod.docsiteassets.roblox.com/assets/game-design/season-pass-design/season-pass-design-0.png) Seizoenpas in * Jailbreak*

Voor kant-en-klare functionaliteit om seizoenpassen te maken, zie het [Seizoenpassen](/docs/nl-nl/resources/feature-packages/season-passes)  functiepakket.

Hoewel ze qua naam vergelijkbaar zijn, zijn seizoenpassen geen algemene ervaringpassen. Algemene [passen](/docs/nl-nl/production/monetization/passes)  zijn eenmalige aankopen die gameplay-bonussen verlenen.

## [Doelen identificeren](#doelen-identificeren)[](#doelen-identificeren)

Het * doel*  van een seizoenpas wordt gedefinieerd door de gewenste impact op spelers. Een seizoenpas kan meerdere doelen hebben. Veelvoorkomende doelen die succesvolle seizoenpassen prioriteren zijn:

-

Kernloopafstemming

-

Spelermotivatie

-

Spelerbegrip

-

Speleranticipatie

#### Kernloopafstemming

Een succesvol seizoenpassysteem is gebouwd op de kernloop van de ervaring, de mechaniek waarop de ervaring is gebaseerd, en stimuleert spelers om zich met alle systemen en content van je ervaring bezig te houden. Seizoenpasmissies aan elk systeem en type content in je ervaring te koppelen heeft meerdere voordelen:

-

Zorgt ervoor dat spelers de context hebben om je seizoenpas gameplayvereisten te begrijpen.

-

Introduceert spelers aan nieuwe systemen en content waar ze zich misschien niet van bewust zijn op een begrijpelijke manier.

-

Geeft spelers een verscheidenheid aan dingen om te doen, zodat het voltooien van de pas niet saai wordt.

Voor meer informatie over kernlopen, zie [Kernlopen](/docs/nl-nl/production/game-design/core-loops) .

#### Spelermotivatie

Een succesvolle seizoenpas zorgt ervoor dat spelers gemotiveerd zijn om de missies van het hele seizoen te voltooien. Dit kan worden bereikt door missies beheersbaar te maken en niet de volledige speeltijd van de speler elke dag in beslag te nemen, in te spelen op verschillende speelstijlen door een verscheidenheid aan taken aan te bieden, de seizoensinterface duidelijk de voortgang van de speler weer te geven, en de beloningen van de seizoenpas nauwkeurig de inspanning te laten weerspiegelen die nodig is om ze te verkrijgen.

#### Spelerbegrip

Een succesvolle seizoenpas is vanzelfsprekend, waarbij spelers begrijpen hoe ze vooruitgang kunnen boeken in de pas in een gegeven seizoen. Spelers zijn automatisch ingeschreven in het systeem van het seizoen, ze hoeven zich niet te herinneren om zich elke nieuwe seizoen aan te melden. Een zeer zichtbare Seizoen UI helpt dit te faciliteren, met de missie- en seizoensvoortgang, beloningsstatus en resterende tijd om het seizoen te voltooien, allemaal duidelijk gecommuniceerd.

#### Speleranticipatie

Een succesvolle seizoenpaservaring laat spelers enthousiast zijn voor het volgende seizoen en uitkijken naar nieuwe beloningen. Dit is te bereiken door de beloningen, vooral de premium en laatste beloningen, de moeite waard te maken. Het hebben van een waardevolle laatste beloning als een kroonstuk en viering van de inspanning en toewijding van de speler kan ertoe leiden dat spelers zich afvragen wat het thema en de laatste beloningen van het volgende seizoen zullen zijn, en moedigt hen aan om terug te komen voor meer.

## [Parameters creëren](#parameters-creëren)[](#parameters-creëren)

Met je doelen gedefinieerd, zijn je seizoenpasparameters de grenzen waarin je ze zult bereiken. Bij het definiëren van parameters voor je seizoenpas is het belangrijk om rekening te houden met het volgende:

-

Seizoensduur

-

Seizoensniveaus

-

Niveau beloningen

-

Toekomstige updates

### [Seizoensduur](#seizoensduur)[](#seizoensduur)

De * seizoensduur*  is de periode dat een seizoen van beloningen beschikbaar is voor spelers. De lengte van het seizoen is gebaseerd op de capaciteit van je team, maar één maand wordt beschouwd als een goed startpunt. Een cadans  is hoe vaak seizoensgebonden evenementen beschikbaar zijn. Het toestaan van ten minste een week rust tussen het einde van het ene seizoen en het begin van het volgende creëert een buffer die de volgende voordelen heeft:

-

Beschermt spelers tegen burn-out die zich hard hebben ingespannen om het laatste niveau te behalen.

-

Biedt het ontwikkelingsteam meer tijd om missies en beloningen te produceren.

![](https://prod.docsiteassets.roblox.com/assets/game-design/season-pass-design/season-pass-design-4.png) Seizoensduur in * Jailbreak*

### [Seizoensniveaus](#seizoensniveaus)[](#seizoensniveaus)

* Seizoensniveaus*  zijn de mijlpalen die spelers moeten bereiken om beloningen te verdienen gedurende het seizoen. Om door de niveaus te klimmen, voltooien spelers missies om ervaring punten (XP) te verdienen. Wanneer spelers genoeg XP verdienen, promoveren ze naar het volgende niveau en ontvangen ze beloningen voor het niveau dat ze net hebben voltooid. Bij het ontwerpen van seizoensniveaus is tien niveaus een goed begin. Spelers moeten het gevoel hebben dat ze vaak vooruitgang boeken, maar het aantal niveaus moet kort genoeg zijn zodat het niet ontmoedigend is aan het begin van een seizoen.

![](https://prod.docsiteassets.roblox.com/assets/game-design/season-pass-design/season-pass-design-5.png) Seizoensniveaus in * Jailbreak*

#### Niveau beloningen

* Niveau beloningen*  zijn de items die spelers ontvangen wanneer ze een seizoensniveau-mijlpaal bereiken die gedurende het seizoen is vastgesteld. Wanneer een speler genoeg XP verzamelt om van het ene niveau naar het andere te promoveren, verdient hij niveau beloningen. De beloningen moeten een afspiegeling zijn van de hoeveelheid inspanning die nodig is om het niveau te voltooien op basis van de hoeveelheid vereiste XP. Niveau beloningen moeten items bevatten die spelers willen, maar niet te waardevol zijn. Enkele ideeën zijn:

-

Consumables: gezondheidsdranken, voedsel, power-ups, munitie.

-

Valuta: zacht of hard (kleine hoeveelheden).

-

Tijdelijke buffs: 10% schild, schadeboost, hulpbron generatie.

-

Aanpassingsitems: kleine avatarstukken, een nieuwe verf kleur voor een huis.

Extra aandacht is nodig bij het implementeren van de volgende secties van een seizoenpas:

-

Laatste beloningen

-

Hoe beloningen te claimen

-

Gratis passen

-

Premium passen

![](https://prod.docsiteassets.roblox.com/assets/game-design/season-pass-design/season-pass-design-6.png) Niveau beloningen in * Jailbreak*

#### Laatste beloningen

Een * laatste beloning*  is de laatste beloning aan het einde van de seizoenpas. Het creëren van een gloednieuw item voor de laatste beloning is een geweldige optie. Bovendien, het beëindigen van dat laatste beloningsitem nadat het seizoen voorbij is om het exclusief te maken voor het seizoenpassysteem creëert een sterkere prikkel en moedigt meer speeltijd aan. Laatste beloningen definiëren vaak de impact van een seizoenpas en zijn cruciaal om correct te ontwerpen om je gemeenschap te stimuleren en te belonen.

Hoewel je UI voor niveaus de beloningen toont die spelers verdienen, is het goed om ook eventuele 3D-modelgebaseerde beloningen direct weer te geven, vooral als het de laatste beloning is. Items zoals auto's, huizen, huisdieren en avatar kleding zijn veel aantrekkelijker "in het echt" dan een 2D-afbeelding in een UI. De laatste beloning zo tastbaar en spannend mogelijk maken voor je spelers zal hen betrekken en inspireren gedurende het hele seizoen.

![](https://prod.docsiteassets.roblox.com/assets/game-design/season-pass-design/season-pass-design-2.png)  Laatste beloning in * Jailbreak*

![](https://prod.docsiteassets.roblox.com/assets/game-design/season-pass-design/season-pass-design-1.png)  Laatste beloning in [* Dragon Adventures*](https://www.roblox.com/games/3475397644/)

##### Hoe beloningen te claimen

Bij het * claimen van beloningen*  is het beste om spelers te vereisen om ze te claimen via een knop in de seizoenpas UI. Automatische beloningen lopen het risico over het hoofd te worden gezien of verkeerd begrepen. Spelers dwingen om beloningen handmatig te accepteren doet twee dingen:

-

Het zorgt ervoor dat spelers weten dat ze beloningen hebben ontvangen en wat deze waren.

-

Het brengt spelers terug naar de seizoenpas UI, wat hen mogelijk de functie voor het eerst presenteert, of hen opnieuw betrekt na een periode van afwezigheid.

Zorg ervoor dat het voor de speler duidelijk is dat ze beloningen te verzamelen hebben. Een veelgebruikte manier om dit te doen is door een pictogram op de knop van de functie te plaatsen om de aandacht van spelers te trekken. Als een speler aan het einde van het seizoen onopgehaalde beloningen heeft, zorgt automatisch toekennen ervoor dat de speler nog steeds wordt beloond voor hun inspanningen.

##### Gratis passen

Een * gratis pas*  is een versie van een seizoenpas die beschikbaar is voor alle spelers. Spelers zijn automatisch ingeschreven in een gratis pas, waarbij ze standaard zich aanmelden voor elk seizoen om missies te voltooien en beloningen te verdienen. Gratis passen geven spelers een aantal missies elke dag die ze kunnen voltooien om XP te verdienen, maar ontvangen aparte beloningen dan degenen die premium passen hebben.

![](https://prod.docsiteassets.roblox.com/assets/game-design/season-pass-design/season-pass-design-7.png) Gratis seizoenpas in * Jailbreak*

Houders van gratis passen mogen geen premium missies voltooien of premium niveau beloningen verdienen, tenzij ze upgraden naar de premium pas. Het hebben van dit gelaagde verschil moedigt en beloont nog steeds de inspanning en speeltijd van spelers, maar biedt een monetisatiekans voor je ervaring en stimuleert spelers om te blijven spelen.

##### Premium passen

Een * premium pas*  is een variant van een seizoenpas waarvoor spelers moeten betalen om toegang te krijgen. De prijs van de pas wordt bepaald door de ontwikkelaar, maar moet de waarde van de beloningen nauwkeurig prijzen ten opzichte van de kosten van de pas. Premium passen bieden over het algemeen extra missies en de mogelijkheid om grotere beloningen te verdienen.

![](https://prod.docsiteassets.roblox.com/assets/game-design/season-pass-design/season-pass-design-8.png) Premium seizoenpas in * Jailbreak*

Als gratis spelers halverwege het seizoen upgraden naar de premium pas, is het goed om alle premium beloningen voor niveaus die ze al hebben voltooid toe te kennen, zodat ze de volledige waarde uit de pas halen en niet worden gestraft voor het wachten.

### [Toekomstige updates](#toekomstige-updates)[](#toekomstige-updates)

Bij het ontwerpen van een nieuw systeem is het noodzakelijk om na te denken over hoe het in de toekomst zal worden ondersteund en verbeterd. Om je seizoenpas relevant en spannend te houden voor spelers op de lange termijn, overweeg het volgende:

-

Introduceer nieuwe missies: Terwijl je een nieuwe functie aan je ervaring toevoegt, voeg nieuwe missies toe die deze gebruiken. Dit verhoogt de variëteit aan missies en helpt spelers om zich met de nieuwe functie bezig te houden door hun interactie te belonen.

-

Vorm coöperatieve missies: Laat spelers teams vormen, waarbij elk lid bijdraagt aan de collectieve voortgang. Dit sociale component verfrist het systeem, waardoor een samenwerkende omgeving ontstaat om gedeelde doelen te bereiken.

-

Implementeer een inhaalmethode: Bied dubbele XP in de laatste week van het seizoen, waardoor achteroplopende spelers de kans krijgen om in te halen. Deze functie erkent de uitdaging om het seizoen op tijd af te ronden en toont je toewijding aan het succes van spelers.

-

Rol wekelijkse missies uit: Geef spelers uitdagende, hoogbelonende missies eens per week naast hun dagelijkse taken. Deze missies bieden hoogvliegers meer wekelijkse activiteiten en extra XP, waarmee hun toewijding en inspanning wordt erkend.

## [Missies ontwerpen](#missies-ontwerpen)[](#missies-ontwerpen)

* Missieontwerp*  is de zorgvuldige constructie van seizoenpasmissies om de betrokkenheid en retentie van spelers te maximaliseren, rekening houdend met [missiecategorieën](#missiecategorie%C3%ABn) , [missiedifficulty](#missiedifficulty) , [missieoppervlak](#missieoppervlak) . Kernprincipes van effectief missieontwerp omvatten:

-

Nieuwe missies worden dagelijks ontgrendeld. Dit moedigt dagelijkse betrokkenheid van spelers aan en voorkomt dat zeer betrokken spelers de content van het seizoen te snel consumeren.

-

Missies worden dagelijks gereset. Spelers voltooien ze of verliezen hun voortgang aan het einde van de dag.

-

Missies variëren in categorie. Dit zorgt voor gameplayvariëteit binnen de set missies van elke dag.

-

Missies variëren in moeilijkheid. Missies variëren van gemakkelijk, tot gemiddeld, tot moeilijk, om opties te bieden voor zowel casual als hoger presterende spelers.

-

Missies herhalen zich zelden. Heb zoveel mogelijk unieke missies. Als je niet met een grote variëteit begint, overweeg dan om in toekomstige updates meer toe te voegen.

-

Missies vereisen nooit het uitgeven van harde valuta. Dit zou gratis spelers uitsluiten en premium seizoenpas spelers dwingen om nog meer uit te geven.

-

Gratis spelers ontvangen elke dag een aantal missies.

-

Premium pas houders ontvangen elke dag bonusmissies. Deze extra missies zijn zichtbaar voor iedereen, maar zijn alleen te voltooien door premium pas houders. Deze extra kansen om XP te verdienen en de gemakkelijkere moeilijkheidsgraad om de beloningen van het seizoen te voltooien is een belangrijk verkoopargument van de premium pas.

### [Missiecategorieën](#missiecategorieën)[](#missiecategorieën)

Het afleiden van * missiecategorieën*  uit de verschillende activiteiten in je ervaring is een gemakkelijke manier om ervoor te zorgen dat je spelers een verscheidenheid aan taken toewijst. Deze kunnen omvatten:

-

Verkenning: een vereiste afstand afleggen, naar herkenningspunten reizen of geheime gebieden vinden.

-

Verzameling: items in een verzameling toevoegen, verhandelen of opwaarderen.

-

Gevecht: vechten tegen andere spelers of NPC's.

-

Sociaal: een feest geven, lid worden van een team of deelnemen aan een multiplayer mini-game.

-

Aanpassing: een avatar, huisdier of huis aanpassen.

-

Overleven: voorraden verzamelen, vallen zetten of overleven tot het einde van de wedstrijd.

![](https://prod.docsiteassets.roblox.com/assets/game-design/season-pass-design/season-pass-design-13.png)  Dagelijkse Missies van * Jailbreak*

![](https://prod.docsiteassets.roblox.com/assets/game-design/season-pass-design/season-pass-design-14.png)  Dagelijkse missies van * Dragon Adventures*

De categorieën van je ervaring kunnen er heel anders uitzien, afhankelijk van de systemen die je beschikbaar hebt. Houd de categorieën breed genoeg om meerdere activiteiten te omvatten, met als doel om ten minste drie over je hele ervaring te hebben.

### [Missiedifficulty](#missiedifficulty)[](#missiedifficulty)

Bij het presenteren van spelers met meerdere missies en een tijdslimiet voor het voltooien ervan, is het belangrijk om rekening te houden met de moeilijkheid van de taken. Moeilijkheid kan voortkomen uit de hoeveelheid die nodig is om een missie te voltooien, evenals de taken zelf. Bijvoorbeeld, het eten van 5 bessen is gemakkelijker dan het eten van 25 bessen, en gevechten zijn waarschijnlijk moeilijker dan het besturen van een auto.

Net als bij categorieën kun je gemakkelijke, gemiddelde en moeilijke moeilijkheden toekennen aan taken en die informatie gebruiken om spelers een haalbare set missies voor het seizoen te bieden.

-

Gemakkelijk:  zeer snel te voltooien.

-

Gemiddeld:  de basis moeilijkheid.

-

Moeilijk:  vereist meer inspanning of vaardigheid om te voltooien.

![](https://prod.docsiteassets.roblox.com/assets/game-design/season-pass-design/season-pass-design-9.png)  Dagelijkse missies van * Dragon Adventures*

![](https://prod.docsiteassets.roblox.com/assets/game-design/season-pass-design/season-pass-design-10.png)  Wekelijkse missies van * Dragon Adventures*

Moeilijkheidsaanduidingen helpen je ook om de juiste hoeveelheid XP te bepalen die voor het voltooien van elke missie moet worden toegekend, evenals om de algehele moeilijkheid van je niveaus in balans te houden. Aangezien deze missies bedoeld zijn om binnen een dag te worden voltooid, is het belangrijk om ze niet te moeilijk te maken. Als spelers regelmatig falen in het voltooien van hun missies, neemt hun interesse in de seizoenpasfunctie vaak af. Zorg ervoor dat je spelers wat tijd laat om te spelen zoals ze willen, en om de dingen te doen die ze al leuk vinden in de ervaring.

### [Missieoppervlak](#missieoppervlak)[](#missieoppervlak)

Oppervlak  is de handeling van het zeer zichtbaar maken van een specifiek deel van je ervaring voor je spelers om ontdekbaarheid en betrokkenheid te bevorderen. Wanneer je een nieuw systeem aan je ervaring toevoegt, zorg ervoor dat je alles doet wat je kunt om het te surface. Het hebben van je seizoenpas in het zicht zorgt ervoor dat je spelers zich ervan bewust zijn en ermee omgaan zoals je bedoelt.

![](https://prod.docsiteassets.roblox.com/assets/game-design/season-pass-design/season-pass-design-12.png)  Seizoenpas HUD oppervlak in * Dragon Adventures*

Oppervlakmethoden omvatten:

-

Het maken van je knoppen voor de functie zeer zichtbaar door groot en kleurrijk te zijn.

-

Het zeer zichtbaar maken van de timer voor de duur van het evenement om een gevoel van urgentie te creëren.

-

Het bijwerken van je menu en HUD met graphics die het thema en de beloningen van het huidige seizoen benadrukken.

-

Het toevoegen van een korte boodschap of tutorial de eerste keer dat een speler inlogt nadat het systeem is geactiveerd, die hen waarschuwt voor eventuele wijzigingen.

-

Het toevoegen van een badge aan een knop wanneer er een update is die de speler moet weten. Badges kunnen de aandacht van een speler trekken, waardoor ze weten dat ze nieuwe of voltooide missies hebben, of tier beloningen om te verzamelen.

-

Het creëren van een prijsuitstalling in de wereld om beloningen te tonen. Beloningen in de wereld plaatsen stelt spelers in staat om ze nog meer te waarderen en motiveert hen om het seizoen te voltooien.

## [Effectief samenwerken](#effectief-samenwerken)[](#effectief-samenwerken)

Effectieve samenwerking tussen teams is essentieel bij het creëren van ver reikende en impactvolle systemen en content zoals seizoenpassen. De volgende samenwerkingsmethoden zorgen voor duidelijke communicatie en helpen teams om op één lijn te blijven en gemotiveerd te blijven:

-

Asset aanvragen

-

Tech aanvragen

#### Asset aanvragen

Een * asset aanvraag*  is een formeel document tussen teamleden waarin de behoefte aan specifieke assets voor een functie wordt vermeld. Het opsommen van de in-game assets die nodig zijn om een functie te verzenden, maakt het veel gemakkelijker om je middelen te scopen en toe te wijzen. Zorg ervoor dat je elk asset afzonderlijk opsplitst, zodat de volledige reikwijdte van het werk duidelijk is. Het visuele uiterlijk van het item is op dit moment niet belangrijk, het is voldoende om te weten wat voor soort en hoeveel van een asset je ervaring nodig heeft.

Een assettype is ofwel * evergreen* , dat slechts één keer hoeft te worden gemaakt, of * nieuw elk seizoen* . Een asset aanvraag kan er als volgt uitzien:

Evergreen:

-

Seizoen UI-scherm.

-

Missiescherm.

-

Pictogrammen voor elk type missie, zoals sterren, driehoeken of harten.

Nieuw Elk Seizoen:

-

Laatste niveau beloningsitem.

-

Themed marketing assets voor elk seizoen.

#### Tech aanvragen

Een * tech aanvraag*  is een formeel document tussen de coder die aan de functie zal werken om de reikwijdte van het werk te helpen definiëren. Tijdens tech aanvragen, houd rekening met mogelijke onverwachte uitdagingen of problemen in de ontwikkeling.

Een tech aanvraag kan er als volgt uitzien:

-

Een lijst van de data hooks die de voortgang van de speler in elke missie volgen.

-

Implementatie van seizoens UI.

-

Implementatie van seizoens voortgang tracking.

## [Bronnen](#bronnen)[](#bronnen)

Voor meer informatie over seizoenpassen, zie de volgende bronnen:

-

[Generiek seizoenpas systeem PDF](https://prod.docsiteassets.roblox.com/assets/game-design/season-pass-design/season-pass-design.pdf)

-

[Seizoenpas niveau balans calculator](https://prod.docsiteassets.roblox.com/assets/game-design/season-pass-design/season-pass-spreadsheet-.xlsx)

-

[Seizoenpas UI wireframes](https://prod.docsiteassets.roblox.com/assets/game-design/season-pass-design/season-pass-ui.pdf)

#### Voorbeeldmissies

Het volgende is een lijst van potentiële missietypes en taken die zijn gekozen om de variëteit binnen een gegeven categorie te illustreren. Hoewel moeilijkheid subjectief is ten opzichte van de eenvoud van het voltooien van de taak een enkele keer, neemt de moeilijkheid in het onderstaande voorbeeld toe naarmate de hoeveelheid (X)  toeneemt.

| Missiecategorie | | Taak | | Moeilijkheid | | Opmerkingen |
| --- | --- |
| WERK | | Voltooi (X)  banen | | Gemakkelijk | | Spelers kunnen elke baan kiezen |
| WERK | | Verdien (X)  dollars | | Gemiddeld | | Spelers moeten een vereiste hoeveelheid geld verdienen via banen of andere middelen |
| WERK | | Vervul (X)  bestellingen als Barista | | Moeilijk | | Bijna dezelfde missie als hierboven, maar voor een specifieke baan -- wat het moeilijker maakt om te voltooien |
| SOCIAAL | | Geef of woon (X)  feesten bij | | Gemakkelijk | | Dit vereist geen andere spelers (niemand hoeft op te komen dagen voor het feest dat je geeft), dus het is iets gemakkelijker |
| SOCIAAL | | Doe mee aan (X)  races | | Gemiddeld | | Als de activiteit andere spelers vereist, is het over het algemeen moeilijker dan solo-taken |

#### UI monsters

De UI van je seizoenpas is cruciaal voor het duidelijk communiceren met je spelers. Deze wireframe mockups illustreren één manier waarop deze functie in je ervaring kan worden geïmplementeerd. Het creëren van wireframes zoals deze helpt iedereen in het team om de functie te visualiseren, zorgt ervoor dat de gebruikersinterface consistent blijft van scherm naar scherm, en maakt het uiteindelijk gemakkelijker voor de coder die de UI implementeert.

![](https://prod.docsiteassets.roblox.com/assets/game-design/season-pass-design/season-pass-design-ui1.png) Voorbeeld van de dagelijkse missie UI

![](https://prod.docsiteassets.roblox.com/assets/game-design/season-pass-design/season-pass-design-ui2.png) Voorbeeld van de beloningsniveaus UI

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
