<!-- Source: https://create.roblox.com/docs/et-ee/production/monetization -->

Monetiseerimine | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)

# Monetiseerimine

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Monetiseerimine on osa Roblox'i üldstruktuurist, et pakkuda väärtust loojatele. On mitmeid erinevaid lähenemisviise oma sisu monetiseerimiseks, sealhulgas [tellimuste](#tellimused)  kasutamine, juurdemaksu nõudmine [Robuxis](#tasuline-juurdep%C3%A4%C3%A4s-robuxis)  või [kohalikus valuutas](#tasuline-juurdep%C3%A4%C3%A4s-kohalikus-valuutas) , [esemete või võimete pakkumine, mida kasutajad saavad osta](#arendaja-tooted) , [privaatserverite](#privaatserverid)  pakkumine, kus kasutajad saavad mängida ainult sõpradega, ja [mudelite ja pluginite müük](/docs/en-us/production/creator-store#distribute-and-sell-assets)  teistele loojatele Looja Poest.

Kui otsustate pakkuda ostetavat sisu, ei salvesta Roblox automaatselt toote- või ostuteavet. Andmete kadumise vältimiseks peate hoolikalt salvestama need andmed, kasutades [DataStoreService](/docs/en-us/reference/engine/classes/DataStoreService)  või mõnda muud andmesalvestusteenust, mis on hostitud väljaspool Roblox'i.

Süvitsi minek optimaalsete monetiseerimisstrateegiate kavandamisse oma kogemuse jaoks, vaata [Monetiseerimise alused](/docs/en-us/production/game-design/monetization-foundations) .

## [Monetiseerimisstrateegiad](#monetiseerimisstrateegiad)[](#monetiseerimisstrateegiad)

Olge ettevaatlikud monetiseerimismeetodite osas, mida oma mängu tutvustate, kuna meie kasutajad tõenäoliselt hääletavad  teie mängu vastu, kui nad ei kiida heaks teie strateegiaid. Samuti peavad kõik arendajad olema läbipaistvad igasuguste [juhuslike monetiseerimise](/docs/en-us/production/monetization/paid-random-items)  osas ja kasutama neid mehhanisme vastutustundlikult.

Mõned populaarsed monetiseerimisstrateegiad tasuta mängude jaoks teistel platvormidel ei ole Roblox'is soovitatavad. Näiteks kohtumismehhanismid ja taimerid, mida saab eemaldada või edasi lükata, võivad teistel platvormidel hästi toimida, kuid need mehhanismid ei ole Roblox'i kasutajate seas populaarsed, kes peavad probleemiks, et nende lõbu lõppeb enneaegselt.

Järgmised parimate praktikate soovitused on populaarsed tipparendajate seas, et kohandada monetiseerimisstrateegiaid Roblox'i platvormi ja publiku jaoks.

Palun pange tähele, et nende tehnikate ja kaalutluste rakendamine ei garanteeri, et suudate oma mängu tõhusalt monetiseerida. Pea meeles, et sul ei pea olema mingeid rahalisi eesmärke, et Roblox'i mängu loomisega lõbusalt aega veeta.

### [Turistid ja kohalikud](#turistid-ja-kohalikud)[](#turistid-ja-kohalikud)

On kasulik mõelda Roblox'i kasutajatest kahes kategoorias:

-

Turistid  hüppavad tavaliselt ühest mängust teise, eelistades mitmekesisust sügavusele. Nad eelistavad esemeid, millel on kohesed efektid, kas mängimise lõbusamaks muutmiseks või silma paistmiseks, kutsudes teisi kasutajaid küsima, kuidas ja kust nad selle eseme said.

-

Kohalikud  keskenduvad tõenäolisemalt konkreetsele mängule või väiksemale mängude kogumile. Nad osalevad sügavamalt ja moodustavad tavaliselt peaaegu kogu mängu aktiivse kasutajabaasi. Nad on rohkem huvitatud esemetest, millel on pikaajalised eelised, nagu [lahingupass](/docs/en-us/production/game-design/season-pass-design) .

