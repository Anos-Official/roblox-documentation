<!-- Source: https://create.roblox.com/docs/lv-lv/production/monetization -->

Monetizācija | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)

# Monetizācija

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Monetizācija ir daļa no Roblox kopējās struktūras, lai nodrošinātu vērtību radītājiem. Ir vairāki dažādi veidi, kā monetizēt savu saturu, tostarp izmantojot [abonementus](#abonementi) , iekasējot piekļuves maksu [Robux](#maksas-piek%C4%BCuve-robux)  vai [vietējā valūtā](#maksas-piek%C4%BCuve-viet%C4%93j%C4%81-val%C5%ABt%C4%81) , piedāvājot [preces vai spējas, ko lietotāji var iegādāties](#izstr%C4%81d%C4%81t%C4%81ja-produkti) , piedāvājot [privātus serverus](#priv%C4%81tie-serveri)  lietotājiem, lai spēlētu tikai ar draugiem, un [pārdodot modeļus un spraudņus](/docs/en-us/production/creator-store#distribute-and-sell-assets)  citiem radītājiem Creator Store.

Ja izvēlaties piedāvāt iegādājamu saturu, Roblox automātiski nereģistrē produktu vai pirkumu informāciju. Lai novērstu datu zudumu, jums rūpīgi jāuzglabā šie dati, izmantojot [DataStoreService](/docs/en-us/reference/engine/classes/DataStoreService)  vai citu datu uzglabāšanas pakalpojumu, kas tiek mitināts ārpus Roblox.

Lai iegūtu padziļinātu skatījumu uz optimālu monetizācijas stratēģiju izstrādi jūsu pieredzei, skatiet [Monetizācijas pamatus](/docs/en-us/production/game-design/monetization-foundations) .

## [Monetizācijas stratēģijas](#monetizācijas-stratēģijas)[](#monetizācijas-stratēģijas)

Esiet uzmanīgi ar monetizācijas metodēm, kuras ieviešat savā spēlē, jo mūsu lietotāji, iespējams, nobalso  pret jūsu spēli, ja viņi nepiekrīt jūsu stratēģijām. Turklāt visiem izstrādātājiem jābūt caurspīdīgiem attiecībā uz jebkuru [nejaušu monetizāciju](/docs/en-us/production/monetization/paid-random-items)  un jāizmanto šīs mehānikas atbildīgi.

Dažas populāras monetizācijas stratēģijas bezmaksas spēlēm citās platformās nav ieteicamas Roblox. Piemēram, iecelšanas mehānikas un taimeri, kurus var noņemt vai pārcelt, var labi darboties citās platformās, taču šie mehānismi nav populāri Roblox lietotājiem, kuri iebilst pret to, ka viņu izklaide beidzas pirms laika.

Šādas labākās prakses ieteikumi ir populāri starp labākajiem izstrādātājiem, pielāgojot monetizācijas stratēģijas Roblox platformai un auditorijai.

Lūdzu, ņemiet vērā, ka, piemērojot šīs tehnikas un apsvērumus, jums nav garantijas, ka jūs efektīvi monetizēsiet savu spēli. Atcerieties, ka jums nav jābūt finansiāliem mērķiem, lai izklaidētos, radot Roblox spēli.

### [Tūristi un vietējie](#tūristi-un-vietējie)[](#tūristi-un-vietējie)

Var būt noderīgi domāt par Roblox lietotājiem divās kategorijās:

-

Tūristi  parasti pārlēkā no vienas spēles uz otru, dodot priekšroku dažādībai pār dziļumu. Viņi dod priekšroku precēm ar tūlītēju efektu, vai nu padarot spēli jautrāku, vai arī izceļoties, aicinot citus lietotājus jautāt, kā un kur viņi ieguva preci.

-

Vietējie  ir vairāk tendēti koncentrēties uz konkrētu spēli vai mazāku spēļu kopumu. Viņi iesaistās dziļāk un parasti veido gandrīz visu spēles aktīvo lietotāju bāzi. Viņi ir vairāk ieinteresēti precēs ar ilgtermiņa ieguvumiem, piemēram, [cīņas biļetē](/docs/en-us/production/game-design/season-pass-design) .

Lai uzzinātu vairāk par to, kā izstrādāt savu spēli, ņemot vērā Roblox lietotājus, skatiet [Dizains Roblox](/docs/en-us/production/game-design/design-for-roblox) .

### [Sociālās funkcijas](#sociālās-funkcijas)[](#sociālās-funkcijas)

Roblox lietotāji parasti izbauda spēles, kas uzsver sociālo mijiedarbību. Piemēram, preču vai notikumu, kas ir pieejami tikai ierobežotu laiku , esamība var radīt satraukumu ap šo saturu. Tirdzniecības  sistēma mudina lietotājus mijiedarboties. Lai gan abas sistēmas var būt veiksmīgas atsevišķi, tās ir īpaši efektīvas, kad tās tiek apvienotas.

### [Dzīvie operācijas](#dzīvie-operācijas)[](#dzīvie-operācijas)

Atbalsts pēc palaišanas ir daudz vieglāks Roblox nekā citās platformās, jo jūs varat ātri izlaist atjauninājumus, lai uzlabotu savu spēli.

Bieži  satura atjauninājumi var būt noderīgi, ja vēlaties saglabāt iesaisti ar savu spēli laika gaitā. Roblox lietotāji ir pieraduši pie regulāriem atjauninājumiem, un ir daudz grūtāk atgūt lietotāja interesi, nekā to saglabāt aktīvu. Ideāls ir nedēļas ritms  atjauninājumiem. Vismaz mērķējiet uz mēneša atjauninājumiem. Par diskusiju par satura ritmu skatiet Level Up [satura ritma darbnīcu](/docs/en-us/production/game-design/content-updates) .

Izstrādājot atjauninājumus, turiet tos koncentrētus uz konkrētu tematu . Tas atvieglo lietotājiem saprast jauno atjauninājumu un noteikt, kāds saturs ir jauns, kad viņi pievienojas. Tas arī palīdz jums koordinēt jūsu saturu un reklāmas aktīvus. Piemēram, ja jūs pievienojat jaunu zooloģisko dārzu savai lomu spēlei, pārliecinieties, ka viss jaunais saturs ir saistīts ar zooloģiskā dārza tēmu.

Nebaidieties likt lietotājiem nopelnīt savu piekļuvi  jaunajam saturam. Jauni lietotāji steigsies spēlēt jaunus atjauninājumus, bet, ja viņi nejutīs, ka ir sasnieguši  kaut ko spēlē, viņi var ātri iziet. Jūs varat radīt sajūtu par atjauninājuma nopelnīšanu, monetizējot atjauninājuma saturu vai izveidojot priekšnoteikumu nosacījumus jaunā satura spēlēšanai.

Lai uzzinātu vairāk par to, kā izstrādāt efektīvu atbalstu pēc palaišanas jūsu spēlei, skatiet [Dzīvo operāciju pamati](/docs/en-us/production/game-design/liveops-essentials) .

## [Produkti](#produkti)[](#produkti)

### [Iegremdējošas reklāmas](#iegremdējošas-reklāmas)[](#iegremdējošas-reklāmas)

[iegremdējošo reklāmu](/docs/en-us/production/monetization/immersive-ads)  sistēma ļauj jums ievietot reklāmas vienības savā spēlē, kas ļauj Roblox programmatīvi piegādāt reklāmas saturu no reklāmdevējiem jūsu aktīvajiem lietotājiem.

![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/Overview-ImageAd.jpg) Attēla reklāmas formāts

Portāla reklāmas formāts

### [Roblox Plus](#roblox-plus)[](#roblox-plus)

[Roblox Plus](/docs/en-us/production/monetization/roblox-plus)  ļauj jums pelnīt, palielinot iekšējo pirkumu skaitu, ko veicina Roblox subsidēti lietotāju atlaides, reģistrēšanās bonusi par katru jauno abonentu, kuru jūs piesaistat, un iesaistīšanās maksātos privātajos servidores.

### [Abonementi](#abonementi)[](#abonementi)

[Abonementi](/docs/en-us/production/monetization/subscriptions)  spēlēs ļauj jums piedāvāt lietotājiem atkārtotus ieguvumus par mēneša maksu.

![](https://prod.docsiteassets.roblox.com/assets/monetization/subscriptions/Example-Subscriptions.png) Spēļu abonementu piemēri

### [Biļetes](#biļetes)[](#biļetes)

[Biļete](/docs/en-us/production/monetization/passes)  ļauj jums iekasēt vienreizēju Robux maksu , lai lietotāji varētu piekļūt īpašām privilēģijām spēlē, piemēram, ieejai ierobežotā zonā, iekšējā avatāra priekšmetā vai pastāvīgā jaudā.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/passes/passes-sample.png)

### [Izstrādātāja produkti](#izstrādātāja-produkti)[](#izstrādātāja-produkti)

[izstrādātāja produkts](/docs/en-us/production/monetization/developer-products)  ir prece vai spēja, ko lietotājs var iegādāties vairāk nekā vienu reizi, piemēram, iekšējā valūta, munīcija vai dziedinošie dzērieni. Jūs varat mudināt pirkumus, reģistrēt tos un iegūt produktu informāciju, izmantojot skriptu.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/developer-products/Buy-Product-Example.jpg)

