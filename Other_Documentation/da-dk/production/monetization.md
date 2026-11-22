<!-- Source: https://create.roblox.com/docs/da-dk/production/monetization -->

Monetisering | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)

# Monetisering

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Monetisering er en del af Roblox's overordnede struktur for at give værdi til skabere. Der er flere forskellige tilgange til at monetisere dit indhold, herunder at udnytte [abonnementer](#abonnementer) , opkræve et adgangsgebyr i [Robux](#betalt-adgang-i-robux)  eller [lokal valuta](#betalt-adgang-i-lokal-valuta) , tilbyde [genstande eller evner, som brugere kan købe](#udviklerprodukter) , tilbyde [private servere](#private-servere)  til brugere, der kun vil spille med venner, og [sælge modeller og plugins](/docs/en-us/production/creator-store#distribute-and-sell-assets)  til andre skabere i Creator Store.

Hvis du vælger at tilbyde købeligt indhold, registrerer Roblox ikke automatisk produkt- eller købsoplysninger. For at forhindre datatab skal du omhyggeligt opbevare disse data ved hjælp af [DataStoreService](/docs/en-us/reference/engine/classes/DataStoreService)  eller en anden datalagringstjeneste, der er hostet uden for Roblox.

For en dybdegående gennemgang af design af optimale monetiseringsstrategier for din oplevelse, se [Monetiseringsfundamenter](/docs/en-us/production/game-design/monetization-foundations) .

## [Monetiseringsstrategier](#monetiseringsstrategier)[](#monetiseringsstrategier)

Vær opmærksom på de monetiseringsmetoder, du introducerer i dit spil, da vores brugere sandsynligvis vil downvote  dit spil, hvis de ikke godkender dine strategier. Desuden skal alle udviklere være gennemsigtige med enhver [chancebaseret monetisering](/docs/en-us/production/monetization/paid-random-items)  og bruge disse mekanikker ansvarligt.

Nogle populære monetiseringsstrategier for gratis-spil på andre platforme anbefales ikke til Roblox. For eksempel kan aftalemechanik og timere, der kan fjernes eller fremskyndes, fungere godt på andre platforme, men disse mekanikker er upopulære blandt Roblox-brugere, der har problemer med, at deres sjov kommer til en for tidlig ende.

Følgende bedste praksis forslag er populære blandt topudviklere til at skræddersy monetiseringsstrategier til Roblox-platformen og publikum.

Bemærk venligst, at ved at anvende disse teknikker og overvejelser, er du ikke garanteret at kunne monetisere dit spil effektivt. Husk, at du ikke behøver at have nogen økonomiske mål for at have det sjovt med at skabe et Roblox-spil.

### [Turister og lokale](#turister-og-lokale)[](#turister-og-lokale)

Det kan være nyttigt at tænke på Roblox-brugere i to kategorier:

-

Turister  hopper typisk fra et spil til et andet og prioriterer variation frem for dybde. De foretrækker genstande med umiddelbare effekter, enten ved at gøre gameplay sjovere eller ved at få dem til at skille sig ud, hvilket inviterer andre brugere til at spørge, hvordan og hvor de fik genstanden.

-

Lokale  er mere tilbøjelige til at fokusere på et bestemt spil eller et mindre sæt af spil. De engagerer sig dybere og danner typisk næsten hele et spils engagerede brugerbase. De er mere interesserede i genstande med langsigtede fordele, såsom et [battle pass](/docs/en-us/production/game-design/season-pass-design) .

For at lære mere om, hvordan du designer dit spil med Roblox-brugere i tankerne, se [Design for Roblox](/docs/en-us/production/game-design/design-for-roblox) .

### [Sociale funktioner](#sociale-funktioner)[](#sociale-funktioner)

Roblox-brugere har tendens til at nyde spil, der understreger social interaktion. For eksempel kan det at have genstande eller begivenheder, der kun er tilgængelige i en begrænset tid , skabe spænding omkring det indhold. Et handels system opfordrer brugere til at interagere. Mens begge systemer kan være succesfulde på egen hånd, er de særligt effektive, når de kombineres.

### [Live ops](#live-ops)[](#live-ops)

Support efter lancering er på mange måder lettere på Roblox end på andre platforme, da du hurtigt kan sende opdateringer for at forbedre dit spil.