Kuidas oma mängu Roblox'i kasutajate jaoks kujundada, vaata [Kujunda Roblox'i jaoks](/docs/en-us/production/game-design/design-for-roblox) .

### [Sotsiaalsed funktsioonid](#sotsiaalsed-funktsioonid)[](#sotsiaalsed-funktsioonid)

Roblox'i kasutajad kipuvad nautima mänge, mis rõhutavad sotsiaalset suhtlemist. Näiteks, kui esemed või üritused on saadaval ainult piiratud aja  jooksul, võib see tekitada elevust selle sisu ümber. Kaubanduse  süsteem julgustab kasutajaid suhtlema. Kuigi mõlemad süsteemid võivad iseseisvalt olla edukad, on need eriti tõhusad koos.

### [Elu pärast käivitamist](#elu-pärast-käivitamist)[](#elu-pärast-käivitamist)

Pärast käivitamist on toetamine paljuski lihtsam Roblox'is kui teistel platvormidel, kuna saate kiiresti välja anda uuendusi, et oma mängu parandada.

Sagedased  sisuuuendused võivad olla kasulikud, kui soovite oma mängu ajas aktiivsena hoida. Roblox'i kasutajad on harjunud regulaarselt uuendustega, ja kasutaja huvi taastamine võib olla palju raskem kui aktiivsete huvide säilitamine. Uuenduste jaoks on ideaalne nädalane rütm . Aluseks püüdke vähemalt kuus uuendust. Sisu rütmi arutamiseks vaata Level Up [sisu rütmi töötuba](/docs/en-us/production/game-design/content-updates) .

Uuenduste kavandamisel hoidke need keskendunud konkreetsele teemale . See muudab kasutajatele uue uuenduse mõistmise ja uue sisu tuvastamise lihtsamaks, kui nad liituvad. See aitab teil ka oma sisu ja reklaamivara koordineerida. Näiteks, kui lisate oma rollimängu uue Loomaaia, veenduge, et kogu uus sisu oleks seotud Loomaaia teemaga.

Ärge kartke, et kasutajad teenivad oma juurdepääsu  uuele sisule. Uued kasutajad tulevad mängima uusi uuendusi, kuid kui nad ei tunne, et nad on mängus saavutanud  midagi, võivad nad varsti lahkuda. Saate luua tunde, et uuenduse teenimine toimub kas uuenduse sisu monetiseerimise või uue sisu mängimise eeltingimuste loomise kaudu.

Kuidas kujundada tõhusat toetust pärast käivitamist, vaata [Elu pärast käivitamist](/docs/en-us/production/game-design/liveops-essentials) .

## [Tooted](#tooted)[](#tooted)

### [Immersiivsed reklaamid](#immersiivsed-reklaamid)[](#immersiivsed-reklaamid)

[immersiivsete reklaamide](/docs/en-us/production/monetization/immersive-ads)  süsteem võimaldab teil sisestada reklaamielemente oma mängu, mis võimaldavad Roblox'il programmiliselt edastada reklaamisisu reklaamijatest teie aktiivsetele kasutajatele.

![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/Overview-ImageAd.jpg) Pildi reklaami formaat

Portaali reklaami formaat

### [Roblox Plus](#roblox-plus)[](#roblox-plus)

[Roblox Plus](/docs/en-us/production/monetization/roblox-plus)  võimaldab teil teenida suurenenud mängusiseste ostude kaudu, mida juhivad Roblox'i toetatud kasutaja allahindlused, registreerimisboonused iga uue tellija eest, keda te toote, ja osalemine tasulistes privaatserverites.

### [Tellimused](#tellimused)[](#tellimused)

[Tellimused](/docs/en-us/production/monetization/subscriptions)  mängudes võimaldavad teil pakkuda kasutajatele korduvaid eeliseid igakuise tasu eest.

