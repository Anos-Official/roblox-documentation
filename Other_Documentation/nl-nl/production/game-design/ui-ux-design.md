<!-- Source: https://create.roblox.com/docs/nl-nl/production/game-design/ui-ux-design -->

UI en UX ontwerp | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Game-ontwerp](/docs/nl-nl/production/game-design)
6. /
7. Je ervaring bouwen

# UI en UX ontwerp

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De * gebruikersinterface*  (UI) combineert artistiek visueel ontwerp met communicatiegerichte informatieontwerp om menu's, winkelindelingen, heads-up displays (HUD's) en andere interfaces te produceren waarmee spelers interactie hebben. De * gebruikerservaring*  (UX) heeft betrekking op hoe spelers met het spel omgaan, hoe ze hun keuzes kenbaar maken en hoe ze van de ene keuze naar de andere bewegen. Hoewel UI en UX vaak samen werken, ligt de focus van UX meer op interactiviteit en de ervaring van de speler dan op het visuele en informatieve ontwerp van de UI.

Optimaliseer je interface door [Experimenten](/docs/nl-nl/production/experiments)  te gebruiken om te testen hoe verschillende knopplaatsingen of HUD-indelingen de betrokkenheid van spelers beïnvloeden. Je kunt ook [Configuraties](/docs/nl-nl/production/configs)  gebruiken om platform-specifieke UI-elementen of seizoensgebonden thema's onmiddellijk over alle actieve servers te schakelen om je spel fris te houden.

## [UI](#ui)[](#ui)

De UI deelt belangrijke informatie zoals hitpoints, questdoelen en prijzen die spelers in staat stellen om beslissingen te nemen en door het spel te navigeren. Omdat het vaak de primaire manier is waarop spellen met de speler communiceren, is UI cruciaal voor de ervaring van spelers. Slecht ontworpen UI kan spelers in verwarring brengen en frustreren en leiden tot slechte retentie, terwijl deskundig ontworpen UI kan bijdragen aan betrokkenheid en monetisatie. Effectief ontworpen UI maakt gebruik van de volgende principes:

-

Prioritering

-

Aandacht

-

Visuele Taal

-

Conventies

-

Consistentie

### [Prioritering](#prioritering)[](#prioritering)

Het delen van de belangrijkste informatie eerst staat bekend als de * Hiërarchie van Informatie* . Dit is bijzonder cruciaal in spellen waar spelers vaak onmiddellijke beslissingen moeten nemen op basis van een beperkte set informatie. Bij het prioriteren van de UI, identificeer wat essentieel of het meest relevant is voor de ervaring van de speler en zorg ervoor dat het zowel toegankelijk als gemakkelijk te vinden is. Overweeg deze vragen:

-

Wat doet de speler op dit moment?

-

Wat is het belangrijkste waar ze zich van bewust moeten zijn, of toegang toe moeten hebben?

-

Welke keuzes moeten ze maken?

-

Welke informatie hebben ze nodig om die keuzes te maken?

-

Hoe vaak zullen ze die keuzes maken?

Belangrijke informatie en functies veranderen afhankelijk van factoren zoals de rol die de speler aanneemt, hun locatie in de 3D-wereld en de items die ze vasthouden. De UI kan zo worden ontworpen dat alleen wordt gepresenteerd wat contextueel belangrijk is – de knoppen en informatie verwisselen afhankelijk van wat nuttig is in elke context. Dit zorgt ervoor dat spelers altijd hebben wat ze nodig hebben, zonder de rommel van alles wat ze niet nodig hebben.

#### Voorbeelden