Hyppige  indholdsopdateringer kan være nyttige, hvis du vil opretholde engagementet med dit spil over tid. Roblox-brugere er vant til at blive engageret af regelmæssige opdateringer, og det kan være meget sværere at genvinde en brugers interesse end at opretholde aktive brugere. En ugentlig rytme  for opdateringer er ideel. Som minimum skal du sigte efter månedlige opdateringer. For en diskussion om indholdsrytme, se Level Up [indholdsrytme workshop](/docs/en-us/production/game-design/content-updates) .

Når du designer opdateringer, skal du holde dem fokuseret på et bestemt tema . Dette gør det lettere for brugerne at forstå den nye opdatering og se, hvilket indhold der er nyt, når de logger ind. Det hjælper også med at koordinere dit indhold og dine promoveringsaktiver. For eksempel, hvis du tilføjer en ny Zoo til dit rollespil, skal du sørge for, at alt nyt indhold har en eller anden forbindelse til Zoo-temaet.

Vær ikke bange for at få brugerne til at tjene deres adgang  til nyt indhold. Nye brugere vil strømme til for at spille nye opdateringer, men hvis de ikke føler, at de har opnået  noget i spillet, kan de tjekke ud kort efter. Du kan skabe en følelse af at tjene en opdatering enten ved at monetisere opdateringsindholdet eller ved at skabe forudsætningsbetingelser for at spille det nye indhold.

For at lære mere om, hvordan du designer effektiv support efter lancering for dit spil, se [Live ops essentials](/docs/en-us/production/game-design/liveops-essentials) .

## [Produkter](#produkter)[](#produkter)

### [Immersive annoncer](#immersive-annoncer)[](#immersive-annoncer)

Systemet med [immersive annoncer](/docs/en-us/production/monetization/immersive-ads)  giver dig mulighed for at indsætte annonceenheder i dit spil, der tillader Roblox at programmere annoncer fra annoncører til dine aktive brugere.

![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/Overview-ImageAd.jpg) Billede annonceformat

Portal annonceformat

### [Roblox Plus](#roblox-plus)[](#roblox-plus)

[Roblox Plus](/docs/en-us/production/monetization/roblox-plus)  giver dig mulighed for at tjene penge gennem øgede køb i spillet drevet af Roblox-subsiderede bruger rabatter, tilmeldingsbonusser for hver ny abonnent, du bringer ind, og engagement i betalte private servere.

### [Abonnementer](#abonnementer)[](#abonnementer)

[Abonnementer](/docs/en-us/production/monetization/subscriptions)  inden for spil giver dig mulighed for at tilbyde brugere tilbagevendende fordele for et månedligt gebyr.

![](https://prod.docsiteassets.roblox.com/assets/monetization/subscriptions/Example-Subscriptions.png) Eksempler på spilabonnementer

### [Passer](#passer)[](#passer)

Et [pass](/docs/en-us/production/monetization/passes)  giver dig mulighed for at opkræve et engangs Robux-gebyr  for at brugere kan få adgang til særlige privilegier inden for et spil, såsom adgang til et begrænset område, en in-game avatar genstand eller en permanent power-up.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/passes/passes-sample.png)

### [Udviklerprodukter](#udviklerprodukter)[](#udviklerprodukter)

Et [udviklerprodukt](/docs/en-us/production/monetization/developer-products)  er en genstand eller evne, som en bruger kan købe mere end én gang, såsom in-game valuta, ammunition eller potioner. Du kan opfordre til køb, registrere dem og få produktinformation gennem scripting.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/developer-products/Buy-Product-Example.jpg)

### [Administreret prissætning](#administreret-prissætning)[](#administreret-prissætning)

[Administreret prissætning](/docs/en-us/production/monetization/managed-pricing)  er et samlet system, der bringer [regional prissætning](/docs/en-us/production/monetization/regional-pricing)  og [prisoptimering](/docs/en-us/production/monetization/price-optimization)  sammen ét sted. Du tilmelder dig én gang, vælger hvilke genstande der skal inkluderes, og Administreret prissætning holder dine priser optimeret på tværs af produkter og regioner over tid.

### [Prisoptimering](#prisoptimering)[](#prisoptimering)

[Prisoptimering](/docs/en-us/production/monetization/price-optimization)  giver dig mulighed for at finde de bedste prisniveauer for dine passer og udviklerprodukter, hvilket kan hjælpe dig med at tjene flere penge over tid, mens du holder dine priser konkurrencedygtige.

### [Betalt adgang i Robux](#betalt-adgang-i-robux)[](#betalt-adgang-i-robux)

