<!-- Source: https://create.roblox.com/docs/hr-hr/production/monetization -->

Monetizacija | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)

# Monetizacija

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Monetizacija je dio ukupne strukture Robloxa koja pruža vrijednost kreatorima. Postoji nekoliko različitih pristupa za monetizaciju vašeg sadržaja, uključujući korištenje [pretplata](#pretplate) , naplaćivanje pristupa u [Robuxu](#pla%C4%87eni-pristup-u-robuxu)  ili [lokalnoj valuti](#pla%C4%87eni-pristup-u-lokalnoj-valuti) , pružanje [predmeta ili sposobnosti koje korisnici mogu kupiti](#proizvodi-za-developere) , ponudu [privatnih servera](#privatni-serveri)  za korisnike koji žele igrati samo s prijateljima, i [prodaju modela i dodataka](/docs/en-us/production/creator-store#distribute-and-sell-assets)  drugim kreatorima na Creator Storeu.

Ako se odlučite ponuditi sadržaj koji se može kupiti, Roblox automatski ne bilježi informacije o proizvodima ili kupovinama. Da biste spriječili gubitak podataka, morate pažljivo pohraniti te podatke koristeći [DataStoreService](/docs/en-us/reference/engine/classes/DataStoreService)  ili neku drugu uslugu pohrane podataka koja se hosta izvan Robloxa.

Za detaljan pregled dizajniranja optimalnih strategija monetizacije za vaše iskustvo, pogledajte [Osnove monetizacije](/docs/en-us/production/game-design/monetization-foundations) .

## [Strategije monetizacije](#strategije-monetizacije)[](#strategije-monetizacije)

Budite oprezni s metodama monetizacije koje uvodite u svoju igru jer naši korisnici vjerojatno će negativno ocijeniti  vašu igru ako ne odobre vaše strategije. Također, svi developeri trebaju biti transparentni s bilo kojom [monetizacijom temeljenom na sreći](/docs/en-us/production/monetization/paid-random-items)  i koristiti te mehanizme odgovorno.

Neke popularne strategije monetizacije za igre koje se igraju besplatno na drugim platformama nisu preporučene za Roblox. Na primjer, mehanizmi zakazivanja i tajmeri koji se mogu ukloniti ili pomaknuti mogu dobro funkcionirati na drugim platformama, ali ti mehanizmi nisu popularni među Roblox korisnicima koji se protive tome da njihova zabava dođe do preranog kraja.

Sljedeće preporuke najboljih praksi popularne su među vrhunskim developerima za prilagodbu strategija monetizacije Roblox platformi i publici.

Imajte na umu da primjenom ovih tehnika i razmatranja ne jamčite da ćete učinkovito monetizirati svoju igru. Zapamtite da ne morate imati financijske ciljeve da biste se zabavljali stvarajući Roblox igru.

### [Turisti i lokalci](#turisti-i-lokalci)[](#turisti-i-lokalci)

Može biti korisno razmišljati o Roblox korisnicima u dvije kategorije:

-

Turisti  obično skaču s jedne igre na drugu, prioritizirajući raznolikost umjesto dubine. Preferiraju predmete s neposrednim efektima, bilo kroz povećanje zabave u igri ili kroz isticanje, pozivajući druge korisnike da se pitaju kako i gdje su dobili taj predmet.

-

Lokalci  su skloniji fokusirati se na određenu igru ili manji set igara. Dublje se angažiraju i obično čine gotovo cijelu angažiranu korisničku bazu igre. Više su zainteresirani za predmete s dugoročnim koristima, poput [battle passa](/docs/en-us/production/game-design/season-pass-design) .

Da biste saznali više o tome kako dizajnirati svoju igru s obzirom na Roblox korisnike, pogledajte [Dizajn za Roblox](/docs/en-us/production/game-design/design-for-roblox) .

### [Društvene značajke](#društvene-značajke)[](#društvene-značajke)

Roblox korisnici obično uživaju u igrama koje naglašavaju društvenu interakciju. Na primjer, imati predmete ili događaje koji su dostupni samo na ograničeno vrijeme  može stvoriti uzbuđenje oko tog sadržaja. Sustav trgovanja  potiče korisnike na interakciju. Iako oba sustava mogu biti uspješna sama po sebi, posebno su učinkovita kada se kombiniraju.

### [Operacije uživo](#operacije-uživo)[](#operacije-uživo)

Podrška nakon lansiranja je na Robloxu na mnogo načina lakša nego na drugim platformama jer možete brzo isporučiti ažuriranja za poboljšanje svoje igre.

Česta  ažuriranja sadržaja mogu biti korisna ako želite održati angažman s vašom igrom tijekom vremena. Roblox korisnici su navikli na redovita ažuriranja, a može biti mnogo teže ponovno privući korisnički interes nego održati aktivne. Tjedni ritam  za ažuriranja je idealan. U najmanju ruku, ciljajte na mjesečna ažuriranja. Za raspravu o ritmu sadržaja, pogledajte Level Up [radionicu o ritmu sadržaja](/docs/en-us/production/game-design/content-updates) .

Kada dizajnirate ažuriranja, zadržite ih fokusiranim na određenu temu . To olakšava korisnicima razumijevanje novog ažuriranja i prepoznavanje koji je sadržaj nov kada se pridruže. Također vam pomaže u koordinaciji vašeg sadržaja i promotivnih sredstava. Na primjer, ako dodajete novi Zoološki vrt u svoju igru uloga, pobrinite se da sav novi sadržaj ima neku povezanost s temom Zoološkog vrta.

Ne bojte se natjerati korisnike da zarade svoj pristup  novom sadržaju. Novi korisnici će se okupiti da igraju nova ažuriranja, ali ako ne osjete da su nešto postigli  u igri, mogli bi brzo napustiti. Možete stvoriti osjećaj zarađivanja ažuriranja bilo monetizacijom sadržaja ažuriranja ili stvaranjem preduvjeta za igranje novog sadržaja.

Da biste saznali više o tome kako dizajnirati učinkovitu podršku nakon lansiranja za svoju igru, pogledajte [Osnove operacija uživo](/docs/en-us/production/game-design/liveops-essentials) .

## [Proizvodi](#proizvodi)[](#proizvodi)

### [Imersivne reklame](#imersivne-reklame)[](#imersivne-reklame)

Sustav [imersivnih reklama](/docs/en-us/production/monetization/immersive-ads)  omogućuje vam umetanje reklamnih jedinica u vašu igru koje omogućuju Robloxu da programatski poslužuje reklamni sadržaj od oglašivača vašim aktivnim korisnicima.

![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/Overview-ImageAd.jpg) Format slikovne reklame

Format portal reklame

### [Roblox Plus](#roblox-plus)[](#roblox-plus)

[Roblox Plus](/docs/en-us/production/monetization/roblox-plus)  vam omogućuje da zarađujete kroz povećane kupovine unutar igre potaknute popustima koje subvencionira Roblox, bonuse za prijavu za svakog novog pretplatnika kojeg dovedete, i angažman u plaćenim privatnim serverima.

### [Pretplate](#pretplate)[](#pretplate)

[Pretplate](/docs/en-us/production/monetization/subscriptions)  unutar igara omogućuju vam da korisnicima ponudite ponavljajuće pogodnosti uz mjesečnu naknadu.

![](https://prod.docsiteassets.roblox.com/assets/monetization/subscriptions/Example-Subscriptions.png) Primjeri pretplata za igre

### [Propusnice](#propusnice)[](#propusnice)

[Propusnica](/docs/en-us/production/monetization/passes)  vam omogućuje da naplatite jednokratnu naknadu u Robuxu  kako bi korisnici mogli pristupiti posebnim privilegijama unutar igre, poput ulaska u ograničeno područje, predmeta za avatar unutar igre ili trajnog poboljšanja.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/passes/passes-sample.png)

### [Proizvodi za developere](#proizvodi-za-developere)[](#proizvodi-za-developere)

[Proizvod za developere](/docs/en-us/production/monetization/developer-products)  je predmet ili sposobnost koju korisnik može kupiti više od jednom, poput valute unutar igre, municije ili napitaka. Možete potaknuti kupnje, zabilježiti ih i dobiti informacije o proizvodu putem skriptiranja.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/developer-products/Buy-Product-Example.jpg)

