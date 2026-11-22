<!-- Source: https://create.roblox.com/docs/lt-lt/production/monetization -->

Monetizacija | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)

# Monetizacija

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Monetizacija yra Roblox bendros struktūros dalis, skirta teikti vertę kūrėjams. Yra keletas skirtingų būdų monetizuoti savo turinį, įskaitant [prenumeratas](#prenumeratos) , mokesčio už prieigą rinkimą [Robux](#mokama-prieiga-robux)  arba [vietine valiuta](#mokama-prieiga-vietine-valiuta) , [daiktų ar gebėjimų, kuriuos vartotojai gali įsigyti](#k%C5%ABr%C4%97jo-produktai) , [privatūs serveriai](#privat%C5%ABs-serveriai) , leidžiantys vartotojams žaisti tik su draugais, ir [modelių bei papildinių pardavimą](/docs/en-us/production/creator-store#distribute-and-sell-assets)  kitiems kūrėjams Kūrėjų parduotuvėje.

Jei nuspręsite pasiūlyti įsigyjamą turinį, Roblox automatiškai nerekorduoja produkto ar pirkimo informacijos. Norint išvengti duomenų praradimo, turite atsargiai saugoti šiuos duomenis naudodami [DataStoreService](/docs/en-us/reference/engine/classes/DataStoreService)  arba kitą duomenų saugojimo paslaugą, kuri yra hostinta už Roblox ribų.

Norėdami išsamiai sužinoti apie optimalios monetizacijos strategijų kūrimą jūsų patirčiai, žr. [Monetizacijos pagrindai](/docs/en-us/production/game-design/monetization-foundations) .

## [Monetizacijos strategijos](#monetizacijos-strategijos)[](#monetizacijos-strategijos)

Būkite atidūs monetizacijos metodams, kuriuos įvedate į savo žaidimą, nes mūsų vartotojai greičiausiai neigiamai įvertins  jūsų žaidimą, jei jie nesutiks su jūsų strategijomis. Taip pat visi kūrėjai turi būti skaidrūs dėl bet kokios [atsitiktinės monetizacijos](/docs/en-us/production/monetization/paid-random-items)  ir naudoti šias mechanikas atsakingai.

Kai kurios populiarios monetizacijos strategijos nemokamiems žaidimams kitose platformose nėra rekomenduojamos Roblox. Pavyzdžiui, paskyrimo mechanika ir laikmačiai, kurie gali būti pašalinti arba perkeliami, gali gerai veikti kitose platformose, tačiau šios mechanikos yra nepopuliarios Roblox vartotojams, kurie nepritaria, kad jų pramoga baigiasi per anksti.

Šios geriausios praktikos rekomendacijos yra populiarios tarp geriausių kūrėjų, pritaikant monetizacijos strategijas Roblox platformai ir auditorijai.

Atkreipkite dėmesį, kad taikydami šias technikas ir apsvarstymus, nesate garantuoti, kad galėsite efektyviai monetizuoti savo žaidimą. Prisiminkite, kad jums nereikia turėti jokių finansinių tikslų, kad galėtumėte smagiai kurti Roblox žaidimą.

### [Turistai ir vietiniai](#turistai-ir-vietiniai)[](#turistai-ir-vietiniai)

Gali būti naudinga galvoti apie Roblox vartotojus dviem kategorijomis:

-

Turistai  paprastai šokinėja iš vieno žaidimo į kitą, teikdami pirmenybę įvairovei, o ne gylio. Jie teikia pirmenybę daiktams, turintiems tiesioginį poveikį, arba padedantiems žaidimui būti smagesniam, arba išsiskirti, kviesdami kitus vartotojus klausti, kaip ir kur jie gavo tą daiktą.

-

Vietiniai  labiau linkę sutelkti dėmesį į konkretų žaidimą ar mažesnį žaidimų rinkinį. Jie įsitraukia gilesniu būdu ir paprastai sudaro beveik visą žaidimo įsitraukusių vartotojų bazę. Jie labiau domisi daiktais, turinčiais ilgalaikę naudą, pavyzdžiui, [mūšio praeitimi](/docs/en-us/production/game-design/season-pass-design) .

Norėdami sužinoti daugiau apie tai, kaip sukurti savo žaidimą, atsižvelgdami į Roblox vartotojus, žr. [Dizainas Roblox](/docs/en-us/production/game-design/design-for-roblox) .

### [Socialinės funkcijos](#socialinės-funkcijos)[](#socialinės-funkcijos)

Roblox vartotojai linkę mėgti žaidimus, kurie pabrėžia socialinį bendravimą. Pavyzdžiui, turint daiktų ar renginių, kurie yra prieinami tik ribotą laiką , galima sukurti jaudulį aplink tą turinį. Prekybos  sistema skatina vartotojus bendrauti. Nors abi sistemos gali būti sėkmingos atskirai, jos ypač veiksmingos, kai yra sujungtos.

### [Gyvi operacijos](#gyvi-operacijos)[](#gyvi-operacijos)

Po paleidimo palaikymas yra daugeliu atžvilgių lengvesnis Roblox nei kitose platformose, nes galite greitai siųsti atnaujinimus, kad pagerintumėte savo žaidimą.

Dažni  turinio atnaujinimai gali būti naudingi, jei norite išlaikyti įsitraukimą su savo žaidimu laikui bėgant. Roblox vartotojai yra įpratę būti įtraukti reguliariais atnaujinimais, ir gali būti daug sunkiau atgauti vartotojo susidomėjimą nei išlaikyti aktyvius. Savaitinis atnaujinimų ritmas  yra idealus. Bent jau siekite mėnesinių atnaujinimų. Dėl diskusijos apie turinio ritmą žr. [Turinio ritmas](/docs/en-us/production/game-design/content-updates) .

Kuriant atnaujinimus, laikykitės konkrečios temos . Tai palengvina vartotojams suprasti naują atnaujinimą ir pasakyti, koks turinys yra naujas, kai jie prisijungia. Tai taip pat padeda jums koordinuoti savo turinį ir reklamos turtą. Pavyzdžiui, jei pridedate naują zoologijos sodą savo vaidmenų žaidime, įsitikinkite, kad visas naujas turinys turi tam tikrą ryšį su zoologijos sodo tema.

Nebijokite priversti vartotojus užsidirbti prieigą  prie naujo turinio. Nauji vartotojai plūsta žaisti naujų atnaujinimų, tačiau jei jie nesijaučia, kad pasiekė kažką žaidime, jie gali greitai pasitraukti. Galite sukurti jausmą, kad atnaujinimas buvo uždirbtas, arba monetizuodami atnaujinimo turinį, arba sukurdami išankstines sąlygas, kad galėtumėte žaisti naują turinį.

Norėdami sužinoti daugiau apie tai, kaip sukurti efektyvų po paleidimo palaikymą savo žaidimui, žr. [Gyvi operacijos](/docs/en-us/production/game-design/liveops-essentials) .

## [Produktai](#produktai)[](#produktai)

### [Įtraukiančios reklamos](#įtraukiančios-reklamos)[](#įtraukiančios-reklamos)

[Įtraukiančių reklamų](/docs/en-us/production/monetization/immersive-ads)  sistema leidžia jums įterpti reklamos vienetus į savo žaidimą, leidžiančius Roblox programiškai teikti reklamos turinį iš reklamuotojų jūsų aktyviems vartotojams.

![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/Overview-ImageAd.jpg) Vaizdo reklamos formatas

Portalinės reklamos formatas

### [Roblox Plus](#roblox-plus)[](#roblox-plus)

[Roblox Plus](/docs/en-us/production/monetization/roblox-plus)  leidžia jums uždirbti per padidėjusias žaidimo pirkimus, kuriuos skatina Roblox subsidijuoti vartotojų nuolaidos, registracijos premijos už kiekvieną naują prenumeratorių, kurį atvedate, ir įsitraukimą į mokamus privačius serverius.

### [Prenumeratos](#prenumeratos)[](#prenumeratos)

[Prenumeratos](/docs/en-us/production/monetization/subscriptions)  žaidimuose leidžia jums pasiūlyti vartotojams nuolatines naudas už mėnesinį mokestį.

![](https://prod.docsiteassets.roblox.com/assets/monetization/subscriptions/Example-Subscriptions.png) Žaidimų prenumeratų pavyzdžiai

### [Praėjimai](#praėjimai)[](#praėjimai)

[Praėjimas](/docs/en-us/production/monetization/passes)  leidžia jums imti vienkartinį Robux mokestį , kad vartotojai galėtų pasiekti specialias privilegijas žaidime, tokias kaip įėjimas į ribotą zoną, žaidimo avataro daiktas arba nuolatinis galingumas.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/passes/passes-sample.png)

### [Kūrėjo produktai](#kūrėjo-produktai)[](#kūrėjo-produktai)

[Kūrėjo produktas](/docs/en-us/production/monetization/developer-products)  yra daiktas ar gebėjimas, kurį vartotojas gali įsigyti daugiau nei vieną kartą, pavyzdžiui, žaidimo valiutą, šaudmenis ar eliksyrus. Galite skatinti pirkimus, juos registruoti ir gauti produkto informaciją per skriptus.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/developer-products/Buy-Product-Example.jpg)

