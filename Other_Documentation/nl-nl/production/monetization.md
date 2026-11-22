<!-- Source: https://create.roblox.com/docs/nl-nl/production/monetization -->

Monetisatie | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)

# Monetisatie

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Monetisatie is een onderdeel van de algehele structuur van Roblox om waarde te bieden aan makers. Er zijn verschillende benaderingen om je inhoud te monetiseren, waaronder het gebruik van [abonnementen](#abonnementen) , het vragen van een toegangsprijs in [Robux](#betaalde-toegang-in-robux)  of [lokale valuta](#betaalde-toegang-in-lokale-valuta) , het aanbieden van [items of vaardigheden die gebruikers kunnen kopen](#ontwikkelaarsproducten) , het aanbieden van [privéservers](#priv%C3%A9servers)  voor gebruikers om alleen met vrienden te spelen, en het [verkopen van modellen en plugins](/docs/nl-nl/production/creator-store#distribute-and-sell-assets)  aan andere makers in de Creator Store.

Als je ervoor kiest om aankopenbare inhoud aan te bieden, registreert Roblox niet automatisch product- of aankoopinformatie. Om gegevensverlies te voorkomen, moet je deze gegevens zorgvuldig opslaan met behulp van [DataStoreService](/docs/nl-nl/reference/engine/classes/DataStoreService)  of een andere gegevensopslagdienst die buiten Roblox wordt gehost.

Voor een diepgaande kijk op het ontwerpen van optimale monetisatiestrategieën voor jouw ervaring, zie [Monetisatie fundamenten](/docs/nl-nl/production/game-design/monetization-foundations) .

## [Monetisatiestrategieën](#monetisatiestrategieën)[](#monetisatiestrategieën)

Wees voorzichtig met de monetisatiemethoden die je in je spel introduceert, aangezien onze gebruikers waarschijnlijk je spel zullen afkeuren  als ze niet akkoord gaan met je strategieën. Ook moeten alle ontwikkelaars transparant zijn over eventuele [kansgebonden monetisatie](/docs/nl-nl/production/monetization/paid-random-items)  en deze mechanismen verantwoordelijk gebruiken.

Sommige populaire monetisatiestrategieën voor gratis te spelen spellen op andere platforms worden niet aanbevolen voor Roblox. Bijvoorbeeld, afspraakmechanismen en timers die kunnen worden verwijderd of naar voren kunnen worden gehaald, kunnen goed werken op andere platforms, maar deze mechanismen zijn onpopulair bij Roblox-gebruikers die problemen hebben met het feit dat hun plezier voortijdig eindigt.

De volgende best practice suggesties zijn populair onder topontwikkelaars voor het afstemmen van monetisatiestrategieën op het Roblox-platform en het publiek.

Houd er rekening mee dat door deze technieken en overwegingen toe te passen, je niet gegarandeerd bent dat je je spel effectief kunt monetiseren. Vergeet niet dat je geen financiële doelen hoeft te hebben om plezier te hebben met het maken van een Roblox-spel.

### [Toeristen en locals](#toeristen-en-locals)[](#toeristen-en-locals)

Het kan nuttig zijn om Roblox-gebruikers in twee categorieën te denken:

-

Toeristen  springen meestal van het ene spel naar het andere, waarbij ze variëteit boven diepgang prioriteren. Ze geven de voorkeur aan items met onmiddellijke effecten, hetzij door het spel leuker te maken of door hen te laten opvallen, waardoor andere gebruikers zich afvragen hoe en waar ze het item hebben gekregen.

-

Locals  zijn eerder geneigd zich te concentreren op een bepaald spel of een kleinere set spellen. Ze zijn dieper betrokken en vormen doorgaans bijna de volledige betrokken gebruikersbasis van een spel. Ze zijn meer geïnteresseerd in items met langdurige voordelen, zoals een [battle pass](/docs/nl-nl/production/game-design/season-pass-design) .

Om meer te leren over hoe je je spel kunt ontwerpen met Roblox-gebruikers in gedachten, zie [Ontwerp voor Roblox](/docs/nl-nl/production/game-design/design-for-roblox) .

### [Sociale functies](#sociale-functies)[](#sociale-functies)

Roblox-gebruikers genieten vaak van spellen die de sociale interactie benadrukken. Bijvoorbeeld, het hebben van items of evenementen die slechts voor een beperkte tijd  beschikbaar zijn, kan opwinding rond die inhoud creëren. Een ruil  systeem moedigt gebruikers aan om met elkaar te interageren. Hoewel beide systemen op zichzelf succesvol kunnen zijn, zijn ze bijzonder effectief wanneer ze worden gecombineerd.

### [Live ops](#live-ops)[](#live-ops)

Ondersteuning na de lancering is op veel manieren gemakkelijker op Roblox dan op andere platforms, omdat je snel updates kunt verzenden om je spel te verbeteren.

Frequent  inhoudsupdates kunnen nuttig zijn als je de betrokkenheid bij je spel in de loop van de tijd wilt behouden. Roblox-gebruikers zijn gewend om betrokken te worden door regelmatige updates, en het kan veel moeilijker zijn om de interesse van een gebruiker terug te winnen dan om actieve gebruikers te behouden. Een wekelijkse frequentie  voor updates is ideaal. Als minimum, streef naar maandelijkse updates. Voor een discussie over inhoudsfrequentie, zie de Level Up [inhoudsfrequentieworkshop](/docs/nl-nl/production/game-design/content-updates) .

Bij het ontwerpen van updates, houd ze gefocust op een bepaald thema . Dit maakt het gemakkelijker voor gebruikers om de nieuwe update te begrijpen en te zien welke inhoud nieuw is wanneer ze zich aanmelden. Het helpt je ook om je inhoud en promotionele middelen te coördineren. Bijvoorbeeld, als je een nieuwe Dierentuin toevoegt aan je rollenspel, zorg ervoor dat alle nieuwe inhoud enige verbinding heeft met het Dierentuin-thema.

Wees niet bang om gebruikers hun toegang  tot nieuwe inhoud te laten verdienen. Nieuwe gebruikers zullen zich haasten om nieuwe updates te spelen, maar als ze niet het gevoel hebben dat ze iets hebben bereikt  in het spel, kunnen ze snel weer vertrekken. Je kunt een gevoel van het verdienen van een update creëren, hetzij door de update-inhoud te monetiseren of door voorwaarden te creëren voor het spelen van de nieuwe inhoud.

Om meer te leren over hoe je effectieve ondersteuning na de lancering voor je spel kunt ontwerpen, zie [Live ops essentials](/docs/nl-nl/production/game-design/liveops-essentials) .

## [Producten](#producten)[](#producten)

### [Indringende advertenties](#indringende-advertenties)[](#indringende-advertenties)

Het [indringende advertenties](/docs/nl-nl/production/monetization/immersive-ads)  systeem stelt je in staat om advertentie-eenheden in je spel in te voegen die Roblox in staat stellen om programmatisch advertentie-inhoud van adverteerders aan je actieve gebruikers te tonen.

![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/Overview-ImageAd.jpg) Afbeelding advertentieformaat

Portal advertentieformaat

### [Roblox Plus](#roblox-plus)[](#roblox-plus)

[Roblox Plus](/docs/nl-nl/production/monetization/roblox-plus)  stelt je in staat om te verdienen door verhoogde in-game aankopen die worden aangedreven door door Roblox gesubsidieerde gebruikerskortingen, aanmeldbonussen voor elke nieuwe abonnee die je binnenhaalt, en betrokkenheid bij betaalde privéservers.

### [Abonnementen](#abonnementen)[](#abonnementen)

[Abonnementen](/docs/nl-nl/production/monetization/subscriptions)  binnen spellen stellen je in staat om gebruikers terugkerende voordelen te bieden voor een maandelijkse vergoeding.

![](https://prod.docsiteassets.roblox.com/assets/monetization/subscriptions/Example-Subscriptions.png) Voorbeelden van spelabonnementen

### [Toegangspassen](#toegangspassen)[](#toegangspassen)

Een [pass](/docs/nl-nl/production/monetization/passes)  stelt je in staat om een eenmalige Robux vergoeding  te vragen zodat gebruikers speciale privileges binnen een spel kunnen krijgen, zoals toegang tot een beperkt gebied, een in-game avataritem, of een permanente power-up.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/passes/passes-sample.png)

### [Ontwikkelaarsproducten](#ontwikkelaarsproducten)[](#ontwikkelaarsproducten)

Een [ontwikkelaarsproduct](/docs/nl-nl/production/monetization/developer-products)  is een item of vaardigheid die een gebruiker meer dan eens kan kopen, zoals in-game valuta, munitie of toverdranken. Je kunt aankopen aanmoedigen, ze registreren en productinformatie verkrijgen via scripting.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/developer-products/Buy-Product-Example.jpg)