Irrelevante elementen kunnen verwarring en afleiding veroorzaken. [* Spellbound RPG*](https://www.roblox.com/games/6468323505/)  heeft een schone, minimalistische UI die bijzonder cruciaal is voor mobiele interfaces, aangezien kleine schermen gemakkelijk overweldigd kunnen worden door overmatige knoppen, schermen en tekst.

![Een close-up van een niet-geselecteerde cirkelvormige Items-knop met een bruine boekicoon. De omgeving op de achtergrond is een bruine grond met een patch sneeuw.](https://prod.docsiteassets.roblox.com/assets/game-design/ui-ux-design/ui-ux-design-3.png) Items vóór selectie in [Spellbound RPG](https://www.roblox.com/games/6468323505/)

![Een close-up van een geselecteerde cirkelvormige Items-knop met een bruine boekicoon, samen met drie extra knoppen voor vaardigheden, uitrusting en de spelersdecks. De extra knoppen worden alleen weergegeven wanneer de knop is geselecteerd.](https://prod.docsiteassets.roblox.com/assets/game-design/ui-ux-design/ui-ux-design-2.png) Items na selectie in [Spellbound RPG](https://www.roblox.com/games/6468323505/)

In [* Super Striker League*](https://www.roblox.com/games/3360853050/)  variëren de interacties van spelers afhankelijk van of ze de bal controleren. Zonder de bal kunnen spelers Sprinten en Tackelen om de controle terug te krijgen. Zodra ze in bezit zijn, schakelen de knoppen over naar Deke en Pass, waarmee spelers tegenstanders kunnen ontwijken en de bal kunnen passen. Door deze knoppen af te wisselen, blijft de UI contextueel nuttig en vermijdt onnodige afleidingen.

![](https://prod.docsiteassets.roblox.com/assets/game-design/ui-ux-design/ui-ux-design-6.png) Contextuele knoppen in [Super Striker League](https://www.roblox.com/games/3360853050/)

![](https://prod.docsiteassets.roblox.com/assets/game-design/ui-ux-design/ui-ux-design-7.png) Contextuele knoppen in [Super Striker League](https://www.roblox.com/games/3360853050/)

In [* The Survival Game,*](https://www.roblox.com/games/11156779721/)  moeten spelers zich bewust zijn van hun gezondheid en hongerstatus, en snel toegang hebben tot hun kaart, inventaris en gereedschappen. Deze informatie stelt hen in staat om beslissingen te nemen en acties te prioriteren voor overleving. Als deze informatie of gereedschappen moeilijk te vinden of ontbrekend zijn, wordt overleven uitdagender en onnodig frustrerend.

![](https://prod.docsiteassets.roblox.com/assets/game-design/ui-ux-design/ui-ux-design-1.png)  HUD-functies in [The Survival Game](https://www.roblox.com/games/11156779721/)

### [Aandacht](#aandacht)[](#aandacht)

Ondanks een minimalistische, geprioriteerde en gecontextualiseerde UI, hebben spelers mogelijk nog steeds hulp nodig bij het vinden van wat ze nodig hebben. UI-ontwerpers kunnen verschillende visuele hulpmiddelen gebruiken om de aandacht van spelers te trekken en te begeleiden, zoals:

-

Kleur:  Heldere kleuren trekken meer aandacht dan doffe kleuren. Gebruik levendige tinten voor cruciale tekst, knoppen en andere elementen, en gedempte tinten voor minder belangrijke. Dit contrast verbetert de zichtbaarheid en vermindert afleiding.

-

Grootte:  Grotere elementen zijn opvallender en worden als belangrijker ervaren dan kleinere.

-

Ruimte:  Elementen omringd door voldoende negatieve ruimte of padding zijn opvallend.

-

Proximitiet:  Groepselementen impliceren een verbinding. Door gerelateerde functies en items dicht bij elkaar te plaatsen, kunnen spelers hun associatie begrijpen en ze gemakkelijker vinden.

-

Beweging:  Geanimeerde elementen trekken aandacht. Zelfs lichte beweging kan een element laten opvallen te midden van statische tegenhangers. Deeltjeseffecten, wiebelende knoppen en geanimeerde pijlen worden vaak gebruikt in tutorials voor begeleiding.

Matiging is de sleutel bij het gebruik van deze hulpmiddelen. Overmatig gebruik van heldere, bewegende elementen kan spelers overweldigen en verwarren in plaats van hen te helpen.

#### Voorbeelden

In [* Jailbreak*](https://www.roblox.com/games/606849621/) 's seizoenspas UI ligt een strook van goudgeel onder de seizoenspas-exclusieve iconen, wat de aandacht vestigt op de premium beloningen en ze visueel onderscheidend maakt van de gratis beloningen.

![](https://prod.docsiteassets.roblox.com/assets/game-design/ui-ux-design/ui-ux-design-8.png)  Seizoenspas UI in [Jailbreak](https://www.roblox.com/games/606849621/)

In [* Dragon Adventures,*](https://www.roblox.com/games/3475397644/)  krijgt de hoogste waarde muntbundel visuele prioriteit door de grootte te vergroten en deze te scheiden met meer padding, om deze te onderscheiden van kleinere bundels.

![](https://prod.docsiteassets.roblox.com/assets/game-design/ui-ux-design/ui-ux-design-9.png)  Muntbundels in [Dragon Adventures](https://www.roblox.com/games/3475397644/)

In [* Tower Defense Simulator*](https://www.roblox.com/games/3260590327/)  worden zowel grootte als nabijheid gebruikt om Daily Tower Skins visueel te groeperen en te onderscheiden van Daily Crates.

![](https://prod.docsiteassets.roblox.com/assets/game-design/ui-ux-design/ui-ux-design-10.png) De winkel in [Tower Defense Simulator](https://www.roblox.com/games/3260590327/)

### [Visuele taal](#visuele-taal)[](#visuele-taal)

Naast het richten van de aandacht van spelers op de belangrijkste elementen op het scherm, ontwikkelen UI-ontwerpers een visuele taal om spelers te helpen begrijpen wat ze zien. Een visuele taal is een set van opzettelijke en consistente ontwerpkeuzes die informatie in één oogopslag bieden over het doel, de status, associaties en relevantie van een element. De taal is opgebouwd uit hulpmiddelen zoals vorm, kleur en stijl. Enkele toepassingen van visuele taal zijn:

#### Iconen

Iconen kunnen een visuele identiteit gebruiken die betekenis en associaties overbrengt. Bijvoorbeeld, iconen die gerelateerd zijn aan specifieke statistieken kunnen een kleurenpalet en vergelijkbare vormen delen, waardoor spelers hun functie kunnen herkennen en begrijpen.

![](https://prod.docsiteassets.roblox.com/assets/game-design/ui-ux-design/ui-ux-design-11.png)  Speler Statistieken in [* Winds of Fortune*](https://www.roblox.com/games/7714627632/)

#### Knoppen

Als een veelvoorkomende vorm van spelersinvoer, moeten knoppen gemakkelijk te identificeren zijn. Knoppen in een container plaatsen, zoals een kleur rondom de tekst of het icoon, onderscheidt ze van de achtergrond, waardoor ze interactief lijken. Het toevoegen van highlights of schaduwen kan hun tastbare aantrekkingskracht vergroten door 3D-diepte te suggereren.

![](https://prod.docsiteassets.roblox.com/assets/game-design/ui-ux-design/ui-ux-design-12.png)  Knoppen in [* BotClash Simulator*](https://www.roblox.com/games/9300407930/)

#### Tekst

Headers en titels die belangrijke informatie op hoog niveau bevatten, moeten groter en vetter zijn dan de bodytekst. Kleuren die zeer leesbaar zijn en goed contrasteren met de achtergrondkleur waarop ze worden weergegeven, moeten worden overwogen. Stijlkeuzes zoals kleur en vetgedrukt kunnen belangrijke informatie zoals in-game items, statistieken of vaardigheden benadrukken. Geef altijd prioriteit aan leesbaarheid bij het kiezen van een lettertype.

![](https://prod.docsiteassets.roblox.com/assets/game-design/ui-ux-design/ui-ux-design-13.png)  Kledingwinkel in [Winds of Fortune](https://www.roblox.com/games/7714627632/)

Zodra de visuele taal is ontworpen, kan deze worden gedocumenteerd in een * Stijlgids* , een set regels en voorbeelden die iedereen in het team helpt te begrijpen hoe de taal consistent in het spel kan worden toegepast.

### [Conventies](#conventies)[](#conventies)

Conventies zijn veelvuldig toegepaste ontwerpkeuzes die in veel verschillende spellen worden gezien. Enkele voorbeelden zijn:

-

Een X-symbool op een knop die de dialoog sluit wanneer erop wordt gedrukt

-

De kleur grijs toegepast op knoppen die momenteel niet bruikbaar zijn

-

Een hangsloticoon dat over een knop of functie ligt om aan te geven dat de speler deze nog niet heeft verdiend of ontgrendeld

Gezien hun wijdverspreide gebruik zijn spelers doorgaans bekend met dergelijke conventies. Het benutten van deze bekendheid kan een interface intuïtiever maken en de behoefte aan spel-specifieke instructies verminderen. Het spelen van spellen binnen je doelgenre kan helpen om conventies te identificeren die spelers mogelijk herkennen. Een UI-ontwerper kan ervoor kiezen om een unieke benadering te kiezen die beter bij hun spel past, maar het kennen van deze conventies informeert hun besluitvormingsproces.

![](https://prod.docsiteassets.roblox.com/assets/game-design/ui-ux-design/ui-ux-design-14.png) X Sluitknoppen in [Winds of Fortune](https://www.roblox.com/games/7714627632/) , [Dragon Adventures](https://www.roblox.com/games/3475397644/) , [BotClash Simulator](https://www.roblox.com/games/9300407930/) , en [DOORS](https://www.roblox.com/games/6516141723/)

![](https://prod.docsiteassets.roblox.com/assets/game-design/ui-ux-design/ui-ux-design-15.png) Groene "Gezondheid" stat consistentie in [Arcane Odyssey](https://www.roblox.com/games/3272915504/)

### [Consistentie](#consistentie)[](#consistentie)

Welke beslissingen een UI-ontwerper ook maakt, ze moeten deze consistent toepassen in het hele spel. Consistentie helpt spelers om efficiënter door het spel te navigeren en voorkomt verwarring en frustratie.

Hier zijn enkele voorbeelden van UI-consistentie in een spel:

-

De "Gezondheid" stat verschijnt in het groen in alle tekst, gerelateerde iconen en de gezondheidsbalk.

-

Elke keer dat NPC-dialogen een in-game item vermelden, wordt het vetgedrukt.

-

Sluitknoppen zijn altijd vierkant, rood en bevatten een witte X, die alleen in de rechterbovenhoek van een dialoog verschijnt.

-

Wanneer een speler zich een item in de winkel niet kan veroorloven, wordt de prijs in het rood weergegeven.

Deze keuzes zijn opzettelijk, met als doel de begrip en navigatie van de speler te vergemakkelijken. Door ze consistent toe te passen, stellen ze spelers in staat om gerelateerde elementen te associëren, belangrijke items te identificeren, spierherinnering te ontwikkelen, snel geïnformeerde beslissingen te nemen en meer tijd in het spel door te brengen.

## [UX](#ux)[](#ux)

UX-ontwerp heeft betrekking op hoe spelers met het spel omgaan, hoe ze hun keuzes kenbaar maken en hoe ze van de ene keuze naar de andere bewegen. Hoewel UX vaak hand in hand gaat met de gebruikersinterface (UI), is het meer gericht op interactiviteit en de ervaring van de speler dan op het visuele en informatieve ontwerp van de UI.

### [Begrijpen van spelers](#begrijpen-van-spelers)[](#begrijpen-van-spelers)

Een primair doel van de UX-ontwerper is om interacties en stromen te creëren die intuïtief, onopdringerig en handig zijn voor spelers om te gebruiken. Dit proces begint met een begrip van de spelers zelf, de beoogde doelgroep voor een spel. Bij het identificeren van spelers van een spel, overweeg de volgende:

-

Demografie:  Demografie helpt om ontwerpkeuzes te informeren door gegeneraliseerde informatie over een spelersgroep te onthullen. Bijvoorbeeld, jongere spelers zijn over het algemeen waarschijnlijker om op mobiele of tabletapparaten te spelen dan op persoonlijke computers, dus spellen die voor dat publiek zijn bedoeld, prioriteren vaak het ontwerpen en verfijnen van de mobiele gebruikerservaring.

-

Ervaringsniveau:  Ontwikkelaars kunnen ervoor kiezen om te ontwerpen voor spelers met weinig game-ervaring, een aanzienlijke hoeveelheid, of ergens daartussenin. Interacties die bekend zijn voor ervaren spelers, zoals het indrukken van een nummer toets om een item in een werkbalk uit te rusten, of het indrukken van c om te hurken, zijn mogelijk niet voor de hand liggend voor onervaren spelers en vereisen extra messaging of training.

-

Genre bekendheid:  Vergelijkbaar met het algemene ervaringsniveau, weerspiegelt genre bekendheid het ervaringsniveau van spelers met een specifiek type spel. Spellen die vallen onder populaire genres op Roblox, zoals rollenspel, survival horror en first-person shooter, hebben waarschijnlijk veel potentiële spelers die eerder een vergelijkbaar genre hebben gespeeld. Spellen in andere genres hebben mogelijk minder ervaren spelers, maar die ervaringskloof kan worden overbrugd door middel van tutorials en bruikbaarheid.

-

Gameplay-stijl:  Spelers geven vaak de voorkeur aan specifieke soorten spel, variërend van competitie en het verzamelen van prestaties tot verkenning en samenwerking. Deze voorkeuren worden niet alleen weerspiegeld in de spelmechanica die spelers verkiezen, maar beïnvloeden ook UX-beslissingen. Ontwerpers overwegen welke interacties ze prioriteit moeten geven, welke ze moeten verfijnen en welke ze aan de spelers moeten presenteren. Ze houden ook rekening met de mindset die spelers zullen hebben wanneer ze met deze interacties omgaan en de emoties die ze willen oproepen.

Na het overwegen van deze factoren en het selecteren van een doelspeler groep (of groepen), leer ze beter kennen door ze te ontmoeten, met ze te spelen en meer te leren over hun doelen en voorkeuren om ontwerpkeuzes beter te informeren.

### [Ontwerp interacties](#ontwerp-interacties)[](#ontwerp-interacties)

* Interacties*  zijn functies die spelers in staat stellen om hun keuzes in een spel te ervaren en te communiceren. UX-ontwerpers willen dat die interacties intuïtief zijn en zo min mogelijk uitleg vereisen. Om dit te doen, maken ze gebruik van:

-

Conventies

-

Metafoor

-

Feedback

#### Conventies

* Conventies*  zijn UX-ontwerpen en principes waarmee spelers mogelijk al bekend zijn uit andere spellen.

![](https://prod.docsiteassets.roblox.com/assets/game-design/ui-ux-design/ui-ux-design-16.png)  "E" nabijheidsprompt in [* Mermaid Life*](https://www.roblox.com/games/4377254026/)

Voorbeelden van conventies zijn:

-

De "E" nabijheidsprompt die Roblox-ontwikkelaars gebruiken om spelers te signaleren dat een item interactief is als ze dichtbij genoeg staan voor het om te verschijnen.

-

De "C" toets waarmee de avatar van de speler kan hurken zodat ze onder obstakels kunnen duiken of in krappe ruimtes kunnen passen.

-

Nummer toetsen die items uit een werkbalk in de handen van de avatar uitrusten zodat ze kunnen worden gebruikt.

-

In cirkels op de grond lopen om je aan te melden voor een wedstrijd.

Conventies worden gevestigd wanneer een bepaalde implementatie of ontwerpkeuze populair wordt vanwege het gebruiksgemak. "C" om te hurken, bijvoorbeeld, is gemakkelijk te onthouden omdat het de eerste letter is in het woord hurken, en is handig gelegen naast WASD, de toetsen die spelers gebruiken om te navigeren. Het is een gemakkelijke interactie om snel en onder druk uit te voeren, wat ideaal is aangezien het proberen te verbergen of te vluchten voor een naderende bedreiging een veelvoorkomende gebruiksgeval is voor hurken.

#### Metafoor

* Metafoor*  relateert een abstract concept aan een meer vertrouwd concept, waardoor een snelkoppeling naar begrip ontstaat. In dit voorbeeld van * Spellbound Wizard RPG*  wordt de handeling van het casten van magische spreuken uitgevoerd door kaarten uit een deck te trekken. De deck-gebaseerde UI/UX verankert de abstracte handeling van het casten van spreuken, die geen echte uitdrukking heeft, in iets waar spelers zich gemakkelijker mee kunnen identificeren en sneller kunnen begrijpen.

![](https://prod.docsiteassets.roblox.com/assets/game-design/ui-ux-design/ui-ux-design-4.png)  Spreuken casten als kaarten in [* Spellbound RPG*](https://www.roblox.com/games/6468323505/)

#### Feedback

Communicatie van het spel naar de speler staat bekend als * feedback* . Feedback helpt spelers te begrijpen dat een actie die ze hebben ondernomen. Het kan bijdragen aan het leren hoe het spel functioneert en een extra laag van verfijning toevoegen die een functie bevredigender maakt om te gebruiken. Enkele voorbeelden van feedback zijn:

-

Een vijand die zijn "hit" reactie-animeert om aan te geven dat hij schade heeft opgelopen van het wapen van de speler

-

Een knop die van kleur verandert om de hover-, ingedrukte en vrijgegeven (geselecteerde) staat aan te geven

-

Een kassa "cha-ching!" geluids effect dat afspeelt wanneer de speler een aankoop voltooit

-

Een voortgangsbalk die zich vult terwijl de speler questdoelen voltooit

Wanneer feedback ontbreekt of onvoldoende is, weten spelers mogelijk niet wat ze hebben bereikt, begrijpen ze niet of de effecten goed of slecht waren, of weten ze zelfs niet of de functie die ze gebruiken correct functioneert of bugs ervaart.

### [Ontwerp stromen](#ontwerp-stromen)[](#ontwerp-stromen)

Meerdere interacties zijn vaak vereist voor een speler om een doel te voltooien. UX-ontwerpers zijn bezorgd over hoe spelers van de ene actie of UI-scherm of keuze naar de andere navigeren en zorgen ervoor dat deze paden logisch en handig zijn.

Bijvoorbeeld, om een item op een avatar in [Berry Avenue RP](https://www.roblox.com/games/8481844229/)  uit te rusten, moet een speler:

-

De Avatar-knop vinden en erop tikken

-

Een itemcategorie selecteren (gezicht, hoofd, nek, enz.)

-

Scrollen om een interessant item te vinden

-

Op het item tikken om het op hun avatar uit te rusten

-

De Voltooid-knop vinden en erop tikken om de avatar-aanpassing te verlaten

Avatar-aanpassingsstroom in [Berry Avenue RP](https://www.roblox.com/games/8481844229/)

Deze stappen samen vertegenwoordigen de avatar-aanpassingsstroom. Deze stroom is eenvoudig en rechttoe rechtaan, met zo min mogelijk stappen die nodig zijn om een item uit te rusten. Omdat spelers niet veel acties hoeven uit te voeren of te veel hoeven na te denken over wat ze moeten doen, is deze stroom laag in * frictie* , een maatstaf voor de inspanning die nodig is om een doel te bereiken.

Het ontwerpen van efficiënte, laag-frictie stromen vereist zorgvuldige overweging van gebruiksgevallen. Die gebruiksgevallen kunnen worden uitgedrukt als spelersdoelen zoals:

-

Snel een avatar willen kunnen aanpassen

-

Items gemakkelijk vinden tijdens het aanpassen

-

Items voorafgaand aan selectie bekijken

-

Eenvoudige itemverwijdering na selectie

Deze doelen begeleiden vervolgens het UI- en UX-ontwerp van de functie:

-

Spelers krijgen toegang tot de avatar-aanpassingsfunctie via een prominente knop op de HUD, en kunnen onmiddellijk beginnen met het uitrusten van items op hun avatars

-

Tabs sorteren de items in handige categorieën, en het zoekveld stelt spelers in staat om items direct te zoeken

-

Items worden onmiddellijk op de avatar weergegeven

-

Spelers kunnen het item verwijderen door er opnieuw op te tikken om het te deselecteren, of erop te tikken in de lijst met uitgeruste items

Ontwerpers kunnen dan beginnen met het lay-out van de UI en de stappen plannen die spelers zullen nemen om het doel van het aanpassen van hun avatars te voltooien. Dit proces kan worden ondersteund door het gebruik van een * stroomdiagram* , dat visueel de acties van de spelers afbeeldt terwijl ze door de UI navigeren. Deze diagrammen kunnen helpen om over het hoofd geziene stappen, pijnpunten waar de stappen onduidelijk of ongemakkelijk zijn, en overmatige frictie te identificeren.

![](https://prod.docsiteassets.roblox.com/assets/game-design/ui-ux-design/ui-ux-design-17.png)  Voorbeeld van een stroomdiagram.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