### [Valdomos kainos](#valdomos-kainos)[](#valdomos-kainos)

[Valdomos kainos](/docs/en-us/production/monetization/managed-pricing)  yra suvienodinta sistema, kuri sujungia [regionines kainas](/docs/en-us/production/monetization/regional-pricing)  ir [kainų optimizavimą](/docs/en-us/production/monetization/price-optimization)  vienoje vietoje. Jūs prisijungiate vieną kartą, pasirenkate, kuriuos daiktus įtraukti, ir Valdomos kainos palaiko jūsų kainas optimizuotas per produktus ir regionus laikui bėgant.

### [Kainų optimizavimas](#kainų-optimizavimas)[](#kainų-optimizavimas)

[Kainų optimizavimas](/docs/en-us/production/monetization/price-optimization)  leidžia jums rasti geriausius kainų taškus jūsų praėjimams ir kūrėjo produktams, kurie gali padėti jums uždirbti daugiau pinigų laikui bėgant, išlaikant konkurencingas kainas.

### [Mokama prieiga Robux](#mokama-prieiga-robux)[](#mokama-prieiga-robux)

[Mokama prieiga Robux](/docs/en-us/production/monetization/paid-access-robux)  leidžia jums imti vartotojams vienkartinį Robux mokestį  už prieigą prie jūsų žaidimo. Kai kurie kūrėjai laikinai naudoja šią funkciją, kad sukurtų uždarą beta versiją, kurioje jų labiausiai įsitraukę vartotojai gali turėti ankstyvą prieigą prie žaidimo ir padėti testuoti bei teikti atsiliepimus.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/paid-access/Buy-Access-Example.png)