### [Upravljane cijene](#upravljane-cijene)[](#upravljane-cijene)

[Upravljane cijene](/docs/en-us/production/monetization/managed-pricing)  je jedinstveni sustav koji spaja [regionalne cijene](/docs/en-us/production/monetization/regional-pricing)  i [optimizaciju cijena](/docs/en-us/production/monetization/price-optimization)  na jednom mjestu. Jednom se prijavite, odaberete koje predmete uključiti, a Upravljane cijene održavaju vaše cijene optimiziranim kroz proizvode i regije tijekom vremena.

### [Optimizacija cijena](#optimizacija-cijena)[](#optimizacija-cijena)

[Optimizacija cijena](/docs/en-us/production/monetization/price-optimization)  vam omogućuje da pronađete najbolje cjenovne točke za vaše propusnice i proizvode za developere, što vam može pomoći da zarađujete više novca tijekom vremena dok održavate svoje cijene konkurentnima.

### [Plaćeni pristup u Robuxu](#plaćeni-pristup-u-robuxu)[](#plaćeni-pristup-u-robuxu)

[Plaćeni pristup u Robuxu](/docs/en-us/production/monetization/paid-access-robux)  omogućuje vam da naplatite korisnicima jednokratnu naknadu u Robuxu  za pristup vašoj igri. Neki developeri privremeno koriste ovu značajku za stvaranje zatvorenog beta testiranja gdje njihovi najangažiraniji korisnici mogu imati rani pristup igri i pomoći u testiranju i povratnim informacijama.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/paid-access/Buy-Access-Example.png)