### [Pārvaldīta cenu noteikšana](#pārvaldīta-cenu-noteikšana)[](#pārvaldīta-cenu-noteikšana)

[Pārvaldīta cenu noteikšana](/docs/en-us/production/monetization/managed-pricing)  ir vienota sistēma, kas apvieno [reģionālo cenu noteikšanu](/docs/en-us/production/monetization/regional-pricing)  un [cenu optimizāciju](/docs/en-us/production/monetization/price-optimization)  vienā vietā. Jūs reģistrējaties vienreiz, izvēlaties, kuri priekšmeti jāiekļauj, un Pārvaldīta cenu noteikšana saglabā jūsu cenas optimizētas visā produktu un reģionu laikā.

### [Cenu optimizācija](#cenu-optimizācija)[](#cenu-optimizācija)

[Cenu optimizācija](/docs/en-us/production/monetization/price-optimization)  ļauj jums atrast labākos cenu punktus jūsu biļetēm un izstrādātāja produktiem, kas var palīdzēt jums pelnīt vairāk naudas laika gaitā, saglabājot jūsu cenas konkurētspējīgas.

### [Maksas piekļuve Robux](#maksas-piekļuve-robux)[](#maksas-piekļuve-robux)

[Maksas piekļuve Robux](/docs/en-us/production/monetization/paid-access-robux)  ļauj jums iekasēt lietotājiem vienreizēju Robux maksu  par piekļuvi jūsu spēlei. Daži izstrādātāji pagaidu izmanto šo funkciju, lai izveidotu slēgtu beta versiju, kurā viņu visaktīvākie lietotāji var iegūt agrīnu piekļuvi spēlei un palīdzēt ar testēšanu un atsauksmēm.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/paid-access/Buy-Access-Example.png)

