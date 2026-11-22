<!-- Source: https://create.roblox.com/docs/sk-sk/production/monetization -->

Monetizácia | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)

# Monetizácia

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Monetizácia je súčasťou celkovej štruktúry Robloxu, ktorá poskytuje hodnotu tvorcom. Existuje niekoľko rôznych prístupov k monetizácii vášho obsahu, vrátane využívania [predplatného](#predplatn%C3%A9) , účtovania poplatku za prístup v [Robux](#platen%C3%BD-pr%C3%ADstup-v-robux)  alebo [miestnej mene](#platen%C3%BD-pr%C3%ADstup-v-miestnej-mene) , poskytovania [položiek alebo schopností, ktoré si môžu používatelia zakúpiť](#v%C3%BDvoj%C3%A1rske-produkty) , ponúkania [súkromných serverov](#s%C3%BAkromn%C3%A9-servery)  pre používateľov, aby mohli hrať len s priateľmi, a [predaja modelov a pluginov](/docs/en-us/production/creator-store#distribute-and-sell-assets)  iným tvorcom na Creator Store.

Ak sa rozhodnete ponúknuť zakúpiteľný obsah, Roblox automaticky nezaznamenáva informácie o produktoch alebo nákupoch. Aby ste predišli strate údajov, musíte tieto údaje starostlivo uchovávať pomocou [DataStoreService](/docs/en-us/reference/engine/classes/DataStoreService)  alebo inej služby na ukladanie údajov hostenej mimo Roblox.

Pre podrobný pohľad na navrhovanie optimálnych monetizačných stratégií pre vašu skúsenosť si pozrite [Základy monetizácie](/docs/en-us/production/game-design/monetization-foundations) .

## [Monetizačné stratégie](#monetizačné-stratégie)[](#monetizačné-stratégie)

Buďte opatrní pri monetizačných metódach, ktoré zavádzate do svojej hry, pretože naši používatelia pravdepodobne odhlasujú  vašu hru, ak neschvália vaše stratégie. Taktiež všetci vývojári musia byť transparentní voči akýmkoľvek [monetizáciám založeným na náhode](/docs/en-us/production/monetization/paid-random-items)  a tieto mechaniky používať zodpovedne.

Niektoré populárne monetizačné stratégie pre hry s bezplatným hraním na iných platformách sa neodporúčajú pre Roblox. Napríklad mechaniky plánovania a časovače, ktoré môžu byť odstránené alebo posunuté, môžu fungovať dobre na iných platformách, ale tieto mechaniky sú nepopulárne medzi používateľmi Robloxu, ktorí majú problém s tým, že ich zábava sa predčasne končí.

Nasledujúce odporúčania osvedčených postupov sú populárne medzi najlepšími vývojármi na prispôsobenie monetizačných stratégií platforme a publiku Roblox.

Upozorňujeme, že aplikovaním týchto techník a úvah nie je zaručené, že budete schopní efektívne monetizovať svoju hru. Pamätajte, že na to, aby ste sa bavili pri vytváraní hry Roblox, nemusíte mať žiadne finančné ciele.

### [Turisti a miestni](#turisti-a-miestni)[](#turisti-a-miestni)

Môže byť užitočné myslieť na používateľov Robloxu v dvoch kategóriách:

-

Turisti  zvyčajne preskakujú z jednej hry do druhej, pričom uprednostňujú rozmanitosť pred hĺbkou. Preferujú položky s okamžitými účinkami, buď tým, že robia hru zábavnejšou, alebo tým, že sa odlišujú, čo vyzýva ostatných používateľov, aby sa pýtali, ako a kde získali danú položku.

-

Miestni  sú pravdepodobnejšie zameraní na konkrétnu hru alebo menšiu sadu hier. Hlbšie sa zapájajú a zvyčajne tvoria takmer celú angažovanú používateľskú základňu hry. Viac ich zaujímajú položky s dlhodobými výhodami, ako je [battle pass](/docs/en-us/production/game-design/season-pass-design) .

Ak sa chcete dozvedieť viac o tom, ako navrhnúť svoju hru s ohľadom na používateľov Robloxu, pozrite si [Navrhnúť pre Roblox](/docs/en-us/production/game-design/design-for-roblox) .

### [Sociálne funkcie](#sociálne-funkcie)[](#sociálne-funkcie)

Používatelia Robloxu majú tendenciu si užívať hry, ktoré zdôrazňujú sociálnu interakciu. Napríklad mať položky alebo udalosti, ktoré sú k dispozícii len na obmedzený čas , môže vytvoriť vzrušenie okolo tohto obsahu. Obchodný  systém povzbudzuje používateľov k interakcii. Hoci oba systémy môžu byť úspešné samostatne, sú obzvlášť účinné, keď sú kombinované.

### [Živé operácie](#živé-operácie)[](#živé-operácie)

Podpora po spustení je v mnohých ohľadoch jednoduchšia na Roblox než na iných platformách, pretože môžete rýchlo posielať aktualizácie na zlepšenie vašej hry.

Časté  aktualizácie obsahu môžu byť užitočné, ak chcete udržať angažovanosť s vašou hrou v priebehu času. Používatelia Robloxu sú zvyknutí na pravidelné aktualizácie, a môže byť oveľa ťažšie získať záujem používateľa späť, než udržať aktívnych. Týždenný cyklus  aktualizácií je ideálny. Minimálne sa snažte o mesačné aktualizácie. Pre diskusiu o cykle obsahu si pozrite Level Up [workshop o cykle obsahu](/docs/en-us/production/game-design/content-updates) .

Pri navrhovaní aktualizácií sa sústreďte na konkrétnu tému . To uľahčuje používateľom pochopiť novú aktualizáciu a zistiť, aký obsah je nový, keď sa pripoja. Pomáha vám to tiež koordinovať váš obsah a propagačné aktíva. Napríklad, ak pridávate novú ZOO do svojej hry na hranie rolí, uistite sa, že všetok nový obsah má nejaké spojenie s témou ZOO.

Nebojte sa nechať používateľov získať svoj prístup  k novému obsahu. Noví používatelia sa budú hrnúť, aby hrali nové aktualizácie, ale ak nemajú pocit, že v hre dosiahli  niečo, môžu sa čoskoro odhlásiť. Môžete vytvoriť pocit získania aktualizácie buď monetizovaním obsahu aktualizácie, alebo vytvorením predpokladových podmienok na hranie nového obsahu.

Ak sa chcete dozvedieť viac o tom, ako navrhnúť efektívnu podporu po spustení pre vašu hru, pozrite si [Základy živých operácií](/docs/en-us/production/game-design/liveops-essentials) .

## [Produkty](#produkty)[](#produkty)

### [Pohlcujúce reklamy](#pohlcujúce-reklamy)[](#pohlcujúce-reklamy)

Systém [pohlcujúcich reklám](/docs/en-us/production/monetization/immersive-ads)  vám umožňuje vložiť reklamné jednotky do vašej hry, ktoré umožňujú Robloxu programaticky poskytovať reklamný obsah od inzerentov vašim aktívnym používateľom.

![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/Overview-ImageAd.jpg) Formát obrazovej reklamy

Formát portálovej reklamy

### [Roblox Plus](#roblox-plus)[](#roblox-plus)

[Roblox Plus](/docs/en-us/production/monetization/roblox-plus)  vám umožňuje zarábať prostredníctvom zvýšených nákupov v hre, ktoré sú poháňané zľavami pre používateľov dotovanými Robloxom, bonusmi za registráciu pre každého nového predplatiteľa, ktorého privediete, a angažovaním sa v platených súkromných serveroch.

### [Predplatné](#predplatné)[](#predplatné)

[Predplatné](/docs/en-us/production/monetization/subscriptions)  v hrách vám umožňuje ponúknuť používateľom opakujúce sa výhody za mesačný poplatok.

![](https://prod.docsiteassets.roblox.com/assets/monetization/subscriptions/Example-Subscriptions.png) Príklady herných predplatných

### [Priepustky](#priepustky)[](#priepustky)

[Priepustka](/docs/en-us/production/monetization/passes)  vám umožňuje účtovať jednorazový poplatok v Robux , aby používatelia mohli získať špeciálne privilégiá v hre, ako je vstup do obmedzenej oblasti, položka avatara v hre alebo trvalé vylepšenie.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/passes/passes-sample.png)

### [Vývojárske produkty](#vývojárske-produkty)[](#vývojárske-produkty)

[Vývojársky produkt](/docs/en-us/production/monetization/developer-products)  je položka alebo schopnosť, ktorú si môže používateľ zakúpiť viac ako raz, ako napríklad herná mena, munícia alebo lektvary. Môžete vyzvať k nákupom, zaznamenávať ich a získať informácie o produktoch prostredníctvom skriptovania.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/developer-products/Buy-Product-Example.jpg)

