<!-- Source: https://create.roblox.com/docs/ro-ro/production/monetization -->

Monetizare | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)

# Monetizare

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Monetizarea este o parte a structurii generale a Roblox pentru a oferi valoare creatorilor. Există mai multe abordări diferite pentru a monetiza conținutul tău, inclusiv utilizarea [abonamentelor](#abonamente) , perceperea unei taxe de acces în [Robux](#acces-pl%C4%83tit-%C3%AEn-robux)  sau [monedă locală](#acces-pl%C4%83tit-%C3%AEn-moned%C4%83-local%C4%83) , oferirea de [articole sau abilități pe care utilizatorii le pot cumpăra](#produse-pentru-dezvoltatori) , oferirea de [servere private](#servere-private)  pentru utilizatori care să joace doar cu prietenii și [vânzarea de modele și pluginuri](/docs/en-us/production/creator-store#distribute-and-sell-assets)  altor creatori pe Creator Store.

Dacă alegi să oferi conținut achiziționabil, Roblox nu înregistrează automat informațiile despre produse sau achiziții. Pentru a preveni pierderea datelor, trebuie să stochezi cu atenție aceste date folosind [DataStoreService](/docs/en-us/reference/engine/classes/DataStoreService)  sau un alt serviciu de stocare a datelor găzduit în afara Roblox.

Pentru o privire detaliată asupra proiectării strategiilor optime de monetizare pentru experiența ta, vezi [Fundamentele monetizării](/docs/en-us/production/game-design/monetization-foundations) .

## [Strategii de monetizare](#strategii-de-monetizare)[](#strategii-de-monetizare)

Fii atent la metodele de monetizare pe care le introduci în jocul tău, deoarece utilizatorii noștri sunt susceptibili să voteze negativ  jocul tău dacă nu aprobă strategiile tale. De asemenea, toți dezvoltatorii trebuie să fie transparenți cu privire la orice [monetizare bazată pe șansă](/docs/en-us/production/monetization/paid-random-items)  și să folosească aceste mecanisme în mod responsabil.

Unele strategii populare de monetizare pentru jocurile free-to-play pe alte platforme nu sunt recomandate pentru Roblox. De exemplu, mecanicile de programare și temporizatoarele care pot fi eliminate sau aduse înainte pot funcționa bine pe alte platforme, dar aceste mecanisme sunt nepopulare în rândul utilizatorilor Roblox care au probleme cu distracția lor care ajunge la un sfârșit prematur.

Următoarele sugestii de bune practici sunt populare printre cei mai buni dezvoltatori pentru adaptarea strategiilor de monetizare la platforma și publicul Roblox.

Te rugăm să reții că aplicarea acestor tehnici și considerații nu îți garantează că vei putea monetiza eficient jocul tău. Amintește-ți că nu trebuie să ai obiective financiare pentru a te distra creând un joc Roblox.

### [Turisti și localnici](#turisti-și-localnici)[](#turisti-și-localnici)

Poate fi util să gândești utilizatorii Roblox în două categorii:

-

Turistii  de obicei sar de la un joc la altul, prioritizând varietatea în detrimentul adâncimii. Ei preferă articole cu efecte imediate, fie prin creșterea distracției în joc, fie prin a-i face să iasă în evidență, invitând alți utilizatori să se întrebe cum și de unde au obținut articolul.

-

Localnicii  sunt mai predispuși să se concentreze pe un anumit joc sau un set mai mic de jocuri. Ei se angajează mai profund și, de obicei, formează aproape întreaga bază de utilizatori angajați a unui joc. Ei sunt mai interesați de articole cu beneficii pe termen lung, cum ar fi un [battle pass](/docs/en-us/production/game-design/season-pass-design) .

Pentru a învăța mai multe despre cum să îți proiectezi jocul având în vedere utilizatorii Roblox, vezi [Proiectare pentru Roblox](/docs/en-us/production/game-design/design-for-roblox) .

### [Funcții sociale](#funcții-sociale)[](#funcții-sociale)

Utilizatorii Roblox tind să se bucure de jocuri care pun accent pe interacțiunea socială. De exemplu, având articole sau evenimente care sunt disponibile doar pentru o perioadă limitată  poate crea entuziasm în jurul acelui conținut. Un sistem de tranzacționare  încurajează utilizatorii să interacționeze. Deși ambele sisteme pot fi de succes pe cont propriu, ele sunt deosebit de eficiente atunci când sunt combinate.

### [Operațiuni live](#operațiuni-live)[](#operațiuni-live)

Suportul post-lansare este în multe feluri mai ușor pe Roblox decât pe alte platforme, deoarece poți trimite rapid actualizări pentru a îmbunătăți jocul tău.

Actualizările de conținut frecvente  pot fi utile dacă vrei să menții angajamentul utilizatorilor cu jocul tău în timp. Utilizatorii Roblox sunt obișnuiți să fie angajați prin actualizări regulate, iar poate fi mult mai greu să recâștigi interesul unui utilizator decât să menții utilizatorii activi. O cadentă săptămânală  pentru actualizări este ideală. Cel puțin, vizează actualizări lunare. Pentru o discuție despre cadenta conținutului, vezi atelierul [cadenta conținutului](/docs/en-us/production/game-design/content-updates) .

Când proiectezi actualizări, menține-le concentrate pe un temă  particulară. Acest lucru face mai ușor pentru utilizatori să înțeleagă noua actualizare și să spună ce conținut este nou când se alătură. De asemenea, te ajută să coordonezi conținutul și activele promoționale. De exemplu, dacă adaugi un nou Zoo în jocul tău de rol, asigură-te că tot noul conținut are o legătură cu tema Zoo-ului.

Nu te teme să faci utilizatorii să câștige accesul  la noul conținut. Utilizatorii noi vor veni să joace noile actualizări, dar dacă nu simt că au realizat  ceva în joc, s-ar putea să plece repede după aceea. Poți crea un sentiment de câștig al unei actualizări fie prin monetizarea conținutului actualizării, fie prin crearea unor condiții prealabile pentru a juca noul conținut.

Pentru a învăța mai multe despre cum să proiectezi un suport post-lansare eficient pentru jocul tău, vezi [Esentiale pentru operațiuni live](/docs/en-us/production/game-design/liveops-essentials) .

## [Produse](#produse)[](#produse)

### [Reclame imersive](#reclame-imersive)[](#reclame-imersive)

Sistemul de [reclame imersive](/docs/en-us/production/monetization/immersive-ads)  îți permite să inserezi unități publicitare în jocul tău care permit Roblox să servească programatic conținut publicitar de la anunțători utilizatorilor tăi activi.

![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/Overview-ImageAd.jpg) Format de reclamă pe imagine

Format de reclamă pe portal

### [Roblox Plus](#roblox-plus)[](#roblox-plus)

[Roblox Plus](/docs/en-us/production/monetization/roblox-plus)  îți permite să câștigi prin creșterea achizițiilor în joc, generate de reduceri subvenționate de Roblox, bonusuri de înscriere pentru fiecare nou abonat pe care îl aduci și angajament în servere private plătite.

### [Abonamente](#abonamente)[](#abonamente)

[Abonamentele](/docs/en-us/production/monetization/subscriptions)  din jocuri îți permit să oferi utilizatorilor beneficii recurente pentru o taxă lunară.

![](https://prod.docsiteassets.roblox.com/assets/monetization/subscriptions/Example-Subscriptions.png) Exemple de abonamente pentru jocuri

### [Permise](#permise)[](#permise)

Un [permis](/docs/en-us/production/monetization/passes)  îți permite să percepi o taxă unică în Robux  pentru ca utilizatorii să acceseze privilegii speciale în cadrul unui joc, cum ar fi intrarea într-o zonă restricționată, un articol avatar în joc sau un power-up permanent.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/passes/passes-sample.png)

### [Produse pentru dezvoltatori](#produse-pentru-dezvoltatori)[](#produse-pentru-dezvoltatori)

Un [produs pentru dezvoltatori](/docs/en-us/production/monetization/developer-products)  este un articol sau o abilitate pe care un utilizator o poate cumpăra de mai multe ori, cum ar fi monedă în joc, muniție sau poțiuni. Poți solicita achiziții, le poți înregistra și obține informații despre produse prin scripting.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/developer-products/Buy-Product-Example.jpg)

