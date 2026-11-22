<!-- Source: https://create.roblox.com/docs/hu-hu/production/monetization -->

Monetizáció | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)

# Monetizáció

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

A monetizáció a Roblox általános struktúrájának része, amely értéket biztosít a készítők számára. Számos különböző megközelítést alkalmazhatsz a tartalmad monetizálására, beleértve az [előfizetéseket](#el%C5%91fizet%C3%A9sek) , a [Robux](#fizetett-hozz%C3%A1f%C3%A9r%C3%A9s-robuxban)  vagy [helyi valuta](#fizetett-hozz%C3%A1f%C3%A9r%C3%A9s-helyi-valut%C3%A1ban)  alapú belépési díj beszedését, [vásárolható elemek vagy képességek biztosítását](#fejleszt%C5%91i-term%C3%A9kek) , [privát szerverek](#priv%C3%A1t-szerverek)  ajánlását, ahol a felhasználók csak barátaikkal játszhatnak, és [modellek és pluginek értékesítését](/docs/en-us/production/creator-store#distribute-and-sell-assets)  más készítőknek a Creator Store-on.

Ha úgy döntesz, hogy vásárolható tartalmat kínálsz, a Roblox nem rögzíti automatikusan a termék- vagy vásárlási információkat. Az adatok elvesztésének elkerülése érdekében gondosan kell tárolnod ezeket az adatokat a [DataStoreService](/docs/en-us/reference/engine/classes/DataStoreService)  vagy egy másik, a Robloxon kívül hosztolt adatkezelő szolgáltatás segítségével.

A monetizációs stratégiák optimális tervezéséről részletesebben lásd a [Monetizációs alapok](/docs/en-us/production/game-design/monetization-foundations)  című dokumentumot.

## [Monetizációs stratégiák](#monetizációs-stratégiák)[](#monetizációs-stratégiák)

Legyél tudatában a monetizációs módszereknek, amelyeket a játékodba bevezetsz, mivel a felhasználóink valószínűleg leértékelik  a játékodat, ha nem hagyják jóvá a stratégiáidat. Ezenkívül minden fejlesztőnek átláthatónak kell lennie a [véletlenszerű monetizációval](/docs/en-us/production/monetization/paid-random-items)  kapcsolatban, és ezeket a mechanikákat felelősségteljesen kell használni.

Néhány népszerű monetizációs stratégia, amely más platformokon a szabadon játszható játékok számára ajánlott, nem javasolt a Robloxon. Például az időpont-mechanikák és időzítők, amelyeket el lehet távolítani vagy előre lehet hozni, jól működhetnek más platformokon, de ezek a mechanikák népszerűtlenek a Roblox felhasználói körében, akik problémát látnak abban, hogy a szórakozásuk korán véget ér.

Az alábbi legjobb gyakorlatok javasoltak a legjobb fejlesztők körében a monetizációs stratégiák Roblox platformra és közönségre való szabásához.

Kérjük, vedd figyelembe, hogy ezeknek a technikáknak és megfontolásoknak az alkalmazásával nem garantált, hogy hatékonyan monetizálni tudod a játékodat. Ne feledd, hogy nem szükséges pénzügyi célokat kitűzni ahhoz, hogy élvezd a Roblox játék készítését.

### [Turisták és helyiek](#turisták-és-helyiek)[](#turisták-és-helyiek)

Hasznos lehet a Roblox felhasználóit két kategóriába sorolni:

-

Turisták  általában egyik játékról a másikra ugrálnak, a változatosságot előnyben részesítve a mélységgel szemben. Olyan elemeket preferálnak, amelyek azonnali hatással bírnak, akár a játékmenet szórakoztatóbbá tételével, akár azzal, hogy kiemelkednek, és más felhasználókat arra ösztönöznek, hogy kérdezzék, hogyan és hol szerezték az elemet.

-

Helyiek  valószínűbb, hogy egy adott játékra vagy kisebb játékok halmazára összpontosítanak. Mélyebben elköteleződnek, és jellemzően a játék aktív felhasználói bázisának szinte minden tagját alkotják. Ők inkább a hosszú távú előnyökkel járó elemek iránt érdeklődnek, mint például egy [battlepasse](/docs/en-us/production/game-design/season-pass-design) .

Ha többet szeretnél megtudni arról, hogyan tervezd meg a játékodat a Roblox felhasználóinak figyelembevételével, lásd a [Tervezés a Roblox számára](/docs/en-us/production/game-design/design-for-roblox)  című dokumentumot.

### [Szociális funkciók](#szociális-funkciók)[](#szociális-funkciók)

A Roblox felhasználói általában olyan játékokat kedvelnek, amelyek hangsúlyozzák a társadalmi interakciót. Például, ha olyan elemeket vagy eseményeket kínálsz, amelyek csak korlátozott ideig  érhetők el, az izgalmat kelthet a tartalom körül. Egy kereskedelmi  rendszer ösztönzi a felhasználókat az interakcióra. Míg mindkét rendszer önállóan sikeres lehet, különösen hatékonyak, ha kombinálják őket.

### [Élő üzemeltetés](#élő-üzemeltetés)[](#élő-üzemeltetés)

A megjelenés utáni támogatás sok szempontból könnyebb a Robloxon, mint más platformokon, mivel gyorsan frissítéseket küldhetsz a játékod javítása érdekében.

Gyakori  tartalomfrissítések hasznosak lehetnek, ha szeretnéd fenntartani a játékod iránti elköteleződést az idő múlásával. A Roblox felhasználói hozzászoktak a rendszeres frissítésekhez, és sokkal nehezebb visszanyerni egy felhasználó érdeklődését, mint fenntartani az aktív érdeklődést. Az ideális frissítési ütemterv a heti . A legkevesebb, amit célul tűzhetsz ki, a havi frissítések. A tartalom ütemezéséről a Level Up [tartalom ütemezési workshop](/docs/en-us/production/game-design/content-updates)  című dokumentumában olvashatsz.

A frissítések tervezésekor tartsd őket egy adott téma  köré összpontosítva. Ez megkönnyíti a felhasználók számára az új frissítés megértését és annak megállapítását, hogy mi az új tartalom, amikor csatlakoznak. Ez segít a tartalom és a promóciós eszközök koordinálásában is. Például, ha új állatkertet adsz hozzá a szerepjátékodhoz, győződj meg róla, hogy minden új tartalomnak van valamilyen kapcsolata az állatkert témájával.

Ne félj attól, hogy a felhasználóknak meg kell érdemelniük  az új tartalomhoz való hozzáférést . Az új felhasználók tömegesen fognak játszani az új frissítésekkel, de ha nem érzik úgy, hogy elértek  valamit a játékban, lehet, hogy hamarosan távoznak. Az új frissítés megérdemelt érzését úgy hozhatod létre, hogy monetizálod a frissítési tartalmat, vagy előfeltételeket állítasz fel az új tartalom játszásához.

Ha többet szeretnél megtudni arról, hogyan tervezd meg a hatékony megjelenés utáni támogatást a játékodhoz, lásd a [Élő üzemeltetés alapjai](/docs/en-us/production/game-design/liveops-essentials)  című dokumentumot.

## [Termékek](#termékek)[](#termékek)

### [Immersív hirdetések](#immersív-hirdetések)[](#immersív-hirdetések)

Az [immersív hirdetések](/docs/en-us/production/monetization/immersive-ads)  rendszere lehetővé teszi, hogy hirdetési egységeket illessz a játékodba, amelyek lehetővé teszik a Roblox számára, hogy programozottan hirdetési tartalmat szolgáltasson a hirdetőktől az aktív felhasználóid számára.

![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/Overview-ImageAd.jpg) Kép hirdetés formátum

Portál hirdetés formátum

### [Roblox Plus](#roblox-plus)[](#roblox-plus)

A [Roblox Plus](/docs/en-us/production/monetization/roblox-plus)  lehetővé teszi, hogy a Roblox által támogatott felhasználói kedvezmények, az új előfizetők után járó regisztrációs bónuszok és a fizetett privát szerverekben való részvétel révén növeld a játékbeli vásárlásaidat.

### [Előfizetések](#előfizetések)[](#előfizetések)

A játékokban elérhető [előfizetések](/docs/en-us/production/monetization/subscriptions)  lehetővé teszik, hogy a felhasználóknak havi díjért folyamatos előnyöket kínálj.

![](https://prod.docsiteassets.roblox.com/assets/monetization/subscriptions/Example-Subscriptions.png) Példák játék előfizetésekre

### [Belépők](#belépők)[](#belépők)

A [belépő](/docs/en-us/production/monetization/passes)  lehetővé teszi, hogy egyszeri Robux díjat  számíts fel a felhasználóknak, hogy hozzáférjenek a játékban különleges privilégiumokhoz, például egy korlátozott területhez való belépéshez, egy játékbeli avatar elemhez vagy egy állandó erősítéshez.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/passes/passes-sample.png)

### [Fejlesztői termékek](#fejlesztői-termékek)[](#fejlesztői-termékek)

A [fejlesztői termék](/docs/en-us/production/monetization/developer-products)  olyan elem vagy képesség, amelyet a felhasználó többször is megvásárolhat, például játékbeli valuta, lőszer vagy italok. Vásárlásokat kezdeményezhetsz, rögzítheted őket, és termékinformációkat kaphatsz szkriptek segítségével.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/developer-products/Buy-Product-Example.jpg)

