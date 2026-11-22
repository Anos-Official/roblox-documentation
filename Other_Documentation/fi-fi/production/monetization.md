<!-- Source: https://create.roblox.com/docs/fi-fi/production/monetization -->

Rahastus | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)

# Rahastus

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Rahastus on osa Robloxin kokonaisrakenteesta, joka tarjoaa arvoa luojille. On useita erilaisia lähestymistapoja rahastaa sisältöäsi, mukaan lukien [tilaukset](#tilaukset) , pääsymaksun periminen [Robuxissa](#maksettu-p%C3%A4%C3%A4sy-robuxissa)  tai [paikallisessa valuutassa](#maksettu-p%C3%A4%C3%A4sy-paikallisessa-valuutassa) , [esineiden tai kykyjen tarjoaminen, joita käyttäjät voivat ostaa](#kehitt%C3%A4j%C3%A4tuotteet) , [yksityisten palvelimien](#yksityiset-palvelimet)  tarjoaminen, jotta käyttäjät voivat pelata vain ystävien kanssa, ja [mallien ja liitännäisten myyminen](/docs/en-us/production/creator-store#distribute-and-sell-assets)  muille luojille Luojakaupassa.

Jos päätät tarjota ostettavaa sisältöä, Roblox ei automaattisesti tallenna tuotteen tai ostotietoja. Tietojen menettämisen estämiseksi sinun on huolellisesti tallennettava nämä tiedot käyttämällä [DataStoreService](/docs/en-us/reference/engine/classes/DataStoreService) -palvelua tai muuta Robloxin ulkopuolella isännöityä tietovarastopalvelua.

Jos haluat syvällisemmän katsauksen optimaalisten rahastusstrategioiden suunnitteluun kokemuksellesi, katso [Rahastuksen perusteet](/docs/en-us/production/game-design/monetization-foundations) .

## [Rahastusstrategiat](#rahastusstrategiat)[](#rahastusstrategiat)

Ole tietoinen rahastusmenetelmistä, joita otat käyttöön pelissäsi, sillä käyttäjämme todennäköisesti äänestävät alas  peliäsi, jos he eivät hyväksy strategioitasi. Lisäksi kaikkien kehittäjien on oltava läpinäkyviä kaikista [satunnaiseen rahastukseen perustuvista](/docs/en-us/production/monetization/paid-random-items)  menetelmistä ja käytettävä näitä mekanismeja vastuullisesti.

Jotkut suositut rahastusstrategiat ilmaiseksi pelattaville peleille muilla alustoilla eivät ole suositeltavia Robloxissa. Esimerkiksi ajanvarausmekanismit ja ajastimet, joita voidaan poistaa tai siirtää eteenpäin, voivat toimia hyvin muilla alustoilla, mutta nämä mekanismit eivät ole suosittuja Roblox-käyttäjien keskuudessa, jotka pitävät hauskuuden päättymistä liian aikaisin ongelmallisena.

Seuraavat parhaat käytännöt ovat suosittuja huippukehittäjien keskuudessa, kun räätälöidään rahastusstrategioita Roblox-alustalle ja -yleisölle.

Huomaa, että näiden tekniikoiden ja huomioiden soveltaminen ei takaa, että pystyt tehokkaasti rahastamaan peliäsi. Muista, että sinun ei tarvitse asettaa taloudellisia tavoitteita nauttiaksesi Roblox-pelin luomisesta.

### [Turistit ja paikalliset](#turistit-ja-paikalliset)[](#turistit-ja-paikalliset)

On hyödyllistä ajatella Roblox-käyttäjiä kahdessa kategoriassa:

-

Turistit  hyppivät tyypillisesti yhdestä pelistä toiseen, asettaen monimuotoisuuden syvyyden edelle. He suosivat esineitä, joilla on välittömiä vaikutuksia, joko tekemällä pelistä hauskempaa tai erottamalla heidät muista käyttäjistä, mikä kutsuu muita käyttäjiä kysymään, miten ja mistä he saivat esineen.

-

Paikalliset  keskittyvät todennäköisemmin tiettyyn peliin tai pienempään pelivalikoimaan. He sitoutuvat syvällisemmin ja muodostavat tyypillisesti lähes koko pelin sitoutuneen käyttäjäkannan. He ovat kiinnostuneempia esineistä, joilla on pitkäaikaisia etuja, kuten [taistelupassi](/docs/en-us/production/game-design/season-pass-design) .

Jos haluat oppia lisää siitä, miten suunnitella peliäsi Roblox-käyttäjät mielessäsi, katso [Suunnittelu Robloxille](/docs/en-us/production/game-design/design-for-roblox) .

### [Sosiaaliset ominaisuudet](#sosiaaliset-ominaisuudet)[](#sosiaaliset-ominaisuudet)

Roblox-käyttäjät nauttivat peleistä, jotka korostavat sosiaalista vuorovaikutusta. Esimerkiksi esineiden tai tapahtumien, jotka ovat saatavilla vain rajoitetun ajan , omistaminen voi luoda jännitystä kyseisen sisällön ympärille. Kauppajärjestelmä  kannustaa käyttäjiä vuorovaikuttamaan. Vaikka molemmat järjestelmät voivat olla menestyksekkäitä itsenäisesti, ne ovat erityisen tehokkaita yhdessä.

### [Live-ops](#live-ops)[](#live-ops)

Julkaisun jälkeinen tuki on monella tapaa helpompaa Robloxissa kuin muilla alustoilla, sillä voit nopeasti julkaista päivityksiä parantaaksesi peliäsi.

Usein  tapahtuvat sisällön päivitykset voivat olla hyödyllisiä, jos haluat ylläpitää sitoutumista peliisi ajan myötä. Roblox-käyttäjät ovat tottuneet säännöllisiin päivityksiin, ja käyttäjän kiinnostuksen palauttaminen voi olla paljon vaikeampaa kuin aktiivisten käyttäjien ylläpitäminen. Viikoittainen rytmi  päivityksille on ihanteellinen. Vähintäänkin pyri kuukausittaisiin päivityksiin. Keskustellaksesi sisällön rytmistä, katso Level Up [sisällön rytmi -työpaja](/docs/en-us/production/game-design/content-updates) .

Päivityksiä suunnitellessasi pidä ne keskittyneinä tiettyyn teemaan . Tämä helpottaa käyttäjien ymmärtää uutta päivitystä ja kertoa, mikä sisältö on uutta, kun he liittyvät mukaan. Se auttaa myös sinua koordinoimaan sisältöäsi ja markkinointivaroja. Esimerkiksi, jos lisäät uuden eläintarhan roolipelissäsi, varmista, että kaikki uusi sisältö liittyy eläintarhan teemaan.

Älä pelkää saada käyttäjiä ansaitsemaan pääsyä  uuteen sisältöön. Uudet käyttäjät tulevat pelaamaan uusia päivityksiä, mutta jos he eivät tunne, että he ovat saavuttaneet  jotain pelissä, he saattavat poistua pian sen jälkeen. Voit luoda ansaitsemisen tunteen joko rahastamalla päivityssisältöä tai luomalla ennakkoedellytyksiä uuden sisällön pelaamiselle.

Jos haluat oppia lisää siitä, miten suunnitella tehokasta julkaisun jälkeistä tukea pelillesi, katso [Live-opsin perusteet](/docs/en-us/production/game-design/liveops-essentials) .

## [Tuotteet](#tuotteet)[](#tuotteet)

### [Immersiiviset mainokset](#immersiiviset-mainokset)[](#immersiiviset-mainokset)

[immersiiviset mainokset](/docs/en-us/production/monetization/immersive-ads)  -järjestelmä mahdollistaa mainosyksiköiden lisäämisen peliisi, mikä sallii Robloxin ohjelmallisesti toimittaa mainossisältöä mainostajilta aktiivisille käyttäjillesi.

![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/Overview-ImageAd.jpg) Kuvamainosmuoto

Portaalimainosmuoto

### [Roblox Plus](#roblox-plus)[](#roblox-plus)

[Roblox Plus](/docs/en-us/production/monetization/roblox-plus)  antaa sinun ansaita lisää pelin sisäisistä ostoista, joita ohjaavat Robloxin tukemat käyttäjäalennukset, rekisteröitymisbonukset jokaisesta uudesta tilaajasta, jonka tuot, ja sitoutuminen maksetuissa yksityisissä palvelimissa.

### [Tilaukset](#tilaukset)[](#tilaukset)

[Tilaukset](/docs/en-us/production/monetization/subscriptions)  pelien sisällä antavat sinun tarjota käyttäjille toistuvia etuja kuukausimaksua vastaan.

![](https://prod.docsiteassets.roblox.com/assets/monetization/subscriptions/Example-Subscriptions.png) Esimerkkejä pelitilauksista

### [Passit](#passit)[](#passit)

[Passi](/docs/en-us/production/monetization/passes)  antaa sinun periä kertaluonteisen Robux-maksun  käyttäjiltä, jotta he voivat käyttää erityisiä etuoikeuksia pelissä, kuten pääsyä rajoitettuun alueeseen, pelihahmon esineeseen tai pysyvään tehosteeseen.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/passes/passes-sample.png)

### [Kehittäjätuotteet](#kehittäjätuotteet)[](#kehittäjätuotteet)

[Kehittäjätuote](/docs/en-us/production/monetization/developer-products)  on esine tai kyky, jonka käyttäjä voi ostaa useammin kuin kerran, kuten pelin sisäinen valuutta, ammuksia tai taikoja. Voit kehottaa ostoja, tallentaa niitä ja saada tuotetietoja skriptauksen kautta.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/developer-products/Buy-Product-Example.jpg)