![](https://prod.docsiteassets.roblox.com/assets/monetization/subscriptions/Example-Subscriptions.png) Mängu tellimuste näited

### [Passid](#passid)[](#passid)

[Pass](/docs/en-us/production/monetization/passes)  võimaldab teil nõuda ühekordset Robuxi tasu , et kasutajad saaksid pääseda mängus erilistele privileegidele, nagu juurdepääs piiratud alale, mängu avatariesemele või püsivale võimendusele.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/passes/passes-sample.png)

### [Arendaja tooted](#arendaja-tooted)[](#arendaja-tooted)

[Arendaja toode](/docs/en-us/production/monetization/developer-products)  on ese või võime, mida kasutaja saab osta rohkem kui üks kord, näiteks mängusisene valuuta, laskemoona või potionid. Saate ostude sooritamist, nende salvestamist ja toote teabe saamist läbi skriptimise.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/developer-products/Buy-Product-Example.jpg)

### [Hallatud hinnakujundus](#hallatud-hinnakujundus)[](#hallatud-hinnakujundus)

[Hallatud hinnakujundus](/docs/en-us/production/monetization/managed-pricing)  on ühtne süsteem, mis toob [regionaalse hinnakujunduse](/docs/en-us/production/monetization/regional-pricing)  ja [hinnakujunduse optimeerimise](/docs/en-us/production/monetization/price-optimization)  kokku ühte kohta. Te valite ühekordselt, milliseid esemeid kaasata, ja Hallatud hinnakujundus hoiab teie hinnad aja jooksul optimeeritud üle toodete ja piirkondade.

### [Hinnakujunduse optimeerimine](#hinnakujunduse-optimeerimine)[](#hinnakujunduse-optimeerimine)

[Hinnakujunduse optimeerimine](/docs/en-us/production/monetization/price-optimization)  võimaldab teil leida parimad hinnapunktid oma passide ja arendaja toodete jaoks, mis aitab teil aja jooksul rohkem raha teenida, hoides samal ajal oma hinnad konkurentsivõimelisena.

### [Tasuline juurdepääs Robuxis](#tasuline-juurdepääs-robuxis)[](#tasuline-juurdepääs-robuxis)

[Tasuline juurdepääs Robuxis](/docs/en-us/production/monetization/paid-access-robux)  võimaldab teil nõuda kasutajatelt ühekordset Robuxi tasu  oma mängu juurde pääsemiseks. Mõned arendajad kasutavad seda funktsiooni ajutiselt, et luua suletud beetaversioon, kus nende kõige aktiivsemad kasutajad saavad mängule varakult juurde pääseda ja aidata testimise ja tagasiside osas.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/paid-access/Buy-Access-Example.png)

### [Tasuline juurdepääs kohalikus valuutas](#tasuline-juurdepääs-kohalikus-valuutas)[](#tasuline-juurdepääs-kohalikus-valuutas)

[Tasuline juurdepääs kohalikus valuutas](/docs/en-us/production/monetization/paid-access-local-currency)  võimaldab teil nõuda kasutajatelt ühekordset tasu nende kohalikus valuutas  oma mängu juurde pääsemiseks. Kui nende kohalik valuuta ei ole saadaval, siis neilt nõutakse tasu USD-s. Mõned arendajad kasutavad seda funktsiooni ajutiselt, et luua suletud beetaversioon, kus nende kõige aktiivsemad kasutajad saavad mängule varakult juurde pääseda ja aidata testimise ja tagasiside osas.

### [Privaatserverid](#privaatserverid)[](#privaatserverid)

[Privaatserver](/docs/en-us/production/monetization/private-servers)  on tellimuspõhine funktsioon, mis võimaldab kasutajal otsustada, kes saab mänguga liituda. Kuigi privaatserverid võivad olla tasuta, saate kasutada privaatservereid ka monetiseerimise meetodina, nõudes kasutajatelt, kes soovivad privaatserveritesse pääseda, kuulist Robuxi tasu .

### [Katalooge tasud ja komisjonitasud](#katalooge-tasud-ja-komisjonitasud)[](#katalooge-tasud-ja-komisjonitasud)

