<!-- Source: https://create.roblox.com/docs/cs-cz/production/monetization -->

Monetizace | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)

# Monetizace

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Monetizace je součástí celkové struktury Robloxu, která poskytuje hodnotu tvůrcům. Existuje několik různých přístupů k monetizaci vašeho obsahu, včetně využití [předplatného](#p%C5%99edplatn%C3%A9) , účtování poplatku za přístup v [Robux](#placen%C3%BD-p%C5%99%C3%ADstup-v-robux)  nebo [místní měně](#placen%C3%BD-p%C5%99%C3%ADstup-v-m%C3%ADstn%C3%AD-m%C4%9Bn%C4%9B) , poskytování [předmětů nebo schopností, které si uživatelé mohou zakoupit](#v%C3%BDvoj%C3%A1%C5%99sk%C3%A9-produkty) , nabízení [privátních serverů](#priv%C3%A1tn%C3%AD-servery)  pro uživatele, aby mohli hrát jen s přáteli, a [prodeje modelů a pluginů](/docs/en-us/production/creator-store#distribute-and-sell-assets)  dalším tvůrcům na Creator Store.

Pokud se rozhodnete nabídnout zakoupitelný obsah, Roblox automaticky nezaznamenává informace o produktech nebo nákupech. Aby se předešlo ztrátě dat, musíte pečlivě uchovávat tato data pomocí [DataStoreService](/docs/en-us/reference/engine/classes/DataStoreService)  nebo jiného úložiště dat hostovaného mimo Roblox.

Pro podrobný pohled na navrhování optimálních monetizačních strategií pro vaši zkušenost, viz [Základy monetizace](/docs/en-us/production/game-design/monetization-foundations) .

## [Monetizační strategie](#monetizační-strategie)[](#monetizační-strategie)

Buďte opatrní při zavádění metod monetizace do vaší hry, protože naši uživatelé pravděpodobně ohodnotí  vaši hru negativně, pokud neschvalují vaše strategie. Také všichni vývojáři musí být transparentní ohledně jakékoli [monetizace založené na náhodě](/docs/en-us/production/monetization/paid-random-items)  a tyto mechaniky používat zodpovědně.

Některé populární monetizační strategie pro hry zdarma na jiných platformách nejsou doporučovány pro Roblox. Například mechaniky schůzek a časovače, které mohou být odstraněny nebo posunuty, mohou fungovat dobře na jiných platformách, ale tyto mechaniky jsou nepopulární mezi uživateli Robloxu, kteří mají problém s tím, že jejich zábava končí předčasně.

Následující doporučení osvědčených praktik jsou populární mezi předními vývojáři pro přizpůsobení monetizačních strategií platformě a publiku Robloxu.

Vezměte prosím na vědomí, že použitím těchto technik a úvah nemáte zaručeno, že budete schopni efektivně monetizovat svou hru. Pamatujte, že nemusíte mít žádné finanční cíle, abyste si užili vytváření hry na Robloxu.

### [Turisté a místní obyvatelé](#turisté-a-místní-obyvatelé)[](#turisté-a-místní-obyvatelé)

Může být užitečné myslet na uživatele Robloxu ve dvou kategoriích:

-

Turisté  obvykle skáčou z jedné hry do druhé, upřednostňují rozmanitost před hloubkou. Preferují předměty s okamžitými efekty, buď tím, že činí hru zábavnější, nebo tím, že se odlišují, což vyzývá ostatní uživatele, aby se ptali, jak a kde získali daný předmět.

-

Místní obyvatelé  se pravděpodobně zaměří na konkrétní hru nebo menší sadu her. Zapojí se hlouběji a obvykle tvoří téměř celou zapojenou uživatelskou základnu hry. Zajímají se více o předměty s dlouhodobými výhodami, jako je [battle pass](/docs/en-us/production/game-design/season-pass-design) .

Chcete-li se dozvědět více o tom, jak navrhnout svou hru s ohledem na uživatele Robloxu, viz [Navrhnout pro Roblox](/docs/en-us/production/game-design/design-for-roblox) .

### [Sociální funkce](#sociální-funkce)[](#sociální-funkce)

Uživatelé Robloxu mají tendenci si užívat hry, které zdůrazňují sociální interakci. Například mít předměty nebo události, které jsou k dispozici pouze po omezenou dobu , může vytvořit vzrušení kolem tohoto obsahu. Systém obchodu  povzbuzuje uživatele k interakci. Ačkoli oba systémy mohou být úspěšné samostatně, jsou obzvlášť efektivní, když jsou kombinovány.

### [Živé operace](#živé-operace)[](#živé-operace)

Podpora po spuštění je v mnoha ohledech snazší na Robloxu než na jiných platformách, protože můžete rychle vydávat aktualizace pro zlepšení vaší hry.

Časté  aktualizace obsahu mohou být užitečné, pokud chcete udržet zapojení uživatelů s vaší hrou v průběhu času. Uživatelé Robloxu jsou zvyklí na pravidelné aktualizace, a může být mnohem těžší znovu získat zájem uživatele než udržet aktivní zájem. Ideální je týdenní frekvence  aktualizací. Minimálně se snažte o měsíční aktualizace. Pro diskusi o frekvenci obsahu viz workshop [frekvence obsahu](/docs/en-us/production/game-design/content-updates) .

Při navrhování aktualizací se zaměřte na konkrétní téma . To usnadňuje uživatelům pochopit novou aktualizaci a říct, jaký obsah je nový, když se připojí. Také vám to pomůže koordinovat váš obsah a propagační materiály. Například, pokud přidáváte novou ZOO do vaší role-playing hry, ujistěte se, že veškerý nový obsah má nějakou souvislost s tématem ZOO.

Nebojte se nechat uživatele vydělat si přístup  k novému obsahu. Noví uživatelé se budou hrnout hrát nové aktualizace, ale pokud nebudou mít pocit, že něco dosáhli  ve hře, mohou brzy odejít. Můžete vytvořit pocit, že si uživatelé zaslouží aktualizaci buď monetizací obsahu aktualizace, nebo vytvořením podmínek pro hraní nového obsahu.

Chcete-li se dozvědět více o tom, jak navrhnout efektivní podporu po spuštění pro vaši hru, viz [Základy živých operací](/docs/en-us/production/game-design/liveops-essentials) .

## [Produkty](#produkty)[](#produkty)

### [Imersivní reklamy](#imersivní-reklamy)[](#imersivní-reklamy)

Systém [imersivních reklam](/docs/en-us/production/monetization/immersive-ads)  vám umožňuje vložit reklamní jednotky do vaší hry, které umožňují Robloxu programově poskytovat reklamní obsah od inzerentů vašim aktivním uživatelům.

![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/Overview-ImageAd.jpg) Formát obrazové reklamy

Formát portálové reklamy

### [Roblox Plus](#roblox-plus)[](#roblox-plus)

[Roblox Plus](/docs/en-us/production/monetization/roblox-plus)  vám umožňuje vydělávat prostřednictvím zvýšených nákupů ve hře, které jsou poháněny slevami pro uživatele dotovanými Robloxem, bonusy za registraci pro každého nového předplatitele, kterého přivedete, a zapojením do placených privátních serverů.

### [Předplatné](#předplatné)[](#předplatné)

[Předplatné](/docs/en-us/production/monetization/subscriptions)  v rámci her vám umožňuje nabízet uživatelům opakované výhody za měsíční poplatek.

![](https://prod.docsiteassets.roblox.com/assets/monetization/subscriptions/Example-Subscriptions.png) Příklady herních předplatných

### [Průchody](#průchody)[](#průchody)

[Průchod](/docs/en-us/production/monetization/passes)  vám umožňuje účtovat jednorázový poplatek v Robux , aby uživatelé mohli přistupovat k zvláštním privilegiím v rámci hry, jako je vstup do omezené oblasti, předmět pro avatara ve hře nebo trvalé vylepšení.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/passes/passes-sample.png)

### [Vývojářské produkty](#vývojářské-produkty)[](#vývojářské-produkty)

[Vývojářský produkt](/docs/en-us/production/monetization/developer-products)  je předmět nebo schopnost, kterou si uživatel může zakoupit více než jednou, například herní měnu, munici nebo lektvary. Můžete vyvolat nákupy, zaznamenávat je a získávat informace o produktech prostřednictvím skriptování.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/developer-products/Buy-Product-Example.jpg)

