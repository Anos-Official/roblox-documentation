<!-- Source: https://create.roblox.com/docs/cs-cz/projects/groups -->

Skupiny (týmy) | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Projects](/docs/en-us/projects)
6. /
7. [Work in teams](/docs/en-us/projects/groups)

# Skupiny (týmy)

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Skupina Roblox skupina  umožňuje více tvůrcům pracovat na stejné hře, používat stejné zdroje, sdílet zisky a dávat kredit všem přispěvatelům.

Vlastnictví her ve skupině pomáhá tvůrcům spolupracovat a fungovat jako nezávislá studia. Pokud dojde ke konfliktu ve skupině, Roblox nemůže pomoci s rozhodováním nebo řešením neshod.

## [Vytvoření skupiny](#vytvoření-skupiny)[](#vytvoření-skupiny)

Vytvoření skupiny stojí 100 Robux. Můžete spravovat její [role a oprávnění](#role-a-opr%C3%A1vn%C4%9Bn%C3%AD)  z [Creator Dashboard](https://create.roblox.com/dashboard/creations)  nebo [Komunit](https://www.roblox.com/communities) .

Před vytvořením skupiny si pečlivě přečtěte [pravidla a očekávání](/docs/en-us/projects/group-guidelines)  pro správu skupin.

Chcete-li vytvořit novou skupinu:

1.

Přejděte na [Creator Dashboard](https://create.roblox.com/dashboard/creations) , rozbalte přepínač účtu v levém horním rohu a klikněte na tlačítko plus (+) .

2.

Na stránce Vytvořit skupinu  nahrajte obrázek pro logo skupiny a zadejte název skupiny.

3.

Až budete připraveni, klikněte na tlačítko Koupit . Jakmile je skupina vytvořena, budete přesměrováni na stránku profilu skupiny, kde můžete upravit podrobnosti skupiny, včetně přidání až tří sociálních odkazů.

## [Role a oprávnění](#role-a-oprávnění)[](#role-a-oprávnění)

Členové skupiny mohou být přiřazeni k jedné nebo více rolím  ve skupině a každá role má oprávnění , která specifikují schopnosti jejích členů.

Konfigurace rolí je přístupná pouze v případě, že jste vlastníkem skupiny nebo máte oprávnění vytvářet, konfigurovat a přiřazovat role skupiny.

Chcete-li spravovat přiřazení rolí skupiny programově z herního serveru, použijte [HttpService](/docs/en-us/reference/engine/classes/HttpService)  k volání podporovaných koncových bodů Open Cloud Groups. Pro nastavení a ukázkový kód viz [Použít s Open Cloud](/docs/en-us/cloud-services/http-service#use-with-open-cloud) .

1.

Z [Creator Dashboard](https://create.roblox.com/dashboard/creations)  rozbalte přepínač účtu v levém horním rohu a vyberte skupinu.

2.

Znovu rozbalte přepínač účtu a vyberte Role .

3.

U každé role pečlivě potvrďte oprávnění na kartě Permissions .

Oprávnění jsou organizována do kategorií General , Creation  a Community . Následující sekce popisují oprávnění dostupná v každé kategorii.

### [Obecné](#obecné)[](#obecné)

Obecná oprávnění

| Manage roles | | Členové s tímto oprávněním mohou vytvářet, upravovat, mazat, měnit pořadí a přiřazovat nebo odstraňovat role pod svou nejvyšší rolí. Mohou upravovat pouze oprávnění, která již mají. |
| --- | --- |
| Assign or remove roles from members | | Členové s tímto oprávněním mohou přiřazovat nebo odstraňovat role pod svou nejvyšší rolí jakémukoli členovi. |
| Invite or approve members | | Členové s tímto oprávněním mohou zvát lidi do skupiny a schvalovat žádosti o připojení. |
| Kick members | | Členové s tímto oprávněním mohou odstraňovat členy, jejichž nejvyšší role je pod jejich vlastní. |
| Ban members | | Členové s tímto oprávněním mohou zakazovat členy, jejichž nejvyšší role je pod jejich vlastní. |
| Configure group profile | | Členové s tímto oprávněním mohou konfigurovat profil skupiny. |
| View audit logs | | Členové s tímto oprávněním mohou zobrazit [auditní protokoly skupiny](#auditn%C3%AD-protokoly-skupiny) . |
| Manage allies and enemies | | Členové s tímto oprávněním mohou spravovat spojence a nepřátele skupiny. |

### [Vytváření](#vytváření)[](#vytváření)

Creations

| Playtest experiences | | Členové s touto rolí mohou hrát všechny hry vlastněné skupinou, i když nejsou uvolněny pro širší publikum. Volitelně dostupné jako [oprávnění na hru](/docs/en-us/projects/configure-games) . |
| Edit experiences | | Členové s touto rolí mohou upravovat všechny hry a [zdroje](/docs/en-us/projects/assets)  vlastněné skupinou a používat všechny funkce v [Data Stores Manager](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Nezahrnuje úpravu hry mimo [spolupráci](/docs/en-us/projects/collaboration)  nebo ukládání místa z jedné hry do druhé. Volitelně dostupné jako [oprávnění na hru](/docs/en-us/projects/configure-games) . |
| Publish experiences | | Členové s touto rolí mohou jak upravovat hry, jak je uvedeno výše, tak také publikovat hry na Roblox. Volitelně dostupné jako [oprávnění na hru](/docs/en-us/projects/configure-games) . |
| Manage share links | | Členové s touto rolí mohou vytvářet/konfigurovat [sdílené odkazy](/docs/en-us/production/promotion/share-links) . |
| Manage experience events | | Členové s touto rolí mohou vytvářet/konfigurovat [události zážitků](/docs/en-us/production/promotion/experience-events) . |
| Moderate experiences | | Členové s touto rolí mohou zobrazit všechny zprávy v chatu ve hře (pouze pro čtení; člen musí být starší 18 let) a zakazovat nebo spravovat zakázané uživatele napříč všemi hrami vlastněnými skupinou. |
| Manage monetization for experiences | | Členové s touto rolí mohou spravovat monetizační produkty, jako jsou [pasy](/docs/en-us/production/monetization/passes) , [vývojářské produkty](/docs/en-us/production/monetization/developer-products) , [předplatné](/docs/en-us/production/monetization/subscriptions)  a další. Volitelně dostupné jako [oprávnění na hru](/docs/en-us/projects/configure-games) . |
| Manage secrets for experiences | | Členové s touto rolí mohou vidět seznam [tajemství](/docs/en-us/cloud-services/secrets)  a mohou vytvářet, aktualizovat a mazat tajemství pro všechny hry vlastněné skupinou. Členové s touto rolí potřebují oprávnění Edit experiences  k zobrazení stránky Tajemství. Volitelně dostupné jako [oprávnění na hru](/docs/en-us/projects/configure-games) . |

Analytics

| View analytics for experiences | | Členové s touto rolí mohou přistupovat k [analytice](/docs/en-us/production/analytics)  všech her vlastněných skupinou, i když nemají přístup k úpravám. Volitelně dostupné jako [oprávnění na hru](/docs/en-us/projects/configure-games) . |
| Manage alerts | | Členové s touto rolí mohou vytvářet a spravovat analytické upozornění. Spojte toto oprávnění s View analytics for experiences  pro zobrazení anotací upozornění přímo na grafech metrik. |

Monetization

| View group revenue | | Členové s touto rolí mohou zobrazit zůstatek Robux skupiny, jakékoli nakonfigurované opakované rozdělené platby a funkce sledování příjmů. |
| Manage and spend group revenue | | Členové s touto rolí mohou zobrazit všechny příjmy skupiny, jak je uvedeno výše, a také je přímo spravovat. To zahrnuje nastavení [opakovaných plateb](#opakovan%C3%A9-platby)  a odesílání [jednorázových plateb](#jednor%C3%A1zov%C3%A9-platby)  spolupracovníkům. |
| Create ad campaigns for the group | | Členové s touto rolí mohou inzerovat skupinu. |

Avatar items

| Create avatar items | | Členové s touto rolí mohou vytvářet položky pro avatary, jako je oblečení. |
| Configure avatar items | | Členové s touto rolí mohou konfigurovat detaily prodeje, doplnění a sponzorství pro existující položky avataru skupiny. |

API

| Manage API keys | | Členové s touto rolí mohou spravovat [Open Cloud API klíče](/docs/en-us/cloud/auth/api-keys)  pro skupinu. |

Development items

| View development items | | Členové s touto rolí mohou zobrazit vývojové položky vlastněné skupinou, například Audio . |
| Manage development items | | Členové s touto rolí mohou nahrávat a konfigurovat vývojové položky, jako jsou Decals . |
| Manage development item permissions | | Členové s touto rolí mohou konfigurovat oprávnění vývojových položek, například sdílení zvuku. |

Data Stores

| View Data Stores for experiences | | Členové s touto rolí mohou zobrazit datové úložiště pro všechny hry skupiny prostřednictvím [Data Stores Manager](/docs/en-us/cloud-services/data-stores/data-stores-manager) , ale nemohou mazat data. Volitelně dostupné jako [oprávnění na hru](/docs/en-us/projects/configure-games) . |
| Edit Data Stores for experiences | | Členové s touto rolí mohou mazat konkrétní klíče v datových úložištích pro všechny hry skupiny prostřednictvím [Data Stores Manager](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Volitelně dostupné jako [oprávnění na hru](/docs/en-us/projects/configure-games) . |
| Delete Data Stores for experiences | | Členové s touto rolí mohou mazat celá datová úložiště pro všechny hry skupiny prostřednictvím [Data Stores Manager](/docs/en-us/cloud-services/data-stores/data-stores-manager) . Volitelně dostupné jako [oprávnění na hru](/docs/en-us/projects/configure-games) . |

Notifications

| Manage webhooks for experiences | | Členové s touto rolí mohou seznamovat, vytvářet, aktualizovat a mazat webhooks pro všechny skupinové zážitky. |

Communication

| Manage support tickets for experiences | | Členové s touto rolí mohou spravovat podpůrné tikety pro všechny skupinové zážitky. |

Legacy

| Spravovat přístup k prostředkům této skupiny | | Členové s touto rolí mohou vytvářet a upravovat přístup k prostředkům skupiny. |

### [Komunita](#komunita)[](#komunita)

Posts

| View community announcements | | Členové s touto rolí mohou zobrazit oznámení komunity. |
| Create community announcements | | Členové s touto rolí mohou vytvářet oznámení komunity. |

Forums

| Manage categories | | Členové s touto rolí mohou spravovat kategorie fóra. |
| Create posts | | Členové s touto rolí mohou vytvářet příspěvky na fóru. |
| Remove posts | | Členové s touto rolí mohou odstraňovat příspěvky na fóru. |
| Lock posts | | Členové s touto rolí mohou zamykat příspěvky na fóru. |
| Pin posts | | Členové s touto rolí mohou připínat příspěvky na fóru. |
| Create comments | | Členové s touto rolí mohou vytvářet komentáře k příspěvkům na fóru. |
| Remove comments | | Členové s touto rolí mohou odstraňovat komentáře z příspěvků na fóru. |

Content moderation

| View content moderation | | Členové s touto rolí mohou zobrazit moderaci obsahu. |
| Manage content moderation | | Členové s touto rolí mohou spravovat moderaci obsahu. |

Miscellaneous

| Bypass slow mode | | Členové s touto rolí mohou obejít pomalý režim. |
| View community analytics | | Členové s touto rolí mohou zobrazit analytiku komunity. |

4.

DŮLEŽITÉ

 Klikněte na tlačítko Save  pro aplikaci nastavení oprávnění.

5.

VOLITELNÉ

 Klikněte na kartu Settings  a vyberte barvu a nastavení viditelnosti pro roli, poté klikněte na tlačítko Save .

Sekce Settings  role je také místem, kde mohou vlastníci skupiny a členové s dostatečnými oprávněními zcela odstranit roli pomocí tlačítka Smazat roli .

Role jsou uvedeny v hierarchickém pořadí: role vyšší v seznamu má větší pravomoc než role pod ní. Tento pořadí je důležité, protože některá oprávnění umožňují členům spravovat pouze role pod jejich nejvyšší rolí.

Každá role je buď veřejná , nebo soukromá . Veřejné role mohou být zobrazeny na stránce Komunity a v zážitcích. Soukromé role jsou zobrazeny pouze na správě rolí a oprávnění pro autorizované členy nebo pro členy, kteří drží soukromou roli. Viditelnost mění, kde se role objevuje; nemění však oprávnění, která role uděluje.

Pro udělení Manage roles , Assign or remove roles from members , Manage access to this group’s resources , Manage and spend group revenue  nebo Delete Data Stores for experiences  musíte mít povolenou dvoufázovou verifikaci.

## [Správa členů](#správa-členů)[](#správa-členů)

Konfigurace členů je přístupná pouze v případě, že jste vlastníkem skupiny nebo máte oprávnění spravovat ostatní členy a jejich role.

Chcete-li spravovat členy z Creator Dashboard:

1.

Rozbalte přepínač účtu v levém horním rohu a vyberte skupinu.

2.

Znovu rozbalte přepínač účtu a vyberte Members .

3.

Použijte kartu Člen  k vyhledání existujících členů nebo je filtrovat podle role. Použijte kartu Pozvaní  k přezkoumání čekajících pozvánek.

Chcete-li přidat člena, klikněte na tlačítko Invite  a vyhledejte jeho uživatelské jméno. Roblox upozorní pozvané tvůrce podle jejich preferencí oznámení. Můžete také zkopírovat odkaz na skupinu a sdílet ho přímo.

### [Správa rolí](#správa-rolí)[](#správa-rolí)

Můžete spravovat přiřazení rolí buď na stránce Members , nebo na konkrétní roli:

-

Na stránce Members  klikněte na tlačítko plus (+)  vedle člena pro otevření nabídky rolí. Chcete-li přiřadit roli, klikněte na tlačítko plus (+)  vedle ní pod Přidat role . Chcete-li odebrat roli, klikněte na tlačítko minus (-)  vedle ní pod Aktuální role , nebo klikněte na tlačítko ×  na přiřazené roli vedle jména člena.

-

Na stránce Role  vyberte roli a otevřete její kartu Members . Klikněte na tlačítko Add members  pro vyhledání členů skupiny a přiřazení k roli. Chcete-li odebrat člena, klikněte na tlačítko minus (-)  na konci jejich řádku.

### [Odstranění člena](#odstranění-člena)[](#odstranění-člena)

Chcete-li odstranit člena ze skupiny, klikněte na tlačítko ⋮  na konci jejich řádku, vyberte Vykopnout uživatele  a potvrďte akci.

## [Správa plateb](#správa-plateb)[](#správa-plateb)

Pokud jste vlastníkem skupiny nebo máte správné [oprávnění](#role-a-opr%C3%A1vn%C4%9Bn%C3%AD)  v rámci Příjmy skupiny , najdete stránku Platby  pod Finance  v levé navigaci. Zde můžete odesílat jednorázové platby, stejně jako definovat procentuální rozdělení s ostatními členy.

Některé skupiny nemusí mít tuto stránku zpočátku odemčenou z různých důvodů, jako je věk skupiny nebo nedostatečné prostředky k vyplacení.

Platby nemohou být sdíleny mezi členy skupiny pro hry, které účtují [placený přístup v místní měně](/docs/en-us/production/monetization/paid-access-local-currency) .

### [Jednorázové platby](#jednorázové-platby)[](#jednorázové-platby)

Jednorázové platby mohou být provedeny členům v dávce, přičemž se vybere stanovená částka pro každého. Bezpečnostní funkce zahrnují výzvy 2FA, potvrzovací dialogy a kontroly kolem způsobilosti členů, kteří jsou placeni.

 ![Tlačítko jednorázové platby označeno v sekci Plateb na Creator Dashboard.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-One-Time.png)

Jakmile kliknete na tlačítko Odeslat Robux , můžete vybrat příjemce plateb z vyskakovacího okna nebo nahrát soubor tabulky .csv  s sloupci userId  a payoutInRobux , například:

| userId | | payoutInRobux |
| 012345 | | 5000 |
| 098765 | | 7000 |

### [Opakované platby](#opakované-platby)[](#opakované-platby)

Opakované platby mohou být také provedeny napříč celou skupinou a  na hru, přičemž se každému členu přiřadí procentuální platba předtím, než zbytek vstoupí do celkového zůstatku skupiny.

 ![Tlačítka pro rozdělení plateb označena v sekci Plateb na Creator Dashboard.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Split-Options.png)

Zvažte následující scénář, kde je skupinová hra Laser Maze  rozdělena 40%–30%–10% mezi tři členy, se zbytkem 20%.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-A.png)

Předpokládejme, že hra vydělá 1000 Robux, tři členové obdrží 400, 300 a 100 Robux (40%–30%–10%).

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-B.png)

Zbývajících 200 Robux (20% z rozdělení hry) přechází na procenta skupinového rozdělení , definovaná na 20%–20%–10% mezi stejnými třemi členy; obdrží navíc 40, 40 a 20 Robux.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-C.png)

Zbývajících 100 Robux (50% z rozdělení skupiny) je umístěno do celkového zůstatku skupiny.

 ![Příklad diagramu, jak jsou rozdělení her nejprve distribuována členům skupiny, přičemž zbytek se započítává do skupinových rozdělení pro konečné rozdělení mezi skupinu.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Splits-Example.png)

Všimněte si, že příjmy z [předplatného soukromého serveru](/docs/en-us/production/monetization/private-servers)  se nezmění, pokud později upravíte procenta rozdělení, což znamená, že pokud hráč zakoupí předplatné soukromého serveru, procenta rozdělení v době nákupu se použijí na toto konkrétní předplatné navždy (dokud nebude zrušeno). Tato politika může být v budoucnu změněna.

## [Auditní protokoly skupiny](#auditní-protokoly-skupiny)[](#auditní-protokoly-skupiny)

Členové skupiny s oprávněním View audit logs  mohou přezkoumávat změny ve skupině pomocí těchto povrchů správy skupiny:

-

Na Creator Dashboard vyberte Historie aktivit  pod Spolupráce .

-

Na Komunitách otevřete konfigurační stránku komunity a vyberte Auditní protokol .

Vlastníci skupin mohou tyto protokoly použít k monitorování aktivit, které by mohly porušovat [pravidla skupiny](/docs/en-us/projects/group-guidelines) .

## [Ochrana duševního vlastnictví](#ochrana-duševního-vlastnictví)[](#ochrana-duševního-vlastnictví)

Členové skupiny s oprávněním upravovat všechny hry skupiny mohou povolit nastavení [Kopírování místa](/docs/en-us/projects/configure-games#allow-copying)  pro vytvoření, což potenciálně umožňuje celé komunitě Roblox jej kopírovat a používat zdroje v něm. Aby pomohli chránit duševní vlastnictví ve skupině, by vlastník nebo členové s dostatečnými oprávněními měli:

-

Potvrdit, že každý člen je [přiřazen k odpovídající roli](#spr%C3%A1va-rol%C3%AD) .

-

Zkontrolovat, že každá role skupiny má správná [oprávnění](#role-a-opr%C3%A1vn%C4%9Bn%C3%AD) .

-

Potvrdit, že je nastavení [Kopírování místa](/docs/en-us/projects/configure-games#allow-copying)  zakázáno před přidáním soukromých zdrojů.

## [Další lokalizace pro tuto stránku](#další-lokalizace-pro-tuto-stránku)[](#další-lokalizace-pro-tuto-stránku)

Pro další lokalizované verze této stránky, které nejsou k dispozici v jazykovém výběru na stránce, viz následující odkazy:

-

[Bulharština (български)](https://create.roblox.com/docs/bg-bg/projects/groups)

-

[Chorvatština (hrvatski)](https://create.roblox.com/docs/hr-hr/projects/groups)

-

[Čeština (čeština)](https://create.roblox.com/docs/cs-cz/projects/groups)

-

[Dánština (dansk)](https://create.roblox.com/docs/da-dk/projects/groups)

-

[Nizozemština (Nederlands)](https://create.roblox.com/docs/nl-nl/projects/groups)

-

[Estonština (eesti)](https://create.roblox.com/docs/et-ee/projects/groups)

-

[Finština (suomi)](https://create.roblox.com/docs/fi-fi/projects/groups)

-

[Řečtina (Ελληνικά)](https://create.roblox.com/docs/el-gr/projects/groups)

-

[Maďarština (magyar)](https://create.roblox.com/docs/hu-hu/projects/groups)

-

[Irština (Gaeilge)](https://create.roblox.com/docs/ga-ie/projects/groups)

-

[Lotyština (latviešu)](https://create.roblox.com/docs/lv-lv/projects/groups)

-

[Litevština (lietuvių)](https://create.roblox.com/docs/lt-lt/projects/groups)

-

[Maltština (Malti)](https://create.roblox.com/docs/mt-mt/projects/groups)

-

[Portugalština - Portugalsko (português)](https://create.roblox.com/docs/pt-pt/projects/groups)

-

[Rumunština (română)](https://create.roblox.com/docs/ro-ro/projects/groups)

-

[Slovenština (slovenčina)](https://create.roblox.com/docs/sk-sk/projects/groups)

-

[Slovinština (slovenščina)](https://create.roblox.com/docs/sl-si/projects/groups)

-

[Švédština (svenska)](https://create.roblox.com/docs/sv-se/projects/groups)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