### [Spravované ceny](#spravované-ceny)[](#spravované-ceny)

[Spravované ceny](/docs/en-us/production/monetization/managed-pricing)  je unified systém, ktorý spája [regionálne ceny](/docs/en-us/production/monetization/regional-pricing)  a [optimalizáciu cien](/docs/en-us/production/monetization/price-optimization)  na jednom mieste. Raz sa prihlásite, vyberiete, ktoré položky zahrnúť, a spravované ceny udržujú vaše ceny optimalizované naprieč produktmi a regiónmi v priebehu času.

### [Optimalizácia cien](#optimalizácia-cien)[](#optimalizácia-cien)

[Optimalizácia cien](/docs/en-us/production/monetization/price-optimization)  vám umožňuje nájsť najlepšie cenové body pre vaše priepustky a vývojárske produkty, čo vám môže pomôcť zarábať viac peňazí v priebehu času, pričom si udržíte konkurencieschopné ceny.

### [Platený prístup v Robux](#platený-prístup-v-robux)[](#platený-prístup-v-robux)

[Platený prístup v Robux](/docs/en-us/production/monetization/paid-access-robux)  vám umožňuje účtovať používateľom jednorazový poplatok v Robux  za prístup k vašej hre. Niektorí vývojári dočasne používajú túto funkciu na vytvorenie uzavretého beta testovania, kde môžu mať ich najangažovanejší používatelia skorý prístup k hre a pomôcť s testovaním a spätnou väzbou.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/paid-access/Buy-Access-Example.png)

