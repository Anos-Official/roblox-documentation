<!-- Source: https://create.roblox.com/docs/ga-ie/production/monetization -->

Monetú | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)

# Monetú

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Is é Monetú cuid de struchtúr iomlán Roblox chun luach a sholáthar do chruthaitheoirí. Tá roinnt bealaí éagsúla ann chun do chontae a mhonatóireacht, lena n-áirítear úsáid a bhaint as [suibscríbhinní](#suibscr%C3%ADbhinn%C3%AD) , táille rochtana a ghearradh i [Robux](#rochtain-%C3%ADoctha-i-robux)  nó [airgeadra áitiúil](#rochtain-%C3%ADoctha-i-airgeadra-%C3%A1iti%C3%BAil) , [rudaí nó cumais a sholáthar a féidir le húsáideoirí a cheannach](#t%C3%A1irg%C3%AD-forbr%C3%B3ir%C3%AD) , [freastal ar shócmhainní príobháideacha](#seirbh%C3%ADs%C3%AD-pr%C3%ADobh%C3%A1ideacha)  do dhaoine chun imirt le cairde amháin, agus [móidí agus breiseanna a dhíol](/docs/en-us/production/creator-store#distribute-and-sell-assets)  le cruthaitheoirí eile ar an gCruthaitheoir Siopa.

Má roghnaíonn tú ábhar a thairiscint le ceannach, ní dhéanann Roblox taifead ar fhaisnéis táirge nó ceannach go huathoibríoch. Chun cosc a chur ar chaillteanas sonraí, caithfidh tú an fhaisnéis seo a stóráil go cúramach ag baint úsáide as [DataStoreService](/docs/en-us/reference/engine/classes/DataStoreService)  nó seirbhís stórála sonraí eile a óstáil lasmuigh de Roblox.

Chun breathnú domhain ar dhearadh straitéisí monetú optamacha do do thaithí, féach [bunús monetú](/docs/en-us/production/game-design/monetization-foundations) .

## [Straitéisí Monetú](#straitéisí-monetú)[](#straitéisí-monetú)

Bí cúramach leis na modhanna monetú a thugann tú isteach i do chluiche mar is dócha go díscaoilfidh  ár n-úsáideoirí do chluiche má tá siad míshásta le do straitéisí. Chomh maith leis sin, ní mór do gach forbróir a bheith trédhearcach le haon [monetú bunaithe ar sheans](/docs/en-us/production/monetization/paid-random-items)  agus ba chóir na meicníochtaí seo a úsáid go freagrach.

Níl roinnt straitéisí monetú coitianta do chluichí saor in aisce ar ardáin eile molta do Roblox. Mar shampla, d'fhéadfadh meicníochtaí ceapacháin agus ama a d'fhéadfadh a bheith bainte nó a thabhairt chun cinn a bheith oiriúnach ar ardáin eile, ach tá na meicníochtaí seo neamhshásta le húsáideoirí Roblox a bhíonn ag gearán faoi a n-áthas ag teacht chun críche roimh am.

Tá na moltaí cleachtais is fearr seo coitianta i measc na forbróirí barr chun straitéisí monetú a oiriúnú don ardán agus don lucht féachana Roblox.

Tabhair faoi deara, le do thoil, go bhfuil tú nach bhfuil ráthaithe go mbeidh tú in ann do chluiche a mhonatóireacht go héifeachtach trí na teicnící agus na breithnithe seo a chur i bhfeidhm. Cuimhnigh nach gá duit a bheith ag súil le haon sprioc airgeadais chun taitneamh a bhaint as cruthú cluiche Roblox.

### [Turasóirí agus áitigh](#turasóirí-agus-áitigh)[](#turasóirí-agus-áitigh)

D'fhéadfadh sé a bheith cabhrach smaoineamh ar úsáideoirí Roblox i dhá chatagóir:

-

Turasóirí  go ginearálta a chuaigh ó chluiche go cluiche, ag cur tosaíochta ar éagsúlacht thar doimhneacht. Is fearr leo rudaí le héifeachtaí láithreach, bíodh sé trí chluiche a dhéanamh níos taitneamhaí nó trí iad a dhéanamh chun seasamh amach, ag tabhairt cuireadh do dhaoine eile a cheistiú conas agus cá háit a fuair siad an rud.

-

Áitigh  is dócha go gcuirfidh siad a n-aird ar chluiche ar leith nó ar shraith níos lú cluichí. Déanann siad níos doimhne, agus go ginearálta foirmíonn siad beagnach an t-aon úsáideoir gníomhach atá ag imirt an chluiche. Tá suim níos mó acu i rudaí le sochair fhadtéarmacha, mar shampla [pas comhoibrithe](/docs/en-us/production/game-design/season-pass-design) .

Chun tuilleadh a fhoghlaim faoi conas do chluiche a dhearadh le húsáideoirí Roblox i gcuimhne, féach [Déan do Roblox](/docs/en-us/production/game-design/design-for-roblox) .

### [Gnéithe sóisialta](#gnéithe-sóisialta)[](#gnéithe-sóisialta)

Is maith le húsáideoirí Roblox cluichí a chuireann béim ar idirghníomhú sóisialta. Mar shampla, d'fhéadfadh rudaí nó imeachtaí a bheith ar fáil ach le haghaidh ama teoranta  a chruthú spreagadh timpeall ar an ábhar sin. Cruthaíonn córas trádála  deis do dhaoine idirghníomhú. Cé go bhfuil an dá chóras rathúil ar a n-aon, tá siad go háirithe éifeachtach nuair a chomhcheanglaítear iad.

### [Oibríochtaí beo](#oibríochtaí-beo)[](#oibríochtaí-beo)

Is éard atá i dtaca le tacaíocht tar éis seoladh i go leor bealaí níos éasca ar Roblox ná ar ardáin eile mar is féidir leat nuashonruithe a sheoladh go tapa chun do chluiche a fheabhsú.

Is féidir le nuashonruithe ábhar minic  a bheith cabhrach más mian leat gníomhacht a chothabháil le do chluiche thar am. Tá úsáideoirí Roblox gnáthaithe le bheith gníomhachtaithe ag nuashonruithe rialta, agus is féidir go mbeadh sé i bhfad níos deacra suim úsáideora a fháil ar ais ná mar atá sé chun gníomhacht a chothabháil. Is é cadence seachtainiúil  do nuashonruithe an rud is fearr. Ar a laghad, déan iarracht nuashonruithe míosúla a bhaint amach. Le haghaidh plé ar cadence ábhar, féach ar an [ceardlann cadence ábhar](/docs/en-us/production/game-design/content-updates) .

Nuair a bhíonn tú ag dearadh nuashonruithe, coinnigh iad dírithe ar téama  ar leith. Éascaíonn sé do dhaoine tuiscint a fháil ar an nuashonrú nua agus a thuiscint cad é an t-ábhar nua nuair a théann siad isteach. Cuireann sé ar do chumas freisin do shócmhainní ábhair agus cur chun cinn a chomhordú. Mar shampla, má tá tú ag cur Zú nua le do chluiche ról, déan cinnte go bhfuil gach ábhar nua nasctha leis an téama Zú.

Ná bíodh eagla ort na húsáideoirí a dhéanamh chun a rochtain  a fháil ar ábhar nua. Tiocfaidh úsáideoirí nua chun imirt nuashonruithe nua, ach más rud é nach mbraitheann siad go bhfuil gnóthachtáil  déanta acu i gcluiche, d'fhéadfadh siad a bheith ag dul ar shiúl go luath ina dhiaidh sin. Is féidir leat mothú a chruthú go bhfuil nuashonrú tuillte acu trí ábhar nuashonraithe a mhonatóireacht nó trí choinníollacha réamhchúraim a chruthú le haghaidh imirt an ábhair nua.

Chun tuilleadh a fhoghlaim faoi conas tacaíocht éifeachtach tar éis seoladh a dhearadh do do chluiche, féach [bunghnéithe oibríochtaí beo](/docs/en-us/production/game-design/liveops-essentials) .

## [Táirgí](#táirgí)[](#táirgí)

### [Fógraí tumtha](#fógraí-tumtha)[](#fógraí-tumtha)

Ligeann an córas [fógraí tumtha](/docs/en-us/production/monetization/immersive-ads)  duit aonad fógraíochta a chur isteach i do chluiche a cheadaíonn do Roblox ábhar fógraíochta a sheirbheáil go cliste ó fhógraíocht chuig do úsáideoirí gníomhacha.

![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/Overview-ImageAd.jpg) Formáid fógra íomhá

Formáid fógra dorais

### [Roblox Plus](#roblox-plus)[](#roblox-plus)

Ligeann [Roblox Plus](/docs/en-us/production/monetization/roblox-plus)  duit a thuilleamh trí cheannacháin in-game a mhéadú a dhéantar trí lascainí úsáideora a subsidized ag Roblox, bónais sínithe do gach síntiúsóir nua a thugann tú isteach, agus gníomhacht i seirbhísí príobháideacha íoctha.

### [Suibscríbhinní](#suibscríbhinní)[](#suibscríbhinní)

Ligeann [suibscríbhinní](/docs/en-us/production/monetization/subscriptions)  laistigh de chluichí duit tairiscint a dhéanamh do dhaoine le sochair athchóirithe ar tháille mhíosúil.

![](https://prod.docsiteassets.roblox.com/assets/monetization/subscriptions/Example-Subscriptions.png) Samplaí de shuibscríbhinní cluichí

### [Pasanna](#pasanna)[](#pasanna)

Ligeann [pas](/docs/en-us/production/monetization/passes)  duit táille Robux aon-uaire  a ghearradh ar úsáideoirí chun rochtain a fháil ar phribhléidí speisialta laistigh de chluiche, mar shampla rochtain ar limistéar srianta, mír avatar in-game, nó cumhacht buan.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/passes/passes-sample.png)

### [Táirgí Forbróirí](#táirgí-forbróirí)[](#táirgí-forbróirí)

Is mír nó cumas é [táirge forbróra](/docs/en-us/production/monetization/developer-products)  a féidir le húsáideoir a cheannach níos mó ná uair amháin, mar shampla airgead in-game, ammo, nó potaí. Is féidir leat ceannacháin a spreagadh, iad a thaifeadadh, agus faisnéis táirge a fháil trí scripting.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/developer-products/Buy-Product-Example.jpg)

