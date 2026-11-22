<!-- Source: https://create.roblox.com/docs/hr-hr/projects/groups -->

Grupe (timovi) | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Projects](/docs/en-us/projects)
6. /
7. [Work in teams](/docs/en-us/projects/groups)

# Grupe (timovi)

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Roblox grupa  omogućava više kreatora da rade na istoj igri, koriste iste resurse, dijele dobit i daju priznanje svim suradnicima.

Vlasništvo grupe nad igrama pomaže kreatorima da surađuju i djeluju kao neovisni studiji. Ako dođe do sukoba unutar grupe, Roblox ne može pomoći u posredovanju ili rješavanju nesuglasica.

## [Kreiranje grupe](#kreiranje-grupe)[](#kreiranje-grupe)

Kreiranje grupe košta 100 Robuxa. Možete upravljati njenim [ulogama i dozvolama](#uloge-i-dozvole)  s [Kreatorskog nadzorne ploče](https://create.roblox.com/dashboard/creations)  ili [Zajednica](https://www.roblox.com/communities) .

Prije nego što kreirate grupu, pažljivo pročitajte [pravila i očekivanja](/docs/en-us/projects/group-guidelines)  za upravljanje grupom.

Da biste kreirali novu grupu:

1.

Idite na [Kreatorsku nadzornu ploču](https://create.roblox.com/dashboard/creations) , proširite prekidač računa u gornjem lijevom kutu i kliknite plus (+)  gumb.

2.

Na stranici Kreiraj grupu , učitajte sliku za logo grupe i unesite ime grupe.

3.

Kada ste spremni, kliknite gumb Kupiti . Nakon što je grupa kreirana, bit ćete preusmjereni na stranicu profila grupe gdje možete izmijeniti detalje grupe, uključujući dodavanje do tri društvene poveznice.

## [Uloge i dozvole](#uloge-i-dozvole)[](#uloge-i-dozvole)

Članovi grupe mogu biti dodijeljeni jednoj ili više uloga  unutar grupe, a svaka uloga ima dozvole  koje specificiraju sposobnosti svojih članova.

Konfiguracija uloga dostupna je samo ako ste vlasnik grupe ili imate dozvolu za kreiranje, konfiguriranje i dodjeljivanje uloga grupe.

Da biste upravljali dodjelama uloga grupe programatski s poslužitelja igre, koristite [HttpService](/docs/en-us/reference/engine/classes/HttpService)  za pozivanje podržanih Open Cloud Groups krajnjih točaka. Za postavke i uzorak koda, pogledajte [Koristite s Open Cloud](/docs/en-us/cloud-services/http-service#use-with-open-cloud) .

1.

S [Kreatorske nadzorne ploče](https://create.roblox.com/dashboard/creations) , proširite prekidač računa u gornjem lijevom kutu i odaberite grupu.

2.

Ponovno proširite prekidač računa i odaberite Uloge .

3.

Za svaku ulogu, pažljivo potvrdite dozvole pod Permissions  kartici.

Dozvole su organizirane u General , Creation  i Community  kategorije. Odjeljci u nastavku opisuju dozvole dostupne u svakoj kategoriji.

### [Općenito](#općenito)[](#općenito)

Opće dozvole

| Manage roles | | Članovi s ovom dozvolom mogu kreirati, uređivati, brisati, preuređivati i dodjeljivati ili oduzimati uloge ispod svoje najviše uloge. Mogu uređivati samo dozvole koje već posjeduju. |
| --- | --- |
| Assign or remove roles from members | | Članovi s ovom dozvolom mogu dodjeljivati ili oduzimati uloge ispod svoje najviše uloge bilo kojem članu. |
| Invite or approve members | | Članovi s ovom dozvolom mogu pozivati ljude u grupu i odobravati zahtjeve za pridruživanje. |
| Kick members | | Članovi s ovom dozvolom mogu ukloniti članove čija je najviša uloga ispod njihove. |
| Ban members | | Članovi s ovom dozvolom mogu zabraniti članove čija je najviša uloga ispod njihove. |
| Configure group profile | | Članovi s ovom dozvolom mogu konfigurirati profil grupe. |
| View audit logs | | Članovi s ovom dozvolom mogu pregledavati [revizijske dnevnike grupe](#revizijski-dnevnici-grupe) . |
| Manage allies and enemies | | Članovi s ovom dozvolom mogu upravljati saveznicima i neprijateljima grupe. |

### [Kreacija](#kreacija)[](#kreacija)

Creations

| Playtest experiences | | Članovi s ovom ulogom mogu igrati sve igre koje posjeduje grupa, čak i ako nisu objavljene široj publici. Opcionalno dostupno kao [dozvola po igri](/docs/en-us/projects/configure-games) . |
| Edit experiences | | Članovi s ovom ulogom mogu uređivati sve igre i [resurse](/docs/en-us/projects/assets)  koje posjeduje grupa i koristiti sve značajke u [Upravitelju podataka](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Ne uključuje uređivanje igre izvan [suradničke](/docs/en-us/projects/collaboration)  sesije ili spremanje mjesta iz jedne igre u drugu igru. Opcionalno dostupno kao [dozvola po igri](/docs/en-us/projects/configure-games) . |
| Publish experiences | | Članovi s ovom ulogom mogu i uređivati igre, kao gore, i također objavljivati igre na Robloxu. Opcionalno dostupno kao [dozvola po igri](/docs/en-us/projects/configure-games) . |
| Manage share links | | Članovi s ovom ulogom mogu kreirati/configurirati [poveznice za dijeljenje](/docs/en-us/production/promotion/share-links) . |
| Manage experience events | | Članovi s ovom ulogom mogu kreirati/configurirati [događaje iskustva](/docs/en-us/production/promotion/experience-events) . |
| Moderate experiences | | Članovi s ovom ulogom mogu pregledavati sve poruke u igri (samo za čitanje; član mora imati 18+) i zabraniti ili upravljati zabranjenim korisnicima u svim igrama koje posjeduje grupa. |
| Manage monetization for experiences | | Članovi s ovom ulogom mogu upravljati proizvodima monetizacije kao što su [prolazi](/docs/en-us/production/monetization/passes) , [proizvodi za developere](/docs/en-us/production/monetization/developer-products) , [pretplate](/docs/en-us/production/monetization/subscriptions)  i još mnogo toga. Opcionalno dostupno kao [dozvola po igri](/docs/en-us/projects/configure-games) . |
| Manage secrets for experiences | | Članovi s ovom ulogom mogu vidjeti popis [tajni](/docs/en-us/cloud-services/secrets)  i mogu kreirati, ažurirati i brisati tajne za sve igre koje posjeduje grupa. Članovi s ovom ulogom zahtijevaju Edit experiences  dozvolu za pregled stranice Tajne. Opcionalno dostupno kao [dozvola po igri](/docs/en-us/projects/configure-games) . |

Analytics

| View analytics for experiences | | Članovi s ovom ulogom mogu pristupiti [analitikama](/docs/en-us/production/analytics)  svih igara koje posjeduje grupa, čak i ako nemaju pristup uređivanju. Opcionalno dostupno kao [dozvola po igri](/docs/en-us/projects/configure-games) . |
| Manage alerts | | Članovi s ovom ulogom mogu kreirati i upravljati analitičkim upozorenjima. Uparite ovu dozvolu s View analytics for experiences  kako biste vidjeli oznake upozorenja izravno na grafikonima metrika. |

Monetization

| View group revenue | | Članovi s ovom ulogom mogu pregledavati Robux saldo grupe, sve konfigurirane ponavljajuće isplate i značajke bilježenja prihoda. |
| Manage and spend group revenue | | Članovi s ovom ulogom mogu pregledavati sve prihode grupe, kao gore, i također njima izravno upravljati. To uključuje postavljanje [ponavljajućih isplata](#ponavljaju%C4%87e-isplate)  i slanje [jednokratnih isplata](#jednokratne-isplate)  suradnicima. |
| Create ad campaigns for the group | | Članovi s ovom ulogom mogu oglašavati grupu. |

Avatar items

| Create avatar items | | Članovi s ovom ulogom mogu kreirati avatar stavke kao što su odjeća. |
| Configure avatar items | | Članovi s ovom ulogom mogu konfigurirati detalje prodaje, ponovna punjenja i sponzorstva za postojeće avatar stavke grupe. |

API

| Manage API keys | | Članovi s ovom ulogom mogu upravljati [Open Cloud API ključevima](/docs/en-us/cloud/auth/api-keys)  za grupu. |

Development items

| View development items | | Članovi s ovom ulogom mogu pregledavati razvojne stavke koje posjeduje grupa, na primjer Audio . |
| Manage development items | | Članovi s ovom ulogom mogu učitati i konfigurirati stavke razvoja resursa kao što su Decals . |
| Manage development item permissions | | Članovi s ovom ulogom mogu konfigurirati dozvole razvojnih stavki, na primjer dijeljenje zvuka. |

Data Stores

| View Data Stores for experiences | | Članovi s ovom ulogom mogu pregledavati podatkovne trgovine za sve igre grupe putem [Upravitelja podataka](/docs/en-us/cloud-services/data-stores/data-stores-manager) , ali ne mogu brisati podatke. Opcionalno dostupno kao [dozvola po igri](/docs/en-us/projects/configure-games) . |
| Edit Data Stores for experiences | | Članovi s ovom ulogom mogu brisati specifične ključeve unutar podatkovnih trgovina za sve igre grupe putem [Upravitelja podataka](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Opcionalno dostupno kao [dozvola po igri](/docs/en-us/projects/configure-games) . |
| Delete Data Stores for experiences | | Članovi s ovom ulogom mogu brisati cijele podatkovne trgovine za sve igre grupe putem [Upravitelja podataka](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Opcionalno dostupno kao [dozvola po igri](/docs/en-us/projects/configure-games) . |

Notifications

| Manage webhooks for experiences | | Članovi s ovom ulogom mogu navesti, kreirati, ažurirati i brisati webhooks za sve grupne iskustva. |

Communication

| Manage support tickets for experiences | | Članovi s ovom ulogom mogu upravljati podrškom za sve grupne iskustva. |

Legacy

| Upravljajte pristupom resursima ove grupe | | Članovi s ovom ulogom mogu kreirati i uređivati pristup resursima grupe. |

### [Zajednica](#zajednica)[](#zajednica)

Posts

| View community announcements | | Članovi s ovom ulogom mogu pregledavati zajedničke objave. |
| Create community announcements | | Članovi s ovom ulogom mogu kreirati zajedničke objave. |

Forums

| Manage categories | | Članovi s ovom ulogom mogu upravljati kategorijama foruma. |
| Create posts | | Članovi s ovom ulogom mogu kreirati objave na forumu. |
| Remove posts | | Članovi s ovom ulogom mogu ukloniti objave na forumu. |
| Lock posts | | Članovi s ovom ulogom mogu zaključati objave na forumu. |
| Pin posts | | Članovi s ovom ulogom mogu pričvrstiti objave na forumu. |
| Create comments | | Članovi s ovom ulogom mogu kreirati komentare na objave na forumu. |
| Remove comments | | Članovi s ovom ulogom mogu ukloniti komentare s objava na forumu. |

Content moderation

| View content moderation | | Članovi s ovom ulogom mogu pregledavati moderaciju sadržaja. |
| Manage content moderation | | Članovi s ovom ulogom mogu upravljati moderacijom sadržaja. |

Miscellaneous

| Bypass slow mode | | Članovi s ovom ulogom mogu zaobići spor način. |
| View community analytics | | Članovi s ovom ulogom mogu pregledavati analitiku zajednice. |

4.

VAŽNO

 Kliknite gumb Save  za primjenu postavki dozvola.

5.

OPCIONALNO

 Kliknite karticu Settings  i odaberite boju i postavku vidljivosti za ulogu, a zatim kliknite gumb Save .

Odjeljak Settings  uloge također je mjesto gdje vlasnici grupe i članovi s dovoljnim dozvolama mogu potpuno ukloniti ulogu putem gumba Izbriši ulogu .

Uloge su navedene u hijerarhijskom redu: uloga viša na popisu ima veću ovlast od uloge ispod nje. Ovaj redoslijed je važan jer neke dozvole dozvoljavaju članovima upravljanje ulogama ispod njihove najviše uloge.

Svaka uloga je ili javna  ili privatna . Javne uloge mogu se prikazati na stranici Zajednice i u iskustvima. Privatne uloge prikazuju se samo na površinama za upravljanje ulogama i dozvolama ovlaštenim članovima, ili članovima koji posjeduju privatnu ulogu. Vidljivost mijenja gdje se uloga pojavljuje; ne mijenja dozvole koje uloga dodjeljuje.

Da biste dodijelili Manage roles , Assign or remove roles from members , Manage access to this group’s resources , Manage and spend group revenue  ili Delete Data Stores for experiences , morate imati omogućenu dvostupanjsku provjeru.

## [Upravljanje članovima](#upravljanje-članovima)[](#upravljanje-članovima)

Konfiguracija članova dostupna je samo ako ste vlasnik grupe ili imate dozvolu za upravljanje drugim članovima i njihovim ulogama.

Da biste upravljali članovima s Kreatorske nadzorne ploče:

1.

Proširite prekidač računa u gornjem lijevom kutu i odaberite grupu.

2.

Ponovno proširite prekidač računa i odaberite Members .

3.

Koristite karticu Član  za pretraživanje postojećih članova ili filtriranje po ulozi. Koristite karticu Pozvani  za pregled čekajućih pozivnica.

Da biste dodali člana, kliknite gumb Invite  i pretražite njihovo korisničko ime. Roblox obavještava pozvane kreatore prema njihovim postavkama obavijesti. Također možete kopirati poveznicu grupe i izravno je podijeliti.

### [Upravljanje ulogama](#upravljanje-ulogama)[](#upravljanje-ulogama)

Možete upravljati dodjelama uloga s bilo koje stranice Members  ili specifične uloge:

-

Na stranici Members , kliknite gumb plus (+)  pored člana da biste otvorili izbornik uloga. Da biste dodijelili ulogu, kliknite gumb plus (+)  pored nje pod Dodaj uloge . Da biste oduzeli ulogu, kliknite gumb minus (-)  pored nje pod Trenutne uloge , ili kliknite gumb ×  na dodijeljenoj ulozi pored imena člana.

-

Na stranici Uloge , odaberite ulogu i otvorite njezinu karticu Members . Kliknite gumb Add members  da biste pretražili članove grupe i dodijelili ih ulozi. Da biste oduzeli člana, kliknite gumb minus (-)  na kraju njihovog reda.

### [Uklanjanje člana](#uklanjanje-člana)[](#uklanjanje-člana)

Da biste uklonili člana iz grupe, kliknite gumb ⋮  na kraju njihovog reda, odaberite Izbaci korisnika  i potvrdite radnju.

## [Upravljanje isplatama](#upravljanje-isplatama)[](#upravljanje-isplatama)

Ako ste vlasnik grupe ili imate ispravnu [dozvolu](#uloge-i-dozvole)  unutar Prihoda grupe , pronaći ćete stranicu Isplate  pod Financije  u lijevoj navigaciji. Ovdje možete slati jednokratne isplate, kao i definirati postotke podjele s drugim članovima.

Neke grupe možda nemaju ovu stranicu otključanu isprva iz raznih razloga, kao što su starost grupe ili nedovoljna sredstva za isplatu.

Isplate se ne mogu dijeliti među članovima grupe za igre koje naplaćuju [plaćeni pristup u lokalnoj valuti](/docs/en-us/production/monetization/paid-access-local-currency) .

### [Jednokratne isplate](#jednokratne-isplate)[](#jednokratne-isplate)

Jednokratne isplate mogu se izvršiti članovima u grupi, odabirući određeni iznos za svakog. Značajke sigurnosti uključuju 2FA izazove, dijaloge za potvrdu i provjere oko podobnosti članova koji primaju isplatu.

 ![Gumb za jednokratnu isplatu označen u odjeljku Isplate na Kreatorskoj nadzornoj ploči.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-One-Time.png)

Nakon što kliknete gumb Pošalji Robux , možete odabrati primatelje isplate iz skočnog prozora ili učitati .csv  datoteku s kolonama userId  i payoutInRobux , na primjer:

| userId | | payoutInRobux |
| 012345 | | 5000 |
| 098765 | | 7000 |

### [Ponavljajuće isplate](#ponavljajuće-isplate)[](#ponavljajuće-isplate)

Ponavljajuće isplate također se mogu izvršiti za cijelu grupu i  po igri, dodjeljujući postotak isplate svakom članu prije nego što ostatak uđe u ukupni saldo grupe.

 ![Gumbi za podjelu isplate označeni u odjeljku Isplate na Kreatorskoj nadzornoj ploči.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Split-Options.png)

Razmotrite sljedeći scenarij gdje se grupna igra Laser Maze  dijeli 40%–30%–10% među tri člana, s ostatkom od 20%.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-A.png)

Pod pretpostavkom da igra zaradi 1000 Robuxa, tri člana primaju 400, 300 i 100 Robuxa respektivno (40%–30%–10%).

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-B.png)

Ostatak od 200 Robuxa (20% od podjele igre) prelazi na postotke podjele grupe , definirane na 20%–20%–10% među istim tri člana; oni primaju dodatnih 40, 40 i 20 Robuxa respektivno.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-C.png)

Ostatak od 100 Robuxa (50% od podjele grupe) stavlja se u ukupni saldo grupe.

 ![Primjer dijagrama toka kako se podjele igre prvo distribuiraju članovima grupe, s ostatkom koji se uključuje u podjele grupe za konačnu distribuciju među grupom.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Splits-Example.png)

Napomena da prihodi od [privatnih servera](/docs/en-us/production/monetization/private-servers)  pretplata se ne mijenjaju ako kasnije prilagodite postotke podjele, što znači da ako igrač kupi pretplatu za privatni server, postotci podjele u trenutku kupnje će se primijeniti na tu određenu pretplatu zauvijek (dok se ne otkaže). Ova politika može se promijeniti u budućnosti.

## [Revizijski dnevnici grupe](#revizijski-dnevnici-grupe)[](#revizijski-dnevnici-grupe)

Članovi grupe s dozvolom View audit logs  mogu pregledavati promjene u grupi koristeći ove površine za upravljanje grupom:

-

Na Kreatorskoj nadzornoj ploči, odaberite Povijest aktivnosti  pod Suradnja .

-

Na Zajednicama, otvorite stranicu konfiguracije zajednice i odaberite Revizijski dnevnik .

Vlasnici grupa mogu koristiti ove dnevnike za praćenje aktivnosti koje bi mogle kršiti [smjernice grupe](/docs/en-us/projects/group-guidelines) .

## [Zaštita intelektualnog vlasništva](#zaštita-intelektualnog-vlasništva)[](#zaštita-intelektualnog-vlasništva)

Članovi grupe s dozvolom za uređivanje svih igara grupe mogu omogućiti postavku [Kopiranje mjesta](/docs/en-us/projects/configure-games#allow-copying)  za kreaciju, potencijalno dopuštajući cijeloj Roblox zajednici da je kopira i koristi resurse unutar nje. Kako bi se pomoglo u zaštiti intelektualnog vlasništva u grupi, vlasnik ili članovi s dovoljnim dozvolama trebali bi:

-

Potvrditi da je svaki član [dodijeljen odgovarajućoj ulozi](#upravljanje-ulogama) .

-

Provjeriti da svaka uloga grupe ima ispravne [dozvole](#uloge-i-dozvole) .

-

Potvrditi da je postavka [Kopiranje mjesta](/docs/en-us/projects/configure-games#allow-copying)  onemogućena prije nego što se dodaju privatni resursi.

## [Dodatne lokalizacije za ovu stranicu](#dodatne-lokalizacije-za-ovu-stranicu)[](#dodatne-lokalizacije-za-ovu-stranicu)

Za dodatne, lokalizirane verzije ove stranice koje nisu dostupne u odabiru jezika na stranici, pogledajte sljedeće poveznice:

-

[Bugarski (български)](https://create.roblox.com/docs/bg-bg/projects/groups)

-

[Hrvatski (hrvatski)](https://create.roblox.com/docs/hr-hr/projects/groups)

-

[Češki (čeština)](https://create.roblox.com/docs/cs-cz/projects/groups)

-

[Danski (dansk)](https://create.roblox.com/docs/da-dk/projects/groups)

-

[Nizozemski (Nederlands)](https://create.roblox.com/docs/nl-nl/projects/groups)

-

[Estonski (eesti)](https://create.roblox.com/docs/et-ee/projects/groups)

-

[Finski (suomi)](https://create.roblox.com/docs/fi-fi/projects/groups)

-

[Grčki (Ελληνικά)](https://create.roblox.com/docs/el-gr/projects/groups)

-

[Mađarski (magyar)](https://create.roblox.com/docs/hu-hu/projects/groups)

-

[Irski (Gaeilge)](https://create.roblox.com/docs/ga-ie/projects/groups)

-

[Latvijski (latviešu)](https://create.roblox.com/docs/lv-lv/projects/groups)

-

[Litvanski (lietuvių)](https://create.roblox.com/docs/lt-lt/projects/groups)

-

[Malteški (Malti)](https://create.roblox.com/docs/mt-mt/projects/groups)

-

[Portugalski - Portugal (português)](https://create.roblox.com/docs/pt-pt/projects/groups)

-

[Rumunjski (română)](https://create.roblox.com/docs/ro-ro/projects/groups)

-

[Slovački (slovenčina)](https://create.roblox.com/docs/sk-sk/projects/groups)

-

[Slovenski (slovenščina)](https://create.roblox.com/docs/sl-si/projects/groups)

-

[Švedski (svenska)](https://create.roblox.com/docs/sv-se/projects/groups)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
