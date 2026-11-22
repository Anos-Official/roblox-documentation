<!-- Source: https://create.roblox.com/docs/hr-hr/cloud-services/extended-services -->

Proširene usluge | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Cloud services](/docs/en-us/cloud-services/data-stores-vs-memory-stores)

# Proširene usluge

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Proširene usluge su rješenje koje vam omogućuje upravljanje korištenjem usluga i plaćanjem izvan zadatih ograničenja Robloxa. Uključuje pohranu podataka, pohranu u memoriji, pretvaranje teksta u govor, pretvaranje govora u tekst i izračun.

## [Uvjeti za kvalifikaciju](#uvjeti-za-kvalifikaciju)[](#uvjeti-za-kvalifikaciju)

Da biste koristili Proširene usluge, vaš Roblox račun mora:

-

Biti [verificiran putem ID-a](/docs/en-us/production/publishing/account-verification#verify-through-government-id)  i imati 18+ godina.

-

Biti smješten u [podržanoj zemlji](#podr%C5%BEane-zemlje) .

-

Imati važeću adresu e-pošte povezan s njim.

-

Ne biti trenutno zabranjen ili pod moderacijom.

-

Prihvatiti i pridržavati se [uvjeta korištenja](https://en.help.roblox.com/hc/articles/37967848292500) .

Za grupne račune, samo vlasnik grupe treba ispuniti uvjete za kvalifikaciju.

## [Otključavanje Proširenih usluga](#otključavanje-proširenih-usluga)[](#otključavanje-proširenih-usluga)

Ako ispunjavate sve [uvjete za kvalifikaciju](#uvjeti-za-kvalifikaciju) , možete završiti postavljanje Proširenih usluga unosom podataka o svom računu i informacijama o plaćanju. Za igre u vlasništvu grupe, samo vlasnik grupe može otključati Proširene usluge i uključiti igru u njih.

Da biste otključali i koristili Proširene usluge:

1.

U [Kreatorskoj nadzornoj ploči](https://create.roblox.com/dashboard/creations) , idite na Kreacije  i odaberite igru.

2.

Idite na Proširene usluge .

3.

Ako još niste unijeli podatke o svom računu i informacije o plaćanju, kliknite Dodajte nedostajuće informacije  na gornjoj traci.

1.

Unesite informacije o svom računu. Polja Tip računa , Tip poreznog ID-a  i Porezni ID  su opcionalna.

-

Također možete otići na Financije  ⟩ Informacije o računu  u odjeljku Proširene usluge  kako biste upravljali informacijama o svom računu. Ne trebate ažurirati ništa drugo na ovoj stranici.

2.

Kliknite Dalje .

3.

Unesite metodu plaćanja. Možete unijeti novu metodu plaćanja ili odabrati iz dostupnih opcija plaćanja već povezanih s vašim Roblox računom.

-

Također možete otići na Financije  ⟩ Plaćanja  kako biste dodali nove metode plaćanja, ili otići na Financije  ⟩ Naplate  kako biste postavili novu zadanu metodu plaćanja.

4.

Kliknite Spremi .

##### Status računa

Vaš račun za Proširene usluge može biti u jednom od sljedećih statusa:

| Status | | Opis | | Potrebna akcija |
| Normalno | | Možete koristiti sve značajke Proširenih usluga. | | Nema potrebne akcije. |
| --- | --- |
| Zakašnjelo | | Vaš račun je zakašnjen jer je vaša automatska metoda plaćanja zakazala. Roblox nudi grace period od sedam dana  prije nego što suspendira vaš račun za Proširene usluge. | | Promijenite svoju metodu plaćanja i pokušajte ponovo s ručnim plaćanjem, ili pričekajte da Roblox pokuša ponovo naplatiti vašu metodu plaćanja nakon što grace period završi. |
| Suspendirano | | Ne možete koristiti nijednu plaćenu Proširenu uslugu. Međutim, još uvijek možete koristiti usluge s zadanim ograničenjima. | | Ispravite svoje uvjete za kvalifikaciju, dodajte važeću metodu plaćanja ili ručno platite dospjeli saldo na svom računu. |

## [Omogućavanje usluge](#omogućavanje-usluge)[](#omogućavanje-usluge)

Da biste omogućili uslugu:

1.

Idite na Proširene usluge .

2.

Uključite uslugu koju želite omogućiti.

3.

Unesite mjesečni proračun za svaki primjenjivi resurs pod uslugom. Minimalni mjesečni proračun koji možete postaviti je 0,50 USD.

Vaša metoda plaćanja se naplaćuje ili na kraju mjeseca kada se generira račun, ili kada vaša potrošnja dostigne 10 USD, što god se prije dogodi.

Možete povećati ili smanjiti mjesečni proračun usluge u bilo kojem trenutku. Vaša usluga se automatski ograničava ako smanjite svoj proračun na iznos ispod vaše trenutne potrošnje do danas, ili ako premašite proračun koji ste postavili.

Roblox vas obavještava putem e-pošte kada vaša potrošnja dostigne 80% vašeg proračuna, a zatim ponovno kada dostigne 100%.

### [Proširene usluge za izračun](#proširene-usluge-za-izračun)[](#proširene-usluge-za-izračun)

Svaki server igre dobiva zadanu količinu CPU-a, koja raste s svakim igračem koji se pridruži. Proširene usluge za izračun  više nego udvostručuju CPU po igraču koji vaši serveri igre primaju.

Većina igara na Robloxu ne vidi koristi od ove usluge, ali igre s teškom fizikom na serveru ili koje u velikoj mjeri koriste [server authority](/docs/en-us/projects/server-authority)  dostižu postojeća ograničenja. Da biste vidjeli može li vaša igra imati koristi od Proširenih usluga za izračun :

-

Provjerite [heartbeat servera](/docs/en-us/performance-optimization/identify#server-compute)  za trajne padove ispod 60 FPS.

-

Istražite iskorištenost CPU jezgri na [Nadzornoj ploči performansi](/docs/en-us/production/analytics/performance#server-charts) .

Prije nego što platite za više CPU-a, pokušajte [smanjiti rad koji vaši serveri rade](/docs/en-us/performance-optimization/improve) .

## [Upravljanje naplatom](#upravljanje-naplatom)[](#upravljanje-naplatom)

Da biste pristupili nadzornoj ploči naplate Proširenih usluga:

1.

Idite na Financije  ⟩ Naplate .

2.

Odaberite karticu Cloud usluge  kako biste prikazali sljedeće:

-

Vaš neplaćeni saldo, uključujući trošak do danas

-

Vašu povijest naplate, uključujući sve aktivnosti naplate Proširenih usluga u vašim igrama

Za detaljan pregled troškova vašeg trenutnog neplaćenog salda, kliknite Pogledajte detalje  pored vaše metode plaćanja. Za detaljan račun prethodnog računa, kliknite Pogledajte račun  ispod Povijest naplate .

## [Cijene usluga](#cijene-usluga)[](#cijene-usluga)

Pogledajte sljedeću tablicu za cijene Proširenih usluga:

| Usluga | |  | | Zadano | | Prošireno |
| [Pohrane u memoriji](https://create.roblox.com/docs/cloud-services/memory-stores) | | Zahtjevi | | 1000 + (CCU × 120) zahtjeva po minuti | | $0.003 / 1M zahtjeva |
|  | | Pohrana | | 64 KB + (CCU × 1.2 KB) | | $0.10 / GB po satu¹ |
| [Pretvaranje teksta u govor](https://create.roblox.com/docs/audio/objects#text-to-speech) | | Zahtjevi | | 1 + (CCU × 6) zahtjeva po minuti | | $5.00 / 1M zahtjeva |
| [Pretvaranje govora u tekst](https://create.roblox.com/docs/audio/objects#speech-to-text) | | Zahtjevi | | 1 + (CCU × 5) zahtjeva po minuti | | $1 / 1M zahtjeva |
| [Standardne pohrane podataka](https://create.roblox.com/docs/cloud-services/data-stores) | | Preuzmi | | 250 + (CCU * 40) zahtjeva po minuti | | $0.08 / 1M zahtjeva |
|  | | Postavi | | 250 + (CCU * 20) zahtjeva po minuti | | $0.80 / 1M zahtjeva |
|  | | Popis | | 10 + (CCU * 2) zahtjeva po minuti | | $0.60 / 1M zahtjeva |
|  | | Ukloni | | 100 + (CCU * 40) zahtjeva po minuti | | $0.80 / 1M zahtjeva |
| [Poredane pohrane podataka ](https://create.roblox.com/docs/cloud-services/data-stores) | | Preuzmi | | 250 + (CCU * 40) zahtjeva po minuti | | $0.08 / 1M zahtjeva |
|  | | Postavi | | 250 + (CCU * 20) zahtjeva po minuti | | $0.25 / 1M zahtjeva |
|  | | GetSorted | | 100 + (CCU * 2) zahtjeva po minuti | | $0.32 / 1M zahtjeva |
|  | | Ukloni | | 100 + (CCU * 40) zahtjeva po minuti | | $0.25 / 1M zahtjeva |
| [Pohrana podataka ](https://create.roblox.com/docs/cloud-services/data-stores) | | Pohrana | | 100 MB + (1 MB * Igrači tijekom života) GB po mjesecu | | $0.12 / GB po mjesecu |
| [Izračun ](https://create.roblox.com/docs/production/analytics/performance) | | CPU jezgre | | Prvih 100K sati igranja po mjesecu bez naknade (kada ste upisani u Proširene usluge za izračun) | | $0.001 / sat igranja² |

 ¹ GB po satu = potrošnja pohrane pomnožena s vremenom. Na primjer, 100 GB sati može odgovarati "100 GB × 1 sat" ili "200 GB × 0.5 sati".  ² Proširene usluge za izračun naplaćuju se na temelju vremena tijekom kojeg je značajka omogućena, mjerena u minutama igranja. Budući da omogućavanje značajke rezervira dodatni kapacitet za izračun za vašu igru, troškovi se primjenjuju kad god je značajka aktivna, čak i ako dodatni izračun nije potpuno iskorišten. Sati igranja se računaju kao zbroj svih trajanja sesija igrača. Na primjer, ako 10,000 korisnika igra po 1 sat, to iznosi 10,000 sati igranja, što rezultira troškom od 10 USD iznad uključenog mjesečnog dopuštenja od 100,000 sati igranja. Ova ograničenja i cijene primjenjuju se samo na igre koje su upisane u Proširene usluge za izračun. Igre koje se ne upisuju nastavljaju primati neograničene sate igranja pod trenutnim zadanim ograničenjima bez dodatne naknade.

## [Podržane zemlje](#podržane-zemlje)[](#podržane-zemlje)

Proširene usluge su dostupne u sljedećim zemljama:

| Zemlja |
| Australija | | Njemačka | | Poljska |
| Austrija | | Hong Kong | | Portugal |
| Belgija | | Mađarska | | Rumunija |
| Brazil | | Irska | | Singapur |
| Bugarska | | Italija | | Slovačka |
| Kanada | | Kazahstan | | Slovenija |
| Čile | | Latvija | | Južna Afrika |
| Hrvatska | | Litvanija | | Južna Koreja |
|  Kipar | | Malezija | | Španija |
| Češka | | Malta | | Švedska |
| Danska | | Međunarodna | | Švicarska |
| Estonija | | Nizozemska | | Tajland |
| Finska | | Nova Zeland | | Ujedinjeno Kraljevstvo |
| Francuska | | Norveška | | Sjedinjene Američke Države |
| Gruzija | | Peru | |  |

## [Dodatne lokalizacije za ovu stranicu](#dodatne-lokalizacije-za-ovu-stranicu)[](#dodatne-lokalizacije-za-ovu-stranicu)

Za dodatne, lokalizirane verzije ove stranice koje nisu dostupne u odabiru jezika na stranici, pogledajte sljedeće linkove:

-

[Bugarski (български)](https://create.roblox.com/docs/bg-bg/cloud-services/extended-services)

-

[Hrvatski (hrvatski)](https://create.roblox.com/docs/hr-hr/cloud-services/extended-services)

-

[Češki (čeština)](https://create.roblox.com/docs/cs-cz/cloud-services/extended-services)

-

[Danski (dansk)](https://create.roblox.com/docs/da-dk/cloud-services/extended-services)

-

[Nizozemski (Nederlands)](https://create.roblox.com/docs/nl-nl/cloud-services/extended-services)

-

[Estonski (eesti)](https://create.roblox.com/docs/et-ee/cloud-services/extended-services)

-

[Finski (suomi)](https://create.roblox.com/docs/fi-fi/cloud-services/extended-services)

-

[Grčki (Ελληνικά)](https://create.roblox.com/docs/el-gr/cloud-services/extended-services)

-

[Mađarski (magyar)](https://create.roblox.com/docs/hu-hu/cloud-services/extended-services)

-

[Irski (Gaeilge)](https://create.roblox.com/docs/ga-ie/cloud-services/extended-services)

-

[Latvijski (latviešu)](https://create.roblox.com/docs/lv-lv/cloud-services/extended-services)

-

[Litvanski (lietuvių)](https://create.roblox.com/docs/lt-lt/cloud-services/extended-services)

-

[Malteški (Malti)](https://create.roblox.com/docs/mt-mt/cloud-services/extended-services)

-

[Portugalski - Portugal (português)](https://create.roblox.com/docs/pt-pt/cloud-services/extended-services)

-

[Rumunjski (română)](https://create.roblox.com/docs/ro-ro/cloud-services/extended-services)

-

[Slovački (slovenčina)](https://create.roblox.com/docs/sk-sk/cloud-services/extended-services)

-

[Slovenski (slovenščina)](https://create.roblox.com/docs/sl-si/cloud-services/extended-services)

-

[Švedski (svenska)](https://create.roblox.com/docs/sv-se/cloud-services/extended-services)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