### [Prețuri gestionate](#prețuri-gestionate)[](#prețuri-gestionate)

[Prețurile gestionate](/docs/en-us/production/monetization/managed-pricing)  sunt un sistem unificat care aduce împreună [prețurile regionale](/docs/en-us/production/monetization/regional-pricing)  și [optimizarea prețurilor](/docs/en-us/production/monetization/price-optimization)  într-un singur loc. Te înscrii o dată, alegi ce articole să incluzi, iar Prețurile gestionate îți mențin prețurile optimizate pe parcursul timpului pentru produse și regiuni.

### [Optimizarea prețurilor](#optimizarea-prețurilor)[](#optimizarea-prețurilor)

[Optimizarea prețurilor](/docs/en-us/production/monetization/price-optimization)  îți permite să găsești cele mai bune puncte de preț pentru permisele și produsele pentru dezvoltatori, ceea ce te poate ajuta să câștigi mai mulți bani în timp, menținând în același timp prețurile competitive.

### [Acces plătit în Robux](#acces-plătit-în-robux)[](#acces-plătit-în-robux)

[Accesul plătit în Robux](/docs/en-us/production/monetization/paid-access-robux)  îți permite să percepi utilizatorilor o taxă unică în Robux  pentru a accesa jocul tău. Unii dezvoltatori folosesc temporar această caracteristică pentru a crea o beta închisă în care utilizatorii lor cei mai angajați pot avea acces timpuriu la un joc și pot ajuta cu testarea și feedback-ul.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/paid-access/Buy-Access-Example.png)

