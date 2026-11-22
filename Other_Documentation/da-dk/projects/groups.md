<!-- Source: https://create.roblox.com/docs/da-dk/projects/groups -->

Grupper (hold) | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Projects](/docs/en-us/projects)
6. /
7. [Work in teams](/docs/en-us/projects/groups)

# Grupper (hold)

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

En Roblox gruppe  giver flere skabere mulighed for at arbejde på det samme spil, bruge de samme aktiver, dele overskud og give kredit til alle bidragsydere.

Ejerskab af grupper af spil hjælper skabere med at samarbejde og fungere som uafhængige studier. Hvis der opstår en konflikt inden for en gruppe, kan Roblox ikke hjælpe med at mægle eller løse uenigheder.

## [Oprettelse af gruppe](#oprettelse-af-gruppe)[](#oprettelse-af-gruppe)

At oprette en gruppe koster 100 Robux. Du kan administrere dens [roller og tilladelser](#roller-og-tilladelser)  fra [Creator Dashboard](https://create.roblox.com/dashboard/creations)  eller [Fællesskaber](https://www.roblox.com/communities) .

Før du opretter en gruppe, skal du omhyggeligt læse [reglerne og forventningerne](/docs/en-us/projects/group-guidelines)  for gruppeadministration.

For at oprette en ny gruppe:

1.

Naviger til [Creator Dashboard](https://create.roblox.com/dashboard/creations) , udvid kontovælgeren i øverste venstre hjørne, og klik på plus (+)  knappen.

2.

På siden Opret gruppe  skal du uploade et billede til gruppens logo og indtaste gruppens navn.

3.

Når du er klar, skal du klikke på Køb  knappen. Når gruppen er oprettet, bliver du sendt til gruppens profilside, hvor du kan ændre gruppens oplysninger, herunder tilføje op til tre sociale links.

## [Roller og tilladelser](#roller-og-tilladelser)[](#roller-og-tilladelser)

Gruppemedlemmer kan tildeles en eller flere roller  inden for en gruppe, og hver rolle har tilladelser , der specificerer medlemmernes evner.

Rollekonfiguration er kun tilgængelig, hvis du er gruppeejer, eller hvis du har tilladelse til at oprette, konfigurere og tildele grupperoller.

For at administrere tildelinger af grupperoller programmatisk fra en spilleserver, brug [HttpService](/docs/en-us/reference/engine/classes/HttpService)  til at kalde de understøttede Open Cloud Groups-endepunkter. For opsætning og eksempler på kode, se [Brug med Open Cloud](/docs/en-us/cloud-services/http-service#use-with-open-cloud) .

1.

Fra [Creator Dashboard](https://create.roblox.com/dashboard/creations) , udvid kontovælgeren i øverste venstre hjørne og vælg gruppen.

2.

Udvid kontovælgeren igen og vælg Roller .

3.

For hver rolle skal du omhyggeligt bekræfte tilladelserne under Permissions  fanen.

Tilladelser er organiseret i General , Creation , og Community  kategorier. De følgende sektioner beskriver de tilladelser, der er tilgængelige i hver kategori.

### [Generelt](#generelt)[](#generelt)

Generelle tilladelser

| Manage roles | | Medlemmer med denne tilladelse kan oprette, redigere, slette, omarrangere og tildele eller fjerne roller under deres højeste rolle. De kan kun redigere tilladelser, de allerede har. |
| --- | --- |
| Assign or remove roles from members | | Medlemmer med denne tilladelse kan tildele eller fjerne roller under deres højeste rolle til ethvert medlem. |
| Invite or approve members | | Medlemmer med denne tilladelse kan invitere personer til gruppen og godkende anmodninger om at deltage. |
| Kick members | | Medlemmer med denne tilladelse kan fjerne medlemmer, hvis deres højeste rolle er under deres egen. |
| Ban members | | Medlemmer med denne tilladelse kan udelukke medlemmer, hvis deres højeste rolle er under deres egen. |
| Configure group profile | | Medlemmer med denne tilladelse kan konfigurere gruppeprofilen. |
| View audit logs | | Medlemmer med denne tilladelse kan se [gruppe revisionslogger](#gruppe-revisionslogger) . |
| Manage allies and enemies | | Medlemmer med denne tilladelse kan administrere gruppens allierede og fjender. |

### [Oprettelse](#oprettelse)[](#oprettelse)

Creations

| Playtest experiences | | Medlemmer med denne rolle kan spille alle spil, der ejes af gruppen, selvom de ikke er frigivet til et bredere publikum. Valgfrit tilgængelig som en [per-spil tilladelse](/docs/en-us/projects/configure-games) . |
| Edit experiences | | Medlemmer med denne rolle kan redigere alle spil og [aktiver](/docs/en-us/projects/assets) , der ejes af gruppen, og bruge alle funktioner i [Data Stores Manager](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Inkluderer ikke redigering af et spil uden for en [samarbejdende](/docs/en-us/projects/collaboration)  session eller gemme et sted fra ét spil til et andet spil. Valgfrit tilgængelig som en [per-spil tilladelse](/docs/en-us/projects/configure-games) . |
| Publish experiences | | Medlemmer med denne rolle kan både redigere spil, som ovenfor, og også offentliggøre spil til Roblox. Valgfrit tilgængelig som en [per-spil tilladelse](/docs/en-us/projects/configure-games) . |
| Manage share links | | Medlemmer med denne rolle kan oprette/konfigurere [delingslinks](/docs/en-us/production/promotion/share-links) . |
| Manage experience events | | Medlemmer med denne rolle kan oprette/konfigurere [oplevelsesbegivenheder](/docs/en-us/production/promotion/experience-events) . |
| Moderate experiences | | Medlemmer med denne rolle kan se alle in-game chatbeskeder (kun læse; medlemmet skal være 18+) og udelukke eller administrere udelukkede brugere på tværs af alle spil, der ejes af gruppen. |
| Manage monetization for experiences | | Medlemmer med denne rolle kan administrere monetisering produkter såsom [passes](/docs/en-us/production/monetization/passes) , [udviklerprodukter](/docs/en-us/production/monetization/developer-products) , [abonnementer](/docs/en-us/production/monetization/subscriptions)  og mere. Valgfrit tilgængelig som en [per-spil tilladelse](/docs/en-us/projects/configure-games) . |
| Manage secrets for experiences | | Medlemmer med denne rolle kan se listen over [hemmeligheder](/docs/en-us/cloud-services/secrets)  og kan oprette, opdatere og slette hemmeligheder for alle spil, der ejes af gruppen. Medlemmer med denne rolle kræver Edit experiences  tilladelse for at se Secrets-siden. Valgfrit tilgængelig som en [per-spil tilladelse](/docs/en-us/projects/configure-games) . |

Analytics

| View analytics for experiences | | Medlemmer med denne rolle kan få adgang til [analyse](/docs/en-us/production/analytics)  af alle spil, der ejes af gruppen, selvom de ikke har redigeringstilladelse. Valgfrit tilgængelig som en [per-spil tilladelse](/docs/en-us/projects/configure-games) . |
| Manage alerts | | Medlemmer med denne rolle kan oprette og administrere analysealarmer. Par denne tilladelse med View analytics for experiences  for at se alarmnotater direkte på metrikker. |

Monetization

| View group revenue | | Medlemmer med denne rolle kan se gruppens Robux-balance, eventuelle konfigurerede tilbagevendende splitbetalinger og indtægtslogfunktioner. |
| Manage and spend group revenue | | Medlemmer med denne rolle kan se alle gruppeindtægter, som ovenfor, og også administrere dem direkte. Dette inkluderer opsætning af [tilbagevendende udbetalinger](#tilbagevendende-udbetalinger)  og sende [engangsudbetalinger](#engangsudbetalinger)  til samarbejdspartnere. |
| Create ad campaigns for the group | | Medlemmer med denne rolle kan annoncere gruppen. |

Avatar items

| Create avatar items | | Medlemmer med denne rolle kan oprette avatarartikler såsom tøj. |
| Configure avatar items | | Medlemmer med denne rolle kan konfigurere salgsoplysninger, genopfyldninger og sponsorater for eksisterende gruppeavatarartikler. |

API

| Manage API keys | | Medlemmer med denne rolle kan administrere [Open Cloud API-nøgler](/docs/en-us/cloud/auth/api-keys)  for gruppen. |

Development items

| View development items | | Medlemmer med denne rolle kan se udviklingsartikler, der ejes af gruppen, for eksempel Lyd . |
| Manage development items | | Medlemmer med denne rolle kan uploade og konfigurere aktiver udviklingsartikler såsom Decals . |
| Manage development item permissions | | Medlemmer med denne rolle kan konfigurere tilladelser for udviklingsartikler, for eksempel lyddeling. |

Data Stores

| View Data Stores for experiences | | Medlemmer med denne rolle kan se datalagre for alle gruppe-spil gennem [Data Stores Manager](/docs/en-us/cloud-services/data-stores/data-stores-manager) , men de kan ikke slette data. Valgfrit tilgængelig som en [per-spil tilladelse](/docs/en-us/projects/configure-games) . |
| Edit Data Stores for experiences | | Medlemmer med denne rolle kan slette specifikke nøgler inden for datalagre for alle gruppe-spil gennem [Data Stores Manager](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Valgfrit tilgængelig som en [per-spil tilladelse](/docs/en-us/projects/configure-games) . |
| Delete Data Stores for experiences | | Medlemmer med denne rolle kan slette hele datalagre for alle gruppe-spil gennem [Data Stores Manager](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Valgfrit tilgængelig som en [per-spil tilladelse](/docs/en-us/projects/configure-games) . |

Notifications

| Manage webhooks for experiences | | Medlemmer med denne rolle kan liste, oprette, opdatere og slette webhooks for alle gruppeoplevelser. |

Communication

| Manage support tickets for experiences | | Medlemmer med denne rolle kan administrere supportbilletter for alle gruppeoplevelser. |

Legacy

| Administrer adgang til denne gruppes ressourcer | | Medlemmer med denne rolle kan oprette og redigere adgang til gruppens ressourcer. |

### [Fællesskab](#fællesskab)[](#fællesskab)

Posts

| View community announcements | | Medlemmer med denne rolle kan se fællesskabsmeddelelser. |
| Create community announcements | | Medlemmer med denne rolle kan oprette fællesskabsmeddelelser. |

Forums

| Manage categories | | Medlemmer med denne rolle kan administrere forumkategorier. |
| Create posts | | Medlemmer med denne rolle kan oprette forumindlæg. |
| Remove posts | | Medlemmer med denne rolle kan fjerne forumindlæg. |
| Lock posts | | Medlemmer med denne rolle kan låse forumindlæg. |
| Pin posts | | Medlemmer med denne rolle kan fastgøre forumindlæg. |
| Create comments | | Medlemmer med denne rolle kan oprette kommentarer på forumindlæg. |
| Remove comments | | Medlemmer med denne rolle kan fjerne kommentarer fra forumindlæg. |

Content moderation

| View content moderation | | Medlemmer med denne rolle kan se indholdsmoderation. |
| Manage content moderation | | Medlemmer med denne rolle kan administrere indholdsmoderation. |

Miscellaneous

| Bypass slow mode | | Medlemmer med denne rolle kan omgå langsom tilstand. |
| View community analytics | | Medlemmer med denne rolle kan se fællesskabsanalyse. |

4.

VIGTIGT

 Klik på Save  knappen for at anvende tilladelsesindstillingerne.

5.

VALGFRIT

 Klik på Settings  fanen og vælg en farve og synlighedsindstilling for rollen, og klik derefter på Save  knappen.

En roles Settings  sektion er også, hvor gruppeejere og medlemmer med tilstrækkelige tilladelser kan fjerne en rolle helt gennem Slet rolle  knappen.

Roller er listet i hierarkisk rækkefølge: en rolle højere på listen har mere autoritet end en rolle under den. Denne rækkefølge er vigtig, fordi nogle tilladelser kun lader medlemmer administrere roller under deres egen højeste rolle.

Hver rolle er enten offentlig  eller privat . Offentlige roller kan vises på en fællesskabsside og i oplevelser. Private roller vises kun på rolle- og tilladelsesadministrationsflader for autoriserede medlemmer eller for medlemmer, der har den private rolle. Synlighed ændrer, hvor en rolle vises; det ændrer ikke de tilladelser, rollen giver.

For at give Manage roles , Assign or remove roles from members , Manage access to this group’s resources , Manage and spend group revenue , eller Delete Data Stores for experiences , skal du have to-trins verifikation aktiveret.

## [Administrer medlemmer](#administrer-medlemmer)[](#administrer-medlemmer)

Medlemkonfiguration er kun tilgængelig, hvis du er gruppeejer, eller hvis du har tilladelse til at administrere andre medlemmer og deres roller.

For at administrere medlemmer fra Creator Dashboard:

1.

Udvid kontovælgeren i øverste venstre hjørne og vælg gruppen.

2.

Udvid kontovælgeren igen og vælg Members .

3.

Brug Medlem  fanen til at søge efter eksisterende medlemmer eller filtrere dem efter rolle. Brug Inviteret  fanen til at gennemgå ventende invitationer.

For at tilføje et medlem, klik på Invite  knappen og søg efter deres brugernavn. Roblox underretter inviterede skabere i henhold til deres notifikationspræferencer. Du kan også kopiere gruppens link og dele det direkte.

### [Administrer roller](#administrer-roller)[](#administrer-roller)

Du kan administrere tildelinger af roller fra enten Members  siden eller en specifik rolle:

-

På Members  siden, klik på plus (+)  knappen ved siden af et medlem for at åbne rollemenuen. For at tildele en rolle, klik på plus (+)  knappen ved siden af den under Tilføj roller . For at fjerne en rolle, klik på minus (-)  knappen ved siden af den under Nuværende roller , eller klik på ×  knappen på en tildelt rolle ved siden af medlemmets navn.

-

På Roller  siden, vælg en rolle og åbn dens Members  fanen. Klik på Add members  knappen for at søge efter gruppemedlemmer og tildele dem til rollen. For at fjerne en medlem, klik på minus (-)  knappen i slutningen af deres række.

### [Medlemsfjernelse](#medlemsfjernelse)[](#medlemsfjernelse)

For at fjerne et medlem fra gruppen, klik på ⋮  knappen i slutningen af deres række, vælg Kick bruger , og bekræft handlingen.

## [Administrer udbetalinger](#administrer-udbetalinger)[](#administrer-udbetalinger)

Hvis du er gruppeejer, eller hvis du har den korrekte [tilladelse](#roller-og-tilladelser)  inden for Gruppe Indtægter , finder du en Udbetalinger  side under Finanser  i venstre navigation. Her kan du sende engangsudbetalinger samt definere procentandele med andre medlemmer.

Nogle grupper har muligvis ikke denne side låst op i starten af forskellige årsager, såsom gruppens alder eller utilstrækkelige midler til udbetaling.

Udbetalinger kan ikke deles mellem gruppemedlemmer for spil, der opkræver [betalt adgang i lokal valuta](/docs/en-us/production/monetization/paid-access-local-currency) .

### [Engangsudbetalinger](#engangsudbetalinger)[](#engangsudbetalinger)

Engangsudbetalinger kan foretages til medlemmer i en batch, hvor der vælges et bestemt beløb for hver. Sikkerhedsfunktioner inkluderer 2FA-udfordringer, bekræftelsesdialoger og kontroller omkring berettigelsen af medlemmer, der får udbetalt.

 ![Engangsudbetalingsknap angivet i udbetalingsafsnittet på Creator Dashboard.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-One-Time.png)

Når du klikker på Send Robux  knappen, kan du vælge udbetalingsmodtagere fra popup-vinduet eller uploade en .csv  regnearksfil med kolonnerne userId  og payoutInRobux , for eksempel:

| userId | | payoutInRobux |
| 012345 | | 5000 |
| 098765 | | 7000 |

### [Tilbagevendende udbetalinger](#tilbagevendende-udbetalinger)[](#tilbagevendende-udbetalinger)

Tilbagevendende udbetalinger kan også foretages på tværs af hele gruppen og  per-spil, hvor der tildeles en procentdel udbetaling til hvert medlem, før resten går ind i gruppens samlede balance.

 ![Split udbetalingsknapper angivet i udbetalingsafsnittet på Creator Dashboard.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Split-Options.png)

Overvej følgende scenarie, hvor et gruppe-spil Laser Maze  er delt 40%–30%–10% blandt tre medlemmer, med en rest på 20%.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-A.png)

Antag, at spillet tjener 1000 Robux, modtager de tre medlemmer henholdsvis 400, 300 og 100 Robux (40%–30%–10%).

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-B.png)

De resterende 200 Robux (20% af spilfordelingen) går videre til gruppens split  procenter, defineret til 20%–20%–10% blandt de samme tre medlemmer; de modtager yderligere 40, 40 og 20 Robux henholdsvis.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-C.png)

De resterende 100 Robux (50% af gruppens split) placeres i gruppens samlede balance.

 ![Eksempel på flowdiagram over, hvordan spilfordelinger distribueres til gruppemedlemmer først, med resten der går ind i gruppens splits for den endelige distribution blandt gruppen.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Splits-Example.png)

Bemærk, at indtægter fra [private server](/docs/en-us/production/monetization/private-servers)  abonnementer ikke ændres, hvis du justerer splitprocenterne på et senere tidspunkt, hvilket betyder, at hvis en spiller køber et privat serverabonnement, vil splitprocenterne på købstidspunktet gælde for det pågældende abonnement for evigt (indtil det annulleres). Denne politik kan ændres i fremtiden.

## [Gruppe revisionslogger](#gruppe-revisionslogger)[](#gruppe-revisionslogger)

Gruppemedlemmer med View audit logs  tilladelsen kan gennemgå gruppeændringer ved hjælp af disse gruppeadministrationsflader:

-

På Creator Dashboard, vælg Aktivitets Historik  under Samarbejde .

-

På Fællesskaber, åbn fællesskabets konfigurationsside og vælg Revisionslog .

Gruppeejere kan bruge disse logfiler til at overvåge aktivitet, der kan overtræde [gruppe retningslinjer](/docs/en-us/projects/group-guidelines) .

## [Beskyttelse af intellektuel ejendom](#beskyttelse-af-intellektuel-ejendom)[](#beskyttelse-af-intellektuel-ejendom)

Gruppemedlemmer med tilladelse til at redigere alle gruppe-spil kan aktivere [Plads Kopiering](/docs/en-us/projects/configure-games#allow-copying)  indstillingen for en oprettelse, hvilket potentielt tillader hele Roblox-fællesskabet at kopiere det og bruge aktiver inden for det. For at hjælpe med at beskytte intellektuel ejendom i en gruppe, bør ejeren eller medlemmer med tilstrækkelige tilladelser:

-

Bekræfte, at hvert medlem er [tildelt den passende rolle](#administrer-roller) .

-

Tjekke, at hver grupperolle har de korrekte [tilladelser](#roller-og-tilladelser) .

-

Bekræfte, at [Plads Kopiering](/docs/en-us/projects/configure-games#allow-copying)  indstillingen er deaktiveret, før private aktiver tilføjes.

## [Yderligere lokaliseringer for denne side](#yderligere-lokaliseringer-for-denne-side)[](#yderligere-lokaliseringer-for-denne-side)

For yderligere, lokaliserede versioner af denne side, der ikke er tilgængelige i webstedets sprogvælger, se følgende links:

-

[Bulgarian (български)](https://create.roblox.com/docs/bg-bg/projects/groups)

-

[Croatian (hrvatski)](https://create.roblox.com/docs/hr-hr/projects/groups)

-

[Czech (čeština)](https://create.roblox.com/docs/cs-cz/projects/groups)

-

[Danish (dansk)](https://create.roblox.com/docs/da-dk/projects/groups)

-

[Dutch (Nederlands)](https://create.roblox.com/docs/nl-nl/projects/groups)

-

[Estonian (eesti)](https://create.roblox.com/docs/et-ee/projects/groups)

-

[Finnish (suomi)](https://create.roblox.com/docs/fi-fi/projects/groups)

-

[Greek (Ελληνικά)](https://create.roblox.com/docs/el-gr/projects/groups)

-

[Hungarian (magyar)](https://create.roblox.com/docs/hu-hu/projects/groups)

-

[Irish (Gaeilge)](https://create.roblox.com/docs/ga-ie/projects/groups)

-

[Latvian (latviešu)](https://create.roblox.com/docs/lv-lv/projects/groups)

-

[Lithuanian (lietuvių)](https://create.roblox.com/docs/lt-lt/projects/groups)

-

[Maltese (Malti)](https://create.roblox.com/docs/mt-mt/projects/groups)

-

[Portuguese - Portugal (português)](https://create.roblox.com/docs/pt-pt/projects/groups)

-

[Romanian (română)](https://create.roblox.com/docs/ro-ro/projects/groups)

-

[Slovak (slovenčina)](https://create.roblox.com/docs/sk-sk/projects/groups)

-

[Slovenian (slovenščina)](https://create.roblox.com/docs/sl-si/projects/groups)

-

[Swedish (svenska)](https://create.roblox.com/docs/sv-se/projects/groups)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