### [Kezelt árképzés](#kezelt-árképzés)[](#kezelt-árképzés)

A [kezelt árképzés](/docs/en-us/production/monetization/managed-pricing)  egy egységes rendszer, amely a [regionális árképzést](/docs/en-us/production/monetization/regional-pricing)  és az [ároptimalizálást](/docs/en-us/production/monetization/price-optimization)  egy helyen egyesíti. Egyszer kell bejelentkezned, ki kell választanod, hogy mely elemeket szeretnéd belefoglalni, és a kezelt árképzés folyamatosan optimalizálja az áraikat a termékek és régiók között.

### [Ároptimalizálás](#ároptimalizálás)[](#ároptimalizálás)

Az [ároptimalizálás](/docs/en-us/production/monetization/price-optimization)  lehetővé teszi, hogy megtaláld a legjobb árpontokat a belépőid és fejlesztői termékeid számára, ami segíthet, hogy idővel több pénzt keress, miközben az áraid versenyképesek maradnak.

### [Fizetett hozzáférés Robuxban](#fizetett-hozzáférés-robuxban)[](#fizetett-hozzáférés-robuxban)

A [fizetett hozzáférés Robuxban](/docs/en-us/production/monetization/paid-access-robux)  lehetővé teszi, hogy egyszeri Robux díjat  számíts fel a felhasználóknak a játékodhoz való hozzáférésért. Néhány fejlesztő ideiglenesen használja ezt a funkciót, hogy zárt bétát hozzon létre, ahol a legelkötelezettebb felhasználóik korai hozzáférést kapnak a játékhoz, és segítenek a tesztelésben és a visszajelzésben.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/paid-access/Buy-Access-Example.png)