### [Mokama prieiga vietine valiuta](#mokama-prieiga-vietine-valiuta)[](#mokama-prieiga-vietine-valiuta)

[Mokama prieiga vietine valiuta](/docs/en-us/production/monetization/paid-access-local-currency)  leidžia jums imti vartotojams vienkartinį mokestį jų vietine valiuta  už prieigą prie jūsų žaidimo. Jei jų vietinė valiuta nėra prieinama, jiems imamas mokestis JAV doleriais. Kai kurie kūrėjai laikinai naudoja šią funkciją, kad sukurtų uždarą beta versiją, kurioje jų labiausiai įsitraukę vartotojai gali turėti ankstyvą prieigą prie žaidimo ir padėti testuoti bei teikti atsiliepimus.

### [Privatūs serveriai](#privatūs-serveriai)[](#privatūs-serveriai)

[Privatus serveris](/docs/en-us/production/monetization/private-servers)  yra prenumeratos pagrindu veikianti funkcija, leidžianti vartotojui nuspręsti, kas gali žaisti žaidimą su jais. Nors privatūs serveriai gali būti nemokami, galite taip pat naudoti privačius serverius kaip monetizacijos metodą, imdami vartotojams, kurie nori pasiekti privačius serverius, mėnesinį Robux mokestį .

### [Katalogo mokesčiai ir komisijos](#katalogo-mokesčiai-ir-komisijos)[](#katalogo-mokesčiai-ir-komisijos)