[Betalt adgang i Robux](/docs/en-us/production/monetization/paid-access-robux)  giver dig mulighed for at opkræve brugere et engangs Robux-gebyr  for at få adgang til dit spil. Nogle udviklere bruger midlertidigt denne funktion til at oprette en lukket beta, hvor deres mest engagerede brugere kan få tidlig adgang til et spil og hjælpe med test og feedback.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/paid-access/Buy-Access-Example.png)

### [Betalt adgang i lokal valuta](#betalt-adgang-i-lokal-valuta)[](#betalt-adgang-i-lokal-valuta)

[Betalt adgang i lokal valuta](/docs/en-us/production/monetization/paid-access-local-currency)  giver dig mulighed for at opkræve brugere et engangsgebyr i deres lokale valuta  for at få adgang til dit spil. Hvis deres lokale valuta ikke er tilgængelig, opkræves de i USD. Nogle udviklere bruger midlertidigt denne funktion til at oprette en lukket beta, hvor deres mest engagerede brugere kan få tidlig adgang til et spil og hjælpe med test og feedback.

### [Private servere](#private-servere)[](#private-servere)

En [privat server](/docs/en-us/production/monetization/private-servers)  er en abonnementsbaseret funktion, der giver en bruger mulighed for at bestemme, hvem der kan spille et spil med dem. Mens private servere kan være gratis, kan du også bruge private servere som en metode til monetisering ved at opkræve brugere, der ønsker at få adgang til private servere et månedligt Robux-gebyr .

### [Kataloggebyrer og provisioner](#kataloggebyrer-og-provisioner)[](#kataloggebyrer-og-provisioner)

Du kan oprette og sælge tilbehør og tøj på Marketplace. Efter at du har betalt uploadgebyret og indsendt et nyt aktiv til godkendelse, gennemgår moderationsteamet dit aktiv, og hvis det godkendes, tilføjer de dit aktiv til kataloget.

Du vil modtage en [provision](/docs/en-us/marketplace/marketplace-fees-and-commissions)  hver gang brugere køber dit katalogelement. Hvis brugere køber dit katalogelement inden for et spil ved hjælp af [avatarinspektionsmenuen](/docs/en-us/players/avatar-inspect-menu)  eller [avatarredigeringsservicen](/docs/en-us/players/avatar-editor) , modtager spillets ejer også en provision.

### [Plugins og modeller](#plugins-og-modeller)[](#plugins-og-modeller)

