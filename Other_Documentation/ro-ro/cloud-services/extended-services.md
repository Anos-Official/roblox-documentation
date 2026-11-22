<!-- Source: https://create.roblox.com/docs/ro-ro/cloud-services/extended-services -->

Servicii Extinse | Documentation - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Cloud services](/docs/en-us/cloud-services/data-stores-vs-memory-stores)

# Servicii Extinse

English

* This content is translated using AI (Beta) and may contain errors. To view this page in English, click [here] .

Serviciile Extinse sunt o soluție care vă permite să gestionați utilizarea serviciilor și plățile dincolo de limitele implicite ale Roblox. Acestea includ magazine de date, magazine de memorie, text-to-speech, speech-to-text și calcul.

## [Cerințe de eligibilitate](#cerințe-de-eligibilitate)[](#cerințe-de-eligibilitate)

Pentru a utiliza Serviciile Extinse, contul dumneavoastră Roblox trebuie să:

-

Fie [verificat prin ID](/docs/en-us/production/publishing/account-verification#verify-through-government-id)  și să aibă vârsta de 18 ani sau mai mult.

-

Fie situat într-o [țară acceptată](#%C8%9B%C4%83ri-acceptate) .

-

Aibă o adresă de email validă asociată.

-

Să nu fie în prezent interzis sau moderat.

-

Să accepte și să respecte [termenii de serviciu](https://en.help.roblox.com/hc/articles/37967848292500) .

Pentru conturile de grup, doar proprietarul grupului trebuie să îndeplinească cerințele de eligibilitate.

## [Deblocarea Serviciilor Extinse](#deblocarea-serviciilor-extinse)[](#deblocarea-serviciilor-extinse)

Dacă îndepliniți toate [cerințele de eligibilitate](#cerin%C8%9Be-de-eligibilitate) , puteți finaliza configurarea Serviciilor Extinse introducând detaliile contului și informațiile de plată. Pentru jocurile deținute de grup, doar proprietarul grupului poate debloca Serviciile Extinse și integra jocul în acestea.

Pentru a debloca și utiliza Serviciile Extinse:

1.

În [Creator Dashboard](https://create.roblox.com/dashboard/creations) , mergeți la Creations  și selectați un joc.

2.

Mergeți la Servicii Extinse .

3.

Dacă nu ați introdus încă detaliile contului și informațiile de plată, faceți clic pe Adăugați informațiile lipsă  din bannerul de sus.

1.

Introduceți informațiile contului dumneavoastră. Câmpurile Tip cont , Tip ID fiscal  și ID fiscal  sunt opționale.

-

De asemenea, puteți merge la Finanțe  ⟩ Informații cont  sub secțiunea Servicii Extinse  pentru a gestiona informațiile contului dumneavoastră. Nu trebuie să actualizați nimic altceva pe această pagină.

2.

Faceți clic pe Următorul .

3.

Introduceți o metodă de plată. Puteți introduce o nouă metodă de plată sau selecta din opțiunile de plată disponibile deja asociate cu contul dumneavoastră Roblox.

-

De asemenea, puteți merge la Finanțe  ⟩ Plăți  pentru a adăuga noi metode de plată sau mergeți la Finanțe  ⟩ Facturare  pentru a stabili o nouă metodă de plată implicită.

4.

Faceți clic pe Salvați .

##### Starea contului

Contul dumneavoastră de Servicii Extinse poate fi într-una dintre următoarele stări:

| Stare | | Descriere | | Acțiune necesară |
| Normal | | Puteți utiliza toate funcțiile Serviciilor Extinse. | | Nu este necesară nicio acțiune. |
| --- | --- |
| Întârziat | | Contul dumneavoastră este întârziat deoarece metoda de plată automată a eșuat. Roblox oferă o perioadă de grație de șapte zile  înainte de a suspenda contul dumneavoastră de Servicii Extinse. | | Schimbați metoda de plată și încercați o plată manuală, sau așteptați până când Roblox va încerca din nou să perceapă metoda de plată după ce perioada de grație a expirat. |
| Suspendat | | Nu puteți utiliza niciun serviciu plătit de Servicii Extinse. Cu toate acestea, puteți utiliza în continuare serviciile cu limite implicite. | | Remediați cerințele de eligibilitate, adăugați o metodă de plată validă sau plătiți manual soldul restant al contului dumneavoastră. |

## [Activarea unui serviciu](#activarea-unui-serviciu)[](#activarea-unui-serviciu)

Pentru a activa un serviciu:

1.

Mergeți la Servicii Extinse .

2.

Activați serviciul pe care doriți să-l activați.

3.

Introduceți un buget lunar pentru fiecare resursă aplicabilă sub serviciu. Bugetul lunar minim pe care îl puteți stabili este de 0,50 USD.

Metoda dumneavoastră de plată este taxată fie la sfârșitul lunii, când se generează o factură, fie când utilizarea dumneavoastră atinge 10 USD, oricare dintre acestea se întâmplă prima dată.

Puteți crește sau reduce bugetul lunar al unui serviciu în orice moment. Serviciul dumneavoastră este automat limitat dacă reduceți bugetul la o sumă sub utilizarea curentă de până acum a lunii, sau dacă depășiți bugetul pe care l-ați stabilit.

Roblox vă notifică prin email când utilizarea dumneavoastră atinge 80% din buget, și din nou când atinge 100%.

### [Servicii Extinse pentru Calcul](#servicii-extinse-pentru-calcul)[](#servicii-extinse-pentru-calcul)

Fiecare server de joc primește o cantitate implicită de CPU, care crește cu fiecare jucător care se alătură. Serviciile Extinse pentru Calcul  dublează mai mult CPU-ul pe jucător pe care serverele jocului dumneavoastră îl primesc.

Majoritatea jocurilor de pe Roblox nu beneficiază de acest serviciu, dar jocurile cu fizică intensă pe server sau care fac uz extensiv de [autoritatea serverului](/docs/en-us/projects/server-authority)  ating limitele existente. Pentru a vedea dacă jocul dumneavoastră poate beneficia de Serviciile Extinse pentru Calcul :

-

Verificați [bătăile serverului](/docs/en-us/performance-optimization/identify#server-compute)  pentru scăderi persistente sub 60 FPS.

-

Examinați utilizarea nucleelor CPU pe [panoul de performanță](/docs/en-us/production/analytics/performance#server-charts) .

Înainte de a plăti pentru mai mult CPU, încercați să [reduceți munca pe care o fac serverele dumneavoastră](/docs/en-us/performance-optimization/improve) .

## [Gestionarea facturării](#gestionarea-facturării)[](#gestionarea-facturării)

Pentru a accesa tabloul de bord de facturare pentru Serviciile Extinse:

1.

Mergeți la Finanțe  ⟩ Facturare .

2.

Selectați tab-ul Servicii cloud  pentru a afișa următoarele:

-

Soldul dumneavoastră pending, inclusiv costul de până acum în lună

-

Istoricul dumneavoastră de facturare, inclusiv toată activitatea de facturare a Serviciilor Extinse din jocurile dumneavoastră

Pentru o defalcare detaliată a costurilor soldului dumneavoastră pending curent, faceți clic pe Vezi detalii  lângă metoda dumneavoastră de plată. Pentru o factură detaliată a unei facturi anterioare, faceți clic pe Vezi factură  sub Istoricul facturării .

## [Prețurile serviciilor](#prețurile-serviciilor)[](#prețurile-serviciilor)

Consultați următorul tabel pentru prețurile Serviciilor Extinse:

| Serviciu | |  | | Implicit | | Extins |
| [Magazine de memorie](https://create.roblox.com/docs/cloud-services/memory-stores) | | Solicitări | | 1000 + (CCU × 120) solicitări pe minut | | 0,003 USD / 1M solicitări |
|  | | Stocare | | 64 KB + (CCU × 1,2 KB) | | 0,10 USD / GB pe oră¹ |
| [Text-to-speech](https://create.roblox.com/docs/audio/objects#text-to-speech) | | Solicitări | | 1 + (CCU × 6) solicitări pe minut | | 5,00 USD / 1M solicitări |
| [Speech-to-text](https://create.roblox.com/docs/audio/objects#speech-to-text) | | Solicitări | | 1 + (CCU × 5) solicitări pe minut | | 1 USD / 1M solicitări |
| [Magazine de date standard](https://create.roblox.com/docs/cloud-services/data-stores) | | Obține | | 250 + (CCU * 40) solicitări pe minut | | 0,08 USD / 1M solicitări |
|  | | Setează | | 250 + (CCU * 20) solicitări pe minut | | 0,80 USD / 1M solicitări |
|  | | Listează | | 10 + (CCU * 2) solicitări pe minut | | 0,60 USD / 1M solicitări |
|  | | Elimină | | 100 + (CCU * 40) solicitări pe minut | | 0,80 USD / 1M solicitări |
| [Magazine de date ordonate ](https://create.roblox.com/docs/cloud-services/data-stores) | | Obține | | 250 + (CCU * 40) solicitări pe minut | | 0,08 USD / 1M solicitări |
|  | | Setează | | 250 + (CCU * 20) solicitări pe minut | | 0,25 USD / 1M solicitări |
|  | | GetSorted | | 100 + (CCU * 2) solicitări pe minut | | 0,32 USD / 1M solicitări |
|  | | Elimină | | 100 + (CCU * 40) solicitări pe minut | | 0,25 USD / 1M solicitări |
| [Stocare magazin de date ](https://create.roblox.com/docs/cloud-services/data-stores) | | Stocare | | 100 MB + (1 MB * Jucători pe viață) GB pe lună | | 0,12 USD / GB pe lună |
| [Calcul ](https://create.roblox.com/docs/production/analytics/performance) | | Nuclee CPU | | Primele 100K ore de joc pe lună fără taxă (când sunteți înscris în Serviciile Extinse pentru Calcul) | | 0,001 USD / oră de joc² |

 ¹ GB pe oră = consumul de stocare înmulțit cu timpul. De exemplu, 100 GB ore ar putea echivala cu "100 GB × 1 oră" sau "200 GB × 0,5 ore".  ² Serviciile Extinse pentru Calcul sunt facturate pe baza cât timp rămâne activată funcția, măsurată în minute de joc. Deoarece activarea funcției rezervă capacitate de calcul suplimentară pentru jocul dumneavoastră, se aplică taxe ori de câte ori funcția este activă, chiar dacă calculul suplimentar nu este consumat complet. Orele de joc sunt calculate ca suma tuturor duratelor sesiunilor jucătorilor. De exemplu, dacă 10.000 de utilizatori joacă fiecare timp de 1 oră, aceasta înseamnă 10.000 de ore de joc, rezultând 10 USD în taxe dincolo de alocația lunară inclusă de 100.000 de ore de joc. Aceste limite și prețuri se aplică doar jocurilor înscrise în Serviciile Extinse pentru Calcul. Jocurile care nu se înscriu continuă să primească ore de joc nelimitate sub limitele implicite actuale fără taxe suplimentare.

## [Țări acceptate](#țări-acceptate)[](#țări-acceptate)

Serviciile Extinse sunt disponibile în următoarele țări:

| Țară |
| Australia | | Germania | | Polonia |
| Austria | | Hong Kong | | Portugalia |
| Belgia | | Ungaria | | România |
| Brazilia | | Irlanda | | Singapore |
| Bulgaria | | Italia | | Slovacia |
| Canada | | Kazahstan | | Slovenia |
| Chile | | Letonia | | Africa de Sud |
| Croația | | Lituania | | Coreea de Sud |
| Chipru | | Malaysia | | Spania |
| Cehia | | Malta | | Suedia |
| Dania | | Mexic | | Elveția |
| Estonia | | Olanda | | Thailanda |
| Finlanda | | Noi Zeelandă | | Regatul Unit |
| Franța | | Norvegia | | Statele Unite |
| Georgia | | Peru | |  |

## [Localizări suplimentare pentru această pagină](#localizări-suplimentare-pentru-această-pagină)[](#localizări-suplimentare-pentru-această-pagină)

Pentru versiuni localizate suplimentare ale acestei pagini care nu sunt disponibile în selectorul de limbă al site-ului, consultați următoarele linkuri:

-

[Bulgară (български)](https://create.roblox.com/docs/bg-bg/cloud-services/extended-services)

-

[Croată (hrvatski)](https://create.roblox.com/docs/hr-hr/cloud-services/extended-services)

-

[Cehească (čeština)](https://create.roblox.com/docs/cs-cz/cloud-services/extended-services)

-

[Daneză (dansk)](https://create.roblox.com/docs/da-dk/cloud-services/extended-services)

-

[Olandeză (Nederlands)](https://create.roblox.com/docs/nl-nl/cloud-services/extended-services)

-

[Estonă (eesti)](https://create.roblox.com/docs/et-ee/cloud-services/extended-services)

-

[Finlandeză (suomi)](https://create.roblox.com/docs/fi-fi/cloud-services/extended-services)

-

[Greacă (Ελληνικά)](https://create.roblox.com/docs/el-gr/cloud-services/extended-services)

-

[Maghiară (magyar)](https://create.roblox.com/docs/hu-hu/cloud-services/extended-services)

-

[Irlandeză (Gaeilge)](https://create.roblox.com/docs/ga-ie/cloud-services/extended-services)

-

[Letonă (latviešu)](https://create.roblox.com/docs/lv-lv/cloud-services/extended-services)

-

[Lituaniană (lietuvių)](https://create.roblox.com/docs/lt-lt/cloud-services/extended-services)

-

[Maltese (Malti)](https://create.roblox.com/docs/mt-mt/cloud-services/extended-services)

-

[Portugheză - Portugalia (português)](https://create.roblox.com/docs/pt-pt/cloud-services/extended-services)

-

[Română (română)](https://create.roblox.com/docs/ro-ro/cloud-services/extended-services)

-

[Slovacă (slovenčina)](https://create.roblox.com/docs/sk-sk/cloud-services/extended-services)

-

[Slovenă (slovenščina)](https://create.roblox.com/docs/sl-si/cloud-services/extended-services)

-

[Suedeză (svenska)](https://create.roblox.com/docs/sv-se/cloud-services/extended-services)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