### [Fizetett hozzáférés helyi valutában](#fizetett-hozzáférés-helyi-valutában)[](#fizetett-hozzáférés-helyi-valutában)

A [fizetett hozzáférés helyi valutában](/docs/en-us/production/monetization/paid-access-local-currency)  lehetővé teszi, hogy egyszeri díjat számíts fel a felhasználóknak a helyi valutájukban  a játékodhoz való hozzáférésért. Ha a helyi valuta nem elérhető, akkor USD-ban számítják fel őket. Néhány fejlesztő ideiglenesen használja ezt a funkciót, hogy zárt bétát hozzon létre, ahol a legelkötelezettebb felhasználóik korai hozzáférést kapnak a játékhoz, és segítenek a tesztelésben és a visszajelzésben.

### [Privát szerverek](#privát-szerverek)[](#privát-szerverek)

A [privát szerver](/docs/en-us/production/monetization/private-servers)  egy előfizetés alapú funkció, amely lehetővé teszi a felhasználó számára, hogy eldöntse, ki játszhat a játékkal. Míg a privát szerverek ingyenesek lehetnek, a privát szerverek monetizálásának módszereként is használhatod őket, ha havi Robux díjat  számítasz fel a felhasználóknak, akik hozzá akarnak férni a privát szerverekhez.