### [Hallittu hinnoittelu](#hallittu-hinnoittelu)[](#hallittu-hinnoittelu)

[Hallittu hinnoittelu](/docs/en-us/production/monetization/managed-pricing)  on yhtenäinen järjestelmä, joka yhdistää [aluehinnoittelun](/docs/en-us/production/monetization/regional-pricing)  ja [hintojen optimoinnin](/docs/en-us/production/monetization/price-optimization)  yhteen paikkaan. Liity kerran, valitse, mitkä tuotteet sisällytetään, ja hallittu hinnoittelu pitää hintasi optimoituna tuotteiden ja alueiden välillä ajan myötä.

### [Hintojen optimointi](#hintojen-optimointi)[](#hintojen-optimointi)

[Hintojen optimointi](/docs/en-us/production/monetization/price-optimization)  antaa sinun löytää parhaat hintapisteet passeillesi ja kehittäjätuotteillesi, mikä voi auttaa sinua ansaitsemaan enemmän rahaa ajan myötä pitäen samalla hintasi kilpailukykyisinä.

### [Maksettu pääsy Robuxissa](#maksettu-pääsy-robuxissa)[](#maksettu-pääsy-robuxissa)

[Maksettu pääsy Robuxissa](/docs/en-us/production/monetization/paid-access-robux)  antaa sinun periä käyttäjiltä kertaluonteisen Robux-maksun  päästäksesi peliisi. Jotkut kehittäjät käyttävät tätä ominaisuutta tilapäisesti luodakseen suljetun beetatestin, jossa heidän sitoutuneimmat käyttäjänsä voivat saada varhaisen pääsyn peliin ja auttaa testauksessa ja palautteessa.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/paid-access/Buy-Access-Example.png)

