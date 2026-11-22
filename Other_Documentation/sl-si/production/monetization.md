<!-- Source: https://create.roblox.com/docs/sl-si/production/monetization -->

Monetizacija | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)

# Monetizacija

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Monetizacija je del celotne strukture Roblox, ki ustvarja vrednost za ustvarjalce. Obstaja več različnih pristopov za monetizacijo vaših vsebin, vključno z uporabo [naročnin](#naro%C4%8Dnine) , zaračunavanjem pristojbine za dostop v [Robux](#pla%C4%8Dan-dostop-v-robux)  ali [lokalni valuti](#pla%C4%8Dan-dostop-v-lokalni-valuti) , zagotavljanjem [predmetov ali sposobnosti, ki jih uporabniki lahko kupijo](#izdelki-razvijalcev) , ponujanjem [zasebnih strežnikov](#zasebni-stre%C5%BEniki)  za uporabnike, da igrajo samo s prijatelji, in [prodajo modelov in vtičnikov](/docs/en-us/production/creator-store#distribute-and-sell-assets)  drugim ustvarjalcem v Creator Store.

Če se odločite ponuditi vsebine za nakup, Roblox samodejno ne beleži informacij o izdelkih ali nakupih. Da preprečite izgubo podatkov, morate te podatke skrbno shraniti z uporabo [DataStoreService](/docs/en-us/reference/engine/classes/DataStoreService)  ali druge storitve za shranjevanje podatkov, ki je gostovana zunaj Robloxa.

Za poglobljen vpogled v oblikovanje optimalnih strategij monetizacije za vašo izkušnjo si oglejte [Osnove monetizacije](/docs/en-us/production/game-design/monetization-foundations) .

## [Strategije monetizacije](#strategije-monetizacije)[](#strategije-monetizacije)

Bodite pozorni na metode monetizacije, ki jih uvedete v svojo igro, saj bodo naši uporabniki verjetno zmanjšali oceno  vaše igre, če ne odobrijo vaših strategij. Prav tako morajo vsi razvijalci biti pregledni glede kakršne koli [monetizacije, ki temelji na naključju](/docs/en-us/production/monetization/paid-random-items)  in te mehanizme uporabljati odgovorno.

Nekatere priljubljene strategije monetizacije za igre, ki so brezplačne za igranje na drugih platformah, niso priporočljive za Roblox. Na primer, mehanizmi za določanje časa in časovniki, ki jih je mogoče odstraniti ali premakniti, morda dobro delujejo na drugih platformah, vendar so ti mehanizmi nepriljubljeni med uporabniki Robloxa, ki se pritožujejo, da se njihova zabava konča prezgodaj.

Naslednji predlogi najboljših praks so priljubljeni med najboljšimi razvijalci za prilagajanje strategij monetizacije platformi Roblox in njenemu občinstvu.

Upoštevajte, da z uporabo teh tehnik in premislekov niste zagotovljeni, da boste učinkovito monetizirali svojo igro. Ne pozabite, da ne potrebujete nobenih finančnih ciljev, da bi se zabavali pri ustvarjanju igre Roblox.

### [Turisti in domačini](#turisti-in-domačini)[](#turisti-in-domačini)

Pomembno je razmišljati o uporabnikih Robloxa v dveh kategorijah:

-

Turisti  običajno skačejo iz ene igre v drugo, pri čemer dajejo prednost raznolikosti pred globino. Raje imajo predmete z neposrednimi učinki, bodisi da igra postane bolj zabavna bodisi da izstopajo, kar druge uporabnike vabi, da se sprašujejo, kako in kje so pridobili predmet.

-

Domačini  se bolj verjetno osredotočajo na določeno igro ali manjši nabor iger. Bolj se poglobijo in običajno tvorijo skoraj celotno angažirano uporabniško bazo igre. Zanimajo jih predmeti z dolgoročnimi koristmi, kot je [bitka prehod](/docs/en-us/production/game-design/season-pass-design) .

Če želite izvedeti več o tem, kako oblikovati svojo igro z mislijo na uporabnike Robloxa, si oglejte [Oblikovanje za Roblox](/docs/en-us/production/game-design/design-for-roblox) .

### [Družbene funkcije](#družbene-funkcije)[](#družbene-funkcije)

Uporabniki Robloxa običajno uživajo v igrah, ki poudarjajo socialno interakcijo. Na primer, imeti predmete ali dogodke, ki so na voljo le za omejen čas , lahko ustvari navdušenje okoli te vsebine. Sistem trgovanja  spodbuja uporabnike k interakciji. Medtem ko lahko oba sistema uspešno delujeta sama, sta še posebej učinkovita, ko sta združena.

### [Živi operativni dogodki](#živi-operativni-dogodki)[](#živi-operativni-dogodki)

Podpora po zagonu je v mnogih pogledih lažja na Robloxu kot na drugih platformah, saj lahko hitro pošljete posodobitve za izboljšanje svoje igre.

Pogoste  posodobitve vsebine so lahko koristne, če želite ohraniti angažiranost s svojo igro skozi čas. Uporabniki Robloxa so navajeni, da jih redne posodobitve angažirajo, in veliko težje je ponovno pridobiti zanimanje uporabnika, kot pa ohraniti aktivne. Idealna je tedenska frekvenca  posodobitev. Vsaj si prizadevajte za mesečne posodobitve. Za razpravo o frekvenci vsebine si oglejte delavnico [frekvenca vsebine](/docs/en-us/production/game-design/content-updates) .

Ko oblikujete posodobitve, jih osredotočite na določeno temo . To uporabnikom olajša razumevanje nove posodobitve in prepoznavanje nove vsebine, ko se pridružijo. Pomaga vam tudi usklajevati vašo vsebino in promocijske materiale. Na primer, če dodajate nov živalski vrt v svojo igro igranja vlog, poskrbite, da bo vsa nova vsebina povezana s temo živalskega vrta.

Ne bojte se uporabnikom omogočiti, da si pridobijo  dostop do nove vsebine. Novi uporabniki se bodo zgrnili, da bi igrali nove posodobitve, vendar, če ne bodo imeli občutka, da so v igri dosegli  nekaj, se lahko kmalu odjavijo. Ustvarite lahko občutek zaslužka posodobitve bodisi z monetizacijo vsebine posodobitve bodisi z ustvarjanjem predpogojev za igranje nove vsebine.

Če želite izvedeti več o tem, kako oblikovati učinkovito podporo po zagonu za svojo igro, si oglejte [Osnove živih operativnih dogodkov](/docs/en-us/production/game-design/liveops-essentials) .

## [Izdelki](#izdelki)[](#izdelki)

### [Potopne oglase](#potopne-oglase)[](#potopne-oglase)

Sistem [potopnih oglasov](/docs/en-us/production/monetization/immersive-ads)  vam omogoča, da v svojo igro vstavite oglasne enote, ki omogočajo Robloxu, da programatično prikazuje oglasno vsebino oglaševalcev vašim aktivnim uporabnikom.

![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/Overview-ImageAd.jpg) Format slikovnega oglasa

Format portalnega oglasa

### [Roblox Plus](#roblox-plus)[](#roblox-plus)

[Roblox Plus](/docs/en-us/production/monetization/roblox-plus)  vam omogoča, da zaslužite z večjimi nakupi v igri, ki jih spodbujajo popusti za uporabnike, ki jih subvencionira Roblox, bonusi za prijavo za vsakega novega naročnika, ki ga pripeljete, in angažiranjem v plačanih zasebnih strežnikih.

### [Naročnine](#naročnine)[](#naročnine)

[Naročnine](/docs/en-us/production/monetization/subscriptions)  znotraj iger vam omogočajo, da uporabnikom ponudite ponavljajoče se koristi za mesečno pristojbino.

![](https://prod.docsiteassets.roblox.com/assets/monetization/subscriptions/Example-Subscriptions.png) Primeri naročnin za igre

### [Prehodi](#prehodi)[](#prehodi)

[Prehod](/docs/en-us/production/monetization/passes)  vam omogoča, da zaračunate enkratno pristojbino v Robux , da uporabniki pridobijo posebne privilegije znotraj igre, kot so vstop v omejeno območje, predmet za avatar v igri ali trajni bonus.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/passes/passes-sample.png)

### [Izdelki razvijalcev](#izdelki-razvijalcev)[](#izdelki-razvijalcev)

[Izdelek razvijalca](/docs/en-us/production/monetization/developer-products)  je predmet ali sposobnost, ki jo lahko uporabnik kupi več kot enkrat, kot so valuta v igri, strelivo ali napoji. Lahko spodbujate nakupe, jih beležite in pridobite informacije o izdelku preko skriptiranja.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/developer-products/Buy-Product-Example.jpg)