### [Platený prístup v miestnej mene](#platený-prístup-v-miestnej-mene)[](#platený-prístup-v-miestnej-mene)

[Platený prístup v miestnej mene](/docs/en-us/production/monetization/paid-access-local-currency)  vám umožňuje účtovať používateľom jednorazový poplatok v ich miestnej mene  za prístup k vašej hre. Ak ich miestna mena nie je k dispozícii, účtujú sa v USD. Niektorí vývojári dočasne používajú túto funkciu na vytvorenie uzavretého beta testovania, kde môžu mať ich najangažovanejší používatelia skorý prístup k hre a pomôcť s testovaním a spätnou väzbou.

### [Súkromné servery](#súkromné-servery)[](#súkromné-servery)

[Súkromný server](/docs/en-us/production/monetization/private-servers)  je funkcia založená na predplatnom, ktorá umožňuje používateľovi rozhodnúť, kto môže hrať hru s nimi. Hoci súkromné servery môžu byť zadarmo, môžete ich tiež použiť ako metódu monetizácie účtovaním používateľom, ktorí chcú získať prístup k súkromným serverom, mesačný poplatok v Robux .

### [Poplatky a provízie za katalóg](#poplatky-a-provízie-za-katalóg)[](#poplatky-a-provízie-za-katalóg)

Môžete vytvárať a predávať doplnky a oblečenie na trhu. Po zaplatení poplatku za nahrávanie a predložení nového aktíva na schválenie tím moderátorov preskúma vaše aktívum a, ak je schválené, pridá vaše aktívum do katalógu.