Saate luua ja müüa aksessuaare ja riideid Turul. Pärast üleslaadimistasu tasumist ja uue vara heakskiitmiseks esitamist vaatab modereerimismeeskond teie vara üle ja, kui see on heaks kiidetud, lisab teie vara katalooge.

Saate [komisjoni](/docs/en-us/marketplace/marketplace-fees-and-commissions)  iga kord, kui kasutajad ostavad teie katalooge. Kui kasutajad ostavad teie katalooge mängus, kasutades [avatarite kontrollimise menüüd](/docs/en-us/players/avatar-inspect-menu)  või [avatarite redigeerimise teenust](/docs/en-us/players/avatar-editor) , saab mängu omanik samuti komisjoni.

### [Pluginid ja mudelid](#pluginid-ja-mudelid)[](#pluginid-ja-mudelid)

[Plugin](/docs/en-us/studio/plugins)  on laiendus, mis lisab Studio'le täiendavat funktsionaalsust, ja [mudel](/docs/en-us/parts/models)  on taaskasutatav vara tüüp. Saate pakkuda mõlemat teistele loojatele [Looja Poest](/docs/en-us/production/creator-store)  tasuta või müüa neid Ameerika Ühendriikide dollarites  (minimaalne hind on $4.99 pluginite ja $2.99 mudelite puhul). Roblox pakub nende müükide jaoks turuliidri tulude jagamist, kuna ainult maksud ja maksetöötlustasud arvatakse maha. Lisainformatsiooni pluginite ja mudelite müümise kohta vaata [Looja Pood - jaotage ja müüge varasid](/docs/en-us/production/creator-store#distribute-and-sell-assets) .

Iga ostu puhul on 30-päevane tagatisraha. Roblox hoiab teie müügiosakonna 30 päeva, alates müügikuupäevast.

## [Suunised](#suunised)[](#suunised)

Kuna kujundate ja rakendate monetiseerimisprodukte oma mängudesse, kaaluge järgmisi suuniseid, et tagada, et teie monetiseerimismeetodid sobivad kõigile platvormi kasutajatele.

### [Toodete esitamine](#toodete-esitamine)[](#toodete-esitamine)

Ohutuse ja õiguse säilitamiseks peate esitama monetiseerimisprodukte viisil, mis on läbipaistev, aus ja kasutajasõbralik. Näiteks, kui pakute allahindlusi, peavad need olema tõelised  ja ausad :

-

Allahindlus ei ole tõeline, kui ese on alati "müügis" sama palju Robuxi eest.

-

Allahindlus ei ole aus, kui seda pakutakse ainult väga lühikese aja jooksul, sundides kasutajaid ostma nii kiiresti kui võimalik.

Kasutajaid ei tohi kunagi eksitada, segadusse ajada või sundida ostma viisil, mida nad ei kavatsenud, ja neil peaks alati olema vabadus teha selge, teadlik valik tellimuse saamiseks või Robuxi kulutamiseks konkreetsele esemele. Üldise juhisena on mõned praktikad, mida tuleks alati vältida, kui esitate monetiseerimisprodukte oma publikule:

-

Ärge väitke, et tellimus või ese on peaaegu otsas või saadaval ainult lühikese aja jooksul, kui see ei ole tõsi.

-

Ärge kasutage taimerit, mis ei ole täpne või mis automaatselt taaskäivitub sama eseme jaoks.

Näiteks, kui teie mäng sisaldab "päeva pakkumist", mis ütleb, et see on saadaval ainult 24 tundi, kuid seejärel näitate sama sõnumit kasutajatele iga kord, kui nad sisse logivad, ja see ei lakka kunagi olemast saadaval, olete loonud vale kiireloomulisuse tunde, mis ei ole kasutajasõbralik.

### [Reklaamimine globaalsetele publikutele](#reklaamimine-globaalsetele-publikutele)[](#reklaamimine-globaalsetele-publikutele)