### [Praghsáil bhainistithe](#praghsáil-bhainistithe)[](#praghsáil-bhainistithe)

Is córas comhoibrithe é [praghsáil bhainistithe](/docs/en-us/production/monetization/managed-pricing)  a thugann [praghsáil réigiúnach](/docs/en-us/production/monetization/regional-pricing)  agus [optamú praghsanna](/docs/en-us/production/monetization/price-optimization)  le chéile in aon áit amháin. Roghnaíonn tú a bheith páirteach uair amháin, roghnaíonn tú na míreanna le cur isteach, agus coimeádann praghsáil bhainistithe do phraghsanna optamaithe trasna táirgí agus réigiún thar am.

### [Optamú praghsanna](#optamú-praghsanna)[](#optamú-praghsanna)

Ligeann [optamú praghsanna](/docs/en-us/production/monetization/price-optimization)  duit na pointí praghsanna is fearr a fháil do do phasanna agus táirgí forbróirí, rud a chabhróidh leat níos mó airgid a thuilleamh thar am agus do phraghsanna a choinneáil iomaíoch.

### [Rochtain íoctha i Robux](#rochtain-íoctha-i-robux)[](#rochtain-íoctha-i-robux)

Ligeann [rochtain íoctha i Robux](/docs/en-us/production/monetization/paid-access-robux)  duit táille Robux aon-uaire  a ghearradh ar úsáideoirí chun rochtain a fháil ar do chluiche. Úsáideann roinnt forbróirí an gné seo go sealadach chun béite dúnta a chruthú áit a bhfuil a n-úsáideoirí is gníomhachtaí in ann rochtain luath a fháil ar chluiche agus cabhrú le tástáil agus aiseolas.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/paid-access/Buy-Access-Example.png)