### [Urejena cena](#urejena-cena)[](#urejena-cena)

[Urejena cena](/docs/en-us/production/monetization/managed-pricing)  je enoten sistem, ki združuje [regionalno ceno](/docs/en-us/production/monetization/regional-pricing)  in [optimizacijo cen](/docs/en-us/production/monetization/price-optimization)  na enem mestu. Enkrat se prijavite, izberete, katere predmete vključiti, in Urejena cena ohranja vaše cene optimizirane skozi čas za izdelke in regije.

### [Optimizacija cen](#optimizacija-cen)[](#optimizacija-cen)

[Optimizacija cen](/docs/en-us/production/monetization/price-optimization)  vam omogoča, da najdete najboljše cenovne točke za vaše prehode in izdelke razvijalcev, kar vam lahko pomaga zaslužiti več denarja skozi čas, medtem ko ohranjate konkurenčne cene.

### [Plačan dostop v Robux](#plačan-dostop-v-robux)[](#plačan-dostop-v-robux)

[Plačan dostop v Robux](/docs/en-us/production/monetization/paid-access-robux)  vam omogoča, da uporabnikom zaračunate enkratno pristojbino v Robux  za dostop do vaše igre. Nekateri razvijalci to funkcijo začasno uporabljajo za ustvarjanje zaprtega beta, kjer lahko njihovi najbolj angažirani uporabniki zgodaj dostopajo do igre in pomagajo pri testiranju in povratnih informacijah.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/paid-access/Buy-Access-Example.png)