### [Maksettu pääsy paikallisessa valuutassa](#maksettu-pääsy-paikallisessa-valuutassa)[](#maksettu-pääsy-paikallisessa-valuutassa)

[Maksettu pääsy paikallisessa valuutassa](/docs/en-us/production/monetization/paid-access-local-currency)  antaa sinun periä käyttäjiltä kertaluonteisen maksun heidän paikallisessa valuutassaan  päästäksesi peliisi. Jos heidän paikallista valuuttaansa ei ole saatavilla, heidät veloitetaan USD:ssä. Jotkut kehittäjät käyttävät tätä ominaisuutta tilapäisesti luodakseen suljetun beetatestin, jossa heidän sitoutuneimmat käyttäjänsä voivat saada varhaisen pääsyn peliin ja auttaa testauksessa ja palautteessa.

### [Yksityiset palvelimet](#yksityiset-palvelimet)[](#yksityiset-palvelimet)

[Yksityinen palvelin](/docs/en-us/production/monetization/private-servers)  on tilauspohjainen ominaisuus, joka antaa käyttäjän päättää, kuka voi pelata peliä heidän kanssaan. Vaikka yksityiset palvelimet voivat olla ilmaisia, voit myös käyttää yksityisiä palvelimia rahastamisen menetelmänä perimällä käyttäjiltä, jotka haluavat käyttää yksityisiä palvelimia, kuukausittaisen Robux-maksun .

