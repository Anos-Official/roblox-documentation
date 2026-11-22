<!-- Source: https://create.roblox.com/docs/mt-mt/projects/groups -->

Grupp (timijiet) | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Projects](/docs/en-us/projects)
6. /
7. [Work in teams](/docs/en-us/projects/groups)

# Grupp (timijiet)

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Grupp ta' Roblox grupp  jippermetti li diversi krejaturi jaħdmu fuq l-istess logħba, jużaw l-istess assi, jaqsmu l-profitti, u jagħtu kreditu lil kulħadd li jikkontribwixxi.

Il-proprjetà tal-grupp ta' logħob tgħin lill-krejaturi jikkollaboraw u jaħdmu bħala studjos indipendenti. Jekk ikun hemm kunflitt fi grupp, Roblox ma tistax tgħin biex tintervjeni jew tirrisolvi d-differenzi.

## [Kreazzjoni tal-grupp](#kreazzjoni-tal-grupp)[](#kreazzjoni-tal-grupp)

Il-ħolqien ta' grupp jiswa 100 Robux. Tista' timmaniġġa l-[ruoli u l-permessi](#ruoli-u-permessi)  tiegħu mill-[Creator Dashboard](https://create.roblox.com/dashboard/creations)  jew mill-[Komunitajiet](https://www.roblox.com/communities) .

Qabel ma toħloq grupp, aqra bir-reqqa l-[regoli u l-aspettattivi](/docs/en-us/projects/group-guidelines)  għall-immaniġġjar tal-grupp.

Biex toħloq grupp ġdid:

1.

Naviga lejn il-[Creator Dashboard](https://create.roblox.com/dashboard/creations) , espandi l-għażla tal-kont fil-kantuniera ta' fuq ix-xellug, u ikklikkja l-buttuna plus (+) .

2.

Fuq il-paġna Oħloq Grupp , ibgħat immaġni għall-logo tal-grupp u daħħal isem il-grupp.

3.

Meta tkun lesta, ikklikkja l-buttuna Ixtri . Ladarba l-grupp jiġi maħluq, inti tkun imdawra lejn il-paġna tal-profil tal-grupp fejn tista' tbiddel id-dettalji tal-grupp, inkluż l-addizzjoni ta' sa tliet links soċjali.

## [Ruoli u permessi](#ruoli-u-permessi)[](#ruoli-u-permessi)

Il-membri tal-grupp jistgħu jiġu assenjati wieħed jew aktar ruoli  fi grupp, u kull rol għandu permessi  li jiddeskrivu l-abbiltajiet tal-membri tiegħu.

Il-konfigurazzjoni tar-ruoli hija aċċessibbli biss jekk int il-proprjetar tal-grupp jew għandek permess biex toħloq, tikkonfigura, u tassigna r-ruoli tal-grupp.

Biex timmaniġġa l-assegnazzjonijiet tar-ruoli tal-grupp b'mod programmatiċi minn server tal-logħba, uża [HttpService](/docs/en-us/reference/engine/classes/HttpService)  biex tikkalla l-endpoints tal-Gruppi Open Cloud appoġġati. Għal settup u kodiċi ta' eżempju, ara [Uża ma' Open Cloud](/docs/en-us/cloud-services/http-service#use-with-open-cloud) .

1.

Mill-[Creator Dashboard](https://create.roblox.com/dashboard/creations) , espandi l-għażla tal-kont fil-kantuniera ta' fuq ix-xellug u agħżel il-grupp.

2.

Espandi l-għażla tal-kont mill-ġdid u agħżel Ruoli .

3.

Għal kull rol, ikkonferma bir-reqqa l-permessi taħt it-tab Permissions .

Il-permessi huma organizzati f'kategoriji General , Creation , u Community . Is-sezzjonijiet li ġejjin jiddeskrivu l-permessi disponibbli f'kull kategorija.

### [Ġenerali](#ġenerali)[](#ġenerali)

Permessi Ġenerali

| Manage roles | | Il-membri li għandhom dan il-permess jistgħu joħolqu, jeditjaw, jneħħu, jiddisponu, u jassignaw jew jnaqqsu r-ruoli taħt ir-ruol tagħhom l-aqwa. Huma jistgħu jeditjaw biss il-permessi li diġà għandhom. |
| --- | --- |
| Assign or remove roles from members | | Il-membri li għandhom dan il-permess jistgħu jassignaw jew jnaqqsu r-ruoli taħt ir-ruol tagħhom l-aqwa lil kwalunkwe membru. |
| Invite or approve members | | Il-membri li għandhom dan il-permess jistgħu jinvità lin-nies għall-grupp u japprovaw it-talbiet biex jingħaqdu. |
| Kick members | | Il-membri li għandhom dan il-permess jistgħu jneħħu membri li r-ruol tagħhom l-aqwa huwa taħt tagħhom. |
| Ban members | | Il-membri li għandhom dan il-permess jistgħu jbanjaw membri li r-ruol tagħhom l-aqwa huwa taħt tagħhom. |
| Configure group profile | | Il-membri li għandhom dan il-permess jistgħu jikkonfiguraw il-profil tal-grupp. |
| View audit logs | | Il-membri li għandhom dan il-permess jistgħu jaraw [logs ta' audit tal-grupp](#logs-ta-audit-tal-grupp) . |
| Manage allies and enemies | | Il-membri li għandhom dan il-permess jistgħu jmexxu l-alleati u l-għedewwa tal-grupp. |

### [Kreazzjoni](#kreazzjoni)[](#kreazzjoni)

Creations

| Playtest experiences | | Il-membri li għandhom dan ir-ruol jistgħu jilagħbu l-logħob kollu li huwa proprjetà tal-grupp, anke jekk ma jkunux rilaxxati għal udjenza usa'. Disponibbli bħala [permess għal kull logħba](/docs/en-us/projects/configure-games) . |
| Edit experiences | | Il-membri li għandhom dan ir-ruol jistgħu jeditjaw il-logħob kollu u l-[assi](/docs/en-us/projects/assets)  li huma proprjetà tal-grupp u jużaw il-karatteristiċi kollha fil-[Data Stores Manager](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Ma jinkludix l-editjar ta' logħba barra minn sessjoni [kollaborattiva](/docs/en-us/projects/collaboration)  jew il-ħażna ta' post minn logħba għal oħra. Disponibbli bħala [permess għal kull logħba](/docs/en-us/projects/configure-games) . |
| Publish experiences | | Il-membri li għandhom dan ir-ruol jistgħu kemm jeditjaw il-logħob, kif imsemmi qabel, kif ukoll jippubblikaw il-logħob għal Roblox. Disponibbli bħala [permess għal kull logħba](/docs/en-us/projects/configure-games) . |
| Manage share links | | Il-membri li għandhom dan ir-ruol jistgħu joħolqu/jikkonfiguraw [links ta' qsim](/docs/en-us/production/promotion/share-links) . |
| Manage experience events | | Il-membri li għandhom dan ir-ruol jistgħu joħolqu/jikkonfiguraw [avvenimenti tal-esperjenza](/docs/en-us/production/promotion/experience-events) . |
| Moderate experiences | | Il-membri li għandhom dan ir-ruol jistgħu jaraw il-messaġġi kollha tal-chat fil-logħba (read-only; il-membru għandu jkun 18+) u jbanjaw jew jmexxu utenti mbanjati madwar il-logħob kollu li huma proprjetà tal-grupp. |
| Manage monetization for experiences | | Il-membri li għandhom dan ir-ruol jistgħu jmexxu prodotti ta' monetizzazzjoni bħal [passes](/docs/en-us/production/monetization/passes) , [prodotti tal-iżviluppatur](/docs/en-us/production/monetization/developer-products) , [abbonamenti](/docs/en-us/production/monetization/subscriptions) , u aktar. Disponibbli bħala [permess għal kull logħba](/docs/en-us/projects/configure-games) . |
| Manage secrets for experiences | | Il-membri li għandhom dan ir-ruol jistgħu jaraw il-lista ta' [sigrieti](/docs/en-us/cloud-services/secrets)  u jistgħu joħolqu, aġġornaw, u jneħħu sigrieti għal kull logħba li hija proprjetà tal-grupp. Il-membri li għandhom dan ir-ruol jeħtieġu il-permess Edit experiences  biex jaraw il-paġna tas-Sigrieti. Disponibbli bħala [permess għal kull logħba](/docs/en-us/projects/configure-games) . |

Analytics

| View analytics for experiences | | Il-membri li għandhom dan ir-ruol jistgħu aċċessaw l-[analitika](/docs/en-us/production/analytics)  tal-logħob kollu li huma proprjetà tal-grupp, anke jekk m'għandhomx aċċess għall-editjar. Disponibbli bħala [permess għal kull logħba](/docs/en-us/projects/configure-games) . |
| Manage alerts | | Il-membri li għandhom dan ir-ruol jistgħu joħolqu u jmexxu allerta analitika. Ippairja dan il-permess ma' View analytics for experiences  biex tara annotazzjonijiet tal-allerta direttament fuq il-graffi tal-metriċi. |

Monetization

| View group revenue | | Il-membri li għandhom dan ir-ruol jistgħu jaraw il-bilanċ ta' Robux tal-grupp, kwalunkwe pagamenti ripetuti konfigurati, u karatteristiċi ta' logging tal-profitti. |
| Manage and spend group revenue | | Il-membri li għandhom dan ir-ruol jistgħu jaraw il-profitti kollha tal-grupp, kif imsemmi qabel, u wkoll jmexxuha direttament. Dan jinkludi l-impostazzjoni ta' [pagamenti ripetuti](#pagamenti-ripetuti)  u l-ħlas ta' [pagamenti waħedin](#pagamenti-wa%C4%A7edin)  lill-kollaboraturi. |
| Create ad campaigns for the group | | Il-membri li għandhom dan ir-ruol jistgħu jippromwovu l-grupp. |

Avatar items

| Create avatar items | | Il-membri li għandhom dan ir-ruol jistgħu joħolqu oġġetti tal-avatar bħal ħwejjeġ. |
| Configure avatar items | | Il-membri li għandhom dan ir-ruol jistgħu jikkonfiguraw id-dettalji tal-bejgħ, ir-restocks, u s-sponsorizzazzjonijiet għall-oġġetti tal-avatar eżistenti tal-grupp. |

API

| Manage API keys | | Il-membri li għandhom dan ir-ruol jistgħu jmexxu [API keys ta' Open Cloud](/docs/en-us/cloud/auth/api-keys)  għall-grupp. |

Development items

| View development items | | Il-membri li għandhom dan ir-ruol jistgħu jaraw oġġetti ta' żvilupp li huma proprjetà tal-grupp, pereżempju Audio . |
| Manage development items | | Il-membri li għandhom dan ir-ruol jistgħu jdaħħlu u jikkonfiguraw oġġetti ta' żvilupp tal-assi bħal Decals . |
| Manage development item permissions | | Il-membri li għandhom dan ir-ruol jistgħu jikkonfiguraw il-permessi ta' oġġetti ta' żvilupp, pereżempju l-qsim tal-audio. |

Data Stores

| View Data Stores for experiences | | Il-membri li għandhom dan ir-ruol jistgħu jaraw il-data stores għal kull logħba tal-grupp permezz tal-[Data Stores Manager](/docs/en-us/cloud-services/data-stores/data-stores-manager) , iżda ma jistgħux jneħħu d-data. Disponibbli bħala [permess għal kull logħba](/docs/en-us/projects/configure-games) . |
| Edit Data Stores for experiences | | Il-membri li għandhom dan ir-ruol jistgħu jneħħu ċerti keys fil-data stores għal kull logħba tal-grupp permezz tal-[Data Stores Manager](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Disponibbli bħala [permess għal kull logħba](/docs/en-us/projects/configure-games) . |
| Delete Data Stores for experiences | | Il-membri li għandhom dan ir-ruol jistgħu jneħħu l-data stores kollha għal kull logħba tal-grupp permezz tal-[Data Stores Manager](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Disponibbli bħala [permess għal kull logħba](/docs/en-us/projects/configure-games) . |

Notifications

| Manage webhooks for experiences | | Il-membri li għandhom dan ir-ruol jistgħu jlistaw, joħolqu, jħejju, u jneħħu webhooks għal kull esperjenza tal-grupp. |

Communication

| Manage support tickets for experiences | | Il-membri li għandhom dan ir-ruol jistgħu jmexxu t-tikets ta' appoġġ għal kull esperjenza tal-grupp. |

Legacy

| Immaniġġa l-aċċess għal riżorsi ta' dan il-grupp | | Il-membri li għandhom dan ir-ruol jistgħu joħolqu u jeditjaw l-aċċess għal riżorsi tal-grupp. |

### [Komunità](#komunità)[](#komunità)

Posts

| View community announcements | | Il-membri li għandhom dan ir-ruol jistgħu jaraw l-annunzji tal-komunità. |
| Create community announcements | | Il-membri li għandhom dan ir-ruol jistgħu joħolqu annunzji tal-komunità. |

Forums

| Manage categories | | Il-membri li għandhom dan ir-ruol jistgħu jmexxu kategoriji tal-forum. |
| Create posts | | Il-membri li għandhom dan ir-ruol jistgħu joħolqu posts fil-forum. |
| Remove posts | | Il-membri li għandhom dan ir-ruol jistgħu jneħħu posts fil-forum. |
| Lock posts | | Il-membri li għandhom dan ir-ruol jistgħu jlockjaw posts fil-forum. |
| Pin posts | | Il-membri li għandhom dan ir-ruol jistgħu jpinjaw posts fil-forum. |
| Create comments | | Il-membri li għandhom dan ir-ruol jistgħu joħolqu kummenti fuq posts fil-forum. |
| Remove comments | | Il-membri li għandhom dan ir-ruol jistgħu jneħħu kummenti minn posts fil-forum. |

Content moderation

| View content moderation | | Il-membri li għandhom dan ir-ruol jistgħu jaraw il-moderazzjoni tal-kontenut. |
| Manage content moderation | | Il-membri li għandhom dan ir-ruol jistgħu jmexxu l-moderazzjoni tal-kontenut. |

Miscellaneous

| Bypass slow mode | | Il-membri li għandhom dan ir-ruol jistgħu jaqbżu l-mod ta' bil-mod. |
| View community analytics | | Il-membri li għandhom dan ir-ruol jistgħu jaraw l-analitika tal-komunità. |

4.

IMPORTANT

 Ikklikkja l-buttuna Save  biex tapplika l-impostazzjonijiet tal-permess.

5.

OPTIONAL

 Ikklikkja t-tab Settings  u agħżel kulur u sett ta' viżibilità għall-rol, imbagħad ikklikkja l-buttuna Save .

Is-sezzjoni Settings  ta' rol hija wkoll fejn il-proprjetar tal-grupp u l-membri bi permessi biżżejjed jistgħu jneħħu rol kompletament permezz tal-buttuna Ħassar Rol .

Ir-ruoli huma elenkati fl-ordni tal-jerarkija: rol ogħla fil-lista għandu aktar awtorità minn rol taħt tiegħu. Din l-ordni għandha importanza għax xi permessi jippermettu biss lill-membri jmexxu r-ruoli taħt ir-ruol l-aqwa tagħhom.

Kull rol huwa pubbliku  jew privat . Ir-ruoli pubbliċi jistgħu jidhru fuq paġna tal Komunità u fl-esperjenzi. Ir-ruoli privati jidhru biss fuq il-pjanijiet ta' rol u immaniġġjar tal-permessi għal membri awtorizzati, jew għal membri li għandhom ir-ruol privat. Il-viżibilità tbiddel fejn jidher rol; ma tbiddilx il-permessi li r-rol jagħti.

Biex tagħti Manage roles , Assign or remove roles from members , Manage access to this group’s resources , Manage and spend group revenue , jew Delete Data Stores for experiences , trid ikollok verifika b'żewġ passi attivata.

## [Immaniġġa l-membri](#immaniġġa-l-membri)[](#immaniġġa-l-membri)

Il-konfigurazzjoni tal-membri hija aċċessibbli biss jekk int il-proprjetar tal-grupp jew għandek permess biex timmaniġġa membri oħra u r-ruoli tagħhom.

Biex timmaniġġa l-membri mill-Creator Dashboard:

1.

Espandi l-għażla tal-kont fil-kantuniera ta' fuq ix-xellug u agħżel il-grupp.

2.

Espandi l-għażla tal-kont mill-ġdid u agħżel Members .

3.

Uża t-tab Membru  biex tfittxija għal membri eżistenti jew filtra minnhom skont ir-ruol. Uża t-tab Invitati  biex tirrevedi l-invitazzjonijiet pendenti.

Biex iżżid membru, ikklikkja l-buttuna Invite  u tfittxija għal isem ta' l-utent tagħhom. Roblox tinforma lill-krejaturi mistiedna skont il-preferenzi tagħhom ta' notifika. Tista' wkoll tikkopja l-link tal-grupp u taqsamha direttament.

### [Immaniġġa r-ruoli](#immaniġġa-r-ruoli)[](#immaniġġa-r-ruoli)

Tista' timmaniġġa l-assegnazzjonijiet tar-ruoli kemm mill-paġna Members  jew minn rol speċifiku:

-

Fuq il-paġna Members , ikklikkja l-buttuna plus (+)  ħdejn membru biex tiftaħ il-menu tar-ruoli. Biex tassigna rol, ikklikkja l-buttuna plus (+)  ħdejnha taħt Żid ruoli . Biex tnaddaf rol, ikklikkja l-buttuna minus (-)  ħdejnha taħt Ruoli attwali , jew ikklikkja l-buttuna ×  fuq rol assenjat ħdejn isem il-membru.

-

Fuq il-paġna Ruoli , agħżel rol u ftħ il-tab Members  tiegħu. Ikklikkja l-buttuna Add members  biex tfittxija għal membri tal-grupp u tassignahom lir-rol. Biex tnaddaf membru, ikklikkja l-buttuna minus (-)  fil-fond tar-row tagħhom.

### [Neħħi membru](#neħħi-membru)[](#neħħi-membru)

Biex tnaddaf membru mill-grupp, ikklikkja l-buttuna ⋮  fil-fond tar-row tagħhom, agħżel Kick user , u kkonferma l-azzjoni.

## [Immaniġġa l-pagamenti](#immaniġġa-l-pagamenti)[](#immaniġġa-l-pagamenti)

Jekk int il-proprjetar tal-grupp jew għandek il-permess korrett [permissjoni](#ruoli-u-permessi)  fi Dħul tal-Grupp , issib paġna Pagamenti  taħt Finanzi  fil-nav ta' fuq. Hawnhekk, tista' tibgħat pagamenti waħedin, kif ukoll tiddefinixxi splittings ta' percentwali ma' membri oħra.

Xi gruppi jistgħu ma jkollhomx din il-paġna miftuħa inizjalment għal diversi raġunijiet, bħal l-età tal-grupp jew fondi insuffiċjenti biex jagħtu pagamenti.

Il-pagamenti ma jistgħux jiġu mqassma bejn il-membri tal-grupp għal logħob li jħallsu għall-[aċċess imħallas fil-munita lokali](/docs/en-us/production/monetization/paid-access-local-currency) .

### [Pagamenti waħedin](#pagamenti-waħedin)[](#pagamenti-waħedin)

Pagamenti waħedin jistgħu jsiru lil membri f'batċ, billi tagħżel ammont sett għal kull wieħed. Il-karatteristiċi ta' sigurtà jinkludu sfidi 2FA, dialogi ta' kkonferma, u kontrolli madwar l-eligibbiltà tal-membri li qed jiġu mħallsa.

 ![Il-buttuna ta' pagament waħdieni indikat fil-parti tal-Pagamenti fuq il-Creator Dashboard.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-One-Time.png)

Ladarba ikklikkja l-buttuna Send Robux , tista' tagħżel ir-reċipjenti tal-pagament mill-popup jew tgħaqqad fajl ta' spreadsheet .csv  bil-kolonni userId  u payoutInRobux , pereżempju:

| userId | | payoutInRobux |
| 012345 | | 5000 |
| 098765 | | 7000 |

### [Pagamenti ripetuti](#pagamenti-ripetuti)[](#pagamenti-ripetuti)

Pagamenti ripetuti jistgħu jsiru wkoll madwar il-grupp kollu u  għal kull logħba, billi tassigna pagament ta' percentwali lil kull membru qabel il-bqija tidħol fil-bilanċ ġenerali tal-grupp.

 ![Il-buttuni ta' pagamenti mqassma indikat fil-parti tal-Pagamenti fuq il-Creator Dashboard.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Split-Options.png)

Ikkunsidra s-sena li ġejja fejn logħba tal-grupp Laser Maze  hija mqassma 40%–30%–10% bejn tliet membri, bil-bqija ta' 20%.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-A.png)

Assumendo li l-logħba tagħmel 1000 Robux, it-tliet membri jirċievu 400, 300, u 100 Robux rispettivament (40%–30%–10%).

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-B.png)

Il-bqija ta' 200 Robux (20% tal-qsim tal-logħba) tgħaddi 'l quddiem għall-percentwali ta' qsim tal-grupp , definiti f'20%–20%–10% bejn l-istess tliet membri; jirċievu 40, 40, u 20 Robux rispettivament.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-C.png)

Il-bqija ta' 100 Robux (50% tal-qsim tal-grupp) tiġi mqiegħda fil-bilanċ ġenerali tal-grupp.

 ![Eżempju ta' fluss ta' kif il-qsim tal-logħba jitqassam lill-membri tal-grupp l-ewwel, bil-bqija li tidħol fil-qsim tal-grupp għall-aħħar distribuzzjoni bejn il-grupp.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Splits-Example.png)

Innota li l-profitti mill-abbonamenti [server privat](/docs/en-us/production/monetization/private-servers)  ma jinbidlux jekk tbiddel il-percentwali ta' qsim f'waqtu aktar tard, li jfisser li jekk plejer jixtri abbonament ta' server privat, il-percentwali ta' qsim fil-ħin tal-xiri se japplika għal dak l-abbonament partikolarment għal dejjem (sakemm jiġi kkanċellat). Din il-politika tista' tiġi mibdula fil-futur.

## [Logs ta' audit tal-grupp](#logs-ta-audit-tal-grupp)[](#logs-ta-audit-tal-grupp)

Il-membri tal-grupp li għandhom il-permess View audit logs  jistgħu jirrevedu bidliet fil-grupp billi jużaw dawn il-pjanijiet ta' immaniġġjar tal-grupp:

-

Fuq il-Creator Dashboard, agħżel Storia tal-Attività  taħt Kollaborazzjoni .

-

Fuq il-Komunitajiet, ftħ il-paġna tal-konfigurazzjoni tal-komunità u agħżel Audit Log .

Il-proprjetar tal-grupp jistgħu jużaw dawn il-logs biex jissorveljaw l-attività li tista' tikser [linji gwida tal-grupp](/docs/en-us/projects/group-guidelines) .

## [Protezzjoni tal-proprjetà intellettwali](#protezzjoni-tal-proprjetà-intellettwali)[](#protezzjoni-tal-proprjetà-intellettwali)

Il-membri tal-grupp li għandhom permess biex jeditjaw il-logħob kollu tal-grupp jistgħu jattivaw l-impostazzjoni [Kopja tal-Post](/docs/en-us/projects/configure-games#allow-copying)  għal kreazzjoni, li potenzjalment jippermetti lill-komunità kollha ta' Roblox li tikkopjaha u tuża l-assi fiha. Biex jgħin fil-protezzjoni tal-proprjetà intellettwali f'grupp, il-proprjetar jew il-membri bi permessi biżżejjed għandhom:

-

Ikkonferma li kull membru huwa [assegnat ir-ruol xieraq](#immani%C4%A1%C4%A1a-r-ruoli) .

-

Iċċekkja li kull rol tal-grupp għandu l-[permsi](#ruoli-u-permessi)  korretti.

-

Ikkonferma li l-impostazzjoni [Kopja tal-Post](/docs/en-us/projects/configure-games#allow-copying)  hija diżattivata qabel ma jiġu miżjuda assi privati.

## [Lokalizzazzjonijiet addizzjonali għal din il-paġna](#lokalizzazzjonijiet-addizzjonali-għal-din-il-paġna)[](#lokalizzazzjonijiet-addizzjonali-għal-din-il-paġna)

Għal verżjonijiet lokalizzati addizzjonali ta' din il-paġna li mhumiex disponibbli fil-pick ta' lingwa tas-sit, ara l-links li ġejjin:

-

[Bulgarian (български)](https://create.roblox.com/docs/bg-bg/projects/groups)

-

[Croatian (hrvatski)](https://create.roblox.com/docs/hr-hr/projects/groups)

-

[Czech (čeština)](https://create.roblox.com/docs/cs-cz/projects/groups)

-

[Danish (dansk)](https://create.roblox.com/docs/da-dk/projects/groups)

-

[Dutch (Nederlands)](https://create.roblox.com/docs/nl-nl/projects/groups)

-

[Estonian (eesti)](https://create.roblox.com/docs/et-ee/projects/groups)

-

[Finnish (suomi)](https://create.roblox.com/docs/fi-fi/projects/groups)

-

[Greek (Ελληνικά)](https://create.roblox.com/docs/el-gr/projects/groups)

-

[Hungarian (magyar)](https://create.roblox.com/docs/hu-hu/projects/groups)

-

[Irish (Gaeilge)](https://create.roblox.com/docs/ga-ie/projects/groups)

-

[Latvian (latviešu)](https://create.roblox.com/docs/lv-lv/projects/groups)

-

[Lithuanian (lietuvių)](https://create.roblox.com/docs/lt-lt/projects/groups)

-

[Maltese (Malti)](https://create.roblox.com/docs/mt-mt/projects/groups)

-

[Portuguese - Portugal (português)](https://create.roblox.com/docs/pt-pt/projects/groups)

-

[Romanian (română)](https://create.roblox.com/docs/ro-ro/projects/groups)

-

[Slovak (slovenčina)](https://create.roblox.com/docs/sk-sk/projects/groups)

-

[Slovenian (slovenščina)](https://create.roblox.com/docs/sl-si/projects/groups)

-

[Swedish (svenska)](https://create.roblox.com/docs/sv-se/projects/groups)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