### [Maksas piekļuve vietējā valūtā](#maksas-piekļuve-vietējā-valūtā)[](#maksas-piekļuve-vietējā-valūtā)

[Maksas piekļuve vietējā valūtā](/docs/en-us/production/monetization/paid-access-local-currency)  ļauj jums iekasēt lietotājiem vienreizēju maksu viņu vietējā valūtā  par piekļuvi jūsu spēlei. Ja viņu vietējā valūta nav pieejama, viņi tiek iekasēti USD. Daži izstrādātāji pagaidu izmanto šo funkciju, lai izveidotu slēgtu beta versiju, kurā viņu visaktīvākie lietotāji var iegūt agrīnu piekļuvi spēlei un palīdzēt ar testēšanu un atsauksmēm.

### [Privātie serveri](#privātie-serveri)[](#privātie-serveri)

[Privātais serveris](/docs/en-us/production/monetization/private-servers)  ir abonementa bāzes funkcija, kas ļauj lietotājam izlemt, kurš var spēlēt spēli kopā ar viņiem. Lai gan privātie serveri var būt bezmaksas, jūs varat arī izmantot privātos serverus kā monetizācijas metodi, iekasējot lietotājiem, kuri vēlas piekļūt privātajiem serveriem, mēneša Robux maksu .

### [Katalogu maksas un komisijas](#katalogu-maksas-un-komisijas)[](#katalogu-maksas-un-komisijas)

