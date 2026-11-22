<!-- Source: https://create.roblox.com/docs/sk-sk/cloud-services/extended-services -->

Rozšírené služby | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Cloud services](/docs/en-us/cloud-services/data-stores-vs-memory-stores)

# Rozšírené služby

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Rozšírené služby sú riešením, ktoré vám umožňuje spravovať používanie služieb a platby nad rámec predvolených limitov Robloxu. Zahrňuje úložiská dát, pamäťové úložiská, text na reč, reč na text a výpočty.

## [Požiadavky na oprávnenosť](#požiadavky-na-oprávnenosť)[](#požiadavky-na-oprávnenosť)

Aby ste mohli používať rozšírené služby, váš účet Roblox musí:

-

Byť [overený ID](/docs/en-us/production/publishing/account-verification#verify-through-government-id)  a mať 18+ rokov.

-

Byť umiestnený v [podporovanej krajine](#podporovan%C3%A9-krajiny) .

-

Mať platnú e-mailovú adresu priradenú k účtu.

-

Nebyť momentálne zablokovaný alebo moderovaný.

-

Akceptovať a dodržiavať [podmienky služby](https://en.help.roblox.com/hc/articles/37967848292500) .

Pre skupinové účty musí splniť požiadavky na oprávnenosť iba vlastník skupiny.

## [Odomknutie rozšírených služieb](#odomknutie-rozšírených-služieb)[](#odomknutie-rozšírených-služieb)

Ak spĺňate všetky [požiadavky na oprávnenosť](#po%C5%BEiadavky-na-opr%C3%A1vnenos%C5%A5) , môžete dokončiť nastavenie rozšírených služieb zadaním údajov o účte a platobných informácií. Pre hry vlastnené skupinou môže rozšírené služby odomknúť iba vlastník skupiny a onboardovať hru na ne.

Na odomknutie a používanie rozšírených služieb:

1.

V [Creator Dashboard](https://create.roblox.com/dashboard/creations)  prejdite na Vytvorenia  a vyberte hru.

2.

Prejdite na Rozšírené služby .

3.

Ak ste ešte nezadali údaje o účte a platobné informácie, kliknite na Pridať chýbajúce informácie  na hornom banneri.

1.

Zadajte svoje údaje o účte. Polia Typ účtu , Typ daňového ID  a Daňové ID  sú voliteľné.

-

Môžete tiež prejsť na Financie  ⟩ Informácie o účte  v sekcii Rozšírené služby , aby ste spravovali svoje údaje o účte. Na tejto stránke nemusíte aktualizovať nič iné.

2.

Kliknite na Ďalej .

3.

Zadajte spôsob platby. Môžete zadať nový spôsob platby alebo vybrať z dostupných platobných možností už priradených k vášmu účtu Roblox.

-

Môžete tiež prejsť na Financie  ⟩ Platby , aby ste pridali nové spôsoby platby, alebo prejsť na Financie  ⟩ Fakturácia , aby ste nastavili nový predvolený spôsob platby.

4.

Kliknite na Uložiť .

##### Stav účtu

Váš účet rozšírených služieb môže mať jeden z nasledujúcich stavov:

| Stav | | Popis | | Požadovaná akcia |
| Normálny | | Môžete používať všetky funkcie rozšírených služieb. | | Nie je potrebná žiadna akcia. |
| --- | --- |
| Po termíne | | Váš účet je po termíne, pretože váš automatický spôsob platby zlyhal. Roblox ponúka lehotu sedem dní  pred pozastavením vášho účtu rozšírených služieb. | | Zmeňte svoj spôsob platby a skúste manuálnu platbu, alebo počkajte, kým sa Roblox pokúsi znova naúčtovať váš spôsob platby po uplynutí lehoty. |
| Pozastavený | | Nemôžete používať žiadne platené rozšírené služby. Môžete však stále používať služby s predvolenými limitmi. | | Opraviť svoje požiadavky na oprávnenosť, pridať platný spôsob platby alebo manuálne zaplatiť zostatok na účte po termíne. |

## [Aktivácia služby](#aktivácia-služby)[](#aktivácia-služby)

Ak chcete aktivovať službu:

1.

Prejdite na Rozšírené služby .

2.

Prepnite službu, ktorú chcete aktivovať.

3.

Zadajte mesačný rozpočet pre každý relevantný zdroj pod službou. Minimálny mesačný rozpočet, ktorý môžete nastaviť, je 0,50 USD.

Váš spôsob platby bude zaúčtovaný buď na konci mesiaca, keď sa vygeneruje faktúra, alebo keď vaše používanie dosiahne 10 USD, podľa toho, čo nastane skôr.

Môžete kedykoľvek zvýšiť alebo znížiť mesačný rozpočet služby. Vaša služba bude automaticky obmedzená, ak znížite svoj rozpočet na sumu nižšiu ako vaše aktuálne používanie za mesiac, alebo ak prekročíte nastavený rozpočet.

Roblox vás upozorní e-mailom, keď vaše používanie dosiahne 80% vášho rozpočtu, a potom znova, keď dosiahne 100%.

### [Rozšírené služby pre výpočty](#rozšírené-služby-pre-výpočty)[](#rozšírené-služby-pre-výpočty)

Každý herný server dostáva predvolený objem CPU, ktorý rastie s každým hráčom, ktorý sa pripojí. Rozšírené služby pre výpočty  viac ako zdvojnásobujú CPU na hráča, ktoré vaše herné servery dostávajú.

Väčšina hier na Robloxu z tejto služby nemá žiadny prospech, ale hry s ťažkou serverovou fyzikou alebo ktoré intenzívne využívajú [serverovú autoritu](/docs/en-us/projects/server-authority)  narazia na existujúce limity. Ak chcete zistiť, či vaša hra môže mať prospech z rozšírených služieb pre výpočty :

-

Skontrolujte [serverový heartbeat](/docs/en-us/performance-optimization/identify#server-compute)  na pretrvávajúce poklesy pod 60 FPS.

-

Skontrolujte využitie CPU jadra na [paneli výkonu](/docs/en-us/production/analytics/performance#server-charts) .

Predtým, ako zaplatíte za viac CPU, skúste [znižiť prácu, ktorú vaše servery vykonávajú](/docs/en-us/performance-optimization/improve) .

## [Správa fakturácie](#správa-fakturácie)[](#správa-fakturácie)

Ak chcete získať prístup k panelu fakturácie rozšírených služieb:

1.

Prejdite na Financie  ⟩ Fakturácia .

2.

Vyberte kartu Cloudové služby , aby ste zobrazili nasledujúce:

-

Váš čakajúci zostatok, vrátane nákladov za mesiac

-

Vašu históriu fakturácie, vrátane všetkých aktivít fakturácie rozšírených služieb naprieč vašimi hrami

Pre podrobný prehľad vašich aktuálnych čakajúcich nákladov kliknite na Zobraziť podrobnosti  vedľa vášho spôsobu platby. Pre podrobnú faktúru predchádzajúcej faktúry kliknite na Zobraziť faktúru  pod História fakturácie .

## [Ceny služieb](#ceny-služieb)[](#ceny-služieb)

Pozrite si nasledujúcu tabuľku s cenami rozšírených služieb:

| Služba | |  | | Predvolené | | Rozšírené |
| [Pamäťové úložiská](https://create.roblox.com/docs/cloud-services/memory-stores) | | Žiadosti | | 1000 + (CCU × 120) žiadostí za minútu | | 0,003 USD / 1M žiadostí |
|  | | Úložisko | | 64 KB + (CCU × 1,2 KB) | | 0,10 USD / GB za hodinu¹ |
| [Text na reč](https://create.roblox.com/docs/audio/objects#text-to-speech) | | Žiadosti | | 1 + (CCU × 6) žiadostí za minútu | | 5,00 USD / 1M žiadostí |
| [Reč na text](https://create.roblox.com/docs/audio/objects#speech-to-text) | | Žiadosti | | 1 + (CCU × 5) žiadostí za minútu | | 1 USD / 1M žiadostí |
| [Štandardné úložiská dát](https://create.roblox.com/docs/cloud-services/data-stores) | | Získať | | 250 + (CCU * 40) žiadostí za minútu | | 0,08 USD / 1M žiadostí |
|  | | Nastaviť | | 250 + (CCU * 20) žiadostí za minútu | | 0,80 USD / 1M žiadostí |
|  | | Zoznam | | 10 + (CCU * 2) žiadostí za minútu | | 0,60 USD / 1M žiadostí |
|  | | Odstrániť | | 100 + (CCU * 40) žiadostí za minútu | | 0,80 USD / 1M žiadostí |
| [Usporiadané úložiská dát](https://create.roblox.com/docs/cloud-services/data-stores) | | Získať | | 250 + (CCU * 40) žiadostí za minútu | | 0,08 USD / 1M žiadostí |
|  | | Nastaviť | | 250 + (CCU * 20) žiadostí za minútu | | 0,25 USD / 1M žiadostí |
|  | | ZískaťZoradené | | 100 + (CCU * 2) žiadostí za minútu | | 0,32 USD / 1M žiadostí |
|  | | Odstrániť | | 100 + (CCU * 40) žiadostí za minútu | | 0,25 USD / 1M žiadostí |
| [Úložisko dát](https://create.roblox.com/docs/cloud-services/data-stores) | | Úložisko | | 100 MB + (1 MB * Počet hráčov) GB za mesiac | | 0,12 USD / GB za mesiac |
| [Výpočty](https://create.roblox.com/docs/production/analytics/performance) | | CPU jadrá | | Prvých 100K hodín hrania za mesiac bez poplatku (pri zapísaní do rozšírených služieb pre výpočty) | | 0,001 USD / hodina hrania² |

 ¹ GB za hodinu = spotreba úložiska vynásobená množstvom času. Napríklad, 100 GB hodín môže zodpovedať "100 GB × 1 hodina" alebo "200 GB × 0,5 hodiny".  ² Rozšírené služby pre výpočty sú fakturované na základe toho, ako dlho je funkcia povolená, merané v minútach hrania. Pretože povolenie funkcie rezervuje dodatočnú výpočtovú kapacitu pre vašu hru, poplatky sa uplatňujú vždy, keď je funkcia aktívna, aj keď dodatočné výpočty nie sú úplne spotrebované. Hodiny hrania sa počítajú ako súčet všetkých trvaní relácií hráčov. Napríklad, ak 10 000 používateľov hrá každé 1 hodinu, to predstavuje 10 000 hodín hrania, čo vedie k poplatkom vo výške 10 USD nad zahrnutý mesačný limit 100 000 hodín hrania. Tieto limity a ceny sa vzťahujú iba na hry zapísané do rozšírených služieb pre výpočty. Hry, ktoré sa nezapíšu, naďalej dostávajú neobmedzené hodiny hrania pod aktuálnymi predvolenými limitmi bez ďalších poplatkov.

## [Podporované krajiny](#podporované-krajiny)[](#podporované-krajiny)

Rozšírené služby sú dostupné v nasledujúcich krajinách:

| Krajina |
| Austrália | | Nemecko | | Poľsko |
| Rakúsko | | Hongkong | | Portugalsko |
| Belgicko | | Maďarsko | | Rumunsko |
| Brazil | | Írsko | | Singapur |
| Bulharsko | | Taliansko | | Slovensko |
| Kanada | | Kazachstan | | Slovinsko |
| Čile | | Lotyšsko | | Južná Afrika |
| Chorvátsko | | Litva | | Južná Kórea |
| Cyprus | | Malajzia | | Španielsko |
| Česká republika | | Malta | | Švédsko |
| Dánsko | | Mexiko | | Švajčiarsko |
| Estónia | | Holandsko | | Thajsko |
| Fínsko | | Nový Zéland | | Veľká Británia |
| Francúzsko | | Nórsko | | Spojené štáty |
| Gruzínsko | | Peru | |  |

## [Ďalšie lokalizácie pre túto stránku](#ďalšie-lokalizácie-pre-túto-stránku)[](#ďalšie-lokalizácie-pre-túto-stránku)

Pre ďalšie lokalizované verzie tejto stránky, ktoré nie sú dostupné v jazykovom výbere stránky, si pozrite nasledujúce odkazy:

-

[Bulharčina (български)](https://create.roblox.com/docs/bg-bg/cloud-services/extended-services)

-

[Chorvátčina (hrvatski)](https://create.roblox.com/docs/hr-hr/cloud-services/extended-services)

-

[Čeština (čeština)](https://create.roblox.com/docs/cs-cz/cloud-services/extended-services)

-

[Dánčina (dansk)](https://create.roblox.com/docs/da-dk/cloud-services/extended-services)

-

[Holandčina (Nederlands)](https://create.roblox.com/docs/nl-nl/cloud-services/extended-services)

-

[Estónčina (eesti)](https://create.roblox.com/docs/et-ee/cloud-services/extended-services)

-

[Fínčina (suomi)](https://create.roblox.com/docs/fi-fi/cloud-services/extended-services)

-

[Gréčtina (Ελληνικά)](https://create.roblox.com/docs/el-gr/cloud-services/extended-services)

-

[Maďarčina (magyar)](https://create.roblox.com/docs/hu-hu/cloud-services/extended-services)

-

[Írčina (Gaeilge)](https://create.roblox.com/docs/ga-ie/cloud-services/extended-services)

-

[Lotyština (latviešu)](https://create.roblox.com/docs/lv-lv/cloud-services/extended-services)

-

[Litovčina (lietuvių)](https://create.roblox.com/docs/lt-lt/cloud-services/extended-services)

-

[Maltčina (Malti)](https://create.roblox.com/docs/mt-mt/cloud-services/extended-services)

-

[Portugalčina - Portugalsko (português)](https://create.roblox.com/docs/pt-pt/cloud-services/extended-services)

-

[Rumunčina (română)](https://create.roblox.com/docs/ro-ro/cloud-services/extended-services)

-

[Slovenčina (slovenčina)](https://create.roblox.com/docs/sk-sk/cloud-services/extended-services)

-

[Slovinčina (slovenščina)](https://create.roblox.com/docs/sl-si/cloud-services/extended-services)

-

[Švédčina (svenska)](https://create.roblox.com/docs/sv-se/cloud-services/extended-services)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