Každýkrát, keď používatelia zakúpia vašu položku v katalógu, dostanete [províziu](/docs/en-us/marketplace/marketplace-fees-and-commissions) . Ak používatelia zakúpia vašu položku v katalógu v hre pomocou [menu na kontrolu avatara](/docs/en-us/players/avatar-inspect-menu)  alebo [služby editora avatara](/docs/en-us/players/avatar-editor) , majiteľ hry tiež dostane províziu.

### [Pluginy a modely](#pluginy-a-modely)[](#pluginy-a-modely)

[Plugin](/docs/en-us/studio/plugins)  je rozšírenie, ktoré pridáva ďalšiu funkčnosť do Studio, a [model](/docs/en-us/parts/models)  je typ opakovateľného aktíva. Môžete oboje ponúknuť iným tvorcom na [Creator Store](/docs/en-us/production/creator-store)  zadarmo, alebo ich môžete predávať za americké doláre  (minimálna cena je 4,99 USD za pluginy a 2,99 USD za modely). Roblox ponúka vedúci podiel na príjmoch z týchto predajov, pretože sa odpočítavajú len dane a poplatky za spracovanie platieb. Pre viac informácií o predaji pluginov a modelov si pozrite [Creator Store - Distribuovať a predávať aktíva](/docs/en-us/production/creator-store#distribute-and-sell-assets) .

Na každú kúpu sa vzťahuje 30-dňový zadržovací hold. Roblox zadrží váš podiel z predaja na 30 dní, počnúc dňom predaja.

## [Pokyny](#pokyny)[](#pokyny)

Pri navrhovaní a implementácii monetizačných produktov do vašich hier zvážte nasledujúce pokyny, aby ste zabezpečili, že vaše metódy monetizácie sú vhodné pre všetky publikum na platforme.

### [Predstavovanie produktov](#predstavovanie-produktov)[](#predstavovanie-produktov)

Aby ste udržali bezpečnosť a spravodlivosť, musíte prezentovať monetizačné produkty spôsobom, ktorý je transparentný, čestný a priateľský k používateľom. Napríklad, ak ponúkate zľavy, musia byť skutočné  a spravodlivé :

-

Zľava nie je skutočná, ak je položka vždy "v akcii" za rovnakú sumu Robux.

-

Zľava nie je spravodlivá, ak je ponúkaná len na veľmi krátky čas, čím tlačí používateľov, aby uskutočnili nákup čo najrýchlejšie.

Používatelia nikdy nesmú byť uvedení do omylu, zmätku alebo nátlaku na nákupy spôsobmi, ktoré nemali v úmysle, a mali by mať vždy slobodu urobiť jasný, zámerný výber na získanie predplatného alebo na utratenie Robux za konkrétnu položku. Ako všeobecné usmernenie existujú niektoré praktiky, ktorým sa treba vyhnúť za každých okolností pri prezentovaní monetizačných produktov vašemu publiku:

-

Nezavádzajte, že predplatné alebo položka sú takmer vypredané alebo sú k dispozícii len na krátky čas, ak to nie je pravda.

-

Nepoužívajte odpočítavací časovač, ktorý nie je presný alebo sa automaticky reštartuje pre tú istú položku.

Napríklad, ak vaša hra obsahuje "ponuku dňa", ktorá hovorí, že je k dispozícii len 24 hodín, ale potom ukazujete rovnakú správu používateľom zakaždým, keď sa prihlásia, a nikdy sa neprestáva byť k dispozícii, vytvorili ste falošný pocit naliehavosti, ktorý nie je priateľský k používateľom.

### [Propagácia globálnym publikám](#propagácia-globálnym-publikám)[](#propagácia-globálnym-publikám)

Roblox je globálna komunita pre používateľov všetkých vekových kategórií, takže propagácie vo vašich hrách by mali byť vhodné pre všetky publikum ako predvolené. Ak sú určité monetizačné produkty obmedzené v určitých lokalitách, ako sú platené náhodné položky, Roblox poskytuje API [PolicyService](/docs/en-us/reference/engine/classes/PolicyService) , aby vám pomohol zabezpečiť, že tieto produkty sú viditeľné len pre oprávnených používateľov.

[PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  vracia, či je používateľ oprávnený na konkrétne položky alebo funkcie podľa ich polohy, veku a platformy. Musíte integrovať toto API do vašej hry, aby ste splnili svoje povinnosti v oblasti dodržiavania predpisov, vrátane určenia, či je každý používateľ:

-

Oprávnený na nákup predplatného alebo obchodných produktov.

-

Oprávnený na platené náhodné položky, platené obchodovanie s položkami alebo na zobrazenie pohlcujúcich reklám.

Ak môže používateľ použiť Robux alebo niečo iné, čo bolo získané pomocou Robux, na získanie náhodnej odmeny, ste povinní použiť [PolicyService](/docs/en-us/reference/engine/classes/PolicyService) , aby ste zablokovali túto funkciu pre používateľov, ktorí nemajú povolené používať náhodné položky výmenou za Robux.

Ako všeobecné usmernenie sa vyhnite používaniu naliehavých alebo nátlakových správ pri interakcii s maloletými, pretože jazyk s vysokým tlakom môže byť ohromujúci:

| ** Jazyk, ktorému sa treba vyhnúť** | | ** Odporúčané alternatívy** |
| --- | --- |
| "ZÍSKAJTE TO TERAZ" | | "Zobraziť položku" |
| "POSLEDNÁ ŠANCA, KONAJTE TERAZ" | | "Pozrieť cenu" |
| "KÚPTE PREDTÝM, NEŽ TO ZMIZNE!" | | "Otvorené obchody" |

## [Ďalšie lokalizácie pre túto stránku](#ďalšie-lokalizácie-pre-túto-stránku)[](#ďalšie-lokalizácie-pre-túto-stránku)

Pre ďalšie lokalizované verzie tejto stránky, ktoré nie sú k dispozícii v jazykovom výbere stránky, si pozrite nasledujúce odkazy:

-

[Bulharčina (български)](https://create.roblox.com/docs/bg-bg/production/monetization)

-

[Chorvátčina (hrvatski)](https://create.roblox.com/docs/hr-hr/production/monetization)

-

[Čeština (čeština)](https://create.roblox.com/docs/cs-cz/production/monetization)

-

[Dánčina (dansk)](https://create.roblox.com/docs/da-dk/production/monetization)

-

[Holandčina (Nederlands)](https://create.roblox.com/docs/nl-nl/production/monetization)

-

[Estónčina (eesti)](https://create.roblox.com/docs/et-ee/production/monetization)

-

[Fínčina (suomi)](https://create.roblox.com/docs/fi-fi/production/monetization)

-

[Gréčtina (Ελληνικά)](https://create.roblox.com/docs/el-gr/production/monetization)

-

[Maďarčina (magyar)](https://create.roblox.com/docs/hu-hu/production/monetization)

-

[Írčina (Gaeilge)](https://create.roblox.com/docs/ga-ie/production/monetization)

-

[Lotyština (latviešu)](https://create.roblox.com/docs/lv-lv/production/monetization)

-

[Litovčina (lietuvių)](https://create.roblox.com/docs/lt-lt/production/monetization)

-

[Maltčina (Malti)](https://create.roblox.com/docs/mt-mt/production/monetization)

-

[Portugalčina - Portugalsko (português)](https://create.roblox.com/docs/pt-pt/production/monetization)

-

[Rumunčina (română)](https://create.roblox.com/docs/ro-ro/production/monetization)

-

[Slovenčina (slovenčina)](https://create.roblox.com/docs/sk-sk/production/monetization)

-

[Slovinčina (slovenščina)](https://create.roblox.com/docs/sl-si/production/monetization)

-

[Švédčina (svenska)](https://create.roblox.com/docs/sv-se/production/monetization)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
