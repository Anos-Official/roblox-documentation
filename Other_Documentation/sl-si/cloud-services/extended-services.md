<!-- Source: https://create.roblox.com/docs/sl-si/cloud-services/extended-services -->

Razširjene storitve | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Cloud services](/docs/en-us/cloud-services/data-stores-vs-memory-stores)

# Razširjene storitve

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Razširjene storitve so rešitev, ki vam omogoča upravljanje uporabe storitev in plačil preko privzetih omejitev Robloxa. Vključuje podatkovne skladišče, pomnilniška skladišča, pretvorbo besedila v govor, pretvorbo govora v besedilo in računske zmogljivosti.

## [Zahteve za upravičenost](#zahteve-za-upravičenost)[](#zahteve-za-upravičenost)

Za uporabo razširjenih storitev mora biti vaš Roblox račun:

-

[Potrjen z ID-jem](/docs/en-us/production/publishing/account-verification#verify-through-government-id)  in star 18 let ali več.

-

Nahajati se v [podprti državi](#podprte-dr%C5%BEave) .

-

Imeti veljaven e-poštni naslov, povezan z njim.

-

Ne sme biti trenutno prepovedan ali moderiran.

-

Sprejeti in se držati [pogojev storitve](https://en.help.roblox.com/hc/articles/37967848292500) .

Za skupinske račune mora izpolniti zahteve za upravičenost le lastnik skupine.

## [Odkleni razširjene storitve](#odkleni-razširjene-storitve)[](#odkleni-razširjene-storitve)

Če izpolnjujete vse [zahteve za upravičenost](#zahteve-za-upravi%C4%8Denost) , lahko dokončate nastavitev razširjenih storitev tako, da vnesete podatke o svojem računu in plačilne informacije. Za igre, ki jih lasti skupina, lahko razširjene storitve odklenete in igro nanje vključi le lastnik skupine.

Za odklepanje in uporabo razširjenih storitev:

1.

V [Upravitelju ustvarjalcev](https://create.roblox.com/dashboard/creations)  pojdite na Ustvarjanje  in izberite igro.

2.

Pojdite na Razširjene storitve .

3.

Če še niste vnesli podatkov o svojem računu in plačilnih informacijah, kliknite Dodajte manjkajoče informacije  na zgornji pasici.

1.

Vnesite informacije o svojem računu. Polja Vrsta računa , Vrsta davčnega ID  in Davčni ID  so neobvezna.

-

Prav tako lahko greste na Finance  ⟩ Informacije o računu  v razdelku Razširjene storitve , da upravljate svoje informacije o računu. Na tej strani ni potrebno posodobiti ničesar drugega.

2.

Kliknite Naprej .

3.

Vnesite način plačila. Vnesete lahko nov način plačila ali izberete med razpoložljivimi plačilnimi možnostmi, ki so že povezane z vašim Roblox računom.

-

Prav tako lahko greste na Finance  ⟩ Plačila , da dodate nove načine plačila, ali pa greste na Finance  ⟩ Računanje , da nastavite nov privzeti način plačila.

4.

Kliknite Shrani .

##### Status računa

Vaš račun za razširjene storitve je lahko v enem od naslednjih statusov:

| Status | | Opis | | Zahtevana akcija |
| Normalno | | Vse funkcije razširjenih storitev lahko uporabljate. | | Ni potrebna nobena akcija. |
| --- | --- |
| Zapadlo | | Vaš račun je zapadel, ker je vaš avtomatski način plačila spodletel. Roblox ponuja prehodno obdobje sedmih dni  pred suspendiranjem vašega računa za razširjene storitve. | | Spremenite svoj način plačila in poskusite ponovno ročno plačilo ali počakajte, da Roblox ponovno poskusi zaračunati vaš način plačila po koncu prehodnega obdobja. |
| Suspendirano | | Ne morete uporabljati nobenih plačanih razširjenih storitev. Vendar pa lahko še vedno uporabljate storitve s privzetimi omejitvami. | | Odpravite svoje zahteve za upravičenost, dodajte veljaven način plačila ali ročno poravnajte zapadlo stanje na svojem računu. |

## [Omogočite storitev](#omogočite-storitev)[](#omogočite-storitev)

Za omogočanje storitve:

1.

Pojdite na Razširjene storitve .

2.

Preklopite na storitev, ki jo želite omogočiti.

3.

Vnesite mesečni proračun za vsak ustrezen vir pod storitvijo. Najmanjši mesečni proračun, ki ga lahko nastavite, je 0,50 USD.

Vaš način plačila se zaračuna bodisi na koncu meseca, ko je izdan račun, bodisi, ko vaša uporaba doseže 10 USD, kar pride prej.

Kadar koli lahko povečate ali zmanjšate mesečni proračun storitve. Vaša storitev se samodejno omeji, če zmanjšate proračun na znesek, ki je nižji od vaše trenutne uporabe do danes, ali če presežete proračun, ki ste ga nastavili.

Roblox vas obvesti po e-pošti, ko vaša uporaba doseže 80 % vašega proračuna, in nato še enkrat, ko doseže 100 %.

### [Razširjene storitve za računske zmogljivosti](#razširjene-storitve-za-računske-zmogljivosti)[](#razširjene-storitve-za-računske-zmogljivosti)

Vsak strežnik igre dobi privzeto količino CPU, ki se povečuje s vsakim igralcem, ki se pridruži. Razširjene storitve za računske zmogljivosti  več kot podvojijo CPU na igralca, ki ga prejmejo strežniki vaše igre.

Večina iger na Robloxu ne vidi koristi od te storitve, vendar igre z intenzivno fiziko na strežniku ali tiste, ki obsežno uporabljajo [avtoriteto strežnika](/docs/en-us/projects/server-authority) , naletijo na obstoječe omejitve. Da vidite, ali lahko vaša igra koristi od razširjenih storitev za računske zmogljivosti :

-

Preverite [srčni utrip strežnika](/docs/en-us/performance-optimization/identify#server-compute)  za vztrajne padce pod 60 FPS.

-

Preverite izkoriščenost CPU jeder na [Nadzorni plošči zmogljivosti](/docs/en-us/production/analytics/performance#server-charts) .

Preden plačate za več CPU, poskusite [zmanjšati delo, ki ga opravljajo vaši strežniki](/docs/en-us/performance-optimization/improve) .

## [Upravljanje obračunavanja](#upravljanje-obračunavanja)[](#upravljanje-obračunavanja)

Za dostop do nadzorne plošče obračunavanja razširjenih storitev:

1.

Pojdite na Finance  ⟩ Računanje .

2.

Izberite zavihek Oblačne storitve , da prikažete naslednje:

-

Vaše neporavnano stanje, vključno s stroški do danes

-

Vaša zgodovina obračunavanja, vključno z vsemi aktivnostmi obračunavanja razširjenih storitev v vaših igrah

Za podroben pregled stroškov vašega trenutnega neporavnanega stanja kliknite Poglej podrobnosti  poleg vašega načina plačila. Za podroben račun prejšnjega računa kliknite Poglej račun  pod Zgodovina obračunavanja .

## [Cene storitev](#cene-storitev)[](#cene-storitev)

Oglejte si naslednjo tabelo za cene razširjenih storitev:

| Storitev | |  | | Privzeto | | Razširjeno |
| [Pomnilniška skladišča](https://create.roblox.com/docs/cloud-services/memory-stores) | | Zahteve | | 1000 + (CCU × 120) zahtev na minuto | | $0.003 / 1M zahtev |
|  | | Shranjevanje | | 64 KB + (CCU × 1.2 KB) | | $0.10 / GB na uro¹ |
| [Pretvorba besedila v govor](https://create.roblox.com/docs/audio/objects#text-to-speech) | | Zahteve | | 1 + (CCU × 6) zahtev na minuto | | $5.00 / 1M zahtev |
| [Pretvorba govora v besedilo](https://create.roblox.com/docs/audio/objects#speech-to-text) | | Zahteve | | 1 + (CCU × 5) zahtev na minuto | | $1 / 1M zahtev |
| [Standardna podatkovna skladišča](https://create.roblox.com/docs/cloud-services/data-stores) | | Pridobi | | 250 + (CCU * 40) zahtev na minuto | | $0.08 / 1M zahtev |
|  | | Nastavi | | 250 + (CCU * 20) zahtev na minuto | | $0.80 / 1M zahtev |
|  | | Seznam | | 10 + (CCU * 2) zahtev na minuto | | $0.60 / 1M zahtev |
|  | | Odstrani | | 100 + (CCU * 40) zahtev na minuto | | $0.80 / 1M zahtev |
| [Urejena podatkovna skladišča ](https://create.roblox.com/docs/cloud-services/data-stores) | | Pridobi | | 250 + (CCU * 40) zahtev na minuto | | $0.08 / 1M zahtev |
|  | | Nastavi | | 250 + (CCU * 20) zahtev na minuto | | $0.25 / 1M zahtev |
|  | | GetSorted | | 100 + (CCU * 2) zahtev na minuto | | $0.32 / 1M zahtev |
|  | | Odstrani | | 100 + (CCU * 40) zahtev na minuto | | $0.25 / 1M zahtev |
| [Shranjevanje podatkovnih skladišč ](https://create.roblox.com/docs/cloud-services/data-stores) | | Shranjevanje | | 100 MB + (1 MB * Igralci v življenjski dobi) GB na mesec | | $0.12 / GB na mesec |
| [Računanje ](https://create.roblox.com/docs/production/analytics/performance) | | CPU jedra | | Prvih 100K ur igranja na mesec brezplačno (ko ste vpisani v razširjene storitve za računske zmogljivosti) | | $0.001 / ura igranja² |

 ¹ GB na uro = poraba shranjevanja pomnožena s časom. Na primer, 100 GB ur bi lahko pomenilo "100 GB × 1 ura" ali "200 GB × 0.5 ur".  ² Razširjene storitve za računske zmogljivosti se obračunavajo glede na to, kako dolgo ostane funkcija omogočena, merjeno v minutah igranja. Ker omogočanje funkcije rezervira dodatno računsko kapaciteto za vašo igro, se stroški obračunavajo, kadar koli je funkcija aktivna, tudi če dodatno računsko zmogljivost ni popolnoma porabljena. Ure igranja se izračunajo kot vsota vseh trajanj sej igralcev. Na primer, če 10.000 uporabnikov igra vsako po 1 uro, to pomeni 10.000 ur igranja, kar pomeni 10 USD stroškov poleg vključenega mesečnega dovoljenja 100.000 ur igranja. Te omejitve in cene veljajo le za igre, ki so vpisane v razširjene storitve za računske zmogljivosti. Igre, ki se ne vpišejo, še naprej prejemajo neomejene ure igranja pod trenutnimi privzetimi omejitvami brez dodatnih stroškov.

## [Podprte države](#podprte-države)[](#podprte-države)

Razširjene storitve so na voljo v naslednjih državah:

| Država |
| Avstralija | | Nemčija | | Poljska |
| Avstrija | | Hongkong | | Portugalska |
| Belgija | | Madžarska | | Romunija |
| Brazil | | Irska | | Singapur |
| Bolgarska | | Italija | | Slovaška |
| Kanada | | Kazahstan | | Slovenija |
| Čile | | Latvija | | Južna Afrika |
| Kroacija | | Litvanija | | Južna Koreja |
| Ciper | | Malezija | | Španija |
| Češka | | Malta | | Švedska |
| Danska | | Mehika | | Švica |
| Estonija | | Nizozemska | | Tajska |
| Finska | | Nova Zelandija | | Združeno kraljestvo |
| Francija | | Norveška | | Združene države |
| Gruzija | | Peru | |  |

## [Dodatne lokalizacije za to stran](#dodatne-lokalizacije-za-to-stran)[](#dodatne-lokalizacije-za-to-stran)

Za dodatne, lokalizirane različice te strani, ki niso na voljo v izbiri jezika na spletnem mestu, si oglejte naslednje povezave:

-

[Bolgarščina (български)](https://create.roblox.com/docs/bg-bg/cloud-services/extended-services)

-

[Hrvaščina (hrvatski)](https://create.roblox.com/docs/hr-hr/cloud-services/extended-services)

-

[Češčina (čeština)](https://create.roblox.com/docs/cs-cz/cloud-services/extended-services)

-

[Danščina (dansk)](https://create.roblox.com/docs/da-dk/cloud-services/extended-services)

-

[Nizozemščina (Nederlands)](https://create.roblox.com/docs/nl-nl/cloud-services/extended-services)

-

[Estonščina (eesti)](https://create.roblox.com/docs/et-ee/cloud-services/extended-services)

-

[Finščina (suomi)](https://create.roblox.com/docs/fi-fi/cloud-services/extended-services)

-

[Grščina (Ελληνικά)](https://create.roblox.com/docs/el-gr/cloud-services/extended-services)

-

[Madžarščina (magyar)](https://create.roblox.com/docs/hu-hu/cloud-services/extended-services)

-

[Irščina (Gaeilge)](https://create.roblox.com/docs/ga-ie/cloud-services/extended-services)

-

[Latvijščina (latviešu)](https://create.roblox.com/docs/lv-lv/cloud-services/extended-services)

-

[Litvanščina (lietuvių)](https://create.roblox.com/docs/lt-lt/cloud-services/extended-services)

-

[Malteščina (Malti)](https://create.roblox.com/docs/mt-mt/cloud-services/extended-services)

-

[Portugalščina - Portugalska (português)](https://create.roblox.com/docs/pt-pt/cloud-services/extended-services)

-

[Romunščina (română)](https://create.roblox.com/docs/ro-ro/cloud-services/extended-services)

-

[Slovaščina (slovenčina)](https://create.roblox.com/docs/sk-sk/cloud-services/extended-services)

-

[Slovenščina (slovenščina)](https://create.roblox.com/docs/sl-si/cloud-services/extended-services)

-

[Švedščina (svenska)](https://create.roblox.com/docs/sv-se/cloud-services/extended-services)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