### [Plaćeni pristup u lokalnoj valuti](#plaćeni-pristup-u-lokalnoj-valuti)[](#plaćeni-pristup-u-lokalnoj-valuti)

[Plaćeni pristup u lokalnoj valuti](/docs/en-us/production/monetization/paid-access-local-currency)  omogućuje vam da naplatite korisnicima jednokratnu naknadu u njihovoj lokalnoj valuti  za pristup vašoj igri. Ako njihova lokalna valuta nije dostupna, naplaćuje im se u USD-u. Neki developeri privremeno koriste ovu značajku za stvaranje zatvorenog beta testiranja gdje njihovi najangažiraniji korisnici mogu imati rani pristup igri i pomoći u testiranju i povratnim informacijama.

### [Privatni serveri](#privatni-serveri)[](#privatni-serveri)

[Privatni server](/docs/en-us/production/monetization/private-servers)  je značajka temeljena na pretplati koja omogućuje korisniku da odluči tko može igrati igru s njima. Iako privatni serveri mogu biti besplatni, također ih možete koristiti kao metodu monetizacije naplaćujući korisnicima koji žele pristup privatnim serverima mjesečnu naknadu u Robuxu .

### [Naknade i provizije za katalog](#naknade-i-provizije-za-katalog)[](#naknade-i-provizije-za-katalog)

Možete kreirati i prodavati dodatke i odjeću na Marketplaceu. Nakon što platite naknadu za učitavanje i pošaljete novi predmet na odobrenje, tim za moderaciju pregledava vaš predmet i, ako je odobren, dodaje vaš predmet u katalog.

Primat ćete [proviziju](/docs/en-us/marketplace/marketplace-fees-and-commissions)  svaki put kada korisnici kupe vaš predmet iz kataloga. Ako korisnici kupe vaš predmet iz kataloga unutar igre koristeći [izbornik za inspekciju avatara](/docs/en-us/players/avatar-inspect-menu)  ili [uslugu uređivača avatara](/docs/en-us/players/avatar-editor) , vlasnik igre također prima proviziju.

### [Dodaci i modeli](#dodaci-i-modeli)[](#dodaci-i-modeli)

