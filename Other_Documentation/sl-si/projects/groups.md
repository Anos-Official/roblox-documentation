<!-- Source: https://create.roblox.com/docs/sl-si/projects/groups -->

Skupine (ekipe) | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Projects](/docs/en-us/projects)
6. /
7. [Work in teams](/docs/en-us/projects/groups)

# Skupine (ekipe)

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Skupina Roblox skupina  omogoča več ustvarjalcem, da delajo na isti igri, uporabljajo iste vire, delijo dobičke in priznajo vse prispevke.

Lastništvo skupine nad igrami pomaga ustvarjalcem sodelovati in delovati kot neodvisni studii. Če pride do konflikta znotraj skupine, Roblox ne more pomagati pri mediaciji ali reševanju nesoglasij.

## [Ustvarjanje skupine](#ustvarjanje-skupine)[](#ustvarjanje-skupine)

Ustvarjanje skupine stane 100 Robux. Njene [vloge in dovoljenja](#vloge-in-dovoljenja)  lahko upravljate iz [Nadzorne plošče ustvarjalca](https://create.roblox.com/dashboard/creations)  ali [Skupnosti](https://www.roblox.com/communities) .

Pred ustvarjanjem skupine natančno preberite [pravila in pričakovanja](/docs/en-us/projects/group-guidelines)  za upravljanje skupin.

Za ustvarjanje nove skupine:

1.

Pojdite na [Nadzorno ploščo ustvarjalca](https://create.roblox.com/dashboard/creations) , razširite preklopnik računov v zgornjem levem kotu in kliknite gumb plus (+) .

2.

Na strani Ustvari skupino  naložite sliko za logotip skupine in vnesite ime skupine.

3.

Ko ste pripravljeni, kliknite gumb Nakup . Ko je skupina ustvarjena, boste preusmerjeni na stran profila skupine, kjer lahko spremenite podrobnosti skupine, vključno z dodajanjem do treh družbenih povezav.

## [Vloge in dovoljenja](#vloge-in-dovoljenja)[](#vloge-in-dovoljenja)

Člani skupine lahko dobijo eno ali več vlog  znotraj skupine, vsaka vloga pa ima dovoljenja , ki določajo sposobnosti njenih članov.

Konfiguracija vlog je dostopna le, če ste lastnik skupine ali imate dovoljenje za ustvarjanje, konfiguracijo in dodeljevanje vlog skupine.

Za programatsko upravljanje dodelitev vlog skupine iz strežnika igre uporabite [HttpService](/docs/en-us/reference/engine/classes/HttpService) , da pokličete podprte končne točke Open Cloud Groups. Za nastavitev in vzorčno kodo si oglejte [Uporaba z Open Cloud](/docs/en-us/cloud-services/http-service#use-with-open-cloud) .

1.

Iz [Nadzorne plošče ustvarjalca](https://create.roblox.com/dashboard/creations)  razširite preklopnik računov v zgornjem levem kotu in izberite skupino.

2.

Ponovno razširite preklopnik računov in izberite Vloge .

3.

Za vsako vlogo natančno potrdite dovoljenja pod zavihkom Permissions .

Dovoljenja so organizirana v kategorije General , Creation  in Community . Spodnje sekcije opisujejo dovoljenja, ki so na voljo v vsaki kategoriji.

### [Splošno](#splošno)[](#splošno)

Splošna dovoljenja

| Manage roles | | Člani s tem dovoljenjem lahko ustvarjajo, urejajo, brišejo, preurejajo in dodeljujejo ali odvzemajo vloge pod njihovo najvišjo vlogo. Urejajo lahko le dovoljenja, ki jih že imajo. |
| --- | --- |
| Assign or remove roles from members | | Člani s tem dovoljenjem lahko dodelijo ali odvzamejo vloge pod njihovo najvišjo vlogo kateremu koli članu. |
| Invite or approve members | | Člani s tem dovoljenjem lahko povabijo ljudi v skupino in odobrijo prošnje za pridružitev. |
| Kick members | | Člani s tem dovoljenjem lahko odstranijo člane, katerih najvišja vloga je pod njihovo. |
| Ban members | | Člani s tem dovoljenjem lahko prepovejo člane, katerih najvišja vloga je pod njihovo. |
| Configure group profile | | Člani s tem dovoljenjem lahko konfigurirajo profil skupine. |
| View audit logs | | Člani s tem dovoljenjem lahko ogledajo [revizijske dnevnike skupine](#revizijski-dnevniki-skupine) . |
| Manage allies and enemies | | Člani s tem dovoljenjem lahko upravljajo zaveznike in sovražnike skupine. |

### [Ustvarjanje](#ustvarjanje)[](#ustvarjanje)

Creations

| Playtest experiences | | Člani s to vlogo lahko igrajo vse igre, ki jih ima skupina, tudi če niso objavljene širši javnosti. Na voljo kot [dovoljenje na ravni igre](/docs/en-us/projects/configure-games) . |
| Edit experiences | | Člani s to vlogo lahko urejajo vse igre in [sredstva](/docs/en-us/projects/assets) , ki jih ima skupina, ter uporabljajo vse funkcije v [Upravitelju podatkovnih skladišč](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Ne vključuje urejanja igre zunaj [sodelovalne](/docs/en-us/projects/collaboration)  seje ali shranjevanja mesta iz ene igre v drugo igro. Na voljo kot [dovoljenje na ravni igre](/docs/en-us/projects/configure-games) . |
| Publish experiences | | Člani s to vlogo lahko tako urejajo igre, kot je navedeno zgoraj, in tudi objavljajo igre na Roblox. Na voljo kot [dovoljenje na ravni igre](/docs/en-us/projects/configure-games) . |
| Manage share links | | Člani s to vlogo lahko ustvarjajo/configurirajo [povezave za deljenje](/docs/en-us/production/promotion/share-links) . |
| Manage experience events | | Člani s to vlogo lahko ustvarjajo/configurirajo [izkušnje dogodkov](/docs/en-us/production/promotion/experience-events) . |
| Moderate experiences | | Člani s to vlogo lahko vidijo vse sporočila v igri (samo za branje; član mora biti star 18 let ali več) in prepovejo ali upravljajo prepovedane uporabnike v vseh igrah, ki jih ima skupina. |
| Manage monetization for experiences | | Člani s to vlogo lahko upravljajo monetizacijske izdelke, kot so [dovoljenja](/docs/en-us/production/monetization/passes) , [izdelki za razvijalce](/docs/en-us/production/monetization/developer-products) , [naročnine](/docs/en-us/production/monetization/subscriptions)  in še več. Na voljo kot [dovoljenje na ravni igre](/docs/en-us/projects/configure-games) . |
| Manage secrets for experiences | | Člani s to vlogo lahko vidijo seznam [skrivnosti](/docs/en-us/cloud-services/secrets)  in lahko ustvarjajo, posodabljajo in brišejo skrivnosti za vse igre, ki jih ima skupina. Člani s to vlogo potrebujejo dovoljenje Edit experiences  za ogled strani Skrivnosti. Na voljo kot [dovoljenje na ravni igre](/docs/en-us/projects/configure-games) . |

Analytics

| View analytics for experiences | | Člani s to vlogo lahko dostopajo do [analitik](/docs/en-us/production/analytics)  vseh iger, ki jih ima skupina, tudi če nimajo dostopa za urejanje. Na voljo kot [dovoljenje na ravni igre](/docs/en-us/projects/configure-games) . |
| Manage alerts | | Člani s to vlogo lahko ustvarjajo in upravljajo analitična opozorila. Povežite to dovoljenje z View analytics for experiences , da vidite opombe opozoril neposredno na grafih metrik. |

Monetization

| View group revenue | | Člani s to vlogo lahko vidijo stanje Robux skupine, vse konfigurirane ponavljajoče se izplačila in funkcije beleženja prihodkov. |
| Manage and spend group revenue | | Člani s to vlogo lahko vidijo vse prihodke skupine, kot je navedeno zgoraj, in jih tudi neposredno upravljajo. To vključuje nastavitev [ponavljajočih se izplačil](#ponavljajo%C4%8Da-se-izpla%C4%8Dila)  in pošiljanje [enkratnih izplačil](#enkratna-izpla%C4%8Dila)  sodelavcem. |
| Create ad campaigns for the group | | Člani s to vlogo lahko oglašujejo skupino. |

Avatar items

| Create avatar items | | Člani s to vlogo lahko ustvarjajo predmete za avatar, kot so oblačila. |
| Configure avatar items | | Člani s to vlogo lahko konfigurirajo podrobnosti prodaje, ponovno založitev in sponzorstva za obstoječe predmete za avatar skupine. |

API

| Manage API keys | | Člani s to vlogo lahko upravljajo [ključne API-je Open Cloud](/docs/en-us/cloud/auth/api-keys)  za skupino. |

Development items

| View development items | | Člani s to vlogo lahko vidijo razvojne predmete, ki jih ima skupina, na primer Zvočne posnetke . |
| Manage development items | | Člani s to vlogo lahko nalagajo in konfigurirajo razvojne predmete, kot so Dekali . |
| Manage development item permissions | | Člani s to vlogo lahko konfigurirajo dovoljenja razvojnih predmetov, na primer deljenje zvoka. |

Data Stores

| View Data Stores for experiences | | Člani s to vlogo lahko vidijo podatkovne sklade za vse igre skupine preko [Upravitelja podatkovnih skladišč](/docs/en-us/cloud-services/data-stores/data-stores-manager) , vendar ne morejo brisati podatkov. Na voljo kot [dovoljenje na ravni igre](/docs/en-us/projects/configure-games) . |
| Edit Data Stores for experiences | | Člani s to vlogo lahko brišejo specifične ključe znotraj podatkovnih skladišč za vse igre skupine preko [Upravitelja podatkovnih skladišč](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Na voljo kot [dovoljenje na ravni igre](/docs/en-us/projects/configure-games) . |
| Delete Data Stores for experiences | | Člani s to vlogo lahko brišejo celotne podatkovne sklade za vse igre skupine preko [Upravitelja podatkovnih skladišč](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Na voljo kot [dovoljenje na ravni igre](/docs/en-us/projects/configure-games) . |

Notifications

| Manage webhooks for experiences | | Člani s to vlogo lahko naštejejo, ustvarjajo, posodabljajo in brišejo spletne klice za vse izkušnje skupine. |

Communication

| Manage support tickets for experiences | | Člani s to vlogo lahko upravljajo podporne karte za vse izkušnje skupine. |

Legacy

| Upravljajte dostop do virov te skupine | | Člani s to vlogo lahko ustvarjajo in urejajo dostop do virov skupine. |

### [Skupnost](#skupnost)[](#skupnost)

Posts

| View community announcements | | Člani s to vlogo lahko vidijo skupnostne napovedi. |
| Create community announcements | | Člani s to vlogo lahko ustvarjajo skupnostne napovedi. |

Forums

| Manage categories | | Člani s to vlogo lahko upravljajo kategorije forumov. |
| Create posts | | Člani s to vlogo lahko ustvarjajo objave na forumu. |
| Remove posts | | Člani s to vlogo lahko odstranjujejo objave na forumu. |
| Lock posts | | Člani s to vlogo lahko zaklenejo objave na forumu. |
| Pin posts | | Člani s to vlogo lahko pripnejo objave na forumu. |
| Create comments | | Člani s to vlogo lahko ustvarjajo komentarje na objave na forumu. |
| Remove comments | | Člani s to vlogo lahko odstranjujejo komentarje iz objav na forumu. |

Content moderation

| View content moderation | | Člani s to vlogo lahko vidijo moderiranje vsebine. |
| Manage content moderation | | Člani s to vlogo lahko upravljajo moderiranje vsebine. |

Miscellaneous

| Bypass slow mode | | Člani s to vlogo lahko obidejo počasni način. |
| View community analytics | | Člani s to vlogo lahko vidijo analitiko skupnosti. |

4.

POZORNO

 Kliknite gumb Save  za uporabo nastavitev dovoljenj.

5.

NEOBVEZNO

 Kliknite zavihek Settings  in izberite barvo ter nastavitev vidnosti za vlogo, nato kliknite gumb Save .

Oddelek Settings  vloge je tudi mesto, kjer lahko lastniki skupin in člani z zadostnimi dovoljenji popolnoma odstranijo vlogo preko gumba Izbriši vlogo .

Vloge so navedene v hierarhičnem redu: vloga, ki je višja na seznamu, ima večjo avtoriteto kot vloga pod njo. Ta vrstni red je pomemben, ker nekatera dovoljenja dovoljujejo članom upravljanje vlog pod njihovo najvišjo vlogo.

Vsaka vloga je bodisi javna  bodisi zasebna . Javne vloge se lahko prikažejo na strani Skupnosti in v izkušnjah. Zasebne vloge so prikazane le na površinah za upravljanje vlog in dovoljenj pooblaščenim članom ali članom, ki imajo zasebno vlogo. Spremembe vidnosti vplivajo na to, kje se vloga prikaže; ne spreminjajo pa dovoljenj, ki jih vloga podeljuje.

Za dodelitev Manage roles , Assign or remove roles from members , Manage access to this group’s resources , Manage and spend group revenue  ali Delete Data Stores for experiences  morate imeti omogočeno dvofaktorsko preverjanje.

## [Upravljanje članov](#upravljanje-članov)[](#upravljanje-članov)

Konfiguracija članov je dostopna le, če ste lastnik skupine ali imate dovoljenje za upravljanje drugih članov in njihovih vlog.

Za upravljanje članov iz Nadzorne plošče ustvarjalca:

1.

Razširite preklopnik računov v zgornjem levem kotu in izberite skupino.

2.

Ponovno razširite preklopnik računov in izberite Members .

3.

Uporabite zavihek Član  za iskanje obstoječih članov ali jih filtrirajte po vlogi. Uporabite zavihek Povabljeni , da pregledate čakajoče povabila.

Za dodajanje člana kliknite gumb Invite  in poiščite njihovo uporabniško ime. Roblox obvešča povabljene ustvarjalce v skladu z njihovimi nastavitvami obveščanja. Povezavo skupine lahko tudi kopirate in jo delite neposredno.

### [Upravljanje vlog](#upravljanje-vlog)[](#upravljanje-vlog)

Upravljate lahko dodelitve vlog bodisi na strani Members  bodisi na specifični vlogi:

-

Na strani Members  kliknite gumb plus (+)  poleg člana, da odprete meni vlog. Za dodelitev vloge kliknite gumb plus (+)  poleg nje pod Dodaj vloge . Za odvzem vloge kliknite gumb minus (-)  poleg nje pod Trenutne vloge , ali kliknite gumb ×  na dodeljeni vlogi poleg imena člana.

-

Na strani Vloge  izberite vlogo in odprite njen zavihek Members . Kliknite gumb Add members  za iskanje članov skupine in dodelitev vlog. Za odvzem člana kliknite gumb minus (-)  na koncu njihove vrstice.

### [Odstranitev člana](#odstranitev-člana)[](#odstranitev-člana)

Za odstranitev člana iz skupine kliknite gumb ⋮  na koncu njihove vrstice, izberite Izključi uporabnika  in potrdite dejanje.

## [Upravljanje izplačil](#upravljanje-izplačil)[](#upravljanje-izplačil)

Če ste lastnik skupine ali imate pravilno [dovoljenje](#vloge-in-dovoljenja)  znotraj Prihodkov skupine , boste našli stran Izplačila  pod Finančne zadeve  v levem navigacijskem meniju. Tukaj lahko pošljete enkratna izplačila ter določite odstotne deleže z drugimi člani.

Nekatere skupine morda sprva nimajo te strani odklenjene iz različnih razlogov, kot so starost skupine ali nezadostna sredstva za izplačilo.

Izplačila se ne morejo deliti med člani skupine za igre, ki zaračunavajo [plačan dostop v lokalni valuti](/docs/en-us/production/monetization/paid-access-local-currency) .

### [Enkratna izplačila](#enkratna-izplačila)[](#enkratna-izplačila)

Enkratna izplačila se lahko izvedejo članom v seriji, pri čemer se izbere določen znesek za vsakega. Varnostne funkcije vključujejo izzive 2FA, potrditvene dialoge in preverjanja glede upravičenosti članov, ki prejemajo plačilo.

 ![Gumb za enkratno izplačilo, označen v razdelku Izplačila na Nadzorni plošči ustvarjalca.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-One-Time.png)

Ko kliknete gumb Pošlji Robux , lahko izberete prejemnike iz pojavnega okna ali naložite datoteko .csv  s stolpci userId  in payoutInRobux , na primer:

| userId | | payoutInRobux |
| 012345 | | 5000 |
| 098765 | | 7000 |

### [Ponavljajoča se izplačila](#ponavljajoča-se-izplačila)[](#ponavljajoča-se-izplačila)

Ponavljajoča se izplačila se lahko prav tako izvajajo po celotni skupini in  na ravni igre, pri čemer se dodeli odstotno izplačilo vsakemu članu, preden preostanek vstopi v skupni saldo skupine.

 ![Gumbi za delitev izplačil, označeni v razdelku Izplačila na Nadzorni plošči ustvarjalca.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Split-Options.png)

Upoštevajte naslednji scenarij, kjer je igra skupine Laser Maze  razdeljena 40%–30%–10% med tremi člani, preostanek pa je 20%.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-A.png)

Če igra zasluži 1000 Robux, trije člani prejmejo 400, 300 in 100 Robux, kar ustreza 40%–30%–10%.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-B.png)

Preostalih 200 Robux (20% razdelitve igre) preide na odstotke razdelitve skupine , ki so določeni na 20%–20%–10% med istimi tremi člani; prejmejo dodatnih 40, 40 in 20 Robux.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-C.png)

Preostalih 100 Robux (50% razdelitve skupine) se doda v skupni saldo skupine.

 ![Primer poteka, kako se razdelijo dobički iz iger najprej članom skupine, preostanek pa se upošteva v razdelitvah skupine za končno razdelitev med skupino.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Splits-Example.png)

Upoštevajte, da prihodki iz [privatnih strežnikov](/docs/en-us/production/monetization/private-servers)  ne spremenijo, če kasneje prilagodite odstotke razdelitve, kar pomeni, da če igralec kupi naročnino na privatni strežnik, se bodo odstotki razdelitve ob nakupu uporabili za to naročnino za vedno (dokler se ne prekliče). Ta politika se lahko v prihodnosti spremeni.

## [Revizijski dnevniki skupine](#revizijski-dnevniki-skupine)[](#revizijski-dnevniki-skupine)

Člani skupine s dovoljenjem View audit logs  lahko pregledajo spremembe skupine z uporabo teh površin za upravljanje skupin:

-

Na Nadzorni plošči ustvarjalca izberite Zgodovina dejavnosti  pod Sodelovanje .

-

V Skupnostih odprite stran za konfiguracijo skupnosti in izberite Revizijski dnevnik .

Lastniki skupin lahko te dnevnike uporabijo za spremljanje dejavnosti, ki bi lahko kršila [pravila skupine](/docs/en-us/projects/group-guidelines) .

## [Zaščita intelektualne lastnine](#zaščita-intelektualne-lastnine)[](#zaščita-intelektualne-lastnine)

Člani skupine, ki imajo dovoljenje za urejanje vseh iger skupine, lahko omogočijo nastavitev [Kopiranje mest](/docs/en-us/projects/configure-games#allow-copying)  za ustvarjanje, kar lahko omogoči celotni skupnosti Roblox, da ga kopira in uporablja vire v njem. Da bi zaščitili intelektualno lastnino v skupini, bi morali lastnik ali člani z zadostnimi dovoljenji:

-

Potrdite, da je vsak član [dodeljen ustrezni vlogi](#upravljanje-vlog) .

-

Preverite, da ima vsaka vloga skupine pravilna [dovoljenja](#vloge-in-dovoljenja) .

-

Potrdite, da je nastavitev [Kopiranje mest](/docs/en-us/projects/configure-games#allow-copying)  onemogočena, preden se dodajo zasebna sredstva.

## [Dodatne lokalizacije za to stran](#dodatne-lokalizacije-za-to-stran)[](#dodatne-lokalizacije-za-to-stran)

Za dodatne, lokalizirane različice te strani, ki niso na voljo v izbiri jezika na spletnem mestu, si oglejte naslednje povezave:

-

[Bolgarščina (български)](https://create.roblox.com/docs/bg-bg/projects/groups)

-

[Hrvaščina (hrvatski)](https://create.roblox.com/docs/hr-hr/projects/groups)

-

[Češčina (čeština)](https://create.roblox.com/docs/cs-cz/projects/groups)

-

[Danščina (dansk)](https://create.roblox.com/docs/da-dk/projects/groups)

-

[Nizozemščina (Nederlands)](https://create.roblox.com/docs/nl-nl/projects/groups)

-

[Estonščina (eesti)](https://create.roblox.com/docs/et-ee/projects/groups)

-

[Finščina (suomi)](https://create.roblox.com/docs/fi-fi/projects/groups)

-

[Grščina (Ελληνικά)](https://create.roblox.com/docs/el-gr/projects/groups)

-

[Madžarščina (magyar)](https://create.roblox.com/docs/hu-hu/projects/groups)

-

[Irščina (Gaeilge)](https://create.roblox.com/docs/ga-ie/projects/groups)

-

[Latvijščina (latviešu)](https://create.roblox.com/docs/lv-lv/projects/groups)

-

[Litvanščina (lietuvių)](https://create.roblox.com/docs/lt-lt/projects/groups)

-

[Malteščina (Malti)](https://create.roblox.com/docs/mt-mt/projects/groups)

-

[Portugalščina - Portugalska (português)](https://create.roblox.com/docs/pt-pt/projects/groups)

-

[Romunščina (română)](https://create.roblox.com/docs/ro-ro/projects/groups)

-

[Slovaščina (slovenčina)](https://create.roblox.com/docs/sk-sk/projects/groups)

-

[Slovenščina (slovenščina)](https://create.roblox.com/docs/sl-si/projects/groups)

-

[Švedščina (svenska)](https://create.roblox.com/docs/sv-se/projects/groups)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