Roblox on globaalne kogukond, mis on mõeldud kasutajatele igas vanuses, seega peaksid teie mängudes olevad reklaamid olema vaikimisi sobivad kõigile publikutele. Kui teatud monetiseerimisprodukte on teatud kohtades piiratud, näiteks tasulised juhuslikud esemed, pakub Roblox [PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  API-d, et aidata teil tagada, et need tooted on nähtavad ainult sobivatele kasutajatele.

[PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  tagastab, kas kasutaja on teatud esemete või funktsioonide jaoks sobiv vastavalt nende asukohale, vanusele ja platvormile. Peate selle API oma mängu integreerima, et täita oma vastavusnõudeid, sealhulgas määrata, kas iga kasutaja on:

-

Sobiv tellimuste või kaubandustoodete ostmiseks.

-

Lubatud tasulised juhuslikud esemed, tasulised esemete kaubandused või näha immersiivseid reklaame.

Kui kasutaja saab kasutada Robuxi või midagi muud, mis on saadud Robuxi abil, et saada juhuslikku auhinda, peate kasutama [PolicyService](/docs/en-us/reference/engine/classes/PolicyService) , et blokeerida see funktsioon kasutajatele, kellel ei ole lubatud kasutada juhuslikke esemeid Robuxi vastu.

Üldise juhisena vältige survestavaid või kiireloomulisi sõnumeid, kui suhtlete alaealistega, kuna kõrge survekeel võib olla ülekaalukas:

| ** Keel, mida vältida** | | ** Soovitatavad alternatiivid** |
| --- | --- |
| "SAADA SEE NÜÜD" | | "Vaata eset" |
| "VIIMANE VÕIMALUS, TEGELE NÜÜD" | | "Vaata hinda" |
| "OSTA ENNE KUI SEE KADUNUD ON!" | | "Ava pood" |

## [Täiendavad lokaliseerimised selle lehe jaoks](#täiendavad-lokaliseerimised-selle-lehe-jaoks)[](#täiendavad-lokaliseerimised-selle-lehe-jaoks)

Lisaks lokaliseeritud versioonidele sellest lehe, mis ei ole saadaval saidi keelevalijas, vaata järgmisi linke:

-

[Bulgaaria (български)](https://create.roblox.com/docs/bg-bg/production/monetization)

-

[Horvaatia (hrvatski)](https://create.roblox.com/docs/hr-hr/production/monetization)

-

[Tšehhi (čeština)](https://create.roblox.com/docs/cs-cz/production/monetization)

-

[Taani (dansk)](https://create.roblox.com/docs/da-dk/production/monetization)

-

[Hollandi (Nederlands)](https://create.roblox.com/docs/nl-nl/production/monetization)

-

[Eesti (eesti)](https://create.roblox.com/docs/et-ee/production/monetization)

-

[Soome (suomi)](https://create.roblox.com/docs/fi-fi/production/monetization)

-

[Kreeka (Ελληνικά)](https://create.roblox.com/docs/el-gr/production/monetization)

-

[Ungari (magyar)](https://create.roblox.com/docs/hu-hu/production/monetization)

-

[Iiri (Gaeilge)](https://create.roblox.com/docs/ga-ie/production/monetization)

-

[Läti (latviešu)](https://create.roblox.com/docs/lv-lv/production/monetization)

-

[Leedu (lietuvių)](https://create.roblox.com/docs/lt-lt/production/monetization)

-

[Malta (Malti)](https://create.roblox.com/docs/mt-mt/production/monetization)

-

[Portugali - Portugal (português)](https://create.roblox.com/docs/pt-pt/production/monetization)

-

[Rumeenia (română)](https://create.roblox.com/docs/ro-ro/production/monetization)

-

[Slovaki (slovenčina)](https://create.roblox.com/docs/sk-sk/production/monetization)

-

[Sloveenia (slovenščina)](https://create.roblox.com/docs/sl-si/production/monetization)

-

[Rootsi (svenska)](https://create.roblox.com/docs/sv-se/production/monetization)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
