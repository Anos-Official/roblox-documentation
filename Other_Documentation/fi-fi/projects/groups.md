<!-- Source: https://create.roblox.com/docs/fi-fi/projects/groups -->

Ryhmät (tiimit) | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Projects](/docs/en-us/projects)
6. /
7. [Work in teams](/docs/en-us/projects/groups)

# Ryhmät (tiimit)

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Roblox ryhmä  mahdollistaa useiden luojien työskentelyn samassa pelissä, samojen resurssien käytön, voittojen jakamisen ja kaikkien osallistujien tunnustamisen.

Pelin ryhmän omistaminen auttaa luojia tekemään yhteistyötä ja toimimaan itsenäisinä studioina. Jos ryhmässä syntyy erimielisyyksiä, Roblox ei voi auttaa sovituksessa tai erimielisyyksien ratkaisemisessa.

## [Ryhmän luominen](#ryhmän-luominen)[](#ryhmän-luominen)

Ryhmän luominen maksaa 100 Robuxia. Voit hallita sen [rooleja ja oikeuksia](#roolit-ja-oikeudet)  [Luojaohjauspaneelista](https://create.roblox.com/dashboard/creations)  tai [Yhteisöistä](https://www.roblox.com/communities) .

Ennen ryhmän luomista, lue huolellisesti [säännöt ja odotukset](/docs/en-us/projects/group-guidelines)  ryhmän hallinnasta.

Luo uusi ryhmä:

1.

Siirry [Luojaohjauspaneeliin](https://create.roblox.com/dashboard/creations) , laajenna tilinvaihtajaa vasemmassa yläkulmassa ja napsauta plus (+)  -painiketta.

2.

Luo ryhmä  -sivulla, lataa kuva ryhmän logoksi ja syötä ryhmän nimi.

3.

Kun olet valmis, napsauta Osta  -painiketta. Kun ryhmä on luotu, sinut ohjataan ryhmän profiilisivulle, jossa voit muokata ryhmän tietoja, mukaan lukien lisätä jopa kolme sosiaalista linkkiä.

## [Roolit ja oikeudet](#roolit-ja-oikeudet)[](#roolit-ja-oikeudet)

Ryhmäjäsenille voidaan määrittää yksi tai useampi rooli  ryhmässä, ja jokaisella roolilla on oikeudet , jotka määrittävät sen jäsenten kyvyt.

Roolin määrittäminen on vain saatavilla, jos olet ryhmän omistaja tai sinulla on lupa luoda, määrittää ja jakaa ryhmän rooleja.

Hallinnoi ryhmän roolijakoja ohjelmallisesti pelipalvelimelta käyttämällä [HttpService](/docs/en-us/reference/engine/classes/HttpService)  -luokkaa kutsuaksesi tuettuja Open Cloud Groups -päätepisteitä. Asennusta ja esimerkkikoodia varten katso [Käytä Open Cloudin kanssa](/docs/en-us/cloud-services/http-service#use-with-open-cloud) .

1.

[Luojaohjauspaneelista](https://create.roblox.com/dashboard/creations) , laajenna tilinvaihtajaa vasemmassa yläkulmassa ja valitse ryhmä.

2.

Laajenna tilinvaihtajaa uudelleen ja valitse Roolit .

3.

Varmista jokaisen roolin osalta huolellisesti oikeudet Permissions  -välilehdellä.

Oikeudet on järjestetty General , Creation  ja Community  -kategorioihin. Alla olevat osiot kuvaavat kunkin kategorian käytettävissä olevia oikeuksia.

### [Yleiset](#yleiset)[](#yleiset)

Yleiset oikeudet

| Manage roles | | Jäsenet, joilla on tämä oikeus, voivat luoda, muokata, poistaa, järjestää uudelleen ja jakaa tai poistaa rooleja, jotka ovat heidän korkeimman roolinsa alapuolella. He voivat muokata vain oikeuksia, jotka he jo pitävät. |
| --- | --- |
| Assign or remove roles from members | | Jäsenet, joilla on tämä oikeus, voivat jakaa tai poistaa rooleja, jotka ovat heidän korkeimman roolinsa alapuolella, mille tahansa jäsenelle. |
| Invite or approve members | | Jäsenet, joilla on tämä oikeus, voivat kutsua ihmisiä ryhmään ja hyväksyä liittymispyynnöt. |
| Kick members | | Jäsenet, joilla on tämä oikeus, voivat poistaa jäseniä, joiden korkein rooli on heidän omaansa alhaisempi. |
| Ban members | | Jäsenet, joilla on tämä oikeus, voivat kieltää jäseniä, joiden korkein rooli on heidän omaansa alhaisempi. |
| Configure group profile | | Jäsenet, joilla on tämä oikeus, voivat määrittää ryhmän profiilin. |
| View audit logs | | Jäsenet, joilla on tämä oikeus, voivat tarkastella [ryhmän tarkastuspöytäkirjoja](#ryhm%C3%A4n-tarkastusp%C3%B6yt%C3%A4kirjat) . |
| Manage allies and enemies | | Jäsenet, joilla on tämä oikeus, voivat hallita ryhmän liittolaisia ja vihollisia. |

### [Luominen](#luominen)[](#luominen)

Creations

| Playtest experiences | | Jäsenet, joilla on tämä rooli, voivat pelata kaikkia ryhmän omistamia pelejä, vaikka niitä ei olisi julkaistu laajemmalle yleisölle. Saatavilla myös [pelikohtaisena oikeutena](/docs/en-us/projects/configure-games) . |
| Edit experiences | | Jäsenet, joilla on tämä rooli, voivat muokata kaikkia ryhmän omistamia pelejä ja [resursseja](/docs/en-us/projects/assets)  ja käyttää kaikkia [Data Stores Manager](/docs/en-us/cloud-services/data-stores/data-stores-manager)  -toimintoja. Ei sisällä pelin muokkaamista [yhteistyö](/docs/en-us/projects/collaboration)  -istunnon ulkopuolella tai paikan tallentamista yhdestä pelistä toiseen. Saatavilla myös [pelikohtaisena oikeutena](/docs/en-us/projects/configure-games) . |
| Publish experiences | | Jäsenet, joilla on tämä rooli, voivat sekä muokata pelejä, kuten edellä, että julkaista pelejä Robloxiin. Saatavilla myös [pelikohtaisena oikeutena](/docs/en-us/projects/configure-games) . |
| Manage share links | | Jäsenet, joilla on tämä rooli, voivat luoda/määrittää [jakolinkkejä](/docs/en-us/production/promotion/share-links) . |
| Manage experience events | | Jäsenet, joilla on tämä rooli, voivat luoda/määrittää [kokemustapahtumia](/docs/en-us/production/promotion/experience-events) . |
| Moderate experiences | | Jäsenet, joilla on tämä rooli, voivat nähdä kaikki pelin sisäiset chat-viestit (vain luku; jäsenen on oltava 18+) ja kieltää tai hallita kiellettyjä käyttäjiä kaikissa ryhmän omistamissa peleissä. |
| Manage monetization for experiences | | Jäsenet, joilla on tämä rooli, voivat hallita ansaintatuotteita, kuten [passeja](/docs/en-us/production/monetization/passes) , [kehittäjätuotteita](/docs/en-us/production/monetization/developer-products) , [tilauksia](/docs/en-us/production/monetization/subscriptions)  ja muita. Saatavilla myös [pelikohtaisena oikeutena](/docs/en-us/projects/configure-games) . |
| Manage secrets for experiences | | Jäsenet, joilla on tämä rooli, voivat nähdä [salaisuuksien](/docs/en-us/cloud-services/secrets)  luettelon ja voivat luoda, päivittää ja poistaa salaisuuksia kaikista ryhmän omistamista peleistä. Tämän roolin omaavilla jäsenillä on oltava Edit experiences  -oikeus nähdä Salaisuudet-sivu. Saatavilla myös [pelikohtaisena oikeutena](/docs/en-us/projects/configure-games) . |

Analytics

| View analytics for experiences | | Jäsenet, joilla on tämä rooli, voivat käyttää kaikkien ryhmän omistamien pelien [analytiikkaa](/docs/en-us/production/analytics) , vaikka heillä ei olisi muokkausoikeuksia. Saatavilla myös [pelikohtaisena oikeutena](/docs/en-us/projects/configure-games) . |
| Manage alerts | | Jäsenet, joilla on tämä rooli, voivat luoda ja hallita analytiikka-alarmeja. Yhdistä tämä oikeus View analytics for experiences  -oikeuden kanssa nähdäksesi hälytyksen merkinnät suoraan mittaristografiikoissa. |

Monetization

| View group revenue | | Jäsenet, joilla on tämä rooli, voivat nähdä ryhmän Robux-saldon, kaikki määritetyt toistuvat jakopalkkiot ja tulonkirjausominaisuudet. |
| Manage and spend group revenue | | Jäsenet, joilla on tämä rooli, voivat nähdä kaikki ryhmän tulot, kuten edellä, ja myös hallita niitä suoraan. Tämä sisältää [toistuvien maksujen](#toistuvat-maksut)  määrittämisen ja [kertamaksujen](#kertamaksut)  lähettämisen yhteistyökumppaneille. |
| Create ad campaigns for the group | | Jäsenet, joilla on tämä rooli, voivat mainostaa ryhmää. |

Avatar items

| Create avatar items | | Jäsenet, joilla on tämä rooli, voivat luoda avatar-esineitä, kuten vaatteita. |
| Configure avatar items | | Jäsenet, joilla on tämä rooli, voivat määrittää myyntitiedot, varastot ja sponsoroinnit olemassa oleville ryhmän avatar-esineille. |

API

| Manage API keys | | Jäsenet, joilla on tämä rooli, voivat hallita [Open Cloud API -avaimia](/docs/en-us/cloud/auth/api-keys)  ryhmälle. |

Development items

| View development items | | Jäsenet, joilla on tämä rooli, voivat nähdä ryhmän omistamat kehitysesineet, esimerkiksi Äänet . |
| Manage development items | | Jäsenet, joilla on tämä rooli, voivat ladata ja määrittää resurssikehitysesineitä, kuten Decalit . |
| Manage development item permissions | | Jäsenet, joilla on tämä rooli, voivat määrittää kehitysesineiden oikeuksia, esimerkiksi äänen jakamista. |

Data Stores

| View Data Stores for experiences | | Jäsenet, joilla on tämä rooli, voivat nähdä tietovarastoja kaikissa ryhmän peleissä [Data Stores Manager](/docs/en-us/cloud-services/data-stores/data-stores-manager)  -sivun kautta, mutta he eivät voi poistaa tietoja. Saatavilla myös [pelikohtaisena oikeutena](/docs/en-us/projects/configure-games) . |
| Edit Data Stores for experiences | | Jäsenet, joilla on tämä rooli, voivat poistaa tietovarastoista tiettyjä avaimia kaikissa ryhmän peleissä [Data Stores Manager](/docs/en-us/cloud-services/data-stores/data-stores-manager)  -sivun kautta. Saatavilla myös [pelikohtaisena oikeutena](/docs/en-us/projects/configure-games) . |
| Delete Data Stores for experiences | | Jäsenet, joilla on tämä rooli, voivat poistaa kokonaisia tietovarastoja kaikista ryhmän peleistä [Data Stores Manager](/docs/en-us/cloud-services/data-stores/data-stores-manager)  -sivun kautta. Saatavilla myös [pelikohtaisena oikeutena](/docs/en-us/projects/configure-games) . |

Notifications

| Manage webhooks for experiences | | Jäsenet, joilla on tämä rooli, voivat luetella, luoda, päivittää ja poistaa webhookkeja kaikista ryhmän kokemuksista. |

Communication

| Manage support tickets for experiences | | Jäsenet, joilla on tämä rooli, voivat hallita tukilippuja kaikista ryhmän kokemuksista. |

Legacy

| Hallitse pääsyä tämän ryhmän resursseihin | | Jäsenet, joilla on tämä rooli, voivat luoda ja muokata pääsyä ryhmän resursseihin. |

### [Yhteisö](#yhteisö)[](#yhteisö)

Posts

| View community announcements | | Jäsenet, joilla on tämä rooli, voivat nähdä yhteisöilmoituksia. |
| Create community announcements | | Jäsenet, joilla on tämä rooli, voivat luoda yhteisöilmoituksia. |

Forums

| Manage categories | | Jäsenet, joilla on tämä rooli, voivat hallita foorumikategorioita. |
| Create posts | | Jäsenet, joilla on tämä rooli, voivat luoda foorumiviestejä. |
| Remove posts | | Jäsenet, joilla on tämä rooli, voivat poistaa foorumiviestejä. |
| Lock posts | | Jäsenet, joilla on tämä rooli, voivat lukita foorumiviestejä. |
| Pin posts | | Jäsenet, joilla on tämä rooli, voivat kiinnittää foorumiviestejä. |
| Create comments | | Jäsenet, joilla on tämä rooli, voivat luoda kommentteja foorumiviesteihin. |
| Remove comments | | Jäsenet, joilla on tämä rooli, voivat poistaa kommentteja foorumiviesteistä. |

Content moderation

| View content moderation | | Jäsenet, joilla on tämä rooli, voivat nähdä sisällön moderoinnin. |
| Manage content moderation | | Jäsenet, joilla on tämä rooli, voivat hallita sisällön moderointia. |

Miscellaneous

| Bypass slow mode | | Jäsenet, joilla on tämä rooli, voivat ohittaa hidastustilan. |
| View community analytics | | Jäsenet, joilla on tämä rooli, voivat nähdä yhteisöanalytiikkaa. |

4.

TÄRKEÄ

 Napsauta Save  -painiketta ottaaksesi käyttöön oikeusasetukset.

5.

VALINNAINEN

 Napsauta Settings  -välilehteä ja valitse väri ja näkyvyysasetukset roolille, sitten napsauta Save  -painiketta.

Roolin Settings  -osio on myös paikka, jossa ryhmän omistajat ja jäsenet, joilla on riittävät oikeudet, voivat poistaa roolin kokonaan Poista rooli  -painikkeen kautta.

Roolit on lueteltu hierarkkisesti: rooli, joka on listassa korkeammalla, on voimakkaampi kuin sen alapuolella oleva rooli. Tämä järjestys on tärkeä, koska jotkin oikeudet antavat jäsenille mahdollisuuden hallita vain rooleja, jotka ovat heidän korkeimman roolinsa alapuolella.

Jokainen rooli on joko julkinen  tai yksityinen . Julkiset roolit voidaan näyttää Yhteisö-sivulla ja kokemuksissa. Yksityiset roolit näkyvät vain rooli- ja oikeushallintapinnalla valtuutetuilla jäsenillä tai jäsenillä, joilla on yksityinen rooli. Näkyvyyden muutokset vaikuttavat siihen, missä rooli näkyy; se ei muuta roolin myöntämiä oikeuksia.

Jotta voit myöntää Manage roles , Assign or remove roles from members , Manage access to this group’s resources , Manage and spend group revenue  tai Delete Data Stores for experiences , sinun on oltava kaksivaiheinen vahvistus käytössä.

## [Jäsenten hallinta](#jäsenten-hallinta)[](#jäsenten-hallinta)

Jäsenen määrittäminen on vain saatavilla, jos olet ryhmän omistaja tai sinulla on lupa hallita muita jäseniä ja heidän roolejaan.

Hallinnoi jäseniä Luojaohjauspaneelista:

1.

Laajenna tilinvaihtajaa vasemmassa yläkulmassa ja valitse ryhmä.

2.

Laajenna tilinvaihtajaa uudelleen ja valitse Members .

3.

Käytä Jäsen -välilehteä etsiäksesi olemassa olevia jäseniä tai suodattaaksesi heitä roolin mukaan. Käytä Kutsutut -välilehteä tarkistaaksesi odottavat kutsut.

Lisätäksesi jäsenen, napsauta Invite  -painiketta ja etsi heidän käyttäjänimensä. Roblox ilmoittaa kutsutuille luojille heidän ilmoitusasetustensa mukaan. Voit myös kopioida ryhmän linkin ja jakaa sen suoraan.

### [Roolien hallinta](#roolien-hallinta)[](#roolien-hallinta)

Voit hallita roolijakoja joko Members  -sivulta tai tietystä roolista:

-

Members  -sivulla napsauta plus (+)  -painiketta jäsenen vieressä avataksesi roolivalikon. Jotta voit jakaa roolin, napsauta plus (+)  -painiketta sen vieressä kohdassa Lisää rooleja . Poistaaksesi rooli, napsauta miinus (-)  -painiketta sen vieressä kohdassa Nykyiset roolit , tai napsauta ×  -painiketta jaetun roolin vieressä jäsenen nimen kohdalla.

-

Roolit -sivulla valitse rooli ja avaa sen Members  -välilehti. Napsauta Add members  -painiketta etsiäksesi ryhmän jäseniä ja jakaa heidät rooliin. Poistaaksesi jäsenen, napsauta miinus (-)  -painiketta heidän rivinsä lopussa.

### [Jäsenen poistaminen](#jäsenen-poistaminen)[](#jäsenen-poistaminen)

Poistaaksesi jäsenen ryhmästä, napsauta ⋮  -painiketta heidän rivinsä lopussa, valitse Poista käyttäjä  ja vahvista toiminto.

## [Maksujen hallinta](#maksujen-hallinta)[](#maksujen-hallinta)

Jos olet ryhmän omistaja tai sinulla on oikeat [oikeudet](#roolit-ja-oikeudet)  Ryhmä Tuloon , löydät Maksut -sivun Rahoitus -osasta vasemmasta navigaatiosta. Täällä voit lähettää kertamaksuja sekä määrittää prosenttijakoja muiden jäsenten kanssa.

Joillakin ryhmillä ei ehkä ole tätä sivua aluksi avattuna eri syistä, kuten ryhmän iästä tai riittämättömistä varoista maksua varten.

Maksuja ei voida jakaa ryhmän jäsenten kesken peleissä, jotka veloittavat [maksullisesta pääsystä paikallisessa valuutassa](/docs/en-us/production/monetization/paid-access-local-currency) .

### [Kertamaksut](#kertamaksut)[](#kertamaksut)

Kertamaksuja voidaan tehdä jäsenille erässä, valitsemalla tietty summa jokaiselle. Turvatoimiin kuuluu 2FA-haasteita, vahvistusdialogeja ja tarkistuksia maksua saavien jäsenten kelpoisuudesta.

 ![Kertamaksupainike merkitty maksusivulla Luojaohjauspaneelissa.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-One-Time.png)

Kun napsautat Lähetä Robux  -painiketta, voit valita maksunsaajat ponnahdusikkunasta tai ladata .csv -taulukkolaskentatiedoston, jossa on sarakkeet userId  ja payoutInRobux , esimerkiksi:

| userId | | payoutInRobux |
| 012345 | | 5000 |
| 098765 | | 7000 |

### [Toistuvat maksut](#toistuvat-maksut)[](#toistuvat-maksut)

Toistuvia maksuja voidaan myös tehdä koko ryhmälle ja  pelikohtaisesti, määrittämällä prosenttiosuus jokaiselle jäsenelle ennen kuin loppusumma siirtyy ryhmän kokonaissaldoon.

 ![Jakomaksupainikkeet merkitty maksusivulla Luojaohjauspaneelissa.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Split-Options.png)

Harkitse seuraavaa skenaariota, jossa ryhmäpeli Laser Maze  jaetaan 40%–30%–10% kolmen jäsenen kesken, ja jäljelle jää 20%.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-A.png)

Oletetaan, että peli ansaitsee 1000 Robuxia, kolme jäsentä saavat 400, 300 ja 100 Robuxia vastaavasti (40%–30%–10%).

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-B.png)

Jäljelle jäävät 200 Robuxia (20% pelin jaosta) siirtyvät ryhmän jakautumisen  prosentteihin, jotka on määritetty 20%–20%–10% samojen kolmen jäsenen kesken; he saavat lisäyhteensä 40, 40 ja 20 Robuxia vastaavasti.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-C.png)

Jäljelle jäävät 100 Robuxia (50% ryhmän jaosta) sijoitetaan ryhmän kokonaissaldoon.

 ![Esimerkkikaavio siitä, kuinka pelin jaot jaetaan ensin ryhmän jäsenille, ja jäljelle jäävät siirretään ryhmän jakautumisiin lopullista jakelua varten.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Splits-Example.png)

Huomaa, että [yksityisten palvelimien](/docs/en-us/production/monetization/private-servers)  tilausmaksut eivät muutu, jos säädät jakoprosentteja myöhemmin, mikä tarkoittaa, että jos pelaaja ostaa yksityisen palvelimen tilauksen, ostohetkellä voimassa olevat jakoprosentit koskevat kyseistä tilausta ikuisesti (kunnes se peruutetaan). Tätä käytäntöä voidaan muuttaa tulevaisuudessa.

## [Ryhmän tarkastuspöytäkirjat](#ryhmän-tarkastuspöytäkirjat)[](#ryhmän-tarkastuspöytäkirjat)

Ryhmäjäsenet, joilla on View audit logs  -oikeus, voivat tarkastella ryhmän muutoksia näiden ryhmän hallintapintojen kautta:

-

Luo Luojaohjauspaneelissa Toimintahistoria  kohdassa Yhteistyö .

-

Yhteisöissä avaa yhteisön kokoonpanosivu ja valitse Tarkastuspöytäkirja .

Ryhmäomistajat voivat käyttää näitä lokitietoja valvoakseen toimintaa, joka saattaa rikkoa [ryhmän ohjeita](/docs/en-us/projects/group-guidelines) .

## [Immateriaalioikeuksien suojaaminen](#immateriaalioikeuksien-suojaaminen)[](#immateriaalioikeuksien-suojaaminen)

Ryhmäjäsenet, joilla on oikeus muokata kaikkia ryhmän pelejä, voivat ottaa käyttöön [Paikan kopiointi](/docs/en-us/projects/configure-games#allow-copying)  -asetuksen luomuksessa, mikä mahdollistaa koko Roblox-yhteisön kopioida sen ja käyttää sen resursseja. Suojellakseen immateriaalioikeuksia ryhmässä, omistajan tai riittävät oikeudet omaavien jäsenten tulisi:

-

Varmistaa, että jokaiselle jäsenelle on [määritetty oikea rooli](#roolien-hallinta) .

-

Tarkistaa, että jokaisella ryhmän roolilla on oikeat [oikeudet](#roolit-ja-oikeudet) .

-

Varmistaa, että [Paikan kopiointi](/docs/en-us/projects/configure-games#allow-copying)  -asetus on poistettu käytöstä ennen yksityisten resurssien lisäämistä.

## [Lisälocalisaatiot tälle sivulle](#lisälocalisaatiot-tälle-sivulle)[](#lisälocalisaatiot-tälle-sivulle)

Lisälocalisoituja versioita tästä sivusta, joita ei ole saatavilla sivuston kielivalitsimessa, katso seuraavat linkit:

-

[Bulgaria (български)](https://create.roblox.com/docs/bg-bg/projects/groups)

-

[Kroatia (hrvatski)](https://create.roblox.com/docs/hr-hr/projects/groups)

-

[Tšekki (čeština)](https://create.roblox.com/docs/cs-cz/projects/groups)

-

[Tanska (dansk)](https://create.roblox.com/docs/da-dk/projects/groups)

-

[Hollanti (Nederlands)](https://create.roblox.com/docs/nl-nl/projects/groups)

-

[Viro (eesti)](https://create.roblox.com/docs/et-ee/projects/groups)

-

[Suomi (suomi)](https://create.roblox.com/docs/fi-fi/projects/groups)

-

[Kreikka (Ελληνικά)](https://create.roblox.com/docs/el-gr/projects/groups)

-

[Unkari (magyar)](https://create.roblox.com/docs/hu-hu/projects/groups)

-

[Irlanti (Gaeilge)](https://create.roblox.com/docs/ga-ie/projects/groups)

-

[Latvia (latviešu)](https://create.roblox.com/docs/lv-lv/projects/groups)

-

[Liettua (lietuvių)](https://create.roblox.com/docs/lt-lt/projects/groups)

-

[Malta (Malti)](https://create.roblox.com/docs/mt-mt/projects/groups)

-

[Portugali - Portugali (português)](https://create.roblox.com/docs/pt-pt/projects/groups)

-

[Romania (română)](https://create.roblox.com/docs/ro-ro/projects/groups)

-

[Slovakki (slovenčina)](https://create.roblox.com/docs/sk-sk/projects/groups)

-

[Slovenia (slovenščina)](https://create.roblox.com/docs/sl-si/projects/groups)

-

[Ruotsi (svenska)](https://create.roblox.com/docs/sv-se/projects/groups)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
