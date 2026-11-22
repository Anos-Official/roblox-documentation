<!-- Source: https://create.roblox.com/docs/lv-lv/projects/groups -->

Grupas (komandas) | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Projects](/docs/en-us/projects)
6. /
7. [Work in teams](/docs/en-us/projects/groups)

# Grupas (komandas)

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Roblox grupa  ļauj vairākiem veidotājiem strādāt pie vienas spēles, izmantot tos pašus resursus, dalīties peļņā un sniegt kredītu visiem līdzstrādniekiem.

Grupas īpašumtiesības uz spēlēm palīdz veidotājiem sadarboties un darboties kā neatkarīgi studijas. Ja grupā rodas konflikts, Roblox nevar palīdzēt izšķirt vai atrisināt domstarpības.

## [Grupas izveide](#grupas-izveide)[](#grupas-izveide)

Grupas izveide maksā 100 Robux. Jūs varat pārvaldīt tās [lomas un atļaujas](#lomas-un-at%C4%BCaujas)  no [Veidotāja informācijas paneļa](https://create.roblox.com/dashboard/creations)  vai [Kopienām](https://www.roblox.com/communities) .

Pirms grupas izveides rūpīgi izlasiet [noteikumus un gaidas](/docs/en-us/projects/group-guidelines)  grupas pārvaldībai.

Lai izveidotu jaunu grupu:

1.

Dodieties uz [Veidotāja informācijas paneli](https://create.roblox.com/dashboard/creations) , paplašiniet konta pārslēdzēju augšējā kreisajā stūrī un noklikšķiniet uz plus (+)  pogas.

2.

Izveidot grupu  lapā augšupielādējiet attēlu grupas logotipam un ievadiet grupas nosaukumu.

3.

Kad esat gatavs, noklikšķiniet uz Iegādāties  pogas. Kad grupa ir izveidota, jūs tiksiet novirzīts uz grupas profila lapu, kur varat mainīt grupas detaļas, tostarp pievienot līdz trīs sociālos saites.

## [Lomas un atļaujas](#lomas-un-atļaujas)[](#lomas-un-atļaujas)

Grupas dalībniekiem var piešķirt vienu vai vairākas lomas  grupā, un katrai lomai ir atļaujas , kas nosaka tās dalībnieku spējas.

Lomu konfigurācija ir pieejama tikai tad, ja esat grupas īpašnieks vai jums ir atļauja izveidot, konfigurēt un piešķirt grupas lomas.

Lai pārvaldītu grupas lomu piešķiršanu programmatiski no spēles servera, izmantojiet [HttpService](/docs/en-us/reference/engine/classes/HttpService) , lai izsauktu atbalstītās Open Cloud Groups API galapunktus. Lai iegūtu iestatījumus un paraugu kodu, skatiet [Izmantošana ar Open Cloud](/docs/en-us/cloud-services/http-service#use-with-open-cloud) .

1.

No [Veidotāja informācijas paneļa](https://create.roblox.com/dashboard/creations)  paplašiniet konta pārslēdzēju augšējā kreisajā stūrī un izvēlieties grupu.

2.

Atkal paplašiniet konta pārslēdzēju un izvēlieties Lomas .

3.

Katras lomas gadījumā rūpīgi apstipriniet atļaujas Permissions  cilnē.

Atļaujas ir organizētas General , Creation  un Community  kategorijās. Zemāk esošās sadaļas apraksta pieejamās atļaujas katrā kategorijā.

### [Vispārējā](#vispārējā)[](#vispārējā)

Vispārējās atļaujas

| Manage roles | | Dalībnieki ar šo atļauju var izveidot, rediģēt, dzēst, pārvietot un piešķirt vai atņemt lomas zem savas augstākās lomas. Viņi var rediģēt tikai atļaujas, kuras viņi jau tur. |
| --- | --- |
| Assign or remove roles from members | | Dalībnieki ar šo atļauju var piešķirt vai atņemt lomas zem savas augstākās lomas jebkuram dalībniekam. |
| Invite or approve members | | Dalībnieki ar šo atļauju var aicināt cilvēkus pievienoties grupai un apstiprināt pievienošanās pieprasījumus. |
| Kick members | | Dalībnieki ar šo atļauju var izņemt dalībniekus, kuru augstākā loma ir zem viņu pašu. |
| Ban members | | Dalībnieki ar šo atļauju var aizliegt dalībniekus, kuru augstākā loma ir zem viņu pašu. |
| Configure group profile | | Dalībnieki ar šo atļauju var konfigurēt grupas profilu. |
| View audit logs | | Dalībnieki ar šo atļauju var skatīt [grupas audita žurnālus](#grupas-audita-%C5%BEurn%C4%81li) . |
| Manage allies and enemies | | Dalībnieki ar šo atļauju var pārvaldīt grupas sabiedrotos un ienaidniekus. |

### [Izveide](#izveide)[](#izveide)

Creations

| Playtest experiences | | Dalībnieki ar šo lomu var spēlēt visas grupas īpašumā esošās spēles, pat ja tās nav izlaistas plašākai auditorijai. Opcionalitāte pieejama kā [atļauja par spēli](/docs/en-us/projects/configure-games) . |
| Edit experiences | | Dalībnieki ar šo lomu var rediģēt visas grupas īpašumā esošās spēles un [resursus](/docs/en-us/projects/assets)  un izmantot visas funkcijas [Datu veikalu pārvaldniekā](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Neietver spēles rediģēšanu ārpus [sadarbības](/docs/en-us/projects/collaboration)  sesijas vai vietas saglabāšanu no vienas spēles uz citu spēli. Opcionalitāte pieejama kā [atļauja par spēli](/docs/en-us/projects/configure-games) . |
| Publish experiences | | Dalībnieki ar šo lomu var gan rediģēt spēles, kā minēts iepriekš, gan arī publicēt spēles Roblox. Opcionalitāte pieejama kā [atļauja par spēli](/docs/en-us/projects/configure-games) . |
| Manage share links | | Dalībnieki ar šo lomu var izveidot/configure [dalīšanās saites](/docs/en-us/production/promotion/share-links) . |
| Manage experience events | | Dalībnieki ar šo lomu var izveidot/configure [pieredzes notikumus](/docs/en-us/production/promotion/experience-events) . |
| Moderate experiences | | Dalībnieki ar šo lomu var skatīt visus spēles čata ziņojumus (tikai lasīšanai; dalībniekam jābūt 18+) un aizliegt vai pārvaldīt aizliegtos lietotājus visās grupas īpašumā esošajās spēlēs. |
| Manage monetization for experiences | | Dalībnieki ar šo lomu var pārvaldīt monetizācijas produktus, piemēram, [pārejas](/docs/en-us/production/monetization/passes) , [izstrādātāja produktus](/docs/en-us/production/monetization/developer-products) , [abonementus](/docs/en-us/production/monetization/subscriptions)  un citus. Opcionalitāte pieejama kā [atļauja par spēli](/docs/en-us/projects/configure-games) . |
| Manage secrets for experiences | | Dalībnieki ar šo lomu var redzēt [noslēpumu](/docs/en-us/cloud-services/secrets)  sarakstu un var izveidot, atjaunināt un dzēst noslēpumus visām grupas īpašumā esošajām spēlēm. Dalībniekiem ar šo lomu ir nepieciešama Edit experiences  atļauja, lai skatītu Noslēpumu lapu. Opcionalitāte pieejama kā [atļauja par spēli](/docs/en-us/projects/configure-games) . |

Analytics

| View analytics for experiences | | Dalībnieki ar šo lomu var piekļūt [analītikai](/docs/en-us/production/analytics)  visām grupas īpašumā esošajām spēlēm, pat ja viņiem nav rediģēšanas piekļuves. Opcionalitāte pieejama kā [atļauja par spēli](/docs/en-us/projects/configure-games) . |
| Manage alerts | | Dalībnieki ar šo lomu var izveidot un pārvaldīt analītikas brīdinājumus. Apvienojiet šo atļauju ar View analytics for experiences , lai redzētu brīdinājumu anotācijas tieši uz metrikas grafikiem. |

Monetization

| View group revenue | | Dalībnieki ar šo lomu var skatīt grupas Robux bilanci, jebkādas konfigurētas atkārtotas sadales izmaksas un ieņēmumu reģistrēšanas funkcijas. |
| Manage and spend group revenue | | Dalībnieki ar šo lomu var skatīt visus grupas ieņēmumus, kā minēts iepriekš, un arī tieši tos pārvaldīt. Tas ietver [atkārtotu izmaksu](#atk%C4%81rtotas-izmaksas)  iestatīšanu un [vienreizēju izmaksu](#vienreiz%C4%93jas-izmaksas)  nosūtīšanu līdzstrādniekiem. |
| Create ad campaigns for the group | | Dalībnieki ar šo lomu var reklamēt grupu. |

Avatar items

| Create avatar items | | Dalībnieki ar šo lomu var izveidot avatara priekšmetus, piemēram, apģērbu. |
| Configure avatar items | | Dalībnieki ar šo lomu var konfigurēt pārdošanas detaļas, atkārtotas piegādes un sponsorēšanu esošajiem grupas avatara priekšmetiem. |

API

| Manage API keys | | Dalībnieki ar šo lomu var pārvaldīt [Open Cloud API atslēgas](/docs/en-us/cloud/auth/api-keys)  grupai. |

Development items

| View development items | | Dalībnieki ar šo lomu var skatīt attīstības priekšmetus, kas pieder grupai, piemēram, Audio . |
| Manage development items | | Dalībnieki ar šo lomu var augšupielādēt un konfigurēt aktīvu attīstības priekšmetus, piemēram, Decals . |
| Manage development item permissions | | Dalībnieki ar šo lomu var konfigurēt attīstības priekšmetu atļaujas, piemēram, audio koplietošanu. |

Data Stores

| View Data Stores for experiences | | Dalībnieki ar šo lomu var skatīt datu veikalus visām grupas spēlēm, izmantojot [Datu veikalu pārvaldnieku](/docs/en-us/cloud-services/data-stores/data-stores-manager) , bet viņi nevar dzēst datus. Opcionalitāte pieejama kā [atļauja par spēli](/docs/en-us/projects/configure-games) . |
| Edit Data Stores for experiences | | Dalībnieki ar šo lomu var dzēst konkrētus atslēgas datu veikalos visām grupas spēlēm, izmantojot [Datu veikalu pārvaldnieku](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Opcionalitāte pieejama kā [atļauja par spēli](/docs/en-us/projects/configure-games) . |
| Delete Data Stores for experiences | | Dalībnieki ar šo lomu var dzēst visus datu veikalus visām grupas spēlēm, izmantojot [Datu veikalu pārvaldnieku](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Opcionalitāte pieejama kā [atļauja par spēli](/docs/en-us/projects/configure-games) . |

Notifications

| Manage webhooks for experiences | | Dalībnieki ar šo lomu var uzskaitīt, izveidot, atjaunināt un dzēst tīmekļa saites visām grupas pieredzēm. |

Communication

| Manage support tickets for experiences | | Dalībnieki ar šo lomu var pārvaldīt atbalsta biļetes visām grupas pieredzēm. |

Legacy

| Pārvaldīt piekļuvi šīs grupas resursiem | | Dalībnieki ar šo lomu var izveidot un rediģēt piekļuvi grupas resursiem. |

### [Kopiena](#kopiena)[](#kopiena)

Posts

| View community announcements | | Dalībnieki ar šo lomu var skatīt kopienas paziņojumus. |
| Create community announcements | | Dalībnieki ar šo lomu var izveidot kopienas paziņojumus. |

Forums

| Manage categories | | Dalībnieki ar šo lomu var pārvaldīt foruma kategorijas. |
| Create posts | | Dalībnieki ar šo lomu var izveidot foruma ziņojumus. |
| Remove posts | | Dalībnieki ar šo lomu var dzēst foruma ziņojumus. |
| Lock posts | | Dalībnieki ar šo lomu var bloķēt foruma ziņojumus. |
| Pin posts | | Dalībnieki ar šo lomu var piespraust foruma ziņojumus. |
| Create comments | | Dalībnieki ar šo lomu var izveidot komentārus uz foruma ziņojumiem. |
| Remove comments | | Dalībnieki ar šo lomu var dzēst komentārus no foruma ziņojumiem. |

Content moderation

| View content moderation | | Dalībnieki ar šo lomu var skatīt satura moderēšanu. |
| Manage content moderation | | Dalībnieki ar šo lomu var pārvaldīt satura moderēšanu. |

Miscellaneous

| Bypass slow mode | | Dalībnieki ar šo lomu var apiet lēno režīmu. |
| View community analytics | | Dalībnieki ar šo lomu var skatīt kopienas analītiku. |

4.

SVARĪGI

 Noklikšķiniet uz Save  pogas, lai piemērotu atļauju iestatījumus.

5.

OPCIONĀLI

 Noklikšķiniet uz Settings  cilnes un izvēlieties krāsu un redzamības iestatījumu lomai, pēc tam noklikšķiniet uz Save  pogas.

Lomas Settings  sadaļa ir arī vieta, kur grupas īpašnieki un dalībnieki ar pietiekamām atļaujām var pilnībā noņemt lomu, izmantojot Dzēst lomu  pogu.

Lomas ir uzskaitītas hierarhijas secībā: loma, kas ir augstāk sarakstā, ir ar lielāku varu nekā loma, kas ir zemāk. Šī secība ir svarīga, jo dažas atļaujas ļauj dalībniekiem pārvaldīt lomas tikai zem viņu augstākās lomas.

Katras lomas ir vai nu publiskas , vai privātas . Publiskās lomas var tikt rādītas Kopienas lapā un pieredzēs. Privātās lomas tiek rādītas tikai lomu un atļauju pārvaldības virsmās autorizētiem dalībniekiem vai dalībniekiem, kuriem ir privātā loma. Redzamības izmaiņas nosaka, kur loma parādās; tas nemaina atļaujas, ko loma piešķir.

Lai piešķirtu Manage roles , Assign or remove roles from members , Manage access to this group’s resources , Manage and spend group revenue  vai Delete Data Stores for experiences , jums ir jābūt iespējotai divu soļu verifikācijai.

## [Pārvaldīt dalībniekus](#pārvaldīt-dalībniekus)[](#pārvaldīt-dalībniekus)

Dalībnieku konfigurācija ir pieejama tikai tad, ja esat grupas īpašnieks vai jums ir atļauja pārvaldīt citus dalībniekus un viņu lomas.

Lai pārvaldītu dalībniekus no Veidotāja informācijas paneļa:

1.

Paplašiniet konta pārslēdzēju augšējā kreisajā stūrī un izvēlieties grupu.

2.

Atkal paplašiniet konta pārslēdzēju un izvēlieties Members .

3.

Izmantojiet Dalībnieku  cilni, lai meklētu esošos dalībniekus vai filtrētu tos pēc lomas. Izmantojiet Aicinātie  cilni, lai pārskatītu gaidošos aicinājumus.

Lai pievienotu dalībnieku, noklikšķiniet uz Invite  pogas un meklējiet viņu lietotājvārdu. Roblox paziņo aicinātajiem veidotājiem atbilstoši viņu paziņojumu preferencēm. Jūs varat arī kopēt grupas saiti un dalīties ar to tieši.

### [Pārvaldīt lomas](#pārvaldīt-lomas)[](#pārvaldīt-lomas)

Jūs varat pārvaldīt lomu piešķiršanu gan Members  lapā, gan konkrētā lomā:

-

Members  lapā noklikšķiniet uz plus (+)  pogas blakus dalībniekam, lai atvērtu lomu izvēlni. Lai piešķirtu lomu, noklikšķiniet uz plus (+)  pogas blakus tai sadaļā Pievienot lomas . Lai atņemt lomu, noklikšķiniet uz minus (-)  pogas blakus tai sadaļā Pašreizējās lomas , vai noklikšķiniet uz ×  pogas pie piešķirtās lomas blakus dalībnieka vārdam.

-

Lomu  lapā izvēlieties lomu un atveriet tās Members  cilni. Noklikšķiniet uz Add members  pogas, lai meklētu grupas dalībniekus un piešķirtu viņus lomai. Lai atņemt dalībnieku, noklikšķiniet uz minus (-)  pogas viņu rindas beigās.

### [Dalībnieku noņemšana](#dalībnieku-noņemšana)[](#dalībnieku-noņemšana)

Lai noņemtu dalībnieku no grupas, noklikšķiniet uz ⋮  pogas viņu rindas beigās, izvēlieties Izsist lietotāju  un apstipriniet darbību.

## [Pārvaldīt izmaksas](#pārvaldīt-izmaksas)[](#pārvaldīt-izmaksas)

Ja esat grupas īpašnieks vai jums ir pareizā [atļauja](#lomas-un-at%C4%BCaujas)  Grupas ieņēmumos , jūs atradīsiet Izmaksu  lapu sadaļā Finanses  kreisajā navigācijā. Šeit jūs varat nosūtīt vienreizējas izmaksas, kā arī definēt procentuālos sadalījumus ar citiem dalībniekiem.

Dažām grupām šī lapa sākotnēji var nebūt atbloķēta dažādu iemeslu dēļ, piemēram, grupas vecuma vai nepietiekamu līdzekļu izmaksām.

Izmaksas nevar tikt dalītas starp grupas dalībniekiem spēlēm, kas iekasē [maksas piekļuvi vietējā valūtā](/docs/en-us/production/monetization/paid-access-local-currency) .

### [Vienreizējas izmaksas](#vienreizējas-izmaksas)[](#vienreizējas-izmaksas)

Vienreizējas izmaksas var tikt veiktas dalībniekiem grupā, izvēloties noteiktu summu katram. Drošības funkcijas ietver 2FA izaicinājumus, apstiprināšanas dialogus un pārbaudes par dalībnieku, kuri saņem maksājumus, piemērotību.

 ![Vienreizējas izmaksas poga norādīta Izmaksu sadaļā Veidotāja informācijas panelī.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-One-Time.png)

Kad noklikšķināt uz Nosūtīt Robux  pogas, jūs varat izvēlēties izmaksu saņēmējus no uznirstošā loga vai augšupielādēt .csv  izklājlapu ar kolonnām userId  un payoutInRobux , piemēram:

| userId | | payoutInRobux |
| 012345 | | 5000 |
| 098765 | | 7000 |

### [Atkārtotas izmaksas](#atkārtotas-izmaksas)[](#atkārtotas-izmaksas)

Atkārtotas izmaksas var tikt veiktas visai grupai un  par spēli, piešķirot procentuālo izmaksu katram dalībniekam, pirms atlikums nonāk grupas kopējā bilancē.

 ![Sadalīto izmaksu pogas norādītas Izmaksu sadaļā Veidotāja informācijas panelī.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Split-Options.png)

Apsveriet sekojošo scenāriju, kur grupas spēle Laser Maze  tiek sadalīta 40%–30%–10% starp trim dalībniekiem, ar atlikumu 20%.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-A.png)

Pieņemot, ka spēle nopelna 1000 Robux, trīs dalībnieki saņem 400, 300 un 100 Robux attiecīgi (40%–30%–10%).

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-B.png)

Atlikušās 200 Robux (20% no spēles sadalījuma) tiek nodotas grupas sadalījuma  procentiem, kas definēti 20%–20%–10% starp tiem pašiem trim dalībniekiem; viņi saņem papildu 40, 40 un 20 Robux attiecīgi.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-C.png)

Atlikušās 100 Robux (50% no grupas sadalījuma) tiek novietotas grupas kopējā bilancē.

 ![Piemēra plūsmas diagramma, kā spēles sadalījumi tiek sadalīti grupas dalībniekiem vispirms, ar atlikumu, kas tiek iekļauts grupas sadalījumos galīgai sadalei starp grupu.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Splits-Example.png)

Ņemiet vērā, ka ieņēmumi no [privātā servera](/docs/en-us/production/monetization/private-servers)  abonementiem nemainās, ja jūs vēlāk pielāgojat sadalījuma procentus, tas nozīmē, ka, ja spēlētājs iegādājas privātā servera abonementu, sadalījuma procenti pirkuma brīdī tiks piemēroti šim konkrētajam abonementam uz visiem laikiem (līdz tas tiek atcelts). Šī politika var tikt mainīta nākotnē.

## [Grupas audita žurnāli](#grupas-audita-žurnāli)[](#grupas-audita-žurnāli)

Grupas dalībnieki ar View audit logs  atļauju var pārskatīt grupas izmaiņas, izmantojot šīs grupas pārvaldības virsmas:

-

Uz Veidotāja informācijas paneļa izvēlieties Aktivitātes vēsture  sadaļā Sadarbība .

-

Uz Kopienām atveriet kopienas konfigurācijas lapu un izvēlieties Audita žurnāls .

Grupas īpašnieki var izmantot šos žurnālus, lai uzraudzītu darbības, kas varētu pārkāpt [grupas vadlīnijas](/docs/en-us/projects/group-guidelines) .

## [Intelektuālā īpašuma aizsardzība](#intelektuālā-īpašuma-aizsardzība)[](#intelektuālā-īpašuma-aizsardzība)

Grupas dalībnieki ar atļaujām rediģēt visas grupas spēles var iespējot [Vietnes kopēšanu](/docs/en-us/projects/configure-games#allow-copying)  iestatījumu radīšanai, potenciāli ļaujot visai Roblox kopienai to kopēt un izmantot tajā esošos resursus. Lai palīdzētu aizsargāt intelektuālo īpašumu grupā, īpašniekam vai dalībniekiem ar pietiekamām atļaujām vajadzētu:

-

Apstiprināt, ka katrs dalībnieks ir [piešķirts atbilstošai lomai](#p%C4%81rvald%C4%ABt-lomas) .

-

Pārbaudīt, ka katrai grupas lomai ir pareizas [atļaujas](#lomas-un-at%C4%BCaujas) .

-

Apstiprināt, ka [Vietnes kopēšana](/docs/en-us/projects/configure-games#allow-copying)  iestatījums ir atspējots, pirms tiek pievienoti privāti resursi.

## [Papildu lokalizācijas šai lapai](#papildu-lokalizācijas-šai-lapai)[](#papildu-lokalizācijas-šai-lapai)

Papildu lokalizētām šīs lapas versijām, kas nav pieejamas vietnes valodas izvēlnē, skatiet šādas saites:

-

[Bulgāru (български)](https://create.roblox.com/docs/bg-bg/projects/groups)

-

[Horvātu (hrvatski)](https://create.roblox.com/docs/hr-hr/projects/groups)

-

[Čehijas (čeština)](https://create.roblox.com/docs/cs-cz/projects/groups)

-

[Dāņu (dansk)](https://create.roblox.com/docs/da-dk/projects/groups)

-

[Nīderlandiešu (Nederlands)](https://create.roblox.com/docs/nl-nl/projects/groups)

-

[Igauņu (eesti)](https://create.roblox.com/docs/et-ee/projects/groups)

-

[Somu (suomi)](https://create.roblox.com/docs/fi-fi/projects/groups)

-

[Grieķu (Ελληνικά)](https://create.roblox.com/docs/el-gr/projects/groups)

-

[Ungāru (magyar)](https://create.roblox.com/docs/hu-hu/projects/groups)

-

[Īru (Gaeilge)](https://create.roblox.com/docs/ga-ie/projects/groups)

-

[Lietuviešu (latviešu)](https://create.roblox.com/docs/lv-lv/projects/groups)

-

[Lietuviešu (lietuvių)](https://create.roblox.com/docs/lt-lt/projects/groups)

-

[Maltiešu (Malti)](https://create.roblox.com/docs/mt-mt/projects/groups)

-

[Portugāļu - Portugāle (português)](https://create.roblox.com/docs/pt-pt/projects/groups)

-

[Rumāņu (română)](https://create.roblox.com/docs/ro-ro/projects/groups)

-

[Slovāku (slovenčina)](https://create.roblox.com/docs/sk-sk/projects/groups)

-

[Slovēņu (slovenščina)](https://create.roblox.com/docs/sl-si/projects/groups)

-

[Zviedru (svenska)](https://create.roblox.com/docs/sv-se/projects/groups)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