### [Acces plătit în monedă locală](#acces-plătit-în-monedă-locală)[](#acces-plătit-în-monedă-locală)

[Accesul plătit în monedă locală](/docs/en-us/production/monetization/paid-access-local-currency)  îți permite să percepi utilizatorilor o taxă unică în moneda lor locală  pentru a accesa jocul tău. Dacă moneda lor locală nu este disponibilă, aceștia sunt taxați în USD. Unii dezvoltatori folosesc temporar această caracteristică pentru a crea o beta închisă în care utilizatorii lor cei mai angajați pot avea acces timpuriu la un joc și pot ajuta cu testarea și feedback-ul.

### [Servere private](#servere-private)[](#servere-private)

Un [server privat](/docs/en-us/production/monetization/private-servers)  este o caracteristică bazată pe abonament care permite unui utilizator să decidă cine poate juca un joc cu ei. Deși serverele private pot fi gratuite, poți folosi, de asemenea, serverele private ca metodă de monetizare, percepând utilizatorilor care doresc să acceseze servere private o taxă lunară în Robux .

### [Taxe și comisioane pentru catalog](#taxe-și-comisioane-pentru-catalog)[](#taxe-și-comisioane-pentru-catalog)

Poți crea și vinde accesorii și haine pe Marketplace. După ce plătești taxa de încărcare și trimiți un nou activ pentru aprobat, echipa de moderare îți revizuiește activul și, dacă este aprobat, îl adaugă în catalog.

Vei primi un [comision](/docs/en-us/marketplace/marketplace-fees-and-commissions)  de fiecare dată când utilizatorii cumpără articolul tău din catalog. Dacă utilizatorii cumpără articolul tău din catalog într-un joc folosind [meniul de inspectare a avatarului](/docs/en-us/players/avatar-inspect-menu)  sau [serviciul de editor de avatar](/docs/en-us/players/avatar-editor) , proprietarul jocului primește, de asemenea, un comision.

### [Pluginuri și modele](#pluginuri-și-modele)[](#pluginuri-și-modele)

