<!-- Source: https://create.roblox.com/docs/lt-lt/projects/groups -->

Grupės (komandos) | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Projects](/docs/en-us/projects)
6. /
7. [Work in teams](/docs/en-us/projects/groups)

# Grupės (komandos)

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Roblox grupė  leidžia keliems kūrėjams dirbti prie to paties žaidimo, naudoti tuos pačius išteklius, dalintis pelnu ir suteikti kreditą visiems prisidėjusiems.

Žaidimų grupės nuosavybė padeda kūrėjams bendradarbiauti ir veikti kaip nepriklausomos studijos. Jei grupėje kyla konfliktas, Roblox negali padėti spręsti ar išspręsti nesutarimų.

## [Grupės kūrimas](#grupės-kūrimas)[](#grupės-kūrimas)

Sukurti grupę kainuoja 100 Robux. Galite valdyti jos [roles ir teises](#roles-ir-teis%C4%97s)  iš [Kūrėjo valdymo pulto](https://create.roblox.com/dashboard/creations)  arba [Bendruomenių](https://www.roblox.com/communities) .

Prieš kuriant grupę, atidžiai perskaitykite [taisykles ir lūkesčius](/docs/en-us/projects/group-guidelines)  grupės valdymui.

Norėdami sukurti naują grupę:

1.

Eikite į [Kūrėjo valdymo pultą](https://create.roblox.com/dashboard/creations) , išplėskite paskyros perjungiklį viršuje kairėje ir spustelėkite pliuso (+)  mygtuką.

2.

Sukurti grupę  puslapyje įkelkite grupės logotipo vaizdą ir įveskite grupės pavadinimą.

3.

Kai būsite pasiruošę, spustelėkite Pirkti  mygtuką. Sukūrus grupę, būsite nukreipti į grupės profilio puslapį, kur galėsite redaguoti grupės detales, įskaitant iki trijų socialinių nuorodų pridėjimą.

## [Roles ir teisės](#roles-ir-teisės)[](#roles-ir-teisės)

Grupės nariams gali būti priskirta viena arba kelios roles  grupėje, o kiekviena rolė turi teises , kurios nurodo jos narių galimybes.

Rolės konfigūracija yra prieinama tik tuo atveju, jei esate grupės savininkas arba turite leidimą kurti, konfigūruoti ir priskirti grupės roles.

Norėdami valdyti grupės rolės priskyrimus programiškai iš žaidimo serverio, naudokite [HttpService](/docs/en-us/reference/engine/classes/HttpService) , kad paskambintumėte palaikomiems Open Cloud Groups galiniams taškams. Dėl nustatymo ir pavyzdinės kodo, žr. [Naudokite su Open Cloud](/docs/en-us/cloud-services/http-service#use-with-open-cloud) .

1.

Iš [Kūrėjo valdymo pulto](https://create.roblox.com/dashboard/creations)  išplėskite paskyros perjungiklį viršuje kairėje ir pasirinkite grupę.

2.

Išplėskite paskyros perjungiklį dar kartą ir pasirinkite Roles .

3.

Kiekvienai rolei atidžiai patvirtinkite teises Permissions  skirtuke.

Teisės yra organizuotos į General , Creation  ir Community  kategorijas. Žemiau pateikiamos kiekvienos kategorijos teisių aprašymai.

### [Bendros](#bendros)[](#bendros)

Bendros teisės

| Manage roles | | Nariai, turintys šią teisę, gali kurti, redaguoti, šalinti, perkelti ir priskirti arba atšaukti roles, esančias žemiau jų aukščiausios rolės. Jie gali redaguoti tik teises, kurias jau turi. |
| --- | --- |
| Assign or remove roles from members | | Nariai, turintys šią teisę, gali priskirti arba atšaukti roles, esančias žemiau jų aukščiausios rolės, bet kuriam nariui. |
| Invite or approve members | | Nariai, turintys šią teisę, gali kviesti žmones į grupę ir patvirtinti prisijungimo užklausas. |
| Kick members | | Nariai, turintys šią teisę, gali pašalinti narius, kurių aukščiausia rolė yra žemiau jų pačių. |
| Ban members | | Nariai, turintys šią teisę, gali uždrausti narius, kurių aukščiausia rolė yra žemiau jų pačių. |
| Configure group profile | | Nariai, turintys šią teisę, gali konfigūruoti grupės profilį. |
| View audit logs | | Nariai, turintys šią teisę, gali peržiūrėti [grupės audito žurnalus](#grup%C4%97s-audito-%C5%BEurnalai) . |
| Manage allies and enemies | | Nariai, turintys šią teisę, gali valdyti grupės sąjungininkus ir priešus. |

### [Kūrimas](#kūrimas)[](#kūrimas)

Creations

| Playtest experiences | | Nariai, turintys šią rolę, gali žaisti visus grupės turimus žaidimus, net jei jie nėra išleisti platesnei auditorijai. Pasirinktinai prieinama kaip [per žaidimą leidimas](/docs/en-us/projects/configure-games) . |
| Edit experiences | | Nariai, turintys šią rolę, gali redaguoti visus grupės turimus žaidimus ir [išteklius](/docs/en-us/projects/assets)  bei naudoti visas funkcijas [Duomenų saugyklų valdytojo](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Tai neapima žaidimo redagavimo už [bendradarbiavimo](/docs/en-us/projects/collaboration)  sesijos ribų arba vietos iš vieno žaidimo išsaugojimo kitame žaidime. Pasirinktinai prieinama kaip [per žaidimą leidimas](/docs/en-us/projects/configure-games) . |
| Publish experiences | | Nariai, turintys šią rolę, gali tiek redaguoti žaidimus, kaip nurodyta aukščiau, tiek ir publikuoti žaidimus Roblox. Pasirinktinai prieinama kaip [per žaidimą leidimas](/docs/en-us/projects/configure-games) . |
| Manage share links | | Nariai, turintys šią rolę, gali kurti/konfigūruoti [dalijimosi nuorodas](/docs/en-us/production/promotion/share-links) . |
| Manage experience events | | Nariai, turintys šią rolę, gali kurti/konfigūruoti [patirčių renginius](/docs/en-us/production/promotion/experience-events) . |
| Moderate experiences | | Nariai, turintys šią rolę, gali peržiūrėti visus žaidimo pokalbių pranešimus (tik skaitymui; narys turi būti 18+) ir uždrausti arba valdyti uždraustus vartotojus visose grupės turimose žaidimuose. |
| Manage monetization for experiences | | Nariai, turintys šią rolę, gali valdyti monetizacijos produktus, tokius kaip [prašymai](/docs/en-us/production/monetization/passes) , [kūrėjų produktai](/docs/en-us/production/monetization/developer-products) , [prenumeratos](/docs/en-us/production/monetization/subscriptions)  ir kt. Pasirinktinai prieinama kaip [per žaidimą leidimas](/docs/en-us/projects/configure-games) . |
| Manage secrets for experiences | | Nariai, turintys šią rolę, gali matyti [slaptažodžių](/docs/en-us/cloud-services/secrets)  sąrašą ir gali kurti, atnaujinti ir šalinti slaptažodžius visiems grupės turimiems žaidimams. Nariai, turintys šią rolę, reikalauja Edit experiences  teisės, kad galėtų peržiūrėti Slaptažodžių puslapį. Pasirinktinai prieinama kaip [per žaidimą leidimas](/docs/en-us/projects/configure-games) . |

Analytics

| View analytics for experiences | | Nariai, turintys šią rolę, gali pasiekti visų grupės turimų žaidimų [analitiką](/docs/en-us/production/analytics) , net jei jie neturi redagavimo prieigos. Pasirinktinai prieinama kaip [per žaidimą leidimas](/docs/en-us/projects/configure-games) . |
| Manage alerts | | Nariai, turintys šią rolę, gali kurti ir valdyti analitikos įspėjimus. Sujunkite šią teisę su View analytics for experiences , kad matytumėte įspėjimų anotacijas tiesiogiai ant metrikų grafikų. |

Monetization

| View group revenue | | Nariai, turintys šią rolę, gali peržiūrėti grupės Robux balansą, bet kokius sukonfigūruotus periodinius išmokėjimus ir pajamų registravimo funkcijas. |
| Manage and spend group revenue | | Nariai, turintys šią rolę, gali peržiūrėti visas grupės pajamas, kaip nurodyta aukščiau, ir taip pat tiesiogiai jas valdyti. Tai apima [periodinių išmokėjimų](#periodin%C4%97s-i%C5%A1mokos)  nustatymą ir [vienkartinių išmokėjimų](#vienkartin%C4%97s-i%C5%A1mokos)  siuntimą bendradarbiams. |
| Create ad campaigns for the group | | Nariai, turintys šią rolę, gali reklamuoti grupę. |

Avatar items

| Create avatar items | | Nariai, turintys šią rolę, gali kurti avataro daiktus, tokius kaip drabužiai. |
| Configure avatar items | | Nariai, turintys šią rolę, gali konfigūruoti pardavimo detales, papildymus ir rėmimus esamiems grupės avataro daiktams. |

API

| Manage API keys | | Nariai, turintys šią rolę, gali valdyti [Open Cloud API raktus](/docs/en-us/cloud/auth/api-keys)  grupėje. |

Development items

| View development items | | Nariai, turintys šią rolę, gali peržiūrėti grupės turimus kūrimo daiktus, pavyzdžiui, Garso . |
| Manage development items | | Nariai, turintys šią rolę, gali įkelti ir konfigūruoti turto kūrimo daiktus, tokius kaip Dekoracijos . |
| Manage development item permissions | | Nariai, turintys šią rolę, gali konfigūruoti kūrimo daiktų teises, pavyzdžiui, garso dalijimą. |

Data Stores

| View Data Stores for experiences | | Nariai, turintys šią rolę, gali peržiūrėti duomenų saugyklas visiems grupės žaidimams per [Duomenų saugyklų valdytoją](/docs/en-us/cloud-services/data-stores/data-stores-manager) , tačiau jie negali šalinti duomenų. Pasirinktinai prieinama kaip [per žaidimą leidimas](/docs/en-us/projects/configure-games) . |
| Edit Data Stores for experiences | | Nariai, turintys šią rolę, gali šalinti konkrečius raktus duomenų saugyklose visiems grupės žaidimams per [Duomenų saugyklų valdytoją](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Pasirinktinai prieinama kaip [per žaidimą leidimas](/docs/en-us/projects/configure-games) . |
| Delete Data Stores for experiences | | Nariai, turintys šią rolę, gali šalinti visą duomenų saugyklą visiems grupės žaidimams per [Duomenų saugyklų valdytoją](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Pasirinktinai prieinama kaip [per žaidimą leidimas](/docs/en-us/projects/configure-games) . |

Notifications

| Manage webhooks for experiences | | Nariai, turintys šią rolę, gali sąrašą, kurti, atnaujinti ir šalinti webhook'us visoms grupės patirtims. |

Communication

| Manage support tickets for experiences | | Nariai, turintys šią rolę, gali valdyti palaikymo bilietus visoms grupės patirtims. |

Legacy

| Valdyti prieigą prie šios grupės išteklių | | Nariai, turintys šią rolę, gali kurti ir redaguoti prieigą prie grupės išteklių. |

### [Bendruomenė](#bendruomenė)[](#bendruomenė)

Posts

| View community announcements | | Nariai, turintys šią rolę, gali peržiūrėti bendruomenės pranešimus. |
| Create community announcements | | Nariai, turintys šią rolę, gali kurti bendruomenės pranešimus. |

Forums

| Manage categories | | Nariai, turintys šią rolę, gali valdyti forumo kategorijas. |
| Create posts | | Nariai, turintys šią rolę, gali kurti forumo įrašus. |
| Remove posts | | Nariai, turintys šią rolę, gali šalinti forumo įrašus. |
| Lock posts | | Nariai, turintys šią rolę, gali užrakinti forumo įrašus. |
| Pin posts | | Nariai, turintys šią rolę, gali prisegti forumo įrašus. |
| Create comments | | Nariai, turintys šią rolę, gali kurti komentarus forumo įrašuose. |
| Remove comments | | Nariai, turintys šią rolę, gali šalinti komentarus iš forumo įrašų. |

Content moderation

| View content moderation | | Nariai, turintys šią rolę, gali peržiūrėti turinio moderavimą. |
| Manage content moderation | | Nariai, turintys šią rolę, gali valdyti turinio moderavimą. |

Miscellaneous

| Bypass slow mode | | Nariai, turintys šią rolę, gali apeiti lėto režimo. |
| View community analytics | | Nariai, turintys šią rolę, gali peržiūrėti bendruomenės analitiką. |

4.

SVARBU

 Spustelėkite Save  mygtuką, kad pritaikytumėte teisių nustatymus.

5.

PASIRINKTINAI

 Spustelėkite Settings  skirtuką ir pasirinkite spalvą bei matomumo nustatymą rolei, tada spustelėkite Save  mygtuką.

Rolės Settings  skyrius taip pat yra vieta, kur grupės savininkai ir nariai, turintys pakankamai teisių, gali visiškai pašalinti rolę per Pašalinti rolę  mygtuką.

Roles yra išvardytos hierarchine tvarka: rolė, esanti aukščiau sąraše, turi daugiau įgaliojimų nei rolė, esanti žemiau. Ši tvarka yra svarbi, nes kai kurios teisės leidžia nariams valdyti roles, esančias žemiau jų pačios aukščiausios rolės.

Kiekviena rolė yra arba vieša , arba privati . Viešosios rolės gali būti rodomos Bendruomenės puslapyje ir patirtyse. Privatos rolės rodomos tik rolės ir teisių valdymo paviršiuose įgaliotiems nariams arba nariams, kurie turi privatų rolę. Matomumo pokyčiai keičia, kur rodomas rolė; tai nekeičia teisių, kurias rolė suteikia.

Norint suteikti Manage roles , Assign or remove roles from members , Manage access to this group’s resources , Manage and spend group revenue  arba Delete Data Stores for experiences , turite turėti įgalintą dviejų žingsnių patvirtinimą.

## [Valdyti narius](#valdyti-narius)[](#valdyti-narius)

Narių konfigūracija yra prieinama tik tuo atveju, jei esate grupės savininkas arba turite leidimą valdyti kitus narius ir jų roles.

Norėdami valdyti narius iš Kūrėjo valdymo pulto:

1.

Išplėskite paskyros perjungiklį viršuje kairėje ir pasirinkite grupę.

2.

Išplėskite paskyros perjungiklį dar kartą ir pasirinkite Members .

3.

Naudokite Narys  skirtuką, kad ieškotumėte esamų narių arba filtruotumėte juos pagal rolę. Naudokite Kviesti  skirtuką, kad peržiūrėtumėte laukiančias kvietimus.

Norėdami pridėti narį, spustelėkite Invite  mygtuką ir ieškokite jų vartotojo vardo. Roblox praneša pakviestiems kūrėjams pagal jų pranešimų nustatymus. Taip pat galite kopijuoti grupės nuorodą ir pasidalyti ja tiesiogiai.

### [Valdyti roles](#valdyti-roles)[](#valdyti-roles)

Galite valdyti rolės priskyrimus tiek Members  puslapyje, tiek konkrečioje rolėje:

-

Members  puslapyje spustelėkite pliuso (+)  mygtuką šalia nario, kad atidarytumėte rolės meniu. Norėdami priskirti rolę, spustelėkite pliuso (+)  mygtuką šalia jos po Pridėti roles . Norėdami atšaukti rolę, spustelėkite minus (-)  mygtuką šalia jos po Dabartinės roles , arba spustelėkite ×  mygtuką ant priskirtos rolės šalia nario vardo.

-

Roles  puslapyje pasirinkite rolę ir atidarykite jos Members  skirtuką. Spustelėkite Add members  mygtuką, kad ieškotumėte grupės narių ir priskirtumėte juos rolėms. Norėdami atšaukti narį, spustelėkite minus (-)  mygtuką jų eilutės pabaigoje.

### [Nario pašalinimas](#nario-pašalinimas)[](#nario-pašalinimas)

Norėdami pašalinti narį iš grupės, spustelėkite ⋮  mygtuką jų eilutės pabaigoje, pasirinkite Pašalinti vartotoją  ir patvirtinkite veiksmą.

## [Valdyti išmokas](#valdyti-išmokas)[](#valdyti-išmokas)

Jei esate grupės savininkas arba turite tinkamą [leidimą](#roles-ir-teis%C4%97s)  Grupės Pajamose , rasite Išmokos  puslapį po Finansai  kairėje navigacijoje. Čia galite siųsti vienkartines išmokas, taip pat nustatyti procentinius pasidalijimus su kitais nariais.

Kai kurios grupės gali neturėti šio puslapio atrakinto iš pradžių dėl įvairių priežasčių, tokių kaip grupės amžius arba nepakankamos lėšos išmokoms.

Išmokos negali būti dalijamos tarp grupės narių žaidimams, kurie ima mokestį už [mokamą prieigą vietine valiuta](/docs/en-us/production/monetization/paid-access-local-currency) .

### [Vienkartinės išmokos](#vienkartinės-išmokos)[](#vienkartinės-išmokos)

Vienkartinės išmokos gali būti atliekamos nariams grupėje, pasirenkant nustatytą sumą kiekvienam. Saugumo funkcijos apima 2FA iššūkius, patvirtinimo dialogus ir patikrinimus dėl narių, kurie gauna mokėjimus, tinkamumo.

 ![Vienkartinės išmokos mygtukas nurodytas Išmokų skyriuje Kūrėjo valdymo pultu.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-One-Time.png)

Kai spustelėsite Siųsti Robux  mygtuką, galite pasirinkti išmokų gavėjus iš iššokančio lango arba įkelti .csv  skaičiuoklės failą su stulpeliais userId  ir payoutInRobux , pavyzdžiui:

| userId | | payoutInRobux |
| 012345 | | 5000 |
| 098765 | | 7000 |

### [Periodinės išmokos](#periodinės-išmokos)[](#periodinės-išmokos)

Periodinės išmokos taip pat gali būti atliekamos visai grupei ir  per žaidimą, priskiriant procentinę išmoką kiekvienam nariui prieš likutį, kuris patenka į grupės bendrą balansą.

 ![Pasidalijimo išmokų mygtukai nurodyti Išmokų skyriuje Kūrėjo valdymo pultu.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Split-Options.png)

Apsvarstykite šį scenarijų, kai grupės žaidimas Laser Maze  yra padalintas 40%–30%–10% tarp trijų narių, o likutis yra 20%.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-A.png)

Jei žaidimas uždirba 1000 Robux, trys nariai gauna 400, 300 ir 100 Robux atitinkamai (40%–30%–10%).

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-B.png)

Likusieji 200 Robux (20% žaidimo pasidalijimo) perduodami grupės pasidalijimo  procentams, nustatytiems 20%–20%–10% tarp tų pačių trijų narių; jie gauna papildomai 40, 40 ir 20 Robux atitinkamai.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-C.png)

Likusieji 100 Robux (50% grupės pasidalijimo) patenka į grupės bendrą balansą.

 ![Pavyzdinė srauto diagrama, kaip žaidimo pasidalijimai pirmiausia paskirstomi grupės nariams, o likutis įtraukiamas į grupės pasidalijimus galutiniam paskirstymui tarp grupės.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Splits-Example.png)

Atkreipkite dėmesį, kad pajamos iš [privatų serverį](/docs/en-us/production/monetization/private-servers)  prenumeratų nesikeičia, jei vėliau pakeisite pasidalijimo procentus, tai reiškia, kad jei žaidėjas perka privatų serverio prenumeratą, pasidalijimo procentai, galiojantys pirkimo metu, bus taikomi šiai konkrečiai prenumeratai amžinai (kol ji bus atšaukta). Ši politika gali būti pakeista ateityje.

## [Grupės audito žurnalai](#grupės-audito-žurnalai)[](#grupės-audito-žurnalai)

Grupės nariai, turintys View audit logs  teisę, gali peržiūrėti grupės pakeitimus naudodami šiuos grupės valdymo paviršius:

-

Kūrėjo valdymo pultuose pasirinkite Veiklos Istorija  po Bendradarbiavimas .

-

Bendruomenėse atidarykite bendruomenės konfigūracijos puslapį ir pasirinkite Audito žurnalas .

Grupės savininkai gali naudoti šiuos žurnalus stebėti veiklą, kuri gali pažeisti [grupės gaires](/docs/en-us/projects/group-guidelines) .

## [Intelektinės nuosavybės apsauga](#intelektinės-nuosavybės-apsauga)[](#intelektinės-nuosavybės-apsauga)

Grupės nariai, turintys leidimą redaguoti visus grupės žaidimus, gali įgalinti [Vietos kopijavimą](/docs/en-us/projects/configure-games#allow-copying)  nustatymą kūrime, potencialiai leidžiančiu visai Roblox bendruomenei kopijuoti jį ir naudoti jame esančius išteklius. Norint padėti apsaugoti intelektinę nuosavybę grupėje, savininkas arba nariai, turintys pakankamai teisių, turėtų:

-

Patvirtinti, kad kiekvienas narys yra [priskirtas tinkamai rolei](#valdyti-roles) .

-

Patikrinti, ar kiekviena grupės rolė turi teisingas [teises](#roles-ir-teis%C4%97s) .

-

Patvirtinti, kad [Vietos kopijavimas](/docs/en-us/projects/configure-games#allow-copying)  nustatymas yra išjungtas prieš pridedant privačius išteklius.

## [Papildomos lokalizacijos šiai svetainei](#papildomos-lokalizacijos-šiai-svetainei)[](#papildomos-lokalizacijos-šiai-svetainei)

Dėl papildomų lokalizuotų šios svetainės versijų, kurios nėra prieinamos svetainės kalbos pasirinkiklyje, žr. šias nuorodas:

-

[Bulgarų (български)](https://create.roblox.com/docs/bg-bg/projects/groups)

-

[Kroatų (hrvatski)](https://create.roblox.com/docs/hr-hr/projects/groups)

-

[Čekų (čeština)](https://create.roblox.com/docs/cs-cz/projects/groups)

-

[Danų (dansk)](https://create.roblox.com/docs/da-dk/projects/groups)

-

[Nyderlandų (Nederlands)](https://create.roblox.com/docs/nl-nl/projects/groups)

-

[Estų (eesti)](https://create.roblox.com/docs/et-ee/projects/groups)

-

[Suomių (suomi)](https://create.roblox.com/docs/fi-fi/projects/groups)

-

[Graikų (Ελληνικά)](https://create.roblox.com/docs/el-gr/projects/groups)

-

[Vengrų (magyar)](https://create.roblox.com/docs/hu-hu/projects/groups)

-

[Airių (Gaeilge)](https://create.roblox.com/docs/ga-ie/projects/groups)

-

[Latvių (latviešu)](https://create.roblox.com/docs/lv-lv/projects/groups)

-

[Lietuvių (lietuvių)](https://create.roblox.com/docs/lt-lt/projects/groups)

-

[Maltiečių (Malti)](https://create.roblox.com/docs/mt-mt/projects/groups)

-

[Portugalų - Portugalas (português)](https://create.roblox.com/docs/pt-pt/projects/groups)

-

[Rumunų (română)](https://create.roblox.com/docs/ro-ro/projects/groups)

-

[Slovakų (slovenčina)](https://create.roblox.com/docs/sk-sk/projects/groups)

-

[Slovėnų (slovenščina)](https://create.roblox.com/docs/sl-si/projects/groups)

-

[Švedų (svenska)](https://create.roblox.com/docs/sv-se/projects/groups)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
