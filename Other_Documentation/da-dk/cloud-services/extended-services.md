<!-- Source: https://create.roblox.com/docs/da-dk/cloud-services/extended-services -->

Udvidede tjenester | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Cloud services](/docs/en-us/cloud-services/data-stores-vs-memory-stores)

# Udvidede tjenester

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Udvidede tjenester er en løsning, der giver dig mulighed for at administrere servicebrug og betaling ud over Roblox's standardgrænser. Det inkluderer datalagre, hukommelseslagre, tekst-til-tale, tale-til-tekst og beregning.

## [Berettigelseskrav](#berettigelseskrav)[](#berettigelseskrav)

For at bruge udvidede tjenester skal din Roblox-konto:

-

Være [ID-verificeret](/docs/en-us/production/publishing/account-verification#verify-through-government-id)  og være 18 år eller ældre.

-

Være beliggende i et [understøttet land](#underst%C3%B8ttede-lande) .

-

Have en gyldig e-mailadresse tilknyttet.

-

Ikke være i øjeblikket udelukket eller modereret.

-

Acceptere og overholde [servicevilkårene](https://en.help.roblox.com/hc/articles/37967848292500) .

For gruppekonti er det kun gruppeejeren, der skal opfylde berettigelseskravene.

## [Lås op for udvidede tjenester](#lås-op-for-udvidede-tjenester)[](#lås-op-for-udvidede-tjenester)

Hvis du opfylder alle [berettigelseskravene](#berettigelseskrav) , kan du afslutte opsætningen af udvidede tjenester ved at indtaste dine kontooplysninger og betalingsoplysninger. For gruppeejede spil kan kun gruppeejeren låse op for udvidede tjenester og onboarde spillet til det.

For at låse op for og bruge udvidede tjenester:

1.

Gå til [Creator Dashboard](https://create.roblox.com/dashboard/creations) , gå til Skabelser  og vælg et spil.

2.

Gå til Udvidede tjenester .

3.

Hvis du ikke har indtastet dine kontooplysninger og betalingsoplysninger endnu, skal du klikke på Tilføj manglende oplysninger  på topbanneret.

1.

Indtast dine kontooplysninger. Felterne Kontotype , Skatte-ID-type  og Skatte-ID  er valgfrie.

-

Du kan også gå til Finanser  ⟩ Kontoinformation  under sektionen Udvidede tjenester  for at administrere dine kontooplysninger. Du behøver ikke at opdatere noget andet på denne side.

2.

Klik på Næste .

3.

Indtast en betalingsmetode. Du kan indtaste en ny betalingsmetode eller vælge fra de tilgængelige betalingsmuligheder, der allerede er tilknyttet din Roblox-konto.

-

Du kan også gå til Finanser  ⟩ Betalinger  for at tilføje nye betalingsmetoder, eller gå til Finanser  ⟩ Fakturering  for at indstille en ny standard betalingsmetode.

4.

Klik på Gem .

##### Kontostatus

Din konto for udvidede tjenester kan være i en af følgende statusser:

| Status | | Beskrivelse | | Nødvendig handling |
| Normal | | Du kan bruge alle funktioner i udvidede tjenester. | | Ingen handling er nødvendig. |
| --- | --- |
| Forfalden | | Din konto er forfalden, fordi din automatiske betalingsmetode fejlede. Roblox tilbyder en graceperiode på syv dage  før din konto for udvidede tjenester suspenderes. | | Skift din betalingsmetode og prøv en manuel betaling igen, eller vent indtil Roblox forsøger at opkræve din betalingsmetode igen efter graceperioden er udløbet. |
| Suspenderet | | Du kan ikke bruge nogen betalte udvidede tjenester. Du kan dog stadig bruge tjenester med standardgrænser. | | Ret dine berettigelseskrav, tilføj en gyldig betalingsmetode, eller betal manuelt den forfaldne saldo på din konto. |

## [Aktivér en tjeneste](#aktivér-en-tjeneste)[](#aktivér-en-tjeneste)

For at aktivere en tjeneste:

1.

Gå til Udvidede tjenester .

2.

Tænd for den tjeneste, du vil aktivere.

3.

Indtast et månedligt budget for hver relevant ressource under tjenesten. Det mindste månedlige budget, du kan indstille, er $0,50 USD.

Din betalingsmetode opkræves enten ved slutningen af måneden, når en regning genereres, eller når dit forbrug når $10 USD, alt efter hvad der kommer først.

Du kan øge eller mindske en tjenestes månedlige budget når som helst. Din tjeneste bliver automatisk begrænset, hvis du sænker dit budget til et beløb under dit nuværende forbrug til dato, eller hvis du overskrider det budget, du har sat.

Roblox underretter dig via e-mail, når dit forbrug når 80% af dit budget, og igen når det når 100%.

### [Udvidede tjenester til beregning](#udvidede-tjenester-til-beregning)[](#udvidede-tjenester-til-beregning)

Hver spilleserver får et standardbeløb af CPU, som vokser med hver spiller, der tilslutter sig. Udvidede tjenester til beregning  mere end fordobler den per-spiller CPU, som dine spilleservere modtager.

Langt de fleste spil på Roblox ser ingen fordel ved denne tjeneste, men spil med tung server-side fysik eller der gør omfattende brug af [serverautoritet](/docs/en-us/projects/server-authority)  rammer eksisterende grænser. For at se, om dit spil kan drage fordel af Udvidede tjenester til beregning :

-

Tjek [server heartbeat](/docs/en-us/performance-optimization/identify#server-compute)  for vedvarende fald under 60 FPS.

-

Undersøg CPU-kerneudnyttelse på [Performance dashboard](/docs/en-us/production/analytics/performance#server-charts) .

Før du betaler for mere CPU, så prøv at [reducere det arbejde, dine servere udfører](/docs/en-us/performance-optimization/improve) .

## [Administrer fakturering](#administrer-fakturering)[](#administrer-fakturering)

For at få adgang til faktureringsdashboardet for udvidede tjenester:

1.

Gå til Finanser  ⟩ Fakturering .

2.

Vælg fanen Cloud services  for at vise følgende:

-

Din ventende saldo, inklusive omkostningerne indtil dato

-

Din faktureringshistorik, inklusive al fakturering af udvidede tjenester på tværs af dine spil

For en detaljeret opgørelse af dine nuværende ventende saldoomkostninger, klik på Se detaljer  ved siden af din betalingsmetode. For en detaljeret faktura af en tidligere regning, klik på Se regning  under Faktureringshistorik .

## [Tjenestepriser](#tjenestepriser)[](#tjenestepriser)

Se følgende tabel for priser på udvidede tjenester:

| Tjeneste | |  | | Standard | | Udvidet |
| [Hukommelseslagre](https://create.roblox.com/docs/cloud-services/memory-stores) | | Forespørgsler | | 1000 + (CCU × 120) forespørgsler pr. minut | | $0.003 / 1M forespørgsler |
|  | | Lagring | | 64 KB + (CCU × 1.2 KB) | | $0.10 / GB pr. time¹ |
| [Tekst-til-tale](https://create.roblox.com/docs/audio/objects#text-to-speech) | | Forespørgsler | | 1 + (CCU × 6) forespørgsler pr. minut | | $5.00 / 1M forespørgsler |
| [Tale-til-tekst](https://create.roblox.com/docs/audio/objects#speech-to-text) | | Forespørgsler | | 1 + (CCU × 5) forespørgsler pr. minut | | $1 / 1M forespørgsler |
| [Standard datalagre](https://create.roblox.com/docs/cloud-services/data-stores) | | Hent | | 250 + (CCU * 40) forespørgsler pr. minut | | $0.08 / 1M forespørgsler |
|  | | Indstil | | 250 + (CCU * 20) forespørgsler pr. minut | | $0.80 / 1M forespørgsler |
|  | | Liste | | 10 + (CCU * 2) forespørgsler pr. minut | | $0.60 / 1M forespørgsler |
|  | | Fjern | | 100 + (CCU * 40) forespørgsler pr. minut | | $0.80 / 1M forespørgsler |
| [Ordnet datalagre ](https://create.roblox.com/docs/cloud-services/data-stores) | | Hent | | 250 + (CCU * 40) forespørgsler pr. minut | | $0.08 / 1M forespørgsler |
|  | | Indstil | | 250 + (CCU * 20) forespørgsler pr. minut | | $0.25 / 1M forespørgsler |
|  | | GetSorted | | 100 + (CCU * 2) forespørgsler pr. minut | | $0.32 / 1M forespørgsler |
|  | | Fjern | | 100 + (CCU * 40) forespørgsler pr. minut | | $0.25 / 1M forespørgsler |
| [Datalagerlagring ](https://create.roblox.com/docs/cloud-services/data-stores) | | Lagring | | 100 MB + (1 MB * Livstids spillere) GB pr. måned | | $0.12 / GB pr. måned |
| [Beregning ](https://create.roblox.com/docs/production/analytics/performance) | | CPU-kerner | | De første 100K spilletimer pr. måned uden beregning (når tilmeldt udvidede tjenester til beregning) | | $0.001 / spilletime² |

 ¹ GB pr. time = lagringsforbruget ganget med den tid. For eksempel kan 100 GB timer svare til "100 GB × 1 time" eller "200 GB × 0,5 timer".  ² Udvidede tjenester til beregning faktureres baseret på, hvor længe funktionen forbliver aktiveret, målt i minutter af spilletid. Fordi aktivering af funktionen reserverer yderligere beregningskapacitet til dit spil, gælder gebyrer, når funktionen er aktiv, selvom den ekstra beregning ikke er fuldt udnyttet. Spilletimer beregnes som summen af alle spiller-sessioners varighed. For eksempel, hvis 10.000 brugere hver spiller i 1 time, svarer det til 10.000 spilletimer, hvilket resulterer i $10 i gebyrer ud over den inkluderede månedlige tilladelse på 100.000 spilletimer. Disse grænser og priser gælder kun for spil, der er tilmeldt udvidede tjenester til beregning. Spil, der ikke tilmelder sig, fortsætter med at modtage ubegrænsede spilletimer under de nuværende standardgrænser uden yderligere omkostninger.

## [Understøttede lande](#understøttede-lande)[](#understøttede-lande)

Udvidede tjenester er tilgængelige i følgende lande:

| Land |
| Australien | | Tyskland | | Polen |
| Østrig | | Hongkong | | Portugal |
| Belgien | | Ungarn | | Rumænien |
| Brasilien | | Irland | | Singapore |
| Bulgaria | | Italien | | Slovakiet |
| Canada | | Kasakhstan | | Slovenien |
| Chile | | Letland | | Sydafrika |
| Kroatien | | Litauen | | Sydkorea |
| Cypern | | Malaysia | | Spanien |
| Tjekkiet | | Malta | | Sverige |
| Danmark | | Mexico | | Schweiz |
| Estland | | Holland | | Thailand |
| Finland | | New Zealand | | Storbritannien |
| Frankrig | | Norge | | USA |
| Georgien | | Peru | |  |

## [Yderligere lokaliseringer for denne side](#yderligere-lokaliseringer-for-denne-side)[](#yderligere-lokaliseringer-for-denne-side)

For yderligere, lokaliserede versioner af denne side, der ikke er tilgængelige i sidens sprogvælger, se følgende links:

-

[Bulgarisk (български)](https://create.roblox.com/docs/bg-bg/cloud-services/extended-services)

-

[Kroatisk (hrvatski)](https://create.roblox.com/docs/hr-hr/cloud-services/extended-services)

-

[Tjekkisk (čeština)](https://create.roblox.com/docs/cs-cz/cloud-services/extended-services)

-

[Dansk (dansk)](https://create.roblox.com/docs/da-dk/cloud-services/extended-services)

-

[Hollandsk (Nederlands)](https://create.roblox.com/docs/nl-nl/cloud-services/extended-services)

-

[Estisk (eesti)](https://create.roblox.com/docs/et-ee/cloud-services/extended-services)

-

[Finsk (suomi)](https://create.roblox.com/docs/fi-fi/cloud-services/extended-services)

-

[Græsk (Ελληνικά)](https://create.roblox.com/docs/el-gr/cloud-services/extended-services)

-

[Ungarsk (magyar)](https://create.roblox.com/docs/hu-hu/cloud-services/extended-services)

-

[Irsk (Gaeilge)](https://create.roblox.com/docs/ga-ie/cloud-services/extended-services)

-

[Lettisk (latviešu)](https://create.roblox.com/docs/lv-lv/cloud-services/extended-services)

-

[Litauisk (lietuvių)](https://create.roblox.com/docs/lt-lt/cloud-services/extended-services)

-

[Maltesisk (Malti)](https://create.roblox.com/docs/mt-mt/cloud-services/extended-services)

-

[Portugisisk - Portugal (português)](https://create.roblox.com/docs/pt-pt/cloud-services/extended-services)

-

[Rumænsk (română)](https://create.roblox.com/docs/ro-ro/cloud-services/extended-services)

-

[Slovakisk (slovenčina)](https://create.roblox.com/docs/sk-sk/cloud-services/extended-services)

-

[Slovensk (slovenščina)](https://create.roblox.com/docs/sl-si/cloud-services/extended-services)

-

[Svensk (svenska)](https://create.roblox.com/docs/sv-se/cloud-services/extended-services)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