### [Spravované ceny](#spravované-ceny)[](#spravované-ceny)

[Spravované ceny](/docs/en-us/production/monetization/managed-pricing)  je jednotný systém, který spojuje [regionální ceny](/docs/en-us/production/monetization/regional-pricing)  a [optimalizaci cen](/docs/en-us/production/monetization/price-optimization)  na jednom místě. Přihlásíte se jednou, vyberete, které položky zahrnout, a Spravované ceny udržují vaše ceny optimalizované napříč produkty a regiony v průběhu času.

### [Optimalizace cen](#optimalizace-cen)[](#optimalizace-cen)

[Optimalizace cen](/docs/en-us/production/monetization/price-optimization)  vám umožňuje najít nejlepší cenové body pro vaše průchody a vývojářské produkty, což vám může pomoci vydělat více peněz v průběhu času, zatímco udržujete vaše ceny konkurenceschopné.

### [Placený přístup v Robux](#placený-přístup-v-robux)[](#placený-přístup-v-robux)

[Placený přístup v Robux](/docs/en-us/production/monetization/paid-access-robux)  vám umožňuje účtovat uživatelům jednorázový poplatek v Robux  za přístup k vaší hře. Někteří vývojáři dočasně používají tuto funkci k vytvoření uzavřené beta verze, kde mohou mít jejich nejvíce zapojení uživatelé předčasný přístup k hře a pomoci s testováním a zpětnou vazbou.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/paid-access/Buy-Access-Example.png)