### [Katalógus díjak és jutalékok](#katalógus-díjak-és-jutalékok)[](#katalógus-díjak-és-jutalékok)

Kiegészítőket és ruhákat hozhatsz létre és értékesíthetsz a Piacon. Miután kifizetted a feltöltési díjat és benyújtottál egy új eszközt jóváhagyásra, a moderáló csapat átnézi az eszközödet, és ha jóváhagyják, hozzáadják az eszközödet a katalógushoz.

Minden alkalommal, amikor a felhasználók megvásárolják a katalógus elemedet, [jutalékot](/docs/en-us/marketplace/marketplace-fees-and-commissions)  kapsz. Ha a felhasználók a játékban vásárolják meg a katalógus elemedet az [avatar ellenőrző menü](/docs/en-us/players/avatar-inspect-menu)  vagy az [avatar szerkesztő szolgáltatás](/docs/en-us/players/avatar-editor)  segítségével, a játék tulajdonosa is jutalékot kap.

### [Pluginek és modellek](#pluginek-és-modellek)[](#pluginek-és-modellek)

A [plugin](/docs/en-us/studio/plugins)  egy kiterjesztés, amely további funkciókat ad a Studiohoz, és egy [modell](/docs/en-us/parts/models)  egy újrahasználható eszköztípus. Mindkettőt ingyenesen kínálhatod más készítőknek a [Creator Store](/docs/en-us/production/creator-store)  platformon, vagy eladhatod őket amerikai dollárban  (a minimum ár $4.99 a pluginek és $2.99 a modellek esetében). A Roblox piacvezető bevételi részesedést kínál ezekből az értékesítésekből, mivel csak az adók és a fizetési feldolgozási díjak kerülnek levonásra. További információkért a pluginek és modellek értékesítéséről lásd a [Creator Store - Eszközök terjesztése és értékesítése](/docs/en-us/production/creator-store#distribute-and-sell-assets)  című dokumentumot.

Minden vásárlás esetén 30 napos letétkezelési időszak van. A Roblox 30 napig tartja a te részesedésedet az értékesítésből, az értékesítés dátumától kezdődően.

## [Irányelvek](#irányelvek)[](#irányelvek)

Amikor monetizációs termékeket tervezel és valósítasz meg a játékaidban, vedd figyelembe az alábbi irányelveket, hogy biztosítsd, hogy a monetizációs módszereid minden közönség számára megfelelőek legyenek a platformon.

### [Termékek bemutatása](#termékek-bemutatása)[](#termékek-bemutatása)

A biztonság és a méltányosság fenntartása érdekében a monetizációs termékeket átlátható, őszinte és felhasználóbarát módon kell bemutatnod. Például, ha kedvezményeket kínálsz, azoknak valódiaknak  és méltányosaknak  kell lenniük:

-

A kedvezmény nem valós, ha egy elem mindig "akciós" ugyanannyi Robuxért.

-

A kedvezmény nem méltányos, ha csak nagyon rövid ideig érhető el, nyomást gyakorolva a felhasználókra, hogy a lehető leggyorsabban vásároljanak.

A felhasználókat soha nem szabad félrevezetni, összezavarni vagy nyomás alá helyezni a vásárlások során, amelyeket nem szándékoztak, és mindig szabadon kell választaniuk, hogy világosan és szándékosan előfizetést szerezzenek vagy Robuxot költsenek egy adott elemre. Általános irányelvként van néhány gyakorlat, amelyet mindig el kell kerülni, amikor monetizációs termékeket mutatsz be a közönségednek:

-

Ne állítsd, hogy egy előfizetés vagy elem majdnem elfogyott, vagy csak rövid ideig elérhető, ha ez nem igaz.

-

Ne használj olyan visszaszámláló időzítőt, amely nem pontos vagy automatikusan újraindul ugyanarra az elemre.

Például, ha a játékod tartalmaz egy "nap ajánlatát", amely azt mondja, hogy csak 24 óráig érhető el, de aztán minden alkalommal megjeleníted ugyanazt az üzenetet a felhasználóknak, amikor bejelentkeznek, és soha nem áll le az elérhetősége, akkor hamis sürgősségérzetet keltettél, ami nem felhasználóbarát.

### [Promóció globális közönségek számára](#promóció-globális-közönségek-számára)[](#promóció-globális-közönségek-számára)

A Roblox egy globális közösség minden korosztály számára, így a játékodban végzett promócióknak alapértelmezés szerint minden közönség számára megfelelőnek kell lenniük. Ha bizonyos monetizációs termékek bizonyos helyeken korlátozottak, például a fizetett véletlenszerű elemek, a Roblox biztosítja a [PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  API-t, hogy segítsen biztosítani, hogy ezek a termékek csak az arra jogosult felhasználók számára legyenek láthatók.

A [PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  visszaadja, hogy egy felhasználó jogosult-e bizonyos elemekre vagy funkciókra a helyük, koruk és platformjuk szerint. Integrálnod kell ezt az API-t a játékodba, hogy megfelelj a megfelelőségi kötelezettségeidnek, beleértve annak meghatározását, hogy minden felhasználó:

-

Jogosult-e előfizetések vagy kereskedelmi termékek vásárlására.

-

Engedélyezett-e a fizetett véletlenszerű elemek, a fizetett elemkereskedelem, vagy hogy láthasson immersív hirdetéseket.

Ha egy felhasználó Robuxot vagy valami mást, amit Robuxért szereztek, használhat véletlenszerű jutalom megszerzésére, kötelező használni a [PolicyService](/docs/en-us/reference/engine/classes/PolicyService) -t, hogy blokkolja ezt a funkciót azok számára, akik nem jogosultak véletlenszerű elemek használatára Robuxért.

Általános irányelvként kerüld a nyomásgyakorló vagy sürgető üzenetek használatát, amikor kiskorúakkal lépsz kapcsolatba, mivel a nagy nyomású nyelvezet túlterhelő lehet:

| ** Kerülendő nyelvezet** | | ** Ajánlott alternatívák** |
| --- | --- |
| "SZEREZZE MEG MOST" | | "Elem megtekintése" |
| "UTOLSÓ LEHETŐSÉG, AZONNAL CSELEKEDJ" | | "Ár megtekintése" |
| "VÁSÁROLJON, MIELŐTT ELTŰNIK!" | | "Bolt megnyitása" |

## [További lokalizációk ezen az oldalon](#további-lokalizációk-ezen-az-oldalon)[](#további-lokalizációk-ezen-az-oldalon)

A webhely nyelvi választójában nem elérhető, további lokalizált verziókért lásd az alábbi linkeket:

-

[Bolgár (български)](https://create.roblox.com/docs/bg-bg/production/monetization)

-

[Horvát (hrvatski)](https://create.roblox.com/docs/hr-hr/production/monetization)

-

[Cseh (čeština)](https://create.roblox.com/docs/cs-cz/production/monetization)

-

[Dán (dansk)](https://create.roblox.com/docs/da-dk/production/monetization)

-

[Holland (Nederlands)](https://create.roblox.com/docs/nl-nl/production/monetization)

-

[Észt (eesti)](https://create.roblox.com/docs/et-ee/production/monetization)

-

[Finn (suomi)](https://create.roblox.com/docs/fi-fi/production/monetization)

-

[Görög (Ελληνικά)](https://create.roblox.com/docs/el-gr/production/monetization)

-

[Magyar (magyar)](https://create.roblox.com/docs/hu-hu/production/monetization)

-

[Ír (Gaeilge)](https://create.roblox.com/docs/ga-ie/production/monetization)

-

[Lett (latviešu)](https://create.roblox.com/docs/lv-lv/production/monetization)

-

[Litván (lietuvių)](https://create.roblox.com/docs/lt-lt/production/monetization)

-

[Máltai (Malti)](https://create.roblox.com/docs/mt-mt/production/monetization)

-

[Portugál - Portugália (português)](https://create.roblox.com/docs/pt-pt/production/monetization)

-

[Román (română)](https://create.roblox.com/docs/ro-ro/production/monetization)

-

[Szlovák (slovenčina)](https://create.roblox.com/docs/sk-sk/production/monetization)

-

[Szlovén (slovenščina)](https://create.roblox.com/docs/sl-si/production/monetization)

-

[Svéd (svenska)](https://create.roblox.com/docs/sv-se/production/monetization)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