### [Plačan dostop v lokalni valuti](#plačan-dostop-v-lokalni-valuti)[](#plačan-dostop-v-lokalni-valuti)

[Plačan dostop v lokalni valuti](/docs/en-us/production/monetization/paid-access-local-currency)  vam omogoča, da uporabnikom zaračunate enkratno pristojbino v njihovi lokalni valuti  za dostop do vaše igre. Če njihova lokalna valuta ni na voljo, se zaračuna v USD. Nekateri razvijalci to funkcijo začasno uporabljajo za ustvarjanje zaprtega beta, kjer lahko njihovi najbolj angažirani uporabniki zgodaj dostopajo do igre in pomagajo pri testiranju in povratnih informacijah.

### [Zasebni strežniki](#zasebni-strežniki)[](#zasebni-strežniki)

Zasebni [zasebni strežnik](/docs/en-us/production/monetization/private-servers)  je funkcija na osnovi naročnine, ki uporabniku omogoča, da odloči, kdo lahko igra igro z njim. Medtem ko so lahko zasebni strežniki brezplačni, lahko zasebne strežnike uporabite tudi kot metodo monetizacije, tako da zaračunate uporabnikom, ki želijo dostopati do zasebnih strežnikov, mesečno pristojbino v Robux .

### [Provizije in provizije za katalog](#provizije-in-provizije-za-katalog)[](#provizije-in-provizije-za-katalog)