Jūs varat izveidot un pārdot aksesuārus un apģērbu tirgū. Pēc tam, kad esat samaksājis augšupielādes maksu un iesniedzis jaunu aktīvu apstiprināšanai, moderācijas komanda pārskata jūsu aktīvu un, ja tas tiek apstiprināts, pievieno jūsu aktīvu katalogam.

Jūs saņemsiet [komisiju](/docs/en-us/marketplace/marketplace-fees-and-commissions)  katru reizi, kad lietotāji iegādājas jūsu katalogā esošo preci. Ja lietotāji iegādājas jūsu katalogā esošo preci spēlē, izmantojot [avatāra pārbaudes izvēlni](/docs/en-us/players/avatar-inspect-menu)  vai [avatāra redaktora pakalpojumu](/docs/en-us/players/avatar-editor) , spēles īpašnieks arī saņem komisiju.

### [Spraudņi un modeļi](#spraudņi-un-modeļi)[](#spraudņi-un-modeļi)

[Spraudnis](/docs/en-us/studio/plugins)  ir paplašinājums, kas pievieno papildu funkcionalitāti Studio, un [modelis](/docs/en-us/parts/models)  ir atkārtoti izmantojams aktīvu veids. Jūs varat piedāvāt abus citiem radītājiem [Creator Store](/docs/en-us/production/creator-store)  bez maksas vai pārdot tos par Amerikas Savienoto Valstu dolāriem  (minimālā cena ir $4.99 spraudņiem un $2.99 modeļiem). Roblox piedāvā tirgū vadošo ieņēmumu daļu šiem pārdošanas darījumiem, jo ​​tikai nodokļi un maksājumu apstrādes maksas tiek atskaitītas. Lai iegūtu vairāk informācijas par spraudņu un modeļu pārdošanu, skatiet [Creator Store - Izplatiet un pārdodiet aktīvus](/docs/en-us/production/creator-store#distribute-and-sell-assets) .

Katram pirkumam ir 30 dienu noguldījuma turēšana. Roblox turēs jūsu pārdošanas daļu 30 dienas, sākot no pārdošanas datuma.

## [Vadlīnijas](#vadlīnijas)[](#vadlīnijas)

Izstrādājot un īstenojot monetizācijas produktus savās spēlēs, ņemiet vērā šādas vadlīnijas, lai nodrošinātu, ka jūsu monetizācijas metodes ir piemērotas visām auditorijām platformā.

### [Produktu prezentēšana](#produktu-prezentēšana)[](#produktu-prezentēšana)

Lai saglabātu drošību un godīgumu, jums jāprezentē monetizācijas produkti veidā, kas ir caurspīdīgs, godīgs un lietotājam draudzīgs. Piemēram, ja piedāvājat atlaides, tām jābūt īstām  un godīgām :

-

Atlaide nav īsta, ja prece vienmēr ir "pārdošanā" par to pašu Robux summu.

-

Atlaide nav godīga, ja tā tiek piedāvāta tikai ļoti īsu laiku, spiežot lietotājus veikt pirkumu pēc iespējas ātrāk.

Lietotājiem nekad nedrīkst būt maldinoši, apjucis vai spiestu veikt pirkumus veidos, kādos viņi to neplānoja, un viņiem vienmēr jābūt brīvai izvēlei skaidri un apzināti iegūt abonementu vai iztērēt Robux par konkrētu preci. Kā vispārējs vadlīnijas, ir dažas prakses, kuras vienmēr jāizvairās, prezentējot monetizācijas produktus jūsu auditorijai:

-

Neapgalvojiet, ka abonements vai prece ir gandrīz izpārdota vai pieejama tikai īsu laiku, ja tas nav patiesi.

-

Neizmantojiet atpakaļskaitīšanas taimeri, kas nav precīzs vai automātiski restartējas par to pašu preci.

Piemēram, ja jūsu spēle ietver "dienas piedāvājumu", kas saka, ka tas ir pieejams tikai 24 stundas, bet pēc tam jūs katru reizi, kad lietotāji piesakās, rādāt to pašu ziņu un tas nekad nebeidzas, jūs esat radījis nepatiesu steigu, kas nav lietotājam draudzīgs.

### [Veicināšana globālajai auditorijai](#veicināšana-globālajai-auditorijai)[](#veicināšana-globālajai-auditorijai)

Roblox ir globāla kopiena visām vecuma grupām, tāpēc reklāmas jūsu spēlēs pēc noklusējuma jābūt piemērotām visām auditorijām. Ja noteikti monetizācijas produkti ir ierobežoti noteiktās vietās, piemēram, maksas nejaušām precēm, Roblox nodrošina [PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  API, lai palīdzētu jums nodrošināt, ka šie produkti ir redzami tikai atbilstošiem lietotājiem.

[PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  atgriež, vai lietotājs ir piemērots konkrētām precēm vai funkcijām atbilstoši viņu atrašanās vietai, vecumam un platformai. Jums jāintegrē šis API savā spēlē, lai izpildītu savas atbilstības saistības, tostarp nosakot, vai katrs lietotājs ir:

-

Piemērots iegādāties abonementus vai komercproduktu.

-

Atļauts maksas nejaušām precēm, maksas preču tirdzniecībai vai redzēt iegremdējošas reklāmas.

Ja lietotājs var izmantot Robux vai kaut ko citu, kas iegūts ar Robux, lai iegūtu nejaušu atlīdzību, jums ir pienākums izmantot [PolicyService](/docs/en-us/reference/engine/classes/PolicyService) , lai bloķētu šo funkciju lietotājiem, kuriem nav atļauts izmantot nejaušas preces apmaiņā pret Robux.

Kā vispārējs vadlīnijas, izvairieties no uzmācīgām vai steidzamām ziņām, mijiedarbojoties ar nepilngadīgajiem, jo augsta spiediena valoda var būt pārāk intensīva:

| ** Valoda, no kuras jāizvairās** | | ** Ieteiktie alternatīvi risinājumi** |
| --- | --- |
| "IEGŪSTI TAGAD" | | "Skatīt preci" |
| "PĒDĒJĀ IESPĒJA, RĪKOJIES TAGAD" | | "Skatīt cenu" |
| "PĒRC PIRMS TAS IR ZUDIS!" | | "Atvērt veikalu" |

## [Papildu lokalizācijas šai lapai](#papildu-lokalizācijas-šai-lapai)[](#papildu-lokalizācijas-šai-lapai)

Papildu lokalizētās versijas šai lapai, kas nav pieejamas vietnes valodas izvēlnē, skatiet šādus saites:

-

[Bulgāru (български)](https://create.roblox.com/docs/bg-bg/production/monetization)

-

[Horvātu (hrvatski)](https://create.roblox.com/docs/hr-hr/production/monetization)

-

[Čehijas (čeština)](https://create.roblox.com/docs/cs-cz/production/monetization)

-

[Dāņu (dansk)](https://create.roblox.com/docs/da-dk/production/monetization)

-

[Nīderlandiešu (Nederlands)](https://create.roblox.com/docs/nl-nl/production/monetization)

-

[Igauņu (eesti)](https://create.roblox.com/docs/et-ee/production/monetization)

-

[Somu (suomi)](https://create.roblox.com/docs/fi-fi/production/monetization)

-

[Grieķu (Ελληνικά)](https://create.roblox.com/docs/el-gr/production/monetization)

-

[Ungāru (magyar)](https://create.roblox.com/docs/hu-hu/production/monetization)

-

[Īru (Gaeilge)](https://create.roblox.com/docs/ga-ie/production/monetization)

-

[Latviešu (latviešu)](https://create.roblox.com/docs/lv-lv/production/monetization)

-

[Lietuviešu (lietuvių)](https://create.roblox.com/docs/lt-lt/production/monetization)

-

[Maltiešu (Malti)](https://create.roblox.com/docs/mt-mt/production/monetization)

-

[Portugāļu - Portugāle (português)](https://create.roblox.com/docs/pt-pt/production/monetization)

-

[Rumāņu (română)](https://create.roblox.com/docs/ro-ro/production/monetization)

-

[Slovāku (slovenčina)](https://create.roblox.com/docs/sk-sk/production/monetization)

-

[Slovēņu (slovenščina)](https://create.roblox.com/docs/sl-si/production/monetization)

-

[Zviedru (svenska)](https://create.roblox.com/docs/sv-se/production/monetization)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