### [Placený přístup v místní měně](#placený-přístup-v-místní-měně)[](#placený-přístup-v-místní-měně)

[Placený přístup v místní měně](/docs/en-us/production/monetization/paid-access-local-currency)  vám umožňuje účtovat uživatelům jednorázový poplatek v jejich místní měně  za přístup k vaší hře. Pokud jejich místní měna není k dispozici, účtují se v USD. Někteří vývojáři dočasně používají tuto funkci k vytvoření uzavřené beta verze, kde mohou mít jejich nejvíce zapojení uživatelé předčasný přístup k hře a pomoci s testováním a zpětnou vazbou.

### [Privátní servery](#privátní-servery)[](#privátní-servery)

[Privátní server](/docs/en-us/production/monetization/private-servers)  je funkce založená na předplatném, která umožňuje uživateli rozhodnout, kdo může hrát hru s nimi. Ačkoli mohou být privátní servery zdarma, můžete také použít privátní servery jako metodu monetizace tím, že účtujete uživatelům, kteří chtějí přístup k privátním serverům, měsíční poplatek v Robux .

### [Poplatky za katalog a provize](#poplatky-za-katalog-a-provize)[](#poplatky-za-katalog-a-provize)

Můžete vytvářet a prodávat doplňky a oblečení na Marketplace. Poté, co zaplatíte poplatek za nahrání a předložíte nový majetek k schválení, tým moderátorů zkontroluje váš majetek a, pokud je schválen, přidá váš majetek do katalogu.

Obdržíte [provizi](/docs/en-us/marketplace/marketplace-fees-and-commissions)  pokaždé, když uživatelé zakoupí váš katalogový předmět. Pokud uživatelé zakoupí váš katalogový předmět v rámci hry pomocí [menu pro inspekci avatara](/docs/en-us/players/avatar-inspect-menu)  nebo [služby pro úpravu avatarů](/docs/en-us/players/avatar-editor) , vlastník hry také obdrží provizi.

### [Pluginy a modely](#pluginy-a-modely)[](#pluginy-a-modely)

