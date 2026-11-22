<!-- Source: https://create.roblox.com/docs/et-ee/projects/groups -->

Grupid (meeskonnad) | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Projects](/docs/en-us/projects)
6. /
7. [Work in teams](/docs/en-us/projects/groups)

# Grupid (meeskonnad)

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Robloxi grupp  võimaldab mitmel loojal töötada sama mängu kallal, kasutada samu varasid, jagada kasumit ja anda krediiti kõigile panustajatele.

Mängude grupi omamine aitab loojatel koostööd teha ja tegutseda iseseisvate stuudiodena. Kui grupis tekib konflikt, ei saa Roblox aidata vahekohtuniku või erimeelsuste lahendamise osas.

## [Grupi loomine](#grupi-loomine)[](#grupi-loomine)

Grupi loomine maksab 100 Robuxi. Saate hallata selle [rolle ja õigusi](#rollid-ja-%C3%B5igused)  [Looja juhtpaneelilt](https://create.roblox.com/dashboard/creations)  või [Kogukondadest](https://www.roblox.com/communities) .

Enne grupi loomist lugege hoolikalt läbi [reeglid ja ootused](/docs/en-us/projects/group-guidelines)  grupi haldamiseks.

Uue grupi loomiseks:

1.

Liikuge [Looja juhtpaneelile](https://create.roblox.com/dashboard/creations) , avage ülemises vasakus nurgas konto vahetaja ja klõpsake pluss (+)  nuppu.

2.

Loo grupp  lehel laadige üles gruppi logo pilt ja sisestage grupi nimi.

3.

Kui olete valmis, klõpsake Osta  nuppu. Kui grupp on loodud, suunatakse teid grupi profiili lehele, kus saate muuta grupi üksikasju, sealhulgas lisada kuni kolm sotsiaalset linki.

## [Rollid ja õigused](#rollid-ja-õigused)[](#rollid-ja-õigused)

Grupi liikmetele saab määrata ühe või mitu rolli  grupis, ja igal rollil on õigused , mis määratlevad selle liikmete võimed.

Rolli seadistamine on saadaval ainult siis, kui olete grupi omanik või teil on luba luua, seadistada ja määrata grupi rolle.

Grupi rollide määramiseks programmiliselt mängu serverist kasutage [HttpService](/docs/en-us/reference/engine/classes/HttpService) , et kutsuda toetatud Open Cloud Groups lõpp-punkte. Seadistamise ja näidiskoodi jaoks vaadake [Kasutamine Open Cloudiga](/docs/en-us/cloud-services/http-service#use-with-open-cloud) .

1.

[Looja juhtpaneelilt](https://create.roblox.com/dashboard/creations)  avage ülemises vasakus nurgas konto vahetaja ja valige grupp.

2.

Avage konto vahetaja uuesti ja valige Rollid .

3.

Iga rolli puhul kinnitage hoolikalt õigused Permissions  vahekaardil.

Õigused on organiseeritud General , Creation  ja Community  kategooriatesse. Allpool kirjeldatakse iga kategooria saadaval olevaid õigusi.

### [Üldine](#üldine)[](#üldine)

Üldised õigused

| Manage roles | | Liikmed, kellel on see õigus, saavad luua, redigeerida, kustutada, ümber korraldada ja määrata või tühistada rolle allpool oma kõrgeimat rolli. Nad saavad redigeerida ainult õigusi, mis neil juba on. |
| --- | --- |
| Assign or remove roles from members | | Liikmed, kellel on see õigus, saavad määrata või tühistada rolle allpool oma kõrgeimat rolli igale liikmele. |
| Invite or approve members | | Liikmed, kellel on see õigus, saavad kutsuda inimesi gruppi ja kinnitada liitumistaotlusi. |
| Kick members | | Liikmed, kellel on see õigus, saavad eemaldada liikmeid, kelle kõrgeim roll on madalam kui nende oma. |
| Ban members | | Liikmed, kellel on see õigus, saavad keelata liikmeid, kelle kõrgeim roll on madalam kui nende oma. |
| Configure group profile | | Liikmed, kellel on see õigus, saavad seadistada grupi profiili. |
| View audit logs | | Liikmed, kellel on see õigus, saavad vaadata [grupi auditi logisid](#grupi-auditi-logid) . |
| Manage allies and enemies | | Liikmed, kellel on see õigus, saavad hallata grupi liitlasi ja vaenlasi. |

### [Loomine](#loomine)[](#loomine)

Creations

| Playtest experiences | | Liikmed, kellel on see roll, saavad mängida kõiki grupi omanduses olevaid mänge, isegi kui need ei ole laiemale publikule välja antud. Valikuline [mänguõigus](/docs/en-us/projects/configure-games) . |
| Edit experiences | | Liikmed, kellel on see roll, saavad redigeerida kõiki grupi omanduses olevaid mänge ja [varasid](/docs/en-us/projects/assets)  ning kasutada kõiki funktsioone [Andmehoidlate halduris](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Ei hõlma mängu redigeerimist väljaspool [koostöö](/docs/en-us/projects/collaboration)  seanssi või koha salvestamist ühest mängust teise. Valikuline [mänguõigus](/docs/en-us/projects/configure-games) . |
| Publish experiences | | Liikmed, kellel on see roll, saavad nii redigeerida mänge, nagu eespool, kui ka avaldada mänge Robloxis. Valikuline [mänguõigus](/docs/en-us/projects/configure-games) . |
| Manage share links | | Liikmed, kellel on see roll, saavad luua/seadistada [jagamislinke](/docs/en-us/production/promotion/share-links) . |
| Manage experience events | | Liikmed, kellel on see roll, saavad luua/seadistada [kogemuse sündmusi](/docs/en-us/production/promotion/experience-events) . |
| Moderate experiences | | Liikmed, kellel on see roll, saavad vaadata kõiki mängusiseseid vestlusi (ainult lugemiseks; liige peab olema 18+) ja keelata või hallata keelatud kasutajaid kõigis grupi omanduses olevates mängudes. |
| Manage monetization for experiences | | Liikmed, kellel on see roll, saavad hallata monetiseerimise tooteid, nagu [piletid](/docs/en-us/production/monetization/passes) , [arendaja tooted](/docs/en-us/production/monetization/developer-products) , [tellimused](/docs/en-us/production/monetization/subscriptions)  ja palju muud. Valikuline [mänguõigus](/docs/en-us/projects/configure-games) . |
| Manage secrets for experiences | | Liikmed, kellel on see roll, saavad näha [saladuste](/docs/en-us/cloud-services/secrets)  loendit ning luua, uuendada ja kustutada saladusi kõigi grupi omanduses olevate mängude jaoks. Selle rolli omavad liikmed vajavad [Edit experiences](#rollid-ja-%C3%B5igused)  õigust, et näha Saladuste lehte. Valikuline [mänguõigus](/docs/en-us/projects/configure-games) . |

Analytics

| View analytics for experiences | | Liikmed, kellel on see roll, saavad juurdepääsu kõigi grupi omanduses olevate mängude [analüütikale](/docs/en-us/production/analytics) , isegi kui neil ei ole redigeerimisõigust. Valikuline [mänguõigus](/docs/en-us/projects/configure-games) . |
| Manage alerts | | Liikmed, kellel on see roll, saavad luua ja hallata analüütika häireid. Siduge see õigus View analytics for experiences -ga, et näha häire märkmeid otse mõõdikute graafikutes. |

Monetization

| View group revenue | | Liikmed, kellel on see roll, saavad vaadata grupi Robuxi saldo, kõik seadistatud korduvad jagatud maksed ja tulude logimise funktsioonid. |
| Manage and spend group revenue | | Liikmed, kellel on see roll, saavad vaadata kogu grupi tulu, nagu eespool, ja ka seda otse hallata. See hõlmab [korduvate maksete](#korduvad-maksed)  seadistamist ja [ühekordsete maksete](#%C3%BChekordsed-maksed)  saatmist koostööpartneritele. |
| Create ad campaigns for the group | | Liikmed, kellel on see roll, saavad reklaamida gruppi. |

Avatar items

| Create avatar items | | Liikmed, kellel on see roll, saavad luua avatarite esemeid, nagu riided. |
| Configure avatar items | | Liikmed, kellel on see roll, saavad seadistada müügiga seotud üksikasju, täiendusi ja sponsoreeringuid olemasolevatele grupi avatarite esemetel. |

API

| Manage API keys | | Liikmed, kellel on see roll, saavad hallata [Open Cloud API võtmeid](/docs/en-us/cloud/auth/api-keys)  grupi jaoks. |

Development items

| View development items | | Liikmed, kellel on see roll, saavad vaadata grupi omanduses olevaid arendusobjekte, näiteks Audio . |
| Manage development items | | Liikmed, kellel on see roll, saavad üles laadida ja seadistada varade arendusobjekte, nagu Decals . |
| Manage development item permissions | | Liikmed, kellel on see roll, saavad seadistada arendusobjektide õigusi, näiteks heli jagamine. |

Data Stores

| View Data Stores for experiences | | Liikmed, kellel on see roll, saavad vaadata andmehoidlaid kõigi grupi mängude jaoks [Andmehoidlate halduri](/docs/en-us/cloud-services/data-stores/data-stores-manager)  kaudu, kuid nad ei saa andmeid kustutada. Valikuline [mänguõigus](/docs/en-us/projects/configure-games) . |
| Edit Data Stores for experiences | | Liikmed, kellel on see roll, saavad kustutada konkreetseid võtmeid andmehoidlatest kõigi grupi mängude jaoks [Andmehoidlate halduri](/docs/en-us/cloud-services/data-stores/data-stores-manager)  kaudu. Valikuline [mänguõigus](/docs/en-us/projects/configure-games) . |
| Delete Data Stores for experiences | | Liikmed, kellel on see roll, saavad kustutada terveid andmehoidlaid kõigi grupi mängude jaoks [Andmehoidlate halduri](/docs/en-us/cloud-services/data-stores/data-stores-manager)  kaudu. Valikuline [mänguõigus](/docs/en-us/projects/configure-games) . |

Notifications

| Manage webhooks for experiences | | Liikmed, kellel on see roll, saavad loetleda, luua, uuendada ja kustutada veebihooke kõigi grupi kogemuste jaoks. |

Communication

| Manage support tickets for experiences | | Liikmed, kellel on see roll, saavad hallata tugipileteid kõigi grupi kogemuste jaoks. |

Legacy

| Haldage juurdepääsu selle grupi ressurssidele | | Liikmed, kellel on see roll, saavad luua ja redigeerida juurdepääsu grupi ressurssidele. |

### [Kogukond](#kogukond)[](#kogukond)

Posts

| View community announcements | | Liikmed, kellel on see roll, saavad vaadata kogukonna teadandeid. |
| Create community announcements | | Liikmed, kellel on see roll, saavad luua kogukonna teadandeid. |

Forums

| Manage categories | | Liikmed, kellel on see roll, saavad hallata foorumi kategooriaid. |
| Create posts | | Liikmed, kellel on see roll, saavad luua foorumi postitusi. |
| Remove posts | | Liikmed, kellel on see roll, saavad eemaldada foorumi postitusi. |
| Lock posts | | Liikmed, kellel on see roll, saavad lukustada foorumi postitusi. |
| Pin posts | | Liikmed, kellel on see roll, saavad kinnitada foorumi postitusi. |
| Create comments | | Liikmed, kellel on see roll, saavad luua kommentaare foorumi postitustes. |
| Remove comments | | Liikmed, kellel on see roll, saavad eemaldada kommentaare foorumi postitustest. |

Content moderation

| View content moderation | | Liikmed, kellel on see roll, saavad vaadata sisu modereerimist. |
| Manage content moderation | | Liikmed, kellel on see roll, saavad hallata sisu modereerimist. |

Miscellaneous

| Bypass slow mode | | Liikmed, kellel on see roll, saavad aeglustuse mööda hiilida. |
| View community analytics | | Liikmed, kellel on see roll, saavad vaadata kogukonna analüütikat. |

4.

OLULINE

 Klõpsake Save  nuppu, et rakendada õiguste seadeid.

5.

VALIKULINE

 Klõpsake Settings  vahekaarti ja valige rolli jaoks värv ja nähtavuse seade, seejärel klõpsake Save  nuppu.

Rolli Settings  sektsioon on ka koht, kus grupi omanikud ja liikmed, kellel on piisavad õigused, saavad rolli täielikult eemaldada Kustuta roll  nupu kaudu.

Rollid on loetletud hierarhilises järjekorras: roll, mis on loendis kõrgemal, omab rohkem volitusi kui allpool olev roll. See järjekord on oluline, kuna mõned õigused lubavad liikmetel hallata rolle ainult allpool oma kõrgeimat rolli.

Iga roll on kas avalik  või privaatne . Avalikud rollid võivad olla nähtavad Kogukonna lehel ja kogemustes. Privaatseid rolle näidatakse ainult rolli ja õiguste haldamise pindadel volitatud liikmetele või liikmetele, kellel on privaatne roll. Nähtavuse muutmine muudab rolli ilmumist; see ei muuda rolli andvaid õigusi.

Et anda Manage roles , Assign or remove roles from members , Manage access to this group’s resources , Manage and spend group revenue  või Delete Data Stores for experiences  õigusi, peate olema lubanud kaheastmelise kinnituse.

## [Hallake liikmeid](#hallake-liikmeid)[](#hallake-liikmeid)

Liikmete seadistamine on saadaval ainult siis, kui olete grupi omanik või teil on luba hallata teisi liikmeid ja nende rolle.

Liikmete haldamiseks Looja juhtpaneelilt:

1.

Avage ülemises vasakus nurgas konto vahetaja ja valige grupp.

2.

Avage konto vahetaja uuesti ja valige Members .

3.

Kasutage Liikme  vahekaarti, et otsida olemasolevaid liikmeid või filtreerida neid rolli järgi. Kasutage Kutsutud  vahekaarti, et vaadata ootel kutseid.

Liikme lisamiseks klõpsake Invite  nuppu ja otsige nende kasutajanime. Roblox teavitab kutsutud loojat vastavalt nende teavitamise eelistustele. Samuti saate kopeerida grupi lingi ja jagada seda otse.

### [Hallake rolle](#hallake-rolle)[](#hallake-rolle)

Saate hallata rollide määramisi kas Members  lehelt või konkreetsest rollist:

-

Members  lehelt klõpsake liikme kõrval pluss (+)  nuppu, et avada rolli menüü. Rolli määramiseks klõpsake selle kõrval pluss (+)  nuppu Lisa rolle  all. Rolli tühistamiseks klõpsake selle kõrval miinus (-)  nuppu Praegused rollid , või klõpsake liikme nime kõrval määratud rolli ×  nuppu.

-

Rollide  lehelt valige roll ja avage selle Members  vahekaart. Klõpsake Add members  nuppu, et otsida grupi liikmeid ja määrata neid rollile. Liikme tühistamiseks klõpsake nende rea lõpus miinus (-)  nuppu.

### [Liikme eemaldamine](#liikme-eemaldamine)[](#liikme-eemaldamine)

Liikme grupist eemaldamiseks klõpsake nende rea lõpus ⋮  nuppu, valige Käivita kasutaja  ja kinnitage toiming.

## [Hallake makseid](#hallake-makseid)[](#hallake-makseid)

Kui olete grupi omanik või teil on õige [õigus](#rollid-ja-%C3%B5igused)  Grupi Tulu  all, leiate vasakpoolses navigeerimises Maksed  lehe. Siin saate saata ühekordseid makseid, samuti määrata protsentuaalseid jagamisi teiste liikmete vahel.

Mõned grupid ei pruugi selle lehe avamiseks algselt olla lukustatud erinevatel põhjustel, näiteks grupi vanus või ebapiisavad vahendid maksmiseks.

Makse ei saa jagada grupi liikmete vahel mängude puhul, mis nõuavad [tasulist juurdepääsu kohaliku valuuta](/docs/en-us/production/monetization/paid-access-local-currency)  kaudu.

### [Ühekordsed maksed](#ühekordsed-maksed)[](#ühekordsed-maksed)

Ühekordseid makseid saab teha liikmetele grupina, valides igaühe jaoks kindla summa. Turvafunktsioonid hõlmavad 2FA väljakutseid, kinnitamise dialooge ja kontrollimist, kas makstavad liikmed on sobivad.

 ![Ühekordse makse nupp, mis on näidatud Looja juhtpaneeli maksete sektsioonis.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-One-Time.png)

Kui olete klõpsanud Saada Robux  nuppu, saate valida makse saajad hüpikaknas või üles laadida .csv  tabelifaili, mille veerud on userId  ja payoutInRobux , näiteks:

| userId | | payoutInRobux |
| 012345 | | 5000 |
| 098765 | | 7000 |

### [Korduvad maksed](#korduvad-maksed)[](#korduvad-maksed)

Korduvaid makseid saab teha kogu grupi ja  mängu kaupa, määrates iga liikme jaoks protsentuaalse makse enne, kui ülejäänud summa läheb grupi üldisele saldole.

 ![Jagatud makse nupp, mis on näidatud Looja juhtpaneeli maksete sektsioonis.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Split-Options.png)

Kujutage ette järgmist stsenaariumi, kus grupimäng Laser Maze  jagatakse 40%–30%–10% kolme liikme vahel, jääk 20%.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-A.png)

Arvestades, et mäng teenib 1000 Robuxi, saavad kolm liiget vastavalt 400, 300 ja 100 Robuxi (40%–30%–10%).

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-B.png)

Jääk 200 Robuxi (20% mängu jagamisest) läheb edasi grupi jagamise  protsentide juurde, mis on määratud 20%–20%–10% kolme sama liikme vahel; nad saavad vastavalt veel 40, 40 ja 20 Robuxi.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-C.png)

Jääk 100 Robuxi (50% grupi jagamisest) paigutatakse grupi üldsaldole.

 ![Näide vooskeemist, kuidas mängu jagamised jaotatakse esmalt grupi liikmetele, jääk läheb grupi jagamiste arvesse lõppjaotamiseks grupi vahel.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Splits-Example.png)

Pange tähele, et [privaatserveri](/docs/en-us/production/monetization/private-servers)  tellimustest saadud tulu ei muutu, kui muudate jagamisprotsentide väärtusi hiljem, mis tähendab, et kui mängija ostab privaatserveri tellimuse, kehtivad ostuhetkel kehtivad jagamisprotsendid selle konkreetse tellimuse kohta igavesti (kuni see tühistatakse). Seda poliitikat võib tulevikus muuta.

## [Grupi auditi logid](#grupi-auditi-logid)[](#grupi-auditi-logid)

Grupi liikmed, kellel on View audit logs  õigus, saavad vaadata grupi muudatusi järgmiste grupihalduse pindade kaudu:

-

Looja juhtpaneelil valige Tegevuse Ajalugu  all Koostöö .

-

Kogukondades avage kogukonna seadistamise leht ja valige Auditi logi .

Grupi omanikud saavad neid logisid kasutada tegevuse jälgimiseks, mis võib rikkuda [grupi juhiseid](/docs/en-us/projects/group-guidelines) .

## [Intellektuaalomandi kaitse](#intellektuaalomandi-kaitse)[](#intellektuaalomandi-kaitse)

Grupi liikmed, kellel on õigus redigeerida kõiki grupi mänge, saavad lubada [Koha kopeerimise](/docs/en-us/projects/configure-games#allow-copying)  seade loomisel, võimaldades potentsiaalselt kogu Roblox kogukonnal seda kopeerida ja kasutada selle sees olevaid varasid. Intellektuaalomandi kaitsmiseks grupis peaks omanik või piisavate õigustega liikmed:

-

Kinnitage, et iga liige on [määritud sobivale rollile](#hallake-rolle) .

-

Kontrollige, et igal grupi rollil on õiged [õigused](#rollid-ja-%C3%B5igused) .

-

Kinnitage, et [Koha kopeerimise](/docs/en-us/projects/configure-games#allow-copying)  seade on keelatud enne privaatsete varade lisamist.

## [Täiendavad lokaliseerimised sellel lehel](#täiendavad-lokaliseerimised-sellel-lehel)[](#täiendavad-lokaliseerimised-sellel-lehel)

Sellel lehel, mis ei ole saadaval saidi keele valijas, on täiendavad lokaliseeritud versioonid:

-

[Bulgaaria (български)](https://create.roblox.com/docs/bg-bg/projects/groups)

-

[Horvaatia (hrvatski)](https://create.roblox.com/docs/hr-hr/projects/groups)

-

[Tšehhi (čeština)](https://create.roblox.com/docs/cs-cz/projects/groups)

-

[Taani (dansk)](https://create.roblox.com/docs/da-dk/projects/groups)

-

[Hollandi (Nederlands)](https://create.roblox.com/docs/nl-nl/projects/groups)

-

[Eesti (eesti)](https://create.roblox.com/docs/et-ee/projects/groups)

-

[Soome (suomi)](https://create.roblox.com/docs/fi-fi/projects/groups)

-

[Kreeka (Ελληνικά)](https://create.roblox.com/docs/el-gr/projects/groups)

-

[Ungari (magyar)](https://create.roblox.com/docs/hu-hu/projects/groups)

-

[Iiri (Gaeilge)](https://create.roblox.com/docs/ga-ie/projects/groups)

-

[Läti (latviešu)](https://create.roblox.com/docs/lv-lv/projects/groups)

-

[Leedu (lietuvių)](https://create.roblox.com/docs/lt-lt/projects/groups)

-

[Malta (Malti)](https://create.roblox.com/docs/mt-mt/projects/groups)

-

[Portugali - Portugal (português)](https://create.roblox.com/docs/pt-pt/projects/groups)

-

[Rumeenia (română)](https://create.roblox.com/docs/ro-ro/projects/groups)

-

[Slovaki (slovenčina)](https://create.roblox.com/docs/sk-sk/projects/groups)

-

[Sloveenia (slovenščina)](https://create.roblox.com/docs/sl-si/projects/groups)

-

[Rootsi (svenska)](https://create.roblox.com/docs/sv-se/projects/groups)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
