<!-- Source: https://create.roblox.com/docs/hu-hu/cloud-services/extended-services -->

Kiterjesztett Szolgáltatások | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Cloud services](/docs/en-us/cloud-services/data-stores-vs-memory-stores)

# Kiterjesztett Szolgáltatások

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

A Kiterjesztett Szolgáltatások egy olyan megoldás, amely lehetővé teszi a szolgáltatások használatának és a kifizetések kezelését a Roblox alapértelmezett korlátain túl. Tartalmaz adatboltokat, memória boltokat, szöveg-beszédet, beszéd-szöveget és számítást.

## [Jogosultsági követelmények](#jogosultsági-követelmények)[](#jogosultsági-követelmények)

A Kiterjesztett Szolgáltatások használatához a Roblox fiókjának:

-

[ID-ellenőrzött](/docs/en-us/production/publishing/account-verification#verify-through-government-id)  és 18 éves vagy annál idősebb kell legyen.

-

Olyan [támogatott országban](#t%C3%A1mogatott-orsz%C3%A1gok)  kell lennie.

-

Érvényes e-mail címnek kell társulnia hozzá.

-

Jelenleg nem lehet felfüggesztve vagy moderálva.

-

El kell fogadnia és be kell tartania a [szolgáltatási feltételeket](https://en.help.roblox.com/hc/articles/37967848292500) .

Csoportfiókok esetén csak a csoport tulajdonosának kell megfelelnie a jogosultsági követelményeknek.

## [Kiterjesztett Szolgáltatások feloldása](#kiterjesztett-szolgáltatások-feloldása)[](#kiterjesztett-szolgáltatások-feloldása)

Ha megfelel az összes [jogosultsági követelménynek](#jogosults%C3%A1gi-k%C3%B6vetelm%C3%A9nyek) , befejezheti a Kiterjesztett Szolgáltatások beállítását a fiókadatai és a fizetési információk megadásával. Csoport által birtokolt játékok esetén csak a csoport tulajdonosa tudja feloldani a Kiterjesztett Szolgáltatásokat és onboardolni a játékot.

A Kiterjesztett Szolgáltatások feloldásához és használatához:

1.

A [Creator Dashboard](https://create.roblox.com/dashboard/creations)  oldalon lépjen a Creations  fülre, és válasszon ki egy játékot.

2.

Lépjen a Kiterjesztett Szolgáltatások  fülre.

3.

Ha még nem adta meg a fiókadatait és a fizetési információkat, kattintson a Hiányzó információk hozzáadása  gombra a felső sávon.

1.

Adja meg a fiókadatait. A Fiók típusa , Adóazonosító típus  és Adóazonosító  mezők opcionálisak.

-

A Kiterjesztett Szolgáltatások  szakasz alatt a Finanszírozás  ⟩ Fiók információk  menüpont alatt is kezelheti a fiókadatait. Ezen az oldalon nem szükséges semmit másként frissíteni.

2.

Kattintson a Tovább  gombra.

3.

Adjon meg egy fizetési módot. Új fizetési módot adhat meg, vagy választhat a Roblox fiókjához már társított elérhető fizetési lehetőségek közül.

-

Új fizetési módok hozzáadásához lépjen a Finanszírozás  ⟩ Fizetések  menüpontra, vagy lépjen a Finanszírozás  ⟩ Számlázás  menüpontra, hogy új alapértelmezett fizetési módot állítson be.

4.

Kattintson a Mentés  gombra.

##### Fiók állapota

A Kiterjesztett Szolgáltatások fiókja az alábbi állapotok egyikében lehet:

| Állapot | | Leírás | | Szükséges intézkedés |
| Normál | | Az összes Kiterjesztett Szolgáltatás funkciót használhatja. | | Nincs szükség intézkedésre. |
| --- | --- |
| Késedelmes | | A fiókja késedelmes, mert az automatikus fizetési módja meghiúsult. A Roblox hét napos  türelmi időt biztosít, mielőtt felfüggesztené a Kiterjesztett Szolgáltatások fiókját. | | Változtassa meg a fizetési módját, és próbáljon meg manuális kifizetést, vagy várjon, amíg a Roblox újra megpróbálja terhelni a fizetési módját a türelmi időszak végén. |
| Felfüggesztett | | Nem használhat semmilyen fizetett Kiterjesztett Szolgáltatást. Azonban továbbra is használhatja a szolgáltatásokat az alapértelmezett korlátokkal. | | Javítsa ki a jogosultsági követelményeit, adjon hozzá érvényes fizetési módot, vagy fizesse ki manuálisan a fiókján lévő késedelmes egyenleget. |

## [Szolgáltatás engedélyezése](#szolgáltatás-engedélyezése)[](#szolgáltatás-engedélyezése)

Szolgáltatás engedélyezéséhez:

1.

Lépjen a Kiterjesztett Szolgáltatások  fülre.

2.

Kapcsolja be a szolgáltatást, amelyet engedélyezni szeretne.

3.

Adjon meg egy havi költségkeretet minden alkalmazható erőforrásra a szolgáltatáson belül. A beállítható minimális havi költségkeret $0.50 USD.

A fizetési módját a hónap végén terhelik, amikor a számla generálódik, vagy amikor a felhasználása eléri a $10 USD-t, attól függően, hogy mi történik előbb.

Bármikor növelheti vagy csökkentheti a szolgáltatás havi költségkeretét. A szolgáltatása automatikusan korlátozásra kerül, ha a költségkeretét a jelenlegi havi felhasználásánál alacsonyabb összegre csökkenti, vagy ha túllépi a beállított költségkeretet.

A Roblox e-mailben értesíti, amikor a felhasználása eléri a költségkeretének 80%-át, majd újra, amikor eléri a 100%-ot.

### [Kiterjesztett Szolgáltatások a Számításhoz](#kiterjesztett-szolgáltatások-a-számításhoz)[](#kiterjesztett-szolgáltatások-a-számításhoz)

Minden játék szerver alapértelmezett mennyiségű CPU-t kap, amely növekszik, ahogy egyre több játékos csatlakozik. A Kiterjesztett Szolgáltatások a Számításhoz  több mint kétszeresére növeli a játék szervereinek egy játékosra jutó CPU-ját.

A Robloxon található játékok túlnyomó többsége nem lát előnyt ebből a szolgáltatásból, de azok a játékok, amelyek nehéz szerveroldali fizikát használnak, vagy amelyek széleskörűen használják a [szerver hatáskört](/docs/en-us/projects/server-authority) , elérik a meglévő korlátokat. Annak megállapításához, hogy a játéka hasznot húzhat-e a Kiterjesztett Szolgáltatások a Számításhoz :

-

Ellenőrizze a [szerver szívverést](/docs/en-us/performance-optimization/identify#server-compute)  a 60 FPS alatti tartós csökkenésekhez.

-

Vizsgálja meg a CPU magok kihasználtságát a [Teljesítmény irányítópulton](/docs/en-us/production/analytics/performance#server-charts) .

Mielőtt többlet CPU-t fizetne, próbálja meg [csökkenteni a szerverek munkáját](/docs/en-us/performance-optimization/improve) .

## [Számlázás kezelése](#számlázás-kezelése)[](#számlázás-kezelése)

A Kiterjesztett Szolgáltatások számlázási irányítópultjának eléréséhez:

1.

Lépjen a Finanszírozás  ⟩ Számlázás  menüpontra.

2.

Válassza a Felhőszolgáltatások  fület, hogy megjelenítse a következőket:

-

A függő egyenlegét, beleértve a hónap eddigi költségét

-

A számlázási előzményeit, beleértve az összes Kiterjesztett Szolgáltatások számlázási tevékenységét a játékaiban

A jelenlegi függő egyenleg költségeinek részletes bontásához kattintson a Részletek megtekintése  gombra a fizetési módja mellett. Egy korábbi számla részletes számlájához kattintson a Számla megtekintése  gombra a Számlázási előzmények  alatt.

## [Szolgáltatás árképzés](#szolgáltatás-árképzés)[](#szolgáltatás-árképzés)

A Kiterjesztett Szolgáltatások árképzéséhez lásd az alábbi táblázatot:

| Szolgáltatás | |  | | Alapértelmezett | | Kiterjesztett |
| [Memória boltok](https://create.roblox.com/docs/cloud-services/memory-stores) | | Kérések | | 1000 + (CCU × 120) kérés percenként | | $0.003 / 1M kérés |
|  | | Tárolás | | 64 KB + (CCU × 1.2 KB) | | $0.10 / GB óránként¹ |
| [Szöveg-beszéd](https://create.roblox.com/docs/audio/objects#text-to-speech) | | Kérések | | 1 + (CCU × 6) kérés percenként | | $5.00 / 1M kérés |
| [Beszéd-szöveg](https://create.roblox.com/docs/audio/objects#speech-to-text) | | Kérések | | 1 + (CCU × 5) kérés percenként | | $1 / 1M kérés |
| [Standard adatboltok](https://create.roblox.com/docs/cloud-services/data-stores) | | Get | | 250 + (CCU * 40) kérés percenként | | $0.08 / 1M kérés |
|  | | Set | | 250 + (CCU * 20) kérés percenként | | $0.80 / 1M kérés |
|  | | List | | 10 + (CCU * 2) kérés percenként | | $0.60 / 1M kérés |
|  | | Remove | | 100 + (CCU * 40) kérés percenként | | $0.80 / 1M kérés |
| [Rendezett adatboltok ](https://create.roblox.com/docs/cloud-services/data-stores) | | Get | | 250 + (CCU * 40) kérés percenként | | $0.08 / 1M kérés |
|  | | Set | | 250 + (CCU * 20) kérés percenként | | $0.25 / 1M kérés |
|  | | GetSorted | | 100 + (CCU * 2) kérés percenként | | $0.32 / 1M kérés |
|  | | Remove | | 100 + (CCU * 40) kérés percenként | | $0.25 / 1M kérés |
| [Adatbolt tárolás ](https://create.roblox.com/docs/cloud-services/data-stores) | | Tárolás | | 100 MB + (1 MB * Életre szóló játékosok) GB havonta | | $0.12 / GB havonta |
| [Számítás ](https://create.roblox.com/docs/production/analytics/performance) | | CPU magok | | Az első 100K játékidő óra havonta díjmentes (ha be van iratkozva a Kiterjesztett Szolgáltatások a Számításhoz) | | $0.001 / játékidő óra² |

 ¹ GB óránként = a tárolási fogyasztás szorozva az időtartammal. Például, 100 GB óra lehet "100 GB × 1 óra" vagy "200 GB × 0.5 óra".  ² A Kiterjesztett Szolgáltatások a Számításhoz a funkció engedélyezésének időtartama alapján kerül számlázásra, amelyet a játékidő percekben mérnek. Mivel a funkció engedélyezése további számítási kapacitást tart fenn a játékához, díjak merülnek fel, amikor a funkció aktív, még akkor is, ha a további számítási kapacitás nincs teljesen kihasználva. A játékidő órák a játékosok összes session időtartamának összegét jelentik. Például, ha 10,000 felhasználó mindegyike 1 órát játszik, az 10,000 játékidő órát jelent, ami $10 díjat eredményez a 100,000 játékidő órás havi keret felett. Ezek a korlátok és árképzés csak a Kiterjesztett Szolgáltatások a Számításhoz beiratkozott játékokra vonatkoznak. Azok a játékok, amelyek nem iratkoznak be, továbbra is korlátlan játékidő órákat kapnak az aktuális alapértelmezett korlátok alatt, további díj nélkül.

## [Támogatott országok](#támogatott-országok)[](#támogatott-országok)

A Kiterjesztett Szolgáltatások az alábbi országokban érhetők el:

| Ország |
| Ausztrália | | Németország | | Lengyelország |
| Ausztria | | Hongkong | | Portugália |
| Belgium | | Magyarország | | Románia |
| Brazilia | | Írország | | Szingapúr |
| Bulgária | | Olaszország | | Szlovákia |
| Kanada | | Kazahsztán | | Szlovénia |
| Chile | | Letónia | | Dél-Afrika |
| Horvátország | | Lettország | | Délnyugat-Korea |
| Ciprus | | Malajzia | | Spanyolország |
| Csehország | | Málta | | Svédország |
| Dánia | | Mexikó | | Svájc |
| Észtország | | Hollandia | | Thaiföld |
| Finnország | | Új-Zéland | |  Egyesült Királyság |
| Franciaország | | Norvégia | |  Egyesült Államok |
| Grúzia | | Peru | |  |

## [További lokalizációk ezen az oldalon](#további-lokalizációk-ezen-az-oldalon)[](#további-lokalizációk-ezen-az-oldalon)

A webhely nyelvi választójában nem elérhető, további lokalizált verziókért lásd az alábbi linkeket:

-

[Bolgár (български)](https://create.roblox.com/docs/bg-bg/cloud-services/extended-services)

-

[Horvát (hrvatski)](https://create.roblox.com/docs/hr-hr/cloud-services/extended-services)

-

[Cseh (čeština)](https://create.roblox.com/docs/cs-cz/cloud-services/extended-services)

-

[Dán (dansk)](https://create.roblox.com/docs/da-dk/cloud-services/extended-services)

-

[Holland (Nederlands)](https://create.roblox.com/docs/nl-nl/cloud-services/extended-services)

-

[Észt (eesti)](https://create.roblox.com/docs/et-ee/cloud-services/extended-services)

-

[Finn (suomi)](https://create.roblox.com/docs/fi-fi/cloud-services/extended-services)

-

[Görög (Ελληνικά)](https://create.roblox.com/docs/el-gr/cloud-services/extended-services)

-

[Magyar (magyar)](https://create.roblox.com/docs/hu-hu/cloud-services/extended-services)

-

[Ír (Gaeilge)](https://create.roblox.com/docs/ga-ie/cloud-services/extended-services)

-

[Lett (latviešu)](https://create.roblox.com/docs/lv-lv/cloud-services/extended-services)

-

[Litván (lietuvių)](https://create.roblox.com/docs/lt-lt/cloud-services/extended-services)

-

[Máltai (Malti)](https://create.roblox.com/docs/mt-mt/cloud-services/extended-services)

-

[Portugál - Portugália (português)](https://create.roblox.com/docs/pt-pt/cloud-services/extended-services)

-

[Román (română)](https://create.roblox.com/docs/ro-ro/cloud-services/extended-services)

-

[Szlovák (slovenčina)](https://create.roblox.com/docs/sk-sk/cloud-services/extended-services)

-

[Szlovén (slovenščina)](https://create.roblox.com/docs/sl-si/cloud-services/extended-services)

-

[Svéd (svenska)](https://create.roblox.com/docs/sv-se/cloud-services/extended-services)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