[Dodaci](/docs/en-us/studio/plugins)  su proširenja koja dodaju dodatnu funkcionalnost Studio-u, a [model](/docs/en-us/parts/models)  je tip ponovljivog sredstva. Možete ponuditi oboje drugim kreatorima na [Creator Store](/docs/en-us/production/creator-store)  besplatno, ili ih možete prodati za američke dolare  (minimalna cijena je $4.99 za dodatke i $2.99 za modele). Roblox nudi vodeći udio prihoda za te prodaje, jer se odbijaju samo porezi i naknade za obradu plaćanja. Za više informacija o prodaji dodataka i modela, pogledajte [Creator Store - Distribuirajte i prodajte sredstva](/docs/en-us/production/creator-store#distribute-and-sell-assets) .

Postoji 30-dnevna zadržavanje za svaku kupnju. Roblox zadržava vaš udio od prodaje 30 dana, počevši od datuma prodaje.

## [Smjernice](#smjernice)[](#smjernice)

Dok dizajnirate i implementirate proizvode monetizacije u svoje igre, razmotrite sljedeće smjernice kako biste osigurali da su vaše metode monetizacije prikladne za sve publike na platformi.

### [Predstavljanje proizvoda](#predstavljanje-proizvoda)[](#predstavljanje-proizvoda)

Kako biste održali sigurnost i pravednost, morate predstaviti proizvode monetizacije na način koji je transparentan, pošten i prijateljski prema korisnicima. Na primjer, ako nudite popuste, oni moraju biti iskreni  i pošteni :

-

Popust nije iskren ako je predmet uvijek "na rasprodaji" za isti iznos Robuxa.

-

Popust nije pošten ako se nudi samo na vrlo kratko vrijeme, pritiskajući korisnike da što brže izvrše kupnju.

Korisnici nikada ne smiju biti zavedeni, zbunjeni ili prisiljeni na kupnje na načine koje nisu namjeravali, i uvijek bi trebali imati slobodu da donesu jasnu, promišljenu odluku o dobivanju pretplate ili trošenju Robuxa na određeni predmet. Kao opća smjernica, postoje neke prakse koje treba izbjegavati u svakom trenutku kada predstavljate proizvode monetizacije svojoj publici:

-

Ne tvrdite da je pretplata ili predmet skoro rasprodan ili dostupan samo na kratko ako to nije istina.

-

Ne koristite odbrojavanje koje nije točno ili se automatski ponovo pokreće za isti predmet.

Na primjer, ako vaša igra uključuje "ponudu dana" koja kaže da je dostupna samo 24 sata, ali zatim prikazujete istu poruku korisnicima svaki put kada se prijave i nikada ne prestaje biti dostupna, stvorili ste lažni osjećaj hitnosti koji nije prijateljski prema korisnicima.

### [Promocija globalnim publikama](#promocija-globalnim-publikama)[](#promocija-globalnim-publikama)

Roblox je globalna zajednica za korisnike svih uzrasta, pa bi promocije unutar vaših igara trebale biti prikladne za sve publike prema zadanim postavkama. Ako su određeni proizvodi monetizacije ograničeni na određenim lokacijama, poput plaćenih nasumičnih predmeta, Roblox pruža [PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  API kako bi vam pomogao osigurati da su ti proizvodi vidljivi samo korisnicima koji ispunjavaju uvjete.

[PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  vraća je li korisnik podoban za određene predmete ili značajke prema njihovoj lokaciji, dobi i platformi. Morate integrirati ovaj API u svoju igru kako biste ispunili svoje obveze usklađenosti, uključujući određivanje je li svaki korisnik:

-

Podoban za kupnju pretplata ili proizvoda u trgovini.

-

Dozvoljeni plaćeni nasumični predmeti, trgovanje plaćenim predmetima ili gledanje imersivnih reklama.

Ako korisnik može koristiti Robux ili nešto drugo što je stečeno s Robuxom za dobivanje nasumične nagrade, obavezni ste koristiti [PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  kako biste blokirali ovu značajku za korisnike koji nemaju dopuštenje za korištenje nasumičnih predmeta u zamjenu za Robux.

Kao opća smjernica, izbjegavajte korištenje napornih ili hitnih poruka kada komunicirate s maloljetnicima, jer jezik visokog pritiska može biti preopterećujući:

| ** Jezik koji treba izbjegavati** | | ** Preporučene alternative** |
| --- | --- |
| "UZMI TO ODMAH" | | "Pogledaj predmet" |
| "POSLJEDNJA PRILIKA, DJELUJ ODMAH" | | "Pogledaj cijenu" |
| "KUPI PRIJE NEGO ŠTO ODE!" | | "Otvorite trgovinu" |

## [Dodatne lokalizacije za ovu stranicu](#dodatne-lokalizacije-za-ovu-stranicu)[](#dodatne-lokalizacije-za-ovu-stranicu)

Za dodatne, lokalizirane verzije ove stranice koje nisu dostupne u jeziku odabira na stranici, pogledajte sljedeće poveznice:

-

[Bugarski (български)](https://create.roblox.com/docs/bg-bg/production/monetization)

-

[Hrvatski (hrvatski)](https://create.roblox.com/docs/hr-hr/production/monetization)

-

[Češki (čeština)](https://create.roblox.com/docs/cs-cz/production/monetization)

-

[Danski (dansk)](https://create.roblox.com/docs/da-dk/production/monetization)

-

[Nizozemski (Nederlands)](https://create.roblox.com/docs/nl-nl/production/monetization)

-

[Estonski (eesti)](https://create.roblox.com/docs/et-ee/production/monetization)

-

[Finski (suomi)](https://create.roblox.com/docs/fi-fi/production/monetization)

-

[Grčki (Ελληνικά)](https://create.roblox.com/docs/el-gr/production/monetization)

-

[Mađarski (magyar)](https://create.roblox.com/docs/hu-hu/production/monetization)

-

[Irski (Gaeilge)](https://create.roblox.com/docs/ga-ie/production/monetization)

-

[Latvijski (latviešu)](https://create.roblox.com/docs/lv-lv/production/monetization)

-

[Litvanski (lietuvių)](https://create.roblox.com/docs/lt-lt/production/monetization)

-

[Malteški (Malti)](https://create.roblox.com/docs/mt-mt/production/monetization)

-

[Portugalski - Portugal (português)](https://create.roblox.com/docs/pt-pt/production/monetization)

-

[Rumunjski (română)](https://create.roblox.com/docs/ro-ro/production/monetization)

-

[Slovački (slovenčina)](https://create.roblox.com/docs/sk-sk/production/monetization)

-

[Slovenski (slovenščina)](https://create.roblox.com/docs/sl-si/production/monetization)

-

[Švedski (svenska)](https://create.roblox.com/docs/sv-se/production/monetization)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