### [Beheerde prijzen](#beheerde-prijzen)[](#beheerde-prijzen)

[Beheerde prijzen](/docs/nl-nl/production/monetization/managed-pricing)  is een verenigd systeem dat [regionale prijzen](/docs/nl-nl/production/monetization/regional-pricing)  en [prijsoptimalisatie](/docs/nl-nl/production/monetization/price-optimization)  samenbrengt op één plek. Je meldt je één keer aan, kiest welke items je wilt opnemen, en Beheerde prijzen houdt je prijzen in de loop van de tijd geoptimaliseerd over producten en regio's.

### [Prijsoptimalisatie](#prijsoptimalisatie)[](#prijsoptimalisatie)

[Prijsoptimalisatie](/docs/nl-nl/production/monetization/price-optimization)  stelt je in staat om de beste prijsniveaus voor je passen en ontwikkelaarsproducten te vinden, wat je kan helpen om in de loop van de tijd meer geld te verdienen terwijl je prijzen concurrerend blijven.

### [Betaalde toegang in Robux](#betaalde-toegang-in-robux)[](#betaalde-toegang-in-robux)

[Betaalde toegang in Robux](/docs/nl-nl/production/monetization/paid-access-robux)  stelt je in staat om gebruikers een eenmalige Robux vergoeding  te vragen om toegang te krijgen tot je spel. Sommige ontwikkelaars gebruiken deze functie tijdelijk om een gesloten bèta te creëren waar hun meest betrokken gebruikers vroegtijdig toegang tot een spel kunnen krijgen en kunnen helpen met testen en feedback.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/paid-access/Buy-Access-Example.png)