Un [plugin](/docs/en-us/studio/plugins)  este o extensie care adaugă funcționalitate suplimentară în Studio, iar un [model](/docs/en-us/parts/models)  este un tip de activ reutilizabil. Poți oferi ambele altor creatori pe [Creator Store](/docs/en-us/production/creator-store)  gratuit sau le poți vinde pentru dolari americani  (prețul minim este de 4,99 USD pentru pluginuri și 2,99 USD pentru modele). Roblox oferă o împărțire a veniturilor de lider pe piață pentru aceste vânzări, deoarece doar impozitele și comisioanele de procesare a plăților sunt deduse. Pentru mai multe informații despre vânzarea pluginurilor și modelelor, vezi [Creator Store - Distribuie și vinde active](/docs/en-us/production/creator-store#distribute-and-sell-assets) .

Există o reținere de 30 de zile pentru fiecare achiziție. Roblox reține partea ta din vânzare timp de 30 de zile, începând de la data vânzării.

## [Ghiduri](#ghiduri)[](#ghiduri)

Pe măsură ce proiectezi și implementezi produse de monetizare în jocurile tale, ia în considerare următoarele ghiduri pentru a te asigura că metodele tale de monetizare sunt potrivite pentru toate audiențele de pe platformă.

### [Prezentarea produselor](#prezentarea-produselor)[](#prezentarea-produselor)

Pentru a menține siguranța și corectitudinea, trebuie să prezinți produsele de monetizare într-un mod care să fie transparent, onest și prietenos pentru utilizatori. De exemplu, dacă oferi reduceri, acestea trebuie să fie genuină  și corecte :

-

O reducere nu este genuină dacă un articol este întotdeauna "la reducere" pentru aceeași sumă de Robux.

-

O reducere nu este corectă dacă este oferită doar pentru o perioadă foarte scurtă, presând utilizatorii să facă o achiziție cât mai repede posibil.

Utilizatorii nu trebuie niciodată să fie induși în eroare, confuzi sau presați să facă achiziții în moduri pe care nu le-au intenționat, iar ei ar trebui să aibă întotdeauna libertatea de a face o alegere clară și deliberată de a obține un abonament sau de a cheltui Robux pe un articol specific. Ca ghid general, există câteva practici de evitat în orice moment atunci când prezinți produsele de monetizare publicului tău:

-

Nu afirma că un abonament sau un articol este aproape epuizat sau disponibil doar pentru o perioadă scurtă de timp dacă nu este adevărat.

-

Nu folosi un cronometru de numărătoare inversă care nu este precis sau se repornește automat pentru același articol.

De exemplu, dacă jocul tău include o "ofertă a zilei" care spune că este disponibilă doar timp de 24 de ore, dar apoi arăți același mesaj utilizatorilor de fiecare dată când se conectează și nu se oprește niciodată din a fi disponibil, ai creat un sentiment fals de urgență care nu este prietenos pentru utilizatori.

### [Promovarea către audiențe globale](#promovarea-către-audiențe-globale)[](#promovarea-către-audiențe-globale)

Roblox este o comunitate globală pentru utilizatori de toate vârstele, așa că promoțiile din jocurile tale ar trebui să fie potrivite pentru toate audiențele în mod implicit. Dacă anumite produse de monetizare sunt restricționate în anumite locații, cum ar fi articolele random plătite, Roblox oferă API-ul [PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  pentru a te ajuta să te asiguri că acele produse sunt vizibile doar pentru utilizatorii eligibili.

[PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  returnează dacă un utilizator este eligibil pentru articole sau caracteristici specifice în funcție de locația, vârsta și platforma lor. Trebuie să integrezi acest API în jocul tău pentru a-ți îndeplini obligațiile de conformitate, inclusiv determinarea dacă fiecare utilizator este:

-

Eligibil să cumpere abonamente sau produse comerciale.

-

Permis articole random plătite, tranzacționarea articolelor plătite sau să vadă reclame imersive.

Dacă un utilizator poate folosi Robux sau altceva care a fost obținut cu Robux pentru a obține o recompensă random, ești obligat să folosești [PolicyService](/docs/en-us/reference/engine/classes/PolicyService)  pentru a bloca această caracteristică pentru utilizatorii care nu au permisiunea de a folosi articole random în schimbul Robux.

Ca ghid general, evită să folosești mesaje presante sau urgente atunci când interacționezi cu minori, deoarece limbajul de mare presiune poate fi copleșitor:

| ** Limbaj de evitat** | | ** Alternative recomandate** |
| --- | --- |
| "IA-L ACUM" | | "Vezi articolul" |
| "ULTIMA ȘANSĂ, ACȚIONEAZĂ ACUM" | | "Vezi prețul" |
| "CUMPĂRĂ ÎNAINTE SĂ DISPARE!" | | "Deschide magazinul" |

## [Localizări suplimentare pentru această pagină](#localizări-suplimentare-pentru-această-pagină)[](#localizări-suplimentare-pentru-această-pagină)

Pentru versiuni localizate suplimentare ale acestei pagini care nu sunt disponibile în selectorul de limbă al site-ului, vezi următoarele linkuri:

-

[Bulgară (български)](https://create.roblox.com/docs/bg-bg/production/monetization)

-

[Croată (hrvatski)](https://create.roblox.com/docs/hr-hr/production/monetization)

-

[Cehă (čeština)](https://create.roblox.com/docs/cs-cz/production/monetization)

-

[Daneză (dansk)](https://create.roblox.com/docs/da-dk/production/monetization)

-

[Olandeză (Nederlands)](https://create.roblox.com/docs/nl-nl/production/monetization)

-

[Estonă (eesti)](https://create.roblox.com/docs/et-ee/production/monetization)

-

[Finlandeză (suomi)](https://create.roblox.com/docs/fi-fi/production/monetization)

-

[Greacă (Ελληνικά)](https://create.roblox.com/docs/el-gr/production/monetization)

-

[Maghiară (magyar)](https://create.roblox.com/docs/hu-hu/production/monetization)

-

[Irlandeză (Gaeilge)](https://create.roblox.com/docs/ga-ie/production/monetization)

-

[Letonă (latviešu)](https://create.roblox.com/docs/lv-lv/production/monetization)

-

[Lituaniană (lietuvių)](https://create.roblox.com/docs/lt-lt/production/monetization)

-

[Maltese (Malti)](https://create.roblox.com/docs/mt-mt/production/monetization)

-

[Portugheză - Portugalia (português)](https://create.roblox.com/docs/pt-pt/production/monetization)

-

[Română (română)](https://create.roblox.com/docs/ro-ro/production/monetization)

-

[Slovacă (slovenčina)](https://create.roblox.com/docs/sk-sk/production/monetization)

-

[Slovenă (slovenščina)](https://create.roblox.com/docs/sl-si/production/monetization)

-

[Suedeză (svenska)](https://create.roblox.com/docs/sv-se/production/monetization)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