Galite kurti ir parduoti aksesuarus bei drabužius Rinkoje. Po to, kai sumokėsite įkėlimo mokestį ir pateiksite naują turtą patvirtinimui, moderavimo komanda peržiūri jūsų turtą ir, jei jis patvirtinamas, prideda jūsų turtą į katalogą.

Kiekvieną kartą, kai vartotojai įsigyja jūsų katalogo daiktą, gausite [komisiją](/docs/en-us/marketplace/marketplace-fees-and-commissions) . Jei vartotojai perka jūsų katalogo daiktą žaidime naudodami [avataro tikrinimo meniu](/docs/en-us/players/avatar-inspect-menu)  arba [avataro redagavimo paslaugą](/docs/en-us/players/avatar-editor) , žaidimo savininkas taip pat gauna komisiją.

### [Papildiniai ir modeliai](#papildiniai-ir-modeliai)[](#papildiniai-ir-modeliai)

[Papildinys](/docs/en-us/studio/plugins)  yra plėtinys, kuris prideda papildomą funkcionalumą Studijai, o [modelis](/docs/en-us/parts/models)  yra pakartotinai naudojamas turto tipas. Galite pasiūlyti abu kitiems kūrėjams [Kūrėjų parduotuvėje](/docs/en-us/production/creator-store)  nemokamai arba galite juos parduoti už Jungtinių Amerikos Valstijų dolerius  (minimalus kaina yra 4,99 USD už papildinius ir 2,99 USD už modelius). Roblox siūlo rinkoje pirmaujančią pajamų dalį už šias pardavimus, nes tik mokesčiai ir mokėjimo apdorojimo mokesčiai yra atimami. Daugiau informacijos apie papildinių ir modelių pardavimą žr. [Kūrėjų parduotuvė - Platinti ir parduoti turtą](/docs/en-us/production/creator-store#distribute-and-sell-assets) .

Kiekvienam pirkimui taikomas 30 dienų užstato laikotarpis. Roblox laiko jūsų pardavimo dalį 30 dienų nuo pardavimo datos.

## [Gairės](#gairės)[](#gairės)

Kuriant ir įgyvendinant monetizacijos produktus savo žaidimuose, apsvarstykite šias gaires, kad užtikrintumėte, jog jūsų monetizacijos metodai būtų tinkami visiems auditorijos nariams platformoje.

### [Produktų pristatymas](#produktų-pristatymas)[](#produktų-pristatymas)

Norint išlaikyti saugumą ir teisingumą, turite pristatyti monetizacijos produktus būdu, kuris yra skaidrus, sąžiningas ir vartotojui draugiškas. Pavyzdžiui, jei siūlote nuolaidas, jos turi būti tikros  ir teisingos :

-

Nuolaida nėra tikra, jei daiktas visada "parduodamas" už tą pačią Robux sumą.

-

Nuolaida nėra teisinga, jei ji siūloma tik labai trumpą laiką, spaudžiant vartotojus pirkti kuo greičiau.

Vartotojai niekada neturi būti klaidinami, sumišę ar spaudžiami pirkti būdais, kurių jie nenorėjo, ir jie visada turėtų turėti laisvę aiškiai ir sąmoningai pasirinkti gauti prenumeratą arba išleisti Robux konkrečiam daiktui. Kaip bendrą gairę, yra keletas praktikų, kurių visada reikėtų vengti pristatant monetizacijos produktus savo auditorijai:

-

Nepriklausomai nuo to, ar prenumerata ar daiktas beveik baigiasi, ar tik trumpam laikui, jei tai nėra tiesa.

-

Nenaudokite laikmačio, kuris nėra tikslus arba automatiškai atsinaujina tam pačiam daiktui.

Pavyzdžiui, jei jūsų žaidimas apima "dienos pasiūlymą", kuris sako, kad jis yra prieinamas tik 24 valandas, tačiau tada kiekvieną kartą, kai vartotojai prisijungia, rodo tą patį pranešimą ir jis niekada nesibaigia, jūs sukūrėte klaidingą skubėjimo jausmą, kuris nėra draugiškas vartotojui.

### [Skatinimas pasaulinei auditorijai](#skatinimas-pasaulinei-auditorijai)[](#skatinimas-pasaulinei-auditorijai)

Roblox yra pasaulinė bendruomenė visų amžiaus grupių vartotojams, todėl skatinimai jūsų žaidimuose turėtų būti tinkami visiems auditorijos nariams pagal numatytuosius nustatymus. Jei tam tikri monetizacijos produktai yra ribojami tam tikrose vietose, pavyzdžiui, mokami atsitiktiniai daiktai, Roblox teikia [PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  API, kad padėtų jums užtikrinti, jog šie produktai būtų matomi tik tinkamiems vartotojams.

[PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  grąžina, ar vartotojas yra tinkamas tam tikriems daiktams ar funkcijoms pagal jų vietą, amžių ir platformą. Turite integruoti šį API į savo žaidimą, kad atitiktumėte savo atitikties įsipareigojimus, įskaitant nustatymą, ar kiekvienas vartotojas yra:

-

Tinkamas pirkti prenumeratas ar komercinius produktus.

-

Leidžiama naudoti mokamus atsitiktinius daiktus, mokamą daiktų prekybą ar matyti įtraukiančias reklamas.

Jei vartotojas gali naudoti Robux arba ką nors kitą, kas buvo gauta su Robux, kad gautų atsitiktinį atlygį, privalote naudoti [PolicyService](/docs/en-us/reference/engine/classes/PolicyService) , kad užblokuotumėte šią funkciją vartotojams, kurie neturi teisės naudoti atsitiktinių daiktų mainais už Robux.

Kaip bendrą gairę, venkite naudoti spaudžiančius ar skubius pranešimus bendraujant su nepilnamečiais, nes didelio spaudimo kalba gali būti per daug.

| ** Vengti kalbos** | | ** Rekomenduojami alternatyvai** |
| --- | --- |
| "GAUKITE DABAR" | | "Peržiūrėti daiktą" |
| "PASKUTINĖ GALIMYBĖ, VEIKITE DABAR" | | "Žiūrėti kainą" |
| "PIRKITE PRIEŠ JIS IŠNYKS!" | | "Atidaryti parduotuvę" |

## [Papildomos lokalizacijos šiai svetainei](#papildomos-lokalizacijos-šiai-svetainei)[](#papildomos-lokalizacijos-šiai-svetainei)

Dėl papildomų, lokalizuotų šios svetainės versijų, kurios nėra prieinamos svetainės kalbos pasirinkiklyje, žr. šiuos nuorodas:

-

[Bulgarų (български)](https://create.roblox.com/docs/bg-bg/production/monetization)

-

[Kroatų (hrvatski)](https://create.roblox.com/docs/hr-hr/production/monetization)

-

[Čekų (čeština)](https://create.roblox.com/docs/cs-cz/production/monetization)

-

[Danų (dansk)](https://create.roblox.com/docs/da-dk/production/monetization)

-

[Nyderlandų (Nederlands)](https://create.roblox.com/docs/nl-nl/production/monetization)

-

[Estų (eesti)](https://create.roblox.com/docs/et-ee/production/monetization)

-

[Suomių (suomi)](https://create.roblox.com/docs/fi-fi/production/monetization)

-

[Graikų (Ελληνικά)](https://create.roblox.com/docs/el-gr/production/monetization)

-

[Vengrų (magyar)](https://create.roblox.com/docs/hu-hu/production/monetization)

-

[Airių (Gaeilge)](https://create.roblox.com/docs/ga-ie/production/monetization)

-

[Latvių (latviešu)](https://create.roblox.com/docs/lv-lv/production/monetization)

-

[Lietuvių (lietuvių)](https://create.roblox.com/docs/lt-lt/production/monetization)

-

[Maltiečių (Malti)](https://create.roblox.com/docs/mt-mt/production/monetization)

-

[Portugalų - Portugalas (português)](https://create.roblox.com/docs/pt-pt/production/monetization)

-

[Rumunų (română)](https://create.roblox.com/docs/ro-ro/production/monetization)

-

[Slovakų (slovenčina)](https://create.roblox.com/docs/sk-sk/production/monetization)

-

[Slovėnų (slovenščina)](https://create.roblox.com/docs/sl-si/production/monetization)

-

[Švedų (svenska)](https://create.roblox.com/docs/sv-se/production/monetization)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