### [Betaalde toegang in lokale valuta](#betaalde-toegang-in-lokale-valuta)[](#betaalde-toegang-in-lokale-valuta)

[Betaalde toegang in lokale valuta](/docs/nl-nl/production/monetization/paid-access-local-currency)  stelt je in staat om gebruikers een eenmalige vergoeding in hun lokale valuta  te vragen om toegang te krijgen tot je spel. Als hun lokale valuta niet beschikbaar is, worden ze in USD in rekening gebracht. Sommige ontwikkelaars gebruiken deze functie tijdelijk om een gesloten bèta te creëren waar hun meest betrokken gebruikers vroegtijdig toegang tot een spel kunnen krijgen en kunnen helpen met testen en feedback.

### [Privéservers](#privéservers)[](#privéservers)

Een [privéserver](/docs/nl-nl/production/monetization/private-servers)  is een abonnementsfunctie die een gebruiker in staat stelt te beslissen wie er met hen een spel kan spelen. Hoewel privéservers gratis kunnen zijn, kun je privéservers ook gebruiken als een methode van monetisatie door gebruikers die toegang willen tot privéservers een maandelijkse Robux vergoeding  te vragen.

### [Catalogusvergoedingen en commissies](#catalogusvergoedingen-en-commissies)[](#catalogusvergoedingen-en-commissies)