Et [plugin](/docs/en-us/studio/plugins)  er en udvidelse, der tilføjer yderligere funktionalitet til Studio, og en [model](/docs/en-us/parts/models)  er en genanvendelig aktivtype. Du kan tilbyde begge til andre skabere i [Creator Store](/docs/en-us/production/creator-store)  gratis, eller du kan sælge dem for amerikanske dollars  (minimumsprisen er $4.99 for plugins og $2.99 for modeller). Roblox tilbyder en markedsledende indtægtsandel for disse salg, da kun skatter og betalingsbehandlingsgebyrer trækkes fra. For mere information om salg af plugins og modeller, se [Creator Store - Distribuer og sælg aktiver](/docs/en-us/production/creator-store#distribute-and-sell-assets) .

Der er en 30 dages escrow-hold for hvert køb. Roblox holder din andel af salget i 30 dage, startende fra salgsdatoen.

## [Retningslinjer](#retningslinjer)[](#retningslinjer)

Når du designer og implementerer monetiseringsprodukter i dine spil, skal du overveje følgende retningslinjer for at sikre, at dine monetiseringsmetoder er egnede for alle publikum på platformen.

### [Præsentation af produkter](#præsentation-af-produkter)[](#præsentation-af-produkter)

For at opretholde sikkerhed og retfærdighed skal du præsentere monetiseringsprodukter på en måde, der er gennemsigtig, ærlig og brugervenlig. For eksempel, hvis du tilbyder rabatter, skal de være ægte  og retfærdige :

-

En rabat er ikke ægte, hvis en genstand altid er "på tilbud" for det samme beløb af Robux.

-

En rabat er ikke retfærdig, hvis den kun tilbydes i meget kort tid, hvilket presser brugerne til at foretage et køb så hurtigt som muligt.

Brugere må aldrig blive vildledt, forvirret eller presset til køb på måder, de ikke havde til hensigt, og de skal altid have friheden til at træffe et klart, bevidst valg om at få et abonnement eller bruge Robux på en bestemt genstand. Som generel vejledning er der nogle praksisser, der altid skal undgås, når du præsenterer monetiseringsprodukter for dit publikum:

-

Påstå ikke, at et abonnement eller en genstand næsten er udsolgt eller kun er tilgængelig i kort tid, hvis det ikke er sandt.

-

Brug ikke en nedtællingstimer, der ikke er nøjagtig eller automatisk genstarter for den samme genstand.

For eksempel, hvis dit spil inkluderer et "dagens tilbud", der siger, at det kun er tilgængeligt i 24 timer, men så viser du den samme besked til brugerne hver gang, de logger ind, og det stopper aldrig med at være tilgængeligt, har du skabt en falsk følelse af hast, der ikke er brugervenlig.

### [Promovering til globale publikum](#promovering-til-globale-publikum)[](#promovering-til-globale-publikum)

Roblox er et globalt fællesskab for brugere i alle aldre, så kampagner inden for dine spil skal som standard være egnede for alle publikum. Hvis visse monetiseringsprodukter er begrænset i visse lokationer, såsom betalte tilfældige genstande, giver Roblox [PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  API til at hjælpe dig med at sikre, at disse produkter kun er synlige for berettigede brugere.

[PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  returnerer, om en bruger er berettiget til specifikke genstande eller funktioner i henhold til deres placering, alder og platform. Du skal integrere denne API i dit spil for at opfylde dine overholdelsesforpligtelser, herunder at bestemme, om hver bruger er:

-

Berettiget til at købe abonnementer eller handelsprodukter.

-

Tilladt betalte tilfældige genstande, betalt genstandsbytte eller at se immersive annoncer.

Hvis en bruger kan bruge Robux eller noget andet, der blev erhvervet med Robux, til at få en tilfældig belønning, er du forpligtet til at bruge [PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  til at blokere denne funktion for brugere, der ikke har tilladelse til at bruge tilfældige genstande i bytte for Robux.

Som generel vejledning, undgå at bruge påtrængende eller hastige beskeder, når du interagerer med mindreårige, da højt trykssprog kan være overvældende:

| ** Sprog at undgå** | | ** Anbefalede alternativer** |
| --- | --- |
| "FÅ DET NU" | | "Se genstand" |
| "SIDSTE CHANCE, HANDL NU" | | "Se pris" |
| "KØB FØR DET ER VÆK!" | | "Åbn butik" |

## [Yderligere lokaliseringer for denne side](#yderligere-lokaliseringer-for-denne-side)[](#yderligere-lokaliseringer-for-denne-side)

For yderligere, lokaliserede versioner af denne side, der ikke er tilgængelige i sidens sprogvælger, se følgende links:

-

[Bulgarian (български)](https://create.roblox.com/docs/bg-bg/production/monetization)

-

[Croatian (hrvatski)](https://create.roblox.com/docs/hr-hr/production/monetization)

-

[Czech (čeština)](https://create.roblox.com/docs/cs-cz/production/monetization)

-

[Danish (dansk)](https://create.roblox.com/docs/da-dk/production/monetization)

-

[Dutch (Nederlands)](https://create.roblox.com/docs/nl-nl/production/monetization)

-

[Estonian (eesti)](https://create.roblox.com/docs/et-ee/production/monetization)

-

[Finnish (suomi)](https://create.roblox.com/docs/fi-fi/production/monetization)

-

[Greek (Ελληνικά)](https://create.roblox.com/docs/el-gr/production/monetization)

-

[Hungarian (magyar)](https://create.roblox.com/docs/hu-hu/production/monetization)

-

[Irish (Gaeilge)](https://create.roblox.com/docs/ga-ie/production/monetization)

-

[Latvian (latviešu)](https://create.roblox.com/docs/lv-lv/production/monetization)

-

[Lithuanian (lietuvių)](https://create.roblox.com/docs/lt-lt/production/monetization)

-

[Maltese (Malti)](https://create.roblox.com/docs/mt-mt/production/monetization)

-

[Portuguese - Portugal (português)](https://create.roblox.com/docs/pt-pt/production/monetization)

-

[Romanian (română)](https://create.roblox.com/docs/ro-ro/production/monetization)

-

[Slovak (slovenčina)](https://create.roblox.com/docs/sk-sk/production/monetization)

-

[Slovenian (slovenščina)](https://create.roblox.com/docs/sl-si/production/monetization)

-

[Swedish (svenska)](https://create.roblox.com/docs/sv-se/production/monetization)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