### [Katalogimaksut ja komissiot](#katalogimaksut-ja-komissiot)[](#katalogimaksut-ja-komissiot)

Voit luoda ja myydä asusteita ja vaatteita Markkinapaikalla. Kun olet maksanut latausmaksun ja lähettänyt uuden omaisuuden hyväksyttäväksi, moderointitiimi tarkistaa omaisuutesi ja, jos se hyväksytään, lisää omaisuutesi katalogiin.

Saat [komission](/docs/en-us/marketplace/marketplace-fees-and-commissions)  joka kerta, kun käyttäjät ostavat katalogiesi esineen. Jos käyttäjät ostavat katalogiesi esineen pelissä käyttäen [hahmon tarkistusvalikkoa](/docs/en-us/players/avatar-inspect-menu)  tai [hahmon muokkauspalvelua](/docs/en-us/players/avatar-editor) , pelin omistaja saa myös komission.

### [Liitännäiset ja mallit](#liitännäiset-ja-mallit)[](#liitännäiset-ja-mallit)

[Liitännäinen](/docs/en-us/studio/plugins)  on laajennus, joka lisää lisätoimintoja Studiolle, ja [malli](/docs/en-us/parts/models)  on uudelleenkäytettävä omaisuustyyppi. Voit tarjota molempia muille luojille [Luojakaupassa](/docs/en-us/production/creator-store)  ilmaiseksi tai voit myydä niitä Yhdysvaltain dollareissa  (minimihinta on 4,99 dollaria liitännäisille ja 2,99 dollaria malleille). Roblox tarjoaa markkinoiden johtavan tulonjakojärjestelmän näistä myynneistä, sillä vain verot ja maksunkäsittelymaksut vähennetään. Lisätietoja liitännäisten ja mallien myynnistä, katso [Luojakauppa - Jaa ja myy omaisuutta](/docs/en-us/production/creator-store#distribute-and-sell-assets) .

Jokaiselle ostolle on 30 päivän pidätys. Roblox pidättää osasi myynnistä 30 päivän ajan myyntipäivämäärästä alkaen.

## [Ohjeet](#ohjeet)[](#ohjeet)

Kun suunnittelet ja toteutat rahastus tuotteita peleihisi, harkitse seuraavia ohjeita varmistaaksesi, että rahastusmenetelmäsi ovat sopivia kaikille alustan käyttäjille.

### [Tuotteiden esittely](#tuotteiden-esittely)[](#tuotteiden-esittely)

Turvallisuuden ja oikeudenmukaisuuden ylläpitämiseksi sinun on esitettävä rahastus tuotteet tavalla, joka on läpinäkyvä, rehellinen ja käyttäjäystävällinen. Esimerkiksi, jos tarjoat alennuksia, niiden on oltava aitoja  ja oikeudenmukaisia :

-

Alennus ei ole aito, jos esine on aina "alennuksessa" samalle määrälle Robuxia.

-

Alennus ei ole oikeudenmukainen, jos sitä tarjotaan vain hyvin lyhyen ajan, painostaen käyttäjiä tekemään osto mahdollisimman nopeasti.

Käyttäjiä ei koskaan saa johtaa harhaan, hämmentää tai painostaa ostoihin tavoilla, joita he eivät tarkoittaneet, ja heidän tulisi aina olla vapaita tekemään selkeä, harkittu valinta tilauksen saamiseksi tai Robuxin käyttämiseksi tiettyyn esineeseen. Yleisenä ohjeena on joitakin käytäntöjä, joita on vältettävä aina, kun esittelet rahastus tuotteita yleisöllesi:

-

Älä väitä, että tilaus tai esine on lähes loppu tai saatavilla vain lyhyen ajan, jos se ei pidä paikkaansa.

-

Älä käytä laskentakelloa, joka ei ole tarkka tai joka käynnistyy automaattisesti uudelleen saman esineen kohdalla.

Esimerkiksi, jos pelisi sisältää "päivän tarjous", joka sanoo, että se on saatavilla vain 24 tuntia, mutta sitten näytät saman viestin käyttäjille joka kerta, kun he kirjautuvat sisään, eikä se koskaan lakkaa olemasta saatavilla, olet luonut väärän kiireen tunteen, joka ei ole käyttäjäystävällinen.

### [Mainostaminen globaaleille yleisöille](#mainostaminen-globaaleille-yleisöille)[](#mainostaminen-globaaleille-yleisöille)

Roblox on globaali yhteisö kaikille ikäryhmille, joten mainosten tulisi olla oletusarvoisesti sopivia kaikille yleisöille. Jos tietyt rahastus tuotteet ovat rajoitettuja tietyillä alueilla, kuten maksetut satunnaiset esineet, Roblox tarjoaa [PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  API:n auttaakseen sinua varmistamaan, että nämä tuotteet ovat näkyvissä vain kelvollisille käyttäjille.

[PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  palauttaa, onko käyttäjä kelvollinen tiettyihin esineisiin tai ominaisuuksiin sijaintinsa, ikänsä ja alustansa mukaan. Sinun on integroitava tämä API peliisi täyttääksesi vaatimustenmukaisuusvelvoitteesi, mukaan lukien sen määrittäminen, onko jokainen käyttäjä:

-

Kelvollinen ostamaan tilauksia tai kaupallisia tuotteita.

-

Sallittu maksetut satunnaiset esineet, maksetut esinekaupat tai nähdä immersiiviset mainokset.

Jos käyttäjä voi käyttää Robuxia tai jotain muuta, joka on hankittu Robuxilla saadakseen satunnaisen palkinnon, sinun on käytettävä [PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  estääksesi tämän ominaisuuden käyttäjiltä, jotka eivät saa käyttää satunnaisia esineitä Robuxin vaihdossa.

Yleisenä ohjeena vältä painostavia tai kiireellisiä viestejä vuorovaikutuksessa alaikäisten kanssa, sillä korkean painostuksen kieli voi olla ylivoimaista:

| ** Vältettävä kieli** | | ** Suositellut vaihtoehdot** |
| --- | --- |
| "HAE SE NYT" | | "Näytä esine" |
| "VIIMEINEN MAHDOLLISUUS, TOIMI NYT" | | "Katso hinta" |
| "OSTA ENNEN KUIN SE ON MENNYT!" | | "Avaa kauppa" |

## [Lisälocalisoinnit tälle sivulle](#lisälocalisoinnit-tälle-sivulle)[](#lisälocalisoinnit-tälle-sivulle)

Lisäversioita tästä sivusta, jotka eivät ole saatavilla sivuston kielivalitsimessa, katso seuraavat linkit:

-

[Bulgaria (български)](https://create.roblox.com/docs/bg-bg/production/monetization)

-

[Kroatia (hrvatski)](https://create.roblox.com/docs/hr-hr/production/monetization)

-

[Tšekki (čeština)](https://create.roblox.com/docs/cs-cz/production/monetization)

-

[Tanska (dansk)](https://create.roblox.com/docs/da-dk/production/monetization)

-

[Hollanti (Nederlands)](https://create.roblox.com/docs/nl-nl/production/monetization)

-

[Viro (eesti)](https://create.roblox.com/docs/et-ee/production/monetization)

-

[Suomi (suomi)](https://create.roblox.com/docs/fi-fi/production/monetization)

-

[Kreikka (Ελληνικά)](https://create.roblox.com/docs/el-gr/production/monetization)

-

[Unkari (magyar)](https://create.roblox.com/docs/hu-hu/production/monetization)

-

[Irlanti (Gaeilge)](https://create.roblox.com/docs/ga-ie/production/monetization)

-

[Latvia (latviešu)](https://create.roblox.com/docs/lv-lv/production/monetization)

-

[Liettua (lietuvių)](https://create.roblox.com/docs/lt-lt/production/monetization)

-

[Malta (Malti)](https://create.roblox.com/docs/mt-mt/production/monetization)

-

[Portugali - Portugali (português)](https://create.roblox.com/docs/pt-pt/production/monetization)

-

[Romania (română)](https://create.roblox.com/docs/ro-ro/production/monetization)

-

[Slovakia (slovenčina)](https://create.roblox.com/docs/sk-sk/production/monetization)

-

[Slovenia (slovenščina)](https://create.roblox.com/docs/sl-si/production/monetization)

-

[Ruotsi (svenska)](https://create.roblox.com/docs/sv-se/production/monetization)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