Je kunt accessoires en kleding maken en verkopen op de Marketplace. Nadat je de uploadvergoeding hebt betaald en een nieuw asset ter goedkeuring hebt ingediend, beoordeelt het moderatorteam je asset en, als deze is goedgekeurd, wordt je asset aan de catalogus toegevoegd.

Je ontvangt een [commissie](/docs/nl-nl/marketplace/marketplace-fees-and-commissions)  elke keer dat gebruikers je catalogusitem kopen. Als gebruikers je catalogusitem binnen een spel kopen met behulp van het [avatar inspectiemenu](/docs/nl-nl/players/avatar-inspect-menu)  of de [avatar editor service](/docs/nl-nl/players/avatar-editor) , ontvangt de spel eigenaar ook een commissie.

### [Plugins en Modellen](#plugins-en-modellen)[](#plugins-en-modellen)

Een [plugin](/docs/nl-nl/studio/plugins)  is een extensie die extra functionaliteit aan Studio toevoegt, en een [model](/docs/nl-nl/parts/models)  is een herbruikbaar assettype. Je kunt beide gratis aanbieden aan andere makers in de [Creator Store](/docs/nl-nl/production/creator-store) , of je kunt ze verkopen voor Verenigde Staten Dollars  (de minimale prijs is $4.99 voor plugins en $2.99 voor modellen). Roblox biedt een marktleidend inkomstenpercentage voor deze verkopen, aangezien alleen belastingen en verwerkingskosten worden afgetrokken. Voor meer informatie over het verkopen van plugins en modellen, zie [Creator Store - Distribueer en verkoop assets](/docs/nl-nl/production/creator-store#distribute-and-sell-assets) .

Er is een escrow-hold van 30 dagen voor elke aankoop. Roblox houdt je aandeel van de verkoop 30 dagen vast, te beginnen vanaf de datum van verkoop.

## [Richtlijnen](#richtlijnen)[](#richtlijnen)

Wanneer je monetisatieproducten in je spellen ontwerpt en implementeert, overweeg dan de volgende richtlijnen om ervoor te zorgen dat je monetisatiemethoden geschikt zijn voor alle doelgroepen op het platform.

### [Producten presenteren](#producten-presenteren)[](#producten-presenteren)

Om veiligheid en eerlijkheid te waarborgen, moet je monetisatieproducten op een transparante, eerlijke en gebruiksvriendelijke manier presenteren. Bijvoorbeeld, als je kortingen aanbiedt, moeten deze oprecht  en eerlijk  zijn:

-

Een korting is niet oprecht als een item altijd "in de aanbieding" is voor hetzelfde aantal Robux.

-

Een korting is niet eerlijk als deze slechts voor een zeer korte tijd wordt aangeboden, waardoor gebruikers onder druk worden gezet om zo snel mogelijk een aankoop te doen.

Gebruikers mogen nooit worden misleid, verward of onder druk gezet tot aankopen op manieren die ze niet van plan waren, en ze moeten altijd de vrijheid hebben om een duidelijke, weloverwogen keuze te maken om een abonnement te verkrijgen of Robux uit te geven aan een specifiek item. Als algemene richtlijn zijn er enkele praktijken die je altijd moet vermijden bij het presenteren van monetisatieproducten aan je publiek:

-

Claim niet dat een abonnement of item bijna op is of slechts voor een korte tijd beschikbaar is als dat niet waar is.

-

Gebruik geen afteltimer die niet nauwkeurig is of automatisch opnieuw begint voor hetzelfde item.

Bijvoorbeeld, als je spel een "aanbieding van de dag" bevat die zegt dat het slechts 24 uur beschikbaar is, maar je toont dezelfde boodschap aan gebruikers elke keer dat ze inloggen en het nooit stopt met beschikbaar zijn, heb je een vals gevoel van urgentie gecreëerd dat niet gebruiksvriendelijk is.

### [Promoten aan wereldwijde doelgroepen](#promoten-aan-wereldwijde-doelgroepen)[](#promoten-aan-wereldwijde-doelgroepen)

Roblox is een wereldwijde gemeenschap voor gebruikers van alle leeftijden, dus promoties binnen je spellen moeten standaard geschikt zijn voor alle doelgroepen. Als bepaalde monetisatieproducten in bepaalde locaties zijn beperkt, zoals betaalde willekeurige items, biedt Roblox de [PolicyService](/docs/nl-nl/reference/engine/classes/PolicyService)  API om je te helpen ervoor te zorgen dat die producten alleen zichtbaar zijn voor in aanmerking komende gebruikers.

[PolicyService](/docs/nl-nl/reference/engine/classes/PolicyService)  geeft terug of een gebruiker in aanmerking komt voor specifieke items of functies op basis van hun locatie, leeftijd en platform. Je moet deze API in je spel integreren om aan je nalevingsverplichtingen te voldoen, inclusief het bepalen of elke gebruiker:

-

In aanmerking komt om abonnementen of commerciële producten aan te schaffen.

-

Betaalde willekeurige items, betaalde itemruil, of om indringende advertenties te zien.

Als een gebruiker Robux of iets anders dat met Robux is verkregen kan gebruiken om een willekeurige beloning te krijgen, ben je verplicht om [PolicyService](/docs/nl-nl/reference/engine/classes/PolicyService)  te gebruiken om deze functie te blokkeren voor gebruikers die niet zijn toegestaan om willekeurige items in ruil voor Robux te gebruiken.

Als algemene richtlijn, vermijd het gebruik van opdringerige of urgente berichten bij interactie met minderjarigen, aangezien hoge druktaal overweldigend kan zijn:

| ** Taal om te vermijden** | | ** Aangeraden alternatieven** |
| --- | --- |
| "KRIJG HET NU" | | "Bekijk Item" |
| "LAATSTE KANS, ACTEER NU" | | "Bekijk Prijs" |
| "KOOP VOORDAT HET WEG IS!" | | "Open Winkel" |

## [Aanvullende lokalisaties voor deze pagina](#aanvullende-lokalisaties-voor-deze-pagina)[](#aanvullende-lokalisaties-voor-deze-pagina)

Voor aanvullende, gelokaliseerde versies van deze pagina die niet beschikbaar zijn in de taalkeuzer van de site, zie de volgende links:

-

[Bulgaars (български)](https://create.roblox.com/docs/bg-bg/production/monetization)

-

[Kroatisch (hrvatski)](https://create.roblox.com/docs/hr-hr/production/monetization)

-

[Tsjechisch (čeština)](https://create.roblox.com/docs/cs-cz/production/monetization)

-

[Deens (dansk)](https://create.roblox.com/docs/da-dk/production/monetization)

-

[Nederlands (Nederlands)](https://create.roblox.com/docs/nl-nl/production/monetization)

-

[Estisch (eesti)](https://create.roblox.com/docs/et-ee/production/monetization)

-

[Fins (suomi)](https://create.roblox.com/docs/fi-fi/production/monetization)

-

[Grieks (Ελληνικά)](https://create.roblox.com/docs/el-gr/production/monetization)

-

[Hongaars (magyar)](https://create.roblox.com/docs/hu-hu/production/monetization)

-

[Iers (Gaeilge)](https://create.roblox.com/docs/ga-ie/production/monetization)

-

[Lets (latviešu)](https://create.roblox.com/docs/lv-lv/production/monetization)

-

[Litouws (lietuvių)](https://create.roblox.com/docs/lt-lt/production/monetization)

-

[Maltees (Malti)](https://create.roblox.com/docs/mt-mt/production/monetization)

-

[Portugees - Portugal (português)](https://create.roblox.com/docs/pt-pt/production/monetization)

-

[Roemeens (română)](https://create.roblox.com/docs/ro-ro/production/monetization)

-

[Slowaaks (slovenčina)](https://create.roblox.com/docs/sk-sk/production/monetization)

-

[Sloveens (slovenščina)](https://create.roblox.com/docs/sl-si/production/monetization)

-

[Zweeds (svenska)](https://create.roblox.com/docs/sv-se/production/monetization)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
