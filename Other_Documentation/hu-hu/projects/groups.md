<!-- Source: https://create.roblox.com/docs/hu-hu/projects/groups -->

Csoportok (csapatok) | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Projects](/docs/en-us/projects)
6. /
7. [Work in teams](/docs/en-us/projects/groups)

# Csoportok (csapatok)

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

A Roblox csoport  lehetővé teszi, hogy több alkotó dolgozzon ugyanazon a játékon, használja ugyanazokat az eszközöket, megossza a nyereséget, és elismerje az összes hozzájárulót.

A játékok csoportos tulajdonlása segíti az alkotókat az együttműködésben és független stúdióként való működésben. Ha konfliktus merül fel egy csoporton belül, a Roblox nem tud segíteni a viták közvetítésében vagy megoldásában.

## [Csoport létrehozása](#csoport-létrehozása)[](#csoport-létrehozása)

Egy csoport létrehozása 100 Robux-ba kerül. A csoport [szerepeit és engedélyeit](#szerepek-%C3%A9s-enged%C3%A9lyek)  a [Creator Dashboard](https://create.roblox.com/dashboard/creations)  vagy a [Közösségek](https://www.roblox.com/communities)  menüpontból kezelheti.

A csoport létrehozása előtt alaposan olvassa el a csoportkezelésre vonatkozó [szabályokat és elvárásokat](/docs/en-us/projects/group-guidelines) .

Új csoport létrehozásához:

1.

Navigáljon a [Creator Dashboard](https://create.roblox.com/dashboard/creations)  oldalra, bővítse ki a fiók váltót a bal felső sarokban, és kattintson a plusz (+)  gombra.

2.

A Csoport létrehozása  oldalon töltse fel a csoport logóját és adja meg a csoport nevét.

3.

Amikor készen áll, kattintson a Vásárlás  gombra. Miután a csoport létrejött, átirányítják a csoport profiloldalára, ahol módosíthatja a csoport részleteit, beleértve akár három közösségi link hozzáadását is.

## [Szerepek és engedélyek](#szerepek-és-engedélyek)[](#szerepek-és-engedélyek)

A csoport tagjai egy vagy több szerepet  kaphatnak a csoporton belül, és minden szerepnek engedélyei  vannak, amelyek meghatározzák a tagok képességeit.

A szerepkonfiguráció csak akkor érhető el, ha Ön a csoport tulajdonosa, vagy engedéllyel rendelkezik a csoport szerepeinek létrehozására, konfigurálására és hozzárendelésére.

A csoport szerepkiosztásának programozott kezelése érdekében a játék szerverről használja a [HttpService](/docs/en-us/reference/engine/classes/HttpService) -t a támogatott Open Cloud Groups végpontok hívásához. A beállításhoz és a példa kódhoz lásd: [Használat Open Cloud-dal](/docs/en-us/cloud-services/http-service#use-with-open-cloud) .

1.

A [Creator Dashboard](https://create.roblox.com/dashboard/creations)  oldalról bővítse ki a fiók váltót a bal felső sarokban, és válassza ki a csoportot.

2.

Ismét bővítse ki a fiók váltót, és válassza a Szerepek  lehetőséget.

3.

Minden szerep esetében gondosan erősítse meg az engedélyeket a Permissions  fül alatt.

Az engedélyek a General , Creation  és Community  kategóriákba vannak rendezve. Az alábbi szakaszok leírják az egyes kategóriákban elérhető engedélyeket.

### [Általános](#általános)[](#általános)

Általános engedélyek

| Manage roles | | Az ezzel az engedéllyel rendelkező tagok létrehozhatják, szerkeszthetik, törölhetik, átrendezhetik és hozzárendelhetik vagy eltávolíthatják a szerepeket a legmagasabb szerepük alatt. Csak azokat az engedélyeket szerkeszthetik, amelyeket már birtokolnak. |
| --- | --- |
| Assign or remove roles from members | | Az ezzel az engedéllyel rendelkező tagok bármely tagnak hozzárendelhetik vagy eltávolíthatják a legmagasabb szerepük alatti szerepeket. |
| Invite or approve members | | Az ezzel az engedéllyel rendelkező tagok meghívhatják az embereket a csoportba és jóváhagyhatják a csatlakozási kérelmeket. |
| Kick members | | Az ezzel az engedéllyel rendelkező tagok eltávolíthatják azokat a tagokat, akiknek a legmagasabb szerepe alacsonyabb, mint a sajátjuk. |
| Ban members | | Az ezzel az engedéllyel rendelkező tagok kitilthatják azokat a tagokat, akiknek a legmagasabb szerepe alacsonyabb, mint a sajátjuk. |
| Configure group profile | | Az ezzel az engedéllyel rendelkező tagok konfigurálhatják a csoport profilját. |
| View audit logs | | Az ezzel az engedéllyel rendelkező tagok megtekinthetik a [csoport audit naplóit](#csoport-audit-napl%C3%B3k) . |
| Manage allies and enemies | | Az ezzel az engedéllyel rendelkező tagok kezelhetik a csoport szövetségeseit és ellenségeit. |

### [Létrehozás](#létrehozás)[](#létrehozás)

Creations

| Playtest experiences | | Az ezzel a szereppel rendelkező tagok játszhatnak a csoport által birtokolt összes játékkal, még akkor is, ha azok nincsenek szélesebb közönség számára kiadva. Opcionálisan elérhető [játékonkénti engedélyként](/docs/en-us/projects/configure-games) . |
| Edit experiences | | Az ezzel a szereppel rendelkező tagok szerkeszthetik a csoport által birtokolt összes játékot és [eszközt](/docs/en-us/projects/assets) , és használhatják az összes funkciót a [Data Stores Manager](/docs/en-us/cloud-services/data-stores/data-stores-manager)  alkalmazásban. Nem tartalmazza a játék szerkesztését egy [együttműködési](/docs/en-us/projects/collaboration)  munkamenet során, vagy egy hely mentését az egyik játékból a másikba. Opcionálisan elérhető [játékonkénti engedélyként](/docs/en-us/projects/configure-games) . |
| Publish experiences | | Az ezzel a szereppel rendelkező tagok szerkeszthetik a játékokat, mint fent, és kiadhatják a játékokat a Robloxra. Opcionálisan elérhető [játékonkénti engedélyként](/docs/en-us/projects/configure-games) . |
| Manage share links | | Az ezzel a szereppel rendelkező tagok létrehozhatják/konfigurálhatják a [megosztási linkeket](/docs/en-us/production/promotion/share-links) . |
| Manage experience events | | Az ezzel a szereppel rendelkező tagok létrehozhatják/konfigurálhatják a [tapasztalati eseményeket](/docs/en-us/production/promotion/experience-events) . |
| Moderate experiences | | Az ezzel a szereppel rendelkező tagok megtekinthetik az összes játékbeli chat üzenetet (csak olvasható; a tagnak 18 évesnek kell lennie), és kitilthatják vagy kezelhetik a kitiltott felhasználókat a csoport által birtokolt összes játékban. |
| Manage monetization for experiences | | Az ezzel a szereppel rendelkező tagok kezelhetik a monetizációs termékeket, például a [bérleteket](/docs/en-us/production/monetization/passes) , [fejlesztői termékeket](/docs/en-us/production/monetization/developer-products) , [előfizetéseket](/docs/en-us/production/monetization/subscriptions)  és még sok mást. Opcionálisan elérhető [játékonkénti engedélyként](/docs/en-us/projects/configure-games) . |
| Manage secrets for experiences | | Az ezzel a szereppel rendelkező tagok láthatják a [titkok](/docs/en-us/cloud-services/secrets)  listáját, és létrehozhatják, frissíthetik és törölhetik a titkokat a csoport által birtokolt összes játékhoz. Az ezzel a szereppel rendelkező tagoknak Edit experiences  engedéllyel kell rendelkezniük a Titkok oldal megtekintéséhez. Opcionálisan elérhető [játékonkénti engedélyként](/docs/en-us/projects/configure-games) . |

Analytics

| View analytics for experiences | | Az ezzel a szereppel rendelkező tagok hozzáférhetnek a csoport által birtokolt összes játék [analitikájához](/docs/en-us/production/analytics) , még akkor is, ha nincs szerkesztési hozzáférésük. Opcionálisan elérhető [játékonkénti engedélyként](/docs/en-us/projects/configure-games) . |
| Manage alerts | | Az ezzel a szereppel rendelkező tagok létrehozhatják és kezelhetik az analitikai riasztásokat. Párosítsa ezt az engedélyt a View analytics for experiences  engedéllyel, hogy közvetlenül láthassa a riasztási annotációkat a metrikák grafikonjain. |

Monetization

| View group revenue | | Az ezzel a szereppel rendelkező tagok megtekinthetik a csoport Robux egyenlegét, a beállított rendszeres kifizetéseket és a bevételi naplózási funkciókat. |
| Manage and spend group revenue | | Az ezzel a szereppel rendelkező tagok megtekinthetik az összes csoportbevétele, mint fent, és közvetlenül kezelhetik azt. Ez magában foglalja a [rendszeres kifizetések](#rendszeres-kifizet%C3%A9sek)  beállítását és a [egyszeri kifizetések](#egyszeri-kifizet%C3%A9sek)  küldését az együttműködőknek. |
| Create ad campaigns for the group | | Az ezzel a szereppel rendelkező tagok hirdethetik a csoportot. |

Avatar items

| Create avatar items | | Az ezzel a szereppel rendelkező tagok létrehozhatnak avatar elemeket, például ruházatot. |
| Configure avatar items | | Az ezzel a szereppel rendelkező tagok konfigurálhatják az értékesítési részleteket, a készletezést és a szponzorálásokat a meglévő csoport avatar elemekhez. |

API

| Manage API keys | | Az ezzel a szereppel rendelkező tagok kezelhetik a csoport [Open Cloud API kulcsait](/docs/en-us/cloud/auth/api-keys) . |

Development items

| View development items | | Az ezzel a szereppel rendelkező tagok megtekinthetik a csoport által birtokolt fejlesztési elemeket, például Audio . |
| Manage development items | | Az ezzel a szereppel rendelkező tagok feltölthetik és konfigurálhatják az eszközfejlesztési elemeket, például Decals . |
| Manage development item permissions | | Az ezzel a szereppel rendelkező tagok konfigurálhatják a fejlesztési elemek engedélyeit, például az audio megosztást. |

Data Stores

| View Data Stores for experiences | | Az ezzel a szereppel rendelkező tagok megtekinthetik az összes csoportjáték adatboltját a [Data Stores Manager](/docs/en-us/cloud-services/data-stores/data-stores-manager)  alkalmazáson keresztül, de nem törölhetnek adatokat. Opcionálisan elérhető [játékonkénti engedélyként](/docs/en-us/projects/configure-games) . |
| Edit Data Stores for experiences | | Az ezzel a szereppel rendelkező tagok törölhetnek konkrét kulcsokat az adatboltokból az összes csoportjáték esetében a [Data Stores Manager](/docs/en-us/cloud-services/data-stores/data-stores-manager)  alkalmazáson keresztül. Opcionálisan elérhető [játékonkénti engedélyként](/docs/en-us/projects/configure-games) . |
| Delete Data Stores for experiences | | Az ezzel a szereppel rendelkező tagok törölhetik az egész adatboltot az összes csoportjáték esetében a [Data Stores Manager](/docs/en-us/cloud-services/data-stores/data-stores-manager)  alkalmazáson keresztül. Opcionálisan elérhető [játékonkénti engedélyként](/docs/en-us/projects/configure-games) . |

Notifications

| Manage webhooks for experiences | | Az ezzel a szereppel rendelkező tagok listázhatják, létrehozhatják, frissíthetik és törölhetik a webhorgokat az összes csoportélményhez. |

Communication

| Manage support tickets for experiences | | Az ezzel a szereppel rendelkező tagok kezelhetik a támogatási jegyeket az összes csoportélményhez. |

Legacy

| A csoport erőforrásaihoz való hozzáférés kezelése | | Az ezzel a szereppel rendelkező tagok létrehozhatják és szerkeszthetik a csoport erőforrásaihoz való hozzáférést. |

### [Közösség](#közösség)[](#közösség)

Posts

| View community announcements | | Az ezzel a szereppel rendelkező tagok megtekinthetik a közösségi bejelentéseket. |
| Create community announcements | | Az ezzel a szereppel rendelkező tagok létrehozhatják a közösségi bejelentéseket. |

Forums

| Manage categories | | Az ezzel a szereppel rendelkező tagok kezelhetik a fórum kategóriákat. |
| Create posts | | Az ezzel a szereppel rendelkező tagok létrehozhatják a fórum bejegyzéseket. |
| Remove posts | | Az ezzel a szereppel rendelkező tagok eltávolíthatják a fórum bejegyzéseket. |
| Lock posts | | Az ezzel a szereppel rendelkező tagok lezárhatják a fórum bejegyzéseket. |
| Pin posts | | Az ezzel a szereppel rendelkező tagok rögzíthetik a fórum bejegyzéseket. |
| Create comments | | Az ezzel a szereppel rendelkező tagok létrehozhatnak megjegyzéseket a fórum bejegyzéseken. |
| Remove comments | | Az ezzel a szereppel rendelkező tagok eltávolíthatják a megjegyzéseket a fórum bejegyzésekről. |

Content moderation

| View content moderation | | Az ezzel a szereppel rendelkező tagok megtekinthetik a tartalom moderálását. |
| Manage content moderation | | Az ezzel a szereppel rendelkező tagok kezelhetik a tartalom moderálását. |

Miscellaneous

| Bypass slow mode | | Az ezzel a szereppel rendelkező tagok megkerülhetik a lassú módot. |
| View community analytics | | Az ezzel a szereppel rendelkező tagok megtekinthetik a közösségi analitikát. |

4.

FONTOS

 Kattintson a Save  gombra az engedélybeállítások alkalmazásához.

5.

OPCIONÁLIS

 Kattintson a Settings  fülre, és válasszon egy színt és láthatósági beállítást a szerephez, majd kattintson a Save  gombra.

A szerep Settings  szakasza az is, ahol a csoport tulajdonosai és a megfelelő engedéllyel rendelkező tagok teljesen eltávolíthatják a szerepet a Szerep törlése  gomb segítségével.

A szerepek hierarchikus sorrendben vannak felsorolva: egy magasabb szerep a listában nagyobb hatalommal bír, mint az alatta lévő szerep. Ez a sorrend fontos, mert egyes engedélyek csak lehetővé teszik a tagok számára, hogy a legmagasabb szerepük alatti szerepeket kezeljék.

Minden szerep vagy nyilvános , vagy privát . A nyilvános szerepek megjeleníthetők a Közösségi oldalon és az élményekben. A privát szerepek csak a szerep- és engedélykezelési felületeken jelennek meg az arra jogosult tagok számára, vagy azok számára, akik birtokolják a privát szerepet. A láthatóság megváltoztatja, hogy hol jelenik meg egy szerep; nem változtatja meg a szerep által biztosított engedélyeket.

A Manage roles , Assign or remove roles from members , Manage access to this group’s resources , Manage and spend group revenue  vagy Delete Data Stores for experiences  engedélyek megadásához kétlépcsős azonosítást kell engedélyeznie.

## [Tagok kezelése](#tagok-kezelése)[](#tagok-kezelése)

A tagok konfigurálása csak akkor érhető el, ha Ön a csoport tulajdonosa, vagy engedéllyel rendelkezik más tagok és szerepeik kezelésére.

A tagok kezeléséhez a Creator Dashboard-ból:

1.

Bővítse ki a fiók váltót a bal felső sarokban, és válassza ki a csoportot.

2.

Ismét bővítse ki a fiók váltót, és válassza a Members  lehetőséget.

3.

Használja a Tag  fület a meglévő tagok keresésére vagy szerep szerint történő szűrésére. Használja az Invited  fület a függőben lévő meghívások áttekintésére.

Tag hozzáadásához kattintson a Invite  gombra, és keresse meg a felhasználónevét. A Roblox értesíti a meghívott alkotókat a beállított értesítési preferenciáik szerint. A csoport linkjét is másolhatja, és közvetlenül megoszthatja.

### [Szerepek kezelése](#szerepek-kezelése)[](#szerepek-kezelése)

A szerepkiosztásokat kezelheti a Members  oldalon vagy egy adott szerepnél:

-

A Members  oldalon kattintson a plusz (+)  gombra egy tag mellett a szerepmenü megnyitásához. Szerep hozzárendeléséhez kattintson a plusz (+)  gombra mellette az Add roles  alatt. Szerep eltávolításához kattintson a mínusz (-)  gombra mellette a Current roles  alatt, vagy kattintson a ×  gombra egy hozzárendelt szerepnél a tag neve mellett.

-

A Szerepek  oldalon válasszon ki egy szerepet, és nyissa meg a Members  fület. Kattintson a Add members  gombra, hogy keressen csoporttagokat, és hozzárendelje őket a szerephez. Tag eltávolításához kattintson a mínusz (-)  gombra a sor végén.

### [Tag eltávolítása](#tag-eltávolítása)[](#tag-eltávolítása)

Tag eltávolításához a csoportból kattintson a ⋮  gombra a sora végén, válassza a Felhasználó eltávolítása  lehetőséget, és erősítse meg a műveletet.

## [Kifizetések kezelése](#kifizetések-kezelése)[](#kifizetések-kezelése)

Ha Ön a csoport tulajdonosa, vagy rendelkezik a megfelelő [engedéllyel](#szerepek-%C3%A9s-enged%C3%A9lyek)  a Csoport Bevétel  alatt, a bal navigációs sávban talál egy Kifizetések  oldalt. Itt egyszeri kifizetéseket küldhet, valamint meghatározhatja a százalékos megosztásokat más tagokkal.

Egyes csoportok számára ez az oldal kezdetben nem érhető el különböző okok miatt, például a csoport életkorából vagy a kifizetéshez szükséges elegendő forrás hiányából.

A kifizetések nem oszthatók meg a csoporttagok között olyan játékok esetében, amelyek [fizetős hozzáférést kérnek helyi valutában](/docs/en-us/production/monetization/paid-access-local-currency) .

### [Egyszeri kifizetések](#egyszeri-kifizetések)[](#egyszeri-kifizetések)

Egyszeri kifizetések végezhetők el tagok számára egy csoportban, mindenki számára egy meghatározott összeg kiválasztásával. A biztonsági funkciók közé tartozik a 2FA kihívások, megerősítő párbeszédablakok és ellenőrzések a kifizetésre jogosult tagok körében.

 ![Egyszeri kifizetés gomb, amely a Kifizetések szakaszban van megjelölve a Creator Dashboard-on.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-One-Time.png)

Miután rákattintott a Robux küldése  gombra, választhat kifizetésre jogosultakat a felugró ablakból, vagy feltölthet egy .csv  táblázatfájlt a userId  és payoutInRobux  oszlopokkal, például:

| userId | | payoutInRobux |
| 012345 | | 5000 |
| 098765 | | 7000 |

### [Rendszeres kifizetések](#rendszeres-kifizetések)[](#rendszeres-kifizetések)

Rendszeres kifizetések is végezhetők az egész csoport és  játékonként, százalékos kifizetést rendelhet minden tagnak, mielőtt a fennmaradó összeg a csoport összesített egyenlegébe kerül.

 ![Megosztási kifizetés gombok, amelyek a Kifizetések szakaszban vannak megjelölve a Creator Dashboard-on.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Split-Options.png)

Vegyük figyelembe a következő forgatókönyvet, ahol a csoport játéka, a Laser Maze , 40%–30%–10%-ra van osztva három tag között, a fennmaradó 20%-kal.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-A.png)

Feltételezve, hogy a játék 1000 Robux-ot keres, a három tag 400, 300 és 100 Robux-ot kap (40%–30%–10%).

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-B.png)

A fennmaradó 200 Robux (a játék megosztásának 20%-a) továbbhalad a csoport megosztás  százalékaira, amelyeket 20%–20%–10%-ra határoztak meg ugyanazon három tag között; ők további 40, 40 és 20 Robux-ot kapnak.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-C.png)

A fennmaradó 100 Robux (a csoport megosztásának 50%-a) a csoport összesített egyenlegébe kerül.

 ![Példa folyamatábra, amely bemutatja, hogyan oszlanak el a játékmegosztások először a csoporttagok között, a fennmaradó összeg pedig a csoportmegosztásokba kerül a végső elosztás érdekében.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Splits-Example.png)

Vegye figyelembe, hogy a [privát szerver](/docs/en-us/production/monetization/private-servers)  előfizetésekből származó bevétel nem változik, ha később módosítja a megosztási százalékokat, ami azt jelenti, hogy ha egy játékos megvásárol egy privát szerver előfizetést, a vásárlás időpontjában érvényes megosztási százalékok örökre érvényesek maradnak (amíg le nem mondják). Ez a politika a jövőben változhat.

## [Csoport audit naplók](#csoport-audit-naplók)[](#csoport-audit-naplók)

A View audit logs  engedéllyel rendelkező csoporttagok áttekinthetik a csoportváltozásokat a következő csoportkezelési felületeken:

-

A Creator Dashboard-on válassza az Activity History  lehetőséget a Collaboration  alatt.

-

A Közösségekben nyissa meg a közösség konfigurációs oldalát, és válassza az Audit Log  lehetőséget.

A csoport tulajdonosai ezeket a naplókat használhatják az olyan tevékenységek nyomon követésére, amelyek megsérthetik a [csoport irányelveit](/docs/en-us/projects/group-guidelines) .

## [Szellemi tulajdon védelme](#szellemi-tulajdon-védelme)[](#szellemi-tulajdon-védelme)

A csoport összes játékának szerkesztésére jogosult tagok engedélyezhetik a [Hely másolása](/docs/en-us/projects/configure-games#allow-copying)  beállítást egy alkotásnál, lehetővé téve ezzel, hogy a teljes Roblox közösség lemásolja azt és felhasználja az abban található eszközöket. A szellemi tulajdon védelme érdekében a csoport tulajdonosának vagy a megfelelő engedéllyel rendelkező tagoknak:

-

Meg kell erősíteniük, hogy minden tag [megkapta a megfelelő szerepet](#szerepek-kezel%C3%A9se) .

-

Ellenőrizniük kell, hogy minden csoport szerep rendelkezik a megfelelő [engedélyekkel](#szerepek-%C3%A9s-enged%C3%A9lyek) .

-

Meg kell erősíteniük, hogy a [Hely másolása](/docs/en-us/projects/configure-games#allow-copying)  beállítás ki van kapcsolva, mielőtt privát eszközöket adnak hozzá.

## [További lokalizációk ezen az oldalon](#további-lokalizációk-ezen-az-oldalon)[](#további-lokalizációk-ezen-az-oldalon)

A webhely nyelvválasztójában nem elérhető, további lokalizált verziókért lásd az alábbi linkeket:

-

[Bolgár (български)](https://create.roblox.com/docs/bg-bg/projects/groups)

-

[Horvát (hrvatski)](https://create.roblox.com/docs/hr-hr/projects/groups)

-

[Cseh (čeština)](https://create.roblox.com/docs/cs-cz/projects/groups)

-

[Dán (dansk)](https://create.roblox.com/docs/da-dk/projects/groups)

-

[Holland (Nederlands)](https://create.roblox.com/docs/nl-nl/projects/groups)

-

[Észt (eesti)](https://create.roblox.com/docs/et-ee/projects/groups)

-

[Finn (suomi)](https://create.roblox.com/docs/fi-fi/projects/groups)

-

[Görög (Ελληνικά)](https://create.roblox.com/docs/el-gr/projects/groups)

-

[Magyar (magyar)](https://create.roblox.com/docs/hu-hu/projects/groups)

-

[Ír (Gaeilge)](https://create.roblox.com/docs/ga-ie/projects/groups)

-

[Lett (latviešu)](https://create.roblox.com/docs/lv-lv/projects/groups)

-

[Litván (lietuvių)](https://create.roblox.com/docs/lt-lt/projects/groups)

-

[Máltai (Malti)](https://create.roblox.com/docs/mt-mt/projects/groups)

-

[Portugál - Portugália (português)](https://create.roblox.com/docs/pt-pt/projects/groups)

-

[Román (română)](https://create.roblox.com/docs/ro-ro/projects/groups)

-

[Szlovák (slovenčina)](https://create.roblox.com/docs/sk-sk/projects/groups)

-

[Szlovén (slovenščina)](https://create.roblox.com/docs/sl-si/projects/groups)

-

[Svéd (svenska)](https://create.roblox.com/docs/sv-se/projects/groups)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