[Plugin](/docs/en-us/studio/plugins)  je rozšíření, které přidává další funkčnost do Studia, a [model](/docs/en-us/parts/models)  je typ opakovaně použitelných aktiv. Můžete obě nabídnout dalším tvůrcům na [Creator Store](/docs/en-us/production/creator-store)  zdarma, nebo je můžete prodávat za americké dolary  (minimální cena je 4,99 z a p l u g i n y a 2 , 99 za pluginy a 2,99 z a pl ug in y a 2 , 99  za modely). Roblox nabízí vedoucí podíl na příjmech z těchto prodejů, protože jsou odečteny pouze daně a poplatky za zpracování plateb. Pro více informací o prodeji pluginů a modelů viz [Creator Store - Distribuujte a prodávejte aktiva](/docs/en-us/production/creator-store#distribute-and-sell-assets) .

Na každou koupi se vztahuje 30denní zadržení. Roblox zadržuje váš podíl na prodeji po dobu 30 dnů, počínaje datem prodeje.

## [Směrnice](#směrnice)[](#směrnice)

Při navrhování a implementaci monetizačních produktů do vašich her zvažte následující směrnice, abyste zajistili, že vaše metody monetizace jsou vhodné pro všechny publika na platformě.

### [Prezentace produktů](#prezentace-produktů)[](#prezentace-produktů)

Aby byla zajištěna bezpečnost a spravedlnost, musíte prezentovat monetizační produkty způsobem, který je transparentní, čestný a uživatelsky přívětivý. Například, pokud nabízíte slevy, musí být skutečné  a spravedlivé :

-

Sleva není skutečná, pokud je předmět vždy "v akci" za stejnou částku Robux.

-

Sleva není spravedlivá, pokud je nabízena pouze na velmi krátkou dobu, což tlačí uživatele k tomu, aby co nejrychleji provedli nákup.

Uživatelé nesmí být nikdy uvedeni v omyl, zmatení nebo pod tlakem k nákupům způsoby, které nechtěli, a měli by mít vždy svobodu učinit jasnou, záměrnou volbu získat předplatné nebo utratit Robux za konkrétní předmět. Jako obecné vodítko existují některé praktiky, kterým se je třeba vyhnout za všech okolností při prezentaci monetizačních produktů vašemu publiku:

-

Neříkejte, že je předplatné nebo předmět téměř vyprodán nebo k dispozici pouze na krátkou dobu, pokud to není pravda.

-

Nepoužívejte odpočítávací časovač, který není přesný nebo se automaticky restartuje pro stejný předmět.

Například, pokud vaše hra zahrnuje "nabídku dne", která říká, že je k dispozici pouze 24 hodin, ale pak ukazujete stejnou zprávu uživatelům pokaždé, když se přihlásí, a nikdy se nezastaví, vytvořili jste falešný pocit naléhavosti, který není uživatelsky přívětivý.

### [Propagace pro globální publika](#propagace-pro-globální-publika)[](#propagace-pro-globální-publika)

Roblox je globální komunitou pro uživatele všech věkových kategorií, takže propagace ve vašich hrách by měla být z principu vhodná pro všechna publika. Pokud jsou některé monetizační produkty omezeny v určitých lokalitách, jako jsou placené náhodné předměty, Roblox poskytuje API [PolicyService](/docs/en-us/reference/engine/classes/PolicyService) , které vám pomůže zajistit, že tyto produkty jsou viditelné pouze pro oprávněné uživatele.

[PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  vrací, zda je uživatel oprávněn k určitým položkám nebo funkcím podle jejich umístění, věku a platformy. Musíte integrovat toto API do vaší hry, abyste splnili své povinnosti v oblasti souladu, včetně určení, zda je každý uživatel:

-

Oprávněn k nákupu předplatných nebo obchodních produktů.

-

Oprávněn k placeným náhodným předmětům, placenému obchodování s předměty nebo k vidění imersivních reklam.

Pokud může uživatel použít Robux nebo něco jiného, co bylo získáno pomocí Robux, k získání náhodné odměny, jste povinni použít [PolicyService](/docs/en-us/reference/engine/classes/PolicyService) , abyste zablokovali tuto funkci pro uživatele, kteří nemají povolení používat náhodné předměty výměnou za Robux.

Jako obecné vodítko se vyhněte používání naléhavých nebo naléhavých zpráv při interakci s nezletilými, protože jazyk s vysokým tlakem může být ohromující:

| ** Jazyk, kterému se vyhnout** | | ** Doporučené alternativy** |
| --- | --- |
| "ZÍSKEJTE TO NYNÍ" | | "Zobrazit předmět" |
| "POSLEDNÍ ŠANCE, JDI NYNÍ" | | "Zobrazit cenu" |
| "KUPTE PŘEDTÍM, NEŽ TO ZMIZÍ!" | | "Otevřít obchod" |

## [Další lokalizace pro tuto stránku](#další-lokalizace-pro-tuto-stránku)[](#další-lokalizace-pro-tuto-stránku)

Pro další lokalizované verze této stránky, které nejsou k dispozici v jazykovém výběru na stránce, viz následující odkazy:

-

[Bulharština (български)](https://create.roblox.com/docs/bg-bg/production/monetization)

-

[Chorvatština (hrvatski)](https://create.roblox.com/docs/hr-hr/production/monetization)

-

[Čeština (čeština)](https://create.roblox.com/docs/cs-cz/production/monetization)

-

[Dánština (dansk)](https://create.roblox.com/docs/da-dk/production/monetization)

-

[Nizozemština (Nederlands)](https://create.roblox.com/docs/nl-nl/production/monetization)

-

[Estonština (eesti)](https://create.roblox.com/docs/et-ee/production/monetization)

-

[Finština (suomi)](https://create.roblox.com/docs/fi-fi/production/monetization)

-

[Řečtina (Ελληνικά)](https://create.roblox.com/docs/el-gr/production/monetization)

-

[Maďarština (magyar)](https://create.roblox.com/docs/hu-hu/production/monetization)

-

[Irština (Gaeilge)](https://create.roblox.com/docs/ga-ie/production/monetization)

-

[Lotyština (latviešu)](https://create.roblox.com/docs/lv-lv/production/monetization)

-

[Litevština (lietuvių)](https://create.roblox.com/docs/lt-lt/production/monetization)

-

[Maltština (Malti)](https://create.roblox.com/docs/mt-mt/production/monetization)

-

[Portugalština - Portugalsko (português)](https://create.roblox.com/docs/pt-pt/production/monetization)

-

[Rumunština (română)](https://create.roblox.com/docs/ro-ro/production/monetization)

-

[Slovenština (slovenčina)](https://create.roblox.com/docs/sk-sk/production/monetization)

-

[Slovinština (slovenščina)](https://create.roblox.com/docs/sl-si/production/monetization)

-

[Švédština (svenska)](https://create.roblox.com/docs/sv-se/production/monetization)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