### [Rochtain íoctha i airgeadra áitiúil](#rochtain-íoctha-i-airgeadra-áitiúil)[](#rochtain-íoctha-i-airgeadra-áitiúil)

Ligeann [rochtain íoctha i airgeadra áitiúil](/docs/en-us/production/monetization/paid-access-local-currency)  duit táille aon-uaire i n-airgeadra áitiúil  a ghearradh ar úsáideoirí chun rochtain a fháil ar do chluiche. Má tá a n-airgeadra áitiúil ar fáil, gheobhaidh siad íoc i USD. Úsáideann roinnt forbróirí an gné seo go sealadach chun béite dúnta a chruthú áit a bhfuil a n-úsáideoirí is gníomhachtaí in ann rochtain luath a fháil ar chluiche agus cabhrú le tástáil agus aiseolas.

### [Seirbhísí príobháideacha](#seirbhísí-príobháideacha)[](#seirbhísí-príobháideacha)

Is gné bunaithe ar shuíomh é [seirbhís phríobháideach](/docs/en-us/production/monetization/private-servers)  a ligeann do úsáideoir a chinneadh cé a d'fhéadfadh imirt cluiche leo. Cé go bhfuil seirbhísí príobháideacha saor in aisce, is féidir leat seirbhísí príobháideacha a úsáid mar mhodh monetú trí táille Robux mhíosúil  a ghearradh ar úsáideoirí a theastaíonn uathu rochtain a fháil ar sheirbhísí príobháideacha.