Lahko ustvarite in prodajate dodatke in oblačila na trgu. Ko plačate pristojbino za nalaganje in predložite novo sredstvo v odobritev, ekipa za moderiranje pregleda vaše sredstvo in, če je odobreno, doda vaše sredstvo v katalog.

Prejeli boste [provizijo](/docs/en-us/marketplace/marketplace-fees-and-commissions)  vsakič, ko uporabniki kupijo vaš katalog. Če uporabniki kupijo vaš katalog znotraj igre z uporabo [menija za pregled avatarja](/docs/en-us/players/avatar-inspect-menu)  ali [storitev za urejanje avatarjev](/docs/en-us/players/avatar-editor) , lastnik igre prav tako prejme provizijo.

### [Vtičniki in modeli](#vtičniki-in-modeli)[](#vtičniki-in-modeli)

[Vtičnik](/docs/en-us/studio/plugins)  je razširitev, ki dodaja dodatno funkcionalnost Studiu, model pa je vrsta ponovne uporabe sredstev. Oboje lahko ponudite drugim ustvarjalcem v [Creator Store](/docs/en-us/production/creator-store)  brezplačno ali pa jih prodajate za ameriške dolarje  (minimalna cena je 4,99 USD za vtičnike in 2,99 USD za modele). Roblox ponuja vodilni delež prihodkov za te prodaje, saj se odštejejo le davki in stroški obdelave plačil. Za več informacij o prodaji vtičnikov in modelov si oglejte [Creator Store - Distribucija in prodaja sredstev](/docs/en-us/production/creator-store#distribute-and-sell-assets) .

Za vsak nakup velja 30-dnevni zadržek. Roblox zadrži vaš delež od prodaje 30 dni, od datuma prodaje.

## [Smernice](#smernice)[](#smernice)

Ko oblikujete in izvajate monetizacijske izdelke v svoje igre, upoštevajte naslednje smernice, da zagotovite, da so vaše metode monetizacije primerne za vse občinstvo na platformi.

### [Predstavljanje izdelkov](#predstavljanje-izdelkov)[](#predstavljanje-izdelkov)

Da ohranite varnost in poštenost, morate monetizacijske izdelke predstaviti na način, ki je pregleden, pošten in prijazen do uporabnika. Na primer, če ponujate popuste, morajo biti pristni  in pošteni :

-

Popust ni pristni, če je predmet vedno "v akciji" za enako količino Robux.

-

Popust ni pošten, če je ponujen le za zelo kratek čas, kar pritiska na uporabnike, da čim hitreje opravijo nakup.

Uporabniki nikoli ne smejo biti zavedeni, zmedeni ali prisiljeni v nakupe na načine, ki jih niso nameravali, in vedno bi morali imeti svobodo, da sprejmejo jasno, namerno odločitev o pridobitvi naročnine ali porabi Robux za določen predmet. Kot splošno vodilo obstajajo nekatere prakse, ki se jim je treba vedno izogibati pri predstavljanju monetizacijskih izdelkov vašemu občinstvu:

-

Ne trdite, da je naročnina ali predmet skoraj razprodan ali na voljo le za kratek čas, če to ni res.

-

Ne uporabljajte štoparice, ki ni natančna ali se samodejno ponastavi za isti predmet.

Na primer, če vaša igra vključuje "ponudbo dneva", ki pravi, da je na voljo le 24 ur, vendar nato to sporočilo prikažete uporabnikom vsakič, ko se prijavijo, in nikoli ne preneha biti na voljo, ste ustvarili lažen občutek nujnosti, ki ni prijazen do uporabnika.

### [Promocija globalnim občinstvom](#promocija-globalnim-občinstvom)[](#promocija-globalnim-občinstvom)

Roblox je globalna skupnost za uporabnike vseh starosti, zato bi morale biti promocije v vaših igrah privlačne za vse občinstvo po privzetku. Če so določeni monetizacijski izdelki omejeni v določenih lokacijah, kot so plačani naključni predmeti, Roblox zagotavlja API [PolicyService](/docs/en-us/reference/engine/classes/PolicyService) , da vam pomaga zagotoviti, da so ti izdelki vidni le upravičenim uporabnikom.

[PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  vrne, ali je uporabnik upravičen do določenih predmetov ali funkcij glede na njihovo lokacijo, starost in platformo. Ta API morate integrirati v svojo igro, da izpolnite svoje obveznosti glede skladnosti, vključno z ugotavljanjem, ali je vsak uporabnik:

-

Upravičen do nakupa naročnin ali trgovinskih izdelkov.

-

Dovoljeni plačani naključni predmeti, trgovanje s plačanimi predmeti ali ogled potopnih oglasov.

Če lahko uporabnik uporabi Robux ali kaj drugega, kar je bilo pridobljeno z Robux, da pridobi naključno nagrado, ste dolžni uporabiti [PolicyService](/docs/en-us/reference/engine/classes/PolicyService) , da blokirate to funkcijo za uporabnike, ki jim ni dovoljeno uporabljati naključnih predmetov v zameno za Robux.

Kot splošno vodilo se izogibajte uporabi pritiskajočih ali nujnih sporočil pri interakciji z mladoletniki, saj lahko jezik pod pritiskom preobremeni:

| ** Jezik, ki se mu je treba izogibati** | | ** Priporočene alternative** |
| --- | --- |
| "PRIDOBITE TO TAKOJ" | | "Ogled predmeta" |
| "ZADNJA PRILOŽNOST, UKREPITE TAKOJ" | | "Oglejte si ceno" |
| "KUPITE, PREDEN JE IZGUBLJENO!" | | "Odprite trgovino" |

## [Dodatne lokalizacije za to stran](#dodatne-lokalizacije-za-to-stran)[](#dodatne-lokalizacije-za-to-stran)

Za dodatne, lokalizirane različice te strani, ki niso na voljo v izbiri jezikov na spletnem mestu, si oglejte naslednje povezave:

-

[Bolgarščina (български)](https://create.roblox.com/docs/bg-bg/production/monetization)

-

[Hrvaščina (hrvatski)](https://create.roblox.com/docs/hr-hr/production/monetization)

-

[Češčina (čeština)](https://create.roblox.com/docs/cs-cz/production/monetization)

-

[Danščina (dansk)](https://create.roblox.com/docs/da-dk/production/monetization)

-

[Nizozemščina (Nederlands)](https://create.roblox.com/docs/nl-nl/production/monetization)

-

[Estonščina (eesti)](https://create.roblox.com/docs/et-ee/production/monetization)

-

[Finščina (suomi)](https://create.roblox.com/docs/fi-fi/production/monetization)

-

[Grščina (Ελληνικά)](https://create.roblox.com/docs/el-gr/production/monetization)

-

[Madžarščina (magyar)](https://create.roblox.com/docs/hu-hu/production/monetization)

-

[Irščina (Gaeilge)](https://create.roblox.com/docs/ga-ie/production/monetization)

-

[Latvijščina (latviešu)](https://create.roblox.com/docs/lv-lv/production/monetization)

-

[Litvanščina (lietuvių)](https://create.roblox.com/docs/lt-lt/production/monetization)

-

[Malteščina (Malti)](https://create.roblox.com/docs/mt-mt/production/monetization)

-

[Portugalščina - Portugalska (português)](https://create.roblox.com/docs/pt-pt/production/monetization)

-

[Romunščina (română)](https://create.roblox.com/docs/ro-ro/production/monetization)

-

[Slovaščina (slovenčina)](https://create.roblox.com/docs/sk-sk/production/monetization)

-

[Slovenščina (slovenščina)](https://create.roblox.com/docs/sl-si/production/monetization)

-

[Švedščina (svenska)](https://create.roblox.com/docs/sv-se/production/monetization)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
