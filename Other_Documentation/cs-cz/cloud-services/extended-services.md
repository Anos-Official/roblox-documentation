<!-- Source: https://create.roblox.com/docs/cs-cz/cloud-services/extended-services -->

Rozšířené služby | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Cloud services](/docs/en-us/cloud-services/data-stores-vs-memory-stores)

# Rozšířené služby

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Rozšířené služby jsou řešení, které vám umožňuje spravovat používání služeb a platby nad rámec výchozích limitů Robloxu. Zahrnují datová úložiště, paměťová úložiště, syntézu řeči, rozpoznávání řeči a výpočetní výkon.

## [Požadavky na způsobilost](#požadavky-na-způsobilost)[](#požadavky-na-způsobilost)

Abyste mohli používat rozšířené služby, musí být váš účet Roblox:

-

[Ověřený ID](/docs/en-us/production/publishing/account-verification#verify-through-government-id)  a starší 18 let.

-

Nacházet se v [podporované zemi](#podporovan%C3%A9-zem%C4%9B) .

-

Mít platnou e-mailovou adresu spojenou s účtem.

-

Nebýt aktuálně zablokován nebo moderován.

-

Přijmout a dodržovat [podmínky služby](https://en.help.roblox.com/hc/articles/37967848292500) .

U skupinových účtů musí splnit požadavky na způsobilost pouze vlastník skupiny.

## [Odemknout rozšířené služby](#odemknout-rozšířené-služby)[](#odemknout-rozšířené-služby)

Pokud splňujete všechny [požadavky na způsobilost](#po%C5%BEadavky-na-zp%C5%AFsobilost) , můžete dokončit nastavení rozšířených služeb zadáním údajů o účtu a platebních informací. U her vlastněných skupinou může rozšířené služby odemknout pouze vlastník skupiny a onboardovat hru na ně.

Chcete-li odemknout a používat rozšířené služby:

1.

V [Kreativním panelu](https://create.roblox.com/dashboard/creations)  přejděte na Vytvoření  a vyberte hru.

2.

Přejděte na Rozšířené služby .

3.

Pokud jste ještě nezadali údaje o účtu a platební informace, klikněte na Přidat chybějící informace  v horním banneru.

1.

Zadejte informace o účtu. Pole Typ účtu , Typ daňového ID  a Daňové ID  jsou volitelná.

-

Můžete také přejít na Finance  ⟩ Informace o účtu  v sekci Rozšířené služby  pro správu informací o účtu. Na této stránce nemusíte aktualizovat nic jiného.

2.

Klikněte na Další .

3.

Zadejte platební metodu. Můžete zadat novou platební metodu nebo vybrat z dostupných platebních možností již spojených s vaším účtem Roblox.

-

Můžete také přejít na Finance  ⟩ Platby  pro přidání nových platebních metod, nebo přejít na Finance  ⟩ Fakturace  pro nastavení nové výchozí platební metody.

4.

Klikněte na Uložit .

##### Stav účtu

Váš účet pro rozšířené služby může mít jeden z následujících stavů:

| Stav | | Popis | | Požadovaná akce |
| Normální | | Můžete používat všechny funkce rozšířených služeb. | | Není vyžadována žádná akce. |
| --- | --- |
| Po splatnosti | | Váš účet je po splatnosti, protože vaše automatická platební metoda selhala. Roblox nabízí lhůtu sedmi dnů  před pozastavením vašeho účtu pro rozšířené služby. | | Změňte svou platební metodu a zkuste provést manuální platbu, nebo počkejte, až se Roblox pokusí znovu načíst vaši platební metodu po uplynutí lhůty. |
| Pozastaveno | | Nemůžete používat žádné placené rozšířené služby. Můžete však stále používat služby s výchozími limity. | | Opravit požadavky na způsobilost, přidat platnou platební metodu nebo ručně zaplatit dlužnou částku na vašem účtu. |

## [Aktivovat službu](#aktivovat-službu)[](#aktivovat-službu)

Chcete-li aktivovat službu:

1.

Přejděte na Rozšířené služby .

2.

Přepněte službu, kterou chcete aktivovat, na zapnuto.

3.

Zadejte měsíční rozpočet pro každý relevantní zdroj pod službou. Minimální měsíční rozpočet, který můžete nastavit, je 0,50 USD.

Vaše platební metoda bude účtována buď na konci měsíce, když je vygenerována faktura, nebo když vaše používání dosáhne 10 USD, podle toho, co nastane dříve.

Můžete kdykoli zvýšit nebo snížit měsíční rozpočet služby. Vaše služba je automaticky omezena, pokud snížíte svůj rozpočet na částku pod vaše aktuální měsíční používání, nebo pokud překročíte nastavený rozpočet.

Roblox vás upozorní e-mailem, když vaše používání dosáhne 80 % vašeho rozpočtu, a poté znovu, když dosáhne 100 %.

### [Rozšířené služby pro výpočet](#rozšířené-služby-pro-výpočet)[](#rozšířené-služby-pro-výpočet)

Každý herní server dostává výchozí množství CPU, které roste s každým hráčem, který se připojí. Rozšířené služby pro výpočet  více než zdvojnásobují CPU na hráče, které servery vaší hry dostávají.

Většina her na Robloxu z této služby nemá žádný prospěch, ale hry s těžkou fyzikou na straně serveru nebo které intenzivně využívají [serverovou autoritu](/docs/en-us/projects/server-authority)  narazí na stávající limity. Chcete-li zjistit, zda vaše hra může mít prospěch z rozšířených služeb pro výpočet :

-

Zkontrolujte [serverový heartbeat](/docs/en-us/performance-optimization/identify#server-compute)  pro trvalé poklesy pod 60 FPS.

-

Zkontrolujte využití CPU jádra na [panelu výkonu](/docs/en-us/production/analytics/performance#server-charts) .

Než zaplatíte za více CPU, zkuste [snížit práci, kterou vaše servery dělají](/docs/en-us/performance-optimization/improve) .

## [Správa fakturace](#správa-fakturace)[](#správa-fakturace)

Chcete-li přistupovat k panelu fakturace rozšířených služeb:

1.

Přejděte na Finance  ⟩ Fakturace .

2.

Vyberte kartu Cloudové služby , abyste zobrazili následující:

-

Váš čekající zůstatek, včetně nákladů za aktuální měsíc

-

Vaši historii fakturace, včetně všech aktivit fakturace rozšířených služeb napříč vašimi hrami

Pro podrobný rozpis vašich aktuálních čekajících nákladů klikněte na Zobrazit podrobnosti  vedle vaší platební metody. Pro podrobnou fakturu z předchozí faktury klikněte na Zobrazit fakturu  pod Historie fakturace .

## [Ceny služeb](#ceny-služeb)[](#ceny-služeb)

Podívejte se na následující tabulku pro ceny rozšířených služeb:

| Služba | |  | | Výchozí | | Rozšířené |
| [Paměťová úložiště](https://create.roblox.com/docs/cloud-services/memory-stores) | | Požadavky | | 1000 + (CCU × 120) požadavků za minutu | | 0,003 USD / 1M požadavků |
|  | | Úložiště | | 64 KB + (CCU × 1,2 KB) | | 0,10 USD / GB za hodinu¹ |
| [Syntéza řeči](https://create.roblox.com/docs/audio/objects#text-to-speech) | | Požadavky | | 1 + (CCU × 6) požadavků za minutu | | 5,00 USD / 1M požadavků |
| [Rozpoznávání řeči](https://create.roblox.com/docs/audio/objects#speech-to-text) | | Požadavky | | 1 + (CCU × 5) požadavků za minutu | | 1 USD / 1M požadavků |
| [Standardní datová úložiště](https://create.roblox.com/docs/cloud-services/data-stores) | | Získat | | 250 + (CCU * 40) požadavků za minutu | | 0,08 USD / 1M požadavků |
|  | | Nastavit | | 250 + (CCU * 20) požadavků za minutu | | 0,80 USD / 1M požadavků |
|  | | Seznam | | 10 + (CCU * 2) požadavků za minutu | | 0,60 USD / 1M požadavků |
|  | | Odstranit | | 100 + (CCU * 40) požadavků za minutu | | 0,80 USD / 1M požadavků |
| [Seřazená datová úložiště ](https://create.roblox.com/docs/cloud-services/data-stores) | | Získat | | 250 + (CCU * 40) požadavků za minutu | | 0,08 USD / 1M požadavků |
|  | | Nastavit | | 250 + (CCU * 20) požadavků za minutu | | 0,25 USD / 1M požadavků |
|  | | ZískatSeřazené | | 100 + (CCU * 2) požadavků za minutu | | 0,32 USD / 1M požadavků |
|  | | Odstranit | | 100 + (CCU * 40) požadavků za minutu | | 0,25 USD / 1M požadavků |
| [Úložiště datových úložišť ](https://create.roblox.com/docs/cloud-services/data-stores) | | Úložiště | | 100 MB + (1 MB * Počet hráčů za život) GB za měsíc | | 0,12 USD / GB za měsíc |
| [Výpočet ](https://create.roblox.com/docs/production/analytics/performance) | | CPU jádra | | Prvních 100K hodin hraní za měsíc bez poplatku (při registraci do rozšířených služeb pro výpočet) | | 0,001 USD / hodina hraní² |

 ¹ GB za hodinu = spotřeba úložiště vynásobená dobou. Například 100 GB hodin může odpovídat "100 GB × 1 hodina" nebo "200 GB × 0,5 hodiny".  ² Rozšířené služby pro výpočet jsou účtovány na základě toho, jak dlouho zůstává funkce aktivována, měřeno v minutách hraní. Protože aktivace funkce rezervuje další výpočetní kapacitu pro vaši hru, poplatky se uplatňují, kdykoli je funkce aktivní, i když není plně využita. Hodiny hraní se počítají jako součet všech trvání herních sezení. Například pokud 10 000 uživatelů hraje každé 1 hodinu, to odpovídá 10 000 hodinám hraní, což vede k poplatkům 10 USD nad zahrnutý měsíční limit 100 000 hodin hraní. Tyto limity a ceny se vztahují pouze na hry zaregistrované do rozšířených služeb pro výpočet. Hry, které se nezaregistrují, nadále dostávají neomezené hodiny hraní podle aktuálních výchozích limitů bez dalších poplatků.

## [Podporované země](#podporované-země)[](#podporované-země)

Rozšířené služby jsou k dispozici v následujících zemích:

| Země |
| Austrálie | | Německo | | Polsko |
| Rakousko | | Hongkong | | Portugalsko |
| Belgie | | Maďarsko | | Rumunsko |
| Brazílie | | Irská | | Singapur |
| Bulharsko | | Itálie | | Slovensko |
| Kanada | | Kazachstán | | Slovinsko |
| Chile | | Lotyšsko | | Jižní Afrika |
| Chorvatsko | | Litva | | Jižní Korea |
| Kipř | | Malajsie | | Španělsko |
| Česká republika | | Malta | | Švédsko |
| Dánsko | | Mexiko | | Švýcarsko |
| Estonsko | | Nizozemsko | | Thajsko |
| Finsko | | Nový Zéland | | Velká Británie |
| Francie | | Norsko | | Spojené státy |
| Gruzie | | Peru | |  |

## [Další lokalizace pro tuto stránku](#další-lokalizace-pro-tuto-stránku)[](#další-lokalizace-pro-tuto-stránku)

Pro další lokalizované verze této stránky, které nejsou k dispozici v jazykovém výběru na stránce, se podívejte na následující odkazy:

-

[Bulharština (български)](https://create.roblox.com/docs/bg-bg/cloud-services/extended-services)

-

[Chorvatština (hrvatski)](https://create.roblox.com/docs/hr-hr/cloud-services/extended-services)

-

[Čeština (čeština)](https://create.roblox.com/docs/cs-cz/cloud-services/extended-services)

-

[Dánština (dansk)](https://create.roblox.com/docs/da-dk/cloud-services/extended-services)

-

[Nizozemština (Nederlands)](https://create.roblox.com/docs/nl-nl/cloud-services/extended-services)

-

[Estonština (eesti)](https://create.roblox.com/docs/et-ee/cloud-services/extended-services)

-

[Finština (suomi)](https://create.roblox.com/docs/fi-fi/cloud-services/extended-services)

-

[Řečtina (Ελληνικά)](https://create.roblox.com/docs/el-gr/cloud-services/extended-services)

-

[Maďarština (magyar)](https://create.roblox.com/docs/hu-hu/cloud-services/extended-services)

-

[Irština (Gaeilge)](https://create.roblox.com/docs/ga-ie/cloud-services/extended-services)

-

[Lotyština (latviešu)](https://create.roblox.com/docs/lv-lv/cloud-services/extended-services)

-

[Litevština (lietuvių)](https://create.roblox.com/docs/lt-lt/cloud-services/extended-services)

-

[Maltština (Malti)](https://create.roblox.com/docs/mt-mt/cloud-services/extended-services)

-

[Portugalština - Portugalsko (português)](https://create.roblox.com/docs/pt-pt/cloud-services/extended-services)

-

[Rumunština (română)](https://create.roblox.com/docs/ro-ro/cloud-services/extended-services)

-

[Slovenština (slovenčina)](https://create.roblox.com/docs/sk-sk/cloud-services/extended-services)

-

[Slovinština (slovenščina)](https://create.roblox.com/docs/sl-si/cloud-services/extended-services)

-

[Švédština (svenska)](https://create.roblox.com/docs/sv-se/cloud-services/extended-services)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