### [Táillí agus coimisiúin catagóirí](#táillí-agus-coimisiúin-catagóirí)[](#táillí-agus-coimisiúin-catagóirí)

Is féidir leat rochtain a chruthú agus éadaí a dhíol ar an Margadh. Tar éis duit an táille uaslódála a íoc agus sócmhainn nua a chur isteach le haghaidh cead, déanann an foireann modhnóireachta athbhreithniú ar do shócmhainn agus, más ceadaithe, cuireann siad do shócmhainn leis an gcatagóir.

Gheobhaidh tú [coimisiún](/docs/en-us/marketplace/marketplace-fees-and-commissions)  gach uair a cheannaíonn úsáideoirí do shócmhainní catagóra. Má cheannaíonn úsáideoirí do shócmhainní catagóra laistigh de chluiche ag baint úsáide as an [mearghearrthóir avatar](/docs/en-us/players/avatar-inspect-menu)  nó an [seirbhís eagarthóra avatar](/docs/en-us/players/avatar-editor) , faigheann an t-úinéir cluiche coimisiún freisin.

### [Breiseanna agus Móidí](#breiseanna-agus-móidí)[](#breiseanna-agus-móidí)

Is síneadh é [breiseán](/docs/en-us/studio/plugins)  a chuireann feidhmeanna breise le Studio, agus is cineál sócmhainne inúsáidte é [móid](/docs/en-us/parts/models) . Is féidir leat an dá rud a thairiscint do chruthaitheoirí eile ar an [Cruthaitheoir Siopa](/docs/en-us/production/creator-store)  saor in aisce, nó is féidir leat iad a dhíol ar Dollar na Stát Aontaithe  (is é an praghas íosta $4.99 do bhreiseanna agus $2.99 do mhóidí). Tairgeann Roblox comhoibriú iontach maidir le hioncam as na díolacháin seo, mar níl ach cáin agus táillí próiseála íocaíochta á gcur as. Le haghaidh tuilleadh faisnéise ar dhíol breiseanna agus móidí, féach [Cruthaitheoir Siopa - Dáilte agus díol sócmhainní](/docs/en-us/production/creator-store#distribute-and-sell-assets) .

Tá hold escrow 30 lá ar gach ceannach. Coimeádann Roblox do chuid scaireanna díola ar feadh 30 lá, ag tosú ón dáta díola.

## [Treoirlínte](#treoirlínte)[](#treoirlínte)

De réir mar a dhearann tú agus a chuireann tú táirgí monetú i bhfeidhm i do chluichí, smaoinigh ar na treoirlínte seo a chinntiú go bhfuil do mhodhanna monetú oiriúnach do gach lucht féachana ar an ardán.

### [Ag cur táirgí i láthair](#ag-cur-táirgí-i-láthair)[](#ag-cur-táirgí-i-láthair)

Chun sábháilteacht agus cothroime a chothabháil, caithfidh tú táirgí monetú a chur i láthair ar bhealach atá trédhearcach, macánta, agus atá éasca le húsáid. Mar shampla, má thairgeann tú lascainí, caithfidh siad a bheith fíor  agus cothrom :

-

Ní hé lascaine fíor é má tá mír i gcónaí "ar díol" don méid céanna Robux.

-

Ní hé lascaine cothrom é má tá sé ar fáil ach ar feadh tréimhse an-ghearr, ag brú úsáideoirí chun ceannach a dhéanamh chomh tapa agus is féidir.

Ní mór do dhaoine a bheith míthreoraithe, mearbhall, nó brúite chun ceannach a dhéanamh ar bhealaí nach raibh siad ag súil leo, agus ba chóir dóibh i gcónaí a bheith saor chun cinneadh soiléir, d'aon toil a dhéanamh chun síntiús a fháil nó Robux a chaitheamh ar mhír ar leith. Mar threoir ginearálta, tá roinnt cleachtais le sheachaint i gcónaí nuair a bhíonn tú ag cur táirgí monetú i láthair do do lucht féachana:

-

Ná bíodh tú ag éileamh go bhfuil síntiús nó mír beagnach as stoc nó ar fáil ach ar feadh tréimhse ghearr más rud é nach bhfuil sé fíor.

-

Ná bain úsáid as uaireadóirí comhoibrithe nach bhfuil cruinn nó a athosclaíonn go huathoibríoch don mhír chéanna.

Mar shampla, má tá do chluiche ag cur "conradh an lae" a deir go bhfuil sé ar fáil ach ar feadh 24 uair an chloig, ach ansin taispeánann tú an teachtaireacht chéanna do dhaoine gach uair a logálann siad isteach agus ní stopann sé riamh a bheith ar fáil, tá tú tar éis mothú bréagach éigeandála a chruthú nach bhfuil éasca le húsáid.

### [Ag cur chun cinn do lucht féachana domhanda](#ag-cur-chun-cinn-do-lucht-féachana-domhanda)[](#ag-cur-chun-cinn-do-lucht-féachana-domhanda)

Is pobal domhanda é Roblox do dhaoine de gach aois, mar sin ba chóir go mbeadh cur chun cinn laistigh de do chluichí oiriúnach do gach lucht féachana de réir réamhshocraithe. Má tá táirgí monetú áirithe srianta i suíomhanna áirithe, mar shampla rudaí randamacha íoctha, soláthraíonn Roblox [PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  API chun cabhrú leat a chinntiú go bhfuil na táirgí sin infheicthe do dhaoine atá incháilithe amháin.

Tugann [PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  ar ais an bhfuil úsáideoir incháilithe do shócmhainní nó gnéithe ar leith de réir a suíomh, a aois, agus a ardán. Caithfidh tú an API seo a chomhtháthú i do chluiche chun freastal ar do dhualgais comhoiriúnachta, lena n-áirítear a chinneadh an bhfuil gach úsáideoir:

-

Incháilithe chun síntiúis nó táirgí trádála a cheannach.

-

Ceadaithe rudaí randamacha íoctha, trádáil rudaí íoctha, nó fógraí tumtha a fheiceáil.

Má tá úsáideoir in ann Robux nó rud éigin eile a fuarthas le Robux a úsáid chun duais randamach a fháil, tá tú éigeantaigh [PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  a úsáid chun an gné seo a bhac do dhaoine nach bhfuil cead acu rudaí randamacha a úsáid in éadan Robux.

Mar threoir ginearalta, seachain úsáid a bhaint as teachtaireachtaí brúidiúla nó éigeandála nuair a bhíonn tú ag idirghníomhú le leanaí, mar is féidir le teanga ard brú a bheith ró-throm:

| ** Teanga le sheachaint** | | ** Comhoiriúnachtaí molta** |
| --- | --- |
| "GHEOBHAIM É ANOIS" | | "Féach ar Mhír" |
| "DEIREADH DEIREADH, Gníomhú ANOIS" | | "Féach ar Praghas" |
| "CEANNAIGH SULA NÍL É GONE!" | | "Oscail Siopa" |

## [Leaganacha áitiúla breise don leathanach seo](#leaganacha-áitiúla-breise-don-leathanach-seo)[](#leaganacha-áitiúla-breise-don-leathanach-seo)

Chun leaganacha áitiúla breise den leathanach seo nach bhfuil ar fáil i bpicking teanga an láithreáin, féach na naisc seo a leanas:

-

[Bulgarian (български)](https://create.roblox.com/docs/bg-bg/production/monetization)

-

[Croatian (hrvatski)](https://create.roblox.com/docs/hr-hr/production/monetization)

-

[Czech (čeština)](https://create.roblox.com/docs/cs-cz/production/monetization)

-

[Danish (dansk)](https://create.roblox.com/docs/da-dk/production/monetization)

-

[Dutch (Nederlands)](https://create.roblox.com/docs/nl-nl/production/monetization)

-

[Estonian (eesti)](https://create.roblox.com/docs/et-ee/production/monetization)

-

[Finnish (suomi)](https://create.roblox.com/docs/fi-fi/production/monetization)

-

[Greek (Ελληνικά)](https://create.roblox.com/docs/el-gr/production/monetization)

-

[Hungarian (magyar)](https://create.roblox.com/docs/hu-hu/production/monetization)

-

[Irish (Gaeilge)](https://create.roblox.com/docs/ga-ie/production/monetization)

-

[Latvian (latviešu)](https://create.roblox.com/docs/lv-lv/production/monetization)

-

[Lithuanian (lietuvių)](https://create.roblox.com/docs/lt-lt/production/monetization)

-

[Maltese (Malti)](https://create.roblox.com/docs/mt-mt/production/monetization)

-

[Portuguese - Portugal (português)](https://create.roblox.com/docs/pt-pt/production/monetization)

-

[Romanian (română)](https://create.roblox.com/docs/ro-ro/production/monetization)

-

[Slovak (slovenčina)](https://create.roblox.com/docs/sk-sk/production/monetization)

-

[Slovenian (slovenščina)](https://create.roblox.com/docs/sl-si/production/monetization)

-

[Swedish (svenska)](https://create.roblox.com/docs/sv-se/production/monetization)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
