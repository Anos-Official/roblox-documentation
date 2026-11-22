<!-- Source: https://create.roblox.com/docs/nl-nl/production/experiments -->

Experimenten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Analytics](/docs/nl-nl/production/analytics)

# Experimenten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Experimenten  stellen je in staat om A/B-tests in-game en voor matchmaking uit te voeren om de causale impact van wijzigingen in je spel te meten. Je kunt bijvoorbeeld verschillende onboarding-ervaringen aan verschillende spelers tonen en het verschil in speeltijd, retentie en andere belangrijke prestatie-indicatoren meten.

Experimenten zijn uitstekend voor het meten van het volgende:

-

Betrokkenheid - Onboarding-stromen, voortgangssystemen, besturingsschema's, aangepaste matchmaking

-

Monetisatie - Winkelzichtbaarheid en gebruikerservaring, soorten starterspakketten, prijsstelling

 ![Overzicht van de Experiments-pagina op Creator Hub](https://prod.docsiteassets.roblox.com/assets/analytics/configs/experiment-overview.png)

## [Experimenteer met experimenten](#experimenteer-met-experimenten)[](#experimenteer-met-experimenten)

Experimenten komen in twee types:

-

In-game  experimenten stellen je in staat om de impact van verschillende [config-waarden](/docs/nl-nl/production/configs)  te meten.

-

Matchmaking-experimenten  stellen je in staat om de impact van verschillende [aangepaste matchmaking-configuraties](/docs/nl-nl/matchmaking/customize-matchmaking)  te meten. In tegenstelling tot in-game experimenten kun je slechts één matchmaking-experiment tegelijk uitvoeren.

In-game Matchmaking

1.

Als je nog geen [config](/docs/nl-nl/production/configs)  hebt, maak er dan een voor je spel.

2.

Ga naar de [Creator Hub](https://create.roblox.com/dashboard/creations)  Experiments -pagina voor je spel en klik op Create experiment .

3.

Voor Type , kies In-experience .

4.

Geef een naam op voor het experiment.

5.

Voor Metric set , kies de set van metrics die je wilt dat het experiment bijhoudt:

| Metric set | | Wat het bijhoudt |
| --- | --- |
| Default | | Standaard prestatie- en betrokkenheids-[metrics](#metrics)  zoals ARPU, sessietijd en retentie van nieuwe gebruikers. |
| Rewarded Video Earnings | | [Metrics voor beloofde video-advertenties](#metrics-voor-beloofde-video) : opt-in percentage, frequentie, impressies, advertentie-inkomsten en totale inkomsten per gebruiker, plus standaard betrokkenheid, retentie en monetisatie metrics. |
| Custom | | De standaard metrics plus tot drie [aangepaste metrics](#aangepaste-metrics)  die je definieert vanuit je [aangepaste](/docs/nl-nl/production/analytics/custom-events) , [economie](/docs/nl-nl/production/analytics/economy-events)  en [trechter](/docs/nl-nl/production/analytics/funnel-events)  evenementen. |

 ![De Metric set dropdown met de opties Default, Rewarded Video Earnings en Custom](https://prod.docsiteassets.roblox.com/assets/analytics/configs/experiment-metric-set.png)

6.

Geef een doelmetric en geplande duur voor het experiment op. Experimenten duren tussen de 14 en 60 dagen.

Ongeacht wat je kiest als je doelmetric, experimenten volgen alle metrics in de metric set. Als je de Rewarded Video Earnings  metric set kiest, stelt Roblox de doelmetrics voor je in, zodat je alleen de duur hoeft op te geven.

7.

Kies een percentage rollout. Dit getal is het percentage spelers dat je wilt opnemen in het experiment.

Over het algemeen geldt: hoe meer mensen je in een experiment opneemt, hoe beter de gegevens, maar gebruik je oordeel over wat het beste is voor je spel.

Let op het [minimum detecteerbare effect](#best-practices-voor-experimenten) , dat de kleinste verandering in de geselecteerde metric is die het experiment betrouwbaar kan detecteren.

8.

Geef varianten en percentages op.

Varianten zijn alternatieve waarden voor je config. Voor een numerieke config-sleutel bossHealth  met een controlewaarde van 500, kun je een variant van 300 opgeven. Je kunt tot twee varianten  en één controle in een experiment hebben.

Percentages bepalen hoe varianten binnen de experiment rollout  worden toegewezen. Overweeg het volgende voorbeeld:

-

Je kiest een totale rollout van 40%.

-

Je specificeert twee varianten en een 50/50-splitsing tussen hen en de controle.

In dit voorbeeld worden 60% van je gebruikers uitgesloten van het experiment; deze gebruikers ontvangen de controle en hebben geen impact op de experimentresultaten. Ongeveer 20% van je gebruikers ontvangt de controle als onderdeel van het experiment. Nog eens 20% ontvangt de variant. Afhankelijk van je spelersaantal is deze verdeling mogelijk niet groot genoeg om bruikbare resultaten op te leveren.

Bij twijfel raden we eenvoudige 50/50-experimenten aan met één variant en één controle bij grote rollouts. De experimenten zijn gemakkelijker te configureren en de resultaten zijn gemakkelijker te interpreteren.

![Variant-pagina](https://prod.docsiteassets.roblox.com/assets/analytics/configs/experiment-variant.png)

9.

(Optioneel) Richt het experiment op een specifiek publiek zodat alleen bijpassende spelers in aanmerking komen voor inschrijving. Targeting gebruikt dezelfde [spelerattributen als voor voorwaardelijke configs](/docs/nl-nl/production/configs#ondersteunde-attributen) , en je kunt bestaande voorwaarden rechtstreeks van je configs kopiëren. Voor meer informatie, zie [Experimenteer met specifieke doelgroepen](#experimenteer-met-specifieke-doelgroepen) .

![De optionele targetingstap tijdens het maken van een experiment](https://prod.docsiteassets.roblox.com/assets/analytics/configs/experiment-targeting.png)

10.

De laatste stap is het plannen. Je kunt experimenten onmiddellijk starten of ze plannen voor een latere datum en tijd. Nadat je een experiment hebt gepland, kun je de configuratie (duur, rolloutpercentage, varianten, enz.) niet meer wijzigen, maar je kunt het opnieuw plannen.

### [Metrics](#metrics)[](#metrics)

Experimenten volgen al de volgende metrics gedurende de duur van het experiment. Deze metrics worden elke 24 uur bijgewerkt terwijl het experiment draait. Tijdens de eerste 24 uur van je experiment worden Playtime, Payer conversion rate en ARPU ook elke 5 minuten bijgewerkt, zodat je kritieke regressies ([early harm](#vroeg-schadelijke-metrics) ) snel kunt opvangen.

| Metric | | Beschrijving | | Vroeg schadelijk? |
| D1 retentie | | Percentage van nieuwe spelers die na één dag terugkwamen naar je spel. | | Nee |
| D7 retentie | | Percentage van nieuwe spelers die na een week terugkwamen naar je spel. | | Nee |
| Speeltijd | | Gemiddelde tijd die spelers in je spel hebben doorgebracht. Cumulatief voor de duur van het experiment. | | Ja |
| ARPU | | Gemiddelde omzet per gebruiker. Omzet gedeeld door het aantal spelers. Cumulatief voor de duur van het experiment. | | Ja |
| ARPPU | | Gemiddelde omzet per betalende gebruiker. Omzet gedeeld door het aantal spelers die een spelgerelateerd item hebben gekocht. Cumulatief voor de duur van het experiment. | | Nee |
| Payer conversion rate | | Percentage van spelers die een spelgerelateerd item hebben gekocht. Cumulatief voor de duur van het experiment. | | Ja |
| Sessietijd | | Speeltijd gedeeld door het aantal sessies. Cumulatief voor de duur van het experiment. | | Nee |

### [Status van experimenten](#status-van-experimenten)[](#status-van-experimenten)

De Experiments -pagina toont de volgende statussen voor experimenten.

| Status | | Beschrijving |
| Voltooid | | Het experiment is afgelopen, wat gebeurt wanneer je het handmatig stopt, wanneer je een beslissing bereikt, of automatisch kort na de beslissingsdatum (14 dagen na voor in-game, onmiddellijk voor matchmaking). Je kunt de details en resultaten nog steeds bekijken. |
| Beslissing nodig | | Het experiment heeft zijn beslissingsdatum bereikt. Dit is een goed moment om de resultaten te bekijken. |
| Lopend | | Het experiment is aan de gang maar heeft zijn beslissingsdatum nog niet bereikt. |
| Gepland | | Het experiment is gepland om op een toekomstige datum te beginnen. |
| Concept | | Het experiment is nog niet gestart of gepland. Je kunt het instellen. |

## [Aangepaste metrics](#aangepaste-metrics)[](#aangepaste-metrics)

Standaard volgen experimenten topline metrics zoals speeltijd, ARPU en D1 retentie. Deze metrics vertellen je of een wijziging een algehele impact had, maar je wilt misschien ook weten wat er specifiek is veranderd in je spel, zoals of spelers meer of minder geneigd waren om een vaardigheid te gebruiken, een baas te verslaan of de onboarding-stroom te voltooien.

Aangepaste metrics  stellen je in staat om je eigen operationele metrics aan een in-game experiment toe te voegen, opgebouwd uit de [aangepaste evenementen](/docs/nl-nl/production/analytics/custom-events) , [economie evenementen](/docs/nl-nl/production/analytics/economy-events)  en [trechter evenementen](/docs/nl-nl/production/analytics/funnel-events)  die je al logt met [AnalyticsService](/docs/nl-nl/reference/engine/classes/AnalyticsService) . Gebruik ze om:

-

Een vlak resultaat uit te leggen.  D1 retentie is onveranderd, maar de voltooiing van de onboarding-trechter is met 8% gedaald. Je wilt misschien de wijziging niet doorvoeren, of je wilt misschien een andere waarde testen.

-

Toch een rollout rechtvaardigen.  ARPU is vlak, maar de muntenbalansen van betalende gebruikers nemen sneller af, wat de monetisatie in de loop van de tijd zou moeten verbeteren.

-

Een hypothese over je kernloop testen.  Als je gelooft dat meer tijd besteden aan het opnemen van video's leidt tot meer delen en betere retentie, kun je beide in hetzelfde experiment meten.

### [Voordat je begint](#voordat-je-begint)[](#voordat-je-begint)

-

Log eerst je evenementen.  Je bouwt aangepaste metrics op uit evenementen die je spel verzendt, dus je kunt alleen kiezen uit evenementnamen, valuta en trechters die al gegevens hebben. Om ze in te stellen, zie [aangepaste evenementen](/docs/nl-nl/production/analytics/custom-events) , [economie evenementen](/docs/nl-nl/production/analytics/economy-events)  en [trechter evenementen](/docs/nl-nl/production/analytics/funnel-events) .

-

Nieuwe evenementen hebben tijd nodig om te verwerken.  Als je net een evenement hebt toegevoegd, kan het tot 24 uur duren voordat het in het dashboard verschijnt.

### [Voeg aangepaste metrics toe aan een experiment](#voeg-aangepaste-metrics-toe-aan-een-experiment)[](#voeg-aangepaste-metrics-toe-aan-een-experiment)

1.

Ga naar de [Creator Hub](https://create.roblox.com/dashboard/creations)  Experiments -pagina voor je spel, klik op Create experiment  en vul het type en de naam zoals gebruikelijk in.

2.

Voor Metric set , kies Custom .

3.

In de sectie Custom metrics , klik op Add . Om een metric die je voor een vorig experiment hebt gemaakt opnieuw te gebruiken, klik je in plaats daarvan op Add from past experiment .

 ![De Custom metrics-sectie met de knoppen Add en Add from past experiment](https://prod.docsiteassets.roblox.com/assets/analytics/configs/experiment-custom-metrics.png)

4.

Kies een Bron : Custom , Economy  of Funnel .

5.

Kies wat de metric meet: het type aangepast evenement, de valuta of de trechter en de voltooiingsstap.

6.

Kies een Berekening . Voor meer informatie, zie [Kies een berekening](#kies-een-berekening) .

7.

(Optioneel) Voeg Filters  toe om te bepalen welke evenementen meetellen voor de metric.

8.

Controleer de Metric name . Roblox genereert een naam op basis van je keuzes, maar je kunt deze bewerken naar iets dat je team herkent, of deze op elk moment resetten.

 ![Het Add custom metric-paneel met een trechterbron, de Onboarding-trechter, een voltooiingsstap en de per-gebruiker conversieberekening](https://prod.docsiteassets.roblox.com/assets/analytics/configs/experiment-add-custom-metric.png)

9.

Klik op Save . Je kunt tot drie aangepaste metrics toevoegen.

10.

Voor Goal metric , kies de metric die het experiment bepaalt. Je aangepaste metrics verschijnen in deze lijst naast speeltijd en gemiddelde omzet per gebruiker. Het experiment volgt nog steeds elke aangepaste metric die je niet als doelmetric instelt als een leer-metric.

11.

Voltooi het instellen van het experiment zoals gebruikelijk: duur, rolloutpercentage, varianten, targeting en planning.

Nadat een experiment is gestart, kun je de metrics niet meer wijzigen. Definieer ze voordat je het experiment start of plant, en wijzig de manier waarop je spelcode analytics-evenementen verzendt niet terwijl het experiment draait.

### [Kies een berekening](#kies-een-berekening)[](#kies-een-berekening)

Elke berekening telt alleen spelers die zijn ingeschreven voor het experiment en alleen evenementen die tijdens het experiment zijn gelogd. De meeste berekeningen gebruiken een van de twee op spelers gebaseerde noemers:

-

Per alle gebruikers  deelt door iedereen die is ingeschreven in de experimentgroep, inclusief spelers die het evenement nooit hebben geactiveerd. Gebruik deze noemer wanneer je wilt dat de metric zowel weerspiegelt hoe vaak het gedrag voorkomt als hoeveel spelers het überhaupt doen.

-

Per deelnemer  deelt alleen door ingeschreven spelers die het evenement minstens één keer hebben gelogd. Gebruik deze noemer wanneer je de intensiteit onder de spelers die betrokken zijn wilt meten, ongeacht hoeveel spelers betrokken zijn.

De uitzondering is [per-instance funnel conversion](#trechtermetrics) , die deelt door trechterinstanties in plaats van spelers.

#### [Aangepaste evenementmetrics](#aangepaste-evenementmetrics)[](#aangepaste-evenementmetrics)

Selecteer een type aangepast evenement, en vervolgens een van de volgende berekeningen:

| Berekening | | Wat het meet |
| Gemiddelde aangepaste waarde | | Totale waarde van het evenement, gedeeld door het aantal ingeschreven spelers die het minstens één keer hebben gelogd. |
| Gemiddelde aangepaste waarde over alle gebruikers | | Totale waarde van het evenement, gedeeld door alle ingeschreven spelers. |
| Deelname % | | Aandeel van ingeschreven spelers die het evenement minstens één keer hebben gelogd. |

Bijvoorbeeld, stel dat je een nieuwe kruidenverzamelingsloop test. Voeg Gemiddelde aangepaste waarde over alle gebruikers  toe op een HerbsGathered -evenement om te zien of de variant het verzamelen in de hele groep verhoogt, en Deelname %  op hetzelfde evenement om te zien of het spelers aantrekt die het anders zouden negeren.

#### [Economiemetrics](#economiemetrics)[](#economiemetrics)

Selecteer een valuta, en vervolgens een van de volgende berekeningen:

| Berekening | | Wat het meet |
| Gemiddelde netto valuta delta | | Totale bron min totale afvoer, gedeeld door het aantal ingeschreven spelers die minstens één bron- of afvoer-evenement hebben gelogd. |
| Gemiddelde valuta bron delta | | Totale hoeveelheid van bron-evenementen, gedeeld door het aantal ingeschreven spelers die minstens één bron- of afvoer-evenement hebben gelogd. |
| Gemiddelde valuta afvoer delta | | Totale hoeveelheid van afvoer-evenementen, gedeeld door het aantal ingeschreven spelers die minstens één bron- of afvoer-evenement hebben gelogd. |

Om uitgaven aan specifieke delen van je economie te meten, filter je op specifieke transactie typen of item SKU's.

Bijvoorbeeld, stel dat je een nieuw seizoenpas test dat munten geeft als voortgangsbeloningen. Je hebt het zo afgesteld dat het bereiken van de laatste exclusieve prijs op tijd vereist dat spelers munten uitgeven aan gameplay-boosts. Op je muntenvaluta:

-

Gemiddelde valuta afvoer delta  vertelt je of spelers meer uitgeven.

-

Gemiddelde valuta bron delta  vertelt je of spelers meer verdienen.

-

Gemiddelde netto valuta delta  vertelt je of de extra uitgaven genoeg zijn om te voorkomen dat de balansen toenemen.

#### [Trechtermetrics](#trechtermetrics)[](#trechtermetrics)

Selecteer een trechter, vervolgens een voltooiingsstap, en dan een van de volgende berekeningen:

| Berekening | | Wat het meet |
| Per-gebruiker trechter conversie % | | Unieke spelers die de voltooiingsstap hebben bereikt, gedeeld door unieke spelers die een stap hebben gelogd. |
| Per-instance trechter conversie % | | Unieke funnelSessionId -waarden die de voltooiingsstap hebben bereikt, gedeeld door alle funnelSessionId -waarden die een stap hebben gelogd. |

Houd het volgende in gedachten voor trechtermetrics:

-

Je moet een voltooiingsstap kiezen.  Je kunt deze stap niet meer wijzigen nadat het experiment is gestart, dus kies een stap die cruciaal is voor je metric.

-

Eenmalige trechters geven hetzelfde resultaat voor beide berekeningen terug.  Voor [eenmalige trechters](/docs/nl-nl/production/analytics/funnel-events#eenmalige-trechters-volgen) , inclusief de onboarding-trechter, zijn per-gebruiker en per-instance conversie gelijk omdat elke speler slechts één instantie heeft. De berekeningen verschillen alleen voor [terugkerende trechters](/docs/nl-nl/production/analytics/funnel-events#terugkerende-trechters-volgen)  die gebruik maken van funnelSessionId .

-

Terugkerende trechters beantwoorden verschillende vragen.  Per-gebruiker conversie beantwoordt "hoeveel spelers voltooien dit minstens één keer," terwijl per-instance conversie beantwoordt "hoe vaak slaagt een poging." Deze metrics kunnen in tegengestelde richtingen bewegen.

-

Overgeslagen stappen tellen als voltooid.  Als een speler stap 3 logt zonder stap 1 en 2 te loggen, beschouwt de trechter stappen 1 en 2 als voltooid. Herhaalde stappen tellen slechts één keer. Voor meer informatie, zie [Overgeslagen stappen](/docs/nl-nl/production/analytics/funnel-events#overgeslagen-stappen)  en [Herhaalde stappen](/docs/nl-nl/production/analytics/funnel-events#herhaalde-stappen) .

Bijvoorbeeld, stel dat je je tutorial hebt herwerkt. Voeg Per-gebruiker trechter conversie %  toe op de onboarding-trechter met de laatste stap als de voltooiingsstap, en maak het je doelmetric. Controleer vervolgens D1 retentie om te zien of een betere voltooiing daadwerkelijk leidt tot spelers die terugkomen.

### [Voorbeelden van aangepaste metrics](#voorbeelden-van-aangepaste-metrics)[](#voorbeelden-van-aangepaste-metrics)

| Wat je verandert | | Wat je wilt weten | | Metric om toe te voegen |
| Verkort je tutorial van acht stappen naar vijf | | Doen meer nieuwe spelers de tutorial af? | | Trechter : onboarding, per-gebruiker conversie % met de laatste stap als voltooiing |
| Voeg een dagelijkse quests-knop toe aan het hoofdmenu | | Doen meer spelers mee aan dagelijkse quests? | | Aangepast : deelname % op QuestStarted |
| Verlaag de prijs van de snelheid boost van 100 naar 50 munten | | Doen spelers meer munten uitgeven in de winkel? | | Economie : munten, gemiddelde afvoer delta, gefilterd op de snelheid boost item SKU |
| Verdubbel de munten van dagelijkse inlogbeloningen | | Sparen spelers te veel munten? | | Economie : munten, gemiddelde netto delta (munten verdiend min munten uitgegeven) |

### [Lees resultaten van aangepaste metrics](#lees-resultaten-van-aangepaste-metrics)[](#lees-resultaten-van-aangepaste-metrics)

Experimentmetrics zijn cumulatief, maar [analytics](/docs/nl-nl/production/analytics)  dashboards zijn dagelijks. Een experimentmetric telt de hele experimentperiode op en, waar de noemer spelers zijn, telt elke speler slechts één keer. Analytics-pagina's hebben standaard een dagelijkse weergave, zodat hetzelfde onderliggende evenement verschillende cijfers in de twee plaatsen kan opleveren. Gebruik analytics om je evenementen te verkennen en te valideren dat ze correct worden geactiveerd, en gebruik de experimentresultaten om varianten met de controle te vergelijken.

Wanneer je aangepaste metrics interpreteert, houd dan het volgende in gedachten:

-

Een aangepaste metric die beweegt zonder een topline metric is informatie, geen ruis.  Het betekent meestal dat de wijziging mechanisch werkte, maar nog geen statistisch significante impact heeft gehad op retentie of omzet, of dat het dat nooit zal doen.

-

Richting is niet altijd goed nieuws.  Een daling in winpercentages kan precies zijn wat je wilde als je meer uitdagingen voor gevestigde spelers hebt toegevoegd. Beslis voordat het experiment begint welke richting als een overwinning telt.

-

Statistische significantie is nog steeds van toepassing.  Aangepaste metrics zijn onderhevig aan dezelfde steekproefgroottebeperkingen als elke andere metric. Als een wijziging niet statistisch significant is, moet je er niet op handelen.

-

Overdrijf niet één metric.  Als je doelmetric omhoog is, maar een leer-metric significant omlaag, heb je een afweging te maken, geen duidelijke overwinning.

## [Metrics voor beloofde video](#metrics-voor-beloofde-video)[](#metrics-voor-beloofde-video)

[Beloofde video-advertenties](/docs/nl-nl/production/promotion/rewarded-video-ads)  kunnen je helpen meer te verdienen met je spel, ook van spelers die geen Robux uitgeven. Je moet echter de plaatsing van beloofde video-advertenties afstemmen op je spel en de economie ervan. Waar je de advertentie plaatst en welke items je spelers beloont, beïnvloedt zowel de advertentie-inkomsten als de betrokkenheid.

De Rewarded Video Earnings  metric set volgt de advertentieprestaties naast een selectie van standaard betrokkenheid, retentie en monetisatie metrics, zodat je kunt controleren of het draaien van advertenties de rest van je spel niet schaadt. Gebruik het om:

-

Een beloofde advertentie af te stemmen.  Test een grotere beloning of een andere plaatsing, en controleer of het opt-in percentage en de frequentie toenemen.

-

Controleer de afweging.  Als de advertentie-inkomsten toenemen, controleer dan of de speeltijd, retentie of payer conversion is gedaald. Totale inkomsten per gebruiker tonen het gecombineerde effect van advertenties en microtransacties.

-

Bereik spelers die niet betalen.  Test of een advertentieoptie inkomsten genereert van spelers die geen aankoop hebben gedaan, zonder te verlagen wat je betalende gebruikers uitgeven.

### [Stel een experiment voor beloofde video-inkomsten in](#stel-een-experiment-voor-beloofde-video-inkomsten-in)[](#stel-een-experiment-voor-beloofde-video-inkomsten-in)

Beloofde video-experimenten zijn in-game experimenten, dus ze werken zoals elk ander in-game experiment. Je controleert de advertentiefunctie, zoals de beloningsgrootte of advertentiefrequentie, met een [config](/docs/nl-nl/production/configs) . Elke variant heeft een andere config-waarde, en je code leest de waarde met [ConfigService:GetConfigForPlayerAsync()](/docs/nl-nl/reference/engine/classes/ConfigService#GetConfigForPlayerAsync) . Voor meer informatie, zie [Voeg experimenten toe aan je code](#voeg-experimenten-toe-aan-je-code) .

1.

Als je nog geen config hebt voor de beloofde video-advertentie die je wilt testen, maak er dan een. Maak bijvoorbeeld een numerieke config-sleutel adCooldownSeconds  met je huidige cooldown-tijd als controlewaarde.

2.

Ga naar de [Creator Hub](https://create.roblox.com/dashboard/creations)  Experiments -pagina voor je spel en klik op Create experiment .

3.

Voor Type , kies In-experience .

4.

Voor Metric set , kies Rewarded Video Earnings . Roblox stelt impressies per gebruiker en totale inkomsten per gebruiker in als de doelmetrics, zodat je er geen hoeft te kiezen.

 ![Een in-experience experiment met de Rewarded Video Earnings metric set geselecteerd](https://prod.docsiteassets.roblox.com/assets/analytics/configs/experiment-rewarded-video.png)

5.

Voltooi het instellen van het experiment zoals gebruikelijk: duur, rolloutpercentage, varianten, targeting en planning.

### [Metrics voor beloofde video-inkomsten](#metrics-voor-beloofde-video-inkomsten)[](#metrics-voor-beloofde-video-inkomsten)

De Rewarded Video Earnings  metric set volgt de volgende advertentiemetrics, plus een selectie van de standaard [metrics](#metrics)  zodat je kunt controleren of advertenties de betrokkenheid, retentie of monetisatie niet schaden.

| Metric | | Beschrijving |
| Totale inkomsten per gebruiker | | Inkomsten per speler uit beloofde video-advertenties en microtransacties (ontwikkelaarsproducten, passen, privéservers en betaalde toegang). Cumulatief voor de duur van het experiment. |
| Impressies per gebruiker | | Advertentie-impressies per speler. Cumulatief voor de duur van het experiment. |
| Opt-in percentage | | Percentage van in aanmerking komende spelers die minstens één advertentie hebben bekeken. |
| Frequentie | | Advertentie-impressies gedeeld door unieke kijkers. |
| Advertentie-inkomsten per gebruiker | | Inkomsten per speler uit beloofde video-advertenties. Cumulatief voor de duur van het experiment. |

## [Experimenteer met specifieke doelgroepen](#experimenteer-met-specifieke-doelgroepen)[](#experimenteer-met-specifieke-doelgroepen)

Standaard kan een in-game experiment elke speler inschrijven in je rolloutpercentage. Targeting  stelt je in staat om het experiment op een specifieke doelgroep uit te voeren, zoals spelers in bepaalde landen, specifieke tijdsvensters of actieve spenderniveaus. Deze attributen bepalen wie het experiment kan betreden. Targeting gebruikt dezelfde attributen als [config-targeting](/docs/nl-nl/production/configs#target-configuraties-naar-specifieke-spelers) .

In nieuwere experimenten, als een getarget attribuut verandert nadat een speler zich heeft ingeschreven, verwijdert Roblox ze niet uit het experiment. Om te zien op welke experimenten dit van toepassing is, zie [Per-sessie evaluatie](#per-sessie-evaluatie) .

Targeting is alleen van toepassing op in-game experimenten.

### [Stel gerichte experimenten in](#stel-gerichte-experimenten-in)[](#stel-gerichte-experimenten-in)

Je configureert targetingcriteria wanneer je [het experiment maakt](#experimenteer-met-experimenten) . Nadat het experiment is gestart, kun je de targetingregels, de controlewaarde, de varianten of enige voorwaardelijke regels die de config-sleutel gebruikt niet meer wijzigen.

Je kunt bestaande voorwaardelijke regels uit je configs hergebruiken om je targeting te definiëren, maar het experiment slaat een onafhankelijke kopie  van elke regel op. Het bewerken of verwijderen van de oorspronkelijke config-voorwaarde later heeft geen effect op de targeting van het experiment.

Omdat het verkleinen van je publiek je steekproefgrootte vermindert, werkt Roblox het [minimum detecteerbare effect (MDE)](#best-practices-voor-experimenten)  bij met een schatting van het publiek dat aan je targetingcriteria voldoet. Zorg ervoor dat je getargete publiek groot genoeg is om statistisch significante resultaten te produceren.

### [Hoe Roblox getargete waarden oplost](#hoe-roblox-getargete-waarden-oplost)[](#hoe-roblox-getargete-waarden-oplost)

Roblox evalueert experimenten eerst , voordat enige regels van standaard voorwaardelijke configs. Wanneer een config-sleutel een actief experiment heeft, lost Roblox de waarde in deze volgorde op. Deze resolutie is van toepassing op experimenten die na 17 november 2026 beginnen; voor eerdere experimenten, zie [Per-sessie evaluatie](#per-sessie-evaluatie) .

1.

Als de speler al is ingeschreven voor het experiment, ontvangt hij zijn toegewezen experimentwaarde (controle of variant), zelfs als hij niet meer aan de targetingcriteria voldoet.

2.

Als de speler niet is ingeschreven, controleert Roblox hen tegen de targetingcriteria. Als ze overeenkomen en binnen de rollout vallen, schrijft Roblox hen in en wijst een experimentwaarde toe.

3.

De eerste overeenkomende config-voorwaarde.

4.

Alle daaropvolgende overeenkomende config-voorwaarden.

5.

De standaardwaarde.

Spelers in de controlegroep ontvangen de waarde die je bestaande configregels produceren. Je kunt niet meer dan één actief experiment op dezelfde config-sleutel tegelijk uitvoeren.

Bijvoorbeeld, stel dat je een nieuwe tutorial test en alleen nieuwe gebruikers target. Een speler bezoekt je ervaring voor de eerste keer op maandag, wordt ingeschreven en krijgt de nieuwe tutorial. Op woensdag komen ze terug. Ze zijn nu een terugkerende gebruiker, maar ze zijn nog steeds in het experiment en zien nog steeds de nieuwe tutorial.

### [Per-sessie evaluatie](#per-sessie-evaluatie)[](#per-sessie-evaluatie)

Voor experimenten die na 17 november 2026 beginnen, is targeting een toegangscontrole : het bepaalt of een speler kan worden ingeschreven, niet of ze ingeschreven blijven.

Zodra een speler zich inschrijft voor een van deze experimenten, behoudt hij zijn toewijzing (controle of variant) over sessies voor de rest van het experiment, zelfs als ze later niet meer aan je targetingcriteria voldoen.

Voor experimenten die op of vóór die datum zijn gestart, evalueert Roblox targetingattributen per sessie , zodat de geschiktheid van een individuele speler in de loop van de tijd kan veranderen. Als een speler tijdens een sessie aan je targetingcriteria voldoet, kan hij zich inschrijven en een experimentvariant ontvangen. Als ze later niet meer overeenkomen in een latere sessie, ontvangen ze de experimentwaarde niet meer en vallen ze onmiddellijk terug op je standaard configregels. Als je experiment continuïteit nodig heeft die verder gaat dan geschiktheid—bijvoorbeeld een multi-sessie onboarding-stroom gericht op nieuwe spelers—bewaar dan de waarde zelf, bijvoorbeeld in een [data store](/docs/nl-nl/cloud-services/data-stores) .

De gegevens van een speler blijven toegeschreven aan de variant (of controle) waarin ze zijn ingeschreven, zelfs als ze later niet meer aan de criteria voldoen. Bijvoorbeeld, D7 retentie telt nog steeds een speler die zich op dag 0 heeft ingeschreven en of ze op dag 7 zijn teruggekomen, zelfs als ze op dag 4 niet meer kwalificeren. Voor experimenten die na die datum beginnen, blijft de speler ook de toewijzing zien die deze metrics meten.

### [Config-wijzigingen terwijl een experiment draait](#config-wijzigingen-terwijl-een-experiment-draait)[](#config-wijzigingen-terwijl-een-experiment-draait)

Om configuratiedrift en beschadigde experimentgegevens te voorkomen, vergrendelt Roblox de config-sleutel  op het moment dat een experiment begint te draaien:

-

Je kunt de draaiende config-sleutel niet bewerken of verwijderen, noch kun je de standaard voorwaardelijke waarden ervan wijzigen.

-

Alle globale voorwaarden waar de actieve config naar verwijst, zijn ook vergrendeld. Je kunt ze niet bewerken, verwijderen of opnieuw ordenen ten opzichte van elkaar.

De vergrendeling wordt opgeheven wanneer het experiment is voltooid.

## [Voeg experimenten toe aan je code](#voeg-experimenten-toe-aan-je-code)[](#voeg-experimenten-toe-aan-je-code)

Deze sectie is alleen van toepassing op in-game experimenten. Matchmaking-experimenten vereisen geen codewijzigingen.

Het toepassen van in-game experimenten is vergelijkbaar met [het toepassen van configs](/docs/nl-nl/production/configs#voeg-configuraties-toe-aan-je-code) . Het belangrijkste verschil is het gebruik van [ConfigService:GetConfigForPlayerAsync()](/docs/nl-nl/reference/engine/classes/ConfigService#GetConfigForPlayerAsync)  in plaats van [ConfigService:GetConfigAsync()](/docs/nl-nl/reference/engine/classes/ConfigService#GetConfigAsync) .

[GetConfigForPlayerAsync()](/docs/nl-nl/reference/engine/classes/ConfigService#GetConfigForPlayerAsync)  haalt een speler-specifieke snapshot op. Wanneer je [GetValue()](/docs/nl-nl/reference/engine/classes/ConfigSnapshot#GetValue)  aanroept, controleert de snapshot op een actief experiment en schrijft de gebruiker in (of niet) op basis van het rolloutpercentage.

```

local ConfigService = game:GetService("ConfigService")

local Players = game:GetService("Players")

local function onPlayerAdded(player)

    local playerConfig = ConfigService:GetConfigForPlayerAsync(player)

    local leaderboardColor = playerConfig:GetValue("leaderboardColor")

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

-

Je moet [GetConfigForPlayerAsync()](/docs/nl-nl/reference/engine/classes/ConfigService#GetConfigForPlayerAsync)  afzonderlijk aanroepen voor elke speler; [GetConfigAsync()](/docs/nl-nl/reference/engine/classes/ConfigService#GetConfigAsync)  past geen experimenten toe.

-

Nadat je [GetValue()](/docs/nl-nl/reference/engine/classes/ConfigSnapshot#GetValue)  op een speler-specifieke snapshot hebt aangeroepen, is de speler die aan de snapshot is gekoppeld ingeschreven in het experiment voor die sleutel en die sleutel alleen. Alle volgende aanroepen naar de methode retourneren dezelfde controle of variant voor de duur van het experiment. Voor experimenten die na 17 november 2026 beginnen, geldt dit over sessies, zelfs nadat een getarget attribuut verandert. Voor eerdere getargete experimenten, zie [Per-sessie evaluatie](#per-sessie-evaluatie) . De eerste aanroep is nog steeds de enige willekeurige aanroep, en het is nog steeds wat de speler inschrijft.

Wacht met het aanroepen van [GetValue()](/docs/nl-nl/reference/engine/classes/ConfigSnapshot#GetValue)  totdat je het nodig hebt. Te vroeg aanroepen van [GetValue()](/docs/nl-nl/reference/engine/classes/ConfigSnapshot#GetValue)  kan ervoor zorgen dat je spelers inschrijft die nooit interactie hebben met het deel van het spel waar je op experimenteert.

-

Inschrijving voor experimenten is niet beperkt tot nieuwe gebruikers. Zelfs als een gebruiker eerder een waarde van [GetConfigAsync()](/docs/nl-nl/reference/engine/classes/ConfigService#GetConfigAsync)  heeft ontvangen, kun je ze nog steeds inschrijven in een experiment met een speler-specifieke snapshot van [GetConfigForPlayerAsync()](/docs/nl-nl/reference/engine/classes/ConfigService#GetConfigForPlayerAsync) .

-

Als een sleutel in een speler-specifieke snapshot geen actief experiment heeft, retourneert [GetValue()](/docs/nl-nl/reference/engine/classes/ConfigSnapshot#GetValue)  de standaard configwaarde (of nil als het geen waarde heeft).

### [Aangepaste inschrijving](#aangepaste-inschrijving)[](#aangepaste-inschrijving)

Om spelers te targeten op basis van attributen zoals land, anciënniteit of betaalstatus, gebruik je in plaats daarvan [experiment-targeting](#experimenteer-met-specifieke-doelgroepen) . De aanpak in deze sectie is voor in-game status, zoals hoe ver een speler is gevorderd.

Als je alleen spelers wilt inschrijven die voldoen aan criteria op basis van in-game status, moet je extra code schrijven om die criteria te controleren en pas dan [GetValue()](/docs/nl-nl/reference/engine/classes/ConfigSnapshot#GetValue)  aanroepen om ze in het experiment in te schrijven. Overweeg het volgende voorbeeld:

-

Je wilt een nieuw besturingsschema testen in je racegame.

-

Het schema is voor gevorderde spelers, dus je wilt spelers targeten die een groot aantal races hebben gewonnen.

Je code zou er ongeveer zo uit kunnen zien:

```

local function getControlScheme(player, racesWon)

    if racesWon < 20 then

        return "standardScheme"

    else

        -- Speler heeft veel overwinningen, schrijf in voor experiment

        local playerConfigSnapshot = ConfigService:GetConfigForPlayerAsync(player)

        if playerConfigSnapshot:GetValue("useNewControlScheme") then

            return "newScheme"

        else

            return "standardScheme"

        end

    end

end

```

Een aangepaste in-game poort zoals racesWon  is anders dan [experiment-targeting](#experimenteer-met-specifieke-doelgroepen) . Sticky inschrijving heeft alleen effect zodra je [GetValue()](/docs/nl-nl/reference/engine/classes/ConfigSnapshot#GetValue)  aanroept. Omdat dit script [GetValue()](/docs/nl-nl/reference/engine/classes/ConfigSnapshot#GetValue)  alleen aanroept terwijl de in-game voorwaarde geldt, wordt een speler die niet aan de voorwaarde voldoet nooit ingeschreven, zodat sticky inschrijving nooit op hen van toepassing is. Voor experimenten die na 17 november 2026 beginnen, zal de experimentwaarde niet vanzelf verdwijnen zodra een speler is ingeschreven. Als je een eenmalig oppervlak hebt dat alleen moet draaien terwijl de speler nog aan de voorwaarde voldoet, zoals een pop-up die alleen moet verschijnen terwijl een speler nieuw is, houd dan je eigen controle rond dat oppervlak in plaats van te vertrouwen op de experimentwaarde om uit te schakelen.

## [Bekijk en interpreteer resultaten](#bekijk-en-interpreteer-resultaten)[](#bekijk-en-interpreteer-resultaten)

Klik op View  om details en resultaten te zien. In het tabblad Details And Progress  kun je het totale aantal ingeschreven spelers zien, evenals het aantal spelers dat de controlewaarde en elke variant heeft ontvangen. Deze pagina vroeg in het experiment bekijken is nuttig om ervoor te zorgen dat het experiment goed draait, niet  om actie te ondernemen. Voordat je actie onderneemt, zie [Best practices](#best-practices-voor-experimenten) .

![De details pagina voor een experiment](https://prod.docsiteassets.roblox.com/assets/analytics/configs/experiment-details.png)

### [Vroeg schadelijke metrics](#vroeg-schadelijke-metrics)[](#vroeg-schadelijke-metrics)

Voor de eerste 24 uur, of totdat de eerste dagelijkse resultaten binnenkomen, worden vroeg schadelijke [metrics](#metrics)  elke 5 minuten bijgewerkt, zodat je onbedoelde kritieke schade vroeg kunt opvangen. Klik op Metrics  om deze resultaten te zien. Zoek naar kritisch schadelijke metrics die in het rood zijn gemarkeerd.

Beweeg over een metric en klik op View confidence  om het betrouwbaarheidsinterval te zien.

![Vroeg schadelijke resultaten voor een experiment](https://prod.docsiteassets.roblox.com/assets/analytics/configs/experiment-ehd-results.png)

Tijdens dit venster testen resultaten alleen op schade, dus het betrouwbaarheidsinterval heeft geen ondergrens, alleen een bovengrens. Een metric wordt als kritisch schadelijk gemarkeerd als het hele betrouwbaarheidsinterval onder de kritieke schadegrens valt. In het volgende voorbeeld is de speeltijd -12,67% met een bovengrens van -2,73%. Hoewel de schatting lager is dan de kritieke schadegrens van -10% en het hele betrouwbaarheidsinterval onder 0% ligt, wordt de metric niet geclassificeerd als kritisch schadelijk omdat het interval niet volledig onder de schadegrens ligt.

![Betrouwbaarheidsinterval voor een vroeg schadelijke metric](https://prod.docsiteassets.roblox.com/assets/analytics/configs/experiment-ehd-confidence.png)

Gebruik deze resultaten alleen om vroege stopbeslissingen in de eerste 24 uur te begeleiden. Gebruik ze niet  voor lanceerbeslissingen, vertrouw in plaats daarvan op [dagelijkse resultaten](#dagelijkse-resultaten) .

### [Vroeg schadelijke drempels](#vroeg-schadelijke-drempels)[](#vroeg-schadelijke-drempels)

Elke metric heeft zijn eigen vroeg schadelijke drempel. Als de lift van een variant onder deze drempel valt, wordt deze geclassificeerd als kritisch schadelijk voor die metric. Voor vergelijkingen van metric-varianten met minder dan 10.000 ingeschreven spelers over de variant en de controle worden variantliften weergegeven, maar beslissingen over schade worden pas genomen wanneer de steekproefgrootte voldoende gegevens biedt om schade betrouwbaar te detecteren.

| Metric | | Vroeg schadelijke drempel |
| Speeltijd | | -10% |
| ARPU | | -20% |
| Payer conversion rate | | -20% |

### [Vroeg schadelijke meldingen](#vroeg-schadelijke-meldingen)[](#vroeg-schadelijke-meldingen)

Als er kritieke schade wordt gedetecteerd in je experiment tijdens de vroeg schadelijke analyseperiode, wordt er een melding verzonden naar de spel eigenaar en experiment eigenaar voor vroege actie. Meldingen worden verzonden via e-mail, Creator Hub-meldingspaneel en via een optionele [webhook](/docs/nl-nl/cloud/webhooks/webhook-notifications) . Na ontvangst van een vroeg schadelijke melding moet je de experimentmetrics bekijken en beslissen of het experiment vroeg moet worden gestopt.

![Vroeg schadelijke melding in de creator hub](https://prod.docsiteassets.roblox.com/assets/analytics/configs/experiment-ehd-notification.png)

### [Dagelijkse resultaten](#dagelijkse-resultaten)[](#dagelijkse-resultaten)

Nadat een experiment minstens 24 uur heeft gedraaid, klik je op Results  om de laatste resultaten te zien, die elke 24 uur worden bijgewerkt. Zoek naar statistisch significante veranderingen in doelmetrics, die het dashboard in het groen of rood markeert. Deze veranderingen zijn waarschijnlijker om de impact van je variant te tonen en minder waarschijnlijk om valse positieven of negatieven te zijn.

![De details pagina voor een experiment](https://prod.docsiteassets.roblox.com/assets/analytics/configs/experiment-results.png)

Een metric is statistisch significant wanneer het betrouwbaarheidsinterval voor de procentuele verandering niet overlapt met 0%. In het volgende voorbeeld is ARPU met 2,37% gestegen, met onder- en bovengrenzen van 0,55% en 4,19%, wat de verandering statistisch significant maakt.

![Betrouwbaarheidsinterval voor een metric](https://prod.docsiteassets.roblox.com/assets/analytics/configs/experiment-confidence.png)

Voor de gemak biedt de resultatenpagina je de mogelijkheid om de standaard configwaarde te vervangen door een van de varianten uit het experiment.

### [Steekproefverhouding mismatch](#steekproefverhouding-mismatch)[](#steekproefverhouding-mismatch)

Als je experiment er niet in slaagt om gebruikers in de verwachte verhoudingen in te schrijven, verschijnt er een waarschuwingsbanner voor Steekproefverhouding mismatch (SRM)  in het tabblad experimentresultaten. Als SRM wordt gedetecteerd, wordt aanbevolen om je experiment te stoppen en opnieuw te starten.

SRM wordt elke 5 minuten gecontroleerd voor de eerste 24 uur van je experiment, en daarna dagelijks. SRM kan experimentresultaten ongeldig maken; neem geen lanceerbeslissingen op basis van gecompromitteerde en onbetrouwbare resultaten.

![Steekproefverhouding mismatch banner](https://prod.docsiteassets.roblox.com/assets/analytics/configs/srm-banner.png)

### [Neem een beslissing](#neem-een-beslissing)[](#neem-een-beslissing)

Wanneer je experiment is afgelopen, klik je op Make decision  om een begeleide rollout te starten. Roblox toont eventuele waarschuwingen over statistische significantie en experimentduur, en vraagt je vervolgens om een winnende variant te selecteren of de controle te behouden. Op basis van je keuze voert Roblox de juiste wijziging door naar je permanente configs; terugkeren naar de Configs -pagina toont de nieuwe waarde. Klik op Change winner  als je van gedachten verandert.

Als je onopgeloste gestage wijzigingen op de config hebt wanneer je het experiment voltooit, slaat Roblox ze tijdelijk op en herstelt ze op basis van de beste inspanning na de rollout.

Je beslissing bepaalt de config-wijzigingen die Roblox voorstelt:

-

Controle : Roblox maakt geen wijzigingen aan je bestaande configs.

-

Ongetargete variant : De variantwaarde wordt de nieuwe standaardwaarde van de config. Roblox verwijdert alle andere voorwaarden op die config-sleutel, hoewel ze in je globale voorwaardenlijst blijven.

-

Getargete variant : Roblox integreert de winnende regel terug in je permanente config met behulp van de eerste toepasselijke optie in deze prioriteitsvolgorde:

1.

Overschrijven : Als er al een identieke voorwaarde bovenaan de config staat, overschrijft Roblox de waarde met de waarde van de winnende variant.

2.

Bestaande toevoegen : Als er een overeenkomende globale voorwaarde bestaat die van nature bovenaan zou staan, voegt Roblox deze toe aan de config met de waarde van de variant.

3.

Promoten : Als een overeenkomende globale voorwaarde veilig kan worden gepromoot naar de laagste rang die nodig is om het de bovenste regel in deze config te maken (zonder andere configs te wijzigen), voegt Roblox deze toe aan de config en herschikt deze globaal.

4.

Nieuwe maken : Anders maakt Roblox een nieuwe globale voorwaarde die één niveau boven de hoogste voorwaarde die momenteel in de config wordt gebruikt, is gerangschikt. Als dit een dubbele regel binnen de config creëert, verwijdert Roblox de overbodige voorwaardelijke waarde terwijl de globale regel behouden blijft.

## [Best practices voor experimenten](#best-practices-voor-experimenten)[](#best-practices-voor-experimenten)

-

Gebruik het minimum detecteerbare effect (MDE)  om te beslissen of je experiment de moeite waard is om uit te voeren.

Roblox berekent MDE met behulp van je doelmetric en het aantal spelers per variant, dat is gebaseerd op dagelijks actieve gebruikers, rolloutpercentage, experimentduur en variant splits. Als de MDE te hoog is voor je doelmetric (bijvoorbeeld meer dan 100%), is het onwaarschijnlijk dat je statistische significantie kunt bereiken. Spellen met minder dan 1.000 dagelijks actieve gebruikers kunnen moeite hebben om bruikbare gegevens uit experimenten te halen.

![Onvoldoende MDE-scherm tijdens creatie.](https://prod.docsiteassets.roblox.com/assets/analytics/configs/experiment-mde.png)

-

Begin met een hypothese.  In plaats van gewoon een variabele te wijzigen en de resultaten te controleren, schrijf een oorzaak-en-gevolgverklaring over wat je hebt veranderd, wat je verwacht dat er gebeurt en waarom. Naarmate je meer en meer experimenteert, kan het hebben van een set geschreven hypothesen om je resultaten te begeleiden helpen om je denken te verduidelijken en nieuwe ideeën voor experimenten te stimuleren.

-

Laat experimenten hun volledige duur draaien.  Het nieuwheidseffect (tijdelijke interesse in een wijziging niet omdat deze beter is, maar omdat deze nieuw is) kan vroege resultaten sterk vertekenen, waardoor ze soms in en uit statistische significantie kunnen schommelen. Experimenten vroeg beëindigen vergroot de kans dat je voortijdige actie onderneemt op basis van anomalieën die meer gegevens zouden hebben afgevlakt of zelfs tegengesproken.

-

De uitzondering is [vroeg schadelijk](#vroeg-schadelijke-metrics)  in de eerste 24 uur: als metrics worden gemarkeerd als kritisch schadelijk of je ziet [steekproefverhouding mismatch](#steekproefverhouding-mismatch) , bekijk en overweeg dan om te stoppen. Gebruik geen  vroeg schadelijke resultaten voor lanceerbeslissingen.

-

Handel niet zonder statistische significantie.  Zelfs schijnbaar grote veranderingen in het gedrag van spelers zijn mogelijk niet statistisch significant, meestal vanwege een kleine steekproefgrootte. Als een wijziging niet statistisch significant is, negeer deze dan.

-

Vermijd wijzigingen tijdens experimenten.  Grote bugs moeten natuurlijk worden opgelost, maar wijzigingen in spelinhoud kunnen het gedrag van spelers beïnvloeden en je resultaten ongeldig maken, zelfs als de wijzigingen schijnbaar  niet gerelateerd zijn aan je experiment. Evenzo, voer alleen experimenten gelijktijdig uit als je zeker weet dat ze elkaar niet zullen beïnvloeden.

-

Gebruik betrouwbaarheidsintervallen voor diepgaande analyses  van metrics en om te controleren op grensgevallen van statistische significantie. Als het betrouwbaarheidsinterval te breed is, kan de metric nooit statistische significantie bereiken.

-

Als één metric significant omhoog is en een andere significant omlaag, moet je beslissen of de afweging het waard is , mogelijk in combinatie met andere statistisch significante bewegingen.

-

Experimenten bieden sterke signalen, maar statistische significantie handelt in waarschijnlijkheden, niet zekerheden —vandaar het betrouwbaarheidsinterval. Gegevensvariabiliteit, steekproefgrootte en de omvang van de wijziging beïnvloeden allemaal de waarschijnlijkheid om te detecteren of een variant het gedrag van spelers heeft beïnvloed. Elke actie die je onderneemt op basis van de resultaten van een experiment moet worden afgewogen tegen kwalitatieve gegevens zoals feedback van spelers en je algehele visie voor het spel.

-

Documenteer je bevindingen en beslissingen.  Zelfs als je ze niet gebruikt om aanvullende experimenten uit te voeren, kan het hebben van een kennisbasis en bewijs helpen bij het ontwerpen van je spellen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
