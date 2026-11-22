<!-- Source: https://create.roblox.com/docs/sk-sk/projects/groups -->

Skupiny (tímy) | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Projects](/docs/en-us/projects)
6. /
7. [Work in teams](/docs/en-us/projects/groups)

# Skupiny (tímy)

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Skupina Roblox skupina  umožňuje viacerým tvorcom pracovať na tej istej hre, používať rovnaké zdroje, zdieľať zisky a priznávať zásluhy všetkým prispievateľom.

Vlastníctvo hier v skupinách pomáha tvorcom spolupracovať a fungovať ako nezávislé štúdiá. Ak dôjde k konfliktu v rámci skupiny, Roblox nemôže pomôcť pri rozhodovaní alebo riešení nezhôd.

## [Vytvorenie skupiny](#vytvorenie-skupiny)[](#vytvorenie-skupiny)

Vytvorenie skupiny stojí 100 Robux. Môžete spravovať jej [úlohy a oprávnenia](#%C3%BAlohy-a-opr%C3%A1vnenia)  z [Creator Dashboard](https://create.roblox.com/dashboard/creations)  alebo [Komunit](https://www.roblox.com/communities) .

Pred vytvorením skupiny si dôkladne prečítajte [pravidlá a očakávania](/docs/en-us/projects/group-guidelines)  pre správu skupín.

Ak chcete vytvoriť novú skupinu:

1.

Prejdite na [Creator Dashboard](https://create.roblox.com/dashboard/creations) , rozbaľte prepínač účtov v ľavom hornom rohu a kliknite na tlačidlo plus (+) .

2.

Na stránke Vytvoriť skupinu  nahrajte obrázok pre logo skupiny a zadajte názov skupiny.

3.

Keď ste pripravení, kliknite na tlačidlo Kúpiť . Po vytvorení skupiny budete presmerovaní na stránku profilu skupiny, kde môžete upraviť podrobnosti skupiny, vrátane pridania až troch sociálnych odkazov.

## [Úlohy a oprávnenia](#úlohy-a-oprávnenia)[](#úlohy-a-oprávnenia)

Členovia skupiny môžu byť priradení k jednej alebo viacerým úlohám  v rámci skupiny a každá úloha má oprávnenia , ktoré špecifikujú schopnosti jej členov.

Konfigurácia úloh je prístupná iba v prípade, že ste vlastníkom skupiny alebo máte oprávnenie vytvárať, konfigurovať a priraďovať úlohy skupiny.

Na spravovanie priradení úloh skupiny programovo z herného servera použite [HttpService](/docs/en-us/reference/engine/classes/HttpService)  na volanie podporovaných koncových bodov Open Cloud Groups. Pre nastavenie a ukážkový kód pozrite [Použiť s Open Cloud](/docs/en-us/cloud-services/http-service#use-with-open-cloud) .

1.

Z [Creator Dashboard](https://create.roblox.com/dashboard/creations)  rozbaľte prepínač účtov v ľavom hornom rohu a vyberte skupinu.

2.

Znova rozbaľte prepínač účtov a vyberte Úlohy .

3.

Pre každú úlohu dôkladne potvrďte oprávnenia na karte Permissions .

Oprávnenia sú usporiadané do kategórií General , Creation  a Community . Nasledujúce sekcie popisujú oprávnenia dostupné v každej kategórii.

### [Všeobecné](#všeobecné)[](#všeobecné)

Všeobecné oprávnenia

| Manage roles | | Členovia s týmto oprávnením môžu vytvárať, upravovať, mazať, preusporiadať a priraďovať alebo odoberať úlohy pod ich najvyššou úlohou. Môžu upravovať iba oprávnenia, ktoré už majú. |
| --- | --- |
| Assign or remove roles from members | | Členovia s týmto oprávnením môžu priraďovať alebo odoberať úlohy pod ich najvyššou úlohou akémukoľvek členovi. |
| Invite or approve members | | Členovia s týmto oprávnením môžu pozývať ľudí do skupiny a schvaľovať žiadosti o pripojenie. |
| Kick members | | Členovia s týmto oprávnením môžu odstraňovať členov, ktorých najvyššia úloha je pod ich vlastnou. |
| Ban members | | Členovia s týmto oprávnením môžu zakazovať členov, ktorých najvyššia úloha je pod ich vlastnou. |
| Configure group profile | | Členovia s týmto oprávnením môžu konfigurovať profil skupiny. |
| View audit logs | | Členovia s týmto oprávnením môžu zobraziť [auditné záznamy skupiny](#auditn%C3%A9-z%C3%A1znamy-skupiny) . |
| Manage allies and enemies | | Členovia s týmto oprávnením môžu spravovať spojencov a nepriateľov skupiny. |

### [Vytvorenie](#vytvorenie)[](#vytvorenie)

Creations

| Playtest experiences | | Členovia s touto úlohou môžu hrať všetky hry, ktoré vlastní skupina, aj keď nie sú sprístupnené širšiemu publiku. Voliteľne dostupné ako [oprávnenie na hru](/docs/en-us/projects/configure-games) . |
| Edit experiences | | Členovia s touto úlohou môžu upravovať všetky hry a [zdroje](/docs/en-us/projects/assets) , ktoré vlastní skupina, a používať všetky funkcie v [Správcovi úložiska dát](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Nezahŕňa úpravu hry mimo [spolupráce](/docs/en-us/projects/collaboration)  alebo uloženie miesta z jednej hry do druhej. Voliteľne dostupné ako [oprávnenie na hru](/docs/en-us/projects/configure-games) . |
| Publish experiences | | Členovia s touto úlohou môžu upravovať hry, ako je uvedené vyššie, a tiež publikovať hry na Roblox. Voliteľne dostupné ako [oprávnenie na hru](/docs/en-us/projects/configure-games) . |
| Manage share links | | Členovia s touto úlohou môžu vytvárať/konfigurovať [zdieľacie odkazy](/docs/en-us/production/promotion/share-links) . |
| Manage experience events | | Členovia s touto úlohou môžu vytvárať/konfigurovať [skúsenostné udalosti](/docs/en-us/production/promotion/experience-events) . |
| Moderate experiences | | Členovia s touto úlohou môžu zobraziť všetky správy v hre (iba na čítanie; člen musí mať 18+) a zakazovať alebo spravovať zakázaných používateľov vo všetkých hrách, ktoré vlastní skupina. |
| Manage monetization for experiences | | Členovia s touto úlohou môžu spravovať produkty monetizácie, ako sú [pasy](/docs/en-us/production/monetization/passes) , [vývojárske produkty](/docs/en-us/production/monetization/developer-products) , [predplatné](/docs/en-us/production/monetization/subscriptions)  a ďalšie. Voliteľne dostupné ako [oprávnenie na hru](/docs/en-us/projects/configure-games) . |
| Manage secrets for experiences | | Členovia s touto úlohou môžu vidieť zoznam [tajomstiev](/docs/en-us/cloud-services/secrets)  a môžu vytvárať, aktualizovať a mazať tajomstvá pre všetky hry, ktoré vlastní skupina. Členovia s touto úlohou potrebujú oprávnenie Edit experiences  na zobrazenie stránky Tajomstvá. Voliteľne dostupné ako [oprávnenie na hru](/docs/en-us/projects/configure-games) . |

Analytics

| View analytics for experiences | | Členovia s touto úlohou môžu pristupovať k [analytike](/docs/en-us/production/analytics)  všetkých hier, ktoré vlastní skupina, aj keď nemajú prístup na úpravy. Voliteľne dostupné ako [oprávnenie na hru](/docs/en-us/projects/configure-games) . |
| Manage alerts | | Členovia s touto úlohou môžu vytvárať a spravovať analytické upozornenia. Spojte toto oprávnenie s View analytics for experiences  na zobrazenie anotácií upozornení priamo na grafoch metrík. |

Monetization

| View group revenue | | Členovia s touto úlohou môžu zobraziť zostatok Robux skupiny, akékoľvek nakonfigurované opakujúce sa rozdelenia platieb a funkcie zaznamenávania príjmov. |
| Manage and spend group revenue | | Členovia s touto úlohou môžu zobraziť všetky príjmy skupiny, ako je uvedené vyššie, a tiež ich priamo spravovať. To zahŕňa nastavenie [opakujúcich sa platieb](#opakuj%C3%BAce-sa-platby)  a odosielanie [jednorazových platieb](#jednorazov%C3%A9-platby)  spolupracovníkom. |
| Create ad campaigns for the group | | Členovia s touto úlohou môžu inzerovať skupinu. |

Avatar items

| Create avatar items | | Členovia s touto úlohou môžu vytvárať položky avatara, ako je oblečenie. |
| Configure avatar items | | Členovia s touto úlohou môžu konfigurovať podrobnosti predaja, doplnenia a sponzoringu pre existujúce položky avatara skupiny. |

API

| Manage API keys | | Členovia s touto úlohou môžu spravovať [Open Cloud API kľúče](/docs/en-us/cloud/auth/api-keys)  pre skupinu. |

Development items

| View development items | | Členovia s touto úlohou môžu zobraziť vývojové položky, ktoré vlastní skupina, napríklad Audio . |
| Manage development items | | Členovia s touto úlohou môžu nahrávať a konfigurovať vývojové položky aktív, ako sú Decals . |
| Manage development item permissions | | Členovia s touto úlohou môžu konfigurovať oprávnenia vývojových položiek, napríklad zdieľanie zvuku. |

Data Stores

| View Data Stores for experiences | | Členovia s touto úlohou môžu zobraziť úložiská dát pre všetky hry skupiny prostredníctvom [Správcu úložiska dát](/docs/en-us/cloud-services/data-stores/data-stores-manager) , ale nemôžu mazať dáta. Voliteľne dostupné ako [oprávnenie na hru](/docs/en-us/projects/configure-games) . |
| Edit Data Stores for experiences | | Členovia s touto úlohou môžu mazať konkrétne kľúče v úložiskách dát pre všetky hry skupiny prostredníctvom [Správcu úložiska dát](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Voliteľne dostupné ako [oprávnenie na hru](/docs/en-us/projects/configure-games) . |
| Delete Data Stores for experiences | | Členovia s touto úlohou môžu mazať celé úložiská dát pre všetky hry skupiny prostredníctvom [Správcu úložiska dát](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Voliteľne dostupné ako [oprávnenie na hru](/docs/en-us/projects/configure-games) . |

Notifications

| Manage webhooks for experiences | | Členovia s touto úlohou môžu zoznamovať, vytvárať, aktualizovať a mazať webhooks pre všetky skupinové skúsenosti. |

Communication

| Manage support tickets for experiences | | Členovia s touto úlohou môžu spravovať podporné tikety pre všetky skupinové skúsenosti. |

Legacy

| Spravovať prístup k zdrojom tejto skupiny | | Členovia s touto úlohou môžu vytvárať a upravovať prístup k zdrojom skupiny. |

### [Komunita](#komunita)[](#komunita)

Posts

| View community announcements | | Členovia s touto úlohou môžu zobraziť oznámenia komunity. |
| Create community announcements | | Členovia s touto úlohou môžu vytvárať oznámenia komunity. |

Forums

| Manage categories | | Členovia s touto úlohou môžu spravovať kategórie fóra. |
| Create posts | | Členovia s touto úlohou môžu vytvárať príspevky na fóre. |
| Remove posts | | Členovia s touto úlohou môžu odstraňovať príspevky na fóre. |
| Lock posts | | Členovia s touto úlohou môžu zamykať príspevky na fóre. |
| Pin posts | | Členovia s touto úlohou môžu pripínať príspevky na fóre. |
| Create comments | | Členovia s touto úlohou môžu vytvárať komentáre k príspevkom na fóre. |
| Remove comments | | Členovia s touto úlohou môžu odstraňovať komentáre z príspevkov na fóre. |

Content moderation

| View content moderation | | Členovia s touto úlohou môžu zobraziť moderáciu obsahu. |
| Manage content moderation | | Členovia s touto úlohou môžu spravovať moderáciu obsahu. |

Miscellaneous

| Bypass slow mode | | Členovia s touto úlohou môžu obísť pomalý režim. |
| View community analytics | | Členovia s touto úlohou môžu zobraziť analytiku komunity. |

4.

DÔLEŽITÉ

 Kliknite na tlačidlo Save , aby ste uplatnili nastavenia oprávnení.

5.

VOLITEĽNÉ

 Kliknite na kartu Settings  a vyberte farbu a nastavenie viditeľnosti pre úlohu, potom kliknite na tlačidlo Save .

Sekcia Settings  úlohy je tiež miestom, kde môžu vlastníci skupiny a členovia s dostatočnými oprávneniami úplne odstrániť úlohu prostredníctvom tlačidla Odstrániť úlohu .

Úlohy sú uvedené v hierarchickom poradí: úloha vyššia v zozname má väčšiu autoritu ako úloha nižšie. Toto poradie je dôležité, pretože niektoré oprávnenia umožňujú členom spravovať iba úlohy pod ich najvyššou úlohou.

Každá úloha je buď verejná , alebo súkromná . Verejné úlohy môžu byť zobrazené na stránke Komunity a v skúsenostiach. Súkromné úlohy sú zobrazené iba na správe úloh a oprávnení pre autorizovaných členov alebo pre členov, ktorí majú súkromnú úlohu. Viditeľnosť mení, kde sa úloha zobrazuje; nemení oprávnenia, ktoré úloha udeľuje.

Na udelenie Manage roles , Assign or remove roles from members , Manage access to this group’s resources , Manage and spend group revenue  alebo Delete Data Stores for experiences  musíte mať povolené dvojstupňové overenie.

## [Spravovať členov](#spravovať-členov)[](#spravovať-členov)

Konfigurácia členov je prístupná iba v prípade, že ste vlastníkom skupiny alebo máte oprávnenie spravovať ostatných členov a ich úlohy.

Na spravovanie členov z Creator Dashboard:

1.

Rozbaľte prepínač účtov v ľavom hornom rohu a vyberte skupinu.

2.

Znova rozbaľte prepínač účtov a vyberte Members .

3.

Použite kartu Člen  na vyhľadávanie existujúcich členov alebo ich filtrovanie podľa úlohy. Použite kartu Pozvaní  na preskúmanie čakajúcich pozvaní.

Ak chcete pridať člena, kliknite na tlačidlo Invite  a vyhľadajte jeho používateľské meno. Roblox upozorní pozvaných tvorcov podľa ich preferencií notifikácií. Môžete tiež skopírovať odkaz na skupinu a zdieľať ho priamo.

### [Spravovať úlohy](#spravovať-úlohy)[](#spravovať-úlohy)

Môžete spravovať priradenia úloh buď na stránke Members , alebo na konkrétnej úlohe:

-

Na stránke Members  kliknite na tlačidlo plus (+)  vedľa člena, aby ste otvorili ponuku úloh. Ak chcete priradiť úlohu, kliknite na tlačidlo plus (+)  vedľa nej pod Pridať úlohy . Ak chcete odobrať úlohu, kliknite na tlačidlo minus (-)  vedľa nej pod Aktuálne úlohy , alebo kliknite na tlačidlo ×  na priradenej úlohe vedľa mena člena.

-

Na stránke Úlohy  vyberte úlohu a otvorte jej kartu Members . Kliknite na tlačidlo Add members  a vyhľadajte členov skupiny a priraďte ich k úlohe. Ak chcete odobrať člena, kliknite na tlačidlo minus (-)  na konci jeho riadku.

### [Odstránenie člena](#odstránenie-člena)[](#odstránenie-člena)

Ak chcete odstrániť člena zo skupiny, kliknite na tlačidlo ⋮  na konci jeho riadku, vyberte Vykopnúť používateľa  a potvrďte akciu.

## [Spravovať platby](#spravovať-platby)[](#spravovať-platby)

Ak ste vlastníkom skupiny alebo máte správne [oprávnenie](#%C3%BAlohy-a-opr%C3%A1vnenia)  v rámci Príjmy skupiny , nájdete stránku Platby  pod Financie  v ľavej navigácii. Tu môžete posielať jednorazové platby, ako aj definovať percentuálne rozdelenia s ostatnými členmi.

Niektoré skupiny nemusia mať túto stránku odomknutú spočiatku z rôznych dôvodov, ako je vek skupiny alebo nedostatočné prostriedky na platbu.

Platby nemôžu byť zdieľané medzi členmi skupiny pre hry, ktoré účtujú [platený prístup v miestnej mene](/docs/en-us/production/monetization/paid-access-local-currency) .

### [Jednorazové platby](#jednorazové-platby)[](#jednorazové-platby)

Jednorazové platby môžu byť vykonané členom v dávke, pričom sa vyberie stanovená suma pre každého. Bezpečnostné funkcie zahŕňajú výzvy 2FA, potvrdzovacie dialógy a kontroly okolo oprávnenosti členov, ktorí dostávajú platby.

 ![Tlačidlo jednorazovej platby označené v sekcii Platby na Creator Dashboard.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-One-Time.png)

Akonáhle kliknete na tlačidlo Odoslať Robux , môžete vybrať príjemcov platieb z vyskakovacieho okna alebo nahrať súbor tabuľky .csv  s stĺpcami userId  a payoutInRobux , napríklad:

| userId | | payoutInRobux |
| 012345 | | 5000 |
| 098765 | | 7000 |

### [Opakujúce sa platby](#opakujúce-sa-platby)[](#opakujúce-sa-platby)

Opakujúce sa platby môžu byť tiež vykonané naprieč celou skupinou a  na hru, pričom sa priradí percentuálne rozdelenie platby každému členovi predtým, ako zvyšok vstúpi do celkového zostatku skupiny.

 ![Tlačidlá rozdelenia platieb označené v sekcii Platby na Creator Dashboard.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Split-Options.png)

Zvážte nasledujúci scenár, kde je skupinová hra Laser Maze  rozdelená 40%–30%–10% medzi troch členov, pričom zvyšok je 20%.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-A.png)

Predpokladajme, že hra zarobí 1000 Robux, traja členovia dostanú 400, 300 a 100 Robux, resp. (40%–30%–10%).

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-B.png)

Zvyšných 200 Robux (20% z rozdelenia hry) prechádza na percentá skupinového rozdelenia , definované na 20%–20%–10% medzi rovnakými tromi členmi; dostanú ďalších 40, 40 a 20 Robux, resp.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-C.png)

Zvyšných 100 Robux (50% zo skupinového rozdelenia) sa umiestni do celkového zostatku skupiny.

 ![Príklad diagramu toku, ako sú rozdelenia hier najprv distribuované členom skupiny, pričom zvyšok sa zohľadňuje v skupinových rozdeleniach pre konečnú distribúciu medzi skupinou.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Splits-Example.png)

Upozorňujeme, že príjmy z [súkromných serverov](/docs/en-us/production/monetization/private-servers)  sa nezmenia, ak neskôr upravíte percentá rozdelenia, čo znamená, že ak si hráč zakúpi predplatné súkromného servera, percentá rozdelenia v čase nákupu sa budú vzťahovať na toto konkrétne predplatné navždy (až do jeho zrušenia). Táto politika sa môže v budúcnosti zmeniť.

## [Auditné záznamy skupiny](#auditné-záznamy-skupiny)[](#auditné-záznamy-skupiny)

Členovia skupiny s oprávnením View audit logs  môžu preskúmať zmeny v skupine pomocou týchto povrchov správy skupiny:

-

Na Creator Dashboard vyberte História aktivít  pod Spolupráca .

-

Na komunitách otvorte konfiguračnú stránku komunity a vyberte Auditný záznam .

Vlastníci skupiny môžu tieto záznamy použiť na monitorovanie aktivít, ktoré by mohli porušovať [pravidlá skupiny](/docs/en-us/projects/group-guidelines) .

## [Ochrana duševného vlastníctva](#ochrana-duševného-vlastníctva)[](#ochrana-duševného-vlastníctva)

Členovia skupiny s oprávnením upravovať všetky hry skupiny môžu povoliť nastavenie [Kopírovanie miesta](/docs/en-us/projects/configure-games#allow-copying)  pre vytvorenie, čo potenciálne umožňuje celej komunite Roblox ho kopírovať a používať zdroje v ňom. Na ochranu duševného vlastníctva v skupine by mal vlastník alebo členovia s dostatočnými oprávneniami:

-

Potvrdiť, že každý člen je [priradený k príslušnej úlohe](#spravova%C5%A5-%C3%BAlohy) .

-

Skontrolovať, že každá úloha skupiny má správne [oprávnenia](#%C3%BAlohy-a-opr%C3%A1vnenia) .

-

Potvrdiť, že je nastavenie [Kopírovanie miesta](/docs/en-us/projects/configure-games#allow-copying)  zakázané pred pridaním súkromných aktív.

## [Ďalšie lokalizácie pre túto stránku](#ďalšie-lokalizácie-pre-túto-stránku)[](#ďalšie-lokalizácie-pre-túto-stránku)

Pre ďalšie lokalizované verzie tejto stránky, ktoré nie sú dostupné v jazykovom výbere na stránke, pozrite nasledujúce odkazy:

-

[Bulharčina (български)](https://create.roblox.com/docs/bg-bg/projects/groups)

-

[Chorvátčina (hrvatski)](https://create.roblox.com/docs/hr-hr/projects/groups)

-

[Čeština (čeština)](https://create.roblox.com/docs/cs-cz/projects/groups)

-

[Dánčina (dansk)](https://create.roblox.com/docs/da-dk/projects/groups)

-

[Holandčina (Nederlands)](https://create.roblox.com/docs/nl-nl/projects/groups)

-

[Estónčina (eesti)](https://create.roblox.com/docs/et-ee/projects/groups)

-

[Fínčina (suomi)](https://create.roblox.com/docs/fi-fi/projects/groups)

-

[Gréčtina (Ελληνικά)](https://create.roblox.com/docs/el-gr/projects/groups)

-

[Maďarčina (magyar)](https://create.roblox.com/docs/hu-hu/projects/groups)

-

[Írčina (Gaeilge)](https://create.roblox.com/docs/ga-ie/projects/groups)

-

[Lotyština (latviešu)](https://create.roblox.com/docs/lv-lv/projects/groups)

-

[Litovčina (lietuvių)](https://create.roblox.com/docs/lt-lt/projects/groups)

-

[Maltčina (Malti)](https://create.roblox.com/docs/mt-mt/projects/groups)

-

[Portugalčina - Portugalsko (português)](https://create.roblox.com/docs/pt-pt/projects/groups)

-

[Rumunčina (română)](https://create.roblox.com/docs/ro-ro/projects/groups)

-

[Slovenčina (slovenčina)](https://create.roblox.com/docs/sk-sk/projects/groups)

-

[Slovinčina (slovenščina)](https://create.roblox.com/docs/sl-si/projects/groups)

-

[Švédčina (svenska)](https://create.roblox.com/docs/sv-se/projects/groups)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
